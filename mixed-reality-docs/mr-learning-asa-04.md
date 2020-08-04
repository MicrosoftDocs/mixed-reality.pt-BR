---
title: Tutoriais de Âncoras Espaciais do Azure – 4. Exibir comentários de Âncoras Espaciais do Azure
description: Conclua este curso para saber como implementar as Âncoras Espaciais do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: afcd7753fb2296503e67a1977b183df951124560
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376518"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a><span data-ttu-id="59ac5-105">4. Exibir comentários das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="59ac5-105">4. Displaying feedback from Azure Spatial Anchors</span></span>

<span data-ttu-id="59ac5-106">Neste tutorial, você aprenderá a fornecer comentários sobre a descoberta de âncora, eventos e status aos usuários ao usar o ASA (Âncoras Espaciais do Azure).</span><span class="sxs-lookup"><span data-stu-id="59ac5-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="59ac5-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="59ac5-107">Objectives</span></span>

* <span data-ttu-id="59ac5-108">Saber como configurar um painel de interface do usuário que exibe informações essenciais sobre a sessão atual do ASA</span><span class="sxs-lookup"><span data-stu-id="59ac5-108">Learn how to set up a UI panel that displays essential information about the current ASA session</span></span>
* <span data-ttu-id="59ac5-109">Saber e explorar os elementos de comentários que o SDK do ASA disponibiliza para os usuários</span><span class="sxs-lookup"><span data-stu-id="59ac5-109">learn about and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="setting-up-asa-feedback-panel"></a><span data-ttu-id="59ac5-110">Configurar o painel de comentários do ASA</span><span class="sxs-lookup"><span data-stu-id="59ac5-110">Setting up ASA feedback panel</span></span>

<span data-ttu-id="59ac5-111">Na janela Hierarquia, clique com o botão direito do mouse no objeto **Instruções** > **TextContent**.</span><span class="sxs-lookup"><span data-stu-id="59ac5-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object.</span></span> <span data-ttu-id="59ac5-112">Selecione **Objeto 3D** > **Text – TextMeshPro** para criar um objeto de texto TextMeshPro como um filho do objeto Instruções > TextContent:</span><span class="sxs-lookup"><span data-stu-id="59ac5-112">Select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="59ac5-114">Para facilitar o trabalho com sua cena, defina a <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Visibilidade da Cena</a> para o objeto ParentAnchor como off clicando no ícone de olho à esquerda do objeto.</span><span class="sxs-lookup"><span data-stu-id="59ac5-114">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="59ac5-115">Isso oculta o objeto na janela Cena sem alterar a visibilidade no jogo.</span><span class="sxs-lookup"><span data-stu-id="59ac5-115">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="59ac5-116">Renomeie o objeto Texto (TMP) recém criado **Comentários** e, na janela Inspetor, altere sua posição e tamanho para que ele seja posicionado de maneira organizada, abaixo do texto de instrução, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="59ac5-116">Rename the newly created Text (TMP) object **Feedback**, then, in the Inspector window, change its position and size, so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="59ac5-117">Altere a **Pos Y** do componente do Rect Transform para -0,24.</span><span class="sxs-lookup"><span data-stu-id="59ac5-117">Change the Rect Transform component's **Pos Y** to -0.24.</span></span>
* <span data-ttu-id="59ac5-118">Altere a **Largura** do componente do Rect Transform para 0,555.</span><span class="sxs-lookup"><span data-stu-id="59ac5-118">Change the Rect Transform component's **Width** to 0.555.</span></span>
* <span data-ttu-id="59ac5-119">Altere a **Altura** do componente do Rect Transform para 0,1.</span><span class="sxs-lookup"><span data-stu-id="59ac5-119">Change the Rect Transform component's **Height** to 0.1.</span></span>

<span data-ttu-id="59ac5-120">Em seguida, escolha as propriedades da fonte para que o texto caiba bem na área de texto, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="59ac5-120">Then choose font properties, so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="59ac5-121">Altere o **Estilo da Fonte** do componente de texto – TextMeshPro para negrito.</span><span class="sxs-lookup"><span data-stu-id="59ac5-121">Change the TextMeshPro - Text component's **Font Style** to Bold.</span></span>
* <span data-ttu-id="59ac5-122">Altere o **Tamanho da Fonte** do componente de texto – TextMeshPro para 0,17.</span><span class="sxs-lookup"><span data-stu-id="59ac5-122">Change the TextMeshPro - Text component's **Font Size** to 0.17.</span></span>
* <span data-ttu-id="59ac5-123">Altere o **Alinhamento** do componente de texto – TextMeshPro para Centro e Meio.</span><span class="sxs-lookup"><span data-stu-id="59ac5-123">Change the TextMeshPro - Text component's **Alignment** to Center and Middle.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-2.png)

<span data-ttu-id="59ac5-125">Na janela Hierarquia, selecione o objeto **Comentários** e, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Script de Comentários de Âncora (Script)** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="59ac5-125">In the Hierarchy window, select the **Feedback** object still, then in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="59ac5-126">Atribua o objeto **Comentários** ao campo **Texto do Comentário** do componente **Script de Comentário da Âncora (Script)** .</span><span class="sxs-lookup"><span data-stu-id="59ac5-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="59ac5-128">Parabéns</span><span class="sxs-lookup"><span data-stu-id="59ac5-128">Congratulations</span></span>

<span data-ttu-id="59ac5-129">Neste tutorial, você aprendeu a criar um painel de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="59ac5-129">In this tutorial, you learned how to create a UI panel.</span></span> <span data-ttu-id="59ac5-130">Ele exibe o status atual da experiência de Âncoras Espaciais do Azure para fornecer comentários em tempo real aos usuários.</span><span class="sxs-lookup"><span data-stu-id="59ac5-130">It displays the current status of the Azure Spatial Anchors experience for providing users with real-time feedback.</span></span>

[<span data-ttu-id="59ac5-131">Próximo tutorial: 5. Âncoras Espaciais do Azure para o Android e o iOS</span><span class="sxs-lookup"><span data-stu-id="59ac5-131">Next Tutorial: 5. Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)
