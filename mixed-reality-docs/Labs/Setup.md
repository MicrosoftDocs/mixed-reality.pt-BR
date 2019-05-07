# <a name="setting-up"></a><span data-ttu-id="cae0d-101">Como configurar</span><span class="sxs-lookup"><span data-stu-id="cae0d-101">Setting Up</span></span>

<span data-ttu-id="cae0d-102">Guia de Introdução com a API do Azure Kinect DK?</span><span class="sxs-lookup"><span data-stu-id="cae0d-102">Getting started with the Azure Kinect DK API?</span></span> <span data-ttu-id="cae0d-103">Não procure mais!</span><span class="sxs-lookup"><span data-stu-id="cae0d-103">Look no further!</span></span> <span data-ttu-id="cae0d-104">Este documento irá proporcionar a você tudo em funcionamento com acesso ao dispositivo!</span><span class="sxs-lookup"><span data-stu-id="cae0d-104">This document will get you up and running with access to the device!</span></span>

<span data-ttu-id="cae0d-105">Primeiro, baixe e instale o [API do Azure Kinect DK](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) do Github.</span><span class="sxs-lookup"><span data-stu-id="cae0d-105">First, download and install the [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) from Github.</span></span>

<span data-ttu-id="cae0d-106">**Conteúdo**</span><span class="sxs-lookup"><span data-stu-id="cae0d-106">**Contents**</span></span>  
[<span data-ttu-id="cae0d-107">Cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="cae0d-107">Headers</span></span>](#Headers)  
[<span data-ttu-id="cae0d-108">Localizando um dispositivo Kinect</span><span class="sxs-lookup"><span data-stu-id="cae0d-108">Finding a Kinect Device</span></span>](#Finding-a-Kinect-Device)  
[<span data-ttu-id="cae0d-109">Iniciando as câmeras</span><span class="sxs-lookup"><span data-stu-id="cae0d-109">Starting the Cameras</span></span>](#Starting-the-Cameras)  
[<span data-ttu-id="cae0d-110">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="cae0d-110">Error Handling</span></span>](#Error-Handling)  
[<span data-ttu-id="cae0d-111">Código-fonte completo</span><span class="sxs-lookup"><span data-stu-id="cae0d-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="cae0d-112">**Aqui estão as funções que usaremos:**</span><span class="sxs-lookup"><span data-stu-id="cae0d-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a><span data-ttu-id="cae0d-113">Cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="cae0d-113">Headers</span></span>
<span data-ttu-id="cae0d-114">Há apenas um cabeçalho que você vai precisar, e que é k4a.h!</span><span class="sxs-lookup"><span data-stu-id="cae0d-114">There's only one header that you'll need, and that's k4a.h!</span></span> <span data-ttu-id="cae0d-115">Verifique se que o compilador de escolha é configurada com lib do SDK e incluir pastas.</span><span class="sxs-lookup"><span data-stu-id="cae0d-115">Make sure your compiler of choice is set up with the SDK's lib and include folders.</span></span> <span data-ttu-id="cae0d-116">Os arquivos k4a.lib e k4a.dll vinculados também será necessário.</span><span class="sxs-lookup"><span data-stu-id="cae0d-116">You'll also need the k4a.lib and k4a.dll files linked up.</span></span>
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a><span data-ttu-id="cae0d-117">Localizando um dispositivo Kinect</span><span class="sxs-lookup"><span data-stu-id="cae0d-117">Finding a Kinect Device</span></span>

![](img/Serial.png)

<span data-ttu-id="cae0d-118">Vários dispositivos Azure Kinect DK podem ser conectados ao computador!</span><span class="sxs-lookup"><span data-stu-id="cae0d-118">Multiple Azure Kinect DK devices can be connected to your computer!</span></span> <span data-ttu-id="cae0d-119">Vamos começar pela primeira vez pelo Localizando out quantos, ou se qualquer um estiver conectado a alguma usando o [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) função.</span><span class="sxs-lookup"><span data-stu-id="cae0d-119">We'll first start by finding out how many, or if any are connected at all using the [`k4a_device_get_installed_count`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) function.</span></span> <span data-ttu-id="cae0d-120">Essa função deve funcionar imediatamente, sem nenhuma configuração adicional!</span><span class="sxs-lookup"><span data-stu-id="cae0d-120">This function should work right away, without any additional setup!</span></span>

```C
uint32_t count = k4a_device_get_installed_count();
```

<span data-ttu-id="cae0d-121">Depois de determinar lá está, na verdade, um dispositivo conectado ao computador, você pode abri-lo usando [ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span><span class="sxs-lookup"><span data-stu-id="cae0d-121">Once you've determined there is actually a device connected to the computer, you can open it using [`k4a_device_open`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span></span> <span data-ttu-id="cae0d-122">Você pode fornecer o índice do dispositivo que deseja abrir, ou você pode usar apenas [ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) para o primeiro.</span><span class="sxs-lookup"><span data-stu-id="cae0d-122">You can provide the index of the device you want to open, or you can just use [`K4A_DEVICE_DEFAULT`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) for the first one.</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
<span data-ttu-id="cae0d-123">Como com a maioria das coisas na API do k4a, quando você abre algo, você deve também fechá-lo quando tiver terminado com ele!</span><span class="sxs-lookup"><span data-stu-id="cae0d-123">As with most things in the k4a API, when you open something, you should also close it when you're finished with it!</span></span> <span data-ttu-id="cae0d-124">Quando você estiver desligado, lembre-se de fazer uma chamada para [ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span><span class="sxs-lookup"><span data-stu-id="cae0d-124">When you're shutting down, remember to make a call to [`k4a_device_close`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span></span>

```C
k4a_device_close(device);
```

<span data-ttu-id="cae0d-125">Quando o dispositivo é aberto, podemos fazer um teste realmente simples para garantir que ele é muito bom.</span><span class="sxs-lookup"><span data-stu-id="cae0d-125">Once the device is open, we can make a really simple test to ensure it's all good.</span></span> <span data-ttu-id="cae0d-126">Então, vamos ler o número de série do dispositivo!</span><span class="sxs-lookup"><span data-stu-id="cae0d-126">So let's read the device's serial number!</span></span>

```C
// Get the size of the serial number
size_t serial_size = 0;
k4a_device_get_serialnum(device, NULL, &serial_size);

// Allocate memory for the serial, then acquire it
char *serial = static_cast<char*>(malloc(serial_size));
k4a_device_get_serialnum(device, serial, &serial_size);
printf("Opened device: %s\n", serial);
free(serial);
```

## <a name="starting-the-cameras"></a><span data-ttu-id="cae0d-127">Iniciando as câmeras</span><span class="sxs-lookup"><span data-stu-id="cae0d-127">Starting the Cameras</span></span>

<span data-ttu-id="cae0d-128">Depois de abrir o dispositivo, você precisará configurar a câmera com um [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) objeto!</span><span class="sxs-lookup"><span data-stu-id="cae0d-128">Once you've opened the device, you'll need to configure the camera with a [`k4a_device_configuration_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) object!</span></span> <span data-ttu-id="cae0d-129">A configuração de câmera tem várias opções diferentes, e você precisará escolher as configurações que melhor se ajustam ao seu próprio cenário.</span><span class="sxs-lookup"><span data-stu-id="cae0d-129">Camera configuration has a number of different options, and you'll need to choose the settings that best fit your own scenario.</span></span>

```C
// Configure a stream of 4096x3072 BRGA color data at 15 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_15;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

// Start the camera with the given configuration
k4a_device_start_cameras(device, &config)

// ...Camera capture and application specific code would go here...

// Shut down the camera when finished with application logic
k4a_device_stop_cameras(device);
```

<span data-ttu-id="cae0d-130">Para obter detalhes de configuração sobre o __cor__ câmera, [check-out neste documento]()!</span><span class="sxs-lookup"><span data-stu-id="cae0d-130">For configuration details about the __color__ camera, [check out this document]()!</span></span>  
<span data-ttu-id="cae0d-131">Para obter detalhes de configuração sobre o __profundidade__ câmera, [check-out neste documento]()!</span><span class="sxs-lookup"><span data-stu-id="cae0d-131">For configuration details about the __depth__ camera, [check out this document]()!</span></span>

## <a name="error-handling"></a><span data-ttu-id="cae0d-132">Tratamento de erro</span><span class="sxs-lookup"><span data-stu-id="cae0d-132">Error Handling</span></span>

<span data-ttu-id="cae0d-133">Para fins de brevidade e clareza, não mostraremos alguns exemplos de embutido de tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="cae0d-133">For the sake of brevity and clarity, we don't show error handling in some inline examples.</span></span> <span data-ttu-id="cae0d-134">No entanto, tratamento de erro é sempre importante!</span><span class="sxs-lookup"><span data-stu-id="cae0d-134">However, error handling is always important!</span></span> <span data-ttu-id="cae0d-135">Muitas funções retornará um tipo de êxito/falha geral [ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), ou uma variante mais específica com informações detalhadas, como [ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span><span class="sxs-lookup"><span data-stu-id="cae0d-135">Many functions will return a general success/failure type [`k4a_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), or a more specific variant with detailed information such as [`k4a_wait_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span></span> <span data-ttu-id="cae0d-136">Verifique os documentos ou intellisense de uma função específica para ver quais mensagens de erro que você pode esperar ver dele!</span><span class="sxs-lookup"><span data-stu-id="cae0d-136">Be sure to check the docs or intellisense of a specific function to see what error messages you might expect to see from it!</span></span>

<span data-ttu-id="cae0d-137">Além dos tipos de erro, há também o [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) e [ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macros que você pode usar com eles.</span><span class="sxs-lookup"><span data-stu-id="cae0d-137">Along with the error types, there's also the [`K4A_SUCCEEDED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) and [`K4A_FAILED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macros that you can use with them.</span></span> <span data-ttu-id="cae0d-138">Portanto, em vez de apenas abrir um dispositivo k4a, podemos pode Proteja-o assim:</span><span class="sxs-lookup"><span data-stu-id="cae0d-138">So instead of just opening a k4a device, we might guard it like this:</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a><span data-ttu-id="cae0d-139">Código-fonte completo</span><span class="sxs-lookup"><span data-stu-id="cae0d-139">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

int main()
{
    uint32_t count = k4a_device_get_installed_count();
    if (count == 0)
    {
        printf("No k4a devices attached!\n");
        return 0;
    }

    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    if (K4A_FAILED(k4a_device_open(K4A_DEVICE_DEFAULT, &device)))
    {
        printf("Failed to open k4a device!\n");
        return 0;
    }

    // Get the size of the serial number
    size_t serial_size = 0;
    k4a_device_get_serialnum(device, NULL, &serial_size);

    // Allocate memory for the serial, then acquire it
    char* serial = static_cast<char*>(malloc(serial_size));
    k4a_device_get_serialnum(device, serial, &serial_size);
    printf("Opened device: %s\n", serial);
    free(serial);

    // Configure a stream of 4096x3072 BRGA color data at 15 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_15;
    config.color_format = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

    // Start the camera with the given configuration
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
    {
        printf("Failed to start cameras!\n");
        k4a_device_close(device);
        return 0;
    }

    // ...Camera capture and application specific code would go here...

    // Shut down the camera when finished with application logic
    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}
```

## <a name="next-lab---reading-depth-datareaddepthmd"></a><span data-ttu-id="cae0d-140">Próximo laboratório - [lendo dados de profundidade](ReadDepth.md)</span><span class="sxs-lookup"><span data-stu-id="cae0d-140">Next Lab - [Reading Depth Data](ReadDepth.md)</span></span>
