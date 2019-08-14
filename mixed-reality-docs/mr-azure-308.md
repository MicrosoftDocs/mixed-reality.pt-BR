---
title: Sr e Azure 308-notificações entre dispositivos
description: Conclua este curso para aprender a implementar hubs de notificação do Azure, Azure Functions e armazenamento e tabelas do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, notificação, funções, tabelas, hubs de notificação, hololens, imersão, VR
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694602"
---
>[!NOTE]
><span data-ttu-id="c4f3e-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c4f3e-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c4f3e-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c4f3e-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c4f3e-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c4f3e-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="c4f3e-110">Sr e Azure 308: Notificações entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="c4f3e-110">MR and Azure 308: Cross-device notifications</span></span>

![início do produto final](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="c4f3e-112">Neste curso, você aprenderá a adicionar recursos de hubs de notificação a um aplicativo de realidade misturada usando os hubs de notificação do Azure, tabelas do Azure e Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="c4f3e-113">Os **hubs de notificação do Azure** são um serviço da Microsoft, que permite aos desenvolvedores enviar notificações por push direcionadas e personalizadas para qualquer plataforma, tudo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="c4f3e-114">Isso pode efetivamente permitir que os desenvolvedores se comuniquem com os usuários finais ou até mesmo se comunicarem entre vários aplicativos, dependendo do cenário.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="c4f3e-115">Para obter mais informações, visite a [página](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview) **hubs de notificação do Azure** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="c4f3e-116">**Azure Functions** é um serviço da Microsoft, que permite aos desenvolvedores executar pequenas partes de código, ' Functions ', no Azure.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="c4f3e-117">Isso fornece uma maneira de delegar trabalho para a nuvem, em vez de seu aplicativo local, que pode ter muitos benefícios.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="c4f3e-118">O **Azure Functions** dá suporte a várias linguagens\#de desenvolvimento\#, incluindo C, F, Node. js, Java e php.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="c4f3e-119">Para obter mais informações, visite a [página](https://docs.microsoft.com/azure/azure-functions/functions-overview) **Azure Functions** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="c4f3e-120">As **tabelas do Azure** são um serviço de nuvem da Microsoft, que permite aos desenvolvedores armazenar dados estruturados não SQL na nuvem, tornando-os facilmente acessíveis em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="c4f3e-121">O serviço apresenta um design sem esquema, permitindo a evolução das tabelas conforme necessário e, portanto, é muito flexível.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="c4f3e-122">Para obter mais informações, visite a [página](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) **tabelas do Azure**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="c4f3e-123">Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada e um aplicativo de PC desktop, que poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="c4f3e-124">O aplicativo de PC Desktop permitirá que o usuário mova um objeto em espaço 2D (X e Y), usando o mouse.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="c4f3e-125">A movimentação de objetos no aplicativo de PC será enviada para a nuvem usando JSON, que estará na forma de uma cadeia de caracteres, contendo uma ID de objeto, tipo e informações de transformação (coordenadas X e Y).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="c4f3e-126">O aplicativo de realidade misturada, que tem uma cena idêntica ao aplicativo da área de trabalho, receberá notificações referentes à movimentação de objetos, do serviço de hubs de notificação (que acabou de ser atualizado pelo aplicativo de PC desktop).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="c4f3e-127">Após receber uma notificação, que conterá a ID do objeto, o tipo e as informações de transformação, o aplicativo de realidade misturada aplicará as informações recebidas à sua própria cena.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="c4f3e-128">Em seu aplicativo, cabe a você como você integrará os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="c4f3e-129">Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="c4f3e-130">É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="c4f3e-131">Este curso é um tutorial independente, que não envolve diretamente nenhum outro laboratório de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="c4f3e-132">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="c4f3e-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c4f3e-133">Course</span><span class="sxs-lookup"><span data-stu-id="c4f3e-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c4f3e-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c4f3e-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c4f3e-135"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="c4f3e-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c4f3e-136">Sr e Azure 308: Notificações entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="c4f3e-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="c4f3e-137">✔️</span><span class="sxs-lookup"><span data-stu-id="c4f3e-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c4f3e-138">✔️</span><span class="sxs-lookup"><span data-stu-id="c4f3e-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="c4f3e-139">Embora este curso se concentre principalmente em fones de ouvido (VR) de realidade mista do Windows, você também pode aplicar o que aprende neste curso ao Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="c4f3e-140">Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="c4f3e-141">Ao usar o HoloLens, você pode notar um eco durante a captura de voz.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c4f3e-142">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c4f3e-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c4f3e-143">Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c4f3e-144">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="c4f3e-145">Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="c4f3e-146">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c4f3e-147">Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)</span><span class="sxs-lookup"><span data-stu-id="c4f3e-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="c4f3e-148">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="c4f3e-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c4f3e-149">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="c4f3e-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c4f3e-150">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="c4f3e-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c4f3e-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c4f3e-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="c4f3e-152">Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="c4f3e-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="c4f3e-153">Acesso à Internet para a instalação do Azure e para acessar os hubs de notificação</span><span class="sxs-lookup"><span data-stu-id="c4f3e-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c4f3e-154">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="c4f3e-154">Before you start</span></span>

- <span data-ttu-id="c4f3e-155">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="c4f3e-156">Você deve ser o proprietário do seu portal do desenvolvedor da Microsoft e seu portal de registro de aplicativo, caso contrário, você não terá permissão para acessar o aplicativo no [capítulo 2](#chapter-2---retrieve-your-new-apps-credentials).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="c4f3e-157">Capítulo 1-criar um aplicativo no portal do desenvolvedor da Microsoft</span><span class="sxs-lookup"><span data-stu-id="c4f3e-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="c4f3e-158">Para usar o serviço de **hubs de notificação do Azure** , você precisará criar um aplicativo no portal do desenvolvedor da Microsoft, pois seu aplicativo precisará ser registrado, para que ele possa enviar e receber notificações.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="c4f3e-159">Faça logon no [portal do desenvolvedor da Microsoft](https://developer.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="c4f3e-160">Você precisará fazer logon em sua conta da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="c4f3e-161">No painel, clique em **criar um novo aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-161">From the Dashboard, click **Create a new app**.</span></span>

    ![Criar um aplicativo](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="c4f3e-163">Um pop-up será exibido, onde você precisa reservar um nome para o novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="c4f3e-164">Na caixa de texto, insira um nome apropriado; Se o nome escolhido estiver disponível, um tique aparecerá à direita da caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="c4f3e-165">Quando você tiver um nome disponível inserido, clique no botão **reservar o nome do produto** na parte inferior esquerda do pop-up.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![inverter um nome](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="c4f3e-167">Com o aplicativo criado agora, você está pronto para ir para o próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="c4f3e-168">Capítulo 2-recuperar suas novas credenciais de aplicativos</span><span class="sxs-lookup"><span data-stu-id="c4f3e-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="c4f3e-169">Faça logon no portal de registro de aplicativo, em que seu novo aplicativo será listado e recupere as credenciais que serão usadas para configurar o **serviço de hubs de notificação** no **portal do Azure**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="c4f3e-170">Navegue até o [portal de registro de aplicativos](http://apps.dev.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![Portal de registro de aplicativos](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="c4f3e-172">Você precisará usar sua conta da Microsoft para fazer logon.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="c4f3e-173">Essa **deve** ser a conta da Microsoft que você usou no [capítulo](#chapter-1---create-an-application-on-the-microsoft-developer-portal)anterior, com o portal do desenvolvedor da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="c4f3e-174">Você encontrará seu aplicativo na seção **meus aplicativos** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="c4f3e-175">Depois de encontrá-lo, clique nele e você será levado para uma nova página que tem o nome do aplicativo e o **registro**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![seu aplicativo recentemente registrado](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="c4f3e-177">Role para baixo na página de registro para localizar a seção **segredos do aplicativo** e o **SID do pacote** para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="c4f3e-178">Copie ambos para uso com a configuração do **serviço de hubs de notificação do Azure** no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![segredos do aplicativo](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="c4f3e-180">Capítulo 3-configurar o portal do Azure: criar serviço de hubs de notificação</span><span class="sxs-lookup"><span data-stu-id="c4f3e-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="c4f3e-181">Com suas credenciais de aplicativos recuperadas, você precisará ir para o portal do Azure, no qual você criará um serviço de hubs de notificação do Azure.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="c4f3e-182">Faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="c4f3e-183">Se você ainda não tiver uma conta do Azure, será necessário criar uma.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c4f3e-184">Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="c4f3e-185">Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure **Hub de notificação**e clique em ***Enter***.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![Pesquisar Hub de notificação](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="c4f3e-187">A palavra ***novo*** pode ter sido substituída por **criar um recurso**, em portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="c4f3e-188">A nova página fornecerá uma descrição do serviço de *hubs de notificação* .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="c4f3e-189">Na parte inferior esquerda desse prompt, selecione o botão **criar** para criar uma associação com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![criar instância de hubs de notificação](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="c4f3e-191">Depois de clicar em ***criar***:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="c4f3e-192">Insira o nome desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="c4f3e-193">Forneça um **namespace** que você poderá associar a este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="c4f3e-194">Selecione um **local.**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="c4f3e-195">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c4f3e-196">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c4f3e-197">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="c4f3e-198">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="c4f3e-199">Selecione uma **assinatura**apropriada.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="c4f3e-200">Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="c4f3e-201">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-201">Select **Create**.</span></span>

        ![detalhes do serviço de preenchimento](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="c4f3e-203">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="c4f3e-204">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notificação](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="c4f3e-206">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="c4f3e-207">Você será levado para sua nova instância de serviço do **Hub de notificação** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![Ir para o recurso](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="c4f3e-209">Na página Visão geral, na metade inferior da página, clique em **Windows (WNS).**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="c4f3e-210">O painel à direita será alterado para mostrar dois campos de texto, que exigem o **SID do pacote** e a **chave de segurança**do aplicativo que você configurou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![serviço de hubs recém-criado](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="c4f3e-212">Depois de copiar os detalhes nos campos corretos, clique em **salvar**e você receberá uma notificação quando o Hub de notificação tiver sido atualizado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![Copiar detalhes de segurança](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="c4f3e-214">Capítulo 4-configurar o portal do Azure: criar serviço de tabela</span><span class="sxs-lookup"><span data-stu-id="c4f3e-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="c4f3e-215">Depois de criar sua instância de serviço de hubs de notificação, navegue de volta para o portal do Azure, onde você criará um serviço de tabelas do Azure criando um recurso de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="c4f3e-216">Se ainda não estiver conectado, faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="c4f3e-217">Depois de conectado, clique em **novo** no canto superior esquerdo e procure **conta de armazenamento**e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="c4f3e-218">A palavra ***novo*** pode ter sido substituída por **criar um recurso**, em portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="c4f3e-219">Selecione **conta de armazenamento-BLOB, arquivo, tabela, fila** na lista.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Pesquisar conta de armazenamento](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="c4f3e-221">A nova página fornecerá uma descrição do serviço de **conta de armazenamento** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="c4f3e-222">Na parte inferior esquerda deste prompt, selecione o botão **criar** para criar uma instância desse serviço.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![criar instância de armazenamento](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="c4f3e-224">Depois de clicar em **criar**, um painel será exibido:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="c4f3e-225">Insira o **nome** desejado para esta instância de serviço (deve estar em letras minúsculas).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="c4f3e-226">Para **modelo de implantação**, clique em **Gerenciador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="c4f3e-227">Para **tipo de conta**, usando o menu suspenso, selecione **armazenamento (uso geral v1)** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="c4f3e-228">Selecione um **local**apropriado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="c4f3e-229">Para o menu suspenso **replicação** , selecione **armazenamento com redundância geográfica e acesso de leitura (ra-grs)** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="c4f3e-230">Para **desempenho**, clique em **padrão**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="c4f3e-231">Na seção **transferência segura necessária** , selecione **desabilitado**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="c4f3e-232">No menu suspenso **assinatura** , selecione uma assinatura apropriada.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="c4f3e-233">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c4f3e-234">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c4f3e-235">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="c4f3e-236">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="c4f3e-237">Deixe as **redes virtuais** como **desabilitadas** se essa for uma opção para você.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="c4f3e-238">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-238">Click **Create**.</span></span>

        ![preencher detalhes do armazenamento](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="c4f3e-240">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="c4f3e-241">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="c4f3e-242">Clique nas notificações para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-242">Click on the notifications to explore your new Service instance.</span></span>

    ![Nova notificação de armazenamento](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="c4f3e-244">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="c4f3e-245">Você será levado para sua página de visão geral da nova instância do serviço de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![Ir para o recurso](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="c4f3e-247">Na página Visão geral, no lado direito, clique em **tabelas**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="c4f3e-248">O painel à direita será alterado para mostrar as informações do **serviço tabela** , onde você precisa adicionar uma nova tabela.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="c4f3e-249">Para fazer isso, clique **+** no botão **tabela** no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![Abrir tabelas](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="c4f3e-251">Uma nova página será mostrada, onde você precisa inserir um nome de **tabela**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="c4f3e-252">Esse é o nome que você usará para se referir aos dados em seu aplicativo em capítulos posteriores.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="c4f3e-253">Insira um nome apropriado e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-253">Insert an appropriate name and click **OK**.</span></span>

    ![criar nova tabela](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="c4f3e-255">Depois que a nova tabela tiver sido criada, você poderá vê-la na página de **serviço tabela** (na parte inferior).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![nova tabela criada](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="c4f3e-257">Capítulo 5 – concluindo a tabela do Azure no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c4f3e-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="c4f3e-258">Agora que a conta de armazenamento do **serviço de tabela** foi configurada, é hora de adicionar dados a ela, que será usada para armazenar e recuperar informações.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="c4f3e-259">A edição das tabelas pode ser feita por meio do **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="c4f3e-260">Abra o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="c4f3e-261">No menu, clique em **Exibir** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![abrir o Cloud Explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="c4f3e-263">O **Cloud Explorer** será aberto como um item encaixado (seja paciente, pois o carregamento pode levar tempo).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="c4f3e-264">Se a assinatura que você usou para criar suas *contas de armazenamento* não estiver visível, verifique se você tem:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="c4f3e-265">Conectado à mesma conta que você usou para o portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="c4f3e-266">Selecione sua assinatura na página de gerenciamento de conta (talvez seja necessário aplicar um filtro de suas configurações de conta):</span><span class="sxs-lookup"><span data-stu-id="c4f3e-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![Localizar assinatura](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="c4f3e-268">Os serviços de nuvem do Azure serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="c4f3e-269">Localize **contas de armazenamento** e clique na seta à esquerda dela para expandir suas contas.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![abrir contas de armazenamento](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="c4f3e-271">Uma vez expandido, sua **conta de armazenamento** recém-criada deve estar disponível.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="c4f3e-272">Clique na seta à esquerda do armazenamento e, depois de expandida, localize as **tabelas** e clique na seta ao lado dela para revelar a **tabela** que você criou no último capítulo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="c4f3e-273">Clique duas vezes em sua **tabela**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-273">Double click your **Table**.</span></span>

    ![Abrir tabela de objetos de cena](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="c4f3e-275">Sua tabela será aberta no centro da janela do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="c4f3e-276">Clique no ícone de tabela com **+** o (mais) nele.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![Adicionar nova tabela](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="c4f3e-278">Uma janela será exibida solicitando que você *adicione a entidade*.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="c4f3e-279">Você criará três entidades no total, cada uma com várias propriedades.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="c4f3e-280">Você observará que *PartitionKey* e *RowKey* já foram fornecidos, pois eles são usados pela tabela para localizar seus dados.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![partição e chave de linha](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="c4f3e-282">Atualize o *valor* de **PartitionKey** e **RowKey** da seguinte maneira (Lembre-se de fazer isso para cada propriedade de linha que você adicionar, ao mesmo tempo em que incrementa o RowKey a cada vez):</span><span class="sxs-lookup"><span data-stu-id="c4f3e-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![Adicionar valores corretos](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="c4f3e-284">Clique em **Adicionar Propriedade** para adicionar linhas extras de dados.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="c4f3e-285">Faça sua primeira tabela vazia corresponder à tabela abaixo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="c4f3e-286">Clique em **OK** quando terminar.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-286">Click **OK** when you are finished.</span></span>

    ![clique em OK quando terminar](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="c4f3e-288">Verifique se você alterou o **tipo** das entradas **X**, **Y**e **Z**para **Double**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="c4f3e-289">Você notará que a tabela agora tem uma linha de dados.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="c4f3e-290">Clique no **+** ícone (mais) novamente para adicionar outra entidade.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![primeira linha](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="c4f3e-292">Crie uma propriedade adicional e, em seguida, defina os valores da nova entidade para que correspondam às mostradas abaixo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![Adicionar cubo](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="c4f3e-294">Repita a última etapa para adicionar outra entidade.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="c4f3e-295">Defina os valores dessa entidade como os mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-295">Set the values for this entity to those shown below.</span></span>

    ![Adicionar cilindro](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="c4f3e-297">Agora, sua tabela deve ser parecida com a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-297">Your table should now look like the one below.</span></span>

    ![tabela concluída](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="c4f3e-299">Você concluiu este capítulo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-299">You have completed this Chapter.</span></span> <span data-ttu-id="c4f3e-300">Certifique-se de salvar.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="c4f3e-301">Capítulo 6-criar uma Aplicativo de funções do Azure</span><span class="sxs-lookup"><span data-stu-id="c4f3e-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="c4f3e-302">Crie uma Aplicativo de funções do Azure, que será chamada pelo aplicativo da área de trabalho para atualizar o serviço **tabela** e enviar uma notificação por meio do **Hub de notificação**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="c4f3e-303">Primeiro, você precisa criar um arquivo que permitirá que o Azure function carregue as bibliotecas necessárias.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="c4f3e-304">Abra o **bloco de notas** (pressione a tecla Windows e digite notepad).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![abrir bloco de notas](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="c4f3e-306">Com o bloco de notas aberto, insira a estrutura JSON abaixo dele.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="c4f3e-307">Depois de fazer isso, salve-o em sua área de trabalho como **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="c4f3e-308">É importante que a nomenclatura esteja correta: Verifique se ela **não tem uma extensão de arquivo. txt** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="c4f3e-309">Esse arquivo define as bibliotecas que sua função usará, se você tiver usado o NuGet, parecerá familiar.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

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

3.  <span data-ttu-id="c4f3e-310">Faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="c4f3e-311">Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure **aplicativo de funções**, pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![Pesquisar o aplicativo de funções](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="c4f3e-313">A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="c4f3e-314">A nova página fornecerá uma descrição do serviço **aplicativo de funções** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="c4f3e-315">Na parte inferior esquerda desse prompt, selecione o botão **criar** para criar uma associação com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![instância do aplicativo de funções](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="c4f3e-317">Depois de clicar em **criar**, preencha o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="c4f3e-318">Para **nome do aplicativo**, insira o nome desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="c4f3e-319">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="c4f3e-320">Selecione o tipo de preço apropriado para você, se esta for a primeira vez que criar um **serviço de aplicativo de funções**, uma camada gratuita deverá estar disponível para você.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="c4f3e-321">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c4f3e-322">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c4f3e-323">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="c4f3e-324">Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="c4f3e-325">Para o **sistema operacional**, clique em Windows, pois essa é a plataforma pretendida.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="c4f3e-326">Selecione um **plano de hospedagem** (este tutorial está usando um **plano de consumo**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="c4f3e-327">Selecione um **local** **(escolha o mesmo local do armazenamento que você criou na etapa anterior)**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="c4f3e-328">Para a seção de **armazenamento** , **você deve selecionar o serviço de armazenamento criado na etapa anterior**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="c4f3e-329">Você não precisará de *Application insights* neste aplicativo, portanto, fique à vontade para deixá-lo **desativado**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="c4f3e-330">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-330">Click **Create**.</span></span>

        ![criar nova instância](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="c4f3e-332">Depois de clicar em **criar** , você precisará aguardar a criação do serviço; isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="c4f3e-333">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Nova notificação](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="c4f3e-335">Clique nas notificações para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="c4f3e-336">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Ir para o recurso](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="c4f3e-338">Clique no **+** ícone (mais) ao lado de *funções*, para *criar novo*.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![Adicionar nova função](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="c4f3e-340">No painel central, a janela de criação da **função** será exibida.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="c4f3e-341">Ignore as informações na metade superior do painel e clique em **função personalizada**, que está localizada próximo à parte inferior (na área azul, como abaixo).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![função personalizada](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="c4f3e-343">A nova página dentro da janela mostrará vários tipos de função.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="c4f3e-344">Role para baixo para exibir os tipos roxos e clique no elemento **http Put** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![link http put](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="c4f3e-346">Talvez você precise rolar mais para baixo na página (e essa imagem pode não parecer exatamente a mesma, se as atualizações do portal do Azure tiverem sido realizadas), no entanto, você está procurando um elemento chamado *http Put*.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="c4f3e-347">A janela **http Put** será exibida, na qual você precisa configurar a função (veja abaixo para obter a imagem).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="c4f3e-348">Para **idioma,** usando o menu suspenso, selecione C\#.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="c4f3e-349">Para **nome,** Insira um nome apropriado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="c4f3e-350">No menu suspenso **nível de autenticação** , selecione **função**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="c4f3e-351">Para a seção **nome da tabela** , você precisa usar o nome exato usado para criar o serviço **tabela** anteriormente (incluindo o mesmo caso de letra).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="c4f3e-352">Na seção **conexão da conta de armazenamento** , use o menu suspenso e selecione sua conta de armazenamento a partir daí.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="c4f3e-353">Se não estiver lá, clique no **novo** hiperlink junto com o título da seção, para mostrar outro painel, em que sua conta de armazenamento deve ser listada.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![novo armazenamento](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="c4f3e-355">Clique em **criar** e você receberá uma notificação informando que suas configurações foram atualizadas com êxito.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![criar função](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="c4f3e-357">Depois de clicar em **criar**, você será redirecionado para o editor de funções.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![atualizar código de função](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="c4f3e-359">Insira o código a seguir no editor de função (substituindo o código na função):</span><span class="sxs-lookup"><span data-stu-id="c4f3e-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

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
    > <span data-ttu-id="c4f3e-360">Usando as bibliotecas incluídas, a função recebe o nome e o local do objeto que foi movido na cena do Unity (como um C# objeto, chamado **UnityGameObject**).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="c4f3e-361">Esse objeto é usado para atualizar os parâmetros de objeto na tabela criada.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="c4f3e-362">Depois disso, a função faz uma chamada para o serviço de Hub de notificação criado, que notifica todos os aplicativos assinados.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="c4f3e-363">Com o código em vigor, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="c4f3e-364">Em seguida, clique **\<** no ícone (seta), no lado direito da página.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![Abrir painel de carregamento](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="c4f3e-366">Um painel será deslizado da direita.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-366">A panel will slide in from the right.</span></span> <span data-ttu-id="c4f3e-367">Nesse painel, clique em **carregar**e um navegador de arquivos será exibido.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="c4f3e-368">Navegue até e clique no arquivo **Project. JSON** , que você criou anteriormente no **bloco de notas** e, em seguida, clique no botão **abrir** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="c4f3e-369">Esse arquivo define as bibliotecas que sua função usará.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-369">This file defines the libraries that your function will use.</span></span>

    ![carregar JSON](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="c4f3e-371">Quando o arquivo for carregado, ele será exibido no painel à direita.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="c4f3e-372">Clicar nele irá abri-lo no editor de **funções** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="c4f3e-373">Ele deve ser **exatamente** o mesmo que a próxima imagem (abaixo da etapa 23).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="c4f3e-374">Em seguida, no painel à esquerda, abaixo de **funções**, clique no link **integrar** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![função de integração](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="c4f3e-376">Na página seguinte, no canto superior direito, clique em **Editor avançado** (como abaixo).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![abrir editor avançado](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="c4f3e-378">Um arquivo **Function. JSON** será aberto no painel central, que precisa ser substituído pelo seguinte trecho de código.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="c4f3e-379">Isso define a função que você está criando e os parâmetros passados para a função.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-379">This defines the function you are building and the parameters passed into the function.</span></span>

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

26. <span data-ttu-id="c4f3e-380">O editor agora deve se parecer com a imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-380">Your editor should now look like the image below:</span></span>

    ![voltar ao editor padrão](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="c4f3e-382">Você pode observar que os parâmetros de entrada que você acabou de inserir podem não corresponder aos detalhes da tabela e do armazenamento e, portanto, precisarão ser atualizados com suas informações.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="c4f3e-383">Não **faça isso aqui**, pois ele será abordado a seguir.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="c4f3e-384">Basta clicar no link **editor padrão** , no canto superior direito da página, para voltar.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="c4f3e-385">De volta ao **editor padrão**, clique em **armazenamento de tabela do Azure (tabela)** , em **entradas**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![Entradas de tabela](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="c4f3e-387">Garanta a seguinte correspondência com **suas** informações, pois elas podem ser diferentes (há uma imagem abaixo das seguintes etapas):</span><span class="sxs-lookup"><span data-stu-id="c4f3e-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="c4f3e-388">**Nome da tabela**: o nome da tabela que você criou em seu armazenamento do Azure, serviço de tabelas.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="c4f3e-389">**Conexão da conta de armazenamento:** clique em **novo**, que aparece junto com o menu suspenso, e um painel será exibido à direita da janela.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![novo armazenamento](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="c4f3e-391">Selecione sua **conta de armazenamento**, que você criou anteriormente para hospedar os **aplicativos de funções.**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="c4f3e-392">Você observará que o valor de conexão da **conta de armazenamento** foi criado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="c4f3e-393">Certifique-se de pressionar **salvar** quando terminar.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="c4f3e-394">A página de **entradas** agora deve corresponder à mostrada abaixo, mostrando **suas** informações.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![entradas concluídas](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="c4f3e-396">Em seguida, clique em **Hub de notificação do Azure (notificação)** -em **saídas**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="c4f3e-397">Verifique se os itens a seguir correspondem às **suas** informações, pois podem ser diferentes (há uma imagem abaixo das seguintes etapas):</span><span class="sxs-lookup"><span data-stu-id="c4f3e-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="c4f3e-398">**Nome do hub de notificação**: Este é o nome da sua instância de serviço do **Hub de notificação** , que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="c4f3e-399">**Conexão de namespace de hubs de notificação**: clique em **novo**, que aparece junto com o menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![verificar saídas](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="c4f3e-401">O pop-up de **conexão** será exibido (consulte a imagem abaixo), onde você precisa selecionar o **namespace** do **Hub de notificação**, que você configurou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="c4f3e-402">Selecione o nome do **Hub de notificação** no menu suspenso central.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="c4f3e-403">Defina o menu suspenso **política** como **DefaultFullSharedAccessSignature**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="c4f3e-404">Clique no botão **selecionar** para voltar.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-404">Click the **Select** button to go back.</span></span>

        ![atualização de saída](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="c4f3e-406">A página de **saídas** agora deve corresponder à mostrada abaixo, mas com **suas** informações.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="c4f3e-407">Certifique-se de pressionar **salvar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="c4f3e-408">*Não edite o nome do hub de notificação diretamente* (isso deve ser feito usando o **Editor avançado**, desde que você tenha seguido as etapas anteriores corretamente.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![saídas concluídas](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="c4f3e-410">Neste ponto, você deve testar a função para garantir que ela esteja funcionando.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="c4f3e-411">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-411">To do this:</span></span> 

    1. <span data-ttu-id="c4f3e-412">Navegue até a página de função mais uma vez:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-412">Navigate to the function page once more:</span></span>

        ![saídas concluídas](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="c4f3e-414">De volta à página função, clique na guia **teste** no canto mais à direita da página para abrir a folha *teste* :</span><span class="sxs-lookup"><span data-stu-id="c4f3e-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![saídas concluídas](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="c4f3e-416">Na caixa de texto **corpo da solicitação** da folha, Cole o código abaixo:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

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

    4. <span data-ttu-id="c4f3e-417">Com o código de teste em vigor, clique no botão **executar** na parte inferior direita e o teste será executado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="c4f3e-418">Os logs de saída do teste serão exibidos na área do console, abaixo do seu código de função.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![saídas concluídas](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="c4f3e-420">Se o teste acima falhar, você precisará verificar se você seguiu as etapas acima exatamente, principalmente as configurações no **painel integrar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="c4f3e-421">Capítulo 7-configurar o projeto de desktop Unity</span><span class="sxs-lookup"><span data-stu-id="c4f3e-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4f3e-422">O aplicativo de área de trabalho que você está criando agora **não** funcionará no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="c4f3e-423">Ele precisa ser executado fora do editor, seguindo a compilação do aplicativo, usando o Visual Studio (ou o aplicativo implantado).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="c4f3e-424">Veja a seguir uma configuração típica para o desenvolvimento com o Unity e a realidade misturada e, como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="c4f3e-425">Configure e teste seu headset de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="c4f3e-426">Você **não** precisará de controladores de animação para este curso.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="c4f3e-427">Se você precisar de suporte para configurar o headset de imersão, siga este [link sobre como configurar a realidade mista do Windows](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="c4f3e-428">Abra o **Unity** e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-428">Open **Unity** and click **New**.</span></span>

    ![novo projeto do Unity](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="c4f3e-430">Você precisa fornecer um nome de projeto de Unity, inserir **UnityDesktopNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="c4f3e-431">Verifique se o tipo de projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="c4f3e-432">Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c4f3e-433">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-433">Then, click **Create project**.</span></span>

    ![Criar projeto](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="c4f3e-435">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="c4f3e-436">Vá para **Editar** > **preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="c4f3e-437">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="c4f3e-438">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-438">Close the **Preferences** window.</span></span>

    ![definir ferramentas VS externas](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="c4f3e-440">Em seguida, vá para **arquivo** > **configurações de compilação** e selecione **plataforma universal do Windows**, em seguida, clique no botão **alternar plataforma** para aplicar sua seleção.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![alternar plataformas](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="c4f3e-442">Ainda em**configurações de compilação**de **arquivo** > , verifique se:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="c4f3e-443">O **dispositivo de destino** está definido para **qualquer dispositivo**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="c4f3e-444">Esse aplicativo será para sua área de trabalho, portanto, deve ser **qualquer dispositivo**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="c4f3e-445">O **tipo de compilação** está definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="c4f3e-446">O **SDK** está definido para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="c4f3e-447">A **versão do Visual Studio** está definida para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="c4f3e-448">**Compilar e executar** é definido como **computador local**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="c4f3e-449">Enquanto isso, vale a pena salvar a cena e adicioná-la à compilação.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="c4f3e-450">Faça isso selecionando **Adicionar abrir cenas**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="c4f3e-451">Uma janela salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-451">A save window will appear.</span></span>

            ![Adicionar cenas abertas](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="c4f3e-453">Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![nova pasta de cenas](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="c4f3e-455">Abra sua pasta de **cenas** recém-criada e, em seguida, no campo **nome do arquivo:** texto, digite **cena do\_NH desktop\_** e, em seguida, pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![novo NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="c4f3e-457">As configurações restantes, em **configurações de compilação**, devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="c4f3e-458">Na mesma janela, clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o **Inspetor** está localizado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="c4f3e-459">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="c4f3e-460">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="c4f3e-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="c4f3e-461">A **versão de tempo de execução de script** deve ser **Experimental (.NET 4,6 equivalente)**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="c4f3e-462">O **back-end de script** deve ser **.net**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="c4f3e-463">O **nível de compatibilidade da API** deve ser **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![versão do 4,6 net](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="c4f3e-465">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="c4f3e-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-466">**InternetClient**</span></span>

            ![cliente de Internet em escala](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="c4f3e-468">De volta às **configurações de compilação** , projetos do *Unity C\#*  não ficam mais esmaecidos; marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="c4f3e-469">Feche a janela **configurações de compilação** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="c4f3e-470">Salve sua cena e **arquivo** > de projeto**salvar cena/arquivo** > **salvar projeto**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="c4f3e-471">Se você quiser ignorar o componente de *configuração do Unity* para este projeto (aplicativo de desktop) e continuar diretamente no código, fique à vontade para baixá-lo [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importe-o para seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue do [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="c4f3e-472">Ainda será necessário adicionar os componentes de script.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="c4f3e-473">Capítulo 8-importando as DLLs no Unity</span><span class="sxs-lookup"><span data-stu-id="c4f3e-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="c4f3e-474">Você usará o armazenamento do Azure para Unity (que, por sua vez, utiliza o SDK do .net para o Azure).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="c4f3e-475">Para obter mais informações, siga este [link sobre o armazenamento do Azure para Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="c4f3e-476">Atualmente, há um problema conhecido no Unity que exige que os plugins sejam reconfigurados após a importação.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="c4f3e-477">Essas etapas (4-7 nesta seção) não serão mais necessárias depois que o bug for resolvido.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="c4f3e-478">Para importar o SDK para seu próprio projeto, certifique-se de ter baixado o [ **. unitypackage**](https://aka.ms/azstorage-unitysdk) mais recente do github.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="c4f3e-479">Em seguida, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-479">Then, do the following:</span></span>

1.  <span data-ttu-id="c4f3e-480">Adicione o **. unitypackage** ao Unity usando a opção de menu **pacote \> personalizado do pacote de \> importação de ativos** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="c4f3e-481">Na caixa **Importar pacote de Unity** que é exibida, você pode selecionar tudo em **plugin**\> **armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="c4f3e-482">Desmarque todas as outras opções, pois elas não são necessárias para este curso.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![importar para pacote](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="c4f3e-484">Clique no botão ***importar*** para adicionar os itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="c4f3e-485">Vá para a pasta **armazenamento** em **plug-ins** na exibição do projeto e selecione os seguintes plugins *somente*:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="c4f3e-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="c4f3e-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="c4f3e-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="c4f3e-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="c4f3e-488">Microsoft. WindowsAzure. Storage</span><span class="sxs-lookup"><span data-stu-id="c4f3e-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="c4f3e-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="c4f3e-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="c4f3e-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="c4f3e-490">System.Spatial</span></span>

![desmarcar qualquer plataforma](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="c4f3e-492">Com *esses plugins específicos* selecionados, **desmarque** **qualquer plataforma** e **desmarque** **WSAPlayer** e clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![aplicar DLLs de plataforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="c4f3e-494">Estamos marcando esses plugins específicos para serem usados apenas no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="c4f3e-495">Isso ocorre porque há diferentes versões dos mesmos plug-ins na pasta WSA que serão usados depois que o projeto for exportado do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="c4f3e-496">Na pasta plug-in de **armazenamento** , selecione somente:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="c4f3e-497">Microsoft. Data. Services. Client</span><span class="sxs-lookup"><span data-stu-id="c4f3e-497">Microsoft.Data.Services.Client</span></span>

        ![definir não processar para DLLs](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="c4f3e-499">Marque a caixa **não processar** em **configurações da plataforma** e clique em ***aplicar***.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![aplicar nenhum processamento](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="c4f3e-501">Estamos marcando este plug-in "não processar", porque o assembly do Unity Patcher tem dificuldade para processar esse plug-in.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="c4f3e-502">O plug-in ainda funcionará, embora não seja processado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="c4f3e-503">Capítulo 9-criar a classe TableToScene no projeto de desktop Unity</span><span class="sxs-lookup"><span data-stu-id="c4f3e-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="c4f3e-504">Agora você precisa criar os scripts que contêm o código para executar este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="c4f3e-505">O primeiro script que você precisa criar é **TableToScene**, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="c4f3e-506">Lendo entidades na tabela do Azure.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="c4f3e-507">Usando os dados da tabela, determine quais objetos gerar e em qual posição.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="c4f3e-508">O segundo script que você precisa criar é **CloudScene**, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="c4f3e-509">Registrando o evento de clique com o botão esquerdo, para permitir que o usuário arraste objetos em volta da cena.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="c4f3e-510">Serializar os dados de objeto desta cena do Unity e enviá-los para o Aplicativo de funções do Azure.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="c4f3e-511">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-511">To create this class:</span></span>

1.  <span data-ttu-id="c4f3e-512">Clique com o botão direito do mouse na pasta de **ativos** localizada no painel projeto, **crie** > a**pasta**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="c4f3e-513">Nomeie a pasta **scripts**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-513">Name the folder **Scripts**.</span></span>

    ![criar pasta de scripts](images/AzureLabs-Lab8-66.png)

    ![criar a pasta de scripts 2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="c4f3e-516">Clique duas vezes na pasta recém-criada para abri-la.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="c4f3e-517">Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="c4f3e-518">Nomeie o script **TableToScene**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="c4f3e-519">![novo script](images/AzureLabs-Lab8-68.png)
    ![c# TableToScene renomear](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="c4f3e-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="c4f3e-520">Clique duas vezes no script para abri-lo no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="c4f3e-521">Adicione os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="c4f3e-522">Dentro da classe, insira as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-522">Within the class, insert the following variables:</span></span>

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
    > <span data-ttu-id="c4f3e-523">Substitua o valor **accountName** pelo nome do serviço de armazenamento do Azure e pelo valor de **accountKey** pelo valor de chave encontrado no serviço de armazenamento do Azure, no portal do Azure (consulte a imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![buscar chave de conta](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="c4f3e-525">Agora, adicione os métodos **Start ()** e **ativo ()** para inicializar a classe.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

8.  <span data-ttu-id="c4f3e-526">Dentro da classe **TableToScene** , adicione o método que recuperará os valores da tabela do Azure e use-os para gerar os primitivos apropriados na cena.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

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

9.  <span data-ttu-id="c4f3e-527">Fora da classe **TableToScene** , você precisa definir a classe usada pelo aplicativo para serializar e desserializar as **entidades de tabela**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

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

10. <span data-ttu-id="c4f3e-528">Certifique-se de **salvar** antes de voltar para o editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="c4f3e-529">Clique na **câmera principal** do painel **hierarquia** , para que suas propriedades apareçam no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="c4f3e-530">Com a pasta **scripts** aberta, selecione o **arquivo script TableToScene** e arraste-o para a **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="c4f3e-531">O resultado deve ser o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-531">The result should be as below:</span></span>

    ![Adicionar script à câmera principal](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="c4f3e-533">Capítulo 10 – criar a classe CloudScene no projeto de desktop Unity</span><span class="sxs-lookup"><span data-stu-id="c4f3e-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="c4f3e-534">O segundo script que você precisa criar é **CloudScene**, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="c4f3e-535">Registrando o evento de clique com o botão esquerdo, para permitir que o usuário arraste objetos em volta da cena.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="c4f3e-536">Serializar os dados de objeto desta cena do Unity e enviá-los para o Aplicativo de funções do Azure.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="c4f3e-537">Para criar o segundo script:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-537">To create the second script:</span></span>

1.  <span data-ttu-id="c4f3e-538">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar**, **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="c4f3e-539">Nomeie o script **CloudScene**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="c4f3e-540">![novo script](images/AzureLabs-Lab8-72.png)
    ![c# renomear CloudScene](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="c4f3e-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="c4f3e-541">Adicione os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="c4f3e-542">Insira as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-542">Insert the following variables:</span></span>

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

4.  <span data-ttu-id="c4f3e-543">Substitua o valor **azureFunctionEndpoint** pela URL de aplicativo de funções do Azure encontrada no serviço de aplicativo de funções do Azure, no portal do Azure, conforme mostrado na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![Obter URL da função](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="c4f3e-545">Agora, adicione os métodos **Start ()** e **ativo ()** para inicializar a classe.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

6.  <span data-ttu-id="c4f3e-546">Dentro do método **Update ()** , adicione o seguinte código que irá detectar a entrada do mouse e arrastar, que, por sua vez, moverá Gameobjects na cena.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="c4f3e-547">Se o usuário tiver arrastado e descartado um objeto, ele passará o nome e as coordenadas do objeto para o método **UpdateCloudScene ()** , que chamará o serviço de aplicativo de funções do Azure, que atualizará a tabela do Azure e disparará a notificação.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

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

7.  <span data-ttu-id="c4f3e-548">Agora, adicione o método **UpdateCloudScene ()** , como abaixo:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

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

8.  <span data-ttu-id="c4f3e-549">Salve o código e retorne ao Unity</span><span class="sxs-lookup"><span data-stu-id="c4f3e-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="c4f3e-550">Arraste o script **CloudScene** para a **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="c4f3e-551">Clique na **câmera principal** do painel **hierarquia** , para que suas propriedades apareçam no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="c4f3e-552">Com a pasta **scripts** aberta, selecione o script **CloudScene** e arraste-o para a **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="c4f3e-553">O resultado deve ser o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-553">The result should be as below:</span></span>

        > ![Arraste o script de nuvem para a câmera principal](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="c4f3e-555">Capítulo 11-criar o projeto de desktop para UWP</span><span class="sxs-lookup"><span data-stu-id="c4f3e-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="c4f3e-556">Tudo o que é necessário para a seção do Unity deste projeto foi concluído.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="c4f3e-557">Navegue até **configurações de compilação** (**configurações de compilação**de**arquivo** > ).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="c4f3e-558">Na janela **configurações de compilação** , clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-558">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilar projeto](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="c4f3e-560">Uma janela do **Explorador de arquivos** será Popup, solicitando um local para compilar.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="c4f3e-561">Crie uma nova pasta (clicando em **nova pasta** no canto superior esquerdo) e nomeie-a como **Build**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![nova pasta para compilação](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="c4f3e-563">Abra a nova pasta builds e crie outra pasta (usando a **nova pasta** mais uma vez) e nomeie-a **\_NH desktop\_app**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![nome da pasta NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="c4f3e-565">Com o **aplicativo\_de\_área de trabalho NH** selecionado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="c4f3e-566">Clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-566">click **Select Folder**.</span></span> <span data-ttu-id="c4f3e-567">O projeto levará um minuto ou mais para ser compilado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="c4f3e-568">Após a compilação, o **Explorador de arquivos** aparecerá mostrando o local do novo projeto.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="c4f3e-569">No entanto, não é necessário abri-lo, pois você precisa criar o outro projeto do Unity primeiro, nos próximos capítulos.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="c4f3e-570">Capítulo 12-configurar o projeto de Unity da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c4f3e-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="c4f3e-571">A seguir está uma configuração típica para o desenvolvimento com a realidade misturada e, como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="c4f3e-572">Abra o **Unity** e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-572">Open **Unity** and click **New**.</span></span>

    ![novo projeto do Unity](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="c4f3e-574">Agora, você precisará fornecer um nome de projeto de Unity, inserir **UnityMRNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="c4f3e-575">Verifique se o tipo de projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="c4f3e-576">Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c4f3e-577">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-577">Then, click **Create project**.</span></span>

    ![nome UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="c4f3e-579">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="c4f3e-580">Vá para **Editar** > **preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="c4f3e-581">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="c4f3e-582">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-582">Close the **Preferences** window.</span></span>

    ![definir editor externo como VS](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="c4f3e-584">Em seguida, vá para **arquivo** > **configurações de compilação** e alterne a plataforma para **plataforma universal do Windows**, clicando no botão **alternar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![alternar plataformas para UWP](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="c4f3e-586">Vá para **arquivo** > **configurações de compilação** e verifique se:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="c4f3e-587">O **dispositivo de destino** está definido para **qualquer dispositivo**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="c4f3e-588">Para o Microsoft HoloLens, defina o **dispositivo de destino** como *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="c4f3e-589">O **tipo de compilação** está definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="c4f3e-590">O **SDK** está definido para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="c4f3e-591">A **versão do Visual Studio** está definida para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="c4f3e-592">**Compilar e executar** é definido como **computador local**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="c4f3e-593">Enquanto isso, vale a pena salvar a cena e adicioná-la à compilação.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="c4f3e-594">Faça isso selecionando **Adicionar abrir cenas**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="c4f3e-595">Uma janela salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-595">A save window will appear.</span></span>

            ![Adicionar cenas abertas](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="c4f3e-597">Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![nova pasta de cenas](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="c4f3e-599">Abra sua pasta de **cenas** recém-criada e, em seguida, no campo **nome do arquivo:** texto, digite **\_NH Mr\_Scene**e pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![nova cena-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="c4f3e-601">As configurações restantes, em **configurações de compilação**, devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="c4f3e-602">Na mesma janela, clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o **Inspetor** está localizado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![abrir configurações do Player](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="c4f3e-604">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="c4f3e-605">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="c4f3e-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="c4f3e-606">A **versão de tempo de execução de script** deve ser **Experimental** (.NET 4,6 equivalente)</span><span class="sxs-lookup"><span data-stu-id="c4f3e-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="c4f3e-607">O **back-end de script** deve ser ***.net***</span><span class="sxs-lookup"><span data-stu-id="c4f3e-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="c4f3e-608">O **nível de compatibilidade da API** deve ser **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![compatibilidade de API](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="c4f3e-610">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o SDK do **Windows Mixed Reality** foi adicionado</span><span class="sxs-lookup"><span data-stu-id="c4f3e-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![configurações de atualização XR](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="c4f3e-612">Na guia **configurações de publicação** , em **recursos**, verificar:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="c4f3e-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="c4f3e-613">**InternetClient**</span></span>           

            ![cliente de Internet em escala](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="c4f3e-615">De volta às **configurações de compilação**, os projetos de **Unity C#**  não ficam mais esmaecidos: marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="c4f3e-616">Com essas alterações feitas, feche a janela configurações de compilação.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="c4f3e-617">Salve sua cena e **arquivo** > de projeto**salvar cena/arquivo** > **salvar projeto**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="c4f3e-618">Se você quiser ignorar o componente de *configuração do Unity* para este projeto (aplicativo de realidade misturada) e continuar diretamente no código, fique à vontade para baixá-lo [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importe-o para seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue de [ Capítulo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="c4f3e-619">Ainda será necessário adicionar os componentes de script.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="c4f3e-620">Capítulo 13-importando as DLLs no projeto de Unity da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c4f3e-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="c4f3e-621">Você usará o armazenamento do Azure para biblioteca do Unity (que usa o SDK do .net para Azure).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="c4f3e-622">Siga este [link sobre como usar o armazenamento do Azure com o Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="c4f3e-623">Atualmente, há um problema conhecido no Unity que exige que os plugins sejam reconfigurados após a importação.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="c4f3e-624">Essas etapas (4-7 nesta seção) não serão mais necessárias depois que o bug for resolvido.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="c4f3e-625">Para importar o SDK para seu próprio projeto, certifique-se de ter baixado o [. unitypackage](https://aka.ms/azstorage-unitysdk)mais recente.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="c4f3e-626">Em seguida, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-626">Then, do the following:</span></span>

1.  <span data-ttu-id="c4f3e-627">Adicione o. unitypackage que você baixou do, para o Unity usando a opção de menu**pacote personalizado** de**importação** > de **ativos** > .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="c4f3e-628">Na caixa **Importar pacote de Unity** que aparece, você pode selecionar tudo em**armazenamento**de **plug-in** > .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![Importar pacote](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="c4f3e-630">Clique no botão **importar** para adicionar os itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="c4f3e-631">Vá para a pasta **armazenamento** em **plug-ins** na exibição do projeto e selecione os seguintes plugins *somente*:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="c4f3e-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="c4f3e-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="c4f3e-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="c4f3e-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="c4f3e-634">Microsoft. WindowsAzure. Storage</span><span class="sxs-lookup"><span data-stu-id="c4f3e-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="c4f3e-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="c4f3e-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="c4f3e-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="c4f3e-636">System.Spatial</span></span>

    ![selecionar plug-ins](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="c4f3e-638">Com *esses plugins específicos* selecionados, **desmarque** **qualquer plataforma** e **desmarque** **WSAPlayer** e clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![aplicar alterações de plataforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="c4f3e-640">Você está marcando esses plugins específicos para serem usados apenas no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="c4f3e-641">Isso ocorre porque há diferentes versões dos mesmos plug-ins na pasta WSA que serão usados depois que o projeto for exportado do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="c4f3e-642">Na pasta plug-in de **armazenamento** , selecione somente:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="c4f3e-643">Microsoft. Data. Services. Client</span><span class="sxs-lookup"><span data-stu-id="c4f3e-643">Microsoft.Data.Services.Client</span></span>

        ![selecionar cliente de serviços de dados](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="c4f3e-645">Marque a caixa **não processar** em **configurações da plataforma** e clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![não processar](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="c4f3e-647">Você está marcando este plug-in "não processar" porque o assembly do Unity Patcher tem dificuldade para processar esse plug-in.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="c4f3e-648">O plug-in ainda funcionará, embora não seja processado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="c4f3e-649">Capítulo 14-criando a classe TableToScene no projeto de Unity de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c4f3e-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="c4f3e-650">A classe **TableToScene** é idêntica à explicada no [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="c4f3e-651">Crie a mesma classe no projeto de Unity de realidade misturada seguindo o mesmo procedimento explicado no [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="c4f3e-652">Depois de concluir este capítulo, os dois projetos do **Unity** terão essa classe configurada na câmera principal.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="c4f3e-653">Capítulo 15 – criando a classe NotificationReceiver no projeto de Unity de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c4f3e-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="c4f3e-654">O segundo script que você precisa criar é **NotificationReceiver**, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="c4f3e-655">Registrando o aplicativo com o Hub de notificação na inicialização.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="c4f3e-656">Escutando notificações provenientes do hub de notificação.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="c4f3e-657">Desserializando os dados de objeto de notificações recebidas.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="c4f3e-658">Mova o GameObjects na cena, com base nos dados desserializados.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="c4f3e-659">Para criar o script **NotificationReceiver** :</span><span class="sxs-lookup"><span data-stu-id="c4f3e-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="c4f3e-660">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar**, **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="c4f3e-661">Nomeie o script **NotificationReceiver**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="c4f3e-662">![criar novo script](images/AzureLabs-Lab8-95.png)
    ![c# nome it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="c4f3e-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="c4f3e-663">Clique duas vezes no script para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="c4f3e-664">Adicione os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-664">Add the following namespaces:</span></span>

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

4.  <span data-ttu-id="c4f3e-665">Insira as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-665">Insert the following variables:</span></span>

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

5.  <span data-ttu-id="c4f3e-666">Substitua o valor **hubName** pelo nome do serviço do hub de notificação e o valor **hubListenEndpoint** com o valor do ponto de extremidade encontrado na guia políticas de acesso, serviço Hub de notificação do Azure, no portal do Azure (consulte a imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![Inserir ponto de extremidade de política de hubs de notificação](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="c4f3e-668">Agora, adicione os métodos **Start ()** e **ativo ()** para inicializar a classe.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

7.  <span data-ttu-id="c4f3e-669">Adicione o método **WaitForNotification** para permitir que o aplicativo receba notificações da biblioteca do hub de notificação sem conflitar com o thread principal:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

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

8.  <span data-ttu-id="c4f3e-670">O método a seguir, **InitNotificationAsync ()** , registrará o aplicativo com o serviço de Hub de notificação na inicialização.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="c4f3e-671">O código é comentado, pois o Unity não poderá compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="c4f3e-672">Você removerá os comentários quando importar o pacote NuGet de mensagens do Azure no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

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

9.  <span data-ttu-id="c4f3e-673">O manipulador a seguir **,\_PushNotificationReceived de canal ()** , será disparado sempre que uma notificação for recebida.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="c4f3e-674">Ele desserializará a notificação, que será a entidade de tabela do Azure que foi movida no aplicativo da área de trabalho e, em seguida, moverá o gameobject correspondente na cena MR para a mesma posição.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="c4f3e-675">O código é comentado porque o código faz referência à biblioteca de mensagens do Azure, que você adicionará depois de criar o projeto do Unity usando o Gerenciador de pacotes NuGet, no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="c4f3e-676">Assim, o projeto do Unity não será capaz de Compilar, a menos que seja comentado. Lembre-se de que, se você criar seu projeto e desejar retornar ao Unity, será necessário **comentar novamente** esse código.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

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

10. <span data-ttu-id="c4f3e-677">Lembre-se de salvar suas alterações antes de voltar para o editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="c4f3e-678">Clique na **câmera principal** do painel **hierarquia** , para que suas propriedades apareçam no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="c4f3e-679">Com a pasta **scripts** aberta, selecione o script **NotificationReceiver** e arraste-o para a **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="c4f3e-680">O resultado deve ser o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-680">The result should be as below:</span></span>

    ![Arraste o script do receptor de notificação para a câmera](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="c4f3e-682">Se estiver desenvolvendo isso para o Microsoft HoloLens, você precisará atualizar o componente da *câmera* da **câmera principal**, para que:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="c4f3e-683">Limpar sinalizadores: Cor sólida</span><span class="sxs-lookup"><span data-stu-id="c4f3e-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="c4f3e-684">Seguindo Preto</span><span class="sxs-lookup"><span data-stu-id="c4f3e-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="c4f3e-685">Capítulo 16-criar o projeto de realidade misturada para UWP</span><span class="sxs-lookup"><span data-stu-id="c4f3e-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="c4f3e-686">Este capítulo é idêntico ao processo de compilação para o projeto anterior.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="c4f3e-687">Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="c4f3e-688">Navegue até **configurações de compilação** (**configurações de compilação** de **arquivo** > ).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="c4f3e-689">No menu **configurações de Build** , verifique se os **projetos do Unity C#** \* estão com tiques (o que permitirá que você edite os scripts neste projeto, após a compilação).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="c4f3e-690">Depois que isso for feito, clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-690">After this is done, click **Build**.</span></span>

    ![Compilar projeto](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="c4f3e-692">Uma janela do **Explorador de arquivos** será Popup, solicitando um local para compilar.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="c4f3e-693">Crie uma nova pasta (clicando em **nova pasta** no canto superior esquerdo) e nomeie-a como **Build**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![criar pasta de builds](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="c4f3e-695">Abra a nova pasta builds e crie outra pasta (usando a **nova pasta** mais uma vez) e nomeie-a como **\_aplicativo NH\_Mr**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![criar pasta NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="c4f3e-697">Com o **aplicativo\_NH\_Mr** selecionado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="c4f3e-698">Clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-698">click **Select Folder**.</span></span> <span data-ttu-id="c4f3e-699">O projeto levará um minuto ou mais para ser compilado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="c4f3e-700">Após a compilação, uma janela **Explorador de arquivos** será aberta no local do novo projeto.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="c4f3e-701">Capítulo 17 – adicionar pacotes NuGet à solução UnityMRNotifHub</span><span class="sxs-lookup"><span data-stu-id="c4f3e-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="c4f3e-702">Lembre-se de que, depois de adicionar os seguintes pacotes do NuGet (e remover o comentário do código no próximo [capítulo](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), o código, quando reaberto no projeto do Unity, apresentará erros.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="c4f3e-703">Se desejar voltar e continuar a edição no editor do Unity, você precisará comentar o código errosome e, em seguida, remover o comentário novamente mais tarde, depois de voltar ao Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="c4f3e-704">Após a conclusão da compilação da realidade misturada, navegue até o projeto de realidade misturada, que você criou e clique duas vezes no arquivo da solução (. sln) dentro dessa pasta para abrir sua solução com o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="c4f3e-705">Agora, você precisará adicionar o pacote NuGet **WindowsAzure. Messaging. Managed** ; Esta é uma biblioteca que é usada para receber notificações do hub de notificação.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="c4f3e-706">Para importar o pacote NuGet:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="c4f3e-707">Na **Gerenciador de soluções**, clique com o botão direito do mouse em sua solução</span><span class="sxs-lookup"><span data-stu-id="c4f3e-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="c4f3e-708">Clique em **gerenciar pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-708">Click on **Manage NuGet Packages**.</span></span>

    ![abrir o Gerenciador do NuGet](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="c4f3e-710">Selecione a guia ***procurar*** e procure **WindowsAzure. Messaging. Managed**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![Localizar pacote de mensagens do Windows Azure](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="c4f3e-712">Selecione o resultado (como mostrado abaixo) e, na janela à direita, marque a caixa de seleção ao lado de **projeto**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="c4f3e-713">Isso coloca um tique na caixa de seleção ao lado de **Project**, juntamente com a caixa de seleção ao lado do projeto **assembly-Csharp** e **UnityMRNotifHub** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![todos os projetos em escala](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="c4f3e-715">A versão fornecida inicialmente **pode não** ser compatível com este projeto.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="c4f3e-716">Portanto, clique no menu suspenso ao lado de **versão**e clique em **versão 0.1.7.9**, em seguida, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="c4f3e-717">Agora você terminou de instalar o pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="c4f3e-718">Localize o código comentado que você inseriu na classe **NotificationReceiver** e remova os comentários.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="c4f3e-719">Capítulo 18-editar aplicativo UnityMRNotifHub, classe NotificationReceiver</span><span class="sxs-lookup"><span data-stu-id="c4f3e-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="c4f3e-720">Depois de ter adicionado os **pacotes NuGet**, você precisará remover o *Comentário* de parte do código dentro da classe **NotificationReceiver** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="c4f3e-721">Isso inclui:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-721">This includes:</span></span>

1. <span data-ttu-id="c4f3e-722">O namespace na parte superior:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="c4f3e-723">Todo o código dentro do método **InitNotificationsAsync ()** :</span><span class="sxs-lookup"><span data-stu-id="c4f3e-723">All the code within the **InitNotificationsAsync()** method:</span></span>

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
> <span data-ttu-id="c4f3e-724">O código acima tem um comentário: Certifique-se de que você não tenha desmarcado *acidentalmente esse* comentário (pois o código não será compilado se você tiver!).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="c4f3e-725">E, por fim, o evento **Channel_PushNotificationReceived** :</span><span class="sxs-lookup"><span data-stu-id="c4f3e-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

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

<span data-ttu-id="c4f3e-726">Com esses comentários, certifique-se de salvar e, em seguida, vá para o próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="c4f3e-727">Capítulo 19 – associar o projeto de realidade misturada ao aplicativo da loja</span><span class="sxs-lookup"><span data-stu-id="c4f3e-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="c4f3e-728">Agora você precisa associar o projeto de **realidade misturada** ao aplicativo da loja criado no no início do laboratório.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="c4f3e-729">Abra a solução.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-729">Open the solution.</span></span>

2.  <span data-ttu-id="c4f3e-730">Clique com o botão direito do mouse no projeto de aplicativo UWP no painel de Gerenciador de Soluções, acesse **armazenar**e **associe o aplicativo à loja...** .</span><span class="sxs-lookup"><span data-stu-id="c4f3e-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![abrir Associação de armazenamento](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="c4f3e-732">Uma nova janela será exibida chamada **associar seu aplicativo à Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="c4f3e-733">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-733">Click **Next**.</span></span>

    ![ir para a próxima tela](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="c4f3e-735">Ele carregará todos os aplicativos associados à conta em que você fez logon.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="c4f3e-736">Se você não estiver conectado à sua conta, poderá **fazer logon** nesta página.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="c4f3e-737">Localize o **nome do aplicativo da loja** que você criou no início deste tutorial e selecione-o.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="c4f3e-738">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-738">Then click **Next**.</span></span>

    ![Localizar e selecionar o nome do repositório](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="c4f3e-740">Clique em **associar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-740">Click **Associate**.</span></span>

    ![associar o aplicativo](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="c4f3e-742">Seu aplicativo agora está **associado** ao aplicativo da loja.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="c4f3e-743">Isso é necessário para habilitar as notificações.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="c4f3e-744">Capítulo 20-implantar aplicativos UnityMRNotifHub e UnityDesktopNotifHub</span><span class="sxs-lookup"><span data-stu-id="c4f3e-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="c4f3e-745">Este capítulo pode ser mais fácil com duas pessoas, pois o resultado incluirá ambos os aplicativos em execução, um em execução na área de trabalho do computador e o outro no headset de imersão.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="c4f3e-746">O aplicativo de headset de imersão está aguardando para receber alterações na cena (alterações de posição do GameObjects local) e o aplicativo de área de trabalho fará alterações em sua cena local (alterações de posição), que será compartilhada para o aplicativo MR.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="c4f3e-747">Faz sentido implantar o aplicativo Sr primeiro, seguido pelo aplicativo de desktop, para que o receptor possa começar a escutar.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="c4f3e-748">Para implantar o aplicativo **UnityMRNotifHub** em seu computador local:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="c4f3e-749">Abra o arquivo de solução do seu aplicativo **UnityMRNotifHub** no **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="c4f3e-750">Na **plataforma da solução**, selecione **x86, computador local**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="c4f3e-751">Na **configuração da solução** , selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![definir configuração do projeto](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="c4f3e-753">Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="c4f3e-754">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="c4f3e-755">Para implantar o aplicativo **UnityDesktopNotifHub** no computador local:</span><span class="sxs-lookup"><span data-stu-id="c4f3e-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="c4f3e-756">Abra o arquivo de solução do seu aplicativo **UnityDesktopNotifHub** no **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="c4f3e-757">Na **plataforma da solução**, selecione **x86, computador local**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="c4f3e-758">Na **configuração da solução** , selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![definir configuração do projeto](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="c4f3e-760">Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="c4f3e-761">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="c4f3e-762">Inicie o aplicativo de realidade misturada, seguido pelo aplicativo de desktop.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="c4f3e-763">Com ambos os aplicativos em execução, mova um objeto na cena da área de trabalho (usando o botão esquerdo do mouse).</span><span class="sxs-lookup"><span data-stu-id="c4f3e-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="c4f3e-764">Essas alterações posicionais serão feitas localmente, serializadas e enviadas para o serviço de Aplicativo de funções.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="c4f3e-765">O serviço de Aplicativo de funções atualizará a tabela junto com o Hub de notificação.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="c4f3e-766">Após ter recebido uma atualização, o Hub de notificação enviará os dados atualizados diretamente para todos os aplicativos registrados (nesse caso, o aplicativo de headsets de imersão), que desserializará os dados de entrada e aplicará os novos dados posicionais aos objetos locais, movendo-os em cena.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="c4f3e-767">Seu aplicativo de hubs de notificação do Azure foi concluído</span><span class="sxs-lookup"><span data-stu-id="c4f3e-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="c4f3e-768">Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço de hubs de notificação do Azure e permite a comunicação entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c4f3e-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![final do produto final](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="c4f3e-770">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="c4f3e-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c4f3e-771">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="c4f3e-771">Exercise 1</span></span>

<span data-ttu-id="c4f3e-772">Você pode solucionar como alterar a cor do GameObjects e enviar essa notificação para outros aplicativos que visualizam a cena?</span><span class="sxs-lookup"><span data-stu-id="c4f3e-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c4f3e-773">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="c4f3e-773">Exercise 2</span></span>

<span data-ttu-id="c4f3e-774">Você pode adicionar movimento do GameObjects ao seu aplicativo MR e ver a cena atualizada em seu aplicativo de desktop?</span><span class="sxs-lookup"><span data-stu-id="c4f3e-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
