# <a name="setting-up"></a>Como configurar

Guia de Introdução com a API do Azure Kinect DK? Não procure mais! Este documento irá proporcionar a você tudo em funcionamento com acesso ao dispositivo!

Primeiro, baixe e instale o [API do Azure Kinect DK](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) do Github.

**Conteúdo**  
[Cabeçalhos](#Headers)  
[Localizando um dispositivo Kinect](#Finding-a-Kinect-Device)  
[Iniciando as câmeras](#Starting-the-Cameras)  
[Tratamento de erros](#Error-Handling)  
[Código-fonte completo](#Full-Source)  

**Aqui estão as funções que usaremos:**  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a>Cabeçalhos
Há apenas um cabeçalho que você vai precisar, e que é k4a.h! Verifique se que o compilador de escolha é configurada com lib do SDK e incluir pastas. Os arquivos k4a.lib e k4a.dll vinculados também será necessário.
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a>Localizando um dispositivo Kinect

![](img/Serial.png)

Vários dispositivos Azure Kinect DK podem ser conectados ao computador! Vamos começar pela primeira vez pelo Localizando out quantos, ou se qualquer um estiver conectado a alguma usando o [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) função. Essa função deve funcionar imediatamente, sem nenhuma configuração adicional!

```C
uint32_t count = k4a_device_get_installed_count();
```

Depois de determinar lá está, na verdade, um dispositivo conectado ao computador, você pode abri-lo usando [ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open). Você pode fornecer o índice do dispositivo que deseja abrir, ou você pode usar apenas [ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) para o primeiro.

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
Como com a maioria das coisas na API do k4a, quando você abre algo, você deve também fechá-lo quando tiver terminado com ele! Quando você estiver desligado, lembre-se de fazer uma chamada para [ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).

```C
k4a_device_close(device);
```

Quando o dispositivo é aberto, podemos fazer um teste realmente simples para garantir que ele é muito bom. Então, vamos ler o número de série do dispositivo!

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

## <a name="starting-the-cameras"></a>Iniciando as câmeras

Depois de abrir o dispositivo, você precisará configurar a câmera com um [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) objeto! A configuração de câmera tem várias opções diferentes, e você precisará escolher as configurações que melhor se ajustam ao seu próprio cenário.

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

Para obter detalhes de configuração sobre o __cor__ câmera, [check-out neste documento]()!  
Para obter detalhes de configuração sobre o __profundidade__ câmera, [check-out neste documento]()!

## <a name="error-handling"></a>Tratamento de erro

Para fins de brevidade e clareza, não mostraremos alguns exemplos de embutido de tratamento de erros. No entanto, tratamento de erro é sempre importante! Muitas funções retornará um tipo de êxito/falha geral [ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), ou uma variante mais específica com informações detalhadas, como [ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t). Verifique os documentos ou intellisense de uma função específica para ver quais mensagens de erro que você pode esperar ver dele!

Além dos tipos de erro, há também o [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) e [ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macros que você pode usar com eles. Portanto, em vez de apenas abrir um dispositivo k4a, podemos pode Proteja-o assim:

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a>Código-fonte completo

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

## <a name="next-lab---reading-depth-datareaddepthmd"></a>Próximo laboratório - [lendo dados de profundidade](ReadDepth.md)
