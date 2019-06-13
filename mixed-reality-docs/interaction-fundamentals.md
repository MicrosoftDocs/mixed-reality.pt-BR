---
title: Visão geral de interação multimodal
description: Visão geral de interação multimodal
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, foco, direcionamento do foco, interação, design, hololens, MMR, multimodal
ms.openlocfilehash: bea205edf484a55db701e8e0d1a233234882a272
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516018"
---
# <a name="introducing-instinctual-interactions"></a>Apresentação de interações instintivas

A filosofia de interações simples e instintivas está presente em toda a plataforma de Realidade Misturada da Microsoft.  Temos três etapas para garantir que os desenvolvedores e designers de aplicativos possam fornecer interações fáceis e intuitivas para seus clientes. 

Primeiro, nos asseguramos que nossos incríveis sensores e tecnologia de entrada, incluindo o acompanhamento da mão, de olho e linguagem natural se combinassem em modelos descomplicados de interação multimodal.  Com base em nossa pesquisa, projetar e desenvolver de forma multimodal, e não com base em entradas únicas, é a chave para criar experiências instintivas.

Em segundo lugar, reconhecemos que muitos desenvolvedores têm vários dispositivos como alvo, sejam HoloLens 2 e HoloLens (1ª geração) ou HoloLens e VR.  Portanto, criamos nossos modelos de interação para que funcionem em vários dispositivos (mesmo que a tecnologia de entrada varie em cada dispositivo).  Por exemplo, interação distante em um fone de ouvido de imersão do Windows com um controlador 6DOF e interação distante em um HoloLens 2 usam as capacidades e os padrões idênticos, facilitando para os aplicativos que funcionam em vários dispositivos. Isso não só é conveniente para desenvolvedores e designers, mas também parece natural para os usuários finais. 

Por fim, ainda que reconheçamos que há milhares de interações eficazes, envolventes e mágicas possíveis no MR, descobrimos que empregar intencionalmente um único modelo de interação de ponta a ponta em um aplicativo é a melhor maneira de garantir que os usuários sejam bem-sucedidos e tenha uma ótima experiência.  Para isso, incluímos três coisas neste guia de interação:
* Estruturamos este guia de acordo com os três principais modelos de interação e os componentes e os padrões necessários para cada um
* Incluímos orientação complementar sobre os outros benefícios fornecidos por nossa plataforma
* Incluímos orientação para ajudar a selecionar o modelo de interação apropriado para seu cenário

## <a name="multimodal-interaction-models"></a>Modelos de interação multimodal

Com base na pesquisa e no trabalho com os clientes até o momento, descobrimos que três modelos de interação principais atendem à maioria das experiências de realidade misturada.

Em muitos aspectos, o modelo de interação é o modelo mental do usuário para concluir seus fluxos.  Cada um desses modelos de interação é otimizado para um conjunto de necessidades do cliente e cada um é conveniente, potente e pode ser usado sozinho. 

O gráfico abaixo é uma visão geral simplificada.  Há links para informações detalhadas de uso de cada modelo de interação nas páginas abaixo com imagens e exemplos de código. 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo</strong></td>
        <td><strong>Cenários de exemplo</strong></td>
        <td><strong>Ajustar</strong></td>
        <td><strong>Hardware</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Controladores de movimentos e mãos</a></td>
        <td>Experiências 3D espaciais, por exemplo, design e layout espacial, manipulação de conteúdo ou simulação.</td>
        <td>Excelente para novos usuários, juntamente com voz, acompanhamento ocular ou movimento de cabeça. Baixa curva de aprendizado. Experiência do usuário consistente com acompanhamento da mão e 6 controladores DoF.</td>
        <td>HoloLens 2<br>Headsets imersivos</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Mãos livres</a></td>
        <td>Experiências contextuais, nas quais as mãos de um usuário estão ocupadas, por exemplo, no aprendizado no trabalho, na manutenção.</td>
        <td>Algum aprendizado é necessário. Caso as mãos não estejam disponíveis, emparelha bem com voz e linguagem natural.</td>
        <td>HoloLens 2<br>HoloLens (1ª geração)<br>Headsets imersivos</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Focar com a cabeça e confirmar</a></td>
        <td>Clique pelas experiências, p.ex., apresentações e demonstrações 3D.</td>
        <td>Requer treinamento em HMDs, mas não em dispositivos móveis. Melhor para controladores acessíveis. Melhor para HoloLens (1ª geração).</td>
        <td>HoloLens 2<br>HoloLens (1ª geração)<br>Headsets imersivos<br>AR móvel</td>
    </tr>
