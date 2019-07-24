---
title: Tabela periódica dos elementos
description: A tabela periódica dos elementos é um aplicativo de exemplo de software livre dos laboratórios de design da realidade misturada da Microsoft, em que você pode aprender a criar uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma coleção de objetos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, aplicativo de exemplo, controles
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525335"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="c27e6-104">Tabela periódica dos elementos</span><span class="sxs-lookup"><span data-stu-id="c27e6-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="c27e6-105">Este artigo discute um exemplo exploratório que criamos nos laboratórios de [design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity), um lugar onde compartilhamos nossas aprendeções e sugestões para o desenvolvimento de aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c27e6-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="c27e6-106">Nossos artigos e códigos relacionados ao design irão evoluir à medida que fizermos novas descobertas.</span><span class="sxs-lookup"><span data-stu-id="c27e6-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="c27e6-107">[A tabela periódica dos elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) é um aplicativo de exemplo de código-fonte aberto dos laboratórios de design de realidade misturada da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c27e6-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="c27e6-108">Com esse projeto, você pode aprender a formatar uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma **[coleção de objetos](object-collection.md)** .</span><span class="sxs-lookup"><span data-stu-id="c27e6-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="c27e6-109">Saiba também como criar objetos que respondam às entradas padrão do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c27e6-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="c27e6-110">Você pode usar os componentes deste projeto para criar sua própria experiência de aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c27e6-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabela de período do aplicativo de elementos](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="c27e6-112">Sobre o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c27e6-112">About the app</span></span>

<span data-ttu-id="c27e6-113">A tabela periódica dos elementos visualiza os elementos químicos e cada uma de suas propriedades em um espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="c27e6-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="c27e6-114">Ele incorpora as interações básicas de HoloLens, como olhar e toque de ar.</span><span class="sxs-lookup"><span data-stu-id="c27e6-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="c27e6-115">Os usuários podem aprender sobre os elementos com modelos 3D animados.</span><span class="sxs-lookup"><span data-stu-id="c27e6-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="c27e6-116">Eles podem entender visualmente o Shell de um dos elementos do seu núcleo, que é composto de protoneladas e neutrons.</span><span class="sxs-lookup"><span data-stu-id="c27e6-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="c27e6-117">Informações preliminares</span><span class="sxs-lookup"><span data-stu-id="c27e6-117">Background</span></span>

<span data-ttu-id="c27e6-118">Depois de ter experimentado o HoloLens pela primeira vez, um aplicativo de tabela periódico foi uma ideia que eu sabia que queria experimentar em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c27e6-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="c27e6-119">Como cada elemento tem muitos pontos de dados que são exibidos com texto, pensei que seria um ótimo assunto para explorar a composição tipográfica em um espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="c27e6-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="c27e6-120">Ser capaz de visualizar o modelo de sem interesse do elemento foi outra parte interessante deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c27e6-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="c27e6-121">Criar</span><span class="sxs-lookup"><span data-stu-id="c27e6-121">Design</span></span>

<span data-ttu-id="c27e6-122">Para a exibição padrão da tabela periódica, Imaginai caixas tridimensionais que conteriam o modelo de todos os elementos.</span><span class="sxs-lookup"><span data-stu-id="c27e6-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="c27e6-123">A superfície de cada caixa seria translúcida para que o usuário pudesse obter uma ideia aproximada do volume do elemento.</span><span class="sxs-lookup"><span data-stu-id="c27e6-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="c27e6-124">Com o olhar e o toque do Air, o usuário pode abrir uma exibição detalhada de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="c27e6-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="c27e6-125">Para fazer com que a transição entre a exibição de tabela e a exibição de detalhes seja suave e natural, eu o fiz de forma semelhante à interação física de uma abertura de caixa na vida real.</span><span class="sxs-lookup"><span data-stu-id="c27e6-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="c27e6-126">![Esboço de design](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="c27e6-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="c27e6-127">*Esboços de design*</span><span class="sxs-lookup"><span data-stu-id="c27e6-127">*Design sketches*</span></span>

<span data-ttu-id="c27e6-128">No modo de exibição de detalhes, eu queria visualizar as informações de cada elemento com o texto renderizado linda em espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="c27e6-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="c27e6-129">O modelo de rede 3D animada é exibido na área central e pode ser exibido a partir de diferentes ângulos.</span><span class="sxs-lookup"><span data-stu-id="c27e6-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interação](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="c27e6-131">![Protótipos](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="c27e6-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="c27e6-132">*Protótipos de interação*</span><span class="sxs-lookup"><span data-stu-id="c27e6-132">*Interaction prototypes*</span></span>

<span data-ttu-id="c27e6-133">O usuário pode alterar o tipo de superfície por ar tocando nos botões na parte inferior da tabela-eles podem alternar entre plano, cilindro, esfera e dispersão.</span><span class="sxs-lookup"><span data-stu-id="c27e6-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="c27e6-134">Controles e padrões comuns usados neste aplicativo</span><span class="sxs-lookup"><span data-stu-id="c27e6-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="c27e6-135">Objeto interagir (botão)</span><span class="sxs-lookup"><span data-stu-id="c27e6-135">Interactable object (button)</span></span>

<span data-ttu-id="c27e6-136">O [objeto de interação](interactable-object.md) é um objeto que pode responder às entradas básicas do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c27e6-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="c27e6-137">Ele é fornecido como um pré-fabricado/script que você pode aplicar facilmente a qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="c27e6-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="c27e6-138">Por exemplo, você pode fazer com que uma xícara de café em sua cena interaja e responda a entradas como olhar, toque de ar, navegação e gestos de manipulação.</span><span class="sxs-lookup"><span data-stu-id="c27e6-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="c27e6-139">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="c27e6-139">Learn more</span></span>](interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="c27e6-141">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="c27e6-141">Object collection</span></span>

<span data-ttu-id="c27e6-142">A [coleção de objetos](object-collection.md) é um objeto que ajuda você a dispor vários objetos em várias formas.</span><span class="sxs-lookup"><span data-stu-id="c27e6-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="c27e6-143">Ele dá suporte a plano, cilindro, esfera e dispersão.</span><span class="sxs-lookup"><span data-stu-id="c27e6-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="c27e6-144">Você pode configurar propriedades adicionais, como RADIUS, número de linhas e espaçamento.</span><span class="sxs-lookup"><span data-stu-id="c27e6-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="c27e6-145">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="c27e6-145">Learn more</span></span>](object-collection.md)

![Coleção de objetos](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="c27e6-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="c27e6-147">Fitbox</span></span>

<span data-ttu-id="c27e6-148">Por padrão, os hologramas serão colocados no local onde o usuário está nuvens no momento em que o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="c27e6-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="c27e6-149">Às vezes, isso leva a um resultado indesejado, como os hologramas sendo colocados atrás de uma parede ou no meio de uma tabela.</span><span class="sxs-lookup"><span data-stu-id="c27e6-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="c27e6-150">Um fitbox permite que um usuário use olhar para determinar o local onde o holograma será colocado.</span><span class="sxs-lookup"><span data-stu-id="c27e6-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="c27e6-151">Ele é feito com uma simples textura de imagem PNG que pode ser facilmente personalizada com suas próprias imagens ou objetos 3D.</span><span class="sxs-lookup"><span data-stu-id="c27e6-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="c27e6-153">Detalhes técnicos</span><span class="sxs-lookup"><span data-stu-id="c27e6-153">Technical details</span></span>

<span data-ttu-id="c27e6-154">Você pode encontrar scripts e pré-fabricados para a tabela periódica do aplicativo de elementos no [GitHub de laboratórios de design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="c27e6-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="c27e6-155">Exemplos de aplicativos</span><span class="sxs-lookup"><span data-stu-id="c27e6-155">Application examples</span></span>

<span data-ttu-id="c27e6-156">Aqui estão algumas ideias para o que você poderia criar aproveitando os componentes neste projeto.</span><span class="sxs-lookup"><span data-stu-id="c27e6-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="c27e6-157">Aplicativo de visualização de dados de ações</span><span class="sxs-lookup"><span data-stu-id="c27e6-157">Stock data visualization app</span></span>

<span data-ttu-id="c27e6-158">Usando os mesmos controles e modelos de interação que a tabela periódica dos elementos de exemplo, você poderia criar um aplicativo que visualize os dados do mercado de ações.</span><span class="sxs-lookup"><span data-stu-id="c27e6-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="c27e6-159">Este exemplo usa o controle de coleção de objetos para dispor dados de ações em uma forma esférica.</span><span class="sxs-lookup"><span data-stu-id="c27e6-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="c27e6-160">Você pode imaginar uma exibição de detalhes em que informações adicionais sobre cada ação podem ser exibidas de forma interessante.</span><span class="sxs-lookup"><span data-stu-id="c27e6-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![Exemplo de aplicativo: Finanças (1 de 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Exemplo de aplicativo: Finanças (2 de 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="c27e6-163">![Exemplo de aplicativo: Finanças (3 de 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="c27e6-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="c27e6-164">*Um exemplo de como a coleção de objetos usada na tabela periódica do aplicativo de exemplo de elementos pode ser usada em um aplicativo de finanças*</span><span class="sxs-lookup"><span data-stu-id="c27e6-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="c27e6-165">Aplicativo esportivo</span><span class="sxs-lookup"><span data-stu-id="c27e6-165">Sports app</span></span>

<span data-ttu-id="c27e6-166">Este é um exemplo de visualização de dados de esportes usando a coleta de objetos e outros componentes da tabela periódica do aplicativo de exemplo de elementos.</span><span class="sxs-lookup"><span data-stu-id="c27e6-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![Exemplo de aplicativo: Esportes (1 de 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Exemplo de aplicativo: Esportes (2 de 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="c27e6-169">![Exemplo de aplicativo: Esportes (3 de 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="c27e6-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="c27e6-170">*Um exemplo de como a coleção de objetos usada na tabela periódica dos elementos de exemplo appcould ser usada em um aplicativo esportivo*</span><span class="sxs-lookup"><span data-stu-id="c27e6-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="c27e6-171">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="c27e6-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="c27e6-172"><b>Parque Yoon Dong</b></span><span class="sxs-lookup"><span data-stu-id="c27e6-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="c27e6-173">Designer de UX@Microsoft</span><span class="sxs-lookup"><span data-stu-id="c27e6-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="c27e6-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c27e6-174">See also</span></span>

* [<span data-ttu-id="c27e6-175">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="c27e6-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="c27e6-176">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="c27e6-176">Object collection</span></span>](object-collection.md)
