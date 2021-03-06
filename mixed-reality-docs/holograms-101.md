---
title: Sr noções básicas 101 – projeto completo com o dispositivo
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender as noções básicas sobre a realidade mista do Windows.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realidade misturada, realidade do Windows Mixed, HoloLens, holograma, Academia, tutorial
ms.openlocfilehash: 456aeea88b0d7f51acb52156d8139ec2df06883a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434713"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

<br>

# <a name="mr-basics-101-complete-project-with-device"></a>Sr Basics 101: concluir o projeto com o dispositivo

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

Este tutorial o guiará por um projeto completo, criado no Unity, que demonstra os principais recursos do Windows Mixed Reality no HoloLens, incluindo [olhar](gaze-and-commit.md), [gestos](gaze-and-commit.md#composite-gestures), [entrada de voz](voice-input.md), [som espacial](spatial-sound.md) e [mapeamento espacial](spatial-mapping.md) .

O tutorial levará aproximadamente 1 hora para ser concluído.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Sr Basics 101: concluir o projeto com o dispositivo</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md).
* Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) exigidos pelo projeto. Requer o Unity 2017,2 ou posterior.
  * Se você ainda precisar de suporte do Unity 5,6, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Se você ainda precisar de suporte do Unity 5,5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Se você ainda precisar de suporte do Unity 5,4, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar. Mantenha o nome da pasta como **origami**.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Capítulo 1 – mundo "holo"

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

Neste capítulo, vamos configurar nosso primeiro projeto do Unity e percorrer o processo de compilação e implantação.

### <a name="objectives"></a>Objetivos

* Configure o Unity para o desenvolvimento de Holographic.
* Crie um holograma.
* Veja um holograma que você fez.

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **abrir**.
* Insira o local como a pasta de **origami** que você cancelou anteriormente.
* Selecione **origami** e clique em **Selecionar pasta**.
* Como o projeto de **origami** não contém uma cena, salve a cena padrão vazia em um novo arquivo usando: **arquivo** / **salvar cena como**.
* Nomeie o novo **origami** de cena e pressione o botão **salvar** .

#### <a name="setup-the-main-virtual-camera"></a>Configurar a câmera virtual principal

* No **painel hierarquia**, selecione **câmera principal**.
* No **Inspetor** , defina sua posição de transformação como **0, 0, 0**.
* Localize a propriedade **limpar sinalizadores** e altere a lista suspensa de **Skybox** para **cor sólida**.
* Clique no campo **plano de fundo** para abrir um seletor de cores.
* Defina **R, G, B e** a como **0**.

#### <a name="setup-the-scene"></a>Configurar a cena

* No **painel hierarquia**, clique em **criar** e em **criar vazio**.
* Clique com o botão direito do mouse no novo **gameobject** e selecione Renomear. Renomeie o gameobject para **origamicollection**.
* Na pasta **hologramas** do painel projeto (expanda ativos e selecione hologramas ou clique duas vezes na pasta hologramas no painel projeto):
  * Arraste o **estágio** para a hierarquia para ser um filho de **origamicollection**.
  * Arraste **Sphere1** para a hierarquia para ser um filho de **origamicollection**.
  * Arraste **Sphere2** para a hierarquia para ser um filho de **origamicollection**.
* Clique com o botão direito do mouse no objeto de **luz direcional** no **painel hierarquia** e selecione **excluir**.
* Na pasta **hologramas** , arraste as **luzes** para a raiz do **painel hierarquia**.
* Na **hierarquia**, selecione o **origamicollection**.
* No **Inspetor**, defina a posição de transformação como **0,-0,5, 2,0**.
* Pressione o botão **reproduzir** no Unity para visualizar os hologramas.
* Você deve ver os objetos de origami na janela de visualização.
* Pressione **executar** uma segunda vez para parar o modo de visualização.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Exportar o projeto do Unity para o Visual Studio

