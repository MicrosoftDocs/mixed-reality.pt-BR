---
title: Entrada MR 213
description: Siga este tutorial de codificação usando o Unity, o Visual Studio e os headsets de imersão para aprender os detalhes dos controladores de movimento.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, imersiva, controlador de movimento, Academia, tutorial
ms.openlocfilehash: e2199c3afed21f9396ed84f71093a8b2fb3bb23b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438550"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

<br>

# <a name="mr-input-213-motion-controllers"></a>Entrada MR 213: controladores de movimento

Os controladores de movimento no mundo da realidade misturada adicionam outro nível de interatividade. Com os [controladores de movimento](motion-controllers.md), podemos interagir diretamente com objetos de forma mais natural, semelhante às nossas interações físicas na vida real, aumentando imersão e fascinam em sua experiência de aplicativo.

No Sr Input 213, exploraremos os eventos de entrada do controlador de movimento criando uma experiência de pintura espacial simples. Com esse aplicativo, os usuários podem pintar em espaço tridimensional com vários tipos de pincéis e cores.

## <a name="topics-covered-in-this-tutorial"></a>Tópicos abordados neste tutorial

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Visualização do controlador**|**Eventos de entrada do controlador**|**Controlador personalizado e interface do usuário**|
|Saiba como renderizar modelos de controlador de movimento no modo de jogo e em tempo de execução do Unity.|Entenda os diferentes tipos de eventos de botão e seus aplicativos.|Saiba como sobrepor elementos de interface do usuário na parte superior do controlador ou personalizá-lo totalmente.|

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Entrada MR 213: controladores de movimento</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

Consulte a lista de verificação da instalação para headsets de imersão nesta [página](install-the-tools.md).

