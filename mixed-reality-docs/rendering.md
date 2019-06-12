---
title: Renderização
description: Renderização holográfica permite que seu aplicativo desenhar um holograma em um local exato no mundo em torno do usuário, se ele é colocado com precisão no mundo físico ou em um território virtual que você criou.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: renderização, holograma
ms.openlocfilehash: 5271e94521b99e76998c2cbb43475a5f3f847917
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829906"
---
# <a name="rendering"></a>Renderização

Renderização holográfica permite que seu aplicativo desenhar um holograma em um local exato no mundo em torno do usuário, se ele é colocado com precisão no mundo físico ou em um território virtual que você criou. [Hologramas](hologram.md) são feitos de objetos de luz e som e renderização permite que seu aplicativo Adicionar a luz.

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
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
    </tr>
     <tr>
        <td>Renderização</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Renderização holográfica

Chave à renderização holográfica é saber se você estiver renderizando para uma exibição transparente como HoloLens, que permite que o usuário ver o mundo físico e seu hologramas juntos – ou uma exibição opaca como o Windows Mixed Reality imersivo fone de ouvido, quais blocos no mundo todo.

Dispositivos com **transparente exibe**, como [HoloLens](hololens-hardware-details.md), adicionam luz ao mundo. Pixels pretos será totalmente transparentes, enquanto pixels mais brilhantes será cada vez mais opacas. Como a luz usando as exibições é adicionado à luz do mundo real, até mesmo brancos pixels são um pouco translúcidos.

Enquanto a renderização estereoscópica fornece uma indicação de profundidade para seu hologramas, adicionando [efeitos de aterramento](interaction-fundamentals.md) pode ajudar os usuários a ver mais facilmente quais superfície um holograma está próximo. Uma técnica de aterramento é adicionar um brilho ao redor de um holograma na superfície do próxima e, em seguida, renderizar uma sombra em relação a esse brilho. Dessa forma, a sombra será exibida para subtrair a luz do ambiente. [Som espacial](spatial-sound.md) pode ser outra indicação de profundidade extremamente importante, permitindo que o motivo dos usuários sobre o local relativo de um holograma e distância.

Dispositivos com **exibe opaco**, como [fones imersivos em exposição Windows Mixed Reality](immersive-headset-hardware-details.md), bloquear o mundo. Pixels pretos será preto sólido, e qualquer outra cor será exibido como essa cor para o usuário. Seu aplicativo é responsável por processar tudo o que o usuário verá, portanto, é ainda mais importante manter uma taxa de atualização constante para que os usuários tenham uma experiência confortável.

## <a name="predicted-rendering-parameters"></a>Parâmetros de renderização previsto

Misto headsets realidade (HoloLens e fones imersivos em exposição) acompanhar continuamente a posição e orientação da cabeça do usuário em relação ao seu ambiente. Conforme seu aplicativo começa a preparar seu próximo quadro, o sistema prevê onde head do usuário será no futuro no exato momento em que o quadro serão exibidos nos vídeos. Com base nessa previsão, o sistema calculará as transformações de projeção e exibição a ser usado para esse quadro. Seu aplicativo **deve usar essas transformações para produzir resultados corretos**; se não forem usadas transformações fornecido pelo sistema, a imagem resultante não será alinhado com o mundo real, levando a discomfort do usuário.

Observe que para prever com precisão quando um novo quadro alcançará o exibe, o sistema está constantemente medindo a latência de ponta a ponta eficaz do pipeline de renderização do seu aplicativo. Enquanto o sistema irá se ajustar ao tamanho do seu pipeline de renderização, você pode melhorar ainda mais estabilidade holograma mantendo esse pipeline tão curtas quanto possível.

Aplicativos que usam técnicas avançadas para aumentar a previsão de sistema podem substituir as transformações de projeção e exibição do sistema. Esses aplicativos devem ainda devem usar transformações fornecido pelo sistema como base para suas transformações personalizadas para produzir resultados significativos.

## <a name="other-rendering-parameters"></a>Outros parâmetros de renderização

Durante a renderização de um quadro, o sistema especificará o visor back buffer no qual seu aplicativo deve ser desenhado. Esse visor geralmente será menor do que o tamanho total do buffer de quadro. Independentemente do tamanho do visor, depois que o quadro foi renderizado pelo aplicativo, o sistema irá aumentar a imagem para preencher todo o exibe.

Para aplicativos que não conseguem processar em que a taxa de atualização necessários, [parâmetros de renderização do sistema podem ser configurados](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) para reduzir a pressão de memória e/ou o custo de processamento às custas de suavização de aumento de pixel. O formato de buffer de fundo também pode ser alterado, que, para alguns aplicativos podem ajudar a melhorar a produtividade de pixel e largura de banda de memória.

O frustum de renderização, resolução e taxa de quadros no qual seu aplicativo é solicitado a renderizar também podem alterar o quadro a quadro e podem diferir entre os olhos de left e right. Por exemplo, quando [misto captura realidade](mixed-reality-capture.md) (MRC) está ativo e o [configuração de modo de exibição de câmera foto/vídeo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) não é aceito no, um olho pode ser renderizado com uma resolução ou FOV maiores.

