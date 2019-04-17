---
title: Câmera no Unity
description: Como usar o desenvolvimento de Main câmera para Windows Mixed Reality do Unity para fazer a renderização holográfica
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, renderização holográfica, ponto de foco holográfica e imersivo, buffers de profundidade, clip somente orientação, posicional, opaca, transparente,
ms.openlocfilehash: 8ea5a1f53351faab1b2863a0afac74e958b4b1a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589128"
---
# <a name="camera-in-unity"></a>Câmera no Unity

Quando você wear um headset de realidade misturada, torna o centro da sua holográfica do mundo. O Unity [câmera](http://docs.unity3d.com/Manual/class-Camera.html) componente manipula automaticamente a renderização estereoscópica e seguirá a movimentação do cabeçote e rotação quando seu projeto tiver "Virtual realidade com suporte" marcada com "Windows Mixed Reality" como o dispositivo (em seção outras configurações das configurações de Player do Windows Store). Isso pode ser listado como "Windows Holographic" em versões mais antigas do Unity.

No entanto, para otimizar a qualidade visual totalmente e [estabilidade holograma](hologram-stability.md), você deve definir as configurações de câmera descritas abaixo.

>[!NOTE]
>Essas configurações precisam ser aplicadas para a câmera no cada cena do seu aplicativo.
>
>Por padrão, quando você cria uma nova cena no Unity, ele conterá um GameObject de câmera principal na hierarquia que inclui o componente de câmera, mas não tem as configurações abaixo aplicadas corretamente.

## <a name="holographic-vs-immersive-headsets"></a>Holográfica versus fones imersivos em exposição

As configurações padrão no componente de câmera do Unity são para aplicativos tradicionais de 3D que precisam de um plano de fundo skybox semelhante que elas não tenham um mundo real.
* Durante a execução em um  **[fone de ouvido imersivo](immersive-headset-hardware-details.md)**, você está renderizando tudo o que o usuário vê e então, você provavelmente desejará manter o skybox.
* No entanto, durante a execução em um **fone de ouvido holográfica** como [HoloLens](hololens-hardware-details.md), o mundo real deve aparecer por trás de tudo, a câmera é renderizada. Para fazer isso, defina o plano de fundo da câmera para ser transparente (em HoloLens, preto renderizado como transparente), em vez de uma textura Skybox:
    1. Selecione a câmera principal no painel de hierarquia
    2. No painel Inspetor, localizar o componente de câmera e altere a lista suspensa de Limpar sinalizadores de Skybox para cor sólida
    3. Selecione o seletor de cor do plano de fundo e altere os valores RGBA (0, 0, 0, 0)

Você pode usar o código de script para determinar no tempo de execução se o fone de ouvido é imersivo ou holográfica verificando [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).


## <a name="positioning-the-camera"></a>Posicionamento da câmera

Será mais fácil para dispor o seu aplicativo se você imaginar a posição inicial do usuário como (x: 0, Y: 0, Z: 0). Uma vez que a câmera principal está acompanhando a movimentação do cabeçote do usuário, a posição inicial do usuário pode ser definida, definindo a posição inicial da câmera principal.
1. Selecione a câmera principal no painel de hierarquia
2. No painel Inspetor, localizar o componente de transformação e alterar a posição de (x: 0, Y: Z 1,: -10) para (x: 0, Y: 0, Z: 0)

   ![Câmera no painel de Inspetor no Unity](images/maincamera-350px.png)<br>
   *Câmera no painel de Inspetor no Unity*

## <a name="clip-planes"></a>Planos de recorte

Renderizando conteúdo muito perto do usuário pode ser incomodado na realidade mista. Você pode ajustar a [quase e recortar muito planos](hologram-stability.md#hologram-render-distances) no componente de câmera.
1. Selecione a câmera principal no painel de hierarquia
2. No painel Inspetor, localizar os planos de recorte de componente de câmera e altere a caixa de texto curto de 0,3 para.85. Conteúdo renderizado ainda mais próximo pode levar a discomfort de usuário e deve ser evitada pela [diretrizes de distância de renderizar](hologram-stability.md#hologram-render-distances).

## <a name="multiple-cameras"></a>Câmeras múltiplas

Quando há vários componentes da câmera na cena, Unity sabe qual câmera a ser usado para renderização estereoscópica e controle de cabeçalho, verificando quais GameObject tem a marca de MainCamera.

## <a name="recentering-a-seated-experience"></a>Recentering uma experiência sentada

Se você estiver criando um [escala encaixado experiência](coordinate-systems.md), é possível origem de mundo do Unity centralizar novamente na posição atual de principal do usuário chamando o **[XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** método.

## <a name="reprojection-modes"></a>Modos de reprojection

HoloLens e fones imersivos em exposição será reproject cada quadro renderiza o seu aplicativo para ajustar para qualquer misprediction da posição de cabeçalho real do usuário quando photons são emitidos.

Por padrão:

* **Fones imersivos em exposição** executará reprojection posicional, ajustando seu hologramas para misprediction na posição e orientação, se o aplicativo fornece um buffer de profundidade de um determinado quadro.  Se um buffer de profundidade não for fornecido, o sistema corrigirá apenas por causa das interdependências na orientação.
* **Fones de ouvido holográfica** como HoloLens executará reprojection posicional, se o aplicativo fornece o buffer de profundidade ou não.  Reprojection posicional é possível sem buffers de profundidade em HoloLens, como renderização geralmente é esparsa com um plano de fundo estável fornecido pelo mundo real.

Se você souber que você esteja criando um [experiência somente orientação](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) com o conteúdo rigidamente bloqueado no corpo (conteúdo de vídeo de 360 graus, por exemplo,), você pode definir explicitamente o modo de reprojection como orientação apenas, definindo [ HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) à [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).

## <a name="sharing-your-depth-buffers-with-windows"></a>Compartilhar seus buffers de profundidade com Windows

Buffer de profundidade do seu aplicativo para Windows de cada quadro dará seu aplicativo um dos dois aumentos na estabilidade holograma, com base no tipo de fone de ouvido de compartilhamento que você estiver renderizando para:
* **Fones imersivos em exposição** pode executar reprojection posicional quando é fornecido um buffer de profundidade, ajustando seu hologramas para misprediction na posição e orientação.
* **Fones de ouvido holográfica** como o HoloLens selecionará automaticamente um [concentre-se o ponto de](focus-point-in-unity.md) quando é fornecido um buffer de profundidade, otimizando a estabilidade holograma ao longo do plano que faz interseção com o máximo de conteúdo.

Para definir se o seu aplicativo do Unity fornecerá um buffer de profundidade para Windows:
1. Vá para **edite** > **configurações do projeto** > **Player** > **guia da plataforma Universal do Windows**  >  **XR configurações**.
2. Expanda o **SDK de realidade mista do Windows** item.
3. Marque ou desmarque a **ativar o compartilhamento de Buffer de profundidade** caixa de seleção.  Isso será verificado por padrão em novos projetos criados desde que esse recurso foi adicionado ao Unity e será desmarcado por padrão para projetos mais antigos que foram atualizados.

Fornecer um buffer de profundidade para Windows pode melhorar a qualidade visual, desde que o Windows podem mapear com precisão os valores de profundidade normalizada por pixel em seu buffer de profundidade para distâncias em metros, usando os planos de perto ou longe que você definiu no Unity na câmera principal.  Se sua renderização passa a profundidade da alça de valores de maneiras típicas, você geralmente deve ser bem aqui, embora translúcida renderização passa que gravam no buffer de profundidade ao mostradas existente pixels de cor podem confundir o reprojection.  Se você souber que seus passes de renderização deixará muitos dos seus pixels de final de profundidade com valores de profundidade imprecisas, você provavelmente obter a melhor qualidade visual compartilhando desmarcando"habilitar a profundidade de Buffer".

## <a name="mixed-reality-toolkits-automatic-scenesetup"></a>Instalação automática de cena misto realidade do Kit de ferramentas
Quando você importa [MRTK liberar pacotes do Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) ou clonar o projeto a partir o [repositório GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), você vai encontrar um novo menu 'Toolkit de realidade mista' no Unity. No menu 'Configurar', você verá o menu 'Aplicar misto realidade cena configurações'. Quando você clica nele, ele remove a câmera padrão e adiciona os componentes básicos - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), e [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![Menu MRTK para a instalação de cena](images/MRTK_Input_Menu.png)<br>
*Menu MRTK para a instalação de cena*

![Instalação automática de cena no MRTK](images/MRTK_HowTo_Input1.png)<br>
*Instalação automática de cena no MRTK*

## <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera pré-fabricado
Você também pode adicionar manualmente esses do painel de projeto. Você pode encontrar esses componentes como pré-fabricados. Quando você procura **MixedRealityCamera**, você poderá ver duas pré-fabricados de câmera diferente. A diferença é que **MixedRealityCamera** é a câmera apenas pré-fabricado enquanto que o **MixedRealityCameraParent** inclui componentes adicionais para os fones imersivos em exposição como Teleportation, movimento Controlador e, limite.

![Pré-fabricados de câmera em MRTK](images/MRTK_HowTo_Input2.png)<br>
*Pré-fabricados de câmera em MRTK*

**MixedRealtyCamera** dá suporte ao HoloLens e envolvente fone de ouvido. Ele detecta o tipo de dispositivo e otimiza as propriedades como sinalizadores claras e Skybox. Abaixo você encontrará algumas das propriedades úteis que você pode personalizar como o Cursor personalizado, modelos de controlador de movimento e Floor.

![Propriedades para o controlador de movimento, Cursor e Floor](images/MRTK_HowTo_Input3.png)<br>
*Propriedades para o controlador de movimento, Cursor e Floor*

## <a name="see-also"></a>Consulte também
* [Estabilidade holograma](hologram-stability.md)
* [MixedRealityToolkit Main Camera.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
