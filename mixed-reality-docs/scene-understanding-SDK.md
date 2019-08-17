---
title: SDK de compreensão da cena
description: Guia de programação para o SDK de compreensão da cena
author: szymons
ms.author: szymons
ms.date: 07/08/19
ms.topic: article
keywords: Compreensão da cena, mapeamento espacial, realidade do Windows Mixed, Unity
ms.openlocfilehash: 152ffdbd84798c164963717a8dc41beb2e1a0902
ms.sourcegitcommit: e9a55528965048ce34f8247ef6e544f9f432ee37
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559857"
---
## <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="24cd3-104">Visão geral do SDK de compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="24cd3-104">Scene Understanding SDK Overview</span></span>

<span data-ttu-id="24cd3-105">A meta da compreensão da cena é transformar os dados do sensor de ambiente não estruturado que o dispositivo da realidade misturada captura e convertê-lo em uma representação avançada, mas abstrata, intuitiva e fácil de desenvolver para o.</span><span class="sxs-lookup"><span data-stu-id="24cd3-105">The goal of Scene Understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span></span> <span data-ttu-id="24cd3-106">O SDK atua como a camada de comunicação entre seu aplicativo e o tempo de execução de compreensão da cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="24cd3-107">Ele é destinado a imitar construções padrão existentes, como grafos de cena 3D para representações 3D e retângulos/painéis 2D para aplicativos 2D.</span><span class="sxs-lookup"><span data-stu-id="24cd3-107">It's aimed to mimic existing standard constructs such as 3d scene graphs for 3d representations and 2D rectangles/panels for 2d applications.</span></span> <span data-ttu-id="24cd3-108">Embora as construções que compreendem as imitações da cena sejam mapeadas para as estruturas concretas que você pode usar, em geral SceneUnderstanding é a estrutura independente, permitindo a interoperabilidade entre estruturas variadas que interagem com ela.</span><span class="sxs-lookup"><span data-stu-id="24cd3-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span></span> <span data-ttu-id="24cd3-109">Conforme a compreensão da cena desenvolve a função do SDK, para garantir que novas representações e funcionalidades continuem a ser expostas em uma estrutura unificada.</span><span class="sxs-lookup"><span data-stu-id="24cd3-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="24cd3-110">Neste documento, primeiro apresentaremos conceitos de alto nível que ajudarão você a se familiarizar com o uso/ambiente de desenvolvimento e, em seguida, fornecer uma documentação mais detalhada para classes e construções específicas.</span><span class="sxs-lookup"><span data-stu-id="24cd3-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="24cd3-111">Onde obtenho o SDK?</span><span class="sxs-lookup"><span data-stu-id="24cd3-111">Where do I get the SDK?</span></span>

<span data-ttu-id="24cd3-112">O SDK do SceneUnderstanding é baixável via NuGet.</span><span class="sxs-lookup"><span data-stu-id="24cd3-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="24cd3-113">SDK do SceneUnderstanding</span><span class="sxs-lookup"><span data-stu-id="24cd3-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="24cd3-114">Antes de começar, observe que o SDK é executado na parte superior do UWP e requer SDK do Windows versão 18362 ou superior.</span><span class="sxs-lookup"><span data-stu-id="24cd3-114">Before you begin please note that the SDK runs on top of the UWP, and requires Windows SDK version 18362 or higher.</span></span> 

### <a name="the-scene"></a><span data-ttu-id="24cd3-115">A cena</span><span class="sxs-lookup"><span data-stu-id="24cd3-115">The Scene</span></span>

