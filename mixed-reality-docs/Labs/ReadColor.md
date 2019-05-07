# <a name="reading-rgb-data"></a>Lendo dados RGB

**Conteúdo**  
[Configuração do dispositivo](#Configuring-the-Device)  
[Obtendo um quadro de cor](#Getting-a-Color-Frame)  
[Limpando](#Cleaning-Up)  
[Código-fonte completo](#Full-Source)  

**Aqui estão as funções que usaremos:**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a>Configuração do dispositivo

Após [abrir um dispositivo k4a](), precisaremos configurar câmeras para capturar dados de cor! Há muitas opções aqui também, portanto, vamos abordá-los. Aqui está um exemplo rápido de sua aparência para iniciar uma câmera de cor básico realmente.

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

O `color_format` permite-nos dizer como queremos que nossas informações de cor armazenadas no buffer de imagem! `K4A_IMAGE_FORMAT_COLOR_BGRA32` seria de 32 bits por pixel, armazenados como 8 bits cada para alfa, vermelho, verde e azul. Podemos usar esse formato nos exemplos devido a sua conveniência, mas se você quiser ser concious de uso de memória, outros formatos podem ser excelentes opções!

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|Dados de cor estarão em [formato JPEG de movimento](https://en.wikipedia.org/wiki/Motion_JPEG)|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|[YUV](https://en.wikipedia.org/wiki/YUV) 4:2 de espaço de cores: formato 0, NV12, disponível apenas na resolução de 720p.|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|[YUV](https://en.wikipedia.org/wiki/YUV) 4:2 de espaço de cores: formato 2, YUY2, disponível apenas na resolução de 720p.|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|Dados brutos de cor, 32 bits por pixel, ordenados como azul, verde, vermelho e alfa|

Durante a gravação sua própria conversão YUV pode ser bem fácil, uma biblioteca rápida e robusta para conversão YUV pode ser encontrado em [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).

O `color_resolution` também tem algumas opções!

|`color_resolution`|Resolução|Aspecto|campo de visão| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | 1280 x 720  | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1080P` | 1920 x 1080 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1440P` | 2560 x 1440 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_2160P` | 3840 x 2160 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1536P` | 2048 x 1536 | 4:3  | 90x74.3 
|`K4A_COLOR_RESOLUTION_3072P` | 4096 x 3072 | 4:3  | 90x74.3 | Taxa de quadros máxima 15.

E, claro, o `camera_fps` também.

|camera_fps||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a>Obtendo um quadro de cor

A obtenção de dados para uma cor e um quadro de profundidade é um processo muito semelhante! Primeiro, obtemos uma captura do dispositivo, em seguida, podemos extrair a imagem de cores dele e, em seguida, podemos extrair os dados brutos fora dessa imagem.

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

Os dados armazenados agora no `colorDataBRGA` é dependente no formato indicado na configuração. Uma vez que eu pedi `K4A_IMAGE_FORMAT_COLOR_BGRA32`, temos uma matriz completa de valores de cor de 32 bits armazenados em BGRA ordem!

Nesse caso, os arquivos. tga armazenam cores na ordem BGR já! E, desde que a nossa função salvando pode ignorar o canal alfa com estes argumentos, que podemos passar apenas os dados da imagem como é!

## <a name="cleaning-up"></a>Limpando

E, como sempre, lembre-se de seus recursos de versão quando você terminar com elas!
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a>Código-fonte completo

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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a>Próximo laboratório - [combinação de cor e dados de profundidade](MixDepthAndRGB.md)