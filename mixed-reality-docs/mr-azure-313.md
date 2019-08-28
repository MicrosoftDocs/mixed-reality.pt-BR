---
title: Sr e Azure 313-serviço de Hub IoT
description: Conclua este curso para aprender a implementar o serviço de Hub IoT do Azure em uma máquina virtual que executa o Ubuntu 16,4 e, em seguida, Visualizar os dados da mensagem usando o Microsoft HoloLens ou um headset de imersão (VR).
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, borda, IOT Edge, tutorial, API, notificação, funções, tabelas, hololens, imersão, VR, IOT, máquina virtual, Ubuntu, Python
ms.openlocfilehash: ec669b799e7c46a9a4ed87674ed78e50f816c9e9
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047238"
---
>[!NOTE]
><span data-ttu-id="c298d-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c298d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c298d-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c298d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c298d-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c298d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c298d-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="c298d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c298d-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c298d-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c298d-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="c298d-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="c298d-110">Sr e Azure 313: Serviço do Hub IoT</span><span class="sxs-lookup"><span data-stu-id="c298d-110">MR and Azure 313: IoT Hub Service</span></span>

![resultado do curso](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="c298d-112">Neste curso, você aprenderá a implementar um serviço de **Hub IOT do Azure** em uma máquina virtual que executa o sistema operacional Ubuntu 16,4.</span><span class="sxs-lookup"><span data-stu-id="c298d-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="c298d-113">Um **aplicativo de funções do Azure** será usado para receber mensagens de sua VM do Ubuntu e armazenar o resultado em um **serviço tabela do Azure**.</span><span class="sxs-lookup"><span data-stu-id="c298d-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="c298d-114">Você poderá exibir esses dados usando **Power bi** em fone de ouvido Microsoft HoloLens ou IMERSIVA (VR).</span><span class="sxs-lookup"><span data-stu-id="c298d-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="c298d-115">O conteúdo deste curso *é aplicável* a IOT Edge dispositivos, no entanto, para fins deste curso, o foco estará em um ambiente de máquina virtual, para que o acesso a um dispositivo de borda físico não seja necessário.</span><span class="sxs-lookup"><span data-stu-id="c298d-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="c298d-116">Ao concluir este curso, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="c298d-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="c298d-117">Implante um **módulo IOT Edge** em uma máquina virtual (Ubuntu 16 os), que representará seu dispositivo IOT.</span><span class="sxs-lookup"><span data-stu-id="c298d-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="c298d-118">Adicione um **modelo do Azure visão personalizada Tensorflow** ao módulo de borda, com código que analisará as imagens armazenadas no contêiner.</span><span class="sxs-lookup"><span data-stu-id="c298d-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="c298d-119">Configure o módulo para enviar a mensagem de resultado de análise de volta para o **serviço do Hub IOT**.</span><span class="sxs-lookup"><span data-stu-id="c298d-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="c298d-120">Use uma **aplicativo de funções do Azure** para armazenar a mensagem em uma **tabela do Azure**.</span><span class="sxs-lookup"><span data-stu-id="c298d-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="c298d-121">Configure **Power bi** para coletar a mensagem armazenada e criar um relatório.</span><span class="sxs-lookup"><span data-stu-id="c298d-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="c298d-122">Visualize os dados da mensagem de IoT dentro do **Power bi**.</span><span class="sxs-lookup"><span data-stu-id="c298d-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="c298d-123">Os serviços que serão usados incluem:</span><span class="sxs-lookup"><span data-stu-id="c298d-123">The Services you will use include:</span></span>

- <span data-ttu-id="c298d-124">O **Hub IOT do Azure** é um serviço Microsoft Azure que permite aos desenvolvedores conectar, monitorar e gerenciar ativos de IOT.</span><span class="sxs-lookup"><span data-stu-id="c298d-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="c298d-125">Para obter mais informações, visite a página de [ **serviço do Hub IOT do Azure** ](https://azure.microsoft.com/en-au/services/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="c298d-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/en-au/services/iot-hub/).</span></span>

- <span data-ttu-id="c298d-126">O **registro de contêiner do Azure** é um serviço Microsoft Azure que permite aos desenvolvedores armazenar imagens de contêiner para vários tipos de contêineres.</span><span class="sxs-lookup"><span data-stu-id="c298d-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="c298d-127">Para obter mais informações, visite a página de [ **serviço do registro de contêiner do Azure** ](https://azure.microsoft.com/en-au/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="c298d-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/en-au/services/container-registry/).</span></span>

- <span data-ttu-id="c298d-128">O **azure aplicativo de funções** é um serviço Microsoft Azure, que permite aos desenvolvedores executar pequenas partes de código, ' Functions ', no Azure.</span><span class="sxs-lookup"><span data-stu-id="c298d-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="c298d-129">Isso fornece uma maneira de delegar trabalho para a nuvem, em vez de seu aplicativo local, que pode ter muitos benefícios.</span><span class="sxs-lookup"><span data-stu-id="c298d-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="c298d-130">O **Azure Functions** dá suporte a várias linguagens\#de desenvolvimento\#, incluindo C, F, Node. js, Java e php.</span><span class="sxs-lookup"><span data-stu-id="c298d-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="c298d-131">Para obter mais informações, visite a [página **Azure Functions** ](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="c298d-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="c298d-132">**Armazenamento do Azure: As** tabelas são um serviço Microsoft Azure, que permite aos desenvolvedores armazenar dados estruturados, não SQL, na nuvem, tornando-os facilmente acessíveis em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="c298d-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="c298d-133">O serviço apresenta um design sem esquema, permitindo a evolução das tabelas conforme necessário e, portanto, é muito flexível.</span><span class="sxs-lookup"><span data-stu-id="c298d-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="c298d-134">Para obter mais informações, visite a [página **tabelas do Azure**](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="c298d-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="c298d-135">Este curso ensinará a você como configurar e usar o serviço do Hub IoT e, em seguida, Visualizar uma resposta fornecida por um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c298d-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="c298d-136">Será necessário aplicar esses conceitos a uma configuração de serviço do Hub IoT personalizada, que você pode estar criando.</span><span class="sxs-lookup"><span data-stu-id="c298d-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="c298d-137">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="c298d-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c298d-138">Course</span><span class="sxs-lookup"><span data-stu-id="c298d-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c298d-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c298d-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c298d-140"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="c298d-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c298d-141">Sr e Azure 313: Serviço do Hub IoT</span><span class="sxs-lookup"><span data-stu-id="c298d-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="c298d-142">✔️</span><span class="sxs-lookup"><span data-stu-id="c298d-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c298d-143">✔️</span><span class="sxs-lookup"><span data-stu-id="c298d-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="c298d-144">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c298d-144">Prerequisites</span></span>

