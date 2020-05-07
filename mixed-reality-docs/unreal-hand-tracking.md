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
# <a name="hand-tracking"></a>Acompanhamento à mão

O sistema de acompanhamento manual usa Palms e dedos de uma pessoa como entrada para inreal. Um desenvolvedor pode obter a posição e a rotação de cada dedo, toda a palma e gestos de mão para usar em seu próprio código. 

## <a name="hand-pose"></a>Pose de mão

Usando a pose de mão, os desenvolvedores podem controlar as mãos e os dedos do usuário ativo como entrada. Esse sistema é exposto por meio dos planos gráficos e do C++. Os detalhes técnicos estão na classe WinRT correspondente [Windows. percepção. People. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) essa API inreal fornece os dados no formato de sistema de coordenadas e tiques inreais que são sincronizados com o mecanismo inreal.

### <a name="enum"></a>Enum

EWMRHandKeypoint descreve a hierarquia do Bone da mão. 

Gráfico

![Mão keypoint BP](images/unreal/hand-keypoint-bp.png)
 
C++:
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

Os valores numéricos podem ser encontrados na tabela [Windows. percepção. People. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)
 
### <a name="functions"></a>Funções

Para usar funções de acompanhamento de mão em plantas, abra "acompanhamento à mão/realidade mista do Windows"

![Controle à mão BP](images/unreal/hand-tracking-bp.png)

Para funções do C++, inclua "WindowsMixedRealityHandTrackingFunctionLibrary. h"

BP

