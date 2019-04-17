---
title: Tabela periódica dos elementos
description: Tabela periódica dos elementos é um aplicativo de exemplo de código-fonte aberto do laboratórios da Microsoft misto realidade Design onde você pode aprender como criar uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma coleção de objetos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, o aplicativo de exemplo, controles
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590817"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="cf1f2-104">Tabela periódica dos elementos</span><span class="sxs-lookup"><span data-stu-id="cf1f2-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="cf1f2-105">Este artigo descreve um exemplo de análise exploratório que criamos na [laboratórios de Design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity), um lugar onde podemos compartilhar nossos aprendizados sobre e sugestões para desenvolvimento de aplicativos de realidade de misto.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="cf1f2-106">Nossos artigos relacionados ao design e código evolui à medida que fizermos novas descobertas.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="cf1f2-107">[Tabela periódica dos elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) é um aplicativo de exemplo de código-fonte aberto de laboratórios de Design de realidade misturada da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="cf1f2-108">Com este projeto, você pode aprender como dispor de uma matriz de objetos no espaço 3D com vários tipos de superfície usando um  **[coleção de objetos](object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="cf1f2-109">Saiba também como criar objetos interagível que respondem a entradas padrão do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="cf1f2-110">Você pode usar os componentes deste projeto para criar seus próprios misto experiência de aplicativo de realidade.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabela Períoda do aplicativo elementos](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="cf1f2-112">Sobre o aplicativo</span><span class="sxs-lookup"><span data-stu-id="cf1f2-112">About the app</span></span>

<span data-ttu-id="cf1f2-113">Tabela periódica dos elementos visualiza os elementos químicos e cada uma de suas propriedades em um espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="cf1f2-114">Ele incorpora as interações básicas do HoloLens, como toque olhar e ar.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="cf1f2-115">Os usuários podem aprender sobre os elementos com modelos 3D animados.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="cf1f2-116">Eles possam entender visualmente shell electron de um elemento e seu núcleo - que é composto de protons e neutrons.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="cf1f2-117">Histórico</span><span class="sxs-lookup"><span data-stu-id="cf1f2-117">Background</span></span>

<span data-ttu-id="cf1f2-118">Depois que experimentei primeiro HoloLens, um aplicativo de tabela periódica era uma ideia que eu sabia que queria fazer experiências com na realidade mista.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="cf1f2-119">Como cada elemento tem muitos pontos de dados que são exibidos com texto, pensei que seria ótimo no assunto para explorar tipográfica composição em um espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="cf1f2-120">Ser capaz de visualizar o modelo do elemento electron era outra parte interessante deste projeto.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="cf1f2-121">Criar</span><span class="sxs-lookup"><span data-stu-id="cf1f2-121">Design</span></span>

<span data-ttu-id="cf1f2-122">Modo de exibição padrão da tabela periódica, imaginei caixas tridimensionais que contém o modelo do bombardeador de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="cf1f2-123">A superfície de cada caixa seria translúcida para que o usuário pode ter uma noção aproximada do volume do elemento.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="cf1f2-124">Com toque olhar e ar, o usuário pode abrir uma exibição detalhada de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="cf1f2-125">Para fazer a transição entre a exibição de tabela e exibição de detalhes suave e natural, eu o tornei semelhante à interação física de uma caixa de abertura na vida real.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="cf1f2-126">![Esboço de design](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="cf1f2-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="cf1f2-127">*Esboços de design*</span><span class="sxs-lookup"><span data-stu-id="cf1f2-127">*Design sketches*</span></span>

<span data-ttu-id="cf1f2-128">No modo de exibição de detalhes, eu queria visualizar as informações de cada elemento com o texto lindamente renderizado no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="cf1f2-129">O modelo de elétrons 3D animados é exibido na área central e pode ser exibido de ângulos diferentes.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interação](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="cf1f2-131">![Protótipos](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="cf1f2-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="cf1f2-132">*Protótipos de interação*</span><span class="sxs-lookup"><span data-stu-id="cf1f2-132">*Interaction prototypes*</span></span>

<span data-ttu-id="cf1f2-133">O usuário pode alterar o tipo de superfície por via aérea tocando os botões na parte inferior da tabela - eles podem alternar entre o plano, cilindro, esfera e dispersão.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="cf1f2-134">Padrões usados neste aplicativo e controles comuns</span><span class="sxs-lookup"><span data-stu-id="cf1f2-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="cf1f2-135">Objeto interagível (botão)</span><span class="sxs-lookup"><span data-stu-id="cf1f2-135">Interactable object (button)</span></span>

<span data-ttu-id="cf1f2-136">[Objeto interagível](interactable-object.md) é um objeto que pode responder a entradas básicas do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="cf1f2-137">Ele é fornecido como um pré-fabricado/script que você pode aplicar facilmente a qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="cf1f2-138">Por exemplo, você pode fazer uma xícara de café na sua cena interagível e responder a entradas como olhar, indicador e polegar, navegação e manipulação de gestos.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="cf1f2-139">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="cf1f2-139">Learn more</span></span>](interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="cf1f2-141">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="cf1f2-141">Object collection</span></span>

<span data-ttu-id="cf1f2-142">[Coleção de objetos](object-collection.md) é um objeto que ajuda você a dispor vários objetos em diversas formas.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="cf1f2-143">Ele dá suporte ao plano, cilindro, esfera e dispersão.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="cf1f2-144">Você pode configurar propriedades adicionais, como o raio, o número de linhas e espaçamento.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="cf1f2-145">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="cf1f2-145">Learn more</span></span>](object-collection.md)

![Coleção de objetos](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="cf1f2-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="cf1f2-147">Fitbox</span></span>

<span data-ttu-id="cf1f2-148">Por padrão, hologramas serão colocadas no local em que o usuário é Observação no momento, o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="cf1f2-149">Às vezes, isso leva a resultados indesejados como hologramas que está sendo colocado atrás de uma parede ou no meio de uma tabela.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="cf1f2-150">Um fitbox permite que um usuário use olhar para determinar o local onde o holograma será colocado.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="cf1f2-151">Ela é feita com uma textura de imagem PNG simple que pode ser facilmente personalizada com suas próprias imagens ou objetos 3D.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="cf1f2-153">Detalhes técnicos</span><span class="sxs-lookup"><span data-stu-id="cf1f2-153">Technical details</span></span>

<span data-ttu-id="cf1f2-154">Você pode encontrar scripts e pré-fabricados para a tabela de atividades periódicas do aplicativo de elementos na [GitHub de laboratórios de Design de realidade mista](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="cf1f2-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="cf1f2-155">Exemplos de aplicativos</span><span class="sxs-lookup"><span data-stu-id="cf1f2-155">Application examples</span></span>

<span data-ttu-id="cf1f2-156">Aqui estão algumas ideias para o que você pode criar, aproveitando os componentes neste projeto.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="cf1f2-157">Aplicativo de visualização de dados de estoque</span><span class="sxs-lookup"><span data-stu-id="cf1f2-157">Stock data visualization app</span></span>

<span data-ttu-id="cf1f2-158">Usando os mesmos controles e o modelo de interação como a tabela periódica da amostra de elementos, você pode criar um aplicativo que visualiza dados de mercado de ações.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="cf1f2-159">Este exemplo usa o controle de coleta de objeto para dispor os dados de estoque em uma forma esférica.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="cf1f2-160">Você pode imaginar um modo de exibição de detalhes em que informações adicionais sobre cada ação poderiam ser exibidas em uma forma interessante.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![Exemplo de aplicativo: Finanças (1 de 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Exemplo de aplicativo: Finanças (2 de 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="cf1f2-163">![Exemplo de aplicativo: Finanças (3 de 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="cf1f2-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="cf1f2-164">*Um exemplo de como a coleção de objetos usada na tabela periódica o elementos do aplicativo de exemplo poderia ser usada em um aplicativo de finanças*</span><span class="sxs-lookup"><span data-stu-id="cf1f2-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="cf1f2-165">Aplicativo de esportes</span><span class="sxs-lookup"><span data-stu-id="cf1f2-165">Sports app</span></span>

<span data-ttu-id="cf1f2-166">Este é um exemplo de visualização de dados de esportes, usando a coleção de objetos e outros componentes da tabela de atividades periódicas do aplicativo de exemplo de elementos.</span><span class="sxs-lookup"><span data-stu-id="cf1f2-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![Exemplo de aplicativo: Esportes (1 de 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Exemplo de aplicativo: Esportes (2 de 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="cf1f2-169">![Exemplo de aplicativo: Esportes (3 de 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="cf1f2-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="cf1f2-170">*Um exemplo de como a coleção de objetos usados na tabela de atividades periódicas de appcould de exemplo de elementos a ser usado em um aplicativo de esportes*</span><span class="sxs-lookup"><span data-stu-id="cf1f2-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="cf1f2-171">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="cf1f2-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="cf1f2-172"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="cf1f2-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="cf1f2-173">Designer de UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="cf1f2-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="cf1f2-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf1f2-174">See also</span></span>

* [<span data-ttu-id="cf1f2-175">Objeto interagível</span><span class="sxs-lookup"><span data-stu-id="cf1f2-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="cf1f2-176">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="cf1f2-176">Object collection</span></span>](object-collection.md)
