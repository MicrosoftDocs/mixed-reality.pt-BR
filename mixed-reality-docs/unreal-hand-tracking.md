---
title: Rastreamento manual em não real
description: Explica como usar o rastreamento manual em não real
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, acompanhamento à mão
ms.openlocfilehash: 3f7f4dd1eb62cb707eaaf8632a2ba3c280a4ac31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835337"
---
# <a name="hand-tracking"></a><span data-ttu-id="dad43-104">Acompanhamento à mão</span><span class="sxs-lookup"><span data-stu-id="dad43-104">Hand Tracking</span></span>

<span data-ttu-id="dad43-105">O sistema de acompanhamento manual usa Palms e dedos de uma pessoa como entrada para inreal.</span><span class="sxs-lookup"><span data-stu-id="dad43-105">The hand tracking system uses a person’s palms and fingers as input to Unreal.</span></span> <span data-ttu-id="dad43-106">Um desenvolvedor pode obter a posição e a rotação de cada dedo, toda a palma e gestos de mão para usar em seu próprio código.</span><span class="sxs-lookup"><span data-stu-id="dad43-106">A developer can get every finger’s position and rotation, the entire palm, and even hand gestures to use in their own code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="dad43-107">Pose de mão</span><span class="sxs-lookup"><span data-stu-id="dad43-107">Hand Pose</span></span>

<span data-ttu-id="dad43-108">Usando a pose de mão, os desenvolvedores podem controlar as mãos e os dedos do usuário ativo como entrada.</span><span class="sxs-lookup"><span data-stu-id="dad43-108">Using the hand pose, developers can track the hands and fingers of the active user as input.</span></span> <span data-ttu-id="dad43-109">Esse sistema é exposto por meio dos planos gráficos e do C++.</span><span class="sxs-lookup"><span data-stu-id="dad43-109">This system is exposed through both Blueprints and C++.</span></span> <span data-ttu-id="dad43-110">Os detalhes técnicos estão na classe WinRT correspondente [Windows. percepção. People. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) essa API inreal fornece os dados no formato de sistema de coordenadas e tiques inreais que são sincronizados com o mecanismo inreal.</span><span class="sxs-lookup"><span data-stu-id="dad43-110">Technical details are in the corresponding WinRT class [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) This Unreal API provides the data in the format of Unreal’s coordinate system and ticks are synchronised with the Unreal Engine.</span></span>

### <a name="enum"></a><span data-ttu-id="dad43-111">Enum</span><span class="sxs-lookup"><span data-stu-id="dad43-111">Enum</span></span>

<span data-ttu-id="dad43-112">EWMRHandKeypoint descreve a hierarquia do Bone da mão.</span><span class="sxs-lookup"><span data-stu-id="dad43-112">EWMRHandKeypoint describes the Hand’s bone hierarchy.</span></span> 

<span data-ttu-id="dad43-113">Gráfico</span><span class="sxs-lookup"><span data-stu-id="dad43-113">Blueprint:</span></span>

![Mão keypoint BP](images/unreal/hand-keypoint-bp.png)
 
<span data-ttu-id="dad43-115">C++:</span><span class="sxs-lookup"><span data-stu-id="dad43-115">C++:</span></span>
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

![Esqueleto da mão](images/hand-skeleton.png)

