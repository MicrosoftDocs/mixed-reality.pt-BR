---
title: Visão geral de interação multimodal
description: Visão geral da interação multimodal
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: Misto realidade, olhar, olhar direcionamento, interação, de design
ms.openlocfilehash: f52a0cd8ec53bfe0f4c5da2c054c538eda1c93ca
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993597"
---
# <a name="introducing-instinctual-interactions"></a>Introdução ao instinctual interações
A filosofia de interações simples, instinctual entrelaçada-se em toda a plataforma Microsoft de realidade misturada.  Pegamos três etapas para garantir que os desenvolvedores e designers de aplicativos podem fornecer as interações e intuitivas para seus clientes. 

Primeiro, tornamos-se de que nosso sensores incríveis e a tecnologia de entrada, incluindo o acompanhamento de mão, acompanhamento a olho nu e linguagem natural, combinam em modelos de interação multimodal contínuo.  Com base em nossa pesquisa, projetar e desenvolver multimodally – e não com base em entradas únicas--é a chave para a criação de experiências instinctual.

Em segundo lugar, reconhecemos que muitos desenvolvedores direcionar vários dispositivos, se isso significa que 2 HoloLens e HoloLens (1º gen) ou HoloLens e VR.  Portanto, criamos nossos modelos de interação funcione em todos os dispositivos (mesmo que a tecnologia de entrada varia em cada dispositivo).  Por exemplo, interação mais distante em um fone de ouvido imersão do Windows com um controlador 6DOF e interação mais distante em um 2 HoloLens os dois usam as capacidades idênticas e os padrões, tornando mais fácil para aplicativos entre dispositivos. Não é apenas nesse conveniente para desenvolvedores e designers, mas ele parece natural para os usuários finais. 

Por fim, reconhecemos que há milhares de eficaz, envolventes, e interações de mágicas possíveis no MR, descobrimos que intencionalmente empregar um modelo de interação única ponta a ponta em um aplicativo é a melhor maneira de garantir que os usuários forem bem-sucedidas e tenha uma ótima experiência.  Para esse fim, incluímos três coisas neste guia de interação:
* Podemos estruturou essa orientação sobre os três modelos de interação primário e os componentes e os padrões de para cada
* Incluímos orientação complementar sobre os outros benefícios de nossa plataforma fornece
* Incluímos orientação para ajudar a selecionar o modelo de interação apropriado para seu cenário


## <a name="three-multimodal-interaction-models"></a>Três modelos de interação multimodal
Com base em nossa pesquisa e trabalho com clientes até o momento, descobrimos que três modelos de interação primário atender a maioria das experiências de realidade misturada.

Em muitos aspectos, o modelo de interação é o modelo mental do usuário para concluir seus fluxos.  Cada um desses modelos de interação é otimizada para um conjunto de necessidades do cliente, e cada um é conveniente, potente e pode ser usada em seus próprios méritos. 

O gráfico abaixo é uma visão geral simplificada.  Informações detalhadas de uso de cada modelo de interação é vinculadas nas páginas abaixo com imagens e exemplos de código.  

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
        <td><strong>ajustar</strong></td>
        <td><strong>Hardware</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Mãos e ferramentas</a></td>
        <td>Experiências espaciais 3D<br>Por exemplo, espacial layout e design, manipulação de conteúdo ou simulação</td>
        <td>Ótimo para novos usuários<br>Baixa curva de aprendizado<br>Com base na fácil capacidades visual<br>Experiência do usuário consistente em mão de acompanhamento e controladores de DoF 6<br>Olhares excelente quando combinado com voz, de acompanhamento a olho nu ou head</td>
        <td>HoloLens 2<br>Windows envolventes com controladores 6DOF</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Mãos livres</a></td>
        <td>Experiências contextuais, onde as mãos do usuário estiverem ocupadas, por exemplo, sobre o trabalho de aprendizado, manutenção</td>
        <td>Alguns de aprendizado necessário<br>Se não estiverem disponíveis intervenção<br>pares bem com voz e de linguagem natural</td>
        <td>HoloLens 2<br>HoloLens (1ª geração)<br> Imersão do Windows</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Olhar head e confirmar</a></td>
        <td>Por exemplo, 3D apresentações, demonstrações experiências de Clickthrough</td>
        <td>Requer treinamento em HMDs, mas não em dispositivos móveis<br>Melhor para controladores acessíveis<br>Melhor para HoloLens (1ª geração)</td>
        <td>HoloLens 2<br>HoloLens (1ª geração)<br> Imersão do Windows<br> Mobile AR</td>
    </tr>
