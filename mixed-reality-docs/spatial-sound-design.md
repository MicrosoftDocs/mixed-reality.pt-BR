---
title: Design de som espacial
description: Som espacial é uma ferramenta poderosa para uma imersão, acessibilidade e design UX em aplicativos de realidade misturada.
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, som espacial, design, estilo
ms.openlocfilehash: c758037300392d9365c16933677fb0f026976c2a
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750310"
---
# <a name="spatial-sound-design"></a>Design de som espacial

Som espacial é uma ferramenta poderosa para uma imersão, acessibilidade e design UX em aplicativos de realidade misturada.

Se você nunca foram executados [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game)), ou tivesse alguém chamar seu telefone para ajudar a localizá-lo, você já estiver familiarizado com a importância de som espacial. Podemos usar indicações de som em nossas vidas diárias para localizar objetos, atenção de alguém ou obter um melhor entendimento do nosso ambiente. Mais de perto o som do seu aplicativo se comporta, como ele faz no mundo real, o mais convencer e envolver que seu mundo virtual será.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
    </tr>
     <tr>
        <td>Design de som espacial</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a>Quatro coisas principais som espacial faz para o desenvolvimento de realidade misturada

Por padrão, sons são reproduzidos em estéreo. Isso significa que o som será reproduzido com nenhuma posição espacial, portanto, o usuário não sabe onde veio o som. Som espacial executa quatro tarefas principais para o desenvolvimento de realidade mista:

**Aterramento**

Sem som, os objetos virtuais efetivamente deixam de existir quando transformamos nossas head longe-los. Assim como objetos reais, você deseja ser capaz de ouvir esses objetos, mesmo quando você não pode vê-los, e você deseja ser capaz de localizá-los em qualquer lugar ao seu redor. Assim como os objetos virtuais precisam ser com aterramento visualmente para mesclar com o mundo real, eles precisam ser com aterramento poder ouvi-lo. Som espacial perfeitamente combina seu ambiente de áudio do mundo real com o ambiente de áudio digital.

**Atenção do usuário**

Experiências de realidade misturada, você não é possível supor em que o usuário está procurando e esperar que eles vejam algo que colocar visualmente no mundo. Mas os usuários sempre podem ouvir um som reproduzir mesmo quando o objeto de reprodução do som está por trás delas. As pessoas são usadas para ter sua atenção desenhada pelo som - instinctually veremos em direção a um objeto que ouvimos ao nosso redor. Quando você quiser direcionar olhar do usuário para um local específico, em vez de usar uma seta para apontá-los visualmente, colocando um som em que local é uma maneira muito natural e rápida para ajudá-los.

**Imersão**

Quando objetos move ou entrem em conflito, normalmente ouvimos dessas interações entre materiais. Portanto, quando seus objetos não faça o mesmo som fariam no mundo real, um nível de imersão serão perdido - assistindo a um filme assustador com o volume de todo o caminho para baixo. Todos os sons no mundo real provenientes de um determinado ponto no espaço - quando chamamos nossa atenção, ouvimos a alteração no onde esses sons vêm em relação a nossos ouvidos e podemos controlar o local de qualquer som dessa maneira. Sons spatialized compõem a "aparência" de um lugar além do que nós vemos.

**Design de interação**

Em experiências interativas mais tradicionais, os sons de interação como efeitos de som de interface do usuário são executados em mono padrão ou estéreo. Mas, porque tudo o que na realidade mista existe no espaço 3D - incluindo a interface do usuário - esses objetos se beneficiar de sons spatialized. Quando clicamos em um botão no mundo real, o som que ouvimos proveniente desse botão. Por spatializing sons de interação, fornecemos novamente uma experiência de usuário mais natural e realista.

## <a name="best-practices-when-using-spatial-sound"></a>Práticas recomendadas ao usar som espacial

**Sons real funcionam melhor do que sintetizada ou artificiais sons**

É o usuário quanto mais familiarizado com um tipo de som, o mais real sentirá, e mais fácil ele poderá localizá-lo em seu ambiente. Uma voz humana, por exemplo, é um tipo muito comum de som e que os usuários serão localizá-lo mais rápido como uma pessoa real na sala de falar com eles.

**Expectativa supera a simulação**

