---
title: Visão geral de interação multimodal
description: Visão geral da interação multimodal
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Misto realidade, olhar, olhar direcionamento, interação, de design, hololens, MMR, multimodal
ms.openlocfilehash: 771ebe44dc984c9d4550638bef405810d86b8d69
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730828"
---
# <a name="introducing-instinctual-interactions"></a>Introdução ao instinctual interações

A filosofia de interações simples, instinctual entrelaçada-se em toda a plataforma Microsoft misto realidade (MMR), do hardware para o software.

Essas interações instinctual utilizam todas as tecnologias de entrada disponíveis, incluindo dentro para fora de controle, acompanhamento de mão, acompanhamento a olho nu e linguagem natural, em modelos de interação multimodal contínuo. Com base em nossa pesquisa, projetar e desenvolver multimodals e não com base em entradas únicas, é essencial durante a criação de experiências instintiva.

Os modelos de interação Instinctual alinham também naturalmente em todos os tipos de dispositivo.  Por exemplo, interação mais distante em um fone de ouvido envolvente com um 6 graus de controlador de liberdade (DoF) e interação mais distante em um 2 HoloLens usam as mesmas capacidades, padrões e comportamentos.  Não é apenas nesse conveniente para desenvolvedores e designers, mas ele parece natural para os usuários finais.


Por fim, reconhecemos que há milhares de eficaz, envolventes, e interações de mágicas possíveis no MR, descobrimos que intencionalmente empregar um modelo de interação única ponta a ponta em um aplicativo é a melhor maneira de garantir que os usuários forem bem-sucedidas e tenha uma ótima experiência.  Para esse fim, incluímos três coisas neste guia de interação:
* Podemos estruturou essa orientação sobre os três modelos de interação primário e os componentes e os padrões de para cada
* Incluímos orientação complementar sobre os outros benefícios de nossa plataforma fornece
* Incluímos orientação para ajudar a selecionar o modelo de interação apropriado para seu cenário

## <a name="multimodal-interaction-models"></a>Modelos de interação multimodal

Com base em nossa pesquisa e trabalho com clientes até o momento, descobrimos três modelos de interação que atender a maioria das experiências de realidade misturada.  

Considere esses modelos de interação como modelo mental do usuário para concluir seus fluxos.

Cada um desses modelos de interação é conveniente, potente e pode ser usada em seus próprios méritos e todos são otimizados para um conjunto de necessidades do cliente. Exiba o gráfico abaixo, para benefícios de cada modelo de interação, exemplos e cenários.  

**Modelo** | **[Mãos e ferramentas](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-and-tools)** | **[Mãos livres](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-free)** | **[Mantenha o foco e confirmar](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-and-commit?)**
|--------- | --------------| ------------| ---------|
**Cenários de exemplo** | Experiências espaciais 3D, espacial, por exemplo, layout e design, manipulação ou simulação de conteúdo | Experiências contextuais, onde as mãos de um usuário estiverem ocupadas, por exemplo, em que o trabalho de aprendizado, manutenção| Clique no experiências, por exemplo, 3D apresentações, demonstrações
**ajustar** | Muito bem para novos usuários, voz wit acopladas, olho olhar principal ou de rastreamento. Baixa curva de aprendizado. Experiência do usuário consistente entre controladores de DoF 6 e acompanhamento de mão. | Algumas de aprendizado necessário. Se as mãos são pares indisponíveis bem com voz e de linguagem natural | Requer treinamento em HMDs, mas não em dispositivos móveis. Melhor para controladores acessíveis melhor para HoloLens (1ª geração) |
**Hardware** | HoloLens 2 imersivo fones de ouvido | HoloLens 2 HoloLens (1º gen) fones Imersivos em exposição | HoloLens 2 imersivo fones de ouvido | HoloLens 2 HoloLens (1º gen) fones Imersivos em exposição Mobile AR |

Informações detalhadas para usar todas as entradas disponíveis perfeitamente em conjunto em cada modelo de interação são nas páginas a seguem, bem como as ilustrações e links para conteúdo de exemplo do nosso MRTK do Unity.


## <a name="choose-an-interaction-model-for-your-customer"></a>Escolha um modelo de interação para seu cliente


Provavelmente, os desenvolvedores e os criadores de também já tem algumas ideias em mente dos tipos de experiência de interação, que eles querem que seus usuários tenham.
Para incentivar uma abordagem voltada para projetar, é recomendável seguir as diretrizes abaixo para selecionar o modelo de interação é otimizado para seu cliente.

### <a name="why-follow-this-guidance"></a>Por que siga esta orientação?

