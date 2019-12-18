---
title: Tutoriais de áudio espacial-4. Habilitando e desabilitando o áudio espacial em tempo de execução
description: Use um botão para habilitar e desabilitar a espacialização de áudio em tempo de execução.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial
ms.openlocfilehash: 3fc9b56dc58d4c19f229d92f4562f04cbca0e7a6
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182863"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a>Habilitando e desabilitando a espacial em tempo de execução

## <a name="objectives"></a>Objetivos
Neste 4º Capítulo, você vai:
* Adicionar um novo script para controlar a espacialização em um objeto de jogo
* Direcionar o script de controle de espacial de ações de botão

## <a name="add-spatialization-control-script"></a>Adicionar script de controle de espacial
Clique com o botão direito do mouse no painel **projeto** e C# crie um novo script escolhendo **criar C# -> script**. Nomeie o seu script como "SpatializeOnOff".

![Criar script](images/spatial-audio/create-script.png)

Clique duas vezes no script no painel de **projeto** para abri-lo no Visual Studio. Substitua o conteúdo do script padrão pelo seguinte:

> [!NOTE]
> Várias linhas do script são comentadas. Essas linhas não serão comentadas no [capítulo 5](unity-spatial-audio-ch5.md).

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> Para habilitar ou desabilitar a espacialização, o script ajusta apenas a propriedade **spatialBlend** , deixando a propriedade de **espacial** habilitada. Nesse modo, o Unity ainda aplica a curva de **volume** . Caso contrário, se o usuário tivesse de desabilitar a espacial quando estiver longe da origem, ele ouviria o volume aumentar abruptamente. <br> <br>
> Se você preferir desabilitar totalmente a espacialização, modifique o script para ajustar também a **Propriedade booliana** booleana da variável **SourceObject** .

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Anexe o script e o conduza do botão
No painel **Inspetor** do **Quad**, clique em **Adicionar componente** e adicione o script **Spatial-off** :

![Adicionar script ao Quad](images/spatial-audio/add-script-to-quad.png)

No componente **espacial em diante** do **Quad**:
1. Localizar o subobjeto **PressableButtonHoloLens2-> IconAndText-> TextMeshPro** na **hierarquia**
2. Arraste o **TextMeshPro** suboject para o campo **ButtonTextObject** do componente **espacial on off**

Após essas alterações, o componente **espacial ativado** do **Quad** terá a seguinte aparência:

![Espacial desabilitada básica](images/spatial-audio/spatialize-on-off-basic.png)

Para definir o botão para chamar o script **Spatial on off** quando o botão for liberado, abra o painel **Inspetor** do objeto **PressableButtonHoloLens2** , localize o componente **interagindo** e:
1. Localizar a região **OnClick ()** da subseção de **eventos**
2. Arraste o **Quad** da **hierarquia** para o slot do objeto de destino.
3. Selecione **SpatializeOnOff. SwapSpatialization** na caixa suspensa ação.

Após essas alterações, o componente **interagindo** terá a seguinte aparência:

![Configurações de ação do botão](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a>Próximas etapas
Experimente seu aplicativo em um HoloLens 2 ou no editor do Unity. No aplicativo, agora você pode tocar no botão para ativar e desativar a espacial no vídeo. Ao testar no editor do Unity, pressione a barra de espaço e role com a roda de rolagem para ativar a simulação de mão. 

Continue no [capítulo 5](unity-spatial-audio-ch5.md) para adicionar uma distância percebida às fontes de som usando o reverberar.

