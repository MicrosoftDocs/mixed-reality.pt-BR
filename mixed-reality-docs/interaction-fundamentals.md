---
title: Interações instintivas
description: Conheça a filosofia de simples interações instintivas, presentes em toda a plataforma da realidade misturada.
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, foco, direcionamento do foco, interação, design, hololens, MMR, multimodal
ms.openlocfilehash: 6b54d6e844c1b501a0835fc3a48deb4932ba551d
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "74539727"
---
# <a name="introducing-instinctual-interactions"></a>Apresentação de interações instintivas

![Manipulação distante com as mãos](images/04_InteractionFundamentals.png)

A filosofia de interações simples e instintivas está presente em toda a plataforma de MR (realidade misturada). Temos três etapas para os desenvolvedores e designers de aplicativos fornecerem interações fáceis e intuitivas para os clientes deles. 

Primeiro, fizemos nossos incríveis sensores e tecnologia de entrada, incluindo o acompanhamento da mão, de olho e de linguagem natural, serem combinados em modelos descomplicados de interação multimodal.  
Com base em nossa pesquisa, projetar e desenvolver em uma estrutura multimodal (em vez de com base em entradas individuais) é o segredo para criar experiências instintivas.

Em segundo lugar, reconhecemos que muitos desenvolvedores destinam suas criações a vários dispositivos HoloLens, por exemplo, HoloLens 2 e HoloLens (1ª geração) ou então HoloLens e VR.  
Sendo assim, criamos nossos modelos de interação para que funcionem em vários dispositivos (mesmo que a tecnologia de entrada varie em cada dispositivo).  
Por exemplo, a interação distante em um headset imersivo do Windows com um controlador 6DoF e interação distante em um HoloLens 2 usam as funcionalidades e os padrões idênticos, facilitando o desenvolvimento de aplicativos entre dispositivos e oferecendo uma sensação natural para interações do usuário. 

Ainda que reconheçamos que há milhares de interações eficazes, envolventes e mágicas possíveis na MR, descobrimos que empregar intencionalmente um único modelo de interação de ponta a ponta em um aplicativo é a melhor maneira de garantir que os usuários sejam bem-sucedidos e tenha uma ótima experiência. Para isso, incluímos três coisas neste guia de interação:
* Diretrizes específicas sobre os três principais modelos de interação e os componentes e os padrões necessários para cada um.
* Diretrizes complementares sobre os outros benefícios fornecidos por nossa plataforma.
* Diretrizes gerais para ajudar a selecionar o modelo de interação apropriado para seu cenário de desenvolvimento.

## <a name="multimodal-interaction-models"></a>Modelos de interação multimodal

Com base na pesquisa e nos comentários dos clientes, descobrimos que três modelos de interação principais atendem à maioria das experiências de realidade misturada. Em muitos aspectos, o modelo de interação é o modelo mental do usuário para a maneira como concluir um fluxo de trabalho. Cada um desses modelos de interação é otimizado para um conjunto de necessidades do cliente e é conveniente, avançado e utilizável quando usado corretamente. 

O gráfico abaixo é uma visão geral simplificada. Há links para informações detalhadas de uso de cada modelo de interação nas páginas abaixo com imagens e exemplos de código. 

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
        <td>Excelente para novos usuários, juntamente com voz, acompanhamento ocular ou foco com a cabeça. Baixa curva de aprendizado. Experiência do usuário consistente com acompanhamento da mão e controladores 6DoF.</td>
        <td>HoloLens 2<br>Headsets imersivos</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Mãos livres</a></td>
        <td>Experiências contextuais, nas quais as mãos de um usuário estão ocupadas, por exemplo, no aprendizado no trabalho e na manutenção.</td>
        <td>Algum aprendizado é necessário. Caso as mãos não estejam disponíveis, o dispositivo emparelha bem com voz e linguagem natural.</td>
        <td>HoloLens 2<br>HoloLens (1ª geração)<br>Headsets imersivos</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Focar e confirmar</a></td>
        <td>Clique pelas experiências, p.ex., apresentações e demonstrações 3D.</td>
        <td>Requer treinamento em HMDs, mas não em dispositivos móveis. Melhor para controladores acessíveis. Melhor para HoloLens (1ª geração).</td>
        <td>HoloLens 2<br>HoloLens (1ª geração)<br>Headsets imersivos<br>AR móvel</td>
    </tr>
</table>
<br>

A melhor maneira de garantir que não existem lacunas na experiência de interação do usuário é seguir as diretrizes para um único modelo, do início ao fim.

As seções a seguir seguem as etapas de seleção e implementação de um desses modelos de interação.  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>No final desta página, você entenderá nossas diretrizes em:
 
* Escolhendo um modelo de interação para seu cliente
* Implementar o modelo de interação
* Transição entre os modelos de interação
* Próximas etapas de design


## <a name="choose-an-interaction-model-for-your-customer"></a>Escolha um modelo de interação para seu cliente

Na maioria dos casos, os desenvolvedores e criadores pensaram nos tipos de interações que seus clientes podem ter. Para incentivar uma abordagem do design voltada para o cliente, é recomendável seguir as orientações abaixo para selecionar o modelo de interação que é otimizado para o cliente.

### <a name="why-follow-this-guidance"></a>Por que seguir esta orientação?

* Nossos modelos de interação são testados com critérios objetivos e subjetivos, tais como esforço físico e cognitivo, intuitividade e capacidade de aprendizado. 
* Como as interações são diferentes, as funcionalidades de áudio/visuais e o comportamento de objeto podem ser diferentes entre os modelos de interação.  
* Combinar partes de vários modelos de interação cria o risco de funcionalidades conflitantes, tais como raios de mão simultâneos e um cursor de foco com a cabeça. Isso pode sobrecarregar e confundir os usuários.