<span data-ttu-id="24cd3-116">Seu dispositivo de realidade misturada está constantemente integrando informações sobre o que vê em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="24cd3-116">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="24cd3-117">A compreensão da cena funil todas essas fontes de dados e produz uma única abstração coesa.</span><span class="sxs-lookup"><span data-stu-id="24cd3-117">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="24cd3-118">A compreensão da cena gera cenas que são uma composição de [SceneObjects](scene-understanding-SDK.md#sceneobjects) que representam uma instância de uma única coisa (por exemplo, uma parede/teto/andar). Os próprios objetos de cena são uma composição de [SceneComponents](scene-understanding-SDK.md#scenecomponents) que representam partes mais granulares que compõem esse sceneobject.</span><span class="sxs-lookup"><span data-stu-id="24cd3-118">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="24cd3-119">Exemplos de componentes são quádruplos e malhas, mas no futuro poderiam representar caixas delimitadoras, mehses de colisão, metadados, etc...</span><span class="sxs-lookup"><span data-stu-id="24cd3-119">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision mehses, metadata etc...</span></span>

<span data-ttu-id="24cd3-120">O processo de converter os dados brutos do sensor em uma cena é uma operação potencialmente cara que pode levar segundos para espaços médios (~ 10x10m) a minutos para espaços muito grandes (~ 50x50m) e, portanto, não é algo que está sendo computado pelo dispositivo sem solicitação de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24cd3-120">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="24cd3-121">Em vez disso, a geração de cena é disparada por seu aplicativo sob demanda.</span><span class="sxs-lookup"><span data-stu-id="24cd3-121">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="24cd3-122">A classe SceneObserver tem métodos estáticos que podem calcular ou desserializar uma cena, com a qual você pode enumerar/interagir.</span><span class="sxs-lookup"><span data-stu-id="24cd3-122">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="24cd3-123">A ação de "computação" é executada sob demanda e é executada na CPU, mas em um processo separado (o driver de realidade misturada).</span><span class="sxs-lookup"><span data-stu-id="24cd3-123">The "Compute" action is executed on-demand and executes on the CPU but in a seperate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="24cd3-124">No entanto, enquanto fazemos a computação em outro processo, os dados de cena resultantes são armazenados e mantidos em seu aplicativo no objeto de cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-124">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="24cd3-125">Veja abaixo um diagrama que ilustra esse fluxo de processo e mostra exemplos de dois aplicativos que se destinam ao tempo de execução de compreensão da cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-125">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Diagrama de processo](images/SU-ProcessFlow.png)

<span data-ttu-id="24cd3-127">No lado esquerdo, há um diagrama do tempo de execução misto da realidade que está sempre ligado e em execução em seu próprio processo.</span><span class="sxs-lookup"><span data-stu-id="24cd3-127">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span></span> <span data-ttu-id="24cd3-128">Esse tempo de execução é responsável por executar o rastreamento de dispositivos, a reconstrução da superfície e outras operações que a cena entende para entender e o motivo do mundo em torno de você.</span><span class="sxs-lookup"><span data-stu-id="24cd3-128">This runtime is responsible for performing device tracking, surface reconstruction, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="24cd3-129">No lado direito do diagrama, mostramos dois aplicativos teóricos que fazem uso da compreensão da cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-129">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="24cd3-130">As primeiras interfaces de aplicativo com MRTK que usam o SDK de compreensão da cena internamente, o segundo aplicativo computa e usa duas instâncias de cena sepereate.</span><span class="sxs-lookup"><span data-stu-id="24cd3-130">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two sepereate scene instances.</span></span> <span data-ttu-id="24cd3-131">Todos os 3 bastidores neste diagrama geram instâncias distintas dos bastidores, o driver não está acompanhando o estado global que é compartilhado entre aplicativos e objetos de cena em uma cena não é encontrado em outro.</span><span class="sxs-lookup"><span data-stu-id="24cd3-131">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span></span> <span data-ttu-id="24cd3-132">A compreensão da cena fornece um mecanismo para controlar ao longo do tempo, mas isso é feito usando o SDK e o código que executa esse controle é executado no SDK no processo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24cd3-132">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and code the code that performs this tracking is running in the SDK in your app's process.</span></span>

<span data-ttu-id="24cd3-133">Como cada cena armazena os dados no espaço de memória do seu aplicativo, você pode pressupor que toda a função do objeto de cena ou de seus dados internos sempre seja executada no processo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24cd3-133">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

#### <a name="layout"></a><span data-ttu-id="24cd3-134">Layout</span><span class="sxs-lookup"><span data-stu-id="24cd3-134">Layout</span></span>

<span data-ttu-id="24cd3-135">Para trabalhar com a compreensão da cena, pode ser importante saber e entender como o tempo de execução representa os componentes logicamente e fisicamente.</span><span class="sxs-lookup"><span data-stu-id="24cd3-135">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="24cd3-136">A cena representa dados com um layout específico que foi escolhido para ser simples enquanto mantém uma estrutura subjacente que é pliable para atender aos requisitos futuros sem precisar de revisões principais.</span><span class="sxs-lookup"><span data-stu-id="24cd3-136">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="24cd3-137">A cena faz isso armazenando todos os componentes (blocos de construção para todos os objetos de cena) em uma lista simples e definindo a hierarquia e a composição por meio de referências em que componentes específicos fazem referência a outros.</span><span class="sxs-lookup"><span data-stu-id="24cd3-137">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="24cd3-138">Abaixo, apresentamos um exemplo de uma estrutura em sua forma fixa e lógica.</span><span class="sxs-lookup"><span data-stu-id="24cd3-138">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="24cd3-139">Layout lógico</span><span class="sxs-lookup"><span data-stu-id="24cd3-139">Logical Layout</span></span></th><th><span data-ttu-id="24cd3-140">Layout físico</span><span class="sxs-lookup"><span data-stu-id="24cd3-140">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="24cd3-141">Cena</span><span class="sxs-lookup"><span data-stu-id="24cd3-141">Scene</span></span>
  <ul>
  <li><span data-ttu-id="24cd3-142">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="24cd3-142">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="24cd3-143">Mesh_1</span><span class="sxs-lookup"><span data-stu-id="24cd3-143">Mesh_1</span></span></li>
      <li><span data-ttu-id="24cd3-144">Quad_1</span><span class="sxs-lookup"><span data-stu-id="24cd3-144">Quad_1</span></span></li>
      <li><span data-ttu-id="24cd3-145">Quad_2</span><span class="sxs-lookup"><span data-stu-id="24cd3-145">Quad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="24cd3-146">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="24cd3-146">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="24cd3-147">Quad_1</span><span class="sxs-lookup"><span data-stu-id="24cd3-147">Quad_1</span></span></li>
      <li><span data-ttu-id="24cd3-148">Quad_3</span><span class="sxs-lookup"><span data-stu-id="24cd3-148">Quad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="24cd3-149">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="24cd3-149">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="24cd3-150">Mesh_3</span><span class="sxs-lookup"><span data-stu-id="24cd3-150">Mesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="24cd3-151">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="24cd3-151">SceneObject_1</span></span></li>
  <li><span data-ttu-id="24cd3-152">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="24cd3-152">SceneObject_2</span></span></li>
  <li><span data-ttu-id="24cd3-153">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="24cd3-153">SceneObject_3</span></span></li>
  <li><span data-ttu-id="24cd3-154">Quad_1</span><span class="sxs-lookup"><span data-stu-id="24cd3-154">Quad_1</span></span></li>
  <li><span data-ttu-id="24cd3-155">Quad_2</span><span class="sxs-lookup"><span data-stu-id="24cd3-155">Quad_2</span></span></li>
  <li><span data-ttu-id="24cd3-156">Quad_3</span><span class="sxs-lookup"><span data-stu-id="24cd3-156">Quad_3</span></span></li>
  <li><span data-ttu-id="24cd3-157">Mesh_1</span><span class="sxs-lookup"><span data-stu-id="24cd3-157">Mesh_1</span></span></li>
  <li><span data-ttu-id="24cd3-158">Mesh_2</span><span class="sxs-lookup"><span data-stu-id="24cd3-158">Mesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="24cd3-159">Esta ilustração realça a diferença entre o layout lógico e físico da cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-159">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="24cd3-160">À direita, vemos o layout hierárquico dos dados que seu aplicativo vê ao enumerar a cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-160">On the right we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="24cd3-161">À esquerda, vemos que a cena é realmente composta de 12 componentes distintos acessíveis individualmente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="24cd3-161">On the left we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="24cd3-162">Ao processar uma nova cena, esperamos que os aplicativos orientem essa hierarquia logicamente, no entanto, ao controlar entre as atualizações de cena, alguns aplicativos só podem estar interessados em direcionar componentes específicos que são compartilhados entre duas cenas.</span><span class="sxs-lookup"><span data-stu-id="24cd3-162">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

### <a name="high-level-overview"></a><span data-ttu-id="24cd3-163">Visão geral de alto nível</span><span class="sxs-lookup"><span data-stu-id="24cd3-163">High-level Overview</span></span>

<span data-ttu-id="24cd3-164">A seção a seguir fornece uma visão geral de alto nível das construções na compreensão da cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-164">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="24cd3-165">A leitura desta seção lhe dará uma compreensão de como as cenas são representadas e de quais os vários componentes do/são usados.</span><span class="sxs-lookup"><span data-stu-id="24cd3-165">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="24cd3-166">A próxima seção fornecerá exemplos de código concretos e detalhes adicionais que são brilhantes nesta visão geral.</span><span class="sxs-lookup"><span data-stu-id="24cd3-166">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

#### <a name="scenecomponents"></a><span data-ttu-id="24cd3-167">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="24cd3-167">SceneComponents</span></span>

<span data-ttu-id="24cd3-168">Agora que você entende o layout lógico de cenas, agora podemos apresentar o conceito de SceneComponents e como eles são usados para compor a hierarquia.</span><span class="sxs-lookup"><span data-stu-id="24cd3-168">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span></span> <span data-ttu-id="24cd3-169">SceneComponents são as decomposiçãos mais granulares em SceneUnderstanding que representam uma única coisa principal, por exemplo, uma malha ou uma caixa delimitadora ou quádrupla.</span><span class="sxs-lookup"><span data-stu-id="24cd3-169">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="24cd3-170">SceneComponents são coisas que podem ser atualizadas de forma independente e podem ser referenciadas por outras SceneComponents, portanto, elas têm uma única propriedade global uma ID exclusiva, que permite esse tipo de mecanismo de controle/referência.</span><span class="sxs-lookup"><span data-stu-id="24cd3-170">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="24cd3-171">As IDs são usadas para a composição lógica da hierarquia de cena, bem como a persistência de objeto (o ato de atualizar uma cena em relação a outra).</span><span class="sxs-lookup"><span data-stu-id="24cd3-171">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="24cd3-172">Se você estiver tratando cada cena recém calculada como distinta e simplesmente enumerando todos os dados dentro dela, as IDs serão amplamente transparentes para você.</span><span class="sxs-lookup"><span data-stu-id="24cd3-172">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="24cd3-173">No entanto, se você estiver planejando rastrear componentes em várias atualizações, usará as IDs para indexar e localizar SceneComponents entre objetos de cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-173">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span></span>

#### <a name="sceneobjects"></a><span data-ttu-id="24cd3-174">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="24cd3-174">SceneObjects</span></span>

<span data-ttu-id="24cd3-175">Um Sceneobject é um SceneComponent que representa uma instância de uma "coisa", por exemplo, uma parede, um andar, um teto, etc... expresso por sua propriedade Kind.</span><span class="sxs-lookup"><span data-stu-id="24cd3-175">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span></span> <span data-ttu-id="24cd3-176">SceneObjects são geométricos e, portanto, têm funções e propriedades que representam sua localização no espaço, no entanto, elas não contêm nenhuma estrutura geométrica ou lógica.</span><span class="sxs-lookup"><span data-stu-id="24cd3-176">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="24cd3-177">Em vez disso, SceneObjects referenciam outros SceneComponents, especificamente SceneQuads e SceneMeshes, que fornecem as representações variadas que são suportadas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="24cd3-177">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="24cd3-178">Quando uma nova cena é computada, seu aplicativo provavelmente irá enumerar o SceneObjects da cena para processar o que está interessado.</span><span class="sxs-lookup"><span data-stu-id="24cd3-178">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="24cd3-179">SceneObjects pode ter qualquer um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="24cd3-179">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="24cd3-180">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="24cd3-180">SceneObjectKind</span></span></th> <th><span data-ttu-id="24cd3-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="24cd3-181">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="24cd3-182">Informações preliminares</span><span class="sxs-lookup"><span data-stu-id="24cd3-182">Background</span></span></td><td><span data-ttu-id="24cd3-183">O Sceneobject é conhecido como <b>não</b> um dos outros tipos reconhecidos de objeto de cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-183">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="24cd3-184">Essa classe não deve ser confundida quando o plano de fundo não for conhecido como parede/piso/teto, etc... Embora desconhecido ainda não esteja categorizado.</span><span class="sxs-lookup"><span data-stu-id="24cd3-184">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="24cd3-185">Meu</span><span class="sxs-lookup"><span data-stu-id="24cd3-185">Wall</span></span></td><td><span data-ttu-id="24cd3-186">Uma parede física.</span><span class="sxs-lookup"><span data-stu-id="24cd3-186">A physical wall.</span></span> <span data-ttu-id="24cd3-187">As paredes são presumidas como estruturas ambientais immovíveis.</span><span class="sxs-lookup"><span data-stu-id="24cd3-187">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="24cd3-188">Floor</span><span class="sxs-lookup"><span data-stu-id="24cd3-188">Floor</span></span></td><td><span data-ttu-id="24cd3-189">Os andares são quaisquer superfícies nas quais um pode ser movimentado.</span><span class="sxs-lookup"><span data-stu-id="24cd3-189">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="24cd3-190">Observação: escadas não são andares.</span><span class="sxs-lookup"><span data-stu-id="24cd3-190">Note: stairs are not floors.</span></span> <span data-ttu-id="24cd3-191">Observe também que os andares assumem qualquer superfície que seja orientada e, portanto, não há nenhuma suposição explícita de um piso singular.</span><span class="sxs-lookup"><span data-stu-id="24cd3-191">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span></span> <span data-ttu-id="24cd3-192">Estruturas de vários níveis, rampas, etc... todos devem ser classificados como piso.</span><span class="sxs-lookup"><span data-stu-id="24cd3-192">Multi-level structures, ramps etc... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="24cd3-193">Limite</span><span class="sxs-lookup"><span data-stu-id="24cd3-193">Ceiling</span></span></td><td><span data-ttu-id="24cd3-194">A superfície superior de uma sala.</span><span class="sxs-lookup"><span data-stu-id="24cd3-194">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="24cd3-195">Plataforma</span><span class="sxs-lookup"><span data-stu-id="24cd3-195">Platform</span></span></td><td><span data-ttu-id="24cd3-196">Uma grande superfície plana na qual você pode posicionar os hologramas.</span><span class="sxs-lookup"><span data-stu-id="24cd3-196">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="24cd3-197">Elas tendem a representar tabelas, Intertops e outras superfícies horizontais grandes.</span><span class="sxs-lookup"><span data-stu-id="24cd3-197">These tend to represent tables, countertops and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="24cd3-198">World</span><span class="sxs-lookup"><span data-stu-id="24cd3-198">World</span></span></td><td><span data-ttu-id="24cd3-199">Um rótulo reservado para dados geométricos que são independentes de rotulagem.</span><span class="sxs-lookup"><span data-stu-id="24cd3-199">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="24cd3-200">A malha gerada pela configuração do sinalizador de atualização EnableWorldMesh seria classificada como mundo.</span><span class="sxs-lookup"><span data-stu-id="24cd3-200">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="24cd3-201">Unknown</span><span class="sxs-lookup"><span data-stu-id="24cd3-201">Unknown</span></span></td><td><span data-ttu-id="24cd3-202">Este objeto de cena ainda deve ser classificado e atribuído a um tipo.</span><span class="sxs-lookup"><span data-stu-id="24cd3-202">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="24cd3-203">Isso não deve ser confundido com o plano de fundo, pois esse objeto pode ser qualquer coisa, o sistema simplesmente não surgiu com uma classificação suficientemente forte para ele.</span><span class="sxs-lookup"><span data-stu-id="24cd3-203">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

#### <a name="scenemesh"></a><span data-ttu-id="24cd3-204">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="24cd3-204">SceneMesh</span></span>

<span data-ttu-id="24cd3-205">Um SceneMesh é um SceneComponent que aproxima a geometria de objetos geométricos arbitrários usando uma lista de triângulos.</span><span class="sxs-lookup"><span data-stu-id="24cd3-205">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="24cd3-206">SceneMeshes são usados em vários contextos diferentes, eles podem representar componentes da estrutura de célula Watertight ou como WorldMesh, que representa a reconstrução de superfície não associada associada à cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-206">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded Surface Reconstruction associated with the Scene.</span></span> <span data-ttu-id="24cd3-207">Os dados de índice e vértice fornecidos com cada malha usam o mesmo layout familiar que os buffers de [vértice e de índice](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) usados para renderizar malhas de triângulo em todas as APIs de renderização modernas.</span><span class="sxs-lookup"><span data-stu-id="24cd3-207">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="24cd3-208">Observe que, na compreensão da cena, as malhas usam índices de 32 bits e talvez precisem ser divididas em partes para determinados mecanismos de renderização.</span><span class="sxs-lookup"><span data-stu-id="24cd3-208">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="scenequad"></a><span data-ttu-id="24cd3-209">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="24cd3-209">SceneQuad</span></span>

<span data-ttu-id="24cd3-210">Um SceneQuad é um SceneComponent que representa superfícies 2D que ocupam o mundo 3D.</span><span class="sxs-lookup"><span data-stu-id="24cd3-210">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="24cd3-211">SceneQuads pode ser usado de forma semelhante aos planos ARKit ARPlaneAnchor ou ARCore, mas eles oferecem funcionalidade de nível mais alto como telas 2D a serem usadas por aplicativos simples, ou UX aumentada.</span><span class="sxs-lookup"><span data-stu-id="24cd3-211">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="24cd3-212">as APIs específicas de 2D são fornecidas para quatro processadores que tornam o posicionamento e o layout simples de usar, e o desenvolvimento (com exceção de renderização) com quádruplos deve se sentir mais parecido com o trabalho com telas 2D do que com malhas 3D.</span><span class="sxs-lookup"><span data-stu-id="24cd3-212">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

### <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="24cd3-213">Detalhes do SDK de compreensão da cena e referência</span><span class="sxs-lookup"><span data-stu-id="24cd3-213">Scene Understanding SDK Details and Reference</span></span>

#### <a name="sdk"></a><span data-ttu-id="24cd3-214">SDK</span><span class="sxs-lookup"><span data-stu-id="24cd3-214">SDK</span></span>

<span data-ttu-id="24cd3-215">A seção a seguir ajudará você a se familiarizar com os conceitos básicos do SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="24cd3-215">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="24cd3-216">Esta seção deve fornecer as noções básicas, em que ponto você deve ter contexto suficiente para navegar pelos aplicativos de exemplo para ver como o SceneUnderstanding é usado de forma holística.</span><span class="sxs-lookup"><span data-stu-id="24cd3-216">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

#### <a name="initialization"></a><span data-ttu-id="24cd3-217">Inicialização</span><span class="sxs-lookup"><span data-stu-id="24cd3-217">Initialization</span></span>

<span data-ttu-id="24cd3-218">A primeira etapa para trabalhar com SceneUnderstanding é para seu aplicativo obter referência a um objeto de cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-218">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="24cd3-219">Isso pode ser feito de duas maneiras, uma cena pode ser computada pelo driver ou uma cena existente que foi computada no passado pode ser desserializada.</span><span class="sxs-lookup"><span data-stu-id="24cd3-219">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="24cd3-220">O último é particularmente útil para trabalhar com SceneUnderstanding durante o desenvolvimento, em que aplicativos e experiências podem ser protótipos rapidamente sem um dispositivo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="24cd3-220">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="24cd3-221">As cenas são computadas usando um SceneObserver.</span><span class="sxs-lookup"><span data-stu-id="24cd3-221">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="24cd3-222">Antes de criar uma cena, seu aplicativo deve consultar seu dispositivo para garantir que ele dê suporte a SceneUnderstanding, bem como solicitar acesso de usuário para obter informações de que o SceneUnderstanding precisa.</span><span class="sxs-lookup"><span data-stu-id="24cd3-222">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="24cd3-223">Se RequestAccessAsync () não for chamado, a computação de uma nova cena falhará.</span><span class="sxs-lookup"><span data-stu-id="24cd3-223">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="24cd3-224">Em seguida, computaremos uma nova cena com raiz em relação ao headset da realidade misturada e que tem um raio de 10 medidores.</span><span class="sxs-lookup"><span data-stu-id="24cd3-224">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.Compute(querySettings, 10.0f);
```

#### <a name="initialization-from-data-aka-the-pc-path"></a><span data-ttu-id="24cd3-225">Inicialização a partir de dados (também conhecido como.</span><span class="sxs-lookup"><span data-stu-id="24cd3-225">Initialization from Data (aka.</span></span> <span data-ttu-id="24cd3-226">o caminho do PC)</span><span class="sxs-lookup"><span data-stu-id="24cd3-226">the PC Path)</span></span>

<span data-ttu-id="24cd3-227">Embora as cenas possam ser computadas para consumo direto, elas também podem ser computadas em formato serializado para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="24cd3-227">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="24cd3-228">Isso provou ser muito útil para o desenvolvimento, pois permite que os desenvolvedores trabalhem e testem a compreensão da cena sem a necessidade de um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="24cd3-228">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="24cd3-229">O ato de serializar uma cena é quase idêntico a computar a ti, os dados são retornados ao seu aplicativo em vez de serem desserializados localmente pelo SDK.</span><span class="sxs-lookup"><span data-stu-id="24cd3-229">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="24cd3-230">Você pode desserializá-lo por conta própria ou salvá-lo para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="24cd3-230">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneUnderstanding.QuerySettings querySettings;

// Compute a scene but serialized as a byte array
byte[] newSceneBlob = SceneObserver.ComputeSerialized(querySettings, 10.0f);

// If we want to use it immediatley we can de-serialize the scene ourselves
Scene mySceneDeSerialized = Scene.Deserialize(newSceneBlob);

// Save newSceneBlob for later
```

#### <a name="sceneobject-enumeration"></a><span data-ttu-id="24cd3-231">Enumeração de sceneobject</span><span class="sxs-lookup"><span data-stu-id="24cd3-231">SceneObject Enumeration</span></span>

<span data-ttu-id="24cd3-232">Agora que seu aplicativo tem uma cena, seu aplicativo irá examinar e interagir com o SceneObjects.</span><span class="sxs-lookup"><span data-stu-id="24cd3-232">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="24cd3-233">Isso é feito acessando a propriedade **SceneObjects** :</span><span class="sxs-lookup"><span data-stu-id="24cd3-233">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

#### <a name="component-update-and-re-finding-components"></a><span data-ttu-id="24cd3-234">Atualização de componente e redescoberta de componentes</span><span class="sxs-lookup"><span data-stu-id="24cd3-234">Component update and re-finding components</span></span>

<span data-ttu-id="24cd3-235">Há outra função que recupera componentes na cena chamada ***FindComponent***.</span><span class="sxs-lookup"><span data-stu-id="24cd3-235">There is another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="24cd3-236">Essa função é útil ao atualizar objetos de acompanhamento e localizá-los em cenas subsequentes.</span><span class="sxs-lookup"><span data-stu-id="24cd3-236">This function is useful when updating tracking objects and finding them in subsequent scenes.</span></span> <span data-ttu-id="24cd3-237">O código a seguir calculará uma nova cena em relação a uma cena anterior e, em seguida, encontrará o andar na nova cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-237">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, but tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.Compute(querySettings, 10.0f, myScene);

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attatched to this floor transform
}
```

### <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="24cd3-238">Acessando malhas e quatros de objetos de cena</span><span class="sxs-lookup"><span data-stu-id="24cd3-238">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="24cd3-239">Depois que SceneObjects tiver sido localizado, o aplicativo provavelmente desejará acessar os dados contidos em n os quatro quádruplos/malhas dos quais ele é composto.</span><span class="sxs-lookup"><span data-stu-id="24cd3-239">Once SceneObjects have been found your application will most likely want to access the data that is contained n the quads/meshes that it is comprised of.</span></span> <span data-ttu-id="24cd3-240">Esses dados são acessados com as propriedades de quádruplas e de ***malhas*** .</span><span class="sxs-lookup"><span data-stu-id="24cd3-240">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span></span> <span data-ttu-id="24cd3-241">O código a seguir enumerará todos os quádruplos e malhas do nosso objeto Floor.</span><span class="sxs-lookup"><span data-stu-id="24cd3-241">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the matrix for the SceneObject
System.Numerics.Matrix4x4 floorTransform = firstFloor.LocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="24cd3-242">Observe que é o Sceneobject que tem a transformação relativa à origem da cena.</span><span class="sxs-lookup"><span data-stu-id="24cd3-242">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="24cd3-243">Isso ocorre porque o Sceneobject representa uma instância de "coisa" e é localizável no espaço, as quádruplas e as malhas representam a geometria transformada em relação ao seu pai.</span><span class="sxs-lookup"><span data-stu-id="24cd3-243">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="24cd3-244">É possível que SceneObjects separadas referenciem o mesmo SceneMesh/SceneQuad SceneComponewnts, e também é possível que um Sceneobject tenha mais de um SceneMesh/SceneQuad.</span><span class="sxs-lookup"><span data-stu-id="24cd3-244">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponewnts, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="24cd3-245">Lidando com transformações</span><span class="sxs-lookup"><span data-stu-id="24cd3-245">Dealing with Transforms</span></span>

<span data-ttu-id="24cd3-246">A compreensão da cena fez uma tentativa deliberada de se alinhar com as representações tradicionais de cena 3D ao lidar com transformações.</span><span class="sxs-lookup"><span data-stu-id="24cd3-246">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="24cd3-247">Portanto, cada cena é confinada a um único sistema de coordenadas, assim como as representações de ambiente 3D mais comuns.</span><span class="sxs-lookup"><span data-stu-id="24cd3-247">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="24cd3-248">Se seu aplicativo estiver lidando com cenas que ampliam o limite do que uma única origem fornece, ela pode ancorar SceneObjects para SpatialAnchors ou gerar várias cenas e mesclá-las, mas para simplificar, vamos supor que as cenas de Watertight existam por conta própria origem localizada por um NodeId definido por Scene:: OriginSpatialGraphNodeId.</span><span class="sxs-lookup"><span data-stu-id="24cd3-248">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene::OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="24cd3-249">O seguinte código de Unity, por exemplo, mostra como usar a percepção do Windows e as APIs do Unity para alinhar os sistemas de coordenadas em conjunto:</span><span class="sxs-lookup"><span data-stu-id="24cd3-249">The following unity code, for example, shows how to use windows perception and Unity APIs to align coordinate systems together:</span></span>


```cs
    public static System.Numerics.Matrix4x4? GetSceneToUnityTransform(Guid nodeId)
    {
        System.Numerics.Matrix4x4? sceneToUnityTransform; 
       
        SpatialCoordinateSystem sceneSpatialCoordinateSystem = Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(nodeId);
        SpatialCoordinateSystem unitySpatialCoordinateSystem = (SpatialCoordinateSystem)System.Runtime.InteropServices.Marshal.GetObjectForIUnknown(UnityEngine.XR.WSA.WorldManager.GetNativeISpatialCoordinateSystemPtr());

        sceneToUnityTransform = sceneSpatialCoordinateSystem.TryGetTransformTo(unitySpatialCoordinateSystem);

        if (sceneToUnityTransform != null)
        {
            sceneToUnityTransform = TransformUtils.ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
        }
        
        return sceneToUnityTransform;
    }

    /// <summary>
    /// Converts a transformation matrix from right handed (+x is right, +y is up, +z is back) to left handed (+x is right, +y is up, +z is front).
    /// </summary>
    /// <param name="transformationMatrix">Right-handed transformation matrix to convert.</param>
    /// <returns>Converted left-handed matrix.</returns>
    public System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 transformationMatrix)
    {
        transformationMatrix.M13 = -transformationMatrix.M13;
        transformationMatrix.M23 = -transformationMatrix.M23;
        transformationMatrix.M43 = -transformationMatrix.M43;

        transformationMatrix.M31 = -transformationMatrix.M31;
        transformationMatrix.M32 = -transformationMatrix.M32;
        transformationMatrix.M34 = -transformationMatrix.M34;

        return transformationMatrix;
    }
