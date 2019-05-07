---
title: Olhar e duração
description: Visão geral do modelo de entrada olhar e duração
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: Misto realidade, olhar, duração, interação, de design
ms.openlocfilehash: a50ae948a351f5152ebb98778da9be8c08090d72
ms.sourcegitcommit: 222cba2d622b47f75949bf8af80d5c62de4dceab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "64914616"
---
# <a name="gaze-and-dwell"></a>Olhar e duração

Quando prático está ocupados com partes e as ferramentas, gestos podem ser entediante ou impossível.  Os comandos de voz, como o gesto, podem ser circunstancialmente não confiáveis, por exemplo, sob condições excessivamente altos.  Além disso, o uso de voz para controlar computadores não é ainda uma interação de base, mas certamente está ganhando steam!  Duração de olhar oferece o mecanismo mais familiar e fácil em mestre para heads-up de trabalho viva-voz em HoloLens.  Além disso, a duração de olhar é 100% confiável independentes de restrições de interferência nem de silêncio de ruído no ambiente operacional.

## <a name="goals"></a>Metas

Fornece um mecanismo para interações assistido completo, sem o uso de voz.

## <a name="design-principles"></a>Princípios de design

1. Olhar não é uma arma
    
    Olhar requer comentários visuais para interação intuitiva, mas muitos comentários podem induzir a ansiedade. Os comentários devem ajudar um usuário sabe o que eles está visando, mas não-seleção automática em relação a sua intenção. Lendo texto requer uma consideração extra para fornecer um espaço de usuário para absorver as informações antes de selecionar.
    
2. Busca de velocidade Cachinhos Dourados
    
    O preenchimento de duração de exibição pode ter temporizadores diferentes com base no impacto do painel de navegação - funções usadas com mais frequência geralmente se beneficiará tempos mais rápidos de preenchimento, enquanto as funções mais CONSEQUENCIAIS podem se beneficiar de tempos de preenchimento. Curvas de animação da cor de preenchimento positivamente podem influenciar uma sensação de tempos mais rápidos de preenchimento. Consideração deve ser tomada para habilitar a decisão de usuário do fast/médio/lento preencher substituições de velocidade.
    
3. Digamos que pseudocódigos para efeito de yo-yo

    O efeito de yo-yo (também conhecido como "noite em the Roxbury") é um padrão de desagradáveis que pode surgir de determinados posicionamento de conteúdo e controles com base em olhar. Por exemplo, uma barra de navegação da lista com o botão de preenchimento na parte inferior induz um loop do - aparência para baixo lidam bem com, examine os resultados, examine a duração, etc. Esse padrão resultante é desconfortável e deve ser evitado, colocando os controles de navegação em um local centralizado que exige menos back bidirecional. Posicionamento dos botões de duração em relação a seus efeitos se torna importante de conforto.

## <a name="ui-patterns"></a>Padrões de interface do usuário

### <a name="high-frequency-buttons"></a>Botões de alta frequência
    
* Botões Avançar/voltar
  * Pré-preenchimento de atraso muito curto (buffer de cintilação popups)
  * Botões maiores são mais fáceis de atingir com olhar
  * BOM para mantê-los na altura de olho para que não haja pressão para interagir
  * Região de duração pode ser maior que o ícone de inativo para torná-lo mais fácil de usar (VERSO)

### <a name="low-frequency-buttons"></a>Botões de baixa frequência
    
* Ativar o menu Configurações
  * Atrasar mais pré-preenchimento okey (buffer de cintilação popups)
  * Tente manter esses botões fora caminhos frequente de cursor

* Confirmações (ou seja, verificação de fluxo, caixas de diálogo)
  * Mostrar Realce de seleção no botão principal
  * Revelar lidam bem com destino ao mesmo tempo que o realce de seleção
  * Use lidam bem com destino ao redor de ícone para manter a interface simples
  * Decisão importante, portanto, não ativa o realce, revela a duração de destino para o tempo de uma reconsideração
        
### <a name="toggle-buttons"></a>Botões de alternância

* Pin
  * Estado visual clara ativo/inativo
  * Preenchimento radial ajuda o usuário de foco e fornece o andamento natural 

