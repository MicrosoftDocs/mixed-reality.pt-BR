---
title: Estudo de caso - capturar e criação de conteúdo para HoloTour
description: HoloTour para o Microsoft HoloLens fornece imersivos tours pessoais 3D de icônicos locais em todo o mundo.
author: DannyAskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: Windows HoloTour, HoloLens, realidade misturada
ms.openlocfilehash: 6c9e5f44c439310883c8b0271187a7b2263b0854
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589099"
---
# <a name="case-study---capturing-and-creating-content-for-holotour"></a>Estudo de caso - capturar e criação de conteúdo para HoloTour

HoloTour para o Microsoft HoloLens fornece imersivos tours pessoais 3D de icônicos locais em todo o mundo. Como os designers, artistas, produtores, áudio designers e desenvolvedores que trabalham nesse projeto descobriu, criando um processamento 3D convincingly real de um local conhecido usa uma combinação exclusiva de wizardry criativo e tecnológica.

## <a name="the-tech"></a>O técnico

Com HoloTour, queríamos tornam possível para que as pessoas visite alguns dos destinos de mais incríveis do mundo — como o [ruins de Machu Picchu](https://en.wikipedia.org/wiki/Machu_Picchu) Peru ou o dia modernos [Piazza Navona](https://en.wikipedia.org/wiki/Piazza_Navona) na Itália — diretamente do suas próprias salas de estar. Nossa equipe fez o objetivo de HoloTour "fazer você se sentir que você é realmente existe." A experiência necessária para ser mais do que apenas imagens ou vídeos. Aproveitando a exibição exclusivo, o acompanhamento e a tecnologia de áudio do HoloLens, acredita-se que estamos poderia praticamente de transporte você para outro lugar. Precisamos capturar o turísticos, sons e tridimensional geometria de cada local é visitado e, em seguida, recrie que dentro do nosso aplicativo.

Para fazer isso, precisávamos de uma câmera de 360 ° equipamento de captura de áudio direcional. Ele precisava capturar extremamente alta resolução, para que a sequência de imagens ficaria claro quando reproduzido em um HoloLens e as câmeras precisaria ser posicionado próximos uns dos outros para minimizar a junção de artefatos. Nós queríamos completo esférica cobertura, não apenas ao longo de horizonte, mas acima e abaixo, você também. O simulador de carga também precisava ser portáteis para que podemos incrementá-lo em todo o mundo. Podemos avaliada opções disponíveis no mercado disponíveis e percebi que eles simplesmente não estavam boas o suficiente para realizar nossa visão – por causa de resolução, o custo ou o tamanho. Se não foi possível encontrar um simulador de carga de câmera que satisfeitas nossas necessidades, teríamos que compilar um sozinhos.

### <a name="building-the-rig"></a>Criando os simuladores de carga

A primeira versão — feitas de papelão, Velcro, adesiva fita e câmeras de GoPro 14 — foi algo MacGyver teria sido orgulhar. Depois de revisar tudo, desde soluções low-end para equipamentos fabricados personalizados, câmeras GoPro foram, por fim, a melhor opção para nós porque eles foram pequeno e acessível e tinham o armazenamento de memória de fácil de usar. O fator forma pequeno foi especialmente importante porque ele nos permitiu colocar câmeras razoavelmente próximos uns dos outros — quanto menor a distância entre as câmeras, quanto menor os artefatos montagens estarão. Nossa organização de câmera exclusivo nos permitiu obter cobertura completa de esfera *plus* suficiente sobreposição para alinhar câmeras e suavizar alguns artefatos durante o processo de montagens de forma inteligente.

Aproveitando os [som espacial](spatial-sound.md) recursos em HoloLens é fundamental para criar uma experiência de imersão convincingly real. Nós usamos uma matriz de quatro microfone situada abaixo as câmeras no tripé, qual seria capturar som do local de nossa câmera em quatro direções, dando informações suficientes para criar espaciais sons em nosso cenas.

![Nosso simuladores de carga de câmera de 360° definida para filmagem fora o Pantheon.](images/camera-pantheon-200px.png)

Nosso simuladores de carga de câmera de 360° definida para filmagem fora o Pantheon. 


Testamos out nosso caseiro simuladores de carga ao levá-la até Ridge Rattlesnake perto de Seattle, capturando o cenário na parte superior de caminhada. O resultado, embora significativamente menos refinada os locais que você vê no HoloTour hoje, nos proporcionou certeza de que nosso design de simuladores de carga foi bom o suficiente para torná-lo a sentir como você está realmente lá.

Podemos atualizado nosso simuladores de carga do Velcro e cardboard para uma estrutura de câmera 3D-impresso e comprado pacotes de bateria externo para as câmeras GoPro simplificar o gerenciamento da bateria. Em seguida, fizemos um teste mais abrangente, viajando para baixo até a San Francisco para criar um miniatura tour Costa da cidade e a icônico Golden Gate bridge. Esse simulador de carga de câmera é o que usamos para a maioria de nossos capturas dos locais em que você visitar em HoloTour.

![O 360° câmera simuladores de carga filmagem em Machu Picchu.](images/camera-machu-pichu-500px.png)

O 360° câmera simuladores de carga filmagem em Machu Picchu. 


## <a name="behind-the-scenes"></a>Nos bastidores

Antes de filmagem, precisávamos Figura out quais locais que queríamos incluir nosso tour virtual. Roma foi o primeiro local em que é destinado para o envio e queríamos fazer tudo certo, portanto, decidimos fazer uma viagem scouting com antecedência. Enviamos uma equipe de seis pessoas — incluindo artistas, designers e produtores — para uma visita no local para os sites que pensavam. A viagem levou aproximadamente 9 dias – 2.5 para viagem, o restante para filmagem. (Para Machu Picchu podemos optou por não para fazer uma viagem scout, pesquisando com antecedência e reserva alguns dias de buffer para filmagem.)

Enquanto estiver em Roma, a equipe levou fotos de cada área e são indicados fatos interessantes, bem como a considerações práticas, por exemplo, muito difícil é a cada ponto e a dificuldade de viagem seria a um filme devido a restrições ou cheias. Isso pode parecer suas férias, mas é muito trabalho. Iniciado no início da manhã de dias e iria sem parar até a noite. Todas as noites, filmagens fosse carregada para a equipe de volta em Seattle para examinar. 

![Nossa equipe de captura em Roma.](images/holotour-filming-crew-rome-500px.jpg) 

Nossa equipe de captura em Roma. 


Depois que a viagem scout foi concluída, um plano final foi feito para filmagem real. Isso exigia uma lista detalhada de onde temos para filmes, em que dia e o horário. Todos os dias no exterior é caro, portanto, essas viagens necessário para ser eficiente. Podemos registrado guias e manipuladores em Roma para nos ajudar e totalmente usado de todos os dias antes de Nascer do sol para depois pôr do sol. Precisamos obter filmagens a melhor possível para torná-lo a sentir como você está realmente lá.

### <a name="capturing-the-video"></a>Captura de vídeo

Fazer algumas coisas simples durante a captura pode fazer o pós-processamento muito mais fácil. Por exemplo, sempre que você costurar imagens de vários câmeras, acabar com artefatos visuais, porque cada câmera tem uma exibição um pouco diferente. Os objetos mais próximos são para a câmera, maior a diferença entre os modos de exibição e maior será os artefatos de junção. Aqui está uma maneira fácil de visualizar o problema: mantenha o polegar para cima na frente o rosto e vê-la com apenas um olho. Agora, alterne olhos. Você verá que o polegar parece se mexer em relação ao plano de fundo. Se você mantenha o polegar ainda mais longe o rosto e repita o teste, o polegar aparecerá mover menor. Isto aparente movimentação é semelhante ao problema montagens nós nos deparamos com: Seus olhos, como nosso câmeras, não ver exatamente da mesma imagem, porque eles são separados por uma pequena distância.

Como é muito mais fácil de impedir que os artefatos pior enquanto filmagem do que corrigi-los no pós-processamento, tentamos manter as pessoas e coisas distante da câmera na esperança de que podemos eliminar a necessidade de unir os objetos aproximados. Manter uma compensação grande em torno de nossos câmera foi provavelmente um dos maiores desafios que tínhamos durante a solução e tivemos que exercitar a criatividade para fazê-lo funcionar. Trabalhar com guias locais era de grande ajuda no gerenciamento cheias, mas também descobrimos que usar assina — e, às vezes, pequenas cones ou recipientes de bean — marcar nosso espaço filming foi razoavelmente eficaz, especialmente porque precisamos apenas obter um curto período de filmagem sem marcações em cada local. Muitas vezes a melhor maneira de obter uma captura de BOM era apenas para chegar logo no início da manhã, antes da maioria das pessoas aparecia.

Algumas outras técnicas de captura úteis são provenientes diretamente práticas tradicionais de filme. Por exemplo, usamos um cartão de correção de cor em todos os nossos câmeras e fotos de referência capturada de texturas e objetos, talvez seja necessário mais tarde. 

![A cortar aproximada Picchu Machu mostrando o cartão de correção de cor.](images/rough-cut-machu-picchu-500px.png)

Recortar aproximada de filmagem sem marcações Pantheon antes de união.

### <a name="processing-the-video"></a>Processando o vídeo

Captura de conteúdo de 360° é apenas a primeira etapa — muito processamento é necessário para converter a filmagens de câmeras brutos que capturamos no finais ativos que você vê no HoloTour. Depois que estávamos volta home precisávamos dar o vídeo de câmera diferentes 14 feeds e transformá-lo em um único vídeo contínuo com artefatos mínimo. Nossa equipe de arte usei uma série de ferramentas para combinar e polonês a sequência de imagens capturada e desenvolvemos um pipeline para otimizar o processamento tanto quanto possível. A sequência de imagens tinha que ser Unido cor junto, corrigido e, em seguida, composto para remover elementos de distração e artefatos ou adicionar bolsos complementares da vida e movimento, tudo com a meta para aprimorar essa sensação de estar lá de fato.

![Recortar aproximada de filmagem sem marcações Pantheon antes de união.](images/rough-cut-pantheon-500px.png)

Recortar aproximada de filmagem sem marcações Pantheon antes de união. 


Para unir os vídeos, usamos uma ferramenta chamada [PTGui](http://www.ptgui.com/) e integrados a nosso pipeline de processamento. Como parte do pós-processamento de executamos extraídos ainda quadros de nossos vídeos e encontramos um padrão de montagens que era bom para um dos quadros. Em seguida, aplicamos esse padrão para um plug-in personalizado que escrevemos que permitido nosso vídeos artistas para otimizar e ajustar o padrão de montagens diretamente durante a composição em efeitos após. 

![Mostrando a sequência de imagens do Pantheon costurada captura de tela de PTGui.](images/stitching-tool-pantheon-500px.png)

Mostrando a sequência de imagens do Pantheon costurada captura de tela de PTGui. 


### <a name="video-playback"></a>Reprodução de vídeo

Após a conclusão do processamento da sequência de imagens, temos um vídeo perfeito, mas é incrivelmente grandes — resolução de aproximadamente 8 K. Decodificação de vídeo é caro e há muito poucos computadores que podem manipular um vídeo de 8K para que o próximo desafio era encontrar uma forma para reproduzir este vídeo novamente no HoloLens. Desenvolvemos um número de estratégias para evitar o custo de decodificação enquanto ainda deixa a percepção do usuário, como eles foram exibindo todo o vídeo.

A otimização mais fácil é para evitar que partes do vídeo que não mudará muito de decodificação. Criamos uma ferramenta para identificar as áreas em cada cena que têm pouca ou nenhuma animação. Para as regiões vamos mostrar uma imagem estática em vez de um vídeo de decodificação cada quadro. Para tornar isso possível, podemos dividida vídeo grande em partes muito menores.

Também fizemos-se de que cada pixel que são decodificados foi usado com mais eficiência. Experimentamos usando técnicas de compactação para reduzir o tamanho do vídeo. dividimos os vídeos regiões de acordo com os polígonos da geometria que ele seria projetado; podemos ajustada UVs e empacotadas os vídeos com base no quanto polígonos diferentes de detalhe incluído. O resultado desse trabalho, que é o que começou como um único 8K vídeo transformado em muitas partes que se parecem quase ininteligíveis até que eles sejam adequadamente novamente projetados na cena. Para um desenvolvedor de jogo que compreende o mapeamento da textura e empacotamento UV, isso provavelmente lhe parecerá familiar. 

![Uma exibição completa do Pantheon antes de otimizações.](images/pantheon-before-optimization-500px.png) 

Uma exibição completa do Pantheon antes de otimizações. 


![Metade direita do Pantheon, processado para reprodução de vídeo.](images/pantheon-process-video-playback-500px.png) 

Metade direita do Pantheon, processado para reprodução de vídeo. 


![Exemplo de uma única região vídeo após o empacotamento e a otimização.](images/single-video-region-after-optimization-500px.png) 

Exemplo de uma única região vídeo após o empacotamento e a otimização. 


Outro truque que usamos era evitar decodificação não são ativamente de exibição do vídeo. Enquanto estiver no HoloTour, você pode ver apenas parte da cena completa em um determinado momento. Estamos apenas decodificar vídeos dentro ou fora daqui a pouco do seu campo de exibição (FOV). Conforme você gira a cabeça, podemos iniciar a reprodução as regiões do vídeo que agora estão em seu FOV e parassem a execução aqueles que não estão mais dentro dele. A maioria das pessoas ainda não irá notar isso está acontecendo, mas se você ativar em torno de rapidamente, você verá o vídeo leva alguns segundos para iniciar, enquanto isso, você verá uma imagem estática que esmaece em seguida, de volta para o vídeo quando ele estiver pronto.

Para fazer com que essa estratégia funcione desenvolvemos um sistema abrangente de reprodução de vídeo. Otimizamos o código de reprodução de nível baixo para tornar extremamente eficiente vídeo de alternância. Além disso, tivemos de codificar nossos vídeos de maneira especial para que seja possível alternar rapidamente para qualquer vídeo a qualquer momento. Esse pipeline de reprodução levou a uma quantidade significativa de tempo de desenvolvimento, e implementamos em estágios. Nós começamos com um sistema mais simples do que era menos eficiente, mas designers permitidos e artistas para trabalhar na experiência e lentamente aprimorado para um sistema de reprodução mais robusto que nos permitiu entregar a barra de qualidade final. Esse sistema final tinha criado dentro do Unity para configurar o vídeo dentro da cena e monitorar o mecanismo de reprodução de ferramentas personalizadas.

### <a name="recreating-near-space-objects-in-3d"></a>Recriar objetos perto de espaço em 3D

Vídeos formam a maioria do que você vê no HoloTour, mas há um número de objetos 3D que aparecem perto de você, como a pintura em Piazza Navona, fica a fonte fora o Pantheon, ou o balão de ar quente que coloque em funcionamento em para cenas aéreas. Esses objetos 3D são importantes porque a percepção de profundidade humana é muito bom de perto, mas não muito bons distantes. Podemos fazer com vídeo na distância, mas para permitir que os usuários para fazer a ronda seu espaço e sentem que são realmente existe, próximos objetos precisam de profundidade. Essa técnica é semelhante ao tipo de coisa que você pode ver em um museu histórico natural — um diorama que tem paisagismo físico, plantas e espécimes animais em primeiro plano, mas é recuado em uma pintura fosca inteligentemente mascarada no plano de fundo de imagem.

Alguns objetos são ativos 3D simplesmente é criado e adicionado à cena para aprimorar a experiência. A pintura e o balão de ar quente entram nessa categoria porque não estavam presentes quando estamos são feitos. Assim como ativos de jogos, elas foram criadas por um artista 3D em nossa equipe e texturizadas adequadamente. Podemos colocá-los em nosso cenas perto de onde você está, e o mecanismo de jogos pode processá-los para as duas exibições HoloLens para que eles apareçam como um objeto 3D.

Outros ativos, como fica a fonte fora o Pantheon, são objetos reais que existem nos locais em que podemos estiver acertar vídeos, mas colocar esses objetos para fora o vídeo e em 3D, precisamos fazer uma série de coisas.

Primeiro, precisamos obter informações adicionais sobre cada objeto. Enquanto estiver no local para filmagem, nossa equipe capturada muita filmagens de referência desses objetos de modo que teríamos bastante detalhadas de imagens para recriar com precisão as texturas. A equipe também realizada uma [photogrammetry](https://en.wikipedia.org/wiki/Photogrammetry) scan, que constrói um modelo 3D de dezenas de imagens 2D, dando a um modelo aproximado do objeto em escala perfeita.

Como podemos processar nossa sequência de imagens, objetos que mais tarde serão substituídos com uma representação 3D são removidos do vídeo. O ativo 3D é baseado no modelo photogrammetry mas limpos e simplificado por nosso Artistas. Alguns objetos, podemos usar partes do vídeo — como a textura de água em fica a fonte — mas com muita frequência fica a fonte é agora um objeto 3D, o que permite aos usuários percebem a profundidade e ir em um espaço limitado na experiência. Ter objetos de espaço de perto como este bastante adiciona ao sentido de realismo e ajuda a Terra os usuários no local virtual. 

![Filmagens do pantheon com fica a fonte é removido. Ele será substituído com um ativo de 3D.](images/object-removal-pantheon-500px.png)

Filmagens do pantheon com fica a fonte é removido. Ele será substituído com um ativo de 3D.


## <a name="final-thoughts"></a>Considerações finais

Obviamente, foi mais para criar esse conteúdo que o que discutimos aqui. Há alguns cenas — gostamos de chamá-los "impossíveis perspectivas" — incluindo lutar contra a jornada de balão de ar quente e o gladiator em Colosseum, o que levou a uma abordagem mais criativa. Vamos abordar esses no futuro estudo de caso.

Esperamos que o compartilhamento de soluções para alguns dos maiores desafios que tínhamos durante a produção é útil para outros desenvolvedores e que você se inspirar a usar algumas dessas técnicas para criar suas próprias experiências de imersão para HoloLens. (E, se você, não se esqueça de compartilhá-lo conosco sobre o [Fórum do HoloLens App Development](https://forums.hololens.com/)!)

## <a name="about-the-authors"></a>Sobre os autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> é desenvolvedor sênior que aprendeu mais sobre os simuladores de câmera e reprodução de vídeo que ele pensou possíveis de trabalhar em HoloTour.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Daniel Askew</b> é um artista de vídeo que certificou de que sua jornada pelo Roma era tão perfeita possível.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> é um Designer de áudio que certificou de que você poderá experimentar o soundscape de cada destino que você visitar, mesmo quando você voltar no tempo.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis Steiner</b> é um diretor de Design que pesquisou e scouted locais, criar planos de viagem e direcionado a filmagem no site.</td>
</tr>
</table>



## <a name="see-also"></a>Consulte também
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