* Em Unity, selecione **arquivo > configurações de Build**.
* Selecione **plataforma universal do Windows** na lista **plataforma** e clique em **alternar plataforma**.
* Defina o **SDK** como **Universal 10** e o **tipo de compilação** como **D3D**.
* Verifique **os C# projetos do Unity**.
* Clique em **Adicionar abrir cenas** para adicionar a cena.
* Clique em **Compilar**.
* Na janela Explorador de arquivos que aparece, crie uma **nova pasta** chamada "aplicativo".
* Clique uma vez na **pasta do aplicativo**.
* Pressione **Selecionar pasta**.
* Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.
* Abra a pasta do **aplicativo** .
* Abra (clique duas vezes) **origami. sln**.
* Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.
* Clique na seta ao lado do botão dispositivo e selecione **computador remoto** para implantar por Wi-Fi.
  * Defina o **endereço** para o nome ou endereço IP do seu HoloLens. Se você não souber o endereço IP do dispositivo, procure **configurações > rede & Internet > opções avançadas** ou pergunte ao Cortana **"Ei Cortana, qual é meu endereço IP?"**
  * Se o HoloLens estiver conectado via USB, você poderá selecionar o **dispositivo** a ser implantado sobre USB.
  * Deixe o **modo de autenticação** definido como **Universal**.
  * Clique em **selecionar**

