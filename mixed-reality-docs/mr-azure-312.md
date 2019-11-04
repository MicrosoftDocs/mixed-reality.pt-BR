---
title: Integração do Sr e do Azure 312-bot
description: Conclua este curso para aprender a criar e implantar um bot, usando o Microsoft bot Framework v4 e se comunicar com ele em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, pesquisa Visual computacional, hololens, imersão, VR, Microsoft bot Framework v4, bot de aplicativo Web, bot Framework, Microsoft bot
ms.openlocfilehash: dc428f01a8333bf812fe03c59a46b7a2fa20df83
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438488"
---
>[!NOTE]
><span data-ttu-id="1f855-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="1f855-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1f855-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1f855-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1f855-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1f855-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1f855-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="1f855-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1f855-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1f855-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1f855-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="1f855-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="1f855-110">Sr e Azure 312: integração de bot</span><span class="sxs-lookup"><span data-stu-id="1f855-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="1f855-111">Neste curso, você aprenderá a criar e a implantar um bot usando o Microsoft bot Framework v4 e se comunicar com ele por meio de um aplicativo do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1f855-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="1f855-112">O **Microsoft bot Framework v4** é um conjunto de APIs projetado para fornecer aos desenvolvedores as ferramentas para criar um aplicativo de bot extensível e escalonável.</span><span class="sxs-lookup"><span data-stu-id="1f855-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="1f855-113">Para obter mais informações, visite a [página Microsoft bot Framework](https://dev.botframework.com/) ou o [repositório git v4](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span><span class="sxs-lookup"><span data-stu-id="1f855-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="1f855-114">Depois de concluir este curso, você terá criado um aplicativo do Windows Mixed Reality, que poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1f855-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="1f855-115">Use um **gesto de toque** para iniciar a escuta de bot para a voz dos usuários.</span><span class="sxs-lookup"><span data-stu-id="1f855-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="1f855-116">Quando o usuário disse algo, o bot tentará fornecer uma resposta.</span><span class="sxs-lookup"><span data-stu-id="1f855-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="1f855-117">Exiba as respostas de bots como texto, posicionadas próximo ao bot, na cena do Unity.</span><span class="sxs-lookup"><span data-stu-id="1f855-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="1f855-118">Em seu aplicativo, cabe a você como você integrará os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="1f855-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="1f855-119">Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="1f855-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="1f855-120">É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="1f855-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="1f855-121">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="1f855-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1f855-122">Course</span><span class="sxs-lookup"><span data-stu-id="1f855-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1f855-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1f855-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1f855-124"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="1f855-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1f855-125">Sr e Azure 312: integração de bot</span><span class="sxs-lookup"><span data-stu-id="1f855-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="1f855-126">✔️</span><span class="sxs-lookup"><span data-stu-id="1f855-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1f855-127">✔️</span><span class="sxs-lookup"><span data-stu-id="1f855-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="1f855-128">Embora este curso se concentre principalmente no HoloLens, você também pode aplicar o que aprende neste curso a fones de ouvido (VR) de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="1f855-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="1f855-129">Como os headsets de imersão (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu PC.</span><span class="sxs-lookup"><span data-stu-id="1f855-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="1f855-130">Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a headsets de imersão (VR).</span><span class="sxs-lookup"><span data-stu-id="1f855-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1f855-131">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1f855-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="1f855-132">Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o.</span><span class="sxs-lookup"><span data-stu-id="1f855-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="1f855-133">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (julho de 2018).</span><span class="sxs-lookup"><span data-stu-id="1f855-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="1f855-134">Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso correspondam perfeitamente ao que você encontrará no software mais recente do que o que está listado abaixo.</span><span class="sxs-lookup"><span data-stu-id="1f855-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="1f855-135">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="1f855-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="1f855-136">Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)</span><span class="sxs-lookup"><span data-stu-id="1f855-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="1f855-137">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="1f855-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1f855-138">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="1f855-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1f855-139">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="1f855-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1f855-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1f855-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="1f855-141">Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="1f855-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="1f855-142">Acesso à Internet para o Azure e para a recuperação do bot do Azure.</span><span class="sxs-lookup"><span data-stu-id="1f855-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="1f855-143">Para obter mais informações, [siga este link](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="1f855-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="1f855-144">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="1f855-144">Before you start</span></span>

1.  <span data-ttu-id="1f855-145">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="1f855-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="1f855-146">Configure e teste seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1f855-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="1f855-147">Se você precisar de suporte para configurar seu HoloLens, [visite o artigo configuração do hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="1f855-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="1f855-148">É uma boa ideia executar a calibragem e o ajuste do sensor ao começar a desenvolver um novo aplicativo do HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="1f855-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="1f855-149">Para obter ajuda sobre calibragem, siga este [link para o artigo Calibration do HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="1f855-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="1f855-150">Para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste do sensor do HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="1f855-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="1f855-151">Capítulo 1 – criar o aplicativo bot</span><span class="sxs-lookup"><span data-stu-id="1f855-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="1f855-152">A primeira etapa é criar o bot como um aplicativo Web ASP.Net Core local.</span><span class="sxs-lookup"><span data-stu-id="1f855-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="1f855-153">Depois de concluir e testar, você o publicará no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="1f855-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="1f855-154">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f855-154">Open Visual Studio.</span></span> <span data-ttu-id="1f855-155">Crie um novo projeto, selecione **aplicativo Web ASP .NET Core** como o tipo de projeto (você o encontrará na subseção .NET Core) e chame-o de **MyBot**.</span><span class="sxs-lookup"><span data-stu-id="1f855-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="1f855-156">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="1f855-156">Click **OK**.</span></span>

2.  <span data-ttu-id="1f855-157">Na janela que aparecerá, selecione **vazio**.</span><span class="sxs-lookup"><span data-stu-id="1f855-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="1f855-158">Verifique também se o destino está definido como **ASP NET Core 2,0** e se a autenticação está definida como **sem autenticação**.</span><span class="sxs-lookup"><span data-stu-id="1f855-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="1f855-159">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="1f855-159">Click **OK**.</span></span>  

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="1f855-161">A solução agora será aberta.</span><span class="sxs-lookup"><span data-stu-id="1f855-161">The solution will now open.</span></span> <span data-ttu-id="1f855-162">Clique com o botão direito do mouse em Solution **Mybot** na **Gerenciador de soluções** e clique em **Manage NuGet packages for Solution**.</span><span class="sxs-lookup"><span data-stu-id="1f855-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="1f855-164">Na guia **procurar** , procure **Microsoft. bot. Builder. Integration. AspNet. Core** (certifique-se de que **incluiu a versão prévia** verificada).</span><span class="sxs-lookup"><span data-stu-id="1f855-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="1f855-165">Selecione a versão do pacote **4.0.1-Preview**e marque as caixas do projeto.</span><span class="sxs-lookup"><span data-stu-id="1f855-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="1f855-166">Em seguida, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="1f855-166">Then click on **Install**.</span></span> <span data-ttu-id="1f855-167">Agora você instalou as bibliotecas necessárias para o **bot Framework v4**.</span><span class="sxs-lookup"><span data-stu-id="1f855-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="1f855-168">Feche a página NuGet.</span><span class="sxs-lookup"><span data-stu-id="1f855-168">Close the NuGet page.</span></span>

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="1f855-170">Clique com o botão direito do mouse em seu *projeto*, **MyBot**, na **Gerenciador de Soluções** e clique em **Adicionar** **|** **classe**.</span><span class="sxs-lookup"><span data-stu-id="1f855-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="1f855-172">Nomeie a classe **MyBot** e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="1f855-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="1f855-174">Repita o ponto anterior para criar outra classe chamada **ConversationContext**.</span><span class="sxs-lookup"><span data-stu-id="1f855-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="1f855-175">Clique com o botão direito do mouse em **wwwroot** no **Gerenciador de soluções** e clique em **Adicionar** **|** **novo item**.</span><span class="sxs-lookup"><span data-stu-id="1f855-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="1f855-176">Selecione a **página HTML** (você a encontrará na subseção Web).</span><span class="sxs-lookup"><span data-stu-id="1f855-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="1f855-177">Nomeie o arquivo **como default. html**.</span><span class="sxs-lookup"><span data-stu-id="1f855-177">Name the file **default.html**.</span></span> <span data-ttu-id="1f855-178">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="1f855-178">Click **Add**.</span></span>

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="1f855-180">A lista de classes/objetos no **Gerenciador de soluções** deve ser parecida com a imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="1f855-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="1f855-182">Clique duas vezes na classe **ConversationContext** .</span><span class="sxs-lookup"><span data-stu-id="1f855-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="1f855-183">Essa classe é responsável por conter as variáveis usadas pelo bot para manter o contexto da conversa.</span><span class="sxs-lookup"><span data-stu-id="1f855-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="1f855-184">Esses valores de contexto de conversa são mantidos em uma instância dessa classe, porque qualquer instância da classe **MyBot** será atualizada toda vez que uma atividade for recebida.</span><span class="sxs-lookup"><span data-stu-id="1f855-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="1f855-185">Adicione o seguinte código à classe:</span><span class="sxs-lookup"><span data-stu-id="1f855-185">Add the following code to the class:</span></span>

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. <span data-ttu-id="1f855-186">Clique duas vezes na classe **MyBot** .</span><span class="sxs-lookup"><span data-stu-id="1f855-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="1f855-187">Essa classe hospedará os manipuladores chamados por qualquer atividade de entrada do cliente.</span><span class="sxs-lookup"><span data-stu-id="1f855-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="1f855-188">Nessa classe, você adicionará o código usado para criar a conversa entre o bot e o cliente.</span><span class="sxs-lookup"><span data-stu-id="1f855-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="1f855-189">Como mencionado anteriormente, uma instância dessa classe é inicializada toda vez que uma atividade é recebida.</span><span class="sxs-lookup"><span data-stu-id="1f855-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="1f855-190">Adicione o seguinte código a esta classe:</span><span class="sxs-lookup"><span data-stu-id="1f855-190">Add the following code to this class:</span></span>

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. <span data-ttu-id="1f855-191">Clique duas vezes na classe **Startup** .</span><span class="sxs-lookup"><span data-stu-id="1f855-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="1f855-192">Essa classe irá inicializar o bot.</span><span class="sxs-lookup"><span data-stu-id="1f855-192">This class will initialize the bot.</span></span> <span data-ttu-id="1f855-193">Adicione o seguinte código à classe:</span><span class="sxs-lookup"><span data-stu-id="1f855-193">Add the following code to the class:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. <span data-ttu-id="1f855-194">Abra o arquivo de classe **programa** e verifique se o código nele é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1f855-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. <span data-ttu-id="1f855-195">Lembre-se de salvar suas alterações, para fazer isso, vá para **arquivo** > **salvar tudo**, na barra de ferramentas na parte superior do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f855-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="1f855-196">Capítulo 2 – criar o serviço de bot do Azure</span><span class="sxs-lookup"><span data-stu-id="1f855-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="1f855-197">Agora que você criou o código para o bot, é necessário publicá-lo em uma instância do serviço de *bot do aplicativo Web* , no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="1f855-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="1f855-198">Este capítulo mostrará como criar e configurar o serviço bot no Azure e, em seguida, publicar seu código nele.</span><span class="sxs-lookup"><span data-stu-id="1f855-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="1f855-199">Primeiro, faça logon no portal do Azure (https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="1f855-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="1f855-200">Se você ainda não tiver uma conta do Azure, será necessário criar uma.</span><span class="sxs-lookup"><span data-stu-id="1f855-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="1f855-201">Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="1f855-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="1f855-202">Depois de fazer logon, clique em **criar um recurso** no canto superior esquerdo e procure por *bot do aplicativo Web*e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1f855-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="1f855-204">A nova página fornecerá uma descrição do serviço de *bot do aplicativo Web* .</span><span class="sxs-lookup"><span data-stu-id="1f855-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="1f855-205">Na parte inferior esquerda desta página, selecione o botão **criar** para criar uma associação com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="1f855-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="1f855-207">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="1f855-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="1f855-208">Insira o **nome** desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="1f855-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="1f855-209">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="1f855-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="1f855-210">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="1f855-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1f855-211">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="1f855-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1f855-212">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="1f855-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="1f855-213">Se você quiser ler mais sobre grupos de recursos do Azure, [siga este link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="1f855-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="1f855-214">Determine o local do seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="1f855-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="1f855-215">O local ideal seria na região em que o aplicativo seria executado.</span><span class="sxs-lookup"><span data-stu-id="1f855-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="1f855-216">Alguns ativos do Azure só estão disponíveis em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="1f855-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="1f855-217">Selecione o **tipo de preço** apropriado para você, se esta for a primeira vez que criar um serviço de *bot de aplicativo Web* , uma camada gratuita (chamada F0) deverá estar disponível para você</span><span class="sxs-lookup"><span data-stu-id="1f855-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="1f855-218">O **nome do aplicativo** pode apenas ser deixado o mesmo que o nome do *bot*.</span><span class="sxs-lookup"><span data-stu-id="1f855-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="1f855-219">Deixe o *modelo de bot* como **básicoC#()** .</span><span class="sxs-lookup"><span data-stu-id="1f855-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="1f855-220">O *plano/local do serviço de aplicativo* deve ter sido preenchido automaticamente para sua conta.</span><span class="sxs-lookup"><span data-stu-id="1f855-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="1f855-221">Defina o **armazenamento do Azure** que você deseja usar para hospedar o bot.</span><span class="sxs-lookup"><span data-stu-id="1f855-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="1f855-222">Se você ainda não tiver um, poderá criá-lo aqui.</span><span class="sxs-lookup"><span data-stu-id="1f855-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="1f855-223">Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="1f855-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="1f855-224">Clique em criar.</span><span class="sxs-lookup"><span data-stu-id="1f855-224">Click Create.</span></span>
 
        ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="1f855-226">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="1f855-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="1f855-227">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="1f855-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="1f855-229">Clique na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="1f855-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="1f855-231">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="1f855-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="1f855-232">Você será levado para sua nova instância de serviço do Azure.</span><span class="sxs-lookup"><span data-stu-id="1f855-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="1f855-234">Neste ponto, você precisa configurar um recurso chamado **linha direta** para permitir que o aplicativo cliente se comunique com esse serviço de bot.</span><span class="sxs-lookup"><span data-stu-id="1f855-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="1f855-235">Clique em **canais**e, na seção **Adicionar um canal em destaque** , clique em **Configurar canal de linha direta**.</span><span class="sxs-lookup"><span data-stu-id="1f855-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="1f855-237">Nesta página, você encontrará as **chaves secretas** que permitirão que seu aplicativo cliente seja autenticado com o bot.</span><span class="sxs-lookup"><span data-stu-id="1f855-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="1f855-238">Clique no botão **Mostrar** e faça uma cópia de uma das chaves exibidas, pois você precisará dela posteriormente em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1f855-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="1f855-240">Capítulo 3 – publicar o bot no serviço de bot do aplicativo Web do Azure</span><span class="sxs-lookup"><span data-stu-id="1f855-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="1f855-241">Agora que seu serviço está pronto, você precisa publicar seu código de bot, que você criou anteriormente, para o serviço de bot do aplicativo Web criado recentemente.</span><span class="sxs-lookup"><span data-stu-id="1f855-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="1f855-242">Você precisará publicar o bot no serviço do Azure sempre que fizer alterações na solução/código de bot.</span><span class="sxs-lookup"><span data-stu-id="1f855-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="1f855-243">Volte para a solução do Visual Studio que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1f855-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="1f855-244">Clique com o botão direito do mouse no projeto **MyBot** , na **Gerenciador de soluções**e clique em **publicar**.</span><span class="sxs-lookup"><span data-stu-id="1f855-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![Publicar o bot no serviço de bot do aplicativo Web do Azure](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="1f855-246">Na página *escolher um destino de publicação* , clique em **serviço de aplicativo**e **selecione existente**, por fim, clique em **Criar perfil** (talvez seja necessário clicar na seta suspensa junto com o botão *publicar* , se isso não estiver visível).</span><span class="sxs-lookup"><span data-stu-id="1f855-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![Publicar o bot no serviço de bot do aplicativo Web do Azure](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="1f855-248">Se você ainda não estiver conectado à sua conta da Microsoft, precisará fazê-lo aqui.</span><span class="sxs-lookup"><span data-stu-id="1f855-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="1f855-249">Na página **publicar** , você verá que precisa definir a mesma **assinatura** que usou para a criação do serviço de *bot do aplicativo Web* .</span><span class="sxs-lookup"><span data-stu-id="1f855-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="1f855-250">Em seguida, defina a **exibição** como **grupo de recursos** e, na estrutura de pastas suspensa, selecione o **grupo de recursos** que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1f855-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="1f855-251">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="1f855-251">Click **OK**.</span></span> 

    ![Publicar o bot no serviço de bot do aplicativo Web do Azure](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="1f855-253">Agora, clique no botão **publicar** e aguarde até que o bot seja publicado (pode levar alguns minutos).</span><span class="sxs-lookup"><span data-stu-id="1f855-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![Publicar o bot no serviço de bot do aplicativo Web do Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="1f855-255">Capítulo 4 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="1f855-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="1f855-256">A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="1f855-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="1f855-257">Abra o *Unity* e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="1f855-257">Open *Unity* and click **New**.</span></span> 

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="1f855-259">Agora, você precisará fornecer um nome de projeto de Unity.</span><span class="sxs-lookup"><span data-stu-id="1f855-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="1f855-260">Inserir **bot do HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="1f855-260">Insert **HoloLens Bot**.</span></span> <span data-ttu-id="1f855-261">Verifique se o modelo de projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="1f855-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="1f855-262">Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="1f855-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1f855-263">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="1f855-263">Then, click **Create project**.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="1f855-265">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1f855-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="1f855-266">Vá para **Editar preferências de >** e, em seguida, na nova janela, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="1f855-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1f855-267">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="1f855-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="1f855-268">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="1f855-268">Close the **Preferences** window.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="1f855-270">Em seguida, vá para **arquivo > configurações de Build** e selecione **plataforma universal do Windows**e, em seguida, clique no botão **alternar plataforma** para aplicar sua seleção.</span><span class="sxs-lookup"><span data-stu-id="1f855-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="1f855-272">Ainda no **arquivo > configurações de compilação** e certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="1f855-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="1f855-273">O **dispositivo de destino** está definido como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="1f855-273">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="1f855-274">Para os headsets de imersão, defina **dispositivo de destino** para *qualquer dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="1f855-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="1f855-275">O **tipo de compilação** está definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="1f855-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="1f855-276">O **SDK** está definido para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="1f855-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="1f855-277">A **versão do Visual Studio** está definida para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="1f855-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="1f855-278">**Compilar e executar** é definido como **computador local**</span><span class="sxs-lookup"><span data-stu-id="1f855-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="1f855-279">Salve a cena e adicione-a à compilação.</span><span class="sxs-lookup"><span data-stu-id="1f855-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="1f855-280">Faça isso selecionando **Adicionar abrir cenas**.</span><span class="sxs-lookup"><span data-stu-id="1f855-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="1f855-281">Uma janela salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="1f855-281">A save window will appear.</span></span>
        
            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="1f855-283">Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.</span><span class="sxs-lookup"><span data-stu-id="1f855-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Configurar o projeto do Unity](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="1f855-285">Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo*:, digite **BotScene**e clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="1f855-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="1f855-287">As configurações restantes, em **configurações de compilação**, devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="1f855-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="1f855-288">Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="1f855-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="1f855-290">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="1f855-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="1f855-291">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="1f855-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="1f855-292">A **versão de tempo de execução de script** deve ser **Experimental (NET 4,6 equivalente)** ; alterar isso exigirá uma reinicialização do editor.</span><span class="sxs-lookup"><span data-stu-id="1f855-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="1f855-293">O **back-end de script** deve ser **.net**</span><span class="sxs-lookup"><span data-stu-id="1f855-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="1f855-294">O **nível de compatibilidade da API** deve ser **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="1f855-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="1f855-296">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="1f855-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="1f855-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="1f855-297">**InternetClient**</span></span>
        - <span data-ttu-id="1f855-298">**Phone**</span><span class="sxs-lookup"><span data-stu-id="1f855-298">**Microphone**</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="1f855-300">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o **SDK do Windows Mixed Reality** foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="1f855-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurar o projeto do Unity](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="1f855-302">De volta *às configurações de Build* , os projetos do  _C# Unity_ não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste.</span><span class="sxs-lookup"><span data-stu-id="1f855-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="1f855-303">Feche a janela configurações de compilação.</span><span class="sxs-lookup"><span data-stu-id="1f855-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="1f855-304">Salve sua cena e projeto (**arquivo > salvar cena/arquivo > salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="1f855-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="1f855-305">Capítulo 5 – configuração da câmera</span><span class="sxs-lookup"><span data-stu-id="1f855-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f855-306">Se você quiser ignorar o componente de *configuração do Unity* deste curso e continuar diretamente no código, sinta-se à vontade para baixar este [Azure-Mr-312-Package. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), importá-lo em seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuar de [ Capítulo 7](#chapter-8--create-the-botobjects-class).</span><span class="sxs-lookup"><span data-stu-id="1f855-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-8--create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="1f855-307">No *painel hierarquia*, selecione a **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="1f855-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="1f855-308">Depois de selecionado, você poderá ver todos os componentes da **câmera principal** no *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="1f855-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="1f855-309">O **objeto de câmera** deve ser nomeado como a **câmera principal** (Observe a grafia)</span><span class="sxs-lookup"><span data-stu-id="1f855-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="1f855-310">A **marca** da câmera principal deve ser definida como **MainCamera** (Observe a grafia)</span><span class="sxs-lookup"><span data-stu-id="1f855-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="1f855-311">Verifique se a **posição de transformação** está definida como **0, 0,** 0</span><span class="sxs-lookup"><span data-stu-id="1f855-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="1f855-312">Defina **limpar sinalizadores** como **cor sólida**.</span><span class="sxs-lookup"><span data-stu-id="1f855-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="1f855-313">Defina a cor do **plano de fundo** do componente da câmera como **preto, alfa 0 (código hex: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="1f855-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![Configuração da câmera](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="1f855-315">Capítulo 6 – importar a biblioteca Newtonsoft</span><span class="sxs-lookup"><span data-stu-id="1f855-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="1f855-316">Para ajudá-lo a desserializar e serializar objetos recebidos e enviados ao serviço bot, você precisa baixar a biblioteca **Newtonsoft** .</span><span class="sxs-lookup"><span data-stu-id="1f855-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="1f855-317">Você encontrará uma [versão compatível já organizada com a estrutura de pasta do Unity correta aqui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="1f855-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="1f855-318">Para importar a biblioteca Newtonsoft para seu projeto, use o pacote do Unity que acompanha este curso.</span><span class="sxs-lookup"><span data-stu-id="1f855-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="1f855-319">Adicione o *. unitypackage* ao Unity usando a opção de menu **ativos** > **Importar pacote** > **pacote personalizado** .</span><span class="sxs-lookup"><span data-stu-id="1f855-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Importar a biblioteca Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="1f855-321">Na caixa **Importar pacote de Unity** que é exibida, verifique se tudo em (e incluindo) **plug-ins** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="1f855-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importar a biblioteca Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="1f855-323">Clique no botão **importar** para adicionar os itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1f855-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="1f855-324">Vá para a pasta **Newtonsoft** em **plug-ins** na exibição de projeto e selecione o plug-in Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="1f855-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="1f855-325">Com o plug-in Newtonsoft selecionado, verifique se **qualquer plataforma** está **desmarcada**e, em seguida, verifique se o **WSAPlayer** também está **desmarcado**e clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="1f855-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="1f855-326">Isso é apenas para confirmar que os arquivos estão configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="1f855-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="1f855-327">Marcar esses plug-ins os configura para ser usado apenas no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="1f855-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="1f855-328">Há um conjunto diferente deles na pasta WSA que será usada depois que o projeto for exportado do Unity.</span><span class="sxs-lookup"><span data-stu-id="1f855-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="1f855-329">Em seguida, você precisa abrir a pasta **WSA** , dentro da pasta **Newtonsoft** .</span><span class="sxs-lookup"><span data-stu-id="1f855-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="1f855-330">Você verá uma cópia do mesmo arquivo que acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="1f855-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="1f855-331">Selecione o arquivo e, no Inspetor, verifique se</span><span class="sxs-lookup"><span data-stu-id="1f855-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="1f855-332">**Qualquer plataforma** está **desmarcada**</span><span class="sxs-lookup"><span data-stu-id="1f855-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="1f855-333">**somente** **WSAPlayer** está **marcado**</span><span class="sxs-lookup"><span data-stu-id="1f855-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="1f855-334">Não **processar** está **marcado**</span><span class="sxs-lookup"><span data-stu-id="1f855-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="1f855-335">Capítulo 7 – criar o BotTag</span><span class="sxs-lookup"><span data-stu-id="1f855-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="1f855-336">Crie um novo objeto de **marca** chamado **BotTag**.</span><span class="sxs-lookup"><span data-stu-id="1f855-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="1f855-337">Selecione a câmera principal na cena.</span><span class="sxs-lookup"><span data-stu-id="1f855-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="1f855-338">Clique no menu suspenso marca no painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="1f855-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="1f855-339">Clique em **adicionar marca**.</span><span class="sxs-lookup"><span data-stu-id="1f855-339">Click on **Add Tag**.</span></span>

    ![Configuração da câmera](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="1f855-341">Clique no símbolo de **+** .</span><span class="sxs-lookup"><span data-stu-id="1f855-341">Click on the **+** symbol.</span></span> <span data-ttu-id="1f855-342">Nomeie a nova **marca** como **BotTag**, *salve*.</span><span class="sxs-lookup"><span data-stu-id="1f855-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![Configuração da câmera](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="1f855-344">**Não** aplique o **BotTag** à câmera principal.</span><span class="sxs-lookup"><span data-stu-id="1f855-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="1f855-345">Se você tiver feito isso acidentalmente, certifique-se de alterar a marca da câmera principal de volta para *MainCamera*.</span><span class="sxs-lookup"><span data-stu-id="1f855-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="1f855-346">Capítulo 8 – criar a classe BotObjects</span><span class="sxs-lookup"><span data-stu-id="1f855-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="1f855-347">O primeiro script que você precisa criar é a classe **BotObjects** , que é uma classe vazia criada para que uma série de outros objetos de classe possa ser armazenada dentro do mesmo script e acessada por outros scripts na cena.</span><span class="sxs-lookup"><span data-stu-id="1f855-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="1f855-348">A criação dessa classe é puramente uma opção arquitetônica, esses objetos podem ser hospedados no script bot que você criará posteriormente neste curso.</span><span class="sxs-lookup"><span data-stu-id="1f855-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="1f855-349">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="1f855-349">To create this class:</span></span> 

1.  <span data-ttu-id="1f855-350">Clique com o botão direito do mouse no *painel Projeto*e **crie > pasta**.</span><span class="sxs-lookup"><span data-stu-id="1f855-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="1f855-351">Nomeie a pasta **scripts**.</span><span class="sxs-lookup"><span data-stu-id="1f855-351">Name the folder **Scripts**.</span></span> 

    ![Criar pasta de scripts.](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="1f855-353">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="1f855-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="1f855-354">Em seguida, dentro dessa pasta, clique com o botão direito do mouse e selecione **criar > C# script**.</span><span class="sxs-lookup"><span data-stu-id="1f855-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="1f855-355">Nomeie o script **BotObjects**.</span><span class="sxs-lookup"><span data-stu-id="1f855-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="1f855-356">Clique duas vezes no novo script **BotObjects** para abri-lo com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1f855-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="1f855-357">Exclua o conteúdo do script e substitua-o pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="1f855-357">Delete the content of the script and replace it with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  <span data-ttu-id="1f855-358">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="1f855-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="1f855-359">Capítulo 9 – criar a classe GazeInput</span><span class="sxs-lookup"><span data-stu-id="1f855-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="1f855-360">A próxima classe que você vai criar é a classe **GazeInput** .</span><span class="sxs-lookup"><span data-stu-id="1f855-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="1f855-361">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="1f855-361">This class is responsible for:</span></span>

- <span data-ttu-id="1f855-362">Criar um cursor que representará o *olhar* do Player.</span><span class="sxs-lookup"><span data-stu-id="1f855-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="1f855-363">Detectar objetos atingidos pelo olhar do Player e manter uma referência a objetos detectados.</span><span class="sxs-lookup"><span data-stu-id="1f855-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="1f855-364">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="1f855-364">To create this class:</span></span> 

1.  <span data-ttu-id="1f855-365">Vá para a pasta **scripts** que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1f855-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="1f855-366">Clique com o botão direito do mouse dentro da pasta, **crie > C# script**.</span><span class="sxs-lookup"><span data-stu-id="1f855-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="1f855-367">Chame o script **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="1f855-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="1f855-368">Clique duas vezes no novo script **GazeInput** para abri-lo com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1f855-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="1f855-369">Insira a linha a seguir na parte superior do nome da classe:</span><span class="sxs-lookup"><span data-stu-id="1f855-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="1f855-370">Em seguida, adicione as seguintes variáveis dentro da classe **GazeInput** , acima do método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="1f855-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

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

6.  <span data-ttu-id="1f855-371">O código para o método **Start ()** deve ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="1f855-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="1f855-372">Isso será chamado quando a classe for inicializada:</span><span class="sxs-lookup"><span data-stu-id="1f855-372">This will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="1f855-373">Implemente um método que criará uma instância e configurará o cursor olhar:</span><span class="sxs-lookup"><span data-stu-id="1f855-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  <span data-ttu-id="1f855-374">Implemente os métodos que irão configurar o Raycast da câmera principal e acompanhará o objeto focalizado atual.</span><span class="sxs-lookup"><span data-stu-id="1f855-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

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
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
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
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  <span data-ttu-id="1f855-375">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="1f855-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="1f855-376">Capítulo 10 – criar a classe bot</span><span class="sxs-lookup"><span data-stu-id="1f855-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="1f855-377">O script que você vai criar agora é chamado de **bot**.</span><span class="sxs-lookup"><span data-stu-id="1f855-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="1f855-378">Essa é a classe principal do seu aplicativo, armazena:</span><span class="sxs-lookup"><span data-stu-id="1f855-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="1f855-379">Suas credenciais de bot do aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="1f855-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="1f855-380">O método que coleta os comandos de voz do usuário</span><span class="sxs-lookup"><span data-stu-id="1f855-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="1f855-381">O método necessário para iniciar conversas com o bot do aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="1f855-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="1f855-382">O método necessário para enviar mensagens para o bot do aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="1f855-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="1f855-383">Para enviar mensagens para o serviço bot, a corotina **SendMessageToBot ()** criará uma atividade, que é um objeto reconhecido pela estrutura de bot como dados enviados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="1f855-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="1f855-384">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="1f855-384">To create this class:</span></span> 

1. <span data-ttu-id="1f855-385">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="1f855-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="1f855-386">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > C# script**.</span><span class="sxs-lookup"><span data-stu-id="1f855-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="1f855-387">Nomeie o script **bot**.</span><span class="sxs-lookup"><span data-stu-id="1f855-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="1f855-388">Clique duas vezes no novo script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f855-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="1f855-389">Atualize os namespaces para que sejam iguais aos seguintes, na parte superior da classe **bot** :</span><span class="sxs-lookup"><span data-stu-id="1f855-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="1f855-390">Dentro da classe **bot** , adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="1f855-390">Inside the **Bot** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > <span data-ttu-id="1f855-391">Certifique-se de inserir a **chave secreta de bot** na variável **botSecret** .</span><span class="sxs-lookup"><span data-stu-id="1f855-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="1f855-392">Você terá anotado sua **chave secreta de bot** no início deste curso, no  **[capítulo 2](#chapter-2---create-the-azure-bot-service), etapa 10**.</span><span class="sxs-lookup"><span data-stu-id="1f855-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="1f855-393">O código para **ativo ()** e **Start ()** agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="1f855-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. <span data-ttu-id="1f855-394">Adicione os dois manipuladores que são chamados pelas bibliotecas de fala quando a captura de voz começa e termina.</span><span class="sxs-lookup"><span data-stu-id="1f855-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="1f855-395">O *DictationRecognizer* interromperá automaticamente a captura da voz do usuário quando o usuário parar de falar.</span><span class="sxs-lookup"><span data-stu-id="1f855-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. <span data-ttu-id="1f855-396">O manipulador a seguir coleta o resultado da entrada de voz do usuário e chama a corrotina responsável por enviar a mensagem para o serviço de bot do aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="1f855-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. <span data-ttu-id="1f855-397">A seguinte corrotina é chamada para iniciar uma conversa com o bot.</span><span class="sxs-lookup"><span data-stu-id="1f855-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="1f855-398">Você observará que, depois que a chamada de conversa for concluída, ela chamará o **SendMessageToCoroutine ()** passando uma série de parâmetros que definirão a atividade a ser enviada ao serviço bot como uma mensagem vazia.</span><span class="sxs-lookup"><span data-stu-id="1f855-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="1f855-399">Isso é feito para solicitar que o serviço de bot inicie a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="1f855-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. <span data-ttu-id="1f855-400">A seguinte corrotina é chamada para criar a atividade a ser enviada ao serviço bot.</span><span class="sxs-lookup"><span data-stu-id="1f855-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. <span data-ttu-id="1f855-401">A seguinte corrotina é chamada para solicitar uma resposta depois de enviar uma atividade para o serviço de bot.</span><span class="sxs-lookup"><span data-stu-id="1f855-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. <span data-ttu-id="1f855-402">O último método a ser adicionado a essa classe é necessário para exibir a mensagem na cena:</span><span class="sxs-lookup"><span data-stu-id="1f855-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="1f855-403">Você pode ver um erro no console do editor do Unity, sobre a ausência da classe **SceneOrganiser** .</span><span class="sxs-lookup"><span data-stu-id="1f855-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="1f855-404">Desconsidere esta mensagem, pois você criará essa classe posteriormente no tutorial.</span><span class="sxs-lookup"><span data-stu-id="1f855-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="1f855-405">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="1f855-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="1f855-406">Capítulo 11 – criar a classe interações</span><span class="sxs-lookup"><span data-stu-id="1f855-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="1f855-407">A classe que você pretende criar agora é chamada de **interações**.</span><span class="sxs-lookup"><span data-stu-id="1f855-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="1f855-408">Essa classe é usada para detectar a entrada de toque do HoloLens do usuário.</span><span class="sxs-lookup"><span data-stu-id="1f855-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="1f855-409">Se o usuário tocar enquanto examina o objeto *bot* na cena e o bot estiver pronto para escutar entradas de voz, o objeto bot mudará de cor para **vermelho** e começará a escutar as entradas de voz.</span><span class="sxs-lookup"><span data-stu-id="1f855-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="1f855-410">Essa classe herda da classe **GazeInput** e, portanto, é capaz de fazer referência ao método **Start ()** e às variáveis dessa classe, denotada pelo uso de **base**.</span><span class="sxs-lookup"><span data-stu-id="1f855-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="1f855-411">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="1f855-411">To create this class:</span></span>

1.  <span data-ttu-id="1f855-412">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="1f855-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="1f855-413">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > C# script**.</span><span class="sxs-lookup"><span data-stu-id="1f855-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="1f855-414">Nomeie o script de **interações**.</span><span class="sxs-lookup"><span data-stu-id="1f855-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="1f855-415">Clique duas vezes no novo script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f855-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="1f855-416">Atualize os namespaces e a herança de classe para ser o mesmo que o seguinte, na parte superior da classe **interações** :</span><span class="sxs-lookup"><span data-stu-id="1f855-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="1f855-417">Dentro da classe **interações** , adicione a seguinte variável:</span><span class="sxs-lookup"><span data-stu-id="1f855-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="1f855-418">Em seguida, adicione o método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="1f855-418">Then add the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="1f855-419">Adicione o manipulador que será disparado quando o usuário executar o gesto de toque na frente da câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="1f855-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. <span data-ttu-id="1f855-420">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="1f855-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="1f855-421">Capítulo 12 – criar a classe SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="1f855-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="1f855-422">A última classe necessária neste laboratório é chamada de **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="1f855-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="1f855-423">Essa classe configurará a cena programaticamente, adicionando componentes e scripts à câmera principal e criando os objetos apropriados na cena.</span><span class="sxs-lookup"><span data-stu-id="1f855-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="1f855-424">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="1f855-424">To create this class:</span></span>

1.  <span data-ttu-id="1f855-425">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="1f855-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="1f855-426">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > C# script**.</span><span class="sxs-lookup"><span data-stu-id="1f855-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="1f855-427">Nomeie o script **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="1f855-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="1f855-428">Clique duas vezes no novo script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f855-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="1f855-429">Dentro da classe **SceneOrganiser** , adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="1f855-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  <span data-ttu-id="1f855-430">Em seguida, adicione os métodos **ativo ()** e **Iniciar ()** :</span><span class="sxs-lookup"><span data-stu-id="1f855-430">Then add the **Awake()** and **Start()** methods:</span></span>

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  <span data-ttu-id="1f855-431">Adicione o seguinte método, responsável por criar o objeto bot na cena e configurar os parâmetros e os componentes:</span><span class="sxs-lookup"><span data-stu-id="1f855-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  <span data-ttu-id="1f855-432">Adicione o seguinte método, responsável por criar o objeto de interface do usuário na cena, representando as respostas do bot:</span><span class="sxs-lookup"><span data-stu-id="1f855-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  <span data-ttu-id="1f855-433">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="1f855-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="1f855-434">No editor do Unity, arraste o script **SceneOrganiser** da pasta scripts para a câmera principal.</span><span class="sxs-lookup"><span data-stu-id="1f855-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="1f855-435">O componente de Organizer de cena agora deve aparecer no objeto de câmera principal, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="1f855-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Criar o serviço de bot do Azure](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="1f855-437">Capítulo 13 – antes de criar</span><span class="sxs-lookup"><span data-stu-id="1f855-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="1f855-438">Para executar um teste completo de seu aplicativo, você precisará Sideload-lo no seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1f855-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="1f855-439">Antes de fazer isso, verifique se:</span><span class="sxs-lookup"><span data-stu-id="1f855-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="1f855-440">Todas as configurações mencionadas no [**capítulo 4**](#chapter-4--set-up-the-unity-project) são definidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="1f855-440">All the settings mentioned in the [**Chapter 4**](#chapter-4--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="1f855-441">O script **SceneOrganiser** é anexado ao objeto da **câmera principal** .</span><span class="sxs-lookup"><span data-stu-id="1f855-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="1f855-442">Na classe **bot** , verifique se você inseriu a **chave secreta de bot** na variável **botSecret** .</span><span class="sxs-lookup"><span data-stu-id="1f855-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="1f855-443">Capítulo 14 – criar e Sideloadr para o HoloLens</span><span class="sxs-lookup"><span data-stu-id="1f855-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="1f855-444">Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.</span><span class="sxs-lookup"><span data-stu-id="1f855-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="1f855-445">Navegue até **configurações de compilação**, **arquivo > configurações de compilação...** .</span><span class="sxs-lookup"><span data-stu-id="1f855-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="1f855-446">Na janela **configurações de compilação** , clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="1f855-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilando o aplicativo do Unity](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="1f855-448">Se ainda não estiver, **os C# projetos de Unity**de tique.</span><span class="sxs-lookup"><span data-stu-id="1f855-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="1f855-449">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="1f855-449">Click **Build**.</span></span> <span data-ttu-id="1f855-450">O Unity iniciará uma janela **Explorador de arquivos** , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado.</span><span class="sxs-lookup"><span data-stu-id="1f855-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="1f855-451">Crie essa pasta agora e nomeie-a como **aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="1f855-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="1f855-452">Em seguida, com a pasta de **aplicativo** selecionada, clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="1f855-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="1f855-453">O Unity começará a criar seu projeto na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="1f855-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="1f855-454">Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).</span><span class="sxs-lookup"><span data-stu-id="1f855-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="1f855-455">Capítulo 15 – implantar no HoloLens</span><span class="sxs-lookup"><span data-stu-id="1f855-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="1f855-456">Para implantar no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="1f855-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="1f855-457">Você precisará do endereço IP do seu HoloLens (para implantação remota) e para garantir que seu HoloLens esteja no **modo de desenvolvedor**.</span><span class="sxs-lookup"><span data-stu-id="1f855-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="1f855-458">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="1f855-458">To do this:</span></span>

    1. <span data-ttu-id="1f855-459">Enquanto estiver desgastando seu HoloLens, abra as **configurações**.</span><span class="sxs-lookup"><span data-stu-id="1f855-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="1f855-460">Acessar **Opções de rede & Internet > Wi-Fi > avançado**</span><span class="sxs-lookup"><span data-stu-id="1f855-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="1f855-461">Anote o endereço **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="1f855-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="1f855-462">Em seguida, navegue de volta para **configurações**e, em seguida, **atualize & > de segurança para desenvolvedores**</span><span class="sxs-lookup"><span data-stu-id="1f855-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="1f855-463">Defina o modo de desenvolvedor em.</span><span class="sxs-lookup"><span data-stu-id="1f855-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="1f855-464">Navegue até sua nova compilação do Unity (a pasta do **aplicativo** ) e abra o arquivo de solução com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1f855-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="1f855-465">Na **configuração da solução** , selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="1f855-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="1f855-466">Na **plataforma da solução**, selecione **x86**, **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="1f855-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="1f855-468">Vá para o **menu Compilar** e clique em **implantar solução**para Sideload o aplicativo ao seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1f855-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="1f855-469">Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="1f855-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f855-470">Para implantar em headsets de imersão, defina a **plataforma da solução** como *computador local*e defina a **configuração** a ser *depurada*, com *x86* como a **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="1f855-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="1f855-471">Em seguida, implante no computador local, usando o **menu Compilar**, selecionando *implantar solução*.</span><span class="sxs-lookup"><span data-stu-id="1f855-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="1f855-472">Capítulo 16 – usando o aplicativo no HoloLens</span><span class="sxs-lookup"><span data-stu-id="1f855-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="1f855-473">Depois de iniciar o aplicativo, você verá o bot como uma esfera azul na frente de você.</span><span class="sxs-lookup"><span data-stu-id="1f855-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="1f855-474">Use o **gesto de toque** enquanto você estiver nuvens na esfera para iniciar uma conversa.</span><span class="sxs-lookup"><span data-stu-id="1f855-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="1f855-475">Aguarde até que a conversa seja iniciada (a interface do usuário exibirá uma mensagem quando ela ocorrer).</span><span class="sxs-lookup"><span data-stu-id="1f855-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="1f855-476">Depois de receber a mensagem introdutória do bot, toque novamente no bot para que ele se transforme em vermelho e comece a escutar sua voz.</span><span class="sxs-lookup"><span data-stu-id="1f855-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="1f855-477">Depois de parar de conversar, seu aplicativo enviará sua mensagem para o bot e você receberá uma resposta que será exibida na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1f855-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="1f855-478">Repita o processo para enviar mais mensagens para o bot (você precisa tocar sempre que desejar receber uma mensagem).</span><span class="sxs-lookup"><span data-stu-id="1f855-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="1f855-479">Essa conversa demonstra como o bot pode reter informações (seu nome), enquanto fornece também informações conhecidas (como os itens que estão em estoque).</span><span class="sxs-lookup"><span data-stu-id="1f855-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="1f855-480">Algumas perguntas a serem feitas ao bot:</span><span class="sxs-lookup"><span data-stu-id="1f855-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="1f855-481">Seu aplicativo Web App bot (v4) concluído</span><span class="sxs-lookup"><span data-stu-id="1f855-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="1f855-482">Parabéns, você criou um aplicativo de realidade misturada que aproveita o bot do aplicativo Web do Azure, o Microsoft bot Framework v4.</span><span class="sxs-lookup"><span data-stu-id="1f855-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![Produto final](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="1f855-484">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="1f855-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="1f855-485">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="1f855-485">Exercise 1</span></span>

<span data-ttu-id="1f855-486">A estrutura de conversa neste laboratório é muito básica.</span><span class="sxs-lookup"><span data-stu-id="1f855-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="1f855-487">Use o Microsoft LUIS para dar aos seus recursos de reconhecimento de linguagem natural de bot.</span><span class="sxs-lookup"><span data-stu-id="1f855-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="1f855-488">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="1f855-488">Exercise 2</span></span>

<span data-ttu-id="1f855-489">Este exemplo não inclui o encerramento de uma conversa e a reinicialização de uma nova.</span><span class="sxs-lookup"><span data-stu-id="1f855-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="1f855-490">Para que o recurso de bot seja concluído, tente implementar o fechamento na conversa.</span><span class="sxs-lookup"><span data-stu-id="1f855-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
