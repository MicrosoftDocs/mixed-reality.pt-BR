---
title: Tutoriais de âncoras espaciais do Azure-3. Exibindo comentários de âncora espacial do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 3d762950ea8e211fd5a8e4cf8af717674d3fe7e1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553914"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. exibindo comentários de âncora espacial do Azure

Neste tutorial, você aprenderá a fornecer aos usuários comentários sobre a descoberta de âncora, eventos e status ao usar o ASA (âncoras espaciais) do Azure.

## <a name="objectives"></a>Objetivos

* Saiba como configurar um painel de interface do usuário que exibe informações importantes sobre a sessão atual do ASA
* Entender e explorar os elementos de comentários que o SDK do ASA disponibiliza para os usuários

## <a name="set-up-asa-feedback-ui-panel"></a>Configurar o painel de IU de comentários do ASA

Na janela hierarquia, clique com o botão direito do mouse nas **instruções** > objeto **textcontent** e selecione **objeto 3D** > **Text-TextMeshPro** para criar um objeto de texto TextMeshPro como um filho das instruções > objeto textcontent e dê a ele um nome adequado, por exemplo, **comentários**:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> Para facilitar o trabalho com sua cena, defina a visibilidade da <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">cena</a> para o objeto ParentAnchor como off clicando no ícone de olho à esquerda do objeto. Isso oculta o objeto na janela cena sem alterar sua visibilidade no jogo.

Com o objeto de **comentários** ainda selecionado, na janela Inspetor, altere sua posição e tamanho para que ele seja posicionado de forma organizada, abaixo do texto de instrução, por exemplo:

* Alterar a transformação Rect **pos Y** para-0,24
* Altere a **largura** do Rect Transform para 0,555
* Altere a **altura** do Rect Transform para 0,1

Em seguida, escolha Propriedades da fonte para que o texto caiba bem na área de texto, por exemplo:

* Altere o **estilo de fonte** pro (script) de malha de texto para negrito
* Altere o **tamanho da fonte** do pro (script de malha de texto) para 0,17
* Alterar o **alinhamento** pro (script) da malha de texto para o centro e o meio

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

Com o objeto de **comentários** ainda selecionado, na janela Inspetor, use o botão **Adicionar componente** para adicionar o componente **script de âncora de comentário (script)** ao objeto de comentários:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

Atribua o próprio objeto de **comentários** ao campo de **texto de comentários** do componente script de **âncora (script)** :

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a criar um painel de interface do usuário para exibir o status atual da experiência de ancoragem espacial do Azure para fornecer aos usuários comentários em tempo real.
