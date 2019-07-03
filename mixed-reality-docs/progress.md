---
title: Exibindo o progresso
description: Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, controles da interface do usuário, experiência do usuário
ms.openlocfilehash: 84853a23a73bbece30c1f96b83e586642f3ab762
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523256"
---
# <a name="displaying-progress"></a>Exibindo o progresso

Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento. Isso pode significar que o usuário não pode interagir com o aplicativo quando o indicador de progresso está visível e também pode indicar a duração do tempo de espera, dependendo do indicador usado.

![Exemplo de anel de progresso no HoloLens](images/HoloLens2_Loader.gif)<br>
*Exemplo de anel de progresso no HoloLens*

## <a name="types-of-progress"></a>Tipo de progresso

É importante fornecer as informações do usuário sobre o que está acontecendo. Na realidade mista que os usuários podem ser facilmente Distraídos com ambiente físico ou objetos se seu aplicativo não dá bons comentários visuais. Para situações que levam alguns segundos, como quando o carregamento de dados ou uma cena está atualizando, é recomendável para mostrar um indicador visual. Há duas opções para mostrar ao usuário que uma operação está em andamento – uma **barra de progresso** ou um **anel de progresso**.

### <a name="progress-bar"></a>Barra de progresso

![Exemplo de barra de progresso no HoloLens](images/640px-progressbar.jpg)

Uma barra de progresso mostra o percentual da conclusão de uma tarefa. Ele deve ser usado durante uma operação cuja duração é conhecida (determinada), mas seu andamento não deve bloquear a interação do usuário com o aplicativo.

### <a name="progress-ring"></a>Anel de progresso

![Exemplo de anel de progresso no HoloLens](images/640px-progressring.jpg)

Apenas um anel de progresso tem um estado indeterminado e deve ser usado quando qualquer interação adicional do usuário é bloqueada até que a operação foi concluída.

### <a name="progress-with-a-custom-object"></a>Progresso com um objeto personalizado

![Progresso com exemplo de malha personalizadas HoloLens](images/640px-progresscustom.jpg)

Você pode adicionar a personalidade e uma identidade visual do seu aplicativo, personalizando o controle de progresso com seus próprios objetos 2D/3D personalizados.

## <a name="best-practices"></a>Práticas recomendadas
* Acoplar rigidamente [billboarding ou tag-along](billboarding-and-tag-along.md) para a exibição do progresso, pois o usuário pode facilmente mover suas cabeças no espaço vazio e perder o contexto. Seu aplicativo pode parecer falhou se o usuário não conseguir ver nada. Billboarding e tag-along é incorporada no pré-fabricado progresso.
* É sempre bom fornecer informações de status sobre o que está acontecendo para o usuário. Pré-fabricado andamento fornece diversos estilos visuais, incluindo o progresso de padrão de tipo de anel do Windows para fornecer o status. Você também pode usar uma malha personalizada com uma animação, se você deseja que o estilo de seu progresso para alinhar à marca do seu aplicativo.

## <a name="see-also"></a>Consulte também
* [Pré-fabricados no Kit de ferramentas de realidade mista e scripts de progresso](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [caixa delimitadora](app-bar-and-bounding-box.md)
* [Objeto interativo](interactable-object.md)
* [Coleção de objetos](object-collection.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
