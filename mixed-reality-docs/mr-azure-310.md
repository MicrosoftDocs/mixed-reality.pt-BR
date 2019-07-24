---
title: Sr e Azure 310-detecção de objeto
description: Conclua este curso para aprender a treinar um modelo de aprendizado de máquina e, em seguida, usar o modelo treinado para reconhecer objetos semelhantes e sua posição no mundo real de dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, visão personalizada, detecção de objetos, realidade misturada, Academia, Unity, tutorial, API, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63544415"
---
>[!NOTE]
><span data-ttu-id="b6701-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="b6701-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b6701-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b6701-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b6701-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b6701-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b6701-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="b6701-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b6701-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b6701-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b6701-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="b6701-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="b6701-110">Sr e Azure 310: Detecção de objeto</span><span class="sxs-lookup"><span data-stu-id="b6701-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="b6701-111">Neste curso, você aprenderá a reconhecer o conteúdo Visual personalizado e sua posição espacial dentro de uma imagem fornecida, usando o Azure Visão Personalizada recursos de "detecção de objeto" em um aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="b6701-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="b6701-112">Este serviço permitirá que você treine um modelo de aprendizado de máquina usando imagens de objeto.</span><span class="sxs-lookup"><span data-stu-id="b6701-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="b6701-113">Em seguida, você usará o modelo treinado para reconhecer objetos semelhantes e aproximar seu local no mundo real, conforme fornecido pela captura de câmera do Microsoft HoloLens ou uma câmera conectar-se a um PC para headsets de imersão (VR).</span><span class="sxs-lookup"><span data-stu-id="b6701-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![resultado do curso](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="b6701-115">**Visão personalizada do Azure, a detecção de objeto** é um serviço da Microsoft que permite aos desenvolvedores criar classificadores de imagem personalizados.</span><span class="sxs-lookup"><span data-stu-id="b6701-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="b6701-116">Esses classificadores podem ser usados com novas imagens para detectar objetos nessa nova imagem, fornecendo **limites de caixa** dentro da própria imagem.</span><span class="sxs-lookup"><span data-stu-id="b6701-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="b6701-117">O serviço fornece um portal online simples, fácil de usar, para simplificar esse processo.</span><span class="sxs-lookup"><span data-stu-id="b6701-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="b6701-118">Para obter mais informações, visite os links a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6701-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="b6701-119">Página de Visão Personalizada do Azure</span><span class="sxs-lookup"><span data-stu-id="b6701-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="b6701-120">Limites e cotas</span><span class="sxs-lookup"><span data-stu-id="b6701-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="b6701-121">Após a conclusão deste curso, você terá um aplicativo de realidade misturada que poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b6701-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="b6701-122">O usuário poderá *olhar* em um objeto, que foi treinado usando a serviço de visão personalizada do Azure, a detecção de objetos.</span><span class="sxs-lookup"><span data-stu-id="b6701-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="b6701-123">O usuário usará o gesto de *toque* para capturar uma imagem do que está olhando.</span><span class="sxs-lookup"><span data-stu-id="b6701-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="b6701-124">O aplicativo enviará a imagem para a Serviço de Visão Personalizada do Azure.</span><span class="sxs-lookup"><span data-stu-id="b6701-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="b6701-125">Haverá uma resposta do serviço que exibirá o resultado do reconhecimento como texto de espaço mundial.</span><span class="sxs-lookup"><span data-stu-id="b6701-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="b6701-126">Isso será realizado por meio da utilização do acompanhamento espacial do Microsoft HoloLens, como uma maneira de entender a posição mundial do objeto reconhecido e, em seguida, usar a *marca* associada ao que é detectado na imagem, para fornecer o texto do rótulo.</span><span class="sxs-lookup"><span data-stu-id="b6701-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="b6701-127">O curso também abordará manualmente o carregamento de imagens, a criação de marcas e o treinamento do serviço, para reconhecer objetos diferentes (no exemplo fornecido, uma xícara), definindo a *caixa de limite* na imagem que você envia.</span><span class="sxs-lookup"><span data-stu-id="b6701-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="b6701-128">Após a criação e o uso do aplicativo, o desenvolvedor deve navegar de volta para a Serviço de Visão Personalizada do Azure e identificar as previsões feitas pelo serviço e determinar se elas estavam corretas ou não (por meio da marcação de qualquer coisa que o serviço perdeu e ajustando as *caixas*delimitadoras).</span><span class="sxs-lookup"><span data-stu-id="b6701-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="b6701-129">Em seguida, o serviço pode ser treinado novamente, o que aumentará a probabilidade de reconhecê-los em objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="b6701-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="b6701-130">Este curso ensinará como obter os resultados da Serviço de Visão Personalizada do Azure, detecção de objetos, em um aplicativo de exemplo baseado em Unity.</span><span class="sxs-lookup"><span data-stu-id="b6701-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="b6701-131">Será necessário aplicar esses conceitos a um aplicativo personalizado que você possa estar criando.</span><span class="sxs-lookup"><span data-stu-id="b6701-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="b6701-132">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="b6701-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b6701-133">Course</span><span class="sxs-lookup"><span data-stu-id="b6701-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b6701-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b6701-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b6701-135"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="b6701-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="b6701-136">Sr e Azure 310: Detecção de objeto</span><span class="sxs-lookup"><span data-stu-id="b6701-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="b6701-137">✔️</span><span class="sxs-lookup"><span data-stu-id="b6701-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="b6701-138">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b6701-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b6701-139">Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o.</span><span class="sxs-lookup"><span data-stu-id="b6701-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b6701-140">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (julho de 2018).</span><span class="sxs-lookup"><span data-stu-id="b6701-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="b6701-141">Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) , embora não seja recomendável que as informações neste curso correspondam perfeitamente ao que você encontrará no software mais recente do que o que está listado abaixo.</span><span class="sxs-lookup"><span data-stu-id="b6701-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="b6701-142">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="b6701-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b6701-143">Um PC de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="b6701-143">A development PC</span></span>
- [<span data-ttu-id="b6701-144">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="b6701-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="b6701-145">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="b6701-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="b6701-146">Unity 2017,4 LTS</span><span class="sxs-lookup"><span data-stu-id="b6701-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="b6701-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b6701-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="b6701-148">Um [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="b6701-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="b6701-149">Acesso à Internet para a instalação do Azure e recuperação de Serviço de Visão Personalizada</span><span class="sxs-lookup"><span data-stu-id="b6701-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="b6701-150">Uma série de pelo menos quinze (15) imagens são necessárias) para cada objeto que você deseja que o Visão Personalizada reconheça.</span><span class="sxs-lookup"><span data-stu-id="b6701-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="b6701-151">Se desejar, você pode usar as imagens já fornecidas com este curso, [uma série de CUPS](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="b6701-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="b6701-152">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="b6701-152">Before you start</span></span>

1.  <span data-ttu-id="b6701-153">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="b6701-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="b6701-154">Configure e teste seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b6701-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="b6701-155">Se você precisar de suporte para configurar seu HoloLens, [visite o artigo configuração do hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="b6701-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="b6701-156">É uma boa ideia executar a calibragem e o ajuste do sensor ao começar a desenvolver um novo aplicativo do HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="b6701-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="b6701-157">Para obter ajuda sobre calibragem, siga este [link para o artigo Calibration do HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="b6701-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="b6701-158">Para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste do sensor do HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="b6701-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="b6701-159">Capítulo 1-o portal de Visão Personalizada</span><span class="sxs-lookup"><span data-stu-id="b6701-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="b6701-160">Para usar o **serviço de visão personalizada do Azure**, você precisará configurar uma instância dele para ser disponibilizada para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6701-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="b6701-161">Navegue [até a página principal do **serviço de visão personalizada** ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="b6701-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="b6701-162">Clique em **introdução**.</span><span class="sxs-lookup"><span data-stu-id="b6701-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="b6701-163">Entre no portal de Visão Personalizada.</span><span class="sxs-lookup"><span data-stu-id="b6701-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="b6701-164">Se você ainda não tiver uma conta do Azure, será necessário criar uma.</span><span class="sxs-lookup"><span data-stu-id="b6701-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="b6701-165">Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="b6701-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="b6701-166">Depois de fazer logon pela primeira vez, você será solicitado com o painel *termos de serviço* .</span><span class="sxs-lookup"><span data-stu-id="b6701-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="b6701-167">Clique na caixa de seleção para *concordar com os termos*.</span><span class="sxs-lookup"><span data-stu-id="b6701-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="b6701-168">Em seguida, clique em **concordo**.</span><span class="sxs-lookup"><span data-stu-id="b6701-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="b6701-169">Tendo acordado os termos, agora você está na seção *meus projetos* .</span><span class="sxs-lookup"><span data-stu-id="b6701-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="b6701-170">Clique em **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="b6701-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="b6701-171">Uma guia será exibida no lado direito, o que solicitará que você especifique alguns campos para o projeto.</span><span class="sxs-lookup"><span data-stu-id="b6701-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="b6701-172">Inserir um nome para seu projeto</span><span class="sxs-lookup"><span data-stu-id="b6701-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="b6701-173">Inserir uma descrição para seu projeto (**opcional**)</span><span class="sxs-lookup"><span data-stu-id="b6701-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="b6701-174">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="b6701-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="b6701-175">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="b6701-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b6701-176">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="b6701-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="b6701-177">Se você quiser [ler mais sobre os grupos de recursos do Azure, navegue até o docs associado](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="b6701-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="b6701-178">Defina os **tipos de projeto** como **detecção de objeto (versão prévia)** .</span><span class="sxs-lookup"><span data-stu-id="b6701-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="b6701-179">Quando terminar, clique em **criar projeto**e você será redirecionado para a página do projeto serviço de visão personalizada.</span><span class="sxs-lookup"><span data-stu-id="b6701-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="b6701-180">Capítulo 2-treinando seu Visão Personalizada projeto</span><span class="sxs-lookup"><span data-stu-id="b6701-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="b6701-181">Uma vez no portal de Visão Personalizada, seu objetivo principal é treinar seu projeto para reconhecer objetos específicos em imagens.</span><span class="sxs-lookup"><span data-stu-id="b6701-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="b6701-182">Você precisa de pelo menos quinze (15) imagens para cada objeto que você deseja que seu aplicativo reconheça.</span><span class="sxs-lookup"><span data-stu-id="b6701-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="b6701-183">Você pode usar as imagens fornecidas com este curso ([uma série de CUPS](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="b6701-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="b6701-184">Para treinar seu projeto de Visão Personalizada:</span><span class="sxs-lookup"><span data-stu-id="b6701-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="b6701-185">Clique no **+** botão ao lado de **marcas**.</span><span class="sxs-lookup"><span data-stu-id="b6701-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="b6701-186">Adicione um **nome** para a marca que será usada para associar suas imagens ao.</span><span class="sxs-lookup"><span data-stu-id="b6701-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="b6701-187">Neste exemplo, estamos usando imagens de CUPS para reconhecimento e, portanto, nomeamos a marca para isso, **Cup**.</span><span class="sxs-lookup"><span data-stu-id="b6701-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="b6701-188">Clique em **salvar** após concluir.</span><span class="sxs-lookup"><span data-stu-id="b6701-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="b6701-189">Você notará que sua **marca** foi adicionada (talvez seja necessário recarregar sua página para que ela apareça).</span><span class="sxs-lookup"><span data-stu-id="b6701-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="b6701-190">Clique em **Adicionar imagens** no centro da página.</span><span class="sxs-lookup"><span data-stu-id="b6701-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="b6701-191">Clique em **procurar arquivos locais**e navegue até as imagens que você deseja carregar para um objeto, com o mínimo de quinze (15).</span><span class="sxs-lookup"><span data-stu-id="b6701-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="b6701-192">Você pode selecionar várias imagens de cada vez para carregar.</span><span class="sxs-lookup"><span data-stu-id="b6701-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="b6701-193">Pressione **carregar arquivos** depois de selecionar todas as imagens com as quais você gostaria de treinar o projeto.</span><span class="sxs-lookup"><span data-stu-id="b6701-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="b6701-194">Os arquivos começarão a ser carregados.</span><span class="sxs-lookup"><span data-stu-id="b6701-194">The files will begin uploading.</span></span> <span data-ttu-id="b6701-195">Depois de confirmar o carregamento, clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="b6701-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="b6701-196">Neste ponto, suas imagens são carregadas, mas não marcadas.</span><span class="sxs-lookup"><span data-stu-id="b6701-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="b6701-197">Para marcar suas imagens, use o mouse.</span><span class="sxs-lookup"><span data-stu-id="b6701-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="b6701-198">À medida que você passa o mouse sobre a imagem, um realce de seleção o ajudará a desenhar automaticamente uma seleção em volta do objeto.</span><span class="sxs-lookup"><span data-stu-id="b6701-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="b6701-199">Se não for preciso, você poderá desenhar o seu próprio.</span><span class="sxs-lookup"><span data-stu-id="b6701-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="b6701-200">Isso é feito mantendo o clique com o botão esquerdo do mouse e arrastando a região de seleção para abranger seu objeto.</span><span class="sxs-lookup"><span data-stu-id="b6701-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="b6701-201">Após a seleção do objeto na imagem, um pequeno prompt solicitará que você *adicione a marca de região*.</span><span class="sxs-lookup"><span data-stu-id="b6701-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="b6701-202">Selecione a marca criada anteriormente (' Cup ', no exemplo acima) ou, se você estiver adicionando mais marcas, digite-as em e clique no botão **+ (mais)** .</span><span class="sxs-lookup"><span data-stu-id="b6701-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="b6701-203">Para marcar a próxima imagem, você pode clicar na seta à direita da folha ou fechar a folha de marca (clicando no **X** no canto superior direito da folha) e, em seguida, na imagem seguinte.</span><span class="sxs-lookup"><span data-stu-id="b6701-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="b6701-204">Quando a próxima imagem estiver pronta, repita o mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="b6701-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="b6701-205">Faça isso para todas as imagens que você carregou, até que todas estejam marcadas.</span><span class="sxs-lookup"><span data-stu-id="b6701-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="b6701-206">Você pode selecionar vários objetos na mesma imagem, como a imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="b6701-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="b6701-207">Depois de ter marcado todos eles, clique no botão **marcado** , à esquerda da tela, para revelar as imagens marcadas.</span><span class="sxs-lookup"><span data-stu-id="b6701-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="b6701-208">Agora você está pronto para treinar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="b6701-208">You are now ready to train your Service.</span></span> <span data-ttu-id="b6701-209">Clique no botão **treinar** e a primeira iteração de treinamento será iniciada.</span><span class="sxs-lookup"><span data-stu-id="b6701-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="b6701-210">Depois de compilado, você poderá ver dois botões chamados **Make Default** e predição **URL**.</span><span class="sxs-lookup"><span data-stu-id="b6701-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="b6701-211">Clique em **tornar padrão** primeiro e, em seguida, clique em **URL de previsão**.</span><span class="sxs-lookup"><span data-stu-id="b6701-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="b6701-212">O ponto de extremidade fornecido por isso é definido para qualquer *iteração* marcada como padrão.</span><span class="sxs-lookup"><span data-stu-id="b6701-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="b6701-213">Dessa forma, se você fizer uma nova *iteração* e atualizá-la como padrão, não será necessário alterar seu código.</span><span class="sxs-lookup"><span data-stu-id="b6701-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="b6701-214">Depois de clicar em **URL de previsão**, abra o *bloco de notas*e copie e cole a **URL** (também chamada de ponto de extremidade de **previsão**) e a chave de **previsão do serviço**para que você possa recuperá-la quando precisar mais tarde no código.</span><span class="sxs-lookup"><span data-stu-id="b6701-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="b6701-215">Capítulo 3 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="b6701-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="b6701-216">A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="b6701-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="b6701-217">Abra o **Unity** e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="b6701-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="b6701-218">Agora, você precisará fornecer um nome de projeto de Unity.</span><span class="sxs-lookup"><span data-stu-id="b6701-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="b6701-219">Insira **CustomVisionObjDetection**.</span><span class="sxs-lookup"><span data-stu-id="b6701-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="b6701-220">Verifique se o tipo de projeto está definido como **3D**e defina o **local** como algum lugar apropriado para você (Lembre-se de que mais próximo aos diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="b6701-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b6701-221">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="b6701-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="b6701-222">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b6701-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b6701-223">Vá para **Editar* > *preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="b6701-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b6701-224">Altere o **Editor de script externo** para o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b6701-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="b6701-225">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="b6701-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="b6701-226">Em seguida, vá para **arquivo > configurações de compilação** , alterne a **plataforma** para *plataforma universal do Windows*e, em seguida, clique no botão **alternar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="b6701-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="b6701-227">Na mesma janela **configurações de compilação** , verifique se o seguinte está definido:</span><span class="sxs-lookup"><span data-stu-id="b6701-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="b6701-228">O **dispositivo de destino** está definido como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="b6701-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="b6701-229">O **tipo de compilação** está definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="b6701-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="b6701-230">O **SDK** está definido para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="b6701-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="b6701-231">A **versão do Visual Studio** está definida para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="b6701-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="b6701-232">**Compilar e executar** é definido como **computador local**</span><span class="sxs-lookup"><span data-stu-id="b6701-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="b6701-233">As configurações restantes, em **configurações de compilação**, devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="b6701-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="b6701-234">Na mesma janela **configurações de compilação** , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o **Inspetor** está localizado.</span><span class="sxs-lookup"><span data-stu-id="b6701-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="b6701-235">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="b6701-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="b6701-236">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="b6701-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="b6701-237">A **versão de tempo de execução de script** deve ser **Experimental** (.NET 4,6 equivalente), o que irá disparar uma necessidade de reiniciar o editor.</span><span class="sxs-lookup"><span data-stu-id="b6701-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="b6701-238">O **back-end de script** deve ser **.net**.</span><span class="sxs-lookup"><span data-stu-id="b6701-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="b6701-239">O **nível de compatibilidade da API** deve ser **.NET 4,6**.</span><span class="sxs-lookup"><span data-stu-id="b6701-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="b6701-240">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="b6701-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="b6701-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="b6701-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="b6701-242">**Integrada**</span><span class="sxs-lookup"><span data-stu-id="b6701-242">**Webcam**</span></span>

        3. <span data-ttu-id="b6701-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="b6701-243">**SpatialPerception**</span></span>

            <span data-ttu-id="b6701-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="b6701-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="b6701-245">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**de tique, em seguida, verifique se o SDK do **Windows Mixed Reality** foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="b6701-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="b6701-246">De volta às **configurações de compilação**, *\# projetos Unity C* não estão mais esmaecidos: marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="b6701-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="b6701-247">Feche a janela **configurações de compilação** .</span><span class="sxs-lookup"><span data-stu-id="b6701-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="b6701-248">No **Editor**, clique em **Editar** > **configurações** > do projeto**gráficos**.</span><span class="sxs-lookup"><span data-stu-id="b6701-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="b6701-249">No **painel Inspetor** , as *configurações de gráficos* serão abertas.</span><span class="sxs-lookup"><span data-stu-id="b6701-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="b6701-250">Role para baixo até ver uma matriz chamada **sempre incluir sombreadores**.</span><span class="sxs-lookup"><span data-stu-id="b6701-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="b6701-251">Adicione um slot aumentando a variável de **tamanho** em um (neste exemplo, ele era 8, então fizemos 9).</span><span class="sxs-lookup"><span data-stu-id="b6701-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="b6701-252">Um novo slot será exibido na última posição da matriz, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="b6701-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="b6701-253">No slot, clique no círculo de destino pequeno ao lado do slot para abrir uma lista de sombreadores.</span><span class="sxs-lookup"><span data-stu-id="b6701-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="b6701-254">Procure por sombreadores herdados/sombreador **transparente/difuso** e clique duas vezes nele.</span><span class="sxs-lookup"><span data-stu-id="b6701-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="b6701-255">Capítulo 4-importando o pacote do CustomVisionObjDetection Unity</span><span class="sxs-lookup"><span data-stu-id="b6701-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="b6701-256">Para este curso, você receberá um pacote de ativos de Unity chamado **Azure-Mr-310. unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="b6701-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="b6701-257">Dicas Todos os objetos com suporte do Unity, incluindo cenas inteiras, podem ser empacotados em um arquivo **. unitypackage** e exportados/importados em outros projetos.</span><span class="sxs-lookup"><span data-stu-id="b6701-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="b6701-258">É a maneira mais segura, e mais eficiente, de mover ativos entre diferentes **projetos do Unity**.</span><span class="sxs-lookup"><span data-stu-id="b6701-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="b6701-259">Você pode encontrar o [pacote Azure-Mr-310 que você precisa baixar aqui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="b6701-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="b6701-260">Com o painel do Unity na frente, clique em **ativos** no menu na parte superior da tela e, em seguida, clique em **Importar pacote > pacote personalizado**.</span><span class="sxs-lookup"><span data-stu-id="b6701-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="b6701-261">Use o seletor de arquivos para selecionar o pacote **Azure-Mr-310. unitypackage** e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="b6701-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="b6701-262">Uma lista de componentes para este ativo será exibida para você.</span><span class="sxs-lookup"><span data-stu-id="b6701-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="b6701-263">Confirme a importação clicando no botão **importar** .</span><span class="sxs-lookup"><span data-stu-id="b6701-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="b6701-264">Depois de concluir a importação, você observará que as pastas do pacote agora foram adicionadas à sua pasta de **ativos** .</span><span class="sxs-lookup"><span data-stu-id="b6701-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="b6701-265">Esse tipo de estrutura de pastas é típico para um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="b6701-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="b6701-266">A pasta **materiais** contém o material usado pelo **cursor olhar**.</span><span class="sxs-lookup"><span data-stu-id="b6701-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="b6701-267">A pasta **plugins** contém a dll Newtonsoft usada pelo código para desserializar a resposta da Web do serviço.</span><span class="sxs-lookup"><span data-stu-id="b6701-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="b6701-268">As duas (2) diferentes versões contidas na pasta e na subpasta são necessárias para permitir que a biblioteca seja usada e criada pelo editor de Unity e pela compilação UWP.</span><span class="sxs-lookup"><span data-stu-id="b6701-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="b6701-269">A pasta **pré-fabricados** contém o pré-fabricados contido na cena.</span><span class="sxs-lookup"><span data-stu-id="b6701-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="b6701-270">São eles:</span><span class="sxs-lookup"><span data-stu-id="b6701-270">Those are:</span></span>

        1.  <span data-ttu-id="b6701-271">O **GazeCursor**, o cursor usado no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6701-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="b6701-272">Trabalhará junto com o SpatialMapping pré-fabricado para poder ser colocado na cena sobre objetos físicos.</span><span class="sxs-lookup"><span data-stu-id="b6701-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="b6701-273">O **rótulo**, que é o objeto de interface do usuário usado para exibir a marca de objeto na cena quando necessário.</span><span class="sxs-lookup"><span data-stu-id="b6701-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="b6701-274">O **SpatialMapping**, que é o objeto que permite que o aplicativo use criar um mapa virtual, usando o acompanhamento espacial do Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b6701-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="b6701-275">A pasta de **cenas** que atualmente contém a cena pré-criada para este curso.</span><span class="sxs-lookup"><span data-stu-id="b6701-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="b6701-276">Abra a pasta de **cenas** , no **painel Projeto**e clique duas vezes em **ObjDetectionScene**para carregar a cena que será usada para este curso.</span><span class="sxs-lookup"><span data-stu-id="b6701-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="b6701-277">**Nenhum código está incluído**, você escreverá o código seguindo este curso.</span><span class="sxs-lookup"><span data-stu-id="b6701-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="b6701-278">Capítulo 5 – criar a classe CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="b6701-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="b6701-279">Neste ponto, você está pronto para escrever um código.</span><span class="sxs-lookup"><span data-stu-id="b6701-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="b6701-280">Você começará com a classe **CustomVisionAnalyser** .</span><span class="sxs-lookup"><span data-stu-id="b6701-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="b6701-281">As chamadas para o **serviço de visão personalizada**, feitas no código mostrado abaixo, são feitas usando a **API REST do visão personalizada**.</span><span class="sxs-lookup"><span data-stu-id="b6701-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="b6701-282">Ao usar isso, você verá como implementar e usar essa API (útil para entender como implementar algo semelhante por conta própria).</span><span class="sxs-lookup"><span data-stu-id="b6701-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="b6701-283">Lembre-se de que a Microsoft oferece um **SDK Visão personalizada** que também pode ser usado para fazer chamadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b6701-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="b6701-284">Para obter mais informações, visite o [artigo visão personalizada SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span><span class="sxs-lookup"><span data-stu-id="b6701-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="b6701-285">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="b6701-285">This class is responsible for:</span></span>

- <span data-ttu-id="b6701-286">Carregando a imagem mais recente capturada como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="b6701-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="b6701-287">Enviando a matriz de bytes para a instância de **serviço de visão personalizada** do Azure para análise.</span><span class="sxs-lookup"><span data-stu-id="b6701-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="b6701-288">Recebendo a resposta como uma cadeia de caracteres JSON.</span><span class="sxs-lookup"><span data-stu-id="b6701-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="b6701-289">Desserializar a resposta e passar a **previsão** resultante para a classe **SceneOrganiser** , que cuidará de como a resposta deve ser exibida.</span><span class="sxs-lookup"><span data-stu-id="b6701-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="b6701-290">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="b6701-290">To create this class:</span></span>

1.  <span data-ttu-id="b6701-291">Clique com o botão direito do mouse na **pasta ativo**, localizada no **painel Projeto**, e clique em **criar** > **pasta**.</span><span class="sxs-lookup"><span data-stu-id="b6701-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="b6701-292">Chame os **scripts**da pasta.</span><span class="sxs-lookup"><span data-stu-id="b6701-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="b6701-293">Clique duas vezes na pasta recém-criada para abri-la.</span><span class="sxs-lookup"><span data-stu-id="b6701-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="b6701-294">Clique com o botão direito do mouse dentro da pasta e clique em **criar** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="b6701-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b6701-295">Nomeie o script **CustomVisionAnalyser.**</span><span class="sxs-lookup"><span data-stu-id="b6701-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="b6701-296">Clique duas vezes no novo script **CustomVisionAnalyser** para abri-lo com o **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="b6701-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="b6701-297">Verifique se você tem os seguintes namespaces referenciados na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="b6701-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="b6701-298">Na classe **CustomVisionAnalyser** , adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="b6701-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="b6701-299">Certifique-se de inserir sua **chave de previsão de serviço** na variável **PredictionKey** e seu **ponto de extremidade de previsão** na variável **predictionEndpoint** .</span><span class="sxs-lookup"><span data-stu-id="b6701-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="b6701-300">Você os copiou no [bloco de notas anteriormente, no capítulo 2, etapa 14](#chapter-2---training-your-custom-vision-project).</span><span class="sxs-lookup"><span data-stu-id="b6701-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="b6701-301">O código para **ativo ()** agora precisa ser adicionado para inicializar a variável de instância:</span><span class="sxs-lookup"><span data-stu-id="b6701-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="b6701-302">Adicione a corrotina (com o método estático **GetImageAsByteArray ()** abaixo dela), que obterá os resultados da análise da imagem, capturada pela classe **ImageCapture** .</span><span class="sxs-lookup"><span data-stu-id="b6701-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b6701-303">Na **AnalyseImageCapture** corrotina, há uma chamada para a classe **SceneOrganiser** que você ainda deseja criar.</span><span class="sxs-lookup"><span data-stu-id="b6701-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="b6701-304">Portanto, **deixe essas linhas comentadas por enquanto**.</span><span class="sxs-lookup"><span data-stu-id="b6701-304">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. <span data-ttu-id="b6701-305">Exclua os métodos **Start ()** e **Update ()** , pois eles não serão usados.</span><span class="sxs-lookup"><span data-stu-id="b6701-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="b6701-306">Certifique-se de salvar as alterações no **Visual Studio**antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="b6701-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6701-307">Como mencionado anteriormente, não se preocupe com o código que pode parecer ter um erro, pois você fornecerá mais classes em breve, o que corrigirá esses erros.</span><span class="sxs-lookup"><span data-stu-id="b6701-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="b6701-308">Capítulo 6-criar a classe CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="b6701-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="b6701-309">A classe que você criará agora é a classe **CustomVisionObjects** .</span><span class="sxs-lookup"><span data-stu-id="b6701-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="b6701-310">Esse script contém vários objetos usados por outras classes para serializar e desserializar as chamadas feitas ao Serviço de Visão Personalizada.</span><span class="sxs-lookup"><span data-stu-id="b6701-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="b6701-311">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="b6701-311">To create this class:</span></span>

1.  <span data-ttu-id="b6701-312">Clique com o botão direito do mouse na pasta **scripts** e clique em **criar** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="b6701-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b6701-313">Chame o script **CustomVisionObjects.**</span><span class="sxs-lookup"><span data-stu-id="b6701-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="b6701-314">Clique duas vezes no novo script **CustomVisionObjects** para abri-lo com o **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="b6701-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="b6701-315">Verifique se você tem os seguintes namespaces referenciados na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="b6701-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="b6701-316">Exclua os métodos **Start ()** e **Update ()** dentro da classe **CustomVisionObjects** , essa classe agora deve estar vazia.</span><span class="sxs-lookup"><span data-stu-id="b6701-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="b6701-317">É importante seguir atentamente a próxima instrução.</span><span class="sxs-lookup"><span data-stu-id="b6701-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="b6701-318">Se você colocar as novas declarações de classe dentro da classe **CustomVisionObjects** , receberá erros de compilação no [capítulo 10](#chapter-10---create-the-imagecapture-class), informando que **AnalysisRootObject** e **BoundingBox** não foram encontrados.</span><span class="sxs-lookup"><span data-stu-id="b6701-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="b6701-319">Adicione as seguintes classes *fora* da classe **CustomVisionObjects** .</span><span class="sxs-lookup"><span data-stu-id="b6701-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="b6701-320">Esses objetos são usados pela biblioteca **Newtonsoft** para serializar e desserializar os dados de resposta:</span><span class="sxs-lookup"><span data-stu-id="b6701-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  <span data-ttu-id="b6701-321">Certifique-se de salvar as alterações no **Visual Studio**antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="b6701-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="b6701-322">Capítulo 7-criar a classe SpatialMapping</span><span class="sxs-lookup"><span data-stu-id="b6701-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="b6701-323">Essa classe definirá o **conflito de mapeamento espacial** na cena para que seja possível detectar colisões entre objetos virtuais e objetos reais.</span><span class="sxs-lookup"><span data-stu-id="b6701-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="b6701-324">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="b6701-324">To create this class:</span></span>

1.  <span data-ttu-id="b6701-325">Clique com o botão direito do mouse na pasta **scripts** e clique em **criar** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="b6701-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b6701-326">Chame o script **SpatialMapping.**</span><span class="sxs-lookup"><span data-stu-id="b6701-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="b6701-327">Clique duas vezes no novo script **SpatialMapping** para abri-lo com o **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="b6701-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="b6701-328">Verifique se você tem os seguintes namespaces referenciados acima da classe **SpatialMapping** :</span><span class="sxs-lookup"><span data-stu-id="b6701-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="b6701-329">Em seguida, adicione as seguintes variáveis dentro da classe **SpatialMapping** , acima do método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="b6701-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  <span data-ttu-id="b6701-330">Adicione o **ativo ()** e o **início ()** :</span><span class="sxs-lookup"><span data-stu-id="b6701-330">Add the **Awake()** and **Start()**:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  <span data-ttu-id="b6701-331">Exclua o método **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="b6701-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="b6701-332">Certifique-se de salvar as alterações no **Visual Studio**antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="b6701-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="b6701-333">Capítulo 8-criar a classe GazeCursor</span><span class="sxs-lookup"><span data-stu-id="b6701-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="b6701-334">Essa classe é responsável por configurar o cursor no local correto em espaço real, fazendo uso do **SpatialMappingCollider**, criado no capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="b6701-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="b6701-335">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="b6701-335">To create this class:</span></span>

1.  <span data-ttu-id="b6701-336">Clique com o botão direito do mouse na pasta **scripts** e clique em **criar** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="b6701-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b6701-337">Chamar o script **GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="b6701-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="b6701-338">Clique duas vezes no novo script **GazeCursor** para abri-lo com o **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="b6701-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="b6701-339">Verifique se você tem o seguinte namespace mencionado acima da classe **GazeCursor** :</span><span class="sxs-lookup"><span data-stu-id="b6701-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="b6701-340">Em seguida, adicione a seguinte variável dentro da classe **GazeCursor** , acima do método **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="b6701-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="b6701-341">Atualize o método **Start ()** com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="b6701-341">Update the **Start()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  <span data-ttu-id="b6701-342">Atualize o método **Update ()** com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="b6701-342">Update the **Update()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="b6701-343">Não se preocupe com o erro para a classe **SceneOrganiser** não ser encontrada, você a criará no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="b6701-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="b6701-344">Certifique-se de salvar as alterações no **Visual Studio**antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="b6701-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="b6701-345">Capítulo 9-criar a classe SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="b6701-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="b6701-346">Essa classe irá:</span><span class="sxs-lookup"><span data-stu-id="b6701-346">This class will:</span></span>

-   <span data-ttu-id="b6701-347">Configure a *câmera principal* anexando os componentes apropriados a ela.</span><span class="sxs-lookup"><span data-stu-id="b6701-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="b6701-348">Quando um objeto é detectado, ele será responsável por calcular sua posição no mundo real e colocar um rótulo de **marca** próximo a ele com o **nome de marca**apropriado.</span><span class="sxs-lookup"><span data-stu-id="b6701-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="b6701-349">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="b6701-349">To create this class:</span></span>

1.  <span data-ttu-id="b6701-350">Clique com o botão direito do mouse na pasta **scripts** e clique em **criar** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="b6701-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b6701-351">Nomeie o script **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="b6701-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="b6701-352">Clique duas vezes no novo script **SceneOrganiser** para abri-lo com o **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="b6701-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="b6701-353">Verifique se você tem os seguintes namespaces referenciados acima da classe **SceneOrganiser** :</span><span class="sxs-lookup"><span data-stu-id="b6701-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="b6701-354">Em seguida, adicione as seguintes variáveis dentro da classe **SceneOrganiser** , acima do método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="b6701-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  <span data-ttu-id="b6701-355">Exclua os métodos **Start ()** e **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="b6701-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="b6701-356">Sob as variáveis, adicione o método **ativo ()** , que irá inicializar a classe e configurar a cena.</span><span class="sxs-lookup"><span data-stu-id="b6701-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  <span data-ttu-id="b6701-357">Adicione o método **PlaceAnalysisLabel ()** , que criará *uma instância* do rótulo na cena (que, neste ponto, é invisível para o usuário).</span><span class="sxs-lookup"><span data-stu-id="b6701-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="b6701-358">Ele também coloca o quad (também invisível) em que a imagem é colocada e se sobrepõe ao mundo real.</span><span class="sxs-lookup"><span data-stu-id="b6701-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="b6701-359">Isso é importante porque as coordenadas de caixa recuperadas do serviço após a análise são rastreadas de volta para esse Quad para determinar o local aproximado do objeto no mundo real.</span><span class="sxs-lookup"><span data-stu-id="b6701-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  <span data-ttu-id="b6701-360">Adicione o método **FinaliseLabel ()** .</span><span class="sxs-lookup"><span data-stu-id="b6701-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="b6701-361">É responsável por:</span><span class="sxs-lookup"><span data-stu-id="b6701-361">It is responsible for:</span></span>

    *   <span data-ttu-id="b6701-362">Definindo o texto do *rótulo* com a *marca* da previsão com a maior confiança.</span><span class="sxs-lookup"><span data-stu-id="b6701-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="b6701-363">Chamar o cálculo da *caixa* delimitadora no objeto Quad, posicionado anteriormente e colocar o rótulo na cena.</span><span class="sxs-lookup"><span data-stu-id="b6701-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="b6701-364">Ajuste da profundidade do rótulo usando um Raycast em direção à *caixa*delimitadora, que deve colidir com o objeto no mundo real.</span><span class="sxs-lookup"><span data-stu-id="b6701-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="b6701-365">Redefinição do processo de captura para permitir que o usuário Capture outra imagem.</span><span class="sxs-lookup"><span data-stu-id="b6701-365">Resetting the capture process to allow the user to capture another image.</span></span>

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  <span data-ttu-id="b6701-366">Adicione o método **CalculateBoundingBoxPosition ()** , que hospeda vários cálculos necessários para converter as coordenadas da *caixa* delimitadora recuperadas do serviço e recriá-las proporcionalmente no Quad.</span><span class="sxs-lookup"><span data-stu-id="b6701-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. <span data-ttu-id="b6701-367">Certifique-se de salvar as alterações no **Visual Studio**antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="b6701-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b6701-368">Antes de continuar, abra a classe **CustomVisionAnalyser** e, dentro do método **AnalyseLastImageCaptured ()** , *remova os comentários* das seguintes linhas:</span><span class="sxs-lookup"><span data-stu-id="b6701-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> <span data-ttu-id="b6701-369">Não se preocupe com a mensagem "não foi possível encontrar a classe **ImageCapture** ", você a criará no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="b6701-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="b6701-370">Capítulo 10 – criar a classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="b6701-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="b6701-371">A próxima classe que você vai criar é a classe **ImageCapture** .</span><span class="sxs-lookup"><span data-stu-id="b6701-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="b6701-372">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="b6701-372">This class is responsible for:</span></span>

*   <span data-ttu-id="b6701-373">Capturando uma imagem usando a câmera do HoloLens e armazenando-a na pasta do *aplicativo* .</span><span class="sxs-lookup"><span data-stu-id="b6701-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="b6701-374">Lidando com gestos de *toque* do usuário.</span><span class="sxs-lookup"><span data-stu-id="b6701-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="b6701-375">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="b6701-375">To create this class:</span></span>

1.  <span data-ttu-id="b6701-376">Vá para a pasta **scripts** que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b6701-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="b6701-377">Clique com o botão direito do mouse dentro da pasta e clique em **criar** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="b6701-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b6701-378">Nomeie o script **ImageCapture**.</span><span class="sxs-lookup"><span data-stu-id="b6701-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="b6701-379">Clique duas vezes no novo script **ImageCapture** para abri-lo com o **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="b6701-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="b6701-380">Substitua os namespaces na parte superior do arquivo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="b6701-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="b6701-381">Em seguida, adicione as seguintes variáveis dentro da classe **ImageCapture** , acima do método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="b6701-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="b6701-382">O código para os métodos **ativo ()** e **Iniciar ()** agora precisa ser adicionado:</span><span class="sxs-lookup"><span data-stu-id="b6701-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="b6701-383">Implemente um manipulador que será chamado quando ocorrer um gesto de toque:</span><span class="sxs-lookup"><span data-stu-id="b6701-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="b6701-384">Quando o cursor estiver **verde**, isso significa que a câmera está disponível para tirar a imagem.</span><span class="sxs-lookup"><span data-stu-id="b6701-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="b6701-385">Quando o cursor estiver **vermelho**, significa que a câmera está ocupada.</span><span class="sxs-lookup"><span data-stu-id="b6701-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="b6701-386">Adicione o método que o aplicativo usa para iniciar o processo de captura de imagem e armazenar a imagem:</span><span class="sxs-lookup"><span data-stu-id="b6701-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  <span data-ttu-id="b6701-387">Adicione os manipuladores que serão chamados quando a foto tiver sido capturada e quando ela estiver pronta para ser analisada.</span><span class="sxs-lookup"><span data-stu-id="b6701-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="b6701-388">O resultado é passado para o **CustomVisionAnalyser** para análise.</span><span class="sxs-lookup"><span data-stu-id="b6701-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="b6701-389">Certifique-se de salvar as alterações no **Visual Studio**antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="b6701-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="b6701-390">Capítulo 11-Configurando os scripts na cena</span><span class="sxs-lookup"><span data-stu-id="b6701-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="b6701-391">Agora que você escreveu todo o código necessário para esse projeto, é hora de configurar os scripts na cena e, no pré-fabricados, para que eles se comportem corretamente.</span><span class="sxs-lookup"><span data-stu-id="b6701-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="b6701-392">No **Editor do Unity**, no **painel hierarquia**, selecione a **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="b6701-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="b6701-393">No **painel Inspetor**, com a **câmera principal** selecionada, clique em **Adicionar componente**, em seguida, procure o script **SceneOrganiser** e clique duas vezes para adicioná-lo.</span><span class="sxs-lookup"><span data-stu-id="b6701-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="b6701-394">No **painel Projeto**, abra a **pasta pré-fabricados**, arraste o **rótulo** pré-fabricado para a área de entrada destino de referência vazia do *rótulo* , no script **SceneOrganiser** que você acabou de adicionar à *câmera principal*, conforme mostrado na a imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="b6701-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="b6701-395">No **painel hierarquia**, selecione o filho **GazeCursor** da **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="b6701-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="b6701-396">No **painel Inspetor**, com o **GazeCursor** selecionado, clique em **Adicionar componente**, em seguida, pesquise por **GazeCursor** script e clique duas vezes para adicioná-lo.</span><span class="sxs-lookup"><span data-stu-id="b6701-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="b6701-397">Novamente, no **painel hierarquia**, selecione o filho **SpatialMapping** da **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="b6701-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="b6701-398">No **painel Inspetor**, com o **SpatialMapping** selecionado, clique em **Adicionar componente**, em seguida, pesquise por **SpatialMapping** script e clique duas vezes para adicioná-lo.</span><span class="sxs-lookup"><span data-stu-id="b6701-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="b6701-399">Os scripts restantes que você não tiver definido serão adicionados pelo código no script **SceneOrganiser** , durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b6701-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="b6701-400">Capítulo 12 – antes de Compilar</span><span class="sxs-lookup"><span data-stu-id="b6701-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="b6701-401">Para executar um teste completo de seu aplicativo, você precisará Sideload-lo no Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b6701-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="b6701-402">Antes de fazer isso, verifique se:</span><span class="sxs-lookup"><span data-stu-id="b6701-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="b6701-403">Todas as configurações mencionadas no [capítulo 3](#chapter-3---set-up-the-unity-project) estão definidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="b6701-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="b6701-404">O script **SceneOrganiser** é anexado ao objeto da **câmera principal** .</span><span class="sxs-lookup"><span data-stu-id="b6701-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="b6701-405">O script **GazeCursor** é anexado ao objeto **GazeCursor** .</span><span class="sxs-lookup"><span data-stu-id="b6701-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="b6701-406">O script **SpatialMapping** é anexado ao objeto **SpatialMapping** .</span><span class="sxs-lookup"><span data-stu-id="b6701-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="b6701-407">No [capítulo 5](#chapter-5---create-the-customvisionanalyser-class), etapa 6:</span><span class="sxs-lookup"><span data-stu-id="b6701-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="b6701-408">Certifique-se de inserir sua **chave de previsão de serviço** na variável **predictionKey** .</span><span class="sxs-lookup"><span data-stu-id="b6701-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="b6701-409">Você inseriu o **ponto de extremidade de previsão** na classe **predictionEndpoint** .</span><span class="sxs-lookup"><span data-stu-id="b6701-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="b6701-410">Capítulo 13-criar a solução UWP e Sideload seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="b6701-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="b6701-411">Agora você está pronto para compilar seu aplicativo como uma solução UWP que você poderá implantar no Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b6701-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="b6701-412">Para iniciar o processo de compilação:</span><span class="sxs-lookup"><span data-stu-id="b6701-412">To begin the build process:</span></span>

1.  <span data-ttu-id="b6701-413">Vá para **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="b6701-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="b6701-414">**Projetos em tique\# Unity C**.</span><span class="sxs-lookup"><span data-stu-id="b6701-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="b6701-415">Clique em **Adicionar cenas de abertura**.</span><span class="sxs-lookup"><span data-stu-id="b6701-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="b6701-416">Isso adicionará a cena aberta no momento à compilação.</span><span class="sxs-lookup"><span data-stu-id="b6701-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="b6701-417">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="b6701-417">Click **Build**.</span></span> <span data-ttu-id="b6701-418">O Unity iniciará uma janela *Explorador de arquivos* , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado.</span><span class="sxs-lookup"><span data-stu-id="b6701-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="b6701-419">Crie essa pasta agora e nomeie-a como **aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="b6701-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="b6701-420">Em seguida, com a pasta de **aplicativo** selecionada, clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="b6701-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="b6701-421">O Unity começará a criar seu projeto na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="b6701-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="b6701-422">Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).</span><span class="sxs-lookup"><span data-stu-id="b6701-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="b6701-423">Para implantar o no Microsoft HoloLens, você precisará do endereço IP desse dispositivo (para implantação remota) e para garantir que ele também tenha o **modo de desenvolvedor** definido.</span><span class="sxs-lookup"><span data-stu-id="b6701-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="b6701-424">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="b6701-424">To do this:</span></span>

    1.  <span data-ttu-id="b6701-425">Enquanto estiver desgastando seu HoloLens, abra as **configurações**.</span><span class="sxs-lookup"><span data-stu-id="b6701-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="b6701-426">Vá para **rede &**  > **Opções avançadas** **de Internet Wi-Fi** > </span><span class="sxs-lookup"><span data-stu-id="b6701-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="b6701-427">Anote o endereço **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="b6701-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="b6701-428">Em seguida, navegue de volta para **configurações**e, em seguida, para **Atualizar & segurança** > **para desenvolvedores**</span><span class="sxs-lookup"><span data-stu-id="b6701-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="b6701-429">Defina o **modo de desenvolvedor** *em*.</span><span class="sxs-lookup"><span data-stu-id="b6701-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="b6701-430">Navegue até sua nova compilação do Unity (a pasta do **aplicativo** ) e abra o arquivo de solução com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b6701-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="b6701-431">Na configuração da solução, selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="b6701-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="b6701-432">Na plataforma da solução, selecione **x86, computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="b6701-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="b6701-433">Você será solicitado a inserir o **endereço IP** de um dispositivo remoto (o Microsoft HoloLens, neste caso, que você anotou).</span><span class="sxs-lookup"><span data-stu-id="b6701-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="b6701-434">Vá para o menu **Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b6701-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="b6701-435">Seu aplicativo agora deve aparecer na lista de aplicativos instalados no Microsoft HoloLens, pronto para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="b6701-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="b6701-436">Para usar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="b6701-436">To use the application:</span></span>

* <span data-ttu-id="b6701-437">Examine um objeto, que você tem treinado com sua **serviço de visão personalizada do Azure, detecção de objetos**e use o **gesto de toque**.</span><span class="sxs-lookup"><span data-stu-id="b6701-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="b6701-438">Se o objeto for detectado com êxito, um *texto de rótulo* de espaço mundial será exibido com o nome da marca.</span><span class="sxs-lookup"><span data-stu-id="b6701-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6701-439">Sempre que você captura uma foto e a envia para o serviço, pode voltar para a página de serviço e treinar novamente o serviço com as imagens recentemente capturadas.</span><span class="sxs-lookup"><span data-stu-id="b6701-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="b6701-440">No início, você provavelmente também precisará corrigir as *caixas* delimitadores para ser mais preciso e treinar novamente o serviço.</span><span class="sxs-lookup"><span data-stu-id="b6701-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="b6701-441">O texto do rótulo colocado pode não aparecer próximo ao objeto quando os sensores do Microsoft HoloLens e/ou o SpatialTrackingComponent no Unity falharem em colocar os colisor apropriados, em relação aos objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="b6701-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="b6701-442">Tente usar o aplicativo em uma superfície diferente, se esse for o caso.</span><span class="sxs-lookup"><span data-stu-id="b6701-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="b6701-443">Seu Visão Personalizada, aplicativo de detecção de objeto</span><span class="sxs-lookup"><span data-stu-id="b6701-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="b6701-444">Parabéns, você criou um aplicativo de realidade misturada que aproveita o Visão Personalizada do Azure, a API de detecção de objeto, que pode reconhecer um objeto de uma imagem e, em seguida, fornecer uma posição aproximada para esse objeto no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="b6701-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b6701-445">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="b6701-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="b6701-446">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="b6701-446">Exercise 1</span></span>

<span data-ttu-id="b6701-447">Adicionando ao rótulo de texto, use um cubo semitransparente para encapsular o objeto real em uma *caixa*delimitadora 3D.</span><span class="sxs-lookup"><span data-stu-id="b6701-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="b6701-448">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="b6701-448">Exercise 2</span></span>

<span data-ttu-id="b6701-449">Treine sua Serviço de Visão Personalizada para reconhecer mais objetos.</span><span class="sxs-lookup"><span data-stu-id="b6701-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="b6701-450">Exercício 3</span><span class="sxs-lookup"><span data-stu-id="b6701-450">Exercise 3</span></span>

<span data-ttu-id="b6701-451">Tocar um som quando um objeto for reconhecido.</span><span class="sxs-lookup"><span data-stu-id="b6701-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="b6701-452">Exercício 4</span><span class="sxs-lookup"><span data-stu-id="b6701-452">Exercise 4</span></span>

<span data-ttu-id="b6701-453">Use a API para treinar novamente seu serviço com as mesmas imagens que seu aplicativo está analisando, para tornar o serviço mais preciso (faça a previsão e o treinamento simultaneamente).</span><span class="sxs-lookup"><span data-stu-id="b6701-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
