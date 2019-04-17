---
title: Fundamentos do MR 101E - projeto completo com o emulador
description: Siga este passo a passo usando o Unity, o Visual Studio e o emulador do HoloLens para aprender os fundamentos de um aplicativo holográfico de codificação.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realidade misturada, realidade mista do Windows, HoloLens, holograma, o emulador do tutorial, academy
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589453"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a>Noções básicas sobre MR 101E: Projeto completo com o emulador

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

Este tutorial orientará você por meio de um projeto completo, compilado no Unity, que demonstra os principais recursos do Windows Mixed Reality em, incluindo HoloLens [olhares](gaze.md), [gestos](gestures.md), [deentradadevoz](voice-input.md), [som espacial](spatial-sound.md) e [mapeamento espacial](spatial-mapping.md). O tutorial levará cerca de 1 hora para ser concluída.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td>Noções básicas sobre MR 101E: Projeto completo com o emulador</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).

### <a name="project-files"></a>Arquivos de projeto

* Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) exigidos pelo projeto. Requer o Unity 2017.2 ou posterior.
  * Se você ainda precisar de suporte do Unity 5.6, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Se você ainda precisar de suporte do Unity 5.5, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Se você ainda precisar de suporte de Unity 5.4, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local. Mantenha o nome da pasta como **Origami**.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Capítulo 1 - world "Holo"

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

Neste capítulo, vamos configurar nosso primeiro projeto do Unity e percorrer a compilação e o processo de implantação.

### <a name="objectives"></a>Objetivos

* Configure o Unity para o desenvolvimento holográfico.
* Faça um holograma.
* Consulte um holograma que você fez.

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **aberto**.
* Insira o local como o **Origami** pasta você anteriormente não arquivadas.
* Selecione **Origami** e clique em **Selecionar pasta**.
* Salve a nova cena: **Arquivo** / **salvar cena como**.
* Nomeie a cena **Origami** e pressione a **salvar** botão.

#### <a name="setup-the-main-camera"></a>A câmera principal de instalação

* No **painel de hierarquia**, selecione **câmera principal**.
* No **Inspector** defina sua posição de transformação **0, 0,0**.
* Localizar o **Limpar sinalizadores** propriedade e altere a lista suspensa de **Skybox** para **cor sólida**.
* Clique no **plano de fundo** campo para abrir um seletor de cores.
* Definir **R, G, B e A** à **0**.

#### <a name="setup-the-scene"></a>Instalação da cena

* No **painel de hierarquia**, clique em **Create** e **criar vazio**.
* Clique com botão direito a nova **GameObject** e selecione Renomear. Renomeie o GameObject para **OrigamiCollection**.
* Dos **hologramas** pasta o **painel projeto**:
  * Arraste **estágio** na hierarquia para ser um filho do **OrigamiCollection**.
  * Arraste **Sphere1** na hierarquia para ser um filho do **OrigamiCollection**.
  * Arraste **Sphere2** na hierarquia para ser um filho do **OrigamiCollection**.
* Com o botão direito do **luz direcional** do objeto na **painel de hierarquia** e selecione **excluir**.
* Dos **hologramas** pasta, arraste **luzes** na raiz do **painel de hierarquia**.
* No **hierarquia**, selecione o **OrigamiCollection**.
* No **Inspector**, defina a posição de transformação **0, -0,5, 2.0**.
* Pressione a **reproduzir** botão no Unity para visualizar seu hologramas.
* Você deve ver os objetos do Origami na janela de visualização.
* Pressione **reproduzir** uma segunda vez para parar o modo de visualização.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Exportar o projeto do Unity para Visual Studio

* No, selecione Unity **arquivo > configurações de Build**.
* Selecione **Windows Store** na **plataforma** lista e clique em **alternar plataforma**.
* Definir **SDK** à **10 Universal** e **tipo de Build** para **D3D**.
* Verifique **Unity C# projetos**.
* Clique em **cenas abra Adicionar** para adicionar a cena.
* Clique em **configurações do Player...** .
* No, selecione Painel Inspetor a **logotipo do Windows Store**. Em seguida, selecione **configurações de publicação**.
* No **capacidades** seção, selecione a **microfone** e **SpatialPerception** recursos.
* Na janela Configurações de compilação, clique em **Build**.
* Criar uma **nova pasta** chamado "App".
* Único clique a **pasta aplicativo**.
* Pressione **Selecionar pasta**.
* Quando Unity é feito, será exibida uma janela do Explorador de arquivos.
* Abra o **aplicativo** pasta.
* Abra o **solução do Visual Studio Origami**.
* Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **X86**.
  * Clique na seta ao lado do botão de dispositivo e selecione **HoloLens emulador**.
  * Clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.
  * Após algum tempo, o emulador será iniciado com o projeto Origami. Ao iniciar pela primeira vez o [emulador](using-the-hololens-emulator.md), ele pode levar até 15 minutos para que o emulador será iniciado. Depois que ele é iniciado, não o feche.