```

<span data-ttu-id="24cd3-250">E o código a seguir chama essa função:</span><span class="sxs-lookup"><span data-stu-id="24cd3-250">And the following code calls this function:</span></span>

```cs
System.Numerics.Matrix4x4? sceneToUnityTransform = TransformUtils.GetSceneToUnityTransform(scene.OriginSpatialGraphNodeId);

// Set the root transform
Vector3 t;
Quaternion r;
Vector3 s;

System.Numerics.Matrix4x4.Decompose(sceneToUnityTransform, out s, out r, out t);
SceneRoot.Transform.SetPositionAndRotation(t, r);
```

### <a name="quad"></a><span data-ttu-id="24cd3-251">Quadra</span><span class="sxs-lookup"><span data-stu-id="24cd3-251">Quad</span></span>

<span data-ttu-id="24cd3-252">Os quatro processadores foram projetados para facilitar os cenários de posicionamento de 2D e devem ser considerados como extensões para elementos de UX de tela 2D.</span><span class="sxs-lookup"><span data-stu-id="24cd3-252">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="24cd3-253">Embora os quatro processadores sejam componentes de SceneObjects e possam ser renderizados em 3D, as APIs quádruplas em si pressupõem que as quatro são estruturas 2D.</span><span class="sxs-lookup"><span data-stu-id="24cd3-253">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="24cd3-254">Eles oferecem informações como extensão, forma e fornecem APIs para posicionamento.</span><span class="sxs-lookup"><span data-stu-id="24cd3-254">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="24cd3-255">Os quatro processadores têm extensões retangulares, mas representam superfícies 2D com formato arbitrário.</span><span class="sxs-lookup"><span data-stu-id="24cd3-255">Quads have rectangular extents, but they represent arbitrarily shaped 2d surfaces.</span></span> <span data-ttu-id="24cd3-256">Para habilitar o posicionamento nessas superfícies 2D que interagem com o ambiente 3D, as quatro ofertas oferecem utilitários para tornar essa interação possível.</span><span class="sxs-lookup"><span data-stu-id="24cd3-256">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="24cd3-257">Atualmente, a compreensão da cena fornece duas funções desse tipo, **FindCentermostPlacement** e **GetOcclusionMask**.</span><span class="sxs-lookup"><span data-stu-id="24cd3-257">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask**.</span></span> <span data-ttu-id="24cd3-258">FindCentermostPlacement é uma API de alto nível que localiza uma posição no Quad em que um objeto pode ser colocado e tentará encontrar o melhor local para seu objeto, garantindo que a caixa delimitadora que você fornece residirá na superfície subjacente.</span><span class="sxs-lookup"><span data-stu-id="24cd3-258">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span></span>

<span data-ttu-id="24cd3-259">O exemplo a seguir mostra como localizar o local centermost posicionável e ancorar um holograma para o quad.</span><span class="sxs-lookup"><span data-stu-id="24cd3-259">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new node QuadTransformNode as a child of Root, and set the transform from quad[0].Transform
                // Step 2: Create your hologram and set it as a child of QuadTransformNode
                // Step 3: Set the QuadTransformNode tranform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="24cd3-260">As etapas 1-3 são altamente dependentes de sua estrutura/implementação específica, mas os temas devem ser semelhantes.</span><span class="sxs-lookup"><span data-stu-id="24cd3-260">Steps 1-3 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="24cd3-261">É importante observar que o quad normalmente não se destina a ser, representa apenas um plano 2D limitado que é localizado no espaço.</span><span class="sxs-lookup"><span data-stu-id="24cd3-261">It is important to note that the Quad is not usually intended to be, is just represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="24cd3-262">Tendo seu mecanismo/estrutura sabendo onde o Quad é e criando a raiz de seus objetos em relação ao Quad, seus hologramas estarão localizados corretamente.</span><span class="sxs-lookup"><span data-stu-id="24cd3-262">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly.</span></span> <span data-ttu-id="24cd3-263">Para obter informações mais detalhadas, consulte nossos exemplos em quatro processadores que mostram implementações específicas.</span><span class="sxs-lookup"><span data-stu-id="24cd3-263">For more detailed information please see our samples on quads which show specific implementations.</span></span>

### <a name="mesh"></a><span data-ttu-id="24cd3-264">Integrada</span><span class="sxs-lookup"><span data-stu-id="24cd3-264">Mesh</span></span>

<span data-ttu-id="24cd3-265">As malhas representam representações geométricas de objetos ou ambientes.</span><span class="sxs-lookup"><span data-stu-id="24cd3-265">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="24cd3-266">Assim como o [mapeamento espacial](spatial-mapping.md), o índice de malha e os dados de vértice fornecidos com cada malha de superfície espacial usam o mesmo layout familiar que os buffers de vértice e de índice usados para renderizar malhas de triângulo em todas as APIs de renderização modernas.</span><span class="sxs-lookup"><span data-stu-id="24cd3-266">Much like [spatial mapping](spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="24cd3-267">As APIs específicas usadas para fazer referência a esses dados são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="24cd3-267">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(float[] vertices);
```

