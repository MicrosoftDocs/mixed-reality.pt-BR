---
title: Câmera localizáveis
description: Informações gerais sobre a câmera frontal HoloLens, como ele funciona e os perfis e as resoluções disponíveis para desenvolvedores.
author: cdedmonds
ms.author: wguyman, cdedmonds
ms.date: 06/12/2019
ms.topic: article
keywords: câmera, hololens, câmera de cor, voltadas para, hololens, 2, VC, pesquisa Visual computacional, fiducial frente, marcadores, código qr, qr, fotos, vídeo
ms.openlocfilehash: b80e201723f8f499a6d35008b9d308f93b925b1c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694532"
---
# <a name="locatable-camera"></a>Câmera localizáveis

HoloLens incluem uma câmera voltados para o mundo montada na parte frontal do dispositivo que permite que os aplicativos ver o que o usuário vê. Os desenvolvedores têm acesso e controle da câmera, assim como fariam para câmeras de cor em smartphones, computadores portáteis ou áreas de trabalho. O mesmo windows universal [captura de mídia](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) e funcionam de APIs que funcionam em dispositivos móveis e área de trabalho de base de mídia do windows em HoloLens. Unity [também foi quebrada essa APIs do windows](locatable-camera-in-unity.md) abstrair o simple uso da câmera em HoloLens para tarefas como levando regulares fotos e vídeos (com ou sem hologramas) e localizar a posição da câmera no e perspectiva sobre o cena.

## <a name="device-camera-information"></a>Informações de câmera do dispositivo

### <a name="hololens-first-generation"></a>HoloLens (first-generation)

* Câmera de foto/vídeo (PV) foco fixo com o balanço automático branca, exposição automática e pipeline de processamento de imagem completa.
* LED de privacidade em branco voltados para o mundo acenderá sempre que a câmera está ativa
* A câmera suporta os seguintes modos (todos os modos são a taxa de proporção de 16:9) em 5 de fps, 24, 20, 15 e 30:

  |  Vídeo  |  Visualizar  |  Ainda  |  Campo de exibição horizontal (H-FOV) |  Uso sugerido | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  (modo de padrão com estabilização do vídeo) | 
  |  N/D |  N/D |  2048x1152 |  67deg |  Imagem estática de resolução mais alta | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  Excedem resolução (preenchimento) antes de estabilização do vídeo | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  Modo de vídeo de FOV grande com overscan | 
  |  896x504 |  896x504 |  896x504 |  48deg |  Baixa energia / tarefas de processamento de modo de baixa resolução de imagem | 

### <a name="hololens-2"></a>HoloLens 2

* Câmera de foto/vídeo (PV) foco automático com o balanço automático branca, exposição automática e pipeline de processamento de imagem completa.
* LED de privacidade em branco voltados para o mundo acenderá sempre que a câmera está ativa.
* HoloLens 2 dá suporte a perfis de câmera diferente. Saiba como [descobrir e selecionar recursos de câmera](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles).
* A câmera suporta os seguintes perfis e resoluções (todos os modos de vídeos são a taxa de proporção de 16:9):
  
  | Perfil                                         | Vídeo     | Visualizar   | Ainda     | Taxas de quadros | Campo de exibição horizontal (H-FOV) | Uso sugerido                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy,0  BalancedVideoAndPhoto,100             | 2272x1278 | 2272x1278 |           | 15,30       | 64.69                            | Gravação de vídeo de alta qualidade                |
  | Legacy,0  BalancedVideoAndPhoto,100             | 896x504   | 896x504   |           | 15,30       | 64.69                            | Fluxo de visualização para a captura de foto de alta qualidade |
  | Legacy,0  BalancedVideoAndPhoto,100             |           |           | 3904x2196 |             | 64.69                            | Captura de fotos de alta qualidade                  |
  | BalancedVideoAndPhoto,120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15,30       | 64.69                            | Cenários de longa duração                     |
  | BalancedVideoAndPhoto,120                       | 1504x846  | 1504x846  |           | 15,30       | 64.69                            | Cenários de longa duração                     |
  | Videoconferência, 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | Conferência de vídeo, cenários de longa duração |
  | Videoconferência, 100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | Conferência de vídeo, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | Conferência de vídeo, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1280x720  | 1280x720  | 1280x720  | 15,30       | 64.69                            | Conferência de vídeo, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1128x636  |           |           | 15,30       | 64.69                            | Conferência de vídeo, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 960 x 540   |           |           | 15,30       | 64.69                            | Conferência de vídeo, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 760x428   |           |           | 15,30       | 64.69                            | Conferência de vídeo, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 640x360   |           |           | 15,30       | 64.69                            | Conferência de vídeo, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 500x282   |           |           | 15,30       | 64.69                            | Conferência de vídeo, cenários de longa duração |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 424x240   |           |           | 15,30       | 64.69                            | Conferência de vídeo, cenários de longa duração |

