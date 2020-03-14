---
title: Captura de realidade misturada para desenvolvedores
description: Práticas recomendadas para captura de realidade misturada para desenvolvedores.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: MRC, foto, vídeo, captura, câmera
ms.openlocfilehash: 72600f889997c96a629faebc35aba4b4841d4d8b
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375963"
---
# <a name="mixed-reality-capture-for-developers"></a>Captura de realidade misturada para desenvolvedores

> [!NOTE]
> Confira [renderizar da câmera VP](#render-from-the-pv-camera-opt-in) abaixo para obter orientação sobre um novo recurso da MRC para o HoloLens 2.

Como um usuário poderia pegar uma foto ou vídeo da MRC ( [captura de realidade misturada](mixed-reality-capture.md) ) a qualquer momento, há algumas coisas que você deve ter em mente ao desenvolver seu aplicativo. Isso inclui as práticas recomendadas para a qualidade visual da MRC e a resposta a alterações do sistema enquanto os MRCs estão sendo capturados.

Os desenvolvedores também podem integrar diretamente a captura e a inserção da realidade misturada em seus aplicativos.

A MRC no HoloLens (primeira geração) dá suporte a vídeos e fotos de até 720p, enquanto a MRC no HoloLens 2 dá suporte a vídeos de até 1080p e fotos de até 4K de resolução.

## <a name="the-importance-of-quality-mrc"></a>A importância da qualidade da MRC

A realidade misturada fotos capturadas e vídeos é provavelmente a primeira exposição que um usuário terá de seu aplicativo. Seja como capturas de tela de realidade misturadas na sua página de Microsoft Store ou de outros usuários que compartilham MRCs em redes sociais. Você pode usar a MRC para demonstrar seu aplicativo, instruir os usuários, incentivar os usuários a compartilharem suas interações do mundo misto e para a solução de problemas e pesquisa de usuários.

## <a name="how-mrc-impacts-your-app"></a>Como a MRC impacta seu aplicativo

### <a name="enabling-mrc-in-your-app"></a>Habilitando a MRC em seu aplicativo

Por padrão, um aplicativo não precisa fazer nada para permitir que os usuários façam capturas de realidade misturada.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Habilitando o alinhamento aprimorado para a MRC em seu aplicativo

Por padrão, a captura de realidade mista combina a saída de Holographic do olho direito com a câmera de foto/vídeo (VP). Essas duas fontes são combinadas usando o ponto de foco definido pelo aplicativo de imersão em execução no momento.

Isso significa que os hologramas fora do plano de foco também não serão alinhados (devido à distância física entre a câmera PV e a exibição correta).

#### <a name="set-the-focus-point"></a>Definir o ponto de foco

Aplicativos de imersão (no HoloLens) devem definir o [ponto de foco](focus-point-in-unity.md) de onde deseja que seu plano de estabilização seja. Isso garante o melhor alinhamento no headset e na captura de realidade misturada.

Se um ponto de foco não estiver definido, o plano de estabilização usará como padrão dois medidores.

#### <a name="render-from-the-pv-camera-opt-in"></a>Renderizar da câmera PV (aceitar)

O HoloLens 2 adiciona a capacidade de um aplicativo de imersão **renderizar da câmera VP** enquanto a captura de realidade misturada está em execução. Para garantir que o aplicativo dê suporte à renderização adicional corretamente, o aplicativo precisa aceitar essa funcionalidade.

A renderização da câmera PV oferece as seguintes melhorias em relação à experiência padrão da MRC:
* O alinhamento do holograma ao ambiente físico e às mãos (para interações próximas) deve ser preciso em todas as distâncias, em vez de ter um deslocamento em distâncias que não seja o ponto de foco, como você pode ver na MRC padrão.
* O olho certo no headset não será comprometido, pois ele não será usado para renderizar os hologramas da saída da MRC.

Há três etapas para habilitar a renderização da câmera PV:
1. Habilitar PhotoVideoCamera HolographicViewConfiguration
2. Manipular a renderização HolographicCamera adicional
3. Verifique se os sombreadores e o código são renderizados corretamente deste HolographicCamera adicional

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a>Habilitar PhotoVideoCamera HolographicViewConfiguration

Para aceitar, um aplicativo simplesmente habilita o [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)do PhotoVideoCamera:
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Manipular a renderização HolographicCamera adicional no DirectX

Quando o aplicativo tem consentimento para renderizar da câmera PV e a captura de realidade misturada começa:
1. O evento CameraAdded de HolographicSpace será acionado. Esse evento pode ser adiado se o aplicativo não puder lidar com a câmera no momento.
2. Depois que o evento for concluído (e não houver adiamentos pendentes), o HolographicCamera será exibido na lista de AddedCameras do próximo HolographicFrame.

Quando a captura de realidade misturada for interrompida (ou se o aplicativo desabilitar a configuração de exibição enquanto a captura da realidade misturada estiver em execução): o HolographicCamera aparecerá na lista de RemovedCameras do próximo HolographicFrame e o evento CameraRemoved do HolographicSpace será ativar.

Uma propriedade [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) foi adicionada a HolographicCamera para ajudar a identificar a configuração à qual uma câmera pertence.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Manipular o processamento de HolographicCamera adicional no Unity

>[!NOTE]
> O suporte do Unity para renderização da câmera PV está em desenvolvimento e não pode ser usado ainda. Esta documentação será atualizada quando um Build do Unity com suporte para renderização da câmera PV estiver disponível.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Verifique se os sombreadores e o código dão suporte a câmeras adicionais

Execute uma captura de realidade misturada e verifique o alinhamento incomum, o conteúdo ausente ou os problemas de desempenho. Atualize os sombreadores e o código conforme apropriado.

Se houver certas cenas que não dão suporte à renderização em uma câmera adicional, você poderá desabilitar o HolographicViewConfiguration do PhotoVideoCamera durante eles.

### <a name="disabling-mrc-in-your-app"></a>Desabilitando a MRC em seu aplicativo

#### <a name="2d-app"></a>aplicativo 2D

os aplicativos 2D podem optar por ter seu conteúdo Visual obscuro quando a captura de realidade misturada está em execução por:
* Presente com o sinalizador de [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)
* Criar a cadeia de permuta do aplicativo com o sinalizador [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)
* Com a atualização do Windows 10 de maio de 2019, configurando o [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) da ApplicationView

#### <a name="immersive-app"></a>Aplicativo de imersão

Aplicativos de imersão podem optar por ter seu conteúdo Visual excluído da captura de realidade misturada por:
* Definindo [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) de HolographicCameraRenderingParameter para desabilitar a captura de realidade misturada para seu quadro associado
* Definindo [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) de HolographicCamera para desabilitar a captura de realidade misturada para sua câmera Holographic associada

#### <a name="password-keyboard"></a>Teclado de senha

Com a atualização do Windows 10 de maio de 2019, o conteúdo do Visual é excluído automaticamente da captura de realidade misturada quando um teclado de senha ou PIN está visível.

### <a name="knowing-when-mrc-is-active"></a>Sabendo quando a MRC está ativa

A classe [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) pode ser usada por um aplicativo para saber quando a captura de realidade misturada do sistema está em execução (para áudio ou vídeo).

>[!NOTE]
>A API [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) do AppCapture poderá retornar NULL se a captura da realidade misturada não estiver disponível no dispositivo. Também é importante cancelar o registro do evento Capturechanged quando seu aplicativo é suspenso; caso contrário, a MRC pode entrar em um estado bloqueado.

### <a name="best-practices-hololens-specific"></a>Práticas recomendadas (específicas do HoloLens)

Espera-se que a MRC funcione sem trabalho adicional dos desenvolvedores, mas há algumas coisas que você deve conhecer para fornecer a melhor experiência de captura de realidade misturada de seu aplicativo.

**A MRC usa o canal alfa do holograma para misturar com as imagens da [câmera](locatable-camera.md)**

A etapa mais importante é garantir que seu aplicativo esteja apagando para preto transparente em vez de limpá-lo em preto opaco. No Unity, isso é feito por padrão com o MixedRealityToolkit, mas se você estiver desenvolvendo em não Unity, talvez seja necessário fazer uma alteração de uma linha.

Aqui estão alguns dos artefatos que você poderá ver na MRC se seu aplicativo não estiver sendo desmarcado para preto transparente:

**Falhas de exemplo**: bordas pretas em todo o conteúdo (falha ao apagar para preto transparente)

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

**Falhas de exemplo**: toda a cena em segundo plano do holograma aparece em preto. A definição de um valor alfa de segundo plano de 1 resulta em um plano de fundo preto

![A definição de um valor alfa de segundo plano de 1 resulta em um plano de fundo preto](images/clearopaqueblack-300px.png)

**Resultado esperado**: os hologramas aparecem corretamente mesclados com o mundo real (resultado esperado se estiver desmarcando para preto transparente)

![Resultado esperado se estiver desmarcando para preto transparente](images/cleartransparentblack-300px.png)

**Solução**:
* Altere qualquer conteúdo que esteja aparecendo como preto opaco para ter um valor alfa igual a 0.
* Verifique se o aplicativo está apagando para preto transparente.
* O Unity usa como padrão limpar automaticamente o MixedRealityToolkit, mas se for um aplicativo não-Unity, você deverá modificar a cor usada com ID3D11DeiceContext:: ClearRenderTargetView (). Você deseja garantir que fique claro para preto transparente (0, 0, 0, 0) em vez de preto opaco (0, 0, 0, 1).

Agora você pode ajustar os valores Alfa de seus ativos, se desejar, mas normalmente não precisa. Na maioria das vezes, o MRCs parecerá bom para uso. A MRC pressupõe uma alfa multiplicada previamente. Os valores Alfa afetarão apenas a captura da MRC.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>O que esperar quando a MRC está habilitada no HoloLens

O seguinte se aplica ao HoloLens (primeira geração) e ao HoloLens 2, a menos que indicado de outra forma:

* O sistema limitará o aplicativo para a renderização 30Hz. Isso cria algum espaço para que a MRC seja executada para que o aplicativo não precise manter uma reserva de orçamento constante e também corresponda à taxa de quadros de registro de vídeo da MRC de 30fps
* O conteúdo de holograma no olho certo do dispositivo pode parecer "Sparkle" ao gravar/transmitir a MRC: o texto pode ser mais difícil de ler e as bordas do holograma podem parecer mais Jaggy (aceitar a 3ª câmera renderizar no **HoloLens 2** evita esse comprometimento)
* Os vídeos e fotos da MRC respeitarão o [ponto de foco](focus-point-in-unity.md) do aplicativo se o aplicativo o tiver habilitado, o que ajudará a garantir que os hologramas sejam posicionados com precisão. Para vídeos, o ponto de foco é suavizado, de modo que os hologramas podem parecer descompassos mais lentamente se a profundidade do ponto de foco muda significativamente. Os hologramas que estão em diferentes profundidades do ponto de foco podem parecer deslocamento do mundo real (Veja o exemplo abaixo, em que ponto de foco está definido em 2 metros, mas o holograma está posicionado em 1 metro).

![Os hologramas a 2 metros serão exibidos perfeitamente registrados no mundo. Os hologramas em distâncias próximas ou distantes podem ser um deslocamento ligeiramente.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integrando a funcionalidade da MRC de dentro de seu aplicativo

Seu aplicativo de realidade misturada pode iniciar a captura de vídeo ou foto da MRC de dentro do aplicativo, e o conteúdo capturado é disponibilizado para seu aplicativo sem ser armazenado no "rolo de câmera" do dispositivo. Você pode criar um gravador da MRC personalizado ou aproveitar a interface do usuário de captura de câmera interna. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC com interface do usuário da câmera interna

Os desenvolvedores podem usar a *[API da interface do usuário de captura de câmera](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* para obter uma foto ou vídeo de realidade misturada do usuário com apenas algumas linhas de código.

Essa API inicia a interface do usuário da câmera da MRC interna, da qual o usuário pode tirar uma foto ou um vídeo, e retorna a captura resultante para seu aplicativo.  Se você quiser criar sua própria interface do usuário da câmera ou precisar de acesso de nível inferior ao fluxo de captura, poderá criar um gravador de captura de realidade misturada personalizado.

### <a name="creating-a-custom-mrc-recorder"></a>Criando um gravador da MRC personalizado

Embora o usuário sempre possa disparar uma foto ou vídeo usando o serviço de captura de MRC do sistema, um aplicativo pode querer criar um aplicativo de câmera personalizado, mas incluir hologramas no fluxo da câmera, assim como a MRC. Isso permite que o aplicativo inicie capturas em nome do usuário, crie uma interface de usuário de gravação personalizada ou personalize as configurações da MRC para citar alguns exemplos.

**HoloStudio adiciona uma câmera da MRC personalizada usando efeitos da MRC**

![HoloStudio adiciona uma câmera da MRC personalizada usando efeitos da MRC](images/cameraiconholostudio-300px.jpg)

Os aplicativos do Unity devem ver [Locatable_camera_in_Unity](locatable-camera-in-unity.md) para a propriedade para habilitar os hologramas.

Outros aplicativos podem fazer isso usando as [APIs de captura de mídia do Windows](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) para controlar a câmera e adicionar um efeito de vídeo e áudio da MRC para incluir hologramas virtuais e áudio do aplicativo nos vídeos e continuas.

Os aplicativos têm duas opções para adicionar o efeito:
* A API mais antiga: [Windows. Media. Capture. MediaCapture. AddEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* A nova API recomendada da Microsoft (retorna um objeto, possibilitando a manipulação de propriedades dinâmicas): [Windows. Media. Capture. MediaCapture. AddVideoEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows. Media. Capture. MediaCapture. AddAudioEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) que exige que o aplicativo Crie sua própria implementação de [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) e [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition). Consulte o exemplo de efeito da MRC para uso de exemplo.

>[!NOTE]
> O namespace Windows. Media. MixedRealityCapture não será reconhecido pelo Visual Studio, mas as cadeias de caracteres ainda são válidas.

Efeito de vídeo da MRC (**Windows. Media. MixedRealityCapture. MixedRealityCaptureVideoEffect**)

|  Nome da Propriedade  |  Tipo  |  Valor padrão  |  Descrição | 
|----------|----------|----------|----------|
|  Streamtype  |  UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  Descreva para qual fluxo de captura esse efeito é usado. O áudio não está disponível. | 
|  HologramCompositionEnabled  |  booliano  |  TRUE  |  Sinalizador para habilitar ou desabilitar hologramas na captura de vídeo. | 
|  RecordingIndicatorEnabled  |  booliano  |  TRUE  |  Sinalizador para habilitar ou desabilitar o indicador de gravação na tela durante a captura de holograma. | 
|  VideoStabilizationEnabled  |  booliano  |  FALSE  |  Sinalizador para habilitar ou desabilitar a estabilização de vídeo da plataforma do controlador de HoloLens. | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Defina quantos quadros históricos são usados para estabilização de vídeo. 0 é a latência e quase "livre" de uma perspectiva de potência e desempenho. 15 é recomendado para a qualidade mais alta (com o custo de 15 quadros de latência e memória). | 
|  GlobalOpacityCoefficient  |  float  |  0,9 (HoloLens) 1,0 (Headset de imersão)  |  Defina o coeficiente de opacidade global de holograma no intervalo de 0,0 (totalmente transparente) para 1,0 (totalmente opaco). | 
|  BlankOnProtectedContent  |  booliano  |  FALSE  |  Sinalizador para habilitar ou desabilitar o retorno de um quadro vazio se houver um aplicativo UWP 2D mostrando o conteúdo protegido. Se esse sinalizador for false e um aplicativo UWP 2D estiver mostrando o conteúdo protegido, o aplicativo UWP 2D será substituído por uma textura de conteúdo protegida no headset e na captura da realidade misturada. |
|  ShowHiddenMesh  |  booliano  |  FALSE  |  Sinalizador para habilitar ou desabilitar mostrando a malha da área oculta da câmera Holographic e o conteúdo vizinho. |
| Sobrecolocações | Size | 0, 0 | Defina o tamanho de saída desejado após o corte para estabilização de vídeo. Um tamanho de corte padrão será escolhido se 0 ou um tamanho de saída inválido for especificado. |
| PreferredHologramPerspective | UINT32 | 1 (PhotoVideoCamera) | Enumeração usada para indicar qual configuração de exibição de câmera Holographic deve ser capturada. Definir 0 (display) significa que o aplicativo não será solicitado a renderizar da câmera de foto/vídeo |

Efeito de áudio da MRC (**Windows. Media. MixedRealityCapture. MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>Nome da Propriedade</th>
<th>Tipo</th>
<th>Valor padrão</th>
<th>Descrição</th>
</tr>
<tr>
<td>Mixermode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>0: somente áudio do MIC</li>
<li>1: somente áudio do sistema</li>
<li>2: MIC e áudio do sistema</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>Limitações de MRC simultâneas

Há certas limitações em relação a vários aplicativos que acessam a MRC ao mesmo tempo.

#### <a name="photovideo-camera-access"></a>Acesso à câmera de foto/vídeo

A câmera de foto/vídeo é limitada ao número de processos que podem acessá-lo ao mesmo tempo. Enquanto um processo estiver gravando vídeo ou tirando uma foto, qualquer outro processo falhará ao adquirir a câmera de foto/vídeo. (isso se aplica a captura de realidade mista e captura de foto/vídeo padrão)

Com o HoloLens 2, um aplicativo pode usar a propriedade ' [sharingmode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) de MediaCaptureInitializationSettings para indicar que deseja executar SharedReadOnly se não precisar de controle exclusivo sobre a câmera de foto/vídeo. Isso significa que a resolução e a taxa de quadros da captura serão limitadas a quais outros aplicativos configuraram a câmera para fornecer.

##### <a name="built-in-mrc-photovideo-camera-access"></a>Acesso interno à câmera de fotos/vídeo da MRC

Funcionalidade da MRC incorporada ao Windows 10 (via Cortana, menu Iniciar, atalhos de hardware, Miracast, portal de dispositivos Windows):
* Será executado com ExclusiveControl por padrão

No entanto, o suporte foi adicionado a cada subsistema para operar em um modo compartilhado:
* Se um aplicativo solicitar acesso ExclusiveControl à câmera de foto/vídeo, a MRC interna interromperá automaticamente o uso da câmera de foto/vídeo para que a solicitação do aplicativo seja realizada com sucesso
* Se a MRC interna for iniciada enquanto um aplicativo tiver ExclusiveControl, a MRC interna será executada no modo SharedReadOnly

Essa funcionalidade de modo compartilhado tem determinadas restrições:
* Foto via Cortana, atalhos de hardware ou menu iniciar: requer a atualização do Windows 10 de abril de 2018 (ou posterior)
* Vídeo via Cortana, atalhos de hardware ou menu iniciar: requer a atualização do Windows 10 de abril de 2018 (ou posterior)
* Streaming de MRC sobre Miracast: requer a atualização do Windows 10 de outubro de 2018 (ou posterior)
* Streaming de MRC no portal de dispositivo do Windows ou por meio do aplicativo de complemento do HoloLens: requer o HoloLens 2

>[!NOTE]
> A resolução e a taxa de quadros da interface do usuário da câmera da MRC interna podem ser reduzidas de seus valores normais quando outro aplicativo estiver usando a câmera de foto/vídeo.

#### <a name="mrc-access"></a>Acesso da MRC

Com a atualização do Windows 10 de abril de 2018, não há mais uma limitação em relação a vários aplicativos que acessam o fluxo da MRC (no entanto, o acesso à câmera de foto/vídeo ainda tem limitações).

Anterior à atualização de abril de 2018 do Windows, o gravador da MRC personalizada de um aplicativo era mutuamente exclusivo com o sistema da MRC (capturando fotos, capturando vídeos ou transmitindo do portal de dispositivos do Windows).

## <a name="see-also"></a>Consulte também
* [Captura de realidade misturada](mixed-reality-capture.md)
* [Modo de exibição Espectador](spectator-view.md)
