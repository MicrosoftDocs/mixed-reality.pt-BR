---
title: Estudo de caso-criando um Galaxy em realidade misturada
description: Antes de o Microsoft HoloLens ser enviado, pedimos à nossa comunidade de desenvolvedores que tipo de aplicativo gostaria de ver um Build de equipe interno experiente para o novo dispositivo. Mais de 5000 ideias foram compartilhadas e, após uma sondagem do Twitter de 24 horas, o vencedor foi uma ideia chamada "Galaxy Explorer".
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, realidade mista do Windows, compartilhe sua ideia, estudo de caso
ms.openlocfilehash: f13395250c8a73718408c051ab95d2ec4bf62014
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278174"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>Estudo de caso-criando um Galaxy em realidade misturada

Antes de o Microsoft HoloLens ser enviado, pedimos à nossa comunidade de desenvolvedores que tipo de aplicativo gostaria de ver um Build de equipe interno experiente para o novo dispositivo. Mais de 5000 ideias foram compartilhadas e, após uma sondagem do Twitter de 24 horas, o vencedor foi uma ideia chamada [Galaxy Explorer](galaxy-explorer.md).

Andy Zibits, líder de arte do projeto e Karim Luccin, engenheiro de gráficos da equipe, conversa sobre o esforço colaborativo entre arte e engenharia que levaram à criação de uma representação precisa e interativa da forma de leite do Galaxy no Galaxy Explorer.

## <a name="the-tech"></a>O Tech