* Este tutorial requer o [Unity 2017.2.1 P2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>Arquivos de projeto

* [Baixe os arquivos](https://github.com/Microsoft/MixedReality213/archive/master.zip) exigidos pelo projeto e extraia os arquivos para a área de trabalho.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/MixedReality213).

## <a name="unity-setup"></a>Configuração do Unity

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Objetivos

* Otimizar o Unity para o desenvolvimento de realidade mista do Windows
* Configuração da câmera de realidade misturada
* Ambiente de instalação

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **abrir**.
* Navegue até sua área de trabalho e localize a pasta **MixedReality213-Master** que você desarquivou anteriormente.
* Clique em **Selecionar Pasta**.
* Depois que o Unity terminar de carregar arquivos de projeto, você poderá ver o editor do Unity.
* No Unity, selecione **arquivo > configurações de Build**.

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* Selecione **plataforma universal do Windows** na lista **plataforma** e clique no botão **alternar plataforma** .
* Definir o dispositivo de destino para **qualquer dispositivo**
* Definir tipo de compilação como **D3D**
* Definir o SDK para o **mais recente instalado**
* Verificar **projetos C# do Unity**
    * Isso permite que você modifique os arquivos de script no projeto do Visual Studio sem recriar o projeto do Unity.
* Clique em **configurações do Player**.
* No painel **Inspetor** , role para baixo até a parte inferior
* Em configurações de XR, verifique a **realidade virtual com suporte**
* Em SDKs de realidade virtual, selecione **realidade mista do Windows**

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* Feche a janela **configurações de compilação** .

### <a name="project-structure"></a>Estrutura do projeto

Este tutorial usa o **[Kit de ferramentas de realidade misturada-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** . Você pode encontrar as versões nesta [página](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).

![ProjectStructure](images/mr213-projectstructure-650px.png)

**Cenas concluídas para sua referência**

* Você encontrará duas cenas de Unity concluídas na pasta de **cenas** .
    * **MixedReality213**: cena concluída com pincel único
    * **MixedReality213Advanced**: cena concluída para design avançado com vários pincéis

**Nova configuração de cena para o tutorial**

* No Unity, clique em **arquivo > nova cena**
* Excluir a **câmera principal** e a **luz direcional**
* No **painel Projeto**, pesquise e arraste o seguinte pré-fabricados para o painel **hierarquia** :
    * Assets/HoloToolkit/Input/pré-fabricados/**MixedRealityCamera**
    * Ativos/AppPrefabs/**ambiente**

    ![Câmera e ambiente](images/mr213-cameraenvironment-300px.jpg)

* Há duas pré-fabricados de câmera no kit de ferramentas de realidade misturada:
    * **MixedRealityCamera. pré-fabricado**: câmera somente
    * **MixedRealityCameraParent. pré-fabricado**: câmera + Teleportation + limite
    * Neste tutorial, usaremos o **MixedRealityCamera** sem o recurso de Teleportation. Por isso, adicionamos um **ambiente** simples pré-fabricado que contém uma base básica para fazer com que o usuário se sinta à vontade.
    * Para saber mais sobre a teleportabilidade com o **MixedRealityCameraParent**, consulte [design avançado – Teleportation e Locomotion](#advanced-design---teleportation-and-locomotion)

**Configuração do Skybox**

* Clique em **janela > iluminação > configurações**
* Clique no círculo no lado direito do **campo material de Skybox**
* Digite "Gray" e selecione **SkyboxGray** (ativos/AppPrefabs/suporte/materiais/SkyboxGray. passe-partout)

    ![Configurando Skybox](images/mr123-skyboxsetting-400px.jpg)

* Marque a opção **Skybox** para poder ver Skybox gradiente cinza atribuído

    ![Alternar opção Skybox](images/mr213-skyboxcheck-400px.jpg)

* A cena com MixedRealityCamera, ambiente e Skybox cinza terá a seguinte aparência.

    ![Ambiente MixedReality213](images/mr213-environment-600px.jpg)

* Clique em **arquivo > salvar cena como**
* **Salve** sua cena na pasta de cenas com qualquer nome

## <a name="chapter-1---controller-visualization"></a>Capítulo 1-visualização do controlador

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Objetivos

* Saiba como renderizar modelos de controlador de movimento no modo de jogo do Unity e em tempo de execução.

O Windows Mixed Reality fornece um modelo de controlador animado para a visualização do controlador. Há várias abordagens que você pode tomar para a visualização do controlador em seu aplicativo:

* Padrão-usando o controlador padrão sem modificação
* Híbrido-usando o controlador padrão, mas Personalizando alguns de seus elementos ou sobrepondo componentes de interface do usuário
* Substituição-usando seu próprio modelo 3D personalizado para o controlador

Neste capítulo, aprenderemos sobre os exemplos dessas personalizações do controlador.

### <a name="instructions"></a>Instruções

* No painel **projeto** , digite **MotionControllers** na caixa de pesquisa. Você também pode encontrá-lo em assets/HoloToolkit/Input/pré-fabricados/.
* Arraste **MotionControllers** pré-fabricado para o painel **hierarquia** .
* Clique em **MotionControllers** pré-fabricado no painel **hierarquia** .

**MotionControllers pré-fabricado**

**MotionControllers** pré-fabricado tem um script **MotionControllerVisualizer** que fornece os slots para modelos de controlador alternativos. Se você atribuir seus próprios modelos 3D personalizados, como uma mão ou um gumes, e marcar a opção ' sempre usar o modelo alternativo esquerdo/direito ', você os verá em vez do modelo padrão. Usaremos esse slot no capítulo 4 para substituir o modelo do controlador por um pincel.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Sobre**

* No painel **Inspetor** , clique duas vezes em script **MotionControllerVisualizer** para ver o código no Visual Studio

**Script MotionControllerVisualizer**

As classes **MotionControllerVisualizer** e **MotionControllerInfo** fornecem os meios para acessar & modificar os modelos de controlador padrão. **MotionControllerVisualizer** assina o evento **InteractionSourceDetected** do Unity e instancia automaticamente os modelos do controlador quando eles são encontrados.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

Os modelos de controlador são fornecidos de acordo com [a especificação glTF](https://github.com/KhronosGroup/glTF). Esse formato foi criado para fornecer um formato comum, ao mesmo tempo em que melhora o processo por trás da transmissão e desempacotamento de ativos 3D. Nesse caso, precisamos recuperar e carregar os modelos de controlador em tempo de execução, pois queremos tornar a experiência do usuário o mais direta possível e não há garantia de qual versão dos controladores de movimento o usuário pode estar usando. Este curso, por meio do kit de ferramentas de realidade misturada, usa uma versão do [projeto UnityGLTF](https://github.com/KhronosGroup/UnityGLTF)do grupo Khronos.

Depois que o controlador foi entregue, os scripts podem usar o **MotionControllerInfo** para localizar as transformações de elementos específicos do controlador para que eles possam se posicionar corretamente.

Em um capítulo posterior, veremos como usar esses scripts para anexar elementos de interface do usuário aos controladores.

*Em alguns scripts, você encontrará blocos de código com **#if! UNITY_EDITOR** ou **UNITY_WSA**. Esses blocos de código são executados somente no tempo de execução do UWP quando você implanta no Windows. Isso ocorre porque o conjunto de APIs usado pelo editor do Unity e o tempo de execução do aplicativo UWP são diferentes.*

* **Salve** a cena e clique no botão **reproduzir** .

Você poderá ver a cena com os controladores de movimento em seu headset. Você pode ver animações detalhadas para cliques de botão, movimentação de Thumbstick e realce de toque do touchpad.

![Padrão de visualização de MR213_Controller](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Capítulo 2-anexando elementos da interface do usuário ao controlador

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Objetivos

* Saiba mais sobre os elementos dos controladores de movimento
* Saiba como anexar objetos a partes específicas dos controladores

Neste capítulo, você aprenderá a adicionar elementos de interface do usuário ao controlador que o usuário pode acessar e manipular facilmente a qualquer momento. Você também aprenderá a adicionar uma interface do usuário de seletor de cor simples usando a entrada do touchpad.

### <a name="instructions"></a>Instruções

* No painel **projeto** , pesquise o script **MotionControllerInfo** .
* No resultado da pesquisa, clique duas vezes em **MotionControllerInfo** script para ver o código no Visual Studio.

**Script MotionControllerInfo**

A primeira etapa é escolher o elemento do controlador ao qual você deseja que a interface do usuário seja anexada. Esses elementos são definidos em **ControllerElementEnum** em **MotionControllerInfo.cs**.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **Casa**
* **AdicionarMenu**
* **Compreendi**
* **Thumbstick**
* **Não**
* **Touchpad**
* **Pose de ponteiro** – esse elemento representa a ponta da direção do encaminhamento do controlador.

**Sobre**

* No painel **projeto** , pesquise o script **AttachToController** .
* No resultado da pesquisa, clique duas vezes em **AttachToController** script para ver o código no Visual Studio.

**Script AttachToController**

O script **AttachToController** fornece uma maneira simples de anexar quaisquer objetos a um elemento e destro/canhoto do controlador especificado.

Em **AttachElementToController ()** ,

* Confira destromente usando **MotionControllerInfo. destroly**
* Obter um elemento específico do controlador usando **MotionControllerInfo. TryGetElement ()**
* Depois de recuperar a transformação do elemento do modelo do controlador, pai o objeto abaixo dele e definir a posição local do objeto & rotação como zero.

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

A maneira mais simples de usar o script **AttachToController** é herdar dele, como fizemos no caso de **ColorPickerWheel.** Basta substituir as funções **OnAttachToController** e **OnDetatchFromController** para executar sua configuração/divisão quando o controlador for detectado/desconectado.

**Sobre**

* No painel **projeto** , digite na caixa de pesquisa **ColorPickerWheel**. Você também pode encontrá-lo em ativos/AppPrefabs/.
* Arraste **ColorPickerWheel** pré-fabricado para o painel **hierarquia** .
* Clique no **ColorPickerWheel** pré-fabricado no painel **hierarquia** .
* No painel **Inspetor** , clique duas vezes em **ColorPickerWheel** script para ver o código no Visual Studio.

![ColorPickerWheel pré-fabricado](images/mr213-colorpickerwheel-1000px.jpg)

**Script ColorPickerWheel**

Como **ColorPickerWheel** herda **AttachToController**, ele mostra **destroly** e **Element** no painel de **inspetores** . Vamos anexar a interface do usuário ao elemento Touchpad no controlador à esquerda.

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** substitui o **OnAttachToController** e o **OnDetatchFromController** para assinar o evento de entrada que será usado no próximo capítulo para seleção de cores com entrada do touchpad.

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* **Salve** a cena e clique no botão **reproduzir** .

**Método alternativo para anexar objetos aos controladores**

É recomendável que seus scripts herdem de **AttachToController** e substituam **OnAttachToController**. No entanto, isso nem sempre pode ser possível. Uma alternativa é usá-lo como um componente autônomo. Isso pode ser útil quando você deseja anexar um pré-fabricado existente a um controlador sem refatorar seus scripts. Basta ter a sua classe aguardar que isanexou seja definido como true antes de executar qualquer configuração. A maneira mais simples de fazer isso é usando uma corrotina para ' Iniciar '.

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Capítulo 3-trabalhando com entrada do Touchpad

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Objetivos

* Saiba como obter eventos de dados de entrada do Touchpad
* Saiba como usar informações de posição do eixo do Touchpad para sua experiência de aplicativo

### <a name="instructions"></a>Instruções

* No painel **hierarquia** , clique em **ColorPickerWheel**
* No painel **Inspetor** , em **animatior**, clique duas vezes em **ColorPickerWheelController**
* Você poderá ver a guia **Animator** aberta

**Mostrando/ocultando a interface do usuário com o controlador de animação do Unity**

Para mostrar e ocultar a interface do usuário do **amColorPickerWheel** com animação, estamos usando o [sistema de animação do Unity](https://docs.unity3d.com/Manual/AnimationOverview.html). Definir a propriedade **Visible** do **ColorPickerWheel**como true ou false triggers **mostra** e **oculta** os gatilhos de animação. Os parâmetros **show** e **Hide** são definidos no controlador de animação **ColorPickerWheelController** .

![Controlador de animação Unity](images/mr123-animationcontroller-550px.jpg)

**Sobre**

* No painel **hierarquia** , selecione **ColorPickerWheel** pré-fabricado
* No painel **Inspetor** , clique duas vezes em script **ColorPickerWheel** para ver o código no Visual Studio

**Script ColorPickerWheel**

**ColorPickerWheel** assina o evento **InteractionSourceUpdated** do Unity para escutar eventos do touchpad.

Em **InteractionSourceUpdated ()** , o script primeiro verifica se ele:

* é, na verdade, um evento de Touchpad (obj. State. **touchpadTouched**)
* origina-se do controlador à esquerda (obj. State. Source. **destro/canhoto**)

Se ambos forem verdadeiros, a posição do Touchpad (obj. State. **touchpadPosition**) é atribuído a **selectorPosition**.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

Em **Update ()** , com base na propriedade **Visible** , ele dispara mostrar e ocultar gatilhos de animação no componente Animator do seletor de cores

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

Em **Update ()** , **selectorPosition** é usado para converter um raio no Colisor de malha da roda de cores, que retorna uma posição UV. Essa posição pode ser usada para localizar a coordenada de pixel e o valor de cor da textura da roda de cores. Esse valor é acessível a outros scripts por meio da propriedade **SelectedColor** .

![Seletor de cores raycasting de roda](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>Capítulo 4-substituindo modelo de controlador

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Objetivos

* Saiba como substituir o modelo do controlador por um modelo 3D personalizado.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Instruções

* Clique em **MotionControllers** no painel **hierarquia** .
* Clique no círculo no lado direito do campo **controlador alternativo direito** .
* Digite **' BrushController**' e selecione o pré-fabricado do resultado. Você pode encontrá-lo em ativos/AppPrefabs/**BrushController**.
* Marque **sempre usar modelo alternativo correto**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

O **BrushController** pré-fabricado não precisa ser incluído no painel **hierarquia** . No entanto, para conferir seus componentes filho:

* No painel **projeto** , digite **BrushController** e arraste **BrushController** pré-fabricado para o painel **hierarquia** .

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Você encontrará o componente de **dica** em **BrushController**. Usaremos sua transformação para iniciar/parar as linhas de desenho.

* Exclua o **BrushController** do painel **hierarquia** .
* **Salve** a cena e clique no botão **reproduzir** . Você poderá ver o modelo de pincel substituiu o controlador de movimento à direita.

## <a name="chapter-5---painting-with-select-input"></a>Capítulo 5-pintura com selecionar entrada

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Objetivos

* Saiba como usar o evento de botão SELECT para iniciar e parar um desenho de linha

### <a name="instructions"></a>Instruções

* Pesquise **BrushController** pré-fabricado no painel de **projeto** .
* No painel **Inspetor** , clique duas vezes em script **BrushController** para ver o código no Visual Studio

**Script BrushController**

**BrushController** assina os eventos **InteractionSourcePressed** e **InteractionSourceReleased** de interactionmanager. Quando o evento **InteractionSourcePressed** é disparado, a propriedade **draw** do pincel é definida como true; Quando o evento **InteractionSourceReleased** é disparado, a propriedade **draw** do pincel é definida como false.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

Enquanto **draw** estiver definido como true, o pincel gerará pontos em um **LineRenderer**de Unity instanciado. Uma referência a esse pré-fabricado é mantida no campo de **pré-fabricado de traço** do pincel.

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

Para usar a cor atualmente selecionada na interface do usuário da roda do seletor de cores, **BrushController** precisa ter uma referência ao objeto **ColorPickerWheel** . Como o **BrushController** pré-fabricado é instanciado em tempo de execução como um controlador de substituição, todas as referências a objetos na cena precisarão ser definidas em tempo de execução. Nesse caso, usamos **gameobject. FindObjectOfType** para localizar o **ColorPickerWheel**:

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* **Salve** a cena e clique no botão **reproduzir** . Você poderá desenhar as linhas e pintar usando o botão Selecionar no controlador à direita.

## <a name="chapter-6---object-spawning-with-select-input"></a>Capítulo 6-gerando objeto com a entrada SELECT

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Objetivos

* Saiba como usar os eventos de entrada do botão Selecionar e entender
* Saiba como criar uma instância de objetos

### <a name="instructions"></a>Instruções

* No painel **projeto** , digite **objectgerador** na caixa de pesquisa. Você também pode encontrá-lo em ativos/AppPrefabs/
* Arraste o **Objectgerador** pré-fabricado para o painel **hierarquia** .
* Clique em **Objectgerador** no painel **hierarquia** .
* **Objectgerador** tem um campo denominado **fonte de cores**.
* No painel **hierarquia** , arraste a referência **ColorPickerWheel** para esse campo.

    ![Inspetor de objeto](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* Clique no pré-fabricado do **Objectgerador** no painel **hierarquia** .
* No painel **Inspetor** , clique duas vezes em script de **objectgerador** para ver o código no Visual Studio.

**Script objectgerador**

O **Objectgerador** instancia cópias de uma malha primitiva (cubo, esfera, cilindro) para o espaço. Quando um **InteractionSourcePressed** é detectado, ele verifica a destro/canhoto e, se for um evento **InteractionSourcePressType. Segure** ou **InteractionSourcePressType. Select** .

Para um evento **Segure** , ele incrementa o índice do tipo de malha atual (Sphere, Cube, cilindro)

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

Para um evento **Select** , em CodeObject **()** , um novo objeto é instanciado, não pai e liberado no mundo.

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

O **Objectgerador** usa o **ColorPickerWheel** para definir a cor do material do objeto de exibição. Os objetos gerados recebem uma instância desse material para que eles retenham sua cor.

* **Salve** a cena e clique no botão **reproduzir** .

Você poderá alterar os objetos com o botão compreender e gerar objetos com o botão Selecionar.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Criar e implantar o aplicativo no portal de realidade misturada

* No Unity, selecione **arquivo > configurações de Build**.
* Clique em **Adicionar abrir cenas** para adicionar a cena atual às **cenas na compilação**.
* Clique em **Compilar**.
* Crie uma **nova pasta** chamada "app".
* Clique uma vez na pasta do **aplicativo** .
* Clique em **Selecionar Pasta**.
* Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.
* Abra a pasta do **aplicativo** .
* Clique duas vezes em arquivo de solução do Visual Studio **YourSceneName. sln** .
* Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x64**.
* Clique na seta suspensa ao lado do botão dispositivo e selecione **computador local**.
* Clique em **depurar-> iniciar sem Depurar** no menu ou pressione **Ctrl + F5**.

Agora, o aplicativo é criado e instalado no portal de realidade misturada. Você pode iniciá-lo novamente por meio do menu iniciar no portal de realidade misturada.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Design avançado – ferramentas de pincel com layout radial

![MixedReality213 principal](images/mr213-main-600px.jpg)

Neste capítulo, você aprenderá a substituir o modelo de controlador de movimento padrão por uma coleção de ferramentas de pincel personalizada. Para sua referência, você pode encontrar o **MixedReality213Advanced** de cena concluído na pasta de **cenas** .

### <a name="instructions"></a>Instruções

* No painel **projeto** , digite **BrushSelector** na caixa de pesquisa. Você também pode encontrá-lo em ativos/AppPrefabs/
* Arraste **BrushSelector** pré-fabricado para o painel **hierarquia** .
* Para a organização, crie um gameobject vazio chamado **pincéis**
* Arraste o pré-fabricados a seguir do painel de **projeto** para **pincéis**
    * Ativos/AppPrefabs/**BrushFat**
    * Ativos/AppPrefabs/**BrushThin**
    * Ativos/AppPrefabs/**borracha**
    * Ativos/AppPrefabs/**MarkerFat**
    * Ativos/AppPrefabs/**MarkerThin**
    * Ativos/AppPrefabs/**lápis**

    ![Pincéis](images/mixedreality213-brushes-250px.png)

* Clique em **MotionControllers** pré-fabricado no painel **hierarquia** .
* No painel **Inspetor** , desmarque **sempre usar o modelo alternativo à direita** no **Visualizador do controlador de movimento**
* No painel **hierarquia** , clique em **BrushSelector**
* **BrushSelector** tem um campo chamado **ColorPicker**
* No painel **hierarquia** , arraste o **ColorPickerWheel** para o campo **ColorPicker** no painel **Inspetor** .

    ![Atribuir ColorPickerWheel ao seletor de pincel](images/mr213-brushselector-500px.jpg)

* No painel **hierarquia** , em **BrushSelector** pré-fabricado, selecione o objeto de **menu** .
* No painel **Inspetor** , no componente **LineObjectCollection** , abra a lista suspensa **objetos** matriz. Você verá seis slots vazios.
* No painel **hierarquia** , arraste cada um dos pré-fabricados pais sob os **pincéis** gameobject nesses slots em qualquer ordem. (Certifique-se de que você está arrastando o pré-fabricados da cena, não o pré-fabricados na pasta do projeto.)

![Seletor de pincel](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector pré-fabricado**

Como o **BrushSelector** herda **AttachToController**, ele mostra opções de **redireção** e **elemento** no painel **Inspetor** . Selecionamos **direita** e **apontando** para a pose para anexar ferramentas de pincel ao controlador à direita com direção de encaminhamento.

O **BrushSelector** usa dois utilitários:

* **Ellipse**: usada para gerar pontos no espaço ao longo de uma forma Ellipse.
* **LineObjectCollection**: distribui objetos usando os pontos gerados por qualquer classe de linha (por exemplo, Ellipse). Isso é o que usaremos para colocar nossos pincéis ao longo da forma de elipse.

Quando combinados, esses utilitários podem ser usados para criar um menu radial.

**Script LineObjectCollection**

**LineObjectCollection** tem controles para o tamanho, a posição e a rotação de objetos distribuídos ao longo de sua linha. Isso é útil para criar menus radiais como o seletor de pincel. Para criar a aparência de pincéis que se expandem de nada à medida que eles se aproximam da posição selecionada central, os picos de curva de **objectscale** no centro e nas fitas são desativados nas bordas.

**Script BrushSelector**

No caso do **BrushSelector**, optamos por usar a animação de procedimento. Primeiro, os modelos de pincel são distribuídos em uma elipse pelo script **LineObjectCollection** . Em seguida, cada pincel é responsável por manter sua posição na mão do usuário com base em seu valor de **DisplayMode** , que é alterado com base na seleção. Escolhemos uma abordagem de procedimento devido à alta probabilidade de transições de posição de pincel serem interrompidas à medida que o usuário seleciona pincéis. As animações Mecanim podem lidar com as interrupções normalmente, mas tendem a ser mais complicadas do que uma operação simples de Lerp.

**BrushSelector** usa uma combinação de ambos. Quando a entrada do Touchpad é detectada, as opções de pincel tornam-se visíveis e escaladas para cima ao longo do menu radial. Após um período de tempo limite (que indica que o usuário fez uma seleção), as opções de pincel são reduzidas novamente, deixando apenas o pincel selecionado.

**Visualizando entrada do Touchpad**

Mesmo nos casos em que o modelo do controlador foi completamente substituído, pode ser útil mostrar a entrada nas entradas do modelo original. Isso ajuda a aterrar as ações do usuário na realidade. Para o **BrushSelector** , escolhemos tornar o touchpad visível brevemente quando a entrada é recebida. Isso foi feito recuperando o elemento Touchpad do controlador, substituindo seu material por um material personalizado e aplicando um gradiente à cor desse material com base na última vez que a entrada do Touchpad foi recebida.

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**Seleção da ferramenta pincel com entrada do Touchpad**

Quando o seletor de pincel detecta a entrada pressionada do Touchpad, ele verifica a posição da entrada para determinar se ela foi à esquerda ou à direita.

**Espessura do traço com selectPressedAmount**

Em vez do evento **InteractionSourcePressType. Select** no **InteractionSourcePressed ()** , você pode obter o valor analógico do valor pressionado por meio de **selectPressedAmount**. Esse valor pode ser recuperado em **InteractionSourceUpdated ()** .

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**Script de borracha**

**Borracha** é um tipo especial de pincel que substitui a função **DrawOverTime ()** do **pincel**de base. Embora Draw seja true, o apagador verifica se a sua gorjeta está interseccionada com qualquer traçado de pincel existente. Em caso afirmativo, eles são adicionados a uma fila para serem reduzidos e excluídos.

## <a name="advanced-design---teleportation-and-locomotion"></a>Design avançado – portabilidade e Locomotion

Se você quiser permitir que o usuário se mova pela cena com a Teleportation usando Thumbstick, use **MixedRealityCameraParent** em vez de **MixedRealityCamera**. Você também precisa adicionar **InputManager** e **DefaultCusor**. Como **o MixedRealityCameraParent** já inclui **MotionControllers** e **limite** como componentes filho, você deve remover o **MotionControllers** existente e o **ambiente** pré-fabricado.

### <a name="instructions"></a>Instruções

* No painel **hierarquia** , exclua **MixedRealityCamera**, **Environment** e **MotionControllers**
* No **painel Projeto**, pesquise e arraste o seguinte pré-fabricados para o painel **hierarquia** :
    * Assets/AppPrefabs/Input/pré-fabricados/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/pré-fabricados/**InputManager**
    * Ativos/AppPrefabs/entrada/pré-fabricados/cursor/**DefaultCursor**

    ![Pai da câmera de realidade misturada](images/mr213-cameraparent-300px.png)

* No painel **hierarquia** , clique em **Gerenciador de entrada**
* No painel **Inspetor** , role para baixo até a seção **simples do seletor de ponteiro único**
* No painel **hierarquia** , arraste **DefaultCursor** para o campo **cursor**

    ![Atribuindo DefaultCursor](images/mr213-defaultcursor-500px.png)

* **Salve** a cena e clique no botão **reproduzir** . Você poderá usar o Thumbstick para girar para a esquerda/direita ou teleport.

## <a name="the-end"></a>Fim

E esse é o fim deste tutorial! Você aprendeu:

* Como trabalhar com modelos de controlador de movimento no modo de jogo e no tempo de execução do Unity.
* Como usar diferentes tipos de eventos de botão e seus aplicativos.
* Como sobrepor elementos de interface do usuário na parte superior do controlador ou personalizá-lo totalmente.

Agora você está pronto para começar a criar sua própria experiência de imersão com os controladores de movimento!

## <a name="completed-scenes"></a>Cenas concluídas

* No painel de **projeto** do Unity, clique na pasta **cenas** .
* Você encontrará dois Unity sceens **MixedReality213** e **MixedReality213Advanced**.
    * **MixedReality213**: cena concluída com pincel único
    * **MixedReality213Advanced**: cena concluída com vários Brushes com o exemplo de valor de pressionar do botão Selecionar

## <a name="see-also"></a>Consulte também

* [Arquivos de projeto 213 de entrada do MR](https://github.com/Microsoft/MixedReality213)
* [Kit de ferramentas de realidade misturada – cena de teste do controlador de movimento](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Kit de ferramentas de realidade misturada-capturar mecânica](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Diretrizes de desenvolvimento do controlador de movimento](motion-controllers.md)
