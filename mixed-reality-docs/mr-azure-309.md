---
title: Sr e Azure 309-Application insights
description: Conclua este curso para aprender a coletar análises sobre o comportamento do usuário em um aplicativo de realidade misturada, usando o serviço do insights Aplicativo Azure.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, Application insights, hololens, imersão, VR
ms.openlocfilehash: 481fe3fc16ada06085a64c86867a1a892c76f2ad
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926896"
---
>[!NOTE]
><span data-ttu-id="ca735-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="ca735-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ca735-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="ca735-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ca735-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ca735-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ca735-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="ca735-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ca735-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ca735-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ca735-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="ca735-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="ca735-110">Sr e Azure 309: Application insights</span><span class="sxs-lookup"><span data-stu-id="ca735-110">MR and Azure 309: Application insights</span></span>

![início do produto final](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="ca735-112">Neste curso, você aprenderá a adicionar recursos de Application Insights a um aplicativo de realidade misturada, usando a API do Aplicativo Azure insights para coletar análises sobre o comportamento do usuário.</span><span class="sxs-lookup"><span data-stu-id="ca735-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="ca735-113">Application Insights é um serviço da Microsoft, permitindo aos desenvolvedores coletar análises de seus aplicativos e gerenciá-los de um portal fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="ca735-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="ca735-114">A análise pode ser qualquer coisa, desde o desempenho até as informações personalizadas que você gostaria de coletar.</span><span class="sxs-lookup"><span data-stu-id="ca735-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="ca735-115">Para obter mais informações, visite a [página Application insights](https://azure.microsoft.com/services/application-insights/).</span><span class="sxs-lookup"><span data-stu-id="ca735-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="ca735-116">Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada que poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ca735-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="ca735-117">Permitir que o usuário olhar e mova-se em uma cena.</span><span class="sxs-lookup"><span data-stu-id="ca735-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="ca735-118">Dispare o envio de análises para o *serviço de Application insights*, por meio do uso de olhar e proximidade para objetos em cena.</span><span class="sxs-lookup"><span data-stu-id="ca735-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="ca735-119">O aplicativo também chamará o serviço, buscando informações sobre qual objeto foi mais abordado pelo usuário, nas últimas 24 horas.</span><span class="sxs-lookup"><span data-stu-id="ca735-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="ca735-120">Esse objeto alterará sua cor para verde.</span><span class="sxs-lookup"><span data-stu-id="ca735-120">That object will change its color to green.</span></span>

<span data-ttu-id="ca735-121">Este curso ensinará a você como obter os resultados do serviço de Application Insights em um aplicativo de exemplo baseado em Unity.</span><span class="sxs-lookup"><span data-stu-id="ca735-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="ca735-122">Será necessário aplicar esses conceitos a um aplicativo personalizado que você possa estar criando.</span><span class="sxs-lookup"><span data-stu-id="ca735-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="ca735-123">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="ca735-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ca735-124">Course</span><span class="sxs-lookup"><span data-stu-id="ca735-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ca735-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ca735-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ca735-126"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="ca735-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ca735-127">Sr e Azure 309: Application insights</span><span class="sxs-lookup"><span data-stu-id="ca735-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="ca735-128">✔️</span><span class="sxs-lookup"><span data-stu-id="ca735-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ca735-129">✔️</span><span class="sxs-lookup"><span data-stu-id="ca735-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ca735-130">Embora este curso se concentre principalmente em fones de ouvido (VR) de realidade mista do Windows, você também pode aplicar o que aprende neste curso ao Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ca735-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="ca735-131">Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ca735-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="ca735-132">Ao usar o HoloLens, você pode notar um eco durante a captura de voz.</span><span class="sxs-lookup"><span data-stu-id="ca735-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ca735-133">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ca735-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ca735-134">Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o.</span><span class="sxs-lookup"><span data-stu-id="ca735-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ca735-135">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (julho de 2018).</span><span class="sxs-lookup"><span data-stu-id="ca735-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="ca735-136">Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso correspondam perfeitamente ao que você encontrará no software mais recente do que o que está listado abaixo.</span><span class="sxs-lookup"><span data-stu-id="ca735-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="ca735-137">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="ca735-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ca735-138">Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)</span><span class="sxs-lookup"><span data-stu-id="ca735-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ca735-139">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="ca735-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ca735-140">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="ca735-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ca735-141">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="ca735-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ca735-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ca735-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="ca735-143">Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="ca735-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="ca735-144">Um conjunto de fones de ouvido com um microfone interno (se o headset não tiver um MIC interno e alto-falantes)</span><span class="sxs-lookup"><span data-stu-id="ca735-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="ca735-145">Acesso à Internet para a instalação do Azure e recuperação de dados de Application Insights</span><span class="sxs-lookup"><span data-stu-id="ca735-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ca735-146">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="ca735-146">Before you start</span></span>

