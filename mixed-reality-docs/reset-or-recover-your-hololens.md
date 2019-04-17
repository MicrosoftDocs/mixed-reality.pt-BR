---
title: Redefinir ou recuperar o HoloLens
description: Instruções básicas e avançadas para reinicializar ou redefinindo o HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: instruções, reinicializar, redefinir, recuperar, reinicialização forçada, reinicialização suave, ciclo de energia, HoloLens, desligar
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589548"
---
# <a name="reset-or-recover-your-hololens"></a>Redefinir ou recuperar o HoloLens

Se você estiver tendo problemas com o HoloLens, talvez você queira experimentar uma reinicialização, redefinição ou até mesmo flash novamente com a recuperação do dispositivo. Este documento orientará você as etapas recomendadas em sucessão.

## <a name="perform-a-device-reboot"></a>Executar uma reinicialização do dispositivo

Se o HoloLens está com problemas ou não está respondendo, primeiro tente reinicializá-lo por meio de um a métodos abaixo.

### <a name="perform-a-safe-reboot-via-cortana"></a>Executar uma reinicialização segura por meio do Cortana

A maneira mais segura para reinicializar o HoloLens é por meio da Cortana. Isso geralmente é uma excelente primeira-etapa quando tendo um problema com o HoloLens:
1. Colocar em seu dispositivo
2. Verifique se ele está ligado, um usuário está conectado e o dispositivo não está aguardando uma senha para desbloqueá-lo.
3. Dizer "Ei Cortana, reinicializar" ou "Ei Cortana, reinicie."
4. Quando ela reconhece ela solicitará confirmação. Espere um segundo para um som a ser executado depois que ela terminar sua pergunta, indicando que ela está escutando para você e, em seguida, diga "Sim".
5. O dispositivo será agora reinicialização/reinício.

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>Executar uma reinicialização segura por meio do Windows Device Portal

Se as opções acima não funcionar, você pode tentar reiniciar o dispositivo por meio [Windows Device Portal](using-the-windows-device-portal.md). No canto superior direito, há uma opção para reiniciar/desligar o dispositivo.

### <a name="perform-a-safe-reboot-via-the-power-button"></a>Executar uma reinicialização segura por meio do botão de energia

Se você ainda não é possível reinicializar seu dispositivo, você pode tentar emitir uma reinicialização por meio do botão de energia:
1. Pressione e mantenha pressionado o botão de energia por 5 segundos
   1. Após 1 segundo, você verá todos os iluminam LEDs 5, em seguida, lentamente desativar da direita para esquerda
   2. Depois de 5 segundos, todos os LEDs serão desligados, indicando que o comando de desligamento foi emitido com êxito
   3. Observe que é importante parar pressionando o botão imediatamente depois de todos os LEDs tem desativado
2. Espere um minuto para o desligamento corretamente tenha êxito. Observe que o desligamento pode ainda estar em andamento, mesmo se o exibe estiverem desativada
3. Ligar o dispositivo novamente, mantenha pressionado o botão de energia por 1 segundo

### <a name="perform-an-unsafe-forced-reboot"></a>Executar uma reinicialização forçada não segura

Se nenhum dos métodos acima são capazes de reinicializar o seu dispositivo com êxito, você pode forçar uma reinicialização. Observe que esse método é equivalente ao extrair a bateria do HoloLens e como tal, é uma operação perigosa que pode deixar seu dispositivo em um estado corrompido. 

>[!WARNING]
>Isso é um método potencialmente prejudicial e só deve ser usado no caso de nenhum dos métodos acima funcionar.

1. Pressione e mantenha pressionado o botão de energia pelo menos 10 segundos
   * Ele é okey manter o botão por mais de 10 segundos
   * É seguro ignorar qualquer atividade de LED
2. Solte o botão e aguarde 2 a 3 segundos
3. Ligar o dispositivo novamente, mantenha pressionado o botão de energia por 1 segundo

## <a name="reset-the-device-to-a-factory-clean-state"></a>Redefinir o dispositivo para um estado limpo de fábrica

Se seu HoloLens ainda estiver com problemas após a reinicialização, tente redefini-lo para um estado limpo de fábrica. Se você redefinir seu dispositivo, todos os dados pessoais, aplicativos e configurações serão apagadas. Redefinindo apenas instalará a versão mais recente instalada do Windows Holographic e você terá que refazer todas as etapas de inicialização (calibrar, conecte-se ao Wi-Fi, criar uma conta de usuário e baixar aplicativos, etc...).
1. Inicie o **as configurações** -> aplicativo **atualização** -> **redefinir**
2. Selecione o **redefinir dispositivo** opção e a caixa de diálogo de confirmação de leitura
3. Se você concordar com redefinir seu dispositivo, o dispositivo reinicializará e exibir um conjunto de engrenagens com uma barra de progresso de rotação
4. Aguarde cerca de 30 minutos para que esse processo seja concluído
5. A reinicialização seja concluída e o dispositivo será reiniciado no fora da experiência de caixa

## <a name="perform-a-full-device-recovery"></a>Executar uma recuperação completa do dispositivo

Se, depois de executar as opções acima, o dispositivo está **ainda** congelado, problemas não responde ou está passando por software ou atualização você pode recuperá-lo usando o do Windows Device Recovery Tool. Recuperar o dispositivo é semelhante para redefini-lo no sentido de que irá apagar todo o conteúdo de usuário no dispositivo, incluindo aplicativos, jogos, fotos, contas de usuário e muito mais. Se possível, fazer backup de quaisquer informações que você deseja manter.

Para recuperar totalmente o HoloLens:
1. Desconecte todos os telefones e dispositivos do Windows do PC
2. Instale e inicie o [Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) em seu PC
3. Conecte seu HoloLens ao PC usando o cabo micro USB ele acompanha
   * Observe que nem todos os cabos USB são criados iguais. Mesmo se você estava usando outro cabo com êxito, este fluxo irá expor novos estados em que o cabo não pode executar tão bem. O seu HoloLens acompanham é a opção mais bem testada e melhores
4. Se a ferramenta detecta automaticamente o seu dispositivo, ele exibirá um bloco do HoloLens. Clique nele e siga as instruções para concluir o processo

>[!NOTE]
>WDRT poderá recuperar seu dispositivo para uma versão anterior do Windows Holographic; Talvez você precise instalar atualizações após Flash

Se a ferramenta não consegue detectar automaticamente o seu dispositivo, tente o seguinte:
1. Reinicie seu computador e tente novamente (isso corrige a maioria dos problemas)
2. Clique o **meu dispositivo não foi detectado botão**, escolha **Microsoft HoloLens**e siga o restante das instruções na tela
