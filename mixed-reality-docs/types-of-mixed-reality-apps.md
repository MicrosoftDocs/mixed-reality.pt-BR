---
title: Tipos de aplicativos de realidade misturada
description: Uma das vantagens do desenvolvimento de aplicativos para Windows Mixed Reality é que há uma variedade de experiências que a plataforma pode oferecer suporte de ambientes completamente imersivos, virtuais, a disposição em camadas de informações claras sobre environmentl atual de um usuário.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, padrões de aplicativo
ms.openlocfilehash: 97f8039dcd9bbf8ee3d6c7be926db16b60a76b97
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589313"
---
# <a name="types-of-mixed-reality-apps"></a>Tipos de aplicativos de realidade misturada

Uma das vantagens do desenvolvimento de aplicativos para Windows Mixed Reality é que há uma variedade de experiências que a plataforma pode dar suporte. Em ambientes completamente imersivos, virtuais, a luz informações disposição em camadas em um ambiente do usuário atual, realidade mista do Windows fornece um conjunto robusto de ferramentas para dar vida a qualquer experiência. É importante que um criador de aplicativos compreender seu processo de desenvolvimento sobre onde essa espectro de sua experiência está no início. Essa decisão, por fim, terá impacto sobre a composição de design do aplicativo e o caminho tecnológico para o desenvolvimento.

## <a name="enhanced-environment-apps-hololens-only"></a>Ambiente avançado de aplicativos (HoloLens)

Uma das maneiras mais eficazes que realidade misturada pode agregar valor aos usuários é, facilitando a colocação de informações digitais ou conteúdo em um ambiente do usuário atual. Isso é um ambiente avançado de aplicativo. Essa abordagem é popular para aplicativos em que o posicionamento contextual de conteúdo digital no mundo real é fundamental e/ou manter o ambiente do usuário reais "present" durante a sua experiência é a chave. Essa abordagem também permite aos usuários mover de tarefas do mundo real para tarefas digitais facilmente e de volta com facilidade, ainda mais credibilidade Promise que os aplicativos de realidade misturada, que o usuário vê realmente fazem parte do seu ambiente de empréstimo.

![Ambiente avançado de aplicativos](images/enhancedenvironmentapps-640px.jpg)<br>
*Ambiente avançado de aplicativos*

**Exemplos de uso**
* Um aplicativo de estilo de bloco de notas de realidade mista que permite aos usuários criar e colocar anotações em torno de seu ambiente
* Um aplicativo de realidade misturada televisão colocado em um ponto à vontade para exibição
* Uma realidade misturada cozinhar o aplicativo é colocado acima da ilha de cozinha para ajudá-lo em uma tarefa de culinária
* Um aplicativo de realidade mista que dá aos usuários a sensação de "visão de raios-x" (ou seja, um holograma colocados na parte superior do e simula um objeto do mundo real, permitindo que o usuário veja holográfica "dentro dele")
* Anotações de realidade misturada colocadas em toda uma fábrica para fornecer as informações necessárias do trabalhador
* Realidade misturada wayfinding em um espaço do office
* Experiências de mesa de realidade misturada (ou seja, o estilo de jogo de tabuleiro experiências)
* Aplicativos de comunicação de realidade misturada como Skype

## <a name="blended-environment-apps"></a>Aplicativos do ambiente combinada

Recebe a capacidade de realidade mista Windows para reconhecer e mapear o ambiente do usuário, é capaz de criar uma camada digital que pode ser sobreposta completamente no espaço do usuário. Camada fina respeita a forma e dos limites de ambiente do usuário, mas o aplicativo pode optar por transformar determinados elementos mais indicados para envolvê-o usuário no aplicativo. Isso é chamado de um aplicativo de ambiente combinada. Ao contrário de um ambiente avançado de aplicativo, aplicativos do ambiente combinada podem apenas cuidado suficiente sobre o ambiente para melhor usar sua composição para incentivando comportamento do usuário específico (como movimentação ou exploração incentivando) ou pela substituição de elementos com alterações (uma cozinha contador é praticamente transparente para mostrar um padrão lado a lado diferentes). Esse tipo de experiência pode até mesmo transformar um elemento em um objeto totalmente diferente, mas ainda manter as dimensões aproximadas do objeto como sua base (uma ilha cozinha é transformada em um dumpster para um jogo de suspense crime).

![Aplicativos do ambiente combinada](images/blendedenvironmentapps-640px.jpg)<br>
*Aplicativos do ambiente combinada*

**Exemplos de uso**
* Um aplicativo de design do interior de realidade mista que pode pintar paredes, Granito ou andares em diferentes cores e padrões
* Um aplicativo de realidade mista que permite que um designer automotivo novas iterações de design camada para uma atualização futura do carro na parte superior de um carro existente
* Um ambiente é "coberto" e substituído por uma espera de frutas de realidade misturada em jogo para crianças
* Um suporte técnico é "coberto" e substituído por uma realidade misturada dumpster em um jogo de suspense crime
* Uma lanterna deslocado "coberta" e substituída por sinais indicadores usando aproximadamente a mesma forma e dimensão
* Um aplicativo que permite aos usuários buracos de explosão em seus paredes do mundo real ou imersivo, que revelar um mundo mágico

## <a name="immersive-environment-apps"></a>Aplicativos envolventes de ambiente

Aplicativos envolventes de ambiente são centralizados em torno de um ambiente que muda completamente o mundo do usuário e colocá-los em um momento diferente e espaço. Esses ambientes podem se sentir muito reais, criar experiências envolventes e emocionante que são limitadas apenas pela imaginação do criador do aplicativo. Ao contrário de aplicativos do ambiente combinada, depois que o Windows Mixed Reality identifica o espaço do usuário, um aplicativo de ambiente imersivo pode totalmente desconsiderar o ambiente do usuário atual e substitua-estoque inteira com um dos seus próprios. Essas experiências completamente também podem separar tempo e espaço, o que significa que um usuário poderia percorrer ruas de Roma em uma experiência imersiva, enquanto permanecem relativamente ainda em seu espaço de mundo real. Contexto do ambiente do mundo real não pode ser importante para um aplicativo de imersão do ambiente.

![Aplicativos envolventes de ambiente](images/windows-mixed-reality-640px.jpg)<br>
*Aplicativos envolventes de ambiente*

**Exemplos de uso**
* Um aplicativo de imersão que permite ao usuário fazer um tour um espaço completamente separado de suas próprias (ou seja, percorrer uma construção famosa, Museu, cidade popular)
* Um aplicativo de imersão que orquestra a um evento ou um cenário de usuário (ou seja, uma batalha ou um desempenho)

## <a name="see-also"></a>Consulte também
* [Visão geral de desenvolvimento](development-overview.md)
* [Modelo de aplicativo](app-model.md)
* [Modos de exibição do aplicativo](app-views.md)
