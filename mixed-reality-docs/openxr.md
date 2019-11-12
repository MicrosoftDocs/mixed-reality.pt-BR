---
title: OpenXR
description: Crie um mecanismo usando o padrão da API OpenXR portátil e implante-o na realidade mista do Windows e fones de ouvido 2 do HoloLens.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Mixed Realm OpenXR portal do desenvolvedor, DirectX, nativo, mecanismo personalizado do aplicativo nativo, middleware
ms.openlocfilehash: 67d2ab42a40aa04eb9dcd6881a4392a81c0f3b8f
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914389"
---
# <a name="openxr"></a>OpenXR

O OpenXR é um padrão de API livre de royalties aberto da <a href="https://www.khronos.org/" target="_blank">Khronos</a> que fornece aos mecanismos acesso nativo a uma ampla gama de dispositivos de muitos fornecedores que abrangem o [espectro de realidade misturada](mixed-reality.md).

Você pode desenvolver usando OpenXR em um headset de imersão de realidade 2 ou Windows misto na área de trabalho.  Se você não tiver acesso a um headset, poderá usar o emulador do HoloLens 2 ou o simulador de realidade mista do Windows.

## <a name="why-openxr"></a>Por que OpenXR?

Com o OpenXR, você pode criar mecanismos direcionados a ambos os dispositivos Holographic (como o HoloLens 2) que colocam o conteúdo digital no mundo real como se estivesse realmente lá, bem como dispositivos de imersão (como o Windows Mixed Realm headsets para PCs Desktop) que ocultam o físico o mundo e o substituem por uma experiência digital.  O OpenXR permite que você escreva código depois de ser portátil em uma ampla gama de plataformas de hardware.

A API OpenXR usa um carregador que conecta seu aplicativo diretamente ao suporte de plataforma nativa do headset.  Isso oferece aos seus usuários finais o desempenho máximo e a latência mínima, se eles estiverem usando um headset de realidade mista do Windows ou qualquer outro headset.

## <a name="what-is-openxr"></a>O que é o OpenXR?

A API Core OpenXR 1,0 fornece a funcionalidade básica que você precisará para criar um mecanismo que pode ter como alvo os dispositivos Holographic, como o HoloLens 2 e dispositivos de imersão, como headsets de realidade mista do Windows:
* Sistemas + sessões
* Espaços de referência (exibição, local, estágio)
* Exibir configurações (mono, estéreo)
* Permuta + temporização de quadro
* Camadas de composição
* Entrada e haptics
* API de gráficos + integração de plataforma

Para saber mais sobre a API do OpenXR, confira a <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação</a>do OpenXR 1,0, <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">referência de API</a> e <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guia de referência rápida</a>.  Para obter mais informações, consulte a <a href="https://www.khronos.org/openxr/" target="_blank">página Khronos OpenXR</a>.

