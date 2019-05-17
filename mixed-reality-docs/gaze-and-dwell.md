---
title: Olhar head e duração
description: Visão geral do modelo de entrada olhar head e duração
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: Misto realidade, olhar, duração, interação, de design
ms.openlocfilehash: 05457b35c13422c8aa6663bdf52a489a4f5afdaa
ms.sourcegitcommit: b5bad4eeb5cdd0c2a7b639442656c306e8b5853b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65813989"
---
# <a name="head-gaze-and-dwell"></a>Olhar head e duração

Quando prático está ocupados com partes e as ferramentas, gestos podem ser entediante ou impossível. Os comandos de voz, como gestos, podem não ser confiáveis em determinados contextos, por exemplo, sob condições excessivamente altos. Além disso, usando a voz para controlar computadores não universalmente comum, mas certamente está ganhando steam! Olhar head e duração oferece o mecanismo mais familiar e fácil em mestre para trabalho heads-up e viva-voz em HoloLens. Além disso, o head-olhar e a duração é 100% confiável independentes de restrições de interferência nem de silêncio de ruído no ambiente operacional.

## <a name="scenarios"></a>Cenários

Olhar head e duração se destaca em cenários onde as mãos de uma pessoa estão ocupadas com outras tarefas e voz não for 100% confiáveis nem Enable devido a restrições de redes sociais ou ambientais. Um bom exemplo é uma pessoa use um HoloLens para informações de referência durante a correção de um mecanismo de carro de sobreposição. Laboratórios práticos estão ocupados com ferramentas ou dar suporte a seu corpo conforme elas lean no compartimento de mecanismo. O espaço de garagem é alto, com a constante quebrar e zumbido das ferramentas, dificultando a comandos de voz. Olhar head e duração permite que a pessoa o HoloLens para navegar com confiança sua material de referência sem interromper seu fluxo de trabalho. 

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
    </tr>
     <tr>
        <td>Olhar head e duração</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
    </tr>
</table>

## <a name="goals"></a>Metas

Fornece um mecanismo para interações totalmente viva-voz, sem o uso de voz.

## <a name="design-principles"></a>Princípios de design

1. Evitar "Olhares como uma arma"

    Olhar head e duração requer comentários visuais para que seja intuitiva, mas muitos comentários podem induzir a ansiedade. Os comentários devem ajudar um usuário sabe o que direcionada, mas a seleção automática não-lo em relação a sua intenção. Ler texto, ícones e rótulos requer uma consideração extra para fornecer uma sala de pessoa para absorver as informações antes de selecionar.
    
2. Busca de velocidade Cachinhos Dourados
    
    Interações de duração de exibição podem ter temporizadores diferentes com base no impacto do painel de navegação - funções usadas com mais frequência geralmente se beneficiará tempos mais rápidos de preenchimento, enquanto as funções mais CONSEQUENCIAIS podem se beneficiar de tempos de preenchimento. Ao usar um efeito de preenchimento para mostrar esses temporizadores, curvas de animação da cor de preenchimento positivamente podem influenciar uma sensação de tempos mais rápidos de preenchimento. Consideração deve ser tomada para habilitar a decisão de usuário do fast/médio/lento preencher substituições de velocidade.
    
3. Digamos que pseudocódigos para efeito de yo-yo

    O efeito de yo-yo é um padrão desconfortável de movimentação do cabeçote que pode surgir quando o posicionamento de controles de conteúdo e olhar head e duração força pessoas constantemente procurar e reduzir verticalmente várias vezes. Por exemplo, uma barra de navegação da lista com o botão de olhar head e duração de exibição na parte inferior induz um loop do - aparência para baixo lidam bem com, pesquisar em resultados, procure lidam bem com, etc. Esse padrão resultante é desconfortável e deve ser evitado, colocando os controles de navegação em um local centralizado que exige menos back bidirecional. Posicionamento dos botões de duração em relação a seus efeitos se torna importante de conforto.

## <a name="ux-guidelines-and-best-practices"></a>Práticas recomendadas e diretrizes de experiência do usuário

### <a name="target-sizes"></a>Tamanhos do alvo
  Para ser facilmente acessível, olhar head e lidam bem com destinos precisam ser grande o suficiente para o destino comforatably e mantenha de um cabeçalho stabily no destino por período determinado. É recomendável um tamanho de destino mínimo de 2 graus para alcançar a experiência mais confortável. 

### <a name="visual-feedback"></a>Feedback visual

