---
title: Câmera localizável no Unity
description: Uso da câmera localizável do HoloLens no Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: foto, vídeo, hololens, câmera, Unity, localizável
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515440"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="c667a-104">Câmera localizável no Unity</span><span class="sxs-lookup"><span data-stu-id="c667a-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="c667a-105">Habilitando o recurso de câmera de vídeo fotográfico</span><span class="sxs-lookup"><span data-stu-id="c667a-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="c667a-106">A capacidade de "WebCam" deve ser declarada para que um aplicativo use a [câmera](locatable-camera.md).</span><span class="sxs-lookup"><span data-stu-id="c667a-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="c667a-107">No editor do Unity, vá para as configurações do Player navegando para a página "Editar configurações do projeto > > Player"</span><span class="sxs-lookup"><span data-stu-id="c667a-107">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="c667a-108">Clique na guia "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="c667a-108">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="c667a-109">Na seção "configurações de publicação > recursos", verifique os recursos de **webcam** e de **microfone**</span><span class="sxs-lookup"><span data-stu-id="c667a-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="c667a-110">Apenas uma única operação pode ocorrer com a câmera de cada vez.</span><span class="sxs-lookup"><span data-stu-id="c667a-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="c667a-111">Para determinar qual modo (foto, vídeo ou nenhum) a câmera está no momento, você pode verificar UnityEngine. XR. WSA. WebCam. Mode.</span><span class="sxs-lookup"><span data-stu-id="c667a-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="c667a-112">Captura de fotos</span><span class="sxs-lookup"><span data-stu-id="c667a-112">Photo Capture</span></span>

<span data-ttu-id="c667a-113">**Namespace:** *UnityEngine. XR. WSA. WebCam*</span><span class="sxs-lookup"><span data-stu-id="c667a-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="c667a-114">**Escreva** *Captura*</span><span class="sxs-lookup"><span data-stu-id="c667a-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="c667a-115">O tipo de *captura* de imagem permite que você faça ainda fotografias com a câmera de vídeo de fotos.</span><span class="sxs-lookup"><span data-stu-id="c667a-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="c667a-116">O padrão geral para usar o *Capture* para tirar uma foto é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c667a-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="c667a-117">Criar um  objeto do pocapture</span><span class="sxs-lookup"><span data-stu-id="c667a-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="c667a-118">Criar um  objeto cameraparameters com as configurações que desejamos</span><span class="sxs-lookup"><span data-stu-id="c667a-118">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="c667a-119">Iniciar o modo de foto via *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="c667a-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="c667a-120">Tirar a foto desejada</span><span class="sxs-lookup"><span data-stu-id="c667a-120">Take the desired photo</span></span>
    * <span data-ttu-id="c667a-121">adicional Interagir com essa imagem</span><span class="sxs-lookup"><span data-stu-id="c667a-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="c667a-122">Parar o modo de foto e limpar os recursos</span><span class="sxs-lookup"><span data-stu-id="c667a-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="c667a-123">Configuração comum para o Capture</span><span class="sxs-lookup"><span data-stu-id="c667a-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="c667a-124">Para todos os três usos, começamos com as mesmas primeiras 3 etapas acima</span><span class="sxs-lookup"><span data-stu-id="c667a-124">For all three uses, we start with the same first 3 steps above</span></span>

<span data-ttu-id="c667a-125">Começamos criando um objeto do *Pocapture*</span><span class="sxs-lookup"><span data-stu-id="c667a-125">We start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="c667a-126">Em seguida, armazenamos nosso objeto, definimos nossos parâmetros e iniciamos o modo de foto</span><span class="sxs-lookup"><span data-stu-id="c667a-126">Next we store our object, set our parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="c667a-127">No final, também usaremos o mesmo código de limpeza apresentado aqui</span><span class="sxs-lookup"><span data-stu-id="c667a-127">In the end, we will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="c667a-128">Após essas etapas, você pode escolher o tipo de foto a ser capturado.</span><span class="sxs-lookup"><span data-stu-id="c667a-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="c667a-129">Capturar uma foto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="c667a-129">Capture a Photo to a File</span></span>

<span data-ttu-id="c667a-130">A operação mais simples é capturar uma foto diretamente em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c667a-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="c667a-131">A foto pode ser salva como um JPG ou um PNG.</span><span class="sxs-lookup"><span data-stu-id="c667a-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="c667a-132">Se o modo de foto for iniciado com êxito, vamos pegar uma foto e armazená-la em disco</span><span class="sxs-lookup"><span data-stu-id="c667a-132">If we successfully started photo mode, we now will take a photo and store it on disk</span></span>

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

<span data-ttu-id="c667a-133">Depois de capturar a foto para o disco, encerraremos o modo de foto e, em seguida, limparemos os objetos</span><span class="sxs-lookup"><span data-stu-id="c667a-133">After capturing the photo to disk, we will exit photo mode and then clean up our objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="c667a-134">Capturar uma foto para um Texture2D</span><span class="sxs-lookup"><span data-stu-id="c667a-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="c667a-135">Ao capturar dados para um Texture2D, o processo é extremamente semelhante à captura para o disco.</span><span class="sxs-lookup"><span data-stu-id="c667a-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="c667a-136">Seguiremos o processo de configuração acima.</span><span class="sxs-lookup"><span data-stu-id="c667a-136">We will follow the set up process above.</span></span>

