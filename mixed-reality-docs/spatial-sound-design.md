---
title: Usando som em aplicativos de realidade misturada
description: O som espacial é uma ferramenta poderosa para imersão, acessibilidade e design de UX em aplicativos de realidade misturada.
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Realidade mista do Windows, som espacial, design, estilo
ms.openlocfilehash: c069095808eaa9d31b1ffa41dbaa29c9f635837b
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641058"
---
# <a name="using-sound-in-mixed-reality-applications"></a>Usando som em aplicativos de realidade misturada

Use o som para informar e reforçar o modelo mental do usuário do estado do aplicativo. Use a espacial, quando apropriado, para inserir sons no mundo misto. Conectar a auditoria e o Visual dessa maneira aprofunda a natureza intuitiva de muitas interações e leva a uma maior confiança do usuário.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-should-i-add-sounds"></a>Quando devo adicionar sons?
Os aplicativos de realidade misturada geralmente têm uma necessidade maior de sons do que aplicativos em uma tela 2D, devido à falta de uma interface física. Os sons devem ser adicionados quando informam ao usuário ou reforçam as interações.

### <a name="inform-and-reinforce"></a>Informar e reforçar
* Para eventos não iniciados pelo usuário, como notificações, considere adicionar sons para informar ao usuário que ocorreu uma alteração.
* As interações podem ter vários estágios. Considere o uso de sons para reforçar as transições de estágio.

Veja abaixo exemplos de interações, eventos e características de som sugeridas.

### <a name="exercise-restraint"></a>Retentor exercício
Os usuários não têm uma capacidade ilimitada para informações de áudio:
* Cada som deve comunicar uma informação específica e valiosa
* Ao reproduzir sons para informar o usuário, reduza temporariamente o volume de outros sons
* Para sons de botão de mouse (veja abaixo), adicione um atraso de tempo para evitar o disparo excessivo de sons

### <a name="dont-rely-solely-on-sounds"></a>Não confie exclusivamente em sons
Os sons usados também serão valiosos quando os usuários puderem ouvi-los, mas garantir que seu aplicativo seja utilizável mesmo com o som desativado.
* Os usuários podem estar com deficiência auditiva
* Seu aplicativo pode ser usado em um ambiente alto
* Os usuários podem ter privacidade ou outros motivos para desabilitar o áudio do dispositivo

## <a name="how-should-i-sonify-interactions"></a>Como devo sonifyr as interações?
Os tipos de interação na realidade misturada incluem gesto, manipulação direta e voz. Use as características sugeridas a seguir para selecionar ou criar sons para essas interações.

### <a name="gesture-interactions"></a>Interações de gesto
Em realidade misturada, os usuários podem interagir com botões usando um cursor. As ações de botão geralmente são executadas quando o usuário libera o botão, em vez de quando ele foi pressionado, para permitir que o usuário tenha a chance de cancelar a interação. Use sons para reforçar esses estágios. Além disso, para ajudar os usuários a se destinarem a botões distantes, considere usar um som de foco do cursor.
* Os sons de pressionamento de botão devem ter um breve clique tactile. Exemplo: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Os sons de botão não pressionados devem ter uma aparência tactile semelhante. Ter um tom elevado versus o som de imprensa reforça a sensação de conclusão. Exemplo: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* Para sons de foco, considere usar um som sutil e sem ameaça, como um Thud ou um choque de baixa frequência.


### <a name="direct-manipulation"></a>Manipulação direta
No HoloLens 2, o controle de mão articulado dá suporte à manipulação direta de elementos da interface do usuário. Os sons são substituições importantes para a falta de comentários físicos.

Um som de **pressionamento de botão** é importante na manipulação direta porque o usuário não tem indicação física de quando atingiu a parte inferior da viagem principal. Indicadores visuais de viagem de chave podem ser pequenos, sutis e obstruído. Assim como acontece com as interações de gestos, os pressionamentos de botão devem ter um som curto, tactile, como um clique, e as prensas devem ter um clique semelhante com uma densidade elevada.
* Exemplo: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Exemplo: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress)

