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
# <a name="using-xaml-with-holographic-directx-apps"></a><span data-ttu-id="146ff-104">Usando XAML com aplicativos de DirectX holográfico</span><span class="sxs-lookup"><span data-stu-id="146ff-104">Using XAML with holographic DirectX apps</span></span>

<span data-ttu-id="146ff-105">Este tópico explica o impacto da troca entre [2D modos de exibição XAML e imersivos](app-views.md) no seu aplicativo DirectX e como fazer uso eficiente de um modo de exibição XAML e a exibição envolvente.</span><span class="sxs-lookup"><span data-stu-id="146ff-105">This topic explains the impact of switching between [2D XAML views and immersive views](app-views.md) in your DirectX app, and how to make efficient use of both a XAML view and immersive view.</span></span>

## <a name="xaml-view-switching-overview"></a><span data-ttu-id="146ff-106">Visão geral de alternância de exibição XAML</span><span class="sxs-lookup"><span data-stu-id="146ff-106">XAML view switching overview</span></span>

<span data-ttu-id="146ff-107">Em HoloLens, um aplicativo geralmente imersão que posteriormente poderá exibir um modo de exibição XAML 2D deve inicializar esse modo de exibição XAML pela primeira vez e retorne imediatamente para um modo de exibição de imersão a partir daí.</span><span class="sxs-lookup"><span data-stu-id="146ff-107">On HoloLens, a generally immersive app that may later display a 2D XAML view must initialize that XAML view first and immediately switch to an immersive view from there.</span></span> <span data-ttu-id="146ff-108">Isso significa que o XAML será carregado antes de seu aplicativo pode fazer qualquer coisa.</span><span class="sxs-lookup"><span data-stu-id="146ff-108">This means XAML will load before your app can do anything.</span></span> <span data-ttu-id="146ff-109">Como resultado, haverá um pequeno aumento no seu tempo de inicialização, e XAML continuarão a ocupar espaço de memória no processo de seu aplicativo enquanto ele estiver no plano de fundo; a quantidade de memória depende do uso que seu aplicativo faz com XAML antes de alternar para o modo nativo e atraso na inicialização.</span><span class="sxs-lookup"><span data-stu-id="146ff-109">As a result, there will be a small increase in your startup time, and XAML will continue to occupy memory space in your app process while it resides in the background; the amount of startup delay and memory usage depends on what your app does with XAML before switching to the native view.</span></span> <span data-ttu-id="146ff-110">Se você não fizer nada em seu código no início, exceto pelo fato iniciar seu modo de exibição de imersão de inicialização do XAML, o impacto deve ser menor.</span><span class="sxs-lookup"><span data-stu-id="146ff-110">If you do nothing in your XAML start up code at first except start your immersive view, the impact should be minor.</span></span> <span data-ttu-id="146ff-111">Além disso, como sua renderização holográfica é feita diretamente para a exibição imersiva, evitará qualquer restrições relacionadas a XAML em que a renderização.</span><span class="sxs-lookup"><span data-stu-id="146ff-111">Also, because your holographic rendering is done directly to the immersive view, you will avoid any XAML-related restrictions on that rendering.</span></span>

<span data-ttu-id="146ff-112">Observe que o uso de memória contagens de CPU e GPU.</span><span class="sxs-lookup"><span data-stu-id="146ff-112">Note that the memory usage counts for both CPU and GPU.</span></span> <span data-ttu-id="146ff-113">Direct3D 11 é capaz de trocar de memória virtual gráfica, mas ele não poderá trocar alguns ou todos os recursos de GPU XAML e pode haver um impacto perceptível no desempenho.</span><span class="sxs-lookup"><span data-stu-id="146ff-113">Direct3D 11 is able to swap virtual graphics memory, but it might not be able to swap out some or all of the XAML GPU resources, and there might be a noticeable performance hit.</span></span> <span data-ttu-id="146ff-114">De qualquer forma, não ao carregar os recursos XAML, você não precisa deixar mais espaço para seu aplicativo e proporcionar uma melhor experiência.</span><span class="sxs-lookup"><span data-stu-id="146ff-114">Either way, not loading any XAML features you don't need will leave more room for your app and provide a better experience.</span></span>

