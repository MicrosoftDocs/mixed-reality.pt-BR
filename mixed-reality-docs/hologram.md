---
title: O que é um holograma?
description: O HoloLens permite exibir e interagir com hologramas tridimensionais, objetos compostos de luz e som que aparecem no mundo todo.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, hologramas, design, interação
ms.openlocfilehash: 714b08db23aa641252291aebe89fa3059c209a6f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829786"
---
# <a name="what-is-a-hologram"></a>O que é um holograma?

O HoloLens permite criar **hologramas**, objetos compostos de luz e som que aparecem no mundo, assim como se fossem objetos reais. Os hologramas respondem aos seus [olhar](gaze.md), [gestos](gestures.md) e [comandos de voz](voice-input.md)e podem interagir com [superfícies reais](spatial-mapping.md) em todo o mundo. Com os hologramas, você pode criar objetos digitais que fazem parte do seu mundo.

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

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
        <td>Hologramas</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a>Um holograma é formado de luz e som

Os hologramas que o HoloLens [renderiza](rendering.md) aparecem no quadro Holographic diretamente na frente dos olhos do usuário. Os hologramas adicionam luz ao seu mundo, o que significa que você vê a luz da tela e a luz de seus arredores. O HoloLens não remove a luz dos seus olhos, portanto, os hologramas não podem ser renderizados com a cor preta. Em vez disso, o conteúdo preto aparece como transparente.

Os hologramas podem ter várias aparências e comportamentos diferentes. Alguns são realísticos e sólidos, e outros são animados e o Ethereal. Os hologramas podem destacar recursos no seu ambiente e podem ser elementos na interface do usuário do aplicativo.

![Holographic Dog no chão](images/fang3-640px.jpg)

Os hologramas também podem fazer [sons](spatial-sound.md), que parecerão vir de um local específico em seus arredores. No HoloLens, o som vem de dois alto-falantes que estão localizados diretamente acima de seus ouvidos, sem cobri-los. Semelhante às telas, os alto-falantes são aditivos, apresentando novos sons sem bloquear os sons do seu ambiente.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Um holograma pode ser colocado no mundo ou em uma marca junto com você

Quando você tem um local específico onde deseja um holograma, você pode [colocá](coordinate-systems.md) -lo precisamente no mundo. À medida que você percorre esse holograma, ele parecerá estável em relação ao mundo em seu lugar. Se você usar uma [âncora espacial](coordinate-systems.md#spatial-anchors) para fixar esse objeto firmemente ao mundo, o sistema poderá até mesmo lembrar onde você o deixou quando voltar mais tarde.

![Holographic criando maquette sentado em uma tabela](images/image5-640px.png)

Em vez disso, alguns hologramas seguem o usuário. Esses hologramas de marcas são posicionados em relação ao usuário, independentemente de onde eles se movimentam. Você pode até mesmo optar por trazer um holograma com você por um tempo e colocá-lo na parede quando chegar a outra sala.

**Práticas recomendadas**
* Alguns cenários podem exigir que os hologramas permaneçam facilmente detectáveis ou visíveis em toda a experiência. Há duas abordagens de alto nível para esse tipo de posicionamento. Vamos chamá-los de **"display-Locked"** e **"Body-Locked"** .
   * O conteúdo bloqueado de exibição é posicionado "bloqueado" na tela do dispositivo. Isso é complicado por vários motivos, incluindo uma sensação não natural de "clingyness" que torna muitos usuários frustrados e querendo "agite-los". Em geral, muitos designers acharam melhor evitar conteúdo de bloqueio de exibição.
   * A abordagem de corpo bloqueado é muito mais forgivable. O bloqueio de corpo é quando um holograma é vinculado ao corpo do usuário ou ao vetor olhar, mas está posicionado no espaço 3D em todo o usuário. Muitas experiências adotaram um comportamento de bloqueio de corpo onde o holograma "segue" os usuários olhar, o que permite ao usuário girar seu corpo e percorrer o espaço sem perder o holograma. Incorporar um atraso ajuda o movimento do holograma a se sentir mais natural. Por exemplo, alguma interface do usuário principal do sistema operacional Windows Holographic usa uma variação no bloqueio de corpo que segue o olhar do usuário com um atraso de AdaBoost e elástico, enquanto o usuário transforma sua cabeça.
* Coloque o holograma em uma distância de exibição confortável, normalmente, cerca de 1-2 metros longe do início.
* Forneça uma quantidade de descompasso para elementos que devem estar continuamente no quadro Holographic ou considere animar seu conteúdo para um lado da exibição quando o usuário alterar seu ponto de vista.

**Coloque os hologramas na zona ideal-entre 1,25 m e 5 min**

Dois medidores são os mais ideais e a experiência diminuirá quanto mais perto você chegar de um medidor. Às distâncias mais próximas de um medidor, os hologramas que se movem regularmente em profundidade têm maior probabilidade de serem problemáticos do que os hologramas fixos. Considere recortar ou desbotar seu conteúdo de forma elegante quando ficar muito próximo, para não desconectar o usuário em uma experiência inesperada.

![Distância ideal para colocar os hologramas do usuário.](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Um holograma interage com você e seu mundo

Os hologramas não são apenas sobre luz e som; Eles também são uma parte ativa do seu mundo. Olhar com um holograma e um gesto com sua mão, e um holograma pode começar a acompanhá-lo. Dê um comando de voz para um holograma e ele pode responder.

![Design de Holographic Motorcycle ajustado em um corpo Motorcycle de vida real](images/image8-640px.png)

Os hologramas permitem interações pessoais que não são possíveis em outro lugar. Como o HoloLens sabe onde ele está no mundo, um caractere Holographic pode examiná-lo diretamente nos olhos à medida que você percorre a sala.

Um holograma também pode interagir com seus arredores. Por exemplo, você pode inserir uma bola saltando Holographic acima de uma tabela. Em seguida, com um [toque de ar](gestures.md#air-tap), observe o salto de bola e faça o som quando ele atingir a tabela.

Os hologramas também podem ser obstruídodos por objetos do mundo real. Por exemplo, um caractere Holographic pode percorrer uma porta e atrás de uma parede, fora de sua visão.

**Dicas para integrar hologramas e o mundo real**
* Alinhar às regras do Gravitational torna os hologramas mais fáceis de se relacionar e mais verossímeis. por exemplo, Coloque um cachorro Holographic no chão & um vaso na tabela em vez de tê-los flutuantes no espaço.
* Muitos designers descobriram que eles podem ainda mais believably integrar hologramas criando uma "sombra negativa" na superfície em que o holograma está sentado. Eles fazem isso criando um brilho suave no chão ao lado do holograma e subtraindo a "sombra" do brilho. O brilho suave se integra com a luz do mundo real e a sombra aterra o holograma no ambiente.

## <a name="a-hologram-is-whatever-you-dream-up"></a>Um holograma é aquilo que você sonhou

Como desenvolvedor de Holographic, você tem a capacidade de dividir sua criatividade em telas 2D e em seu mundo. O que *você* vai criar?

![Holographic imaginário mundial na sala de vida](images/designoverview.jpg)

## <a name="see-also"></a>Consulte também
* [Som espacial](spatial-sound.md)
* [Cor, luz e materiais](color,-light-and-materials.md)
