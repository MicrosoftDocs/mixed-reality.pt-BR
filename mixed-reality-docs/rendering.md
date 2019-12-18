---
title: Renderização
description: A renderização Holographic permite que seu aplicativo desenhe um holograma em um local preciso no mundo todo, seja com precisão no mundo físico ou em um realm que você criou.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: renderização, holograma
ms.openlocfilehash: 8984a16d92ed2f2b72d99e103eaae81b8eba742b
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182026"
---
# <a name="rendering"></a>Renderização

A renderização de Holographic permite que seu aplicativo desenhe um holograma em um local preciso no mundo todo, seja precisamente colocado no mundo físico ou em um realm que você criou. Os [hologramas](hologram.md) são objetos compostos de som e luz. A renderização permite que seu aplicativo adicione a luz.

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Renderização</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Renderização de Holographic

A chave para a renderização de Holographic é saber se você está renderizando para uma exibição visível, como o HoloLens, que permite que o usuário veja o mundo físico e seus hologramas juntos, ou uma exibição opaca como um headset de imersão de realidade do Windows misto que bloqueia o mundo.

Dispositivos com **telas de exibição**, tais [HoloLens](hololens-hardware-details.md), adicionam luz ao mundo. Os pixels pretos são totalmente transparentes, enquanto os pixels mais brilhantes são cada vez mais opacos. Como a luz das telas é adicionada à luz do mundo real, os pixels brancos são, de certa forma, translúcidas.

Embora a renderização de estereoscópico forneça uma indicação de profundidade para os hologramas, adicionar [efeitos de aterramento](interaction-fundamentals.md) pode ajudar os usuários a ver mais facilmente qual superfície um holograma está próximo. Uma técnica de aterramento é adicionar um brilho em um holograma na superfície adjacente e renderizar uma sombra em relação a esse brilho. Dessa forma, sua sombra parece subtrair a luz do ambiente. O [som espacial](spatial-sound.md) é outra indicação de profundidade extremamente importante, permitindo aos usuários o motivo da distância e do local relativo de um holograma.

Dispositivos com **telas opacas**, como [headsets de imersão de realidade do Windows](immersive-headset-hardware-details.md), bloqueiam o mundo. Os pixels pretos são pretos sólidos e qualquer outra cor aparecerá como essa cor para o usuário. Seu aplicativo é responsável por renderizar tudo o que o usuário vê. Isso torna ainda mais importante manter uma taxa de atualização constante para que os usuários tenham uma experiência confortável.

## <a name="predicted-rendering-parameters"></a>Parâmetros de renderização previstos

Os headsets de realidade misturada (headsets de HoloLens e de imersão) acompanham continuamente a posição e a orientação da cabeça do usuário em relação ao seu ambiente. À medida que seu aplicativo começa a preparar seu próximo quadro, o sistema prevê onde o cabeçalho do usuário estará no futuro no momento exato em que o quadro aparece nos monitores. Com base nessa previsão, o sistema calcula a exibição e as transformações de projeção a serem usadas para esse quadro. Seu aplicativo **deve usar essas transformações para produzir resultados corretos**; Se as transformações fornecidas pelo sistema não forem usadas, a imagem resultante não será alinhada com o mundo real, levando ao discomfort do usuário.

Observe que para prever com precisão quando um novo quadro atingirá os monitores, o sistema está medindo constantemente a latência efetiva de ponta a ponta do pipeline de renderização do seu aplicativo. Enquanto o sistema se ajusta à duração do seu pipeline de renderização, você pode melhorar a estabilidade do holograma mantendo o pipeline o mais curto possível.

Os aplicativos que usam técnicas avançadas para aumentar a previsão do sistema podem substituir a exibição do sistema e as transformações de projeção. Esses aplicativos ainda devem usar transformações fornecidas pelo sistema como base para suas transformações personalizadas a fim de produzir resultados significativos.

