---
title: Câmera localizável no Unity
description: Uso da câmera localizável do HoloLens no Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: foto, vídeo, hololens, câmera, Unity, localizável
ms.openlocfilehash: b4a1a7e11a7606dab76b954c8d58a335d6bae0ab
ms.sourcegitcommit: d0da0214fdd2bbac5a91a5d895bf0e87413b29b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597609"
---
# <a name="locatable-camera-in-unity"></a>Câmera localizável no Unity

## <a name="enabling-the-capability-for-photo-video-camera"></a>Habilitando o recurso de câmera de vídeo fotográfico

A capacidade de "WebCam" deve ser declarada para que um aplicativo use a [câmera](locatable-camera.md).
1. No editor do Unity, vá para as configurações do Player navegando até a página "Editar configurações do projeto > > Player"
2. Clique na guia "Windows Store"
3. Na seção "configurações de publicação > recursos", verifique os recursos de **webcam** e de **microfone**

Apenas uma única operação pode ocorrer com a câmera de cada vez. Para determinar qual modo (foto, vídeo ou nenhum) a câmera está no momento, você pode verificar UnityEngine. XR. WSA. WebCam. Mode.

## <a name="photo-capture"></a>Captura de fotos

**Namespace:** *UnityEngine. XR. WSA. webcam*<br>
**Tipo:** o *Capture*

O tipo de *captura* de imagem permite que você faça ainda fotografias com a câmera de vídeo de fotos. O padrão geral para usar o *Capture* para tirar uma foto é o seguinte:
1. Criar um objeto do *Pocapture*
2. Crie um objeto *cameraparameters* com as configurações desejadas
3. Iniciar o modo de foto via *StartPhotoModeAsync*
4. Tirar a foto desejada
    * adicional Interagir com essa imagem
5. Parar o modo de foto e limpar os recursos

### <a name="common-set-up-for-photocapture"></a>Configuração comum para o Capture

Para todos os três usos, comece com as mesmas primeiras 3 etapas acima

Comece criando um objeto do *Pocapture*

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

Em seguida, armazene seu objeto, defina seus parâmetros e inicie o modo de foto

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

No final, você também usará o mesmo código de limpeza apresentado aqui

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

Após essas etapas, você pode escolher o tipo de foto a ser capturado.

### <a name="capture-a-photo-to-a-file"></a>Capturar uma foto em um arquivo

A operação mais simples é capturar uma foto diretamente em um arquivo. A foto pode ser salva como um JPG ou um PNG.

Se você iniciou o modo de foto com êxito, tire uma foto e armazene-a em disco

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

Depois de capturar a foto para o disco, saia do modo de foto e limpe os objetos

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a>Capturar uma foto para um Texture2D

Ao capturar dados para um Texture2D, o processo é extremamente semelhante à captura para o disco.

Siga o processo de configuração acima.

No *OnPhotoModeStarted*, Capture um quadro na memória.

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

Em seguida, você aplicará o resultado a uma textura e usará o código de limpeza comum acima.

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Capture uma foto e interaja com os bytes brutos

Para interagir com os bytes brutos de um quadro na memória, siga as mesmas etapas de configuração descritas acima e *OnPhotoModeStarted* como em capturando uma foto para um Texture2D. A diferença está em *OnCapturedPhotoToMemory* , em que você pode obter os bytes brutos e interagir com eles.

Neste exemplo, você criará uma *lista<Color>* que pode ser processada ou aplicada a uma textura por meio de *setPixels ()*

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a>Captura de vídeo

**Namespace:** *UnityEngine. XR. WSA. webcam*<br>
**Tipo:** *VideoCapture*

O *VideoCapture* funciona de forma semelhante à do *Capture*. As duas únicas diferenças são que você deve especificar um valor de quadros por segundo (FPS) e só pode salvar diretamente no disco como um arquivo. mp4. As etapas para usar o *VideoCapture* são as seguintes:
1. Criar um objeto *VideoCapture*
2. Crie um objeto *cameraparameters* com as configurações desejadas
3. Iniciar o modo de vídeo via *StartVideoModeAsync*
4. Iniciar gravação de vídeo
5. Parar de gravar vídeo
6. Parar o modo de vídeo e limpar os recursos

Comece criando nosso objeto *VideoCapture* *VideoCapture m_VideoCapture = NULL;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

Em seguida, configure os parâmetros desejados para a gravação e o início.

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

Depois de iniciado, inicie a gravação

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

Após o início da gravação, você pode atualizar sua interface do usuário ou comportamentos para habilitar a interrupção. Aqui você acabou de fazer logon.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

Em um ponto posterior, você desejará parar a gravação. Isso pode acontecer de uma entrada de temporizador ou de usuário, por exemplo.

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

Depois que a gravação for interrompida, pare o modo de vídeo e limpe os recursos.

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a>Painel de controle da
* Não há resoluções disponíveis
    * Verifique se a capacidade de **webcam** está especificada no seu projeto.

## <a name="see-also"></a>Veja também
* [Câmera localizável](locatable-camera.md)
