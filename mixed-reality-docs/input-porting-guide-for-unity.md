---
title: Guia de porta de entrada para Unity
description: Saiba como lidar com a entrada para a realidade mista do Windows no Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: entrada, Unity, portabilidade
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515488"
---
# <a name="input-porting-guide-for-unity"></a>Guia de porta de entrada para Unity

Você pode portar sua lógica de entrada para a realidade mista do Windows usando uma das duas abordagens, as APIs de entrada geral do Unity e do getbutton/getaxis que se estendem por várias plataformas ou pelo XR específico do Windows. WSA. APIs de entrada que oferecem dados mais ricos especificamente para controladores de movimento e mãos de HoloLens.

## <a name="general-inputgetbuttongetaxis-apis"></a>Informações gerais de entrada. getbutton/getaxis

No momento, o Unity usa suas APIs Input. getbutton/Input. getaxis gerais para expor a entrada para [o SDK do Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) e [o SDK do OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html). Se seus aplicativos já estiverem usando essas APIs para entrada, este é o caminho mais fácil para dar suporte a controladores de movimento no Windows Mixed Reality: você deve apenas precisar remapear botões e eixos no Gerenciador de entrada.

Para obter mais informações, consulte a [tabela de mapeamento de botões/eixo do Unity](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) e a [visão geral das APIs comuns do Unity](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR específico do Windows. WSA. APIs de entrada

Se seu aplicativo já criar uma lógica de entrada personalizada para cada plataforma, você poderá optar por usar as APIs de entrada espaciais específicas do Windows no namespace **UnityEngine. XR. WSA. Input** . Isso permite que você acesse informações adicionais, como precisão de posição ou tipo de fonte, permitindo que você informe as mãos e os controladores no HoloLens.

Para obter mais informações, consulte a [visão geral das APIs UnityEngine. XR. WSA. Input](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Segurar pose vs. ponto de apontar

O Windows Mixed Reality dá suporte a controladores de movimento em uma variedade de fatores forma, sendo que o design de cada controlador difere em sua relação entre a posição da mão do usuário e a direção natural "encaminhar" que os aplicativos devem usar para apontar ao renderizar o controle.

Para representar melhor esses controladores, há dois tipos de poses que você pode investigar para cada fonte de interação:

* A **alça de fixação**, que representa o local da palma de uma mão detectada por um HoloLens ou o Palm que possui um controlador de movimento.
    * Em headsets de imersão, essa pose é melhor usada para renderizar **a mão do usuário** ou **um objeto mantido na mão do usuário**, como uma gumes ou uma arma.
    * A **posição da alça**: O Palm centróide ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralizar a posição dentro da alça.
    * O **eixo direito da orientação de alça**: Quando você abre completamente a mão para formar uma pose plana de 5 dedos, o raio normal para o Palm (para frente do Palm esquerdo, para trás do Palm direito)
    * O **eixo de avanço da orientação de alça**: Quando você fecha a sua mão parcialmente (como se você mantiver o controlador), o raio que aponta para "encaminhar" por meio do tubo formado por seus dedos não-thumbs.
    * O **eixo superior da orientação de alça**: O eixo superior implícito pelas definições direita e avançar.
    * Você pode acessar a alça de pose por meio da API de entrada entre fornecedores do Unity ( **[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) ou por meio da API específica do Windows (**SourceState. SourcePose. TryGetPosition/Rotation**, solicitando a pose de alça).
* A **pose do ponteiro**, representando a ponta do controlador apontando para frente.
    * Essa pose é mais bem usada para Raycast ao apontar para a **interface do usuário** quando você está renderizando o próprio modelo do controlador.
    * Atualmente, a pose do ponteiro está disponível somente por meio da API específica do Windows (**SourceState. sourcePose. TryGetPosition/Rotation**, solicitando a pose do ponteiro).

Essas coordenadas de pose são todas expressas nas coordenadas do mundo do Unity.

## <a name="see-also"></a>Consulte também
* [Controladores de movimentos](motion-controllers.md)
* [Gestos e controladores de movimento no Unity](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guias de portabilidade](porting-guides.md)
