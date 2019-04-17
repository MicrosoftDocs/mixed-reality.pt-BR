---
title: Olhar, gestos e controladores de movimento no DirectX
description: Combinação de entrada provenientes de olhar, gestos e controladores de movimento, você pode permitir que um usuário colocar um holograma em seu aplicativo.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: olhares, gestos, controladores de movimento, directx, entrada, hologramas
ms.openlocfilehash: 7cee3d3d7fbcd903eae0376e205034b9cc4ead3b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591018"
---
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a>Olhar, gestos e controladores de movimento no DirectX

Se você pretende criar diretamente sobre a plataforma, você terá que lidar com a entrada proveniente do usuário – como onde o usuário está procurando por meio [olhar principal](gaze.md) e o que o usuário selecionou com [gestos](gestures.md) ou [controladores de movimento](motion-controllers.md). Combinando esses formulários de entrada, você pode permitir que um usuário colocar uma [holograma](hologram.md) em seu aplicativo. O [modelo de aplicativo holográfica](creating-a-holographic-directx-project.md) tem um exemplo de fácil de usar.

>[!NOTE]
>Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.

## <a name="gaze-input"></a>Entrada com foco

Para acessar o usuário [olhar principal](gaze.md), você usa o [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) tipo. O modelo de aplicativo holográfica inclui código básico para olhar compreensão. Esse código fornece um vetor que aponta para a frente entre a atenção do usuário, levando em conta posição do dispositivo e a orientação em um determinado [sistema de coordenadas](coordinate-systems-in-directx.md).




```cpp
void SpinningCubeRenderer::PositionHologram(SpatialPointerPose^ pointerPose)
{
    if (pointerPose != nullptr)
    {
        // Get the gaze direction relative to the given coordinate system.
        const float3 headPosition    = pointerPose->Head->Position;
        const float3 headDirection   = pointerPose->Head->ForwardDirection;
    
        // The hologram is positioned two meters along the user's gaze direction.
        static const float distanceFromUser = 2.0f; // meters
        const float3 gazeAtTwoMeters        = headPosition + (distanceFromUser * headDirection);
    
        // This will be used as the translation component of the hologram's
        // model transform.
        SetPosition(gazeAtTwoMeters);
    }
}
```

Você pode achar se perguntando: "Mas, em que o sistema de coordenadas vêm do?"

Vamos responder essa pergunta. Em nosso AppMain **atualização** função, processamos um evento de entrada espacial adquirindo-lo em relação ao sistema de coordenadas para nosso StationaryFrameOfReference. Lembre-se de que o StationaryFrameOfReference foi criado quando configuramos o [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), e o sistema de coordenadas foi adquirido no início da [atualização](rendering-in-directx.md).




```cpp
// Check for new input state since the last frame.
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
if (pointerState != nullptr)
{
    // When a Pressed gesture is detected, the sample hologram will be repositioned
    // two meters in front of the user.
    m_spinningCubeRenderer->PositionHologram(
        pointerState->TryGetPointerPose(currentCoordinateSystem)
        );
}
```

Observe que os dados estão vinculados a um estado de algum tipo de ponteiro. Podemos obter isso de um evento de entrada espacial. O objeto de dados de evento inclui um sistema de coordenadas, para que você sempre pode relacionar a direção de olhar no momento do evento a qualquer sistema de coordenadas espacial, você precisa. Na verdade, você deve fazer isso para obter a pose de ponteiro.

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).

## <a name="gesture-and-motion-controller-input"></a>Controlador de movimento e de gesto de entrada

Na realidade mista do Windows, ambos entregar [gestos](gestures.md) e [controladores de movimento](motion-controllers.md) são tratadas por meio da mesma espacial entrada APIs, encontrada no [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) namespace. Isso permite que você manipule facilmente ações comuns, como **selecionar** pressiona da mesma maneira em mãos e controladores de movimento.

