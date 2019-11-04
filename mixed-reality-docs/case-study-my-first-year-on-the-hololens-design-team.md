---
title: Estudo de caso – meu primeiro ano na equipe de design do HoloLens
description: Minha jornada de um Flatland 2D para o mundo 3D começou quando ingressei na equipe de design do HoloLens em janeiro de 2016.
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, design, editorial, pessoal
ms.openlocfilehash: 47ed5edd58846687daa4242f7bdbc85dae0f5255
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436609"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>Estudo de caso – meu primeiro ano na equipe de design do HoloLens

Minha jornada de um Flatland 2D para o mundo 3D começou quando ingressei na equipe de design do HoloLens em janeiro de 2016. Antes de ingressar na equipe, eu tinha muito pouca experiência no design 3D. Era como o chinês provérbio sobre uma jornada de milhares de milhas que começa com uma única etapa, exceto no meu caso, a primeira etapa era um salto!

![levando o salto de 2D para 3D](images/2D_to_3D-800px.gif)<br>
*Levando o salto de 2D para 3D*

> *"Pensei que, embora eu tenha colocado na estação do driver sem saber como dirigir o carro. Fiquei sobrecarregado e medo, mas muito focado. "*<br>
> — Hae Jin Lee

Durante o ano passado, eu escolhi habilidades e conhecimento o mais rápido possível, mas ainda tenho muito o que aprender. Aqui, escrevi quatro observações com um tutorial em vídeo documentando minha transição de um designer de interação 2D para 3D. Espero que minha experiência inspirará outros designers para levar o salto para o 3D.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>Quadro de boa-adeus. Saudação da interface espacial/diegetic

Sempre que projetei cartazes, revistas, sites ou telas de aplicativos, um quadro definido (geralmente um retângulo) era uma constante para cada problema. A menos que você esteja lendo esta postagem em um HoloLens ou outro dispositivo VR, você está *olhando para isso* na tela externa por meio de 2D protegida com segurança dentro de um quadro. O conteúdo é externo a você. No entanto, o headset da realidade misturada *elimina o quadro*, portanto, você está dentro do espaço de conteúdo, examinando e percorrendo o conteúdo de dentro para fora.

