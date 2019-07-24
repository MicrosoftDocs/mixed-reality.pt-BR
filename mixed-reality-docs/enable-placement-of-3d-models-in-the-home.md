---
title: Habilitar o posicionamento de modelos 3D na página inicial
description: Como posicionar modelos 3D de seu site ou aplicativo na página inicial do Windows Mixed Reality
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modelo, lugar em casa, lugar, mundo, modelagem, realidade misturada, página inicial, Web, aplicativo
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829728"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="aa519-104">Habilitar o posicionamento de modelos 3D no início da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="aa519-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="aa519-105">Esse recurso foi adicionado como parte da [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md).</span><span class="sxs-lookup"><span data-stu-id="aa519-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="aa519-106">As versões mais antigas do Windows não são compatíveis com esse recurso.</span><span class="sxs-lookup"><span data-stu-id="aa519-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="aa519-107">O [Windows Mixed Reality Home](navigating-the-windows-mixed-reality-home.md) é o ponto de partida onde os usuários vão antes de iniciar os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="aa519-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="aa519-108">Em alguns cenários, os aplicativos 2D (como o aplicativo hologramas) permitem o posicionamento de modelos 3D diretamente na casa mistura de realidade como decorações ou para uma inspeção mais detalhada no 3D completo.</span><span class="sxs-lookup"><span data-stu-id="aa519-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="aa519-109">O *protocolo adicionar modelo* permite que você envie um modelo 3D de seu site ou aplicativo diretamente para a página inicial do Windows Mixed Realm, onde ele persistirá como inicializadores de [aplicativos 3D](3d-app-launcher-design-guidance.md), aplicativos 2D e hologramas.</span><span class="sxs-lookup"><span data-stu-id="aa519-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="aa519-110">Por exemplo, se você estiver desenvolvendo um aplicativo que superfícies um catálogo de mobília 3D para criar um espaço, poderá usar o *protocolo adicionar modelo* para permitir que os usuários coloquem esses modelos de móveis 3D a partir do catálogo.</span><span class="sxs-lookup"><span data-stu-id="aa519-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="aa519-111">Uma vez colocado no mundo, os usuários podem mover, redimensionar e remover esses modelos 3D assim como outros hologramas em casa.</span><span class="sxs-lookup"><span data-stu-id="aa519-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="aa519-112">Este artigo fornece uma visão geral da implementação do *protocolo adicionar modelo* para que você possa começar a permitir que os usuários decorem seu mundo com objetos 3D do seu aplicativo ou da Web.</span><span class="sxs-lookup"><span data-stu-id="aa519-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="aa519-113">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="aa519-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="aa519-114"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="aa519-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="aa519-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="aa519-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="aa519-116"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="aa519-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="aa519-117">Adicionar protocolo de modelo</span><span class="sxs-lookup"><span data-stu-id="aa519-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="aa519-118">✔️</span><span class="sxs-lookup"><span data-stu-id="aa519-118">✔️</span></span></td>
        <td><span data-ttu-id="aa519-119">✔️</span><span class="sxs-lookup"><span data-stu-id="aa519-119">✔️</span></span></td>
    </tr>
</table>

## <a name="overview"></a><span data-ttu-id="aa519-120">Visão geral</span><span class="sxs-lookup"><span data-stu-id="aa519-120">Overview</span></span>

<span data-ttu-id="aa519-121">Há duas etapas para habilitar o posicionamento de modelos 3D na página inicial do Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="aa519-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="aa519-122">[Verifique se seu modelo 3D é compatível com a página inicial do Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="aa519-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="aa519-123">Implemente o *protocolo adicionar modelo* em seu aplicativo ou página da Web (este artigo).</span><span class="sxs-lookup"><span data-stu-id="aa519-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="aa519-124">Implementando o *protocolo adicionar modelo*</span><span class="sxs-lookup"><span data-stu-id="aa519-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="aa519-125">Depois de ter um [modelo 3D compatível](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), você pode implementar o *protocolo adicionar modelo* ativando o seguinte URI de qualquer página da Web ou aplicativo:</span><span class="sxs-lookup"><span data-stu-id="aa519-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="aa519-126">Se o URI apontar para um recurso remoto, ele será baixado automaticamente e colocado em casa.</span><span class="sxs-lookup"><span data-stu-id="aa519-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="aa519-127">Os recursos locais serão copiados para a pasta de dados de aplicativo da página inicial da realidade misturada antes de serem colocados em casa.</span><span class="sxs-lookup"><span data-stu-id="aa519-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="aa519-128">É recomendável projetar sua experiência para considerar cenários em que o usuário pode estar executando uma versão mais antiga do Windows que não dá suporte a esse recurso, ocultando o botão ou desabilitando-o, se possível.</span><span class="sxs-lookup"><span data-stu-id="aa519-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="aa519-129">Invocando o *protocolo adicionar modelo* de um aplicativo plataforma universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="aa519-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="aa519-130">Invocando o *protocolo adicionar modelo* de uma página da Web:</span><span class="sxs-lookup"><span data-stu-id="aa519-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="aa519-131">Considerações sobre headsets de imersão (VR)</span><span class="sxs-lookup"><span data-stu-id="aa519-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="aa519-132">Para headsets de imersão (VR), o portal de realidade misturada não precisa estar em execução antes de invocar o *protocolo adicionar modelo*.</span><span class="sxs-lookup"><span data-stu-id="aa519-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="aa519-133">Nesse caso, o *protocolo adicionar modelo* iniciará o portal de realidade misturada e posicionará o objeto diretamente, no qual o headset está olhando quando você chegar na casa misturada da realidade.</span><span class="sxs-lookup"><span data-stu-id="aa519-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="aa519-134">Ao invocar o *protocolo adicionar modelo* da área de trabalho com o portal da realidade misturada já em execução, verifique se o headset está "ativo".</span><span class="sxs-lookup"><span data-stu-id="aa519-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="aa519-135">Caso contrário, o posicionamento não terá sucesso.</span><span class="sxs-lookup"><span data-stu-id="aa519-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="aa519-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa519-136">See also</span></span>

* [<span data-ttu-id="aa519-137">Criando modelos 3D para uso na página inicial do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="aa519-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="aa519-138">Como navegar na página inicial do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="aa519-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