## <a name="other-rendering-parameters"></a>Outros parâmetros de renderização

Ao renderizar um quadro, o sistema especifica o visor de buffer de fundo no qual seu aplicativo deve desenhar. Esse visor é geralmente menor do que o tamanho total do buffer de quadro. Independentemente do tamanho do visor, depois que o quadro for renderizado pelo aplicativo, o sistema ampliará a imagem para preencher todo o exibido.

Para aplicativos que não conseguem renderizar na taxa de atualização necessária, os [parâmetros de renderização do sistema podem ser configurados](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) para reduzir a pressão de memória e o custo de renderização no custo do aumento de alias de pixel. O formato de buffer de fundo também pode ser alterado, o que para alguns aplicativos pode ajudar a melhorar a largura de banda de memória e a taxa de transferência de pixel.

O frustum de renderização, a resolução e a taxa de quadros em que seu aplicativo é solicitado a renderizar também podem mudar de quadro para quadro e podem ser diferentes nos olhos esquerdo e direito. Por exemplo, quando a MRC ( [captura de realidade mista](mixed-reality-capture.md) ) está ativa e a [configuração de exibição de câmera de foto/vídeo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) não é aceita, um olho pode ser renderizado com um FOV ou resolução maior.

Para qualquer quadro específico, seu aplicativo *deve* renderizar usando a transformação de exibição, transformação de projeção e resolução de visor fornecida pelo sistema. Além disso, seu aplicativo nunca deve supor que qualquer parâmetro de renderização ou de exibição permaneça fixo do quadro para o quadro. Mecanismos como o Unity lidam com todas essas transformações para você em seus próprios objetos de câmera, para que o movimento físico dos usuários e o estado do sistema seja sempre respeitado. Se seu aplicativo permitir a movimentação virtual do usuário por meio do mundo (por exemplo, usando o Thumbstick em um gamepad), você poderá adicionar um objeto Rig pai acima da câmera que o move. Isso faz com que a câmera reflita o movimento físico e virtual do usuário. Se seu aplicativo Modificar a transformação exibição, transformação de projeção ou dimensão viewport fornecida pelo sistema, ele deverá informar o sistema chamando a [API de substituição](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)apropriada.

Para aprimorar a estabilidade da renderização do Holographic, seu aplicativo deve fornecer ao Windows cada quadro o buffer de profundidade usado para renderização. Se o seu aplicativo fornecer um buffer de profundidade, ele deverá ter valores de profundidade coerentes, com profundidade expressa em metros da câmera. Isso permite que o sistema use seus dados de profundidade por pixel para melhor estabilizar o conteúdo se o cabeçalho do usuário terminar um desvio levemente do local previsto. Se não for possível fornecer o buffer de profundidade, você poderá fornecer um ponto de foco e normal, definindo um plano que reduz a maior parte do seu conteúdo. Se o buffer de profundidade e um plano de foco forem fornecidos, o sistema poderá usar ambos. Em particular, é útil fornecer o buffer de profundidade e um ponto de foco que inclui um vetor de velocidade quando seu aplicativo exibe hologramas que estão em movimento.

Consulte o artigo [renderizando no DirectX](rendering-in-directx.md) para obter detalhes de baixo nível sobre seu tópico.

## <a name="holographic-cameras"></a>Câmeras holographics

A realidade mista do Windows apresenta o conceito de uma **câmera Holographic**. As câmeras Holographic são semelhantes à câmera tradicional encontrada em textos de gráficos 3D: elas definem a extrínsecos (posição e a orientação) e as propriedades intrínsecas da câmera. (Por exemplo:, campo de exibição é usado para exibir uma cena 3D virtual.) Ao contrário das câmeras 3D tradicionais, o aplicativo não está no controle da posição, da orientação e das propriedades intrínsecas da câmera. Em vez disso, a posição e a orientação da câmera Holographic são implicitamente controladas pelo movimento do usuário. O movimento do usuário é retransmitido para o aplicativo em uma base quadro a quadro por meio de uma transformação de exibição. Da mesma forma, as propriedades intrínsecas da câmera são definidas pela ótica calibrada do dispositivo e retransmitidas quadro a quadro por meio da transformação projeção.

