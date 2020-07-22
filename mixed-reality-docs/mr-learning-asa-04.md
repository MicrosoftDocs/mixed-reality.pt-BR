---
title: Tutoriais de Âncoras Espaciais do Azure – 4. Exibir comentários de Âncoras Espaciais do Azure
description: Conclua este curso para saber como implementar as Âncoras Espaciais do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d221a7e64bda7a6dabf76b60c7bff7c6333666ef
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303917"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a>4. Exibir comentários das Âncoras Espaciais do Azure

Neste tutorial, você aprenderá a fornecer comentários sobre a descoberta de âncora, eventos e status aos usuários ao usar o ASA (Âncoras Espaciais do Azure).

## <a name="objectives"></a>Objetivos

* Saber como configurar um painel de interface do usuário que exibe informações essenciais sobre a sessão atual do ASA
* Saber e explorar os elementos de comentários que o SDK do ASA disponibiliza para os usuários

## <a name="setting-up-asa-feedback-panel"></a>Configurar o painel de comentários do ASA

Na janela Hierarquia, clique com o botão direito do mouse no objeto **Instruções** > **TextContent**. Selecione **Objeto 3D** > **Text – TextMeshPro** para criar um objeto de texto TextMeshPro como um filho do objeto Instruções > TextContent:

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> Para facilitar o trabalho com sua cena, defina a <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Visibilidade da Cena</a> para o objeto ParentAnchor como off clicando no ícone de olho à esquerda do objeto. Isso oculta o objeto na janela Cena sem alterar a visibilidade no jogo.

Renomeie o objeto Texto (TMP) recém criado **Comentários** e, na janela Inspetor, altere sua posição e tamanho para que ele seja posicionado de maneira organizada, abaixo do texto de instrução, por exemplo:

* Altere a **Pos Y** do componente do Rect Transform para -0,24.
* Altere a **Largura** do componente do Rect Transform para 0,555.
* Altere a **Altura** do componente do Rect Transform para 0,1.

Em seguida, escolha as propriedades da fonte para que o texto caiba bem na área de texto, por exemplo:

* Altere o **Estilo da Fonte** do componente de texto – TextMeshPro para negrito.
* Altere o **Tamanho da Fonte** do componente de texto – TextMeshPro para 0,17.
* Altere o **Alinhamento** do componente de texto – TextMeshPro para Centro e Meio.

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-2.png)

Na janela Hierarquia, selecione o objeto **Comentários** e, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Script de Comentários de Âncora (Script)** e configure-o da seguinte maneira:

* Atribua o objeto **Comentários** ao campo **Texto do Comentário** do componente **Script de Comentário da Âncora (Script)** .

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a criar um painel de interface do usuário. Ele exibe o status atual da experiência de Âncoras Espaciais do Azure para fornecer comentários em tempo real aos usuários.

[Próximo tutorial: 5. Âncoras Espaciais do Azure para o Android e o iOS](mr-learning-asa-05.md)
