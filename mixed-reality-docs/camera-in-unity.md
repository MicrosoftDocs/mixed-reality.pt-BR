---
title: Câmera no Unity
description: Como usar a câmera principal do Unity para o desenvolvimento de realidade mista do Windows para fazer a renderização Holographic
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Holographic renderização, Holographic, imersão, ponto de foco, buffer de profundidade, somente orientação, posicional, opaco, transparente, clipe
ms.openlocfilehash: 3a9846242dd1709bcaf927d8ffae33862e96ecc8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522384"
---
# <a name="camera-in-unity"></a>Câmera no Unity

Quando você gasta um headset de realidade misturada, ele se torna o centro do seu Holographic World. O componente da [câmera](http://docs.unity3d.com/Manual/class-Camera.html) do Unity manipulará automaticamente a renderização de estereoscópico e seguirá o movimento e a rotação da cabeça quando o seu projeto tiver "realidade virtual com suporte" selecionada com "realidade mista do Windows" como o dispositivo (em outras configurações da seção Configurações do Windows Store Player). Isso pode estar listado como "Windows Holographic" em versões mais antigas do Unity.

No entanto, para otimizar totalmente a qualidade visual e a [estabilidade do holograma](hologram-stability.md), você deve definir as configurações de câmera descritas abaixo.

>[!NOTE]
>Essas configurações precisam ser aplicadas à câmera em cada cena do seu aplicativo.
>
>Por padrão, quando você cria uma nova cena no Unity, ela conterá uma câmara de jogo principal na hierarquia que inclui o componente da câmera, mas não tem as configurações abaixo aplicadas corretamente.

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit-v2"></a>Configuração automática de cena e câmera com o Mixed Reality Toolkit v2. 

Siga o guia [passo a passo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) para adicionar o kit de ferramentas de realidade misturada v2 ao seu projeto do Unity e ele configurará seu projeto automaticamente.

Você também pode configurar manualmente o projeto sem MRTK com o guia na seção abaixo. 

## <a name="holographic-vs-immersive-headsets"></a>Headsets de Holographic vs. imersiva

As configurações padrão no componente câmera do Unity são para aplicativos 3D tradicionais que precisam de um plano de fundo Skybox, pois não têm um mundo real.
* Ao executar em um **[headset de imersão](immersive-headset-hardware-details.md)** , você está renderizando tudo o que o usuário vê e, portanto, provavelmente desejará manter o Skybox.
* No entanto, ao executar em um **Headset Holographic** como o [HoloLens](hololens-hardware-details.md), o mundo real deve aparecer atrás de tudo que a câmera renderiza. Para fazer isso, defina o plano de fundo da câmera como transparente (no HoloLens, o preto é renderizado como transparente) em vez de uma textura Skybox:
    1. Selecione a câmera principal no painel hierarquia
    2. No painel Inspetor, localize o componente câmera e altere a lista suspensa limpar sinalizadores de Skybox para cor sólida
    3. Selecione o seletor de cor do plano de fundo e altere os valores de RGBA para (0, 0, 0, 0)

Você pode usar o código de script para determinar em tempo de execução se o headset é imersiva ou Holographic verificando [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).


## <a name="positioning-the-camera"></a>Posicionando a câmera

Será mais fácil definir o layout do seu aplicativo se você imaginar a posição inicial do usuário como (X: 0, Y: 0, Z: 0). Como a câmera principal está acompanhando a movimentação do cabeçalho do usuário, a posição inicial do usuário pode ser definida definindo a posição inicial da câmera principal.
1. Selecione a câmera principal no painel hierarquia
2. No painel Inspetor, localize o componente transformação e altere a posição de (X: 0, Y: 1, Z:-10) a (X: 0, Y: 0, Z: 0

   ![Câmera no painel de Inspetor no Unity](images/maincamera-350px.png)<br>
   *Câmera no painel de Inspetor no Unity*

## <a name="clip-planes"></a>Planos de clipes

O processamento de conteúdo muito próximo ao usuário pode ser desconfortável em realidade misturada. Você pode ajustar os [planos de corte próximo e longe](hologram-stability.md#hologram-render-distances) no componente da câmera.
1. Selecione a câmera principal no painel hierarquia
2. No painel Inspetor, localize os planos de recorte do componente da câmera e altere a caixa de texto próximo de 0,3 para. 85. O conteúdo renderizado ainda mais próximo pode levar ao usuário discomfort e deve ser evitado de acordo com as [diretrizes de distância de renderização](hologram-stability.md#hologram-render-distances).

## <a name="multiple-cameras"></a>Várias câmeras

Quando há vários componentes de câmera na cena, o Unity sabe qual câmera usar para a renderização estereoscópico e o rastreamento de cabeçalho verificando qual gameobject tem a marca MainCamera.

## <a name="recentering-a-seated-experience"></a>Recentralizando uma experiência em estação

Se você estiver criando uma [experiência de escala](coordinate-systems.md)em posição, poderá recentralizar a origem mundial da unidade na posição de cabeçalho atual do usuário chamando o **[XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .

## <a name="reprojection-modes"></a>Modos de Reprojeção

Os headsets de HoloLens e de imersão reprojetarão cada quadro que seu aplicativo renderiza para se ajustar para qualquer previsão incorreta da posição de cabeçalho real do usuário quando fótons são emitidos.

Por padrão:

* Os headsets de **imersão** executarão a Reprojeção posicional, ajustando os hologramas para uma previsão incorreta na posição e na orientação, se o aplicativo fornecer um buffer de profundidade para um determinado quadro.  Se um buffer de profundidade não for fornecido, o sistema só corrigirá as informações incorretas na orientação.
* **Holographic headsets** como HoloLens executarão a Reprojeção posicional se o aplicativo fornece seu buffer de profundidade ou não.  A Reprojeção posicional é possível sem buffers de profundidade no HoloLens, pois a renderização costuma ser esparsa com um plano de fundo estável fornecido pelo mundo real.

Se você souber que está criando uma [experiência somente de orientação](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) com conteúdo com bloqueio de corpo rígido (por exemplo, conteúdo de vídeo de 360 graus), você pode definir explicitamente o modo de Reprojeção para ser somente orientação por meio da configuração [ HolographicSettings.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) reprojemode para [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).

## <a name="sharing-your-depth-buffers-with-windows"></a>Compartilhando buffers de profundidade com o Windows

Compartilhar o buffer de profundidade do seu aplicativo para o Windows cada quadro dará ao seu aplicativo um dos dois aumentos na estabilidade do holograma, com base no tipo de headset que você está renderizando:
* Os headsets de **imersão** podem executar a Reprojeção posicional quando um buffer de profundidade é fornecido, ajustando os hologramas para uma previsão incorreta na posição e na orientação.
* Os fones de **ouvido Holographic** como o HoloLens selecionarão automaticamente um [ponto de foco](focus-point-in-unity.md) quando um buffer de profundidade for fornecido, otimizando a estabilidade do holograma ao longo do plano que intercepta o maior conteúdo.

Para definir se seu aplicativo de Unity fornecerá um buffer de profundidade para o Windows:
1. Vá para **Editar** > **configurações** > do projeto Player plataforma universal do Windowsguia > configurações do XR. > 
2. Expanda o item **Windows Mixed Reality SDK** .
3. Marque ou desmarque a caixa de seleção **Habilitar compartilhamento de buffer de profundidade** .  Isso será verificado por padrão em novos projetos criados, pois esse recurso foi adicionado ao Unity e será desmarcado por padrão para projetos mais antigos que foram atualizados.

Fornecer um buffer de profundidade para o Windows pode melhorar a qualidade visual desde que o Windows possa mapear com precisão os valores de profundidade por pixel normalizados em seu buffer de profundidade de volta para distâncias em metros, usando os planos próximos e distantes que você definiu no Unity na câmera principal.  Se a renderização passar a lidar com valores de profundidade de maneiras típicas, geralmente você deve estar bom aqui, embora o processamento translúcida passe na gravação para o buffer de profundidade durante a exibição para pixels de cor existentes pode confundir a Reprojeção.  Se você souber que os seus passos de renderização deixarão muitos dos seus pixels de profundidade final com valores de profundidade imprecisos, você provavelmente obterá uma melhor qualidade visual desmarcando "Habilitar compartilhamento de buffer de profundidade".


## <a name="see-also"></a>Consulte também
* [Estabilidade do holograma](hologram-stability.md)
* [MixedRealityToolkit principal. pré-fabricado](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
