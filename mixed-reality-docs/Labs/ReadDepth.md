# <a name="reading-depth-data"></a><span data-ttu-id="0ab9f-101">Lendo dados de profundidade</span><span class="sxs-lookup"><span data-stu-id="0ab9f-101">Reading Depth Data</span></span>

<span data-ttu-id="0ab9f-102">Você precisa ler dados de profundidade do dispositivo?</span><span class="sxs-lookup"><span data-stu-id="0ab9f-102">Need to read depth data from the device?</span></span> <span data-ttu-id="0ab9f-103">É fácil!</span><span class="sxs-lookup"><span data-stu-id="0ab9f-103">It's easy!</span></span>

<span data-ttu-id="0ab9f-104">**Conteúdo**</span><span class="sxs-lookup"><span data-stu-id="0ab9f-104">**Contents**</span></span>  
[<span data-ttu-id="0ab9f-105">Configuração do dispositivo</span><span class="sxs-lookup"><span data-stu-id="0ab9f-105">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="0ab9f-106">Profundidade acessando dados</span><span class="sxs-lookup"><span data-stu-id="0ab9f-106">Acessing Depth Data</span></span>](#Acessing-Depth-Data)  
[<span data-ttu-id="0ab9f-107">Limpando</span><span class="sxs-lookup"><span data-stu-id="0ab9f-107">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="0ab9f-108">Código-fonte completo</span><span class="sxs-lookup"><span data-stu-id="0ab9f-108">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="0ab9f-109">**Aqui estão as funções que usaremos:**</span><span class="sxs-lookup"><span data-stu-id="0ab9f-109">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a><span data-ttu-id="0ab9f-110">Configuração do dispositivo</span><span class="sxs-lookup"><span data-stu-id="0ab9f-110">Configuring the Device</span></span>

<span data-ttu-id="0ab9f-111">Após [abrindo uma interface]() para o dispositivo Azure Kinect DK, você precisará configurar a câmera para capturar dados de profundidade.</span><span class="sxs-lookup"><span data-stu-id="0ab9f-111">After [opening an interface]() to the Azure Kinect DK device, you'll need to configure the camera for capturing depth data.</span></span> <span data-ttu-id="0ab9f-112">Há apenas um item que você realmente precisa saber sobre ao configurar a profundidade, e que o `depth_mode`!</span><span class="sxs-lookup"><span data-stu-id="0ab9f-112">There's only one item you really need to know about when configuring depth, and that's the `depth_mode`!</span></span>

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="0ab9f-113">Aqui o `depth_mode` tem duas opções!</span><span class="sxs-lookup"><span data-stu-id="0ab9f-113">Here the `depth_mode` has a couple choices!</span></span> <span data-ttu-id="0ab9f-114">Dependendo do contexto de nosso aplicativo, podemos pode solicitar nossos dados de profundidade em formatos diferentes.</span><span class="sxs-lookup"><span data-stu-id="0ab9f-114">Depending on the context of our application, we can request our depth data in different formats.</span></span>

<span data-ttu-id="0ab9f-115">Você está executando algoritmos restringidas ao tempo nos dados de profundidade?</span><span class="sxs-lookup"><span data-stu-id="0ab9f-115">Are you running time constrained algorithms on the depth data?</span></span> <span data-ttu-id="0ab9f-116">Talvez, escolha um modo de 2X2BINNED para que haja menos dados no qual operar!</span><span class="sxs-lookup"><span data-stu-id="0ab9f-116">Maybe pick a 2X2BINNED mode so there's less data to operate on!</span></span> <span data-ttu-id="0ab9f-117">Isso importa mais sobre o que é o momento out diretamente à frente, em vez do que é fechar e na periferia?</span><span class="sxs-lookup"><span data-stu-id="0ab9f-117">Do you care more about what's far out directly ahead, rather than what's close and in the periphery?</span></span> <span data-ttu-id="0ab9f-118">Use um campo de visão estreito com os modos de NFOV!</span><span class="sxs-lookup"><span data-stu-id="0ab9f-118">Use a narrow field of view with the NFOV modes!</span></span>
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | <span data-ttu-id="0ab9f-119">description</span><span class="sxs-lookup"><span data-stu-id="0ab9f-119">description</span></span> |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|<span data-ttu-id="0ab9f-120">Ângulo ampla exibição (120 x 120), profundidade superficial (0,25-2.21 m), dados de alta resolução (1024 x 1024).</span><span class="sxs-lookup"><span data-stu-id="0ab9f-120">Wide angle view (120x120), shallow depth (0.25-2.21m), high data resolution (1024x1024).</span></span> <span data-ttu-id="0ab9f-121">Tem uma taxa de quadros de máximo de 15.</span><span class="sxs-lookup"><span data-stu-id="0ab9f-121">Has a maximum framerate of 15.</span></span>|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|<span data-ttu-id="0ab9f-122">Ângulo ampla exibição (120 x 120), profundidade superficial (0,25-2,88 m), dados de baixa resolução (512 x 512).</span><span class="sxs-lookup"><span data-stu-id="0ab9f-122">Wide angle view (120x120), shallow depth (0.25-2.88m), low data resolution (512x512).</span></span>|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|<span data-ttu-id="0ab9f-123">Ângulo estreita exibição (75 x 65), profundidade distante (0,5-3.86 m), dados de alta resolução (640 x 576).</span><span class="sxs-lookup"><span data-stu-id="0ab9f-123">Narrow angle view (75x65), far depth (0.5-3.86m), high data resolution (640x576).</span></span>|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|<span data-ttu-id="0ab9f-124">Ângulo estreita exibição (75 x 65), profundidade distante (0,5-5,46 m), dados de baixa resolução (320 x 288).</span><span class="sxs-lookup"><span data-stu-id="0ab9f-124">Narrow angle view (75x65), far depth (0.5-5.46m), low data resolution (320x288).</span></span>|
|`K4A_DEPTH_MODE_PASSIVE_IR`|<span data-ttu-id="0ab9f-125">RAW feed da câmera IR (1024 x 1024)</span><span class="sxs-lookup"><span data-stu-id="0ab9f-125">Raw feed from the IR camera (1024x1024)</span></span>|
||<span data-ttu-id="0ab9f-126">Profundidade será fornecida fora do intervalo indicado dependendo reflexibilidade do objeto.</span><span class="sxs-lookup"><span data-stu-id="0ab9f-126">Depth will be provided outside of indicated range depending on object reflectivity.</span></span>|

## <a name="acessing-depth-data"></a><span data-ttu-id="0ab9f-127">Profundidade acessando dados</span><span class="sxs-lookup"><span data-stu-id="0ab9f-127">Acessing Depth Data</span></span>

![](img/Depth.png)

<span data-ttu-id="0ab9f-128">Quando podemos capturar um quadro do dispositivo, podemos usar `k4a_capture_get_depth_image` e `k4a_image_get_buffer` para obter os dados brutos de profundidade!</span><span class="sxs-lookup"><span data-stu-id="0ab9f-128">When we capture a frame from the device, we can use `k4a_capture_get_depth_image` and `k4a_image_get_buffer` to get the raw depth data!</span></span>

```C
// Capture a frame
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the depth data and information from the current capture
k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
int32_t width  = k4a_image_get_width_pixels (depth_image);
int32_t height = k4a_image_get_height_pixels(depth_image);
```

<span data-ttu-id="0ab9f-129">Informações de profundidade são fornecidas como uma matriz de inteiros sem sinal de 16 bits, que representa o milímetros da câmera.</span><span class="sxs-lookup"><span data-stu-id="0ab9f-129">Depth information is provided as an array of unsigned 16 bit integers, representing millimeters from the camera.</span></span> <span data-ttu-id="0ab9f-130">A matriz conterá um zero se o valor de profundidade não estiver presente para um determinado pixel.</span><span class="sxs-lookup"><span data-stu-id="0ab9f-130">The array will hold a zero if the depth value isn't present for a particular pixel.</span></span>

<span data-ttu-id="0ab9f-131">Neste exemplo, estamos apenas vai converter os dados de profundidade em uma imagem em escala de cinza e salvá-lo em um arquivo!</span><span class="sxs-lookup"><span data-stu-id="0ab9f-131">In this example, we'll just convert the depth data into a grayscale image, and save it to file!</span></span>

```C
// Write this depth capture to an image file

// Allocate memory for an 8-bit grayscale image
uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

// Convert each depth value to a shade of gray!
for (int32_t i = 0; i < width*height; i++)
{
    // Make a gray from the depth, white up close, black at 3 meters in the distance
    float depth_gray = 1-(depth_buffer[i] / 3000.0f);
    // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
    depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

    file_color[i] = static_cast<uint8_t>(depth_gray * 255);
}
tga_write("outDepth.tga", width, height, file_color, 1, 3);
free(file_color);
```

## <a name="cleaning-up"></a><span data-ttu-id="0ab9f-132">Limpando</span><span class="sxs-lookup"><span data-stu-id="0ab9f-132">Cleaning Up</span></span>

<span data-ttu-id="0ab9f-133">Lembre-se desligar e liberar tudo o que você já alocado ou capturados!</span><span class="sxs-lookup"><span data-stu-id="0ab9f-133">Remember to shut down and release everything you've allocated or grabbed!</span></span> <span data-ttu-id="0ab9f-134">Lembre-se de que as capturas de quadro devem ser liberadas depois que tiver terminado com eles e antes da captura outro quadro.</span><span class="sxs-lookup"><span data-stu-id="0ab9f-134">Remember that frame captures should be freed after you're finished with them and before grabbing another frame.</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="0ab9f-135">Código-fonte completo</span><span class="sxs-lookup"><span data-stu-id="0ab9f-135">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 1024x1024 wide FOV at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_5;
    config.depth_mode = K4A_DEPTH_MODE_WFOV_UNBINNED;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the depth data and information from the current capture
    k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
    uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
    int32_t width  = k4a_image_get_width_pixels (depth_image);
    int32_t height = k4a_image_get_height_pixels(depth_image);
    printf("Captured depth image, %dx%d\n", width, height);

    // Write this depth capture to an image file

    // Allocate memory for an 8-bit grayscale image
    uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

    // Convert each depth value to a shade of gray!
    for (int32_t i = 0; i < width*height; i++)
    {
        // Make a gray from the depth, white up close, black at 3 meters in the distance
        float depth_gray = 1-(depth_buffer[i] / 3000.0f);
        // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
        depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

        file_color[i] = static_cast<uint8_t>(depth_gray * 255);
    }
    tga_write("outDepth.tga", width, height, file_color, 1, 3);
    free(file_color);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(depth_image);
    k4a_capture_release(capture);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width % 256, (uint8_t)(width / 256), height % 256, (uint8_t)(height / 256), file_channels * 8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---reading-rgb-datareadcolormd"></a><span data-ttu-id="0ab9f-136">Próximo laboratório - [lendo dados RGB](ReadColor.md)</span><span class="sxs-lookup"><span data-stu-id="0ab9f-136">Next Lab - [Reading RGB Data](ReadColor.md)</span></span>