</table>
<br>

A melhor maneira de garantir que não existem lacunas ou problemas na interação de sua experiência é seguir as diretrizes para um único modelo do início ao fim. 

Para acelerar o desenvolvimento e o design, incluímos informações detalhadas e links para exemplos de código e imagens em nossa cobertura de cada modelo.

Mas primeiro, as seções a seguir seguem as etapas de seleção e implementação de um desses modelos de interação.  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>No final desta página, você entenderá nossas diretrizes em:
 
* Escolhendo um modelo de interação para seu cliente
* Usando as diretrizes de modelo de interação
* Transição entre os modelos de interação
* Próximas etapas de design


## <a name="choose-an-interaction-model-for-your-customer"></a>Escolha um modelo de interação para seu cliente


Muito provavelmente, os desenvolvedores e os criadores de também já tem algumas ideias em mente dos tipos de experiência de interação que querem que seus usuários tenham.
Para incentivar uma abordagem do design voltada para o cliente, é recomendável seguir as diretrizes abaixo para selecionar o modelo de interação que é otimizado para o cliente.

### <a name="why-follow-this-guidance"></a>Por que seguir esta orientação?

* Nossos modelos de interação são testados com critérios objetivos e subjetivos, como esforço físico e cognitivo, intuitividade e capacidade de aprendizado. 
* Como a interação é diferente, as capacidades de áudio e vídeo e o comportamento de objeto também podem ser diferentes entre os modelos de interação.  
* Combinar partes de vários modelos de interação, cria o risco de capacidades conflitantes, como raios de mão simultâneos e um cursor de foco com a cabeça que pode sobrecarregar e confundir os usuários.

Aqui estão alguns exemplos de como as capacidades e os comportamentos são otimizados para cada modelo de interação.  Vemos com frequência que novos usuários têm perguntas semelhantes, como "como faço para saber se o sistema está funcionando, como saber o que posso fazer e como saber se entendi o que acabei de fazer?"

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo</strong></td>
        <td><strong>Como saber se está funcionando?</strong></td>
        <td><strong>Como saber o que posso fazer?</strong></td>
        <td><strong>Como saber o que eu acabei de fazer?</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Controladores de movimentos e mãos</a></td>
        <td>Vejo uma malha de mão, vejo uma funcionalidade de ponta do dedo ou raios de controlador/mão.</td>
        <td>Vejo uma caixa delimitadora ou alças que aparecem quando a minha mão está próxima.</td>
        <td>Posso ouvir sons e ver animações ao capturar e soltar.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Focar com a cabeça e confirmar</a></td>
        <td>Eu vejo um cursor no centro do meu campo de visão.</td>
        <td>O cursor do foco com a cabeça muda de estado quando está sobre determinados objetos.</td>
        <td>Posso ver/ouvir confirmações visuais e audíveis quando executo uma ação.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">Mãos livres (foco com a cabeça e permanência)</a></td>
        <td>Eu vejo um cursor no centro do meu campo de visão.</td>
        <td>Vejo um indicador de progresso quando paro em um objeto com o qual posso interagir.</td>
        <td>Posso ver/ouvir confirmações visuais e audíveis quando executo uma ação.</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Mãos livres (comandos de voz)</a></td>
        <td>Vejo um indicador de escuta e legendas que mostram o que o sistema ouviu.</td>
        <td>Obtenho prompts de voz e dicas.  Quando digo "o que posso dizer?" Vejo feedback.</td>
        <td>Vejo/ouço confirmações visuais e auditivas quando emito um comando ou obtenho uma experiência de usuário de desambiguidade quando necessário.</a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a>Veja as perguntas que descobrimos ajudar as equipes e selecionar um modelo de interação:
 
