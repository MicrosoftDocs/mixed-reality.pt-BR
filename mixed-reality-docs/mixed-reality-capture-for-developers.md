---
title: Misto captura realidade para desenvolvedores
description: Práticas recomendadas para realidade misturada capturam para desenvolvedores.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: MRC, fotos, vídeo, captura, câmera
ms.openlocfilehash: c2d98baf16b2ea724247224aabadc1e2ca533ec1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589463"
---
# <a name="mixed-reality-capture-for-developers"></a>Misto captura realidade para desenvolvedores

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes). 

Ver [MRC habilitando em seu aplicativo](#enabling-mrc-in-your-app) abaixo para obter diretrizes sobre uma nova funcionalidade MRC para HoloLens 2.

Uma vez que um usuário pode levar uma [misto captura realidade](mixed-reality-capture.md) foto (MRC) ou o vídeo a qualquer momento, há algumas coisas que você deve ter em mente ao desenvolver seu aplicativo. Isso inclui as práticas recomendadas para uma qualidade visual MRC e sua capacidade de resposta a alterações do sistema enquanto MRCs estão sendo capturadas.

Os desenvolvedores podem integrar perfeitamente também captura realidade mista e inserção em seus aplicativos.

MRC no HoloLens (primeira geração) dá suporte a vídeos e fotos até 720p, enquanto MRC em HoloLens 2 dá suporte a vídeos até 1080p e fotos até a resolução de 4K.

## <a name="the-importance-of-quality-mrc"></a>A importância da qualidade MRC

Realidade misturada capturados fotos e vídeos provavelmente são a primeira exposição que um usuário terá de seu aplicativo. Se, como capturas de tela de realidade misturada em sua página da Microsoft Store ou de outros usuários de compartilhamento MRCs em redes sociais. Você pode usar MRC para seu aplicativo de demonstração, instrua os usuários, encorajar os usuários a compartilhar suas interações com mundo misto e para pesquisa de usuários e solução de problemas.

## <a name="how-mrc-impacts-your-app"></a>Como MRC afeta o seu aplicativo

### <a name="enabling-mrc-in-your-app"></a>Habilitar MRC em seu aplicativo

Por padrão, um aplicativo não precisa fazer nada para habilitar usuários a obter capturas de realidade misturada. No entanto, como o design do HoloLens 2 aumenta a distância entre a câmera de foto/vídeo (PV) e a exibição, incluiremos uma nova opção para produzir uma renderização de câmera 3ª alinhada com a câmera VP de **HoloLens 2**. 

Autorização de câmera 3ª renderizar em HoloLens 2 oferece os seguintes aperfeiçoamentos sobre a experiência MRC padrão:
* Alinhamento de holograma para seu ambiente físico e de mãos (para interações quase) deve ser preciso em todos os distâncias, em vez de ter um deslocamento em distâncias diferente do [concentre-se o ponto](focus-point-in-unity.md) como você pode ver no MRC padrão.
* O olho à direita o Headset não será comprometido, pois ele não será usado para renderizar as hologramas para a saída MRC.

### <a name="disabling-mrc-in-your-app"></a>Desabilitando MRC em seu aplicativo

Quando usa um aplicativo 2D [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx) ou [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx) para mostrar o conteúdo protegido com uma cadeia de troca configurado corretamente, o conteúdo do aplicativo visual será obscurecido automaticamente enquanto realidade misturada captura está em execução.

### <a name="knowing-when-mrc-is-active"></a>Sabendo quando MRC está ativa

O [AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx) classe pode ser usada por um aplicativo para saber quando o sistema misturadas captura realidade está em execução (para áudio ou vídeo).

>[!NOTE]
>Do AppCapture [GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) API pode retornar null se misturada captura realidade não está disponível no dispositivo. Também é importante cancelar o registro do evento de CapturingChanged quando seu aplicativo está suspenso, caso contrário, MRC pode entrar em um estado bloqueado.

### <a name="best-practices-hololens-specific"></a>Práticas recomendadas (específico do HoloLens)

MRC deve funcionar sem trabalho adicional de desenvolvedores, mas há algumas coisas a serem consideradas para fornecer uma experiência melhor de realidade misturada captura do seu aplicativo.

**MRC usa o canal alfa do holograma para combinar com o [câmera](locatable-camera.md) imagens**

A etapa mais importante é garantir que seu aplicativo está apagando para preto transparente, em vez de compensação para preto opaco. No Unity, isso é feito por padrão com o MixedRealityToolkit, mas se você estiver desenvolvendo no não Unity, você talvez precise fazer com que uma linha de uma alteração.

Aqui estão alguns dos artefatos que você pode ver em MRC se seu aplicativo não está limpando para preto transparente:

**Falhas de exemplo**: Preto bordas em torno do conteúdo (Falha ao limpar para preto transparente)

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**Falhas de exemplo**: A cena inteira do plano de fundo do holograma aparece em preta. Definir um valor de alfa de plano de fundo de 1 resulta em um plano de fundo preto

![Definir um valor de alfa de plano de fundo de 1 resulta em um plano de fundo preto](images/clearopaqueblack-300px.png)

**Resultado esperado**: Hologramas aparecem corretamente combinadas com o mundo real (resultado esperado se desmarcar para preto transparente)

![Resultado esperado se desmarcar para preto transparente](images/cleartransparentblack-300px.png)

**Solução**:
* Altere qualquer conteúdo que está aparecendo como preto opaco para ter um valor alfa de 0.
* Certifique-se de que o aplicativo está apagando para preto transparente.
* Padrões do Unity para limpar para limpar automaticamente com o MixedRealityToolkit, mas se ele for um aplicativo não Unity que você deve modificar a cor usada com ID3D11DeiceContext::ClearRenderTargetView(). Você deseja garantir que você desmarque para preto transparente (0,0,0,0) em vez do preto opaco (0,0,0,1).

Agora você pode ajustar os valores alfa de seus ativos, se você gostaria de ter, mas normalmente não é necessário. Na maioria das vezes, MRCs uma boas aparência fora da caixa. MRC pressupõe o alfa pré-multiplicado. Os valores alfa afetará apenas a captura MRC.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>O que esperar quando MRC está habilitada em HoloLens

O exemplo a seguir se aplicam a HoloLens (primeira geração) e 2 do HoloLens, a menos que indicado o contrário:

* O sistema limitará o aplicativo para a renderização de 30Hz. Isso cria alguns sobra para MRC ser executado para que o aplicativo não precisa manter uma reserva de orçamento constante e também corresponde a taxa de quadros MRC gravação de vídeo de 30fps
* Holograma conteúdo nos olhos correto do dispositivo poderá parecer "fagulhas" quando a gravação/streaming MRC: texto pode se tornar mais difícil de ler e bordas holograma pareça mais com bordas irregulares (autorização de câmera 3ª renderizar na **HoloLens 2** evita Esse comprometimento)
* MRC fotos e vídeos do aplicativo respeita [focar ponto](focus-point-in-unity.md) se o aplicativo tiver habilitado, que ajudará a garantir hologramas são posicionados com precisão. Para vídeos, o ponto de foco é suavizado, portanto, podem parecer hologramas descompasso lentamente no lugar, se a profundidade do ponto de foco for alterado significativamente. Hologramas que correm profundidades diferentes do ponto de foco podem aparecer deslocamento do mundo real (veja o exemplo abaixo onde o ponto de foco é definido no 2 metros mas holograma é posicionada no medidor de 1).

![Hologramas em 2 metros aparecerá perfeitamente registradas para o mundo. Hologramas distâncias fechar ou far podem Deslocar um pouco.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integrar a funcionalidade MRC de dentro de seu aplicativo

Seu aplicativo de realidade misturada pode iniciar foto MRC ou captura de vídeo de dentro do aplicativo, e o conteúdo capturado é disponibilizado para seu aplicativo sem ser armazenado para do dispositivo "rolo da câmera." Você pode criar um gravador MRC personalizado ou tirar proveito da captura de câmera interna da interface do usuário. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC com câmera interna da interface do usuário

Os desenvolvedores podem usar o *[API de interface do usuário de captura câmera](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* para obter uma foto de realidade misturada capturados pelo usuário ou um vídeo com apenas algumas linhas de código.

Essa API inicia a câmera MRC interna da interface do usuário, do qual o usuário pode tirar uma foto ou vídeo e retorna a captura resultante para seu aplicativo.  Se você quiser criar sua própria interface do usuário da câmera ou precisa de nível inferior acesso ao fluxo de captura, você pode criar um gravador de captura de realidade misturada personalizado.

### <a name="creating-a-custom-mrc-recorder"></a>Criar um gravador MRC personalizado

Enquanto o usuário sempre pode disparar uma foto ou capturar MRC vídeo usando o sistema de serviço, um aplicativo talvez queira criar um aplicativo de câmera personalizado, mas incluem hologramas no fluxo de câmera, assim como MRC. Isso permite que o aplicativo disparar capturas em nome do usuário, criar gravação de personalizados da interface do usuário ou personalizar as configurações de MRC para citar alguns exemplos.

**HoloStudio adiciona uma câmera MRC personalizada usando efeitos MRC**

![HoloStudio adiciona uma câmera MRC personalizada usando efeitos MRC](images/cameraiconholostudio-300px.jpg)

Aplicativos do Unity devem ver [Locatable_camera_in_Unity](locatable-camera-in-unity.md) para a propriedade para habilitar hologramas.

Outros aplicativos podem fazer isso usando o [APIs de captura de mídia do Windows](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) para controlar a câmera e adicionar um efeito de áudio e vídeo MRC para incluir hologramas virtuais e o áudio do aplicativo em vídeos e ainda pode.

Os aplicativos têm duas opções para adicionar o efeito:
* A API mais antiga: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)
* O novo Microsoft recomendável API (retorna um objeto, tornando possível manipular as propriedades dinâmicas): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) que exige que o aplicativo criar sua própria implementação do [IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx) e [IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx). Consulte o exemplo de efeito MRC para exemplo de uso.

(Observe que esses namespaces não serão reconhecidos pelo Visual Studio, mas as cadeias de caracteres ainda são válidas)

O efeito de vídeo MRC (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  Nome da propriedade  |  Tipo  |  Valor padrão  |  Descrição | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))  |  1 (VideoRecord)  |  Descreva esse efeito é usado para qual fluxo de captura. Áudio não está disponível. | 
|  HologramCompositionEnabled  |  booliano  |  TRUE  |  Sinalizador para habilitar ou desabilitar hologramas na captura de vídeo. | 
|  RecordingIndicatorEnabled  |  booliano  |  TRUE  |  Sinalizador para habilitar ou desabilitar o indicador de gravação na tela durante a captura de holograma. | 
|  VideoStabilizationEnabled  |  booliano  |  FALSE  |  Sinalizador para habilitar ou desabilitar a estabilização do vídeo alimentada pelo controlador de HoloLens. | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Defina o número de quadros de histórico é usado para a estabilização do vídeo. 0 é a latência de 0 e quase "gratuito" de uma perspectiva de capacidade e desempenho. 15 é recomendado para a mais alta qualidade (às custas de 15 quadros de latência e a memória). | 
|  GlobalOpacityCoefficient  |  flutuante  |  0.9 (HoloLens) 1.0 (fone de ouvido imersivo)  |  Definir coeficiente de opacidade global de holograma no intervalo de 0,0 (totalmente transparente) a 1.0 (completamente opaco). | 
|  BlankOnProtectedContent  |  booliano  |  FALSE  |  Sinalizador para habilitar ou desabilitar retornando um quadro vazio se não houver um conteúdo mostrando de aplicativo UWP protegido 2d. Se esse sinalizador é false e um 2d aplicativo da UWP é mostrando protegido conteúdo, que o aplicativo UWP 2d será substituído por uma textura de conteúdo protegida no fone de ouvido e na captura de realidade misturada. |
|  ShowHiddenMesh  |  booliano  |  FALSE  |  Sinalizador para habilitar ou desabilitar mostrando a malha de área oculto da câmera holográfica e os vizinhos de conteúdo. |

