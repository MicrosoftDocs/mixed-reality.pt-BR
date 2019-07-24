---
title: Design de som espacial
description: O som espacial é uma ferramenta poderosa para imersão, acessibilidade e design de UX em aplicativos de realidade misturada.
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, som espacial, design, estilo
ms.openlocfilehash: c758037300392d9365c16933677fb0f026976c2a
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750310"
---
# <a name="spatial-sound-design"></a>Design de som espacial

O som espacial é uma ferramenta poderosa para imersão, acessibilidade e design de UX em aplicativos de realidade misturada.

Se você já tiver jogado [Marco aquático](https://en.wikipedia.org/wiki/Marco_Polo_(game))ou alguém ligar para seu telefone para ajudá-lo a localizá-lo, você já está familiarizado com a importância do som espacial. Usamos indicações de som em nossas vidas diárias para localizar objetos, obter a atenção de alguém ou obter uma compreensão melhor de nosso ambiente. Quanto mais próximo o som do seu aplicativo se comparecer com o mundo real, mais convincente e envolvente seu mundo virtual será.

<br>

> [!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Design de som espacial</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a>As quatro principais coisas que o som espacial faz para o desenvolvimento de realidade misturada

Por padrão, os sons são reproduzidos no estéreo. Isso significa que o som será tocado sem nenhuma posição espacial, portanto, o usuário não sabe de onde veio o som. O som espacial faz quatro coisas importantes para o desenvolvimento de realidade misturada:

**Aterramento**

Sem som, os objetos virtuais deixam de existir efetivamente quando viramos o nosso nosso rumo. Assim como os objetos reais, você deseja ser capaz de ouvir esses objetos mesmo quando não consegue vê-los e deseja localizá-los em qualquer lugar em sua parte. Assim como os objetos virtuais precisam ser aterrados visualmente para misturar com o mundo real, eles também precisam ser forma audíveldos. O som espacial combina diretamente o seu ambiente de áudio real no mundo inteiro com o ambiente de áudio digital.

**Atenção do usuário**

Em experiências de realidade misturada, você não pode supor onde seu usuário está olhando e esperar que eles vejam algo que você coloca no mundo visualmente. Mas os usuários sempre podem ouvir uma reprodução de som mesmo quando o objeto que está tocando o som está por trás deles. As pessoas são usadas para ter sua atenção desenhada por som-nós instinctuallymos em direção a um objeto que ouvimos em nosso lugar. Quando você deseja direcionar o olhar do usuário para um local específico, em vez de usar uma seta para apontar visualmente, colocar um som nesse local é uma maneira muito natural e rápida de orientá-los.

**Imersão**

Quando os objetos se movem ou colidem, geralmente ouvimos essas interações entre os materiais. Então, quando os objetos não fazem o mesmo som que fariam no mundo real, um nível de imersão é perdido, como assistir a um filme assustador com o volume em todo o caminho. Todos os sons do mundo real são provenientes de um ponto específico no espaço, quando viramos nossos cabeçotes, ouvimos a alteração de onde esses sons estão vindos em relação aos nossos ouvidos e podemos acompanhar o local de qualquer som dessa maneira. Os sons espaciais formam a "sensação" de um lugar além do que podemos ver.

**Design de interação**

Na maioria das experiências interativas tradicionais, a interação parece que os efeitos de som da interface do usuário são reproduzidos em mono ou estéreo padrão. Mas como tudo em realidade misturada existe no espaço 3D-incluindo a interface do usuário-esses objetos se beneficiam de sons espaciais. Quando pressionamos um botão no mundo real, o som que ouvimos é proveniente desse botão. Ao espacialar os sons de interação, fornecemos novamente uma experiência de usuário mais natural e realista.

## <a name="best-practices-when-using-spatial-sound"></a>Práticas recomendadas ao usar som espacial

**Sons reais funcionam melhor do que sons sintetizados ou não naturais**

Quanto mais familiar o usuário estiver com um tipo de som, mais real ele se sentirá e, mais facilmente, ele poderá localizá-lo em seu ambiente. Uma voz humana, por exemplo, é um tipo muito comum de som, e os usuários vão localizá-lo tão rapidamente quanto uma pessoa na sala conversando com eles.

**Simulação de trunfos de expectativa**

Se você for usado para um som proveniente de uma determinada direção, sua atenção será guiada nessa direção, independentemente das indicações espaciais. Por exemplo, na maioria das vezes que ouvimos pássaros, eles estão acima dos EUA. Tocar o som de um pássaro provavelmente fará com que o usuário pesquise, mesmo que você coloque o som abaixo deles. Isso geralmente é confuso e é recomendável que você trabalhe com expectativas como essas em vez de ir contra elas para uma experiência mais natural.

**A maioria dos sons deve ser espacial**

Conforme mencionado acima, tudo em realidade misturada existe no espaço 3D-seus sons também devem ser. Às vezes, as músicas podem se beneficiar da espacial, especialmente quando estão ligadas a um menu ou a alguma outra interface do usuário.

**Evitar emissores invisíveis**

Como temos sido condicionados a olhar os sons que ouvimos em nosso lugar, pode ser uma experiência não natural e até mesmo unnerving para localizar um som que não tenha nenhuma presença Visual. Os sons do mundo real não vêm de espaço vazio, então certifique-se de que se um emissor de áudio for colocado dentro do ambiente imediato do usuário que ele também possa ser visto.

**Evitar mascaramento espacial**

O som espacial se baseia em indicações acústicas muito sutis que podem ser sobreligadas por outros sons. Se você tiver música estéreo ou sons de ambiente, verifique se eles são baixos o suficiente na combinação para dar espaço para os detalhes de seus sons espaciais que permitirão que os usuários os localizem facilmente e os mantenham informais reais e naturais.

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a>Conceitos gerais para ter em mente ao usar som espacial

**O som espacial é uma simulação**

O uso mais frequente de som espacial é fazer com que pareça que ele está emanando de um objeto real ou virtual no mundo. Assim, os sons espaciais podem fazer mais sentido provenientes desses objetos.

Observe que a precisão percebida do som espacial significa que um som não deve ser necessariamente emitido a partir do centro de um objeto, pois a diferença será perceptível, dependendo do tamanho do objeto e da distância do usuário. Com objetos pequenos, o ponto central do objeto geralmente é suficiente. Para objetos maiores, você pode querer um emissor de som ou vários emissores no local específico dentro do objeto que deve estar produzindo o som.

**Normalizar todos os sons**

A atenuação de distância ocorre rapidamente no primeiro medidor do usuário, como faz no mundo real. Todos os arquivos de áudio devem ser normalizados para garantir a atenuação de distância fisicamente precisa e garantir que um som possa ser ouvido quando houver vários medidores de distância (quando aplicável). O mecanismo de áudio espacial tratará a atenuação necessária para um som "sentir" como está em uma determinada distância (com uma combinação de atenuação e "indicações de distância") e a aplicação de qualquer atenuação sobre isso pode reduzir o efeito. Fora da simulação de um objeto real, a distância inicial decaimento de sons de *som espaciais* provavelmente será mais do que suficiente para uma combinação adequada do seu áudio.

**Descoberta de objeto e interfaces de usuário**

Ao usar as indicações de áudio para direcionar a atenção do usuário para além de sua exibição atual, o som deve ser audível e proeminente na mistura, bem acima de qualquer som estéreo, e quaisquer outros sons espaciais que possam atrapalhar a indicação de áudio direcional. Para sons e músicas associados a um elemento da interface do usuário (por exemplo, um menu), o emissor de som deve ser anexado a esse objeto. O estéreo e outra reprodução de áudio não posicional podem dificultar a localização de elementos espaciais para os usuários (veja acima: Evite mascaramento espacial).

**Usar som espacial sobre som 3D padrão o máximo possível**

Em realidade misturada, para a melhor experiência do usuário, o áudio 3D deve ser obtido usando o som espacial em vez de tecnologias de áudio 3D herdadas. Em geral, a espacial aprimorada vale a pena ter um pequeno custo de CPU em relação ao som 3D padrão. O áudio 3D padrão pode ser usado para sons de baixa prioridade, sons que são espaciais, mas não necessariamente vinculados a um objeto físico ou virtual, e os objetos que o usuário nunca precisam localizar para interagir com o aplicativo.

## <a name="see-also"></a>Consulte também
* [Som espacial](spatial-sound.md)
* [Mapeamento espacial](spatial-mapping.md)
