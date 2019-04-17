---
title: MR e 313 - serviço do Hub IoT do Azure
description: Concluir este curso para saber como implementar o serviço do Hub IoT em uma máquina virtual executando Ubuntu 16.4 e, em seguida, visualizar os dados da mensagem usando o Microsoft HoloLens ou um fone de ouvido imersivo (VR).
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: realidade mista, Azure, academy, borda, iot edge, tutorial, api, notificação, funções, tabelas, imersivo, hololens, vr, iot, máquina virtual, ubuntu, python
ms.openlocfilehash: 1ab7c48ac3cff1cb2283cadb171098af9e148628
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589086"
---
>[!NOTE]
><span data-ttu-id="07ddf-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="07ddf-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="07ddf-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="07ddf-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="07ddf-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="07ddf-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="07ddf-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="07ddf-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="07ddf-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="07ddf-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="07ddf-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="07ddf-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="07ddf-110">MR e o Azure 313: Serviço do Hub IoT</span><span class="sxs-lookup"><span data-stu-id="07ddf-110">MR and Azure 313: IoT Hub Service</span></span>

![resultado do curso](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="07ddf-112">Neste curso, você aprenderá a implementar uma **serviço do Hub IoT** em uma máquina virtual executando o sistema operacional Ubuntu 16.4.</span><span class="sxs-lookup"><span data-stu-id="07ddf-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="07ddf-113">Uma **aplicativo de funções do Azure** será usado para receber mensagens da sua VM do Ubuntu e armazenar o resultado dentro de uma **serviço de tabela do Azure**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="07ddf-114">Em seguida, ser capaz de exibir esses dados usando **Power BI** no Microsoft HoloLens ou imersivo fone de ouvido (VR).</span><span class="sxs-lookup"><span data-stu-id="07ddf-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="07ddf-115">O conteúdo deste curso *é aplicável* para dispositivos do IoT Edge, embora com a finalidade deste curso, o foco estará em um ambiente de máquina virtual, para que o acesso a um dispositivo físico do Edge não é necessário.</span><span class="sxs-lookup"><span data-stu-id="07ddf-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="07ddf-116">Ao concluir este curso, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="07ddf-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="07ddf-117">Implantar um **módulo do IoT Edge** a uma máquina Virtual Ubuntu 16 SO (), que representará o seu dispositivo IoT.</span><span class="sxs-lookup"><span data-stu-id="07ddf-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="07ddf-118">Adicionar um **modelo do Tensorflow de visão do Azure personalizado** para o módulo de borda, com um código que analisará imagens armazenadas no contêiner.</span><span class="sxs-lookup"><span data-stu-id="07ddf-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="07ddf-119">Configurar o módulo para enviar a mensagem de resultado de análise para seu **no Hub IOT**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="07ddf-120">Use uma **aplicativo de funções do Azure** para armazenar a mensagem dentro de uma **tabelas do Azure**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="07ddf-121">Configure **Power BI** para coletar a mensagem armazenada e criar um relatório.</span><span class="sxs-lookup"><span data-stu-id="07ddf-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="07ddf-122">Visualize os dados de mensagem de IoT dentro **Power BI**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="07ddf-123">Os serviços que você usará incluem:</span><span class="sxs-lookup"><span data-stu-id="07ddf-123">The Services you will use include:</span></span>

- <span data-ttu-id="07ddf-124">**O IoT Hub** é um serviço do Microsoft Azure que permite aos desenvolvedores se conectar, monitorar e gerenciar ativos de IoT.</span><span class="sxs-lookup"><span data-stu-id="07ddf-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="07ddf-125">Para obter mais informações, visite o [ **serviço do Hub IoT** página](https://azure.microsoft.com/en-au/services/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="07ddf-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/en-au/services/iot-hub/).</span></span>

- <span data-ttu-id="07ddf-126">**O registro de contêiner do Azure** é um serviço do Microsoft Azure que permite aos desenvolvedores armazenar imagens de contêiner para vários tipos de contêineres.</span><span class="sxs-lookup"><span data-stu-id="07ddf-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="07ddf-127">Para obter mais informações, visite o [ **serviço de registro de contêiner do Azure** página](https://azure.microsoft.com/en-au/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="07ddf-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/en-au/services/container-registry/).</span></span>

- <span data-ttu-id="07ddf-128">**Aplicativo de funções do Azure** é um serviço de Azure da Microsoft, que permite que os desenvolvedores executem pequenos trechos de código, 'funções', no Azure.</span><span class="sxs-lookup"><span data-stu-id="07ddf-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="07ddf-129">Isso fornece uma maneira para delegar trabalho para a nuvem, em vez de seu aplicativo local, o que pode ter muitos benefícios.</span><span class="sxs-lookup"><span data-stu-id="07ddf-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="07ddf-130">**O Azure Functions** dá suporte a várias linguagens de desenvolvimento, incluindo C\#, F\#, Node. js, Java e PHP.</span><span class="sxs-lookup"><span data-stu-id="07ddf-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="07ddf-131">Para obter mais informações, visite o [ **do Azure Functions** página](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="07ddf-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="07ddf-132">**Armazenamento do Azure: Tabelas** é um Microsoft Azure Service, que permite aos desenvolvedores armazenar a estruturadas, não-SQL, os dados na nuvem, tornando-o facilmente acessível em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="07ddf-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="07ddf-133">O serviço apresenta um design sem esquema, permitindo a evolução das tabelas conforme necessário e, portanto, é muito flexível.</span><span class="sxs-lookup"><span data-stu-id="07ddf-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="07ddf-134">Para obter mais informações, visite o [ **tabelas do Azure** página](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="07ddf-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="07ddf-135">Este curso ensinará como configurar e usar o serviço de Hub IoT e, em seguida, visualizar uma resposta fornecida por um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="07ddf-136">Ele será cabe a você aplicar esses conceitos para uma instalação personalizada do serviço de Hub IoT, que você pode criar.</span><span class="sxs-lookup"><span data-stu-id="07ddf-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="07ddf-137">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="07ddf-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="07ddf-138">Curso</span><span class="sxs-lookup"><span data-stu-id="07ddf-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="07ddf-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="07ddf-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="07ddf-140"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="07ddf-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="07ddf-141">MR e o Azure 313: Serviço do Hub IoT</span><span class="sxs-lookup"><span data-stu-id="07ddf-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="07ddf-142">✔️</span><span class="sxs-lookup"><span data-stu-id="07ddf-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="07ddf-143">✔️</span><span class="sxs-lookup"><span data-stu-id="07ddf-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="07ddf-144">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="07ddf-144">Prerequisites</span></span>

