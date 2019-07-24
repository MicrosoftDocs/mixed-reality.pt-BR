---
title: Estudo de caso-capturando e criando conteúdo para HoloTour
description: O HoloTour para Microsoft HoloLens fornece Tours pessoais 3D de imersão de locais de icônico em todo o mundo.
author: DannyAskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, realidade misturada do Windows
ms.openlocfilehash: 6c9e5f44c439310883c8b0271187a7b2263b0854
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63518241"
---
# <a name="case-study---capturing-and-creating-content-for-holotour"></a>Estudo de caso-capturando e criando conteúdo para HoloTour

O HoloTour para Microsoft HoloLens fornece Tours pessoais 3D de imersão de locais de icônico em todo o mundo. Como os designers, artistas, produtores, designers de áudio e desenvolvedores que trabalham neste projeto foram encontrados, criar uma renderização 3D realmente conhecida de um local conhecido leva a uma mistura exclusiva de criativo e wizardry tecnológicos.

## <a name="the-tech"></a>O Tech

Com o HoloTour, queríamos possibilitar que as pessoas visitassem alguns dos destinos mais incríveis do mundo, como o [ruins da Machu Picchu](https://en.wikipedia.org/wiki/Machu_Picchu) no Peru ou o dia moderno [Piazza Navona](https://en.wikipedia.org/wiki/Piazza_Navona) na Itália — diretamente de suas próprias salas de vida. Nossa equipe fez o objetivo da HoloTour para "fazer você sentir como você está realmente lá". A experiência precisava ser mais do que apenas imagens ou vídeos. Aproveitando a tecnologia exclusiva de exibição, controle e áudio do HoloLens, acreditamos que poderíamos transportar virtualmente para outro lugar. Precisamos capturar o atenções, sons e a geometria tridimensional de cada local que visitamos e, em seguida, recriá-lo em nosso aplicativo.

Para fazer isso, precisávamos de um rig de câmera de 360 ° com captura de áudio direcional. Ele precisava capturar uma resolução extremamente alta, para que a seqüência de imagens pareça nítida quando reproduzida em um HoloLens e as câmeras precisassem ser posicionadas em conjunto para minimizar os artefatos de costura. Queríamos cobertura esférica completa, não apenas ao longo do horizonte, mas acima e abaixo também. O Rig também precisava ser portátil para que possamos fazer tudo isso por todo o mundo. Avaliamos as opções disponíveis no mercado e percebemos que elas simplesmente não eram boas para concretizar nossa visão – devido à resolução, ao custo ou ao tamanho. Se não pudermos encontrar um rig de câmera que satisfaça nossas necessidades, teríamos que criar um por si mesmo.

### <a name="building-the-rig"></a>Compilando o Rig

A primeira versão — feita desde papel, velcro, fita de dutos e 14 câmeras GoPros — era algo que MacGyver seria orgulho. Depois de examinar tudo, desde soluções de low-end até Rigs de fabricação personalizadas, as câmeras GoPro foram, na verdade, a melhor opção para nós porque eram pequenas, acessíveis e tinham um armazenamento de memória fácil de usar. O fator forma pequeno era especialmente importante porque permitia posicionar as câmeras com muita proximidade – quanto menor a distância entre as câmeras, menor será o tamanho dos artefatos de costura. Nosso único arranjo de câmera nos permitiu obter cobertura completa da esfera, *além* de sobreposição suficiente para alinhar as câmeras de forma inteligente e suavizar alguns artefatos durante o processo de junção.

Tirar proveito dos recursos de [som espaciais](spatial-sound.md) no HoloLens é essencial para criar uma experiência de imersão realmente real. Usamos uma matriz de quatro microfone situada debaixo das câmeras no Tripod, que capturariam o som da localização de nossa câmera em quatro direções, fornecendo-nos informações suficientes para criar sons espaciais em nossas cenas.

![Nossa câmara de câmera de 360 ° configurada para filming fora do Pantheon.](images/camera-pantheon-200px.png)

Nossa câmara de câmera de 360 ° configurada para filming fora do Pantheon. 


Testamos nosso Rig Homemade ao colocá-lo em Rattlesnake ondulado perto de Seattle, capturando o cenário na parte superior do trilha. O resultado, embora seja significativamente menos elegante do que os locais que você vê no HoloTour hoje, nos deu a certeza de que nosso design de Rig era bom o suficiente para que você se sinta realmente lá.

Atualizamos nosso Rig de velcro e papel para um invólucro de câmera impresso em 3D e compramos pacotes de bateria externos para que as câmeras GoPro simplifiquem o gerenciamento de bateria. Em seguida, fizemos um teste mais extensivo, viajando até San Francisco para criar um tour em miniatura da costa da cidade e da ponte de porta dourada icônico. Esse Rig de câmera é o que usamos para a maioria de nossas capturas dos locais que você visita no HoloTour.

![The 360 ° Camera Rig filming em Machu Picchu.](images/camera-machu-pichu-500px.png)

The 360 ° Camera Rig filming em Machu Picchu. 


## <a name="behind-the-scenes"></a>Nos bastidores

Antes de filming, precisávamos descobrir quais locais queríamos incluir em nosso tour virtual. Roma foi o primeiro local que pretendemos fornecer e queríamos obtê-lo certo, então decidimos fazer uma viagem de protetor com antecedência. Enviamos uma equipe de seis pessoas, incluindo artistas, designers e produtores, para uma visita pessoalmente aos sites que estávamos considerando. A corrida levou cerca de 9 dias – 2,5 para viagem, o restante para filming. (Para Machu Picchu, optamos por não fazer uma corrida de atendente, Pesquisar antecipadamente e reservar alguns dias de buffer para filming.)

Enquanto estiver em Roma, a equipe tirou fotos de cada área e observou fatos interessantes, bem como considerações práticas, como o quão difícil é viajar para cada lugar e quão difícil seria o filme devido a áreas de escalabilidade ou restrições. Isso pode parecer uma férias, mas é muito trabalho. Os dias começaram desde a manhã e não vão parar até a noite. Toda noite, a seqüência foi carregada para a equipe de volta em Seattle para revisão. 

![Nosso equipe de captura em Roma.](images/holotour-filming-crew-rome-500px.jpg) 

Nosso equipe de captura em Roma. 


Após a conclusão da corrida do Scout, foi feito um plano final para filming reais. Isso exigia uma lista detalhada de onde vamos fazer um filme, em que dia e em que hora. Todos os dias no exterior são caros, portanto, essas viagens precisavam ser eficientes. Nós registramos guias e manipuladores em Roma para nos ajudar e a usar totalmente todos os dias, desde o nascer até o pôr do sol. É necessário obter a melhor seqüência possível para que você se sinta lá mesmo.

### <a name="capturing-the-video"></a>Capturando o vídeo

Fazer algumas coisas simples durante a captura pode tornar o pós-processamento muito mais fácil. Por exemplo, sempre que unir imagens de várias câmeras, você acabará com os artefatos visuais, pois cada câmera tem uma exibição um pouco diferente. Os objetos mais próximos são a câmera, quanto maior a diferença entre as exibições e quanto maior os artefatos de costura serão. Aqui está uma maneira fácil de visualizar o problema: Mantenha seu polegar na frente do seu rosto e examine-o com apenas um olho. Agora, mude os olhos. Você verá que seu thumb parece se mover em relação ao plano de fundo. Se você mantiver seu polegar mais longe de seu rosto e repetir o experimento, seu thumb parecerá ser movido para menos. Esse movimento aparente é semelhante ao problema de costura que enfrentamos: Seus olhos, como nossas câmeras, não veem exatamente a mesma imagem porque elas são separadas por uma pequena distância.

Como é muito mais fácil evitar os piores artefatos enquanto filming do que é necessário corrigi-los no pós-processamento, tentamos manter as pessoas e as coisas longe da câmera na esperança que poderíamos eliminar a necessidade de unir objetos de fechamento. A manutenção de uma grande limpeza em nossa câmera era provavelmente um dos maiores desafios que tínhamos durante a solução e tivemos que fazer com que ela funcione. Trabalhar com guias locais foi uma enorme ajuda no gerenciamento de áreas de trabalho, mas também descobrimos que o uso de sinais — e, às vezes, pequenos coness ou de bolsas de Beans — para marcar nosso espaço de filming era razoavelmente eficaz, especialmente porque só precisávamos obter uma pequena quantidade de imagens em cada local. Geralmente, a melhor maneira de obter uma boa captura era apenas chegar muito cedo na manhã, antes que a maioria das pessoas fosse mostrada.

Algumas outras técnicas de captura úteis vêm diretamente de práticas de filme tradicionais. Por exemplo, usamos um cartão de correção de cor em todas as nossas câmeras e capturamos fotos de referência de texturas e objetos que talvez sejam necessários mais tarde. 

![Um corte áspero de Machu Picchu mostrando o cartão de correção de cor.](images/rough-cut-machu-picchu-500px.png)

Um corte aproximado da Pantheon de imagens antes de unir.

### <a name="processing-the-video"></a>Processando o vídeo

Capturar o conteúdo de 360 ° é apenas a primeira etapa — é necessário muito processamento para converter a seqüência bruta da câmera que capturamos nos ativos finais que você vê em HoloTour. Depois de voltar, precisamos pegar o vídeo de 14 feeds de câmera diferentes e transformá-lo em um único vídeo contínuo com artefatos mínimos. Nossa equipe de arte usou várias ferramentas para combinar e aprimorar a seqüência capturada e desenvolvemos um pipeline para otimizar o processamento o máximo possível. A seqüência tinha que ser juntada, corrigida por cor e, em seguida, compostada para remover elementos e artefatos de distração ou para adicionar bolsos suplementares de vida e movimento, tudo com o objetivo de aprimorar essa sensação de realmente estar lá.

![Um corte aproximado da Pantheon de imagens antes de unir.](images/rough-cut-pantheon-500px.png)

Um corte aproximado da Pantheon de imagens antes de unir. 


Para unir os vídeos, usamos uma ferramenta chamada [PTGui](http://www.ptgui.com/) e a integro ao nosso pipeline de processamento. Como parte do pós-processamento, extraímos os quadros de nossos vídeos e encontramos um padrão de costura que parecia bom para um desses quadros. Em seguida, aplicamos esse padrão a um plug-in personalizado que escrevemos, que permitia que nossos artistas de vídeo ajustassem e ajustassem o padrão de costura diretamente durante a composição nos efeitos após. 

![Captura de tela de PTGui mostrando a seqüência de Pantheon costurada.](images/stitching-tool-pantheon-500px.png)

Captura de tela de PTGui mostrando a seqüência de Pantheon costurada. 


### <a name="video-playback"></a>Reprodução de vídeo

Após a conclusão do processamento da seqüência de imagens, temos um vídeo contínuo, mas ele é extremamente grande, em vez de resolução de 8K. A decodificação de vídeo é cara e há poucos computadores que podem lidar com um vídeo de 8K, de modo que o próximo desafio estava encontrando uma forma de reproduzir esse vídeo no HoloLens. Desenvolvemos várias estratégias para evitar o custo da decodificação enquanto o usuário parece que estava exibindo todo o vídeo.

A otimização mais fácil é evitar a decodificação de partes do vídeo que não mudam muito. Escrevemos uma ferramenta para identificar áreas em cada cena que têm pouco ou nenhum movimento. Para essas regiões, mostramos uma imagem estática em vez de decodificar um vídeo em cada quadro. Para tornar isso possível, dividimos o grande vídeo em partes muito menores.

Também garantimos que todos os pixels decodificados foram usados com mais eficiência. Experimentamos as técnicas de compactação para diminuir o tamanho do vídeo; Dividimos as regiões de vídeo de acordo com os polígonos da geometria em que ela seria projetada; ajustamos o UVs e reempacotamos os vídeos com base na quantidade de detalhes de polígonos diferentes incluídos. O resultado desse trabalho é que o que começou como um vídeo único de 8K se transformou em muitas partes que parecem quase ininteligível até que sejam reformuladas corretamente na cena. Para um desenvolvedor de jogos que entenda o mapeamento de textura e a embalagem UV, isso provavelmente será familiar. 

![Uma exibição completa do Pantheon antes das otimizações.](images/pantheon-before-optimization-500px.png) 

Uma exibição completa do Pantheon antes das otimizações. 


![A metade direita do Pantheon, processada para reprodução de vídeo.](images/pantheon-process-video-playback-500px.png) 

A metade direita do Pantheon, processada para reprodução de vídeo. 


![Exemplo de uma única região de vídeo após a otimização e a embalagem.](images/single-video-region-after-optimization-500px.png) 

Exemplo de uma única região de vídeo após a otimização e a embalagem. 


Outro truque que usamos foi para evitar a decodificação de vídeo que você não está visualizando ativamente. Enquanto estiver no HoloTour, você só poderá ver parte da cena completa em um determinado momento. Decodificamos apenas vídeos dentro ou logo fora do campo de exibição (FOV). Ao girar sua cabeça, começamos a jogar as regiões do vídeo que agora estão em sua FOV e param de executá-las que não estão mais dentro dela. A maioria das pessoas nem mesmo perceberá que isso está acontecendo, mas se você virar rapidamente, verá que o vídeo leva um segundo para começar – enquanto isso, você verá uma imagem estática que, em seguida, esmaecerá para o vídeo quando ele estiver pronto.

Para fazer essa estratégia funcionar, desenvolvemos um sistema de reprodução de vídeo extensivo. Otimizamos o código de reprodução de nível baixo para tornar a alternância de vídeo extremamente eficiente. Além disso, tivemos que codificar nossos vídeos de forma especial para tornar possível alternar rapidamente para qualquer vídeo a qualquer momento. Esse pipeline de reprodução levou uma quantidade significativa de tempo de desenvolvimento para que possamos implementá-lo em estágios. Começamos com um sistema mais simples, que era menos eficiente, mas permitia designers e artistas para trabalhar na experiência e o melhorou lentamente para um sistema de reprodução mais robusto que nos permitia remeter na barra de qualidade final. Esse sistema final tinha ferramentas personalizadas que criamos no Unity para configurar o vídeo dentro da cena e monitorar o mecanismo de reprodução.

### <a name="recreating-near-space-objects-in-3d"></a>Recriando objetos Near-Space em 3D

Os vídeos compõem a maior parte do que você vê em HoloTour, mas há uma série de objetos 3D que aparecem perto de você, como a pintura em Piazza Navona, a Fountain fora do Pantheon ou o balão de ar quente no qual você se destaca para cenas aéreas. Esses objetos 3D são importantes porque a percepção de profundidade humana está muito próxima, mas não muito bem longe. Podemos ficar com o vídeo à distância, mas para permitir que os usuários percorram seu espaço e pareçam que estão realmente lá, os objetos próximos precisam de profundidade. Essa técnica é semelhante ao tipo de coisa que você pode ver em um museu de história natural — imagem a diorama que tem Landscaping físico, plantas e animais de Specimens em primeiro plano, mas se reprevalece em uma pintura fosca com máscara inteligente em segundo plano.

Alguns objetos são simplesmente ativos 3D que criamos e adicionamos à cena para aprimorar a experiência. A pintura e o balão de ar quente se enquadram nessa categoria porque não estavam presentes quando nos refilmemos. Semelhante aos ativos de jogos, eles foram criados por um artista 3D em nossa equipe e texturizados adequadamente. Nós os colocamos em nossas cenas perto de onde você tem, e o mecanismo de jogo pode renderizá-los para os dois HoloLenss exibidos para que eles apareçam como um objeto 3D.

Outros ativos, como o Fountain fora do Pantheon, são objetos reais que existem nos locais onde estamos capturando vídeo, mas para trazer esses objetos do vídeo e para o 3D, temos que fazer várias coisas.

Primeiro, precisamos de informações adicionais sobre cada objeto. Enquanto estiver no local para filming, nossa equipe capturou uma grande quantidade de seqüências de referência desses objetos para que possamos ter imagens detalhadas suficientes para recriar as texturas com precisão. A equipe também realizou uma verificação de [Photogrammetry](https://en.wikipedia.org/wiki/Photogrammetry) , que constrói um modelo 3D de dezenas de imagens 2D, dando-nos um modelo aproximado do objeto em escala perfeita.

À medida que processamos nossa seqüência, os objetos que posteriormente serão substituídos por uma representação 3D serão removidos do vídeo. O ativo 3D é baseado no modelo Photogrammetry, mas limpo e simplificado por nossos artistas. Para alguns objetos, podemos usar partes do vídeo — como a textura de água no Fountain — mas a maior parte do Fountain agora é um objeto 3D, que permite aos usuários perceber a profundidade e acompanhá-lo em um espaço limitado na experiência. Ter objetos quase de espaço como esse aumenta muito a sensação de realm e ajuda a aterrar os usuários no local virtual. 

![Pantheon de seqüência com o Fountain removido. Ele será substituído por um ativo 3D.](images/object-removal-pantheon-500px.png)

Pantheon de seqüência com o Fountain removido. Ele será substituído por um ativo 3D.


## <a name="final-thoughts"></a>Pensamentos finais

Obviamente, houve mais para criar esse conteúdo do que o que discutimos aqui. Há algumas cenas – gostaríamos de chamá-las de "perspectivas impossíveis", incluindo a jornada de balões de ar quente e a luta Gladiator no Colosseum, que adotou uma abordagem mais criativa. Vamos solucioná-los em um estudo de caso futuro.

Esperamos que o compartilhamento de soluções para alguns dos maiores desafios que tínhamos durante a produção seja útil para outros desenvolvedores e que você tenha inspirado o uso de algumas dessas técnicas para criar suas próprias experiências de imersão para o HoloLens. (E, se você fizer isso, certifique-se de compartilhá-lo conosco no [Fórum de desenvolvimento de aplicativos do HoloLens](https://forums.hololens.com/)!)

## <a name="about-the-authors"></a>Sobre os autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> é desenvolvedor sênior que aprendeu mais sobre a câmera Rigs e reprodução de vídeo do que achou possível de trabalhar em HoloTour.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b> é um artista de vídeo que se certificava de que sua jornada por Roma foi o mais perfeita possível.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> é um designer de áudio que garantiu que você pudesse experimentar o soundscape de todos os destinos visitados, mesmo quando volta a usar o tempo.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis Steiner</b> é diretor de design que pesquisava e reprotetorou locais, criou planos de viagem e direcionou filming no site.</td>
</tr>
</table>



## <a name="see-also"></a>Consulte também
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
