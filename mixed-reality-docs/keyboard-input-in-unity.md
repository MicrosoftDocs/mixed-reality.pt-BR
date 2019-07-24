---
title: Entrada de teclado no Unity
description: O Unity fornece a classe TouchScreenKeyboard para aceitar a entrada de teclado quando não há nenhum teclado físico disponível.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: teclado, entrada, Unity, touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515732"
---
# <a name="keyboard-input-in-unity"></a>Entrada de teclado no Unity

**Namespace:** *UnityEngine*<br>
 **Tipo**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Embora o HoloLens dê suporte a muitas formas de entrada, incluindo teclados Bluetooth, a maioria dos aplicativos não pode pressupor que todos os usuários terão um Keyboard físico disponível. Se seu aplicativo exigir entrada de texto, alguma forma de teclado na tela deverá ser fornecida.

O Unity fornece a classe *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* para aceitar a entrada de teclado quando não há nenhum teclado físico disponível.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Comportamento do teclado do sistema do HoloLens no Unity

No HoloLens, o *TouchScreenKeyboard* aproveita o teclado do sistema na tela. O teclado na tela do sistema não pode sobrepor a parte superior de uma exibição volumétricos para que o Unity precise criar uma exibição XAML 2D secundária para mostrar o teclado e retornar à exibição volumétricos depois que a entrada tiver sido enviada. O fluxo do usuário é assim:
1. O usuário executa uma ação fazendo com que o código do aplicativo chame *TouchScreenKeyboard*
    * O aplicativo é responsável por pausar o estado do aplicativo antes de chamar *TouchScreenKeyboard*
    * O aplicativo pode terminar antes de mudar de volta para a exibição volumétricos
2. O Unity alterna para uma exibição XAML 2D que é colocada automaticamente no mundo
3. O usuário digita o texto usando o teclado do sistema e envia ou cancela
4. O Unity alterna para a exibição volumétricos
    * O aplicativo é responsável por retomar o estado do aplicativo quando o *TouchScreenKeyboard* é concluído
5. O texto enviado está disponível no *TouchScreenKeyboard*

### <a name="available-keyboard-views"></a>Modos de exibição de teclado disponíveis

Há seis exibições de teclado diferentes disponíveis:
* Caixa de texto de linha única
* Caixa de texto de linha única com título
* Caixa de texto de várias linhas
* Caixa de texto de várias linhas com título
* Caixa de senha de linha única
* Caixa de senha de linha única com título

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Como habilitar o teclado do sistema no Unity

O teclado do sistema do HoloLens está disponível somente para aplicativos do Unity que são exportados com o "tipo de compilação UWP" definido como "XAML". Há compensações que você faz quando escolhe "XAML" como o "tipo de compilação UWP" sobre "D3D". Se você não estiver familiarizado com essas compensações, talvez queira explorar uma [solução de entrada alternativa](#alternative-keyboard-options) para o teclado do sistema.
1. Abra o menu **arquivo** e selecione **configurações de compilação...**
2. Verifique se **a plataforma** está definida como **Windows Store**, se o **SDK** está definido como **Universal 10**e defina o **tipo de compilação UWP** como **XAML**.
3. Na caixa de diálogo **configurações de compilação** , clique no botão **configurações do Player...**
4. Selecione a guia **configurações da Windows Store**
5. Expanda o grupo **outras configurações**
6. Na seção **renderização** , marque a caixa de seleção **suporte à realidade virtual** para adicionar uma nova lista de **dispositivos de realidade virtual**
7. Verifique se o **Windows Holographic** aparece na lista de SDKs de realidade virtual

>[!NOTE]
>Se você não marcar a compilação como realidade virtual com suporte com o dispositivo de HoloLens, o projeto será exportado como um aplicativo XAML 2D.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Usando o teclado do sistema em seu aplicativo do Unity

### <a name="declare-the-keyboard"></a>Declarar o teclado

Na classe, declare uma variável para armazenar o *TouchScreenKeyboard* e uma variável para conter a cadeia de caracteres que o teclado retorna.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Invocar o teclado

Quando ocorrer um evento solicitando entrada de teclado, chame uma dessas funções dependendo do tipo de entrada desejado. Observe que o título é especificado no parâmetro textplaceholder.

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

### <a name="retrieve-typed-contents"></a>Recuperar conteúdo digitado

No loop de atualização, verifique se o teclado recebeu uma nova entrada e armazene-a para uso em outro lugar.

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

## <a name="alternative-keyboard-options"></a>Opções de teclado alternativas

Entendemos que a mudança de uma exibição volumétricos para uma exibição 2D não é a maneira ideal de obter a entrada de texto do usuário.

As alternativas atuais para aproveitar o teclado do sistema por meio do Unity incluem:
* Usando o ditado de fala para entrada (<b>Observação:</b> isso costuma ser propenso a erros para palavras não encontradas no dicionário e não é adequado para entrada de senha)
* Criar um teclado que funciona em sua exibição exclusiva de aplicativos
