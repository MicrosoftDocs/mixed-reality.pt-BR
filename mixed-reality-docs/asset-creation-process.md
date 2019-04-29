---
title: Processo de criação do ativo
description: Orientação sobre a criação de ativos para experiências de realidade misturada.
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: ativo, criação, processo, orçamento, polígonos, texturas, sombreadores, desempenho
ms.openlocfilehash: cec689ab4d44591d2d3e84679c3fe51dba161bc5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590942"
---
# <a name="asset-creation-process"></a><span data-ttu-id="69db9-104">Processo de criação do ativo</span><span class="sxs-lookup"><span data-stu-id="69db9-104">Asset creation process</span></span>

<span data-ttu-id="69db9-105">Windows Mixed Reality se baseia em décadas de investimento que a Microsoft fez no DirectX.</span><span class="sxs-lookup"><span data-stu-id="69db9-105">Windows Mixed Reality builds on the decades of investment Microsoft has made into DirectX.</span></span> <span data-ttu-id="69db9-106">Isso significa que todos os desenvolvedores a experiência e habilidades com a criação de 3D gráficos continuam a ser valiosa para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="69db9-106">This means that all of the experience and skills developers have with building 3D graphics continues to be valuable with HoloLens.</span></span>

<span data-ttu-id="69db9-107">Os ativos que você cria para um projeto são fornecidos em várias formas e formulários.</span><span class="sxs-lookup"><span data-stu-id="69db9-107">The assets you create for a project come in many shapes and forms.</span></span> <span data-ttu-id="69db9-108">Eles podem ser compostos de uma série de texturas/imagens, áudio, vídeo, modelos 3D e animações.</span><span class="sxs-lookup"><span data-stu-id="69db9-108">They can be comprised of a series of textures/images, audio, video, 3D models and animations.</span></span> <span data-ttu-id="69db9-109">Não é possível começar cobrir todas as ferramentas que estão disponíveis para criar os diferentes tipos de ativos usados em um projeto.</span><span class="sxs-lookup"><span data-stu-id="69db9-109">We can't begin to cover all the tools that are available to create the different types of assets used in a project.</span></span> <span data-ttu-id="69db9-110">Para este artigo, nos concentraremos em métodos de criação de ativos 3D.</span><span class="sxs-lookup"><span data-stu-id="69db9-110">For this article we will focus on 3D asset creation methods.</span></span>

