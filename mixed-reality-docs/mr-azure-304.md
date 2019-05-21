---
title: MR e Azure 304 - reconhecimento facial
description: Conclua este curso para aprender a implementar o reconhecimento de Face do Azure dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, misto realidade, academy, unity, tutorial, api, o reconhecimento, hololens, vr de imersão, facial
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590741"
---
>[!NOTE]
><span data-ttu-id="1ee20-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="1ee20-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1ee20-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1ee20-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1ee20-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="1ee20-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1ee20-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="1ee20-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1ee20-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1ee20-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1ee20-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="1ee20-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="1ee20-110">MR e o Azure 304: Reconhecimento facial</span><span class="sxs-lookup"><span data-stu-id="1ee20-110">MR and Azure 304: Face recognition</span></span>

![resultado de concluírem este curso](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="1ee20-112">Neste curso você aprenderá como adicionar recursos de reconhecimento de face a um aplicativo de realidade misturada, usando serviços Cognitivos do Azure, com a API de detecção facial da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1ee20-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="1ee20-113">*API de detecção facial do Azure* é um serviço da Microsoft, que fornece aos desenvolvedores com os algoritmos mais avançados de detecção facial, tudo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="1ee20-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="1ee20-114">O *API de detecção facial* tem duas funções principais: detecção com atributos facial e reconhecimento facial.</span><span class="sxs-lookup"><span data-stu-id="1ee20-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="1ee20-115">Isso permite que os desenvolvedores simplesmente definir um conjunto de grupos de rostos e, em seguida, enviar imagens de consulta para o serviço posteriormente, para determinar à qual pertence uma face.</span><span class="sxs-lookup"><span data-stu-id="1ee20-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="1ee20-116">Para obter mais informações, visite o [página de reconhecimento de Face Azure](https://azure.microsoft.com/services/cognitive-services/face/).</span><span class="sxs-lookup"><span data-stu-id="1ee20-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="1ee20-117">Com a conclusão deste curso, você terá uma realidade misturada aplicativo HoloLens, que será capaz de fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1ee20-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="1ee20-118">Use uma **gestos de toque** para iniciar a captura de uma imagem usando a câmera HoloLens integrada.</span><span class="sxs-lookup"><span data-stu-id="1ee20-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="1ee20-119">Enviar a imagem capturada para o *API de detecção facial Azure* service.</span><span class="sxs-lookup"><span data-stu-id="1ee20-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="1ee20-120">Receber os resultados do *API de detecção facial* algoritmo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="1ee20-121">Use uma Interface de usuário simples, para exibir o nome das pessoas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="1ee20-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="1ee20-122">Isso irá ensiná-lo como obter os resultados do serviço de API de detecção facial em seu aplicativo de realidade misturada com base no Unity.</span><span class="sxs-lookup"><span data-stu-id="1ee20-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="1ee20-123">Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="1ee20-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="1ee20-124">Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="1ee20-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="1ee20-125">Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="1ee20-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="1ee20-126">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="1ee20-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1ee20-127">Curso</span><span class="sxs-lookup"><span data-stu-id="1ee20-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1ee20-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1ee20-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1ee20-129"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="1ee20-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1ee20-130">MR e o Azure 304: Reconhecimento facial</span><span class="sxs-lookup"><span data-stu-id="1ee20-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="1ee20-131">✔️</span><span class="sxs-lookup"><span data-stu-id="1ee20-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1ee20-132">✔️</span><span class="sxs-lookup"><span data-stu-id="1ee20-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="1ee20-133">Enquanto este curso se concentra principalmente em HoloLens, você também pode aplicar o que você aprenderá neste curso para fones de ouvido Windows Mixed Reality de imersão (VR).</span><span class="sxs-lookup"><span data-stu-id="1ee20-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="1ee20-134">Como fones imersivos em exposição (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="1ee20-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="1ee20-135">Como acompanhar o curso, você verá notas quaisquer alterações que você talvez precise ser empregadas para dar suporte a fones imersivos em exposição (VR).</span><span class="sxs-lookup"><span data-stu-id="1ee20-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1ee20-136">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1ee20-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="1ee20-137">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="1ee20-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="1ee20-138">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="1ee20-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="1ee20-139">Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .</span><span class="sxs-lookup"><span data-stu-id="1ee20-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="1ee20-140">Recomendamos que o hardware e software para este curso a seguir:</span><span class="sxs-lookup"><span data-stu-id="1ee20-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="1ee20-141">Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)</span><span class="sxs-lookup"><span data-stu-id="1ee20-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="1ee20-142">Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="1ee20-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="1ee20-143">O SDK mais recente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="1ee20-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="1ee20-144">2017.4 do Unity</span><span class="sxs-lookup"><span data-stu-id="1ee20-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="1ee20-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1ee20-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="1ee20-146">Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="1ee20-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="1ee20-147">Uma câmera conectada ao seu PC (para desenvolvimento imersivo fone de ouvido)</span><span class="sxs-lookup"><span data-stu-id="1ee20-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="1ee20-148">Acesso à Internet para a instalação do Azure e a recuperação de API de detecção facial</span><span class="sxs-lookup"><span data-stu-id="1ee20-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1ee20-149">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="1ee20-149">Before you start</span></span>

1.  <span data-ttu-id="1ee20-150">Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="1ee20-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="1ee20-151">Configurar e testar o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1ee20-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="1ee20-152">Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="1ee20-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="1ee20-153">É uma boa ideia executar calibragem e ajuste de Sensor ao começar a desenvolver um new App HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="1ee20-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="1ee20-154">Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="1ee20-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="1ee20-155">Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="1ee20-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="1ee20-156">Capítulo 1 - Portal do Azure</span><span class="sxs-lookup"><span data-stu-id="1ee20-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="1ee20-157">Para usar o *API de detecção facial* serviço no Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="1ee20-158">Primeiro, faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="1ee20-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="1ee20-159">Se você ainda não tiver uma conta do Azure, você precisará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="1ee20-160">Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="1ee20-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="1ee20-161">Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure *API de detecção facial*, pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![Pesquisar para api de detecção facial](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="1ee20-163">A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="1ee20-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="1ee20-164">A nova página fornecerá uma descrição do *API de detecção facial* service.</span><span class="sxs-lookup"><span data-stu-id="1ee20-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="1ee20-165">Na parte inferior esquerda desse prompt, selecione a **criar** botão para criar uma associação com este serviço.</span><span class="sxs-lookup"><span data-stu-id="1ee20-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![enfrentam informações da api](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="1ee20-167">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="1ee20-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="1ee20-168">Insira o nome desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="1ee20-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="1ee20-169">Selecione uma assinatura.</span><span class="sxs-lookup"><span data-stu-id="1ee20-169">Select a subscription.</span></span>

    3. <span data-ttu-id="1ee20-170">Selecione o tipo de preço apropriado para você, se esta for a primeira hora de criar uma *serviço de API de detecção facial*, uma camada gratuita (chamada F0) deve estar disponível para você.</span><span class="sxs-lookup"><span data-stu-id="1ee20-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="1ee20-171">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1ee20-172">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="1ee20-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1ee20-173">É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="1ee20-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="1ee20-174">Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="1ee20-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="1ee20-175">O aplicativo UWP **pessoa Maker**, que você usará mais tarde, requer o uso de 'Oeste dos Estados Unidos' para o local.</span><span class="sxs-lookup"><span data-stu-id="1ee20-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="1ee20-176">Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="1ee20-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="1ee20-177">Selecione **criar\*.**</span><span class="sxs-lookup"><span data-stu-id="1ee20-177">Select **Create\*.**</span></span>

        ![Criar enfrentam o serviço de api](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="1ee20-179">Depois de clicar em **criar**\* você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="1ee20-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="1ee20-180">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="1ee20-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notificação de criação de serviço](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="1ee20-182">Clique em notificações para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="1ee20-182">Click on the notifications to explore your new Service instance.</span></span>

    ![Vá para a notificação do recurso](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="1ee20-184">Quando você estiver pronto, clique em **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="1ee20-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![acesso enfrentam chaves de api](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="1ee20-186">Dentro deste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, que é feito por meio de assinatura do serviço 'key'.</span><span class="sxs-lookup"><span data-stu-id="1ee20-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="1ee20-187">Do *início rápido* página, de seu *API de detecção facial* de serviço, o primeiro ponto é o número 1, para *pegue suas chaves.*</span><span class="sxs-lookup"><span data-stu-id="1ee20-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="1ee20-188">No *serviço* página selecionar qualquer um dos azul **chaves** hiperlink (se estiver na página de início rápido), ou o **chaves** link no menu de navegação de serviços (à esquerda, indicada pelo ' chave ' ícone), para revelar as chaves.</span><span class="sxs-lookup"><span data-stu-id="1ee20-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="1ee20-189">Tome nota de qualquer um das chaves e protegê-lo, pois você precisará dele mais tarde.</span><span class="sxs-lookup"><span data-stu-id="1ee20-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="1ee20-190">Capítulo 2 - usando o aplicativo UWP de 'Person Maker'</span><span class="sxs-lookup"><span data-stu-id="1ee20-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="1ee20-191">Certifique-se de baixar o aplicativo de UWP predefinidos chamados [pessoa Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span><span class="sxs-lookup"><span data-stu-id="1ee20-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="1ee20-192">Este aplicativo não é o produto final deste curso, uma simples ferramenta para ajudá-lo a criar suas entradas do Azure, que contarão com o projeto posterior.</span><span class="sxs-lookup"><span data-stu-id="1ee20-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="1ee20-193">**Criador de pessoa** permite que você crie entradas do Azure, que estão associadas com pessoas e grupos de pessoas.</span><span class="sxs-lookup"><span data-stu-id="1ee20-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="1ee20-194">O aplicativo coloca as informações necessárias em um formato que pode então ser usado posteriormente por FaceAPI, para reconhecer os rostos de pessoas com quem você adicionou.</span><span class="sxs-lookup"><span data-stu-id="1ee20-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="1ee20-195">[IMPORTANTE] **Pessoa Maker** usa alguns limitação básica, para ajudar a garantir que você não exceda o número de chamadas de serviço por minuto para o **nível de assinatura gratuita**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="1ee20-196">O texto verde na parte superior irá mudar para vermelho e atualizar como 'Ativo' quando a limitação está ocorrendo; Se esse for o caso, simplesmente Aguarde para o aplicativo (ele aguardará até que ele em seguida pode continuar a acessar o serviço de detecção facial, a atualização como 'Ativa em' quando você pode usá-lo novamente).</span><span class="sxs-lookup"><span data-stu-id="1ee20-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="1ee20-197">Esse aplicativo usa o *Microsoft.ProjectOxford.Face* usam de bibliotecas, o que permitirá que você faça completa da API de detecção facial.</span><span class="sxs-lookup"><span data-stu-id="1ee20-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="1ee20-198">Essa biblioteca está disponível gratuitamente como um pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="1ee20-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="1ee20-199">Para obter mais informações sobre isso e é semelhante, as APIs [Certifique-se de visitar o artigo de referência de API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span><span class="sxs-lookup"><span data-stu-id="1ee20-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="1ee20-200">São apenas as etapas necessárias, mais adiante o documento de instruções sobre como fazer essas coisas.</span><span class="sxs-lookup"><span data-stu-id="1ee20-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="1ee20-201">O **pessoa Maker** aplicativo permitirá que você:</span><span class="sxs-lookup"><span data-stu-id="1ee20-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="1ee20-202">Criar uma *grupo de pessoas*, que é composto de um grupo de várias pessoas que você deseja associar a ele.</span><span class="sxs-lookup"><span data-stu-id="1ee20-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="1ee20-203">Com sua conta do Azure, você pode hospedar vários grupos de pessoas.</span><span class="sxs-lookup"><span data-stu-id="1ee20-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="1ee20-204">Criar uma *pessoa*, que é um membro de um grupo de pessoas.</span><span class="sxs-lookup"><span data-stu-id="1ee20-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="1ee20-205">Cada pessoa tem inúmeras *Face* imagens associadas a ele.</span><span class="sxs-lookup"><span data-stu-id="1ee20-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="1ee20-206">Atribua *enfrentam imagens* para um *pessoa*, para permitir que o serviço de API do Azure Face reconhecer um *pessoa* por correspondente *face*.</span><span class="sxs-lookup"><span data-stu-id="1ee20-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="1ee20-207">*Treinar* sua *Azure enfrentam o serviço de API*.</span><span class="sxs-lookup"><span data-stu-id="1ee20-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="1ee20-208">Lembre-se, portanto, para treinar esse aplicativo para reconhecer pessoas, você terá dez (10) fotos aproximadas de cada pessoa que você deseja adicionar ao seu grupo de pessoas.</span><span class="sxs-lookup"><span data-stu-id="1ee20-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="1ee20-209">O aplicativo do Windows 10 Cam pode ajudar você a tirá-las.</span><span class="sxs-lookup"><span data-stu-id="1ee20-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="1ee20-210">Você deve garantir que cada foto é clara (Evite desfoque, ocultando ou sendo muito longe, da entidade), têm a foto no formato de arquivo jpg ou png, com o tamanho do arquivo de imagem que está sendo não deve exceder **4MB**e não menos do que **1 KB**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="1ee20-211">Se você estiver seguindo este tutorial, não use seu próprio face para treinamento, pois quando você coloca o HoloLens, você não pode examinar por conta própria.</span><span class="sxs-lookup"><span data-stu-id="1ee20-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="1ee20-212">Use a face de um amigo ou colega aluno.</span><span class="sxs-lookup"><span data-stu-id="1ee20-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="1ee20-213">Executando **pessoa Maker**:</span><span class="sxs-lookup"><span data-stu-id="1ee20-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="1ee20-214">Abra o **PersonMaker** pasta e clique duas vezes no *solução PersonMaker* para abri-lo com *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="1ee20-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="1ee20-215">Uma vez a *PersonMaker solução* estiver aberto, certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="1ee20-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="1ee20-216">O *configuração da solução* é definido como **depurar**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="1ee20-217">O *plataforma da solução* é definido como **x86**</span><span class="sxs-lookup"><span data-stu-id="1ee20-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="1ee20-218">O *plataforma de destino* é **Máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="1ee20-219">Você também precisará *restaurar pacotes NuGet* (com o botão direito do *solução* e selecione **restaurar pacotes do NuGet**).</span><span class="sxs-lookup"><span data-stu-id="1ee20-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="1ee20-220">Clique em *computador Local* e o aplicativo será iniciado.</span><span class="sxs-lookup"><span data-stu-id="1ee20-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="1ee20-221">Lembre-se em telas menores, todo o conteúdo pode não estar visível, embora você pode rolar mais adiante para exibi-lo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![interface de usuário do criador de pessoa](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="1ee20-223">Insira sua **chave de autenticação do Azure**, que você deve ter, de seu *API de detecção facial* serviço dentro do Azure.</span><span class="sxs-lookup"><span data-stu-id="1ee20-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="1ee20-224">Inserir:</span><span class="sxs-lookup"><span data-stu-id="1ee20-224">Insert:</span></span>

    1. <span data-ttu-id="1ee20-225">O *identificação* você deseja atribuir à *grupo de pessoas*.</span><span class="sxs-lookup"><span data-stu-id="1ee20-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="1ee20-226">A ID deve ser em letras minúsculas, sem espaços.</span><span class="sxs-lookup"><span data-stu-id="1ee20-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="1ee20-227">Anote essa ID, pois ela será necessária posteriormente no seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="1ee20-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="1ee20-228">O *nome* você deseja atribuir à *grupo de pessoas* (pode ter espaços).</span><span class="sxs-lookup"><span data-stu-id="1ee20-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="1ee20-229">Pressione **criar grupo de pessoas** botão.</span><span class="sxs-lookup"><span data-stu-id="1ee20-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="1ee20-230">Uma mensagem de confirmação deve aparecer abaixo do botão.</span><span class="sxs-lookup"><span data-stu-id="1ee20-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="1ee20-231">Se você tiver um erro "Acesso negado", verifique o local em que você definiu para o serviço do Azure.</span><span class="sxs-lookup"><span data-stu-id="1ee20-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="1ee20-232">Como mencionado acima, este aplicativo foi projetado para 'Oeste dos Estados Unidos'.</span><span class="sxs-lookup"><span data-stu-id="1ee20-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ee20-233">Você observará que também é possível clicar o **buscar um grupo conhecido** botão: isso é para se você já tiver criado uma pessoa, grupo e quiser usá-lo, em vez de criar um novo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="1ee20-234">Lembre-se, se você clicar *criar um grupo de pessoas* com um grupo conhecido, isso também buscará um grupo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="1ee20-235">Insira o *nome* da *pessoa* você deseja criar.</span><span class="sxs-lookup"><span data-stu-id="1ee20-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="1ee20-236">Clique o **pessoa crie** botão.</span><span class="sxs-lookup"><span data-stu-id="1ee20-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="1ee20-237">Uma mensagem de confirmação deve aparecer abaixo do botão.</span><span class="sxs-lookup"><span data-stu-id="1ee20-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="1ee20-238">Se você desejar excluir uma pessoa criou anteriormente, você pode escrever o nome na caixa de texto e pressione **excluir pessoa**</span><span class="sxs-lookup"><span data-stu-id="1ee20-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="1ee20-239">Verifique se que você souber o local de dez (10) fotos da pessoa que você deseja adicionar ao seu grupo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="1ee20-240">Pressione **criar e abrir pasta** para abrir o Windows Explorer para a pasta associada à pessoa.</span><span class="sxs-lookup"><span data-stu-id="1ee20-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="1ee20-241">Adicione as imagens de dez (10) na pasta.</span><span class="sxs-lookup"><span data-stu-id="1ee20-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="1ee20-242">Elas devem ter *JPG* ou *PNG* formato de arquivo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="1ee20-243">Clique em **enviar para o Azure**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="1ee20-244">Um contador mostra o estado de envio, seguido por uma mensagem quando ela for concluída.</span><span class="sxs-lookup"><span data-stu-id="1ee20-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="1ee20-245">Depois que o contador foi concluído e uma mensagem de confirmação foi exibida, clique em **treinar** para treinar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="1ee20-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="1ee20-246">Quando o processo for concluído, você está pronto para passar para o Unity.</span><span class="sxs-lookup"><span data-stu-id="1ee20-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="1ee20-247">Capítulo 3 - configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="1ee20-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="1ee20-248">A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="1ee20-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="1ee20-249">Abra *Unity* e clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-249">Open *Unity* and click **New**.</span></span> 

    ![Inicie um novo projeto do Unity.](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="1ee20-251">Agora, você precisará fornecer um nome de projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="1ee20-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="1ee20-252">Inserir **MR_FaceRecognition**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="1ee20-253">Verifique se o tipo de projeto é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="1ee20-254">Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="1ee20-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1ee20-255">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-255">Then, click **Create project**.</span></span>

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="1ee20-257">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="1ee20-258">Vá para **Editar > Preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1ee20-259">Alteração **Editor de Script externo** à **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="1ee20-260">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="1ee20-260">Close the **Preferences** window.</span></span>

    ![Atualize as preferências do editor de script.](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="1ee20-262">Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma **plataforma Universal do Windows**, clicando no **alternar plataforma** botão.</span><span class="sxs-lookup"><span data-stu-id="1ee20-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Crie janela de configurações, alternar a plataforma para a UWP.](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="1ee20-264">Vá para **arquivo > configurações de Build** e certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="1ee20-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="1ee20-265">**Dispositivo de destino** é definido como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="1ee20-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="1ee20-266">Para os fones imersivos em exposição, defina **dispositivo de destino** à *qualquer dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="1ee20-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="1ee20-267">**Tipo de compilação** é definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="1ee20-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="1ee20-268">**SDK** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="1ee20-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="1ee20-269">**Versão do Visual Studio** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="1ee20-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="1ee20-270">**Compilar e executar** é definido como **Máquina Local**</span><span class="sxs-lookup"><span data-stu-id="1ee20-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="1ee20-271">Salve a cena e adicioná-lo para a compilação.</span><span class="sxs-lookup"><span data-stu-id="1ee20-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="1ee20-272">Fazer isso selecionando **cenas abra Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="1ee20-273">Salvamento janela será exibida.</span><span class="sxs-lookup"><span data-stu-id="1ee20-273">A save window will appear.</span></span>

            ![Clique em Adicionar botão cenas aberto](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="1ee20-275">Selecione o **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Criar nova pasta de scripts](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="1ee20-277">Abra seu recém-criado **cenas** pasta e, em seguida, no **nome do arquivo**: campo de texto, digite **FaceRecScene**, em seguida, pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![Dê um nome de nova cena.](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="1ee20-279">O restante de configurações, em *configurações de Build*, deverá ser deixado como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="1ee20-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="1ee20-280">No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="1ee20-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra configurações do player.](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="1ee20-282">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="1ee20-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="1ee20-283">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="1ee20-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="1ee20-284">**Criação de scripts** **versão de tempo de execução** deve ser **Experimental** (equivalente ao .NET 4.6).</span><span class="sxs-lookup"><span data-stu-id="1ee20-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="1ee20-285">Essa alteração irá disparar uma necessidade de reiniciar o Editor.</span><span class="sxs-lookup"><span data-stu-id="1ee20-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="1ee20-286">**Script de back-end** deve ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="1ee20-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="1ee20-287">**Nível de compatibilidade de API** deve ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="1ee20-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Outras configurações de atualização.](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="1ee20-289">Dentro de **configurações de publicação** guia, em **recursos**, verifique:</span><span class="sxs-lookup"><span data-stu-id="1ee20-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="1ee20-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="1ee20-290">**InternetClient**</span></span>
        - <span data-ttu-id="1ee20-291">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="1ee20-291">**Webcam**</span></span>

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="1ee20-293">Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.</span><span class="sxs-lookup"><span data-stu-id="1ee20-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Atualize as configurações de R de X.](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="1ee20-295">Volta *configurações de Build*, **Unity C# projetos** não fica acinzentado; marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="1ee20-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="1ee20-296">Feche a janela de configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="1ee20-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="1ee20-297">Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="1ee20-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="1ee20-298">Capítulo 4 - instalação de câmera principal</span><span class="sxs-lookup"><span data-stu-id="1ee20-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ee20-299">Se você quiser ignorar a *Unity configurar* componente deste curso e continuar diretamente no código, fique à vontade para [baixar esse unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importe-o para seu projeto como um [personalizado Pacote](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="1ee20-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="1ee20-300">Lembre-se de que este pacote também inclui a importação do *DLL Newtonsoft*, abordada [capítulo 5](#chapter-5--import-the-newtonsoft.json-library).</span><span class="sxs-lookup"><span data-stu-id="1ee20-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoft.json-library).</span></span> <span data-ttu-id="1ee20-301">Com isso importado, você pode continuar de [capítulo 6](#chapter-6-create-the-faceanalysis-class).</span><span class="sxs-lookup"><span data-stu-id="1ee20-301">With this imported, you can continue from [Chapter 6](#chapter-6-create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="1ee20-302">No *hierarquia* painel, selecione o **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="1ee20-303">Depois de selecionado, você poderá ver todos os componentes do **câmera principal** na *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="1ee20-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="1ee20-304">O **objeto de câmera** deve ser nomeado **câmera principal** (Observe a ortografia!)</span><span class="sxs-lookup"><span data-stu-id="1ee20-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="1ee20-305">A câmera principal **marca** deve ser definida como **MainCamera** (Observe a ortografia!)</span><span class="sxs-lookup"><span data-stu-id="1ee20-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="1ee20-306">Verifique se o **transformar posição** é definido como **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="1ee20-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="1ee20-307">Definir **limpar os sinalizadores** para **cor sólida**</span><span class="sxs-lookup"><span data-stu-id="1ee20-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="1ee20-308">Defina a **em segundo plano** cor do componente a câmera **preto, alfa 0 (Hex código: 00000000 #)**</span><span class="sxs-lookup"><span data-stu-id="1ee20-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![configurar os componentes de câmera](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="1ee20-310">Capítulo 5 – importar a biblioteca newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="1ee20-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ee20-311">Se você tiver importado o unitypackage' ' na [último capítulo](#chapter-4--main-camera-setup), você pode ignorar este capítulo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4--main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="1ee20-312">Para ajudá-lo a desserializam e serializam os objetos recebidos e enviados para o serviço de Bot, você precisa baixar o *newtonsoft. JSON* biblioteca.</span><span class="sxs-lookup"><span data-stu-id="1ee20-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="1ee20-313">Você encontrará uma versão compatível já organizada com a estrutura de pastas do Unity correta desta [arquivo de pacote do Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="1ee20-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="1ee20-314">Para importar a biblioteca:</span><span class="sxs-lookup"><span data-stu-id="1ee20-314">To import the library:</span></span>

1.  <span data-ttu-id="1ee20-315">Baixe o pacote do Unity.</span><span class="sxs-lookup"><span data-stu-id="1ee20-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="1ee20-316">Clique em **ativos**, **Importar pacote**, **pacote personalizado**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![Importar a biblioteca newtonsoft. JSON](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="1ee20-318">Procure o pacote do Unity que você baixou e clique em Abrir.</span><span class="sxs-lookup"><span data-stu-id="1ee20-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="1ee20-319">Verifique se todos os componentes do pacote estão marcados e clique em **importação**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![Importar a biblioteca newtonsoft. JSON](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="1ee20-321">Capítulo 6 - criar a classe FaceAnalysis</span><span class="sxs-lookup"><span data-stu-id="1ee20-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="1ee20-322">A finalidade da classe FaceAnalysis é hospedar os métodos necessários para se comunicar com o serviço de reconhecimento de Face do Azure.</span><span class="sxs-lookup"><span data-stu-id="1ee20-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="1ee20-323">Depois de enviar o serviço de uma imagem de captura, ele possam analisá-las e identificar as faces dentro e determinar se qualquer pertencem a uma pessoa conhecida.</span><span class="sxs-lookup"><span data-stu-id="1ee20-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="1ee20-324">Se uma pessoa conhecida for encontrada, essa classe exibirá seu nome como texto de interface do usuário na cena.</span><span class="sxs-lookup"><span data-stu-id="1ee20-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="1ee20-325">Para criar o *FaceAnalysis* classe:</span><span class="sxs-lookup"><span data-stu-id="1ee20-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="1ee20-326">Clique com botão direito no *pasta ativos* localizado no painel de projeto, em seguida, clique em **Create** > **pasta**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="1ee20-327">Chame a pasta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-327">Call the folder **Scripts**.</span></span> 

    ![Crie a classe FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="1ee20-329">Clique duas vezes na pasta recém-criada, para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="1ee20-330">Clique com botão direito dentro da pasta, clique em **Create**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="1ee20-331">Chame o script *FaceAnalysis*.</span><span class="sxs-lookup"><span data-stu-id="1ee20-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="1ee20-332">Clique duas vezes na nova *FaceAnalysis* script para abri-lo com o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="1ee20-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="1ee20-333">Insira os seguintes namespaces acima de *FaceAnalysis* classe:</span><span class="sxs-lookup"><span data-stu-id="1ee20-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="1ee20-334">Agora você precisa adicionar todos os objetos que são usados para deserialising.</span><span class="sxs-lookup"><span data-stu-id="1ee20-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="1ee20-335">Esses objetos precisam ser adicionados **fora** da *FaceAnalysis* script (sob a chave inferior).</span><span class="sxs-lookup"><span data-stu-id="1ee20-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

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
7. <span data-ttu-id="1ee20-336">O *Start ()* e *Update ()* métodos não serão usadas, por isso, exclua-os agora.</span><span class="sxs-lookup"><span data-stu-id="1ee20-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="1ee20-337">Dentro de *FaceAnalysis* de classe, adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="1ee20-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

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
    > <span data-ttu-id="1ee20-338">Substitua os **chave** e o **personGroupId** com sua chave de serviço e a Id do grupo que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1ee20-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="1ee20-339">Adicione a *Awake()* método, que initialises a classe, adicionando o *ImageCapture* classe para a câmera principal e chama o método de criação de rótulo:</span><span class="sxs-lookup"><span data-stu-id="1ee20-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

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

10. <span data-ttu-id="1ee20-340">Adicione a *CreateLabel()* método, que cria a *rótulo* objeto para exibir o resultado da análise:</span><span class="sxs-lookup"><span data-stu-id="1ee20-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

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

11. <span data-ttu-id="1ee20-341">Adicione a *DetectFacesFromImage()* e *GetImageAsByteArray()* método.</span><span class="sxs-lookup"><span data-stu-id="1ee20-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="1ee20-342">O primeiro solicitará o serviço de reconhecimento de Face para detectar qualquer possível face na imagem enviada, enquanto o segundo é necessário para converter a imagem capturada em uma matriz de bytes:</span><span class="sxs-lookup"><span data-stu-id="1ee20-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

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

12. <span data-ttu-id="1ee20-343">Adicione a *IdentifyFaces()* método, que solicita a *serviço de reconhecimento de Face* para identificar qualquer face conhecido anteriormente detectado na imagem enviada.</span><span class="sxs-lookup"><span data-stu-id="1ee20-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="1ee20-344">A solicitação retornará uma id da pessoa identificada, mas não o nome:</span><span class="sxs-lookup"><span data-stu-id="1ee20-344">The request will return an id of the identified person but not the name:</span></span>

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

13. <span data-ttu-id="1ee20-345">Adicione a *GetPerson()* método.</span><span class="sxs-lookup"><span data-stu-id="1ee20-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="1ee20-346">Fornecendo a pessoa id, esse método e as solicitações para o *serviço de reconhecimento de Face* para retornar o nome da pessoa identificado:</span><span class="sxs-lookup"><span data-stu-id="1ee20-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

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

14.  <span data-ttu-id="1ee20-347">Lembre-se **salvar** as alterações antes de voltar ao Editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="1ee20-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="1ee20-348">No Editor do Unity, arraste o script FaceAnalysis da pasta Scripts no painel de projeto ao objeto de câmera principal na *painel de hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="1ee20-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="1ee20-349">O novo componente script será então, adicionado à câmera principal.</span><span class="sxs-lookup"><span data-stu-id="1ee20-349">The new script component will be so added to the Main Camera.</span></span> 

![Coloque FaceAnalysis para a câmera principal](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="1ee20-351">Capítulo 7 - criar a classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="1ee20-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="1ee20-352">A finalidade do *ImageCapture* classe é hospedar os métodos necessários para se comunicar com seu *serviço de reconhecimento de Face do Azure* para analisar a imagem que vai capturar, identificando as faces nele e Determinando se ele pertence a uma pessoa conhecida.</span><span class="sxs-lookup"><span data-stu-id="1ee20-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="1ee20-353">Se uma pessoa conhecida for encontrada, essa classe exibirá seu nome como texto de interface do usuário na cena.</span><span class="sxs-lookup"><span data-stu-id="1ee20-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="1ee20-354">Para criar o *ImageCapture* classe:</span><span class="sxs-lookup"><span data-stu-id="1ee20-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="1ee20-355">Com o botão direito dentro de **Scripts** pasta você criou anteriormente e clique em **Create**,  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="1ee20-356">Chame o script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="1ee20-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="1ee20-357">Clique duas vezes na nova *ImageCapture* script para abri-lo com o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="1ee20-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="1ee20-358">Insira os seguintes namespaces acima da classe ImageCapture:</span><span class="sxs-lookup"><span data-stu-id="1ee20-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="1ee20-359">Dentro de *ImageCapture* de classe, adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="1ee20-359">Inside the *ImageCapture* class, add the following variables:</span></span>

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

5.  <span data-ttu-id="1ee20-360">Adicione a *Awake()* e *Start ()* métodos necessários para inicializar a classe e permitir que o HoloLens capturar os gestos do usuário:</span><span class="sxs-lookup"><span data-stu-id="1ee20-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

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

6.  <span data-ttu-id="1ee20-361">Adicione a *TapHandler()* que é chamado quando o usuário executa um *toque* gesto:</span><span class="sxs-lookup"><span data-stu-id="1ee20-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

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

7.  <span data-ttu-id="1ee20-362">Adicione a *ExecuteImageCaptureAndAnalysis()* método, que iniciará o processo de captura de imagem:</span><span class="sxs-lookup"><span data-stu-id="1ee20-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

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

8.  <span data-ttu-id="1ee20-363">Adicione os manipuladores que são chamados quando o processo de captura de foto for concluído:</span><span class="sxs-lookup"><span data-stu-id="1ee20-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

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

9. <span data-ttu-id="1ee20-364">Lembre-se **salvar** as alterações antes de voltar ao Editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="1ee20-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="1ee20-365">Capítulo 8 - Compilando a solução</span><span class="sxs-lookup"><span data-stu-id="1ee20-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="1ee20-366">Para executar um teste completo de seu aplicativo você precisará para fazer sideload dele para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1ee20-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="1ee20-367">Antes de começar, verifique se:</span><span class="sxs-lookup"><span data-stu-id="1ee20-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="1ee20-368">Todas as configurações mencionadas no capítulo 3 estão definidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="1ee20-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="1ee20-369">O script *FaceAnalysis* está anexado ao objeto de câmera principal.</span><span class="sxs-lookup"><span data-stu-id="1ee20-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="1ee20-370">Ambas as a **Auth Key** e **Id do grupo** tiver sido definida dentro a *FaceAnalysis* script.</span><span class="sxs-lookup"><span data-stu-id="1ee20-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="1ee20-371">Esse ponto você está pronto para compilar a solução.</span><span class="sxs-lookup"><span data-stu-id="1ee20-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="1ee20-372">Depois que a solução foi criada, você estará pronto para implantar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="1ee20-373">Para iniciar o processo de compilação:</span><span class="sxs-lookup"><span data-stu-id="1ee20-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="1ee20-374">Salve a cena atual clicando em arquivo, salvar.</span><span class="sxs-lookup"><span data-stu-id="1ee20-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="1ee20-375">Ir para o arquivo de configurações de compilação, clique em Adicionar cenas aberto.</span><span class="sxs-lookup"><span data-stu-id="1ee20-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="1ee20-376">Lembre-se de escala Unity C# projetos.</span><span class="sxs-lookup"><span data-stu-id="1ee20-376">Make sure to tick Unity C# Projects.</span></span>

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="1ee20-378">Pressione a compilação.</span><span class="sxs-lookup"><span data-stu-id="1ee20-378">Press Build.</span></span> <span data-ttu-id="1ee20-379">Ao fazer isso, o Unity iniciará uma janela do Explorador de arquivos, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em.</span><span class="sxs-lookup"><span data-stu-id="1ee20-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="1ee20-380">Criar pasta agora, dentro do projeto do Unity e chamá-lo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="1ee20-381">Em seguida, com a pasta do aplicativo, pressione Selecionar pasta.</span><span class="sxs-lookup"><span data-stu-id="1ee20-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="1ee20-382">Unity começará a compilar seu projeto para a pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="1ee20-383">Uma vez Unity terminou de construção (pode levar algum tempo), ele abrirá uma janela do Explorador de arquivos no local de sua compilação.</span><span class="sxs-lookup"><span data-stu-id="1ee20-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="1ee20-385">Abra a pasta de aplicativo e, em seguida, abra a nova solução de projeto (como visto acima, MR_FaceRecognition.sln).</span><span class="sxs-lookup"><span data-stu-id="1ee20-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="1ee20-386">Capítulo 9 - implantação de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1ee20-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="1ee20-387">Para implantar o HoloLens:</span><span class="sxs-lookup"><span data-stu-id="1ee20-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="1ee20-388">Será necessário o endereço IP do seu HoloLens (para a implantação remota) e garantir que seu HoloLens está em **modo de desenvolvedor**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="1ee20-389">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="1ee20-389">To do this:</span></span>

    1. <span data-ttu-id="1ee20-390">Durante o uso de seu HoloLens, abra o **configurações**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="1ee20-391">Vá para **rede e Internet > Wi-Fi > Opções avançadas**</span><span class="sxs-lookup"><span data-stu-id="1ee20-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="1ee20-392">Observe a **IPv4** endereço.</span><span class="sxs-lookup"><span data-stu-id="1ee20-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="1ee20-393">Em seguida, navegue até **as configurações**e, em seguida, para **atualização e segurança > para desenvolvedores**</span><span class="sxs-lookup"><span data-stu-id="1ee20-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="1ee20-394">Definir o modo de desenvolvedor em.</span><span class="sxs-lookup"><span data-stu-id="1ee20-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="1ee20-395">Navegue até seu novo build do Unity (o *App* pasta) e abra o arquivo de solução com *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="1ee20-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="1ee20-396">No, selecione a configuração da solução **depurar**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="1ee20-397">Na plataforma da solução, selecione **x86**, **máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="1ee20-399">Vá para o **menu Build** e clique em **implantar solução**, carregar o aplicativo para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1ee20-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="1ee20-400">Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="1ee20-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="1ee20-401">Para implantar o fone de ouvido imersivo, defina as **plataforma da solução** para *Máquina Local*e defina o **configuração** para *depurar*, com *x86* como o **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="1ee20-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="1ee20-402">Em seguida, implantar no local de máquina, usando o **menu Build**, selecionando *implantar solução*.</span><span class="sxs-lookup"><span data-stu-id="1ee20-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="1ee20-403">Capítulo 10 - como usar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="1ee20-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="1ee20-404">Use o HoloLens, inicie o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="1ee20-405">Examinar a pessoa que você registrou com o *API de detecção facial*.</span><span class="sxs-lookup"><span data-stu-id="1ee20-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="1ee20-406">Certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="1ee20-406">Make sure that:</span></span>

    -  <span data-ttu-id="1ee20-407">Face da pessoa não está muito distante e claramente visíveis</span><span class="sxs-lookup"><span data-stu-id="1ee20-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="1ee20-408">A iluminação ambiente não está muito escura</span><span class="sxs-lookup"><span data-stu-id="1ee20-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="1ee20-409">Use o gesto de tocar para capturar a imagem da pessoa.</span><span class="sxs-lookup"><span data-stu-id="1ee20-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="1ee20-410">Aguarde até que o aplicativo enviar a solicitação de análise e receber uma resposta.</span><span class="sxs-lookup"><span data-stu-id="1ee20-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="1ee20-411">Se a pessoa que foi reconhecida com sucesso, o nome da pessoa será exibido como texto de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1ee20-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="1ee20-412">Você pode repetir o processo de captura usando o gesto de toque de alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="1ee20-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="1ee20-413">Seu aplicativo de API de detecção facial do Azure concluída</span><span class="sxs-lookup"><span data-stu-id="1ee20-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="1ee20-414">Parabéns, você criou um aplicativo de realidade mista que aproveita o serviço de reconhecimento de Face do Azure para detectar faces dentro de uma imagem e identificar qualquer faces conhecidos.</span><span class="sxs-lookup"><span data-stu-id="1ee20-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![resultado de concluírem este curso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="1ee20-416">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="1ee20-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="1ee20-417">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="1ee20-417">Exercise 1</span></span>

<span data-ttu-id="1ee20-418">O **API de detecção facial Azure** é poderoso o suficiente para detectar até 64 faces em uma única imagem.</span><span class="sxs-lookup"><span data-stu-id="1ee20-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="1ee20-419">Estenda o aplicativo, para que ele poderia reconhece dois ou três faces, entre muitas outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="1ee20-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="1ee20-420">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="1ee20-420">Exercise 2</span></span>

<span data-ttu-id="1ee20-421">O **API de detecção facial Azure** também é capaz de realizar todos os tipos de informações de atributo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="1ee20-422">Integre isso ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee20-422">Integrate this into the application.</span></span> <span data-ttu-id="1ee20-423">Isso pode ser ainda mais interessante, quando combinado com o [API de emoções](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span><span class="sxs-lookup"><span data-stu-id="1ee20-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
