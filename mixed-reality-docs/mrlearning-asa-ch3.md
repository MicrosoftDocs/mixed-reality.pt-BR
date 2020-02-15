---
title: Tutoriais de âncoras espaciais do Azure-3. Exibindo comentários de âncora espacial do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: f4f609a71b05a52e8761e282763a540b42e9f7f5
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250671"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="6cb8e-105">3. exibindo comentários de âncora espacial do Azure</span><span class="sxs-lookup"><span data-stu-id="6cb8e-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="6cb8e-106">Neste tutorial, você aprenderá a fornecer aos usuários comentários sobre a descoberta de âncora, eventos e status ao usar o ASA (âncoras espaciais) do Azure.</span><span class="sxs-lookup"><span data-stu-id="6cb8e-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="6cb8e-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="6cb8e-107">Objectives</span></span>

* <span data-ttu-id="6cb8e-108">Saiba como configurar um painel de interface do usuário que exibe informações importantes sobre a sessão atual do ASA</span><span class="sxs-lookup"><span data-stu-id="6cb8e-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="6cb8e-109">Entender e explorar os elementos de comentários que o SDK do ASA disponibiliza para os usuários</span><span class="sxs-lookup"><span data-stu-id="6cb8e-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="6cb8e-110">Configurar o painel de IU de comentários do ASA</span><span class="sxs-lookup"><span data-stu-id="6cb8e-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="6cb8e-111">Na janela hierarquia, clique com o botão direito do mouse nas **instruções** > objeto **textcontent** e selecione **objeto 3D** > **Text-TextMeshPro** para criar um objeto de texto TextMeshPro como um filho das instruções > objeto textcontent e dê a ele um nome adequado, por exemplo, **comentários**:</span><span class="sxs-lookup"><span data-stu-id="6cb8e-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="6cb8e-113">Para facilitar o trabalho com sua cena, defina a visibilidade da <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">cena</a> para o objeto ParentAnchor como off clicando no ícone de olho à esquerda do objeto.</span><span class="sxs-lookup"><span data-stu-id="6cb8e-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="6cb8e-114">Isso oculta o objeto na janela cena sem alterar sua visibilidade no jogo.</span><span class="sxs-lookup"><span data-stu-id="6cb8e-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="6cb8e-115">Com o objeto de **comentários** ainda selecionado, na janela Inspetor, altere sua posição e tamanho para que ele seja posicionado de forma organizada, abaixo do texto de instrução, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6cb8e-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="6cb8e-116">Alterar a transformação Rect **pos Y** para-0,24</span><span class="sxs-lookup"><span data-stu-id="6cb8e-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="6cb8e-117">Altere a **largura** do Rect Transform para 0,555</span><span class="sxs-lookup"><span data-stu-id="6cb8e-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="6cb8e-118">Altere a **altura** do Rect Transform para 0,1</span><span class="sxs-lookup"><span data-stu-id="6cb8e-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="6cb8e-119">Em seguida, escolha Propriedades da fonte para que o texto caiba bem na área de texto, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6cb8e-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="6cb8e-120">Altere o **estilo de fonte** pro (script) de malha de texto para negrito</span><span class="sxs-lookup"><span data-stu-id="6cb8e-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="6cb8e-121">Altere o **tamanho da fonte** do pro (script de malha de texto) para 0,17</span><span class="sxs-lookup"><span data-stu-id="6cb8e-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="6cb8e-122">Alterar o **alinhamento** pro (script) da malha de texto para o centro e o meio</span><span class="sxs-lookup"><span data-stu-id="6cb8e-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="6cb8e-124">Com o objeto de **comentários** ainda selecionado, na janela Inspetor, use o botão **Adicionar componente** para adicionar o componente **script de âncora de comentário (script)** ao objeto de comentários:</span><span class="sxs-lookup"><span data-stu-id="6cb8e-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="6cb8e-126">Atribua o objeto de **comentários** ao campo de **texto de comentário** do componente script de **âncora (script)** :</span><span class="sxs-lookup"><span data-stu-id="6cb8e-126">Assign the **Feedback** object to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="6cb8e-128">Parabéns</span><span class="sxs-lookup"><span data-stu-id="6cb8e-128">Congratulations</span></span>

<span data-ttu-id="6cb8e-129">Neste tutorial, você aprendeu a criar um painel de interface do usuário para exibir o status atual da experiência de ancoragem espacial do Azure para fornecer aos usuários comentários em tempo real.</span><span class="sxs-lookup"><span data-stu-id="6cb8e-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