1.  P:  Meus usuários desejam tocar em hologramas e executar manipulações holográficas de precisão?<br><br>
R:  Nesse caso, confira o modelo de interação de mãos e ferramentas para direcionamento de precisão e a manipulação com as mãos ou com controladores de movimento.
 
2.  P:  Meus usuários precisam manter as mãos livres para tarefas do mundo real?<br><br>
R:  Nesse caso, examine o modelo de interação mãos livres, que fornece uma ótima experiência de mãos livres por meio de interações de movimento e voz.
 
3.  P:  Meus usuários têm tempo para aprender as interações de meu aplicativo de realidade misturada ou precisam das interações com a curva de aprendizado mais baixa possível?<br><br>
R:  Recomendamos o modelo de mãos e ferramentas para a mais baixa curva de aprendizado e interações mais intuitivas, desde que os usuários sejam capazes de usar as mãos para interagir.
 
4.  P:  Meus usuários usam controladores de movimento para apontar e manipular?<br><br>
R:  O modelo de mãos e de ferramentas inclui todas as diretrizes para uma ótima experiência com os controladores de movimento.
 
5.  P:  Meus usuários usam um controlador de acessibilidade ou um controlador de Bluetooth comum, como um clicker?<br><br>
R:  Recomendamos o modelo de foco com a cabeça e de confirmação para todos os controles não acompanhados.  Ele foi projetado para permitir que um usuário passe por uma experiência completa com uma mecânica simples de “direcionar e confirmar". 
 
6.  P: Meus usuários progridem por uma experiência somente "clicando" (por exemplo em um ambiente de apresentação de slides 3D), em vez de navegar por layouts densos de controles de interface de usuário?<br><br>
R:  Caso os usuários não precisem controlar muita interface de usuário, o foco de cabeça e confirmação oferece uma opção que pode ser aprendida, na qual os usuários não precisam se preocupar com direcionamento. 
 
7.  P:  Meus usuários usam o HoloLens (1ª geração) e HoloLens 2/ Imersivo do Windows (headsets VR)<br><br>
R:  Como o foco de cabeça e confirmação é o modelo de interação do HoloLens (1ª geração), recomendamos que os criadores que oferecem suporte ao HoloLens (1ª geração) use o foco de cabeça e confirmação para os recursos ou modos que os usuários podem experimentar em um headset HoloLens (1ª geração).  Consulte a próxima seção abaixo em *Transição de modelos de interação* para obter detalhes sobre como ter uma excelente experiência em várias gerações do HoloLens.
 
8.  P: E quanto aos usuários que normalmente usam dispositivos móveis (que abrangem um grande espaço ou o movimento entre espaços) em relação aos usuários que tendem a trabalhar em um único espaço?<br><br>
R:  Qualquer um dos modelos de interação funcionará para esses usuários.  

> [!NOTE]
> Mais diretrizes específicas ao design de aplicativo [em breve](index.md#news-and-notes).


## <a name="transition-interaction-models"></a>Modelos de interação de transição
Também há casos em que seus casos de uso podem exigir a utilização de mais de um modelo de interação.  Por exemplo, o “fluxo de criação” do aplicativo utiliza o modelo de mãos e controladores de movimento, mas você deseja empregar um modo mãos livres para técnicos de campo.  

Caso sua experiência precise de vários modelos de interação, descobrimos que muitos usuários finais podem encontrar dificuldade para fazer a transição de um modelo para outro – especialmente os usuários que são novos na realidade misturada.

> [!Note]
> Para ajudar a guiar os designers e desenvolvedores por meio de opções que podem ser difíceis na MR, estamos trabalhando em mais orientações para usar vários modelos de interação.
 

## <a name="see-also"></a>Consulte também
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Focar com a cabeça e esperar](gaze-and-dwell.md)
* [Manipulação direta com as mãos](direct-manipulation.md)
* [Apontar e confirmar com as mãos](point-and-commit.md)
* [Gestos](gestures.md)
* [Comando de voz](voice-design.md)
* [Controladores de movimentos](motion-controllers.md)
* [Projeto de som espacial](spatial-sound-design.md)
* [Projeto de mapeamento espacial](spatial-mapping-design.md)
* [Conforto](comfort.md)

