---
title: Estudo de caso-criando HoloSketch, um layout espacial e um aplicativo de esboço de UX para o HoloLens
description: HoloSketch é um layout espacial do dispositivo e uma ferramenta de esboço de UX para o HoloLens para ajudar a criar experiências de Holographic.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, realidade mista do Windows, esboço, aplicativo
ms.openlocfilehash: d6d22aae7709bcc1a33b142a100d1a0f9645d3cc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436949"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="7e420-104">Estudo de caso-criando HoloSketch, um layout espacial e um aplicativo de esboço de UX para o HoloLens</span><span class="sxs-lookup"><span data-stu-id="7e420-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="7e420-105">HoloSketch é um layout espacial do dispositivo e uma ferramenta de esboço de UX para o HoloLens para ajudar a criar experiências de Holographic.</span><span class="sxs-lookup"><span data-stu-id="7e420-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="7e420-106">O HoloSketch funciona com um teclado e mouse Bluetooth emparelhados, bem como comandos de voz e de gesto.</span><span class="sxs-lookup"><span data-stu-id="7e420-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="7e420-107">A finalidade do HoloSketch é fornecer uma ferramenta de layout de UX simples para visualização e iteração rápidas.</span><span class="sxs-lookup"><span data-stu-id="7e420-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="7e420-108">![HoloSketch: um layout espacial e um aplicativo de esboço de UX para o HoloLens.](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="7e420-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="7e420-109">*HoloSketch: layout espacial e aplicativo de esboço de UX para o HoloLens*</span><span class="sxs-lookup"><span data-stu-id="7e420-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="7e420-110">![uma ferramenta de layout de UX simples para visualização e iteração rápidas.](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="7e420-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="7e420-111">*Uma ferramenta de layout de UX simples para visualização e iteração rápidas*</span><span class="sxs-lookup"><span data-stu-id="7e420-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="7e420-112">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e420-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="7e420-113">Primitivos para estudos rápidos e criação de protótipos de escala</span><span class="sxs-lookup"><span data-stu-id="7e420-113">Primitives for quick studies and scale-prototyping</span></span>

