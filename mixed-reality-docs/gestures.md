---
title: Gestos
description: Gestos de mão permitem aos usuários executar a ação em realidade misturada.
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: Realidade misturada, gestos, interação, o design
ms.openlocfilehash: afebefddfd620b4697b86616e8ecc930b271dca2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589085"
---
# <a name="gestures"></a><span data-ttu-id="4f30e-104">Gestos</span><span class="sxs-lookup"><span data-stu-id="4f30e-104">Gestures</span></span>

<span data-ttu-id="4f30e-105">Gestos de mão permitem que os usuários realizar uma ação na realidade mista.</span><span class="sxs-lookup"><span data-stu-id="4f30e-105">Hand gestures allow users take action in mixed reality.</span></span> <span data-ttu-id="4f30e-106">Interação baseia **olhares** ao destino e **gesto** ou **voz** para atuar em qualquer elemento foram direcionado.</span><span class="sxs-lookup"><span data-stu-id="4f30e-106">Interaction is built on **gaze** to target and **gesture** or **voice** to act upon whatever element has been targeted.</span></span> <span data-ttu-id="4f30e-107">Gestos de mão não fornecem um local exato no espaço, mas a simplicidade de colocar em um HoloLens e estão interagindo imediatamente com conteúdo permite que os usuários começar a trabalhar sem os outros acessórios.</span><span class="sxs-lookup"><span data-stu-id="4f30e-107">Hand gestures do not provide a precise location in space, but the simplicity of putting on a HoloLens and immediately interacting with content allows users to get to work without any other accessories.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

## <a name="device-support"></a><span data-ttu-id="4f30e-108">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="4f30e-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4f30e-109">Recurso</span><span class="sxs-lookup"><span data-stu-id="4f30e-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="4f30e-110"><a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></span><span class="sxs-lookup"><span data-stu-id="4f30e-110"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="4f30e-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4f30e-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="4f30e-112"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="4f30e-112"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4f30e-113">Gestos</span><span class="sxs-lookup"><span data-stu-id="4f30e-113">Gestures</span></span></td><td style="text-align: center;"> <span data-ttu-id="4f30e-114">✔️</span><span class="sxs-lookup"><span data-stu-id="4f30e-114">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="4f30e-115">✔️</span><span class="sxs-lookup"><span data-stu-id="4f30e-115">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
<tr>
<td> <span data-ttu-id="4f30e-116">Mãos articuladas</span><span class="sxs-lookup"><span data-stu-id="4f30e-116">Articulated hands</span></span></td><td></td><td style="text-align: center;"> <span data-ttu-id="4f30e-117">✔️</span><span class="sxs-lookup"><span data-stu-id="4f30e-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="4f30e-118">Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="4f30e-118">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="gaze-and-commit"></a><span data-ttu-id="4f30e-119">Olhar e confirmação</span><span class="sxs-lookup"><span data-stu-id="4f30e-119">Gaze-and-commit</span></span>