<span data-ttu-id="dad43-117">Os valores numéricos podem ser encontrados na tabela [Windows. percepção. People. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span><span class="sxs-lookup"><span data-stu-id="dad43-117">The numerical values can be found in the table [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span></span>
 
### <a name="functions"></a><span data-ttu-id="dad43-118">Funções</span><span class="sxs-lookup"><span data-stu-id="dad43-118">Functions</span></span>

<span data-ttu-id="dad43-119">Para usar funções de acompanhamento de mão em plantas, abra "acompanhamento à mão/realidade mista do Windows"</span><span class="sxs-lookup"><span data-stu-id="dad43-119">To use hand tracking functions in Blueprints, open "Hand Tracking/Windows Mixed Reality"</span></span>

![Controle à mão BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="dad43-121">Para funções do C++, inclua "WindowsMixedRealityHandTrackingFunctionLibrary. h"</span><span class="sxs-lookup"><span data-stu-id="dad43-121">For C++ functions, include "WindowsMixedRealityHandTrackingFunctionLibrary.h"</span></span>

<span data-ttu-id="dad43-122">BP</span><span class="sxs-lookup"><span data-stu-id="dad43-122">BP:</span></span>

![Dá suporte ao controle à mão BP](images/unreal/supports-hand-tracking-bp.png)
 
<span data-ttu-id="dad43-124">C++:</span><span class="sxs-lookup"><span data-stu-id="dad43-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

<span data-ttu-id="dad43-125">Retorna true se o acompanhamento de mão tiver suporte no dispositivo; false se o acompanhamento de mão não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="dad43-125">Returns true if hand tracking is supported on the device, false if hand tracking is not available.</span></span>

<span data-ttu-id="dad43-126">BP</span><span class="sxs-lookup"><span data-stu-id="dad43-126">BP:</span></span>

![Obter transformação conjunta de entrega](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="dad43-128">C++:</span><span class="sxs-lookup"><span data-stu-id="dad43-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="dad43-129">Essa função retorna dados espaciais da mão.</span><span class="sxs-lookup"><span data-stu-id="dad43-129">This function returns spatial data of the hand.</span></span> <span data-ttu-id="dad43-130">Os dados são atualizados a cada quadro, dentro de um quadro, os valores retornados são armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="dad43-130">The data updates every frame, inside a frame the returned values are cached.</span></span> <span data-ttu-id="dad43-131">Não é recomendável ter muita lógica nessa função por motivos de desempenho.</span><span class="sxs-lookup"><span data-stu-id="dad43-131">It is not recommended to have heavy logic on this function for performance reasons.</span></span> 

* <span data-ttu-id="dad43-132">**Mão** – à mão do usuário, pode ser esquerda ou direita</span><span class="sxs-lookup"><span data-stu-id="dad43-132">**Hand** – hand of the user, may be left or right</span></span>
* <span data-ttu-id="dad43-133">**Ponto de extremidade** – o Bone da mão.</span><span class="sxs-lookup"><span data-stu-id="dad43-133">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="dad43-134">**Transformação** – coordenadas e orientação da base do Bone.</span><span class="sxs-lookup"><span data-stu-id="dad43-134">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="dad43-135">Para obter os dados de transformação para o final de um Bone, a base do próximo Bone deve ser solicitada.</span><span class="sxs-lookup"><span data-stu-id="dad43-135">To get the transform data for the end of a bone, the base of the next bone should be requested.</span></span> <span data-ttu-id="dad43-136">Um Bone de dica especial dá ao fim do distal.</span><span class="sxs-lookup"><span data-stu-id="dad43-136">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="dad43-137">**RADIUS** — raio da base do Bone.</span><span class="sxs-lookup"><span data-stu-id="dad43-137">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="dad43-138">**Valor de retorno** — true se o Bone for rastreado neste quadro, false se o Bone não for acompanhado.</span><span class="sxs-lookup"><span data-stu-id="dad43-138">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="dad43-139">Animação do link ao vivo à mão</span><span class="sxs-lookup"><span data-stu-id="dad43-139">Hand Live Link Animation</span></span>
<span data-ttu-id="dad43-140">As poses de mão são expostas à animação usando o plug-in de vínculo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="dad43-140">Hand poses are exposed to Animation using the Live Link plugin.</span></span> <span data-ttu-id="dad43-141">A documentação do plug-in está [aqui](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span><span class="sxs-lookup"><span data-stu-id="dad43-141">The plugin documentation is [here](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span></span>

<span data-ttu-id="dad43-142">Se a realidade mista do Windows e os plug-ins do Live link estiverem habilitados, vá para a **janela > link ao vivo** para abrir a janela do editor de link dinâmico.</span><span class="sxs-lookup"><span data-stu-id="dad43-142">If the Windows Mixed Reality and Live Link plugins are enabled, go to **Window > Live Link** to open the Live Link editor window.</span></span> <span data-ttu-id="dad43-143">Clique no **botão + fonte** e habilite a fonte de acompanhamento do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="dad43-143">Click the **+ Source button** and enable Windows Mixed Reality Hand Tracking Source</span></span>

![Origem do link dinâmico](images/unreal/live-link-source.png)
 
<span data-ttu-id="dad43-145">Depois de habilitar a origem e abrir qualquer ativo de animação, a guia Visualizar cena da animação terá as seguintes opções adicionais (os detalhes estão na documentação de link dinâmico do inreal-como o plug-in está na versão beta, o processo pode ser alterado posteriormente)</span><span class="sxs-lookup"><span data-stu-id="dad43-145">After you enable the source and open any animation asset, the Preview Scene tab of Animation will have the following additional options (the details are in Unreal’s Live Link documentation- as the plugin is in beta, the process may change later)</span></span>

![Animação de link ao vivo](images/unreal/live-link-animation.png)
 
<span data-ttu-id="dad43-147">A hierarquia de animação da mão é a mesma do EWMRHandKeypoint.</span><span class="sxs-lookup"><span data-stu-id="dad43-147">The hand animation hierarchy is the same as in EWMRHandKeypoint.</span></span> <span data-ttu-id="dad43-148">A animação pode ser redirecionada usando WindowsMixedRealityHandTrackingLiveLinkRemapAsset.</span><span class="sxs-lookup"><span data-stu-id="dad43-148">Animation can be retargeted using WindowsMixedRealityHandTrackingLiveLinkRemapAsset.</span></span> 

![Animação de link ao vivo 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="dad43-150">Pode ser uma subclasse no editor</span><span class="sxs-lookup"><span data-stu-id="dad43-150">It can be subclassed in the editor</span></span>

![Remapeamento de link dinâmico](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a><span data-ttu-id="dad43-152">Malha à mão</span><span class="sxs-lookup"><span data-stu-id="dad43-152">Hand Mesh</span></span>
<span data-ttu-id="dad43-153">Malha que representa as mãos do usuário.</span><span class="sxs-lookup"><span data-stu-id="dad43-153">Mesh representing the user hands.</span></span> 

![Malha à mão](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a><span data-ttu-id="dad43-155">Como habilitar e configurar</span><span class="sxs-lookup"><span data-stu-id="dad43-155">How to enable and configure</span></span>

<span data-ttu-id="dad43-156">Os desenvolvedores podem obter acesso direto a malhas à mão para suas próprias finalidades.</span><span class="sxs-lookup"><span data-stu-id="dad43-156">Developers can get direct access to hand meshes for their own purposes.</span></span> <span data-ttu-id="dad43-157">Esse acesso deve ser habilitado em ARSessionConfig: configurações de AR-> World Mapping-> gerar dados de malha da geometria rastreada.</span><span class="sxs-lookup"><span data-stu-id="dad43-157">This access must be enabled in ARSessionConfig: AR Settings -> World Mapping -> Generate Mesh Data from Tracked Geometry.</span></span> 

<span data-ttu-id="dad43-158">Estes são os parâmetros padrão para malhas:</span><span class="sxs-lookup"><span data-stu-id="dad43-158">Here are the default parameters for meshes:</span></span>

1.  <span data-ttu-id="dad43-159">Usar dados de malha para oclusão</span><span class="sxs-lookup"><span data-stu-id="dad43-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="dad43-160">Gerar colisão para dados de malha</span><span class="sxs-lookup"><span data-stu-id="dad43-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="dad43-161">Gerar malha NAV para dados de malha</span><span class="sxs-lookup"><span data-stu-id="dad43-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="dad43-162">Renderizar dados de malha em wireframe – parâmetro de depuração que mostra a malha gerada</span><span class="sxs-lookup"><span data-stu-id="dad43-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="dad43-163">Para projetos de realidade misturada, esses valores de parâmetro serão usados como os padrões de malha de mapeamento espacial e malha de mão.</span><span class="sxs-lookup"><span data-stu-id="dad43-163">For mixed reality projects, these parameter values will be used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="dad43-164">Os desenvolvedores podem alterá-los em BP ou em código para qualquer malha específica.</span><span class="sxs-lookup"><span data-stu-id="dad43-164">Developers can change them in BP or code for any particular mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="dad43-165">Referência da API do C++</span><span class="sxs-lookup"><span data-stu-id="dad43-165">C++ API Reference</span></span> 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

<span data-ttu-id="dad43-166">Esse valor é a malha de mão entre todos os objetos rastreáveis.</span><span class="sxs-lookup"><span data-stu-id="dad43-166">This value is the hand mesh among all trackable objects.</span></span>

```cpp
class FARSupportInterface 
{
public:
// other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="dad43-167">Esses delegados são chamados quando o sistema detecta qualquer objeto rastreável, incluindo uma malha à mão.</span><span class="sxs-lookup"><span data-stu-id="dad43-167">These delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
<span data-ttu-id="dad43-168">Os manipuladores para os delegados devem ter a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="dad43-168">Handlers to the delegates should have the following signature:</span></span>
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

<span data-ttu-id="dad43-169">Os dados de malha podem ser acessados pelo`UARTrackedGeometry::GetUnderlyingMesh`</span><span class="sxs-lookup"><span data-stu-id="dad43-169">Mesh data can be accessed by `UARTrackedGeometry::GetUnderlyingMesh`</span></span>

### <a name="blueprint-api-reference"></a><span data-ttu-id="dad43-170">Referência de API de Blueprint</span><span class="sxs-lookup"><span data-stu-id="dad43-170">Blueprint API Reference</span></span>

<span data-ttu-id="dad43-171">Os desenvolvedores devem adicionar um componente de notificação rastreável do AR a um ator do Blueprint</span><span class="sxs-lookup"><span data-stu-id="dad43-171">Developers should add an AR Trackable Notify Component to a Blueprint actor</span></span>

![ARTrackable notificar](images/unreal/ar-trackable-notify.png)
 
<span data-ttu-id="dad43-173">Em seguida, vá para os detalhes do componente</span><span class="sxs-lookup"><span data-stu-id="dad43-173">Then go to the component’s details</span></span> 

![Notificação ARTrackable 2](images/unreal/ar-trackable-notify2.png)
 
<span data-ttu-id="dad43-175">E substituir em Adicionar/atualizar/remover geometria rastreada com código como o mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="dad43-175">And overwrite On Add/Update/Remove Tracked Geometry with code like the below:</span></span>

![Na notificação do ARTrackable](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="dad43-177">Raios de mão</span><span class="sxs-lookup"><span data-stu-id="dad43-177">Hand Rays</span></span>

<span data-ttu-id="dad43-178">Os desenvolvedores podem usar um raio de alcance como um dispositivo apontador.</span><span class="sxs-lookup"><span data-stu-id="dad43-178">Developers can use a hand ray as a pointing device.</span></span> <span data-ttu-id="dad43-179">O sistema está disponível em C++ e Blueprint.</span><span class="sxs-lookup"><span data-stu-id="dad43-179">The system is available in C++ and Blueprint.</span></span> <span data-ttu-id="dad43-180">Tecnicamente, ele expõe [Windows. UI. Input. Spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span><span class="sxs-lookup"><span data-stu-id="dad43-180">Technically it exposes [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span></span>

<span data-ttu-id="dad43-181">É importante mencionar que, como os resultados de todas as funções são alterados em todos os quadros, todos eles se tornaram chamáveis.</span><span class="sxs-lookup"><span data-stu-id="dad43-181">It’s important to mention that since the results of all the functions changes every frame, they are all made callable.</span></span> <span data-ttu-id="dad43-182">Para obter mais informações sobre funções puras ou que podem ser chamadas, [Confira](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span><span class="sxs-lookup"><span data-stu-id="dad43-182">For more information about pure vs impure or callable functions, see [that](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="dad43-183">Para o Blueprint, abra "Windows Mixed Reality HMD"</span><span class="sxs-lookup"><span data-stu-id="dad43-183">For Blueprint open “Windows Mixed Reality HMD”</span></span>

![Raios-mão BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="dad43-185">Para C++, inclua "WindowsMixedRealityFunctionLibrary. h"</span><span class="sxs-lookup"><span data-stu-id="dad43-185">For C++ include "WindowsMixedRealityFunctionLibrary.h"</span></span>

### <a name="enum"></a><span data-ttu-id="dad43-186">Enum</span><span class="sxs-lookup"><span data-stu-id="dad43-186">Enum</span></span>

![Botões do controlador de entrada](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* <span data-ttu-id="dad43-188">**Select** -– disparado pelo usuário selecionar evento, que pode ser disparado no HoloLens 2 por airtap ou olhar e Commit.</span><span class="sxs-lookup"><span data-stu-id="dad43-188">**Select** -– User triggered Select event, which can be triggered in HoloLens 2 by airtap or gaze and commit.</span></span> <span data-ttu-id="dad43-189">Outra maneira de disparar esse evento é dizer "Select".</span><span class="sxs-lookup"><span data-stu-id="dad43-189">Another way to trigger this event is to say “Select”.</span></span> 
* <span data-ttu-id="dad43-190">**Segure** -– evento de Segure acionado pelo usuário, que é disparado no HoloLens 2 fechando os dedos do usuário em um holograma.</span><span class="sxs-lookup"><span data-stu-id="dad43-190">**Grasp** -– User triggered Grasp event, which is triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* <span data-ttu-id="dad43-191">Não **rastreado** – a mão não está visível</span><span class="sxs-lookup"><span data-stu-id="dad43-191">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="dad43-192">**Acompanhado** – a mão é totalmente controlada</span><span class="sxs-lookup"><span data-stu-id="dad43-192">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="dad43-193">Struct</span><span class="sxs-lookup"><span data-stu-id="dad43-193">Struct</span></span>

![Ponteiro de pose de informações BP](images/unreal/pointer-pose-info-bp.png)
```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```
* <span data-ttu-id="dad43-195">**Origem** – origem da mão</span><span class="sxs-lookup"><span data-stu-id="dad43-195">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="dad43-196">**Direção** – direção da mão</span><span class="sxs-lookup"><span data-stu-id="dad43-196">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="dad43-197">**Up** – vetor de cima à mão</span><span class="sxs-lookup"><span data-stu-id="dad43-197">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="dad43-198">**Orientação** – o quaternion de orientação</span><span class="sxs-lookup"><span data-stu-id="dad43-198">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="dad43-199">**Status de rastreamento** – status de acompanhamento atual</span><span class="sxs-lookup"><span data-stu-id="dad43-199">**Tracking Status** – current tracking status</span></span>

### <a name="functions"></a><span data-ttu-id="dad43-200">Funções</span><span class="sxs-lookup"><span data-stu-id="dad43-200">Functions</span></span>

<span data-ttu-id="dad43-201">Todas as funções devem ser chamáveis em todos os quadros para monitoramento contínuo.</span><span class="sxs-lookup"><span data-stu-id="dad43-201">All the functions should be callable on every frame for continuous monitoring.</span></span> 

![Obter informações de pose de ponteiro](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
<span data-ttu-id="dad43-203">A função retorna as informações completas sobre a direção de raio da mão neste quadro.</span><span class="sxs-lookup"><span data-stu-id="dad43-203">The function returns the full information about the hand ray direction in this frame.</span></span> 

![BP é compreendida](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
<span data-ttu-id="dad43-205">Retornará true se a mão estiver segurando neste quadro.</span><span class="sxs-lookup"><span data-stu-id="dad43-205">Returns true if the hand is grasped in this frame.</span></span> 

![É selecione BP pressionado](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
<span data-ttu-id="dad43-207">Retornará true se o usuário disparasse Select neste quadro.</span><span class="sxs-lookup"><span data-stu-id="dad43-207">Returns true if the user triggered Select in this frame.</span></span>

![É um botão clicado em BP](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
<span data-ttu-id="dad43-209">Retornará true se o evento/botão for disparado neste quadro.</span><span class="sxs-lookup"><span data-stu-id="dad43-209">Returns true if the event/button is triggered in this frame.</span></span>

![Obter o status de controle do controlador BP](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
<span data-ttu-id="dad43-211">Retorna o status de acompanhamento neste quadro.</span><span class="sxs-lookup"><span data-stu-id="dad43-211">Returns the tracking status in this frame.</span></span>

## <a name="gestures"></a><span data-ttu-id="dad43-212">Gestos</span><span class="sxs-lookup"><span data-stu-id="dad43-212">Gestures</span></span>

<span data-ttu-id="dad43-213">O Hololens 2 pode acompanhar gestos espaciais.</span><span class="sxs-lookup"><span data-stu-id="dad43-213">The Hololens 2 can track spatial gestures.</span></span> <span data-ttu-id="dad43-214">Os detalhes sobre esses gestos são [aqui](https://docs.microsoft.com/hololens/hololens2-basic-usage) que um desenvolvedor pode capturá-los como entrada para seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="dad43-214">Details about these gestures are [here](https://docs.microsoft.com/hololens/hololens2-basic-usage) A developer can capture them as input to their mixed reality application.</span></span> 

<span data-ttu-id="dad43-215">A função C++ está em "WindowsMixedRealitySpatialInputFunctionLibrary. h"</span><span class="sxs-lookup"><span data-stu-id="dad43-215">The C++ function is in "WindowsMixedRealitySpatialInputFunctionLibrary.h"</span></span>

<span data-ttu-id="dad43-216">A função Blueprint está na entrada espacial de realidade misturada do Windows</span><span class="sxs-lookup"><span data-stu-id="dad43-216">The Blueprint function is in Windows Mixed Reality Spatial Input</span></span>

![Gestos de captura](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="dad43-218">Enum</span><span class="sxs-lookup"><span data-stu-id="dad43-218">Enum</span></span>

![Tipo de gesto](images/unreal/gesture-type.png)
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```
<span data-ttu-id="dad43-220">Essa enumeração descreve gestos de eixo espacial.</span><span class="sxs-lookup"><span data-stu-id="dad43-220">This enum describes spatial axis gestures.</span></span> <span data-ttu-id="dad43-221">Você pode ler sobre eles [aqui](holograms-211.md)</span><span class="sxs-lookup"><span data-stu-id="dad43-221">You can read about them [here](holograms-211.md)</span></span>

### <a name="function"></a><span data-ttu-id="dad43-222">Função</span><span class="sxs-lookup"><span data-stu-id="dad43-222">Function</span></span>

![Gestos de captura BP](images/unreal/capture-gestures-bp.png)
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```
<span data-ttu-id="dad43-224">A função habilita e desabilita a captura de gestos.</span><span class="sxs-lookup"><span data-stu-id="dad43-224">The function enables and disables capturing of gestures.</span></span> <span data-ttu-id="dad43-225">Os gestos habilitados acionam eventos de entrada.</span><span class="sxs-lookup"><span data-stu-id="dad43-225">The enabled gestures fire input events.</span></span> <span data-ttu-id="dad43-226">Retornará true se a ativação da captura do gesto for bem-sucedida e false se houver um erro.</span><span class="sxs-lookup"><span data-stu-id="dad43-226">It returns true if enabling gesture capture succeeded and false if there's an error.</span></span>
<span data-ttu-id="dad43-227">Principais eventos</span><span class="sxs-lookup"><span data-stu-id="dad43-227">Key Events</span></span>

![Principais eventos](images/unreal/key-events.png)

![Principais eventos 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```
<span data-ttu-id="dad43-230">Se o gesto estiver habilitado, os eventos começarão a ser acionados.</span><span class="sxs-lookup"><span data-stu-id="dad43-230">If the gesture is enabled, the events begin firing.</span></span> 