![Dá suporte ao controle à mão BP](images/unreal/supports-hand-tracking-bp.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

Retorna true se o acompanhamento de mão tiver suporte no dispositivo; false se o acompanhamento de mão não estiver disponível.

BP

![Obter transformação conjunta de entrega](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Essa função retorna dados espaciais da mão. Os dados são atualizados a cada quadro, dentro de um quadro, os valores retornados são armazenados em cache. Não é recomendável ter muita lógica nessa função por motivos de desempenho. 

* **Mão** – à mão do usuário, pode ser esquerda ou direita
* **Ponto de extremidade** – o Bone da mão. 
* **Transformação** – coordenadas e orientação da base do Bone. Para obter os dados de transformação para o final de um Bone, a base do próximo Bone deve ser solicitada. Um Bone de dica especial dá ao fim do distal. 
* **RADIUS** — raio da base do Bone.
* **Valor de retorno** — true se o Bone for rastreado neste quadro, false se o Bone não for acompanhado.

## <a name="hand-live-link-animation"></a>Animação do link ao vivo à mão
As poses de mão são expostas à animação usando o plug-in de vínculo dinâmico. A documentação do plug-in está [aqui](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)

Se a realidade mista do Windows e os plug-ins do Live link estiverem habilitados, vá para a **janela > link ao vivo** para abrir a janela do editor de link dinâmico. Clique no **botão + fonte** e habilite a fonte de acompanhamento do Windows Mixed Reality

![Origem do link dinâmico](images/unreal/live-link-source.png)
 
Depois de habilitar a origem e abrir qualquer ativo de animação, a guia Visualizar cena da animação terá as seguintes opções adicionais (os detalhes estão na documentação de link dinâmico do inreal-como o plug-in está na versão beta, o processo pode ser alterado posteriormente)

![Animação de link ao vivo](images/unreal/live-link-animation.png)
 
A hierarquia de animação da mão é a mesma do EWMRHandKeypoint. A animação pode ser redirecionada usando WindowsMixedRealityHandTrackingLiveLinkRemapAsset. 

![Animação de link ao vivo 2](images/unreal/live-link-animation2.png)
 
Pode ser uma subclasse no editor

![Remapeamento de link dinâmico](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a>Malha à mão
Malha que representa as mãos do usuário. 

![Malha à mão](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a>Como habilitar e configurar

Os desenvolvedores podem obter acesso direto a malhas à mão para suas próprias finalidades. Esse acesso deve ser habilitado em ARSessionConfig: configurações de AR-> World Mapping-> gerar dados de malha da geometria rastreada. 

Estes são os parâmetros padrão para malhas:

1.  Usar dados de malha para oclusão
2.  Gerar colisão para dados de malha
3.  Gerar malha NAV para dados de malha
4.  Renderizar dados de malha em wireframe – parâmetro de depuração que mostra a malha gerada

Para projetos de realidade misturada, esses valores de parâmetro serão usados como os padrões de malha de mapeamento espacial e malha de mão. Os desenvolvedores podem alterá-los em BP ou em código para qualquer malha específica.

### <a name="c-api-reference"></a>Referência da API do C++ 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

Esse valor é a malha de mão entre todos os objetos rastreáveis.

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

Esses delegados são chamados quando o sistema detecta qualquer objeto rastreável, incluindo uma malha à mão. 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
Os manipuladores para os delegados devem ter a seguinte assinatura:
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

Os dados de malha podem ser acessados pelo`UARTrackedGeometry::GetUnderlyingMesh`

### <a name="blueprint-api-reference"></a>Referência de API de Blueprint

Os desenvolvedores devem adicionar um componente de notificação rastreável do AR a um ator do Blueprint

![ARTrackable notificar](images/unreal/ar-trackable-notify.png)
 
Em seguida, vá para os detalhes do componente 

![Notificação ARTrackable 2](images/unreal/ar-trackable-notify2.png)
 
E substituir em Adicionar/atualizar/remover geometria rastreada com código como o mostrado abaixo:

![Na notificação do ARTrackable](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>Raios de mão

Os desenvolvedores podem usar um raio de alcance como um dispositivo apontador. O sistema está disponível em C++ e Blueprint. Tecnicamente, ele expõe [Windows. UI. Input. Spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)

É importante mencionar que, como os resultados de todas as funções são alterados em todos os quadros, todos eles se tornaram chamáveis. Para obter mais informações sobre funções puras ou que podem ser chamadas, [Confira](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

Para o Blueprint, abra "Windows Mixed Reality HMD"

![Raios-mão BP](images/unreal/hand-rays-bp.png)
 
Para C++, inclua "WindowsMixedRealityFunctionLibrary. h"

### <a name="enum"></a>Enum

![Botões do controlador de entrada](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* **Select** -– disparado pelo usuário selecionar evento, que pode ser disparado no HoloLens 2 por airtap ou olhar e Commit. Outra maneira de disparar esse evento é dizer "Select". 
* **Segure** -– evento de Segure acionado pelo usuário, que é disparado no HoloLens 2 fechando os dedos do usuário em um holograma. 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* Não **rastreado** – a mão não está visível
* **Acompanhado** – a mão é totalmente controlada

### <a name="struct"></a>Struct

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
* **Origem** – origem da mão
* **Direção** – direção da mão
* **Up** – vetor de cima à mão
* **Orientação** – o quaternion de orientação 
* **Status de rastreamento** – status de acompanhamento atual

### <a name="functions"></a>Funções

Todas as funções devem ser chamáveis em todos os quadros para monitoramento contínuo. 

![Obter informações de pose de ponteiro](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
A função retorna as informações completas sobre a direção de raio da mão neste quadro. 

![BP é compreendida](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
Retornará true se a mão estiver segurando neste quadro. 

![É selecione BP pressionado](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
Retornará true se o usuário disparasse Select neste quadro.

![É um botão clicado em BP](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
Retornará true se o evento/botão for disparado neste quadro.

![Obter o status de controle do controlador BP](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
Retorna o status de acompanhamento neste quadro.

## <a name="gestures"></a>Gestos

O Hololens 2 pode acompanhar gestos espaciais. Os detalhes sobre esses gestos são [aqui](https://docs.microsoft.com/hololens/hololens2-basic-usage) que um desenvolvedor pode capturá-los como entrada para seu aplicativo de realidade misturada. 

A função C++ está em "WindowsMixedRealitySpatialInputFunctionLibrary. h"

A função Blueprint está na entrada espacial de realidade misturada do Windows

![Gestos de captura](images/unreal/capture-gestures.png)

### <a name="enum"></a>Enum

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
Essa enumeração descreve gestos de eixo espacial. Você pode ler sobre eles [aqui](holograms-211.md)

### <a name="function"></a>Função

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
A função habilita e desabilita a captura de gestos. Os gestos habilitados acionam eventos de entrada. Retornará true se a ativação da captura do gesto for bem-sucedida e false se houver um erro.
Principais eventos

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
Se o gesto estiver habilitado, os eventos começarão a ser acionados. 