Aqui estão alguns exemplos de como as capacidades e os comportamentos são otimizados para cada modelo de interação. Vemos com frequência que novos usuários têm perguntas semelhantes, como _"como faço para saber se o sistema está funcionando”_ , _“como saber o que posso fazer”_ e _“como saber se entendi o que acabei de fazer?"_

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
        <td>Vejo uma malha de mão, uma funcionalidade de ponta do dedo ou raios de mão/controlador.</td>
        <td>Vejo alças ou uma caixa delimitadora é exibida quando a minha mão está próxima de um objeto.</td>
        <td>Posso ouvir sons e ver animações ao capturar e soltar.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Focar com a cabeça e confirmar</a></td>
        <td>Eu vejo um cursor no centro do meu campo de visão.</td>
        <td>O cursor muda de estado quando está sobre determinados objetos.</td>
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
        <td>Obtenho prompts de voz e dicas. Quando digo: "O que posso falar?" Vejo feedback.</td>
        <td>Vejo/ouço confirmações visuais e auditivas quando emito um comando ou obtenho uma experiência de usuário de desambiguação quando necessário.</a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a>Veja as perguntas que descobrimos que ajudam as equipes e selecionar um modelo de interação:
 
1.  P:  Meus usuários desejam tocar em hologramas e executar manipulações holográficas de precisão?<br><br>
R:  Nesse caso, confira o modelo de interação de mãos e controladores de movimentos para direcionamento de precisão e manipulação.
 
2.  P:  Meus usuários precisam manter as mãos livres para tarefas do mundo real?<br><br>
R:  Nesse caso, examine o modelo de interação de mãos livres, que fornece uma ótima experiência de mãos livres por meio de interações de movimento e voz.
 
3.  P:  Meus usuários têm tempo para aprender as interações de meu aplicativo de realidade misturada ou precisam das interações com a curva de aprendizado mais baixa possível?<br><br>
R:  Para a mais baixa curva de aprendizado e as interações mais intuitivas, recomendamos o modelo de mãos e controladores de movimentos, desde que os usuários sejam capazes de usar suas mãos para interação.
 
4.  P:  Meus usuários usam controladores de movimento para apontar e manipular?<br><br>
R:  O modelo de mãos e de controladores de movimentos inclui todas as orientações para uma ótima experiência com os controladores de movimentos.
 
5.  P:  Meus usuários usam um controlador de acessibilidade ou um controlador de Bluetooth comum, como um clicker?<br><br>
R:  Recomendamos o modelo de foco com a cabeça e de confirmação para todos os controladores não acompanhados. Ele foi projetado para permitir que um usuário passe por uma experiência completa com um mecanismo simples de "direcionar e confirmar". 
 
6.  P: Meus usuários progridem por uma experiência somente "clicando" (por exemplo em um ambiente de apresentação de slides 3D), em vez de navegar por layouts densos de controles de interface de usuário?<br><br>
R:  Caso os usuários não precisem controlar muita interface de usuário, o foco de cabeça e confirmação oferece uma opção que pode ser aprendida, na qual os usuários não precisam se preocupar com direcionamento. 
 
7.  P:  Meus usuários usam o HoloLens (1ª geração) e HoloLens 2/headsets imersivos do Windows Mixed Reality (VR)?<br><br>
R:  Como o foco com a cabeça e confirmação é o modelo de interação do HoloLens (1ª geração), recomendamos que os criadores que dão suporte ao HoloLens (1ª geração) usem o foco com a cabeça e confirmação para os recursos ou modos que os usuários experimentarão em um headset HoloLens (1ª geração). Consulte a próxima seção abaixo em *Transição de modelos de interação* para obter detalhes sobre como ter uma excelente experiência em várias gerações do HoloLens.
 
8.  P: E quanto aos usuários que normalmente usam dispositivos móveis, que abrangem um grande espaço ou o movimento entre espaços, em relação aos usuários que tendem a trabalhar em um único espaço?<br><br>
R:  Qualquer um dos modelos de interação funcionará para esses usuários.  

> [!NOTE]
> Mais diretrizes específicas ao design de aplicativo [em breve](news.md).


## <a name="transitioning-interaction-models"></a>Modelos de interação de transição
Também há casos de uso que podem exigir a utilização de mais de um modelo de interação. Por exemplo, o fluxo de criação do aplicativo utiliza o modelo de interação de _“mãos e controladores de movimentos”_ , mas convém empregar um modo de mãos livres para técnicos de campo.
Caso sua experiência precise de vários modelos de interação, tenha em mente que muitos usuários podem encontrar dificuldade ao fazer a transição de um modelo para outro, especialmente os usuários novatos na realidade misturada.

> [!Note]
> Estamos trabalhando constantemente em mais diretrizes que estarão disponíveis para desenvolvedores e designers, informando-os sobre como, quando e por que usar vários modelos de interação de realidade misturada.
 

## <a name="see-also"></a>Veja também
* [Conforto](comfort.md)
* [Interação ocular](eye-gaze-interaction.md)
* [Acompanhamento ocular no HoloLens 2](eye-tracking.md)
* [Focar e confirmar](gaze-and-commit.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Mãos – Manipulação direta](direct-manipulation.md)
* [Mãos – Gestos](gaze-and-commit.md#composite-gestures)
* [Mãos – Apontar e confirmar](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Controladores de movimentos](motion-controllers.md)
* [Mapeamento espacial](spatial-mapping.md)
* [Projeto de som espacial](spatial-sound-design.md)
* [Entrada de voz](voice-input.md)


