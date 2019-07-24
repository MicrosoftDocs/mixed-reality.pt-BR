---
title: Compras no aplicativo
description: As compras no aplicativo têm suporte em aplicativos de realidade misturada, mas há algum trabalho para configurá-las.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: compras no aplicativo, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515297"
---
# <a name="in-app-purchases"></a><span data-ttu-id="a09e7-104">Compras no aplicativo</span><span class="sxs-lookup"><span data-stu-id="a09e7-104">In-app purchases</span></span>

<span data-ttu-id="a09e7-105">As compras no aplicativo têm suporte no HoloLens, mas há algum trabalho para configurá-las.</span><span class="sxs-lookup"><span data-stu-id="a09e7-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="a09e7-106">Para aproveitar a funcionalidade de compra de aplicativo, você deve:</span><span class="sxs-lookup"><span data-stu-id="a09e7-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="a09e7-107">Criar uma [exibição XAML 2D](app-views.md) para aparecer como um Slate</span><span class="sxs-lookup"><span data-stu-id="a09e7-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="a09e7-108">Alterne para a ti para ativar o posicionamento, o que deixa a exibição imersiva</span><span class="sxs-lookup"><span data-stu-id="a09e7-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="a09e7-109">Chame a API: Await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="a09e7-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="a09e7-110">Essa API abrirá o pop-up do sistema operacional Windows de estoque que mostra o nome, a descrição e o preço da compra no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a09e7-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="a09e7-111">Em seguida, o usuário pode escolher opções de compra.</span><span class="sxs-lookup"><span data-stu-id="a09e7-111">The user can then choose purchase options.</span></span> <span data-ttu-id="a09e7-112">Depois que a ação for concluída, o aplicativo precisará apresentar a interface do usuário, o que permitirá que ele volte para sua [exibição de imersão](app-views.md).</span><span class="sxs-lookup"><span data-stu-id="a09e7-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="a09e7-113">Para aplicativos destinados a headsets de imersão de realidade mista do Windows com base na área de trabalho, não é necessário alternar manualmente para uma exibição XAML antes de chamar a API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="a09e7-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
