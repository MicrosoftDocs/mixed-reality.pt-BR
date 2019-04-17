---
title: MR e 312 Azure - integração do Bot
description: Conclua este curso para aprender a criar e implantar um bot, usando o Microsoft Bot Framework v4 e se comunicar com ele em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, pesquisa Visual computacional, hololens, vr de imersão, microsoft bot framework v4, bot de aplicativo web, estrutura do bot, bot da microsoft
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590996"
---
>[!NOTE]
><span data-ttu-id="d5666-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="d5666-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d5666-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="d5666-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d5666-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="d5666-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d5666-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="d5666-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d5666-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d5666-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d5666-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="d5666-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="d5666-110">MR e o Azure 312: Integração do bot</span><span class="sxs-lookup"><span data-stu-id="d5666-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="d5666-111">Neste curso, você aprenderá como criar e implantar um bot usando a V4 do Microsoft Bot Framework e se comunicar com ele por meio de um aplicativo de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="d5666-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="d5666-112">O **Microsoft Bot Framework V4** é um conjunto de APIs projetado para fornecer aos desenvolvedores as ferramentas para compilar um bot extensível e escalonável com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d5666-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="d5666-113">Para obter mais informações, visite o [página do Microsoft Bot Framework](https://dev.botframework.com/) ou o [repositório de Git V4](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span><span class="sxs-lookup"><span data-stu-id="d5666-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="d5666-114">Depois de concluir este curso, você terá criado um aplicativo de realidade mista do Windows, será possível fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d5666-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="d5666-115">Use uma **gestos de toque** para iniciar o bot de escuta de voz a usuários.</span><span class="sxs-lookup"><span data-stu-id="d5666-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="d5666-116">Quando o usuário disse algo, o bot tentará fornecer uma resposta.</span><span class="sxs-lookup"><span data-stu-id="d5666-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="d5666-117">Exibe a resposta de bots como texto, posicionado perto o bot, na cena Unity.</span><span class="sxs-lookup"><span data-stu-id="d5666-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="d5666-118">Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="d5666-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="d5666-119">Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="d5666-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="d5666-120">Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="d5666-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="d5666-121">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="d5666-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d5666-122">Curso</span><span class="sxs-lookup"><span data-stu-id="d5666-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d5666-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d5666-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d5666-124"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="d5666-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d5666-125">MR e o Azure 312: Integração do bot</span><span class="sxs-lookup"><span data-stu-id="d5666-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="d5666-126">✔️</span><span class="sxs-lookup"><span data-stu-id="d5666-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d5666-127">✔️</span><span class="sxs-lookup"><span data-stu-id="d5666-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="d5666-128">Enquanto este curso se concentra principalmente em HoloLens, você também pode aplicar o que você aprenderá neste curso para fones de ouvido Windows Mixed Reality de imersão (VR).</span><span class="sxs-lookup"><span data-stu-id="d5666-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="d5666-129">Como fones imersivos em exposição (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="d5666-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="d5666-130">Como acompanhar o curso, você verá notas quaisquer alterações que você talvez precise ser empregadas para dar suporte a fones imersivos em exposição (VR).</span><span class="sxs-lookup"><span data-stu-id="d5666-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d5666-131">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d5666-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="d5666-132">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="d5666-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="d5666-133">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (julho de 2018).</span><span class="sxs-lookup"><span data-stu-id="d5666-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="d5666-134">Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que está listado abaixo.</span><span class="sxs-lookup"><span data-stu-id="d5666-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="d5666-135">Recomendamos que o hardware e software para este curso a seguir:</span><span class="sxs-lookup"><span data-stu-id="d5666-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="d5666-136">Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)</span><span class="sxs-lookup"><span data-stu-id="d5666-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="d5666-137">Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="d5666-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d5666-138">O SDK mais recente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="d5666-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d5666-139">2017.4 do Unity</span><span class="sxs-lookup"><span data-stu-id="d5666-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d5666-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d5666-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="d5666-141">Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="d5666-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="d5666-142">Acesso à Internet para o Azure e para recuperação de Bot do Azure.</span><span class="sxs-lookup"><span data-stu-id="d5666-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="d5666-143">Para obter mais informações, [, siga este link](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="d5666-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="d5666-144">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="d5666-144">Before you start</span></span>

1.  <span data-ttu-id="d5666-145">Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="d5666-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="d5666-146">Configurar e testar o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d5666-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="d5666-147">Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="d5666-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="d5666-148">É uma boa ideia executar calibragem e ajuste de Sensor ao começar a desenvolver um novo aplicativo HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="d5666-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="d5666-149">Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="d5666-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="d5666-150">Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="d5666-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="d5666-151">Capítulo 1 – criar o aplicativo Bot</span><span class="sxs-lookup"><span data-stu-id="d5666-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="d5666-152">A primeira etapa é criar seu bot como um aplicativo Web do ASP.Net Core local.</span><span class="sxs-lookup"><span data-stu-id="d5666-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="d5666-153">Depois de concluído e testá-lo, você será publicá-lo no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="d5666-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="d5666-154">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5666-154">Open Visual Studio.</span></span> <span data-ttu-id="d5666-155">Criar um novo projeto, selecione **aplicativo Web do ASP NET Core** como o tipo de projeto (você irá encontrá-la sob a subseção do .NET Core) e chamá-lo **MyBot**.</span><span class="sxs-lookup"><span data-stu-id="d5666-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="d5666-156">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="d5666-156">Click **OK**.</span></span>

2.  <span data-ttu-id="d5666-157">Na janela que aparecerá select **vazio**.</span><span class="sxs-lookup"><span data-stu-id="d5666-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="d5666-158">Também verifique se o destino é definido como **ASP NET Core 2.0** e a autenticação está definida como **sem autenticação**.</span><span class="sxs-lookup"><span data-stu-id="d5666-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="d5666-159">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="d5666-159">Click **OK**.</span></span>  

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="d5666-161">A solução agora será aberto.</span><span class="sxs-lookup"><span data-stu-id="d5666-161">The solution will now open.</span></span> <span data-ttu-id="d5666-162">Clique com botão direito na solução **Mybot** na **Gerenciador de soluções** e clique em **gerenciar pacotes NuGet para solução**.</span><span class="sxs-lookup"><span data-stu-id="d5666-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![Criar o aplicativo Bot](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="d5666-164">No **procurar** guia, pesquise por **Microsoft.Bot.Builder.Integration.AspNet.Core** (Verifique se você tem **incluir pré-lançamento** marcada).</span><span class="sxs-lookup"><span data-stu-id="d5666-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="d5666-165">Selecione a versão do pacote **4.0.1-Preview**, marque as caixas de projeto.</span><span class="sxs-lookup"><span data-stu-id="d5666-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="d5666-166">Em seguida, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="d5666-166">Then click on **Install**.</span></span> <span data-ttu-id="d5666-167">Agora você instalou as bibliotecas necessárias para o **v4 do Bot Framework**.</span><span class="sxs-lookup"><span data-stu-id="d5666-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="d5666-168">Feche a página do NuGet.</span><span class="sxs-lookup"><span data-stu-id="d5666-168">Close the NuGet page.</span></span>

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="d5666-170">Clique com botão direito no seu *projeto*, **MyBot**, no **Gerenciador de soluções** e clique em **adicionar** **|** **Classe**.</span><span class="sxs-lookup"><span data-stu-id="d5666-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![Criar o aplicativo Bot](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="d5666-172">Nomeie a classe **MyBot** e clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="d5666-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="d5666-174">Repita o ponto anterior, para criar outra classe denominada **ConversationContext**.</span><span class="sxs-lookup"><span data-stu-id="d5666-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="d5666-175">Clique duas vezes em **wwwroot** na **Gerenciador de soluções** e clique em **Add** **|** **denovoItem**.</span><span class="sxs-lookup"><span data-stu-id="d5666-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="d5666-176">Selecione **página HTML** (você irá encontrá-la sob a subseção da Web).</span><span class="sxs-lookup"><span data-stu-id="d5666-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="d5666-177">Nomeie o arquivo **default. HTML**.</span><span class="sxs-lookup"><span data-stu-id="d5666-177">Name the file **default.html**.</span></span> <span data-ttu-id="d5666-178">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="d5666-178">Click **Add**.</span></span>

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="d5666-180">A lista de classes / objetos na **Gerenciador de soluções** deve se parecer com a imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="d5666-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="d5666-182">Clique duas vezes no **ConversationContext** classe.</span><span class="sxs-lookup"><span data-stu-id="d5666-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="d5666-183">Essa classe é responsável por armazenar as variáveis usadas pelo bot para manter o contexto da conversa.</span><span class="sxs-lookup"><span data-stu-id="d5666-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="d5666-184">Esses valores de contexto de conversa são mantidos em uma instância dessa classe, porque qualquer instância das **MyBot** classe será atualizada sempre que uma atividade é recebida.</span><span class="sxs-lookup"><span data-stu-id="d5666-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="d5666-185">Adicione o seguinte código à classe:</span><span class="sxs-lookup"><span data-stu-id="d5666-185">Add the following code to the class:</span></span>

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

11. <span data-ttu-id="d5666-186">Clique duas vezes no **MyBot** classe.</span><span class="sxs-lookup"><span data-stu-id="d5666-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="d5666-187">Essa classe hospedará os manipuladores de chamada por qualquer atividade de entrada do cliente.</span><span class="sxs-lookup"><span data-stu-id="d5666-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="d5666-188">Essa classe, você adicionará o código usado para criar a conversa entre o cliente e de bot.</span><span class="sxs-lookup"><span data-stu-id="d5666-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="d5666-189">Como mencionado anteriormente, uma instância dessa classe será inicializada sempre que uma atividade é recebida.</span><span class="sxs-lookup"><span data-stu-id="d5666-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="d5666-190">Adicione o seguinte código para esta classe:</span><span class="sxs-lookup"><span data-stu-id="d5666-190">Add the following code to this class:</span></span>

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

12. <span data-ttu-id="d5666-191">Clique duas vezes no **inicialização** classe.</span><span class="sxs-lookup"><span data-stu-id="d5666-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="d5666-192">Essa classe irá inicializar o bot.</span><span class="sxs-lookup"><span data-stu-id="d5666-192">This class will initialize the bot.</span></span> <span data-ttu-id="d5666-193">Adicione o seguinte código à classe:</span><span class="sxs-lookup"><span data-stu-id="d5666-193">Add the following code to the class:</span></span>

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

13. <span data-ttu-id="d5666-194">Abra o **programa** arquivo de classe e verifique se o código é o mesmo que o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d5666-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

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

14. <span data-ttu-id="d5666-195">Lembre-se de salvar suas alterações, para fazer isso, vá para **arquivo** > **Salvar tudo**, na barra de ferramentas na parte superior do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5666-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="d5666-196">Capítulo 2 - criar o serviço de Bot do Azure</span><span class="sxs-lookup"><span data-stu-id="d5666-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="d5666-197">Agora que você criou o código para o bot, você precisa publicá-lo em uma instância das *Bot de aplicativo Web* serviço no Portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="d5666-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="d5666-198">Este capítulo mostra como criar e configurar o serviço de Bot do Azure e, em seguida, publicar seu código nele.</span><span class="sxs-lookup"><span data-stu-id="d5666-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="d5666-199">Primeiro, faça logon portal do Azure (https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="d5666-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="d5666-200">Se você ainda não tiver uma conta do Azure, você precisará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="d5666-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="d5666-201">Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="d5666-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="d5666-202">Quando você estiver conectado, clique em **criar um recurso** no canto superior esquerdo de canto e procure *bot de aplicativo Web*e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="d5666-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="d5666-204">A nova página fornecerá uma descrição do *Bot de aplicativo Web* serviço.</span><span class="sxs-lookup"><span data-stu-id="d5666-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="d5666-205">Na parte inferior esquerda desta página, selecione a **criar** botão para criar uma associação com este serviço.</span><span class="sxs-lookup"><span data-stu-id="d5666-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="d5666-207">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="d5666-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="d5666-208">Inserir sua desejada **nome** para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="d5666-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="d5666-209">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="d5666-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="d5666-210">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="d5666-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="d5666-211">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="d5666-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="d5666-212">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="d5666-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="d5666-213">Se você quiser ler mais sobre grupos de recursos do Azure, [, siga este link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="d5666-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="d5666-214">Determine o local para seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="d5666-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="d5666-215">O local seria o ideal é que na região em que o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="d5666-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="d5666-216">Alguns ativos do Azure estão disponíveis somente em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="d5666-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="d5666-217">Selecione o **tipo de preço** apropriado para você, se esse for o primeiro tempo para criar um *Bot de aplicativo Web* serviço, uma camada gratuita (chamada F0) deve estar disponível para você</span><span class="sxs-lookup"><span data-stu-id="d5666-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="d5666-218">**Nome do aplicativo** pode apenas ser deixada igual a *nome do Bot*.</span><span class="sxs-lookup"><span data-stu-id="d5666-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="d5666-219">Deixe o *modelo de Bot* como **básica (C#)**.</span><span class="sxs-lookup"><span data-stu-id="d5666-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="d5666-220">*Localização/plano de serviço de aplicativo* deveria ter sido preenchidos automaticamente para sua conta.</span><span class="sxs-lookup"><span data-stu-id="d5666-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="d5666-221">Defina as **armazenamento do Azure** que você deseja usar para hospedar seu Bot.</span><span class="sxs-lookup"><span data-stu-id="d5666-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="d5666-222">Se você ainda não tiver uma, você pode criá-lo aqui.</span><span class="sxs-lookup"><span data-stu-id="d5666-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="d5666-223">Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="d5666-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="d5666-224">Clique em criar.</span><span class="sxs-lookup"><span data-stu-id="d5666-224">Click Create.</span></span>
 
        ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="d5666-226">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="d5666-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="d5666-227">Uma notificação será exibida no Portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="d5666-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="d5666-229">Clique na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="d5666-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="d5666-231">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="d5666-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="d5666-232">Você será levado para a nova instância de serviço do Azure.</span><span class="sxs-lookup"><span data-stu-id="d5666-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="d5666-234">Neste ponto, você precisa configurar um recurso chamado **linha direta** para permitir que seu aplicativo cliente para se comunicar com o serviço de Bot.</span><span class="sxs-lookup"><span data-stu-id="d5666-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="d5666-235">Clique em **canais**, em seguida, no **adicionar um canal em destaque** seção, clique em **canal de linha direta para configurar**.</span><span class="sxs-lookup"><span data-stu-id="d5666-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="d5666-237">Nesta página você encontrará os **chaves secretas** que permitirá que seu aplicativo cliente autenticar com o bot.</span><span class="sxs-lookup"><span data-stu-id="d5666-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="d5666-238">Clique no **Mostrar** botão e faça uma cópia de uma das chaves exibidas, pois precisará dele posteriormente em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d5666-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="d5666-240">Capítulo 3 – publicar o Bot para o serviço de Bot do aplicativo Web do Azure</span><span class="sxs-lookup"><span data-stu-id="d5666-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="d5666-241">Agora que seu serviço estiver pronto, você precisa publicar seu código de Bot, o que você criou anteriormente, ao serviço de Bot de aplicativo Web recém-criado.</span><span class="sxs-lookup"><span data-stu-id="d5666-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="d5666-242">Você precisará publicar seu Bot para o serviço do Azure sempre que você fizer alterações à solução Bot / code.</span><span class="sxs-lookup"><span data-stu-id="d5666-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="d5666-243">Volte para sua solução do Visual Studio que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d5666-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="d5666-244">Clique com botão direito no seu **MyBot** projeto, o **Gerenciador de soluções**, em seguida, clique em **publicar**.</span><span class="sxs-lookup"><span data-stu-id="d5666-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![Publicar o Bot para o serviço de Bot do aplicativo Web do Azure](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="d5666-246">Sobre o *escolher um destino de publicação* , clique em **serviço de aplicativo**, em seguida, **selecionar existente**, por fim, clique em **criar perfil** (talvez você precise Clique na seta suspensa ao lado de *publicar* botão, se não estiver visível).</span><span class="sxs-lookup"><span data-stu-id="d5666-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![Publicar o Bot para o serviço de Bot do aplicativo Web do Azure](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="d5666-248">Se você ainda não está conectados em seu Account da Microsoft, você precisa fazê-lo aqui.</span><span class="sxs-lookup"><span data-stu-id="d5666-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="d5666-249">Sobre o **publicar** página você encontrará, você deve definir o mesmo **assinatura** que você usou para o *Bot de aplicativo Web* criação de serviço.</span><span class="sxs-lookup"><span data-stu-id="d5666-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="d5666-250">Em seguida, defina a **modo de exibição** como **grupo de recursos** e, no menu suspenso de estrutura de pasta, selecione o **grupo de recursos** criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d5666-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="d5666-251">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="d5666-251">Click **OK**.</span></span> 

    ![Publicar o Bot para o serviço de Bot do aplicativo Web do Azure](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="d5666-253">Agora, clique na **publicar** botão e, em seguida, aguarde até que o Bot para serem publicados (pode levar alguns minutos).</span><span class="sxs-lookup"><span data-stu-id="d5666-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![Publicar o Bot para o serviço de Bot do aplicativo Web do Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="d5666-255">Capítulo 4-configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="d5666-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="d5666-256">A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="d5666-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="d5666-257">Abra *Unity* e clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="d5666-257">Open *Unity* and click **New**.</span></span> 

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="d5666-259">Agora, você precisará fornecer um nome de projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="d5666-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="d5666-260">Inserir **Hololens Bot**.</span><span class="sxs-lookup"><span data-stu-id="d5666-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="d5666-261">Verifique se o modelo de projeto é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="d5666-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="d5666-262">Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="d5666-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="d5666-263">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="d5666-263">Then, click **Create project**.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="d5666-265">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d5666-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="d5666-266">Vá para **Editar > Preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="d5666-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="d5666-267">Alteração **Editor de Script externo** à **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="d5666-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="d5666-268">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="d5666-268">Close the **Preferences** window.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="d5666-270">Em seguida, vá para **arquivo > configurações de Build** e selecione **plataforma Universal do Windows**, em seguida, clique no **alternar plataforma** botão Aplicar sua seleção.</span><span class="sxs-lookup"><span data-stu-id="d5666-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="d5666-272">Enquanto estiver na **arquivo > configurações de Build** e certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="d5666-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="d5666-273">**Dispositivo de destino** é definido como **Hololens**</span><span class="sxs-lookup"><span data-stu-id="d5666-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="d5666-274">Para os fones imersivos em exposição, defina **dispositivo de destino** à *qualquer dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="d5666-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="d5666-275">**Tipo de compilação** é definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="d5666-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="d5666-276">**SDK** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="d5666-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="d5666-277">**Versão do Visual Studio** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="d5666-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="d5666-278">**Compilar e executar** é definido como **Máquina Local**</span><span class="sxs-lookup"><span data-stu-id="d5666-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="d5666-279">Salve a cena e adicioná-lo para a compilação.</span><span class="sxs-lookup"><span data-stu-id="d5666-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="d5666-280">Fazer isso selecionando **cenas abra Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="d5666-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="d5666-281">Salvamento janela será exibida.</span><span class="sxs-lookup"><span data-stu-id="d5666-281">A save window will appear.</span></span>
        
            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="d5666-283">Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.</span><span class="sxs-lookup"><span data-stu-id="d5666-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Configurar o projeto do Unity](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="d5666-285">Abrir seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo*: campo de texto, digite **BotScene**, em seguida, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="d5666-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="d5666-287">O restante de configurações, em **configurações de Build**, deverá ser deixado como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="d5666-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="d5666-288">No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="d5666-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="d5666-290">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="d5666-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="d5666-291">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="d5666-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="d5666-292">**Versão de tempo de execução de scripts** deve ser **Experimental (NET 4.6 equivalente)**; essa alteração exigirá uma reinicialização do Editor.</span><span class="sxs-lookup"><span data-stu-id="d5666-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="d5666-293">**Script de back-end** deve ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="d5666-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="d5666-294">**Nível de compatibilidade de API** deve ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="d5666-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="d5666-296">Dentro de **configurações de publicação** guia, em **recursos**, verifique:</span><span class="sxs-lookup"><span data-stu-id="d5666-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="d5666-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="d5666-297">**InternetClient**</span></span>
        - <span data-ttu-id="d5666-298">**Microfone**</span><span class="sxs-lookup"><span data-stu-id="d5666-298">**Microphone**</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="d5666-300">Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.</span><span class="sxs-lookup"><span data-stu-id="d5666-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurar o projeto do Unity](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="d5666-302">Volta *configurações de Build* _Unity C#_  projetos não fica acinzentado; marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="d5666-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="d5666-303">Feche a janela de configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="d5666-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="d5666-304">Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="d5666-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="d5666-305">Capítulo 5 – instalação da câmera</span><span class="sxs-lookup"><span data-stu-id="d5666-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d5666-306">Se você quiser ignorar a *configurar o Unity* componente deste curso e continuar diretamente no código, fique à vontade para baixá-lo [Azure MR-312 Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 7](#chapter-7-–-create-the-botobjects-class).</span><span class="sxs-lookup"><span data-stu-id="d5666-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-7-–-create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="d5666-307">No *painel de hierarquia*, selecione o **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="d5666-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="d5666-308">Depois de selecionado, você poderá ver todos os componentes do **câmera principal** na *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="d5666-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="d5666-309">O **objeto de câmera** deve ser nomeado **câmera principal** (Observe a ortografia)</span><span class="sxs-lookup"><span data-stu-id="d5666-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="d5666-310">A câmera principal **marca** deve ser definida como **MainCamera** (Observe a ortografia)</span><span class="sxs-lookup"><span data-stu-id="d5666-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="d5666-311">Verifique se o **transformar posição** é definido como **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="d5666-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="d5666-312">Definir **limpar os sinalizadores** à **cor sólida**.</span><span class="sxs-lookup"><span data-stu-id="d5666-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="d5666-313">Definir a **plano de fundo** cor do componente de câmera para **preto, alfa 0 (código hexadecimal: 00000000 #)**</span><span class="sxs-lookup"><span data-stu-id="d5666-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![a instalação da câmera](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="d5666-315">Capítulo 6 – importar a biblioteca Newtonsoft</span><span class="sxs-lookup"><span data-stu-id="d5666-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="d5666-316">Para ajudá-lo a desserializam e serializam os objetos recebidos e enviados para o serviço de Bot, você precisa baixar o **Newtonsoft** biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d5666-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="d5666-317">Você encontrará uma [versão compatível já organizado com a estrutura pasta Unity correta aqui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="d5666-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="d5666-318">Para importar a biblioteca Newtonsoft para seu projeto, use o pacote do Unity que acompanha este curso.</span><span class="sxs-lookup"><span data-stu-id="d5666-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="d5666-319">Adicionar o *unitypackage* para o Unity, usando o **ativos** > **Importar pacote** > **pacote personalizado** opção de menu.</span><span class="sxs-lookup"><span data-stu-id="d5666-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Importar a biblioteca Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="d5666-321">No **Importar pacote do Unity** caixa é exibido para cima, certifique-se de tudo em (e incluindo) **plug-ins** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="d5666-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importar a biblioteca Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="d5666-323">Clique o **importação** botão para adicionar itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d5666-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="d5666-324">Vá para o **Newtonsoft** pasta sob **plug-ins** no modo de exibição do projeto e selecione o plug-in do Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="d5666-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="d5666-325">Com o plug-in Newtonsoft selecionado, certifique-se de que **Any Platform** é **desmarcada**, em seguida, certifique-se de que **WSAPlayer** também é **desmarcada**, em seguida, clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="d5666-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="d5666-326">Isso é apenas para confirmar que os arquivos estão configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="d5666-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="d5666-327">Marcar esses plug-ins configura para ser usado apenas no Editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="d5666-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="d5666-328">Há um conjunto diferente de-los na pasta do WSA que será usado depois que o projeto é exportado do Unity.</span><span class="sxs-lookup"><span data-stu-id="d5666-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="d5666-329">Em seguida, você precisa abrir o **WSA** pasta, dentro de **Newtonsoft** pasta.</span><span class="sxs-lookup"><span data-stu-id="d5666-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="d5666-330">Você verá uma cópia do mesmo arquivo que você acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="d5666-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="d5666-331">Selecione o arquivo e, em seguida, no Inspetor de, certifique-se de que</span><span class="sxs-lookup"><span data-stu-id="d5666-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="d5666-332">**Qualquer plataforma** é **desmarcada**</span><span class="sxs-lookup"><span data-stu-id="d5666-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="d5666-333">**somente** **WSAPlayer** é **marcada**</span><span class="sxs-lookup"><span data-stu-id="d5666-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="d5666-334">**Não processar** é **marcada**</span><span class="sxs-lookup"><span data-stu-id="d5666-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="d5666-335">Capítulo 7 – criar o BotTag</span><span class="sxs-lookup"><span data-stu-id="d5666-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="d5666-336">Criar um novo **marca** objeto chamado **BotTag**.</span><span class="sxs-lookup"><span data-stu-id="d5666-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="d5666-337">Selecione a câmera principal na cena.</span><span class="sxs-lookup"><span data-stu-id="d5666-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="d5666-338">Clique no menu no painel Inspetor suspenso marca.</span><span class="sxs-lookup"><span data-stu-id="d5666-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="d5666-339">Clique em **Adicionar marca**.</span><span class="sxs-lookup"><span data-stu-id="d5666-339">Click on **Add Tag**.</span></span>

    ![a instalação da câmera](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="d5666-341">Clique no **+** símbolo.</span><span class="sxs-lookup"><span data-stu-id="d5666-341">Click on the **+** symbol.</span></span> <span data-ttu-id="d5666-342">Nomeie o novo **marca** como **BotTag**, *salvar*.</span><span class="sxs-lookup"><span data-stu-id="d5666-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![a instalação da câmera](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="d5666-344">**Não o fazem** se aplicam a **BotTag** para a câmera principal.</span><span class="sxs-lookup"><span data-stu-id="d5666-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="d5666-345">Se você acidentalmente tiver feito isso, certifique-se de alterar a câmera principal marca de volta para *MainCamera*.</span><span class="sxs-lookup"><span data-stu-id="d5666-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="d5666-346">Capítulo 8 – criar a classe BotObjects</span><span class="sxs-lookup"><span data-stu-id="d5666-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="d5666-347">É o primeiro script que você precisa criar o **BotObjects** classe, que é uma classe vazia criada para que uma série de outros objetos de classe pode ser armazenada dentro do mesmo script e acessados por outros scripts na cena.</span><span class="sxs-lookup"><span data-stu-id="d5666-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="d5666-348">A criação dessa classe é puramente uma opção de arquitetura, esses objetos podem ser hospedados em vez disso, no script Bot que você criará posteriormente no curso.</span><span class="sxs-lookup"><span data-stu-id="d5666-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="d5666-349">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="d5666-349">To create this class:</span></span> 

1.  <span data-ttu-id="d5666-350">Clique com botão direito no *painel projeto*, em seguida, **criar > pasta**.</span><span class="sxs-lookup"><span data-stu-id="d5666-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="d5666-351">Nomeie a pasta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="d5666-351">Name the folder **Scripts**.</span></span> 

    ![Crie a pasta de scripts.](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="d5666-353">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="d5666-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="d5666-354">Em seguida, dentro dessa pasta, clique com botão direito e selecione **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="d5666-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="d5666-355">Nomeie o script **BotObjects**.</span><span class="sxs-lookup"><span data-stu-id="d5666-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="d5666-356">Clique duas vezes na nova **BotObjects** script para abri-lo com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d5666-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="d5666-357">Exclua o conteúdo do script e substitua-o pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="d5666-357">Delete the content of the script and replace it with the following code:</span></span>

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

6.  <span data-ttu-id="d5666-358">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="d5666-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="d5666-359">Capítulo 9 – criar a classe GazeInput</span><span class="sxs-lookup"><span data-stu-id="d5666-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="d5666-360">A próxima classe que você pretende criar é a **GazeInput** classe.</span><span class="sxs-lookup"><span data-stu-id="d5666-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="d5666-361">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="d5666-361">This class is responsible for:</span></span>

- <span data-ttu-id="d5666-362">Criar um cursor que representará o *olhares* do player.</span><span class="sxs-lookup"><span data-stu-id="d5666-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="d5666-363">Detecção de objetos atingidos pelo olhar do player e mantendo uma referência a objetos detectados.</span><span class="sxs-lookup"><span data-stu-id="d5666-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="d5666-364">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="d5666-364">To create this class:</span></span> 

1.  <span data-ttu-id="d5666-365">Vá para o **Scripts** pasta que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d5666-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="d5666-366">Clique com botão direito dentro da pasta **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="d5666-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="d5666-367">Chame o script **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="d5666-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="d5666-368">Clique duas vezes na nova **GazeInput** script para abri-lo com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d5666-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="d5666-369">Insira a seguinte linha à direita no topo do nome da classe:</span><span class="sxs-lookup"><span data-stu-id="d5666-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="d5666-370">Em seguida, adicione as seguintes variáveis dentro de **GazeInput** classe acima a **Start ()** método:</span><span class="sxs-lookup"><span data-stu-id="d5666-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="d5666-371">Código para o **Start ()** método deve ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="d5666-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="d5666-372">Isso será chamado quando a classe é inicializado:</span><span class="sxs-lookup"><span data-stu-id="d5666-372">This will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="d5666-373">Implemente um método que será criar uma instância e o cursor de olhar de instalação:</span><span class="sxs-lookup"><span data-stu-id="d5666-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

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

8.  <span data-ttu-id="d5666-374">Implemente os métodos que irá configurar o Raycast da câmera principal e serão manter o controle do objeto atual com foco.</span><span class="sxs-lookup"><span data-stu-id="d5666-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

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
 
9.  <span data-ttu-id="d5666-375">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="d5666-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="d5666-376">Capítulo 10 – criar a classe de Bot</span><span class="sxs-lookup"><span data-stu-id="d5666-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="d5666-377">O script que você pretende criar agora é chamado **Bot**.</span><span class="sxs-lookup"><span data-stu-id="d5666-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="d5666-378">Esta é a classe principal do seu aplicativo, ele armazena:</span><span class="sxs-lookup"><span data-stu-id="d5666-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="d5666-379">Suas credenciais de Bot do aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="d5666-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="d5666-380">O método que coleta os comandos de voz do usuário</span><span class="sxs-lookup"><span data-stu-id="d5666-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="d5666-381">O método necessário para iniciar conversas com seu Bot de aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="d5666-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="d5666-382">O método necessário para enviar mensagens ao seu Bot de aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="d5666-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="d5666-383">Para enviar mensagens para o serviço de Bot, o **SendMessageToBot()** corrotina criará uma atividade, que é um objeto reconhecido pela estrutura do Bot como os dados enviados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="d5666-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="d5666-384">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="d5666-384">To create this class:</span></span> 

1. <span data-ttu-id="d5666-385">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="d5666-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="d5666-386">Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="d5666-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="d5666-387">Nomeie o script **Bot**.</span><span class="sxs-lookup"><span data-stu-id="d5666-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="d5666-388">Clique duas vezes no novo script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5666-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="d5666-389">Atualizar os namespaces para ser o mesmo que o seguinte, na parte superior do **Bot** classe:</span><span class="sxs-lookup"><span data-stu-id="d5666-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="d5666-390">Dentro de **Bot** classe adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="d5666-390">Inside the **Bot** class add the following variables:</span></span>

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
    > <span data-ttu-id="d5666-391">Certifique-se de inserir sua **chave de segredo do Bot** para o **botSecret** variável.</span><span class="sxs-lookup"><span data-stu-id="d5666-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="d5666-392">Você irá ter anotado sua **chave de segredo do Bot** no início deste curso, em  **[capítulo 2](#chapter-2---create-the-azure-bot-service), etapa 10**.</span><span class="sxs-lookup"><span data-stu-id="d5666-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="d5666-393">Código para o **Awake()** e **Start ()** agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="d5666-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

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

8. <span data-ttu-id="d5666-394">Adicione os dois manipuladores são chamados pelas bibliotecas de fala quando a captura de voz começa e termina.</span><span class="sxs-lookup"><span data-stu-id="d5666-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="d5666-395">O *DictationRecognizer* automaticamente irá parar de capturar a voz do usuário quando o usuário para falar.</span><span class="sxs-lookup"><span data-stu-id="d5666-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

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

1. <span data-ttu-id="d5666-396">O manipulador a seguir coleta o resultado da entrada de voz do usuário e chama a corrotina responsável por enviar a mensagem para o serviço de Bot de aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="d5666-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

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

10. <span data-ttu-id="d5666-397">A seguir co-rotina é chamada para iniciar uma conversa com o Bot.</span><span class="sxs-lookup"><span data-stu-id="d5666-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="d5666-398">Você observará que quando a chamada de conversa for concluída, ele chamará o **SendMessageToCoroutine()** , passando uma série de parâmetros que definirá a atividade a ser enviada para o serviço de Bot como uma mensagem vazia.</span><span class="sxs-lookup"><span data-stu-id="d5666-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="d5666-399">Isso é feito para solicitar que o serviço de Bot para iniciar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="d5666-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

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

11. <span data-ttu-id="d5666-400">A seguir co-rotina é chamada para criar a atividade a ser enviada para o serviço de Bot.</span><span class="sxs-lookup"><span data-stu-id="d5666-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

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

12. <span data-ttu-id="d5666-401">A seguir co-rotina é chamada para solicitar uma resposta após o envio de uma atividade para o serviço de Bot.</span><span class="sxs-lookup"><span data-stu-id="d5666-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

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

13. <span data-ttu-id="d5666-402">O último método a ser adicionado a essa classe, é necessário para exibir a mensagem na cena:</span><span class="sxs-lookup"><span data-stu-id="d5666-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

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
    > <span data-ttu-id="d5666-403">Você verá um erro dentro do Console do Editor do Unity, sobre ausentes a **SceneOrganiser** classe.</span><span class="sxs-lookup"><span data-stu-id="d5666-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="d5666-404">Ignore essa mensagem, como você criará essa classe posteriormente no tutorial.</span><span class="sxs-lookup"><span data-stu-id="d5666-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="d5666-405">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="d5666-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="d5666-406">Capítulo 11 – criar a classe de interações</span><span class="sxs-lookup"><span data-stu-id="d5666-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="d5666-407">A classe que você pretende criar agora é chamada **interações**.</span><span class="sxs-lookup"><span data-stu-id="d5666-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="d5666-408">Essa classe é usada para detectar a entrada de toque do HoloLens do usuário.</span><span class="sxs-lookup"><span data-stu-id="d5666-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="d5666-409">Se o usuário toca ao examinar a *Bot* objeto na cena e o Bot está pronto para ouvir de entradas de voz, o objeto de Bot mudará de cor para **vermelho** e começar a escutar as entradas de voz.</span><span class="sxs-lookup"><span data-stu-id="d5666-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="d5666-410">Essa classe herda a **GazeInput** de classe e, portanto, é possível fazer referência a **Start ()** método e variáveis de classe, indicado pelo uso de **base**.</span><span class="sxs-lookup"><span data-stu-id="d5666-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="d5666-411">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="d5666-411">To create this class:</span></span>

1.  <span data-ttu-id="d5666-412">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="d5666-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="d5666-413">Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="d5666-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="d5666-414">Nomeie o script **interações**.</span><span class="sxs-lookup"><span data-stu-id="d5666-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="d5666-415">Clique duas vezes no novo script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5666-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="d5666-416">Os namespaces e a herança de classe para ser o mesmo que o seguinte, na parte superior da atualização do **interações** classe:</span><span class="sxs-lookup"><span data-stu-id="d5666-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="d5666-417">Dentro de **interações** classe adicione a seguinte variável:</span><span class="sxs-lookup"><span data-stu-id="d5666-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="d5666-418">Em seguida, adicione a **Start ()** método:</span><span class="sxs-lookup"><span data-stu-id="d5666-418">Then add the **Start()** method:</span></span>

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

7.  <span data-ttu-id="d5666-419">Adicione o manipulador que será acionado quando o usuário executa o gesto de tocar na frente da câmera HoloLens</span><span class="sxs-lookup"><span data-stu-id="d5666-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

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

8. <span data-ttu-id="d5666-420">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="d5666-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="d5666-421">Capítulo 12 – criar a classe SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="d5666-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="d5666-422">A última classe necessária neste laboratório é chamada **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="d5666-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="d5666-423">Essa classe irá configurar a cena programaticamente, adicionando scripts e componentes para a câmera principal, e criando os objetos apropriados na cena.</span><span class="sxs-lookup"><span data-stu-id="d5666-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="d5666-424">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="d5666-424">To create this class:</span></span>

1.  <span data-ttu-id="d5666-425">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="d5666-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="d5666-426">Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="d5666-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="d5666-427">Nomeie o script **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="d5666-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="d5666-428">Clique duas vezes no novo script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5666-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="d5666-429">Dentro de **SceneOrganiser** classe adicione as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="d5666-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

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

6.  <span data-ttu-id="d5666-430">Em seguida, adicione a **Awake()** e **Start ()** métodos:</span><span class="sxs-lookup"><span data-stu-id="d5666-430">Then add the **Awake()** and **Start()** methods:</span></span>

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

7.  <span data-ttu-id="d5666-431">Adicione o seguinte método, responsável por criar o objeto de Bot na cena e como configurar os parâmetros e os componentes:</span><span class="sxs-lookup"><span data-stu-id="d5666-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

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

7.  <span data-ttu-id="d5666-432">Adicione o seguinte método, responsável por criar o objeto de interface do usuário na cena, que representa as respostas do Bot:</span><span class="sxs-lookup"><span data-stu-id="d5666-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

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

8.  <span data-ttu-id="d5666-433">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="d5666-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="d5666-434">No Editor do Unity, arraste a **SceneOrganiser** script da pasta de Scripts para a câmera principal.</span><span class="sxs-lookup"><span data-stu-id="d5666-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="d5666-435">O componente de cena Gallery agora deve aparecer no objeto de câmera principal, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="d5666-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="d5666-437">Capítulo 13 – antes da construção</span><span class="sxs-lookup"><span data-stu-id="d5666-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="d5666-438">Para executar um teste completo de seu aplicativo você precisará para fazer sideload dele para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d5666-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="d5666-439">Antes de começar, verifique se:</span><span class="sxs-lookup"><span data-stu-id="d5666-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="d5666-440">Todas as configurações mencionadas a [ **capítulo 4** ](#Chapter-4-–-Set-up-the-unity-project) estão definidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="d5666-440">All the settings mentioned in the [**Chapter 4**](#Chapter-4-–-Set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="d5666-441">O script **SceneOrganiser** está associada a **câmera principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="d5666-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="d5666-442">No **Bot** classe, certifique-se de inserir sua **chave de segredo do Bot** no **botSecret** variável.</span><span class="sxs-lookup"><span data-stu-id="d5666-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="d5666-443">Capítulo 14 – Build e carregar para o HoloLens</span><span class="sxs-lookup"><span data-stu-id="d5666-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="d5666-444">Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído, portanto, é hora de criá-lo do Unity.</span><span class="sxs-lookup"><span data-stu-id="d5666-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="d5666-445">Navegue até **configurações de Build**, **arquivo > configurações de Build...** .</span><span class="sxs-lookup"><span data-stu-id="d5666-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="d5666-446">Dos **configurações de Build** janela, clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="d5666-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilando o aplicativo do Unity](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="d5666-448">Se ainda não estiver, marque **Unity C# projetos**.</span><span class="sxs-lookup"><span data-stu-id="d5666-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="d5666-449">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="d5666-449">Click **Build**.</span></span> <span data-ttu-id="d5666-450">Unity iniciará uma **Explorador de arquivos** janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em.</span><span class="sxs-lookup"><span data-stu-id="d5666-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="d5666-451">Criar pasta agora e nomeie- **aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="d5666-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="d5666-452">Em seguida, com o **App** pasta selecionada, clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="d5666-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="d5666-453">Unity começará a compilar seu projeto para o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="d5666-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="d5666-454">Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um **Explorador de arquivos** janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).</span><span class="sxs-lookup"><span data-stu-id="d5666-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="d5666-455">Capítulo 15 – implantar ao HoloLens</span><span class="sxs-lookup"><span data-stu-id="d5666-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="d5666-456">Para implantar o HoloLens:</span><span class="sxs-lookup"><span data-stu-id="d5666-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="d5666-457">Será necessário o endereço IP do seu HoloLens (para a implantação remota) e garantir que seu HoloLens está em **modo de desenvolvedor**.</span><span class="sxs-lookup"><span data-stu-id="d5666-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="d5666-458">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="d5666-458">To do this:</span></span>

    1. <span data-ttu-id="d5666-459">Durante o uso de seu HoloLens, abra o **configurações**.</span><span class="sxs-lookup"><span data-stu-id="d5666-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="d5666-460">Vá para **rede e Internet > Wi-Fi > Opções avançadas**</span><span class="sxs-lookup"><span data-stu-id="d5666-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="d5666-461">Observe a **IPv4** endereço.</span><span class="sxs-lookup"><span data-stu-id="d5666-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="d5666-462">Em seguida, navegue até **as configurações**e, em seguida, para **atualização e segurança > para desenvolvedores**</span><span class="sxs-lookup"><span data-stu-id="d5666-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="d5666-463">Definir o modo de desenvolvedor em.</span><span class="sxs-lookup"><span data-stu-id="d5666-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="d5666-464">Navegue até seu novo build do Unity (o **App** pasta) e abra o arquivo de solução com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d5666-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="d5666-465">No **configuração da solução** selecionar **depurar**.</span><span class="sxs-lookup"><span data-stu-id="d5666-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="d5666-466">No **plataforma da solução**, selecione **x86**, **máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="d5666-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="d5666-468">Vá para o **menu Build** e clique em **implantar solução**, carregar o aplicativo para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d5666-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="d5666-469">Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="d5666-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="d5666-470">Para implantar o fone de ouvido imersivo, defina as **plataforma da solução** para *Máquina Local*e defina o **configuração** para *depurar*, com *x86* como o **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="d5666-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="d5666-471">Em seguida, implantar no local de máquina, usando o **menu Build**, selecionando *implantar solução*.</span><span class="sxs-lookup"><span data-stu-id="d5666-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="d5666-472">Capítulo 16 – usando o aplicativo no HoloLens</span><span class="sxs-lookup"><span data-stu-id="d5666-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="d5666-473">Quando você tiver iniciado o aplicativo, você verá o Bot como um círculo azul na sua frente.</span><span class="sxs-lookup"><span data-stu-id="d5666-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="d5666-474">Use o **gestos de toque** enquanto você estiver Observação na esfera para iniciar uma conversa.</span><span class="sxs-lookup"><span data-stu-id="d5666-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="d5666-475">Aguarde até que a conversa iniciar (a interface do usuário exibirá uma mensagem quando isso acontece).</span><span class="sxs-lookup"><span data-stu-id="d5666-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="d5666-476">Depois de receber a mensagem introdutória do Bot, toque em novamente no Bot para que ele fique vermelho e começar a ouvir sua voz.</span><span class="sxs-lookup"><span data-stu-id="d5666-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="d5666-477">Depois que você parar de falar, seu aplicativo enviará a mensagem para o Bot e você receberá imediatamente uma resposta que será exibida na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="d5666-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="d5666-478">Repita o processo para enviar mais mensagens para seu Bot (você precisa tocar em cada vez que você deseja enviar uma mensagem).</span><span class="sxs-lookup"><span data-stu-id="d5666-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="d5666-479">Esta conversa demonstra como o Bot pode reter informações (seu nome), enquanto também fornecendo informações conhecidas (como os itens que estão em estoque).</span><span class="sxs-lookup"><span data-stu-id="d5666-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="d5666-480">Algumas perguntas a fazer o Bot:</span><span class="sxs-lookup"><span data-stu-id="d5666-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="d5666-481">O aplicativo Bot de aplicativo Web (v4) concluído</span><span class="sxs-lookup"><span data-stu-id="d5666-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="d5666-482">Parabéns, você criou um aplicativo de realidade mista que aproveita o Bot de aplicativo Web do Azure, o Microsoft Bot Framework v4.</span><span class="sxs-lookup"><span data-stu-id="d5666-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![Final do produto](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="d5666-484">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="d5666-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="d5666-485">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="d5666-485">Exercise 1</span></span>

<span data-ttu-id="d5666-486">A estrutura de conversa neste laboratório é muito básica.</span><span class="sxs-lookup"><span data-stu-id="d5666-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="d5666-487">Use Microsoft LUIS para oferecer recursos de compreensão de idioma natural de seu bot.</span><span class="sxs-lookup"><span data-stu-id="d5666-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="d5666-488">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="d5666-488">Exercise 2</span></span>

<span data-ttu-id="d5666-489">Este exemplo não inclui terminando uma conversa e reiniciando uma nova.</span><span class="sxs-lookup"><span data-stu-id="d5666-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="d5666-490">Para tornar o recurso de Bot concluir, tente implementar fechamento a conversa.</span><span class="sxs-lookup"><span data-stu-id="d5666-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
