---
title: Controladores de mãos e de movimento no DirectX
description: Guia do desenvolvedor para usar o rastreamento e os controladores de movimento em aplicativos nativos do DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: mãos, controladores de movimento, DirectX, entrada, hologramas
ms.openlocfilehash: 54eaacc3f0dccf728b5438c020a5efd7e0788251
ms.sourcegitcommit: 4081dc2356fec0ea3625f1d989689cfbbb3fcf5f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74203335"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Controladores de mãos e de movimento no DirectX

No Windows Mixed Reality, a entrada do [controlador de movimento](motion-controllers.md) e a mão são manipuladas por meio de APIs de entrada espaciais, encontradas no namespace [Windows. UI. Input. espacial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) . Isso permite que você manipule facilmente ações comuns, como **Select** , da mesma maneira em ambos os controladores de mãos e de movimento.

## <a name="getting-started"></a>Introdução

Para acessar a entrada espacial na realidade mista do Windows, comece com a interface SpatialInteractionManager.  Você pode acessar essa interface chamando [SpatialInteractionManager:: GetForCurrentView](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview), normalmente durante a inicialização do aplicativo.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

O trabalho do SpatialInteractionManager é fornecer acesso ao [SpatialInteractionSources](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource), que representa uma fonte de entrada.  Há três tipos de SpatialInteractionSources disponíveis no sistema.
* A **mão** representa a mão detectada do usuário. As fontes de mão oferecem diferentes recursos com base no dispositivo, variando de gestos básicos no HoloLens até o controle de mão totalmente articulado no HoloLens 2. 
* O **controlador** representa um controlador de movimento emparelhado. Os controladores de movimento podem oferecer uma variedade de recursos.  Por exemplo: selecionar gatilhos, botões de menu, entender botões, touchpads e Thumbsticks.
* **Voz** representa as palavras-chave detectadas pelo sistema de fala de voz do usuário. Por exemplo, essa fonte injetará uma prensa e uma liberação Select sempre que o usuário disser "Select".

Os dados por quadro de uma fonte são representados pela interface [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) . Há duas maneiras diferentes de acessar esses dados, dependendo se você deseja usar um modelo controlado por eventos ou baseado em sondagem em seu aplicativo.

### <a name="event-driven-input"></a>Entrada orientada por evento
O SpatialInteractionManager fornece vários eventos que seu aplicativo pode escutar.  Alguns exemplos incluem [SourcePressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) e [SourceUpdated](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated).

Por exemplo, o código a seguir conecta um manipulador de eventos chamado MyApp:: OnSourcePressed ao evento SourcePressed.  Isso permite que seu aplicativo detecte pressionamentos em qualquer tipo de fonte de interação.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Esse evento pressionado é enviado para seu aplicativo de forma assíncrona, junto com o SpatialInteractionSourceState correspondente no momento em que a ocorrência ocorreu. Seu aplicativo ou mecanismo de jogo pode querer executar algum processamento imediatamente ou você pode querer enfileirar os dados de evento em sua rotina de processamento de entrada. Aqui está uma função de manipulador de eventos para o evento SourcePressed, que mostra como verificar se o botão de seleção foi pressionado.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

O código acima verifica apenas a prensa ' Select ', que corresponde à ação principal no dispositivo. Os exemplos incluem fazer um AirTap no HoloLens ou extrair o gatilho em um controlador de movimento.  "Select" Presss representam a intenção do usuário de ativar o holograma que eles estão direcionando.  O evento SourcePressed será acionado para vários botões e gestos diferentes, e você poderá inspecionar outras propriedades no SpatialInteractionSource para testar esses casos.

### <a name="polling-based-input"></a>Entrada baseada em sondagem
Você também pode usar SpatialInteractionManager para sondar o estado atual de entrada de cada quadro.  Para fazer isso, basta chamar [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) todos os quadros.  Essa função retorna uma matriz que contém um [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) para cada [SpatialInteractionSource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)ativo. Isso significa que um para cada controlador de movimento ativo, um para cada mão controlada e outro para fala se um comando ' Select ' foi recentemente desmarcado. Em seguida, você pode inspecionar as propriedades em cada SpatialInteractionSourceState para direcionar a entrada para o seu aplicativo. 

