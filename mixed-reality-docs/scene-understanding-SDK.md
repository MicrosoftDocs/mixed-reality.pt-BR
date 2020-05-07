---
title: SDK de compreensão da cena
description: Guia de programação para o SDK de compreensão da cena
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Compreensão da cena, mapeamento espacial, realidade do Windows Mixed, Unity
ms.openlocfilehash: 3eb54f84e30b2354907204895e62accdb9ad54f9
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604947"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="8f52b-104">Visão geral do SDK de compreensão da cena</span><span class="sxs-lookup"><span data-stu-id="8f52b-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="8f52b-105">A meta da compreensão da cena é transformar os dados do sensor de ambiente não estruturado que o dispositivo da realidade misturada captura e convertê-lo em uma representação avançada, mas abstrata, intuitiva e fácil de desenvolver para o.</span><span class="sxs-lookup"><span data-stu-id="8f52b-105">The goal of Scene understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span></span> <span data-ttu-id="8f52b-106">O SDK atua como a camada de comunicação entre seu aplicativo e o tempo de execução de compreensão da cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="8f52b-107">Ele é destinado a imitar construções padrão existentes, como grafos de cena 3D para representações 3D e retângulos 2D e painéis para aplicativos 2D.</span><span class="sxs-lookup"><span data-stu-id="8f52b-107">It's aimed to mimic existing standard constructs such as 3D scene graphs for 3D representations and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="8f52b-108">Embora as construções que compreendem as imitações da cena sejam mapeadas para as estruturas concretas que você pode usar, em geral SceneUnderstanding é a estrutura independente, permitindo a interoperabilidade entre estruturas variadas que interagem com ela.</span><span class="sxs-lookup"><span data-stu-id="8f52b-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span></span> <span data-ttu-id="8f52b-109">Conforme a compreensão da cena desenvolve a função do SDK, para garantir que novas representações e funcionalidades continuem a ser expostas em uma estrutura unificada.</span><span class="sxs-lookup"><span data-stu-id="8f52b-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="8f52b-110">Neste documento, primeiro apresentaremos conceitos de alto nível que ajudarão você a se familiarizar com o uso/ambiente de desenvolvimento e, em seguida, fornecer uma documentação mais detalhada para classes e construções específicas.</span><span class="sxs-lookup"><span data-stu-id="8f52b-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="8f52b-111">Onde obtenho o SDK?</span><span class="sxs-lookup"><span data-stu-id="8f52b-111">Where do I get the SDK?</span></span>

<span data-ttu-id="8f52b-112">O SDK do SceneUnderstanding é baixável via NuGet.</span><span class="sxs-lookup"><span data-stu-id="8f52b-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="8f52b-113">SDK do SceneUnderstanding</span><span class="sxs-lookup"><span data-stu-id="8f52b-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="8f52b-114">**Observação:** a versão mais recente depende dos pacotes de visualização e você precisará habilitar os pacotes de pré-lançamento para vê-lo.</span><span class="sxs-lookup"><span data-stu-id="8f52b-114">**Note:** the latest release depends on preview packages and you will need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="8f52b-115">A partir da versão 0.5.2022-RC, o entendimento da cena dá suporte a projeções de linguagem para C# e C++, permitindo que os aplicativos desenvolvam aplicativos para plataformas Win32 ou UWP.</span><span class="sxs-lookup"><span data-stu-id="8f52b-115">As of version 0.5.2022-rc, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="8f52b-116">A partir dessa versão, SceneUnderstanding dá suporte ao suporte do Unity no editor para o bloqueio do SceneObserver, que é usado exclusivamente para comunicação com o HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="8f52b-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="8f52b-117">O SceneUnderstanding requer SDK do Windows versão 18362 ou superior.</span><span class="sxs-lookup"><span data-stu-id="8f52b-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="8f52b-118">Se você estiver usando o SDK em um projeto do Unity, use o [NuGet para o Unity](https://github.com/GlitchEnzo/NuGetForUnity) para instalar o pacote em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="8f52b-118">If you are using the SDK in a Unity project, please use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="8f52b-119">Visão geral conceitual</span><span class="sxs-lookup"><span data-stu-id="8f52b-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="8f52b-120">A cena</span><span class="sxs-lookup"><span data-stu-id="8f52b-120">The Scene</span></span>

