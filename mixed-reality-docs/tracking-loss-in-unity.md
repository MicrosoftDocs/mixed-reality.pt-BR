---
title: Controlando a perda no Unity
description: Tratamento de perda de dentro de um aplicativo do Unity de acompanhamento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, controlando a perda, a imagem de perda de controle
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590491"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="6d7e2-104">Controlando a perda no Unity</span><span class="sxs-lookup"><span data-stu-id="6d7e2-104">Tracking loss in Unity</span></span>

<span data-ttu-id="6d7e2-105">Quando o dispositivo não pode localizar-se no mundo, o aplicativo passa por "perda de controle".</span><span class="sxs-lookup"><span data-stu-id="6d7e2-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="6d7e2-106">Por padrão, o Unity pausar o loop de atualização e exibir uma imagem de abertura para o usuário.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="6d7e2-107">Quando o rastreamento é recuperado, a imagem inicial desaparece e continua o loop de atualização.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="6d7e2-108">Como alternativa, o usuário pode manipular manualmente essa transição ao recusar a configuração.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="6d7e2-109">Todo o conteúdo parecerá tornam-se o corpo bloqueado durante a perda de controle se nada é feito para manipulá-lo.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="6d7e2-110">O tratamento padrão</span><span class="sxs-lookup"><span data-stu-id="6d7e2-110">Default Handling</span></span>

<span data-ttu-id="6d7e2-111">Por padrão, o loop de atualização do aplicativo, bem como todos os eventos e mensagens será interrompido para a duração da perda de controle.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="6d7e2-112">Ao mesmo tempo, uma imagem será exibida ao usuário.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="6d7e2-113">Você pode personalizar essa imagem ao ir até Editar -> Configurações -> Player, clicando em imagem inicial e definir a imagem holográfica perda de controle.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="6d7e2-114">Manipulação manual</span><span class="sxs-lookup"><span data-stu-id="6d7e2-114">Manual Handling</span></span>

<span data-ttu-id="6d7e2-115">Para lidar manualmente com a perda de controle, você precisará ir para **edite** > **configurações do projeto** > **Player**  >   **Guia de configurações de plataforma Windows universal** > **imagem inicial** > **Windows Holographic** e desmarque a opção "no controle perda pausa e Mostrar imagem ".</span><span class="sxs-lookup"><span data-stu-id="6d7e2-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="6d7e2-116">Depois disso, você precisa lidar com o controle de alterações com as APIs especificadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="6d7e2-117">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="6d7e2-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="6d7e2-118">**Tipo:** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="6d7e2-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="6d7e2-119">Gerenciador de mundo expõe um evento para detectar obtidas/perdidas acompanhamento (*WorldManager.OnPositionalLocatorStateChanged*) e uma propriedade para consultar o estado atual (*WorldManager.state*)</span><span class="sxs-lookup"><span data-stu-id="6d7e2-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="6d7e2-120">Quando o estado de controle não está ativo, a câmera não aparecerá converter no mundo virtual, até mesmo quando o usuário converte.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="6d7e2-121">Isso significa que os objetos não corresponderá ao qualquer local físico e todos aparecerão corpo bloqueado.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="6d7e2-122">Ao lidar com o controle de alterações em seus próprios, você precisará sondar a propriedade state cada quadro ou identificador a *OnPositionalLocatorStateChanged* eventos.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="6d7e2-123">sondagem</span><span class="sxs-lookup"><span data-stu-id="6d7e2-123">Polling</span></span>

<span data-ttu-id="6d7e2-124">É o estado mais importante *PositionalLocatorState.Active* que significa que o acompanhamento está totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="6d7e2-125">Qualquer outro estado resulta em apenas rotacional deltas para a câmera principal.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="6d7e2-126">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="6d7e2-126">For example:</span></span>

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="6d7e2-127">Manipulando o evento OnPositionalLocatorStateChanged</span><span class="sxs-lookup"><span data-stu-id="6d7e2-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="6d7e2-128">Como alternativa e mais conveniente, você também pode assinar *OnPositionalLocatorStateChanged* para lidar com as transições:</span><span class="sxs-lookup"><span data-stu-id="6d7e2-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6d7e2-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d7e2-129">See also</span></span>
* [<span data-ttu-id="6d7e2-130">Tratamento de perda de acompanhamento no DirectX</span><span class="sxs-lookup"><span data-stu-id="6d7e2-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)
