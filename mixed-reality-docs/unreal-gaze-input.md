---
title: Entrada olhar em não real
description: Explica como usar a entrada olhar em um modo inreal
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, HoloLens, acompanhamento de olho
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835615"
---
# <a name="gaze-input"></a>Entrada olhar

O plug-in de realidade mista do Windows não fornece nenhuma função especial para a entrada olhar. Tudo funciona embora a API não real padrão.

[API do Head olhar](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a>Acompanhamento ocular

Para usar a API de acompanhamento ocular, os desenvolvedores devem habilitar a funcionalidade de "entrada olhar" em suas configurações de projeto do HoloLens. Quando o aplicativo for iniciado, o usuário verá o seguinte prompt de consentimento

![Permissões de entrada de olho](images/unreal/eye-input-permissions.png)
 
Se o usuário der sua permissão, o aplicativo receberá uma entrada olhar. 

A API de acompanhamento de olho inreal está documentada [aqui](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)

Os detalhes técnicos de acompanhamento de olho estão [aqui](eye-tracking.md)

Observe que, especificamente para o controle de olhos inreal, o HoloLens tem um único olhar Ray para ambos os olhos. O HoloLens não fornece controle ocular estereoscópico.
