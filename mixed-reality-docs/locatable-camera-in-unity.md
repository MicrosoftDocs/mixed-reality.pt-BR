---
title: Localizáveis câmera no Unity
description: Uso de câmera localizáveis HoloLens no Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: fotos, vídeo, hololens, câmera, unity, localizáveis
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589926"
---
# <a name="locatable-camera-in-unity"></a>Localizáveis câmera no Unity

## <a name="enabling-the-capability-for-photo-video-camera"></a>Habilitando a funcionalidade de câmera de vídeo de foto

O recurso de "WebCam" deve ser declarado para um aplicativo usar o [câmera](locatable-camera.md).
1. No Editor do Unity, vá para as configurações de player, navegando até a página "Editar > projeto Configurações > Player"
2. Clique na guia "Windows Store"
3. Na seção "> recursos de publicação configurações", verifique as **WebCam** e **microfone** recursos

Apenas uma única operação pode ocorrer com a câmera por vez. Para determinar qual modo (fotos, vídeo ou nenhuma) a câmera está atualmente no, você pode verificar UnityEngine.XR.WSA.WebCam.Mode.

## <a name="photo-capture"></a>Photo Capture

**Namespace:** *UnityEngine.XR.WSA.WebCam*<br>
**Tipo:** *PhotoCapture*

O *PhotoCapture* tipo permite que você ainda tirar fotografias com a câmera de vídeo de fotos. O padrão geral para usar *PhotoCapture* tirar uma foto é da seguinte maneira:
1. Criar uma *PhotoCapture* objeto
2. Criar uma *CameraParameters* objeto com as configurações que queremos
3. Iniciar modo de foto por meio do *StartPhotoModeAsync*
4. Tirar a foto desejada
    * (opcional) Interagir com essa imagem
5. Parar o modo de foto e limpar recursos

### <a name="common-set-up-for-photocapture"></a>Comuns configuradas para PhotoCapture

Para todos os usos de três, vamos começar com o mesmo primeiro 3 etapas acima

Vamos começar criando um *PhotoCapture* objeto

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

Em seguida podemos armazenar nosso objeto, definir nossos parâmetros e iniciar o modo de foto

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

No final, também usaremos o mesmo código apresentado aqui de limpeza

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

Após essas etapas, você pode escolher qual tipo de foto para capturar.

### <a name="capture-a-photo-to-a-file"></a>Capturar uma foto para um arquivo

A operação mais simples é capturar uma foto diretamente para um arquivo. A foto pode ser salvas como um JPG ou um PNG.

Se é iniciado com êxito o modo de foto, podemos agora irá tirar uma foto e armazená-lo no disco

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

Depois de capturar a foto no disco, vamos sair do modo de foto e, em seguida, limpar nossos objetos

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

### <a name="capture-a-photo-to-a-texture2d"></a>Capturar uma foto a uma Texture2D

Durante a captura de dados para uma Texture2D, o processo é muito semelhante à captura de disco.

Vamos seguir o processo acima de configuração.

Na *OnPhotoModeStarted*, podemos irá capturar um quadro para a memória.

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

Nós, em seguida, aplicar nossos resultados com uma textura e usar comuns acima do código de limpeza.

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Capturar uma foto e interagir com os bytes brutos

Para interagir com os bytes brutos de uma memória no quadro, Seguiremos as mesmas etapas acima e *OnPhotoModeStarted* como capturar uma foto a uma Texture2D. A diferença está na *OnCapturedPhotoToMemory* onde podemos obter os bytes brutos e interagir com eles.

Neste exemplo, vamos criar uma *lista<Color>*  que pode ser mais processadas ou aplicadas a uma textura por meio de *setPixels)*

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

**Namespace:** *UnityEngine.XR.WSA.WebCam*<br>
**Tipo:** *VideoCapture*

*VideoCapture* função é muito semelhante à *PhotoCapture*. Somente duas diferenças são que você deve especificar um valor de quadros por segundo (FPS) e você só pode salvar diretamente no disco como um arquivo. mp4. As etapas para usar *VideoCapture* são da seguinte maneira:
1. Criar uma *VideoCapture* objeto
2. Criar uma *CameraParameters* objeto com as configurações que queremos
3. Iniciar modo de vídeo por meio de *StartVideoModeAsync*
4. Iniciar gravação de vídeo
5. Parar a gravação de vídeo
6. Parar o modo de vídeo e limpar recursos

Vamos começar criando nosso *VideoCapture* objeto *VideoCapture m_VideoCapture = null;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

Em seguida, definiremos os parâmetros que serão desejadas para a gravação e o início.

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

Uma vez iniciada, começaremos a gravação

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

Após a gravação foi iniciada, você poderia atualizar a interface do usuário ou comportamentos para habilitar a interrupção. Aqui podemos simplesmente fazer

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

Em um momento posterior, queremos interromper a gravação. Isso pode acontecer de um timer ou entrada do usuário, por exemplo.

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

Depois que a gravação foi interrompido, vamos parar o modo de vídeo e limpar os nossos recursos.

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

## <a name="troubleshooting"></a>Solução de problemas
* Nenhuma resolução está disponíveis
    * Verifique se o **WebCam** recurso é especificado em seu projeto.

## <a name="see-also"></a>Consulte também
* [Câmera localizáveis](locatable-camera.md)
