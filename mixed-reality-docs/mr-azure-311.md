---
title: Sr e Azure 311-Microsoft Graph
description: Conclua este curso para aprender a aproveitar Microsoft Graph e conectar-se aos dados que impulsionam a produtividade, em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, Microsoft Graph, hololens, imersão, VR
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694523"
---
>[!NOTE]
><span data-ttu-id="615ce-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="615ce-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="615ce-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="615ce-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="615ce-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="615ce-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="615ce-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="615ce-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="615ce-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="615ce-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="615ce-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="615ce-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="615ce-110">Sr e Azure 311-Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="615ce-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="615ce-111">Neste curso, você aprenderá a usar o *Microsoft Graph* para fazer logon em seu conta Microsoft usando a autenticação segura em um aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="615ce-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="615ce-112">Em seguida, você irá recuperar e exibir suas reuniões agendadas na interface do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="615ce-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="615ce-113">*Microsoft Graph* é um conjunto de APIs criadas para permitir o acesso a muitos dos serviços da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="615ce-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="615ce-114">A Microsoft descreve Microsoft Graph como sendo uma matriz de recursos conectados por relações, o que significa que ele permite que um aplicativo acesse todos os tipos de dados de usuário conectados.</span><span class="sxs-lookup"><span data-stu-id="615ce-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="615ce-115">Para obter mais informações, visite a [página Microsoft Graph](https://developer.microsoft.com/graph).</span><span class="sxs-lookup"><span data-stu-id="615ce-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="615ce-116">O desenvolvimento incluirá a criação de um aplicativo no qual o usuário será instruído a olhar e, em seguida, tocará em uma esfera, que solicitará que o usuário faça logon com segurança em um conta Microsoft.</span><span class="sxs-lookup"><span data-stu-id="615ce-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="615ce-117">Depois de conectado à sua conta, o usuário poderá ver uma lista de reuniões agendadas para o dia.</span><span class="sxs-lookup"><span data-stu-id="615ce-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="615ce-118">Após a conclusão deste curso, você terá um aplicativo de HoloLens de realidade misturada, que poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="615ce-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="615ce-119">Usando o gesto de toque, toque em um objeto, que solicitará que o usuário faça logon em uma conta da Microsoft (saindo do aplicativo para fazer logon e, em seguida, volte para o aplicativo novamente).</span><span class="sxs-lookup"><span data-stu-id="615ce-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="615ce-120">Exiba uma lista de reuniões agendadas para o dia.</span><span class="sxs-lookup"><span data-stu-id="615ce-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="615ce-121">Em seu aplicativo, cabe a você como você integrará os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="615ce-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="615ce-122">Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="615ce-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="615ce-123">É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="615ce-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="615ce-124">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="615ce-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="615ce-125">Course</span><span class="sxs-lookup"><span data-stu-id="615ce-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="615ce-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="615ce-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="615ce-127"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="615ce-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="615ce-128">Sr e Azure 311: Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="615ce-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="615ce-129">✔️</span><span class="sxs-lookup"><span data-stu-id="615ce-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="615ce-130">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="615ce-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="615ce-131">Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o.</span><span class="sxs-lookup"><span data-stu-id="615ce-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="615ce-132">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (julho de 2018).</span><span class="sxs-lookup"><span data-stu-id="615ce-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="615ce-133">Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso correspondam perfeitamente ao que você encontrará no software mais recente do que o que está listado abaixo.</span><span class="sxs-lookup"><span data-stu-id="615ce-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="615ce-134">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="615ce-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="615ce-135">Um PC de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="615ce-135">A development PC</span></span>
- [<span data-ttu-id="615ce-136">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="615ce-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="615ce-137">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="615ce-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="615ce-138">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="615ce-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="615ce-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="615ce-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="615ce-140">Um [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="615ce-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="615ce-141">Acesso à Internet para a instalação do Azure e recuperação de dados de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="615ce-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="615ce-142">Uma **conta da Microsoft** válida (pessoal ou corporativa/de estudante)</span><span class="sxs-lookup"><span data-stu-id="615ce-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="615ce-143">Algumas reuniões agendadas para o dia atual, usando a mesma conta da Microsoft</span><span class="sxs-lookup"><span data-stu-id="615ce-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="615ce-144">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="615ce-144">Before you start</span></span>

1.  <span data-ttu-id="615ce-145">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="615ce-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="615ce-146">Configure e teste seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="615ce-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="615ce-147">Se você precisar de suporte para configurar seu HoloLens, [visite o artigo configuração do hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="615ce-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="615ce-148">É uma boa ideia executar a calibragem e o ajuste do sensor ao começar a desenvolver um novo aplicativo do HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="615ce-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="615ce-149">Para obter ajuda sobre calibragem, siga este [link para o artigo Calibration do HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="615ce-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="615ce-150">Para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste do sensor do HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="615ce-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="615ce-151">Capítulo 1-criar seu aplicativo no portal de registro de aplicativos</span><span class="sxs-lookup"><span data-stu-id="615ce-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="615ce-152">Para começar, você precisará criar e registrar seu aplicativo no **portal de registro de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="615ce-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="615ce-153">Neste capítulo, você também encontrará a chave de serviço que permitirá fazer chamadas para *Microsoft Graph* acessar o conteúdo da conta.</span><span class="sxs-lookup"><span data-stu-id="615ce-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="615ce-154">Navegue até o [portal de registro de aplicativos da Microsoft](https://apps.dev.microsoft.com) e faça logon com sua conta da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="615ce-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="615ce-155">Depois de fazer logon, você será redirecionado para o portal de **registro de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="615ce-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="615ce-156">Na seção **meus aplicativos** , clique no botão **Adicionar um aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="615ce-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="615ce-157">O **portal de registro de aplicativos** pode parecer diferente, dependendo se você já trabalhou com *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="615ce-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="615ce-158">As capturas de tela abaixo exibem essas versões diferentes.</span><span class="sxs-lookup"><span data-stu-id="615ce-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="615ce-159">Adicione um nome para seu aplicativo e clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="615ce-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="615ce-160">Depois que o aplicativo tiver sido criado, você será redirecionado para a página principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="615ce-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="615ce-161">Copie a **ID do aplicativo** e anote esse valor em algum lugar seguro, você o usará em breve no seu código.</span><span class="sxs-lookup"><span data-stu-id="615ce-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="615ce-162">Na seção **plataformas** , verifique se o **aplicativo nativo** é exibido.</span><span class="sxs-lookup"><span data-stu-id="615ce-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="615ce-163">Se *não* clique em **Adicionar plataforma** e selecione **aplicativo nativo**.</span><span class="sxs-lookup"><span data-stu-id="615ce-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="615ce-164">Role para baixo na mesma página e, na seção chamada **Microsoft Graph permissões** , você precisará adicionar permissões adicionais para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="615ce-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="615ce-165">Clique em **Adicionar** ao lado de **permissões delegadas**.</span><span class="sxs-lookup"><span data-stu-id="615ce-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="615ce-166">Como você deseja que seu aplicativo acesse o calendário do usuário, marque a caixa chamada **calendários. Leia** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="615ce-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="615ce-167">Role até a parte inferior e clique no botão **salvar** .</span><span class="sxs-lookup"><span data-stu-id="615ce-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="615ce-168">Seu salvamento será confirmado e você poderá fazer logoff do **portal de registro de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="615ce-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="615ce-169">Capítulo 2 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="615ce-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="615ce-170">A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="615ce-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="615ce-171">Abra o *Unity* e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="615ce-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="615ce-172">Você precisa fornecer um nome de projeto de Unity.</span><span class="sxs-lookup"><span data-stu-id="615ce-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="615ce-173">Insira **MSGraphMR**.</span><span class="sxs-lookup"><span data-stu-id="615ce-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="615ce-174">Verifique se o modelo de projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="615ce-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="615ce-175">Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="615ce-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="615ce-176">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="615ce-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="615ce-177">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="615ce-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="615ce-178">Vá para **Editar** > **preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="615ce-178">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="615ce-179">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="615ce-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="615ce-180">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="615ce-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="615ce-181">Vá para **arquivo** > **configurações de compilação** e selecione **plataforma universal do Windows**, em seguida, clique no botão **alternar plataforma** para aplicar sua seleção.</span><span class="sxs-lookup"><span data-stu-id="615ce-181">Go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="615ce-182">Ainda em**configurações de compilação**de **arquivo** > , verifique se:</span><span class="sxs-lookup"><span data-stu-id="615ce-182">While still in **File** > **Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="615ce-183">O **dispositivo de destino** está definido como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="615ce-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="615ce-184">O **tipo de compilação** está definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="615ce-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="615ce-185">O **SDK** está definido para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="615ce-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="615ce-186">A **versão do Visual Studio** está definida para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="615ce-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="615ce-187">**Compilar e executar** é definido como **computador local**</span><span class="sxs-lookup"><span data-stu-id="615ce-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="615ce-188">Salve a cena e adicione-a à compilação.</span><span class="sxs-lookup"><span data-stu-id="615ce-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="615ce-189">Faça isso selecionando **Adicionar abrir cenas**.</span><span class="sxs-lookup"><span data-stu-id="615ce-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="615ce-190">Uma janela salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="615ce-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="615ce-191">Crie uma nova pasta para isso e qualquer cena futura.</span><span class="sxs-lookup"><span data-stu-id="615ce-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="615ce-192">Selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.</span><span class="sxs-lookup"><span data-stu-id="615ce-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="615ce-193">Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo*:, digite **MR_ComputerVisionScene**e clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="615ce-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="615ce-194">Lembre-se de que você deve salvar as cenas do Unity na pasta *ativos* , pois elas devem ser associadas ao projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="615ce-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="615ce-195">Criar a pasta de cenas (e outras pastas semelhantes) é uma maneira típica de estruturar um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="615ce-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="615ce-196">As configurações restantes, em *configurações de compilação*, devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="615ce-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="615ce-197">Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="615ce-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="615ce-198">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="615ce-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="615ce-199">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="615ce-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="615ce-200">**Criando scripts** A **versão de tempo de execução** deve ser **Experimental** (.NET 4,6 equivalente), o que irá disparar uma necessidade de reiniciar o editor.</span><span class="sxs-lookup"><span data-stu-id="615ce-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="615ce-201">O **back-end de script** deve ser **.net**</span><span class="sxs-lookup"><span data-stu-id="615ce-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="615ce-202">O **nível de compatibilidade da API** deve ser **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="615ce-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="615ce-203">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="615ce-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="615ce-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="615ce-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="615ce-205">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), verifique a **realidade virtual com suporte**, verifique se o **SDK do Windows Mixed Reality** foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="615ce-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="615ce-206">De volta *às configurações de compilação*, os *projetos de C# Unity* não ficam mais esmaecidos; Marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="615ce-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="615ce-207">Feche a janela *configurações de compilação* .</span><span class="sxs-lookup"><span data-stu-id="615ce-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="615ce-208">Salve sua cena e seu projeto **(arquivo salvar arquivos** > de salvamento **/**  > **salvar**arquivo).</span><span class="sxs-lookup"><span data-stu-id="615ce-208">Save your scene and project (**FILE** > **SAVE SCENES / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="615ce-209">Capítulo 3 – importar bibliotecas no Unity</span><span class="sxs-lookup"><span data-stu-id="615ce-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="615ce-210">Se você quiser ignorar o componente de *configuração do Unity* deste curso e continuar diretamente no código, sinta-se à vontade para baixar este [Azure-Mr-311. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), importá-lo em seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar no [capítulo 5 ](#chapter-5---create-meetingsui-class).</span><span class="sxs-lookup"><span data-stu-id="615ce-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="615ce-211">Para usar *Microsoft Graph* no Unity, você precisa fazer uso da dll **Microsoft. Identity. Client** .</span><span class="sxs-lookup"><span data-stu-id="615ce-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="615ce-212">É possível usar o SDK do Microsoft Graph, no entanto, ele exigirá a adição de um pacote NuGet depois que você criar o projeto do Unity (ou seja, editando o projeto após a compilação).</span><span class="sxs-lookup"><span data-stu-id="615ce-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="615ce-213">É considerado mais simples importar as DLLs necessárias diretamente para o Unity.</span><span class="sxs-lookup"><span data-stu-id="615ce-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="615ce-214">Atualmente, há um problema conhecido no Unity que exige que os plugins sejam reconfigurados após a importação.</span><span class="sxs-lookup"><span data-stu-id="615ce-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="615ce-215">Essas etapas (4-7 nesta seção) não serão mais necessárias depois que o bug for resolvido.</span><span class="sxs-lookup"><span data-stu-id="615ce-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="615ce-216">Para importar *Microsoft Graph* para seu próprio projeto, [Baixe o arquivo MSGraph_LabPlugins. zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="615ce-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="615ce-217">Este pacote foi criado com versões das bibliotecas que foram testadas.</span><span class="sxs-lookup"><span data-stu-id="615ce-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="615ce-218">Se você quiser saber mais sobre como adicionar DLLs personalizadas ao seu projeto do Unity, [siga este link](https://docs.unity3d.com/Manual/UsingDLL.html).</span><span class="sxs-lookup"><span data-stu-id="615ce-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="615ce-219">Para importar o pacote:</span><span class="sxs-lookup"><span data-stu-id="615ce-219">To import the package:</span></span>

1.  <span data-ttu-id="615ce-220">Adicione o pacote do Unity ao Unity usando a opção de menu**pacote personalizado** do**pacote** > de importação de **ativos** > .</span><span class="sxs-lookup"><span data-stu-id="615ce-220">Add the Unity Package to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span> <span data-ttu-id="615ce-221">Selecione o pacote que você acabou de baixar.</span><span class="sxs-lookup"><span data-stu-id="615ce-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="615ce-222">Na caixa **Importar pacote de Unity** que é exibida, verifique se tudo em (e incluindo) **plug-ins** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="615ce-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="615ce-223">Clique no botão **importar** para adicionar os itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="615ce-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="615ce-224">Vá para a pasta **MSGraph** em **plug-ins** no *painel Projeto* e selecione o plug-in chamado **Microsoft. Identity. Client**.</span><span class="sxs-lookup"><span data-stu-id="615ce-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="615ce-225">Com o *plug-in* selecionado, verifique se **qualquer plataforma** está desmarcada e, em seguida, verifique se **WSAPlayer** também está desmarcado e clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="615ce-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="615ce-226">Isso é apenas para confirmar que os arquivos estão configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="615ce-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="615ce-227">Marcar esses plug-ins os configura para ser usado apenas no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="615ce-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="615ce-228">Há um conjunto diferente de DLLs na pasta WSA que será usado depois que o projeto for exportado do Unity como um aplicativo universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="615ce-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="615ce-229">Em seguida, você precisa abrir a pasta **WSA** , dentro da pasta **MSGraph** .</span><span class="sxs-lookup"><span data-stu-id="615ce-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="615ce-230">Você verá uma cópia do mesmo arquivo que acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="615ce-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="615ce-231">Selecione o arquivo e, em seguida, no Inspetor:</span><span class="sxs-lookup"><span data-stu-id="615ce-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="615ce-232">Verifique se **qualquer plataforma** está desmarcada e se **somente** **WSAPlayer** está **marcado**.</span><span class="sxs-lookup"><span data-stu-id="615ce-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="615ce-233">Verifique se o **SDK** está definido como **UWP**e se o **back-end de script** está definido como **dot net**</span><span class="sxs-lookup"><span data-stu-id="615ce-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="615ce-234">Verifique se **não processar** está **marcado**.</span><span class="sxs-lookup"><span data-stu-id="615ce-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="615ce-235">Clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="615ce-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="615ce-236">Capítulo 4 – configuração da câmera</span><span class="sxs-lookup"><span data-stu-id="615ce-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="615ce-237">Durante este capítulo, você configurará a câmera principal da sua cena:</span><span class="sxs-lookup"><span data-stu-id="615ce-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="615ce-238">No *painel hierarquia*, selecione a **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="615ce-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="615ce-239">Depois de selecionado, você poderá ver todos os componentes da **câmera principal** no painel *Inspetor* .</span><span class="sxs-lookup"><span data-stu-id="615ce-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="615ce-240">O **objeto de câmera** deve ser nomeado como a **câmera principal** (Observe a grafia!)</span><span class="sxs-lookup"><span data-stu-id="615ce-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="615ce-241">A **marca** da câmera principal deve ser definida como **MainCamera** (Observe a ortografia!)</span><span class="sxs-lookup"><span data-stu-id="615ce-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="615ce-242">Verifique se a **posição de transformação** está definida como **0, 0,** 0</span><span class="sxs-lookup"><span data-stu-id="615ce-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="615ce-243">Definir **sinalizadores de limpeza** como **cor sólida**</span><span class="sxs-lookup"><span data-stu-id="615ce-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="615ce-244">Defina a **cor do plano de fundo** do componente da câmera como **preto, alfa 0** **(código hex: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="615ce-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="615ce-245">A estrutura final do objeto no *painel hierarquia* deve ser parecida com a mostrada na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="615ce-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="615ce-246">Capítulo 5-criar classe MeetingsUI</span><span class="sxs-lookup"><span data-stu-id="615ce-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="615ce-247">O primeiro script que você precisa criar é **MeetingsUI**, que é responsável por hospedar e preencher a interface do usuário do aplicativo (mensagem de boas-vindas, instruções e os detalhes da reunião).</span><span class="sxs-lookup"><span data-stu-id="615ce-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="615ce-248">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="615ce-248">To create this class:</span></span>

1.  <span data-ttu-id="615ce-249">Clique com o botão direito do mouse na pasta **ativos** no *painel Projeto*e selecione **criar** > **pasta**.</span><span class="sxs-lookup"><span data-stu-id="615ce-249">Right-click on the **Assets** folder in the *Project Panel*, then select **Create** > **Folder**.</span></span> <span data-ttu-id="615ce-250">Nomeie a pasta **scripts**.</span><span class="sxs-lookup"><span data-stu-id="615ce-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="615ce-251">Abra a pasta **scripts** e, nessa pasta, clique com o botão direito do mouse em **criar**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="615ce-251">Open the **Scripts** folder then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="615ce-252">Nomeie o script **MeetingsUI.**</span><span class="sxs-lookup"><span data-stu-id="615ce-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="615ce-253">Clique duas vezes no novo script **MeetingsUI** para abri-lo com o *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="615ce-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="615ce-254">Insira os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="615ce-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="615ce-255">Dentro da classe, insira as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="615ce-255">Inside the class insert the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  <span data-ttu-id="615ce-256">Em seguida, substitua o método **Start ()** e adicione um método **ativo ()** .</span><span class="sxs-lookup"><span data-stu-id="615ce-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="615ce-257">Eles serão chamados quando a classe for inicializada:</span><span class="sxs-lookup"><span data-stu-id="615ce-257">These will be called when the class initializes:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  <span data-ttu-id="615ce-258">Adicione os métodos responsáveis por criar a *interface do usuário de reuniões* e preenchê-la com as reuniões atuais quando solicitado:</span><span class="sxs-lookup"><span data-stu-id="615ce-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. <span data-ttu-id="615ce-259">**Exclua** o método **Update ()** e **salve as alterações** no Visual Studio antes de retornar ao Unity.</span><span class="sxs-lookup"><span data-stu-id="615ce-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="615ce-260">Capítulo 6 – criar a classe do grafo</span><span class="sxs-lookup"><span data-stu-id="615ce-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="615ce-261">O próximo script a ser criado é o script do **grafo** .</span><span class="sxs-lookup"><span data-stu-id="615ce-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="615ce-262">Esse script é responsável por fazer as chamadas autenticar o usuário e recuperar as reuniões agendadas para o dia atual do calendário do usuário.</span><span class="sxs-lookup"><span data-stu-id="615ce-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="615ce-263">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="615ce-263">To create this class:</span></span>

1.  <span data-ttu-id="615ce-264">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="615ce-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="615ce-265">Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="615ce-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="615ce-266">Nomeie o **gráfico**de script.</span><span class="sxs-lookup"><span data-stu-id="615ce-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="615ce-267">Clique duas vezes no script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="615ce-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="615ce-268">Insira os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="615ce-268">Insert the following namespaces:</span></span>

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="615ce-269">Você observará que partes do código nesse script são encapsuladas em torno de [diretivas de pré-compilação](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), isso é para evitar problemas com as bibliotecas ao criar a solução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="615ce-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="615ce-270">Exclua os métodos **Start ()** e **Update ()** , pois eles não serão usados.</span><span class="sxs-lookup"><span data-stu-id="615ce-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="615ce-271">Fora da classe do **grafo** , insira os seguintes objetos, que são necessários para desserializar o objeto JSON que representa as reuniões agendadas diariamente:</span><span class="sxs-lookup"><span data-stu-id="615ce-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  <span data-ttu-id="615ce-272">Dentro da classe do **grafo** , adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="615ce-272">Inside the **Graph** class, add the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > <span data-ttu-id="615ce-273">Altere o valor **AppID** para que seja a **ID do aplicativo** que você anotou no  **[capítulo 1](#chapter-1---create-your-app-in-the-application-registration-portal), etapa 4**.</span><span class="sxs-lookup"><span data-stu-id="615ce-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="615ce-274">Esse valor deve ser o mesmo que o exibido no **portal de registro de aplicativos,** na página de registro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="615ce-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="615ce-275">Dentro da classe do **grafo** , adicione os métodos **SignInAsync ()** e **AquireTokenAsync ()** , que solicitará que o usuário insira as credenciais de logon.</span><span class="sxs-lookup"><span data-stu-id="615ce-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  <span data-ttu-id="615ce-276">Adicione os dois métodos a seguir:</span><span class="sxs-lookup"><span data-stu-id="615ce-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="615ce-277">**BuildTodayCalendarEndpoint ()** , que compila o URI que especifica o dia e o período de tempo em que as reuniões agendadas são recuperadas.</span><span class="sxs-lookup"><span data-stu-id="615ce-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="615ce-278">**ListMeetingsAsync ()** , que solicita as reuniões agendadas de *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="615ce-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. <span data-ttu-id="615ce-279">Agora você concluiu o script do **grafo** .</span><span class="sxs-lookup"><span data-stu-id="615ce-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="615ce-280">**Salve suas alterações** no Visual Studio antes de retornar ao Unity.</span><span class="sxs-lookup"><span data-stu-id="615ce-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="615ce-281">Capítulo 7-criar o script GazeInput</span><span class="sxs-lookup"><span data-stu-id="615ce-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="615ce-282">Agora, você criará o **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="615ce-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="615ce-283">Essa classe manipula e controla o olhar do usuário, usando um **Raycast** proveniente da **câmera principal**, projetando em frente.</span><span class="sxs-lookup"><span data-stu-id="615ce-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="615ce-284">Para criar o script:</span><span class="sxs-lookup"><span data-stu-id="615ce-284">To create the script:</span></span>

1.  <span data-ttu-id="615ce-285">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="615ce-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="615ce-286">Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="615ce-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="615ce-287">Nomeie o script **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="615ce-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="615ce-288">Clique duas vezes no script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="615ce-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="615ce-289">Altere o código de namespaces para corresponder ao mostrado abaixo, juntamente com a adição da marca ' **\[System. Serializable\]** ' acima da classe **GazeInput** , para que possa ser serializada:</span><span class="sxs-lookup"><span data-stu-id="615ce-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="615ce-290">Dentro da classe **GazeInput** , adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="615ce-290">Inside the **GazeInput** class, add the following variables:</span></span>

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="615ce-291">Adicione o método **CreateCursor ()** para criar o cursor do HoloLens na cena e chame o método do método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="615ce-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  <span data-ttu-id="615ce-292">Os métodos a seguir habilitam o olhar Raycast e controlam os objetos focados.</span><span class="sxs-lookup"><span data-stu-id="615ce-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="615ce-293">**Salve suas alterações** no Visual Studio antes de retornar ao Unity.</span><span class="sxs-lookup"><span data-stu-id="615ce-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="615ce-294">Capítulo 8-criar a classe interações</span><span class="sxs-lookup"><span data-stu-id="615ce-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="615ce-295">Agora será necessário criar o script de **interações** , que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="615ce-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="615ce-296">Manipular a interação de **toque** e a **câmera olhar**, que permite ao usuário interagir com o logon "Button" na cena.</span><span class="sxs-lookup"><span data-stu-id="615ce-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="615ce-297">Criando o objeto "Button" de logon na cena para o usuário interagir com o.</span><span class="sxs-lookup"><span data-stu-id="615ce-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="615ce-298">Para criar o script:</span><span class="sxs-lookup"><span data-stu-id="615ce-298">To create the script:</span></span>

1.  <span data-ttu-id="615ce-299">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="615ce-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="615ce-300">Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="615ce-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="615ce-301">Nomeie o script de interações.</span><span class="sxs-lookup"><span data-stu-id="615ce-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="615ce-302">Clique duas vezes no script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="615ce-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="615ce-303">Insira os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="615ce-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="615ce-304">Altere a herança da classe de **interação** de *monocomportamento* para **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="615ce-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="615ce-305">~~interações de classe pública: MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="615ce-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="615ce-306">Dentro da classe de **interação** , insira a seguinte variável:</span><span class="sxs-lookup"><span data-stu-id="615ce-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="615ce-307">Substituir o método **Start** ; Observe que é um método override, que chama o método de classe ' base ' olhar.</span><span class="sxs-lookup"><span data-stu-id="615ce-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="615ce-308">**Start ()** será chamado quando a classe for inicializada, registrando-se para o reconhecimento de entrada e criando o *botão* entrar na cena:</span><span class="sxs-lookup"><span data-stu-id="615ce-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  <span data-ttu-id="615ce-309">Adicione o método **CreateSignInButton ()** , que criará uma instância do *botão* entrar na cena e definirá suas propriedades:</span><span class="sxs-lookup"><span data-stu-id="615ce-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  <span data-ttu-id="615ce-310">Adicione o método **GestureRecognizer_Tapped ()** , que será respondido para o evento *Tap* User.</span><span class="sxs-lookup"><span data-stu-id="615ce-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. <span data-ttu-id="615ce-311">**Exclua** o método **Update ()** e **salve as alterações** no Visual Studio antes de retornar ao Unity.</span><span class="sxs-lookup"><span data-stu-id="615ce-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="615ce-312">Capítulo 9-configurar as referências de script</span><span class="sxs-lookup"><span data-stu-id="615ce-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="615ce-313">Neste capítulo, você precisa posicionar o  script de interações na **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="615ce-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="615ce-314">Esse script manipulará a colocação dos outros scripts onde eles precisam ser.</span><span class="sxs-lookup"><span data-stu-id="615ce-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="615ce-315">Na pasta **scripts** do *painel Projeto*, arraste as interações de  script para o objeto da **câmera principal** , conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="615ce-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="615ce-316">Capítulo 10-Configurando a marca</span><span class="sxs-lookup"><span data-stu-id="615ce-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="615ce-317">O código que manipula o olhar fará uso da marca **SignInButton** para identificar a qual objeto o usuário irá interagir para entrar no *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="615ce-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="615ce-318">Para criar a marca:</span><span class="sxs-lookup"><span data-stu-id="615ce-318">To create the Tag:</span></span>

1.  <span data-ttu-id="615ce-319">No editor do Unity, clique na **câmera principal** no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="615ce-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="615ce-320">No *painel Inspetor* , clique na marca **MainCamera**  para abrir uma lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="615ce-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="615ce-321">Clique em **adicionar marca..** .</span><span class="sxs-lookup"><span data-stu-id="615ce-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="615ce-322">Clique no **+** botão.</span><span class="sxs-lookup"><span data-stu-id="615ce-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="615ce-323">Escreva o nome da marca como **SignInButton** e clique em salvar.</span><span class="sxs-lookup"><span data-stu-id="615ce-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="615ce-324">Capítulo 11-criar o projeto do Unity para UWP</span><span class="sxs-lookup"><span data-stu-id="615ce-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="615ce-325">Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.</span><span class="sxs-lookup"><span data-stu-id="615ce-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="615ce-326">Navegue até *configurações de Build* (**arquivo*>*Compilar configurações**).</span><span class="sxs-lookup"><span data-stu-id="615ce-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="615ce-327">Se ainda não tiver feito isso, **projetos de unidade C\#** Tick.</span><span class="sxs-lookup"><span data-stu-id="615ce-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="615ce-328">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="615ce-328">Click **Build**.</span></span> <span data-ttu-id="615ce-329">O Unity iniciará uma janela **Explorador de arquivos** , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado.</span><span class="sxs-lookup"><span data-stu-id="615ce-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="615ce-330">Crie essa pasta agora e nomeie-a como **aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="615ce-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="615ce-331">Em seguida, com a pasta de **aplicativo** selecionada, clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="615ce-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="615ce-332">O Unity começará a criar seu projeto na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="615ce-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="615ce-333">Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).</span><span class="sxs-lookup"><span data-stu-id="615ce-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="615ce-334">Capítulo 12 – implantar no HoloLens</span><span class="sxs-lookup"><span data-stu-id="615ce-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="615ce-335">Para implantar no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="615ce-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="615ce-336">Você precisará do endereço IP do seu HoloLens (para implantação remota) e para garantir que seu HoloLens esteja no **modo de desenvolvedor.**</span><span class="sxs-lookup"><span data-stu-id="615ce-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="615ce-337">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="615ce-337">To do this:</span></span>

    1.  <span data-ttu-id="615ce-338">Enquanto estiver desgastando seu HoloLens, abra as **configurações**.</span><span class="sxs-lookup"><span data-stu-id="615ce-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="615ce-339">Vá para **rede &**  > **Opções avançadas** **de Internet Wi-Fi** > </span><span class="sxs-lookup"><span data-stu-id="615ce-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="615ce-340">Anote o endereço **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="615ce-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="615ce-341">Em seguida, navegue de volta para **configurações**e, em seguida, para **Atualizar & segurança** > **para desenvolvedores**</span><span class="sxs-lookup"><span data-stu-id="615ce-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="615ce-342">Defina o **modo de desenvolvedor em**.</span><span class="sxs-lookup"><span data-stu-id="615ce-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="615ce-343">Navegue até sua nova compilação do Unity (a pasta do **aplicativo** ) e abra o arquivo de solução com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="615ce-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="615ce-344">Na **configuração da solução** , selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="615ce-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="615ce-345">Na **plataforma da solução**, selecione **x86, computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="615ce-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="615ce-346">Você será solicitado a inserir o **endereço IP** de um dispositivo remoto (o HoloLens, neste caso, que você anotou).</span><span class="sxs-lookup"><span data-stu-id="615ce-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="615ce-347">Vá para o menu **Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="615ce-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="615ce-348">Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="615ce-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="615ce-349">Seu aplicativo Microsoft Graph HoloLens</span><span class="sxs-lookup"><span data-stu-id="615ce-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="615ce-350">Parabéns, você criou um aplicativo de realidade misturada que aproveita o Microsoft Graph, para ler e exibir dados de calendário do usuário.</span><span class="sxs-lookup"><span data-stu-id="615ce-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="615ce-351">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="615ce-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="615ce-352">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="615ce-352">Exercise 1</span></span>

<span data-ttu-id="615ce-353">Use Microsoft Graph para exibir outras informações sobre o usuário</span><span class="sxs-lookup"><span data-stu-id="615ce-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="615ce-354">Email do usuário/número do telefone/imagem do perfil</span><span class="sxs-lookup"><span data-stu-id="615ce-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="615ce-355">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="615ce-355">Exercise 1</span></span>

<span data-ttu-id="615ce-356">Implemente o controle de voz para navegar na interface do usuário do Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="615ce-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