* Clique em **depurar > iniciar sem Depurar** ou pressione **Ctrl + F5**. Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com o Visual Studio](using-visual-studio.md#pairing-your-device).

* O projeto de origami agora será compilado, implantado em seu HoloLens e, em seguida, executado.
* Coloque em seu HoloLens e procure ver os novos hologramas.

## <a name="chapter-2---gaze"></a>Capítulo 2 – olhar

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

Neste capítulo, vamos apresentar a primeira das três maneiras de interagir com seus hologramas-- [olhar](gaze-and-commit.md).

### <a name="objectives"></a>Objetivos

* Visualize seu olhar usando um cursor com bloqueio mundial.

### <a name="instructions"></a>Instruções

* Volte ao seu projeto do Unity e feche a janela de configurações de Build se ela ainda estiver aberta.
* Selecione a pasta **hologramas** no **painel Projeto**.
* Arraste o objeto **cursor** para o **painel hierarquia** no nível raiz.
* Clique duas vezes no objeto de **cursor** para examiná-lo mais detalhadamente.
* Clique com o botão direito do mouse na pasta **scripts** no painel projeto.
* Clique no submenu **criar** .
* Selecione  **C# script**.
* Nomeie o script **WorldCursor**. Observação: o nome diferencia maiúsculas de minúsculas. Você não precisa adicionar a extensão. cs.
* Selecione o objeto **cursor** no **painel hierarquia**.
* Arraste e solte o script **WorldCursor** no **painel Inspetor**.
* Clique duas vezes no script **WorldCursor** para abri-lo no Visual Studio.
* Copie e cole esse código em **WorldCursor.cs** e **Salve tudo**.

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* Recompile o aplicativo do **arquivo > configurações de Build**.
* Retorne à solução do Visual Studio usada anteriormente para implantar em seu HoloLens.
* Selecione ' recarregar tudo ' quando solicitado.
* Clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.
* Agora, observe a cena e observe como o cursor interage com a forma de objetos.

## <a name="chapter-3---gestures"></a>Capítulo 3-gestos

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

Neste capítulo, adicionaremos suporte para [gestos](gaze-and-commit.md#composite-gestures). Quando o usuário seleciona uma esfera de papel, vamos fazer com que a esfera fique ativando a gravidade usando o mecanismo de física do Unity.

### <a name="objectives"></a>Objetivos

* Controle seus hologramas com o gesto de seleção.

### <a name="instructions"></a>Instruções

Vamos começar criando um script e, em seguida, pode detectar o gesto de seleção.

* Na pasta **scripts** , crie um script chamado **GazeGestureManager**.
* Arraste o script **GazeGestureManager** para o objeto **origamicollection** na hierarquia.
* Abra o script **GazeGestureManager** no Visual Studio e adicione o seguinte código:

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Crie outro script na pasta scripts, desta vez com o nome **SphereCommands**.
* Expanda o objeto **origamicollection** na exibição hierarquia.
* Arraste o script **SphereCommands** para o objeto **Sphere1** no painel hierarquia.
* Arraste o script **SphereCommands** para o objeto **Sphere2** no painel hierarquia.
* Abra o script no Visual Studio para edição e substitua o código padrão por este:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* Exporte, compile e implante o aplicativo em seu HoloLens.
* Examine um dos seus próprios.
* Execute o gesto de seleção e observe a caixa de círculo na superfície abaixo.

## <a name="chapter-4---voice"></a>Capítulo 4-voz

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

Neste capítulo, adicionaremos suporte para dois comandos de [voz](voice-input.md): "redefinir mundo" para retornar o separador para o local original e "soltar a esfera" para fazer a esfera cair.

### <a name="objectives"></a>Objetivos

* Adicione comandos de voz que sempre escutam em segundo plano.
* Crie um holograma que reage a um comando de voz.

### <a name="instructions"></a>Instruções

* Na pasta **scripts** , crie um script chamado **speechmanager**.
* Arraste o script **speechmanager** para o objeto **Origamicollection** na hierarquia
* Abra o script **speechmanager** no Visual Studio.
* Copie e cole esse código em **SpeechManager.cs** e **Salve todos**:

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* Abra o script **SphereCommands** no Visual Studio.
* Atualize o script para ler da seguinte maneira:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* Exporte, compile e implante o aplicativo em seu HoloLens.
* Examine uma das esferas e, em seguida, diga "**drop Sphere**".
* Diga "**Redefinir mundo**" para trazê-los de volta para suas posições iniciais.

## <a name="chapter-5---spatial-sound"></a>Capítulo 5-som espacial

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

Neste capítulo, vamos adicionar música ao aplicativo e, em seguida, disparar efeitos sonoros em determinadas ações. Vamos usar o [som espacial](spatial-sound.md) para dar sons a um local específico no espaço 3D.

### <a name="objectives"></a>Objetivos

* Ouça os hologramas em seu mundo.

### <a name="instructions"></a>Instruções

* Em Unity SELECT no menu superior, **edite > configurações do projeto > áudio**
* No painel inspetor no lado direito, localize a configuração do **plug-in Spatializer** e selecione **MS HRTF Spatializer**.
* Na pasta **hologramas** no painel projeto, arraste o objeto **Ambience** para o objeto **origamicollection** no painel hierarquia.
* Selecione **origamicollection** e localize o componente **fonte de áudio** no painel inspetor. Altere estas propriedades:
  * Verifique a propriedade **espacialize** .
  * Verifique o **jogo em ativo**.
  * Altere a **mistura espacial** para **3D** arrastando o controle deslizante para a direita. O valor deve mudar de 0 para 1 quando você move o controle deslizante.
  * Verifique a propriedade **loop** .
  * Expanda **configurações de som 3D**e insira **0,1** para o **nível de Doppler**.
  * Definir **rolloff de volume** para **rolloff logarítmica**.
  * Defina a **distância máxima** como **20**.
* Na pasta **scripts** , crie um script chamado **SphereSounds**.
* Arraste e solte **SphereSounds** para os objetos **Sphere1** e **Sphere2** na hierarquia.
* Abra o **SphereSounds** no Visual Studio, atualize o código a seguir e **Salve tudo**.

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* Salve o script e retorne ao Unity.
* Exporte, compile e implante o aplicativo em seu HoloLens.
* Mova-se mais de perto do palco e gire-o lado a lado para ouvir a alteração dos sons.

## <a name="chapter-6---spatial-mapping"></a>Capítulo 6-mapeamento espacial

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

Agora vamos usar o [mapeamento espacial](spatial-mapping.md) para posicionar o tabuleiro em um objeto real no mundo real.

### <a name="objectives"></a>Objetivos

* Traga seu mundo real para o mundo virtual.
* Coloque seus hologramas onde forem mais importantes para você.

### <a name="instructions"></a>Instruções

* No Unity, clique na pasta **hologramas** no painel projeto.
* Arraste o ativo de **mapeamento espacial** para a raiz da **hierarquia**.
* Clique no objeto de **mapeamento espacial** na hierarquia.
* No **painel Inspetor**, altere as seguintes propriedades:
  * Marque a caixa **desenhar malhas visuais** .
  * Localize **material de desenho** e clique no círculo à direita. Digite "**wireframe**" no campo de pesquisa na parte superior. Clique no resultado e feche a janela. Quando você fizer isso, o valor para o material de desenho deverá ser definido como wireframe.
* Exporte, compile e implante o aplicativo em seu HoloLens.
* Quando o aplicativo é executado, uma malha delineada se sobrepõe ao seu mundo real.
* Observe como uma esfera de rolagem ficará fora do palco e até o andar!

Agora, mostraremos como mover o Origamicollection para um novo local:

* Na pasta **scripts** , crie um script chamado **TapToPlaceParent**.
* Na **hierarquia**, expanda o **origamicollection** e selecione o objeto **Stage** .
* Arraste o script **TapToPlaceParent** para o objeto Stage.
* Abra o script **TapToPlaceParent** no Visual Studio e atualize-o para o seguinte:

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* Exportar, compilar e implantar o aplicativo.
* Agora você deve ser capaz de posicionar o jogo em um local específico por nuvens-lo, usando o gesto de seleção e, em seguida, movendo para um novo local e usando o gesto de seleção novamente.

## <a name="chapter-7---holographic-fun"></a>Capítulo 7 – diversão Holographic

### <a name="objectives"></a>Objetivos

* Revele a entrada para um Holographic Underworld.

### <a name="instructions"></a>Instruções

Agora, mostraremos como descobrir o Holographic Underworld:

* Na pasta **hologramas** no painel Projeto:
  * Arraste **Underworld** para a hierarquia para ser um filho de **origamicollection**.
* Na pasta **scripts** , crie um script chamado **HitTarget**.
* Na **hierarquia**, expanda o **origamicollection**.
* Expanda o objeto de **estágio** e selecione o objeto de **destino** (ventilador azul).
* Arraste o script **HitTarget** para o objeto de **destino** .
* Abra o script **HitTarget** no Visual Studio e atualize-o para o seguinte:

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* No Unity, selecione o objeto de **destino** .
* Agora, duas propriedades públicas estão visíveis no componente de **destino de visita** e precisam fazer referência a objetos em nossa cena:
  * Arraste **Underworld** do painel **hierarquia** para a propriedade **Underworld** no componente de **destino de visita** .
  * Arraste o **estágio** do painel **hierarquia** até o **objeto para ocultar** a propriedade no componente de destino de **visita** .
* Exportar, compilar e implantar o aplicativo.
* Coloque a coleção de origami no piso e, em seguida, use o gesto de seleção para fazer uma queda de esfera.
* Quando a esfera atinge o destino (ventilador azul), ocorrerá uma explosão. A coleção será ocultada e um orifício para o Underworld será exibido.

## <a name="the-end"></a>Fim

E esse é o fim deste tutorial!

Você aprendeu:

* Como criar um aplicativo Holographic no Unity.
* Como fazer uso de olhar, gesto, voz, som e mapeamento espacial.
* Como criar e implantar um aplicativo usando o Visual Studio.

Agora você está pronto para começar a criar sua própria experiência de Holographic!

## <a name="see-also"></a>Consulte também

* [Sr Basics 101E: concluir o projeto com o emulador](holograms-101e.md)
* [Foco](gaze-and-commit.md)
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Entrada de voz](voice-input.md)
* [Som espacial](spatial-sound.md)
* [Mapeamento espacial](spatial-mapping.md)
