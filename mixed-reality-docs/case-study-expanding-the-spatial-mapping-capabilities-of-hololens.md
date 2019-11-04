---
title: Estudo de caso – expandindo os recursos de mapeamento espacial do HoloLens
description: Ao criar nossos primeiros aplicativos para o Microsoft HoloLens, estamos ansiosos para ver a distância dos limites do mapeamento espacial no dispositivo.
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, mapeamento espacial
ms.openlocfilehash: 5142cb383d4408b29eb17eb5ede84d19b2533dc4
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436726"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="c6b0e-104">Estudo de caso – expandindo os recursos de mapeamento espacial do HoloLens</span><span class="sxs-lookup"><span data-stu-id="c6b0e-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="c6b0e-105">Ao criar nossos primeiros aplicativos para o Microsoft HoloLens, estamos ansiosos para ver a distância dos limites do mapeamento espacial no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="c6b0e-106">Jeff Evertt, engenheiro de software da Microsoft estúdios, explica como uma nova tecnologia foi desenvolvida fora da necessidade de mais controle sobre como os hologramas são colocados no ambiente real do usuário.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

> [!NOTE]
> <span data-ttu-id="c6b0e-107">O HoloLens 2 implementa uma nova [cena que entende o tempo de execução](scene-understanding.md), que fornece aos desenvolvedores de realidade misturada uma representação de ambiente estruturada e de alto nível projetada para tornar o desenvolvimento para aplicativos com reconhecimento de ambiente intuitivo.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-107">HoloLens 2 implements a new [Scene Understanding Runtime](scene-understanding.md), that provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> 

## <a name="watch-the-video"></a><span data-ttu-id="c6b0e-108">Assista ao vídeo</span><span class="sxs-lookup"><span data-stu-id="c6b0e-108">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="c6b0e-109">Além do mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="c6b0e-109">Beyond spatial mapping</span></span>

