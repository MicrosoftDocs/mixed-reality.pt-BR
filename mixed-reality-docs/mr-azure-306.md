---
title: Sr e Azure 306-vídeo de streaming
description: Conclua este curso para aprender a implementar os serviços de mídia do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, serviços de mídia, vídeo de streaming, 360, imersão, VR
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63555570"
---
>[!NOTE]
><span data-ttu-id="eb5d0-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="eb5d0-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="eb5d0-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="eb5d0-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="eb5d0-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="eb5d0-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="eb5d0-110">Sr e Azure 306: Vídeo de streaming</span><span class="sxs-lookup"><span data-stu-id="eb5d0-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="eb5d0-111">![produto final –](images/AzureLabs-Lab6-00.png)
![início do produto final-início](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="eb5d0-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="eb5d0-112">Neste curso, você aprenderá como conectar seus serviços de mídia do Azure a uma experiência do Windows Mixed Reality VR para permitir a reprodução de vídeo de streaming de 360 graus em headsets de imersão.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="eb5d0-113">Os **serviços de mídia do Azure** são uma coleção de serviços que fornece serviços de streaming de vídeo de qualidade de difusão para alcançar públicos maiores nos dispositivos móveis mais populares de hoje.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="eb5d0-114">Para obter mais informações, visite a [página dos serviços de mídia do Azure](https://azure.microsoft.com/services/media-services).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="eb5d0-115">Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada, que poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="eb5d0-116">Recuperar um vídeo de 360 graus de um **armazenamento do Azure**por meio do **serviço de mídia do Azure**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="eb5d0-117">Exiba o vídeo de 360 graus recuperado em uma cena do Unity.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="eb5d0-118">Navegue entre duas cenas, com dois vídeos diferentes.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="eb5d0-119">Em seu aplicativo, cabe a você como você integrará os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="eb5d0-120">Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="eb5d0-121">É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="eb5d0-122">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="eb5d0-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="eb5d0-123">Course</span><span class="sxs-lookup"><span data-stu-id="eb5d0-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="eb5d0-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="eb5d0-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="eb5d0-125"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="eb5d0-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="eb5d0-126">Sr e Azure 306: Vídeo de streaming</span><span class="sxs-lookup"><span data-stu-id="eb5d0-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="eb5d0-127">✔️</span><span class="sxs-lookup"><span data-stu-id="eb5d0-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="eb5d0-128">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="eb5d0-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="eb5d0-129">Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="eb5d0-130">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="eb5d0-131">Você está livre para usar o software mais recente, conforme listado no [artigo instalar as ferramentas](install-the-tools.md), embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="eb5d0-132">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="eb5d0-133">Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)</span><span class="sxs-lookup"><span data-stu-id="eb5d0-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="eb5d0-134">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="eb5d0-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="eb5d0-135">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="eb5d0-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="eb5d0-136">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="eb5d0-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="eb5d0-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="eb5d0-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="eb5d0-138">Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="eb5d0-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="eb5d0-139">Acesso à Internet para a instalação do Azure e recuperação de dados</span><span class="sxs-lookup"><span data-stu-id="eb5d0-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="eb5d0-140">Vídeos de 2 360 graus no formato MP4 (você pode encontrar alguns vídeos isentos de royalties nesta [página de download](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span><span class="sxs-lookup"><span data-stu-id="eb5d0-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="eb5d0-141">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="eb5d0-141">Before you start</span></span>

1.  <span data-ttu-id="eb5d0-142">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="eb5d0-143">Configure e teste seu headset de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="eb5d0-144">Você **não** precisará de controladores de animação para este curso.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="eb5d0-145">Se você precisar de suporte para configurar o headset de imersão, clique em [link sobre como configurar a realidade mista do Windows](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="eb5d0-146">Capítulo 1-o portal do Azure: criando a conta de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="eb5d0-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="eb5d0-147">Para usar o **serviço de armazenamento do Azure**, você precisará criar e configurar uma **conta de armazenamento** no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="eb5d0-148">Faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="eb5d0-149">Se você ainda não tiver uma conta do Azure, será necessário criar uma.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="eb5d0-150">Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="eb5d0-151">Depois de fazer logon, clique em **contas de armazenamento** no menu à esquerda.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="eb5d0-153">Na guia **contas de armazenamento** , clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="eb5d0-155">Na guia **criar conta de armazenamento** :</span><span class="sxs-lookup"><span data-stu-id="eb5d0-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="eb5d0-156">Insira um **nome** para sua conta, lembre-se de que esse campo aceita apenas números e letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="eb5d0-157">Para **modelo de implantação,** selecione **Gerenciador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="eb5d0-158">Para **tipo de conta**, selecione **armazenamento (uso geral v1)** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="eb5d0-159">Para **desempenho**, selecione **padrão\*.**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="eb5d0-160">Para **replicação** , selecione **armazenamento com REDUNDÂNCIA local (LRS)** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="eb5d0-161">Deixe a **transferência segura necessária** como **desabilitada**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="eb5d0-162">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="eb5d0-163">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="eb5d0-164">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="eb5d0-165">Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="eb5d0-166">O local ideal seria na região em que o aplicativo seria executado.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="eb5d0-167">Alguns ativos do Azure só estão disponíveis em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="eb5d0-168">Você precisará confirmar que entendeu os termos e condições aplicados a este serviço.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="eb5d0-170">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="eb5d0-171">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="eb5d0-173">Neste ponto, você não precisa seguir o recurso, simplesmente vá para o próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="eb5d0-174">Capítulo 2-o portal do Azure: criando o serviço de mídia</span><span class="sxs-lookup"><span data-stu-id="eb5d0-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="eb5d0-175">Para usar o serviço de mídia do Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo (onde o titular da conta precisa ser um administrador).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="eb5d0-176">No portal do Azure, clique em **criar um recurso** no canto superior esquerdo e procure **serviço de mídia,** pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="eb5d0-177">O recurso que você deseja atualmente tem um ícone rosa; Clique aqui para mostrar uma nova página.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="eb5d0-179">A nova página fornecerá uma descrição do **serviço de mídia**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="eb5d0-180">Na parte inferior esquerda desse prompt, clique no botão **criar** para criar uma associação com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="eb5d0-182">Depois de clicar em **criar** um painel, aparecerá onde você precisa fornecer alguns detalhes sobre o novo serviço de mídia:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="eb5d0-183">Insira o **nome da conta** desejada para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="eb5d0-184">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="eb5d0-185">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="eb5d0-186">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="eb5d0-187">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="eb5d0-188">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar grupos de recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="eb5d0-189">Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="eb5d0-190">O local ideal seria na região em que o aplicativo seria executado.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="eb5d0-191">Alguns ativos do Azure só estão disponíveis em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="eb5d0-192">Para a seção **conta de armazenamento** , clique na seção **selecionar...** e clique na conta de **armazenamento** que você criou no último capítulo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="eb5d0-193">Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="eb5d0-194">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-194">Click **Create**.</span></span>

        ![O portal do Azure](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="eb5d0-196">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="eb5d0-197">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="eb5d0-199">Clique na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-199">Click on the notification to explore your new Service instance.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="eb5d0-201">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="eb5d0-202">Na página novo serviço de mídia, no painel à esquerda, clique no link **ativos** , que está sobre a metade para baixo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="eb5d0-203">Na página seguinte, no canto superior esquerdo da página, clique em **carregar**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="eb5d0-205">Clique no ícone de **pasta** para procurar os arquivos e selecione o primeiro vídeo 360 que você deseja transmitir.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="eb5d0-206">Você pode seguir este [link para baixar um vídeo de exemplo](https://vimeo.com/214401712).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="eb5d0-208">Nomes de arquivo longos podem causar um problema com o codificador: para garantir que os vídeos não tenham problemas, considere reduzir o tamanho dos nomes de arquivos de vídeo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="eb5d0-209">A barra de progresso ficará verde quando o vídeo terminar de ser carregado.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="eb5d0-211">Clique no texto acima (**yourservicename-assets**) para retornar à página **ativos** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="eb5d0-212">Você observará que o vídeo foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="eb5d0-213">Clique nele.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-213">Click on it.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="eb5d0-215">A página para a qual você será redirecionado mostrará informações detalhadas sobre o vídeo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="eb5d0-216">Para poder usar seu vídeo, você precisa codificá-lo clicando no botão **codificar** na parte superior esquerda da página.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="eb5d0-218">Um novo painel será exibido à direita, onde você poderá definir as opções de codificação para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="eb5d0-219">Defina as propriedades a seguir (algumas já estarão definidas por padrão):</span><span class="sxs-lookup"><span data-stu-id="eb5d0-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="eb5d0-220">**Nome do codificador de mídia *Media Encoder Standard***</span><span class="sxs-lookup"><span data-stu-id="eb5d0-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="eb5d0-221">**Codificação de *taxa de bits múltipla adaptável com conteúdo* predefinido**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="eb5d0-222">**Nome *do trabalho Media Encoder Standard processamento de Video1. mp4***</span><span class="sxs-lookup"><span data-stu-id="eb5d0-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="eb5d0-223">**Nome do ativo *de mídia de saída Video1. mp4--Media Encoder Standard codificado***</span><span class="sxs-lookup"><span data-stu-id="eb5d0-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![O portal do Azure](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="eb5d0-225">Clique no botão **Criar**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="eb5d0-226">Você notará uma barra com o **trabalho de codificação adicionado**, clicará nessa barra e um painel será exibido com o andamento da codificação exibido nela.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-17.png)

    ![O portal do Azure](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="eb5d0-229">Aguarde a conclusão do trabalho.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="eb5d0-230">Quando terminar, fique à vontade para fechar o painel com o ' X ' na parte superior direita desse painel.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-19.png)

    ![O portal do Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="eb5d0-233">O tempo que isso leva, depende do tamanho do arquivo do seu vídeo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="eb5d0-234">Esse processo pode levar muito tempo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="eb5d0-235">Agora que a versão codificada do vídeo foi criada, você pode publicá-la para torná-la acessível.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="eb5d0-236">Para fazer isso, clique nos **ativos** do link azul para voltar para a página ativos.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="eb5d0-238">Você verá seu vídeo, juntamente com outra, o que é do \*\*tipo de ativo \*múltiplas taxas de bits MP4\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-238">You will see your video along with another, which is of \*\*Asset Type \*Multi-Bitrate MP4\*\*\*.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="eb5d0-240">Você pode notar que o novo ativo, junto com o vídeo inicial, é *desconhecido*e tem ' 0 ' bytes para seu **tamanho**, basta atualizar sua janela para que ele seja atualizado.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="eb5d0-241">Clique nesse novo ativo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-241">Click this new asset.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="eb5d0-243">Você verá um painel semelhante ao que você usou antes, apenas esse é um ativo diferente.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="eb5d0-244">Clique no botão **publicar** localizado na parte superior central da página.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="eb5d0-246">Você será solicitado a definir um localizador , que é o ponto de entrada, para arquivos/s em seus ativos.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="eb5d0-247">Para seu cenário, defina as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="eb5d0-248">Tipo > de localizador**progressivo**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="eb5d0-249">A **Data** e a **hora** serão definidas para você, da data atual, para uma hora no futuro (100 anos, nesse caso).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="eb5d0-250">Deixe como está ou altere-o para o naipe.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="eb5d0-251">Para obter mais informações sobre localizadores e o que você pode escolher, visite a [documentação dos serviços de mídia do Azure](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="eb5d0-252">Na parte inferior do painel, clique no botão **Adicionar** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="eb5d0-254">Seu vídeo agora está publicado e pode ser transmitido usando seu ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="eb5d0-255">Além disso, a página é uma seção de **arquivos** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="eb5d0-256">É aí que as diferentes versões codificadas do seu vídeo serão.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="eb5d0-257">Selecione a resolução mais alta possível (na imagem abaixo dele é o arquivo 1920x960) e, em seguida, um painel à direita será exibido.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="eb5d0-258">Lá, você encontrará uma **URL de download**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="eb5d0-259">Copie esse **ponto de extremidade** , pois você o usará posteriormente em seu código.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-26.png)    

    ![O portal do Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="eb5d0-262">Você também pode pressionar o botão **reproduzir** para reproduzir seu vídeo e testá-lo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="eb5d0-263">Agora você precisa carregar o segundo vídeo que será usado neste laboratório.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="eb5d0-264">Siga as etapas acima, repetindo o mesmo processo para o segundo vídeo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="eb5d0-265">Certifique-se de copiar o segundo **ponto de extremidade** também.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="eb5d0-266">Use o link a seguir [para baixar um segundo vídeo](https://vimeo.com/214402865).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="eb5d0-267">Depois que os dois vídeos tiverem sido publicados, você estará pronto para ir para o próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="eb5d0-268">Capítulo 3-Configurando o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="eb5d0-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="eb5d0-269">A seguir está uma configuração típica para o desenvolvimento com a realidade misturada e, como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="eb5d0-270">Abra o **Unity** e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-270">Open **Unity** and click **New**.</span></span> 

    ![O portal do Azure](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="eb5d0-272">Agora, você precisará fornecer um nome de projeto de Unity, inserir **\_Mr 360VideoStreaming.** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="eb5d0-273">Verifique se o tipo de projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="eb5d0-274">Defina o local como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="eb5d0-275">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-275">Then, click **Create project**.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="eb5d0-277">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="eb5d0-278">Vá para ***Editar* *preferências*** e, em seguida, na janela novo, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="eb5d0-279">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="eb5d0-280">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-280">Close the **Preferences** window.</span></span>

    ![O portal do Azure](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="eb5d0-282">Em seguida, vá para ***arquivo* *configurações de compilação*** e alterne a plataforma para **plataforma universal do Windows**, clicando no botão **alternar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="eb5d0-283">Verifique também se:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-283">Also make sure that:</span></span>

    1. <span data-ttu-id="eb5d0-284">O **dispositivo de destino** está definido como **qualquer dispositivo.**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="eb5d0-285">O **tipo de compilação** está definido como **D3D.**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="eb5d0-286">O **SDK** está definido para o **mais recente instalado.**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="eb5d0-287">A **versão do Visual Studio** está definida como **mais recente instalada.**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="eb5d0-288">**Compilar e executar** é definido como **computador local.**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="eb5d0-289">Não se preocupe com a configuração de **cenas** no momento, pois você as configurará posteriormente.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="eb5d0-290">As configurações restantes devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-290">The remaining settings should be left as default for now.</span></span>

        ![Configurando o projeto do Unity](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="eb5d0-292">Na janela **configurações de compilação** , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o **Inspetor** está localizado.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="eb5d0-293">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="eb5d0-294">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="eb5d0-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="eb5d0-295">**Criando scripts** A **versão de tempo de execução** deve ser **estável** (.net 3,5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="eb5d0-296">O **back-end de script** deve ser **.net.**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="eb5d0-297">O **nível de compatibilidade da API** deve ser **.NET 4,6.**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Configurando o projeto do Unity](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="eb5d0-299">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o SDK do **Windows Mixed Reality** foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurando o projeto do Unity](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="eb5d0-301">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="eb5d0-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-302">**InternetClient**</span></span>

            ![Configurando o projeto do Unity](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="eb5d0-304">Depois de fazer essas alterações, feche a janela **configurações de compilação** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="eb5d0-305">Salve seu projeto \**arquivo* \*Salvar projeto\*\*.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="eb5d0-306">Capítulo 4-importando o pacote do InsideOutSphere Unity</span><span class="sxs-lookup"><span data-stu-id="eb5d0-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb5d0-307">Se você quiser ignorar o componente *de configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para baixar esse [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), importe-o para seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue no **capítulo 5**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="eb5d0-308">Você ainda precisará criar um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="eb5d0-309">Para este curso, você precisará baixar um pacote de ativos de Unity chamado [**InsideOutSphere. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="eb5d0-310">Como importar o **unitypackage**:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="eb5d0-311">Com o painel do Unity na frente, clique em **ativos** no menu na parte superior da tela e, em seguida, clique em **Importar pacote > pacote personalizado**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="eb5d0-313">Use o seletor de arquivos para selecionar o pacote **InsideOutSphere. unitypackage** e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="eb5d0-314">Uma lista de componentes para este ativo será exibida para você.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="eb5d0-315">Confirme a importação clicando em **importar**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-315">Confirm the import by clicking **Import**.</span></span>

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="eb5d0-317">Depois de concluir a importação, você notará três novas pastas, **materiais**, **modelos**e **pré-fabricados**, foram adicionados à sua pasta de **ativos** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="eb5d0-318">Esse tipo de estrutura de pastas é típico para um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="eb5d0-320">Abra a pasta **modelos** e você verá que o modelo **InsideOutSphere** foi importado.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="eb5d0-321">Na pasta **materiais** , você encontrará o material de **InsideOutSpheres** *LAMBERT1*, junto com um material chamado *ButtonMaterial*, que é usado pelo GazeButton, que será exibido em breve.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="eb5d0-322">A pasta **pré-fabricados** contém o **InsideOutSphere** pré-fabricado que contém o modelo **InsideOutSphere**  e o *GazeButton*.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="eb5d0-323">**Nenhum código está incluído**, você escreverá o código seguindo este curso.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="eb5d0-324">Na **hierarquia**, selecione o objeto de **câmera principal** e atualize os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="eb5d0-325">**Tenha**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-325">**Transform**</span></span>

        1.  <span data-ttu-id="eb5d0-326">Posição = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="eb5d0-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="eb5d0-328">Escala **X**: 1, **Y**: 1, **Z**: 1.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="eb5d0-329">**Câmera**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-329">**Camera**</span></span>

        1. <span data-ttu-id="eb5d0-330">**Limpar sinalizadores**: Cor sólida.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="eb5d0-331">**Planos**de recorte: Meu 0,1, longe: 6.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="eb5d0-333">Navegue até a pasta **pré-fabricado** e, em seguida, arraste o **InsideOutSphere** pré-fabricado para o painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="eb5d0-335">Expanda o objeto **InsideOutSphere** dentro da **hierarquia** clicando na pequena seta ao lado dele.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="eb5d0-336">Você verá um objeto **filho** abaixo dele chamado **GazeButton**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="eb5d0-337">Isso será usado para alterar cenas e vídeos assim.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-337">This will be used to change scenes and thus videos.</span></span>

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="eb5d0-339">Na janela do Inspetor, clique no componente de transformação do **InsideOutSphere**, verifique se as seguintes propriedades estão definidas:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="eb5d0-340">TRANSFORMAÇÃO-POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="eb5d0-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="eb5d0-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-341">**X** 0</span></span>  |          <span data-ttu-id="eb5d0-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-342">**Y** 0</span></span>          |  <span data-ttu-id="eb5d0-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="eb5d0-344">TRANSFORMAÇÃO-ROTAÇÃO</span><span class="sxs-lookup"><span data-stu-id="eb5d0-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="eb5d0-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-345">**X** 0</span></span>  |          <span data-ttu-id="eb5d0-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="eb5d0-346">**Y** -50</span></span>        |  <span data-ttu-id="eb5d0-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="eb5d0-348">TRANSFORMAR EM ESCALA</span><span class="sxs-lookup"><span data-stu-id="eb5d0-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="eb5d0-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="eb5d0-349">**X** 1</span></span>   |          <span data-ttu-id="eb5d0-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="eb5d0-350">**Y** 1</span></span>          |  <span data-ttu-id="eb5d0-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="eb5d0-351">**Z** 1</span></span>  |

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="eb5d0-353">Clique no objeto filho **GazeButton** e defina sua **transformação** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="eb5d0-354">TRANSFORMAÇÃO-POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="eb5d0-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="eb5d0-355">**X** 3,6</span><span class="sxs-lookup"><span data-stu-id="eb5d0-355">**X** 3.6</span></span>|          <span data-ttu-id="eb5d0-356">**Y** 1,3</span><span class="sxs-lookup"><span data-stu-id="eb5d0-356">**Y** 1.3</span></span>        |  <span data-ttu-id="eb5d0-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="eb5d0-358">TRANSFORMAÇÃO-ROTAÇÃO</span><span class="sxs-lookup"><span data-stu-id="eb5d0-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="eb5d0-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-359">**X** 0</span></span>  |          <span data-ttu-id="eb5d0-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-360">**Y** 0</span></span>          |  <span data-ttu-id="eb5d0-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="eb5d0-362">TRANSFORMAR EM ESCALA</span><span class="sxs-lookup"><span data-stu-id="eb5d0-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="eb5d0-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="eb5d0-363">**X** 1</span></span>   |          <span data-ttu-id="eb5d0-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="eb5d0-364">**Y** 1</span></span>          |  <span data-ttu-id="eb5d0-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="eb5d0-365">**Z** 1</span></span>  |

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="eb5d0-367">Capítulo 5 – criar a classe VideoController</span><span class="sxs-lookup"><span data-stu-id="eb5d0-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="eb5d0-368">A classe **VideoController** hospeda os dois pontos de extremidade de vídeo que serão usados para transmitir o conteúdo do serviço de mídia do Azure.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="eb5d0-369">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-369">To create this class:</span></span>

1.  <span data-ttu-id="eb5d0-370">Clique com o botão direito do mouse na **pasta ativo**, localizada no painel **projeto** , e clique em **criar > pasta**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="eb5d0-371">Nomeie a pasta **scripts**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-371">Name the folder **Scripts**.</span></span>

    ![Criar a classe VideoController](images/AzureLabs-Lab6-43.png)

    ![Criar a classe VideoController](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="eb5d0-374">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="eb5d0-375">Clique com o botão direito do mouse dentro da pasta e clique em **criar > script C\#** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="eb5d0-376">Nomeie o script **VideoController**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-376">Name the script **VideoController**.</span></span>

    ![Criar a classe VideoController](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="eb5d0-378">Clique duas vezes no novo script **VideoController** para abri-lo com o **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![Criar a classe VideoController](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="eb5d0-380">Atualize os namespaces na parte superior do arquivo de código da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="eb5d0-381">Insira as variáveis a seguir na classe **VideoController** , juntamente com o método **ativo ()** :</span><span class="sxs-lookup"><span data-stu-id="eb5d0-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  <span data-ttu-id="eb5d0-382">Agora é o momento de inserir os pontos de extremidade dos vídeos do serviço de mídia do Azure:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="eb5d0-383">O primeiro na variável *video1endpoint* .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="eb5d0-384">O segundo na variável *video2endpoint* .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="eb5d0-385">Há um problema conhecido com o uso de *https* no Unity, com a versão 2017.4.1 F1.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="eb5d0-386">Se os vídeos fornecerem um erro na reprodução, tente usar "http" em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="eb5d0-387">Em seguida, o método **Start ()** precisa ser editado.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="eb5d0-388">Esse método será disparado sempre que o usuário alternar a cena (consequentemente, alternando o vídeo) examinando o botão olhar.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="eb5d0-389">Após o método **Start ()** , insira o método **PlayVideo ()** *IEnumerator* , que será usado para iniciar vídeos diretamente (portanto, nenhum stutter é visto).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. <span data-ttu-id="eb5d0-390">O último método necessário para essa classe é o método **ChangeScene ()** , que será usado para alternar entre cenas.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="eb5d0-391">O método **ChangeScene ()** usa um recurso C\# útil chamado *operador condicional*.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="eb5d0-392">Isso permite que as condições sejam verificadas e, em seguida, os valores retornados com base no resultado da verificação, tudo dentro de uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="eb5d0-393">Siga este [link para saber mais sobre o operador condicional](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="eb5d0-394">Salve suas alterações no Visual Studio antes de retornar ao Unity.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="eb5d0-395">De volta ao editor do Unity, clique e arraste a classe **VideoController** [de] {. Underline} a pasta **scripts** para o objeto da **câmera principal** no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="eb5d0-396">Clique na **câmera principal** e examine o **painel Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="eb5d0-397">Você observará que, dentro do componente de script recém-adicionado, há um campo com um valor vazio.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="eb5d0-398">Este é um campo de referência, que tem como alvo as variáveis públicas no seu código.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="eb5d0-399">Arraste o objeto **InsideOutSphere** do **painel hierarquia** para o slot de **esfera** , conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="eb5d0-400">![Criar a classe](images/AzureLabs-Lab6-47.png)
    ![VideoController criar a classe VideoController](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="eb5d0-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="eb5d0-401">Capítulo 6-criar a classe olhar</span><span class="sxs-lookup"><span data-stu-id="eb5d0-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="eb5d0-402">Essa classe é responsável por criar um **Raycast** que será projetado para a frente da **câmera principal**, para detectar qual objeto o usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-402">This class is responsible for creating a **Raycast** that will beprojected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="eb5d0-403">Nesse caso, o **Raycast** precisará identificar se o usuário está olhando para o objeto **GazeButton** na cena e disparar um comportamento.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="eb5d0-404">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-404">To create this Class:</span></span>

1.  <span data-ttu-id="eb5d0-405">Vá para a pasta **scripts** que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="eb5d0-406">Clique com botão direito no **Project** painel, \**crie* \*C\# Script\*\*.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="eb5d0-407">Nomeie o script **olhar**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="eb5d0-408">Clique duas vezes no novo script ***olhar*** para abri-lo com o **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="eb5d0-409">Verifique se o namespace a seguir está na parte superior do script e remova todos os outros:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="eb5d0-410">Em seguida, adicione as seguintes variáveis dentro da classe **olhar** :</span><span class="sxs-lookup"><span data-stu-id="eb5d0-410">Then add the following variables inside the **Gaze** class:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  <span data-ttu-id="eb5d0-411">Agora, o código para os métodos **ativo ()** e **Iniciar ()** precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  <span data-ttu-id="eb5d0-412">Adicione o código a seguir no método **Update ()** para projetar um Raycast e detectar o destino atingido:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  <span data-ttu-id="eb5d0-413">Salve suas alterações no Visual Studio antes de retornar ao Unity.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="eb5d0-414">Clique e arraste a classe **olhar** da pasta scripts para o objeto de câmera principal no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="eb5d0-415">Capítulo 7-configurar as duas cenas de Unity</span><span class="sxs-lookup"><span data-stu-id="eb5d0-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="eb5d0-416">A finalidade deste capítulo é configurar as duas cenas, cada uma hospedando um vídeo para transmitir.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="eb5d0-417">Você duplicará a cena que já criou, para que não seja necessário configurá-la novamente, embora você editará a nova cena, para que o objeto *GazeButton* esteja em um local diferente e tenha uma aparência diferente.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="eb5d0-418">Isso é para mostrar como alterar entre cenas.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="eb5d0-419">Faça isso indo para **arquivo > salvar cena como...** . Uma janela salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="eb5d0-420">Clique no botão **nova pasta** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-420">Click the **New folder** button.</span></span>

    ![Capítulo 7-configurar as duas cenas de Unity](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="eb5d0-422">Nomeie a pasta como **cenas**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="eb5d0-423">A janela **salvar cena** ainda estará aberta.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="eb5d0-424">Abra sua pasta de **cenas** recém-criada.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="eb5d0-425">No campo **nome do arquivo:** texto, digite **VideoScene1**e pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="eb5d0-426">De volta ao Unity, abra a pasta **cenas** e clique com o botão esquerdo do mouse no arquivo **VideoScene1** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="eb5d0-427">Use o teclado e pressione **Ctrl + D** para duplicar essa cena</span><span class="sxs-lookup"><span data-stu-id="eb5d0-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="eb5d0-428">O  comando duplicado também pode ser executado navegando para **Editar > duplicado**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="eb5d0-429">O Unity incrementará automaticamente o número de nomes de cena, mas o verificará de qualquer forma, para garantir que ele corresponda ao código inserido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="eb5d0-430">Você deve ter **VideoScene1** e **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="eb5d0-431">Com seus dois bastidores, vá para **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="eb5d0-432">Com a janela **configurações de compilação** aberta, arraste suas cenas para a seção **cenas na compilação** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="eb5d0-434">Você pode selecionar os dois bastidores da sua pasta de **cenas** pressionando o botão **Ctrl** e, em seguida, clicando em cada uma das cenas e, por fim, arrastando ambos.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="eb5d0-435">Feche a janela **configurações de Build** e clique duas vezes em **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="eb5d0-436">Com a segunda cena aberta, clique no objeto filho **GazeButton** do **InsideOutSphere**e defina sua transformação da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="eb5d0-437">TRANSFORMAÇÃO-POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="eb5d0-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="eb5d0-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-438">**X** 0</span></span>  |         <span data-ttu-id="eb5d0-439">**Y** 1,3</span><span class="sxs-lookup"><span data-stu-id="eb5d0-439">**Y** 1.3</span></span>         | <span data-ttu-id="eb5d0-440">**Z** 3,6</span><span class="sxs-lookup"><span data-stu-id="eb5d0-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="eb5d0-441">TRANSFORMAÇÃO-ROTAÇÃO</span><span class="sxs-lookup"><span data-stu-id="eb5d0-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="eb5d0-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-442">**X** 0</span></span>  |          <span data-ttu-id="eb5d0-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-443">**Y** 0</span></span>          |  <span data-ttu-id="eb5d0-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="eb5d0-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="eb5d0-445">TRANSFORMAR EM ESCALA</span><span class="sxs-lookup"><span data-stu-id="eb5d0-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="eb5d0-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="eb5d0-446">**X** 1</span></span>   |          <span data-ttu-id="eb5d0-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="eb5d0-447">**Y** 1</span></span>          |  <span data-ttu-id="eb5d0-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="eb5d0-448">**Z** 1</span></span>  |

10. <span data-ttu-id="eb5d0-449">Com o filho **GazeButton** ainda selecionado, examine o **Inspetor** e o filtro de **malha**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="eb5d0-450">Clique no pequeno destino ao lado do campo de referência de **malha** :</span><span class="sxs-lookup"><span data-stu-id="eb5d0-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="eb5d0-452">Uma janela pop-up **selecionar malha** será exibida.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="eb5d0-453">Clique duas vezes na malha do **cubo** na lista de **ativos**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="eb5d0-455">O **filtro de malha** será atualizado e agora será um **cubo**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="eb5d0-456">Agora, clique no ícone de **engrenagem** ao lado de **Colisor de esfera** e clique em **remover componente**para excluir o colisor desse objeto.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="eb5d0-458">Com o **GazeButton** ainda selecionado, clique no botão **Adicionar componente** na parte inferior do **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="eb5d0-459">No campo de pesquisa, digite **Box**e o **colisor do box** será uma opção – clique nele para adicionar um **Colisor de caixa** ao seu objeto **GazeButton** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="eb5d0-461">O **GazeButton** agora é parcialmente atualizado, para parecer diferente, no entanto, agora você criará um novo **material**, para que ele pareça completamente diferente e seja mais fácil de reconhecer como um objeto diferente do objeto na primeira cena.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="eb5d0-462">Navegue até a pasta **materiais** , no **painel Projeto**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="eb5d0-463">Duplique o material **ButtonMaterial** (pressione **Ctrl** + **D** no teclado ou clique com o botão esquerdo do mouse no **material**e, em seguida, na opção de menu **Editar** arquivo, selecione **duplicar**).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="eb5d0-464">![Capítulo 7 – configurar os dois bastidores](images/AzureLabs-Lab6-55.png)
    ![do Unity capítulo 7 – configurar as duas cenas do Unity](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="eb5d0-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="eb5d0-465">Selecione o novo material de **ButtonMaterial** (aqui chamado **ButtonMaterial 1**) e, dentro do **Inspetor**, clique na janela de cores **albedo** .</span><span class="sxs-lookup"><span data-stu-id="eb5d0-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="eb5d0-466">Um pop-up será exibido, no qual você pode selecionar outra cor (escolha o que desejar) e, em seguida, feche o pop-up.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="eb5d0-467">O material será sua própria instância e diferente do original.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-467">The Material will be its own instance, and different to the original.</span></span>

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="eb5d0-469">Arraste o novo **material** para o filho do **GazeButton** , para agora atualizar completamente sua aparência, de modo que seja facilmente distinguivel do primeiro botão de cenas.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="eb5d0-471">Neste ponto, você pode testar o projeto no editor antes de criar o projeto UWP.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="eb5d0-472">Pressione o botão **reproduzir** no **Editor** e desgaste do headset.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="eb5d0-474">Examine os dois objetos **GazeButton** para alternar entre o primeiro e o segundo vídeo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="eb5d0-475">Capítulo 8-compilar a solução UWP</span><span class="sxs-lookup"><span data-stu-id="eb5d0-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="eb5d0-476">Depois de garantir que o editor não tem erros, você estará pronto para compilar.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="eb5d0-477">Para compilar:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-477">To Build:</span></span>

1.  <span data-ttu-id="eb5d0-478">Salve a cena atual clicando em **arquivo > salvar**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="eb5d0-479">Marque a caixa chamado **projetos do\# Unity C** (isso é importante porque ele permitirá que você edite as classes após a conclusão da compilação).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="eb5d0-480">Vá para **arquivo > configurações de compilação**, clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="eb5d0-481">Você será solicitado a selecionar a pasta onde deseja buildThe a solução.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-481">You will be prompted to select the folder where you want to buildthe Solution.</span></span>

5.  <span data-ttu-id="eb5d0-482">Crie uma  pasta builds e dentro dessa pasta crie outra pasta com um nome apropriado de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="eb5d0-483">Clique na nova pasta e, em seguida, clique em **Selecionar pasta**, para escolher essa pasta, para iniciar a compilação nesse local.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="eb5d0-484">![Capítulo 8--criar a solução](images/AzureLabs-Lab6-60.png)
    ![UWP capítulo 8--criar a solução UWP](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="eb5d0-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="eb5d0-485">Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="eb5d0-486">Capítulo 9 – implantar no computador local</span><span class="sxs-lookup"><span data-stu-id="eb5d0-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="eb5d0-487">Depois que a compilação for concluída, uma janela **Explorador de arquivos** será exibida no local da sua compilação.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="eb5d0-488">Abra a pasta que você nomeou e criou e clique duas vezes no arquivo da solução (. sln) dentro dessa pasta para abrir sua solução com o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="eb5d0-489">A única coisa que resta fazer é implantar seu aplicativo em seu computador (ou *computador local*).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="eb5d0-490">Para implantar no computador local:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="eb5d0-491">No **Visual Studio 2017**, abra o arquivo de solução que acabou de ser criado.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="eb5d0-492">Na **plataforma da solução**, selecione **x86, computador local**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="eb5d0-493">Na **configuração da solução** , selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![Capítulo 9 – implantar no computador local](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="eb5d0-495">Agora, você precisará restaurar todos os pacotes para sua solução.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="eb5d0-496">Clique com o botão direito do mouse em sua **solução**e clique em **restaurar pacotes NuGet para solução...**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="eb5d0-497">Isso é feito porque os pacotes que o Unity criou precisam ser destinados para trabalhar com suas referências de computadores locais.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="eb5d0-498">Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="eb5d0-499">O Visual Studio primeiro compilará e, em seguida, implantará seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="eb5d0-500">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![Capítulo 9 – implantar no computador local](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="eb5d0-502">Ao executar o aplicativo de realidade misturada, você estará dentro do modelo de **InsideOutSphere** que você usou em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="eb5d0-503">Essa esfera será onde o vídeo será transmitido, fornecendo uma exibição de 360 graus do vídeo de entrada (que foi cofilme para esse tipo de perspectiva).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="eb5d0-504">Não se surpreenda se o vídeo levar alguns segundos para ser carregado, seu aplicativo estará sujeito à velocidade da Internet disponível, uma vez que o vídeo precisa ser buscado e então baixado, portanto, para transmitir em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="eb5d0-505">Quando estiver pronto, altere as cenas e abra o segundo vídeo, por nuvens na esfera vermelha!</span><span class="sxs-lookup"><span data-stu-id="eb5d0-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="eb5d0-506">Em seguida, fique à vontade para voltar, usando o cubo azul na segunda cena!</span><span class="sxs-lookup"><span data-stu-id="eb5d0-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="eb5d0-507">Seu aplicativo de serviço de mídia do Azure concluído</span><span class="sxs-lookup"><span data-stu-id="eb5d0-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="eb5d0-508">Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço de mídia do Azure para transmitir vídeos 360.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![resultado do laboratório](images/AzureLabs-Lab6-00.png)

![resultado do laboratório](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="eb5d0-511">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="eb5d0-511">Bonus Exercises</span></span>

<span data-ttu-id="eb5d0-512">**Exercício 1**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-512">**Exercise 1**</span></span>

<span data-ttu-id="eb5d0-513">É totalmente possível usar apenas uma única cena para alterar vídeos dentro deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="eb5d0-514">Experimente seu aplicativo e torne-o em uma única cena!</span><span class="sxs-lookup"><span data-stu-id="eb5d0-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="eb5d0-515">Talvez até mesmo Adicione outro vídeo à combinação.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="eb5d0-516">**Exercício 2**</span><span class="sxs-lookup"><span data-stu-id="eb5d0-516">**Exercise 2**</span></span>

<span data-ttu-id="eb5d0-517">Experimente com o Azure e o Unity e tente implementar a capacidade para o aplicativo selecionar automaticamente um vídeo com um tamanho de arquivo diferente, dependendo da força de uma conexão com a Internet.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