>[!NOTE]
>Os clientes podem aproveitar [misto captura realidade](mixed-reality-capture.md) para tirar fotos do seu aplicativo, que incluem hologramas e estabilização de vídeo ou vídeos.
>
>Como desenvolvedor, há considerações que você deve levar em conta ao criar seu aplicativo, se você deseja que ele ser tão bom quanto possível quando um cliente captura o conteúdo. Você pode também habilitar (e personalizar) captura de realidade mista de dentro de seu aplicativo. Saiba mais em [misto captura realidade para os desenvolvedores](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Localizando a câmera do dispositivo no mundo

Quando houver HoloLens fotos e vídeos, os quadros capturados incluem o local da câmera no mundo, bem como o modelo de lentes da câmera. Isso permite que aplicativos raciocinar sobre a posição da câmera no mundo real para cenários de geração de imagens aumentados. Os desenvolvedores poderão ser revertidas criativamente seus próprios cenários usando seu processamento de imagens favorito ou bibliotecas de visão personalizada do computador.

"Câmera" em outro lugar na documentação do HoloLens pode se referir a "jogo câmera virtual" (o aplicativo frustum renderiza o). A menos que indicado o contrário, "câmera" nesta página refere-se a câmera de cor RGB do mundo real.

Os detalhes sobre essa cobertura da página usando o [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference) classe, no entanto, há também as APIs para intrínsecos de câmera de pull e locais usando [Media Foundation atributos](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx). Consulte a [holográfica face acompanhamento exemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) para obter mais informações.

### <a name="images-with-coordinate-systems"></a>Imagens com sistemas de coordenadas

Cada quadro da imagem (se foto ou vídeo) inclui um [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) enraizada na câmera no momento da captura que pode ser acessado usando o [CoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) propriedade de seu [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference). Além disso, cada quadro contém uma descrição do modelo de Lente de câmera que pode ser encontrada na [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) propriedade. Juntas, essas transformações definem para cada pixel um raio no espaço 3D, que representa o caminho tomada pelos photons que produziu o pixel. Esses raios podem estar relacionados a outro conteúdo no aplicativo Obtendo a transformação do sistema de coordenadas do quadro para algum outro sistema de coordenadas (por exemplo, de um [quadro estacionário de referência](coordinate-systems.md#stationary-frame-of-reference)). Para resumir, cada quadro da imagem fornece o seguinte:
* Dados de pixel (no formato RGB/NV12/JPEG/etc.)
* Um [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) do local de captura
* Um [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) classe que contém o modo de lentes da câmera

### <a name="camera-to-application-specified-coordinate-system"></a>Câmera para o sistema de coordenadas especificado pelo aplicativo

Para ir do 'CameraIntrinsics' e 'CameraCoordinateSystem' para o seu sistema de coordenadas de mundo/aplicativo, você precisará do seguinte:

[Localizáveis câmera no Unity](locatable-camera-in-unity.md): CameraToWorldMatrix é fornecida automaticamente pela classe PhotoCaptureFrame (de modo que você não precisa se preocupar sobre as transformações CameraCoordinateSystem).

[Câmera localizáveis no DirectX](locatable-camera-in-directx.md): Mostra a maneira bastante simples de consulta para a transformação entre o sistema de coordenadas da câmera e coordinate system(s) seu próprio aplicativo.

### <a name="distortion-error"></a>Erro de distorção

Em HoloLens, o vídeo e os fluxos de imagem ainda estão sem distorção no pipeline de processamento de imagem do sistema antes dos quadros são disponibilizados para o aplicativo (o fluxo de visualização contém os quadros distorcidos originais). Porque somente os CameraIntrinsics são disponibilizados, aplicativos devem assumir que representam de quadros de imagem uma câmera pinhole perfeito, no entanto o undistortion funcionar no processador de imagem pode ainda deixar um erro de até 10 pixels em HoloLens (primeira geração) ao usar o CameraIntrinsics nos metadados do quadro. Em muitos casos de uso, esse erro não será relevante, mas se alinhando hologramas para cartazes/marcadores do mundo real, por exemplo, e você notar um < 10px deslocamento (aproximadamente 11mm para hologramas posicionado 2 metros de distância) essa distorção erro poderia ser a causa. 

## <a name="locatable-camera-usage-scenarios"></a>Cenários de uso de câmera localizáveis

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Mostrar uma foto ou vídeo no mundo em que ele foi capturado

Os quadros de câmera do dispositivo vem com uma transformação "Câmera para World", que pode ser usada para mostrar onde o dispositivo foi exatamente quando a imagem foi capturada. Por exemplo, você pode posicionar um pequeno ícone holográfico neste local (CameraToWorld.MultiplyPoint(Vector3.zero)) e draw até mesmo uma pequena seta na direção que a câmera enfrentava (CameraToWorld.MultiplyVector(Vector3.forward)).

### <a name="tag--pattern--poster--object-tracking"></a>Marca / padrão / pôster / acompanhamento de objeto

Muitos aplicativos de realidade misturada usam uma imagem reconhecível ou padrão visual para criar um ponto controláveis no espaço. Em seguida, isso é usado para processar objetos em relação ao que apontam ou criar um local conhecido. Alguns usos para o HoloLens incluem Localizando um objeto do mundo real marcado com fiducials (por exemplo, um monitor de TV com um código QR), colocando hologramas sobre fiducials e visualmente emparelhamento com dispositivos não HoloLens, como tablets que foram configurados para se comunicar com o HoloLens por meio de Wi-Fi.

Para reconhecer um padrão visual e, em seguida, colocar esse objeto no espaço de mundo de aplicativos, você precisará de algumas coisas:
1. Uma imagem padrão reconhecimento Kit de ferramentas, como o código QR, marcas de AR, o localizador de face, rastreadores de círculo, OCR etc.
2. Colete os quadros de imagem em tempo de execução e passá-los para a camada de reconhecimento
3. Unproject suas imagens locais de volta ao posições do mundo ou raios do mundo provavelmente. Consulte
4. Posicione os modelos de virtuais sobre esses locais do mundo

Alguns links de processamento de imagem importantes:
* [OpenCV](http://opencv.org/)
* [QR marcas](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Manter uma taxa de quadros do aplicativo interativo é fundamental, especialmente ao lidar com os algoritmos de reconhecimento de imagem de longa execução. Por esse motivo que nós geralmente usamos o seguinte padrão:
1. Thread principal: gerencia o objeto de câmera
2. Thread principal: solicitações novos quadros (assíncrono)
3. Thread principal: passar novos quadros para controle de thread
4. Controle de Thread: imagem de processos coletar pontos-chave
5. Thread principal: move o modelo virtual para corresponder ao encontra pontos-chave
6. Thread principal: repita a etapa 2

Alguns sistemas de marcador da imagem apenas fornecem um local de pixel único (outros fornecem a transformação completa nesse caso, esta seção não será necessário), que é igual a um raio de possíveis locais. Para obter uma única localização 3d podemos, em seguida, aproveitar vários raios e localizar o resultado final, a interseção entre elas aproximado. Para fazer isso, você precisará:
1. Obter um loop que irá coletar várias imagens da câmera
2. Localizar os pontos de recursos associado e seus raios do mundo
3. Quando você tem um dicionário de recursos, cada um com vários raios do mundo, você pode usar o código a seguir para resolver para a interseção dos raios:

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

Dois ou mais locais de marca controladas, você pode posicionar uma cena modelled de acordo com o cenário atual de usuários. Se você não pode assumir a gravidade, em seguida, você precisará três locais de marca. Em muitos casos, que podemos usar um esquema de cores simples onde esferas brancas representam em tempo real rastreadas locais de marca e esferas azuis representam os locais de marca modeladas, isso permite que o usuário visualmente a qualidade do alinhamento do medidor. Vamos supor a seguinte configuração em todos os nossos aplicativos:
* Dois ou mais locais de marca modeladas
* Um 'espaço de calibragem', que é o pai das marcas na cena
* Identificador de recurso de câmera
* Comportamento que move o espaço de calibração para alinhar as marcas modelled com as marcas em tempo real (estamos cuidadosos para mover o espaço do pai, não os marcadores modelled por conta própria, porque outros connect é posições relativas aos-los).

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Faixa ou identificar marcado estático ou movendo reais objetos/faces usando LEDs ou outras bibliotecas do reconhecedor

Exemplos:
* Robôs industriais com LEDs (ou objetos de códigos QR para mover mais lenta)
* Identificar e reconhecer os objetos na sala
* Identificar e reconhecer pessoas na sala (por exemplo, coloque holográfica cartões de visita dos rostos)

## <a name="see-also"></a>Consulte também
* [Câmera localizável no DirectX](locatable-camera-in-directx.md)
* [Câmera localizável no Unity](locatable-camera-in-unity.md)
* [Captura de realidade misturada](mixed-reality-capture.md)
* [Captura de realidade misturada para desenvolvedores](mixed-reality-capture-for-developers.md)
* [Introdução de captura de mídia](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [Exemplo de acompanhamento de face holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
