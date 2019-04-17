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
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="c96fb-104">Localizáveis câmera no Unity</span><span class="sxs-lookup"><span data-stu-id="c96fb-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="c96fb-105">Habilitando a funcionalidade de câmera de vídeo de foto</span><span class="sxs-lookup"><span data-stu-id="c96fb-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="c96fb-106">O recurso de "WebCam" deve ser declarado para um aplicativo usar o [câmera](locatable-camera.md).</span><span class="sxs-lookup"><span data-stu-id="c96fb-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="c96fb-107">No Editor do Unity, vá para as configurações de player, navegando até a página "Editar > projeto Configurações > Player"</span><span class="sxs-lookup"><span data-stu-id="c96fb-107">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="c96fb-108">Clique na guia "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="c96fb-108">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="c96fb-109">Na seção "> recursos de publicação configurações", verifique as **WebCam** e **microfone** recursos</span><span class="sxs-lookup"><span data-stu-id="c96fb-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="c96fb-110">Apenas uma única operação pode ocorrer com a câmera por vez.</span><span class="sxs-lookup"><span data-stu-id="c96fb-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="c96fb-111">Para determinar qual modo (fotos, vídeo ou nenhuma) a câmera está atualmente no, você pode verificar UnityEngine.XR.WSA.WebCam.Mode.</span><span class="sxs-lookup"><span data-stu-id="c96fb-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="c96fb-112">Photo Capture</span><span class="sxs-lookup"><span data-stu-id="c96fb-112">Photo Capture</span></span>

<span data-ttu-id="c96fb-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="c96fb-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="c96fb-114">**Tipo:** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="c96fb-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="c96fb-115">O *PhotoCapture* tipo permite que você ainda tirar fotografias com a câmera de vídeo de fotos.</span><span class="sxs-lookup"><span data-stu-id="c96fb-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="c96fb-116">O padrão geral para usar *PhotoCapture* tirar uma foto é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c96fb-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="c96fb-117">Criar uma *PhotoCapture* objeto</span><span class="sxs-lookup"><span data-stu-id="c96fb-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="c96fb-118">Criar uma *CameraParameters* objeto com as configurações que queremos</span><span class="sxs-lookup"><span data-stu-id="c96fb-118">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="c96fb-119">Iniciar modo de foto por meio do *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="c96fb-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="c96fb-120">Tirar a foto desejada</span><span class="sxs-lookup"><span data-stu-id="c96fb-120">Take the desired photo</span></span>
    * <span data-ttu-id="c96fb-121">(opcional) Interagir com essa imagem</span><span class="sxs-lookup"><span data-stu-id="c96fb-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="c96fb-122">Parar o modo de foto e limpar recursos</span><span class="sxs-lookup"><span data-stu-id="c96fb-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="c96fb-123">Comuns configuradas para PhotoCapture</span><span class="sxs-lookup"><span data-stu-id="c96fb-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="c96fb-124">Para todos os usos de três, vamos começar com o mesmo primeiro 3 etapas acima</span><span class="sxs-lookup"><span data-stu-id="c96fb-124">For all three uses, we start with the same first 3 steps above</span></span>

<span data-ttu-id="c96fb-125">Vamos começar criando um *PhotoCapture* objeto</span><span class="sxs-lookup"><span data-stu-id="c96fb-125">We start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="c96fb-126">Em seguida podemos armazenar nosso objeto, definir nossos parâmetros e iniciar o modo de foto</span><span class="sxs-lookup"><span data-stu-id="c96fb-126">Next we store our object, set our parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="c96fb-127">No final, também usaremos o mesmo código apresentado aqui de limpeza</span><span class="sxs-lookup"><span data-stu-id="c96fb-127">In the end, we will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="c96fb-128">Após essas etapas, você pode escolher qual tipo de foto para capturar.</span><span class="sxs-lookup"><span data-stu-id="c96fb-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="c96fb-129">Capturar uma foto para um arquivo</span><span class="sxs-lookup"><span data-stu-id="c96fb-129">Capture a Photo to a File</span></span>

<span data-ttu-id="c96fb-130">A operação mais simples é capturar uma foto diretamente para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c96fb-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="c96fb-131">A foto pode ser salvas como um JPG ou um PNG.</span><span class="sxs-lookup"><span data-stu-id="c96fb-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="c96fb-132">Se é iniciado com êxito o modo de foto, podemos agora irá tirar uma foto e armazená-lo no disco</span><span class="sxs-lookup"><span data-stu-id="c96fb-132">If we successfully started photo mode, we now will take a photo and store it on disk</span></span>

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

<span data-ttu-id="c96fb-133">Depois de capturar a foto no disco, vamos sair do modo de foto e, em seguida, limpar nossos objetos</span><span class="sxs-lookup"><span data-stu-id="c96fb-133">After capturing the photo to disk, we will exit photo mode and then clean up our objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="c96fb-134">Capturar uma foto a uma Texture2D</span><span class="sxs-lookup"><span data-stu-id="c96fb-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="c96fb-135">Durante a captura de dados para uma Texture2D, o processo é muito semelhante à captura de disco.</span><span class="sxs-lookup"><span data-stu-id="c96fb-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="c96fb-136">Vamos seguir o processo acima de configuração.</span><span class="sxs-lookup"><span data-stu-id="c96fb-136">We will follow the set up process above.</span></span>

