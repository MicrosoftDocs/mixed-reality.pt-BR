---
title: Conectando-se ao Wi-Fi no HoloLens
description: Instruções sobre como se conectar à Internet sem fio com o HoloLens e como identificar o endereço IP do dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, WiFi, sem fio, Internet, IP, endereço IP
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670112"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>Conectando-se ao Wi-Fi no HoloLens

O HoloLens contém uma rádio Wi-Fi com capacidade para AC 802.11, 2x2. Conectar o HoloLens a uma rede Wi-Fi é semelhante a conectar um dispositivo Windows 10 desktop ou móvel a uma rede Wi-Fi.

![Configurações de Wi-Fi do HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>Conectando-se a uma rede Wi-Fi no HoloLens

1. [Cair](gestures.md#bloom) para o menu **Iniciar** .
2. Selecione o aplicativo **configurações** em iniciar ou na lista **todos os aplicativos** à direita do menu iniciar.
3. O aplicativo de **configurações** será colocado automaticamente na frente de você.
4. Selecione **rede & Internet**.
5. Verifique se o Wi-Fi está ativado.
6. Selecione uma rede Wi-Fi na lista.
7. Digite a senha da rede Wi-Fi (se necessário).

## <a name="disabling-wi-fi-on-hololens"></a>Desabilitando Wi-Fi no HoloLens

### <a name="using-the-settings-app-on-hololens"></a>Usando o aplicativo de configurações no HoloLens

1. [Cair](gestures.md#bloom) para o menu **Iniciar** .
2. Selecione o aplicativo **configurações** em iniciar ou na lista **todos os aplicativos** à direita do menu iniciar.
3. O aplicativo de **configurações** será colocado automaticamente na frente de você.
4. Selecione **rede & Internet**.
5. Selecione a opção de controle deslizante Wi-Fi para movê-la para a posição "off". Isso desligará os componentes RF da rádio Wi-Fi e desabilitará toda a funcionalidade de Wi-Fi no HoloLens. 

    >[!WARNING]
    >O HoloLens não poderá carregar seus [espaços](environment-considerations-for-hololens.md#WiFi fingerprint considerations) automaticamente quando o Wi-Fi Radio estiver desabilitado.
    
6. Mova o controle deslizante para a posição "on" para ativar o rádio Wi-Fi e restaurar a funcionalidade Wi-Fi no Microsoft HoloLens. O estado de rádio Wi-Fi selecionado ("on" de "off") persistirá entre as reinicializações.

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>Como confirmar que você está conectado a uma rede Wi-Fi

1. [Incair](gestures.md#bloom) para abrir o menu **Iniciar** .
2. Examine a parte superior esquerda do menu Iniciar para status de Wi-Fi. O estado de Wi-Fi e o SSID da rede conectada serão mostrados.

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>Identificando o endereço IP do seu HoloLens na rede Wi-Fi

### <a name="using-the-settings-app"></a>Usando o aplicativo configurações

1. [Cair](gestures.md#bloom) para o menu **Iniciar** .
2. Selecione o aplicativo **configurações** em iniciar ou na lista **todos os aplicativos** à direita do menu iniciar.
3. O aplicativo de **configurações** será colocado automaticamente na frente de você.
4. Selecione **rede & Internet**.
5. Role para baixo até a lista de redes Wi-Fi disponíveis e selecione **Propriedades de hardware**.

    ![Propriedades de hardware nas configurações de Wi-Fi](images/wifi-hololens-hwdetails.jpg)

O endereço IP será mostrado ao lado do **endereço IPv4**.

### <a name="using-cortana"></a>Usando a Cortana

Diga "*Ei Cortana, qual é meu endereço IP?* " e a Cortana exibirá e lerá seu endereço IP.

### <a name="using-windows-device-portal"></a>Usando o portal de dispositivos do Windows

1. Abra o [portal do dispositivo](using-the-windows-device-portal.md#networking) em um navegador da Web em seu computador.
2. Navegue até a seção **rede** .

Seu endereço IP e outras informações de rede serão exibidos lá. Esse método permite copiar e colar facilmente o endereço IP no seu computador de desenvolvimento.
