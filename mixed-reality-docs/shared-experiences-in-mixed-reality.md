---
title: Compartilhado experiências na realidade mista
description: Aplicativos holográfico podem compartilhar âncoras espaciais do um HoloLens para outro, permitindo que os usuários renderizar um holograma no mesmo lugar no mundo real em vários dispositivos.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: experiência compartilhada, misturadas realidade, holograma, âncora espacial, multiusuário, vários
ms.openlocfilehash: b27da1e73c927a26e33746cd2db08e67c6f70acc
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591026"
---
# <a name="shared-experiences-in-mixed-reality"></a>Compartilhado experiências na realidade mista

Hologramas não precisam permanecer particulares para apenas um usuário. Aplicativos holográfico podem compartilhar [âncoras espaciais](coordinate-systems.md) de um HoloLens, dispositivo iOS ou Android para outro, permitindo que os usuários renderizar um holograma no mesmo lugar no mundo real em vários dispositivos.

## <a name="six-questions-to-define-shared-scenarios"></a>Seis perguntas para definir cenários compartilhados

Antes de começar a criação de experiências compartilhadas, é importante definir os cenários de destino. Esses cenários ajudar a esclarecer o que você está projetando e estabelecer um vocabulário comum para ajudar a comparar e contrastar os recursos necessários em sua experiência. Noções básicas sobre o problema principal e os caminhos diferentes para soluções, é fundamental para descobrir oportunidades inerentes essa nova mídia.

Por meio de protótipos internos e explorações de nosso agências de parceiro do HoloLens, criamos seis perguntas para ajudá-lo a definir cenários compartilhados. Essas perguntas formam uma estrutura, que não se destina a ser completa, para ajudar a extrair os atributos importantes de seus cenários.

### <a name="1-how-are-they-sharing"></a>1. Como eles estão compartilhando?

Uma apresentação pode ser levada por um único usuário virtual, enquanto os vários usuários podem colaborar, ou quando um professor pode fornecer orientação para os alunos virtuais trabalhar com materiais virtuais — a complexidade do experiências aumenta com base no nível da agência, um usuário tem ou pode ter em um cenário.

![Homem e mulher com holograph na tabela](images/man-and-women-with-holograph-on-table-500px.png)

Há muitas maneiras de compartilhar, mas descobrimos que a maioria delas se enquadram em três categorias:
* **Apresentação**: Quando o mesmo conteúdo está sendo exibido para vários usuários. Por exemplo: Professor é fornecer uma palestra para vários alunos usando o mesmo material holográfico sendo apresentado para todos. O professor Entretanto pode ter seu próprias dicas e anotações que podem não estar visíveis para outras pessoas.
* **Colaboração**: Quando as pessoas estão trabalhando juntos para atingir alguns objetivos comuns. Por exemplo:  O professor deu a um projeto para saber mais sobre como executar uma cirurgia do coração. Os alunos ao emparelhar e criar uma experiência de laboratório de habilidades compartilhado que permite que os alunos médicos colaborar no modelo de coração e aprender.
* **Diretrizes de**: Quando uma pessoa está ajudando a alguém para resolver um problema em uma interação de estilo mais um. Por exemplo: O professor fornecendo diretrizes para um aluno quando ele está executando o laboratório de habilidades de cirurgia do coração na experiência de compartilhado.

### <a name="2-what-is-the-group-size"></a>2. O que é o tamanho do grupo?

