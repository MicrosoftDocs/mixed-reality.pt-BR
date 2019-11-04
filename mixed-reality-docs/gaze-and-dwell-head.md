---
title: Focar com a cabeça e esperar
description: Visão geral do modelo de entrada de focar com a cabeça e esperar
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: Realidade Misturada, focar, esperar, interação, design
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439307"
---
# <a name="head-gaze-and-dwell"></a>Focar com a cabeça e esperar

Quando as mãos estão ocupadas com ferramentas e peças, os gestos podem ser entediantes ou impossíveis. Os comandos de voz, assim como os gestos, podem não ser confiáveis em determinados contextos (por exemplo, em ambientes excessivamente barulhentos). Além disso, usar a voz para controlar computadores não é universalmente comum, mas certamente está ganhando força! O modelo de focar com a cabeça e esperar oferece o mecanismo mais familiar e fácil de dominar para trabalhar sem utilizar as mãos no HoloLens. Além disso, esse modelo é 100% confiável, independentemente da interferência de ruído e das restrições de silêncio do ambiente operacional.

## <a name="scenarios"></a>Cenários

A olhar e a pesquisa são Excel em cenários nos quais as mãos de uma pessoa estão ocupadas com outras tarefas, e a voz não é 100% confiável ou está disponível devido a restrições ambientais ou sociais. Um bom exemplo é uma pessoa que usa o HoloLens para sobrepor informações de referência ao realizar reparos no motor de um carro. Suas mãos estão ocupadas com ferramentas ou para apoiar o corpo conforme acessa o compartimento do motor. O ambiente da garagem é barulhento, com estrondos e zumbidos constantes de ferramentas, o que dificulta os comandos de voz. O Head-olhar e a pesquisa permitem que a pessoa que usa o HoloLens Navegue com confiança no material de referência sem interromper o fluxo de trabalho. 

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Focar com a cabeça e esperar</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
    </tr>
</table>


## <a name="design-principles"></a>Princípios do design

**Evite "olhar como uma arma"**

A ação de focar com a cabeça e esperar exige que o retorno visual seja intuitivo, mas seu excesso pode induzir a ansiedade. Os retornos devem ajudar um usuário a saber o que está sendo focalizando, mas não selecionar automaticamente se essa não for sua intenção. Ler textos, ícones e rótulos exige consideração adicional para dar tempo para a pessoa absorver as informações antes de selecionar.
    
**Buscar velocidade de Cachinhos dourados**
    
As interações de espera podem ter tempos diferentes com base no impacto na navegação: as funções usadas com mais frequência geralmente se beneficiam de tempos de preenchimento mais rápidos, enquanto que as funções mais consequentes podem se beneficiar de tempos de preenchimento mais longos. Ao usar um efeito de preenchimento para mostrar esses tempos, curvas de animação da cor de preenchimento podem influenciar positivamente uma sensação de tempo mais rápido. Consideração deve ser tomada para permitir a decisão do usuário a partir de substituições das velocidades de preenchimento rápidas/médias/lentas.
    
**Diga não-no para o efeito de Yo Yo**

O efeito ioiô é um padrão desconfortável de movimentação da cabeça que pode surgir quando o posicionamento do conteúdo e dos controles de focar com a cabeça e esperar força as pessoas a olharem para cima e para baixo repetidamente. Por exemplo, uma barra de navegação de lista com o botão de olhar e de duração na parte inferior induzi um loop de-Look to acessation, look up in Results, olhe Down to acessation, etc. Esse padrão resultante é desconfortável e deve ser evitado colocando-se controles de navegação em um local centralizado que requer menos suporte. O posicionamento dos botões de espera próximo aos seus efeitos é importante para o conforto.

<br>

---


## <a name="ux-guidelines-and-best-practices"></a>Diretrizes e práticas recomendadas para a experiência do usuário

### <a name="target-sizes"></a>Tamanhos do alvo
  Para ser facilmente acessível, os destinos de olhar e de duração de pesquisa precisam ser grandes o suficiente para examinar de maneira confortável e manter um rumo estável no destino pelo tempo prescrito. Recomendamos um tamanho mínimo de destino de 2 graus para alcançar a experiência mais confortável. 

### <a name="visual-feedback"></a>Feedback visual