<span data-ttu-id="c298d-145">Para obter os pré-requisitos mais atualizados para o desenvolvimento com realidade misturada, incluindo com o Microsoft HoloLens, visite o artigo [instalar as ferramentas](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) .</span><span class="sxs-lookup"><span data-stu-id="c298d-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="c298d-146">Este tutorial foi projetado para desenvolvedores que têm experiência básica com o Python.</span><span class="sxs-lookup"><span data-stu-id="c298d-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="c298d-147">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (julho de 2018).</span><span class="sxs-lookup"><span data-stu-id="c298d-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="c298d-148">Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso correspondam perfeitamente ao que você encontrará em softwares mais recentes do que os listados abaixo.</span><span class="sxs-lookup"><span data-stu-id="c298d-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="c298d-149">O hardware e o software a seguir são necessários:</span><span class="sxs-lookup"><span data-stu-id="c298d-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="c298d-150">Atualização dos criadores de outono do Windows 10 (ou posterior), **modo de desenvolvedor habilitado**</span><span class="sxs-lookup"><span data-stu-id="c298d-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="c298d-151">Você não pode executar uma máquina virtual usando o Hyper-V no Windows 10 Home Edition.</span><span class="sxs-lookup"><span data-stu-id="c298d-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="c298d-152">SDK do Windows 10 (versão mais recente)</span><span class="sxs-lookup"><span data-stu-id="c298d-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="c298d-153">Um HoloLens, **modo de desenvolvedor habilitado**</span><span class="sxs-lookup"><span data-stu-id="c298d-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="c298d-154">Visual Studio 2017.15.4 (usado somente para acessar o Azure cloud Explorer)</span><span class="sxs-lookup"><span data-stu-id="c298d-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="c298d-155">Acesso à Internet para o Azure e para o serviço Hub IoT.</span><span class="sxs-lookup"><span data-stu-id="c298d-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="c298d-156">Para obter mais informações, siga este [link para a página de serviço do Hub IOT](https://azure.microsoft.com/en-au/services/iot-hub/)</span><span class="sxs-lookup"><span data-stu-id="c298d-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/en-au/services/iot-hub/)</span></span>
- <span data-ttu-id="c298d-157">Um modelo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="c298d-157">A machine learning model.</span></span> <span data-ttu-id="c298d-158">Se você não tiver seu próprio modelo pronto para usar, [poderá usar o modelo fornecido com este curso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span><span class="sxs-lookup"><span data-stu-id="c298d-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="c298d-159">Software **Hyper-V** habilitado em seu computador de desenvolvimento do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c298d-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="c298d-160">Uma máquina virtual executando o Ubuntu (16,4 ou 18,4), em execução em seu computador de desenvolvimento ou, como alternativa, você pode usar um computador separado executando o Linux (Ubuntu 16,4 ou 18,4).</span><span class="sxs-lookup"><span data-stu-id="c298d-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="c298d-161">Você pode encontrar mais informações sobre como criar uma VM no Windows usando o Hyper-V no [capítulo "antes de começar"](#before-you-start). (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="c298d-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="c298d-162">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="c298d-162">Before you start</span></span>

1. <span data-ttu-id="c298d-163">Configure e teste seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c298d-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="c298d-164">Se você precisar de suporte para configurar seu HoloLens, [visite o artigo configuração do hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="c298d-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="c298d-165">É uma boa ideia executar a calibragem e o **ajuste do sensor** ao começar a desenvolver um novo aplicativo do HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="c298d-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="c298d-166">Para obter ajuda sobre calibragem, siga este [link para o artigo Calibration do HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="c298d-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="c298d-167">Para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste do sensor do HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="c298d-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="c298d-168">Configure sua **máquina virtual Ubuntu** usando o **Hyper-V**.</span><span class="sxs-lookup"><span data-stu-id="c298d-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="c298d-169">Os recursos a seguir ajudarão você com o processo.</span><span class="sxs-lookup"><span data-stu-id="c298d-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="c298d-170">Primeiro, siga este link para [baixar o ISO 16.04.4 LTS (Xenial Xerus)](http://au.releases.ubuntu.com/16.04/).</span><span class="sxs-lookup"><span data-stu-id="c298d-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="c298d-171">Selecione a **imagem da área de trabalho do PC de 64 bits (amd64)** .</span><span class="sxs-lookup"><span data-stu-id="c298d-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="c298d-172">Verifique se o **Hyper-V** está habilitado em seu computador com Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c298d-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="c298d-173">Você pode seguir este link para obter orientação sobre como [instalar e habilitar o Hyper-V no Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span><span class="sxs-lookup"><span data-stu-id="c298d-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="c298d-174">Inicie o Hyper-V e crie uma nova VM Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="c298d-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="c298d-175">Você pode seguir este link para obter um [guia passo a passo sobre como criar uma VM com o Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="c298d-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="c298d-176">Quando solicitado a **"instalar um sistema operacional de um arquivo de imagem inicializável"** , selecione a **ISO do Ubuntu** que você baixou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c298d-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c298d-177">Não é recomendável usar a **criação rápida do Hyper-V** .</span><span class="sxs-lookup"><span data-stu-id="c298d-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="c298d-178">Capítulo 1 – recuperar o modelo de Visão Personalizada</span><span class="sxs-lookup"><span data-stu-id="c298d-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="c298d-179">Com este curso, você terá acesso a um [modelo de visão personalizada predefinido](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) que detecta teclados e mouses de imagens.</span><span class="sxs-lookup"><span data-stu-id="c298d-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="c298d-180">Se você usar isso, vá para o [capítulo 2](#chapter-2---the-container-registry-service).</span><span class="sxs-lookup"><span data-stu-id="c298d-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="c298d-181">No entanto, você pode seguir estas etapas se desejar usar seu próprio modelo de Visão Personalizada:</span><span class="sxs-lookup"><span data-stu-id="c298d-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="c298d-182">Em seu **projeto de visão personalizada** , vá para a guia **desempenho** .</span><span class="sxs-lookup"><span data-stu-id="c298d-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="c298d-183">Seu modelo deve usar um domínio *compacto* para exportar o modelo.</span><span class="sxs-lookup"><span data-stu-id="c298d-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="c298d-184">Você pode alterar o domínio de modelos nas configurações do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c298d-184">You can change your models domain in the settings for your project.</span></span>

    ![guia desempenho](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="c298d-186">Selecione a **iteração** que você deseja exportar e clique em **Exportar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="c298d-187">Uma folha será exibida.</span><span class="sxs-lookup"><span data-stu-id="c298d-187">A blade will appear.</span></span>

    ![folha de exportação](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="c298d-189">Na folha, clique em **arquivo**do Docker.</span><span class="sxs-lookup"><span data-stu-id="c298d-189">In the blade click **Docker File**.</span></span>

    ![selecionar Docker](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="c298d-191">Clique em **Linux** no menu suspenso e, em seguida, clique em **baixar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![Clique em baixar](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="c298d-193">Descompacte o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c298d-193">Unzip the content.</span></span> <span data-ttu-id="c298d-194">Você vai usá-lo mais tarde neste curso.</span><span class="sxs-lookup"><span data-stu-id="c298d-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="c298d-195">Capítulo 2-o serviço de registro de contêiner</span><span class="sxs-lookup"><span data-stu-id="c298d-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="c298d-196">O **serviço de registro de contêiner** é o repositório usado para hospedar seus contêineres.</span><span class="sxs-lookup"><span data-stu-id="c298d-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="c298d-197">O **serviço do Hub IOT** que você criará e usará neste curso, se refere ao **serviço de registro de contêiner** para obter os contêineres a serem implantados em seu dispositivo de borda.</span><span class="sxs-lookup"><span data-stu-id="c298d-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="c298d-198">Primeiro, siga este [link para o portal do Azure](https://portal.azure.com/)e faça logon com suas credenciais.</span><span class="sxs-lookup"><span data-stu-id="c298d-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="c298d-199">Vá para **criar um recurso** e procure **registro de contêiner**.</span><span class="sxs-lookup"><span data-stu-id="c298d-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![registro de contêiner](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="c298d-201">Clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="c298d-202">Defina os parâmetros de instalação do serviço:</span><span class="sxs-lookup"><span data-stu-id="c298d-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="c298d-203">Insira um nome para seu projeto, neste exemplo, seu chamado **IoTCRegistry**.</span><span class="sxs-lookup"><span data-stu-id="c298d-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="c298d-204">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="c298d-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c298d-205">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="c298d-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="c298d-206">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="c298d-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="c298d-207">Defina o local do serviço.</span><span class="sxs-lookup"><span data-stu-id="c298d-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="c298d-208">Defina **usuário administrador** para **habilitar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="c298d-209">Defina **SKU** como **básico**.</span><span class="sxs-lookup"><span data-stu-id="c298d-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="c298d-210">Clique em **criar** e aguarde até que os serviços sejam criados.</span><span class="sxs-lookup"><span data-stu-id="c298d-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="c298d-211">Depois que a notificação for exibida informando sobre a criação bem-sucedida do *registro de contêiner*, clique em **ir para o recurso** a ser redirecionado para sua página de serviço.</span><span class="sxs-lookup"><span data-stu-id="c298d-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="c298d-212">Na página Serviço de *registro de contêiner* , clique em **chaves de acesso**.</span><span class="sxs-lookup"><span data-stu-id="c298d-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="c298d-213">Tome nota (você pode usar o bloco de notas) dos seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="c298d-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="c298d-214">**Servidor de logon**</span><span class="sxs-lookup"><span data-stu-id="c298d-214">**Login Server**</span></span>
    2. <span data-ttu-id="c298d-215">**Usu**</span><span class="sxs-lookup"><span data-stu-id="c298d-215">**Username**</span></span>
    3. <span data-ttu-id="c298d-216">**Senha**</span><span class="sxs-lookup"><span data-stu-id="c298d-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="c298d-217">Capítulo 3-o serviço do Hub IoT</span><span class="sxs-lookup"><span data-stu-id="c298d-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="c298d-218">Agora, você começará a criação e a configuração do seu **serviço de Hub IOT**.</span><span class="sxs-lookup"><span data-stu-id="c298d-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="c298d-219">Se ainda não estiver conectado, faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c298d-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="c298d-220">Depois de conectado, clique em **criar um recurso** no canto superior esquerdo e procure **Hub IOT**e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="c298d-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![Pesquisar conta de armazenamento](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="c298d-222">A nova página fornecerá uma descrição do serviço de **conta de armazenamento** .</span><span class="sxs-lookup"><span data-stu-id="c298d-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="c298d-223">Na parte inferior esquerda desse prompt, clique no botão **criar** para criar uma instância desse serviço.</span><span class="sxs-lookup"><span data-stu-id="c298d-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![criar instância de armazenamento](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="c298d-225">Depois de clicar em **criar**, um painel será exibido:</span><span class="sxs-lookup"><span data-stu-id="c298d-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="c298d-226">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="c298d-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c298d-227">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="c298d-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c298d-228">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="c298d-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="c298d-229">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c298d-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="c298d-230">Selecione um **local** apropriado (use o mesmo local em todos os serviços criados neste curso).</span><span class="sxs-lookup"><span data-stu-id="c298d-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="c298d-231">Insira o **nome** desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="c298d-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="c298d-232">Na parte inferior da página, clique em **avançar: Tamanho e escala**.</span><span class="sxs-lookup"><span data-stu-id="c298d-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![criar instância de armazenamento](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="c298d-234">Nesta página, selecione seu **preço e camada de escala** (se esta for sua primeira instância de serviço do Hub IOT, uma camada gratuita deverá estar disponível para você).</span><span class="sxs-lookup"><span data-stu-id="c298d-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="c298d-235">Clique em **examinar + criar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-235">Click on **Review + Create**.</span></span>

    ![criar instância de armazenamento](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="c298d-237">Examine suas configurações e clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-237">Review your settings and click on **Create**.</span></span>

    ![criar instância de armazenamento](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="c298d-239">Depois que a notificação for exibida informando sobre a criação bem-sucedida do serviço do *Hub IOT* , clique em **ir para o recurso** a ser redirecionado para sua página de serviço.</span><span class="sxs-lookup"><span data-stu-id="c298d-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![criar instância de armazenamento](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="c298d-241">Role o painel lateral à esquerda até ver o *Gerenciamento de dispositivo automático*, clique em **IOT Edge**.</span><span class="sxs-lookup"><span data-stu-id="c298d-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![criar instância de armazenamento](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="c298d-243">Na janela que aparece à direita, clique em **adicionar IOT Edge dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="c298d-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="c298d-244">Uma folha será exibida à direita.</span><span class="sxs-lookup"><span data-stu-id="c298d-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="c298d-245">Na folha, forneça ao novo dispositivo uma **ID de dispositivo** (um nome de sua escolha).</span><span class="sxs-lookup"><span data-stu-id="c298d-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="c298d-246">Em seguida, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-246">Then, click **Save**.</span></span> <span data-ttu-id="c298d-247">As chaves *primária* e *secundária* serão geradas automaticamente, se você tiver a **geração automática** de tiques.</span><span class="sxs-lookup"><span data-stu-id="c298d-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![criar instância de armazenamento](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="c298d-249">Você navegará de volta para a seção *dispositivos IOT Edge* , em que o novo dispositivo será listado.</span><span class="sxs-lookup"><span data-stu-id="c298d-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="c298d-250">Clique em seu novo dispositivo (descrito em vermelho na imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="c298d-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![criar instância de armazenamento](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="c298d-252">Na página de *detalhes do dispositivo* que aparece, faça uma cópia da **cadeia de conexão** (chave primária).</span><span class="sxs-lookup"><span data-stu-id="c298d-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![criar instância de armazenamento](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="c298d-254">Volte para o painel à esquerda e clique em políticas de *acesso compartilhado*para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="c298d-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="c298d-255">Na página exibida, clique em **iothubowner**e uma folha será exibida à direita da tela.</span><span class="sxs-lookup"><span data-stu-id="c298d-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="c298d-256">Tome nota (no bloco de notas) da **cadeia de conexão** (chave primária) para usar posteriormente ao definir a *cadeia de conexão* para o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c298d-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![criar instância de armazenamento](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="c298d-258">Capítulo 4-Configurando o ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="c298d-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="c298d-259">Para criar e implantar módulos para borda do *Hub IOT*, você precisará dos seguintes componentes instalados em seu computador de desenvolvimento executando o Windows 10:</span><span class="sxs-lookup"><span data-stu-id="c298d-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="c298d-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), ele solicitará que você crie uma conta para ser capaz de baixar.</span><span class="sxs-lookup"><span data-stu-id="c298d-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="c298d-261">[![baixar o Docker para Windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="c298d-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="c298d-262">O Docker requer *Windows 10 pro*, *Enterprise 14393*ou *Windows Server 2016 RTM*para ser executado.</span><span class="sxs-lookup"><span data-stu-id="c298d-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="c298d-263">Se você estiver executando outras versões do Windows 10, poderá tentar instalar o Docker usando a caixa de [ferramentas](https://docs.docker.com/toolbox/toolbox_install_windows/)do Docker.</span><span class="sxs-lookup"><span data-stu-id="c298d-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="c298d-264">[Python 3,6](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="c298d-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="c298d-265">[![baixar o Python 3,6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="c298d-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="c298d-266">[Visual Studio Code (também conhecido como vs Code)](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="c298d-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="c298d-267">[![baixar VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="c298d-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="c298d-268">Depois de instalar o software mencionado acima, será necessário reiniciar o computador.</span><span class="sxs-lookup"><span data-stu-id="c298d-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="c298d-269">Capítulo 5-Configurando o ambiente do Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c298d-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="c298d-270">Agora você pode passar para a configuração de seu dispositivo **que executa o sistema operacional Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="c298d-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="c298d-271">Siga as etapas abaixo para instalar o software necessário, para implantar seus contêineres no seu quadro:</span><span class="sxs-lookup"><span data-stu-id="c298d-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c298d-272">Você sempre deve preceder os comandos de terminal com **sudo** para executar como usuário administrador.</span><span class="sxs-lookup"><span data-stu-id="c298d-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="c298d-273">,</span><span class="sxs-lookup"><span data-stu-id="c298d-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="c298d-274">Abra o **terminal do Ubuntu**e use o seguinte comando para instalar o **Pip**:</span><span class="sxs-lookup"><span data-stu-id="c298d-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [! Dica]<span data-ttu-id="c298d-275"> você pode abrir o *terminal* muito facilmente usando o atalho de teclado: **Ctrl + Alt + T**.</span><span class="sxs-lookup"><span data-stu-id="c298d-275"> You can open *Terminal* very easily through using the keyboard shortcut: **Ctrl + Alt + T**.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="c298d-276">Ao longo deste capítulo, você pode ser solicitado, por *terminal*, por permissão para usar o armazenamento do dispositivo e, para inserir **y/n** (Sim ou não), digite **' y '** e pressione a tecla **Enter** , para aceitar.</span><span class="sxs-lookup"><span data-stu-id="c298d-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="c298d-277">Depois que esse comando for concluído, use o seguinte comando parainstalar a ondulação:</span><span class="sxs-lookup"><span data-stu-id="c298d-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="c298d-278">Depois que o **Pip** e a **ondulação** forem instalados, use o seguinte comando para instalar o **IOT Edge Runtime**, que é necessário para implantar e controlar os módulos no seu quadro:</span><span class="sxs-lookup"><span data-stu-id="c298d-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

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

5. <span data-ttu-id="c298d-279">Neste ponto, você será solicitado a abrir o *arquivo de configuração de tempo de execução*, para inserir a cadeia de conexão do **dispositivo**, que você anotou (no bloco de notas), ao criar o **serviço de Hub IOT** ([na etapa 14, do capítulo 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="c298d-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="c298d-280">Execute a seguinte linha no terminal para abrir esse arquivo:</span><span class="sxs-lookup"><span data-stu-id="c298d-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="c298d-281">O arquivo **config. YAML** será exibido, pronto para você editar:</span><span class="sxs-lookup"><span data-stu-id="c298d-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="c298d-282">Quando esse arquivo é aberto, pode ser um pouco confuso.</span><span class="sxs-lookup"><span data-stu-id="c298d-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="c298d-283">Você será o texto editando esse arquivo, dentro do próprio *terminal* .</span><span class="sxs-lookup"><span data-stu-id="c298d-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="c298d-284">Use as teclas de direção do teclado para rolar para baixo (você precisará rolar uma pequena maneira) para chegar à linha que contém ":</span><span class="sxs-lookup"><span data-stu-id="c298d-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="c298d-285">"ADICIONAR CADEIA DE CONEXÃO DE**DISPOSITIVOAQUI>"\<** .</span><span class="sxs-lookup"><span data-stu-id="c298d-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="c298d-286">Substitua a linha, **incluindo os colchetes**, pela **cadeia de conexão do dispositivo** que você anotou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c298d-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="c298d-287">Com a cadeia de conexão em vigor, no teclado, pressione as teclas **Ctrl-X** para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c298d-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="c298d-288">Ele solicitará que você confirme digitando **Y**. Em seguida, pressione a tecla **Enter** para confirmar.</span><span class="sxs-lookup"><span data-stu-id="c298d-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="c298d-289">Você voltará para o *terminal*normal.</span><span class="sxs-lookup"><span data-stu-id="c298d-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="c298d-290">Depois que todos os comandos forem executados com êxito, você terá instalado o **IOT Edge Runtime**.</span><span class="sxs-lookup"><span data-stu-id="c298d-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="c298d-291">Depois de inicializado, o tempo de execução começará por conta própria toda vez que o dispositivo for ligado e ficará em segundo plano, aguardando que os módulos sejam implantados do **serviço do Hub IOT**.</span><span class="sxs-lookup"><span data-stu-id="c298d-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="c298d-292">Execute a seguinte linha de comando para inicializar o *tempo de execução de IOT Edge*:</span><span class="sxs-lookup"><span data-stu-id="c298d-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="c298d-293">Se você fizer alterações no arquivo. YAML ou na configuração acima, será necessário executar a linha de reinicialização acima novamente, dentro do *terminal*.</span><span class="sxs-lookup"><span data-stu-id="c298d-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="c298d-294">Verifique o status do *tempo de execução do IOT Edge* executando a seguinte linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c298d-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="c298d-295">O tempo de execução deve aparecer com o status **ativo (em execução)** em texto verde.</span><span class="sxs-lookup"><span data-stu-id="c298d-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="c298d-296">Pressione as teclas **Ctrl-C** para sair da página status.</span><span class="sxs-lookup"><span data-stu-id="c298d-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="c298d-297">Você pode verificar se o *tempo de execução de IOT Edge* está extraindo os contêineres corretamente digitando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="c298d-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="c298d-298">Uma lista com dois (2) contêineres deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="c298d-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="c298d-299">Esses são os módulos padrão criados automaticamente pelo serviço de Hub IoT (edgeAgent e edgeHub).</span><span class="sxs-lookup"><span data-stu-id="c298d-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="c298d-300">Depois de criar e implantar seus próprios módulos, eles serão exibidos nessa lista, sob os padrões.</span><span class="sxs-lookup"><span data-stu-id="c298d-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="c298d-301">Capítulo 6-instalar as extensões</span><span class="sxs-lookup"><span data-stu-id="c298d-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c298d-302">Os próximos capítulos (6-9) devem ser executados em seu computador com Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c298d-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="c298d-303">Abra **vs Code**.</span><span class="sxs-lookup"><span data-stu-id="c298d-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="c298d-304">Clique no botão **extensões** (quadrado) na barra à esquerda de vs Code, para abrir o **painel extensões**.</span><span class="sxs-lookup"><span data-stu-id="c298d-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="c298d-305">Procure e instale as seguintes extensões (conforme mostrado na imagem abaixo):</span><span class="sxs-lookup"><span data-stu-id="c298d-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="c298d-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="c298d-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="c298d-307">Kit de ferramentas do Azure IoT</span><span class="sxs-lookup"><span data-stu-id="c298d-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="c298d-308">Docker</span><span class="sxs-lookup"><span data-stu-id="c298d-308">Docker</span></span>   

    ![Criar seu contêiner](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="c298d-310">Depois que as extensões forem instaladas, feche e abra novamente VS Code.</span><span class="sxs-lookup"><span data-stu-id="c298d-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="c298d-311">Com vs Code abrir mais uma vez, navegue para **Exibir** > **terminal integrado**.</span><span class="sxs-lookup"><span data-stu-id="c298d-311">With VS Code open once more, navigate to **View** > **Integrated terminal**.</span></span>

6. <span data-ttu-id="c298d-312">Agora, você instalará o **CookieCutter**.</span><span class="sxs-lookup"><span data-stu-id="c298d-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="c298d-313">No terminal, execute o seguinte comando bash:</span><span class="sxs-lookup"><span data-stu-id="c298d-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! Dica]<span data-ttu-id="c298d-314"> se você tiver problemas com este comando:</span><span class="sxs-lookup"><span data-stu-id="c298d-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="c298d-315">Reinicie VS Code e/ou seu computador.</span><span class="sxs-lookup"><span data-stu-id="c298d-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="c298d-316">Pode ser necessário alternar o terminal de **vs Code** para aquele que você esteve usando para instalar o Python, ou seja, o **PowerShell** (especialmente caso o ambiente do Python já tenha sido instalado em seu computador).</span><span class="sxs-lookup"><span data-stu-id="c298d-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="c298d-317">Com o terminal aberto, você encontrará o menu suspenso no lado direito do terminal.</span><span class="sxs-lookup"><span data-stu-id="c298d-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="c298d-318">![Criar seu contêiner](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="c298d-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="c298d-319">Verifique se o caminho de instalação do **Python** foi adicionado como **variável de ambiente** em seu computador.</span><span class="sxs-lookup"><span data-stu-id="c298d-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="c298d-320">CookieCutter deve fazer parte do mesmo caminho de local.</span><span class="sxs-lookup"><span data-stu-id="c298d-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="c298d-321">Siga este [link para obter mais informações sobre variáveis de ambiente](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span><span class="sxs-lookup"><span data-stu-id="c298d-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="c298d-322">Depois que o **CookieCutter** terminar de instalar, você deverá reiniciar o computador para que o **CookieCutter** seja reconhecido como um comando, no ambiente do sistema.</span><span class="sxs-lookup"><span data-stu-id="c298d-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="c298d-323">Capítulo 7-criar sua solução de contêiner</span><span class="sxs-lookup"><span data-stu-id="c298d-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="c298d-324">Neste ponto, você precisa criar o contêiner, com o módulo, para ser enviado por push para o *registro de contêiner*.</span><span class="sxs-lookup"><span data-stu-id="c298d-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="c298d-325">Depois de enviar o contêiner por push, você usará o serviço de *borda do Hub IOT* para implantá-lo em seu dispositivo, que está executando o *tempo de execução de IOT Edge*.</span><span class="sxs-lookup"><span data-stu-id="c298d-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="c298d-326">Em vs Code, clique em **Exibir** > **paleta de comandos**.</span><span class="sxs-lookup"><span data-stu-id="c298d-326">From VS Code, click **View** > **Command palette**.</span></span>

2. <span data-ttu-id="c298d-327">Na paleta, pesquise e execute **Azure IOT Edge: Nova solução**do IOT Edge.</span><span class="sxs-lookup"><span data-stu-id="c298d-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="c298d-328">Navegue até um local onde você deseja criar sua solução.</span><span class="sxs-lookup"><span data-stu-id="c298d-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="c298d-329">Pressione a tecla **Enter** para aceitar o local.</span><span class="sxs-lookup"><span data-stu-id="c298d-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="c298d-330">Dê um nome à sua solução.</span><span class="sxs-lookup"><span data-stu-id="c298d-330">Give a name to your solution.</span></span> <span data-ttu-id="c298d-331">Pressione a tecla **Enter** para confirmar o nome fornecido.</span><span class="sxs-lookup"><span data-stu-id="c298d-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="c298d-332">Agora, você será solicitado a escolher a estrutura de modelo para sua solução.</span><span class="sxs-lookup"><span data-stu-id="c298d-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="c298d-333">Clique em **módulo python**.</span><span class="sxs-lookup"><span data-stu-id="c298d-333">Click **Python Module**.</span></span> <span data-ttu-id="c298d-334">Pressione a tecla **Enter** para confirmar essa escolha.</span><span class="sxs-lookup"><span data-stu-id="c298d-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="c298d-335">Dê um nome ao seu módulo.</span><span class="sxs-lookup"><span data-stu-id="c298d-335">Give a name to your module.</span></span> <span data-ttu-id="c298d-336">Pressione a tecla **Enter** para confirmar o nome do seu módulo.</span><span class="sxs-lookup"><span data-stu-id="c298d-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="c298d-337">Certifique-se de anotar (com o bloco de notas) do nome do módulo, pois ele será usado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="c298d-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="c298d-338">Você observará que um endereço de *repositório de imagem* do Docker predefinido aparecerá na paleta.</span><span class="sxs-lookup"><span data-stu-id="c298d-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="c298d-339">Ele se parecerá com:</span><span class="sxs-lookup"><span data-stu-id="c298d-339">It will look like:</span></span>

    <span data-ttu-id="c298d-340">**localhost: 5000/-o nome do seu módulo-** .</span><span class="sxs-lookup"><span data-stu-id="c298d-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="c298d-341">Exclua **localhost: 5000**e, em seu lugar, insira o endereço do **servidor de logon** *do registro de contêiner* , que você anotou ao criar o serviço de registro de **contêiner** ([na etapa 8, do capítulo 2](#chapter-2---the-container-registry-service)).</span><span class="sxs-lookup"><span data-stu-id="c298d-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="c298d-342">Pressione a tecla **Enter** para confirmar o endereço.</span><span class="sxs-lookup"><span data-stu-id="c298d-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="c298d-343">Neste ponto, a solução que contém o modelo para seu módulo python será criada e sua estrutura será exibida na **guia explorar**, de vs Code, no lado esquerdo da tela.</span><span class="sxs-lookup"><span data-stu-id="c298d-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="c298d-344">Se a **guia explorar** não estiver aberta, você poderá abri-la clicando no botão superior, na barra à esquerda.</span><span class="sxs-lookup"><span data-stu-id="c298d-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![Criar seu contêiner](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="c298d-346">A última etapa deste capítulo é clicar e abrir o **arquivo. env**, de dentro da **guia explorar**e adicionar o **nome de usuário** e a **senha** *do registro de contêiner* .</span><span class="sxs-lookup"><span data-stu-id="c298d-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="c298d-347">Esse arquivo é ignorado pelo git, mas na criação do contêiner, o definirá as credenciais para acessar o **serviço de registro de contêiner**.</span><span class="sxs-lookup"><span data-stu-id="c298d-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![Criar seu contêiner](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="c298d-349">Capítulo 8-editando sua solução de contêiner</span><span class="sxs-lookup"><span data-stu-id="c298d-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="c298d-350">Agora você vai concluir a solução de contêiner, atualizando os seguintes arquivos:</span><span class="sxs-lookup"><span data-stu-id="c298d-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="c298d-351">script de Python *<span></span>Main. py* .</span><span class="sxs-lookup"><span data-stu-id="c298d-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="c298d-352">*requirements. txt*.</span><span class="sxs-lookup"><span data-stu-id="c298d-352">*requirements.txt*.</span></span>
- <span data-ttu-id="c298d-353">*implantação. Template. JSON*.</span><span class="sxs-lookup"><span data-stu-id="c298d-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="c298d-354">*Dockerfile. AMD64*</span><span class="sxs-lookup"><span data-stu-id="c298d-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="c298d-355">Em seguida, você criará a pasta *imagens* , usada pelo script Python para verificar se há imagens para corresponder ao seu *modelo de visão personalizada*.</span><span class="sxs-lookup"><span data-stu-id="c298d-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="c298d-356">Por fim, você adicionará o arquivo *Labels. txt* , para ajudar a ler seu modelo e o arquivo *Model. PB* , que é o seu modelo.</span><span class="sxs-lookup"><span data-stu-id="c298d-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="c298d-357">Com VS Code aberto, navegue até a pasta do módulo e procure o script chamado **<span></span>Main. py**.</span><span class="sxs-lookup"><span data-stu-id="c298d-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="c298d-358">Clique duas vezes para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="c298d-358">Double-click to open it.</span></span>

2. <span data-ttu-id="c298d-359">Exclua o conteúdo do arquivo e insira o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c298d-359">Delete the content of the file and insert the following code:</span></span>

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

3.  <span data-ttu-id="c298d-360">Abra o arquivo chamado **requirements. txt**e substitua seu conteúdo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="c298d-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="c298d-361">Abra o arquivo chamado **Deployment. Template. JSON**e substitua seu conteúdo seguindo a diretriz abaixo:</span><span class="sxs-lookup"><span data-stu-id="c298d-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="c298d-362">Como você terá sua própria estrutura JSON exclusiva, será necessário editá-la manualmente (em vez de copiar um exemplo).</span><span class="sxs-lookup"><span data-stu-id="c298d-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="c298d-363">Para facilitar, use a imagem abaixo como guia.</span><span class="sxs-lookup"><span data-stu-id="c298d-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="c298d-364">Áreas que terão aparência diferente da sua, mas que **não devem**ser alteradas, serão realçadas como amarelos.</span><span class="sxs-lookup"><span data-stu-id="c298d-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="c298d-365">**As seções que você precisa excluir são um vermelho realçado.**</span><span class="sxs-lookup"><span data-stu-id="c298d-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="c298d-366">Tenha cuidado para excluir os colchetes corretos e também remova as vírgulas.</span><span class="sxs-lookup"><span data-stu-id="c298d-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![Criar seu contêiner](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="c298d-368">O JSON concluído deve se parecer com a imagem a seguir (no entanto, com suas diferenças exclusivas: nome de *usuário/senha/módulo referências*de módulo):</span><span class="sxs-lookup"><span data-stu-id="c298d-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![Criar seu contêiner](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="c298d-370">Abra o arquivo chamado **Dockerfile. AMD64**e substitua seu conteúdo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="c298d-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

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

6.  <span data-ttu-id="c298d-371">Clique com o botão direito do mouse na pasta abaixo de **módulos** (ele terá o nome fornecido anteriormente; no exemplo mais abaixo, ele é chamado de *pythonmodule*) e clique em **nova pasta**.</span><span class="sxs-lookup"><span data-stu-id="c298d-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="c298d-372">Nomeie as **imagens**da pasta.</span><span class="sxs-lookup"><span data-stu-id="c298d-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="c298d-373">Dentro da pasta, adicione algumas imagens que contêm o mouse ou o teclado.</span><span class="sxs-lookup"><span data-stu-id="c298d-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="c298d-374">Essas serão as imagens que serão analisadas pelo modelo Tensorflow.</span><span class="sxs-lookup"><span data-stu-id="c298d-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="c298d-375">Se você estiver usando seu próprio modelo, será necessário alterar isso para refletir seus próprios dados de modelos.</span><span class="sxs-lookup"><span data-stu-id="c298d-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="c298d-376">Agora, você precisará recuperar os arquivos **Labels. txt** e **Model. PB** da pasta modelo, que você baixou anteriormente (ou criado a partir de seu próprio **serviço de visão personalizada**), no [capítulo 1](#chapter-1---retrieve-the-custom-vision-model).</span><span class="sxs-lookup"><span data-stu-id="c298d-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="c298d-377">Quando você tiver os arquivos, coloque-os dentro de sua solução, juntamente com os outros arquivos.</span><span class="sxs-lookup"><span data-stu-id="c298d-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="c298d-378">O resultado final deve ser semelhante à imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="c298d-378">The final result should look like the image below:</span></span>

    ![Criar seu contêiner](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="c298d-380">Capítulo 9-empacotar a solução como um contêiner</span><span class="sxs-lookup"><span data-stu-id="c298d-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="c298d-381">Agora você está pronto para "empacotar" seus arquivos como um contêiner e enviá-los por push para o **registro de contêiner do Azure**.</span><span class="sxs-lookup"><span data-stu-id="c298d-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="c298d-382">Em vs Code, abra o *terminal integrado* (**Exibir** > **terminal integrado** ou **Ctrl**+ **\`** ) e use a linha a seguir para fazer logon no Docker (substitua os valores do comando com as credenciais do seu **ACR (registro de contêiner do Azure)** ):</span><span class="sxs-lookup"><span data-stu-id="c298d-382">Within VS Code, open the *Integrated Terminal* (**View** > **Integrated Terminal** or **Ctrl**+**\`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="c298d-383">Clique com o botão direito do mouse no arquivo **Deployment. Template. JSON**e clique em **Compilar IOT Edge solução**.</span><span class="sxs-lookup"><span data-stu-id="c298d-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="c298d-384">Esse processo de compilação leva algum tempo (dependendo do seu dispositivo), portanto, esteja preparado para aguardar.</span><span class="sxs-lookup"><span data-stu-id="c298d-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="c298d-385">Após a conclusão do processo de compilação, um arquivo **Deployment. JSON** será criado dentro de uma nova pasta chamada **config**.</span><span class="sxs-lookup"><span data-stu-id="c298d-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![criar implantação](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="c298d-387">Abra a **paleta de comandos** novamente e pesquise pelo **Azure:** Entre.</span><span class="sxs-lookup"><span data-stu-id="c298d-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="c298d-388">Siga os prompts usando suas credenciais de conta do Azure; VS Code fornecerá uma opção para *copiar e abrir*, que copiará o código do dispositivo que você precisará em breve e abrirá o navegador da Web padrão.</span><span class="sxs-lookup"><span data-stu-id="c298d-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="c298d-389">Quando solicitado, Cole o código do dispositivo para autenticar seu computador.</span><span class="sxs-lookup"><span data-stu-id="c298d-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![copiar e abrir](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="c298d-391">Depois de conectado, você observará, no lado inferior do painel *explorar* , uma nova seção chamada **dispositivos do Hub IOT do Azure**.</span><span class="sxs-lookup"><span data-stu-id="c298d-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="c298d-392">Clique nesta seção para expandi-la.</span><span class="sxs-lookup"><span data-stu-id="c298d-392">Click this section to expand it.</span></span>

    ![dispositivo do Edge](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="c298d-394">Se o dispositivo não estiver aqui, será necessário clicar com o botão direito do mouse em *dispositivos do Hub IOT do Azure*e clicar em **Definir cadeia de conexão do Hub IOT**.</span><span class="sxs-lookup"><span data-stu-id="c298d-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="c298d-395">Em seguida, você verá que a **paleta de comandos** (na parte superior de vs Code) solicitará que você insira sua cadeia de *conexão*.</span><span class="sxs-lookup"><span data-stu-id="c298d-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="c298d-396">Essa é a *cadeia de conexão* que você anotou no final do [capítulo 3](#chapter-3---the-iot-hub-service).</span><span class="sxs-lookup"><span data-stu-id="c298d-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="c298d-397">Pressione a tecla **Enter** , depois de ter copiado a cadeia de caracteres no.</span><span class="sxs-lookup"><span data-stu-id="c298d-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="c298d-398">Seu dispositivo deve ser carregado e exibido.</span><span class="sxs-lookup"><span data-stu-id="c298d-398">Your device should load, and appear.</span></span> <span data-ttu-id="c298d-399">Clique com o botão direito do mouse no nome do dispositivo e clique em **criar implantação para um único dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="c298d-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![criar implantação](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="c298d-401">Você obterá um prompt do *Explorador de arquivos* , onde poderá navegar para a pasta **config** e, em seguida, selecionar o arquivo **Deployment. JSON** .</span><span class="sxs-lookup"><span data-stu-id="c298d-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="c298d-402">Com esse arquivo selecionado, clique no botão **selecionar manifesto de implantação de borda** .</span><span class="sxs-lookup"><span data-stu-id="c298d-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![criar implantação](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="c298d-404">Neste ponto, você forneceu ao seu **serviço de Hub IOT** o manifesto para implantar seu contêiner, como um módulo, do registro de **contêiner do Azure**, implantando-o efetivamente em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c298d-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="c298d-405">Para exibir as mensagens enviadas do seu dispositivo para o Hub IoT, clique com o botão direito do mouse novamente no nome do dispositivo na seção **dispositivos do Hub IOT do Azure** , no painel **Gerenciador** e clique em **Iniciar Monitoramento de mensagem D2C**.</span><span class="sxs-lookup"><span data-stu-id="c298d-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="c298d-406">As mensagens enviadas do seu dispositivo devem aparecer no terminal do VS.</span><span class="sxs-lookup"><span data-stu-id="c298d-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="c298d-407">Seja paciente, pois isso pode levar algum tempo.</span><span class="sxs-lookup"><span data-stu-id="c298d-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="c298d-408">Consulte o próximo capítulo para depuração e verificando se a implantação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c298d-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="c298d-409">Este módulo agora fará a iteração entre as imagens na pasta **imagens** e as analisará, com cada iteração.</span><span class="sxs-lookup"><span data-stu-id="c298d-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="c298d-410">Isso é, obviamente, apenas uma demonstração de como obter o modelo básico de aprendizado de máquina para trabalhar em um ambiente de dispositivo IoT Edge.</span><span class="sxs-lookup"><span data-stu-id="c298d-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="c298d-411">Para expandir a funcionalidade deste exemplo, você pode proceder de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="c298d-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="c298d-412">Uma maneira pode ser incluir algum código no contêiner, que captura fotos de uma webcam conectada ao dispositivo e salva as imagens na pasta imagens.</span><span class="sxs-lookup"><span data-stu-id="c298d-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="c298d-413">Outra maneira seria copiar as imagens do dispositivo IoT para o contêiner.</span><span class="sxs-lookup"><span data-stu-id="c298d-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="c298d-414">Uma maneira prática de fazer isso é executar o seguinte comando no terminal do dispositivo IoT (talvez um aplicativo pequeno possa fazer o trabalho, se desejar automatizar o processo).</span><span class="sxs-lookup"><span data-stu-id="c298d-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="c298d-415">Você pode testar esse comando executando-o manualmente do local da pasta onde os arquivos são armazenados:</span><span class="sxs-lookup"><span data-stu-id="c298d-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="c298d-416">Capítulo 10-Depurando o tempo de execução de IoT Edge</span><span class="sxs-lookup"><span data-stu-id="c298d-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="c298d-417">Veja a seguir uma lista de linhas de comando e dicas para ajudá-lo a monitorar e depurar a atividade de mensagens do *tempo de execução de IOT Edge*, do seu **dispositivo Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="c298d-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="c298d-418">Verifique o status do *tempo de execução do IOT Edge* executando a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="c298d-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="c298d-419">Lembre-se de pressionar **Ctrl + C**para concluir a exibição do status.</span><span class="sxs-lookup"><span data-stu-id="c298d-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="c298d-420">Liste os contêineres que estão implantados no momento.</span><span class="sxs-lookup"><span data-stu-id="c298d-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="c298d-421">Se o *serviço Hub IOT* implantou os contêineres com êxito, eles serão exibidos executando a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="c298d-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="c298d-422">Ou</span><span class="sxs-lookup"><span data-stu-id="c298d-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="c298d-423">O acima é uma boa maneira de verificar se o módulo foi implantado com êxito, como aparecerá na lista; caso contrário, você verá **apenas** o *EdgeHub* e o *edgeAgent*.</span><span class="sxs-lookup"><span data-stu-id="c298d-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="c298d-424">Para exibir os logs de código de um contêiner, execute a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="c298d-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="c298d-425">**Comandos úteis para gerenciar o tempo de execução de IoT Edge:**</span><span class="sxs-lookup"><span data-stu-id="c298d-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="c298d-426">Para excluir todos os contêineres no host:</span><span class="sxs-lookup"><span data-stu-id="c298d-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="c298d-427">Para interromper o *tempo de execução de IOT Edge*:</span><span class="sxs-lookup"><span data-stu-id="c298d-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="c298d-428">Capítulo 11 – criar serviço de tabela</span><span class="sxs-lookup"><span data-stu-id="c298d-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="c298d-429">Navegue de volta para o portal do Azure, no qual você criará um serviço de tabelas do Azure, criando um recurso de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="c298d-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="c298d-430">Se ainda não estiver conectado, faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c298d-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="c298d-431">Depois de conectado, clique em **criar um recurso**, no canto superior esquerdo, procure a conta de **armazenamento**e pressione a tecla **Enter** para iniciar a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c298d-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="c298d-432">Depois de ter aparecido, clique em **conta de armazenamento-BLOB, arquivo, tabela, fila** na lista.</span><span class="sxs-lookup"><span data-stu-id="c298d-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Pesquisar conta de armazenamento](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="c298d-434">A nova página fornecerá uma descrição do serviço de **conta de armazenamento** .</span><span class="sxs-lookup"><span data-stu-id="c298d-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="c298d-435">Na parte inferior esquerda desse prompt, clique no botão **criar** para criar uma instância desse serviço.</span><span class="sxs-lookup"><span data-stu-id="c298d-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![criar instância de armazenamento](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="c298d-437">Depois de clicar em **criar**, um painel será exibido:</span><span class="sxs-lookup"><span data-stu-id="c298d-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="c298d-438">Insira o **nome** desejado para esta instância de serviço (*deve estar em letras minúsculas*).</span><span class="sxs-lookup"><span data-stu-id="c298d-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="c298d-439">Para **modelo de implantação**, clique em **Gerenciador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="c298d-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="c298d-440">Para **tipo de conta**, usando o menu suspenso, clique em **armazenamento (uso geral v1)** .</span><span class="sxs-lookup"><span data-stu-id="c298d-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="c298d-441">Clique em um **local**apropriado.</span><span class="sxs-lookup"><span data-stu-id="c298d-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="c298d-442">Para o menu suspenso **replicação** , clique em **armazenamento com redundância geográfica e acesso de leitura (ra-grs)** .</span><span class="sxs-lookup"><span data-stu-id="c298d-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="c298d-443">Para **desempenho**, clique em **padrão**.</span><span class="sxs-lookup"><span data-stu-id="c298d-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="c298d-444">Na seção **transferência segura necessária** , clique em **desabilitado**.</span><span class="sxs-lookup"><span data-stu-id="c298d-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="c298d-445">No menu suspenso **assinatura** , clique em uma assinatura apropriada.</span><span class="sxs-lookup"><span data-stu-id="c298d-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="c298d-446">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="c298d-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c298d-447">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="c298d-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="c298d-448">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="c298d-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="c298d-449">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c298d-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="c298d-450">Deixe as **redes virtuais** como **desabilitadas**, se essa for uma opção para você.</span><span class="sxs-lookup"><span data-stu-id="c298d-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="c298d-451">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-451">Click **Create**.</span></span>

        ![preencher detalhes do armazenamento](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="c298d-453">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="c298d-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="c298d-454">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="c298d-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="c298d-455">Clique nas notificações para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="c298d-455">Click on the notifications to explore your new Service instance.</span></span>

    ![Nova notificação de armazenamento](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="c298d-457">Clique no botão **ir para recurso** na notificação e você será levado para a página de visão geral da nova instância do serviço de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="c298d-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![ir para o recurso](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="c298d-459">Na página Visão geral, no lado direito, clique em **tabelas**.</span><span class="sxs-lookup"><span data-stu-id="c298d-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![tabelas](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="c298d-461">O painel à direita será alterado para mostrar as informações do **serviço tabela** , onde você precisa adicionar uma nova tabela.</span><span class="sxs-lookup"><span data-stu-id="c298d-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="c298d-462">Para fazer isso, clique no botão **+ tabela** no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="c298d-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![Abrir tabelas](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="c298d-464">Uma nova página será mostrada, onde você precisa inserir um nome de **tabela**.</span><span class="sxs-lookup"><span data-stu-id="c298d-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="c298d-465">Esse é o nome que você usará para se referir aos dados em seu aplicativo em capítulos posteriores (criando Aplicativo de funções e Power BI).</span><span class="sxs-lookup"><span data-stu-id="c298d-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="c298d-466">Insira **IoTMessages** como o nome (você pode escolher o seu próprio, apenas lembre-se dele quando usado mais tarde neste documento) e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c298d-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="c298d-467">Depois que a nova tabela tiver sido criada, você poderá vê-la na página de **serviço tabela** (na parte inferior).</span><span class="sxs-lookup"><span data-stu-id="c298d-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![nova tabela criada](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="c298d-469">Agora, clique em **chaves de acesso** e faça uma cópia do nome e da **chave** da conta de **armazenamento** (usando o bloco de notas). você usará esses valores posteriormente neste curso, ao criar o **aplicativo de funções do Azure**.</span><span class="sxs-lookup"><span data-stu-id="c298d-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![nova tabela criada](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="c298d-471">Usando o painel à esquerda novamente, role até a seção *serviço tabela* e clique em **tabelas** (ou **procure tabelas**, em portais mais recentes) e faça uma cópia da **URL da tabela** (usando o bloco de notas).</span><span class="sxs-lookup"><span data-stu-id="c298d-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="c298d-472">Você usará esse valor posteriormente neste curso, ao vincular sua tabela ao seu aplicativo **Power bi** .</span><span class="sxs-lookup"><span data-stu-id="c298d-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![nova tabela criada](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="c298d-474">Capítulo 12 – concluindo a tabela do Azure</span><span class="sxs-lookup"><span data-stu-id="c298d-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="c298d-475">Agora que a conta de armazenamento do **serviço de tabela** foi configurada, é hora de adicionar dados a ela, que será usada para armazenar e recuperar informações.</span><span class="sxs-lookup"><span data-stu-id="c298d-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="c298d-476">A edição das tabelas pode ser feita por meio do **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c298d-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="c298d-477">Abra o **Visual Studio** (**não** Visual Studio Code).</span><span class="sxs-lookup"><span data-stu-id="c298d-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="c298d-478">No menu, clique em **Exibir** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="c298d-478">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![abrir o Cloud Explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="c298d-480">O **Cloud Explorer** será aberto como um item encaixado (seja paciente, pois o carregamento pode levar tempo).</span><span class="sxs-lookup"><span data-stu-id="c298d-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="c298d-481">Se a assinatura que você usou para criar suas *contas de armazenamento* não estiver visível, verifique se você tem:</span><span class="sxs-lookup"><span data-stu-id="c298d-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="c298d-482">Conectado à mesma conta que você usou para o portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="c298d-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="c298d-483">Selecione sua assinatura na página de gerenciamento de conta (talvez seja necessário aplicar um filtro de suas configurações de conta):</span><span class="sxs-lookup"><span data-stu-id="c298d-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![Localizar assinatura](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="c298d-485">Os serviços de nuvem do Azure serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="c298d-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="c298d-486">Localize **contas de armazenamento** e clique na seta à esquerda dela para expandir suas contas.</span><span class="sxs-lookup"><span data-stu-id="c298d-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![abrir contas de armazenamento](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="c298d-488">Uma vez expandido, sua **conta de armazenamento** recém-criada deve estar disponível.</span><span class="sxs-lookup"><span data-stu-id="c298d-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="c298d-489">Clique na seta à esquerda do armazenamento e, depois de expandida, localize as **tabelas** e clique na seta ao lado dela para revelar a **tabela** que você criou no último capítulo.</span><span class="sxs-lookup"><span data-stu-id="c298d-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="c298d-490">Clique duas vezes em sua **tabela**.</span><span class="sxs-lookup"><span data-stu-id="c298d-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="c298d-491">Sua tabela será aberta no centro da janela do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c298d-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="c298d-492">Clique no ícone de tabela com **+** o (mais) nele.</span><span class="sxs-lookup"><span data-stu-id="c298d-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![Adicionar nova tabela](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="c298d-494">Uma janela será exibida solicitando que você *adicione a entidade*.</span><span class="sxs-lookup"><span data-stu-id="c298d-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="c298d-495">Você criará apenas uma entidade, embora ela terá três propriedades.</span><span class="sxs-lookup"><span data-stu-id="c298d-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="c298d-496">Você observará que *PartitionKey* e *RowKey* já foram fornecidos, pois eles são usados pela tabela para localizar seus dados.</span><span class="sxs-lookup"><span data-stu-id="c298d-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![partição e chave de linha](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="c298d-498">Atualize os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="c298d-498">Update the following values:</span></span>

    - <span data-ttu-id="c298d-499">Nome: **PartitionKey**, valor: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="c298d-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="c298d-500">Nome: **RowKey**, valor: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="c298d-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="c298d-501">Em seguida, clique em **Adicionar Propriedade** (na parte inferior esquerda da janela *Adicionar entidade* ) e adicione a seguinte propriedade:</span><span class="sxs-lookup"><span data-stu-id="c298d-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="c298d-502">**MessageContent**, como uma *cadeia de caracteres*, deixe o valor vazio.</span><span class="sxs-lookup"><span data-stu-id="c298d-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="c298d-503">Sua tabela deve corresponder à que está na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="c298d-503">Your table should match the one in the image below:</span></span>

    ![Adicionar valores corretos](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="c298d-505">O motivo pelo qual a entidade tem o número 1 na chave de linha, é porque você talvez queira adicionar mais mensagens, caso deseje fazer experiências com este curso.</span><span class="sxs-lookup"><span data-stu-id="c298d-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="c298d-506">Clique em **OK** quando terminar.</span><span class="sxs-lookup"><span data-stu-id="c298d-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="c298d-507">Sua tabela agora está pronta para ser usada.</span><span class="sxs-lookup"><span data-stu-id="c298d-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="c298d-508">Capítulo 13-criar uma Aplicativo de funções do Azure</span><span class="sxs-lookup"><span data-stu-id="c298d-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="c298d-509">Agora é hora de criar uma *aplicativo de funções do Azure*, que será chamada pelo serviço de *Hub IOT* para armazenar as mensagens de dispositivo *IOT Edge* no serviço **tabela** , que você criou no capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="c298d-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="c298d-510">Primeiro, você precisa criar um arquivo que permitirá que o Azure function carregue as bibliotecas necessárias.</span><span class="sxs-lookup"><span data-stu-id="c298d-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="c298d-511">Abra o **bloco de notas** (pressione a *tecla Windows*e digite *notepad*).</span><span class="sxs-lookup"><span data-stu-id="c298d-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![abrir bloco de notas](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="c298d-513">Com o bloco de notas aberto, insira a estrutura JSON abaixo dele.</span><span class="sxs-lookup"><span data-stu-id="c298d-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="c298d-514">Depois de fazer isso, salve-o em sua área de trabalho como **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="c298d-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="c298d-515">Esse arquivo define as bibliotecas que sua função usará.</span><span class="sxs-lookup"><span data-stu-id="c298d-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="c298d-516">Se você usou o NuGet, ele parecerá familiar.</span><span class="sxs-lookup"><span data-stu-id="c298d-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="c298d-517">É importante que a nomenclatura esteja correta; Verifique se ele **não tem uma extensão de arquivo. txt** .</span><span class="sxs-lookup"><span data-stu-id="c298d-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="c298d-518">Consulte abaixo para obter referência:</span><span class="sxs-lookup"><span data-stu-id="c298d-518">See below for reference:</span></span>
    >
    > ![Salvar JSON](images/AzureLabs-Lab313-52.png)

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

3.  <span data-ttu-id="c298d-520">Faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c298d-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="c298d-521">Depois de fazer logon, clique em **criar um recurso** no canto superior esquerdo e procure **aplicativo de funções**e pressione a tecla **Enter** para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="c298d-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="c298d-522">Clique em *aplicativo de funções* nos resultados para abrir um novo painel.</span><span class="sxs-lookup"><span data-stu-id="c298d-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![Pesquisar o aplicativo de funções](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="c298d-524">O novo painel fornecerá uma descrição do serviço de **aplicativo de funções** .</span><span class="sxs-lookup"><span data-stu-id="c298d-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="c298d-525">Na parte inferior esquerda deste painel, clique no botão **criar** para criar uma associação com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="c298d-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![instância do aplicativo de funções](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="c298d-527">Depois de clicar em **criar**, preencha o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c298d-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="c298d-528">Para **nome do aplicativo**, insira o nome desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="c298d-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="c298d-529">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="c298d-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="c298d-530">Selecione o tipo de preço apropriado para você, se esta for a primeira vez que criar um **serviço de aplicativo de funções**, uma camada gratuita deverá estar disponível para você.</span><span class="sxs-lookup"><span data-stu-id="c298d-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="c298d-531">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="c298d-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c298d-532">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="c298d-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="c298d-533">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="c298d-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="c298d-534">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c298d-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="c298d-535">Para o **sistema operacional**, clique em Windows, pois essa é a plataforma pretendida.</span><span class="sxs-lookup"><span data-stu-id="c298d-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="c298d-536">Selecione um **plano de hospedagem** (este tutorial está usando um **plano de consumo**.</span><span class="sxs-lookup"><span data-stu-id="c298d-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="c298d-537">Selecione um **local** (escolha o mesmo local do armazenamento que você criou na etapa anterior)</span><span class="sxs-lookup"><span data-stu-id="c298d-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="c298d-538">Para a seção de **armazenamento** , **você deve selecionar o serviço de armazenamento criado na etapa anterior**.</span><span class="sxs-lookup"><span data-stu-id="c298d-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="c298d-539">Você não precisará de *Application insights* neste aplicativo, portanto, fique à vontade para deixá-lo **desativado**.</span><span class="sxs-lookup"><span data-stu-id="c298d-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="c298d-540">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-540">Click **Create**.</span></span>

        ![criar nova instância](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="c298d-542">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="c298d-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="c298d-543">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="c298d-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Nova notificação](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="c298d-545">Clique na notificação, depois que a implantação for bem-sucedida (concluída).</span><span class="sxs-lookup"><span data-stu-id="c298d-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="c298d-546">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="c298d-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![ir para o recurso](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="c298d-548">No lado esquerdo do painel novo, clique no **+** ícone (mais) ao lado de *funções*, para criar uma nova função.</span><span class="sxs-lookup"><span data-stu-id="c298d-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![Adicionar nova função](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="c298d-550">No painel central, a janela de criação da **função** será exibida.</span><span class="sxs-lookup"><span data-stu-id="c298d-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="c298d-551">Role para baixo e clique em **função personalizada**.</span><span class="sxs-lookup"><span data-stu-id="c298d-551">Scroll down further, and click on **Custom function**.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="c298d-553">Role para baixo na próxima página, até encontrar o **Hub IOT (Hub de eventos)** e clique nele.</span><span class="sxs-lookup"><span data-stu-id="c298d-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="c298d-555">Na folha **Hub IOT (Hub de eventos)** , defina o **idioma** como **C#** e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="c298d-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="c298d-557">Na janela que será exibida, verifique se **Hub IOT** está selecionado e se o nome do campo *Hub IOT* corresponde ao nome do *serviço do Hub IOT* que você criou anteriormente ([na etapa 8, do capítulo 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="c298d-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="c298d-558">Em seguida, clique no botão **selecionar** .</span><span class="sxs-lookup"><span data-stu-id="c298d-558">Then click the **Select** button.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="c298d-560">De volta à folha **Hub IOT (Hub de eventos)** , clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="c298d-562">Você será redirecionado para o editor de funções.</span><span class="sxs-lookup"><span data-stu-id="c298d-562">You will be redirected to the function editor.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="c298d-564">Exclua todo o código e substitua-o pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="c298d-564">Delete all the code in it and replace it with the following:</span></span>

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

19. <span data-ttu-id="c298d-565">Altere as seguintes variáveis, para que elas correspondam aos valores apropriados (**tabela** e valores de **armazenamento** , da [etapa 11 e 13, respectivamente, do capítulo 11](#chapter-11---create-table-service)), que você encontrará em sua **conta de armazenamento**:</span><span class="sxs-lookup"><span data-stu-id="c298d-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="c298d-566">**TableName**, com o nome da sua **tabela** localizado em sua **conta de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="c298d-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="c298d-567">**tableURL**, com a URL da sua **tabela** localizada em sua **conta de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="c298d-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="c298d-568">**storageAccountName**, com o nome do valor correspondente ao nome do seu nome de **conta de armazenamento** .</span><span class="sxs-lookup"><span data-stu-id="c298d-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="c298d-569">**storageAccountKey**, com a chave que você obteve no serviço de armazenamento que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c298d-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="c298d-571">Com o código em vigor, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="c298d-572">Em seguida, clique **\<** no ícone (seta), no lado direito da página.</span><span class="sxs-lookup"><span data-stu-id="c298d-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="c298d-574">Um painel será deslizado da direita.</span><span class="sxs-lookup"><span data-stu-id="c298d-574">A panel will slide in from the right.</span></span> <span data-ttu-id="c298d-575">Nesse painel, clique em **carregar**e um *navegador de arquivos* será exibido.</span><span class="sxs-lookup"><span data-stu-id="c298d-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="c298d-576">Navegue até e clique no arquivo **Project. JSON** , que você criou anteriormente no **bloco de notas** e, em seguida, clique no botão **abrir** .</span><span class="sxs-lookup"><span data-stu-id="c298d-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="c298d-577">Esse arquivo define as bibliotecas que sua função usará.</span><span class="sxs-lookup"><span data-stu-id="c298d-577">This file defines the libraries that your function will use.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="c298d-579">Quando o arquivo for carregado, ele será exibido no painel à direita.</span><span class="sxs-lookup"><span data-stu-id="c298d-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="c298d-580">Clicar nele irá abri-lo no editor de **funções** .</span><span class="sxs-lookup"><span data-stu-id="c298d-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="c298d-581">Ele deve ser **exatamente** o mesmo que a próxima imagem.</span><span class="sxs-lookup"><span data-stu-id="c298d-581">It must look **exactly** the same as the next image.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="c298d-583">Neste ponto, seria bom testar a capacidade da sua função de armazenar a mensagem em sua *tabela*.</span><span class="sxs-lookup"><span data-stu-id="c298d-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="c298d-584">No canto superior direito da janela, clique em **testar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-584">On the top right side of the window, click on **Test**.</span></span>

    ![função personalizada](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="c298d-586">Insira uma mensagem no **corpo da solicitação**, conforme mostrado na imagem acima, e clique em **executar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="c298d-587">A função será executada, exibindo o status do resultado (você notará o **status verde 202 aceito**, acima da janela de *saída* , o que significa que ele foi uma chamada bem-sucedida):</span><span class="sxs-lookup"><span data-stu-id="c298d-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![resultado da saída](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="c298d-589">Capítulo 14-exibir mensagens ativas</span><span class="sxs-lookup"><span data-stu-id="c298d-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="c298d-590">Se agora você abrir o Visual Studio (**não** Visual Studio Code), poderá visualizar o resultado da mensagem de teste, pois ele será armazenado na área da cadeia de caracteres *MessageContent* .</span><span class="sxs-lookup"><span data-stu-id="c298d-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![função personalizada](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="c298d-592">Com o serviço tabela e Aplicativo de funções em vigor, suas mensagens do dispositivo Ubuntu aparecerão na sua tabela *IoTMessages* .</span><span class="sxs-lookup"><span data-stu-id="c298d-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="c298d-593">Se ainda não estiver em execução, inicie o dispositivo novamente e você poderá ver as mensagens de resultado do seu dispositivo, e módulo, em sua tabela, usando o Visual Studio *Cloud Explorer*.</span><span class="sxs-lookup"><span data-stu-id="c298d-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![Visualizar dados](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="c298d-595">Capítulo 15-instalação do Power BI</span><span class="sxs-lookup"><span data-stu-id="c298d-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="c298d-596">Para visualizar os dados de seu dispositivo IOT, você irá configurar **Power bi** (versão da área de trabalho) para coletar os dados do serviço *tabela* que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="c298d-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="c298d-597">A versão do *HoloLens* do Power bi usará esses dados para visualizar o resultado.</span><span class="sxs-lookup"><span data-stu-id="c298d-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="c298d-598">Abra o Microsoft Store no Windows 10 e procure **Power bi desktop**.</span><span class="sxs-lookup"><span data-stu-id="c298d-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="c298d-600">Baixe o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c298d-600">Download the application.</span></span> <span data-ttu-id="c298d-601">Depois de concluir o download, abra-o.</span><span class="sxs-lookup"><span data-stu-id="c298d-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="c298d-602">Faça logon no *Power bi* com sua **conta do Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="c298d-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="c298d-603">Você pode ser redirecionado para um navegador, para se inscrever.</span><span class="sxs-lookup"><span data-stu-id="c298d-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="c298d-604">Depois de se inscrever, volte para o aplicativo Power BI e entre novamente.</span><span class="sxs-lookup"><span data-stu-id="c298d-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="c298d-605">Clique em **obter dados** e, em seguida, clique em **mais..** ..</span><span class="sxs-lookup"><span data-stu-id="c298d-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="c298d-607">Clique em **Azure**, **armazenamento de tabelas do Azure**e, em seguida, clique em **conectar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="c298d-609">Você será solicitado a inserir a URL da **tabela** que você coletou anteriormente ([na etapa 13 do capítulo 11](#chapter-11---create-table-service)), ao criar o serviço tabela.</span><span class="sxs-lookup"><span data-stu-id="c298d-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="c298d-610">Depois de inserir a URL, exclua a parte do caminho referente à tabela "subpasta" (que foi IoTMessages, neste curso).</span><span class="sxs-lookup"><span data-stu-id="c298d-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="c298d-611">O resultado final deve ser exibido na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="c298d-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="c298d-612">Em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c298d-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="c298d-614">Você será solicitado a inserir a chave de **armazenamento** que anotou ([na etapa 11 do capítulo 11](#chapter-11---create-table-service)) antes de criar o armazenamento de tabela.</span><span class="sxs-lookup"><span data-stu-id="c298d-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="c298d-615">Em seguida, clique em **conectar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="c298d-617">Um **painel de navegador** será exibido, marque a caixa ao lado de sua tabela e clique em **carregar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="c298d-619">Sua tabela agora foi carregada em Power BI, mas ela requer uma consulta para exibir os valores nela.</span><span class="sxs-lookup"><span data-stu-id="c298d-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="c298d-620">Para fazer isso, clique com o botão direito do mouse no nome da tabela localizado no **painel campos** , no lado direito da tela.</span><span class="sxs-lookup"><span data-stu-id="c298d-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="c298d-621">Em seguida, clique em **Editar consulta**.</span><span class="sxs-lookup"><span data-stu-id="c298d-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="c298d-623">Um **Editor de Power Query** será aberto como uma nova janela, exibindo a tabela.</span><span class="sxs-lookup"><span data-stu-id="c298d-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="c298d-624">Clique no **registro** do Word na coluna *conteúdo* da tabela para visualizar o conteúdo armazenado.</span><span class="sxs-lookup"><span data-stu-id="c298d-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="c298d-626">Clique em na **tabela**, na parte superior esquerda da janela.</span><span class="sxs-lookup"><span data-stu-id="c298d-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="c298d-628">Clique em **fechar & aplicar**.</span><span class="sxs-lookup"><span data-stu-id="c298d-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="c298d-630">Depois de terminar de carregar a consulta, no **painel campos**, no lado direito da tela, marque as caixas correspondentes ao **nome** e ao **valor**dos parâmetros para visualizar o conteúdo da coluna **MessageContent** .</span><span class="sxs-lookup"><span data-stu-id="c298d-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="c298d-632">Clique no **ícone de disco azul** na parte superior esquerda da janela para salvar seu trabalho em uma pasta de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="c298d-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="c298d-634">Agora você pode clicar no botão Publicar para carregar sua tabela em seu espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c298d-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="c298d-635">Quando solicitado, clique em **meu espaço de trabalho** e clique em *selecionar*.</span><span class="sxs-lookup"><span data-stu-id="c298d-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="c298d-636">Aguarde até que ele exiba o resultado bem-sucedido do envio.</span><span class="sxs-lookup"><span data-stu-id="c298d-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="c298d-639">O capítulo a seguir é específico do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c298d-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="c298d-640">O Power BI atualmente não é disponíveis como um aplicativo de imersão, no entanto, você pode executar a versão da área de trabalho no portal do Windows Mixed Reality (também conhecido como Cliff House), por meio do aplicativo de desktop.</span><span class="sxs-lookup"><span data-stu-id="c298d-640">Power BI is not currently availble as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="c298d-641">Capítulo 16-exibir dados de Power BI no HoloLens</span><span class="sxs-lookup"><span data-stu-id="c298d-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="c298d-642">No seu HoloLens, faça logon no **Microsoft Store**, tocando em seu ícone na lista de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c298d-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="c298d-644">Pesquise e baixe o aplicativo **Power bi** .</span><span class="sxs-lookup"><span data-stu-id="c298d-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="c298d-646">Inicie o **Power bi** na sua lista de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c298d-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="c298d-647">**Power bi** pode solicitar que você faça logon na sua **conta do Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="c298d-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="c298d-648">Uma vez dentro do aplicativo, o espaço de trabalho deve ser exibido por padrão, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="c298d-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="c298d-649">Se isso não acontecer, basta clicar no ícone do espaço de trabalho no lado esquerdo da janela.</span><span class="sxs-lookup"><span data-stu-id="c298d-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="c298d-651">Seu aplicativo de Hub IoT foi concluído</span><span class="sxs-lookup"><span data-stu-id="c298d-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="c298d-652">Parabéns, você criou com êxito um serviço de Hub IoT, com um dispositivo de borda de máquina virtual simulado.</span><span class="sxs-lookup"><span data-stu-id="c298d-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="c298d-653">Seu dispositivo pode comunicar os resultados de um modelo de aprendizado de máquina para um serviço tabela do Azure, facilitado por um Aplicativo de funções do Azure, que é lido no Power BI e visualizado em um Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c298d-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c298d-655">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="c298d-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c298d-656">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="c298d-656">Exercise 1</span></span>

<span data-ttu-id="c298d-657">Expanda a estrutura de mensagens armazenada na tabela e exiba-a como um grafo.</span><span class="sxs-lookup"><span data-stu-id="c298d-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="c298d-658">Talvez você queira coletar mais dados e armazená-los na mesma tabela, para serem exibidos posteriormente.</span><span class="sxs-lookup"><span data-stu-id="c298d-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c298d-659">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="c298d-659">Exercise 2</span></span>

<span data-ttu-id="c298d-660">Crie um módulo adicional de "captura de câmera" para ser implantado na placa IoT, para que ele possa capturar imagens por meio da câmera a ser analisada.</span><span class="sxs-lookup"><span data-stu-id="c298d-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