<span data-ttu-id="ca735-147">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="ca735-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="ca735-148">Lembre-se de que os dados enviados para *Application insights* leva tempo, portanto, seja paciente.</span><span class="sxs-lookup"><span data-stu-id="ca735-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="ca735-149">Se você quiser verificar se o serviço recebeu seus dados, confira o [capítulo 14](#chapter-14---the-application-insights-service-portal), que lhe mostrará como navegar no Portal.</span><span class="sxs-lookup"><span data-stu-id="ca735-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="ca735-150">Capítulo 1-o portal do Azure</span><span class="sxs-lookup"><span data-stu-id="ca735-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="ca735-151">Para usar *Application insights*, será necessário criar e configurar um serviço de *Application insights* no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="ca735-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="ca735-152">Faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="ca735-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ca735-153">Se você ainda não tiver uma conta do Azure, será necessário criar uma.</span><span class="sxs-lookup"><span data-stu-id="ca735-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ca735-154">Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="ca735-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ca735-155">Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure *Application insights*e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="ca735-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ca735-156">A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="ca735-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="ca735-158">A nova página à direita fornecerá uma descrição do serviço de *informações de aplicativo Azure* .</span><span class="sxs-lookup"><span data-stu-id="ca735-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="ca735-159">Na parte inferior esquerda desta página, selecione o botão **criar** para criar uma associação com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="ca735-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="ca735-161">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="ca735-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="ca735-162">Insira o **nome** desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="ca735-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="ca735-163">Como **tipo de aplicativo**, selecione **geral**.</span><span class="sxs-lookup"><span data-stu-id="ca735-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="ca735-164">Selecione uma **assinatura**apropriada.</span><span class="sxs-lookup"><span data-stu-id="ca735-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="ca735-165">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="ca735-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ca735-166">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="ca735-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ca735-167">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="ca735-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="ca735-168">Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="ca735-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="ca735-169">Selecione um **local**.</span><span class="sxs-lookup"><span data-stu-id="ca735-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="ca735-170">Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="ca735-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="ca735-171">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="ca735-171">Select **Create**.</span></span>

        ![Portal do Azure](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="ca735-173">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="ca735-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="ca735-174">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="ca735-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="ca735-176">Clique nas notificações para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="ca735-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="ca735-178">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="ca735-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="ca735-179">Você será levado para sua nova instância do *serviço Application insights* .</span><span class="sxs-lookup"><span data-stu-id="ca735-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="ca735-181">Mantenha essa página da Web aberta e fácil de acessar, você voltará aqui para ver os dados coletados.</span><span class="sxs-lookup"><span data-stu-id="ca735-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ca735-182">Para implementar Application Insights, será necessário usar três (3) valores específicos: chave de **Instrumentação**, **ID do aplicativo**e **chave de API**.</span><span class="sxs-lookup"><span data-stu-id="ca735-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="ca735-183">Abaixo, você verá como recuperar esses valores do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="ca735-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="ca735-184">Lembre-se de anotar esses valores em uma página de *bloco de notas* em branco, pois você os usará em breve em seu código.</span><span class="sxs-lookup"><span data-stu-id="ca735-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="ca735-185">Para localizar a **chave de instrumentação**, você precisará rolar a lista de funções de serviço e clicar em **Propriedades**, a guia exibida revelará a **chave de serviço**.</span><span class="sxs-lookup"><span data-stu-id="ca735-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="ca735-187">Um pouco abaixo **das propriedades**, você encontrará o **acesso à API**, no qual você precisa clicar.</span><span class="sxs-lookup"><span data-stu-id="ca735-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="ca735-188">O painel à direita fornecerá a **ID do aplicativo** do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca735-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="ca735-190">Com o painel **ID do aplicativo** ainda aberto, clique em **criar chave de API**, que abrirá o painel *criar chave de API* .</span><span class="sxs-lookup"><span data-stu-id="ca735-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="ca735-192">No painel abrir a *chave de API criar* agora, digite uma descrição e **marque as três caixas**.</span><span class="sxs-lookup"><span data-stu-id="ca735-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="ca735-193">Clique em **gerar chave**.</span><span class="sxs-lookup"><span data-stu-id="ca735-193">Click **Generate Key**.</span></span> <span data-ttu-id="ca735-194">Sua **chave de API** será criada e exibida.</span><span class="sxs-lookup"><span data-stu-id="ca735-194">Your **API Key** will be created and displayed.</span></span> 

    ![Portal do Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="ca735-196">Essa é a única vez que a sua **chave de serviço** será exibida, portanto, certifique-se de fazer uma cópia dela agora.</span><span class="sxs-lookup"><span data-stu-id="ca735-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="ca735-197">Capítulo 2 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="ca735-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="ca735-198">A seguir está uma configuração típica para o desenvolvimento com a realidade misturada e, como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="ca735-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="ca735-199">Abra o *Unity* e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="ca735-199">Open *Unity* and click **New**.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="ca735-201">Agora, você precisará fornecer um nome de projeto de Unity, inserir o **sr\_aplicativo de\_do Azure\_insights**.</span><span class="sxs-lookup"><span data-stu-id="ca735-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="ca735-202">Verifique se o *modelo* está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="ca735-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="ca735-203">Defina o *local* como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="ca735-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ca735-204">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="ca735-204">Then, click **Create project**.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="ca735-206">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ca735-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ca735-207">Vá para **Editar preferências de \>** e, em seguida, na nova janela, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="ca735-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ca735-208">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="ca735-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ca735-209">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="ca735-209">Close the **Preferences** window.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="ca735-211">Em seguida, vá para **arquivo \> configurações de Build** e alterne a plataforma para **plataforma universal do Windows**clicando no botão **alternar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="ca735-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="ca735-213">Vá para **arquivo \> configurações de compilação** e verifique se:</span><span class="sxs-lookup"><span data-stu-id="ca735-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="ca735-214">O **dispositivo de destino** está definido para **qualquer dispositivo**</span><span class="sxs-lookup"><span data-stu-id="ca735-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="ca735-215">Para o Microsoft HoloLens, defina o **dispositivo de destino** como *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="ca735-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="ca735-216">O **tipo de compilação** está definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="ca735-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="ca735-217">O **SDK** está definido para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="ca735-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="ca735-218">**Compilar e executar** é definido como **computador local**</span><span class="sxs-lookup"><span data-stu-id="ca735-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="ca735-219">Salve a cena e adicione-a à compilação.</span><span class="sxs-lookup"><span data-stu-id="ca735-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="ca735-220">Faça isso selecionando **Adicionar abrir cenas**.</span><span class="sxs-lookup"><span data-stu-id="ca735-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="ca735-221">Uma janela salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="ca735-221">A save window will appear.</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="ca735-223">Crie uma nova pasta para isso e qualquer cena futura, clique no botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.</span><span class="sxs-lookup"><span data-stu-id="ca735-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="ca735-225">Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo:* , digite **ApplicationInsightsScene**e clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="ca735-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="ca735-227">As configurações restantes, em **configurações de compilação**, devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="ca735-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="ca735-228">Na janela **configurações de compilação** , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o **Inspetor** está localizado.</span><span class="sxs-lookup"><span data-stu-id="ca735-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="ca735-230">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="ca735-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="ca735-231">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="ca735-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="ca735-232">A **versão de tempo de execução** de **script** deve ser **experimental (.NET 4,6 equivalente)** , o que irá disparar uma necessidade de reiniciar o editor.</span><span class="sxs-lookup"><span data-stu-id="ca735-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="ca735-233">O **back-end de script** deve ser **.net**</span><span class="sxs-lookup"><span data-stu-id="ca735-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="ca735-234">O **nível de compatibilidade da API** deve ser **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="ca735-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Configurar o projeto do Unity](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="ca735-236">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="ca735-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="ca735-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ca735-237">**InternetClient**</span></span>     

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="ca735-239">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o **SDK do Windows Mixed Reality** foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="ca735-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurar o projeto do Unity](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="ca735-241">De volta **às configurações de compilação**, os **projetos de C# Unity** não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste.</span><span class="sxs-lookup"><span data-stu-id="ca735-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="ca735-242">Feche a janela configurações de compilação.</span><span class="sxs-lookup"><span data-stu-id="ca735-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="ca735-243">Salve sua cena e projeto (**arquivo** > **salvar cena/arquivo** > **salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="ca735-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="ca735-244">Capítulo 3 – importar o pacote do Unity</span><span class="sxs-lookup"><span data-stu-id="ca735-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ca735-245">Se você quiser ignorar os componentes de *configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para baixar este [Azure-Mr-309. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), importe-o para seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="ca735-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="ca735-246">Isso também conterá as DLLs do próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="ca735-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="ca735-247">Após a importação, continue no [**capítulo 6**](#chapter-6---create-the-applicationinsightstracker-class).</span><span class="sxs-lookup"><span data-stu-id="ca735-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ca735-248">Para usar Application Insights no Unity, você precisa importar a DLL para ela, juntamente com a DLL Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="ca735-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="ca735-249">Atualmente, há um problema conhecido no Unity que exige que os plugins sejam reconfigurados após a importação.</span><span class="sxs-lookup"><span data-stu-id="ca735-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="ca735-250">Essas etapas (4-7 nesta seção) não serão mais necessárias depois que o bug for resolvido.</span><span class="sxs-lookup"><span data-stu-id="ca735-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="ca735-251">Para importar Application Insights para seu próprio projeto, verifique se você [baixou o '. unitypackage ', que contém os plug-ins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="ca735-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="ca735-252">Em seguida, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ca735-252">Then, do the following:</span></span>

1.  <span data-ttu-id="ca735-253">Adicione o **. unitypackage** ao Unity usando a opção de menu **ativos \> importar pacote \> pacote personalizado** .</span><span class="sxs-lookup"><span data-stu-id="ca735-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="ca735-254">Na caixa **Importar pacote de Unity** que é exibida, verifique se tudo em (e incluindo) **plug-ins** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="ca735-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="ca735-256">Clique no botão **importar** para adicionar os itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ca735-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="ca735-257">Vá para a pasta **insights** em **plug-ins** na exibição do projeto e selecione os seguintes plugins *somente*:</span><span class="sxs-lookup"><span data-stu-id="ca735-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="ca735-258">Microsoft. ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="ca735-258">Microsoft.ApplicationInsights</span></span>

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="ca735-260">Com este *plug-in* selecionado, verifique se **qualquer plataforma** está **desmarcada**e, em seguida, verifique se **WSAPlayer** também está **desmarcado**e clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="ca735-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="ca735-261">Fazer isso é apenas para confirmar que os arquivos estão configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="ca735-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="ca735-263">Marcando os plug-ins como este, os configura para serem usados apenas no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="ca735-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="ca735-264">Há um conjunto diferente de DLLs na pasta WSA que será usado depois que o projeto for exportado do Unity.</span><span class="sxs-lookup"><span data-stu-id="ca735-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="ca735-265">Em seguida, você precisa abrir a pasta **WSA** na pasta **insights** .</span><span class="sxs-lookup"><span data-stu-id="ca735-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="ca735-266">Você verá uma cópia do mesmo arquivo que acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="ca735-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="ca735-267">Selecione esse arquivo e, no Inspetor, verifique se **qualquer plataforma** está **desmarcada**e, em seguida, verifique se **somente** **WSAPlayer** está **marcado**.</span><span class="sxs-lookup"><span data-stu-id="ca735-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="ca735-268">Clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="ca735-268">Click **Apply**.</span></span>

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="ca735-270">Agora, você precisará seguir **as etapas de 4-6**, mas para os plug-ins *Newtonsoft* em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ca735-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="ca735-271">Consulte a captura de tela abaixo para saber a aparência do resultado.</span><span class="sxs-lookup"><span data-stu-id="ca735-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="ca735-273">Capítulo 4-configurar os controles de câmera e de usuário</span><span class="sxs-lookup"><span data-stu-id="ca735-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="ca735-274">Neste capítulo, você configurará a câmera e os controles para permitir que o usuário veja e mova-se na cena.</span><span class="sxs-lookup"><span data-stu-id="ca735-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="ca735-275">Clique com o botão direito do mouse em uma área vazia no painel hierarquia e, em seguida, em **criar** > **vazio**.</span><span class="sxs-lookup"><span data-stu-id="ca735-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="ca735-277">Renomeie o novo gameobject vazio para a **câmera pai**.</span><span class="sxs-lookup"><span data-stu-id="ca735-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="ca735-279">Clique com o botão direito do mouse em uma área vazia no painel hierarquia, depois em **objeto 3D**e, em seguida, em **esfera**.</span><span class="sxs-lookup"><span data-stu-id="ca735-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="ca735-280">Renomeie a esfera para a **direita**.</span><span class="sxs-lookup"><span data-stu-id="ca735-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="ca735-281">Defina a **escala de transformação** da mão direita para **0,1, 0,1, 0,1**</span><span class="sxs-lookup"><span data-stu-id="ca735-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="ca735-283">Remova o **componente colisor do Sphere** do lado direito clicando na **engrenagem** no componente colisor do *Sphere* e, em seguida, **remover componente**.</span><span class="sxs-lookup"><span data-stu-id="ca735-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="ca735-285">No painel hierarquia, arraste a **câmera principal** e os objetos **à direita** para o objeto **pai da câmera** .</span><span class="sxs-lookup"><span data-stu-id="ca735-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="ca735-287">Defina a **posição de transformação** da **câmera principal** e o objeto à **direita** como **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="ca735-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-31.png)

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="ca735-290">Capítulo 5 – configurar os objetos na cena do Unity</span><span class="sxs-lookup"><span data-stu-id="ca735-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="ca735-291">Agora você vai criar algumas formas básicas para sua cena, com as quais o usuário pode interagir.</span><span class="sxs-lookup"><span data-stu-id="ca735-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="ca735-292">Clique com o botão direito do mouse em uma área vazia no *painel hierarquia*e, em seguida, em **objeto 3D**, selecione **plano**.</span><span class="sxs-lookup"><span data-stu-id="ca735-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="ca735-293">Defina a **posição de transformação** plano como **0,-1, 0**.</span><span class="sxs-lookup"><span data-stu-id="ca735-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="ca735-294">Defina a **escala de transformação** do plano como **5, 1, 5**.</span><span class="sxs-lookup"><span data-stu-id="ca735-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="ca735-296">Crie um material básico para usar com o seu objeto **plano** , para que as outras formas sejam mais fáceis de ver.</span><span class="sxs-lookup"><span data-stu-id="ca735-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="ca735-297">Navegue até o *painel do projeto*, clique com o botão direito do mouse em, em seguida, **crie**, seguido por **pasta**, para criar uma nova pasta.</span><span class="sxs-lookup"><span data-stu-id="ca735-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="ca735-298">Nomeie os **materiais**de ti.</span><span class="sxs-lookup"><span data-stu-id="ca735-298">Name it **Materials**.</span></span>

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-34.png) ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="ca735-301">Abra a pasta **materiais** , clique com o botão direito do mouse em, clique em **criar**, em **material**, para criar um novo material.</span><span class="sxs-lookup"><span data-stu-id="ca735-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="ca735-302">Nomeie-o como **azul**.</span><span class="sxs-lookup"><span data-stu-id="ca735-302">Name it **Blue**.</span></span>

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-36.png) ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="ca735-305">Com o novo material **azul** selecionado, examine o *Inspetor*e clique na janela retangular junto com **albedo**.</span><span class="sxs-lookup"><span data-stu-id="ca735-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="ca735-306">Selecione uma cor azul (a imagem abaixo é uma **cor hexadecimal: \#3592FFFF**).</span><span class="sxs-lookup"><span data-stu-id="ca735-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="ca735-307">Clique no botão fechar depois de escolher.</span><span class="sxs-lookup"><span data-stu-id="ca735-307">Click the close button once you have chosen.</span></span>

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="ca735-309">Arraste o novo material da pasta **materiais** para o **plano**recém-criado, dentro de sua cena (ou solte-o no objeto **plano** dentro da *hierarquia*).</span><span class="sxs-lookup"><span data-stu-id="ca735-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="ca735-311">Clique com o botão direito do mouse em uma área vazia no *painel hierarquia*e, em seguida, em **objeto 3D, cápsula**.</span><span class="sxs-lookup"><span data-stu-id="ca735-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="ca735-312">Com a **cápsula** selecionada, altere sua *posição* de transformação para: **-10, 1, 0**.</span><span class="sxs-lookup"><span data-stu-id="ca735-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="ca735-313">Clique com o botão direito do mouse em uma área vazia no *painel hierarquia*e, em seguida, em **objeto 3D, cubo**.</span><span class="sxs-lookup"><span data-stu-id="ca735-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="ca735-314">Com o **cubo** selecionado, altere sua *posição* de transformação para: **0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="ca735-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="ca735-315">Clique com o botão direito do mouse em uma área vazia no *painel hierarquia*e, em seguida, em **objeto 3D, esfera**.</span><span class="sxs-lookup"><span data-stu-id="ca735-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="ca735-316">Com a **esfera** selecionada, altere sua *posição* de transformação para: **10, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="ca735-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="ca735-318">Esses valores de *posição* são *sugestões*.</span><span class="sxs-lookup"><span data-stu-id="ca735-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="ca735-319">Você tem a liberdade de definir as posições dos objetos para o que desejar, embora seja mais fácil para o usuário do aplicativo se as distâncias dos objetos não estiverem muito longe da câmera.</span><span class="sxs-lookup"><span data-stu-id="ca735-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="ca735-320">Quando seu aplicativo está em execução, ele precisa ser capaz de identificar os objetos na cena, para conseguir isso, eles precisam ser marcados.</span><span class="sxs-lookup"><span data-stu-id="ca735-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="ca735-321">Selecione um dos objetos e, no painel *Inspetor* , clique em **adicionar marca...** , que vai alternar o *Inspetor* com as **marcas & painel camadas** .</span><span class="sxs-lookup"><span data-stu-id="ca735-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="ca735-322">![configurar os objetos no](images/AzureLabs-Lab309-41.png) de cena do Unity ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="ca735-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="ca735-323">Clique no símbolo **+ (mais)** e digite o nome da marca como **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="ca735-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="ca735-325">Se você usar um nome diferente para sua marca, será necessário garantir que essa alteração também tenha *DataFromAnalytics*, *objecttrigger*e *olhar*, scripts mais tarde, para que seus objetos sejam encontrados e detectados dentro de sua cena.</span><span class="sxs-lookup"><span data-stu-id="ca735-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="ca735-326">Com a marca criada, agora você precisa aplicá-la a todos os três objetos.</span><span class="sxs-lookup"><span data-stu-id="ca735-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="ca735-327">Na *hierarquia*, mantenha a tecla **Shift** pressionada e, em seguida, clique nos objetos **cápsula**, **cubo**e **esfera**, no *Inspetor*, clique no menu suspenso junto com a **marca**e clique na marca *ObjectInScene* que você criou.</span><span class="sxs-lookup"><span data-stu-id="ca735-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="ca735-328">![configurar os objetos no](images/AzureLabs-Lab309-44.png) de cena do Unity ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="ca735-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="ca735-329">Capítulo 6-criar a classe ApplicationInsightsTracker</span><span class="sxs-lookup"><span data-stu-id="ca735-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="ca735-330">O primeiro script que você precisa criar é **ApplicationInsightsTracker**, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="ca735-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="ca735-331">Criar eventos com base nas interações do usuário para enviar ao Aplicativo Azure insights.</span><span class="sxs-lookup"><span data-stu-id="ca735-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="ca735-332">Criando nomes de evento apropriados, dependendo da interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="ca735-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="ca735-333">Enviando eventos para a instância do serviço de Application Insights.</span><span class="sxs-lookup"><span data-stu-id="ca735-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="ca735-334">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="ca735-334">To create this class:</span></span>

1.  <span data-ttu-id="ca735-335">Clique com o botão direito do mouse no *painel Projeto*e **crie** > **pasta**.</span><span class="sxs-lookup"><span data-stu-id="ca735-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="ca735-336">Nomeie a pasta **scripts**.</span><span class="sxs-lookup"><span data-stu-id="ca735-336">Name the folder **Scripts**.</span></span>

    ![Criar a classe ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Criar a classe ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="ca735-339">Com a pasta **scripts** criada, clique duas vezes nela para abrir.</span><span class="sxs-lookup"><span data-stu-id="ca735-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="ca735-340">Em seguida, dentro dessa pasta, clique com o botão direito do mouse em **criar** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="ca735-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="ca735-341">Nomeie o script **ApplicationInsightsTracker**.</span><span class="sxs-lookup"><span data-stu-id="ca735-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="ca735-342">Clique duas vezes no novo script **ApplicationInsightsTracker** para abri-lo com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ca735-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="ca735-343">Atualize os namespaces na parte superior do script para que sejam os seguintes:</span><span class="sxs-lookup"><span data-stu-id="ca735-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="ca735-344">Dentro da classe, insira as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="ca735-344">Inside the class insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > <span data-ttu-id="ca735-345">Defina os valores de **instrumentationKey, ApplicationId e API_Key** adequadamente, usando as *chaves de serviço* do portal do Azure, conforme mencionado no [capítulo 1](#chapter-1---the-azure-portal), etapa 9 em diante.</span><span class="sxs-lookup"><span data-stu-id="ca735-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="ca735-346">Em seguida, adicione os métodos **Start ()** e **ativo ()** , que serão chamados quando a classe for inicializada:</span><span class="sxs-lookup"><span data-stu-id="ca735-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  <span data-ttu-id="ca735-347">Adicione os métodos responsáveis por enviar os eventos e as métricas registradas pelo seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ca735-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  <span data-ttu-id="ca735-348">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="ca735-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="ca735-349">Capítulo 7-criar o script olhar</span><span class="sxs-lookup"><span data-stu-id="ca735-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="ca735-350">O próximo script a ser criado é o script **olhar** .</span><span class="sxs-lookup"><span data-stu-id="ca735-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="ca735-351">Esse script é responsável por criar um *Raycast* que será projetado para a frente da *câmera principal*, para detectar qual objeto o usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="ca735-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="ca735-352">Nesse caso, o *Raycast* precisará identificar se o usuário está olhando para um objeto com a marca **ObjectInScene** e, em seguida, contar quanto tempo o usuário *gazes* nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="ca735-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="ca735-353">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="ca735-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="ca735-354">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="ca735-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ca735-355">Nomeie o script **olhar**.</span><span class="sxs-lookup"><span data-stu-id="ca735-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="ca735-356">Clique duas vezes no script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca735-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="ca735-357">Substitua o código existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="ca735-357">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  <span data-ttu-id="ca735-358">Agora, o código para os métodos **ativo ()** e **Iniciar ()** precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="ca735-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  <span data-ttu-id="ca735-359">Dentro da classe **olhar** , adicione o seguinte código no método **Update ()** para projetar um *Raycast* e detectar a visita de destino:</span><span class="sxs-lookup"><span data-stu-id="ca735-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  <span data-ttu-id="ca735-360">Adicione o método **ResetFocusedObject ()** para enviar dados para **Application insights** quando o usuário tiver examinado um objeto.</span><span class="sxs-lookup"><span data-stu-id="ca735-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  <span data-ttu-id="ca735-361">Agora você concluiu o script **olhar** .</span><span class="sxs-lookup"><span data-stu-id="ca735-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="ca735-362">Salve suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="ca735-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="ca735-363">Capítulo 8-criar a classe objecttrigger</span><span class="sxs-lookup"><span data-stu-id="ca735-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="ca735-364">O próximo script que você precisa criar é **objecttrigger**, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="ca735-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="ca735-365">Adição de componentes necessários para a colisão na câmera principal.</span><span class="sxs-lookup"><span data-stu-id="ca735-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="ca735-366">Detectando se a câmera está perto de um objeto marcado como **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="ca735-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="ca735-367">Para criar o script:</span><span class="sxs-lookup"><span data-stu-id="ca735-367">To create the script:</span></span>

1.  <span data-ttu-id="ca735-368">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="ca735-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="ca735-369">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="ca735-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ca735-370">Nomeie o script **loadtrigger**.</span><span class="sxs-lookup"><span data-stu-id="ca735-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="ca735-371">Clique duas vezes no script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca735-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="ca735-372">Substitua o código existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="ca735-372">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  <span data-ttu-id="ca735-373">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="ca735-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="ca735-374">Capítulo 9-criar a classe DataFromAnalytics</span><span class="sxs-lookup"><span data-stu-id="ca735-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="ca735-375">Agora, você precisará criar o script **DataFromAnalytics** , que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="ca735-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="ca735-376">Buscar dados de análise sobre qual objeto foi abordado pela câmera mais.</span><span class="sxs-lookup"><span data-stu-id="ca735-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="ca735-377">Usando as *chaves de serviço*, que permitem a comunicação com sua instância de serviço do aplicativo Azure insights.</span><span class="sxs-lookup"><span data-stu-id="ca735-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="ca735-378">Classificação dos objetos em cena, de acordo com o qual tem a maior contagem de eventos.</span><span class="sxs-lookup"><span data-stu-id="ca735-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="ca735-379">Alterar a cor do material, do objeto mais aproximado, para *verde*.</span><span class="sxs-lookup"><span data-stu-id="ca735-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="ca735-380">Para criar o script:</span><span class="sxs-lookup"><span data-stu-id="ca735-380">To create the script:</span></span>

1.  <span data-ttu-id="ca735-381">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="ca735-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="ca735-382">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="ca735-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ca735-383">Nomeie o script **DataFromAnalytics**.</span><span class="sxs-lookup"><span data-stu-id="ca735-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="ca735-384">Clique duas vezes no script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca735-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="ca735-385">Insira os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="ca735-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="ca735-386">No script, insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ca735-386">Inside the script, insert the following:</span></span>

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  <span data-ttu-id="ca735-387">Dentro da classe **DataFromAnalytics** , logo após o método **Start ()** , adicione o método a seguir chamado **FetchAnalytics ()** .</span><span class="sxs-lookup"><span data-stu-id="ca735-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="ca735-388">Esse método é responsável por preencher a lista de pares chave-valor, com um *gameobject* e um número de contagem de eventos de espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="ca735-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="ca735-389">Em seguida, ele inicializa a corotina **GetWebRequest ()** .</span><span class="sxs-lookup"><span data-stu-id="ca735-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="ca735-390">A estrutura de consulta da chamada para *Application insights* pode ser encontrada dentro desse método também, como o ponto de extremidade da *URL de consulta* .</span><span class="sxs-lookup"><span data-stu-id="ca735-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  <span data-ttu-id="ca735-391">Logo abaixo do método **FetchAnalytics ()** , adicione um método chamado **GetWebRequest ()** , que retorna um *IEnumerator*.</span><span class="sxs-lookup"><span data-stu-id="ca735-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="ca735-392">Esse método é responsável por solicitar o número de vezes que um evento, correspondente a um *gameobject*específico, foi chamado dentro de *Application insights*.</span><span class="sxs-lookup"><span data-stu-id="ca735-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="ca735-393">Quando todas as consultas enviadas retornam, o método **DetermineWinner ()** é chamado.</span><span class="sxs-lookup"><span data-stu-id="ca735-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readability).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="ca735-394">O método Next é **DetermineWinner ()** , que classifica a lista de pares *gameobject* e *int* , de acordo com a contagem de eventos mais alta.</span><span class="sxs-lookup"><span data-stu-id="ca735-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="ca735-395">Em seguida, ele altera a cor do material desse *gameobject* para *verde* (como comentários para ele com a contagem mais alta).</span><span class="sxs-lookup"><span data-stu-id="ca735-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="ca735-396">Isso exibe uma mensagem com os resultados da análise.</span><span class="sxs-lookup"><span data-stu-id="ca735-396">This displays a message with the analytics results.</span></span>

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  <span data-ttu-id="ca735-397">Adicione a estrutura de classe que será usada para desserializar o objeto JSON, recebido do *Application insights*.</span><span class="sxs-lookup"><span data-stu-id="ca735-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="ca735-398">Adicione essas classes na parte inferior do arquivo de classe **DataFromAnalytics** , **fora** da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="ca735-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. <span data-ttu-id="ca735-399">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="ca735-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="ca735-400">Capítulo 10 – criar a classe de movimento</span><span class="sxs-lookup"><span data-stu-id="ca735-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="ca735-401">O script de **movimento** é o próximo script que será necessário criar.</span><span class="sxs-lookup"><span data-stu-id="ca735-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="ca735-402">É responsável por:</span><span class="sxs-lookup"><span data-stu-id="ca735-402">It is responsible for:</span></span>

- <span data-ttu-id="ca735-403">Mover a câmera principal de acordo com a direção em que a câmera está procurando.</span><span class="sxs-lookup"><span data-stu-id="ca735-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="ca735-404">Adicionando todos os outros scripts a objetos de cena.</span><span class="sxs-lookup"><span data-stu-id="ca735-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="ca735-405">Para criar o script:</span><span class="sxs-lookup"><span data-stu-id="ca735-405">To create the script:</span></span>

1.  <span data-ttu-id="ca735-406">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="ca735-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="ca735-407">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="ca735-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ca735-408">Nomeie a **movimentação**do script.</span><span class="sxs-lookup"><span data-stu-id="ca735-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="ca735-409">Clique duas vezes no script para abri-lo com o *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="ca735-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="ca735-410">Substitua o código existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="ca735-410">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  <span data-ttu-id="ca735-411">Dentro da classe de **movimento** , *abaixo* do método **Update ()** vazio, insira os seguintes métodos que permitem ao usuário usar o controlador de mão para mover no espaço virtual:</span><span class="sxs-lookup"><span data-stu-id="ca735-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  <span data-ttu-id="ca735-412">Adicione por último a chamada de método no método **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="ca735-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="ca735-413">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="ca735-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="ca735-414">Capítulo 11-configurando as referências de scripts</span><span class="sxs-lookup"><span data-stu-id="ca735-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="ca735-415">Neste capítulo, você precisa posicionar o script de **movimento** no **pai da câmera** e definir seus destinos de referência.</span><span class="sxs-lookup"><span data-stu-id="ca735-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="ca735-416">Esse script manipulará a colocação dos outros scripts onde eles precisam ser.</span><span class="sxs-lookup"><span data-stu-id="ca735-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="ca735-417">Na pasta **scripts** do *painel Projeto*, arraste o script de **movimento** para o objeto **pai da câmera** , localizado no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="ca735-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Configurando as referências de scripts na cena do Unity](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="ca735-419">Clique no **pai da câmera**.</span><span class="sxs-lookup"><span data-stu-id="ca735-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="ca735-420">No *painel hierarquia*, arraste o objeto **à direita** do *painel hierarquia* para o destino de referência, **controlador**, no *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="ca735-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="ca735-421">Defina a **velocidade do usuário** como **5**, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="ca735-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Configurando as referências de scripts na cena do Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="ca735-423">Capítulo 12-criar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="ca735-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="ca735-424">Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.</span><span class="sxs-lookup"><span data-stu-id="ca735-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="ca735-425">Navegue até **configurações de compilação**, (**arquivo** > **configurações de Build**).</span><span class="sxs-lookup"><span data-stu-id="ca735-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="ca735-426">Na janela **configurações de compilação** , clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ca735-426">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilar o projeto do Unity para a solução UWP](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="ca735-428">Uma janela do **Explorador de arquivos** será exibida, solicitando um local para a compilação.</span><span class="sxs-lookup"><span data-stu-id="ca735-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="ca735-429">Crie uma nova pasta (clicando em **nova pasta** no canto superior esquerdo) e nomeie-a como **Build**.</span><span class="sxs-lookup"><span data-stu-id="ca735-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Compilar o projeto do Unity para a solução UWP](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="ca735-431">Abra a nova pasta **Builds** e crie outra pasta (usando a **nova pasta** mais uma vez) e nomeie-a como **sr\_Azure\_aplicativo\_insights**.</span><span class="sxs-lookup"><span data-stu-id="ca735-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![Compilar o projeto do Unity para a solução UWP](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="ca735-433">Com a pasta **sr\_aplicativo do Azure\_\_insights** selecionada, clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="ca735-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="ca735-434">O projeto levará um minuto ou mais para ser compilado.</span><span class="sxs-lookup"><span data-stu-id="ca735-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="ca735-435">Após a *compilação*, o **Explorador de arquivos** aparecerá mostrando o local do novo projeto.</span><span class="sxs-lookup"><span data-stu-id="ca735-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a><span data-ttu-id="ca735-436">Capítulo 13-implantar MR_Azure_Application_Insights aplicativo em seu computador</span><span class="sxs-lookup"><span data-stu-id="ca735-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="ca735-437">Para implantar o **aplicativo do sr\_Azure\_\_aplicativo insights** em seu computador local:</span><span class="sxs-lookup"><span data-stu-id="ca735-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="ca735-438">Abra o arquivo de solução do seu **sr\_aplicativo do Azure\_\_aplicativo insights** no **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ca735-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="ca735-439">Na **plataforma da solução**, selecione **x86, computador local**.</span><span class="sxs-lookup"><span data-stu-id="ca735-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="ca735-440">Na **configuração da solução** , selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="ca735-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![Compilar o projeto do Unity para a solução UWP](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="ca735-442">Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="ca735-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="ca735-443">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="ca735-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="ca735-444">Inicie o aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="ca735-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="ca735-445">Mova-se para a cena, abordando objetos e examinando-os, quando o *serviço do Azure insights* coletou dados de eventos suficientes, ele definirá o objeto que foi abordado o mais verde.</span><span class="sxs-lookup"><span data-stu-id="ca735-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="ca735-446">Enquanto o tempo de espera médio para os *eventos e as métricas* a serem coletados pelo serviço leva cerca de 15 minutos, em algumas ocasiões, pode levar até 1 hora.</span><span class="sxs-lookup"><span data-stu-id="ca735-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="ca735-447">Capítulo 14-o portal do serviço Application Insights</span><span class="sxs-lookup"><span data-stu-id="ca735-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="ca735-448">Depois de fazer roaming da cena e gazed em vários objetos, você pode ver os dados coletados no portal do *serviço de Application insights* .</span><span class="sxs-lookup"><span data-stu-id="ca735-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="ca735-449">Volte para o portal do serviço Application Insights.</span><span class="sxs-lookup"><span data-stu-id="ca735-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="ca735-450">Clique em *Metrics Explorer*.</span><span class="sxs-lookup"><span data-stu-id="ca735-450">Click on *Metrics Explorer*.</span></span>

    ![Examinando os dados coletados](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="ca735-452">Ele será aberto em uma guia que contém o grafo que representa os *eventos e as métricas* relacionados ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca735-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="ca735-453">Conforme mencionado acima, pode levar algum tempo (até 1 hora) para que os dados sejam exibidos no grafo</span><span class="sxs-lookup"><span data-stu-id="ca735-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![Examinando os dados coletados](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="ca735-455">Clique na *barra de eventos* no *total de eventos* por versão do aplicativo para ver uma análise detalhada dos eventos com seus nomes.</span><span class="sxs-lookup"><span data-stu-id="ca735-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![Examinando os dados coletados](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="ca735-457">Seu aplicativo de serviço Application Insights concluído</span><span class="sxs-lookup"><span data-stu-id="ca735-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="ca735-458">Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço de Application Insights para monitorar a atividade do usuário em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca735-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![resultado do curso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="ca735-460">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="ca735-460">Bonus Exercises</span></span>

<span data-ttu-id="ca735-461">**Exercício 1**</span><span class="sxs-lookup"><span data-stu-id="ca735-461">**Exercise 1**</span></span>

<span data-ttu-id="ca735-462">Tente gerar, em vez de criar manualmente, os objetos ObjectInScene e definir suas coordenadas no plano dentro de seus scripts.</span><span class="sxs-lookup"><span data-stu-id="ca735-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="ca735-463">Dessa forma, você pode perguntar ao Azure qual era o objeto mais popular (seja de olhar ou resultados de proximidade) e gerar um *extra* desses objetos.</span><span class="sxs-lookup"><span data-stu-id="ca735-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="ca735-464">**Exercício 2**</span><span class="sxs-lookup"><span data-stu-id="ca735-464">**Exercise 2**</span></span>

<span data-ttu-id="ca735-465">Classifique seus resultados de Application Insights por tempo, para que você obtenha os dados mais relevantes e implemente esses dados confidenciais em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca735-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

