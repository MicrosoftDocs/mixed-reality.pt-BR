---
title: Usando XAML com aplicativos Holographic DirectX
description: Explica o impacto de alternar entre exibições do XAML 2D e exibições de imersão em seu aplicativo DirectX e como fazer uso eficiente de uma exibição XAML e de imersão.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: realidade mista do Windows, UWP, gerenciamento de exibição de aplicativo, XAML, teclado, passo a passos, DirectX
ms.openlocfilehash: 4136e674cfc1737dba9dcc1f70bd68edd4e95a41
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277954"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Usando XAML com aplicativos Holographic DirectX

Este tópico explica o impacto de alternar entre [exibições do XAML 2D e exibições de imersão](app-views.md) em seu aplicativo DirectX e como fazer uso eficiente de uma exibição XAML e exibição imersiva.

## <a name="xaml-view-switching-overview"></a>Visão geral de alternância de exibição XAML

No HoloLens, um aplicativo geralmente envolvente que pode exibir posteriormente uma exibição XAML 2D deve inicializar essa exibição XAML primeiro e imediatamente alternar para uma exibição de imersão a partir daí. Isso significa que o XAML será carregado antes que seu aplicativo possa fazer qualquer coisa. Como resultado, haverá um pequeno aumento no tempo de inicialização, e o XAML continuará ocupando espaço de memória no processo do aplicativo enquanto ele reside em segundo plano; a quantidade de atraso de inicialização e uso de memória depende do que seu aplicativo faz com XAML antes de alternar para a exibição nativa. Se você não fizer nada em seu código de inicialização de XAML a princípio, exceto iniciar a exibição de imersão, o impacto deverá ser menor. Além disso, como a renderização Holographic é feita diretamente na exibição imersiva, você evitará restrições relacionadas a XAML nessa renderização.

Observe que o uso de memória conta tanto para CPU quanto para GPU. O Direct3D 11 é capaz de trocar a memória gráfica virtual, mas pode não ser capaz de trocar alguns ou todos os recursos de GPU XAML, e pode haver um impacto perceptível no desempenho. De qualquer forma, não carregar nenhum recurso XAML de que você não precisa deixará mais espaço para seu aplicativo e fornecerá uma experiência melhor.

## <a name="xaml-view-switching-workflow"></a>Fluxo de trabalho de alternância de exibição XAML

O fluxo de trabalho para um aplicativo que vai diretamente do XAML para o modo de imersão é assim:
* O aplicativo é iniciado na exibição 2D XAML.
* A sequência de inicialização XAML do aplicativo detecta se o sistema atual dá suporte à renderização Holographic:
* Em caso afirmativo, o aplicativo cria a exibição imersiva e a coloca em primeiro plano imediatamente. O carregamento XAML é ignorado por qualquer coisa não necessária em dispositivos Windows Mixed Reality, incluindo quaisquer classes de renderização e carregamento de ativos na exibição XAML. Se o aplicativo estiver usando XAML para entrada de teclado, essa página de entrada ainda deverá ser criada.
* Caso contrário, o modo de exibição XAML pode prosseguir com os negócios como de costume.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Dica para renderizar elementos gráficos em ambas as exibições

Se seu aplicativo precisar implementar alguma quantidade de renderização no DirectX para o modo de exibição XAML no Windows Mixed Reality, sua melhor aposta é criar um renderizador que possa funcionar com ambos os modos de exibição. O renderizador deve ser uma instância que possa ser acessada de ambos os modos de exibição e deve ser capaz de alternar entre a renderização 2D e Holographic. Dessa forma, os ativos de GPU são carregados apenas uma vez – isso reduz os tempos de carregamento, o impacto de memória e a quantidade de recursos a serem trocados ao alternar as exibições.
