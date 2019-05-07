---
title: Estudo de caso - equipe de design do meu primeiro ano sobre o HoloLens
description: Minha jornada de um flatland 2D para o mundo 3D iniciado quando eu ingressou na equipe de design do HoloLens em janeiro de 2016.
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Pessoal editorial, do design, Windows Mixed Reality, HoloLens,
ms.openlocfilehash: 050645e6096559a4f37b033e5ddfdc5444039c08
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873950"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>Estudo de caso - equipe de design do meu primeiro ano sobre o HoloLens

Minha jornada de um flatland 2D para o mundo 3D iniciado quando eu ingressou na equipe de design do HoloLens em janeiro de 2016. Antes de se juntar à equipe, eu tinha muito pouca experiência no design 3D. Como o chinês provérbio sobre uma jornada de milhas de mil começando com uma única etapa, exceto no meu caso, essa primeira etapa era um salto era!

![Levando o salto de 2D para 3D](images/2D_to_3D-800px.gif)<br>
*Levando o salto de 2D para 3D*

> *"Me senti que eu pulei de motorista sem precisar saber como dirigir o carro. Eu estava sobrecarregado e com medo, ainda que muito focada. "*<br>
> — Hae Jin Lee

Durante o ano passado, eu captado habilidades e conhecimentos tão rápido quanto eu poderia, mas ainda tenho muito a aprender. Aqui, eu escrevi backup 4 observações com um tutorial em vídeo documentando minha transição de um 2D para o designer de interação 3D. Espero que minha experiência inspire outros designers para levar o salto para 3D.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>Quadro de um adeus. Olá espacial / diegetic da interface do usuário

Sempre que projetei cartazes, revistas, sites ou telas do aplicativo, um quadro definido (normalmente, um retângulo) era uma constante para cada problema. A menos que você está lendo esta postagem em um HoloLens ou outro dispositivo VR, você está *olhando externo* por meio da tela 2D protegida com segurança dentro de um quadro. O conteúdo é externo para você. No entanto, headset de realidade misturada *elimina o quadro*, de modo que você está no espaço de conteúdo, procurando e percorrer o conteúdo de dentro para fora.

