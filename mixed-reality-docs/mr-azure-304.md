---
title: Sr e Azure 304-reconhecimento facial
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, reconhecimento facial, hololens, imersão, VR
ms.openlocfilehash: 7cd2a6683c80279129934c619a9b9cb857badf67
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047181"
---
>[!NOTE]
><span data-ttu-id="769b8-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="769b8-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="769b8-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="769b8-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="769b8-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="769b8-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="769b8-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="769b8-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="769b8-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="769b8-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="769b8-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="769b8-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="769b8-110">Sr e Azure 304: Reconhecimento facial</span><span class="sxs-lookup"><span data-stu-id="769b8-110">MR and Azure 304: Face recognition</span></span>

![resultado da conclusão deste curso](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="769b8-112">Neste curso, você aprenderá a adicionar recursos de reconhecimento facial a um aplicativo de realidade misturada, usando os serviços cognitivas do Azure, com o Microsoft API de Detecção Facial.</span><span class="sxs-lookup"><span data-stu-id="769b8-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="769b8-113">O *Azure API de detecção facial* é um serviço da Microsoft, que fornece aos desenvolvedores os algoritmos de face mais avançados, tudo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="769b8-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="769b8-114">O *API de detecção facial* tem duas funções principais: detecção facial com atributos e reconhecimento facial.</span><span class="sxs-lookup"><span data-stu-id="769b8-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="769b8-115">Isso permite que os desenvolvedores simplesmente definam um conjunto de grupos para rostos e, em seguida, enviem imagens de consulta para o serviço posteriormente, para determinar a quem uma face pertence.</span><span class="sxs-lookup"><span data-stu-id="769b8-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="769b8-116">Para obter mais informações, visite a [página de reconhecimento de face do Azure](https://azure.microsoft.com/services/cognitive-services/face/).</span><span class="sxs-lookup"><span data-stu-id="769b8-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="769b8-117">Após a conclusão deste curso, você terá um aplicativo de HoloLens de realidade misturada, que poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="769b8-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="769b8-118">Use um **gesto de toque** para iniciar a captura de uma imagem usando a câmera do HoloLens na placa.</span><span class="sxs-lookup"><span data-stu-id="769b8-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="769b8-119">Envie a imagem capturada para o serviço de *API de detecção facial do Azure* .</span><span class="sxs-lookup"><span data-stu-id="769b8-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="769b8-120">Receba os resultados do algoritmo *API de detecção facial* .</span><span class="sxs-lookup"><span data-stu-id="769b8-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="769b8-121">Use uma interface do usuário simples para exibir o nome de pessoas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="769b8-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="769b8-122">Isso ensinará a você como obter os resultados do serviço de API de Detecção Facial em seu aplicativo de realidade mista com base no Unity.</span><span class="sxs-lookup"><span data-stu-id="769b8-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="769b8-123">Em seu aplicativo, cabe a você como você integrará os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="769b8-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="769b8-124">Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="769b8-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="769b8-125">É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="769b8-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="769b8-126">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="769b8-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="769b8-127">Course</span><span class="sxs-lookup"><span data-stu-id="769b8-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="769b8-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="769b8-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="769b8-129"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="769b8-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="769b8-130">Sr e Azure 304: Reconhecimento facial</span><span class="sxs-lookup"><span data-stu-id="769b8-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="769b8-131">✔️</span><span class="sxs-lookup"><span data-stu-id="769b8-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="769b8-132">✔️</span><span class="sxs-lookup"><span data-stu-id="769b8-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="769b8-133">Embora este curso se concentre principalmente no HoloLens, você também pode aplicar o que aprende neste curso a fones de ouvido (VR) de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="769b8-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="769b8-134">Como os headsets de imersão (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu PC.</span><span class="sxs-lookup"><span data-stu-id="769b8-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="769b8-135">Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a headsets de imersão (VR).</span><span class="sxs-lookup"><span data-stu-id="769b8-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="769b8-136">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="769b8-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="769b8-137">Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o.</span><span class="sxs-lookup"><span data-stu-id="769b8-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="769b8-138">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="769b8-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="769b8-139">Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="769b8-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="769b8-140">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="769b8-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="769b8-141">Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)</span><span class="sxs-lookup"><span data-stu-id="769b8-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="769b8-142">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="769b8-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="769b8-143">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="769b8-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="769b8-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="769b8-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="769b8-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="769b8-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="769b8-146">Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="769b8-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="769b8-147">Uma câmera conectada ao seu PC (para desenvolvimento de headsets de imersão)</span><span class="sxs-lookup"><span data-stu-id="769b8-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="769b8-148">Acesso à Internet para a instalação do Azure e recuperação de API de Detecção Facial</span><span class="sxs-lookup"><span data-stu-id="769b8-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="769b8-149">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="769b8-149">Before you start</span></span>

1.  <span data-ttu-id="769b8-150">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="769b8-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="769b8-151">Configure e teste seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="769b8-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="769b8-152">Se você precisar de suporte para configurar seu HoloLens, [visite o artigo configuração do hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="769b8-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="769b8-153">É uma boa ideia executar a calibragem e o ajuste do sensor ao começar a desenvolver um novo aplicativo do HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="769b8-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="769b8-154">Para obter ajuda sobre calibragem, siga este [link para o artigo Calibration do HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="769b8-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="769b8-155">Para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste do sensor do HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="769b8-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="769b8-156">Capítulo 1-o portal do Azure</span><span class="sxs-lookup"><span data-stu-id="769b8-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="769b8-157">Para usar o serviço de *API de detecção facial* no Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="769b8-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="769b8-158">Primeiro, faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="769b8-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="769b8-159">Se você ainda não tiver uma conta do Azure, será necessário criar uma.</span><span class="sxs-lookup"><span data-stu-id="769b8-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="769b8-160">Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="769b8-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="769b8-161">Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure *API de detecção facial*, pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="769b8-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![Pesquisar API de detecção facial](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="769b8-163">A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="769b8-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="769b8-164">A nova página fornecerá uma descrição do serviço *API de detecção facial* .</span><span class="sxs-lookup"><span data-stu-id="769b8-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="769b8-165">Na parte inferior esquerda desse prompt, selecione o botão **criar** para criar uma associação com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="769b8-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![informações da API facial](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="769b8-167">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="769b8-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="769b8-168">Insira o nome desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="769b8-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="769b8-169">Selecione uma assinatura.</span><span class="sxs-lookup"><span data-stu-id="769b8-169">Select a subscription.</span></span>

    3. <span data-ttu-id="769b8-170">Selecione o tipo de preço apropriado para você, se esta for a primeira vez que criar um *serviço de API de detecção facial*, uma camada gratuita (chamada F0) deverá estar disponível para você.</span><span class="sxs-lookup"><span data-stu-id="769b8-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="769b8-171">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="769b8-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="769b8-172">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="769b8-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="769b8-173">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="769b8-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="769b8-174">Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="769b8-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="769b8-175">O aplicativo UWP, **criador de pessoas**, que você usa mais tarde, requer o uso de ' oeste dos EUA ' para o local.</span><span class="sxs-lookup"><span data-stu-id="769b8-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="769b8-176">Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="769b8-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="769b8-177">Selecione **criar\*.**</span><span class="sxs-lookup"><span data-stu-id="769b8-177">Select **Create\*.**</span></span>

        ![Criar serviço de API facial](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="769b8-179">Depois de clicar em **criar**\* você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="769b8-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="769b8-180">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="769b8-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notificação de criação de serviço](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="769b8-182">Clique nas notificações para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="769b8-182">Click on the notifications to explore your new Service instance.</span></span>

    ![ir para notificação de recurso](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="769b8-184">Quando estiver pronto, clique no botão **ir para o recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="769b8-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![acessar chaves de API de face](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="769b8-186">Neste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, o que é feito por meio do uso da assinatura ' Key ' de seu serviço.</span><span class="sxs-lookup"><span data-stu-id="769b8-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="769b8-187">Na página *início rápido* , do seu serviço de *API de detecção facial* , o primeiro ponto é o número 1, para *captar suas chaves.*</span><span class="sxs-lookup"><span data-stu-id="769b8-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="769b8-188">Na página *serviço* , selecione o hiperlink **teclas** azuis (se estiver na página início rápido) ou o link **chaves** no menu de navegação serviços (à esquerda, indicado pelo ícone "chave"), para revelar suas chaves.</span><span class="sxs-lookup"><span data-stu-id="769b8-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="769b8-189">Anote qualquer uma das chaves e proteja-a, pois você precisará dela mais tarde.</span><span class="sxs-lookup"><span data-stu-id="769b8-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="769b8-190">Capítulo 2-usando o aplicativo UWP do ' criador de pessoas '</span><span class="sxs-lookup"><span data-stu-id="769b8-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="769b8-191">Certifique-se de baixar o aplicativo UWP pré-criado chamado [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span><span class="sxs-lookup"><span data-stu-id="769b8-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="769b8-192">Este aplicativo não é o produto final para este curso, apenas uma ferramenta para ajudá-lo a criar suas entradas do Azure, com as quais o projeto posterior dependerá.</span><span class="sxs-lookup"><span data-stu-id="769b8-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="769b8-193">O **criador** de pessoas permite que você crie entradas do Azure, que estão associadas a pessoas e grupos de pessoas.</span><span class="sxs-lookup"><span data-stu-id="769b8-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="769b8-194">O aplicativo coloca todas as informações necessárias em um formato que, posteriormente, pode ser usado pelo FaceAPI para reconhecer as faces de pessoas que você adicionou.</span><span class="sxs-lookup"><span data-stu-id="769b8-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="769b8-195">FUNDAMENTAL O **criador de pessoas** usa uma limitação básica para ajudar a garantir que você não exceda o número de chamadas de serviço por minuto para a camada de **assinatura gratuita**.</span><span class="sxs-lookup"><span data-stu-id="769b8-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="769b8-196">O texto verde na parte superior mudará para vermelho e será atualizado como ' ativo ' quando a limitação estiver acontecendo; Se esse for o caso, basta aguardar o aplicativo (ele aguardará até que possa continuar acessando o serviço de face, atualizando como ' IN-ACTIVE ' quando você puder usá-lo novamente).</span><span class="sxs-lookup"><span data-stu-id="769b8-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="769b8-197">Esse aplicativo usa as bibliotecas *Microsoft. ProjectOxford. facial* , que permitirão que você faça uso completo da API de detecção facial.</span><span class="sxs-lookup"><span data-stu-id="769b8-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="769b8-198">Essa biblioteca está disponível gratuitamente como um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="769b8-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="769b8-199">Para obter mais informações sobre isso e APIs semelhantes, [visite o artigo de referência de API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span><span class="sxs-lookup"><span data-stu-id="769b8-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="769b8-200">Essas são apenas as etapas necessárias, as instruções sobre como fazer essas coisas estão mais abaixo do documento.</span><span class="sxs-lookup"><span data-stu-id="769b8-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="769b8-201">O aplicativo **Person Maker** lhe permitirá:</span><span class="sxs-lookup"><span data-stu-id="769b8-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="769b8-202">Crie um *grupo de pessoas*, que é um grupo composto por várias pessoas que você deseja associar a ela.</span><span class="sxs-lookup"><span data-stu-id="769b8-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="769b8-203">Com sua conta do Azure, você pode hospedar vários grupos de pessoas.</span><span class="sxs-lookup"><span data-stu-id="769b8-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="769b8-204">Crie uma *pessoa*, que é um membro de um grupo de pessoas.</span><span class="sxs-lookup"><span data-stu-id="769b8-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="769b8-205">Cada pessoa tem várias imagens de *face* associadas a ela.</span><span class="sxs-lookup"><span data-stu-id="769b8-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="769b8-206">Atribua *imagens de face* a uma *pessoa*, para permitir que o serviço de API de detecção facial do Azure reconheça uma *pessoa* pela *face*correspondente.</span><span class="sxs-lookup"><span data-stu-id="769b8-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="769b8-207">*Treine* seu *serviço de API de detecção facial do Azure*.</span><span class="sxs-lookup"><span data-stu-id="769b8-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="769b8-208">Lembre-se de que, para treinar esse aplicativo para reconhecer pessoas, você precisará de dez (10) fotos de fechamento de cada pessoa que deseja adicionar ao seu grupo de pessoas.</span><span class="sxs-lookup"><span data-stu-id="769b8-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="769b8-209">O aplicativo de Cam do Windows 10 pode ajudá-lo a fazer isso.</span><span class="sxs-lookup"><span data-stu-id="769b8-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="769b8-210">Você deve garantir que cada foto esteja clara (Evite desfocar, obscurecer ou estar muito longe, do assunto), ter a foto no formato de arquivo jpg ou png, com o tamanho do arquivo de imagem que não seja maior que **4 MB**e não seja menor que **1 KB**.</span><span class="sxs-lookup"><span data-stu-id="769b8-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="769b8-211">Se você estiver seguindo este tutorial, não use sua própria face para treinamento, como quando você coloca o HoloLens em, você não pode examinar por conta própria.</span><span class="sxs-lookup"><span data-stu-id="769b8-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="769b8-212">Use a face de um colega ou colega de aluno.</span><span class="sxs-lookup"><span data-stu-id="769b8-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="769b8-213">**Criador de pessoas**em execução:</span><span class="sxs-lookup"><span data-stu-id="769b8-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="769b8-214">Abra a pasta **PersonMaker** e clique duas vezes na *solução PersonMaker* para abri-la com o *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="769b8-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="769b8-215">Depois que a *solução PersonMaker* estiver aberta, verifique se:</span><span class="sxs-lookup"><span data-stu-id="769b8-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="769b8-216">A *configuração da solução* está definida como **depurar**.</span><span class="sxs-lookup"><span data-stu-id="769b8-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="769b8-217">A *plataforma da solução* está definida como **x86**</span><span class="sxs-lookup"><span data-stu-id="769b8-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="769b8-218">A *plataforma de destino* é a **máquina local**.</span><span class="sxs-lookup"><span data-stu-id="769b8-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="769b8-219">Talvez você também precise *restaurar os pacotes NuGet* (clique com o botão direito do mouse na *solução* e selecione **restaurar pacotes NuGet**).</span><span class="sxs-lookup"><span data-stu-id="769b8-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="769b8-220">Clique em *computador local* e o aplicativo será iniciado.</span><span class="sxs-lookup"><span data-stu-id="769b8-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="769b8-221">Lembre-se de que, em telas menores, todo o conteúdo pode não estar visível, embora você possa rolar mais para baixo para exibi-lo.</span><span class="sxs-lookup"><span data-stu-id="769b8-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![interface do usuário do criador de pessoas](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="769b8-223">Insira sua **chave de autenticação do Azure**, que você deve ter, do seu serviço de *API de detecção facial* no Azure.</span><span class="sxs-lookup"><span data-stu-id="769b8-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="769b8-224">Inserido</span><span class="sxs-lookup"><span data-stu-id="769b8-224">Insert:</span></span>

    1. <span data-ttu-id="769b8-225">A *ID* que você deseja atribuir ao *grupo de pessoas*.</span><span class="sxs-lookup"><span data-stu-id="769b8-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="769b8-226">A ID deve estar em minúsculas, sem espaços.</span><span class="sxs-lookup"><span data-stu-id="769b8-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="769b8-227">Anote essa ID, pois ela será necessária mais tarde no seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="769b8-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="769b8-228">O *nome* que você deseja atribuir ao *grupo de pessoas* (pode ter espaços).</span><span class="sxs-lookup"><span data-stu-id="769b8-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="769b8-229">Pressione o botão **Criar grupo de pessoas** .</span><span class="sxs-lookup"><span data-stu-id="769b8-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="769b8-230">Uma mensagem de confirmação deve aparecer abaixo do botão.</span><span class="sxs-lookup"><span data-stu-id="769b8-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="769b8-231">Se você tiver um erro de ' acesso negado ', verifique o local definido para o serviço do Azure.</span><span class="sxs-lookup"><span data-stu-id="769b8-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="769b8-232">Conforme mencionado acima, este aplicativo foi projetado para o "oeste dos EUA".</span><span class="sxs-lookup"><span data-stu-id="769b8-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="769b8-233">Você observará que também pode clicar no botão **buscar um grupo conhecido** : isso ocorrerá se você já tiver criado um grupo de pessoas e quiser usá-lo, em vez de criar um novo.</span><span class="sxs-lookup"><span data-stu-id="769b8-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="769b8-234">Lembre-se de que, se você clicar em *criar um grupo de pessoas* com um grupo conhecido, isso também obterá um grupo.</span><span class="sxs-lookup"><span data-stu-id="769b8-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="769b8-235">Insira o *nome* da *pessoa* que você deseja criar.</span><span class="sxs-lookup"><span data-stu-id="769b8-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="769b8-236">Clique no botão **criar pessoa** .</span><span class="sxs-lookup"><span data-stu-id="769b8-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="769b8-237">Uma mensagem de confirmação deve aparecer abaixo do botão.</span><span class="sxs-lookup"><span data-stu-id="769b8-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="769b8-238">Se desejar excluir uma pessoa que você criou anteriormente, você poderá escrever o nome na caixa de texto e pressionar **excluir pessoa**</span><span class="sxs-lookup"><span data-stu-id="769b8-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="769b8-239">Verifique se você sabe o local de dez (dez) fotos da pessoa que deseja adicionar ao seu grupo.</span><span class="sxs-lookup"><span data-stu-id="769b8-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="769b8-240">Pressione **criar e abrir pasta** para abrir o Windows Explorer na pasta associada à pessoa.</span><span class="sxs-lookup"><span data-stu-id="769b8-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="769b8-241">Adicione as dez (10) imagens na pasta.</span><span class="sxs-lookup"><span data-stu-id="769b8-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="769b8-242">Eles devem ser do formato de arquivo *jpg* ou *png* .</span><span class="sxs-lookup"><span data-stu-id="769b8-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="769b8-243">Clique em **Enviar para o Azure**.</span><span class="sxs-lookup"><span data-stu-id="769b8-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="769b8-244">Um contador mostrará o estado do envio, seguido por uma mensagem quando for concluído.</span><span class="sxs-lookup"><span data-stu-id="769b8-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="769b8-245">Depois que o contador for concluído e uma mensagem de confirmação for exibida, clique em **treinar** para treinar o serviço.</span><span class="sxs-lookup"><span data-stu-id="769b8-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="769b8-246">Depois que o processo for concluído, você estará pronto para passar para o Unity.</span><span class="sxs-lookup"><span data-stu-id="769b8-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="769b8-247">Capítulo 3 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="769b8-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="769b8-248">A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="769b8-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="769b8-249">Abra o *Unity* e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="769b8-249">Open *Unity* and click **New**.</span></span> 

    ![Inicie o novo projeto do Unity.](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="769b8-251">Agora, você precisará fornecer um nome de projeto de Unity.</span><span class="sxs-lookup"><span data-stu-id="769b8-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="769b8-252">Insira **MR_FaceRecognition**.</span><span class="sxs-lookup"><span data-stu-id="769b8-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="769b8-253">Verifique se o tipo de projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="769b8-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="769b8-254">Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="769b8-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="769b8-255">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="769b8-255">Then, click **Create project**.</span></span>

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="769b8-257">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="769b8-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="769b8-258">Vá para **Editar preferências de >** e, em seguida, na nova janela, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="769b8-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="769b8-259">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="769b8-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="769b8-260">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="769b8-260">Close the **Preferences** window.</span></span>

    ![Atualize a preferência do editor de script.](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="769b8-262">Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma para **plataforma universal do Windows**clicando no botão **alternar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="769b8-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Janela de configurações de compilação, alterne a plataforma para UWP.](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="769b8-264">Vá para **arquivo > configurações de compilação** e verifique se:</span><span class="sxs-lookup"><span data-stu-id="769b8-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="769b8-265">O **dispositivo de destino** está definido como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="769b8-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="769b8-266">Para os headsets de imersão, defina **dispositivo de destino** para *qualquer dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="769b8-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="769b8-267">O **tipo de compilação** está definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="769b8-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="769b8-268">O **SDK** está definido para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="769b8-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="769b8-269">A **versão do Visual Studio** está definida para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="769b8-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="769b8-270">**Compilar e executar** é definido como **computador local**</span><span class="sxs-lookup"><span data-stu-id="769b8-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="769b8-271">Salve a cena e adicione-a à compilação.</span><span class="sxs-lookup"><span data-stu-id="769b8-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="769b8-272">Faça isso selecionando **Adicionar abrir cenas**.</span><span class="sxs-lookup"><span data-stu-id="769b8-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="769b8-273">Uma janela salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="769b8-273">A save window will appear.</span></span>

            ![Clique no botão Adicionar cenas abertas](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="769b8-275">Selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.</span><span class="sxs-lookup"><span data-stu-id="769b8-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Criar nova pasta de scripts](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="769b8-277">Abra sua pasta de **cenas** recém-criada e, no campo **nome do arquivo**:, digite **FaceRecScene**e pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="769b8-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![Dê um nome à nova cena.](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="769b8-279">As configurações restantes, em *configurações de compilação*, devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="769b8-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="769b8-280">Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="769b8-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra as configurações do Player.](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="769b8-282">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="769b8-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="769b8-283">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="769b8-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="769b8-284">**Criando scripts** A **versão de tempo de execução** deve ser **Experimental** (.NET 4,6 equivalente).</span><span class="sxs-lookup"><span data-stu-id="769b8-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="769b8-285">Alterar isso irá disparar a necessidade de reiniciar o editor.</span><span class="sxs-lookup"><span data-stu-id="769b8-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="769b8-286">O **back-end de script** deve ser **.net**</span><span class="sxs-lookup"><span data-stu-id="769b8-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="769b8-287">O **nível de compatibilidade da API** deve ser **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="769b8-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Atualize outras configurações.](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="769b8-289">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="769b8-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="769b8-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="769b8-290">**InternetClient**</span></span>
        - <span data-ttu-id="769b8-291">**Integrada**</span><span class="sxs-lookup"><span data-stu-id="769b8-291">**Webcam**</span></span>

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="769b8-293">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o SDK do **Windows Mixed Reality** foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="769b8-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Atualize as configurações de X R.](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="769b8-295">De volta *às configurações de compilação*, os **projetos de C# Unity** não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste.</span><span class="sxs-lookup"><span data-stu-id="769b8-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="769b8-296">Feche a janela configurações de compilação.</span><span class="sxs-lookup"><span data-stu-id="769b8-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="769b8-297">Salve sua cena e projeto (**arquivo > salvar cena/arquivo > salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="769b8-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="769b8-298">Capítulo 4-configuração principal da câmera</span><span class="sxs-lookup"><span data-stu-id="769b8-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="769b8-299">Se você quiser ignorar o componente de *configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para [baixar esse. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importe-o para seu projeto como um [pacote personalizado](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="769b8-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="769b8-300">Lembre-se de que esse pacote também inclui a importação da *dll Newtonsoft*, abordada no [capítulo 5](#chapter-5--import-the-newtonsoftjson-library).</span><span class="sxs-lookup"><span data-stu-id="769b8-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoftjson-library).</span></span> <span data-ttu-id="769b8-301">Com isso importado, você pode continuar no [capítulo 6](#chapter-6---create-the-faceanalysis-class).</span><span class="sxs-lookup"><span data-stu-id="769b8-301">With this imported, you can continue from [Chapter 6](#chapter-6---create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="769b8-302">No painel *hierarquia* , selecione a **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="769b8-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="769b8-303">Depois de selecionado, você poderá ver todos os componentes da **câmera principal** no *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="769b8-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="769b8-304">O **objeto de câmera** deve ser nomeado como a **câmera principal** (Observe a grafia!)</span><span class="sxs-lookup"><span data-stu-id="769b8-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="769b8-305">A **marca** da câmera principal deve ser definida como **MainCamera** (Observe a ortografia!)</span><span class="sxs-lookup"><span data-stu-id="769b8-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="769b8-306">Verifique se a **posição de transformação** está definida como **0, 0,** 0</span><span class="sxs-lookup"><span data-stu-id="769b8-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="769b8-307">Definir **sinalizadores de limpeza** como **cor sólida**</span><span class="sxs-lookup"><span data-stu-id="769b8-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="769b8-308">Defina a cor do **plano de fundo** do componente da câmera como **preto, alfa 0 (código hex: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="769b8-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![configurar componentes da câmera](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="769b8-310">Capítulo 5 – importar a biblioteca Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="769b8-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="769b8-311">Se você importou o '. unitypackage ' no [último capítulo](#chapter-4---main-camera-setup), poderá ignorar este capítulo.</span><span class="sxs-lookup"><span data-stu-id="769b8-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4---main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="769b8-312">Para ajudá-lo a desserializar e serializar objetos recebidos e enviados ao serviço bot, você precisa baixar a biblioteca *Newtonsoft. JSON* .</span><span class="sxs-lookup"><span data-stu-id="769b8-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="769b8-313">Você encontrará uma versão compatível já organizada com a estrutura de pasta do Unity correta neste [arquivo de pacote do Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="769b8-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="769b8-314">Para importar a biblioteca:</span><span class="sxs-lookup"><span data-stu-id="769b8-314">To import the library:</span></span>

1.  <span data-ttu-id="769b8-315">Baixe o pacote do Unity.</span><span class="sxs-lookup"><span data-stu-id="769b8-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="769b8-316">Clique em **ativos**, **Importar pacote**, **pacote personalizado**.</span><span class="sxs-lookup"><span data-stu-id="769b8-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![Importar a biblioteca Newtonsoft. JSON](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="769b8-318">Procure o pacote do Unity que você baixou e clique em abrir.</span><span class="sxs-lookup"><span data-stu-id="769b8-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="769b8-319">Verifique se todos os componentes do pacote estão com tique e clique em **importar**.</span><span class="sxs-lookup"><span data-stu-id="769b8-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![Importar a biblioteca Newtonsoft. JSON](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="769b8-321">Capítulo 6-criar a classe FaceAnalysis</span><span class="sxs-lookup"><span data-stu-id="769b8-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="769b8-322">A finalidade da classe FaceAnalysis é hospedar os métodos necessários para se comunicar com o serviço de reconhecimento de face do Azure.</span><span class="sxs-lookup"><span data-stu-id="769b8-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="769b8-323">Depois de enviar a imagem de captura do serviço, ela a analisará e identificará as faces dentro e determinará se alguém pertence a uma pessoa conhecida.</span><span class="sxs-lookup"><span data-stu-id="769b8-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="769b8-324">Se uma pessoa conhecida for encontrada, essa classe exibirá seu nome como texto da interface do usuário na cena.</span><span class="sxs-lookup"><span data-stu-id="769b8-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="769b8-325">Para criar a classe *FaceAnalysis* :</span><span class="sxs-lookup"><span data-stu-id="769b8-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="769b8-326">Clique com o botão direito do mouse na *pasta ativos* , localizada no painel projeto, e clique em **criar** > **pasta**.</span><span class="sxs-lookup"><span data-stu-id="769b8-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="769b8-327">Chame os **scripts**da pasta.</span><span class="sxs-lookup"><span data-stu-id="769b8-327">Call the folder **Scripts**.</span></span> 

    ![Crie a classe FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="769b8-329">Clique duas vezes na pasta recém-criada para abri-la.</span><span class="sxs-lookup"><span data-stu-id="769b8-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="769b8-330">Clique com o botão direito do mouse dentro da pasta e clique em **criar**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="769b8-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="769b8-331">Chame o script *FaceAnalysis*.</span><span class="sxs-lookup"><span data-stu-id="769b8-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="769b8-332">Clique duas vezes no novo script *FaceAnalysis* para abri-lo com o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="769b8-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="769b8-333">Insira os seguintes namespaces acima da classe *FaceAnalysis* :</span><span class="sxs-lookup"><span data-stu-id="769b8-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="769b8-334">Agora você precisa adicionar todos os objetos que são usados para deserialising.</span><span class="sxs-lookup"><span data-stu-id="769b8-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="769b8-335">Esses objetos precisam ser adicionados **fora** do script *FaceAnalysis* (abaixo da chave inferior).</span><span class="sxs-lookup"><span data-stu-id="769b8-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. <span data-ttu-id="769b8-336">Os métodos *Start ()* e *Update ()* não serão usados, portanto, exclua-os agora.</span><span class="sxs-lookup"><span data-stu-id="769b8-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="769b8-337">Dentro da classe *FaceAnalysis* , adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="769b8-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > <span data-ttu-id="769b8-338">Substitua a **chave** e o **PersonGroupId** pela sua chave de serviço e a ID do grupo que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="769b8-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="769b8-339">Adicione o método *ativo ()* , que initialises a classe, adicionando a classe *ImageCapture* à câmera principal e chama o método de criação de rótulo:</span><span class="sxs-lookup"><span data-stu-id="769b8-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. <span data-ttu-id="769b8-340">Adicione o método *CreateLabel ()* , que cria o objeto *Label* para exibir o resultado da análise:</span><span class="sxs-lookup"><span data-stu-id="769b8-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. <span data-ttu-id="769b8-341">Adicione o método *DetectFacesFromImage ()* e *GetImageAsByteArray ()* .</span><span class="sxs-lookup"><span data-stu-id="769b8-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="769b8-342">O primeiro solicitará que o serviço de reconhecimento facial detecte qualquer face possível na imagem enviada, enquanto o último é necessário para converter a imagem capturada em uma matriz de bytes:</span><span class="sxs-lookup"><span data-stu-id="769b8-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. <span data-ttu-id="769b8-343">Adicione o método *IdentifyFaces ()* , que solicita que o *serviço de reconhecimento facial* identifique qualquer face conhecida detectada anteriormente na imagem enviada.</span><span class="sxs-lookup"><span data-stu-id="769b8-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="769b8-344">A solicitação retornará uma ID da pessoa identificada, mas não o nome:</span><span class="sxs-lookup"><span data-stu-id="769b8-344">The request will return an id of the identified person but not the name:</span></span>

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. <span data-ttu-id="769b8-345">Adicione o método *GetPerson ()* .</span><span class="sxs-lookup"><span data-stu-id="769b8-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="769b8-346">Ao fornecer a ID Person, esse método solicita que o *serviço de reconhecimento facial* retorne o nome da pessoa identificada:</span><span class="sxs-lookup"><span data-stu-id="769b8-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  <span data-ttu-id="769b8-347">Lembre-se de **salvar** as alterações antes de voltar para o editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="769b8-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="769b8-348">No editor do Unity, arraste o script FaceAnalysis da pasta scripts no painel projeto para o objeto da câmera principal no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="769b8-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="769b8-349">O novo componente de script será tão adicionado à câmera principal.</span><span class="sxs-lookup"><span data-stu-id="769b8-349">The new script component will be so added to the Main Camera.</span></span> 

![Coloque FaceAnalysis na câmera principal](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="769b8-351">Capítulo 7-criar a classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="769b8-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="769b8-352">A finalidade da classe *ImageCapture* é hospedar os métodos necessários para se comunicar com o *serviço de reconhecimento de face do Azure* para analisar a imagem que será capturada, identificando as faces e determinando se ela pertence a uma pessoa conhecida.</span><span class="sxs-lookup"><span data-stu-id="769b8-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="769b8-353">Se uma pessoa conhecida for encontrada, essa classe exibirá seu nome como texto da interface do usuário na cena.</span><span class="sxs-lookup"><span data-stu-id="769b8-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="769b8-354">Para criar a classe *ImageCapture* :</span><span class="sxs-lookup"><span data-stu-id="769b8-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="769b8-355">Clique com o botão direito do mouse na pasta **scripts** que você criou anteriormente e, em seguida, clique em **criar**,  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="769b8-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="769b8-356">Chame o script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="769b8-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="769b8-357">Clique duas vezes no novo script *ImageCapture* para abri-lo com o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="769b8-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="769b8-358">Insira os seguintes namespaces acima da classe ImageCapture:</span><span class="sxs-lookup"><span data-stu-id="769b8-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="769b8-359">Dentro da classe *ImageCapture* , adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="769b8-359">Inside the *ImageCapture* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  <span data-ttu-id="769b8-360">Adicione os métodos *ativo ()* e *Iniciar ()* necessários para inicializar a classe e permitir que o HoloLens capture os gestos do usuário:</span><span class="sxs-lookup"><span data-stu-id="769b8-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  <span data-ttu-id="769b8-361">Adicione o *TapHandler ()* que é chamado quando o usuário executa um gesto de *toque* :</span><span class="sxs-lookup"><span data-stu-id="769b8-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  <span data-ttu-id="769b8-362">Adicione o método *ExecuteImageCaptureAndAnalysis ()* , que iniciará o processo de captura de imagem:</span><span class="sxs-lookup"><span data-stu-id="769b8-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  <span data-ttu-id="769b8-363">Adicione os manipuladores que são chamados quando o processo de captura de foto foi concluído:</span><span class="sxs-lookup"><span data-stu-id="769b8-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. <span data-ttu-id="769b8-364">Lembre-se de **salvar** as alterações antes de voltar para o editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="769b8-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="769b8-365">Capítulo 8-criando a solução</span><span class="sxs-lookup"><span data-stu-id="769b8-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="769b8-366">Para executar um teste completo de seu aplicativo, você precisará Sideload-lo no seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="769b8-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="769b8-367">Antes de fazer isso, verifique se:</span><span class="sxs-lookup"><span data-stu-id="769b8-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="769b8-368">Todas as configurações mencionadas no capítulo 3 estão definidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="769b8-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="769b8-369">O script *FaceAnalysis* é anexado ao objeto da câmera principal.</span><span class="sxs-lookup"><span data-stu-id="769b8-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="769b8-370">A **chave de autenticação** e a **ID do grupo** foram definidas no script *FaceAnalysis* .</span><span class="sxs-lookup"><span data-stu-id="769b8-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="769b8-371">R neste ponto você está pronto para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="769b8-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="769b8-372">Depois que a solução tiver sido criada, você estará pronto para implantar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="769b8-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="769b8-373">Para iniciar o processo de compilação:</span><span class="sxs-lookup"><span data-stu-id="769b8-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="769b8-374">Salve a cena atual clicando em arquivo, salvar.</span><span class="sxs-lookup"><span data-stu-id="769b8-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="769b8-375">Vá para arquivo, configurações de compilação, clique em Adicionar cenas de abertura.</span><span class="sxs-lookup"><span data-stu-id="769b8-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="769b8-376">Certifique-se de que C# os projetos de Unity em escala.</span><span class="sxs-lookup"><span data-stu-id="769b8-376">Make sure to tick Unity C# Projects.</span></span>

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="769b8-378">Pressione compilar.</span><span class="sxs-lookup"><span data-stu-id="769b8-378">Press Build.</span></span> <span data-ttu-id="769b8-379">Ao fazer isso, o Unity iniciará uma janela Explorador de arquivos, onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado.</span><span class="sxs-lookup"><span data-stu-id="769b8-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="769b8-380">Crie essa pasta agora, dentro do projeto do Unity, e chame-a de App.</span><span class="sxs-lookup"><span data-stu-id="769b8-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="769b8-381">Em seguida, com a pasta de aplicativo selecionada, pressione Selecionar pasta.</span><span class="sxs-lookup"><span data-stu-id="769b8-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="769b8-382">O Unity começará a compilar seu projeto, na pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="769b8-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="769b8-383">Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do explorador de arquivos no local de sua compilação.</span><span class="sxs-lookup"><span data-stu-id="769b8-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="769b8-385">Abra a pasta do aplicativo e, em seguida, abra a nova solução de projeto (como visto acima, MR_FaceRecognition. sln).</span><span class="sxs-lookup"><span data-stu-id="769b8-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="769b8-386">Capítulo 9-implantando seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="769b8-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="769b8-387">Para implantar no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="769b8-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="769b8-388">Você precisará do endereço IP do seu HoloLens (para implantação remota) e para garantir que seu HoloLens esteja no **modo de desenvolvedor**.</span><span class="sxs-lookup"><span data-stu-id="769b8-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="769b8-389">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="769b8-389">To do this:</span></span>

    1. <span data-ttu-id="769b8-390">Enquanto estiver desgastando seu HoloLens, abra as **configurações**.</span><span class="sxs-lookup"><span data-stu-id="769b8-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="769b8-391">Acessar **Opções de rede & Internet > Wi-Fi > avançado**</span><span class="sxs-lookup"><span data-stu-id="769b8-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="769b8-392">Anote o endereço **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="769b8-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="769b8-393">Em seguida, navegue de volta para **configurações**e, em seguida, **atualize & > de segurança para desenvolvedores**</span><span class="sxs-lookup"><span data-stu-id="769b8-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="769b8-394">Defina o modo de desenvolvedor em.</span><span class="sxs-lookup"><span data-stu-id="769b8-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="769b8-395">Navegue até sua nova compilação do Unity (a pasta do *aplicativo* ) e abra o arquivo de solução com o *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="769b8-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="769b8-396">Na configuração da solução, selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="769b8-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="769b8-397">Na plataforma da solução, selecione **x86**, **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="769b8-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="769b8-399">Vá para o **menu Compilar** e clique em **implantar solução**para Sideload o aplicativo ao seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="769b8-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="769b8-400">Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="769b8-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="769b8-401">Para implantar em headsets de imersão, defina a **plataforma da solução** como *computador local*e defina a **configuração** a ser depurada, com *x86* como a **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="769b8-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="769b8-402">Em seguida, implante no computador local, usando o **menu Compilar**, selecionando *implantar solução*.</span><span class="sxs-lookup"><span data-stu-id="769b8-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="769b8-403">Capítulo 10-usando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="769b8-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="769b8-404">Desgastando o HoloLens, inicie o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="769b8-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="769b8-405">Examine a pessoa que você registrou com o *API de detecção facial*.</span><span class="sxs-lookup"><span data-stu-id="769b8-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="769b8-406">Certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="769b8-406">Make sure that:</span></span>

    -  <span data-ttu-id="769b8-407">A face da pessoa não está muito distante e claramente visível</span><span class="sxs-lookup"><span data-stu-id="769b8-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="769b8-408">A iluminação do ambiente não é muito escura</span><span class="sxs-lookup"><span data-stu-id="769b8-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="769b8-409">Use o gesto de toque para capturar a imagem da pessoa.</span><span class="sxs-lookup"><span data-stu-id="769b8-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="769b8-410">Aguarde até que o aplicativo envie a solicitação de análise e receba uma resposta.</span><span class="sxs-lookup"><span data-stu-id="769b8-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="769b8-411">Se a pessoa tiver sido reconhecida com êxito, o nome da pessoa aparecerá como texto da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="769b8-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="769b8-412">Você pode repetir o processo de captura usando o gesto de toque a cada poucos segundos.</span><span class="sxs-lookup"><span data-stu-id="769b8-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="769b8-413">Seu aplicativo de API de Detecção Facial do Azure concluído</span><span class="sxs-lookup"><span data-stu-id="769b8-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="769b8-414">Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço de reconhecimento de face do Azure para detectar rostos em uma imagem e identificar quaisquer faces conhecidas.</span><span class="sxs-lookup"><span data-stu-id="769b8-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![resultado da conclusão deste curso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="769b8-416">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="769b8-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="769b8-417">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="769b8-417">Exercise 1</span></span>

<span data-ttu-id="769b8-418">A **API de detecção facial do Azure** é eficiente o suficiente para detectar até 64 rostos em uma única imagem.</span><span class="sxs-lookup"><span data-stu-id="769b8-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="769b8-419">Estenda o aplicativo para que ele possa reconhecer duas ou três faces, entre muitas outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="769b8-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="769b8-420">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="769b8-420">Exercise 2</span></span>

<span data-ttu-id="769b8-421">O **API de detecção facial do Azure** também é capaz de fornecer de volta todos os tipos de informações de atributo.</span><span class="sxs-lookup"><span data-stu-id="769b8-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="769b8-422">Integre-o ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="769b8-422">Integrate this into the application.</span></span> <span data-ttu-id="769b8-423">Isso pode ser ainda mais interessante, quando combinado com o [API de detecção de emoções](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span><span class="sxs-lookup"><span data-stu-id="769b8-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
