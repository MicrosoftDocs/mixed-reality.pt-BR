---
title: MR compartilhamento 240 - vários dispositivos do HoloLens
description: Siga este passo a passo usando o Unity, o Visual Studio e o HoloLens para saber os detalhes de compartilhamento hologramas de codificação.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, compartilhamento, rede, academy, tutorial
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589850"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR Sharing 240: Vários dispositivos do HoloLens

Hologramas recebem presença em nosso mundo por restantes em vigor à medida que avançarmos no espaço. HoloLens mantém hologramas no lugar usando vários [sistemas de coordenadas](coordinate-systems.md) para controlar o local e a orientação de objetos. Quando podemos compartilhar esses sistemas de coordenadas entre dispositivos, podemos criar uma experiência compartilhada que permite fazer parte de um mundo holográfico compartilhado.

Neste tutorial, nós iremos:

* Configure uma rede para uma experiência compartilhada.
* Compartilhar hologramas em todos os dispositivos do HoloLens.
* Descubra outras pessoas em nosso mundo holográfica compartilhado.
* Crie uma experiência interativa compartilhada onde você pode direcionar o outros jogadores - e iniciar os projéteis-los!

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td>MR Sharing 240: Vários dispositivos do HoloLens</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md) com acesso à Internet.
* Pelo menos dois dispositivos HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) exigidos pelo projeto. Requer o Unity 2017.2 ou posterior.
  * Se você ainda precisar de suporte do Unity 5.6, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).
  * Se você ainda precisar de suporte do Unity 5.5, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Se você ainda precisar de suporte de Unity 5.4, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local. Mantenha o nome da pasta como **SharedHolograms**.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Capítulo 1 - Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

Neste capítulo, vamos configurar nosso primeiro projeto do Unity e percorrer a compilação e o processo de implantação.

### <a name="objectives"></a>Objetivos

* A instalação do Unity para desenvolver aplicativos holographic.
* Consulte seu holograma!

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **aberto**.
* Insira o local como o **SharedHolograms** pasta você anteriormente não arquivados.
* Selecione **nome do projeto** e clique em **Selecionar pasta**.
* No **hierarquia**, clique com botão direito do **câmera principal** e selecione **excluir**.
* No **HoloToolkit-Sharing-240/pré-fabricados/câmera** pasta, localize a **câmera principal** pré-fabricado.
* Arraste e solte os **câmera principal** para o **hierarquia**.
* No **hierarquia**, clique em **Create** e **criar vazio**.
* Clique com botão direito a nova **GameObject** e selecione **Renomear**.
* Renomeie o GameObject para **HologramCollection**.
* Selecione o **HologramCollection** do objeto na **hierarquia**.
* No **Inspetor** definir o **transformar posição** para: **X: 0, Y: -0,25, Z: 2**.
* No **hologramas** pasta no **painel projeto**, localize o **EnergyHub** ativo.
* Arraste e solte a **EnergyHub** do objeto da **painel projeto** para o **hierarquia** como um **filho de HologramCollection**.
* Selecione **arquivo > Salvar cena como...**
* Nomeie a cena **SharedHolograms** e clique em **salvar**.
* Pressione a **reproduzir** botão no Unity para visualizar seu hologramas.
* Pressione **reproduzir** uma segunda vez para parar o modo de visualização.

**Exportar o projeto do Unity para Visual Studio**
* No, selecione Unity **arquivo > configurações de Build**.
* Clique em **cenas abra Adicionar** para adicionar a cena.
* Selecione **plataforma Universal do Windows** na **plataforma** lista e clique em **alternar plataforma**.
* Definir **SDK** à **10 Universal**.
* Definir **dispositivo de destino** à **HoloLens** e **tipo de compilação de UWP** para **D3D**.
* Verifique **Unity C# projetos**.
* Clique em **Compilar**.
* Na janela do Gerenciador de arquivo aparece, crie uma **nova pasta** chamado "App".
* Único clique a **aplicativo** pasta.
* Pressione **Selecionar pasta**.
* Quando Unity é feito, será exibida uma janela do Explorador de arquivos.
* Abra o **aplicativo** pasta.
* Abra **SharedHolograms.sln** para iniciar o Visual Studio.
* Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **X86**.
* Clique na seta suspensa ao lado do computador Local e selecione **dispositivo remoto**.
    * Defina as **endereço** no nome ou endereço IP do seu HoloLens. Se você não souber o endereço IP do dispositivo, examine **Configurações > rede e Internet > Opções avançadas** ou perguntar ao Cortana **"Ei Cortana, o que é meu endereço IP?"**
    * Deixe o **modo de autenticação** definido como **Universal**.
    * Clique em **selecionar**
