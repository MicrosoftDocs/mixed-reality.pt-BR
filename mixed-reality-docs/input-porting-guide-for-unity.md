---
title: Entrada de portabilidade de guia para Unity
description: Saiba como manipular a entrada para o Windows Mixed Reality no Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: entrada, unity, portabilidade
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590495"
---
# <a name="input-porting-guide-for-unity"></a>Entrada de portabilidade de guia para Unity

Você pode portar sua lógica de entrada para o Windows Mixed Reality usando uma das duas abordagens, APIs Input.GetButton/GetAxis geral do Unity que se estendem por várias plataformas ou o XR específicos do Windows. WSA. APIs de entrada que oferecem dados avançados especificamente para controladores de movimento e HoloLens mãos.

## <a name="general-inputgetbuttongetaxis-apis"></a>APIs de Input.GetButton/GetAxis geral

Atualmente, o Unity usa suas APIs Input.GetButton/Input.GetAxis geral para expor a entrada para [o SDK do Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) e [SDK OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html). Se seus aplicativos já estiver usando essas APIs para a entrada, este é o caminho mais fácil para dar suporte a controladores de movimento na realidade mista do Windows: você só precisa remapear botões e eixos no Gerenciador de entrada.

Para obter mais informações, consulte o [tabela de mapeamento de botão/eixo do Unity](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) e o [visão geral das APIs do Unity comuns](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR específicas do Windows. WSA. APIs de entrada

Se seu aplicativo já compilado lógica personalizada de entrada para cada plataforma, você pode optar por usar as APIs de entrada espaciais específicos do Windows sob a **UnityEngine.XR.WSA.Input** namespace. Isso lhe permite acessar informações adicionais, como precisão de posição ou o tipo de fonte, permitindo que você conte mãos e controladores separados em HoloLens.

Para obter mais informações, consulte o [visão geral das APIs UnityEngine.XR.WSA.Input](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Alça pose versus pose apontador

Realidade mista do Windows oferece suporte a controladores de movimento em uma variedade de fatores forma, com o design de cada controlador difere em sua relação entre a posição do usuário mão e natural "encaminhar" direção que aplicativos deve usar para apontando ao renderizar o controlador.

Para melhor representar esses controladores, há dois tipos de poses, que você pode investigar para cada fonte de interação:

* O **alça pose**, que representa o local de palma da mão detectada por um HoloLens ou palma mantendo um controlador de animação.
    * Em fones imersivos em exposição, essa pose é melhor usado para renderizar **mão do usuário** ou **um objeto é mantido em mãos do usuário**, como uma espada ou elétrons.
    * O **segure posição**: O centroide de palm pressionando o controlador naturalmente, ajustado esquerda ou direita para centralizar a posição dentro a alça.
    * O **Segure o eixo à direita da orientação**: Quando você abre completamente sua mão para formar uma dedo simples 5 pose, raio que é normal para o palm (para a frente da esquerda palm, com versões anteriores do palm à direita)
    * O **Segure o eixo de encaminhamento da orientação**: Quando você fecha sua mão parcialmente (como se que mantém o controlador), o raio que aponta "forward" por meio de tubo formado por seus dedos não thumb.
    * O **segure orientação backup eixo**: O eixo de cima indicado pelas definições de direito e Avançar.
    * Você pode acessar a alça pose por meio da API de entrada entre fornecedores do Unity, qualquer um dos (**[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) ou por meio da API do Windows específica (**sourceState.sourcePose.TryGetPosition/Rotation**, solicitando a pose alça).
* O **ponteiro pose**, que representa a dica do controlador que aponta para a frente.
    * Essa pose é melhor usado para raycast quando **apontando para a interface do usuário** quando você está renderizando o próprio modelo de controlador.
    * Atualmente, pose o ponteiro está disponível apenas através da API do Windows específica (**sourceState.sourcePose.TryGetPosition/Rotation**, solicitando a pose ponteiro).

Esses representam as coordenadas são expressas em coordenadas de mundo do Unity.

## <a name="see-also"></a>Consulte também
* [Controladores de movimento](motion-controllers.md)
* [Gestos e controladores de movimento no Unity](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Portabilidade de guias](porting-guides.md)
