---
title: Estudo de caso - HoloStudio 3 da interface do usuário e a interação de design lições aprendidas
description: UI HoloStudio e lições aprendidas de design de interação
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: Windows HoloLens, HoloStudio, realidade misturada
ms.openlocfilehash: 217c489fed3c0588dae1c2753db6ba15da3522c8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590591"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="c4624-104">Estudo de caso - HoloStudio 3 da interface do usuário e a interação de design lições aprendidas</span><span class="sxs-lookup"><span data-stu-id="c4624-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="c4624-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) foi um dos aplicativos da Microsoft primeiro para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c4624-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="c4624-106">Por isso, tivemos que criar novas práticas recomendadas para 3D da interface do usuário e design de interação.</span><span class="sxs-lookup"><span data-stu-id="c4624-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="c4624-107">Fizemos isso por meio de um lote de teste do usuário, criação de protótipos e tentativa e erro.</span><span class="sxs-lookup"><span data-stu-id="c4624-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="c4624-108">Nós sabemos que nem todo mundo tem os recursos à sua disposição para fazer esse tipo de pesquisa, portanto, tínhamos nosso Designer holográfica sênior, Marcus Ghaly, compartilhar três coisas que aprendemos durante o desenvolvimento de HoloStudio sobre design de interface do usuário e a interação para aplicativos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c4624-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="c4624-109">Assista ao vídeo</span><span class="sxs-lookup"><span data-stu-id="c4624-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="c4624-110">Problema 1 #: As pessoas não desejam mover suas criações</span><span class="sxs-lookup"><span data-stu-id="c4624-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="c4624-111">Originalmente projetamos o workbench no HoloStudio como um retângulo, muito como faria no mundo real.</span><span class="sxs-lookup"><span data-stu-id="c4624-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="c4624-112">O problema é que as pessoas têm uma vida útil de experiência que lhes diga para permanecer ainda quando elas são sentada em uma mesa ou trabalhando na frente de um computador, portanto, eles não eram movendo-se a Bancada de trabalho e explorar sua criação 3D de todos os lados.</span><span class="sxs-lookup"><span data-stu-id="c4624-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![O design retangular da Bancada de trabalho em HoloStudio dissuaded usuários de mover-se e ver suas criações de todos os lados.](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="c4624-114">Tínhamos o insight para tornar o workbench de ida e volta, para que não havia nenhum "front" ou desmarque o que deveria ser colocados.</span><span class="sxs-lookup"><span data-stu-id="c4624-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="c4624-115">Quando testamos isso, as pessoas começaram repentinamente mover-se e explorar suas criações por conta própria.</span><span class="sxs-lookup"><span data-stu-id="c4624-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![O design da Bancada de trabalho circular incentivados usuários para fazer a ronda totalmente suas criações.](images/circular-workbench-500px.jpg)

<span data-ttu-id="c4624-117">**O que aprendemos**</span><span class="sxs-lookup"><span data-stu-id="c4624-117">**What we learned**</span></span>

<span data-ttu-id="c4624-118">Sempre ser pensar sobre o que está à vontade para o usuário.</span><span class="sxs-lookup"><span data-stu-id="c4624-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="c4624-119">Tirar proveito de seu espaço físico é um recurso interessante do HoloLens e algo que você não pode fazer com outros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c4624-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="c4624-120">Problema #2: Caixas de diálogo modais, às vezes, estão fora do quadro holográfico</span><span class="sxs-lookup"><span data-stu-id="c4624-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="c4624-121">Às vezes, o usuário pode estar procurando em outra direção de algo que precisa de sua atenção em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4624-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="c4624-122">Em um PC, você pode apenas pop backup uma caixa de diálogo, mas se você fizer isso em da alguém face em um ambiente 3D, ele pode se sentir como a caixa de diálogo está obtendo sua maneira.</span><span class="sxs-lookup"><span data-stu-id="c4624-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="c4624-123">Você precisará delas para ler a mensagem, mas seu instinto é tentar obter para longe dela.</span><span class="sxs-lookup"><span data-stu-id="c4624-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="c4624-124">Essa reação é ótima se você estiver reproduzindo um jogo, mas uma ferramenta projetada para o trabalho, é inferior ao ideal.</span><span class="sxs-lookup"><span data-stu-id="c4624-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="c4624-125">Depois de tentar algumas coisas diferentes, podemos finalmente optou por usar um sistema de "pensados bolha" para nossas caixas de diálogo e adicionado tendrils que os usuários podem seguir para onde a atenção é necessário em nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4624-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="c4624-126">Também fizemos o pulso tendrils, o que significava um senso de direcionalidade, de modo que os usuários sabiam onde ir.</span><span class="sxs-lookup"><span data-stu-id="c4624-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![O sistema de "Bolha considerado" incluído tendrils pulsando em que forneceu um senso de direção, levando os usuários a onde sua atenção era necessário no aplicativo.](images/thought-bubble-500px.jpg)

