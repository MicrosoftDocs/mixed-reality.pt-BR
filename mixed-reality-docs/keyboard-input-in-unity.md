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
# <a name="keyboard-input-in-unity"></a>Entrada do teclado no Unity

**Namespace:** *UnityEngine*<br>
 **Tipo**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Enquanto o HoloLens dá suporte a muitos formulários de entrada, incluindo Bluetooth teclados, a maioria dos aplicativos não pode presumir que todos os usuários terão um teclado físico disponível. Se seu aplicativo exigir a entrada de texto, alguma forma de teclado na tela deve ser fornecida.

Unity fornece a *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* classe para aceitar a entrada do teclado quando não há nenhum teclado físico disponível.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Comportamento de teclado do sistema HoloLens no Unity

Em HoloLens, o *TouchScreenKeyboard* aproveita o teclado na tela do sistema. Teclado na tela do sistema é capaz de sobreposição na parte superior de um modo de exibição volumétricos para que o Unity tem que criar uma exibição XAML 2D secundária para mostrar o teclado em seguida, retornar para o modo de exibição volumétricos depois que a entrada foi enviada. O fluxo de usuário funciona assim:
1. O usuário executa uma ação, fazendo com que o código do aplicativo chamar *TouchScreenKeyboard*
    * O aplicativo é responsável por estado de pausa do aplicativo antes de chamar *TouchScreenKeyboard*
    * O aplicativo pode encerrar antes de alternar nunca para o modo de exibição volumétrico
2. Unity alterna para um modo de exibição XAML 2D que é colocado em automática no mundo
3. O usuário digita texto usando o teclado de sistema e envia ou cancele
4. Unity alterna para o modo de exibição volumétricos
    * O aplicativo é responsável para continuar o aplicativo estado quando o *TouchScreenKeyboard* é feito
5. Texto enviados está disponível na *TouchScreenKeyboard*

### <a name="available-keyboard-views"></a>Modos de exibição de teclado disponíveis

Há seis exibições diferentes de teclado disponíveis:
* Caixa de texto de linha única
* Caixa de texto de linha única com título
* Caixa de texto de várias linha
* Caixa de texto de várias linha com título
* Caixa de senha de linha única
* Caixa de senha de uma linha com o título

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Como habilitar o teclado de sistema no Unity

O teclado de sistema do HoloLens só está disponível para aplicativos Unity são exportados com o "UWP criar tipo" definido como "XAML". Há compensações feitas quando você escolhe "XAML" como o "tipo de compilação em UWP" sobre "D3D". Se você não estiver confortável com essas desvantagens, talvez você queira explorar uma [solução de entrada alternativa](#alternative-keyboard-options) para o teclado do sistema.
1. Abra o **arquivo** menu e selecione **configurações de compilação...**
2. Certifique-se a **plataforma** é definido como **Windows Store**, o **SDK** é definido como **10 Universal**e defina o **tipo de compilação de UWP**  à **XAML**.
3. No **configurações de Build** caixa de diálogo, clique o **configurações do Player...**  botão
4. Selecione o **configurações para Windows Store** guia
5. Expanda o **outras configurações** grupo
6. No **renderização** seção, verifique os **suporte de realidade Virtual** caixa de seleção para adicionar uma nova **dispositivos de realidade Virtual** lista
7. Certifique-se **Windows Holographic** aparece na lista de SDKs de realidade Virtual

>[!NOTE]
>Se você não marcar a compilação como suporte de realidade Virtual com o dispositivo HoloLens, o projeto serão exportados como um aplicativo XAML de 2D.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Usando o teclado de sistema no seu aplicativo do Unity

### <a name="declare-the-keyboard"></a>Declare o teclado

Na classe, declare uma variável para armazenar o *TouchScreenKeyboard* e retorna uma variável para conter a cadeia de caracteres do teclado.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Invocar o teclado

Quando um evento ocorre solicitar entrada do teclado, chame uma dessas funções, dependendo do tipo de entrada desejado. Observe que o título é especificado no parâmetro textPlaceholder.

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

### <a name="retrieve-typed-contents"></a>Recuperar conteúdo tipado

No loop de atualização, verifique se o teclado recebeu uma nova entrada e armazená-lo para uso em outro lugar.

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

## <a name="alternative-keyboard-options"></a>Opções de teclado alternativos

Entendemos que desativando uma exibição volumétricas em uma exibição 2D não é a maneira ideal de obter entrada de texto do usuário.

As alternativas atuais para aproveitar o teclado do sistema por meio do Unity incluem:
* Usando comandos de fala para entrada (<b>Observação:</b> isso geralmente é propenso a falhas não encontrado no dicionário de palavras e não é adequado para entrada de senha)
* Criar um teclado que funciona no modo de exibição exclusivo aplicativos
