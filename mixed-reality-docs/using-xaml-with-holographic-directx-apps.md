---
title: Usando XAML com aplicativos de DirectX holográfico
description: Explica o impacto de alternar entre modos de exibição XAML 2D e imersivos no seu aplicativo DirectX e como fazer uso eficiente de um modo de exibição XAML e a exibição envolvente.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: aplicativo de realidade misturada, UWP, Windows exibir gerenciamento, xaml, teclado, passo a passo, DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589309"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Usando XAML com aplicativos de DirectX holográfico

Este tópico explica o impacto da troca entre [2D modos de exibição XAML e imersivos](app-views.md) no seu aplicativo DirectX e como fazer uso eficiente de um modo de exibição XAML e a exibição envolvente.

## <a name="xaml-view-switching-overview"></a>Visão geral de alternância de exibição XAML

Em HoloLens, um aplicativo geralmente imersão que posteriormente poderá exibir um modo de exibição XAML 2D deve inicializar esse modo de exibição XAML pela primeira vez e retorne imediatamente para um modo de exibição de imersão a partir daí. Isso significa que o XAML será carregado antes de seu aplicativo pode fazer qualquer coisa. Como resultado, haverá um pequeno aumento no seu tempo de inicialização, e XAML continuarão a ocupar espaço de memória no processo de seu aplicativo enquanto ele estiver no plano de fundo; a quantidade de memória depende do uso que seu aplicativo faz com XAML antes de alternar para o modo nativo e atraso na inicialização. Se você não fizer nada em seu código no início, exceto pelo fato iniciar seu modo de exibição de imersão de inicialização do XAML, o impacto deve ser menor. Além disso, como sua renderização holográfica é feita diretamente para a exibição imersiva, evitará qualquer restrições relacionadas a XAML em que a renderização.

Observe que o uso de memória contagens de CPU e GPU. Direct3D 11 é capaz de trocar de memória virtual gráfica, mas ele não poderá trocar alguns ou todos os recursos de GPU XAML e pode haver um impacto perceptível no desempenho. De qualquer forma, não ao carregar os recursos XAML, você não precisa deixar mais espaço para seu aplicativo e proporcionar uma melhor experiência.

## <a name="xaml-view-switching-workflow"></a>Fluxo de trabalho de alternância de exibição XAML

O fluxo de trabalho para um aplicativo que vai diretamente no XAML para o modo imersivo é da seguinte forma:
* O aplicativo é inicializado no modo de exibição XAML 2D.
* Sequência de inicialização do aplicativo XAML detecta se o sistema atual dá suporte à renderização holográfica:
* Nesse caso, o aplicativo cria a exibição envolvente e coloca-o para o primeiro plano imediatamente. Carregamento de XAML será ignorado para qualquer coisa que não é necessário em dispositivos Windows Mixed Reality, inclusive todos os ativos carregando no modo de exibição XAML e classes de renderização. Se o aplicativo estiver usando o XAML para entrada de teclado, essa página de entrada ainda deve ser criada.
* Caso contrário, o modo de exibição XAML pode prosseguir com negócios como de costume.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Dica para o processamento de gráficos em ambos os modos de exibição

Se seu aplicativo precisa implementar alguma quantidade de processamento no DirectX para o modo de exibição XAML no Windows Mixed Reality, sua melhor aposta é criar um processador que pode trabalhar com ambos os modos de exibição. O renderizador deve ser uma instância que pode ser acessada em ambos os modos de exibição, e ele deve ser capaz de alternar entre a renderização 2D e holographic. Dessa forma, os ativos GPU só são carregados uma vez - isso reduz a quantidade de recursos a serem trocados ao alternar os modos de exibição, impacto na memória e tempos de carregamento.
