---
title: Entrada de teclado, mouse e controlador no DirectX
description: Explica como criar um aplicativo para a realidade mista do Windows que usa controladores de teclado, mouse e jogo.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, teclado, mouse, Game Controller, Xbox Controller, HoloLens, desktop, passo a passos, código de exemplo
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835092"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="fbd19-104">Entrada de teclado, mouse e controlador no DirectX</span><span class="sxs-lookup"><span data-stu-id="fbd19-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="fbd19-105">Teclados, mouses e controladores de jogos podem ser formas úteis de entrada para dispositivos Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="fbd19-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="fbd19-106">Os teclados e os mouses Bluetooth têm suporte no HoloLens, para uso com a depuração do aplicativo ou como uma forma alternativa de entrada.</span><span class="sxs-lookup"><span data-stu-id="fbd19-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="fbd19-107">A realidade mista do Windows também dá suporte a headsets de imersão conectadas a PCs – onde os mouses, teclados e controladores de jogos têm sido historicamente a norma.</span><span class="sxs-lookup"><span data-stu-id="fbd19-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="fbd19-108">Para usar a entrada de teclado no HoloLens, Emparelhe um teclado Bluetooth para seu dispositivo ou use a entrada virtual por meio do portal de dispositivo do Windows.</span><span class="sxs-lookup"><span data-stu-id="fbd19-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="fbd19-109">Para usar a entrada de teclado ao utilizar um headset de imersão de realidade mista do Windows, atribua o foco de entrada à realidade mista, colocando no dispositivo ou usando a combinação de teclas do Windows + Y.</span><span class="sxs-lookup"><span data-stu-id="fbd19-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="fbd19-110">Tenha em mente que os aplicativos destinados ao HoloLens devem fornecer funcionalidade sem esses dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="fbd19-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="fbd19-111">Os trechos de código neste artigo demonstram atualmente o C++uso de/CX em vez de/WinRT em C++conformidade com C + +17, conforme usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="fbd19-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="fbd19-112">Os conceitos são equivalentes a C++um projeto/WinRT, embora você precise converter o código.</span><span class="sxs-lookup"><span data-stu-id="fbd19-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="fbd19-113">Assinar eventos de entrada do CoreWindow</span><span class="sxs-lookup"><span data-stu-id="fbd19-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="fbd19-114">Entrada por teclado</span><span class="sxs-lookup"><span data-stu-id="fbd19-114">Keyboard input</span></span>

<span data-ttu-id="fbd19-115">No modelo de aplicativo Holographic do Windows, incluímos um manipulador de eventos para entrada de teclado, assim como qualquer outro aplicativo UWP.</span><span class="sxs-lookup"><span data-stu-id="fbd19-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="fbd19-116">Seu aplicativo consome dados de entrada de teclado da mesma maneira no Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="fbd19-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="fbd19-117">De AppView. cpp:</span><span class="sxs-lookup"><span data-stu-id="fbd19-117">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="fbd19-118">Entrada de teclado virtual</span><span class="sxs-lookup"><span data-stu-id="fbd19-118">Virtual keyboard input</span></span>
<span data-ttu-id="fbd19-119">Para headsets de área de trabalho de imersão, você também pode dar suporte a teclados virtuais renderizados pelo Windows sobre sua exibição de imersão.</span><span class="sxs-lookup"><span data-stu-id="fbd19-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="fbd19-120">Para dar suporte a isso, seu aplicativo pode implementar o **CoreTextEditContext**.</span><span class="sxs-lookup"><span data-stu-id="fbd19-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="fbd19-121">Isso permite que o Windows entenda o estado de suas próprias caixas de texto renderizadas pelo aplicativo, de modo que o teclado virtual possa contribuir corretamente para o texto lá.</span><span class="sxs-lookup"><span data-stu-id="fbd19-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="fbd19-122">Para obter mais informações sobre como implementar o suporte a CoreTextEditContext, consulte o [exemplo CoreTextEditContext](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="fbd19-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="fbd19-123">Entrada do mouse</span><span class="sxs-lookup"><span data-stu-id="fbd19-123">Mouse Input</span></span>