* Nossos modelos de interação são testados para o objetivo e critérios subjetivos como físico e cognitivo esforço, intuitiveness e learnability. 
* Como interação é diferente, as capacidades de áudio e vídeo e o comportamento de objeto também podem ser diferentes entre os modelos de interação.  
* Combinar partes de vários modelos de interação, cria o risco de capacidades de concorrentes, como raios de mão simultâneas e um cursor de olhar head, que sobrecarregar e confundir os usuários.

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
        <td><a href="gaze-and-commit.md">Focar com a cabeça e confirmar</a></td>
        <td>Eu vejo um cursor no centro do meu campo de visão.</td>
        <td>O cursor de olhar head muda de estado quando estiver sobre determinados objetos.</td>
        <td>Posso ver / ouvir confirmações visuais e audíveis quando eu executar ação.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">Viva-voz (Head-olhar e duração)</a></td>
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
 
1.  P:  Meus usuários deseja tocar hologramas e executar manipulações de holográfica precisão?<br><br>
R:  Nesse caso, confira o modelo de interação de mãos e ferramentas para direcionamento de precisão e a manipulação com mãos ou controladores de movimento.
 
2.  P:  Meus usuários precisam manter suas mãos livres para tarefas do mundo real?<br><br>
R:  Nesse caso, examine o modelo de interação viva-voz, que fornece uma ótima experiência viva-voz por meio de interações baseadas em olhar e voz.
 
3.  P:  Meus usuários têm tempo para aprender as interações para meu aplicativo de realidade misturada, ou eles precisam as interações com a curva de aprendizado mais baixa possível?<br><br>
R:  É recomendável o modelo de mãos e ferramentas para a mais baixa curva de aprendizado e interações mais intuitivas, desde que os usuários são capazes de usar suas mãos para interação.
 
4.  P:  Fazer meus usuários usar controladores de movimento para a manipulação e apontando?<br><br>
R:  O modelo de mãos e de ferramentas inclui todas as diretrizes para uma ótima experiência com os controladores de movimento.
 
5.  P:  Fazer meus usuários usar um controlador de acessibilidade ou um controlador de Bluetooth comuns, como um clicker?<br><br>
R:  Recomendamos que o modelo de olhar Head e confirmação para todos os controladores não controladas.  Ele foi projetado para permitir que um usuário percorrer toda a experiência com um mecânico simple de "destino e confirmação". 
 
6.  P: Meus usuários somente de progresso por meio de uma experiência clicando em"por meio de" (por exemplo, em um apresentação de slides como ambiente 3d), em vez de navegar densos layouts de controles de interface do usuário?<br><br>
R:  Se os usuários precisam controlar muitas da interface do usuário, o Head olhar e confirmação oferece uma opção de learnable em que os usuários não precisam se preocupar sobre direcionamento. 
 
7.  P:  Fazer meus usuários usar ambos os HoloLens (1º gen) e HoloLens 2 / Windows imersivo (headsets VR)<br><br>
R:  Uma vez que o Head olhar e a confirmação é o modelo de interação para HoloLens (1º gen), é recomendável que criadores que oferecem suporte a HoloLens (1º gen) usar olhar Head e de confirmação para quaisquer recursos ou os modos de que os usuários podem enfrentar em um HoloLens (1º gen) fone de ouvido.  Consulte a próxima seção abaixo em *fazendo a transição de modelos de interação* para obter detalhes sobre como tornar uma ótima experiência para várias gerações HoloLens.
 
8.  P: E quanto para usuários que são geralmente móveis (que abrangem um grande espaço ou movendo entre espaços), em comparação com os usuários que tendem a funcionar em um único espaço?<br><br>
R:  Qualquer um dos modelos de interação funcionará para esses usuários.  

> [!NOTE]
> Mais orientações específicas para o design de aplicativos [em breve](index.md#news-and-notes).


## <a name="transition-interaction-models"></a>Modelos de interação de transição
Também há casos em que seus casos de uso podem exigir que utiliza mais de um modelo de interação.  Por exemplo, o fluxo do aplicativo"criação" utiliza o modelo de interação de mãos e ferramentas, mas você deseja empregar um modo assistido para técnicos de campo.  

Se precisar de sua experiência de vários modelos de interação, descobrimos que muitos usuários finais podem encontrar dificuldade para fazer a transição de um modelo para outro – especialmente os usuários finais não familiarizados com MR.

> [!Note]
> Para ajudar os designers de guia e desenvolvedores por meio de opções que podem ser difíceis em MR, estamos trabalhando para obter mais diretrizes para usar vários modelos de interação.
 

## <a name="see-also"></a>Consulte também
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Manipulação direta](direct-manipulation.md)
* [Apontar e confirmar](point-and-commit.md)
* [Focar direcionamento](gaze-targeting.md)
* [Gestos](gestures.md)
* [Design de voz](voice-design.md)
* [Controladores de movimentos](motion-controllers.md)
* [Projeto de som espacial](spatial-sound-design.md)
* [Projeto de mapeamento espacial](spatial-mapping-design.md)
* [Conforto](comfort.md)