**Um para um** compartilhando experiências pode fornecer uma linha de base forte e o ideal é que suas provas de conceito podem ser criadas nesse nível. Mas lembre-se de que compartilhando com grandes grupos (além de 6 pessoas) pode levar a dificuldade da técnica (dados e sistema de rede) para social (o impacto de haver uma sala com [avatares vários](https://vimeo.com/160704056)). Complexidade aumenta exponencialmente conforme você vai **pequena** à **grandes grupos**.

Descobrimos que as necessidades dos grupos podem se enquadrar em três categorias de tamanho:
* 1:1
* Pequeno < 7
* Grande > = 7

Tamanho do grupo torna-se para uma pergunta importante porque ela influencia:
* Representações de pessoas no espaço holográfica
* Escala de objetos
* Escala do ambiente

### <a name="3-where-is-everyone"></a>3. Onde estão todos?

A intensidade da realidade misturada entra em jogo quando uma experiência compartilhada podem ocorrer no mesmo local. Chamamos esse **colocalizado**. Por outro lado, quando o grupo é distribuído e pelo menos um participante que não está no mesmo espaço físico (como é geralmente o caso com VR) chamamos que uma experiência remota. Geralmente é o caso em que seu grupo tem **ambos** participantes colocalizados e remotos (por exemplo, dois grupos em salas de conferência).

![Três pessoas com holograph na tabela](images/three-people-with-holograph-on-table-500px.png)

Categorias a seguir ajudam a transmitir onde os usuários estão localizados:
* Localizado em conjunto: Todos os seus usuários será no mesmo espaço físico.
* Remoto: Todos os seus usuários será em espaços físicos separados.
* Ambos: Seus usuários ficarão uma mistura de espaços colocalizados e remotos.

Algumas razões por que essa pergunta é crucial porque ela influencia:
* Como as pessoas se comunicar?
* Por exemplo:  Se eles devem ter avatares?
* Quais objetos que eles veem. Todos os objetos são compartilhados?
* Se é necessário para se adaptar ao seu ambiente?

### <a name="4-when-are-they-sharing"></a>4. Quando estiver compartilhando?

Costumamos pensar **síncrona** experiências quando experiências compartilhadas vêm à mente: Estamos todos fazendo-la em conjunto. Mas incluir um único elemento virtual que foi adicionado por outra pessoa, e você tem um **assíncrona** cenário. Imagine uma nota ou Memorando de voz, à esquerda em um ambiente virtual. Como você lida com 100 memorandos virtuais deixados no seu design? E se forem de dezenas de pessoas com diferentes níveis de privacidade?

Considere suas experiências como uma destas categorias de tempo:
* **Forma síncrona**: Compartilhando a experiência holográfica ao mesmo tempo. Por exemplo:  Dois alunos a execução do laboratório de habilidades ao mesmo tempo.
* **Assincronamente**: Compartilhando a experiência holográfica em momentos diferentes. Por exemplo:  Dois alunos a execução do laboratório de habilidades, mas trabalhando em seções separadas em momentos diferentes.
* **Ambos**: Os usuários às vezes, compartilhará forma síncrona, mas outras vezes assincronamente. Por exemplo:  Professor de classificação a atribuição executada pelos alunos em um momento posterior e deixando notas do aluno para o próximo dia.

Algumas razões por que essa pergunta é importante porque ela influencia:
* Persistência de objeto e o ambiente. Por exemplo: Armazenando os estados para que eles possam ser recuperados.
* Perspectiva do usuário. Por exemplo: Talvez lembrar-se de que o usuário estava observando ao sair de notas.

### <a name="5-how-similar-are-their-physical-environments"></a>5. A semelhança são seus ambientes físicos?

A probabilidade de dois ambientes reais idênticos, fora de experiências colocalizadas, é reduzida, a menos que esses ambientes foram projetados para ser idênticos. Provavelmente você ter **semelhante** ambientes. Por exemplo, salas de conferência são semelhantes, eles normalmente têm uma tabela localizada centralmente cercada por cadeiras. Salas de estar, por outro lado, são geralmente **diferentes** e pode incluir qualquer número de itens de móveis em uma matriz de infinita de layouts.

![Holograph na tabela](images/holograph-on-table-500px.png)

Considere suas experiências de compartilhamento ajustando-se em uma dessas duas categorias:
* **Semelhante**: Ambientes que tendem a ter móveis semelhante, luz ambiente e som, tamanho do espaço físico. Por exemplo:  Professor está em um de sala de aula e os alunos estão em palestra hall hall palestra de B. um pode ter menos cadeiras que B, mas ambos podem ter uma mesa de física para colocar hologramas no.
* **Diferentes tipos**: Ambientes que são bastante diferentes em configurações móveis, tamanhos de sala, considerações de luz e som. Por exemplo:  Professor está em uma sala de foco, enquanto que os alunos estão em uma sala de palestra grande preenchida com os alunos e professores.

É importante pensar sobre o ambiente conforme ela influenciará:
* Como as pessoas receberão a esses objetos. Por exemplo: Se a sua experiência funciona melhor em uma tabela e o usuário não tem nenhuma tabela? Ou, em uma superfície plana floor, mas o usuário tem um espaço desorganizado.
* Escala dos objetos. Por exemplo:  Colocar um modelo de 6 pés humano em uma tabela pode ser um desafio, mas um modelo de coração funcionaria muito bem.

### <a name="6-what-devices-are-they-using"></a>6. Quais dispositivos estão usando?

Hoje você muitas vezes é provável ver experiências compartilhadas entre dois **dispositivos imersivos** (esses dispositivos podem diferir ligeiramente em termos de botões e a capacidade relativa, mas não muito) ou dois **dispositivos holográfico** considerando as soluções que está sendo direcionadas a esses dispositivos. Mas considere que **dispositivos 2D** (um participante mobile/área de trabalho ou observador) serão considerados necessários, especialmente em situações de **misto dispositivos 2D e 3D**. Noções básicas sobre os tipos de dispositivos que usando o dos participantes é importante, não apenas porque elas vêm com fidelidade diferente e restrições de dados e oportunidades, mas porque os usuários têm expectativas exclusivas para cada plataforma.

## <a name="exploring-the-potential-of-shared-experiences"></a>Explorar o potencial de experiências compartilhadas

Respostas às perguntas acima podem ser combinadas para entender melhor o seu cenário compartilhado, crystallizing os desafios, como expandir a experiência. Para a equipe da Microsoft, isso ajudou a estabelecer um roteiro para melhorar as experiências usamos hoje em dia, Noções básicas sobre a nuance desses problemas complexos e como tirar proveito das experiências compartilhadas na realidade mista.

Por exemplo, considere um dos cenários do Skype desde o lançamento do HoloLens: um usuário trabalhou por meio [como corrigir um comutador de luz quebrado](https://www.youtube.com/watch?v=iBfzs3G8BEA) com a Ajuda de uma especialista em localizado remotamente.

![Correção de um comutador de luz com assistência por meio do Skype para HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

<i>Fornece um especialista <b>1:1</b> diretrizes de sua <b>2D</b>, computador desktop para um usuário de um <b>3D, a realidade misturada</b> dispositivo. O <b>orientações</b> é <b>síncrona</b> e os ambientes físicos são <b>diferentes</b>.</i>

Uma experiência como essa é uma alteração de etapa de nossa experiência atual — aplicando o paradigma de voz e vídeo para uma nova mídia. Mas como podemos olhar para o futuro, devemos melhor definir a oportunidade de nossos cenários e criar experiências que refletem a intensidade da realidade misturada.

Considere a [ferramenta de colaboração OnSight](https://www.youtube.com/watch?v=ZOWQp0-Bkkw) desenvolvido pela laboratório de propulsão Jet do NASA. Cientistas trabalhando nos dados de missões a Marte de exploração de Marte podem colaborar com colegas em tempo real dentro dos dados do cenário Martian.

![Colaborando com os colegas separados remotamente para planejar o trabalho para a exploração de Marte](images/onsight-nasa-jpl.gif)

<i>Um cientista explora um ambiente usando um <b>3D, a realidade misturada</b> dispositivo com um <b>pequeno</b> grupo de <b>remoto</b> colegas usando <b>3D e 2D</b> dispositivos. O <b>colaboração</b> é <b>síncrona</b> (mas pode ser revisto de forma assíncrona) e os ambientes físicos (virtualmente) são <b>semelhante</b>.</i>

Experiências, como OnSight apresentam novas oportunidades para colaborar. De fisicamente apontando os elementos no ambiente virtual alocado ao lado de um colega e compartilhar sua perspectiva conforme eles explicam suas descobertas. OnSight usa das lentes de presença e de imersão para repensar o compartilhamento de experiências na realidade mista.

Colaboração intuitiva é o alicerce de conversa e trabalhando juntos e é fundamental compreender como podemos aplicar este intuição a complexidade de realidade misturada. Se podemos pode não só recriar o compartilhamento de experiências na realidade mista, mas incremente-los, será uma mudança de paradigma para o futuro do trabalho. A criação de experiências compartilhadas na realidade mista é um espaço e coisas interessante — e é só o começo.

## <a name="get-started-sharing-experiences"></a>Comece a compartilhar experiências

Dependendo do aplicativo e o cenário, haverá vários requisitos para alcançar a experiência desejada. Alguns deles incluem
* Tomada de correspondência: Capacidade para criar sessões, sessão, de anunciar e descobrir e convidar pessoas específicas, tanto localmente e remotamente para ingressarem em sua sessão.
* Ancorar compartilhamento: Capacidade de alinhar coordenadas em vários dispositivos em um espaço local comum, portanto, hologramas aparecem no mesmo lugar para todas as pessoas.
* Rede: Capacidade de ter posiciona, interações, e os movimentos de pessoas e hologramas sincronizada em tempo real em todos os participantes.
* Armazenamento de estado: Capacidade de armazenar características holograma e locais de espaço para associação de sessão intermediário, lembre-se em uma hora posterior e robustez em relação a problemas de rede.


A chave para experiências compartilhadas está vendo as mesmas hologramas no mundo em seus próprios dispositivos, frequentemente feito por meio do compartilhamento âncoras para alinhar as coordenadas entre dispositivos de vários usuários.
Para compartilhar as âncoras, use o <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espacial do Azure</a>:
* Primeiro, o usuário coloca o holograma.
* Aplicativo cria uma [âncora espacial](coordinate-systems.md) para fixar esse holograma precisamente no mundo.
* As âncoras podem ser compartilhadas para HoloLens, dispositivos iOS e Android por meio de <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espacial do Azure</a>. 

Com uma âncora espacial compartilhada, o aplicativo em cada dispositivo agora tem um sistema de coordenadas comuns nos quais eles podem colocar o conteúdo. Agora o aplicativo pode garantir para posicionar e orientar o holograma no mesmo local.
Em dispositivos do HoloLens, você também pode compartilhar as âncoras offline de um dispositivo para outro.  Use os links abaixo para decidir o que é melhor para seu aplicativo.


## <a name="see-also"></a>Consulte também
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras espaciais do Azure</a>
* [Compartilhado âncoras espaciais no DirectX](shared-spatial-anchors-in-directx.md)
* [Experiências compartilhadas no Unity](shared-experiences-in-unity.md)
* [Modo de exibição spectator](spectator-view.md)