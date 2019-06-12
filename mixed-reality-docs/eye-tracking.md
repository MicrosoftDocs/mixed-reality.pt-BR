---
title: Acompanhamento ocular
description: Acompanhamento ocular
author: sostel
ms.author: sostel
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Acompanhamento ocular, realidade misturada, entrada, foco com o olhar
ms.openlocfilehash: 7298a34a946f86aaf789cfe44ad971169fc8ece3
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66453697"
---
# <a name="eye-tracking-on-hololens-2"></a>Acompanhamento ocular no HoloLens 2
O HoloLens 2 permite um nível totalmente novo de contexto e entendimento humano dentro da experiência holográfica, fornecendo aos desenvolvedores a incrível capacidade de usar as informações sobre o que os usuários estão vendo. Esta página fornece uma visão geral de como os desenvolvedores podem se beneficiar do acompanhamento ocular para vários casos de uso e as considerações mais importantes durante a criação de interfaces do usuário baseadas no foco com o olhar. 

## <a name="use-cases"></a>Casos de uso
O acompanhamento ocular permite que os aplicativos acompanhem para que local o usuário está olhando em tempo real. Esta seção descreve alguns dos possíveis casos de uso e novas interações que se tornam possíveis com o acompanhamento ocular na realidade misturada.
Antes de começar, a seguir, mencionaremos o [Kit de Ferramentas de Realidade Misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) várias vezes, pois ele fornece vários exemplos interessantes e avançados para uso do acompanhamento ocular, como seleções rápidas e fáceis de alvo com suporte ocular e rolagem automática pelo texto com base no local para o qual o usuário olha. 

