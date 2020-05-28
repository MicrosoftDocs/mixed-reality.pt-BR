---
title: Interação com base no foco com o olhar
description: O HoloLens 2 permite um nível novo de contexto e entendimento humano dentro da experiência holográfica, fornecendo aos desenvolvedores a capacidade de usar as informações sobre o que os usuários estão vendo. Esta página aborda as recomendações de design para os desenvolvedores que desejam usar olhar como uma entrada.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Acompanhamento de olho, realidade misturada, entrada, olho-olhar
ms.openlocfilehash: 2ae7723f116771986edc757f1c9d4f454b0a256f
ms.sourcegitcommit: b0d15083ec1095e08c9d776e5bae66b4449383bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84111034"
---
# <a name="eye-gaze-based-interaction-on-hololens-2"></a>Interação baseada em olhar no HoloLens 2

![Demonstração de controle de olho no MRTK](images/mrtk_et_scenemenu.jpg)

Um dos nossos novos recursos empolgantes no HoloLens 2 é o acompanhamento dos olhos.
Em nossa página de [acompanhamento de olho no HoloLens 2](eye-tracking.md) , mencionamos a necessidade de cada usuário passar por uma [calibração](https://docs.microsoft.com/hololens/hololens-calibration), fornecemos algumas diretrizes para desenvolvedores e casos de uso destacados para acompanhamento de olho.
Olho – a entrada olhar ainda é um tipo bem novo de entrada de usuário e há muito a aprender. Embora a entrada olhar seja usada de forma muito sutil em nossa experiência de Shell de Holographic (a interface do usuário que você vê ao iniciar o seu HoloLens 2), vários aplicativos, como o ["HoloLens playground"](https://www.microsoft.com/p/mr-playground/9nb31lh723s2), demonstram ótimos exemplos de como as informações de olhar de entrada podem ser adicionadas à mágica da sua experiência com o Holographic.
Nesta página, discutiremos as considerações de design para integrar a entrada olhar para interagir com seus aplicativos Holographic.
Você aprenderá sobre as principais vantagens e também desafios exclusivos que acompanham a entrada olhar.  
Com base nesses, fornecemos várias recomendações de design para ajudá-lo a criar interfaces de usuário com suporte olhar. 

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
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
</tr>
<tr>
     <td>Olho-olhar</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>


## <a name="eye-gaze-input-design-guidelines"></a>Diretrizes de design de entrada olhar
A criação de uma interação que aproveita o direcionamento de olho rápido pode ser desafiadora. Nesta seção, resumimos as principais vantagens e desafios a serem considerados ao projetar seu aplicativo. 

### <a name="benefits-of-eye-gaze-input"></a>Benefícios da entrada olhar
- **Apontar com alta velocidade.** O olho capacidade é o capacidade mais rápido de reagir no corpo humano. 

- **Pouco esforço.** Quase nenhum movimento físico é necessário. 

- **Capacidade de ser implícito.** Geralmente descritas pelos usuários como "leitura mental", as informações sobre os movimentos de um usuário permitem que o sistema saiba qual alvo o usuário planeja participar. 

- **Canal de entrada alternativo.** O olho-olhar pode fornecer uma poderosa entrada de suporte para a mão e entrada de voz em anos de experiência de usuários com base em sua coordenação de olhos.

- **Atenção visual.** Outro benefício importante é a possibilidade de inferir o que um usuário está prestando a atenção. Isso pode ajudar em várias áreas de aplicativos que vão desde a avaliação de diferentes designs para auxiliar em interfaces de usuário mais inteligentes e indicações sociais aprimoradas para comunicação remota.

Resumindo, usar olhar como uma entrada oferece um sinal de entrada contextual rápido e sem esforço. Isso é particularmente poderoso quando combinado com outras entradas, como *voz* e entrada *manual* , para confirmar a intenção do usuário.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Desafios de olhar de olho como uma entrada
Com muita potência, vem muito de responsabilidade.
Embora os olhos olhar possam ser usados para criar experiências de usuário satisfatórias que fazem você sentir como um Superhero, também é importante saber o que não é bom para se considerar adequadamente. O a seguir discute alguns *desafios* a serem considerados e como solucioná-los ao trabalhar com a entrada de olhar de olho: 

- **Seu olho-olhar é "Always on"** No momento em que você abre suas tampas de olho, seus olhos começam a fixatingr sobre as coisas no ambiente. Reagir a todas as aparências que você fizer e emitir ações acidentalmente, porque você examinou algo por muito tempo, resultaria em uma experiência que não satisfaça.
Portanto, é recomendável combinar olhars de olho com um *comando de voz*, um *gesto de mão*, um clique de *botão* ou uma pesquisa estendida para disparar a seleção de um destino (para obter mais informações, consulte [olhar de olho e confirmação](gaze-and-commit-eyes.md)).
Essa solução também permite um modo no qual o usuário pode procurar livremente sem ser sobrecarregado por disparar involuntariamente algo. Esse problema também deve ser considerado ao criar comentários sobre Visual e auditoria ao examinar um destino.
Tente não sobrecarregar o usuário com efeitos pop-out imediatos ou sons de foco. A sutileza é fundamental. Discutiremos algumas práticas recomendadas para isso mais adiante, ao falar sobre [recomendações de design](eye-gaze-interaction.md#design-recommendations).

- **Observação vs. controle** Imagine que você deseja endireitar precisamente uma fotografia em sua parede. Você olha para as bordas da fotografia e em volta dela para ver se ela fica bem alinhada. Agora imagine como você faria isso quando quiser usar seu olho-olhar como uma entrada para mover a imagem. Difícil, não é mesmo? Isso descreve a função dupla de olhar quando é necessário para entrada e controle. 

- **Sair antes de clicar em:** Para seleções de destino rápido, a pesquisa mostrou que o olhar de olho do usuário pode passar antes de concluir um clique manual (por exemplo, um toque de ar). Portanto, atenção especial deve ser paga para sincronizar o sinal de olhar rápido com entrada de controle mais lenta (por exemplo, voz, mãos, controlador).

- **Destinos pequenos:** Você sabe a sensação quando tenta ler um texto que é um pouco pequeno demais para ler confortavelmente? Essa sensação de sobrecarregar seus olhos pode fazer com que você fique cansado e desgastado, pois você tenta reajustar os olhos para se concentrar melhor.
Essa é uma sensação que você pode invocar em seus usuários ao forçá-los a selecionar destinos que são muito pequenos em seu aplicativo usando o direcionamento de olho.
Para o design, visando criar uma experiência agradável e confortável para seus usuários, recomendamos que os alvos tenham um ângulo visual de, pelo menos, 2°, preferencialmente maior.

- **Olhos irregulares – movimentos olhars** Nossos olhos realizam movimentos rápidos do fixação da para o fixação da. Se você examinar os caminhos de exame dos movimentos oculares registrados, poderá ver que eles parecem irregulares. Seus olhos se movem rapidamente e em saltos ESPONTANEOS em comparação com os *olhar* ou os *movimentos de mão*.  

- **Confiabilidade de rastreamento:** A precisão do controle de olho pode diminuir um pouco a luz de alteração à medida que seus olhos se ajustam às novas condições.
Embora isso não deva afetar necessariamente o design do aplicativo, uma vez que a precisão deve estar dentro da limitação de 2 °, pode ser necessário que o usuário calibre novamente. 


## <a name="design-recommendations"></a>Recomendações sobre design
Veja a seguir uma lista de recomendações de design específicas com base nas vantagens e nos desafios descritos para a entrada de olhar de olho:

1. **Olho-olhar não é o mesmo que Head-olhar:**
    - **Considere se movimentos de olho rápidos e irregulares se ajustam à sua tarefa de entrada:** Embora nossos movimentos de olho rápidos e irregulares sejam ótimos na seleção rápida de destinos em nosso campo de exibição, ele é menos aplicável para tarefas que exigem trajetórias de entrada suaves (por exemplo, desenho ou ennotamento de anotações). Nesse caso, apontar com a mão ou a cabeça deve ser preferencial.
  
    - **Evite anexar algo diretamente ao olhar de olho do usuário (por exemplo, um controle deslizante ou cursor).**
No caso de um cursor, isso pode resultar em um efeito de "cursor fleeing" devido a pequenos deslocamentos no sinal olhar de olho projetado. No caso de um controle deslizante, ele pode entrar em conflito com a função dupla de controlar o controle deslizante com seus olhos, enquanto também deseja verificar se o objeto está no local correto. Para o exemplo do controle deslizante, faz mais sentido usar olhar de olho em combinação com gestos de mão. Isso significa que o usuário pode alternar de forma rápida e sem esforço entre vários controles deslizantes, levantando sua mão e Pinçando seu polegar e indexar o dedo para pegar e movê-lo. Quando o pinçamento é liberado, o controle deslizante para de mover. Resumindo, os usuários poderiam se tornar sobrecarregados e distraídoss, especialmente se o sinal for impreciso para esse usuário. 
  
2. **Combine olho-olhar com outras entradas:** A integração do controle de olho com outras entradas, como gestos à mão, comandos de voz ou prensas de botão, oferece várias vantagens:
    - **Permita a observação gratuita:** Considerando que a função principal de nossos olhos é observar nosso ambiente, é importante que os usuários tenham permissão para olhar sem disparar qualquer comentário ou ação (Visual, auditoria, etc.). 
    Combinar o controle de olho com outro controle de entrada permite a transição tranqüila entre a observação de acompanhamento de olho e os modos de controle de entrada.
  
    - **Provedor de contexto poderoso:** O uso de informações sobre onde e o que o usuário está observando ao dizer um comando de voz ou a execução de um gesto de mão permite canalizar diretamente a entrada entre os campos de exibição. Por exemplo: digamos _"colocar isso"_ para selecionar e posicionar um holograma de forma rápida e fluente em toda a cena simplesmente observando um destino e seu destino pretendido. 

    - **Precisa de sincronização de entradas de multimodal:** Combinar movimentos de olhos rápidos com entradas adicionais mais complexas, como comandos de voz longos ou gestos de mão, tem o risco que o usuário já continua a examinar antes que o comando de entrada adicional seja concluído e reconhecido. Portanto, se você criar seus próprios controles de entrada (por exemplo, gestos de mão personalizada), certifique-se de registrar o início dessa entrada ou duração aproximada para correlacioná-lo com o que um usuário examinou no passado.
    
3. **Comentários sutis para entrada de acompanhamento de olho:** É útil fornecer comentários quando um destino é examinado para indicar que o sistema está funcionando como pretendido, mas deve ser mantido sutil. Isso pode incluir a mistura lenta, a entrada e a saída dos destaques visuais ou a execução de outros comportamentos de destino sutis, como movimentos lentos, como o aumento ligeiramente do tamanho de destino, para indicar que o sistema detectou corretamente que o usuário está olhando para um destino sem interromper desnecessariamente o fluxo de trabalho atual do usuário. 

4. **Evite impor movimentos de olho não naturais como entrada:** Não force os usuários a executar movimentos de olho específicos (gestos de olhar) para disparar ações em seu aplicativo.

5. **Conta para imprecisãos:** Distinguemos dois tipos de impedições que são perceptíveis para os usuários: deslocamento e Tremulação. A maneira mais fácil de resolver um deslocamento é fornecer destinos suficientemente grandes para interagir com o. É recomendável que você use um ângulo visual maior que 2 ° como referência. Por exemplo, sua miniatura é de cerca de 2 ° no ângulo visual quando você amplia seu braço. Isso resulta nas seguintes diretrizes:
    - Não force os usuários a selecionar pequenos destinos. A pesquisa mostrou que se os destinos são suficientemente grandes e que o sistema foi projetado bem, os usuários descrevem suas interações como sem esforço e mágico. Se os alvos ficarem muito pequenos, os usuários descreverão a experiência como cansativa e frustrante.
  
<br>

Esta página forneceu uma boa visão geral para ajudá-lo a começar a entender os olhos olhar como uma entrada na realidade misturada. Para começar a desenvolver, confira nossas informações sobre [olhar no Unity](https://aka.ms/mrtk-eyes) e [olhar de olho no DirectX](gaze-in-directx.md).


## <a name="see-also"></a>Consulte também
* [Conforto](comfort.md)
* [Olho-olhar no DirectX](gaze-in-directx.md)
* [Olho-olhar no Unity (Kit de ferramentas de realidade misturada)](https://aka.ms/mrtk-eyes)
* [Acompanhamento ocular no HoloLens 2](eye-tracking.md)
* [Focar e confirmar](gaze-and-commit.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Entrada de voz](voice-design.md)
