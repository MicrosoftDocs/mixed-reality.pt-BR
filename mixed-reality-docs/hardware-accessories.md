---
title: Acessórios de hardware
description: Descreve os tipos de acessórios disponíveis para uso com o HoloLens e a realidade mista do Windows e como configurá-los.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: instruções, acessórios, Bluetooth, BT, controlador, gamepad, clico, Xbox
ms.openlocfilehash: 566d4217fb674057e1dc3d9791b247185bf61d32
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435151"
---
# <a name="hardware-accessories"></a>Acessórios de hardware

Os dispositivos Windows Mixed Reality dão suporte a acessórios. Você emparelhará os acessórios com suporte para o HoloLens usando o Bluetooth, enquanto você pode usar Bluetooth ou USB para emparelhar os acessórios com suporte para um headset de imersão por meio do PC ao qual ele está conectado.

Dois cenários comuns de uso de acessórios com o HoloLens são como substitutos para o gesto de toque do ar e o teclado virtual. Para isso, os dois acessórios mais comuns são o **clicador de HoloLens** e os **teclados Bluetooth**. O Microsoft HoloLens inclui um rádio Bluetooth 4,1 e dá suporte a perfis Bluetooth [HID](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29) e [Bluetooth GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29) .

Os headsets de imersão de realidade mista do Windows exigem acessórios para entrada além de [olhar](gaze-and-commit.md) e [voz](voice-input.md). Os acessórios com suporte incluem **teclado e mouse**, **gamepad**e **[controladores de movimento](motion-controllers.md)** .

## <a name="pairing-bluetooth-accessories"></a>Emparelhamento de acessórios Bluetooth

Emparelhar um periférico Bluetooth com o Microsoft HoloLens é semelhante a emparelhar um periférico Bluetooth com um dispositivo Windows 10 desktop ou móvel:
1. No menu Iniciar, abra o aplicativo **configurações**
2. Ir para **dispositivos**
3. Ligue o rádio Bluetooth se ele estiver desligado usando a opção Slider
4. Coloque seu dispositivo Bluetooth no modo de emparelhamento. Isso varia de dispositivo para dispositivo. Na maioria dos dispositivos Bluetooth, isso é feito pressionando e segurando um ou mais botões.
5. Aguarde até que o nome do dispositivo apareça na lista de dispositivos Bluetooth. Quando tiver, selecione o dispositivo e, em seguida, selecione o botão **emparelhar** . Se você tiver muitos dispositivos Bluetooth próximos, talvez seja necessário rolar para a parte inferior da lista de dispositivos Bluetooth para ver o dispositivo que você está tentando emparelhar.
6. Ao emparelhar periféricos Bluetooth com capacidade de entrada (por exemplo: teclados Bluetooth), um PIN de seis dígitos ou 8 dígitos pode ser exibido. Certifique-se de digitar esse PIN no periférico e pressione ENTER para concluir o emparelhamento com o Microsoft HoloLens.

## <a name="motion-controllers"></a>Controladores de movimento

Os controladores de [movimento](motion-controllers.md) de realidade mista do Windows têm suporte por headsets de imersão, mas não com o HoloLens. Esses controladores oferecem acompanhamento preciso e responsivo de movimento em seu campo de exibição usando os sensores no headset de imersão, o que significa que não há necessidade de instalar o hardware nas paredes no seu espaço. Cada controlador apresenta vários métodos de entrada.