Em geral, seu aplicativo será renderizado para uma única câmera estéreo. No entanto, um loop de renderização robusto dará suporte a várias câmeras e dará suporte a câmeras mono e estéreo. Por exemplo, o sistema pode solicitar que seu aplicativo seja renderizado de uma perspectiva alternativa quando o usuário ativar um recurso como a MRC ( [captura de realidade misturada](mixed-reality-capture.md) ), dependendo da forma do headset em questão. Os aplicativos que podem dar suporte a várias câmeras [os obtêm](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) conferendo ao [tipo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) de câmeras às quais eles podem dar suporte.

## <a name="volume-rendering"></a>Renderização de volume

Ao renderizar MRIs médicos ou volumes de engenharia em 3D, as técnicas de [renderização de volume](volume-rendering.md) são usadas com frequência. Essas técnicas podem ser particularmente interessantes em realidade misturada, em que os usuários podem ver naturalmente um volume desses ângulos de chave, simplesmente movendo sua cabeça.

## <a name="supported-resolutions-on-hololens-1st-gen"></a>Resoluções com suporte no HoloLens (1ª gen)

* O tamanho máximo do visor é uma propriedade do [HolographicDisplay](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay). O HoloLens é definido como o tamanho máximo do visor, que é 720p (1268x720), por padrão.
* O tamanho do visor pode ser alterado definindo o ViewportScaleFactor no HolographicCamera. Esse fator de escala está no intervalo de 0 a 1.
* O menor tamanho de visor com suporte no HoloLens (1º gen) é de 50% de 720p, que é 360p (634x360). Este é um ViewportScaleFactor de 0,5.
* Qualquer coisa inferior a 540p não é recomendada devido à degradação Visual, mas pode ser usada para identificar afunilamentos na taxa de preenchimento de pixel.

## <a name="supported-resolutions-on-hololens-2"></a>Resoluções com suporte no HoloLens 2

* Os tamanhos de destino de renderização atual e máximo com suporte são propriedades da [configuração de exibição](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). O HoloLens 2 é definido como o tamanho máximo de destino de renderização, que é 1440x936, por padrão.
* Os aplicativos podem alterar o tamanho dos buffers de destino de renderização chamando o método RequestRenderTargetSize para solicitar um novo tamanho de destino de renderização. Um novo tamanho de destino de renderização será escolhido para atender ou exceder o tamanho de destino de renderização solicitado. Essa API altera o tamanho do buffer de destino de renderização, que requer realocação de memória na GPU. As implicações disso incluem: o tamanho do destino de renderização pode ser reduzido para reduzir a pressão de memória na GPU, e esse método não deve ser chamado com alta frequência.
* Os aplicativos ainda podem alterar o tamanho do visor da mesma maneira que faziam para o HoloLens 1. Isso não causa a realocação de memória na GPU, portanto, ela pode ser alterada com alta frequência, mas não pode ser usada para reduzir a pressão de memória na GPU.
* O menor tamanho de visor com suporte no HoloLens 2 é 634x412. Esse é um ViewportScaleFactor de aproximadamente 0,44 quando o tamanho de destino de renderização padrão está em uso.
* Se for fornecido um tamanho de destino de renderização que seja menor do que o menor tamanho de visor com suporte, o fator de escala do visor será ignorado.
* Qualquer coisa inferior a 540p não é recomendada devido à degradação Visual, mas pode ser usada para identificar afunilamentos na taxa de preenchimento de pixel.



## <a name="see-also"></a>Consulte também
* [Estabilidade do holograma](hologram-stability.md)
* [Como renderizar no DirectX](rendering-in-directx.md)
