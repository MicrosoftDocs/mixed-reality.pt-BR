---
title: Solução de problemas do HoloLens
description: Etapas de solução de problemas para o Microsoft HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: problemas, Bug, solução de problemas, correção, ajuda, suporte, HoloLens
ms.openlocfilehash: 855bb0cafb0d3fba0d8d97c93d9415b51bcc2fb3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438277"
---
# <a name="hololens-troubleshooting"></a>Solução de problemas do HoloLens

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>Meu HoloLens está sem resposta ou não inicializa

Se o seu HoloLens não inicializar:
* Se os LEDs pelo botão de energia não acenderem ou apenas 1 LED piscar brevemente, talvez seja necessário cobrar seu HoloLens.
* Se os LEDs acenderem quando você pressionar o botão de energia, mas não conseguir ver nada nos monitores, mantenha o botão de energia até que todos os cinco LEDs do botão de energia sejam desligados.

Se seu HoloLens ficar congelado ou sem resposta:
* Desative seu HoloLens pressionando o botão de energia até que todos os cinco LEDs pelo botão de energia desliguem ou por 10 segundos se os LEDs não responderem. Pressione o botão de energia novamente para inicializar.

Se essas etapas não funcionarem:
* Você pode tentar [recuperar seu dispositivo](reset-or-recover-your-hololens.md).

## <a name="holograms-dont-look-good-or-are-moving-around"></a>Os hologramas não parecem bons ou estão se movendo.

Se os hologramas estiverem instáveis, com salto ou não estiverem corretos, tente uma destas correções:
* Limpe o visor do dispositivo e certifique-se de que nada esteja obstruindo os sensores.
* Verifique se há luz suficiente em sua sala.
* Tente percorrer e olhar seu lugar para que o HoloLens possa examiná-los mais completamente.
* Tente executar o aplicativo de calibragem. Ele Calibra o seu HoloLens para funcionar melhor para seus olhos. Acesse **configurações** > **sistema** > **utilitários**. Em calibragem, selecione **abrir calibragem**.
* Se você ainda tiver problemas depois de executar o aplicativo de calibragem, use o aplicativo de ajuste de sensor para ajustar os sensores do dispositivo. Acesse **configurações** > **sistema** > **utilitários**. Em ajuste do sensor, selecione **abrir ajuste do sensor**.

## <a name="hololens-doesnt-respond-to-my-gestures"></a>O HoloLens não responde aos meus gestos.

Para garantir que o HoloLens possa ver seus gestos, mantenha sua mão no quadro do gesto, que estende alguns pés em ambos os lados. Quando o HoloLens pode ver sua mão, o cursor será alterado de um ponto para um anel. Saiba mais sobre como usar [gestos](gaze-and-commit.md#composite-gestures).

Se o seu ambiente for muito escuro, o HoloLens poderá não ver sua mão, portanto, verifique se há muita luz suficiente.

Se o seu visor tiver impressões digitais ou borrar, use o pano de limpeza do microfiber que veio com o HoloLens para limpar o visor com cuidado.

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>O HoloLens não responde aos meus comandos de voz.

Se a Cortana não estiver respondendo aos seus comandos de voz, verifique se a Cortana está ativada. Na lista todos os aplicativos, selecione o menu Cortana > > notebook > configurações para fazer alterações. Para saber mais sobre o que você pode dizer, consulte usar sua voz para controlar o HoloLens.

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>Não posso colocar hologramas nem Ver os hologramas que fiz anteriormente.

Se o HoloLens não puder mapear ou carregar seu espaço, ele entrará no modo limitado e você não poderá colocar os hologramas ou Ver os hologramas que você colocou. Tente o seguinte:
* Verifique se há luz suficiente em seu ambiente para que o HoloLens possa ver e mapear o espaço.
* Verifique se você está conectado a uma rede Wi-Fi. Se você não estiver conectado ao Wi-Fi, o HoloLens não poderá identificar e carregar um espaço conhecido.
* Se você precisar criar um novo espaço, conecte-se ao Wi-Fi e reinicie o HoloLens.
* Para ver se o espaço correto está ativo ou para carregar manualmente um espaço, vá para **configurações** > **espaço**de > do **sistema** .
* Se o espaço correto for carregado e você ainda tiver problemas, o espaço poderá estar corrompido. Para corrigir isso, selecione o espaço e, em seguida, selecione remover. Depois que o espaço for removido, o HoloLens começará a mapear seus arredores e criará um novo espaço.

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>Meu HoloLens frequentemente entra no modo limitado ou mostra uma mensagem de "rastreamento perdido".

Se o dispositivo costuma mostrar uma mensagem "modo limitado" ou "controle perdido", tente as sugestões dos [meus hologramas não parecem boas ou estão se movendo](#holograms-dont-look-good-or-are-moving-around).

## <a name="my-hololens-cant-tell-what-space-im-in"></a>Meu HoloLens não pode saber em que espaço estou.

Se o seu HoloLens não puder identificar e carregar automaticamente o espaço em que você está, verifique se você está conectado ao Wi-Fi, se há muita luz na sala e não houve nenhuma alteração importante no ambiente. Você também pode carregar um espaço manualmente ou gerenciar seus espaços acessando **configurações** > **espaço**de > do **sistema** .

## <a name="im-getting-a-low-disk-space-error"></a>Estou recebendo um erro de "pouco espaço em disco".

Você precisará liberar espaço de armazenamento seguindo um ou mais destes procedimentos:
* Exclua alguns espaços não utilizados. Vá para **configurações** > **espaço**de > do **sistema** , selecione um espaço que não seja mais necessário e, em seguida, selecione **remover**.
* Remova alguns dos hologramas que você colocou.
* Exclua algumas imagens e vídeos no aplicativo fotos.
* Desinstale alguns aplicativos do seu HoloLens. Na lista todos os aplicativos, toque e mantenha o aplicativo que você deseja desinstalar e, em seguida, selecione **desinstalar**.

## <a name="my-hololens-cant-create-a-new-space"></a>Meu HoloLens não pode criar um novo espaço.

O problema mais provável é que você está ficando com pouco espaço de armazenamento. Tente uma das [dicas acima](#im-getting-a-low-disk-space-error) para liberar espaço em disco.