</table>
<br>

A melhor maneira de garantir que não existem lacunas ou buracos na interação para a sua experiência é seguir as diretrizes para um único modelo do início ao fim. 

Para acelerar o desenvolvimento e design, incluímos informações detalhadas e links para exemplos de código e imagens dentro de nossa cobertura de cada modelo.

Mas primeiro, as seções a seguir siga as etapas de seleção e implementação de um desses modelos de interação.  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>No final desta página, você entenderá nossas diretrizes em:
 
* Escolhendo um modelo de interação para seu cliente
* Usando as diretrizes de modelo de interação
* A transição entre os modelos de interação
* Próximas etapas de design

## <a name="choosing-an-interaction-model-for-your-customer"></a>Escolhendo um modelo de interação para seu cliente

Provavelmente, os desenvolvedores e os criadores já tem algumas ideias em mente dos tipos de experiência de interação que desejarem para seus usuários.
Para incentivar uma abordagem voltada para projetar, é recomendável seguir as diretrizes abaixo para selecionar o modelo de interação é otimizado para seu cliente.

### <a name="why-follow-this-guidance"></a>Por que siga esta orientação?

* Nossos modelos de interação são testados para o objetivo e critérios subjetivos como físico e cognitivo esforço, intuitiveness e learnability. 
* Como interação é diferente, as capacidades de áudio e vídeo e o comportamento de objeto também podem ser diferentes entre os modelos de interação.  
* Combinar partes de vários modelos de interação, cria o risco de capacidades de concorrentes, como raios de mão simultâneas e um cursor de olhar, que sobrecarregar e confundir os usuários.

Aqui estão alguns exemplos de como as capacidades e comportamentos são otimizados para cada modelo de interação.  Vemos com frequência novos usuários como perguntas semelhantes, como "como faço para saber se o sistema estiver funcionando, como saber o que posso fazer, e como saber se é compreender o que eu acabei de fazer?"

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
        <td><strong>Como sabê-lo está funcionando?</strong></td>
        <td><strong>Como saber o que posso fazer?</strong></td>
        <td><strong>Como saber o que eu acabei de fazer?</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Mãos e ferramentas</a></td>
        <td>Eu vejo uma mão de malha, vejo uma funcionalidade de ponta do dedo ou mão / controlador raios.</td>
        <td>Eu vejo uma caixa delimitadora que aparecem quando a minha mão está próximo ou identificadores grabbable.</td>
        <td>Posso ouvir sons e ver animações na captura e versão.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Olhar head e confirmar</a></td>
        <td>Eu vejo um cursor no centro do meu campo de visão.</td>
        <td>O cursor de olhar muda de estado quando estiver sobre determinados objetos.</td>
        <td>Posso ver / ouvir confirmações visuais e audíveis quando eu executar ação.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">Viva-voz (olhar e duração)</a></td>
        <td>Eu vejo um cursor no centro do meu campo de visão.</td>
        <td>Eu vejo um indicador de progresso quando eu lidam bem com um objeto interagível.</td>
        <td>Posso ver / ouvir confirmações visuais e audíveis quando eu executar ação.</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Viva-voz (comandos de voz)</a></td>
        <td>Eu vejo um indicador de escutando e legendas que mostram o que o sistema ouvido.</td>
        <td>Posso obter prompts de voz e dicas.  Quando eu digo "o que posso dizer?" Posso ver comentários.</td>
        <td>Posso ver / ouvir confirmações visuais e audíveis quando emitir um comando, ou obter Desambiguidade UX quando necessário.</a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a>Veja as perguntas que descobrimos que as equipes de ajudar a selecionar um modelo de interação a seguir:
 
