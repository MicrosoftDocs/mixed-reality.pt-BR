---
title: Sr Sharing 240-vários dispositivos HoloLens
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes do compartilhamento de hologramas.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, compartilhamento, rede, Academia, tutorial
ms.openlocfilehash: 0d8e8f4484546d82caadf162623a6f4059eb2f00
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434569"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>Sr Sharing 240: vários dispositivos HoloLens

Os hologramas têm a presença em nosso mundo, permanecendo em vigor conforme avançamos no espaço. O HoloLens mantém os hologramas em vigor usando vários [sistemas de coordenadas](coordinate-systems.md) para controlar o local e a orientação dos objetos. Quando compartilhamos esses sistemas de coordenadas entre dispositivos, podemos criar uma experiência compartilhada que nos permite participar de um mundo Holographic compartilhado.

Neste tutorial, iremos:

* Configure uma rede para uma experiência compartilhada.
* Compartilhe hologramas entre dispositivos de HoloLens.
* Descubra outras pessoas em nosso mundo Holographic compartilhado.
* Crie uma experiência interativa compartilhada onde você pode ter como alvo outros jogadores – e inicie o projéteis neles!

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Sr Sharing 240: vários dispositivos HoloLens</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md) com acesso à Internet.
* Pelo menos dois dispositivos HoloLens [configurados para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) exigidos pelo projeto. Requer o Unity 2017,2 ou posterior.
  * Se você ainda precisar de suporte do Unity 5,6, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).
  * Se você ainda precisar de suporte do Unity 5,5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Se você ainda precisar de suporte do Unity 5,4, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar. Mantenha o nome da pasta como **SharedHolograms**.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Capítulo 1 – holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

Neste capítulo, vamos configurar nosso primeiro projeto do Unity e percorrer o processo de compilação e implantação.

### <a name="objectives"></a>Objetivos

* Configurar o Unity para desenvolver aplicativos Holographic.
* Veja seu holograma!

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **abrir**.
* Insira o local como a pasta **SharedHolograms** que você desarquivou anteriormente.
* Selecione **nome do projeto** e clique em **Selecionar pasta**.
* Na **hierarquia**, clique com o botão direito do mouse na **câmera principal** e selecione **excluir**.
* Na pasta **HoloToolkit-Sharing-240/pré-fabricados/Camera** , localize a **câmera principal** pré-fabricado.
* Arraste e solte a **câmera principal** na **hierarquia**.
* Na **hierarquia**, clique em **criar** e em **criar vazio**.
* Clique com o botão direito do mouse no novo **gameobject** e selecione **renomear**.
* Renomeie o gameobject para **hologramacollection**.
* Selecione o objeto **hologramacollection** na **hierarquia**.
* No **Inspetor** , defina a **posição de transformação** como: **X: 0, Y:-0,25, Z: 2**.
* Na pasta **hologramas** no **painel Projeto**, localize o ativo **EnergyHub** .
* Arraste e solte o objeto **EnergyHub** do **painel Projeto** para a **hierarquia** como um **filho de hologramacollection**.
* Selecione **arquivo > salvar cena como...**
* Nomeie a cena **SharedHolograms** e clique em **salvar**.
* Pressione o botão **reproduzir** no Unity para visualizar os hologramas.
* Pressione **executar** uma segunda vez para parar o modo de visualização.

**Exportar o projeto do Unity para o Visual Studio**

* Em Unity, selecione **arquivo > configurações de Build**.
* Clique em **Adicionar abrir cenas** para adicionar a cena.
* Selecione **plataforma universal do Windows** na lista **plataforma** e clique em **alternar plataforma**.
* Defina o **SDK** como **Universal 10**.
* Defina **o dispositivo de destino** para o tipo de compilação **HoloLens** e **UWP** como **D3D**.
* Verifique **os C# projetos do Unity**.
* Clique em **Compilar**.
* Na janela Explorador de arquivos que aparece, crie uma **nova pasta** chamada "aplicativo".
* Clique uma vez na pasta do **aplicativo** .
* Pressione **Selecionar pasta**.
* Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.
* Abra a pasta do **aplicativo** .
* Abra **SharedHolograms. sln** para iniciar o Visual Studio.
* Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.
* Clique na seta suspensa ao lado de computador local e selecione **dispositivo remoto**.
    * Defina o **endereço** para o nome ou endereço IP do seu HoloLens. Se você não souber o endereço IP do dispositivo, procure **configurações > rede & Internet > opções avançadas** ou pergunte ao Cortana **"Ei Cortana, qual é meu endereço IP?"**
    * Deixe o **modo de autenticação** definido como **Universal**.
    * Clique em **selecionar**
