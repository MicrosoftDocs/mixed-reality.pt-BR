---
title: MR e 302b do Azure - visão personalizada
description: Conclua este curso para aprender a treinar um modelo de aprendizado de máquina e, em seguida, use o modelo treinado para reconhecer objetos semelhantes dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, visão personalizada, hololens, imersivo, vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589572"
---
>[!NOTE]
><span data-ttu-id="a3eca-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="a3eca-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a3eca-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="a3eca-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a3eca-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="a3eca-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a3eca-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="a3eca-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a3eca-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a3eca-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a3eca-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="a3eca-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="a3eca-110">MR e 302b do Azure: Visão personalizada</span><span class="sxs-lookup"><span data-stu-id="a3eca-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="a3eca-111">Neste curso, você aprenderá a reconhecer conteúdo visual personalizado em uma imagem fornecido, usando recursos de visão personalizada do Azure em um aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="a3eca-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="a3eca-112">Esse serviço permitirá que você treinar um modelo de aprendizado de máquina usando imagens de objeto.</span><span class="sxs-lookup"><span data-stu-id="a3eca-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="a3eca-113">Em seguida, usará o modelo treinado para reconhecer objetos semelhantes, conforme fornecido pela captura de câmera do Microsoft HoloLens ou de uma câmera conectada ao seu PC para fones imersivos em exposição (VR).</span><span class="sxs-lookup"><span data-stu-id="a3eca-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![resultado do curso](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="a3eca-115">Visão personalizada do Azure é um serviço cognitivo da Microsoft que permite aos desenvolvedores criar classificadores de imagem personalizada.</span><span class="sxs-lookup"><span data-stu-id="a3eca-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="a3eca-116">Os classificadores, em seguida, podem ser usados com novas imagens para reconhecer ou classificam objetos em se a nova imagem.</span><span class="sxs-lookup"><span data-stu-id="a3eca-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="a3eca-117">O serviço fornece um portal simple, fácil de usar on-line para simplificar o processo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="a3eca-118">Para obter mais informações, visite o [página do serviço de visão personalizada do Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="a3eca-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="a3eca-119">Após a conclusão deste curso, você terá um aplicativo de realidade mista que será capaz de trabalhar em dois modos:</span><span class="sxs-lookup"><span data-stu-id="a3eca-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="a3eca-120">**Modo de análise**: configurar o serviço personalizado de visão manualmente por carregar imagens, criação de marcas e o serviço de treinamento para reconhecer a diferentes objetos (nesse caso do mouse e teclado).</span><span class="sxs-lookup"><span data-stu-id="a3eca-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="a3eca-121">Em seguida, você irá criar um aplicativo do HoloLens que capturar imagens usando a câmera e tente reconhecer esses objetos no mundo real.</span><span class="sxs-lookup"><span data-stu-id="a3eca-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="a3eca-122">**Modo de treinamento**: você implementará o código que permitirá que um "modo de treinamento" em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="a3eca-123">O modo de treinamento permitirá que você capturar imagens usando a câmera dos HoloLens, carregar as imagens capturadas para o serviço e treinar o modelo de visão personalizada.</span><span class="sxs-lookup"><span data-stu-id="a3eca-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="a3eca-124">Este curso ensinará você a obter os resultados com o serviço de visão personalizada em um aplicativo de exemplo com base no Unity.</span><span class="sxs-lookup"><span data-stu-id="a3eca-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="a3eca-125">Ele será cabe a você aplicar esses conceitos para um aplicativo personalizado que você pode criar.</span><span class="sxs-lookup"><span data-stu-id="a3eca-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="a3eca-126">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="a3eca-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a3eca-127">Curso</span><span class="sxs-lookup"><span data-stu-id="a3eca-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a3eca-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a3eca-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a3eca-129"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="a3eca-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="a3eca-130">MR e 302b do Azure: Visão personalizada</span><span class="sxs-lookup"><span data-stu-id="a3eca-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="a3eca-131">✔️</span><span class="sxs-lookup"><span data-stu-id="a3eca-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a3eca-132">✔️</span><span class="sxs-lookup"><span data-stu-id="a3eca-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="a3eca-133">Enquanto este curso se concentra principalmente em HoloLens, você também pode aplicar o que você aprenderá neste curso para fones de ouvido Windows Mixed Reality de imersão (VR).</span><span class="sxs-lookup"><span data-stu-id="a3eca-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="a3eca-134">Como fones imersivos em exposição (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="a3eca-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="a3eca-135">Como acompanhar o curso, você verá notas quaisquer alterações que você talvez precise ser empregadas para dar suporte a fones imersivos em exposição (VR).</span><span class="sxs-lookup"><span data-stu-id="a3eca-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a3eca-136">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a3eca-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="a3eca-137">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="a3eca-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="a3eca-138">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (julho de 2018).</span><span class="sxs-lookup"><span data-stu-id="a3eca-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="a3eca-139">Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que está listado abaixo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="a3eca-140">Recomendamos que o hardware e software para este curso a seguir:</span><span class="sxs-lookup"><span data-stu-id="a3eca-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="a3eca-141">Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)</span><span class="sxs-lookup"><span data-stu-id="a3eca-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="a3eca-142">Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="a3eca-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a3eca-143">O SDK mais recente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="a3eca-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a3eca-144">2017.4 do Unity</span><span class="sxs-lookup"><span data-stu-id="a3eca-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a3eca-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a3eca-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="a3eca-146">Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="a3eca-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="a3eca-147">Uma câmera conectada ao seu PC (para desenvolvimento imersivo fone de ouvido)</span><span class="sxs-lookup"><span data-stu-id="a3eca-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="a3eca-148">Acesso à Internet para a instalação do Azure e a recuperação de API de visão personalizada</span><span class="sxs-lookup"><span data-stu-id="a3eca-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="a3eca-149">Uma série de pelo menos cinco (5) imagens (dez (10) recomendado) para cada objeto que você gostaria que o serviço personalizado de visão para reconhecer.</span><span class="sxs-lookup"><span data-stu-id="a3eca-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="a3eca-150">Se desejar, você pode usar [as imagens que já é fornecidas com este curso (um mouse do computador e um teclado) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="a3eca-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="a3eca-151">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="a3eca-151">Before you start</span></span>

1.  <span data-ttu-id="a3eca-152">Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="a3eca-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="a3eca-153">Configurar e testar o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a3eca-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="a3eca-154">Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="a3eca-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="a3eca-155">É uma boa ideia executar calibragem e ajuste de Sensor ao começar a desenvolver um novo aplicativo HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="a3eca-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="a3eca-156">Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="a3eca-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="a3eca-157">Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="a3eca-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="a3eca-158">Capítulo 1 - Portal do serviço de visão personalizada</span><span class="sxs-lookup"><span data-stu-id="a3eca-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="a3eca-159">Para usar o *serviço de visão personalizada* no Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="a3eca-160">Primeiro, [navegue até a *serviço personalizado de visão* página principal](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="a3eca-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="a3eca-161">Clique no **começar** botão.</span><span class="sxs-lookup"><span data-stu-id="a3eca-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="a3eca-162">Entrar para o *serviço personalizado de visão* Portal.</span><span class="sxs-lookup"><span data-stu-id="a3eca-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="a3eca-163">Se você ainda não tiver uma conta do Azure, você precisará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="a3eca-164">Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="a3eca-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="a3eca-165">Quando você estiver conectado pela primeira vez, você será solicitado com o *termos de serviço* painel.</span><span class="sxs-lookup"><span data-stu-id="a3eca-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="a3eca-166">Clique na caixa de seleção para aceitar os termos.</span><span class="sxs-lookup"><span data-stu-id="a3eca-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="a3eca-167">Em seguida, clique em **concordo**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="a3eca-168">Tendo concordou com os termos, você será direcionado para o *projetos* seção do Portal.</span><span class="sxs-lookup"><span data-stu-id="a3eca-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="a3eca-169">Clique em **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="a3eca-170">Uma guia aparecerá no lado direito, que solicitará que você especifique alguns campos para o projeto.</span><span class="sxs-lookup"><span data-stu-id="a3eca-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="a3eca-171">Inserir uma *nome* para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a3eca-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="a3eca-172">Inserir uma *descrição* para seu projeto (*opcional*).</span><span class="sxs-lookup"><span data-stu-id="a3eca-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="a3eca-173">Escolha uma *grupo de recursos* ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="a3eca-174">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="a3eca-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="a3eca-175">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="a3eca-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="a3eca-176">Defina as *tipos de projeto* para **classificação**</span><span class="sxs-lookup"><span data-stu-id="a3eca-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="a3eca-177">Defina as *domínios* como **geral**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="a3eca-178">Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="a3eca-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="a3eca-179">Quando tiver terminado, clique em **criar projeto**, você será redirecionado para o serviço personalizado de visão, página do projeto.</span><span class="sxs-lookup"><span data-stu-id="a3eca-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="a3eca-180">Capítulo 2 - treinamento de seu projeto de visão personalizada</span><span class="sxs-lookup"><span data-stu-id="a3eca-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="a3eca-181">Uma vez no portal de visão personalizada, seu principal objetivo é treinar seu projeto para reconhecer a objetos específicos em imagens.</span><span class="sxs-lookup"><span data-stu-id="a3eca-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="a3eca-182">Você precisa de pelo menos cinco (5) imagens, embora dez (10) é preferível, para cada objeto que você deseja que seu aplicativo reconheça.</span><span class="sxs-lookup"><span data-stu-id="a3eca-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="a3eca-183">[Você pode usar as imagens fornecidas com este curso (um mouse do computador e um teclado)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="a3eca-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="a3eca-184">Para treinar seu projeto de serviço de visão personalizada:</span><span class="sxs-lookup"><span data-stu-id="a3eca-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="a3eca-185">Clique no **+** lado **marcas.**</span><span class="sxs-lookup"><span data-stu-id="a3eca-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="a3eca-186">Adicione a **nome** do objeto que você gostaria de reconhecer.</span><span class="sxs-lookup"><span data-stu-id="a3eca-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="a3eca-187">Clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="a3eca-188">Você notará sua **marca** foi adicionado (talvez seja necessário recarregar a página para que ele seja exibido).</span><span class="sxs-lookup"><span data-stu-id="a3eca-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="a3eca-189">Clique na caixa de seleção junto com sua nova marca, se já não estiver marcada.</span><span class="sxs-lookup"><span data-stu-id="a3eca-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="a3eca-190">Clique em **adicionar imagens** no centro da página.</span><span class="sxs-lookup"><span data-stu-id="a3eca-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="a3eca-191">Clique em **procurar arquivos locais**, pesquise e selecione as imagens que você gostaria de carregar, com o mínimo sendo cinco (5).</span><span class="sxs-lookup"><span data-stu-id="a3eca-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="a3eca-192">Lembre-se de que todas essas imagens devem conter o objeto que você está ensinando.</span><span class="sxs-lookup"><span data-stu-id="a3eca-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="a3eca-193">Você pode selecionar várias imagens por vez, para carregar.</span><span class="sxs-lookup"><span data-stu-id="a3eca-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="a3eca-194">Depois que você pode ver as imagens na guia, selecione a marca apropriada na **minhas marcas** caixa.</span><span class="sxs-lookup"><span data-stu-id="a3eca-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="a3eca-195">Clique em **carregar arquivos**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-195">Click on **Upload files**.</span></span> <span data-ttu-id="a3eca-196">Os arquivos de começar a carregar.</span><span class="sxs-lookup"><span data-stu-id="a3eca-196">The files will begin uploading.</span></span> <span data-ttu-id="a3eca-197">Depois que você tiver a confirmação do upload, clique em **feito**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="a3eca-198">Repita o mesmo processo para criar um novo **marca** denominado **teclado** e carregar as fotos apropriadas para ele.</span><span class="sxs-lookup"><span data-stu-id="a3eca-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="a3eca-199">Certifique-se **desmarcar** *Mouse* depois de criar as novas marcas, portanto, para mostrar os *adicionar imagens* janela.</span><span class="sxs-lookup"><span data-stu-id="a3eca-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="a3eca-200">Uma vez que ambas as marcas, configuradas, clique em **Train**, e a primeira iteração de treinamento iniciará a compilação.</span><span class="sxs-lookup"><span data-stu-id="a3eca-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="a3eca-201">Depois que ele é criado, você poderá ver dois botões chamados **tornar padrão** e **URL de previsão**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="a3eca-202">Clique em **tornar padrão** pela primeira vez, em seguida, clique em **URL de previsão**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="a3eca-203">A URL de ponto de extremidade que é fornecida a partir disso, é definido como o que ocorrer *iteração* foi marcada como padrão.</span><span class="sxs-lookup"><span data-stu-id="a3eca-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="a3eca-204">Como tal, se você fizer um novo mais tarde *iteração* e atualizá-lo como padrão, você não precisará alterar seu código.</span><span class="sxs-lookup"><span data-stu-id="a3eca-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="a3eca-205">Depois de clicar em *URL de previsão*, abra *bloco de notas*e copie e cole o **URL** e o **chave previsão**, de modo que você pode recuperá-la quando precisar dele posteriormente no código.</span><span class="sxs-lookup"><span data-stu-id="a3eca-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="a3eca-206">Clique no **engrenagem** na parte superior direita da tela.</span><span class="sxs-lookup"><span data-stu-id="a3eca-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="a3eca-207">Cópia a **chave de treinamento** e cole-o em um *o bloco de notas*, para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="a3eca-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="a3eca-208">Também copiar sua **Id do projeto**e também colá-lo em seu *bloco de notas* arquivo para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="a3eca-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="a3eca-209">Capítulo 3 - configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="a3eca-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="a3eca-210">A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="a3eca-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="a3eca-211">Abra *Unity* e clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="a3eca-212">Agora, você precisará fornecer um nome de projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="a3eca-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="a3eca-213">Inserir **AzureCustomVision.**</span><span class="sxs-lookup"><span data-stu-id="a3eca-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="a3eca-214">Verifique se o modelo de projeto é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="a3eca-215">Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="a3eca-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="a3eca-216">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="a3eca-217">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="a3eca-218">Vá para **edite* > *preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="a3eca-219">Alteração **Editor de Script externo** à **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="a3eca-220">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="a3eca-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="a3eca-221">Em seguida, vá para **arquivo > configurações de Build** e selecione **plataforma Universal do Windows**, em seguida, clique no **alternar plataforma** botão Aplicar sua seleção.</span><span class="sxs-lookup"><span data-stu-id="a3eca-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="a3eca-222">Enquanto estiver na **arquivo > configurações de Build** e certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="a3eca-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="a3eca-223">**Dispositivo de destino** é definido como **Hololens**</span><span class="sxs-lookup"><span data-stu-id="a3eca-223">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="a3eca-224">Para os fones imersivos em exposição, defina **dispositivo de destino** à *qualquer dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="a3eca-225">**Tipo de compilação** é definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="a3eca-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="a3eca-226">**SDK** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="a3eca-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="a3eca-227">**Versão do Visual Studio** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="a3eca-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="a3eca-228">**Compilar e executar** é definido como **Máquina Local**</span><span class="sxs-lookup"><span data-stu-id="a3eca-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="a3eca-229">Salve a cena e adicioná-lo para a compilação.</span><span class="sxs-lookup"><span data-stu-id="a3eca-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="a3eca-230">Fazer isso selecionando **cenas abra Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="a3eca-231">Salvamento janela será exibida.</span><span class="sxs-lookup"><span data-stu-id="a3eca-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="a3eca-232">Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="a3eca-233">Abrir seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo:* campo de texto, digite **CustomVisionScene**, em seguida, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="a3eca-234">Esteja ciente de que você deve salvar suas cenas de Unity dentro do *ativos* pasta, pois eles devem estar associados ao projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="a3eca-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="a3eca-235">Criando a pasta de cenas (e outras pastas semelhantes) é uma maneira comum de estruturar um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="a3eca-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="a3eca-236">O restante de configurações, em *configurações de Build*, deverá ser deixado como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="a3eca-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="a3eca-237">No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="a3eca-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="a3eca-238">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="a3eca-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="a3eca-239">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="a3eca-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="a3eca-240">**Versão de tempo de execução de scripts** deve ser **Experimental (equivalente ao .NET 4.6)**, que irá disparar uma necessidade de reiniciar o Editor.</span><span class="sxs-lookup"><span data-stu-id="a3eca-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="a3eca-241">**Script de back-end** deve ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="a3eca-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="a3eca-242">**Nível de compatibilidade de API** deve ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="a3eca-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="a3eca-243">Dentro de **configurações de publicação** guia, em **recursos**, verifique:</span><span class="sxs-lookup"><span data-stu-id="a3eca-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="a3eca-244">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="a3eca-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="a3eca-245">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="a3eca-245">**Webcam**</span></span>

        3. <span data-ttu-id="a3eca-246">**Microfone**</span><span class="sxs-lookup"><span data-stu-id="a3eca-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="a3eca-247">Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.</span><span class="sxs-lookup"><span data-stu-id="a3eca-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="a3eca-248">Volta *configurações de Build* *Unity C\# projetos* não fica acinzentado; marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="a3eca-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="a3eca-249">Feche a janela de configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="a3eca-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="a3eca-250">Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="a3eca-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="a3eca-251">Capítulo 4 - importação de DLL Newtonsoft no Unity</span><span class="sxs-lookup"><span data-stu-id="a3eca-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a3eca-252">Se você quiser ignorar a *Unity configurar* componente deste curso e continuar diretamente no código, fique à vontade para baixá-lo [MR-Azure-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 6](#chapter-6---create-the-customvisionanalyser-class).</span><span class="sxs-lookup"><span data-stu-id="a3eca-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="a3eca-253">Este curso requer o uso do **Newtonsoft** biblioteca, que pode ser adicionado como uma DLL para seus ativos.</span><span class="sxs-lookup"><span data-stu-id="a3eca-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="a3eca-254">O pacote que contém [essa biblioteca pode ser baixada deste link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="a3eca-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="a3eca-255">Para importar a biblioteca Newtonsoft para seu projeto, use o pacote do Unity que acompanha este curso.</span><span class="sxs-lookup"><span data-stu-id="a3eca-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="a3eca-256">Adicionar o *unitypackage* para o Unity, usando o **ativos* > *importação* *pacote*  >  *Personalizada* *pacote** opção de menu.</span><span class="sxs-lookup"><span data-stu-id="a3eca-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="a3eca-257">No **Importar pacote do Unity** caixa é exibido para cima, certifique-se de tudo em (e incluindo) **plug-ins** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="a3eca-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="a3eca-258">Clique o **importação** botão para adicionar itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a3eca-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="a3eca-259">Vá para o **Newtonsoft** pasta sob **plug-ins** na exibição do projeto e selecione o *plug-in do newtonsoft. JSON*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="a3eca-260">Com o *plug-in do newtonsoft. JSON* selecionado, certifique-se de que **Any Platform** é **desmarcada**, em seguida, certifique-se de que **WSAPlayer** também é **desmarcada**, em seguida, clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="a3eca-261">Isso é apenas para confirmar que os arquivos estão configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="a3eca-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="a3eca-262">Marcar esses plug-ins configura para ser usado apenas no Editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="a3eca-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="a3eca-263">Há um conjunto diferente de-los na pasta do WSA que será usado depois que o projeto é exportado do Unity.</span><span class="sxs-lookup"><span data-stu-id="a3eca-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="a3eca-264">Em seguida, você precisa abrir o **WSA** pasta, dentro de **Newtonsoft** pasta.</span><span class="sxs-lookup"><span data-stu-id="a3eca-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="a3eca-265">Você verá uma cópia do mesmo arquivo que você acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="a3eca-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="a3eca-266">Selecione o arquivo e, em seguida, no Inspetor de, certifique-se de que</span><span class="sxs-lookup"><span data-stu-id="a3eca-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="a3eca-267">**Qualquer plataforma** é **desmarcada**</span><span class="sxs-lookup"><span data-stu-id="a3eca-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="a3eca-268">**somente** **WSAPlayer** é **marcada**</span><span class="sxs-lookup"><span data-stu-id="a3eca-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="a3eca-269">**Não processar** é **marcada**</span><span class="sxs-lookup"><span data-stu-id="a3eca-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="a3eca-270">Capítulo 5 – instalação da câmera</span><span class="sxs-lookup"><span data-stu-id="a3eca-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="a3eca-271">No painel de hierarquia, selecione a *câmera principal*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="a3eca-272">Depois de selecionado, você poderá ver todos os componentes do *câmera principal* na *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="a3eca-273">O *câmera* objeto deve ser nomeado **câmera principal** (Observe a ortografia!)</span><span class="sxs-lookup"><span data-stu-id="a3eca-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="a3eca-274">A câmera principal **marca** deve ser definida como **MainCamera** (Observe a ortografia!)</span><span class="sxs-lookup"><span data-stu-id="a3eca-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="a3eca-275">Verifique se o **transformar posição** é definido como **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="a3eca-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="a3eca-276">Definir **Limpar sinalizadores** à **cor sólida** (Ignorar para fone de ouvido imersivo).</span><span class="sxs-lookup"><span data-stu-id="a3eca-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="a3eca-277">Defina a **em segundo plano** cor da câmera componente **preto, alfa 0 (código hexadecimal: #00000000)** (Ignorar para fone de ouvido imersivo).</span><span class="sxs-lookup"><span data-stu-id="a3eca-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="a3eca-278">Capítulo 6 - criar a classe CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="a3eca-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="a3eca-279">Neste ponto, você está pronto para escrever um código.</span><span class="sxs-lookup"><span data-stu-id="a3eca-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="a3eca-280">Você começará com o *CustomVisionAnalyser* classe.</span><span class="sxs-lookup"><span data-stu-id="a3eca-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="a3eca-281">As chamadas para o **serviço personalizado de visão** feitas no código mostrado a seguir são feitas usando o **API de REST de visão personalizada**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="a3eca-282">Usando isso, você verá como implementar e usar essa API (útil para entender como implementar algo semelhante em seu próprio).</span><span class="sxs-lookup"><span data-stu-id="a3eca-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="a3eca-283">Lembre-se que a Microsoft oferece uma **SDK do serviço de visão personalizada** que também pode ser usado para fazer chamadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a3eca-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="a3eca-284">Para obter mais informações, visite o [SDK do serviço de visão personalizada](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) artigo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="a3eca-285">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="a3eca-285">This class is responsible for:</span></span>

-   <span data-ttu-id="a3eca-286">Carregando a imagem mais recente capturada como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="a3eca-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="a3eca-287">Enviando a matriz de bytes para o Azure *serviço de visão personalizada* instância para análise.</span><span class="sxs-lookup"><span data-stu-id="a3eca-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="a3eca-288">Recebendo a resposta como uma cadeia de caracteres JSON.</span><span class="sxs-lookup"><span data-stu-id="a3eca-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="a3eca-289">Ao desserializar a resposta e passando resultante *previsão* para o *SceneOrganiser* classe, que se encarregará de como a resposta deve ser exibida.</span><span class="sxs-lookup"><span data-stu-id="a3eca-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="a3eca-290">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="a3eca-290">To create this class:</span></span>

1.  <span data-ttu-id="a3eca-291">Com o botão direito no *pasta ativo* localizado na *painel projeto*, em seguida, clique em **criar > pasta**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="a3eca-292">Chame a pasta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="a3eca-293">Clique duas vezes na pasta recém-criada, para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="a3eca-294">Clique com botão direito dentro da pasta e clique em **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="a3eca-295">Nomeie o script *CustomVisionAnalyser*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="a3eca-296">Clique duas vezes na nova *CustomVisionAnalyser* script para abri-lo com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="a3eca-297">Atualize os namespaces na parte superior do seu arquivo para corresponder ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="a3eca-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="a3eca-298">No *CustomVisionAnalyser* de classe, adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="a3eca-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

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
    > <span data-ttu-id="a3eca-299">Certifique-se de inserir sua **chave de previsão** na **predictionKey** variável e seu **ponto de extremidade de previsão** no **predictionEndpoint** variável.</span><span class="sxs-lookup"><span data-stu-id="a3eca-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="a3eca-300">Você copiou para *bloco de notas* anteriormente no curso.</span><span class="sxs-lookup"><span data-stu-id="a3eca-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="a3eca-301">Código para o **Awake()** agora precisa ser adicionada para inicializar a variável de instância:</span><span class="sxs-lookup"><span data-stu-id="a3eca-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

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

8.  <span data-ttu-id="a3eca-302">Excluir os métodos **Start ()** e **Update ()**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="a3eca-303">Em seguida, adicione a corrotina (com a estática **GetImageAsByteArray()** método abaixo dele), que irá obter os resultados da análise da imagem capturada pelo *ImageCapture* classe.</span><span class="sxs-lookup"><span data-stu-id="a3eca-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a3eca-304">No **AnalyseImageCapture** corrotina, há uma chamada para o *SceneOrganiser* classe que você ainda está a criar.</span><span class="sxs-lookup"><span data-stu-id="a3eca-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="a3eca-305">Portanto, **deixar as linhas comentadas agora**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-305">Therefore, **leave those lines commented for now**.</span></span>

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

10.  <span data-ttu-id="a3eca-306">Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="a3eca-307">Capítulo 7 - criar a classe CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="a3eca-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="a3eca-308">A classe que você criará agora é o *CustomVisionObjects* classe.</span><span class="sxs-lookup"><span data-stu-id="a3eca-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="a3eca-309">Esse script contém um número de objetos usados por outras classes para serializar e desserializar as chamadas feitas para o *serviço de visão personalizada*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="a3eca-310">É importante que você tome nota do ponto de extremidade que o serviço de visão personalizada fornece a você, como o JSON abaixo estrutura foi configurada para trabalhar com [ *previsão de visão personalizado v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span><span class="sxs-lookup"><span data-stu-id="a3eca-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="a3eca-311">Se você tiver uma versão diferente, talvez você precise atualizar o abaixo da estrutura.</span><span class="sxs-lookup"><span data-stu-id="a3eca-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="a3eca-312">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="a3eca-312">To create this class:</span></span>

1.  <span data-ttu-id="a3eca-313">Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="a3eca-314">Chame o script *CustomVisionObjects*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="a3eca-315">Clique duas vezes na nova **CustomVisionObjects** script para abri-lo com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="a3eca-316">Adicione os namespaces a seguir na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="a3eca-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="a3eca-317">Excluir o **Start ()** e **Update ()** métodos dentro de *CustomVisionObjects* classe; essa classe agora deve estar vazia.</span><span class="sxs-lookup"><span data-stu-id="a3eca-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="a3eca-318">Adicione as seguintes classes **fora** as *CustomVisionObjects* classe.</span><span class="sxs-lookup"><span data-stu-id="a3eca-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="a3eca-319">Esses objetos são usados pelos *Newtonsoft* biblioteca para serializar e desserializar os dados de resposta:</span><span class="sxs-lookup"><span data-stu-id="a3eca-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

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

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="a3eca-320">Capítulo 8 - criar a classe VoiceRecognizer</span><span class="sxs-lookup"><span data-stu-id="a3eca-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="a3eca-321">Essa classe reconhecerá a entrada de voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="a3eca-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="a3eca-322">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="a3eca-322">To create this class:</span></span>

1.  <span data-ttu-id="a3eca-323">Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="a3eca-324">Chame o script *VoiceRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="a3eca-325">Clique duas vezes na nova **VoiceRecognizer** script para abri-lo com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="a3eca-326">Adicione os seguintes namespaces acima de *VoiceRecognizer* classe:</span><span class="sxs-lookup"><span data-stu-id="a3eca-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="a3eca-327">Em seguida, adicione as seguintes variáveis dentro de *VoiceRecognizer* classe acima a *Start ()* método:</span><span class="sxs-lookup"><span data-stu-id="a3eca-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

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

5.  <span data-ttu-id="a3eca-328">Adicione a **Awake()** e **Start ()** métodos, o último será definido pelo usuário *palavras-chave* para serem reconhecidos quando a associação de uma marca para uma imagem:</span><span class="sxs-lookup"><span data-stu-id="a3eca-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

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

6.  <span data-ttu-id="a3eca-329">Excluir o **Update ()** método.</span><span class="sxs-lookup"><span data-stu-id="a3eca-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="a3eca-330">Adicione o seguinte manipulador, que é chamado sempre que a entrada de voz é reconhecida:</span><span class="sxs-lookup"><span data-stu-id="a3eca-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

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

8.  <span data-ttu-id="a3eca-331">Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="a3eca-332">Não se preocupe sobre código que pode aparecer ter um erro, pois você fornecerá em breve, as classes adicionais que corrigi-los.</span><span class="sxs-lookup"><span data-stu-id="a3eca-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="a3eca-333">Capítulo 9 - criar a classe CustomVisionTrainer</span><span class="sxs-lookup"><span data-stu-id="a3eca-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="a3eca-334">Essa classe será encadear uma série de chamadas de web para treinar o *serviço de visão personalizada*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="a3eca-335">Cada chamada será explicada em detalhes logo acima do código.</span><span class="sxs-lookup"><span data-stu-id="a3eca-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="a3eca-336">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="a3eca-336">To create this class:</span></span>

1.  <span data-ttu-id="a3eca-337">Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="a3eca-338">Chame o script *CustomVisionTrainer*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="a3eca-339">Clique duas vezes na nova *CustomVisionTrainer* script para abri-lo com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="a3eca-340">Adicione os seguintes namespaces acima de *CustomVisionTrainer* classe:</span><span class="sxs-lookup"><span data-stu-id="a3eca-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="a3eca-341">Em seguida, adicione as seguintes variáveis dentro de *CustomVisionTrainer* classe acima a **Start ()** método.</span><span class="sxs-lookup"><span data-stu-id="a3eca-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="a3eca-342">A URL de treinamento usada aqui é fornecida dentro de *1.2 de treinamento de visão personalizada* documentação, e tem uma estrutura de: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="a3eca-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="a3eca-343">Para obter mais informações, visite o [ *API de referência do treinamento de visão personalizada v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="a3eca-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="a3eca-344">É importante que você tome nota do ponto de extremidade que o serviço de visão personalizada fornece para o modo de treinamento, como a estrutura do JSON usada (dentro de **CustomVisionObjects** classe) foi configurado para trabalhar com [  *Personalizado de visão treinamento v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="a3eca-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="a3eca-345">Se você tiver uma versão diferente, talvez você precise atualizar o *objetos* estrutura.</span><span class="sxs-lookup"><span data-stu-id="a3eca-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

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
    > <span data-ttu-id="a3eca-346">Certifique-se de que você adicione sua **chave de serviço** valor (chave de treinamento) e **Id do projeto** valor, o que você anotou anterior; esses são os valores você [coletados a partir do portal no início do curso ( Capítulo 2, etapa 10 em diante)](#chapter-2---training-your-custom-vision-oroject).</span><span class="sxs-lookup"><span data-stu-id="a3eca-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-oroject).</span></span>

5.  <span data-ttu-id="a3eca-347">Adicione o seguinte **Start ()** e **Awake()** métodos.</span><span class="sxs-lookup"><span data-stu-id="a3eca-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="a3eca-348">Esses métodos são chamados na inicialização e contenham a chamada para definir a interface do usuário:</span><span class="sxs-lookup"><span data-stu-id="a3eca-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

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

6.  <span data-ttu-id="a3eca-349">Excluir o **Update ()** método.</span><span class="sxs-lookup"><span data-stu-id="a3eca-349">Delete the **Update()** method.</span></span> <span data-ttu-id="a3eca-350">Essa classe não precisará dela.</span><span class="sxs-lookup"><span data-stu-id="a3eca-350">This class will not need it.</span></span>

7.  <span data-ttu-id="a3eca-351">Adicione a **RequestTagSelection()** método.</span><span class="sxs-lookup"><span data-stu-id="a3eca-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="a3eca-352">Esse método é o primeiro a ser chamado quando uma imagem foi capturada e armazenada no dispositivo e agora está pronto para ser enviado para o *serviço de visão personalizada*, treiná-lo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="a3eca-353">Esse método exibe no treinamento de interface do usuário, um conjunto de palavras-chave, que o usuário pode usar para marcar a imagem que foi capturada.</span><span class="sxs-lookup"><span data-stu-id="a3eca-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="a3eca-354">Ele também alerta o *VoiceRecognizer* classe para começar a escutar ao usuário para entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="a3eca-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="a3eca-355">Adicione a **VerifyTag()** método.</span><span class="sxs-lookup"><span data-stu-id="a3eca-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="a3eca-356">Esse método receberá a entrada de voz reconhecida pelo **VoiceRecognizer** de classe e verificar sua validade e, em seguida, iniciar o processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="a3eca-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

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

9.  <span data-ttu-id="a3eca-357">Adicione a **SubmitImageForTraining()** método.</span><span class="sxs-lookup"><span data-stu-id="a3eca-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="a3eca-358">Esse método iniciará o processo de treinamento do serviço de visão personalizada.</span><span class="sxs-lookup"><span data-stu-id="a3eca-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="a3eca-359">A primeira etapa é recuperar o **Id de marca** do serviço que está associado com a entrada de fala validado do usuário.</span><span class="sxs-lookup"><span data-stu-id="a3eca-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="a3eca-360">O **Id de marca** , em seguida, será carregado junto com a imagem.</span><span class="sxs-lookup"><span data-stu-id="a3eca-360">The **Tag Id** will then be uploaded along with the image.</span></span>

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

10. <span data-ttu-id="a3eca-361">Adicione a **TrainCustomVisionProject()** método.</span><span class="sxs-lookup"><span data-stu-id="a3eca-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="a3eca-362">Depois que a imagem foi enviada e marcada, esse método será chamado.</span><span class="sxs-lookup"><span data-stu-id="a3eca-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="a3eca-363">Ele criará uma nova iteração será preparada com todas as imagens anteriores enviadas ao serviço mais a imagem acabou de carregar.</span><span class="sxs-lookup"><span data-stu-id="a3eca-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="a3eca-364">Depois que o treinamento for concluído, esse método chamará um método para definir o recém-criado **iteração** como **padrão**, de modo que o ponto de extremidade que você está usando para análise é a iteração mais recente treinada.</span><span class="sxs-lookup"><span data-stu-id="a3eca-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

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

11. <span data-ttu-id="a3eca-365">Adicione a **SetDefaultIteration()** método.</span><span class="sxs-lookup"><span data-stu-id="a3eca-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="a3eca-366">Esse método definirá a iteração anteriormente criada e treinada como *padrão*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="a3eca-367">Depois de concluído, esse método será preciso excluir iteração anterior existente no serviço.</span><span class="sxs-lookup"><span data-stu-id="a3eca-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="a3eca-368">No momento da redação deste curso, há um limite de um máximo 10 (dez) iterações podem existir ao mesmo tempo em que o serviço.</span><span class="sxs-lookup"><span data-stu-id="a3eca-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

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

12. <span data-ttu-id="a3eca-369">Adicione a **DeletePreviousIteration()** método.</span><span class="sxs-lookup"><span data-stu-id="a3eca-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="a3eca-370">Esse método irá localizar e excluir iteração anterior não padrão:</span><span class="sxs-lookup"><span data-stu-id="a3eca-370">This method will find and delete the previous non-default iteration:</span></span>

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

13. <span data-ttu-id="a3eca-371">O último método para adicionar essa classe é o **GetImageAsByteArray()** método, usado em chamadas de web para converter a imagem capturada em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="a3eca-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

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

14. <span data-ttu-id="a3eca-372">Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="a3eca-373">Capítulo 10 - criar a classe SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="a3eca-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="a3eca-374">Essa classe será:</span><span class="sxs-lookup"><span data-stu-id="a3eca-374">This class will:</span></span>

-   <span data-ttu-id="a3eca-375">Criar uma **Cursor** objeto a ser anexado à câmera principal.</span><span class="sxs-lookup"><span data-stu-id="a3eca-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="a3eca-376">Criar uma **rótulo** objeto que será exibido quando o serviço reconhece os objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="a3eca-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="a3eca-377">Configure a câmera principal, anexando os componentes apropriados para ele.</span><span class="sxs-lookup"><span data-stu-id="a3eca-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="a3eca-378">Quando estiver sendo **modo de análise**, gerar os rótulos em tempo de execução, no espaço de mundo apropriado em relação a posição da câmera principal e exibir os dados recebidos do serviço personalizado de visão.</span><span class="sxs-lookup"><span data-stu-id="a3eca-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="a3eca-379">Quando estiver sendo **modo de treinamento**, gerar a interface do usuário que exibirá os diferentes estágios do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="a3eca-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="a3eca-380">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="a3eca-380">To create this class:</span></span>

1.  <span data-ttu-id="a3eca-381">Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="a3eca-382">Nomeie o script *SceneOrganiser*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="a3eca-383">Clique duas vezes na nova *SceneOrganiser* script para abri-lo com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="a3eca-384">Só é necessário um namespace, remova as outras acima de *SceneOrganiser* classe:</span><span class="sxs-lookup"><span data-stu-id="a3eca-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="a3eca-385">Em seguida, adicione as seguintes variáveis dentro de *SceneOrganiser* classe acima a **Start ()** método:</span><span class="sxs-lookup"><span data-stu-id="a3eca-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="a3eca-386">Excluir o **Start ()** e **Update ()** métodos.</span><span class="sxs-lookup"><span data-stu-id="a3eca-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="a3eca-387">Logo abaixo das variáveis, adicione a **Awake()** método, que irá inicializar a classe e configure a cena.</span><span class="sxs-lookup"><span data-stu-id="a3eca-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

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

7.  <span data-ttu-id="a3eca-388">Agora, adicione a **CreateCameraCursor()** método que cria e posiciona o cursor de câmera principal, e o **CreateLabel()** método, que cria o **rótulo de análises** objeto .</span><span class="sxs-lookup"><span data-stu-id="a3eca-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

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

8. <span data-ttu-id="a3eca-389">Adicione a **SetCameraStatus()** método que manipulará as mensagens destinadas a malha de texto, fornecendo o status da câmera.</span><span class="sxs-lookup"><span data-stu-id="a3eca-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

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

9. <span data-ttu-id="a3eca-390">Adicione a **PlaceAnalysisLabel()** e **SetTagsToLastLabel()** métodos, que irá gerar e exibir os dados do serviço personalizado de visão na cena.</span><span class="sxs-lookup"><span data-stu-id="a3eca-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

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

10. <span data-ttu-id="a3eca-391">Por fim, adicione a **CreateTrainingUI()** método, que irá gerar a interface do usuário exibindo os vários estágios do processo de treinamento quando o aplicativo está no modo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="a3eca-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="a3eca-392">Esse método também será ser usado para criar o objeto de status de câmera.</span><span class="sxs-lookup"><span data-stu-id="a3eca-392">This method will also be harnessed to create the camera status object.</span></span>

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

11. <span data-ttu-id="a3eca-393">Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a3eca-394">Antes de continuar, abra o **CustomVisionAnalyser** classe e dentro de **AnalyseLastImageCaptured()** método, *Descomente* as seguintes linhas:</span><span class="sxs-lookup"><span data-stu-id="a3eca-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="a3eca-395">Capítulo 11 - criar a classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="a3eca-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="a3eca-396">A próxima classe que você pretende criar é a *ImageCapture* classe.</span><span class="sxs-lookup"><span data-stu-id="a3eca-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="a3eca-397">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="a3eca-397">This class is responsible for:</span></span>

-   <span data-ttu-id="a3eca-398">Capturar uma imagem usando a câmera HoloLens e armazená-los de *aplicativo* pasta.</span><span class="sxs-lookup"><span data-stu-id="a3eca-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="a3eca-399">Tratamento de gestos de toque do usuário.</span><span class="sxs-lookup"><span data-stu-id="a3eca-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="a3eca-400">Mantendo os *Enum* valor que determina se o aplicativo será executado no *Analysis* modo ou *treinamento* modo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="a3eca-401">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="a3eca-401">To create this class:</span></span>

1.  <span data-ttu-id="a3eca-402">Vá para o **Scripts** pasta que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a3eca-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="a3eca-403">Clique com botão direito dentro da pasta e clique em **criar > C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="a3eca-404">Nomeie o script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="a3eca-405">Clique duas vezes na nova **ImageCapture** script para abri-lo com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="a3eca-406">Substitua os namespaces na parte superior do arquivo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="a3eca-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="a3eca-407">Em seguida, adicione as seguintes variáveis dentro de *ImageCapture* classe acima a **Start ()** método:</span><span class="sxs-lookup"><span data-stu-id="a3eca-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="a3eca-408">Código para o **Awake()** e **Start ()** métodos agora precisa ser adicionado:</span><span class="sxs-lookup"><span data-stu-id="a3eca-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

7.  <span data-ttu-id="a3eca-409">Implemente um manipulador que será chamado quando ocorre um gesto de tocar.</span><span class="sxs-lookup"><span data-stu-id="a3eca-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

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
    > <span data-ttu-id="a3eca-410">Na *Analysis* modo, o **TapHandler** método atua como uma opção para iniciar ou parar o loop de captura de fotos.</span><span class="sxs-lookup"><span data-stu-id="a3eca-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="a3eca-411">Na *treinamento* modo, ele irá capturar uma imagem da câmera.</span><span class="sxs-lookup"><span data-stu-id="a3eca-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="a3eca-412">Quando o cursor estiver verde, significa que a câmera está disponível para capturar a imagem.</span><span class="sxs-lookup"><span data-stu-id="a3eca-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="a3eca-413">Quando o cursor está vermelho, significa que a câmera está ocupada.</span><span class="sxs-lookup"><span data-stu-id="a3eca-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="a3eca-414">Adicione o método que o aplicativo usa para iniciar o processo de captura de imagem e armazenar a imagem.</span><span class="sxs-lookup"><span data-stu-id="a3eca-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

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

9.  <span data-ttu-id="a3eca-415">Adicione os manipuladores que serão chamados quando a foto tiver sido capturada e para quando ele estiver pronto para ser analisado.</span><span class="sxs-lookup"><span data-stu-id="a3eca-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="a3eca-416">O resultado é então passado para o *CustomVisionAnalyser* ou o *CustomVisionTrainer* dependendo de qual modo o código é definido no.</span><span class="sxs-lookup"><span data-stu-id="a3eca-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

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

10. <span data-ttu-id="a3eca-417">Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="a3eca-418">Agora que todos os scripts tiverem sido concluídos, volte no Editor do Unity, em seguida, clique e arraste a **SceneOrganiser** classe a **Scripts** pasta para o **câmera principal** objeto de *painel de hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="a3eca-419">Capítulo 12 - antes de compilar</span><span class="sxs-lookup"><span data-stu-id="a3eca-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="a3eca-420">Para executar um teste completo de seu aplicativo você precisará para fazer sideload dele para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a3eca-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="a3eca-421">Antes de começar, verifique se:</span><span class="sxs-lookup"><span data-stu-id="a3eca-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="a3eca-422">Todas as configurações mencionadas a [capítulo 2](#chapter-2---training-your-custom-vision-project) estão definidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="a3eca-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="a3eca-423">Todos os campos a **câmera principal**, painel de Inspetor, são atribuídas corretamente.</span><span class="sxs-lookup"><span data-stu-id="a3eca-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="a3eca-424">O script **SceneOrganiser** está associada a **câmera principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="a3eca-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="a3eca-425">Certifique-se de inserir sua **chave de previsão** para o **predictionKey** variável.</span><span class="sxs-lookup"><span data-stu-id="a3eca-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="a3eca-426">Você inseriu sua **ponto de extremidade de previsão** para o **predictionEndpoint** variável.</span><span class="sxs-lookup"><span data-stu-id="a3eca-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="a3eca-427">Você inseriu sua **chave de treinamento** na **trainingKey** variável, da *CustomVisionTrainer* classe.</span><span class="sxs-lookup"><span data-stu-id="a3eca-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="a3eca-428">Você inseriu seu **ID do projeto** para o **projectId** variável da *CustomVisionTrainer* classe.</span><span class="sxs-lookup"><span data-stu-id="a3eca-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="a3eca-429">Capítulo 13 - Build e carregar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="a3eca-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="a3eca-430">Para iniciar o *Build* processo:</span><span class="sxs-lookup"><span data-stu-id="a3eca-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="a3eca-431">Vá para **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="a3eca-432">Escala **Unity C\# projetos**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="a3eca-433">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-433">Click **Build**.</span></span> <span data-ttu-id="a3eca-434">Unity iniciará uma **Explorador de arquivos** janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em.</span><span class="sxs-lookup"><span data-stu-id="a3eca-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="a3eca-435">Criar pasta agora e nomeie- **aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="a3eca-436">Em seguida, com o **App** pasta selecionada, clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="a3eca-437">Unity começará a compilar seu projeto para o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="a3eca-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="a3eca-438">Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um **Explorador de arquivos** janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).</span><span class="sxs-lookup"><span data-stu-id="a3eca-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="a3eca-439">Para implantar o HoloLens:</span><span class="sxs-lookup"><span data-stu-id="a3eca-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="a3eca-440">Será necessário o endereço IP do seu HoloLens (para a implantação remota) e garantir que seu HoloLens está em **modo de desenvolvedor**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="a3eca-441">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="a3eca-441">To do this:</span></span>

    1.  <span data-ttu-id="a3eca-442">Durante o uso de seu HoloLens, abra o **configurações**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="a3eca-443">Vá para **rede e Internet** > **Wi-Fi** > **opções avançadas**</span><span class="sxs-lookup"><span data-stu-id="a3eca-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="a3eca-444">Observe a **IPv4** endereço.</span><span class="sxs-lookup"><span data-stu-id="a3eca-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="a3eca-445">Em seguida, navegue até **as configurações**e, em seguida, para **atualização e segurança** > **para desenvolvedores**</span><span class="sxs-lookup"><span data-stu-id="a3eca-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="a3eca-446">Definir **modo de desenvolvedor no**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="a3eca-447">Navegue até seu novo build do Unity (o **App** pasta) e abra o arquivo de solução com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="a3eca-448">No *configuração da solução* selecionar **depurar**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="a3eca-449">No *plataforma da solução*, selecione **x86, computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="a3eca-450">Você será solicitado a inserir o **endereço IP** de um dispositivo remoto (o HoloLens, nesse caso, que você anotou).</span><span class="sxs-lookup"><span data-stu-id="a3eca-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="a3eca-451">Vá para **construir** menu e clique em **implantar solução** para carregar o aplicativo para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a3eca-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="a3eca-452">Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="a3eca-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="a3eca-453">Para implantar o fone de ouvido imersivo, defina as **plataforma da solução** para *Máquina Local*e defina o **configuração** para *depurar*, com *x86* como o **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="a3eca-454">Em seguida, implantar no local de máquina, usando o **compilar** item de menu, selecionando *implantar solução*.</span><span class="sxs-lookup"><span data-stu-id="a3eca-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="a3eca-455">Para usar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="a3eca-455">To use the application:</span></span>

<span data-ttu-id="a3eca-456">Para alternar entre a funcionalidade do aplicativo *treinamento* modo e *previsão* modo, você precisa atualizar o **AppMode** variável, localizado no **Awake()** método localizado dentro de *ImageCapture* classe.</span><span class="sxs-lookup"><span data-stu-id="a3eca-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="a3eca-457">ou</span><span class="sxs-lookup"><span data-stu-id="a3eca-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="a3eca-458">Na *treinamento* modo:</span><span class="sxs-lookup"><span data-stu-id="a3eca-458">In *Training* mode:</span></span>

- <span data-ttu-id="a3eca-459">Examinar **Mouse** ou **teclado** e use o **gesto de toque**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="a3eca-460">Em seguida, o texto será exibida solicitando que você forneça uma marca.</span><span class="sxs-lookup"><span data-stu-id="a3eca-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="a3eca-461">Indicar **Mouse** ou **teclado**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="a3eca-462">Na *previsão* modo:</span><span class="sxs-lookup"><span data-stu-id="a3eca-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="a3eca-463">Examinar o objeto e usar o **gesto de toque**.</span><span class="sxs-lookup"><span data-stu-id="a3eca-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="a3eca-464">Texto será exibido, fornecendo o objeto detectado, com a probabilidade mais alta (Isso é normalizado).</span><span class="sxs-lookup"><span data-stu-id="a3eca-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="a3eca-465">Capítulo 14 - avaliar e melhorar seu modelo de visão personalizada</span><span class="sxs-lookup"><span data-stu-id="a3eca-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="a3eca-466">Para fazer com que seu serviço mais precisos, você precisará continuar treinar o modelo usado para previsão.</span><span class="sxs-lookup"><span data-stu-id="a3eca-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="a3eca-467">Isso é feito por meio de seu novo aplicativo, com ambos os *treinamento* e *previsão* modos, com o último exigir que você visite o portal, que é o que é abordado neste capítulo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="a3eca-468">Prepare-se de rever seu portal muitas vezes, para melhorar continuamente seu modelo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="a3eca-469">Vá até o Portal do Azure personalizado visão novamente e quando estiver em seu projeto, selecione a *previsões* guia (da parte superior central da página):</span><span class="sxs-lookup"><span data-stu-id="a3eca-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="a3eca-470">Você verá todas as imagens que foram enviadas ao seu serviço, enquanto seu aplicativo estava em execução.</span><span class="sxs-lookup"><span data-stu-id="a3eca-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="a3eca-471">Se você passar o mouse sobre as imagens, eles lhe fornecerá as previsões que foram feitas para essa imagem:</span><span class="sxs-lookup"><span data-stu-id="a3eca-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="a3eca-472">Selecione uma das suas imagens para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="a3eca-472">Select one of your images to open it.</span></span> <span data-ttu-id="a3eca-473">Depois de aberto, você verá as previsões feitas dessa imagem à direita.</span><span class="sxs-lookup"><span data-stu-id="a3eca-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="a3eca-474">Se você as previsões corretas, e você deseja adicionar essa imagem ao modelo de treinamento do seu serviço, clique o *minhas marcas* caixa de entrada e, em seguida, selecione a marca que você deseja associar.</span><span class="sxs-lookup"><span data-stu-id="a3eca-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="a3eca-475">Quando tiver terminado, clique no *salvar e fechar* botão na parte inferior direita e prosseguir para a próxima imagem.</span><span class="sxs-lookup"><span data-stu-id="a3eca-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="a3eca-476">Uma vez para a grade de imagens, você observará que as imagens que você tiver adicionado marcas para (e salvo), serão removidos.</span><span class="sxs-lookup"><span data-stu-id="a3eca-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="a3eca-477">Se você encontrar todas as imagens que você acha que não têm seu item marcado dentro deles, você pode excluí-los, clicando o tique nessa imagem (pode fazer isso para várias imagens) e, em seguida, clicando em *excluir* no canto superior direito da página da grade.</span><span class="sxs-lookup"><span data-stu-id="a3eca-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="a3eca-478">Sobre o pop-up que segue, você pode clicar *Sim, exclua* ou *não*, para confirmar a exclusão ou cancelá-la, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a3eca-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="a3eca-479">Quando você estiver pronto para continuar, clique em verde *Train* botão no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="a3eca-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="a3eca-480">O modelo de serviço será ser treinado com todas as imagens que você forneceu agora (que tornam mais precisos).</span><span class="sxs-lookup"><span data-stu-id="a3eca-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="a3eca-481">Quando o treinamento estiver concluído, certifique-se de clicar o *tornar padrão* botão mais uma vez, para que seu *URL de previsão* continua a usar a iteração mais atualizada de seu serviço.</span><span class="sxs-lookup"><span data-stu-id="a3eca-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="a3eca-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="a3eca-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="a3eca-483">O aplicativo de API de visão personalizada concluído</span><span class="sxs-lookup"><span data-stu-id="a3eca-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="a3eca-484">Parabéns, você criou um aplicativo de realidade mista que aproveita a API de visão personalizada do Azure para reconhecer os objetos do mundo real, treinar o modelo de serviço e, em seguida, exibir a confiança de que foi visto.</span><span class="sxs-lookup"><span data-stu-id="a3eca-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="a3eca-485">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="a3eca-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="a3eca-486">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="a3eca-486">Exercise 1</span></span>

<span data-ttu-id="a3eca-487">Treinar sua **serviço de visão personalizada** a reconhecer mais objetos.</span><span class="sxs-lookup"><span data-stu-id="a3eca-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="a3eca-488">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="a3eca-488">Exercise 2</span></span>

<span data-ttu-id="a3eca-489">Como uma maneira para expandir o que você aprendeu, conclua os seguintes exercícios:</span><span class="sxs-lookup"><span data-stu-id="a3eca-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="a3eca-490">Tocar um som quando um objeto é reconhecido.</span><span class="sxs-lookup"><span data-stu-id="a3eca-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="a3eca-491">Exercício 3</span><span class="sxs-lookup"><span data-stu-id="a3eca-491">Exercise 3</span></span>

<span data-ttu-id="a3eca-492">Usar a API para treinar novamente seu serviço com as mesmas imagens de análise de seu aplicativo, portanto, para tornar o serviço mais precisos (fazer a previsão e o treinamento simultaneamente).</span><span class="sxs-lookup"><span data-stu-id="a3eca-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
