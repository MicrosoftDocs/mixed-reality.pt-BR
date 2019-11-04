---
title: Sr e Azure 301 – tradução de idioma
description: Conclua este curso para aprender a implementar o API de Tradução de Texto do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, texto do tradutor, hololens, imersão, VR
ms.openlocfilehash: 012eb5522c866e9e0f1caf5e4024305af07e298c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438530"
---
>[!NOTE]
><span data-ttu-id="7b942-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="7b942-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7b942-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="7b942-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7b942-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7b942-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7b942-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="7b942-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7b942-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7b942-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7b942-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="7b942-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="7b942-110">Sr e Azure 301: tradução de idioma</span><span class="sxs-lookup"><span data-stu-id="7b942-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="7b942-111">Neste curso, você aprenderá a adicionar recursos de tradução a um aplicativo de realidade misturada usando os serviços cognitivas do Azure, com o API de Tradução de Texto.</span><span class="sxs-lookup"><span data-stu-id="7b942-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![Produto final](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="7b942-113">O API de Tradução de Texto é um serviço de tradução que funciona quase em tempo real.</span><span class="sxs-lookup"><span data-stu-id="7b942-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="7b942-114">O serviço é baseado em nuvem e, usando uma chamada à API REST, um aplicativo pode usar a tecnologia de conversão de máquina neural para traduzir texto para outro idioma.</span><span class="sxs-lookup"><span data-stu-id="7b942-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="7b942-115">Para obter mais informações, visite a [página de API de tradução de texto do Azure](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span><span class="sxs-lookup"><span data-stu-id="7b942-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="7b942-116">Após a conclusão deste curso, você terá um aplicativo de realidade misturada que poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7b942-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="7b942-117">O usuário vai falar em um microfone conectado a um headset de imersão (VR) (ou o microfone interno do HoloLens).</span><span class="sxs-lookup"><span data-stu-id="7b942-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="7b942-118">O aplicativo irá capturar o ditado e enviá-lo para o API de Tradução de Texto do Azure.</span><span class="sxs-lookup"><span data-stu-id="7b942-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="7b942-119">O resultado da tradução será exibido em um grupo de interface do usuário simples na cena do Unity.</span><span class="sxs-lookup"><span data-stu-id="7b942-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="7b942-120">Este curso ensinará como obter os resultados do serviço do tradutor em um aplicativo de exemplo baseado em Unity.</span><span class="sxs-lookup"><span data-stu-id="7b942-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="7b942-121">Será necessário aplicar esses conceitos a um aplicativo personalizado que você possa estar criando.</span><span class="sxs-lookup"><span data-stu-id="7b942-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="7b942-122">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="7b942-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7b942-123">Course</span><span class="sxs-lookup"><span data-stu-id="7b942-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7b942-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7b942-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7b942-125"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="7b942-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="7b942-126">Sr e Azure 301: tradução de idioma</span><span class="sxs-lookup"><span data-stu-id="7b942-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="7b942-127">✔️</span><span class="sxs-lookup"><span data-stu-id="7b942-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="7b942-128">✔️</span><span class="sxs-lookup"><span data-stu-id="7b942-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="7b942-129">Embora este curso se concentre principalmente em fones de ouvido (VR) de realidade mista do Windows, você também pode aplicar o que aprende neste curso ao Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7b942-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="7b942-130">Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7b942-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="7b942-131">Ao usar o HoloLens, você pode notar um eco durante a captura de voz.</span><span class="sxs-lookup"><span data-stu-id="7b942-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7b942-132">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7b942-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="7b942-133">Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o.</span><span class="sxs-lookup"><span data-stu-id="7b942-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="7b942-134">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="7b942-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="7b942-135">Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="7b942-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="7b942-136">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="7b942-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="7b942-137">Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)</span><span class="sxs-lookup"><span data-stu-id="7b942-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="7b942-138">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="7b942-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="7b942-139">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="7b942-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="7b942-140">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="7b942-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="7b942-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7b942-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="7b942-142">Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="7b942-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="7b942-143">Um conjunto de fones de ouvido com um microfone interno (se o headset não tiver um MIC interno e alto-falantes)</span><span class="sxs-lookup"><span data-stu-id="7b942-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="7b942-144">Acesso à Internet para a instalação do Azure e recuperação de tradução</span><span class="sxs-lookup"><span data-stu-id="7b942-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="7b942-145">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="7b942-145">Before you start</span></span>

