---
title: Sr e Azure 305 – funções e armazenamento
description: Conclua este curso para aprender a implementar o armazenamento e as funções do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, funções, armazenamento, hololens, imersão, VR
ms.openlocfilehash: 79c276d45163465c9921d02343d41d52d5f094e7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437982"
---
>[!NOTE]
><span data-ttu-id="2ed9a-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="2ed9a-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="2ed9a-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="2ed9a-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="2ed9a-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="2ed9a-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="2ed9a-110">Sr e Azure 305: funções e armazenamento</span><span class="sxs-lookup"><span data-stu-id="2ed9a-110">MR and Azure 305: Functions and storage</span></span>

![início do produto final](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="2ed9a-112">Neste curso, você aprenderá a criar e usar Azure Functions e armazenar dados com um recurso de armazenamento do Azure, em um aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="2ed9a-113">*Azure Functions* é um serviço da Microsoft, que permite aos desenvolvedores executar pequenas partes de código, ' Functions ', no Azure.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="2ed9a-114">Isso fornece uma maneira de delegar trabalho para a nuvem, em vez de seu aplicativo local, que pode ter muitos benefícios.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="2ed9a-115">O *Azure Functions* dá suporte a várias linguagens de desenvolvimento, incluindo C\#, F\#, Node. js, Java e php.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="2ed9a-116">Para obter mais informações, visite o [artigo Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="2ed9a-117">O *armazenamento do Azure* é um serviço de nuvem da Microsoft, que permite aos desenvolvedores armazenar dados, com o seguro de que ele será altamente disponível, seguro, durável, escalonável e redundante.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="2ed9a-118">Isso significa que a Microsoft tratará de toda a manutenção e problemas críticos para você.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="2ed9a-119">Para obter mais informações, visite o [artigo armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="2ed9a-120">Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada que poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="2ed9a-121">Permitir que o usuário olhar em uma cena.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="2ed9a-122">Dispare a geração de objetos quando o usuário gazes em um "botão" 3D.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="2ed9a-123">Os objetos gerados serão escolhidos por uma função do Azure.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="2ed9a-124">À medida que cada objeto é gerado, o aplicativo armazenará o tipo de objeto em um *arquivo do Azure*, localizado no *armazenamento do Azure*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="2ed9a-125">Ao carregar uma segunda vez, os dados de *arquivo do Azure* serão recuperados e usados para reproduzir as ações de geração da instância anterior do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="2ed9a-126">Em seu aplicativo, cabe a você como você integrará os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="2ed9a-127">Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="2ed9a-128">É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="2ed9a-129">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="2ed9a-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="2ed9a-130">Course</span><span class="sxs-lookup"><span data-stu-id="2ed9a-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="2ed9a-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="2ed9a-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="2ed9a-132"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="2ed9a-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="2ed9a-133">Sr e Azure 305: funções e armazenamento</span><span class="sxs-lookup"><span data-stu-id="2ed9a-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="2ed9a-134">✔️</span><span class="sxs-lookup"><span data-stu-id="2ed9a-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="2ed9a-135">✔️</span><span class="sxs-lookup"><span data-stu-id="2ed9a-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="2ed9a-136">Embora este curso se concentre principalmente em fones de ouvido (VR) de realidade mista do Windows, você também pode aplicar o que aprende neste curso ao Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="2ed9a-137">Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ed9a-138">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2ed9a-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="2ed9a-139">Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="2ed9a-140">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="2ed9a-141">Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="2ed9a-142">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="2ed9a-143">Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)</span><span class="sxs-lookup"><span data-stu-id="2ed9a-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="2ed9a-144">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="2ed9a-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2ed9a-145">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="2ed9a-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2ed9a-146">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="2ed9a-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2ed9a-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="2ed9a-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="2ed9a-148">Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="2ed9a-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="2ed9a-149">Uma assinatura para uma conta do Azure para criar recursos do Azure</span><span class="sxs-lookup"><span data-stu-id="2ed9a-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="2ed9a-150">Acesso à Internet para a instalação do Azure e recuperação de dados</span><span class="sxs-lookup"><span data-stu-id="2ed9a-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="2ed9a-151">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="2ed9a-151">Before you start</span></span>

<span data-ttu-id="2ed9a-152">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="2ed9a-153">Capítulo 1-o portal do Azure</span><span class="sxs-lookup"><span data-stu-id="2ed9a-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="2ed9a-154">Para usar o **serviço de armazenamento do Azure**, você precisará criar e configurar uma **conta de armazenamento** no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="2ed9a-155">Faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="2ed9a-156">Se você ainda não tiver uma conta do Azure, será necessário criar uma.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="2ed9a-157">Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="2ed9a-158">Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure *conta de armazenamento*e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![pesquisa de armazenamento do Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="2ed9a-160">A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="2ed9a-161">A nova página fornecerá uma descrição do serviço de *conta de armazenamento do Azure* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="2ed9a-162">Na parte inferior esquerda desse prompt, selecione o botão **criar** para criar uma associação com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Criar serviço](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="2ed9a-164">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="2ed9a-165">Insira um *nome* para sua conta, lembre-se de que esse campo aceita apenas números e letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="2ed9a-166">Para *modelo de implantação*, selecione **Gerenciador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="2ed9a-167">Para *tipo de conta*, selecione **armazenamento (uso geral v1)** .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="2ed9a-168">Determine o *local* do seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="2ed9a-169">O local ideal seria na região em que o aplicativo seria executado.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="2ed9a-170">Alguns ativos do Azure só estão disponíveis em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="2ed9a-171">Para *replicação* **, selecione leitura-acesso-armazenamento com REDUNDÂNCIA geográfica (ra-grs)** .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="2ed9a-172">Para *desempenho*, selecione **padrão**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="2ed9a-173">Deixe a *transferência segura necessária* como **desabilitada**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="2ed9a-174">Selecione uma *assinatura*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="2ed9a-175">Escolha um *grupo de recursos* ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="2ed9a-176">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="2ed9a-177">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="2ed9a-178">Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="2ed9a-179">Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="2ed9a-180">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-180">Select **Create**.</span></span>

        ![informações do serviço de entrada](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="2ed9a-182">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="2ed9a-183">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Nova notificação no portal do Azure](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="2ed9a-185">Clique nas notificações para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-185">Click on the notifications to explore your new Service instance.</span></span>

    ![ir para o recurso](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="2ed9a-187">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="2ed9a-188">Você será levado para sua nova instância de serviço da *conta de armazenamento* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![teclas de acesso](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="2ed9a-190">Clique em *chaves de acesso*para revelar os pontos de extremidade para este serviço de nuvem.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="2ed9a-191">Use o *bloco de notas* ou semelhante para copiar uma de suas chaves para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="2ed9a-192">Além disso, observe o valor da *cadeia de conexão* , pois ele será usado na classe *azureservices* , que será criada mais tarde.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![copiar cadeia de conexão](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="2ed9a-194">Capítulo 2-Configurando uma função do Azure</span><span class="sxs-lookup"><span data-stu-id="2ed9a-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="2ed9a-195">Agora, você escreverá uma **função** **do Azure** no serviço do Azure.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="2ed9a-196">Você pode usar uma **função do Azure** para fazer praticamente tudo o que faria com uma função clássica em seu código, a diferença é que essa função pode ser acessada por qualquer aplicativo que tenha credenciais para acessar sua conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="2ed9a-197">Para criar uma função do Azure:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="2ed9a-198">No *portal do Azure*, clique em **novo** no canto superior esquerdo e procure *aplicativo de funções*e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![Criar aplicativo de funções](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="2ed9a-200">A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="2ed9a-201">A nova página fornecerá uma descrição do serviço de *aplicativo de funções do Azure* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="2ed9a-202">Na parte inferior esquerda desse prompt, selecione o botão **criar** para criar uma associação com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![informações do aplicativo de funções](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="2ed9a-204">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="2ed9a-205">Forneça um *nome de aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-205">Provide an *App name*.</span></span> <span data-ttu-id="2ed9a-206">Somente letras e números podem ser usados aqui (é permitido um caso superior ou inferior).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="2ed9a-207">Selecione sua *assinatura*preferida.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="2ed9a-208">Escolha um *grupo de recursos* ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="2ed9a-209">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="2ed9a-210">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="2ed9a-211">Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="2ed9a-212">Para este exercício, selecione *Windows* como o **sistema operacional**escolhido.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="2ed9a-213">Selecione *plano de consumo* para o **plano de hospedagem**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="2ed9a-214">Determine o *local* do seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="2ed9a-215">O local ideal seria na região em que o aplicativo seria executado.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="2ed9a-216">Alguns ativos do Azure só estão disponíveis em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="2ed9a-217">Para obter um desempenho ideal, selecione a mesma região que a conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="2ed9a-218">Para *armazenamento*, selecione **usar existente**e, em seguida, usando o menu suspenso, localize o armazenamento criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="2ed9a-219">Deixe *Application insights* desativado para este exercício.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-219">Leave *Application Insights* off for this exercise.</span></span>

        ![detalhes do aplicativo de função de entrada](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="2ed9a-221">Clique no botão **Criar**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="2ed9a-222">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="2ed9a-223">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Nova notificação do portal do Azure](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="2ed9a-225">Clique nas notificações para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![ir para o aplicativo de função de recurso](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="2ed9a-227">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="2ed9a-228">Você será levado para sua nova instância do serviço *aplicativo de funções* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="2ed9a-229">No painel *aplicativo de funções* , passe o mouse sobre as *funções*, localizadas no painel à esquerda e clique no símbolo **+ (mais)** .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![criar nova função](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="2ed9a-231">Na página seguinte, verifique se **webhook + API** está selecionado e, para *escolher um idioma,* selecione **Csharp**, pois esse será o idioma usado para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="2ed9a-232">Por fim, clique no botão **criar esta função** .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-232">Lastly, click the **Create this function** button.</span></span>

    ![selecionar o Web Hook Csharp](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="2ed9a-234">Você deve ser levado para a página de código (Run. CSX), se não estiver, clique na função recém-criada na lista de funções no painel à esquerda.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![abrir nova função](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="2ed9a-236">Copie o código a seguir em sua função.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-236">Copy the following code into your function.</span></span> <span data-ttu-id="2ed9a-237">Essa função simplesmente retornará um inteiro aleatório entre 0 e 2, quando chamado.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="2ed9a-238">Não se preocupe com o código existente, fique à vontade para colar na parte superior.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. <span data-ttu-id="2ed9a-239">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-239">Select **Save**.</span></span>

14. <span data-ttu-id="2ed9a-240">O resultado deve ser semelhante à imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="2ed9a-241">Clique em **obter URL da função** e anote o *ponto de extremidade* exibido.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="2ed9a-242">Você precisará inseri-lo na classe *azureservices* que será criada posteriormente neste curso.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![obter ponto de extremidade de função](images/AzureLabs-Lab5-16.png)

    ![obter ponto de extremidade de função](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="2ed9a-245">Capítulo 3-Configurando o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="2ed9a-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="2ed9a-246">A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="2ed9a-247">Configure e teste seu headset de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="2ed9a-248">Você **não** precisará de controladores de animação para este curso.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="2ed9a-249">Se você precisar de suporte para configurar o headset de imersão, [visite o artigo configuração de realidade misturada](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="2ed9a-250">Abra o Unity e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-250">Open Unity and click **New**.</span></span>

    ![criar novo projeto de Unity](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="2ed9a-252">Agora, você precisará fornecer um nome de projeto de Unity.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="2ed9a-253">Insira **MR_Azure_Functions**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="2ed9a-254">Verifique se o tipo de projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="2ed9a-255">Defina o *local* como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="2ed9a-256">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-256">Then, click **Create project**.</span></span>

    ![Dê um nome ao novo projeto do Unity](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="2ed9a-258">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="2ed9a-259">Vá para **Editar** **preferências** de > e, em seguida, na nova janela, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-259">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="2ed9a-260">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="2ed9a-261">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-261">Close the **Preferences** window.</span></span>

    ![definir o Visual Studio como editor de script](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="2ed9a-263">Em seguida, vá para **arquivo** > **configurações de Build** e alterne a plataforma para **plataforma universal do Windows**clicando no botão **alternar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-263">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![alternar plataforma para UWP](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="2ed9a-265">Vá para **arquivo** > **configurações de compilação** e verifique se:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-265">Go to **File** > **Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="2ed9a-266">O **dispositivo de destino** está definido como **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="2ed9a-267">Para o Microsoft HoloLens, defina o **dispositivo de destino** para o *hololens*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="2ed9a-268">O **tipo de compilação** está definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="2ed9a-269">O **SDK** está definido para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="2ed9a-270">A **versão do Visual Studio** está definida para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="2ed9a-271">**Compilar e executar** é definido como **computador local**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="2ed9a-272">Salve a cena e adicione-a à compilação.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="2ed9a-273">Faça isso selecionando **Adicionar abrir cenas**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="2ed9a-274">Uma janela salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-274">A save window will appear.</span></span>

            ![Adicionar cenas abertas](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="2ed9a-276">Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![criar pasta de cenas](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="2ed9a-278">Abra sua pasta de **cenas** recém-criada e, no campo **nome do arquivo:** , digite **FunctionsScene**e pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![cena de salvar funções](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="2ed9a-280">As configurações restantes, em **configurações de compilação**, devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![cena de salvar funções](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="2ed9a-282">Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![configurações do Player no Inspetor](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="2ed9a-284">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="2ed9a-285">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="2ed9a-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="2ed9a-286">A **versão de tempo de execução de script** deve ser **Experimental** (.NET 4,6 equivalente), o que irá disparar uma necessidade de reiniciar o editor.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="2ed9a-287">O **back-end de script** deve ser **.net**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="2ed9a-288">O **nível de compatibilidade da API** deve ser **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="2ed9a-289">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="2ed9a-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-290">**InternetClient**</span></span>

            ![definir recursos](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="2ed9a-292">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o **SDK do Windows Mixed Reality** foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![definir configurações de XR](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="2ed9a-294">De volta *às configurações de Build* , os *projetos do C# Unity* não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![projetos em escala em c#](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="2ed9a-296">Feche a janela configurações de compilação.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="2ed9a-297">Salve sua cena e projeto (**arquivo** > **salvar cena/arquivo** > **salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-297">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="2ed9a-298">Capítulo 4-configurar a câmera principal</span><span class="sxs-lookup"><span data-stu-id="2ed9a-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ed9a-299">Se você quiser ignorar os componentes de *configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para [baixar esse. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importe-o para seu projeto como um [pacote personalizado](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="2ed9a-300">Isso também conterá as DLLs do próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="2ed9a-301">Após a importação, continue no [capítulo 7](#chapter-7---create-the-azureservices-class).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="2ed9a-302">No *painel hierarquia*, você encontrará um objeto chamado **câmera principal**, esse objeto representa o ponto de vista de "cabeçalho" quando você estiver "dentro" de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="2ed9a-303">Com o painel do Unity na frente de você, selecione a **câmera principal gameobject**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="2ed9a-304">Você observará que o *painel Inspetor* (geralmente localizado à direita, dentro do painel) mostrará os vários componentes desse *gameobject*, com a *transformação* na parte superior, seguida pela *câmera*e alguns outros componentes.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="2ed9a-305">Você precisará redefinir a transformação da câmera principal, para que ela seja posicionada corretamente.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="2ed9a-306">Para fazer isso, selecione o ícone de **engrenagem** ao lado do componente *transformação* da câmera e selecione **Redefinir**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![redefinir transformação](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="2ed9a-308">Em seguida, atualize o componente **transformar** para se parecer com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="2ed9a-309">TRANSFORMAÇÃO-POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="2ed9a-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="2ed9a-310">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-310">**X**</span></span>   | <span data-ttu-id="2ed9a-311">**Iar**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-311">**Y**</span></span>                     | <span data-ttu-id="2ed9a-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-312">**Z**</span></span> |
    | <span data-ttu-id="2ed9a-313">0</span><span class="sxs-lookup"><span data-stu-id="2ed9a-313">0</span></span>       | <span data-ttu-id="2ed9a-314">1</span><span class="sxs-lookup"><span data-stu-id="2ed9a-314">1</span></span>                         | <span data-ttu-id="2ed9a-315">0</span><span class="sxs-lookup"><span data-stu-id="2ed9a-315">0</span></span>     |    

    |       | <span data-ttu-id="2ed9a-316">TRANSFORMAÇÃO-ROTAÇÃO</span><span class="sxs-lookup"><span data-stu-id="2ed9a-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="2ed9a-317">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-317">**X**</span></span> | <span data-ttu-id="2ed9a-318">**Iar**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-318">**Y**</span></span>                | <span data-ttu-id="2ed9a-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-319">**Z**</span></span> |
    | <span data-ttu-id="2ed9a-320">0</span><span class="sxs-lookup"><span data-stu-id="2ed9a-320">0</span></span>     | <span data-ttu-id="2ed9a-321">0</span><span class="sxs-lookup"><span data-stu-id="2ed9a-321">0</span></span>                    | <span data-ttu-id="2ed9a-322">0</span><span class="sxs-lookup"><span data-stu-id="2ed9a-322">0</span></span>     |

    |       | <span data-ttu-id="2ed9a-323">TRANSFORMAR EM ESCALA</span><span class="sxs-lookup"><span data-stu-id="2ed9a-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="2ed9a-324">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-324">**X**</span></span> | <span data-ttu-id="2ed9a-325">**Iar**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-325">**Y**</span></span>             | <span data-ttu-id="2ed9a-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-326">**Z**</span></span> |
    | <span data-ttu-id="2ed9a-327">1</span><span class="sxs-lookup"><span data-stu-id="2ed9a-327">1</span></span>     | <span data-ttu-id="2ed9a-328">1</span><span class="sxs-lookup"><span data-stu-id="2ed9a-328">1</span></span>                 | <span data-ttu-id="2ed9a-329">1</span><span class="sxs-lookup"><span data-stu-id="2ed9a-329">1</span></span>     |

    ![definir transformação de câmera](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="2ed9a-331">Capítulo 5-Configurando a cena do Unity</span><span class="sxs-lookup"><span data-stu-id="2ed9a-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="2ed9a-332">Clique com o botão direito do mouse em uma área vazia do *painel hierarquia*, em **objeto 3D**, adicione um **plano**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![criar novo plano](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="2ed9a-334">Com o objeto **plano** selecionado, altere os seguintes parâmetros no *painel Inspetor*:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="2ed9a-335">TRANSFORMAÇÃO-POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="2ed9a-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="2ed9a-336">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-336">**X**</span></span> | <span data-ttu-id="2ed9a-337">**Iar**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-337">**Y**</span></span>                | <span data-ttu-id="2ed9a-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-338">**Z**</span></span> |
    | <span data-ttu-id="2ed9a-339">0</span><span class="sxs-lookup"><span data-stu-id="2ed9a-339">0</span></span>     | <span data-ttu-id="2ed9a-340">0</span><span class="sxs-lookup"><span data-stu-id="2ed9a-340">0</span></span>                    | <span data-ttu-id="2ed9a-341">추가를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-341">4</span></span>     |

    |       | <span data-ttu-id="2ed9a-342">TRANSFORMAR EM ESCALA</span><span class="sxs-lookup"><span data-stu-id="2ed9a-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="2ed9a-343">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-343">**X**</span></span> | <span data-ttu-id="2ed9a-344">**Iar**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-344">**Y**</span></span>             | <span data-ttu-id="2ed9a-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-345">**Z**</span></span> |
    | <span data-ttu-id="2ed9a-346">10</span><span class="sxs-lookup"><span data-stu-id="2ed9a-346">10</span></span>    | <span data-ttu-id="2ed9a-347">1</span><span class="sxs-lookup"><span data-stu-id="2ed9a-347">1</span></span>                 | <span data-ttu-id="2ed9a-348">10</span><span class="sxs-lookup"><span data-stu-id="2ed9a-348">10</span></span>    |

    ![definir posição e escala do plano](images/AzureLabs-Lab5-32.png)

    ![exibição da cena do plano](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="2ed9a-351">Clique com o botão direito do mouse em uma área vazia do *painel hierarquia*, em **objeto 3D**, adicione um **cubo**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="2ed9a-352">Renomeie o cubo para **GazeButton** (com o cubo selecionado, pressione ' F2 ').</span><span class="sxs-lookup"><span data-stu-id="2ed9a-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="2ed9a-353">Altere os seguintes parâmetros no *painel de Inspetor*:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="2ed9a-354">TRANSFORMAÇÃO-POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="2ed9a-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="2ed9a-355">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-355">**X**</span></span> | <span data-ttu-id="2ed9a-356">**Iar**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-356">**Y**</span></span>                | <span data-ttu-id="2ed9a-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-357">**Z**</span></span> |
        | <span data-ttu-id="2ed9a-358">0</span><span class="sxs-lookup"><span data-stu-id="2ed9a-358">0</span></span>     | <span data-ttu-id="2ed9a-359">3</span><span class="sxs-lookup"><span data-stu-id="2ed9a-359">3</span></span>                    | <span data-ttu-id="2ed9a-360">5</span><span class="sxs-lookup"><span data-stu-id="2ed9a-360">5</span></span>     |


        ![definir transformação do botão olhar](images/AzureLabs-Lab5-34.png)

        ![exibição de cena do botão olhar](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="2ed9a-363">Clique no botão suspenso **marca** e clique em **adicionar marca** para abrir o *painel marcas & camadas*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![Adicionar nova marca](images/AzureLabs-Lab5-36.png)

        ![selecionar mais](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="2ed9a-366">Selecione o botão **+ (mais)** e, no campo *nome da nova marca* , digite **GazeButton**e pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![nomear nova marca](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="2ed9a-368">Clique no objeto **GazeButton** no *painel hierarquia*e, no *painel Inspetor*, atribua a marca **GazeButton** recém-criada.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![atribuir botão olhar à nova marca](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="2ed9a-370">Clique com o botão direito do mouse no objeto **GazeButton** , no *painel hierarquia*e adicione um **gameobject vazio** (que será adicionado como um objeto *filho* ).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="2ed9a-371">Selecione o novo objeto e renomeie-o **ShapeSpawnPoint**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="2ed9a-372">Altere os seguintes parâmetros no *painel de Inspetor*:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="2ed9a-373">TRANSFORMAÇÃO-POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="2ed9a-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="2ed9a-374">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-374">**X**</span></span> |<span data-ttu-id="2ed9a-375">**Iar**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-375">**Y**</span></span>                 | <span data-ttu-id="2ed9a-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-376">**Z**</span></span> |
        | <span data-ttu-id="2ed9a-377">0</span><span class="sxs-lookup"><span data-stu-id="2ed9a-377">0</span></span>     | <span data-ttu-id="2ed9a-378">-1</span><span class="sxs-lookup"><span data-stu-id="2ed9a-378">-1</span></span>                   | <span data-ttu-id="2ed9a-379">0</span><span class="sxs-lookup"><span data-stu-id="2ed9a-379">0</span></span>     |

        ![atualizar transformação de ponto de geração de forma](images/AzureLabs-Lab5-40.png)

        ![exibição de cena de ponto de geração de forma](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="2ed9a-382">Em seguida, você criará um objeto de **texto 3D** para fornecer comentários sobre o status do serviço do Azure.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="2ed9a-383">Clique com o botão direito do mouse em **GazeButton** no painel hierarquia novamente e adicione um **objeto 3D** > objeto de **texto 3D** como um *filho*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object** > **3D Text** object as a *child*.</span></span>

    ![criar novo objeto de texto 3D](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="2ed9a-385">Renomeie o objeto de **texto 3D** para **AzureStatusText**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="2ed9a-386">Altere a transformação do objeto **AzureStatusText** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="2ed9a-387">TRANSFORMAÇÃO-POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="2ed9a-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="2ed9a-388">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-388">**X**</span></span> | <span data-ttu-id="2ed9a-389">**Iar**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-389">**Y**</span></span>                | <span data-ttu-id="2ed9a-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-390">**Z**</span></span> |
    | <span data-ttu-id="2ed9a-391">0</span><span class="sxs-lookup"><span data-stu-id="2ed9a-391">0</span></span>     | <span data-ttu-id="2ed9a-392">0</span><span class="sxs-lookup"><span data-stu-id="2ed9a-392">0</span></span>                    | <span data-ttu-id="2ed9a-393">-0,6</span><span class="sxs-lookup"><span data-stu-id="2ed9a-393">-0.6</span></span>  |

    |       | <span data-ttu-id="2ed9a-394">TRANSFORMAR EM ESCALA</span><span class="sxs-lookup"><span data-stu-id="2ed9a-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="2ed9a-395">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-395">**X**</span></span> | <span data-ttu-id="2ed9a-396">**Iar**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-396">**Y**</span></span>             | <span data-ttu-id="2ed9a-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="2ed9a-397">**Z**</span></span> |
    | <span data-ttu-id="2ed9a-398">0,1</span><span class="sxs-lookup"><span data-stu-id="2ed9a-398">0.1</span></span>   | <span data-ttu-id="2ed9a-399">0,1</span><span class="sxs-lookup"><span data-stu-id="2ed9a-399">0.1</span></span>               | <span data-ttu-id="2ed9a-400">0,1</span><span class="sxs-lookup"><span data-stu-id="2ed9a-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="2ed9a-401">Não se preocupe se parece estar fora do centro, pois isso será corrigido quando o componente de malha de texto abaixo for atualizado.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="2ed9a-402">Altere o componente de **malha de texto** para corresponder ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-402">Change the **Text Mesh** component to match the below:</span></span>

    ![definir componente de malha de texto](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="2ed9a-404">A cor selecionada aqui é a cor hexadecimal: **000000FF**, embora sinta-se à vontade para escolher sua própria, apenas verifique se ela é legível.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="2ed9a-405">A estrutura do painel de hierarquia agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![malha de texto na exibição de cena](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="2ed9a-407">Sua cena agora deve se parecer com esta:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-407">Your scene should now look like this:</span></span>

    ![malha de texto na exibição de cena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="2ed9a-409">Capítulo 6 – importar o armazenamento do Azure para o Unity</span><span class="sxs-lookup"><span data-stu-id="2ed9a-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="2ed9a-410">Você usará o armazenamento do Azure para Unity (que, por sua vez, utiliza o SDK do .net para o Azure).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="2ed9a-411">Você pode ler mais sobre isso no [artigo armazenamento do Azure para Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="2ed9a-412">Atualmente, há um problema conhecido no Unity que exige que os plugins sejam reconfigurados após a importação.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="2ed9a-413">Essas etapas (4-7 nesta seção) não serão mais necessárias depois que o bug for resolvido.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="2ed9a-414">Para importar o SDK para seu próprio projeto, verifique se você baixou o ['. unitypackage ' mais recente do GitHub](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="2ed9a-415">Em seguida, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-415">Then, do the following:</span></span>

1.  <span data-ttu-id="2ed9a-416">Adicione o arquivo **. unitypackage** ao Unity usando a opção de menu **ativos** > **Importar pacote** > **pacote personalizado** .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-416">Add the **.unitypackage** file to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="2ed9a-417">Na caixa **Importar pacote do Unity** que é exibida, você pode selecionar tudo em **armazenamento** > do **plug-in** .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-417">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span> <span data-ttu-id="2ed9a-418">Desmarque todas as outras opções, pois elas não são necessárias para este curso.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![importar para pacote](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="2ed9a-420">Clique no botão **importar** para adicionar os itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="2ed9a-421">Vá para a pasta de *armazenamento* em *plug-ins*, na exibição do projeto e selecione *apenas*os seguintes plugins:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="2ed9a-422">Microsoft. Data. Edm</span><span class="sxs-lookup"><span data-stu-id="2ed9a-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="2ed9a-423">Microsoft. Data. OData</span><span class="sxs-lookup"><span data-stu-id="2ed9a-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="2ed9a-424">Microsoft. WindowsAzure. Storage</span><span class="sxs-lookup"><span data-stu-id="2ed9a-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="2ed9a-425">Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="2ed9a-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="2ed9a-426">System. espacial</span><span class="sxs-lookup"><span data-stu-id="2ed9a-426">System.Spatial</span></span>

        ![desmarcar qualquer plataforma](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="2ed9a-428">Com *esses plugins específicos* selecionados, **desmarque** *qualquer plataforma* e **desmarque** *WSAPlayer* e clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![aplicar DLLs de plataforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="2ed9a-430">Estamos marcando esses plugins específicos para serem usados apenas no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="2ed9a-431">Isso ocorre porque há diferentes versões dos mesmos plug-ins na pasta WSA que serão usados depois que o projeto for exportado do Unity.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="2ed9a-432">Na pasta plug-in de *armazenamento* , selecione somente:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="2ed9a-433">Microsoft. Data. Services. Client</span><span class="sxs-lookup"><span data-stu-id="2ed9a-433">Microsoft.Data.Services.Client</span></span>

        ![definir não processar para DLLs](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="2ed9a-435">Marque a caixa **não processar** em *configurações da plataforma* e clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![aplicar nenhum processamento](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="2ed9a-437">Estamos marcando este plug-in "não processar" porque o assembly do Unity Patcher tem dificuldade para processar esse plug-in.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="2ed9a-438">O plug-in ainda funcionará, embora não seja processado.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="2ed9a-439">Capítulo 7-criar a classe Azureservices</span><span class="sxs-lookup"><span data-stu-id="2ed9a-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="2ed9a-440">A primeira classe que você pretende criar é a classe *azureservices* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="2ed9a-441">A classe *azureservices* será responsável por:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="2ed9a-442">Armazenando as credenciais da conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="2ed9a-443">Chamando sua função Azure App.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="2ed9a-444">O upload e o download do arquivo de dados no armazenamento em nuvem do Azure.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="2ed9a-445">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-445">To create this Class:</span></span>

1.  <span data-ttu-id="2ed9a-446">Clique com o botão direito do mouse na pasta *ativo* , localizada no painel projeto, **crie** > **pasta**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="2ed9a-447">Nomeie a pasta **scripts**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-447">Name the folder **Scripts**.</span></span>

    ![criar nova pasta](images/AzureLabs-Lab5-50.png)

    ![pasta de chamadas-scripts](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="2ed9a-450">Clique duas vezes na pasta recém-criada para abri-la.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="2ed9a-451">Clique com o botão direito do mouse dentro da pasta, **crie** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-451">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="2ed9a-452">Chame o script *azureservices*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="2ed9a-453">Clique duas vezes na nova classe *azureservices* para abri-la com o *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="2ed9a-454">Adicione os seguintes namespaces à parte superior do *azureservices*:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="2ed9a-455">Adicione os seguintes campos de Inspetor dentro da classe *azureservices* :</span><span class="sxs-lookup"><span data-stu-id="2ed9a-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  <span data-ttu-id="2ed9a-456">Em seguida, adicione as seguintes variáveis de membro dentro da classe *azureservices* :</span><span class="sxs-lookup"><span data-stu-id="2ed9a-456">Then add the following member variables inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="2ed9a-457">Substitua os valores do *ponto de extremidade* e da *cadeia de conexão* pelos valores do seu armazenamento do Azure, encontrado no portal do Azure</span><span class="sxs-lookup"><span data-stu-id="2ed9a-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="2ed9a-458">O código para os métodos *ativo ()* e *Iniciar ()* agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="2ed9a-459">Esses métodos serão chamados quando a classe inicializar:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-459">These methods will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="2ed9a-460">Iremos preencher o código para *CallAzureFunctionForNextShape ()* em um [capítulo futuro](#chapter-10---completing-the-azureservices-class).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-azureservices-class).</span></span>

9.  <span data-ttu-id="2ed9a-461">Exclua o método *Update ()* , pois essa classe não o usará.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="2ed9a-462">Salve suas alterações no Visual Studio e, em seguida, retorne ao Unity.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="2ed9a-463">Clique e arraste a classe *azureservices* da pasta scripts para o objeto de câmera principal no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="2ed9a-464">Selecione a câmera principal e, em seguida, pegue o objeto filho **AzureStatusText** sob o objeto **GazeButton** e coloque-o dentro do campo destino de referência do **AzureStatusText** , no *Inspetor*, para fornecer a referência ao  *Script do azureservices* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![atribuir destino de referência de texto de status do Azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="2ed9a-466">Capítulo 8-criar a classe ShapeFactory</span><span class="sxs-lookup"><span data-stu-id="2ed9a-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="2ed9a-467">O próximo script a ser criado é a classe *ShapeFactory* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="2ed9a-468">A função dessa classe é criar uma nova forma, quando solicitado, e manter um histórico das formas criadas em uma *lista de histórico de formas*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="2ed9a-469">Sempre que uma forma é criada, a *lista de histórico de formas* é atualizada na classe *AzureService* e, em seguida, armazenada no *armazenamento do Azure*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="2ed9a-470">Quando o aplicativo for iniciado, se um arquivo armazenado for encontrado no *armazenamento do Azure*, a *lista do histórico de formas* será recuperada e reproduzida, com o objeto de **texto 3D** que fornecerá se a forma gerada é do armazenamento ou de nova.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="2ed9a-471">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-471">To create this class:</span></span>

1.  <span data-ttu-id="2ed9a-472">Vá para a pasta **scripts** que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="2ed9a-473">Clique com o botão direito do mouse dentro da pasta, **crie** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-473">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="2ed9a-474">Chame o script *ShapeFactory*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="2ed9a-475">Clique duas vezes no novo script *ShapeFactory* para abri-lo com o *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="2ed9a-476">Verifique se a classe *ShapeFactory* inclui os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="2ed9a-477">Adicione as variáveis mostradas abaixo à classe *ShapeFactory* e substitua as funções *Start ()* e *ativo ()* pelas seguintes:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  <span data-ttu-id="2ed9a-478">O método *createShape ()* gera as formas primitivas, com base no parâmetro *inteiro* fornecido.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="2ed9a-479">O parâmetro booliano é usado para especificar se a forma criada no momento é do armazenamento ou de nova.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="2ed9a-480">Coloque o seguinte código em sua classe *ShapeFactory* , abaixo dos métodos anteriores:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  <span data-ttu-id="2ed9a-481">Certifique-se de salvar suas alterações no Visual Studio antes de retornar ao Unity.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="2ed9a-482">De volta ao editor do Unity, clique e arraste a classe *ShapeFactory* da pasta **scripts** para o objeto da **câmera principal** no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="2ed9a-483">Com a câmera principal selecionada, você observará que o componente de script *ShapeFactory* não tem a referência de *ponto de geração* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="2ed9a-484">Para corrigi-lo, arraste o objeto **ShapeSpawnPoint** do *painel hierarquia* para o destino de referência do **ponto de geração** .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![definir destino de referência de fábrica de forma](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="2ed9a-486">Capítulo 9-criar a classe olhar</span><span class="sxs-lookup"><span data-stu-id="2ed9a-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="2ed9a-487">O último script que você precisa criar é a classe *olhar* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="2ed9a-488">Essa classe é responsável por criar um **Raycast** que será projetado para a frente da câmera principal, para detectar qual objeto o usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="2ed9a-489">Nesse caso, o Raycast precisará identificar se o usuário está olhando para o objeto **GazeButton** na cena e disparar um comportamento.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="2ed9a-490">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-490">To create this Class:</span></span>

1.  <span data-ttu-id="2ed9a-491">Vá para a pasta **scripts** que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="2ed9a-492">Clique com o botão direito do mouse no painel projeto, **crie** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-492">Right-click in the Project Panel, **Create** > **C# Script**.</span></span> <span data-ttu-id="2ed9a-493">Chame o script *olhar*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="2ed9a-494">Clique duas vezes no novo script *olhar* para abri-lo com o *Visual Studio.*</span><span class="sxs-lookup"><span data-stu-id="2ed9a-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="2ed9a-495">Verifique se o namespace a seguir está incluído na parte superior do script:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="2ed9a-496">Em seguida, adicione as seguintes variáveis dentro da classe *olhar* :</span><span class="sxs-lookup"><span data-stu-id="2ed9a-496">Then add the following variables inside the *Gaze* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> <span data-ttu-id="2ed9a-497">Algumas dessas variáveis poderão ser editadas no *Editor*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="2ed9a-498">Agora, o código para os métodos *ativo ()* e *Iniciar ()* precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="2ed9a-499">Adicione o código a seguir, que criará um objeto cursor no início, juntamente com o método *Update ()* , que executará o método Raycast, juntamente com o local em que o booliano GazeEnabled é alternado:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. <span data-ttu-id="2ed9a-500">Em seguida, adicione o método *UpdateRaycast ()* , que projetará um Raycast e detectará o destino de acesso.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. <span data-ttu-id="2ed9a-501">Por fim, adicione o método *ResetFocusedObject ()* , que irá alternar a cor atual dos objetos GazeButton, indicando se ele está criando uma nova forma ou não.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  <span data-ttu-id="2ed9a-502">Salve suas alterações no Visual Studio antes de retornar ao Unity.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="2ed9a-503">Clique e arraste a classe *olhar* da pasta scripts para o objeto de **câmera principal** no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="2ed9a-504">Capítulo 10 – concluindo a classe Azureservices</span><span class="sxs-lookup"><span data-stu-id="2ed9a-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="2ed9a-505">Com os outros scripts em vigor, agora é possível *concluir* a classe *azureservices* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="2ed9a-506">Isso será obtido por meio de:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="2ed9a-507">Adicionar um novo método chamado *CreateCloudIdentityAsync ()* para configurar as variáveis de autenticação necessárias para se comunicar com o Azure.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="2ed9a-508">Esse método também verificará a existência de um arquivo armazenado anteriormente que contém a lista de formas.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="2ed9a-509">**Se o arquivo for encontrado**, ele desabilitará o usuário *olhar*e disparará a criação de forma, de acordo com o padrão de formas, conforme armazenado no **arquivo de armazenamento do Azure**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="2ed9a-510">O usuário pode ver isso, pois a **malha de texto** fornecerá exibir ' armazenamento ' ou ' novo ', dependendo da origem das formas.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="2ed9a-511">**Se nenhum arquivo for encontrado**, ele permitirá o *olhar*, permitindo que o usuário crie formas ao examinar o objeto **GazeButton** na cena.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  <span data-ttu-id="2ed9a-512">O próximo trecho de código é de dentro do método *Start ()* ; Onde será feita uma chamada para o método *CreateCloudIdentityAsync ()* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="2ed9a-513">Fique à vontade para copiar sobre o método *Start ()* atual, com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  <span data-ttu-id="2ed9a-514">Preencha o código para o método *CallAzureFunctionForNextShape ()* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="2ed9a-515">Você usará o *Azure aplicativo de funções* criado anteriormente para solicitar um índice de forma.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="2ed9a-516">Depois que a nova forma for recebida, esse método enviará a forma para a classe *ShapeFactory* para criar a nova forma na cena.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="2ed9a-517">Use o código abaixo para concluir o corpo de *CallAzureFunctionForNextShape ()* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  <span data-ttu-id="2ed9a-518">Adicione um método para criar uma cadeia de caracteres, concatenando os inteiros armazenados na lista de histórico de formas e salvando-os em seu *arquivo de armazenamento do Azure*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  <span data-ttu-id="2ed9a-519">Adicione um método para recuperar o texto armazenado no arquivo localizado no arquivo de *armazenamento do Azure* e *desserializá* -lo em uma lista.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="2ed9a-520">Quando esse processo for concluído, o método reabilitará o olhar para que o usuário possa adicionar mais formas à cena.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  <span data-ttu-id="2ed9a-521">Salve suas alterações no Visual Studio antes de retornar ao Unity.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="2ed9a-522">Capítulo 11-criar a solução UWP</span><span class="sxs-lookup"><span data-stu-id="2ed9a-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="2ed9a-523">Para iniciar o processo de compilação:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="2ed9a-524">Vá para **arquivo** > **configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-524">Go to **File** > **Build Settings**.</span></span>

    ![compilar o aplicativo](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="2ed9a-526">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-526">Click **Build**.</span></span> <span data-ttu-id="2ed9a-527">O Unity iniciará uma janela *Explorador de arquivos* , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="2ed9a-528">Crie essa pasta agora e nomeie-a como *aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="2ed9a-529">Em seguida, com a pasta de *aplicativo* selecionada, pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="2ed9a-530">O Unity começará a criar seu projeto na pasta do *aplicativo* .</span><span class="sxs-lookup"><span data-stu-id="2ed9a-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="2ed9a-531">Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do *Explorador de arquivos* no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="2ed9a-532">Capítulo 12-implantando seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2ed9a-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="2ed9a-533">Para implantar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-533">To deploy your application:</span></span>

1.  <span data-ttu-id="2ed9a-534">Navegue até a pasta do *aplicativo* que foi criada no [último capítulo](#chapter-11---build-the-uwp-solution).</span><span class="sxs-lookup"><span data-stu-id="2ed9a-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="2ed9a-535">Você verá um arquivo com o nome de seus aplicativos, com a extensão '. sln ', que você deve clicar duas vezes para abri-lo no *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="2ed9a-536">Na **plataforma da solução**, selecione **x86, computador local**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="2ed9a-537">Na **configuração da solução** , selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="2ed9a-538">Para o Microsoft HoloLens, você pode achar mais fácil definir isso como *computador remoto*, para que você não esteja vinculado ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="2ed9a-539">No entanto, também será necessário fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="2ed9a-540">Conheça o **endereço IP** do seu HoloLens, que pode ser encontrado dentro das **configurações** > **rede & Internet** > **Wi-Fi** > **Opções avançadas**; o IPv4 é o endereço que você deve usar.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-540">Know the **IP Address** of your HoloLens, which can be found within the **Settings** > **Network & Internet** > **Wi-Fi** > **Advanced Options**; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="2ed9a-541">Verificar se o modo **de** **desenvolvedor** está ativado; encontrado em **configurações** > **atualização &**  > **de segurança para desenvolvedores**.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-541">Ensure **Developer Mode** is **On**; found in **Settings** > **Update & Security** > **For developers**.</span></span>

    ![implantar solução](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="2ed9a-543">Vá para o menu **Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="2ed9a-544">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado e testado!</span><span class="sxs-lookup"><span data-stu-id="2ed9a-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="2ed9a-545">O Azure Functions e o aplicativo de armazenamento concluídos</span><span class="sxs-lookup"><span data-stu-id="2ed9a-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="2ed9a-546">Parabéns, você criou um aplicativo de realidade misturada que aproveita tanto o Azure Functions quanto os serviços de armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="2ed9a-547">Seu aplicativo poderá desenhar dados armazenados e fornecer uma ação com base nesses dados.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![final do produto final](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="2ed9a-549">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="2ed9a-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="2ed9a-550">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="2ed9a-550">Exercise 1</span></span>

<span data-ttu-id="2ed9a-551">Crie um segundo ponto de geração e registro do qual ponto de geração um objeto foi criado.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="2ed9a-552">Ao carregar o arquivo de dados, reproduza as formas que estão sendo geradas do local em que foram criadas originalmente.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="2ed9a-553">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="2ed9a-553">Exercise 2</span></span>

<span data-ttu-id="2ed9a-554">Crie uma maneira de reiniciar o aplicativo, em vez de ter que reabri-lo a cada vez.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="2ed9a-555">O **carregamento de cenas** é um bom ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="2ed9a-556">Depois de fazer isso, crie uma maneira de limpar a lista armazenada no *armazenamento do Azure*, para que ela possa ser redefinida facilmente do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
