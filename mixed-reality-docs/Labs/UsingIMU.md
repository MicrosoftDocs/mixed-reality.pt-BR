# <a name="accessing-the-imu"></a><span data-ttu-id="00405-101">Acessando o IMU</span><span class="sxs-lookup"><span data-stu-id="00405-101">Accessing the IMU</span></span>

<span data-ttu-id="00405-102">Azure Kinect DK contém uma unidade de medida inercial (IMU)!</span><span class="sxs-lookup"><span data-stu-id="00405-102">Azure Kinect DK contains an Inertial Measurement Unit (IMU)!</span></span> <span data-ttu-id="00405-103">Isso pode ser útil para ajudar a determinar o movimento e a orientação do dispositivo durante a captura.</span><span class="sxs-lookup"><span data-stu-id="00405-103">This can be useful for helping to determine motion and orientation of the device during capture.</span></span> <span data-ttu-id="00405-104">Especialmente se o dispositivo não está parado!</span><span class="sxs-lookup"><span data-stu-id="00405-104">Especially if you device isn't stationary!</span></span>

<span data-ttu-id="00405-105">**Conteúdo:**</span><span class="sxs-lookup"><span data-stu-id="00405-105">**Contents:**</span></span>  
[<span data-ttu-id="00405-106">Instalação e configuração</span><span class="sxs-lookup"><span data-stu-id="00405-106">Configuration and Setup</span></span>](#Configuration-and-Setup)  
[<span data-ttu-id="00405-107">Obtendo dados</span><span class="sxs-lookup"><span data-stu-id="00405-107">Getting Data</span></span>](#Getting-Data)  
[<span data-ttu-id="00405-108">Limpando</span><span class="sxs-lookup"><span data-stu-id="00405-108">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="00405-109">Código-fonte completo</span><span class="sxs-lookup"><span data-stu-id="00405-109">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="00405-110">**Aqui estão as funções que usaremos:**</span><span class="sxs-lookup"><span data-stu-id="00405-110">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_imu()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-imu)  
[`k4a_device_stop_imu()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-imu)  
[`k4a_device_get_imu_sample()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-imu-sample)  

## <a name="configuration-and-setup"></a><span data-ttu-id="00405-111">Instalação e configuração</span><span class="sxs-lookup"><span data-stu-id="00405-111">Configuration and Setup</span></span>

<span data-ttu-id="00405-112">Configuração aqui é muito simple!</span><span class="sxs-lookup"><span data-stu-id="00405-112">Configuration here is pretty simple!</span></span> <span data-ttu-id="00405-113">Não há itens você precisa especificar na configuração do dispositivo para IMU amostragem funcionam, mas você precisará chamar `k4a_device_start_cameras` antes que ele vai trabalhar!</span><span class="sxs-lookup"><span data-stu-id="00405-113">There are no items you need to specify the in the device configuration for IMU sampling to work, but you will need to call `k4a_device_start_cameras` before it'll work!</span></span> <span data-ttu-id="00405-114">Em vez disso, você fará uma chamada para `k4a_device_start_imu` depois de iniciar as câmeras.</span><span class="sxs-lookup"><span data-stu-id="00405-114">Instead, you'll make a call to `k4a_device_start_imu` after starting the cameras.</span></span>

```C
// Cameras need to be 'started' even if all we want is the IMU
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
k4a_device_start_cameras(device, &config);

// Start up the IMU sensors
k4a_device_start_imu(device);
```

## <a name="getting-data"></a><span data-ttu-id="00405-115">Obtendo dados</span><span class="sxs-lookup"><span data-stu-id="00405-115">Getting Data</span></span>

<span data-ttu-id="00405-116">![Imagem de aplicativo de exemplo IMU](img/IMU.png "aqui está o que vamos compilar como um exemplo!")</span><span class="sxs-lookup"><span data-stu-id="00405-116">![IMU sample app image](img/IMU.png "Here's what we'll build as an example!")</span></span>

<span data-ttu-id="00405-117">O IMU fornece dados a uma taxa de 1.6 kHz!</span><span class="sxs-lookup"><span data-stu-id="00405-117">The IMU provides data at a rate of 1.6kHz!</span></span> <span data-ttu-id="00405-118">Há muitos dados, e isso significa que, se você está procurando apenas isso sempre que um quadro de profundidade/cor está disponível, você provavelmente terá uma grande fila de amostras IMU esperando por você!</span><span class="sxs-lookup"><span data-stu-id="00405-118">That's a lot of data, and this means that if you're only looking at it each time a depth/color frame is available, you'll likely have quite a queue of IMU samples waiting for you!</span></span> <span data-ttu-id="00405-119">Observe que esses dados não são uma orientação ou posição, mas em vez disso, uma medida da força atualmente aplicada ao dispositivo.</span><span class="sxs-lookup"><span data-stu-id="00405-119">Note that this data is not an orientation or position, but rather, a measure of the force currently applied to the device.</span></span>

<span data-ttu-id="00405-120">Podemos pegar um exemplo e removê-lo da fila chamando `k4a_device_get_imu_sample` com um tempo limite de 0 milissegundo.</span><span class="sxs-lookup"><span data-stu-id="00405-120">We can grab a sample and remove it from the queue by calling `k4a_device_get_imu_sample` with a timeout of 0 milliseconds.</span></span> <span data-ttu-id="00405-121">Ela vai retornar `K4A_WAIT_RESULT_SUCCEEDED` desde que ele tem um exemplo disponível!</span><span class="sxs-lookup"><span data-stu-id="00405-121">It'll return `K4A_WAIT_RESULT_SUCCEEDED` as long as it has a sample available!</span></span>

<span data-ttu-id="00405-122">Aqui está um exemplo de soma de todos os exemplos atualmente na fila e a média de impressão.</span><span class="sxs-lookup"><span data-stu-id="00405-122">Here's an example of summing all the samples currently in the queue, and printing the average.</span></span> 

```C
k4a_float3_t gyro_sum  = {0};
k4a_float3_t acc_sum   = {0};
int32_t      sum_count = 0;

// Sum the current queue of IMU samples
k4a_imu_sample_t sample;
while (k4a_device_get_imu_sample(device, &sample, 0) == K4A_WAIT_RESULT_SUCCEEDED)
{
    gyro_sum.xyz = { 
        gyro_sum.xyz.x + sample.gyro_sample.xyz.x, 
        gyro_sum.xyz.y + sample.gyro_sample.xyz.y, 
        gyro_sum.xyz.z + sample.gyro_sample.xyz.z };
    acc_sum.xyz = { 
        acc_sum.xyz.x + sample.acc_sample.xyz.x,  
        acc_sum.xyz.y + sample.acc_sample.xyz.y,  
        acc_sum.xyz.z + sample.acc_sample.xyz.z };
    sum_count += 1;
    samples   += 1;
}

// If we got any samples, print out their average!
if (sum_count > 0)
{
    k4a_float3_t gyro_avg = {
        gyro_sum.xyz.x / sum_count,
        gyro_sum.xyz.y / sum_count,
        gyro_sum.xyz.z / sum_count };
    k4a_float3_t acc_avg = {
        acc_sum.xyz.x / sum_count,
        acc_sum.xyz.y / sum_count,
        acc_sum.xyz.z / sum_count };

    printf("<%6.2f, %6.2f, %6.2f>   ", gyro_avg.xyz.x, gyro_avg.xyz.y, gyro_avg.xyz.z);
    printf("<%6.2f, %6.2f, %6.2f>", acc_avg.xyz.x, acc_avg.xyz.y, acc_avg.xyz.z);

    // Write backspaces so we'll overwrite this line next time
    printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
    printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
}
```

## <a name="cleaning-up"></a><span data-ttu-id="00405-123">Limpando</span><span class="sxs-lookup"><span data-stu-id="00405-123">Cleaning Up</span></span>

<span data-ttu-id="00405-124">E como sempre, liberar tudo quando tiver terminado :)</span><span class="sxs-lookup"><span data-stu-id="00405-124">And as always, release everything when you're finished :)</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_device_stop_imu(device);
k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="00405-125">Código-fonte completo</span><span class="sxs-lookup"><span data-stu-id="00405-125">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Cameras need to be 'started' even if all we want is the IMU
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    k4a_device_start_cameras(device, &config);

    // Start up the IMU sensors
    k4a_device_start_imu(device);

    // Display 10,000 samples as fast as they arrive
    printf("Sampling 10,000 times.\n");
    printf("Gyroscope radians/s:       Accelerometer meters/s^2:\n");
    int32_t samples = 0;
    while (samples < 10000)
    {
        k4a_float3_t gyro_sum  = {0};
        k4a_float3_t accel_sum = {0};
        int32_t      sum_count = 0;

        // Sum the current queue of IMU samples
        k4a_imu_sample_t sample;
        while (k4a_device_get_imu_sample(device, &sample, 0) == K4A_WAIT_RESULT_SUCCEEDED)
        {
            gyro_sum.xyz = { 
                gyro_sum.xyz.x + sample.gyro_sample.xyz.x, 
                gyro_sum.xyz.y + sample.gyro_sample.xyz.y, 
                gyro_sum.xyz.z + sample.gyro_sample.xyz.z };
            accel_sum.xyz = { 
                accel_sum.xyz.x + sample.acc_sample.xyz.x,  
                accel_sum.xyz.y + sample.acc_sample.xyz.y,  
                accel_sum.xyz.z + sample.acc_sample.xyz.z };
            sum_count += 1;
            samples   += 1;
        }

        // If we got any samples this loop, print out their average!
        if (sum_count > 0)
        {
            k4a_float3_t gyro_avg = {
                gyro_sum.xyz.x / sum_count,
                gyro_sum.xyz.y / sum_count,
                gyro_sum.xyz.z / sum_count };
            k4a_float3_t accel_avg = {
                accel_sum.xyz.x / sum_count,
                accel_sum.xyz.y / sum_count,
                accel_sum.xyz.z / sum_count };

            printf("<%6.2f, %6.2f, %6.2f>   ", gyro_avg.xyz.x, gyro_avg.xyz.y, gyro_avg.xyz.z);
            printf("<%6.2f, %6.2f, %6.2f>", accel_avg.xyz.x, accel_avg.xyz.y, accel_avg.xyz.z);

            // Write backspaces so we'll overwrite this line next time
            printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
            printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
        }
    }
    printf("\nShutting down.\n");

    // Release all allocated resources, and shut down the Kinect
    k4a_device_stop_imu(device);
    k4a_device_stop_cameras(device);
    k4a_device_close(device);
}
```