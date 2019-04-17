---
title: MR e Azure 309 - Application insights
description: Conclua este curso para aprender a coletar análise sobre o comportamento do usuário dentro de um aplicativo de realidade misturada, usando o serviço de Insights de aplicativo do Azure.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, insights de aplicativo, hololens, imersivo, vr
ms.openlocfilehash: 838dbe38724d29f4c5987e2f6ac7a07231015c82
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590954"
---
>[!NOTE]
><span data-ttu-id="faced-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="faced-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="faced-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="faced-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="faced-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="faced-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="faced-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="faced-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="faced-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="faced-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="faced-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="faced-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="faced-110">MR e o Azure 309: Insights de aplicativo</span><span class="sxs-lookup"><span data-stu-id="faced-110">MR and Azure 309: Application insights</span></span>

![final do produto-iniciar](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="faced-112">Neste curso, você aprenderá a adicionar recursos do Application Insights a um aplicativo de realidade misturada, usando a API do Azure Application Insights para coletar análises sobre o comportamento do usuário.</span><span class="sxs-lookup"><span data-stu-id="faced-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="faced-113">Application Insights é um serviço da Microsoft, permitindo que os desenvolvedores colete análises em seus aplicativos e gerenciá-lo de um portal fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="faced-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="faced-114">A análise pode ser qualquer coisa, desde desempenho a informações personalizadas que você deseja coletar.</span><span class="sxs-lookup"><span data-stu-id="faced-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="faced-115">Para obter mais informações, visite o [página do Application Insights](https://azure.microsoft.com/services/application-insights/).</span><span class="sxs-lookup"><span data-stu-id="faced-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="faced-116">Com a conclusão deste curso, você terá um aplicativo de imersivo headset de realidade misturada que serão capaz de fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="faced-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="faced-117">Permitir que o usuário olhares e navegar em torno de uma cena.</span><span class="sxs-lookup"><span data-stu-id="faced-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="faced-118">Disparar o envio de análise para o *serviço Application Insights*, com o uso de olhar e a proximidade com os objetos na cena.</span><span class="sxs-lookup"><span data-stu-id="faced-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="faced-119">O aplicativo também chamará após o serviço, buscando informações sobre qual objeto foi atingido o máximo pelo usuário, nas últimas 24 horas.</span><span class="sxs-lookup"><span data-stu-id="faced-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="faced-120">Esse objeto será alterar sua cor verde.</span><span class="sxs-lookup"><span data-stu-id="faced-120">That object will change its color to green.</span></span>

<span data-ttu-id="faced-121">Este curso ensinará como obter os resultados do serviço Application Insights, em um aplicativo de exemplo com base no Unity.</span><span class="sxs-lookup"><span data-stu-id="faced-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="faced-122">Ele será cabe a você aplicar esses conceitos para um aplicativo personalizado que você pode criar.</span><span class="sxs-lookup"><span data-stu-id="faced-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="faced-123">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="faced-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="faced-124">Curso</span><span class="sxs-lookup"><span data-stu-id="faced-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="faced-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="faced-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="faced-126"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="faced-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="faced-127">MR e o Azure 309: Insights de aplicativo</span><span class="sxs-lookup"><span data-stu-id="faced-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="faced-128">✔️</span><span class="sxs-lookup"><span data-stu-id="faced-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="faced-129">✔️</span><span class="sxs-lookup"><span data-stu-id="faced-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="faced-130">Enquanto este curso se concentra primariamente em fones de ouvido Windows Mixed Reality de imersão (VR), você também pode aplicar o que você aprenderá neste curso para o Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="faced-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="faced-131">Como acompanhar o curso, você verá notas quaisquer alterações que talvez seja necessário empregar para dar suporte ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="faced-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="faced-132">Ao usar o HoloLens, você pode perceber algum eco durante a captura de voz.</span><span class="sxs-lookup"><span data-stu-id="faced-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="faced-133">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="faced-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="faced-134">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="faced-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="faced-135">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (julho de 2018).</span><span class="sxs-lookup"><span data-stu-id="faced-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="faced-136">Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que está listado abaixo.</span><span class="sxs-lookup"><span data-stu-id="faced-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="faced-137">Recomendamos que o hardware e software para este curso a seguir:</span><span class="sxs-lookup"><span data-stu-id="faced-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="faced-138">Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)</span><span class="sxs-lookup"><span data-stu-id="faced-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="faced-139">Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="faced-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="faced-140">O SDK mais recente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="faced-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="faced-141">2017.4 do Unity</span><span class="sxs-lookup"><span data-stu-id="faced-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="faced-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="faced-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="faced-143">Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="faced-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="faced-144">Um conjunto de fones de ouvido com um microfone interno (se o fone de ouvido não tem um microfone interno e alto-falantes)</span><span class="sxs-lookup"><span data-stu-id="faced-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="faced-145">Acesso à Internet para a instalação do Azure e a recuperação de dados do Application Insights</span><span class="sxs-lookup"><span data-stu-id="faced-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="faced-146">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="faced-146">Before you start</span></span>

