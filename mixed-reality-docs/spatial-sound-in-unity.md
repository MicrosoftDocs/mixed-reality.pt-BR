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
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="700ce-104">Som espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="700ce-104">Spatial Sound in Unity</span></span>

<span data-ttu-id="700ce-105">Esta página contém links para recursos para ajudá-lo a usar e projetar com o Microsoft HRTF spatializer em seus projetos de realidade misturada no Unity.</span><span class="sxs-lookup"><span data-stu-id="700ce-105">This page links to resources to help you use and design with the Microsoft HRTF spatializer in your Unity mixed reality projects.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="700ce-106">Habilitar a espacialização</span><span class="sxs-lookup"><span data-stu-id="700ce-106">Enable spatialization</span></span>

<span data-ttu-id="700ce-107">Habilite o **Spatializer MS HRTF** nas configurações de áudio do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="700ce-107">Enable the **MS HRTF Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="700ce-108">Para obter mais detalhes, consulte a [documentação do spatializer do Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span><span class="sxs-lookup"><span data-stu-id="700ce-108">For more details, see [Unity's spatializer documentation](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span></span> 

<span data-ttu-id="700ce-109">Anexe uma **fonte de áudio** a um objeto na hierarquia e habilite a espacial marcando a caixa de seleção **habilitar a espacial** e movendo o controle deslizante de **mistura espacial** para ' 1 '.</span><span class="sxs-lookup"><span data-stu-id="700ce-109">Attach an **Audio Source** to an object in the hierarchy, and enable spatialization by checking the **Enable spatialization** checkbox and moving the **Spatial Blend** slider to '1'.</span></span> <span data-ttu-id="700ce-110">Para obter mais detalhes, consulte a [documentação de fonte de áudio do Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span><span class="sxs-lookup"><span data-stu-id="700ce-110">For more details, see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span></span> 

## <a name="design-with-spatialization"></a><span data-ttu-id="700ce-111">Design com espacialização</span><span class="sxs-lookup"><span data-stu-id="700ce-111">Design with spatialization</span></span>

### <a name="distance-based-attenuation"></a><span data-ttu-id="700ce-112">Atenuação baseada em distância</span><span class="sxs-lookup"><span data-stu-id="700ce-112">Distance-based attenuation</span></span>
<span data-ttu-id="700ce-113">O decaimento baseado em distância padrão da Unity tem uma distância mínima de 1 medidor e uma distância máxima de 500 metros, com um rolloff logarítmica.</span><span class="sxs-lookup"><span data-stu-id="700ce-113">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="700ce-114">Isso pode funcionar para seu cenário, ou você pode encontrar fontes que são atenuadas muito rapidamente ou muito lentamente.</span><span class="sxs-lookup"><span data-stu-id="700ce-114">This may work for your scenario, or you may find sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="700ce-115">Consulte [design de som em realidade misturada](spatial-sound-design.md) para obter as configurações recomendadas para as curvas de decaimento de distância e consulte a [documentação de fonte de áudio do Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) para obter informações sobre como definir essas curvas no Unity.</span><span class="sxs-lookup"><span data-stu-id="700ce-115">See [sound design in mixed reality](spatial-sound-design.md) for recommended settings for distance decay curves, and see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for information on setting these curves in Unity.</span></span>

### <a name="environment"></a><span data-ttu-id="700ce-116">Ambiente</span><span class="sxs-lookup"><span data-stu-id="700ce-116">Environment</span></span>
<span data-ttu-id="700ce-117">O **Spatializer MS HRTF** inclui um componente de reverberação de sala com [quatro configurações de reverberação](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) e um padrão de ' pequeno '.</span><span class="sxs-lookup"><span data-stu-id="700ce-117">The **MS HRTF Spatializer** includes a room reverb component with [four reverb settings](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) and a default of 'small'.</span></span> <span data-ttu-id="700ce-118">A configuração de sala pode ser alterada programaticamente para cada fonte de áudio C# anexando o seguinte script a cada objeto no Unity que tem uma fonte de áudio espacial:</span><span class="sxs-lookup"><span data-stu-id="700ce-118">The room setting can be changed programmatically for each audio source by attaching the following C# script to each object in Unity that has a spatialized Audio Source:</span></span>

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

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="700ce-119">Exemplos de som espacial do Unity</span><span class="sxs-lookup"><span data-stu-id="700ce-119">Unity spatial sound examples</span></span>
<span data-ttu-id="700ce-120">O MRTK (Mixed Reality Toolkit) inclui exemplos de maneiras de aplicar efeitos de áudio em realidade misturada: [demonstrações do MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span><span class="sxs-lookup"><span data-stu-id="700ce-120">The Mixed Reality Toolkit (MRTK) includes examples of ways to apply audio effects in mixed reality: [MRTK demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span></span>