<span data-ttu-id="c4624-128">**O que aprendemos**</span><span class="sxs-lookup"><span data-stu-id="c4624-128">**What we learned**</span></span>

<span data-ttu-id="c4624-129">É muito mais difícil em 3D para alertar os usuários as coisas precisam prestar atenção.</span><span class="sxs-lookup"><span data-stu-id="c4624-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="c4624-130">Usando os diretores de atenção, como [som espacial](spatial-sound.md), raios de luz ou bolhas de pensamento, podem levar os usuários para onde elas precisam ser.</span><span class="sxs-lookup"><span data-stu-id="c4624-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="c4624-131">Problema #3: Às vezes, interface do usuário pode ser bloqueado por outras hologramas</span><span class="sxs-lookup"><span data-stu-id="c4624-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="c4624-132">Há vezes quando um usuário deseja interagir com um holograma e seus controles de interface do usuário associados, mas eles estão bloqueados do modo de exibição porque outro holograma está na frente delas.</span><span class="sxs-lookup"><span data-stu-id="c4624-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="c4624-133">Enquanto desenvolvíamos HoloStudio, nós usamos a tentativa e erro para chegar a uma solução para isso.</span><span class="sxs-lookup"><span data-stu-id="c4624-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![Um controle de interface do usuário associado a um holograma pode ser bloqueado se não houver outro holograma entre ele e o usuário vestindo HoloLens.](images/ui-blocked-500px.jpg)

<span data-ttu-id="c4624-135">Tentamos movendo o controle de interface do usuário mais próximo ao usuário para que ele não foi possível obter bloqueado, mas encontrado que não estava confortável para o usuário observar um controle que estava perto de você ao mesmo tempo, observando simultaneamente um holograma que estava longe.</span><span class="sxs-lookup"><span data-stu-id="c4624-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="c4624-136">Se, no entanto, movemos o controle na frente de holograma mais próximo ao usuário, eles sentiram como ele foi desanexado do holograma deveria afetar.</span><span class="sxs-lookup"><span data-stu-id="c4624-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="c4624-137">Por fim terminou o espelhamento no controle de interface do usuário e colocá-lo na mesma distância do usuário como o holograma que ele está associado, portanto, ambos se sinta conectados.</span><span class="sxs-lookup"><span data-stu-id="c4624-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="c4624-138">Isso permite que o usuário interaja com o controle, mesmo que ele é foram ocultado.</span><span class="sxs-lookup"><span data-stu-id="c4624-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![A solução: estamos fantasma o controle de interface do usuário, que tanto permitido a interação com o controle e fez se sinta conectado ao holograma ela estava afetando.](images/ghosting-ui-500px.jpg)

<span data-ttu-id="c4624-140">**O que aprendemos**</span><span class="sxs-lookup"><span data-stu-id="c4624-140">**What we learned**</span></span>

<span data-ttu-id="c4624-141">Os usuários precisam ser capazes de acessar facilmente os controles de interface do usuário, mesmo se eles já foram bloqueados, por isso, descubra métodos para garantir que os usuários podem concluir suas tarefas, independentemente de onde seus hologramas estão no mundo real.</span><span class="sxs-lookup"><span data-stu-id="c4624-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="c4624-142">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="c4624-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="c4624-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="c4624-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="c4624-144">Designer holográfica sênior @Microsoft</span><span class="sxs-lookup"><span data-stu-id="c4624-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="c4624-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4624-145">See also</span></span>
* [<span data-ttu-id="c4624-146">Conceitos básicos de interação</span><span class="sxs-lookup"><span data-stu-id="c4624-146">Interaction fundamentals</span></span>](interaction-fundamentals.md)

 