## <a name="chapter-2---gaze"></a>Capítulo 2 - olhar

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

Neste capítulo, vamos apresentar a primeira das três maneiras de interagir com seu hologramas – [olhares](gaze.md).

### <a name="objectives"></a>Objetivos

* Visualize seu foco usando um cursor bloqueado pelo mundo.

### <a name="instructions"></a>Instruções

* Volte para seu projeto do Unity e fechar a janela de configurações de compilação se ele ainda está aberto.
* Selecione o **hologramas** pasta o **painel projeto**.
* Arraste o **Cursor** do objeto para o **painel de hierarquia** no nível raiz.
* Clique duas vezes no **Cursor** objeto para examiná-lo.
* Clique com botão direito no **Scripts** pasta no painel de projeto.
* Clique o **criar** submenu.
* Selecione  **C# Script**.
* Nomeie o script **WorldCursor**. Observação: O nome diferencia maiúsculas de minúsculas. Você não precisará adicionar a extensão. cs.
* Selecione o **Cursor** do objeto na **painel de hierarquia**.
* Arraste e solte os **WorldCursor** o script na **painel Inspetor**.
* Clique duas vezes o **WorldCursor** script para abri-lo no Visual Studio.
* Copie e cole este código em **WorldCursor.cs** e **Salvar tudo**.

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

            // Move thecursor to the point where the raycast hit.
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
* Retorne para a solução do Visual Studio usada anteriormente para implantar no emulador.
* Selecione 'Recarregar todos' quando solicitado.
* Clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.
* Use o controlador do Xbox para olhar em volta da cena. Observe como o cursor interage com a forma de objetos.

## <a name="chapter-3---gestures"></a>Capítulo 3 - gestos

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

Neste capítulo, vamos adicionar suporte para [gestos](gestures.md). Quando o usuário seleciona uma esfera de papel, faremos a esfera se enquadram ativando gravidade usando o mecanismo de física do Unity.

### <a name="objectives"></a>Objetivos

* Controle seu hologramas com o gesto de Select.

### <a name="instructions"></a>Instruções

Vamos começar criando um script que pode detectar o gesto de Select.

* No **Scripts** pasta, crie um script chamado **GazeGestureManager**.
* Arraste o **GazeGestureManager** de script para o **OrigamiCollection** objeto na hierarquia.
* Abra o **GazeGestureManager** script no Visual Studio e adicione o seguinte código:

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
    void Start()
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

* Criar outro script na pasta Scripts, desta vez denominada **SphereCommands**.
* Expanda o **OrigamiCollection** objeto na exibição de hierarquia.
* Arraste o **SphereCommands** gerar script para o **Sphere1** objeto no painel de hierarquia.
* Arraste o **SphereCommands** gerar script para o **Sphere2** objeto no painel de hierarquia.
* Abra o script no Visual Studio para edição e substitua o código padrão com este:

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

* Exportar, criar e implantar o aplicativo no emulador do HoloLens.
* Olhar em volta da cena e center em um das esferas.
* Pressione a **um** botão no controlador Xbox ou pressione a Spacebar para simular o gesto de Select.

## <a name="chapter-4---voice"></a>Capítulo 4 - voz

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

Neste capítulo, vamos adicionar suporte para dois [comandos de voz](voice-input.md): "Redefinir world" para retorna esferas soltos no local original e "Soltar esfera" para fazer com que a esfera se encaixam.

### <a name="objectives"></a>Objetivos

* Adicione comandos de voz que sempre escutam em segundo plano.
* Crie um holograma que reage a um comando de voz.

### <a name="instructions"></a>Instruções

* No **Scripts** pasta, crie um script chamado **SpeechManager**.
* Arraste o **SpeechManager** de script para o **OrigamiCollection** objeto na hierarquia
* Abra o **SpeechManager** script no Visual Studio.
* Copie e cole este código em **SpeechManager.cs** e **Salvar tudo**:

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

* Abra o **SphereCommands** script no Visual Studio.
* Atualize o script da seguinte forma:

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

* Exportar, criar e implantar o aplicativo no emulador do HoloLens.
* O emulador dará suporte microfone do PC e responder a sua voz: ajuste o modo de exibição, para que o cursor estiver em um das esferas e dizer "Drop esfera".
* Dizer "**mundo redefinir**" para colocá-los de volta para suas posições iniciais.

