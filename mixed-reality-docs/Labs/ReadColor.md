# <a name="reading-rgb-data"></a><span data-ttu-id="a6eb2-101">Lendo dados RGB</span><span class="sxs-lookup"><span data-stu-id="a6eb2-101">Reading RGB Data</span></span>

<span data-ttu-id="a6eb2-102">**Conteúdo**</span><span class="sxs-lookup"><span data-stu-id="a6eb2-102">**Contents**</span></span>  
[<span data-ttu-id="a6eb2-103">Configuração do dispositivo</span><span class="sxs-lookup"><span data-stu-id="a6eb2-103">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="a6eb2-104">Obtendo um quadro de cor</span><span class="sxs-lookup"><span data-stu-id="a6eb2-104">Getting a Color Frame</span></span>](#Getting-a-Color-Frame)  
[<span data-ttu-id="a6eb2-105">Limpando</span><span class="sxs-lookup"><span data-stu-id="a6eb2-105">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="a6eb2-106">Código-fonte completo</span><span class="sxs-lookup"><span data-stu-id="a6eb2-106">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="a6eb2-107">**Aqui estão as funções que usaremos:**</span><span class="sxs-lookup"><span data-stu-id="a6eb2-107">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a><span data-ttu-id="a6eb2-108">Configuração do dispositivo</span><span class="sxs-lookup"><span data-stu-id="a6eb2-108">Configuring the Device</span></span>

<span data-ttu-id="a6eb2-109">Após [abrir um dispositivo k4a](), precisaremos configurar câmeras para capturar dados de cor!</span><span class="sxs-lookup"><span data-stu-id="a6eb2-109">After [opening a k4a device](), we'll need to set up the cameras to grab color data!</span></span> <span data-ttu-id="a6eb2-110">Há muitas opções aqui também, portanto, vamos abordá-los.</span><span class="sxs-lookup"><span data-stu-id="a6eb2-110">There's a lot of options here as well, so we'll go through them.</span></span> <span data-ttu-id="a6eb2-111">Aqui está um exemplo rápido de sua aparência para iniciar uma câmera de cor básico realmente.</span><span class="sxs-lookup"><span data-stu-id="a6eb2-111">Here's a quick example of what it looks like to start up a really basic color camera.</span></span>

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="a6eb2-112">O `color_format` permite-nos dizer como queremos que nossas informações de cor armazenadas no buffer de imagem!</span><span class="sxs-lookup"><span data-stu-id="a6eb2-112">The `color_format` allows us to say how we want our color information stored in the image buffer!</span></span> <span data-ttu-id="a6eb2-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` seria de 32 bits por pixel, armazenados como 8 bits cada para alfa, vermelho, verde e azul.</span><span class="sxs-lookup"><span data-stu-id="a6eb2-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` would be 32 bits per pixel, stored as 8 bits each for Blue, Green, Red, and Alpha.</span></span> <span data-ttu-id="a6eb2-114">Podemos usar esse formato nos exemplos devido a sua conveniência, mas se você quiser ser concious de uso de memória, outros formatos podem ser excelentes opções!</span><span class="sxs-lookup"><span data-stu-id="a6eb2-114">We use this format in the examples due to its convenience, but if you want to be concious of memory usage, other formats may be superior choices!</span></span>

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|<span data-ttu-id="a6eb2-115">Dados de cor estarão em [formato JPEG de movimento](https://en.wikipedia.org/wiki/Motion_JPEG)</span><span class="sxs-lookup"><span data-stu-id="a6eb2-115">Color data will be in [Motion JPEG format](https://en.wikipedia.org/wiki/Motion_JPEG)</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|<span data-ttu-id="a6eb2-116">[YUV](https://en.wikipedia.org/wiki/YUV) 4:2 de espaço de cores: formato 0, NV12, disponível apenas na resolução de 720p.</span><span class="sxs-lookup"><span data-stu-id="a6eb2-116">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:0 format, NV12, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|<span data-ttu-id="a6eb2-117">[YUV](https://en.wikipedia.org/wiki/YUV) 4:2 de espaço de cores: formato 2, YUY2, disponível apenas na resolução de 720p.</span><span class="sxs-lookup"><span data-stu-id="a6eb2-117">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:2 format, YUY2, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|<span data-ttu-id="a6eb2-118">Dados brutos de cor, 32 bits por pixel, ordenados como azul, verde, vermelho e alfa</span><span class="sxs-lookup"><span data-stu-id="a6eb2-118">Raw color data, 32 bits per pixel, ordered as Blue, Green, Red, Alpha</span></span>|

<span data-ttu-id="a6eb2-119">Durante a gravação sua própria conversão YUV pode ser bem fácil, uma biblioteca rápida e robusta para conversão YUV pode ser encontrado em [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).</span><span class="sxs-lookup"><span data-stu-id="a6eb2-119">While writing your own YUV conversion may be easy enough, a fast, robust library for YUV conversion can be found at [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).</span></span>

<span data-ttu-id="a6eb2-120">O `color_resolution` também tem algumas opções!</span><span class="sxs-lookup"><span data-stu-id="a6eb2-120">The `color_resolution` also has a couple of options!</span></span>

|`color_resolution`|<span data-ttu-id="a6eb2-121">Resolução</span><span class="sxs-lookup"><span data-stu-id="a6eb2-121">resolution</span></span>|<span data-ttu-id="a6eb2-122">Aspecto</span><span class="sxs-lookup"><span data-stu-id="a6eb2-122">aspect</span></span>|<span data-ttu-id="a6eb2-123">campo de visão</span><span class="sxs-lookup"><span data-stu-id="a6eb2-123">field of view</span></span>| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | <span data-ttu-id="a6eb2-124">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="a6eb2-124">1280 x 720</span></span>  | <span data-ttu-id="a6eb2-125">16:9</span><span class="sxs-lookup"><span data-stu-id="a6eb2-125">16:9</span></span> | <span data-ttu-id="a6eb2-126">90x59</span><span class="sxs-lookup"><span data-stu-id="a6eb2-126">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1080P` | <span data-ttu-id="a6eb2-127">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="a6eb2-127">1920 x 1080</span></span> | <span data-ttu-id="a6eb2-128">16:9</span><span class="sxs-lookup"><span data-stu-id="a6eb2-128">16:9</span></span> | <span data-ttu-id="a6eb2-129">90x59</span><span class="sxs-lookup"><span data-stu-id="a6eb2-129">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1440P` | <span data-ttu-id="a6eb2-130">2560 x 1440</span><span class="sxs-lookup"><span data-stu-id="a6eb2-130">2560 x 1440</span></span> | <span data-ttu-id="a6eb2-131">16:9</span><span class="sxs-lookup"><span data-stu-id="a6eb2-131">16:9</span></span> | <span data-ttu-id="a6eb2-132">90x59</span><span class="sxs-lookup"><span data-stu-id="a6eb2-132">90x59</span></span>
|`K4A_COLOR_RESOLUTION_2160P` | <span data-ttu-id="a6eb2-133">3840 x 2160</span><span class="sxs-lookup"><span data-stu-id="a6eb2-133">3840 x 2160</span></span> | <span data-ttu-id="a6eb2-134">16:9</span><span class="sxs-lookup"><span data-stu-id="a6eb2-134">16:9</span></span> | <span data-ttu-id="a6eb2-135">90x59</span><span class="sxs-lookup"><span data-stu-id="a6eb2-135">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1536P` | <span data-ttu-id="a6eb2-136">2048 x 1536</span><span class="sxs-lookup"><span data-stu-id="a6eb2-136">2048 x 1536</span></span> | <span data-ttu-id="a6eb2-137">4:3</span><span class="sxs-lookup"><span data-stu-id="a6eb2-137">4:3</span></span>  | <span data-ttu-id="a6eb2-138">90x74.3</span><span class="sxs-lookup"><span data-stu-id="a6eb2-138">90x74.3</span></span> 
|`K4A_COLOR_RESOLUTION_3072P` | <span data-ttu-id="a6eb2-139">4096 x 3072</span><span class="sxs-lookup"><span data-stu-id="a6eb2-139">4096 x 3072</span></span> | <span data-ttu-id="a6eb2-140">4:3</span><span class="sxs-lookup"><span data-stu-id="a6eb2-140">4:3</span></span>  | <span data-ttu-id="a6eb2-141">90x74.3</span><span class="sxs-lookup"><span data-stu-id="a6eb2-141">90x74.3</span></span> | <span data-ttu-id="a6eb2-142">Taxa de quadros máxima 15.</span><span class="sxs-lookup"><span data-stu-id="a6eb2-142">Max framerate 15.</span></span>

<span data-ttu-id="a6eb2-143">E, claro, o `camera_fps` também.</span><span class="sxs-lookup"><span data-stu-id="a6eb2-143">And of course, the `camera_fps` as well.</span></span>

|<span data-ttu-id="a6eb2-144">camera_fps</span><span class="sxs-lookup"><span data-stu-id="a6eb2-144">camera_fps</span></span>||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a><span data-ttu-id="a6eb2-145">Obtendo um quadro de cor</span><span class="sxs-lookup"><span data-stu-id="a6eb2-145">Getting a Color Frame</span></span>

<span data-ttu-id="a6eb2-146">A obtenção de dados para uma cor e um quadro de profundidade é um processo muito semelhante!</span><span class="sxs-lookup"><span data-stu-id="a6eb2-146">Getting data for a color frame and a depth frame is a very similar process!</span></span> <span data-ttu-id="a6eb2-147">Primeiro, obtemos uma captura do dispositivo, em seguida, podemos extrair a imagem de cores dele e, em seguida, podemos extrair os dados brutos fora dessa imagem.</span><span class="sxs-lookup"><span data-stu-id="a6eb2-147">First we get a capture from the device, then we extract the color image from it, and then we pull the raw data out of that image.</span></span>

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the color data and information from the current capture
k4a_image_t colors      = k4a_capture_get_color_image(capture);
uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
int width  = k4a_image_get_width_pixels (colors);
int height = k4a_image_get_height_pixels(colors);

// Write this capture to file
tga_write("out.tga", width, height, colorDataBGRA, 4, 3);
```

<span data-ttu-id="a6eb2-148">Os dados armazenados agora no `colorDataBRGA` é dependente no formato indicado na configuração.</span><span class="sxs-lookup"><span data-stu-id="a6eb2-148">The data now stored in `colorDataBRGA` is dependant on the format we indicated in configuration.</span></span> <span data-ttu-id="a6eb2-149">Uma vez que eu pedi `K4A_IMAGE_FORMAT_COLOR_BGRA32`, temos uma matriz completa de valores de cor de 32 bits armazenados em BGRA ordem!</span><span class="sxs-lookup"><span data-stu-id="a6eb2-149">Since we asked for `K4A_IMAGE_FORMAT_COLOR_BGRA32`, we have an array full of 32 bit color values stored in BGRA order!</span></span>

<span data-ttu-id="a6eb2-150">Nesse caso, os arquivos. tga armazenam cores na ordem BGR já!</span><span class="sxs-lookup"><span data-stu-id="a6eb2-150">In this case, .tga files store colors in BGR order already!</span></span> <span data-ttu-id="a6eb2-151">E, desde que a nossa função salvando pode ignorar o canal alfa com estes argumentos, que podemos passar apenas os dados da imagem como é!</span><span class="sxs-lookup"><span data-stu-id="a6eb2-151">And since our saving function can skip the alpha channel with these arguments, we can just pass the image data as is!</span></span>

## <a name="cleaning-up"></a><span data-ttu-id="a6eb2-152">Limpando</span><span class="sxs-lookup"><span data-stu-id="a6eb2-152">Cleaning Up</span></span>

<span data-ttu-id="a6eb2-153">E, como sempre, lembre-se de seus recursos de versão quando você terminar com elas!</span><span class="sxs-lookup"><span data-stu-id="a6eb2-153">And as always, remember to release your resources when you're done with them!</span></span>
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a><span data-ttu-id="a6eb2-154">Código-fonte completo</span><span class="sxs-lookup"><span data-stu-id="a6eb2-154">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main() {
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure a stream of 1280x720 BRGA data at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the color data and information from the current capture
    k4a_image_t colors      = k4a_capture_get_color_image(capture);
    uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
    int width  = k4a_image_get_width_pixels (colors);
    int height = k4a_image_get_height_pixels(colors);
    printf("Captured RGB image, %dx%d\n", width, height);

    // Write this capture to file
    tga_write("out.tga", width, height, colors_bgra, 4, 3);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(colors);
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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a><span data-ttu-id="a6eb2-155">Próximo laboratório - [combinação de cor e dados de profundidade](MixDepthAndRGB.md)</span><span class="sxs-lookup"><span data-stu-id="a6eb2-155">Next Lab - [Mixing Color and Depth Data](MixDepthAndRGB.md)</span></span>