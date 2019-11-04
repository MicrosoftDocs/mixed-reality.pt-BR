---
title: Entrada de teclado no Unity
description: O Unity fornece a classe TouchScreenKeyboard para aceitar a entrada de teclado quando não há nenhum teclado físico disponível.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: teclado, entrada, Unity, touchscreenkeyboard
ms.openlocfilehash: f506415f9658d9723bf31b339d63fe4569100ace
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438556"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="36932-104">Entrada de teclado no Unity</span><span class="sxs-lookup"><span data-stu-id="36932-104">Keyboard input in Unity</span></span>

<span data-ttu-id="36932-105">**Namespace:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="36932-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="36932-106">**Tipo**:  *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="36932-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="36932-107">Embora o HoloLens dê suporte a muitas formas de entrada, incluindo teclados Bluetooth, a maioria dos aplicativos não pode pressupor que todos os usuários terão um Keyboard físico disponível.</span><span class="sxs-lookup"><span data-stu-id="36932-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="36932-108">Se seu aplicativo exigir entrada de texto, alguma forma de teclado na tela deverá ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="36932-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="36932-109">O Unity fornece a classe *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* para aceitar a entrada de teclado quando não há nenhum teclado físico disponível.</span><span class="sxs-lookup"><span data-stu-id="36932-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="36932-110">Comportamento do teclado do sistema do HoloLens no Unity</span><span class="sxs-lookup"><span data-stu-id="36932-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="36932-111">No HoloLens, o *TouchScreenKeyboard* aproveita o teclado do sistema na tela.</span><span class="sxs-lookup"><span data-stu-id="36932-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="36932-112">O teclado na tela do sistema não pode sobrepor a parte superior de uma exibição volumétricos para que o Unity precise criar uma exibição XAML 2D secundária para mostrar o teclado e retornar à exibição volumétricos depois que a entrada tiver sido enviada.</span><span class="sxs-lookup"><span data-stu-id="36932-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="36932-113">O fluxo do usuário é assim:</span><span class="sxs-lookup"><span data-stu-id="36932-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="36932-114">O usuário executa uma ação fazendo com que o código do aplicativo chame *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="36932-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="36932-115">O aplicativo é responsável por pausar o estado do aplicativo antes de chamar *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="36932-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="36932-116">O aplicativo pode terminar antes de mudar de volta para a exibição volumétricos</span><span class="sxs-lookup"><span data-stu-id="36932-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="36932-117">O Unity alterna para uma exibição XAML 2D que é colocada automaticamente no mundo</span><span class="sxs-lookup"><span data-stu-id="36932-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="36932-118">O usuário digita o texto usando o teclado do sistema e envia ou cancela</span><span class="sxs-lookup"><span data-stu-id="36932-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="36932-119">O Unity alterna para a exibição volumétricos</span><span class="sxs-lookup"><span data-stu-id="36932-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="36932-120">O aplicativo é responsável por retomar o estado do aplicativo quando o *TouchScreenKeyboard* é concluído</span><span class="sxs-lookup"><span data-stu-id="36932-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="36932-121">O texto enviado está disponível no *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="36932-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="36932-122">Modos de exibição de teclado disponíveis</span><span class="sxs-lookup"><span data-stu-id="36932-122">Available keyboard views</span></span>