Se você está acostumado a um som provenientes de uma direção específica, sua atenção será orientada nessa direção, independentemente de indicações espaciais. Por exemplo, na maioria das vezes que ouvimos pássaros, eles estão acima conosco. Reproduzir o som de bird provavelmente causará o seu usuário a ser pesquisado, mesmo se você colocar o som abaixo deles. Isso é geralmente confuso, e é recomendável que você trabalhe com as expectativas, como esses em vez de em relação a eles uma experiência mais natural.

**A maioria dos sons devem ser spatialized**

Conforme mencionado acima, tudo o que na realidade mista existe no espaço 3D - os sons de devem também. Até mesma música, às vezes, pode se beneficiar de funcionamento em, especialmente quando ele está associado a um menu ou alguma outra interface de usuário.

**Evite os emissores invisíveis**

Porque estamos condicionados examinar sons que ouvimos nos cerca, ele pode ser uma experiência não natural e até mesmo unnerving para localizar um som que não tem visual presença. Sons no mundo real não vêm de espaço vazio, portanto, certifique-se que se um emissor de áudio é colocado dentro do ambiente de imediato do usuário que ele também pode ser visto.

**Evite mascaramento espacial**

Som espacial depende muito sutis indicações acústicas que podem ser sobrecarregadas por outros sons. Se você tiver música estéreo ou sons de ambientes, verifique se que eles estão baixos o suficiente na combinação para dar espaço para os detalhes de seu spatialized sons que permitem que os usuários localizá-los com facilidade e mantê-los soar realista e natural.

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a>Conceitos gerais para ter em mente ao usar som espacial

**Som espacial é uma simulação**

O uso mais frequente de som espacial está fazendo um som a parecer que ele é procedentes de um objeto real ou virtual do mundo. Assim, sons spatialized talvez façam mais sentido provenientes de tais objetos.

Observe que a precisão percebida de espacial significa som que não deve necessariamente emissão de um som do Centro de um objeto, como a diferença notável, dependendo do tamanho do objeto e da distância do usuário. Com objetos pequenos, o ponto central do objeto normalmente é suficiente. Para objetos maiores, talvez você queira um emissor de som ou vários emissores no local específico em um objeto que deve ser produzindo o som.

**Normalizar todos os sons**

Atenuação de distância rapidamente acontece dentro do primeiro medidor do usuário, como faz no mundo real. Todos os arquivos de áudio devem ser normalizados para garantir a atenuação de distância fisicamente precisos e certifique-se de que pode ser ouvido um som quando vários distância medidores (quando aplicável). O mecanismo de áudio espacial manipulará a necessários para um som "sentir" como ele está em uma determinada distância (com uma combinação de atenuação e "indicações de distância") e aplicar qualquer atenuação em cima dessa poderia reduzir o efeito de atenuação. Fora simulando um objeto real, inicial distância decaimento dos *som espacial* sons provavelmente será mais do que suficiente para apropriadas mistura de áudio.

**Interfaces de usuário e a descoberta de objeto**

Ao usar as indicações de áudio para chamar a atenção do usuário além do seu modo de exibição atual, o som deve ser audíveis e proeminentes na combinação, bem acima nenhum som estéreo e outros sons spatialized que podem atrapalhar o exame de indicação de áudio direcional. Para sons e músicas que estão associados um elemento da interface do usuário (por exemplo, um menu), o emissor de som deve ser anexado a esse objeto. Estéreo e outros não posicionais reproduzindo áudio podem dificultar o spatialized elementos para os usuários localizem (veja acima: Evite mascaramento espacial).

**Usar o som espacial som 3D padrão tanto quanto possível**

Na realidade mista, para a melhor experiência de usuário, 3D áudio deve ser feito usando o som espacial em vez de tecnologias de áudio 3D herdadas. Em geral, o funcionamento em aprimorado está vale o custo de CPU pequeno sobre padrão 3D de som. Padrão de áudio 3D pode ser usado para sons de baixa prioridade, sons spatialized, mas não necessariamente ligados a um objeto físico ou virtual e objetos que o usuário nunca precisa localizar para interagir com o aplicativo.

## <a name="see-also"></a>Consulte também
* [Som espacial](spatial-sound.md)
* [Mapeamento espacial](spatial-mapping.md)