<span data-ttu-id="c96fb-137">Na *OnPhotoModeStarted*, podemos irá capturar um quadro para a memória.</span><span class="sxs-lookup"><span data-stu-id="c96fb-137">In *OnPhotoModeStarted*, we will capture a frame to memory.</span></span>

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

<span data-ttu-id="c96fb-138">Nós, em seguida, aplicar nossos resultados com uma textura e usar comuns acima do código de limpeza.</span><span class="sxs-lookup"><span data-stu-id="c96fb-138">We will then apply our result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="c96fb-139">Capturar uma foto e interagir com os bytes brutos</span><span class="sxs-lookup"><span data-stu-id="c96fb-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="c96fb-140">Para interagir com os bytes brutos de uma memória no quadro, Seguiremos as mesmas etapas acima e *OnPhotoModeStarted* como capturar uma foto a uma Texture2D.</span><span class="sxs-lookup"><span data-stu-id="c96fb-140">To interact with the raw bytes of an in memory frame, we will follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="c96fb-141">A diferença está na *OnCapturedPhotoToMemory* onde podemos obter os bytes brutos e interagir com eles.</span><span class="sxs-lookup"><span data-stu-id="c96fb-141">The difference is in *OnCapturedPhotoToMemory* where we can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="c96fb-142">Neste exemplo, vamos criar uma *lista<Color>*  que pode ser mais processadas ou aplicadas a uma textura por meio de *setPixels)*</span><span class="sxs-lookup"><span data-stu-id="c96fb-142">In this example, we will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="c96fb-143">Captura de vídeo</span><span class="sxs-lookup"><span data-stu-id="c96fb-143">Video Capture</span></span>

<span data-ttu-id="c96fb-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="c96fb-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="c96fb-145">**Tipo:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="c96fb-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="c96fb-146">*VideoCapture* função é muito semelhante à *PhotoCapture*.</span><span class="sxs-lookup"><span data-stu-id="c96fb-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="c96fb-147">Somente duas diferenças são que você deve especificar um valor de quadros por segundo (FPS) e você só pode salvar diretamente no disco como um arquivo. mp4.</span><span class="sxs-lookup"><span data-stu-id="c96fb-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="c96fb-148">As etapas para usar *VideoCapture* são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c96fb-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="c96fb-149">Criar uma *VideoCapture* objeto</span><span class="sxs-lookup"><span data-stu-id="c96fb-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="c96fb-150">Criar uma *CameraParameters* objeto com as configurações que queremos</span><span class="sxs-lookup"><span data-stu-id="c96fb-150">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="c96fb-151">Iniciar modo de vídeo por meio de *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="c96fb-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="c96fb-152">Iniciar gravação de vídeo</span><span class="sxs-lookup"><span data-stu-id="c96fb-152">Start recording video</span></span>
5. <span data-ttu-id="c96fb-153">Parar a gravação de vídeo</span><span class="sxs-lookup"><span data-stu-id="c96fb-153">Stop recording video</span></span>
6. <span data-ttu-id="c96fb-154">Parar o modo de vídeo e limpar recursos</span><span class="sxs-lookup"><span data-stu-id="c96fb-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="c96fb-155">Vamos começar criando nosso *VideoCapture* objeto *VideoCapture m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="c96fb-155">We start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="c96fb-156">Em seguida, definiremos os parâmetros que serão desejadas para a gravação e o início.</span><span class="sxs-lookup"><span data-stu-id="c96fb-156">We then will set up the parameters we will want for the recording and start.</span></span>

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

<span data-ttu-id="c96fb-157">Uma vez iniciada, começaremos a gravação</span><span class="sxs-lookup"><span data-stu-id="c96fb-157">Once started, we will begin the recording</span></span>

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

<span data-ttu-id="c96fb-158">Após a gravação foi iniciada, você poderia atualizar a interface do usuário ou comportamentos para habilitar a interrupção.</span><span class="sxs-lookup"><span data-stu-id="c96fb-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="c96fb-159">Aqui podemos simplesmente fazer</span><span class="sxs-lookup"><span data-stu-id="c96fb-159">Here we just log</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="c96fb-160">Em um momento posterior, queremos interromper a gravação.</span><span class="sxs-lookup"><span data-stu-id="c96fb-160">At a later point, we will want to stop the recording.</span></span> <span data-ttu-id="c96fb-161">Isso pode acontecer de um timer ou entrada do usuário, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="c96fb-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="c96fb-162">Depois que a gravação foi interrompido, vamos parar o modo de vídeo e limpar os nossos recursos.</span><span class="sxs-lookup"><span data-stu-id="c96fb-162">Once the recording has stopped, we will stop video mode and clean up our resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="c96fb-163">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c96fb-163">Troubleshooting</span></span>
* <span data-ttu-id="c96fb-164">Nenhuma resolução está disponíveis</span><span class="sxs-lookup"><span data-stu-id="c96fb-164">No resolutions are available</span></span>
    * <span data-ttu-id="c96fb-165">Verifique se o **WebCam** recurso é especificado em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c96fb-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="c96fb-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c96fb-166">See Also</span></span>
* [<span data-ttu-id="c96fb-167">Câmera localizáveis</span><span class="sxs-lookup"><span data-stu-id="c96fb-167">Locatable camera</span></span>](locatable-camera.md)
