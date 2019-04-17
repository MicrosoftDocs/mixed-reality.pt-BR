---
title: Obtenha aplicativos para o HoloLens
description: Descreve a instalação de aplicativos para o HoloLens, tanto por meio da Microsoft Store e o sideload.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: fazer sideload, carga de lado, sideload, store, uwp, aplicativo, instalar
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589083"
---
# <a name="get-apps-for-hololens"></a>Obtenha aplicativos para o HoloLens

Como um dispositivo Windows 10, HoloLens, dá suporte a muitos aplicativos UWP na loja de aplicativos, bem como novos aplicativos criados especificamente para o HoloLens. Sobre eles, você talvez ainda queira [desenvolver](development-overview.md) e instalar seus próprios aplicativos ou aqueles dos seus amigos!

## <a name="installing-apps"></a>Instalação de aplicativos

Há três maneiras de instalar novos aplicativos em sua HoloLens. O método primário será instalar novos aplicativos da Store do Windows. No entanto, você também pode instalar seus próprios aplicativos usando o Portal de dispositivos ou implantá-los a partir do Visual Studio.

### <a name="from-the-microsoft-store"></a>De que a Microsoft Store
1. Executar uma [bloom](gestures.md#bloom) gesto para abrir o [Menu Iniciar](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Selecione o aplicativo Store e, em seguida, toque para colocar esse bloco no seu mundo.
3. Depois que o aplicativo Store é aberta, use a barra de pesquisa para procurar qualquer aplicativo desejado.
4. Selecione **Obtenha** ou **instalar** na página do aplicativo (uma compra pode ser necessária).

### <a name="installing-an-application-package-with-the-device-portal"></a>Instalar um pacote de aplicativos com o Portal do dispositivo
1. Estabelecer uma conexão de [Portal do dispositivo](using-the-windows-device-portal.md) para o destino HoloLens.
2. Navegue até a **aplicativos** página no painel de navegação à esquerda.
3. Sob **pacote do aplicativo** navegue até o arquivo. AppX associado ao seu aplicativo.
  >[!IMPORTANT]
  >Certifique-se de fazer referência a quaisquer arquivos associados de dependência e o certificado.

4. Clique em **acesse**.

![Instalar o formulário do aplicativo no Windows Device Portal no Microsoft HoloLens](images/deviceportal-appmanager.jpg)<br>
Usando o Windows Device Portal para instalar um aplicativo em HoloLens

### <a name="deploying-from-microsoft-visual-studio-2015"></a>Implantação do Microsoft Visual Studio 2015
1. Abra a solução do Visual Studio do seu aplicativo (arquivo. sln).
2. Abra o projeto **propriedades** .
3. Selecione a configuração de compilação a seguir: Computador mestre/x86/remoto.
4. Quando você seleciona o computador remoto:
   * Verifique se os pontos de endereço para o endereço de IP de WiFi dos HoloLens.
   * Definir a autenticação universal (protocolo não criptografado).
5. Compile sua solução.
6. Clique o **máquina remota** botão para implantar o aplicativo do seu computador de desenvolvimento para o HoloLens. Se você já tiver uma compilação existente no HoloLens, selecione Sim para reinstalar essa versão mais recente.<br>
  ![Implantação de máquina remota para os aplicativos Microsoft HoloLens no Visual Studio](images/vs2015-remotedeployment.jpg)<br>
7. O aplicativo será instalar e inicializar no seu HoloLens automaticamente.
