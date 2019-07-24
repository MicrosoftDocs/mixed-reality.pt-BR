---
title: Perda de rastreamento no Unity
description: Tratamento da perda de controle em um aplicativo do Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, perda de controle, imagem de perda de rastreamento
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548749"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="f3f8f-104">Perda de rastreamento no Unity</span><span class="sxs-lookup"><span data-stu-id="f3f8f-104">Tracking loss in Unity</span></span>

<span data-ttu-id="f3f8f-105">Quando o dispositivo não consegue se localizar no mundo, o aplicativo tem "perda de rastreamento".</span><span class="sxs-lookup"><span data-stu-id="f3f8f-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="f3f8f-106">Por padrão, o Unity pausará o loop de atualização e exibirá uma imagem de abertura para o usuário.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="f3f8f-107">Quando o rastreamento é retomado, a imagem de abertura desaparece e o loop de atualização continua.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="f3f8f-108">Como alternativa, o usuário pode lidar com essa transição manualmente, recusando a configuração.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="f3f8f-109">Todo o conteúdo parecerá ficar bloqueado durante a perda de rastreamento se nada for feito para tratá-lo.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="f3f8f-110">Manipulação padrão</span><span class="sxs-lookup"><span data-stu-id="f3f8f-110">Default Handling</span></span>

<span data-ttu-id="f3f8f-111">Por padrão, o loop Update do aplicativo, bem como todas as mensagens e eventos, serão interrompidos durante a perda de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="f3f8f-112">Ao mesmo tempo, uma imagem será exibida para o usuário.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="f3f8f-113">Você pode personalizar essa imagem acessando configurações de > de edição – > Player, clicando em imagem de abertura e definindo a imagem de perda de rastreamento de Holographic.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="f3f8f-114">Manipulação manual</span><span class="sxs-lookup"><span data-stu-id="f3f8f-114">Manual Handling</span></span>

<span data-ttu-id="f3f8f-115">Para lidar manualmente com a perda de controle, você precisa ir para **Editar** > **configurações** >  > do projeto plataforma universal do Windows**imagem**  > deSplashdaguiaConfigurações >  **Windows Holographic** e desmarque "ao rastrear a perda e mostrar imagem".</span><span class="sxs-lookup"><span data-stu-id="f3f8f-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="f3f8f-116">Depois, você precisa lidar com as alterações de controle com as APIs especificadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="f3f8f-117">**Namespace:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="f3f8f-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="f3f8f-118">**Escreva** *Worldmanager*</span><span class="sxs-lookup"><span data-stu-id="f3f8f-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="f3f8f-119">O World Manager expõe um evento para detectar o controle perdido/obtido (*worldmanager. OnPositionalLocatorStateChanged*) e uma propriedade para consultar o estado atual (*worldmanager. State*)</span><span class="sxs-lookup"><span data-stu-id="f3f8f-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="f3f8f-120">Quando o estado de acompanhamento não estiver ativo, a câmera não parecerá traduzir no mundo virtual mesmo que o usuário se traduz.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="f3f8f-121">Isso significa que os objetos não corresponderão mais a qualquer local físico e todos serão exibidos no corpo bloqueado.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="f3f8f-122">Ao lidar com alterações de controle por conta própria, você precisa sondar a propriedade de estado em cada quadro ou manipular o evento *OnPositionalLocatorStateChanged* .</span><span class="sxs-lookup"><span data-stu-id="f3f8f-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="f3f8f-123">Poll</span><span class="sxs-lookup"><span data-stu-id="f3f8f-123">Polling</span></span>

<span data-ttu-id="f3f8f-124">O estado mais importante é *PositionalLocatorState. Active* , o que significa que o controle é totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="f3f8f-125">Qualquer outro Estado resultará em apenas deltas rotacionais para a câmera principal.</span><span class="sxs-lookup"><span data-stu-id="f3f8f-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="f3f8f-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f3f8f-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="f3f8f-127">Manipulando o evento OnPositionalLocatorStateChanged</span><span class="sxs-lookup"><span data-stu-id="f3f8f-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="f3f8f-128">Como alternativa e mais conveniente, você também pode assinar o *OnPositionalLocatorStateChanged* para lidar com as transições:</span><span class="sxs-lookup"><span data-stu-id="f3f8f-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="f3f8f-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3f8f-129">See also</span></span>
* [<span data-ttu-id="f3f8f-130">Lidando com a perda de controle no DirectX</span><span class="sxs-lookup"><span data-stu-id="f3f8f-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)
