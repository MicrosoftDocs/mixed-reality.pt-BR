---
title: Tutoriais de áudio espacial-5. Usando o reverberar para adicionar distância ao áudio espacial
description: Adicione um efeito de reverberação para melhorar o sentido de variação de distância para áudio espacial.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial
ms.openlocfilehash: abe78417dc231e6228d1942e03418ba699bc0938
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182733"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a>Usando o reverberar para adicionar distância ao áudio espacial

## <a name="objectives"></a>Objetivos
Nos capítulos anteriores, adicionamos a espacialização a sons para dar a eles uma ideia de direção. Neste quinto capítulo, vamos adicionar um efeito de reverberação para dar aos sons uma sensação de distância. Nossos objetivos são:
* Melhorar a distância percebida de fontes de som adicionando o reverberador
* Controle a distância percebida do som usando a distância do ouvinte para o holograma

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Adicionar um grupo de mixers e um efeito de reverberação
No [capítulo 2](unity-spatial-audio-ch2.md), adicionamos um mixer. O mixer inclui um **grupo** por padrão chamado **Master**. Como só desejamos aplicar um efeito de reverberação a alguns sons, vamos adicionar um segundo **grupo** para esses sons. Para adicionar um **grupo**, clique com o botão direito do mouse no grupo **mestre** no **mixer de áudio** e escolha **Adicionar grupo filho**:

![Adicionar grupo filho](images/spatial-audio/add-child-group.png)

Neste exemplo, nomeamos o novo grupo "efeito de sala".

Cada **grupo** tem seu próprio conjunto de efeitos. Adicione um efeito de reverberação ao novo grupo clicando em **Adicionar...** no novo grupo e escolhendo o **reverberar de SFX**:

![Adicionar reverbo SFX](images/spatial-audio/add-sfx-reverb.png)

Na terminologia de áudio, o áudio unreverberated original é chamado de _caminho seco_, e o áudio após a filtragem com o filtro de reverberação é chamado de _caminho úmida_. Ambos os caminhos são enviados para a saída de áudio, e seus pontos fortes relativos nessa mistura são chamados de _mistura úmida/seca_. A mistura úmida/seca afeta fortemente a sensação de distância.

O **inverbo SFX** inclui controles para ajustar a mistura úmida/seca dentro do efeito. Como o plug-in **Spatializer da Microsoft** trata o caminho seco, usaremos o único **verbo SFX** somente para o caminho úmida. No painel **Inspetor** de seu **reverbo SFX**:
* Definir a propriedade de nível seco para a configuração mais baixa (-10000 mB)
* Definir a propriedade Room como a configuração mais alta (0 mB)

Após essas alterações, o painel de **Inspetor** do **reverberador SFX** terá a seguinte aparência:

![Propriedades de reverberação SFX](images/spatial-audio/sfx-reverb-properties.png)

As outras configurações controlam a sensação da sala simulada. Em particular, o **tempo de decaimento** está relacionado ao tamanho de sala percebido. 

## <a name="enable-reverb-on-the-video-playback"></a>Habilitar reverberação na reprodução de vídeo
Há duas etapas para habilitar o reverberador em uma fonte de áudio:
* Rotear a **fonte de áudio** para o **grupo** apropriado
* Defina o plug-in **Microsoft Spatializer** para passar áudio para o **grupo** para processamento

Nas etapas a seguir, vamos ajustar nosso script para controlar o roteamento de áudio e anexar um script de controle fornecido com o plug-in do **Microsoft Spatializer** para alimentar dados no reverberador.

No painel **Inspetor** para o **Quad**, clique em **Adicionar componente** e adicione o script de **nível de envio de efeito Room** :

![Adicionar script de nível de envio](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> A menos que você habilite o recurso de **nível de envio de efeito Room** do plug-in do **Microsoft Spatializer** , ele não envia nenhum áudio de volta para o mecanismo de áudio do Unity para processamento de efeito.

O componente de **nível de envio de efeito Room** inclui um controle de gráfico que define o nível do áudio enviado ao mecanismo de áudio do Unity para o processamento de reverberação. Clique e arraste a curva para baixo para definir o nível como About-30dB:

![Ajustar curva de reverberação](images/spatial-audio/adjust-reverb-curve.png)

Em seguida, remova os comentários das 4 linhas comentadas no script **SpatializeOnOff** . O script agora terá esta aparência:
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

Remover os comentários dessas linhas adiciona duas propriedades ao painel de **Inspetor** para o script. Para defini-las, no painel **Inspetor** do componente **espacial on off** do **Quad**:
* Defina a propriedade **grupo de efeitos da sala** como o novo grupo do mixer de efeito Room
* Definir a propriedade do **grupo mestre** como o grupo do mixer mestre

Após essas alterações, as propriedades **espaciais off** ficarão assim:

![Espacial eslongada estendida](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a>Próximas etapas

Experimente seu aplicativo em um HoloLens 2 ou no editor do Unity. Agora, ao tocar o botão no aplicativo para ativar a espacialização, o script roteará o áudio do vídeo para o grupo de efeitos Room para adicionar o reverberador. Ao alternar para o estéreo, ele encaminhará o áudio para o grupo mestre e evitará adicionar o reverberador.

Você concluiu os tutoriais de áudio espacial 2 do HoloLens para o Unity. Parabéns!


