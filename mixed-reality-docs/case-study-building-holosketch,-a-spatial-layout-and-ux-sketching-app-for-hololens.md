---
title: Estudo de caso - HoloSketch de construção, um layout espacial e a experiência do usuário fazer um rascunho de aplicativo para o HoloLens
description: HoloSketch é um layout de espacial no dispositivo e a experiência do usuário fazer um rascunho de ferramenta para HoloLens ajudar a criar experiências holográfica.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, fazer um rascunho, aplicativo
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589599"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="14298-104">Estudo de caso - HoloSketch de construção, um layout espacial e a experiência do usuário fazer um rascunho de aplicativo para o HoloLens</span><span class="sxs-lookup"><span data-stu-id="14298-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="14298-105">HoloSketch é um layout de espacial no dispositivo e a experiência do usuário fazer um rascunho de ferramenta para HoloLens ajudar a criar experiências holográfica.</span><span class="sxs-lookup"><span data-stu-id="14298-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="14298-106">HoloSketch funciona com um comandos de teclado e mouse, bem como gestos e voz de Bluetooth emparelhados.</span><span class="sxs-lookup"><span data-stu-id="14298-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="14298-107">A finalidade de HoloSketch é fornecer uma ferramenta de layout de experiência do usuário simple para iteração e visualização rápida.</span><span class="sxs-lookup"><span data-stu-id="14298-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="14298-108">![HoloSketch: Um layout espacial e a experiência do usuário fazer um rascunho de aplicativo para o HoloLens.](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="14298-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="14298-109">*HoloSketch: layout espacial e a experiência do usuário fazer um rascunho de aplicativo para o HoloLens*</span><span class="sxs-lookup"><span data-stu-id="14298-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="14298-110">![Uma ferramenta de layout de experiência do usuário simple para visualização rápida e de iteração.](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="14298-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="14298-111">*Uma ferramenta simples de layout UX para visualização rápida e de iteração*</span><span class="sxs-lookup"><span data-stu-id="14298-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="14298-112">Recursos</span><span class="sxs-lookup"><span data-stu-id="14298-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="14298-113">Primitivos para estudos rápido e criação de protótipos de escala</span><span class="sxs-lookup"><span data-stu-id="14298-113">Primitives for quick studies and scale-prototyping</span></span>