Para qualquer dado de quadro, seu aplicativo *deve* renderizar usando a transformação de exibição, transformação de projeção e resolução de visor fornecido pelo sistema. Além disso, seu aplicativo nunca deve assumir que qualquer parâmetro de renderização/exibição permanece fixo do quadro a quadro. Mecanismos como o Unity tratar todas essas transformações para você em seus próprios objetos de câmera, para que o movimento físico dos seus usuários e o estado do sistema sempre seja respeitado. Se ainda mais seu aplicativo possibilita a movimentação de virtual do usuário por meio do mundo (por exemplo, usando o analógico em um gamepad), você pode adicionar um objeto pai do "equipamento" acima da câmera que move ao redor, fazendo com que a câmera refletir o movimento físico e virtual de ambas do usuário. Se seu aplicativo modifica a transformação de exibição, a transformação de projeção ou a dimensão de visor fornecido pelo sistema, ele deve informar o sistema chamando apropriado [substituir API](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose).

Para aprimorar a estabilidade da sua renderização holográfica, seu aplicativo deve fornecer ao Windows cada quadro-usado para renderizar o buffer de profundidade. Se seu aplicativo fornecer um buffer de profundidade, ele deve ter valores de profundidade coerente com profundidade expressa em metros da câmera. Isso permite que o sistema a usar seus dados de profundidade por pixel melhor se estabilizar conteúdo se head do usuário fica um pouco de deslocamento do local previsto. Se você não for capaz de fornecer seu buffer de profundidade, você deve em vez disso, fornecer um ponto de foco e normal, definindo um plano que Recorta a maioria do seu conteúdo. Se o buffer de profundidade e um plano de foco são fornecidos, o sistema pode usar ambos. Em particular, ele pode ser útil fornecer o buffer de profundidade e um ponto de foco que inclui um vetor de velocidade quando seu aplicativo é exibido hologramas que estão em movimento.

Para todos os detalhes de baixo nível aqui, confira a [processamento no DirectX](rendering-in-directx.md) artigo.

## <a name="holographic-cameras"></a>Câmeras holográfica

Windows Mixed Reality apresenta o conceito de um **câmera holográfica**. Câmeras holográfica são semelhantes à câmera tradicional encontrada em textos de gráficos em 3D: eles definem os dois o extrínsecos (posição e orientação) e propriedades da câmera intrínseco (ex: campo de visão) usado para exibir uma cena 3D virtual. Ao contrário de câmeras 3D tradicionais, o aplicativo não está no controle de posição, orientação e as propriedades intrínsecas da câmera. Em vez disso, a posição e orientação da câmera holográfica implicitamente é controlado pelo movimento do usuário. Movimento do usuário é retransmitido para o aplicativo em uma base quadro a quadro por meio de uma transformação de exibição. Da mesma forma, propriedades intrínsecas da câmera são definidas pela ótica de calibrada do dispositivo e de retransmissão do quadro a quadro via a transformação de projeção.

Em geral, seu aplicativo será ser renderização para uma única câmera estéreo. No entanto, um loop de renderização robusto deve dar suporte a vários câmeras e deve dar suporte a câmeras mono e estéreo. Por exemplo, o sistema pode solicitar que seu aplicativo para processar de uma perspectiva alternativa quando o usuário ativa um recurso semelhante [misto captura realidade](mixed-reality-capture.md) (MRC), dependendo da forma do fone de ouvido em questão. Aplicativos que dão suporte a vários câmeras obtêm-los [recusa no](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) para o [tipo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) das câmeras podem dar suporte.

## <a name="volume-rendering"></a>Renderização de volume

Durante a renderização de médicos MRI ou volumes em 3D, de engenharia [renderização de volume](volume-rendering.md) técnicas são usadas com frequência. Essas técnicas podem ser particularmente interessantes na realidade mista, em que os usuários podem exibir naturalmente tal um volume de ângulos de chave, simplesmente movendo suas cabeças.

## <a name="supported-resolutions-on-hololens-1st-gen"></a>Suporte a resoluções no HoloLens (1ª geração)
> [!NOTE]
> Haverá mais atualizações no futuro, este artigo. [Exibir a lista de atualização](release-notes-april-2018.md)

* As resoluções com suporte atuais e máxima são propriedades do [Exibir configuração](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). HoloLens é definido como a resolução máxima, o que é de 720p (1268 x 720), por padrão.
* O tamanho do mais baixo com suporte visor é 50% de 720p, que é 360p (634 x 360). No HoloLens, este é um ViewportScaleFactor de 0,5.
* Nada inferior à 540p é **não recomendável** devido à degradação visual, mas pode ser usado para identificar o bottle necks na taxa de preenchimento de pixel.

## <a name="supported-resolutions-on-hololens-2"></a>Resoluções com suporte em HoloLens 2

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).


## <a name="see-also"></a>Consulte também
* [Estabilidade do holograma](hologram-stability.md)
* [Como renderizar no DirectX](rendering-in-directx.md)