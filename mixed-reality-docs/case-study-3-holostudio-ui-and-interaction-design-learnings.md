---
title: Estudo de caso-3 HoloStudio de interface do usuário e de design de interação
description: HoloStudio da interface do usuário e de design de interação
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, realidade misturada do Windows
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974825"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="5faba-104">Estudo de caso-3 HoloStudio de interface do usuário e de design de interação</span><span class="sxs-lookup"><span data-stu-id="5faba-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="5faba-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) foi um dos primeiros aplicativos da Microsoft para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5faba-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="5faba-106">Por isso, tivemos que criar novas práticas recomendadas para a interface do usuário 3D e o design de interação.</span><span class="sxs-lookup"><span data-stu-id="5faba-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="5faba-107">Fizemos isso por vários testes de usuário, protótipos e avaliação e erro.</span><span class="sxs-lookup"><span data-stu-id="5faba-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="5faba-108">Sabemos que nem todos têm os recursos em sua disposição para fazer esse tipo de pesquisa, então tivemos nosso designer Sr. Holographic, Marcus Ghaly, compartilhamos três coisas que aprendemos durante o desenvolvimento de HoloStudio sobre o design de interação e a interface do usuário para aplicativos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5faba-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="5faba-109">Assista ao vídeo</span><span class="sxs-lookup"><span data-stu-id="5faba-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="5faba-110">#1 do problema: As pessoas não desejavam se mover em suas criações</span><span class="sxs-lookup"><span data-stu-id="5faba-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="5faba-111">Originalmente, criamos o Workbench em HoloStudio como um retângulo, assim como você encontraria no mundo real.</span><span class="sxs-lookup"><span data-stu-id="5faba-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="5faba-112">O problema é que as pessoas têm um tempo de vida de experiência que os instrui a permanecer ainda quando estiverem sentado em uma mesa ou trabalhando na frente de um computador, de modo que não se estivessem passando pelo Workbench e explorando a criação de 3D de todos os lados.</span><span class="sxs-lookup"><span data-stu-id="5faba-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![O design retangular do Workbench em HoloStudio dissuaded os usuários de se movimentar e ver suas criações de todos os lados.](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="5faba-114">Tivemos a percepção de fazer o Workbench ser arredondado, de forma que não houvesse nenhuma "frente" ou claro que você deveria parar.</span><span class="sxs-lookup"><span data-stu-id="5faba-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="5faba-115">Quando testamos isso, as pessoas repentinamente começaram a percorrer e explorar suas próprias criações por conta própria.</span><span class="sxs-lookup"><span data-stu-id="5faba-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![O design do Workbench circular incentiva os usuários a percorrer o caminho em relação às suas criações.](images/circular-workbench-500px.jpg)

<span data-ttu-id="5faba-117">**O que aprendemos**</span><span class="sxs-lookup"><span data-stu-id="5faba-117">**What we learned**</span></span>

<span data-ttu-id="5faba-118">Sempre esteja pensando sobre o que é confortável para o usuário.</span><span class="sxs-lookup"><span data-stu-id="5faba-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="5faba-119">Tirar proveito do espaço físico é um recurso interessante do HoloLens e algo que você não pode fazer com outros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="5faba-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="5faba-120">#2 do problema: As caixas de diálogo modais às vezes estão fora do quadro Holographic</span><span class="sxs-lookup"><span data-stu-id="5faba-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="5faba-121">Às vezes, o usuário pode estar olhando em uma direção diferente de algo que precisa de sua atenção em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5faba-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="5faba-122">Em um PC, você pode simplesmente exibir uma caixa de diálogo, mas se fizer isso na face de alguém em um ambiente 3D, pode parecer que a caixa de diálogo está ficando de seu jeito.</span><span class="sxs-lookup"><span data-stu-id="5faba-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="5faba-123">Você precisa deles para ler a mensagem, mas seu instinto é tentar sair dela.</span><span class="sxs-lookup"><span data-stu-id="5faba-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="5faba-124">Essa reação será excelente se você estiver jogando um jogo, mas em uma ferramenta projetada para o trabalho, será menos do que o ideal.</span><span class="sxs-lookup"><span data-stu-id="5faba-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="5faba-125">Depois de experimentar algumas coisas diferentes, finalmente temos liquidado o uso de um sistema de "bolha pensada" para nossas caixas de diálogo e adicionamos tendrils que os usuários podem seguir para onde a atenção é necessária em nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5faba-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="5faba-126">Também fizemos o pulso tendrils, que implícita uma noção de direcionalidade para que os usuários soubessem aonde ir.</span><span class="sxs-lookup"><span data-stu-id="5faba-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![O sistema de "bolha pensada" incluiu Pulsing tendrils que fornecia uma noção de direção, levando os usuários a onde sua atenção era necessária no aplicativo.](images/thought-bubble-500px.jpg)

