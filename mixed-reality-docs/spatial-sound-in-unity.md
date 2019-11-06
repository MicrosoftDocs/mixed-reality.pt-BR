---
title: Som espacial no Unity
description: Reprodução de som espacial proveniente de um ponto 3D específico dentro de sua cena do Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, som espacial, HRTF, tamanho da sala
ms.openlocfilehash: c96717d9df9b89fbb09f0b4466ee3a9bf5c8a149
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641072"
---
# <a name="spatial-sound-in-unity"></a>Som espacial no Unity

Esta página contém links para recursos para ajudá-lo a usar e projetar com o Microsoft HRTF spatializer em seus projetos de realidade misturada no Unity.

## <a name="enable-spatialization"></a>Habilitar a espacialização

Habilite o **Spatializer MS HRTF** nas configurações de áudio do seu projeto. Para obter mais detalhes, consulte a [documentação do spatializer do Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html). 

Anexe uma **fonte de áudio** a um objeto na hierarquia e habilite a espacial marcando a caixa de seleção **habilitar a espacial** e movendo o controle deslizante de **mistura espacial** para ' 1 '. Para obter mais detalhes, consulte a [documentação de fonte de áudio do Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html). 

## <a name="design-with-spatialization"></a>Design com espacialização

### <a name="distance-based-attenuation"></a>Atenuação baseada em distância
O decaimento baseado em distância padrão da Unity tem uma distância mínima de 1 medidor e uma distância máxima de 500 metros, com um rolloff logarítmica. Isso pode funcionar para seu cenário, ou você pode encontrar fontes que são atenuadas muito rapidamente ou muito lentamente. Consulte [design de som em realidade misturada](spatial-sound-design.md) para obter as configurações recomendadas para as curvas de decaimento de distância e consulte a [documentação de fonte de áudio do Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) para obter informações sobre como definir essas curvas no Unity.

### <a name="environment"></a>Ambiente
O **Spatializer MS HRTF** inclui um componente de reverberação de sala com [quatro configurações de reverberação](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) e um padrão de ' pequeno '. A configuração de sala pode ser alterada programaticamente para cada fonte de áudio C# anexando o seguinte script a cada objeto no Unity que tem uma fonte de áudio espacial:

```cs
using UnityEngine;
   using System.Collections;
   public class SetHRTF : MonoBehaviour    {
       public enum ROOMSIZE { Small, Medium, Large, None };
       public ROOMSIZE room = ROOMSIZE.Small;  // Small is regarded as the "most average"
       // defaults and docs from MSDN
       // https://msdn.microsoft.com/library/windows/desktop/mt186602(v=vs.85).aspx
       AudioSource audiosource;
       void Awake()
       {
           audiosource = this.gameObject.GetComponent<AudioSource>();
           if (audiosource == null)
           {
               print("SetHRTFParams needs an audio source to do anything.");
               return;
           }
           audiosource.spatialize = 1; // we DO want spatialized audio
           audiosource.spread = 0; // we dont want to reduce our angle of hearing
           audiosource.spatialBlend = 1;   // we do want to hear spatialized audio
           audiosource.SetSpatializerFloat(1, (float)room);    // 1 is the roomsize param
       }
   }
```

## <a name="unity-spatial-sound-examples"></a>Exemplos de som espacial do Unity
O MRTK (Mixed Reality Toolkit) inclui exemplos de maneiras de aplicar efeitos de áudio em realidade misturada: [demonstrações do MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).

