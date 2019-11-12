---
title: Tutoriais de âncoras espaciais do Azure-3. Exibindo comentários de âncora espacial do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 9f57cb9874aade2d6b19d0c061fd83eb04b9ef11
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914377"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="d0cb3-105">3. exibindo comentários de âncora espacial do Azure</span><span class="sxs-lookup"><span data-stu-id="d0cb3-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="d0cb3-106">Nesta lição, você aprenderá a fornecer aos usuários comentários sobre a descoberta de âncora, eventos e status ao usar âncoras espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="d0cb3-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="d0cb3-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d0cb3-107">Objectives</span></span>

* <span data-ttu-id="d0cb3-108">Saiba como configurar um painel de interface do usuário que exibe informações importantes sobre a sessão atual do ASA</span><span class="sxs-lookup"><span data-stu-id="d0cb3-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="d0cb3-109">Entender e explorar os elementos de comentários que o SDK do ASA disponibiliza para os usuários</span><span class="sxs-lookup"><span data-stu-id="d0cb3-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="d0cb3-110">Instruções</span><span class="sxs-lookup"><span data-stu-id="d0cb3-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="d0cb3-111">Configurar o painel de IU de comentários do ASA</span><span class="sxs-lookup"><span data-stu-id="d0cb3-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="d0cb3-112">Nesta lição, não estamos usando os botões "SaveAnchorToDisk" e "ShareAnchor", portanto, selecione ambos os botões e desmarque a caixa de seleção no painel Inspetor (conforme mostrado abaixo) para ocultar esses botões.</span><span class="sxs-lookup"><span data-stu-id="d0cb3-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="d0cb3-114">Crie o painel de instruções.</span><span class="sxs-lookup"><span data-stu-id="d0cb3-114">Create the instruction panel.</span></span> <span data-ttu-id="d0cb3-115">Comece clicando com o botão direito do mouse em "instruções", focalize o "objeto 3D" e selecione "textmeshpro-Text".</span><span class="sxs-lookup"><span data-stu-id="d0cb3-115">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="d0cb3-117">Ajuste a escala e o posicionamento do texto para que ele corresponda às instruções em sua cena.</span><span class="sxs-lookup"><span data-stu-id="d0cb3-117">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="d0cb3-118">Além disso, verifique se o alinhamento de todo o texto está centralizado.</span><span class="sxs-lookup"><span data-stu-id="d0cb3-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="d0cb3-119">Em seguida, exclua o texto de exemplo do editor de texto, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="d0cb3-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="d0cb3-121">Altere o nome do objeto TextMeshPro para "FeedbackPanel".</span><span class="sxs-lookup"><span data-stu-id="d0cb3-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="d0cb3-123">Verifique se o texto "feedbackpanel" está selecionado na hierarquia de ASA_feedback, clique em "Adicionar componente" e adicione o script de comentários de âncora pesquisando-o e selecionando-o quando ele for exibido.</span><span class="sxs-lookup"><span data-stu-id="d0cb3-123">Ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. <span data-ttu-id="d0cb3-125">Arraste o objeto de texto "feedbackPanel" da hierarquia ASA_Feedback para o slot vazio abaixo do script, como mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="d0cb3-125">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="d0cb3-127">Parabéns</span><span class="sxs-lookup"><span data-stu-id="d0cb3-127">Congratulations</span></span>

<span data-ttu-id="d0cb3-128">Nesta lição, aprendemos como criar um painel de interface do usuário para exibir o status atual da experiência de ancoragem espacial do Azure para fornecer aos usuários comentários em tempo real.</span><span class="sxs-lookup"><span data-stu-id="d0cb3-128">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>


