---
title: Tutoriais de Âncoras Espaciais do Azure – 3. Exibir os comentários da Âncora Espacial do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 62ce1151837a345dea1bea4a8bea275cc851b9bd
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866896"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Exibir os comentários da Âncora Espacial do Azure

Neste tutorial, você aprenderá a fornecer aos usuários comentários sobre a descoberta de âncora, eventos e status ao usar o ASA (Âncoras Espaciais do Azure).

## <a name="objectives"></a>Objetivos

* Saiba como configurar um painel de interface do usuário que exibe informações importantes sobre a sessão atual do ASA
* Entender e explorar os elementos de comentários que o SDK do ASA disponibiliza para os usuários

## <a name="set-up-asa-feedback-ui-panel"></a>Configurar o painel da interface do usuário de feedback do ASA

Na janela Hierarquia, clique com o botão direito do mouse no objeto **Instruções** > **TextContent** e selecione **Objeto 3D** > **Texto – TextMeshPro** para criar um objeto de texto TextMeshPro como um filho do objeto Instruções > TextContent e dar a ele um nome adequado, como **Comentários**:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> Para facilitar o trabalho com sua cena, defina a <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Visibilidade da Cena</a> para o objeto ParentAnchor como off clicando no ícone de olho à esquerda do objeto. Isso oculta o objeto na janela Cena sem alterar a visibilidade no jogo.

Com o objeto **Comentários** ainda selecionado, na janela Inspetor, altere sua posição e tamanho para que ele seja posicionado de maneira organizada, abaixo do texto de instrução, por exemplo:

* Alterar a **Pos Y** de Rect Transform para -0,24
* Alterar a **Largura** de Rect Transform para 0,555
* Alterar a **Altura** de Rect Transform para 0,1

Em seguida, escolha as propriedades da fonte para que o texto caiba bem na área de texto, por exemplo:

* Alterar o **Estilo da Fonte** do Text Mesh Pro (Script) para Negrito
* Alterar o **Tamanho da Fonte** do Text Mesh Pro (Script) para 0,17
* Alterar o **Alinhamento** do Text Mesh Pro (Script) para Centro e Meio

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

Com o objeto **Comentários** ainda selecionado, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Script de Comentários da Âncora (Script)** ao objeto Comentários:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

Atribua o objeto **Feedback** ao campo **Texto do Feedback** do componente **Script de Feedback da Âncora (Script)** :

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a criar um painel da interface do usuário para exibir o status atual da experiência de Âncora Espacial do Azure para fornecer aos usuários feedback em tempo real.

[Próxima lição: 4. Âncoras Espaciais do Azure para o Android e o iOS](mrlearning-asa-ch4.md)
