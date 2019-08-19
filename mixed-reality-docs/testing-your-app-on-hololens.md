---
title: Testando seu aplicativo no HoloLens
description: Diretrizes e sugestões para testar seu aplicativo de HoloLens
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, teste
ms.openlocfilehash: b8c8e7ea8f90633cbb3b2aa01764398ef9a5c12a
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507905"
---
# <a name="testing-your-app-on-hololens"></a>Testando seu aplicativo no HoloLens

O teste de aplicativos de HoloLens é muito semelhante ao teste de aplicativos do Windows. Todas as áreas usuais devem ser consideradas (funcionalidade, interoperabilidade, desempenho, segurança, confiabilidade, etc.). No entanto, há algumas áreas que exigem tratamento especial ou atenção para detalhes que geralmente não são observados em aplicativos de PC ou telefone. Os aplicativos Holographic precisam ser executados sem problemas em um conjunto diversificado de ambientes. Eles também precisam manter o desempenho e o conforto do usuário em todos os momentos. As diretrizes para testar essas áreas são detalhadas neste tópico.

## <a name="performance"></a>Desempenho

Os aplicativos Holographic precisam ser executados sem problemas em um conjunto diversificado de ambientes. Eles também precisam manter o desempenho e o conforto do usuário em todos os momentos. O desempenho é tão importante para a experiência do usuário com um aplicativo Holographic que temos um tópico inteiro dedicado a ele. Certifique-se de ler e seguir o [desempenho de compreensão para realidade misturada](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>Testando 3D em 3D
1. **Teste seu aplicativo em quantos espaços diferentes forem possíveis.** Experimente em grandes salas, salas pequenas, intervaloss, cozinhas, quartos, escritórios, etc. Também leve em consideração as salas com recursos não padrão, como paredes não verticais, paredes curvas, tetos não horizontais. Ele funciona bem ao fazer a transição entre salas, andares, percorrendo corredores ou escadas?
2. **Teste seu aplicativo em condições de iluminação diferentes.** Ele responde corretamente a diferentes condições ambientais, como iluminação, superfícies pretas, superfícies transparentes/de reflexão, como espelhos, paredes de vidro, etc.
3. **Teste seu aplicativo em condições de movimento diferentes.** Coloque no dispositivo e experimente seus cenários em vários Estados de movimento. Ele responde corretamente a um estado estável ou de movimento diferente?
4. **Teste como seu aplicativo funciona de diferentes ângulos.** Se você tiver um holograma protegido por um mundo, o que acontecerá se o usuário se movimentar por trás dele? O que acontece se algo vier entre o usuário e o holograma? E se o usuário examinar o holograma acima ou abaixo?
5. **Use indicações espaciais e de áudio.** Verifique se seu aplicativo os usa para impedir que o usuário se perca.
6. **Teste seu aplicativo em diferentes níveis de ruído de ambiente.** Se você tiver implementado comandos de voz, tente chamá-los com diferentes níveis de ruído de ambiente.
7. **Teste seu aplicativo encaixado e em pé**. Certifique-se de testar as posições de assentos e de posição.
8. **Teste seu aplicativo de distâncias diferentes**. Os elementos da interface do usuário podem ser lidos e interagindos de longe? Seu aplicativo reage aos usuários ficando muito próximos de seus hologramas?
9. **Teste seu aplicativo em relação às interações comuns da barra de aplicativos**. Todos os blocos de aplicativo e aplicativos universais 2D têm uma [barra de aplicativos](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) que permite controlar como o aplicativo é posicionado no mundo misto. Certifique-se de que clicar em remover finaliza o processo do aplicativo normalmente e que o botão voltar tenha suporte no contexto do seu aplicativo universal 2D. Tente dimensionar e mover seu aplicativo no [modo de ajuste](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) enquanto ele estiver ativo e, embora seja um bloco de aplicativo suspenso.

### <a name="environmental-test-matrix"></a>Matriz de teste ambiental

![Matriz de teste de ambiente para desenvolvimento de aplicativo HoloLens](images/environment-matrix-600px.png)

## <a name="comfort"></a>Conforto
1. **Planos de corte.** Ser cuidadosa para onde os [hologramas são renderizados](hologram-stability.md#hologram-render-distances).
2. **Evite a movimentação virtual inconsistente com a movimentação de cabeçalho real.** Evite mover a câmera de forma que não seja representativa do movimento real do usuário. Se seu aplicativo exigir a movimentação do usuário por meio de uma cena, torne o movimento previsível, minimize a aceleração e permita que o usuário controle o movimento.
3. **Siga as diretrizes de qualidade do holograma.** Aplicativos de alto desempenho que implementam as [diretrizes de qualidade do holograma](hologram-stability.md) são menos prováveis de resultar no discomfort do usuário.
4. **Distribua os hologramas horizontalmente em vez de verticalmente.** Forçar o usuário a gastar períodos prolongados de tempo de pesquisa ou redução pode levar a fadiga no pescoço.

## <a name="input"></a>Entrada

### <a name="gaze-and-gestures"></a>Olhar e gestos

[Olhar](gaze.md) é uma forma básica de entrada no HoloLens que permite aos usuários visar em hologramas e no ambiente. Você pode ver visualmente onde seu olhar está direcionando com base na posição do cursor. É comum associar o cursor olhar a um cursor do mouse.

Os [gestos](gestures.md) são como você interage com os hologramas, como um clique do mouse. Na maioria das vezes, os comportamentos de mouse e toque são os mesmos, mas é importante entender e validar quando eles diferem.

**Valide quando seu aplicativo tiver um comportamento diferente com o mouse e o toque.** Isso identificará inconsistências e ajudará com decisões de design para tornar a experiência mais natural para os usuários. Por exemplo, disparar uma ação com base no foco.

> [!NOTE]
> Mais diretrizes específicas para o HoloLens 2 em [breve](index.md#news-and-notes).

### <a name="custom-voice-commands"></a>Comandos de voz personalizados

A [entrada de voz](voice-input.md) é uma forma natural de interação. A experiência do usuário pode ser mágico ou confusa, dependendo da sua escolha de comandos e de como você os expõe. Como regra, você não deve usar comandos de voz do sistema, como "Select" ou "Ei Cortana" como comandos personalizados. Aqui estão alguns pontos a serem considerados:
1. **Evite usar comandos que parecem semelhantes.** Isso pode potencialmente disparar o comando incorreto.
2. **Escolha palavras com o formato fonético, quando possível.** Isso minimizará e/ou evitará ativações falsas.

### <a name="peripherals"></a>Periféricos

Os usuários podem interagir com seu aplicativo por meio de [periféricos](hardware-accessories.md). Os aplicativos não precisam fazer nada especial para aproveitar esse recurso, no entanto, há algumas coisas que vale a pena verificar.
1. **Validar interações personalizadas.** Coisas como atalhos de teclado personalizados para seu aplicativo.
2. **Valide a alternância de tipos de entrada.** A tentativa de usar vários métodos de entrada para concluir uma tarefa, como voz, gesto, mouse e teclado, tudo no mesmo cenário.

## <a name="system-integration"></a>Integração do sistema

### <a name="battery"></a>Bateria

Teste seu aplicativo sem uma fonte de energia conectada para entender a rapidez com que ele drena a bateria. É possível entender facilmente o estado da bateria examinando as leituras do LED de energia. 

![Estados de LED que indicam a energia da bateria](images/batterypowerledindication-500px.png)<br>

*Estados de LED que indicam a energia da bateria*

### <a name="power-state-transitions"></a>Transições de estado de energia

Os principais cenários de validação funcionam conforme o esperado ao fazer a transição entre os Estados de energia. Por exemplo, o aplicativo permanece em sua posição original? Ele mantém corretamente seu estado? Ele continua funcionando conforme o esperado?
1. **Retomada/retomar.** Para entrar em espera, é possível pressionar e liberar o botão de energia imediatamente. O dispositivo também entrará em espera automaticamente após 3 minutos de inatividade. Para retomar do modo de espera, é possível pressionar e liberar o botão de energia imediatamente. O dispositivo também será retomado se você se conectar ou desconectá-lo de uma fonte de alimentação.
2. **Desligamento/reinicialização.** Para desligar, pressione e mantenha pressionado o botão de energia continuamente por 6 segundos. Para reiniciar, pressione o botão de energia.

### <a name="multi-app-scenarios"></a>Cenários de vários aplicativos

Valide a funcionalidade principal do aplicativo ao alternar entre aplicativos, especialmente se você tiver implementado uma tarefa em segundo plano. A integração de copiar/colar e Cortana também vale a pena verificar onde aplicável.

## <a name="telemetry"></a>Telemetria

Use a telemetria e a análise para orientá-lo. A integração da análise em seu aplicativo ajudará você a obter informações sobre seu aplicativo dos testadores beta e dos usuários finais. Esses dados podem ser usados para ajudar a otimizar seu aplicativo antes do envio para a loja e para atualizações futuras. Há muitas opções de análise por aí. Se você não tiver certeza de onde começar, confira o [app](https://www.visualstudio.com/products/application-insights-vs.aspx)insights.

Perguntas a serem consideradas:
1. Como os usuários estão usando o espaço?
2. Como o aplicativo está colocando objetos no mundo – você pode detectar problemas?
3. Quanto tempo eles gastam em diferentes estágios do aplicativo?
4. Quanto tempo eles gastam no aplicativo?
5. Quais são os caminhos de uso mais comuns que os usuários estão tentando?
6. Os usuários estão atingindo Estados e/ou erros inesperados?

## <a name="emulator-and-simulated-input"></a>Emulador e entrada simulada

O [emulador do HoloLens](using-the-hololens-emulator.md) é uma ótima maneira de testar com eficiência seu aplicativo Holographic com uma variedade de características e espaços de usuário simulados. Aqui estão algumas sugestões para usar efetivamente o emulador para testar seu aplicativo:
1. **Use as salas virtuais do emulador para expandir seus testes.** O emulador vem com um conjunto de salas virtuais que você pode usar para testar seu aplicativo em ambientes ainda mais.
2. **Use o emulador para examinar seu aplicativo de todos os ângulos.** As chaves PageUp/PageDn tornarão o usuário simulado mais alto ou menor.
3. **Teste seu aplicativo com um HoloLens real.** O emulador do HoloLens é uma excelente ferramenta para ajudá-lo a iterar rapidamente em um aplicativo e detectar novos bugs, mas também deve testar um HoloLens físico antes de enviar para a Windows Store. Isso é importante para garantir que o desempenho e a experiência sejam ótimos no hardware real.

## <a name="automated-testing-with-perception-simulation"></a>Teste automatizado com simulação de percepção

Alguns desenvolvedores de aplicativos podem querer automatizar o teste de seus aplicativos. Além dos testes de unidade simples, você pode usar a pilha de [simulação de percepção](perception-simulation.md) no HoloLens para automatizar a entrada humana e mundial para seu aplicativo. A API de simulação de percepção pode enviar entrada simulada para o emulador do HoloLens ou um HoloLens físico.

## <a name="windows-app-certification-kit"></a>Kit de Certificação de Aplicativos Windows

Para dar ao seu aplicativo a melhor chance de ser [publicado na Windows Store](submitting-an-app-to-the-microsoft-store.md), valide-o e teste-o localmente antes de enviá-lo para certificação. Se seu aplicativo for destinado à família de dispositivos Windows. Holographic, o [Kit de certificação de aplicativos para Windows](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx) executará apenas testes de análise estática local em seu computador. Nenhum teste será executado em seu HoloLens.

## <a name="see-also"></a>Consulte também
* [Enviando um aplicativo para a Windows Store](submitting-an-app-to-the-microsoft-store.md)
