---
title: Solução de problemas do HoloLens
description: Etapas de solução de problemas para o Microsoft HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: problemas de bugs, solucionar problemas, corrigir, ajuda, suporte, HoloLens
ms.openlocfilehash: 7b7a32a9a358ff75b2675d265445d9ef1acc1b9e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589087"
---
# <a name="hololens-troubleshooting"></a>Solução de problemas do HoloLens

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>Meu HoloLens não está respondendo ou não inicializar

Se seu HoloLens não inicializam:
* Se os LEDs pelo botão liga/desliga não leve, disponível ou apenas 1 brevemente o LED pisca, talvez seja necessário a cobrar o HoloLens.
* Se os LEDs acendem quando você pressiona o botão de energia, mas não é possível ver nada sobre o exibe, mantenha o botão de energia até que todas as 5 os LEDs pelo botão de energia desligue.

Se seu HoloLens ficar congelado ou não responder:
* Desative o HoloLens, pressionando o botão de energia até que todas as 5 os LEDs pelo botão liga/desliga em si, ou desativar por 10 segundos se os LEDs estão respondendo. Pressione o botão de energia novamente a inicialização.

Se essas etapas não funcionam:
* Você pode tentar [recuperando seu dispositivo](reset-or-recover-your-hololens.md).

## <a name="holograms-dont-look-good-or-are-moving-around"></a>Hologramas não parecem bons ou estiver movendo ao redor.

Se seu hologramas estiver instável, agitadas ou não parecem corretas, tente uma dessas correções:
* Limpa o visor e do seu dispositivo e verifique se há algo que impeça os sensores.
* Verifique se que há luz suficiente na sua sala.
* Tente andar e observando arredores HoloLens então poderá verificá-los mais completamente.
* Tente executar o aplicativo de calibragem. Ele Calibra seu HoloLens funcionará melhor para seus olhos. Vá para **as configurações** > **sistema** > **utilitários**. Em calibração, selecione **calibragem aberto**.
* Se você ainda estiver tendo problemas depois de executar o aplicativo de calibragem, use o aplicativo de Sensor de ajuste para ajustar seus sensores de dispositivo. Vá para **as configurações** > **sistema** > **utilitários**. Em ajuste de Sensor, selecione **abrir Opções de ajuste de Sensor**.

## <a name="hololens-doesnt-respond-to-my-gestures"></a>HoloLens não responderá a minha gestos.

Para garantir que o HoloLens podem ver seu gestos, mantenha suas mãos no quadro de gesto, que estende a alguns pés em ambos os lados de você. Quando o HoloLens podem ver sua mão, o cursor será alterado de um ponto para um anel. Saiba mais sobre como usar [gestos](gestures.md).

Se seu ambiente está muito escuro, HoloLens talvez não veja sua mão, portanto, verifique se que há suficiente luz.

Se o visor tem impressões digitais ou Borrar, use o microfiber limpeza pano que acompanha o HoloLens para limpar o visor com cuidado.

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>HoloLens não responderá a Meus comandos de voz.

Se a Cortana não está respondendo aos seus comandos de voz, certifique-se de que cortana está ativado. Na lista de todos os aplicativos, selecione Cortana > Menu > Notebook > configurações para fazer alterações. Para saber mais sobre o que você pode dizer, consulte usar sua voz para controlar o HoloLens.

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>Não consigo colocar hologramas ou consulte hologramas que coloquei anteriormente.

Se o HoloLens não é possível mapear ou seu espaço de carga, ele entrará no modo limitado e não conseguirá colocar hologramas ou consulte hologramas que você colocou. Tente o seguinte:
* Verifique se há luz suficiente em seu ambiente para que HoloLens podem ver e mapear o espaço.
* Verifique se que você está conectado a uma rede Wi-Fi. Se você não estiver conectado ao Wi-Fi, HoloLens não é possível identificar e carregar um espaço conhecido.
* Se você precisar criar um novo espaço, conecte-se ao Wi-Fi e reinicie o HoloLens.
* Para ver se o espaço correto está ativo ou carregar manualmente um espaço, vá para **as configurações** > **sistema** > **espaços**.
* Se o espaço correto é carregado e você ainda estiver tendo problemas, o espaço pode estar corrompido. Para corrigir isso, selecione o espaço, e em seguida, selecione Remover. Depois que o espaço é removido, o HoloLens começar a mapear seu ambiente e criar um novo espaço.

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>Meu HoloLens frequentemente entra no modo limitado ou mostra uma mensagem "O controle perdida".

Se seu dispositivo geralmente mostra um "modo limited" ou uma mensagem de "perda de controle", tente as sugestões de [hologramas meu não parecem bons ou estiver movendo em torno de](#holograms-dont-look-good-or-are-moving-around).

## <a name="my-hololens-cant-tell-what-space-im-in"></a>Meu HoloLens não podem determinar o espaço em que estou.

Se seu HoloLens automaticamente não podem identificar e carregar o espaço que você está, verifique se você está conectado ao Wi-Fi, há muita luz na sala e não houver nenhuma alteração principal para o ambiente. Você também pode carregar um espaço manualmente ou gerenciar seus espaços de acessando **as configurações** > **sistema** > **espaços**.

## <a name="im-getting-a-low-disk-space-error"></a>Estou recebendo um erro de "espaço em disco insuficiente".

Você precisará liberar algum espaço de armazenamento seguindo um ou mais destes procedimentos:
* Exclua alguns espaços não utilizados. Vá para **as configurações** > **sistema** > **espaços**, selecione um espaço, você não for mais necessário e, em seguida, selecione **remover**.
* Remova algumas das hologramas que você colocou.
* Exclua algumas imagens e vídeos no aplicativo de fotos.
* Desinstale alguns aplicativos do seu HoloLens. Na lista de todos os aplicativos, toque e segure o aplicativo que você deseja desinstalar e, em seguida, selecione **desinstalação**.

## <a name="my-hololens-cant-create-a-new-space"></a>Meu HoloLens não é possível criar um novo espaço.

O problema mais provável é que você tiver pouco espaço de armazenamento. Tente uma da [dicas acima](#im-getting-a-low-disk-space-error) para liberar algum espaço em disco.
