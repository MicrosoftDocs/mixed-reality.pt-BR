---
title: MR e Azure 303 - (LUIS) de compreensão de idioma Natural
description: Conclua este curso para aprender a implementar o Azure Language Intelligence Service Luis (reconhecimento vocal) dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, serviço de inteligência de reconhecimento vocal, luis, hololens, vr de imersão,
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590557"
---
>[!NOTE]
><span data-ttu-id="7ceb1-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7ceb1-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7ceb1-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7ceb1-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7ceb1-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7ceb1-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="7ceb1-110">MR e o Azure 303: Compreensão de idioma natural (LUIS)</span><span class="sxs-lookup"><span data-stu-id="7ceb1-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="7ceb1-111">Neste curso, você aprenderá como integrar a compreensão de idioma em um aplicativo de realidade misturada usando serviços Cognitivos do Azure, com a API de reconhecimento vocal.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![resultado de laboratório](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="7ceb1-113">*Compreensão de idioma (LUIS)* é um serviço do Microsoft Azure, que fornece aos aplicativos com capacidade de fazer o significado fora de entrada do usuário, como por meio de extrair o que uma pessoa poderá, em suas próprias palavras.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="7ceb1-114">Isso é feito por meio do machine learning, que compreende e aprende as informações de entrada e, em seguida, pode responder com informações relevantes, detalhadas.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="7ceb1-115">Para obter mais informações, visite o [página do Azure (Luis reconhecimento vocal)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="7ceb1-116">Com a conclusão deste curso, você terá um aplicativo de imersivo headset de realidade misturada que serão capaz de fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="7ceb1-117">Captura de fala de entrada de usuário, usando o microfone conectado para o fone de ouvido envolvente.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="7ceb1-118">Enviar o ditado capturado a *serviço inteligente de reconhecimento de linguagem do Azure* (*LUIS*).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="7ceb1-119">Ter extração de LUIS, que significa que a partir das informações de envio, que serão analisadas e tentam determinar que a intenção da solicitação do usuário será feita.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="7ceb1-120">Desenvolvimento incluirá a criação de um aplicativo em que o usuário será capaz de usar voz e/ou olhar para alterar o tamanho e a cor dos objetos na cena.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="7ceb1-121">O uso de controladores de movimento não será abordado.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="7ceb1-122">Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="7ceb1-123">Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="7ceb1-124">Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="7ceb1-125">Esteja preparado para treinar LUIS várias vezes, que é abordado na [capítulo 12](#chapter-12--improving-your-luis-service).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="7ceb1-126">Você obterá melhores resultados os mais vezes que LUIS foi treinado.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="7ceb1-127">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="7ceb1-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7ceb1-128">Curso</span><span class="sxs-lookup"><span data-stu-id="7ceb1-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7ceb1-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7ceb1-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7ceb1-130"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="7ceb1-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="7ceb1-131">MR e o Azure 303: Compreensão de idioma natural (LUIS)</span><span class="sxs-lookup"><span data-stu-id="7ceb1-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="7ceb1-132">✔️</span><span class="sxs-lookup"><span data-stu-id="7ceb1-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="7ceb1-133">✔️</span><span class="sxs-lookup"><span data-stu-id="7ceb1-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="7ceb1-134">Enquanto este curso se concentra primariamente em fones de ouvido Windows Mixed Reality de imersão (VR), você também pode aplicar o que você aprenderá neste curso para o Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="7ceb1-135">Como acompanhar o curso, você verá notas quaisquer alterações que talvez seja necessário empregar para dar suporte ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="7ceb1-136">Ao usar o HoloLens, você pode perceber algum eco durante a captura de voz.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7ceb1-137">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7ceb1-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="7ceb1-138">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="7ceb1-139">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="7ceb1-140">Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .</span><span class="sxs-lookup"><span data-stu-id="7ceb1-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="7ceb1-141">Recomendamos que o hardware e software para este curso a seguir:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="7ceb1-142">Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)</span><span class="sxs-lookup"><span data-stu-id="7ceb1-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="7ceb1-143">Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="7ceb1-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="7ceb1-144">O SDK mais recente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="7ceb1-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="7ceb1-145">2017.4 do Unity</span><span class="sxs-lookup"><span data-stu-id="7ceb1-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="7ceb1-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7ceb1-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="7ceb1-147">Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="7ceb1-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="7ceb1-148">Um conjunto de fones de ouvido com um microfone interno (se o fone de ouvido não tiver um mic internos e alto-falantes)</span><span class="sxs-lookup"><span data-stu-id="7ceb1-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="7ceb1-149">Acesso à Internet para a instalação do Azure e a recuperação do LUIS</span><span class="sxs-lookup"><span data-stu-id="7ceb1-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="7ceb1-150">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="7ceb1-150">Before you start</span></span>

1.  <span data-ttu-id="7ceb1-151">Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="7ceb1-152">Para permitir que seu computador habilitar o ditado, vá para **configurações do Windows > privacidade > fala, escrita à tinta e digitando** e pressione o botão **ativar serviços de fala e sugestões de digitação**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="7ceb1-153">O código neste tutorial permitirá que você deseja gravar dos **dispositivo padrão de microfone** definido em seu computador.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="7ceb1-154">Verifique se que o dispositivo de microfone padrão está definido como aquele que você deseja usar para capturar sua voz.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="7ceb1-155">Se o fone de ouvido tem um microfone interno, certifique-se a opção *"Quando eu wear meu fone de ouvido, alternar para o fone de ouvido mic"* está ativado na *Portal de realidade misturada* configurações.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![Configurando o fone de ouvido envolvente](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="7ceb1-157">Capítulo 1 – configurar o Portal do Azure</span><span class="sxs-lookup"><span data-stu-id="7ceb1-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="7ceb1-158">Para usar o *vocal* serviço no Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="7ceb1-159">Faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="7ceb1-160">Se você ainda não tiver uma conta do Azure, você precisará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="7ceb1-161">Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="7ceb1-162">Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure *vocal*e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![Criar recurso do LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="7ceb1-164">A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="7ceb1-165">A nova página à direita fornece uma descrição do serviço de reconhecimento vocal.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="7ceb1-166">Na parte inferior esquerda desta página, selecione a **criar** botão para criar uma instância desse serviço.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![Criação do serviço LUIS - aviso legal](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="7ceb1-168">Depois de clicar em criar:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="7ceb1-169">Inserir sua desejada **nome** para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="7ceb1-170">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="7ceb1-171">Selecione o **tipo de preço** apropriado para você, se esse for o primeiro tempo para criar um *Service LUIS*, uma camada gratuita (chamada F0) deve estar disponível para você.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="7ceb1-172">A alocação livre deve ser mais do que suficiente para este curso.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="7ceb1-173">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="7ceb1-174">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="7ceb1-175">É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="7ceb1-176">Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="7ceb1-177">Determinar a **local** para seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="7ceb1-178">O local seria o ideal é que na região em que o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="7ceb1-179">Alguns ativos do Azure estão disponíveis somente em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="7ceb1-180">Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="7ceb1-181">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-181">Select **Create**.</span></span>

        ![Criar serviço LUIS - entrada do usuário](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="7ceb1-183">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="7ceb1-184">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![Nova imagem de notificação do Azure](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="7ceb1-186">Clique na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-186">Click on the notification to explore your new Service instance.</span></span>

    ![Notificação de criação do recurso com êxito](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="7ceb1-188">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="7ceb1-189">Você será levado para a nova instância do serviço LUIS.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![Acessando chaves LUIS](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="7ceb1-191">Dentro deste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, que é feito por meio do uso de chave de assinatura do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="7ceb1-192">Dos *início rápido* página, de seu *API LUIS* do serviço, navegue até a primeira etapa, *pegue suas chaves*e clique em **chaves** (você também pode fazer isso clicando no hiperlink azul chaves, localizado no menu de navegação de serviços, indicado pelo ícone de chave).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="7ceb1-193">Isso irá revelar o seu serviço *chaves*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="7ceb1-194">Faça uma cópia de uma das chaves exibidas, pois precisará dele posteriormente em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="7ceb1-195">No *Service* , clique em *Portal do reconhecimento vocal* ser redirecionado para a página da Web que você usará para criar seu novo serviço no App LUIS.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="7ceb1-196">Capítulo 2 – o Portal do reconhecimento vocal</span><span class="sxs-lookup"><span data-stu-id="7ceb1-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="7ceb1-197">Nesta seção, você aprenderá como fazer um App LUIS no Portal do LUIS.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="7ceb1-198">Por favor, lembre-se que a configuração de *entidades*, *intenções*, e *declarações* dentro deste capítulo é apenas a primeira etapa na criação de seu serviço LUIS: você também precisará treinar novamente o serviço, várias vezes, portanto, para torná-lo mais precisos.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="7ceb1-199">Treinar novamente seu serviço é abordado a [último capítulo](#chapter-12--improving-your-luis-service) deste curso, portanto, certifique-se de que você conclua.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="7ceb1-200">Ao atingir o *Portal do reconhecimento vocal*, talvez seja necessário fazer logon, se você não ainda estiver, com as mesmas credenciais que o seu portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![Página de logon do LUIS](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="7ceb1-202">Se essa for sua primeira vez usando o LUIS, você precisará rolar para baixo até a parte inferior da página de boas-vinda, para localizar e clique no **aplicativo LUIS criar** botão.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![Criar página de aplicativo LUIS](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="7ceb1-204">Depois de conectado, clique em **meus aplicativos** (se você não estiver nessa seção).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="7ceb1-205">Você pode, em seguida, clique em **criar novo aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-205">You can then click on **Create new app**.</span></span>

    ![LUIS - minha imagem de aplicativos](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="7ceb1-207">Dar ao seu aplicativo uma *nome*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="7ceb1-208">Se seu aplicativo deve para compreender um idioma diferente do inglês, você deve alterar o *cultura* para o idioma apropriado.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="7ceb1-209">Aqui você também pode adicionar um *descrição* do seu novo aplicativo LUIS.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS - criar um novo aplicativo](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="7ceb1-211">Depois de pressionar **feito**, você inserirá o *compilar* página de seu novo *LUIS* aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="7ceb1-212">Há alguns conceitos importantes para entender aqui:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="7ceb1-213">*Intenção*, representa o método que será chamado após uma consulta do usuário.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="7ceb1-214">Uma *INTENÇÃO* pode ter um ou mais *ENTIDADES*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="7ceb1-215">*Entidade*, é um componente da consulta que descreve informações relevantes para o *INTENÇÃO*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="7ceb1-216">*Declarações*, são exemplos de consultas fornecido pelo desenvolvedor, que LUIS usará para treinar a próprio.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="7ceb1-217">Se esses conceitos não são perfeitamente desmarcar, não se preocupe, pois este curso esclarecê-los ainda mais neste capítulo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="7ceb1-218">Você começará criando os *entidades* necessários para compilar este curso.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="7ceb1-219">No lado esquerdo da página, clique em *entidades*, em seguida, clique em **criar nova entidade**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![Criar nova entidade](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="7ceb1-221">Chame a nova entidade *cor*, defina seu tipo como *simples*, em seguida, pressione **feito**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![Criar entidade simples - cor](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="7ceb1-223">Repita esse processo para criar três (3) mais entidades simples chamado:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="7ceb1-224">*upsize*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-224">*upsize*</span></span>
    -   <span data-ttu-id="7ceb1-225">*downsize*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-225">*downsize*</span></span>
    -   <span data-ttu-id="7ceb1-226">*target*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-226">*target*</span></span>

<span data-ttu-id="7ceb1-227">O resultado deve ser semelhante a imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-227">The result should look like the image below:</span></span>

![Resultado da criação da entidade](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="7ceb1-229">Agora você pode começar a criar *intenções*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="7ceb1-230">Não exclua os **None** intenção.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="7ceb1-231">No lado esquerdo da página, clique em **intenções**, em seguida, clique em **criar novo propósito**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![Criar novas tentativas](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="7ceb1-233">Chame o novo *intenção* **ChangeObjectColor**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7ceb1-234">Isso *intenção* nome é usado dentro do código posteriormente no curso, portanto, para obter melhores resultados, use esse nome exatamente como fornecido.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="7ceb1-235">Depois que você confirme o nome que você será direcionado para a página de tentativas.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS - página intenções](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="7ceb1-237">Você observará que há uma caixa de texto solicitando que você para o tipo de 5 ou mais diferente *declarações*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="7ceb1-238">LUIS converte todas as declarações em letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="7ceb1-239">Insira o seguinte *expressão* na caixa de texto superior (atualmente com o texto *digite exemplos cerca de 5...*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="7ceb1-240">) e pressione **Enter**:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="7ceb1-241">Você observará que o novo *expressão* aparecerá em uma lista abaixo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="7ceb1-242">Seguindo o mesmo processo, insira as seguintes declarações de seis (6):</span><span class="sxs-lookup"><span data-stu-id="7ceb1-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="7ceb1-243">Para cada expressão que você criou, você deve identificar quais palavras devem ser usadas pelo LUIS como entidades.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="7ceb1-244">Neste exemplo, você precisa rotular todas as cores como uma *cor* entidade e todos os possíveis referência a um destino como um *destino* entidade.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="7ceb1-245">Para fazer isso, tente clicar na palavra *cilindro* na primeira expressão e selecione *destino*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![Identificar alvos de expressão](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="7ceb1-247">Agora, clique na palavra *vermelho* na primeira expressão e selecione *cor*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![Identificar as entidades de expressão](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="7ceb1-249">Além disso, a próxima linha do rótulo em que *cubo* deve ser um *destino*, e *preto* deve ser um *cor*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="7ceb1-250">Observe também o uso de palavras *'this'*, *'it'*, e *'este objeto'*, que estamos fornecendo, portanto, ter tipos de destino não específicas disponíveis também.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="7ceb1-251">Repita o processo acima até que todas as declarações têm as entidades rotuladas.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="7ceb1-252">Consulte a imagem se você precisar de ajuda abaixo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="7ceb1-253">Ao selecionar palavras para rotulá-los como entidades:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="7ceb1-254">Para palavras individuais, basta clicá-los.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-254">For single words just click them.</span></span>
    > - <span data-ttu-id="7ceb1-255">Para um conjunto de duas ou mais palavras, clique no início e no final do conjunto.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7ceb1-256">Você pode usar o *modo de exibição de Tokens* botão Ativar/desativar para alternar entre **entidades / Tokens exibir**!</span><span class="sxs-lookup"><span data-stu-id="7ceb1-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="7ceb1-257">Os resultados devem ser, conforme mostrado nas imagens a seguir, mostrando os **entidades / Tokens exibir**:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![Tokens e modos de exibição de entidades](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="7ceb1-259">Agora pressione a **Train** botão no canto superior direito da página e aguarde até o pequeno indicador de round-la para ficar verde.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="7ceb1-260">Isso indica que LUIS foi treinado com êxito para reconhecer a intenção.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![Treinar LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="7ceb1-262">Como um exercício para você, crie um novo propósito chamado **ChangeObjectSize**, usando as entidades *destino*, *upsizing*, e *diminuir o tamanho de*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="7ceb1-263">Seguindo o mesmo processo que a intenção anterior, insira as seguintes oito (8) declarações para *tamanho* alterar:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

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

23. <span data-ttu-id="7ceb1-264">O resultado deve ser como o mostrado na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-264">The result should be like the one in the image below:</span></span>

    ![Configurar Tokens ChangeObjectSize / entidades](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="7ceb1-266">Uma vez ambas as intenções **ChangeObjectColor** e **ChangeObjectSize**, foram criados e treinado, clique no **publicar** botão na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![Publicar o serviço LUIS](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="7ceb1-268">Sobre o *publicar* página você finalizar e publicar seu App LUIS para que ele possa ser acessado pelo seu código.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="7ceb1-269">Defina a operação de soltar para baixo *Publish To* como **produção**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="7ceb1-270">Defina as *fuso horário* para seu fuso horário.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="7ceb1-271">A caixa de seleção **prevista de incluir todas as pontuações de intenção**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="7ceb1-272">Clique em **publicar no Slot de produção**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-272">Click on **Publish to Production Slot**.</span></span>

        ![Configurações de publicação](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="7ceb1-274">Na seção *recursos e as chaves*:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="7ceb1-275">Selecione a região que você definiu para a instância de serviço no Portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="7ceb1-276">Você observará uma **Starter_Key** elemento abaixo, ignorá-la.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="7ceb1-277">Clique em **Add Key** e insira o *chave* que você obteve no Portal do Azure quando você criou sua instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="7ceb1-278">Se o Azure e o portal de LUIS estiver conectados ao mesmo usuário, você receberá menus suspensos para *nome do locatário*, *nome da assinatura*e o *chave* você deseja usar ( terá o mesmo nome que você forneceu anteriormente no Portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="7ceb1-279">Sob *ponto de extremidade*, faça uma cópia do ponto de extremidade correspondente à chave inserida por você, você irá usá-lo em breve em seu código.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="7ceb1-280">Capítulo 3 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="7ceb1-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="7ceb1-281">A seguir é um conjunto típico backup para o desenvolvimento com a realidade misturada e como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="7ceb1-282">Abra *Unity* e clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-282">Open *Unity* and click **New**.</span></span> 

    ![Inicie um novo projeto do Unity.](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="7ceb1-284">Agora você precisará fornecer um nome de projeto do Unity, insira **MR_LUIS**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="7ceb1-285">Verifique se o tipo de projeto é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="7ceb1-286">Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="7ceb1-287">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-287">Then, click **Create project**.</span></span>

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="7ceb1-289">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="7ceb1-290">Acesse Editar > Preferências e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="7ceb1-291">Alteração **Editor de Script externo** à **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="7ceb1-292">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-292">Close the **Preferences** window.</span></span>

    ![Atualize as preferências do editor de script.](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="7ceb1-294">Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma **plataforma Universal do Windows**, clicando no **alternar plataforma** botão.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Crie janela de configurações, alternar a plataforma para a UWP.](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="7ceb1-296">Vá para **arquivo > configurações de Build** e certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="7ceb1-297">**Dispositivo de destino** é definido como **qualquer dispositivo**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="7ceb1-298">Para o Microsoft HoloLens, defina **dispositivo de destino** à *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="7ceb1-299">**Tipo de compilação** é definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="7ceb1-300">**SDK** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="7ceb1-301">**Versão do Visual Studio** é definido como **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="7ceb1-302">**Compilar e executar** é definido como **Máquina Local**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="7ceb1-303">Salve a cena e adicioná-lo para a compilação.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="7ceb1-304">Fazer isso selecionando **cenas abra Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="7ceb1-305">Salvamento janela será exibida.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-305">A save window will appear.</span></span>
        
            ![Clique em Adicionar botão cenas aberto](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="7ceb1-307">Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Criar nova pasta de scripts](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="7ceb1-309">Abra seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo*: campo de texto, digite **MR_LuisScene**, em seguida, pressione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![Dê um nome de nova cena.](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="7ceb1-311">O restante de configurações, em *configurações de Build*, deverá ser deixado como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="7ceb1-312">No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra configurações do player.](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="7ceb1-314">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="7ceb1-315">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="7ceb1-316">**Versão de tempo de execução de scripts** deve ser **estável** (.NET 3.5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="7ceb1-317">**Script de back-end** deve ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="7ceb1-318">**Nível de compatibilidade de API** deve ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Outras configurações de atualização.](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="7ceb1-320">Dentro de **configurações de publicação** guia, em **recursos**, verifique:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="7ceb1-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-321">**InternetClient**</span></span>
        2. <span data-ttu-id="7ceb1-322">**Microfone**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-322">**Microphone**</span></span>

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="7ceb1-324">Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Atualize as configurações de R de X.](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="7ceb1-326">Volta *configurações de Build* _Unity C#_  projetos não fica acinzentado; marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="7ceb1-327">Feche a janela de configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="7ceb1-328">Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="7ceb1-329">Capítulo 4-criar a cena</span><span class="sxs-lookup"><span data-stu-id="7ceb1-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ceb1-330">Se você quiser ignorar a *configurar o Unity* componente deste curso e continuar diretamente no código, fique à vontade para baixá-lo [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importá-lo para seu projeto como um [pacote personalizado ](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 5](#chapter-5--create-the-microphonemanager-class).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="7ceb1-331">Clique com botão direito em uma área vazia do *painel de hierarquia*, em **objeto 3D**, adicionar um **plano**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![Crie um plano.](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="7ceb1-333">Lembre-se que quando você clique com botão direito dentro de *hierarquia* novamente para criar mais objetos, se você ainda tiver o último objeto selecionado, o objeto selecionado será o pai do seu novo objeto.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="7ceb1-334">Evite isso left-clicking em um espaço vazio dentro da hierarquia e, em seguida, clicando duas vezes.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="7ceb1-335">Repita o procedimento acima para adicionar os seguintes objetos:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="7ceb1-336">*Sphere*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-336">*Sphere*</span></span>
    2. <span data-ttu-id="7ceb1-337">*Cilindro*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-337">*Cylinder*</span></span>
    3. <span data-ttu-id="7ceb1-338">*Cube*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-338">*Cube*</span></span>
    4. <span data-ttu-id="7ceb1-339">*3D Text*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-339">*3D Text*</span></span>

4.  <span data-ttu-id="7ceb1-340">A cena resultante *hierarquia* deve ser como o mostrado na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![Configuração da hierarquia de cena.](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="7ceb1-342">Clique com o botão esquerdo na **câmera principal** para selecioná-la, examine o *painel Inspetor* você verá o objeto de câmera com todas as a seus componentes.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="7ceb1-343">Clique no **Add Component** botão localizado na parte inferior do *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![Adicionar fonte de áudio](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="7ceb1-345">Pesquise o componente chamado *Audio Source*, conforme mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="7ceb1-346">Também verifique se o *transformar* componente da câmera principal é definido como (0, 0,0), isso pode ser feito, pressionando as **engrenagem** ícone ao lado da câmera *transformar* componente e selecionando **redefinir**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="7ceb1-347">O *transformar* componente, em seguida, deve se parecer com:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="7ceb1-348">*Posição* é definido como **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="7ceb1-349">*Rotação* é definido como **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="7ceb1-350">Para o Microsoft HoloLens, você precisará alterar também o seguinte, que fazem parte dos **câmera** componente, que está no seu **câmera principal**:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="7ceb1-351">**Limpe os sinalizadores de:** Cor sólida.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="7ceb1-352">**Plano de fundo** ' preto, alfa 0' – cor hexadecimal: 00000000 #.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="7ceb1-353">Clique com o botão esquerdo na **plano** para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="7ceb1-354">No *painel Inspetor* definir os *transformar* componente com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="7ceb1-355">Transformar - *posição*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="7ceb1-356">**X**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-356">**X**</span></span> | <span data-ttu-id="7ceb1-357">**Y**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-357">**Y**</span></span>                  | <span data-ttu-id="7ceb1-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-358">**Z**</span></span> |
    | <span data-ttu-id="7ceb1-359">0</span><span class="sxs-lookup"><span data-stu-id="7ceb1-359">0</span></span>     | <span data-ttu-id="7ceb1-360">-1</span><span class="sxs-lookup"><span data-stu-id="7ceb1-360">-1</span></span>                     | <span data-ttu-id="7ceb1-361">0</span><span class="sxs-lookup"><span data-stu-id="7ceb1-361">0</span></span>     |


10. <span data-ttu-id="7ceb1-362">Clique com o botão esquerdo na **esfera** para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="7ceb1-363">No *painel Inspetor* definir os *transformar* componente com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="7ceb1-364">Transformar - *posição*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="7ceb1-365">**X**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-365">**X**</span></span> | <span data-ttu-id="7ceb1-366">**Y**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-366">**Y**</span></span>                  | <span data-ttu-id="7ceb1-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-367">**Z**</span></span> |
    | <span data-ttu-id="7ceb1-368">2</span><span class="sxs-lookup"><span data-stu-id="7ceb1-368">2</span></span>     | <span data-ttu-id="7ceb1-369">1</span><span class="sxs-lookup"><span data-stu-id="7ceb1-369">1</span></span>                      | <span data-ttu-id="7ceb1-370">2</span><span class="sxs-lookup"><span data-stu-id="7ceb1-370">2</span></span>     |

11. <span data-ttu-id="7ceb1-371">Clique com o botão esquerdo na **cilindro** para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="7ceb1-372">No *painel Inspetor* definir os *transformar* componente com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="7ceb1-373">Transformar - *posição*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="7ceb1-374">**X**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-374">**X**</span></span> | <span data-ttu-id="7ceb1-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-375">**Y**</span></span>                  | <span data-ttu-id="7ceb1-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-376">**Z**</span></span> |
    | <span data-ttu-id="7ceb1-377">-2</span><span class="sxs-lookup"><span data-stu-id="7ceb1-377">-2</span></span>    | <span data-ttu-id="7ceb1-378">1</span><span class="sxs-lookup"><span data-stu-id="7ceb1-378">1</span></span>                      | <span data-ttu-id="7ceb1-379">2</span><span class="sxs-lookup"><span data-stu-id="7ceb1-379">2</span></span>     |

12. <span data-ttu-id="7ceb1-380">Clique com o botão esquerdo na **cubo** para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="7ceb1-381">No *painel Inspetor* definir os *transformar* componente com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="7ceb1-382">Transformar - *posição*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="7ceb1-383">Transformar - *rotação*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="7ceb1-384">**X**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-384">**X**</span></span> | <span data-ttu-id="7ceb1-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-385">**Y**</span></span>                   | <span data-ttu-id="7ceb1-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-386">**Z**</span></span> |  \| | <span data-ttu-id="7ceb1-387">**X**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-387">**X**</span></span> | <span data-ttu-id="7ceb1-388">**Y**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-388">**Y**</span></span>                  | <span data-ttu-id="7ceb1-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-389">**Z**</span></span> |
    | <span data-ttu-id="7ceb1-390">0</span><span class="sxs-lookup"><span data-stu-id="7ceb1-390">0</span></span>     | <span data-ttu-id="7ceb1-391">1</span><span class="sxs-lookup"><span data-stu-id="7ceb1-391">1</span></span>                       | <span data-ttu-id="7ceb1-392">4</span><span class="sxs-lookup"><span data-stu-id="7ceb1-392">4</span></span>     |  \| | <span data-ttu-id="7ceb1-393">45</span><span class="sxs-lookup"><span data-stu-id="7ceb1-393">45</span></span>    | <span data-ttu-id="7ceb1-394">45</span><span class="sxs-lookup"><span data-stu-id="7ceb1-394">45</span></span>                     | <span data-ttu-id="7ceb1-395">0</span><span class="sxs-lookup"><span data-stu-id="7ceb1-395">0</span></span>     | 

13. <span data-ttu-id="7ceb1-396">Clique com o botão esquerdo na **novo texto** objeto para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="7ceb1-397">No *painel Inspetor* definir os *transformar* componente com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="7ceb1-398">Transformar - *posição*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="7ceb1-399">Transformar - *escala*</span><span class="sxs-lookup"><span data-stu-id="7ceb1-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="7ceb1-400">**X**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-400">**X**</span></span> | <span data-ttu-id="7ceb1-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-401">**Y**</span></span>                  | <span data-ttu-id="7ceb1-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-402">**Z**</span></span> |  \| | <span data-ttu-id="7ceb1-403">**X**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-403">**X**</span></span> | <span data-ttu-id="7ceb1-404">**Y**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-404">**Y**</span></span>               | <span data-ttu-id="7ceb1-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-405">**Z**</span></span> |
    | <span data-ttu-id="7ceb1-406">-2</span><span class="sxs-lookup"><span data-stu-id="7ceb1-406">-2</span></span>    | <span data-ttu-id="7ceb1-407">6</span><span class="sxs-lookup"><span data-stu-id="7ceb1-407">6</span></span>                      | <span data-ttu-id="7ceb1-408">9</span><span class="sxs-lookup"><span data-stu-id="7ceb1-408">9</span></span>     |  \| | <span data-ttu-id="7ceb1-409">0.1</span><span class="sxs-lookup"><span data-stu-id="7ceb1-409">0.1</span></span>   | <span data-ttu-id="7ceb1-410">0.1</span><span class="sxs-lookup"><span data-stu-id="7ceb1-410">0.1</span></span>                 | <span data-ttu-id="7ceb1-411">0.1</span><span class="sxs-lookup"><span data-stu-id="7ceb1-411">0.1</span></span>   | 

14. <span data-ttu-id="7ceb1-412">Alteração **Font Size** na **texto de malha** componente **50**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="7ceb1-413">Alterar o *nome* da **texto de malha** o objeto para a **texto ditado**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![Criar objeto de texto 3D](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="7ceb1-415">A estrutura de hierarquia painel agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![texto de malha no modo de exibição de cena](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="7ceb1-417">A cena final deve parecer com a imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-417">The final scene should look like the image below:</span></span>

    ![O modo de exibição de cena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="7ceb1-419">Capítulo 5 – criar a classe MicrophoneManager</span><span class="sxs-lookup"><span data-stu-id="7ceb1-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="7ceb1-420">É o primeiro Script que você pretende criar o *MicrophoneManager* classe.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="7ceb1-421">Depois disso, você aprenderá a criar o *LuisManager*, o *comportamentos* classe e por fim, o *olhares* classe (fique à vontade para criar todos esses agora, embora será abordada como você alcance cada capítulo).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="7ceb1-422">O *MicrophoneManager* classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="7ceb1-423">Detectando o dispositivo de gravação anexado ao computador (o que é o padrão) ou fone de ouvido.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="7ceb1-424">Capturar áudio (voz) e usar ditado para armazená-la como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="7ceb1-425">Depois que a voz foi pausado, enviar o ditado para o *LuisManager* classe.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="7ceb1-426">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-426">To create this class:</span></span> 

1.  <span data-ttu-id="7ceb1-427">Clique com botão direito no *painel do projeto*, **criar > pasta**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="7ceb1-428">Chame a pasta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-428">Call the folder **Scripts**.</span></span> 

    ![Crie a pasta de Scripts.](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="7ceb1-430">Com o **Scripts** pasta criada, clique duas vezes nele para abrir.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="7ceb1-431">Em seguida, dentro dessa pasta, direito do mouse **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="7ceb1-432">Nomeie o script *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="7ceb1-433">Clique duas vezes em *MicrophoneManager* para abri-lo com *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="7ceb1-434">Adicione os namespaces a seguir na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="7ceb1-435">Em seguida, adicione as seguintes variáveis dentro do *MicrophoneManager* classe:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="7ceb1-436">Código para o *Awake()* e *Start ()* métodos agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="7ceb1-437">Eles serão chamados quando inicializa a classe:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-437">These will be called when the class initializes:</span></span>

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
 
7.  <span data-ttu-id="7ceb1-438">Agora, você precisa que o método que o aplicativo usa para iniciar e parar a captura de voz e passá-lo para o *LuisManager* classe, que você criará em breve.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

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

8.  <span data-ttu-id="7ceb1-439">Adicionar um *ditado manipulador* que será invocado quando a voz pausa.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="7ceb1-440">Esse método irá passar o texto ditado para o *LuisManager* classe.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

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
    > <span data-ttu-id="7ceb1-441">Excluir o *Update ()* método uma vez que essa classe não irá usá-lo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="7ceb1-442">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7ceb1-443">Neste ponto, você observará um erro que aparecem na *painel de Console do Editor do Unity*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="7ceb1-444">Isso ocorre porque o código faz referência a *LuisManager* classe que você criará no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="7ceb1-445">Capítulo 6 – criar a classe LUISManager</span><span class="sxs-lookup"><span data-stu-id="7ceb1-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="7ceb1-446">É hora de criar o *LuisManager* classe, que faz com que a chamada para o serviço LUIS do Azure.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="7ceb1-447">A finalidade dessa classe é receber o texto ditado do *MicrophoneManager* classe e enviá-lo para o *API de reconhecimento vocal Azure* a serem analisados.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="7ceb1-448">Essa classe desserializará o *JSON* resposta e chamar os métodos apropriados da *comportamentos* classe para disparar uma ação.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="7ceb1-449">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-449">To create this class:</span></span> 

1.  <span data-ttu-id="7ceb1-450">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="7ceb1-451">Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="7ceb1-452">Nomeie o script *LuisManager*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="7ceb1-453">Clique duas vezes no script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="7ceb1-454">Adicione os namespaces a seguir na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="7ceb1-455">Você começará criando três classes **dentro de** as *LuisManager* classe (dentro do mesmo arquivo de script, acima o *Start ()* método) que representará o desserializado Resposta JSON do Azure.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

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

6.  <span data-ttu-id="7ceb1-456">Em seguida, adicione as seguintes variáveis dentro do *LuisManager* classe:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="7ceb1-457">Certifique-se de colocar o ponto de extremidade do LUIS no agora (que você terá de seu portal LUIS).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="7ceb1-458">Código para o *Awake()* método agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="7ceb1-459">Esse método será chamado quando a classe é inicializado:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="7ceb1-460">Agora, você precisa que os métodos que esse aplicativo usa para enviar o ditado recebido do *MicrophoneManager* classe *LUIS*e, em seguida, receber e desserializar a resposta.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="7ceb1-461">Depois de determinar o valor da intenção e as entidades associadas, eles são passados para a instância das *comportamentos* classe para disparar a ação pretendida.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

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
 
11. <span data-ttu-id="7ceb1-462">Criar um novo método chamado *AnalyseResponseElements()* lerá resultante *AnalysedQuery* e determinar as entidades.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="7ceb1-463">Depois que essas entidades são determinadas, eles serão passados para a instância das *comportamentos* classe a ser usada nas ações.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

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

            // Depending on the topmost recognised intent, read the entities name
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
    > <span data-ttu-id="7ceb1-464">Excluir o *Start ()* e *Update ()* métodos, já que essa classe não irá usá-los.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="7ceb1-465">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="7ceb1-466">Neste ponto, você vai notar vários erros que aparecem na *painel de Console do Editor do Unity*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="7ceb1-467">Isso ocorre porque o código faz referência a *comportamentos* classe que você criará no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="7ceb1-468">Capítulo 7 – criar a classe de comportamentos</span><span class="sxs-lookup"><span data-stu-id="7ceb1-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="7ceb1-469">O *comportamentos* classe irá disparar as ações usando as entidades fornecidas pelo *LuisManager* classe.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="7ceb1-470">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-470">To create this class:</span></span> 

1.  <span data-ttu-id="7ceb1-471">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="7ceb1-472">Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="7ceb1-473">Nomeie o script *comportamentos*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="7ceb1-474">Clique duas vezes para abri-lo com o script *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="7ceb1-475">Em seguida, adicione as seguintes variáveis dentro do *comportamentos* classe:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="7ceb1-476">Adicione a *Awake()* código do método.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="7ceb1-477">Esse método será chamado quando a classe é inicializado:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="7ceb1-478">Os seguintes métodos são chamados pelo *LuisManager* classe (que você criou anteriormente) para determinar qual objeto é o destino da consulta e, em seguida, disparar a ação apropriada.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

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
 
7.  <span data-ttu-id="7ceb1-479">Adicione a *FindTarget()* método para determinar quais as *GameObjects* é o destino da intenção atual.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="7ceb1-480">Este método assume como padrão o destino para o *GameObject* sendo "gazed" se nenhum destino explícito é definido nas entidades.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
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
    > <span data-ttu-id="7ceb1-481">Excluir o *Start ()* e *Update ()* métodos, já que essa classe não irá usá-los.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="7ceb1-482">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="7ceb1-483">Capítulo 8 – criar a classe de olhar</span><span class="sxs-lookup"><span data-stu-id="7ceb1-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="7ceb1-484">A última classe que você precisará concluir este aplicativo é o *olhares* classe.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="7ceb1-485">Essa classe atualiza a referência para o *GameObject* em foco de visual do usuário no momento.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="7ceb1-486">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-486">To create this Class:</span></span> 

1.  <span data-ttu-id="7ceb1-487">Clique duas vezes no **Scripts** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="7ceb1-488">Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="7ceb1-489">Nomeie o script *olhares*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="7ceb1-490">Clique duas vezes para abri-lo com o script *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="7ceb1-491">Insira o seguinte código para esta classe:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-491">Insert the following code for this class:</span></span>

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
 
5.  <span data-ttu-id="7ceb1-492">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="7ceb1-493">Capítulo 9 – concluir a configuração de cena</span><span class="sxs-lookup"><span data-stu-id="7ceb1-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="7ceb1-494">Para concluir a instalação da cena, arraste cada script que você tenha criado a partir da pasta de Scripts para o **câmera principal** do objeto na *painel de hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="7ceb1-495">Selecione o **câmera principal** e examine o *painel Inspetor*, você deve ser capaz de ver cada script que você já anexou e você observará que há parâmetros em cada script que ainda estão a ser definido.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![Definindo os destinos de referência de câmera.](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="7ceb1-497">Para definir esses parâmetros corretamente, siga estas instruções:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="7ceb1-498">*MicrophoneManager*:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="7ceb1-499">Do *painel de hierarquia*, arraste o **texto ditado** objeto para o **texto ditado** caixa do valor de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="7ceb1-500">*Comportamentos*, do *painel de hierarquia*:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="7ceb1-501">Arraste o **esfera** do objeto para o *esfera* caixa do destino de referência.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="7ceb1-502">Arraste o **cilindro** para o *cilindro* caixa do destino de referência.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="7ceb1-503">Arraste o **cubo** para o *cubo* caixa do destino de referência.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="7ceb1-504">*Gaze*:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-504">*Gaze*:</span></span>

        - <span data-ttu-id="7ceb1-505">Defina as *olhares Max distância* para **300** (se ele não ainda estiver).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="7ceb1-506">O resultado deve ser semelhante a imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-506">The result should look like the image below:</span></span>

    ![Agora, mostrando os destinos de referência de câmera, defina.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="7ceb1-508">Capítulo 10 – teste no Editor do Unity</span><span class="sxs-lookup"><span data-stu-id="7ceb1-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="7ceb1-509">Teste a configuração de cena é implementada corretamente.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="7ceb1-510">Certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-510">Ensure that:</span></span>

-   <span data-ttu-id="7ceb1-511">Todos os scripts são anexados para o **câmera principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="7ceb1-512">Todos os campos a *painel de Inspetor de câmera principal* são atribuídas corretamente.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="7ceb1-513">Pressione a **reproduzir** botão na *Editor do Unity*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="7ceb1-514">O aplicativo deve estar executando dentro de fone de ouvido imersivo anexado.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="7ceb1-515">Tente algumas frases, tais como:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="7ceb1-516">Se você vir um erro no console do Unity sobre o dispositivo de áudio padrão a alteração, a cena pode não funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="7ceb1-517">Isso é devido à maneira como o portal de realidade misturada lida com microfones internos para fones de ouvido que têm-los.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="7ceb1-518">Se você vir esse erro, simplesmente parar a cena e iniciá-lo novamente e as coisas devem funcionar como esperado.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="7ceb1-519">Capítulo 11 – Build e carregar a solução de UWP</span><span class="sxs-lookup"><span data-stu-id="7ceb1-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="7ceb1-520">Depois que você garante que o aplicativo está funcionando no Editor do Unity, você está pronto para compilar e implantar.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="7ceb1-521">Para construir:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-521">To Build:</span></span>

1.  <span data-ttu-id="7ceb1-522">Salve a cena atual clicando em **arquivo > Salvar**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="7ceb1-523">Vá para **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="7ceb1-524">Marque a caixa denominada **Unity C# projetos** (útil para ver e depurar seu código depois de criar o projeto UWP.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="7ceb1-525">Clique em **adicionar cenas aberto**, em seguida, clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![Janela de configurações da compilação](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="7ceb1-527">Você será solicitado a selecionar a pasta onde você deseja criar a solução.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="7ceb1-528">Criar uma *compilações* pasta e dentro dessa pasta, crie outra pasta com um nome apropriado de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="7ceb1-529">Clique em **Selecionar pasta** para iniciar a compilação nesse local.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="7ceb1-530">![Criar pasta Builds](images/AzureLabs-Lab3-44.png)
    ![Select cria a pasta](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="7ceb1-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="7ceb1-531">Uma vez Unity terminou de construção (pode levar algum tempo), ele deverá abrir um **Explorador de arquivos** janela no local de sua compilação.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="7ceb1-532">Para implantar no computador Local:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="7ceb1-533">Na *Visual Studio*, abra o arquivo de solução que foi criado na [capítulo anterior](#chapter-10--test-in-the-unity-editor).</span><span class="sxs-lookup"><span data-stu-id="7ceb1-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="7ceb1-534">No **plataforma da solução**, selecione **x86**, **Máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="7ceb1-535">No **configuração da solução** selecionar **depurar**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="7ceb1-536">Para o Microsoft HoloLens, talvez você ache mais fácil de definir isso como *máquina remota*, de modo que você não estiver vinculado ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="7ceb1-537">No entanto, você precisará também fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7ceb1-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="7ceb1-538">Saber a **endereço IP** de seu HoloLens, que podem ser encontrado dentro a *Configurações > rede e Internet > Wi-Fi > Opções avançadas de*; o IPv4 é o endereço que você deve usar.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="7ceb1-539">Certifique-se **modo de desenvolvedor** é **na**; encontrado na *Configurações > atualização e segurança > para os desenvolvedores*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Implantar aplicativo](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="7ceb1-541">Vá para o **menu Build** e clique em **implantar solução** para carregar o aplicativo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="7ceb1-542">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="7ceb1-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="7ceb1-543">Depois de iniciado, o aplicativo solicitará que você autorizar o acesso para o _microfone_.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="7ceb1-544">Use o *controladores movimento*, ou *entrada de voz*, ou o *teclado* pressionar o **Sim** botão.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="7ceb1-545">Capítulo 12 – melhorando o seu serviço LUIS</span><span class="sxs-lookup"><span data-stu-id="7ceb1-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="7ceb1-546">Este capítulo é incrivelmente importante e talvez precise ser interated após várias vezes, pois ajudará a melhorar a precisão do seu serviço LUIS: Certifique-se de concluir isso.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-546">This chapter is incredibly important, and may need to be interated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="7ceb1-547">Para aumentar o nível de compreensão fornecida pelo LUIS, você precisa capturar novas declarações e usá-los para treinar novamente seu App LUIS.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="7ceb1-548">Por exemplo, você pode ter treinado LUIS para entender a "Increase" e "Ampliar", mas não seria você quiser que seu aplicativo para também reconhecer palavras como "Ampliar"?</span><span class="sxs-lookup"><span data-stu-id="7ceb1-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="7ceb1-549">Depois que você usou seu aplicativo algumas vezes, tudo o que você já disse serão coletados pelo LUIS e estarão disponíveis no PORTAL do LUIS.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="7ceb1-550">Vá para seu aplicativo de portal seguindo este [LINK](https://www.luis.ai/home)e fazer logon.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="7ceb1-551">Depois que você está conectado com suas Credentials MS, clique em seu *nome do aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="7ceb1-552">Clique o **examine as declarações de ponto de extremidade** botão à esquerda da página.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![Examinar declarações](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="7ceb1-554">Você verá uma lista das declarações que foram enviadas para o LUIS pelo seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![Lista de declarações](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="7ceb1-556">Você observará algumas realçado *entidades*.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="7ceb1-557">Passando o mouse sobre cada palavra realçada, você pode examinar cada expressão e determinar quais entidades foi reconhecida corretamente, quais entidades estão erradas e quais entidades são perdidas.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="7ceb1-558">No exemplo acima, ele foi encontrado que a palavra "spear" tinha sido realçada como um destino, então ele necessárias para corrigir o erro, o que é feito ao passar o mouse sobre a palavra com o mouse e clicando em **remover rótulo**.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="7ceb1-559">![Verificar as declarações](images/AzureLabs-Lab3-49.png)
![remover a imagem do rótulo](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="7ceb1-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="7ceb1-560">Se você encontrar declarações que estão completamente erradas, você poderá excluí-los usando o **excluir** botão no lado direito da tela.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![Excluir declarações erradas](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="7ceb1-562">Ou se você achar que LUIS tem a declaração interpretada corretamente, você pode validar sua compreensão usando o **adicionar a intenção alinhado** botão.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![Adicionar a intenção alinhada](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="7ceb1-564">Depois que você tenha classificado Rotulasse exibido, experimente e recarregue a página para ver se mais estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="7ceb1-565">É muito importante repetir esse processo tantas vezes quanto possível melhorar seu entendimento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="7ceb1-566">**Divertir-se!**</span><span class="sxs-lookup"><span data-stu-id="7ceb1-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="7ceb1-567">Seu aplicativo LUIS integrado concluído</span><span class="sxs-lookup"><span data-stu-id="7ceb1-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="7ceb1-568">Parabéns, você criou um aplicativo de realidade mista que aproveita o Azure serviço reconhecimento vocal inteligência, para entender o que um usuário diz e agir sobre essas informações.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![resultado de laboratório](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="7ceb1-570">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="7ceb1-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="7ceb1-571">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="7ceb1-571">Exercise 1</span></span>

<span data-ttu-id="7ceb1-572">Ao usar este aplicativo, você pode observar que se você olhar no objeto do chão e pedir para alterar sua cor, ele fará isso.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="7ceb1-573">Você pode trabalhar como interromper a alterar a cor base do aplicativo?</span><span class="sxs-lookup"><span data-stu-id="7ceb1-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="7ceb1-574">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="7ceb1-574">Exercise 2</span></span>

<span data-ttu-id="7ceb1-575">Experimente a extensão dos recursos de aplicativo e LUIS, acrescentando funcionalidade adicional para objetos na cena; Por exemplo, crie novos objetos ao olhar ponto de clique, dependendo do que o usuário diz e, em seguida, ser capaz de usá-los junto com objetos de cena atual, com os comandos existentes.</span><span class="sxs-lookup"><span data-stu-id="7ceb1-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