Eu entendi isso conceitualmente, mas no início eu cometi o erro de transferência de simplesmente pensar 2D em espaço 3D. Isso obviamente não funcionou bem porque o espaço 3D tem suas próprias propriedades exclusivas, como uma alteração do modo de exibição (com base na movimentação do cabeçote do usuário) e [requisito diferente para o conforto do usuário](https://www.youtube.com/watch?v=-606oZKLa_s/) (com base nas propriedades de dispositivos e os humanos usando -los). Por exemplo, em um espaço 2D de design de interface do usuário, o bloqueio de elementos de interface do usuário no canto de uma tela é um padrão muito comum, mas esse estilo de HUD (Head-se exibir) da interface do usuário não se sintam natural em experiências MR/VR; Ele impede imersão do usuário para o espaço e faz com que o discomfort do usuário. É como ter uma partícula poeira irritante em seus óculos que você está ansioso para eliminar. Ao longo do tempo, eu aprendi que ela se parece mais natural para posicionar o conteúdo no espaço 3D e adicionar comportamento bloqueado de corpo que faz o seguinte conteúdo o usuário a uma distância fixa relativo.

![Bloqueado por corpo](images/bodylockedtagalong.gif)<br>
*Bloqueado por corpo*

<br>

![Bloqueado pelo mundo](images/worldlocked.gif)<br>
*Bloqueado pelo mundo*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>Fragmentos: Um exemplo de excelente Diegetic UI

[Fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8), um suspense crime de primeira pessoa desenvolvido pela [Asobo Studio](http://www.asobostudio.com/) para HoloLens demonstra uma UI Diegetic excelente. Nesse jogo, o usuário se torna um caractere principal, um detetive que tenta resolver um mistério. As pivotal dicas para resolver esse mistério obterem espalhadas em sala de física do usuário e são muitas vezes incorporado dentro de um objeto fictício, em vez de existentes por conta própria. Este diegetic na interface do usuário tende a ser menos identificáveis que bloqueado o corpo da interface do usuário, portanto, a equipe Asobo inteligentemente usado muitas indicações, incluindo a direção de olhar virtual caracteres, som, luz e guias (por exemplo, seta apontando para o local da pista) para captar a atenção do usuário.

![Fragmentos - exemplos Diegetic UI](images/fragments-game-example-1.jpg)<br>
*Fragmentos - exemplos Diegetic UI*

### <a name="observations-about-diegetic-ui"></a>Observações sobre diegetic da interface do usuário

Diegetic da interface do usuário e interface do usuário (ambos bloqueado de corpo e bloqueada pelo mundo) espacial tem seus próprios pontos fortes e fracos. Eu recomendo que os designers para experimentar tantos aplicativos MR/VR possível e desenvolver suas próprias compreensão e sensibility para interface do usuário vários métodos de posicionamento.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>O retorno de esqueumorfismo e interação de mágica

Esqueumorfismo, uma interface digital que imita a forma de objetos do mundo real foi "legal" nos últimos 5 a 7 anos no setor de design. Quando por fim, a Apple deu lugar ao design simples no iOS 7, mesmo pareceu esqueumorfismo morreu, por fim, como uma metodologia de design de interface. Mas, em seguida, uma nova mídia, fone de ouvido MR/VR chegou ao mercado e parece que esqueumorfismo retornado novamente. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>Simulador de trabalho: Um exemplo de design VR skeuomorphic

[Trabalho Simulator](http://jobsimulatorgame.com/), um jogo extravagante desenvolvido pela [Owlchemy laboratórios](https://owlchemylabs.com/) é um do exemplo mais popular do design VR skeuomorphic. Dentro nesse jogo, os jogadores são transportados para futuro onde robôs substituir os seres humanos e humanos visitar um museu para experimentar a sensação para realizar tarefas rotineiras em uma das quatro diferentes trabalhos: Auto mecânico, Gourmet Chef, administrador Store ou trabalhador de escritório.

O benefício de esqueumorfismo é evidente. Ambiente familiar e objetos dentro desse jogo ajudam novos usuários VR se sentir mais confortável e presente no espaço virtual. Ele também torna-os sentir como eles estão no controle por meio da associação de dados de Conhecimento familiar e comportamentos com objetos e reações deles físicas correspondentes. Por exemplo, para tomar uma xícara de café, as pessoas simplesmente precisam percorrer para a máquina de café, pressionar um botão, arraste a alça de cup e incliná-la em direção a seu boca como fazem no mundo real.

![Simulador de trabalho](images/job-simulator.gif)<br>
*Simulador de trabalho*

Como MR/VR ainda é um meio de desenvolvimento, usar um certo grau de esqueumorfismo é necessário para desmistificar tecnologia MR/VR e conectá-lo para um público maior em todo o mundo. Além disso, usando esqueumorfismo ou representação realista pode ser benéfico para tipos específicos de aplicativos, como simulação de cirurgia ou voo. Como o objetivo desses aplicativos é desenvolver e refinar as habilidades específicas que podem ser aplicadas diretamente no mundo real, quanto mais próximo a simulação é mundo real, o conhecimento é transferível mais.

Lembre-se de que esqueumorfismo é apenas uma abordagem. O potencial do mundo MR/VR é muito maior do que e designers devem se esforçar para criar interações com o hyper-natural mágicas — novas capacidades que são possíveis exclusivamente no mundo MR/VR. Para começar, considere adicionar potências mágicas para objetos comuns para permitir que os usuários atender a seus pontos fundamentais — incluindo teleportation e omniscience.

![Porta mágica do Doraemon (à esquerda) e slippers(right) Ruby](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Porta mágica do Doraemon (à esquerda) e slippers(right) ruby*

### <a name="observations-about-skeuomorphism-in-vr"></a>Observações sobre esqueumorfismo em VR

De "Em qualquer lugar da porta" no Doraemon, "Chinelos de rubi", o mágico de Oz do Maurader "mapa" em Harry Potter, exemplos de objetos comuns com energia mágico são muitas ficção popular. Esses objetos mágicos nos ajudar a visualizar uma conexão entre o mundo real e o fantástico, entre o que é e o que poderia ser. Tenha em mente que, durante a criação de mágico ou surreal objeto um precisa atingir um equilíbrio entre funcionalidade e entretenimento. Tenha cuidado com a tentação de criar algo de mágico puramente apenas para exemplificar do novidade.

## <a name="understanding-different-input-methods"></a>Noções básicas sobre os diferentes métodos de entrada

Quando projetei a mídia 2D, tive de se concentrar em toque, mouse e interações de teclado para as entradas. No espaço de design MR/VR, o nosso corpo torna-se a interface e os usuários são capazes de usar uma seleção mais ampla de métodos de entrada: incluindo fala, olhar, gesto, [dof 6 controladores](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)e luvas que arcar com mais de conexão direta e intuitiva com objetos virtuais.

![Entradas disponíveis no HoloLens](images/inputs.jpg)<br>
*Entradas disponíveis no HoloLens*

> *"Tudo o que é melhor para algo e os piores para outra coisa".*<br>
> — [Bill Buxton](https://www.billbuxton.com/)

Por exemplo, o gesto de entrada usando bare mão e sensores de câmera em um dispositivo HMD libera mão de usuários de contendo controladores ou utilize sweaty luvas, mas uso frequente pode causar fadiga física (também conhecidas como braço de gorila). Além disso, os usuários precisam manter suas mãos dentro da linha de visão; Se a câmera não é possível ver as mãos, os ponteiros não podem ser usados.

Entrada de fala é bom na atravessando tarefas complexas, porque ela permite que os usuários recortem por meio de menus aninhados com um comando (por exemplo, "Mostre-me os filmes feitos pelo studio Laika.") e também muito econômico quando combinado com outra modalidade (por exemplo, "Face para mim" comando orienta o holograma de um usuário está olhando para o usuário). No entanto, a entrada de fala pode não funcionar bem no ambiente barulhento ou talvez não apropriados em um espaço muito silencioso.

Além de gestos e fala, portáteis controlados controladores (por exemplo, Oculus touch, proceder, etc.) são muito populares métodos de entrada, porque eles são fáceis de usar e precisas, aproveitar das pessoas [proprioception](https://en.wikipedia.org/wiki/Proprioception)e fornecer dicas hápticos passivas. No entanto, esses benefícios são fornecidos ao custo de não poder ser bare-hands e usar o controle completos de dedo.

![Senso (à esquerda) e Manus VR(Right)](images/senso-and-manus-vr.jpg)<br>
*Senso (à esquerda) e Manus VR (à direita)*

Embora não seja tão populares como controladores, luvas estão ganhando força a onda MR/VR graças ao. Mais recentemente, a entrada de dupla personalidade/Lembre-se tiver começado a ganhar força como uma interface para ambientes virtuais, integrando o sensor EEG ou EMG para fone de ouvido (por exemplo, [MindMaze VR](http://www.mindmaze.com/)).

### <a name="observations-about-input-methods"></a>Observações sobre métodos de entrada

Esses são apenas uma amostra dos dispositivos de entrada disponíveis no mercado para MR/VR. Eles continuarão a se proliferam até que o setor se desenvolve e entra em acordo sobre as práticas recomendadas. Até lá, os designers devem ficar atento a novos dispositivos de entrada e ser bem familiarizado com os métodos de entrada específicos para seu projeto específico. Designers de precisam Procurar soluções criativas dentro de limitações, quando estiver em execução também para os pontos fortes do dispositivo.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>Esboço da cena e testar o headset

Quando trabalhei em 2D, eu principalmente elaborado apenas o conteúdo. No entanto, no espaço de realidade mista que não era suficiente. Tive de esboço de toda a cena imaginar melhor as relações entre os objetos de usuário e virtuais. Para ajudar a meu raciocínio espacial, comecei a esboçar cenas [Cinema 4d](https://www.maxon.net/en/products/cinema-4d/overview/) e, às vezes, criar ativos simples para protótipos nos [Maya](http://www.autodesk.com/products/maya/overview/). Eu nunca tivesse usado o programa antes de se juntar à equipe do HoloLens e eu ainda sou um iniciante, mas trabalhar com esses programas 3D certamente me ajudou a fique à vontade com a nova terminologia, tais como [sombreador](https://en.wikipedia.org/wiki/Shader) e [IK (inverso cinemática)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/).

**"Não importa a forma como eu elaborado a cena em 3D, a experiência real Headset quase nunca foi o mesmo que o esboço. É por isso que é importante testar a cena no destino headsets. "— Hae Jin Lee**

Para a criação de protótipos HoloLens, eu tentei todos os tutoriais na [tutoriais de realidade misturada](tutorials.md) para iniciar. Em seguida, eu comecei a brincar com [HoloToolkit.Unity](https://github.com/Microsoft/HoloToolkit-Unity/) que a Microsoft fornece aos desenvolvedores para acelerar o desenvolvimento de aplicativos holographic. Quando eu não conseguir Avançar com algo, eu publiquei minha pergunta para [Fórum de resposta e HoloLens pergunta](https://forums.hololens.com/categories/questions-and-answers/).

Depois de adquirir noções básicas sobre criação de protótipos HoloLens, eu queria capacitar outros não codificadores para criar um protótipo por conta própria. Então, fiz um vídeo tutorial que ensina como desenvolver um projectile simple usando o HoloLens. Eu explique resumidamente os conceitos básicos, portanto, mesmo que se você tiver zero experiência no desenvolvimento HoloLens, você deve ser capaz de acompanhar.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*Eu fiz este tutorial simples para programadores, como eu mesmo.*

Para a criação de protótipos VR, peguei cursos em [VR Dev School](http://learn.vrdev.school/) e também levou [criação de conteúdo 3D de realidade Virtual](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) no Lynda.com. Desenvolvimento VR escola fornecido-me mais conhecimento profundo na codificação e o curso de Laura me oferecida uma breve introdução à criação de ativos para VR a BOM.

## <a name="take-the-leap"></a>Levar o leap

Um ano atrás, me senti como tudo isso foi um pouco sobrecarregado. Agora posso dizer que era 100% vale o esforço. MR/VR ainda é muito jovem médio e há muitas possibilidades interessantes esperando a serem obtidos. Sinto inspirar e favorável ser capaz de reproduzir uma pequena parte em Projetando o futuro. Espero que você se Junte a mim na jornada em espaço 3D!

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>Designer de UX @Microsoft</td>
</tr>
</table>

 