* Clique em **Depurar > Iniciar sem depuração** ou pressione **Ctrl + F5**. Se essa for a primeira vez em que implantar seu dispositivo, você precisará [emparelhá-lo com o Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
* Coloque o HoloLens e localizar o holograma EnergyHub.

## <a name="chapter-2---interaction"></a>Capítulo 2 - interação

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

Neste capítulo, vai interagimos com nossos hologramas. Primeiro, vamos adicionar um cursor para visualizar nossos [olhares](gaze.md). Em seguida, adicionaremos [gestos](gestures.md) e use nossos mãos para colocar nosso hologramas no espaço.

### <a name="objectives"></a>Objetivos

* Use a olhar para controlar um cursor de entrada.
* Use o gesto de entrada para interagir com hologramas.

### <a name="instructions"></a>Instruções

**Gaze**
* No **painel de hierarquia** selecionar a **HologramCollection** objeto.
* No **painel Inspetor** clique a **adicionar componente** botão.
* No menu, digite na caixa de pesquisa **olhares Manager**. Selecione o resultado da pesquisa.
* No **240\Prefabs\Input compartilhamento HoloToolkit** pasta, localize a **Cursor** ativo.
* Arraste e solte os **Cursor** ativo para o **hierarquia**.

**Gesto**
* No **painel de hierarquia** selecionar a **HologramCollection** objeto.
* Clique em **Add Component** e digite **gesto Manager** no campo de pesquisa. Selecione o resultado da pesquisa.
* No **painel de hierarquia**, expanda **HologramCollection**.
* Selecione o filho **EnergyHub** objeto.
* No **painel Inspetor** clique a **adicionar componente** botão.
* No menu, digite na caixa de pesquisa **holograma posicionamento**. Selecione o resultado da pesquisa.
* Salve a cena selecionando **arquivo > Salvar cena**.

**Implantar e aproveitar**
* Criar e implantar para o HoloLens, usando as instruções do capítulo anterior.
* Depois que o aplicativo for iniciado no seu HoloLens, mover sua cabeça e observe como o EnergyHub segue seu foco.
* Observe como o cursor exibido quando você contempla após o holograma e muda para um ponto de luz quando não Observação em um holograma.
* Execute um polegar para colocar o holograma. No momento em nosso projeto, você só pode colocar uma vez o holograma (reimplantação para tentar novamente).

## <a name="chapter-3---shared-coordinates"></a>Coordenadas de capítulo 3 - compartilhado

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

É divertido ver e interagir com hologramas, mas vamos aprofundar. Vamos definir nossa primeira experiência compartilhada - um holograma todos podem ver juntos.

### <a name="objectives"></a>Objetivos

* Configure uma rede para uma experiência compartilhada.
* Estabelecer um ponto de referência comum.
* Compartilhe os sistemas de coordenadas em todos os dispositivos.
* Todos veem o mesmo holograma!

>[!NOTE]
>O **InternetClientServer** e **PrivateNetworkClientServer** recursos devem ser declarados para um aplicativo para se conectar ao servidor de compartilhamento. Isso é feito para que você já no hologramas 240, mas lembre-se para seus próprios projetos.
>1. No Editor do Unity, vá para as configurações de player, navegando até "Editar > projeto Configurações > Player"
>2. Clique na guia "Windows Store"
>3. Na seção "> recursos de publicação configurações", verifique as **InternetClientServer** capacidade e o **PrivateNetworkClientServer** capacidade

### <a name="instructions"></a>Instruções

* No **painel projeto** navegue até a **240\Prefabs\Sharing compartilhamento HoloToolkit** pasta.
* Arraste e solte a **compartilhamento** pré-fabricado para o **painel de hierarquia**.

Em seguida, precisamos iniciar o serviço de compartilhamento. Somente **um único PC** compartilhado experiência precisa realizar esta etapa.
* No Unity - no menu superior - selecione a **240 compartilhamento HoloToolkit menu**.
* Selecione o **inicie o serviço de compartilhamento** item na lista suspensa.
* Verifique as **rede privada** opção e clique em **permitir o acesso** quando aparece o prompt do firewall.
* Anote o endereço IPv4 exibido na janela do console de serviço de compartilhamento. Isso é o mesmo IP da máquina que o serviço está sendo executado.

Siga o restante das instruções em **todos os PCs** que ingressará experiência compartilhada.
* No **hierarquia**, selecione o **Sharing** objeto.
* No **Inspetor**, no **estágio de compartilhamento** componente, altere a **endereço do servidor** do 'localhost' para o endereço IPv4 do computador que executa o SharingService.exe.
* No **hierarquia** selecionar a **HologramCollection** objeto.
* No **Inspector** clique a **adicionar componente** botão.
* Na caixa de pesquisa, digite **importação exportação âncora Manager**. Selecione o resultado da pesquisa.
* No **painel projeto** navegue até a **Scripts** pasta.
* Clique duas vezes o **HologramPlacement** script para abri-lo no Visual Studio.
* Substitua o conteúdo pelo código a seguir.

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

* No Unity, selecione a **HologramCollection** na **painel de hierarquia**.
* No **painel Inspetor** clique a **adicionar componente** botão.
* No menu, digite na caixa de pesquisa **Gerenciador de estado do aplicativo**. Selecione o resultado da pesquisa.

**Implantar e aproveitar**
* Compile o projeto para seus dispositivos do HoloLens.
* Designe um HoloLens implantar primeiro. Você precisará aguardar a âncora ser carregado para o serviço antes de colocar o EnergyHub (Isso pode levar cerca de 30 a 60 segundos). Até que o carregamento for concluído, seu gestos de toque serão ignorados.
* Depois que o EnergyHub foi colocado, sua localização será carregada para o serviço e, em seguida, você pode implantar para todos os outros dispositivos do HoloLens.
* Quando um novo HoloLens primeiro ingressar na sessão, o local do EnergyHub pode não estar correto no dispositivo. No entanto, assim que a âncora e os locais de EnergyHub tiverem sido baixados do serviço, o EnergyHub deve ir para o novo local compartilhado. Se isso não acontece em cerca de 30 a 60 segundos, percorrer para onde o HoloLens original estava ao configurar a âncora para reunir mais dicas de ambiente. Se o local ainda não bloqueia, reimplantar no dispositivo.
* Quando os dispositivos estão todos prontos e executando o aplicativo, procure o EnergyHub. Todos concordam na localização do holograma e a direção na qual o texto está enfrentando?

## <a name="chapter-4---discovery"></a>Capítulo 4 - descoberta

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Agora, todos podem ver o holograma mesmo! Agora vamos ver todos else conectados a nosso mundo holográfico compartilhado. Neste capítulo, podemos irá obter o local principal e a rotação de todos os outros dispositivos do HoloLens na mesma sessão de compartilhamento.

### <a name="objectives"></a>Objetivos

* Descobrir uns aos outros em nossa experiência compartilhada.
* Escolha e compartilhar um avatar player.
* Anexe o avatar do player ao lado de cabeça de todos os usuários.

### <a name="instructions"></a>Instruções

* No **painel projeto** navegue até a **hologramas** pasta.
* Arraste e solte os **PlayerAvatarStore** para o **hierarquia**.
* No **painel projeto** navegue até a **Scripts** pasta.
* Clique duas vezes o **AvatarSelector** script para abri-lo no Visual Studio.
* Substitua o conteúdo pelo código a seguir.

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

* No **hierarquia** selecionar a **HologramCollection** objeto.
* No **Inspector** clique em **adicionar componente**.
* Na caixa de pesquisa, digite **Gerenciador de Player Local**. Selecione o resultado da pesquisa.
* No **hierarquia** selecionar a **HologramCollection** objeto.
* No **Inspector** clique em **adicionar componente**.
* Na caixa de pesquisa, digite **Gerenciador de Player remota**. Selecione o resultado da pesquisa.
* Abra o **HologramPlacement** script no Visual Studio.
* Substitua o conteúdo pelo código a seguir.

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

* Abra o **AppStateManager** script no Visual Studio.
* Substitua o conteúdo pelo código a seguir.

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

**Implantar e aproveitar**
* Criar e implantar o projeto para seus dispositivos do HoloLens.
* Quando você ouve um som de ping, localize o menu de seleção de avatar e selecione um avatar com o gesto de toque de ar.
* Se você não estiver olhando qualquer hologramas, o ponto de luz em torno de seu cursor ativará uma cor diferente quando o HoloLens está se comunicando com o serviço: inicializando (roxo escuro), baixar a âncora (verde), importar/exportar dados de localização (amarelo) Carregando a âncora (azul). Se o ponto de luz em torno de seu cursor é a cor padrão (roxo-claro), em seguida, você está pronto para interagir com outros jogadores na sua sessão!
* Examinar a outras pessoas conectado ao seu espaço - não haverá um robô holográfico flutuante acima seu shoulder e imitando seus movimentos de cabeçalho!

## <a name="chapter-5---placement"></a>Capítulo 5 - posicionamento

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

Neste capítulo, faremos a âncora podem ser posicionados em superfícies do mundo real. Vamos usar coordenadas compartilhadas para colocar essa âncora no ponto médio entre todos conectados a experiência compartilhada.

### <a name="objectives"></a>Objetivos

* Coloque hologramas no mapa espacial com base na posição de cabeçalho dos jogadores.

### <a name="instructions"></a>Instruções

* No **painel projeto** navegue até a **hologramas** pasta.
* Arraste e solte os **CustomSpatialMapping** pré-fabricado até a **hierarquia**.
* No **painel projeto** navegue até a **Scripts** pasta.
* Clique duas vezes o **AppStateManager** script para abri-lo no Visual Studio.
* Substitua o conteúdo pelo código a seguir.

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

* No **painel projeto** navegue até a **Scripts** pasta.
* Clique duas vezes o **HologramPlacement** script para abri-lo no Visual Studio.
* Substitua o conteúdo pelo código a seguir.

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

**Implantar e aproveitar**
* Criar e implantar o projeto para seus dispositivos do HoloLens.
* Quando o aplicativo estiver pronto, coloque em funcionamento em um círculo e observe como o EnergyHub aparece no Centro de todas as pessoas.
* Toque para colocar o EnergyHub.
* Tente o comando de voz 'Redefinir Target' para pegar o EnergyHub e trabalham juntos como um grupo para mover o holograma para um novo local.

## <a name="chapter-6---real-world-physics"></a>Capítulos 6 - física do mundo Real

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

Neste capítulo vamos adicionar hologramas salte nas superfícies do mundo real. Assista ao seu espaço preenchido com projetos iniciados por você e seus amigos!

### <a name="objectives"></a>Objetivos

* Inicie os projéteis salte nas superfícies do mundo real.
* Compartilhe os projéteis para que outros jogadores podem vê-los.

### <a name="instructions"></a>Instruções

* No **hierarquia** selecionar a **HologramCollection** objeto.
* No **Inspector** clique em **adicionar componente**.
* Na caixa de pesquisa, digite **Projectile iniciador**. Selecione o resultado da pesquisa.

**Implantar e aproveitar**
* Compilar e implantar em seus dispositivos do HoloLens.
* Quando o aplicativo está em execução em todos os dispositivos, execute um polegar para iniciar projectile em superfícies do mundo real.
* Veja o que acontece quando sua projectile entra em conflito com o avatar do outro jogador!

## <a name="chapter-7---grand-finale"></a>Capítulo 7 - Grand finale:

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

Neste capítulo, vamos vai descobrir um portal que só pode ser descoberto com a colaboração.

### <a name="objectives"></a>Objetivos

* Trabalham juntos para iniciar o suficiente projéteis à âncora para revelar um portal secreto!

### <a name="instructions"></a>Instruções

* No **painel projeto** navegue até a **hologramas** pasta.
* Arraste e solte os **mundo virtual** ativo como um **filho de HologramCollection**.
* Com **HologramCollection** selecionado, clique no **Add Component** botão no **Inspetor**.
* No menu, digite na caixa de pesquisa **ExplodeTarget**. Selecione o resultado da pesquisa.
* Com **HologramCollection** selecionado, da **hierarquia** arrastar a **EnergyHub** do objeto para o **destino** campo o **Inspector**.
* Com **HologramCollection** selecionado, da **hierarquia** arrastar a **mundo virtual** do objeto para o **mundo virtual** campo o  **Inspetor de**.

**Implantar e aproveitar**
* Compilar e implantar em seus dispositivos do HoloLens.
* Quando o aplicativo for iniciado, colaborem para iniciar os projéteis no EnergyHub.
* Quando aparece o mundo virtual, inicie projéteis nas robôs de mundo virtual (acerto de um robô três vezes por diversão extra).
