---
title: Diretrizes de design de iniciador do aplicativo 3D
description: Um inicializador de aplicativos 3D é um objeto "físico" casa de realidade mista do usuário que eles podem selecionar para iniciar um aplicativo.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, o iniciador do aplicativo 3D, fone de ouvido imersivo, live cubo
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589282"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="1c44f-104">Diretrizes de design de iniciador do aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="1c44f-104">3D app launcher design guidance</span></span>

<span data-ttu-id="1c44f-105">Quando você coloca em um headset do Windows Mixed Reality imersivo (VR), insira o Windows Mixed Reality doméstica, visualizados como a Paciência com um precipício cercada por Montanhas e água (embora você possa [escolher outros ambientes e até mesmo criar seu próprio](add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="1c44f-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="1c44f-106">Página inicial, dentro do espaço do que isso um usuário é livre para organizar os objetos 3D e os aplicativos que ele está preocupado quando desejado.</span><span class="sxs-lookup"><span data-stu-id="1c44f-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="1c44f-107">Um **inicializador de aplicativos 3D** é um objeto "físico" o usuário do misto casa realidade que eles podem selecionar para iniciar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1c44f-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="1c44f-108">![Exemplo: Iniciador de aplicativos 3D de pássaro flutuante](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c44f-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="1c44f-109">*Exemplo de iniciador de aplicativo 3D de pássaro flutuante (aplicativo fictício)*</span><span class="sxs-lookup"><span data-stu-id="1c44f-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="1c44f-110">Processo de criação de iniciador do aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="1c44f-110">3D app launcher creation process</span></span>

<span data-ttu-id="1c44f-111">Há 3 etapas para criar um inicializador de aplicativos 3D:</span><span class="sxs-lookup"><span data-stu-id="1c44f-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="1c44f-112">Criando e concepting (Este artigo)</span><span class="sxs-lookup"><span data-stu-id="1c44f-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="1c44f-113">Modelagem e exportando</span><span class="sxs-lookup"><span data-stu-id="1c44f-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="1c44f-114">Integração ao seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="1c44f-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="1c44f-115">Aplicativos UWP</span><span class="sxs-lookup"><span data-stu-id="1c44f-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="1c44f-116">Aplicativos do Win32</span><span class="sxs-lookup"><span data-stu-id="1c44f-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="1c44f-117">Conceitos de design</span><span class="sxs-lookup"><span data-stu-id="1c44f-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="1c44f-118">Fantástico ainda familiar</span><span class="sxs-lookup"><span data-stu-id="1c44f-118">Fantastic yet familiar</span></span>

<span data-ttu-id="1c44f-119">O ambiente do Windows Mixed Reality que seu iniciador do aplicativo reside no é parte familiar, parte maço de folhas/sci-fi.</span><span class="sxs-lookup"><span data-stu-id="1c44f-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="1c44f-120">Os iniciadores melhor seguem as regras esse mundo.</span><span class="sxs-lookup"><span data-stu-id="1c44f-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="1c44f-121">Pense como você pode tirar um objeto familiar e representativo do seu aplicativo, mas curvar algumas das regras de realidade real.</span><span class="sxs-lookup"><span data-stu-id="1c44f-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="1c44f-122">Resultará mágica.</span><span class="sxs-lookup"><span data-stu-id="1c44f-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="1c44f-123">Intuitivo</span><span class="sxs-lookup"><span data-stu-id="1c44f-123">Intuitive</span></span>

<span data-ttu-id="1c44f-124">Quando você examinar seu inicializador de aplicativos, sua finalidade - o para iniciar seu aplicativo - deve ser óbvia e não deve causar confusão.</span><span class="sxs-lookup"><span data-stu-id="1c44f-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="1c44f-125">Por exemplo, certifique-se de que o iniciador é um representante óbvio o suficiente do seu aplicativo que não será confundido para uma parte da decoração no Cliff House.</span><span class="sxs-lookup"><span data-stu-id="1c44f-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="1c44f-126">O inicializador de aplicativos deve convidar pessoas touch/selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="1c44f-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="1c44f-127">![Exemplo: Iniciador de aplicativo 3D novo Observação](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c44f-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="1c44f-128">*Exemplo de iniciador de aplicativo 3D de Observação atualizado (aplicativo fictício)*</span><span class="sxs-lookup"><span data-stu-id="1c44f-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="1c44f-129">Dimensionamento inicial</span><span class="sxs-lookup"><span data-stu-id="1c44f-129">Home scale</span></span>

<span data-ttu-id="1c44f-130">Inicializadores de aplicativos 3D ao vivo no Cliff House e seu tamanho padrão deve fazer sentido com os outros objetos "físicos" no espaço.</span><span class="sxs-lookup"><span data-stu-id="1c44f-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="1c44f-131">Se você colocar seu inicializador ao lado, digamos, uma fábrica de casa ou alguma móveis, ele deve se sentir em casa, size-wise.</span><span class="sxs-lookup"><span data-stu-id="1c44f-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="1c44f-132">É um bom ponto de partida ver a aparência dele em centímetros cúbicos 30, mas lembre-se de que os usuários podem escalá-lo para cima ou para baixo se desejarem.</span><span class="sxs-lookup"><span data-stu-id="1c44f-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="1c44f-133">Capaz de proprietário</span><span class="sxs-lookup"><span data-stu-id="1c44f-133">Own-able</span></span>

<span data-ttu-id="1c44f-134">O iniciador do aplicativo deve se sentir como um objeto de uma pessoa seria entusiasmada por ter em seu espaço.</span><span class="sxs-lookup"><span data-stu-id="1c44f-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="1c44f-135">Eles vai ser praticamente ao redor em si com essas coisas, para que o iniciador deve se sentir como algo que o pensamento do usuário era desejável para buscar e mantenha próximos.</span><span class="sxs-lookup"><span data-stu-id="1c44f-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="1c44f-136">![Exemplo: Iniciador do aplicativo 3D astro Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c44f-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="1c44f-137">*Exemplo de iniciador de aplicativo 3D astro Warp (aplicativo fictício)*</span><span class="sxs-lookup"><span data-stu-id="1c44f-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="1c44f-138">Reconhecível</span><span class="sxs-lookup"><span data-stu-id="1c44f-138">Recognizable</span></span>

<span data-ttu-id="1c44f-139">Seu inicializador de aplicativos 3D instantaneamente deva expressar a "marca do aplicativo" para as pessoas que vê-lo.</span><span class="sxs-lookup"><span data-stu-id="1c44f-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="1c44f-140">Se você tiver um caractere de estrela ou um objeto especialmente identificável em seu aplicativo, é recomendável usá-la como uma grande parte do seu design.</span><span class="sxs-lookup"><span data-stu-id="1c44f-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="1c44f-141">Em um mundo de realidade misturada, um objeto desenhará mais interesse dos usuários que apenas um logotipo sozinho.</span><span class="sxs-lookup"><span data-stu-id="1c44f-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="1c44f-142">Objetos reconhecíveis se comunicar da marca de maneira rápida e clara.</span><span class="sxs-lookup"><span data-stu-id="1c44f-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="1c44f-143">Volumétricas</span><span class="sxs-lookup"><span data-stu-id="1c44f-143">Volumetric</span></span>

<span data-ttu-id="1c44f-144">Seu aplicativo merece mais do que apenas colocando seu logotipo em um plano simples e encerrando o expediente.</span><span class="sxs-lookup"><span data-stu-id="1c44f-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="1c44f-145">O iniciador deve parecer como um objeto interessante, 3D e físico no espaço do usuário.</span><span class="sxs-lookup"><span data-stu-id="1c44f-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="1c44f-146">Uma boa abordagem é imaginar o que seu aplicativo iria ter um balão em vez de dia de ação de Graças de Macy.</span><span class="sxs-lookup"><span data-stu-id="1c44f-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="1c44f-147">Se perguntar o que seria realmente o wow pessoas como vieram da rua de baixo?</span><span class="sxs-lookup"><span data-stu-id="1c44f-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="1c44f-148">O que seria ótimo de todos os ângulos de exibição?</span><span class="sxs-lookup"><span data-stu-id="1c44f-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="1c44f-149">Dicas de bons modelos 3D</span><span class="sxs-lookup"><span data-stu-id="1c44f-149">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="1c44f-150">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="1c44f-150">Best practices</span></span>
* <span data-ttu-id="1c44f-151">Ao planejar dimensões para seu iniciador do aplicativo, envie-o para aproximadamente um cubo de 30cm.</span><span class="sxs-lookup"><span data-stu-id="1c44f-151">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="1c44f-152">Portanto, um 1: proporção de tamanho de 1:1.</span><span class="sxs-lookup"><span data-stu-id="1c44f-152">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="1c44f-153">Modelos devem ser menos de 10.000 polígonos.</span><span class="sxs-lookup"><span data-stu-id="1c44f-153">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="1c44f-154">Saiba mais sobre níveis de detalhes (LODs) e contagens de triângulo</span><span class="sxs-lookup"><span data-stu-id="1c44f-154">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="1c44f-155">Teste em um fone de ouvido imersivo quando possível.</span><span class="sxs-lookup"><span data-stu-id="1c44f-155">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="1c44f-156">Detalhes da compilação na geometria do seu modelo sempre que possível – não dependem de texturas para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="1c44f-156">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="1c44f-157">Geometria "água apertados" fechada de compilação.</span><span class="sxs-lookup"><span data-stu-id="1c44f-157">Build “water tight” closed geometry.</span></span> <span data-ttu-id="1c44f-158">Não há buracos que não são modelados no.</span><span class="sxs-lookup"><span data-stu-id="1c44f-158">No holes that are not modeled in.</span></span>
* <span data-ttu-id="1c44f-159">Use materiais naturais em seu objeto.</span><span class="sxs-lookup"><span data-stu-id="1c44f-159">Use natural materials in your object.</span></span> <span data-ttu-id="1c44f-160">Imagine criá-lo no mundo real.</span><span class="sxs-lookup"><span data-stu-id="1c44f-160">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="1c44f-161">Verifique se que seu modelo lê bem nesse tamanho e a distância diferente.</span><span class="sxs-lookup"><span data-stu-id="1c44f-161">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="1c44f-162">Quando o modelo estiver pronto para começar, leia as [exportando diretrizes ativos](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span><span class="sxs-lookup"><span data-stu-id="1c44f-162">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="1c44f-163">![Modelo com detalhes sutis na textura](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c44f-163">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="1c44f-164">*Modelo com detalhes sutis na textura*</span><span class="sxs-lookup"><span data-stu-id="1c44f-164">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="1c44f-165">O que evitar</span><span class="sxs-lookup"><span data-stu-id="1c44f-165">What to avoid</span></span>
* <span data-ttu-id="1c44f-166">Não use os detalhes de alto contraste ou padrões de pequenos, ocupados e texturas.</span><span class="sxs-lookup"><span data-stu-id="1c44f-166">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="1c44f-167">Não use geometria thin – ele não funcionar bem em uma distância e alias incorretamente.</span><span class="sxs-lookup"><span data-stu-id="1c44f-167">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="1c44f-168">Não deixe que partes do seu modelo estender muito além de 1: proporção de tamanho de 1:1.</span><span class="sxs-lookup"><span data-stu-id="1c44f-168">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="1c44f-169">Ele cria problemas de dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="1c44f-169">It will create scaling problems.</span></span>

<span data-ttu-id="1c44f-170">![Evite padrões ocupados pequenas, de alto contraste](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c44f-170">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="1c44f-171">*Evite padrões de alto contraste, pequeno, ocupados*</span><span class="sxs-lookup"><span data-stu-id="1c44f-171">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="1c44f-172">Como lidar com tipo</span><span class="sxs-lookup"><span data-stu-id="1c44f-172">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="1c44f-173">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="1c44f-173">Best practices</span></span>
* <span data-ttu-id="1c44f-174">É recomendável que seu tipo consiste em cerca de 1/3 do seu inicializador de aplicativos (ou mais).</span><span class="sxs-lookup"><span data-stu-id="1c44f-174">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="1c44f-175">Tipo é a coisa principal que dá uma ideia que o iniciador é, na verdade, um inicializador, portanto, é bom se ele é bastante significativo de pessoas.</span><span class="sxs-lookup"><span data-stu-id="1c44f-175">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="1c44f-176">Evite fazer tipo super amplo – tente mantê-lo dentro dos limites de iniciadores de aplicativo dimensões do core (mais ou menos).</span><span class="sxs-lookup"><span data-stu-id="1c44f-176">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="1c44f-177">Tipo simples pode funcionar, mas lembre-se de que ele pode ser difícil de ler de determinados ângulos e em determinados ambientes.</span><span class="sxs-lookup"><span data-stu-id="1c44f-177">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="1c44f-178">Você pode considerar a colocação de um objeto sólido ou pano de fundo atrás dele para ajudar com isso.</span><span class="sxs-lookup"><span data-stu-id="1c44f-178">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="1c44f-179">Adicionar dimensão ao seu tipo parece bom em 3D.</span><span class="sxs-lookup"><span data-stu-id="1c44f-179">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="1c44f-180">Sombreamento os lados do tipo de uma cor mais escura diferente pode ajudar a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="1c44f-180">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


<span data-ttu-id="1c44f-181">**Cores de tipo que funcionam**</span><span class="sxs-lookup"><span data-stu-id="1c44f-181">**Type colors that work**</span></span>
* <span data-ttu-id="1c44f-182">Branco</span><span class="sxs-lookup"><span data-stu-id="1c44f-182">White</span></span>
* <span data-ttu-id="1c44f-183">Preto</span><span class="sxs-lookup"><span data-stu-id="1c44f-183">Black</span></span>
* <span data-ttu-id="1c44f-184">Cor semisaturado brilhante</span><span class="sxs-lookup"><span data-stu-id="1c44f-184">Bright semi-saturated color</span></span>

<span data-ttu-id="1c44f-185">![Tipo de cores que funcionam.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c44f-185">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="1c44f-186">*Cores de tipo que funcionam*</span><span class="sxs-lookup"><span data-stu-id="1c44f-186">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="1c44f-187">O que evitar</span><span class="sxs-lookup"><span data-stu-id="1c44f-187">What to avoid</span></span>

<span data-ttu-id="1c44f-188">**Cores de tipo que causam problemas**</span><span class="sxs-lookup"><span data-stu-id="1c44f-188">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="1c44f-189">Mid tons</span><span class="sxs-lookup"><span data-stu-id="1c44f-189">Mid-tones</span></span>
* <span data-ttu-id="1c44f-190">Cinza</span><span class="sxs-lookup"><span data-stu-id="1c44f-190">Gray</span></span>
* <span data-ttu-id="1c44f-191">Cores em excesso saturadas ou sem saturação de cores</span><span class="sxs-lookup"><span data-stu-id="1c44f-191">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="1c44f-192">![Tipo de cores que causam problemas.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c44f-192">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="1c44f-193">*Cores de tipo que causam problemas*</span><span class="sxs-lookup"><span data-stu-id="1c44f-193">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="1c44f-194">Iluminação</span><span class="sxs-lookup"><span data-stu-id="1c44f-194">Lighting</span></span>

<span data-ttu-id="1c44f-195">A iluminação seu iniciador do aplicativo é proveniente do ambiente Cliff House.</span><span class="sxs-lookup"><span data-stu-id="1c44f-195">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="1c44f-196">Certifique-se de testar seu inicializador em vários locais em toda a casa para que fique BOM na luz e sombras.</span><span class="sxs-lookup"><span data-stu-id="1c44f-196">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="1c44f-197">A boa notícia é que se você seguiu as outras diretrizes de design neste documento, o iniciador deve ser em boa forma para a maioria dos iluminação no Cliff House.</span><span class="sxs-lookup"><span data-stu-id="1c44f-197">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="1c44f-198">Bons locais para a aparência do seu iniciador no várias luzes no ambiente de teste são o Studio, a sala de mídia, em qualquer lugar fora e no volta quintal (a área com o jardim concreta).</span><span class="sxs-lookup"><span data-stu-id="1c44f-198">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="1c44f-199">Outro bom teste é colocá-lo na metade de luz e sombra metade e ver sua aparência.</span><span class="sxs-lookup"><span data-stu-id="1c44f-199">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="1c44f-200">![Certifique-se de que seu inicializador ficou BOM na luz e sombras.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c44f-200">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="1c44f-201">*Certifique-se de que seu inicializador ficou BOM na luz e sombras*</span><span class="sxs-lookup"><span data-stu-id="1c44f-201">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="1c44f-202">Texturização</span><span class="sxs-lookup"><span data-stu-id="1c44f-202">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="1c44f-203">As texturas de criação</span><span class="sxs-lookup"><span data-stu-id="1c44f-203">Authoring your textures</span></span>

<span data-ttu-id="1c44f-204">O formato de final de seu inicializador de aplicativos 3D será um arquivo de .glb, que é feito usando o pipeline PBR (fisicamente com base em renderização).</span><span class="sxs-lookup"><span data-stu-id="1c44f-204">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="1c44f-205">Isso pode ser um processo complicado - agora é um bom momento para empregar um artista técnico se você ainda não fez isso.</span><span class="sxs-lookup"><span data-stu-id="1c44f-205">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="1c44f-206">Se você for um corajoso DIY faça você mesmo-er, pena [pesquisar e aprenda a terminologia PBR](http://wiki.polycount.com/wiki/PBR) e o que está acontecendo nos bastidores, antes de começar o ajudará a evitar erros comuns.</span><span class="sxs-lookup"><span data-stu-id="1c44f-206">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](http://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="1c44f-207">![Exemplo: Observação de novo aplicativo](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="1c44f-207">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="1c44f-208">*Exemplo de iniciador de aplicativo 3D de Observação atualizado (aplicativo fictício)*</span><span class="sxs-lookup"><span data-stu-id="1c44f-208">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="1c44f-209">**Ferramenta de criação recomendada**</span><span class="sxs-lookup"><span data-stu-id="1c44f-209">**Recommended authoring tool**</span></span>

<span data-ttu-id="1c44f-210">É recomendável usar [substância pintor](https://www.allegorithmic.com/products/substance-painter) por Allegorithmic para criar o arquivo final.</span><span class="sxs-lookup"><span data-stu-id="1c44f-210">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="1c44f-211">Se você não estiver familiarizado com a criação de sombreadores PBR substância, aqui de pincel uma [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="1c44f-211">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="1c44f-212">(Alternativamente [3D Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), ou [Marmoset Toolbag](https://www.marmoset.co/toolbag/) também funcionaria se você estiver familiarizado com uma destas opções.)</span><span class="sxs-lookup"><span data-stu-id="1c44f-212">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="1c44f-213">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="1c44f-213">Best practices</span></span>

* <span data-ttu-id="1c44f-214">Se seu objeto iniciador de aplicativo foi criado para PBR, ele deve ser bem simples para convertê-lo para o ambiente Cliff House.</span><span class="sxs-lookup"><span data-stu-id="1c44f-214">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="1c44f-215">Nosso sombreador está esperando um fluxo de trabalho do sistema operacional/Aspereza – sombreador PBR Unreal o é um fax fechar.</span><span class="sxs-lookup"><span data-stu-id="1c44f-215">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="1c44f-216">Ao exportar as texturas manter o [textura tamanhos recomendados](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) em mente.</span><span class="sxs-lookup"><span data-stu-id="1c44f-216">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="1c44f-217">Certifique-se de criar objetos de iluminação em tempo real — isso significa que:</span><span class="sxs-lookup"><span data-stu-id="1c44f-217">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="1c44f-218">Evite sombras assadas – ou sombras pintadas</span><span class="sxs-lookup"><span data-stu-id="1c44f-218">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="1c44f-219">Evite assada iluminação em texturas</span><span class="sxs-lookup"><span data-stu-id="1c44f-219">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="1c44f-220">Usar um do material PBR criação de pacotes para instalar os mapas direita gerados para nosso sombreador</span><span class="sxs-lookup"><span data-stu-id="1c44f-220">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="1c44f-221">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c44f-221">See also</span></span>

* [<span data-ttu-id="1c44f-222">Criar modelos 3D para uso na realidade misturada inicial</span><span class="sxs-lookup"><span data-stu-id="1c44f-222">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="1c44f-223">Implementar iniciadores de aplicativo 3D (aplicativos UWP)</span><span class="sxs-lookup"><span data-stu-id="1c44f-223">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="1c44f-224">Implementar iniciadores de aplicativo 3D (aplicativos Win32)</span><span class="sxs-lookup"><span data-stu-id="1c44f-224">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
