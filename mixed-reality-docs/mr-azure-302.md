---
title: MR e 302 do Azure - visão do computador
description: Conclua este curso para aprender a reconhecer conteúdo visual em uma imagem fornecido, usando a visão do computador do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, pesquisa Visual computacional, hololens, imersivo, vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589150"
---
>[!NOTE]
><span data-ttu-id="40da8-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="40da8-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="40da8-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="40da8-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="40da8-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="40da8-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="40da8-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="40da8-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="40da8-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="40da8-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="40da8-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="40da8-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="40da8-110">MR e 302 do Azure: Pesquisa Visual computacional</span><span class="sxs-lookup"><span data-stu-id="40da8-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="40da8-111">Neste curso, você aprenderá a reconhecer conteúdo visual em uma imagem fornecido, usando recursos de pesquisa Visual computacional do Azure em um aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="40da8-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="40da8-112">Resultados do reconhecimento serão exibidos como marcas descritivas.</span><span class="sxs-lookup"><span data-stu-id="40da8-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="40da8-113">Você pode usar esse serviço sem a necessidade para treinar um modelo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="40da8-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="40da8-114">Se a sua implementação exija treinar um modelo de aprendizado de máquina, consulte [MR e Azure 302b](mr-azure-302b.md).</span><span class="sxs-lookup"><span data-stu-id="40da8-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![resultado de laboratório](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="40da8-116">A visão da Microsoft de computador é um conjunto de APIs projetados para fornecer aos desenvolvedores de processamento de imagens e análise (com informações de retorno), usando algoritmos avançados, tudo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="40da8-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="40da8-117">Os desenvolvedores carregar uma imagem ou URL da imagem e os algoritmos de API de visão do computador Microsoft analisar o conteúdo visual, com base em entradas escolhidas o usuário, que, em seguida, pode retornar informações, incluindo, identificando o tipo e a qualidade de uma imagem, detectar rostos humanos ( retornando suas coordenadas) e a marcação ou categorizar imagens.</span><span class="sxs-lookup"><span data-stu-id="40da8-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="40da8-118">Para obter mais informações, visite o [página de API de visão do computador Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span><span class="sxs-lookup"><span data-stu-id="40da8-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="40da8-119">Com a conclusão deste curso, você terá uma realidade misturada aplicativo HoloLens, que será capaz de fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="40da8-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="40da8-120">Usando o gesto de toque, a câmera do HoloLens irá capturar uma imagem.</span><span class="sxs-lookup"><span data-stu-id="40da8-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="40da8-121">A imagem será enviada ao serviço de API de visão do computador do Azure.</span><span class="sxs-lookup"><span data-stu-id="40da8-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="40da8-122">Os objetos reconhecidos serão listados em um grupo de interface do usuário simple posicionado na cena Unity.</span><span class="sxs-lookup"><span data-stu-id="40da8-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="40da8-123">Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="40da8-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="40da8-124">Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="40da8-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="40da8-125">Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="40da8-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="40da8-126">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="40da8-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="40da8-127">Curso</span><span class="sxs-lookup"><span data-stu-id="40da8-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="40da8-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="40da8-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="40da8-129"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="40da8-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="40da8-130">MR e 302 do Azure: Pesquisa Visual computacional</span><span class="sxs-lookup"><span data-stu-id="40da8-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="40da8-131">✔️</span><span class="sxs-lookup"><span data-stu-id="40da8-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="40da8-132">✔️</span><span class="sxs-lookup"><span data-stu-id="40da8-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="40da8-133">Enquanto este curso se concentra principalmente em HoloLens, você também pode aplicar o que você aprenderá neste curso para fones de ouvido Windows Mixed Reality de imersão (VR).</span><span class="sxs-lookup"><span data-stu-id="40da8-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="40da8-134">Como fones imersivos em exposição (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="40da8-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="40da8-135">Como acompanhar o curso, você verá notas quaisquer alterações que você talvez precise ser empregadas para dar suporte a fones imersivos em exposição (VR).</span><span class="sxs-lookup"><span data-stu-id="40da8-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="40da8-136">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="40da8-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="40da8-137">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="40da8-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="40da8-138">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="40da8-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="40da8-139">Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .</span><span class="sxs-lookup"><span data-stu-id="40da8-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="40da8-140">Recomendamos que o hardware e software para este curso a seguir:</span><span class="sxs-lookup"><span data-stu-id="40da8-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="40da8-141">Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)</span><span class="sxs-lookup"><span data-stu-id="40da8-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="40da8-142">Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="40da8-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="40da8-143">O SDK mais recente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="40da8-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="40da8-144">2017.4 do Unity</span><span class="sxs-lookup"><span data-stu-id="40da8-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="40da8-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="40da8-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="40da8-146">Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="40da8-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="40da8-147">Uma câmera conectada ao seu PC (para desenvolvimento imersivo fone de ouvido)</span><span class="sxs-lookup"><span data-stu-id="40da8-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="40da8-148">Acesso à Internet para a instalação do Azure e a recuperação de API de visão do computador</span><span class="sxs-lookup"><span data-stu-id="40da8-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="40da8-149">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="40da8-149">Before you start</span></span>

1.  <span data-ttu-id="40da8-150">Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="40da8-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="40da8-151">Configurar e testar o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="40da8-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="40da8-152">Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="40da8-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="40da8-153">É uma boa ideia executar calibragem e ajuste de Sensor ao começar a desenvolver um new App HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="40da8-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="40da8-154">Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="40da8-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="40da8-155">Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="40da8-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="40da8-156">Capítulo 1 – Portal do Azure</span><span class="sxs-lookup"><span data-stu-id="40da8-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="40da8-157">Para usar o *API de visão do computador* serviço no Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40da8-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="40da8-158">Primeiro, faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="40da8-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="40da8-159">Se você ainda não tiver uma conta do Azure, você precisará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="40da8-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="40da8-160">Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="40da8-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="40da8-161">Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure *API de visão do computador*e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="40da8-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![Criar um novo recurso no Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="40da8-163">A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="40da8-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="40da8-164">A nova página fornecerá uma descrição do *API de visão do computador* service.</span><span class="sxs-lookup"><span data-stu-id="40da8-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="40da8-165">Na parte inferior esquerda desta página, selecione a **criar** botão para criar uma associação com este serviço.</span><span class="sxs-lookup"><span data-stu-id="40da8-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![Sobre o serviço de api de visão do computador](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="40da8-167">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="40da8-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="40da8-168">Inserir sua desejada **nome** para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="40da8-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="40da8-169">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="40da8-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="40da8-170">Selecione o **tipo de preço** apropriado para você, se esse for o primeiro tempo para criar um *API de visão do computador* serviço, uma camada gratuita (chamada F0) deve estar disponível para você.</span><span class="sxs-lookup"><span data-stu-id="40da8-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="40da8-171">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="40da8-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="40da8-172">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="40da8-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="40da8-173">É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="40da8-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="40da8-174">Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="40da8-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="40da8-175">Determine o local para seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="40da8-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="40da8-176">O local seria o ideal é que na região em que o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="40da8-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="40da8-177">Alguns ativos do Azure estão disponíveis somente em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="40da8-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="40da8-178">Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="40da8-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="40da8-179">Clique em criar.</span><span class="sxs-lookup"><span data-stu-id="40da8-179">Click Create.</span></span>

        ![Informações de criação de serviço](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="40da8-181">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="40da8-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="40da8-182">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="40da8-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Veja a nova notificação para seu novo serviço](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="40da8-184">Clique na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="40da8-184">Click on the notification to explore your new Service instance.</span></span> 

    ![Selecione o botão Ir para o recurso.](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="40da8-186">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="40da8-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="40da8-187">Você será levado para a nova instância de serviço de API de visão do computador.</span><span class="sxs-lookup"><span data-stu-id="40da8-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![Seu novo serviço de API de visão do computador](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="40da8-189">Dentro deste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, que é feito por meio do uso de chave de assinatura do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="40da8-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="40da8-190">Dos *início rápido* página, de seu *API de visão do computador* do serviço, navegue até a primeira etapa, *pegue suas chaves*e clique em **chaves** ( Você também pode obter isso clicando no hiperlink azul chaves, localizado no menu de navegação de serviços, indicado pelo ícone de chave).</span><span class="sxs-lookup"><span data-stu-id="40da8-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="40da8-191">Isso irá revelar o seu serviço *chaves*.</span><span class="sxs-lookup"><span data-stu-id="40da8-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="40da8-192">Faça uma cópia de uma das chaves exibidas, pois precisará dele posteriormente em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="40da8-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="40da8-193">Volte para o *início rápido* da página e a partir daí, buscar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="40da8-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="40da8-194">Lembre-se de que seu site pode ser diferente, dependendo da sua região (que se for, você precisará fazer uma alteração em seu código mais tarde).</span><span class="sxs-lookup"><span data-stu-id="40da8-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="40da8-195">Faça uma cópia desse ponto de extremidade para uso posterior:</span><span class="sxs-lookup"><span data-stu-id="40da8-195">Take a copy of this endpoint for use later:</span></span>

    ![Seu novo serviço de API de visão do computador](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="40da8-197">Você pode verificar quais são os vários pontos de extremidade [aqui](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="40da8-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="40da8-198">Capítulo 2 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="40da8-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="40da8-199">A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="40da8-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="40da8-200">Abra *Unity* e clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="40da8-200">Open *Unity* and click **New**.</span></span> 

    ![Inicie um novo projeto do Unity.](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="40da8-202">Agora, você precisará fornecer um nome de projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="40da8-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="40da8-203">Inserir **MR_ComputerVision**.</span><span class="sxs-lookup"><span data-stu-id="40da8-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="40da8-204">Verifique se o tipo de projeto é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="40da8-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="40da8-205">Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="40da8-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="40da8-206">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="40da8-206">Then, click **Create project**.</span></span>

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="40da8-208">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="40da8-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="40da8-209">Vá para **Editar > Preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="40da8-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="40da8-210">Alteração **Editor de Script externo** à **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="40da8-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="40da8-211">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="40da8-211">Close the **Preferences** window.</span></span>

    ![Atualize as preferências do editor de script.](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="40da8-213">Em seguida, vá para **arquivo > configurações de Build** e selecione **plataforma Universal do Windows**, em seguida, clique no **alternar plataforma** botão Aplicar sua seleção.</span><span class="sxs-lookup"><span data-stu-id="40da8-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Crie janela de configurações, alternar a plataforma para a UWP.](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="40da8-215">Enquanto estiver na **arquivo > configurações de Build** e certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="40da8-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="40da8-216">**Dispositivo de destino** é definido como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="40da8-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="40da8-217">Para os fones imersivos em exposição, defina **dispositivo de destino** à *qualquer dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="40da8-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="40da8-218">**Tipo de compilação** é definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="40da8-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="40da8-219">**SDK** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="40da8-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="40da8-220">**Versão do Visual Studio** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="40da8-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="40da8-221">**Compilar e executar** é definido como **Máquina Local**</span><span class="sxs-lookup"><span data-stu-id="40da8-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="40da8-222">Salve a cena e adicioná-lo para a compilação.</span><span class="sxs-lookup"><span data-stu-id="40da8-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="40da8-223">Fazer isso selecionando **cenas abra Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="40da8-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="40da8-224">Salvamento janela será exibida.</span><span class="sxs-lookup"><span data-stu-id="40da8-224">A save window will appear.</span></span>
        
            ![Clique em Adicionar botão cenas aberto](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="40da8-226">Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.</span><span class="sxs-lookup"><span data-stu-id="40da8-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Criar nova pasta de scripts](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="40da8-228">Abrir seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo*: campo de texto, digite **MR_ComputerVisionScene**, em seguida, clique em **salvar** .</span><span class="sxs-lookup"><span data-stu-id="40da8-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![Dê um nome de nova cena.](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="40da8-230">Esteja ciente de que você deve salvar suas cenas de Unity dentro do *ativos* pasta, pois eles devem estar associados ao projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="40da8-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="40da8-231">Criando a pasta de cenas (e outras pastas semelhantes) é uma maneira comum de estruturar um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="40da8-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="40da8-232">O restante de configurações, em *configurações de Build*, deverá ser deixado como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="40da8-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="40da8-233">No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="40da8-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra configurações do player.](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="40da8-235">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="40da8-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="40da8-236">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="40da8-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="40da8-237">**Versão de tempo de execução de scripts** deve ser **estável** (.NET 3.5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="40da8-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="40da8-238">**Script de back-end** deve ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="40da8-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="40da8-239">**Nível de compatibilidade de API** deve ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="40da8-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Outras configurações de atualização.](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="40da8-241">Dentro de **configurações de publicação** guia, em **recursos**, verifique:</span><span class="sxs-lookup"><span data-stu-id="40da8-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="40da8-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="40da8-242">**InternetClient**</span></span>
        2. <span data-ttu-id="40da8-243">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="40da8-243">**Webcam**</span></span>

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="40da8-245">Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.</span><span class="sxs-lookup"><span data-stu-id="40da8-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Atualize as configurações de R de X.](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="40da8-247">Volta *configurações de Build* _Unity C#_  projetos não fica acinzentado; marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="40da8-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="40da8-248">Feche a janela de configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="40da8-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="40da8-249">Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="40da8-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="40da8-250">Capítulo 3 – instalação de câmera principal</span><span class="sxs-lookup"><span data-stu-id="40da8-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40da8-251">Se você quiser ignorar a *configurar o Unity* componente deste curso e continuar diretamente no código, fique à vontade para baixá-lo [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), importá-lo para seu projeto como um [pacote personalizado ](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 5](#chapter-5--create-the-resultslabel-class).</span><span class="sxs-lookup"><span data-stu-id="40da8-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="40da8-252">No *painel de hierarquia*, selecione o **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="40da8-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="40da8-253">Depois de selecionado, você poderá ver todos os componentes do **câmera principal** na *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="40da8-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="40da8-254">O **objeto de câmera** deve ser nomeado **câmera principal** (Observe a ortografia!)</span><span class="sxs-lookup"><span data-stu-id="40da8-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="40da8-255">A câmera principal **marca** deve ser definida como **MainCamera** (Observe a ortografia!)</span><span class="sxs-lookup"><span data-stu-id="40da8-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="40da8-256">Verifique se o **transformar posição** é definido como **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="40da8-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="40da8-257">Definir **Limpar sinalizadores** à **cor sólida** (Ignorar para fone de ouvido imersivo).</span><span class="sxs-lookup"><span data-stu-id="40da8-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="40da8-258">Definir a **em segundo plano** cor do componente a câmera **preto, alfa 0 (código hexadecimal: #00000000)** (Ignorar para fone de ouvido imersivo).</span><span class="sxs-lookup"><span data-stu-id="40da8-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![Atualize os componentes de câmera.](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="40da8-260">Em seguida, você terá que criar um objeto simples "Cursor" anexado à **câmera principal**, que ajudam a posicionar a análise de imagem produzirá quando o aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="40da8-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="40da8-261">Esse Cursor determinará o ponto central do foco da câmera.</span><span class="sxs-lookup"><span data-stu-id="40da8-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="40da8-262">Para criar o Cursor:</span><span class="sxs-lookup"><span data-stu-id="40da8-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="40da8-263">No *painel de hierarquia*, clique com botão direito no **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="40da8-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="40da8-264">Sob **objeto 3D**, clique em **esfera**.</span><span class="sxs-lookup"><span data-stu-id="40da8-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![Selecione o objeto de Cursor.](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="40da8-266">Renomear a **esfera** à **Cursor** (clique duas vezes o objeto de Cursor ou pressione o botão de teclado 'F2' com o objeto selecionado) e verifique se ele está localizado como filho do **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="40da8-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="40da8-267">No *painel de hierarquia*, clique com o botão esquerdo na **Cursor**.</span><span class="sxs-lookup"><span data-stu-id="40da8-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="40da8-268">Com o Cursor selecionado, ajustar as seguintes variáveis na *painel Inspetor*:</span><span class="sxs-lookup"><span data-stu-id="40da8-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="40da8-269">Defina as *transformar posição* para **0, 0, 5**</span><span class="sxs-lookup"><span data-stu-id="40da8-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="40da8-270">Defina as *dimensionamento* para **0,02, 0,02, 0,02**</span><span class="sxs-lookup"><span data-stu-id="40da8-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![Atualize a posição de transformação e a escala.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="40da8-272">Capítulo 4-instalação do sistema de rótulo</span><span class="sxs-lookup"><span data-stu-id="40da8-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="40da8-273">Depois de capturar uma imagem com câmera dos HoloLens, essa imagem será enviada para seu *API de visão do computador Azure* instância de serviço para análise.</span><span class="sxs-lookup"><span data-stu-id="40da8-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="40da8-274">Os resultados dessa análise será uma lista de objetos, reconhecidos chamado **marcas**.</span><span class="sxs-lookup"><span data-stu-id="40da8-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="40da8-275">Você usará rótulos (como um texto 3D no espaço de mundo) para exibir essas marcas no local em que a foto foi tirada.</span><span class="sxs-lookup"><span data-stu-id="40da8-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="40da8-276">As etapas a seguir mostram como configurar o **rótulo** objeto.</span><span class="sxs-lookup"><span data-stu-id="40da8-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="40da8-277">Clique com botão direito em qualquer lugar no painel de hierarquia (o local no momento não importa), sob **objeto 3D**, adicione uma **texto 3D**.</span><span class="sxs-lookup"><span data-stu-id="40da8-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="40da8-278">Denomine **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="40da8-278">Name it **LabelText**.</span></span>

    ![Crie objeto de texto 3D.](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="40da8-280">No *painel de hierarquia*, clique com o botão esquerdo na **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="40da8-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="40da8-281">Com o **LabelText** selecionado, ajustar as seguintes variáveis na *painel Inspetor*:</span><span class="sxs-lookup"><span data-stu-id="40da8-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="40da8-282">Defina as **posição** para **0, 0,0**</span><span class="sxs-lookup"><span data-stu-id="40da8-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="40da8-283">Defina as **dimensionamento** para **0,01, 0,01, 0,01**</span><span class="sxs-lookup"><span data-stu-id="40da8-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="40da8-284">No componente **texto de malha**:</span><span class="sxs-lookup"><span data-stu-id="40da8-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="40da8-285">Substitua todo o texto dentro **texto**, com "..."</span><span class="sxs-lookup"><span data-stu-id="40da8-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="40da8-286">Defina as **âncora** para **parte intermediária central**</span><span class="sxs-lookup"><span data-stu-id="40da8-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="40da8-287">Defina as **alinhamento** para **Center**</span><span class="sxs-lookup"><span data-stu-id="40da8-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="40da8-288">Defina as **tamanho da tabulação** para **4**</span><span class="sxs-lookup"><span data-stu-id="40da8-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="40da8-289">Defina as **Font Size** para **50**</span><span class="sxs-lookup"><span data-stu-id="40da8-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="40da8-290">Defina as **cor** para **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="40da8-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![Componente de texto](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="40da8-292">Arraste o **LabelText** da *painel de hierarquia*, no *pasta ativo*, dentro no *painel do projeto*.</span><span class="sxs-lookup"><span data-stu-id="40da8-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="40da8-293">Isso fará com que o **LabelText** um pré-fabricado, portanto, o que ele pode ser instanciado no código.</span><span class="sxs-lookup"><span data-stu-id="40da8-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![Crie um pré-fabricado do objeto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="40da8-295">Você deve excluir o **LabelText** da *painel de hierarquia*, de modo que ele não será exibido na cena de abertura.</span><span class="sxs-lookup"><span data-stu-id="40da8-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="40da8-296">Como é agora um pré-fabricado, o que será chamado para instâncias individuais da sua pasta de ativos, não é necessário para mantê-la dentro da cena.</span><span class="sxs-lookup"><span data-stu-id="40da8-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="40da8-297">A estrutura de objeto final na *painel de hierarquia* deve ser semelhante à mostrada na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="40da8-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![Estrutura final do painel de hierarquia.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="40da8-299">Capítulo 5 – criar a classe ResultsLabel</span><span class="sxs-lookup"><span data-stu-id="40da8-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="40da8-300">É o primeiro script que você precisa criar o *ResultsLabel* classe, que é responsável pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="40da8-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="40da8-301">Criando os rótulos no espaço de mundo apropriado, em relação a posição da câmera.</span><span class="sxs-lookup"><span data-stu-id="40da8-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="40da8-302">Exibindo as marcas do enorme de imagem.</span><span class="sxs-lookup"><span data-stu-id="40da8-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="40da8-303">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="40da8-303">To create this class:</span></span> 

1.  <span data-ttu-id="40da8-304">Clique com botão direito no *painel do projeto*, em seguida, **criar > pasta**.</span><span class="sxs-lookup"><span data-stu-id="40da8-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="40da8-305">Nomeie a pasta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="40da8-305">Name the folder **Scripts**.</span></span> 

    ![Crie a pasta de scripts.](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="40da8-307">Com o **Scripts** pasta criar, clique duas vezes nele para abrir.</span><span class="sxs-lookup"><span data-stu-id="40da8-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="40da8-308">Em seguida, dentro dessa pasta, clique com botão direito e selecione **criar >** , em seguida,  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="40da8-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="40da8-309">Nomeie o script *ResultsLabel*.</span><span class="sxs-lookup"><span data-stu-id="40da8-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="40da8-310">Clique duas vezes na nova *ResultsLabel* script para abri-lo com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="40da8-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="40da8-311">Dentro da classe, insira o seguinte código na *ResultsLabel* classe:</span><span class="sxs-lookup"><span data-stu-id="40da8-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  <span data-ttu-id="40da8-312">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="40da8-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="40da8-313">Na *Editor do Unity*, clique e arraste o *ResultsLabel* classe da **Scripts** pasta para o **câmera principal** objeto no  *Painel de hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="40da8-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="40da8-314">Clique no **câmera principal** e examine o *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="40da8-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="40da8-315">Você vai notar que o script que você acabou de arrastar para a câmera, há dois campos: **Cursor** e **rotular pré-fabricado**.</span><span class="sxs-lookup"><span data-stu-id="40da8-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="40da8-316">Arraste o objeto chamado **Cursor** da *painel de hierarquia* para o slot chamado **Cursor**, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="40da8-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="40da8-317">Arraste o objeto chamado **LabelText** da *pasta ativos* no *painel projeto* para o slot chamado **rótulo pré-fabricado**, conforme mostrado no imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="40da8-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![Defina as metas de referência dentro do Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="40da8-319">Capítulo 6 – criar a classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="40da8-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="40da8-320">A próxima classe que você pretende criar é a *ImageCapture* classe.</span><span class="sxs-lookup"><span data-stu-id="40da8-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="40da8-321">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="40da8-321">This class is responsible for:</span></span>

-   <span data-ttu-id="40da8-322">Capturar uma imagem usando a HoloLens câmera e armazená-lo na pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40da8-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="40da8-323">Capturando os gestos de toque do usuário.</span><span class="sxs-lookup"><span data-stu-id="40da8-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="40da8-324">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="40da8-324">To create this class:</span></span> 

1.  <span data-ttu-id="40da8-325">Vá para o **Scripts** pasta que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="40da8-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="40da8-326">Clique com botão direito dentro da pasta **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="40da8-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="40da8-327">Chame o script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="40da8-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="40da8-328">Clique duas vezes na nova *ImageCapture* script para abri-lo com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="40da8-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="40da8-329">Adicione os namespaces a seguir na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="40da8-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="40da8-330">Em seguida, adicione as seguintes variáveis dentro de *ImageCapture* classe acima a *Start ()* método:</span><span class="sxs-lookup"><span data-stu-id="40da8-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="40da8-331">O **tapsCount** variável armazenará o número de gestos de toque capturados do usuário.</span><span class="sxs-lookup"><span data-stu-id="40da8-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="40da8-332">Esse número é usado na nomeação das imagens capturadas.</span><span class="sxs-lookup"><span data-stu-id="40da8-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="40da8-333">Código para o *Awake()* e *Start ()* métodos agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="40da8-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="40da8-334">Eles serão chamados quando inicializa a classe:</span><span class="sxs-lookup"><span data-stu-id="40da8-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="40da8-335">Implemente um manipulador que será chamado quando ocorre um gesto de tocar.</span><span class="sxs-lookup"><span data-stu-id="40da8-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
<span data-ttu-id="40da8-336">O *TapHandler()* método incrementa o número de toques capturados do usuário e usa a posição do Cursor atual para determinar onde posicionar um novo rótulo.</span><span class="sxs-lookup"><span data-stu-id="40da8-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="40da8-337">Esse método, em seguida, chama o *ExecuteImageCaptureAndAnalysis()* método para iniciar a funcionalidade principal desse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40da8-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="40da8-338">Depois que uma imagem foi capturada e armazenada, os seguintes manipuladores serão chamados.</span><span class="sxs-lookup"><span data-stu-id="40da8-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="40da8-339">Se o processo for bem-sucedida, o resultado é passado para o *VisionManager* (que ainda estão criar) para análise.</span><span class="sxs-lookup"><span data-stu-id="40da8-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  <span data-ttu-id="40da8-340">Em seguida, adicione o método que o aplicativo usa para iniciar o processo de captura de imagem e armazenar a imagem.</span><span class="sxs-lookup"><span data-stu-id="40da8-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> <span data-ttu-id="40da8-341">Neste ponto, você observará um erro que aparecem na *painel de Console do Editor do Unity*.</span><span class="sxs-lookup"><span data-stu-id="40da8-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="40da8-342">Isso ocorre porque o código faz referência a *VisionManager* classe que você criará no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="40da8-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="40da8-343">Capítulo 7 – chamada para o Azure e análise de imagem</span><span class="sxs-lookup"><span data-stu-id="40da8-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="40da8-344">É o último script que você precisa criar o *VisionManager* classe.</span><span class="sxs-lookup"><span data-stu-id="40da8-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="40da8-345">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="40da8-345">This class is responsible for:</span></span>

-   <span data-ttu-id="40da8-346">Carregando a imagem mais recente capturada como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="40da8-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="40da8-347">Enviando a matriz de bytes para seu *API de visão do computador Azure* instância de serviço para análise.</span><span class="sxs-lookup"><span data-stu-id="40da8-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="40da8-348">Recebendo a resposta como uma cadeia de caracteres JSON.</span><span class="sxs-lookup"><span data-stu-id="40da8-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="40da8-349">Ao desserializar a resposta e passando as marcas resultantes para o *ResultsLabel* classe.</span><span class="sxs-lookup"><span data-stu-id="40da8-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="40da8-350">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="40da8-350">To create this class:</span></span>

1.  <span data-ttu-id="40da8-351">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="40da8-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="40da8-352">Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="40da8-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="40da8-353">Nomeie o script *VisionManager*.</span><span class="sxs-lookup"><span data-stu-id="40da8-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="40da8-354">Clique duas vezes no novo script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40da8-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="40da8-355">Atualizar os namespaces para ser o mesmo que o seguinte, na parte superior do *VisionManager* classe:</span><span class="sxs-lookup"><span data-stu-id="40da8-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="40da8-356">Na parte superior do seu script *dentro de* o *VisionManager* classe (acima a *Start ()* método), agora você precisa criar dois *Classes* que representa a resposta JSON desserializada do Azure:</span><span class="sxs-lookup"><span data-stu-id="40da8-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="40da8-357">O *TagData* e *AnalysedObject* classes precisam ter o *[System.Serializable]* atributo adicionado antes da declaração para poder ser desserializado com o Unity bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="40da8-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="40da8-358">Na classe VisionManager, você deve adicionar as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="40da8-358">In the VisionManager class, you should add the following variables:</span></span>

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > <span data-ttu-id="40da8-359">Certifique-se de inserir sua **Auth Key** para o **authorizationKey** variável.</span><span class="sxs-lookup"><span data-stu-id="40da8-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="40da8-360">Você será observou sua **Auth Key** no início deste curso [capítulo 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="40da8-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="40da8-361">O **visionAnalysisEndpoint** variável pode ser diferente do especificado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="40da8-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="40da8-362">O **west-us** estritamente refere-se a instâncias de serviço criadas para a região Oeste dos EUA.</span><span class="sxs-lookup"><span data-stu-id="40da8-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="40da8-363">Atualize-o com seu [URL de ponto de extremidade](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); aqui estão alguns exemplos do que podem parecer com:</span><span class="sxs-lookup"><span data-stu-id="40da8-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="40da8-364">Europa Ocidental: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="40da8-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="40da8-365">Sudeste da Ásia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="40da8-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="40da8-366">Leste da Austrália: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="40da8-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="40da8-367">Agora o código para Awake precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="40da8-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="40da8-368">Em seguida, adicione a corrotina (com o fluxo estático método abaixo dele), que irá obter os resultados da análise da imagem capturada pelo *ImageCapture* classe.</span><span class="sxs-lookup"><span data-stu-id="40da8-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  <span data-ttu-id="40da8-369">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="40da8-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="40da8-370">No Editor do Unity, clique em Voltar e arraste o *VisionManager* e *ImageCapture* as classes do **Scripts** pasta para o **câmera principal**objeto de *painel de hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="40da8-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="40da8-371">Capítulo 8 – antes da construção</span><span class="sxs-lookup"><span data-stu-id="40da8-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="40da8-372">Para executar um teste completo de seu aplicativo você precisará para fazer sideload dele para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="40da8-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="40da8-373">Antes de começar, verifique se:</span><span class="sxs-lookup"><span data-stu-id="40da8-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="40da8-374">Todas as configurações mencionadas [capítulo 2](#chapter-2--set-up-the-unity-project) estão definidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="40da8-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="40da8-375">Todos os scripts são anexados para o **câmera principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="40da8-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="40da8-376">Todos os campos a *painel de Inspetor de câmera principal* são atribuídas corretamente.</span><span class="sxs-lookup"><span data-stu-id="40da8-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="40da8-377">Certifique-se de inserir sua **Auth Key** para o **authorizationKey** variável.</span><span class="sxs-lookup"><span data-stu-id="40da8-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="40da8-378">Certifique-se de que você também verificou o ponto de extremidade seu *VisionManager* script e ele se alinhe com *sua* região (Este documento usa *Oeste-nos* por padrão).</span><span class="sxs-lookup"><span data-stu-id="40da8-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="40da8-379">Capítulo 9 – compilar a solução de UWP e carregar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="40da8-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="40da8-380">Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído, portanto, é hora de criá-lo do Unity.</span><span class="sxs-lookup"><span data-stu-id="40da8-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="40da8-381">Navegue até *configurações de Build* - **arquivo > configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="40da8-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="40da8-382">Dos *configurações de Build* janela, clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="40da8-382">From the *Build Settings* window, click **Build**.</span></span>

    ![Compilando o aplicativo do Unity](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="40da8-384">Se ainda não estiver, marque **Unity C# projetos**.</span><span class="sxs-lookup"><span data-stu-id="40da8-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="40da8-385">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="40da8-385">Click **Build**.</span></span> <span data-ttu-id="40da8-386">Unity iniciará uma *Explorador de arquivos* janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em.</span><span class="sxs-lookup"><span data-stu-id="40da8-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="40da8-387">Criar pasta agora e nomeie- *aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="40da8-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="40da8-388">Em seguida, com o *App* pasta selecionada, pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="40da8-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="40da8-389">Unity começará a compilar seu projeto para o *aplicativo* pasta.</span><span class="sxs-lookup"><span data-stu-id="40da8-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="40da8-390">Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um *Explorador de arquivos* janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).</span><span class="sxs-lookup"><span data-stu-id="40da8-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="40da8-391">Capítulo 10 – implantar ao HoloLens</span><span class="sxs-lookup"><span data-stu-id="40da8-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="40da8-392">Para implantar o HoloLens:</span><span class="sxs-lookup"><span data-stu-id="40da8-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="40da8-393">Será necessário o endereço IP do seu HoloLens (para a implantação remota) e garantir que seu HoloLens está em **modo de desenvolvedor**.</span><span class="sxs-lookup"><span data-stu-id="40da8-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="40da8-394">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="40da8-394">To do this:</span></span>

    1. <span data-ttu-id="40da8-395">Durante o uso de seu HoloLens, abra o **configurações**.</span><span class="sxs-lookup"><span data-stu-id="40da8-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="40da8-396">Vá para **rede e Internet > Wi-Fi > Opções avançadas**</span><span class="sxs-lookup"><span data-stu-id="40da8-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="40da8-397">Observe a **IPv4** endereço.</span><span class="sxs-lookup"><span data-stu-id="40da8-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="40da8-398">Em seguida, navegue até **as configurações**e, em seguida, para **atualização e segurança > para desenvolvedores**</span><span class="sxs-lookup"><span data-stu-id="40da8-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="40da8-399">Definir o modo de desenvolvedor em.</span><span class="sxs-lookup"><span data-stu-id="40da8-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="40da8-400">Navegue até seu novo build do Unity (o *App* pasta) e abra o arquivo de solução com *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="40da8-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="40da8-401">No, selecione a configuração da solução **depurar**.</span><span class="sxs-lookup"><span data-stu-id="40da8-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="40da8-402">Na plataforma da solução, selecione **x86**, **máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="40da8-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="40da8-404">Vá para o **menu Build** e clique em **implantar solução**, carregar o aplicativo para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="40da8-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="40da8-405">Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="40da8-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="40da8-406">Para implantar o fone de ouvido imersivo, defina as **plataforma da solução** para *Máquina Local*e defina o **configuração** para *depurar*, com *x86* como o **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="40da8-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="40da8-407">Em seguida, implantar no local de máquina, usando o **menu Build**, selecionando *implantar solução*.</span><span class="sxs-lookup"><span data-stu-id="40da8-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="40da8-408">O aplicativo de API de visão do computador concluído</span><span class="sxs-lookup"><span data-stu-id="40da8-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="40da8-409">Parabéns, você criou um aplicativo de realidade mista que aproveita a API de visão do computador do Azure para reconhecer os objetos do mundo real e, em seguida, exibir a confiança de que foi visto.</span><span class="sxs-lookup"><span data-stu-id="40da8-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![resultado de laboratório](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="40da8-411">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="40da8-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="40da8-412">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="40da8-412">Exercise 1</span></span>

<span data-ttu-id="40da8-413">Assim como você usou o *marcas* parâmetro (conforme evidenciado dentro a *ponto de extremidade* usados dentro a *VisionManager*), estenda o aplicativo para detectar outras informações; dar uma olhada quais outros parâmetros que você tem acesso ao [aqui](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="40da8-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="40da8-414">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="40da8-414">Exercise 2</span></span>

<span data-ttu-id="40da8-415">Exiba os dados retornados do Azure, de forma mais conversacional e legível, talvez ocultando os números.</span><span class="sxs-lookup"><span data-stu-id="40da8-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="40da8-416">Como se pode estar falando um bot para o usuário.</span><span class="sxs-lookup"><span data-stu-id="40da8-416">As though a bot might be speaking to the user.</span></span>