[Nossa equipe](galaxy-explorer.md#meet-the-team) , composta por dois designers, três desenvolvedores, quatro artistas, um produtor e um testador, tinha seis semanas para criar um aplicativo totalmente funcional que permitiria que as pessoas aprendessem e explorassem a grande vantagem e a beleza de nossa maneira de leite.

Queríamos aproveitar ao máximo a capacidade do HoloLens de processar objetos 3D diretamente em seu espaço de vida, então decidimos que queríamos criar um Galaxy de aparência realista, em que as pessoas poderiam ampliar e ver as estrelas individuais, cada uma em suas próprias trajetórias.

Na primeira semana do desenvolvimento, nós reunimos algumas metas para nossa representação da nossa forma de leite: a ti precisava ter profundidade, movimento e sensação de volumétricos – cheia de estrelas que ajudam a criar a forma do Galaxy.

O problema da criação de um Galaxy animado que tinha bilhões de estrelas era que o número enorme de elementos únicos que precisam de atualização seria muito grande por quadro para o HoloLens animar usando a CPU. Nossa solução envolvia uma mistura complexa de arte e ciência.

## <a name="behind-the-scenes"></a>Nos bastidores

Para permitir que as pessoas explorem estrelas individuais, nossa primeira etapa foi descobrir quantas partículas poderíamos renderizar de uma vez.

### <a name="rendering-particles"></a>Partículas de renderização

As CPUs atuais são ótimas para processar tarefas seriais e até algumas tarefas paralelas de uma vez (dependendo de quantos núcleos eles têm), mas as GPUs são muito mais eficientes no processamento de milhares de operações em paralelo. No entanto, como normalmente não compartilham a mesma memória que a CPU, a troca de dados entre a CPU < > GPU pode rapidamente se tornar um afunilamento. Nossa solução era fazer um Galaxy na GPU e precisava viver completamente na GPU.

Começamos testes de estresse com milhares de partículas de ponto em vários padrões. Isso nos permitiu obter o Galaxy no HoloLens para ver o que funcionou e o que não funcionou.

### <a name="creating-the-position-of-the-stars"></a>Criando a posição das estrelas

Um dos nossos membros da equipe já escreveu o C# código que geraria estrelas em sua posição inicial. As estrelas estão em uma elipse e sua posição pode ser descrita por (**curveOffset**, **ellipseSize**, **elevação**), em que **curveOffset** é o ângulo da estrela ao longo da elipse, **EllipseSize** é a dimensão da elipse ao longo de X e Z e elevação da elevação adequada da estrela no Galaxy. Assim, podemos criar um buffer ([ComputeBuffer do Unity](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) que seria inicializado com cada atributo Star e enviá-lo na GPU onde ele residiria para o restante da experiência. Para desenhar esse buffer, usamos o [DrawProcedural do Unity](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) , que permite executar um sombreador (código em uma GPU) em um conjunto arbitrário de pontos sem ter uma malha real que represente o Galaxy:

**CPUs**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

Começamos com padrões circulares brutos com milhares de partículas. Isso nos proporcionou a prova de que precisávamos gerenciar várias partículas e executá-la em velocidades de desempenho, mas não estamos satisfeitos com a forma geral do Galaxy. Para melhorar a forma, tentamos vários padrões e sistemas de partículas com rotação. Inicialmente, esses eram promissores porque o número de partículas e o desempenho permaneciam consistentes, mas a forma é desligada perto do centro e as estrelas estavam sendo emitidas de maneira retroativa, o que não era realista. Precisávamos de uma emissão que nos permitisse manipular o tempo e fazer com que as partículas se movam de forma realista, fazendo um loop mais próximo do centro do Galaxy.

![Tentamos vários padrões e sistemas de partículas que giramos, como esses.](images/galaxy-patterns-500px.png)

Tentamos vários padrões e sistemas de partículas que giramos, como esses.

Nossa equipe fez alguma pesquisa sobre a maneira como Galaxies a função e criamos um sistema de partículas personalizado especificamente para o Galaxy, para que possamos mover as partículas em elipses com base na "[teoria de ondas de densidade](https://en.wikipedia.org/wiki/Density_wave_theory)", que theorizes que os braços de um Galaxy são áreas de maior densidade, mas em fluxo constante, como uma obstrução de tráfego. Ele parece estável e sólido, mas as estrelas estão, na verdade, passando para dentro e para fora dos braços à medida que eles se movem ao longo de suas respectivas elipses. Em nosso sistema, as partículas nunca existem na CPU — geramos os cartões e os orientamos todos na GPU, de modo que o sistema inteiro é simplesmente estado inicial + tempo. Ele progrediu da seguinte maneira:

![Progressão do sistema de partículas com renderização de GPU](images/spiral-galaxy-arms-500px.jpg)

Progressão do sistema de partículas com renderização de GPU


Depois que as reticências suficientes são adicionadas e definidas para girar, o Galaxies começou a formar "braços" onde a movimentação de estrelas é convergida. O espaçamento das estrelas ao longo de cada caminho elíptico recebeu alguma aleatoriedade, e cada estrela tinha um pouco de aleatoriedade posicional adicionada. Isso criou uma distribuição de aparência muito mais natural do movimento de estrela e da forma ARM. Por fim, adicionamos a capacidade de impulsionar a cor com base na distância do centro.

### <a name="creating-the-motion-of-the-stars"></a>Criando o movimento das estrelas

Para animar o movimento de estrela geral, precisávamos adicionar um ângulo constante para cada quadro e fazer com que as estrelas se movimentem ao longo de suas reticências a uma velocidade radial constante. Esse é o principal motivo para usar o **curveOffset**. Isso não é tecnicamente correto, pois as estrelas se moverão mais rapidamente ao longo dos lados longos das reticências, mas o movimento geral parecia bom.

![As estrelas se movem mais rapidamente no arco longo, mais devagar nas bordas.](images/ellipse-movement.jpg)

As estrelas se movem mais rapidamente no arco longo, mais devagar nas bordas.


Com isso, cada estrela é totalmente descrita por (**curveOffset**, **ellipseSize**, **elevação**, **idade**), em que **age** é uma acumulação do tempo total que passou desde que a cena foi carregada.




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

Isso nos permitiu gerar dezenas de milhares de estrelas uma vez no início do aplicativo e, em seguida, animamos um conjunto único de estrelas ao longo das curvas estabelecidas. Como tudo está na GPU, o sistema pode animar todas as estrelas em paralelo sem nenhum custo para a CPU.

![A aparência é semelhante ao desenho de quatro processadores brancos.](images/drawing-white-quads-300px.jpg)

A aparência é semelhante ao desenho de quatro processadores brancos.



Para fazer com que cada Quad face a câmera, usamos um sombreador Geometry para transformar cada posição de estrela em um retângulo 2D na tela que conterá nossa textura em estrela.

![Ouros em vez de quádruplos.](images/drawing-white-quads-300px.jpg)

Ouros em vez de quádruplos.


Como queríamos limitar o excesso de empates (número de vezes que um pixel será processado) o máximo possível, nós giramos nossos quatro processadores para que eles tenham menos sobreposição.

### <a name="adding-clouds"></a>Adicionando nuvens

Há várias maneiras de obter uma sensação volumétricos com partículas, de raio de março dentro de um volume para desenhar o máximo de partículas possível para simular uma nuvem. O raio de março em tempo real seria muito caro e difícil de criar, portanto, primeiro tentamos criar um sistema impostor usando um método para renderizar florestas em jogos, com muitas imagens 2D de árvores voltadas para a câmera. Quando fazemos isso em um jogo, podemos ter texturas de árvores renderizadas de uma câmera que gira em direção, salvar todas essas imagens e, em tempo de execução para cada cartão de mensagem, selecionar a imagem que corresponde à direção da exibição. Isso não funciona tão bem quando as imagens são hologramas. A diferença entre os olhos à esquerda e o direito de fazer isso é que precisamos de uma resolução muito maior, ou simplesmente parece simples, com alias ou repetitivo.

Na segunda tentativa, tentamos ter o máximo de partículas possível. Os melhores elementos visuais foram obtidos quando desenhamos as partículas e as desfoquei antes de adicioná-las à cena. Os problemas típicos dessa abordagem estavam relacionados à quantidade de partículas que poderíamos desenhar em um único momento e na quantidade de área de tela coberta e, ao mesmo tempo, manter o 60fps. Desfocar a imagem resultante para obter essa sensação de nuvem normalmente era uma operação muito dispendiosa.

![Sem textura, é assim que as nuvens se pareceriam com uma opacidade de 2%.](images/clouds-without-texture-300px.jpg)

Sem textura, é assim que as nuvens se pareceriam com uma opacidade de 2%.



Ser aditivo e ter muitos deles significa que teríamos vários quatro quádruplos sobre os outros, sombreando repetidamente o mesmo pixel. No centro do Galaxy, o mesmo pixel tem centenas de quatro quádruplos em cima um do outro, e isso tinha um enorme custo ao ser feito em tela inteira.

Fazer nuvens de tela inteira e tentar desfocar elas teria sido uma má ideia, então decidimos deixar o hardware fazer o trabalho para nós.

### <a name="a-bit-of-context-first"></a>Primeiro um pouco de contexto

Ao usar texturas em um jogo, o tamanho da textura raramente corresponderá à área em que desejamos usá-la, mas podemos usar um tipo diferente de filtragem de textura para obter o cartão gráfico para interpolar a cor que desejamos dos pixels da textura ([filtragem de textura](https://msdn.microsoft.com/library/dn642451.aspx)). A filtragem que nos interessa é a [filtragem biline](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) , que calculará o valor de qualquer pixel usando os 4 vizinhos mais próximos.

![Original antes da filtragem](images/texture-1.png)

![Resultado após a filtragem](images/texture-2.png)

Usando essa propriedade, vemos que cada vez que tentamos desenhar uma textura em uma área duas vezes maior, ela desfoca o resultado.

Em vez de renderizar para uma tela inteira e perder os preciosos milissegundos que poderíamos estar gastando em alguma outra coisa, renderizamos para uma pequena versão da tela. Em seguida, copiando essa textura e esticando-a por um fator 2 várias vezes, obtemos a tela inteira enquanto desfocamos o conteúdo no processo.

![dimensionamento do X3 de volta para a resolução completa.](images/galaxy-resolutions-300px.png)

dimensionamento do X3 de volta para a resolução completa.



Isso nos permitiu obter a parte da nuvem com apenas uma fração do custo original. Em vez de adicionar nuvens na resolução completa, só pintamos 1/64th dos pixels e apenas alongamos a textura de volta para a resolução completa.

![Esquerda, com uma escala de 1/8 para resolução completa; e para a direita, com 3 upscale usando a potência de 2.](images/stars-upscaled-300px.jpg)

Esquerda, com uma escala de 1/8 para resolução completa; e para a direita, com 3 upscale usando a potência de 2.


Observe que tentar ir de 1/64th do tamanho para o tamanho total em uma só vez pareceria completamente diferente, pois o cartão gráfico ainda usaria 4 pixels em nossa configuração para sombrear uma área maior e os artefatos começarão a aparecer.

Em seguida, se adicionarmos estrelas de resolução completa com cartões menores, obteremos o Galaxy completo:

![Resultado quase final da renderização do Galaxy usando estrelas de resolução completa](images/full-galaxy-500px.png)

Depois de termos o controle certo com a forma, adicionamos uma camada de nuvens, trocamos os pontos temporários por aqueles que pintamos no Photoshop e adicionamos alguma cor adicional. O resultado foi uma forma de leite com as quais as equipes de arte e engenharia se sentiram bons e atendemos às nossas metas de ter profundidade, volume e movimento, tudo isso sem contorno da CPU.

![Nossa maneira de leite final do Galaxy em 3D.](images/final-galaxy-500px.jpg)

Nossa maneira de leite final do Galaxy em 3D.


### <a name="more-to-explore"></a>Mais para explorar

Abrimos o código do aplicativo Galaxy Explorer e o disponibilizamos no [GitHub](https://github.com/Microsoft/GalaxyExplorer) para que os desenvolvedores se criem.

Interessado em saber mais sobre o processo de desenvolvimento do Galaxy Explorer? Confira todas as nossas atualizações de projeto passadas no [canal do YouTube do Microsoft HoloLens](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).

## <a name="about-the-authors"></a>Sobre os autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b> é engenheiro de software e entusiasta de visuais sofisticados. Ele foi engenheiro de gráficos do Galaxy Explorer.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b> é um líder de arte e entusiasta de espaço que gerenciava a equipe de modelagem 3D para o Galaxy Explorer e o lutaram para obter ainda mais partículas.</td>
</tr>
</table>


## <a name="see-also"></a>Consulte também
* [Gerenciador do Galaxy no GitHub](https://github.com/Microsoft/GalaxyExplorer)
* [Atualizações de projeto do Galaxy Explorer no YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
