---
title: MR e Azure 301 - conversão de linguagem
description: Conclua este curso para saber como implementar a API de texto de tradução do Azure dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, tradução de texto, hololens, imersivo, vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590691"
---
>[!NOTE]
><span data-ttu-id="945cf-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="945cf-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="945cf-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="945cf-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="945cf-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="945cf-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="945cf-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="945cf-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="945cf-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="945cf-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="945cf-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="945cf-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="945cf-110">MR e o Azure 301: Tradução de idioma</span><span class="sxs-lookup"><span data-stu-id="945cf-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="945cf-111">Neste curso, você aprenderá como adicionar funcionalidades de tradução para um aplicativo de realidade misturada usando serviços Cognitivos do Azure, com a API de tradução de texto.</span><span class="sxs-lookup"><span data-stu-id="945cf-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![Final do produto](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="945cf-113">A API de tradução de texto é uma serviço que funciona em tempo quase real de conversão.</span><span class="sxs-lookup"><span data-stu-id="945cf-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="945cf-114">O serviço é baseado em nuvem e, usando uma chamada à API REST, um aplicativo pode fazer uso da tecnologia de tradução automática neural para traduzir o texto em outra linguagem.</span><span class="sxs-lookup"><span data-stu-id="945cf-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="945cf-115">Para obter mais informações, visite o [página do Azure API de tradução de texto](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span><span class="sxs-lookup"><span data-stu-id="945cf-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="945cf-116">Após a conclusão deste curso, você terá um aplicativo de realidade mista que serão capaz de fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="945cf-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="945cf-117">O usuário irá falar em um microfone conectado a um fone de ouvido imersivo (VR) (ou o microfone interno do HoloLens).</span><span class="sxs-lookup"><span data-stu-id="945cf-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="945cf-118">O aplicativo irá capturar o ditado e enviá-lo para a API de texto de tradução do Azure.</span><span class="sxs-lookup"><span data-stu-id="945cf-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="945cf-119">O resultado da conversão será exibido em um grupo de interface do usuário simple na cena Unity.</span><span class="sxs-lookup"><span data-stu-id="945cf-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="945cf-120">Este curso ensinará você a obter os resultados do serviço Translator em um aplicativo de exemplo com base no Unity.</span><span class="sxs-lookup"><span data-stu-id="945cf-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="945cf-121">Ele será cabe a você aplicar esses conceitos para um aplicativo personalizado que você pode criar.</span><span class="sxs-lookup"><span data-stu-id="945cf-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="945cf-122">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="945cf-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="945cf-123">Curso</span><span class="sxs-lookup"><span data-stu-id="945cf-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="945cf-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="945cf-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="945cf-125"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="945cf-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="945cf-126">MR e o Azure 301: Tradução de idioma</span><span class="sxs-lookup"><span data-stu-id="945cf-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="945cf-127">✔️</span><span class="sxs-lookup"><span data-stu-id="945cf-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="945cf-128">✔️</span><span class="sxs-lookup"><span data-stu-id="945cf-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="945cf-129">Enquanto este curso se concentra primariamente em fones de ouvido Windows Mixed Reality de imersão (VR), você também pode aplicar o que você aprenderá neste curso para o Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="945cf-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="945cf-130">Como acompanhar o curso, você verá notas quaisquer alterações que talvez seja necessário empregar para dar suporte ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="945cf-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="945cf-131">Ao usar o HoloLens, você pode perceber algum eco durante a captura de voz.</span><span class="sxs-lookup"><span data-stu-id="945cf-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="945cf-132">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="945cf-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="945cf-133">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="945cf-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="945cf-134">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="945cf-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="945cf-135">Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .</span><span class="sxs-lookup"><span data-stu-id="945cf-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="945cf-136">Recomendamos que o hardware e software para este curso a seguir:</span><span class="sxs-lookup"><span data-stu-id="945cf-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="945cf-137">Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)</span><span class="sxs-lookup"><span data-stu-id="945cf-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="945cf-138">Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="945cf-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="945cf-139">O SDK mais recente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="945cf-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="945cf-140">2017.4 do Unity</span><span class="sxs-lookup"><span data-stu-id="945cf-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="945cf-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="945cf-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="945cf-142">Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="945cf-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="945cf-143">Um conjunto de fones de ouvido com um microfone interno (se o fone de ouvido não tiver um mic internos e alto-falantes)</span><span class="sxs-lookup"><span data-stu-id="945cf-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="945cf-144">Acesso à Internet para a recuperação do Azure de instalação e translation</span><span class="sxs-lookup"><span data-stu-id="945cf-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="945cf-145">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="945cf-145">Before you start</span></span>

- <span data-ttu-id="945cf-146">Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="945cf-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="945cf-147">O código neste tutorial permitirá que você grave do microfone padrão dispositivo conectado ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="945cf-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="945cf-148">Verifique se que o dispositivo de microfone padrão está definido para o dispositivo que você planeja usar para capturar sua voz.</span><span class="sxs-lookup"><span data-stu-id="945cf-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="945cf-149">Para permitir que seu computador habilitar o ditado, vá para **Configurações > privacidade > fala, escrita à tinta e digitando** e selecione o botão **ativar serviços de fala e sugestões de digitação**.</span><span class="sxs-lookup"><span data-stu-id="945cf-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="945cf-150">Se você estiver usando um microfone e fones de ouvido (ou internos) fone de ouvido, verifique se a opção "Quando eu wear meu fone de ouvido, alternar para o fone de ouvido mic" está ativado no **Configurações > realidade misturada > áudio e fala**.</span><span class="sxs-lookup"><span data-stu-id="945cf-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![Configurações de realidade misturada](images/AzureLabs-Lab1-00-5.png)

   ![Configuração do microfone](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="945cf-153">Lembre-se de que, se você estiver desenvolvendo para um fone de ouvido envolvente para este laboratório, você poderá enfrentar problemas de dispositivo de saída de áudio.</span><span class="sxs-lookup"><span data-stu-id="945cf-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="945cf-154">Isso é devido a um problema com o Unity, que é fixo em versões posteriores do Unity (Unity 2018.2).</span><span class="sxs-lookup"><span data-stu-id="945cf-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="945cf-155">O problema impede que o Unity altere o dispositivo de saída de áudio padrão em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="945cf-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="945cf-156">Como uma solução alternativa, verifique se que você concluiu as etapas acima e feche e reabra o Editor, quando esse problema se apresenta.</span><span class="sxs-lookup"><span data-stu-id="945cf-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="945cf-157">Capítulo 1 – Portal do Azure</span><span class="sxs-lookup"><span data-stu-id="945cf-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="945cf-158">Para usar a API de tradução do Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="945cf-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="945cf-159">Faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="945cf-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="945cf-160">Se você ainda não tiver uma conta do Azure, você precisará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="945cf-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="945cf-161">Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="945cf-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="945cf-162">Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure "Tradução de texto API".</span><span class="sxs-lookup"><span data-stu-id="945cf-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="945cf-163">Selecione **insira**.</span><span class="sxs-lookup"><span data-stu-id="945cf-163">Select **Enter**.</span></span>

    ![Novo recurso](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="945cf-165">A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="945cf-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="945cf-166">A nova página fornecerá uma descrição do *API de tradução de texto* Service.</span><span class="sxs-lookup"><span data-stu-id="945cf-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="945cf-167">Na parte inferior esquerda desta página, selecione a **criar** botão para criar uma associação com este serviço.</span><span class="sxs-lookup"><span data-stu-id="945cf-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Criar serviço de API do Translator texto](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="945cf-169">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="945cf-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="945cf-170">Inserir sua desejada **nome** para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="945cf-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="945cf-171">Selecione uma opção apropriada **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="945cf-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="945cf-172">Selecione o **tipo de preço** apropriado para você, se esse for o primeiro tempo para criar um *serviço de tradução de texto*, uma camada gratuita (chamada F0) deve estar disponível para você.</span><span class="sxs-lookup"><span data-stu-id="945cf-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="945cf-173">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="945cf-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="945cf-174">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="945cf-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="945cf-175">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="945cf-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="945cf-176">Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="945cf-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="945cf-177">Determinar a **local** para seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="945cf-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="945cf-178">O local seria o ideal é que na região em que o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="945cf-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="945cf-179">Alguns ativos do Azure estão disponíveis somente em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="945cf-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="945cf-180">Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="945cf-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="945cf-181">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="945cf-181">Select **Create**.</span></span>

        ![Selecione o botão Criar.](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="945cf-183">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="945cf-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="945cf-184">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="945cf-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Notificação de criação de serviço do Azure](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="945cf-186">Clique na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="945cf-186">Click on the notification to explore your new Service instance.</span></span> 

    ![Vá para a janela pop-up de recurso.](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="945cf-188">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="945cf-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="945cf-189">Você será levado à instância do serviço de API do Translator texto novo.</span><span class="sxs-lookup"><span data-stu-id="945cf-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Página de serviço de API de texto do tradutor](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="945cf-191">Dentro deste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, que é feito por meio do uso de chave de assinatura do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="945cf-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="945cf-192">Dos *início rápido* página do seu *tradução de texto* Service, navegue até a primeira etapa, *pegue suas chaves*e clique em **chaves** (você pode também fazer isso clicando no hiperlink azul chaves, localizado no menu de navegação de serviços, indicado pelo ícone de chave).</span><span class="sxs-lookup"><span data-stu-id="945cf-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="945cf-193">Isso irá revelar o seu serviço *chaves*.</span><span class="sxs-lookup"><span data-stu-id="945cf-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="945cf-194">Faça uma cópia de uma das chaves exibidas, pois precisará dele posteriormente em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="945cf-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="945cf-195">Capítulo 2 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="945cf-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="945cf-196">Configurar e testar o headset de realidade misturada envolvente.</span><span class="sxs-lookup"><span data-stu-id="945cf-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="945cf-197">Você não precisará controladores de movimento para este curso.</span><span class="sxs-lookup"><span data-stu-id="945cf-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="945cf-198">Se você precisar dar suporte a configurar um fone de ouvido imersivo, faça [siga estas etapas](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="945cf-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="945cf-199">A seguir é um conjunto típico backup para o desenvolvimento de realidade mista e, dessa forma, é um bom modelo para outros projetos:</span><span class="sxs-lookup"><span data-stu-id="945cf-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="945cf-200">Abra *Unity* e clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="945cf-200">Open *Unity* and click **New**.</span></span> 

    ![Inicie um novo projeto do Unity.](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="945cf-202">Agora, você precisará fornecer um nome de projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="945cf-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="945cf-203">Inserir **MR_Translation**.</span><span class="sxs-lookup"><span data-stu-id="945cf-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="945cf-204">Verifique se o tipo de projeto é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="945cf-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="945cf-205">Defina as *local* para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="945cf-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="945cf-206">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="945cf-206">Then, click **Create project**.</span></span>

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="945cf-208">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="945cf-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="945cf-209">Vá para **Editar > Preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="945cf-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="945cf-210">Alteração **Editor de Script externo** à **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="945cf-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="945cf-211">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="945cf-211">Close the **Preferences** window.</span></span>

    ![Atualize as preferências do editor de script.](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="945cf-213">Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma **plataforma Universal do Windows**, clicando no **alternar plataforma** botão.</span><span class="sxs-lookup"><span data-stu-id="945cf-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Crie janela de configurações, alternar a plataforma para a UWP.](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="945cf-215">Vá para **arquivo > configurações de Build** e certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="945cf-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="945cf-216">**Dispositivo de destino** é definido como **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="945cf-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="945cf-217">Para o Microsoft HoloLens, defina **dispositivo de destino** à *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="945cf-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="945cf-218">**Tipo de compilação** é definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="945cf-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="945cf-219">**SDK** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="945cf-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="945cf-220">**Versão do Visual Studio** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="945cf-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="945cf-221">**Compilar e executar** é definido como **Máquina Local**</span><span class="sxs-lookup"><span data-stu-id="945cf-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="945cf-222">Salve a cena e adicioná-lo para a compilação.</span><span class="sxs-lookup"><span data-stu-id="945cf-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="945cf-223">Fazer isso selecionando **cenas abra Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="945cf-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="945cf-224">Salvamento janela será exibida.</span><span class="sxs-lookup"><span data-stu-id="945cf-224">A save window will appear.</span></span>

            ![Clique em Adicionar botão cenas aberto](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="945cf-226">Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.</span><span class="sxs-lookup"><span data-stu-id="945cf-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Criar nova pasta de scripts](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="945cf-228">Abra seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo*: campo de texto, digite **MR_TranslationScene**, em seguida, pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="945cf-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![Dê um nome de nova cena.](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="945cf-230">Esteja ciente de que você deve salvar suas cenas de Unity dentro do *ativos* pasta, pois eles devem estar associados ao projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="945cf-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="945cf-231">Criando a pasta de cenas (e outras pastas semelhantes) é uma maneira comum de estruturar um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="945cf-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="945cf-232">O restante de configurações, em *configurações de Build*, deverá ser deixado como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="945cf-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="945cf-233">No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="945cf-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra configurações do player.](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="945cf-235">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="945cf-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="945cf-236">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="945cf-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="945cf-237">**Versão de tempo de execução de scripts** deve ser **estável** (.NET 3.5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="945cf-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="945cf-238">**Script de back-end** deve ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="945cf-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="945cf-239">**Nível de compatibilidade de API** deve ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="945cf-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Outras configurações de atualização.](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="945cf-241">Dentro de **configurações de publicação** guia, em **recursos**, verifique:</span><span class="sxs-lookup"><span data-stu-id="945cf-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="945cf-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="945cf-242">**InternetClient**</span></span>
        2. <span data-ttu-id="945cf-243">**Microfone**</span><span class="sxs-lookup"><span data-stu-id="945cf-243">**Microphone**</span></span>

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="945cf-245">Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.</span><span class="sxs-lookup"><span data-stu-id="945cf-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Atualize as configurações de R de X.](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="945cf-247">Volta **configurações de Build**, *Unity C# projetos* não fica acinzentado; marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="945cf-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="945cf-248">Feche a janela de configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="945cf-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="945cf-249">Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="945cf-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="945cf-250">Capítulo 3 – instalação de câmera principal</span><span class="sxs-lookup"><span data-stu-id="945cf-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="945cf-251">Se você quiser ignorar a *configurar o Unity* componente deste curso e continuar diretamente no código, fique à vontade para [baixar esse unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), importá-lo para seu projeto como um [ *Pacote personalizado*](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 5](#chapter-5--create-the-results-class).</span><span class="sxs-lookup"><span data-stu-id="945cf-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="945cf-252">Você ainda precisará criar um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="945cf-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="945cf-253">No *painel de hierarquia*, você encontrará um objeto chamado **câmera principal**, este objeto representa o ponto de vista de "head" quando estiver "dentro" de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="945cf-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="945cf-254">Com o painel do Unity na sua frente, selecione a **GameObject de câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="945cf-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="945cf-255">Você observará que o *painel Inspetor* (geralmente encontrado para a direita, no painel) mostrará os vários componentes do que *GameObject*, com *transformar* na parte superior, seguido por *câmera*e alguns outros componentes.</span><span class="sxs-lookup"><span data-stu-id="945cf-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="945cf-256">Você precisará redefinir a transformação da câmera principal, para que ele está posicionado corretamente.</span><span class="sxs-lookup"><span data-stu-id="945cf-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="945cf-257">Para fazer isso, selecione a **engrenagem** ícone ao lado da câmera *transformar* componente e selecionando **redefinir**.</span><span class="sxs-lookup"><span data-stu-id="945cf-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![Redefina a transformação de câmera principal.](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="945cf-259">O *transformar* componente, em seguida, deve se parecer com:</span><span class="sxs-lookup"><span data-stu-id="945cf-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="945cf-260">O *posição* é definido como **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="945cf-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="945cf-261">*Rotação* é definido como **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="945cf-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="945cf-262">E *dimensionamento* é definido como **1, 1, 1**</span><span class="sxs-lookup"><span data-stu-id="945cf-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![Transformar informações de câmera](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="945cf-264">Em seguida, com o **câmera principal** objeto selecionado, consulte o **Add Component** botão localizado na parte inferior do *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="945cf-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="945cf-265">Selecione esse botão e de pesquisa (digitando *Audio Source* no campo de pesquisa ou navegação as seções) para o componente chamado **Audio Source** conforme mostrado abaixo e selecioná-lo (pressionando enter nele também funciona).</span><span class="sxs-lookup"><span data-stu-id="945cf-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="945cf-266">Uma *Audio Source* componente será adicionado para o **câmera principal**, conforme demonstrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="945cf-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![Adicione um componente de Audio Source.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="945cf-268">Para o Microsoft HoloLens, você precisará alterar também o seguinte, que fazem parte dos **câmera** componente no seu **câmera principal**:</span><span class="sxs-lookup"><span data-stu-id="945cf-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="945cf-269">**Limpe os sinalizadores de:** Cor sólida.</span><span class="sxs-lookup"><span data-stu-id="945cf-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="945cf-270">**Plano de fundo** ' preto, alfa 0' – cor hexadecimal: 00000000 #.</span><span class="sxs-lookup"><span data-stu-id="945cf-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="945cf-271">Capítulo 4-tela de depuração do programa de instalação</span><span class="sxs-lookup"><span data-stu-id="945cf-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="945cf-272">Para mostrar a entrada e saída da tradução, uma interface do usuário básica precisa ser criado.</span><span class="sxs-lookup"><span data-stu-id="945cf-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="945cf-273">Para este curso, você criará um objeto de tela da interface do usuário, com vários objetos de 'Text' para mostrar os dados.</span><span class="sxs-lookup"><span data-stu-id="945cf-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="945cf-274">Com o botão direito em uma área vazia do *painel de hierarquia*, em **UI**, adicionar um **tela**.</span><span class="sxs-lookup"><span data-stu-id="945cf-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![Adicione um novo objeto de tela da interface do usuário.](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="945cf-276">Com o objeto de tela selecionado, o *painel Inspetor* (dentro do componente 'Tela'), altere **modo de renderização** para **espaço de mundo**.</span><span class="sxs-lookup"><span data-stu-id="945cf-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="945cf-277">Em seguida, alterar os seguintes parâmetros na *Rect transformação do painel do Inspetor*:</span><span class="sxs-lookup"><span data-stu-id="945cf-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="945cf-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="945cf-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="945cf-279">*Largura* - 500</span><span class="sxs-lookup"><span data-stu-id="945cf-279">*Width* -    500</span></span>
    3. <span data-ttu-id="945cf-280">*Height* -   300</span><span class="sxs-lookup"><span data-stu-id="945cf-280">*Height* -   300</span></span>
    4. <span data-ttu-id="945cf-281">*Escala* - **X** 0.13 **Y** 0.13 **Z** 0.13</span><span class="sxs-lookup"><span data-stu-id="945cf-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![Atualize a transformação rect para a tela.](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="945cf-283">Clique com botão direito no **Canvas** na *painel de hierarquia*, em **interface do usuário**e adicione um **painel**.</span><span class="sxs-lookup"><span data-stu-id="945cf-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="945cf-284">Isso **painel** fornecerá um plano de fundo para o texto que você deseja exibir na cena.</span><span class="sxs-lookup"><span data-stu-id="945cf-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="945cf-285">Clique com botão direito no **painel** na *painel de hierarquia*, em **interface do usuário**e adicione um **objeto de texto**.</span><span class="sxs-lookup"><span data-stu-id="945cf-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="945cf-286">Repita o mesmo processo até que você criou quatro objetos de texto de interface do usuário no total (Dica: se você tiver o primeiro objeto de 'Text' selecionado, você pode simplesmente pressionar **'Ctrl' + tinha '**, duplicar, até que você tenha quatro no total).</span><span class="sxs-lookup"><span data-stu-id="945cf-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="945cf-287">Para cada **objeto de texto**, selecioná-lo e usar as tabelas para definir os parâmetros no abaixo a *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="945cf-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="945cf-288">Para o *Rect transformação* componente:</span><span class="sxs-lookup"><span data-stu-id="945cf-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="945cf-289">Nome</span><span class="sxs-lookup"><span data-stu-id="945cf-289">Name</span></span>                   | <span data-ttu-id="945cf-290">Transformar - *posição*</span><span class="sxs-lookup"><span data-stu-id="945cf-290">Transform - *Position*</span></span>             | <span data-ttu-id="945cf-291">Largura</span><span class="sxs-lookup"><span data-stu-id="945cf-291">Width</span></span>      | <span data-ttu-id="945cf-292">Height</span><span class="sxs-lookup"><span data-stu-id="945cf-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="945cf-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="945cf-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="945cf-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="945cf-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="945cf-295">300</span><span class="sxs-lookup"><span data-stu-id="945cf-295">300</span></span>        | <span data-ttu-id="945cf-296">30</span><span class="sxs-lookup"><span data-stu-id="945cf-296">30</span></span>        |
        | <span data-ttu-id="945cf-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="945cf-297">AzureResponseLabel</span></span>     | <span data-ttu-id="945cf-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="945cf-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="945cf-299">300</span><span class="sxs-lookup"><span data-stu-id="945cf-299">300</span></span>        | <span data-ttu-id="945cf-300">30</span><span class="sxs-lookup"><span data-stu-id="945cf-300">30</span></span>        |
        | <span data-ttu-id="945cf-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="945cf-301">DictationLabel</span></span>         | <span data-ttu-id="945cf-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="945cf-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="945cf-303">300</span><span class="sxs-lookup"><span data-stu-id="945cf-303">300</span></span>        | <span data-ttu-id="945cf-304">30</span><span class="sxs-lookup"><span data-stu-id="945cf-304">30</span></span>        |
        | <span data-ttu-id="945cf-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="945cf-305">TranslationResultLabel</span></span> | <span data-ttu-id="945cf-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="945cf-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="945cf-307">300</span><span class="sxs-lookup"><span data-stu-id="945cf-307">300</span></span>        | <span data-ttu-id="945cf-308">30</span><span class="sxs-lookup"><span data-stu-id="945cf-308">30</span></span>        |


    2. <span data-ttu-id="945cf-309">Para o **texto (Script)** componente:</span><span class="sxs-lookup"><span data-stu-id="945cf-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="945cf-310">Nome</span><span class="sxs-lookup"><span data-stu-id="945cf-310">Name</span></span>                   | <span data-ttu-id="945cf-311">Texto</span><span class="sxs-lookup"><span data-stu-id="945cf-311">Text</span></span>               | <span data-ttu-id="945cf-312">Tamanho da fonte</span><span class="sxs-lookup"><span data-stu-id="945cf-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="945cf-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="945cf-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="945cf-314">Status de microfone:</span><span class="sxs-lookup"><span data-stu-id="945cf-314">Microphone Status:</span></span> | <span data-ttu-id="945cf-315">20</span><span class="sxs-lookup"><span data-stu-id="945cf-315">20</span></span>           |
        | <span data-ttu-id="945cf-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="945cf-316">AzureResponseLabel</span></span>     | <span data-ttu-id="945cf-317">Azure Web Response</span><span class="sxs-lookup"><span data-stu-id="945cf-317">Azure Web Response</span></span> | <span data-ttu-id="945cf-318">20</span><span class="sxs-lookup"><span data-stu-id="945cf-318">20</span></span>           |
        | <span data-ttu-id="945cf-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="945cf-319">DictationLabel</span></span>         |   <span data-ttu-id="945cf-320">Você disse:</span><span class="sxs-lookup"><span data-stu-id="945cf-320">You just said:</span></span>   | <span data-ttu-id="945cf-321">20</span><span class="sxs-lookup"><span data-stu-id="945cf-321">20</span></span>           |
        | <span data-ttu-id="945cf-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="945cf-322">TranslationResultLabel</span></span> |    <span data-ttu-id="945cf-323">Tradução:</span><span class="sxs-lookup"><span data-stu-id="945cf-323">Translation:</span></span>    | <span data-ttu-id="945cf-324">20</span><span class="sxs-lookup"><span data-stu-id="945cf-324">20</span></span>           |

        ![Os valores correspondentes para os rótulos da interface do usuário de entrada.](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="945cf-326">Além disso, verifique o estilo da fonte **negrito**.</span><span class="sxs-lookup"><span data-stu-id="945cf-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="945cf-327">Isso tornará o texto mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="945cf-327">This will make the text easier to read.</span></span>

        ![Fonte em negrito.](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="945cf-329">Para cada *objeto de texto de interface do usuário* criado na [capítulo 5](#chapter-5--create-the-results-class), crie um novo *filho* **objeto de texto de interface do usuário**.</span><span class="sxs-lookup"><span data-stu-id="945cf-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="945cf-330">Esses filhos exibirá a saída do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="945cf-330">These children will display the output of the application.</span></span> <span data-ttu-id="945cf-331">Crie *filho* objetos por meio de seu pai pretendido botão direito do mouse (por exemplo, *MicrophoneStatusLabel*) e, em seguida, selecione **interface de usuário** e, em seguida, selecione **texto**.</span><span class="sxs-lookup"><span data-stu-id="945cf-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="945cf-332">Para cada um desses filhos, selecione-o e use as tabelas para definir os parâmetros no painel Inspetor abaixo.</span><span class="sxs-lookup"><span data-stu-id="945cf-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="945cf-333">Para o **Rect transformação** componente:</span><span class="sxs-lookup"><span data-stu-id="945cf-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="945cf-334">Nome</span><span class="sxs-lookup"><span data-stu-id="945cf-334">Name</span></span>                  | <span data-ttu-id="945cf-335">Transformar - *posição*</span><span class="sxs-lookup"><span data-stu-id="945cf-335">Transform - *Position*</span></span> | <span data-ttu-id="945cf-336">Largura</span><span class="sxs-lookup"><span data-stu-id="945cf-336">Width</span></span>      | <span data-ttu-id="945cf-337">Height</span><span class="sxs-lookup"><span data-stu-id="945cf-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="945cf-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="945cf-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="945cf-339">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="945cf-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="945cf-340">300</span><span class="sxs-lookup"><span data-stu-id="945cf-340">300</span></span>        | <span data-ttu-id="945cf-341">30</span><span class="sxs-lookup"><span data-stu-id="945cf-341">30</span></span>        |
        | <span data-ttu-id="945cf-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="945cf-342">AzureResponseText</span></span>     | <span data-ttu-id="945cf-343">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="945cf-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="945cf-344">300</span><span class="sxs-lookup"><span data-stu-id="945cf-344">300</span></span>        | <span data-ttu-id="945cf-345">30</span><span class="sxs-lookup"><span data-stu-id="945cf-345">30</span></span>        |
        | <span data-ttu-id="945cf-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="945cf-346">DictationText</span></span>         | <span data-ttu-id="945cf-347">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="945cf-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="945cf-348">300</span><span class="sxs-lookup"><span data-stu-id="945cf-348">300</span></span>        | <span data-ttu-id="945cf-349">30</span><span class="sxs-lookup"><span data-stu-id="945cf-349">30</span></span>        |
        | <span data-ttu-id="945cf-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="945cf-350">TranslationResultText</span></span> | <span data-ttu-id="945cf-351">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="945cf-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="945cf-352">300</span><span class="sxs-lookup"><span data-stu-id="945cf-352">300</span></span>        | <span data-ttu-id="945cf-353">30</span><span class="sxs-lookup"><span data-stu-id="945cf-353">30</span></span>        |

    2. <span data-ttu-id="945cf-354">Para o **texto (Script)** componente:</span><span class="sxs-lookup"><span data-stu-id="945cf-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="945cf-355">Nome</span><span class="sxs-lookup"><span data-stu-id="945cf-355">Name</span></span>                  | <span data-ttu-id="945cf-356">Texto</span><span class="sxs-lookup"><span data-stu-id="945cf-356">Text</span></span>          | <span data-ttu-id="945cf-357">Tamanho da fonte</span><span class="sxs-lookup"><span data-stu-id="945cf-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="945cf-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="945cf-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="945cf-359">??</span><span class="sxs-lookup"><span data-stu-id="945cf-359">??</span></span>       | <span data-ttu-id="945cf-360">20</span><span class="sxs-lookup"><span data-stu-id="945cf-360">20</span></span>           |
        | <span data-ttu-id="945cf-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="945cf-361">AzureResponseText</span></span>     |      <span data-ttu-id="945cf-362">??</span><span class="sxs-lookup"><span data-stu-id="945cf-362">??</span></span>       | <span data-ttu-id="945cf-363">20</span><span class="sxs-lookup"><span data-stu-id="945cf-363">20</span></span>           |
        | <span data-ttu-id="945cf-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="945cf-364">DictationText</span></span>         |      <span data-ttu-id="945cf-365">??</span><span class="sxs-lookup"><span data-stu-id="945cf-365">??</span></span>       | <span data-ttu-id="945cf-366">20</span><span class="sxs-lookup"><span data-stu-id="945cf-366">20</span></span>           |
        | <span data-ttu-id="945cf-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="945cf-367">TranslationResultText</span></span> |      <span data-ttu-id="945cf-368">??</span><span class="sxs-lookup"><span data-stu-id="945cf-368">??</span></span>       | <span data-ttu-id="945cf-369">20</span><span class="sxs-lookup"><span data-stu-id="945cf-369">20</span></span>           |

9. <span data-ttu-id="945cf-370">Em seguida, selecione a opção de alinhamento 'centre' para cada componente de texto:</span><span class="sxs-lookup"><span data-stu-id="945cf-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![Alinhe o texto.](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="945cf-372">Para garantir que o **filho do texto da interface** objetos são fáceis de ler, alterar suas *cor*.</span><span class="sxs-lookup"><span data-stu-id="945cf-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="945cf-373">Faça isso clicando na barra de (atualmente ' preto') ao lado *cor*.</span><span class="sxs-lookup"><span data-stu-id="945cf-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![Entrada correspondente valores para as saídas do texto da interface do usuário.](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="945cf-375">Em seguida, no novo, pequena, *cor* janela, altere o *cor Hex* para: **0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="945cf-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![Atualize a cor para azul.](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="945cf-377">Veja abaixo como o **interface do usuário** deve se parecer.</span><span class="sxs-lookup"><span data-stu-id="945cf-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="945cf-378">No *painel de hierarquia*:</span><span class="sxs-lookup"><span data-stu-id="945cf-378">In the *Hierarchy Panel*:</span></span>

        ![Tem a hierarquia na estrutura fornecida.](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="945cf-380">No *cena* e *modos de exibição de jogos*:</span><span class="sxs-lookup"><span data-stu-id="945cf-380">In the *Scene* and *Game Views*:</span></span>

        ![Ter os modos de exibição de cena e jogo na mesma estrutura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="945cf-382">Capítulo 5 – criar a classe de resultados</span><span class="sxs-lookup"><span data-stu-id="945cf-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="945cf-383">É o primeiro script que você precisa criar o *resultados* classe, que é responsável por fornecer uma maneira de ver os resultados da tradução.</span><span class="sxs-lookup"><span data-stu-id="945cf-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="945cf-384">A classe armazena e exibe o seguinte:</span><span class="sxs-lookup"><span data-stu-id="945cf-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="945cf-385">O resultado da resposta do Azure.</span><span class="sxs-lookup"><span data-stu-id="945cf-385">The response result from Azure.</span></span>
- <span data-ttu-id="945cf-386">O status de microfone.</span><span class="sxs-lookup"><span data-stu-id="945cf-386">The microphone status.</span></span> 
- <span data-ttu-id="945cf-387">O resultado do ditado (voz em texto).</span><span class="sxs-lookup"><span data-stu-id="945cf-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="945cf-388">O resultado da conversão.</span><span class="sxs-lookup"><span data-stu-id="945cf-388">The result of the translation.</span></span>

<span data-ttu-id="945cf-389">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="945cf-389">To create this class:</span></span> 

1.  <span data-ttu-id="945cf-390">Clique com botão direito no *painel do projeto*, em seguida, **criar > pasta**.</span><span class="sxs-lookup"><span data-stu-id="945cf-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="945cf-391">Nomeie a pasta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="945cf-391">Name the folder **Scripts**.</span></span> 
 
    ![Crie a pasta de scripts.](images/AzureLabs-Lab1-31.png)

    ![Abra a pasta de scripts.](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="945cf-394">Com o **Scripts** pasta criar, clique duas vezes nele para abrir.</span><span class="sxs-lookup"><span data-stu-id="945cf-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="945cf-395">Em seguida, dentro dessa pasta, clique com botão direito e selecione **criar >** , em seguida,  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="945cf-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="945cf-396">Nomeie o script *resultados*.</span><span class="sxs-lookup"><span data-stu-id="945cf-396">Name the script *Results*.</span></span> 

    ![Crie o primeiro script.](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="945cf-398">Clique duas vezes na nova *resultados* script para abri-lo com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="945cf-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="945cf-399">Insira os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="945cf-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="945cf-400">Dentro da classe, insira as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="945cf-400">Inside the Class insert the following variables:</span></span>

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  <span data-ttu-id="945cf-401">Em seguida, adicione a *Awake()* método, que será chamado quando a classe inicializa.</span><span class="sxs-lookup"><span data-stu-id="945cf-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="945cf-402">Por fim, adicione os métodos que são responsáveis por produzir várias informações de resultados na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="945cf-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  <span data-ttu-id="945cf-403">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="945cf-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="945cf-404">Capítulo 6 – criar o *MicrophoneManager* classe</span><span class="sxs-lookup"><span data-stu-id="945cf-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="945cf-405">É a segunda classe que você pretende criar o *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="945cf-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="945cf-406">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="945cf-406">This class is responsible for:</span></span>

- <span data-ttu-id="945cf-407">Detectando o dispositivo de gravação anexado ao computador (o que é o padrão) ou fone de ouvido.</span><span class="sxs-lookup"><span data-stu-id="945cf-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="945cf-408">Capturar áudio (voz) e usar ditado para armazená-la como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="945cf-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="945cf-409">Depois que a voz foi pausado, envie o ditado para a classe de conversor.</span><span class="sxs-lookup"><span data-stu-id="945cf-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="945cf-410">Hospede um método que pode parar a captura de voz, se desejado.</span><span class="sxs-lookup"><span data-stu-id="945cf-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="945cf-411">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="945cf-411">To create this class:</span></span> 
1.  <span data-ttu-id="945cf-412">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="945cf-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="945cf-413">Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="945cf-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="945cf-414">Nomeie o script *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="945cf-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="945cf-415">Clique duas vezes no novo script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="945cf-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="945cf-416">Atualizar os namespaces para ser o mesmo que o seguinte, na parte superior do *MicrophoneManager* classe:</span><span class="sxs-lookup"><span data-stu-id="945cf-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="945cf-417">Em seguida, adicione as seguintes variáveis dentro do *MicrophoneManager* classe:</span><span class="sxs-lookup"><span data-stu-id="945cf-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  <span data-ttu-id="945cf-418">Código para o *Awake()* e *Start ()* métodos agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="945cf-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="945cf-419">Eles serão chamados quando inicializa a classe:</span><span class="sxs-lookup"><span data-stu-id="945cf-419">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  <span data-ttu-id="945cf-420">Você pode *exclua* as *Update ()* método uma vez que essa classe não irá usá-lo.</span><span class="sxs-lookup"><span data-stu-id="945cf-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="945cf-421">Agora, você precisa que os métodos que o aplicativo usa para iniciar e parar a captura de voz e passá-lo para o *tradutor* classe, que você criará em breve.</span><span class="sxs-lookup"><span data-stu-id="945cf-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="945cf-422">Copie o código a seguir e cole-a sob o *Start ()* método.</span><span class="sxs-lookup"><span data-stu-id="945cf-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > <span data-ttu-id="945cf-423">Embora este aplicativo não fará usá-lo, o *StopCapturingAudio()* método também foi fornecido aqui, você deve implementar a capacidade de parar a captura de áudio em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="945cf-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="945cf-424">Agora, você precisará adicionar um manipulador de ditado que será invocado quando a voz é interrompido.</span><span class="sxs-lookup"><span data-stu-id="945cf-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="945cf-425">Esse método, em seguida, passará o texto ditado para o *tradutor* classe.</span><span class="sxs-lookup"><span data-stu-id="945cf-425">This method will then pass the dictated text to the *Translator* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. <span data-ttu-id="945cf-426">Certifique-se de salvar suas alterações no Visual Studio antes de retornar para o Unity.</span><span class="sxs-lookup"><span data-stu-id="945cf-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="945cf-427">Neste ponto, você observará um erro que aparecem na *Console do Unity Editor* painel ("o nome 'Conversor' não existe...").</span><span class="sxs-lookup"><span data-stu-id="945cf-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="945cf-428">Isso ocorre porque o código faz referência a *tradutor* classe, que você criará no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="945cf-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="945cf-429">Capítulo 7 – chamada ao serviço do Azure e tradução</span><span class="sxs-lookup"><span data-stu-id="945cf-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="945cf-430">É o último script que você precisa criar o *tradutor* classe.</span><span class="sxs-lookup"><span data-stu-id="945cf-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="945cf-431">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="945cf-431">This class is responsible for:</span></span>

-   <span data-ttu-id="945cf-432">Autenticar o aplicativo com *Azure*, no exchange para um **Token de autenticação**.</span><span class="sxs-lookup"><span data-stu-id="945cf-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="945cf-433">Use o **Token de autenticação** para enviar texto (recebido do *MicrophoneManager* classe) a ser traduzido.</span><span class="sxs-lookup"><span data-stu-id="945cf-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="945cf-434">Receber o resultado convertido e passá-lo para o *resultados* classe a ser visualizado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="945cf-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="945cf-435">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="945cf-435">To create this Class:</span></span> 
1.  <span data-ttu-id="945cf-436">Vá para o **Scripts** pasta que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="945cf-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="945cf-437">Clique com botão direito no **painel do projeto**, **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="945cf-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="945cf-438">Chame o script *tradutor*.</span><span class="sxs-lookup"><span data-stu-id="945cf-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="945cf-439">Clique duas vezes na nova *tradutor* script para abri-lo **com o Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="945cf-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="945cf-440">Adicione os namespaces a seguir na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="945cf-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="945cf-441">Em seguida, adicione as seguintes variáveis dentro do *tradutor* classe:</span><span class="sxs-lookup"><span data-stu-id="945cf-441">Then add the following variables inside the *Translator* class:</span></span>

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - <span data-ttu-id="945cf-442">Os idiomas inseridos para as linguagens **enum** são apenas exemplos.</span><span class="sxs-lookup"><span data-stu-id="945cf-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="945cf-443">Fique à vontade para adicionar mais se desejar; o [API dá suporte a mais de 60 idiomas](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (incluindo Klingon)!</span><span class="sxs-lookup"><span data-stu-id="945cf-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="945cf-444">Há um [página mais interativa que abrangem os idiomas disponíveis](https://www.microsoft.com/translator/business/languages/), porém lembre-se a página será exibida apenas trabalhar quando o idioma do site é definido como ' en-us' (e o site da Microsoft será a probabilidade de redirecionamento para seu idioma nativo).</span><span class="sxs-lookup"><span data-stu-id="945cf-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="945cf-445">Você pode alterar o idioma na parte inferior da página ou alterando a URL do site.</span><span class="sxs-lookup"><span data-stu-id="945cf-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="945cf-446">O **authorizationKey** valor, no trecho de código acima deve ser a **chave** recebida quando você se inscreveu para o *Azure API de tradução de texto*.</span><span class="sxs-lookup"><span data-stu-id="945cf-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="945cf-447">Isso foi abordado em [capítulo 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="945cf-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="945cf-448">Código para o *Awake()* e *Start ()* métodos agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="945cf-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="945cf-449">Nesse caso, o código será fazer uma chamada para *Azure* usando a autorização de chave, para obter uma *Token*.</span><span class="sxs-lookup"><span data-stu-id="945cf-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="945cf-450">O token expirará após 10 minutos.</span><span class="sxs-lookup"><span data-stu-id="945cf-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="945cf-451">Dependendo do cenário para seu aplicativo, você terá que fazer com que a mesma corrotina chamada várias vezes.</span><span class="sxs-lookup"><span data-stu-id="945cf-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="945cf-452">A corrotina para obter o Token é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="945cf-452">The coroutine to obtain the Token is the following:</span></span>

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > <span data-ttu-id="945cf-453">Se você editar o nome do método IEnumerator **GetTokenCoroutine()**, você precisa atualizar o *StartCoroutine* e *StopCoroutine* chamar valores de cadeia de caracteres no código acima.</span><span class="sxs-lookup"><span data-stu-id="945cf-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="945cf-454">[De acordo com a documentação do Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), para interromper um determinado *Corrotina*, você precisa usar o método de valor de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="945cf-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="945cf-455">Em seguida, adicione a corrotina (com um método do fluxo "suporte" logo abaixo dele) para obter a tradução do texto recebido pelo *MicrophoneManager* classe.</span><span class="sxs-lookup"><span data-stu-id="945cf-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="945cf-456">Esse código cria uma cadeia de caracteres de consulta para enviar para o *Azure API de tradução de texto*e, em seguida, usa a classe Unity UnityWebRequest interna para fazer uma chamada de 'Get' para o ponto de extremidade com a cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="945cf-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="945cf-457">O resultado, em seguida, é usado para definir a tradução em seu objeto de resultados.</span><span class="sxs-lookup"><span data-stu-id="945cf-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="945cf-458">O código a seguir mostra a implementação:</span><span class="sxs-lookup"><span data-stu-id="945cf-458">The code below shows the implementation:</span></span>

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. <span data-ttu-id="945cf-459">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="945cf-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="945cf-460">Capítulo 8 – configurar a cena do Unity</span><span class="sxs-lookup"><span data-stu-id="945cf-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="945cf-461">Novamente no Editor do Unity, clique e arraste a *resultados* classe *de* o **Scripts** pasta para o **câmera principal** objeto no  *Painel de hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="945cf-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="945cf-462">Clique no **câmera principal** e examine o *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="945cf-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="945cf-463">Você observará que na recém-adicionada *Script* componente, há quatro campos com valores vazios.</span><span class="sxs-lookup"><span data-stu-id="945cf-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="945cf-464">Essas são as referências de saída para as propriedades no código.</span><span class="sxs-lookup"><span data-stu-id="945cf-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="945cf-465">Arraste apropriado **texto** objetos das *painel de hierarquia* para esse quatro slots, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="945cf-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![Atualize referências de destino com valores especificados.](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="945cf-467">Em seguida, clique e arraste a *Translator* classe o **Scripts** pasta para o **câmera principal** do objeto no *painel de hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="945cf-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="945cf-468">Em seguida, clique e arraste o *MicrophoneManager* classe o **Scripts** pasta para o **câmera principal** do objeto no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="945cf-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="945cf-469">Por fim, clique no **câmera principal** e examine o *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="945cf-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="945cf-470">Você observará que o script que no qual você arrastou, há duas caixas suspensas para que permitirá que você defina os idiomas.</span><span class="sxs-lookup"><span data-stu-id="945cf-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![Verifique se que os idiomas de tradução pretendida são de entrada.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="945cf-472">Capítulo 9 – teste na realidade mista</span><span class="sxs-lookup"><span data-stu-id="945cf-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="945cf-473">Neste ponto, você precisa testar a cena foi implementada corretamente.</span><span class="sxs-lookup"><span data-stu-id="945cf-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="945cf-474">Certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="945cf-474">Ensure that:</span></span>

- <span data-ttu-id="945cf-475">Todas as configurações mencionadas [capítulo 1](#chapter-1--the-azure-portal) estão definidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="945cf-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="945cf-476">O *resultados*, *Translator*, e *MicrophoneManager*, scripts estão anexados ao **câmera principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="945cf-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="945cf-477">Você fez sua *Azure API de tradução de texto* serviço **chave** dentro a **authorizationKey** variável dentro a *Translator* Script.</span><span class="sxs-lookup"><span data-stu-id="945cf-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="945cf-478">Todos os campos a *painel de Inspetor de câmera principal* são atribuídas corretamente.</span><span class="sxs-lookup"><span data-stu-id="945cf-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="945cf-479">O microfone está funcionando ao executar sua cena (se não, verifique se o microfone anexado é o *padrão* dispositivo e se você tem [configurá-lo corretamente dentro do Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span><span class="sxs-lookup"><span data-stu-id="945cf-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="945cf-480">Você pode testar o fone de ouvido imersivo, pressionando as **reproduzir** botão na *Editor do Unity*.</span><span class="sxs-lookup"><span data-stu-id="945cf-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="945cf-481">O aplicativo deve estar funcionando por meio de fone de ouvido imersivo anexado.</span><span class="sxs-lookup"><span data-stu-id="945cf-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="945cf-482">Se você vir um erro no console do Unity sobre o dispositivo de áudio padrão a alteração, a cena pode não funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="945cf-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="945cf-483">Isso é devido à maneira como o portal de realidade misturada lida com microfones internos para fones de ouvido que têm-los.</span><span class="sxs-lookup"><span data-stu-id="945cf-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="945cf-484">Se você vir esse erro, simplesmente parar a cena e iniciá-lo novamente e as coisas devem funcionar como esperado.</span><span class="sxs-lookup"><span data-stu-id="945cf-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="945cf-485">Capítulo 10 – compilar a solução UWP e carregar no computador local</span><span class="sxs-lookup"><span data-stu-id="945cf-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="945cf-486">Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído, portanto, é hora de criá-lo do Unity.</span><span class="sxs-lookup"><span data-stu-id="945cf-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="945cf-487">Navegue até **configurações de Build**: **Arquivo > configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="945cf-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="945cf-488">Dos **configurações de Build** janela, clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="945cf-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Compile a cena do Unity.](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="945cf-490">Se ainda não estiver, marque **Unity C# projetos**.</span><span class="sxs-lookup"><span data-stu-id="945cf-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="945cf-491">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="945cf-491">Click **Build**.</span></span> <span data-ttu-id="945cf-492">Unity iniciará uma *Explorador de arquivos* janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em.</span><span class="sxs-lookup"><span data-stu-id="945cf-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="945cf-493">Criar pasta agora e nomeie- *aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="945cf-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="945cf-494">Em seguida, com o *App* pasta selecionada, pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="945cf-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="945cf-495">Unity começará a compilar seu projeto para o *aplicativo* pasta.</span><span class="sxs-lookup"><span data-stu-id="945cf-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="945cf-496">Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um *Explorador de arquivos* janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).</span><span class="sxs-lookup"><span data-stu-id="945cf-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="945cf-497">Capítulo 11 – implantar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="945cf-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="945cf-498">Para implantar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="945cf-498">To deploy your application:</span></span>

1.  <span data-ttu-id="945cf-499">Navegue até seu novo build do Unity (o *App* pasta) e abra o arquivo de solução com *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="945cf-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="945cf-500">No, selecione a configuração da solução **depurar**.</span><span class="sxs-lookup"><span data-stu-id="945cf-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="945cf-501">Na plataforma da solução, selecione **x86**, **Máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="945cf-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="945cf-502">Para o Microsoft HoloLens, talvez você ache mais fácil de definir isso como *máquina remota*, de modo que você não estiver vinculado ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="945cf-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="945cf-503">No entanto, você precisará também fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="945cf-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="945cf-504">Saber a **endereço IP** de seu HoloLens, que podem ser encontrado dentro a *Configurações > rede e Internet > Wi-Fi > Opções avançadas de*; o IPv4 é o endereço que você deve usar.</span><span class="sxs-lookup"><span data-stu-id="945cf-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="945cf-505">Certifique-se *modo de desenvolvedor* é **na**; encontrado na *Configurações > atualização e segurança > para os desenvolvedores*.</span><span class="sxs-lookup"><span data-stu-id="945cf-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="945cf-507">Vá para **menu Build** e clique em **implantar solução** para carregar o aplicativo a seu computador.</span><span class="sxs-lookup"><span data-stu-id="945cf-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="945cf-508">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="945cf-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="945cf-509">Depois de iniciado, o aplicativo solicitará que você autorizar o acesso ao microfone.</span><span class="sxs-lookup"><span data-stu-id="945cf-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="945cf-510">Certifique-se de clicar o **Sim** botão.</span><span class="sxs-lookup"><span data-stu-id="945cf-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="945cf-511">Agora você está pronto para começar a traduzir!</span><span class="sxs-lookup"><span data-stu-id="945cf-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="945cf-512">O aplicativo de API de tradução de texto concluído</span><span class="sxs-lookup"><span data-stu-id="945cf-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="945cf-513">Parabéns, você criou um aplicativo de realidade mista que aproveita a API de texto de tradução do Azure para converter fala em texto traduzido.</span><span class="sxs-lookup"><span data-stu-id="945cf-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![Produto final.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="945cf-515">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="945cf-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="945cf-516">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="945cf-516">Exercise 1</span></span>

<span data-ttu-id="945cf-517">Você pode adicionar funcionalidade de texto em fala para o aplicativo, para que o texto retornado é falado?</span><span class="sxs-lookup"><span data-stu-id="945cf-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="945cf-518">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="945cf-518">Exercise 2</span></span>

<span data-ttu-id="945cf-519">Tornam possível para o usuário altere os idiomas de origem e de saída ('de' e 'para') dentro do próprio aplicativo, portanto, o aplicativo não precisa ser recriado sempre que você deseja alterar os idiomas.</span><span class="sxs-lookup"><span data-stu-id="945cf-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
