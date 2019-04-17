---
title: Entrada do teclado no Unity
description: Unity fornece a classe TouchScreenKeyboard para aceitar a entrada do teclado quando não há nenhum teclado físico disponível.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: unity de entrada, do teclado, touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590977"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="bdc50-104">Entrada do teclado no Unity</span><span class="sxs-lookup"><span data-stu-id="bdc50-104">Keyboard input in Unity</span></span>

<span data-ttu-id="bdc50-105">**Namespace:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="bdc50-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="bdc50-106">**Tipo**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="bdc50-106">**Type**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="bdc50-107">Enquanto o HoloLens dá suporte a muitos formulários de entrada, incluindo Bluetooth teclados, a maioria dos aplicativos não pode presumir que todos os usuários terão um teclado físico disponível.</span><span class="sxs-lookup"><span data-stu-id="bdc50-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="bdc50-108">Se seu aplicativo exigir a entrada de texto, alguma forma de teclado na tela deve ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="bdc50-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="bdc50-109">Unity fornece a *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* classe para aceitar a entrada do teclado quando não há nenhum teclado físico disponível.</span><span class="sxs-lookup"><span data-stu-id="bdc50-109">Unity provides the *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="bdc50-110">Comportamento de teclado do sistema HoloLens no Unity</span><span class="sxs-lookup"><span data-stu-id="bdc50-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="bdc50-111">Em HoloLens, o *TouchScreenKeyboard* aproveita o teclado na tela do sistema.</span><span class="sxs-lookup"><span data-stu-id="bdc50-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="bdc50-112">Teclado na tela do sistema é capaz de sobreposição na parte superior de um modo de exibição volumétricos para que o Unity tem que criar uma exibição XAML 2D secundária para mostrar o teclado em seguida, retornar para o modo de exibição volumétricos depois que a entrada foi enviada.</span><span class="sxs-lookup"><span data-stu-id="bdc50-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="bdc50-113">O fluxo de usuário funciona assim:</span><span class="sxs-lookup"><span data-stu-id="bdc50-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="bdc50-114">O usuário executa uma ação, fazendo com que o código do aplicativo chamar *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="bdc50-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="bdc50-115">O aplicativo é responsável por estado de pausa do aplicativo antes de chamar *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="bdc50-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="bdc50-116">O aplicativo pode encerrar antes de alternar nunca para o modo de exibição volumétrico</span><span class="sxs-lookup"><span data-stu-id="bdc50-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="bdc50-117">Unity alterna para um modo de exibição XAML 2D que é colocado em automática no mundo</span><span class="sxs-lookup"><span data-stu-id="bdc50-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="bdc50-118">O usuário digita texto usando o teclado de sistema e envia ou cancele</span><span class="sxs-lookup"><span data-stu-id="bdc50-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="bdc50-119">Unity alterna para o modo de exibição volumétricos</span><span class="sxs-lookup"><span data-stu-id="bdc50-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="bdc50-120">O aplicativo é responsável para continuar o aplicativo estado quando o *TouchScreenKeyboard* é feito</span><span class="sxs-lookup"><span data-stu-id="bdc50-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="bdc50-121">Texto enviados está disponível na *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="bdc50-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="bdc50-122">Modos de exibição de teclado disponíveis</span><span class="sxs-lookup"><span data-stu-id="bdc50-122">Available keyboard views</span></span>

