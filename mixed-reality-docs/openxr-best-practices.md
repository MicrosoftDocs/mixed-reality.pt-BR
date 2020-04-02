---
title: Práticas recomendadas do OpenXR
description: Conheça as práticas recomendadas para qualidade visual, estabilidade e desempenho para seus aplicativos OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, práticas recomendadas, desempenho, qualidade, estabilidade
ms.openlocfilehash: 0a0bbd37521be52ec328b4f32e53969c0ec7fef4
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549367"
---
# <a name="openxr-app-best-practices"></a>Práticas recomendadas do aplicativo OpenXR

Você pode ver um exemplo das práticas recomendadas abaixo no arquivo OpenXRProgram. cpp do <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>. A função Run () no início captura um fluxo de código do aplicativo OpenXR típico da inicialização para o loop de evento e de renderização.

## <a name="best-practices-for-visual-quality-and-stability"></a>Práticas recomendadas para qualidade visual e estabilidade

As práticas recomendadas nesta seção descrevem como obter a melhor qualidade visual e estabilidade em qualquer aplicativo OpenXR.

Para obter mais recomendações de desempenho específicas para o HoloLens 2, consulte a seção [práticas recomendadas de desempenho no hololens 2](#best-practices-for-performance-on-hololens-2) abaixo.

### <a name="gamma-correct-rendering"></a>Gama-renderização correta

Deve-se ter cuidado para garantir que seu pipeline de renderização seja de gama correto. Ao renderizar para um SwapChain, o formato de exibição de destino de renderização deve corresponder ao formato SwapChain (por exemplo, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` tanto para o formato SwapChain como para a exibição de destino de renderização).
A exceção é se o pipeline de renderização do aplicativo faz uma conversão manual do sRGB no código do sombreador; nesse caso, o aplicativo deve solicitar um formato de SwapChain sRGB, mas usar o formato linear para a exibição de destino de renderização (por exemplo, solicitar `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` como o formato SwapChain, mas usar `DXGI_FORMAT_B8G8R8A8_UNORM` como a exibição de destino de renderização) para impedir que o conteúdo seja corrigido duas vezes.

### <a name="submit-depth-buffer-for-projection-layers"></a>Enviar buffer de profundidade para camadas de projeção

Sempre use `XR_KHR_composition_layer_depth` extensão e envie o buffer de profundidade junto com a camada de projeção ao enviar um quadro para `xrEndFrame`.
Isso melhora a estabilidade do holograma habilitando a Reprojeção de profundidade de hardware no HoloLens 2.

### <a name="choose-a-reasonable-depth-range"></a>Escolher um intervalo de profundidade razoável

Prefira um intervalo de profundidade mais estreito para o escopo do conteúdo virtual para ajudar a estabilidade do holograma no HoloLens.
Por exemplo, o exemplo OpenXrProgram. cpp está usando 0,1 a 20 metros.
Use [-Z invertido](https://developer.nvidia.com/content/depth-precision-visualized) para uma resolução de profundidade mais uniforme.
Observe que, no HoloLens 2, o uso do formato de profundidade de `DXGI_FORMAT_D16_UNORM` preferencial ajudará a obter uma melhor taxa de quadros e desempenho, embora os buffers de profundidade de 16 bits forneçam uma resolução de menos profundidade do que os buffers de profundidade de 24 bits.
Portanto, seguir essas práticas recomendadas para fazer o melhor uso da resolução de profundidade se torna mais importante.

### <a name="prepare-for-different-environment-blend-modes"></a>Preparar para modos de mesclagem de ambiente diferentes

Se seu aplicativo também for executado em headsets de imersão que bloqueiam completamente o mundo, certifique-se de enumerar modos de mistura de ambiente com suporte usando `xrEnumerateEnvironmentBlendModes` API e prepare o conteúdo de renderização de acordo.
Por exemplo, para um sistema com `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` como o HoloLens, o aplicativo deve usar transparente como a cor clara, enquanto para um sistema com `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`, o aplicativo deve renderizar alguma cor opaca ou alguma sala virtual em segundo plano.

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>Escolher o espaço de referência não associado como espaço raiz do aplicativo

Normalmente, os aplicativos estabelecem algum espaço de coordenadas do mundo raiz para conectar modos de exibição, ações e hologramas juntos.
Use `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` quando houver suporte para a extensão para estabelecer um [sistema de coordenadas de escala mundial](coordinate-systems.md#building-a-world-scale-experience), permitindo que seu aplicativo Evite descompasso de holograma indesejados quando o usuário se move de longe (por exemplo, 5 metros de distância) de onde o aplicativo é iniciado.
Use `XR_REFERENCE_SPACE_TYPE_LOCAL` como um fallback se a extensão de espaço não associado não existir.

### <a name="associate-hologram-with-spatial-anchor"></a>Associar holograma a âncora espacial

Ao usar um espaço de referência não associado, os hologramas que você coloca diretamente no espaço de referência [podem cair conforme o usuário percorre as salas distantes e, em seguida, retorna](coordinate-systems.md#building-a-world-scale-experience).
Para usuários com holograma, coloque em um local discreto no mundo, [crie uma âncora espacial](spatial-anchors.md#best-practices) usando a função de extensão `xrCreateSpatialAnchorSpaceMSFT` e posicione o holograma em sua origem.
Isso manterá esse holograma independentemente estável ao longo do tempo.

### <a name="support-mixed-reality-capture"></a>Suporte à captura de realidade misturada

Embora a exibição primária do HoloLens 2 Use a mistura de ambiente aditivo, quando o usuário inicia a [captura de realidade misturada](mixed-reality-capture-for-developers.md), o conteúdo de renderização do aplicativo será misturado com o fluxo de vídeo do ambiente.
Para obter a melhor qualidade visual em vídeos de captura de realidade misturada, é melhor definir o `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` no `layerFlags`da camada de projeção.

## <a name="best-practices-for-performance-on-hololens-2"></a>Práticas recomendadas para o desempenho no HoloLens 2

Como um dispositivo móvel com suporte à Reprojeção de hardware, o HoloLens 2 tem requisitos mais estritos para obter o desempenho ideal.  Há várias maneiras de enviar dados de composição por meio de `xrEndFrame`, o que resultará em pós-processamento que terá uma penalidade de desempenho perceptível.

### <a name="select-a-swapchain-format"></a>Selecionar um formato SwapChain

Sempre enumere os formatos de pixel com suporte usando `xrEnumerateSwapchainFormats`e escolha a primeira cor e o formato de pixel de profundidade do tempo de execução ao qual o aplicativo dá suporte, pois é isso que o tempo de execução prefere para o desempenho ideal. Observe que, no HoloLens 2, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` e `DXGI_FORMAT_D16_UNORM` normalmente é a primeira opção para obter um melhor desempenho de renderização. Essa preferência pode ser diferente nos headsets de VR em execução em um PC desktop, em que os buffers de profundidade de 24 bits têm menos impacto no desempenho.
  
**Aviso de desempenho:** O uso de um formato diferente do formato de cor SwapChain primário resultará em pós-processamento de tempo de execução, o que resulta em uma penalidade de desempenho significativa.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>Renderizar com os parâmetros de renderização recomendados e o tempo de quadro

Sempre renderizar com a largura/altura da configuração de exibição recomendada (`recommendedImageRectWidth` e `recommendedImageRectHeight` de `XrViewConfigurationView`) e sempre usar a API `xrLocateViews` para consultar a exibição recomendada, FOV e outros parâmetros de renderização antes da renderização.
Sempre use o `XrFrameEndInfo.predictedDisplayTime` da chamada de `xrWaitFrame` mais recente ao consultar poses e exibições.
Isso permite que o HoloLens ajuste a renderização e otimize a qualidade visual para a pessoa que está desgastando o HoloLens.

### <a name="use-a-single-projection-layer"></a>Usar uma única camada de projeção

O HoloLens 2 tem energia limitada de GPU para que os aplicativos processem conteúdo e um compositor de hardware otimizado para uma única camada de projeção.
Sempre usar uma única camada de projeção pode ajudar a taxa de quadros, a estabilidade do holograma e a qualidade visual do aplicativo.  
  
**Aviso de desempenho:** O envio de qualquer coisa, exceto uma única camada de proteção, resultará em um pós-processamento de tempo de execução que apresenta uma penalidade de desempenho significativa.

### <a name="render-with-texture-array-and-vprt"></a>Renderizar com matriz de textura e VPRT

Crie um `xrSwapchain` para os olhos esquerdo e direito usando `arraySize=2` para SwapChain de cor e outro para profundidade.
Renderize o olho esquerdo na fatia 0 e no olho certo para a fatia 1.
Use um sombreador com VPRT e chamadas de desenho em instância para a renderização estereoscópico para minimizar a carga de GPU.
Isso também permite que a otimização do tempo de execução alcance o melhor desempenho no HoloLens 2.
Alternativas ao uso de uma matriz de textura, como renderização em toda a parte ou uma SwapChain separada por olho, resultarão em um pós-processamento de tempo de execução que vem em uma penalidade de desempenho significativa.

### <a name="avoid-quad-layers"></a>Evitar camadas quádruplas

Em vez de enviar camadas quádruplas como camadas de composição com `XrCompositionLayerQuad`, processe o conteúdo Quad diretamente no SwapChain de projeção.

**Aviso de desempenho:** Fornecer camadas adicionais além de uma única camada de projeção, como camadas quádruplas, resultará em um pós-processamento de tempo de execução que apresenta uma penalidade de desempenho significativa.