Ao usar um preenchimento radial para representar o temporizador de duração, inicie-o do centro do botão. Uma resposta consistente é menos confusa que todas as direções diferentes nos botões diferentes. 

  * Essa regra pode ser interrompida para interações direcionais (por exemplo, etc. para cima/baixo/esquerda/direita, nav.). Por exemplo, Microsoft Dynamics 365 guias faz uma exceção em Avançar/voltar sendo deixado preenche à direita.
  * Considere a possibilidade de inversão de preenchimento radial de fora, para cenários como ativar/desativar um botão de logoff. A inversa sensação de apertar um botão é um bom padrão visual para manter. 

### <a name="progressive-disclosure"></a>Divulgação progressiva

Divulgação progressiva significa, mostrando apenas a quantidade de detalhes é relevante em cada estágio de uma interação. Para a duração, isso significa que o destino de duração é revelado no realce (por exemplo, em um controle de lista).

 ### <a name="oversized-targets"></a>Destinos muito grandes
Região de duração de exibição pode ser maior do que o ícone de inativo para torná-lo mais fácil de usar, como o botão Voltar no Microsoft Dynamics 365 guias.

### <a name="prevent-flickering-with-delayed-feedback"></a>Evitar a cintilação com comentários atrasado
Use um pequeno atraso antes de iniciar o feedback visual para evitar a cintilação quando alguém passa sobre um destino de duração.
* Para botões inteacted com frequência, mantenha o atraso muito curto para que o aplicativo parece reativo.
* Para os botões são interagidos infrequenctly um atraso maior pode ser apropriados para evitar a interface se sentindo twitchy.

## <a name="ui-patterns"></a>Padrões de interface do usuário

### <a name="high-frequency-buttons"></a>Botões de alta frequência
![Botão Avançar de guias do Microsoft Dynamics 365](images/GuideNextButton.png "botão Avançar de guias do Microsoft Dynamics 365") os botões de alta frequência são aqueles que são usados normalmente em um aplicativo. Um bom exemplo de estes são os botões Voltar e Avançar no Microsoft Dynamics 365 guias.

Botões de alta frequência devem...
* botões maiores, mais fácil de atingir com olhar head
* Mantenha-se quase altura de olho para evitar sobrecarregar ergonômicos.

### <a name="low-frequency-buttons"></a>Botões de baixa frequência
Botões de baixa frequência são aqueles que não são interagido como regularmente em todo o aplicativo. Um bom exemplo pode ser um botão para acessar o menu de configurações, ou um botão para limpar todo o trabalho.

* Tente manter esses botões fora frequentes caminhos head olhar para evitar a ativação acidental. 

### <a name="confirmations"></a>Confirmações
![Caixa de diálogo de confirmação do Microsoft Dynamics 365 guias](images/GuidesConfirmation.png "caixa de diálogo de confirmação do Microsoft Dynamics 365 guias")

Quando uma ação tem um impacto significativo, como cobrar dinheiro, excluindo o trabalho ou iniciar um processo longo, ele é útil confirmar que uma pessoa deve selecionar um botão. Para olhar head e duração há interfaces de usuário são alguns padrões e considerações para caixas de diálogo de confirmação:

  * Mostre realce de seleção no botão principal.
  * Revelar lidam bem com destino ao mesmo tempo que o realce de seleção.
  * Para o botão secundário, revele o destino de duração na cabeça olhar.
        
### <a name="toggle-buttons"></a>Botões de alternância
Botões de alternância exigem alguma lógica sutil funcione corretamente. Quando uma pessoa dwells em um botão de alternância e ativos-la, eles precisarão sair do botão e, em seguida, retornar para reiniciar a lógica de duração. É importante que o alternáveis botões têm um ativo não criptografado versus estado inativo. 

### <a name="list-views"></a>Modos de exibição de lista
![Diálogo de confirmação de guias do Microsoft Dynamics 365](images/GuidesListView.png "diálogo de confirmação de guias do Microsoft Dynamics 365") modos de exibição de lista um desafio específico para olhar head e lidam bem com a entrada. As pessoas precisam ser capaz de examinar o conteúdo sem se sentindo como que precise tiptoe em torno de destinos de duração. 

Algumas dicas para criar exibições de lista:
* ter toda a linha realçar quando gazed a cabeça, mas não começa a duração, a menos que seja de cabeça olhar no destino de duração de exibição específico.
* mostra o duração de destino somente quando a linha é realçada para reduzir o ruído visual.
* ser claro e consistente com a posição de destinos de duração.
* Não mostrar que todos os destinos de uma vez para evitar repetitiva da interface do usuário de duração da pesquisa
* reutilizar o mesmo padrão sempre que possível para estabelecer a familiaridade da experiência do usuário
 
 ## <a name="see-also"></a>Consulte também
* [Manipulação direta](direct-manipulation.md)
* [Apontar e confirmar](point-and-commit.md)
* [Conceitos básicos de interação](interaction-fundamentals.md)
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Foco e voz](voice-design.md)