- <span data-ttu-id="7b942-146">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="7b942-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="7b942-147">O código neste tutorial permitirá que você registre a partir do dispositivo de microfone padrão conectado ao seu PC.</span><span class="sxs-lookup"><span data-stu-id="7b942-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="7b942-148">Verifique se o dispositivo de microfone padrão está definido para o dispositivo que você planeja usar para capturar sua voz.</span><span class="sxs-lookup"><span data-stu-id="7b942-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="7b942-149">Para permitir que seu computador habilite o ditado, vá para **configurações > privacidade > fala, digitando a tinta & digitar** e selecione o botão **ativar os serviços de fala e digitar sugestões**.</span><span class="sxs-lookup"><span data-stu-id="7b942-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="7b942-150">Se você estiver usando um microfone e fones de ouvido conectados ao (ou integrados ao) seu headset, certifique-se de que a opção "quando eu usar meu Headset, mude para microfone MIC" esteja ativada em **configurações > realidade misturada > áudio e fala**.</span><span class="sxs-lookup"><span data-stu-id="7b942-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![Configurações de realidade misturada](images/AzureLabs-Lab1-00-5.png)

   ![Configuração do microfone](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="7b942-153">Lembre-se de que, se você estiver desenvolvendo um headset de imersão para este laboratório, poderá enfrentar problemas de dispositivo de saída de áudio.</span><span class="sxs-lookup"><span data-stu-id="7b942-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="7b942-154">Isso ocorre devido a um problema com o Unity, que é corrigido em versões posteriores do Unity (Unity 2018,2).</span><span class="sxs-lookup"><span data-stu-id="7b942-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="7b942-155">O problema impede que o Unity altere o dispositivo de saída de áudio padrão em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7b942-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="7b942-156">Como solução alternativa, verifique se você concluiu as etapas acima e feche e reabra o editor, quando esse problema apresenta.</span><span class="sxs-lookup"><span data-stu-id="7b942-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="7b942-157">Capítulo 1 – o portal do Azure</span><span class="sxs-lookup"><span data-stu-id="7b942-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="7b942-158">Para usar a API do Azure Translator, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b942-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="7b942-159">Faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="7b942-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="7b942-160">Se você ainda não tiver uma conta do Azure, será necessário criar uma.</span><span class="sxs-lookup"><span data-stu-id="7b942-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="7b942-161">Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="7b942-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="7b942-162">Depois de fazer logon, clique em **novo** no canto superior esquerdo e pesquise por "API de tradução de texto".</span><span class="sxs-lookup"><span data-stu-id="7b942-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="7b942-163">Selecione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="7b942-163">Select **Enter**.</span></span>

    ![Novo recurso](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="7b942-165">A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="7b942-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="7b942-166">A nova página fornecerá uma descrição do serviço *API de tradução de texto* .</span><span class="sxs-lookup"><span data-stu-id="7b942-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="7b942-167">Na parte inferior esquerda desta página, selecione o botão **criar** para criar uma associação com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="7b942-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Criar API de Tradução de Texto serviço](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="7b942-169">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="7b942-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="7b942-170">Insira o **nome** desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="7b942-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="7b942-171">Selecione uma **assinatura**apropriada.</span><span class="sxs-lookup"><span data-stu-id="7b942-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="7b942-172">Selecione o **tipo de preço** apropriado para você, se esta for a primeira vez que criar um *serviço de tradução de texto*, uma camada gratuita (chamada F0) deverá estar disponível para você.</span><span class="sxs-lookup"><span data-stu-id="7b942-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="7b942-173">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="7b942-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="7b942-174">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="7b942-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="7b942-175">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="7b942-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="7b942-176">Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="7b942-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="7b942-177">Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="7b942-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="7b942-178">O local ideal seria na região em que o aplicativo seria executado.</span><span class="sxs-lookup"><span data-stu-id="7b942-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="7b942-179">Alguns ativos do Azure só estão disponíveis em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="7b942-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="7b942-180">Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="7b942-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="7b942-181">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="7b942-181">Select **Create**.</span></span>

        ![Selecione o botão criar.](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="7b942-183">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="7b942-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="7b942-184">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="7b942-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Notificação de criação de serviço do Azure](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="7b942-186">Clique na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="7b942-186">Click on the notification to explore your new Service instance.</span></span> 

    ![Vá para o pop-up de recursos.](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="7b942-188">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="7b942-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="7b942-189">Você será levado para sua nova instância do serviço API de Tradução de Texto.</span><span class="sxs-lookup"><span data-stu-id="7b942-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![API de Tradução de Texto página de serviço](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="7b942-191">Neste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, o que é feito por meio do uso da chave de assinatura do serviço.</span><span class="sxs-lookup"><span data-stu-id="7b942-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="7b942-192">Na página *início rápido* do serviço de *tradução de texto* , navegue até a primeira etapa, *pegue as chaves*e clique em **chaves** (você também pode fazer isso clicando nas teclas de hiperlink azul, localizadas no menu de navegação serviços, indicado pelo ícone de chave).</span><span class="sxs-lookup"><span data-stu-id="7b942-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="7b942-193">Isso revelará suas *chaves*de serviço.</span><span class="sxs-lookup"><span data-stu-id="7b942-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="7b942-194">Faça uma cópia de uma das chaves exibidas, pois você precisará dela posteriormente em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7b942-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="7b942-195">Capítulo 2 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="7b942-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="7b942-196">Configure e teste seu headset de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="7b942-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="7b942-197">Você não precisará de controladores de animação para este curso.</span><span class="sxs-lookup"><span data-stu-id="7b942-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="7b942-198">Se você precisar de suporte para configurar um headset de imersão, [siga estas etapas](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="7b942-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="7b942-199">A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos:</span><span class="sxs-lookup"><span data-stu-id="7b942-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="7b942-200">Abra o *Unity* e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="7b942-200">Open *Unity* and click **New**.</span></span> 

    ![Inicie o novo projeto do Unity.](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="7b942-202">Agora, você precisará fornecer um nome de projeto de Unity.</span><span class="sxs-lookup"><span data-stu-id="7b942-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="7b942-203">Insira **MR_Translation**.</span><span class="sxs-lookup"><span data-stu-id="7b942-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="7b942-204">Verifique se o tipo de projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="7b942-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="7b942-205">Defina o *local* como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="7b942-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="7b942-206">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="7b942-206">Then, click **Create project**.</span></span>

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="7b942-208">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7b942-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="7b942-209">Vá para **Editar preferências de >** e, em seguida, na nova janela, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="7b942-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="7b942-210">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="7b942-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="7b942-211">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="7b942-211">Close the **Preferences** window.</span></span>

    ![Atualize a preferência do editor de script.](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="7b942-213">Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma para **plataforma universal do Windows**clicando no botão **alternar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="7b942-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Janela de configurações de compilação, alterne a plataforma para UWP.](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="7b942-215">Vá para **arquivo > configurações de compilação** e verifique se:</span><span class="sxs-lookup"><span data-stu-id="7b942-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="7b942-216">O **dispositivo de destino** está definido como **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="7b942-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="7b942-217">Para o Microsoft HoloLens, defina o **dispositivo de destino** para o *hololens*.</span><span class="sxs-lookup"><span data-stu-id="7b942-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="7b942-218">O **tipo de compilação** está definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="7b942-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="7b942-219">O **SDK** está definido para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="7b942-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="7b942-220">A **versão do Visual Studio** está definida para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="7b942-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="7b942-221">**Compilar e executar** é definido como **computador local**</span><span class="sxs-lookup"><span data-stu-id="7b942-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="7b942-222">Salve a cena e adicione-a à compilação.</span><span class="sxs-lookup"><span data-stu-id="7b942-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="7b942-223">Faça isso selecionando **Adicionar abrir cenas**.</span><span class="sxs-lookup"><span data-stu-id="7b942-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="7b942-224">Uma janela salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="7b942-224">A save window will appear.</span></span>

            ![Clique no botão Adicionar cenas abertas](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="7b942-226">Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.</span><span class="sxs-lookup"><span data-stu-id="7b942-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Criar nova pasta de scripts](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="7b942-228">Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo*:, digite **MR_TranslationScene**e pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="7b942-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![Dê um nome à nova cena.](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="7b942-230">Lembre-se de que você deve salvar as cenas do Unity na pasta *ativos* , pois elas devem ser associadas ao projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="7b942-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="7b942-231">Criar a pasta de cenas (e outras pastas semelhantes) é uma maneira típica de estruturar um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="7b942-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="7b942-232">As configurações restantes, em *configurações de compilação*, devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="7b942-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="7b942-233">Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="7b942-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra as configurações do Player.](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="7b942-235">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="7b942-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="7b942-236">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="7b942-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="7b942-237">A **versão de tempo de execução de script** deve ser **estável** (.net 3,5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="7b942-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="7b942-238">O **back-end de script** deve ser **.net**</span><span class="sxs-lookup"><span data-stu-id="7b942-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="7b942-239">O **nível de compatibilidade da API** deve ser **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="7b942-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Atualize outras configurações.](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="7b942-241">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="7b942-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="7b942-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="7b942-242">**InternetClient**</span></span>
        2. <span data-ttu-id="7b942-243">**Phone**</span><span class="sxs-lookup"><span data-stu-id="7b942-243">**Microphone**</span></span>

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="7b942-245">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o **SDK do Windows Mixed Reality** foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="7b942-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Atualize as configurações de X R.](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="7b942-247">De volta **às configurações de compilação**, os *projetos de C# Unity* não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste.</span><span class="sxs-lookup"><span data-stu-id="7b942-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="7b942-248">Feche a janela configurações de compilação.</span><span class="sxs-lookup"><span data-stu-id="7b942-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="7b942-249">Salve sua cena e projeto (**arquivo > salvar cena/arquivo > salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="7b942-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="7b942-250">Capítulo 3 – configuração principal da câmera</span><span class="sxs-lookup"><span data-stu-id="7b942-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b942-251">Se você quiser ignorar o componente *de configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para [baixar esse. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), importe-o para seu projeto como um [*pacote personalizado*](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue no [capítulo 5](#chapter-5--create-the-results-class).</span><span class="sxs-lookup"><span data-stu-id="7b942-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="7b942-252">Você ainda precisará criar um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="7b942-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="7b942-253">No *painel hierarquia*, você encontrará um objeto chamado **câmera principal**, esse objeto representa o ponto de vista de "cabeçalho" quando você estiver "dentro" de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b942-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="7b942-254">Com o painel do Unity na frente de você, selecione a **câmera principal gameobject**.</span><span class="sxs-lookup"><span data-stu-id="7b942-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="7b942-255">Você observará que o *painel Inspetor* (geralmente localizado à direita, dentro do painel) mostrará os vários componentes desse *gameobject*, com a *transformação* na parte superior, seguida pela *câmera*e alguns outros componentes.</span><span class="sxs-lookup"><span data-stu-id="7b942-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="7b942-256">Você precisará redefinir a transformação da câmera principal, para que ela seja posicionada corretamente.</span><span class="sxs-lookup"><span data-stu-id="7b942-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="7b942-257">Para fazer isso, selecione o ícone de **engrenagem** ao lado do componente *transformação* da câmera e selecione **Redefinir**.</span><span class="sxs-lookup"><span data-stu-id="7b942-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![Redefina a transformação principal da câmera.](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="7b942-259">O componente de *transformação* deve ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="7b942-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="7b942-260">A *posição* é definida como **0, 0,** 0</span><span class="sxs-lookup"><span data-stu-id="7b942-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="7b942-261">A *rotação* está definida como **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="7b942-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="7b942-262">E *Scale* é definido como **1, 1, 1**</span><span class="sxs-lookup"><span data-stu-id="7b942-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![Transformar informações da câmera](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="7b942-264">Em seguida, com o objeto **principal da câmera** selecionado, consulte o botão **Adicionar componente** localizado na parte inferior do *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="7b942-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="7b942-265">Selecione esse botão e pesquise (digitando fonte de *áudio* no campo de pesquisa ou navegando nas seções) para o componente chamado **fonte de áudio** , conforme mostrado abaixo, e selecione-o (pressionar Enter em também funciona).</span><span class="sxs-lookup"><span data-stu-id="7b942-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="7b942-266">Um componente de *fonte de áudio* será adicionado à **câmera principal**, conforme demonstrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="7b942-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![Adicione um componente de fonte de áudio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="7b942-268">Para o Microsoft HoloLens, você também precisará alterar o seguinte, que fazem parte do componente da **câmera** em sua **câmera principal**:</span><span class="sxs-lookup"><span data-stu-id="7b942-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="7b942-269">**Limpar sinalizadores:** Cor sólida.</span><span class="sxs-lookup"><span data-stu-id="7b942-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="7b942-270">**Plano de fundo** ' Black, Alpha 0 ' – cor hexadecimal: #00000000.</span><span class="sxs-lookup"><span data-stu-id="7b942-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="7b942-271">Capítulo 4 – tela de depuração da instalação</span><span class="sxs-lookup"><span data-stu-id="7b942-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="7b942-272">Para mostrar a entrada e a saída da tradução, é necessário criar uma interface do usuário básica.</span><span class="sxs-lookup"><span data-stu-id="7b942-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="7b942-273">Para este curso, você criará um objeto de interface do usuário de tela, com vários objetos ' Text ' para mostrar os dados.</span><span class="sxs-lookup"><span data-stu-id="7b942-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="7b942-274">Clique com o botão direito do mouse em uma área vazia do *painel hierarquia*, em **interface do usuário**, adicionar uma **tela**.</span><span class="sxs-lookup"><span data-stu-id="7b942-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![Adicionar novo objeto de interface do usuário da tela.](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="7b942-276">Com o objeto Canvas selecionado, no *painel Inspetor* (dentro do componente ' Canvas '), altere o **modo de processamento** para **espaço mundial**.</span><span class="sxs-lookup"><span data-stu-id="7b942-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="7b942-277">Em seguida, altere os seguintes parâmetros na *transformação Rect do painel Inspetor*:</span><span class="sxs-lookup"><span data-stu-id="7b942-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="7b942-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="7b942-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="7b942-279">*Largura* -500</span><span class="sxs-lookup"><span data-stu-id="7b942-279">*Width* -    500</span></span>
    3. <span data-ttu-id="7b942-280">*Altura* -300</span><span class="sxs-lookup"><span data-stu-id="7b942-280">*Height* -   300</span></span>
    4. <span data-ttu-id="7b942-281">*Escala* - **X** 0,13 **Y** 0,13 **Z** 0,13</span><span class="sxs-lookup"><span data-stu-id="7b942-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![Atualize a transformação Rect para a tela.](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="7b942-283">Clique com o botão direito do mouse na **tela** no *painel hierarquia*, em **interface do usuário**e adicione um **painel**.</span><span class="sxs-lookup"><span data-stu-id="7b942-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="7b942-284">Esse **painel** fornecerá uma tela de fundo para o texto que será exibido na cena.</span><span class="sxs-lookup"><span data-stu-id="7b942-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="7b942-285">Clique com o botão direito do mouse no **painel** no *painel hierarquia*, em **interface do usuário**e adicione um **objeto de texto**.</span><span class="sxs-lookup"><span data-stu-id="7b942-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="7b942-286">Repita o mesmo processo até que você tenha criado quatro objetos de texto da interface do usuário no total (dica: se você tiver o primeiro objeto ' texto ' selecionado, poderá simplesmente pressionar **' CTRL ' + ' d'** para duplicá-lo, até que você tenha quatro no total).</span><span class="sxs-lookup"><span data-stu-id="7b942-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="7b942-287">Para cada **objeto de texto**, selecione-o e use as tabelas abaixo para definir os parâmetros no *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="7b942-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="7b942-288">Para o componente de *transformação Rect* :</span><span class="sxs-lookup"><span data-stu-id="7b942-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="7b942-289">Nome</span><span class="sxs-lookup"><span data-stu-id="7b942-289">Name</span></span>                   | <span data-ttu-id="7b942-290">Transformação- *posição*</span><span class="sxs-lookup"><span data-stu-id="7b942-290">Transform - *Position*</span></span>             | <span data-ttu-id="7b942-291">Largura</span><span class="sxs-lookup"><span data-stu-id="7b942-291">Width</span></span>      | <span data-ttu-id="7b942-292">Tamanho</span><span class="sxs-lookup"><span data-stu-id="7b942-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="7b942-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="7b942-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="7b942-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="7b942-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="7b942-295">300</span><span class="sxs-lookup"><span data-stu-id="7b942-295">300</span></span>        | <span data-ttu-id="7b942-296">30</span><span class="sxs-lookup"><span data-stu-id="7b942-296">30</span></span>        |
        | <span data-ttu-id="7b942-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="7b942-297">AzureResponseLabel</span></span>     | <span data-ttu-id="7b942-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="7b942-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="7b942-299">300</span><span class="sxs-lookup"><span data-stu-id="7b942-299">300</span></span>        | <span data-ttu-id="7b942-300">30</span><span class="sxs-lookup"><span data-stu-id="7b942-300">30</span></span>        |
        | <span data-ttu-id="7b942-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="7b942-301">DictationLabel</span></span>         | <span data-ttu-id="7b942-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="7b942-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="7b942-303">300</span><span class="sxs-lookup"><span data-stu-id="7b942-303">300</span></span>        | <span data-ttu-id="7b942-304">30</span><span class="sxs-lookup"><span data-stu-id="7b942-304">30</span></span>        |
        | <span data-ttu-id="7b942-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="7b942-305">TranslationResultLabel</span></span> | <span data-ttu-id="7b942-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="7b942-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="7b942-307">300</span><span class="sxs-lookup"><span data-stu-id="7b942-307">300</span></span>        | <span data-ttu-id="7b942-308">30</span><span class="sxs-lookup"><span data-stu-id="7b942-308">30</span></span>        |


    2. <span data-ttu-id="7b942-309">Para o componente de **texto (script)** :</span><span class="sxs-lookup"><span data-stu-id="7b942-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="7b942-310">Nome</span><span class="sxs-lookup"><span data-stu-id="7b942-310">Name</span></span>                   | <span data-ttu-id="7b942-311">Texto</span><span class="sxs-lookup"><span data-stu-id="7b942-311">Text</span></span>               | <span data-ttu-id="7b942-312">Tamanho da fonte</span><span class="sxs-lookup"><span data-stu-id="7b942-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="7b942-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="7b942-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="7b942-314">Status do microfone:</span><span class="sxs-lookup"><span data-stu-id="7b942-314">Microphone Status:</span></span> | <span data-ttu-id="7b942-315">20</span><span class="sxs-lookup"><span data-stu-id="7b942-315">20</span></span>           |
        | <span data-ttu-id="7b942-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="7b942-316">AzureResponseLabel</span></span>     | <span data-ttu-id="7b942-317">Resposta da Web do Azure</span><span class="sxs-lookup"><span data-stu-id="7b942-317">Azure Web Response</span></span> | <span data-ttu-id="7b942-318">20</span><span class="sxs-lookup"><span data-stu-id="7b942-318">20</span></span>           |
        | <span data-ttu-id="7b942-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="7b942-319">DictationLabel</span></span>         |   <span data-ttu-id="7b942-320">Você acabou de dizer:</span><span class="sxs-lookup"><span data-stu-id="7b942-320">You just said:</span></span>   | <span data-ttu-id="7b942-321">20</span><span class="sxs-lookup"><span data-stu-id="7b942-321">20</span></span>           |
        | <span data-ttu-id="7b942-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="7b942-322">TranslationResultLabel</span></span> |    <span data-ttu-id="7b942-323">Transferência</span><span class="sxs-lookup"><span data-stu-id="7b942-323">Translation:</span></span>    | <span data-ttu-id="7b942-324">20</span><span class="sxs-lookup"><span data-stu-id="7b942-324">20</span></span>           |

        ![Insira os valores correspondentes para os rótulos de interface do usuário.](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="7b942-326">Além disso, torne o estilo da fonte em **negrito**.</span><span class="sxs-lookup"><span data-stu-id="7b942-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="7b942-327">Isso fará com que o texto seja mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="7b942-327">This will make the text easier to read.</span></span>

        ![Fonte em negrito.](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="7b942-329">Para cada *objeto de texto da interface do usuário* criado no [capítulo 5](#chapter-5--create-the-results-class), crie um novo **objeto de texto da interface do usuário** *filho* .</span><span class="sxs-lookup"><span data-stu-id="7b942-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="7b942-330">Esses filhos exibirão a saída do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b942-330">These children will display the output of the application.</span></span> <span data-ttu-id="7b942-331">Crie objetos *filho* clicando com o botão direito do mouse no pai pretendido (por exemplo, *MicrophoneStatusLabel*) e selecione **interface do usuário** e, em seguida, selecione **texto**.</span><span class="sxs-lookup"><span data-stu-id="7b942-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="7b942-332">Para cada um desses filhos, selecione-o e use as tabelas abaixo para definir os parâmetros no painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="7b942-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="7b942-333">Para o componente de **transformação Rect** :</span><span class="sxs-lookup"><span data-stu-id="7b942-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="7b942-334">Nome</span><span class="sxs-lookup"><span data-stu-id="7b942-334">Name</span></span>                  | <span data-ttu-id="7b942-335">Transformação- *posição*</span><span class="sxs-lookup"><span data-stu-id="7b942-335">Transform - *Position*</span></span> | <span data-ttu-id="7b942-336">Largura</span><span class="sxs-lookup"><span data-stu-id="7b942-336">Width</span></span>      | <span data-ttu-id="7b942-337">Tamanho</span><span class="sxs-lookup"><span data-stu-id="7b942-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="7b942-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="7b942-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="7b942-339">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="7b942-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="7b942-340">300</span><span class="sxs-lookup"><span data-stu-id="7b942-340">300</span></span>        | <span data-ttu-id="7b942-341">30</span><span class="sxs-lookup"><span data-stu-id="7b942-341">30</span></span>        |
        | <span data-ttu-id="7b942-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="7b942-342">AzureResponseText</span></span>     | <span data-ttu-id="7b942-343">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="7b942-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="7b942-344">300</span><span class="sxs-lookup"><span data-stu-id="7b942-344">300</span></span>        | <span data-ttu-id="7b942-345">30</span><span class="sxs-lookup"><span data-stu-id="7b942-345">30</span></span>        |
        | <span data-ttu-id="7b942-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="7b942-346">DictationText</span></span>         | <span data-ttu-id="7b942-347">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="7b942-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="7b942-348">300</span><span class="sxs-lookup"><span data-stu-id="7b942-348">300</span></span>        | <span data-ttu-id="7b942-349">30</span><span class="sxs-lookup"><span data-stu-id="7b942-349">30</span></span>        |
        | <span data-ttu-id="7b942-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="7b942-350">TranslationResultText</span></span> | <span data-ttu-id="7b942-351">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="7b942-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="7b942-352">300</span><span class="sxs-lookup"><span data-stu-id="7b942-352">300</span></span>        | <span data-ttu-id="7b942-353">30</span><span class="sxs-lookup"><span data-stu-id="7b942-353">30</span></span>        |

    2. <span data-ttu-id="7b942-354">Para o componente de **texto (script)** :</span><span class="sxs-lookup"><span data-stu-id="7b942-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="7b942-355">Nome</span><span class="sxs-lookup"><span data-stu-id="7b942-355">Name</span></span>                  | <span data-ttu-id="7b942-356">Texto</span><span class="sxs-lookup"><span data-stu-id="7b942-356">Text</span></span>          | <span data-ttu-id="7b942-357">Tamanho da fonte</span><span class="sxs-lookup"><span data-stu-id="7b942-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="7b942-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="7b942-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="7b942-359">??</span><span class="sxs-lookup"><span data-stu-id="7b942-359">??</span></span>       | <span data-ttu-id="7b942-360">20</span><span class="sxs-lookup"><span data-stu-id="7b942-360">20</span></span>           |
        | <span data-ttu-id="7b942-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="7b942-361">AzureResponseText</span></span>     |      <span data-ttu-id="7b942-362">??</span><span class="sxs-lookup"><span data-stu-id="7b942-362">??</span></span>       | <span data-ttu-id="7b942-363">20</span><span class="sxs-lookup"><span data-stu-id="7b942-363">20</span></span>           |
        | <span data-ttu-id="7b942-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="7b942-364">DictationText</span></span>         |      <span data-ttu-id="7b942-365">??</span><span class="sxs-lookup"><span data-stu-id="7b942-365">??</span></span>       | <span data-ttu-id="7b942-366">20</span><span class="sxs-lookup"><span data-stu-id="7b942-366">20</span></span>           |
        | <span data-ttu-id="7b942-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="7b942-367">TranslationResultText</span></span> |      <span data-ttu-id="7b942-368">??</span><span class="sxs-lookup"><span data-stu-id="7b942-368">??</span></span>       | <span data-ttu-id="7b942-369">20</span><span class="sxs-lookup"><span data-stu-id="7b942-369">20</span></span>           |

9. <span data-ttu-id="7b942-370">Em seguida, selecione a opção de alinhamento ' centro ' para cada componente de texto:</span><span class="sxs-lookup"><span data-stu-id="7b942-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![alinhar texto.](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="7b942-372">Para garantir que os objetos de **texto da interface do usuário filho** sejam facilmente legíveis, altere sua *cor*.</span><span class="sxs-lookup"><span data-stu-id="7b942-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="7b942-373">Para fazer isso, clique na barra (atualmente, ' preto ') ao lado de *cor*.</span><span class="sxs-lookup"><span data-stu-id="7b942-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![Insira valores correspondentes para as saídas de texto da interface do usuário.](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="7b942-375">Em seguida, na janela nova, pequena, *cor* , altere a *cor hexadecimal* para: **0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="7b942-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![Atualizar cor para azul.](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="7b942-377">Veja abaixo a aparência da **interface do usuário** .</span><span class="sxs-lookup"><span data-stu-id="7b942-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="7b942-378">No *painel hierarquia*:</span><span class="sxs-lookup"><span data-stu-id="7b942-378">In the *Hierarchy Panel*:</span></span>

        ![Ter hierarquia na estrutura fornecida.](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="7b942-380">Nas *exibições*de *cena* e de jogo:</span><span class="sxs-lookup"><span data-stu-id="7b942-380">In the *Scene* and *Game Views*:</span></span>

        ![Ter as exibições de cena e jogo na mesma estrutura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="7b942-382">Capítulo 5 – criar a classe Results</span><span class="sxs-lookup"><span data-stu-id="7b942-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="7b942-383">O primeiro script que você precisa criar é a classe *Results* , que é responsável por fornecer uma maneira de ver os resultados da tradução.</span><span class="sxs-lookup"><span data-stu-id="7b942-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="7b942-384">A classe armazena e exibe o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7b942-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="7b942-385">O resultado da resposta do Azure.</span><span class="sxs-lookup"><span data-stu-id="7b942-385">The response result from Azure.</span></span>
- <span data-ttu-id="7b942-386">O status do microfone.</span><span class="sxs-lookup"><span data-stu-id="7b942-386">The microphone status.</span></span> 
- <span data-ttu-id="7b942-387">O resultado do ditado (voz para texto).</span><span class="sxs-lookup"><span data-stu-id="7b942-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="7b942-388">O resultado da tradução.</span><span class="sxs-lookup"><span data-stu-id="7b942-388">The result of the translation.</span></span>

<span data-ttu-id="7b942-389">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="7b942-389">To create this class:</span></span> 

1.  <span data-ttu-id="7b942-390">Clique com o botão direito do mouse no *painel Projeto*e **crie > pasta**.</span><span class="sxs-lookup"><span data-stu-id="7b942-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="7b942-391">Nomeie a pasta **scripts**.</span><span class="sxs-lookup"><span data-stu-id="7b942-391">Name the folder **Scripts**.</span></span> 
 
    ![Criar pasta de scripts.](images/AzureLabs-Lab1-31.png)

    ![Abra a pasta scripts.](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="7b942-394">Com a pasta **scripts** Create, clique duas vezes nela para abrir.</span><span class="sxs-lookup"><span data-stu-id="7b942-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="7b942-395">Em seguida, dentro dessa pasta, clique com o botão direito do mouse **C#** e selecione **criar >** , em seguida, script.</span><span class="sxs-lookup"><span data-stu-id="7b942-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="7b942-396">Nomeie os *resultados*do script.</span><span class="sxs-lookup"><span data-stu-id="7b942-396">Name the script *Results*.</span></span> 

    ![Crie o primeiro script.](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="7b942-398">Clique duas vezes no script novos *resultados* para abri-lo com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7b942-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="7b942-399">Insira os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="7b942-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="7b942-400">Dentro da classe, insira as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="7b942-400">Inside the Class insert the following variables:</span></span>

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

6.  <span data-ttu-id="7b942-401">Em seguida, adicione o método *ativo ()* , que será chamado quando a classe for inicializada.</span><span class="sxs-lookup"><span data-stu-id="7b942-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="7b942-402">Por fim, adicione os métodos que são responsáveis pela saída de várias informações de resultados para a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="7b942-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

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

8.  <span data-ttu-id="7b942-403">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="7b942-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="7b942-404">Capítulo 6 – criar a classe *microphonemanager*</span><span class="sxs-lookup"><span data-stu-id="7b942-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="7b942-405">A segunda classe que você pretende criar é o *microphonemanager*.</span><span class="sxs-lookup"><span data-stu-id="7b942-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="7b942-406">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="7b942-406">This class is responsible for:</span></span>

- <span data-ttu-id="7b942-407">Detectando o dispositivo de gravação conectado ao headset ou ao computador (o que for o padrão).</span><span class="sxs-lookup"><span data-stu-id="7b942-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="7b942-408">Capture o áudio (voz) e use o ditado para armazená-lo como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7b942-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="7b942-409">Depois que a voz for pausada, envie o ditado para a classe tradutor.</span><span class="sxs-lookup"><span data-stu-id="7b942-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="7b942-410">Hospede um método que pode parar a captura de voz, se desejado.</span><span class="sxs-lookup"><span data-stu-id="7b942-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="7b942-411">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="7b942-411">To create this class:</span></span> 
1.  <span data-ttu-id="7b942-412">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="7b942-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="7b942-413">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > C# script**.</span><span class="sxs-lookup"><span data-stu-id="7b942-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="7b942-414">Nomeie o script *microphonemanager*.</span><span class="sxs-lookup"><span data-stu-id="7b942-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="7b942-415">Clique duas vezes no novo script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b942-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="7b942-416">Atualize os namespaces para ser o mesmo que o seguinte, na parte superior da classe *microphonemanager* :</span><span class="sxs-lookup"><span data-stu-id="7b942-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="7b942-417">Em seguida, adicione as seguintes variáveis dentro da classe *microphonemanager* :</span><span class="sxs-lookup"><span data-stu-id="7b942-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

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

6.  <span data-ttu-id="7b942-418">Agora, o código para os métodos *ativo ()* e *Iniciar ()* precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="7b942-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="7b942-419">Eles serão chamados quando a classe for inicializada:</span><span class="sxs-lookup"><span data-stu-id="7b942-419">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="7b942-420">Você pode *excluir* o método *Update ()* , pois essa classe não o usará.</span><span class="sxs-lookup"><span data-stu-id="7b942-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="7b942-421">Agora você precisa dos métodos que o aplicativo usa para iniciar e parar a captura de voz e passá-la para a classe *Tradutor* , que será criada em breve.</span><span class="sxs-lookup"><span data-stu-id="7b942-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="7b942-422">Copie o código a seguir e cole-o abaixo do método *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="7b942-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

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
    > <span data-ttu-id="7b942-423">Embora esse aplicativo não faça uso, o método *StopCapturingAudio ()* também foi fornecido aqui, caso você queira implementar a capacidade de interromper a captura de áudio em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b942-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="7b942-424">Agora você precisa adicionar um manipulador de ditado que será invocado quando a voz parar.</span><span class="sxs-lookup"><span data-stu-id="7b942-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="7b942-425">Esse método passará o texto ditado para a classe do *Tradutor* .</span><span class="sxs-lookup"><span data-stu-id="7b942-425">This method will then pass the dictated text to the *Translator* class.</span></span>

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

10. <span data-ttu-id="7b942-426">Certifique-se de salvar suas alterações no Visual Studio antes de retornar ao Unity.</span><span class="sxs-lookup"><span data-stu-id="7b942-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="7b942-427">Neste ponto, você observará um erro exibido no painel de *console do editor do Unity* ("o nome ' Tradutor ' não existe...").</span><span class="sxs-lookup"><span data-stu-id="7b942-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="7b942-428">Isso ocorre porque o código faz referência à classe do *Tradutor* , que será criada no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="7b942-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="7b942-429">Capítulo 7 – chamada para o serviço do Azure e do Tradutor</span><span class="sxs-lookup"><span data-stu-id="7b942-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="7b942-430">O último script que você precisa criar é a classe *Translator* .</span><span class="sxs-lookup"><span data-stu-id="7b942-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="7b942-431">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="7b942-431">This class is responsible for:</span></span>

-   <span data-ttu-id="7b942-432">Autenticando o aplicativo com o *Azure*, no Exchange para um **token de autenticação**.</span><span class="sxs-lookup"><span data-stu-id="7b942-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="7b942-433">Use o **token de autenticação** para enviar texto (recebido da classe *microphonemanager* ) a ser traduzido.</span><span class="sxs-lookup"><span data-stu-id="7b942-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="7b942-434">Receba o resultado traduzido e passe-o para a classe *Results* para ser visualizado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="7b942-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="7b942-435">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="7b942-435">To create this Class:</span></span> 
1.  <span data-ttu-id="7b942-436">Vá para a pasta **scripts** que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7b942-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="7b942-437">Clique com o botão direito do mouse no **painel Projeto**, **crie > C# script**.</span><span class="sxs-lookup"><span data-stu-id="7b942-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="7b942-438">Chame o *Tradutor*de script.</span><span class="sxs-lookup"><span data-stu-id="7b942-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="7b942-439">Clique duas vezes no novo script do *Tradutor* para abri-lo **com o Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7b942-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="7b942-440">Adicione os seguintes namespaces à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="7b942-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="7b942-441">Em seguida, adicione as seguintes variáveis dentro da classe *Translator* :</span><span class="sxs-lookup"><span data-stu-id="7b942-441">Then add the following variables inside the *Translator* class:</span></span>

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
    > - <span data-ttu-id="7b942-442">Os idiomas inseridos na **Enumeração** Languages são apenas exemplos.</span><span class="sxs-lookup"><span data-stu-id="7b942-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="7b942-443">Fique à vontade para adicionar mais se desejar; a [API dá suporte a mais de 60 idiomas](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (incluindo Klingon)!</span><span class="sxs-lookup"><span data-stu-id="7b942-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="7b942-444">Há uma [página mais interativa que abrange os idiomas disponíveis](https://www.microsoft.com/translator/business/languages/), embora esteja ciente de que a página só parece funcionar quando o idioma do site está definido como ' ' (e o site da Microsoft provavelmente será redirecionado para seu idioma nativo).</span><span class="sxs-lookup"><span data-stu-id="7b942-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to '' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="7b942-445">Você pode alterar o idioma do site na parte inferior da página ou alterando a URL.</span><span class="sxs-lookup"><span data-stu-id="7b942-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="7b942-446">O valor de **authorizationKey** , no trecho de código acima, deve ser a **chave** que você recebeu quando assinou o *API de tradução de texto do Azure*.</span><span class="sxs-lookup"><span data-stu-id="7b942-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="7b942-447">Isso foi abordado no [capítulo 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="7b942-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="7b942-448">Agora, o código para os métodos *ativo ()* e *Iniciar ()* precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="7b942-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="7b942-449">Nesse caso, o código fará uma chamada para o *Azure* usando a chave de autorização para obter um *token*.</span><span class="sxs-lookup"><span data-stu-id="7b942-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

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
    > <span data-ttu-id="7b942-450">O token expirará após 10 minutos.</span><span class="sxs-lookup"><span data-stu-id="7b942-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="7b942-451">Dependendo do cenário do seu aplicativo, talvez seja necessário fazer a mesma chamada de corrotina várias vezes.</span><span class="sxs-lookup"><span data-stu-id="7b942-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="7b942-452">A corrotina para obter o token é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="7b942-452">The coroutine to obtain the Token is the following:</span></span>

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
    > <span data-ttu-id="7b942-453">Se você editar o nome do método IEnumerator **GetTokenCoroutine ()** , precisará atualizar os valores de cadeia de caracteres de chamada *StartCoroutine* e *StopCoroutine* no código acima.</span><span class="sxs-lookup"><span data-stu-id="7b942-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="7b942-454">[De](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)acordo com a documentação do Unity, para interromper uma *corrotina*específica, você precisa usar o método de valor da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7b942-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="7b942-455">Em seguida, adicione a corrotina (com um método de fluxo de "suporte" logo abaixo) para obter a tradução do texto recebido pela classe *microphonemanager* .</span><span class="sxs-lookup"><span data-stu-id="7b942-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="7b942-456">Esse código cria uma cadeia de caracteres de consulta para enviar ao *API de tradução de texto do Azure*e, em seguida, usa a classe interna do Unity UnityWebRequest para fazer uma chamada "Get" para o ponto de extremidade com a cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="7b942-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="7b942-457">Em seguida, o resultado é usado para definir a tradução no seu objeto de resultados.</span><span class="sxs-lookup"><span data-stu-id="7b942-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="7b942-458">O código a seguir mostra a implementação:</span><span class="sxs-lookup"><span data-stu-id="7b942-458">The code below shows the implementation:</span></span>

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

10. <span data-ttu-id="7b942-459">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="7b942-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="7b942-460">Capítulo 8 – configurar a cena do Unity</span><span class="sxs-lookup"><span data-stu-id="7b942-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="7b942-461">De volta ao editor do Unity, clique e arraste a classe *Results* *da* pasta **scripts** para o objeto da **câmera principal** no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="7b942-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="7b942-462">Clique na **câmera principal** e examine o *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="7b942-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="7b942-463">Você observará que, no componente de *script* recém-adicionado, há quatro campos com valores vazios.</span><span class="sxs-lookup"><span data-stu-id="7b942-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="7b942-464">Essas são as referências de saída para as propriedades no código.</span><span class="sxs-lookup"><span data-stu-id="7b942-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="7b942-465">Arraste os objetos de **texto** apropriados do *painel hierarquia* para esses quatro slots, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="7b942-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![Atualizar referências de destino com valores especificados.](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="7b942-467">Em seguida, clique e arraste a classe *Tradutor* da pasta **scripts** para o objeto de **câmera principal** no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="7b942-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="7b942-468">Em seguida, clique e arraste a classe *microphonemanager* da pasta **scripts** para o objeto de **câmera principal** no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="7b942-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="7b942-469">Por fim, clique na **câmera principal** e examine o *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="7b942-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="7b942-470">Você observará que, no script que você arrastou, há duas caixas suspensas que permitirão que você defina os idiomas.</span><span class="sxs-lookup"><span data-stu-id="7b942-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![Verifique se os idiomas de tradução pretendidos são de entrada.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="7b942-472">Capítulo 9 – testar em realidade misturada</span><span class="sxs-lookup"><span data-stu-id="7b942-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="7b942-473">Neste ponto, você precisa testar se a cena foi implementada corretamente.</span><span class="sxs-lookup"><span data-stu-id="7b942-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="7b942-474">Certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="7b942-474">Ensure that:</span></span>

- <span data-ttu-id="7b942-475">Todas as configurações mencionadas no [capítulo 1](#chapter-1--the-azure-portal) estão definidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="7b942-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="7b942-476">Os *resultados*, o *Tradutor*e o *microfonemanager*, os scripts são anexados ao objeto da **câmera principal** .</span><span class="sxs-lookup"><span data-stu-id="7b942-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="7b942-477">Você colocou sua **chave** do serviço de *API de tradução de texto do Azure* dentro da variável **AuthorizationKey** dentro do script do *Tradutor* .</span><span class="sxs-lookup"><span data-stu-id="7b942-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="7b942-478">Todos os campos no *painel principal do Inspetor de câmera* são atribuídos corretamente.</span><span class="sxs-lookup"><span data-stu-id="7b942-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="7b942-479">O microfone está funcionando ao executar sua cena (caso contrário, verifique se o microfone anexado é o dispositivo *padrão* e se você o [configurou corretamente no Windows](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span><span class="sxs-lookup"><span data-stu-id="7b942-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="7b942-480">Você pode testar o headset de imersão pressionando o botão **reproduzir** no *Editor do Unity*.</span><span class="sxs-lookup"><span data-stu-id="7b942-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="7b942-481">O aplicativo deve estar funcionando por meio do headset de imersão anexado.</span><span class="sxs-lookup"><span data-stu-id="7b942-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="7b942-482">Se você vir um erro no console do Unity sobre a alteração do dispositivo de áudio padrão, a cena poderá não funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="7b942-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="7b942-483">Isso ocorre devido à maneira como o portal de realidade misturada lida com microfones internos para fones de ouvido que os têm.</span><span class="sxs-lookup"><span data-stu-id="7b942-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="7b942-484">Se você vir esse erro, simplesmente pare a cena e inicie-a novamente e as coisas devem funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="7b942-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="7b942-485">Capítulo 10 – criar a solução UWP e Sideload no computador local</span><span class="sxs-lookup"><span data-stu-id="7b942-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="7b942-486">Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.</span><span class="sxs-lookup"><span data-stu-id="7b942-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="7b942-487">Navegue até **configurações de compilação**: **arquivo > configurações de compilação...**</span><span class="sxs-lookup"><span data-stu-id="7b942-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="7b942-488">Na janela **configurações de compilação** , clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="7b942-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Compile a cena do Unity.](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="7b942-490">Se ainda não estiver, **os C# projetos de Unity**de tique.</span><span class="sxs-lookup"><span data-stu-id="7b942-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="7b942-491">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="7b942-491">Click **Build**.</span></span> <span data-ttu-id="7b942-492">O Unity iniciará uma janela *Explorador de arquivos* , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado.</span><span class="sxs-lookup"><span data-stu-id="7b942-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="7b942-493">Crie essa pasta agora e nomeie-a como *aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="7b942-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="7b942-494">Em seguida, com a pasta de *aplicativo* selecionada, pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="7b942-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="7b942-495">O Unity começará a criar seu projeto na pasta do *aplicativo* .</span><span class="sxs-lookup"><span data-stu-id="7b942-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="7b942-496">Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do *Explorador de arquivos* no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).</span><span class="sxs-lookup"><span data-stu-id="7b942-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="7b942-497">Capítulo 11 – implantar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7b942-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="7b942-498">Para implantar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7b942-498">To deploy your application:</span></span>

1.  <span data-ttu-id="7b942-499">Navegue até sua nova compilação do Unity (a pasta do *aplicativo* ) e abra o arquivo de solução com o *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="7b942-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="7b942-500">Na configuração da solução, selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="7b942-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="7b942-501">Na plataforma da solução, selecione **x86**, **computador local**.</span><span class="sxs-lookup"><span data-stu-id="7b942-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="7b942-502">Para o Microsoft HoloLens, você pode achar mais fácil definir isso como *computador remoto*, para que você não esteja vinculado ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="7b942-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="7b942-503">No entanto, também será necessário fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7b942-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="7b942-504">Conheça o **endereço IP** do seu HoloLens, que pode ser encontrado dentro das *configurações > rede & Internet > Wi-Fi > opções avançadas*; o IPv4 é o endereço que você deve usar.</span><span class="sxs-lookup"><span data-stu-id="7b942-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="7b942-505">Verificar se o modo **de** *desenvolvedor* está ativado; encontrado em *configurações > atualização & > de segurança para desenvolvedores*.</span><span class="sxs-lookup"><span data-stu-id="7b942-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="7b942-507">Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu PC.</span><span class="sxs-lookup"><span data-stu-id="7b942-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="7b942-508">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="7b942-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="7b942-509">Depois de iniciado, o aplicativo solicitará que você autorize o acesso ao microfone.</span><span class="sxs-lookup"><span data-stu-id="7b942-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="7b942-510">Certifique-se de clicar no botão **Sim** .</span><span class="sxs-lookup"><span data-stu-id="7b942-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="7b942-511">Agora você está pronto para começar a traduzir!</span><span class="sxs-lookup"><span data-stu-id="7b942-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="7b942-512">Seu aplicativo de API de tradução de texto concluído</span><span class="sxs-lookup"><span data-stu-id="7b942-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="7b942-513">Parabéns, você criou um aplicativo de realidade misturada que aproveita a API de texto de tradução do Azure para converter a fala em texto traduzido.</span><span class="sxs-lookup"><span data-stu-id="7b942-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![Produto final.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="7b942-515">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="7b942-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="7b942-516">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="7b942-516">Exercise 1</span></span>

<span data-ttu-id="7b942-517">Você pode adicionar a funcionalidade de conversão de texto em fala ao aplicativo para que o texto retornado seja falado?</span><span class="sxs-lookup"><span data-stu-id="7b942-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="7b942-518">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="7b942-518">Exercise 2</span></span>

<span data-ttu-id="7b942-519">Possibilitar que o usuário altere os idiomas de origem e saída (' de ' e ' para ') no próprio aplicativo, para que o aplicativo não precise ser recriado sempre que você quiser alterar os idiomas.</span><span class="sxs-lookup"><span data-stu-id="7b942-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
