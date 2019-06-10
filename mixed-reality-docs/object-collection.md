---
title: Coleção de objetos
description: Coleção de objetos é um controle de layout que ajuda você a dispor de uma matriz de objetos em uma forma tridimensional predefinido.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, controles, design
ms.openlocfilehash: 7c3bbd82ec909b5a2e3c81f122366be564934f4d
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813878"
---
# <a name="object-collection"></a><span data-ttu-id="22875-104">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="22875-104">Object collection</span></span>

<span data-ttu-id="22875-105">Coleção de objetos é um controle de layout que ajuda você a dispor de uma matriz de objetos em uma forma tridimensional predefinido.</span><span class="sxs-lookup"><span data-stu-id="22875-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="22875-106">Ele dá suporte a vários estilos de superfície - **plano, cilindro, esfera** e **radial**.</span><span class="sxs-lookup"><span data-stu-id="22875-106">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="22875-107">Você pode ajustar o radius e o tamanho dos objetos e o espaço entre eles.</span><span class="sxs-lookup"><span data-stu-id="22875-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="22875-108">Coleção de objetos dá suporte a qualquer objeto do Unity - 2D e 3D.</span><span class="sxs-lookup"><span data-stu-id="22875-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="22875-109">No  **[Kit de ferramentas de realidade misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** , criamos um script do Unity e exemplos que ajudarão você a criam uma coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="22875-109">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

<span data-ttu-id="22875-110">![Coleção de objetos usada na tabela Atividades Periódicas do aplicativo elementos](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="22875-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="22875-111">*Exemplos de como usar a coleção de objetos*</span><span class="sxs-lookup"><span data-stu-id="22875-111">*Examples of using object collection*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="22875-112">Exemplos de coleção do objeto</span><span class="sxs-lookup"><span data-stu-id="22875-112">Object collection examples</span></span>

<span data-ttu-id="22875-113">[Tabela periódica dos elementos](periodic-table-of-the-elements.md) é um aplicativo de exemplo que demonstra como funciona a coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="22875-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="22875-114">Ele usa a coleção de objetos para dispor caixas elemento químico 3D em formas diferentes.</span><span class="sxs-lookup"><span data-stu-id="22875-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="22875-115">![Exemplos de coleção do objeto mostrados na tabela Atividades Periódicas do aplicativo elementos](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="22875-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="22875-116">*Exemplos de coleção do objeto mostrados na tabela Atividades Periódicas do aplicativo de exemplo de elementos*</span><span class="sxs-lookup"><span data-stu-id="22875-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="22875-117">Objetos 3D</span><span class="sxs-lookup"><span data-stu-id="22875-117">3D objects</span></span>

<span data-ttu-id="22875-118">Você pode usar a coleção de objetos para dispor objetos 3D importados.</span><span class="sxs-lookup"><span data-stu-id="22875-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="22875-119">O exemplo a seguir mostra um plano e um layout de cilindro de alguns objetos 3D cadeira.</span><span class="sxs-lookup"><span data-stu-id="22875-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="22875-120">![Exemplos de plano e cilíndricas layouts de objetos 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="22875-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="22875-121">*Exemplos de plano e cilíndricas layouts de objetos 3D*</span><span class="sxs-lookup"><span data-stu-id="22875-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="22875-122">Objetos 2D</span><span class="sxs-lookup"><span data-stu-id="22875-122">2D objects</span></span>

<span data-ttu-id="22875-123">Você também pode usar imagens 2D com a coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="22875-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="22875-124">Os exemplos a seguir demonstram como 2D imagens podem ser exibidos em uma grade.</span><span class="sxs-lookup"><span data-stu-id="22875-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Um exemplo de imagens 2D com a coleção de objetos](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="22875-126">![Um exemplo de imagens 2D com a coleção de objetos](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="22875-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="22875-127">*Exemplos de como usar a coleção de objetos com imagens 2D*</span><span class="sxs-lookup"><span data-stu-id="22875-127">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="22875-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22875-128">See also</span></span>
* [<span data-ttu-id="22875-129">Pré-fabricados para a coleção de objetos no Kit de ferramentas realidade mista no GitHub e scripts</span><span class="sxs-lookup"><span data-stu-id="22875-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="22875-130">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="22875-130">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="22875-131">Caixa delimitadora</span><span class="sxs-lookup"><span data-stu-id="22875-131">Bounding Box</span></span>](app-bar-and-bounding-box.md)
