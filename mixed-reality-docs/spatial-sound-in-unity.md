---
title: Som espacial no Unity
description: Reprodução de som espacial que vem de um ponto 3D específico dentro de sua cena do Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, som espacial, HRTF, tamanho do espaço
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589075"
---
# <a name="spatial-sound-in-unity"></a>Som espacial no Unity

Este tópico descreve como usar o som espacial em seus projetos do Unity. Ele aborda os arquivos de plug-in necessárias, bem como os componentes de Unity e propriedades que permitem que o som de espacial.

## <a name="enabling-spatial-sound-in-unity"></a>Habilitando o som espacial no Unity

Som espacial, no Unity, é habilitado usando um plug-in spatializer áudio. Os arquivos de plug-in são empacotados diretamente para o Unity para habilitar o som espacial é tão fácil quanto vai **Editar > configurações do projeto > áudio** e alterando o **plug-in de Spatializer** no Inspetor de para o  **MS HRTF Spatializer**. Como o spatializer Microsoft só dá suporte a 48000Hz no momento, você também deve definir sua taxa de amostragem do sistema para 48000 para evitar uma falha HRTF no caso raro em que o dispositivo de saída do sistema não está definido para 48000 já:

![Inspetor de AudioManager](images/audio-250px.png)<br>
*Inspetor de AudioManager*

Seu projeto do Unity agora está configurado para usar som espacial.

>[!NOTE]
>Se você não estiver usando um computador Windows 10 para desenvolvimento, você não obterá espacial som no editor nem no dispositivo (mesmo se você estiver usando o SDK do Windows 10).

## <a name="using-spatial-sound-in-unity"></a>Usando o som espacial no Unity

Som espacial é usado em seu projeto do Unity, ajustando as três configurações em seus componentes de fonte de áudio. As etapas a seguir configurará os componentes de fonte de áudio para som espacial.
* No **hierarquia** do painel, selecione o objeto do jogo que tenha um anexado **Audio Source**.
* No **Inspector** do painel, nas **Audio Source** componente
    * Verifique as **Spatialize** opção.
    * Definir **Blend espacial** à **3D** (valor numérico 1).
    * Para obter melhores resultados, expanda **configurações de som 3D** e defina **Volume Rolloff** para **personalizado Rolloff**.

![Painel de Inspetor no Unity mostrando a fonte de áudio](images/audiosource.png)<br>
*Painel de Inspetor no Unity mostrando a fonte de áudio*

Os sons agora na verdade, existem dentro do ambiente do seu projeto!

É altamente recomendável que você se familiarize com o [diretrizes de design de som espacial](spatial-sound-design.md). Essas diretrizes ajudam a integrar o seu áudio perfeitamente em seu projeto e para ainda mais que os usuários com a experiência que você criou.

## <a name="setting-spatial-sound-settings"></a>Definindo configurações de som espaciais

O plug-in Microsoft Spatial Sound fornece um parâmetro adicional que pode ser definido, em um acordo com a fonte de áudio, para permitir que o controle adicional da simulação áudio. Esse parâmetro é o tamanho da sala simulado.

### <a name="room-size"></a>Tamanho do espaço

O tamanho da sala que está sendo simulada pelo som espacial. Os tamanhos aproximados das salas são; pequena (um escritório em uma sala de conferência pequeno), média (uma sala de conferência grande) e grande (um auditório). Você também pode especificar um tamanho de sala de none para simular um ambiente ao ar livre. O tamanho de espaço padrão é pequeno.

### <a name="example"></a>Exemplo

O MixedRealityToolkit para Unity fornece uma classe estática que faz a definir as configurações de som espacial fácil. Essa classe pode ser encontrada na [MixedRealityToolkit\SpatialSound pasta](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) e podem ser chamados de qualquer script em seu projeto. É recomendável que você defina esses parâmetros em cada componente de fonte de áudio em seu projeto. O exemplo a seguir mostra como selecionar o tamanho médio de espaço para uma fonte de áudio anexado.

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Acessar diretamente os parâmetros do Unity

Se você não quiser usar as ferramentas de áudio excelente no MixedRealityToolkit, aqui está como você alteraria HRTF parâmetros. Você pode copiar/colar isso em um script chamado *SetHRTF.cs* que você deseja anexar a cada AudioSource HRTF. Ele permite alterar os parâmetros importantes para HRTF.

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>Som espacial no Kit de ferramentas de realidade misturada
- [HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

Os exemplos a seguir do Kit de ferramentas de realidade misturada são exemplos de efeito de áudio geral que demonstram formas de tornar suas experiências mais envolventes usando o som.
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>Consulte também
* [Som espacial](spatial-sound.md)
* [Design de som espacial](spatial-sound-design.md)