![Controladores de movimento do Windows Mixed Reality](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>Clicador de HoloLens

O clicador de HoloLens é o primeiro dispositivo periférico criado especificamente para o HoloLens e está incluído na edição de desenvolvimento do HoloLens. O clicador de HoloLens permite que um usuário clique e role com o movimento mínimo para o gesto de toque de ar. Não é uma substituição para todos os [gestos](gaze-and-commit.md#composite-gestures). Por exemplo, [incair](system-gesture.md#bloom) e [redimensionar ou mover](gaze-and-commit.md#composite-gestures) gestos usam movimentos de mão. O clicador de HoloLens é um dispositivo de sensor de orientação com um botão simples. Ele se conecta ao HoloLens usando o Bluetooth de baixa energia (BTLE).

![O clicador de HoloLens](images/hololens-clicker-500px.jpg)

Para selecionar um [holograma](hologram.md), olhar-o e, em seguida, clique em. A orientação do clico não importa para esta operação. Para rolar ou deslocar, clique e segure e, em seguida, gire o clique para cima/para baixo ou para a esquerda/direita. Durante a rolagem, você alcançará a velocidade mais rápida com menos de +/-15 ° de rotação de pulso. Mover mais não fará a rolagem mais rapidamente.

Há dois LEDs dentro do clicador:
* O LED branco indica se o dispositivo está emparelhando (piscando) ou carregando (sólido)
* O LED âmbar indica que o dispositivo tem bateria fraca (piscando) ou sofreu uma falha (sólida)

Você pode esperar duas semanas ou mais de uso regular em um encargo total (ou seja, 2-3 horas em um carregador de parede). Quando a bateria estiver baixa, o LED âmbar piscará 10 vezes em um período de 5 segundos se você pressionar o botão ou ativá-lo da suspensão. O LED âmbar piscará mais rapidamente em um período de 5 segundos se o seu clicador estiver em um modo de bateria muito baixo.

## <a name="bluetooth-keyboards"></a>Teclados Bluetooth

Os teclados Bluetooth do idioma inglês QWERTY podem ser emparelhados e usados em qualquer lugar que você possa usar o Holographic Keyboard. Obter um teclado de qualidade faz uma diferença, portanto, recomendamos o [teclado Microsoft Universal dobrável](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) ou a [área de trabalho do Microsoft designer Bluetooth](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001).

## <a name="bluetooth-gamepads"></a>Gamepads Bluetooth

Você pode usar um controlador com aplicativos e jogos que habilitam especificamente o suporte a gamepad. Os gamepads não podem ser usados para controlar a interface do usuário do HoloLens.

Os controladores sem fio do Xbox que acompanham o Xbox One ou vendidos como acessórios para a conectividade Bluetooth um recurso do Xbox One, que os habilitam a serem usados com o HoloLens e o headsets de imersão. O controlador sem fio do Xbox [deve ser atualizado](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) para que possa ser usado com o HoloLens.

Outras marcas de gamepads Bluetooth podem funcionar com dispositivos Windows Mixed Reality, mas o suporte irá variar por aplicativo.

## <a name="other-bluetooth-accessories"></a>Outros acessórios Bluetooth

Contanto que o periférico dê suporte aos perfis HID ou GATT Bluetooth, ele poderá emparelhar com o HoloLens. Outros dispositivos Bluetooth HID e GATT além do teclado, mouse e o clicador do HoloLens podem exigir que um aplicativo complementar no Microsoft HoloLens seja totalmente funcional.

Os periféricos sem suporte incluem:
* Não há suporte para os periféricos nos perfis de áudio Bluetooth.
* Dispositivos de áudio Bluetooth, como alto-falantes e headsets, podem aparecer como disponíveis no aplicativo configurações, mas não têm suporte para serem usados com o Microsoft HoloLens como um ponto de extremidade de áudio.
* Telefones e computadores habilitados para Bluetooth não têm suporte para serem emparelhados e usados para transferência de arquivos.

## <a name="unpairing-a-bluetooth-peripheral"></a>Desemparelhando um periférico Bluetooth
1. No menu Iniciar, abra o aplicativo **configurações**
2. Ir para **dispositivos**
3. Ligue o rádio Bluetooth se ele estiver desativado
4. Localize seu dispositivo na lista de dispositivos Bluetooth disponíveis
5. Selecione o dispositivo na lista e, em seguida, selecione o botão **remover**

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>Desabilitando o Bluetooth no Microsoft HoloLens

Isso desligará os componentes RF do rádio Bluetooth e desabilitará toda a funcionalidade do Bluetooth no Microsoft HoloLens.
1. No menu Iniciar, abra o aplicativo **configurações**
2. Ir para **dispositivos**
3. Mover a opção de controle deslizante para Bluetooth para a posição desativado
