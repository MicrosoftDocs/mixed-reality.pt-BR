---
title: Olho-olhar
description: O HoloLens 2 permite um nível novo de contexto e entendimento humano dentro da experiência holográfica, fornecendo aos desenvolvedores a capacidade de usar as informações sobre o que os usuários estão vendo.
author: sostel
ms.author: sostel
ms.date: 04/05/2019
ms.topic: article
keywords: Acompanhamento de olho, realidade misturada, entrada, olho-olhar
ms.openlocfilehash: 51779b7b210522aa4d19b5a32d7df6ccb2cb3a35
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122070"
---
# <a name="eye-gaze-on-hololens-2"></a>Olho-olhar no HoloLens 2
O HoloLens 2 permite um nível novo de contexto e entendimento humano dentro da experiência holográfica, fornecendo aos desenvolvedores a capacidade de usar as informações sobre o que os usuários estão vendo. Esta página informa aos desenvolvedores como eles podem se beneficiar do controle de olho para vários casos de uso, bem como o que procurar ao projetar interfaces de usuário baseadas em olhar. 


## <a name="device-support"></a>Suporte a dispositivos

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Recurso</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
     <td><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
</tr>
<tr>
     <td>Olho-olhar</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="use-cases"></a>Casos de uso
O acompanhamento ocular permite que os aplicativos acompanhem para que local o usuário está olhando em tempo real. Os casos de uso a seguir descrevem algumas interações que são possíveis com o acompanhamento de olho na realidade misturada.
Tenha em mente que o [Kit de ferramentas de realidade misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) é útil para fornecer vários exemplos interessantes e eficientes para usar o acompanhamento de olho, como seleções de destino com suporte rápido e sem esforço, bem como percorrer automaticamente o texto com base em o que o usuário examina. 

