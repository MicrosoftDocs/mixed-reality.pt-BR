---
title: Ativar a colocação de modelos 3D em casa
description: Como colocar os modelos 3D do seu site ou aplicativo em que o Windows Mixed Reality inicial
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modelo, local na página inicial, local, mundo, modelagem, realidade misturada doméstica, web, aplicativo
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829728"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="893c4-104">Ativar a colocação de modelos 3D na realidade misturada inicial</span><span class="sxs-lookup"><span data-stu-id="893c4-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="893c4-105">Esse recurso foi adicionado como parte do [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md).</span><span class="sxs-lookup"><span data-stu-id="893c4-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="893c4-106">Versões mais antigas do Windows não são compatíveis com esse recurso.</span><span class="sxs-lookup"><span data-stu-id="893c4-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="893c4-107">O [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) é o ponto de partida em que os usuários cheguem antes de iniciar aplicativos.</span><span class="sxs-lookup"><span data-stu-id="893c4-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="893c4-108">Em alguns cenários, aplicativos 2D (como o aplicativo de hologramas) ativar a colocação de modelos 3D diretamente para a página inicial de realidade misturada como decorações ou para uma inspeção detalhada em 3D completo.</span><span class="sxs-lookup"><span data-stu-id="893c4-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="893c4-109">O *Adicionar modelo de protocolo* permite que você envie um modelo 3D de seu site ou aplicativo diretamente para o Windows Mixed Reality doméstica, onde ele será mantido como [iniciadores de aplicativo 3D](3d-app-launcher-design-guidance.md), aplicativos 2D e hologramas.</span><span class="sxs-lookup"><span data-stu-id="893c4-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="893c4-110">Por exemplo, se você estiver desenvolvendo um aplicativo que exiba um catálogo de 3D mobília para a criação de um espaço, você pode usar o *Adicionar modelo protocolo* para permitir que os usuários a colocar esses modelos 3D Mobília do catálogo.</span><span class="sxs-lookup"><span data-stu-id="893c4-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="893c4-111">Uma vez colocado no mundo, os usuários podem mover, redimensionar e remover esses modelos 3D, assim como outros hologramas em casa.</span><span class="sxs-lookup"><span data-stu-id="893c4-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="893c4-112">Este artigo fornece uma visão geral da implementação de *Adicionar modelo protocolo* para que você possa começar permitindo que os usuários decorar seu mundo com objetos 3D do seu aplicativo ou da web.</span><span class="sxs-lookup"><span data-stu-id="893c4-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="893c4-113">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="893c4-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="893c4-114"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="893c4-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="893c4-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="893c4-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="893c4-116"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="893c4-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="893c4-117">Adicionar modelo de protocolo</span><span class="sxs-lookup"><span data-stu-id="893c4-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="893c4-118">✔️</span><span class="sxs-lookup"><span data-stu-id="893c4-118">✔️</span></span></td>
        <td><span data-ttu-id="893c4-119">✔️</span><span class="sxs-lookup"><span data-stu-id="893c4-119">✔️</span></span></td>
    </tr>
</table>

## <a name="overview"></a><span data-ttu-id="893c4-120">Visão geral</span><span class="sxs-lookup"><span data-stu-id="893c4-120">Overview</span></span>

<span data-ttu-id="893c4-121">Há 2 etapas para habilitar o posicionamento dos modelos 3D no Windows Mixed Reality inicial:</span><span class="sxs-lookup"><span data-stu-id="893c4-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="893c4-122">[Verifique se seu modelo 3D é compatível com o Windows Mixed Reality doméstica](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="893c4-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="893c4-123">Implemente a *Adicionar modelo protocolo* em seu aplicativo ou página da Web (Este artigo).</span><span class="sxs-lookup"><span data-stu-id="893c4-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="893c4-124">Implementando o *Adicionar modelo de protocolo*</span><span class="sxs-lookup"><span data-stu-id="893c4-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="893c4-125">Uma vez que um [modelo 3D compatível](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), você pode implementar o *Adicionar modelo protocolo* ativando o seguinte URI de qualquer página da Web ou aplicativo:</span><span class="sxs-lookup"><span data-stu-id="893c4-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="893c4-126">Se o URI aponta para um recurso remoto, em seguida, ele será automaticamente ser baixado e colocado em casa.</span><span class="sxs-lookup"><span data-stu-id="893c4-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="893c4-127">Recursos locais serão copiados para a pasta de dados a realidade misturada página inicial aplicativo antes de ser colocada em casa.</span><span class="sxs-lookup"><span data-stu-id="893c4-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="893c4-128">É recomendável Projetando sua experiência de conta para cenários em que o usuário pode estar executando uma versão anterior do Windows que não oferecem suporte a esse recurso, ocultar o botão ou desabilitá-lo se possível.</span><span class="sxs-lookup"><span data-stu-id="893c4-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="893c4-129">Invocar o *Adicionar modelo protocolo* de um aplicativo da plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="893c4-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="893c4-130">Invocar o *Adicionar modelo protocolo* em uma página da Web:</span><span class="sxs-lookup"><span data-stu-id="893c4-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="893c4-131">Considerações para fones imersivos em exposição (VR)</span><span class="sxs-lookup"><span data-stu-id="893c4-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="893c4-132">Para um fones imersivos em exposição de (VR), o Portal de realidade mista não precisa estar em execução antes de invocar o *Adicionar modelo protocolo*.</span><span class="sxs-lookup"><span data-stu-id="893c4-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="893c4-133">Nesse caso, o *Adicionar modelo protocolo* irá iniciar o Portal de realidade mista e colocar o objeto diretamente em que o fone de ouvido é parecido quando você chegar na realidade misturada inicial.</span><span class="sxs-lookup"><span data-stu-id="893c4-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="893c4-134">Ao invocar o *Adicionar modelo protocolo* da área de trabalho com o Portal de realidade misturada já em execução, certifique-se de que o fone de ouvido está "ativo".</span><span class="sxs-lookup"><span data-stu-id="893c4-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="893c4-135">Caso contrário, o posicionamento não terá êxito.</span><span class="sxs-lookup"><span data-stu-id="893c4-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="893c4-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="893c4-136">See also</span></span>

* [<span data-ttu-id="893c4-137">Criar modelos 3D para uso no ambiente doméstico Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="893c4-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="893c4-138">Como navegar na página inicial do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="893c4-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
