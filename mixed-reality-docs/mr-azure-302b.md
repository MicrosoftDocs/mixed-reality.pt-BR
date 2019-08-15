---
title: Sr e Azure 302b-visão personalizada
description: Conclua este curso para aprender a treinar um modelo de aprendizado de máquina e, em seguida, use o modelo treinado para reconhecer objetos semelhantes em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, visão personalizada, hololens, imersão, VR
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63553910"
---
>[!NOTE]
><span data-ttu-id="452f7-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="452f7-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="452f7-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="452f7-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="452f7-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="452f7-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="452f7-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="452f7-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="452f7-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="452f7-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="452f7-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="452f7-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="452f7-110">302b do Sr e do Azure: Visão personalizada</span><span class="sxs-lookup"><span data-stu-id="452f7-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="452f7-111">Neste curso, você aprenderá a reconhecer o conteúdo Visual personalizado dentro de uma imagem fornecida, usando os recursos de Visão Personalizada do Azure em um aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="452f7-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="452f7-112">Este serviço permitirá que você treine um modelo de aprendizado de máquina usando imagens de objeto.</span><span class="sxs-lookup"><span data-stu-id="452f7-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="452f7-113">Em seguida, você usará o modelo treinado para reconhecer objetos semelhantes, conforme fornecido pela captura de câmera do Microsoft HoloLens ou uma câmera conectada ao seu PC para headsets de imersão (VR).</span><span class="sxs-lookup"><span data-stu-id="452f7-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![resultado do curso](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="452f7-115">O Azure Visão Personalizada é um serviço cognitiva da Microsoft que permite aos desenvolvedores criar classificadores de imagem personalizados.</span><span class="sxs-lookup"><span data-stu-id="452f7-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="452f7-116">Esses classificadores podem ser usados com novas imagens para reconhecer ou classificar objetos dentro dessa nova imagem.</span><span class="sxs-lookup"><span data-stu-id="452f7-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="452f7-117">O serviço fornece um portal online simples e fácil de usar para simplificar o processo.</span><span class="sxs-lookup"><span data-stu-id="452f7-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="452f7-118">Para obter mais informações, visite a [página de serviço de visão personalizada do Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="452f7-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="452f7-119">Após a conclusão deste curso, você terá um aplicativo de realidade misturada que poderá trabalhar em dois modos:</span><span class="sxs-lookup"><span data-stu-id="452f7-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="452f7-120">**Modo de análise**: configurar o serviço de visão personalizada manualmente carregando imagens, criando marcas e treinando o serviço para reconhecer objetos diferentes (nesse caso, mouse e teclado).</span><span class="sxs-lookup"><span data-stu-id="452f7-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="452f7-121">Em seguida, você criará um aplicativo do HoloLens que capturará imagens usando a câmera e tentará reconhecer esses objetos no mundo real.</span><span class="sxs-lookup"><span data-stu-id="452f7-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="452f7-122">**Modo de treinamento**: você irá implementar o código que habilitará um "modo de treinamento" em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="452f7-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="452f7-123">O modo de treinamento permitirá que você capture imagens usando a câmera do HoloLens, carregue as imagens capturadas no serviço e treine o modelo de visão personalizada.</span><span class="sxs-lookup"><span data-stu-id="452f7-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="452f7-124">Este curso ensinará a você como obter os resultados do Serviço de Visão Personalizada em um aplicativo de exemplo baseado em Unity.</span><span class="sxs-lookup"><span data-stu-id="452f7-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="452f7-125">Será necessário aplicar esses conceitos a um aplicativo personalizado que você possa estar criando.</span><span class="sxs-lookup"><span data-stu-id="452f7-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="452f7-126">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="452f7-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="452f7-127">Course</span><span class="sxs-lookup"><span data-stu-id="452f7-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="452f7-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="452f7-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="452f7-129"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="452f7-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="452f7-130">302b do Sr e do Azure: Visão personalizada</span><span class="sxs-lookup"><span data-stu-id="452f7-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="452f7-131">✔️</span><span class="sxs-lookup"><span data-stu-id="452f7-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="452f7-132">✔️</span><span class="sxs-lookup"><span data-stu-id="452f7-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="452f7-133">Embora este curso se concentre principalmente no HoloLens, você também pode aplicar o que aprende neste curso a fones de ouvido (VR) de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="452f7-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="452f7-134">Como os headsets de imersão (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu PC.</span><span class="sxs-lookup"><span data-stu-id="452f7-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="452f7-135">Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a headsets de imersão (VR).</span><span class="sxs-lookup"><span data-stu-id="452f7-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="452f7-136">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="452f7-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="452f7-137">Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o.</span><span class="sxs-lookup"><span data-stu-id="452f7-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="452f7-138">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (julho de 2018).</span><span class="sxs-lookup"><span data-stu-id="452f7-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="452f7-139">Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso correspondam perfeitamente ao que você encontrará no software mais recente do que o que está listado abaixo.</span><span class="sxs-lookup"><span data-stu-id="452f7-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="452f7-140">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="452f7-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="452f7-141">Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)</span><span class="sxs-lookup"><span data-stu-id="452f7-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="452f7-142">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="452f7-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="452f7-143">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="452f7-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="452f7-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="452f7-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="452f7-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="452f7-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="452f7-146">Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="452f7-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="452f7-147">Uma câmera conectada ao seu PC (para desenvolvimento de headsets de imersão)</span><span class="sxs-lookup"><span data-stu-id="452f7-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="452f7-148">Acesso à Internet para a instalação do Azure e recuperação de API de Visão Personalizada</span><span class="sxs-lookup"><span data-stu-id="452f7-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="452f7-149">Uma série de pelo menos cinco (5) imagens (dez (10) recomendado) para cada objeto que você deseja que a Serviço de Visão Personalizada reconheça.</span><span class="sxs-lookup"><span data-stu-id="452f7-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="452f7-150">Se desejar, você pode usar [as imagens já fornecidas com este curso (um mouse de computador e um teclado) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="452f7-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="452f7-151">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="452f7-151">Before you start</span></span>

1.  <span data-ttu-id="452f7-152">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="452f7-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="452f7-153">Configure e teste seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="452f7-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="452f7-154">Se você precisar de suporte para configurar seu HoloLens, [visite o artigo configuração do hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="452f7-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="452f7-155">É uma boa ideia executar a calibragem e o ajuste do sensor ao começar a desenvolver um novo aplicativo do HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="452f7-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="452f7-156">Para obter ajuda sobre calibragem, siga este [link para o artigo Calibration do HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="452f7-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="452f7-157">Para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste do sensor do HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="452f7-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="452f7-158">Capítulo 1-o portal de Serviço de Visão Personalizada</span><span class="sxs-lookup"><span data-stu-id="452f7-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="452f7-159">Para usar o *serviço de visão personalizada* no Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="452f7-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="452f7-160">Primeiro, [navegue até a página principal do *serviço de visão personalizada* ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="452f7-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="452f7-161">Clique **no botão introdução** .</span><span class="sxs-lookup"><span data-stu-id="452f7-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="452f7-162">Entre no portal de *serviço de visão personalizada* .</span><span class="sxs-lookup"><span data-stu-id="452f7-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="452f7-163">Se você ainda não tiver uma conta do Azure, será necessário criar uma.</span><span class="sxs-lookup"><span data-stu-id="452f7-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="452f7-164">Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="452f7-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="452f7-165">Depois de fazer logon pela primeira vez, você será solicitado com o painel *termos de serviço* .</span><span class="sxs-lookup"><span data-stu-id="452f7-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="452f7-166">Clique na caixa de seleção para concordar com os termos.</span><span class="sxs-lookup"><span data-stu-id="452f7-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="452f7-167">Em seguida, clique em **concordo**.</span><span class="sxs-lookup"><span data-stu-id="452f7-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="452f7-168">Tendo acordado os termos, você será navegado até a seção de *projetos* do Portal.</span><span class="sxs-lookup"><span data-stu-id="452f7-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="452f7-169">Clique em **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="452f7-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="452f7-170">Uma guia será exibida no lado direito, o que solicitará que você especifique alguns campos para o projeto.</span><span class="sxs-lookup"><span data-stu-id="452f7-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="452f7-171">Insira um *nome* para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="452f7-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="452f7-172">Insira uma *Descrição* para seu projeto (*opcional*).</span><span class="sxs-lookup"><span data-stu-id="452f7-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="452f7-173">Escolha um *grupo de recursos* ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="452f7-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="452f7-174">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="452f7-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="452f7-175">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="452f7-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="452f7-176">Definir os *tipos de projeto* para **classificação**</span><span class="sxs-lookup"><span data-stu-id="452f7-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="452f7-177">Defina os *domínios* como **geral**.</span><span class="sxs-lookup"><span data-stu-id="452f7-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="452f7-178">Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="452f7-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="452f7-179">Quando terminar, clique em **criar projeto**, você será redirecionado para a página Serviço de visão personalizada, projeto.</span><span class="sxs-lookup"><span data-stu-id="452f7-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="452f7-180">Capítulo 2-treinando seu Visão Personalizada projeto</span><span class="sxs-lookup"><span data-stu-id="452f7-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="452f7-181">Uma vez no portal de Visão Personalizada, seu objetivo principal é treinar seu projeto para reconhecer objetos específicos em imagens.</span><span class="sxs-lookup"><span data-stu-id="452f7-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="452f7-182">Você precisa de pelo menos cinco (5) imagens, embora dez (10) seja preferencial, para cada objeto que você deseja que seu aplicativo reconheça.</span><span class="sxs-lookup"><span data-stu-id="452f7-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="452f7-183">[Você pode usar as imagens fornecidas com este curso (um mouse de computador e um teclado)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="452f7-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="452f7-184">Para treinar seu projeto de Serviço de Visão Personalizada:</span><span class="sxs-lookup"><span data-stu-id="452f7-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="452f7-185">Clique no **+** botão ao lado de **marcas.**</span><span class="sxs-lookup"><span data-stu-id="452f7-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="452f7-186">Adicione o **nome** do objeto que você deseja reconhecer.</span><span class="sxs-lookup"><span data-stu-id="452f7-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="452f7-187">Clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="452f7-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="452f7-188">Você notará que sua **marca** foi adicionada (talvez seja necessário recarregar sua página para que ela apareça).</span><span class="sxs-lookup"><span data-stu-id="452f7-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="452f7-189">Clique na caixa de seleção ao lado de sua nova marca, se ainda não estiver marcada.</span><span class="sxs-lookup"><span data-stu-id="452f7-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="452f7-190">Clique em **Adicionar imagens** no centro da página.</span><span class="sxs-lookup"><span data-stu-id="452f7-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="452f7-191">Clique em **procurar arquivos locais**e pesquise, em seguida, selecione as imagens que você deseja carregar, com o mínimo de cinco (5).</span><span class="sxs-lookup"><span data-stu-id="452f7-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="452f7-192">Lembre-se de que todas essas imagens devem conter o objeto que você está treinando.</span><span class="sxs-lookup"><span data-stu-id="452f7-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="452f7-193">Você pode selecionar várias imagens de cada vez para carregar.</span><span class="sxs-lookup"><span data-stu-id="452f7-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="452f7-194">Depois que você puder ver as imagens na guia, selecione a marca apropriada na caixa **minhas marcas** .</span><span class="sxs-lookup"><span data-stu-id="452f7-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="452f7-195">Clique em **carregar arquivos**.</span><span class="sxs-lookup"><span data-stu-id="452f7-195">Click on **Upload files**.</span></span> <span data-ttu-id="452f7-196">Os arquivos começarão a ser carregados.</span><span class="sxs-lookup"><span data-stu-id="452f7-196">The files will begin uploading.</span></span> <span data-ttu-id="452f7-197">Depois de confirmar o carregamento, clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="452f7-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="452f7-198">Repita o mesmo processo para criar uma nova **marca** chamada **teclado** e carregar as fotos apropriadas para ela.</span><span class="sxs-lookup"><span data-stu-id="452f7-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="452f7-199">Certifique-se de desmarcar a **seleção** do *mouse* depois de criar as novas marcas, para mostrar a janela *Adicionar imagens* .</span><span class="sxs-lookup"><span data-stu-id="452f7-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="452f7-200">Depois de configurar as duas marcas, clique em **treinar**e a primeira iteração de treinamento começará a criar.</span><span class="sxs-lookup"><span data-stu-id="452f7-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="452f7-201">Depois de compilado, você poderá ver dois botões chamados **Make Default** e predição **URL**.</span><span class="sxs-lookup"><span data-stu-id="452f7-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="452f7-202">Clique em **tornar padrão** primeiro e, em seguida, clique em **URL de previsão**.</span><span class="sxs-lookup"><span data-stu-id="452f7-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="452f7-203">A URL do ponto de extremidade fornecida por isso é definida para qualquer *iteração* marcada como padrão.</span><span class="sxs-lookup"><span data-stu-id="452f7-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="452f7-204">Dessa forma, se você fizer uma nova *iteração* e atualizá-la como padrão, não será necessário alterar seu código.</span><span class="sxs-lookup"><span data-stu-id="452f7-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="452f7-205">Depois de clicar em *URL de previsão*, abra o *bloco de notas*e copie e cole a **URL** e a chave de **previsão**, para que você possa recuperá-la quando precisar mais tarde no código.</span><span class="sxs-lookup"><span data-stu-id="452f7-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="452f7-206">Clique no **engrenagem** na parte superior direita da tela.</span><span class="sxs-lookup"><span data-stu-id="452f7-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="452f7-207">Copie a **chave de treinamento** e cole-a em um *bloco de notas*, para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="452f7-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="452f7-208">Além disso, copie a **ID do projeto**e cole-a no arquivo do *bloco de notas* para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="452f7-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="452f7-209">Capítulo 3 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="452f7-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="452f7-210">A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="452f7-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="452f7-211">Abra o *Unity* e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="452f7-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="452f7-212">Agora, você precisará fornecer um nome de projeto de Unity.</span><span class="sxs-lookup"><span data-stu-id="452f7-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="452f7-213">Insira **AzureCustomVision.**</span><span class="sxs-lookup"><span data-stu-id="452f7-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="452f7-214">Verifique se o modelo de projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="452f7-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="452f7-215">Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="452f7-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="452f7-216">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="452f7-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="452f7-217">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="452f7-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="452f7-218">Vá para **Editar* > *preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="452f7-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="452f7-219">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="452f7-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="452f7-220">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="452f7-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="452f7-221">Em seguida, vá para **arquivo > configurações de Build** e selecione **plataforma universal do Windows**e, em seguida, clique no botão **alternar plataforma** para aplicar sua seleção.</span><span class="sxs-lookup"><span data-stu-id="452f7-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="452f7-222">Ainda no **arquivo > configurações de compilação** e certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="452f7-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="452f7-223">O **dispositivo de destino** está definido como **Hololens**</span><span class="sxs-lookup"><span data-stu-id="452f7-223">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="452f7-224">Para os headsets de imersão, defina **dispositivo de destino** para *qualquer dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="452f7-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="452f7-225">O **tipo de compilação** está definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="452f7-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="452f7-226">O **SDK** está definido para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="452f7-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="452f7-227">A **versão do Visual Studio** está definida para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="452f7-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="452f7-228">**Compilar e executar** é definido como **computador local**</span><span class="sxs-lookup"><span data-stu-id="452f7-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="452f7-229">Salve a cena e adicione-a à compilação.</span><span class="sxs-lookup"><span data-stu-id="452f7-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="452f7-230">Faça isso selecionando **Adicionar abrir cenas**.</span><span class="sxs-lookup"><span data-stu-id="452f7-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="452f7-231">Uma janela salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="452f7-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="452f7-232">Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.</span><span class="sxs-lookup"><span data-stu-id="452f7-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="452f7-233">Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo:* , digite **CustomVisionScene**e clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="452f7-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="452f7-234">Lembre-se de que você deve salvar as cenas do Unity na pasta *ativos* , pois elas devem ser associadas ao projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="452f7-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="452f7-235">Criar a pasta de cenas (e outras pastas semelhantes) é uma maneira típica de estruturar um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="452f7-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="452f7-236">As configurações restantes, em *configurações de compilação*, devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="452f7-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="452f7-237">Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="452f7-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="452f7-238">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="452f7-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="452f7-239">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="452f7-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="452f7-240">A **versão de tempo de execução de script** deve ser **Experimental (.NET 4,6 equivalente)** , o que irá disparar uma necessidade de reiniciar o editor.</span><span class="sxs-lookup"><span data-stu-id="452f7-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="452f7-241">O **back-end de script** deve ser **.net**</span><span class="sxs-lookup"><span data-stu-id="452f7-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="452f7-242">O **nível de compatibilidade da API** deve ser **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="452f7-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="452f7-243">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="452f7-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="452f7-244">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="452f7-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="452f7-245">**Integrada**</span><span class="sxs-lookup"><span data-stu-id="452f7-245">**Webcam**</span></span>

        3. <span data-ttu-id="452f7-246">**Phone**</span><span class="sxs-lookup"><span data-stu-id="452f7-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="452f7-247">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o SDK do **Windows Mixed Reality** foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="452f7-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="452f7-248">De volta às *configurações de compilação* , projetos do *Unity C\#*  não ficam mais esmaecidos; marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="452f7-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="452f7-249">Feche a janela configurações de compilação.</span><span class="sxs-lookup"><span data-stu-id="452f7-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="452f7-250">Salve sua cena e projeto (**arquivo > salvar cena/arquivo > salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="452f7-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="452f7-251">Capítulo 4-importando a DLL Newtonsoft no Unity</span><span class="sxs-lookup"><span data-stu-id="452f7-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="452f7-252">Se você quiser ignorar o componente de *configuração do Unity* deste curso e continuar diretamente no código, sinta-se à vontade para baixar este [Azure-Mr-302b. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), importá-lo em seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar no [capítulo 6 ](#chapter-6---create-the-customvisionanalyser-class).</span><span class="sxs-lookup"><span data-stu-id="452f7-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="452f7-253">Este curso requer o uso da biblioteca **Newtonsoft** , que você pode adicionar como uma DLL aos seus ativos.</span><span class="sxs-lookup"><span data-stu-id="452f7-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="452f7-254">O pacote que contém [essa biblioteca pode ser baixado deste link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="452f7-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="452f7-255">Para importar a biblioteca Newtonsoft para seu projeto, use o pacote do Unity que acompanha este curso.</span><span class="sxs-lookup"><span data-stu-id="452f7-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="452f7-256">Adicione o *.unitypackage* ao Unity usando a opção de menu \**pacote* *personalizado*do *pacote* > *de importação* de *ativos* > \* .</span><span class="sxs-lookup"><span data-stu-id="452f7-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="452f7-257">Na caixa **Importar pacote de Unity** que é exibida, verifique se tudo em (e incluindo) **plug-ins** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="452f7-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="452f7-258">Clique no botão **importar** para adicionar os itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="452f7-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="452f7-259">Vá para a pasta **Newtonsoft** em **plug-ins** na exibição de projeto e selecione o *plug-in Newtonsoft. JSON*.</span><span class="sxs-lookup"><span data-stu-id="452f7-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="452f7-260">Com o *plug-in Newtonsoft. JSON* selecionado, verifique se **qualquer plataforma** está desmarcada e, em seguida, verifique se **WSAPlayer** também está desmarcado e clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="452f7-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="452f7-261">Isso é apenas para confirmar que os arquivos estão configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="452f7-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="452f7-262">Marcar esses plug-ins os configura para ser usado apenas no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="452f7-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="452f7-263">Há um conjunto diferente deles na pasta WSA que será usada depois que o projeto for exportado do Unity.</span><span class="sxs-lookup"><span data-stu-id="452f7-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="452f7-264">Em seguida, você precisa abrir a pasta **WSA** , dentro da pasta **Newtonsoft** .</span><span class="sxs-lookup"><span data-stu-id="452f7-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="452f7-265">Você verá uma cópia do mesmo arquivo que acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="452f7-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="452f7-266">Selecione o arquivo e, no Inspetor, verifique se</span><span class="sxs-lookup"><span data-stu-id="452f7-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="452f7-267">**Qualquer plataforma** está desmarcada</span><span class="sxs-lookup"><span data-stu-id="452f7-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="452f7-268">**somente** **WSAPlayer** está **marcado**</span><span class="sxs-lookup"><span data-stu-id="452f7-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="452f7-269">Não **processar** está **marcado**</span><span class="sxs-lookup"><span data-stu-id="452f7-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="452f7-270">Capítulo 5 – configuração da câmera</span><span class="sxs-lookup"><span data-stu-id="452f7-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="452f7-271">No painel hierarquia, selecione a *câmera principal*.</span><span class="sxs-lookup"><span data-stu-id="452f7-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="452f7-272">Depois de selecionado, você poderá ver todos os componentes da *câmera principal* no *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="452f7-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="452f7-273">O objeto de *câmera* deve ser nomeado como a **câmera principal** (Observe a grafia!)</span><span class="sxs-lookup"><span data-stu-id="452f7-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="452f7-274">A **marca** da câmera principal deve ser definida como **MainCamera** (Observe a ortografia!)</span><span class="sxs-lookup"><span data-stu-id="452f7-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="452f7-275">Verifique se a **posição de transformação** está definida como **0, 0,** 0</span><span class="sxs-lookup"><span data-stu-id="452f7-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="452f7-276">Defina **limpar sinalizadores** como **cor sólida** (ignore isto para fone de ouvido de imersão).</span><span class="sxs-lookup"><span data-stu-id="452f7-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="452f7-277">Defina a cor do **plano de fundo** do componente da câmera como **preto, alfa 0 (código hex: #00000000)** (ignorar isso para headsets de imersão).</span><span class="sxs-lookup"><span data-stu-id="452f7-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="452f7-278">Capítulo 6-criar a classe CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="452f7-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="452f7-279">Neste ponto, você está pronto para escrever um código.</span><span class="sxs-lookup"><span data-stu-id="452f7-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="452f7-280">Você começará com a classe *CustomVisionAnalyser* .</span><span class="sxs-lookup"><span data-stu-id="452f7-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="452f7-281">As chamadas para o **serviço de visão personalizada** feitas no código mostrado abaixo são feitas usando a **API REST visão personalizada**.</span><span class="sxs-lookup"><span data-stu-id="452f7-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="452f7-282">Ao usar isso, você verá como implementar e usar essa API (útil para entender como implementar algo semelhante por conta própria).</span><span class="sxs-lookup"><span data-stu-id="452f7-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="452f7-283">Lembre-se de que a Microsoft oferece um **SDK serviço de visão personalizada** que também pode ser usado para fazer chamadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="452f7-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="452f7-284">Para obter mais informações, visite o artigo [serviço de visão personalizada SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) .</span><span class="sxs-lookup"><span data-stu-id="452f7-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="452f7-285">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="452f7-285">This class is responsible for:</span></span>

-   <span data-ttu-id="452f7-286">Carregando a imagem mais recente capturada como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="452f7-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="452f7-287">Enviando a matriz de bytes para a instância de *serviço de visão personalizada* do Azure para análise.</span><span class="sxs-lookup"><span data-stu-id="452f7-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="452f7-288">Recebendo a resposta como uma cadeia de caracteres JSON.</span><span class="sxs-lookup"><span data-stu-id="452f7-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="452f7-289">Desserializar a resposta e passar a *previsão* resultante para a classe *SceneOrganiser* , que cuidará de como a resposta deve ser exibida.</span><span class="sxs-lookup"><span data-stu-id="452f7-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="452f7-290">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="452f7-290">To create this class:</span></span>

1.  <span data-ttu-id="452f7-291">Clique com o botão direito do mouse na *pasta de ativos* localizada no *painel Projeto*e clique em **criar > pasta**.</span><span class="sxs-lookup"><span data-stu-id="452f7-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="452f7-292">Chame os **scripts**da pasta.</span><span class="sxs-lookup"><span data-stu-id="452f7-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="452f7-293">Clique duas vezes na pasta recém-criada para abri-la.</span><span class="sxs-lookup"><span data-stu-id="452f7-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="452f7-294">Clique com o botão direito do mouse dentro da pasta e clique em **criar** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="452f7-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="452f7-295">Nomeie o script *CustomVisionAnalyser*.</span><span class="sxs-lookup"><span data-stu-id="452f7-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="452f7-296">Clique duas vezes no novo script *CustomVisionAnalyser* para abri-lo com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="452f7-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="452f7-297">Atualize os namespaces na parte superior do seu arquivo para corresponder ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="452f7-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="452f7-298">Na classe *CustomVisionAnalyser* , adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="452f7-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="452f7-299">Certifique-se de inserir **sua chave de previsão** na variável **PredictionKey** e seu **ponto de extremidade de previsão** na variável **predictionEndpoint** .</span><span class="sxs-lookup"><span data-stu-id="452f7-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="452f7-300">Você os copiou para o *bloco de notas* no início do curso.</span><span class="sxs-lookup"><span data-stu-id="452f7-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="452f7-301">O código para **ativo ()** agora precisa ser adicionado para inicializar a variável de instância:</span><span class="sxs-lookup"><span data-stu-id="452f7-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="452f7-302">Exclua os métodos **Start ()** e **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="452f7-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="452f7-303">Em seguida, adicione a corrotina (com o método estático **GetImageAsByteArray ()** abaixo dela), que obterá os resultados da análise da imagem capturada pela classe *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="452f7-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="452f7-304">Na **AnalyseImageCapture** corrotina, há uma chamada para a classe *SceneOrganiser* que você ainda deseja criar.</span><span class="sxs-lookup"><span data-stu-id="452f7-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="452f7-305">Portanto, **deixe essas linhas comentadas por enquanto**.</span><span class="sxs-lookup"><span data-stu-id="452f7-305">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  <span data-ttu-id="452f7-306">Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="452f7-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="452f7-307">Capítulo 7-criar a classe CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="452f7-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="452f7-308">A classe que você criará agora é a classe *CustomVisionObjects* .</span><span class="sxs-lookup"><span data-stu-id="452f7-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="452f7-309">Esse script contém vários objetos usados por outras classes para serializar e desserializar as chamadas feitas ao *serviço de visão personalizada*.</span><span class="sxs-lookup"><span data-stu-id="452f7-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="452f7-310">É importante que você anote o ponto de extremidade que o Serviço de Visão Personalizada fornece, pois a estrutura JSON abaixo foi configurada para funcionar com [*visão personalizada previsão v 2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span><span class="sxs-lookup"><span data-stu-id="452f7-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="452f7-311">Se você tiver uma versão diferente, talvez seja necessário atualizar a estrutura abaixo.</span><span class="sxs-lookup"><span data-stu-id="452f7-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="452f7-312">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="452f7-312">To create this class:</span></span>

1.  <span data-ttu-id="452f7-313">Clique com o botão direito do mouse na pasta **scripts** e clique em **criar** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="452f7-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="452f7-314">Chame o script *CustomVisionObjects*.</span><span class="sxs-lookup"><span data-stu-id="452f7-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="452f7-315">Clique duas vezes no novo script **CustomVisionObjects** para abri-lo com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="452f7-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="452f7-316">Adicione os seguintes namespaces à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="452f7-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="452f7-317">Exclua os métodos **Start ()** e **Update ()** dentro da classe *CustomVisionObjects* ; Essa classe agora deve estar vazia.</span><span class="sxs-lookup"><span data-stu-id="452f7-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="452f7-318">Adicione as seguintes classes **fora** da classe *CustomVisionObjects* .</span><span class="sxs-lookup"><span data-stu-id="452f7-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="452f7-319">Esses objetos são usados pela biblioteca *Newtonsoft* para serializar e desserializar os dados de resposta:</span><span class="sxs-lookup"><span data-stu-id="452f7-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="452f7-320">Capítulo 8-criar a classe VoiceRecognizer</span><span class="sxs-lookup"><span data-stu-id="452f7-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="452f7-321">Essa classe reconhecerá a entrada de voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="452f7-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="452f7-322">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="452f7-322">To create this class:</span></span>

1.  <span data-ttu-id="452f7-323">Clique com o botão direito do mouse na pasta **scripts** e clique em **criar** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="452f7-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="452f7-324">Chame o script *VoiceRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="452f7-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="452f7-325">Clique duas vezes no novo script **VoiceRecognizer** para abri-lo com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="452f7-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="452f7-326">Adicione os seguintes namespaces acima da classe *VoiceRecognizer* :</span><span class="sxs-lookup"><span data-stu-id="452f7-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="452f7-327">Em seguida, adicione as seguintes variáveis dentro da classe *VoiceRecognizer* , acima do método *Start ()* :</span><span class="sxs-lookup"><span data-stu-id="452f7-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="452f7-328">Adicione os métodos **ativo ()** e **Iniciar ()** , o último deles configurará as *palavras-chave* do usuário que serão reconhecidas ao associar uma marca a uma imagem:</span><span class="sxs-lookup"><span data-stu-id="452f7-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="452f7-329">Exclua o método **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="452f7-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="452f7-330">Adicione o seguinte manipulador, que é chamado sempre que a entrada de voz é reconhecida:</span><span class="sxs-lookup"><span data-stu-id="452f7-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="452f7-331">Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="452f7-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="452f7-332">Não se preocupe com o código que pode parecer ter um erro, pois você fornecerá mais classes em breve, o que irá corrigi-los.</span><span class="sxs-lookup"><span data-stu-id="452f7-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="452f7-333">Capítulo 9-criar a classe CustomVisionTrainer</span><span class="sxs-lookup"><span data-stu-id="452f7-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="452f7-334">Essa classe encadeará uma série de chamadas Web para treinar o *serviço de visão personalizada*.</span><span class="sxs-lookup"><span data-stu-id="452f7-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="452f7-335">Cada chamada será explicada em detalhes logo acima do código.</span><span class="sxs-lookup"><span data-stu-id="452f7-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="452f7-336">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="452f7-336">To create this class:</span></span>

1.  <span data-ttu-id="452f7-337">Clique com o botão direito do mouse na pasta **scripts** e clique em **criar** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="452f7-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="452f7-338">Chame o script *CustomVisionTrainer*.</span><span class="sxs-lookup"><span data-stu-id="452f7-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="452f7-339">Clique duas vezes no novo script *CustomVisionTrainer* para abri-lo com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="452f7-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="452f7-340">Adicione os seguintes namespaces acima da classe *CustomVisionTrainer* :</span><span class="sxs-lookup"><span data-stu-id="452f7-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="452f7-341">Em seguida, adicione as seguintes variáveis dentro da classe *CustomVisionTrainer* , acima do método **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="452f7-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="452f7-342">A URL de treinamento usada aqui é fornecida na documentação do *visão personalizada training 1,2* e tem uma estrutura de: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="452f7-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="452f7-343">Para obter mais informações, visite a [*API de referência do visão personalizada Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="452f7-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="452f7-344">É importante anotar o ponto de extremidade que o Serviço de Visão Personalizada fornece a você para o modo de treinamento, já que a estrutura JSON usada (dentro da classe **CustomVisionObjects** ) foi configurada para funcionar com o [*treinamento de visão personalizada v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="452f7-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="452f7-345">Se você tiver uma versão diferente, talvez seja necessário atualizar a estrutura de *objetos* .</span><span class="sxs-lookup"><span data-stu-id="452f7-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="452f7-346">Certifique-se de adicionar o valor da **chave de serviço** (chave de treinamento) e o valor da **ID do projeto** , que você anotou anteriormente; Esses são os valores que você [coletou do portal anteriormente no curso (capítulo 2, etapa 10 em diante)](#chapter-2---training-your-custom-vision-oroject).</span><span class="sxs-lookup"><span data-stu-id="452f7-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-oroject).</span></span>

5.  <span data-ttu-id="452f7-347">Adicione os seguintes métodos **Start ()** e **ativo ()** .</span><span class="sxs-lookup"><span data-stu-id="452f7-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="452f7-348">Esses métodos são chamados na inicialização e contêm a chamada para configurar a interface do usuário:</span><span class="sxs-lookup"><span data-stu-id="452f7-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="452f7-349">Exclua o método **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="452f7-349">Delete the **Update()** method.</span></span> <span data-ttu-id="452f7-350">Essa classe não será necessária.</span><span class="sxs-lookup"><span data-stu-id="452f7-350">This class will not need it.</span></span>

7.  <span data-ttu-id="452f7-351">Adicione o método **RequestTagSelection ()** .</span><span class="sxs-lookup"><span data-stu-id="452f7-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="452f7-352">Esse método é o primeiro a ser chamado quando uma imagem foi capturada e armazenada no dispositivo e agora está pronta para ser enviada para o *serviço de visão personalizada*, para treiná-la.</span><span class="sxs-lookup"><span data-stu-id="452f7-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="452f7-353">Esse método exibe, na interface do usuário de treinamento, um conjunto de palavras-chave que o usuário pode usar para marcar a imagem que foi capturada.</span><span class="sxs-lookup"><span data-stu-id="452f7-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="452f7-354">Ele também alerta a classe *VoiceRecognizer* para começar a escutar o usuário para entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="452f7-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="452f7-355">Adicione o método **VerifyTag ()** .</span><span class="sxs-lookup"><span data-stu-id="452f7-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="452f7-356">Esse método receberá a entrada de voz reconhecida pela classe **VoiceRecognizer** e verificará sua validade e, em seguida, iniciará o processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="452f7-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="452f7-357">Adicione o método **SubmitImageForTraining ()** .</span><span class="sxs-lookup"><span data-stu-id="452f7-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="452f7-358">Esse método iniciará o Serviço de Visão Personalizada processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="452f7-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="452f7-359">A primeira etapa é recuperar a **ID de marca** do serviço que está associado à entrada de fala validada do usuário.</span><span class="sxs-lookup"><span data-stu-id="452f7-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="452f7-360">A **ID da marca** será então carregada junto com a imagem.</span><span class="sxs-lookup"><span data-stu-id="452f7-360">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="452f7-361">Adicione o método **TrainCustomVisionProject ()** .</span><span class="sxs-lookup"><span data-stu-id="452f7-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="452f7-362">Depois que a imagem for enviada e marcada, esse método será chamado.</span><span class="sxs-lookup"><span data-stu-id="452f7-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="452f7-363">Ele criará uma nova iteração que será treinada com todas as imagens anteriores enviadas ao serviço mais a imagem que acabou de ser carregada.</span><span class="sxs-lookup"><span data-stu-id="452f7-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="452f7-364">Depois que o treinamento for concluído, esse método chamará um método para definir a iteração recém-criada como **padrão**, para que o ponto de extremidade que você está usando para análise seja a iteração mais recente treinada.</span><span class="sxs-lookup"><span data-stu-id="452f7-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="452f7-365">Adicione o método **SetDefaultIteration ()** .</span><span class="sxs-lookup"><span data-stu-id="452f7-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="452f7-366">Esse método definirá a iteração criada anteriormente e treinada como *padrão*.</span><span class="sxs-lookup"><span data-stu-id="452f7-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="452f7-367">Depois de concluído, esse método terá que excluir a iteração anterior existente no serviço.</span><span class="sxs-lookup"><span data-stu-id="452f7-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="452f7-368">No momento da elaboração deste curso, há um limite de 10 (10) iterações de máximo que podem existir ao mesmo tempo no serviço.</span><span class="sxs-lookup"><span data-stu-id="452f7-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="452f7-369">Adicione o método **DeletePreviousIteration ()** .</span><span class="sxs-lookup"><span data-stu-id="452f7-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="452f7-370">Esse método irá encontrar e excluir a iteração não padrão anterior:</span><span class="sxs-lookup"><span data-stu-id="452f7-370">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="452f7-371">O último método a ser adicionado nessa classe é o método **GetImageAsByteArray ()** , usado nas chamadas da Web para converter a imagem capturada em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="452f7-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. <span data-ttu-id="452f7-372">Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="452f7-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="452f7-373">Capítulo 10 – criar a classe SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="452f7-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="452f7-374">Essa classe irá:</span><span class="sxs-lookup"><span data-stu-id="452f7-374">This class will:</span></span>

-   <span data-ttu-id="452f7-375">Crie um objeto de **cursor** para anexar à câmera principal.</span><span class="sxs-lookup"><span data-stu-id="452f7-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="452f7-376">Crie um objeto de **rótulo** que será exibido quando o serviço reconhecer os objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="452f7-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="452f7-377">Configure a câmera principal anexando os componentes apropriados a ela.</span><span class="sxs-lookup"><span data-stu-id="452f7-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="452f7-378">No **modo de análise**, gera os rótulos em tempo de execução, no espaço do mundo apropriado em relação à posição da câmera principal e exibe os dados recebidos do serviço de visão personalizada.</span><span class="sxs-lookup"><span data-stu-id="452f7-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="452f7-379">No **modo de treinamento**, gerar a interface do usuário que exibirá os diferentes estágios do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="452f7-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="452f7-380">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="452f7-380">To create this class:</span></span>

1.  <span data-ttu-id="452f7-381">Clique com o botão direito do mouse na pasta **scripts** e clique em **criar** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="452f7-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="452f7-382">Nomeie o script *SceneOrganiser*.</span><span class="sxs-lookup"><span data-stu-id="452f7-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="452f7-383">Clique duas vezes no novo script *SceneOrganiser* para abri-lo com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="452f7-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="452f7-384">Você só precisará de um namespace, remova os outros de acima da classe *SceneOrganiser* :</span><span class="sxs-lookup"><span data-stu-id="452f7-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="452f7-385">Em seguida, adicione as seguintes variáveis dentro da classe *SceneOrganiser* , acima do método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="452f7-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="452f7-386">Exclua os métodos **Start ()** e **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="452f7-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="452f7-387">Logo abaixo das variáveis, adicione o método **ativo ()** , que irá inicializar a classe e configurar a cena.</span><span class="sxs-lookup"><span data-stu-id="452f7-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="452f7-388">Agora, adicione o método **CreateCameraCursor ()** que cria e posiciona o cursor de câmera principal e o método CreateLabel **()** , que cria o objeto de **rótulo de análise** .</span><span class="sxs-lookup"><span data-stu-id="452f7-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="452f7-389">Adicione o método **SetCameraStatus ()** , que tratará as mensagens destinadas à malha de texto que fornece o status da câmera.</span><span class="sxs-lookup"><span data-stu-id="452f7-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="452f7-390">Adicione os métodos **PlaceAnalysisLabel ()** e **SetTagsToLastLabel ()** , que gerarão e exibirão os dados do serviço de visão personalizada na cena.</span><span class="sxs-lookup"><span data-stu-id="452f7-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="452f7-391">Por fim, adicione o método **CreateTrainingUI ()** , que irá gerar a interface do usuário exibindo os vários estágios do processo de treinamento quando o aplicativo estiver no modo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="452f7-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="452f7-392">Esse método também será aproveitado para criar o objeto status da câmera.</span><span class="sxs-lookup"><span data-stu-id="452f7-392">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="452f7-393">Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="452f7-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="452f7-394">Antes de continuar, abra a classe **CustomVisionAnalyser** e, dentro do método **AnalyseLastImageCaptured ()** , *remova os comentários* das seguintes linhas:</span><span class="sxs-lookup"><span data-stu-id="452f7-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="452f7-395">Capítulo 11 – criar a classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="452f7-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="452f7-396">A próxima classe que você vai criar é a classe *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="452f7-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="452f7-397">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="452f7-397">This class is responsible for:</span></span>

-   <span data-ttu-id="452f7-398">Capturando uma imagem usando a câmera do HoloLens e armazenando-a na pasta do *aplicativo* .</span><span class="sxs-lookup"><span data-stu-id="452f7-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="452f7-399">Lidando com gestos de toque do usuário.</span><span class="sxs-lookup"><span data-stu-id="452f7-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="452f7-400">Manter o valor de *Enumeração* que determina se o aplicativo será executado no modo de *análise* ou no modo de *treinamento* .</span><span class="sxs-lookup"><span data-stu-id="452f7-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="452f7-401">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="452f7-401">To create this class:</span></span>

1.  <span data-ttu-id="452f7-402">Vá para a pasta **scripts** que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="452f7-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="452f7-403">Clique com o botão direito do mouse dentro da pasta e clique em **criar > script C\#** .</span><span class="sxs-lookup"><span data-stu-id="452f7-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="452f7-404">Nomeie o script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="452f7-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="452f7-405">Clique duas vezes no novo script **ImageCapture** para abri-lo com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="452f7-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="452f7-406">Substitua os namespaces na parte superior do arquivo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="452f7-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="452f7-407">Em seguida, adicione as seguintes variáveis dentro da classe *ImageCapture* , acima do método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="452f7-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="452f7-408">O código para os métodos **ativo ()** e **Iniciar ()** agora precisa ser adicionado:</span><span class="sxs-lookup"><span data-stu-id="452f7-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="452f7-409">Implemente um manipulador que será chamado quando ocorrer um gesto de toque.</span><span class="sxs-lookup"><span data-stu-id="452f7-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="452f7-410">No modo de *análise* , o método **TapHandler** atua como uma opção para iniciar ou parar o loop de captura de foto.</span><span class="sxs-lookup"><span data-stu-id="452f7-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="452f7-411">No modo de *treinamento* , ele capturará uma imagem da câmera.</span><span class="sxs-lookup"><span data-stu-id="452f7-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="452f7-412">Quando o cursor estiver verde, isso significa que a câmera está disponível para tirar a imagem.</span><span class="sxs-lookup"><span data-stu-id="452f7-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="452f7-413">Quando o cursor estiver vermelho, significa que a câmera está ocupada.</span><span class="sxs-lookup"><span data-stu-id="452f7-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="452f7-414">Adicione o método que o aplicativo usa para iniciar o processo de captura de imagem e armazenar a imagem.</span><span class="sxs-lookup"><span data-stu-id="452f7-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  <span data-ttu-id="452f7-415">Adicione os manipuladores que serão chamados quando a foto tiver sido capturada e quando ela estiver pronta para ser analisada.</span><span class="sxs-lookup"><span data-stu-id="452f7-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="452f7-416">Em seguida, o resultado é passado para *CustomVisionAnalyser* ou *CustomVisionTrainer* , dependendo de qual modo o código está definido.</span><span class="sxs-lookup"><span data-stu-id="452f7-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="452f7-417">Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="452f7-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="452f7-418">Agora que todos os scripts foram concluídos, volte no editor do Unity e, em seguida, clique e arraste a classe **SceneOrganiser** da pasta **scripts** para o objeto da **câmera principal** no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="452f7-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="452f7-419">Capítulo 12 – antes de Compilar</span><span class="sxs-lookup"><span data-stu-id="452f7-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="452f7-420">Para executar um teste completo de seu aplicativo, você precisará Sideload-lo no seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="452f7-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="452f7-421">Antes de fazer isso, verifique se:</span><span class="sxs-lookup"><span data-stu-id="452f7-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="452f7-422">Todas as configurações mencionadas no [capítulo 2](#chapter-2---training-your-custom-vision-project) estão definidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="452f7-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="452f7-423">Todos os campos na **câmera principal**, no painel de inspetores, são atribuídos corretamente.</span><span class="sxs-lookup"><span data-stu-id="452f7-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="452f7-424">O script **SceneOrganiser** é anexado ao objeto da **câmera principal** .</span><span class="sxs-lookup"><span data-stu-id="452f7-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="452f7-425">Certifique-se de inserir sua **chave de previsão** na variável **predictionKey** .</span><span class="sxs-lookup"><span data-stu-id="452f7-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="452f7-426">Você inseriu o **ponto de extremidade de previsão** na variável **predictionEndpoint** .</span><span class="sxs-lookup"><span data-stu-id="452f7-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="452f7-427">Você inseriu sua **chave de treinamento** na variável **TrainingKey** da classe *CustomVisionTrainer* .</span><span class="sxs-lookup"><span data-stu-id="452f7-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="452f7-428">Você inseriu a **ID do projeto** na variável ProjectId da classe *CustomVisionTrainer* .</span><span class="sxs-lookup"><span data-stu-id="452f7-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="452f7-429">Capítulo 13-criar e sideloadr seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="452f7-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="452f7-430">Para iniciar o processo de *compilação* :</span><span class="sxs-lookup"><span data-stu-id="452f7-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="452f7-431">Vá para **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="452f7-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="452f7-432">**Projetos em tique\# Unity C**.</span><span class="sxs-lookup"><span data-stu-id="452f7-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="452f7-433">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="452f7-433">Click **Build**.</span></span> <span data-ttu-id="452f7-434">O Unity iniciará uma janela **Explorador de arquivos** , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado.</span><span class="sxs-lookup"><span data-stu-id="452f7-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="452f7-435">Crie essa pasta agora e nomeie-a como **aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="452f7-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="452f7-436">Em seguida, com a pasta de **aplicativo** selecionada, clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="452f7-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="452f7-437">O Unity começará a criar seu projeto na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="452f7-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="452f7-438">Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).</span><span class="sxs-lookup"><span data-stu-id="452f7-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="452f7-439">Para implantar no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="452f7-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="452f7-440">Você precisará do endereço IP do seu HoloLens (para implantação remota) e para garantir que seu HoloLens esteja no **modo de desenvolvedor**.</span><span class="sxs-lookup"><span data-stu-id="452f7-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="452f7-441">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="452f7-441">To do this:</span></span>

    1.  <span data-ttu-id="452f7-442">Enquanto estiver desgastando seu HoloLens, abra as **configurações**.</span><span class="sxs-lookup"><span data-stu-id="452f7-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="452f7-443">Vá para **rede &**  > **Opções avançadas** **de Internet Wi-Fi** > </span><span class="sxs-lookup"><span data-stu-id="452f7-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="452f7-444">Anote o endereço **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="452f7-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="452f7-445">Em seguida, navegue de volta para **configurações**e, em seguida, para **Atualizar & segurança** > **para desenvolvedores**</span><span class="sxs-lookup"><span data-stu-id="452f7-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="452f7-446">Defina o **modo de desenvolvedor em**.</span><span class="sxs-lookup"><span data-stu-id="452f7-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="452f7-447">Navegue até sua nova compilação do Unity (a pasta do **aplicativo** ) e abra o arquivo de solução com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="452f7-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="452f7-448">Na *configuração da solução* , selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="452f7-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="452f7-449">Na *plataforma da solução*, selecione **x86, computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="452f7-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="452f7-450">Você será solicitado a inserir o **endereço IP** de um dispositivo remoto (o HoloLens, neste caso, que você anotou).</span><span class="sxs-lookup"><span data-stu-id="452f7-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="452f7-451">Vá para o menu **Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="452f7-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="452f7-452">Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="452f7-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="452f7-453">Para implantar em headsets de imersão, defina a **plataforma da solução** como *computador local*e defina a **configuração** a ser depurada, com *x86* como a **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="452f7-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="452f7-454">Em seguida, implante no computador local, usando o item de menu **Compilar** , selecionando *implantar solução*.</span><span class="sxs-lookup"><span data-stu-id="452f7-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="452f7-455">Para usar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="452f7-455">To use the application:</span></span>

<span data-ttu-id="452f7-456">Para alternar a funcionalidade do aplicativo entre o modo de *treinamento* e o modo de *previsão* , você precisa atualizar a variável **AppMode** , localizada no método **ativo ()** localizado na classe *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="452f7-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="452f7-457">ou</span><span class="sxs-lookup"><span data-stu-id="452f7-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="452f7-458">No modo de *treinamento* :</span><span class="sxs-lookup"><span data-stu-id="452f7-458">In *Training* mode:</span></span>

- <span data-ttu-id="452f7-459">Examine o **mouse** ou o **teclado** e use o **gesto de toque**.</span><span class="sxs-lookup"><span data-stu-id="452f7-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="452f7-460">Em seguida, o texto será exibido solicitando que você forneça uma marca.</span><span class="sxs-lookup"><span data-stu-id="452f7-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="452f7-461">Diga o **mouse** ou o **teclado**.</span><span class="sxs-lookup"><span data-stu-id="452f7-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="452f7-462">No modo de *previsão* :</span><span class="sxs-lookup"><span data-stu-id="452f7-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="452f7-463">Examine um objeto e use o **gesto de toque**.</span><span class="sxs-lookup"><span data-stu-id="452f7-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="452f7-464">O texto será exibido fornecendo o objeto detectado, com a maior probabilidade (isso é normalizado).</span><span class="sxs-lookup"><span data-stu-id="452f7-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="452f7-465">Capítulo 14-avaliar e aprimorar seu modelo de Visão Personalizada</span><span class="sxs-lookup"><span data-stu-id="452f7-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="452f7-466">Para tornar seu serviço mais preciso, você precisará continuar a treinar o modelo usado para previsão.</span><span class="sxs-lookup"><span data-stu-id="452f7-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="452f7-467">Isso é feito por meio do uso de seu novo aplicativo, com os modos de *treinamento* e *previsão* , com o último, que exige que você visite o portal, que é o que é abordado neste capítulo.</span><span class="sxs-lookup"><span data-stu-id="452f7-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="452f7-468">Esteja preparado para revisitar seu portal muitas vezes, para melhorar continuamente seu modelo.</span><span class="sxs-lookup"><span data-stu-id="452f7-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="452f7-469">Acesse o portal de Visão Personalizada do Azure novamente e, quando estiver em seu projeto, selecione a guia *previsões* (do centro superior da página):</span><span class="sxs-lookup"><span data-stu-id="452f7-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="452f7-470">Você verá todas as imagens que foram enviadas para o serviço enquanto o aplicativo estava em execução.</span><span class="sxs-lookup"><span data-stu-id="452f7-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="452f7-471">Se você passar o mouse sobre as imagens, elas fornecerão as previsões que foram feitas para essa imagem:</span><span class="sxs-lookup"><span data-stu-id="452f7-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="452f7-472">Selecione uma das imagens para abri-la.</span><span class="sxs-lookup"><span data-stu-id="452f7-472">Select one of your images to open it.</span></span> <span data-ttu-id="452f7-473">Uma vez aberto, você verá as previsões feitas para essa imagem à direita.</span><span class="sxs-lookup"><span data-stu-id="452f7-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="452f7-474">Se as previsões estiverem corretas e você quiser adicionar essa imagem ao modelo de treinamento do serviço, clique na caixa de entrada *minhas marcas* e selecione a marca que deseja associar.</span><span class="sxs-lookup"><span data-stu-id="452f7-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="452f7-475">Quando tiver terminado, clique no botão *salvar e fechar* na parte inferior direita e continue na próxima imagem.</span><span class="sxs-lookup"><span data-stu-id="452f7-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="452f7-476">Depois de voltar à grade de imagens, você notará que as imagens às quais você adicionou marcas (e salvas) serão removidas.</span><span class="sxs-lookup"><span data-stu-id="452f7-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="452f7-477">Se você encontrar alguma imagem que ache que não tem seu item marcado dentro delas, poderá excluí-las clicando no tique nessa imagem (pode fazer isso para várias imagens) e, em seguida, clicando em *excluir* no canto superior direito da página de grade.</span><span class="sxs-lookup"><span data-stu-id="452f7-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="452f7-478">No pop-up que segue, você pode clicar em *Sim, excluir* ou *não*, para confirmar a exclusão ou cancelá-la, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="452f7-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="452f7-479">Quando você estiver pronto para continuar, clique no botão de *trem* verde no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="452f7-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="452f7-480">Seu modelo de serviço será treinado com todas as imagens que você forneceu agora (o que o tornará mais preciso).</span><span class="sxs-lookup"><span data-stu-id="452f7-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="452f7-481">Quando o treinamento for concluído, certifique-se de clicar no botão *tornar padrão* mais uma vez, para que sua *URL de previsão* continue a usar a iteração mais atualizada do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="452f7-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="452f7-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="452f7-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="452f7-483">Seu aplicativo de API Visão Personalizada concluído</span><span class="sxs-lookup"><span data-stu-id="452f7-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="452f7-484">Parabéns, você criou um aplicativo de realidade misturada que aproveita a API de Visão Personalizada do Azure para reconhecer objetos do mundo real, treinar o modelo de serviço e exibir a confiança do que foi visto.</span><span class="sxs-lookup"><span data-stu-id="452f7-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="452f7-485">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="452f7-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="452f7-486">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="452f7-486">Exercise 1</span></span>

<span data-ttu-id="452f7-487">Treine sua **serviço de visão personalizada** para reconhecer mais objetos.</span><span class="sxs-lookup"><span data-stu-id="452f7-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="452f7-488">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="452f7-488">Exercise 2</span></span>

<span data-ttu-id="452f7-489">Como uma maneira de expandir o que você aprendeu, conclua os seguintes exercícios:</span><span class="sxs-lookup"><span data-stu-id="452f7-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="452f7-490">Tocar um som quando um objeto for reconhecido.</span><span class="sxs-lookup"><span data-stu-id="452f7-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="452f7-491">Exercício 3</span><span class="sxs-lookup"><span data-stu-id="452f7-491">Exercise 3</span></span>

<span data-ttu-id="452f7-492">Use a API para treinar novamente seu serviço com as mesmas imagens que seu aplicativo está analisando, para tornar o serviço mais preciso (faça a previsão e o treinamento simultaneamente).</span><span class="sxs-lookup"><span data-stu-id="452f7-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
