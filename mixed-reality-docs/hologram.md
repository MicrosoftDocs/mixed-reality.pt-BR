---
title: O que é um holograma?
description: HoloLens permite exibir e interagir com hologramas tridimensionais, feitas de objetos de luz e som que aparecem no mundo ao seu redor.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, hologramas, design e interação
ms.openlocfilehash: 5a6cc4df764b1f92f6bea2d7d6e6effe2164e4d6
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589139"
---
# <a name="what-is-a-hologram"></a>O que é um holograma?

HoloLens permite que você crie **hologramas**, feita de objetos de luz e som que aparecem no mundo, assim como se fossem objetos reais. Hologramas respondem à sua [olhares](gaze.md), [gestos](gestures.md) e [comandos de voz](voice-input.md)e pode interagir com [superfícies do mundo real](spatial-mapping.md) ao seu redor. Com hologramas, você pode criar objetos digitais que fazem parte do seu mundo.

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> Hologramas</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a>Um holograma é feito da luz e som

As hologramas que HoloLens [renderiza](rendering.md) aparecem no quadro holográfico diretamente na frente de atenção do usuário. Hologramas adicionam luz ao seu mundo, o que significa que você verá a luz da exibição e a luz do seu ambiente. HoloLens não remove a luz do seus olhos, portanto, hologramas não podem ser renderizadas com a cor pretas. Em vez disso, o conteúdo preto aparece como transparente.

Hologramas podem ter várias aparências diferentes e comportamentos. Alguns são realistas e sólida e outras são quadrinhos e ethereal. Hologramas podem realçar os recursos nos arredores e podem ser elementos na interface do usuário do seu aplicativo.

![Cachorro holográfico walking no chão](images/fang3-640px.jpg)

Hologramas também podem fazer [sons](spatial-sound.md), que parecerá vir de um local específico em seu ambiente. Em HoloLens, som vem dos alto-dois falantes localizados diretamente acima do ouvido, sem falar sobre eles. Assim como as exibições, são de alto-falantes aditiva, introduzindo novos sons sem bloquear os sons de seu ambiente.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Um holograma pode ser colocado no mundo ou marca junto com você

Quando você tem um local específico em que você deseja um holograma, você pode [colocar](coordinate-systems.md) -lo com precisão no mundo. Conforme percorrer esse holograma, ele será exibido estável em relação ao mundo você. Se você usar um [âncora espacial](coordinate-systems.md#spatial-anchors) para fixar esse objeto firmemente para o mundo, o sistema pode até mesmo Lembre-se de onde ela for deixada quando voltar mais tarde.

![Maquette construção holográfica sentado em uma tabela](images/image5-640px.png)

Alguns hologramas siga o usuário em vez disso. Esses hologramas tag-along posicionam por conta própria em relação ao usuário, não importa onde eles percorrer. Você ainda pode optar por trazer um holograma com você por um tempo e, em seguida, coloque-o na parede depois de abrir outra sala.

**Práticas recomendadas**
* Alguns cenários podem exigir que hologramas permanecem visível em toda a experiência ou facilmente identificável. Há duas abordagens de alto nível para esse tipo de posicionamento. Vamos chamá-los **"exibição bloqueada"** e **"corpo bloqueada"**.
   * Bloqueado para exibição de conteúdo é posições "bloqueado" para a tela do dispositivo. Isso é complicado de inúmeros motivos, incluindo uma sensação artificial de "clingyness" que faz com que muitos usuários frustrados e desejam "livrá-lo." Em geral, muitos designers encontrá-lo melhor evitar o bloqueio de exibição de conteúdo.
   * A abordagem de bloqueado o corpo é muito mais forgivable. Bloqueio de corpo é quando um holograma é vinculado ao corpo do usuário ou olhar vetor, mas está posicionado no espaço 3d em torno do usuário. Muitas experiências adotaram um comportamento de bloqueio de corpo onde o holograma "segue" olhar a usuários, que permite ao usuário girar o corpo e percorrer o espaço sem perder o holograma. Incorporar um atraso ajuda a movimentação de holograma parecer mais natural. Por exemplo, alguns principais da interface do usuário do SO Windows Holographic usa uma variação no corpo de bloqueio que segue a olhar do usuário com um atraso suave, semelhante ao Elástico, enquanto o usuário virar suas cabeças.
* Coloque o holograma em uma distância de visualização confortável normalmente cerca de 1 a 2 metros longe no cabeçalho.
* Fornecem uma quantidade maior de descompasso para elementos que devem ser continuamente no quadro holográfico ou considere animando seu conteúdo em um lado da tela quando o usuário altera seu ponto de vista.

**Coloque hologramas na zona ideal - entre m 1,25 e 5 min**

Dois medidores é o ideal e a experiência prejudicará o mais próximo você chegar de um metro. Em distâncias quanto mais próxima de um medidor, são mais prováveis de ser problemática do que hologramas estacionários hologramas move regularmente em profundidade. Considere normalmente recorte ou desaparecimento seu conteúdo quando fica muito próximo então, como não jar do usuário em uma experiência inesperada.

![Distância ideal para posicionamento hologramas do usuário.](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Um holograma interage com você e seu mundo

Hologramas não trata apenas de luz e som; Eles também são uma parte ativa do seu mundo. Olhar em uma holograma e gesto com sua mão e um holograma pode começar a seguir, você. Dê um comando de voz para um holograma, e ele pode responder.

![Design de motocicleta holográfica ajustado no corpo de uma motocicleta da vida real](images/image8-640px.png)

Hologramas habilitam interações pessoais que não são possíveis em outro lugar. Como o HoloLens sabe onde ele está no mundo, um caractere holográfico pode examinar você diretamente aos olhos enquanto você anda por sala.

Um holograma também pode interagir com seu ambiente. Por exemplo, você pode colocar uma bola saltitante holográfica acima de uma tabela. Em seguida, com um [polegar](gestures.md#air-tap), assista a bola bater e tornar som quando ele atinge a tabela.

Também podem ser obstruídas hologramas por objetos do mundo real. Por exemplo, um caractere holográfico pode percorrer por meio de uma porta e por trás de uma parede, fora de sua Vista.

**Dicas para a integração hologramas e o mundo real**
* Alinhando às regras gravitacional hologramas relacionar a facilita e torna mais verossímeis. eg: Coloque um cachorro holographic em zero e um vaso na tabela em vez de fazer com que eles flutuando no espaço.
* Muitos designers descobriram que eles podem integrar ainda mais believably hologramas criando uma "sombra negativa" na superfície do que o holograma está situada sobre a. Eles fazem isso criando um leve brilho no chão em torno de holograma e subtraindo o "sombra" de brilho. O brilho reversível integra-se a luz do mundo real e sombra aterra o holograma no ambiente.

## <a name="a-hologram-is-whatever-you-dream-up"></a>Um holograma é tudo o que você imaginar

Como um desenvolvedor holográfico, você tem a capacidade de quebrar sua criatividade para fora de telas 2D e para o mundo ao. O que será *você* compilar?

![Mundo imaginário holográfico na sala](images/designoverview.jpg)

## <a name="see-also"></a>Consulte também
* [Som espacial](spatial-sound.md)
* [Cor, luz e materiais](color,-light-and-materials.md)
