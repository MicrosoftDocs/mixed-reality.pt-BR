---
title: Olhar e confirmar
description: Visão geral do modelo de entrada "olhar e Commit"-usando a entrada de olho ou de cabeçalho.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidade misturada, olhar, direcionamento de olhar, interação, design, acompanhamento de cabeça, acompanhamento de cabeçalho
ms.openlocfilehash: df152f6a3a6e4ae2d6c32a0c56fbb615bcfa7aa8
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375843"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="6904f-104">Olhar e confirmar</span><span class="sxs-lookup"><span data-stu-id="6904f-104">Gaze and commit</span></span>

<span data-ttu-id="6904f-105">_Olhar e commit_ é um modelo de entrada fundamental que está fortemente relacionado com a maneira como estamos interagindo com nossos computadores usando o mouse: _Point & clique_.</span><span class="sxs-lookup"><span data-stu-id="6904f-105">_Gaze and commit_ is a fundamental input model that is closely related with the way we're interacting with our computers using the mouse: _Point & click_.</span></span>
<span data-ttu-id="6904f-106">Nesta página, apresentamos dois tipos de entrada olhar (cabeça e olho-olhar) e tipos diferentes de ações de confirmação.</span><span class="sxs-lookup"><span data-stu-id="6904f-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> 
<span data-ttu-id="6904f-107">_Olhar e commit_ são considerados um modelo de entrada distante com manipulação indireta.</span><span class="sxs-lookup"><span data-stu-id="6904f-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span>
<span data-ttu-id="6904f-108">Isso significa que ele é melhor usado para interagir com conteúdo Holographic que está fora do alcance.</span><span class="sxs-lookup"><span data-stu-id="6904f-108">This means it is best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="6904f-109">Os headsets de realidade misturada podem usar a posição e a orientação da cabeça do usuário para determinar o vetor de direção da cabeça.</span><span class="sxs-lookup"><span data-stu-id="6904f-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="6904f-110">Você pode considerar isso como um laser que aponta para a frente, diretamente entre os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="6904f-110">You can think of this as a laser that points straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="6904f-111">Essa é uma aproximação bastante grosseira da direção para a qual o usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="6904f-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="6904f-112">Seu aplicativo pode interceptar esse raio com objetos virtuais ou do mundo real e desenhar um cursor nesse local para permitir que o usuário saiba o que eles têm como destino no momento.</span><span class="sxs-lookup"><span data-stu-id="6904f-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they are currently targeting.</span></span>

<span data-ttu-id="6904f-113">Além do Head olhar, alguns headsets de realidade misturada, como o HoloLens 2, incluem sistemas de controle ocular que produzem um vetor olhar de olho.</span><span class="sxs-lookup"><span data-stu-id="6904f-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="6904f-114">Isso fornece uma medida refinada da direção para a qual o usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="6904f-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="6904f-115">Em ambos os casos, o olhar representa um sinal importante para a intenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="6904f-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="6904f-116">Quanto melhor o sistema, é possível interpretar e prever as ações pretendidas do usuário, a satisfação do usuário aumenta e o desempenho melhora.</span><span class="sxs-lookup"><span data-stu-id="6904f-116">The better the system can interpret and predict the user's intended actions, user satisfaction increases and performance improves.</span></span>

<span data-ttu-id="6904f-117">Abaixo estão alguns exemplos de como um desenvolvedor de realidade misturada pode se beneficiar do olhar de cabeça ou olho:</span><span class="sxs-lookup"><span data-stu-id="6904f-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="6904f-118">Seu aplicativo pode Interseccionar olhar com os hologramas em sua cena para determinar onde a atenção do usuário é (mais precisa com o olho-olhar).</span><span class="sxs-lookup"><span data-stu-id="6904f-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="6904f-119">Seu aplicativo pode canalizar gestos de canal e pressionamentos de controlador com base no olhar do usuário, permitindo que o usuário selecione, ative, pegue, role ou interaja, de outra maneira, com seus hologramas.</span><span class="sxs-lookup"><span data-stu-id="6904f-119">Your app can channel gestures and controller presses based on the user's gaze, letting the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="6904f-120">Seu aplicativo pode permitir que o usuário Coloque os hologramas em superfícies do mundo real interseccionando seu olhar Ray com a malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="6904f-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="6904f-121">Seu aplicativo pode saber quando o usuário *não* está olhando para a direção de um objeto importante, o que pode levar seu aplicativo a dar indicações visuais e de áudio para virar esse objeto.</span><span class="sxs-lookup"><span data-stu-id="6904f-121">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>