<span data-ttu-id="5faba-128">**O que aprendemos**</span><span class="sxs-lookup"><span data-stu-id="5faba-128">**What we learned**</span></span>

<span data-ttu-id="5faba-129">É muito mais difícil em 3D alertar os usuários sobre as coisas de que precisam para prestar atenção.</span><span class="sxs-lookup"><span data-stu-id="5faba-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="5faba-130">O uso de diretores de atenção, como [som espacial](spatial-sound.md), raios leves ou bolhas de pensamento, pode levar os usuários a onde precisam.</span><span class="sxs-lookup"><span data-stu-id="5faba-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="5faba-131">#3 do problema: Às vezes, a interface do usuário pode ser bloqueada por outros hologramas</span><span class="sxs-lookup"><span data-stu-id="5faba-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="5faba-132">Há ocasiões em que um usuário deseja interagir com um holograma e seus controles de interface do usuário associados, mas eles são bloqueados da exibição porque outro holograma está na frente deles.</span><span class="sxs-lookup"><span data-stu-id="5faba-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="5faba-133">Enquanto estávamos desenvolvendo o HoloStudio, usamos a avaliação e o erro para chegar a uma solução para isso.</span><span class="sxs-lookup"><span data-stu-id="5faba-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![Um controle de interface do usuário associado a um holograma pode se tornar bloqueado se houver outro holograma entre ele e o usuário com o HoloLens.](images/ui-blocked-500px.jpg)

<span data-ttu-id="5faba-135">Tentamos mover o controle da interface do usuário para mais perto de quando ele não podia ser bloqueado, mas descobriu que não era confortável que o usuário examinasse um controle que estava perto de você ao olhar simultaneamente um holograma que estava muito distante.</span><span class="sxs-lookup"><span data-stu-id="5faba-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="5faba-136">No entanto, se movermos o controle na frente do holograma mais próximo para o usuário, eles acharam que ele foi desanexado do holograma que deveria estar afetando.</span><span class="sxs-lookup"><span data-stu-id="5faba-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="5faba-137">Finalmente acabamos de duplicar o controle de interface do usuário e colocá-lo com a mesma distância de um User como o holograma ao qual ele está associado, para que ambos se sintam conectados.</span><span class="sxs-lookup"><span data-stu-id="5faba-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="5faba-138">Isso permite que o usuário interaja com o controle, mesmo que ele tenha sido obscurecido.</span><span class="sxs-lookup"><span data-stu-id="5faba-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![A solução: fantasmas o controle da interface do usuário, que permitia a interação com o controle e o fizemos conectado ao holograma que estava afetando.](images/ghosting-ui-500px.jpg)

<span data-ttu-id="5faba-140">**O que aprendemos**</span><span class="sxs-lookup"><span data-stu-id="5faba-140">**What we learned**</span></span>

<span data-ttu-id="5faba-141">Os usuários precisam ser capazes de acessar facilmente os controles da interface do usuário, mesmo que tenham sido bloqueados; portanto, descubra métodos para garantir que os usuários possam concluir suas tarefas, independentemente de onde estão os hologramas no mundo real.</span><span class="sxs-lookup"><span data-stu-id="5faba-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="5faba-142">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="5faba-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="5faba-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="5faba-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="5faba-144">Designer do Sr. Holographic@Microsoft</span><span class="sxs-lookup"><span data-stu-id="5faba-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="5faba-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5faba-145">See also</span></span>
* [<span data-ttu-id="5faba-146">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="5faba-146">Instinctual interactions</span></span>](interaction-fundamentals.md)

 