## <a name="xaml-view-switching-workflow"></a><span data-ttu-id="146ff-115">Fluxo de trabalho de alternância de exibição XAML</span><span class="sxs-lookup"><span data-stu-id="146ff-115">XAML view switching workflow</span></span>

<span data-ttu-id="146ff-116">O fluxo de trabalho para um aplicativo que vai diretamente no XAML para o modo imersivo é da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="146ff-116">The workflow for an app that goes directly from XAML to immersive mode is like so:</span></span>
* <span data-ttu-id="146ff-117">O aplicativo é inicializado no modo de exibição XAML 2D.</span><span class="sxs-lookup"><span data-stu-id="146ff-117">The app starts up in the 2D XAML view.</span></span>
* <span data-ttu-id="146ff-118">Sequência de inicialização do aplicativo XAML detecta se o sistema atual dá suporte à renderização holográfica:</span><span class="sxs-lookup"><span data-stu-id="146ff-118">The app’s XAML startup sequence detects if the current system supports holographic rendering:</span></span>
* <span data-ttu-id="146ff-119">Nesse caso, o aplicativo cria a exibição envolvente e coloca-o para o primeiro plano imediatamente.</span><span class="sxs-lookup"><span data-stu-id="146ff-119">If so, the app creates the immersive view and brings it to the foreground right away.</span></span> <span data-ttu-id="146ff-120">Carregamento de XAML será ignorado para qualquer coisa que não é necessário em dispositivos Windows Mixed Reality, inclusive todos os ativos carregando no modo de exibição XAML e classes de renderização.</span><span class="sxs-lookup"><span data-stu-id="146ff-120">XAML loading is skipped for anything not necessary on Windows Mixed Reality devices, including any rendering classes and asset loading in the XAML view.</span></span> <span data-ttu-id="146ff-121">Se o aplicativo estiver usando o XAML para entrada de teclado, essa página de entrada ainda deve ser criada.</span><span class="sxs-lookup"><span data-stu-id="146ff-121">If the app is using XAML for keyboard input, that input page should still be created.</span></span>
* <span data-ttu-id="146ff-122">Caso contrário, o modo de exibição XAML pode prosseguir com negócios como de costume.</span><span class="sxs-lookup"><span data-stu-id="146ff-122">If not, the XAML view can proceed with business as usual.</span></span>

## <a name="tip-for-rendering-graphics-across-both-views"></a><span data-ttu-id="146ff-123">Dica para o processamento de gráficos em ambos os modos de exibição</span><span class="sxs-lookup"><span data-stu-id="146ff-123">Tip for rendering graphics across both views</span></span>

<span data-ttu-id="146ff-124">Se seu aplicativo precisa implementar alguma quantidade de processamento no DirectX para o modo de exibição XAML no Windows Mixed Reality, sua melhor aposta é criar um processador que pode trabalhar com ambos os modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="146ff-124">If your app needs to implement some amount of rendering in DirectX for the XAML view in Windows Mixed Reality, your best bet is to create one renderer that can work with both views.</span></span> <span data-ttu-id="146ff-125">O renderizador deve ser uma instância que pode ser acessada em ambos os modos de exibição, e ele deve ser capaz de alternar entre a renderização 2D e holographic.</span><span class="sxs-lookup"><span data-stu-id="146ff-125">The renderer should be one instance that can be accessed from both views, and it should be able to switch between 2D and holographic rendering.</span></span> <span data-ttu-id="146ff-126">Dessa forma, os ativos GPU só são carregados uma vez - isso reduz a quantidade de recursos a serem trocados ao alternar os modos de exibição, impacto na memória e tempos de carregamento.</span><span class="sxs-lookup"><span data-stu-id="146ff-126">That way GPU assets are only loaded once - this reduces load times, memory impact, and the amount of resources to be swapped when switching views.</span></span>