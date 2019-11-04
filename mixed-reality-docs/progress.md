---
title: Exibindo progresso
description: Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, controles, interface do usuário, UX
ms.openlocfilehash: 43b4802e7c821c98c847509ace950f381da12f95
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437532"
---
# <a name="displaying-progress"></a>Exibindo progresso

<br>

<img src="images/HoloLens2_Loader.gif" alt="Progress ring example in HoloLens" width="940px">

Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento. Isso pode significar que o usuário não pode interagir com o aplicativo quando o indicador de progresso está visível e também pode indicar a duração do tempo de espera, dependendo do indicador usado.

<br>

---

## <a name="types-of-progress"></a>Tipo de progresso

É importante fornecer as informações do usuário sobre o que está acontecendo. Em realidade misturada, os usuários podem ser facilmente distraídosdos por ambientes físicos ou objetos se seu aplicativo não fornecer bons comentários visuais. Para situações que levam alguns segundos, como quando os dados estão sendo carregados ou uma cena está atualizando, é recomendável mostrar um indicador visual. Há duas opções para mostrar ao usuário que uma operação está em andamento – uma **barra de progresso** ou um **anel de progresso**.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>Barra de progresso<br>
        Uma barra de progresso mostra a porcentagem concluída de uma tarefa. Ele deve ser usado durante uma operação cuja duração é conhecida (desterminada), mas o progresso não deve bloquear a interação do usuário com o aplicativo.<br>
        <br>
        *Imagem: exemplo de barra de progresso no HoloLens*
    :::column-end:::
        :::column:::
        ![de espaço](images/spacer-20x582.png)<br>
       ![exemplo de barra de progresso no HoloLens](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>Anel de progresso<br>
        Um anel de progresso tem apenas um estado indeterminado e deve ser usado quando qualquer interação adicional do usuário é bloqueada até que a operação seja concluída.<br>
        <br>
        *Imagem: exemplo de anel de andamento no HoloLens*
    :::column-end:::
        :::column:::
        ![de espaço](images/spacer-20x582.png)<br>
       ![exemplo de anel de progresso no HoloLens](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>Progresso com um objeto personalizado<br>
        Você pode adicionar à identidade da marca e personalidade do seu aplicativo Personalizando o controle de progresso com seus próprios objetos 2D/3D personalizados.<br>
        <br>
        *Imagem: progresso com o exemplo de malha personalizada no HoloLens*
    :::column-end:::
        :::column:::
        ![de espaço](images/spacer-20x582.png)<br>
       ![andamento com o exemplo de malha personalizada no HoloLens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>Práticas recomendadas
* Associe rigidamente a [mensagem ou a marca](billboarding-and-tag-along.md) à exibição do progresso, uma vez que o usuário pode mover facilmente o cabeçalho para o espaço vazio e perder o contexto. Seu aplicativo pode parecer que ele falhou se o usuário não conseguir ver nada. A cobrança e a marcação são criadas no pré-fabricado de progresso.
* É sempre bom fornecer informações de status sobre o que está acontecendo com o usuário. O progresso pré-fabricado fornece vários estilos visuais, incluindo o progresso padrão do Windows do tipo de toque para fornecer o status. Você também pode usar uma malha personalizada com uma animação se quiser que o estilo do seu progresso se alinhe à marca do seu aplicativo.

<br>

---

## <a name="see-also"></a>Consulte também
* [Scripts de progresso e pré-fabricados no kit de ferramentas de realidade misturada](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [Caixa delimitadora](app-bar-and-bounding-box.md)
* [Objeto interativo](interactable-object.md)
* [Coleção de objetos](object-collection.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
