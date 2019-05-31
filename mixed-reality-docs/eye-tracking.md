---
title: Acompanhamento a olho nu
description: Acompanhamento a olho nu
author: sostel
ms.author: sostel
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Acompanhamento de olhos, misturadas realidade, entrada, olhar olho
ms.openlocfilehash: d41b9973ede323e842d7187becb1220ba9980a5d
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402347"
---
# <a name="eye-tracking-on-hololens-2"></a>Acompanhamento em HoloLens 2 a olho nu
HoloLens 2 permite a um nível totalmente novo de contexto e o entendimento humanos dentro de Holographic experiência ao fornecer aos desenvolvedores a incrível capacidade de uso das informações sobre o que os usuários estão vendo. Esta página fornece uma visão geral de como os desenvolvedores podem se beneficiar de acompanhamento de olho para vários casos de uso e o que procurar durante a criação de interfaces do usuário com base em olhar olho. 

## <a name="use-cases"></a>Casos de uso
Acompanhamento a olho nu permite que os aplicativos controlar onde o usuário está procurando em tempo real. Esta seção descreve algumas das possíveis casos de uso e novas interações que se tornam possíveis com os olhos de acompanhamento na realidade mista.
Antes de começar, no seguinte mencionaremos a [Kit de ferramentas de realidade misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) várias vezes, pois ele fornece vários exemplos de interessantes e potente para usar o rastreamento de olho como destino com suporte de olho rápido e fácil as seleções e automaticamente rolar por texto com base em onde o usuário levar analisando. 

