---
title: MR e Azure 308 - notificações entre dispositivos
description: Conclua este curso para aprender a implementar os Hubs de notificação do Azure, Azure Functions e o armazenamento do Azure e tabelas dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, notificação, funções, tabelas, os hubs de notificação, hololens, vr de imersão,
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694602"
---
>[!NOTE]
><span data-ttu-id="59cfa-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="59cfa-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="59cfa-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="59cfa-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="59cfa-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="59cfa-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="59cfa-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="59cfa-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="59cfa-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="59cfa-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="59cfa-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="59cfa-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="59cfa-110">MR e o Azure 308: Notificações de vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="59cfa-110">MR and Azure 308: Cross-device notifications</span></span>

![final do produto-iniciar](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="59cfa-112">Neste curso, você aprenderá como adicionar recursos de Hubs de notificação para um aplicativo de realidade misturada usando os Hubs de notificação do Azure, tabelas do Azure e Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="59cfa-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="59cfa-113">**Os Hubs de notificação do Azure** é um serviço da Microsoft, que permite aos desenvolvedores enviar notificações por push direcionadas e personalizadas para qualquer plataforma, tudo é alimentada dentro da nuvem.</span><span class="sxs-lookup"><span data-stu-id="59cfa-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="59cfa-114">Isso pode efetivamente permitem que os desenvolvedores para se comunicar com os usuários finais, ou até mesmo se comunicar entre vários aplicativos, dependendo do cenário.</span><span class="sxs-lookup"><span data-stu-id="59cfa-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="59cfa-115">Para obter mais informações, visite o **os Hubs de notificação do Azure** [página](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span><span class="sxs-lookup"><span data-stu-id="59cfa-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="59cfa-116">**O Azure Functions** é um serviço da Microsoft, que permite que os desenvolvedores executem pequenos trechos de código, 'funções', no Azure.</span><span class="sxs-lookup"><span data-stu-id="59cfa-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="59cfa-117">Isso fornece uma maneira para delegar trabalho para a nuvem, em vez de seu aplicativo local, o que pode ter muitos benefícios.</span><span class="sxs-lookup"><span data-stu-id="59cfa-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="59cfa-118">**O Azure Functions** dá suporte a várias linguagens de desenvolvimento, incluindo C\#, F\#, Node. js, Java e PHP.</span><span class="sxs-lookup"><span data-stu-id="59cfa-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="59cfa-119">Para obter mais informações, visite o **Azure Functions** [página](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="59cfa-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="59cfa-120">**As tabelas do Azure** é um serviço de nuvem da Microsoft, que permite aos desenvolvedores armazenar dados estruturados não-SQL na nuvem, tornando-o facilmente acessível em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="59cfa-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="59cfa-121">O serviço apresenta um design sem esquema, permitindo a evolução das tabelas conforme necessário e, portanto, é muito flexível.</span><span class="sxs-lookup"><span data-stu-id="59cfa-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="59cfa-122">Para obter mais informações, visite o **tabelas do Azure** [página](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="59cfa-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="59cfa-123">Com a conclusão deste curso, você terá um aplicativo de imersão headset de realidade misturada e um aplicativo de Desktop PC, será possível fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="59cfa-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="59cfa-124">O aplicativo de Desktop PC permitirá que o usuário mover um objeto no espaço 2D (X e Y), usando o mouse.</span><span class="sxs-lookup"><span data-stu-id="59cfa-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="59cfa-125">A movimentação de objetos dentro do aplicativo de computador será enviada para a nuvem usando JSON, que será na forma de uma cadeia de caracteres, que contém uma ID de objeto, tipo e transformar informações (coordenadas X e Y).</span><span class="sxs-lookup"><span data-stu-id="59cfa-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="59cfa-126">O aplicativo de realidade misturada, que tem uma cena idêntica para o aplicativo da área de trabalho, receberá notificações sobre a movimentação de objeto do serviço de Hubs de notificação (que acabou de ser atualizado pelo aplicativo de Desktop PC).</span><span class="sxs-lookup"><span data-stu-id="59cfa-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="59cfa-127">Ao receber uma notificação, que irá conter a ID de objeto, tipo e informações de transformação, o aplicativo de realidade misturada aplicará as informações recebidas à própria cena.</span><span class="sxs-lookup"><span data-stu-id="59cfa-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="59cfa-128">Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="59cfa-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="59cfa-129">Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="59cfa-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="59cfa-130">Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="59cfa-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="59cfa-131">Este curso é um tutorial independente, o que não envolvem diretamente quaisquer outros laboratórios de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="59cfa-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="59cfa-132">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="59cfa-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="59cfa-133">Curso</span><span class="sxs-lookup"><span data-stu-id="59cfa-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="59cfa-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="59cfa-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="59cfa-135"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="59cfa-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="59cfa-136">MR e o Azure 308: Notificações de vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="59cfa-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="59cfa-137">✔️</span><span class="sxs-lookup"><span data-stu-id="59cfa-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="59cfa-138">✔️</span><span class="sxs-lookup"><span data-stu-id="59cfa-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="59cfa-139">Enquanto este curso se concentra primariamente em fones de ouvido Windows Mixed Reality de imersão (VR), você também pode aplicar o que você aprenderá neste curso para o Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="59cfa-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="59cfa-140">Como acompanhar o curso, você verá notas quaisquer alterações que talvez seja necessário empregar para dar suporte ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="59cfa-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="59cfa-141">Ao usar o HoloLens, você pode perceber algum eco durante a captura de voz.</span><span class="sxs-lookup"><span data-stu-id="59cfa-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59cfa-142">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="59cfa-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="59cfa-143">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="59cfa-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="59cfa-144">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="59cfa-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="59cfa-145">Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .</span><span class="sxs-lookup"><span data-stu-id="59cfa-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="59cfa-146">Recomendamos que o hardware e software para este curso a seguir:</span><span class="sxs-lookup"><span data-stu-id="59cfa-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="59cfa-147">Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)</span><span class="sxs-lookup"><span data-stu-id="59cfa-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="59cfa-148">Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="59cfa-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="59cfa-149">O SDK mais recente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="59cfa-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="59cfa-150">2017.4 do Unity</span><span class="sxs-lookup"><span data-stu-id="59cfa-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="59cfa-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="59cfa-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="59cfa-152">Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="59cfa-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="59cfa-153">Acesso à Internet para a configuração do Azure e acessar os Hubs de notificação</span><span class="sxs-lookup"><span data-stu-id="59cfa-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="59cfa-154">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="59cfa-154">Before you start</span></span>

- <span data-ttu-id="59cfa-155">Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="59cfa-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="59cfa-156">Você deve ser o proprietário do seu Portal do desenvolvedor Microsoft e o Portal de registro de aplicativo, caso contrário, você não terá permissão para acessar o aplicativo no [capítulo 2](#chapter-2---retrieve-your-new-apps-credentials).</span><span class="sxs-lookup"><span data-stu-id="59cfa-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="59cfa-157">Capítulo 1 - criar um aplicativo no Portal do desenvolvedor Microsoft</span><span class="sxs-lookup"><span data-stu-id="59cfa-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="59cfa-158">Para usar o **os Hubs de notificação do Azure** serviço, você precisará criar um aplicativo no Portal do desenvolvedor da Microsoft, como seu aplicativo precisará ser registrado, para que ele possa enviar e receber notificações.</span><span class="sxs-lookup"><span data-stu-id="59cfa-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="59cfa-159">Faça logon na [Portal do desenvolvedor Microsoft](https://developer.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="59cfa-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="59cfa-160">Você precisará fazer logon no seu Account da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="59cfa-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="59cfa-161">No painel, clique em **criar um novo aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-161">From the Dashboard, click **Create a new app**.</span></span>

    ![Criar um aplicativo](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="59cfa-163">Um pop-up será exibida, no qual você precisa reservar um nome para seu novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="59cfa-164">Na caixa de texto, insira um nome apropriado; Se o nome escolhido estiver disponível, um tique aparecerá à direita da caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="59cfa-165">Quando você tiver um nome disponível inseridos, clique o **reservar nome do produto** botão na parte inferior esquerda do popup.</span><span class="sxs-lookup"><span data-stu-id="59cfa-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![um nome inversa](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="59cfa-167">Com o aplicativo agora criado, você está pronto para passar para o próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="59cfa-168">Capítulo 2 - recuperar suas novas credenciais de aplicativos</span><span class="sxs-lookup"><span data-stu-id="59cfa-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="59cfa-169">Faça logon no Portal de registro de aplicativo, onde seu novo aplicativo será listado e recuperar as credenciais que serão usadas para a instalação do **serviço de Hubs de notificação** dentro a **Portal do Azure**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="59cfa-170">Navegue até a [Portal de registro de aplicativo](http://apps.dev.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="59cfa-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![portal de registro de aplicativo](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="59cfa-172">Você precisará usar sua Account da Microsoft para fazer logon.</span><span class="sxs-lookup"><span data-stu-id="59cfa-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="59cfa-173">Isso **devem** ser Account da Microsoft que você usou anteriormente na [capítulo](#chapter-1---create-an-application-on-the-microsoft-developer-portal), com o portal do desenvolvedor do Windows Store.</span><span class="sxs-lookup"><span data-stu-id="59cfa-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="59cfa-174">Você encontrará o seu aplicativo sob o **meus aplicativos** seção.</span><span class="sxs-lookup"><span data-stu-id="59cfa-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="59cfa-175">Depois de encontrá-lo, clique nele e você será levado para uma nova página que tem o aplicativo do nome do sinal de adição **registro**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![seu aplicativo recentemente registrado](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="59cfa-177">Role para baixo a página de registro para encontrar seu **segredos do aplicativo** seção e a **SID do pacote** para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="59cfa-178">Copiar ambos para uso com a configuração de **serviço de Hubs de notificação do Azure** no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![Segredos do aplicativo](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="59cfa-180">Capítulo 3 - Portal do programa de instalação do Azure: criar serviço de Hubs de notificação</span><span class="sxs-lookup"><span data-stu-id="59cfa-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="59cfa-181">Com suas credenciais de aplicativos recuperados, você precisará ir para o Portal do Azure, onde você irá criar um serviço de Hubs de notificação do Azure.</span><span class="sxs-lookup"><span data-stu-id="59cfa-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="59cfa-182">Faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="59cfa-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="59cfa-183">Se você ainda não tiver uma conta do Azure, você precisará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="59cfa-184">Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="59cfa-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="59cfa-185">Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure **Hub de notificação**e clique em ***Enter***.</span><span class="sxs-lookup"><span data-stu-id="59cfa-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![Pesquisar hub de notificação](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="59cfa-187">A palavra ***New*** foram substituídos por **criar um recurso**, nos portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="59cfa-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="59cfa-188">A nova página fornecerá uma descrição do *os Hubs de notificação* service.</span><span class="sxs-lookup"><span data-stu-id="59cfa-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="59cfa-189">Na parte inferior esquerda desse prompt, selecione a **criar** botão para criar uma associação com este serviço.</span><span class="sxs-lookup"><span data-stu-id="59cfa-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Criar instância de hubs de notificação](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="59cfa-191">Depois de clicar em ***criar***:</span><span class="sxs-lookup"><span data-stu-id="59cfa-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="59cfa-192">Insira o nome desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="59cfa-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="59cfa-193">Fornecer um **namespace** que você poderá associar a esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="59cfa-194">Selecione um **local.**</span><span class="sxs-lookup"><span data-stu-id="59cfa-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="59cfa-195">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="59cfa-196">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="59cfa-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="59cfa-197">É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="59cfa-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="59cfa-198">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="59cfa-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="59cfa-199">Selecione uma opção apropriada **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="59cfa-200">Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="59cfa-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="59cfa-201">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-201">Select **Create**.</span></span>

        ![Preencha os detalhes do serviço](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="59cfa-203">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="59cfa-204">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="59cfa-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notificação](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="59cfa-206">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="59cfa-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="59cfa-207">Você será levado para a nova **Hub de notificação** instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="59cfa-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![Ir para o recurso](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="59cfa-209">Na página de visão geral, metade de página, clique em **Windows (WNS).**</span><span class="sxs-lookup"><span data-stu-id="59cfa-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="59cfa-210">O painel à direita será alterado para mostrar dois campos de texto, que exigem sua **SID do pacote** e **chave de segurança**, do aplicativo que você configurou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="59cfa-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![criado recentemente o serviço de hubs](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="59cfa-212">Depois de copiar os detalhes nos campos corretos, clique em **salvar**, e você receberá uma notificação quando o Hub de notificação foi atualizado com êxito.</span><span class="sxs-lookup"><span data-stu-id="59cfa-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![Anote os detalhes de segurança](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="59cfa-214">Capítulo 4 - Portal do programa de instalação do Azure: criar serviço de tabela</span><span class="sxs-lookup"><span data-stu-id="59cfa-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="59cfa-215">Depois de criar sua instância do serviço de Hubs de notificação, navegue de volta para seu Portal do Azure, onde você irá criar um serviço de tabelas do Azure, criando um recurso de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="59cfa-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="59cfa-216">Se ainda não estiver conectado, faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="59cfa-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="59cfa-217">Depois de conectado, clique em **New** no canto superior esquerdo de canto e procure **conta de armazenamento**e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="59cfa-218">A palavra ***New*** foram substituídos por **criar um recurso**, nos portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="59cfa-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="59cfa-219">Selecione **conta de armazenamento - blob, arquivo, tabela, fila** na lista.</span><span class="sxs-lookup"><span data-stu-id="59cfa-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Procure a conta de armazenamento](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="59cfa-221">A nova página fornecerá uma descrição do **conta de armazenamento** service.</span><span class="sxs-lookup"><span data-stu-id="59cfa-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="59cfa-222">Na parte inferior esquerda desse prompt, selecione a **criar** botão para criar uma instância desse serviço.</span><span class="sxs-lookup"><span data-stu-id="59cfa-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![Criar instância de armazenamento](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="59cfa-224">Depois de clicar em **criar**, um painel será exibido:</span><span class="sxs-lookup"><span data-stu-id="59cfa-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="59cfa-225">Inserir sua desejada **nome** para esta instância de serviço (deve estar todo em letras maiusculas).</span><span class="sxs-lookup"><span data-stu-id="59cfa-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="59cfa-226">Para **modelo de implantação**, clique em **Gerenciador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="59cfa-227">Para **tipo de conta**, usando o menu suspenso, selecione **(uso geral v1) de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="59cfa-228">Selecione uma opção apropriada **local**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="59cfa-229">Para o **replicação** menu suspenso, selecione **leitura-acesso-com redundância geográfica (RA-GRS) de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="59cfa-230">Para **desempenho**, clique em **padrão**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="59cfa-231">Dentro de **transferência segura obrigatória** seção, selecione **desabilitado**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="59cfa-232">Dos **assinatura** menu suspenso, selecione a assinatura apropriada.</span><span class="sxs-lookup"><span data-stu-id="59cfa-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="59cfa-233">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="59cfa-234">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="59cfa-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="59cfa-235">É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="59cfa-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="59cfa-236">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="59cfa-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="59cfa-237">Deixe **redes virtuais** como **desabilitado** quando se trata de uma opção para você.</span><span class="sxs-lookup"><span data-stu-id="59cfa-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="59cfa-238">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-238">Click **Create**.</span></span>

        ![Preencha os detalhes de armazenamento](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="59cfa-240">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="59cfa-241">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="59cfa-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="59cfa-242">Clique em notificações para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="59cfa-242">Click on the notifications to explore your new Service instance.</span></span>

    ![nova notificação de armazenamento](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="59cfa-244">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="59cfa-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="59cfa-245">Você será levado para a nova página de visão geral de instância de serviço de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="59cfa-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![Ir para o recurso](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="59cfa-247">Na página de visão geral, para o lado direito, clique em **tabelas**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="59cfa-248">O painel à direita será alterado para mostrar o **do serviço tabela** informações, no qual você precisa adicionar uma nova tabela.</span><span class="sxs-lookup"><span data-stu-id="59cfa-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="59cfa-249">Faça isso clicando o **+** **tabela** botão no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![abrir tabelas](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="59cfa-251">Uma nova página será mostrada, no qual você precisa inserir uma **nome da tabela**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="59cfa-252">Esse é o nome que você usará para se referir aos dados em seu aplicativo em capítulos.</span><span class="sxs-lookup"><span data-stu-id="59cfa-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="59cfa-253">Insira um nome apropriado e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-253">Insert an appropriate name and click **OK**.</span></span>

    ![Criar nova tabela](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="59cfa-255">Quando a nova tabela tiver sido criada, você poderá vê-lo dentro de **do serviço tabela** página (na parte inferior).</span><span class="sxs-lookup"><span data-stu-id="59cfa-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![nova tabela criada](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="59cfa-257">Capítulo 5 – Concluindo a tabela do Azure no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="59cfa-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="59cfa-258">Agora que sua **do serviço tabela** conta de armazenamento tiver sido configurado, é hora de adicionar dados a ele, que será usada para armazenar e recuperar informações.</span><span class="sxs-lookup"><span data-stu-id="59cfa-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="59cfa-259">A edição de suas tabelas pode ser feita por meio **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="59cfa-260">Abra **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="59cfa-261">No menu, clique em **modo de exibição** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![Abra o cloud explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="59cfa-263">O **Cloud Explorer** será aberto como um item encaixado (seja paciente, pois o carregamento pode levar tempo).</span><span class="sxs-lookup"><span data-stu-id="59cfa-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="59cfa-264">Se a assinatura que você usou para criar sua *contas de armazenamento* não estiver visível, certifique-se de que você tenha:</span><span class="sxs-lookup"><span data-stu-id="59cfa-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="59cfa-265">Conectado à mesma conta que você usou para o Portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="59cfa-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="59cfa-266">Selecionado sua assinatura na página de gerenciamento de conta (talvez você precise aplicar um filtro de suas configurações de conta):</span><span class="sxs-lookup"><span data-stu-id="59cfa-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![localizar a assinatura](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="59cfa-268">Os serviços de nuvem do Azure serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="59cfa-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="59cfa-269">Encontre **contas de armazenamento** e clique na seta à esquerda do que para expandir suas contas.</span><span class="sxs-lookup"><span data-stu-id="59cfa-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Abra as contas de armazenamento](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="59cfa-271">Quando expandida, seu recém-criado **conta de armazenamento** devem estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="59cfa-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="59cfa-272">Clique na seta à esquerda de seu armazenamento e, em seguida, depois que é expandido, encontrar **tabelas** e clique na seta ao lado de que, para revelar as **tabela** você criou no último capítulo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="59cfa-273">Clique duas vezes em sua **tabela**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-273">Double click your **Table**.</span></span>

    ![Abra a tabela de objetos de cena](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="59cfa-275">A tabela será aberta no centro da janela do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59cfa-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="59cfa-276">Clique no ícone de tabela com o **+** (mais) nele.</span><span class="sxs-lookup"><span data-stu-id="59cfa-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![Adicionar nova tabela](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="59cfa-278">Uma janela será exibida solicitando que você *Adicionar entidade*.</span><span class="sxs-lookup"><span data-stu-id="59cfa-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="59cfa-279">Você criará três entidades no total, cada um com várias propriedades.</span><span class="sxs-lookup"><span data-stu-id="59cfa-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="59cfa-280">Você observará que *PartitionKey* e *RowKey* já são fornecidas, pois eles são usados pela tabela para localizar os dados.</span><span class="sxs-lookup"><span data-stu-id="59cfa-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![chave de partição e de linha](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="59cfa-282">Atualização a *valor* da **PartitionKey** e **RowKey** da seguinte maneira (Lembre-se de fazer isso para cada propriedade de linha que você adiciona, porém incrementar a RowKey cada vez):</span><span class="sxs-lookup"><span data-stu-id="59cfa-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![Adicione os valores corretos](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="59cfa-284">Clique em **adicionar propriedade** para adicionar linhas extras de dados.</span><span class="sxs-lookup"><span data-stu-id="59cfa-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="59cfa-285">Fazer com sua primeira tabela vazia que correspondam a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="59cfa-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="59cfa-286">Clique em **Okey** quando tiver terminado.</span><span class="sxs-lookup"><span data-stu-id="59cfa-286">Click **OK** when you are finished.</span></span>

    ![Clique em okey quando concluído](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="59cfa-288">Certifique-se de que você alterou o **tipo** da **X**, **Y**, e **Z**, entradas a serem **Double**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="59cfa-289">Você observará que sua tabela agora tem uma linha de dados.</span><span class="sxs-lookup"><span data-stu-id="59cfa-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="59cfa-290">Clique o **+** (ícone novamente para adicionar outra entidade mais).</span><span class="sxs-lookup"><span data-stu-id="59cfa-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![primeira linha](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="59cfa-292">Criar uma propriedade adicional e, em seguida, defina os valores da nova entidade para corresponderem às mostradas abaixo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![Adicionar o cubo](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="59cfa-294">Repita a última etapa para adicionar outra entidade.</span><span class="sxs-lookup"><span data-stu-id="59cfa-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="59cfa-295">Defina os valores para essa entidade ao mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-295">Set the values for this entity to those shown below.</span></span>

    ![Adicionar o cilindro](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="59cfa-297">Sua tabela agora deve ser semelhante a mostrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-297">Your table should now look like the one below.</span></span>

    ![tabela completa](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="59cfa-299">Você concluiu este capítulo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-299">You have completed this Chapter.</span></span> <span data-ttu-id="59cfa-300">Certifique-se de salvar.</span><span class="sxs-lookup"><span data-stu-id="59cfa-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="59cfa-301">Capítulo 6 - criar um aplicativo de funções do Azure</span><span class="sxs-lookup"><span data-stu-id="59cfa-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="59cfa-302">Criar um aplicativo de função do Azure, que será chamado pelo aplicativo da área de trabalho para atualizar o **tabela** de serviço e enviar uma notificação por meio de **Hub de notificação**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="59cfa-303">Primeiro, você precisa criar um arquivo que permitirá que sua função do Azure carregar as bibliotecas que necessárias.</span><span class="sxs-lookup"><span data-stu-id="59cfa-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="59cfa-304">Abra **bloco de notas** (pressione a tecla Windows e o bloco de notas do tipo).</span><span class="sxs-lookup"><span data-stu-id="59cfa-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![Abra o bloco de notas](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="59cfa-306">Com o bloco de notas aberto, insira a estrutura JSON abaixo nela.</span><span class="sxs-lookup"><span data-stu-id="59cfa-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="59cfa-307">Depois de ter feito isso, salve-o na área de trabalho como **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="59cfa-308">É importante que a nomenclatura está correta: Certifique-se de que ele faz **não tiver uma. txt** extensão de arquivo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="59cfa-309">Esse arquivo define as bibliotecas de que sua função usará, se você tiver usado o NuGet parecerá familiar.</span><span class="sxs-lookup"><span data-stu-id="59cfa-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="59cfa-310">Faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="59cfa-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="59cfa-311">Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure **aplicativo de funções**, pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![Procure o aplicativo de funções](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="59cfa-313">A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="59cfa-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="59cfa-314">A nova página fornecerá uma descrição do **aplicativo de funções** service.</span><span class="sxs-lookup"><span data-stu-id="59cfa-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="59cfa-315">Na parte inferior esquerda desse prompt, selecione a **criar** botão para criar uma associação com este serviço.</span><span class="sxs-lookup"><span data-stu-id="59cfa-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![instância do aplicativo de função](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="59cfa-317">Depois de clicar em **criar**, preencha o seguinte:</span><span class="sxs-lookup"><span data-stu-id="59cfa-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="59cfa-318">Para **nome do aplicativo**, inserir seu nome desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="59cfa-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="59cfa-319">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="59cfa-320">Selecione o tipo de preço apropriado para você, se esta for a primeira hora de criar uma **serviço de aplicativo de função**, uma camada gratuita deve estar disponível para você.</span><span class="sxs-lookup"><span data-stu-id="59cfa-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="59cfa-321">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="59cfa-322">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="59cfa-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="59cfa-323">É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="59cfa-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="59cfa-324">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="59cfa-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="59cfa-325">Para **SO**, clique em Windows, já que é a plataforma destinada.</span><span class="sxs-lookup"><span data-stu-id="59cfa-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="59cfa-326">Selecione uma **plano de hospedagem** (Este tutorial está usando uma **plano de consumo**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="59cfa-327">Selecione uma **local** **(escolha o mesmo local como o armazenamento que você criou na etapa anterior)**</span><span class="sxs-lookup"><span data-stu-id="59cfa-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="59cfa-328">Para o **armazenamento** seção, **você deve selecionar o serviço de armazenamento que você criou na etapa anterior**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="59cfa-329">Você não precisará *Application Insights* neste aplicativo, fique à vontade para deixá-lo **Off**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="59cfa-330">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-330">Click **Create**.</span></span>

        ![Criar nova instância](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="59cfa-332">Depois de clicar em **criar** você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="59cfa-333">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="59cfa-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nova notificação](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="59cfa-335">Clique em notificações para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="59cfa-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="59cfa-336">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="59cfa-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Ir para o recurso](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="59cfa-338">Clique o **+** (mais) ícone próximo ao *funções*, ao *criar novo*.</span><span class="sxs-lookup"><span data-stu-id="59cfa-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![Adicionar nova função](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="59cfa-340">No painel central, o **função** será exibida a janela de criação.</span><span class="sxs-lookup"><span data-stu-id="59cfa-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="59cfa-341">Ignorar as informações na metade superior do painel e, em seguida, clique em **função personalizada**, que está localizado na parte inferior (na área azul, como mostrado abaixo).</span><span class="sxs-lookup"><span data-stu-id="59cfa-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![função personalizada](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="59cfa-343">A nova página dentro da janela mostrará os vários tipos de função.</span><span class="sxs-lookup"><span data-stu-id="59cfa-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="59cfa-344">Role para baixo para exibir os tipos de roxos e clique em **HTTP PUT** elemento.</span><span class="sxs-lookup"><span data-stu-id="59cfa-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![Coloque o link de http](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="59cfa-346">Você talvez tenha que rolar ainda mais a para baixo a página (e essa imagem pode não exatamente a mesma aparência, se as atualizações do Portal do Azure terá ocorrido), no entanto, você estiver procurando por um elemento chamado *HTTP PUT*.</span><span class="sxs-lookup"><span data-stu-id="59cfa-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="59cfa-347">O **HTTP PUT** janela será exibida, onde você precisa configurar a função (consulte abaixo para imagem).</span><span class="sxs-lookup"><span data-stu-id="59cfa-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="59cfa-348">Para **linguagem** usando o menu suspenso, selecione C\#.</span><span class="sxs-lookup"><span data-stu-id="59cfa-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="59cfa-349">Para **nome,** um nome apropriado de entrada.</span><span class="sxs-lookup"><span data-stu-id="59cfa-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="59cfa-350">No **nível de autenticação** menu suspenso, selecione **função**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="59cfa-351">Para o **nome da tabela** seção, você precisa usar o nome exato que você usou para criar sua **tabela** serviço anteriormente (incluindo a letra da mesma forma).</span><span class="sxs-lookup"><span data-stu-id="59cfa-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="59cfa-352">Dentro de **conexão de conta de armazenamento** seção, use o menu suspenso e selecione sua conta de armazenamento a partir daí.</span><span class="sxs-lookup"><span data-stu-id="59cfa-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="59cfa-353">Se ainda não estiver lá, clique o **New** hiperlink junto com o título da seção, para mostrar outro painel, em que sua conta de armazenamento deve estar listada.</span><span class="sxs-lookup"><span data-stu-id="59cfa-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![novo armazenamento](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="59cfa-355">Clique em **criar** e você receberá uma notificação de que suas configurações foram atualizadas com êxito.</span><span class="sxs-lookup"><span data-stu-id="59cfa-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![Criar função](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="59cfa-357">Depois de clicar em **criar**, você será redirecionado para o editor de função.</span><span class="sxs-lookup"><span data-stu-id="59cfa-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![atualizar o código de função](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="59cfa-359">Insira o seguinte código no editor de função (substituindo o código na função):</span><span class="sxs-lookup"><span data-stu-id="59cfa-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="59cfa-360">Usando as bibliotecas incluídas, a função recebe o nome e o local do objeto que foi movido na cena Unity (como um C# objeto, chamado **UnityGameObject**).</span><span class="sxs-lookup"><span data-stu-id="59cfa-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="59cfa-361">Esse objeto, em seguida, é usado para atualizar os parâmetros de objeto dentro da tabela criada.</span><span class="sxs-lookup"><span data-stu-id="59cfa-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="59cfa-362">Depois disso, a função faz uma chamada para seu serviço de Hub de notificação criado, que notifica os aplicativos de todos os inscritos.</span><span class="sxs-lookup"><span data-stu-id="59cfa-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="59cfa-363">Com o código no local, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="59cfa-364">Em seguida, clique o **\<** ícone (seta), no lado direito da página.</span><span class="sxs-lookup"><span data-stu-id="59cfa-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![Painel de upload aberto](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="59cfa-366">Um painel será Deslizar pela direita.</span><span class="sxs-lookup"><span data-stu-id="59cfa-366">A panel will slide in from the right.</span></span> <span data-ttu-id="59cfa-367">Nesse painel, clique em **carregar**, e um navegador de arquivos será exibida.</span><span class="sxs-lookup"><span data-stu-id="59cfa-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="59cfa-368">Navegue até e, em seguida, clique em, o **Project. JSON** arquivo, que você criou na **bloco de notas** anteriormente e, em seguida, clique no **abrir** botão.</span><span class="sxs-lookup"><span data-stu-id="59cfa-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="59cfa-369">Esse arquivo define as bibliotecas que sua função usará.</span><span class="sxs-lookup"><span data-stu-id="59cfa-369">This file defines the libraries that your function will use.</span></span>

    ![carregar o json](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="59cfa-371">Quando o arquivo foi carregado, ele será exibido no painel à direita.</span><span class="sxs-lookup"><span data-stu-id="59cfa-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="59cfa-372">Ao clicar nele irá abri-lo dentro de **função** editor.</span><span class="sxs-lookup"><span data-stu-id="59cfa-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="59cfa-373">Ele deve parecer **exatamente** o mesmo que a próxima imagem (etapa abaixo 23).</span><span class="sxs-lookup"><span data-stu-id="59cfa-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="59cfa-374">Em seguida, no painel à esquerda, abaixo **funções**, clique no **integrar** link.</span><span class="sxs-lookup"><span data-stu-id="59cfa-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![integrar a função](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="59cfa-376">Na próxima página, no canto superior direito, clique em **editor avançado** (conforme mostrado abaixo).</span><span class="sxs-lookup"><span data-stu-id="59cfa-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![abrir editor avançado](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="59cfa-378">Um **Function. JSON** arquivo será aberto no painel central, que precisa ser substituído com o seguinte trecho de código.</span><span class="sxs-lookup"><span data-stu-id="59cfa-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="59cfa-379">Isso define a função que você está criando e os parâmetros passados para a função.</span><span class="sxs-lookup"><span data-stu-id="59cfa-379">This defines the function you are building and the parameters passed into the function.</span></span>

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. <span data-ttu-id="59cfa-380">O editor agora deve ser semelhante a imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="59cfa-380">Your editor should now look like the image below:</span></span>

    ![volta para o editor padrão](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="59cfa-382">Você pode observar os parâmetros de entrada que você inseriu podem não corresponder a seus detalhes de tabela e armazenamento e, portanto, precisará ser atualizada com as informações.</span><span class="sxs-lookup"><span data-stu-id="59cfa-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="59cfa-383">**Não faça isso aqui**, conforme ele é explicado a seguir.</span><span class="sxs-lookup"><span data-stu-id="59cfa-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="59cfa-384">Basta clicar o **editor padrão** link no canto superior direito da página, para retornar.</span><span class="sxs-lookup"><span data-stu-id="59cfa-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="59cfa-385">Volta a **editor padrão**, clique em **armazenamento de tabela do Azure (tabela)** , em **entradas**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![Entradas de tabela](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="59cfa-387">Verifique se a correspondência seguinte **sua** informações, como eles podem ser diferentes (há uma imagem abaixo as etapas a seguir):</span><span class="sxs-lookup"><span data-stu-id="59cfa-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="59cfa-388">**Nome da tabela**: o nome da tabela que você criou no seu armazenamento do Azure, serviço de tabelas.</span><span class="sxs-lookup"><span data-stu-id="59cfa-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="59cfa-389">**Conexão da conta de armazenamento:** clique em **nova**, que é exibido junto com o menu suspenso e um painel será exibido à direita da janela.</span><span class="sxs-lookup"><span data-stu-id="59cfa-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![novo armazenamento](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="59cfa-391">Selecione suas **conta de armazenamento**, que você criou anteriormente para hospedar o **aplicativos de funções.**</span><span class="sxs-lookup"><span data-stu-id="59cfa-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="59cfa-392">Você observará que o **conta de armazenamento** valor de conexão foi criado.</span><span class="sxs-lookup"><span data-stu-id="59cfa-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="59cfa-393">Certifique-se de pressionar **salvar** quando terminar.</span><span class="sxs-lookup"><span data-stu-id="59cfa-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="59cfa-394">O **entradas** página agora deve corresponder a abaixo, mostrando **sua** informações.</span><span class="sxs-lookup"><span data-stu-id="59cfa-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![entradas concluída](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="59cfa-396">Em seguida, clique em **Hub de notificação do Azure (notificação)** – em **saídas**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="59cfa-397">Certifique-se a seguir correspondem à **sua** informações, como eles podem ser diferentes (há uma imagem abaixo as etapas a seguir):</span><span class="sxs-lookup"><span data-stu-id="59cfa-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="59cfa-398">**Nome do Hub de notificação**: esse é o nome do seu **Hub de notificação** instância de serviço, o que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="59cfa-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="59cfa-399">**Conexão de namespace de Hubs de notificação**: clique em **nova**, que é exibido junto com o menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="59cfa-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![Verifique as saídas](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="59cfa-401">O **Conexão** pop-up será exibida (consulte a imagem abaixo), em que você precisa selecionar o **Namespace** dos **Hub de notificação**, que você configurou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="59cfa-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="59cfa-402">Selecione suas **Hub de notificação** nome no menu suspenso central.</span><span class="sxs-lookup"><span data-stu-id="59cfa-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="59cfa-403">Defina as **diretiva** menu suspenso **DefaultFullSharedAccessSignature**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="59cfa-404">Clique o **selecionar** botão Voltar.</span><span class="sxs-lookup"><span data-stu-id="59cfa-404">Click the **Select** button to go back.</span></span>

        ![atualização de saída](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="59cfa-406">O **saídas** página agora deve corresponder a abaixo, mas com **sua** informações em vez disso.</span><span class="sxs-lookup"><span data-stu-id="59cfa-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="59cfa-407">Certifique-se de pressionar **salvar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="59cfa-408">*Não edite o nome do Hub de notificação diretamente* (isso deve ser feito usando o **Editor Avançado**, desde que você seguiu as etapas anteriores corretamente.</span><span class="sxs-lookup"><span data-stu-id="59cfa-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![saídas concluída](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="59cfa-410">Neste ponto, você deve testar a função, para garantir que ele está funcionando.</span><span class="sxs-lookup"><span data-stu-id="59cfa-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="59cfa-411">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="59cfa-411">To do this:</span></span> 

    1. <span data-ttu-id="59cfa-412">Navegue até a página de função mais uma vez:</span><span class="sxs-lookup"><span data-stu-id="59cfa-412">Navigate to the function page once more:</span></span>

        ![saídas concluída](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="59cfa-414">Na página de função, clique no **teste** guia na extrema direita da página, para abrir o *teste* folha:</span><span class="sxs-lookup"><span data-stu-id="59cfa-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![saídas concluída](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="59cfa-416">Dentro de **corpo da solicitação** caixa de texto da folha, cole o código abaixo:</span><span class="sxs-lookup"><span data-stu-id="59cfa-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. <span data-ttu-id="59cfa-417">Com o código de teste em vigor, clique o **executar** botão na parte inferior direita e o teste será executado.</span><span class="sxs-lookup"><span data-stu-id="59cfa-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="59cfa-418">Os logs de saída do teste serão exibidos na área de console, abaixo de seu código de função.</span><span class="sxs-lookup"><span data-stu-id="59cfa-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![saídas concluída](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="59cfa-420">Se o teste acima falhar, você precisará verificar duas vezes, você seguiu as etapas acima, exatamente, especialmente as configurações dentro do **integrar o painel**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="59cfa-421">Capítulo 7 - configurar o projeto do Unity da área de trabalho</span><span class="sxs-lookup"><span data-stu-id="59cfa-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59cfa-422">O aplicativo da área de trabalho que você está criando agora **não** funcionam no Editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="59cfa-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="59cfa-423">Ele precisa ser executado fora do Editor, seguindo a criação do aplicativo, usando o Visual Studio (ou o aplicativo implantado).</span><span class="sxs-lookup"><span data-stu-id="59cfa-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="59cfa-424">A seguir é um conjunto típico backup para o desenvolvimento com o Unity e realidade mista e como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="59cfa-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="59cfa-425">Configurar e testar o headset de realidade misturada envolvente.</span><span class="sxs-lookup"><span data-stu-id="59cfa-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="59cfa-426">Você irá **não** exigem controladores de movimento para este curso.</span><span class="sxs-lookup"><span data-stu-id="59cfa-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="59cfa-427">Se você precisar dar suporte a configurar o fone de ouvido imersivo, siga este [link sobre como configurar o Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="59cfa-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="59cfa-428">Abra **Unity** e clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-428">Open **Unity** and click **New**.</span></span>

    ![novo projeto do unity](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="59cfa-430">Você precisa fornecer um nome de projeto do Unity, insira **UnityDesktopNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="59cfa-431">Verifique se o tipo de projeto é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="59cfa-432">Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="59cfa-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="59cfa-433">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-433">Then, click **Create project**.</span></span>

    ![Criar projeto](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="59cfa-435">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="59cfa-436">Vá para **edite** > **preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="59cfa-437">Alteração **Editor de Script externo** à **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="59cfa-438">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="59cfa-438">Close the **Preferences** window.</span></span>

    ![conjunto de ferramentas do VS externas](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="59cfa-440">Em seguida, vá para **arquivo** > **configurações de Build** e selecione **plataforma Universal do Windows**, em seguida, clique no **alternar plataforma**botão Aplicar sua seleção.</span><span class="sxs-lookup"><span data-stu-id="59cfa-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![plataformas de switch](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="59cfa-442">Enquanto estiver na **arquivo** > **configurações de Build**, certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="59cfa-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="59cfa-443">**Dispositivo de destino** é definido como **qualquer dispositivo**</span><span class="sxs-lookup"><span data-stu-id="59cfa-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="59cfa-444">Este aplicativo estará para sua área de trabalho, portanto, deve ser **qualquer dispositivo**</span><span class="sxs-lookup"><span data-stu-id="59cfa-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="59cfa-445">**Tipo de compilação** é definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="59cfa-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="59cfa-446">**SDK** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="59cfa-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="59cfa-447">**Versão do Visual Studio** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="59cfa-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="59cfa-448">**Compilar e executar** é definido como **Máquina Local**</span><span class="sxs-lookup"><span data-stu-id="59cfa-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="59cfa-449">Enquanto está aqui, vale a pena salvar cena e adicioná-lo para a compilação.</span><span class="sxs-lookup"><span data-stu-id="59cfa-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="59cfa-450">Fazer isso selecionando **cenas abra Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="59cfa-451">Salvamento janela será exibida.</span><span class="sxs-lookup"><span data-stu-id="59cfa-451">A save window will appear.</span></span>

            ![Adicionar cenas abertas](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="59cfa-453">Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![nova pasta de cenas](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="59cfa-455">Abrir seu recém-criado **cenas** pasta e, em seguida, no **nome do arquivo:** campo de texto, digite **NH\_Desktop\_cena**, em seguida, pressione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![new NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="59cfa-457">O restante de configurações, em **configurações de Build**, deverá ser deixado como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="59cfa-458">Na mesma janela, clique no **configurações do Player** botão, isso abrirá o painel relacionado no espaço em que o **Inspetor** está localizado.</span><span class="sxs-lookup"><span data-stu-id="59cfa-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="59cfa-459">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="59cfa-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="59cfa-460">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="59cfa-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="59cfa-461">**Versão de tempo de execução de scripts** deve ser **Experimental (equivalente ao .NET 4.6)**</span><span class="sxs-lookup"><span data-stu-id="59cfa-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="59cfa-462">**Script de back-end** deve ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="59cfa-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="59cfa-463">**Nível de compatibilidade de API** deve ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="59cfa-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![.NET versão 4.6](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="59cfa-465">Dentro de **configurações de publicação** guia, em **recursos**, verifique:</span><span class="sxs-lookup"><span data-stu-id="59cfa-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="59cfa-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="59cfa-466">**InternetClient**</span></span>

            ![cliente de escala da internet](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="59cfa-468">Volta **configurações de Build** *Unity C\# projetos* não fica acinzentado; marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="59cfa-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="59cfa-469">Fechar o **configurações de Build** janela.</span><span class="sxs-lookup"><span data-stu-id="59cfa-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="59cfa-470">Salvar sua cena e seu projeto **arquivo** > **salvar cena de arquivos** > **Salvar projeto**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="59cfa-471">Se você quiser ignorar a *configurar o Unity* componente para este projeto (aplicativo da área de trabalho) e continuar diretamente no código, fique à vontade para [baixar esse unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="59cfa-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="59cfa-472">Você ainda precisará adicionar os componentes de script.</span><span class="sxs-lookup"><span data-stu-id="59cfa-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="59cfa-473">Capítulo 8 - importando as DLLs no Unity</span><span class="sxs-lookup"><span data-stu-id="59cfa-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="59cfa-474">Você usará o armazenamento do Azure para Unity (que por si só aproveita o .net SDK do Azure).</span><span class="sxs-lookup"><span data-stu-id="59cfa-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="59cfa-475">Para obter mais informações, siga este [link sobre o armazenamento do Azure para Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="59cfa-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="59cfa-476">Atualmente, há um problema conhecido no Unity que requer o plug-ins para ser reconfigurado após a importação.</span><span class="sxs-lookup"><span data-stu-id="59cfa-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="59cfa-477">Estas etapas (4 a 7 desta seção) não será necessárias depois que o bug foi resolvido.</span><span class="sxs-lookup"><span data-stu-id="59cfa-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="59cfa-478">Para importar o SDK no seu próprio projeto, verifique se você baixou a versão mais recente [ **unitypackage** ](https://aka.ms/azstorage-unitysdk) do GitHub.</span><span class="sxs-lookup"><span data-stu-id="59cfa-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="59cfa-479">Em seguida, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="59cfa-479">Then, do the following:</span></span>

1.  <span data-ttu-id="59cfa-480">Adicionar o **unitypackage** para o Unity, usando o **ativos \> Importar pacote \> pacote personalizado** opção de menu.</span><span class="sxs-lookup"><span data-stu-id="59cfa-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="59cfa-481">No **Importar pacote do Unity** caixa que é exibida, você pode selecionar tudo em \* \**plug-in* \> \* armazenamento \* \* \*.</span><span class="sxs-lookup"><span data-stu-id="59cfa-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="59cfa-482">Desmarque todas as outras, como ele não é necessário para este curso.</span><span class="sxs-lookup"><span data-stu-id="59cfa-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Importar pacote](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="59cfa-484">Clique o ***importação*** botão para adicionar itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="59cfa-485">Vá para o **armazenamento** pasta sob **plug-ins** no projeto, exibir e selecione os seguintes plug-ins *apenas*:</span><span class="sxs-lookup"><span data-stu-id="59cfa-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="59cfa-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="59cfa-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="59cfa-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="59cfa-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="59cfa-488">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="59cfa-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="59cfa-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="59cfa-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="59cfa-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="59cfa-490">System.Spatial</span></span>

![desmarque qualquer plataforma](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="59cfa-492">Com o *esses plug-ins específicos* selecionado, **desmarque** **Any Platform** e **desmarque** **WSAPlayer** em seguida, clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![Aplicar as dlls de plataforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="59cfa-494">Nós estamos marcando esses plug-ins específicos para ser usado apenas no Editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="59cfa-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="59cfa-495">Isso ocorre porque há versões diferentes dos mesmos plug-ins na pasta WSA que será usado depois que o projeto é exportado do Unity.</span><span class="sxs-lookup"><span data-stu-id="59cfa-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="59cfa-496">No **armazenamento** pasta Plug-in, selecione apenas:</span><span class="sxs-lookup"><span data-stu-id="59cfa-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="59cfa-497">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="59cfa-497">Microsoft.Data.Services.Client</span></span>

        ![conjunto não processar para dlls](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="59cfa-499">Verifique as **processo não** caixa sob **configurações de plataforma** e clique em ***aplicar***.</span><span class="sxs-lookup"><span data-stu-id="59cfa-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![não aplicar nenhum processamento](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="59cfa-501">Nós estamos marcando esse plug-in "Não processar", porque o patcher de assembly do Unity tem dificuldade para processar esse plug-in.</span><span class="sxs-lookup"><span data-stu-id="59cfa-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="59cfa-502">O plug-in ainda funcionará, mesmo que ele não será processado.</span><span class="sxs-lookup"><span data-stu-id="59cfa-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="59cfa-503">Capítulo 9 - criar a classe TableToScene no projeto do Unity da área de trabalho</span><span class="sxs-lookup"><span data-stu-id="59cfa-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="59cfa-504">Agora você precisa criar os scripts que contém o código para executar este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="59cfa-505">É o primeiro script que você precisa criar **TableToScene**, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="59cfa-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="59cfa-506">Ler entidades dentro da tabela do Azure.</span><span class="sxs-lookup"><span data-stu-id="59cfa-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="59cfa-507">Usando os dados da tabela, determinar quais objetos ao gerar e em qual posição.</span><span class="sxs-lookup"><span data-stu-id="59cfa-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="59cfa-508">É o segundo script, você precisa criar **CloudScene**, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="59cfa-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="59cfa-509">Registrando o evento do botão esquerdo do mouse, para permitir que o usuário arrastar objetos em torno da cena.</span><span class="sxs-lookup"><span data-stu-id="59cfa-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="59cfa-510">Serializar os dados do objeto desta cena do Unity e enviá-la para o aplicativo de funções do Azure.</span><span class="sxs-lookup"><span data-stu-id="59cfa-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="59cfa-511">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="59cfa-511">To create this class:</span></span>

1.  <span data-ttu-id="59cfa-512">Clique com botão direito no **ativo** pasta localizada no painel de projeto, **Create** > **pasta**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="59cfa-513">Nomeie a pasta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-513">Name the folder **Scripts**.</span></span>

    ![criar a pasta de scripts](images/AzureLabs-Lab8-66.png)

    ![Crie a pasta de scripts 2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="59cfa-516">Clique duas vezes na pasta recém-criada, para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="59cfa-517">Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="59cfa-518">Nomeie o script **TableToScene**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="59cfa-519">![novo script c#](images/AzureLabs-Lab8-68.png)
    ![TableToScene renomeação](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="59cfa-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="59cfa-520">Clique duas vezes no script para abri-lo no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="59cfa-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="59cfa-521">Adicione os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="59cfa-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="59cfa-522">Dentro da classe, insira as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="59cfa-522">Within the class, insert the following variables:</span></span>

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > <span data-ttu-id="59cfa-523">Substitua os **accountName** valor com o nome do serviço de armazenamento do Azure e **accountKey** valor com o valor da chave encontrado no serviço de armazenamento do Azure, no Portal do Azure (consulte imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="59cfa-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![chave da conta de busca](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="59cfa-525">Agora, adicione a **Start ()** e **Awake()** métodos para inicializar a classe.</span><span class="sxs-lookup"><span data-stu-id="59cfa-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  <span data-ttu-id="59cfa-526">Dentro de **TableToScene** de classe, adicione o método que irá recuperar os valores da tabela do Azure e usá-las para gerar os primitivos apropriados na cena.</span><span class="sxs-lookup"><span data-stu-id="59cfa-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  <span data-ttu-id="59cfa-527">Fora de **TableToScene** classe, você precisa definir a classe usada pelo aplicativo para serializar e desserializar os **entidades de tabela**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. <span data-ttu-id="59cfa-528">Verifique se você **salvar** antes de voltar ao Editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="59cfa-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="59cfa-529">Clique o **câmera principal** da **hierarquia** do painel, para que suas propriedades aparecem na **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="59cfa-530">Com o **Scripts** pasta aberta, selecione o script **arquivo TableToScene** e arraste-a para o **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="59cfa-531">O resultado deve ser conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="59cfa-531">The result should be as below:</span></span>

    ![Adicionar o script a câmera principal](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="59cfa-533">Capítulo 10 - criar a classe CloudScene no projeto do Unity a área de trabalho</span><span class="sxs-lookup"><span data-stu-id="59cfa-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="59cfa-534">É o segundo script, você precisa criar **CloudScene**, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="59cfa-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="59cfa-535">Registrando o evento do botão esquerdo do mouse, para permitir que o usuário arrastar objetos em torno da cena.</span><span class="sxs-lookup"><span data-stu-id="59cfa-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="59cfa-536">Serializar os dados do objeto desta cena do Unity e enviá-la para o aplicativo de funções do Azure.</span><span class="sxs-lookup"><span data-stu-id="59cfa-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="59cfa-537">Para criar o segundo script:</span><span class="sxs-lookup"><span data-stu-id="59cfa-537">To create the second script:</span></span>

1.  <span data-ttu-id="59cfa-538">Clique com botão direito dentro de **Scripts** pasta, clique em **Create**, **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="59cfa-539">Nomeie o script **CloudScene**</span><span class="sxs-lookup"><span data-stu-id="59cfa-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="59cfa-540">![novo script c#](images/AzureLabs-Lab8-72.png)
    ![renomear CloudScene](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="59cfa-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="59cfa-541">Adicione os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="59cfa-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="59cfa-542">Insira as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="59cfa-542">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  <span data-ttu-id="59cfa-543">Substitua os **azureFunctionEndpoint** valor com a URL do aplicativo de função do Azure encontrada no serviço de aplicativo de função do Azure, no Portal do Azure, conforme mostrado na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="59cfa-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![obter URL de função](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="59cfa-545">Agora, adicione a **Start ()** e **Awake()** métodos para inicializar a classe.</span><span class="sxs-lookup"><span data-stu-id="59cfa-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  <span data-ttu-id="59cfa-546">Dentro de **Update ()** método, adicione o seguinte código que irá detectar a entrada de mouse e a ação de arrastar, que por sua vez moverá GameObjects na cena.</span><span class="sxs-lookup"><span data-stu-id="59cfa-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="59cfa-547">Se o usuário tiver arrastado e solto um objeto, ele passará o nome e as coordenadas do objeto para o método **UpdateCloudScene()** , que chamará o serviço de aplicativo de funções do Azure, que atualizará a tabela do Azure e disparar o notificação.</span><span class="sxs-lookup"><span data-stu-id="59cfa-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  <span data-ttu-id="59cfa-548">Agora, adicione a **UpdateCloudScene()** método, conforme mostrado a seguir:</span><span class="sxs-lookup"><span data-stu-id="59cfa-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  <span data-ttu-id="59cfa-549">Salve o código e retorne ao Unity</span><span class="sxs-lookup"><span data-stu-id="59cfa-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="59cfa-550">Arraste o **CloudScene** gerar script para o **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="59cfa-551">Clique o **câmera principal** da **hierarquia** do painel, para que suas propriedades aparecem na **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="59cfa-552">Com o **Scripts** aberto, selecione de pasta a **CloudScene** do script e arraste-a para o **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="59cfa-553">O resultado deve ser conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="59cfa-553">The result should be as below:</span></span>

        > ![Arraste o script de nuvem para a câmera principal](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="59cfa-555">Capítulo 11 - compilar o projeto da área de trabalho para a UWP</span><span class="sxs-lookup"><span data-stu-id="59cfa-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="59cfa-556">Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído.</span><span class="sxs-lookup"><span data-stu-id="59cfa-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="59cfa-557">Navegue até **configurações de Build** (**arquivo** > **configurações de Build**).</span><span class="sxs-lookup"><span data-stu-id="59cfa-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="59cfa-558">Dos **configurações de Build** janela, clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-558">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilar projeto](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="59cfa-560">Um **Explorador de arquivos** janela será pop-up, que pedirá um local para compilação.</span><span class="sxs-lookup"><span data-stu-id="59cfa-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="59cfa-561">Crie uma nova pasta (clicando **nova pasta** no canto superior esquerdo) e nomeie-o **compilações**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![nova pasta para o build](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="59cfa-563">Abra o novo **compilações** pasta e criar outra pasta (usando **nova pasta** mais uma vez) e nomeie- **NH\_Desktop\_aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![nome da pasta NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="59cfa-565">Com o **NH\_área de trabalho\_aplicativo** selecionado.</span><span class="sxs-lookup"><span data-stu-id="59cfa-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="59cfa-566">Clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-566">click **Select Folder**.</span></span> <span data-ttu-id="59cfa-567">O projeto será levar um minuto ou mais para compilar.</span><span class="sxs-lookup"><span data-stu-id="59cfa-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="59cfa-568">Compilação, a seguir **Explorador de arquivos** será exibida mostrando o local do novo projeto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="59cfa-569">Não há necessidade de abri-lo, no entanto, conforme necessário criar outro Unity projeto pela primeira vez, nos próximos capítulos.</span><span class="sxs-lookup"><span data-stu-id="59cfa-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="59cfa-570">Capítulo 12 - configurar o projeto do Unity realidade mista</span><span class="sxs-lookup"><span data-stu-id="59cfa-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="59cfa-571">A seguir é um conjunto típico backup para o desenvolvimento com a realidade misturada e como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="59cfa-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="59cfa-572">Abra **Unity** e clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-572">Open **Unity** and click **New**.</span></span>

    ![novo projeto do unity](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="59cfa-574">Agora você precisará fornecer um nome de projeto do Unity, insira **UnityMRNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="59cfa-575">Verifique se o tipo de projeto é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="59cfa-576">Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="59cfa-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="59cfa-577">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-577">Then, click **Create project**.</span></span>

    ![nome UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="59cfa-579">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="59cfa-580">Vá para **edite** > **preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="59cfa-581">Alteração **Editor de Script externo** à **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="59cfa-582">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="59cfa-582">Close the **Preferences** window.</span></span>

    ![editor de conjunto externo para o VS](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="59cfa-584">Em seguida, vá para **arquivo** > **configurações de Build** e alternar a plataforma **plataforma Universal do Windows**, clicando no **alternar plataforma**  botão.</span><span class="sxs-lookup"><span data-stu-id="59cfa-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![plataformas de comutador para UWP](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="59cfa-586">Vá para **arquivo** > **configurações de Build** e certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="59cfa-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="59cfa-587">**Dispositivo de destino** é definido como **qualquer dispositivo**</span><span class="sxs-lookup"><span data-stu-id="59cfa-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="59cfa-588">Para o Microsoft HoloLens, defina **dispositivo de destino** à *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="59cfa-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="59cfa-589">**Tipo de compilação** é definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="59cfa-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="59cfa-590">**SDK** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="59cfa-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="59cfa-591">**Versão do Visual Studio** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="59cfa-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="59cfa-592">**Compilar e executar** é definido como **Máquina Local**</span><span class="sxs-lookup"><span data-stu-id="59cfa-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="59cfa-593">Enquanto está aqui, vale a pena salvar cena e adicioná-lo para a compilação.</span><span class="sxs-lookup"><span data-stu-id="59cfa-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="59cfa-594">Fazer isso selecionando **cenas abra Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="59cfa-595">Salvamento janela será exibida.</span><span class="sxs-lookup"><span data-stu-id="59cfa-595">A save window will appear.</span></span>

            ![Adicionar cenas abertas](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="59cfa-597">Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![nova pasta de cenas](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="59cfa-599">Abra seu recém-criado **cenas** pasta e, em seguida, no **nome do arquivo:** campo de texto, digite **NH\_MR\_cena**, em seguida, pressione  **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![new scene - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="59cfa-601">O restante de configurações, em **configurações de Build**, deverá ser deixado como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="59cfa-602">Na mesma janela, clique no **configurações do Player** botão, isso abrirá o painel relacionado no espaço em que o **Inspetor** está localizado.</span><span class="sxs-lookup"><span data-stu-id="59cfa-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![Abrir configurações do player](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="59cfa-604">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="59cfa-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="59cfa-605">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="59cfa-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="59cfa-606">**Versão de tempo de execução de scripts** deve ser **Experimental** (equivalente ao .NET 4.6)</span><span class="sxs-lookup"><span data-stu-id="59cfa-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="59cfa-607">**Script de back-end** deve ser ***.NET***</span><span class="sxs-lookup"><span data-stu-id="59cfa-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="59cfa-608">**Nível de compatibilidade de API** deve ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="59cfa-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![compatibilidade de API](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="59cfa-610">Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado</span><span class="sxs-lookup"><span data-stu-id="59cfa-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![atualizar as configurações de xr](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="59cfa-612">Dentro de **configurações de publicação** guia, em **recursos**, fazer check-in:</span><span class="sxs-lookup"><span data-stu-id="59cfa-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="59cfa-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="59cfa-613">**InternetClient**</span></span>           

            ![cliente de escala da internet](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="59cfa-615">Volta **configurações de Build**, **Unity C# projetos** não fica acinzentado: marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="59cfa-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="59cfa-616">Com essas alterações foi feitas, feche a janela de configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="59cfa-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="59cfa-617">Salvar sua cena e seu projeto **arquivo** > **salvar cena de arquivos** > **Salvar projeto**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="59cfa-618">Se você quiser ignorar a *configurar o Unity* componente para este projeto (misturado realidade aplicativo) e continuar diretamente no código, fique à vontade para [baixar esse unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span><span class="sxs-lookup"><span data-stu-id="59cfa-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="59cfa-619">Você ainda precisará adicionar os componentes de script.</span><span class="sxs-lookup"><span data-stu-id="59cfa-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="59cfa-620">Capítulo 13 - importando as DLLs no projeto do Unity realidade mista</span><span class="sxs-lookup"><span data-stu-id="59cfa-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="59cfa-621">Usando o armazenamento do Azure para a biblioteca de Unity (que usa o SDK do .net para Azure).</span><span class="sxs-lookup"><span data-stu-id="59cfa-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="59cfa-622">Siga este [link sobre como usar o armazenamento do Azure com o Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="59cfa-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="59cfa-623">Atualmente, há um problema conhecido no Unity que requer o plug-ins para ser reconfigurado após a importação.</span><span class="sxs-lookup"><span data-stu-id="59cfa-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="59cfa-624">Estas etapas (4 a 7 desta seção) não será necessárias depois que o bug foi resolvido.</span><span class="sxs-lookup"><span data-stu-id="59cfa-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="59cfa-625">Para importar o SDK no seu próprio projeto, verifique se você baixou a versão mais recente [unitypackage](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="59cfa-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="59cfa-626">Em seguida, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="59cfa-626">Then, do the following:</span></span>

1.  <span data-ttu-id="59cfa-627">Adicionar o unitypackage baixado acima, para o Unity, usando o **ativos** > **Importar pacote** > **pacote personalizado** opção de menu .</span><span class="sxs-lookup"><span data-stu-id="59cfa-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="59cfa-628">No **Importar pacote do Unity** caixa que é exibida, você pode selecionar tudo sob **plug-in** > **armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![Importar pacote](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="59cfa-630">Clique o **importação** botão para adicionar itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="59cfa-631">Vá para o **armazenamento** pasta sob **plug-ins** no projeto, exibir e selecione os seguintes plug-ins *apenas*:</span><span class="sxs-lookup"><span data-stu-id="59cfa-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="59cfa-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="59cfa-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="59cfa-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="59cfa-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="59cfa-634">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="59cfa-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="59cfa-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="59cfa-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="59cfa-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="59cfa-636">System.Spatial</span></span>

    ![Selecione o plug-ins](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="59cfa-638">Com o *esses plug-ins específicos* selecionado, **desmarque** **Any Platform** e **desmarque** **WSAPlayer** em seguida, clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![Aplicar alterações de plataforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="59cfa-640">Você marcar esses plug-ins específicos para ser usado apenas no Editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="59cfa-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="59cfa-641">Isso ocorre porque há versões diferentes dos mesmos plug-ins na pasta WSA que será usado depois que o projeto é exportado do Unity.</span><span class="sxs-lookup"><span data-stu-id="59cfa-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="59cfa-642">No **armazenamento** pasta Plug-in, selecione apenas:</span><span class="sxs-lookup"><span data-stu-id="59cfa-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="59cfa-643">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="59cfa-643">Microsoft.Data.Services.Client</span></span>

        ![Selecione o cliente de serviços de dados](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="59cfa-645">Verifique as **processo não** caixa sob **configurações de plataforma** e clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![não processar](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="59cfa-647">Você marcar esse plug-in "Não processar" porque o patcher de assembly do Unity tem dificuldade para processar esse plug-in.</span><span class="sxs-lookup"><span data-stu-id="59cfa-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="59cfa-648">O plug-in ainda funcionará, mesmo que ele não será processado.</span><span class="sxs-lookup"><span data-stu-id="59cfa-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="59cfa-649">Capítulo 14 - criar a classe de TableToScene no projeto do Unity a realidade misturada</span><span class="sxs-lookup"><span data-stu-id="59cfa-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="59cfa-650">O **TableToScene** classe é idêntico àquele explicado [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="59cfa-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="59cfa-651">Criar a mesma classe na projeto do Unity seguindo o mesmo procedimento explicado de realidade misturada [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="59cfa-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="59cfa-652">Depois de concluir este capítulo, ambos seus **projetos do Unity** terá essa classe configurar na câmera principal.</span><span class="sxs-lookup"><span data-stu-id="59cfa-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="59cfa-653">Capítulo 15 - criar a classe de NotificationReceiver no projeto para Unity realidade mista</span><span class="sxs-lookup"><span data-stu-id="59cfa-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="59cfa-654">É o segundo script, você precisa criar **NotificationReceiver**, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="59cfa-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="59cfa-655">Ao registrar o aplicativo com o Hub de notificação na inicialização.</span><span class="sxs-lookup"><span data-stu-id="59cfa-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="59cfa-656">Escutar as notificações provenientes do Hub de notificação.</span><span class="sxs-lookup"><span data-stu-id="59cfa-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="59cfa-657">Os dados do objeto de notificações recebidas durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="59cfa-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="59cfa-658">Mova o GameObjects na cena, com base em dados desserializados.</span><span class="sxs-lookup"><span data-stu-id="59cfa-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="59cfa-659">Para criar o **NotificationReceiver** script:</span><span class="sxs-lookup"><span data-stu-id="59cfa-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="59cfa-660">Clique com botão direito dentro de **Scripts** pasta, clique em **Create**, **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="59cfa-661">Nomeie o script **NotificationReceiver**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="59cfa-662">![criar um novo script c#](images/AzureLabs-Lab8-95.png)
    ![Nomeie-o NotificationReceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="59cfa-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="59cfa-663">Clique duas vezes no script para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="59cfa-664">Adicione os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="59cfa-664">Add the following namespaces:</span></span>

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  <span data-ttu-id="59cfa-665">Insira as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="59cfa-665">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  <span data-ttu-id="59cfa-666">Substituto a **hubName** valor com o nome do serviço de Hub de notificação, e **hubListenEndpoint** valor com o valor de ponto de extremidade localizado na guia políticas de acesso, o serviço de Hub de notificação do Azure, além de Portal do Azure (veja a imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="59cfa-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![Inserir endpoint de política de hubs de notificação](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="59cfa-668">Agora, adicione a **Start ()** e **Awake()** métodos para inicializar a classe.</span><span class="sxs-lookup"><span data-stu-id="59cfa-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  <span data-ttu-id="59cfa-669">Adicione a **WaitForNotification** método para permitir que o aplicativo para receber notificações da biblioteca de Hub de notificação sem conflitos entre com o Thread principal:</span><span class="sxs-lookup"><span data-stu-id="59cfa-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  <span data-ttu-id="59cfa-670">O seguinte método, **InitNotificationAsync()** , registrará o aplicativo com a notificação de serviço do Hub na inicialização.</span><span class="sxs-lookup"><span data-stu-id="59cfa-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="59cfa-671">O código é comentado, pois o Unity não poderá compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="59cfa-672">Quando você importa o pacote Nuget do sistema de mensagens do Azure no Visual Studio, você removerá os comentários.</span><span class="sxs-lookup"><span data-stu-id="59cfa-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  <span data-ttu-id="59cfa-673">O manipulador a seguir, **Channel\_PushNotificationReceived()** , será disparado sempre que uma notificação é recebida.</span><span class="sxs-lookup"><span data-stu-id="59cfa-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="59cfa-674">Ele serão desserializados a notificação, que será a entidade de tabela do Azure que foi movido no aplicativo de área de trabalho e, em seguida, mova o GameObject correspondente na cena MR para a mesma posição.</span><span class="sxs-lookup"><span data-stu-id="59cfa-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="59cfa-675">O código é comentado porque o código faz referência a biblioteca de mensagens do Azure, que você irá adicionar depois de criar o projeto do Unity usando o Gerenciador de pacotes do Nuget, dentro do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59cfa-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="59cfa-676">Como tal, o projeto do Unity não poderão criar, a menos que ele é comentado. Lembre-se que deve compilar o projeto e, em seguida, deseja retornar para o Unity, você precisará **comentar novamente** que o código.</span><span class="sxs-lookup"><span data-stu-id="59cfa-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. <span data-ttu-id="59cfa-677">Lembre-se de salvar suas alterações antes de voltar ao Editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="59cfa-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="59cfa-678">Clique o **câmera principal** da **hierarquia** do painel, para que suas propriedades aparecem na **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="59cfa-679">Com o **Scripts** aberto, selecione de pasta a **NotificationReceiver** do script e arraste-a para o **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="59cfa-680">O resultado deve ser conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="59cfa-680">The result should be as below:</span></span>

    ![Arraste o script do destinatário de notificação à câmera](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="59cfa-682">Se você estiver desenvolvendo isso para o Microsoft HoloLens, você precisará atualizar o **câmera principal**do *câmera* componente, para que:</span><span class="sxs-lookup"><span data-stu-id="59cfa-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="59cfa-683">Limpe os sinalizadores de: Cor sólida</span><span class="sxs-lookup"><span data-stu-id="59cfa-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="59cfa-684">Em segundo plano: Preto</span><span class="sxs-lookup"><span data-stu-id="59cfa-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="59cfa-685">Capítulo 16 - compilar o projeto de realidade mista para UWP</span><span class="sxs-lookup"><span data-stu-id="59cfa-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="59cfa-686">Este capítulo é idêntico ao criar processo para o projeto anterior.</span><span class="sxs-lookup"><span data-stu-id="59cfa-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="59cfa-687">Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído, portanto, é hora de criá-lo do Unity.</span><span class="sxs-lookup"><span data-stu-id="59cfa-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="59cfa-688">Navegue até **configurações de Build** ( **arquivo** > **configurações de Build** ).</span><span class="sxs-lookup"><span data-stu-id="59cfa-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="59cfa-689">Do **configurações de Build** menu, verifique se **Unity C# projetos**\* está marcada (que permitirá que você edite os scripts neste projeto, depois de compilação).</span><span class="sxs-lookup"><span data-stu-id="59cfa-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="59cfa-690">Depois de fazer isso, clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-690">After this is done, click **Build**.</span></span>

    ![Compilar projeto](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="59cfa-692">Um **Explorador de arquivos** janela será pop-up, que pedirá um local para compilação.</span><span class="sxs-lookup"><span data-stu-id="59cfa-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="59cfa-693">Crie uma nova pasta (clicando **nova pasta** no canto superior esquerdo) e nomeie-o **compilações**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Criar pasta builds](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="59cfa-695">Abra o novo **compilações** pasta e criar outra pasta (usando **nova pasta** mais uma vez) e nomeie- **NH\_MR\_aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![Criar pasta NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="59cfa-697">Com o **NH\_MR\_aplicativo** selecionado.</span><span class="sxs-lookup"><span data-stu-id="59cfa-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="59cfa-698">Clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-698">click **Select Folder**.</span></span> <span data-ttu-id="59cfa-699">O projeto será levar um minuto ou mais para compilar.</span><span class="sxs-lookup"><span data-stu-id="59cfa-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="59cfa-700">Após a compilação, uma **Explorador de arquivos** janela será aberta no local do novo projeto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="59cfa-701">Capítulo 17 - adicionar pacotes NuGet para a solução UnityMRNotifHub</span><span class="sxs-lookup"><span data-stu-id="59cfa-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="59cfa-702">Por favor, lembre-se de que, depois de adicionar os seguintes pacotes NuGet (e remova o código nos próximos [capítulo](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), o código, quando reaberta dentro do projeto do Unity, apresentará erros.</span><span class="sxs-lookup"><span data-stu-id="59cfa-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="59cfa-703">Se você quiser voltar e continuar a editar no Editor do Unity, você precisa que o código errosome de comentário e, em seguida, remova os comentários novamente mais tarde, depois que você está de volta no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59cfa-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="59cfa-704">Quando a compilação de realidade misturada tiver sido concluída, navegue até o projeto de realidade misturada, que você criou, e clique duas vezes no arquivo de solução (. sln) nessa pasta, para abrir sua solução com o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="59cfa-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="59cfa-705">Agora você precisará adicionar o **windowsazure** pacote do NuGet; essa é uma biblioteca que é usada para receber notificações do Hub de notificação.</span><span class="sxs-lookup"><span data-stu-id="59cfa-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="59cfa-706">Para importar o pacote do NuGet:</span><span class="sxs-lookup"><span data-stu-id="59cfa-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="59cfa-707">No **Gerenciador de soluções**, clique com botão direito em sua solução</span><span class="sxs-lookup"><span data-stu-id="59cfa-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="59cfa-708">Clique em **gerenciar pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-708">Click on **Manage NuGet Packages**.</span></span>

    ![Abra o Gerenciador do nuget](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="59cfa-710">Selecione o ***navegue*** guia e pesquise **windowsazure**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![localizar o pacote de sistema de mensagens do windows azure](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="59cfa-712">Selecione o resultado (como mostrado abaixo) e na janela à direita, selecione a caixa de seleção ao lado **projeto**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="59cfa-713">Isso colocará um tique na caixa de seleção ao lado **Project**, juntamente com a caixa de seleção ao lado de **Assembly-CSharp** e **UnityMRNotifHub** projeto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![todos os projetos de escala](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="59cfa-715">A versão fornecida inicialmente **talvez não** ser compatível com este projeto.</span><span class="sxs-lookup"><span data-stu-id="59cfa-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="59cfa-716">Portanto, clique no menu suspenso ao lado **versão**e clique em **versão 0.1.7.9**, em seguida, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="59cfa-717">Você terminou de instalar o pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="59cfa-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="59cfa-718">Localizar inserido no código comentado a **NotificationReceiver** de classe e remova os comentários...</span><span class="sxs-lookup"><span data-stu-id="59cfa-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="59cfa-719">Capítulo 18 - aplicativo de edição UnityMRNotifHub, classe NotificationReceiver</span><span class="sxs-lookup"><span data-stu-id="59cfa-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="59cfa-720">Após ter adicionado a **pacotes do NuGet**, você precisará *Descomente* algum código dentro a **NotificationReceiver** classe.</span><span class="sxs-lookup"><span data-stu-id="59cfa-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="59cfa-721">Isso inclui:</span><span class="sxs-lookup"><span data-stu-id="59cfa-721">This includes:</span></span>

1. <span data-ttu-id="59cfa-722">O namespace na parte superior:</span><span class="sxs-lookup"><span data-stu-id="59cfa-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="59cfa-723">Todo o código dentro de **InitNotificationsAsync()** método:</span><span class="sxs-lookup"><span data-stu-id="59cfa-723">All the code within the **InitNotificationsAsync()** method:</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> <span data-ttu-id="59cfa-724">O código acima tem um comentário em si: Verifique se você não acidentalmente *sem marca de comentário* que de comentário (como o código não será compilado se você tiver!).</span><span class="sxs-lookup"><span data-stu-id="59cfa-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="59cfa-725">E, por fim, o **Channel_PushNotificationReceived** eventos:</span><span class="sxs-lookup"><span data-stu-id="59cfa-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

<span data-ttu-id="59cfa-726">Com essas sem marca de comentário, certifique-se de que você salve e, em seguida, vá para o próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="59cfa-727">Capítulo 19 - associar o projeto de realidade mista para a app Store</span><span class="sxs-lookup"><span data-stu-id="59cfa-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="59cfa-728">Agora você precisa associar o **realidade misturada** projeto para o aplicativo Store criado no início do laboratório.</span><span class="sxs-lookup"><span data-stu-id="59cfa-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="59cfa-729">Abra a solução.</span><span class="sxs-lookup"><span data-stu-id="59cfa-729">Open the solution.</span></span>

2.  <span data-ttu-id="59cfa-730">Clique com botão direito no aplicativo UWP projeto no painel Gerenciador de soluções, acesse **Store**, e **associar aplicativo com o Store...** .</span><span class="sxs-lookup"><span data-stu-id="59cfa-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![Abra o repositório de associação](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="59cfa-732">Uma nova janela será exibida chamada **associar seu aplicativo com a Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="59cfa-733">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-733">Click **Next**.</span></span>

    ![Vá para a próxima tela](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="59cfa-735">Ele carregará todos os aplicativos associados à conta que você fez logon.</span><span class="sxs-lookup"><span data-stu-id="59cfa-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="59cfa-736">Se você não estiver conectado à sua conta, você poderá **fazer logon** nesta página.</span><span class="sxs-lookup"><span data-stu-id="59cfa-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="59cfa-737">Localizar o **nome do aplicativo da Store** que você criou no início deste tutorial e selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="59cfa-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="59cfa-738">Em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-738">Then click **Next**.</span></span>

    ![Localize e selecione o nome do repositório](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="59cfa-740">Clique em **associar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-740">Click **Associate**.</span></span>

    ![associar o aplicativo](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="59cfa-742">Seu aplicativo agora está **associados** com a App Store.</span><span class="sxs-lookup"><span data-stu-id="59cfa-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="59cfa-743">Isso é necessário para habilitar as notificações.</span><span class="sxs-lookup"><span data-stu-id="59cfa-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="59cfa-744">Capítulo 20 - implantar aplicativos UnityMRNotifHub e UnityDesktopNotifHub</span><span class="sxs-lookup"><span data-stu-id="59cfa-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="59cfa-745">Este capítulo pode ser mais fácil com duas pessoas, como o resultado incluirá tanto aplicativos em execução, um que executa em seu computador Desktop e o outro dentro de imersão fone de ouvido.</span><span class="sxs-lookup"><span data-stu-id="59cfa-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="59cfa-746">O aplicativo de fone de ouvido imersivo está aguardando para receber alterações para a cena (alterações na posição dos GameObjects local) e o aplicativo da área de trabalho será fazer alterações à sua cena local (alterações de posição), que será compartilhada para o aplicativo MR.</span><span class="sxs-lookup"><span data-stu-id="59cfa-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="59cfa-747">Faz sentido para implantar o aplicativo MR primeiro, seguido pelo aplicativo da área de trabalho, para que o receptor pode começar a escutar.</span><span class="sxs-lookup"><span data-stu-id="59cfa-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="59cfa-748">Para implantar o **UnityMRNotifHub** aplicativo em seu computador Local:</span><span class="sxs-lookup"><span data-stu-id="59cfa-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="59cfa-749">Abra o arquivo de solução do seu **UnityMRNotifHub** app **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="59cfa-750">No **plataforma da solução**, selecione **x86, computador Local**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="59cfa-751">No **configuração da solução** selecionar **depurar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![definir a configuração de projeto](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="59cfa-753">Vá para **menu Build** e clique em **implantar solução** para carregar o aplicativo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="59cfa-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="59cfa-754">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="59cfa-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="59cfa-755">Para implantar o **UnityDesktopNotifHub** aplicativo no computador Local:</span><span class="sxs-lookup"><span data-stu-id="59cfa-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="59cfa-756">Abra o arquivo de solução do seu **UnityDesktopNotifHub** app **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="59cfa-757">No **plataforma da solução**, selecione **x86, computador Local**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="59cfa-758">No **configuração da solução** selecionar **depurar**.</span><span class="sxs-lookup"><span data-stu-id="59cfa-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![definir a configuração de projeto](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="59cfa-760">Vá para **menu Build** e clique em **implantar solução** para carregar o aplicativo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="59cfa-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="59cfa-761">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="59cfa-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="59cfa-762">Inicie o aplicativo de realidade misturada, seguido pelo aplicativo da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="59cfa-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="59cfa-763">Com ambos os aplicativos em execução, mova um objeto na cena da área de trabalho (usando o botão esquerdo do Mouse).</span><span class="sxs-lookup"><span data-stu-id="59cfa-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="59cfa-764">Essas alterações posicionais serão feitas localmente, serializadas e enviadas para o serviço de aplicativo de funções.</span><span class="sxs-lookup"><span data-stu-id="59cfa-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="59cfa-765">O serviço de aplicativo de funções, em seguida, atualizará a tabela junto com o Hub de notificação.</span><span class="sxs-lookup"><span data-stu-id="59cfa-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="59cfa-766">Recebeu uma atualização, o Hub de notificação enviará os dados atualizados diretamente para todos os aplicativos registrados (no caso o aplicativo de imersão fone de ouvido), que serão então desserializar os dados de entrada e aplicar os novos dados posicionais para os objetos de local, movendo-os na cena.</span><span class="sxs-lookup"><span data-stu-id="59cfa-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="59cfa-767">A conclusão de seu aplicativo de Hubs de notificação do Azure</span><span class="sxs-lookup"><span data-stu-id="59cfa-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="59cfa-768">Parabéns, você criou um aplicativo de realidade mista que aproveita o serviço de Hubs de notificação do Azure e permitir a comunicação entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="59cfa-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![final do produto-end](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="59cfa-770">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="59cfa-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="59cfa-771">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="59cfa-771">Exercise 1</span></span>

<span data-ttu-id="59cfa-772">Você pode trabalhar como alterar a cor dos GameObjects e enviar essa notificação para outros aplicativos, exibindo a cena?</span><span class="sxs-lookup"><span data-stu-id="59cfa-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="59cfa-773">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="59cfa-773">Exercise 2</span></span>

<span data-ttu-id="59cfa-774">Você pode adicionar o movimento do GameObjects ao seu aplicativo MR e ver a cena atualizada em seu aplicativo da área de trabalho?</span><span class="sxs-lookup"><span data-stu-id="59cfa-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