<span data-ttu-id="8f52b-121">Seu dispositivo de realidade misturada está constantemente integrando informações sobre o que vê em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="8f52b-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="8f52b-122">A compreensão da cena funil todas essas fontes de dados e produz uma única abstração coesa.</span><span class="sxs-lookup"><span data-stu-id="8f52b-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="8f52b-123">A compreensão da cena gera cenas que são uma composição de [SceneObjects](scene-understanding-SDK.md#sceneobjects) que representam uma instância de uma única coisa (por exemplo, uma parede/teto/andar). Os próprios objetos de cena são uma composição de [SceneComponents](scene-understanding-SDK.md#scenecomponents) que representam partes mais granulares que compõem esse sceneobject.</span><span class="sxs-lookup"><span data-stu-id="8f52b-123">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="8f52b-124">Exemplos de componentes são quádruplos e malhas, mas no futuro podem representar caixas delimitadoras, malhas de colisão, metadados, etc...</span><span class="sxs-lookup"><span data-stu-id="8f52b-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc...</span></span>

<span data-ttu-id="8f52b-125">O processo de converter os dados brutos do sensor em uma cena é uma operação potencialmente cara que pode levar segundos para espaços médios (~ 10x10m) a minutos para espaços muito grandes (~ 50x50m) e, portanto, não é algo que está sendo computado pelo dispositivo sem solicitação de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f52b-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="8f52b-126">Em vez disso, a geração de cena é disparada por seu aplicativo sob demanda.</span><span class="sxs-lookup"><span data-stu-id="8f52b-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="8f52b-127">A classe SceneObserver tem métodos estáticos que podem calcular ou desserializar uma cena, com a qual você pode enumerar/interagir.</span><span class="sxs-lookup"><span data-stu-id="8f52b-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="8f52b-128">A ação de "computação" é executada sob demanda e é executada na CPU, mas em um processo separado (o driver de realidade misturada).</span><span class="sxs-lookup"><span data-stu-id="8f52b-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="8f52b-129">No entanto, enquanto fazemos a computação em outro processo, os dados de cena resultantes são armazenados e mantidos em seu aplicativo no objeto de cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="8f52b-130">Veja abaixo um diagrama que ilustra esse fluxo de processo e mostra exemplos de dois aplicativos que se destinam ao tempo de execução de compreensão da cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Diagrama de processo](images/SU-ProcessFlow.png)

<span data-ttu-id="8f52b-132">No lado esquerdo, há um diagrama do tempo de execução misto da realidade que está sempre ligado e em execução em seu próprio processo.</span><span class="sxs-lookup"><span data-stu-id="8f52b-132">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span></span> <span data-ttu-id="8f52b-133">Esse tempo de execução é responsável por executar o rastreamento de dispositivos, o mapeamento espacial e outras operações que a cena entende para entender e o motivo do mundo em torno de você.</span><span class="sxs-lookup"><span data-stu-id="8f52b-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="8f52b-134">No lado direito do diagrama, mostramos dois aplicativos teóricos que fazem uso da compreensão da cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="8f52b-135">As primeiras interfaces de aplicativo com MRTK que usam o SDK de compreensão da cena internamente, o segundo aplicativo computa e usa duas instâncias de cena separadas.</span><span class="sxs-lookup"><span data-stu-id="8f52b-135">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="8f52b-136">Todos os 3 bastidores neste diagrama geram instâncias distintas dos bastidores, o driver não está acompanhando o estado global que é compartilhado entre aplicativos e objetos de cena em uma cena não é encontrado em outro.</span><span class="sxs-lookup"><span data-stu-id="8f52b-136">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span></span> <span data-ttu-id="8f52b-137">A compreensão da cena fornece um mecanismo para controlar ao longo do tempo, mas isso é feito usando o SDK e o código que executa esse controle é executado no SDK no processo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f52b-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and the code that performs this tracking is running in the SDK in your app's process.</span></span>

<span data-ttu-id="8f52b-138">Como cada cena armazena os dados no espaço de memória do seu aplicativo, você pode pressupor que toda a função do objeto de cena ou de seus dados internos sempre seja executada no processo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f52b-138">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="8f52b-139">Layout</span><span class="sxs-lookup"><span data-stu-id="8f52b-139">Layout</span></span>

<span data-ttu-id="8f52b-140">Para trabalhar com a compreensão da cena, pode ser importante saber e entender como o tempo de execução representa os componentes logicamente e fisicamente.</span><span class="sxs-lookup"><span data-stu-id="8f52b-140">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="8f52b-141">A cena representa dados com um layout específico que foi escolhido para ser simples enquanto mantém uma estrutura subjacente que é pliable para atender aos requisitos futuros sem precisar de revisões principais.</span><span class="sxs-lookup"><span data-stu-id="8f52b-141">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="8f52b-142">A cena faz isso armazenando todos os componentes (blocos de construção para todos os objetos de cena) em uma lista simples e definindo a hierarquia e a composição por meio de referências em que componentes específicos fazem referência a outros.</span><span class="sxs-lookup"><span data-stu-id="8f52b-142">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="8f52b-143">Abaixo, apresentamos um exemplo de uma estrutura em sua forma fixa e lógica.</span><span class="sxs-lookup"><span data-stu-id="8f52b-143">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="8f52b-144">Layout lógico</span><span class="sxs-lookup"><span data-stu-id="8f52b-144">Logical Layout</span></span></th><th><span data-ttu-id="8f52b-145">Layout Físico</span><span class="sxs-lookup"><span data-stu-id="8f52b-145">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="8f52b-146">Cena</span><span class="sxs-lookup"><span data-stu-id="8f52b-146">Scene</span></span>
  <ul>
  <li><span data-ttu-id="8f52b-147">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="8f52b-147">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="8f52b-148">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="8f52b-148">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="8f52b-149">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="8f52b-149">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="8f52b-150">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="8f52b-150">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="8f52b-151">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="8f52b-151">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="8f52b-152">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="8f52b-152">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="8f52b-153">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="8f52b-153">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="8f52b-154">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="8f52b-154">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="8f52b-155">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="8f52b-155">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="8f52b-156">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="8f52b-156">SceneObject_1</span></span></li>
  <li><span data-ttu-id="8f52b-157">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="8f52b-157">SceneObject_2</span></span></li>
  <li><span data-ttu-id="8f52b-158">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="8f52b-158">SceneObject_3</span></span></li>
  <li><span data-ttu-id="8f52b-159">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="8f52b-159">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="8f52b-160">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="8f52b-160">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="8f52b-161">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="8f52b-161">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="8f52b-162">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="8f52b-162">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="8f52b-163">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="8f52b-163">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="8f52b-164">Esta ilustração realça a diferença entre o layout lógico e físico da cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-164">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="8f52b-165">À esquerda, vemos o layout hierárquico dos dados que seu aplicativo vê ao enumerar a cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-165">On the left we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="8f52b-166">À direita, vemos que a cena é, na verdade, composta de 12 componentes distintos acessíveis individualmente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="8f52b-166">On the right we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="8f52b-167">Ao processar uma nova cena, esperamos que os aplicativos orientem essa hierarquia logicamente, no entanto, ao controlar entre as atualizações de cena, alguns aplicativos só podem estar interessados em direcionar componentes específicos que são compartilhados entre duas cenas.</span><span class="sxs-lookup"><span data-stu-id="8f52b-167">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="8f52b-168">Visão geral da API</span><span class="sxs-lookup"><span data-stu-id="8f52b-168">API overview</span></span>

<span data-ttu-id="8f52b-169">A seção a seguir fornece uma visão geral de alto nível das construções na compreensão da cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-169">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="8f52b-170">A leitura desta seção lhe dará uma compreensão de como as cenas são representadas e de quais os vários componentes do/são usados.</span><span class="sxs-lookup"><span data-stu-id="8f52b-170">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="8f52b-171">A próxima seção fornecerá exemplos de código concretos e detalhes adicionais que são brilhantes nesta visão geral.</span><span class="sxs-lookup"><span data-stu-id="8f52b-171">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="8f52b-172">Todos os tipos descritos abaixo residem no `Microsoft.MixedReality.SceneUnderstanding` namespace.</span><span class="sxs-lookup"><span data-stu-id="8f52b-172">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="8f52b-173">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="8f52b-173">SceneComponents</span></span>

<span data-ttu-id="8f52b-174">Agora que você entende o layout lógico de cenas, agora podemos apresentar o conceito de SceneComponents e como eles são usados para compor a hierarquia.</span><span class="sxs-lookup"><span data-stu-id="8f52b-174">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span></span> <span data-ttu-id="8f52b-175">SceneComponents são as decomposiçãos mais granulares em SceneUnderstanding que representam uma única coisa principal, por exemplo, uma malha ou uma caixa delimitadora ou quádrupla.</span><span class="sxs-lookup"><span data-stu-id="8f52b-175">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="8f52b-176">SceneComponents são coisas que podem ser atualizadas de forma independente e podem ser referenciadas por outras SceneComponents, portanto, elas têm uma única propriedade global uma ID exclusiva, que permite esse tipo de mecanismo de controle/referência.</span><span class="sxs-lookup"><span data-stu-id="8f52b-176">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="8f52b-177">As IDs são usadas para a composição lógica da hierarquia de cena, bem como a persistência de objeto (o ato de atualizar uma cena em relação a outra).</span><span class="sxs-lookup"><span data-stu-id="8f52b-177">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="8f52b-178">Se você estiver tratando cada cena recém calculada como distinta e simplesmente enumerando todos os dados dentro dela, as IDs serão amplamente transparentes para você.</span><span class="sxs-lookup"><span data-stu-id="8f52b-178">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="8f52b-179">No entanto, se você estiver planejando rastrear componentes em várias atualizações, usará as IDs para indexar e localizar SceneComponents entre objetos de cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-179">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="8f52b-180">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="8f52b-180">SceneObjects</span></span>

<span data-ttu-id="8f52b-181">Um Sceneobject é um SceneComponent que representa uma instância de uma "coisa", por exemplo, uma parede, um andar, um teto, etc... expresso por sua propriedade Kind.</span><span class="sxs-lookup"><span data-stu-id="8f52b-181">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span></span> <span data-ttu-id="8f52b-182">SceneObjects são geométricos e, portanto, têm funções e propriedades que representam sua localização no espaço, no entanto, elas não contêm nenhuma estrutura geométrica ou lógica.</span><span class="sxs-lookup"><span data-stu-id="8f52b-182">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="8f52b-183">Em vez disso, SceneObjects referenciam outros SceneComponents, especificamente SceneQuads e SceneMeshes, que fornecem as representações variadas que são suportadas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="8f52b-183">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="8f52b-184">Quando uma nova cena é computada, seu aplicativo provavelmente irá enumerar o SceneObjects da cena para processar o que está interessado.</span><span class="sxs-lookup"><span data-stu-id="8f52b-184">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="8f52b-185">SceneObjects pode ter qualquer um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="8f52b-185">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="8f52b-186">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="8f52b-186">SceneObjectKind</span></span></th> <th><span data-ttu-id="8f52b-187">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f52b-187">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="8f52b-188">Segundo plano</span><span class="sxs-lookup"><span data-stu-id="8f52b-188">Background</span></span></td><td><span data-ttu-id="8f52b-189">O Sceneobject é conhecido como <b>não</b> um dos outros tipos reconhecidos de objeto de cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-189">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="8f52b-190">Essa classe não deve ser confundida quando o plano de fundo não for conhecido como parede/piso/teto, etc... Embora desconhecido ainda não esteja categorizado.</span><span class="sxs-lookup"><span data-stu-id="8f52b-190">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="8f52b-191">Meu</span><span class="sxs-lookup"><span data-stu-id="8f52b-191">Wall</span></span></td><td><span data-ttu-id="8f52b-192">Uma parede física.</span><span class="sxs-lookup"><span data-stu-id="8f52b-192">A physical wall.</span></span> <span data-ttu-id="8f52b-193">As paredes são presumidas como estruturas ambientais immovíveis.</span><span class="sxs-lookup"><span data-stu-id="8f52b-193">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="8f52b-194">Piso</span><span class="sxs-lookup"><span data-stu-id="8f52b-194">Floor</span></span></td><td><span data-ttu-id="8f52b-195">Os andares são quaisquer superfícies nas quais um pode ser movimentado.</span><span class="sxs-lookup"><span data-stu-id="8f52b-195">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="8f52b-196">Observação: escadas não são andares.</span><span class="sxs-lookup"><span data-stu-id="8f52b-196">Note: stairs are not floors.</span></span> <span data-ttu-id="8f52b-197">Observe também que os andares assumem qualquer superfície que seja orientada e, portanto, não há nenhuma suposição explícita de um piso singular.</span><span class="sxs-lookup"><span data-stu-id="8f52b-197">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span></span> <span data-ttu-id="8f52b-198">Estruturas de vários níveis, rampas, etc... todos devem ser classificados como piso.</span><span class="sxs-lookup"><span data-stu-id="8f52b-198">Multi-level structures, ramps etc... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="8f52b-199">Ceiling</span><span class="sxs-lookup"><span data-stu-id="8f52b-199">Ceiling</span></span></td><td><span data-ttu-id="8f52b-200">A superfície superior de uma sala.</span><span class="sxs-lookup"><span data-stu-id="8f52b-200">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="8f52b-201">Plataforma</span><span class="sxs-lookup"><span data-stu-id="8f52b-201">Platform</span></span></td><td><span data-ttu-id="8f52b-202">Uma grande superfície plana na qual você pode posicionar os hologramas.</span><span class="sxs-lookup"><span data-stu-id="8f52b-202">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="8f52b-203">Elas tendem a representar tabelas, Intertops e outras superfícies horizontais grandes.</span><span class="sxs-lookup"><span data-stu-id="8f52b-203">These tend to represent tables, countertops and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="8f52b-204">Mundo</span><span class="sxs-lookup"><span data-stu-id="8f52b-204">World</span></span></td><td><span data-ttu-id="8f52b-205">Um rótulo reservado para dados geométricos que são independentes de rotulagem.</span><span class="sxs-lookup"><span data-stu-id="8f52b-205">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="8f52b-206">A malha gerada pela configuração do sinalizador de atualização EnableWorldMesh seria classificada como mundo.</span><span class="sxs-lookup"><span data-stu-id="8f52b-206">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="8f52b-207">Unknown</span><span class="sxs-lookup"><span data-stu-id="8f52b-207">Unknown</span></span></td><td><span data-ttu-id="8f52b-208">Este objeto de cena ainda deve ser classificado e atribuído a um tipo.</span><span class="sxs-lookup"><span data-stu-id="8f52b-208">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="8f52b-209">Isso não deve ser confundido com o plano de fundo, pois esse objeto pode ser qualquer coisa, o sistema simplesmente não surgiu com uma classificação suficientemente forte para ele.</span><span class="sxs-lookup"><span data-stu-id="8f52b-209">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="8f52b-210">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="8f52b-210">SceneMesh</span></span>

<span data-ttu-id="8f52b-211">Um SceneMesh é um SceneComponent que aproxima a geometria de objetos geométricos arbitrários usando uma lista de triângulos.</span><span class="sxs-lookup"><span data-stu-id="8f52b-211">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="8f52b-212">SceneMeshes são usados em vários contextos diferentes, eles podem representar componentes da estrutura de célula Watertight ou como WorldMesh, que representa a malha de mapeamento espacial não associado associada à cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-212">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="8f52b-213">Os dados de índice e vértice fornecidos com cada malha usam o mesmo layout familiar que os [buffers de vértice e de índice](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) usados para renderizar malhas de triângulo em todas as APIs de renderização modernas.</span><span class="sxs-lookup"><span data-stu-id="8f52b-213">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="8f52b-214">Observe que, na compreensão da cena, as malhas usam índices de 32 bits e talvez precisem ser divididas em partes para determinados mecanismos de renderização.</span><span class="sxs-lookup"><span data-stu-id="8f52b-214">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="8f52b-215">Sistemas de ordem e coordenação de enrolamento</span><span class="sxs-lookup"><span data-stu-id="8f52b-215">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="8f52b-216">Todas as malhas produzidas pela compreensão da cena devem retornar malhas em um sistema de coordenadas à direita usando a ordem de enrolamento no sentido horário.</span><span class="sxs-lookup"><span data-stu-id="8f52b-216">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="8f52b-217">Observação: OS Builds do sistema operacional anteriores a. 191105 podem ter um bug conhecido em que as malhas "mundo" estavam retornando na ordem de enrolamento no sentido anti-horário, que, subsequentemente, foi corrigida.</span><span class="sxs-lookup"><span data-stu-id="8f52b-217">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="8f52b-218">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="8f52b-218">SceneQuad</span></span>

<span data-ttu-id="8f52b-219">Um SceneQuad é um SceneComponent que representa superfícies 2D que ocupam o mundo 3D.</span><span class="sxs-lookup"><span data-stu-id="8f52b-219">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="8f52b-220">SceneQuads pode ser usado de forma semelhante aos planos ARKit ARPlaneAnchor ou ARCore, mas eles oferecem funcionalidade de nível mais alto como telas 2D a serem usadas por aplicativos simples, ou UX aumentada.</span><span class="sxs-lookup"><span data-stu-id="8f52b-220">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="8f52b-221">as APIs específicas de 2D são fornecidas para quatro processadores que tornam o posicionamento e o layout simples de usar, e o desenvolvimento (com exceção de renderização) com quádruplos deve se sentir mais parecido com o trabalho com telas 2D do que com malhas 3D.</span><span class="sxs-lookup"><span data-stu-id="8f52b-221">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="8f52b-222">Forma SceneQuad</span><span class="sxs-lookup"><span data-stu-id="8f52b-222">SceneQuad shape</span></span>

<span data-ttu-id="8f52b-223">SceneQuads definir uma superfície retangular limitada em 2D.</span><span class="sxs-lookup"><span data-stu-id="8f52b-223">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="8f52b-224">No entanto, SceneQuads estão representando superfícies com formas arbitrárias e potencialmente complexas (por exemplo, uma tabela com formato de rosca.) Para representar a forma complexa da superfície de um quádruplo, você pode usar a API GetSurfaceMask para renderizar a forma da superfície em um buffer de imagem que você fornece.</span><span class="sxs-lookup"><span data-stu-id="8f52b-224">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="8f52b-225">Se o Sceneobject que tem o quad também tiver uma malha, os triângulos de malha devem ser equivalentes a essa imagem renderizada, ambos representam a geometria real da superfície, apenas em coordenadas 2D ou 3D.</span><span class="sxs-lookup"><span data-stu-id="8f52b-225">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, just either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="8f52b-226">Detalhes do SDK de compreensão da cena e referência</span><span class="sxs-lookup"><span data-stu-id="8f52b-226">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="8f52b-227">A seção a seguir ajudará você a se familiarizar com os conceitos básicos do SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="8f52b-227">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="8f52b-228">Esta seção deve fornecer as noções básicas, em que ponto você deve ter contexto suficiente para navegar pelos aplicativos de exemplo para ver como o SceneUnderstanding é usado de forma holística.</span><span class="sxs-lookup"><span data-stu-id="8f52b-228">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="8f52b-229">Inicialização</span><span class="sxs-lookup"><span data-stu-id="8f52b-229">Initialization</span></span>

<span data-ttu-id="8f52b-230">A primeira etapa para trabalhar com SceneUnderstanding é para seu aplicativo obter referência a um objeto de cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-230">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="8f52b-231">Isso pode ser feito de duas maneiras, uma cena pode ser computada pelo driver ou uma cena existente que foi computada no passado pode ser desserializada.</span><span class="sxs-lookup"><span data-stu-id="8f52b-231">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="8f52b-232">O último é particularmente útil para trabalhar com SceneUnderstanding durante o desenvolvimento, em que aplicativos e experiências podem ser protótipos rapidamente sem um dispositivo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="8f52b-232">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="8f52b-233">As cenas são computadas usando um SceneObserver.</span><span class="sxs-lookup"><span data-stu-id="8f52b-233">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="8f52b-234">Antes de criar uma cena, seu aplicativo deve consultar seu dispositivo para garantir que ele dê suporte a SceneUnderstanding, bem como solicitar acesso de usuário para obter informações de que o SceneUnderstanding precisa.</span><span class="sxs-lookup"><span data-stu-id="8f52b-234">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="8f52b-235">Se RequestAccessAsync () não for chamado, a computação de uma nova cena falhará.</span><span class="sxs-lookup"><span data-stu-id="8f52b-235">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="8f52b-236">Em seguida, computaremos uma nova cena com raiz em relação ao headset da realidade misturada e que tem um raio de 10 medidores.</span><span class="sxs-lookup"><span data-stu-id="8f52b-236">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-aka-the-pc-path"></a><span data-ttu-id="8f52b-237">Inicialização a partir de dados (também conhecido como.</span><span class="sxs-lookup"><span data-stu-id="8f52b-237">Initialization from Data (aka.</span></span> <span data-ttu-id="8f52b-238">o caminho do PC)</span><span class="sxs-lookup"><span data-stu-id="8f52b-238">the PC Path)</span></span>

<span data-ttu-id="8f52b-239">Embora as cenas possam ser computadas para consumo direto, elas também podem ser computadas em formato serializado para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="8f52b-239">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="8f52b-240">Isso provou ser muito útil para o desenvolvimento, pois permite que os desenvolvedores trabalhem e testem a compreensão da cena sem a necessidade de um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8f52b-240">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="8f52b-241">O ato de serializar uma cena é quase idêntico a computar a ti, os dados são retornados ao seu aplicativo em vez de serem desserializados localmente pelo SDK.</span><span class="sxs-lookup"><span data-stu-id="8f52b-241">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="8f52b-242">Você pode desserializá-lo por conta própria ou salvá-lo para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="8f52b-242">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneBlob for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="8f52b-243">Enumeração de sceneobject</span><span class="sxs-lookup"><span data-stu-id="8f52b-243">SceneObject Enumeration</span></span>

<span data-ttu-id="8f52b-244">Agora que seu aplicativo tem uma cena, seu aplicativo irá examinar e interagir com o SceneObjects.</span><span class="sxs-lookup"><span data-stu-id="8f52b-244">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="8f52b-245">Isso é feito acessando a propriedade **SceneObjects** :</span><span class="sxs-lookup"><span data-stu-id="8f52b-245">This is done by accessing the **SceneObjects** property:</span></span>

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

### <a name="component-update-and-re-finding-components"></a><span data-ttu-id="8f52b-246">Atualização de componente e redescoberta de componentes</span><span class="sxs-lookup"><span data-stu-id="8f52b-246">Component update and re-finding components</span></span>

<span data-ttu-id="8f52b-247">Há outra função que recupera componentes na cena chamada ***FindComponent***.</span><span class="sxs-lookup"><span data-stu-id="8f52b-247">There is another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="8f52b-248">Essa função é útil ao atualizar objetos de acompanhamento e localizá-los em cenas subsequentes.</span><span class="sxs-lookup"><span data-stu-id="8f52b-248">This function is useful when updating tracking objects and finding them in subsequent scenes.</span></span> <span data-ttu-id="8f52b-249">O código a seguir calculará uma nova cena em relação a uma cena anterior e, em seguida, encontrará o andar na nova cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-249">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="8f52b-250">Acessando malhas e quatros de objetos de cena</span><span class="sxs-lookup"><span data-stu-id="8f52b-250">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="8f52b-251">Depois que SceneObjects tiver sido localizado, o aplicativo provavelmente desejará acessar os dados contidos nos quatro processadores/malhas dos quais ele é composto.</span><span class="sxs-lookup"><span data-stu-id="8f52b-251">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is comprised of.</span></span> <span data-ttu-id="8f52b-252">Esses dados são acessados com as propriedades de ***quádruplas*** e de ***malhas*** .</span><span class="sxs-lookup"><span data-stu-id="8f52b-252">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span></span> <span data-ttu-id="8f52b-253">O código a seguir enumerará todos os quádruplos e malhas do nosso objeto Floor.</span><span class="sxs-lookup"><span data-stu-id="8f52b-253">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

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

<span data-ttu-id="8f52b-254">Observe que é o Sceneobject que tem a transformação relativa à origem da cena.</span><span class="sxs-lookup"><span data-stu-id="8f52b-254">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="8f52b-255">Isso ocorre porque o Sceneobject representa uma instância de "coisa" e é localizável no espaço, as quádruplas e as malhas representam a geometria transformada em relação ao seu pai.</span><span class="sxs-lookup"><span data-stu-id="8f52b-255">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="8f52b-256">É possível que SceneObjects separadas referenciem o mesmo SceneMesh/SceneQuad SceneComponents, e também é possível que um Sceneobject tenha mais de um SceneMesh/SceneQuad.</span><span class="sxs-lookup"><span data-stu-id="8f52b-256">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="8f52b-257">Lidando com transformações</span><span class="sxs-lookup"><span data-stu-id="8f52b-257">Dealing with Transforms</span></span>

<span data-ttu-id="8f52b-258">A compreensão da cena fez uma tentativa deliberada de se alinhar com as representações tradicionais de cena 3D ao lidar com transformações.</span><span class="sxs-lookup"><span data-stu-id="8f52b-258">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="8f52b-259">Portanto, cada cena é confinada a um único sistema de coordenadas, assim como as representações de ambiente 3D mais comuns.</span><span class="sxs-lookup"><span data-stu-id="8f52b-259">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="8f52b-260">SceneObjects cada um fornece seu local como uma posição e orientação dentro desse sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="8f52b-260">SceneObjects each provide their location as a position and orientation within that coordinate system.</span></span> <span data-ttu-id="8f52b-261">Se seu aplicativo estiver lidando com cenas que ampliam o limite do que uma única origem fornece, ela pode ancorar SceneObjects para SpatialAnchors ou gerar várias cenas e mesclá-las, mas para simplificar, vamos supor que as cenas de Watertight existam em sua própria origem localizada por um NodeId definido por Scene. OriginSpatialGraphNodeId.</span><span class="sxs-lookup"><span data-stu-id="8f52b-261">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="8f52b-262">O seguinte código de Unity, por exemplo, mostra como usar a percepção do Windows e as APIs do Unity para alinhar os sistemas de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="8f52b-262">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="8f52b-263">Consulte [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) e [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) para obter detalhes sobre as APIs de percepção do Windows e [objetos nativos da realidade misturada no Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) para obter detalhes sobre como obter um SpatialCoordinateSystem que corresponde à origem mundial da `.ToUnity()` Unity, bem como o `System.Numerics.Matrix4x4` método `UnityEngine.Matrix4x4`de extensão para converter entre e.</span><span class="sxs-lookup"><span data-stu-id="8f52b-263">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin, as well as the `.ToUnity()` extension method for converting between `System.Numerics.Matrix4x4` and `UnityEngine.Matrix4x4`.</span></span>

```cs
public class SceneRootComponent : MonoBehavior
{
    public SpatialCoordinateSystem worldOrigin;
    public Scene scene;
    SpatialCoordinateSystem sceneOrigin;
    
    void Start()
    {
        // Initialize a SpatialCoordinateSystem for the scene's node in the system's Spatial Graph.
        scene.origin = SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
    }
    
    void Update()
    {
        // Try to get the current transform of the scene's spatial graph node.
        // This may not be available, e.g. when tracking has been lost.
        var sceneToWorld = sceneOrigin.TryGetTransformTo(worldOrigin);
        if (sceneToWorld.HasValue)
        {
            // Convert the transform to Unity numerics and update the game object.
            var sceneToWorldUnity = sceneToWorld.Value.ToUnity();
            this.gameObject.transform.SetPositionAndRotation(sceneToWorldUnity.GetColumn(3), sceneToWorldUnity.rotation);
        }
    }
}
```

<span data-ttu-id="8f52b-264">Cada `SceneObject` tem uma `Position` propriedade `Orientation` e que pode ser usada para posicionar o conteúdo correspondente em relação à origem do `Scene`recipiente.</span><span class="sxs-lookup"><span data-stu-id="8f52b-264">Each `SceneObject` has a `Position` and `Orientation` property which can be used to position corresponding content relative to the origin of the containing `Scene`.</span></span> <span data-ttu-id="8f52b-265">Por exemplo, o exemplo a seguir pressupõe que o jogo é filho da raiz da cena e atribui sua posição local e rotação para alinhar a um determinado `SceneObject`:</span><span class="sxs-lookup"><span data-stu-id="8f52b-265">For example, the following example assumes that the game is a child of the scene root, and assigns its local position and rotation to align to a given `SceneObject`:</span></span>

```cs
void SetLocalTransformFromSceneObject(GameObject gameObject, SceneObject sceneObject)
{
    gameObject.transform.localPosition = sceneObject.Position.ToUnity();
    gameObject.transform.localRotation = sceneObject.Orientation.ToUnity());
}
```

### <a name="quad"></a><span data-ttu-id="8f52b-266">Quadra</span><span class="sxs-lookup"><span data-stu-id="8f52b-266">Quad</span></span>

<span data-ttu-id="8f52b-267">Os quatro processadores foram projetados para facilitar os cenários de posicionamento de 2D e devem ser considerados como extensões para elementos de UX de tela 2D.</span><span class="sxs-lookup"><span data-stu-id="8f52b-267">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="8f52b-268">Embora os quatro processadores sejam componentes de SceneObjects e possam ser renderizados em 3D, as APIs quádruplas em si pressupõem que as quatro são estruturas 2D.</span><span class="sxs-lookup"><span data-stu-id="8f52b-268">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="8f52b-269">Eles oferecem informações como extensão, forma e fornecem APIs para posicionamento.</span><span class="sxs-lookup"><span data-stu-id="8f52b-269">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="8f52b-270">Os quatro processadores têm extensões retangulares, mas representam superfícies 2D com formato arbitrário.</span><span class="sxs-lookup"><span data-stu-id="8f52b-270">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="8f52b-271">Para habilitar o posicionamento nessas superfícies 2D que interagem com o ambiente 3D, as quatro ofertas oferecem utilitários para tornar essa interação possível.</span><span class="sxs-lookup"><span data-stu-id="8f52b-271">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="8f52b-272">Atualmente, a compreensão da cena fornece duas funções desse tipo, **FindCentermostPlacement** e **GetOcclusionMask**.</span><span class="sxs-lookup"><span data-stu-id="8f52b-272">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask**.</span></span> <span data-ttu-id="8f52b-273">FindCentermostPlacement é uma API de alto nível que localiza uma posição no Quad em que um objeto pode ser colocado e tentará encontrar o melhor local para seu objeto, garantindo que a caixa delimitadora que você fornece residirá na superfície subjacente.</span><span class="sxs-lookup"><span data-stu-id="8f52b-273">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span></span>

<span data-ttu-id="8f52b-274">O exemplo a seguir mostra como localizar o local centermost posicionável e ancorar um holograma para o quad.</span><span class="sxs-lookup"><span data-stu-id="8f52b-274">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

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
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="8f52b-275">As etapas 1-4 são altamente dependentes de sua estrutura/implementação específica, mas os temas devem ser semelhantes.</span><span class="sxs-lookup"><span data-stu-id="8f52b-275">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="8f52b-276">É importante observar que o quad simplesmente representa um plano 2D limitado que é localizado no espaço.</span><span class="sxs-lookup"><span data-stu-id="8f52b-276">It is important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="8f52b-277">Tendo seu mecanismo/estrutura sabendo onde o Quad é e criando a raiz de seus objetos em relação ao Quad, seus hologramas estarão localizados corretamente em relação ao mundo real.</span><span class="sxs-lookup"><span data-stu-id="8f52b-277">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> <span data-ttu-id="8f52b-278">Para obter informações mais detalhadas, consulte nossos exemplos em quatro processadores que mostram implementações específicas.</span><span class="sxs-lookup"><span data-stu-id="8f52b-278">For more detailed information please see our samples on quads which show specific implementations.</span></span>

### <a name="mesh"></a><span data-ttu-id="8f52b-279">Malha</span><span class="sxs-lookup"><span data-stu-id="8f52b-279">Mesh</span></span>

<span data-ttu-id="8f52b-280">As malhas representam representações geométricas de objetos ou ambientes.</span><span class="sxs-lookup"><span data-stu-id="8f52b-280">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="8f52b-281">Assim como o [mapeamento espacial](spatial-mapping.md), o índice de malha e os dados de vértice fornecidos com cada malha de superfície espacial usam o mesmo layout familiar que os buffers de vértice e de índice usados para renderizar malhas de triângulo em todas as APIs de renderização modernas.</span><span class="sxs-lookup"><span data-stu-id="8f52b-281">Much like [spatial mapping](spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="8f52b-282">As posições de vértice são fornecidas no sistema de coordenadas `Scene`do.</span><span class="sxs-lookup"><span data-stu-id="8f52b-282">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="8f52b-283">As APIs específicas usadas para fazer referência a esses dados são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="8f52b-283">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="8f52b-284">O código a seguir fornece um exemplo de como gerar uma lista de triângulos a partir da estrutura de malha:</span><span class="sxs-lookup"><span data-stu-id="8f52b-284">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="8f52b-285">Os buffers de índice/vértice devem ser >= as contagens de índice/vértice, mas, caso contrário, podem ser arbitrariamente dimensionados permitindo uma reutilização de memória eficiente.</span><span class="sxs-lookup"><span data-stu-id="8f52b-285">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span></span>

## <a name="developing-with-scene-understandings"></a><span data-ttu-id="8f52b-286">Desenvolvendo com entendimentos em cena</span><span class="sxs-lookup"><span data-stu-id="8f52b-286">Developing with scene understandings</span></span>

<span data-ttu-id="8f52b-287">Neste ponto, você deve entender os principais blocos de construção da cena que compreendem o tempo de execução e o SDK.</span><span class="sxs-lookup"><span data-stu-id="8f52b-287">At this point you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="8f52b-288">A maior parte do poder e da complexidade está em padrões de acesso, interação com estruturas 3D e ferramentas que podem ser escritas sobre essas APIs para executar tarefas mais avançadas como planejamento espacial, análise de sala, navegação, física etc. Esperamos capturá-los em exemplos que esperamos orientá-lo na direção correta para fazer seus cenários brilharem.</span><span class="sxs-lookup"><span data-stu-id="8f52b-288">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc. We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="8f52b-289">Se houver amostras/cenários que não estão sendo abordados, informe-nos e tentaremos documentar/criar um protótipo do que você precisa.</span><span class="sxs-lookup"><span data-stu-id="8f52b-289">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="8f52b-290">Onde posso obter o código de exemplo?</span><span class="sxs-lookup"><span data-stu-id="8f52b-290">Where can I get sample code?</span></span>

<span data-ttu-id="8f52b-291">O código de exemplo de compreensão da cena para Unity pode ser encontrado em nossa página [da página de exemplo do Unity](https://github.com/sceneunderstanding-microsoft/unitysample) .</span><span class="sxs-lookup"><span data-stu-id="8f52b-291">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="8f52b-292">Este aplicativo permitirá que você se comunique com seu dispositivo e processe os vários objetos de cena, ou ele permitirá que você carregue uma cena serializada em seu PC e permita que você experimente a compreensão da cena sem um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8f52b-292">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="8f52b-293">Onde posso obter exemplos de cenas?</span><span class="sxs-lookup"><span data-stu-id="8f52b-293">Where can I get sample scenes?</span></span>

<span data-ttu-id="8f52b-294">Se você tiver um HoloLens2, poderá salvar qualquer cena capturada salvando a saída de ComputeSerializedAsync em arquivo e desserializando-a de sua própria conveniência.</span><span class="sxs-lookup"><span data-stu-id="8f52b-294">If you have a HoloLens2 you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="8f52b-295">Se você não tiver um dispositivo HoloLens2, mas quiser brincar com a compreensão da cena, será necessário baixar uma cena previamente capturada.</span><span class="sxs-lookup"><span data-stu-id="8f52b-295">If you do not have a HoloLens2 device but want to play with Scene Understanding you will need to download a pre-captured scene.</span></span> <span data-ttu-id="8f52b-296">A amostra de compreensão da cena é fornecida atualmente com cenas serializadas que podem ser baixadas e usadas por sua própria conveniência.</span><span class="sxs-lookup"><span data-stu-id="8f52b-296">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="8f52b-297">Você pode encontrá-los aqui:</span><span class="sxs-lookup"><span data-stu-id="8f52b-297">You can find them here:</span></span>

[<span data-ttu-id="8f52b-298">Cenas de exemplo de compreensão de cena</span><span class="sxs-lookup"><span data-stu-id="8f52b-298">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a><span data-ttu-id="8f52b-299">Confira também</span><span class="sxs-lookup"><span data-stu-id="8f52b-299">See also</span></span>

* [<span data-ttu-id="8f52b-300">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="8f52b-300">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="8f52b-301">Reconhecimento de cena</span><span class="sxs-lookup"><span data-stu-id="8f52b-301">Scene understanding</span></span>](scene-understanding.md)
* [<span data-ttu-id="8f52b-302">Exemplo de Unity</span><span class="sxs-lookup"><span data-stu-id="8f52b-302">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
