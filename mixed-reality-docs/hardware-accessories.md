---
title: Acessórios de hardware
description: Descreve os tipos de Acessórios disponíveis para uso com o HoloLens e realidade mista do Windows e como configurá-los.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: como fazer, Acessórios, bluetooth, bt, controlador, gamepad, xbox, clicker
ms.openlocfilehash: c25f849cbf05a78ba2fe7118dbe160d05e0f5e3f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590947"
---
# <a name="hardware-accessories"></a>Acessórios de hardware

Suportam a dispositivos Windows Mixed Reality Acessórios. Você vai emparelhar Acessórios com suporte para o HoloLens usando Bluetooth, enquanto você pode usar o Bluetooth ou USB para par tem suporte em Acessórios para um fone de ouvido imersivo via PC ao qual ele está conectado.

Dois cenários comuns para usar os acessórios com o HoloLens são como substitutos para conexão sem fio toque gesto e o teclado virtual. Para isso, os dois Acessórios mais comuns são as **HoloLens Clicker** e **teclados Bluetooth**. Microsoft HoloLens inclui um rádio Bluetooth 4.1 e suporta [HID Bluetooth](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29) e [GATT Bluetooth](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29) perfis.

Fones imersivos em exposição Windows Mixed Reality exigem Acessórios para entrada além [olhares](gaze.md) e [voz](voice-input.md). Acessórios com suporte incluem **teclado e mouse**, **gamepad**, e  **[controladores de movimento](motion-controllers.md)**.

## <a name="pairing-bluetooth-accessories"></a>Emparelhamento Acessórios do Bluetooth

Emparelhamento de um periféricos de Bluetooth com o Microsoft HoloLens é semelhante ao emparelhamento de um periféricos de Bluetooth com um Windows 10 desktop ou dispositivo móvel:
1. No Menu Iniciar, abra o **configurações** aplicativo
2. Vá para **dispositivos**
3. Ativar o rádio Bluetooth, se ele estiver desativado usando a opção de controle deslizante
4. Coloque o dispositivo Bluetooth no modo de emparelhamento. Isso varia de um dispositivo para o dispositivo. Na maioria dos dispositivos Bluetooth, isso é feito pressionando e mantendo um ou mais botões.
5. Aguarde até que o nome do dispositivo para aparecer na lista de dispositivos Bluetooth. Quando ele, selecione o dispositivo e selecione o **par** botão. Se você tiver muitos dispositivos Bluetooth próximos a você talvez precise rolar para a parte inferior da lista de dispositivos Bluetooth para ver o dispositivo que você está tentando emparelhar.
6. Quando emparelhamento periféricos de Bluetooth com capacidade de entrada (por exemplo: Teclados Bluetooth), um dígito de 6 ou um pin de 8 dígitos pode ser exibido. Certifique-se de digitar o pin no periférico e, em seguida, pressione enter para emparelhamento completa com o Microsoft HoloLens.

## <a name="motion-controllers"></a>Controladores de movimento

Windows Mixed Reality [controladores de movimento](motion-controllers.md) são suportados pelo fones imersivos em exposição, mas não o HoloLens. Esses controladores oferecem controle preciso e responsivo de movimentação em seu campo de exibição usando os sensores o Headset imersivo, que significa que não é necessário para instalar o hardware nas paredes em seu espaço de. Cada controlador apresenta vários métodos de entrada.

