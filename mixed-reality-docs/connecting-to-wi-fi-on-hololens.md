---
title: Conectar-se ao Wi-Fi em HoloLens
description: Instruções sobre como se conectar à internet sem fio com o HoloLens e como identificar o endereço IP do dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, wifi, wireless, internet, ip, ip address
ms.openlocfilehash: 0440c3dad48d73db51e7d730e79d6eb1e74a5694
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590816"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>Conectar-se ao Wi-Fi em HoloLens

HoloLens contém um 802.11ac-capaz, 2 x 2 rádio de Wi-Fi. Conectar o HoloLens a uma rede Wi-Fi é semelhante a conectar um dispositivo Windows 10 Desktop ou Mobile a uma rede Wi-Fi.

![Configurações de Wi-Fi HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>Conectar a uma rede Wi-Fi em HoloLens

1. [Bloom](gestures.md#bloom) para o **iniciar** menu.
2. Selecione o **as configurações** aplicativo de início ou do **todos os aplicativos** lista à direita do menu Iniciar.
3. O **configurações** aplicativo será colocado automaticamente na sua frente.
4. Selecione **rede e Internet**.
5. Verifique se o Wi-Fi está ativado.
6. Selecione uma rede Wi-Fi na lista.
7. Digite a senha de rede Wi-Fi (se necessário).

## <a name="disabling-wi-fi-on-hololens"></a>Desabilitando o Wi-Fi em HoloLens

### <a name="using-the-settings-app-on-hololens"></a>Usando o aplicativo de configurações em HoloLens

1. [Bloom](gestures.md#bloom) para o **iniciar** menu.
2. Selecione o **as configurações** aplicativo de início ou do **todos os aplicativos** lista à direita do menu Iniciar.
3. O **configurações** aplicativo será colocado automaticamente na sua frente.
4. Selecione **rede e Internet**.
5. Selecione a opção de controle deslizante de Wi-Fi para movê-lo para a posição "Desativado". Isso irá desativar os componentes de RF do rádio Wi-Fi e desabilitar todas as funcionalidades de Wi-Fi em HoloLens. 

    >[!WARNING]
    >HoloLens não poderão carregar automaticamente seus [espaços](environment-considerations-for-hololens.md#spaces) quando a opção de Wi-Fi está desabilitada.
    
6. Mova a opção de controle deslizante para a posição de "On" para ativar a opção de Wi-Fi e restaurar a funcionalidade de Wi-Fi no Microsoft HoloLens. O estado de rádio Wi-Fi selecionado ("ligado" de "Desativado") será mantido entre as reinicializações.

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>Como confirmar que você está conectado a uma rede Wi-Fi

1. [Bloom](gestures.md#bloom) para abrir o **iniciar** menu.
2. Observe a parte superior esquerda do menu Iniciar para o status de Wi-Fi. O estado de Wi-Fi e o SSID da rede conectada serão mostrados.

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>Identificar o endereço IP do seu HoloLens na rede Wi-Fi

### <a name="using-the-settings-app"></a>Usando o aplicativo de configurações

1. [Bloom](gestures.md#bloom) para o **iniciar** menu.
2. Selecione o **as configurações** aplicativo de início ou do **todos os aplicativos** lista à direita do menu Iniciar.
3. O **configurações** aplicativo será colocado automaticamente na sua frente.
4. Selecione **rede e Internet**.
5. Role para baixo até abaixo da lista de redes Wi-Fi disponíveis e selecione **propriedades de Hardware**.

    ![Propriedades de hardware nas configurações de Wi-Fi](images/wifi-hololens-hwdetails.jpg)

O endereço IP será mostrado ao lado **endereço IPv4**.

### <a name="using-cortana"></a>Usando o Cortana

Dizer "*Ei Cortana, o que é meu endereço IP?*" e Cortana exibirá e ler seu endereço IP.

### <a name="using-windows-device-portal"></a>Usando o Windows Device Portal

1. Abra o [portal do dispositivo](using-the-windows-device-portal.md#networking) em um navegador da web em seu computador.
2. Navegue até a **rede** seção.

Seu endereço IP e outras informações de rede serão exibidos lá. Esse método permite fácil copiar e colar do endereço IP em seu computador de desenvolvimento.
