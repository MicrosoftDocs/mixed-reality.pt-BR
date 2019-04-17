---
title: MR e Azure 310 - detecção de objetos
description: Conclua este curso para aprender a treinar um modelo de aprendizado de máquina e, em seguida, use o modelo treinado para reconhecer objetos semelhantes e sua posição no mundo real de dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, visão personalizada, detecção, misto realidade, academy, unity, tutorial, api, hololens do objeto
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589102"
---
>[!NOTE]
><span data-ttu-id="f0b62-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="f0b62-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f0b62-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f0b62-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f0b62-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="f0b62-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f0b62-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="f0b62-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f0b62-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f0b62-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f0b62-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="f0b62-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="f0b62-110">MR e o Azure 310: Detecção de objetos</span><span class="sxs-lookup"><span data-stu-id="f0b62-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="f0b62-111">Neste curso, você aprenderá a reconhecer conteúdo visual personalizado e sua posição espacial dentro de uma imagem fornecida, usando a visão personalizada do Azure os recursos de "Detecção de objeto" em um aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="f0b62-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="f0b62-112">Esse serviço permitirá que você treinar um modelo de aprendizado de máquina usando imagens de objeto.</span><span class="sxs-lookup"><span data-stu-id="f0b62-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="f0b62-113">Você usará o modelo treinado para reconhecer objetos semelhantes e aproximar de sua localização no mundo real, conforme fornecido pela captura de câmera do Microsoft HoloLens ou conecte-se de uma câmera em um PC para fones imersivos em exposição (VR).</span><span class="sxs-lookup"><span data-stu-id="f0b62-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![resultado do curso](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="f0b62-115">**Visão personalizada do Azure, detecção de objetos** é um Service Microsoft que permite aos desenvolvedores criar classificadores de imagem personalizada.</span><span class="sxs-lookup"><span data-stu-id="f0b62-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="f0b62-116">Os classificadores, em seguida, podem ser usados com novas imagens para detectar objetos dentro dessa nova imagem, fornecendo **limites da caixa** dentro da imagem em si.</span><span class="sxs-lookup"><span data-stu-id="f0b62-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="f0b62-117">O serviço fornece um portal simple, fácil de usar on-line para simplificar esse processo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="f0b62-118">Para obter mais informações, visite os links a seguir:</span><span class="sxs-lookup"><span data-stu-id="f0b62-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="f0b62-119">Página de visão personalizada do Azure</span><span class="sxs-lookup"><span data-stu-id="f0b62-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="f0b62-120">Limites e cotas</span><span class="sxs-lookup"><span data-stu-id="f0b62-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="f0b62-121">Após a conclusão deste curso, você terá um aplicativo de realidade mista que serão capaz de fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f0b62-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="f0b62-122">O usuário será capaz *olhares* em um objeto, que têm treinados usando o serviço do Azure personalizado da pesquisa Visual computacional, detecção de objetos.</span><span class="sxs-lookup"><span data-stu-id="f0b62-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="f0b62-123">O usuário usará o *toque* gesto para capturar uma imagem de que eles estão observando.</span><span class="sxs-lookup"><span data-stu-id="f0b62-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="f0b62-124">O aplicativo enviará a imagem para o serviço de visão personalizada do Azure.</span><span class="sxs-lookup"><span data-stu-id="f0b62-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="f0b62-125">Haverá uma resposta do serviço que exibe o resultado de reconhecimento como texto de espaço de mundo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="f0b62-126">Isso será realizado por meio da utilização espacial rastreando dos o Microsoft HoloLens, como uma maneira de Noções básicas sobre a posição do mundo do objeto reconhecido e, em seguida, usando o *marca* associado com o que é detectado como na imagem, Forneça o texto do rótulo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="f0b62-127">O curso também discutirá manualmente carregar imagens, criação de marcas, e treinamento do serviço, reconhecer diferentes objetos (no exemplo fornecido, uma xícara), por definir a *caixa limite* dentro da imagem que você enviar.</span><span class="sxs-lookup"><span data-stu-id="f0b62-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="f0b62-128">Após a criação e uso do aplicativo, o desenvolvedor deve navegar de volta para o Azure serviço personalizado de visão, identificar as previsões feitas pelo serviço e determinar se eles estavam corretos ou não (por meio de marcação nada o serviço perdido, e ajustando o *caixas delimitadoras*).</span><span class="sxs-lookup"><span data-stu-id="f0b62-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="f0b62-129">O serviço pode, em seguida, ser treinado outra vez, que aumenta a probabilidade de ele reconhecer os objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="f0b62-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="f0b62-130">Este curso ensinará você a obter os resultados com o Azure serviço personalizado de visão, detecção de objetos em um aplicativo de exemplo com base no Unity.</span><span class="sxs-lookup"><span data-stu-id="f0b62-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="f0b62-131">Ele será cabe a você aplicar esses conceitos para um aplicativo personalizado que você pode criar.</span><span class="sxs-lookup"><span data-stu-id="f0b62-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="f0b62-132">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="f0b62-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f0b62-133">Curso</span><span class="sxs-lookup"><span data-stu-id="f0b62-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f0b62-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f0b62-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f0b62-135"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="f0b62-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="f0b62-136">MR e o Azure 310: Detecção de objetos</span><span class="sxs-lookup"><span data-stu-id="f0b62-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="f0b62-137">✔️</span><span class="sxs-lookup"><span data-stu-id="f0b62-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="f0b62-138">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f0b62-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="f0b62-139">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="f0b62-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="f0b62-140">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (julho de 2018).</span><span class="sxs-lookup"><span data-stu-id="f0b62-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="f0b62-141">Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que está listado abaixo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="f0b62-142">Recomendamos que o hardware e software para este curso a seguir:</span><span class="sxs-lookup"><span data-stu-id="f0b62-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="f0b62-143">Um computador de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="f0b62-143">A development PC</span></span>
- [<span data-ttu-id="f0b62-144">Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="f0b62-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="f0b62-145">O SDK mais recente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="f0b62-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="f0b62-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="f0b62-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="f0b62-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f0b62-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="f0b62-148">Um [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="f0b62-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="f0b62-149">Acesso à Internet para a instalação do Azure e a recuperação de serviço de visão personalizada</span><span class="sxs-lookup"><span data-stu-id="f0b62-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="f0b62-150">Uma série de imagens pelo menos quinze (15) são necessários) para cada objeto que você gostaria de visão personalizada para reconhecer.</span><span class="sxs-lookup"><span data-stu-id="f0b62-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="f0b62-151">Se desejar, você pode usar as imagens que já é fornecidas com este curso [uma série de cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="f0b62-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="f0b62-152">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="f0b62-152">Before you start</span></span>

1.  <span data-ttu-id="f0b62-153">Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="f0b62-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="f0b62-154">Configurar e testar o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f0b62-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="f0b62-155">Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="f0b62-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="f0b62-156">É uma boa ideia executar calibragem e ajuste de Sensor ao começar a desenvolver um new App HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="f0b62-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="f0b62-157">Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="f0b62-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="f0b62-158">Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="f0b62-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="f0b62-159">Capítulo 1 - o Portal de visão personalizada</span><span class="sxs-lookup"><span data-stu-id="f0b62-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="f0b62-160">Para usar o **serviço de visão personalizada do Azure**, você precisará configurar uma instância para ficar disponível para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="f0b62-161">Navegue [para o **serviço personalizado de visão** página principal](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="f0b62-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="f0b62-162">Clique em **Introdução ao**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="f0b62-163">Entre Portal de visão personalizada.</span><span class="sxs-lookup"><span data-stu-id="f0b62-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="f0b62-164">Se você ainda não tiver uma conta do Azure, você precisará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="f0b62-165">Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="f0b62-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="f0b62-166">Quando você estiver conectado pela primeira vez, você será solicitado com o *termos de serviço* painel.</span><span class="sxs-lookup"><span data-stu-id="f0b62-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="f0b62-167">Clique na caixa de seleção para *concordar com os termos*.</span><span class="sxs-lookup"><span data-stu-id="f0b62-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="f0b62-168">Em seguida, clique em **concordo**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="f0b62-169">Tendo concordou com os termos, agora você está no *meus projetos* seção.</span><span class="sxs-lookup"><span data-stu-id="f0b62-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="f0b62-170">Clique em **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="f0b62-171">Uma guia aparecerá no lado direito, que solicitará que você especifique alguns campos para o projeto.</span><span class="sxs-lookup"><span data-stu-id="f0b62-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="f0b62-172">Insira um nome para seu projeto</span><span class="sxs-lookup"><span data-stu-id="f0b62-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="f0b62-173">Insira uma descrição para o seu projeto (**opcional**)</span><span class="sxs-lookup"><span data-stu-id="f0b62-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="f0b62-174">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f0b62-175">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="f0b62-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f0b62-176">É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="f0b62-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="f0b62-177">Se você quiser [Leia mais sobre grupos de recursos do Azure, navegue até os documentos associados](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="f0b62-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="f0b62-178">Defina as **tipos de projeto** como **detecção de objetos (visualização)**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="f0b62-179">Quando tiver terminado, clique em **criar projeto**, e você será redirecionado para a página do projeto de serviço personalizado de visão.</span><span class="sxs-lookup"><span data-stu-id="f0b62-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="f0b62-180">Capítulo 2 - treinamento de seu projeto de visão personalizada</span><span class="sxs-lookup"><span data-stu-id="f0b62-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="f0b62-181">Uma vez no Portal da pesquisa Visual computacional personalizado, seu principal objetivo é treinar seu projeto para reconhecer a objetos específicos em imagens.</span><span class="sxs-lookup"><span data-stu-id="f0b62-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="f0b62-182">Você precisa de pelo menos 15 (15) imagens para cada objeto que você deseja que seu aplicativo reconheça.</span><span class="sxs-lookup"><span data-stu-id="f0b62-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="f0b62-183">Você pode usar as imagens fornecidas com este curso ([uma série de cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="f0b62-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="f0b62-184">Para treinar seu projeto de visão personalizada:</span><span class="sxs-lookup"><span data-stu-id="f0b62-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="f0b62-185">Clique no **+** lado **marcas**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="f0b62-186">Adicionar um **nome** da marca que será usada para associar suas imagens com.</span><span class="sxs-lookup"><span data-stu-id="f0b62-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="f0b62-187">Neste exemplo estamos usando imagens do cups para reconhecimento, portanto, ter chamado a marca para isso, **Cup**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="f0b62-188">Clique em **salvar** após a conclusão.</span><span class="sxs-lookup"><span data-stu-id="f0b62-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="f0b62-189">Você notará sua **marca** foi adicionado (talvez seja necessário recarregar a página para que ele seja exibido).</span><span class="sxs-lookup"><span data-stu-id="f0b62-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="f0b62-190">Clique em **adicionar imagens** no centro da página.</span><span class="sxs-lookup"><span data-stu-id="f0b62-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="f0b62-191">Clique em **procurar arquivos locais**e navegue para as imagens que você gostaria de carregar um objeto, com sendo a mínima quinze (15).</span><span class="sxs-lookup"><span data-stu-id="f0b62-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="f0b62-192">Você pode selecionar várias imagens por vez, para carregar.</span><span class="sxs-lookup"><span data-stu-id="f0b62-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="f0b62-193">Pressione **carregar arquivos** depois de selecionar todas as imagens você deseja treinar o projeto com.</span><span class="sxs-lookup"><span data-stu-id="f0b62-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="f0b62-194">Os arquivos de começar a carregar.</span><span class="sxs-lookup"><span data-stu-id="f0b62-194">The files will begin uploading.</span></span> <span data-ttu-id="f0b62-195">Depois que você tiver a confirmação do upload, clique em **feito**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="f0b62-196">Neste ponto suas imagens são carregadas, mas não estão marcadas.</span><span class="sxs-lookup"><span data-stu-id="f0b62-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="f0b62-197">Para marcar as imagens, use o mouse.</span><span class="sxs-lookup"><span data-stu-id="f0b62-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="f0b62-198">Quando você focaliza sua imagem, um realce de seleção auxiliará desenhando automaticamente uma seleção em torno de seu objeto.</span><span class="sxs-lookup"><span data-stu-id="f0b62-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="f0b62-199">Se não estiverem corretas, você pode desenhar seus próprios.</span><span class="sxs-lookup"><span data-stu-id="f0b62-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="f0b62-200">Isso é feito segurando o botão esquerdo do mouse no mouse e, em seguida, arrastando a região de seleção para abranger o seu objeto.</span><span class="sxs-lookup"><span data-stu-id="f0b62-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="f0b62-201">Após a seleção do objeto dentro da imagem, um pequeno prompt pedirá para você *Adicionar marca de região*.</span><span class="sxs-lookup"><span data-stu-id="f0b62-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="f0b62-202">Selecione sua marca criada anteriormente ('Cup', no exemplo acima), ou se você estiver adicionando mais marcas, digitar isso em e clique no **+ (adição)** botão.</span><span class="sxs-lookup"><span data-stu-id="f0b62-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="f0b62-203">Para marcar a imagem a seguir, que você pode clicar na seta à direita da folha ou feche a folha de marca (clicando o **X** no canto superior direito da folha) e, em seguida, clique na imagem a próxima.</span><span class="sxs-lookup"><span data-stu-id="f0b62-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="f0b62-204">Depois que a próxima imagem pronta, repita o mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="f0b62-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="f0b62-205">Faça isso para todas as imagens que você carregou, até que eles estão marcados.</span><span class="sxs-lookup"><span data-stu-id="f0b62-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="f0b62-206">Você pode selecionar vários objetos na mesma imagem, como a imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="f0b62-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="f0b62-207">Depois que você tiver marcado todos eles, clique no **marcadas** botão à esquerda da tela, para revelar as imagens marcadas.</span><span class="sxs-lookup"><span data-stu-id="f0b62-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="f0b62-208">Agora você está pronto para treinar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="f0b62-208">You are now ready to train your Service.</span></span> <span data-ttu-id="f0b62-209">Clique o **Train** botão e a primeira iteração de treinamento serão iniciada.</span><span class="sxs-lookup"><span data-stu-id="f0b62-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="f0b62-210">Depois que ele é criado, você poderá ver dois botões chamados **tornar padrão** e **URL de previsão**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="f0b62-211">Clique em **tornar padrão** pela primeira vez, em seguida, clique em **URL de previsão**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="f0b62-212">O ponto de extremidade que é fornecido a partir disso, é definido como o que ocorrer *iteração* foi marcada como padrão.</span><span class="sxs-lookup"><span data-stu-id="f0b62-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="f0b62-213">Como tal, se você fizer um novo mais tarde *iteração* e atualizá-lo como padrão, você não precisará alterar seu código.</span><span class="sxs-lookup"><span data-stu-id="f0b62-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="f0b62-214">Depois de clicar em **URL de previsão**, abra *bloco de notas*e copie e cole o **URL** (também chamado de seu **ponto de extremidade de previsão**) e o **chave do serviço previsão**, de modo que você pode recuperá-la quando precisar dele posteriormente no código.</span><span class="sxs-lookup"><span data-stu-id="f0b62-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="f0b62-215">Capítulo 3 - configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="f0b62-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="f0b62-216">A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="f0b62-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="f0b62-217">Abra **Unity** e clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="f0b62-218">Agora, você precisará fornecer um nome de projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="f0b62-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="f0b62-219">Inserir **CustomVisionObjDetection**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="f0b62-220">Verifique se o tipo de projeto é definido como **3D**e defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="f0b62-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="f0b62-221">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="f0b62-222">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="f0b62-223">Vá para **edite* > *preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="f0b62-224">Alteração **Editor de Script externo** à **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="f0b62-225">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="f0b62-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="f0b62-226">Em seguida, vá para **arquivo > configurações de Build** e alterne os **plataforma** para *plataforma Universal do Windows*e, em seguida, clicando no **alternar plataforma** botão.</span><span class="sxs-lookup"><span data-stu-id="f0b62-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="f0b62-227">No mesmo **configurações de Build** janela, verifique se a seguir está definida:</span><span class="sxs-lookup"><span data-stu-id="f0b62-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="f0b62-228">**Dispositivo de destino** é definido como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="f0b62-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="f0b62-229">**Tipo de compilação** é definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="f0b62-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="f0b62-230">**SDK** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="f0b62-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="f0b62-231">**Versão do Visual Studio** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="f0b62-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="f0b62-232">**Compilar e executar** é definido como **Máquina Local**</span><span class="sxs-lookup"><span data-stu-id="f0b62-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="f0b62-233">O restante de configurações, em **configurações de Build**, deverá ser deixado como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="f0b62-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="f0b62-234">No mesmo **configurações de Build** janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o **Inspetor** está localizado.</span><span class="sxs-lookup"><span data-stu-id="f0b62-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="f0b62-235">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="f0b62-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="f0b62-236">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="f0b62-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="f0b62-237">**Versão de tempo de execução de scripts** deve ser **Experimental** (equivalente ao .NET 4.6), que irá disparar uma necessidade de reiniciar o Editor.</span><span class="sxs-lookup"><span data-stu-id="f0b62-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="f0b62-238">**Script de back-end** deve ser **.NET**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="f0b62-239">**Nível de compatibilidade de API** deve ser **.NET 4.6**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="f0b62-240">Dentro de **configurações de publicação** guia, em **recursos**, verifique:</span><span class="sxs-lookup"><span data-stu-id="f0b62-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="f0b62-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="f0b62-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="f0b62-242">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="f0b62-242">**Webcam**</span></span>

        3. <span data-ttu-id="f0b62-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="f0b62-243">**SpatialPerception**</span></span>

            <span data-ttu-id="f0b62-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="f0b62-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="f0b62-245">Mais para baixo no painel, no **XR configurações** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se da **misto do Windows Realidade SDK** é adicionado.</span><span class="sxs-lookup"><span data-stu-id="f0b62-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="f0b62-246">Volta **configurações de Build**, *Unity C\# projetos* não fica acinzentado: marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="f0b62-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="f0b62-247">Fechar o **configurações de Build** janela.</span><span class="sxs-lookup"><span data-stu-id="f0b62-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="f0b62-248">No **Editor**, clique em **editar** > **configurações do projeto** > **gráficos**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="f0b62-249">No **painel Inspetor** as *configurações de gráficos* será aberta.</span><span class="sxs-lookup"><span data-stu-id="f0b62-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="f0b62-250">Role para baixo até ver uma matriz chamada **sempre incluem sombreadores**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="f0b62-251">Adicionar um slot, aumentando a **tamanho** variável por um (neste exemplo, fosse 8 então o definimos-9).</span><span class="sxs-lookup"><span data-stu-id="f0b62-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="f0b62-252">Um novo slot será exibida, na última posição da matriz, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="f0b62-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="f0b62-253">No slot, clique no círculo ao lado do slot para abrir uma lista de sombreadores de destino menores.</span><span class="sxs-lookup"><span data-stu-id="f0b62-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="f0b62-254">Procure os **herdado sombreadores, Transparent/difusa** sombreador e clique duas vezes nele.</span><span class="sxs-lookup"><span data-stu-id="f0b62-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="f0b62-255">Capítulo 4 - importar o pacote do CustomVisionObjDetection Unity</span><span class="sxs-lookup"><span data-stu-id="f0b62-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="f0b62-256">Para este curso, você receberá um pacote do Unity Asset denominada **Azure-MR-310.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="f0b62-257">[DICA] Todos os objetos compatíveis com o Unity, incluindo o plano inteiro, podem ser empacotados em um **unitypackage** arquivo e exportado / importado em outros projetos.</span><span class="sxs-lookup"><span data-stu-id="f0b62-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="f0b62-258">É a maneira mais segura e mais eficiente, mover ativos entre diferentes **projetos do Unity**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="f0b62-259">Você pode encontrar o [pacote Azure-MR-310 que você precisa baixar aqui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="f0b62-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="f0b62-260">Com o painel do Unity na sua frente, clique em **ativos** no menu na parte superior da tela, em seguida, clique em **Importar pacote > pacote personalizado**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="f0b62-261">Use o seletor de arquivos para selecionar o **Azure-MR-310.unitypackage** de pacote e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="f0b62-262">Uma lista de componentes para esse ativo será exibida para você.</span><span class="sxs-lookup"><span data-stu-id="f0b62-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="f0b62-263">Confirme a importação clicando o **importação** botão.</span><span class="sxs-lookup"><span data-stu-id="f0b62-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="f0b62-264">Quando tiver terminado a importação, você observará que pastas do pacote agora foram adicionadas ao seu **ativos** pasta.</span><span class="sxs-lookup"><span data-stu-id="f0b62-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="f0b62-265">Esse tipo de estrutura de pastas é típico para um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="f0b62-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="f0b62-266">O **materiais** pasta contém o material usado pelas **olhares Cursor**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="f0b62-267">O **plug-ins** pasta contém a DLL da Newtonsoft usado pelo código para desserializar a resposta do serviço web.</span><span class="sxs-lookup"><span data-stu-id="f0b62-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="f0b62-268">Dois (2) versões diferentes contidas na pasta e subpasta, são necessárias para permitir que a biblioteca a ser usado e compilados pelo Editor do Unity e o build UWP.</span><span class="sxs-lookup"><span data-stu-id="f0b62-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="f0b62-269">O **pré-fabricados** pasta contém os pré-fabricados contidos na cena.</span><span class="sxs-lookup"><span data-stu-id="f0b62-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="f0b62-270">Eles são:</span><span class="sxs-lookup"><span data-stu-id="f0b62-270">Those are:</span></span>

        1.  <span data-ttu-id="f0b62-271">O **GazeCursor**, o cursor usado no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="f0b62-272">Funcionará junto com pré-fabricado SpatialMapping para poder ser colocado na cena na parte superior de objetos físicos.</span><span class="sxs-lookup"><span data-stu-id="f0b62-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="f0b62-273">O **rótulo**, que é o objeto de interface do usuário usado para exibir a marca de objeto na cena quando necessário.</span><span class="sxs-lookup"><span data-stu-id="f0b62-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="f0b62-274">O **SpatialMapping**, que é o objeto que permite que o aplicativo use criar um mapa virtual, usando o rastreamento de espacial dos o Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f0b62-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="f0b62-275">O **cenas** pasta que contém atualmente a cena pré-criados para este curso.</span><span class="sxs-lookup"><span data-stu-id="f0b62-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="f0b62-276">Abra o **cenas** pasta, no **painel projeto**e clique duas vezes no **ObjDetectionScene**, para carregar a cena que você usará para este curso.</span><span class="sxs-lookup"><span data-stu-id="f0b62-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="f0b62-277">**Nenhum código foi incluído**, você irá escrever o código seguindo este curso.</span><span class="sxs-lookup"><span data-stu-id="f0b62-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="f0b62-278">Capítulo 5 - criar a classe CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="f0b62-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="f0b62-279">Neste ponto, você está pronto para escrever um código.</span><span class="sxs-lookup"><span data-stu-id="f0b62-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="f0b62-280">Você começará com o **CustomVisionAnalyser** classe.</span><span class="sxs-lookup"><span data-stu-id="f0b62-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="f0b62-281">As chamadas para o **serviço personalizado de visão**, no código mostrado abaixo, são feitas usando o **API de REST de visão personalizada**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="f0b62-282">Usando isso, você verá como implementar e usar essa API (útil para entender como implementar algo semelhante em seu próprio).</span><span class="sxs-lookup"><span data-stu-id="f0b62-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="f0b62-283">Lembre-se que a Microsoft oferece uma **SDK de visão personalizada** que também pode ser usado para fazer chamadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f0b62-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="f0b62-284">Para obter mais informações, visite o [artigo do SDK de visão personalizada](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span><span class="sxs-lookup"><span data-stu-id="f0b62-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="f0b62-285">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="f0b62-285">This class is responsible for:</span></span>

- <span data-ttu-id="f0b62-286">Carregando a imagem mais recente capturada como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="f0b62-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="f0b62-287">Enviando a matriz de bytes para o Azure **serviço de visão personalizada** instância para análise.</span><span class="sxs-lookup"><span data-stu-id="f0b62-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="f0b62-288">Recebendo a resposta como uma cadeia de caracteres JSON.</span><span class="sxs-lookup"><span data-stu-id="f0b62-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="f0b62-289">Ao desserializar a resposta e passando resultante **previsão** para o **SceneOrganiser** classe, que se encarregará de como a resposta deve ser exibida.</span><span class="sxs-lookup"><span data-stu-id="f0b62-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="f0b62-290">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="f0b62-290">To create this class:</span></span>

1.  <span data-ttu-id="f0b62-291">Com o botão direito no **pasta ativo**, localizado na **painel projeto**, em seguida, clique em **criar** > **pasta**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="f0b62-292">Chame a pasta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="f0b62-293">Clique duas vezes na pasta recém-criada, para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="f0b62-294">Clique com botão direito dentro da pasta e clique em **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="f0b62-295">Nomeie o script **CustomVisionAnalyser.**</span><span class="sxs-lookup"><span data-stu-id="f0b62-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="f0b62-296">Clique duas vezes na nova **CustomVisionAnalyser** script para abri-lo com **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="f0b62-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="f0b62-297">Verifique se que você tem os seguintes namespaces referenciados na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="f0b62-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="f0b62-298">No **CustomVisionAnalyser** de classe, adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="f0b62-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

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
    > <span data-ttu-id="f0b62-299">Certifique-se de inserir seu **previsão-chave de serviço** para o **predictionKey** variável e seu **ponto de extremidade de previsão** no **predictionEndpoint**  variável.</span><span class="sxs-lookup"><span data-stu-id="f0b62-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="f0b62-300">Você copiou para [bloco de notas anteriormente, no capítulo 2, etapa 14](#chapter-2---training-your-custom-vision-project).</span><span class="sxs-lookup"><span data-stu-id="f0b62-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="f0b62-301">Código para o **Awake()** agora precisa ser adicionada para inicializar a variável de instância:</span><span class="sxs-lookup"><span data-stu-id="f0b62-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

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

8.  <span data-ttu-id="f0b62-302">Adicionar a corrotina (com a estática **GetImageAsByteArray()** método abaixo dele), que irá obter os resultados da análise de imagem, capturada pelo **ImageCapture** classe.</span><span class="sxs-lookup"><span data-stu-id="f0b62-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f0b62-303">No **AnalyseImageCapture** corrotina, há uma chamada para o **SceneOrganiser** classe que você ainda está a criar.</span><span class="sxs-lookup"><span data-stu-id="f0b62-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="f0b62-304">Portanto, **deixar as linhas comentadas agora**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-304">Therefore, **leave those lines commented for now**.</span></span>

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

9. <span data-ttu-id="f0b62-305">Excluir o **Start ()** e **Update ()** métodos, pois não serão usados.</span><span class="sxs-lookup"><span data-stu-id="f0b62-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="f0b62-306">Certifique-se de salvar suas alterações no **Visual Studio**, antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0b62-307">Como mencionado anteriormente, não se preocupe sobre código que pode aparecer ter um erro, pois você fornecerá ainda mais em breve, classes que corrigi-los.</span><span class="sxs-lookup"><span data-stu-id="f0b62-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="f0b62-308">Capítulo 6 - criar a classe CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="f0b62-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="f0b62-309">A classe que você criará agora é o **CustomVisionObjects** classe.</span><span class="sxs-lookup"><span data-stu-id="f0b62-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="f0b62-310">Esse script contém um número de objetos usados por outras classes para serializar e desserializar as chamadas feitas para o serviço personalizado de visão.</span><span class="sxs-lookup"><span data-stu-id="f0b62-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="f0b62-311">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="f0b62-311">To create this class:</span></span>

1.  <span data-ttu-id="f0b62-312">Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="f0b62-313">Chame o script **CustomVisionObjects.**</span><span class="sxs-lookup"><span data-stu-id="f0b62-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="f0b62-314">Clique duas vezes na nova **CustomVisionObjects** script para abri-lo com **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="f0b62-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="f0b62-315">Verifique se que você tem os seguintes namespaces referenciados na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="f0b62-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="f0b62-316">Excluir o **Start ()** e **Update ()** métodos dentro de **CustomVisionObjects** classe, essa classe deve agora estar vazia.</span><span class="sxs-lookup"><span data-stu-id="f0b62-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="f0b62-317">É importante que você siga a próxima instrução com cuidado.</span><span class="sxs-lookup"><span data-stu-id="f0b62-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="f0b62-318">Se você colocar novas declarações de classe dentro do **CustomVisionObjects** classe, você receberá erros de compilação na [capítulo 10](#chapter-10---create-the-imagecapture-class), informando que **AnalysisRootObject** e  **BoundingBox** não foram encontrados.</span><span class="sxs-lookup"><span data-stu-id="f0b62-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="f0b62-319">Adicione as seguintes classes *fora* as **CustomVisionObjects** classe.</span><span class="sxs-lookup"><span data-stu-id="f0b62-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="f0b62-320">Esses objetos são usados pelos **Newtonsoft** biblioteca para serializar e desserializar os dados de resposta:</span><span class="sxs-lookup"><span data-stu-id="f0b62-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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

6.  <span data-ttu-id="f0b62-321">Certifique-se de salvar suas alterações no **Visual Studio**, antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="f0b62-322">Capítulo 7 - criar a classe SpatialMapping</span><span class="sxs-lookup"><span data-stu-id="f0b62-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="f0b62-323">Essa classe será definido o **Colisor de mapeamento espacial** na cena, portanto, para ser capaz de detectar colisões entre objetos virtuais e objetos reais.</span><span class="sxs-lookup"><span data-stu-id="f0b62-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="f0b62-324">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="f0b62-324">To create this class:</span></span>

1.  <span data-ttu-id="f0b62-325">Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="f0b62-326">Chame o script **SpatialMapping.**</span><span class="sxs-lookup"><span data-stu-id="f0b62-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="f0b62-327">Clique duas vezes na nova **SpatialMapping** script para abri-lo com **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="f0b62-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="f0b62-328">Verifique se você tem os seguintes namespaces mencionados acima de **SpatialMapping** classe:</span><span class="sxs-lookup"><span data-stu-id="f0b62-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="f0b62-329">Em seguida, adicione as seguintes variáveis dentro do **SpatialMapping** classe acima a **Start ()** método:</span><span class="sxs-lookup"><span data-stu-id="f0b62-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="f0b62-330">Adicione a **Awake()** e **Start ()**:</span><span class="sxs-lookup"><span data-stu-id="f0b62-330">Add the **Awake()** and **Start()**:</span></span>

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

6.  <span data-ttu-id="f0b62-331">Excluir o **Update ()** método.</span><span class="sxs-lookup"><span data-stu-id="f0b62-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="f0b62-332">Certifique-se de salvar suas alterações no **Visual Studio**, antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="f0b62-333">Capítulo 8 - criar a classe GazeCursor</span><span class="sxs-lookup"><span data-stu-id="f0b62-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="f0b62-334">Essa classe é responsável por configurar o cursor no local correto no espaço real, ao utilizar o **SpatialMappingCollider**, criado no capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="f0b62-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="f0b62-335">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="f0b62-335">To create this class:</span></span>

1.  <span data-ttu-id="f0b62-336">Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="f0b62-337">Chame o script **GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="f0b62-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="f0b62-338">Clique duas vezes na nova **GazeCursor** script para abri-lo com **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="f0b62-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="f0b62-339">Verifique se você tem o namespace a seguir mencionado acima de **GazeCursor** classe:</span><span class="sxs-lookup"><span data-stu-id="f0b62-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="f0b62-340">Em seguida, adicione a seguinte variável dentro de **GazeCursor** classe acima a **Start ()** método.</span><span class="sxs-lookup"><span data-stu-id="f0b62-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="f0b62-341">Atualizar o **Start ()** método com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="f0b62-341">Update the **Start()** method with the following code:</span></span>

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

6.  <span data-ttu-id="f0b62-342">Atualizar o **Update ()** método com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="f0b62-342">Update the **Update()** method with the following code:</span></span>

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
    > <span data-ttu-id="f0b62-343">Não se preocupe sobre o erro para o **SceneOrganiser** classe não foi encontrada, você criará no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="f0b62-344">Certifique-se de salvar suas alterações no **Visual Studio**, antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="f0b62-345">Capítulo 9 - criar a classe SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="f0b62-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="f0b62-346">Essa classe será:</span><span class="sxs-lookup"><span data-stu-id="f0b62-346">This class will:</span></span>

-   <span data-ttu-id="f0b62-347">Configurar o *câmera principal* anexando os componentes apropriados para ele.</span><span class="sxs-lookup"><span data-stu-id="f0b62-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="f0b62-348">Quando um objeto é detectado, será responsável por calcular sua posição no mundo real e coloque um **etiqueta** quase-lo com os devidos **nome da marca**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="f0b62-349">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="f0b62-349">To create this class:</span></span>

1.  <span data-ttu-id="f0b62-350">Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="f0b62-351">Nomeie o script **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="f0b62-352">Clique duas vezes na nova **SceneOrganiser** script para abri-lo com **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="f0b62-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="f0b62-353">Verifique se você tem os seguintes namespaces mencionados acima de **SceneOrganiser** classe:</span><span class="sxs-lookup"><span data-stu-id="f0b62-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="f0b62-354">Em seguida, adicione as seguintes variáveis dentro de **SceneOrganiser** classe acima a **Start ()** método:</span><span class="sxs-lookup"><span data-stu-id="f0b62-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="f0b62-355">Excluir o **Start ()** e **Update ()** métodos.</span><span class="sxs-lookup"><span data-stu-id="f0b62-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="f0b62-356">Abaixo das variáveis, adicione a **Awake()** método, que irá inicializar a classe e configure a cena.</span><span class="sxs-lookup"><span data-stu-id="f0b62-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

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

7.  <span data-ttu-id="f0b62-357">Adicione a **PlaceAnalysisLabel()** método, que serão *instanciar* o rótulo na cena (que neste ponto, é invisível para o usuário).</span><span class="sxs-lookup"><span data-stu-id="f0b62-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="f0b62-358">Ele também coloca o quad (também invisível) em que a imagem é colocada e se sobrepõe com o mundo real.</span><span class="sxs-lookup"><span data-stu-id="f0b62-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="f0b62-359">Isso é importante porque as coordenadas da caixa recuperados do serviço após a análise são rastreadas nesse quad determinada a localização aproximada do objeto no mundo real.</span><span class="sxs-lookup"><span data-stu-id="f0b62-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

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

8.  <span data-ttu-id="f0b62-360">Adicione a **FinaliseLabel()** método.</span><span class="sxs-lookup"><span data-stu-id="f0b62-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="f0b62-361">Ele é responsável por:</span><span class="sxs-lookup"><span data-stu-id="f0b62-361">It is responsible for:</span></span>

    *   <span data-ttu-id="f0b62-362">Definindo o *etiqueta* texto com o *marca* da previsão com a confiança mais alta.</span><span class="sxs-lookup"><span data-stu-id="f0b62-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="f0b62-363">Chamar o cálculo do *caixa delimitadora* no objeto quad, posicionado anteriormente e colocar o rótulo na cena.</span><span class="sxs-lookup"><span data-stu-id="f0b62-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="f0b62-364">Ajustando a profundidade de rótulo usando um Raycast em direção a *caixa delimitadora*, que deve entrem em conflito com o objeto no mundo real.</span><span class="sxs-lookup"><span data-stu-id="f0b62-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="f0b62-365">Redefinindo o processo de captura para permitir que o usuário capture outra imagem.</span><span class="sxs-lookup"><span data-stu-id="f0b62-365">Resetting the capture process to allow the user to capture another image.</span></span>

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

9.  <span data-ttu-id="f0b62-366">Adicione a **CalculateBoundingBoxPosition()** método, que hospeda um número de cálculos necessários para traduzir o *caixa delimitadora* coordenadas recuperados do serviço e recriá-los proporcionalmente em quad.</span><span class="sxs-lookup"><span data-stu-id="f0b62-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

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

10. <span data-ttu-id="f0b62-367">Certifique-se de salvar suas alterações no **Visual Studio**, antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="f0b62-368">Antes de continuar, abra o **CustomVisionAnalyser** classe e dentro de **AnalyseLastImageCaptured()** método, *Descomente* as seguintes linhas:</span><span class="sxs-lookup"><span data-stu-id="f0b62-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
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
> <span data-ttu-id="f0b62-369">Não se preocupar sobre o **ImageCapture** mensagem 'não pôde ser encontrado' da classe, você criará no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="f0b62-370">Capítulo 10 - criar a classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="f0b62-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="f0b62-371">A próxima classe que você pretende criar é a **ImageCapture** classe.</span><span class="sxs-lookup"><span data-stu-id="f0b62-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="f0b62-372">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="f0b62-372">This class is responsible for:</span></span>

*   <span data-ttu-id="f0b62-373">Capturar uma imagem usando a câmera HoloLens e armazená-los de *aplicativo* pasta.</span><span class="sxs-lookup"><span data-stu-id="f0b62-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="f0b62-374">Manipulando *toque* gestos do usuário.</span><span class="sxs-lookup"><span data-stu-id="f0b62-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="f0b62-375">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="f0b62-375">To create this class:</span></span>

1.  <span data-ttu-id="f0b62-376">Vá para o **Scripts** pasta que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f0b62-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="f0b62-377">Clique com botão direito dentro da pasta e clique em **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="f0b62-378">Nomeie o script **ImageCapture**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="f0b62-379">Clique duas vezes na nova **ImageCapture** script para abri-lo com **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="f0b62-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="f0b62-380">Substitua os namespaces na parte superior do arquivo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="f0b62-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="f0b62-381">Em seguida, adicione as seguintes variáveis dentro de **ImageCapture** classe acima a **Start ()** método:</span><span class="sxs-lookup"><span data-stu-id="f0b62-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="f0b62-382">Código para o **Awake()** e **Start ()** métodos agora precisa ser adicionado:</span><span class="sxs-lookup"><span data-stu-id="f0b62-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

7.  <span data-ttu-id="f0b62-383">Implemente um manipulador que será chamado quando ocorre um gesto de tocar:</span><span class="sxs-lookup"><span data-stu-id="f0b62-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

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
    > <span data-ttu-id="f0b62-384">Quando o cursor estiver **verde**, isso significa que a câmera está disponível para capturar a imagem.</span><span class="sxs-lookup"><span data-stu-id="f0b62-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="f0b62-385">Quando o cursor estiver **vermelho**, isso significa que a câmera está ocupada.</span><span class="sxs-lookup"><span data-stu-id="f0b62-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="f0b62-386">Adicione o método que o aplicativo usa para iniciar o processo de captura de imagem e armazenar a imagem:</span><span class="sxs-lookup"><span data-stu-id="f0b62-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

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

9.  <span data-ttu-id="f0b62-387">Adicione os manipuladores que serão chamados quando a foto tiver sido capturada e para quando ele estiver pronto para ser analisado.</span><span class="sxs-lookup"><span data-stu-id="f0b62-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="f0b62-388">O resultado é então passado para o **CustomVisionAnalyser** para análise.</span><span class="sxs-lookup"><span data-stu-id="f0b62-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

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

10. <span data-ttu-id="f0b62-389">Certifique-se de salvar suas alterações no **Visual Studio**, antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="f0b62-390">Capítulo 11 - como configurar os scripts na cena</span><span class="sxs-lookup"><span data-stu-id="f0b62-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="f0b62-391">Agora que você tenha escrito todo o código necessário para este projeto, é hora de configurar os scripts na cena e, em pré-fabricados, para que eles se comportam corretamente.</span><span class="sxs-lookup"><span data-stu-id="f0b62-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="f0b62-392">Dentro do **Editor do Unity**, no **painel de hierarquia**, selecione o **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="f0b62-393">No **painel Inspetor**, com o **câmera principal** selecionado, clique em **adicionar componente**, em seguida, procure **SceneOrganiser** script e Clique duas vezes, para adicioná-lo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="f0b62-394">No **painel projeto**, abra o **pasta pré-fabricados**, arraste o **rótulo** pré-fabricado no *rótulo* área, de entrada de destino da referência vazio no **SceneOrganiser** script que você acabou de adicionar para o *câmera principal*, conforme mostrado na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="f0b62-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="f0b62-395">No **painel de hierarquia**, selecione o **GazeCursor** filho do **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="f0b62-396">No **painel Inspetor**, com o **GazeCursor** selecionado, clique em **adicionar componente**, em seguida, procure **GazeCursor** script e Clique duas vezes, para adicioná-lo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="f0b62-397">Novamente, na **painel de hierarquia**, selecione o **SpatialMapping** filho do **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="f0b62-398">No **painel Inspetor**, com o **SpatialMapping** selecionado, clique em **adicionar componente**, em seguida, procure **SpatialMapping** script e clique duas vezes, para adicioná-lo.</span><span class="sxs-lookup"><span data-stu-id="f0b62-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="f0b62-399">Os scripts restantes que você não tem conjunto será adicionado pelo código na **SceneOrganiser** script durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f0b62-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="f0b62-400">Capítulo 12 - antes de compilar</span><span class="sxs-lookup"><span data-stu-id="f0b62-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="f0b62-401">Para executar um teste completo de seu aplicativo você precisará para fazer sideload dele para o Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f0b62-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="f0b62-402">Antes de começar, verifique se:</span><span class="sxs-lookup"><span data-stu-id="f0b62-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="f0b62-403">Todas as configurações mencionadas a [capítulo 3](#chapter-3---set-up-the-unity-project) estão definidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="f0b62-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="f0b62-404">O script **SceneOrganiser** está associada a **câmera principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="f0b62-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="f0b62-405">O script **GazeCursor** está associada a **GazeCursor** objeto.</span><span class="sxs-lookup"><span data-stu-id="f0b62-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="f0b62-406">O script **SpatialMapping** está associada a **SpatialMapping** objeto.</span><span class="sxs-lookup"><span data-stu-id="f0b62-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="f0b62-407">Na [capítulo 5](#chapter-5---create-the-customvisionanalyser-class), etapa 6:</span><span class="sxs-lookup"><span data-stu-id="f0b62-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="f0b62-408">Certifique-se de inserir sua **chave de previsão do serviço** para o **predictionKey** variável.</span><span class="sxs-lookup"><span data-stu-id="f0b62-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="f0b62-409">Você inseriu sua **ponto de extremidade de previsão** para o **predictionEndpoint** classe.</span><span class="sxs-lookup"><span data-stu-id="f0b62-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="f0b62-410">Capítulo 13 - criar a solução UWP e fazer sideload de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f0b62-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="f0b62-411">Agora você está pronto para compilar o aplicativo como uma solução de UWP que você será capaz de implantar para o Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f0b62-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="f0b62-412">Para iniciar o processo de compilação:</span><span class="sxs-lookup"><span data-stu-id="f0b62-412">To begin the build process:</span></span>

1.  <span data-ttu-id="f0b62-413">Vá para **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="f0b62-414">Escala **Unity C\# projetos**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="f0b62-415">Clique em **adicionar cenas abertas**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="f0b62-416">Isso adicionará a cena aberta atualmente para a compilação.</span><span class="sxs-lookup"><span data-stu-id="f0b62-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="f0b62-417">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-417">Click **Build**.</span></span> <span data-ttu-id="f0b62-418">Unity iniciará uma *Explorador de arquivos* janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em.</span><span class="sxs-lookup"><span data-stu-id="f0b62-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="f0b62-419">Criar pasta agora e nomeie- **aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="f0b62-420">Em seguida, com o **App** pasta selecionada, clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="f0b62-421">Unity começará a compilar seu projeto para o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="f0b62-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="f0b62-422">Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um **Explorador de arquivos** janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).</span><span class="sxs-lookup"><span data-stu-id="f0b62-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="f0b62-423">Para implantar o logon no Microsoft HoloLens, será necessário o endereço IP do dispositivo (para a implantação remota) e garantir que ele também tem **modo de desenvolvedor** definido.</span><span class="sxs-lookup"><span data-stu-id="f0b62-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="f0b62-424">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="f0b62-424">To do this:</span></span>

    1.  <span data-ttu-id="f0b62-425">Durante o uso de seu HoloLens, abra o **configurações**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="f0b62-426">Vá para **rede e Internet** > **Wi-Fi** > **opções avançadas**</span><span class="sxs-lookup"><span data-stu-id="f0b62-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="f0b62-427">Observe a **IPv4** endereço.</span><span class="sxs-lookup"><span data-stu-id="f0b62-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="f0b62-428">Em seguida, navegue até **as configurações**e, em seguida, para **atualização e segurança** > **para desenvolvedores**</span><span class="sxs-lookup"><span data-stu-id="f0b62-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="f0b62-429">Definir **modo de desenvolvedor** *em*.</span><span class="sxs-lookup"><span data-stu-id="f0b62-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="f0b62-430">Navegue até seu novo build do Unity (o **App** pasta) e abra o arquivo de solução com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="f0b62-431">No, selecione a configuração da solução **depurar**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="f0b62-432">Na plataforma da solução, selecione **x86, computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="f0b62-433">Você será solicitado a inserir o **endereço IP** de um dispositivo remoto (o Microsoft HoloLens, nesse caso, que você anotou).</span><span class="sxs-lookup"><span data-stu-id="f0b62-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="f0b62-434">Vá para o **construir** menu e clique em **implantar solução** para carregar o aplicativo para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f0b62-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="f0b62-435">Seu aplicativo agora deve aparecer na lista de aplicativos instalados no seu Microsoft HoloLens, pronto para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="f0b62-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="f0b62-436">Para usar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="f0b62-436">To use the application:</span></span>

* <span data-ttu-id="f0b62-437">Examinar um objeto, que você ter treinado com seu **serviço de visão personalizada do Azure, detecção de objetos**e usar o **gesto de toque**.</span><span class="sxs-lookup"><span data-stu-id="f0b62-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="f0b62-438">Se o objeto for detectado com êxito, um espaço de mundo *texto do rótulo* aparecerá com o nome da marca.</span><span class="sxs-lookup"><span data-stu-id="f0b62-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0b62-439">Sempre que você captura uma foto e enviá-lo para o serviço, você pode voltar para a página de serviço e readaptar o serviço com as imagens capturadas recentemente.</span><span class="sxs-lookup"><span data-stu-id="f0b62-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="f0b62-440">No início, você provavelmente também precisará corrigir a *caixas delimitadoras* sejam mais precisos e readaptar o serviço.</span><span class="sxs-lookup"><span data-stu-id="f0b62-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="f0b62-441">O texto do rótulo colocado poderão não aparecer perto o objeto quando os sensores do Microsoft HoloLens e/ou o SpatialTrackingComponent no Unity não conseguir colocar os colisores apropriados, em relação os objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="f0b62-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="f0b62-442">Tente usar o aplicativo em uma superfície diferente se esse for o caso.</span><span class="sxs-lookup"><span data-stu-id="f0b62-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="f0b62-443">Sua visão personalizada, o aplicativo de detecção de objetos</span><span class="sxs-lookup"><span data-stu-id="f0b62-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="f0b62-444">Parabéns, você criou um aplicativo de realidade mista que aproveita a visão personalizada do Azure, API de detecção de objeto, que pode reconhecer um objeto de uma imagem e, em seguida, fornecem uma posição aproximada para esse objeto no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="f0b62-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="f0b62-445">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="f0b62-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="f0b62-446">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="f0b62-446">Exercise 1</span></span>

<span data-ttu-id="f0b62-447">Adicionando para o rótulo de texto, use um cubo semitransparente para encapsular o objeto real em um 3D *caixa delimitadora*.</span><span class="sxs-lookup"><span data-stu-id="f0b62-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="f0b62-448">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="f0b62-448">Exercise 2</span></span>

<span data-ttu-id="f0b62-449">Treine seu serviço personalizado de visão para reconhecer mais objetos.</span><span class="sxs-lookup"><span data-stu-id="f0b62-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="f0b62-450">Exercício 3</span><span class="sxs-lookup"><span data-stu-id="f0b62-450">Exercise 3</span></span>

<span data-ttu-id="f0b62-451">Tocar um som quando um objeto é reconhecido.</span><span class="sxs-lookup"><span data-stu-id="f0b62-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="f0b62-452">Exercício 4</span><span class="sxs-lookup"><span data-stu-id="f0b62-452">Exercise 4</span></span>

<span data-ttu-id="f0b62-453">Usar a API para treinar novamente seu serviço com as mesmas imagens de análise de seu aplicativo, portanto, para tornar o serviço mais precisos (fazer a previsão e o treinamento simultaneamente).</span><span class="sxs-lookup"><span data-stu-id="f0b62-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
