---
title: Módulo do ASA de aprendizado do MR âncora espacial do Azure em 2 HoloLens
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326351"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="d40e6-104">Exibindo comentários de âncora espacial do Azure</span><span class="sxs-lookup"><span data-stu-id="d40e6-104">Displaying Azure Spatial Anchor Feedback</span></span>

<span data-ttu-id="d40e6-105">Nesta lição, você saberá mais sobre como fornecer aos usuários com comentários sobre a descoberta de âncora, eventos e status ao usar âncoras espacial do Azure.</span><span class="sxs-lookup"><span data-stu-id="d40e6-105">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="d40e6-106">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="d40e6-106">Objectives:</span></span>

* <span data-ttu-id="d40e6-107">Saiba como configurar um painel de interface do usuário que exibe informações importantes sobre a sessão atual do ASA</span><span class="sxs-lookup"><span data-stu-id="d40e6-107">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="d40e6-108">Compreender e explorar os elementos de comentários que o SDK do ASA torna disponível para usuários</span><span class="sxs-lookup"><span data-stu-id="d40e6-108">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

  

## <a name="instructions"></a><span data-ttu-id="d40e6-109">Instruções</span><span class="sxs-lookup"><span data-stu-id="d40e6-109">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="d40e6-110">Configurar o painel de interface do usuário de comentários do ASA</span><span class="sxs-lookup"><span data-stu-id="d40e6-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="d40e6-111">Nesta lição, não estamos usando "SaveAnchorToDisk" e botões de "ShareAnchor" então, selecione ambos os botões e desmarque a caixa de seleção no painel Inspetor (conforme mostrado abaixo) para ocultar esses botões.</span><span class="sxs-lookup"><span data-stu-id="d40e6-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="d40e6-113">Em seguida, crie o painel de instrução.</span><span class="sxs-lookup"><span data-stu-id="d40e6-113">Next, create the instruction panel.</span></span> <span data-ttu-id="d40e6-114">Inicie clicando com o botão direito no botão "instruções", passe o mouse sobre "objetos 3D" e selecione "textmeshpro-text".</span><span class="sxs-lookup"><span data-stu-id="d40e6-114">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. <span data-ttu-id="d40e6-116">Ajuste a escala e o posicionamento do texto para que corresponda com as instruções na sua cena.</span><span class="sxs-lookup"><span data-stu-id="d40e6-116">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="d40e6-117">Além disso, verifique se que o alinhamento para todo o texto é centralizado.</span><span class="sxs-lookup"><span data-stu-id="d40e6-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="d40e6-118">Exclua o texto de exemplo do editor de texto, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="d40e6-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="d40e6-120">Altere o nome do objeto TextMeshPro para "FeedbackPanel".</span><span class="sxs-lookup"><span data-stu-id="d40e6-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. <span data-ttu-id="d40e6-122">No painel de projeto, selecione "ativos" e clique com botão direito e selecione "Mostrar no explorer".</span><span class="sxs-lookup"><span data-stu-id="d40e6-122">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="d40e6-124">Agora, clique em [aqui](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) baixar os arquivos necessários nas próximas etapas.</span><span class="sxs-lookup"><span data-stu-id="d40e6-124">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="d40e6-125">Depois que o explorer é aberta, selecione a pasta ativos e, em seguida, a pasta "ASAmodulesAssets" e copie o script de comentários de âncora e os arquivos de script de módulo de âncora para a pasta.</span><span class="sxs-lookup"><span data-stu-id="d40e6-125">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="d40e6-127">Observação: se você receber um pop-up perguntando se você gostaria de substituir o antigo ou manter o antigo Certifique-se de selecione Substituir.</span><span class="sxs-lookup"><span data-stu-id="d40e6-127">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="d40e6-128">Agora, volte para a pasta ativos.</span><span class="sxs-lookup"><span data-stu-id="d40e6-128">Now return to the Assets folder.</span></span> <span data-ttu-id="d40e6-129">Em seguida, vá para a pasta "AzureSpatialAnchorsPlugin", a pasta de exemplos e, finalmente, a pasta de scripts e copie o wrapper de demonstração âncoras espacial do Azure para essa pasta.</span><span class="sxs-lookup"><span data-stu-id="d40e6-129">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="d40e6-131">Agora que os arquivos são carregados, verifique se o texto "feedbackpanel" está selecionado na hierarquia de ASA_feedback e clique em "adicionar o componente" e adicione o script de comentários de âncora procurá-lo e selecioná-la depois que ela for exibida.</span><span class="sxs-lookup"><span data-stu-id="d40e6-131">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="d40e6-133">Arraste o objeto de texto "feedbackPanel" da hierarquia de ASA_Feedback no slot vazio abaixo o script conforme mostrado na figura abaixo.</span><span class="sxs-lookup"><span data-stu-id="d40e6-133">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a><span data-ttu-id="d40e6-135">Parabéns</span><span class="sxs-lookup"><span data-stu-id="d40e6-135">Congratulations</span></span>

<span data-ttu-id="d40e6-136">Nesta lição, aprendemos como criar um painel de interface do usuário para exibir o status atual da experiência de âncora espacial do Azure para fornecer o usuário com comentários em tempo real.</span><span class="sxs-lookup"><span data-stu-id="d40e6-136">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