* Clique em **depurar > iniciar sem Depurar** ou pressione **Ctrl + F5**. Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com o Visual Studio](using-visual-studio.md#pairing-your-device).
* Coloque em seu HoloLens e encontre o holograma EnergyHub.

## <a name="chapter-2---interaction"></a>Capítulo 2-interação

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

Neste capítulo, vamos interagir com nossos hologramas. Primeiro, vamos adicionar um cursor para visualizar nosso [olhar](gaze-and-commit.md). Em seguida, vamos adicionar [gestos](gaze-and-commit.md#composite-gestures) e usar nossa mão para colocar nossos hologramas em espaço.

### <a name="objectives"></a>Objetivos

* Use a entrada olhar para controlar um cursor.
* Use a entrada de gestos para interagir com os hologramas.

### <a name="instructions"></a>Instruções

**Foco**

* No **painel hierarquia** , selecione o objeto **hologramacollection** .
* No **painel Inspetor** , clique no botão **Adicionar componente** .
* No menu, digite na caixa de pesquisa **olhar Manager**. Selecione o resultado da pesquisa.
* Na pasta **HoloToolkit-Sharing-240\Prefabs\Input** , localize o ativo de **cursor** .
* Arraste e solte o ativo do **cursor** na **hierarquia**.

**Gesture**

* No **painel hierarquia** , selecione o objeto **hologramacollection** .
* Clique em **Adicionar componente** e digite **Gerenciador de gestos** no campo de pesquisa. Selecione o resultado da pesquisa.
* No **painel hierarquia**, expanda **hologramacollection**.
* Selecione o objeto **EnergyHub** filho.
* No **painel Inspetor** , clique no botão **Adicionar componente** .
* No menu, digite o **posicionamento do holograma**da caixa de pesquisa. Selecione o resultado da pesquisa.
* Salve a cena selecionando **arquivo > salvar cena**.

**Implantar e desfrutar**

* Crie e implante em seu HoloLens, usando as instruções do capítulo anterior.
* Depois que o aplicativo for iniciado no seu HoloLens, mova seu rumo e observe como o EnergyHub segue o olhar.
* Observe como o cursor aparece quando você olhar sobre o holograma e muda para uma luz pontual quando não nuvens em um holograma.
* Execute um toque de ar para posicionar o holograma. No momento em nosso projeto, você só pode posicionar o holograma uma vez (reimplantar para tentar novamente).

## <a name="chapter-3---shared-coordinates"></a>Capítulo 3-coordenadas compartilhadas

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

É divertido ver e interagir com os hologramas, mas vamos continuar. Vamos configurar nossa primeira experiência compartilhada-um holograma que todos possam ver em conjunto.

### <a name="objectives"></a>Objetivos

* Configure uma rede para uma experiência compartilhada.
* Estabeleça um ponto de referência comum.
* Compartilhe sistemas de coordenadas entre dispositivos.
* Todos veem o mesmo holograma!

>[!NOTE]
>Os recursos **InternetClientServer** e **PrivateNetworkClientServer** devem ser declarados para que um aplicativo se conecte ao servidor de compartilhamento. Isso é feito para você já nos hologramas 240, mas tenha isso em mente para seus próprios projetos.

>1. No editor do Unity, vá para as configurações do Player navegando até "Editar configurações do projeto > > Player"
>2. Clique na guia "Windows Store"
>3. Na seção "publicando Configurações > recursos", verifique o recurso **InternetClientServer** e o recurso **PrivateNetworkClientServer**

### <a name="instructions"></a>Instruções

* No **painel Projeto** , navegue até a pasta **HoloToolkit-Sharing-240\Prefabs\Sharing**
* Arraste e solte o pré-fabricado de **compartilhamento** no **painel hierarquia**.

Em seguida, precisamos iniciar o serviço de compartilhamento. Apenas **um PC** na experiência compartilhada precisa fazer essa etapa.

* No Unity-no menu superior, selecione o **menu HoloToolkit-Sharing-240**.
* Selecione o item **Iniciar compartilhamento de serviço** na lista suspensa.
* Marque a opção **rede privada** e clique em **permitir acesso** quando o prompt de firewall for exibido.
* Anote o endereço IPv4 exibido na janela do console do serviço de compartilhamento. Esse é o mesmo IP que o computador no qual o serviço está sendo executado.

Siga o restante das instruções em **todos os PCs** que ingressarão na experiência compartilhada.

* Na **hierarquia**, selecione o objeto de **compartilhamento** .
* No **Inspetor**, no componente **estágio de compartilhamento** , altere o **endereço do servidor** de ' localhost ' para o endereço IPv4 do computador que executa o SharingService. exe.
* Na **hierarquia** , selecione o objeto **hologramacollection** .
* No **Inspetor** , clique no botão **Adicionar componente** .
* Na caixa de pesquisa, digite **Gerenciador de importação e exportação**. Selecione o resultado da pesquisa.
* No **painel Projeto** , navegue até a pasta **scripts** .
* Clique duas vezes no script **HologramPlacement** para abri-lo no Visual Studio.
* Substitua o conteúdo pelo código abaixo.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* De volta ao Unity, selecione **hologramacollection** no **painel hierarquia**.
* No **painel Inspetor** , clique no botão **Adicionar componente** .
* No menu, digite o Gerenciador de estado do **aplicativo**da caixa de pesquisa. Selecione o resultado da pesquisa.

**Implantar e desfrutar**

* Compile o projeto para seus dispositivos de HoloLens.
* Designe um HoloLens para implantar primeiro. Você precisará aguardar a âncora ser carregada no serviço antes de poder colocar o EnergyHub (isso pode levar aproximadamente 30-60 segundos). Até que o upload seja feito, seus gestos de toque serão ignorados.
* Depois que o EnergyHub tiver sido colocado, seu local será carregado para o serviço e você poderá implantá-lo em todos os outros dispositivos do HoloLens.
* Quando um novo HoloLens ingressa primeiro na sessão, o local do EnergyHub pode não estar correto nesse dispositivo. No entanto, assim que os locais de âncora e EnergyHub tiverem sido baixados do serviço, o EnergyHub deverá ir para o local novo e compartilhado. Se isso não acontecer em cerca de 30-60 segundos, passe para o local em que o HoloLens original estava ao definir a âncora para reunir mais pistas de ambiente. Se o local ainda não for bloqueado, reimplante-o no dispositivo.
* Quando os dispositivos estiverem prontos e executando o aplicativo, procure o EnergyHub. Você pode concordar com o local do holograma e em qual direção o texto está voltado?

## <a name="chapter-4---discovery"></a>Capítulo 4-descoberta

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Agora, todos podem ver o mesmo holograma! Agora, vamos ver todos os outros conectados ao nosso mundo Holographic compartilhado. Neste capítulo, vamos pegar o local e a rotação do cabeçalho de todos os outros dispositivos HoloLens na mesma sessão de compartilhamento.

### <a name="objectives"></a>Objetivos

* Descubra um ao outro em nossa experiência compartilhada.
* Escolha e compartilhe um avatar de jogador.
* Anexe o avatar do jogador ao lado dos cabeçotes de todos.

### <a name="instructions"></a>Instruções

* No **painel Projeto** , navegue até a pasta **hologramas** .
* Arraste e solte o **PlayerAvatarStore** na **hierarquia**.
* No **painel Projeto** , navegue até a pasta **scripts** .
* Clique duas vezes no script **AvatarSelector** para abri-lo no Visual Studio.
* Substitua o conteúdo pelo código abaixo.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* Na **hierarquia** , selecione o objeto **hologramacollection** .
* No **Inspetor** , clique em **Adicionar componente**.
* Na caixa de pesquisa, digite **Gerenciador do player local**. Selecione o resultado da pesquisa.
* Na **hierarquia** , selecione o objeto **hologramacollection** .
* No **Inspetor** , clique em **Adicionar componente**.
* Na caixa de pesquisa, digite **Gerenciador de Player remoto**. Selecione o resultado da pesquisa.
* Abra o script **HologramPlacement** no Visual Studio.
* Substitua o conteúdo pelo código abaixo.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Abra o script **AppStateManager** no Visual Studio.
* Substitua o conteúdo pelo código abaixo.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**Implantar e desfrutar**

* Crie e implante o projeto em seus dispositivos de HoloLens.
* Quando você ouvir um som de ping, localize o menu de seleção de avatar e selecione um avatar com o gesto de toque do ar.
* Se você não estiver olhando para nenhum holograma, o ponto leve em volta do cursor irá transformar uma cor diferente quando o seu HoloLens estiver se comunicando com o serviço: inicializando (roxo escuro), baixando a âncora (verde), importando/exportando dados do local (amarelo), carregando a âncora (azul). Se o seu ponto leve em volta do cursor for a cor padrão (roxo claro), você estará pronto para interagir com outros jogadores em sua sessão!
* Examine outras pessoas conectadas ao seu espaço – haverá um robô Holographic flutuante acima de seus ressaltos e imitandondo seus movimentos de cabeça!

## <a name="chapter-5---placement"></a>Capítulo 5 – posicionamento

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

Neste capítulo, vamos tornar a âncora capaz de ser colocada em superfícies do mundo real. Usaremos coordenadas compartilhadas para colocar essa âncora no ponto central entre todos conectados à experiência compartilhada.

### <a name="objectives"></a>Objetivos

* Coloque os hologramas na malha de mapeamento espacial com base na posição de cabeçalho dos jogadores.

### <a name="instructions"></a>Instruções

* No **painel Projeto** , navegue até a pasta **hologramas** .
* Arraste e solte o **CustomSpatialMapping** pré-fabricado na **hierarquia**.
* No **painel Projeto** , navegue até a pasta **scripts** .
* Clique duas vezes no script **AppStateManager** para abri-lo no Visual Studio.
* Substitua o conteúdo pelo código abaixo.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* No **painel Projeto** , navegue até a pasta **scripts** .
* Clique duas vezes no script **HologramPlacement** para abri-lo no Visual Studio.
* Substitua o conteúdo pelo código abaixo.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**Implantar e desfrutar**

* Crie e implante o projeto em seus dispositivos de HoloLens.
* Quando o aplicativo estiver pronto, aguarde um círculo e observe como o EnergyHub aparece no centro de todos.
* Toque para posicionar o EnergyHub.
* Experimente o comando de voz "redefinir destino" para escolher o EnergyHub de backup e trabalhar juntos como um grupo para mover o holograma para um novo local.

## <a name="chapter-6---real-world-physics"></a>Capítulo 6-física do mundo real

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

Neste capítulo, adicionaremos hologramas que separam superfícies do mundo real. Assista ao seu espaço preencha com projetos iniciados por você e seus amigos!

### <a name="objectives"></a>Objetivos

* Inicie o projéteis que salta as superfícies do mundo real.
* Compartilhe o projéteis para que outros jogadores possam vê-los.

### <a name="instructions"></a>Instruções

* Na **hierarquia** , selecione o objeto **hologramacollection** .
* No **Inspetor** , clique em **Adicionar componente**.
* Na caixa de pesquisa, digite **Projectile Launcher**. Selecione o resultado da pesquisa.

**Implantar e desfrutar**

* Crie e implante em seus dispositivos de HoloLens.
* Quando o aplicativo estiver em execução em todos os dispositivos, execute um toque de ar para iniciar o Projectile em superfícies do mundo real.
* Veja o que acontece quando seu Projectile colide com o Avatar de outro jogador!

## <a name="chapter-7---grand-finale"></a>Capítulo 7 – final geral

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

Neste capítulo, vamos descobrir um portal que só pode ser descoberto com a colaboração.

### <a name="objectives"></a>Objetivos

* Trabalhe em conjunto para iniciar o projéteis suficiente na âncora para descobrir um portal secreto!

### <a name="instructions"></a>Instruções

* No **painel Projeto** , navegue até a pasta **hologramas** .
* Arraste e solte o ativo **Underworld** como um **filho de hologramacollection**.
* Com o **hologramacollection** selecionado, clique no botão **Adicionar componente** no **Inspetor**.
* No menu, digite na caixa de pesquisa **ExplodeTarget**. Selecione o resultado da pesquisa.
* Com o **hologramacollection** selecionado, na **hierarquia** , arraste o objeto **EnergyHub** para o campo de **destino** no **Inspetor**.
* Com o **hologramacollection** selecionado, na **hierarquia** , arraste o objeto **Underworld** para o campo **Underworld** no **Inspetor**.

**Implantar e desfrutar**

* Crie e implante em seus dispositivos de HoloLens.
* Quando o aplicativo for iniciado, colabore em conjunto para iniciar o projéteis no EnergyHub.
* Quando o Underworld for exibido, inicie projéteis em Underworld robots (pressione um robô três vezes para diversão extra).