O efeito de áudio MRC (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>Nome da propriedade</th>
<th>Tipo</th>
<th>Valor padrão</th>
<th>Descrição</th>
</tr>
<tr>
<td>MixerMode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>0 : Somente o áudio do microfone</li>
<li>1 : Somente o áudio do sistema</li>
<li>2 : MIC e áudio do sistema</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>Limitações de MRC simultâneas

Há algumas limitações em torno de vários aplicativos acessando MRC ao mesmo tempo.

#### <a name="photovideo-camera-access"></a>Acesso à câmera de vídeo/foto

A câmera de vídeo/foto é limitada ao número de processos que podem acessá-lo ao mesmo tempo. Enquanto um processo está gravando vídeo ou tirar uma foto em qualquer outro processo irá falhar adquirir a câmera de vídeo/foto. (isso se aplica a captura de realidade mista e captura de foto padrão/vídeo)

Com o Windows 10 de abril de 2018 atualização, essa restrição não se aplica a câmera MRC interna da interface do usuário é usada para tirar uma foto ou um vídeo, depois que um aplicativo tiver começado a usar a câmera de vídeo/foto. Quando isso acontece, a resolução e taxa de quadros da câmera MRC interna da interface do usuário podem ser reduzidos de seus valores de normais.

Com o Windows 10 de outubro de 2018 atualização, essa restrição não se aplica para streaming MRC pela Miracast.

#### <a name="mrc-access"></a>Acesso MRC

Com o Windows 10 de abril de 2018 Update, não há uma limitação em torno de vários aplicativos acessando o fluxo MRC (no entanto, o acesso à câmera foto/vídeo ainda tem limitações).

Anteriores ao Windows 10 de abril de 2018 gravador MRC personalizado de um aplicativo, a atualização foi mutuamente exclusiva com o sistema MRC (captura de fotos, vídeos de captura ou fluxo com o Windows Device Portal).

## <a name="see-also"></a>Consulte também
* [Captura de realidade misturada](mixed-reality-capture.md)
* [Modo de exibição spectator](spectator-view.md)
