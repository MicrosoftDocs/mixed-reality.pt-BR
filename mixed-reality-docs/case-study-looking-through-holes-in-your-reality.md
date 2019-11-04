---
title: Estudo de caso-examinando os buracos em sua realidade
description: Este estudo de caso explica como implementar o efeito de "janela mágica" no HoloLens, permitindo que o usuário veja por trás das paredes, sob o andar e em aberturas virtuais dentro de seu ambiente real.
author: EricRehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, janela mágica, da Parallax
ms.openlocfilehash: a1b9f0b2e576379846a867f3d3bffef7d8ec277e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436671"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>Estudo de caso-examinando os buracos em sua realidade

Quando as pessoas consideram a realidade misturada e o que elas podem fazer com o Microsoft HoloLens, elas normalmente se transformam em perguntas como "quais objetos posso adicionar à minha sala?" ou "o que posso fazer na camada acima do meu espaço?" Gostaria de destacar outra área que você pode considerar — essencialmente um truque mágico — usando a mesma tecnologia para examinar ou por meio de objetos físicos reais em seu lugar.

## <a name="the-tech"></a>O Tech

Se você lutaram alienígenas à medida que passa pelas paredes no **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** , desbloqueou uma parede com segurança em **[fragmentos](case-study-creating-an-immersive-experience-in-fragments.md)** , ou se houve sorte suficiente para ver o UNSC infinito hangar na **[experiência do Halo 5 em E3 em 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)** , você já viu o que estou falando. Dependendo da sua imaginação, esse truque visual pode ser usado para colocar buracos temporários em seu isolante ou ocultar mundos sob um Floorboard flexível.

![RoboRaid adiciona pipes tridimensionais e outra estrutura por trás de suas paredes, visíveis somente por meio de buracos criados à medida que os invasores se dividem.](images/roboraid-640px.png)

RoboRaid adiciona pipes tridimensionais e outra estrutura por trás de suas paredes, visíveis somente por meio de buracos criados à medida que os invasores se dividem.

Usando um desses hologramas exclusivos no HoloLens, um aplicativo pode fornecer a ilusão de conteúdo por trás de suas paredes ou de seu andar da mesma forma que a realidade se apresenta por meio de uma janela real. Mova-se para a esquerda e veja o que está no lado direito. Fique mais próximo, e você pode ver um pouco mais de tudo. A principal diferença é que os buracos reais permitem que você, enquanto o stubbornly de chão não permitirá que você percorra o conteúdo do mágico Holographic. (Adicionarei uma tarefa à pendência.)

## <a name="behind-the-scenes"></a>Nos bastidores

Esse truque é uma combinação de dois efeitos. Primeiro, o conteúdo do Holographic é fixado no mundo usando "âncoras espaciais". O uso de âncoras para tornar esse conteúdo "bloqueado pelo mundo" significa que o que você está vendo não se afasta visual dos objetos físicos próximos, mesmo quando você move ou o sistema de mapeamento espacial subjacente atualiza seu modelo 3D de sua sala.

Em segundo lugar, esse conteúdo do Holographic é visualmente limitado a um espaço muito específico, para que você possa ver apenas por meio do orifício em sua realidade. Esse oclusão é necessário para exigir a análise de um buraco lógico, janela ou porta, que vende o truque. Sem algo bloqueando a maior parte da exibição, uma quebra no espaço para uma dimensão Jurássico secreta poderia parecer um dinossauro mal posicionado.

![Essa não é uma captura de tela real, mas uma ilustração de como o segredo Underworld do Sr Basics 101 procura no HoloLens. O compartimento preto não aparece, mas você pode ver o conteúdo por meio de um buraco virtual. (Ao examinar um dispositivo real, o andar parece desaparecer ainda mais porque seus olhos se concentram em uma distância maior, como se não fosse mesmo lá).](images/origamiholecomposited-640px.png)

Essa não é uma captura de tela real, mas uma ilustração de como o segredo Underworld do [Sr basics 101](holograms-101.md) procura no HoloLens. O compartimento preto não aparece, mas você pode ver o conteúdo por meio de um buraco virtual. (Ao examinar um dispositivo real, o andar parece desaparecer ainda mais porque seus olhos se concentram em uma distância maior, como se não fosse mesmo lá).

### <a name="world-locking-holographic-content"></a>Conteúdo do Holographic de bloqueio mundial

No Unity, fazer com que o conteúdo do Holographic permaneça bloqueado pelo mundo é tão fácil quanto adicionar um componente WorldAnchor:

```
myObject.AddComponent<WorldAnchor>();
```

O componente WorldAnchor ajustará constantemente a posição e a rotação de seu gameobject (e, portanto, qualquer outra coisa nesse objeto na hierarquia) para mantê-lo estável em relação aos objetos físicos próximos. Ao criar seu conteúdo, crie-o de forma que o pivô raiz do seu objeto seja centralizado nessa brecha virtual. (Se o pivô do seu objeto for profundo na parede, seus pequenos ajustes em posição e rotação serão muito mais perceptíveis e o orifício poderá não parecer muito estável.)

### <a name="occluding-everything-but-the-virtual-hole"></a>Occluding tudo, exceto a brecha virtual

