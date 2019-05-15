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
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>Estudo de caso - criando uma galáxia na realidade mista

Antes de enviadas do Microsoft HoloLens, perguntamos nossa comunidade de desenvolvedores que tipo de aplicativo eles gostariam de ver uma equipe interna experiente compilar para o novo dispositivo. Mais de 5000 ideias foram compartilhadas e depois de uma pesquisa do Twitter de 24 horas, o vencedor era uma ideia chamada [Galaxy Explorer](galaxy-explorer.md).

Andy Zibits, o líder de arte no projeto e Karim Luccin, engenheiro de elementos gráficos da equipe, fale sobre o esforço colaborativo entre arte e de engenharia que levaram à criação de uma representação precisa, interativa do galaxy Láctea no Explorer Galaxy.

## <a name="the-tech"></a>O técnico

[Nossa equipe](galaxy-explorer.md#meet-the-team) - feita para cima de dois designers, desenvolvedores de três, quatro artistas, um produtor e um testador — tinha seis semanas para criar um aplicativo totalmente funcional que permite que as pessoas saber mais sobre e explorar o vastness e a beleza de nosso Galaxy Láctea.

Gostaríamos de aproveitar ao máximo a capacidade de renderizar objetos 3D diretamente em seu espaço de vida, portanto, decidimos que queríamos criar um realista atraente galaxy onde as pessoas seria capazes de ampliar close e ver estrelas individuais, cada um em seus próprio trajetórias de HoloLens .

Na primeira semana de desenvolvimento, criamos alguns objetivos para nosso representação do Galaxy Láctea: Ele precisava ter profundidade, movimento e aparência volumétricas — completo de estrelas que ajudam a criar a forma do galaxy.

O problema com a criação de uma galáxia animada que tinha bilhões de estrelas era que o enorme número de elementos únicos que precisam de atualização seria muito grande por quadro para HoloLens animar usando a CPU. Nossa solução envolvia uma mistura complexa de arte e ciência.

## <a name="behind-the-scenes"></a>Nos bastidores

Para permitir que as pessoas explorem estrelas individuais, nossa primeira etapa foi descobrir quantos partículas, foi possível processar ao mesmo tempo.

### <a name="rendering-particles"></a>Partículas de renderização

CPUs atuais são ótimos para processar tarefas seriais e até algumas tarefas em paralelo ao mesmo tempo (dependendo de quantos núcleos tiverem), mas as GPUs são muito mais eficazes na processar milhares de operações em paralelo. No entanto, porque eles geralmente não compartilham a mesma memória da CPU, troca de dados entre a CPU <> GPU pode rapidamente se tornar um gargalo. Nossa solução foi fazer uma galáxia na GPU e precisava viver completamente na GPU.

Começamos a testes de estresse com milhares de partículas de ponto em vários padrões. Isso nos permitiu obter o galaxy no HoloLens para ver o que funcionou e o que não funcionou.

### <a name="creating-the-position-of-the-stars"></a>Criando a posição das estrelas

Um dos nossos membros de equipe já tinha escrito o C# código que geraria estrelas em sua posição inicial. As estrelas são em uma elipse e sua posição pode ser descrita por (**curveOffset**, **ellipseSize**, **elevação**) onde **curveOffset**é o ângulo da estrela junto a elipse **ellipseSize** é a dimensão da elipse ao longo de X e Z e a elevação adequada da estrela dentro das galáxias de elevação. Assim, podemos criar um buffer ([ComputeBuffer do Unity](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) que deve ser inicializado com cada atributo em estrela e enviá-lo na GPU em que faria ao vivo para o restante da experiência. Para desenhar esse buffer, usamos [DrawProcedural do Unity](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) que permite executar um sombreador (código em uma GPU) em um conjunto arbitrário de pontos sem a necessidade de uma malha real que representa o galaxy:

**CPU:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

Começamos com padrões circulares brutos com milhares de partículas. Isso nos deu a prova de que precisávamos que poderíamos gerenciar muitos partículas e executá-lo em velocidades de alto desempenho, mas não foi satisfeitos com a forma geral do galaxy. Para melhorar a forma, tentamos vários padrões e sistemas de partículas com rotação. Elas eram inicialmente promissoras, cometendo porque o número de partículas e desempenho permanecia consistente, mas a forma dividiu perto do centro e estrelas estavam emitindo externamente que não era realista. Precisávamos de uma emissão que nos manipular o tempo e ter as partículas mover na verdade, um loop nunca mais próximo ao centro do galaxy.

![Tentamos vários padrões e sistemas de partículas girado, como esses.](images/galaxy-patterns-500px.png)

Tentamos vários padrões e sistemas de partículas girado, como esses.

Nossa equipe fez algumas pesquisas sobre a função de maneira galáxias e fizemos um sistema de partículas personalizadas especificamente para o galaxy para que poderia passar as partículas elipses com base em "[teoria de ondas de densidade](https://en.wikipedia.org/wiki/Density_wave_theory)," que theorizes que o alerta de um Galaxy são áreas de densidade mais alta, mas em fluxo constante, como um congestionamento no tráfego. Ele aparece sólida e estável, mas as estrelas são, na verdade, saem de braços quando eles passam ao longo de seus respectivos elipses. Em nosso sistema, as partículas nunca existirem na CPU, podemos gerar os cartões e orientá-los todos na GPU, portanto, todo o sistema é o estado inicial simplesmente + tempo. Ele avançava como este:

![Progressão do sistema de partículas com a renderização de GPU](images/spiral-galaxy-arms-500px.jpg)

Progressão do sistema de partículas com a renderização de GPU


Depois que o suficiente elipses são adicionadas e são definidos como girar, as galáxias começaram a forma "braços" em que a movimentação de estrelas convergir. O espaçamento das estrelas ao longo de cada caminho elíptico foi fornecido um pouco da aleatoriedade, e cada estrela ficou um pouco da aleatoriedade posicional adicionado. Isso criou uma distribuição de aparência muito mais natural de forma de estrela movimentação e arm. Por fim, adicionamos a capacidade para a cor com base na distância do centro da unidade.

### <a name="creating-the-motion-of-the-stars"></a>Criando o movimento das estrelas

Para animar o movimento de estrela geral, precisávamos para adicionar um ângulo de constante para cada quadro e obter estrelas movendo seus elipses a uma velocidade constante de radial. Isso é o principal motivo para usar **curveOffset**. Isso não é tecnicamente correto, como estrelas moverá mais rapidamente ao longo dos lados longo das elipses, mas o movimento geral sentimos BOM.

![Estrelas Avançar mais rápido do arco longo, mais lentas nas bordas.](images/ellipse-movement.jpg)

Estrelas Avançar mais rápido do arco longo, mais lentas nas bordas.


Com isso, cada estrela é totalmente descrita por (**curveOffset**, **ellipseSize**, **elevação**, **idade**) onde **idade** é um acúmulo do tempo total decorrido desde a cena foi carregada.




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

Isso nos permitiu gerar dezenas de milhares de estrelas, uma vez no início do aplicativo e, em seguida, estamos animados um conjunto a de estrelas curvas estabelecido. Como tudo o que é na GPU, o sistema pode animar estrelas em paralelo sem nenhum custo para a CPU.

![Aqui está o que se parece ao desenhar quadrados em branco.](images/drawing-white-quads-300px.jpg)

Aqui está o que se parece ao desenhar quadrados em branco.



Para tornar cada face quad a câmera, usamos um sombreador de geometria para transformar cada posição estrela a um retângulo 2D na tela que conterá nosso textura em estrela.

![Losangos, em vez de quadrados.](images/drawing-white-quads-300px.jpg)

Losangos, em vez de quadrados.


Porque queríamos limitar os excedentes (número de vezes que um pixel será processado) tanto quanto possível, podemos girado nosso quadrados para que elas podem ter menos sobreposição.

### <a name="adding-clouds"></a>Adicionando nuvens

Há várias maneiras para obter uma sensação volumétricas com partículas — de ray caminhando dentro de um volume ao desenho de partículas tantos quanto possível para simular uma nuvem. Ray em tempo real caminhando estava prestes a ser muito caro e difícil de autor, por isso, tentamos primeiro criar um sistema de impostor usando um método para florestas de renderização em jogos — com uma grande quantidade de imagens 2D das árvores voltados para a câmera. Quando fazemos isso em um jogo, podemos pode ter texturas de árvores processadas a partir de uma câmera que gira em torno de, salve todas essas imagens e em tempo de execução para cada cartão de mensagem de instalação, selecione a imagem que corresponde a direção da exibição. Isso não funciona bem quando as imagens são hologramas. A diferença entre o olho à esquerda e direita olhos torná-lo, de modo que precisamos de uma resolução muito maior, caso contrário, apenas parece simples, um alias ou repetitivas.

Em nossa segunda tentativa, tentamos tendo partículas tantos quanto possível. Os visuais melhores foram atingidos ao fogo desenhou partículas e desfocada-los antes de adicioná-los para a cena. Os problemas típicos com essa abordagem foram partículas relacionadas a quantos nós poderia desenhar em uma única vez e tela quanto a área cobertos por eles e ainda manter a 60fps. Desfoque a imagem resultante para obter esta nuvem está se sentindo costumava ser uma operação muito cara.

![Sem textura, isso é a aparência de nuvens com opacidade de % 2.](images/clouds-without-texture-300px.jpg)

Sem textura, isso é a aparência de nuvens com opacidade de % 2.



Sendo aditivas e ter uma grande quantidade deles significa que teríamos que vários quadrados sobre a outra, sombreamento repetidamente o mesmo pixel. No centro do galaxy, o mesmo pixel tem centenas de quadrados umas sobre as outras e isso tinha um enorme custo ao que está sendo feito a tela inteira.

Fazendo nuvens de tela inteira e tentando desfoque-los seria uma boa ideia, então, em vez disso, que decidimos permitir que o hardware de fazer o trabalho para nós.

### <a name="a-bit-of-context-first"></a>Um pouco de contexto pela primeira vez

Ao usar texturas em um jogo o tamanho da textura raramente corresponderá a área que desejamos usá-lo no, mas podemos usar diferentes tipos de filtragem para obter a placa gráfica para interpolar a cor que queremos por meio de pixels da textura de textura ([filtragemdetextura](https://msdn.microsoft.com/library/dn642451.aspx)). É a filtragem de seu interesse nos [filtragem bilinear](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) que irá calcular o valor de qualquer pixel usando o 4 vizinhos.

![Original antes de filtragem](images/texture-1.png)

![Resultado após a filtragem](images/texture-2.png)

Usando essa propriedade, podemos ver que cada vez que tentarmos desenhe uma textura em uma área duas vezes tão grande, ele Desfoca o resultado.

Em vez de renderização em tela inteira e perder esses milissegundos preciosos que poderia estar gastando em algo mais, podemos processar para uma pequena versão da tela. Em seguida, copiando dessa textura e ampliá-la várias vezes por um fator de 2, obtivemos para tela inteira ao desfocar o conteúdo no processo.

![X3 passarem para uma solução completa.](images/galaxy-resolutions-300px.png)

X3 passarem para uma solução completa.



Isso nos permitiu obter a parte de nuvem com apenas uma fração do custo original. Em vez de adicionar nuvens a resolução completa, estamos apenas paint 1/64 dos pixels e apenas alongar a textura de volta para uma solução completa.

![À esquerda, com um luxuoso de 1/8 à resolução total; e à direita, com 3 luxuoso usando potência de 2.](images/stars-upscaled-300px.jpg)

À esquerda, com um luxuoso de 1/8 à resolução total; e à direita, com 3 luxuoso usando potência de 2.


Observe que tentar ir de 1/64 do tamanho para todo o tamanho de uma só vez seria completamente diferente, como a placa gráfica ainda seria usar 4 pixels em nossa configuração para sombrear uma área maior e artefatos comecem a aparecer.

Em seguida, se adicionarmos estrelas de alta resolução com cartões menores, obtemos o galaxy completo:

![Próximo resultado final de renderização de galaxy usando estrelas de alta resolução](images/full-galaxy-500px.png)

Depois que o chamássemos no caminho certo com a forma, adicionamos uma camada de nuvens, permutado nos pontos temporários com aquelas podemos pintada no Photoshop e adicionou alguns adicionais de cor. O resultado foi uma galáxia Láctea nosso arte e ambas as equipes de engenharia sentiram boa sobre e ela superou nossas metas de profundidade, volume e movimentos de ter — tudo sem sobrecarregar a CPU.

![Nosso Galaxy Láctea final em 3D.](images/final-galaxy-500px.jpg)

Nosso Galaxy Láctea final em 3D.


### <a name="more-to-explore"></a>Mais para explorar

Nós o código para o aplicativo Galaxy Explorer de software livre e disponibilizados no [GitHub](https://github.com/Microsoft/GalaxyExplorer) que os desenvolvedores criem.

Você está interessado em descobrir mais sobre o processo de desenvolvimento para o Galaxy Explorer? Fazer check-out de todas as nossas atualizações de projeto passado na [canal do YouTube do Microsoft HoloLens](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).

## <a name="about-the-authors"></a>Sobre os autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b> é engenheiro de Software e entusiasta visuais sofisticados. Ele era o engenheiro de gráficos para o Galaxy Explorer.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b> é um Lead arte e espaço entusiasta gerenciado a equipe de modelagem 3D para o Galaxy Explorer e teve problemas para partículas ainda mais.</td>
</tr>
</table>


## <a name="see-also"></a>Consulte também
* [Explorer Galaxy no GitHub](https://github.com/Microsoft/GalaxyExplorer)
* [Atualizações do projeto Galaxy Explorer no YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
