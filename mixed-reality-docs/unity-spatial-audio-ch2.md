---
title: Tutoriais de áudio espacial-2. Sons de interação do botão de espacial
description: Adicione um botão ao seu projeto e espaciale os sons de interação do botão.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial
ms.openlocfilehash: bd70e3bc88ee39b2c6257089ac3a2b93dfae0ad1
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182773"
---
# <a name="spatializing-button-interaction-sounds"></a>Sons de interação do botão de espacial

## <a name="objectives"></a>Objetivos
Neste segundo capítulo do módulo de áudio espacial dos tutoriais do HoloLens 2, você irá:
* Adicionar um botão
* Espaciale o botão clique em sons

## <a name="add-a-button"></a>Adicionar um botão
No painel **projeto** , selecione **ativos** e digite "PressableButtonHoloLens2" na barra de pesquisa:

![Botão pré-fabricado em ativos](images/spatial-audio/button-prefab-in-assets.png)

O botão pré-fabricado é a entrada representada por um ícone azul, em vez de um ícone branco. Arraste o pré-fabricado chamado **PressableButtonHoloLens2** para o painel **hierarquia** . No painel **Inspetor** do botão novo, defina a propriedade **Position** como (0,-0,4, 2) para que ela apareça na frente do usuário quando o aplicativo for iniciado. O componente de **transformação** do botão terá a seguinte aparência:

![Transformação de botão](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a>Comentar o botão espacial
Nesta etapa, você causará a espacial dos comentários de áudio para o botão. Para obter sugestões de design relacionadas, consulte [design de som espacial](spatial-sound-design.md). 

O painel **mixer de áudio** é onde você definirá destinos, chamados de grupos de **mixers**, para reprodução de áudio de componentes de **fonte de áudio** . 
* Abra o painel **mixer de áudio** na barra de menus usando o mixer de áudio do > de **áudio > do Windows**
* Crie um **mixer** clicando no sinal de ' + ' ao lado dos **mixers**. O novo mixer incluirá um **grupo** padrão chamado **Master**.

O painel do **mixer** agora terá esta aparência:

![Painel do mixer com o primeiro mixer](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> Até que o verbo de reverberação esteja habilitado no [capítulo 5](unity-spatial-audio-ch5.md), o medidor de volume do mixer não mostra a atividade de sons reproduzidos por meio do Microsoft Spatializer

Clique no **PressableButtonHoloLens2** no painel **hierarquia** . No painel **Inspetor** :
1. Localizar o componente **fonte de áudio**
2. Para a propriedade **saída** , clique no seletor e escolha seu mixer
3. Marque a caixa de seleção **espacialize**
4. Mova o controle deslizante de **mistura espacial** para 3D (1).

> [!NOTE]
> Em versões do Unity anteriores a 2019, a caixa de seleção ' Espacialize ' está na parte inferior do painel do **Inspetor** para a **fonte de áudio**.

Após essas alterações, o componente **fonte de áudio** de seu **PressableButtonHoloLens2** terá a seguinte aparência:

![Fonte de áudio do botão](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> Se você mover a **mistura espacial** para 1 (3D) sem marcar a caixa de seleção **espacialize** , o Unity usará seu spatializer panorâmico, em vez do **Microsoft spatializer** com HRTFs.

## <a name="adjust-the-volume-curve"></a>Ajustar a curva de volume
Por padrão, o Unity atenua os sons espaciais à medida que eles ficam mais distantes do ouvinte. Quando essa atenuação é aplicada aos sons de comentários de interação, a interface pode ser mais difícil de usar.

Para desabilitar essa atenuação, ajuste a curva de **volume** . No componente **fonte de áudio** do painel **Inspetor** para o **PressableButtonHoloLens2**, há uma seção chamada configurações de **som 3D**. Nesta seção:
1. Definir a propriedade **rolloff do volume** como linear
2. Arraste o ponto de extremidade na curva de **volume** (a curva vermelha) de ' 0 ' no eixo y até ' 1 '
3. Para ajustar a forma da curva de **volume** para ser simples, arraste o controle forma de curva de branco para ser paralelo ao eixo X

Após essas alterações, a seção **configurações de som 3D** das propriedades da **fonte de áudio** do **PressableButtonHoloLens2** terá a seguinte aparência:

![Configurações de som 3D do botão](images/spatial-audio/button-3d-sound-settings.png)

## <a name="next-steps"></a>Próximas etapas

Experimente seu aplicativo em um HoloLens 2 ou no editor do Unity. No aplicativo, você pode tocar no botão e ouvir os sons de interação do botão espacial.

Ao testar no editor do Unity, pressione a barra de espaço e role com a roda de rolagem para ativar a simulação de mão. Para obter mais informações, consulte a [documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).

Continue no [capítulo 3](unity-spatial-audio-ch3.md) para adicionar um vídeo ao seu aplicativo e espaciale o áudio do vídeo.