1.  P:  Meus usuários deseja tocar hologramas e executar manipulações de holográfica precisão?
R:  Nesse caso, confira o modelo de interação de mãos e ferramentas para direcionamento de precisão e a manipulação com mãos ou controladores de movimento.
 
2.  P:  Meus usuários precisam manter suas mãos livres para tarefas do mundo real?
R:  Nesse caso, examine o modelo de interação viva-voz, que fornece uma ótima experiência viva-voz por meio de interações baseadas em olhar e voz.
 
3.  P:  Meus usuários têm tempo para aprender as interações para meu aplicativo de realidade misturada, ou eles precisam as interações com a curva de aprendizado mais baixa possível?
R:  É recomendável o modelo de mãos e ferramentas para a mais baixa curva de aprendizado e interações mais intuitivas, desde que os usuários são capazes de usar suas mãos para interação.
 
4.  P:  Fazer meus usuários usar controladores de movimento para a manipulação e apontando?
R:  O modelo de mãos e de ferramentas inclui todas as diretrizes para uma ótima experiência com os controladores de movimento.
 
5.  P:  Fazer meus usuários usar um controlador de acessibilidade ou um controlador de Bluetooth comuns, como um clicker?
R:  Recomendamos que o modelo de olhar Head e confirmação para todos os controladores não controladas.  Ele foi projetado para permitir que um usuário percorrer toda a experiência com um mecânico simple de "destino e confirmação". 
 
6.  P: Meus usuários somente de progresso por meio de uma experiência clicando em"por meio de" (por exemplo, em um apresentação de slides como ambiente 3d), em vez de navegar densos layouts de controles de interface do usuário?
R:  Se os usuários precisam controlar muitas da interface do usuário, o Head olhar e confirmação oferece uma opção de learnable em que os usuários não precisam se preocupar sobre direcionamento. 
 
7.  P:  Fazer meus usuários usar ambos os HoloLens (1º gen) e HoloLens 2 / r Windows imersivo (headsets VR):  Uma vez que o Head olhar e a confirmação é o modelo de interação para HoloLens (1º gen), é recomendável que criadores que oferecem suporte a HoloLens (1º gen) usar olhar Head e de confirmação para quaisquer recursos ou os modos de que os usuários podem enfrentar em um HoloLens (1º gen) fone de ouvido.  Consulte a próxima seção abaixo em *fazendo a transição de modelos de interação* para obter detalhes sobre como tornar uma ótima experiência para várias gerações HoloLens.
 
8.  P: E quanto para usuários que são geralmente móveis (que abrangem um grande espaço ou movendo entre espaços), em comparação com os usuários que tendem a funcionar em um único espaço?  
R:  Qualquer um dos modelos de interação funcionará para esses usuários.  

> [!NOTE]
> Mais orientações específicas para o design de aplicativos [em breve](index.md#news-and-notes).


## <a name="transition-interaction-models"></a>Modelos de interação de transição
Também há casos em que seus casos de uso podem exigir que utiliza mais de um modelo de interação.  Por exemplo, o fluxo do aplicativo"criação" utiliza o modelo de interação de mãos e ferramentas, mas você deseja empregar um modo assistido para técnicos de campo.  

Se precisar de sua experiência de vários modelos de interação, descobrimos que muitos usuários finais podem encontrar dificuldade para fazer a transição de um modelo para outro – especialmente os usuários finais não familiarizados com MR.

> [!Note]
> Para ajudar os designers de guia e desenvolvedores por meio de opções que podem ser difíceis em MR, estamos trabalhando para obter mais diretrizes para usar vários modelos de interação.
 

## <a name="see-also"></a>Consulte também
* [Olhar head e confirmar](gaze-and-commit.md)
* [Manipulação direta](direct-manipulation.md)
* [Ponto e confirmar](point-and-commit.md)
* [Focar direcionamento](gaze-targeting.md)
* [Gestos](gestures.md)
* [Design de voz](voice-design.md)
* [Controladores de movimentos](motion-controllers.md)
* [Projeto de som espacial](spatial-sound-design.md)
* [Projeto de mapeamento espacial](spatial-mapping-design.md)
* [Conforto](comfort.md)