Há várias maneiras de bloquear seletivamente a exibição para o que está oculto em suas paredes. O mais simples aproveita o fato de que o HoloLens usa uma exibição aditiva, o que significa que objetos totalmente pretos aparecem invisíveis. Você pode fazer isso no Unity sem fazer nenhum sombreador especial ou truques de material — basta criar um material preto e atribuí-lo a um objeto que caixas no seu conteúdo. Se você não sentir como fazer a modelagem 3D, use apenas alguns objetos Quad padrão e sobreponha-os ligeiramente. Há várias desvantagens nessa abordagem, mas é a maneira mais rápida de fazer algo funcionar, e ter uma prova de conceito de baixa fidelidade funcionando muito bem, mesmo que você suspeite que talvez queira refatorá-lo mais tarde.

Uma grande desvantagem da abordagem da "caixa preta" acima é que ela não é bem fotografada. Embora seu efeito possa parecer perfeito com a exibição do HoloLens, todas as capturas de tela que você tomarão mostrarão um grande objeto preto em vez do que resta de sua parede ou andar. O motivo disso é que o hardware físico e as capturas de tela compõem os hologramas e a realidade de forma diferente. Vamos desvio por um momento em alguma matemática falsa...

*Alerta de matemática falsa! Esses números e fórmulas destinam-se a ilustrar um ponto, não ser qualquer tipo de métrica precisa!*

O que você vê por meio do HoloLens:

```
( Reality * darkening_amount ) + Holograms
```

O que você vê em capturas de tela e vídeo:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

Em inglês: o que você vê por meio do HoloLens é uma combinação simples de realidade escurecida (como por meio de óculos) e de qualquer holograma que o aplicativo queira mostrar. Mas quando você faz uma captura de tela, a imagem da câmera é combinada com os hologramas do aplicativo de acordo com o valor de transparência por pixel.

Uma maneira de contornar isso é alterar o material de "caixa preta" para gravar apenas no buffer de profundidade e classificar todos os outros materiais opacos. Para obter um exemplo disso, confira o [arquivo WindowOcclusion. Shader no MixedRealityToolkit no GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader). As linhas relevantes são copiadas aqui:

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(Observe que a linha "offset 50, 100" é lidar com problemas não relacionados, portanto, provavelmente faria sentido deixar isso.)

Implementar um material oclusão invisível como esse permitirá que seu aplicativo desenhe uma caixa que pareça correta na tela e em capturas de tela de realidade misturada. Para pontos de bônus, você pode tentar melhorar o desempenho dessa caixa ainda mais, fazendo coisas inteligentes para desenhar até mesmo alguns pixels invisíveis, mas isso pode realmente se aprofundar e normalmente não será necessário.

![Aqui está o segredo Underworld do Sr Basics 101, pois o Unity o desenha, exceto pelas partes externas da caixa occluding. Observe que o pivô para o Underworld está no centro da caixa, o que ajuda a manter o orifício o mais estável possível em relação ao seu piso real.](images/underworld-occluded-640px.png)

Aqui está o segredo Underworld do [Sr basics 101](holograms-101.md) , pois o Unity o desenha, exceto pelas partes externas da caixa occluding. Observe que o pivô para o Underworld está no centro da caixa, o que ajuda a manter o orifício o mais estável possível em relação ao seu piso real.

## <a name="do-it-yourself"></a>Faça você mesmo

Tem um HoloLens e deseja experimentar o efeito para si mesmo? A coisa mais fácil que você pode fazer (sem codificação necessária) é instalar o aplicativo de visualizador 3D gratuito e, em seguida, carregar o [download do arquivo. FBX que forneci no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) para exibir um modelo de flor de flores em sua sala. Carregue-o no HoloLens e você pode ver a ilusão no trabalho. Quando estiver na frente do modelo, você só poderá ver na pequena brecha — tudo o mais estará invisível. Examine o modelo de qualquer outro lado e ele desaparece inteiramente. Use os controles de movimentação, rotação e escala do visualizador 3D para posicionar o orifício virtual em relação a qualquer superfície vertical que você possa considerar para gerar algumas ideias!

![A exibição desse modelo no editor do Unity mostrará uma grande caixa preta em volta do flowerpot. No HoloLens, a caixa desaparece, dando uma forma a um efeito de janela mágica.](images/magicwindowflowerpotineditor.png)

A exibição desse modelo no editor do Unity mostrará uma grande caixa preta em volta do flowerpot. No HoloLens, a caixa desaparece, dando uma forma a um efeito de janela mágica.

Se você quiser criar um aplicativo que usa essa técnica, confira o [tutorial do Sr basics 101](holograms-101.md) nos [tutoriais de realidade misturada](tutorials.md). O capítulo 7 termina com uma explosão no andar que revela um Underworld oculto (como mostrado acima). Quem disse que os tutoriais precisavam ser enfadonhos?

Aqui estão algumas ideias de onde você pode tomar essa ideia em seguida:
* Considere maneiras de tornar o conteúdo dentro do buraco virtual interativo. Permitir que os usuários tenham algum impacto além das suas paredes pode realmente melhorar o sentido de imaginar que esse truque pode fornecer.
* Imagine maneiras de ver os objetos de volta para as áreas conhecidas. Por exemplo, como você pode colocar um buraco de Holographic em sua mesa de café e ver seu andar abaixo dele?

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>Engenheiro de software sênior @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também
* [Sr Basics 101: concluir o projeto com o dispositivo](holograms-101.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Âncoras espaciais](spatial-anchors.md)
* [Mapeamento espacial](spatial-mapping.md)