Entendi isso conceitualmente, mas no início eu fiz o erro de simplesmente transferir o raciocínio 2D para o espaço 3D. Isso obviamente não funcionou bem porque o espaço 3D tem suas próprias propriedades exclusivas, como uma alteração de exibição (com base no movimento do cabeçalho do usuário) e um [requisito diferente para o conforto do usuário](https://www.youtube.com/watch?v=-606oZKLa_s/) (com base nas propriedades dos dispositivos e nos seres humanos que os utilizam). Por exemplo, em um espaço de design de interface do usuário 2D, bloquear elementos da interface do usuário no canto de uma tela é um padrão muito comum, mas essa interface do usuário do estilo HUD (exibição de rumo) não se sente natural em experiências com o Sr/VR; Ele impede o imersão do usuário no espaço e faz discomfort do usuário. É como ter uma partícula de poeira incômodo nos óculos dos quais você está curioso de se livrar. Ao longo do tempo, aprendi que parece mais natural posicionar o conteúdo em espaço 3D e adicionar comportamento de corpo bloqueado que faz com que o conteúdo acompanhe o usuário em uma distância fixa relativa.

](images/bodylockedtagalong.gif) de ![bloqueadas pelo corpo<br>
*Corpo-bloqueado*

<br>

](images/worldlocked.gif) ![bloqueados pelo mundo<br>
*Protegido pelo mundo*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>Fragmentos: um exemplo de grande interface do usuário do Diegetic

[Fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8), um thriller de crime de primeira pessoa desenvolvido pelo [Asobo Studio](https://www.asobostudio.com/) para o HoloLens demonstra uma excelente interface do usuário Diegetic. Neste jogo, o usuário se torna um caractere principal, uma detecção que tenta resolver um mistério. As pistas dinâmicas para resolver esse mistério são espalhadas na sala física do usuário e geralmente são os horários inseridos dentro de um objeto fictício, e não os existentes por conta própria. Essa interface do usuário do diegetic tende a ser menos detectável do que a interface do usuário bloqueada pelo corpo, portanto, a equipe do Asobo usava com muita atenção muitos indícios, incluindo a direção dos caracteres virtuais ' olhar, som, luz e guias (por exemplo, seta apontando o local da pista) para obter a atenção do usuário.

Fragmentos de ![-exemplos de interface do usuário do Diegetic](images/fragments-game-example-1.jpg)<br>
*Fragmentos-exemplos da interface do usuário do Diegetic*

### <a name="observations-about-diegetic-ui"></a>Observações sobre a interface do usuário do amdiegetic

A interface do usuário espacial (de corpo bloqueado e de bloqueio mundial) e a interface do usuário do diegetic têm seus próprios pontos fortes e fracos. Recomendo que os designers experimentem tantos aplicativos MR/VR quanto possível e desenvolvam sua própria compreensão e Sensibility para vários métodos de posicionamento da interface do usuário.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>O retorno da interação esqueumorfismo e mágico

Esqueumorfismo, uma interface digital que imita a forma dos objetos do mundo real é "não legal" nos últimos 5 a 7 anos no setor de design. Quando a Apple finalmente deu o caminho para o design simples no iOS 7, parecia que Esqueumorfismo estava finalmente inoperante como uma metodologia de design de interface. Mas, em seguida, um novo Headset médio, Sr/VR chegou ao mercado e parece que Esqueumorfismo retornou novamente. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>Simulador de trabalho: um exemplo de design skeuomorphic VR

O [simulador de trabalho](https://jobsimulatorgame.com/), um jogo estranho desenvolvido pelo [Owlchemy Labs](https://owlchemylabs.com/) , é um dos exemplos mais populares para o design do skeuomorphic VR. Nesse jogo, os jogadores são transportados para o futuro, onde os robôs substituem seres humanos e seres humanos visitam um museu para experimentar o que parece executar tarefas de comuns em um dos quatro trabalhos diferentes: mecânico automático, gourmet chefe, administrador da loja ou operador do Office.

O benefício do Esqueumorfismo é claro. Os ambientes e os objetos conhecidos desse jogo ajudam os novos usuários de VR a se sentir mais confortáveis e apresentarem espaço virtual. Ele também faz com que eles se sintam no controle associando conhecimento e comportamentos familiares a objetos e suas reações físicas correspondentes. Por exemplo, para bebida uma xícara de café, as pessoas simplesmente precisam ir para a máquina de café, pressionar um botão, pegar a alça da xícara e inclinar a sua boca como faria no mundo real.

![simulador de trabalho](images/job-simulator.gif)<br>
*Simulador de trabalho*

Como o Sr/VR ainda é um meio de desenvolvimento, usar um certo grau de esqueumorfismo é necessário para desmistificar a tecnologia Sr/VR e apresentá-la a públicos maiores em todo o mundo. Além disso, o uso da representação esqueumorfismo ou realista pode ser benéfico para tipos específicos de aplicativos, como cirurgia ou simulação de voo. Como o objetivo desses aplicativos é desenvolver e refinar habilidades específicas que podem ser aplicadas diretamente no mundo real, quanto mais próxima a simulação for o mundo real, mais transferível será o conhecimento.

Lembre-se de que esqueumorfismo é apenas uma abordagem. O potencial do mundo do Sr/VR é muito maior que isso, e os designers devem se esforçar para criar interações de mágico do Hyper-natural — novas capacidades que são exclusivamente possíveis no mundo do Sr/VR. Como um início, considere adicionar mágico poweries a objetos comuns para permitir que os usuários atendam aos seus desejos fundamentais, incluindo a Teleportation e a omniscience.

![porta mágico do Doraemon (esquerda) e Ruby slippers (direita)](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Doraemon da porta mágico (esquerda) e Ruby slippers (direita)*

### <a name="observations-about-skeuomorphism-in-vr"></a>Observações sobre esqueumorfismo em VR

De "porta de qualquer lugar" em Doraemon, "Ruby slippers" no assistente de Oz para "mapa de Maurader" no Harry Potter, exemplos de objetos comuns com mágico Power abound em ficção popular. Esses objetos mágico nos ajudam a visualizar uma conexão entre o mundo real e o fantástico, entre o que é e o que poderia ser. Tenha em mente que, ao criar o objeto mágico ou surreal, é necessário fazer um equilíbrio entre a funcionalidade e a diversão. Tenha cuidado com a tentação de criar algo puramente mágico apenas para a novidade.

## <a name="understanding-different-input-methods"></a>Compreendendo diferentes métodos de entrada

Quando projetei para a mídia 2D, tive que me concentrar nas interações de toque, mouse e teclado para entradas. No espaço de design do Sr/VR, nosso corpo torna-se a interface e os usuários podem usar uma seleção mais ampla de métodos de entrada: incluindo fala, olhar, gesto, [6-DOF controladores](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)e luvas que oferecem conexão mais intuitiva e direta com objetos virtuais.

![entradas disponíveis no HoloLens](images/inputs.jpg)<br>
*Entradas disponíveis no HoloLens*

> *"Tudo é o melhor para algo e o pior para outra coisa".*<br>
> — [Bill Buxton compartilhará](https://www.billbuxton.com/)

Por exemplo, a entrada de gestos usando sensores de câmera e Bare-up em um dispositivo HMD libera os usuários da manutenção de controladores ou utilizando o luvas Sweaty, mas o uso frequente pode causar fadiga física (a. k. a Gorilla ARM). Além disso, os usuários precisam manter suas mãos dentro da linha de visão; se a câmera não puder ver as mãos, as mãos não poderão ser usadas.

A entrada de fala é boa para percorrer tarefas complexas porque permite que os usuários recortem menus aninhados com um comando (por exemplo, "Mostre-me os filmes feitos pelo Laika Studio".) e também muito econômico quando combinado com outra modalidade (por exemplo, o comando "face-me" orienta o holograma que um usuário está examinando em direção ao usuário). No entanto, a entrada de fala pode não funcionar bem em um ambiente barulhento ou pode não ser apropriada em um espaço muito silencioso.

Além de gestos e falas, os controladores rastreados de bolso (por exemplo, Oculus Touch, Naopak, etc.) são métodos de entrada muito populares porque são fáceis de usar, precisos, aproveitam o [proprioception](https://en.wikipedia.org/wiki/Proprioception)das pessoas e fornecem indicações de Haptic passivas. No entanto, esses benefícios têm o custo de não poder ser práticos e usar o controle de dedo completo.

![atestat (left) e Manus VR (right)](images/senso-and-manus-vr.jpg)<br>
*Senso (à esquerda) e Manus VR (direita)*

Embora não sejam tão populares quanto os controladores, o luvas está ganhando impulso novamente graças ao Sr/VR Wave. Mais recentemente, a entrada cérebro/mental começou a obter força como uma interface para ambientes virtuais ao integrar o sensor EEG ou EMG ao headset (por exemplo, [MINDMAZE VR](https://www.mindmaze.com/)).

### <a name="observations-about-input-methods"></a>Observações sobre os métodos de entrada

Esses são apenas um exemplo de dispositivos de entrada disponíveis no mercado para o Sr/VR. Eles continuarão a proliferar até que o setor se expanda e concorde com as práticas recomendadas. Até lá, os designers devem continuar cientes dos novos dispositivos de entrada e ser bem informados nos métodos de entrada específicos para seu projeto específico. Os designers precisam procurar soluções criativas dentro de limitações, enquanto também estão jogando nos pontos fortes do dispositivo.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>Esboço da cena e do teste no headset

Quando trabalhei em 2D, eu esbocei principalmente o conteúdo. No entanto, no espaço de realidade misturada que não era suficiente. Eu tinha que esboçar toda a cena para imaginar melhor as relações entre o usuário e os objetos virtuais. Para ajudar meu pensamento espacial, comecei a esboçar cenas no [cinema 4D](https://www.maxon.net/en/products/cinema-4d/overview/) e, às vezes, criamos ativos simples para a criação de protótipos no [Maya](https://www.autodesk.com/products/maya/overview/). Nunca usei nenhum programa antes de participar da equipe do HoloLens e ainda sou um jogador, mas trabalhar com esses programas 3D me ajudou a se sentir confortável com a nova terminologia, como o [Shader](https://en.wikipedia.org/wiki/Shader) e o [IK (cinemática inversa)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/).

**"Não importa quão bem esboço a cena em 3D, a experiência real em Headset quase nunca foi a mesma coisa que o esboço. É por isso que é importante testar a cena nos headsets de destino. "— Hae Jin Lee**

Para o protótipo do HoloLens, experimentei todos os tutoriais em [tutoriais de realidade misturados](tutorials.md) para começar. Em seguida, comecei a brincar com o [HoloToolkit. Unity](https://github.com/Microsoft/HoloToolkit-Unity/) que a Microsoft fornece aos desenvolvedores para acelerar o desenvolvimento de aplicativos Holographic. Quando fui preso por algo, publiquei minha pergunta sobre o [HoloLens question & Fórum de resposta](https://forums.hololens.com/categories/questions-and-answers/).

Depois de adquirir a compreensão básica do protótipo do HoloLens, eu queria capacitar outros não-codificadores para que eles tenham um protótipo próprio. Eu fiz um tutorial em vídeo que ensina como desenvolver um Projectile simples usando o HoloLens. Expliquei brevemente os conceitos básicos, portanto, mesmo que você tenha zero experiência no desenvolvimento do HoloLens, você deve ser capaz de acompanhar.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*Eu fiz este tutorial simples para não programadores como eu mesmo.*

Para o criação de protótipos VR, eu fiz cursos na [escola de desenvolvimento VR](https://learn.vrdev.school/) e também fiz [a criação de conteúdo 3D para a realidade virtual](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) em Lynda.com. A escola de desenvolvimento VR me proporcionou um conhecimento mais aprofundado na codificação e o curso Laura me ofereceu uma boa introdução à criação de ativos para VR.

## <a name="take-the-leap"></a>Pegue o salto

Há um ano, eu achei que tudo isso era um pouco difícil. Agora, posso dizer que era 100% do esforço. O Sr/VR ainda é muito jovem e há tantas possibilidades interessantes aguardando para serem percebidas. Sinto inspirado e sorte ser capaz de jogar uma pequena parte na criação do futuro. Espero que você se junte à jornada no espaço 3D!

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>@Microsoft do designer de UX</td>
</tr>
</table>

 
