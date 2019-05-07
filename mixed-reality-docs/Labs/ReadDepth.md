# <a name="reading-depth-data"></a>Lendo dados de profundidade

Você precisa ler dados de profundidade do dispositivo? É fácil!

**Conteúdo**  
[Configuração do dispositivo](#Configuring-the-Device)  
[Profundidade acessando dados](#Acessing-Depth-Data)  
[Limpando](#Cleaning-Up)  
[Código-fonte completo](#Full-Source)  

**Aqui estão as funções que usaremos:**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a>Configuração do dispositivo

Após [abrindo uma interface]() para o dispositivo Azure Kinect DK, você precisará configurar a câmera para capturar dados de profundidade. Há apenas um item que você realmente precisa saber sobre ao configurar a profundidade, e que o `depth_mode`!

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

Aqui o `depth_mode` tem duas opções! Dependendo do contexto de nosso aplicativo, podemos pode solicitar nossos dados de profundidade em formatos diferentes.

Você está executando algoritmos restringidas ao tempo nos dados de profundidade? Talvez, escolha um modo de 2X2BINNED para que haja menos dados no qual operar! Isso importa mais sobre o que é o momento out diretamente à frente, em vez do que é fechar e na periferia? Use um campo de visão estreito com os modos de NFOV!
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | description |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|Ângulo ampla exibição (120 x 120), profundidade superficial (0,25-2.21 m), dados de alta resolução (1024 x 1024). Tem uma taxa de quadros de máximo de 15.|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|Ângulo ampla exibição (120 x 120), profundidade superficial (0,25-2,88 m), dados de baixa resolução (512 x 512).|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|Ângulo estreita exibição (75 x 65), profundidade distante (0,5-3.86 m), dados de alta resolução (640 x 576).|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|Ângulo estreita exibição (75 x 65), profundidade distante (0,5-5,46 m), dados de baixa resolução (320 x 288).|
|`K4A_DEPTH_MODE_PASSIVE_IR`|RAW feed da câmera IR (1024 x 1024)|
||Profundidade será fornecida fora do intervalo indicado dependendo reflexibilidade do objeto.|

## <a name="acessing-depth-data"></a>Profundidade acessando dados

![](img/Depth.png)

Quando podemos capturar um quadro do dispositivo, podemos usar `k4a_capture_get_depth_image` e `k4a_image_get_buffer` para obter os dados brutos de profundidade!

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

Informações de profundidade são fornecidas como uma matriz de inteiros sem sinal de 16 bits, que representa o milímetros da câmera. A matriz conterá um zero se o valor de profundidade não estiver presente para um determinado pixel.

Neste exemplo, estamos apenas vai converter os dados de profundidade em uma imagem em escala de cinza e salvá-lo em um arquivo!

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

## <a name="cleaning-up"></a>Limpando

Lembre-se desligar e liberar tudo o que você já alocado ou capturados! Lembre-se de que as capturas de quadro devem ser liberadas depois que tiver terminado com eles e antes da captura outro quadro.

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a>Código-fonte completo

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

## <a name="next-lab---reading-rgb-datareadcolormd"></a>Próximo laboratório - [lendo dados RGB](ReadColor.md)