<span data-ttu-id="24cd3-268">\* \* Observação: Getvértices retorna uma lista de vértices onde cada 3 tupla de valores de ponto flutuante representa uma única coordenada em espaço cartesiano x, y e z.</span><span class="sxs-lookup"><span data-stu-id="24cd3-268">\*\*Note: GetVertices returns a list of vertices where every 3-tuple of floating point values represents a single coordinate in cartesian x,y and z space.</span></span>

<span data-ttu-id="24cd3-269">O código a seguir fornece um exemplo de como gerar uma lista de triângulos a partir da estrutura de malha:</span><span class="sxs-lookup"><span data-stu-id="24cd3-269">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
float[] positions = new float[mesh.VertexCount * 3];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="24cd3-270">Os buffers de índice/vértice devem ser > = as contagens de índice/vértice, mas, caso contrário, podem ser arbitrariamente dimensionados permitindo uma reutilização de memória eficiente.</span><span class="sxs-lookup"><span data-stu-id="24cd3-270">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span></span>

### <a name="developing-with-scene-understandings"></a><span data-ttu-id="24cd3-271">Desenvolvendo com entendimentos em cena</span><span class="sxs-lookup"><span data-stu-id="24cd3-271">Developing with Scene Understandings</span></span>

<span data-ttu-id="24cd3-272">Neste ponto, você deve entender os principais blocos de construção da cena que compreendem o tempo de execução e o SDK.</span><span class="sxs-lookup"><span data-stu-id="24cd3-272">At this point you should understand the core building blocks of the Scene Understanding runtime and SDK.</span></span> <span data-ttu-id="24cd3-273">A maior parte do poder e da complexidade está em padrões de acesso, interação com estruturas 3D e ferramentas que podem ser escritas sobre essas APIs para executar tarefas mais avançadas como planejamento espacial, análise de sala, navegação, física, etc... Esperamos capturá-los em exemplos que esperamos orientá-lo na direção correta para fazer seus cenários brilharem.</span><span class="sxs-lookup"><span data-stu-id="24cd3-273">The bulk of the power and complexity lies in access patterns, interaction with 3d frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc... We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="24cd3-274">Se houver amostras/cenários que não estão sendo abordados, informe-nos e tentaremos documentar/criar um protótipo do que você precisa.</span><span class="sxs-lookup"><span data-stu-id="24cd3-274">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="24cd3-275">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24cd3-275">See also</span></span>

* [<span data-ttu-id="24cd3-276">mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="24cd3-276">spatial mapping</span></span>](spatial-mapping.md)
