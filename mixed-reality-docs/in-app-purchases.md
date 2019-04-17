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
# <a name="in-app-purchases"></a><span data-ttu-id="d9ef3-104">Compras no aplicativo</span><span class="sxs-lookup"><span data-stu-id="d9ef3-104">In-app purchases</span></span>

<span data-ttu-id="d9ef3-105">Compras no aplicativo têm suporte no HoloLens, mas há algum trabalho para configurá-los.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="d9ef3-106">Para aproveitar a compra de aplicativo em funcionalidade, você deve:</span><span class="sxs-lookup"><span data-stu-id="d9ef3-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="d9ef3-107">Criar um XAML [exibição 2D](app-views.md) seja exibido como uma imagem fixa</span><span class="sxs-lookup"><span data-stu-id="d9ef3-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="d9ef3-108">Alternar para ela para ativar o posicionamento, o que deixa o modo de exibição de imersão</span><span class="sxs-lookup"><span data-stu-id="d9ef3-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="d9ef3-109">Chamar a API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="d9ef3-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="d9ef3-110">Essa API abrirá o pop-up do sistema operacional do Windows estoque que mostra o nome de compra no aplicativo, descrição e preço.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="d9ef3-111">O usuário pode escolher as opções de compra.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-111">The user can then choose purchase options.</span></span> <span data-ttu-id="d9ef3-112">Depois que a ação for concluída, o aplicativo precisará apresentar a interface do usuário que permite ao usuário alternar de volta para seu [exibição imersiva](app-views.md).</span><span class="sxs-lookup"><span data-stu-id="d9ef3-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="d9ef3-113">Para aplicativos baseados em desktop Windows Mixed Reality fones imersivos em exposição de direcionamento, ele não é necessário para mudar manualmente para um modo de exibição XAML antes de chamar a API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