<span data-ttu-id="07ddf-145">Para os pré-requisitos mais atualizados para o desenvolvimento de realidade misturada, incluindo o Microsoft HoloLens, visite o [instalar as ferramentas](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) artigo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="07ddf-146">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Python.</span><span class="sxs-lookup"><span data-stu-id="07ddf-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="07ddf-147">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (julho de 2018).</span><span class="sxs-lookup"><span data-stu-id="07ddf-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="07ddf-148">Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas de](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente do que listados abaixo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="07ddf-149">O hardware e software a seguir é necessário:</span><span class="sxs-lookup"><span data-stu-id="07ddf-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="07ddf-150">Windows 10 Fall Creators Update (ou posterior) **modo de desenvolvedor habilitado**</span><span class="sxs-lookup"><span data-stu-id="07ddf-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="07ddf-151">Você não pode executar uma máquina Virtual usando o Hyper-V no Windows 10 Home Edition.</span><span class="sxs-lookup"><span data-stu-id="07ddf-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="07ddf-152">SDK do Windows 10 (versão mais recente)</span><span class="sxs-lookup"><span data-stu-id="07ddf-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="07ddf-153">Um HoloLens, **modo de desenvolvedor habilitado**</span><span class="sxs-lookup"><span data-stu-id="07ddf-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="07ddf-154">Visual Studio 2017.15.4 (usado apenas para acessar o Gerenciador de nuvem do Azure)</span><span class="sxs-lookup"><span data-stu-id="07ddf-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="07ddf-155">Acesso à Internet para o Azure e para o serviço Hub IoT.</span><span class="sxs-lookup"><span data-stu-id="07ddf-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="07ddf-156">Para obter mais informações, siga este [link para a página de serviço do Hub IoT](https://azure.microsoft.com/en-au/services/iot-hub/)</span><span class="sxs-lookup"><span data-stu-id="07ddf-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/en-au/services/iot-hub/)</span></span>
- <span data-ttu-id="07ddf-157">Um modelo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="07ddf-157">A machine learning model.</span></span> <span data-ttu-id="07ddf-158">Se você não tiver seu próprio pronto para usar o modelo, [você pode usar o modelo fornecido com este curso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span><span class="sxs-lookup"><span data-stu-id="07ddf-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="07ddf-159">**Hyper-V** software habilitado em seu computador de desenvolvimento do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="07ddf-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="07ddf-160">Uma máquina Virtual executando Ubuntu (16.4 ou 18.4), em execução no computador de desenvolvimento ou como alternativa, você pode usar um computador separado que executa o Linux (Ubuntu 16.4 ou 18.4).</span><span class="sxs-lookup"><span data-stu-id="07ddf-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="07ddf-161">Você pode encontrar mais informações sobre como criar uma VM no Windows usando o Hyper-V na [capítulo "Antes de começar"](#before-you-start). ( https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="07ddf-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="07ddf-162">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="07ddf-162">Before you start</span></span>

1. <span data-ttu-id="07ddf-163">Configurar e testar o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="07ddf-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="07ddf-164">Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="07ddf-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="07ddf-165">É uma boa ideia realizar **calibragem** e **Sensor ajuste** ao começar a desenvolver um novo aplicativo HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="07ddf-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="07ddf-166">Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="07ddf-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="07ddf-167">Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="07ddf-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="07ddf-168">Configurar seu **Máquina Virtual Ubuntu** usando **Hyper-V**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="07ddf-169">Os recursos a seguir ajudará você com o processo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="07ddf-170">Primeiro, siga este link para [Baixe o ISO do Ubuntu 16.04.4 LTS (Xenial Xerus)](http://au.releases.ubuntu.com/16.04/).</span><span class="sxs-lookup"><span data-stu-id="07ddf-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="07ddf-171">Selecione o **imagem da área de trabalho do PC (AMD64) de 64 bits**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="07ddf-172">Certifique-se **Hyper-V** está habilitado no seu computador Windows 10.</span><span class="sxs-lookup"><span data-stu-id="07ddf-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="07ddf-173">Você pode seguir este link para obter orientação sobre [instalar e habilitar o Hyper-V no Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span><span class="sxs-lookup"><span data-stu-id="07ddf-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="07ddf-174">Inicie o Hyper-V e criar uma nova VM do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="07ddf-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="07ddf-175">Você pode seguir este link para um [guia passo a passo sobre como criar uma VM com o Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="07ddf-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="07ddf-176">Quando solicitado **"Instalar um sistema operacional de um arquivo de imagem inicializável"**, selecione o **Ubuntu ISO** tem o download anteriormente.</span><span class="sxs-lookup"><span data-stu-id="07ddf-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="07ddf-177">Usando o **criação rápida do Hyper-V** não é sugerida.</span><span class="sxs-lookup"><span data-stu-id="07ddf-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="07ddf-178">Capítulo 1: recuperar o modelo de visão personalizada</span><span class="sxs-lookup"><span data-stu-id="07ddf-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="07ddf-179">Com este curso, você terá acesso a um [modelo de visão personalizada pré-criados](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) que detecta teclados e mouses a partir de imagens.</span><span class="sxs-lookup"><span data-stu-id="07ddf-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="07ddf-180">Se você usar essa opção, vá para [capítulo 2](#chapter-2---the-container-registry-service).</span><span class="sxs-lookup"><span data-stu-id="07ddf-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="07ddf-181">No entanto, você pode seguir estas etapas se você quiser usar seu próprio modelo de visão personalizada:</span><span class="sxs-lookup"><span data-stu-id="07ddf-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="07ddf-182">No seu **personalizados de projeto visão** vá para o **desempenho** guia.</span><span class="sxs-lookup"><span data-stu-id="07ddf-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="07ddf-183">O modelo deve usar um *compact* domínio, a fim de exportar o modelo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="07ddf-184">Você pode alterar seu domínio de modelos nas configurações para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="07ddf-184">You can change your models domain in the settings for your project.</span></span>

    ![Guia de desempenho](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="07ddf-186">Selecione o **iteração** você deseja exportar e clique em **exportar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="07ddf-187">Uma folha será exibida.</span><span class="sxs-lookup"><span data-stu-id="07ddf-187">A blade will appear.</span></span>

    ![folha de exportação](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="07ddf-189">Na folha, clique em **arquivo Docker**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-189">In the blade click **Docker File**.</span></span>

    ![Selecione o docker](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="07ddf-191">Clique em **Linux** no menu suspenso e, em seguida, clique em **baixar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![Clique em Baixar](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="07ddf-193">Descompacte o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-193">Unzip the content.</span></span> <span data-ttu-id="07ddf-194">Você o usará posteriormente no curso.</span><span class="sxs-lookup"><span data-stu-id="07ddf-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="07ddf-195">Capítulo 2 - o serviço de registro de contêiner</span><span class="sxs-lookup"><span data-stu-id="07ddf-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="07ddf-196">O **serviço de registro de contêiner** é o repositório usado para hospedar seus contêineres.</span><span class="sxs-lookup"><span data-stu-id="07ddf-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="07ddf-197">O **no Hub IOT** que você criar e usar neste curso, refere-se ao **serviço de registro de contêiner** para obter os contêineres para implantar em seu dispositivo de borda.</span><span class="sxs-lookup"><span data-stu-id="07ddf-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="07ddf-198">Primeiro, siga este [link para o Portal do Azure](https://portal.azure.com/)e faça logon com suas credenciais.</span><span class="sxs-lookup"><span data-stu-id="07ddf-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="07ddf-199">Vá para **criar um recurso** e procure **registro de contêiner**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![registro de contêiner](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="07ddf-201">Clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="07ddf-202">Configurar o serviço de parâmetros de configuração:</span><span class="sxs-lookup"><span data-stu-id="07ddf-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="07ddf-203">Insira um nome para seu projeto, neste exemplo chama **IoTCRegistry**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="07ddf-204">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="07ddf-205">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar, de cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="07ddf-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="07ddf-206">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="07ddf-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="07ddf-207">Defina o local do serviço.</span><span class="sxs-lookup"><span data-stu-id="07ddf-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="07ddf-208">Definir **usuário administrador** à **habilitar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="07ddf-209">Definir **SKU** à **básica**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="07ddf-210">Clique em **criar** e aguarde até que os serviços a serem criados.</span><span class="sxs-lookup"><span data-stu-id="07ddf-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="07ddf-211">Depois que a notificação de pop-up informando sobre a criação bem-sucedida do *registro de contêiner*, clique em **ir para o recurso** ser redirecionado para sua página de serviço.</span><span class="sxs-lookup"><span data-stu-id="07ddf-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="07ddf-212">No *registro de contêiner* página de serviço, clique em **chaves de acesso**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="07ddf-213">Tome nota (você pode usar o bloco de notas) dos seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="07ddf-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="07ddf-214">**Servidor de logon**</span><span class="sxs-lookup"><span data-stu-id="07ddf-214">**Login Server**</span></span>
    2. <span data-ttu-id="07ddf-215">**nome de usuário**</span><span class="sxs-lookup"><span data-stu-id="07ddf-215">**Username**</span></span>
    3. <span data-ttu-id="07ddf-216">**Senha**</span><span class="sxs-lookup"><span data-stu-id="07ddf-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="07ddf-217">Capítulo 3 - o serviço do Hub IoT</span><span class="sxs-lookup"><span data-stu-id="07ddf-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="07ddf-218">Agora, você começará a criação e configuração do seu **no Hub IOT**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="07ddf-219">Se ainda não estiver conectado, faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="07ddf-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="07ddf-220">Depois de conectado, clique em **criar um recurso** no canto superior esquerdo de canto e procure **IoT Hub**e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![Procure a conta de armazenamento](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="07ddf-222">A nova página fornecerá uma descrição do **conta de armazenamento** Service.</span><span class="sxs-lookup"><span data-stu-id="07ddf-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="07ddf-223">Na parte inferior esquerda desse prompt, clique no **criar** botão para criar uma instância deste serviço.</span><span class="sxs-lookup"><span data-stu-id="07ddf-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="07ddf-225">Depois de clicar em **criar**, um painel será exibido:</span><span class="sxs-lookup"><span data-stu-id="07ddf-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="07ddf-226">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="07ddf-227">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="07ddf-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="07ddf-228">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="07ddf-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="07ddf-229">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="07ddf-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="07ddf-230">Selecione uma opção apropriada **local** (Use o mesmo local em todos os serviços que você cria neste curso).</span><span class="sxs-lookup"><span data-stu-id="07ddf-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="07ddf-231">Inserir sua desejada **nome** para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="07ddf-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="07ddf-232">Na parte inferior da página, clique em **Avançar: Tamanho e escala**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="07ddf-234">Nessa página, selecione suas **escala e preço** (se esta for a primeira instância de serviço do Hub IoT, uma camada gratuita deve estar disponível para você).</span><span class="sxs-lookup"><span data-stu-id="07ddf-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="07ddf-235">Clique em **revisar + criar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-235">Click on **Review + Create**.</span></span>

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="07ddf-237">Revise as configurações e clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-237">Review your settings and click on **Create**.</span></span>

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="07ddf-239">Depois que a notificação de pop-up informando sobre a criação bem-sucedida do *IoT Hub* serviço, clique em **ir para o recurso** ser redirecionado para sua página de serviço.</span><span class="sxs-lookup"><span data-stu-id="07ddf-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="07ddf-241">Role o painel lateral à esquerda até ver *gerenciamento de dispositivo automático*, clique em **IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="07ddf-243">Na janela que aparece à direita, clique em **adicionar dispositivo do IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="07ddf-244">Uma folha será exibida à direita.</span><span class="sxs-lookup"><span data-stu-id="07ddf-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="07ddf-245">Na folha, forneça seu novo dispositivo de um **ID do dispositivo** (um nome de sua escolha).</span><span class="sxs-lookup"><span data-stu-id="07ddf-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="07ddf-246">Em seguida, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-246">Then, click **Save**.</span></span> <span data-ttu-id="07ddf-247">O *primário* e *chaves secundárias* irá gerar automaticamente, se você tiver **gerar automaticamente** marcada.</span><span class="sxs-lookup"><span data-stu-id="07ddf-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="07ddf-249">Você navegará de volta para o *dispositivos de borda IoT* seção, onde o novo dispositivo será listado.</span><span class="sxs-lookup"><span data-stu-id="07ddf-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="07ddf-250">Clique no seu novo dispositivo (destacadas em vermelho na imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="07ddf-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="07ddf-252">Sobre o *detalhes do dispositivo* página for exibida, faça uma cópia da **cadeia de caracteres de Conexão** (chave primária).</span><span class="sxs-lookup"><span data-stu-id="07ddf-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="07ddf-254">Volte para o painel à esquerda e clique em *políticas de acesso compartilhado*, para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="07ddf-255">Na página que aparece, clique em **iothubowner**, e uma folha será exibida à direita da tela.</span><span class="sxs-lookup"><span data-stu-id="07ddf-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="07ddf-256">Anote (no bloco de notas) a **cadeia de caracteres de Conexão** (chave primária), para uso posterior ao definir o *cadeia de caracteres de Conexão* ao seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="07ddf-258">Capítulo 4 - configuração do ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="07ddf-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="07ddf-259">Para criar e implantar módulos para *IoT Hub Edge*, serão necessários os seguintes componentes instalados no computador de desenvolvimento executando o Windows 10:</span><span class="sxs-lookup"><span data-stu-id="07ddf-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="07ddf-260">[Docker para Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), ele solicitará que você crie uma conta para poder baixar.</span><span class="sxs-lookup"><span data-stu-id="07ddf-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="07ddf-261">[![Baixe o docker para windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="07ddf-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="07ddf-262">Docker requer *Windows 10 PRO*, *Enterprise 14393*, ou *Windows Server 2016 RTM*, para executar.</span><span class="sxs-lookup"><span data-stu-id="07ddf-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="07ddf-263">Se você estiver executando outras versões do Windows 10, você pode tentar instalar o Docker usando o [caixa de ferramentas do Docker](https://docs.docker.com/toolbox/toolbox_install_windows/).</span><span class="sxs-lookup"><span data-stu-id="07ddf-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="07ddf-264">[Python 3.6](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="07ddf-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="07ddf-265">[![Baixe o python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="07ddf-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="07ddf-266">[Visual Studio Code (também conhecido como VS Code)](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="07ddf-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="07ddf-267">[![baixar o VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="07ddf-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="07ddf-268">Depois de instalar o software mencionado acima, você precisará reiniciar seu computador.</span><span class="sxs-lookup"><span data-stu-id="07ddf-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="07ddf-269">Capítulo 5 – configurar o ambiente do Ubuntu</span><span class="sxs-lookup"><span data-stu-id="07ddf-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="07ddf-270">Agora você pode prosseguir com a configuração do dispositivo **executando o sistema operacional do Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="07ddf-271">Siga as etapas abaixo para instalar o software necessário, para implantar seus contêineres em seu quadro:</span><span class="sxs-lookup"><span data-stu-id="07ddf-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07ddf-272">Você sempre deve preceder os comandos de terminal com **sudo** para ser executado como usuário administrador.</span><span class="sxs-lookup"><span data-stu-id="07ddf-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="07ddf-273">i.e:</span><span class="sxs-lookup"><span data-stu-id="07ddf-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="07ddf-274">Abra o **Ubuntu Terminal**e use o comando a seguir para instalar **pip**:</span><span class="sxs-lookup"><span data-stu-id="07ddf-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [! Dica]<span data-ttu-id="07ddf-275"> você pode abrir \*Terminal* muito facilmente por meio do usando o atalho de teclado: *\*Ctrl + Alt + T*\*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-275"> You can open \*Terminal* very easily through using the keyboard shortcut: *\*Ctrl + Alt + T*\*.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="07ddf-276">Em todo este capítulo, você pode ser solicitado, por *Terminal*, de permissão para usar o armazenamento do dispositivo e para que você insira **s/n** (Sim ou não), digite **'y'** e, em seguida, pressione a **Enter** chave, para aceitar.</span><span class="sxs-lookup"><span data-stu-id="07ddf-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="07ddf-277">Quando esse comando for concluído, use o seguinte comando para instalar **curl**:</span><span class="sxs-lookup"><span data-stu-id="07ddf-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="07ddf-278">Uma vez **pip** e **curl** são instalados, use o seguinte comando para instalar o **tempo de execução do IoT Edge**, isso é necessário para implantar e controlar os módulos em seu quadro:</span><span class="sxs-lookup"><span data-stu-id="07ddf-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. <span data-ttu-id="07ddf-279">Neste ponto, você será solicitado a abrir o *arquivo de configuração de tempo de execução*, para inserir o **cadeia de Conexão do dispositivo**, que você anotou (em seu bloco de notas), ao criar o **no Hub IOT**  ([na etapa 14, do capítulo 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="07ddf-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="07ddf-280">Execute a seguinte linha no terminal para abrir esse arquivo:</span><span class="sxs-lookup"><span data-stu-id="07ddf-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="07ddf-281">O **config. YAML** arquivo será exibido, pronto para edição:</span><span class="sxs-lookup"><span data-stu-id="07ddf-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="07ddf-282">Quando esse arquivo é aberto, ele pode ser um pouco confuso.</span><span class="sxs-lookup"><span data-stu-id="07ddf-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="07ddf-283">Você será o texto para editar esse arquivo, dentro de *Terminal* em si.</span><span class="sxs-lookup"><span data-stu-id="07ddf-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="07ddf-284">Use as teclas de direção no teclado para rolar para baixo (você precisará rolar para baixo de maneira um pouco), para alcançar a linha que contém ":</span><span class="sxs-lookup"><span data-stu-id="07ddf-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="07ddf-285">"**\<ADICIONAR CADEIA DE CONEXÃO DO DISPOSITIVO AQUI &GT;**".</span><span class="sxs-lookup"><span data-stu-id="07ddf-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="07ddf-286">Substitua a linha, **incluindo os colchetes**, com o **cadeia de Conexão do dispositivo** anotados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="07ddf-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="07ddf-287">Com a cadeia de Conexão em vigor no seu teclado, pressione a **Ctrl-X** chaves para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="07ddf-288">Ele solicitará que você confirme digitando **Y**. Em seguida, pressione a **Enter** chave, para confirmar.</span><span class="sxs-lookup"><span data-stu-id="07ddf-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="07ddf-289">Você voltará ao normal *Terminal*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="07ddf-290">Depois que esses comandos têm todos são executados com êxito, você terá instalado a **tempo de execução do IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="07ddf-291">Depois de inicializado, o tempo de execução será iniciado em seu próprio toda vez que o dispositivo é ligado e serão sentar em segundo plano, aguardando módulos ser implantada com o **no Hub IOT**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="07ddf-292">Execute a seguinte linha de comando para inicializar o *tempo de execução do IoT Edge*:</span><span class="sxs-lookup"><span data-stu-id="07ddf-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="07ddf-293">Se você fizer alterações ao seu arquivo. YAML ou a configuração acima, você precisará executar a linha acima de reinicialização novamente, dentro de *Terminal*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="07ddf-294">Verifique as *tempo de execução do IoT Edge* status executando a seguinte linha de comando.</span><span class="sxs-lookup"><span data-stu-id="07ddf-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="07ddf-295">O tempo de execução deve aparecer com status **ativo (em execução)** em texto verde.</span><span class="sxs-lookup"><span data-stu-id="07ddf-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="07ddf-296">Pressione a **Ctrl-C** chaves, para sair da página de status.</span><span class="sxs-lookup"><span data-stu-id="07ddf-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="07ddf-297">Você pode verificar se o *tempo de execução do IoT Edge* está obtendo os contêineres corretamente digitando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="07ddf-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="07ddf-298">Uma lista com duas (2) contêineres deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="07ddf-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="07ddf-299">Esses são os módulos padrão que são criados automaticamente pelo serviço do Hub IoT (edgeAgent e edgeHub).</span><span class="sxs-lookup"><span data-stu-id="07ddf-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="07ddf-300">Depois de criar e implantar seus próprios módulos, eles aparecerão nessa lista, sob os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="07ddf-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="07ddf-301">Capítulo 6 - instalar as extensões</span><span class="sxs-lookup"><span data-stu-id="07ddf-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07ddf-302">Os próximos capítulos (6 a 9) devem ser executadas em seu computador Windows 10.</span><span class="sxs-lookup"><span data-stu-id="07ddf-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="07ddf-303">Abra **VS Code**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="07ddf-304">Clique no **extensões** botão (quadrada) do esquerdo barra do VS Code, para abrir o **painel de extensões**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="07ddf-305">Procurar e instalar as extensões a seguir (conforme mostrado na imagem abaixo):</span><span class="sxs-lookup"><span data-stu-id="07ddf-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="07ddf-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="07ddf-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="07ddf-307">Kit de ferramentas do Azure IoT</span><span class="sxs-lookup"><span data-stu-id="07ddf-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="07ddf-308">Docker</span><span class="sxs-lookup"><span data-stu-id="07ddf-308">Docker</span></span>   

    ![Criar o contêiner](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="07ddf-310">Depois que as extensões são instaladas, feche e abra novamente o VS Code.</span><span class="sxs-lookup"><span data-stu-id="07ddf-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="07ddf-311">Com o VS Code, abra mais uma vez, navegue até **Exibir > terminal integrado**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-311">With VS Code open once more, navigate to **View > Integrated terminal**.</span></span>

6. <span data-ttu-id="07ddf-312">Você instalará **Cookiecutter**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="07ddf-313">No terminal, execute o seguinte comando do bash:</span><span class="sxs-lookup"><span data-stu-id="07ddf-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! Dica]<span data-ttu-id="07ddf-314"> se você tiver dificuldade com este comando:</span><span class="sxs-lookup"><span data-stu-id="07ddf-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="07ddf-315">Reinicie o VS Code, e / ou seu computador.</span><span class="sxs-lookup"><span data-stu-id="07ddf-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="07ddf-316">Talvez seja necessário alternar os **Terminal do VS Code** ao que você usa para instalar o Python, ou seja, **Powershell** (especialmente no caso do ambiente do Python já foi instalado em seu computador).</span><span class="sxs-lookup"><span data-stu-id="07ddf-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="07ddf-317">Com o Terminal aberto, você encontrará o menu suspenso no lado direito do Terminal.</span><span class="sxs-lookup"><span data-stu-id="07ddf-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="07ddf-318">![Criar o contêiner](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="07ddf-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="07ddf-319">Verifique se o **Python** caminho de instalação é adicionado como **variável de ambiente** em seu computador.</span><span class="sxs-lookup"><span data-stu-id="07ddf-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="07ddf-320">Cookiecutter deve fazer parte do caminho do mesmo local.</span><span class="sxs-lookup"><span data-stu-id="07ddf-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="07ddf-321">Siga este [link para obter mais informações sobre variáveis de ambiente](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span><span class="sxs-lookup"><span data-stu-id="07ddf-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="07ddf-322">Uma vez **Cookiecutter** terminou de instalar, você deve reiniciar seu computador, para que **Cookiecutter** é reconhecido como um comando, dentro do ambiente do seu sistema.</span><span class="sxs-lookup"><span data-stu-id="07ddf-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="07ddf-323">Capítulo 7 - criar sua solução de contêiner</span><span class="sxs-lookup"><span data-stu-id="07ddf-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="07ddf-324">Neste ponto, você precisará criar o contêiner, com o módulo, para ser enviados por push para o *registro de contêiner*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="07ddf-325">Depois que você tiver enviado por push seu contêiner, você usará o *IoT Hub de borda* serviço implantá-lo em seu dispositivo, que está executando o *tempo de execução do IoT Edge*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="07ddf-326">No VS Code, clique em **exibição > Paleta de comandos**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-326">From VS Code, click **View > Command palette**.</span></span>

2. <span data-ttu-id="07ddf-327">Na paleta, pesquisar e executar **Azure IoT Edge: Nova solução de Iot Edge**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="07ddf-328">Procure em um local onde você deseja criar sua solução.</span><span class="sxs-lookup"><span data-stu-id="07ddf-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="07ddf-329">Pressione a **Enter** chave, para aceitar o local.</span><span class="sxs-lookup"><span data-stu-id="07ddf-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="07ddf-330">Dê um nome à sua solução.</span><span class="sxs-lookup"><span data-stu-id="07ddf-330">Give a name to your solution.</span></span> <span data-ttu-id="07ddf-331">Pressione a **Enter** chave, para confirmar o nome fornecido.</span><span class="sxs-lookup"><span data-stu-id="07ddf-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="07ddf-332">Agora você será solicitado a escolher a estrutura de modelo para sua solução.</span><span class="sxs-lookup"><span data-stu-id="07ddf-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="07ddf-333">Clique em **módulo de Python**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-333">Click **Python Module**.</span></span> <span data-ttu-id="07ddf-334">Pressione a **Enter** chave, para confirmar se essa opção.</span><span class="sxs-lookup"><span data-stu-id="07ddf-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="07ddf-335">Dê um nome para seu módulo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-335">Give a name to your module.</span></span> <span data-ttu-id="07ddf-336">Pressione a **Enter** chave, para confirmar o nome do seu módulo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="07ddf-337">Certifique-se de observar (com o bloco de notas) o nome do módulo, pois ele é usado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="07ddf-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="07ddf-338">Você observará uma pré-criados *repositório de imagens do Docker* endereço aparecerá na paleta.</span><span class="sxs-lookup"><span data-stu-id="07ddf-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="07ddf-339">Ele se parecerá com:</span><span class="sxs-lookup"><span data-stu-id="07ddf-339">It will look like:</span></span>

    <span data-ttu-id="07ddf-340">**localhost:5000/carros / – o nome do módulo -**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="07ddf-341">Exclua **localhost:5000/carros**e em seu lugar insert a *registro de contêiner* **servidor de logon** endereço, que você anotou ao criar o **contêiner Serviço de registro** ([na etapa 8, capítulo 2](#chapter-2---the-container-registry-service)).</span><span class="sxs-lookup"><span data-stu-id="07ddf-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="07ddf-342">Pressione a **Enter** chave, para confirmar o endereço.</span><span class="sxs-lookup"><span data-stu-id="07ddf-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="07ddf-343">Neste ponto, a solução que contém o modelo para o seu módulo de Python será criada e sua estrutura será exibida na **explorar guia**, do VS Code, no lado esquerdo da tela.</span><span class="sxs-lookup"><span data-stu-id="07ddf-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="07ddf-344">Se o **explorar guia** é não está aberta, você pode abri-lo clicando no botão de mais alto, na barra à esquerda.</span><span class="sxs-lookup"><span data-stu-id="07ddf-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![Criar o contêiner](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="07ddf-346">A última etapa neste capítulo, é clicar e abra o **arquivo. env**, de dentro a **guia explorar**e adicione seu *registro de contêiner* **denomedeusuário** e **senha**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="07ddf-347">Esse arquivo é ignorado pelo git, mas sobre como compilar o contêiner, definirá as credenciais para acessar o **serviço de registro de contêiner**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![Criar o contêiner](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="07ddf-349">Capítulo 8 - edição de sua solução de contêiner</span><span class="sxs-lookup"><span data-stu-id="07ddf-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="07ddf-350">Agora, você concluirá a solução de contêiner, atualizando os arquivos a seguir:</span><span class="sxs-lookup"><span data-stu-id="07ddf-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="07ddf-351">*principal<span></span>. py* script python.</span><span class="sxs-lookup"><span data-stu-id="07ddf-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="07ddf-352">*requirements.txt*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-352">*requirements.txt*.</span></span>
- <span data-ttu-id="07ddf-353">*deployment.template.json*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="07ddf-354">*Dockerfile.amd64*</span><span class="sxs-lookup"><span data-stu-id="07ddf-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="07ddf-355">Em seguida, você criará a *imagens* pasta, usada pelo script do python para verificar se há imagens para correspondência com seu *modelo de visão personalizada*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="07ddf-356">Por fim, você adicionará a *labels.txt* arquivo, para ajudar a ler o seu modelo e o *model.pb* arquivo, que é o seu modelo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="07ddf-357">Com o VS Code abrir, navegue até a pasta de módulo e procure o script chamado **principal<span></span>. py**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="07ddf-358">Clique duas vezes para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-358">Double-click to open it.</span></span>

2. <span data-ttu-id="07ddf-359">Exclua o conteúdo do arquivo e insira o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="07ddf-359">Delete the content of the file and insert the following code:</span></span>

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  <span data-ttu-id="07ddf-360">Abra o arquivo chamado **Requirements. txt**e substitua seu conteúdo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="07ddf-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="07ddf-361">Abra o arquivo chamado **deployment.template.json**e substitua o conteúdo a seguir a abaixo diretriz:</span><span class="sxs-lookup"><span data-stu-id="07ddf-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="07ddf-362">Como você terá seu próprio, exclusiva, estrutura do JSON, será preciso editá-lo manualmente (em vez de copiar um exemplo).</span><span class="sxs-lookup"><span data-stu-id="07ddf-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="07ddf-363">Para facilitar isso, use a imagem como um guia abaixo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="07ddf-364">Áreas que terá uma aparência diferentes para a sua, mas que você **não deve alterar são realçado em amarelo**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="07ddf-365">**As seções que você precisa excluir, são um vermelho realçado.**</span><span class="sxs-lookup"><span data-stu-id="07ddf-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="07ddf-366">Tenha cuidado ao excluir os colchetes corretos e também remover as vírgulas.</span><span class="sxs-lookup"><span data-stu-id="07ddf-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![Criar o contêiner](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="07ddf-368">O JSON concluído deve se parecer com a imagem a seguir (no entanto, com suas diferenças exclusivas: *referências de nome de usuário/senha/nome/módulo*):</span><span class="sxs-lookup"><span data-stu-id="07ddf-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![Criar o contêiner](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="07ddf-370">Abra o arquivo chamado **Dockerfile.amd64**e substitua seu conteúdo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="07ddf-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  <span data-ttu-id="07ddf-371">Clique com botão direito na pasta abaixo **módulos** (ele terá o nome que você forneceu anteriormente; o exemplo abaixo, ele é chamado *pythonmodule*) e clique em **nova pasta**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="07ddf-372">Nomeie a pasta **imagens**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="07ddf-373">Dentro da pasta, adicione algumas imagens que contêm o mouse ou teclado.</span><span class="sxs-lookup"><span data-stu-id="07ddf-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="07ddf-374">Esses serão as imagens que serão analisadas pelo modelo do Tensorflow.</span><span class="sxs-lookup"><span data-stu-id="07ddf-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="07ddf-375">Se você estiver usando seu próprio modelo, você precisará alterar isso para refletir seus próprios dados de modelos.</span><span class="sxs-lookup"><span data-stu-id="07ddf-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="07ddf-376">Agora você precisará recuperar o **labels.txt** e **model.pb** arquivos da pasta de modelo, o que você anterior baixado (ou criado a partir de seu próprio **serviço personalizado de visão** ), em [capítulo 1](#chapter-1---retrieve-the-custom-vision-model).</span><span class="sxs-lookup"><span data-stu-id="07ddf-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="07ddf-377">Depois que os arquivos, coloque-os em sua solução, juntamente com os outros arquivos.</span><span class="sxs-lookup"><span data-stu-id="07ddf-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="07ddf-378">O resultado final deve ser semelhante a imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="07ddf-378">The final result should look like the image below:</span></span>

    ![Criar o contêiner](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="07ddf-380">Capítulo 9 - a solução como um contêiner de pacote</span><span class="sxs-lookup"><span data-stu-id="07ddf-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="07ddf-381">Agora você está pronto "pacotes" de arquivos como um contêiner e enviá-los para seu **registro de contêiner do Azure**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="07ddf-382">Dentro do VS Code, abra o *Terminal integrado* (**Exibir > Terminal integrado / CTRL + '**) e use a seguinte linha para fazer logon **Docker** (substitua os valores da comando com as credenciais de sua **registro de contêiner do Azure (ACR)**):</span><span class="sxs-lookup"><span data-stu-id="07ddf-382">Within VS Code, open the *Integrated Terminal* (**View > Integrated Terminal / CTRL + \`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="07ddf-383">Clique com botão direito no arquivo **deployment.template.json**e clique em **compilar solução do IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="07ddf-384">Esse processo de compilação leva algum tempo (dependendo do seu dispositivo), portanto, esteja preparado para aguardar.</span><span class="sxs-lookup"><span data-stu-id="07ddf-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="07ddf-385">Depois que o processo de compilação for concluída, uma **Deployment** arquivo terá sido criado dentro de uma nova pasta chamada **config**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![Criar implantação](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="07ddf-387">Abra o **paleta de comandos** novamente e pesquise **Azure: Entrar no**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="07ddf-388">Siga os prompts usando suas credenciais de conta do Azure; VS Code fornecerá uma opção para *copiar e abrir*, que irá copiar o código de dispositivo em breve serão necessárias e abra o navegador da web padrão.</span><span class="sxs-lookup"><span data-stu-id="07ddf-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="07ddf-389">Quando solicitado, cole o código de dispositivo, para autenticar seu computador.</span><span class="sxs-lookup"><span data-stu-id="07ddf-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![copiar e abrir](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="07ddf-391">Uma vez conectado em você vai notar, no lado inferior do *explorar* do painel, uma nova seção chamada **dispositivos de Hub IoT do Azure**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="07ddf-392">Clique nesta seção para expandi-la.</span><span class="sxs-lookup"><span data-stu-id="07ddf-392">Click this section to expand it.</span></span>

    ![dispositivo de borda](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="07ddf-394">Se seu dispositivo não está aqui, você precisará com o botão direito *dispositivos de Hub IoT do Azure*e, em seguida, clique em **definir cadeia de Conexão de Hub IoT**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="07ddf-395">Em seguida, você verá que o **paleta de comandos** (na parte superior do VS Code), solicitará que você insira sua *cadeia de caracteres de Conexão*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="07ddf-396">Esse é o *cadeia de caracteres de Conexão* você anotou no final da [capítulo 3](#chapter-3---the-iot-hub-service).</span><span class="sxs-lookup"><span data-stu-id="07ddf-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="07ddf-397">Pressione a **Enter** da chave, depois de copiar a cadeia de caracteres no.</span><span class="sxs-lookup"><span data-stu-id="07ddf-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="07ddf-398">Seu dispositivo, carregue e são exibidos.</span><span class="sxs-lookup"><span data-stu-id="07ddf-398">Your device should load, and appear.</span></span> <span data-ttu-id="07ddf-399">Clique com botão direito no nome do dispositivo e, em seguida, clique em **criar implantação para um único dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![Criar implantação](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="07ddf-401">Você obterá uma *Explorador de arquivos* prompt, onde você pode navegar para o **config** pasta e, em seguida, selecione o **Deployment** arquivo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="07ddf-402">Com o arquivo selecionado, clique o **selecione o manifesto de implantação de borda** botão.</span><span class="sxs-lookup"><span data-stu-id="07ddf-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![Criar implantação](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="07ddf-404">Neste ponto você forneceu suas **no Hub IOT** com o manifesto implantar seu contêiner, como um módulo de seu **registro de contêiner do Azure**, efetivamente implantá-lo em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="07ddf-405">Para exibir as mensagens enviadas do seu dispositivo ao IoT Hub, clique com botão direito novamente em seu nome de dispositivo na **dispositivos de Hub IoT do Azure** seção, o **Explorer** do painel e, em seguida, clique em **Iniciar monitoramento Mensagem D2C**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="07ddf-406">As mensagens enviadas do seu dispositivo devem aparecer no Terminal do VS.</span><span class="sxs-lookup"><span data-stu-id="07ddf-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="07ddf-407">Seja paciente, pois isso pode levar algum tempo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="07ddf-408">Consulte o capítulo seguinte para depuração e verificar se a implantação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="07ddf-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="07ddf-409">Esse módulo agora irá iterar entre as imagens a **imagens** pasta e analisá-los, com cada iteração.</span><span class="sxs-lookup"><span data-stu-id="07ddf-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="07ddf-410">Isso é, obviamente, apenas uma demonstração de como obter o modelo de aprendizado de máquina básico para trabalhar em um ambiente de dispositivo do IoT Edge.</span><span class="sxs-lookup"><span data-stu-id="07ddf-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="07ddf-411">Para expandir a funcionalidade desse exemplo, você pode continuar de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="07ddf-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="07ddf-412">Uma maneira de poderia ser incluindo algum código no contêiner, que captura fotos de uma webcam que está conectado ao dispositivo e salva as imagens na pasta de imagens.</span><span class="sxs-lookup"><span data-stu-id="07ddf-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="07ddf-413">Outra maneira poderia estar apenas copiando as imagens do dispositivo IoT para o contêiner.</span><span class="sxs-lookup"><span data-stu-id="07ddf-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="07ddf-414">Uma maneira prática para fazer isso é executar o comando a seguir no dispositivo IoT do Terminal (o talvez um pequeno aplicativo poderia fazer o trabalho, se você quisesse automatizar o processo).</span><span class="sxs-lookup"><span data-stu-id="07ddf-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="07ddf-415">Você pode testar esse comando, executando-o manualmente do local de pasta onde os arquivos são armazenados:</span><span class="sxs-lookup"><span data-stu-id="07ddf-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="07ddf-416">Capítulo 10 - depuração de tempo de execução do IoT Edge</span><span class="sxs-lookup"><span data-stu-id="07ddf-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="07ddf-417">A seguir é uma lista de linhas de comando e dicas para ajudá-lo a monitorar e depurar as atividades de mensagem do *tempo de execução do IoT Edge*, do seu **dispositivo Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="07ddf-418">Verifique as *tempo de execução do IoT Edge* status executando a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="07ddf-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="07ddf-419">Lembre-se de pressionar **Ctrl + C**, para terminar de exibir o status.</span><span class="sxs-lookup"><span data-stu-id="07ddf-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="07ddf-420">Liste os contêineres que estão implantados no momento.</span><span class="sxs-lookup"><span data-stu-id="07ddf-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="07ddf-421">Se o *no Hub IOT* tiver implantado os contêineres com êxito, eles serão exibidos, executando a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="07ddf-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="07ddf-422">Ou</span><span class="sxs-lookup"><span data-stu-id="07ddf-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="07ddf-423">As opções acima é uma boa maneira de verificar se o módulo foi implantado com êxito, como ele aparecerá na lista; Caso contrário, você irá **só** consulte o *edgeHub* e *edgeAgent*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="07ddf-424">Para exibir os logs de código de um contêiner, execute a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="07ddf-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="07ddf-425">**Comandos úteis para gerenciar o tempo de execução do IoT Edge:**</span><span class="sxs-lookup"><span data-stu-id="07ddf-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="07ddf-426">Para excluir todos os contêineres no host:</span><span class="sxs-lookup"><span data-stu-id="07ddf-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="07ddf-427">Para parar o *tempo de execução do IoT Edge*:</span><span class="sxs-lookup"><span data-stu-id="07ddf-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="07ddf-428">Capítulo 11 - criar o serviço tabela</span><span class="sxs-lookup"><span data-stu-id="07ddf-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="07ddf-429">Navegue de volta para seu Portal do Azure, onde você irá criar um serviço de tabelas do Azure, criando um recurso de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="07ddf-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="07ddf-430">Se ainda não estiver conectado, faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="07ddf-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="07ddf-431">Depois de conectado, clique em **criar um recurso**, no canto superior esquerdo de canto e procure **conta de armazenamento**e pressione a **Enter** tecla para iniciar a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="07ddf-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="07ddf-432">Depois que ele é exibido, clique em **conta de armazenamento - blob, arquivo, tabela, fila** na lista.</span><span class="sxs-lookup"><span data-stu-id="07ddf-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Procure a conta de armazenamento](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="07ddf-434">A nova página fornecerá uma descrição do **conta de armazenamento** Service.</span><span class="sxs-lookup"><span data-stu-id="07ddf-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="07ddf-435">Na parte inferior esquerda desse prompt, clique no **criar** botão para criar uma instância deste serviço.</span><span class="sxs-lookup"><span data-stu-id="07ddf-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="07ddf-437">Depois de clicar em **criar**, um painel será exibido:</span><span class="sxs-lookup"><span data-stu-id="07ddf-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="07ddf-438">Inserir sua desejada **nome** para esta instância de serviço (*deve estar em letras minúsculas*).</span><span class="sxs-lookup"><span data-stu-id="07ddf-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="07ddf-439">Para **modelo de implantação**, clique em **Gerenciador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="07ddf-440">Para **tipo de conta**, usando o menu suspenso, clique em **(uso geral v1) de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="07ddf-441">Clique em um número apropriado **local**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="07ddf-442">Para o **replicação** menu suspenso, clique em **leitura-acesso-com redundância geográfica (RA-GRS) de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="07ddf-443">Para **desempenho**, clique em **padrão**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="07ddf-444">Dentro de **transferência segura obrigatória** seção, clique em **desabilitado**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="07ddf-445">Dos **assinatura** menu suspenso, clique em uma assinatura apropriada.</span><span class="sxs-lookup"><span data-stu-id="07ddf-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="07ddf-446">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="07ddf-447">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar, de cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="07ddf-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="07ddf-448">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="07ddf-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="07ddf-449">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="07ddf-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="07ddf-450">Deixe **redes virtuais** como **desabilitado**, se essa é uma opção para você.</span><span class="sxs-lookup"><span data-stu-id="07ddf-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="07ddf-451">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-451">Click **Create**.</span></span>

        ![Preencha os detalhes de armazenamento](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="07ddf-453">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="07ddf-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="07ddf-454">Uma notificação será exibida no Portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="07ddf-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="07ddf-455">Clique em notificações para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="07ddf-455">Click on the notifications to explore your new Service instance.</span></span>

    ![nova notificação de armazenamento](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="07ddf-457">Clique o **ir para o recurso** botão na notificação e você será levado para a nova página de visão geral de instância de serviço de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="07ddf-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![Ir para o recurso](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="07ddf-459">Na página de visão geral, para o lado direito, clique em **tabelas**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![Tabelas](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="07ddf-461">O painel à direita será alterado para mostrar o **serviço tabela** informações, no qual você precisa adicionar uma nova tabela.</span><span class="sxs-lookup"><span data-stu-id="07ddf-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="07ddf-462">Faça isso clicando o **+ tabela** botão no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![abrir tabelas](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="07ddf-464">Uma nova página será mostrada, no qual você precisa inserir uma **nome da tabela**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="07ddf-465">Esse é o nome que você usará para se referir aos dados em seu aplicativo em capítulos (criar aplicativo de funções e o Power BI).</span><span class="sxs-lookup"><span data-stu-id="07ddf-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="07ddf-466">Inserir **IoTMessages** como o nome (você pode escolher seus próprios, lembre-se, quando usado neste documento) e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="07ddf-467">Quando a nova tabela tiver sido criada, você poderá vê-lo dentro de **serviço tabela** página (na parte inferior).</span><span class="sxs-lookup"><span data-stu-id="07ddf-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![nova tabela criada](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="07ddf-469">Agora, clique em **chaves de acesso** e faça uma cópia do **nome da conta de armazenamento** e **chave** (usando o bloco de notas), você usará esses valores posteriormente no curso, ao criar o **Aplicativo de funções do azure**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![nova tabela criada](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="07ddf-471">Usando o painel à esquerda, role até a *serviço de tabela* seção e, em seguida, clique em **tabelas** (ou **procurar tabelas**, em portais de mais recentes) e faça uma cópia do  **URL de tabela** (usando o bloco de notas).</span><span class="sxs-lookup"><span data-stu-id="07ddf-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="07ddf-472">Você usará esse valor posteriormente no curso, ao vincular a sua tabela para seu **Power BI** aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![nova tabela criada](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="07ddf-474">Capítulo 12 - Concluindo a tabela do Azure</span><span class="sxs-lookup"><span data-stu-id="07ddf-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="07ddf-475">Agora que sua **serviço tabela** conta de armazenamento tiver sido configurado, é hora de adicionar dados a ele, que será usada para armazenar e recuperar informações.</span><span class="sxs-lookup"><span data-stu-id="07ddf-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="07ddf-476">A edição de suas tabelas pode ser feita por meio **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="07ddf-477">Abra **Visual Studio** (**não** Visual Studio Code).</span><span class="sxs-lookup"><span data-stu-id="07ddf-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="07ddf-478">No menu, clique em **exibição > Gerenciador de nuvem**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-478">From the menu, click **View > Cloud Explorer**.</span></span>

    ![Abra o cloud explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="07ddf-480">O **Cloud Explorer** será aberto como um item encaixado (seja paciente, pois o carregamento pode levar tempo).</span><span class="sxs-lookup"><span data-stu-id="07ddf-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="07ddf-481">Se a assinatura que você usou para criar sua *contas de armazenamento* não estiver visível, certifique-se de que você tenha:</span><span class="sxs-lookup"><span data-stu-id="07ddf-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="07ddf-482">Conectado à mesma conta que você usou para o Portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="07ddf-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="07ddf-483">Selecionado sua assinatura na página de gerenciamento de conta (talvez você precise aplicar um filtro de suas configurações de conta):</span><span class="sxs-lookup"><span data-stu-id="07ddf-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![localizar a assinatura](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="07ddf-485">Os serviços de nuvem do Azure serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="07ddf-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="07ddf-486">Encontre **contas de armazenamento** e clique na seta à esquerda do que para expandir suas contas.</span><span class="sxs-lookup"><span data-stu-id="07ddf-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Abra as contas de armazenamento](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="07ddf-488">Quando expandida, seu recém-criado **conta de armazenamento** devem estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="07ddf-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="07ddf-489">Clique na seta à esquerda de seu armazenamento e, em seguida, depois que é expandido, encontrar **tabelas** e clique na seta ao lado de que, para revelar as **tabela** você criou no último capítulo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="07ddf-490">Clique duas vezes em sua **tabela**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="07ddf-491">A tabela será aberta no centro da janela do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07ddf-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="07ddf-492">Clique no ícone de tabela com o **+** (mais) nele.</span><span class="sxs-lookup"><span data-stu-id="07ddf-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![Adicionar nova tabela](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="07ddf-494">Uma janela será exibida solicitando que você *Adicionar entidade*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="07ddf-495">Você irá criar apenas uma única entidade, embora ele terá três propriedades.</span><span class="sxs-lookup"><span data-stu-id="07ddf-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="07ddf-496">Você observará que *PartitionKey* e *RowKey* já são fornecidas, pois eles são usados pela tabela para localizar os dados.</span><span class="sxs-lookup"><span data-stu-id="07ddf-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![chave de partição e de linha](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="07ddf-498">Atualize os valores a seguir:</span><span class="sxs-lookup"><span data-stu-id="07ddf-498">Update the following values:</span></span>

    - <span data-ttu-id="07ddf-499">Nome: **PartitionKey**, valor: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="07ddf-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="07ddf-500">Nome: **RowKey**, valor: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="07ddf-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="07ddf-501">Em seguida, clique em **adicionar propriedade** (para o canto inferior esquerdo das *Adicionar entidade* janela) e adicione a seguinte propriedade:</span><span class="sxs-lookup"><span data-stu-id="07ddf-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="07ddf-502">**O MessageContent**, como uma *cadeia de caracteres*, deixe o valor vazio.</span><span class="sxs-lookup"><span data-stu-id="07ddf-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="07ddf-503">Sua tabela deve corresponder na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="07ddf-503">Your table should match the one in the image below:</span></span>

    ![Adicione os valores corretos](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="07ddf-505">O motivo por que a entidade tem o número 1 na chave de linha, é porque deseja adicionar mais mensagens, você deseja fazer experiências com este curso.</span><span class="sxs-lookup"><span data-stu-id="07ddf-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="07ddf-506">Clique em **Okey** quando tiver terminado.</span><span class="sxs-lookup"><span data-stu-id="07ddf-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="07ddf-507">A tabela agora está pronta para ser usado.</span><span class="sxs-lookup"><span data-stu-id="07ddf-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="07ddf-508">Capítulo 13 - criar um aplicativo de funções do Azure</span><span class="sxs-lookup"><span data-stu-id="07ddf-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="07ddf-509">Chegou a hora agora para criar uma *aplicativo de funções do Azure*, que será chamado pelo *no Hub IOT* para armazenar os *do IoT Edge* mensagens de dispositivo na **tabela** Serviço, que você criou no capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="07ddf-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="07ddf-510">Primeiro, você precisa criar um arquivo que permitirá que sua função do Azure carregar as bibliotecas que necessárias.</span><span class="sxs-lookup"><span data-stu-id="07ddf-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="07ddf-511">Abra **bloco de notas** (pressione a *chave do Windows*e o tipo *o bloco de notas*).</span><span class="sxs-lookup"><span data-stu-id="07ddf-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![Abra o bloco de notas](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="07ddf-513">Com o bloco de notas aberto, insira a estrutura JSON abaixo nela.</span><span class="sxs-lookup"><span data-stu-id="07ddf-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="07ddf-514">Depois de ter feito isso, salve-o na área de trabalho como **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="07ddf-515">Esse arquivo define as bibliotecas de que sua função usará.</span><span class="sxs-lookup"><span data-stu-id="07ddf-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="07ddf-516">Se você tiver usado o NuGet, parecerá familiar.</span><span class="sxs-lookup"><span data-stu-id="07ddf-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="07ddf-517">É importante que a nomenclatura está correta; Certifique-se de que ele faz **não tiver uma. txt** extensão de arquivo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="07ddf-518">Veja abaixo para referência:</span><span class="sxs-lookup"><span data-stu-id="07ddf-518">See below for reference:</span></span>
    >
    > ![JSON save](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="07ddf-520">Faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="07ddf-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="07ddf-521">Quando você estiver conectado, clique em **criar um recurso** no canto superior esquerdo de canto e procure **aplicativo de funções**e pressione a **Enter** chave a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="07ddf-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="07ddf-522">Clique em *aplicativo de funções* nos resultados, para abrir um novo painel.</span><span class="sxs-lookup"><span data-stu-id="07ddf-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![Procure o aplicativo de funções](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="07ddf-524">O novo painel fornecerá uma descrição do **aplicativo de funções** Service.</span><span class="sxs-lookup"><span data-stu-id="07ddf-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="07ddf-525">Na parte inferior esquerda deste painel, clique no **criar** botão para criar uma associação com este serviço.</span><span class="sxs-lookup"><span data-stu-id="07ddf-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![instância do aplicativo de função](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="07ddf-527">Depois de clicar em **criar**, preencha o seguinte:</span><span class="sxs-lookup"><span data-stu-id="07ddf-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="07ddf-528">Para **nome do aplicativo**, inserir seu nome desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="07ddf-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="07ddf-529">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="07ddf-530">Selecione o tipo de preço apropriado para você, se esta for a primeira hora de criar uma **serviço de aplicativo de função**, uma camada gratuita deve estar disponível para você.</span><span class="sxs-lookup"><span data-stu-id="07ddf-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="07ddf-531">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="07ddf-532">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar, de cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="07ddf-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="07ddf-533">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="07ddf-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="07ddf-534">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="07ddf-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="07ddf-535">Para **SO**, clique em Windows, já que é a plataforma destinada.</span><span class="sxs-lookup"><span data-stu-id="07ddf-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="07ddf-536">Selecione uma **plano de hospedagem** (Este tutorial está usando uma **plano de consumo**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="07ddf-537">Selecione uma **local** (escolha o mesmo local como o armazenamento que você criou na etapa anterior)</span><span class="sxs-lookup"><span data-stu-id="07ddf-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="07ddf-538">Para o **armazenamento** seção, **você deve selecionar o serviço de armazenamento que você criou na etapa anterior**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="07ddf-539">Você não precisará *Application Insights* neste aplicativo, fique à vontade para deixá-lo **Off**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="07ddf-540">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-540">Click **Create**.</span></span>

        ![Criar nova instância](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="07ddf-542">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="07ddf-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="07ddf-543">Uma notificação será exibida no Portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="07ddf-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![nova notificação](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="07ddf-545">Clique na notificação, quando a implantação for bem-sucedida (terminou).</span><span class="sxs-lookup"><span data-stu-id="07ddf-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="07ddf-546">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="07ddf-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Ir para o recurso](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="07ddf-548">No lado esquerdo do novo painel, clique no **+** (mais) ícone próximo ao *funções*, para criar uma nova função.</span><span class="sxs-lookup"><span data-stu-id="07ddf-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![Adicionar nova função](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="07ddf-550">No painel central, o **função** será exibida a janela de criação.</span><span class="sxs-lookup"><span data-stu-id="07ddf-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="07ddf-551">Role mais para baixo e clique em **função personalizada**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-551">Scroll down further, and click on **Custom function**.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="07ddf-553">Role para baixo próxima página, até encontrar **IoT Hub (Hub de eventos)**, em seguida, clique nele.</span><span class="sxs-lookup"><span data-stu-id="07ddf-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="07ddf-555">No **IoT Hub (Hub de eventos)** folha, defina as **idioma** para **C#** e, em seguida, clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="07ddf-557">Na janela que será exibido, certifique-se de que **IoT Hub** está selecionado e o nome da *IoT Hub* campo corresponde com o nome do seu *serviço Hub IoT* que você tem criado anteriormente ([na etapa 8, do capítulo 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="07ddf-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="07ddf-558">Em seguida, clique o **selecionar** botão.</span><span class="sxs-lookup"><span data-stu-id="07ddf-558">Then click the **Select** button.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="07ddf-560">Volta a **IoT Hub (Hub de eventos)** folha, clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="07ddf-562">Você será redirecionado para o editor de função.</span><span class="sxs-lookup"><span data-stu-id="07ddf-562">You will be redirected to the function editor.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="07ddf-564">Exclua todo o código nele e substitua-o com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="07ddf-564">Delete all the code in it and replace it with the following:</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. <span data-ttu-id="07ddf-565">Alterar as variáveis a seguir, para que eles correspondam com os valores apropriados (**tabela** e **armazenamento** valores, da [etapa 11 e 13, respectivamente, do Capítulo 11](#chapter-11---create-table-service)), que você encontrará em sua **conta de armazenamento**:</span><span class="sxs-lookup"><span data-stu-id="07ddf-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="07ddf-566">**tableName**, com o nome do seu **tabela** localizado no seu **conta de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="07ddf-567">**tableURL**, com a URL do seu **tabela** localizado no seu **conta de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="07ddf-568">**storageAccountName**, com o nome do valor correspondente com o nome do seu **conta de armazenamento** nome.</span><span class="sxs-lookup"><span data-stu-id="07ddf-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="07ddf-569">**storageAccountKey**, com a chave que você obteve no serviço de armazenamento que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="07ddf-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="07ddf-571">Com o código no local, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="07ddf-572">Em seguida, clique o **\<** ícone (seta), no lado direito da página.</span><span class="sxs-lookup"><span data-stu-id="07ddf-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="07ddf-574">Um painel será Deslizar pela direita.</span><span class="sxs-lookup"><span data-stu-id="07ddf-574">A panel will slide in from the right.</span></span> <span data-ttu-id="07ddf-575">Nesse painel, clique em **carregue**e um *navegador de arquivos* será exibida.</span><span class="sxs-lookup"><span data-stu-id="07ddf-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="07ddf-576">Navegue até e, em seguida, clique em, o **Project. JSON** arquivo, que você criou na **bloco de notas** anteriormente e, em seguida, clique no **abrir** botão.</span><span class="sxs-lookup"><span data-stu-id="07ddf-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="07ddf-577">Esse arquivo define as bibliotecas que sua função usará.</span><span class="sxs-lookup"><span data-stu-id="07ddf-577">This file defines the libraries that your function will use.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="07ddf-579">Quando o arquivo foi carregado, ele será exibido no painel à direita.</span><span class="sxs-lookup"><span data-stu-id="07ddf-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="07ddf-580">Ao clicar nele irá abri-lo dentro de **função** editor.</span><span class="sxs-lookup"><span data-stu-id="07ddf-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="07ddf-581">Ele deve parecer **exatamente** o mesmo que a imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="07ddf-581">It must look **exactly** the same as the next image.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="07ddf-583">Neste ponto, seria bom testar a funcionalidade de sua função para armazenar a mensagem em seu *tabela*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="07ddf-584">No lado superior direito da janela, clique em **teste**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-584">On the top right side of the window, click on **Test**.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="07ddf-586">Inserir uma mensagem sobre o **corpo da solicitação**, conforme mostrado na imagem acima e clique em **executar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="07ddf-587">A função será executado, exibindo o status do resultado (você observará que o verde **Status de 202 aceito**, acima o *saída* janela, o que significa que ele foi uma chamada bem-sucedida):</span><span class="sxs-lookup"><span data-stu-id="07ddf-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![resultado de saída](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="07ddf-589">Capítulo 14 - exibir mensagens de Active Directory</span><span class="sxs-lookup"><span data-stu-id="07ddf-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="07ddf-590">Se você abrir o Visual Studio agora (**não** Visual Studio Code), você pode visualizar o resultado da mensagem de teste, pois ele será armazenado na *o MessageContent* área de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="07ddf-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![função personalizada](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="07ddf-592">Com o serviço de tabela e o aplicativo de funções em vigor, as mensagens de dispositivo do Ubuntu aparecerá no seu *IoTMessages* tabela.</span><span class="sxs-lookup"><span data-stu-id="07ddf-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="07ddf-593">Se ainda não estiver em execução, inicie o dispositivo novamente e você poderá ver as mensagens de resultado do seu dispositivo, módulo e, dentro de sua tabela, por meio do usando o Visual Studio *Cloud Explorer*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![Visualizar dados](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="07ddf-595">Capítulo 15 - instalação do Power BI</span><span class="sxs-lookup"><span data-stu-id="07ddf-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="07ddf-596">Para visualizar os dados do seu dispositivo IOT, você configurará **Power BI** (versão da área de trabalho,) para coletar os dados das *tabela* serviço, que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="07ddf-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="07ddf-597">O *HoloLens* versão do Power BI, em seguida, usará esses dados para visualizar o resultado.</span><span class="sxs-lookup"><span data-stu-id="07ddf-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="07ddf-598">Abra o Microsoft Store no Windows 10 e pesquise **Power BI Desktop**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="07ddf-600">Baixe o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-600">Download the application.</span></span> <span data-ttu-id="07ddf-601">Depois que o download for concluído, abra-o.</span><span class="sxs-lookup"><span data-stu-id="07ddf-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="07ddf-602">Faça logon no *Power BI* com seu **conta do Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="07ddf-603">Você pode ser redirecionado para um navegador, para se inscrever.</span><span class="sxs-lookup"><span data-stu-id="07ddf-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="07ddf-604">Depois que você se inscreveu, vá até o aplicativo Power BI e entrar novamente.</span><span class="sxs-lookup"><span data-stu-id="07ddf-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="07ddf-605">Clique em **obter dados** e, em seguida, clique em **mais...** .</span><span class="sxs-lookup"><span data-stu-id="07ddf-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="07ddf-607">Clique em **Azure**, **Azure Table Storage**, em seguida, clique em **Connect**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="07ddf-609">Você será solicitado a inserir o **adresa URL Tabulky** coletados anteriormente ([na etapa 13 do Capítulo 11](#chapter-11---create-table-service)), durante a criação de seu serviço de tabela.</span><span class="sxs-lookup"><span data-stu-id="07ddf-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="07ddf-610">Depois de inserir a URL, exclua a parte do caminho da referência à tabela "subpasta" (que era IoTMessages, neste curso).</span><span class="sxs-lookup"><span data-stu-id="07ddf-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="07ddf-611">O resultado final deve ser conforme exibido na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="07ddf-612">Em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="07ddf-614">Você será solicitado a inserir o **chave de armazenamento** que você anotou ([na etapa 11 do Capítulo 11](#chapter-11---create-table-service)) anteriores durante a criação de seu armazenamento de tabelas.</span><span class="sxs-lookup"><span data-stu-id="07ddf-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="07ddf-615">Em seguida, clique em **Connect**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="07ddf-617">Um **painel navegador** será exibida, marque a caixa ao lado de sua tabela e clique em **carga**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="07ddf-619">Sua tabela agora tenha sido carregada no Power BI, mas requer uma consulta para exibir os valores nele.</span><span class="sxs-lookup"><span data-stu-id="07ddf-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="07ddf-620">Para fazer isso, clique com botão direito no nome da tabela localizado na **painel CAMPOS** no lado direito da tela.</span><span class="sxs-lookup"><span data-stu-id="07ddf-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="07ddf-621">Em seguida, clique em **Editar consulta**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="07ddf-623">Um **Editor do Power Query** será aberta como uma nova janela, exibindo sua tabela.</span><span class="sxs-lookup"><span data-stu-id="07ddf-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="07ddf-624">Clique na palavra **registro** dentro de *conteúdo* coluna da tabela, para visualizar seu conteúdo armazenado.</span><span class="sxs-lookup"><span data-stu-id="07ddf-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="07ddf-626">Clique em **em uma tabela**, no canto superior esquerdo da janela.</span><span class="sxs-lookup"><span data-stu-id="07ddf-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="07ddf-628">Clique em **fechar e aplicar**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="07ddf-630">Depois de terminar de carregar a consulta dentro de **painel CAMPOS**, no lado direito da tela, marque as caixas correspondentes aos parâmetros **nome** e **valor**, para visualizar a **o MessageContent** conteúdo da coluna.</span><span class="sxs-lookup"><span data-stu-id="07ddf-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="07ddf-632">Clique no **ícone de disco azul** na parte superior esquerda da janela para salvar seu trabalho em uma pasta de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="07ddf-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="07ddf-634">Agora, você pode clicar no botão Publicar para carregar a tabela para seu espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="07ddf-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="07ddf-635">Quando solicitado, clique em **meu espaço de trabalho** e clique em *selecione*.</span><span class="sxs-lookup"><span data-stu-id="07ddf-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="07ddf-636">Aguarde exibir o resultado com êxito do envio.</span><span class="sxs-lookup"><span data-stu-id="07ddf-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="07ddf-639">O capítulo seguinte é específico do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="07ddf-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="07ddf-640">Power BI não está atualmente disponível como um aplicativo imersivo, no entanto, você pode executar a versão da área de trabalho no Portal de realidade mista do Windows (também conhecido como Cliff House), por meio do aplicativo da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="07ddf-640">Power BI is not currently availble as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="07ddf-641">Capítulo 16 - dados de exibição Power BI em HoloLens</span><span class="sxs-lookup"><span data-stu-id="07ddf-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="07ddf-642">No seu HoloLens, faça login para o **Microsoft Store**, tocando no ícone na lista de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="07ddf-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="07ddf-644">Pesquisar e, em seguida, baixe o **Power BI** aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="07ddf-646">Inicie **Power BI** da sua lista de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="07ddf-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="07ddf-647">**Power BI** pode solicitar que você fazer logon em seu **conta do Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="07ddf-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="07ddf-648">Uma vez dentro do aplicativo, o espaço de trabalho deve exibir por padrão como mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="07ddf-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="07ddf-649">Se isso não acontecer, basta clicar no ícone no lado esquerdo da janela do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="07ddf-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="07ddf-651">A conclusão de seu aplicativo de IoT Hub</span><span class="sxs-lookup"><span data-stu-id="07ddf-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="07ddf-652">Parabéns, você criou com êxito um serviço de Hub IoT, com um dispositivo simulado de borda de máquina Virtual.</span><span class="sxs-lookup"><span data-stu-id="07ddf-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="07ddf-653">Seu dispositivo pode se comunicar os resultados de um modelo de machine learning para um serviço de tabela do Azure, facilitada por um aplicativo de função do Azure, que é lido no Power BI e visualizados dentro de um Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="07ddf-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="07ddf-655">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="07ddf-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="07ddf-656">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="07ddf-656">Exercise 1</span></span>

<span data-ttu-id="07ddf-657">Expanda a estrutura de mensagens armazenada na tabela e exibi-lo como um gráfico.</span><span class="sxs-lookup"><span data-stu-id="07ddf-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="07ddf-658">Você talvez queira coletar mais dados e armazená-lo na mesma tabela, a ser exibido mais tarde.</span><span class="sxs-lookup"><span data-stu-id="07ddf-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="07ddf-659">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="07ddf-659">Exercise 2</span></span>

<span data-ttu-id="07ddf-660">Criar um adicional "captura com câmera" módulo a ser implantado na placa de IoT, para que ele possa capturar imagens através da câmera a serem analisados.</span><span class="sxs-lookup"><span data-stu-id="07ddf-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