<span data-ttu-id="fbd19-124">Você também pode usar a entrada do mouse, novamente por meio dos manipuladores de eventos de entrada UWP CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="fbd19-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="fbd19-125">Aqui está como modificar o modelo de aplicativo Holographic do Windows para dar suporte a cliques do mouse da mesma maneira que os gestos pressionados.</span><span class="sxs-lookup"><span data-stu-id="fbd19-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="fbd19-126">Depois de fazer essa modificação, um clique do mouse ao usar um dispositivo de headset de imersão reposicionará o cubo.</span><span class="sxs-lookup"><span data-stu-id="fbd19-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="fbd19-127">Observe que os aplicativos UWP também podem obter dados XY brutos para o mouse usando a API [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) .</span><span class="sxs-lookup"><span data-stu-id="fbd19-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="fbd19-128">Comece declarando um novo manipulador OnPointerPressed em AppView. h:</span><span class="sxs-lookup"><span data-stu-id="fbd19-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="fbd19-129">Em AppView. cpp, adicione este código a SetWindow:</span><span class="sxs-lookup"><span data-stu-id="fbd19-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="fbd19-130">Em seguida, coloque essa definição para OnPointerPressed na parte inferior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="fbd19-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="fbd19-131">O manipulador de eventos que acabamos de adicionar é uma passagem para a classe principal do modelo.</span><span class="sxs-lookup"><span data-stu-id="fbd19-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="fbd19-132">Vamos modificar a classe principal para dar suporte a essa passagem.</span><span class="sxs-lookup"><span data-stu-id="fbd19-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="fbd19-133">Adicione essa declaração de método público ao arquivo de cabeçalho:</span><span class="sxs-lookup"><span data-stu-id="fbd19-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="fbd19-134">Você também precisará dessa variável de membro privado:</span><span class="sxs-lookup"><span data-stu-id="fbd19-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="fbd19-135">Por fim, atualizaremos a classe principal com nova lógica para dar suporte a cliques do mouse.</span><span class="sxs-lookup"><span data-stu-id="fbd19-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="fbd19-136">Comece adicionando este manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="fbd19-136">Start by adding this event handler.</span></span> <span data-ttu-id="fbd19-137">Certifique-se de atualizar o nome da classe:</span><span class="sxs-lookup"><span data-stu-id="fbd19-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="fbd19-138">Agora, no método Update, substitua a lógica existente para obter uma pose de ponteiro com esta:</span><span class="sxs-lookup"><span data-stu-id="fbd19-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="fbd19-139">Recompile e reimplante.</span><span class="sxs-lookup"><span data-stu-id="fbd19-139">Recompile and redeploy.</span></span> <span data-ttu-id="fbd19-140">Você deve observar que o clique do mouse agora reposicionará o cubo no headset de imersão ou no HoloLens com o mouse Bluetooth anexado.</span><span class="sxs-lookup"><span data-stu-id="fbd19-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="fbd19-141">Suporte ao controlador de jogos</span><span class="sxs-lookup"><span data-stu-id="fbd19-141">Game controller support</span></span>

<span data-ttu-id="fbd19-142">Os controladores de jogo podem ser uma maneira divertida e conveniente de permitir que o usuário controle uma experiência de realidade do Windows Mixed realm.</span><span class="sxs-lookup"><span data-stu-id="fbd19-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="fbd19-143">A primeira etapa para adicionar suporte a controladores de jogos ao modelo de aplicativo Holographic do Windows é adicionar as seguintes declarações de membro privado à classe de cabeçalho para o arquivo principal:</span><span class="sxs-lookup"><span data-stu-id="fbd19-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="fbd19-144">Inicializar eventos do gamepad e todos os gamepads que estão anexados no momento, no construtor para sua classe principal:</span><span class="sxs-lookup"><span data-stu-id="fbd19-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="fbd19-145">Adicione esses manipuladores de eventos à classe principal.</span><span class="sxs-lookup"><span data-stu-id="fbd19-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="fbd19-146">Certifique-se de atualizar o nome da classe:</span><span class="sxs-lookup"><span data-stu-id="fbd19-146">Make sure to update the class name:</span></span>

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