<span data-ttu-id="c6b0e-110">Enquanto estávamos trabalhando em [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8) e [jovens conkers](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), dois dos primeiros jogos para o HoloLens, descobrimos que, ao fazer o posicionamento de procedimentos dos hologramas no mundo físico, precisávamos de um nível mais alto de compreensão sobre o ambiente.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-110">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="c6b0e-111">Cada jogo teve suas próprias necessidades de posicionamento específicas: em fragmentos, por exemplo, queríamos ser capaz de distinguir entre diferentes superfícies, como o piso ou uma tabela, para colocar pistas em locais relevantes.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-111">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="c6b0e-112">Também queríamos ser capazes de identificar superfícies em que os caracteres Holographic de tamanho de vida pudessem se sentar, como um sofá ou uma cadeira.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-112">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="c6b0e-113">Em Conker jovem, queríamos que Conker e seus adversários consigam usar superfícies levantadas na sala de um jogador como plataformas.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-113">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="c6b0e-114">[Asobo estúdios](https://www.asobostudio.com/index.html), nosso parceiro de desenvolvimento para esses jogos, enfrentou esse problema e criou uma tecnologia que estende os recursos de mapeamento espacial do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-114">[Asobo Studios](https://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="c6b0e-115">Usando isso, poderíamos analisar a sala de um jogador e identificar superfícies como paredes, tabelas, cadeiras e andares.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-115">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="c6b0e-116">Ele também nos forneceu a capacidade de otimizar em relação a um conjunto de restrições para determinar o melhor posicionamento para objetos Holographic.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-116">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="c6b0e-117">O código de compreensão espacial</span><span class="sxs-lookup"><span data-stu-id="c6b0e-117">The spatial understanding code</span></span>

<span data-ttu-id="c6b0e-118">Pegamos o código original de Asobo e criamos uma biblioteca que encapsula essa tecnologia.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-118">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="c6b0e-119">A Microsoft e o Asobo agora têm o código-fonte aberto e disponibilizado no [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) para você usar em seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-119">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="c6b0e-120">Todo o código-fonte está incluído, permitindo personalizá-lo às suas necessidades e compartilhar suas melhorias com a Comunidade.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-120">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="c6b0e-121">O código do C++ resolvedor foi encapsulado em uma DLL UWP e exposto ao Unity com um [pré-fabricado de distribuição contido no MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span><span class="sxs-lookup"><span data-stu-id="c6b0e-121">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="c6b0e-122">Há muitas consultas úteis incluídas no exemplo de Unity que permitirão que você encontre espaços vazios em paredes, coloque objetos no teto ou em espaços grandes no chão, identifique os locais para os caracteres a serem colocados e uma infinidade de outras consultas de compreensão espacial.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-122">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="c6b0e-123">Embora a solução de mapeamento espacial fornecida pelo HoloLens seja projetada para ser genérica o suficiente para atender às necessidades de toda a gama de espaços problemáticos, o módulo de compreensão espacial foi criado para dar suporte às necessidades de dois jogos específicos.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-123">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="c6b0e-124">Dessa forma, sua solução é estruturada em um processo específico e um conjunto de suposições:</span><span class="sxs-lookup"><span data-stu-id="c6b0e-124">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="c6b0e-125">**Tamanho fixo Playspace**: o usuário especifica o tamanho máximo de Playspace na chamada de inicialização.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-125">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="c6b0e-126">**Processo de verificação única**: o processo requer uma fase de verificação discreta na qual o usuário percorra, definindo o Playspace.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-126">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="c6b0e-127">As funções de consulta não funcionarão até que a verificação seja finalizada.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-127">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="c6b0e-128">**Playspace controlado pelo usuário "pintando**": durante a fase de verificação, o usuário se move e procura o Playspace, pintando efetivamente as áreas que devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-128">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="c6b0e-129">A malha gerada é importante para fornecer comentários do usuário durante essa fase.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-129">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="c6b0e-130">**Inportações domésticas ou de instalação do Office**: as funções de consulta são projetadas em relação a superfícies simples e paredes em ângulos retos.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-130">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="c6b0e-131">Essa é uma limitação flexível.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-131">This is a soft limitation.</span></span> <span data-ttu-id="c6b0e-132">No entanto, durante a fase de verificação, uma análise de eixo primário é concluída para otimizar o mosaico de malha ao longo do eixo principal e secundário.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-132">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="c6b0e-133">Processo de verificação de sala</span><span class="sxs-lookup"><span data-stu-id="c6b0e-133">Room Scanning Process</span></span>

<span data-ttu-id="c6b0e-134">Ao carregar o módulo de compreensão espacial, a primeira coisa que você fará é digitalizar seu espaço, de modo que todas as superfícies utilizáveis — como piso, teto e paredes — sejam identificadas e rotuladas.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-134">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="c6b0e-135">Durante o processo de verificação, você examina sua sala e "pinta" as áreas que devem ser incluídas na verificação.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-135">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="c6b0e-136">A malha vista durante essa fase é uma parte importante dos comentários visuais que permite aos usuários saber quais partes da sala estão sendo examinadas.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-136">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="c6b0e-137">A DLL para o módulo de compreensão espacial armazena internamente o Playspace como uma grade de cubos VOXEL dimensionados 8cm.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-137">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="c6b0e-138">Durante a parte inicial da verificação, uma análise de componente primário é concluída para determinar os eixos da sala.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-138">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="c6b0e-139">Internamente, ele armazena seu espaço VOXEL alinhado a esses eixos.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-139">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="c6b0e-140">Uma malha é gerada aproximadamente a cada segundo, extraindo o isosurface do volume VOXEL.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-140">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![Malha de mapeamento espacial em branco e entendendo a malha Playspace em verde](images/spatial-mapping-500px.png)

<span data-ttu-id="c6b0e-142">Malha de mapeamento espacial em branco e entendendo a malha Playspace em verde</span><span class="sxs-lookup"><span data-stu-id="c6b0e-142">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="c6b0e-143">O arquivo SpatialUnderstanding.cs incluído gerencia o processo da fase de verificação.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-143">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="c6b0e-144">Ele chama as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="c6b0e-144">It calls the following functions:</span></span>
* <span data-ttu-id="c6b0e-145">**SpatialUnderstanding_Init**: chamado uma vez no início.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-145">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="c6b0e-146">**GeneratePlayspace_InitScan**: indica que a fase de verificação deve começar.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-146">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="c6b0e-147">**GeneratePlayspace_UpdateScan_DynamicScan**: chamado cada quadro para atualizar o processo de verificação.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-147">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="c6b0e-148">A posição e a orientação da câmera são passadas e são usadas para o processo de pintura Playspace, descrito acima.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-148">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="c6b0e-149">**GeneratePlayspace_RequestFinish**: chamado para finalizar o Playspace.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-149">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="c6b0e-150">Isso usará as áreas "pintadas" durante a fase de verificação para definir e bloquear o Playspace.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-150">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="c6b0e-151">O aplicativo pode consultar estatísticas durante a fase de verificação, bem como consultar a malha personalizada para fornecer comentários do usuário.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-151">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="c6b0e-152">**Import_UnderstandingMesh**: durante a verificação, o comportamento de **SpatialUnderstandingCustomMesh** fornecido pelo módulo e colocado na compreensão pré-fabricado consultará periodicamente a malha personalizada gerada pelo processo.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-152">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="c6b0e-153">Além disso, isso é feito mais uma vez após a verificação ter sido finalizada.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-153">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="c6b0e-154">O fluxo de verificação, orientado pelo comportamento **SpatialUnderstanding** , chama **InitScan**e, em seguida, **UpdateScan** cada quadro.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-154">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="c6b0e-155">Quando a consulta de estatísticas relata cobertura razoável, o usuário pode airtap chamar **RequestFinish** para indicar o fim da fase de verificação.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-155">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="c6b0e-156">**UpdateScan** continua sendo chamado até que o valor de retorno indique que a dll concluiu o processamento.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-156">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="c6b0e-157">As consultas</span><span class="sxs-lookup"><span data-stu-id="c6b0e-157">The queries</span></span>

<span data-ttu-id="c6b0e-158">Quando a verificação for concluída, você poderá acessar três tipos diferentes de consultas na interface:</span><span class="sxs-lookup"><span data-stu-id="c6b0e-158">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="c6b0e-159">**Consultas de topologia**: essas são consultas rápidas que se baseiam na topologia da sala digitalizada.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-159">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="c6b0e-160">**Consultas de forma**: elas utilizam os resultados de suas consultas de topologia para localizar superfícies horizontais que são uma boa correspondência para formas personalizadas que você define.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-160">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="c6b0e-161">**Consultas de posicionamento de objeto**: são consultas mais complexas que encontram o local de melhor ajuste com base em um conjunto de regras e restrições para o objeto.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-161">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="c6b0e-162">Além das três consultas principais, há uma interface raycasting que pode ser usada para recuperar tipos de superfície marcada e uma malha de sala Watertight personalizada pode ser copiada.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-162">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="c6b0e-163">Consultas de topologia</span><span class="sxs-lookup"><span data-stu-id="c6b0e-163">Topology queries</span></span>

<span data-ttu-id="c6b0e-164">Dentro da DLL, o Gerenciador de topologia lida com a rotulagem do ambiente.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-164">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="c6b0e-165">Conforme mencionado acima, grande parte dos dados é armazenada em surfels, que estão contidos em um volume VOXEL.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-165">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="c6b0e-166">Além disso, a estrutura **PlaySpaceInfos** é usada para armazenar informações sobre o Playspace, incluindo o alinhamento Mundial (mais detalhes sobre isso abaixo), piso e altura do teto.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-166">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="c6b0e-167">A heurística é usada para determinar piso, teto e paredes.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-167">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="c6b0e-168">Por exemplo, a maior e menor superfície horizontal com uma área de superfície maior que 1 m2 é considerada a base.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-168">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="c6b0e-169">Observe que o caminho da câmera durante o processo de verificação também é usado nesse processo.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-169">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="c6b0e-170">Um subconjunto das consultas expostas pelo Gerenciador de topologia é exposto por meio da DLL.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-170">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="c6b0e-171">As consultas de topologia expostas são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="c6b0e-171">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="c6b0e-172">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="c6b0e-172">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="c6b0e-173">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="c6b0e-173">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="c6b0e-174">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="c6b0e-174">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="c6b0e-175">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="c6b0e-175">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="c6b0e-176">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="c6b0e-176">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="c6b0e-177">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="c6b0e-177">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="c6b0e-178">Cada uma das consultas tem um conjunto de parâmetros, específico ao tipo de consulta.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-178">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="c6b0e-179">No exemplo a seguir, o usuário especifica a altura mínima & largura do volume desejado, a altura mínima de posicionamento acima do andar e a quantidade mínima de espaço livre na frente do volume.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-179">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="c6b0e-180">Todas as medidas estão em metros.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-180">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="c6b0e-181">Cada uma dessas consultas usa uma matriz pré-configurada de estruturas **TopologyResult** .</span><span class="sxs-lookup"><span data-stu-id="c6b0e-181">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="c6b0e-182">O parâmetro **locationCount** especifica o comprimento da matriz passada.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-182">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="c6b0e-183">O valor de retorno informa o número de locais retornados.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-183">The return value reports the number of returned locations.</span></span> <span data-ttu-id="c6b0e-184">Esse número nunca é maior que o parâmetro **locationCount** passado.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-184">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="c6b0e-185">O **TopologyResult** contém a posição central do volume retornado, a direção oposta (ou seja, normal) e as dimensões do espaço encontrado.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-185">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="c6b0e-186">Observe que, no exemplo de Unity, cada uma dessas consultas é vinculada a um botão no painel de interface do usuário virtual.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-186">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="c6b0e-187">Os códigos de exemplo codificam os parâmetros de cada uma dessas consultas para valores razoáveis.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-187">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="c6b0e-188">Consulte *SpaceVisualizer.cs* no código de exemplo para obter mais exemplos.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-188">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="c6b0e-189">Consultas de forma</span><span class="sxs-lookup"><span data-stu-id="c6b0e-189">Shape queries</span></span>

<span data-ttu-id="c6b0e-190">Dentro da DLL, o analisador de forma (**ShapeAnalyzer_W**) usa o analisador de topologia para corresponder às formas personalizadas definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-190">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="c6b0e-191">O exemplo de Unity tem um conjunto predefinido de formas que são mostradas no menu consulta, na guia forma.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-191">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="c6b0e-192">Observe que a análise de forma funciona apenas em superfícies horizontais.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-192">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="c6b0e-193">Um sofá, por exemplo, é definido pela superfície de estação plana e a parte superior do sofá de volta.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-193">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="c6b0e-194">A consulta de forma procura duas superfícies de um tamanho, altura e intervalo de aspecto específicos, com as duas superfícies alinhadas e conectadas.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-194">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="c6b0e-195">Usando a terminologia de APIs, a estação de sofá e a parte superior do sofá são componentes de forma e os requisitos de alinhamento são restrições de componente de forma.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-195">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="c6b0e-196">Uma consulta de exemplo definida no exemplo de Unity (**ShapeDefinition.cs**) para objetos "sittable" é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="c6b0e-196">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="c6b0e-197">Cada consulta de forma é definida por um conjunto de componentes de forma, cada um com um conjunto de restrições de componente e um conjunto de restrições de forma que lista as dependências entre os componentes.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-197">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="c6b0e-198">Este exemplo inclui três restrições em uma única definição de componente e nenhuma restrição de forma entre os componentes (já que há apenas um componente).</span><span class="sxs-lookup"><span data-stu-id="c6b0e-198">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="c6b0e-199">Por outro lado, a forma de sofá tem dois componentes Shape e quatro restrições Shape.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-199">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="c6b0e-200">Observe que os componentes são identificados por seu índice na lista de componentes do usuário (0 e 1 neste exemplo).</span><span class="sxs-lookup"><span data-stu-id="c6b0e-200">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="c6b0e-201">As funções de wrapper são fornecidas no módulo do Unity para facilitar a criação de definições de formas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-201">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="c6b0e-202">A lista completa de restrições de componente e forma pode ser encontrada em **SpatialUnderstandingDll.cs** nas estruturas **ShapeComponentConstraint** e **ShapeConstraint** .</span><span class="sxs-lookup"><span data-stu-id="c6b0e-202">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![O retângulo azul realça os resultados da consulta de forma de cadeira.](images/chair-shape-query-500px.png)

<span data-ttu-id="c6b0e-204">O retângulo azul realça os resultados da consulta de forma de cadeira.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-204">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="c6b0e-205">Resolvedor de posicionamento de objeto</span><span class="sxs-lookup"><span data-stu-id="c6b0e-205">Object placement solver</span></span>

<span data-ttu-id="c6b0e-206">As consultas de posicionamento de objeto podem ser usadas para identificar locais ideais no espaço físico para colocar seus objetos.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-206">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="c6b0e-207">O resolvedor encontrará o local de melhor ajuste, considerando as regras e restrições do objeto.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-207">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="c6b0e-208">Além disso, as consultas de objeto persistem até que o objeto seja removido com chamadas **Solver_RemoveObject** ou **Solver_RemoveAllObjects** , permitindo o posicionamento restrito de vários objetos.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-208">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="c6b0e-209">As consultas de posicionamento de objeto consistem em três partes: tipo de posicionamento com parâmetros, uma lista de regras e uma lista de restrições.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-209">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="c6b0e-210">Para executar uma consulta, use a seguinte API:</span><span class="sxs-lookup"><span data-stu-id="c6b0e-210">To run a query, use the following API:</span></span>




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
<span data-ttu-id="c6b0e-211">Essa função usa um nome de objeto, uma definição de posicionamento e uma lista de regras e restrições.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-211">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="c6b0e-212">Os C# wrappers fornecem funções auxiliares de construção para facilitar a construção da regra e da restrição.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-212">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="c6b0e-213">A definição de posicionamento contém o tipo de consulta, ou seja, uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="c6b0e-213">The placement definition contains the query type — that is, one of the following:</span></span>




```
public enum PlacementType
                {
                    Place_OnFloor,
                    Place_OnWall,
                    Place_OnCeiling,
                    Place_OnShape,
                    Place_OnEdge,
                    Place_OnFloorAndCeiling,
                    Place_RandomInAir,
                    Place_InMidAir,
                    Place_UnderFurnitureEdge,
                };
```

<span data-ttu-id="c6b0e-214">Cada um dos tipos de posicionamento tem um conjunto de parâmetros exclusivos para o tipo.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-214">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="c6b0e-215">A estrutura **ObjectPlacementDefinition** contém um conjunto de funções auxiliares estáticas para criar essas definições.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-215">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="c6b0e-216">Por exemplo, para encontrar um local para colocar um objeto no chão, você pode usar a seguinte função:</span><span class="sxs-lookup"><span data-stu-id="c6b0e-216">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="c6b0e-217">Além do tipo de posicionamento, você pode fornecer um conjunto de regras e restrições.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-217">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="c6b0e-218">As regras não podem ser violadas.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-218">Rules cannot be violated.</span></span> <span data-ttu-id="c6b0e-219">Os locais de posicionamento possíveis que atendem ao tipo e às regras são então otimizados em relação ao conjunto de restrições para selecionar o local de posicionamento ideal.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-219">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="c6b0e-220">Cada uma das regras e restrições pode ser criada pelas funções de criação estática fornecidas.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-220">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="c6b0e-221">Uma regra de exemplo e uma função de construção de restrição são fornecidas abaixo.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-221">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="c6b0e-222">A consulta de posicionamento de objeto abaixo está procurando um local para colocar um cubo de meio medidor na borda de uma superfície, longe de outros objetos anteriormente posicionados e perto do centro da sala.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-222">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




```
List<ObjectPlacementRule> rules = 
          new List<ObjectPlacementRule>() {
               ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
          };

     List<ObjectPlacementConstraint> constraints = 
          new List<ObjectPlacementConstraint> {
               ObjectPlacementConstraint.Create_NearCenter(),
          };

     Solver_PlaceObject(
          “MyCustomObject”,
          new ObjectPlacementDefinition.Create_OnEdge(
          new Vector3(0.25f, 0.25f, 0.25f), 
          new Vector3(0.25f, 0.25f, 0.25f)),
          rules.Count,
          UnderstandingDLL.PinObject(rules.ToArray()),
          constraints.Count,
          UnderstandingDLL.PinObject(constraints.ToArray()),
          UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="c6b0e-223">Se for bem-sucedida, uma estrutura **ObjectPlacementResult** que contém a posição de posicionamento, dimensões e orientação será retornada.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-223">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="c6b0e-224">Além disso, o posicionamento é adicionado à lista interna de objetos posicionados da DLL.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-224">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="c6b0e-225">As consultas de posicionamento subsequentes levarão esse objeto à conta.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-225">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="c6b0e-226">O arquivo **LevelSolver.cs** no exemplo de Unity contém mais consultas de exemplo.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-226">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![As caixas azuis mostram o resultado de três lugares em consultas de piso com as regras "distantes da posição da câmera".](images/away-from-camera-position-500px.png)

<span data-ttu-id="c6b0e-228">As caixas azuis mostram o resultado de três lugares em consultas de piso com as regras "distantes da posição da câmera".</span><span class="sxs-lookup"><span data-stu-id="c6b0e-228">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="c6b0e-229">**Sobre**</span><span class="sxs-lookup"><span data-stu-id="c6b0e-229">**Tips:**</span></span>
* <span data-ttu-id="c6b0e-230">Ao resolver o local de posicionamento de vários objetos necessários para um cenário de nível ou aplicativo, primeiro resolva os objetos indispensável e grandes para maximizar a probabilidade de que um espaço possa ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-230">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="c6b0e-231">A ordem de posicionamento é importante.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-231">Placement order is important.</span></span> <span data-ttu-id="c6b0e-232">Se os posicionamentos de objeto não puderem ser encontrados, tente configurações menos restritas.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-232">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="c6b0e-233">Ter um conjunto de configurações de fallback é essencial para dar suporte à funcionalidade em várias configurações de sala.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-233">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="c6b0e-234">Conversão de Ray</span><span class="sxs-lookup"><span data-stu-id="c6b0e-234">Ray casting</span></span>

<span data-ttu-id="c6b0e-235">Além das três consultas principais, uma interface de conversão Ray pode ser usada para recuperar tipos de superfície marcada e uma malha Watertight Playspace personalizada pode ser copiada depois que o espaço é verificado e finalizado, os rótulos são gerados internamente para superfícies como a piso, teto e paredes.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-235">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="c6b0e-236">A função **PlayspaceRaycast** usa um Ray e retorna se o raio colide com uma superfície conhecida e, nesse caso, informações sobre essa superfície na forma de um **RaycastResult**.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-236">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

<span data-ttu-id="c6b0e-237">Internamente, o Raycast é calculado em relação à representação computada 8cm cúbico VOXEL do Playspace.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-237">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="c6b0e-238">Cada voxel contém um conjunto de elementos Surface com dados de topologia processados (também conhecidos como surfels).</span><span class="sxs-lookup"><span data-stu-id="c6b0e-238">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="c6b0e-239">As surfels contidas na célula VOXEL interseccionada são comparadas e a melhor correspondência usada para pesquisar as informações de topologia.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-239">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="c6b0e-240">Esses dados de topologia contêm o rótulo retornado na forma da enumeração **SurfaceTypes** , bem como a área de superfície da superfície interseccionada.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-240">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="c6b0e-241">No exemplo de Unity, o cursor converte um raio cada quadro.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-241">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="c6b0e-242">Primeiro, em relação aos colisors da Unity; segundo, em relação à representação Mundial do módulo de compreensão; e, finalmente, nos elementos da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-242">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="c6b0e-243">Neste aplicativo, a interface do usuário obtém prioridade, então o resultado da compreensão e, finalmente, os colisors do Unity.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-243">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="c6b0e-244">O **surfacetype** é relatado como texto ao lado do cursor.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-244">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Interseção de relatório de resultados Raycast com o piso.](images/raycast-result-500px.jpg)

<span data-ttu-id="c6b0e-246">Interseção de relatório de resultados Raycast com o piso.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-246">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="c6b0e-247">Obter o código</span><span class="sxs-lookup"><span data-stu-id="c6b0e-247">Get the code</span></span>

<span data-ttu-id="c6b0e-248">O código-fonte aberto está disponível em [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span><span class="sxs-lookup"><span data-stu-id="c6b0e-248">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="c6b0e-249">Informe-nos nos [fóruns de desenvolvedores do HoloLens](https://forums.hololens.com/) se você usar o código em um projeto.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-249">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="c6b0e-250">Não podemos esperar para ver o que você faz com!</span><span class="sxs-lookup"><span data-stu-id="c6b0e-250">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="c6b0e-251">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="c6b0e-251">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="c6b0e-252"><b>Jeff Evertt</b> é um líder de engenharia de software que trabalhou no HoloLens desde o início dos dias, da incubação para a experiência de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-252"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="c6b0e-253">Antes do HoloLens, ele trabalhou no Xbox Kinect e no setor de jogos em uma ampla variedade de plataformas e jogos.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-253">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="c6b0e-254">Jeff é apaixonado por robótica, gráficos e coisas com luzes piscantes que vão soar.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-254">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="c6b0e-255">Ele gosta de aprender novas coisas e trabalhar com software, hardware e, particularmente, no espaço em que os dois interseccionam.</span><span class="sxs-lookup"><span data-stu-id="c6b0e-255">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="c6b0e-256">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6b0e-256">See also</span></span>
* [<span data-ttu-id="c6b0e-257">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="c6b0e-257">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="c6b0e-258">Reconhecimento de cena</span><span class="sxs-lookup"><span data-stu-id="c6b0e-258">Scene understanding</span></span>](scene-understanding.md)
* [<span data-ttu-id="c6b0e-259">Visualização de varredura do ambiente</span><span class="sxs-lookup"><span data-stu-id="c6b0e-259">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="c6b0e-260">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="c6b0e-260">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="c6b0e-261">Asobo Studio: lições da frente do desenvolvimento do HoloLens</span><span class="sxs-lookup"><span data-stu-id="c6b0e-261">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
