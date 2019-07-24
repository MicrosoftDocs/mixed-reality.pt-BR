---
title: Som espacial no Unity
description: Reprodução de som espacial proveniente de um ponto 3D específico dentro de sua cena do Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, som espacial, HRTF, tamanho da sala
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549078"
---
# <a name="spatial-sound-in-unity"></a>Som espacial no Unity

Este tópico descreve como usar o som espacial em seus projetos do Unity. Ele abrange os arquivos de plug-in necessários, bem como os componentes e as propriedades do Unity que habilitam o som espacial.

## <a name="enabling-spatial-sound-in-unity"></a>Habilitando o som espacial no Unity

O som espacial, no Unity, é habilitado usando um plug-in de áudio spatializer. Os arquivos de plug-in são agrupados diretamente no Unity, portanto, habilitar o som espacial é tão fácil quanto **editar > configurações de projeto > áudio** e alterar o **plug-in Spatializer** no Inspetor para o **MS HRTF Spatializer**. Como o Microsoft spatializer só dá suporte a 48000Hz no momento, você também deve definir a taxa de amostragem do sistema como 48000 para evitar uma falha de HRTF no caso raro de o dispositivo de saída do sistema não estar definido como 48000 já:

![Inspetor de Áudiomanager](images/audio-250px.png)<br>
*Inspetor de Áudiomanager*

Seu projeto do Unity agora está configurado para usar o som espacial.

>[!NOTE]
>Se você não estiver usando um PC com Windows 10 para desenvolvimento, não obterá um som espacial no editor nem no dispositivo (mesmo que você esteja usando o SDK do Windows 10).

## <a name="using-spatial-sound-in-unity"></a>Usando o som espacial no Unity

O som espacial é usado em seu projeto do Unity ajustando três configurações em seus componentes de fonte de áudio. As etapas a seguir configurarão os componentes de fonte de áudio para o som espacial.
* No painel **hierarquia** , selecione o objeto de jogo que tem uma **fonte de áudio**anexada.
* No painel **Inspetor** , sob o componente **fonte de áudio**
    * Verifique a  opção espacialize.
    * Defina a **mistura espacial** como **3D** (valor numérico 1).
    * Para obter melhores resultados, expanda **configurações de som 3D** e defina **rolloff de volume** como **rolloff personalizado**.

![Painel de Inspetor no Unity mostrando a fonte de áudio](images/audiosource.png)<br>
*Painel de Inspetor no Unity mostrando a fonte de áudio*

Seus sons agora existem de forma realista no ambiente do seu projeto!

É altamente recomendável que você se familiarize com as [diretrizes de design de som espacial](spatial-sound-design.md). Essas diretrizes ajudam a integrar seu áudio perfeitamente ao seu projeto e a aprofundarr seus usuários para a experiência que você criou.

## <a name="setting-spatial-sound-settings"></a>Definindo configurações de som espacial

O plug-in de som espacial da Microsoft fornece um parâmetro adicional que pode ser definido, em uma base de origem por áudio, para permitir o controle adicional da simulação de áudio. Esse parâmetro é o tamanho da sala simulada.

### <a name="room-size"></a>Tamanho da sala

O tamanho do espaço que está sendo simulado por som espacial. Os tamanhos aproximados das salas são; pequeno (um escritório para uma pequena sala de conferências), médio (uma sala de conferência grande) e grande (um auditórios). Você também pode especificar um tamanho de sala de nenhum para simular um ambiente externo. O tamanho de sala padrão é pequeno.

### <a name="example"></a>Exemplo

O MixedRealityToolkit para Unity fornece uma classe estática que torna fácil a definição das configurações de som espaciais. Essa classe pode ser encontrada na [pasta MixedRealityToolkit\SpatialSound](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) e pode ser chamada de qualquer script em seu projeto. É recomendável que você defina esses parâmetros em cada componente de fonte de áudio em seu projeto. O exemplo a seguir mostra a seleção do tamanho médio da sala de uma fonte de áudio anexada.

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Acessando diretamente parâmetros do Unity

Se você não quiser usar as excelentes ferramentas de áudio no MixedRealityToolkit, aqui está como você alteraria os parâmetros de HRTF. Você pode copiar/colar isso em um script chamado *SetHRTF.cs* que você deseja anexar a cada HRTF de áudio. Ele permite que você altere os parâmetros importantes para HRTF.

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>Som espacial no kit de ferramentas de realidade misturada
- [HoloToolkit-Examples/SpatialSound/cenas/UAudioManagerTest. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

Os exemplos a seguir do kit de ferramentas de realidade misturada são exemplos gerais de efeito de áudio que demonstram maneiras de tornar suas experiências mais envolventes usando som.
- [HoloToolkit-Examples/SpatialSound/cenas/AudioLoFiTest. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/cenas/AudioOcclusionTest. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>Consulte também
* [Som espacial](spatial-sound.md)
* [Projeto de som espacial](spatial-sound-design.md)