Ao usar um preenchimento radial para representar o tempo de espera, comece do centro do botão. Uma resposta consistente é menos confusa que diferentes direções em botões diferentes. 

  * Essa regra não precisa ser seguida para interações direcionais (por exemplo, navegação para cima/para baixo/para a esquerda/para a direita etc.). Por exemplo, os Guias do Microsoft Dynamics 365 fazem uma exceção a essa regra nos botões AVANÇAR/VOLTAR, que são preenchidos da esquerda para a direita.
  * Considere a possibilidade de inverter o preenchimento radial, de fora para dentro, em cenários que exigem a ativação/desativação de um botão de alternância, por exemplo. A sensação inversa de apertar um botão é um padrão visual adequado para manter. 

### <a name="progressive-disclosure"></a>Divulgação progressiva

A divulgação progressiva significa mostrar apenas a quantidade de detalhes relevante em cada estágio de uma interação. Para a espera, isso significa que o alvo é revelado no realce (por exemplo, em um controle de lista).

 ### <a name="oversized-targets"></a>Alvos muito grandes
A região de espera pode ser maior do que o ícone inativo para facilitar o uso, como o botão Voltar nos Guias do Microsoft Dynamics 365.

### <a name="prevent-flickering-with-delayed-feedback"></a>Evite a cintilação usando retornos atrasados
Aplique um pequeno atraso antes de iniciar o retorno visual para evitar cintilação ao passar sobre um alvo de espera.
* Para botões interagir com frequência, mantenha o atraso muito curto para que o aplicativo se sinta reativo.
* Para botões que são interagindo com pouca frequência, um atraso mais longo pode ser apropriado para evitar que a interface se sinta twitchy.


<br>

---

## <a name="ui-patterns"></a>Padrões da interface do usuário

### <a name="high-frequency-buttons"></a>Botões de alta frequência

:::row:::
    :::column:::
        Botões de alta frequência são botões que são usados normalmente em um aplicativo. Um bom exemplo são os botões Voltar e Avançar nos Guias do Microsoft Dynamics 365.<br>
        <br>
        **Recommendations**<br>
  * Botões de alta frequência devem ser grandes, mais fáceis de atingir com Head-olhar
  * Fique à altura dos olhos para evitar sobrecarregar o ergonômicos.<br>
        <br>
*Imagem: botão Avançar dos guias do Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Botão Avançar dos guias do Microsoft Dynamics 365](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>Botões de baixa frequência
Botões de baixa frequência são botões que não são regularmente usados no aplicativo. Um bom exemplo é um botão para acessar o menu de configurações ou um botão para limpar toda a tarefa.

* Tente manter esses botões longe dos caminhos de ações frequentes de focar com a cabeça para evitar ativação acidental. 

<br>

---

### <a name="confirmations"></a>Confirmações

:::row:::
    :::column:::
        Quando uma ação tem um impacto significativo, como cobrar dinheiro, excluir uma tarefa ou iniciar um processo longo, é útil confirmar se a pessoa teve a intenção de selecionar o botão.<br>
        <br>
        **Recommendations**<br>
  * Mostre o realce de seleção no botão principal.
  * Revele o alvo da espera ao mesmo tempo que o realce da seleção.
  * Para o botão secundário, revele o alvo da espera ao focar com a cabeça.<br>
        <br>
*Imagem: caixa de diálogo de confirmação de guias do Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Caixa de diálogo de confirmação dos guias do Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>Botões de alternância
Botões de alternância exigem uma lógica sutil para funcionarem corretamente. Quando uma pessoa olha fixo para um botão de alternância e o ativa, ela precisa sair do botão e retornar para reiniciar a lógica de espera. É importante que os botões de alternância tenham estados ativo e inativo claros. 

<br>

---

### <a name="list-views"></a>Modos de exibição de lista

:::row:::
    :::column:::
        As exibições de lista apresentam um desafio específico para a entrada de olhar e de duração da pesquisa. As pessoas devem poder verificar o conteúdo sem sentirem que precisam tomar cuidado com os alvos de espera.<br>
        <br>
**Recommendations**<br>
  * Tenha toda a linha realçada quando Head-gazed, mas não inicia a pesquisa, a menos que Head-olhar esteja no destino de duração específico.
  * Mostrar somente o destino de duração de pesquisa quando a linha for realçada para reduzir o ruído visual.
  * Fique claro e consistente com a posição dos destinos de pesquisa.
  * Não mostre todos os destinos de pesquisa de uma só vez para evitar a interface do usuário repetitiva.
  * Reutilize o mesmo padrão o mais comum possível para estabelecer a familiaridade de UX.<br>
        <br>
*Imagem: lista de guias do Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Lista de guias do Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>Consulte também
* [Olhar e confirmar](gaze-and-commit.md)
* [Manipulação de mãos direta](direct-manipulation.md)
* [Gestos práticos](gaze-and-commit.md#composite-gestures)
* [Ponto de mãos e confirmação](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)
