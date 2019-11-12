---
title: Sr e Azure 303 – LUIS (reconhecimento de linguagem natural)
description: Conclua este curso para aprender a implementar o LUIS (serviço do Azure Reconhecimento vocal Intelligence) em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, serviço de inteligência de reconhecimento de linguagem, Luis, hololens, imersão, VR
ms.openlocfilehash: 9b3e4f081dc8a054d783246554f904a38f43f26c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926811"
---
>[!NOTE]
><span data-ttu-id="58bcc-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="58bcc-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="58bcc-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="58bcc-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="58bcc-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="58bcc-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="58bcc-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="58bcc-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="58bcc-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="58bcc-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="58bcc-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="58bcc-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="58bcc-110">Sr e Azure 303: LUIS (reconhecimento de linguagem natural)</span><span class="sxs-lookup"><span data-stu-id="58bcc-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="58bcc-111">Neste curso, você aprenderá a integrar o Reconhecimento vocal a um aplicativo de realidade misturada usando os serviços cognitivas do Azure, com o API de Reconhecimento Vocal.</span><span class="sxs-lookup"><span data-stu-id="58bcc-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![resultado do laboratório](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="58bcc-113">O *reconhecimento vocal (Luis)* é um serviço Microsoft Azure, que fornece aos aplicativos a capacidade de fazer o significado da entrada do usuário, como por meio da extração do que uma pessoa pode querer, em suas próprias palavras.</span><span class="sxs-lookup"><span data-stu-id="58bcc-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="58bcc-114">Isso é obtido por meio do aprendizado de máquina, que compreende e aprende as informações de entrada e, em seguida, pode responder com informações detalhadas e relevantes.</span><span class="sxs-lookup"><span data-stu-id="58bcc-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="58bcc-115">Para obter mais informações, visite a [página reconhecimento vocal do Azure (Luis)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span><span class="sxs-lookup"><span data-stu-id="58bcc-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="58bcc-116">Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada que poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="58bcc-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="58bcc-117">Capture a fala de entrada do usuário, usando o microfone anexado ao headset de imersão.</span><span class="sxs-lookup"><span data-stu-id="58bcc-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="58bcc-118">Enviar o ditado capturado do *serviço inteligente de reconhecimento vocal do Azure* (*Luis*).</span><span class="sxs-lookup"><span data-stu-id="58bcc-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="58bcc-119">Faça com que o LUIS extra o significado das informações de envio, que serão analisadas, e a tentativa de determinar a intenção da solicitação do usuário será feita.</span><span class="sxs-lookup"><span data-stu-id="58bcc-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="58bcc-120">O desenvolvimento incluirá a criação de um aplicativo em que o usuário poderá usar voz e/ou olhar para alterar o tamanho e a cor dos objetos na cena.</span><span class="sxs-lookup"><span data-stu-id="58bcc-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="58bcc-121">O uso de controladores de movimento não será abordado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="58bcc-122">Em seu aplicativo, cabe a você como você integrará os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="58bcc-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="58bcc-123">Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="58bcc-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="58bcc-124">É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="58bcc-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="58bcc-125">Esteja preparado para treinar o LUIS várias vezes, que é abordado no [capítulo 12](#chapter-12--improving-your-luis-service).</span><span class="sxs-lookup"><span data-stu-id="58bcc-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="58bcc-126">Você obterá resultados melhores, mais vezes o LUIS foi treinado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="58bcc-127">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="58bcc-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="58bcc-128">Course</span><span class="sxs-lookup"><span data-stu-id="58bcc-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="58bcc-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="58bcc-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="58bcc-130"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="58bcc-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="58bcc-131">Sr e Azure 303: LUIS (reconhecimento de linguagem natural)</span><span class="sxs-lookup"><span data-stu-id="58bcc-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="58bcc-132">✔️</span><span class="sxs-lookup"><span data-stu-id="58bcc-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="58bcc-133">✔️</span><span class="sxs-lookup"><span data-stu-id="58bcc-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="58bcc-134">Embora este curso se concentre principalmente em fones de ouvido (VR) de realidade mista do Windows, você também pode aplicar o que aprende neste curso ao Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="58bcc-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="58bcc-135">Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="58bcc-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="58bcc-136">Ao usar o HoloLens, você pode notar um eco durante a captura de voz.</span><span class="sxs-lookup"><span data-stu-id="58bcc-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58bcc-137">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="58bcc-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="58bcc-138">Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o.</span><span class="sxs-lookup"><span data-stu-id="58bcc-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="58bcc-139">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="58bcc-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="58bcc-140">Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="58bcc-141">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="58bcc-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="58bcc-142">Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)</span><span class="sxs-lookup"><span data-stu-id="58bcc-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="58bcc-143">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="58bcc-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="58bcc-144">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="58bcc-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="58bcc-145">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="58bcc-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="58bcc-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="58bcc-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="58bcc-147">Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="58bcc-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="58bcc-148">Um conjunto de fones de ouvido com um microfone interno (se o headset não tiver um MIC interno e alto-falantes)</span><span class="sxs-lookup"><span data-stu-id="58bcc-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="58bcc-149">Acesso à Internet para a instalação do Azure e recuperação LUIS</span><span class="sxs-lookup"><span data-stu-id="58bcc-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="58bcc-150">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="58bcc-150">Before you start</span></span>

1.  <span data-ttu-id="58bcc-151">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="58bcc-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="58bcc-152">Para permitir que o computador habilite o ditado, acesse **as configurações do Windows > privacidade > fala, digitando a tinta & digitar** e pressione o botão **ativar os serviços de fala e digitar sugestões**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="58bcc-153">O código neste tutorial permitirá que você registre a partir do conjunto de **dispositivos do microfone padrão** em seu computador.</span><span class="sxs-lookup"><span data-stu-id="58bcc-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="58bcc-154">Verifique se o dispositivo de microfone padrão está definido como aquele que você deseja usar para capturar sua voz.</span><span class="sxs-lookup"><span data-stu-id="58bcc-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="58bcc-155">Se o headset tiver um microfone interno, certifique-se de que a opção *"quando eu utilizo meu Headset, mude para MIC do headset"* esteja ativada nas configurações do *portal da realidade misturada* .</span><span class="sxs-lookup"><span data-stu-id="58bcc-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![Configurando o headset de imersão](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="58bcc-157">Capítulo 1 – configurar o portal do Azure</span><span class="sxs-lookup"><span data-stu-id="58bcc-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="58bcc-158">Para usar o serviço de *reconhecimento vocal* no Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="58bcc-159">Faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="58bcc-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="58bcc-160">Se você ainda não tiver uma conta do Azure, será necessário criar uma.</span><span class="sxs-lookup"><span data-stu-id="58bcc-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="58bcc-161">Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="58bcc-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="58bcc-162">Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure *reconhecimento vocal*e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![Criar recurso LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="58bcc-164">A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="58bcc-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="58bcc-165">A nova página à direita fornecerá uma descrição do serviço Reconhecimento vocal.</span><span class="sxs-lookup"><span data-stu-id="58bcc-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="58bcc-166">Na parte inferior esquerda desta página, selecione o botão **criar** para criar uma instância desse serviço.</span><span class="sxs-lookup"><span data-stu-id="58bcc-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![Criação de serviço LUIS-aviso legal](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="58bcc-168">Depois de clicar em criar:</span><span class="sxs-lookup"><span data-stu-id="58bcc-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="58bcc-169">Insira o **nome** desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="58bcc-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="58bcc-170">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="58bcc-171">Selecione o **tipo de preço** apropriado para você, se esta for a primeira vez que criar um *serviço Luis*, uma camada gratuita (chamada F0) deverá estar disponível para você.</span><span class="sxs-lookup"><span data-stu-id="58bcc-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="58bcc-172">A alocação gratuita deve ser mais do que suficiente para este curso.</span><span class="sxs-lookup"><span data-stu-id="58bcc-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="58bcc-173">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="58bcc-174">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="58bcc-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="58bcc-175">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="58bcc-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="58bcc-176">Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="58bcc-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="58bcc-177">Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="58bcc-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="58bcc-178">O local ideal seria na região em que o aplicativo seria executado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="58bcc-179">Alguns ativos do Azure só estão disponíveis em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="58bcc-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="58bcc-180">Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="58bcc-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="58bcc-181">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-181">Select **Create**.</span></span>

        ![Criar serviço LUIS-entrada do usuário](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="58bcc-183">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="58bcc-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="58bcc-184">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="58bcc-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![Nova imagem de notificação do Azure](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="58bcc-186">Clique na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="58bcc-186">Click on the notification to explore your new Service instance.</span></span>

    ![Notificação de criação de recursos bem-sucedida](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="58bcc-188">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="58bcc-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="58bcc-189">Você será levado à sua nova instância do serviço LUIS.</span><span class="sxs-lookup"><span data-stu-id="58bcc-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![Acessando chaves LUIS](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="58bcc-191">Neste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, o que é feito por meio do uso da chave de assinatura do serviço.</span><span class="sxs-lookup"><span data-stu-id="58bcc-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="58bcc-192">Na página *início rápido* , do serviço *API do Luis* , navegue até a primeira etapa, *pegue as chaves*e clique em **chaves** (você também pode fazer isso clicando nas teclas de hiperlink azul, localizadas no menu de navegação serviços, indicado pelo ícone de chave).</span><span class="sxs-lookup"><span data-stu-id="58bcc-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="58bcc-193">Isso revelará suas *chaves*de serviço.</span><span class="sxs-lookup"><span data-stu-id="58bcc-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="58bcc-194">Faça uma cópia de uma das chaves exibidas, pois você precisará dela posteriormente em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="58bcc-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="58bcc-195">Na página *serviço* , clique em *reconhecimento vocal portal* para ser redirecionado para a página da Web que você usará para criar seu novo serviço, dentro do aplicativo Luis.</span><span class="sxs-lookup"><span data-stu-id="58bcc-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="58bcc-196">Capítulo 2 – o portal de Reconhecimento vocal</span><span class="sxs-lookup"><span data-stu-id="58bcc-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="58bcc-197">Nesta seção, você aprenderá a criar um aplicativo LUIS no portal do LUIS.</span><span class="sxs-lookup"><span data-stu-id="58bcc-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="58bcc-198">Esteja ciente de que a configuração de *entidades*, *intenções*e *declarações* dentro deste capítulo é apenas a primeira etapa na criação do seu serviço Luis: você também precisará treinar novamente o serviço, várias vezes, para torná-lo mais preciso.</span><span class="sxs-lookup"><span data-stu-id="58bcc-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="58bcc-199">O novo treinamento do seu serviço é abordado no [último capítulo](#chapter-12--improving-your-luis-service) deste curso, portanto, certifique-se de concluí-lo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="58bcc-200">Ao atingir o *portal de reconhecimento vocal*, talvez seja necessário fazer logon, se você ainda não tiver, com as mesmas credenciais que o portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="58bcc-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![Página de logon do LUIS](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="58bcc-202">Se esta for a primeira vez que você usa o LUIS, você precisará rolar para baixo até a parte inferior da página de boas-vindas, para localizar e clicar no botão **criar aplicativo Luis** .</span><span class="sxs-lookup"><span data-stu-id="58bcc-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![Página criar aplicativo LUIS](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="58bcc-204">Depois de conectado, clique em **meus aplicativos** (se você não estiver na seção no momento).</span><span class="sxs-lookup"><span data-stu-id="58bcc-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="58bcc-205">Em seguida, você pode clicar em **criar novo aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-205">You can then click on **Create new app**.</span></span>

    ![LUIS-imagem de meus aplicativos](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="58bcc-207">Dê um *nome*ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="58bcc-208">Se seu aplicativo deve entender uma linguagem diferente do inglês, você deve alterar a *cultura* para o idioma apropriado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="58bcc-209">Aqui você também pode adicionar uma *Descrição* do seu novo aplicativo Luis.</span><span class="sxs-lookup"><span data-stu-id="58bcc-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS-criar um novo aplicativo](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="58bcc-211">Depois de pressionar **concluído**, você vai inserir a página de *compilação* do seu novo aplicativo *Luis* .</span><span class="sxs-lookup"><span data-stu-id="58bcc-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="58bcc-212">Há alguns conceitos importantes a serem compreendidos aqui:</span><span class="sxs-lookup"><span data-stu-id="58bcc-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="58bcc-213">*Intenção*, representa o método que será chamado após uma consulta do usuário.</span><span class="sxs-lookup"><span data-stu-id="58bcc-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="58bcc-214">Uma *intenção* pode ter uma ou mais *entidades*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="58bcc-215">*Entidade*, é um componente da consulta que descreve as informações relevantes para a *intenção*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="58bcc-216">*Declarações*, são exemplos de consultas fornecidas pelo desenvolvedor, que o Luis usará para se treinar.</span><span class="sxs-lookup"><span data-stu-id="58bcc-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="58bcc-217">Se esses conceitos não estiverem perfeitamente claros, não se preocupe, pois este curso os esclarecerá ainda mais neste capítulo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="58bcc-218">Você começará criando as *entidades* necessárias para compilar este curso.</span><span class="sxs-lookup"><span data-stu-id="58bcc-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="58bcc-219">No lado esquerdo da página, clique em *entidades*e, em seguida, clique em **criar nova entidade**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![Criar nova entidade](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="58bcc-221">Chame a nova *cor*da entidade, defina seu tipo como *simples*e pressione **concluído**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![Criar entidade-cor simples](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="58bcc-223">Repita esse processo para criar três (3) entidades mais simples chamadas:</span><span class="sxs-lookup"><span data-stu-id="58bcc-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="58bcc-224">*ampliar*</span><span class="sxs-lookup"><span data-stu-id="58bcc-224">*upsize*</span></span>
    -   <span data-ttu-id="58bcc-225">*diminuir*</span><span class="sxs-lookup"><span data-stu-id="58bcc-225">*downsize*</span></span>
    -   <span data-ttu-id="58bcc-226">*alvo*</span><span class="sxs-lookup"><span data-stu-id="58bcc-226">*target*</span></span>

<span data-ttu-id="58bcc-227">O resultado deve ser semelhante à imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="58bcc-227">The result should look like the image below:</span></span>

![Resultado da criação de entidade](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="58bcc-229">Neste ponto, você pode começar a criar *tentativas*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="58bcc-230">Não exclua a tentativa **nenhum** .</span><span class="sxs-lookup"><span data-stu-id="58bcc-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="58bcc-231">No lado esquerdo da página, clique em **tentativas**e, em seguida, clique em **criar nova tentativa**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![Criar novas tentativas](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="58bcc-233">Chame a nova *intenção* **ChangeObjectColor**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="58bcc-234">Esse nome de *intenção* é usado no código posteriormente neste curso, para obter melhores resultados, use esse nome exatamente como fornecido.</span><span class="sxs-lookup"><span data-stu-id="58bcc-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="58bcc-235">Depois de confirmar o nome, você será direcionado para a página de tentativas.</span><span class="sxs-lookup"><span data-stu-id="58bcc-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS – página de intenções](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="58bcc-237">Você observará que há uma caixa de texto solicitando que você digite 5 ou mais *declarações*diferentes.</span><span class="sxs-lookup"><span data-stu-id="58bcc-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="58bcc-238">LUIS converte todas as declarações em minúsculas.</span><span class="sxs-lookup"><span data-stu-id="58bcc-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="58bcc-239">Insira o seguinte *expressão* na caixa de texto superior (atualmente, com o tipo de texto *cerca de 5 exemplos...*</span><span class="sxs-lookup"><span data-stu-id="58bcc-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="58bcc-240">) e pressione **Enter**:</span><span class="sxs-lookup"><span data-stu-id="58bcc-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="58bcc-241">Você notará que o novo *expressão* aparecerá em uma lista abaixo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="58bcc-242">Seguindo o mesmo processo, insira os seis (6) declarações a seguir:</span><span class="sxs-lookup"><span data-stu-id="58bcc-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="58bcc-243">Para cada expressão que você criou, você deve identificar quais palavras devem ser usadas pelo LUIS como entidades.</span><span class="sxs-lookup"><span data-stu-id="58bcc-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="58bcc-244">Neste exemplo, você precisa rotular todas as cores como uma entidade de *cor* e toda a referência possível a um destino como uma entidade de *destino* .</span><span class="sxs-lookup"><span data-stu-id="58bcc-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="58bcc-245">Para fazer isso, tente clicar no *cilindro* de palavras na primeira expressão e selecionar *destino*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![Identificar destinos de expressão](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="58bcc-247">Agora, clique na palavra *vermelho* na primeira expressão e selecione *cor*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![Identificar entidades expressão](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="58bcc-249">Rotule a próxima linha também, onde o *cubo* deve ser um *destino*e *preto* deve ser uma *cor*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="58bcc-250">Observe também o uso das palavras *' this '* , *' it '* e *' this Object '* , que estamos fornecendo, por isso também há tipos de destino não específicos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="58bcc-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="58bcc-251">Repita o processo acima até que todos os declarações tenham as entidades rotuladas.</span><span class="sxs-lookup"><span data-stu-id="58bcc-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="58bcc-252">Consulte a imagem abaixo se precisar de ajuda.</span><span class="sxs-lookup"><span data-stu-id="58bcc-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="58bcc-253">Ao selecionar palavras para rotulá-las como entidades:</span><span class="sxs-lookup"><span data-stu-id="58bcc-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="58bcc-254">Para palavras únicas, basta clicar nelas.</span><span class="sxs-lookup"><span data-stu-id="58bcc-254">For single words just click them.</span></span>
    > - <span data-ttu-id="58bcc-255">Para um conjunto de duas ou mais palavras, clique no início e, em seguida, no final do conjunto.</span><span class="sxs-lookup"><span data-stu-id="58bcc-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="58bcc-256">Você pode usar o botão de alternância de *exibição de tokens* para alternar entre a **exibição de entidades/tokens**!</span><span class="sxs-lookup"><span data-stu-id="58bcc-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="58bcc-257">Os resultados devem ser mostrados nas imagens abaixo, mostrando a **exibição de entidades/tokens**:</span><span class="sxs-lookup"><span data-stu-id="58bcc-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![Exibições & entidades de tokens](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="58bcc-259">Neste ponto, pressione o botão **treinar** na parte superior direita da página e aguarde até que o pequeno indicador de ida e volta fique verde.</span><span class="sxs-lookup"><span data-stu-id="58bcc-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="58bcc-260">Isso indica que o LUIS foi treinado com êxito para reconhecer essa intenção.</span><span class="sxs-lookup"><span data-stu-id="58bcc-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![Treinar o LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="58bcc-262">Como um exercício para você, crie uma nova tentativa chamada **ChangeObjectSize**, usando as entidades *target*, *upsize*e *diminuir*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="58bcc-263">Seguindo o mesmo processo que a intenção anterior, insira as oito (8) declarações a seguir para alterar o *tamanho* :</span><span class="sxs-lookup"><span data-stu-id="58bcc-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. <span data-ttu-id="58bcc-264">O resultado deve ser semelhante ao mostrado na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="58bcc-264">The result should be like the one in the image below:</span></span>

    ![Configurar os tokens/entidades do ChangeObjectSize](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="58bcc-266">Depois que as tentativas, **ChangeObjectColor** e **ChangeObjectSize**forem criadas e treinadas, clique no botão **publicar** na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="58bcc-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![Publicar serviço LUIS](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="58bcc-268">Na página de *publicação* , você finalizará e publicará seu aplicativo Luis para que ele possa ser acessado pelo seu código.</span><span class="sxs-lookup"><span data-stu-id="58bcc-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="58bcc-269">Defina a lista suspensa *publicar* como **produção**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="58bcc-270">Defina o *fuso horário* para seu fuso horário.</span><span class="sxs-lookup"><span data-stu-id="58bcc-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="58bcc-271">Marque a caixa **incluir todas as pontuações de intenção prevista**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="58bcc-272">Clique em **publicar no slot de produção**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-272">Click on **Publish to Production Slot**.</span></span>

        ![Configurações de publicação](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="58bcc-274">Na seção *recursos e chaves*:</span><span class="sxs-lookup"><span data-stu-id="58bcc-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="58bcc-275">Selecione a região que você definiu para a instância de serviço no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="58bcc-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="58bcc-276">Você observará um elemento **Starter_Key** abaixo, ignorará-o.</span><span class="sxs-lookup"><span data-stu-id="58bcc-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="58bcc-277">Clique em **Adicionar chave** e insira a *chave* que você obteve no portal do Azure quando você criou sua instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="58bcc-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="58bcc-278">Se o Azure e o portal do LUIS estiverem conectados ao mesmo usuário, serão fornecidos menus suspensos para *nome do locatário*, nome da *assinatura*e a *chave* que você deseja usar (terá o mesmo nome fornecido anteriormente no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="58bcc-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="58bcc-279">Sob o *ponto de extremidade*, faça uma cópia do ponto de extremidade correspondente à chave que você inseriu, em breve, você o usará em seu código.</span><span class="sxs-lookup"><span data-stu-id="58bcc-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="58bcc-280">Capítulo 3 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="58bcc-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="58bcc-281">A seguir está uma configuração típica para o desenvolvimento com a realidade misturada e, como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="58bcc-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="58bcc-282">Abra o *Unity* e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-282">Open *Unity* and click **New**.</span></span> 

    ![Inicie o novo projeto do Unity.](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="58bcc-284">Agora será necessário fornecer um nome de projeto de Unity, inserir **MR_LUIS**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="58bcc-285">Verifique se o tipo de projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="58bcc-286">Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="58bcc-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="58bcc-287">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-287">Then, click **Create project**.</span></span>

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="58bcc-289">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="58bcc-290">Vá para editar preferências de > e, em seguida, na nova janela, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="58bcc-291">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="58bcc-292">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="58bcc-292">Close the **Preferences** window.</span></span>

    ![Atualize a preferência do editor de script.](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="58bcc-294">Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma para **plataforma universal do Windows**clicando no botão **alternar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="58bcc-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Janela de configurações de compilação, alterne a plataforma para UWP.](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="58bcc-296">Vá para **arquivo > configurações de compilação** e verifique se:</span><span class="sxs-lookup"><span data-stu-id="58bcc-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="58bcc-297">O **dispositivo de destino** está definido para **qualquer dispositivo**</span><span class="sxs-lookup"><span data-stu-id="58bcc-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="58bcc-298">Para o Microsoft HoloLens, defina o **dispositivo de destino** como *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="58bcc-299">O **tipo de compilação** está definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="58bcc-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="58bcc-300">O **SDK** está definido para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="58bcc-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="58bcc-301">A **versão do Visual Studio** está definida para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="58bcc-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="58bcc-302">**Compilar e executar** é definido como **computador local**</span><span class="sxs-lookup"><span data-stu-id="58bcc-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="58bcc-303">Salve a cena e adicione-a à compilação.</span><span class="sxs-lookup"><span data-stu-id="58bcc-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="58bcc-304">Faça isso selecionando **Adicionar abrir cenas**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="58bcc-305">Uma janela salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="58bcc-305">A save window will appear.</span></span>
        
            ![Clique no botão Adicionar cenas abertas](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="58bcc-307">Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Criar nova pasta de scripts](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="58bcc-309">Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo*:, digite **MR_LuisScene**e pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![Dê um nome à nova cena.](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="58bcc-311">As configurações restantes, em *configurações de compilação*, devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="58bcc-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="58bcc-312">Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra as configurações do Player.](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="58bcc-314">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="58bcc-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="58bcc-315">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="58bcc-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="58bcc-316">A **versão de tempo de execução de script** deve ser **estável** (.net 3,5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="58bcc-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="58bcc-317">O **back-end de script** deve ser **.net**</span><span class="sxs-lookup"><span data-stu-id="58bcc-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="58bcc-318">O **nível de compatibilidade da API** deve ser **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="58bcc-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Atualize outras configurações.](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="58bcc-320">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="58bcc-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="58bcc-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="58bcc-321">**InternetClient**</span></span>
        2. <span data-ttu-id="58bcc-322">**Phone**</span><span class="sxs-lookup"><span data-stu-id="58bcc-322">**Microphone**</span></span>

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="58bcc-324">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o **SDK do Windows Mixed Reality** foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Atualize as configurações de X R.](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="58bcc-326">De volta *às configurações de Build* , os projetos do  _C# Unity_ não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste.</span><span class="sxs-lookup"><span data-stu-id="58bcc-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="58bcc-327">Feche a janela configurações de compilação.</span><span class="sxs-lookup"><span data-stu-id="58bcc-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="58bcc-328">Salve sua cena e projeto (**arquivo > salvar cena/arquivo > salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="58bcc-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="58bcc-329">Capítulo 4 – criar a cena</span><span class="sxs-lookup"><span data-stu-id="58bcc-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="58bcc-330">Se você quiser ignorar o componente *de configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para baixar esse [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importe-o para seu projeto como um [pacote personalizado](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue no [capítulo 5](#chapter-5--create-the-microphonemanager-class).</span><span class="sxs-lookup"><span data-stu-id="58bcc-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="58bcc-331">Clique com o botão direito do mouse em uma área vazia do *painel hierarquia*, em **objeto 3D**, adicione um **plano**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![Crie um plano.](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="58bcc-333">Lembre-se de que, ao clicar com o botão direito do mouse na *hierarquia* novamente para criar mais objetos, se você ainda tiver o último objeto selecionado, o objeto selecionado será o pai do novo objeto.</span><span class="sxs-lookup"><span data-stu-id="58bcc-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="58bcc-334">Evite clicar em um espaço vazio dentro da hierarquia e clicar com o botão direito do mouse.</span><span class="sxs-lookup"><span data-stu-id="58bcc-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="58bcc-335">Repita o procedimento acima para adicionar os seguintes objetos:</span><span class="sxs-lookup"><span data-stu-id="58bcc-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="58bcc-336">*Esfera*</span><span class="sxs-lookup"><span data-stu-id="58bcc-336">*Sphere*</span></span>
    2. <span data-ttu-id="58bcc-337">*Tubo*</span><span class="sxs-lookup"><span data-stu-id="58bcc-337">*Cylinder*</span></span>
    3. <span data-ttu-id="58bcc-338">*Simples*</span><span class="sxs-lookup"><span data-stu-id="58bcc-338">*Cube*</span></span>
    4. <span data-ttu-id="58bcc-339">*Texto 3D*</span><span class="sxs-lookup"><span data-stu-id="58bcc-339">*3D Text*</span></span>

4.  <span data-ttu-id="58bcc-340">A *hierarquia* de cena resultante deve ser parecida com a da imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="58bcc-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![Configuração da hierarquia de cena.](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="58bcc-342">Clique com o botão esquerdo na **câmera principal** para selecioná-lo, examine o *painel Inspetor* . você verá o objeto Camera com todos os seus componentes.</span><span class="sxs-lookup"><span data-stu-id="58bcc-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="58bcc-343">Clique no botão **Adicionar componente** localizado na parte inferior do *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![Adicionar fonte de áudio](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="58bcc-345">Pesquise o componente chamado *fonte de áudio*, conforme mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="58bcc-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="58bcc-346">Além disso, verifique se o componente de *transformação* da câmera principal está definido como (0, 0, 0). isso pode ser feito pressionando o ícone de **engrenagem** ao lado do componente de *transformação* da câmera e selecionando **Redefinir**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="58bcc-347">O componente de *transformação* deve ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="58bcc-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="58bcc-348">A *posição* é definida como **0, 0,** 0.</span><span class="sxs-lookup"><span data-stu-id="58bcc-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="58bcc-349">A *rotação* está definida como **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="58bcc-350">Para o Microsoft HoloLens, você também precisará alterar o seguinte, que fazem parte do componente da **câmera** , que está em sua **câmera principal**:</span><span class="sxs-lookup"><span data-stu-id="58bcc-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="58bcc-351">**Limpar sinalizadores:** Cor sólida.</span><span class="sxs-lookup"><span data-stu-id="58bcc-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="58bcc-352">**Plano de fundo** ' Black, Alpha 0 ' – cor hexadecimal: #00000000.</span><span class="sxs-lookup"><span data-stu-id="58bcc-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="58bcc-353">Clique com o botão esquerdo do **plano** para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="58bcc-354">No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="58bcc-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="58bcc-355">Transformação- *posição*</span><span class="sxs-lookup"><span data-stu-id="58bcc-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="58bcc-356">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="58bcc-356">**X**</span></span> | <span data-ttu-id="58bcc-357">**Iar**</span><span class="sxs-lookup"><span data-stu-id="58bcc-357">**Y**</span></span>                  | <span data-ttu-id="58bcc-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="58bcc-358">**Z**</span></span> |
    | <span data-ttu-id="58bcc-359">0</span><span class="sxs-lookup"><span data-stu-id="58bcc-359">0</span></span>     | <span data-ttu-id="58bcc-360">-1</span><span class="sxs-lookup"><span data-stu-id="58bcc-360">-1</span></span>                     | <span data-ttu-id="58bcc-361">0</span><span class="sxs-lookup"><span data-stu-id="58bcc-361">0</span></span>     |


10. <span data-ttu-id="58bcc-362">Clique com o botão esquerdo do **círculo** para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="58bcc-363">No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="58bcc-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="58bcc-364">Transformação- *posição*</span><span class="sxs-lookup"><span data-stu-id="58bcc-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="58bcc-365">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="58bcc-365">**X**</span></span> | <span data-ttu-id="58bcc-366">**Iar**</span><span class="sxs-lookup"><span data-stu-id="58bcc-366">**Y**</span></span>                  | <span data-ttu-id="58bcc-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="58bcc-367">**Z**</span></span> |
    | <span data-ttu-id="58bcc-368">2</span><span class="sxs-lookup"><span data-stu-id="58bcc-368">2</span></span>     | <span data-ttu-id="58bcc-369">1</span><span class="sxs-lookup"><span data-stu-id="58bcc-369">1</span></span>                      | <span data-ttu-id="58bcc-370">2</span><span class="sxs-lookup"><span data-stu-id="58bcc-370">2</span></span>     |

11. <span data-ttu-id="58bcc-371">Clique com o botão esquerdo do **cilindro** para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="58bcc-372">No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="58bcc-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="58bcc-373">Transformação- *posição*</span><span class="sxs-lookup"><span data-stu-id="58bcc-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="58bcc-374">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="58bcc-374">**X**</span></span> | <span data-ttu-id="58bcc-375">**Iar**</span><span class="sxs-lookup"><span data-stu-id="58bcc-375">**Y**</span></span>                  | <span data-ttu-id="58bcc-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="58bcc-376">**Z**</span></span> |
    | <span data-ttu-id="58bcc-377">-2</span><span class="sxs-lookup"><span data-stu-id="58bcc-377">-2</span></span>    | <span data-ttu-id="58bcc-378">1</span><span class="sxs-lookup"><span data-stu-id="58bcc-378">1</span></span>                      | <span data-ttu-id="58bcc-379">2</span><span class="sxs-lookup"><span data-stu-id="58bcc-379">2</span></span>     |

12. <span data-ttu-id="58bcc-380">Clique com o botão esquerdo do **cubo** para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="58bcc-381">No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="58bcc-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="58bcc-382">Transformação- *posição*</span><span class="sxs-lookup"><span data-stu-id="58bcc-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="58bcc-383">Transformação- *rotação*</span><span class="sxs-lookup"><span data-stu-id="58bcc-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="58bcc-384">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="58bcc-384">**X**</span></span> | <span data-ttu-id="58bcc-385">**Iar**</span><span class="sxs-lookup"><span data-stu-id="58bcc-385">**Y**</span></span>                   | <span data-ttu-id="58bcc-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="58bcc-386">**Z**</span></span> |  \| | <span data-ttu-id="58bcc-387">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="58bcc-387">**X**</span></span> | <span data-ttu-id="58bcc-388">**Iar**</span><span class="sxs-lookup"><span data-stu-id="58bcc-388">**Y**</span></span>                  | <span data-ttu-id="58bcc-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="58bcc-389">**Z**</span></span> |
    | <span data-ttu-id="58bcc-390">0</span><span class="sxs-lookup"><span data-stu-id="58bcc-390">0</span></span>     | <span data-ttu-id="58bcc-391">1</span><span class="sxs-lookup"><span data-stu-id="58bcc-391">1</span></span>                       | <span data-ttu-id="58bcc-392">추가를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58bcc-392">4</span></span>     |  \| | <span data-ttu-id="58bcc-393">45</span><span class="sxs-lookup"><span data-stu-id="58bcc-393">45</span></span>    | <span data-ttu-id="58bcc-394">45</span><span class="sxs-lookup"><span data-stu-id="58bcc-394">45</span></span>                     | <span data-ttu-id="58bcc-395">0</span><span class="sxs-lookup"><span data-stu-id="58bcc-395">0</span></span>     | 

13. <span data-ttu-id="58bcc-396">Clique no botão esquerdo do novo objeto de **texto** para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="58bcc-397">No *painel Inspetor* , defina o componente *transformação* com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="58bcc-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="58bcc-398">Transformação- *posição*</span><span class="sxs-lookup"><span data-stu-id="58bcc-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="58bcc-399">Transformar em *escala*</span><span class="sxs-lookup"><span data-stu-id="58bcc-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="58bcc-400">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="58bcc-400">**X**</span></span> | <span data-ttu-id="58bcc-401">**Iar**</span><span class="sxs-lookup"><span data-stu-id="58bcc-401">**Y**</span></span>                  | <span data-ttu-id="58bcc-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="58bcc-402">**Z**</span></span> |  \| | <span data-ttu-id="58bcc-403">**W.x.y.**</span><span class="sxs-lookup"><span data-stu-id="58bcc-403">**X**</span></span> | <span data-ttu-id="58bcc-404">**Iar**</span><span class="sxs-lookup"><span data-stu-id="58bcc-404">**Y**</span></span>               | <span data-ttu-id="58bcc-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="58bcc-405">**Z**</span></span> |
    | <span data-ttu-id="58bcc-406">-2</span><span class="sxs-lookup"><span data-stu-id="58bcc-406">-2</span></span>    | <span data-ttu-id="58bcc-407">6</span><span class="sxs-lookup"><span data-stu-id="58bcc-407">6</span></span>                      | <span data-ttu-id="58bcc-408">9</span><span class="sxs-lookup"><span data-stu-id="58bcc-408">9</span></span>     |  \| | <span data-ttu-id="58bcc-409">0,1</span><span class="sxs-lookup"><span data-stu-id="58bcc-409">0.1</span></span>   | <span data-ttu-id="58bcc-410">0,1</span><span class="sxs-lookup"><span data-stu-id="58bcc-410">0.1</span></span>                 | <span data-ttu-id="58bcc-411">0,1</span><span class="sxs-lookup"><span data-stu-id="58bcc-411">0.1</span></span>   | 

14. <span data-ttu-id="58bcc-412">Altere o **tamanho da fonte** no componente de malha de **texto** para **50**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="58bcc-413">Altere o *nome* do objeto de **malha de texto** para texto de **ditado**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![Criar objeto de texto 3D](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="58bcc-415">A estrutura do painel de hierarquia agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="58bcc-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![malha de texto na exibição de cena](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="58bcc-417">A cena final deve ser parecida com a imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="58bcc-417">The final scene should look like the image below:</span></span>

    ![A exibição de cena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="58bcc-419">Capítulo 5 – criar a classe microphonemanager</span><span class="sxs-lookup"><span data-stu-id="58bcc-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="58bcc-420">O primeiro script que você pretende criar é a classe *microphonemanager* .</span><span class="sxs-lookup"><span data-stu-id="58bcc-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="58bcc-421">Depois disso, você criará o *LuisManager*, a classe de *comportamentos* e, por fim, a classe *olhar* (fique à vontade para criar todos eles agora, embora ele seja coberto à medida que você atingir cada capítulo).</span><span class="sxs-lookup"><span data-stu-id="58bcc-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="58bcc-422">A classe *microphonemanager* é responsável por:</span><span class="sxs-lookup"><span data-stu-id="58bcc-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="58bcc-423">Detectando o dispositivo de gravação conectado ao headset ou ao computador (o que for o padrão).</span><span class="sxs-lookup"><span data-stu-id="58bcc-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="58bcc-424">Capture o áudio (voz) e use o ditado para armazená-lo como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="58bcc-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="58bcc-425">Depois que a voz for pausada, envie o ditado para a classe *LuisManager* .</span><span class="sxs-lookup"><span data-stu-id="58bcc-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="58bcc-426">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="58bcc-426">To create this class:</span></span> 

1.  <span data-ttu-id="58bcc-427">Clique com o botão direito do mouse no *painel Projeto*, **crie > pasta**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="58bcc-428">Chame os **scripts**da pasta.</span><span class="sxs-lookup"><span data-stu-id="58bcc-428">Call the folder **Scripts**.</span></span> 

    ![Criar pasta de scripts.](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="58bcc-430">Com a pasta **scripts** criada, clique duas vezes nela para abrir.</span><span class="sxs-lookup"><span data-stu-id="58bcc-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="58bcc-431">Em seguida, dentro dessa pasta, clique com o botão direito do mouse em **criar > C# script**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="58bcc-432">Nomeie o script *microphonemanager*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="58bcc-433">Clique duas vezes em *microfonemanager* para abri-lo com o *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="58bcc-434">Adicione os seguintes namespaces à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="58bcc-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="58bcc-435">Em seguida, adicione as seguintes variáveis dentro da classe *microphonemanager* :</span><span class="sxs-lookup"><span data-stu-id="58bcc-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="58bcc-436">O código para os métodos *ativo ()* e *Iniciar ()* agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="58bcc-437">Eles serão chamados quando a classe for inicializada:</span><span class="sxs-lookup"><span data-stu-id="58bcc-437">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  <span data-ttu-id="58bcc-438">Agora você precisa do método que o aplicativo usa para iniciar e parar a captura de voz e passá-la para a classe *LuisManager* , que será criada em breve.</span><span class="sxs-lookup"><span data-stu-id="58bcc-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  <span data-ttu-id="58bcc-439">Adicione um *manipulador de ditado* que será invocado quando a voz pausar.</span><span class="sxs-lookup"><span data-stu-id="58bcc-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="58bcc-440">Esse método passará o texto do ditado para a classe *LuisManager* .</span><span class="sxs-lookup"><span data-stu-id="58bcc-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="58bcc-441">Exclua o método *Update ()* , pois essa classe não o usará.</span><span class="sxs-lookup"><span data-stu-id="58bcc-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="58bcc-442">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="58bcc-443">Neste ponto, você observará um erro exibido no *painel de console do editor do Unity*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="58bcc-444">Isso ocorre porque o código faz referência à classe *LuisManager* , que você criará no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="58bcc-445">Capítulo 6 – criar a classe LUISManager</span><span class="sxs-lookup"><span data-stu-id="58bcc-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="58bcc-446">É hora de criar a classe *LuisManager* , que fará a chamada para o serviço Luis do Azure.</span><span class="sxs-lookup"><span data-stu-id="58bcc-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="58bcc-447">A finalidade dessa classe é receber o texto do ditado da classe *microphonemanager* e enviá-lo para o *API de reconhecimento vocal do Azure* a ser analisado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="58bcc-448">Essa classe desserializará a resposta *JSON* e chamará os métodos apropriados da classe de *comportamentos* para disparar uma ação.</span><span class="sxs-lookup"><span data-stu-id="58bcc-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="58bcc-449">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="58bcc-449">To create this class:</span></span> 

1.  <span data-ttu-id="58bcc-450">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="58bcc-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="58bcc-451">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > C# script**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="58bcc-452">Nomeie o script *LuisManager*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="58bcc-453">Clique duas vezes no script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="58bcc-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="58bcc-454">Adicione os seguintes namespaces à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="58bcc-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="58bcc-455">Você começará criando três classes **dentro** da classe *LuisManager* (dentro do mesmo arquivo de script, acima do método *Start ()* ) que representará a resposta JSON desserializada do Azure.</span><span class="sxs-lookup"><span data-stu-id="58bcc-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  <span data-ttu-id="58bcc-456">Em seguida, adicione as seguintes variáveis dentro da classe *LuisManager* :</span><span class="sxs-lookup"><span data-stu-id="58bcc-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="58bcc-457">Certifique-se de colocar seu ponto de extremidade do LUIS agora (que você terá do seu portal do LUIS).</span><span class="sxs-lookup"><span data-stu-id="58bcc-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="58bcc-458">O código para o método *ativo ()* agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="58bcc-459">Esse método será chamado quando a classe inicializar:</span><span class="sxs-lookup"><span data-stu-id="58bcc-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="58bcc-460">Agora você precisa dos métodos que esse aplicativo usa para enviar o ditado recebido da classe *microphonemanager* para *Luis*e, em seguida, receber e desserializar a resposta.</span><span class="sxs-lookup"><span data-stu-id="58bcc-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="58bcc-461">Depois que o valor da intenção e as entidades associadas forem determinados, eles serão passados para a instância da classe de *comportamentos* para disparar a ação pretendida.</span><span class="sxs-lookup"><span data-stu-id="58bcc-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. <span data-ttu-id="58bcc-462">Crie um novo método chamado *AnalyseResponseElements ()* que lerá o *AnalysedQuery* resultante e determine as entidades.</span><span class="sxs-lookup"><span data-stu-id="58bcc-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="58bcc-463">Depois que essas entidades forem determinadas, elas serão passadas para a instância da classe de *comportamentos* a ser usada nas ações.</span><span class="sxs-lookup"><span data-stu-id="58bcc-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="58bcc-464">Exclua os métodos *Start ()* e *Update ()* , pois essa classe não os usará.</span><span class="sxs-lookup"><span data-stu-id="58bcc-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="58bcc-465">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="58bcc-466">Neste ponto, você observará que vários erros aparecem no *painel de console do editor do Unity*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="58bcc-467">Isso ocorre porque o código faz referência à classe de *comportamentos* que você criará no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="58bcc-468">Capítulo 7 – criar a classe de comportamentos</span><span class="sxs-lookup"><span data-stu-id="58bcc-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="58bcc-469">A classe de *comportamentos* irá disparar as ações usando as entidades fornecidas pela classe *LuisManager* .</span><span class="sxs-lookup"><span data-stu-id="58bcc-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="58bcc-470">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="58bcc-470">To create this class:</span></span> 

1.  <span data-ttu-id="58bcc-471">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="58bcc-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="58bcc-472">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > C# script**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="58bcc-473">Nomeie os *comportamentos*do script.</span><span class="sxs-lookup"><span data-stu-id="58bcc-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="58bcc-474">Clique duas vezes no script para abri-lo com o *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="58bcc-475">Em seguida, adicione as seguintes variáveis dentro da classe de *comportamentos* :</span><span class="sxs-lookup"><span data-stu-id="58bcc-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="58bcc-476">Adicione o código do método *ativo ()* .</span><span class="sxs-lookup"><span data-stu-id="58bcc-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="58bcc-477">Esse método será chamado quando a classe inicializar:</span><span class="sxs-lookup"><span data-stu-id="58bcc-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="58bcc-478">Os métodos a seguir são chamados pela classe *LuisManager* (que você criou anteriormente) para determinar qual objeto é o destino da consulta e, em seguida, disparar a ação apropriada.</span><span class="sxs-lookup"><span data-stu-id="58bcc-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  <span data-ttu-id="58bcc-479">Adicione o método *FindTarget ()* para determinar qual *Gameobjects* é o destino da tentativa atual.</span><span class="sxs-lookup"><span data-stu-id="58bcc-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="58bcc-480">Esse método padroniza o destino para o *gameobject* como "gazed" se nenhum destino explícito for definido nas entidades.</span><span class="sxs-lookup"><span data-stu-id="58bcc-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="58bcc-481">Exclua os métodos *Start ()* e *Update ()* , pois essa classe não os usará.</span><span class="sxs-lookup"><span data-stu-id="58bcc-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="58bcc-482">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="58bcc-483">Capítulo 8 – criar a classe olhar</span><span class="sxs-lookup"><span data-stu-id="58bcc-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="58bcc-484">A última classe que será necessária para concluir esse aplicativo é a classe *olhar* .</span><span class="sxs-lookup"><span data-stu-id="58bcc-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="58bcc-485">Essa classe atualiza a referência ao *gameobject* no momento no foco visual do usuário.</span><span class="sxs-lookup"><span data-stu-id="58bcc-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="58bcc-486">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="58bcc-486">To create this Class:</span></span> 

1.  <span data-ttu-id="58bcc-487">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="58bcc-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="58bcc-488">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > C# script**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="58bcc-489">Nomeie o script *olhar*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="58bcc-490">Clique duas vezes no script para abri-lo com o *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="58bcc-491">Insira o seguinte código para esta classe:</span><span class="sxs-lookup"><span data-stu-id="58bcc-491">Insert the following code for this class:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  <span data-ttu-id="58bcc-492">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="58bcc-493">Capítulo 9 – concluindo a configuração da cena</span><span class="sxs-lookup"><span data-stu-id="58bcc-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="58bcc-494">Para concluir a configuração da cena, arraste cada script que você criou da pasta scripts para o objeto da **câmera principal** no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="58bcc-495">Selecione a **câmera principal** e examine o *painel Inspetor*, você deve ser capaz de ver cada script que você anexou e observará que há parâmetros em cada script que ainda devem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="58bcc-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![Definindo os destinos de referência da câmera.](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="58bcc-497">Para definir esses parâmetros corretamente, siga estas instruções:</span><span class="sxs-lookup"><span data-stu-id="58bcc-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="58bcc-498">*Microfonemanager*:</span><span class="sxs-lookup"><span data-stu-id="58bcc-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="58bcc-499">No *painel hierarquia*, arraste o objeto de **texto ditado** para a caixa valor do parâmetro **texto do ditado** .</span><span class="sxs-lookup"><span data-stu-id="58bcc-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="58bcc-500">*Comportamentos*, no *painel hierarquia*:</span><span class="sxs-lookup"><span data-stu-id="58bcc-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="58bcc-501">Arraste o objeto de **esfera** para a caixa destino de referência de *esfera* .</span><span class="sxs-lookup"><span data-stu-id="58bcc-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="58bcc-502">Arraste o **cilindro** para a caixa destino de referência do *cilindro* .</span><span class="sxs-lookup"><span data-stu-id="58bcc-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="58bcc-503">Arraste o **cubo** para a caixa destino de referência do *cubo* .</span><span class="sxs-lookup"><span data-stu-id="58bcc-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="58bcc-504">*Olhar*:</span><span class="sxs-lookup"><span data-stu-id="58bcc-504">*Gaze*:</span></span>

        - <span data-ttu-id="58bcc-505">Defina a *distância máxima olhar* como **300** (se ainda não estiver).</span><span class="sxs-lookup"><span data-stu-id="58bcc-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="58bcc-506">O resultado deve ser semelhante à imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="58bcc-506">The result should look like the image below:</span></span>

    ![Mostrando os destinos de referência da câmera, agora definido.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="58bcc-508">Capítulo 10 – testar no editor do Unity</span><span class="sxs-lookup"><span data-stu-id="58bcc-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="58bcc-509">Teste se a configuração de cena está implementada corretamente.</span><span class="sxs-lookup"><span data-stu-id="58bcc-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="58bcc-510">Certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="58bcc-510">Ensure that:</span></span>

-   <span data-ttu-id="58bcc-511">Todos os scripts são anexados ao objeto da **câmera principal** .</span><span class="sxs-lookup"><span data-stu-id="58bcc-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="58bcc-512">Todos os campos no *painel principal do Inspetor de câmera* são atribuídos corretamente.</span><span class="sxs-lookup"><span data-stu-id="58bcc-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="58bcc-513">Pressione o botão **reproduzir** no *Editor do Unity*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="58bcc-514">O aplicativo deve estar em execução no headset de imersão anexado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="58bcc-515">Experimente alguns declarações, como:</span><span class="sxs-lookup"><span data-stu-id="58bcc-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="58bcc-516">Se você vir um erro no console do Unity sobre a alteração do dispositivo de áudio padrão, a cena poderá não funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="58bcc-517">Isso ocorre devido à maneira como o portal de realidade misturada lida com microfones internos para fones de ouvido que os têm.</span><span class="sxs-lookup"><span data-stu-id="58bcc-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="58bcc-518">Se você vir esse erro, simplesmente pare a cena e inicie-a novamente e as coisas devem funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="58bcc-519">Capítulo 11 – criar e sideloadr a solução UWP</span><span class="sxs-lookup"><span data-stu-id="58bcc-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="58bcc-520">Depois de garantir que o aplicativo está funcionando no editor do Unity, você estará pronto para compilar e implantar.</span><span class="sxs-lookup"><span data-stu-id="58bcc-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="58bcc-521">Para compilar:</span><span class="sxs-lookup"><span data-stu-id="58bcc-521">To Build:</span></span>

1.  <span data-ttu-id="58bcc-522">Salve a cena atual clicando em **arquivo > salvar**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="58bcc-523">Vá para **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="58bcc-524">Marque a caixa chamada **projetos C# do Unity** (útil para ver e depurar seu código assim que o projeto UWP for criado.</span><span class="sxs-lookup"><span data-stu-id="58bcc-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="58bcc-525">Clique em **Adicionar e abrir cenas**e em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![Janela de configurações de compilação](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="58bcc-527">Você será solicitado a selecionar a pasta na qual deseja criar a solução.</span><span class="sxs-lookup"><span data-stu-id="58bcc-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="58bcc-528">Crie uma pasta *Builds* e dentro dessa pasta crie outra pasta com um nome apropriado de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="58bcc-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="58bcc-529">Clique em **Selecionar pasta** para iniciar a compilação nesse local.</span><span class="sxs-lookup"><span data-stu-id="58bcc-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="58bcc-530">![criar a pasta builds](images/AzureLabs-Lab3-44.png)
    ![selecionar a pasta builds](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="58bcc-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="58bcc-531">Depois de concluir a compilação do Unity (pode levar algum tempo), ele deve abrir uma janela do **Explorador de arquivos** no local de sua compilação.</span><span class="sxs-lookup"><span data-stu-id="58bcc-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="58bcc-532">Para implantar no computador local:</span><span class="sxs-lookup"><span data-stu-id="58bcc-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="58bcc-533">No *Visual Studio*, abra o arquivo de solução que foi criado no [capítulo anterior](#chapter-10--test-in-the-unity-editor).</span><span class="sxs-lookup"><span data-stu-id="58bcc-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="58bcc-534">Na **plataforma da solução**, selecione **x86**, **computador local**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="58bcc-535">Na **configuração da solução** , selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="58bcc-536">Para o Microsoft HoloLens, você pode achar mais fácil definir isso como *computador remoto*, para que você não esteja vinculado ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="58bcc-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="58bcc-537">No entanto, também será necessário fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="58bcc-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="58bcc-538">Conheça o **endereço IP** do seu HoloLens, que pode ser encontrado dentro das *configurações > rede & Internet > Wi-Fi > opções avançadas*; o IPv4 é o endereço que você deve usar.</span><span class="sxs-lookup"><span data-stu-id="58bcc-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="58bcc-539">Verificar se o modo **de** **desenvolvedor** está ativado; encontrado em *configurações > atualização & > de segurança para desenvolvedores*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Implantar aplicativo](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="58bcc-541">Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="58bcc-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="58bcc-542">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="58bcc-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="58bcc-543">Depois de iniciado, o aplicativo solicitará que você autorize o acesso ao _microfone_.</span><span class="sxs-lookup"><span data-stu-id="58bcc-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="58bcc-544">Use os *controladores de movimento*ou a *entrada de voz*ou o *teclado* para pressionar o botão **Sim** .</span><span class="sxs-lookup"><span data-stu-id="58bcc-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="58bcc-545">Capítulo 12 – melhorando seu serviço LUIS</span><span class="sxs-lookup"><span data-stu-id="58bcc-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="58bcc-546">Este capítulo é incrivelmente importante e pode precisar ser iterado várias vezes, pois isso ajudará a melhorar a precisão do seu serviço LUIS: Certifique-se de concluir isso.</span><span class="sxs-lookup"><span data-stu-id="58bcc-546">This chapter is incredibly important, and may need to be iterated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="58bcc-547">Para melhorar o nível de compreensão fornecido pelo LUIS, você precisa capturar novos declarações e usá-los para treinar novamente seu aplicativo LUIS.</span><span class="sxs-lookup"><span data-stu-id="58bcc-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="58bcc-548">Por exemplo, você pode ter treinado LUIS para entender "aumentar" e "upsizing", mas não iria querer que seu aplicativo também entenda palavras como "ampliar"?</span><span class="sxs-lookup"><span data-stu-id="58bcc-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="58bcc-549">Depois de usar seu aplicativo algumas vezes, tudo o que você disse será coletado pelo LUIS e disponível no PORTAL do LUIS.</span><span class="sxs-lookup"><span data-stu-id="58bcc-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="58bcc-550">Acesse o aplicativo do portal seguindo este [link](https://www.luis.ai/home)e faça logon.</span><span class="sxs-lookup"><span data-stu-id="58bcc-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="58bcc-551">Depois de fazer logon com suas credenciais do MS, clique no *nome do aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="58bcc-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="58bcc-552">Clique no botão **examinar ponto de extremidade declarações** à esquerda da página.</span><span class="sxs-lookup"><span data-stu-id="58bcc-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![Examinar declarações](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="58bcc-554">Você verá uma lista dos declarações que foram enviados ao LUIS pelo seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="58bcc-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![Lista de declarações](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="58bcc-556">Você observará algumas *entidades*realçadas.</span><span class="sxs-lookup"><span data-stu-id="58bcc-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="58bcc-557">Ao focalizar cada palavra realçada, você pode examinar cada expressão e determinar qual entidade foi reconhecida corretamente, quais entidades estão erradas e quais entidades estão ausentes.</span><span class="sxs-lookup"><span data-stu-id="58bcc-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="58bcc-558">No exemplo acima, foi detectado que a palavra "Spear" foi realçada como um destino, portanto, é necessário corrigir o erro, o que é feito ao passar pela palavra com o mouse e clicar em **remover rótulo**.</span><span class="sxs-lookup"><span data-stu-id="58bcc-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="58bcc-559">![verificar declarações](images/AzureLabs-Lab3-49.png)
![remover imagem de rótulo](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="58bcc-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="58bcc-560">Se encontrar declarações que estejam completamente errados, você poderá excluí-los usando o botão **excluir** no lado direito da tela.</span><span class="sxs-lookup"><span data-stu-id="58bcc-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![Excluir declarações incorretos](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="58bcc-562">Ou se sentir que o LUIS interpretou o expressão corretamente, você poderá validar sua compreensão usando o botão **Adicionar à intenção alinhada** .</span><span class="sxs-lookup"><span data-stu-id="58bcc-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![Adicionar à intenção alinhada](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="58bcc-564">Depois de classificar todos os declarações exibidos, tente e recarregue a página para ver se há mais informações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="58bcc-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="58bcc-565">É muito importante repetir esse processo tantas vezes quanto possível para melhorar a compreensão do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="58bcc-566">**Divertir-se!**</span><span class="sxs-lookup"><span data-stu-id="58bcc-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="58bcc-567">Seu aplicativo LUIS Integrated concluído</span><span class="sxs-lookup"><span data-stu-id="58bcc-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="58bcc-568">Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço do Azure Reconhecimento vocal Intelligence, para entender o que um usuário diz e agir sobre essas informações.</span><span class="sxs-lookup"><span data-stu-id="58bcc-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![resultado do laboratório](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="58bcc-570">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="58bcc-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="58bcc-571">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="58bcc-571">Exercise 1</span></span>

<span data-ttu-id="58bcc-572">Ao usar esse aplicativo, você pode notar que, se olhar no objeto Floor e pedir para alterar sua cor, ele fará isso.</span><span class="sxs-lookup"><span data-stu-id="58bcc-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="58bcc-573">Você pode solucionar como impedir que seu aplicativo altere a cor do piso?</span><span class="sxs-lookup"><span data-stu-id="58bcc-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="58bcc-574">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="58bcc-574">Exercise 2</span></span>

<span data-ttu-id="58bcc-575">Tente estender os recursos de LUIS e de aplicativo, adicionando funcionalidades adicionais para objetos em cena; como exemplo, crie novos objetos no ponto de acesso olhar, dependendo do que o usuário diz e, em seguida, use esses objetos junto com os objetos de cena atuais, com os comandos existentes.</span><span class="sxs-lookup"><span data-stu-id="58bcc-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
