---
title: Cor, luz e materiais
description: Criação de conteúdo para realidade misturada requer uma consideração cuidadosa de cor, iluminação e materiais para cada um dos ativos visuais usados em sua experiência.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, cor, luz, materiais
ms.openlocfilehash: 3f8ee8edfe4cbbaf8a55b3c4a9125f752823be9c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589848"
---
# <a name="color-light-and-materials"></a><span data-ttu-id="2a13f-104">Cor, luz e materiais</span><span class="sxs-lookup"><span data-stu-id="2a13f-104">Color, light and materials</span></span>

<span data-ttu-id="2a13f-105">Criação de conteúdo para realidade misturada requer uma consideração cuidadosa de cor, iluminação e materiais para cada um dos ativos visuais usados em sua experiência.</span><span class="sxs-lookup"><span data-stu-id="2a13f-105">Designing content for mixed reality requires careful consideration of color, lighting, and materials for each of the visual assets used in your experience.</span></span> <span data-ttu-id="2a13f-106">Essas decisões podem ser para fins estéticos, como o uso de luz e material para definir o tom de um ambiente imersivo e finalidades funcionais, como o uso de cores surpreendentes para alertar os usuários de uma ação iminente.</span><span class="sxs-lookup"><span data-stu-id="2a13f-106">These decisions can be for both aesthetic purposes, like using light and material to set the tone of an immersive environment, and functional purposes, like using striking colors to alert users of an impending action.</span></span> <span data-ttu-id="2a13f-107">Cada uma dessas decisões deve ser contra as oportunidades e restrições de dispositivo de destino da sua experiência.</span><span class="sxs-lookup"><span data-stu-id="2a13f-107">Each of these decisions must be weighed against the opportunities and constraints of your experience’s target device.</span></span>

