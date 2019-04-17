---
title: Estudo de caso - examinando buracos na sua realidade
description: Este estudo de caso explica como implementar o efeito de "janela de mágica" em HoloLens, permitindo que o usuário veja atrás paredes, sob o piso e nas aberturas virtuais no ambiente real.
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, janela mágica, parallax
ms.openlocfilehash: 0c0828a6ebbefdcff7f0a66f48469007c5c532df
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589722"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>Estudo de caso - examinando buracos na sua realidade

Quando as pessoas pensam em realidade mista e o que podem fazer com o Microsoft HoloLens, eles geralmente fique a perguntas como "Quais objetos posso adicionar ao meu quarto?" ou "O que pode, camada na parte superior do meu espaço?" Eu gostaria de destacar outra área que você pode considerar — essencialmente, um truque de mágica — usando a mesma tecnologia para procurar em ou por meio de objetos físicos real ao seu redor.

## <a name="the-tech"></a>O técnico

Se você já teve problemas alienígenas conforme eles Vença seus paredes  **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, desbloqueada uma parede segura em  **[fragmentos](case-study-creating-an-immersive-experience-in-fragments.md)**, ou estavam sorte Para ver o hangar UNSC infinito nas  **[experiência de Halo 5 no E3 em 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, então você já viu o que estou falando. Dependendo de sua imaginação, esse truque visual pode ser usado para colocar os buracos temporários no seu isolantes ou ocultar mundos sob um floorboard flexível.

![RoboRaid adiciona outra estrutura por trás de parede, visível somente por meio de furos criados conforme os invasores superem e Tubos tridimensionais.](images/roboraid-640px.png)

RoboRaid adiciona outra estrutura por trás de parede, visível somente por meio de furos criados conforme os invasores superem e Tubos tridimensionais.

Usando uma dessas hologramas exclusivas em HoloLens, um aplicativo pode fornecer a ilusão de conteúdo por trás da parede ou por meio de seu andar da mesma forma que se apresenta realidade por meio de uma janela real. Mover-se à esquerda, e você pode ver tudo o que está no lado direito. Aproxime-se, e você pode ver um pouco mais de tudo. A principal diferença é que brechas real permitem que você, enquanto o chão paralelizado não permitirá a subir por meio de até que o conteúdo holográfico mágico. (Vou adicionar uma tarefa à lista de pendências.)

## <a name="behind-the-scenes"></a>Nos bastidores

Esse truque é uma combinação de dois efeitos. Conteúdo em primeiro lugar, holographic é fixado ao mundo usando "âncoras espaciais". Usando âncoras para torná-lo "mundo bloqueada" significa que o que você está olhando não visualmente descompasso para longe de objetos físicos próximo a ele, mesmo quando você move ou seu modelo 3D de sua sala de atualizações de sistema subjacente do mapeamento espacial.

Em segundo lugar, esse conteúdo holográfico é visualmente limitado a um espaço muito específico, você só pode ver pelo orifício na sua realidade. Esse oclusão é necessário exigir examinando um buraco lógico, a janela ou a porta de entrada, que vende o truque. Sem alguma coisa que a maioria do modo de exibição de bloqueio, deixarem no espaço para uma dimensão Jurássico secreta pode apenas ter aparência um dinossauro mal posicionado.

![Isso não é uma captura de tela real, mas uma ilustração de como o mundo virtual secreto do MR Noções básicas de 101 aparece no HoloLens. O compartimento preto não é exibida, mas você pode ver o conteúdo por meio de um buraco virtual. (Ao procurar por meio de um dispositivo real, o chão parece desaparecer ainda mais porque os olhos se concentrar em uma distância mais como se ele não estiver lá mesmo.)](images/origamiholecomposited-640px.png)

Isso não é uma captura de tela real, mas uma ilustração de como o mundo virtual secreta do [MR Noções básicas de 101](holograms-101.md) se parece em HoloLens. O compartimento preto não é exibida, mas você pode ver o conteúdo por meio de um buraco virtual. (Ao procurar por meio de um dispositivo real, o chão parece desaparecer ainda mais porque os olhos se concentrar em uma distância mais como se ele não estiver lá mesmo.)

### <a name="world-locking-holographic-content"></a>Bloqueio de mundo holográfico conteúdo

No Unity, fazendo com que o conteúdo holográfico permanecer bloqueado pelo mundo é tão fácil quanto adicionar um componente WorldAnchor:

```
myObject.AddComponent<WorldAnchor>();
```

O componente WorldAnchor constantemente ajustará a posição e rotação de seu GameObject (e, portanto, qualquer outra coisa abaixo desse objeto na hierarquia) para mantê-lo estável relativo nas proximidades de objetos físicos. Quando a criação de seu conteúdo, você deve criá-lo de tal forma que o pivô de raiz de seu objeto é centralizado nesse buraco virtual. (Se dinâmico do objeto é aprofundado na parede, seus pequenos ajustes em posição e rotação será muito mais perceptíveis, e a brecha pode não parecer muito estável.)

### <a name="occluding-everything-but-the-virtual-hole"></a>Occluding tudo, exceto o espaço virtual

Há várias maneiras para bloquear seletivamente o modo de exibição para o que está oculto na parede. Aquele mais simples se beneficia do fato de que o HoloLens usa uma exibição aditiva, o que significa que objetos totalmente pretos aparecem invisíveis. Você pode fazer isso no Unity sem fazer qualquer sombreador especial ou materiais truques — basta criar um material preto e atribuí-lo a um objeto que as caixas no seu conteúdo. Se você não quiser fazer de modelagem 3D, basta usar alguns dos objetos de Quad padrão e se sobrepõem-los um pouco. Há várias desvantagens nessa abordagem, mas é a maneira mais rápida para obter algo em funcionamento e introdução de baixa fidelidade prova de trabalho de conceito é ótimo, mesmo se você suspeitar de que talvez você queira refatorá-lo mais tarde.

Uma grande desvantagem para a abordagem de "caixa preta" acima é que ele não fotografar bem. Embora o efeito possa parecer perfeito por meio da exibição do HoloLens, qualquer capturas de tela que você tomar mostrará um objeto grande preto, em vez do que continua a sua parede ou andar. A razão para isso é que a realidade e hologramas composição físicas de hardware e capturas de tela diferente. Vamos desvio por um momento para alguns cálculos matemáticos de falso...

*Alerta de matemática falso! Esses números e fórmulas destinam-se a ilustrar um ponto, para não ser de qualquer tipo de métrica precisa!*

O que você vê por meio do HoloLens:

```
( Reality * darkening_amount ) + Holograms
```

O que você vê na tela e capturas de vídeo:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

Em inglês: O que você vê por meio do HoloLens é uma combinação simple de realidade escurecida (como por meio de óculos) e tudo o que hologramas o aplicativo deseja mostrar. Mas quando você faz uma captura de tela, a imagem da câmera é combinada com hologramas do aplicativo de acordo com o valor de transparência por pixel.

Uma maneira de contornar esse problema é alterar o material de "caixa preta" para que apenas gravar no buffer de profundidade e classificar com todos os outros materiais opacos. Para obter um exemplo disso, confira a [WindowOcclusion.shader o arquivo em que o MixedRealityToolkit no GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader). As linhas relevantes são copiadas aqui:

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(Observe o "deslocamento 50, 100" linha é lidar com problemas não relacionados, para que ele provavelmente faria sentido deixar que o.)

Implementar um material de oclusão invisível como essa permitirá que seu aplicativo desenhar uma caixa que se parece correta na exibição e nas capturas de tela de realidade misturada. Para pontos de bônus, você pode tentar melhorar o desempenho dessa caixa ainda mais fazendo coisas inteligentes para desenhar o mesmo menos pixels invisíveis, mas isso realmente pode obter o supérfluo e geralmente não será necessário.

![Aqui está o mundo virtual secreto do MR Noções básicas de 101, como Unity desenha a ele, exceto para as partes externas da caixa de ferramentas occluding. Observe que dinâmico para o mundo virtual está no centro da caixa, que ajuda a manter a brecha mais estável possível em relação ao seu floor real.](images/underworld-occluded-640px.png)

Aqui está o mundo virtual secreta da [MR Noções básicas de 101](holograms-101.md) como Unity desenha a ele, exceto para as partes externas da caixa de ferramentas occluding. Observe que dinâmico para o mundo virtual está no centro da caixa, que ajuda a manter a brecha mais estável possível em relação ao seu floor real.

## <a name="do-it-yourself"></a>Faça você mesmo

Ter um HoloLens e deseja testar o efeito para si mesmo? A coisa mais fácil, você pode fazer (sem necessidade de codificação) é instalar o aplicativo visualizador 3D gratuito e, em seguida, carregar o [download the.fbx arquivo fornecidas no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) para exibir um modelo de pot da flor na sua sala. Carregá-lo em HoloLens, e você pode ver a ilusão no trabalho. Quando você estiver na frente do modelo, você só pode ver no pequeno orifício — todo o resto é invisível. Examinar o modelo de qualquer outro lado e desaparecer inteiramente. Use a movimentação, rotação e dimensionamento controles de visualizador 3D para posicionar o buraco virtual contra qualquer superfície vertical, que você pode pensar para gerar algumas ideias!

![Exibindo a esse modelo em seu editor do Unity mostrará uma caixa preta grande em torno de flowerpot. Em HoloLens, a caixa desaparece, dando a maneira como um efeito de janela mágico.](images/magicwindowflowerpotineditor.png)

Exibindo a esse modelo em seu editor do Unity mostrará uma caixa preta grande em torno de flowerpot. Em HoloLens, a caixa desaparece, dando a maneira como um efeito de janela mágico.

Se você quiser criar um aplicativo que usa essa técnica, confira a [tutorial MR fundamentos 101](holograms-101.md) na [Academy de realidade mista](academy.md). Capítulo 7 termina com uma explosão em suas instalações que revela um mundo virtual oculto (como na imagem acima). Quem disse tutoriais tinham que ser sem graça?

Aqui estão algumas ideias de onde você pode pegar essa ideia Avançar:
* Pensamos em maneiras de tornar o conteúdo dentro de buraco virtual interativo. Permitindo que os usuários ter algum impacto além dos seus murais realmente pode melhorar o sentido de se estranhar que esse truque pode fornecer.
* Pense em maneiras de ver por meio de objetos para áreas conhecidos. Por exemplo, como você colocar um buraco holográfico em sua tabela de café e consulte seu floor abaixo dele?

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>Engenheiro sênior de Software @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também
* [Noções básicas sobre MR 101: Projeto completo do dispositivo](holograms-101.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Âncoras espaciais](spatial-anchors.md)
* [Mapeamento espacial](spatial-mapping.md)