<span data-ttu-id="69db9-111">![Fluxo de conceito, criação, integração e iteração](images/concept-creation-integration-iteration-flow-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="69db9-111">![Concept, creation, integration and iteration flow](images/concept-creation-integration-iteration-flow-640px.jpg)</span></span><br>
<span data-ttu-id="69db9-112">*Fluxo de conceito, criação, integração e iteração*</span><span class="sxs-lookup"><span data-stu-id="69db9-112">*Concept, creation, integration and iteration flow*</span></span>

## <a name="things-to-consider"></a><span data-ttu-id="69db9-113">O que deve ser considerado</span><span class="sxs-lookup"><span data-stu-id="69db9-113">Things to consider</span></span>

<span data-ttu-id="69db9-114">Quando examinar a experiência que você está tentando criar pense nisso como uma **orçamento** que você possa passar para tentar criar a melhor experiência.</span><span class="sxs-lookup"><span data-stu-id="69db9-114">When looking at the experience you're trying to create think of it as a **budget** that you can spend to try to create the best experience.</span></span> <span data-ttu-id="69db9-115">Não é necessariamente difícil limites no número de **polígonos** ou **tipos de materiais** usar em seus ativos, mas mais um conjunto orçado de vantagens e desvantagens.</span><span class="sxs-lookup"><span data-stu-id="69db9-115">There is not necessarily hard limits on the number of **polygons** or **types of materials** use in your assets but more a budgeted set of tradeoffs.</span></span>

<span data-ttu-id="69db9-116">Abaixo está um orçamento de exemplo para a sua experiência.</span><span class="sxs-lookup"><span data-stu-id="69db9-116">Below is an example budget for your experience.</span></span> <span data-ttu-id="69db9-117">Desempenho geralmente não é um ponto único de falha, mas morte por mil Cortes por-se.</span><span class="sxs-lookup"><span data-stu-id="69db9-117">Performance is usually not a single point of failure but death by a thousand cuts per-se.</span></span>
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><span data-ttu-id="69db9-118"><b>Ativos</b></span><span class="sxs-lookup"><span data-stu-id="69db9-118"><b>Assets</b></span></span></th><th style="text-align:right;"> <span data-ttu-id="69db9-119">CPU</span><span class="sxs-lookup"><span data-stu-id="69db9-119">CPU</span></span></th><th> <span data-ttu-id="69db9-120">GPU</span><span class="sxs-lookup"><span data-stu-id="69db9-120">GPU</span></span></th><th> <span data-ttu-id="69db9-121">Memória</span><span class="sxs-lookup"><span data-stu-id="69db9-121">Memory</span></span></th>
</tr><tr>
<td> <span data-ttu-id="69db9-122">Polígonos</span><span class="sxs-lookup"><span data-stu-id="69db9-122">Polygons</span></span></td><td> <span data-ttu-id="69db9-123">0%</span><span class="sxs-lookup"><span data-stu-id="69db9-123">0%</span></span></td><td> <span data-ttu-id="69db9-124">5%</span><span class="sxs-lookup"><span data-stu-id="69db9-124">5%</span></span></td><td> <span data-ttu-id="69db9-125">10%</span><span class="sxs-lookup"><span data-stu-id="69db9-125">10%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="69db9-126">Texturas</span><span class="sxs-lookup"><span data-stu-id="69db9-126">Textures</span></span></td><td> <span data-ttu-id="69db9-127">5%</span><span class="sxs-lookup"><span data-stu-id="69db9-127">5%</span></span></td><td> <span data-ttu-id="69db9-128">15%</span><span class="sxs-lookup"><span data-stu-id="69db9-128">15%</span></span></td><td><span data-ttu-id="69db9-129">25%</span><span class="sxs-lookup"><span data-stu-id="69db9-129">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="69db9-130">Sombreadores</span><span class="sxs-lookup"><span data-stu-id="69db9-130">Shaders</span></span></td><td> <span data-ttu-id="69db9-131">15%</span><span class="sxs-lookup"><span data-stu-id="69db9-131">15%</span></span></td><td> <span data-ttu-id="69db9-132">35%</span><span class="sxs-lookup"><span data-stu-id="69db9-132">35%</span></span></td><td> <span data-ttu-id="69db9-133">0%</span><span class="sxs-lookup"><span data-stu-id="69db9-133">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="69db9-134"><b>Dynamics</b></span><span class="sxs-lookup"><span data-stu-id="69db9-134"><b>Dynamics</b></span></span></td><td></td><td></td><td></td>
</tr><tr>
<td> <span data-ttu-id="69db9-135">Física</span><span class="sxs-lookup"><span data-stu-id="69db9-135">Physics</span></span></td><td> <span data-ttu-id="69db9-136">5%</span><span class="sxs-lookup"><span data-stu-id="69db9-136">5%</span></span></td><td> <span data-ttu-id="69db9-137">15%</span><span class="sxs-lookup"><span data-stu-id="69db9-137">15%</span></span></td><td> <span data-ttu-id="69db9-138">0%</span><span class="sxs-lookup"><span data-stu-id="69db9-138">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="69db9-139">Iluminação em tempo real</span><span class="sxs-lookup"><span data-stu-id="69db9-139">Realtime lighting</span></span></td><td> <span data-ttu-id="69db9-140">10%</span><span class="sxs-lookup"><span data-stu-id="69db9-140">10%</span></span></td><td> <span data-ttu-id="69db9-141">0%</span><span class="sxs-lookup"><span data-stu-id="69db9-141">0%</span></span></td><td> <span data-ttu-id="69db9-142">0%</span><span class="sxs-lookup"><span data-stu-id="69db9-142">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="69db9-143">Mídia (áudio/vídeo)</span><span class="sxs-lookup"><span data-stu-id="69db9-143">Media (audio/video)</span></span></td><td> -</td><td> <span data-ttu-id="69db9-144">15%</span><span class="sxs-lookup"><span data-stu-id="69db9-144">15%</span></span></td><td> <span data-ttu-id="69db9-145">25%</span><span class="sxs-lookup"><span data-stu-id="69db9-145">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="69db9-146">Lógica do script</span><span class="sxs-lookup"><span data-stu-id="69db9-146">Script/logic</span></span></td><td> <span data-ttu-id="69db9-147">25%</span><span class="sxs-lookup"><span data-stu-id="69db9-147">25%</span></span></td><td> <span data-ttu-id="69db9-148">0%</span><span class="sxs-lookup"><span data-stu-id="69db9-148">0%</span></span></td><td> <span data-ttu-id="69db9-149">5%</span><span class="sxs-lookup"><span data-stu-id="69db9-149">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="69db9-150">Sobrecarga geral</span><span class="sxs-lookup"><span data-stu-id="69db9-150">General overhead</span></span></td><td> <span data-ttu-id="69db9-151">5%</span><span class="sxs-lookup"><span data-stu-id="69db9-151">5%</span></span></td><td> <span data-ttu-id="69db9-152">5%</span><span class="sxs-lookup"><span data-stu-id="69db9-152">5%</span></span></td><td> <span data-ttu-id="69db9-153">5%</span><span class="sxs-lookup"><span data-stu-id="69db9-153">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="69db9-154"><b>Total</b></span><span class="sxs-lookup"><span data-stu-id="69db9-154"><b>Total</b></span></span></td><td> <span data-ttu-id="69db9-155"><b>65%</b></span><span class="sxs-lookup"><span data-stu-id="69db9-155"><b>65%</b></span></span></td><td> <span data-ttu-id="69db9-156"><b>90%</b></span><span class="sxs-lookup"><span data-stu-id="69db9-156"><b>90%</b></span></span></td><td> <span data-ttu-id="69db9-157"><b>70%</b></span><span class="sxs-lookup"><span data-stu-id="69db9-157"><b>70%</b></span></span></td>
</tr>
</table>

<span data-ttu-id="69db9-158">**Número total de ativos**</span><span class="sxs-lookup"><span data-stu-id="69db9-158">**Total number of assets**</span></span>
* <span data-ttu-id="69db9-159">Como muitos ativos estão ativos na cena?</span><span class="sxs-lookup"><span data-stu-id="69db9-159">How many assets are active in the scene?</span></span>

<span data-ttu-id="69db9-160">**Complexidade de ativos**</span><span class="sxs-lookup"><span data-stu-id="69db9-160">**Complexity of assets**</span></span>
* <span data-ttu-id="69db9-161">Quantos triângulos / polígonos?</span><span class="sxs-lookup"><span data-stu-id="69db9-161">How many triangles / polygons?</span></span>
* <span data-ttu-id="69db9-162">Quão complexo é o sombreador?</span><span class="sxs-lookup"><span data-stu-id="69db9-162">How complex is the shader?</span></span>

<span data-ttu-id="69db9-163">Desenvolvedores e artistas devem considerar os recursos do dispositivo e o mecanismo gráfico.</span><span class="sxs-lookup"><span data-stu-id="69db9-163">Both the developers and artists have to consider the capabilities of the device and the graphics engine.</span></span> <span data-ttu-id="69db9-164">Microsoft HoloLens tem todos os de computação e gráficos integrada no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="69db9-164">Microsoft HoloLens has all of the computational and graphics built into the device.</span></span> <span data-ttu-id="69db9-165">Ele compartilha os recursos que os desenvolvedores encontraria em uma plataforma móvel.</span><span class="sxs-lookup"><span data-stu-id="69db9-165">It shares the capabilities developers would find on a mobile platform.</span></span>

<span data-ttu-id="69db9-166">O processo de criação de ativos é o mesmo, independentemente se você estiver visando uma experiência para um [holográfico dispositivo ou um dispositivo de imersão](mixed-reality.md#the-mixed-reality-spectrum).</span><span class="sxs-lookup"><span data-stu-id="69db9-166">The creation process for assets is the same regardless of whether you're targeting an experience for a [holographic device or an immersive device](mixed-reality.md#the-mixed-reality-spectrum).</span></span> <span data-ttu-id="69db9-167">A coisa principal a observar é a funcionalidade do dispositivo, conforme mencionado acima, bem como escala, pois você pode ver o mundo real na realidade misturada, que você desejará manter a escala correta com base na experiência.</span><span class="sxs-lookup"><span data-stu-id="69db9-167">The primary thing to note is the device capability as mentioned above as well as scale since you can see the real world in mixed reality you will want to maintain the correct scale based on the experience.</span></span> 

## <a name="authoring-assets"></a><span data-ttu-id="69db9-168">Criação de ativos</span><span class="sxs-lookup"><span data-stu-id="69db9-168">Authoring Assets</span></span>

<span data-ttu-id="69db9-169">Vamos começar com as maneiras de obter ativos para seu projeto:</span><span class="sxs-lookup"><span data-stu-id="69db9-169">We'll start with the ways to get assets for your project:</span></span>
1. <span data-ttu-id="69db9-170">Criação de ativos (ferramentas de criação e captura do objeto)</span><span class="sxs-lookup"><span data-stu-id="69db9-170">Creating Assets (Authoring tools and object capture)</span></span>
2. <span data-ttu-id="69db9-171">Compra de ativos (ativos em comprando on-line)</span><span class="sxs-lookup"><span data-stu-id="69db9-171">Purchasing Assets (Buying assets online)</span></span>
3. <span data-ttu-id="69db9-172">Portabilidade de ativos (levando ativos existentes)</span><span class="sxs-lookup"><span data-stu-id="69db9-172">Porting Assets (Taking existing assets)</span></span>
4. <span data-ttu-id="69db9-173">Terceirização ativos (importando ativos de partes 3ª)</span><span class="sxs-lookup"><span data-stu-id="69db9-173">Outsourcing Assets (Importing assets from 3rd parties)</span></span>

### <a name="creating-assets"></a><span data-ttu-id="69db9-174">Criação de ativos</span><span class="sxs-lookup"><span data-stu-id="69db9-174">Creating assets</span></span>

<span data-ttu-id="69db9-175">**Ferramentas de criação**</span><span class="sxs-lookup"><span data-stu-id="69db9-175">**Authoring tools**</span></span><br>
<span data-ttu-id="69db9-176">Primeiro, você pode criar seus próprios ativos em um número de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="69db9-176">First you can create your own assets in a number of different ways.</span></span> <span data-ttu-id="69db9-177">Artistas 3D usam um número de aplicativos e ferramentas para criar modelos que consistem **malhas**, **texturas**, e **materiais**.</span><span class="sxs-lookup"><span data-stu-id="69db9-177">3D artists use a number of applications and tools to create models which consist of **meshes**, **textures**, and **materials**.</span></span> <span data-ttu-id="69db9-178">Isso é salvo em um formato de arquivo que pode ser importado ou usado pelo mecanismo de elementos gráficos usado pelo aplicativo, tais como **. FBX** ou **. OBJ**.</span><span class="sxs-lookup"><span data-stu-id="69db9-178">This is then saved in a file format that can be imported or used by the graphics engine used by the app, such as **.FBX** or **.OBJ**.</span></span> <span data-ttu-id="69db9-179">Qualquer ferramenta que gera um modelo que dá suporte a seu mecanismo de gráfico escolhido funcionará em **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="69db9-179">Any tool that generates a model that your chosen graphics engine supports will work on **HoloLens**.</span></span> <span data-ttu-id="69db9-180">Entre artistas 3D, muitos optar por usar [Autodesk Maya que por si só é capaz de usar o HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) para transformar os ativos da maneira como são criados.</span><span class="sxs-lookup"><span data-stu-id="69db9-180">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="69db9-181">Se você quiser obter algo rápido você também pode usar [construtor 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) que vem com o Windows para exportar. OBJ para uso em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="69db9-181">If you want to get something in quick you can also use [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) that comes with Windows to export .OBJ for use in your application.</span></span>

<span data-ttu-id="69db9-182">**Captura de objeto**</span><span class="sxs-lookup"><span data-stu-id="69db9-182">**Object capture**</span></span><br>
<span data-ttu-id="69db9-183">Também há a opção para capturar objetos em 3D.</span><span class="sxs-lookup"><span data-stu-id="69db9-183">There is also the option to capture objects in 3D.</span></span> <span data-ttu-id="69db9-184">Captura de objetos inanimados em 3D e editá-los com o software de criação de conteúdo digital é cada vez mais popular com o surgimento de impressão 3D.</span><span class="sxs-lookup"><span data-stu-id="69db9-184">Capturing inanimate objects in 3D and editing them with digital content creation software is increasingly popular with the rise of 3D printing.</span></span> <span data-ttu-id="69db9-185">Usando o **Kinect 2** sensor e [construtor 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) você pode usar o recurso de captura para criar ativos de objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="69db9-185">Using the **Kinect 2** sensor and [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) you can use the capture feature to create assets from real world objects.</span></span> <span data-ttu-id="69db9-186">Isso também é um [pacote de ferramentas](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) para fazer o mesmo com **photogrammetry** pelo processamento de um número de imagens para costurar junto e malha e texturas.</span><span class="sxs-lookup"><span data-stu-id="69db9-186">This is also a [suite of tools](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) to do the same with **photogrammetry** by processing a number of images to stitch together and mesh and textures.</span></span>

### <a name="purchasing-assets"></a><span data-ttu-id="69db9-187">Compra de ativos</span><span class="sxs-lookup"><span data-stu-id="69db9-187">Purchasing assets</span></span>

<span data-ttu-id="69db9-188">É outra excelente opção para ativos para a sua experiência de compra.</span><span class="sxs-lookup"><span data-stu-id="69db9-188">Another excellent option is to purchase assets for your experience.</span></span> <span data-ttu-id="69db9-189">Há uma tonelada de ativos disponíveis por meio de serviços, como o [Unity Asset Store](https://www.assetstore.unity3d.com/) ou [TurboSquid](http://www.turbosquid.com/) entre outros.</span><span class="sxs-lookup"><span data-stu-id="69db9-189">There are a ton of assets available through services such as the [Unity Asset Store](https://www.assetstore.unity3d.com/) or [TurboSquid](http://www.turbosquid.com/) among others.</span></span>

<span data-ttu-id="69db9-190">Quando você adquire os ativos de uma parte 3ª que sempre quiser verificar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="69db9-190">When you purchase assets from a 3rd party you always want to check the following:</span></span>
* <span data-ttu-id="69db9-191">**O que é a contagem de poly?**</span><span class="sxs-lookup"><span data-stu-id="69db9-191">**What's the poly count?**</span></span>
  * <span data-ttu-id="69db9-192">Ele se ajustar dentro do orçamento?</span><span class="sxs-lookup"><span data-stu-id="69db9-192">Does it fit within your budget?</span></span>
* <span data-ttu-id="69db9-193">**Há níveis de detalhe (LODs) para o modelo?**</span><span class="sxs-lookup"><span data-stu-id="69db9-193">**Are there levels of detail (LODs) for the model?**</span></span>
  * <span data-ttu-id="69db9-194">Nível de detalhes de um modelo permitem que você dimensione os detalhes de um modelo para o desempenho.</span><span class="sxs-lookup"><span data-stu-id="69db9-194">Level of detail of a model allow you to scale the detail of a model for performance.</span></span>
* <span data-ttu-id="69db9-195">**O arquivo de origem está disponível?**</span><span class="sxs-lookup"><span data-stu-id="69db9-195">**Is the source file available?**</span></span>
  * <span data-ttu-id="69db9-196">Normalmente, não estão incluídos no [Unity Asset Store](https://www.assetstore.unity3d.com/) , mas sempre incluído com serviços como [TurboSquid](http://www.turbosquid.com/).</span><span class="sxs-lookup"><span data-stu-id="69db9-196">Usually not included with [Unity Asset Store](https://www.assetstore.unity3d.com/) but always included with services like [TurboSquid](http://www.turbosquid.com/).</span></span>
  * <span data-ttu-id="69db9-197">Sem o arquivo de origem não será capaz de modificar o ativo.</span><span class="sxs-lookup"><span data-stu-id="69db9-197">Without the source file you won't be able to modify the asset.</span></span>
  * <span data-ttu-id="69db9-198">Verifique se o arquivo de origem fornecido pode ser importado por suas ferramentas 3D.</span><span class="sxs-lookup"><span data-stu-id="69db9-198">Make sure the source file provided can be imported by your 3D tools.</span></span>
* <span data-ttu-id="69db9-199">**Saber o que você esteja tirando**</span><span class="sxs-lookup"><span data-stu-id="69db9-199">**Know what you're getting**</span></span>
  * <span data-ttu-id="69db9-200">As animações são fornecidas?</span><span class="sxs-lookup"><span data-stu-id="69db9-200">Are animations provided?</span></span>
  * <span data-ttu-id="69db9-201">Certifique-se de verificar a lista de conteúdo do ativo que você vai adquirir.</span><span class="sxs-lookup"><span data-stu-id="69db9-201">Make sure to check the contents list of the asset you're purchasing.</span></span>

### <a name="porting-assets"></a><span data-ttu-id="69db9-202">Portabilidade de ativos</span><span class="sxs-lookup"><span data-stu-id="69db9-202">Porting assets</span></span>

<span data-ttu-id="69db9-203">Em alguns casos, será entregue ativos existentes que foram originalmente criados para outros dispositivos e aplicativos diferentes.</span><span class="sxs-lookup"><span data-stu-id="69db9-203">In some cases you'll be handed existing assets that were originally built for other devices and different apps.</span></span> <span data-ttu-id="69db9-204">Na maioria dos casos, esses ativos podem ser convertidos para formatos compatíveis com o mecanismo gráfico do que seu aplicativo está usando.</span><span class="sxs-lookup"><span data-stu-id="69db9-204">In most cases these assets can be converted to formats compatible with the graphics engine their app is using.</span></span>

<span data-ttu-id="69db9-205">Ao portar ativos para usar em seu aplicativo HoloLens, você desejará fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="69db9-205">When porting assets to use in your HoloLens application you will want to ask the following:</span></span>
* <span data-ttu-id="69db9-206">**Você pode importar diretamente ou precisam ser convertidos para outro formato?**</span><span class="sxs-lookup"><span data-stu-id="69db9-206">**Can you import directly or does need to be converted to another format?**</span></span> <span data-ttu-id="69db9-207">Verifique o formato que você está importando com o mecanismo de elementos gráficos que você está usando.</span><span class="sxs-lookup"><span data-stu-id="69db9-207">Check the format you're importing with the graphics engine you're using.</span></span>
* <span data-ttu-id="69db9-208">**Se a conversão em um formato compatível é algo perdido?**</span><span class="sxs-lookup"><span data-stu-id="69db9-208">**If converting to a compatible format is anything lost?**</span></span> <span data-ttu-id="69db9-209">Às vezes, os detalhes podem ser perdidos ou importando pode fazer com que os artefatos que precisam ser limpos em uma ferramenta de criação de 3D.</span><span class="sxs-lookup"><span data-stu-id="69db9-209">Sometimes details can be lost or importing can cause artifacts that need to be cleaned up in a 3D authoring tool.</span></span>
* <span data-ttu-id="69db9-210">**O que é os triângulos / contagem de polígonos para o ativo?**</span><span class="sxs-lookup"><span data-stu-id="69db9-210">**What is the triangles / polygons count for the asset?**</span></span> <span data-ttu-id="69db9-211">Com base no orçamento para o aplicativo você pode usar [Simplygon](https://www.simplygon.com/) ou ferramentas semelhantes para decimate (manual ou forma procedimental reduzir a contagem de poly) o ativo original para caber dentro do orçamento de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="69db9-211">Based on the budget for you application you can use [Simplygon](https://www.simplygon.com/) or similar tools to decimate (procedurally or manually reduce poly count) the original asset to fit within your applications budget.</span></span>

### <a name="outsourcing-assets"></a><span data-ttu-id="69db9-212">Ativos de terceirização</span><span class="sxs-lookup"><span data-stu-id="69db9-212">Outsourcing assets</span></span>

<span data-ttu-id="69db9-213">Outra opção para projetos maiores que exigem mais ativos que sua equipe é equipado para criar é terceirizar a criação do ativo.</span><span class="sxs-lookup"><span data-stu-id="69db9-213">Another option for larger projects that require more assets than your team is equipped to create is to outsource asset creation.</span></span> <span data-ttu-id="69db9-214">O processo de terceirização envolve a localização do studio à direita ou a agência especializada em ativos de terceirização.</span><span class="sxs-lookup"><span data-stu-id="69db9-214">The process of outsourcing involves finding the right studio or agency that specializes in outsourcing assets.</span></span> <span data-ttu-id="69db9-215">Isso pode ser a opção mais cara, mas também ser a mais flexível em que você obtém.</span><span class="sxs-lookup"><span data-stu-id="69db9-215">This can be the most expensive option but also be the most flexible in what you get.</span></span>
* <span data-ttu-id="69db9-216">**Definir claramente o que está solicitando**</span><span class="sxs-lookup"><span data-stu-id="69db9-216">**Clearly define what you're requesting**</span></span>
  * <span data-ttu-id="69db9-217">Forneça o máximo de detalhes possíveis</span><span class="sxs-lookup"><span data-stu-id="69db9-217">Provide as much detail as possible</span></span>
  * <span data-ttu-id="69db9-218">Frontal, lado e imagens do conceito de voltar</span><span class="sxs-lookup"><span data-stu-id="69db9-218">Front, side and back concept images</span></span>
  * <span data-ttu-id="69db9-219">Ativo de mostrando de arte de referência no contexto</span><span class="sxs-lookup"><span data-stu-id="69db9-219">Reference art showing asset in context</span></span>
  * <span data-ttu-id="69db9-220">Escala do objeto (geralmente especificado em centímetros)</span><span class="sxs-lookup"><span data-stu-id="69db9-220">Scale of object (Usually specified in centimeters)</span></span>
* <span data-ttu-id="69db9-221">**Forneça um orçamento**</span><span class="sxs-lookup"><span data-stu-id="69db9-221">**Provide a Budget**</span></span>
  * <span data-ttu-id="69db9-222">Intervalo de contagem Poly</span><span class="sxs-lookup"><span data-stu-id="69db9-222">Poly count range</span></span>
  * <span data-ttu-id="69db9-223">Número de texturas</span><span class="sxs-lookup"><span data-stu-id="69db9-223">Number of textures</span></span>
  * <span data-ttu-id="69db9-224">Tipo de sombreador (para o Unity e HoloLens, você deve sempre padrão sombreadores móveis pela primeira vez)</span><span class="sxs-lookup"><span data-stu-id="69db9-224">Type of shader (For Unity and HoloLens you should always default to mobile shaders first)</span></span>
* <span data-ttu-id="69db9-225">**Entender os custos**</span><span class="sxs-lookup"><span data-stu-id="69db9-225">**Understand the costs**</span></span>
  * <span data-ttu-id="69db9-226">Qual é a política de terceirização para solicitações de mudança?</span><span class="sxs-lookup"><span data-stu-id="69db9-226">What's the outsourcing policy for change requests?</span></span>

<span data-ttu-id="69db9-227">Terceirização pode funcionar muito bem com base em sua linha do tempo de projetos, mas exige mais supervisão para garantir que você obtenha os ativos certos que na primeira vez que você precisa.</span><span class="sxs-lookup"><span data-stu-id="69db9-227">Outsourcing can work extremely well based on your projects timeline but requires more oversight to guarantee that you get the right assets you need the first time.</span></span>