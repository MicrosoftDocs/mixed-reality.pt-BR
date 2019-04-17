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
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a><span data-ttu-id="5aa2c-104">Olhar, gestos e controladores de movimento no DirectX</span><span class="sxs-lookup"><span data-stu-id="5aa2c-104">Gaze, gestures, and motion controllers in DirectX</span></span>

<span data-ttu-id="5aa2c-105">Se você pretende criar diretamente sobre a plataforma, você terá que lidar com a entrada proveniente do usuário – como onde o usuário está procurando por meio [olhar principal](gaze.md) e o que o usuário selecionou com [gestos](gestures.md) ou [controladores de movimento](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="5aa2c-105">If you're going to build directly on top of the platform, you will have to handle input coming from the user - such as where the user is looking via [head gaze](gaze.md) and what the user has selected with [gestures](gestures.md) or [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="5aa2c-106">Combinando esses formulários de entrada, você pode permitir que um usuário colocar uma [holograma](hologram.md) em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-106">Combining these forms of input, you can enable a user to place a [hologram](hologram.md) in your app.</span></span> <span data-ttu-id="5aa2c-107">O [modelo de aplicativo holográfica](creating-a-holographic-directx-project.md) tem um exemplo de fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-107">The [holographic app template](creating-a-holographic-directx-project.md) has an easy to use example.</span></span>

>[!NOTE]
><span data-ttu-id="5aa2c-108">Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="5aa2c-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="5aa2c-109">Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="gaze-input"></a><span data-ttu-id="5aa2c-110">Entrada com foco</span><span class="sxs-lookup"><span data-stu-id="5aa2c-110">Gaze input</span></span>

<span data-ttu-id="5aa2c-111">Para acessar o usuário [olhar principal](gaze.md), você usa o [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) tipo.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-111">To access the user's [head gaze](gaze.md), you use the [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) type.</span></span> <span data-ttu-id="5aa2c-112">O modelo de aplicativo holográfica inclui código básico para olhar compreensão.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-112">The holographic app template includes basic code for understanding gaze.</span></span> <span data-ttu-id="5aa2c-113">Esse código fornece um vetor que aponta para a frente entre a atenção do usuário, levando em conta posição do dispositivo e a orientação em um determinado [sistema de coordenadas](coordinate-systems-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="5aa2c-113">This code provides a vector pointing forward from between the user's eyes, taking into account the device's position and orientation in a given [coordinate system](coordinate-systems-in-directx.md).</span></span>




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

<span data-ttu-id="5aa2c-114">Você pode achar se perguntando: "Mas, em que o sistema de coordenadas vêm do?"</span><span class="sxs-lookup"><span data-stu-id="5aa2c-114">You may find yourself asking: "But where does the coordinate system come from?"</span></span>

<span data-ttu-id="5aa2c-115">Vamos responder essa pergunta.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-115">Let's answer that question.</span></span> <span data-ttu-id="5aa2c-116">Em nosso AppMain **atualização** função, processamos um evento de entrada espacial adquirindo-lo em relação ao sistema de coordenadas para nosso StationaryFrameOfReference.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-116">In our AppMain's **Update** function, we processed a spatial input event by acquiring it relative to the coordinate system for our StationaryFrameOfReference.</span></span> <span data-ttu-id="5aa2c-117">Lembre-se de que o StationaryFrameOfReference foi criado quando configuramos o [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), e o sistema de coordenadas foi adquirido no início da [atualização](rendering-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="5aa2c-117">Recall that the StationaryFrameOfReference was created when we set up the [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), and the coordinate system was acquired at the start of [Update](rendering-in-directx.md).</span></span>




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

<span data-ttu-id="5aa2c-118">Observe que os dados estão vinculados a um estado de algum tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-118">Note that the data is tied to a pointer state of some kind.</span></span> <span data-ttu-id="5aa2c-119">Podemos obter isso de um evento de entrada espacial.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-119">We get this from a spatial input event.</span></span> <span data-ttu-id="5aa2c-120">O objeto de dados de evento inclui um sistema de coordenadas, para que você sempre pode relacionar a direção de olhar no momento do evento a qualquer sistema de coordenadas espacial, você precisa.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-120">The event data object includes a coordinate system, so that you can always relate the gaze direction at the time of the event to whatever spatial coordinate system you need.</span></span> <span data-ttu-id="5aa2c-121">Na verdade, você deve fazer isso para obter a pose de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-121">In fact, you must do so in order to get the pointer pose.</span></span>

> [!NOTE]
> <span data-ttu-id="5aa2c-122">Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="5aa2c-122">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="gesture-and-motion-controller-input"></a><span data-ttu-id="5aa2c-123">Controlador de movimento e de gesto de entrada</span><span class="sxs-lookup"><span data-stu-id="5aa2c-123">Gesture and motion controller input</span></span>

<span data-ttu-id="5aa2c-124">Na realidade mista do Windows, ambos entregar [gestos](gestures.md) e [controladores de movimento](motion-controllers.md) são tratadas por meio da mesma espacial entrada APIs, encontrada no [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) namespace.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-124">In Windows Mixed Reality, both hand [gestures](gestures.md) and [motion controllers](motion-controllers.md) are handled through the same spatial input APIs, found in the [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) namespace.</span></span> <span data-ttu-id="5aa2c-125">Isso permite que você manipule facilmente ações comuns, como **selecionar** pressiona da mesma maneira em mãos e controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-125">This enables you to easily handle common actions like **Select** presses the same way across both hands and motion controllers.</span></span>

<span data-ttu-id="5aa2c-126">Há dois níveis de API que você pode direcionar ao lidar com gestos ou controladores de movimento, na realidade mista:</span><span class="sxs-lookup"><span data-stu-id="5aa2c-126">There are two levels of API you can target when handling gestures or motion controllers in mixed reality:</span></span>
* <span data-ttu-id="5aa2c-127">[Interações](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) e [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), acessado usando um [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span><span class="sxs-lookup"><span data-stu-id="5aa2c-127">[Interactions](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) and [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), accessed using a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span></span>
* <span data-ttu-id="5aa2c-128">[Gestos de composição](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), mantenha, manipulação de navegação), acessado usando um [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span><span class="sxs-lookup"><span data-stu-id="5aa2c-128">[Composite gestures](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), Hold, Manipulation, Navigation), accessed using a [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span></span>

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a><span data-ttu-id="5aa2c-129">Selecione/Menu/compreensão/Touchpad/analógico interações: SpatialInteractionManager</span><span class="sxs-lookup"><span data-stu-id="5aa2c-129">Select/Menu/Grasp/Touchpad/Thumbstick interactions: SpatialInteractionManager</span></span>

<span data-ttu-id="5aa2c-130">Para detectar os pressionamentos de baixo nível, versões e atualizações em mãos e dispositivos de entrada no Windows Mixed Reality, você iniciar de um [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="5aa2c-130">To detect low-level presses, releases and updates across hands and input devices in Windows Mixed Reality, you start from a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span></span> <span data-ttu-id="5aa2c-131">O SpatialInteractionManager tem um evento que informa ao aplicativo quando uma mão ou controlador de movimento foi detectado entrada.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-131">The SpatialInteractionManager has an event that informs the app when a hand or motion controller has detected input.</span></span>

<span data-ttu-id="5aa2c-132">Há três tipos principais de SpatialInteractionSource, cada um representado por um valor diferente de SpatialInteractionSourceKind:</span><span class="sxs-lookup"><span data-stu-id="5aa2c-132">There are three key kinds of SpatialInteractionSource, each represented by a different SpatialInteractionSourceKind value:</span></span>
* <span data-ttu-id="5aa2c-133">**Mão** representa mão de um usuário detectado.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-133">**Hand** represents a user's detected hand.</span></span> <span data-ttu-id="5aa2c-134">Fontes de mão estão disponíveis apenas em HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-134">Hand sources are available only on HoloLens.</span></span>
* <span data-ttu-id="5aa2c-135">**Controlador** representa um controlador de movimento emparelhado.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-135">**Controller** represents a paired motion controller.</span></span> <span data-ttu-id="5aa2c-136">Controladores de movimento podem oferecer uma variedade de recursos, por exemplo: Selecione gatilhos, botões de Menu, botões de compreensão, touchpads e alavancas direcionais.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-136">Motion controllers can offer a variety of capabilities, for example: Select triggers, Menu buttons, Grasp buttons, touchpads and thumbsticks.</span></span>
* <span data-ttu-id="5aa2c-137">**Voz** representa a voz do usuário falando em palavras-chave detectados pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-137">**Voice** represents the user's voice speaking system-detected keywords.</span></span> <span data-ttu-id="5aa2c-138">Isso será injetar um pressionamento de Select e versão sempre que o usuário disser "Select".</span><span class="sxs-lookup"><span data-stu-id="5aa2c-138">This will inject a Select press and release whenever the user says "Select".</span></span>

<span data-ttu-id="5aa2c-139">Para detectar pressionamentos entre qualquer uma dessas fontes de interação, você pode manipular o evento de SourcePressed em SpatialInteractionManager em SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="5aa2c-139">To detect presses across any of these interaction sources, you can handle the SourcePressed event on SpatialInteractionManager in SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

<span data-ttu-id="5aa2c-140">Esse evento pressionado é enviado ao seu aplicativo de maneira assíncrona.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-140">This pressed event is sent to your app asynchronously.</span></span> <span data-ttu-id="5aa2c-141">Seu aplicativo ou o mecanismo de jogo pode desejar executar algum processamento imediatamente, ou talvez você queira colocar na fila os dados de evento em sua rotina de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-141">Your app or game engine may want to perform some processing right away or you may want to queue up the event data in your input processing routine.</span></span>

<span data-ttu-id="5aa2c-142">O modelo inclui uma classe auxiliar para você começar.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-142">The template includes a helper class to get you started.</span></span> <span data-ttu-id="5aa2c-143">Este modelo forgoes qualquer processamento para manter a simplicidade do design.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-143">This template forgoes any processing for simplicity of design.</span></span> <span data-ttu-id="5aa2c-144">A classe auxiliar mantém o controle de se um ou mais **pressionado** eventos ocorridos desde a última **atualização** chamar.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-144">The helper class keeps track of whether one or more **Pressed** events occurred since the last **Update** call.</span></span> <span data-ttu-id="5aa2c-145">De SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="5aa2c-145">From SpatialInputHandler.cpp:</span></span>




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

<span data-ttu-id="5aa2c-146">Se Sim, ele retorna o [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) para o evento de entrada mais recente durante a próxima atualização.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-146">If so, it returns the [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) for the most recent input event during the next Update.</span></span> <span data-ttu-id="5aa2c-147">De SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="5aa2c-147">From SpatialInputHandler.cpp:</span></span>




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

<span data-ttu-id="5aa2c-148">Observe que o código acima tratará todos pressiona da mesma forma, se o usuário executa um primário **selecionar** pressione ou secundárias **Menu** ou **segure** pressione.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-148">Note that the code above will treat all presses the same way, whether the user is performing a primary **Select** press or a secondary **Menu** or **Grasp** press.</span></span> <span data-ttu-id="5aa2c-149">O **selecionar** pressione é uma forma principal de interação com suporte em mãos, movimento controladores e voz, disparado por uma mão executando um toque de ar, um controlador de movimento com o primário gatilho/botão é pressionado ou o usuário voz dizendo "Select".</span><span class="sxs-lookup"><span data-stu-id="5aa2c-149">The **Select** press is a primary form of interaction supported across hands, motion controllers and voice, triggered either by a hand performing an air-tap, a motion controller with its primary trigger/button pressed, or the user's voice saying "Select".</span></span> <span data-ttu-id="5aa2c-150">Selecionados pressionamentos representam a intenção do usuário para ativar o holograma que eles destinados.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-150">Select presses represent the user's intention to activate the hologram they are targeting.</span></span>

<span data-ttu-id="5aa2c-151">Ponderar sobre qual tipo de pressionamento está ocorrendo, modificaremos o manipulador de eventos SpatialInteractionManager::SourceUpdated.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-151">To reason about which kind of press is occurring, we will modify the SpatialInteractionManager::SourceUpdated event handler.</span></span> <span data-ttu-id="5aa2c-152">Nosso código detectará pressionamentos de compreensão (quando disponível) e usá-los para reposicionar o cubo.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-152">Our code will detect Grasp presses (where available) and use them to reposition the cube.</span></span> <span data-ttu-id="5aa2c-153">Se não houver uma melhor compreensão, usaremos pressionamentos de Select em vez disso.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-153">If Grasp is not available, we will use Select presses instead.</span></span>

<span data-ttu-id="5aa2c-154">Adicione as seguintes declarações de membro privado para SpatialInputHandler.h:</span><span class="sxs-lookup"><span data-stu-id="5aa2c-154">Add the following private member declarations to SpatialInputHandler.h:</span></span> 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

<span data-ttu-id="5aa2c-155">Abra SpatialInputHandler.cpp.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-155">Open SpatialInputHandler.cpp.</span></span> <span data-ttu-id="5aa2c-156">Adicione o seguinte registro de evento para o construtor:</span><span class="sxs-lookup"><span data-stu-id="5aa2c-156">Add the following event registration to the constructor:</span></span> 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

<span data-ttu-id="5aa2c-157">Isso é o código de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-157">This is the event handler code.</span></span> <span data-ttu-id="5aa2c-158">Se a fonte de entrada é tendo uma melhor compreensão, pose o ponteiro será armazenado para o próximo loop de atualização.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-158">If the input source is experiencing a Grasp, the pointer pose will be stored for the next update loop.</span></span> <span data-ttu-id="5aa2c-159">Caso contrário, ele verificará se há um pressionamento de Select em vez disso.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-159">Otherwise, it will check for a Select press instead.</span></span> <span data-ttu-id="5aa2c-160">De SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="5aa2c-160">From SpatialInputHandler.cpp:</span></span>




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

<span data-ttu-id="5aa2c-161">Certifique-se de cancelar o registro do manipulador de eventos no destruidor.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-161">Make sure to unregister the event handler in the destructor.</span></span> <span data-ttu-id="5aa2c-162">De SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="5aa2c-162">From SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

<span data-ttu-id="5aa2c-163">Recompilar e reimplantar.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-163">Recompile, and then redeploy.</span></span> <span data-ttu-id="5aa2c-164">Seu projeto de modelo agora deve ser capaz de reconhecer as interações de compreensão para reposicionar o cubo giratório.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-164">Your template project should now be able to recognize Grasp interactions to reposition the spinning cube.</span></span>

<span data-ttu-id="5aa2c-165">A API SpatialInteractionSource dá suporte a controladores com uma ampla variedade de recursos.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-165">The SpatialInteractionSource API supports controllers with a wide range of capabilities.</span></span> <span data-ttu-id="5aa2c-166">No exemplo mostrado acima, verificamos para ver se compreensão tem suporte antes de tentar usá-lo.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-166">In the example shown above, we check to see if Grasp is supported before trying to use it.</span></span> <span data-ttu-id="5aa2c-167">O SpatialInteractionSource suporta os seguintes recursos opcionais além do comum **selecionar** pressione:</span><span class="sxs-lookup"><span data-stu-id="5aa2c-167">The SpatialInteractionSource supports the following optional features beyond the common **Select** press:</span></span>
* <span data-ttu-id="5aa2c-168">**Botão de menu:** Verifique o suporte inspecionando a propriedade IsMenuSupported.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-168">**Menu button:** Check support by inspecting the IsMenuSupported property.</span></span> <span data-ttu-id="5aa2c-169">Quando houver suporte, verifique as [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) propriedade para descobrir se o botão de menu for pressionada.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-169">When supported, check the [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if the menu button is pressed.</span></span>
* <span data-ttu-id="5aa2c-170">**Segure o botão:** Verifique o suporte inspecionando a propriedade IsGraspSupported.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-170">**Grasp button:** Check support by inspecting the IsGraspSupported property.</span></span> <span data-ttu-id="5aa2c-171">Quando houver suporte, verifique as [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) propriedade para descobrir se compreensão é ativado.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-171">When supported, check the [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if grasp is activated.</span></span>

<span data-ttu-id="5aa2c-172">Para controladores, o SpatialInteractionSource tem uma propriedade de controlador com recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-172">For controllers, the SpatialInteractionSource has a Controller property with additional capabilities.</span></span>
* <span data-ttu-id="5aa2c-173">**HasThumbstick:** Se for true, o controlador tem um analógico.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-173">**HasThumbstick:** If true, the controller has a thumbstick.</span></span> <span data-ttu-id="5aa2c-174">Inspecione o [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) propriedade do SpatialInteractionSourceState para adquirir o analógico x e y de valores (ThumbstickX e ThumbstickY), bem como seu estado pressionado (IsThumbstickPressed).</span><span class="sxs-lookup"><span data-stu-id="5aa2c-174">Inspect the [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) property of the SpatialInteractionSourceState to acquire the thumbstick x and y values (ThumbstickX and ThumbstickY), as well as its pressed state (IsThumbstickPressed).</span></span>
* <span data-ttu-id="5aa2c-175">**HasTouchpad:** Se for true, o controlador tem um touchpad.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-175">**HasTouchpad:** If true, the controller has a touchpad.</span></span> <span data-ttu-id="5aa2c-176">Inspecionar a propriedade ControllerProperties do SpatialInteractionSourceState para adquirir o touchpad x e y valores (TouchpadX e TouchpadY), bem como para saber se o usuário toca o teclado (IsTouchpadTouched) e se eles estão nos pressionando o touchpad para baixo ( IsTouchpadPressed).</span><span class="sxs-lookup"><span data-stu-id="5aa2c-176">Inspect the ControllerProperties property of the SpatialInteractionSourceState to acquire the touchpad x and y values (TouchpadX and TouchpadY), and to know if the user is touching the pad (IsTouchpadTouched) and if they are pressing the touchpad down (IsTouchpadPressed).</span></span>
* <span data-ttu-id="5aa2c-177">**SimpleHapticsController:** A API SimpleHapticsController para o controlador permite que você inspecione as capacidades de haptics do controlador, e ele também permite que você controle os comentários hápticos.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-177">**SimpleHapticsController:** The SimpleHapticsController API for the controller allows you to inspect the haptics capabilities of the controller, and it also allows you to control haptic feedback.</span></span>

<span data-ttu-id="5aa2c-178">Observe que o intervalo para touchpad e direcional de -1 para 1 para ambos os eixos (de baixo para cima e da esquerda para direita).</span><span class="sxs-lookup"><span data-stu-id="5aa2c-178">Note that the range for touchpad and thumbstick from -1 to 1 for both axes (from bottom to top, and from left to right).</span></span> <span data-ttu-id="5aa2c-179">O intervalo para o gatilho analógico, que pode é acessado usando a propriedade SpatialInteractionSourceState::SelectPressedValue, tem um intervalo de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-179">The range for the analog trigger, which is accessed using the SpatialInteractionSourceState::SelectPressedValue property, has a range of 0 to 1.</span></span> <span data-ttu-id="5aa2c-180">Um valor de 1 correlaciona com IsSelectPressed sendo igual a true; qualquer outro valor se correlaciona com IsSelectPressed sendo igual a false.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-180">A value of 1 correlates with IsSelectPressed being equal to true; any other value correlates with IsSelectPressed being equal to false.</span></span>

<span data-ttu-id="5aa2c-181">Observe que, para uma mão e um controlador, usar SpatialInteractionSourceState::Properties::TryGetLocation fornecerá a posição do usuário mão - isso é diferente da pose de ponteiro que representa o raio de apontador do controlador.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-181">Note that for both a hand and a controller, using SpatialInteractionSourceState::Properties::TryGetLocation will provide the user's hand position - this is distinct from the pointer pose representing the controller's pointing ray.</span></span> <span data-ttu-id="5aa2c-182">Se você quiser desenhar algo no local disponível, use TryGetLocation.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-182">If you want to draw something at the hand location, use TryGetLocation.</span></span> <span data-ttu-id="5aa2c-183">Se você quiser raycast da ponta do controlador, obtenha o raio de apontador de TryGetInteractionSourcePose sobre o SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-183">If you want to raycast from the tip of the controller, get the pointing ray from TryGetInteractionSourcePose on the SpatialPointerPose.</span></span>

<span data-ttu-id="5aa2c-184">Você também pode usar os outros eventos no SpatialInteractionManager como SourceDetected e SourceLost, para reagir quando mãos entrar ou saiam de exibição do dispositivo ou quando eles movem ou recusar a posição de pronta (dedo gerado com palm para frente), ou quando o motion controladores são ativados ou desativado ou estão emparelhados/não emparelhado.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-184">You can also use the other events on SpatialInteractionManager, such as SourceDetected and SourceLost, to react when hands enter or leave the device's view or when they move in or out of the ready position (index finger raised with palm forward), or when motion controllers are turned on/off or are paired/unpaired.</span></span>

### <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="5aa2c-185">Alça pose versus pose apontador</span><span class="sxs-lookup"><span data-stu-id="5aa2c-185">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="5aa2c-186">Realidade mista do Windows oferece suporte a controladores de movimento em uma variedade de fatores forma, com o design de cada controlador difere em sua relação entre a posição do usuário mão e natural "encaminhar" direção que aplicativos deve usar para apontando ao renderizar o controlador.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-186">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="5aa2c-187">Para melhor representar esses controladores, há dois tipos de poses, que você pode investigar para cada fonte de interação:</span><span class="sxs-lookup"><span data-stu-id="5aa2c-187">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>
* <span data-ttu-id="5aa2c-188">O **alça pose**, que representa o local de palma da mão detectada por um HoloLens ou palma mantendo um controlador de animação.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-188">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="5aa2c-189">Em fones imersivos em exposição, essa pose é melhor usado para renderizar **mão do usuário** ou **um objeto é mantido em mãos do usuário**, como uma espada ou elétrons.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-189">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="5aa2c-190">O **segure posição**: O centroide de palm pressionando o controlador naturalmente, ajustado esquerda ou direita para centralizar a posição dentro a alça.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-190">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="5aa2c-191">O **Segure o eixo à direita da orientação**: Quando você abre completamente sua mão para formar uma dedo simples 5 pose, raio que é normal para o palm (para a frente da esquerda palm, com versões anteriores do palm à direita)</span><span class="sxs-lookup"><span data-stu-id="5aa2c-191">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="5aa2c-192">O **Segure o eixo de encaminhamento da orientação**: Quando você fecha sua mão parcialmente (como se que mantém o controlador), o raio que aponta "forward" por meio de tubo formado por seus dedos não thumb.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-192">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="5aa2c-193">O **segure orientação backup eixo**: O eixo de cima indicado pelas definições de direito e Avançar.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-193">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="5aa2c-194">Você pode acessar a pose alça por meio de [SpatialInteractionSourceState.Properties.TryGetLocation(...) ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span><span class="sxs-lookup"><span data-stu-id="5aa2c-194">You can access the grip pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span></span>
* <span data-ttu-id="5aa2c-195">O **ponteiro pose**, que representa a dica do controlador que aponta para a frente.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-195">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="5aa2c-196">Essa pose é melhor usado para raycast quando **apontando para a interface do usuário** quando você está renderizando o próprio modelo de controlador.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-196">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="5aa2c-197">Você pode acessar a pose ponteiro por meio de [SpatialInteractionSourceState.Properties.TryGetLocation(...). SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) ou [SpatialInteractionSourceState.TryGetPointerPose(...). TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span><span class="sxs-lookup"><span data-stu-id="5aa2c-197">You can access the pointer pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...).SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) or [SpatialInteractionSourceState.TryGetPointerPose(...).TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span></span>

### <a name="composite-gestures-spatialgesturerecognizer"></a><span data-ttu-id="5aa2c-198">Gestos de composição: SpatialGestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="5aa2c-198">Composite gestures: SpatialGestureRecognizer</span></span>

<span data-ttu-id="5aa2c-199">Um [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interpreta interações do usuário de mãos, controladores de movimento e o comando de voz "Selecionar" para eventos de gesto espacial superfície, qual destino de usuários usando seu olhar principal.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-199">A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interprets user interactions from hands, motion controllers, and the "Select" voice command to surface spatial gesture events, which users target using their head gaze.</span></span>

<span data-ttu-id="5aa2c-200">Gestos espaciais são uma forma de chave de entrada para aplicativos de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-200">Spatial gestures are a key form of input for Windows Mixed Reality apps.</span></span> <span data-ttu-id="5aa2c-201">Ao roteamentos interações do SpatialInteractionManager para SpatialGestureRecognizer de um holograma, aplicativos podem detectar eventos de toque, espera, manipulação e navegação uniformemente em mãos, voz e dispositivos de entrada espaciais, sem a necessidade que tratar pressionamentos de e libera manualmente.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-201">By routing interactions from the SpatialInteractionManager to a hologram's SpatialGestureRecognizer, apps can detect Tap, Hold, Manipulation, and Navigation events uniformly across hands, voice, and spatial input devices, without having to handle presses and releases manually.</span></span>

<span data-ttu-id="5aa2c-202">SpatialGestureRecognizer executa somente a Desambiguidade mínimo entre o conjunto de gestos de que você solicitar.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-202">SpatialGestureRecognizer performs only the minimal disambiguation between the set of gestures that you request.</span></span> <span data-ttu-id="5aa2c-203">Por exemplo, se você solicitar apenas toque, o usuário pode pressionada seu dedo, desde que eles gostam e um toque ainda ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-203">For example, if you request just Tap, the user may hold their finger down as long as they like and a Tap will still occur.</span></span> <span data-ttu-id="5aa2c-204">Se você solicitar o toque e mantenha, após cerca de um segundo de mantendo seu dedo, o gesto promoverá a uma isenção e um toque não ocorrerão mais.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-204">If you request both Tap and Hold, after about a second of holding down their finger, the gesture will promote to a Hold and a Tap will no longer occur.</span></span>

<span data-ttu-id="5aa2c-205">Para usar SpatialGestureRecognizer, lidar com o SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) eventos e captura o SpatialPointerPose exposto lá.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-205">To use SpatialGestureRecognizer, handle the SpatialInteractionManager's [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) event and grab the SpatialPointerPose exposed there.</span></span> <span data-ttu-id="5aa2c-206">Use ray de olhar principal do usuário dessa pose para ter interseção com as hologramas e superfície malhas no ambiente do usuário, para determinar o que o usuário pretende interagir com.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-206">Use the user's head gaze ray from this pose to intersect with the holograms and surface meshes in the user's surroundings, in order to determine what the user is intending to interact with.</span></span> <span data-ttu-id="5aa2c-207">Em seguida, encaminhar o SpatialInteraction nos argumentos de evento para SpatialGestureRecognizer do holograma de destino, usando seus [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) método.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-207">Then, route the SpatialInteraction in the event arguments to the target hologram's SpatialGestureRecognizer, using its [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) method.</span></span> <span data-ttu-id="5aa2c-208">Isso inicia a interpretação de interação de acordo com o [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) definir esse reconhecedor no momento da criação - ou pelo [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span><span class="sxs-lookup"><span data-stu-id="5aa2c-208">This starts interpreting that interaction according to the [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) set on that recognizer at creation time - or by [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span></span>

<span data-ttu-id="5aa2c-209">Em HoloLens, interações e gestos geralmente devem derivar seu direcionamento de olhar de principal do usuário, em vez de tentar renderizar ou interagir diretamente no local da mão.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-209">On HoloLens, interactions and gestures should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="5aa2c-210">Após o início de uma interação relativos movimentos da mão podem ser usados para controlar o gesto, assim como acontece com o gesto de manipulação ou navegação.</span><span class="sxs-lookup"><span data-stu-id="5aa2c-210">Once an interaction has started, relative motions of the hand may be used to control the gesture, as with the Manipulation or Navigation gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="5aa2c-211">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5aa2c-211">See also</span></span>
* [<span data-ttu-id="5aa2c-212">Gaze</span><span class="sxs-lookup"><span data-stu-id="5aa2c-212">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="5aa2c-213">Gestos</span><span class="sxs-lookup"><span data-stu-id="5aa2c-213">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="5aa2c-214">Controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="5aa2c-214">Motion controllers</span></span>](motion-controllers.md)
