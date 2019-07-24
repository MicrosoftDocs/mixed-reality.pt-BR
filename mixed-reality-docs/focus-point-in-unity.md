---
title: Ponto de foco no Unity
description: Ajuste manual da estabilidade do holograma no Unity definindo o ponto de foco
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, ponto de foco, plano de foco, plano de estabilização, ponto de estabilização, Reprojeção, LSR, buffer de profundidade
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525464"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="e1fe5-104">Ponto de foco no Unity</span><span class="sxs-lookup"><span data-stu-id="e1fe5-104">Focus point in Unity</span></span>

<span data-ttu-id="e1fe5-105">**Namespace:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="e1fe5-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="e1fe5-106">**Tipo**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="e1fe5-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="e1fe5-107">O [ponto de foco](hologram-stability.md#stabilization-plane) pode ser definido para fornecer uma dica sobre como executar melhor a estabilização nos hologramas que estão sendo exibidos no momento.</span><span class="sxs-lookup"><span data-stu-id="e1fe5-107">The [focus point](hologram-stability.md#stabilization-plane) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="e1fe5-108">Se você quiser definir o ponto de foco no Unity, ele precisará ser definido a cada quadro usando *HolographicSettings. SetFocusPointForFrame ()* .</span><span class="sxs-lookup"><span data-stu-id="e1fe5-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="e1fe5-109">Se o ponto de foco não estiver definido para um quadro, o plano de estabilização padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="e1fe5-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="e1fe5-110">Por padrão, novos projetos do Unity têm a opção "Habilitar compartilhamento de buffer de profundidade" definida.</span><span class="sxs-lookup"><span data-stu-id="e1fe5-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="e1fe5-111">Com essa opção, um aplicativo do Unity em execução em um headset de área de trabalho imersiva ou um HoloLens executando a atualização de abril de 2018 do Windows (RS4) ou posterior enviará seu buffer de profundidade para o Windows para otimizar a estabilidade do holograma automaticamente, sem que seu aplicativo especifique um ponto de foco:</span><span class="sxs-lookup"><span data-stu-id="e1fe5-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="e1fe5-112">Em um headset de área de trabalho imersiva, isso habilitará a Reprojeção baseada em profundidade por pixel.</span><span class="sxs-lookup"><span data-stu-id="e1fe5-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="e1fe5-113">Em um HoloLens executando a atualização de abril de 2018 do Windows 10 ou posterior, isso analisará o buffer de profundidade para escolher um plano de estabilização ideal automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e1fe5-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="e1fe5-114">Qualquer uma das abordagens deve fornecer uma qualidade de imagem ainda melhor sem trabalho explícito por seu aplicativo para selecionar um ponto de foco em cada quadro.</span><span class="sxs-lookup"><span data-stu-id="e1fe5-114">Either approach should provide even better image quality without explicit work by your app to select a focus point each frame.</span></span>  <span data-ttu-id="e1fe5-115">Observe que, se você fornecer um ponto de foco manualmente, isso substituirá o comportamento automático descrito acima e geralmente reduzirá a estabilidade do holograma.</span><span class="sxs-lookup"><span data-stu-id="e1fe5-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="e1fe5-116">Em geral, você deve especificar apenas um ponto de foco manual quando seu aplicativo estiver em execução em um HoloLens que ainda não foi atualizado para a atualização do Windows 10 de abril de 2018.</span><span class="sxs-lookup"><span data-stu-id="e1fe5-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="e1fe5-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1fe5-117">Example</span></span>

<span data-ttu-id="e1fe5-118">Há várias maneiras de definir o ponto de foco, conforme sugerido pelas sobrecargas disponíveis na função estática *SetFocusPointForFrame* .</span><span class="sxs-lookup"><span data-stu-id="e1fe5-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="e1fe5-119">Veja abaixo um exemplo simples para definir o plano de foco para o objeto fornecido em cada quadro:</span><span class="sxs-lookup"><span data-stu-id="e1fe5-119">Presented below is a simple example to set the focus plane to the provided object each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

<span data-ttu-id="e1fe5-120">Observe que o código simples acima pode acabar reduzindo a estabilidade do holograma se o objeto focalizado terminar por trás do usuário.</span><span class="sxs-lookup"><span data-stu-id="e1fe5-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="e1fe5-121">É por isso que você geralmente deve definir "habilitar o compartilhamento de buffer de profundidade" em vez de especificar manualmente um ponto de foco.</span><span class="sxs-lookup"><span data-stu-id="e1fe5-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="e1fe5-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1fe5-122">See also</span></span>
* [<span data-ttu-id="e1fe5-123">Plano de estabilização</span><span class="sxs-lookup"><span data-stu-id="e1fe5-123">Stabilization plane</span></span>](hologram-stability.md#stabilization-plane)