<span data-ttu-id="fbd19-147">Por fim, atualize a lógica de entrada para reconhecer as alterações no estado do controlador.</span><span class="sxs-lookup"><span data-stu-id="fbd19-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="fbd19-148">Aqui, usamos a mesma variável m_pointerPressed discutida na seção acima para adicionar eventos de mouse.</span><span class="sxs-lookup"><span data-stu-id="fbd19-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="fbd19-149">Adicione isso ao método Update, pouco antes de onde ele verifica o SpatialPointerPose:</span><span class="sxs-lookup"><span data-stu-id="fbd19-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="fbd19-150">Não se esqueça de cancelar o registro dos eventos ao limpar a classe principal:</span><span class="sxs-lookup"><span data-stu-id="fbd19-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="fbd19-151">Recompile e reimplante.</span><span class="sxs-lookup"><span data-stu-id="fbd19-151">Recompile, and redeploy.</span></span> <span data-ttu-id="fbd19-152">Agora você pode anexar ou emparelhar um controlador de jogo e usá-lo para reposicionar o cubo de rotação.</span><span class="sxs-lookup"><span data-stu-id="fbd19-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="fbd19-153">Diretrizes importantes para entrada de teclado e mouse</span><span class="sxs-lookup"><span data-stu-id="fbd19-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="fbd19-154">Há algumas diferenças importantes em como esse código pode ser usado no Microsoft HoloLens – que é um dispositivo que depende principalmente da entrada natural do usuário – em comparação com o que está disponível em um PC com o Windows Mixed Reality habilitado.</span><span class="sxs-lookup"><span data-stu-id="fbd19-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="fbd19-155">Você não pode contar com o teclado ou a entrada do mouse para estar presente.</span><span class="sxs-lookup"><span data-stu-id="fbd19-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="fbd19-156">Toda a funcionalidade do seu aplicativo deve funcionar com olhar, gesto e entrada de fala.</span><span class="sxs-lookup"><span data-stu-id="fbd19-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="fbd19-157">Quando um teclado Bluetooth é anexado, pode ser útil habilitar a entrada de teclado para qualquer texto que seu aplicativo possa solicitar.</span><span class="sxs-lookup"><span data-stu-id="fbd19-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="fbd19-158">Isso pode ser um excelente suplemento para ditado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="fbd19-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="fbd19-159">Quando se trata de criar seu aplicativo, não confie (por exemplo) WASD e controles de aparência do mouse para seu jogo.</span><span class="sxs-lookup"><span data-stu-id="fbd19-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="fbd19-160">O HoloLens foi projetado para que o usuário percorra a sala.</span><span class="sxs-lookup"><span data-stu-id="fbd19-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="fbd19-161">Nesse caso, o usuário controla a câmera diretamente.</span><span class="sxs-lookup"><span data-stu-id="fbd19-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="fbd19-162">Uma interface para orientar a câmera em todo o espaço com os controles mover/procurar não fornecerá a mesma experiência.</span><span class="sxs-lookup"><span data-stu-id="fbd19-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="fbd19-163">A entrada de teclado pode ser uma maneira excelente de controlar os aspectos de depuração do seu aplicativo ou do seu mecanismo de jogo, especialmente, uma vez que o usuário não será solicitado a usar o teclado.</span><span class="sxs-lookup"><span data-stu-id="fbd19-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="fbd19-164">Conectar-se a ele é o mesmo que você está acostumado a, com APIs de evento CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="fbd19-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="fbd19-165">Nesse cenário, você pode optar por implementar uma maneira de configurar seu aplicativo para rotear eventos de teclado para um modo de "somente entrada de depuração" durante as sessões de depuração.</span><span class="sxs-lookup"><span data-stu-id="fbd19-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="fbd19-166">Controladores Bluetooth também funcionam.</span><span class="sxs-lookup"><span data-stu-id="fbd19-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbd19-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbd19-167">See also</span></span>
* [<span data-ttu-id="fbd19-168">Acessórios de hardware</span><span class="sxs-lookup"><span data-stu-id="fbd19-168">Hardware accessories</span></span>](hardware-accessories.md)