A confirmação visual de uma **captura** ou **liberação** na manipulação direta é difícil de se comunicar. A mão do usuário geralmente estará no caminho de qualquer efeito visual, e os objetos apto para não têm um análogo visual real de "captação". Por outro lado, os sons podem comunicar efetivamente as interações de captura e liberação bem-sucedidas.
* As ações de captura devem ter um som curto, um pouco muffled tactile, que evoca a ideia de fechar os dedos em um objeto. Às vezes, isso é acompanhado por um som "whoosh" que leva o impacto do som para comunicar o movimento da mão durante a captura. Exemplo: [MRTK_Move_Start. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* As ações de liberação devem ter um som de tactile e curto, geralmente com um efeito de som de captura e em uma ordem inversa no tempo, tendo um impacto e, em seguida, um "whoosh" para comunicar a liquidação do objeto no lugar. Exemplo: [MRTK_Move_End. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_End.wav)

Uma interação de **desenho** deve ter um som persistente e em loop que tenha seu volume controlado pela movimentação da mão do usuário, com que ele seja completamente silencioso quando a mão do usuário ainda estiver e em seu volume máximo quando a mão do usuário estiver se movendo rapidamente.



### <a name="voice-interactions"></a>Interações de voz
As interações de voz geralmente têm elementos visuais sutis. Reforce os estágios de interação usando sons. Considere a escolha de mais sons de tons para diferenciá-los dos sons de gesto e de manipulação direta.

* Use um tom de som positivo para **confirmações**de comando de voz. Os tons crescentes e os principais intervalos musicais são eficazes.
* Use um tom de som mais curto e menos positivo para a **falha**de comando de voz. Evitar sons negativos; em vez disso, use um som mais percussive, neutro para comunicar que o aplicativo está mudando da interação.
* Se seu aplicativo usar uma palavra de ativação, use um tom curto de AdaBoost quando o dispositivo **começar a escutar**e um som de loop sutil enquanto o aplicativo escuta. 

### <a name="notifications"></a>Notificações
As notificações comunicam as alterações de estado do aplicativo e outros eventos não iniciados pelo usuário, como conclusões de processo, mensagens e chamadas.

Na realidade misturada, os objetos que se movem podem sair do campo de exibição do usuário. Acompanha **objetos animados** com um som espacial que depende do objeto e da velocidade de movimento.
* Também ajuda a reproduzir um som espacial no final de uma animação para informar o usuário da nova posição
* Para movimentos graduais, um som "whoosh" durante a movimentação ajudará o usuário a controlar o objeto

As **notificações de mensagem** provavelmente serão ouvidos várias vezes e, às vezes, em uma rápida sucessão. É importante que ele não se sobressaia ou fique sem som. Sons de tons positivos de médio alcance são eficazes aqui.

* As chamadas devem ter qualidades semelhantes a um toque de telefone celular. Em geral, eles são repetindo frases musicais que são executadas até que o usuário responda à chamada.
* A conexão de comunicação de voz e a desconexão devem ter um som tonal curto. O som de conexão deve ter um tom positivo, indicando a conexão bem-sucedida, enquanto o som de desconexão deve ser um som neutro indicando a conclusão da chamada.

## <a name="spatialization"></a>Espacialização
A espacialização usa fones estéreo ou alto-falantes para inserir sons no mundo misto.

### <a name="which-sounds-should-i-spatialize"></a>Quais sons devo ter uma espacial?
Um som deve ser espacial quando estiver associado a um evento que tenha um local espacial. Isso inclui a interface do usuário, as vozes de ia incorporadas e os indicadores visuais.

A espacial dos elementos da **interface do usuário** ajuda a desorganizar o "espaço" do Sonic do usuário, limitando o número de sons estéreo bloqueados a seus cabeçotes. Especialmente em interações de manipulação direta, o toque, a captura e a liberação se sentem mais naturais quando os comentários de áudio são espaciais. No entanto, veja abaixo a atenuação de distância para esses elementos.

A espacialação de **indicadores visuais** e **vozes de ia _incorporadas_**  informam intuitivamente os usuários quando estão fora do campo de exibição.
    
Por outro lado, evite a espacial de **vozes de ia _face_** e outros elementos sem um local espacial bem definido. A espacialização sem um elemento visual relacionado pode distrair os usuários de pensar que há um elemento visual que ele não pode localizar.

Adicionar a spatialização será acompanhado com algum custo de CPU. Muitos aplicativos terão, no máximo, dois sons que são executados simultaneamente. O custo da espacial, nesse caso, pode ser insignificante. Você pode usar o monitor de taxa de quadros MRTK para avaliar o impacto da adição de espacial. 

### <a name="when-and-how-should-i-apply-distance-based-attenuation"></a>Quando e como devo aplicar a atenuação baseada em distância?
No mundo físico, os sons mais distantes são mais silenciosos. O mecanismo de áudio pode modelar essa atenuação com base na distância de origem. Use a atenuação baseada em distância ao comunicar informações relevantes.

As distâncias para **indicadores visuais**, **hologramas animados**e outros sons informativos geralmente são relevantes para o usuário. Use a atenuação baseada em distância para fornecer essa indicação intuitivamente.
* Ajuste a curva de atenuação de cada fonte para se ajustar ao tamanho dos espaços do mundo mistos. A curva padrão do mecanismo de áudio geralmente é destinada a espaços muito grandes (até metade de Kilometer).

Sons que reforçam os **estágios progressivos de botões** e outras interações não devem ter atenuação aplicada. Os efeitos de reforçamento desses sons são geralmente mais importantes do que a comunicação da distância com o botão. As variações podem ser discadas, especialmente com teclados, em que muitos cliques de botão serão ouvidos sucessivamente.

### <a name="which-spatialization-technology-should-i-use"></a>Qual tecnologia de espacial deve ser usada?
Ao usar fones de ouvido ou os alto-falantes do HoloLens, use as tecnologias de espacial com base em HRTF (função de transferência relacionada ao cabeçalho). Eles modelam a propagação de som no mundo físico. Mesmo quando uma fonte de som está longe de um lado da cabeça, o som é propagado para o Ear distante com algumas atenuações e atrasos. A panorâmica do orador, por outro lado, depende apenas da atenuação e aplica a atenuação total no Ear esquerdo quando os sons estão no lado direito (e vice-versa). Isso pode ser desconfortável para ouvintes normais de audição e inacessível para ouvintes com deficiência auditiva em um Ear.

## <a name="next-steps"></a>Próximas etapas
* [Usar som espacial no Unity](spatial-sound-in-unity.md)
* [Estudo de caso do Roboraid](case-study-using-spatial-sound-in-roboraid.md)
* [Estudo de caso do HoloTour](case-study-spatial-sound-design-for-holotour.md)