### <a name="user-intent"></a>Intenção do usuário    
Informações sobre onde um usuário examina fornecem um poderoso **contexto para outras entradas**, como voz, mãos e controladores.
Isso pode ser usado para várias tarefas.
Por exemplo, isso pode variar de forma rápida e facilmente **direcionamento** entre a cena simplesmente observando um holograma e dizendo "selecionar" (Consulte também [olhar Head e confirmação](gaze-and-commit.md)) ou dizendo "colocar isso...", em seguida, procurando para onde deseja colocar o holograma e dizer "... There". Exemplos para isso podem ser encontrados em [Toolkit de realidade misturada - seleção de destino com suporte de olho](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) e [Kit de ferramentas realidade misturada - posicionamento de destino com suporte de olho](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Um exemplo adicional de intenção do usuário pode incluir usando informações sobre o que os usuários se examinar para melhorar o engajamento com agentes virtuais embodied e hologramas interativas. Por exemplo, agentes virtuais poderão adaptar as opções disponíveis e seu comportamento com base em atualmente exibido o conteúdo. 

### <a name="implicit-actions"></a>Ações implícitas
A categoria de ações implícitas está intimamente relacionado à intenção do usuário.
A ideia é hologramas ou elementos de interface do usuário reagem de forma um pouco instinctual pode não até mesmo parecer que você está interagindo com o sistema em todos os, mas em vez disso, o sistema e o usuário estão em sincronia. Por exemplo, é um exemplo bastante bem-sucedida **rolagem automática com base em olhar olho**. A ideia é simple: O usuário lê um texto e pode apenas continue lendo. O texto gradualmente move para manter os usuários em seu fluxo de leitura. Um aspecto importante é que a velocidade de rolagem se adapta à velocidade de leitura do usuário.
Outro exemplo é **suporte de olho zoom e panorâmica** para que o usuário pode parecer mergulhar exatamente em direção a que ele tem se concentrado em. Disparando o zoom e controlar a velocidade de zoom podem ser controlados por meio de voz ou entregar a entrada que é importante sobre como fornecer a sensação de controle e evitar sobrecarregar o usuário (falaremos sobre essas diretrizes de design em mais detalhes abaixo). Depois de ampliar, o usuário pode perfeitamente seguir, por exemplo, o curso de uma rua para explorar seu ambiente usando simplesmente olhar seus olhos.
Exemplos de demonstração para esses tipos de interações podem ser encontrados na [Toolkit de realidade mista - navegação com suporte de olho](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) exemplo.

Casos para usar o adicionais _implícitas ações_ podem incluir:
- **Notificações inteligentes:** Nunca obter incomodar com notificações pop-up de direita onde você foram concentrando-se? Levando em conta em que um usuário no momento, está prestando atenção à, você pode torná-lo melhor! Mostre notificações de deslocamento a partir de onde o usuário atualmente está procurando para limitar distrações e ignorá-las de uma vez automaticamente terminar de ler. 
- **Hologramas atenciosos:** Hologramas que sutilmente reagem quando está sendo analisado. Isso pode variar de elementos de interface do usuário ligeiramente brilhantes, uma flor blooming lentamente a uma inicialização animais de estimação virtual examinar novamente a você ou tentando evitar seu foco de olho após um olhando prolongado. Isso pode fornecer um senso interessante de conectividade e a satisfação em seu aplicativo.

### <a name="attention-tracking"></a>Acompanhamento de atenção   
Informações sobre onde os usuários procuram no são uma ferramenta e poderosa para avaliar a usabilidade dos designs e para identificar problemas em fluxos de trabalho eficientes. Agora, a visualização e análise de acompanhamento a olho nu já é uma prática comum em várias áreas do aplicativo. Com o HoloLens 2, fornecemos uma nova dimensão para essa compreensão conforme hologramas 3D podem ser colocadas em contextos do mundo real e avaliadas junto com o. O [Kit de ferramentas de realidade misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) fornece exemplos básicos para registro em log e carregar dados de acompanhamento a olho nu e como visualizá-las.

Outros aplicativos nessa área podem incluir: 
-   **Visualização de olhar olho remoto:** Visualizar o que os colaboradores remotos estão vendo, por exemplo, verifique se as instruções são compreendidas e seguidas corretamente.
-   **Estudos de pesquisa de usuário:** Atenção de controle pode ser usada para explorar a maneira de iniciante versus usuários especialistas analisar visualmente o conteúdo ou a sua coordenação mão de olho em tarefas complexas (por exemplo, para análise de dados médicos ou enquanto estiver operando máquinas).
-   **Simulações de treinamento e monitoramento de desempenho:** Pratique e otimizar a execução de tarefas, identificando gargalos com mais eficiência no fluxo de execução.
-   **As avaliações, o anúncio e a pesquisa de marketing de design:** Acompanhamento a olho nu é uma ferramenta comum para pesquisa de mercado avaliar os designs de site e o produto.

### <a name="additional-use-cases"></a>Casos de uso adicionais
- **Jogos:** Você já quis ter superpoderes? Esta é sua chance! Levitate hologramas por olhando-los. Envie a laser emissões de seus olhos. Transformar inimigos em pedra ou congele! Use sua visão de raios-x para explorar os prédios. O limite é de sua imaginação!  

- **Avatares expressivas:** Acompanhamento a olho nu auxilia na mais expressivos avatares 3D usando Data do rastreamento de olho em tempo real para animar os olhos do avatar para indicar o que o usuário atualmente está procurando. Ele também adiciona mais expressividade adicionando winks e pisca. 

- **Entrada de texto:** Acompanhamento a olho nu pode ser usado como uma alternativa interessante para entrada de texto de baixo esforço, especialmente quando se fala ou mãos são inconvenientes para uso. 


## <a name="eye-tracking-api"></a>API de acompanhamento de olhos
Antes de entrar em detalhes sobre as diretrizes de design específicas para interação de olho olhar, queremos brevemente apontar para os recursos que o rastreador de olho HoloLens 2 está fornecendo. O [olho que acompanha a API](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) pode ser acessado por meio de: `Windows.Perception.People.EyesPose`. Ele fornece um raio de olhar olho único (origem olhar e direção) para desenvolvedores.
O rastreador de olho fornece dados sobre _30 FPS_.
Olhar o olho previsto está dentro de autoridade de certificação. 1.0-1,5 graus ângulo visual em torno de real procurados no destino. Como pequenas imprecisions forem esperados, você deve planejar alguma margem em torno desse valor de limite inferior. Falaremos sobre isso mais abaixo. Para acompanhamento a olho nu para trabalhar com precisão, cada usuário é necessário para percorrer uma calibração de usuário de acompanhamento a olho nu. 

![Tamanho de destino ideal a distância do medidor 2](images/gazetargeting-size-1000px.jpg)<br>
*Tamanho de destino ideal a distância do medidor 2*


## <a name="eye-gaze-design-guidelines"></a>Diretrizes de design de olhar olho
Criar uma interação que tira proveito do direcionamento de olho movimentação rápida pode ser um desafio. Nesta seção, resumimos os desafios a serem considerados ao projetar seu aplicativo e as principais vantagens. 

### <a name="benefits-of-eye-gaze-input"></a>Benefícios de olho olhar entrada
- **Apontando de alta velocidade.** O músculo olhos é o mais rápido reacting músculo no nosso corpo. 

- **Pouco esforço.** Quase nenhum movimentos físicos são necessários. 

- **Implicitness.** Geralmente descrita por usuários como "Lembre-se de leitura", informações sobre os movimentos de olho de um usuário permite que o sistema sabe que se envolver com os planos de usuário de destino. 

- **Canal de entrada alternativo.** Olhar olho pode fornecer uma entrada de suporte eficiente para mão e voz entrada criando em anos de experiência dos usuários com base em sua coordenação de olho-de-mão.

- **Atenção Visual.** Outro importante benefício é a possibilidade de inferir o que um usuário é prestar atenção. Isso pode ajudar em várias áreas do aplicativo, variando de mais efetivamente avaliando designs diferentes para ajudar a Interfaces de usuário mais inteligentes e aprimorado indicações sociais para comunicação remota.

Em resumo, usando olhar olho como uma entrada potencialmente oferece um sinal contextual rápido e fácil – isso é especialmente eficiente em combinação com outras entradas, como *voz* e *manual* a entrada para Confirme se a intenção do usuário.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Desafios de olho olhares como uma entrada
Com muita energia, vem muita responsabilidade: Ao olhar olho pode ser usado para criar experiências de usuário mágico pareçam uma super-herói, também é importante saber o que isso não é bom na conta para este adequadamente. A seguir, discutiremos alguns *desafios* levar em conta e como resolvê-los ao trabalhar com olhos olhar entrada: 

- **Seu foco de olho é "sempre ativado"** no momento em que você abrir tampas seus olhos, seus olhos iniciar fixating coisas em seu ambiente. Reagindo a cada procure a marca e ações de emissão potencialmente acidentalmente, porque você observou algo por muito tempo resultaria em uma experiência terrível!
Isso é por isso, recomendamos a combinação de olho olhar com um *comando de voz*, *entregar gesto*, *clique de botão* ou duração estendida para disparar a seleção de um destino.
Essa solução também permite que um modo no qual o usuário pode livremente olhar em volta sem a incrível sensação de disparo involuntariamente algo. Esse problema também deve ser levado em conta durante a criação de comentários visuais e auditivos ao examinar apenas um destino.
Não sobrecarregar o usuário com efeitos de pop-out imediatos ou passe o mouse sons. Sutileza é a chave! Vamos discutir algumas práticas recomendadas para a seguir quando falamos sobre recomendações de design.

- **Observação versus controle** Imagine que você deseja alinhar precisamente uma fotografia no seu mural. Examinar suas bordas e seu entorno para ver se ele se alinhe bem. Agora imagine como você faria isso quando ao mesmo tempo que você deseja usar seu foco de olho como uma entrada para mover a imagem. Difícil, não é mesmo? Isso descreve a função dupla de olhar de olho quando for necessário tanto para entrada e controle. 

- **Sair antes de clique:** Para seleções de destino rápida pesquisa mostrou que olhar de olho de um usuário pode passar antes de concluir um manual clique (por exemplo, um airtap). Portanto, atenção especial deve ser dada para sincronizar o sinal de olhar olho rápido com a entrada de controle mais lenta (por exemplo, voz, mãos, controlador).

- **Destinos pequeno:** Você sabe a sensação ao tentar ler o texto que é apenas um pouco muito pequeno para ler confortavelmente? Essa sensação de sobrecarregar os olhos que fazem com que você se sinta cansados e gasta out porque tentar reajustar seus olhos para focar melhor?
Isso é uma sensação que você pode invocar seus usuários quando forçá-los para selecionar destinos muito pequenos em seu aplicativo usando o direcionamento de olho.
Para o seu design, para criar uma experiência agradável e à vontade para seus usuários, é recomendável que os destinos devem ser pelo menos 2° em ângulo visual, preferencialmente maior.

- **Irregular movimentos de olhar olho** olhos realizar movimentações rápidas de fixação para fixação da. Se você examinar os caminhos de varredura de movimentações de olho gravados, você pode ver que eles parecem irregulares. Seus olhos mover rapidamente e em saltos espontâneas em comparação com *olhar principal* ou *entregar movimentos*.  

- **Confiabilidade de rastreamento:** Precisão de acompanhamento a olho nu pode diminuir um pouco na luz e alterado conforme seus olhos ajustar para as novas condições.
Embora isso necessariamente não deve afetar o design de aplicativo, como a precisão deve estar dentro a limitação mencionada acima de 2°. Pode significar que o usuário tem que executar calibragem do outro. 


### <a name="design-recommendations"></a>Recomendações de design
A seguir, listamos as recomendações de design específicas com base nas vantagens descritas e desafios para olho mantenha o foco de entrada:

1. **Olhar olho! = olhar Head:**
    - **Considere se rápido ainda movimentos de olho desbalanceadas ajustar sua tarefa de entrada:** Embora nosso movimentos de olho rápida e irregulares são ótimos selecionar rapidamente os destinos em nosso campo de visão, é menos aplicável para tarefas que exigem smooth trajetórias de entrada (por exemplo, para desenhar ou encircling anotações). Nesse caso, manualmente ou head apontando deve ser preferencial.
  
    - **Evite anexando algo diretamente ao olhar de olho do usuário (por exemplo, um controle deslizante ou cursor).**
No caso de um cursor, isso pode resultar no efeito "fleeing cursor" devido à pequenas deslocamentos no sinal de olhar olho projetado. No caso de um controle deslizante, ele entra em conflito com a função dupla de controlar o controle deslizante com seus olhos, apesar de desejarem também verificar se o objeto está no local correto. Em resumo, os usuários podem se sentir sobrecarregado e distraído, especialmente se o sinal é impreciso para esse usuário. 
  
2. **Combine olho olhar com outras entradas:** A integração do controle de olho com outras entradas, como gestos de mão, comandos de voz ou pressionamentos de botão, tem várias vantagens:
    - **Permitir a Observação gratuitamente:** Considerando que a função principal da seus olhos é observar o nosso ambiente, é importante permitir que usuários olhar em volta sem disparar qualquer (visuais, auditivas,...) comentários ou ações. 
    Combinar ET com outro controle de entrada permite fazer a transição suave entre os modos de controle de entrada e de Observação ET.
  
    - **Provedor de contexto avançados:** Usando informações sobre onde o usuário está observando ao mesmo tempo em que dizer a um comando de voz ou executar um gesto de mão permite facilmente canalização de entrada entre o campo de visualização. Os exemplos incluem: "Put que lá" em rapidamente fluentemente e selecione posicionar um holograma entre a cena examinando simplesmente um alvo e de destino. 

    - **Necessidade de sincronizar entradas multimodais (problema de "deixe antes de clicar em"):** Combinação de movimentações de olho rápida com mais complexas entradas adicionais (por exemplo, comandos de voz longo ou gestos de mão) guarda o risco de avançarmos com seu foco de olho antes de concluir o comando de entrada adicional. Portanto, se você criar seus próprios controles de entrada (por exemplo, gestos de mão personalizado), certifique-se fazer logon do início desta duração aproximada ou de entrada para correlacioná-los com o que um usuário tinha concentrada no passado.
    
3. **Comentários sutis para entrada de acompanhamento a olho nu:** É útil fornecer comentários, se um destino examinou (para indicar que o sistema está funcionando conforme o esperado), mas deve ser mantido sutil. Isso pode incluir combinação lentamente de entrada/saída destaques do visual ou executar outros comportamentos de destino sutis, como movimentos lenta (por exemplo, aumentando ligeiramente o destino) para indicar que o sistema detectou corretamente que o usuário está observando um destino, no entanto, sem interromper o fluxo de trabalho atual do usuário desnecessariamente. 

4. **Evite a imposição de movimentações de olho artificial como entrada:** Não force os usuários realizem movimentos de olho específico (gestos de olhar) para disparar ações em seu aplicativo.

5. **Conta para imprecisions:** Fazemos distinção dois tipos de imprecisions que são perceptíveis aos usuários: Deslocamento e variação. A maneira mais fácil para os deslocamentos de endereço é fornecer destinos grandes o suficiente para interagir com (> 2° em ângulo visual – como referência: sua miniatura é aproximadamente 2° em ângulo visual quando você se estendem o arm (1)). Isso leva as seguintes diretrizes:
    - Não force os usuários para selecionar destinos pequenos: Pesquisas mostram que, se os destinos são suficientemente grandes (e o sistema é muito bem projetado), os usuários descrevem a interação como mágica e sem nenhum esforço. Se os destinos de se tornar muito pequenos, os usuários descrevem a experiência como fatiguing e frustrante.
    
## <a name="eye-gaze-design-guidelines"></a>Diretrizes de design de olhar olho

Com o HoloLens 2, temos a excelente oportunidade de tornar olhar & confirmação mais rápida e mais confortável usando olhar de olho em vez de olhar principal. No entanto, a olhar de olho se comporta de forma muito diferente para olhar principal de determinadas maneiras e, portanto, é fornecido com um número de desafios únicos. Diretrizes de Design olhares olho, resumimos vantagens gerais e os desafios a serem considerados ao usar o acompanhamento de olho como um meio de entrada em seu aplicativo holographic. Nesta seção, abordaremos as considerações de design específicas para olhar olho & confirmação. Primeiro, seus olhos mover incrivelmente rápida e, portanto, são ótimos para direcionamento rapidamente no modo de exibição. Isso torna o olho olhares ideal para olhar rápido & ações, especialmente quando combinadas com confirmações rápidas como um pressionamento de botão-indicador e polegar de confirmação.

Não mostre um cursor: Embora é quase impossível interagir sem um cursor ao usar o head olhares, o cursor se transforma rapidamente causa distração e irritantes ao usar um olhar de olho. Em vez de depender de um cursor para informar ao usuário se o acompanhamento a olho nu esteja funcionando e tenha corretamente detectada no momento pesquisado no destino, o visual sutis de uso destaca (mais detalhes abaixo).

Se esforçam para comentários de focalização combinada sutil: O que parece ótimo comentários visuais para olhar principal pode resultar em experiências terríveis enorme e cansativa usando olhar de olho. Lembre-se de que seus olhos são extremamente rápidos, darting rapidamente entre pontos em seu campo de exibição. Alterações rápidas realce repentina (ativado/desativado) podem resultar em comentários flickery ao procurar ao redor. Portanto, ao fornecer comentários em foco, recomendamos usar um realce perfeitamente combinada em (e combinada-out ao procurar distância). Isso significa que primeiro você mal Note os comentários ao examinar um destino. Durante o curso de 500 a 1000 ms, o realce aumentaria de intensidade. Enquanto usuários menos experientes poderiam continuar procurando no destino para garantir que o sistema tiver determinado corretamente o destino com foco, os usuários experientes poderiam rapidamente olhares & são confirmadas sem esperar até que os comentários são de sua intensidade total. Além disso, é também recomendável usar um mistura-out quando o desaparecimento dos comentários em foco. Pesquisa mostrou que alterações rápidas de movimento e contraste são muito perceptíveis no sua visão periférica (portanto, a área do campo visual em que você está procurando não). O esmaecimento não precisa ser tão lenta quanto o blend-in. Isso só é essencial quando você tiver alto contraste ou alterações de cor para o realce. Se os comentários em foco era bastante sutis para começar, você provavelmente não perceberá uma diferença.

Fique atento sinais olhar e confirmação de sincronização: A sincronização de sinais de entrada pode ser menor do desafio para olhar simple e a confirmação, portanto, não se preocupe! É algo que você fique atento caso você deseje usar ações de confirmação mais complicadas, embora o que pode envolver a comandos de voz longo ou gestos de mão complicada. Imagine que você examinar o destino e emitido um comando de voz longo. Levadas em conta o tempo necessário para falar e a hora em que o sistema precisava para detectar o que você disse, seu foco de olho geralmente tempo passou a algum novo destino na cena. Portanto, torne seus usuários cientes de que eles podem precisar continuar procurando em um destino até que o comando foi reconhecido ou lidar com a entrada de uma maneira para determinar o início do comando e que o usuário tivesse sido observando naquela época.

## <a name="see-also"></a>Consulte também
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Gestos](gestures.md)
* [Comando de voz](voice-design.md)
* [Controladores de movimentos](motion-controllers.md)
* [Conforto](comfort.md)