![Usando formas primitivas](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="7e420-115">Use formas primitivas para estudos rápidos de massa e criação de protótipos de escala.</span><span class="sxs-lookup"><span data-stu-id="7e420-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="7e420-116">Importar objetos por meio do OneDrive</span><span class="sxs-lookup"><span data-stu-id="7e420-116">Import objects through OneDrive</span></span>

![importando objetos](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="7e420-118">Importe imagens PNG/JPG ou objetos FBX 3D (requer empacotamento no Unity) no espaço da realidade misturada por meio do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="7e420-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="7e420-119">Manipular objetos</span><span class="sxs-lookup"><span data-stu-id="7e420-119">Manipulate objects</span></span>

![manipulando objetos](images/manipulate-objects-640px.jpg)

<span data-ttu-id="7e420-121">Manipule objetos (move/gira/dimensionamento) com uma interface de objeto 3D familiar.</span><span class="sxs-lookup"><span data-stu-id="7e420-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="7e420-122">Bluetooth, mouse/teclado, gestos e comandos de voz</span><span class="sxs-lookup"><span data-stu-id="7e420-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![dá suporte a Bluetooth](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="7e420-124">O HoloSketch dá suporte a mouses Bluetooth/teclado, gestos e comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="7e420-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="7e420-125">Histórico</span><span class="sxs-lookup"><span data-stu-id="7e420-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="7e420-126">Importância de experimentar seu design no dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e420-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="7e420-127">Quando você cria algo para o HoloLens, é importante experimentar o design no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7e420-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="7e420-128">Um dos maiores desafios no design de aplicativos de realidade misturada é que é difícil obter o sentido de escala, posição e profundidade, especialmente por meio de esboços 2D tradicionais.</span><span class="sxs-lookup"><span data-stu-id="7e420-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="7e420-129">Custo da comunicação baseada em 2D</span><span class="sxs-lookup"><span data-stu-id="7e420-129">Cost of 2D based communication</span></span>

<span data-ttu-id="7e420-130">Para comunicar efetivamente fluxos e cenários de UX a outros, um designer pode acabar gastando muito tempo criando ativos usando ferramentas 2D tradicionais, como o Illustrator, o Photoshop e o PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="7e420-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="7e420-131">Esses designs 2D geralmente exigem um esforço adicional para convertê-los em 3D.</span><span class="sxs-lookup"><span data-stu-id="7e420-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="7e420-132">Algumas ideias são perdidas nessa tradução de 2D para 3D.</span><span class="sxs-lookup"><span data-stu-id="7e420-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="7e420-133">Processo de implantação complexo</span><span class="sxs-lookup"><span data-stu-id="7e420-133">Complex deployment process</span></span>

<span data-ttu-id="7e420-134">Como a realidade misturada é uma nova tela para nós, ela envolve muita iteração de design e avaliação e erro por sua natureza.</span><span class="sxs-lookup"><span data-stu-id="7e420-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="7e420-135">Para o designer que não estão familiarizados com ferramentas como Unity e Visual Studio, não é fácil colocar algo em conjunto no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7e420-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="7e420-136">Normalmente, você precisa passar pelo processo abaixo para ver sua arte 2D/3D no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7e420-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="7e420-137">Essa era uma grande barreira para os designers Iterando rapidamente em ideias e cenários.</span><span class="sxs-lookup"><span data-stu-id="7e420-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="7e420-138">![processo de implantação complexo](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7e420-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="7e420-139">*Processo de implantação*</span><span class="sxs-lookup"><span data-stu-id="7e420-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="7e420-140">Processo simplificado com o HoloSketch</span><span class="sxs-lookup"><span data-stu-id="7e420-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="7e420-141">Com o HoloSketch, queríamos simplificar esse processo sem envolver as ferramentas de desenvolvimento e o emparelhamento do portal do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7e420-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="7e420-142">Usando o OneDrive, os usuários podem facilmente colocar ativos 2D/3D no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7e420-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="7e420-143">![processo simplificado com o HoloSketch](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7e420-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="7e420-144">*Processo simplificado com o HoloSketch*</span><span class="sxs-lookup"><span data-stu-id="7e420-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="7e420-145">Incentivando a reflexão e as soluções de design tridimensionais</span><span class="sxs-lookup"><span data-stu-id="7e420-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="7e420-146">Achamos que essa ferramenta daria aos designers uma oportunidade de explorar soluções em um espaço verdadeiramente tridimensional e que não estaria presa em 2D.</span><span class="sxs-lookup"><span data-stu-id="7e420-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="7e420-147">Eles não precisam pensar em criar um plano de fundo 3D para sua interface do usuário, pois o plano de fundo é o mundo real no caso do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7e420-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of HoloLens.</span></span> <span data-ttu-id="7e420-148">O HoloSketch abre uma maneira de os designers explorarem facilmente o design 3D no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7e420-148">HoloSketch opens up a way for designers to easily explore 3D design on HoloLens.</span></span>

## <a name="get-started"></a><span data-ttu-id="7e420-149">Introdução</span><span class="sxs-lookup"><span data-stu-id="7e420-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="7e420-150">Como importar imagens 2D (JPG/PNG) para o HoloSketch</span><span class="sxs-lookup"><span data-stu-id="7e420-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="7e420-151">Carregue imagens JPG/PNG na pasta do OneDrive ' Documents/HoloSketch '.</span><span class="sxs-lookup"><span data-stu-id="7e420-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="7e420-152">No menu do OneDrive no HoloSketch, você poderá selecionar e posicionar a imagem no ambiente.</span><span class="sxs-lookup"><span data-stu-id="7e420-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="7e420-153">![importação de imagens 2D](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7e420-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="7e420-154">*Importando imagens e objetos 3D por meio do OneDrive*</span><span class="sxs-lookup"><span data-stu-id="7e420-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="7e420-155">Como importar objetos 3D para o HoloSketch</span><span class="sxs-lookup"><span data-stu-id="7e420-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="7e420-156">Antes de carregar em sua pasta do OneDrive, siga as etapas abaixo para empacotar seus objetos 3D em um pacote de ativos do Unity.</span><span class="sxs-lookup"><span data-stu-id="7e420-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="7e420-157">Usando esse processo, você pode importar seus Arquivos FBX/OBJ de software 3D, como Maya, cinema 4D e Microsoft Paint 3D.</span><span class="sxs-lookup"><span data-stu-id="7e420-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="7e420-158">Atualmente, a criação do pacote de ativos tem suporte com o Unity versão 5.4.5 F1.</span><span class="sxs-lookup"><span data-stu-id="7e420-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="7e420-159">Baixe e abra o projeto do Unity [' AssetBunlder_Unity '](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span><span class="sxs-lookup"><span data-stu-id="7e420-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="7e420-160">Esse projeto de Unity inclui o script para a geração de ativos do pacote.</span><span class="sxs-lookup"><span data-stu-id="7e420-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="7e420-161">Crie um novo gameobject.</span><span class="sxs-lookup"><span data-stu-id="7e420-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="7e420-162">Nomeie o gameobject com base no conteúdo.</span><span class="sxs-lookup"><span data-stu-id="7e420-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="7e420-163">No painel Inspetor, clique em "Adicionar componente" e adicione "cocolisorr".</span><span class="sxs-lookup"><span data-stu-id="7e420-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![No painel Inspetor, clique em "Adicionar componente" e adicionar "Colisor de caixa"](images/holosketch-10a-assetbundles-1000px.png)
   
   ![No painel Inspetor, clique em "Adicionar componente" e adicionar "Colisor de caixa" #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="7e420-166">Importe o arquivo 3D FBX arrastando-o para o painel projeto.</span><span class="sxs-lookup"><span data-stu-id="7e420-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="7e420-167">Arraste o objeto para o painel hierarquia **em seu novo gameobject**.</span><span class="sxs-lookup"><span data-stu-id="7e420-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![Arraste o objeto para o painel hierarquia em seu novo gameobject](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="7e420-169">Ajuste a dimensão do colisor se ele não corresponder ao objeto.</span><span class="sxs-lookup"><span data-stu-id="7e420-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="7e420-170">Gire o objeto para a face do **eixo Z**.</span><span class="sxs-lookup"><span data-stu-id="7e420-170">Rotate the object to face **Z-axis**.</span></span>

   ![Ajuste a dimensão do colisor se ele não corresponder ao objeto.](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="7e420-172">Arraste o objeto do painel hierarquia para o painel projeto para **torná-lo pré-fabricado**.</span><span class="sxs-lookup"><span data-stu-id="7e420-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="7e420-173">Na parte inferior do painel Inspetor, clique no menu suspenso, crie e atribua um novo nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="7e420-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="7e420-174">O exemplo abaixo mostra como adicionar e atribuir ' brownchair ' para o nome do AssetBundle.</span><span class="sxs-lookup"><span data-stu-id="7e420-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![Na parte inferior do painel Inspetor, clique na lista suspensa e atribua um novo nome exclusivo.](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="7e420-176">Prepare uma imagem em miniatura para o objeto de modelo.</span><span class="sxs-lookup"><span data-stu-id="7e420-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="7e420-177">![arraste uma imagem para o painel projeto e atribua o nome usado para o objeto.](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7e420-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="7e420-178">Crie uma pasta chamada ' Assetbundles ' na pasta ' Asset ' do projeto de Unity.</span><span class="sxs-lookup"><span data-stu-id="7e420-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="7e420-179">No menu ativos, selecione ' Compilar AssetBundles ' para gerar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="7e420-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="7e420-180">![no menu ativos, selecione ' Compilar AssetBundles ' para gerar o arquivo.](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="7e420-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="7e420-181">**Carregue o arquivo gerado para a pasta/Files/Documents/HoloSketch no OneDrive.**</span><span class="sxs-lookup"><span data-stu-id="7e420-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="7e420-182">Carregue somente o arquivo asset_unique_name.</span><span class="sxs-lookup"><span data-stu-id="7e420-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="7e420-183">Você não precisa carregar arquivos de manifesto ou arquivo AssetBundles.</span><span class="sxs-lookup"><span data-stu-id="7e420-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="7e420-184">![adicionar arquivos a arquivos/documentos/HoloSketch/pasta](images/holosketch-onedriveupload-1000px.png)
![você verá o objeto 3D adicionado no menu do OneDrive do HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7e420-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="7e420-185">Como manipular os objetos</span><span class="sxs-lookup"><span data-stu-id="7e420-185">How to manipulate the objects</span></span>

<span data-ttu-id="7e420-186">O HoloSketch dá suporte à interface tradicional que é amplamente usada em software 3D.</span><span class="sxs-lookup"><span data-stu-id="7e420-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="7e420-187">Você pode usar mover, girar, dimensionar os objetos com gestos e um mouse.</span><span class="sxs-lookup"><span data-stu-id="7e420-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="7e420-188">Você pode alternar rapidamente entre modos diferentes com voz ou teclado.</span><span class="sxs-lookup"><span data-stu-id="7e420-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="7e420-189">Modos de manipulação de objeto</span><span class="sxs-lookup"><span data-stu-id="7e420-189">Object manipulation modes</span></span>

<span data-ttu-id="7e420-190">![como manipular os objetos](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7e420-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="7e420-191">*Como manipular os objetos*</span><span class="sxs-lookup"><span data-stu-id="7e420-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="7e420-192">Menus contextuais e da correia de ferramenta</span><span class="sxs-lookup"><span data-stu-id="7e420-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="7e420-193">**Usando o menu contextual**</span><span class="sxs-lookup"><span data-stu-id="7e420-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="7e420-194">Toque de ar duplo para abrir o menu contextual.</span><span class="sxs-lookup"><span data-stu-id="7e420-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="7e420-195">Itens de menu:</span><span class="sxs-lookup"><span data-stu-id="7e420-195">Menu items:</span></span>
* <span data-ttu-id="7e420-196">**Superfície de layout:** Esse é um sistema de grade 3D no qual você pode fazer o layout de vários objetos e gerenciá-los como um grupo.</span><span class="sxs-lookup"><span data-stu-id="7e420-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="7e420-197">Air de toque duplo na superfície de layout para adicionar objetos a ele.</span><span class="sxs-lookup"><span data-stu-id="7e420-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="7e420-198">**Primitivos:** Use cubos, por meio de cilindros e cones para estudos em massa.</span><span class="sxs-lookup"><span data-stu-id="7e420-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="7e420-199">**Onedrive:** Abra o menu do OneDrive para importar objetos.</span><span class="sxs-lookup"><span data-stu-id="7e420-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="7e420-200">**Ajuda:** Exibe a tela de ajuda.</span><span class="sxs-lookup"><span data-stu-id="7e420-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="7e420-201">![](images/holosketch-image-07.png) de menu contextual</span><span class="sxs-lookup"><span data-stu-id="7e420-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="7e420-202">*Menu contextual*</span><span class="sxs-lookup"><span data-stu-id="7e420-202">*Contextual menu*</span></span>

<span data-ttu-id="7e420-203">**Usando o menu da correia de ferramentas**</span><span class="sxs-lookup"><span data-stu-id="7e420-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="7e420-204">Mover, girar, dimensionar, salvar e carregar a cena está disponível no menu da correia de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="7e420-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="7e420-205">Usando teclado, gestos e comandos de voz</span><span class="sxs-lookup"><span data-stu-id="7e420-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="7e420-206">![teclado, gestos e comandos de voz](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7e420-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="7e420-207">*Teclado, gestos e comandos de voz*</span><span class="sxs-lookup"><span data-stu-id="7e420-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="7e420-208">Baixar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="7e420-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="7e420-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Baixe e instale o aplicativo HoloSketch gratuitamente do Microsoft Store</a>
</span><span class="sxs-lookup"><span data-stu-id="7e420-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="7e420-210">Problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="7e420-210">Known issues</span></span>
* <span data-ttu-id="7e420-211">Atualmente, há suporte para a criação do pacote de ativos com o **Unity versão 5.4.5 F1.**</span><span class="sxs-lookup"><span data-stu-id="7e420-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="7e420-212">Dependendo da quantidade de dados em seu OneDrive, o aplicativo pode aparecer como se tiver parado durante o carregamento do conteúdo do OneDrive</span><span class="sxs-lookup"><span data-stu-id="7e420-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="7e420-213">Atualmente, o recurso salvar e carregar só dá suporte a objetos primitivos</span><span class="sxs-lookup"><span data-stu-id="7e420-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="7e420-214">Os menus de texto, som, vídeo e foto estão desabilitados no menu contextual</span><span class="sxs-lookup"><span data-stu-id="7e420-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="7e420-215">O botão reproduzir no menu da correia de ferramenta limpa o utensílios de manipulação</span><span class="sxs-lookup"><span data-stu-id="7e420-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="7e420-216">Compartilhando seus esboços</span><span class="sxs-lookup"><span data-stu-id="7e420-216">Sharing your sketches</span></span>

<span data-ttu-id="7e420-217">Você pode usar o recurso de gravação de vídeo no HoloLens dizendo ' Ei Cortana, iniciar/parar a gravação '.</span><span class="sxs-lookup"><span data-stu-id="7e420-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="7e420-218">Pressione a tecla volume para cima/para baixo para tirar uma foto do seu esboço.</span><span class="sxs-lookup"><span data-stu-id="7e420-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="7e420-219">Sobre os autores</span><span class="sxs-lookup"><span data-stu-id="7e420-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="7e420-220"><b>Parque Yoon Dong</b></span><span class="sxs-lookup"><span data-stu-id="7e420-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="7e420-221">@Microsoft do designer de UX</span><span class="sxs-lookup"><span data-stu-id="7e420-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="7e420-222"><b>Patrick Sebring</b></span><span class="sxs-lookup"><span data-stu-id="7e420-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="7e420-223">@Microsoft do desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="7e420-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
