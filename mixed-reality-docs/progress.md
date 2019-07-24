---
title: Exibindo progresso
description: Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, controles, interface do usuário, UX
ms.openlocfilehash: 84853a23a73bbece30c1f96b83e586642f3ab762
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523256"
---
# <a name="displaying-progress"></a>Exibindo progresso

Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento. Isso pode significar que o usuário não pode interagir com o aplicativo quando o indicador de progresso está visível e também pode indicar a duração do tempo de espera, dependendo do indicador usado.

![Exemplo de anel de andamento no HoloLens](images/HoloLens2_Loader.gif)<br>
*Exemplo de anel de andamento no HoloLens*

## <a name="types-of-progress"></a>Tipo de progresso

É importante fornecer as informações do usuário sobre o que está acontecendo. Em realidade misturada, os usuários podem ser facilmente distraídosdos por ambientes físicos ou objetos se seu aplicativo não fornecer bons comentários visuais. Para situações que levam alguns segundos, como quando os dados estão sendo carregados ou uma cena está atualizando, é recomendável mostrar um indicador visual. Há duas opções para mostrar ao usuário que uma operação está em andamento – uma **barra de progresso** ou um **anel de progresso**.

### <a name="progress-bar"></a>Barra de progresso

![Exemplo de barra de progresso no HoloLens](images/640px-progressbar.jpg)

Uma barra de progresso mostra a porcentagem concluída de uma tarefa. Ele deve ser usado durante uma operação cuja duração é conhecida (desterminada), mas o progresso não deve bloquear a interação do usuário com o aplicativo.

### <a name="progress-ring"></a>Anel de progresso

![Exemplo de anel de andamento no HoloLens](images/640px-progressring.jpg)

Um anel de progresso tem apenas um estado indeterminado e deve ser usado quando qualquer interação adicional do usuário é bloqueada até que a operação seja concluída.

### <a name="progress-with-a-custom-object"></a>Progresso com um objeto personalizado

![Progresso com o exemplo de malha personalizada no HoloLens](images/640px-progresscustom.jpg)

Você pode adicionar à identidade da marca e personalidade do seu aplicativo Personalizando o controle de progresso com seus próprios objetos 2D/3D personalizados.

## <a name="best-practices"></a>Práticas recomendadas
* Associe rigidamente a [mensagem ou a marca](billboarding-and-tag-along.md) à exibição do progresso, uma vez que o usuário pode mover facilmente o cabeçalho para o espaço vazio e perder o contexto. Seu aplicativo pode parecer que ele falhou se o usuário não conseguir ver nada. A cobrança e a marcação são criadas no pré-fabricado de progresso.
* É sempre bom fornecer informações de status sobre o que está acontecendo com o usuário. O progresso pré-fabricado fornece vários estilos visuais, incluindo o progresso padrão do Windows do tipo de toque para fornecer o status. Você também pode usar uma malha personalizada com uma animação se quiser que o estilo do seu progresso se alinhe à marca do seu aplicativo.

## <a name="see-also"></a>Consulte também
* [Scripts de progresso e pré-fabricados no kit de ferramentas de realidade misturada](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [Caixa delimitadora](app-bar-and-bounding-box.md)
* [Objeto interativo](interactable-object.md)
* [Coleção de objetos](object-collection.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
