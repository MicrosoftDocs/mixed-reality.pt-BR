---
title: Tipos de aplicativos de realidade misturada
description: Uma das vantagens de desenvolver aplicativos para a realidade mista do Windows é que há um espectro de experiências que a plataforma pode dar suporte a partir de ambientes virtuais de imersão total, a fim de obter informações sobre o ambiente atual de um usuário.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, padrões de aplicativo
ms.openlocfilehash: 62a0b76ba7853262a46b34466a6d3b0567bc137d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438265"
---
# <a name="types-of-mixed-reality-apps"></a>Tipos de aplicativos de realidade misturada

Uma das vantagens de desenvolver aplicativos para o Windows Mixed Reality é que há um espectro de experiências com as quais a plataforma é compatível. Desde ambientes virtuais de imersão completa até disposição em camadas de informações leves sobre o ambiente atual de um usuário, o Windows Mixed Reality fornece um conjunto robusto de ferramentas para dar vida a qualquer experiência. É importante que um criador de aplicativos entenda no início do processo de desenvolvimento para onde está a sua experiência em todo o espectro. Essa decisão, por fim, afetará a composição de design de aplicativo e o caminho tecnológico para o desenvolvimento.

## <a name="enhanced-environment-apps-hololens-only"></a>Aplicativos de ambiente avançado (somente HoloLens)

Uma das maneiras mais eficientes de que a realidade mista pode trazer valor aos usuários é facilitar o posicionamento de informações digitais ou conteúdo no ambiente atual de um usuário. Este é um aplicativo de ambiente avançado. Essa abordagem é popular para aplicativos em que o posicionamento contextual do conteúdo digital no mundo real é fundamental e/ou manter o ambiente real do usuário "presente" durante sua experiência é fundamental. Essa abordagem também permite que os usuários migrem facilmente de tarefas do mundo real para tarefas digitais e voltem facilmente, rescredencendo ainda mais a promessa de que os aplicativos de realidade misturados que o usuário vê são realmente uma parte de seu ambiente.

![aplicativos de ambiente avançado](images/enhancedenvironmentapps-640px.jpg)<br>
*Aplicativos de ambiente aprimorados*

**Exemplo usa**
* Um aplicativo de estilo de realidade misturada do bloco de notas que permite aos usuários criar e posicionar anotações em todo o ambiente
* Um aplicativo de televisão de realidade misturada colocou em um ponto confortável para a exibição
* Um aplicativo de inculinária de realidade mista colocado acima da ilha de cozinha para ajudar em uma tarefa de culinária
* Um aplicativo de realidade misturada que dá aos usuários a sensação de "x-ray Vision" (ou seja, um holograma colocado sobre e imita um objeto do mundo real, ao mesmo tempo que permite que o usuário veja "dentro dele" holographically)
* Anotações de realidade misturadas colocadas em toda a fábrica para fornecer as informações necessárias do trabalhador
* Realidade misturada wayfinding em um espaço do Office
* Experiências de mesa de realidade misturada (ou seja, experiências de estilo de jogo de tabuleiro)
* Aplicativos de comunicação de realidade misturada como Skype

## <a name="blended-environment-apps"></a>Aplicativos de ambiente combinado

Dada a capacidade do Windows Mixed Reality de reconhecer e mapear o ambiente do usuário, ele é capaz de criar uma camada digital que pode ser completamente sobreposta no espaço do usuário. A camada fina respeita a forma e os limites do ambiente do usuário, mas o aplicativo pode optar por transformar determinados elementos mais adequados para aprofundar o usuário no aplicativo. Isso é chamado de aplicativo de ambiente combinado. Ao contrário de um aplicativo de ambiente avançado, os aplicativos de ambiente combinado só podem se preocupar suficientes com o ambiente para melhor usar sua composição para incentivar o comportamento específico do usuário (como encorajar movimento ou exploração) ou substituir elementos por alterações (uma cozinha o contador é virtualmente imcapado para mostrar um padrão de bloco diferente). Esse tipo de experiência pode até mesmo transformar um elemento em um objeto totalmente diferente, mas ainda manter as dimensões aproximadas do objeto como sua base (uma ilha de cozinha é transformada em um dumpster para um jogo thriller de crime).

![aplicativos de ambiente misturados](images/blendedenvironmentapps-640px.jpg)<br>
*Aplicativos de ambiente combinado*

**Exemplo usa**
* Um aplicativo de design interior de realidade misturada que pode pintar paredes, semitops ou andares em cores e padrões diferentes
* Um aplicativo de realidade misturada que permite que um designer automotivo crie uma camada de novas iterações de design para uma atualização próxima do carro sobre um carro existente
* Uma camada é "coberta" e substituída por uma realidade misturada que se destaca no jogo dos filhos
* Uma mesa é "coberta" e substituída por um dumpster de realidade misturada em um jogo de thriller de crime
* Uma lanterna de deslocamento é "coberta" e substituída por poste usando aproximadamente a mesma forma e dimensão
* Um aplicativo que permite aos usuários entrar brechas em suas paredes mundiais reais ou de imersão, que revela um mundo mágico

## <a name="immersive-environment-apps"></a>Aplicativos de ambiente de imersão

Aplicativos de ambiente de imersão são centralizados em um ambiente que altera completamente o mundo do usuário e pode colocá-los em um horário e espaço diferentes. Esses ambientes podem se sentir muito reais, criando experiências de imersão e emocionante que são limitadas apenas pela imaginação do criador do aplicativo. Ao contrário dos aplicativos de ambiente misturados, uma vez que o Windows Mixed Reality identifica o espaço do usuário, um aplicativo de ambiente de imersão pode desconsiderar totalmente o ambiente atual do usuário e substituir todo o estoque por um de seus próprios. Essas experiências também podem ter um tempo e espaço completamente separados, o que significa que um usuário pode percorrer as ruas de Roma em uma experiência de imersão, enquanto ainda resta relativamente ao espaço real do mundo. O contexto do ambiente do mundo real pode não ser importante para um aplicativo de ambiente de imersão.

![aplicativos de ambiente de imersão](images/windows-mixed-reality-640px.jpg)<br>
*Aplicativos de ambiente de imersão*

**Exemplo usa**
* Um aplicativo de imersão que permite a um usuário acompanhar um espaço completamente separado de seus próprios (ou seja, percorrer uma famosa construção, Museu, cidade popular)
* Um aplicativo de imersão que orquestra um evento ou cenário em todo o usuário (ou seja, uma batalha ou um desempenho)

## <a name="see-also"></a>Consulte também
* [Visão geral do desenvolvimento](development.md)
* [Modelo de aplicativo](app-model.md)
* [Modos de exibição do aplicativo](app-views.md)
