---
title: Estudo de caso - criando uma galáxia na realidade mista
description: Antes de enviadas do Microsoft HoloLens, perguntamos nossa comunidade de desenvolvedores que tipo de aplicativo eles gostariam de ver uma equipe interna experiente compilar para o novo dispositivo. Mais de 5000 ideias foram compartilhadas e depois de uma pesquisa do Twitter de 24 horas, o vencedor era uma ideia chamada ""Galaxy Gerenciador.
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Explorer Galaxy, HoloLens, Windows Mixed Reality, compartilhe sua ideia, estudo de caso
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590966"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="4f4df-105">Estudo de caso - criando uma galáxia na realidade mista</span><span class="sxs-lookup"><span data-stu-id="4f4df-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="4f4df-106">Antes de enviadas do Microsoft HoloLens, perguntamos nossa comunidade de desenvolvedores que tipo de aplicativo eles gostariam de ver uma equipe interna experiente compilar para o novo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4f4df-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="4f4df-107">Mais de 5000 ideias foram compartilhadas e depois de uma pesquisa do Twitter de 24 horas, o vencedor era uma ideia chamada [Galaxy Explorer](galaxy-explorer.md).</span><span class="sxs-lookup"><span data-stu-id="4f4df-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="4f4df-108">Andy Zibits, o líder de arte no projeto e Karim Luccin, engenheiro de elementos gráficos da equipe, fale sobre o esforço colaborativo entre arte e de engenharia que levaram à criação de uma representação precisa, interativa do galaxy Láctea no Explorer Galaxy.</span><span class="sxs-lookup"><span data-stu-id="4f4df-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="4f4df-109">O técnico</span><span class="sxs-lookup"><span data-stu-id="4f4df-109">The Tech</span></span>