## <a name="device-support"></a><span data-ttu-id="6904f-122">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="6904f-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6904f-123"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="6904f-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="6904f-124"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6904f-124"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6904f-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6904f-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="6904f-126"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="6904f-126"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6904f-127">Foco com a cabeça e confirmação</span><span class="sxs-lookup"><span data-stu-id="6904f-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="6904f-128">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="6904f-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="6904f-129">✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</span><span class="sxs-lookup"><span data-stu-id="6904f-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="6904f-130">➕ Opção alternativa</span><span class="sxs-lookup"><span data-stu-id="6904f-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="6904f-131">Focar com o olhar e confirmar</span><span class="sxs-lookup"><span data-stu-id="6904f-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="6904f-132">❌ não disponível</span><span class="sxs-lookup"><span data-stu-id="6904f-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="6904f-133">✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</span><span class="sxs-lookup"><span data-stu-id="6904f-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="6904f-134">❌ não disponível</span><span class="sxs-lookup"><span data-stu-id="6904f-134">❌ Not available</span></span></td>
    </tr>
</table>


## <a name="gaze"></a><span data-ttu-id="6904f-135">Focar</span><span class="sxs-lookup"><span data-stu-id="6904f-135">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="6904f-136">Olho ou cabeça-olhar?</span><span class="sxs-lookup"><span data-stu-id="6904f-136">Eye- or head-gaze?</span></span>
<span data-ttu-id="6904f-137">Há várias considerações a serem levadas em conta ao enfrentar a pergunta se você deve usar o modelo de entrada "olho-olhar e confirmação" ou "Head-olhar e Commit".</span><span class="sxs-lookup"><span data-stu-id="6904f-137">There are several considerations to take into account when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="6904f-138">Se você estiver desenvolvendo para um headset de imersão ou para o HoloLens (1º gen), a escolha será simples: Head-olhar e Commit.</span><span class="sxs-lookup"><span data-stu-id="6904f-138">If you're developing for an immersive headset or for HoloLens (1st gen) then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="6904f-139">Se você estiver desenvolvendo para o HoloLens 2, a escolha se tornará um pouco mais difícil, por isso é importante entender as vantagens e os desafios que acompanham cada um deles.</span><span class="sxs-lookup"><span data-stu-id="6904f-139">If you're developing for HoloLens 2, the choice becomes a little harder which is why it's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="6904f-140">Compilamos alguns dos nossos profissionais e contratados na tabela abaixo para contrastars em contraste com a olhar de direcionamento.</span><span class="sxs-lookup"><span data-stu-id="6904f-140">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="6904f-141">Isso está longe de ser concluído e sugerimos saber mais sobre o direcionamento olhar para a realidade misturada aqui:</span><span class="sxs-lookup"><span data-stu-id="6904f-141">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="6904f-142">[Acompanhamento de olho no hololens 2](eye-tracking.md): introdução geral do nosso novo recurso de acompanhamento de olho no hololens 2, incluindo algumas diretrizes para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="6904f-142">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="6904f-143">[Olhar interação](eye-gaze-interaction.md)entre os olhos: considerações de design e recomendações ao planejar o uso de acompanhamento de olho como uma entrada.</span><span class="sxs-lookup"><span data-stu-id="6904f-143">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="6904f-144"><strong>Direcionamento de olhar de olho</strong></span><span class="sxs-lookup"><span data-stu-id="6904f-144"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="6904f-145"><strong>Direcionamento de olhar de cabeça</strong></span><span class="sxs-lookup"><span data-stu-id="6904f-145"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="6904f-146">Rápida!</span><span class="sxs-lookup"><span data-stu-id="6904f-146">Fast!</span></span></td>
        <td><span data-ttu-id="6904f-147">Mais lento</span><span class="sxs-lookup"><span data-stu-id="6904f-147">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="6904f-148">Baixo esforço (mal que qualquer movimento do corpo seja necessário)</span><span class="sxs-lookup"><span data-stu-id="6904f-148">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="6904f-149">Pode ser fatiguing-possível discomfort (por exemplo, tensão do pescoço)</span><span class="sxs-lookup"><span data-stu-id="6904f-149">Can be fatiguing - Possible discomfort (e.g., neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="6904f-150">Não requer um cursor, mas é recomendado um comentário sutil</span><span class="sxs-lookup"><span data-stu-id="6904f-150">Does not require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="6904f-151">Requer para mostrar um cursor</span><span class="sxs-lookup"><span data-stu-id="6904f-151">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="6904f-152">Não há movimentos de olho suaves – por exemplo, não é bom para desenhar</span><span class="sxs-lookup"><span data-stu-id="6904f-152">No smooth eye movements – e.g., not good for drawing</span></span></td>
        <td><span data-ttu-id="6904f-153">Mais controlado e explícito</span><span class="sxs-lookup"><span data-stu-id="6904f-153">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="6904f-154">Difícil para destinos muito pequenos (por exemplo, pequenos botões ou weblinks)</span><span class="sxs-lookup"><span data-stu-id="6904f-154">Difficult for very small targets (e.g., tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="6904f-155">Liable!</span><span class="sxs-lookup"><span data-stu-id="6904f-155">Reliable!</span></span> <span data-ttu-id="6904f-156">Ótimo fallback!</span><span class="sxs-lookup"><span data-stu-id="6904f-156">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="6904f-157">...</span><span class="sxs-lookup"><span data-stu-id="6904f-157">...</span></span></td>
        <td><span data-ttu-id="6904f-158">...</span><span class="sxs-lookup"><span data-stu-id="6904f-158">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="6904f-159">Se você usar Head-olhar ou olho-olhar para seu modelo de entrada de olhar e confirmação é fornecido com diferentes conjuntos de restrições de design, que serão abordados separadamente nos artigos de [olho-olhar e confirmação](gaze-and-commit-eyes.md) e [cabeça-olhar e de confirmação](gaze-and-commit-head.md) .</span><span class="sxs-lookup"><span data-stu-id="6904f-159">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model comes with different sets of design constraints, which will be covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="6904f-160">Cursor</span><span class="sxs-lookup"><span data-stu-id="6904f-160">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="6904f-161">Para o Head olhar, a maioria dos aplicativos deve usar um [cursor](cursors.md) (ou outra indicação de auditoria/Visual) para dar ao usuário a confiança no que eles estão prestes a interagir.</span><span class="sxs-lookup"><span data-stu-id="6904f-161">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="6904f-162">Normalmente, você posiciona esse cursor no mundo em que o Head olhar Ray primeiro cruza um objeto, que pode ser um holograma ou uma superfície do mundo real.</span><span class="sxs-lookup"><span data-stu-id="6904f-162">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="6904f-163">Para olhar de olho, geralmente recomendamos *não* mostrar um cursor, pois isso pode rapidamente se tornar confuso e irritante para o usuário.</span><span class="sxs-lookup"><span data-stu-id="6904f-163">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="6904f-164">Em vez disso, destaque sutilmente os destinos visuais ou use um cursor de olho muito fraco para fornecer confiança sobre o que o usuário está prestes a interagir.</span><span class="sxs-lookup"><span data-stu-id="6904f-164">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="6904f-165">Para obter mais informações, confira nossas [diretrizes de design para entrada baseada em olhos](eye-tracking.md) no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6904f-165">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="6904f-166">![um cursor visual de exemplo para mostrar olhar](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="6904f-166">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="6904f-167">*Imagem: um cursor visual de exemplo para mostrar olhar*</span><span class="sxs-lookup"><span data-stu-id="6904f-167">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="6904f-168">Confirmação</span><span class="sxs-lookup"><span data-stu-id="6904f-168">Commit</span></span>
<span data-ttu-id="6904f-169">Depois de falar sobre diferentes maneiras de _olhar_ em um alvo, vamos falar um pouco mais sobre a parte de _confirmação_ em _olhar e commit_.</span><span class="sxs-lookup"><span data-stu-id="6904f-169">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="6904f-170">Depois de direcionar um objeto ou elemento de interface do usuário, o usuário pode interagir ou clicar nele usando uma entrada secundária.</span><span class="sxs-lookup"><span data-stu-id="6904f-170">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="6904f-171">Isso é conhecido como a etapa de confirmação do modelo de entrada.</span><span class="sxs-lookup"><span data-stu-id="6904f-171">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="6904f-172">Os seguintes métodos de confirmação são compatíveis:</span><span class="sxs-lookup"><span data-stu-id="6904f-172">The following commit methods are supported:</span></span>
- <span data-ttu-id="6904f-173">Gesto de toque do ar à mão (ou seja, levante sua mão na frente e reúna o dedo e o polegar)</span><span class="sxs-lookup"><span data-stu-id="6904f-173">Air tap hand gesture (i.e., raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="6904f-174">Diga _"Select"_ ou um dos comandos de voz de destino</span><span class="sxs-lookup"><span data-stu-id="6904f-174">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="6904f-175">Pressione um único botão em um [clicador de HoloLens](hardware-accessories.md#hololens-clicker)</span><span class="sxs-lookup"><span data-stu-id="6904f-175">Press a single button on a [HoloLens Clicker](hardware-accessories.md#hololens-clicker)</span></span>
- <span data-ttu-id="6904f-176">Pressione o botão ' A ' em um gamepad do Xbox</span><span class="sxs-lookup"><span data-stu-id="6904f-176">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="6904f-177">Pressione o botão ' A ' em um controlador adaptável do Xbox</span><span class="sxs-lookup"><span data-stu-id="6904f-177">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="6904f-178">Gesto de toque olhar e Air</span><span class="sxs-lookup"><span data-stu-id="6904f-178">Gaze and air tap gesture</span></span>
<span data-ttu-id="6904f-179">Fechar e abrir dedos indicador e polegar é um gesto de tocar feito com a mão levantada.</span><span class="sxs-lookup"><span data-stu-id="6904f-179">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="6904f-180">Para executar um toque de ar, aumente o seu indicador para a posição pronta, aperte o polegar e aumente o seu dedo de índice de volta para o lançamento.</span><span class="sxs-lookup"><span data-stu-id="6904f-180">To perform an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="6904f-181">No HoloLens (1ª gen), o Air Tap é a entrada secundária mais comum.</span><span class="sxs-lookup"><span data-stu-id="6904f-181">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="6904f-182">![dedo na posição pronta](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="6904f-182">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="6904f-183">**Dedo na posição pronta**</span><span class="sxs-lookup"><span data-stu-id="6904f-183">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6904f-184">![pressione dedo para baixo para tocar ou clique em](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="6904f-184">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="6904f-185">**Pressione dedo para baixo para tocar ou clique**</span><span class="sxs-lookup"><span data-stu-id="6904f-185">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="6904f-186">O toque de ar também está disponível no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6904f-186">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="6904f-187">Ele foi relaxado da versão original.</span><span class="sxs-lookup"><span data-stu-id="6904f-187">It has been relaxed from the original version.</span></span> <span data-ttu-id="6904f-188">Quase todos os tipos de pinçações agora têm suporte, contanto que a mão esteja na vertical e mantendo ainda.</span><span class="sxs-lookup"><span data-stu-id="6904f-188">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="6904f-189">Isso facilita muito para os usuários aprenderem e fazerem o gesto.</span><span class="sxs-lookup"><span data-stu-id="6904f-189">This makes it much easier for users to learn and perform the gesture.</span></span> <span data-ttu-id="6904f-190">Esse novo toque de ar substitui o antigo por meio da mesma API, de modo que os aplicativos existentes terão o novo comportamento automaticamente após a recompilação para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6904f-190">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="6904f-191">Olhar e comando de voz "Select"</span><span class="sxs-lookup"><span data-stu-id="6904f-191">Gaze and "Select" voice command</span></span>
<span data-ttu-id="6904f-192">A linha de comando de voz é um dos principais métodos de interação na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="6904f-192">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="6904f-193">Ele fornece um mecanismo sem intervenção e eficiência para controlar o sistema.</span><span class="sxs-lookup"><span data-stu-id="6904f-193">It provides a very powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="6904f-194">Há diferentes tipos de modelos de interação de voz:</span><span class="sxs-lookup"><span data-stu-id="6904f-194">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="6904f-195">O comando genérico "Select" que executa um clique actuation ou Commit como uma entrada secundária.</span><span class="sxs-lookup"><span data-stu-id="6904f-195">The generic "Select" command that performs a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="6904f-196">Os comandos de objeto (por exemplo, "fechar" ou "torná-lo maior") executam e se confirmam em uma ação como uma entrada secundária.</span><span class="sxs-lookup"><span data-stu-id="6904f-196">Object commands (e.g., "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="6904f-197">Os comandos globais (por exemplo, "ir para o início") não exigem um destino.</span><span class="sxs-lookup"><span data-stu-id="6904f-197">Global commands (e.g., "Go to start") don't require a target.</span></span>
- <span data-ttu-id="6904f-198">As interfaces de usuário de conversa ou entidades como Cortana têm um recurso de linguagem natural de ia.</span><span class="sxs-lookup"><span data-stu-id="6904f-198">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="6904f-199">Comandos de voz personalizados</span><span class="sxs-lookup"><span data-stu-id="6904f-199">Custom voice commands</span></span>

<span data-ttu-id="6904f-200">Para obter mais detalhes, bem como uma lista abrangente de comandos de voz disponíveis e como usá-los, confira nossas diretrizes de [comando de voz](voice-design.md) .</span><span class="sxs-lookup"><span data-stu-id="6904f-200">To find out more details as well as a comprehensive list of available voice commands and how to use them, check out our [voice commanding](voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="6904f-201">Olhar e clicador de HoloLens</span><span class="sxs-lookup"><span data-stu-id="6904f-201">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="6904f-202">O clicador de HoloLens é o primeiro dispositivo periférico criado especificamente para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6904f-202">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="6904f-203">Ele está incluído com o HoloLens (1ª gen) Development Edition.</span><span class="sxs-lookup"><span data-stu-id="6904f-203">It is included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="6904f-204">O clicador do HoloLens permite que um usuário clique com o movimento mínimo e confirme como uma entrada secundária.</span><span class="sxs-lookup"><span data-stu-id="6904f-204">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="6904f-205">O clico do HoloLens se conecta ao HoloLens (1º gen) ou ao HoloLens 2 usando o Bluetooth de baixa energia (BTLE).</span><span class="sxs-lookup"><span data-stu-id="6904f-205">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="6904f-206">Mais informações e instruções para emparelhar o dispositivo</span><span class="sxs-lookup"><span data-stu-id="6904f-206">More information and instructions to pair the device</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="6904f-207">*Imagem: clicador de HoloLens*</span><span class="sxs-lookup"><span data-stu-id="6904f-207">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![Clicador de HoloLens](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="6904f-209">Controlador sem fio olhar e Xbox</span><span class="sxs-lookup"><span data-stu-id="6904f-209">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="6904f-210">O controlador sem fio do Xbox executa um clique actuation como uma entrada secundária usando o botão ' A '.</span><span class="sxs-lookup"><span data-stu-id="6904f-210">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="6904f-211">O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar e controlar o sistema.</span><span class="sxs-lookup"><span data-stu-id="6904f-211">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="6904f-212">Se você quiser personalizar o controlador, use o aplicativo de acessórios do Xbox para configurar o controlador sem fio do Xbox.</span><span class="sxs-lookup"><span data-stu-id="6904f-212">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="6904f-213">Como emparelhar um controlador Xbox com seu PC</span><span class="sxs-lookup"><span data-stu-id="6904f-213">How to pair an Xbox controller with your PC</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="6904f-214">*Imagem: controlador sem fio do Xbox*</span><span class="sxs-lookup"><span data-stu-id="6904f-214">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Controlador sem fio do Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="6904f-216">Controlador adaptável olhar e Xbox</span><span class="sxs-lookup"><span data-stu-id="6904f-216">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="6904f-217">Projetado principalmente para atender às necessidades de jogos com mobilidade limitada, o controlador adaptável do Xbox é um hub unificado para dispositivos que ajuda a tornar a realidade misturada mais acessível.</span><span class="sxs-lookup"><span data-stu-id="6904f-217">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="6904f-218">O controlador adaptável do Xbox executa um clique actuation como uma entrada secundária usando o botão ' A '.</span><span class="sxs-lookup"><span data-stu-id="6904f-218">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="6904f-219">O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar e controlar o sistema.</span><span class="sxs-lookup"><span data-stu-id="6904f-219">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="6904f-220">Se você quiser personalizar o controlador, use o aplicativo de acessórios do Xbox para configurar o controlador adaptável do Xbox.</span><span class="sxs-lookup"><span data-stu-id="6904f-220">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="6904f-221">![Controle Adaptável Xbox](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="6904f-221">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="6904f-222">*Controle Adaptável Xbox*</span><span class="sxs-lookup"><span data-stu-id="6904f-222">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="6904f-223">Conecte dispositivos externos, como comutadores, botões, montagens e joysticks, para criar uma experiência de controlador personalizada que seja exclusivamente sua.</span><span class="sxs-lookup"><span data-stu-id="6904f-223">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="6904f-224">As entradas de botão, Thumbstick e gatilho são controladas com dispositivos assistenciais conectados por meio de conectores de 3,5 mm e portas USB.</span><span class="sxs-lookup"><span data-stu-id="6904f-224">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5mm jacks and USB ports.</span></span>

<span data-ttu-id="6904f-225">![Portas do Controle Adaptável Xbox](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="6904f-225">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="6904f-226">*Portas do Controle Adaptável Xbox*</span><span class="sxs-lookup"><span data-stu-id="6904f-226">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="6904f-227">Instruções para emparelhar o dispositivo</span><span class="sxs-lookup"><span data-stu-id="6904f-227">Instructions to pair the device</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="6904f-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Mais informações disponíveis no site do Xbox</a></span><span class="sxs-lookup"><span data-stu-id="6904f-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="6904f-229">Gestos compostos</span><span class="sxs-lookup"><span data-stu-id="6904f-229">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="6904f-230">Fechar e abrir dedos indicador e polegar</span><span class="sxs-lookup"><span data-stu-id="6904f-230">Air tap</span></span>
<span data-ttu-id="6904f-231">O gesto de toque do Air (bem como os outros gestos abaixo) reage apenas a um toque específico.</span><span class="sxs-lookup"><span data-stu-id="6904f-231">The air tap gesture (as well as the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="6904f-232">Para detectar outros toques, como menu ou compreender, seu aplicativo deve usar diretamente as interações de nível inferior descritas na seção dois principais gestos de componente acima.</span><span class="sxs-lookup"><span data-stu-id="6904f-232">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="6904f-233">Fechar e abrir dedos indicador e polegar e manter</span><span class="sxs-lookup"><span data-stu-id="6904f-233">Tap and hold</span></span>
<span data-ttu-id="6904f-234">Manter é simplesmente manter a posição do dedo para baixo no gesto de fechar e abrir dedos indicador e polegar.</span><span class="sxs-lookup"><span data-stu-id="6904f-234">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="6904f-235">A combinação de toque e espera de ar permite uma variedade de interações mais complexas de "clicar e arrastar" quando combinadas com a movimentação do ARM, como a seleção de um objeto, em vez de ativá-lo ou interações de secundários de MouseDown, como mostrar um menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="6904f-235">The combination of air tap and hold allows for a variety of more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="6904f-236">No entanto, tenha cuidado ao projetar o uso desse gesto, pois os usuários podem estar propensos a relaxar suas posturas de mão no decorrer de qualquer gesto estendido.</span><span class="sxs-lookup"><span data-stu-id="6904f-236">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during the course of any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="6904f-237">Manipulação</span><span class="sxs-lookup"><span data-stu-id="6904f-237">Manipulation</span></span>
<span data-ttu-id="6904f-238">Os gestos de manipulação podem ser usados para mover, redimensionar ou girar um holograma quando você quiser que o holograma reaja 1:1 aos movimentos da mão do usuário.</span><span class="sxs-lookup"><span data-stu-id="6904f-238">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="6904f-239">Um uso para essas movimentações de 1:1 é permitir que o usuário desenhe ou pinte no mundo.</span><span class="sxs-lookup"><span data-stu-id="6904f-239">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="6904f-240">O direcionamento inicial de um gesto de manipulação deve ser feito pelo foco ou apontando.</span><span class="sxs-lookup"><span data-stu-id="6904f-240">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="6904f-241">Quando o toque e a suspensão são iniciados, qualquer manipulação do objeto é tratada por movimentos de mão, liberando o usuário para examinar enquanto eles manipulam.</span><span class="sxs-lookup"><span data-stu-id="6904f-241">Once the tap and hold starts, any manipulation of the object is handled by hand movements, freeing the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="6904f-242">Navegação</span><span class="sxs-lookup"><span data-stu-id="6904f-242">Navigation</span></span>
<span data-ttu-id="6904f-243">Os gestos de navegação funcionam como um joystick virtual e podem ser usados para navegar por widgets de interface do usuário, como menus radiais.</span><span class="sxs-lookup"><span data-stu-id="6904f-243">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="6904f-244">Feche e abra os dedos indicador e polegar e mantenha para iniciar o gesto e, em seguida, mova a mão dentro de um cubo 3D normalizado, centralizado em torno do pressionamento inicial.</span><span class="sxs-lookup"><span data-stu-id="6904f-244">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="6904f-245">Você pode mover a mão ao longo do eixo X, Y ou Z de um valor -1 a 1, sendo 0 o ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="6904f-245">You can move your hand along the X, Y or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="6904f-246">A navegação pode ser usada para criar gestos de rolagem ou zoom contínuo baseados em velocidade, semelhante à rolagem de uma interface do usuário 2D com um clique no botão do meio do mouse e, em seguida, a movimentação do mouse para cima e para baixo.</span><span class="sxs-lookup"><span data-stu-id="6904f-246">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="6904f-247">A navegação com Rails refere-se à capacidade de reconhecer movimentos em determinado eixo até que um determinado limite seja atingido nesse eixo.</span><span class="sxs-lookup"><span data-stu-id="6904f-247">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="6904f-248">Isso só é útil quando a movimentação em mais de um eixo está habilitada em um aplicativo pelo desenvolvedor, como se um aplicativo estiver configurado para reconhecer gestos de navegação no eixo X, Y, mas também especificado eixo X com Rails.</span><span class="sxs-lookup"><span data-stu-id="6904f-248">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="6904f-249">Nesse caso, o sistema reconhecerá movimentos de mão no eixo X, desde que eles permaneçam dentro de um trilho imaginário (guia) no eixo X, se a movimentação à mão também ocorrer no eixo Y.</span><span class="sxs-lookup"><span data-stu-id="6904f-249">In this case the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="6904f-250">Em aplicativos 2D, os usuários podem usar gestos de navegação vertical para rolagem, zoom ou operações de arrastar dentro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6904f-250">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="6904f-251">Isso injeta toques de dedo virtuais no aplicativo para simular gestos de toque do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="6904f-251">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="6904f-252">Os usuários podem selecionar quais dessas ações ocorrem alternando entre as ferramentas na barra acima do aplicativo, seja selecionando o botão ou dizendo ' < rolar/arrastar/aplicar zoom na ferramenta de > '.</span><span class="sxs-lookup"><span data-stu-id="6904f-252">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="6904f-253">Mais informações sobre gestos compostos</span><span class="sxs-lookup"><span data-stu-id="6904f-253">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="6904f-254">Reconhecedores de gestos</span><span class="sxs-lookup"><span data-stu-id="6904f-254">Gesture recognizers</span></span>

<span data-ttu-id="6904f-255">Um dos benefícios de usar o reconhecimento de gesto é que você pode configurar um reconhecedor de gesto somente para os gestos que o holograma atualmente direcionado pode aceitar.</span><span class="sxs-lookup"><span data-stu-id="6904f-255">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="6904f-256">A plataforma apenas faz a desambiguidade, conforme necessário, para distinguir os gestos com suporte específicos.</span><span class="sxs-lookup"><span data-stu-id="6904f-256">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="6904f-257">Dessa forma, um holograma que apenas dá suporte ao toque de ar pode aceitar qualquer período de tempo entre Press e Release, enquanto um holograma que dá suporte a TAP e Hold pode promover o toque para uma espera após o limite de tempo de espera.</span><span class="sxs-lookup"><span data-stu-id="6904f-257">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="6904f-258">Reconhecimento de mão</span><span class="sxs-lookup"><span data-stu-id="6904f-258">Hand recognition</span></span>
<span data-ttu-id="6904f-259">O HoloLens reconhece gestos de mão acompanhando a posição de uma ou das duas mãos visíveis para o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6904f-259">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="6904f-260">O HoloLens vê as mãos quando elas estão no estado pronto (parte posterior da mão voltada para você com o dedo indicador para cima) ou no estado pressionado (parte posterior da mão voltada para você com o dedo indicador para baixo).</span><span class="sxs-lookup"><span data-stu-id="6904f-260">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="6904f-261">Quando as mãos estão em outras poses, o HoloLens as ignora.</span><span class="sxs-lookup"><span data-stu-id="6904f-261">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="6904f-262">Para cada mão que o HoloLens detecta, você pode acessar sua posição sem orientação e seu estado pressionado.</span><span class="sxs-lookup"><span data-stu-id="6904f-262">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="6904f-263">Conforme a mão se aproxima da borda do quadro de gesto, você também recebe um vetor de direção, que você pode mostrar ao usuário para que ele saiba como mover a mão para retorná-la ao local em que o HoloLens possa vê-la.</span><span class="sxs-lookup"><span data-stu-id="6904f-263">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="6904f-264">Quadro de gesto</span><span class="sxs-lookup"><span data-stu-id="6904f-264">Gesture frame</span></span>
<span data-ttu-id="6904f-265">Para gestos no HoloLens, a mão deve estar dentro de um quadro de gesto, em um intervalo que as câmeras de detecção de gestos podem ver de forma apropriada, de nariz para Estou e entre ombros.</span><span class="sxs-lookup"><span data-stu-id="6904f-265">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="6904f-266">Os usuários precisam ser treinados nessa área de reconhecimento para o sucesso da ação e para seus próprios confortos.</span><span class="sxs-lookup"><span data-stu-id="6904f-266">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="6904f-267">Inicialmente, muitos usuários assumirão que o quadro de gesto deve estar dentro de sua exibição por meio do HoloLens e manter seus braços de forma inconfortável para interagir.</span><span class="sxs-lookup"><span data-stu-id="6904f-267">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold their arms up uncomfortably in order to interact.</span></span> <span data-ttu-id="6904f-268">Ao usar o clicador de HoloLens, não é necessário que as mãos estejam dentro do quadro de gesto.</span><span class="sxs-lookup"><span data-stu-id="6904f-268">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="6904f-269">No caso de gestos contínuos em particular, há algum risco de que os usuários movam suas mãos fora do quadro de gestos enquanto estiverem em um gesto médio ao mover um objeto Holographic, por exemplo, e perder o resultado pretendido.</span><span class="sxs-lookup"><span data-stu-id="6904f-269">In the case of continuous gestures in particular, there is some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="6904f-270">Há três coisas que você deve considerar:</span><span class="sxs-lookup"><span data-stu-id="6904f-270">There are three things that you should consider:</span></span>

- <span data-ttu-id="6904f-271">Educação do usuário na existência do quadro gesto e limites aproximados.</span><span class="sxs-lookup"><span data-stu-id="6904f-271">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="6904f-272">Isso é ensinado durante a configuração do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6904f-272">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="6904f-273">Notificar os usuários quando seus gestos estiverem se aproximando ou dividindo os limites de quadro de gesto dentro de um aplicativo no grau de um gesto perdido levar a resultados indesejados.</span><span class="sxs-lookup"><span data-stu-id="6904f-273">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="6904f-274">A pesquisa mostrou as principais qualidades desse sistema de notificação.</span><span class="sxs-lookup"><span data-stu-id="6904f-274">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="6904f-275">O Shell do HoloLens fornece um bom exemplo desse tipo de notificação – Visual, no cursor central, indicando a direção na qual o cruzamento de limites está ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="6904f-275">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="6904f-276">As consequências de sair dos limites do quadro do gesto deverão ser minimizadas.</span><span class="sxs-lookup"><span data-stu-id="6904f-276">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="6904f-277">Em geral, isso significa que o resultado de um gesto deve ser interrompido no limite e não revertido.</span><span class="sxs-lookup"><span data-stu-id="6904f-277">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="6904f-278">Por exemplo, se um usuário estiver movendo algum objeto Holographic em uma sala, a movimentação deverá parar quando o quadro do gesto for violado e não retornar ao ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="6904f-278">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="6904f-279">O usuário pode enfrentar alguma frustração, mas pode entender mais rapidamente os limites e não precisa reiniciar suas ações pretendidas todas as vezes.</span><span class="sxs-lookup"><span data-stu-id="6904f-279">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="6904f-280">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6904f-280">See also</span></span>
* [<span data-ttu-id="6904f-281">Interação ocular</span><span class="sxs-lookup"><span data-stu-id="6904f-281">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="6904f-282">Acompanhamento ocular no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6904f-282">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="6904f-283">Focar e esperar</span><span class="sxs-lookup"><span data-stu-id="6904f-283">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="6904f-284">Mãos – Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="6904f-284">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6904f-285">Mãos – Gestos</span><span class="sxs-lookup"><span data-stu-id="6904f-285">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="6904f-286">Mãos – Apontar e confirmar</span><span class="sxs-lookup"><span data-stu-id="6904f-286">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="6904f-287">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="6904f-287">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="6904f-288">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="6904f-288">Voice input</span></span>](voice-input.md)

