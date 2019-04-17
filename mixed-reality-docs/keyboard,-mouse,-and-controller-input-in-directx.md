---
title: Teclado, mouse e entrada do controlador em DirectX
description: Explica como criar um aplicativo para Windows Mixed Reality que usa o teclado, mouse e controladores de jogos.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, teclado, mouse, controlador de jogo, controlador do xbox, HoloLens, área de trabalho, passo a passo, código de exemplo
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591017"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Teclado, mouse e entrada do controlador em DirectX

Teclados, mouses e controladores de jogos podem ser útil formulários de entrada para dispositivos de realidade mista do Windows. Mouses e teclados Bluetooth têm suporte no HoloLens, para uso com a depuração de seu aplicativo ou como uma forma alternativa de entrada. Realidade mista do Windows também dá suporte a fones imersivos em exposição anexados aos PCs - onde controladores de jogos, teclados e mouses têm sido historicamente a norma.

Para usar a entrada do teclado em HoloLens, par um teclado Bluetooth em seu dispositivo ou usar a entrada virtual via o Windows Device Portal. Para usar a entrada do teclado ao uso de um fone de ouvido imersivo Windows Mixed Reality, atribua o foco de entrada para a realidade misturada colocando no dispositivo ou usando a tecla Windows + Y combinação de teclado. Tenha em mente que os aplicativos destinados para HoloLens devem fornecer a funcionalidade sem esses dispositivos conectados.

>[!NOTE]
>Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.

## <a name="subscribe-for-corewindow-input-events"></a>Inscrever-se para eventos de entrada CoreWindow

### <a name="keyboard-input"></a>Entrada por teclado

O modelo de aplicativo do Windows Holographic, incluímos um manipulador de eventos para entrada de teclado, assim como qualquer outro aplicativo UWP. Seu aplicativo consome dados de entrada de teclado da mesma maneira que na realidade mista do Windows.

De AppView.cpp:

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a>Entrada do teclado virtual
Para imersivos fones de ouvido da área de trabalho, você também pode dar suporte virtuais teclados processados pelo Windows sobre o modo de exibição envolvente. Para dar suporte a isso, seu aplicativo pode implementar **CoreTextEditContext**. Isso permite que o Windows entender o estado de suas próprias caixas de texto renderizado pelo aplicativo, portanto, corretamente pode contribuir com o teclado virtual existe no texto.

Para obter mais informações sobre como implementar CoreTextEditContext suporte, consulte o [CoreTextEditContext exemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Entrada do mouse

Você também pode usar a entrada do mouse, novamente por meio de manipuladores de evento de entrada de UWP CoreWindow. Aqui está como modificar o modelo de aplicativo do Windows Holographic para dar suporte a cliques do mouse na forma como pressionados gestos do mesmos. Depois de fazer essa modificação, um clique do mouse durante o uso de um dispositivo de imersão fone de ouvido será reposicionar o cubo.

Observe que os aplicativos UWP também podem obter dados brutos de XY do mouse usando o [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.

Comece declarando um novo manipulador de OnPointerPressed AppView.h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

No AppView.cpp, adicione este código ao SetWindow:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

Em seguida, coloque essa definição para OnPointerPressed na parte inferior do arquivo:

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

O manipulador de eventos que acabamos de adicionar é uma passagem para a classe de modelo principal. Vamos modificar a classe principal para dar suporte a essa passagem. Adicione esta declaração de método público para o arquivo de cabeçalho:

```
// Handle mouse input.
       void OnPointerPressed();
```

Essa variável de membro privado, também será necessário:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Por fim, atualizaremos a classe principal com a nova lógica para dar suporte a cliques do mouse. Comece adicionando este manipulador de eventos. Certifique-se de atualizar o nome da classe:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

Agora, o método de atualização, substitua a lógica existente para obter uma pose ponteiro com este:

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Recompilar e reimplantar. Você deve observar que o clique do mouse agora reposicionar o cubo no HoloLens ou fone de ouvido imersivo - com o mouse bluetooth anexado.

### <a name="game-controller-support"></a>Suporte de controlador de jogo

Controladores de jogos podem ser uma forma divertida e conveniente de permitir que o usuário para controlar uma experiência imersiva de realidade mista do Windows.

É a primeira etapa para adicionar suporte para controladores de jogos para o modelo de aplicativo do Windows Holographic adicionar as seguintes declarações de membro privado para a classe de cabeçalho para seu arquivo principal:

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

Inicialize eventos gamepad e qualquer gamepads conectados no momento, no construtor para sua classe principal:

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

Adicione esses manipuladores de eventos à sua classe principal. Certifique-se de atualizar o nome da classe:

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

Por fim, atualize a lógica para reconhecer as alterações no estado do controlador de entrada. Aqui, usamos a mesma variável m_pointerPressed discutida na seção acima para adicionar eventos de mouse. Adicione isso para o método de atualização, antes de onde ele procurará o SpatialPointerPose:

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Não se esqueça de cancelar o registro de eventos ao limpar a classe principal:

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

Recompilar e reimplantar. Agora você pode anexar, ou emparelhar um controlador de jogo e usá-lo para reposicionar o cubo giratório.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Diretrizes importantes para entrada de mouse e teclado

Há algumas das principais diferenças em como esse código pode ser usado no Microsoft HoloLens – que é um dispositivo que se baseia principalmente na entrada do usuário natural – versus o que está disponível em um PC Windows Mixed Reality habilitado.
* Você não pode confiar no teclado ou mouse de entrada esteja presente. Toda a funcionalidade do seu aplicativo deve trabalhar com olhar, gesto e entrada de fala.
* Quando estiver anexado a um teclado Bluetooth, pode ser útil habilitar a entrada do teclado para qualquer texto que seu aplicativo pode solicitar. Isso pode ser um ótimo complemento para ditado, por exemplo.
* Quando se trata de criação de seu aplicativo, não confie em WASD (por exemplo) e mouse procurar controles para o seu jogo. HoloLens é projetado para o usuário sair andando na sala. Nesse caso, o usuário controla diretamente a câmera. Uma interface para impulsionar a câmera em torno da sala com controles de mover/aparência não fornece a mesma experiência.
* Entrada do teclado pode ser uma excelente maneira de controlar os aspectos de depuração do seu aplicativo ou o mecanismo de jogo, especialmente porque o usuário não precisará usar o teclado. Conectando-é o mesmo, que você está acostumado, com APIs de eventos do CoreWindow. Nesse cenário, você pode optar por implementar uma maneira de configurar seu aplicativo para eventos de teclado de rota para um modo de "debug somente entrada" durante as sessões de depuração.
* Controladores de Bluetooth funcionam bem.

## <a name="see-also"></a>Consulte também
* [Acessórios de hardware](hardware-accessories.md)