<span data-ttu-id="36932-123">Há seis exibições de teclado diferentes disponíveis:</span><span class="sxs-lookup"><span data-stu-id="36932-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="36932-124">Caixa de texto de linha única</span><span class="sxs-lookup"><span data-stu-id="36932-124">Single-line textbox</span></span>
* <span data-ttu-id="36932-125">Caixa de texto de linha única com título</span><span class="sxs-lookup"><span data-stu-id="36932-125">Single-line textbox with title</span></span>
* <span data-ttu-id="36932-126">Caixa de texto de várias linhas</span><span class="sxs-lookup"><span data-stu-id="36932-126">Multi-line textbox</span></span>
* <span data-ttu-id="36932-127">Caixa de texto de várias linhas com título</span><span class="sxs-lookup"><span data-stu-id="36932-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="36932-128">Caixa de senha de linha única</span><span class="sxs-lookup"><span data-stu-id="36932-128">Single-line password box</span></span>
* <span data-ttu-id="36932-129">Caixa de senha de linha única com título</span><span class="sxs-lookup"><span data-stu-id="36932-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="36932-130">Como habilitar o teclado do sistema no Unity</span><span class="sxs-lookup"><span data-stu-id="36932-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="36932-131">O teclado do sistema do HoloLens está disponível somente para aplicativos do Unity que são exportados com o "tipo de compilação UWP" definido como "XAML".</span><span class="sxs-lookup"><span data-stu-id="36932-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="36932-132">Há compensações que você faz quando escolhe "XAML" como o "tipo de compilação UWP" sobre "D3D".</span><span class="sxs-lookup"><span data-stu-id="36932-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="36932-133">Se você não estiver familiarizado com essas compensações, talvez queira explorar uma [solução de entrada alternativa](#alternative-keyboard-options) para o teclado do sistema.</span><span class="sxs-lookup"><span data-stu-id="36932-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="36932-134">Abra o menu **arquivo** e selecione **configurações de compilação...**</span><span class="sxs-lookup"><span data-stu-id="36932-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="36932-135">Verifique se **a plataforma** está definida como **Windows Store**, se o **SDK** está definido como **Universal 10**e defina o **tipo de compilação UWP** como **XAML**.</span><span class="sxs-lookup"><span data-stu-id="36932-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="36932-136">Na caixa de diálogo **configurações de compilação** , clique no botão **configurações do Player...**</span><span class="sxs-lookup"><span data-stu-id="36932-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="36932-137">Selecione a guia **configurações da Windows Store**</span><span class="sxs-lookup"><span data-stu-id="36932-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="36932-138">Expanda o grupo **outras configurações**</span><span class="sxs-lookup"><span data-stu-id="36932-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="36932-139">Na seção **renderização** , marque a caixa de seleção **suporte à realidade virtual** para adicionar uma nova lista de **dispositivos de realidade virtual**</span><span class="sxs-lookup"><span data-stu-id="36932-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="36932-140">Verifique se o **Windows Holographic** aparece na lista de SDKs de realidade virtual</span><span class="sxs-lookup"><span data-stu-id="36932-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="36932-141">Se você não marcar a compilação como realidade virtual com suporte com o dispositivo de HoloLens, o projeto será exportado como um aplicativo XAML 2D.</span><span class="sxs-lookup"><span data-stu-id="36932-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="36932-142">Usando o teclado do sistema em seu aplicativo do Unity</span><span class="sxs-lookup"><span data-stu-id="36932-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="36932-143">Declarar o teclado</span><span class="sxs-lookup"><span data-stu-id="36932-143">Declare the keyboard</span></span>

<span data-ttu-id="36932-144">Na classe, declare uma variável para armazenar o *TouchScreenKeyboard* e uma variável para conter a cadeia de caracteres que o teclado retorna.</span><span class="sxs-lookup"><span data-stu-id="36932-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="36932-145">Invocar o teclado</span><span class="sxs-lookup"><span data-stu-id="36932-145">Invoke the keyboard</span></span>

<span data-ttu-id="36932-146">Quando ocorrer um evento solicitando entrada de teclado, chame uma dessas funções dependendo do tipo de entrada desejado.</span><span class="sxs-lookup"><span data-stu-id="36932-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="36932-147">Observe que o título é especificado no parâmetro textplaceholder.</span><span class="sxs-lookup"><span data-stu-id="36932-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a><span data-ttu-id="36932-148">Recuperar conteúdo digitado</span><span class="sxs-lookup"><span data-stu-id="36932-148">Retrieve typed contents</span></span>

<span data-ttu-id="36932-149">No loop de atualização, verifique se o teclado recebeu uma nova entrada e armazene-a para uso em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="36932-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="36932-150">Opções de teclado alternativas</span><span class="sxs-lookup"><span data-stu-id="36932-150">Alternative keyboard options</span></span>

<span data-ttu-id="36932-151">Entendemos que a mudança de uma exibição volumétricos para uma exibição 2D não é a maneira ideal de obter a entrada de texto do usuário.</span><span class="sxs-lookup"><span data-stu-id="36932-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="36932-152">As alternativas atuais para aproveitar o teclado do sistema por meio do Unity incluem:</span><span class="sxs-lookup"><span data-stu-id="36932-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="36932-153">Usando o ditado de fala para entrada (<b>Observação:</b> isso costuma ser propenso a erros para palavras não encontradas no dicionário e não é adequado para entrada de senha)</span><span class="sxs-lookup"><span data-stu-id="36932-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="36932-154">Criar um teclado que funciona em sua exibição exclusiva de aplicativos</span><span class="sxs-lookup"><span data-stu-id="36932-154">Create a keyboard that works in your applications exclusive view</span></span>
