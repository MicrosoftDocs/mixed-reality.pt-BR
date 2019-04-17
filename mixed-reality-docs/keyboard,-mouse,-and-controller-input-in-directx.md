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
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="8cd9d-104">Teclado, mouse e entrada do controlador em DirectX</span><span class="sxs-lookup"><span data-stu-id="8cd9d-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="8cd9d-105">Teclados, mouses e controladores de jogos podem ser útil formulários de entrada para dispositivos de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="8cd9d-106">Mouses e teclados Bluetooth têm suporte no HoloLens, para uso com a depuração de seu aplicativo ou como uma forma alternativa de entrada.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="8cd9d-107">Realidade mista do Windows também dá suporte a fones imersivos em exposição anexados aos PCs - onde controladores de jogos, teclados e mouses têm sido historicamente a norma.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="8cd9d-108">Para usar a entrada do teclado em HoloLens, par um teclado Bluetooth em seu dispositivo ou usar a entrada virtual via o Windows Device Portal.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="8cd9d-109">Para usar a entrada do teclado ao uso de um fone de ouvido imersivo Windows Mixed Reality, atribua o foco de entrada para a realidade misturada colocando no dispositivo ou usando a tecla Windows + Y combinação de teclado.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="8cd9d-110">Tenha em mente que os aplicativos destinados para HoloLens devem fornecer a funcionalidade sem esses dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="8cd9d-111">Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="8cd9d-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="8cd9d-112">Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="8cd9d-113">Inscrever-se para eventos de entrada CoreWindow</span><span class="sxs-lookup"><span data-stu-id="8cd9d-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="8cd9d-114">Entrada por teclado</span><span class="sxs-lookup"><span data-stu-id="8cd9d-114">Keyboard input</span></span>