Aqui está um exemplo de como verificar a ação ' Select ' usando o método de sondagem. Observe que a variável de *previsão* representa um objeto [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , que pode ser obtido do [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

Cada SpatialInteractionSource tem uma ID, que pode ser usada para identificar novas fontes e correlacionar as fontes existentes do quadro ao quadro.  As mãos recebem uma nova ID toda vez que deixam e inserem o FOV, mas as IDs de controlador permanecem estáticas durante a sessão.  Você pode usar os eventos em SpatialInteractionManager, como [SourceDetected](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) e [SourceLost](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost), para reagir quando as mãos entrarem ou saírem do modo de exibição do dispositivo ou quando os controladores de movimento estiverem ativados ou desligados ou estiverem emparelhados/não emparelhados.

### <a name="predicted-vs-historical-poses"></a>Previstos versus histórico de poses
Observe que GetDetectedSourcesAtTimestamp tem um parâmetro timestamp. Isso permite solicitar o estado e representar os dados que são previstos ou históricos, permitindo que você correlacione as interações espaciais com outras fontes de entrada. Por exemplo, ao renderizar a posição da mão no quadro atual, você pode passar o carimbo de data/hora previsto fornecido pelo [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe). Isso permite que o sistema faça uma previsão antecipada da posição da mão para alinhar fortemente com a saída do quadro renderizado, minimizando a latência percebida.

No entanto, tal pose prevista não produz um apontador ideal para direcionar com uma fonte de interação. Por exemplo, quando um botão de controlador de movimento é pressionado, pode levar até 20 ms para que esse evento seja emergido por meio do Bluetooth para o sistema operacional. Da mesma forma, depois que um usuário executa um gesto de mão, uma quantidade de tempo pode passar antes que o sistema detecte o gesto e seu aplicativo o sonda para ele. Quando o aplicativo sonda uma alteração de estado, a cabeça e a mão são usadas para direcionar essa interação realmente ocorrida no passado. Se você se destinar passando o carimbo de data/hora atual do HolographicFrame para GetDetectedSourcesAtTimestamp, a pose será encaminhada prevista para o destino Ray no momento em que o quadro será exibido, o que poderia ser mais de 20 ms no futuro. Essa futura pose é boa para *renderizar* a origem da interação, mas aumenta nosso problema de tempo para *direcionar* a interação, já que o direcionamento do usuário ocorreu no passado.

Felizmente, os eventos [SourcePressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) e [SourceUpdated](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) fornecem o [estado](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) histórico associado a cada evento de entrada.  Isso inclui diretamente o cabeçalho histórico e as poses de mão disponíveis por meio de [TryGetPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose), juntamente com um [carimbo de data/hora](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) histórico que você pode passar para outras APIs para correlacionar com esse evento.

Isso leva às seguintes práticas recomendadas ao renderizar e direcionar com mãos e controladores a cada quadro:
* Para **renderização à mão/controlador** em cada quadro, seu aplicativo deve **sondar** a pose **previsível** de cada fonte de interação na hora do Photon do quadro atual.  Você pode sondar todas as fontes de interação chamando [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) a cada quadro, passando o carimbo de data/hora previsto fornecido por [HolographicFrame:: CurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.currentprediction).
* Para **direcionamento à mão/controlador** em um Press ou Release, seu aplicativo deve lidar com **eventos**prensados/liberados, raycasting com base na cabeça **histórica** ou na pose do evento. Você obtém esse destino Ray manipulando o evento [SourcePressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) ou [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) , obtendo a propriedade [State](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) dos argumentos do evento e, em seguida, chamando seu método [TryGetPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .

## <a name="cross-device-input-properties"></a>Propriedades de entrada de dispositivo cruzado
A API do SpatialInteractionSource dá suporte a controladores e sistemas de acompanhamento de mão com uma ampla gama de recursos. Vários desses recursos são comuns entre os tipos de dispositivo. Por exemplo, o rastreamento de mão e os controladores de movimento fornecem uma ação ' Select ' e uma posição 3D. Sempre que possível, a API mapeia esses recursos comuns para as mesmas propriedades no SpatialInteractionSource.  Isso permite que os aplicativos ofereçam suporte mais facilmente a uma ampla gama de tipos de entrada. A tabela a seguir descreve as propriedades com suporte e como elas são comparadas entre os tipos de entrada.

| Propriedade | Descrição | Gestos de HoloLens (1º gen) | Controladores de movimento | Mãos articuladas|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**destro/canhoto**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | À direita ou à esquerda/controlador. | Sem suporte | Com suporte | Com suporte |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Estado atual do botão primário. | Toque de ar | Disparador | Toque de ar relaxado (pinçagem vertical) |
| [SpatialInteractionSourceState::**Issegured**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Estado atual do botão de captura. | Sem suporte | Botão de captura | Apertar ou fechar mão |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Estado atual do botão de menu.    | Sem suporte | Botão de menu | Sem suporte |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | Local XYZ da posição da mão ou de alças no controlador. | Local do Palm | Segurar posição de pose | Local do Palm |
| [SpatialInteractionSourceLocation::**Orientation**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Quaternion representando a orientação da posição de mão ou de alça no controlador. | Sem suporte | Segure a orientação da pose | Orientação de Palm |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Origem do raio de apontar. | Sem suporte | Com suporte | Com suporte |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Direção do raio de apontar. | Sem suporte | Com suporte | Com suporte |

Algumas das propriedades acima não estão disponíveis em todos os dispositivos, e a API fornece um meio de testar isso. Por exemplo, você pode inspecionar a propriedade [SpatialInteractionSource:: IsGraspSupported](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) para determinar se a origem fornece uma ação de compreensão.

### <a name="grip-pose-vs-pointing-pose"></a>Segurar pose vs. ponto de apontar

O Windows Mixed Reality dá suporte a controladores de movimento em uma variedade de fatores forma.  Ele também dá suporte a sistemas de controle de mão articulados.  Todos esses sistemas têm diferentes relações entre a posição da mão e a direção natural "encaminhar" que os aplicativos devem usar para apontar ou renderizar objetos na mão do usuário.  Para dar suporte a tudo isso, há dois tipos de poses 3D fornecidos para os controladores de rastreamento e de movimento à mão.  A primeira é Segure pose, que representa a posição da mão do usuário.  A segunda é a pose de ponto, que representa um ponteiro de raio originário da mão do usuário ou do controlador. Portanto, se você quiser renderizar **a mão do usuário** ou **um objeto mantido na mão do usuário**, como uma gumes ou uma arma, use a pose de alça. Se você quiser Raycast do controlador ou da mão, por exemplo, quando o usuário estiver **apontando** para a interface de usuário, use a pose de ponteiro.

Você pode acessar a **alça de pose** por meio de [SpatialInteractionSourceState::P Propriedades:: TryGetLocation (...)](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).  Ele é definido da seguinte maneira:
* A **posição de alça**: o Palm centróide ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralizar a posição dentro da alça.
* O **eixo direito da orientação de alça**: quando você abre completamente a mão para formar uma pose plana de 5 dedos, o raio normal para o Palm (para frente do Palm esquerdo, para trás do Palm direito)
* O **eixo de encaminhamento da orientação de alça**: quando você fecha a sua mão parcialmente (como se você mantiver o controlador), o raio que aponta para "encaminhar" por meio do tubo formado por seus dedos não-thumbs.
* O **eixo superior da orientação de alça**: o eixo superior implícito pelas definições direita e avançar.

Você pode acessar o **ponteiro de pose** por meio de [SpatialInteractionSourceState::P Propriedades:: TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) ou [SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

## <a name="controller-specific-input-properties"></a>Propriedades de entrada específicas do controlador
Para controladores, o SpatialInteractionSource tem uma propriedade de controlador com recursos adicionais.
* **HasThumbstick:** Se for true, o controlador terá um Thumbstick. Inspecione a propriedade [controllerproperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) do SpatialInteractionSourceState para adquirir os valores x e y de Thumbstick (ThumbstickX e ThumbstickY), bem como seu estado pressionado (IsThumbstickPressed).
* **HasTouchpad:** Se for true, o controlador terá um touchpad. Inspecione a propriedade Controllerproperties do SpatialInteractionSourceState para adquirir os valores x e y do Touchpad (TouchpadX e touchpad) e para saber se o usuário está tocando no Pad (IsTouchpadTouched) e se eles estão pressionando o touchpad ( IsTouchpadPressed).
* **SimpleHapticsController:** A API do SimpleHapticsController para o controlador permite inspecionar os recursos do haptics do controlador e também permite que você controle os comentários do Haptic.

Observe que o intervalo para Touchpad e Thumbstick é de-1 a 1 para ambos os eixos (de baixo para cima e da esquerda para a direita). O intervalo para o gatilho analógico, que é acessado usando a propriedade SpatialInteractionSourceState:: SelectPressedValue, tem um intervalo de 0 a 1. Um valor de 1 se correlaciona com IsSelectPressed sendo igual a true; qualquer outro valor se correlaciona com IsSelectPressed sendo igual a false.

## <a name="articulated-hand-tracking"></a>Acompanhamento de mão articulada
A API do Windows Mixed Reality fornece suporte completo para acompanhamento de mão articulada, por exemplo, no HoloLens 2. O controle de mão articulado pode ser usado para implementar a manipulação direta e modelos de entrada de ponto e confirmação em seus aplicativos. Ele também pode ser usado para criar interações totalmente personalizadas.

### <a name="hand-skeleton"></a>Esqueleto da mão
O controle de mão articulado fornece um esqueleto de 25 conjunta que permite muitos tipos diferentes de interações.  O esqueleto fornece 5 junções para o índice/meio/anel/pequenos dedos, 4 junções para o Thumb e 1 junta de pulso.  A junta do pulso serve como a base da hierarquia. A figura a seguir ilustra o layout do esqueleto.

![Esqueleto da mão](images/hand-skeleton.png)

Na maioria dos casos, cada conjunto é nomeado com base no Bone que ele representa.  Como há dois Bones em cada conjunto, usamos uma Convenção de nomear cada conjunto com base no Bone filho nesse local.  O Bone filho é definido como o Bone além do pulso.  Por exemplo, a junção "index proximal" contém a posição inicial do proximal Bone do índice e a orientação desse Bone.  Ele não contém a posição final do Bone.  Se precisar disso, você o obteria do próximo conjunto na hierarquia, a junção de "índice intermediário".

Além das 25 junções hierárquicas, o sistema fornece um conjunto de Palm.  A Palm normalmente não é considerada parte da estrutura estrutural.  Ele é fornecido apenas como uma maneira conveniente de obter a posição e a orientação gerais do manual.

As informações a seguir são fornecidas para cada conjunto:

| Nome | Descrição |
|--- |--- |
|Posição | posição 3D da junção, disponível em qualquer sistema de coordenadas solicitado. |
|Orientação | orientação 3D do Bone, disponível em qualquer sistema de coordenadas solicitado. |
|Radius | Distância da superfície da capa na posição conjunta. Útil para ajustar interações diretas ou visualizações que dependem da largura do dedo. |
|Precisão | Fornece uma dica sobre a confiança do sistema sobre as informações deste conjunto. |

Você pode acessar os dados de esqueleto da mão por meio de uma função no [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).  A função é chamada de [TryGetHandPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)e retorna um objeto chamado [HandPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose).  Se a origem não der suporte a mãos articuladas, essa função retornará NULL.  Depois de ter um HandPose, você pode obter os dados concorrentes atuais chamando [TryGetJoint](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), com o nome da junção em que você está interessado.  Os dados são retornados como uma estrutura [JointPose](https://docs.microsoft.com//uwp/api/windows.perception.people.jointpose) .  O código a seguir obtém a posição da dica de dedo do índice. A variável *CurrentState* representa uma instância de [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>Malha à mão

A API de acompanhamento de mão articulada permite uma malha à mão do triângulo totalmente reformado.  Essa malha pode Deform em tempo real junto com o esqueleto da mão e é útil para visualização, bem como técnicas de física avançadas.  Para acessar a malha à mão, primeiro você precisa criar um objeto [HandMeshObserver](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver) chamando [TryCreateHandMeshObserverAsync](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) no [SpatialInteractionSource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource).  Isso só precisa ser feito uma vez por fonte, normalmente na primeira vez que você o vê.  Isso significa que você chamará essa função para criar um objeto HandMeshObserver sempre que uma mão inserir o FOV.  Observe que essa é uma função assíncrona, portanto, você terá que lidar com um pouco de simultaneidade aqui.  Uma vez disponível, você pode solicitar ao objeto HandMeshObserver para o buffer de índice de triângulo chamando [GetTriangleIndices](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___).  Os índices não alteram o quadro no quadro, para que você possa obtê-los uma vez e armazená-los em cache durante o tempo de vida da origem.  Os índices são fornecidos na ordem de enrolamento no sentido horário.

O código a seguir gira um std:: thread desanexado para criar o observador de malha e extrai o buffer de índice quando o observador de malha está disponível.  Ele começa com uma variável chamada *CurrentState*, que é uma instância de [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) que representa uma mão controlada.

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
Iniciar um thread desanexado é apenas uma opção para lidar com chamadas assíncronas.  Como alternativa, você pode usar a nova funcionalidade de [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) com C++suporte do/WinRT.

Depois de ter um objeto HandMeshObserver, você deve mantê-lo durante a duração em que seu SpatialInteractionSource correspondente está ativo.  Em seguida, cada quadro pode ser solicitado para o último buffer de vértice que representa a mão chamando [GetVertexStateForPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) e passando uma instância [HandPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose) que represente a pose para a qual você deseja vértices.  Cada vértice no buffer tem uma posição e um normal.  Aqui está um exemplo de como obter o conjunto atual de vértices para uma malha à mão.  Assim como antes, a variável *CurrentState* representa uma instância de [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

Ao contrário das junções de esqueleto, a API de malha à mão não permite que você especifique um sistema de coordenadas para os vértices.  Em vez disso, o [HandMeshVertexState](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshvertexstate) especifica o sistema de coordenadas no qual os vértices são fornecidos.  Em seguida, você pode obter uma transformação de malha chamando [TryGetTransformTo](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) e especificando o sistema de coordenadas desejado.  Você precisará usar essa transformação de malha sempre que trabalhar com os vértices.  Essa abordagem reduz a sobrecarga da CPU, especialmente se você estiver usando apenas a malha para fins de processamento.

## <a name="gaze-and-commit-composite-gestures"></a>Gestos de composição olhar e Commit
Para aplicativos que usam o modelo de entrada olhar-and-Commit, especialmente no HoloLens (primeira gen), a API de entrada espacial fornece um [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) opcional que pode ser usado para habilitar gestos compostos criados sobre o evento ' Select '.  Ao rotear interações do SpatialInteractionManager para o SpatialGestureRecognizer de um holograma, os aplicativos podem detectar eventos de toque, retenção, manipulação e navegação uniformemente entre dispositivos de entrada de teclado, de voz e espaciais, sem a necessidade de lidar com prensas e libera manualmente.

SpatialGestureRecognizer executa apenas a Desambigüidade mínima entre o conjunto de gestos que você solicita. Por exemplo, se você solicitar apenas o toque, o usuário poderá manter seu dedo no mesmo tempo que desejar e um toque ainda ocorrerá. Se você solicitar tocar e segurar, depois de cerca de um segundo de manter o dedo, o gesto será promovido para uma espera e um toque não ocorrerá mais.

Para usar o SpatialGestureRecognizer, manipule o evento [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) do SpatialInteractionManager e pegue o SpatialPointerPose exposto lá. Use o cabeçalho do usuário olhar Ray desta pose para fazer a interseção com os hologramas e as malhas de superfície no ambiente do usuário, a fim de determinar o que o usuário está pretendendo a interagir com o. Em seguida, encaminhe o SpatialInteraction nos argumentos do evento para o SpatialGestureRecognizer do holograma de destino, usando seu método [CaptureInteraction](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) . Isso começa a interpretar essa interação de acordo com o [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) definido no reconhecedor no momento da criação-ou por [TrySetGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

No HoloLens (primeira gen), as interações e gestos geralmente devem derivar seu direcionamento do olhar de cabeça do usuário, em vez de tentar renderizar ou interagir diretamente no local da mão. Depois que uma interação for iniciada, movimentos relativos da mão poderão ser usados para controlar o gesto, assim como com o gesto de manipulação ou de navegação.

## <a name="see-also"></a>Consulte também
* [Olhar fixo com cabeça e olhos no DirectX](gaze-in-directx.md)
* [Modelo de entrada de manipulação direta](direct-manipulation.md)
* [Modelo de entrada de ponto e confirmação](point-and-commit.md)
* [Olhar e confirmar modelo de entrada](gaze-and-commit.md)
* [Controladores de movimentos](motion-controllers.md)
