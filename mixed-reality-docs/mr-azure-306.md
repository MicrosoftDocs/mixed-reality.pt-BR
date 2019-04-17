---
title: MR e Azure 306 - Streaming de vídeo
description: Conclua este curso para aprender a implementar os serviços de mídia do Azure dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, serviços de mídia, streaming de vídeo, 360, imersivo, vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589469"
---
>[!NOTE]
><span data-ttu-id="52b62-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="52b62-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="52b62-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="52b62-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="52b62-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="52b62-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="52b62-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="52b62-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="52b62-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="52b62-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="52b62-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="52b62-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="52b62-110">MR e o Azure 306: Streaming de vídeo</span><span class="sxs-lookup"><span data-stu-id="52b62-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="52b62-111">![final do produto-inicie](images/AzureLabs-Lab6-00.png)
![final do produto-iniciar](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="52b62-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="52b62-112">Este curso, você aprenderá como conectar os serviços de mídia do Azure para uma experiência VR de realidade mista do Windows para permitir a reprodução de vídeo de 360 graus em fones imersivos em exposição de streaming.</span><span class="sxs-lookup"><span data-stu-id="52b62-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="52b62-113">**Os serviços de mídia do Azure** são uma coleção de serviços que fornece serviços de streaming vídeo com qualidade de difusão para alcançar públicos maiores nos dispositivos móveis mais populares de hoje.</span><span class="sxs-lookup"><span data-stu-id="52b62-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="52b62-114">Para obter mais informações, visite o [página de serviços de mídia do Azure](https://azure.microsoft.com/services/media-services).</span><span class="sxs-lookup"><span data-stu-id="52b62-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="52b62-115">Com a conclusão deste curso, terá um aplicativo de imersão headset de realidade misturada, que será capaz de fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="52b62-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="52b62-116">Recuperar um vídeo de 360 graus de um **armazenamento do Azure**, por meio de **serviço de mídia do Azure**.</span><span class="sxs-lookup"><span data-stu-id="52b62-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="52b62-117">Exiba o vídeo de 360 graus recuperada dentro de uma cena do Unity.</span><span class="sxs-lookup"><span data-stu-id="52b62-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="52b62-118">Navega entre duas cenas, com dois vídeos diferentes.</span><span class="sxs-lookup"><span data-stu-id="52b62-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="52b62-119">Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="52b62-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="52b62-120">Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="52b62-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="52b62-121">Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="52b62-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="52b62-122">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="52b62-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="52b62-123">Curso</span><span class="sxs-lookup"><span data-stu-id="52b62-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="52b62-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="52b62-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="52b62-125"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="52b62-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="52b62-126">MR e o Azure 306: Streaming de vídeo</span><span class="sxs-lookup"><span data-stu-id="52b62-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="52b62-127">✔️</span><span class="sxs-lookup"><span data-stu-id="52b62-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="52b62-128">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="52b62-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="52b62-129">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="52b62-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="52b62-130">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="52b62-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="52b62-131">Você é livre para usar o software mais recente, conforme listado dentro de [instalar o artigo de ferramentas](install-the-tools.md), embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .</span><span class="sxs-lookup"><span data-stu-id="52b62-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="52b62-132">Recomendamos que o hardware e software para este curso a seguir:</span><span class="sxs-lookup"><span data-stu-id="52b62-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="52b62-133">Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)</span><span class="sxs-lookup"><span data-stu-id="52b62-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="52b62-134">Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="52b62-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="52b62-135">O SDK mais recente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="52b62-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="52b62-136">2017.4 do Unity</span><span class="sxs-lookup"><span data-stu-id="52b62-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="52b62-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="52b62-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="52b62-138">Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="52b62-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="52b62-139">Acesso à Internet para recuperação de dados e de instalação do Azure</span><span class="sxs-lookup"><span data-stu-id="52b62-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="52b62-140">Dois vídeos de 360 graus em formato mp4 (você pode encontrar alguns vídeos livre de royalties [a esta página de download](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span><span class="sxs-lookup"><span data-stu-id="52b62-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="52b62-141">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="52b62-141">Before you start</span></span>

1.  <span data-ttu-id="52b62-142">Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="52b62-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="52b62-143">Configurar e testar o fone imersivo realidade mista.</span><span class="sxs-lookup"><span data-stu-id="52b62-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="52b62-144">Você irá **não** exigem controladores de movimento para este curso.</span><span class="sxs-lookup"><span data-stu-id="52b62-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="52b62-145">Se você precisar dar suporte a configurar o fone de ouvido imersivo, clique em [link sobre como configurar o Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="52b62-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="52b62-146">Capítulo 1 - Portal do Azure: criar a conta de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="52b62-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="52b62-147">Para usar o **serviço de armazenamento do Azure**, você precisará criar e configurar um **conta de armazenamento** no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="52b62-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="52b62-148">Faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="52b62-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="52b62-149">Se você ainda não tiver uma conta do Azure, você precisará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="52b62-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="52b62-150">Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="52b62-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="52b62-151">Quando você estiver conectado, clique em **contas de armazenamento** no menu à esquerda.</span><span class="sxs-lookup"><span data-stu-id="52b62-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="52b62-153">Sobre o **contas de armazenamento** guia, clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="52b62-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="52b62-155">No **criar conta de armazenamento** guia:</span><span class="sxs-lookup"><span data-stu-id="52b62-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="52b62-156">Inserir uma **nome** para sua conta, lembre-se que este campo aceita apenas números e letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="52b62-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="52b62-157">Para **modelo de implantação** selecionar **Gerenciador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="52b62-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="52b62-158">Para **tipo de conta**, selecione **(uso geral v1) de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="52b62-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="52b62-159">Para **desempenho**, selecione \**padrão *.**</span><span class="sxs-lookup"><span data-stu-id="52b62-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="52b62-160">Para **replicação** selecionar **armazenamento localmente redundante (LRS)**.</span><span class="sxs-lookup"><span data-stu-id="52b62-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="52b62-161">Deixe **transferência segura obrigatória** como **desabilitado**.</span><span class="sxs-lookup"><span data-stu-id="52b62-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="52b62-162">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="52b62-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="52b62-163">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="52b62-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="52b62-164">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="52b62-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="52b62-165">Determinar a **local** para seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="52b62-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="52b62-166">O local seria o ideal é que na região em que o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="52b62-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="52b62-167">Alguns ativos do Azure estão disponíveis somente em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="52b62-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="52b62-168">Você precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="52b62-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="52b62-170">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="52b62-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="52b62-171">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="52b62-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="52b62-173">Neste momento você não precisa seguir o recurso, basta mover para o próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="52b62-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="52b62-174">Capítulo 2 - Portal do Azure: criar o serviço de mídia</span><span class="sxs-lookup"><span data-stu-id="52b62-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="52b62-175">Para usar o serviço de mídia do Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo (no qual o titular da conta precisa ser um administrador).</span><span class="sxs-lookup"><span data-stu-id="52b62-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="52b62-176">No Portal do Azure, clique em **criar um recurso** no canto superior esquerdo de canto e procure **serviço de mídia** pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="52b62-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="52b62-177">O recurso desejado no momento, tem um ícone rosa; Clique aqui para mostrar uma nova página.</span><span class="sxs-lookup"><span data-stu-id="52b62-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="52b62-179">A nova página fornecerá uma descrição do **serviço de mídia**.</span><span class="sxs-lookup"><span data-stu-id="52b62-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="52b62-180">Na parte inferior esquerda desse prompt, clique no **criar** botão para criar uma associação com este serviço.</span><span class="sxs-lookup"><span data-stu-id="52b62-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="52b62-182">Depois de clicar em **criar** um painel será exibido em que você precisa fornecer alguns detalhes sobre seu novo serviço de mídia:</span><span class="sxs-lookup"><span data-stu-id="52b62-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="52b62-183">Inserir sua desejada **nome da conta** para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="52b62-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="52b62-184">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="52b62-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="52b62-185">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="52b62-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="52b62-186">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="52b62-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="52b62-187">É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="52b62-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="52b62-188">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar grupos de recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="52b62-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="52b62-189">Determinar a **local** para seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="52b62-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="52b62-190">O local seria o ideal é que na região em que o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="52b62-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="52b62-191">Alguns ativos do Azure estão disponíveis somente em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="52b62-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="52b62-192">Para o **conta de armazenamento** seção, clique no **selecione...**  seção e, em seguida, clique em de **conta de armazenamento** você criou no último capítulo.</span><span class="sxs-lookup"><span data-stu-id="52b62-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="52b62-193">Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="52b62-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="52b62-194">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="52b62-194">Click **Create**.</span></span>

        ![O Portal do Azure](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="52b62-196">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="52b62-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="52b62-197">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="52b62-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="52b62-199">Clique na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="52b62-199">Click on the notification to explore your new Service instance.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="52b62-201">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="52b62-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="52b62-202">Dentro da página de serviço de mídia novo, no painel à esquerda, clique no **ativos** link, que é sobre na metade inferior.</span><span class="sxs-lookup"><span data-stu-id="52b62-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="52b62-203">Na próxima página, no canto superior esquerdo da página, clique em **carregar**.</span><span class="sxs-lookup"><span data-stu-id="52b62-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="52b62-205">Clique no **pasta** ícone Procurar seus arquivos e selecione o vídeo de 360 pela primeira vez que você deseja transmitir.</span><span class="sxs-lookup"><span data-stu-id="52b62-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="52b62-206">Você pode seguir este [link para baixar um vídeo de exemplo](https://vimeo.com/214401712).</span><span class="sxs-lookup"><span data-stu-id="52b62-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="52b62-208">Nomes de arquivo longos podem causar um problema com o codificador: por isso, para garantir que os vídeos não terá problemas, considere encurtar o comprimento de seus nomes de arquivo de vídeo.</span><span class="sxs-lookup"><span data-stu-id="52b62-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="52b62-209">A barra de progresso ficará verde quando o vídeo a conclusão do carregamento.</span><span class="sxs-lookup"><span data-stu-id="52b62-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="52b62-211">Clique no texto acima (**yourservicename - ativos**) para retornar para o **ativos** página.</span><span class="sxs-lookup"><span data-stu-id="52b62-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="52b62-212">Você observará que o vídeo foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="52b62-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="52b62-213">Clique nele.</span><span class="sxs-lookup"><span data-stu-id="52b62-213">Click on it.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="52b62-215">Você será redirecionado à página mostrará a que você informações detalhadas sobre seu vídeo.</span><span class="sxs-lookup"><span data-stu-id="52b62-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="52b62-216">Para poder usar o vídeo que você precisa codificar, clicando o **Encode** botão no canto superior esquerdo da página.</span><span class="sxs-lookup"><span data-stu-id="52b62-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="52b62-218">Um novo painel será exibido à direita, onde você poderá definir opções para o arquivo de codificação.</span><span class="sxs-lookup"><span data-stu-id="52b62-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="52b62-219">Defina as propriedades a seguir (alguns serão já definido por padrão):</span><span class="sxs-lookup"><span data-stu-id="52b62-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="52b62-220">**Nome do codificador de mídia *Media Encoder Standard***</span><span class="sxs-lookup"><span data-stu-id="52b62-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="52b62-221">**Predefinição de codificação *conteúdo adaptável várias taxas de bits MP4***</span><span class="sxs-lookup"><span data-stu-id="52b62-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="52b62-222">**Nome do trabalho *Media Encoder Standard processamento do Video1.mp4***</span><span class="sxs-lookup"><span data-stu-id="52b62-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="52b62-223">**Nome do ativo de mídia de saída *Video1.mp4 – Media Encoder Standard codificado***</span><span class="sxs-lookup"><span data-stu-id="52b62-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![O Portal do Azure](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="52b62-225">Clique no botão **Criar**.</span><span class="sxs-lookup"><span data-stu-id="52b62-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="52b62-226">Você observará uma barra com **trabalho de codificação adicionada**, clique na barra e um painel será exibido com o andamento da codificação exibido nela.</span><span class="sxs-lookup"><span data-stu-id="52b62-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-17.png)

    ![O Portal do Azure](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="52b62-229">Aguarde o conclusão do trabalho.</span><span class="sxs-lookup"><span data-stu-id="52b62-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="52b62-230">Quando terminar, fique à vontade fechar o painel com o 'X' no canto superior direito desse painel.</span><span class="sxs-lookup"><span data-stu-id="52b62-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-19.png)

    ![O Portal do Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="52b62-233">O tempo que necessário para isso, depende do tamanho do arquivo de vídeo.</span><span class="sxs-lookup"><span data-stu-id="52b62-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="52b62-234">Esse processo pode levar algum tempo.</span><span class="sxs-lookup"><span data-stu-id="52b62-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="52b62-235">Agora que a versão codificada do vídeo tiver sido criada, você pode publicá-lo para torná-lo acessível.</span><span class="sxs-lookup"><span data-stu-id="52b62-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="52b62-236">Para fazer isso, clique no link azul **ativos** para voltar para a página de ativos.</span><span class="sxs-lookup"><span data-stu-id="52b62-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="52b62-238">Você verá seu vídeo, juntamente com outra, o que é do \* \* tipo de ativo \* múltiplas taxas de bits MP4 \* \* \*.</span><span class="sxs-lookup"><span data-stu-id="52b62-238">You will see your video along with another, which is of \*\*Asset Type \*Multi-Bitrate MP4\*\*\*.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="52b62-240">Você pode perceber que o novo ativo, juntamente com seu vídeo inicial, é *desconhecido*, e tem o '0' bytes para ele é **tamanho**, apenas atualize a janela para atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="52b62-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="52b62-241">Clique nesse novo ativo.</span><span class="sxs-lookup"><span data-stu-id="52b62-241">Click this new asset.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="52b62-243">Você verá um painel semelhante àquele usado antes, apenas esse é um ativo diferente.</span><span class="sxs-lookup"><span data-stu-id="52b62-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="52b62-244">Clique o **publicar** botão localizado na parte superior central da página.</span><span class="sxs-lookup"><span data-stu-id="52b62-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="52b62-246">Você será solicitado a definir um **localizador**, que é o ponto de entrada para o arquivo/s em seus ativos.</span><span class="sxs-lookup"><span data-stu-id="52b62-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="52b62-247">Para o seu cenário, defina as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="52b62-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="52b62-248">**Tipo de localizador** > **progressivo**.</span><span class="sxs-lookup"><span data-stu-id="52b62-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="52b62-249">O **data** e **tempo** será definido para você, a data atual, como uma hora no futuro (Cem anos neste caso).</span><span class="sxs-lookup"><span data-stu-id="52b62-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="52b62-250">Deixe como está ou alterá-la de acordo com.</span><span class="sxs-lookup"><span data-stu-id="52b62-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="52b62-251">Para obter mais informações sobre localizadores e você pode escolher, visite o [documentação de serviços de mídia do Azure](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span><span class="sxs-lookup"><span data-stu-id="52b62-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="52b62-252">Na parte inferior desse painel, clique no **adicionar** botão.</span><span class="sxs-lookup"><span data-stu-id="52b62-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="52b62-254">Seu vídeo agora é publicado e pode ser transmitido por meio de seu ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="52b62-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="52b62-255">Ainda mais para baixo a página é uma **arquivos** seção.</span><span class="sxs-lookup"><span data-stu-id="52b62-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="52b62-256">Isso é onde será codificado em versões diferentes do seu vídeo.</span><span class="sxs-lookup"><span data-stu-id="52b62-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="52b62-257">Selecione a resolução mais alta possível um (na imagem abaixo é o arquivo de 1920 x 960), e um painel à direita será exibida.</span><span class="sxs-lookup"><span data-stu-id="52b62-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="52b62-258">Lá você encontrará uma **URL de Download**.</span><span class="sxs-lookup"><span data-stu-id="52b62-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="52b62-259">Copie essa **ponto de extremidade** conforme você o usará posteriormente em seu código.</span><span class="sxs-lookup"><span data-stu-id="52b62-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-26.png)    

    ![O Portal do Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="52b62-262">Você também pode pressionar o **reproduzir** botão para reproduzir o vídeo e testá-lo.</span><span class="sxs-lookup"><span data-stu-id="52b62-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="52b62-263">Agora, você precisará carregar o segundo vídeo que você usará neste laboratório.</span><span class="sxs-lookup"><span data-stu-id="52b62-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="52b62-264">Siga as etapas acima, repetindo o mesmo processo para o segundo vídeo.</span><span class="sxs-lookup"><span data-stu-id="52b62-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="52b62-265">Verifique se você copiar o segundo **ponto de extremidade** também.</span><span class="sxs-lookup"><span data-stu-id="52b62-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="52b62-266">Use o seguinte [link para baixar um segundo vídeo](https://vimeo.com/214402865).</span><span class="sxs-lookup"><span data-stu-id="52b62-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="52b62-267">Depois que ambos os vídeos tiverem sido publicados, você está pronto para passar para o próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="52b62-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="52b62-268">Capítulo 3 - configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="52b62-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="52b62-269">A seguir é um conjunto típico backup para o desenvolvimento com a realidade misturada e como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="52b62-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="52b62-270">Abra **Unity** e clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="52b62-270">Open **Unity** and click **New**.</span></span> 

    ![O Portal do Azure](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="52b62-272">Agora você precisará fornecer um nome de projeto do Unity, insira **MR\_360VideoStreaming.**.</span><span class="sxs-lookup"><span data-stu-id="52b62-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="52b62-273">Verifique se o tipo de projeto é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="52b62-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="52b62-274">Defina o local para um local apropriado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="52b62-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="52b62-275">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="52b62-275">Then, click **Create project**.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="52b62-277">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="52b62-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="52b62-278">Vá para ***edite* *preferências*** e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="52b62-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="52b62-279">Alteração **Editor de Script externo** à **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="52b62-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="52b62-280">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="52b62-280">Close the **Preferences** window.</span></span>

    ![O Portal do Azure](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="52b62-282">Em seguida, vá para ***arquivo* *configurações de Build*** e alternar a plataforma **plataforma Universal do Windows**, clicando no **Alternar plataforma** botão.</span><span class="sxs-lookup"><span data-stu-id="52b62-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="52b62-283">Também verifique se:</span><span class="sxs-lookup"><span data-stu-id="52b62-283">Also make sure that:</span></span>

    1. <span data-ttu-id="52b62-284">**Dispositivo de destino** é definido como **qualquer dispositivo.**</span><span class="sxs-lookup"><span data-stu-id="52b62-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="52b62-285">**Tipo de compilação** é definido como **D3D.**</span><span class="sxs-lookup"><span data-stu-id="52b62-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="52b62-286">**SDK** é definido como **mais recente instalada.**</span><span class="sxs-lookup"><span data-stu-id="52b62-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="52b62-287">**Versão do Visual Studio** é definido como **mais recente instalada.**</span><span class="sxs-lookup"><span data-stu-id="52b62-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="52b62-288">**Compilar e executar** é definido como **Máquina Local.**</span><span class="sxs-lookup"><span data-stu-id="52b62-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="52b62-289">Não se preocupe sobre como configurar o **cenas** no momento, pois você irá configurar esses mais tarde.</span><span class="sxs-lookup"><span data-stu-id="52b62-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="52b62-290">As configurações restantes devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="52b62-290">The remaining settings should be left as default for now.</span></span>

        ![Configurar o projeto do Unity](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="52b62-292">No **configurações de Build** janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o **Inspetor** está localizado.</span><span class="sxs-lookup"><span data-stu-id="52b62-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="52b62-293">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="52b62-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="52b62-294">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="52b62-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="52b62-295">**Criação de scripts** **versão de tempo de execução** deve ser **estável** (.NET 3.5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="52b62-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="52b62-296">**Script de back-end** deve ser **.NET.**</span><span class="sxs-lookup"><span data-stu-id="52b62-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="52b62-297">**Nível de compatibilidade de API** deve ser **.NET 4.6.**</span><span class="sxs-lookup"><span data-stu-id="52b62-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="52b62-299">Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.</span><span class="sxs-lookup"><span data-stu-id="52b62-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurar o projeto do Unity](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="52b62-301">Dentro de **configurações de publicação** guia, em **recursos**, verifique:</span><span class="sxs-lookup"><span data-stu-id="52b62-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="52b62-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="52b62-302">**InternetClient**</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="52b62-304">Depois de fazer essas alterações, fechar o **configurações de Build** janela.</span><span class="sxs-lookup"><span data-stu-id="52b62-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="52b62-305">Salve seu projeto \**arquivo* \* Salvar projeto \* \*.</span><span class="sxs-lookup"><span data-stu-id="52b62-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="52b62-306">Capítulo 4 - importar o pacote do InsideOutSphere Unity</span><span class="sxs-lookup"><span data-stu-id="52b62-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52b62-307">Se você quiser ignorar a *configurar o Unity* componente deste curso e continuar diretamente no código, fique à vontade para baixá-lo [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir **capítulo 5**.</span><span class="sxs-lookup"><span data-stu-id="52b62-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="52b62-308">Você ainda precisará criar um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="52b62-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="52b62-309">Para este curso, você precisará baixar o pacote Unity Asset denominada [ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="52b62-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="52b62-310">Importar instruções sobre o **unitypackage**:</span><span class="sxs-lookup"><span data-stu-id="52b62-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="52b62-311">Com o painel do Unity na sua frente, clique em **ativos** no menu na parte superior da tela, em seguida, clique em **Importar pacote > pacote personalizado**.</span><span class="sxs-lookup"><span data-stu-id="52b62-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="52b62-313">Use o seletor de arquivos para selecionar o **InsideOutSphere.unitypackage** de pacote e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="52b62-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="52b62-314">Uma lista de componentes para esse ativo será exibida para você.</span><span class="sxs-lookup"><span data-stu-id="52b62-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="52b62-315">Confirme a importação clicando **importação**.</span><span class="sxs-lookup"><span data-stu-id="52b62-315">Confirm the import by clicking **Import**.</span></span>

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="52b62-317">Quando tiver terminado a importação, você vai notar três novas pastas **materiais**, **modelos**, e **pré-fabricados**, foram adicionados ao seu **ativos**pasta.</span><span class="sxs-lookup"><span data-stu-id="52b62-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="52b62-318">Esse tipo de estrutura de pastas é típico para um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="52b62-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="52b62-320">Abra o **modelos** pasta e você verá que o **InsideOutSphere** modelo foi importado.</span><span class="sxs-lookup"><span data-stu-id="52b62-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="52b62-321">Dentro de **materiais** pasta, você encontrará o **InsideOutSpheres** material *lambert1*, junto com um material chamado *ButtonMaterial*, que é usado por GazeButton, o que você verá em breve.</span><span class="sxs-lookup"><span data-stu-id="52b62-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="52b62-322">O **pré-fabricados** pasta contém o **InsideOutSphere** pré-fabricado que contém ambos os **InsideOutSphere** *modelo* e o  *GazeButton*.</span><span class="sxs-lookup"><span data-stu-id="52b62-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="52b62-323">**Nenhum código foi incluído**, você irá escrever o código seguindo este curso.</span><span class="sxs-lookup"><span data-stu-id="52b62-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="52b62-324">Dentro de **hierarquia**, selecione o **câmera principal** de objeto e atualizar os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="52b62-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="52b62-325">**Transformação**</span><span class="sxs-lookup"><span data-stu-id="52b62-325">**Transform**</span></span>

        1.  <span data-ttu-id="52b62-326">Posição = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="52b62-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="52b62-327">Rotação = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="52b62-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="52b62-328">Escala **X**: 1, **Y**: 1, **Z**: 1.</span><span class="sxs-lookup"><span data-stu-id="52b62-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="52b62-329">**Câmera**</span><span class="sxs-lookup"><span data-stu-id="52b62-329">**Camera**</span></span>

        1. <span data-ttu-id="52b62-330">**Limpar os sinalizadores de**: Cor sólida.</span><span class="sxs-lookup"><span data-stu-id="52b62-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="52b62-331">**Planos de recorte**: Próximo: 0,1, agora: 6.</span><span class="sxs-lookup"><span data-stu-id="52b62-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="52b62-333">Navegue até a **pré-fabricado** pasta e, em seguida, arraste o **InsideOutSphere** pré-fabricado para o **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="52b62-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="52b62-335">Expanda o **InsideOutSphere** dentro do objeto de **hierarquia** clicando na pequena seta ao lado dele.</span><span class="sxs-lookup"><span data-stu-id="52b62-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="52b62-336">Você verá uma **filho** objeto abaixo dele chamado **GazeButton**.</span><span class="sxs-lookup"><span data-stu-id="52b62-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="52b62-337">Isso será usado para alterar o plano e, portanto, vídeos.</span><span class="sxs-lookup"><span data-stu-id="52b62-337">This will be used to change scenes and thus videos.</span></span>

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="52b62-339">Na janela Inspetor, clique no **InsideOutSphere**do componente de transformação, certifique-se de que as seguintes propriedades são definidas:</span><span class="sxs-lookup"><span data-stu-id="52b62-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="52b62-340">TRANSFORMAÇÃO - POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="52b62-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="52b62-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-341">**X** 0</span></span>  |          <span data-ttu-id="52b62-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-342">**Y** 0</span></span>          |  <span data-ttu-id="52b62-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="52b62-344">TRANSFORMAÇÃO - ROTAÇÃO</span><span class="sxs-lookup"><span data-stu-id="52b62-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="52b62-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-345">**X** 0</span></span>  |          <span data-ttu-id="52b62-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="52b62-346">**Y** -50</span></span>        |  <span data-ttu-id="52b62-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="52b62-348">TRANSFORMAÇÃO - ESCALA</span><span class="sxs-lookup"><span data-stu-id="52b62-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="52b62-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="52b62-349">**X** 1</span></span>   |          <span data-ttu-id="52b62-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="52b62-350">**Y** 1</span></span>          |  <span data-ttu-id="52b62-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="52b62-351">**Z** 1</span></span>  |

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="52b62-353">Clique no **GazeButton** objeto filho e defina seu **transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="52b62-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="52b62-354">TRANSFORMAÇÃO - POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="52b62-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="52b62-355">**X** 3.6</span><span class="sxs-lookup"><span data-stu-id="52b62-355">**X** 3.6</span></span>|          <span data-ttu-id="52b62-356">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="52b62-356">**Y** 1.3</span></span>        |  <span data-ttu-id="52b62-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="52b62-358">TRANSFORMAÇÃO - ROTAÇÃO</span><span class="sxs-lookup"><span data-stu-id="52b62-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="52b62-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-359">**X** 0</span></span>  |          <span data-ttu-id="52b62-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-360">**Y** 0</span></span>          |  <span data-ttu-id="52b62-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="52b62-362">TRANSFORMAÇÃO - ESCALA</span><span class="sxs-lookup"><span data-stu-id="52b62-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="52b62-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="52b62-363">**X** 1</span></span>   |          <span data-ttu-id="52b62-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="52b62-364">**Y** 1</span></span>          |  <span data-ttu-id="52b62-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="52b62-365">**Z** 1</span></span>  |

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="52b62-367">Capítulo 5 - criar a classe VideoController</span><span class="sxs-lookup"><span data-stu-id="52b62-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="52b62-368">O **VideoController** classe hospeda as duas extremidades de vídeos que serão usadas para transmitir o conteúdo do serviço de mídia do Azure.</span><span class="sxs-lookup"><span data-stu-id="52b62-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="52b62-369">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="52b62-369">To create this class:</span></span>

1.  <span data-ttu-id="52b62-370">Com o botão direito no **pasta ativo**, localizado na **Project** painel e clique **criar > pasta**.</span><span class="sxs-lookup"><span data-stu-id="52b62-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="52b62-371">Nomeie a pasta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="52b62-371">Name the folder **Scripts**.</span></span>

    ![Criar a classe VideoController](images/AzureLabs-Lab6-43.png)

    ![Criar a classe VideoController](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="52b62-374">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="52b62-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="52b62-375">Clique com botão direito dentro da pasta e clique em **criar > C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="52b62-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="52b62-376">Nomeie o script **VideoController**.</span><span class="sxs-lookup"><span data-stu-id="52b62-376">Name the script **VideoController**.</span></span>

    ![Criar a classe VideoController](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="52b62-378">Clique duas vezes na nova **VideoController** script para abri-lo com **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="52b62-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![Criar a classe VideoController](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="52b62-380">Atualize os namespaces na parte superior do arquivo de código da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="52b62-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="52b62-381">Insira as seguintes variáveis na **VideoController** classe, juntamente com o **Awake()** método:</span><span class="sxs-lookup"><span data-stu-id="52b62-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

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

7.  <span data-ttu-id="52b62-382">Agora é o momento para inserir os pontos de extremidade de seus vídeos do serviço de mídia do Azure:</span><span class="sxs-lookup"><span data-stu-id="52b62-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="52b62-383">O primeiro para o *video1endpoint* variável.</span><span class="sxs-lookup"><span data-stu-id="52b62-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="52b62-384">O segundo para o *video2endpoint* variável.</span><span class="sxs-lookup"><span data-stu-id="52b62-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="52b62-385">Há um problema conhecido com o uso *https* dentro do Unity, com a versão 2017.4.1f1.</span><span class="sxs-lookup"><span data-stu-id="52b62-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="52b62-386">Se os vídeos de fornecem um erro no play, tente usar 'http'.</span><span class="sxs-lookup"><span data-stu-id="52b62-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="52b62-387">Em seguida, o **Start ()** método precisa ser editado.</span><span class="sxs-lookup"><span data-stu-id="52b62-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="52b62-388">Esse método será disparado sempre que o usuário alterna a cena (troca, consequentemente, o vídeo), observando o botão de olhares.</span><span class="sxs-lookup"><span data-stu-id="52b62-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="52b62-389">Seguindo a **Start ()** método, insira o **playVideo** *IEnumerator* método, que será usado para iniciar vídeos diretamente (de modo que não é visto nenhum repetitivo).</span><span class="sxs-lookup"><span data-stu-id="52b62-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

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

10. <span data-ttu-id="52b62-390">O último método que você precisa para essa classe é o **ChangeScene()** método, que será usado para alternar entre as cenas.</span><span class="sxs-lookup"><span data-stu-id="52b62-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="52b62-391">O **ChangeScene()** método usa um C útil\# recurso chamado o *operador condicional*.</span><span class="sxs-lookup"><span data-stu-id="52b62-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="52b62-392">Isso permite condições sejam verificadas e, em seguida, os valores retornados com base no resultado da verificação, tudo em uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="52b62-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="52b62-393">Siga esse [link para saber mais sobre o operador condicional](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span><span class="sxs-lookup"><span data-stu-id="52b62-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="52b62-394">Salve suas alterações no Visual Studio antes de retornar para o Unity.</span><span class="sxs-lookup"><span data-stu-id="52b62-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="52b62-395">Novamente no Editor do Unity, clique e arraste a **VideoController** classe [from] {.underline} o **Scripts** pasta para o **câmera principal** do objeto no  **Hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="52b62-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="52b62-396">Clique no **câmera principal** e examine o **painel Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="52b62-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="52b62-397">Você observará que, no componente de Script recém-adicionados, há um campo com um valor vazio.</span><span class="sxs-lookup"><span data-stu-id="52b62-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="52b62-398">Isso é um campo de referência, que tem como alvo as variáveis públicas dentro de seu código.</span><span class="sxs-lookup"><span data-stu-id="52b62-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="52b62-399">Arraste o **InsideOutSphere** de objeto o **painel de hierarquia** para o **esfera** slot, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="52b62-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="52b62-400">![Criar a classe VideoController](images/AzureLabs-Lab6-47.png)
    ![criar a classe VideoController](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="52b62-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="52b62-401">Capítulo 6 - criar a classe de olhar</span><span class="sxs-lookup"><span data-stu-id="52b62-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="52b62-402">Essa classe é responsável por criar uma **Raycast** que beprojected encaminhará da **câmera principal**, para detectar qual objeto de usuário está observando.</span><span class="sxs-lookup"><span data-stu-id="52b62-402">This class is responsible for creating a **Raycast** that will beprojected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="52b62-403">Nesse caso, o **Raycast** precisará identificar se o usuário está observando o **GazeButton** do objeto na cena e disparar um comportamento.</span><span class="sxs-lookup"><span data-stu-id="52b62-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="52b62-404">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="52b62-404">To create this Class:</span></span>

1.  <span data-ttu-id="52b62-405">Vá para o **Scripts** pasta que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="52b62-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="52b62-406">Clique com botão direito no **Project** painel, \**crie* \* C\# Script \* \*.</span><span class="sxs-lookup"><span data-stu-id="52b62-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="52b62-407">Nomeie o script **olhares**.</span><span class="sxs-lookup"><span data-stu-id="52b62-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="52b62-408">Clique duas vezes na nova ***olhares*** script para abri-lo com **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="52b62-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="52b62-409">Verifique se que o namespace a seguir está na parte superior do script e remova todos os outros:</span><span class="sxs-lookup"><span data-stu-id="52b62-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="52b62-410">Em seguida, adicione as seguintes variáveis dentro do **olhares** classe:</span><span class="sxs-lookup"><span data-stu-id="52b62-410">Then add the following variables inside the **Gaze** class:</span></span>

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

6.  <span data-ttu-id="52b62-411">Código para o **Awake()** e **Start ()** métodos agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="52b62-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="52b62-412">Adicione o seguinte código na **Update ()** método um Raycast do projeto e detectar a ocorrência de destino:</span><span class="sxs-lookup"><span data-stu-id="52b62-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

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

8.  <span data-ttu-id="52b62-413">Salve suas alterações no Visual Studio antes de retornar para o Unity.</span><span class="sxs-lookup"><span data-stu-id="52b62-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="52b62-414">Clique e arraste a **olhares** classe da pasta de Scripts para o objeto de câmera principal na **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="52b62-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="52b62-415">Capítulo 7 - instalação as duas cenas de Unity</span><span class="sxs-lookup"><span data-stu-id="52b62-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="52b62-416">O objetivo deste capítulo é configurar as duas cenas, cada uma hospedando um vídeo em fluxo.</span><span class="sxs-lookup"><span data-stu-id="52b62-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="52b62-417">Você vai duplicar a cena que você já tiver criado, para que você não precisa configurá-lo novamente, embora, em seguida, você editará a nova cena, para que o *GazeButton* objeto está em um local diferente e tem uma aparência diferente.</span><span class="sxs-lookup"><span data-stu-id="52b62-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="52b62-418">Isso é para mostrar como alterar entre as cenas.</span><span class="sxs-lookup"><span data-stu-id="52b62-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="52b62-419">Fazer isso acessando **arquivo > Salvar cena como...** . Salvamento janela será exibida.</span><span class="sxs-lookup"><span data-stu-id="52b62-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="52b62-420">Clique o **nova pasta** botão.</span><span class="sxs-lookup"><span data-stu-id="52b62-420">Click the **New folder** button.</span></span>

    ![Capítulo 7 - instalação as duas cenas de Unity](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="52b62-422">Nomeie a pasta **cenas**.</span><span class="sxs-lookup"><span data-stu-id="52b62-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="52b62-423">O **salvar cena** janela ainda será aberta.</span><span class="sxs-lookup"><span data-stu-id="52b62-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="52b62-424">Abra seu recém-criado **cenas** pasta.</span><span class="sxs-lookup"><span data-stu-id="52b62-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="52b62-425">No **nome do arquivo:** campo de texto, digite **VideoScene1**, em seguida, pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="52b62-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="52b62-426">Novamente no Unity, abra sua **cenas** pasta e o botão esquerdo do mouse seu **VideoScene1** arquivo.</span><span class="sxs-lookup"><span data-stu-id="52b62-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="52b62-427">Usar o teclado e pressione **Ctrl + D** duplicará essa cena</span><span class="sxs-lookup"><span data-stu-id="52b62-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="52b62-428">O **duplicar** também pode ser executado, navegando até o comando **Editar > Duplicar**.</span><span class="sxs-lookup"><span data-stu-id="52b62-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="52b62-429">Unity automaticamente incrementar o número de nomes da cena, mas verifique-lo de qualquer forma, se que ele corresponde ao código inserido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="52b62-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="52b62-430">Você deve ter **VideoScene1** e **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="52b62-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="52b62-431">Com suas duas cenas, vá para **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="52b62-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="52b62-432">Com o **configurações de Build** janela aberta, arraste seu plano para o **cenas em compilação** seção.</span><span class="sxs-lookup"><span data-stu-id="52b62-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="52b62-434">Você pode selecionar ambas suas cenas de sua **cenas** pasta por meio de espera a **Ctrl** botão e, em seguida, left-clicking cada cena e, por fim, arraste os dois em.</span><span class="sxs-lookup"><span data-stu-id="52b62-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="52b62-435">Fechar o **configurações de Build** janela e clique duas vezes na **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="52b62-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="52b62-436">Com a segunda cena aberta, clique no **GazeButton** objeto filho do **InsideOutSphere**e defina sua transformação da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="52b62-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="52b62-437">TRANSFORMAÇÃO - POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="52b62-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="52b62-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-438">**X** 0</span></span>  |         <span data-ttu-id="52b62-439">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="52b62-439">**Y** 1.3</span></span>         | <span data-ttu-id="52b62-440">**Z** 3.6</span><span class="sxs-lookup"><span data-stu-id="52b62-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="52b62-441">TRANSFORMAÇÃO - ROTAÇÃO</span><span class="sxs-lookup"><span data-stu-id="52b62-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="52b62-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-442">**X** 0</span></span>  |          <span data-ttu-id="52b62-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-443">**Y** 0</span></span>          |  <span data-ttu-id="52b62-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="52b62-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="52b62-445">TRANSFORMAÇÃO - ESCALA</span><span class="sxs-lookup"><span data-stu-id="52b62-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="52b62-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="52b62-446">**X** 1</span></span>   |          <span data-ttu-id="52b62-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="52b62-447">**Y** 1</span></span>          |  <span data-ttu-id="52b62-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="52b62-448">**Z** 1</span></span>  |

10. <span data-ttu-id="52b62-449">Com o **GazeButton** filho ainda selecionado, procure na **Inspetor** e nos **filtro de malha**.</span><span class="sxs-lookup"><span data-stu-id="52b62-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="52b62-450">Clique o destino pequeno ao lado de **malha** campo de referência:</span><span class="sxs-lookup"><span data-stu-id="52b62-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="52b62-452">Um **selecionar malha** janela pop-up será exibida.</span><span class="sxs-lookup"><span data-stu-id="52b62-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="52b62-453">Clique duas vezes o **cubo** na lista de malha **ativos**.</span><span class="sxs-lookup"><span data-stu-id="52b62-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="52b62-455">O **filtro de malha** atualizará e ser agora uma **cubo**.</span><span class="sxs-lookup"><span data-stu-id="52b62-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="52b62-456">Agora, clique o **engrenagem** ícone próximo ao **esfera Colisor** e clique em **remover componente**, para excluir o colisor deste objeto.</span><span class="sxs-lookup"><span data-stu-id="52b62-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="52b62-458">Com o **GazeButton** ainda selecionada, clique o **Add Component** botão na parte inferior da **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="52b62-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="52b62-459">No campo de pesquisa, digite **caixa de**, e **Box Collider** será ser uma opção – clique que, para adicionar um **Box Collider** ao seu **GazeButton** objeto .</span><span class="sxs-lookup"><span data-stu-id="52b62-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="52b62-461">O **GazeButton** está agora parcialmente atualizada, para uma aparência diferente, no entanto, agora você criará uma nova **Material**, de modo que ele tem uma aparência completamente diferente e é mais fácil de reconhecer como um objeto diferente, que o objeto na cena primeiro.</span><span class="sxs-lookup"><span data-stu-id="52b62-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="52b62-462">Navegue até sua **materiais** pasta, dentro de **painel projeto**.</span><span class="sxs-lookup"><span data-stu-id="52b62-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="52b62-463">Duplicar o **ButtonMaterial** Material (pressione **Ctrl** + **1!d** no teclado ou o botão esquerdo do mouse a **Material**, em seguida, dos **edite** opção de menu, selecione arquivo **duplicar**).</span><span class="sxs-lookup"><span data-stu-id="52b62-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="52b62-464">![Capítulo 7-- Configurar as duas cenas Unity](images/AzureLabs-Lab6-55.png)
    ![capítulo 7-- configurar as duas cenas de Unity](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="52b62-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="52b62-465">Selecione a nova **ButtonMaterial** Material (aqui chamado **ButtonMaterial 1**) e dentro a **Inspetor**, clique no **Albedo** cor janela.</span><span class="sxs-lookup"><span data-stu-id="52b62-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="52b62-466">Um pop-up será exibida, onde você pode selecionar outra cor (escolha aquele que você deseja), em seguida, feche o janela pop-up.</span><span class="sxs-lookup"><span data-stu-id="52b62-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="52b62-467">O Material será sua própria instância e diferente do original.</span><span class="sxs-lookup"><span data-stu-id="52b62-467">The Material will be its own instance, and different to the original.</span></span>

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="52b62-469">Arraste o novo **Material** até a **GazeButton** filho, agora atualizar completamente sua aparência, para que ele seja facilmente perceptível a partir do primeiro botão de segundo plano.</span><span class="sxs-lookup"><span data-stu-id="52b62-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="52b62-471">Neste ponto, você pode testar o projeto no Editor antes de compilar o projeto UWP.</span><span class="sxs-lookup"><span data-stu-id="52b62-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="52b62-472">Pressione a **reproduzir** botão na **Editor** e o desgaste fone de ouvido.</span><span class="sxs-lookup"><span data-stu-id="52b62-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="52b62-474">Examinar os dois **GazeButton** objetos para alternar entre o primeiro e segundo vídeo.</span><span class="sxs-lookup"><span data-stu-id="52b62-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="52b62-475">Capítulo 8 - Compile a solução UWP</span><span class="sxs-lookup"><span data-stu-id="52b62-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="52b62-476">Depois que você garante que o editor não tem erros, você está pronto para compilação.</span><span class="sxs-lookup"><span data-stu-id="52b62-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="52b62-477">Para construir:</span><span class="sxs-lookup"><span data-stu-id="52b62-477">To Build:</span></span>

1.  <span data-ttu-id="52b62-478">Salve a cena atual clicando em **arquivo > Salvar**.</span><span class="sxs-lookup"><span data-stu-id="52b62-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="52b62-479">Marque a caixa denominada **Unity C\# projetos** (Isso é importante porque ele permitirá que você editar as classes após a compilação for concluída).</span><span class="sxs-lookup"><span data-stu-id="52b62-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="52b62-480">Vá para **arquivo > configurações de Build**, clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="52b62-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="52b62-481">Você será solicitado a selecionar a pasta onde você deseja buildthe solução.</span><span class="sxs-lookup"><span data-stu-id="52b62-481">You will be prompted to select the folder where you want to buildthe Solution.</span></span>

5.  <span data-ttu-id="52b62-482">Criar uma **compilações** pasta e dentro dessa pasta, crie outra pasta com um nome apropriado de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="52b62-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="52b62-483">Clique em sua nova pasta e, em seguida, clique em **Selecionar pasta**, portanto, para escolher a pasta, para iniciar a compilação nesse local.</span><span class="sxs-lookup"><span data-stu-id="52b62-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="52b62-484">![Capítulo 8 – Criar a solução UWP](images/AzureLabs-Lab6-60.png)
    ![capítulo 8 - Compile a solução UWP](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="52b62-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="52b62-485">Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um **Explorador de arquivos** janela no local de sua compilação.</span><span class="sxs-lookup"><span data-stu-id="52b62-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="52b62-486">Capítulo 9 - implantar no computador Local</span><span class="sxs-lookup"><span data-stu-id="52b62-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="52b62-487">Quando a compilação for concluída, uma **Explorador de arquivos** janela será exibida no local de sua compilação.</span><span class="sxs-lookup"><span data-stu-id="52b62-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="52b62-488">Abra a pasta denominada e criado para e, em seguida, clique duas vezes no arquivo de solução (. sln) nessa pasta, para abrir sua solução com o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="52b62-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="52b62-489">Tudo o que resta fazer é implantar seu aplicativo no seu computador (ou *computador Local*).</span><span class="sxs-lookup"><span data-stu-id="52b62-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="52b62-490">Para implantar a máquina Local:</span><span class="sxs-lookup"><span data-stu-id="52b62-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="52b62-491">Na **Visual Studio 2017**, abra o arquivo de solução que acabou de ser criado.</span><span class="sxs-lookup"><span data-stu-id="52b62-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="52b62-492">No **plataforma da solução**, selecione **x86, computador Local**.</span><span class="sxs-lookup"><span data-stu-id="52b62-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="52b62-493">No **configuração da solução** selecionar **depurar**.</span><span class="sxs-lookup"><span data-stu-id="52b62-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![Capítulo 9 – Implantar no computador Local](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="52b62-495">Agora, você precisará restaurar todos os pacotes para sua solução.</span><span class="sxs-lookup"><span data-stu-id="52b62-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="52b62-496">Clique com botão direito no seu **Solution**e clique em **restaurar pacotes do NuGet para solução...**</span><span class="sxs-lookup"><span data-stu-id="52b62-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="52b62-497">Isso é feito porque os pacotes que Unity criado precisam ser direcionados para funcionar com as referências de computadores locais.</span><span class="sxs-lookup"><span data-stu-id="52b62-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="52b62-498">Vá para **menu Build** e clique em **implantar solução** para carregar o aplicativo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="52b62-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="52b62-499">Visual Studio criará primeiro e, em seguida, implantar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="52b62-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="52b62-500">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="52b62-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![Capítulo 9 – Implantar no computador Local](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="52b62-502">Quando você executar o aplicativo de realidade misturada, você irá obedecer a **InsideOutSphere** modelo que usado dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="52b62-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="52b62-503">Essa esfera será onde o vídeo será transmitido, fornecendo uma visão de 360 graus de vídeo de entrada (que foi é feito para esse tipo de ponto de Vista).</span><span class="sxs-lookup"><span data-stu-id="52b62-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="52b62-504">Não se surpreenda que se o vídeo leva alguns segundos para carregar, seu aplicativo está sujeito a velocidade com a Internet disponível, como o vídeo precisa ser buscadas e, em seguida, baixados, portanto, para transmitir em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="52b62-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="52b62-505">Quando você estiver pronto, alterar cenas e abra seu segundo vídeo, pela observação na esfera vermelha!</span><span class="sxs-lookup"><span data-stu-id="52b62-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="52b62-506">Em seguida, fique à vontade voltar, usando o cubo azul na cena segundo!</span><span class="sxs-lookup"><span data-stu-id="52b62-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="52b62-507">O aplicativo de serviço de mídia do Azure concluído</span><span class="sxs-lookup"><span data-stu-id="52b62-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="52b62-508">Parabéns, você criou um aplicativo de realidade mista que aproveita o serviço de mídia do Azure para transmitir 360 vídeos.</span><span class="sxs-lookup"><span data-stu-id="52b62-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![resultado de laboratório](images/AzureLabs-Lab6-00.png)

![resultado de laboratório](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="52b62-511">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="52b62-511">Bonus Exercises</span></span>

<span data-ttu-id="52b62-512">**Exercício 1**</span><span class="sxs-lookup"><span data-stu-id="52b62-512">**Exercise 1**</span></span>

<span data-ttu-id="52b62-513">Ele é totalmente possível usar apenas uma única cena para alterar o vídeos dentro deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="52b62-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="52b62-514">Experimentar seu aplicativo e torná-lo em uma única cena!</span><span class="sxs-lookup"><span data-stu-id="52b62-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="52b62-515">Talvez, até mesmo adicione outro vídeo à combinação.</span><span class="sxs-lookup"><span data-stu-id="52b62-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="52b62-516">**Exercício 2**</span><span class="sxs-lookup"><span data-stu-id="52b62-516">**Exercise 2**</span></span>

<span data-ttu-id="52b62-517">Teste com o Azure e o Unity e tentar implementar a capacidade para o aplicativo selecionar automaticamente um vídeo com um tamanho de arquivo diferente, dependendo da força de uma conexão de Internet.</span><span class="sxs-lookup"><span data-stu-id="52b62-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