## <a name="chapter-5---spatial-sound"></a>Capítulo 5 – som espacial

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

Neste capítulo, vamos adicionar música para o aplicativo e, em seguida, disparar efeitos de som em determinadas ações. Usaremos [som espacial](spatial-sound.md) dar sons um local específico no espaço 3D.

### <a name="objectives"></a>Objetivos

* Ouça hologramas seu mundo.

### <a name="instructions"></a>Instruções

* No menu superior, selecione Unity **Editar > configurações do projeto > áudio**
* Localizar o **plug-in do Spatializer** definição e selecione **MS HRTF Spatializer**.
* Dos **hologramas** pasta, arraste o **ambiente** do objeto para o **OrigamiCollection** objeto no painel de hierarquia.
* Selecione **OrigamiCollection** e localize o **Audio Source** componente. Altere essas propriedades:
  * Verifique as **Spatialize** propriedade.
  * Verifique as **tocar no ativo**.
  * Alteração **Blend espacial** à **3D** arrastando o controle deslizante para a direita.
  * Verifique as **Loop** propriedade.
  * Expandir **configurações de som 3D**e insira **0,1** para **nível Doppler**.
  * Definir **Volume Rolloff** à **Rolloff logarítmica**.
  * Definir **distância máxima** à **20**.
* No **Scripts** pasta, crie um script chamado **SphereSounds**.
* Arraste **SphereSounds** para o **Sphere1** e **Sphere2** objetos na hierarquia.
* Abra **SphereSounds** no Visual Studio, atualize o código a seguir e **Salvar tudo**.

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

* Salve o script e retornar para o Unity.
* Exportar, criar e implantar o aplicativo no emulador do HoloLens.
* Use fones de ouvido para obter o efeito completo e mover mais próximo e mais longe ao Palco para ouvir os sons alterar.

## <a name="chapter-6---spatial-mapping"></a>Mapeamento de capítulos 6 - espacial

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

Agora, vamos usar [mapeamento espacial](spatial-mapping.md) para colocar o tabuleiro do jogo em um objeto real no mundo real.

### <a name="objectives"></a>Objetivos

* Traga o seu mundo real para o mundo virtual.
* Coloque seu hologramas onde eles mais importam para você.

### <a name="instructions"></a>Instruções

* Clique no **hologramas** pasta no painel de projeto.
* Arraste o **mapeamento espacial** ativo na raiz do **hierarquia**.
* Clique no **mapeamento espacial** objeto na hierarquia.
* No **painel Inspetor**, altere as seguintes propriedades:
  * Verifique as **desenhar malhas Visual** caixa.
  * Localize **desenhar Material** e clique no círculo no lado direito. Tipo "**wireframe**" no campo de pesquisa na parte superior. Clique no resultado e, em seguida, feche a janela.
* Exportar, criar e implantar o aplicativo no emulador do HoloLens.
* Quando o aplicativo é executado, uma malha de uma sala de estar reais digitalizada anteriormente será renderizada no wireframe.
* Assista como uma esfera sem interrupção cairá desativar o estágio e, para o chão!

Agora, mostraremos como mover o OrigamiCollection para um novo local:

* No **Scripts** pasta, crie um script chamado **TapToPlaceParent**.
* No **hierarquia**, expanda o **OrigamiCollection** e selecione o **estágio** objeto.
* Arraste o **TapToPlaceParent** script para o objeto de estágio.
* Abra o **TapToPlaceParent** de script no Visual Studio e atualizá-lo para ser o seguinte:

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

* Exportar, criar e implantar o aplicativo.
* Agora você agora deve ser capaz de colocar o jogo em um local específico, Observação nisso, usar o gesto de Select (**um** ou barra de espaços) e, em seguida, movendo para um novo local e usar o gesto de Select novamente.

## <a name="the-end"></a>Fim

E esse é o final deste tutorial!

Você aprendeu:

* Como criar um aplicativo holográfico no Unity.
* Como fazer uso de olhar, gesto, voz, sons e mapeamento espacial.
* Como criar e implantar um aplicativo usando o Visual Studio.

Agora você está pronto para começar a criar seus próprios aplicativos holográfico!

## <a name="see-also"></a>Consulte também

* [Noções básicas sobre MR 101: Projeto completo do dispositivo](holograms-101.md)
* [Gaze](gaze.md)
* [Gestos](gestures.md)
* [Entrada de voz](voice-input.md)
* [Som espacial](spatial-sound.md)
* [Mapeamento espacial](spatial-mapping.md)