<span data-ttu-id="8cd9d-115">O modelo de aplicativo do Windows Holographic, incluímos um manipulador de eventos para entrada de teclado, assim como qualquer outro aplicativo UWP.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="8cd9d-116">Seu aplicativo consome dados de entrada de teclado da mesma maneira que na realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="8cd9d-117">De AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-117">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="8cd9d-118">Entrada do teclado virtual</span><span class="sxs-lookup"><span data-stu-id="8cd9d-118">Virtual keyboard input</span></span>
<span data-ttu-id="8cd9d-119">Para imersivos fones de ouvido da área de trabalho, você também pode dar suporte virtuais teclados processados pelo Windows sobre o modo de exibição envolvente.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="8cd9d-120">Para dar suporte a isso, seu aplicativo pode implementar **CoreTextEditContext**.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="8cd9d-121">Isso permite que o Windows entender o estado de suas próprias caixas de texto renderizado pelo aplicativo, portanto, corretamente pode contribuir com o teclado virtual existe no texto.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="8cd9d-122">Para obter mais informações sobre como implementar CoreTextEditContext suporte, consulte o [CoreTextEditContext exemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="8cd9d-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="8cd9d-123">Entrada do mouse</span><span class="sxs-lookup"><span data-stu-id="8cd9d-123">Mouse Input</span></span>

<span data-ttu-id="8cd9d-124">Você também pode usar a entrada do mouse, novamente por meio de manipuladores de evento de entrada de UWP CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="8cd9d-125">Aqui está como modificar o modelo de aplicativo do Windows Holographic para dar suporte a cliques do mouse na forma como pressionados gestos do mesmos.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="8cd9d-126">Depois de fazer essa modificação, um clique do mouse durante o uso de um dispositivo de imersão fone de ouvido será reposicionar o cubo.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="8cd9d-127">Observe que os aplicativos UWP também podem obter dados brutos de XY do mouse usando o [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="8cd9d-128">Comece declarando um novo manipulador de OnPointerPressed AppView.h:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="8cd9d-129">No AppView.cpp, adicione este código ao SetWindow:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="8cd9d-130">Em seguida, coloque essa definição para OnPointerPressed na parte inferior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="8cd9d-131">O manipulador de eventos que acabamos de adicionar é uma passagem para a classe de modelo principal.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="8cd9d-132">Vamos modificar a classe principal para dar suporte a essa passagem.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="8cd9d-133">Adicione esta declaração de método público para o arquivo de cabeçalho:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="8cd9d-134">Essa variável de membro privado, também será necessário:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="8cd9d-135">Por fim, atualizaremos a classe principal com a nova lógica para dar suporte a cliques do mouse.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="8cd9d-136">Comece adicionando este manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-136">Start by adding this event handler.</span></span> <span data-ttu-id="8cd9d-137">Certifique-se de atualizar o nome da classe:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="8cd9d-138">Agora, o método de atualização, substitua a lógica existente para obter uma pose ponteiro com este:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="8cd9d-139">Recompilar e reimplantar.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-139">Recompile and redeploy.</span></span> <span data-ttu-id="8cd9d-140">Você deve observar que o clique do mouse agora reposicionar o cubo no HoloLens ou fone de ouvido imersivo - com o mouse bluetooth anexado.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="8cd9d-141">Suporte de controlador de jogo</span><span class="sxs-lookup"><span data-stu-id="8cd9d-141">Game controller support</span></span>

<span data-ttu-id="8cd9d-142">Controladores de jogos podem ser uma forma divertida e conveniente de permitir que o usuário para controlar uma experiência imersiva de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="8cd9d-143">É a primeira etapa para adicionar suporte para controladores de jogos para o modelo de aplicativo do Windows Holographic adicionar as seguintes declarações de membro privado para a classe de cabeçalho para seu arquivo principal:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="8cd9d-144">Inicialize eventos gamepad e qualquer gamepads conectados no momento, no construtor para sua classe principal:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="8cd9d-145">Adicione esses manipuladores de eventos à sua classe principal.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="8cd9d-146">Certifique-se de atualizar o nome da classe:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-146">Make sure to update the class name:</span></span>

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

<span data-ttu-id="8cd9d-147">Por fim, atualize a lógica para reconhecer as alterações no estado do controlador de entrada.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="8cd9d-148">Aqui, usamos a mesma variável m_pointerPressed discutida na seção acima para adicionar eventos de mouse.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="8cd9d-149">Adicione isso para o método de atualização, antes de onde ele procurará o SpatialPointerPose:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="8cd9d-150">Não se esqueça de cancelar o registro de eventos ao limpar a classe principal:</span><span class="sxs-lookup"><span data-stu-id="8cd9d-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="8cd9d-151">Recompilar e reimplantar.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-151">Recompile, and redeploy.</span></span> <span data-ttu-id="8cd9d-152">Agora você pode anexar, ou emparelhar um controlador de jogo e usá-lo para reposicionar o cubo giratório.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="8cd9d-153">Diretrizes importantes para entrada de mouse e teclado</span><span class="sxs-lookup"><span data-stu-id="8cd9d-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="8cd9d-154">Há algumas das principais diferenças em como esse código pode ser usado no Microsoft HoloLens – que é um dispositivo que se baseia principalmente na entrada do usuário natural – versus o que está disponível em um PC Windows Mixed Reality habilitado.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="8cd9d-155">Você não pode confiar no teclado ou mouse de entrada esteja presente.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="8cd9d-156">Toda a funcionalidade do seu aplicativo deve trabalhar com olhar, gesto e entrada de fala.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="8cd9d-157">Quando estiver anexado a um teclado Bluetooth, pode ser útil habilitar a entrada do teclado para qualquer texto que seu aplicativo pode solicitar.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="8cd9d-158">Isso pode ser um ótimo complemento para ditado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="8cd9d-159">Quando se trata de criação de seu aplicativo, não confie em WASD (por exemplo) e mouse procurar controles para o seu jogo.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="8cd9d-160">HoloLens é projetado para o usuário sair andando na sala.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="8cd9d-161">Nesse caso, o usuário controla diretamente a câmera.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="8cd9d-162">Uma interface para impulsionar a câmera em torno da sala com controles de mover/aparência não fornece a mesma experiência.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="8cd9d-163">Entrada do teclado pode ser uma excelente maneira de controlar os aspectos de depuração do seu aplicativo ou o mecanismo de jogo, especialmente porque o usuário não precisará usar o teclado.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="8cd9d-164">Conectando-é o mesmo, que você está acostumado, com APIs de eventos do CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="8cd9d-165">Nesse cenário, você pode optar por implementar uma maneira de configurar seu aplicativo para eventos de teclado de rota para um modo de "debug somente entrada" durante as sessões de depuração.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="8cd9d-166">Controladores de Bluetooth funcionam bem.</span><span class="sxs-lookup"><span data-stu-id="8cd9d-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cd9d-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8cd9d-167">See also</span></span>
* [<span data-ttu-id="8cd9d-168">Acessórios de hardware</span><span class="sxs-lookup"><span data-stu-id="8cd9d-168">Hardware accessories</span></span>](hardware-accessories.md)