![Controladores de movimento de realidade mista do Windows](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens Clicker

O HoloLens Clicker é o primeiro dispositivo periférico criado especificamente para o HoloLens e está incluído com a edição de desenvolvimento HoloLens. O HoloLens Clicker permite que um usuário clique e role com o movimento de mão mínima como uma substituição para o gesto de toque de ar. Não é uma substituição para todos os [gestos](gestures.md). Por exemplo, [bloom](gestures.md#bloom) e [redimensionar ou mover](gestures.md#composite-gestures) movimentos de mão de usar gestos. O HoloLens clicker é um dispositivo de sensor de orientação com um botão simples. Conecta-se para o HoloLens usando Bluetooth baixa energia (BTLE).

![O HoloLens Clicker](images/hololens-clicker-500px.jpg)

Para selecionar um [holograma](hologram.md)contemplá-la e, em seguida, clique em. Orientação do clicker não importa para esta operação. Para rolar ou panorâmica, clique e mantenha, gire o Clicker para cima/para baixo ou da esquerda/direita. Durante a rolagem, você atingirá a velocidade mais rápida com tão pouco quanto + /-15° de rotação de pulso. Movendo mais não rolará qualquer um com mais rapidez.

Há dois LEDs dentro de Clicker:
* O LED branco indica se o dispositivo é emparelhamento (piscando) ou cobrar (estável)
* O âmbar LED indica que o dispositivo tem pouca bateria (piscando) ou sofreu uma falha (estável)

Você pode esperar 2 semanas ou mais de uso normal em carga total (ou seja, 2 a 3 horas em um carregador de parede). Quando a bateria está fraca, o âmbar que LED piscará 10 vezes em um período de 5 segundos, se você pressionar o botão ou wake-lo do modo de suspensão. O âmbar que LED piscará mais rapidamente ao longo de um período de 5 segundos se seu Clicker está no modo de bateria criticamente baixo.

## <a name="bluetooth-keyboards"></a>Teclados Bluetooth

Teclados do idioma inglês Bluetooth Qwerty podem ser emparelhados e usada em qualquer lugar, que você pode usar o teclado holográfico. Obtendo um teclado de qualidade faz uma diferença, portanto, é recomendável o [Microsoft Keyboard dobráveis Universal](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) ou o [área de trabalho do Microsoft Designer Bluetooth](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001).

## <a name="bluetooth-gamepads"></a>Bluetooth gamepads

Você pode usar um controlador com aplicativos e jogos que habilitar o suporte de gamepad especificamente. Gamepads não pode ser usado para controlar a interface do usuário HoloLens.

Controladores de sem fio do Xbox que vêm com o Xbox um S ou vendido como Acessórios para o recurso do Xbox um S conectividade Bluetooth que permitem que eles sejam utilizados com o HoloLens e fones imersivos em exposição. O controlador do Xbox sem fio [devem ser atualizadas](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) antes que ele pode ser usado com o HoloLens.

Outras marcas de Bluetooth gamepads podem trabalhar com dispositivos de realidade mista do Windows, mas suporte variam de acordo com o aplicativo.

## <a name="other-bluetooth-accessories"></a>Outros acessórios do Bluetooth

Desde que o periférico dá suporte a perfis de HID Bluetooth ou GATT, ele poderá ser emparelhados com o HoloLens. Outros dispositivos HID Bluetooth e GATT além de teclado, mouse e o HoloLens Clicker podem exigir um aplicativo complementar no Microsoft HoloLens estar totalmente funcionais.

Periféricos sem suporte incluem:
* Não há suporte para periféricos nos perfis de áudio de Bluetooth.
* Dispositivos de áudio de Bluetooth como alto-falantes e fones de ouvido são exibidos como disponíveis no aplicativo configurações, mas não há suporte para ser usado com o Microsoft HoloLens como um ponto de extremidade de áudio.
* Habilitado para Bluetooth e telefones não têm suporte para serem combinados e usados para a transferência de arquivo.

## <a name="unpairing-a-bluetooth-peripheral"></a>Desemparelhamento um periféricos de Bluetooth
1. No Menu Iniciar, abra o **configurações** aplicativo
2. Vá para **dispositivos**
3. Ativar o rádio Bluetooth, se ele estiver desativado
4. Encontrar seu dispositivo na lista de dispositivos Bluetooth disponíveis
5. Selecione seu dispositivo na lista e, em seguida, selecione a **remover** botão

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>Desabilitando o Bluetooth no Microsoft HoloLens

Isso desativar os componentes de RF do rádio Bluetooth e desabilitar todas as funcionalidades de Bluetooth em Microsoft HoloLens.
1. No Menu Iniciar, abra o **configurações** aplicativo
2. Vá para **dispositivos**
3. Mova a opção de controle deslizante para Bluetooth para a posição desligado
