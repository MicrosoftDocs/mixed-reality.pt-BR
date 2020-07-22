---
title: Tutoriais de introdução – 8. Como usar o acompanhamento de olho
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 9a9fc7f860e6bf9c5cb3370a9c9ff11e627fe73f
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304121"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="07f6b-105">8. Como usar o acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="07f6b-105">8. Using eye-tracking</span></span>

## <a name="overview"></a><span data-ttu-id="07f6b-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="07f6b-106">Overview</span></span>

<span data-ttu-id="07f6b-107">Neste tutorial, você aprenderá a habilitar o acompanhamento de olho para o HoloLens 2 e a adicionar acompanhamento de olho a objetos para disparar ações quando o usuário examina os objetos.</span><span class="sxs-lookup"><span data-stu-id="07f6b-107">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="07f6b-108">Se você também estiver implantando esse projeto no HoloLens (1ª geração), observe que o acompanhamento de olho só tem suporte no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="07f6b-108">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="07f6b-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="07f6b-109">Objectives</span></span>

* <span data-ttu-id="07f6b-110">Saiba como habilitar o acompanhamento de olho para o HoleLens 2</span><span class="sxs-lookup"><span data-stu-id="07f6b-110">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="07f6b-111">Saiba como usar o acompanhamento de olho para disparar ações</span><span class="sxs-lookup"><span data-stu-id="07f6b-111">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="07f6b-112">Como garantir que a funcionalidade de Entrada de Foco de Olho esteja habilitada</span><span class="sxs-lookup"><span data-stu-id="07f6b-112">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="07f6b-113">No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade de Entrada de Foco de Olho** está esmaecida:</span><span class="sxs-lookup"><span data-stu-id="07f6b-113">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="07f6b-115">A funcionalidade de Entrada de Foco deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) quando você configurou o projeto do Unity no início desta série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="07f6b-115">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="07f6b-116">No entanto, se não estiver habilitada, faça isso agora.</span><span class="sxs-lookup"><span data-stu-id="07f6b-116">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="07f6b-117">Como habilitar o foco baseado em olho no provedor de foco</span><span class="sxs-lookup"><span data-stu-id="07f6b-117">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="07f6b-118">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, na janela Inspetor, selecione a guia MixedRealityToolkit > **Entrada** e execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="07f6b-118">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="07f6b-119">Clone o **DefaultHoloLens2InputSystemProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_HoloLens2InputSystemProfile_</span><span class="sxs-lookup"><span data-stu-id="07f6b-119">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="07f6b-120">Expandir a seção **Ponteiros**</span><span class="sxs-lookup"><span data-stu-id="07f6b-120">Expand the **Pointers** section</span></span>
* <span data-ttu-id="07f6b-121">Clone o **DefaultMixedRealityPointerProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_MixedRealityPointerProfile_</span><span class="sxs-lookup"><span data-stu-id="07f6b-121">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="07f6b-122">Localize a seção **Configurações de Foco** e marque a caixa de seleção **Acompanhamento de Olho Está Habilitado**</span><span class="sxs-lookup"><span data-stu-id="07f6b-122">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="07f6b-124">Para lembrar como clonar perfis de MRTK, consulte as instruções em [Configurando os perfis do MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="07f6b-124">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="07f6b-125">Como habilitar o controle de olho simulado para o editor do Unity</span><span class="sxs-lookup"><span data-stu-id="07f6b-125">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="07f6b-126">Na janela hierarquia, selecione o objeto **MixedRealityToolkit** e, em seguida, na janela Inspetor, navegue até a guia **Entrada** e, em seguida:</span><span class="sxs-lookup"><span data-stu-id="07f6b-126">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="07f6b-127">Expanda a seção **Provedores de Dados de Entrada** > **Serviço de Simulação de Entrada**</span><span class="sxs-lookup"><span data-stu-id="07f6b-127">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="07f6b-128">Clone o **DefaultMixedRealityInputSimulationProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_MixedRealityInputSimulationProfile_</span><span class="sxs-lookup"><span data-stu-id="07f6b-128">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="07f6b-129">Localize a seção **Simulação de Olho** e marque a caixa de seleção **Simular Posição do Olho**</span><span class="sxs-lookup"><span data-stu-id="07f6b-129">Locate the **Eye Simulation** section and check the **Simulate Eye Position** checkbox</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="07f6b-131">Como adicionar acompanhamento de olho a objetos</span><span class="sxs-lookup"><span data-stu-id="07f6b-131">Adding eye-tracking to objects</span></span>

<span data-ttu-id="07f6b-132">Na janela Hierarquia, expanda o objeto RoverExplorer > **Botões** e, para cada um dos três objetos de botão filho, expanda e selecione o objeto SeeItSayItLabel > **TextMeshPro**:</span><span class="sxs-lookup"><span data-stu-id="07f6b-132">In the Hierarchy window, expand the RoverExplorer > **Buttons** object, then for each of the three child button objects, expand and select the SeeItSayItLabel > **TextMeshPro** object:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="07f6b-134">Com os três objetos TextMeshPro ainda selecionados, na janela Inspetor, use o botão **Adicionar Componente** para adicionar os seguintes componentes a todos os objetos selecionados:</span><span class="sxs-lookup"><span data-stu-id="07f6b-134">With the three TextMeshPro objects still selected, in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="07f6b-135">Componente **Colisor de Caixa**</span><span class="sxs-lookup"><span data-stu-id="07f6b-135">**Box Collider** component</span></span>
* <span data-ttu-id="07f6b-136">Componente **EyeTrackingTarget**</span><span class="sxs-lookup"><span data-stu-id="07f6b-136">**EyeTrackingTarget** component</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="07f6b-138">Na janela Hierarquia, selecione o objeto **Dicas** > SeeItSayItLabel > **TextMeshPro** e configure o componente **EyeTrackingTarget** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="07f6b-138">In the Hierarchy window, select the **Hints** > SeeItSayItLabel > **TextMeshPro** object, then configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="07f6b-139">Na seção de evento **On Look At Start ()**</span><span class="sxs-lookup"><span data-stu-id="07f6b-139">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="07f6b-140">Clique no ícone pequeno **+** para adicionar outro evento</span><span class="sxs-lookup"><span data-stu-id="07f6b-140">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="07f6b-141">Atribua o objeto em si, ou seja, o mesmo objeto **TextMeshPro** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="07f6b-141">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="07f6b-142">Na lista suspensa **Sem Função**, selecione **TextMeshPro** > **float fontSize** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="07f6b-142">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="07f6b-143">Defina o argumento como **0,06** para aumentar o tamanho da fonte atual de 0,04 em 50%</span><span class="sxs-lookup"><span data-stu-id="07f6b-143">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="07f6b-144">Na seção de evento **On Look Away ()**</span><span class="sxs-lookup"><span data-stu-id="07f6b-144">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="07f6b-145">Clique no ícone pequeno **+** para adicionar outro evento</span><span class="sxs-lookup"><span data-stu-id="07f6b-145">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="07f6b-146">Atribua o objeto em si, ou seja, o mesmo objeto **TextMeshPro** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="07f6b-146">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="07f6b-147">Na lista suspensa **Sem Função**, selecione **TextMeshPro** > **float fontSize** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="07f6b-147">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="07f6b-148">Defina o argumento como **0,04** para redefinir o tamanho da fonte de volta para 0,04</span><span class="sxs-lookup"><span data-stu-id="07f6b-148">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="07f6b-150">**Repita** esta etapa para o objeto **Explodir** > SeeItSayItLabel > **TextMeshPro** e o objeto **Redefinir** > SeeItSayItLabel > **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="07f6b-150">**Repeat** this step for the **Explode** > SeeItSayItLabel > **TextMeshPro** object and the **Reset** > SeeItSayItLabel > **TextMeshPro** object.</span></span>

<span data-ttu-id="07f6b-151">Se agora você entrar no modo de Jogo e pressionar e manter o botão direito do mouse enquanto move o mouse até que o foco atinja um dos rótulos, verá o tamanho da fonte aumentar em 50% e ser redefinido de volta ao seu tamanho original ao desviar o olhar:</span><span class="sxs-lookup"><span data-stu-id="07f6b-151">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the labels, you will see the font size increase by 50% and reset back to its original size when looking away:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="07f6b-153">Parabéns</span><span class="sxs-lookup"><span data-stu-id="07f6b-153">Congratulations</span></span>

<span data-ttu-id="07f6b-154">Neste tutorial, você aprendeu a habilitar o acompanhamento de olho para o HoloLens 2 e a adicionar acompanhamento de olho a objetos para disparar ações quando o usuário examina os objetos.</span><span class="sxs-lookup"><span data-stu-id="07f6b-154">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

[<span data-ttu-id="07f6b-155">Próximo tutorial: 9. Usando comandos de fala</span><span class="sxs-lookup"><span data-stu-id="07f6b-155">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)