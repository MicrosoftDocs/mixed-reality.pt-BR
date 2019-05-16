---
title: Mãos e controladores de movimento no DirectX
description: Guia do desenvolvedor para usar o acompanhamento de mão e controladores de movimento em aplicativos nativos do DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: mãos, controladores de movimento, directx, entrada, hologramas
ms.openlocfilehash: 08666c8c26cd4851c0c003a96a9e96d7a90228ac
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629639"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Mãos e controladores de movimento no DirectX

Na realidade mista do Windows, ambos entregar e [controlador de movimento](motion-controllers.md) entrada é tratada por meio de entrada espacial APIs, encontrada na [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) namespace. Isso permite que você manipule facilmente ações comuns, como **selecionar** pressiona da mesma maneira em mãos e controladores de movimento.

## <a name="getting-started"></a>Introdução

Espacial do acesso de entrada na realidade mista do Windows, inicie com a interface SpatialInteractionManager.  Você pode acessar essa interface chamando [SpatialInteractionManager::GetForCurrentView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview), normalmente em algum momento durante a inicialização do aplicativo.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

Trabalho do SpatialInteractionManager é fornecer acesso aos [SpatialInteractionSources](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource), que representam uma fonte de entrada.  Há três tipos de SpatialInteractionSources disponíveis no sistema.
* **Mão** representa mão de um usuário detectado. Fontes de mão oferecem recursos diferentes com base no dispositivo, variando de gestos básicos em HoloLens a mão completamente articulado HoloLens 2 de acompanhamento. 
* **Controlador** representa um controlador de movimento emparelhado. Controladores de movimento podem oferecer uma variedade de recursos.  Por exemplo: Selecione gatilhos, botões de Menu, botões de compreensão, touchpads e alavancas direcionais.
* **Voz** representa a voz do usuário falando em palavras-chave detectados pelo sistema. Por exemplo, essa fonte será injetar um pressionamento de Select e versão sempre que o usuário disser "Select".

Dados por quadro para uma fonte é representada pelo [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) interface. Há duas maneiras diferentes de acessar esses dados, dependendo se você deseja usar um modelo controlado por evento ou baseadas em sondagem em seu aplicativo.

### <a name="event-driven-input"></a>Entrada controlada por evento
O SpatialInteractionManager fornece um número de eventos que seu aplicativo pode escutar.  Alguns exemplos incluem [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) e [SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated).

Por exemplo, o código a seguir conecta um manipulador de eventos chamado MyApp::OnSourcePressed ao evento SourcePressed.  Isso permite que seu aplicativo detectar pressionamentos em qualquer tipo de fonte de interação.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Esse evento pressionado é enviado ao seu aplicativo de forma assíncrona, juntamente com o SpatialInteractionSourceState correspondente no momento em que a imprensa aconteceu. Seu aplicativo ou o mecanismo de jogo pode desejar executar algum processamento imediatamente, ou talvez você queira colocar na fila os dados de evento em sua rotina de processamento de entrada. Aqui está uma função de manipulador de eventos para o evento de SourcePressed, que mostra como verificar se o botão de seleção foi pressionado.

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

O código acima verifica apenas pressione 'Select', que corresponde à ação principal no dispositivo. Exemplos incluem fazer uma AirTap em HoloLens ou extraindo o gatilho em um controlador de animação.  'Select' pressionamentos representam a intenção do usuário para ativar o holograma que eles destinados.  O evento SourcePressed será disparado para um número de botões diferentes e gestos, e você pode inspecionar a outras propriedades a SpatialInteractionSource para testar para esses casos.

### <a name="polling-based-input"></a>Entrada de sondagem
Você também pode usar SpatialInteractionManager para sondar o estado atual da entrada de cada quadro.  Para fazer isso, basta chamar [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) cada quadro.  Essa função retorna uma matriz que contém um [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) para cada ativo [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource). Isso significa um para cada controlador de movimento do Active Directory, um de cada ponteiro controlado e outro para fala, se um comando 'select' foi recentemente proferido. Em seguida, você pode inspecionar as propriedades em cada SpatialInteractionSourceState à entrada de unidade em seu aplicativo. 