<span data-ttu-id="bdc50-123">Há seis exibições diferentes de teclado disponíveis:</span><span class="sxs-lookup"><span data-stu-id="bdc50-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="bdc50-124">Caixa de texto de linha única</span><span class="sxs-lookup"><span data-stu-id="bdc50-124">Single-line textbox</span></span>
* <span data-ttu-id="bdc50-125">Caixa de texto de linha única com título</span><span class="sxs-lookup"><span data-stu-id="bdc50-125">Single-line textbox with title</span></span>
* <span data-ttu-id="bdc50-126">Caixa de texto de várias linha</span><span class="sxs-lookup"><span data-stu-id="bdc50-126">Multi-line textbox</span></span>
* <span data-ttu-id="bdc50-127">Caixa de texto de várias linha com título</span><span class="sxs-lookup"><span data-stu-id="bdc50-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="bdc50-128">Caixa de senha de linha única</span><span class="sxs-lookup"><span data-stu-id="bdc50-128">Single-line password box</span></span>
* <span data-ttu-id="bdc50-129">Caixa de senha de uma linha com o título</span><span class="sxs-lookup"><span data-stu-id="bdc50-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="bdc50-130">Como habilitar o teclado de sistema no Unity</span><span class="sxs-lookup"><span data-stu-id="bdc50-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="bdc50-131">O teclado de sistema do HoloLens só está disponível para aplicativos Unity são exportados com o "UWP criar tipo" definido como "XAML".</span><span class="sxs-lookup"><span data-stu-id="bdc50-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="bdc50-132">Há compensações feitas quando você escolhe "XAML" como o "tipo de compilação em UWP" sobre "D3D".</span><span class="sxs-lookup"><span data-stu-id="bdc50-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="bdc50-133">Se você não estiver confortável com essas desvantagens, talvez você queira explorar uma [solução de entrada alternativa](#alternative-keyboard-options) para o teclado do sistema.</span><span class="sxs-lookup"><span data-stu-id="bdc50-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="bdc50-134">Abra o **arquivo** menu e selecione **configurações de compilação...**</span><span class="sxs-lookup"><span data-stu-id="bdc50-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="bdc50-135">Certifique-se a **plataforma** é definido como **Windows Store**, o **SDK** é definido como **10 Universal**e defina o **tipo de compilação de UWP**  à **XAML**.</span><span class="sxs-lookup"><span data-stu-id="bdc50-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="bdc50-136">No **configurações de Build** caixa de diálogo, clique o **configurações do Player...**  botão</span><span class="sxs-lookup"><span data-stu-id="bdc50-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="bdc50-137">Selecione o **configurações para Windows Store** guia</span><span class="sxs-lookup"><span data-stu-id="bdc50-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="bdc50-138">Expanda o **outras configurações** grupo</span><span class="sxs-lookup"><span data-stu-id="bdc50-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="bdc50-139">No **renderização** seção, verifique os **suporte de realidade Virtual** caixa de seleção para adicionar uma nova **dispositivos de realidade Virtual** lista</span><span class="sxs-lookup"><span data-stu-id="bdc50-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="bdc50-140">Certifique-se **Windows Holographic** aparece na lista de SDKs de realidade Virtual</span><span class="sxs-lookup"><span data-stu-id="bdc50-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="bdc50-141">Se você não marcar a compilação como suporte de realidade Virtual com o dispositivo HoloLens, o projeto serão exportados como um aplicativo XAML de 2D.</span><span class="sxs-lookup"><span data-stu-id="bdc50-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="bdc50-142">Usando o teclado de sistema no seu aplicativo do Unity</span><span class="sxs-lookup"><span data-stu-id="bdc50-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="bdc50-143">Declare o teclado</span><span class="sxs-lookup"><span data-stu-id="bdc50-143">Declare the keyboard</span></span>

<span data-ttu-id="bdc50-144">Na classe, declare uma variável para armazenar o *TouchScreenKeyboard* e retorna uma variável para conter a cadeia de caracteres do teclado.</span><span class="sxs-lookup"><span data-stu-id="bdc50-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="bdc50-145">Invocar o teclado</span><span class="sxs-lookup"><span data-stu-id="bdc50-145">Invoke the keyboard</span></span>

<span data-ttu-id="bdc50-146">Quando um evento ocorre solicitar entrada do teclado, chame uma dessas funções, dependendo do tipo de entrada desejado.</span><span class="sxs-lookup"><span data-stu-id="bdc50-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="bdc50-147">Observe que o título é especificado no parâmetro textPlaceholder.</span><span class="sxs-lookup"><span data-stu-id="bdc50-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

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

### <a name="retrieve-typed-contents"></a><span data-ttu-id="bdc50-148">Recuperar conteúdo tipado</span><span class="sxs-lookup"><span data-stu-id="bdc50-148">Retrieve typed contents</span></span>

<span data-ttu-id="bdc50-149">No loop de atualização, verifique se o teclado recebeu uma nova entrada e armazená-lo para uso em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="bdc50-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

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

## <a name="alternative-keyboard-options"></a><span data-ttu-id="bdc50-150">Opções de teclado alternativos</span><span class="sxs-lookup"><span data-stu-id="bdc50-150">Alternative keyboard options</span></span>

<span data-ttu-id="bdc50-151">Entendemos que desativando uma exibição volumétricas em uma exibição 2D não é a maneira ideal de obter entrada de texto do usuário.</span><span class="sxs-lookup"><span data-stu-id="bdc50-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="bdc50-152">As alternativas atuais para aproveitar o teclado do sistema por meio do Unity incluem:</span><span class="sxs-lookup"><span data-stu-id="bdc50-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="bdc50-153">Usando comandos de fala para entrada (<b>Observação:</b> isso geralmente é propenso a falhas não encontrado no dicionário de palavras e não é adequado para entrada de senha)</span><span class="sxs-lookup"><span data-stu-id="bdc50-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="bdc50-154">Criar um teclado que funciona no modo de exibição exclusivo aplicativos</span><span class="sxs-lookup"><span data-stu-id="bdc50-154">Create a keyboard that works in your applications exclusive view</span></span>
