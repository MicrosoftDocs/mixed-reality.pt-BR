---
title: Testar seu aplicativo no HoloLens
description: Diretrizes e sugestões para testar um aplicativo HoloLens
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, testing
ms.openlocfilehash: 35e8eff230cdcd719952ad2633ec610c9a9a26a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589567"
---
# <a name="testing-your-app-on-hololens"></a>Testar seu aplicativo no HoloLens

Testar aplicativos HoloLens são muito semelhantes para testar aplicativos do Windows. Todas as áreas comuns devem ser consideradas (funcionalidade, interoperabilidade, desempenho, segurança, confiabilidade, etc.). No entanto, há algumas áreas que exigem tratamento especial ou atenção a detalhes que geralmente não são observadas em aplicativos de PC ou telefone. Aplicativos holográfico precisam executar sem problemas em um conjunto diversificado de ambientes. Eles também precisam manter o conforto de desempenho e o usuário em todos os momentos. Diretrizes para essas áreas de teste é detalhada neste tópico.

## <a name="performance"></a>Desempenho

Aplicativos holográfico precisam executar sem problemas em um conjunto diversificado de ambientes. Eles também precisam manter o conforto de desempenho e o usuário em todos os momentos. Desempenho é tão importante para a experiência do usuário com um aplicativo holográfica que temos um tópico inteiro dedicado a ele. Certifique-se de que você leia e siga o [Noções básicas sobre desempenho para realidade misturada](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>Teste 3D em 3D
1. **Teste seu aplicativo em diferentes espaços tantos quanto possível.** Tente em salas de big, salas de pequenas, banheiros, cozinhas, quartos, escritórios, etc. Também leva em salas de consideração com recursos fora do padrão como paredes não verticais, curvas paredes, tetos não horizontais. Ele funciona bem quando a transição entre os ambientes, andares, percorrer os corredores ou escadas?
2. **Teste seu aplicativo em condições de iluminação diferentes.** Ele responde corretamente para diferentes condições ambientais, como iluminação, pretas superfícies, transparente refletiva superfícies como espelhos, paredes de vidro, etc.
3. **Teste seu aplicativo em condições diferentes de movimento.** Coloque no dispositivo e tente a seus cenários em vários estados de movimento. Ele responde corretamente para movimentação diferente ou em estado estável?
4. **Teste o funcionamento do seu aplicativo de ângulos diferentes.** Se você tiver um holograma mundo bloqueado, o que acontece se o usuário o conduz por trás dele? O que acontece se trata de algo entre o usuário e o holograma? E se o usuário examina o holograma acima ou abaixo?
5. **Use as indicações de áudio e espaciais.** Verifique se que seu aplicativo utiliza para impedir que o usuário se percam.
6. **Teste seu aplicativo em diferentes níveis de ruído do ambiente.** Se você já implementou comandos de voz, tente invocá-las com níveis variados de ruído do ambiente.
7. **Testar seu aplicativo encaixado e permanente**. Certifique-se de testar de assentos e posições de pé.
8. **Teste seu aplicativo de distâncias diferentes**. Elementos de interface do usuário podem ser lidos e interagidos de longe? Faz o react seu aplicativo para que os usuários recebam muito perto de seu hologramas?
9. **Teste seu aplicativo em relação a interações de barra de aplicativo comuns**. Todos os blocos de aplicativos e aplicativos universais 2D têm uma [barra de aplicativo](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) que permite que você controle como o aplicativo é posicionado no mundo misto. Certifique-se de clicar em Remover encerra o processo de aplicativo normalmente e que o botão Voltar é suportado dentro do contexto de seu aplicativo universal 2D. Tente escalar e movendo seu aplicativo no [modo de ajuste](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) enquanto ele estiver ativo, e enquanto ele é um bloco de aplicativo suspenso.

### <a name="environmental-test-matrix"></a>Matriz de teste ambiental

![Matriz de teste do ambiente para desenvolvimento de aplicativos do HoloLens](images/environment-matrix-600px.png)

## <a name="comfort"></a>Conforto
1. **Planos de recorte.** Ser cuidadosa para onde [hologramas são renderizadas](hologram-stability.md#hologram-render-distances).
2. **Evite a movimentação de virtual inconsistente com a movimentação do cabeçote real.** Evite mover a câmera de forma que não é representativo do movimento de real do usuário. Se seu aplicativo precisar mover o usuário por meio de uma cena, tornar o movimento previsível, minimizar a aceleração e permitem que o usuário controle a movimentação.
3. **Siga as diretrizes de qualidade holograma.** Aplicativos de alto desempenho que implementam o [diretrizes de qualidade holograma](hologram-stability.md) têm menor probabilidade de resultar em discomfort do usuário.
4. **Distribua hologramas horizontalmente em vez de verticalmente.** Forçar o usuário gastar longos períodos de tempo procurando por ou para baixo, pode levar a fadiga no pescoço.

## <a name="input"></a>Entrada

### <a name="gaze-and-gestures"></a>Olhar e gestos

[Mantenha o foco](gaze.md) é um formulário básico de entrada em HoloLens que permitem que os usuários têm por objetivo hologramas e o ambiente. Você pode visualmente ver onde seu foco está definindo como destino com base na posição do cursor. É comum para associar o cursor de olhar um cursor do mouse.

[Gestos](gestures.md) servem para interagir com hologramas, como um clique do mouse. Na maioria das vezes os comportamentos de mouse e toque são os mesmos, mas é importante entender e validar quando eles forem diferentes.

**Valide quando seu aplicativo tem um comportamento diferente com o mouse e toque.** Isso será identificar inconsistências e ajudar a decisões de design para tornar a experiência mais natural para os usuários. Por exemplo, disparar uma ação com base em foco.

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).

### <a name="custom-voice-commands"></a>Comandos de voz personalizadas

[Entrada de voz](voice-input.md) é uma forma natural de interação. A experiência do usuário pode ser mágica ou confuso dependendo de sua escolha de comandos e como expô-los. Como regra, você não deve usar comandos de voz do sistema, como "Select" ou "Ei Cortana" como comandos personalizados. Aqui estão alguns pontos a serem considerados:
1. **Evite usar comandos que soam parecidos.** Potencialmente, isso pode disparar o comando incorreto.
2. **Escolha palavras foneticamente avançadas quando possível.** Isso irá minimizar e/ou evitar ativações falsos.

### <a name="peripherals"></a>Periféricos

Os usuários podem interagir com seu aplicativo por meio [periféricos](hardware-accessories.md). Aplicativos não precisam fazer nada especial para tirar proveito desse recurso, no entanto, há algumas coisas que vale a pena verificar.
1. **Valide interações personalizadas.** Coisas como atalhos de teclado personalizados para seu aplicativo.
2. **Valide a alternância de tipos de entrada.** Tentativa de usar vários métodos de entrada para concluir uma tarefa, como o gesto, voz, mouse e teclado tudo no mesmo cenário.

## <a name="system-integration"></a>Integração do sistema

### <a name="battery"></a>Bateria

Teste seu aplicativo sem uma fonte de alimentação conectada para entender a rapidez ele descarrega a bateria. Um possa compreender facilmente o estado da bateria, observando as leituras do LED de energia. ![Estados de LED que indicam a energia da bateria](images/batterypowerledindication-500px.png)

### <a name="power-state-transitions"></a>Transições de estado de energia

Valide o trabalho de cenários-chave conforme o esperado durante a transição entre estados de energia. Por exemplo, o aplicativo permanece na sua posição original? Ele manter corretamente seu estado? Ele continua a funcionar conforme o esperado?
1. **Espera / retomar.** Para entrar no modo de espera, é possível pressionar e liberar o botão de energia imediatamente. Ele também entrará em espera automaticamente após três minutos de inatividade. Para retomar do modo de espera, é possível pressione e solte o botão de energia imediatamente. O dispositivo também será retomada se você se conectar ou desconectar-se de uma fonte de energia.
2. **Desligamento / reinício.** Para desligar, pressione e segure o botão de energia continuamente para 6 segundos. Para reiniciar, pressione o botão de energia.

### <a name="multi-app-scenarios"></a>Cenários de vários aplicativos

Valide principal funcionalidade do aplicativo ao alternar entre aplicativos, especialmente se você já implementou uma tarefa em segundo plano. Copiar/colar e integração com o Cortana também são vale a pena verificar onde aplicável.

## <a name="telemetry"></a>Telemetria

Usar telemetria e análise para orientá-lo. Integração de análise em seu aplicativo ajudará você a obter insights sobre seu aplicativo de seus testadores Beta e usuários finais. Esses dados podem ser usados para ajudar a otimizar seu aplicativo antes do envio para a Store e para atualizações futuras. Há muitas opções de análise por aí. Se você não tiver certeza de onde começar, confira [App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx).

Perguntas a serem consideradas:
1. Como os usuários estão usando o espaço?
2. O aplicativo é como colocar objetos do mundo - é possível detectar problemas?
3. Quanto tempo eles gastam em diferentes estágios do aplicativo?
4. Quanto tempo eles gastam no aplicativo?
5. Quais são os caminhos de uso mais comuns, os usuários está tentando?
6. Os usuários estão atingindo estados inesperados e/ou erros?

## <a name="emulator-and-simulated-input"></a>Emulador e entrada simulada

O [HoloLens emulador](using-the-hololens-emulator.md) é uma ótima maneira de testar com eficiência o seu aplicativo holográfico com uma variedade de características do usuário simulado e espaços. Aqui estão algumas sugestões para usar efetivamente o emulador para testar seu aplicativo:
1. **Use os ambientes virtuais do emulador para expandir seu teste.** O emulador vem com um conjunto de ambientes virtuais que você pode usar para testar seu aplicativo em ambientes ainda mais.
2. **Use o emulador para examinar seu aplicativo de todos os ângulos.** As chaves PageUp/Pagabaixo tornará seu simulada do usuário mais alta ou mais curta.
3. **Teste seu aplicativo com um HoloLens real.** O emulador do HoloLens é uma excelente ferramenta para ajudá-lo rapidamente iterar em um aplicativo e detectar os bugs novos, mas certifique-se de também testar em um HoloLens físico antes de enviar para a Windows Store. Isso é importante para garantir que o desempenho e a experiência sejam ótimos no hardware real.

## <a name="automated-testing-with-perception-simulation"></a>Testes automatizados com percepção de simulação

Alguns desenvolvedores de aplicativo talvez queira automatizar os testes de seus aplicativos. Além dos testes de unidade simples, você pode usar o [simulação de percepção](perception-simulation.md) pilha no HoloLens, automatizar entrada humana e mundiais para seu aplicativo. A API de simulação de percepção pode enviar entrada simulada para o emulador do HoloLens ou um HoloLens físico.

## <a name="windows-app-certification-kit"></a>Kit de Certificação de Aplicativos Windows

Para dar ao seu aplicativo a melhor chance de que está sendo [publicadas na Windows Store](submitting-an-app-to-the-microsoft-store.md), validar e testá-lo localmente antes de enviá-lo para certificação. Se seu aplicativo for destinado a família do dispositivo Windows.Holographic, o [Kit de certificação de aplicativos do Windows](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx) só executará testes de análise estática de local em seu computador. Não há testes serão executados em seu HoloLens.

## <a name="see-also"></a>Consulte também
* [Enviar um aplicativo para a Windows Store](submitting-an-app-to-the-microsoft-store.md)
