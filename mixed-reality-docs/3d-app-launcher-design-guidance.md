---
title: Diretrizes de design do iniciador de aplicativo 3D
description: Um iniciador de aplicativo 3D é um objeto "físico" na casa de realidade misturada do usuário que pode selecionar para iniciar um aplicativo.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, iniciador de aplicativos 3D, headset de imersão, cubo ao vivo
ms.openlocfilehash: ce9d242e26d67c8fe5af7ac32f4e910a15715d25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437222"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="770c7-104">Diretrizes de design do iniciador de aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="770c7-104">3D app launcher design guidance</span></span>

<span data-ttu-id="770c7-105">Quando você coloca em um headset do Windows Mixed Reality (VR), entra na casa do Windows Mixed Reality, é visualizado como uma casa em uma Cliff cercada por montanhas e água (embora você possa [escolher outros ambientes e até mesmo criar o seu próprio](add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="770c7-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="770c7-106">No espaço desta página inicial, um usuário é livre para organizar e organizar os objetos 3D e os aplicativos que eles se preocupam de qualquer forma que desejarem.</span><span class="sxs-lookup"><span data-stu-id="770c7-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="770c7-107">Um **iniciador de aplicativo 3D** é um objeto "físico" na casa de realidade misturada do usuário que pode selecionar para iniciar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="770c7-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="770c7-108">![exemplo: inicializador de aplicativo 3D de pássaro flutuante](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="770c7-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="770c7-109">*Exemplo de inicializador de aplicativo 3D de pássaro flutuante (aplicativo fictício)*</span><span class="sxs-lookup"><span data-stu-id="770c7-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="770c7-110">processo de criação do inicializador de aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="770c7-110">3D app launcher creation process</span></span>

<span data-ttu-id="770c7-111">Há três etapas para criar um iniciador de aplicativo 3D:</span><span class="sxs-lookup"><span data-stu-id="770c7-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="770c7-112">Design e conceito (este artigo)</span><span class="sxs-lookup"><span data-stu-id="770c7-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="770c7-113">Modelagem e exportação</span><span class="sxs-lookup"><span data-stu-id="770c7-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="770c7-114">Integrando-o em seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="770c7-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="770c7-115">Aplicativos UWP</span><span class="sxs-lookup"><span data-stu-id="770c7-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="770c7-116">Aplicativos Win32</span><span class="sxs-lookup"><span data-stu-id="770c7-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="770c7-117">Conceitos de design</span><span class="sxs-lookup"><span data-stu-id="770c7-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="770c7-118">Fantástico ainda familiar</span><span class="sxs-lookup"><span data-stu-id="770c7-118">Fantastic yet familiar</span></span>

<span data-ttu-id="770c7-119">O ambiente de realidade mista do Windows em que seu inicializador de aplicativo reside faz parte familiar, parte fantástica/Sci-Fi.</span><span class="sxs-lookup"><span data-stu-id="770c7-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="770c7-120">Os melhores iniciadores seguem as regras deste mundo.</span><span class="sxs-lookup"><span data-stu-id="770c7-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="770c7-121">Imagine como você pode pegar um objeto familiar e representativo de seu aplicativo, mas dobre algumas das regras da realidade real.</span><span class="sxs-lookup"><span data-stu-id="770c7-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="770c7-122">A mágica será resultado.</span><span class="sxs-lookup"><span data-stu-id="770c7-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="770c7-123">Simples</span><span class="sxs-lookup"><span data-stu-id="770c7-123">Intuitive</span></span>

<span data-ttu-id="770c7-124">Ao examinar seu iniciador de aplicativo, sua finalidade-para iniciar seu aplicativo-deve ser óbvio e não deve causar qualquer confusão.</span><span class="sxs-lookup"><span data-stu-id="770c7-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="770c7-125">Por exemplo, certifique-se de que o iniciador é um representante óbvio o suficiente do seu aplicativo que não será confundido por uma parte do décor na casa Cliff.</span><span class="sxs-lookup"><span data-stu-id="770c7-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="770c7-126">Seu iniciador de aplicativo deve convidar pessoas para tocar/selecionar.</span><span class="sxs-lookup"><span data-stu-id="770c7-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="770c7-127">![exemplo: recente observação do iniciador de aplicativos 3D](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="770c7-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="770c7-128">*Observação de novo exemplo de inicializador de aplicativo 3D (aplicativo fictício)*</span><span class="sxs-lookup"><span data-stu-id="770c7-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="770c7-129">Escala inicial</span><span class="sxs-lookup"><span data-stu-id="770c7-129">Home scale</span></span>

<span data-ttu-id="770c7-130">os iniciadores de aplicativos 3D residem na casa Cliff e seu tamanho padrão deve fazer sentido com os outros objetos "físicos" no espaço.</span><span class="sxs-lookup"><span data-stu-id="770c7-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="770c7-131">Se você colocar seu iniciador ao lado de, digamos, uma planta de casa ou em algumas mobílias, deverá sentir em casa, com tamanho próprio.</span><span class="sxs-lookup"><span data-stu-id="770c7-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="770c7-132">Um bom ponto de partida é ver como ele analisa 30 centímetros cúbicos, mas lembre-se de que os usuários podem escalá-los ou diminuí-los se quiserem.</span><span class="sxs-lookup"><span data-stu-id="770c7-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="770c7-133">Com capacidade própria</span><span class="sxs-lookup"><span data-stu-id="770c7-133">Own-able</span></span>

<span data-ttu-id="770c7-134">O inicializador de aplicativos deve se parecer com um objeto que uma pessoa estaria empolgando em seu espaço.</span><span class="sxs-lookup"><span data-stu-id="770c7-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="770c7-135">Eles estarão praticamente circundando-se com essas coisas, portanto, o iniciador deve se sentir como algo que o usuário pensava o suficiente para buscar e manter o próximo.</span><span class="sxs-lookup"><span data-stu-id="770c7-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="770c7-136">![exemplo: inicializador de aplicativo 3D Astro Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="770c7-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="770c7-137">*Exemplo de inicializador de aplicativo 3D Astro Warp (aplicativo fictício)*</span><span class="sxs-lookup"><span data-stu-id="770c7-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="770c7-138">Reconhecível</span><span class="sxs-lookup"><span data-stu-id="770c7-138">Recognizable</span></span>

<span data-ttu-id="770c7-139">Seu iniciador de aplicativo 3D deve expressar instantaneamente "a marca do aplicativo" para as pessoas que a veem.</span><span class="sxs-lookup"><span data-stu-id="770c7-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="770c7-140">Se você tiver um caractere de estrela ou um objeto especialmente identificável em seu aplicativo, é recomendável usá-lo como uma grande parte do design.</span><span class="sxs-lookup"><span data-stu-id="770c7-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="770c7-141">Em um mundo de realidade misturada, um objeto desenhará mais interesse dos usuários do que apenas um logotipo.</span><span class="sxs-lookup"><span data-stu-id="770c7-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="770c7-142">Os objetos reconhecíveis comunicam a marca de forma rápida e clara.</span><span class="sxs-lookup"><span data-stu-id="770c7-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="770c7-143">Volumétricos</span><span class="sxs-lookup"><span data-stu-id="770c7-143">Volumetric</span></span>

<span data-ttu-id="770c7-144">Seu aplicativo merece mais do que apenas colocar seu logotipo em um plano plano e chamá-lo por dia.</span><span class="sxs-lookup"><span data-stu-id="770c7-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="770c7-145">Seu iniciador deve parecer um objeto físico empolgante e 3D no espaço do usuário.</span><span class="sxs-lookup"><span data-stu-id="770c7-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="770c7-146">Uma boa abordagem é imaginar que seu aplicativo terá um balão no dia de graças do Macy liderança.</span><span class="sxs-lookup"><span data-stu-id="770c7-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="770c7-147">Pergunte-se, o que realmente seria Wow quando ele chegou à rua?</span><span class="sxs-lookup"><span data-stu-id="770c7-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="770c7-148">O que pareceria muito com todos os ângulos de exibição?</span><span class="sxs-lookup"><span data-stu-id="770c7-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="770c7-149">![logotipo somente](images/20171016-140436-mixedreality-640px.jpg) *logotipo*</span><span class="sxs-lookup"><span data-stu-id="770c7-149">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="770c7-150">![mais reconhecíveis com um caractere](images/20171016-140557-mixedreality-640px.jpg) *mais reconhecível com um caractere*</span><span class="sxs-lookup"><span data-stu-id="770c7-150">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        <span data-ttu-id="770c7-151">![abordagem simples, não surpreendentemente, sente simples](images/20171016-155101-mixedreality-640px.jpg) *abordagem simples, não surpreendentemente, parece simples*</span><span class="sxs-lookup"><span data-stu-id="770c7-151">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="770c7-152">![abordagem volumétricos melhor demonstra o seu aplicativo](images/20171016-161407-mixedreality-640px.jpg) *abordagem de volumétricos melhor apresenta seu aplicativo*</span><span class="sxs-lookup"><span data-stu-id="770c7-152">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="770c7-153">Dicas para bons modelos 3D</span><span class="sxs-lookup"><span data-stu-id="770c7-153">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="770c7-154">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="770c7-154">Best practices</span></span>
* <span data-ttu-id="770c7-155">Ao planejar dimensões para seu inicializador de aplicativo, retenha para aproximadamente um cubo 30cm.</span><span class="sxs-lookup"><span data-stu-id="770c7-155">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="770c7-156">Portanto, uma proporção de tamanho de 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="770c7-156">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="770c7-157">Os modelos devem estar abaixo de 10.000 polígonos.</span><span class="sxs-lookup"><span data-stu-id="770c7-157">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="770c7-158">Saiba mais sobre contagens de triângulos e níveis de detalhes (LODs)</span><span class="sxs-lookup"><span data-stu-id="770c7-158">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="770c7-159">Teste em um headset de imersão quando possível.</span><span class="sxs-lookup"><span data-stu-id="770c7-159">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="770c7-160">Crie detalhes na geometria do modelo quando possível – não confie em texturas para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="770c7-160">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="770c7-161">Crie uma geometria de "água justa" fechada.</span><span class="sxs-lookup"><span data-stu-id="770c7-161">Build “water tight” closed geometry.</span></span> <span data-ttu-id="770c7-162">Não há buracos que não são modelados no.</span><span class="sxs-lookup"><span data-stu-id="770c7-162">No holes that are not modeled in.</span></span>
* <span data-ttu-id="770c7-163">Use materiais naturais em seu objeto.</span><span class="sxs-lookup"><span data-stu-id="770c7-163">Use natural materials in your object.</span></span> <span data-ttu-id="770c7-164">Imagine criá-lo no mundo real.</span><span class="sxs-lookup"><span data-stu-id="770c7-164">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="770c7-165">Certifique-se de que seu modelo Leia bem em diferentes distâncias e tamanhos.</span><span class="sxs-lookup"><span data-stu-id="770c7-165">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="770c7-166">Quando seu modelo estiver pronto para começar, leia as [diretrizes de exportação de ativos](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span><span class="sxs-lookup"><span data-stu-id="770c7-166">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="770c7-167">Modelo de ![com detalhes sutis na](images/20171013-143334-mixedreality-640px.jpg) de textura</span><span class="sxs-lookup"><span data-stu-id="770c7-167">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="770c7-168">*Modelo com detalhes sutis na textura*</span><span class="sxs-lookup"><span data-stu-id="770c7-168">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="770c7-169">O que evitar</span><span class="sxs-lookup"><span data-stu-id="770c7-169">What to avoid</span></span>
* <span data-ttu-id="770c7-170">Não use detalhes de alto contraste ou padrões e texturas pequenos e ocupados.</span><span class="sxs-lookup"><span data-stu-id="770c7-170">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="770c7-171">Não use a geometria fina – ela não funciona bem em uma distância e terá alias incorreto.</span><span class="sxs-lookup"><span data-stu-id="770c7-171">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="770c7-172">Não deixe que partes do seu modelo estendam muito além da proporção de tamanho de 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="770c7-172">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="770c7-173">Ele criará problemas de dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="770c7-173">It will create scaling problems.</span></span>

<span data-ttu-id="770c7-174">![evitar padrões de alto contraste e pequenos ocupados](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="770c7-174">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="770c7-175">*Evitar padrões de alto contraste, pequenos e ocupados*</span><span class="sxs-lookup"><span data-stu-id="770c7-175">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="770c7-176">Como tratar o tipo</span><span class="sxs-lookup"><span data-stu-id="770c7-176">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="770c7-177">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="770c7-177">Best practices</span></span>
* <span data-ttu-id="770c7-178">Recomendamos que seu tipo seja composto por cerca de 1/3 de seu iniciador de aplicativo (ou mais).</span><span class="sxs-lookup"><span data-stu-id="770c7-178">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="770c7-179">O tipo é o principal coisa que dá às pessoas uma ideia de que seu iniciador é, na verdade, um iniciador, portanto, é bom se ele é bastante substancial.</span><span class="sxs-lookup"><span data-stu-id="770c7-179">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="770c7-180">Evite fazer o tipo superlargo – tente mantê-lo dentro dos limites das dimensões principais de iniciadores de aplicativo (mais ou menos).</span><span class="sxs-lookup"><span data-stu-id="770c7-180">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="770c7-181">O tipo flat pode funcionar, mas lembre-se de que pode ser difícil de exibir alguns ângulos e em determinados ambientes.</span><span class="sxs-lookup"><span data-stu-id="770c7-181">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="770c7-182">Você pode considerar colocá-lo em um objeto sólido ou fazer um pano por trás dele para ajudar com isso.</span><span class="sxs-lookup"><span data-stu-id="770c7-182">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="770c7-183">A adição de dimensão ao seu tipo é agradável em 3D.</span><span class="sxs-lookup"><span data-stu-id="770c7-183">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="770c7-184">Sombreamento dos lados do tipo uma cor diferente e mais escura pode ajudar na legibilidade.</span><span class="sxs-lookup"><span data-stu-id="770c7-184">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="770c7-185">![tipo simples sem um pano de fundo pode ser difícil de Exibir de determinados ângulos e em determinados ambientes](images/flattype-640px.png) *tipo simples sem um pano de fundo pode ser difícil de Exibir de determinados ângulos e em determinados ambientes*</span><span class="sxs-lookup"><span data-stu-id="770c7-185">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="770c7-186">![tipo com um pano de fundo interno pode funcionar bem](images/flattypeandbkg-640px.png) *tipo com um pano de fundo interno pode funcionar bem*</span><span class="sxs-lookup"><span data-stu-id="770c7-186">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="770c7-187">![tipo de extrusão pode funcionar bem se você Sombrear os lados](images/20171016-160221-mixedreality-640px.jpg) *tipo de extrusão pode funcionar bem se você Sombrear os lados*</span><span class="sxs-lookup"><span data-stu-id="770c7-187">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::


<span data-ttu-id="770c7-188">**Digitar cores que funcionam**</span><span class="sxs-lookup"><span data-stu-id="770c7-188">**Type colors that work**</span></span>
* <span data-ttu-id="770c7-189">Branco</span><span class="sxs-lookup"><span data-stu-id="770c7-189">White</span></span>
* <span data-ttu-id="770c7-190">Afasta</span><span class="sxs-lookup"><span data-stu-id="770c7-190">Black</span></span>
* <span data-ttu-id="770c7-191">Cor semisaturada brilhante</span><span class="sxs-lookup"><span data-stu-id="770c7-191">Bright semi-saturated color</span></span>

<span data-ttu-id="770c7-192">![digitar as cores que funcionam.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="770c7-192">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="770c7-193">*Digitar cores que funcionam*</span><span class="sxs-lookup"><span data-stu-id="770c7-193">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="770c7-194">O que evitar</span><span class="sxs-lookup"><span data-stu-id="770c7-194">What to avoid</span></span>

<span data-ttu-id="770c7-195">**Digitar cores que causam problemas**</span><span class="sxs-lookup"><span data-stu-id="770c7-195">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="770c7-196">Tons médios</span><span class="sxs-lookup"><span data-stu-id="770c7-196">Mid-tones</span></span>
* <span data-ttu-id="770c7-197">tonalidade</span><span class="sxs-lookup"><span data-stu-id="770c7-197">Gray</span></span>
* <span data-ttu-id="770c7-198">Cores sobresaturadas ou cores dessaturadas</span><span class="sxs-lookup"><span data-stu-id="770c7-198">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="770c7-199">![digitar as cores que causam problemas.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="770c7-199">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="770c7-200">*Digitar cores que causam problemas*</span><span class="sxs-lookup"><span data-stu-id="770c7-200">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="770c7-201">Iluminação</span><span class="sxs-lookup"><span data-stu-id="770c7-201">Lighting</span></span>

<span data-ttu-id="770c7-202">A iluminação para seu inicializador de aplicativos vem do ambiente de casa da Cliff.</span><span class="sxs-lookup"><span data-stu-id="770c7-202">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="770c7-203">Certifique-se de testar seu iniciador em vários lugares em toda a casa para que ele fique bom na luz e nas sombras.</span><span class="sxs-lookup"><span data-stu-id="770c7-203">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="770c7-204">A boa notícia é que, se você seguiu as outras diretrizes de design deste documento, o iniciador deve estar em uma forma muito boa para a maior parte da luz na casa Cliff.</span><span class="sxs-lookup"><span data-stu-id="770c7-204">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="770c7-205">Bons lugares para testar como o iniciador analisa as várias luzes no ambiente são o estúdio, a sala de mídia, em qualquer lugar fora e na Patio de fundo (a área concreta com o gramado).</span><span class="sxs-lookup"><span data-stu-id="770c7-205">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="770c7-206">Outro bom teste é colocá-lo na metade e na metade da sombra e ver como ele se parece.</span><span class="sxs-lookup"><span data-stu-id="770c7-206">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="770c7-207">![Verifique se o iniciador parece bom tanto na luz quanto nas sombras.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="770c7-207">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="770c7-208">*Verifique se o iniciador parece bom tanto na luz quanto nas sombras*</span><span class="sxs-lookup"><span data-stu-id="770c7-208">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="770c7-209">Texturing</span><span class="sxs-lookup"><span data-stu-id="770c7-209">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="770c7-210">Criando suas texturas</span><span class="sxs-lookup"><span data-stu-id="770c7-210">Authoring your textures</span></span>

<span data-ttu-id="770c7-211">O formato final do seu iniciador de aplicativo 3D será um arquivo. glb, que é feito usando o pipeline PBR (processamento com base fisicamente).</span><span class="sxs-lookup"><span data-stu-id="770c7-211">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="770c7-212">Isso pode ser um processo complicado – agora é um bom momento para empregar um artista técnico, caso ainda não tenha feito isso.</span><span class="sxs-lookup"><span data-stu-id="770c7-212">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="770c7-213">Se você for um corajoso DIY, dedicar o tempo para [Pesquisar e aprender a terminologia do PBR](https://wiki.polycount.com/wiki/PBR) e o que está acontecendo nos bastidores antes de começar irá ajudá-lo a evitar erros comuns.</span><span class="sxs-lookup"><span data-stu-id="770c7-213">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="770c7-214">![exemplo: aplicativo de observações recentes](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="770c7-214">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="770c7-215">*Observação de novo exemplo de inicializador de aplicativo 3D (aplicativo fictício)*</span><span class="sxs-lookup"><span data-stu-id="770c7-215">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="770c7-216">**Ferramenta de criação recomendada**</span><span class="sxs-lookup"><span data-stu-id="770c7-216">**Recommended authoring tool**</span></span>

<span data-ttu-id="770c7-217">É recomendável usar a [pincel de substância](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic para criar o arquivo final.</span><span class="sxs-lookup"><span data-stu-id="770c7-217">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="770c7-218">Se você não estiver familiarizado com a criação de sombreadores de PBR no pintor da substância, aqui está um [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="770c7-218">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="770c7-219">(Alternativamente [3D-revestimento](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/)ou [Marmoset Toolbag](https://www.marmoset.co/toolbag/) também funcionaria se você estivesse mais familiarizado com um deles.)</span><span class="sxs-lookup"><span data-stu-id="770c7-219">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="770c7-220">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="770c7-220">Best practices</span></span>

* <span data-ttu-id="770c7-221">Se o objeto iniciador do aplicativo foi criado para o PBR, deve ser bem simples convertê-lo para o ambiente de casa Cliff.</span><span class="sxs-lookup"><span data-stu-id="770c7-221">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="770c7-222">Nosso sombreador está esperando um fluxo de trabalho de metal/áspero – o sombreador do PBR inreal é um fax próximo.</span><span class="sxs-lookup"><span data-stu-id="770c7-222">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="770c7-223">Ao exportar suas texturas, mantenha os [tamanhos de textura recomendados](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) em mente.</span><span class="sxs-lookup"><span data-stu-id="770c7-223">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="770c7-224">Certifique-se de criar seus objetos para iluminação em tempo real – isso significa:</span><span class="sxs-lookup"><span data-stu-id="770c7-224">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="770c7-225">Evite sombras inclusass – ou sombras pintadas</span><span class="sxs-lookup"><span data-stu-id="770c7-225">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="770c7-226">Evite a iluminação inclusas nas texturas</span><span class="sxs-lookup"><span data-stu-id="770c7-226">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="770c7-227">Use um dos pacotes de criação de material do PBR para obter os mapas corretos gerados para nosso sombreador</span><span class="sxs-lookup"><span data-stu-id="770c7-227">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="770c7-228">Consulte também</span><span class="sxs-lookup"><span data-stu-id="770c7-228">See also</span></span>

* [<span data-ttu-id="770c7-229">Crie modelos 3D para uso na página inicial misturada de realidade</span><span class="sxs-lookup"><span data-stu-id="770c7-229">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="770c7-230">Implementar inicializadores de aplicativos 3D (aplicativos UWP)</span><span class="sxs-lookup"><span data-stu-id="770c7-230">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="770c7-231">Implementar inicializadores de aplicativos 3D (aplicativos Win32)</span><span class="sxs-lookup"><span data-stu-id="770c7-231">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