<span data-ttu-id="2a13f-108">Abaixo estão as diretrizes específicas para ativos de renderização em headsets envolventes e holographic.</span><span class="sxs-lookup"><span data-stu-id="2a13f-108">Below are guidelines specific to rendering assets on both immersive and holographic headsets.</span></span> <span data-ttu-id="2a13f-109">Muitos deles estão estreitamente relacionados a outras áreas técnicas e uma lista de tópicos relacionados pode ser encontrada na [Consulte também](color,-light-and-materials.md#see-also) seção no final deste artigo.</span><span class="sxs-lookup"><span data-stu-id="2a13f-109">Many of these are closely tied to other technical areas and a list of related subjects can be found in the [See also](color,-light-and-materials.md#see-also) section at the end of this article.</span></span>

## <a name="rendering-on-immersive-vs-holographic-devices"></a><span data-ttu-id="2a13f-110">Renderização em imersivo versus dispositivos holográfico</span><span class="sxs-lookup"><span data-stu-id="2a13f-110">Rendering on immersive vs. holographic devices</span></span>

<span data-ttu-id="2a13f-111">Conteúdo renderizado no fones imersivos em exposição aparecerá visualmente diferente quando comparado ao conteúdo renderizado no holográfica fones de ouvido.</span><span class="sxs-lookup"><span data-stu-id="2a13f-111">Content rendered in immersive headsets will appear visually different when compared to content rendered in holographic headsets.</span></span> <span data-ttu-id="2a13f-112">Enquanto fones imersivos em exposição geralmente renderizar conteúdo quanto você esperaria em uma tela 2D, headsets holográfica como HoloLens use transparente, sequencial de cor RGB exibe para hologramas processa.</span><span class="sxs-lookup"><span data-stu-id="2a13f-112">While immersive headsets generally render content much as you would expect on a 2D screen, holographic headsets like HoloLens use color-sequential, see-through RGB displays to renders holograms.</span></span>

<span data-ttu-id="2a13f-113">Sempre têm tempo para testar suas experiências holográfica um Headset holográfica.</span><span class="sxs-lookup"><span data-stu-id="2a13f-113">Always take time to test your holographic experiences in a holographic headset.</span></span> <span data-ttu-id="2a13f-114">A aparência do conteúdo, mesmo se ele foi desenvolvido especificamente para dispositivos holográfico, serão diferentes conforme visto no secundários monitores, instantâneos e no modo de exibição spectator.</span><span class="sxs-lookup"><span data-stu-id="2a13f-114">The appearance of content, even if it is built specifically for holographic devices, will differ as seen on secondary monitors, snapshots, and in spectator view.</span></span> <span data-ttu-id="2a13f-115">Lembre-se para fazer a ronda experiências com um dispositivo, teste a iluminação de hologramas e observando de todos os lados (bem como acima e abaixo) como seu conteúdo é renderizado.</span><span class="sxs-lookup"><span data-stu-id="2a13f-115">Remember to walk around experiences with a device, testing the lighting of holograms and observing from all sides (as well as from above and below) how your content is rendered.</span></span> <span data-ttu-id="2a13f-116">Certifique-se de testar em uma variedade de configurações de brilho no dispositivo, porque é improvável que todos os usuários compartilharão um padrão assumido, bem como um conjunto diversificado de condições de iluminação.</span><span class="sxs-lookup"><span data-stu-id="2a13f-116">Be sure to test at a range of brightness settings on the device, as it is unlikely all users will share an assumed default, as well as a diverse set of lighting conditions.</span></span>

## <a name="fundamentals-of-rendering-on-holographic-devices"></a><span data-ttu-id="2a13f-117">Conceitos básicos de renderização em dispositivos holographic</span><span class="sxs-lookup"><span data-stu-id="2a13f-117">Fundamentals of rendering on holographic devices</span></span>
* <span data-ttu-id="2a13f-118">**Dispositivos holográfico têm exibe aditivas** – hologramas são criadas com a adição de luz à luz do mundo real – branco aparecerá muito clara, enquanto preta aparecerá transparente.</span><span class="sxs-lookup"><span data-stu-id="2a13f-118">**Holographic devices have additive displays** – Holograms are created by adding light to the light from the real world – white will appear brightly, while black will appear transparent.</span></span>
* <span data-ttu-id="2a13f-119">**Impacto de cores varia de acordo com o ambiente do usuário** – há muitas condições de iluminação diversificado na sala de um usuário.</span><span class="sxs-lookup"><span data-stu-id="2a13f-119">**Colors impact varies with the user’s environment** – There are many diverse lighting conditions in a user’s room.</span></span> <span data-ttu-id="2a13f-120">Crie conteúdo com níveis apropriados de contraste para proporcionar maior clareza.</span><span class="sxs-lookup"><span data-stu-id="2a13f-120">Create content with appropriate levels of contrast to help with clarity.</span></span>
* <span data-ttu-id="2a13f-121">**Evite iluminação dinâmica** – hologramas estão acesos uniformemente nas experiências holográfica são mais eficientes.</span><span class="sxs-lookup"><span data-stu-id="2a13f-121">**Avoid dynamic lighting** – Holograms that are uniformly lit in holographic experiences are the most efficient.</span></span> <span data-ttu-id="2a13f-122">Usando a iluminação avançada e dinâmica provavelmente excederá os recursos de sombreadores móveis.</span><span class="sxs-lookup"><span data-stu-id="2a13f-122">Using advanced, dynamic lighting will likely exceed the capabilities of mobile shaders.</span></span>

## <a name="designing-with-color"></a><span data-ttu-id="2a13f-123">Criando com cor</span><span class="sxs-lookup"><span data-stu-id="2a13f-123">Designing with color</span></span>

<span data-ttu-id="2a13f-124">Devido à natureza exibe aditiva, determinadas cores podem parecer diferentes em telas holographic.</span><span class="sxs-lookup"><span data-stu-id="2a13f-124">Due to the nature of additive displays, certain colors can appear different on holographic displays.</span></span> <span data-ttu-id="2a13f-125">Algumas cores serão exibida em ambientes de iluminação, enquanto outros serão exibidos como o menor impacto.</span><span class="sxs-lookup"><span data-stu-id="2a13f-125">Some colors will pop in lighting environments while others will appear as less impactful.</span></span> <span data-ttu-id="2a13f-126">As cores frias tendem a recuam na tela de fundo, enquanto as cores quentes saltar para o primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="2a13f-126">Cool colors tend to recede into the background while warm colors jump to the foreground.</span></span> <span data-ttu-id="2a13f-127">Considere estes fatores conforme você explora a cor em suas experiências:</span><span class="sxs-lookup"><span data-stu-id="2a13f-127">Consider these factors as you explore color in your experiences:</span></span>
* <span data-ttu-id="2a13f-128">**A gama** -HoloLens se beneficia de uma "gama ampla" de cor, conceitualmente semelhante a Adobe RGB.</span><span class="sxs-lookup"><span data-stu-id="2a13f-128">**Gamut** - HoloLens benefits from a "wide gamut" of color, conceptually similar to Adobe RGB.</span></span> <span data-ttu-id="2a13f-129">Como resultado, algumas cores podem apresentar diferentes qualidades e representação no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2a13f-129">As a result, some colors can exhibit different qualities and representation in the device.</span></span>
* <span data-ttu-id="2a13f-130">**Gama** -o brilho e contraste da imagem renderizada irão variar entre dispositivos envolventes e holographic.</span><span class="sxs-lookup"><span data-stu-id="2a13f-130">**Gamma** - The brightness and contrast of the rendered image will vary between immersive and holographic devices.</span></span> <span data-ttu-id="2a13f-131">Geralmente, essas diferenças em dispositivos aparecem tornar áreas escuras de cores e sombras, mais ou menos brilhante.</span><span class="sxs-lookup"><span data-stu-id="2a13f-131">These device differences often appear to make dark areas of color and shadows, more or less bright.</span></span>
* <span data-ttu-id="2a13f-132">**Separação de cores** -também chamado de "divisão de cor" ou "margem das cores", separação de cores ocorre com mais frequência movendo hologramas (incluindo o cursor) quando um usuário controla objetos com seus olhos.</span><span class="sxs-lookup"><span data-stu-id="2a13f-132">**Color separation** - Also called "color breakup" or "color fringing", color separation most commonly occurs with moving holograms (including cursor) when a user tracks objects with their eyes.</span></span>
* <span data-ttu-id="2a13f-133">**Cor uniformidade** -normalmente hologramas são renderizadas com brilho bastante para que eles mantenham a uniformidade de cores, independentemente da tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="2a13f-133">**Color uniformity** - Typically holograms are rendered brightly enough so that they maintain color uniformity, regardless of the background.</span></span> <span data-ttu-id="2a13f-134">Grandes áreas podem se tornar toques.</span><span class="sxs-lookup"><span data-stu-id="2a13f-134">Large areas may become blotchy.</span></span> <span data-ttu-id="2a13f-135">Evite grandes regiões da brilhante, cor sólida.</span><span class="sxs-lookup"><span data-stu-id="2a13f-135">Avoid large regions of bright, solid color.</span></span>
* <span data-ttu-id="2a13f-136">**Renderização de cores claras** -branco aparece muito claro e deve ser usado com moderação.</span><span class="sxs-lookup"><span data-stu-id="2a13f-136">**Rendering light colors** - White appears very bright and should be used sparingly.</span></span> <span data-ttu-id="2a13f-137">Na maioria dos casos, considere um valor em branco em torno de R 235 G 235 B 235.</span><span class="sxs-lookup"><span data-stu-id="2a13f-137">For most cases, consider a white value around R 235 G 235 B 235.</span></span> <span data-ttu-id="2a13f-138">Grandes áreas brilhantes podem causar discomfort do usuário.</span><span class="sxs-lookup"><span data-stu-id="2a13f-138">Large bright areas may cause user discomfort.</span></span>

<span data-ttu-id="2a13f-139">**Renderização de cores escuras**</span><span class="sxs-lookup"><span data-stu-id="2a13f-139">**Rendering dark colors**</span></span>

<span data-ttu-id="2a13f-140">Devido à natureza exibe aditivas, as cores escuras aparecem transparentes.</span><span class="sxs-lookup"><span data-stu-id="2a13f-140">Due to the nature of additive displays, dark colors appear transparent.</span></span> <span data-ttu-id="2a13f-141">Um objeto preto sólido aparecerá não é diferente do mundo real.</span><span class="sxs-lookup"><span data-stu-id="2a13f-141">A solid black object will appear no different from the real world.</span></span> <span data-ttu-id="2a13f-142">Canal alfa de consulte abaixo.</span><span class="sxs-lookup"><span data-stu-id="2a13f-142">See Alpha channel below.</span></span> <span data-ttu-id="2a13f-143">Para dar a aparência de "preto" Tente um valor RGB cinza escuro muito como 16,16,16.</span><span class="sxs-lookup"><span data-stu-id="2a13f-143">To give the appearance of “black” try a very dark grey RGB value such as 16,16,16.</span></span>

<span data-ttu-id="2a13f-144">![Normal versus gama de cores](images/640px-widegamut.png)</span><span class="sxs-lookup"><span data-stu-id="2a13f-144">![Normal vs. wide color gamut](images/640px-widegamut.png)</span></span><br>
<span data-ttu-id="2a13f-145">*Normal versus gama de cores*</span><span class="sxs-lookup"><span data-stu-id="2a13f-145">*Normal vs. wide color gamut*</span></span>

## <a name="technical-considerations"></a><span data-ttu-id="2a13f-146">Considerações técnicas</span><span class="sxs-lookup"><span data-stu-id="2a13f-146">Technical considerations</span></span>
* <span data-ttu-id="2a13f-147">**Alias** -considerar o alias, irregulares ou "degraus" em que a borda da geometria de um holograma atinge o mundo real.</span><span class="sxs-lookup"><span data-stu-id="2a13f-147">**Aliasing** - Be considerate of aliasing, jagged or “stair steps” where the edge of a hologram’s geometry meets the real world.</span></span> <span data-ttu-id="2a13f-148">Usando texturas com maior nível de detalhes pode agravados esse efeito.</span><span class="sxs-lookup"><span data-stu-id="2a13f-148">Using textures with high detail can aggravate this effect.</span></span> <span data-ttu-id="2a13f-149">Texturas devem ser mapeadas e a filtragem habilitada.</span><span class="sxs-lookup"><span data-stu-id="2a13f-149">Textures should be mapped and filtering enabled.</span></span> <span data-ttu-id="2a13f-150">Considere as bordas do hologramas-dégradé ou adicionando uma textura que cria uma borda preta de borda em torno de objetos.</span><span class="sxs-lookup"><span data-stu-id="2a13f-150">Consider fading the edges of holograms or adding a texture that creates a black edge border around objects.</span></span> <span data-ttu-id="2a13f-151">Sempre que possível, evite geometria fina.</span><span class="sxs-lookup"><span data-stu-id="2a13f-151">Avoid thin geometry where possible.</span></span>
* <span data-ttu-id="2a13f-152">**Canal alfa** -você deve limpar o canal alfa para totalmente transparente para todas as partes em que você não estiver renderizando um holograma.</span><span class="sxs-lookup"><span data-stu-id="2a13f-152">**Alpha channel** - You must clear your alpha channel to fully transparent for any parts where you are not rendering a hologram.</span></span> <span data-ttu-id="2a13f-153">Deixando os leads indefinidos alfabéticos para artefatos visuais ao fazer vídeos/imagens do dispositivo ou com o modo de exibição Spectator.</span><span class="sxs-lookup"><span data-stu-id="2a13f-153">Leaving the alpha undefined leads to visual artifacts when taking images/videos from the device or with Spectator View.</span></span>
* <span data-ttu-id="2a13f-154">**Suavização de textura** – uma vez que a luz é aditivos exibe holográfica, é melhor evitar grandes regiões da brilhante, cor sólida, conforme eles geralmente não produzir o efeito visual desejado.</span><span class="sxs-lookup"><span data-stu-id="2a13f-154">**Texture softening** - Since light is additive in holographic displays, it is best to avoid large regions of bright, solid color as they often do not produce the intended visual effect.</span></span>

## <a name="storytelling-with-light-and-color"></a><span data-ttu-id="2a13f-155">Storytelling com luz e a cor</span><span class="sxs-lookup"><span data-stu-id="2a13f-155">Storytelling with light and color</span></span>

<span data-ttu-id="2a13f-156">Luz e a cor podem ajudar a tornar seu hologramas aparecer mais naturalmente em de um usuário ambiente, bem como oferecem diretrizes e ajuda para o usuário.</span><span class="sxs-lookup"><span data-stu-id="2a13f-156">Light and color can help make your holograms appear more naturally in a user's environment as well as offer guidance and help for the user.</span></span> <span data-ttu-id="2a13f-157">Para obter experiências holográfica, considere estes fatores conforme você explora a cor e iluminação:</span><span class="sxs-lookup"><span data-stu-id="2a13f-157">For holographic experiences, consider these factors as you explore lighting and color:</span></span>
* <span data-ttu-id="2a13f-158">**Vinheta** -um efeito 'vignette' para escurecer materiais pode ajudar a se concentrar a atenção do usuário no centro do campo de visualização.</span><span class="sxs-lookup"><span data-stu-id="2a13f-158">**Vignetting** - A 'vignette' effect to darken materials can help focus the user's attention on the center of the field of view.</span></span> <span data-ttu-id="2a13f-159">Esse efeito escurece material do holograma em alguns radius do vetor de olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="2a13f-159">This effect darkens the hologram's material at some radius from the user's gaze vector.</span></span> <span data-ttu-id="2a13f-160">Observe que isso também é eficaz quando o usuário vê hologramas a partir de um ângulo Oblíquo ou glancing.</span><span class="sxs-lookup"><span data-stu-id="2a13f-160">Note that this is also effective when the user's views holograms from an oblique or glancing angle.</span></span>
* <span data-ttu-id="2a13f-161">**Ênfase** -chamar a atenção para objetos ou pontos de interação de contraste de cores, brilho, e de iluminação.</span><span class="sxs-lookup"><span data-stu-id="2a13f-161">**Emphasis** - Draw attention to objects or points of interaction by contrasting colors, brightness, and lighting.</span></span> <span data-ttu-id="2a13f-162">Para uma visão mais detalhada de métodos de iluminação na narração, consulte [cinematografia Pixel - uma abordagem de iluminação para gráficos de computador](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).</span><span class="sxs-lookup"><span data-stu-id="2a13f-162">For a more detailed look at lighting methods in storytelling, see [Pixel Cinematography - A Lighting Approach for Computer Graphics](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).</span></span>

<span data-ttu-id="2a13f-163">![Uso de cores para mostrar a ênfase para elementos de narração, mostrada aqui em uma cena de fragmentos.](images/640px-fragments.jpg)</span><span class="sxs-lookup"><span data-stu-id="2a13f-163">![Use of color to show emphasis for storytelling elements, shown here in a scene from Fragments.](images/640px-fragments.jpg)</span></span><br>
<span data-ttu-id="2a13f-164">*Uso de cores para mostrar a ênfase para elementos de narração, mostrada aqui em uma cena [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*</span><span class="sxs-lookup"><span data-stu-id="2a13f-164">*Use of color to show emphasis for storytelling elements, shown here in a scene from [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*</span></span>

## <a name="see-also"></a><span data-ttu-id="2a13f-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a13f-165">See also</span></span>
* [<span data-ttu-id="2a13f-166">Separação de cores</span><span class="sxs-lookup"><span data-stu-id="2a13f-166">Color Separation</span></span>](hologram-stability.md#color-separation)
* [<span data-ttu-id="2a13f-167">Hologramas</span><span class="sxs-lookup"><span data-stu-id="2a13f-167">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="2a13f-168">Linguagem de Design da Microsoft - cor</span><span class="sxs-lookup"><span data-stu-id="2a13f-168">Microsoft Design Language - color</span></span>](https://www.microsoft.com/design/color)
* [<span data-ttu-id="2a13f-169">Plataforma universal do Windows - cor</span><span class="sxs-lookup"><span data-stu-id="2a13f-169">Universal Windows Platform - color</span></span>](https://docs.microsoft.com/windows/uwp/style/color)