* Configurações individuais
  * Estados claro ativo/inativo
  * Lidam bem com destinos todos no ícone adjacente à esquerda
  * Duração tem como alvo apenas aparecem quando a seleção de realçar ativo
  * "Lidam bem com controle deslizante" no lado direito, para ativar/desativar configurações

### <a name="list-views"></a>Modos de exibição de lista

* Exibição de lista de navegação - guia arquivos para abrir
  * Destaques do cursor de linha de qualquer lugar na linha, mas não começa a duração
  * Quando a linha é realçada pelo cursor, o destino de duração é exibida à esquerda
  * Lidam bem com o destino sempre um círculo no lado esquerdo do texto em todos os modos de exibição de lista
  * Não mostrar que todos os destinos de uma vez para evitar repetitiva da interface do usuário de duração da pesquisa
  * Use novamente o mesmo padrão para estabelecer a familiaridade da experiência do usuário
        
* Exibição de lista - hierarquia de tarefas/etapas em um guia de navegação
  * Lidam bem com o destino sempre um círculo no lado esquerdo do texto
  * Expandir/recolher lidam bem com funcionalidade
        
* Exibição de lista de navegação - Selecione modo
  * Siga os padrões estabelecidos acima

### <a name="contextual-buttons"></a>Botões contextuais

* Mostrar/ocultar 3D - mostra-se em 3D ao longo de corda quase hologramas 
  * Estado visual clara ativo/inativo

### <a name="pivots"></a>Tabelas dinâmicas

* Lista de guias recentes/All
  * Preencher a funcionalidade da interface do usuário que permanece para indicar qual guia está ativo
  * Para tabelas dinâmicas de única palavra curta, podemos optou por antecipar o padrão de duração de destino
  * Podemos favorecida a interface simplificada em relação a outro destinos de círculo 2 e uma interface do usuário mais ampla
  * Em nosso caso, as palavras são curtas o suficiente para que um atraso fornece suficiente conforto antes de preenchimento


## <a name="ux-guidelines-and-best-practices"></a>Práticas recomendadas e diretrizes de experiência do usuário

### <a name="target-sizes"></a>Tamanhos do alvo

  * Tamanho mínimo do PIN ícone: 6cm no espaço de mundo no Unity, 30 MRUs (30cm @ 2m)
  * Ficam em todos os destinos "magnetizados" ou "adesivo"? (ou seja, olhares suavização de cursor)

### <a name="animation"></a>Animação

  * Atraso antes de duração visual dispara .5sec
  * Duração de duração visual 1,2 s
  * Curva na animação?

### <a name="visual-feedback"></a>Feedback visual

  * Preenchimento radial do local de início do cursor olhar
  * Preenchimento sempre radial do centro do botão. Uma resposta consistente é menos confusa que todas as direções diferentes nos botões diferentes. 
    * Essa regra pode ser interrompida para interações direcionais (por exemplo, etc. para cima/baixo/esquerda/direita, nav.). Por exemplo, faz uma exceção em Avançar/voltar sendo deixado com guias com o botão direito preenchimentos.
    * Considere a possibilidade de inversão de preenchimento radial de fora (se a alternância desativada). A inversa sensação de apertar um botão é um bom padrão visual para manter. 

### <a name="progressive-disclosure"></a>Divulgação progressiva

 * Divulgação progressiva significa que o destino de duração é revelado no realce (por exemplo, em um controle de lista)
 * Destaques da barra de texto com o spotlight revelam em olhar em qualquer lugar no texto
 * Destino de preenchimento de olhar sempre aparece à esquerda, mas apenas para o item de lista que é realçado
 * Evite ter todos os destinos de duração de todo o tempo devido a aparência repetitiva de círculos empilhadas
 
 ## <a name="see-also"></a>Consulte também
* [Manipulação direta](direct-manipulation.md)
* [Ponto e confirmar](point-and-commit.md)
* [Conceitos básicos de interação](interaction-fundamentals.md)
* [Olhar head e confirmar](gaze-and-commit.md)
* [Olhar e voz](voice-design.md)
