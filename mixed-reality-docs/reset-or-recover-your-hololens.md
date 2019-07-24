---
title: Redefinir ou recuperar seu HoloLens
description: Instruções básicas e avançadas para reinicializar ou redefinir seu HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: instruções, reinicialização, redefinição, recuperação, redefinição de hardware, redefinição reversível, ciclo de energia, HoloLens, desligar
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524035"
---
# <a name="reset-or-recover-your-hololens"></a>Redefinir ou recuperar seu HoloLens

Se você estiver tendo problemas com o seu HoloLens, convém tentar uma reinicialização, redefinição ou até mesmo piscar com a recuperação do dispositivo. Este documento orientará você pelas etapas recomendadas em sucessão.

## <a name="perform-a-device-reboot"></a>Executar uma reinicialização do dispositivo

Se o seu HoloLens estiver enfrentando problemas ou não estiver respondendo, primeiro Tente reinicializá-lo por meio de um dos métodos abaixo.

### <a name="perform-a-safe-reboot-via-cortana"></a>Executar uma reinicialização segura via Cortana

A maneira mais segura de reinicializar o HoloLens é por meio da Cortana. Geralmente, essa é uma ótima primeira etapa ao enfrentar um problema com o HoloLens:
1. Colocar em seu dispositivo
2. Verifique se ele está ligado, se um usuário está conectado e se o dispositivo não está aguardando uma senha para desbloqueá-lo.
3. Diga "Ei Cortana, reboot" ou "Ei Cortana, reiniciar".
4. Quando ela for confirmada, pedirá sua confirmação. Aguarde um pouco para que um som seja tocado depois de concluir sua pergunta, indicando que está ouvindo você e, em seguida, diga "Sim".
5. Agora, o dispositivo será reinicializado/reiniciado.

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>Executar uma reinicialização segura por meio do portal do dispositivo Windows

Se o acima não funcionar, você poderá tentar reinicializar o dispositivo por meio do [portal do dispositivo Windows](using-the-windows-device-portal.md). No canto superior direito, há uma opção para reiniciar/desligar o dispositivo.

### <a name="perform-a-safe-reboot-via-the-power-button"></a>Executar uma reinicialização segura por meio do botão de energia

Se você ainda não conseguir reinicializar o dispositivo, poderá tentar emitir uma reinicialização por meio do botão de energia:
1. Pressione e segure o botão de energia por 5 segundos
   1. Depois de 1 segundo, você verá que todos os 5 LEDs acendem e, em seguida, são desligados lentamente da direita para a esquerda
   2. Após 5 segundos, todos os LEDs estarão desativados, indicando que o comando de desligamento foi emitido com êxito
   3. Observe que é importante parar de pressionar o botão imediatamente após a desativação de todos os LEDs
2. Aguarde 1 minuto para que o desligamento seja limpo com sucesso. Observe que o desligamento ainda pode estar em andamento mesmo se as exibições estiverem desativadas
3. Ligue o dispositivo novamente pressionando e segurando o botão de energia por 1 segundo

### <a name="perform-an-unsafe-forced-reboot"></a>Executar uma reinicialização forçada não segura

Se nenhum dos métodos acima puder reinicializar com êxito o dispositivo, você poderá forçar uma reinicialização. Observe que esse método é equivalente a obter a bateria do HoloLens e, como tal, é uma operação perigosa que pode deixar seu dispositivo em um estado corrompido. 

>[!WARNING]
>Esse é um método potencialmente prejudicial e só deve ser usado no evento que nenhum dos métodos acima funcionam.

1. Pressione e segure o botão de energia por pelo menos 10 segundos
   * Não há problema em manter o botão por mais de 10 segundos
   * É seguro ignorar qualquer atividade de LED
2. Libere o botão e aguarde 2-3 segundos
3. Ligue o dispositivo novamente pressionando e segurando o botão de energia por 1 segundo

## <a name="reset-the-device-to-a-factory-clean-state"></a>Redefinir o dispositivo para um estado de limpeza de fábrica

Se o seu HoloLens ainda estiver enfrentando problemas após a reinicialização, você poderá tentar redefini-lo para um estado de limpeza de fábrica. Se você redefinir seu dispositivo, todos os seus dados pessoais, aplicativos e configurações serão apagados. A redefinição instalará apenas a versão mais recente instalada do Windows Holographic e você precisará refazer todas as etapas de inicialização (calibrar, conectar-se ao WiFi, criar uma conta de usuário, baixar aplicativos etc...).
1. Inicie o aplicativo **configurações** -> **atualização** -> **redefinição**
2. Selecione a opção **Redefinir dispositivo** e leia a caixa de diálogo de confirmação
3. Se você concordar em redefinir seu dispositivo, o dispositivo será reinicializado e exibirá um conjunto de engrenagens giratórias com uma barra de progresso
4. Aguarde cerca de 30 minutos para que este processo seja concluído
5. A redefinição será concluída e o dispositivo será reinicializado na experiência pronta para uso

## <a name="perform-a-full-device-recovery"></a>Executar uma recuperação completa do dispositivo

Se, depois de executar as opções acima, seu dispositivo **ainda** estiver congelado, sem resposta ou tiver problemas de atualização ou software, você poderá recuperá-lo usando a ferramenta de recuperação de dispositivo do Windows. Recuperar seu dispositivo é semelhante a redefini-lo no sentido de que ele apagará todo o conteúdo do usuário no dispositivo, incluindo aplicativos, jogos, fotos, contas de usuário e muito mais. Se possível, faça backup das informações que você deseja manter.

Para recuperar totalmente seu HoloLens:
1. Desconecte todos os telefones e dispositivos Windows do seu PC
2. Instalar e iniciar a [ferramenta de recuperação de dispositivo do Windows](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) em seu computador
3. Conecte seu HoloLens ao seu PC usando o cabo micro USB com o qual ele veio
   * Observe que nem todos os cabos USB são criados iguais. Mesmo que você esteja usando outro cabo com êxito, esse fluxo vai expor novos Estados em que o cabo também pode não ser executado. A única opção que seu HoloLens veio é a melhor e mais bem testada
4. Se a ferramenta detectar automaticamente o seu dispositivo, ele exibirá um bloco do HoloLens. Clique nele e siga as instruções para concluir o processo

>[!NOTE]
>WDRT pode recuperar seu dispositivo para uma versão mais antiga do Windows Holographic; Talvez seja necessário instalar as atualizações após a atualização

Se a ferramenta não conseguir detectar seu dispositivo automaticamente, tente o seguinte:
1. Reinicialize o computador e tente novamente (isso corrige a maioria dos problemas)
2. Clique no **botão meu dispositivo não foi detectado**, escolha **Microsoft HoloLens**e siga o restante das instruções na tela