Há dois níveis de API que você pode direcionar ao lidar com gestos ou controladores de movimento, na realidade mista:
* [Interações](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) e [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), acessado usando um [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)
* [Gestos de composição](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), mantenha, manipulação de navegação), acessado usando um [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a>Selecione/Menu/compreensão/Touchpad/analógico interações: SpatialInteractionManager

Para detectar os pressionamentos de baixo nível, versões e atualizações em mãos e dispositivos de entrada no Windows Mixed Reality, você iniciar de um [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx). O SpatialInteractionManager tem um evento que informa ao aplicativo quando uma mão ou controlador de movimento foi detectado entrada.

Há três tipos principais de SpatialInteractionSource, cada um representado por um valor diferente de SpatialInteractionSourceKind:
* **Mão** representa mão de um usuário detectado. Fontes de mão estão disponíveis apenas em HoloLens.
* **Controlador** representa um controlador de movimento emparelhado. Controladores de movimento podem oferecer uma variedade de recursos, por exemplo: Selecione gatilhos, botões de Menu, botões de compreensão, touchpads e alavancas direcionais.
* **Voz** representa a voz do usuário falando em palavras-chave detectados pelo sistema. Isso será injetar um pressionamento de Select e versão sempre que o usuário disser "Select".

Para detectar pressionamentos entre qualquer uma dessas fontes de interação, você pode manipular o evento de SourcePressed em SpatialInteractionManager em SpatialInputHandler.cpp:


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

Esse evento pressionado é enviado ao seu aplicativo de maneira assíncrona. Seu aplicativo ou o mecanismo de jogo pode desejar executar algum processamento imediatamente, ou talvez você queira colocar na fila os dados de evento em sua rotina de processamento de entrada.

O modelo inclui uma classe auxiliar para você começar. Este modelo forgoes qualquer processamento para manter a simplicidade do design. A classe auxiliar mantém o controle de se um ou mais **pressionado** eventos ocorridos desde a última **atualização** chamar. De SpatialInputHandler.cpp:




```cpp
void SpatialInputHandler::OnSourcePressed(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    m_sourceState = args->State;
    
    //
    // TODO: In your app or game engine, rewrite this method to queue
    //       input events in your input class or event handler.
    //
}
```

Se Sim, ele retorna o [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) para o evento de entrada mais recente durante a próxima atualização. De SpatialInputHandler.cpp:




```cpp
// Checks if the user performed an input gesture since the last call to this method.
// Allows the main update loop to check for asynchronous changes to the user
// input state.
SpatialInteractionSourceState^ SpatialInputHandler::CheckForInput()
{
    SpatialInteractionSourceState^ sourceState = m_sourceState;
    m_sourceState = nullptr;
    return sourceState;
}
```

Observe que o código acima tratará todos pressiona da mesma forma, se o usuário executa um primário **selecionar** pressione ou secundárias **Menu** ou **segure** pressione. O **selecionar** pressione é uma forma principal de interação com suporte em mãos, movimento controladores e voz, disparado por uma mão executando um toque de ar, um controlador de movimento com o primário gatilho/botão é pressionado ou o usuário voz dizendo "Select". Selecionados pressionamentos representam a intenção do usuário para ativar o holograma que eles destinados.

Ponderar sobre qual tipo de pressionamento está ocorrendo, modificaremos o manipulador de eventos SpatialInteractionManager::SourceUpdated. Nosso código detectará pressionamentos de compreensão (quando disponível) e usá-los para reposicionar o cubo. Se não houver uma melhor compreensão, usaremos pressionamentos de Select em vez disso.

Adicione as seguintes declarações de membro privado para SpatialInputHandler.h: 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

Abra SpatialInputHandler.cpp. Adicione o seguinte registro de evento para o construtor: 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

Isso é o código de manipulador de eventos. Se a fonte de entrada é tendo uma melhor compreensão, pose o ponteiro será armazenado para o próximo loop de atualização. Caso contrário, ele verificará se há um pressionamento de Select em vez disso. De SpatialInputHandler.cpp:




```cpp
void SpatialInputHandler::OnSourceUpdated(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    if (args->State->Source->IsGraspSupported)
    {
        if (args->State->IsGrasped)
        {
            m_sourceState = args->State;
        }
    }
    else
    {
        if (args->State->IsSelectPressed)
        {
            m_sourceState = args->State;
        }
    }
}
```

Certifique-se de cancelar o registro do manipulador de eventos no destruidor. De SpatialInputHandler.cpp:


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

Recompilar e reimplantar. Seu projeto de modelo agora deve ser capaz de reconhecer as interações de compreensão para reposicionar o cubo giratório.

A API SpatialInteractionSource dá suporte a controladores com uma ampla variedade de recursos. No exemplo mostrado acima, verificamos para ver se compreensão tem suporte antes de tentar usá-lo. O SpatialInteractionSource suporta os seguintes recursos opcionais além do comum **selecionar** pressione:
* **Botão de menu:** Verifique o suporte inspecionando a propriedade IsMenuSupported. Quando houver suporte, verifique as [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) propriedade para descobrir se o botão de menu for pressionada.
* **Segure o botão:** Verifique o suporte inspecionando a propriedade IsGraspSupported. Quando houver suporte, verifique as [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) propriedade para descobrir se compreensão é ativado.

Para controladores, o SpatialInteractionSource tem uma propriedade de controlador com recursos adicionais.
* **HasThumbstick:** Se for true, o controlador tem um analógico. Inspecione o [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) propriedade do SpatialInteractionSourceState para adquirir o analógico x e y de valores (ThumbstickX e ThumbstickY), bem como seu estado pressionado (IsThumbstickPressed).
* **HasTouchpad:** Se for true, o controlador tem um touchpad. Inspecionar a propriedade ControllerProperties do SpatialInteractionSourceState para adquirir o touchpad x e y valores (TouchpadX e TouchpadY), bem como para saber se o usuário toca o teclado (IsTouchpadTouched) e se eles estão nos pressionando o touchpad para baixo ( IsTouchpadPressed).
* **SimpleHapticsController:** A API SimpleHapticsController para o controlador permite que você inspecione as capacidades de haptics do controlador, e ele também permite que você controle os comentários hápticos.

Observe que o intervalo para touchpad e direcional de -1 para 1 para ambos os eixos (de baixo para cima e da esquerda para direita). O intervalo para o gatilho analógico, que pode é acessado usando a propriedade SpatialInteractionSourceState::SelectPressedValue, tem um intervalo de 0 a 1. Um valor de 1 correlaciona com IsSelectPressed sendo igual a true; qualquer outro valor se correlaciona com IsSelectPressed sendo igual a false.

Observe que, para uma mão e um controlador, usar SpatialInteractionSourceState::Properties::TryGetLocation fornecerá a posição do usuário mão - isso é diferente da pose de ponteiro que representa o raio de apontador do controlador. Se você quiser desenhar algo no local disponível, use TryGetLocation. Se você quiser raycast da ponta do controlador, obtenha o raio de apontador de TryGetInteractionSourcePose sobre o SpatialPointerPose.

Você também pode usar os outros eventos no SpatialInteractionManager como SourceDetected e SourceLost, para reagir quando mãos entrar ou saiam de exibição do dispositivo ou quando eles movem ou recusar a posição de pronta (dedo gerado com palm para frente), ou quando o motion controladores são ativados ou desativado ou estão emparelhados/não emparelhado.

### <a name="grip-pose-vs-pointing-pose"></a>Alça pose versus pose apontador

Realidade mista do Windows oferece suporte a controladores de movimento em uma variedade de fatores forma, com o design de cada controlador difere em sua relação entre a posição do usuário mão e natural "encaminhar" direção que aplicativos deve usar para apontando ao renderizar o controlador.

Para melhor representar esses controladores, há dois tipos de poses, que você pode investigar para cada fonte de interação:
* O **alça pose**, que representa o local de palma da mão detectada por um HoloLens ou palma mantendo um controlador de animação.
    * Em fones imersivos em exposição, essa pose é melhor usado para renderizar **mão do usuário** ou **um objeto é mantido em mãos do usuário**, como uma espada ou elétrons.
    * O **segure posição**: O centroide de palm pressionando o controlador naturalmente, ajustado esquerda ou direita para centralizar a posição dentro a alça.
    * O **Segure o eixo à direita da orientação**: Quando você abre completamente sua mão para formar uma dedo simples 5 pose, raio que é normal para o palm (para a frente da esquerda palm, com versões anteriores do palm à direita)
    * O **Segure o eixo de encaminhamento da orientação**: Quando você fecha sua mão parcialmente (como se que mantém o controlador), o raio que aponta "forward" por meio de tubo formado por seus dedos não thumb.
    * O **segure orientação backup eixo**: O eixo de cima indicado pelas definições de direito e Avançar.
    * Você pode acessar a pose alça por meio de [SpatialInteractionSourceState.Properties.TryGetLocation(...) ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).
* O **ponteiro pose**, que representa a dica do controlador que aponta para a frente.
    * Essa pose é melhor usado para raycast quando **apontando para a interface do usuário** quando você está renderizando o próprio modelo de controlador.
    * Você pode acessar a pose ponteiro por meio de [SpatialInteractionSourceState.Properties.TryGetLocation(...). SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) ou [SpatialInteractionSourceState.TryGetPointerPose(...). TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

### <a name="composite-gestures-spatialgesturerecognizer"></a>Gestos de composição: SpatialGestureRecognizer

Um [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interpreta interações do usuário de mãos, controladores de movimento e o comando de voz "Selecionar" para eventos de gesto espacial superfície, qual destino de usuários usando seu olhar principal.

Gestos espaciais são uma forma de chave de entrada para aplicativos de realidade mista do Windows. Ao roteamentos interações do SpatialInteractionManager para SpatialGestureRecognizer de um holograma, aplicativos podem detectar eventos de toque, espera, manipulação e navegação uniformemente em mãos, voz e dispositivos de entrada espaciais, sem a necessidade que tratar pressionamentos de e libera manualmente.

SpatialGestureRecognizer executa somente a Desambiguidade mínimo entre o conjunto de gestos de que você solicitar. Por exemplo, se você solicitar apenas toque, o usuário pode pressionada seu dedo, desde que eles gostam e um toque ainda ocorrerá. Se você solicitar o toque e mantenha, após cerca de um segundo de mantendo seu dedo, o gesto promoverá a uma isenção e um toque não ocorrerão mais.

Para usar SpatialGestureRecognizer, lidar com o SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) eventos e captura o SpatialPointerPose exposto lá. Use ray de olhar principal do usuário dessa pose para ter interseção com as hologramas e superfície malhas no ambiente do usuário, para determinar o que o usuário pretende interagir com. Em seguida, encaminhar o SpatialInteraction nos argumentos de evento para SpatialGestureRecognizer do holograma de destino, usando seus [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) método. Isso inicia a interpretação de interação de acordo com o [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) definir esse reconhecedor no momento da criação - ou pelo [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

Em HoloLens, interações e gestos geralmente devem derivar seu direcionamento de olhar de principal do usuário, em vez de tentar renderizar ou interagir diretamente no local da mão. Após o início de uma interação relativos movimentos da mão podem ser usados para controlar o gesto, assim como acontece com o gesto de manipulação ou navegação.

## <a name="see-also"></a>Consulte também
* [Gaze](gaze.md)
* [Gestos](gestures.md)
* [Controladores de movimento](motion-controllers.md)