Aqui está um exemplo de como verificar a ação 'select' usando o método de sondagem. Observe que o *previsão* variável representa um [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) objeto, que pode ser obtido de [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).

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

Cada SpatialInteractionSource tem uma ID, que você pode usar para identificar novas fontes e correlacionar fontes existentes do quadro a quadro.  Mãos são atribuídas a uma nova ID sempre que eles deixe e insira o FOV, mas identificações de controlador permanecem estáticas para a duração da sessão.  Você pode usar como os eventos em SpatialInteractionManager [SourceDetected](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) e [SourceLost](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost), reagir quando mãos inserir ou deixar o dispositivo de exibição ou quando os controladores de movimento são ativados/desativada ou estejam emparelhado/não emparelhado.

### <a name="predicted-vs-historical-poses"></a>Previstos versus poses históricas
Observe que GetDetectedSourcesAtTimestamp tem um parâmetro de carimbo de hora. Isso permite que você solicitar o estado e apresentar dados ou previsto ou históricos, permitindo você correlacionar espaciais interações com outras fontes de entrada. Por exemplo, ao renderizar a posição da mão no quadro atual, você pode passar no carimbo de hora previsto fornecido pelo [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe). Isso permite que o sistema para a posição de mão para ficarem alinhados com a saída de quadro processado, minimizando a latência percebida de prever de encaminhamento.

No entanto, tal uma pose prevista não produz um ray apontador ideal para o direcionamento com uma fonte de interação. Por exemplo, quando um botão do controlador de movimento é pressionado, pode levar até 20 ms para o evento de emergirem Bluetooth para o sistema operacional. Da mesma forma, depois que um usuário executa um gesto de mão, alguma quantidade de tempo pode passar antes que o sistema detecta o seu aplicativo e o gesto de sonda para ele. No momento a sonda de seu aplicativo para uma alteração de estado, os cabeçalho e mão poses usado para destino interação realmente ocorreu no passado. Se você direcionar, passando o carimbo de hora do seu HolographicFrame atual para GetDetectedSourcesAtTimestamp, a pose serão em vez disso, para frente prevista para o raio de direcionamento no momento em que o quadro será exibido, que pode ser mais de 20 ms no futuro. Esse futuro pose é bom para *renderização* a fonte de interação, mas aumenta ainda mais nosso problema de tempo para *direcionamento* a interação, como o usuário do direcionamento ocorreu no passado.

Felizmente, o [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) e [SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) eventos fornecem o histórico [estado](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) associado cada evento de entrada.  Isso inclui diretamente as históricas poses head e mão disponíveis por meio [TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose), juntamente com um histórico [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) que você pode passar para outras APIs para correlacionar com esse evento.

Isso leva para as seguintes práticas recomendadas quando a renderização e direcionamento com mãos e controladores de cada quadro:
* Para **renderização de mão/controlador** seu aplicativo de cada quadro deve **sondagem** para o **prevista de avanço** apresentam de cada fonte de interação em tempo de photon do quadro atual.  Você pode sondar para todas as fontes de interação, chamando [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) cada quadro, passando o carimbo de hora previsto fornecido pelo [HolographicFrame::CurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.currentprediction).
* Para **mão/controlador direcionamento** após um press ou versão, seu aplicativo deve tratar pressionado/lançado **eventos**, raycasting com base no **históricos** pose head ou disponível para Esse evento. Obtenha esse direcionamento ray manipulando o [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) ou [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) evento, obtendo o [estado](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) propriedade de argumentos do evento e, em seguida, chamar seu [ TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) método.

## <a name="cross-device-input-properties"></a>Propriedades de entrada entre dispositivos
A API SpatialInteractionSource dá suporte a controladores e sistemas com uma ampla gama de recursos de controle de mão. Um número desses recursos é comuns entre os tipos de dispositivo. Por exemplo, mão acompanhamento de movimento controladores e os dois fornecem uma ação 'select' e uma posição 3D. Sempre que possível, a API mapeia essas funcionalidades comuns para as mesmas propriedades no SpatialInteractionSource.  Isso permite que aplicativos mais facilmente dar suporte a uma ampla variedade de tipos de entrada. A tabela a seguir descreve as propriedades que têm suporte e como eles se comparam em todos os tipos de entrada.

