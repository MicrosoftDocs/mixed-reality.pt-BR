---
title: Focar com a cabeça e esperar
description: Visão geral do modelo de entrada de focar com a cabeça e esperar
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: Realidade Misturada, focar, esperar, interação, design
ms.openlocfilehash: d522ca3a6f36995959e8e6e87482279d05bf0aa3
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387534"
---
# <a name="head-gaze-and-dwell"></a>Focar com a cabeça e esperar

Quando as mãos estão ocupadas com ferramentas e peças, os gestos podem ser entediantes ou impossíveis. Os comandos de voz, assim como os gestos, podem não ser confiáveis em determinados contextos (por exemplo, em ambientes excessivamente barulhentos). Além disso, usar a voz para controlar computadores não é universalmente comum, mas certamente está ganhando força! O modelo de focar com a cabeça e esperar oferece o mecanismo mais familiar e fácil de dominar para trabalhar sem utilizar as mãos no HoloLens. Além disso, esse modelo é 100% confiável, independentemente da interferência de ruído e das restrições de silêncio do ambiente operacional.

## <a name="scenarios"></a>Cenários

O modelo de Focar coma cabeça e esperar se destaca em cenários em que as mãos de uma pessoa estão ocupadas com outras tarefas e a voz não é 100% confiável ou não está disponível devido a restrições sociais ou ambientais. Um bom exemplo é uma pessoa que usa o HoloLens para sobrepor informações de referência ao realizar reparos no motor de um carro. Suas mãos estão ocupadas com ferramentas ou para apoiar o corpo conforme acessa o compartimento do motor. O ambiente da garagem é barulhento, com estrondos e zumbidos constantes de ferramentas, o que dificulta os comandos de voz. O modelo de Focar com a cabeça e esperar permite que a pessoa que utiliza o HoloLens navegue com confiança pelo material de referência, sem interromper seu fluxo de trabalho. 

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Focar com a cabeça e esperar</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
    </tr>
</table>

## <a name="goals"></a>Metas

Fornecer um mecanismo para interações totalmente autônomas, sem o uso de voz.

## <a name="design-principles"></a>Princípios de design

1. Evitar "Mirar como uma arma"

    A ação de focar com a cabeça e esperar exige que o retorno visual seja intuitivo, mas seu excesso pode induzir a ansiedade. Os retornos devem ajudar um usuário a saber o que está sendo focalizando, mas não selecionar automaticamente se essa não for sua intenção. Ler textos, ícones e rótulos exige consideração adicional para dar tempo para a pessoa absorver as informações antes de selecionar.
    
2. Buscar a velocidade ideal
    
    As interações de espera podem ter tempos diferentes com base no impacto na navegação: as funções usadas com mais frequência geralmente se beneficiam de tempos de preenchimento mais rápidos, enquanto que as funções mais consequentes podem se beneficiar de tempos de preenchimento mais longos. Ao usar um efeito de preenchimento para mostrar esses tempos, curvas de animação da cor de preenchimento podem influenciar positivamente uma sensação de tempo mais rápido. Consideração deve ser tomada para permitir a decisão do usuário a partir de substituições das velocidades de preenchimento rápidas/médias/lentas.
    
3. Acabar com o efeito ioiô

    O efeito ioiô é um padrão desconfortável de movimentação da cabeça que pode surgir quando o posicionamento do conteúdo e dos controles de focar com a cabeça e esperar força as pessoas a olharem para cima e para baixo repetidamente. Por exemplo, uma navegação de lista com o botão de focar com a cabeça e esperar localizado na parte inferior induz a um ciclo de "olhar para baixo para esperar", "olhar para cima para analisar os resultados" e "olhar para baixo para esperar" etc. O padrão resultante é desconfortável e deve ser evitado, posicionando os controles de navegação em um local centralizado que exija menos movimentos de vai e vem. O posicionamento dos botões de espera próximo aos seus efeitos é importante para o conforto.

## <a name="ux-guidelines-and-best-practices"></a>Diretrizes e práticas recomendadas para a experiência do usuário

