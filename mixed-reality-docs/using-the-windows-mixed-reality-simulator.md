---
title: Usando o simulador de realidade mista do Windows
description: O simulador de realidade mista do Windows permite que você teste aplicativos de realidade misturados em seu computador sem um headset de imersão de realidade mista do Windows.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Realidade mista do Windows, simulador, teste
ms.openlocfilehash: a7cbd5b5ca1c0ed0e4f81715d337d5eec68117f0
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580699"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Usando o simulador de realidade mista do Windows

O simulador de realidade mista do Windows permite que você teste aplicativos de realidade misturados em seu computador sem um headset de imersão de realidade mista do Windows. Ele está disponível a partir da atualização do Windows 10 para criadores. O simulador é semelhante ao [emulador do HoloLens](using-the-hololens-emulator.md), embora o simulador não use uma máquina virtual. Os aplicativos em execução no simulador são executados em sua sessão de usuário do Windows 10 desktop, assim como fariam se você estivesse usando um headset de imersão. A entrada humana e ambiental que normalmente seria lida pelos sensores em um headset de imersão é, em vez disso, simulada usando o teclado, o mouse ou o controlador Xbox. Os aplicativos não precisam ser modificados para serem executados no simulador e não sabem que não estão sendo executados em um headset de imersão.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Habilitando o simulador de realidade mista do Windows

1. **Habilitar o modo de desenvolvedor** de configurações-> Update e Security-> para desenvolvedores
2. Inicie o **portal de realidade misturada** na área de trabalho
3. Se esta for a primeira vez que você inicia o portal, você precisará passar pela experiência de instalação
   1. Clique em **introdução**
   2. Clique em **concordo** para aceitar o contrato
   3. Clique em **Configurar para simulação (para desenvolvedores)** para prosseguir com a instalação sem um dispositivo físico
   4. Clique em **Configurar** para confirmar sua escolha
4. Clique no botão **para desenvolvedores** no lado esquerdo do portal da realidade misturada
5. Ative a opção de alternância de simulação para **ativado**
   * Habilitar a simulação instala e habilita o controlador 6 DOF simulado à esquerda por padrão.  Antes do Windows 10 ser 2019 atualização, a instalação de um controlador simulado de 6 DOF requer permissões de administrador.  Você deve aceitar a caixa de diálogo controle de conta de usuário se ela for exibida.

Agora você deve estar executando com a simulação!

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Implantando aplicativos no simulador de realidade misturada

Como o simulador é executado em seu PC local sem uma máquina virtual, você pode simplesmente implantar seus aplicativos universais do Windows no **computador local** durante a depuração.

## <a name="basic-simulator-input"></a>Entrada do simulador básico

Controlar o simulador é muito semelhante a muitos jogos de vídeo 3D comuns e ao emulador do [HoloLens](using-the-hololens-emulator.md). Há opções de entrada disponíveis usando o teclado, o mouse ou o controle Xbox.

Você controla o simulador direcionando as ações de um usuário simulado utilizando um headset de imersão. Suas ações movem o usuário simulado e causam interações com aplicativos que respondem como em um headset de imersão.
* **Andar para a frente, para trás, para a esquerda e para a direita** – use as teclas W, A, S e D no teclado ou o joystick esquerdo em um controle Xbox.
* **Olhar para cima, para baixo, para a esquerda e para a direita** – clique e arraste o mouse, use as teclas de seta no teclado ou o joystick direito em um controle Xbox.
* **Pressione o botão de ação no controlador** -clique com o botão direito do mouse, pressione a tecla Enter no teclado ou use o botão a em um controlador Xbox.
* **Pressione o botão página inicial no controlador** -pressione a tecla Windows ou a tecla F2 no teclado ou pressione o botão B em um controlador Xbox.
* **Movimentação do controlador para rolagem** – mantenha a tecla Alt pressionada, mantenha o botão direito do mouse e arraste o mouse para cima/para baixo ou em um controlador Xbox Mantenha o gatilho direito e um botão abaixo e mova o botão direito para cima e para baixo.

## <a name="tracked-controllers"></a>Controladores rastreados

O simulador de realidade misturada pode simular até dois controladores de movimento acompanhados por mão. Habilite-os usando as opções de alternância no portal de realidade misturada. Cada controlador simulado tem:
* Posição e orientação no espaço
* Botão Início
* Botão Menu
* Botão de fixação
* Touchpad
* Thumbstick
* Nível da bateria

## <a name="see-also"></a>Consulte também
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Entrada do simulador de realidade mista avançada](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Mapeamento espacial no Unity](spatial-mapping-in-unity.md)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)