<span data-ttu-id="c667a-137">No *OnPhotoModeStarted*, capturaremos um quadro na memória.</span><span class="sxs-lookup"><span data-stu-id="c667a-137">In *OnPhotoModeStarted*, we will capture a frame to memory.</span></span>

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

<span data-ttu-id="c667a-138">Em seguida, aplicaremos o resultado a uma textura e usaremos o código de limpeza comum acima.</span><span class="sxs-lookup"><span data-stu-id="c667a-138">We will then apply our result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="c667a-139">Capture uma foto e interaja com os bytes brutos</span><span class="sxs-lookup"><span data-stu-id="c667a-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="c667a-140">Para interagir com os bytes brutos de um quadro na memória, seguiremos as mesmas etapas de configuração acima e *OnPhotoModeStarted* como na captura de uma foto para um Texture2D.</span><span class="sxs-lookup"><span data-stu-id="c667a-140">To interact with the raw bytes of an in memory frame, we will follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="c667a-141">A diferença está em *OnCapturedPhotoToMemory* , onde podemos obter os bytes brutos e interagir com eles.</span><span class="sxs-lookup"><span data-stu-id="c667a-141">The difference is in *OnCapturedPhotoToMemory* where we can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="c667a-142">Neste exemplo, criaremos uma *lista<Color>*  que poderia ser processada ou aplicada a uma textura por meio de *setPixels ()*</span><span class="sxs-lookup"><span data-stu-id="c667a-142">In this example, we will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="c667a-143">Captura de vídeo</span><span class="sxs-lookup"><span data-stu-id="c667a-143">Video Capture</span></span>

<span data-ttu-id="c667a-144">**Namespace:** *UnityEngine. XR. WSA. WebCam*</span><span class="sxs-lookup"><span data-stu-id="c667a-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="c667a-145">**Escreva** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="c667a-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="c667a-146">O *VideoCapture* funciona de forma semelhante à do *Capture*.</span><span class="sxs-lookup"><span data-stu-id="c667a-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="c667a-147">As duas únicas diferenças são que você deve especificar um valor de quadros por segundo (FPS) e só pode salvar diretamente no disco como um arquivo. mp4.</span><span class="sxs-lookup"><span data-stu-id="c667a-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="c667a-148">As etapas para usar o *VideoCapture* são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="c667a-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="c667a-149">Criar um objeto *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="c667a-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="c667a-150">Criar um  objeto cameraparameters com as configurações que desejamos</span><span class="sxs-lookup"><span data-stu-id="c667a-150">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="c667a-151">Iniciar o modo de vídeo via *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="c667a-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="c667a-152">Iniciar gravação de vídeo</span><span class="sxs-lookup"><span data-stu-id="c667a-152">Start recording video</span></span>
5. <span data-ttu-id="c667a-153">Parar de gravar vídeo</span><span class="sxs-lookup"><span data-stu-id="c667a-153">Stop recording video</span></span>
6. <span data-ttu-id="c667a-154">Parar o modo de vídeo e limpar os recursos</span><span class="sxs-lookup"><span data-stu-id="c667a-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="c667a-155">Começamos criando nosso objeto *VideoCapture* *VideoCapture m_VideoCapture = NULL;*</span><span class="sxs-lookup"><span data-stu-id="c667a-155">We start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="c667a-156">Em seguida, vamos configurar os parâmetros que desejaremos para a gravação e o início.</span><span class="sxs-lookup"><span data-stu-id="c667a-156">We then will set up the parameters we will want for the recording and start.</span></span>

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

<span data-ttu-id="c667a-157">Depois de iniciado, começaremos a gravação</span><span class="sxs-lookup"><span data-stu-id="c667a-157">Once started, we will begin the recording</span></span>

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

<span data-ttu-id="c667a-158">Após o início da gravação, você pode atualizar sua interface do usuário ou comportamentos para habilitar a interrupção.</span><span class="sxs-lookup"><span data-stu-id="c667a-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="c667a-159">Aqui, acabamos de fazer logon</span><span class="sxs-lookup"><span data-stu-id="c667a-159">Here we just log</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="c667a-160">Em um ponto posterior, queremos parar a gravação.</span><span class="sxs-lookup"><span data-stu-id="c667a-160">At a later point, we will want to stop the recording.</span></span> <span data-ttu-id="c667a-161">Isso pode acontecer de uma entrada de temporizador ou de usuário, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="c667a-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="c667a-162">Depois que a gravação for interrompida, interromperemos o modo de vídeo e limparemos nossos recursos.</span><span class="sxs-lookup"><span data-stu-id="c667a-162">Once the recording has stopped, we will stop video mode and clean up our resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="c667a-163">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c667a-163">Troubleshooting</span></span>
* <span data-ttu-id="c667a-164">Não há resoluções disponíveis</span><span class="sxs-lookup"><span data-stu-id="c667a-164">No resolutions are available</span></span>
    * <span data-ttu-id="c667a-165">Verifique se a capacidade de **webcam** está especificada no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c667a-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="c667a-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c667a-166">See Also</span></span>
* [<span data-ttu-id="c667a-167">Câmera localizável</span><span class="sxs-lookup"><span data-stu-id="c667a-167">Locatable camera</span></span>](locatable-camera.md)