### <a name="user-intent"></a>Intenção do usuário    
As informações sobre onde e o que um usuário observa fornecem um **contexto poderoso para outras entradas**, como voz, mãos e controladores.
Isso pode ser usado para várias tarefas.
Por exemplo, isso pode variar de um **direcionamento** rápido e sem esforço na cena simplesmente observando um holograma e dizendo "Select" (também consulte [Head-olhar e commit](gaze-and-commit.md)) ou dizendo *"Put this..."* e, em seguida, procurando onde o usuário deseja posicionar o holograma e dizer *"... lá "* . Exemplos para esse caso podem ser encontrados em [Kit de Ferramentas de Realidade Misturada – Seleção de alvo com suporte ocular](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) e [Kit de Ferramentas de Realidade Misturada – Posicionamento de alvo com suporte ocular](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Além disso, um exemplo de intenção de usuário pode incluir o uso de informações sobre o que os usuários examinam para aprimorar o envolvimento com os agentes virtuais e os hologramas interativos. Por exemplo, os agentes virtuais podem adaptar as opções disponíveis e seu comportamento com base no conteúdo exibido atualmente. 

### <a name="implicit-actions"></a>Ações implícitas
A categoria de ações implícitas está intimamente relacionada à intenção do usuário.
A ideia é que os hologramas ou os elementos da interface do usuário reagem de uma maneira um pouco instinctual que talvez não pareçam que o usuário esteja interagindo com o sistema, mas que o sistema e o usuário estejam em sincronia. Um exemplo é a **rolagem automática baseada em olhar de olho** em que o usuário pode ler um texto longo que inicia automaticamente a rolagem quando o usuário chega à parte inferior da caixa de texto para manter o usuário no fluxo de leitura sem levantar um dedo.  
Um aspecto fundamental disso é que a velocidade da rolagem se adapta à velocidade de leitura do usuário.
Outro exemplo é o **zoom e a panorâmica com suporte,** em que o usuário pode se sentir como mergulhar exatamente em relação ao que ele está concentrado. O disparo de zoom e controle da velocidade de zoom pode ser controlado por entrada de voz ou por mão, o que é importante para fornecer ao usuário a sensação de controle, evitando que seja sobrecarregado. Falaremos sobre essas diretrizes de design mais detalhadamente abaixo. Uma vez ampliado, o usuário pode seguir, por exemplo, o curso de uma rua para explorar sua vizinhança simplesmente usando seus olhos olhars.
Exemplos de demonstração para esses tipos de interações podem ser encontrados na amostra do [Kit de Ferramentas de Realidade Misturada – Navegação com suporte ocular](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html).

Casos de uso adicionais para _ações implícitas_ podem incluir:
- **Notificações inteligentes:** Já ficou incomodado com notificações aparecendo exatamente no local em que você está focado? Levando em conta o que um usuário está prestando a atenção, você pode melhorar a experiência com notificações de compensação de onde o usuário está nuvens no momento. Isso limita distrações e os descarta automaticamente quando o usuário termina de ler. 
- **Hologramas atentos:** Hologramas que reagem sutilmente ao serem gazeddos. Isso pode variar desde elementos de interface do usuário ligeiramente brilhantes até uma flor de intensão lentamente até um animal virtual começando a olhar de volta ao usuário ou tentando evitar o olhar de olho do usuário depois de uma estrela prolongada. Essa interação pode fornecer uma noção interessante de conectividade e satisfação em seu aplicativo.

### <a name="attention-tracking"></a>Acompanhamento de atenção   
As informações sobre onde ou o que os usuários examinam é uma ferramenta extremamente poderosa para avaliar a usabilidade de designs e identificar problemas em fluxos de trabalho eficientes. A visualização e a análise de controle de olho são uma prática comum em várias áreas de aplicativo. Com o HoloLens 2, fornecemos uma nova dimensão para essa compreensão, pois os hologramas de 3D podem ser colocados em contextos reais e avaliados de acordo. O [Kit de ferramentas de realidade misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) fornece exemplos básicos para registrar e carregar dados de acompanhamento de olho e como visualizá-los.

Outros aplicativos nessa área podem incluir: 
-   **Visualização de olhar de olho remoto:** Visualize o que os colaboradores remotos estão vendo para garantir se as instruções foram compreendidas e seguidas corretamente.
-   **Estudos de pesquisa de usuário:** O acompanhamento de atenção pode ser usado para explorar o modo como o principiante e os usuários especialistas analisam visualmente o conteúdo ou como sua coordenação de olhos para tarefas complexas, como para a análise de dados médicos ou de máquinas operacionais.
-   **Simulações de treinamento e monitoramento de desempenho:** Pratique e otimize a execução de tarefas identificando gargalos com mais eficiência no fluxo de execução.
-   **Avaliações de design, anúncio e pesquisa de marketing:** O controle de olhos é uma ferramenta comum para pesquisa de mercado ao avaliar designs de sites e produtos.

### <a name="additional-use-cases"></a>Casos de uso adicionais
- **Jogos:** Você já quis ter superpoderes? Esta é a sua chance! Você pode levitater os hologramas por estrelas. Lance raios laser de seus olhos. Transforme inimigos em pedra ou congele-os. Use sua visão de raios X para explorar prédios. O limite é sua imaginação.  

- **Avatars expressivos:** Controle de olho ajuda em avatars 3D mais expressivos usando dados de acompanhamento de olho ao vivo para animar os olhos do avatar que indicam o que o usuário está olhando. 

- **Entrada de texto:** O controle de olho pode ser usado como uma alternativa para a entrada de texto de baixo esforço, especialmente quando a fala ou as mãos são inconvenientes de usar. 


## <a name="available-eye-tracking-data"></a>Dados de acompanhamento de olho disponíveis
Antes de entrar em detalhes sobre as diretrizes de design específicas para a interação olhar, queremos destacar rapidamente os recursos fornecidos pela API de acompanhamento de [olhos](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) do HoloLens 2. Os desenvolvedores obtêm acesso a um único olhar Ray (olhar e direção) a aproximadamente _30 fps (60 Hz)_ .
Para obter informações mais detalhadas sobre como acessar dados de controle de olho, consulte nossos guias de desenvolvedor sobre como usar [olhar no DirectX](gaze-in-directx.md) e [olho-olhar no Unity](https://aka.ms/mrtk-eyes).

O olho previsto-olhar é aproximadamente de 1,5 graus no ângulo visual em torno do destino real (consulte a ilustração abaixo). À medida que pequenas imprecisãos são esperadas, os desenvolvedores devem planejar uma margem em relação a esse valor de limite inferior (por exemplo, os graus do 2.0-3.0 podem resultar em uma experiência muito mais confortável). Discutiremos como abordar a seleção de destinos pequenos em mais detalhes abaixo. Para que o acompanhamento ocular funcione com precisão, cada usuário deve passar por uma calibração de usuário de acompanhamento ocular. 

![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamanho de destino ideal em uma distância de 2 medidores*

## <a name="calibration"></a>Calibragem 
Para que o acompanhamento de olho funcione com precisão, cada usuário precisa passar por uma [calibragem do usuário com acompanhamento de olho](calibration.md) para o qual o usuário precisa examinar um conjunto de destinos Holographic. Isso permite que o dispositivo ajuste o sistema para uma experiência de exibição de qualidade mais confortável e mais segura para o usuário e para garantir o acompanhamento preciso do controle de olho ao mesmo tempo. O controle de olhos deve funcionar para a maioria dos usuários, mas há casos em que um usuário pode não conseguir calibrar com êxito.
Para saber mais sobre a calibração, verifique a [calibragem](calibration.md).

## <a name="eye-gaze-input-design-guidelines"></a>Diretrizes de design de entrada olhar
A criação de uma interação que aproveita o direcionamento de olho rápido pode ser desafiadora. Nesta seção, resumimos as principais vantagens e desafios a serem considerados ao projetar seu aplicativo. 

### <a name="benefits-of-eye-gaze-input"></a>Benefícios da entrada olhar
- **Apontar com alta velocidade.** O olho capacidade é o capacidade mais rápido de reagir no corpo humano. 

- **Pouco esforço.** Quase nenhum movimento físico é necessário. 

- **Capacidade de ser implícito.** Geralmente descritas pelos usuários como "leitura mental", as informações sobre os movimentos de um usuário permitem que o sistema saiba qual alvo o usuário planeja participar. 

- **Canal de entrada alternativo.** O olho-olhar pode fornecer uma poderosa entrada de suporte para a mão e entrada de voz em anos de experiência de usuários com base em sua coordenação de olhos.

- **Atenção visual.** Outro benefício importante é a possibilidade de inferir o que um usuário está prestando a atenção. Isso pode ajudar em várias áreas de aplicativos que vão desde a avaliação de diferentes designs para auxiliar em interfaces de usuário mais inteligentes e indicações sociais aprimoradas para comunicação remota.

Resumindo, usar olhar como uma entrada oferece um sinal contextual rápido e sem esforço. Isso é particularmente poderoso quando combinado com outras entradas, como *voz* e entrada *manual* , para confirmar a intenção do usuário.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Desafios de olhar de olho como uma entrada
Com muita potência, vem muito de responsabilidade.
Embora os olhos olhar possam ser usados para criar experiências de usuário satisfatórias que fazem você sentir como um Superhero, também é importante saber o que não é bom para se considerar apropriadamente. O a seguir discute alguns *desafios* a considerar e como solucioná-los ao trabalhar com a entrada de olhar de olho: 

- **Seu olho-olhar é "Always on"** No momento em que você abre suas tampas de olho, seus olhos começam a fixatingr sobre as coisas no ambiente. Reagir a todas as aparências que você fizer e emitir ações acidentalmente, pois você examinou algo por muito tempo resultaria em uma experiência que não satisfaça.
Portanto, é recomendável combinar olhars de olho com um *comando de voz*, um *gesto de mão*, um clique de *botão* ou uma duração estendida para disparar a seleção de um destino.
Essa solução também permite um modo no qual o usuário pode procurar livremente sem ser sobrecarregado por disparar involuntariamente algo. Esse problema também deve ser considerado durante a criação de comentários de auditoria e visuais, ao examinar apenas um destino.
Não sobrecarregue o usuário com efeitos de desencaixe imediatos ou sons de foco. A sutileza é fundamental. Abordaremos algumas melhores práticas para isso mais adiante quando falarmos a respeito de recomendações sobre design.

- **Observação vs. controle** Imagine que você deseja endireitar precisamente uma fotografia em sua parede. Você olha para as bordas da fotografia e em volta dela para ver se ela fica bem alinhada. Agora imagine como você faria isso quando quiser usar seu olho-olhar como uma entrada para mover a imagem. Difícil, não é mesmo? Isso descreve a função dupla de olhar quando é necessário para entrada e controle. 

- **Sair antes de clicar:** Para seleções de destino rápido, a pesquisa mostrou que o olhar de olho do usuário pode passar antes de concluir um clique manual (por exemplo, um airtap). Portanto, atenção especial deve ser paga para sincronizar o sinal de olhar rápido com entrada de controle mais lenta (por exemplo, voz, mãos, controlador).

- **Alvos pequenos:** Você sabe a sensação quando tenta ler um texto que é um pouco pequeno demais para ler confortavelmente? Essa sensação de sobrecarregar seus olhos pode fazer com que você fique cansado e desgastado porque tenta reajustar os olhos para se concentrar melhor.
Essa é uma sensação que você pode invocar em seus usuários ao forçá-los a selecionar destinos que são muito pequenos em seu aplicativo usando o direcionamento de olho.
Para o design, visando criar uma experiência agradável e confortável para seus usuários, recomendamos que os alvos tenham um ângulo visual de, pelo menos, 2°, preferencialmente maior.

- **Olhos irregulares – movimentos olhars** Nossos olhos realizam movimentos rápidos do fixação da para o fixação da. Se você examinar os caminhos de exame dos movimentos oculares registrados, poderá ver que eles parecem irregulares. Seus olhos se movem rapidamente e em saltos ESPONTANEOS em comparação com os *olhar* ou os *movimentos de mão*.  

- **Confiabilidade de acompanhamento:** A precisão do acompanhamento ocular pode diminuir um pouco sob iluminação em constante mudança, pois o olho se ajusta às novas condições.
Embora isso não deva afetar necessariamente o design do aplicativo, pois a precisão deve estar dentro da limitação de 2 °, talvez seja necessário que o usuário calibre novamente. 


## <a name="design-recommendations"></a>Recomendações sobre design
Veja a seguir uma lista de recomendações de design específicas com base nas vantagens e nos desafios descritos para a entrada de olhar de olho:

1. **Olho-olhar não é o mesmo que Head-olhar:**
    - **Considere se movimentos oculares rápidos, ainda que irregulares, se ajustam à sua tarefa de entrada:** Embora nossos movimentos de olho rápidos e irregulares sejam ótimos na seleção rápida de destinos em nosso campo de exibição, ele é menos aplicável para tarefas que exigem trajetórias de entrada suaves (por exemplo, desenho ou ennotamento de anotações). Nesse caso, apontar com a mão ou a cabeça deve ser preferencial.
  
    - **Evite anexar algo diretamente ao olhar de olho do usuário (por exemplo, um controle deslizante ou cursor).**
No caso de um cursor, isso pode resultar no efeito de "cursor fleeing" devido a pequenos deslocamentos no sinal olhar de olho projetado. No caso de um controle deslizante, ele pode entrar em conflito com a função dupla de controlar o controle deslizante com seus olhos, enquanto também deseja verificar se o objeto está no local correto. Resumindo, os usuários poderiam se tornar sobrecarregados e distraídoss, especialmente se o sinal for impreciso para esse usuário. 
  
2. **Combine olho-olhar com outras entradas:** A integração do controle de olho com outras entradas, como gestos à mão, comandos de voz ou prensas de botão, atende a várias vantagens:
    - **Permitir a observação livre:** Considerando que a função principal de nossos olhos é observar nosso ambiente, é muito importante que os usuários sejam configurados sem disparar nenhum comentário ou ação (Visual, auditoria, etc.). 
    Combinar o controle de olho com outro controle de entrada permite a transição tranqüila entre a observação de acompanhamento de olho e os modos de controle de entrada.
  
    - **Provedor de contexto avançado:** Usar informações sobre onde e o que o usuário está olhando ao longo de um comando de voz ou executar um gesto de mão permite canalizar diretamente a entrada no campo de exibição. Por exemplo: “Coloque isso lá” para selecionar rápida e fluentemente um holograma e posicioná-lo na cena apenas olhando um alvo e o destino. 

    - **Necessidade de sincronizar entradas multimodais (problema de “sair antes de clicar”):** Combinar movimentos de olhos rápidos com entradas adicionais mais complexas, como comandos de voz longos ou gestos de mão, tem o risco de continuar o olhar antes de concluir o comando de entrada adicional. Portanto, se você criar seus próprios controles de entrada (por exemplo, gestos de mão personalizada), certifique-se de registrar o início dessa entrada ou duração aproximada para correlacioná-lo com o que um usuário examinou no passado.
    
3. **Comentários sutis para a entrada de acompanhamento ocular:** É útil fornecer comentários quando um destino é examinado para indicar que o sistema está funcionando como pretendido, mas deve ser mantido sutil. Isso pode incluir a mistura lenta, a entrada e a saída dos destaques visuais ou a execução de outros comportamentos de destino sutis, como movimentos lentos, como aumentar ligeiramente o tamanho do destino, para indicar que o sistema detectou corretamente que o usuário está olhando para um destino sem interromper desnecessariamente o fluxo de trabalho atual do usuário. 

4. **Evitar a imposição de movimentos oculares artificiais como entrada:** Não force os usuários a executar movimentos de olho específicos (gestos de olhar) para disparar ações em seu aplicativo.

5. **Levar em conta as imprecisões:** Distinguemos dois tipos de impedições que são perceptíveis para os usuários: deslocamento e Tremulação. A maneira mais fácil de resolver um deslocamento é fornecer destinos suficientemente grandes para interagir com o. É recomendável que você use um ângulo visual maior que 2 ° como referência. Por exemplo, sua miniatura é de cerca de 2 ° no ângulo visual quando você amplia seu braço. Isso resulta nas seguintes diretrizes:
    - Não force os usuários a selecionar pequenos destinos. A pesquisa mostrou que se os destinos são suficientemente grandes e que o sistema foi projetado bem, os usuários descrevem suas interações como sem esforço e mágico. Se os alvos ficarem muito pequenos, os usuários descreverão a experiência como cansativa e frustrante.
  
## <a name="dev-guidance-what-if-eye-tracking-is-not-available"></a>Diretrizes de desenvolvimento: E se o acompanhamento dos olhos não estiver disponível?
Pode haver situações em que seu aplicativo não receberá nenhum dado de controle de olho devido a vários motivos, incluindo, mas não limitado a:
* O usuário ignorou a calibragem de acompanhamento ocular.
* O usuário foi calibrado, mas decidiu não conceder permissão ao seu aplicativo para usar seus dados de controle de olho.
* O usuário tem óculos exclusivo ou alguma condição de olho que ainda não dá suporte ao sistema.
* Fatores externos que impedem o acompanhamento de olho confiável, como manchas no visor ou óculos do HoloLens, luz de sol direta intensa e occlusions devido ao cabelo na frente dos olhos.

Para você como desenvolvedor de aplicativos, isso significa que você precisa considerar como dar suporte a usuários para os quais os dados de acompanhamento de olho podem não estar disponíveis. Abaixo, explicamos primeiro como detectar se o acompanhamento de olhos está disponível e como abordar quando ele não está disponível para aplicativos diferentes.

### <a name="1-how-to-detect-that-eye-tracking-is-available"></a>1. Como detectar se o acompanhamento de olho está disponível
Há algumas verificações para determinar se os dados de acompanhamento de olho estão disponíveis. Verifique se...
* ... o sistema dá suporte a acompanhamento de olho. Chame o seguinte *método*: [Windows. percepção. People. EyesPose. IsSupported ()](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* ... o usuário é calibrado. Chame a seguinte *Propriedade*: [Windows. percepção. People. EyesPose. IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)

* ... o usuário concedeu permissão ao seu aplicativo para usar seus dados de acompanhamento de olho: Recuperar o _' GazeInputAccessStatus '_ atual. Um exemplo de como fazer isso é explicado em [solicitando acesso à entrada olhar](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).

Além disso, talvez você queira verificar se os dados de acompanhamento de olho não estão obsoletos adicionando um tempo limite entre atualizações de dados de acompanhamento de olho recebido e, caso contrário, fallback para o Head-olhar, conforme discutido abaixo. 

Conforme descrito acima, há várias razões pelas quais os dados de acompanhamento de olho podem não estar disponíveis. Embora alguns usuários possam ter decidido a revogar o acesso aos seus dados de controle de olho e estão ok com a compensação de uma experiência de usuário inferior à privacidade de não fornecer acesso aos seus dados de controle de olho, em alguns casos isso pode não ser intencional. Portanto, se seu aplicativo usar o acompanhamento de olho, e essa for uma parte importante da experiência, recomendamos que você se comunique claramente com o usuário. Informando, de maneira adequada, o usuário por que o acompanhamento de olho é essencial para seu aplicativo (talvez até mesmo listar alguns recursos avançados) para experimentar todo o potencial do seu aplicativo pode ajudar o usuário a entender melhor o que está desistindo. Ajudar o usuário a identificar por que o controle de olhos pode não estar funcionando (com base nas verificações acima) e oferecer algumas sugestões para solucionar problemas em potencial rapidamente. Por exemplo, se você puder detectar que o sistema dá suporte ao controle de olho, o usuário é calibrado e até mesmo recebeu sua permissão, mas nenhum dado de acompanhamento de olho é recebido, isso pode apontar para alguns outros problemas, como manchas ou olhos sendo obstruído. Observe que há casos raros de usuários para os quais o acompanhamento de olho pode simplesmente não funcionar. Portanto, seja obedientes disso, permitindo descartar ou até mesmo desabilitar lembretes para habilitar o acompanhamento de olho em seu aplicativo.

### <a name="2-fallback-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>2. Fallback para aplicativos usando olhar de olho como um ponteiro de entrada primário
Se seu aplicativo usa olhar como uma entrada de ponteiro para selecionar rapidamente os hologramas em toda a cena, mas os dados de acompanhamento de olho não estão disponíveis, é recomendável fazer o fallback para Head-olhar e começar a mostrar o cursor Head-olhar. É recomendável usar um tempo limite (por exemplo, 500 – 1500 MS) para determinar se deseja ou não alternar. Isso é para evitar o pop-up de um cursor toda vez que o sistema pode perder o controle rapidamente devido a movimentos ou winks de olhos rápidos e cintilações. Se você for um desenvolvedor do Unity, o fallback automático para Head-olhar já será tratado no kit de ferramentas da realidade misturada. Se você for um desenvolvedor do DirectX, precisará lidar com esse comutador por conta própria.

### <a name="3-fallback-for-other-eye-tracking-specific-applications"></a>3. Fallback para outros aplicativos específicos de acompanhamento de olho
Seu aplicativo pode usar olhar de olho de forma exclusiva, especificamente para os olhos, por exemplo, para animar os olhos de um avatar ou para a atenção com base nos olhos, calor a depender de informações precisas sobre a atenção Visual. Nesse caso, não há nenhum fallback claro. Se o acompanhamento de olho não estiver disponível, esses recursos podem simplesmente ser desabilitados. 

<br>

Essa página espero que você tenha uma boa visão geral para começar a entender a função de acompanhamento de olho e a entrada olhar para o HoloLens 2. Para começar a desenvolver, confira nossas informações sobre [olhar no Unity](https://aka.ms/mrtk-eyes) e [olhar de olho no DirectX](gaze-in-directx.md).


## <a name="see-also"></a>Consulte também
* [Olho-olhar no DirectX](gaze-in-directx.md)
* [Olho-olhar no Unity (Kit de ferramentas de realidade misturada)](https://aka.ms/mrtk-eyes)
* [Calibragem](calibration.md)
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Gestos de mão](gestures.md)
* [Entrada de voz](voice-design.md)
* [Controladores de movimentos](motion-controllers.md)
* [Conforto](comfort.md)