### <a name="user-intent"></a>Intenção do usuário    
As informações sobre o local para o qual um usuário olha fornecem um **contexto avançado para outras entradas**, como voz, mãos e controles.
Isso pode ser usado para várias tarefas.
Por exemplo, isso pode variar do **direcionamento** de forma rápida e fácil pela cena simplesmente observando um holograma e falando "selecionar" (confira também [Foco com a cabeça e confirmação](gaze-and-commit.md)) ou falando "coloque isto..." e, em seguida, procurando o local em que você deseja colocar o holograma e dizendo "...lá". Exemplos para esse caso podem ser encontrados em [Kit de Ferramentas de Realidade Misturada – Seleção de alvo com suporte ocular](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) e [Kit de Ferramentas de Realidade Misturada – Posicionamento de alvo com suporte ocular](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Outro exemplo de intenção do usuário pode incluir o uso de informações sobre para o que os usuários olham a fim de melhorar o envolvimento com agentes virtuais personificados e hologramas interativos. Por exemplo, os agentes virtuais poderão adaptar as opções disponíveis e seu comportamento com base no conteúdo atualmente exibido. 

### <a name="implicit-actions"></a>Ações implícitas
A categoria de ações implícitas está intimamente relacionada à intenção do usuário.
A ideia é que os hologramas ou os elementos de interface do usuário reagem de forma um tanto instintiva que pode até mesmo parecer que você não está interagindo com o sistema, mas, pelo contrário, o sistema e o usuário estão em sincronia. Por exemplo, um exemplo extremamente bem-sucedido é a **rolagem automática baseada no foco com o olhar**. A ideia é simples assim: O usuário lê um texto e pode simplesmente continuar lendo. O texto gradualmente se move para cima para manter os usuários em seus fluxos de leitura. Um aspecto importante é que a velocidade da rolagem se adapta à velocidade de leitura do usuário.
Outro exemplo é o **zoom e a panorâmica com suporte ocular** para os quais o usuário pode parecer estar mergulhando exatamente no que está focando. O gatilho do zoom e o controle da velocidade de zoom podem ser obtidos por meio da entrada de voz ou de mão, que é importante para fornecer a sensação de controle e evitar sobrecarregar o usuário (falaremos sobre essas diretrizes de design mais detalhadamente abaixo). Depois de ampliar, o usuário pode seguir suavemente, por exemplo, o curso de uma rua para explorar a vizinhança simplesmente usando o foco com o olhar.
Exemplos de demonstração para esses tipos de interações podem ser encontrados na amostra do [Kit de Ferramentas de Realidade Misturada – Navegação com suporte ocular](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html).

Casos de uso adicionais para _ações implícitas_ podem incluir:
- **Notificações inteligentes:** Já ficou incomodado com notificações aparecendo exatamente no local em que você está focado? Levando em conta o local em que um usuário está concentrado no momento, você pode torná-lo melhor. Mostre o deslocamento de notificações para o local em que o usuário está olhando no momento a fim de limitar distrações e ignorá-las automaticamente após o término da leitura. 
- **Hologramas atentos:** Hologramas que reagem de forma sutil quando são observados. Isso pode variar de elementos de interface do usuário ligeiramente brilhantes, uma flor desabrochando lentamente a um animal de estimação virtual começando a olhar para você novamente ou tentando evitar seu foco com o olhar após um olhar prolongado. Isso pode fornecer um senso interessante de conectividade e satisfação em seu aplicativo.

### <a name="attention-tracking"></a>Acompanhamento de atenção   
As informações sobre o local para o qual os usuários olham são uma ferramenta imensamente avançada para avaliar a usabilidade dos designs e identificar problemas em fluxos de trabalho eficientes. Por enquanto, a visualização e a análise de acompanhamento ocular já é uma prática comum em várias áreas do aplicativo. Com o HoloLens 2, fornecemos uma nova dimensão para essa compreensão, já que os hologramas 3D podem ser colocados em contextos do mundo real e avaliados juntos. O [Kit de Ferramentas de Realidade Misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) fornece exemplos básicos para log e carregamento de dados de acompanhamento ocular e de como visualizá-los.

Outros aplicativos nessa área podem incluir: 
-   **Visualização de foco com o olhar remoto:** A visualização do que os colaboradores remotos estão olhando, por exemplo, verifica se as instruções foram compreendidas e seguidas corretamente.
-   **Estudos de pesquisa de usuário:** O acompanhamento de atenção pode ser usado para explorar a maneira com os usuários iniciantes vs. experientes analisam visualmente o conteúdo ou sua coordenação mão-olho em tarefas complexas (por exemplo, para análise de dados médicos ou durante a operação de máquinas).
-   **Simulações de treinamento e monitoramento de desempenho:** Pratique e otimize a execução de tarefas identificando gargalos com mais eficiência no fluxo de execução.
-   **Avaliações de design, anúncio e pesquisa de marketing:** O acompanhamento ocular é uma ferramenta comum para a pesquisa de mercado avaliar os designs de sites e produtos.

### <a name="additional-use-cases"></a>Casos de uso adicionais
- **Jogos:** Você já quis ter superpoderes? Esta é a sua chance! Faça hologramas levitarem apenas por meio de seu olhar. Lance raios laser de seus olhos. Transforme inimigos em pedras ou congele-os. Use sua visão de raios X para explorar prédios. O limite é sua imaginação.  

- **Avatars expressivos:** O acompanhamento ocular auxilia na exibição de avatars 3D mais expressivos usando a data de acompanhamento ocular em tempo real para animar os olhos do avatar a fim de indicar para o que o usuário está olhando. Ele também adiciona mais expressividade adicionando piscadinhas. 

- **Entrada de texto:** O acompanhamento ocular pode ser usado como uma alternativa interessante para a entrada de texto de baixo esforço, especialmente quando a fala ou as mãos são inconvenientes de serem usadas. 


## <a name="eye-tracking-api"></a>API de acompanhamento ocular
Antes de entrar em detalhes sobre as diretrizes de design específicas para a interação de foco com o olhar, queremos brevemente nos voltar para as funcionalidades oferecidas pelo HoloLens 2 Eye Tracker. A [API de acompanhamento ocular](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) pode ser acessada por meio de: `Windows.Perception.People.EyesPose`. Ela fornece um raio de foco com o olhar único (origem e direção do foco) para desenvolvedores.
O rastreador ocular fornece dados sobre _30 FPS_.
O foco com o olhar está dentro de aproximadamente 1,0 – 1,5 grau no ângulo visual em torno do alvo real focado. Como pequenas imprecisões são esperadas, você deve planejar alguma margem em torno desse valor de limite inferior. Falaremos sobre isso mais abaixo. Para que o acompanhamento ocular funcione com precisão, cada usuário deve passar por uma calibração de usuário de acompanhamento ocular. 

![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamanho ideal do alvo em uma distância de 2 metros*


## <a name="eye-gaze-design-guidelines"></a>Diretrizes de design de foco com o olhar
A criação de uma interação que aproveita o direcionamento ocular com movimentação rápida pode ser um desafio. Nesta seção, resumimos as principais vantagens e os desafios a serem considerados ao projetar seu aplicativo. 

### <a name="benefits-of-eye-gaze-input"></a>Benefícios da entrada do foco com o olhar
- **Apontar com alta velocidade.** O músculo ocular é o músculo de reação mais rápida em nosso corpo. 

- **Pouco esforço.** Quase nenhum movimento físico é necessário. 

- **Capacidade de ser implícito.** Geralmente descrito pelos usuários como "leitura da mente", as informações sobre os movimentos oculares de um usuário permitem que o sistema saiba com qual alvo o usuário pretende interagir. 

- **Canal de entrada alternativo.** O foco com o olhar pode fornecer uma entrada de suporte eficiente para a entrada de mãos e voz baseada em vários anos de experiência dos usuários com base em sua coordenação mão-olho.

- **Atenção visual.** Outro importante benefício é a possibilidade de inferir o que um usuário está prestando atenção. Isso pode ajudar em várias áreas do aplicativo, que vão da avaliação mais efetiva de diferentes designs ao auxílio na criação de interfaces do usuário mais inteligentes e indicações sociais aprimoradas para comunicação remota.

Em resumo, o uso do foco com o olhar como uma entrada potencialmente oferece um sinal contextual rápido e fácil – isso é especialmente eficiente em combinação com outras entradas, como a entrada de *voz* e *manual* para confirmar a intenção do usuário.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Desafios do foco com o olhar como entrada
Muito poder pressupõe muita responsabilidade: Embora o foco com o olhar possa ser usado para criar experiências mágicas para o usuário, parecidas com as de um super-herói, também é importante saber suas desvantagens para considerá-lo adequadamente. A seguir, abordaremos alguns *desafios* que devem ser levados em conta e como resolvê-los ao trabalhar com a entrada de foco com o olhar: 

- **Seu foco com o olhar está "sempre ativado"** No momento em que você abre os olhos, eles começam a se fixar nas coisas do ambiente. Uma reação a cada olhar seu e a emissão de ações potencialmente feitas de maneira acidental por olhar para algo por muito tempo resultará em uma experiência terrível.
É por isso que recomendamos a combinação do foco com o olhar com um *comando de voz*, um *gesto com as mãos*, um *clique de botão* ou uma espera estendida para disparar a seleção de um alvo.
Essa solução também permite um modo no qual o usuário possa olhar livremente em volta sem a sensação desesperadora de disparar algo involuntariamente. Esse problema também deve ser levado em conta durante o design de comentários visuais e auditivos ao simplesmente olhar para um alvo.
Não sobrecarregue o usuário com efeitos de desencaixe imediatos ou sons de foco. O segredo é empregar a sutileza. Abordaremos algumas melhores práticas para isso mais adiante quando falarmos a respeito de recomendações sobre design.

- **Observação vs. controle** Imagine que você deseje alinhar com precisão uma fotografia em seu mural. Você olha para as bordas da fotografia e em volta dela para ver se ela fica bem alinhada. Agora imagine como você fará isso quando, ao mesmo tempo, você deseja usar seu foco com o olhar como entrada para mover a imagem. Difícil, não é mesmo? Isso descreve a função dupla do foco com o olhar quando ele é necessário tanto para a entrada quanto para o controle. 

- **Sair antes de clicar:** Para seleções de alvo rápidas, as pesquisas mostram que o foco com o olhar de um usuário pode passar para outra coisa antes de concluir um clique manual (por exemplo, um gesto de fechar e abrir dedos indicador e polegar). Portanto, atenção especial deve ser dada à sincronização do sinal de foco com o olhar rápido com uma entrada de controle mais lenta (por exemplo, voz, mãos, controle).

- **Alvos pequenos:** Você já teve a sensação de tentar ler um texto que é muito pequeno para uma leitura confortável? Essa sensação de sobrecarregar os olhos que faz com que você se sinta exausto porque tenta reajustar seus olhos para focar melhor?
Essa é uma sensação que você poderá invocar nos usuários quando forçá-los a selecionar alvos muito pequenos no aplicativo usando o direcionamento ocular.
Para o design, visando criar uma experiência agradável e confortável para seus usuários, recomendamos que os alvos tenham um ângulo visual de, pelo menos, 2°, preferencialmente maior.

- **Movimentos irregulares do foco com o olhar** Nossos olhos fazem movimentações rápidas de fixação em fixação. Se você examinar os caminhos de exame dos movimentos oculares registrados, poderá ver que eles parecem irregulares. Seus olhos se movem rapidamente e em saltos espontâneos comparado ao *foco com a cabeça* ou aos *movimentos com as mãos*.  

- **Confiabilidade de acompanhamento:** A precisão do acompanhamento ocular pode diminuir um pouco sob iluminação em constante mudança, pois o olho se ajusta às novas condições.
Embora isso necessariamente não deva afetar o design do aplicativo, pois a precisão deve estar dentro da limitação mencionada acima de 2°. Isso pode significar que o usuário precise executar outra calibragem. 


### <a name="design-recommendations"></a>Recomendações sobre design
A seguir, listamos recomendações sobre design específicas de acordo com as vantagens e os desafios descritos sobre a entrada de foco com o olhar:

1. **Foco com o olhar! = foco com a cabeça:**
    - **Considere se movimentos oculares rápidos, ainda que irregulares, se ajustam à sua tarefa de entrada:** Embora nossos movimentos oculares rápidos e irregulares sejam ótimos para selecionar alvos rapidamente em nosso campo de visão, eles são menos aplicáveis a tarefas que exigem trajetórias de entrada suave (por exemplo, para desenhar ou circular anotações). Nesse caso, apontar com a mão ou a cabeça deve ser preferencial.
  
    - **Evite anexar algo diretamente ao foco com o olhar do usuário (por exemplo, um controle deslizante ou um cursor).**
No caso de um cursor, isso poderá resultar no efeito de “um cursor fugindo” devido a leves deslocamentos no sinal de foco com o olhar projetado. No caso de um controle deslizante, ele entra em conflito com a função dupla de controlar o controle deslizante com seus olhos, embora também deseje verificar se o objeto está na localização correta. Em resumo, os usuários poderão se sentir sobrecarregados e distraídos, especialmente se o sinal for impreciso para esse usuário. 
  
2. **Combinar o foco com o olhar com outras entradas:** A integração do acompanhamento ocular a outras entradas, como gestos com as mãos, comandos de voz ou pressionamentos de botão, traz várias vantagens:
    - **Permitir a observação livre:** Considerando que a função principal de nossos olhos seja observar o ambiente, é importante permitir que os usuários olhem em volta sem disparar nenhum comentário (visual, auditivo ou outro) nem ação. 
    A combinação do ET com outro controle de entrada permite fazer a transição suave entre a observação do ET e os modos de controle de entrada.
  
    - **Provedor de contexto avançado:** O uso das informações sobre o ponto para o qual o usuário está olhando, ao mesmo tempo em que ele emite um comando de voz ou executa um gesto com as mãos, permite uma canalização fácil da entrada no campo de visão. Os exemplos incluem: “Coloque isso lá” para selecionar rápida e fluentemente um holograma e posicioná-lo na cena apenas olhando um alvo e o destino. 

    - **Necessidade de sincronizar entradas multimodais (problema de “sair antes de clicar”):** A combinação de movimentos oculares rápidos com entradas adicionais mais complexas (por exemplo, comandos de voz longos ou gestos com as mãos) traz o risco de prosseguirmos com o foco com o olhar antes de concluirmos o comando de entrada adicional. Portanto, se você criar seus próprios controles de entrada (por exemplo, gestos com as mãos personalizados), lembre-se de registrar a ocorrência dessa entrada ou sua duração aproximada para correlacioná-la ao que um usuário tinha se fixado no passado.
    
3. **Comentários sutis para a entrada de acompanhamento ocular:** É útil fornecer comentários se um alvo é observado (para indicar que o sistema está funcionando conforme o esperado), mas isso deve ser sutil. Isso pode incluir a mistura/o desaparecimento lentos de destaques visuais ou a execução de outros comportamentos sutis de alvo, como movimentos lentos (por exemplo, um pequeno aumento do alvo) para indicar que o sistema detectou corretamente que o usuário está olhando para um alvo, no entanto, sem desnecessariamente interromper o fluxo de trabalho atual do usuário. 

4. **Evitar a imposição de movimentos oculares artificiais como entrada:** Não force os usuários a realizarem movimentos oculares específicos (gestos com o olhar) para disparar ações em seu aplicativo.

5. **Levar em conta as imprecisões:** Fazemos distinção de dois tipos de imprecisões que são perceptíveis aos usuários: Deslocamento e tremulação. A maneira mais fácil de lidar com os deslocamentos é fornecer alvos grandes o suficiente para interação [ângulo visual de > 2° – como referência: sua miniatura tem um ângulo visual de aproximadamente 2° quando você estende o braço (1)]. Isso resulta nas seguintes diretrizes:
    - Não force os usuários a selecionar alvos minúsculos: As pesquisas mostram que, se os alvos forem suficientemente grandes (e o sistema for muito bem projetado), os usuários descreverão a interação como mágica e sem esforço. Se os alvos ficarem muito pequenos, os usuários descreverão a experiência como cansativa e frustrante.
   

## <a name="see-also"></a>Consulte também
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Olhar fixo com cabeça e olhos no DirectX](gaze-in-directx.md)
* [Foco com o olhar no Unity (Kit de Ferramentas de Realidade Misturada)](https://aka.ms/mrtk-eyes)
* [Gestos de mão](gestures.md)
* [Entrada de voz](voice-design.md)
* [Controladores de movimentos](motion-controllers.md)
* [Conforto](comfort.md)
