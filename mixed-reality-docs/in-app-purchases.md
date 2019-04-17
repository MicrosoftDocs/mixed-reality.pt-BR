---
title: Compras no aplicativo
description: Compras no aplicativo têm suporte em aplicativos de realidade misturada, mas há algum trabalho para configurá-los.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: compras no aplicativo, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590513"
---
# <a name="in-app-purchases"></a>Compras no aplicativo

Compras no aplicativo têm suporte no HoloLens, mas há algum trabalho para configurá-los.

Para aproveitar a compra de aplicativo em funcionalidade, você deve:
* Criar um XAML [exibição 2D](app-views.md) seja exibido como uma imagem fixa
* Alternar para ela para ativar o posicionamento, o que deixa o modo de exibição de imersão
* Chamar a API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Essa API abrirá o pop-up do sistema operacional do Windows estoque que mostra o nome de compra no aplicativo, descrição e preço. O usuário pode escolher as opções de compra. Depois que a ação for concluída, o aplicativo precisará apresentar a interface do usuário que permite ao usuário alternar de volta para seu [exibição imersiva](app-views.md).

Para aplicativos baseados em desktop Windows Mixed Reality fones imersivos em exposição de direcionamento, ele não é necessário para mudar manualmente para um modo de exibição XAML antes de chamar a API RequestProductPurchaseAsync.