![Usando formas primitivas](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="14298-115">Use formas primitivas para estudos massing rápidos e criação de protótipos de escala.</span><span class="sxs-lookup"><span data-stu-id="14298-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="14298-116">Importar objetos por meio do OneDrive</span><span class="sxs-lookup"><span data-stu-id="14298-116">Import objects through OneDrive</span></span>

![importação de objetos](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="14298-118">Importar imagens JPG/PNG ou objetos em 3D FBX (requer o empacotamento no Unity) para o espaço de realidade misturada por meio do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="14298-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="14298-119">Manipular objetos</span><span class="sxs-lookup"><span data-stu-id="14298-119">Manipulate objects</span></span>

![manipulação de objetos](images/manipulate-objects-640px.jpg)

<span data-ttu-id="14298-121">Manipule objetos (mover/girar/escala) com uma interface familiar objeto 3D.</span><span class="sxs-lookup"><span data-stu-id="14298-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="14298-122">Comandos de Bluetooth, mouse/teclado, gestos e voz</span><span class="sxs-lookup"><span data-stu-id="14298-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![dá suporte a Bluetooth](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="14298-124">HoloSketch dá suporte a mouse/teclado Bluetooth, gestos e comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="14298-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="14298-125">Histórico</span><span class="sxs-lookup"><span data-stu-id="14298-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="14298-126">Importância de tendo seu design no dispositivo</span><span class="sxs-lookup"><span data-stu-id="14298-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="14298-127">Quando você projeta algo para HoloLens, é importante experimentar o design no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="14298-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="14298-128">Um dos maiores desafios no design de aplicativos de realidade misturada é que é difícil conseguir o senso de escala, a posição e a profundidade, principalmente por meio de esboços 2D tradicionais.</span><span class="sxs-lookup"><span data-stu-id="14298-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="14298-129">Custo de 2D com base em comunicação</span><span class="sxs-lookup"><span data-stu-id="14298-129">Cost of 2D based communication</span></span>

<span data-ttu-id="14298-130">Para se comunicar efetivamente cenários para outras pessoas e fluxos de experiência do usuário, um designer pode acabar gastando muito tempo na criação de ativos usando ferramentas tradicionais de 2D, como Illustrator, Photoshop e do PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="14298-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="14298-131">Esses designs 2D geralmente exigem mais esforço para convertê-los em 3D.</span><span class="sxs-lookup"><span data-stu-id="14298-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="14298-132">Algumas ideias são perdidas essa conversão de 2D para 3D.</span><span class="sxs-lookup"><span data-stu-id="14298-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="14298-133">Processo de implantação complexas</span><span class="sxs-lookup"><span data-stu-id="14298-133">Complex deployment process</span></span>

<span data-ttu-id="14298-134">Como realidade mista é uma nova tela para nós, ela envolve muita tentativa e erro e de iteração de design por natureza.</span><span class="sxs-lookup"><span data-stu-id="14298-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="14298-135">Para o designer que não estão familiarizados com ferramentas como o Unity e o Visual Studio, não é fácil juntar algo no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="14298-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="14298-136">Normalmente, você precisa passar pelo processo abaixo para ver sua arte 2D/3D no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="14298-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="14298-137">Essa foi uma barreira grande para designers de iteração em cenários e ideias rapidamente.</span><span class="sxs-lookup"><span data-stu-id="14298-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="14298-138">![Processo de implantação complexas](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="14298-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="14298-139">*Processo de implantação*</span><span class="sxs-lookup"><span data-stu-id="14298-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="14298-140">Processo simplificado com HoloSketch</span><span class="sxs-lookup"><span data-stu-id="14298-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="14298-141">Com HoloSketch, queremos simplificar esse processo sem envolver o emparelhamento de portal de dispositivos e ferramentas de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="14298-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="14298-142">Usar o OneDrive, os usuários podem facilmente colocar ativos 2D/3D em HoloLens.</span><span class="sxs-lookup"><span data-stu-id="14298-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="14298-143">![Processo simplificado com HoloSketch](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="14298-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="14298-144">*Processo simplificado com HoloSketch*</span><span class="sxs-lookup"><span data-stu-id="14298-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="14298-145">Incentivar o pensamento do design tridimensional e soluções</span><span class="sxs-lookup"><span data-stu-id="14298-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="14298-146">Achamos que essa ferramenta daria designers uma oportunidade de explorar as soluções em um espaço tridimensional verdadeiramente e não estar preso em 2D.</span><span class="sxs-lookup"><span data-stu-id="14298-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="14298-147">Eles não precisam pensar em criar um plano de fundo 3D para sua interface do usuário, pois o plano de fundo é o mundo real, no caso do Hololens.</span><span class="sxs-lookup"><span data-stu-id="14298-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="14298-148">HoloSketch abre uma maneira para designers explorarem facilmente projeto 3D no Hololens.</span><span class="sxs-lookup"><span data-stu-id="14298-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="14298-149">Introdução</span><span class="sxs-lookup"><span data-stu-id="14298-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="14298-150">Como importar imagens 2D (JPG/PNG) para HoloSketch</span><span class="sxs-lookup"><span data-stu-id="14298-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="14298-151">Carregar imagens JPG/PNG sua pasta do OneDrive ' Documentos/HoloSketch'.</span><span class="sxs-lookup"><span data-stu-id="14298-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="14298-152">No menu OneDrive no HoloSketch, você poderá selecionar e colocar a imagem no ambiente.</span><span class="sxs-lookup"><span data-stu-id="14298-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="14298-153">![A importação de imagens 2D](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="14298-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="14298-154">*Importação de imagens e objetos 3D por meio do OneDrive*</span><span class="sxs-lookup"><span data-stu-id="14298-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="14298-155">Como importar objetos 3D para HoloSketch</span><span class="sxs-lookup"><span data-stu-id="14298-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="14298-156">Antes de carregar sua pasta do OneDrive, siga as etapas abaixo para empacotar seus objetos 3D em um pacote de ativos do Unity.</span><span class="sxs-lookup"><span data-stu-id="14298-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="14298-157">Usando esse processo, você pode importar os arquivos OBJ/FBX de software 3D, como Maya, Cinema 4d e o Microsoft Paint 3D.</span><span class="sxs-lookup"><span data-stu-id="14298-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="14298-158">Atualmente, a criação do pacote ativo é compatível com o Unity versão 5.4.5f1.</span><span class="sxs-lookup"><span data-stu-id="14298-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="14298-159">Baixe e abra o projeto do Unity ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span><span class="sxs-lookup"><span data-stu-id="14298-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="14298-160">Este projeto do Unity inclui o script para a geração de ativo do pacote.</span><span class="sxs-lookup"><span data-stu-id="14298-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="14298-161">Crie um novo GameObject.</span><span class="sxs-lookup"><span data-stu-id="14298-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="14298-162">Nomeie o GameObject com base no conteúdo.</span><span class="sxs-lookup"><span data-stu-id="14298-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="14298-163">No painel de Inspetor, clique em 'Adicionar componente' e adicione 'Box Collider'.</span><span class="sxs-lookup"><span data-stu-id="14298-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![No painel de inspeção, clique em 'Adicionar componente' e adicione 'Box Collider'](images/holosketch-10a-assetbundles-1000px.png)
   
   ![No painel de inspeção, clique em 'Adicionar componente' e adicione 'Box Collider' #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="14298-166">Importe o arquivo FBX 3D, arrastando-o para o painel do projeto.</span><span class="sxs-lookup"><span data-stu-id="14298-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="14298-167">Arraste o objeto para o painel de hierarquia **em seu novo GameObject**.</span><span class="sxs-lookup"><span data-stu-id="14298-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![Arraste o objeto para o painel de hierarquia em seu novo GameObject](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="14298-169">Ajuste a dimensão do colisor se ele não coincide com o objeto.</span><span class="sxs-lookup"><span data-stu-id="14298-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="14298-170">Girar o objeto para enfrentar **eixo z**.</span><span class="sxs-lookup"><span data-stu-id="14298-170">Rotate the object to face **Z-axis**.</span></span>

   ![Ajuste a dimensão do colisor se ele não coincide com o objeto.](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="14298-172">Arraste o objeto do painel de hierarquia para o painel de projeto para **torná-lo pré-fabricado**.</span><span class="sxs-lookup"><span data-stu-id="14298-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="14298-173">Na parte inferior do painel de tarefas do Inspetor de propriedades, clique na lista suspensa, criar e atribuir um novo nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="14298-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="14298-174">Exemplo abaixo mostra a adição e atribuição 'brownchair' para o nome de AssetBundle.</span><span class="sxs-lookup"><span data-stu-id="14298-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![Na parte inferior do painel de tarefas do Inspetor de propriedades, clique na lista suspensa e atribua um novo nome exclusivo.](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="14298-176">Prepare uma imagem em miniatura para o objeto de modelo.</span><span class="sxs-lookup"><span data-stu-id="14298-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="14298-177">![Arraste uma imagem para o painel de projeto e atribua o nome usado para o objeto.](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="14298-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="14298-178">Crie uma pasta chamada 'Assetbundles' na pasta de 'Ativo' do projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="14298-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="14298-179">No menu de ativos, selecione 'Criar AssetBundles' para gerar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="14298-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="14298-180">![No menu de ativos, selecione 'Criar AssetBundles' para gerar o arquivo.](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="14298-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="14298-181">**Carregue o arquivo gerado para a pasta /Files/Documents/HoloSketch no OneDrive.**</span><span class="sxs-lookup"><span data-stu-id="14298-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="14298-182">Carregue o arquivo asset_unique_name apenas.</span><span class="sxs-lookup"><span data-stu-id="14298-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="14298-183">Você não precisa carregar arquivo de AssetBundles ou arquivos de manifesto.</span><span class="sxs-lookup"><span data-stu-id="14298-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="14298-184">![Adicionar arquivos ao arquivos/documentos/HoloSketch/pasta](images/holosketch-onedriveupload-1000px.png)
![você verá o objeto 3D adicionado no menu do OneDrive do HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="14298-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="14298-185">Como manipular os objetos</span><span class="sxs-lookup"><span data-stu-id="14298-185">How to manipulate the objects</span></span>

<span data-ttu-id="14298-186">HoloSketch suporta a interface tradicional que é amplamente usada em software 3D.</span><span class="sxs-lookup"><span data-stu-id="14298-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="14298-187">Você pode usar mover, girar, dimensionar os objetos com gestos e um mouse.</span><span class="sxs-lookup"><span data-stu-id="14298-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="14298-188">Você pode alternar rapidamente entre diferentes modos com voz ou teclado.</span><span class="sxs-lookup"><span data-stu-id="14298-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="14298-189">Modos de manipulação de objeto</span><span class="sxs-lookup"><span data-stu-id="14298-189">Object manipulation modes</span></span>

<span data-ttu-id="14298-190">![Como manipular os objetos](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="14298-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="14298-191">*Como manipular os objetos*</span><span class="sxs-lookup"><span data-stu-id="14298-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="14298-192">Menus contextuais e conjunto de ferramentas</span><span class="sxs-lookup"><span data-stu-id="14298-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="14298-193">**Usando o Menu Contextual**</span><span class="sxs-lookup"><span data-stu-id="14298-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="14298-194">Double e polegar para abrir o Menu Contextual.</span><span class="sxs-lookup"><span data-stu-id="14298-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="14298-195">Itens de menu:</span><span class="sxs-lookup"><span data-stu-id="14298-195">Menu items:</span></span>
* <span data-ttu-id="14298-196">**Superfície de layout:** Esse é um sistema de grade 3D em que você pode definir o layout vários objetos e gerenciá-los como um grupo.</span><span class="sxs-lookup"><span data-stu-id="14298-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="14298-197">Polegar dupla na superfície de Layout para adicionar objetos a ele.</span><span class="sxs-lookup"><span data-stu-id="14298-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="14298-198">**Primitivos:** Usar cubos, esferas, cilindros e cones para massing estudos.</span><span class="sxs-lookup"><span data-stu-id="14298-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="14298-199">**OneDrive:** Abra o menu do OneDrive para importar objetos.</span><span class="sxs-lookup"><span data-stu-id="14298-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="14298-200">**Ajuda:** Exibe a tela de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="14298-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="14298-201">![Menu contextual](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="14298-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="14298-202">*Menu contextual*</span><span class="sxs-lookup"><span data-stu-id="14298-202">*Contextual menu*</span></span>

<span data-ttu-id="14298-203">**Usando o Menu de faixa de ferramenta**</span><span class="sxs-lookup"><span data-stu-id="14298-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="14298-204">Mover, girar, dimensionar, salvar e cena de carga estão disponíveis no Menu de cinto de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="14298-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="14298-205">Usando o teclado, gestos e comandos de voz</span><span class="sxs-lookup"><span data-stu-id="14298-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="14298-206">![Teclado, gestos e comandos de voz](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="14298-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="14298-207">*Teclado, gestos e comandos de voz*</span><span class="sxs-lookup"><span data-stu-id="14298-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="14298-208">Baixe o aplicativo</span><span class="sxs-lookup"><span data-stu-id="14298-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="14298-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Baixe e instale o aplicativo HoloSketch gratuitamente da Microsoft Store</a>
</span><span class="sxs-lookup"><span data-stu-id="14298-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="14298-210">Problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="14298-210">Known issues</span></span>
* <span data-ttu-id="14298-211">Atualmente, a criação do pacote ativo é compatível com **5.4.5f1 de versão do Unity.**</span><span class="sxs-lookup"><span data-stu-id="14298-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="14298-212">Dependendo da quantidade de dados em seu OneDrive, o aplicativo pode aparecer como se ele tiver sido interrompido durante o carregamento de conteúdo do OneDrive</span><span class="sxs-lookup"><span data-stu-id="14298-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="14298-213">Atualmente, salvar e carregar o recurso somente dá suporte a primitivos objetos</span><span class="sxs-lookup"><span data-stu-id="14298-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="14298-214">Menus de texto, som, vídeo e foto estão desabilitados no menu contextual</span><span class="sxs-lookup"><span data-stu-id="14298-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="14298-215">O botão Reproduzir no menu's Tool Belt limpa os utensílios de manipulação</span><span class="sxs-lookup"><span data-stu-id="14298-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="14298-216">Os esboços de compartilhamento</span><span class="sxs-lookup"><span data-stu-id="14298-216">Sharing your sketches</span></span>

<span data-ttu-id="14298-217">Você pode usar o recurso de gravação de vídeo no HoloLens dizendo "Ei Cortana, Iniciar/Parar gravação '.</span><span class="sxs-lookup"><span data-stu-id="14298-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="14298-218">Pressione o chave juntos para tirar uma foto do seu esboço para cima/para baixo volume.</span><span class="sxs-lookup"><span data-stu-id="14298-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="14298-219">Sobre os autores</span><span class="sxs-lookup"><span data-stu-id="14298-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="14298-220"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="14298-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="14298-221">Designer de UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="14298-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="14298-222"><b>Patrick Sebring</b></span><span class="sxs-lookup"><span data-stu-id="14298-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="14298-223">Desenvolvedor @Microsoft</span><span class="sxs-lookup"><span data-stu-id="14298-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