<span data-ttu-id="4f30e-120">Para executar ações, use gestos de mão [olhar principal](gaze.md) como o mecanismo de direcionamento.</span><span class="sxs-lookup"><span data-stu-id="4f30e-120">To take actions, hand gestures use [head gaze](gaze.md) as the targeting mechanism.</span></span> <span data-ttu-id="4f30e-121">A combinação de **olhares** e o **polegar** gesto resulta em um **olhar e confirmação** interação.</span><span class="sxs-lookup"><span data-stu-id="4f30e-121">The combination of **Gaze** and the **Air tap** gesture results in a **gaze-and-commit** interaction.</span></span> <span data-ttu-id="4f30e-122">É uma alternativa à confirmação olhar **ponto-e-confirmação**, habilitado por [controladores de movimento](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="4f30e-122">An alternative to gaze-and-commit is **point-and-commit**, enabled by [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="4f30e-123">Aplicativos que são executados em HoloLens só precisam dar suporte à confirmação olhar como HoloLens não oferece suporte a controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="4f30e-123">Apps that run on HoloLens only need to support gaze-and-commit since HoloLens does not support motion controllers.</span></span> <span data-ttu-id="4f30e-124">Aplicativos que são executados em HoloLens e fones imersivos em exposição devem dar suporte a interações de tanto orientado a olhar e controlado por apontando para fornecer opções dos usuários nos dispositivos de entrada que eles utilizam.</span><span class="sxs-lookup"><span data-stu-id="4f30e-124">Apps that run on both HoloLens and immersive headsets should support both gaze-driven and pointing-driven interactions, to give users choice in what input device they use.</span></span>

## <a name="the-two-core-gestures-of-hololens"></a><span data-ttu-id="4f30e-125">As duas principais gestos do HoloLens</span><span class="sxs-lookup"><span data-stu-id="4f30e-125">The two core gestures of HoloLens</span></span>

<span data-ttu-id="4f30e-126">Atualmente, HoloLens reconhece dois principais gestos-componentes - **polegar** e **Bloom**.</span><span class="sxs-lookup"><span data-stu-id="4f30e-126">HoloLens currently recognizes two core component gestures - **Air tap** and **Bloom**.</span></span> <span data-ttu-id="4f30e-127">Essas interações de dois núcleos são o nível mais baixo de dados espaciais de entrada que um desenvolvedor possa acessar.</span><span class="sxs-lookup"><span data-stu-id="4f30e-127">These two core interactions are the lowest level of spatial input data that a developer can access.</span></span> <span data-ttu-id="4f30e-128">Eles formam a base para uma variedade de ações possíveis do usuário.</span><span class="sxs-lookup"><span data-stu-id="4f30e-128">They form the foundation for a variety of possible user actions.</span></span>

### <a name="air-tap"></a><span data-ttu-id="4f30e-129">Indicador e polegar</span><span class="sxs-lookup"><span data-stu-id="4f30e-129">Air tap</span></span>

<span data-ttu-id="4f30e-130">Indicador e polegar é um gesto de tocar com a mão na vertical, semelhante a um clique do mouse ou selecione.</span><span class="sxs-lookup"><span data-stu-id="4f30e-130">Air tap is a tapping gesture with the hand held upright, similar to a mouse click or select.</span></span> <span data-ttu-id="4f30e-131">Isso é usado na maioria das experiências do HoloLens para o equivalente de "clique" em um elemento de interface do usuário após para direcioná-lo com [olhares](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="4f30e-131">This is used in most HoloLens experiences for the equivalent of a "click" on a UI element after targeting it with [Gaze](gaze.md).</span></span> <span data-ttu-id="4f30e-132">Ele é uma ação universal que você saiba mais uma vez e, em seguida, aplicar em todos os seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4f30e-132">It is a universal action that you learn once and then apply across all your apps.</span></span> <span data-ttu-id="4f30e-133">Outras maneiras de executar select são pressionando o botão único uma [HoloLens Clicker](hardware-accessories.md#hololens-clicker) ou falando a voz de comando "Select".</span><span class="sxs-lookup"><span data-stu-id="4f30e-133">Other ways to perform select are by pressing the single button on a [HoloLens Clicker](hardware-accessories.md#hololens-clicker) or by speaking the voice command "Select".</span></span>

<span data-ttu-id="4f30e-134">![Estado pronto para gestos de mão em HoloLens](images/image9.png)</span><span class="sxs-lookup"><span data-stu-id="4f30e-134">![Ready state for hand gestures on HoloLens](images/image9.png)</span></span><br>
<span data-ttu-id="4f30e-135">*Estado pronto para o indicador e polegar no HoloLens.*</span><span class="sxs-lookup"><span data-stu-id="4f30e-135">*Ready state for Air tap on HoloLens.*</span></span>

<span data-ttu-id="4f30e-136">Indicador e polegar é um gesto discreto.</span><span class="sxs-lookup"><span data-stu-id="4f30e-136">Air tap is a discrete gesture.</span></span> <span data-ttu-id="4f30e-137">Uma seleção é concluída ou não é, uma ação é ou não ocorrer dentro de uma experiência.</span><span class="sxs-lookup"><span data-stu-id="4f30e-137">A selection is either completed or it is not, an action is or is not taken within an experience.</span></span> <span data-ttu-id="4f30e-138">É possível, embora não seja recomendado sem alguma finalidade específica, para criar outros gestos discretos de combinações de componentes principais (por exemplo, um gesto de toque duplo para significar algo diferente de um único toque).</span><span class="sxs-lookup"><span data-stu-id="4f30e-138">It is possible, though not recommended without some specific purpose, to create other discrete gestures from combinations of the main components (e.g. a double-tap gesture to mean something different than a single-tap).</span></span>

<span data-ttu-id="4f30e-139">![Com o dedo na posição pronta e, em seguida, um movimento de toque ou clique em](images/readyandpress.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f30e-139">![Finger in the ready position and then a tap or click motion](images/readyandpress.jpg)</span></span><br>
<span data-ttu-id="4f30e-140">*Como executar um indicador e polegar: Gerar o dedo para a posição de pronto, pressione o dedo para baixo até o toque ou selecione e, em seguida, fazer backup para liberar.*</span><span class="sxs-lookup"><span data-stu-id="4f30e-140">*How to perform an Air tap: Raise your index finger to the ready position, press your finger down to tap or select and then back up to release.*</span></span>

### <a name="bloom"></a><span data-ttu-id="4f30e-141">Bloom</span><span class="sxs-lookup"><span data-stu-id="4f30e-141">Bloom</span></span>

<span data-ttu-id="4f30e-142">Bloom é o gesto de "home" e é reservada para que apenas.</span><span class="sxs-lookup"><span data-stu-id="4f30e-142">Bloom is the "home" gesture and is reserved for that alone.</span></span> <span data-ttu-id="4f30e-143">É uma ação de sistema especial que é usada para retornar ao Menu Iniciar.</span><span class="sxs-lookup"><span data-stu-id="4f30e-143">It is a special system action that is used to go back to the Start Menu.</span></span> <span data-ttu-id="4f30e-144">É equivalente a pressionar a tecla do Windows em um teclado ou o botão do Xbox em um controlador do Xbox.</span><span class="sxs-lookup"><span data-stu-id="4f30e-144">It is equivalent to pressing the Windows key on a keyboard or the Xbox button on an Xbox controller.</span></span> <span data-ttu-id="4f30e-145">O usuário pode usar qualquer um dos mão.</span><span class="sxs-lookup"><span data-stu-id="4f30e-145">The user can use either hand.</span></span>

![Gesto de bloom em HoloLens](images/image10-640px.png)

<span data-ttu-id="4f30e-147">Para fazer o gesto de bloom em HoloLens, mantenha a sua mão, palm, junto com seu alcance.</span><span class="sxs-lookup"><span data-stu-id="4f30e-147">To do the bloom gesture on HoloLens, hold out your hand, palm up, with your fingertips together.</span></span> <span data-ttu-id="4f30e-148">Em seguida, abra a mão.</span><span class="sxs-lookup"><span data-stu-id="4f30e-148">Then open your hand.</span></span> <span data-ttu-id="4f30e-149">Observe que você também sempre pode retornar ao início dizendo "Ei Cortana, Go Home".</span><span class="sxs-lookup"><span data-stu-id="4f30e-149">Note, you can also always return to Start by saying "Hey Cortana, Go Home".</span></span> <span data-ttu-id="4f30e-150">Aplicativos não é possível reagir especificamente a uma ação inicial, como elas são tratadas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="4f30e-150">Apps cannot react specifically to a home action, as these are handled by the system.</span></span>

<span data-ttu-id="4f30e-151">![Gesto de bloom](images/bloom-giphy.gif)</span><span class="sxs-lookup"><span data-stu-id="4f30e-151">![Bloom gesture](images/bloom-giphy.gif)</span></span><br>
<span data-ttu-id="4f30e-152">*Como executar o gesto de bloom em HoloLens.*</span><span class="sxs-lookup"><span data-stu-id="4f30e-152">*How to perform the bloom gesture on HoloLens.*</span></span>

## <a name="composite-gestures"></a><span data-ttu-id="4f30e-153">Gestos de composição</span><span class="sxs-lookup"><span data-stu-id="4f30e-153">Composite gestures</span></span>

<span data-ttu-id="4f30e-154">Aplicativos podem reconhecer os toques de mais de apenas individuais.</span><span class="sxs-lookup"><span data-stu-id="4f30e-154">Apps can recognize more than just individual taps.</span></span> <span data-ttu-id="4f30e-155">Pela combinação de toque, mantenha e de versão com o movimento da mão, gestos de composição mais complexos podem ser executados.</span><span class="sxs-lookup"><span data-stu-id="4f30e-155">By combining tap, hold and release with the movement of the hand, more complex composite gestures can be performed.</span></span> <span data-ttu-id="4f30e-156">Esses gestos de alto nível ou compostos dependem de baixo nível entrados dados espaciais (de indicador e polegar e Bloom) que os desenvolvedores têm acesso ao.</span><span class="sxs-lookup"><span data-stu-id="4f30e-156">These composite or high-level gestures build on the low-level spatial input data (from Air tap and Bloom) that developers have access to.</span></span>

<table>
<tr>
<th> <span data-ttu-id="4f30e-157">Gesto de composição</span><span class="sxs-lookup"><span data-stu-id="4f30e-157">Composite gesture</span></span></th><th> <span data-ttu-id="4f30e-158">Como aplicar</span><span class="sxs-lookup"><span data-stu-id="4f30e-158">How to apply</span></span></th>
</tr><tr>
<td><span data-ttu-id="4f30e-159">Indicador e polegar</span><span class="sxs-lookup"><span data-stu-id="4f30e-159">Air tap</span></span></td><td><span data-ttu-id="4f30e-160">O gesto de toque de ar (bem como outros gestos abaixo) reage somente a um toque específico.</span><span class="sxs-lookup"><span data-stu-id="4f30e-160">The Air tap gesture (as well as the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="4f30e-161">Para detectar outras toques, como o Menu ou compreensão, seu aplicativo deve usar diretamente as interações de baixo nível descritas na seção de gestos de dois componentes principais acima.</span><span class="sxs-lookup"><span data-stu-id="4f30e-161">To detect other taps, such as Menu or Grasp, your app must directly use the lower-level interactions described in two key component gestures section above.</span></span></td>
</tr><tr>
<td><span data-ttu-id="4f30e-162">Tap e hold</span><span class="sxs-lookup"><span data-stu-id="4f30e-162">Tap and hold</span></span></td><td><p><span data-ttu-id="4f30e-163">Espera é simplesmente manter a posição do dedo para baixo do indicador e polegar.</span><span class="sxs-lookup"><span data-stu-id="4f30e-163">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="4f30e-164">A combinação do ar tap e hold permite para uma variedade de mais complexos &quot;clique e arraste&quot; interações quando combinado com o arm movimentação como pegar um objeto em vez de ativá-la ou &quot;mousedown&quot; interações secundárias como mostrar um menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="4f30e-164">The combination of air tap and hold allows for a variety of more complex &quot;click and drag&quot; interactions when combined with arm movement such as picking up an object instead of activating it or &quot;mousedown&quot; secondary interactions such as showing a context menu.</span></span></p><p><span data-ttu-id="4f30e-165">Tenha cuidado ao projetar para esse gesto no entanto, como os usuários pode estar sujeita a relaxar postures suas mãos no decorrer de quaisquer gesto estendido.</span><span class="sxs-lookup"><span data-stu-id="4f30e-165">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during the course of any extended gesture.</span></span></p></td>
</tr><tr>
<td><span data-ttu-id="4f30e-166">Manipulação</span><span class="sxs-lookup"><span data-stu-id="4f30e-166">Manipulation</span></span></td><td><p><span data-ttu-id="4f30e-167">Gestos de manipulação que podem ser usados para mover, redimensionar ou girar um holograma quando desejar que o holograma reagir 1:1 para o usuário&#39;movimentos de mão de s.</span><span class="sxs-lookup"><span data-stu-id="4f30e-167">Manipulation gestures can be used to move, resize or rotate a hologram when you want the hologram to react 1:1 to the user&#39;s hand movements.</span></span> <span data-ttu-id="4f30e-168">Um uso para tais movimentações de 1:1 é permitir que o usuário desenha ou pintar no mundo.</span><span class="sxs-lookup"><span data-stu-id="4f30e-168">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span></p><p><span data-ttu-id="4f30e-169">O direcionamento inicial um gesto de manipulação de deve ser feito pelo olhar ou apontando.</span><span class="sxs-lookup"><span data-stu-id="4f30e-169">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="4f30e-170">Depois que o tap e hold é iniciado, qualquer manipulação do objeto, em seguida, é tratada manualmente os movimentos, liberando o usuário para olhar em volta, embora eles manipulam.</span><span class="sxs-lookup"><span data-stu-id="4f30e-170">Once the tap and hold starts, any manipulation of the object is then handled by hand movements, freeing the user to look around while they manipulate.</span></span></p></td>
</tr><tr>
<td><span data-ttu-id="4f30e-171">Navegação</span><span class="sxs-lookup"><span data-stu-id="4f30e-171">Navigation</span></span></td><td><p><span data-ttu-id="4f30e-172">Gestos de navegação funcionam como um joystick virtual e podem ser usados para navegar de widgets de interface do usuário, como menus radiais.</span><span class="sxs-lookup"><span data-stu-id="4f30e-172">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="4f30e-173">Toque e segure para iniciar o gesto e, em seguida, mova a mão dentro de um cubo 3D normalizado, centralizada em torno de imprensa inicial.</span><span class="sxs-lookup"><span data-stu-id="4f30e-173">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="4f30e-174">Você pode mover sua mão ao longo do eixo X, Y ou Z de um valor de -1 para 1 com 0 sendo o ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="4f30e-174">You can move your hand along the X, Y or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span></p><p><span data-ttu-id="4f30e-175">Navegação pode ser usada para criar com base em velocidade de rolagem contínua ou gestos de zoom, semelhantes a uma interface do usuário de 2D de rolagem clicando no botão do meio do mouse e, em seguida, mover o mouse para cima para baixo.</span><span class="sxs-lookup"><span data-stu-id="4f30e-175">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span></p><p><span data-ttu-id="4f30e-176">A navegação com o rails refere-se à capacidade de reconhecer os movimentos no certo eixo até certo limite é atingido naquele eixo.</span><span class="sxs-lookup"><span data-stu-id="4f30e-176">Navigation with rails refers to the ability of recognizing movements in certain axis until certain threshold is reached on that axis.</span></span> <span data-ttu-id="4f30e-177">Isso só é útil, quando o movimento em mais de um eixo está habilitado em um aplicativo pelo desenvolvedor, por exemplo, se um aplicativo é configurado para reconhecer gestos de navegação em X, eixo Y, mas também especificado eixo com trilhos X.</span><span class="sxs-lookup"><span data-stu-id="4f30e-177">This is only useful, when movement in more than one axis is enabled in an application by the developer, e.g. if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="4f30e-178">Nesse caso, sistema reconhecerá movimentos de mão em eixo X, desde que eles permaneçam dentro de um imaginário rails (guia) no eixo, X se o movimento de mão também ocorre eixo Y.</span><span class="sxs-lookup"><span data-stu-id="4f30e-178">In this case system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on X axis, if hand movement also occurs Y axis.</span></span></p><p><span data-ttu-id="4f30e-179">Em aplicativos 2D, os usuários podem usar gestos de navegação vertical para rolar, aplicar zoom ou arraste dentro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f30e-179">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="4f30e-180">Isso injeta toques de dedo virtual para o aplicativo para simular os gestos de toque do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="4f30e-180">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="4f30e-181">Os usuários podem selecionar qual das seguintes ações ocorrem alternando entre as ferramentas na barra de acima do aplicativo, selecionando o botão ou dizendo &#39; &lt;arrastar/rolagem/Zoom&gt; ferramenta&#39;.</span><span class="sxs-lookup"><span data-stu-id="4f30e-181">Users can select which of these actions take place by toggling between the tools on the bar above the app, either by selecting the button or saying &#39;&lt;Scroll/Drag/Zoom&gt; Tool&#39;.</span></span></p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a><span data-ttu-id="4f30e-182">Reconhecedores de gestos</span><span class="sxs-lookup"><span data-stu-id="4f30e-182">Gesture recognizers</span></span>

<span data-ttu-id="4f30e-183">Uma vantagem de usar o reconhecimento de gesto é que você pode configurar um reconhecedor de gestos apenas para os gestos que de destino atual holograma pode aceitar.</span><span class="sxs-lookup"><span data-stu-id="4f30e-183">One benefit of using gesture recognition is that you can configure a gesture recognizer just for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="4f30e-184">A plataforma fará apenas a necessário para distinguir os gestos com suporte específicos de Desambiguidade.</span><span class="sxs-lookup"><span data-stu-id="4f30e-184">The platform will do only the disambiguation necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="4f30e-185">Dessa forma, um holograma que suporta apenas o polegar pode aceitar qualquer período de tempo entre press e versão, enquanto um holograma que dá suporte tanto tocar e segurar pode promover o tap a uma isenção após o limite de tempo de espera.</span><span class="sxs-lookup"><span data-stu-id="4f30e-185">That way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="4f30e-186">Reconhecimento de mão</span><span class="sxs-lookup"><span data-stu-id="4f30e-186">Hand recognition</span></span>

<span data-ttu-id="4f30e-187">HoloLens reconhece gestos de mão acompanhando a posição de uma ou ambas as mãos que são visíveis para o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4f30e-187">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="4f30e-188">HoloLens vê mãos quando estão em qualquer um de **estado está pronto** (parte posterior a mão voltada para o usuário com o dedo para cima) ou o **estado pressionado** (parte posterior a mão voltada para o usuário com o dedo para baixo).</span><span class="sxs-lookup"><span data-stu-id="4f30e-188">HoloLens sees hands when they are in either the **ready state** (back of the hand facing you with index finger up) or the **pressed state** (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="4f30e-189">Quando as mãos estiverem em outras poses, o HoloLens irá ignorá-los.</span><span class="sxs-lookup"><span data-stu-id="4f30e-189">When hands are in other poses, the HoloLens will ignore them.</span></span>

<span data-ttu-id="4f30e-190">Para cada mão que HoloLens detecta, você pode acessar sua posição (sem orientação) e seu estado pressionado.</span><span class="sxs-lookup"><span data-stu-id="4f30e-190">For each hand that HoloLens detects, you can access its position (without orientation) and its pressed state.</span></span> <span data-ttu-id="4f30e-191">Como a mão se aproximar a borda do quadro de gesto, também são fornecidas com um vetor de direção, você pode mostrar ao usuário para que eles saibam como mover sua mão para obtê-lo novamente no qual o HoloLens podem vê-lo.</span><span class="sxs-lookup"><span data-stu-id="4f30e-191">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="4f30e-192">Quadro de gesto</span><span class="sxs-lookup"><span data-stu-id="4f30e-192">Gesture frame</span></span>

<span data-ttu-id="4f30e-193">Para gestos em HoloLens, a mão deve estar em um "gesto quadro", em um intervalo em que a detecção de gesto câmeras podem ver adequadamente (muito aproximadamente de nariz para foi muito e entre os ombros).</span><span class="sxs-lookup"><span data-stu-id="4f30e-193">For gestures on HoloLens, the hand must be within a “gesture frame”, in a range that the gesture-sensing cameras can see appropriately (very roughly from nose to waist, and between the shoulders).</span></span> <span data-ttu-id="4f30e-194">Os usuários precisam ser treinados para essa área de reconhecimento para o sucesso da ação e para seu próprios conforto (muitos usuários inicialmente pressupor que o quadro de gesto deve ser dentro de sua exibição por meio do HoloLens e mantenha a manter-se uncomfortably para interagir).</span><span class="sxs-lookup"><span data-stu-id="4f30e-194">Users need to be trained on this area of recognition both for success of action and for their own comfort (many users will initially assume that the gesture frame must be within their view through HoloLens, and hold their arms up uncomfortably in order to interact).</span></span> <span data-ttu-id="4f30e-195">Ao usar o HoloLens Clicker, suas mãos não precisa estar dentro do quadro de gesto.</span><span class="sxs-lookup"><span data-stu-id="4f30e-195">When using the HoloLens Clicker, your hands do not need to be within the gesture frame.</span></span>

<span data-ttu-id="4f30e-196">No caso de gestos contínuos em particular, há alguns riscos de usuários movendo suas mãos fora do quadro de gesto no gesto intermediário (ao mover um objeto holográfico, por exemplo) e perder seu resultado pretendido.</span><span class="sxs-lookup"><span data-stu-id="4f30e-196">In the case of continuous gestures in particular, there is some risk of users moving their hands outside of the gesture frame while in mid-gesture (while moving some holographic object, for example), and losing their intended outcome.</span></span>

<span data-ttu-id="4f30e-197">Há três coisas que você deve considerar:</span><span class="sxs-lookup"><span data-stu-id="4f30e-197">There are three things that you should consider:</span></span>
* <span data-ttu-id="4f30e-198">Formação do usuário sobre o quadro de gesto existência e limites aproximados (Isso é ministrado durante a instalação do HoloLens).</span><span class="sxs-lookup"><span data-stu-id="4f30e-198">User education on the gesture frame's existence and approximate boundaries (this is taught during HoloLens setup).</span></span>
* <span data-ttu-id="4f30e-199">Notificar os usuários quando seus gestos estão se aproximando/últimas os limites do quadro de gesto dentro de um aplicativo, para o grau que um gesto perdido leva a resultados indesejados.</span><span class="sxs-lookup"><span data-stu-id="4f30e-199">Notifying users when their gestures are nearing/breaking the gesture frame boundaries within an application, to the degree that a lost gesture will lead to undesired outcomes.</span></span> <span data-ttu-id="4f30e-200">Pesquisas mostram as qualidades principais de tal um sistema de notificação e o shell do HoloLens oferece um bom exemplo desse tipo de notificação (visual, no cursor central, que indica a direção em limites em que está ocorrendo cruzamento).</span><span class="sxs-lookup"><span data-stu-id="4f30e-200">Research has shown the key qualities of such a notification system, and the HoloLens shell provides a good example of this type of notification (visual, on the central cursor, indicating the direction in which boundary crossing is taking place).</span></span>
* <span data-ttu-id="4f30e-201">Consequências de quebrar os limites de quadro do gesto devem ser minimizadas.</span><span class="sxs-lookup"><span data-stu-id="4f30e-201">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="4f30e-202">Em geral, isso significa que o resultado de um gesto deve ser interrompido no limite, mas não invertido.</span><span class="sxs-lookup"><span data-stu-id="4f30e-202">In general, this means that the outcome of a gesture should be stopped at the boundary, but not reversed.</span></span> <span data-ttu-id="4f30e-203">Por exemplo, se um usuário está mudando algum objeto holographic em uma sala, movimentação deve parar quando o quadro de gesto é violado, mas **não** ser retornado para o ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="4f30e-203">For example, if a user is moving some holographic object across a room, movement should stop when the gesture frame is breached, but **not** be returned to the starting point.</span></span> <span data-ttu-id="4f30e-204">O usuário pode experimentar alguns frustração em seguida, mas pode mais rapidamente entender os limites e não precisa reiniciar suas ações pretendidas completas de cada vez.</span><span class="sxs-lookup"><span data-stu-id="4f30e-204">The user may experience some frustration then, but may more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f30e-205">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f30e-205">See also</span></span>
* [<span data-ttu-id="4f30e-206">Mantenha o foco de direcionamento</span><span class="sxs-lookup"><span data-stu-id="4f30e-206">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="4f30e-207">Design de voz</span><span class="sxs-lookup"><span data-stu-id="4f30e-207">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="4f30e-208">Entrada MR 211: Gesto</span><span class="sxs-lookup"><span data-stu-id="4f30e-208">MR Input 211: Gesture</span></span>](holograms-211.md)
* [<span data-ttu-id="4f30e-209">Gestos e controladores de movimento no Unity</span><span class="sxs-lookup"><span data-stu-id="4f30e-209">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="4f30e-210">Olhar, gestos e controladores de movimento no DirectX</span><span class="sxs-lookup"><span data-stu-id="4f30e-210">Gaze, gestures, and motion controllers in DirectX</span></span>](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="4f30e-211">Controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="4f30e-211">Motion controllers</span></span>](motion-controllers.md)