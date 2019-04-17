---
title: Usar o simulador de realidade mista do Windows
description: O simulador de realidade mista do Windows permite que você teste aplicativos de realidade misturada em seu computador sem um fone de ouvido Windows Mixed Reality envolvente.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows misto realidade, o simulador, testando
ms.openlocfilehash: 782cab85f163edd2afc4251210b7596c73dcc8b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590698"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Usar o simulador de realidade mista do Windows

O simulador de realidade mista do Windows permite que você teste aplicativos de realidade misturada em seu computador sem um fone de ouvido Windows Mixed Reality envolvente. Ele está disponível desde o Windows 10 Creators Update. O simulator é semelhante para o [HoloLens emulador](using-the-hololens-emulator.md), embora o simulador não usa uma máquina virtual. Aplicativos em execução no simulador executado na sua sessão de usuário da área de trabalho do Windows 10, assim como fariam se você estivesse usando um fone de ouvido envolvente. A entrada humana e ambiental que normalmente seria lidos pelos sensores em um fone de ouvido imersiva em vez disso, são simulados usando seu teclado, mouse ou controlador do Xbox. Aplicativos não precisam ser modificado para ser executado no simulador e não sabe o que eles não estão em execução em um fone de ouvido envolvente.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Habilitando o simulador de realidade mista do Windows

1. **Habilitar o modo de desenvolvedor** em Configurações -> atualização e segurança -> para desenvolvedores
2. Inicie o **Portal de realidade misturada** da área de trabalho
3. Se essa for a primeira vez que iniciar o portal, você precisará percorrer a experiência de instalação
   1. Clique em **começar**
   2. Clique em **concordo** para aceitar o contrato
   3. Clique em **configurado para simulação (para desenvolvedores)** para prosseguir com a instalação sem um dispositivo físico
   4. Clique em **configurar** para confirmar sua escolha
4. Clique o **para os desenvolvedores** botão no lado esquerdo do Portal de realidade mista
5. Mude a opção de alternância de simulação para **em**
   * Isso requer permissões de administrador e você deve aceitar a caixa de diálogo de controle de conta de usuário que é exibido

Agora, você deve estar executando com simulação!

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Implantação de aplicativos para o simulador de realidade misturada

Como o simulator é executado em seu computador local sem uma máquina Virtual, você pode simplesmente implantar seus aplicativos Windows Universal para o **computador Local** durante a depuração.

## <a name="basic-simulator-input"></a>Entrada de simulador básico

Controlar o simulador é muito semelhante a muitos jogos de vídeo 3D comuns e o [HoloLens emulador](using-the-hololens-emulator.md). Há opções de entrada disponíveis usando o teclado, mouse ou controlador do Xbox.

Você pode controlar o simulador, direcionando as ações de um usuário simulado usando um fone de ouvido imersivo. Suas ações mover o usuário simulado e fazer com que as interações com aplicativos que respondam como fariam em um fone de ouvido envolvente.
* **Percorrer para frente, novamente, à esquerda e logo** -usar W, D, S e um teclas do teclado ou o pen drive à esquerda em um controlador do Xbox.
* **Pesquisar, para baixo, esquerda e o botão direito do mouse** -clicar e arrastar o mouse, use as teclas de direção no teclado ou o pen drive à direita em um controlador do Xbox.
* **Pressionamento do botão de ação no controlador** – com o botão direito do mouse, pressione a tecla Enter no teclado ou usar o botão em um controlador do Xbox.
* **Home pressionamento do botão no controlador** – pressione a tecla do Windows ou F2 no teclado ou pressione o botão de B em um controlador do Xbox.
* **Movimentação de controlador para rolagem** - mantenha pressionada a tecla Alt, mantenha pressionado o botão direito do mouse, arraste o mouse para cima / para baixo, ou em um controlador do Xbox pressionado o gatilho certo e um botão para baixo e mover o pen drive certo para cima para baixo.

## <a name="tracked-controllers"></a>Controladores controladas

O simulador de realidade misturada pode simular até dois controladores de bolso movimento controladas. Habilitá-las usando os comutadores de alternância no Portal de realidade mista. Cada controlador simulado tem:
* Posição no espaço
* Botão Início
* Botão Menu
* Botão da alça
* Touchpad

## <a name="see-also"></a>Consulte também
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Avançadas de entrada do simulador de realidade misturada](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Mapeamento espacial no Unity](spatial-mapping-in-unity.md)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)