### <a name="target-sizes"></a>Tamanhos do alvo
  Para serem facilmente acessados, os alvos da ação de focar com a cabeça e esperar precisam ser grandes o suficiente para serem focalizados com conforto e manter a estabilidade da cabeça no alvo pelo tempo determinado. Recomendamos um tamanho mínimo de 2 graus para alcançar a experiência mais confortável. 

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
* Para botões usados com frequência, aplique um pequeno atraso para que o aplicativo pareça reativo.
* Para botões usados com pouca frequência, um atraso maior pode ser apropriado para evitar que a interface pareça acelerada.

## <a name="ui-patterns"></a>Padrões da interface do usuário

### <a name="high-frequency-buttons"></a>Botões de alta frequência
![Botão Avançar dos guias do Microsoft Dynamics 365](images/GuideNextButton.png "Botão Avançar dos guias do Microsoft Dynamics 365")<br>
*Botões de alta frequência são botões que são usados normalmente em um aplicativo. Um bom exemplo desses são os botões Avançar e voltar nos guias do Microsoft Dynamics 365.*

Botões de alta frequência devem...
* ser maiores e mais fáceis de acionar com o foco com a cabeça
* estar aproximadamente na altura dos olhos para evitar problemas ergonômicos.

### <a name="low-frequency-buttons"></a>Botões de baixa frequência
Botões de baixa frequência são botões que não são regularmente usados no aplicativo. Um bom exemplo é um botão para acessar o menu de configurações ou um botão para limpar toda a tarefa.

* Tente manter esses botões longe dos caminhos de ações frequentes de focar com a cabeça para evitar ativação acidental. 

### <a name="confirmations"></a>Confirmações
![Diálogo de confirmação dos Guias do Microsoft Dynamics 365](images/GuidesConfirmation.png "Diálogo de confirmação dos Guias do Microsoft Dynamics 365")

Quando uma ação tem um impacto significativo, como cobrar dinheiro, excluir uma tarefa ou iniciar um processo longo, é útil confirmar se a pessoa teve a intenção de selecionar o botão. Em interfaces do usuário habilitadas para focar com a cabeça e esperar, há alguns padrões e considerações para diálogos de confirmação:

  * Mostre o realce de seleção no botão principal.
  * Revele o alvo da espera ao mesmo tempo que o realce da seleção.
  * Para o botão secundário, revele o alvo da espera ao focar com a cabeça.
        
### <a name="toggle-buttons"></a>Botões de alternância
Botões de alternância exigem uma lógica sutil para funcionarem corretamente. Quando uma pessoa olha fixo para um botão de alternância e o ativa, ela precisa sair do botão e retornar para reiniciar a lógica de espera. É importante que os botões de alternância tenham estados ativo e inativo claros. 

### <a name="list-views"></a>Modos de exibição de lista
![Diálogo de confirmação dos Guias do Microsoft Dynamics 365](images/GuidesListView.png "Diálogo de confirmação dos Guias do Microsoft Dynamics 365")<br>
*As exibições de lista apresentam um desafio específico para a entrada de olhar e de duração da pesquisa. As pessoas precisam ser capazes de verificar o conteúdo sem se sentir que eles precisam Tiptoe-los em volta dos destinos de pesquisa.*

Algumas dicas para projetar exibições de lista:
* realce toda a linha ao focar com a cabeça, mas não comece a esperar, a menos que o foco com a cabeça esteja fixado no alvo específico.
* somente mostre o alvo quando a linha estiver realçada para reduzir o ruído visual.
* seja claro e consistente com a posição dos alvos.
* não mostre todos os alvos de uma vez para evitar uma interface do usuário repetitiva.
* reutilize um mesmo padrão sempre que possível para estabelecer familiaridade na experiência do usuário.
 
 ## <a name="see-also"></a>Consulte também
* [Manipulação direta com as mãos](direct-manipulation.md)
* [Apontar e confirmar com as mãos](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Comando de voz](voice-design.md)
