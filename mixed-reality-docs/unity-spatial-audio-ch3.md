---
title: Tutoriais de áudio espacial-3. Disespacial de áudio de um vídeo
description: Importar um ativo de vídeo para seu projeto do Unity e espacialar o áudio do vídeo.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial
ms.openlocfilehash: 1e5c84fd7d14cc5edc78839bbdf91590cc7fd8e7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182743"
---
# <a name="spatializing-audio-from-a-video"></a>Disespacial de áudio de um vídeo
Neste terceiro capítulo do módulo de áudio espacial dos tutoriais do HoloLens 2 Unity, você irá:
* Importar um vídeo e adicionar um player de vídeo
* Reproduza o vídeo em um Quadrangle
* Rotear áudio do vídeo para o Quadrangle e espacialar o áudio

## <a name="import-a-video-and-add-a-video-player"></a>Importar um vídeo e adicionar um player de vídeo

Arraste um arquivo de vídeo para o painel **projeto** em seu projeto do Unity. Você pode usar [este vídeo](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) do projeto de exemplo de áudio espacial.

![Pasta de ativos com vídeo](images/spatial-audio/assets-folder-with-video.png)

Ajustar as configurações de qualidade no clipe de vídeo pode garantir uma reprodução suave no HoloLens 2. Clique no arquivo de vídeo no painel **projeto** . Em seguida, no painel **Inspetor** do arquivo de vídeo, substitua as configurações para aplicativos da Windows Store e:
* Habilitar **transcodificação**
* Definir o **codec** como H264
* Definir o **modo de taxa de bits** como baixo
* Definir **qualidade espacial** para qualidade espacial média

Após esses ajustes, o painel de **Inspetor** do arquivo de vídeo terá a seguinte aparência:

![Painel de propriedades de vídeo](images/spatial-audio/video-property-pane.png)

Em seguida, adicione um objeto **player de vídeo** à **hierarquia** clicando com o botão direito do mouse no painel **hierarquia** e escolhendo **vídeo-> player de vídeo**:

![Player de vídeo na hierarquia](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a>Reproduzir vídeo em um Quadrangle
O objeto **player de vídeo** precisa de um objeto de jogo texturizado no qual renderizar o vídeo. Primeiro, adicione um **Quad** à sua **hierarquia** clicando com o botão direito do mouse no painel **hierarquia** e escolhendo **objeto 3D-> Quad**:

![Adicionar quádruplo à hierarquia](images/spatial-audio/add-quad-to-hierarchy.png)

Para garantir que o **Quad** apareça na frente do usuário quando o aplicativo é iniciado, defina a propriedade **Position** de **Quad** para (0, 0, 2) e a propriedade **Scale** como (1,28, 0,72, 1). Após essas alterações, o componente **transformação** no painel **Inspetor** para o **Quad** terá a seguinte aparência:

![Transformação quádrupla](images/spatial-audio/quad-transform.png)

Para Texturizar o **Quad** com vídeo, crie uma nova **textura de renderização**. No painel **projeto** , clique com o botão direito do mouse e escolha **criar-> renderizar textura**:

![Criar textura de renderização](images/spatial-audio/create-render-texture.png)

No painel **Inspetor** da **textura renderizar**, defina a propriedade **tamanho** para corresponder à resolução nativa do vídeo de 1280x720. Em seguida, para garantir um bom desempenho de renderização no HoloLens 2, defina a propriedade **buffer de profundidade** com **pelo menos 16 bits de profundidade**. Após essas configurações, o painel de **Inspetor** para a **textura de renderização** terá a seguinte aparência:

![Renderizar Propriedades de textura](images/spatial-audio/render-texture-properties.png)

Em seguida, use sua nova **textura de renderização** como a textura para o **Quad**:
1. Arraste a **textura renderizar** do painel **projeto** para o **Quad** na **hierarquia**
2. Para garantir um bom desempenho no HoloLens 2, no painel do **Inspetor** para o **Quad**, selecione o **sombreador standard do kit de ferramentas da realidade misturada**.

Com essas configurações, o componente de **textura** no painel de **Inspetor** para o **Quad** terá a seguinte aparência:

![Propriedades de textura quádrupla](images/spatial-audio/quad-texture-properties.png)

Para definir o novo **player de vídeo** e **renderizar a textura** para reproduzir o clipe de vídeo, abra o painel do **Inspetor** para o **player de vídeo** e:
* Defina a propriedade **videoclipe** como seu arquivo de vídeo
* Marque a caixa de seleção **loop**
* Definir a **textura de destino** para sua nova textura de renderização

O painel **Inspetor** do **player de vídeo** terá a seguinte aparência:

![Propriedades do player de vídeo](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a>Esespacialr o áudio do vídeo
No painel de **Inspetor** para o **Quad**, crie uma **fonte de áudio** para a qual você encaminhará o áudio do vídeo:
* Clique em **Adicionar componente** na parte inferior do painel
* Adicionar uma **fonte de áudio**

Em seguida, na **fonte de áudio**:
* Definir **saída** para o mixer
* Marque a caixa **espacialize**
* Mover o controle deslizante de **mistura espacial** para 1 (3D)

Após essas alterações, o componente **fonte de áudio** no painel **Inspetor** para o **Quad** terá a seguinte aparência:

![Inspetor de fonte de áudio quádruplo](images/spatial-audio/quad-audio-source-inspector.png)

Para definir o **player de vídeo** para rotear seu áudio para a **fonte de áudio** no **Quad**, abra o painel do **Inspetor** para o **player de vídeo** e:
* Definir o **modo de saída de áudio** como ' fonte de áudio '
* Definir a propriedade **fonte de áudio** para o quad

Após essas alterações, o painel de **Inspetor** do **player de vídeo** terá a seguinte aparência:

![Fonte de áudio definida do player de vídeo](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a>Próximas etapas
Experimente seu aplicativo em um HoloLens 2 ou no editor do Unity. Você verá e ouvirá o vídeo e o áudio do vídeo será espacial.

Continue no [capítulo 4](unity-spatial-audio-ch4.md) para usar o botão para habilitar e desabilitar a espacial em tempo de execução.