<span data-ttu-id="4f4df-110">[Nossa equipe](galaxy-explorer.md#meet-the-team) - feita para cima de dois designers, desenvolvedores de três, quatro artistas, um produtor e um testador — tinha seis semanas para criar um aplicativo totalmente funcional que permite que as pessoas saber mais sobre e explorar o vastness e a beleza de nosso Galaxy Láctea.</span><span class="sxs-lookup"><span data-stu-id="4f4df-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="4f4df-111">Gostaríamos de aproveitar ao máximo a capacidade de renderizar objetos 3D diretamente em seu espaço de vida, portanto, decidimos que queríamos criar um realista atraente galaxy onde as pessoas seria capazes de ampliar close e ver estrelas individuais, cada um em seus próprio trajetórias de HoloLens .</span><span class="sxs-lookup"><span data-stu-id="4f4df-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="4f4df-112">Na primeira semana de desenvolvimento, criamos alguns objetivos para nosso representação do Galaxy Láctea: Ele precisava ter profundidade, movimento e aparência volumétricas — completo de estrelas que ajudam a criar a forma do galaxy.</span><span class="sxs-lookup"><span data-stu-id="4f4df-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="4f4df-113">O problema com a criação de uma galáxia animada que tinha bilhões de estrelas era que o enorme número de elementos únicos que precisam de atualização seria muito grande por quadro para HoloLens animar usando a CPU.</span><span class="sxs-lookup"><span data-stu-id="4f4df-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="4f4df-114">Nossa solução envolvia uma mistura complexa de arte e ciência.</span><span class="sxs-lookup"><span data-stu-id="4f4df-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="4f4df-115">Nos bastidores</span><span class="sxs-lookup"><span data-stu-id="4f4df-115">Behind the scenes</span></span>

<span data-ttu-id="4f4df-116">Para permitir que as pessoas explorem estrelas individuais, nossa primeira etapa foi descobrir quantos partículas, foi possível processar ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="4f4df-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="4f4df-117">Partículas de renderização</span><span class="sxs-lookup"><span data-stu-id="4f4df-117">Rendering particles</span></span>

<span data-ttu-id="4f4df-118">CPUs atuais são ótimos para processar tarefas seriais e até algumas tarefas em paralelo ao mesmo tempo (dependendo de quantos núcleos tiverem), mas as GPUs são muito mais eficazes na processar milhares de operações em paralelo.</span><span class="sxs-lookup"><span data-stu-id="4f4df-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="4f4df-119">No entanto, porque eles geralmente não compartilham a mesma memória da CPU, troca de dados entre a CPU <> GPU pode rapidamente se tornar um gargalo.</span><span class="sxs-lookup"><span data-stu-id="4f4df-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="4f4df-120">Nossa solução foi fazer uma galáxia na GPU e precisava viver completamente na GPU.</span><span class="sxs-lookup"><span data-stu-id="4f4df-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="4f4df-121">Começamos a testes de estresse com milhares de partículas de ponto em vários padrões.</span><span class="sxs-lookup"><span data-stu-id="4f4df-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="4f4df-122">Isso nos permitiu obter o galaxy no HoloLens para ver o que funcionou e o que não funcionou.</span><span class="sxs-lookup"><span data-stu-id="4f4df-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="4f4df-123">Criando a posição das estrelas</span><span class="sxs-lookup"><span data-stu-id="4f4df-123">Creating the position of the stars</span></span>

<span data-ttu-id="4f4df-124">Um dos nossos membros de equipe já tinha escrito o C# código que geraria estrelas em sua posição inicial.</span><span class="sxs-lookup"><span data-stu-id="4f4df-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="4f4df-125">As estrelas são em uma elipse e sua posição pode ser descrita por (**curveOffset**, **ellipseSize**, **elevação**) onde **curveOffset**é o ângulo da estrela junto a elipse **ellipseSize** é a dimensão da elipse ao longo de X e Z e a elevação adequada da estrela dentro das galáxias de elevação.</span><span class="sxs-lookup"><span data-stu-id="4f4df-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="4f4df-126">Assim, podemos criar um buffer ([ComputeBuffer do Unity](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) que deve ser inicializado com cada atributo em estrela e enviá-lo na GPU em que faria ao vivo para o restante da experiência.</span><span class="sxs-lookup"><span data-stu-id="4f4df-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="4f4df-127">Para desenhar esse buffer, usamos [DrawProcedural do Unity](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) que permite executar um sombreador (código em uma GPU) em um conjunto arbitrário de pontos sem a necessidade de uma malha real que representa o galaxy:</span><span class="sxs-lookup"><span data-stu-id="4f4df-127">To draw this buffer, we use [Unity’s DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="4f4df-128">**CPU:**</span><span class="sxs-lookup"><span data-stu-id="4f4df-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="4f4df-129">**GPU:**</span><span class="sxs-lookup"><span data-stu-id="4f4df-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="4f4df-130">Começamos com padrões circulares brutos com milhares de partículas.</span><span class="sxs-lookup"><span data-stu-id="4f4df-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="4f4df-131">Isso nos deu a prova de que precisávamos que poderíamos gerenciar muitos partículas e executá-lo em velocidades de alto desempenho, mas não foi satisfeitos com a forma geral do galaxy.</span><span class="sxs-lookup"><span data-stu-id="4f4df-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="4f4df-132">Para melhorar a forma, tentamos vários padrões e sistemas de partículas com rotação.</span><span class="sxs-lookup"><span data-stu-id="4f4df-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="4f4df-133">Elas eram inicialmente promissoras, cometendo porque o número de partículas e desempenho permanecia consistente, mas a forma dividiu perto do centro e estrelas estavam emitindo externamente que não era realista.</span><span class="sxs-lookup"><span data-stu-id="4f4df-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="4f4df-134">Precisávamos de uma emissão que nos manipular o tempo e ter as partículas mover na verdade, um loop nunca mais próximo ao centro do galaxy.</span><span class="sxs-lookup"><span data-stu-id="4f4df-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![Tentamos vários padrões e sistemas de partículas girado, como esses.](images/galaxy-patterns-500px.png)

<span data-ttu-id="4f4df-136">Tentamos vários padrões e sistemas de partículas girado, como esses.</span><span class="sxs-lookup"><span data-stu-id="4f4df-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="4f4df-137">Nossa equipe fez algumas pesquisas sobre a função de maneira galáxias e fizemos um sistema de partículas personalizadas especificamente para o galaxy para que poderia passar as partículas elipses com base em "[teoria de ondas de densidade](https://en.wikipedia.org/wiki/Density_wave_theory)," que theorizes que o alerta de um Galaxy são áreas de densidade mais alta, mas em fluxo constante, como um congestionamento no tráfego.</span><span class="sxs-lookup"><span data-stu-id="4f4df-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="4f4df-138">Ele aparece sólida e estável, mas as estrelas são, na verdade, saem de braços quando eles passam ao longo de seus respectivos elipses.</span><span class="sxs-lookup"><span data-stu-id="4f4df-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="4f4df-139">Em nosso sistema, as partículas nunca existirem na CPU, podemos gerar os cartões e orientá-los todos na GPU, portanto, todo o sistema é o estado inicial simplesmente + tempo.</span><span class="sxs-lookup"><span data-stu-id="4f4df-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="4f4df-140">Ele avançava como este:</span><span class="sxs-lookup"><span data-stu-id="4f4df-140">It progressed like this:</span></span>

![Progressão do sistema de partículas com a renderização de GPU](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="4f4df-142">Progressão do sistema de partículas com a renderização de GPU</span><span class="sxs-lookup"><span data-stu-id="4f4df-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="4f4df-143">Depois que o suficiente elipses são adicionadas e são definidos como girar, as galáxias começaram a forma "braços" em que a movimentação de estrelas convergir.</span><span class="sxs-lookup"><span data-stu-id="4f4df-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="4f4df-144">O espaçamento das estrelas ao longo de cada caminho elíptico foi fornecido um pouco da aleatoriedade, e cada estrela ficou um pouco da aleatoriedade posicional adicionado.</span><span class="sxs-lookup"><span data-stu-id="4f4df-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="4f4df-145">Isso criou uma distribuição de aparência muito mais natural de forma de estrela movimentação e arm.</span><span class="sxs-lookup"><span data-stu-id="4f4df-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="4f4df-146">Por fim, adicionamos a capacidade para a cor com base na distância do centro da unidade.</span><span class="sxs-lookup"><span data-stu-id="4f4df-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="4f4df-147">Criando o movimento das estrelas</span><span class="sxs-lookup"><span data-stu-id="4f4df-147">Creating the motion of the stars</span></span>

<span data-ttu-id="4f4df-148">Para animar o movimento de estrela geral, precisávamos para adicionar um ângulo de constante para cada quadro e obter estrelas movendo seus elipses a uma velocidade constante de radial.</span><span class="sxs-lookup"><span data-stu-id="4f4df-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="4f4df-149">Isso é o principal motivo para usar **curveOffset**.</span><span class="sxs-lookup"><span data-stu-id="4f4df-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="4f4df-150">Isso não é tecnicamente correto, como estrelas moverá mais rapidamente ao longo dos lados longo das elipses, mas o movimento geral sentimos BOM.</span><span class="sxs-lookup"><span data-stu-id="4f4df-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![Estrelas Avançar mais rápido do arco longo, mais lentas nas bordas.](images/ellipse-movement.jpg)

<span data-ttu-id="4f4df-152">Estrelas Avançar mais rápido do arco longo, mais lentas nas bordas.</span><span class="sxs-lookup"><span data-stu-id="4f4df-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="4f4df-153">Com isso, cada estrela é totalmente descrita por (**curveOffset**, **ellipseSize**, **elevação**, **idade**) onde **idade** é um acúmulo do tempo total decorrido desde a cena foi carregada.</span><span class="sxs-lookup"><span data-stu-id="4f4df-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

<span data-ttu-id="4f4df-154">Isso nos permitiu gerar dezenas de milhares de estrelas, uma vez no início do aplicativo e, em seguida, estamos animados um conjunto a de estrelas curvas estabelecido.</span><span class="sxs-lookup"><span data-stu-id="4f4df-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="4f4df-155">Como tudo o que é na GPU, o sistema pode animar estrelas em paralelo sem nenhum custo para a CPU.</span><span class="sxs-lookup"><span data-stu-id="4f4df-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![Aqui está o que se parece ao desenhar quadrados em branco.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="4f4df-157">Aqui está o que se parece ao desenhar quadrados em branco.</span><span class="sxs-lookup"><span data-stu-id="4f4df-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="4f4df-158">Para tornar cada face quad a câmera, usamos um sombreador de geometria para transformar cada posição estrela a um retângulo 2D na tela que conterá nosso textura em estrela.</span><span class="sxs-lookup"><span data-stu-id="4f4df-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![Losangos, em vez de quadrados.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="4f4df-160">Losangos, em vez de quadrados.</span><span class="sxs-lookup"><span data-stu-id="4f4df-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="4f4df-161">Porque queríamos limitar os excedentes (número de vezes que um pixel será processado) tanto quanto possível, podemos girado nosso quadrados para que elas podem ter menos sobreposição.</span><span class="sxs-lookup"><span data-stu-id="4f4df-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="4f4df-162">Adicionando nuvens</span><span class="sxs-lookup"><span data-stu-id="4f4df-162">Adding clouds</span></span>

<span data-ttu-id="4f4df-163">Há várias maneiras para obter uma sensação volumétricas com partículas — de ray caminhando dentro de um volume ao desenho de partículas tantos quanto possível para simular uma nuvem.</span><span class="sxs-lookup"><span data-stu-id="4f4df-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="4f4df-164">Ray em tempo real caminhando estava prestes a ser muito caro e difícil de autor, por isso, tentamos primeiro criar um sistema de impostor usando um método para florestas de renderização em jogos — com uma grande quantidade de imagens 2D das árvores voltados para a câmera.</span><span class="sxs-lookup"><span data-stu-id="4f4df-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="4f4df-165">Quando fazemos isso em um jogo, podemos pode ter texturas de árvores processadas a partir de uma câmera que gira em torno de, salve todas essas imagens e em tempo de execução para cada cartão de mensagem de instalação, selecione a imagem que corresponde a direção da exibição.</span><span class="sxs-lookup"><span data-stu-id="4f4df-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="4f4df-166">Isso não funciona bem quando as imagens são hologramas.</span><span class="sxs-lookup"><span data-stu-id="4f4df-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="4f4df-167">A diferença entre o olho à esquerda e direita olhos torná-lo, de modo que precisamos de uma resolução muito maior, caso contrário, apenas parece simples, um alias ou repetitivas.</span><span class="sxs-lookup"><span data-stu-id="4f4df-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="4f4df-168">Em nossa segunda tentativa, tentamos tendo partículas tantos quanto possível.</span><span class="sxs-lookup"><span data-stu-id="4f4df-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="4f4df-169">Os visuais melhores foram atingidos ao fogo desenhou partículas e desfocada-los antes de adicioná-los para a cena.</span><span class="sxs-lookup"><span data-stu-id="4f4df-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="4f4df-170">Os problemas típicos com essa abordagem foram partículas relacionadas a quantos nós poderia desenhar em uma única vez e tela quanto a área cobertos por eles e ainda manter a 60fps.</span><span class="sxs-lookup"><span data-stu-id="4f4df-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="4f4df-171">Desfoque a imagem resultante para obter esta nuvem está se sentindo costumava ser uma operação muito cara.</span><span class="sxs-lookup"><span data-stu-id="4f4df-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![Sem textura, isso é a aparência de nuvens com opacidade de % 2.](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="4f4df-173">Sem textura, isso é a aparência de nuvens com opacidade de % 2.</span><span class="sxs-lookup"><span data-stu-id="4f4df-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="4f4df-174">Sendo aditivas e ter uma grande quantidade deles significa que teríamos que vários quadrados sobre a outra, sombreamento repetidamente o mesmo pixel.</span><span class="sxs-lookup"><span data-stu-id="4f4df-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="4f4df-175">No centro do galaxy, o mesmo pixel tem centenas de quadrados umas sobre as outras e isso tinha um enorme custo ao que está sendo feito a tela inteira.</span><span class="sxs-lookup"><span data-stu-id="4f4df-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="4f4df-176">Fazendo nuvens de tela inteira e tentando desfoque-los seria uma boa ideia, então, em vez disso, que decidimos permitir que o hardware de fazer o trabalho para nós.</span><span class="sxs-lookup"><span data-stu-id="4f4df-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="4f4df-177">Um pouco de contexto pela primeira vez</span><span class="sxs-lookup"><span data-stu-id="4f4df-177">A bit of context first</span></span>

<span data-ttu-id="4f4df-178">Ao usar texturas em um jogo o tamanho da textura raramente corresponderá a área que desejamos usá-lo no, mas podemos usar diferentes tipos de filtragem para obter a placa gráfica para interpolar a cor que queremos por meio de pixels da textura de textura ([filtragemdetextura](https://msdn.microsoft.com/library/dn642451.aspx)).</span><span class="sxs-lookup"><span data-stu-id="4f4df-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="4f4df-179">É a filtragem de seu interesse nos [filtragem bilinear](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) que irá calcular o valor de qualquer pixel usando o 4 vizinhos.</span><span class="sxs-lookup"><span data-stu-id="4f4df-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![Original antes de filtragem](images/texture-1.png)

![Resultado após a filtragem](images/texture-2.png)

<span data-ttu-id="4f4df-182">Usando essa propriedade, podemos ver que cada vez que tentarmos desenhe uma textura em uma área duas vezes tão grande, ele Desfoca o resultado.</span><span class="sxs-lookup"><span data-stu-id="4f4df-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="4f4df-183">Em vez de renderização em tela inteira e perder esses milissegundos preciosos que poderia estar gastando em algo mais, podemos processar para uma pequena versão da tela.</span><span class="sxs-lookup"><span data-stu-id="4f4df-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="4f4df-184">Em seguida, copiando dessa textura e ampliá-la várias vezes por um fator de 2, obtivemos para tela inteira ao desfocar o conteúdo no processo.</span><span class="sxs-lookup"><span data-stu-id="4f4df-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![X3 passarem para uma solução completa.](images/galaxy-resolutions-300px.png)

<span data-ttu-id="4f4df-186">X3 passarem para uma solução completa.</span><span class="sxs-lookup"><span data-stu-id="4f4df-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="4f4df-187">Isso nos permitiu obter a parte de nuvem com apenas uma fração do custo original.</span><span class="sxs-lookup"><span data-stu-id="4f4df-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="4f4df-188">Em vez de adicionar nuvens a resolução completa, estamos apenas paint 1/64 dos pixels e apenas alongar a textura de volta para uma solução completa.</span><span class="sxs-lookup"><span data-stu-id="4f4df-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![À esquerda, com um luxuoso de 1/8 à resolução total; e à direita, com 3 luxuoso usando potência de 2.](images/stars-upscaled-300px.jpg)

<span data-ttu-id="4f4df-190">À esquerda, com um luxuoso de 1/8 à resolução total; e à direita, com 3 luxuoso usando potência de 2.</span><span class="sxs-lookup"><span data-stu-id="4f4df-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="4f4df-191">Observe que tentar ir de 1/64 do tamanho para todo o tamanho de uma só vez seria completamente diferente, como a placa gráfica ainda seria usar 4 pixels em nossa configuração para sombrear uma área maior e artefatos comecem a aparecer.</span><span class="sxs-lookup"><span data-stu-id="4f4df-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="4f4df-192">Em seguida, se adicionarmos estrelas de alta resolução com cartões menores, obtemos o galaxy completo:</span><span class="sxs-lookup"><span data-stu-id="4f4df-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![Próximo resultado final de renderização de galaxy usando estrelas de alta resolução](images/full-galaxy-500px.png)

<span data-ttu-id="4f4df-194">Depois que o chamássemos no caminho certo com a forma, adicionamos uma camada de nuvens, permutado nos pontos temporários com aquelas podemos pintada no Photoshop e adicionou alguns adicionais de cor.</span><span class="sxs-lookup"><span data-stu-id="4f4df-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="4f4df-195">O resultado foi uma galáxia Láctea nosso arte e ambas as equipes de engenharia sentiram boa sobre e ela superou nossas metas de profundidade, volume e movimentos de ter — tudo sem sobrecarregar a CPU.</span><span class="sxs-lookup"><span data-stu-id="4f4df-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![Nosso Galaxy Láctea final em 3D.](images/final-galaxy-500px.jpg)

<span data-ttu-id="4f4df-197">Nosso Galaxy Láctea final em 3D.</span><span class="sxs-lookup"><span data-stu-id="4f4df-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="4f4df-198">Mais para explorar</span><span class="sxs-lookup"><span data-stu-id="4f4df-198">More to explore</span></span>

<span data-ttu-id="4f4df-199">Nós o código para o aplicativo Galaxy Explorer de software livre e disponibilizados no [GitHub](https://github.com/Microsoft/GalaxyExplorer) que os desenvolvedores criem.</span><span class="sxs-lookup"><span data-stu-id="4f4df-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="4f4df-200">Você está interessado em descobrir mais sobre o processo de desenvolvimento para o Galaxy Explorer?</span><span class="sxs-lookup"><span data-stu-id="4f4df-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="4f4df-201">Fazer check-out de todas as nossas atualizações de projeto passado na [canal do YouTube do Microsoft HoloLens](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span><span class="sxs-lookup"><span data-stu-id="4f4df-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="4f4df-202">Sobre os autores</span><span class="sxs-lookup"><span data-stu-id="4f4df-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="4f4df-203"><b>Karim Luccin</b> é engenheiro de Software e entusiasta visuais sofisticados.</span><span class="sxs-lookup"><span data-stu-id="4f4df-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="4f4df-204">Ele era o engenheiro de gráficos para o Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="4f4df-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="4f4df-205"><b>Andy Zibits</b> é um Lead arte e espaço entusiasta gerenciado a equipe de modelagem 3D para o Galaxy Explorer e teve problemas para partículas ainda mais.</span><span class="sxs-lookup"><span data-stu-id="4f4df-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="4f4df-206">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f4df-206">See also</span></span>
* [<span data-ttu-id="4f4df-207">Explorer Galaxy no GitHub</span><span class="sxs-lookup"><span data-stu-id="4f4df-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="4f4df-208">Atualizações do projeto Galaxy Explorer no YouTube</span><span class="sxs-lookup"><span data-stu-id="4f4df-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