| Propriedade | Descrição | Gestos do HoloLens | Controladores de movimento | Mãos articuladas|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**Handedness**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | À direita ou à esquerda / controlador. | Sem suporte | Com suporte | Com suporte |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Estado atual do botão principal. | Indicador e polegar | gatilho | Toque ar reduzida (pinch vertical) |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Estado atual do botão de captura. | Sem suporte | Botão de captura | Mão aperto ou fechado |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Estado atual do botão de menu.    | Sem suporte | Botão de menu | Sem suporte |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | Local de XYZ da mão ou alça de posição no controlador. | Local de Palm | Alça pose posição | Local de Palm |
| [SpatialInteractionSourceLocation::**Orientation**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Quaternion que representa a orientação da mão ou alça representar no controlador. | Sem suporte | Orientação da alça pose | Orientação de Palm |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Origem do raio apontando. | Sem suporte | Com suporte | Com suporte |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Direção do raio apontando. | Sem suporte | Com suporte | Com suporte |

Algumas das propriedades acima não estão disponíveis em todos os dispositivos e a API fornece um meio para testar isso. Por exemplo, você pode inspecionar a [SpatialInteractionSource::IsGraspSupported](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) propriedade para determinar se o código-fonte fornece uma melhor compreensão ação.

### <a name="grip-pose-vs-pointing-pose"></a>Alça pose versus pose apontador

Realidade mista do Windows oferece suporte a controladores de movimento em uma variedade de fatores forma.  Ele também dá suporte a sistemas de controle de mão articulada.  Todos esses sistemas têm diferentes relações entre a posição de mão e a direção de "avanço" natural que aplicativos devem usar para objetos que aponta ou rendreing em mãos do usuário.  Para dar suporte a tudo isso, há dois tipos de 3D poses fornecidos para ambos os controladores de acompanhamento e o movimento de mão.  A primeira é pose alça, que representa a posição do usuário manualmente.  A segunda está apontando pose, que representa um raio de apontador provenientes de mão ou controlador do usuário. Portanto, se você deseja renderizar **mão do usuário** ou **um objeto é mantido em mãos do usuário**, tais como uma espada ou elétrons, use a alça pose. Se você quiser raycast do controlador ou manualmente, por exemplo, quando o usuário estiver **apontando para a interface do usuário** , use o apontador pose.

Você pode acessar o **alça pose** por meio de [SpatialInteractionSourceState::Properties::TryGetLocation(...) ](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).  Ele é definido da seguinte maneira:
* O **segure posição**: O centroide de palm pressionando o controlador naturalmente, ajustado esquerda ou direita para centralizar a posição dentro a alça.
* O **Segure o eixo à direita da orientação**: Quando você abre completamente sua mão para formar uma dedo simples 5 pose, raio que é normal para o palm (para a frente da esquerda palm, com versões anteriores do palm à direita)
* O **Segure o eixo de encaminhamento da orientação**: Quando você fecha sua mão parcialmente (como se que mantém o controlador), o raio que aponta "forward" por meio de tubo formado por seus dedos não thumb.
* O **segure orientação backup eixo**: O eixo de cima indicado pelas definições de direito e Avançar.

Você pode acessar o **ponteiro pose** por meio [SpatialInteractionSourceState::Properties::TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) ou [SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

## <a name="controller-specific-input-properties"></a>Propriedades de entrada específica ao controlador
Para controladores, o SpatialInteractionSource tem uma propriedade de controlador com recursos adicionais.
* **HasThumbstick:** Se for true, o controlador tem um analógico. Inspecione o [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) propriedade do SpatialInteractionSourceState para adquirir o analógico x e y de valores (ThumbstickX e ThumbstickY), bem como seu estado pressionado (IsThumbstickPressed).
* **HasTouchpad:** Se for true, o controlador tem um touchpad. Inspecionar a propriedade ControllerProperties do SpatialInteractionSourceState para adquirir o touchpad x e y valores (TouchpadX e TouchpadY), bem como para saber se o usuário toca o teclado (IsTouchpadTouched) e se eles estão nos pressionando o touchpad para baixo ( IsTouchpadPressed).
* **SimpleHapticsController:** A API SimpleHapticsController para o controlador permite que você inspecione as capacidades de haptics do controlador, e ele também permite que você controle os comentários hápticos.

Observe que o intervalo para touchpad e analógico é -1 para 1 para ambos os eixos (de baixo para cima e da esquerda para direita). O intervalo para o gatilho analógico, que pode é acessado usando a propriedade SpatialInteractionSourceState::SelectPressedValue, tem um intervalo de 0 a 1. Um valor de 1 correlaciona com IsSelectPressed sendo igual a true; qualquer outro valor se correlaciona com IsSelectPressed sendo igual a false.

## <a name="articulated-hand-tracking"></a>Articuladas mão de acompanhamento
A API de realidade mista do Windows fornece suporte completo para articuladas mão de controle, por exemplo em HoloLens 2. Articuladas mão de controle pode ser usado para implementar a manipulação direta e modelos de confirmação e de ponto de entrada em seus aplicativos. Ele também pode ser usado para criar interações totalmente personalizadas.

### <a name="hand-skeleton"></a>Esqueleto de mão
Mão articulada controle fornece um esqueleto conjunta 25 que permite que muitos tipos diferentes de interações.  O esqueleto fornece 5 junções para os dedos de índice/intermediária/anel/pequeno, 4 junções para o elevador e 1 pulso conjunto.  A junção de pulso serve como a base da hierarquia. A imagem a seguir ilustra o layout de esqueleto.

![Esqueleto de mão](images/hand-skeleton.png)

Na maioria dos casos, cada conjunto é nomeado com base em bem-acabados que ele representa.  Como há duas funções em cada conjunto, podemos usar uma convenção de nomenclatura de cada junção com base em bem-acabados filho nesse local.  Bem-acabados filho é definido como bem-acabados mais longe de pulso.  Por exemplo, o "índice Proximal" conjunta contém a posição de início do bem-acabados proximal índice e a orientação de que funções básicas.  Ele não contém a posição final de bem-acabados.  Se você precisar que, você teria obtê-lo do próximo conjunto na hierarquia, o "índice intermediário" conjunta.

Além de 25 junções hierárquicas, o sistema fornece uma união palm.  O palm normalmente não é considerado parte da sua estrutura.  Ele é fornecido apenas como uma maneira conveniente de obter a posição e orientação geral a mão.

As informações a seguir são fornecidas para cada conjunto:

| Nome | Descrição |
|--- |--- |
|Posição | Posição 3D da junção, disponível em qualquer sistema de coordenadas solicitado. |
|Orientação | Orientação 3D do bem-acabados, disponível em nenhum solicitou o sistema de coordenadas. |
|Radius | Distância até a superfície da capa a posição do conjunto. Úteis para ajuste interações diretas ou visualizações que se baseiam na largura do dedo. |
|Precisão | Fornece uma dica sobre o sistema de quão confiante pensa sobre informações de conjuntos. |

Você pode acessar os dados de esqueleto de mão por meio de uma função na [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).  A função é chamada [TryGetHandPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose), e ele retorna um objeto chamado [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose).  Se a fonte não dá suporte a articuladas mãos, em seguida, essa função retornará null.  Quando você tiver um HandPose, você pode obter dados do conjuntos atual chamando [TryGetJoint](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), com o nome da junção que lhe interessam.  Os dados são retornados como uma [JointPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.jointpose) estrutura.  O código a seguir obtém a posição da ponta do dedo. A variável *currentState* representa uma instância de [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

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

### <a name="hand-mesh"></a>Malha de mão

A API de controle de mão articulada permite que uma malha de mão do triângulo deformável totalmente.  Essa malha pode Deformar em tempo real, juntamente com o esqueleto de mão e é útil para visualização, bem como técnicas avançadas de física.  Para acessar a malha de mão, você precisa primeiro criar uma [HandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver) objeto chamando [TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) sobre o [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource).  Isso só precisa ser feito uma vez por origem, normalmente na primeira vez que você vê-lo.  Isso significa que você chamará essa função para criar um objeto HandMeshObserver sempre que o FOV entra em uma mão.  Observe que se trata de uma função assíncrona, então você terá que lidar com um pouco de simultaneidade aqui.  Quando estiver disponível, você pode solicitar o objeto HandMeshObserver o buffer de índices de triângulo chamando [GetTriangleIndices](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___).  Índices não são alterados quadro por quadro, para que você possa obtê-los uma vez e armazenam em cache para o tempo de vida da fonte de.  Índices são fornecidos no sentido horário para giro.

O código a seguir gira um std:: thread desanexado para criar o observador de malha e extrai o buffer de índices depois que o observador de malha está disponível.  Ele inicia de uma variável chamada *currentState*, que é uma instância do [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) que representa uma mão controlada.

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
Iniciar um thread desanexado é apenas uma opção para lidar com chamadas assíncronas.  Como alternativa, você pode usar o novo [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) funcionalidade com suporte de C++/WinRT.

Depois que um objeto HandMeshObserver, deverá mantê-lo durante o tempo que seu SpatialInteractionSource correspondente está ativa.  Em seguida, cada quadro, você poderá pedir para o buffer de vértice mais recente que representa a mão chamando [GetVertexStateForPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) e passar em um [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose) instância que representa a pose que deseja que os vértices para.  Cada vértice no buffer tem uma posição e um normal.  Aqui está um exemplo de como obter o conjunto atual de vértices para uma malha de mão.  Como antes, o *currentState* variável representa uma instância do [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

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

Em contraste com junções de esqueleto, a API de malha de mão não permitem que você especifique um sistema de coordenadas para os vértices.  Em vez disso, o [HandMeshVertexState](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshvertexstate) Especifica que os vértices são fornecidos no sistema de coordenadas.  Em seguida, você pode obter uma transformação de malha chamando [TryGetTransformTo](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) e especifica seu sistema de coordenadas desejado.  Você precisará usar essa transformação malha sempre que trabalhar com os vértices.  Essa abordagem reduz a sobrecarga de CPU, especialmente se você estiver usando a malha apenas para fins de renderização.

## <a name="gaze-and-commit-composite-gestures"></a>Mantenha o foco e confirmar gestos de composição
Para aplicativos que usam o modelo de entrada de olhar e confirmação, particularmente em HoloLens (Ger primeiro), a API de entrada espacial fornece um recurso opcional [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) que pode ser usado para habilitar gestos compostos criados na parte superior das 'select' eventos.  Ao roteamentos interações do SpatialInteractionManager para SpatialGestureRecognizer de um holograma, aplicativos podem detectar eventos de toque, espera, manipulação e navegação uniformemente em mãos, voz e dispositivos de entrada espaciais, sem a necessidade que tratar pressionamentos de e libera manualmente.

SpatialGestureRecognizer executa somente a Desambiguidade mínimo entre o conjunto de gestos de que você solicitar. Por exemplo, se você solicitar apenas toque, o usuário pode pressionada seu dedo, desde que eles gostam e um toque ainda ocorrerá. Se você solicitar o toque e mantenha, após cerca de um segundo de mantendo seu dedo, o gesto promoverá a uma isenção e um toque não ocorrerão mais.

Para usar SpatialGestureRecognizer, lidar com o SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) eventos e captura o SpatialPointerPose exposto lá. Use ray de olhar principal do usuário dessa pose para ter interseção com as hologramas e superfície malhas no ambiente do usuário, para determinar o que o usuário pretende interagir com. Em seguida, encaminhar o SpatialInteraction nos argumentos de evento para SpatialGestureRecognizer do holograma de destino, usando seus [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) método. Isso inicia a interpretação de interação de acordo com o [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) definir esse reconhecedor no momento da criação - ou pelo [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

No HoloLens (Ger primeiro), as interações e gestos geralmente devem derivar seu direcionamento de olhar de principal do usuário, em vez de tentar renderizar ou interagir diretamente no local da mão. Após o início de uma interação relativos movimentos da mão podem ser usados para controlar o gesto, assim como acontece com o gesto de manipulação ou navegação.

## <a name="see-also"></a>Consulte também
* [Cabeçalho e olho olhar no DirectX](gaze-in-directx.md)
* [Modelo de entrada de manipulação direta](direct-manipulation.md)
* [Modelo de entrada de ponto-e-confirmação](point-and-commit.md)
* [Mantenha o foco e confirmar o modelo de entrada](gaze-and-commit.md)
* [Controladores de movimentos](motion-controllers.md)
