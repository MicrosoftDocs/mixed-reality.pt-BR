---
title: Obter aplicativos para o HoloLens
description: Descreve a instalação de aplicativos para o HoloLens, por meio do Microsoft Store e do carregamento lateral.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Sideload, carga lateral, carga, armazenamento, UWP, aplicativo, instalação
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522545"
---
# <a name="get-apps-for-hololens"></a>Obter aplicativos para o HoloLens

Como um dispositivo Windows 10, o HoloLens dá suporte a muitos aplicativos UWP existentes da loja de aplicativos, bem como novos aplicativos criados especificamente para o HoloLens. Além desses, talvez você queira até mesmo [desenvolver](development-overview.md) e instalar seus próprios aplicativos ou aqueles de seus amigos!

## <a name="installing-apps"></a>Instalando aplicativos

Há três maneiras de instalar novos aplicativos em seu HoloLens. O método principal será instalar novos aplicativos da Windows Store. No entanto, você também pode instalar seus próprios aplicativos usando o portal do dispositivo ou implantando-os no Visual Studio.

### <a name="from-the-microsoft-store"></a>Da Microsoft Store
1. Execute um gesto de [cair](gestures.md#bloom) para abrir o [menu iniciar](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Selecione o aplicativo da loja e, em seguida, toque para colocar esse bloco em seu mundo.
3. Quando o aplicativo da loja for aberto, use a barra de pesquisa para procurar qualquer aplicativo desejado.
4. Selecione **obter** ou **instalar** na página do aplicativo (pode ser necessária uma compra).

### <a name="installing-an-application-package-with-the-device-portal"></a>Instalando um pacote de aplicativos com o portal do dispositivo
1. Estabeleça uma conexão do [portal do dispositivo](using-the-windows-device-portal.md) com o HoloLens de destino.
2. Navegue até a página **aplicativos** no painel de navegação esquerdo.
3. Em **pacote do aplicativo** , navegue até o arquivo. Appx associado ao seu aplicativo.
  >[!IMPORTANT]
  >Certifique-se de fazer referência a qualquer dependência associada e arquivos de certificado.

4. Clique em **ir**.

![Instalar formulário de aplicativo no portal de dispositivo do Windows no Microsoft HoloLens](images/deviceportal-appmanager.jpg)<br>
Usando o portal de dispositivos do Windows para instalar um aplicativo no HoloLens

### <a name="deploying-from-microsoft-visual-studio-2015"></a>Implantando do Microsoft Visual Studio 2015
1. Abra a solução do Visual Studio do seu aplicativo (arquivo. sln).
2. Abra as **Propriedades** do projeto.
3. Selecione a seguinte configuração de compilação: Mestre/x86/computador remoto.
4. Quando você seleciona computador remoto:
   * Verifique se o endereço aponta para o endereço IP WiFi do HoloLens.
   * Defina a autenticação como universal (protocolo não criptografado).
5. Crie sua solução.
6. Clique no botão **máquina remota** para implantar o aplicativo do seu computador de desenvolvimento em seu HoloLens. Se você já tiver uma compilação existente no HoloLens, selecione Sim para reinstalar essa nova versão.<br>
  ![Implantação de máquina remota para aplicativos para o Microsoft HoloLens no Visual Studio](images/vs2015-remotedeployment.jpg)<br>
7. O aplicativo será instalado e iniciado automaticamente no seu HoloLens.
