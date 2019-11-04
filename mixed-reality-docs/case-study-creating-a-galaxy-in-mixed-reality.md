---
title: Estudo de caso-criando um Galaxy em realidade misturada
description: Antes de o Microsoft HoloLens ser enviado, pedimos à nossa comunidade de desenvolvedores que tipo de aplicativo gostaria de ver um Build de equipe interno experiente para o novo dispositivo. Mais de 5000 ideias foram compartilhadas e, após uma sondagem do Twitter de 24 horas, o vencedor foi uma ideia chamada "Galaxy Explorer".
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, realidade mista do Windows, compartilhe sua ideia, estudo de caso
ms.openlocfilehash: 696662eb92371708389f8a128dcee6a61acf1816
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436876"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="328b0-105">Estudo de caso-criando um Galaxy em realidade misturada</span><span class="sxs-lookup"><span data-stu-id="328b0-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="328b0-106">Antes de o Microsoft HoloLens ser enviado, pedimos à nossa comunidade de desenvolvedores que tipo de aplicativo gostaria de ver um Build de equipe interno experiente para o novo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="328b0-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="328b0-107">Mais de 5000 ideias foram compartilhadas e, após uma sondagem do Twitter de 24 horas, o vencedor foi uma ideia chamada [Galaxy Explorer](galaxy-explorer.md).</span><span class="sxs-lookup"><span data-stu-id="328b0-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="328b0-108">Andy Zibits, líder de arte do projeto e Karim Luccin, engenheiro de gráficos da equipe, conversa sobre o esforço colaborativo entre arte e engenharia que levaram à criação de uma representação precisa e interativa da forma de leite do Galaxy no Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="328b0-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="328b0-109">O Tech</span><span class="sxs-lookup"><span data-stu-id="328b0-109">The Tech</span></span>