<span data-ttu-id="faced-147">Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="faced-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="faced-148">Esteja ciente de dados que vai *Application Insights* leva tempo, portanto, seja paciente.</span><span class="sxs-lookup"><span data-stu-id="faced-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="faced-149">Se você quiser verificar se o serviço recebeu os dados, fazer check-out [capítulo 14](#chapter-14---the-application-insights-service-portal), que mostra como navegar o portal.</span><span class="sxs-lookup"><span data-stu-id="faced-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="faced-150">Capítulo 1 - Portal do Azure</span><span class="sxs-lookup"><span data-stu-id="faced-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="faced-151">Para usar *Application Insights*, você precisará criar e configurar um *serviço Application Insights* no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="faced-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="faced-152">Faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="faced-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="faced-153">Se você ainda não tiver uma conta do Azure, você precisará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="faced-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="faced-154">Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="faced-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="faced-155">Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure *Application Insights*e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="faced-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="faced-156">A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="faced-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="faced-158">A nova página à direita fornece uma descrição do *Azure Application Insights* Service.</span><span class="sxs-lookup"><span data-stu-id="faced-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="faced-159">Na parte inferior esquerda desta página, selecione a **criar** botão para criar uma associação com este serviço.</span><span class="sxs-lookup"><span data-stu-id="faced-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="faced-161">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="faced-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="faced-162">Inserir sua desejada **nome** para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="faced-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="faced-163">Como **tipo de aplicativo**, selecione **geral**.</span><span class="sxs-lookup"><span data-stu-id="faced-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="faced-164">Selecione uma opção apropriada **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="faced-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="faced-165">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="faced-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="faced-166">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="faced-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="faced-167">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="faced-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="faced-168">Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="faced-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="faced-169">Selecione uma **local**.</span><span class="sxs-lookup"><span data-stu-id="faced-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="faced-170">Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="faced-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="faced-171">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="faced-171">Select **Create**.</span></span>

        ![Portal do Azure](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="faced-173">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="faced-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="faced-174">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="faced-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="faced-176">Clique em notificações para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="faced-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="faced-178">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="faced-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="faced-179">Você será levado para a nova *serviço Application Insights* instância.</span><span class="sxs-lookup"><span data-stu-id="faced-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="faced-181">Mantenha essa página da web aberta e fácil de acesso, você será volte aqui frequentemente para ver os dados coletados.</span><span class="sxs-lookup"><span data-stu-id="faced-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="faced-182">Para implementar o Application Insights, você precisará usar valores específicos três (3): **Chave de instrumentação**, **ID do aplicativo**, e **chave API**.</span><span class="sxs-lookup"><span data-stu-id="faced-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="faced-183">Abaixo, você verá como recuperar esses valores de seu serviço.</span><span class="sxs-lookup"><span data-stu-id="faced-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="faced-184">Anote esses valores em um espaço em branco *bloco de notas* página, pois você irá usá-los em breve em seu código.</span><span class="sxs-lookup"><span data-stu-id="faced-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="faced-185">Para localizar o **chave de instrumentação**, você precisará rolar para baixo a lista de funções de serviço e clique em **propriedades**, a guia exibida revelará o **chave de serviço**.</span><span class="sxs-lookup"><span data-stu-id="faced-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="faced-187">Um pouco abaixo **propriedades**, você encontrará **acesso à API**, que você precisa clicar.</span><span class="sxs-lookup"><span data-stu-id="faced-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="faced-188">O painel à direita fornece o **ID do aplicativo** do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="faced-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="faced-190">Com o **ID do aplicativo** painel ainda estiver aberta, clique **criar chave de API**, que abrirá o *criar chave de API* painel.</span><span class="sxs-lookup"><span data-stu-id="faced-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Portal do Azure](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="faced-192">Dentro de abrir o agora *criar chave de API* do painel, digite uma descrição, e **marque as caixas de três**.</span><span class="sxs-lookup"><span data-stu-id="faced-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="faced-193">Clique em **gerar chave**.</span><span class="sxs-lookup"><span data-stu-id="faced-193">Click **Generate Key**.</span></span> <span data-ttu-id="faced-194">Sua **chave de API** será criado e exibido.</span><span class="sxs-lookup"><span data-stu-id="faced-194">Your **API Key** will be created and displayed.</span></span> 

    ![Portal do Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="faced-196">Esta é a única vez sua **chave de serviço** será exibida, portanto, verifique se você fazer uma cópia dele agora.</span><span class="sxs-lookup"><span data-stu-id="faced-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="faced-197">Capítulo 2 - configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="faced-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="faced-198">A seguir é um conjunto típico backup para o desenvolvimento com a realidade misturada e como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="faced-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="faced-199">Abra *Unity* e clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="faced-199">Open *Unity* and click **New**.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="faced-201">Agora você precisará fornecer um nome de projeto do Unity, insira **MR\_Azure\_Application\_Insights**.</span><span class="sxs-lookup"><span data-stu-id="faced-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="faced-202">Verifique se o *modelo* é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="faced-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="faced-203">Defina as *local* para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="faced-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="faced-204">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="faced-204">Then, click **Create project**.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="faced-206">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="faced-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="faced-207">Vá para **edite \> preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="faced-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="faced-208">Alteração **Editor de Script externo** à **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="faced-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="faced-209">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="faced-209">Close the **Preferences** window.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="faced-211">Em seguida, vá para **arquivo \> configurações de Build** e alterne a plataforma **plataforma Universal do Windows**, clicando no **alternar plataforma** botão.</span><span class="sxs-lookup"><span data-stu-id="faced-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="faced-213">Vá para **arquivo \> configurações de Build** e certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="faced-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="faced-214">**Dispositivo de destino** é definido como **qualquer dispositivo**</span><span class="sxs-lookup"><span data-stu-id="faced-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="faced-215">Para o Microsoft HoloLens, defina **dispositivo de destino** à *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="faced-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="faced-216">**Tipo de compilação** é definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="faced-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="faced-217">**SDK** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="faced-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="faced-218">**Compilar e executar** é definido como **Máquina Local**</span><span class="sxs-lookup"><span data-stu-id="faced-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="faced-219">Salve a cena e adicioná-lo para a compilação.</span><span class="sxs-lookup"><span data-stu-id="faced-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="faced-220">Fazer isso selecionando **cenas abra Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="faced-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="faced-221">Salvamento janela será exibida.</span><span class="sxs-lookup"><span data-stu-id="faced-221">A save window will appear.</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="faced-223">Criar uma nova pasta para isso e qualquer cena futuras, clique o **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.</span><span class="sxs-lookup"><span data-stu-id="faced-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="faced-225">Abrir seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo:* campo de texto, digite **ApplicationInsightsScene**, em seguida, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="faced-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="faced-227">O restante de configurações, em **configurações de Build**, deverá ser deixado como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="faced-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="faced-228">No **configurações de Build** janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o **Inspetor** está localizado.</span><span class="sxs-lookup"><span data-stu-id="faced-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="faced-230">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="faced-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="faced-231">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="faced-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="faced-232">**Criação de scripts** **versão de tempo de execução** deve ser **Experimental (equivalente ao .NET 4.6)**, que irá disparar uma necessidade de reiniciar o Editor.</span><span class="sxs-lookup"><span data-stu-id="faced-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="faced-233">**Script de back-end** deve ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="faced-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="faced-234">**Nível de compatibilidade de API** deve ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="faced-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Configurar o projeto do Unity](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="faced-236">Dentro de **configurações de publicação** guia, em **recursos**, verifique:</span><span class="sxs-lookup"><span data-stu-id="faced-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="faced-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="faced-237">**InternetClient**</span></span>     

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="faced-239">Mais para baixo no painel, no **XR configurações** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **realidade mista do Windows SDK** é adicionado.</span><span class="sxs-lookup"><span data-stu-id="faced-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurar o projeto do Unity](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="faced-241">Volta **configurações de Build**, **Unity C\# projetos** não fica acinzentado; marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="faced-241">Back in **Build Settings**, **Unity C\# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="faced-242">Feche a janela de configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="faced-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="faced-243">Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="faced-243">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="faced-244">Capítulo 3: importar o pacote do Unity</span><span class="sxs-lookup"><span data-stu-id="faced-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="faced-245">Se você quiser ignorar a *configurar o Unity* componentes deste curso e continuar diretamente no código, fique à vontade para baixá-lo [MR-Azure-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="faced-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="faced-246">Isso também irá conter as DLLs do próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="faced-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="faced-247">Após a importação, continuar a partir [ **capítulo 6**](#chapter-6---create-the-applicationinsightstracker-class).</span><span class="sxs-lookup"><span data-stu-id="faced-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="faced-248">Para usar o Application Insights dentro do Unity, você precisa importar a DLL para ele, junto com a DLL da Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="faced-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="faced-249">Atualmente, há um problema conhecido no Unity que requer o plug-ins para ser reconfigurado após a importação.</span><span class="sxs-lookup"><span data-stu-id="faced-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="faced-250">Estas etapas (4 a 7 desta seção) não será necessárias depois que o bug foi resolvido.</span><span class="sxs-lookup"><span data-stu-id="faced-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="faced-251">Para importar o Application Insights em seu próprio projeto, certifique-se de ter [baixado de 'unitypackage', que contém os plug-ins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="faced-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="faced-252">Em seguida, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="faced-252">Then, do the following:</span></span>

1.  <span data-ttu-id="faced-253">Adicionar o **unitypackage** para o Unity, usando o **ativos \> Importar pacote \> pacote personalizado** opção de menu.</span><span class="sxs-lookup"><span data-stu-id="faced-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="faced-254">No **Importar pacote do Unity** caixa é exibido para cima, certifique-se de tudo em (e incluindo) **plug-ins** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="faced-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="faced-256">Clique o **importação** botão para adicionar itens ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="faced-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="faced-257">Vá para o **Insights** pasta sob **plug-ins** no projeto, exibir e selecione os seguintes plug-ins *apenas*:</span><span class="sxs-lookup"><span data-stu-id="faced-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="faced-258">Microsoft.ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="faced-258">Microsoft.ApplicationInsights</span></span>

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="faced-260">Com isso *plug-in* selecionado, certifique-se de que **qualquer plataforma** é **desmarcada**, em seguida, certifique-se de que **WSAPlayer** também é  **não verificado**, em seguida, clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="faced-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="faced-261">Fazer isso é apenas para confirmar se os arquivos estão configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="faced-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="faced-263">Marcar os plug-ins como este, configura para ser usado apenas no Editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="faced-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="faced-264">Há um conjunto diferente de DLLs na pasta do WSA que será usado depois que o projeto é exportado do Unity.</span><span class="sxs-lookup"><span data-stu-id="faced-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="faced-265">Em seguida, você precisa abrir o **WSA** pasta, dentro de **Insights** pasta.</span><span class="sxs-lookup"><span data-stu-id="faced-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="faced-266">Você verá uma cópia do mesmo arquivo que você acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="faced-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="faced-267">Selecione esse arquivo e, em seguida, no Inspetor de, certifique-se de que **Any Platform** é **desmarcada**, em seguida, certifique-se de que **apenas** **WSAPlayer** é **verificado**.</span><span class="sxs-lookup"><span data-stu-id="faced-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="faced-268">Clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="faced-268">Click **Apply**.</span></span>

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="faced-270">Agora você precisará seguir **as etapas 4 a 6**, mas para o *Newtonsoft* plug-ins em vez disso.</span><span class="sxs-lookup"><span data-stu-id="faced-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="faced-271">Consulte a captura de tela para que o resultado deve ter aparência abaixo.</span><span class="sxs-lookup"><span data-stu-id="faced-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="faced-273">Capítulo 4 - configurar a câmera e o usuário controles</span><span class="sxs-lookup"><span data-stu-id="faced-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="faced-274">Neste capítulo você configurará a câmera e os controles para permitir que o usuário vê e mover na cena.</span><span class="sxs-lookup"><span data-stu-id="faced-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="faced-275">Clique duas vezes em uma área vazia no painel de hierarquia, em seguida, em **criar > vazio**.</span><span class="sxs-lookup"><span data-stu-id="faced-275">Right-click in an empty area in the Hierarchy Panel, then on **Create > Empty**.</span></span>

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="faced-277">Renomeie o novo GameObject vazio para **pai da câmera**.</span><span class="sxs-lookup"><span data-stu-id="faced-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="faced-279">Clique duas vezes em uma área vazia no painel de hierarquia, em seguida, em **objeto 3D**, em seguida, na **esfera**.</span><span class="sxs-lookup"><span data-stu-id="faced-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="faced-280">Renomear a esfera **mão direita**.</span><span class="sxs-lookup"><span data-stu-id="faced-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="faced-281">Defina a **transformar escala** da mão direita para **0,1, 0.1, 0,1**</span><span class="sxs-lookup"><span data-stu-id="faced-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="faced-283">Remover o **esfera Colisor** componente da mão direita clicando na **engrenagem** no *Colisor esfera* componente e, em seguida, **remover componente** .</span><span class="sxs-lookup"><span data-stu-id="faced-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="faced-285">Em arrastar o painel de hierarquia a **câmera principal** e o **mão direita** objetos para o **câmera pai** objeto.</span><span class="sxs-lookup"><span data-stu-id="faced-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="faced-287">Defina a **transformar posição** de ambos o **câmera principal** e o **mão direita** do objeto para **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="faced-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-31.png)

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="faced-290">Capítulo 5 – configurar os objetos na cena Unity</span><span class="sxs-lookup"><span data-stu-id="faced-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="faced-291">Agora, você criará algumas formas básicas para sua cena, com a qual o usuário pode interagir.</span><span class="sxs-lookup"><span data-stu-id="faced-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="faced-292">Clique com botão direito em uma área vazia na *painel de hierarquia*, em seguida, na **objeto 3D**, em seguida, selecione **plano**.</span><span class="sxs-lookup"><span data-stu-id="faced-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="faced-293">Defina o plano **transformar posição** à **0, -1, 0**.</span><span class="sxs-lookup"><span data-stu-id="faced-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="faced-294">Defina o plano **transformar escala** à **5, 1, 5**.</span><span class="sxs-lookup"><span data-stu-id="faced-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="faced-296">Criar um material básico para usar com seu **plano** objeto, de modo que as outras formas são mais fácil de ver.</span><span class="sxs-lookup"><span data-stu-id="faced-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="faced-297">Navegue até sua *painel projeto*, direito do mouse em seguida **Create**, seguido por **pasta**, para criar uma nova pasta.</span><span class="sxs-lookup"><span data-stu-id="faced-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="faced-298">Denomine **materiais**.</span><span class="sxs-lookup"><span data-stu-id="faced-298">Name it **Materials**.</span></span>

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-34.png) ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="faced-301">Abra o **materiais** pasta, em seguida, clique com botão direito, clique **criar**, em seguida, **Material**, para criar um novo material.</span><span class="sxs-lookup"><span data-stu-id="faced-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="faced-302">Denomine **azul**.</span><span class="sxs-lookup"><span data-stu-id="faced-302">Name it **Blue**.</span></span>

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-36.png) ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="faced-305">Com o novo **azul** material selecionado, procure na *Inspetor*e clique na janela retangular juntamente com **Albedo**.</span><span class="sxs-lookup"><span data-stu-id="faced-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="faced-306">Selecione uma cor azul (uma imagem abaixo é **cor hexadecimal: \#3592FFFF**).</span><span class="sxs-lookup"><span data-stu-id="faced-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="faced-307">Depois de ter escolhido, clique no botão Fechar.</span><span class="sxs-lookup"><span data-stu-id="faced-307">Click the close button once you have chosen.</span></span>

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="faced-309">Arraste o novo material do **materiais** pasta em seu recém-criado **plano**, dentro de sua cena (ou remova-o na **plano** dentro do objeto a  *Hierarquia*).</span><span class="sxs-lookup"><span data-stu-id="faced-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="faced-311">Clique com botão direito em uma área vazia na *painel de hierarquia*, em seguida, na **objeto 3D, Cápsula**.</span><span class="sxs-lookup"><span data-stu-id="faced-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="faced-312">Com o **Cápsula** selecionado, altere sua **transformar** *posição* para: **-10, 1, 0**.</span><span class="sxs-lookup"><span data-stu-id="faced-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="faced-313">Clique com botão direito em uma área vazia na *painel de hierarquia*, em seguida, na **objeto 3D, o cubo**.</span><span class="sxs-lookup"><span data-stu-id="faced-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="faced-314">Com o **cubo** selecionado, altere sua **transformar** *posição* para: **0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="faced-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="faced-315">Clique com botão direito em uma área vazia na *painel de hierarquia*, em seguida, na **objeto 3D, esfera**.</span><span class="sxs-lookup"><span data-stu-id="faced-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="faced-316">Com o **esfera** selecionado, altere sua **transformar** *posição* para: **10, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="faced-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="faced-318">Eles *posição* valores são *sugestões*.</span><span class="sxs-lookup"><span data-stu-id="faced-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="faced-319">Você é livre para definir as posições dos objetos para tudo o que você gostaria, embora seja mais fácil para o usuário do aplicativo se as distâncias de objetos não são muito distante da câmera.</span><span class="sxs-lookup"><span data-stu-id="faced-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="faced-320">Quando seu aplicativo é executado, ele precisa ser capaz de identificar os objetos na cena, para fazer isso, eles precisam ser marcadas.</span><span class="sxs-lookup"><span data-stu-id="faced-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="faced-321">Selecione um dos objetos e nos *Inspector* do painel, clique em **Adicionar marca...** , que alternará os *Inspetor* com o **marcas e camadas** painel.</span><span class="sxs-lookup"><span data-stu-id="faced-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="faced-322">![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="faced-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="faced-323">Clique o **+ (adição)** símbolo e, em seguida, digite o nome da marca como **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="faced-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="faced-325">Se você usar um nome diferente para a sua marca, você precisará garantir que essa alteração também é feita a *DataFromAnalytics*, *ObjectTrigger*, e *olhares*, scripts mais tarde, para que seu objetos forem encontrados e detectados dentro de sua cena.</span><span class="sxs-lookup"><span data-stu-id="faced-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="faced-326">Com a marca criada, você precisará aplicá-la a todos os três dos seus objetos.</span><span class="sxs-lookup"><span data-stu-id="faced-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="faced-327">Dos *hierarquia*, mantenha a **Shift** da chave e, em seguida, clique no **Cápsula**, **cubo**, e **esfera**, objetos, em seguida, nos *Inspector*, clique no menu suspenso ao lado **marca**, em seguida, clique no *ObjectInScene* marca que você criou.</span><span class="sxs-lookup"><span data-stu-id="faced-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="faced-328">![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="faced-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="faced-329">Capítulo 6 - criar a classe ApplicationInsightsTracker</span><span class="sxs-lookup"><span data-stu-id="faced-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="faced-330">É o primeiro script que você precisa criar **ApplicationInsightsTracker**, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="faced-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="faced-331">Criando eventos com base em interações do usuário para enviar para o Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="faced-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="faced-332">Criando nomes de eventos apropriados, dependendo da interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="faced-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="faced-333">Enviar eventos para a instância do serviço Application Insights.</span><span class="sxs-lookup"><span data-stu-id="faced-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="faced-334">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="faced-334">To create this class:</span></span>

1.  <span data-ttu-id="faced-335">Clique com botão direito no *painel do projeto*, em seguida, **criar > pasta**.</span><span class="sxs-lookup"><span data-stu-id="faced-335">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="faced-336">Nomeie a pasta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="faced-336">Name the folder **Scripts**.</span></span>

    ![Criar a classe ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Criar a classe ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="faced-339">Com o **Scripts** pasta criada, clique duas vezes nele, para abrir.</span><span class="sxs-lookup"><span data-stu-id="faced-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="faced-340">Em seguida, dentro dessa pasta, direito do mouse **criar > C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="faced-340">Then, within that folder, right-click, **Create > C\# Script**.</span></span> <span data-ttu-id="faced-341">Nomeie o script **ApplicationInsightsTracker**.</span><span class="sxs-lookup"><span data-stu-id="faced-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="faced-342">Clique duas vezes na nova **ApplicationInsightsTracker** script para abri-lo com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="faced-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="faced-343">Atualizar os namespaces na parte superior do script para ser conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="faced-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="faced-344">Dentro da classe, insira as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="faced-344">Inside the class insert the following variables:</span></span>

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
    > <span data-ttu-id="faced-345">Defina a **instrumentationKey, applicationId e API_Key** valores adequadamente, usando o *chaves de serviço* do Portal do Azure, conforme mencionado na [capítulo 1](#chapter-1---the-azure-portal), etapa 9 em diante.</span><span class="sxs-lookup"><span data-stu-id="faced-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="faced-346">Em seguida, adicione a **Start ()** e **Awake()** métodos, que serão chamados quando a classe é inicializado:</span><span class="sxs-lookup"><span data-stu-id="faced-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="faced-347">Adicione os métodos responsáveis por enviar os eventos e métricas registradas pelo seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="faced-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

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

8.  <span data-ttu-id="faced-348">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="faced-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="faced-349">Capítulo 7 - criar o script de olhar</span><span class="sxs-lookup"><span data-stu-id="faced-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="faced-350">É o próximo script para criar o **olhares** script.</span><span class="sxs-lookup"><span data-stu-id="faced-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="faced-351">Esse script é responsável por criar uma *Raycast* que será projetado para a frente do *câmera principal*, para detectar qual objeto de usuário está observando.</span><span class="sxs-lookup"><span data-stu-id="faced-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="faced-352">Nesse caso, o *Raycast* precisará identificar se o usuário está observando um objeto com o **ObjectInScene** marcar e, em seguida, contar quanto tempo o usuário *gazes* no objeto.</span><span class="sxs-lookup"><span data-stu-id="faced-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="faced-353">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="faced-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="faced-354">Clique com botão direito dentro de **Scripts** pasta, clique em **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="faced-354">Right-click inside the **Scripts** folder, click **Create** > **C\# Script**.</span></span> <span data-ttu-id="faced-355">Nomeie o script **olhares**.</span><span class="sxs-lookup"><span data-stu-id="faced-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="faced-356">Clique duas vezes no script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="faced-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="faced-357">Substitua o código existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="faced-357">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="faced-358">Código para o **Awake()** e **Start ()** métodos agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="faced-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

6.  <span data-ttu-id="faced-359">Dentro de **olhares** de classe, adicione o seguinte código na **Update ()** método ao projeto um *Raycast* e detectar a ocorrência de destino:</span><span class="sxs-lookup"><span data-stu-id="faced-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

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

7.  <span data-ttu-id="faced-360">Adicione a **ResetFocusedObject()** método para enviar dados a serem **Application Insights** quando o usuário já terá analisado em um objeto.</span><span class="sxs-lookup"><span data-stu-id="faced-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

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

8.  <span data-ttu-id="faced-361">Agora você concluiu a **olhares** script.</span><span class="sxs-lookup"><span data-stu-id="faced-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="faced-362">Salve suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="faced-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="faced-363">Capítulo 8 - criar a classe ObjectTrigger</span><span class="sxs-lookup"><span data-stu-id="faced-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="faced-364">É o próximo script, você precisa criar **ObjectTrigger**, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="faced-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="faced-365">Adicionando componentes necessários de colisão para a câmera principal.</span><span class="sxs-lookup"><span data-stu-id="faced-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="faced-366">Detectar se a câmera está perto de um objeto marcado como **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="faced-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="faced-367">Para criar o script:</span><span class="sxs-lookup"><span data-stu-id="faced-367">To create the script:</span></span>

1.  <span data-ttu-id="faced-368">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="faced-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="faced-369">Clique com botão direito dentro de **Scripts** pasta, clique em **Create** **C\# > Script**.</span><span class="sxs-lookup"><span data-stu-id="faced-369">Right-click inside the **Scripts** folder, click **Create** **C\# > Script**.</span></span> <span data-ttu-id="faced-370">Nomeie o script **ObjectTrigger**.</span><span class="sxs-lookup"><span data-stu-id="faced-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="faced-371">Clique duas vezes no script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="faced-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="faced-372">Substitua o código existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="faced-372">Replace the existing code with the following:</span></span>

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

4.  <span data-ttu-id="faced-373">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="faced-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="faced-374">Capítulo 9 - criar a classe DataFromAnalytics</span><span class="sxs-lookup"><span data-stu-id="faced-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="faced-375">Agora você precisará criar o **DataFromAnalytics** script, que é responsável por:</span><span class="sxs-lookup"><span data-stu-id="faced-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="faced-376">Buscando dados de análise sobre qual objeto foi abordou pela câmera mais.</span><span class="sxs-lookup"><span data-stu-id="faced-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="faced-377">Usando o *chaves de serviço*, que permitem a comunicação com a instância do serviço do Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="faced-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="faced-378">Classificando os objetos na cena, acordo com os quais tem a maior contagem de eventos.</span><span class="sxs-lookup"><span data-stu-id="faced-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="faced-379">Alterar a cor do material, do objeto mais approached, como *verde*.</span><span class="sxs-lookup"><span data-stu-id="faced-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="faced-380">Para criar o script:</span><span class="sxs-lookup"><span data-stu-id="faced-380">To create the script:</span></span>

1.  <span data-ttu-id="faced-381">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="faced-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="faced-382">Clique com botão direito dentro de **Scripts** pasta, clique em **Create** **C\# > Script**.</span><span class="sxs-lookup"><span data-stu-id="faced-382">Right-click inside the **Scripts** folder, click **Create** **C\# > Script**.</span></span> <span data-ttu-id="faced-383">Nomeie o script **DataFromAnalytics**.</span><span class="sxs-lookup"><span data-stu-id="faced-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="faced-384">Clique duas vezes no script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="faced-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="faced-385">Insira os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="faced-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="faced-386">Dentro do script, insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="faced-386">Inside the script, insert the following:</span></span>

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

6.  <span data-ttu-id="faced-387">Dentro de **DataFromAnalytics** classe, logo após o **Start ()** método, adicione o seguinte método chamado **FetchAnalytics()**.</span><span class="sxs-lookup"><span data-stu-id="faced-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="faced-388">Esse método é responsável por popular a lista de pares chave-valor, com um *GameObject* e um número de contagem de eventos do espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="faced-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="faced-389">Em seguida, ele inicializa o **GetWebRequest()** corrotina.</span><span class="sxs-lookup"><span data-stu-id="faced-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="faced-390">A estrutura de consulta da chamada para *Application Insights* pode ser encontrado dentro desse método Além disso, como o *URL de consulta* ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="faced-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

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

7.  <span data-ttu-id="faced-391">Logo abaixo do **FetchAnalytics()** método, adicione um método chamado **GetWebRequest()**, que retorna um *IEnumerator*.</span><span class="sxs-lookup"><span data-stu-id="faced-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="faced-392">Esse método é responsável por solicitar o número de vezes que um evento, correspondente a um determinado *GameObject*, foi chamado dentro *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="faced-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="faced-393">Quando todas as consultas enviadas tem retornado, o **DetermineWinner()** método é chamado.</span><span class="sxs-lookup"><span data-stu-id="faced-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
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

8.  <span data-ttu-id="faced-394">O próximo método é **DetermineWinner()**, que classifica a lista de *GameObject* e *Int* pares, de acordo com a maior contagem de eventos.</span><span class="sxs-lookup"><span data-stu-id="faced-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="faced-395">Ele então altera a cor do material do que *GameObject* à *verde* (como comentários para ter a maior contagem).</span><span class="sxs-lookup"><span data-stu-id="faced-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="faced-396">Isso exibe uma mensagem com os resultados da análise.</span><span class="sxs-lookup"><span data-stu-id="faced-396">This displays a message with the analytics results.</span></span>

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

9.  <span data-ttu-id="faced-397">Adicionar a estrutura de classe que será usada para desserializar o objeto JSON, proveniente *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="faced-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="faced-398">Adicione essas classes na parte inferior de seu **DataFromAnalytics** arquivo de classe **fora** da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="faced-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

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

10. <span data-ttu-id="faced-399">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="faced-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="faced-400">Capítulo 10 - criar a classe de movimentação</span><span class="sxs-lookup"><span data-stu-id="faced-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="faced-401">O **movimentação** script é o próximo script, você precisará criar.</span><span class="sxs-lookup"><span data-stu-id="faced-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="faced-402">Ele é responsável por:</span><span class="sxs-lookup"><span data-stu-id="faced-402">It is responsible for:</span></span>

- <span data-ttu-id="faced-403">Mover a câmera principal de acordo com a direção da câmera está apontando na direção.</span><span class="sxs-lookup"><span data-stu-id="faced-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="faced-404">Adicionando todos os outros scripts para objetos da cena.</span><span class="sxs-lookup"><span data-stu-id="faced-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="faced-405">Para criar o script:</span><span class="sxs-lookup"><span data-stu-id="faced-405">To create the script:</span></span>

1.  <span data-ttu-id="faced-406">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="faced-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="faced-407">Clique com botão direito dentro de **Scripts** pasta, clique em **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="faced-407">Right-click inside the **Scripts** folder, click **Create** > **C\# Script**.</span></span> <span data-ttu-id="faced-408">Nomeie o script **movimentação**.</span><span class="sxs-lookup"><span data-stu-id="faced-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="faced-409">Clique duas vezes em que o script para abri-lo com *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="faced-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="faced-410">Substitua o código existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="faced-410">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="faced-411">Dentro de **movimentação** classe, *abaixo* vazio **Update ()** método, insira os seguintes métodos que permitem ao usuário usar o controlador de mão para mover-se no espaço virtual:</span><span class="sxs-lookup"><span data-stu-id="faced-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

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

6.  <span data-ttu-id="faced-412">Por fim, adicione a chamada de método dentro de **Update ()** método.</span><span class="sxs-lookup"><span data-stu-id="faced-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="faced-413">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="faced-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="faced-414">Capítulo 11 - Configurando as referências de scripts</span><span class="sxs-lookup"><span data-stu-id="faced-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="faced-415">Neste capítulo, você precisa colocar o **movimentação** de script para o **câmera pai** e defina seus destinos de referência.</span><span class="sxs-lookup"><span data-stu-id="faced-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="faced-416">Esse script tratará a colocar outros scripts onde elas precisam ser.</span><span class="sxs-lookup"><span data-stu-id="faced-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="faced-417">Do **Scripts** pasta na *painel projeto*, arraste o **movimentação** gerar um script para o **câmera pai** objeto localizado no  *Painel de hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="faced-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Configurando as referências de scripts na cena Unity](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="faced-419">Clique no **pai da câmera**.</span><span class="sxs-lookup"><span data-stu-id="faced-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="faced-420">No *painel de hierarquia*, arraste o **mão direita** do objeto do *painel da hierarquia* para o destino de referência, **controlador**, no *Painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="faced-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="faced-421">Defina as **usuário velocidade** para **5**, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="faced-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Configurando as referências de scripts na cena Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="faced-423">Capítulo 12 - compilar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="faced-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="faced-424">Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído, portanto, é hora de criá-lo do Unity.</span><span class="sxs-lookup"><span data-stu-id="faced-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="faced-425">Navegue até **configurações de Build**, **(arquivo > configurações de Build...)** .</span><span class="sxs-lookup"><span data-stu-id="faced-425">Navigate to **Build Settings**, **(File > Build Settings...)**.</span></span>

2.  <span data-ttu-id="faced-426">Dos **configurações de Build** janela, clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="faced-426">From the **Build Settings** window, click **Build**.</span></span>

    ![Compile o projeto do Unity para solução UWP](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="faced-428">Um **Explorador de arquivos** janela será pop-up, que pedirá um local para a compilação.</span><span class="sxs-lookup"><span data-stu-id="faced-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="faced-429">Crie uma nova pasta (clicando **nova pasta** no canto superior esquerdo) e nomeie-o **compilações**.</span><span class="sxs-lookup"><span data-stu-id="faced-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Compile o projeto do Unity para solução UWP](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="faced-431">Abra o novo **compilações** pasta e criar outra pasta (usando **nova pasta** mais uma vez) e nomeie- **MR\_Azure\_aplicativo\_ Insights**.</span><span class="sxs-lookup"><span data-stu-id="faced-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![Compile o projeto do Unity para solução UWP](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="faced-433">Com o **MR\_Azure\_Application\_Insights** pasta selecionada, clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="faced-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="faced-434">O projeto será levar um minuto ou mais para compilar.</span><span class="sxs-lookup"><span data-stu-id="faced-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="faced-435">A seguir *construir*, **Explorador de arquivos** será exibida mostrando o local do novo projeto.</span><span class="sxs-lookup"><span data-stu-id="faced-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a><span data-ttu-id="faced-436">Capítulo 13 - implantar aplicativo MR_Azure_Application_Insights em seu computador</span><span class="sxs-lookup"><span data-stu-id="faced-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="faced-437">Para implantar o **MR\_Azure\_Application\_Insights** aplicativo em seu computador Local:</span><span class="sxs-lookup"><span data-stu-id="faced-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="faced-438">Abra o arquivo de solução do seu **MR\_Azure\_Application\_Insights** aplicativo no **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="faced-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="faced-439">No **plataforma da solução**, selecione **x86, computador Local**.</span><span class="sxs-lookup"><span data-stu-id="faced-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="faced-440">No **configuração da solução** selecionar **depurar**.</span><span class="sxs-lookup"><span data-stu-id="faced-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![Compile o projeto do Unity para solução UWP](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="faced-442">Vá para **menu Build** e clique em **implantar solução** para carregar o aplicativo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="faced-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="faced-443">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="faced-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="faced-444">Inicie o aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="faced-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="faced-445">Mova a cena se aproximando objetos e examiná-los, quando o *o serviço do Azure Insight* coletou dados suficientes evento, ele definirá o objeto que abordou mais importantes para verde.</span><span class="sxs-lookup"><span data-stu-id="faced-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="faced-446">Durante o tempo de espera médio para o *métricas e eventos* sejam coletados pelo serviço leva cerca de 15 minutos, em algumas ocasiões ele pode levar até 1 hora.</span><span class="sxs-lookup"><span data-stu-id="faced-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="faced-447">Capítulo 14 - portal do serviço Application Insights</span><span class="sxs-lookup"><span data-stu-id="faced-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="faced-448">Depois que você tenha de roaming em torno da cena e gazed em vários objetos você pode ver os dados coletados na *serviço Application Insights* portal.</span><span class="sxs-lookup"><span data-stu-id="faced-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="faced-449">Volte para seu portal do serviço Application Insights.</span><span class="sxs-lookup"><span data-stu-id="faced-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="faced-450">Clique em *Metrics Explorer*.</span><span class="sxs-lookup"><span data-stu-id="faced-450">Click on *Metrics Explorer*.</span></span>

    ![Observando os dados coletados](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="faced-452">Ele será aberto em uma guia que contém o gráfico que representam o *métricas e eventos* relacionados ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="faced-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="faced-453">Conforme mencionado acima, pode levar algum tempo (até 1 hora) para os dados a serem exibidos no gráfico</span><span class="sxs-lookup"><span data-stu-id="faced-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![Observando os dados coletados](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="faced-455">Clique no *barra de eventos* na *Total de eventos* pela versão do aplicativo, para ver uma análise detalhada dos eventos com seus nomes.</span><span class="sxs-lookup"><span data-stu-id="faced-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![Observando os dados coletados](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="faced-457">A conclusão de seu aplicativo de serviço Application Insights</span><span class="sxs-lookup"><span data-stu-id="faced-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="faced-458">Parabéns, você criou um aplicativo de realidade mista que aproveita o serviço Application Insights para monitorar a atividade do usuário dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="faced-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![resultado do curso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="faced-460">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="faced-460">Bonus Exercises</span></span>

<span data-ttu-id="faced-461">**Exercício 1**</span><span class="sxs-lookup"><span data-stu-id="faced-461">**Exercise 1**</span></span>

<span data-ttu-id="faced-462">Tente reproduzir, em vez de criar manualmente, os objetos ObjectInScene e definir suas coordenadas no plano dentro de seus scripts.</span><span class="sxs-lookup"><span data-stu-id="faced-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="faced-463">Dessa forma, você pode pedir ao Azure foi de que o objeto mais popular (qualquer um dos resultados de olhar ou proximidade) e geração de um *extra* um desses objetos.</span><span class="sxs-lookup"><span data-stu-id="faced-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="faced-464">**Exercício 2**</span><span class="sxs-lookup"><span data-stu-id="faced-464">**Exercise 2**</span></span>

<span data-ttu-id="faced-465">Classifique os resultados de Application Insights por vez, para que você obtenha os dados mais relevantes e implementa esses dados confidenciais de tempo em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="faced-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