Para direcionar o conjunto de recursos completo do HoloLens 2, você também usará extensões de OpenXR específicas de fornecedor e de fornecedor que habilitam recursos adicionais além do OpenXR 1,0 Core, como controle de mão articulado, acompanhamento de olho, mapeamento espacial e âncoras espaciais.  Consulte a seção de [roteiro](openxr.md#roadmap) abaixo para obter mais informações sobre as extensões lançadas posteriormente neste ano.

Observe que o OpenXR não é, em si, um mecanismo de realidade misturada.  Em vez disso, o OpenXR permite que mecanismos como Unity e inreais gravem código portátil uma vez que possam acessar os recursos da plataforma nativa do dispositivo Holographic ou de imersão do usuário, independentemente de qual fornecedor criou essa plataforma.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introdução ao OpenXR para o HoloLens 2

Para começar a desenvolver aplicativos OpenXR para o HoloLens 2:

1. Configure um HoloLens 2 ou siga as instruções para [instalar o emulador do HoloLens 2](using-the-hololens-emulator.md).
1. Inicie o aplicativo da loja de dentro do dispositivo ou emulador e verifique se todos os aplicativos estão atualizados.  Isso garantirá que o tempo de execução do OpenXR em seu HoloLens seja atualizado para o OpenXR 1,0.  Se estiver usando o emulador, você desejará consultar as [instruções de entrada do emulador](using-the-hololens-emulator.md#basic-emulator-input) para ajudá-lo a usar o aplicativo da loja dentro do emulador.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introdução ao OpenXR for Windows Mixed realness headsets

Para começar a desenvolver aplicativos OpenXR para headsets de imersão misturadas do Windows:

1. Verifique se você está executando o Windows 10 pode 2019 atualização (1903), que é o requisito mínimo para o Windows Mixed Reality que os usuários finais executam aplicativos OpenXR.  Se você estiver em uma versão anterior do Windows 10, poderá atualizar para a atualização de maio de 2019 usando o <a href="https://www.microsoft.com//software-download/windows10" target="_blank">Assistente de atualização do Windows 10</a>.  Se você não conseguir atualizar seu computador, também será possível [desenvolver seu aplicativo OpenXR usando a atualização de 10 de outubro de 2018 (1809)](openxr.md#developing-on-windows-10-october-2018-update), embora você possa enfrentar um desempenho inferior ou outros problemas.
2. Configure um headset de realidade mista do Windows ou siga as instruções para [habilitar o simulador de realidade mista do Windows](using-the-windows-mixed-reality-simulator.md).  Depois de configurar a realidade mista do Windows, o portal de realidade misturada instalará automaticamente o tempo de execução do Windows Mixed Reality OpenXR.  O Microsoft Store manterá o tempo de execução atualizado.
3. Torne o tempo de execução do OpenXR do Windows Mixed Realm ativo iniciando o portal de realidade misturada no menu Iniciar, clicando no botão... no canto inferior esquerdo e selecionando "configurar OpenXR".<br>
![configurar o OpenXR no portal de realidade misturada](images/mixed-reality-portal-set-up-openxr.png)

Se você precisar tornar o tempo de execução do Windows Mixed Reality OpenXR ativo novamente, repita a etapa 3.

> [!NOTE]
> Em breve, o tempo de execução do Windows Mixed Reality OpenXR será configurado automaticamente para todos os usuários finais do Windows Mixed Reality.

## <a name="getting-the-mixed-reality-openxr-developer-portal"></a>Obtendo o portal do desenvolvedor OpenXR da realidade misturada

Para experimentar o tempo de execução do Windows Mixed Reality OpenXR, você pode instalar o <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">aplicativo [Mixed Reality OpenXR Developer portal</a>.  Esse aplicativo fornece uma cena de demonstração que exercita vários recursos do OpenXR, juntamente com uma página de status do sistema que fornece informações importantes sobre o tempo de execução ativo e o headset atual.

![Aplicativo de portal do desenvolvedor OpenXR de realidade misturada](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>Criando um aplicativo OpenXR de exemplo

O projeto <a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> demonstra um exemplo de OpenXR simples com dois arquivos de projeto do Visual Studio, um para um aplicativo de área de trabalho Win32 e outro para um aplicativo UWP HoloLens 2.  Como a solução contém um projeto UWP do HoloLens, você precisará do [plataforma universal do Windows carga de trabalho de desenvolvimento](install-the-tools.md#installation-checklist) instalada no Visual Studio para abri-lo totalmente.

Observe que, embora os arquivos de projeto Win32 e UWP sejam separados devido a diferenças no empacotamento e na implantação, o código do aplicativo dentro de cada projeto é de 100% o mesmo!

## <a name="openxr-app-best-practices-for-hololens-2"></a>Práticas recomendadas do aplicativo OpenXR para o HoloLens 2

Você pode ver um exemplo das práticas recomendadas abaixo no arquivo [OpenXRProgram. cpp](https://github.com/microsoft/OpenXR-SDK-VisualStudio/blob/master/samples/BasicXrApp/OpenXrProgram.cpp) do BasicXrApp. A função Run () no início captura um fluxo de código do aplicativo OpenXR típico da inicialização para o loop de evento e de renderização.

### <a name="select-a-pixel-format"></a>Selecionar um formato de pixel

Sempre enumere os formatos de pixel com suporte usando `xrEnumerateSwapchainFormats`e escolha a primeira cor e o formato de pixel de profundidade do tempo de execução ao qual o aplicativo dá suporte, porque é isso que o tempo de execução prefere. Observe que, no HoloLens 2, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` e `DXGI_FORMAT_D16_UNORM` normalmente é a primeira opção para obter um melhor desempenho de renderização. Essa preferência pode ser diferente em headsets de VR em execução em um PC desktop.  
  
**Aviso de desempenho:** O uso de um formato diferente do formato de cor SwapChain primário resultará em pós-processamento de tempo de execução, o que resulta em uma penalidade de desempenho significativa.

### <a name="gamma-correct-rendering"></a>Gama-renderização correta

Embora isso se aplique a todos os tempos de execução do OpenXR, deve-se tomar cuidado para garantir que o pipeline de renderização seja correto para o gama. Ao renderizar para um SwapChain, o formato de exibição de destino de renderização deve corresponder ao formato SwapChain (por exemplo, DXGI_FORMAT_B8G8R8A8_UNORM_SRGB tanto para o formato SwapChain como para a exibição de destino de renderização).
A exceção é se o pipeline de renderização do aplicativo faz uma conversão manual do sRGB no código do sombreador; nesse caso, o aplicativo deve solicitar um formato de SwapChain sRGB, mas usar o formato linear para a exibição de destino de renderização (por exemplo, a solicitação DXGI_FORMAT_B8G8R8A8_UNORM_SRGB como o formato SwapChain, mas use DXGI_FORMAT_B8G8R8A8_UNORM como a exibição de destino de renderização) para impedir que o conteúdo seja corrigido de gama duplo.

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

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>Renderizar com os parâmetros de renderização recomendados e o tempo de quadro

Sempre renderizar com a largura/altura da configuração de exibição recomendada (`recommendedImageRectWidth` e `recommendedImageRectHeight` de `XrViewConfigurationView`) e sempre usar a API `xrLocateViews` para consultar a exibição recomendada, FOV e outros parâmetros de renderização antes da renderização.
Sempre use o `XrFrameEndInfo.predictedDisplayTime` da chamada de `xrWaitFrame` mais recente ao consultar poses e exibições.
Isso permite que o HoloLens ajuste a renderização e otimize a qualidade visual para a pessoa que está desgastando o HoloLens.

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

**Aviso de desempenho:** A omissão do sinalizador de `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` na camada de projeção única resultará em pós-processamento do tempo de execução, o que resulta em uma penalidade de desempenho significativa.

### <a name="avoid-quad-layers"></a>Evitar camadas quádruplas

Em vez de enviar camadas quádruplas como camadas de composição com `XrCompositionLayerQuad`, processe o conteúdo Quad diretamente no SwapChain de projeção.

**Aviso de desempenho:** Fornecer camadas adicionais além de uma única camada de projeção, como camadas quádruplas, resultará em um pós-processamento de tempo de execução que apresenta uma penalidade de desempenho significativa.

## <a name="openxr-app-performance-on-hololens-2"></a>Desempenho do aplicativo OpenXR no HoloLens 2

No HoloLens 2, há várias maneiras de enviar dados de composição por meio de `xrEndFrame`, o que resultará em pós-processamento que terá uma penalidade de desempenho perceptível.
Para evitar o desempenho penalities, [envie um único `XrCompositionProjectionLayer`](#use-a-single-projection-layer) com as seguintes características:
* [Usar uma matriz de textura SwapChain](#render-with-texture-array-and-vprt)
* [Usar o formato SwapChain de cor primária](#select-a-pixel-format)
* [Definir o sinalizador de mistura de origem da textura-fonte-alfa](#support-mixed-reality-capture)
* [Usar as dimensões de exibição recomendadas](#render-with-recommended-rendering-parameters-and-frame-timing)
* Não definir o sinalizador de `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`
* Defina o `XrCompositionLayerDepthInfoKHR` `minDepth` como 0,0 f e `maxDepth` como 1,0 f

Considerações adicionais resultarão em melhor desempenho:
* [Usar o formato de profundidade de 16 bits](#choose-a-reasonable-depth-range)
* [Fazer chamadas de desenho em instância](#render-with-texture-array-and-vprt)

## <a name="roadmap"></a>Mapa

A especificação OpenXR define um mecanismo de extensão que permite que implementadores de tempo de execução exponham funcionalidades adicionais além dos [principais recursos](openxr.md#what-is-openxr) definidos na <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação OpenXR 1,0 base</a>.

Há três tipos de extensões OpenXR:
* **Extensões de fornecedor (por exemplo, MSFT):** Habilita a inovação por fornecedor em recursos de hardware ou software.  Qualquer fornecedor de tempo de execução pode introduzir e enviar uma extensão de fornecedor a qualquer momento.
* **Extensões ext:** Extensões entre fornecedores que várias empresas definem e implementam.  Grupos de empresas interessadas podem introduzir extensões EXT a qualquer momento.
* **Extensões KHR:** As extensões Khronos oficiais são ratificadas como parte de uma versão de especificação principal.  As extensões KHR são cobertas pela mesma licença que a principal espec.

Ao final do ano, o tempo de execução do Windows Mixed Reality OpenXR dará suporte a um conjunto de extensões MSFT e EXT que trazem o conjunto completo de recursos do HoloLens 2 para aplicativos OpenXR:
* [Espaço de referência não associado (experiências de escala mundial)](coordinate-systems.md#building-a-world-scale-experience)
* [Âncoras espaciais + armazenamento](spatial-anchors.md)
* [Mão Articulation + malha à mão](hands-and-tools.md)
* [Foco com o olhar](eye-tracking.md)
* [Configurações de exibição secundárias (captura de realidade mista)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [Reconhecimento de cena](scene-understanding.md)
* Interoperabilidade com APIs de SDK do Windows

Embora algumas dessas extensões possam ser iniciadas como extensões de MSFT específicas do fornecedor, a Microsoft e outros fornecedores de tempo de execução OpenXR estão trabalhando juntos para projetar extensões de extensão ou KHR de vários fornecedores para muitas dessas áreas de recursos.  Isso permitirá que o código que você escreve para esses recursos seja portável em fornecedores de tempo de execução, assim como na Especificação principal.

## <a name="troubleshooting"></a>Painel de controle da

Aqui estão algumas dicas de solução de problemas para o tempo de execução OpenXR do Windows Mixed Reality.  Se você tiver outras dúvidas sobre a <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação do OpenXR 1,0</a>, visite os <a href="https://community.khronos.org/c/openxr" target="_blank">fóruns do Khronos OpenXR</a> ou a <a href="https://khr.io/slack" target="_blank">margem de atraso #openxr canal</a>.

### <a name="developing-on-windows-10-october-2018-update"></a>Desenvolvendo no Windows 10 de outubro de 2018 atualização

Se não for possível [atualizar seu PC de desenvolvimento para a atualização de maio de 2019](https://www.microsoft.com//software-download/windows10), você poderá configurar seu PC de atualização do Windows 10 de outubro de 2018 (1809) para desenvolvimento seguindo mais uma etapa:

1. Siga as etapas acima para começar a usar o OpenXR em seu PC desktop.
1. Para definir o tempo de execução do Windows Mixed Reality OpenXR como o tempo de execução do OpenXR do seu sistema, instale o [pacote de compatibilidade do desenvolvedor do Windows Mixed Reality OpenXR](https://aka.ms/openxr-compat).

> [!NOTE]
> Embora a atualização do Windows 10 de outubro de 2018 (1809) possa ser usada ao desenvolver seus aplicativos OpenXR, a atualização do Windows 10 pode ser 2019 (1903) é o requisito mínimo para que os usuários finais usem o OpenXR com a realidade mista do Windows.  Você pode enfrentar um desempenho inferior ou outros problemas ao executar seu aplicativo OpenXR na atualização de outubro de 2018.  É altamente recomendável que você atualize seu PC de desenvolvimento para a atualização 2019 do Windows 10 (1903).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>O aplicativo OpenXR não está iniciando a realidade mista do Windows

Se seu aplicativo OpenXR não estiver iniciando a realidade mista do Windows quando você executá-lo, o tempo de execução do Windows Mixed Reality OpenXR não poderá ser definido como o tempo de execução ativo.  Siga as instruções acima para [começar a usar o OpenXR for Windows Mixed realness headsets](#getting-started-with-openxr-for-windows-mixed-reality-headsets) para tornar o tempo de execução ativo.

Você também pode executar o [portal do desenvolvedor OpenXR da realidade misturada](#getting-the-mixed-reality-openxr-developer-portal) para solucionar problemas adicionais para obter ajuda em relação ao estado do tempo de execução do Windows Mixed Reality OpenXR em seu sistema.

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>Portal de realidade misturada não mostrando o item de menu "configurar OpenXR"

Verifique se você está executando pelo menos a atualização de 10 de outubro de 2018 do Windows (1809).  Se você estiver em uma versão anterior do Windows 10, poderá atualizar para a atualização de maio de 2019 (1903) usando o [Assistente de atualização do Windows 10](https://www.microsoft.com//software-download/windows10).

O item de menu "configurar OpenXR" pode não estar disponível se você tiver uma versão mais antiga do aplicativo do portal de realidade misturada.  Verifique se há uma [atualização de aplicativo do portal da realidade misturada](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) para garantir que você tem a versão mais recente.

Observe que o item de menu "set up OpenXR" não aparecerá se o tempo de execução do Windows Mixed Reality já estiver instalado e ativo.  Você pode instalar o [portal do desenvolvedor OpenXR da realidade mista](#getting-the-mixed-reality-openxr-developer-portal) para determinar o status atual do tempo de execução do OpenXR em seu sistema.

## <a name="see-also"></a>Consulte também

* <a href="https://www.khronos.org/openxr/" target="_blank">Mais informações sobre o OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Especificação do OpenXR 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Referência de API do OpenXR 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guia de referência rápida do OpenXR 1,0</a>
