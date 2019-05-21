---
title: MR e Azure 305 - funções e armazenamento
description: Conclua este curso para aprender a implementar o armazenamento do Azure e funções dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, funções, armazenamento, hololens, vr imersivo,
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589232"
---
>[!NOTE]
><span data-ttu-id="fa5a4-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="fa5a4-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="fa5a4-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="fa5a4-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="fa5a4-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="fa5a4-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="fa5a4-110">MR e o Azure 305: Funções e armazenamento</span><span class="sxs-lookup"><span data-stu-id="fa5a4-110">MR and Azure 305: Functions and storage</span></span>

![final do produto-iniciar](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="fa5a4-112">Neste curso, você aprenderá como criar e usar o Azure Functions e armazenar dados com um recurso de armazenamento do Azure, dentro de um aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="fa5a4-113">*O Azure Functions* é um serviço da Microsoft, que permite que os desenvolvedores executem pequenos trechos de código, 'funções', no Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="fa5a4-114">Isso fornece uma maneira para delegar trabalho para a nuvem, em vez de seu aplicativo local, o que pode ter muitos benefícios.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="fa5a4-115">*O Azure Functions* dá suporte a várias linguagens de desenvolvimento, incluindo C\#, F\#, Node. js, Java e PHP.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="fa5a4-116">Para obter mais informações, visite o [artigo do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="fa5a4-117">*O armazenamento do Azure* é um serviço de nuvem da Microsoft, que permite aos desenvolvedores armazenar dados, com o seguro que será altamente disponível, seguro, durável, escalonável e redundante.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="fa5a4-118">Isso significa que a Microsoft lidar com todos os manutenção e os problemas críticos para você.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="fa5a4-119">Para obter mais informações, visite o [artigo do armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="fa5a4-120">Com a conclusão deste curso, você terá um aplicativo de imersivo headset de realidade misturada que serão capaz de fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="fa5a4-121">Permitir que o usuário olhares em torno de uma cena.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="fa5a4-122">Dispare a geração de objetos quando o usuário gazes em um 'button' 3D.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="fa5a4-123">Os objetos gerados serão escolhidos por uma função do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="fa5a4-124">Conforme cada objeto for gerado, o aplicativo irá armazenar o tipo de objeto em um *arquivos do Azure*, localizado na *armazenamento do Azure*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="fa5a4-125">Ao carregar uma segunda vez, o *arquivos do Azure* dados serão recuperados e usados para reproduzir as ações de geração da instância anterior do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="fa5a4-126">Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="fa5a4-127">Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="fa5a4-128">Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="fa5a4-129">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="fa5a4-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="fa5a4-130">Curso</span><span class="sxs-lookup"><span data-stu-id="fa5a4-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="fa5a4-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="fa5a4-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="fa5a4-132"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="fa5a4-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="fa5a4-133">MR e o Azure 305: Funções e armazenamento</span><span class="sxs-lookup"><span data-stu-id="fa5a4-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="fa5a4-134">✔️</span><span class="sxs-lookup"><span data-stu-id="fa5a4-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="fa5a4-135">✔️</span><span class="sxs-lookup"><span data-stu-id="fa5a4-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="fa5a4-136">Enquanto este curso se concentra primariamente em fones de ouvido Windows Mixed Reality de imersão (VR), você também pode aplicar o que você aprenderá neste curso para o Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="fa5a4-137">Como acompanhar o curso, você verá notas quaisquer alterações que talvez seja necessário empregar para dar suporte ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fa5a4-138">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fa5a4-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="fa5a4-139">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="fa5a4-140">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="fa5a4-141">Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .</span><span class="sxs-lookup"><span data-stu-id="fa5a4-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="fa5a4-142">Recomendamos que o hardware e software para este curso a seguir:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="fa5a4-143">Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)</span><span class="sxs-lookup"><span data-stu-id="fa5a4-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="fa5a4-144">Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="fa5a4-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="fa5a4-145">O SDK mais recente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="fa5a4-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="fa5a4-146">2017.4 do Unity</span><span class="sxs-lookup"><span data-stu-id="fa5a4-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="fa5a4-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fa5a4-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="fa5a4-148">Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="fa5a4-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="fa5a4-149">Uma assinatura para uma conta do Azure para a criação de recursos do Azure</span><span class="sxs-lookup"><span data-stu-id="fa5a4-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="fa5a4-150">Acesso à Internet para recuperação de dados e de instalação do Azure</span><span class="sxs-lookup"><span data-stu-id="fa5a4-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="fa5a4-151">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="fa5a4-151">Before you start</span></span>

<span data-ttu-id="fa5a4-152">Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="fa5a4-153">Capítulo 1 - Portal do Azure</span><span class="sxs-lookup"><span data-stu-id="fa5a4-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="fa5a4-154">Para usar o **serviço de armazenamento do Azure**, você precisará criar e configurar um **conta de armazenamento** no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="fa5a4-155">Faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="fa5a4-156">Se você ainda não tiver uma conta do Azure, você precisará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="fa5a4-157">Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="fa5a4-158">Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure *conta de armazenamento*e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![pesquisa de armazenamento do Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="fa5a4-160">A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="fa5a4-161">A nova página fornecerá uma descrição do *conta de armazenamento do Azure* service.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="fa5a4-162">Na parte inferior esquerda desse prompt, selecione a **criar** botão para criar uma associação com este serviço.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Criar serviço](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="fa5a4-164">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="fa5a4-165">Inserir uma *nome* para sua conta, lembre-se que este campo aceita apenas números e letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="fa5a4-166">Para *modelo de implantação*, selecione **Gerenciador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="fa5a4-167">Para *tipo de conta*, selecione **(uso geral v1) de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="fa5a4-168">Determinar a *local* para seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="fa5a4-169">O local seria o ideal é que na região em que o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="fa5a4-170">Alguns ativos do Azure estão disponíveis somente em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="fa5a4-171">Para *replicação* selecionar **leitura-acesso-com redundância geográfica (RA-GRS) de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="fa5a4-172">Para *desempenho*, selecione **padrão**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="fa5a4-173">Deixe *transferência segura obrigatória* como **desabilitado**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="fa5a4-174">Selecione uma *assinatura*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="fa5a4-175">Escolha uma *grupo de recursos* ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="fa5a4-176">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="fa5a4-177">É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="fa5a4-178">Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="fa5a4-179">Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="fa5a4-180">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-180">Select **Create**.</span></span>

        ![informações do serviço de entrada](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="fa5a4-182">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="fa5a4-183">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nova notificação no portal do azure](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="fa5a4-185">Clique em notificações para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-185">Click on the notifications to explore your new Service instance.</span></span>

    ![Ir para o recurso](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="fa5a4-187">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="fa5a4-188">Você será levado para a nova *conta de armazenamento* instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![teclas de acesso](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="fa5a4-190">Clique em *chaves de acesso*para revelar os pontos de extremidade para esse serviço de nuvem.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="fa5a4-191">Use *bloco de notas* ou semelhante, a cópia de uma de suas chaves para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="fa5a4-192">Além disso, observe o *cadeia de caracteres de Conexão* de valor, pois ele será usado o *AzureServices* classe, que você criará posteriormente.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![Copie a cadeia de caracteres de conexão](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="fa5a4-194">Capítulo 2 - configurar uma função do Azure</span><span class="sxs-lookup"><span data-stu-id="fa5a4-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="fa5a4-195">Agora você vai escrever um **Azure** **função** no serviço do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="fa5a4-196">Você pode usar um **Azure Function** fazer quase tudo o que você faria com uma função clássica no seu código, a diferença é que essa função pode ser acessada por qualquer aplicativo que tenha credenciais para acessar sua conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="fa5a4-197">Para criar uma função do Azure:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="fa5a4-198">De seu *Portal do Azure*, clique em **New** no canto superior esquerdo de canto e procure *aplicativo de funções*e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![Criar aplicativo de funções](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="fa5a4-200">A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="fa5a4-201">A nova página fornecerá uma descrição do *aplicativo de funções do Azure* service.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="fa5a4-202">Na parte inferior esquerda desse prompt, selecione a **criar** botão para criar uma associação com este serviço.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![informações do aplicativo de função](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="fa5a4-204">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="fa5a4-205">Fornecer um *nome do aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-205">Provide an *App name*.</span></span> <span data-ttu-id="fa5a4-206">Apenas letras e números podem ser usados aqui (maiuscula ou minúscula é permitido).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="fa5a4-207">Selecione sua preferência *assinatura*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="fa5a4-208">Escolha uma *grupo de recursos* ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="fa5a4-209">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="fa5a4-210">É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="fa5a4-211">Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="fa5a4-212">Para este exercício, selecione *Windows* como o escolhido **SO**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="fa5a4-213">Selecione *plano de consumo* para o **plano de hospedagem**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="fa5a4-214">Determinar a *local* para seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="fa5a4-215">O local seria o ideal é que na região em que o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="fa5a4-216">Alguns ativos do Azure estão disponíveis somente em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="fa5a4-217">Para otimizar o desempenho, selecione a mesma região da conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="fa5a4-218">Para *armazenamento*, selecione **usar existente**, e, em seguida, usando o menu suspenso, localize seu armazenamento criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="fa5a4-219">Deixe *Application Insights* desativado para este exercício.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-219">Leave *Application Insights* off for this exercise.</span></span>

        ![detalhes do aplicativo de função de entrada](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="fa5a4-221">Clique no botão **Criar**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="fa5a4-222">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="fa5a4-223">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nova notificação no portal do azure](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="fa5a4-225">Clique em notificações para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![Vá para o aplicativo de funções de recurso](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="fa5a4-227">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="fa5a4-228">Você será levado para a nova *aplicativo de funções* instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="fa5a4-229">No *aplicativo de funções* dashboard, passe o mouse sobre *funções*encontrado dentro do painel à esquerda e, em seguida, clique no **+ (adição)** símbolo.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![Criar uma nova função](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="fa5a4-231">Na próxima página, verifique se **Webhook + API** está selecionada e para *escolher um idioma* selecionar **CSharp**, pois esse será o idioma usado para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="fa5a4-232">Por fim, clique o **criar esta função** botão.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-232">Lastly, click the **Create this function** button.</span></span>

    ![Selecione csharp de gancho da web](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="fa5a4-234">Você será levado para o código de página (Run. CSx), caso contrário, clique na função recém-criada na lista de funções dentro do painel à esquerda.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![Abra a nova função](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="fa5a4-236">Copie o código a seguir para sua função.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-236">Copy the following code into your function.</span></span> <span data-ttu-id="fa5a4-237">Essa função simplesmente retornará um inteiro aleatório entre 0 e 2 quando chamado.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="fa5a4-238">Não se preocupe com o código existente, fique à vontade colar na parte superior dele.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

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

13. <span data-ttu-id="fa5a4-239">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-239">Select **Save**.</span></span>

14. <span data-ttu-id="fa5a4-240">O resultado deve ser semelhante a imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="fa5a4-241">Clique em **obter a URL da função** e anote o *ponto de extremidade* exibido.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="fa5a4-242">Você precisará inseri-lo para o *AzureServices* classe que você criará posteriormente no curso.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![obter ponto de extremidade de função](images/AzureLabs-Lab5-16.png)

    ![obter ponto de extremidade de função](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="fa5a4-245">Capítulo 3 - configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="fa5a4-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="fa5a4-246">A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="fa5a4-247">Configurar e testar o headset de realidade misturada envolvente.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="fa5a4-248">Você irá **não** exigem controladores de movimento para este curso.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="fa5a4-249">Se você precisar dar suporte a configurar o fone de ouvido imersivo, faça [visite a realidade misturada configurar artigo](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="fa5a4-250">Abrir o Unity e clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-250">Open Unity and click **New**.</span></span>

    ![Criar novo projeto do unity](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="fa5a4-252">Agora, você precisará fornecer um nome de projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="fa5a4-253">Inserir **MR_Azure_Functions**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="fa5a4-254">Verifique se o tipo de projeto é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="fa5a4-255">Defina as *local* para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="fa5a4-256">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-256">Then, click **Create project**.</span></span>

    ![Dê um nome de novo projeto do unity](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="fa5a4-258">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="fa5a4-259">Vá para **edite* > *preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-259">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="fa5a4-260">Alteração **Editor de Script externo** à **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="fa5a4-261">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-261">Close the **Preferences** window.</span></span>

    ![conjunto de visual studio como editor de scripts](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="fa5a4-263">Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma **plataforma Universal do Windows**, clicando no **alternar plataforma** botão.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-263">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Alternar plataforma para a uwp](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="fa5a4-265">Vá para **arquivo > configurações de Build** e certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-265">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="fa5a4-266">**Dispositivo de destino** é definido como **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="fa5a4-267">Para o Microsoft HoloLens, defina **dispositivo de destino** à *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="fa5a4-268">**Tipo de compilação** é definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="fa5a4-269">**SDK** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="fa5a4-270">**Versão do Visual Studio** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="fa5a4-271">**Compilar e executar** é definido como **Máquina Local**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="fa5a4-272">Salve a cena e adicioná-lo para a compilação.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="fa5a4-273">Fazer isso selecionando **cenas abra Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="fa5a4-274">Salvamento janela será exibida.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-274">A save window will appear.</span></span>

            ![Adicionar cenas abertas](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="fa5a4-276">Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Criar pasta cenas](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="fa5a4-278">Abra seu recém-criado **cenas** pasta e, em seguida, no **nome do arquivo:** campo de texto, digite **FunctionsScene**, em seguida, pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![Salve a cena de funções](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="fa5a4-280">O restante de configurações, em **configurações de Build**, deverá ser deixado como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![Salve a cena de funções](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="fa5a4-282">No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![configurações do Player no Inspetor](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="fa5a4-284">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="fa5a4-285">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="fa5a4-286">**Versão de tempo de execução de scripts** deve ser **Experimental** (equivalente ao .NET 4.6), que irá disparar uma necessidade de reiniciar o Editor.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="fa5a4-287">**Script de back-end** deve ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="fa5a4-288">**Nível de compatibilidade de API** deve ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="fa5a4-289">Dentro de **configurações de publicação** guia, em **recursos**, verifique:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="fa5a4-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-290">**InternetClient**</span></span>

            ![conjunto de recursos](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="fa5a4-292">Mais para baixo no painel, no **XR configurações** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **realidade mista do Windows SDK** é adicionado.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Definir configurações de XR](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="fa5a4-294">Volta *configurações de Build* *Unity C# projetos* não fica acinzentado; marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![projetos c# de escala](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="fa5a4-296">Feche a janela de configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="fa5a4-297">Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="fa5a4-298">Capítulo 4 - câmera principal de instalação</span><span class="sxs-lookup"><span data-stu-id="fa5a4-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fa5a4-299">Se você quiser ignorar a *configurar o Unity* componentes deste curso e continuar diretamente no código, fique à vontade para [baixar esse unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importe-o para seu projeto como um [personalizado Pacote](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="fa5a4-300">Isso também irá conter as DLLs do próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="fa5a4-301">Após a importação, continuar a partir [capítulo 7](#chapter-7---create-the-azureservices-class).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="fa5a4-302">No *painel de hierarquia*, você encontrará um objeto chamado **câmera principal**, este objeto representa o ponto de vista de "head" quando estiver "dentro" de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="fa5a4-303">Com o painel do Unity na sua frente, selecione a **GameObject de câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="fa5a4-304">Você observará que o *painel Inspetor* (geralmente encontrado para a direita, no painel) mostrará os vários componentes do que *GameObject*, com *transformar* na parte superior, seguido por *câmera*e alguns outros componentes.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="fa5a4-305">Você precisará redefinir a transformação da câmera principal, para que ele está posicionado corretamente.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="fa5a4-306">Para fazer isso, selecione a **engrenagem** ícone ao lado da câmera *transformar* componente e selecione **redefinir**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![Redefinir transformação](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="fa5a4-308">Em seguida, atualize o **transformar** componente para se parecer com:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="fa5a4-309">TRANSFORMAÇÃO - POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="fa5a4-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="fa5a4-310">**X**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-310">**X**</span></span>   | <span data-ttu-id="fa5a4-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-311">**Y**</span></span>                     | <span data-ttu-id="fa5a4-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-312">**Z**</span></span> |
    | <span data-ttu-id="fa5a4-313">0</span><span class="sxs-lookup"><span data-stu-id="fa5a4-313">0</span></span>       | <span data-ttu-id="fa5a4-314">1</span><span class="sxs-lookup"><span data-stu-id="fa5a4-314">1</span></span>                         | <span data-ttu-id="fa5a4-315">0</span><span class="sxs-lookup"><span data-stu-id="fa5a4-315">0</span></span>     |    

    |       | <span data-ttu-id="fa5a4-316">TRANSFORMAÇÃO - ROTAÇÃO</span><span class="sxs-lookup"><span data-stu-id="fa5a4-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="fa5a4-317">**X**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-317">**X**</span></span> | <span data-ttu-id="fa5a4-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-318">**Y**</span></span>                | <span data-ttu-id="fa5a4-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-319">**Z**</span></span> |
    | <span data-ttu-id="fa5a4-320">0</span><span class="sxs-lookup"><span data-stu-id="fa5a4-320">0</span></span>     | <span data-ttu-id="fa5a4-321">0</span><span class="sxs-lookup"><span data-stu-id="fa5a4-321">0</span></span>                    | <span data-ttu-id="fa5a4-322">0</span><span class="sxs-lookup"><span data-stu-id="fa5a4-322">0</span></span>     |

    |       | <span data-ttu-id="fa5a4-323">TRANSFORMAÇÃO - ESCALA</span><span class="sxs-lookup"><span data-stu-id="fa5a4-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="fa5a4-324">**X**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-324">**X**</span></span> | <span data-ttu-id="fa5a4-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-325">**Y**</span></span>             | <span data-ttu-id="fa5a4-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-326">**Z**</span></span> |
    | <span data-ttu-id="fa5a4-327">1</span><span class="sxs-lookup"><span data-stu-id="fa5a4-327">1</span></span>     | <span data-ttu-id="fa5a4-328">1</span><span class="sxs-lookup"><span data-stu-id="fa5a4-328">1</span></span>                 | <span data-ttu-id="fa5a4-329">1</span><span class="sxs-lookup"><span data-stu-id="fa5a4-329">1</span></span>     |

    ![conjunto de transformação de câmera](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="fa5a4-331">Capítulo 5 – configurar a cena do Unity</span><span class="sxs-lookup"><span data-stu-id="fa5a4-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="fa5a4-332">Clique com botão direito em uma área vazia do *painel de hierarquia*, em **objeto 3D**, adicionar um **plano**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![Criar novo plano](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="fa5a4-334">Com o **plano** do objeto selecionado, altere os parâmetros a seguir na *painel Inspetor*:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="fa5a4-335">TRANSFORMAÇÃO - POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="fa5a4-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="fa5a4-336">**X**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-336">**X**</span></span> | <span data-ttu-id="fa5a4-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-337">**Y**</span></span>                | <span data-ttu-id="fa5a4-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-338">**Z**</span></span> |
    | <span data-ttu-id="fa5a4-339">0</span><span class="sxs-lookup"><span data-stu-id="fa5a4-339">0</span></span>     | <span data-ttu-id="fa5a4-340">0</span><span class="sxs-lookup"><span data-stu-id="fa5a4-340">0</span></span>                    | <span data-ttu-id="fa5a4-341">4</span><span class="sxs-lookup"><span data-stu-id="fa5a4-341">4</span></span>     |

    |       | <span data-ttu-id="fa5a4-342">TRANSFORMAÇÃO - ESCALA</span><span class="sxs-lookup"><span data-stu-id="fa5a4-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="fa5a4-343">**X**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-343">**X**</span></span> | <span data-ttu-id="fa5a4-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-344">**Y**</span></span>             | <span data-ttu-id="fa5a4-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-345">**Z**</span></span> |
    | <span data-ttu-id="fa5a4-346">10</span><span class="sxs-lookup"><span data-stu-id="fa5a4-346">10</span></span>    | <span data-ttu-id="fa5a4-347">1</span><span class="sxs-lookup"><span data-stu-id="fa5a4-347">1</span></span>                 | <span data-ttu-id="fa5a4-348">10</span><span class="sxs-lookup"><span data-stu-id="fa5a4-348">10</span></span>    |

    ![definir posição de plano e escala](images/AzureLabs-Lab5-32.png)

    ![exibição de cena do plano](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="fa5a4-351">Clique com botão direito em uma área vazia do *painel de hierarquia*, em **objeto 3D**, adicione um **cubo**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="fa5a4-352">Renomeie o cubo **GazeButton** (com o cubo selecionado, pressione 'F2').</span><span class="sxs-lookup"><span data-stu-id="fa5a4-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="fa5a4-353">Alterar os seguintes parâmetros na *painel Inspetor*:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="fa5a4-354">TRANSFORMAÇÃO - POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="fa5a4-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="fa5a4-355">**X**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-355">**X**</span></span> | <span data-ttu-id="fa5a4-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-356">**Y**</span></span>                | <span data-ttu-id="fa5a4-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-357">**Z**</span></span> |
        | <span data-ttu-id="fa5a4-358">0</span><span class="sxs-lookup"><span data-stu-id="fa5a4-358">0</span></span>     | <span data-ttu-id="fa5a4-359">3</span><span class="sxs-lookup"><span data-stu-id="fa5a4-359">3</span></span>                    | <span data-ttu-id="fa5a4-360">5</span><span class="sxs-lookup"><span data-stu-id="fa5a4-360">5</span></span>     |


        ![transformação de botão de olhar conjunto](images/AzureLabs-Lab5-34.png)

        ![Mantenha o foco de exibição de cena de botão](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="fa5a4-363">Clique no **marca** botão suspenso e clique em **Adicionar marca** para abrir o *painel de camadas de marcas de &*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![Adicionar nova marca](images/AzureLabs-Lab5-36.png)

        ![Select plus](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="fa5a4-366">Selecione o **+ (adição)** botão e, nas *novo nome de marca* , insira **GazeButton**e pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![nova marca de nome](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="fa5a4-368">Clique no **GazeButton** do objeto na *painel de hierarquia*e, na *painel Inspetor*, atribuir recém-criado **GazeButton** marca.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![botão de olhar de atribuir a nova marca](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="fa5a4-370">Com o botão direito no **GazeButton** objeto, o *painel de hierarquia*e adicione um **GameObject vazio** (que será adicionado como um *filho* objeto).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="fa5a4-371">Selecione o novo objeto e renomeá-lo **ShapeSpawnPoint**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="fa5a4-372">Alterar os seguintes parâmetros na *painel Inspetor*:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="fa5a4-373">TRANSFORMAÇÃO - POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="fa5a4-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="fa5a4-374">**X**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-374">**X**</span></span> |<span data-ttu-id="fa5a4-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-375">**Y**</span></span>                 | <span data-ttu-id="fa5a4-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-376">**Z**</span></span> |
        | <span data-ttu-id="fa5a4-377">0</span><span class="sxs-lookup"><span data-stu-id="fa5a4-377">0</span></span>     | <span data-ttu-id="fa5a4-378">-1</span><span class="sxs-lookup"><span data-stu-id="fa5a4-378">-1</span></span>                   | <span data-ttu-id="fa5a4-379">0</span><span class="sxs-lookup"><span data-stu-id="fa5a4-379">0</span></span>     |

        ![transformação de ponto de geração de forma de atualização](images/AzureLabs-Lab5-40.png)

        ![exibição de cena de ponto de geração de forma](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="fa5a4-382">Em seguida você irá criar uma **texto 3D** objeto para fornecer comentários sobre o status do serviço do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="fa5a4-383">Clique com botão direito do **GazeButton** na hierarquia de painel novamente e adicione um **objeto 3D > texto 3D** do objeto como um *filho*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object > 3D Text** object as a *child*.</span></span>

    ![criar um novo objeto de texto 3D](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="fa5a4-385">Renomeie o **texto 3D** objeto **AzureStatusText**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="fa5a4-386">Alterar o **AzureStatusText** transformação do objeto da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="fa5a4-387">TRANSFORMAÇÃO - POSIÇÃO</span><span class="sxs-lookup"><span data-stu-id="fa5a4-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="fa5a4-388">**X**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-388">**X**</span></span> | <span data-ttu-id="fa5a4-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-389">**Y**</span></span>                | <span data-ttu-id="fa5a4-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-390">**Z**</span></span> |
    | <span data-ttu-id="fa5a4-391">0</span><span class="sxs-lookup"><span data-stu-id="fa5a4-391">0</span></span>     | <span data-ttu-id="fa5a4-392">0</span><span class="sxs-lookup"><span data-stu-id="fa5a4-392">0</span></span>                    | <span data-ttu-id="fa5a4-393">-0.6</span><span class="sxs-lookup"><span data-stu-id="fa5a4-393">-0.6</span></span>  |

    |       | <span data-ttu-id="fa5a4-394">TRANSFORMAÇÃO - ESCALA</span><span class="sxs-lookup"><span data-stu-id="fa5a4-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="fa5a4-395">**X**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-395">**X**</span></span> | <span data-ttu-id="fa5a4-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-396">**Y**</span></span>             | <span data-ttu-id="fa5a4-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-397">**Z**</span></span> |
    | <span data-ttu-id="fa5a4-398">0.1</span><span class="sxs-lookup"><span data-stu-id="fa5a4-398">0.1</span></span>   | <span data-ttu-id="fa5a4-399">0.1</span><span class="sxs-lookup"><span data-stu-id="fa5a4-399">0.1</span></span>               | <span data-ttu-id="fa5a4-400">0.1</span><span class="sxs-lookup"><span data-stu-id="fa5a4-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="fa5a4-401">Não se preocupe se ele aparenta estar desativado centre, pois isso será corrigido quando o abaixo do texto de malha componente é atualizado.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="fa5a4-402">Alterar o **texto de malha** componente para corresponder a abaixo:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-402">Change the **Text Mesh** component to match the below:</span></span>

    ![componente de malha do conjunto de texto](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="fa5a4-404">A cor selecionada aqui é a cor hexadecimal: **000000FF**, no entanto, fique à vontade para escolher seus próprios, apenas verifique se ele está legível.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="fa5a4-405">A estrutura de hierarquia painel agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![texto de malha no modo de exibição de cena](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="fa5a4-407">Agora, sua cena deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-407">Your scene should now look like this:</span></span>

    ![texto de malha no modo de exibição de cena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="fa5a4-409">Capítulos 6 - importar do armazenamento do Azure para Unity</span><span class="sxs-lookup"><span data-stu-id="fa5a4-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="fa5a4-410">Você usará o armazenamento do Azure para Unity (que por si só aproveita o .net SDK do Azure).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="fa5a4-411">Você pode ler mais sobre isso na [armazenamento do Azure para o artigo do Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="fa5a4-412">Atualmente, há um problema conhecido no Unity que requer o plug-ins para ser reconfigurado após a importação.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="fa5a4-413">Estas etapas (4 a 7 desta seção) não será necessárias depois que o bug foi resolvido.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="fa5a4-414">Para importar o SDK no seu próprio projeto, verifique se você baixou a versão mais recente [unitypackage do GitHub](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="fa5a4-415">Em seguida, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-415">Then, do the following:</span></span>

1.  <span data-ttu-id="fa5a4-416">Adicione a **unitypackage** arquivo para o Unity, usando o **ativos > Importar pacote > pacote personalizado** opção de menu.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-416">Add the **.unitypackage** file to Unity by using the **Assets > Import Package > Custom Package** menu option.</span></span>

2.  <span data-ttu-id="fa5a4-417">No **Importar pacote do Unity** caixa que é exibida, você pode selecionar tudo sob \**plug-in* > \*de armazenamento\*\*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-417">In the **Import Unity Package** box that pops up, you can select everything under \**Plugin* > \*Storage\*\*.</span></span> <span data-ttu-id="fa5a4-418">Desmarque todas as outras, como ele não é necessário para este curso.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Importar pacote](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="fa5a4-420">Clique o **importação** botão para adicionar itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="fa5a4-421">Vá para o *armazenamento* pasta sob *plug-ins*, na exibição do projeto e selecione os seguintes plug-ins *apenas*:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="fa5a4-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="fa5a4-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="fa5a4-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="fa5a4-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="fa5a4-424">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="fa5a4-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="fa5a4-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="fa5a4-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="fa5a4-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="fa5a4-426">System.Spatial</span></span>

        ![desmarque qualquer plataforma](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="fa5a4-428">Com o *esses plug-ins específicos* selecionado, **desmarque** *Any Platform* e **desmarque** *WSAPlayer* em seguida, clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![Aplicar as dlls de plataforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="fa5a4-430">Nós estamos marcando esses plug-ins específicos para ser usado apenas no Editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="fa5a4-431">Isso ocorre porque há versões diferentes dos mesmos plug-ins na pasta WSA que será usado depois que o projeto é exportado do Unity.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="fa5a4-432">No *armazenamento* pasta Plug-in, selecione apenas:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="fa5a4-433">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="fa5a4-433">Microsoft.Data.Services.Client</span></span>

        ![conjunto não processar para dlls](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="fa5a4-435">Verifique as **processo não** caixa sob *configurações de plataforma* e clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![não aplicar nenhum processamento](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="fa5a4-437">Nós estamos marcando esse plug-in "Não processar" porque o patcher de assembly do Unity tem dificuldade para processar esse plug-in.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="fa5a4-438">O plug-in ainda funcionará, mesmo que ele não será processado.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="fa5a4-439">Capítulo 7 - criar a classe AzureServices</span><span class="sxs-lookup"><span data-stu-id="fa5a4-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="fa5a4-440">É a primeira classe que você pretende criar o *AzureServices* classe.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="fa5a4-441">O *AzureServices* classe será responsável por:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="fa5a4-442">Armazenar credenciais de conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="fa5a4-443">Chamando a função de aplicativo do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="fa5a4-444">O upload e download de arquivo de dados em seu armazenamento em nuvem do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="fa5a4-445">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-445">To create this Class:</span></span>

1.  <span data-ttu-id="fa5a4-446">Clique com botão direito no *Asset* pasta, localizada no painel de projeto, **criar > pasta**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create > Folder**.</span></span> <span data-ttu-id="fa5a4-447">Nomeie a pasta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-447">Name the folder **Scripts**.</span></span>

    ![Criar nova pasta](images/AzureLabs-Lab5-50.png)

    ![pasta chamada - scripts](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="fa5a4-450">Clique duas vezes na pasta recém-criada, para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="fa5a4-451">Clique com botão direito dentro da pasta **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-451">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="fa5a4-452">Chame o script *AzureServices*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="fa5a4-453">Clique duas vezes na nova *AzureServices* classe para abri-lo com *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="fa5a4-454">Adicione os seguintes namespaces na parte superior do *AzureServices*:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="fa5a4-455">Adicione os seguintes campos de Inspetor de dentro de *AzureServices* classe:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

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

7.  <span data-ttu-id="fa5a4-456">Em seguida, adicione as seguintes variáveis de membro dentro de *AzureServices* classe:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-456">Then add the following member variables inside the *AzureServices* class:</span></span>

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
    > <span data-ttu-id="fa5a4-457">Verifique se você substituir a *ponto de extremidade* e *cadeia de caracteres de conexão* valores com os valores do armazenamento do Azure, encontradas no Portal do Azure</span><span class="sxs-lookup"><span data-stu-id="fa5a4-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="fa5a4-458">Código para o *Awake()* e *Start ()* métodos agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="fa5a4-459">Esses métodos serão chamados quando inicializa a classe:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-459">These methods will be called when the class initializes:</span></span>

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
    > <span data-ttu-id="fa5a4-460">Podemos preencherá o código para *CallAzureFunctionForNextShape()* em um [capítulo futuras](#chapter-10---completing-the-AzureServices-class).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-AzureServices-class).</span></span>

9.  <span data-ttu-id="fa5a4-461">Excluir o *Update ()* método uma vez que essa classe não irá usá-lo.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="fa5a4-462">Salve suas alterações no Visual Studio e, em seguida, retornar para o Unity.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="fa5a4-463">Clique e arraste a *AzureServices* classe da pasta de Scripts para o objeto de câmera principal na *painel de hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="fa5a4-464">Selecione a câmera principal, em seguida, pegue o **AzureStatusText** objeto filho abaixo do **GazeButton** de objeto e coloque-o no **AzureStatusText** destino da referência campo, o *Inspector*, para fornecer a referência para o *AzureServices* script.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![atribuir o destino de referência de texto de status do azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="fa5a4-466">Capítulo 8 - criar a classe ShapeFactory</span><span class="sxs-lookup"><span data-stu-id="fa5a4-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="fa5a4-467">É o próximo script para criar, o *ShapeFactory* classe.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="fa5a4-468">A função dessa classe é criar uma nova forma, quando solicitado e manter um histórico das formas criado em uma *lista de histórico de forma*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="fa5a4-469">Sempre que uma forma é criada, o *lista do histórico de forma* é atualizado na *AzureService* classe e, em seguida, armazenadas no seu *armazenamento do Azure*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="fa5a4-470">Quando o aplicativo for iniciado, se um arquivo armazenado for encontrado no seu *armazenamento do Azure*, o *lista do histórico de forma* é recuperado e repetidos, com o **texto 3D** fornecendo de objeto Se a forma gerada é do armazenamento ou novo.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="fa5a4-471">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-471">To create this class:</span></span>

1.  <span data-ttu-id="fa5a4-472">Vá para o **Scripts** pasta que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="fa5a4-473">Clique com botão direito dentro da pasta **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-473">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="fa5a4-474">Chame o script *ShapeFactory*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="fa5a4-475">Clique duas vezes na nova *ShapeFactory* script para abri-lo com *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="fa5a4-476">Verifique se o *ShapeFactory* classe inclui os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="fa5a4-477">Adicione as variáveis mostradas abaixo para o *ShapeFactory* classe e substituir o *Start ()* e *Awake()* funções com aquelas abaixo:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

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

6.  <span data-ttu-id="fa5a4-478">O *createShape ()* método gera as formas primitivas, com base em fornecido *inteiro* parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="fa5a4-479">O parâmetro booliano é usado para especificar se a forma atualmente criada do armazenamento, ou novo.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="fa5a4-480">Coloque o seguinte código no seu *ShapeFactory* classe abaixo dos métodos anteriores:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

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

7.  <span data-ttu-id="fa5a4-481">Certifique-se de salvar suas alterações no Visual Studio antes de retornar para o Unity.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="fa5a4-482">Novamente no Editor do Unity, clique e arraste a *ShapeFactory* classe a **Scripts** pasta para o **câmera principal** do objeto no *hierarquia painel*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="fa5a4-483">Com a câmera principal selecionado, você vai notar a *ShapeFactory* componente de script está faltando a *Spawn ponto* referência.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="fa5a4-484">Para corrigi-lo, arraste a **ShapeSpawnPoint** de objeto a *painel de hierarquia* para o **Spawn ponto** destino da referência.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![destino da referência do conjunto de forma factory](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="fa5a4-486">Capítulo 9 - criar a classe de olhar</span><span class="sxs-lookup"><span data-stu-id="fa5a4-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="fa5a4-487">É o último script que você precisa criar o *olhares* classe.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="fa5a4-488">Essa classe é responsável por criar uma **Raycast** que será projetado para a frente da câmera principal, para detectar qual objeto de usuário está observando.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="fa5a4-489">Nesse caso, o Raycast precisará identificar se o usuário está observando o **GazeButton** do objeto na cena e disparar um comportamento.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="fa5a4-490">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-490">To create this Class:</span></span>

1.  <span data-ttu-id="fa5a4-491">Vá para o **Scripts** pasta que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="fa5a4-492">Clique com botão direito no painel de projeto, **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-492">Right-click in the Project Panel, **Create > C# Script**.</span></span> <span data-ttu-id="fa5a4-493">Chame o script *olhares*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="fa5a4-494">Clique duas vezes na nova *olhares* script para abri-lo com *Visual Studio.*</span><span class="sxs-lookup"><span data-stu-id="fa5a4-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="fa5a4-495">Certifique-se de que o namespace a seguir está incluído na parte superior do script:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="fa5a4-496">Em seguida, adicione as seguintes variáveis dentro do *olhares* classe:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-496">Then add the following variables inside the *Gaze* class:</span></span>

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
> <span data-ttu-id="fa5a4-497">Algumas dessas variáveis poderão ser editados na *Editor*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="fa5a4-498">Código para o *Awake()* e *Start ()* métodos agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="fa5a4-499">Adicione o código a seguir, que criará um objeto de cursor no início, juntamente com o *Update ()* método, que executará o método Raycast, além de ser onde o booliano GazeEnabled é alternada:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

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

8. <span data-ttu-id="fa5a4-500">Em seguida adicione a *UpdateRaycast()* método, que será um Raycast do projeto e detectar o destino de ocorrência.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

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

9. <span data-ttu-id="fa5a4-501">Por fim, adicione a *ResetFocusedObject()* método, que irá ativar/desativar a GazeButton objetos cor atual, que indica se ele está criando uma nova forma ou não.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

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

10.  <span data-ttu-id="fa5a4-502">Salve suas alterações no Visual Studio antes de retornar para o Unity.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="fa5a4-503">Clique e arraste a *olhares* classe a partir da pasta de Scripts para o **câmera principal** objeto o *painel de hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="fa5a4-504">Capítulo 10 - Concluindo a classe AzureServices</span><span class="sxs-lookup"><span data-stu-id="fa5a4-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="fa5a4-505">Com os outros scripts em vigor, é possível *concluída* as *AzureServices* classe.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="fa5a4-506">Isso será feito por meio de:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="fa5a4-507">Adicionando um novo método chamado *CreateCloudIdentityAsync()* para configurar as variáveis de autenticação necessárias para se comunicar com o Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="fa5a4-508">Esse método também verificará a existência de um arquivo armazenado anteriormente que contém a lista de forma.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="fa5a4-509">**Se o arquivo for encontrado**, ele desativará o usuário *olhares*e disparar a criação de forma, acordo com o padrão de formas, conforme armazenado no **arquivo de armazenamento do Azure**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="fa5a4-510">O usuário pode ver isso, como o **texto de malha** fornecerá a exibição 'Armazenamento' ou 'New', dependendo da origem de formas.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="fa5a4-511">**Se nenhum arquivo for encontrado**, ele permitirá que o *olhares*, permitindo que o usuário criar formas ao examinar o **GazeButton** objeto na cena.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

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

2.  <span data-ttu-id="fa5a4-512">O próximo trecho de código é de dentro de *Start ()* método; no qual você será feita uma chamada para o *CreateCloudIdentityAsync()* método.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="fa5a4-513">Fique à vontade copiar sobre as atuais *Start ()* método, com a abaixo:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

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

3.  <span data-ttu-id="fa5a4-514">Preencher o código para o método *CallAzureFunctionForNextShape()*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="fa5a4-515">Você usará o criado anteriormente *aplicativo de funções do Azure* para solicitar um índice de forma.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="fa5a4-516">Depois que a nova forma é recebida, este método enviará a forma para o *ShapeFactory* classe para criar a nova forma na cena.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="fa5a4-517">Use o código a seguir para concluir o corpo da *CallAzureFunctionForNextShape()*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

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

4.  <span data-ttu-id="fa5a4-518">Adicione um método para criar uma cadeia de caracteres concatenando os inteiros armazenados na lista de histórico de forma e salvá-los em seu *arquivos de armazenamento do Azure*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

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

5.  <span data-ttu-id="fa5a4-519">Adicione um método para recuperar o texto armazenado no arquivo localizado em sua *arquivos de armazenamento do Azure* e *desserializar* -lo em uma lista.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="fa5a4-520">Quando esse processo é concluído, o método reabilita o olhar para que o usuário pode adicionar mais formas para a cena.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

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

7.  <span data-ttu-id="fa5a4-521">Salve suas alterações no Visual Studio antes de retornar para o Unity.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="fa5a4-522">Capítulo 11 - criar a solução UWP</span><span class="sxs-lookup"><span data-stu-id="fa5a4-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="fa5a4-523">Para iniciar o processo de compilação:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="fa5a4-524">Vá para **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-524">Go to **File > Build Settings**.</span></span>

    ![Compilar o aplicativo](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="fa5a4-526">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-526">Click **Build**.</span></span> <span data-ttu-id="fa5a4-527">Unity iniciará uma *Explorador de arquivos* janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="fa5a4-528">Criar pasta agora e nomeie- *aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="fa5a4-529">Em seguida, com o *App* pasta selecionada, pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="fa5a4-530">Unity começará a compilar seu projeto para o *aplicativo* pasta.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="fa5a4-531">Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um *Explorador de arquivos* janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="fa5a4-532">Capítulo 12 - implantar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="fa5a4-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="fa5a4-533">Para implantar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-533">To deploy your application:</span></span>

1.  <span data-ttu-id="fa5a4-534">Navegue até a *App* pasta que foi criada na [último capítulo](#chapter-11---build-the-uwp-solution).</span><span class="sxs-lookup"><span data-stu-id="fa5a4-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="fa5a4-535">Você verá um arquivo com seu nome de aplicativos, com a extensão '. sln', que você deve clicar duas vezes, portanto, para abri-lo dentro *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="fa5a4-536">No **plataforma da solução**, selecione **x86, computador Local**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="fa5a4-537">No **configuração da solução** selecionar **depurar**.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="fa5a4-538">Para o Microsoft HoloLens, talvez você ache mais fácil de definir isso como *máquina remota*, de modo que você não estiver vinculado ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="fa5a4-539">No entanto, você precisará também fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fa5a4-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="fa5a4-540">Saber a **endereço IP** de seu HoloLens, que podem ser encontrado dentro a *Configurações > rede e Internet > Wi-Fi > Opções avançadas de*; o IPv4 é o endereço que você deve usar.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-540">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="fa5a4-541">Certifique-se **modo de desenvolvedor** é **na**; encontrado na *Configurações > atualização e segurança > para os desenvolvedores*.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-541">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Implantar solução](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="fa5a4-543">Vá para o **construir** menu e clique em **implantar solução** para carregar o aplicativo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="fa5a4-544">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado e testado!</span><span class="sxs-lookup"><span data-stu-id="fa5a4-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="fa5a4-545">O Azure Functions e o aplicativo de armazenamento concluído</span><span class="sxs-lookup"><span data-stu-id="fa5a4-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="fa5a4-546">Parabéns, você criou um aplicativo de realidade mista que aproveita os serviços do Azure Functions e o armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="fa5a4-547">Seu aplicativo será capaz de desenhar em dados armazenados e fornecer uma ação com base nesses dados.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![final do produto-end](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="fa5a4-549">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="fa5a4-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="fa5a4-550">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="fa5a4-550">Exercise 1</span></span>

<span data-ttu-id="fa5a4-551">Crie uma segunda geração ponto e do registro que gerar um objeto foi criado a partir do ponto.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="fa5a4-552">Quando você carrega o arquivo de dados, repetir as formas que estão sendo geradas do local em que eles foram originalmente criados.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="fa5a4-553">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="fa5a4-553">Exercise 2</span></span>

<span data-ttu-id="fa5a4-554">Crie uma forma para reiniciar o aplicativo, em vez de precisar abra novamente cada vez.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="fa5a4-555">**Carregar cenas** é um bom lugar para começar.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="fa5a4-556">Depois de fazer isso, crie uma maneira de limpar a lista armazenada no *armazenamento do Azure*, de modo que podem ser redefinida facilmente do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