<span data-ttu-id="328b0-110">[Nossa equipe](galaxy-explorer.md#meet-the-team) , composta por dois designers, três desenvolvedores, quatro artistas, um produtor e um testador, tinha seis semanas para criar um aplicativo totalmente funcional que permitiria que as pessoas aprendessem e explorassem a grande vantagem e a beleza de nossa maneira de leite.</span><span class="sxs-lookup"><span data-stu-id="328b0-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="328b0-111">Queríamos aproveitar ao máximo a capacidade do HoloLens de processar objetos 3D diretamente em seu espaço de vida, então decidimos que queríamos criar um Galaxy de aparência realista, em que as pessoas poderiam ampliar e ver as estrelas individuais, cada uma em suas próprias trajetórias .</span><span class="sxs-lookup"><span data-stu-id="328b0-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="328b0-112">Na primeira semana do desenvolvimento, nós reunimos algumas metas para nossa representação da nossa forma de leite: a ti precisava ter profundidade, movimento e sensação de volumétricos – cheia de estrelas que ajudam a criar a forma do Galaxy.</span><span class="sxs-lookup"><span data-stu-id="328b0-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="328b0-113">O problema da criação de um Galaxy animado que tinha bilhões de estrelas era que o número enorme de elementos únicos que precisam de atualização seria muito grande por quadro para o HoloLens animar usando a CPU.</span><span class="sxs-lookup"><span data-stu-id="328b0-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="328b0-114">Nossa solução envolvia uma mistura complexa de arte e ciência.</span><span class="sxs-lookup"><span data-stu-id="328b0-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="328b0-115">Nos bastidores</span><span class="sxs-lookup"><span data-stu-id="328b0-115">Behind the scenes</span></span>

<span data-ttu-id="328b0-116">Para permitir que as pessoas explorem estrelas individuais, nossa primeira etapa foi descobrir quantas partículas poderíamos renderizar de uma vez.</span><span class="sxs-lookup"><span data-stu-id="328b0-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="328b0-117">Partículas de renderização</span><span class="sxs-lookup"><span data-stu-id="328b0-117">Rendering particles</span></span>

<span data-ttu-id="328b0-118">As CPUs atuais são ótimas para processar tarefas seriais e até algumas tarefas paralelas de uma vez (dependendo de quantos núcleos eles têm), mas as GPUs são muito mais eficientes no processamento de milhares de operações em paralelo.</span><span class="sxs-lookup"><span data-stu-id="328b0-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="328b0-119">No entanto, como normalmente não compartilham a mesma memória que a CPU, a troca de dados entre a CPU < > GPU pode rapidamente se tornar um afunilamento.</span><span class="sxs-lookup"><span data-stu-id="328b0-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="328b0-120">Nossa solução era fazer um Galaxy na GPU e precisava viver completamente na GPU.</span><span class="sxs-lookup"><span data-stu-id="328b0-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="328b0-121">Começamos testes de estresse com milhares de partículas de ponto em vários padrões.</span><span class="sxs-lookup"><span data-stu-id="328b0-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="328b0-122">Isso nos permitiu obter o Galaxy no HoloLens para ver o que funcionou e o que não funcionou.</span><span class="sxs-lookup"><span data-stu-id="328b0-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="328b0-123">Criando a posição das estrelas</span><span class="sxs-lookup"><span data-stu-id="328b0-123">Creating the position of the stars</span></span>

<span data-ttu-id="328b0-124">Um dos nossos membros da equipe já escreveu o C# código que geraria estrelas em sua posição inicial.</span><span class="sxs-lookup"><span data-stu-id="328b0-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="328b0-125">As estrelas estão em uma elipse e sua posição pode ser descrita por (**curveOffset**, **ellipseSize**, **elevação**), em que **curveOffset** é o ângulo da estrela ao longo da elipse, **ellipseSize** é a dimensão da elipse ao longo de X e Z, e elevação da elevação adequada da estrela no Galaxy.</span><span class="sxs-lookup"><span data-stu-id="328b0-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="328b0-126">Assim, podemos criar um buffer ([ComputeBuffer do Unity](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) que seria inicializado com cada atributo Star e enviá-lo na GPU onde ele residiria para o restante da experiência.</span><span class="sxs-lookup"><span data-stu-id="328b0-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="328b0-127">Para desenhar esse buffer, usamos o [DrawProcedural do Unity](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) , que permite executar um sombreador (código em uma GPU) em um conjunto arbitrário de pontos sem ter uma malha real que represente o Galaxy:</span><span class="sxs-lookup"><span data-stu-id="328b0-127">To draw this buffer, we use [Unity’s DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="328b0-128">**CPUs**</span><span class="sxs-lookup"><span data-stu-id="328b0-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="328b0-129">**GPU**</span><span class="sxs-lookup"><span data-stu-id="328b0-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="328b0-130">Começamos com padrões circulares brutos com milhares de partículas.</span><span class="sxs-lookup"><span data-stu-id="328b0-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="328b0-131">Isso nos proporcionou a prova de que precisávamos gerenciar várias partículas e executá-la em velocidades de desempenho, mas não estamos satisfeitos com a forma geral do Galaxy.</span><span class="sxs-lookup"><span data-stu-id="328b0-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="328b0-132">Para melhorar a forma, tentamos vários padrões e sistemas de partículas com rotação.</span><span class="sxs-lookup"><span data-stu-id="328b0-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="328b0-133">Inicialmente, esses eram promissores porque o número de partículas e o desempenho permaneciam consistentes, mas a forma é desligada perto do centro e as estrelas estavam sendo emitidas de maneira retroativa, o que não era realista.</span><span class="sxs-lookup"><span data-stu-id="328b0-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="328b0-134">Precisávamos de uma emissão que nos permitisse manipular o tempo e fazer com que as partículas se movam de forma realista, fazendo um loop mais próximo do centro do Galaxy.</span><span class="sxs-lookup"><span data-stu-id="328b0-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![Tentamos vários padrões e sistemas de partículas que giramos, como esses.](images/galaxy-patterns-500px.png)

<span data-ttu-id="328b0-136">Tentamos vários padrões e sistemas de partículas que giramos, como esses.</span><span class="sxs-lookup"><span data-stu-id="328b0-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="328b0-137">Nossa equipe fez alguma pesquisa sobre a maneira como a função Galaxies e criamos um sistema de partículas personalizado especificamente para o Galaxy para que possamos mover as partículas em elipses com base na "[teoria de onda de densidade](https://en.wikipedia.org/wiki/Density_wave_theory)", que theorizes que os braços de um Galaxy são áreas de maior densidade, mas em fluxo constante, como uma obstrução de tráfego.</span><span class="sxs-lookup"><span data-stu-id="328b0-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="328b0-138">Ele parece estável e sólido, mas as estrelas estão, na verdade, passando para dentro e para fora dos braços à medida que eles se movem ao longo de suas respectivas elipses.</span><span class="sxs-lookup"><span data-stu-id="328b0-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="328b0-139">Em nosso sistema, as partículas nunca existem na CPU — geramos os cartões e os orientamos todos na GPU, de modo que o sistema inteiro é simplesmente estado inicial + tempo.</span><span class="sxs-lookup"><span data-stu-id="328b0-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="328b0-140">Ele progrediu da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="328b0-140">It progressed like this:</span></span>

![Progressão do sistema de partículas com renderização de GPU](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="328b0-142">Progressão do sistema de partículas com renderização de GPU</span><span class="sxs-lookup"><span data-stu-id="328b0-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="328b0-143">Depois que as reticências suficientes são adicionadas e definidas para girar, o Galaxies começou a formar "braços" onde a movimentação de estrelas é convergida.</span><span class="sxs-lookup"><span data-stu-id="328b0-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="328b0-144">O espaçamento das estrelas ao longo de cada caminho elíptico recebeu alguma aleatoriedade, e cada estrela tinha um pouco de aleatoriedade posicional adicionada.</span><span class="sxs-lookup"><span data-stu-id="328b0-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="328b0-145">Isso criou uma distribuição de aparência muito mais natural do movimento de estrela e da forma ARM.</span><span class="sxs-lookup"><span data-stu-id="328b0-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="328b0-146">Por fim, adicionamos a capacidade de impulsionar a cor com base na distância do centro.</span><span class="sxs-lookup"><span data-stu-id="328b0-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="328b0-147">Criando o movimento das estrelas</span><span class="sxs-lookup"><span data-stu-id="328b0-147">Creating the motion of the stars</span></span>

<span data-ttu-id="328b0-148">Para animar o movimento de estrela geral, precisávamos adicionar um ângulo constante para cada quadro e fazer com que as estrelas se movimentem ao longo de suas reticências a uma velocidade radial constante.</span><span class="sxs-lookup"><span data-stu-id="328b0-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="328b0-149">Esse é o principal motivo para usar o **curveOffset**.</span><span class="sxs-lookup"><span data-stu-id="328b0-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="328b0-150">Isso não é tecnicamente correto, pois as estrelas se moverão mais rapidamente ao longo dos lados longos das reticências, mas o movimento geral parecia bom.</span><span class="sxs-lookup"><span data-stu-id="328b0-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![As estrelas se movem mais rapidamente no arco longo, mais devagar nas bordas.](images/ellipse-movement.jpg)

<span data-ttu-id="328b0-152">As estrelas se movem mais rapidamente no arco longo, mais devagar nas bordas.</span><span class="sxs-lookup"><span data-stu-id="328b0-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="328b0-153">Com isso, cada estrela é totalmente descrita por (**curveOffset**, **ellipseSize**, **elevação**, **idade**), em que **age** é uma acumulação do tempo total que passou desde que a cena foi carregada.</span><span class="sxs-lookup"><span data-stu-id="328b0-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




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

<span data-ttu-id="328b0-154">Isso nos permitiu gerar dezenas de milhares de estrelas uma vez no início do aplicativo e, em seguida, animamos um conjunto único de estrelas ao longo das curvas estabelecidas.</span><span class="sxs-lookup"><span data-stu-id="328b0-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="328b0-155">Como tudo está na GPU, o sistema pode animar todas as estrelas em paralelo sem nenhum custo para a CPU.</span><span class="sxs-lookup"><span data-stu-id="328b0-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![A aparência é semelhante ao desenho de quatro processadores brancos.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="328b0-157">A aparência é semelhante ao desenho de quatro processadores brancos.</span><span class="sxs-lookup"><span data-stu-id="328b0-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="328b0-158">Para fazer com que cada Quad face a câmera, usamos um sombreador Geometry para transformar cada posição de estrela em um retângulo 2D na tela que conterá nossa textura em estrela.</span><span class="sxs-lookup"><span data-stu-id="328b0-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![Ouros em vez de quádruplos.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="328b0-160">Ouros em vez de quádruplos.</span><span class="sxs-lookup"><span data-stu-id="328b0-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="328b0-161">Como queríamos limitar o excesso de empates (número de vezes que um pixel será processado) o máximo possível, nós giramos nossos quatro processadores para que eles tenham menos sobreposição.</span><span class="sxs-lookup"><span data-stu-id="328b0-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="328b0-162">Adicionando nuvens</span><span class="sxs-lookup"><span data-stu-id="328b0-162">Adding clouds</span></span>

<span data-ttu-id="328b0-163">Há várias maneiras de obter uma sensação volumétricos com partículas, de raio de março dentro de um volume para desenhar o máximo de partículas possível para simular uma nuvem.</span><span class="sxs-lookup"><span data-stu-id="328b0-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="328b0-164">O raio de março em tempo real seria muito caro e difícil de criar, portanto, primeiro tentamos criar um sistema impostor usando um método para renderizar florestas em jogos, com muitas imagens 2D de árvores voltadas para a câmera.</span><span class="sxs-lookup"><span data-stu-id="328b0-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="328b0-165">Quando fazemos isso em um jogo, podemos ter texturas de árvores renderizadas de uma câmera que gira em direção, salvar todas essas imagens e, em tempo de execução para cada cartão de mensagem, selecionar a imagem que corresponde à direção da exibição.</span><span class="sxs-lookup"><span data-stu-id="328b0-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="328b0-166">Isso não funciona tão bem quando as imagens são hologramas.</span><span class="sxs-lookup"><span data-stu-id="328b0-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="328b0-167">A diferença entre os olhos à esquerda e o direito de fazer isso é que precisamos de uma resolução muito maior, ou simplesmente parece simples, com alias ou repetitivo.</span><span class="sxs-lookup"><span data-stu-id="328b0-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="328b0-168">Na segunda tentativa, tentamos ter o máximo de partículas possível.</span><span class="sxs-lookup"><span data-stu-id="328b0-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="328b0-169">Os melhores elementos visuais foram obtidos quando desenhamos as partículas e as desfoquei antes de adicioná-las à cena.</span><span class="sxs-lookup"><span data-stu-id="328b0-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="328b0-170">Os problemas típicos dessa abordagem estavam relacionados à quantidade de partículas que poderíamos desenhar em um único momento e na quantidade de área de tela coberta e, ao mesmo tempo, manter o 60fps.</span><span class="sxs-lookup"><span data-stu-id="328b0-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="328b0-171">Desfocar a imagem resultante para obter essa sensação de nuvem normalmente era uma operação muito dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="328b0-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![Sem textura, é assim que as nuvens se pareceriam com uma opacidade de 2%.](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="328b0-173">Sem textura, é assim que as nuvens se pareceriam com uma opacidade de 2%.</span><span class="sxs-lookup"><span data-stu-id="328b0-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="328b0-174">Ser aditivo e ter muitos deles significa que teríamos vários quatro quádruplos sobre os outros, sombreando repetidamente o mesmo pixel.</span><span class="sxs-lookup"><span data-stu-id="328b0-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="328b0-175">No centro do Galaxy, o mesmo pixel tem centenas de quatro quádruplos em cima um do outro, e isso tinha um enorme custo ao ser feito em tela inteira.</span><span class="sxs-lookup"><span data-stu-id="328b0-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="328b0-176">Fazer nuvens de tela inteira e tentar desfocar elas teria sido uma má ideia, então decidimos deixar o hardware fazer o trabalho para nós.</span><span class="sxs-lookup"><span data-stu-id="328b0-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="328b0-177">Primeiro um pouco de contexto</span><span class="sxs-lookup"><span data-stu-id="328b0-177">A bit of context first</span></span>

<span data-ttu-id="328b0-178">Ao usar texturas em um jogo, o tamanho da textura raramente corresponderá à área em que desejamos usá-la, mas podemos usar um tipo diferente de filtragem de textura para obter o cartão gráfico para interpolar a cor que desejamos dos pixels da textura ([filtragem de textura](https://msdn.microsoft.com/library/dn642451.aspx)).</span><span class="sxs-lookup"><span data-stu-id="328b0-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="328b0-179">A filtragem que nos interessa é a [filtragem biline](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) , que calculará o valor de qualquer pixel usando os 4 vizinhos mais próximos.</span><span class="sxs-lookup"><span data-stu-id="328b0-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![Original antes da filtragem](images/texture-1.png)

![Resultado após a filtragem](images/texture-2.png)

<span data-ttu-id="328b0-182">Usando essa propriedade, vemos que cada vez que tentamos desenhar uma textura em uma área duas vezes maior, ela desfoca o resultado.</span><span class="sxs-lookup"><span data-stu-id="328b0-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="328b0-183">Em vez de renderizar para uma tela inteira e perder os preciosos milissegundos que poderíamos estar gastando em alguma outra coisa, renderizamos para uma pequena versão da tela.</span><span class="sxs-lookup"><span data-stu-id="328b0-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="328b0-184">Em seguida, copiando essa textura e esticando-a por um fator 2 várias vezes, obtemos a tela inteira enquanto desfocamos o conteúdo no processo.</span><span class="sxs-lookup"><span data-stu-id="328b0-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![dimensionamento do X3 de volta para a resolução completa.](images/galaxy-resolutions-300px.png)

<span data-ttu-id="328b0-186">dimensionamento do X3 de volta para a resolução completa.</span><span class="sxs-lookup"><span data-stu-id="328b0-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="328b0-187">Isso nos permitiu obter a parte da nuvem com apenas uma fração do custo original.</span><span class="sxs-lookup"><span data-stu-id="328b0-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="328b0-188">Em vez de adicionar nuvens na resolução completa, só pintamos 1/64th dos pixels e apenas alongamos a textura de volta para a resolução completa.</span><span class="sxs-lookup"><span data-stu-id="328b0-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![Esquerda, com uma escala de 1/8 para resolução completa; e para a direita, com 3 upscale usando a potência de 2.](images/stars-upscaled-300px.jpg)

<span data-ttu-id="328b0-190">Esquerda, com uma escala de 1/8 para resolução completa; e para a direita, com 3 upscale usando a potência de 2.</span><span class="sxs-lookup"><span data-stu-id="328b0-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="328b0-191">Observe que tentar ir de 1/64th do tamanho para o tamanho total em uma só vez pareceria completamente diferente, pois o cartão gráfico ainda usaria 4 pixels em nossa configuração para sombrear uma área maior e os artefatos começarão a aparecer.</span><span class="sxs-lookup"><span data-stu-id="328b0-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="328b0-192">Em seguida, se adicionarmos estrelas de resolução completa com cartões menores, obteremos o Galaxy completo:</span><span class="sxs-lookup"><span data-stu-id="328b0-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![Resultado quase final da renderização do Galaxy usando estrelas de resolução completa](images/full-galaxy-500px.png)

<span data-ttu-id="328b0-194">Depois de termos o controle certo com a forma, adicionamos uma camada de nuvens, trocamos os pontos temporários por aqueles que pintamos no Photoshop e adicionamos alguma cor adicional.</span><span class="sxs-lookup"><span data-stu-id="328b0-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="328b0-195">O resultado foi uma forma de leite com as quais as equipes de arte e engenharia se sentiram bons e atendemos às nossas metas de ter profundidade, volume e movimento, tudo isso sem contorno da CPU.</span><span class="sxs-lookup"><span data-stu-id="328b0-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![Nossa maneira de leite final do Galaxy em 3D.](images/final-galaxy-500px.jpg)

<span data-ttu-id="328b0-197">Nossa maneira de leite final do Galaxy em 3D.</span><span class="sxs-lookup"><span data-stu-id="328b0-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="328b0-198">Mais para explorar</span><span class="sxs-lookup"><span data-stu-id="328b0-198">More to explore</span></span>

<span data-ttu-id="328b0-199">Abrimos o código do aplicativo Galaxy Explorer e o disponibilizamos no [GitHub](https://github.com/Microsoft/GalaxyExplorer) para que os desenvolvedores se criem.</span><span class="sxs-lookup"><span data-stu-id="328b0-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="328b0-200">Interessado em saber mais sobre o processo de desenvolvimento do Galaxy Explorer?</span><span class="sxs-lookup"><span data-stu-id="328b0-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="328b0-201">Confira todas as nossas atualizações de projeto passadas no [canal do YouTube do Microsoft HoloLens](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span><span class="sxs-lookup"><span data-stu-id="328b0-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="328b0-202">Sobre os autores</span><span class="sxs-lookup"><span data-stu-id="328b0-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="328b0-203"><b>Karim Luccin</b> é engenheiro de software e entusiasta de visuais sofisticados.</span><span class="sxs-lookup"><span data-stu-id="328b0-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="328b0-204">Ele foi engenheiro de gráficos do Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="328b0-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="328b0-205"><b>Andy Zibits</b> é um líder de arte e entusiasta de espaço que gerenciava a equipe de modelagem 3D para o Galaxy Explorer e o lutaram para obter ainda mais partículas.</span><span class="sxs-lookup"><span data-stu-id="328b0-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="328b0-206">Consulte também</span><span class="sxs-lookup"><span data-stu-id="328b0-206">See also</span></span>
* [<span data-ttu-id="328b0-207">Gerenciador do Galaxy no GitHub</span><span class="sxs-lookup"><span data-stu-id="328b0-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="328b0-208">Atualizações de projeto do Galaxy Explorer no YouTube</span><span class="sxs-lookup"><span data-stu-id="328b0-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
