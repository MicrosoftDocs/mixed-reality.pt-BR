---
title: Entrada MR 213
description: Siga este tutorial de codificação usando o Unity, o Visual Studio e fones imersivos em exposição para saber os detalhes dos controladores de movimento.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, imersivo, controlador, academy, tutorial de movimento
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590940"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-input-213-motion-controllers"></a>Entrada MR 213: Controladores de movimento

Controladores de movimento do mundo de realidade misturada adicionam outro nível de interatividade. Com o [controladores de movimento](motion-controllers.md), podemos diretamente interagir com objetos de forma mais natural, semelhante às nossas interações físicas na vida real, aumentando a imersão e gostar de sua experiência de aplicativo.

MR 213 de entrada, vamos explorar eventos de entrada do controlador de movimento, criando uma experiência de pintura espacial simples. Com este aplicativo, os usuários podem pintar no espaço tridimensional com diversos tipos de pincéis e cores.

## <a name="topics-covered-in-this-tutorial"></a>Tópicos abordados neste tutorial

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Visualização do controlador**|**Eventos de entrada do controlador**|**Controlador personalizado e a interface do usuário**|
|Saiba como processar modelos de controlador de animação no modo de jogo do Unity e o tempo de execução.|Entenda os diferentes tipos de eventos do botão e seus aplicativos.|Aprenda a sobreposição de elementos de interface do usuário sobre o controlador ou totalmente personalizá-lo.|

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td>Entrada MR 213: Controladores de movimento</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

Consulte a lista de verificação de instalação para fones imersivos em exposição no [nesta página](install-the-tools.md).

* Este tutorial requer [2017.2.1p2 do Unity](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>Arquivos de projeto

* [Baixar os arquivos](https://github.com/Microsoft/MixedReality213/archive/master.zip) exigidos pelo projeto e extraia os arquivos na área de trabalho.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/MixedReality213).

## <a name="unity-setup"></a>Instalação do Unity

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Objetivos

* Otimizar o desenvolvimento do Unity para Windows Mixed Reality
* Câmera de realidade misturada da instalação
* Ambiente de configuração

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **aberto**.
* Navegue até a área de trabalho e localizar o **MixedReality213 mestre** pasta você anteriormente não arquivados.
* Clique em **Selecionar Pasta**.
* Depois que o Unity termina de carregar arquivos de projeto, você poderá ver o editor do Unity.
* No Unity, selecione **arquivo > configurações de Build**.

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* Selecione **plataforma Universal do Windows** na **plataforma** lista e clique no **alternar plataforma** botão.
* Defina o dispositivo de destino **qualquer dispositivo**
* Defina o tipo de compilação como **D3D**
* Defina o SDK **mais recente instalada**
* Verifique **Unity C# projetos**
    * Isso permite que você modifique os arquivos de script no projeto do Visual Studio sem recompilar o projeto do Unity.
* Clique em **configurações do Player**.
* No **Inspetor** painel, role para baixo até a parte inferior
* Nas configurações de XR verificar **suporte de realidade Virtual**
* Em SDKs de realidade Virtual, selecione **realidade mista do Windows**

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* Fechar **configurações de Build** janela.

### <a name="project-structure"></a>Estrutura do projeto

Este tutorial usa  **[Toolkit de realidade misturada - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**. Você pode encontrar as versões na [nesta página](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).

![ProjectStructure](images/mr213-projectstructure-650px.png)

**Concluído nos bastidores para sua referência**
* Você encontrará duas cenas concluídas do Unity sob **cenas** pasta.
    * **MixedReality213**: Cena concluída com pincel único
    * **MixedReality213Advanced**: Concluída a cena para design avançado com vários pincéis

**Nova configuração de cena para o tutorial**
* No Unity, clique em **arquivo > Nova cena**
* Exclua **câmera principal** e **luz direcional**
* Do **painel projeto**, a pesquisa e arraste os seguintes pré-fabricados para o **hierarquia** painel:
    * Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * Assets/AppPrefabs/**Environment**

![Câmera e ambiente](images/mr213-cameraenvironment-300px.jpg)
* Há dois pré-fabricados câmera no Kit de ferramentas de realidade mista:
    * **MixedRealityCamera.prefab**: Somente a câmera
    * **MixedRealityCameraParent.prefab**: Câmera + Teleportation + limites
    * Neste tutorial, usaremos **MixedRealityCamera** sem teleportation recurso. Por isso, adicionamos simples **ambiente** pré-fabricado que contém um piso básico para fazer com que o usuário sentir com aterramento.
    * Para saber mais sobre o teleportation com **MixedRealityCameraParent**, consulte [avançadas de design - Teleportation e locomotion](#advanced-design---teleportation-and-locomotion)

**Instalação de skybox**
* Clique em **Janela > iluminação > configurações**
* Clique no círculo no lado direito do **campo Skybox Material**
* Digite 'cinza' e selecione **SkyboxGray**

(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)

![Definindo skybox](images/mr123-skyboxsetting-400px.jpg)
* Verifique **Skybox** permite que você poderá ver atribuído skybox gradação de cinza

![Ativar/desativar opção de skybox](images/mr213-skyboxcheck-400px.jpg)
* A cena com MixedRealityCamera, ambiente e cinza skybox terá esta aparência.

![Ambiente MixedReality213](images/mr213-environment-600px.jpg)
* Clique em **arquivo > Salvar cena como**
* **Salvar** sua cena na pasta de cenas com qualquer nome

## <a name="chapter-1---controller-visualization"></a>Capítulo 1 - visualização do controlador

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Objetivos

* Saiba como processar modelos de controlador no modo de jogo do Unity e em tempo de execução de movimento.

Realidade mista do Windows fornece um modelo de controlador animado para visualização do controlador. Há várias abordagens que você pode adotar para visualização do controlador em seu aplicativo:
* Padrão - usando o controlador padrão sem modificação
* Hybrid - usando padrão de controlador, mas personalizando alguns de seus elementos ou sobreposição de componentes de interface do usuário
* Substituição - usando seu próprio personalizado a modelo 3D para o controlador

Neste capítulo, podemos aprenderá sobre os exemplos dessas personalizações de controlador.

### <a name="instructions"></a>Instruções

* No **Project** do painel, digite **MotionControllers** na caixa de pesquisa. Você também pode encontrá-la em ativos/HoloToolkit/entrada/pré-fabricados /.
* Arraste o **MotionControllers** pré-fabricado para o **hierarquia** painel.
* Clique no **MotionControllers** pré-fabricado na **hierarquia** painel.

**MotionControllers pré-fabricado**

**MotionControllers** pré-fabricado tem uma **MotionControllerVisualizer** script que fornece os slots para modelos de controlador alternativo. Se você atribuir seus próprios modelos personalizados 3D como uma mão ou uma gumes e marque 'Sempre usar alternativo esquerda/direita Model', você verá em vez do modelo padrão. Usaremos esse slot no capítulo 4 para substituir o modelo de controlador com um pincel.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Instruções**
* No **Inspector** do painel, clique duas vezes **MotionControllerVisualizer** script para ver o código no Visual Studio

**Script MotionControllerVisualizer**

O **MotionControllerVisualizer** e **MotionControllerInfo** classes fornecem os meios para acessar e modificar os modelos de controlador padrão. **MotionControllerVisualizer** assina do Unity **InteractionSourceDetected** eventos e automaticamente cria uma instância de modelos de controlador quando eles forem encontrados.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

Os modelos de controlador são entregues de acordo com a [a especificação de glTF](https://github.com/KhronosGroup/glTF). Esse formato foi criado para fornecer um formato comum, melhorando o processo por trás de transmissão e desempacotar os ativos 3D. Nesse caso, é necessário recuperar e carregar os modelos de controlador no tempo de execução, pois queremos fazer o experiência do usuário mais simples possível, e não tem garantia de qual versão dos controladores de movimento que o usuário pode estar usando. Neste curso, via o Kit de ferramentas de realidade misturada, usa uma versão do grupo de Khronos [UnityGLTF projeto](https://github.com/KhronosGroup/UnityGLTF).

Depois que o controlador foi entregue, os scripts podem usar **MotionControllerInfo** para localizar as transformações para elementos do controlador específico para que eles posicionam corretamente por conta própria.

Um capítulo posterior, aprenderemos a usar esses scripts para anexar os elementos de interface do usuário para os controladores.

*Em alguns scripts, você encontrará blocos de código com **#if! UNITY_EDITOR** ou **UNITY_WSA**. Esses blocos de código executadas somente em tempo de execução do UWP quando você implanta no Windows. Isso ocorre porque o conjunto de APIs usados pelo editor do Unity e o tempo de execução do aplicativo UWP são diferentes.*
* **Salve** a cena e clique em de **reproduzir** botão.

Você será capaz de ver a cena com controladores de movimento em fone de ouvido. Você pode ver as animações detalhadas para cliques de botão direcional movimentação e touchpad realce de toque.

![MR213_Controller visualização padrão](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Capítulo 2 – anexar elementos de interface do usuário para o controlador

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Objetivos

* Saiba mais sobre os elementos dos controladores de movimento
* Saiba como anexar objetos para partes específicas de controladores

Neste capítulo, você aprenderá como adicionar elementos da interface do usuário para o controlador que o usuário pode facilmente acessar e manipular a qualquer momento no. Você também aprenderá como adicionar um selecionador de cores simples da interface do usuário usando o touchpad de entrada.

### <a name="instructions"></a>Instruções

* No **Project** do painel, pesquise **MotionControllerInfo** script.
* Os resultados de pesquisa, clique duas vezes **MotionControllerInfo** script para ver o código no Visual Studio.

**Script MotionControllerInfo**

A primeira etapa é escolher qual elemento do controlador que você deseja anexar a interface do usuário. Esses elementos são definidos no **ControllerElementEnum** na **MotionControllerInfo.cs**.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* **Casa**
* **Menu**
* **Grasp**
* **Thumbstick**
* **Select**
* **Touchpad**
* **Apontador pose** – este elemento representa a dica do controlador que aponta para a direção de avanço.

**Instruções**
* No **Project** do painel, pesquise **AttachToController** script.
* Os resultados de pesquisa, clique duas vezes **AttachToController** script para ver o código no Visual Studio.

**Script AttachToController**

O **AttachToController** script fornece uma maneira simples de todos os objetos se conectar a um destro/canhoto do controlador especificado e o elemento.

In **AttachElementToController()**,
* Verificar o uso de destro/canhoto **MotionControllerInfo.Handedness**
* Obter o elemento específico de controlador usando **MotionControllerInfo.TryGetElement()**
* Depois de recuperar o elemento transformar a partir do modelo de controlador, o objeto sob ele pai e defina a posição local e a rotação do objeto como zero.

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

A maneira mais simples de usar **AttachToController** script é herdar dele, assim como fizemos no caso de **ColorPickerWheel.** Basta substituir a **OnAttachToController** e **OnDetatchFromController** funções para executar a instalação / divisão quando o controlador é detectado / desconectado.

**Instruções**
* No **Project** do painel, digite na caixa de pesquisa **ColorPickerWheel**. Você também pode encontrá-la em ativos/AppPrefabs /.
* Arraste **ColorPickerWheel** pré-fabricado para o **hierarquia** painel.
* Clique o **ColorPickerWheel** pré-fabricado na **hierarquia** painel.
* No **Inspector** do painel, clique duas vezes **ColorPickerWheel** Script para ver o código no Visual Studio.

![ColorPickerWheel pré-fabricado](images/mr213-colorpickerwheel-1000px.jpg)

**Script ColorPickerWheel**

Uma vez que **ColorPickerWheel** herda **AttachToController**, ele mostra **destro/canhoto** e **elemento** no  **Inspetor de** painel. Podemos anexará a interface do usuário para o elemento Touchpad no controlador à esquerda.

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** substitui o **OnAttachToController** e **OnDetatchFromController** para assinar o evento de entrada que será usado no próximo capítulo para seleção de cores com touchpad de entrada.

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
* **Salve** a cena e clique em de **reproduzir** botão.

**Método alternativo para anexar objetos para os controladores**

Recomendamos que seus scripts herdam **AttachToController** e substituir **OnAttachToController**. No entanto, isso talvez nem sempre seja possível. Uma alternativa é usá-lo como um componente autônomo. Isso pode ser útil quando você deseja anexar um pré-fabricado existente a um controlador sem refatoração seus scripts. Simplesmente faça a sua classe aguardar IsAttached ser definido como verdadeiro antes de executar qualquer programa de instalação. A maneira mais simples de fazer isso é por meio de uma corrotina para 'Start'.

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Capítulo 3 – trabalhando com entrada touchpad

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Objetivos

* Saiba como obter eventos de dados de entrada touchpad
* Saiba como usar informações de posição do eixo touchpad para a sua experiência de aplicativo

### <a name="instructions"></a>Instruções

* No **hierarquia** do painel, clique em **ColorPickerWheel**
* No **Inspector** do painel, em **Animatior**, clique duas vezes em **ColorPickerWheelController**
* Você será capaz de ver **Animator** guia aberta

**Mostrar/ocultar a interface de usuário com o controlador de animação do Unity**

Para mostrar e ocultar os **ColorPickerWheel** interface do usuário com a animação, estamos usando [sistema de animação do Unity](https://docs.unity3d.com/Manual/AnimationOverview.html). Definindo o **ColorPickerWheel**do **Visible** propriedade como true ou falsos gatilhos **Mostrar** e **ocultar** disparadores de animação. **Mostrar** e **ocultar** os parâmetros são definidos na **ColorPickerWheelController** controlador de animação.

![Controlador de animação do Unity](images/mr123-animationcontroller-550px.jpg)

**Instruções**
* No **hierarquia** painel, selecione **ColorPickerWheel** pré-fabricado
* No **Inspector** do painel, clique duas vezes **ColorPickerWheel** script para ver o código no Visual Studio

**Script ColorPickerWheel**

**ColorPickerWheel** assina do Unity **InteractionSourceUpdated** eventos para escutar eventos de teclado sensível ao toque.

Na **InteractionSourceUpdated()**, o script primeiro verifica para garantir que ele:
* é, na verdade, um evento touchpad (obj.state. **touchpadTouched**)
* o controlador esquerdo se origina (obj.state.source. **destro/canhoto**)

Se ambos forem verdadeiros, o touchpad posicionar (obj.state. **touchpadPosition**) é atribuído a **selectorPosition**.

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

Na **Update ()**, com base nas **visíveis** propriedade, ele dispara mostrar e ocultar gatilhos de animação no componente animator do seletor de cor

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

Na **Update ()**, **selectorPosition** é usado para converter um raio em colisor de malha da roda de cores, que retorna uma posição UV. Nessa posição, em seguida, pode ser usada para localizar a coordenada de pixel e valor de textura do círculo de cores de cor. Esse valor é acessível para outros scripts por meio de **SelectedColor** propriedade.

![Raycasting de roda de seletor de cor](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a>Capítulo 4 - modelo do controlador de substituição

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Objetivos

* Saiba como substituir o modelo de controlador com um modelo 3D personalizado.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Instruções

* Clique em **MotionControllers** na **hierarquia** painel.
* Clique no círculo no lado direito do **controlador da direita alternativo** campo.
* Digite **' BrushController**' e selecione pré-fabricado do resultado. Você pode encontrá-la no ativos/AppPrefabs/**BrushController**.
* Verificar **sempre usam o modelo certo alternativo**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

O **BrushController** pré-fabricado não precisa ser incluído na **hierarquia** painel. No entanto, fazer check-out de seus componentes filho:
* No **Project** do painel, digite **BrushController** e arraste **BrushController** pré-fabricado no **hierarquia** painel.

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Você encontrará a **dica** componente **BrushController**. Nós usaremos sua transformação para iniciar/parar de desenhar linhas.
* Excluir o **BrushController** da **hierarquia** painel.
* **Salve** a cena e clique em de **reproduzir** botão. Você será capaz de ver que o modelo do pincel substituído o controlador de movimento à direita.

## <a name="chapter-5---painting-with-select-input"></a>Capítulo 5 - entrada de pintura com Select

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Objetivos

* Saiba como usar o evento do botão de seleção para iniciar e parar um desenho de linha

### <a name="instructions"></a>Instruções

* Pesquisa **BrushController** pré-fabricado na **projeto** painel.
* No **Inspector** do painel, clique duas vezes **BrushController** Script para ver o código no Visual Studio

**Script BrushController**

**BrushController** assina o InteractionManager **InteractionSourcePressed** e **InteractionSourceReleased** eventos. Quando **InteractionSourcePressed** evento é disparado, o pincel **desenhar** estiver definida como true; quando **InteractionSourceReleased** evento é disparado, o pincel **Desenhar** propriedade é definida como false.

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

Embora **desenhar** é definido como true, o pincel gerarão os pontos em uma Unity instanciada **LineRenderer**. Uma referência a esse pré-fabricado é mantida no pincel **traço pré-fabricado** campo.

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

Para usar a cor atualmente selecionada do disco de seletor de cores da interface do usuário, **BrushController** precisa ter uma referência para o **ColorPickerWheel** objeto. Porque o **BrushController** pré-fabricado é instanciado em tempo de execução como um controlador de substituição, todas as referências a objetos na cena precisará ser definida em tempo de execução. Nesse caso, usamos **gameobject. Findobjectoftype** para localizar o **ColorPickerWheel**:

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
* **Salve** a cena e clique em de **reproduzir** botão. Você poderá desenhar as linhas e pintar usando o botão de seleção no controlador do lado direito.

## <a name="chapter-6---object-spawning-with-select-input"></a>Capítulo 6 - geração de objeto com Select de entrada

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Objetivos

* Saiba como usar Select e compreender os eventos de entrada de botão
* Saiba como criar uma instância de objetos

### <a name="instructions"></a>Instruções

* No **Project** do painel, digite **ObjectSpawner** na caixa de pesquisa. Você também pode encontrá-la em ativos/AppPrefabs /
* Arraste o **ObjectSpawner** pré-fabricado para o **hierarquia** painel.
* Clique em **ObjectSpawner** na **hierarquia** painel.
* **ObjectSpawner** tem um campo nomeado **cor fonte**.
* Dos **hierarquia** do painel, arraste o **ColorPickerWheel** referência neste campo.

![Inspetor de Spawner de objetos](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* Clique o **ObjectSpawner** pré-fabricado na **hierarquia** painel.
* No **Inspector** do painel, clique duas vezes **ObjectSpawner** Script para ver o código no Visual Studio.

**Script ObjectSpawner**

O **ObjectSpawner** cria uma instância de cópias de uma malha primitiva (cubo, esfera, cilindro) para o espaço. Quando um **InteractionSourcePressed** for detectado, ele verifica a direção e se é um **InteractionSourcePressType.Grasp** ou **InteractionSourcePressType.Select** evento.

Para um **segure** evento, ele incrementa o índice do tipo atual de malha (esfera, cubo, cilindro)

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

Para um **selecionar** evento, na **SpawnObject()**, um novo objeto é instanciado, não parented e liberados para o mundo.

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

O **ObjectSpawner** usa o **ColorPickerWheel** para definir a cor do material do objeto de exibição. Objetos gerados recebem uma instância deste material para que ele manterá sua cor.
* **Salve** a cena e clique em de **reproduzir** botão.

Você poderá alterar os objetos com o botão de compreensão e gerar objetos com o botão de seleção.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Criar e implantar o aplicativo no Portal de realidade mista
* No Unity, selecione **arquivo > configurações de Build**.
* Clique em **adicionar cenas aberto** para adicionar a cena atual para o **cenas em compilação**.
* Clique em **Compilar**.
* Criar uma **nova pasta** chamado "App".
* Único clique a **aplicativo** pasta.
* Clique em **Selecionar Pasta**.
* Quando Unity é feito, será exibida uma janela do Explorador de arquivos.
* Abra o **aplicativo** pasta.
* Clique duas vezes **YourSceneName.sln** arquivo de solução do Visual Studio.
* Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **X64**.
* Clique na seta suspensa ao lado do botão de dispositivo e selecione **computador Local**.
* Clique em **Depurar -> Iniciar sem depuração** na barra de menus ou pressione **Ctrl + F5**.

Agora o aplicativo é criado e instalado no Portal de realidade mista. Você pode iniciá-lo novamente por meio do menu Iniciar no Portal de realidade mista.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Design avançado - ferramentas Pincel com layout radial

![MixedReality213 principal](images/mr213-main-600px.jpg)

Neste capítulo, você aprenderá como substituir o modelo de controlador de movimento padrão com um conjunto de ferramentas Pincel personalizado. Para referência, você pode encontrar a cena concluída **MixedReality213Advanced** sob **cenas** pasta.

### <a name="instructions"></a>Instruções

* No **Project** do painel, digite **BrushSelector** na caixa de pesquisa. Você também pode encontrá-la em ativos/AppPrefabs /
* Arraste o **BrushSelector** pré-fabricado para o **hierarquia** painel.
* Para a organização, criar um GameObject vazio chamado **pincéis**
* Arraste as seguir pré-fabricados do **Project** do painel em **pincéis**
    * Assets/AppPrefabs/**BrushFat**
    * Assets/AppPrefabs/**BrushThin**
    * Assets/AppPrefabs/**Eraser**
    * Assets/AppPrefabs/**MarkerFat**
    * Assets/AppPrefabs/**MarkerThin**
    * Assets/AppPrefabs/**Pencil**

![Pincéis](images/mixedreality213-brushes-250px.png)
* Clique em **MotionControllers** pré-fabricado na **hierarquia** painel.
* No **Inspector** do painel, desmarque a opção **sempre usar alternativas à direita o modelo de** no **Visualizador do controlador de movimento**
* No **hierarquia** do painel, clique em **BrushSelector**
* **BrushSelector** tem um campo chamado **ColorPicker**
* Do **hierarquia** do painel, arraste o **ColorPickerWheel** em **ColorPicker** campo o **Inspetor** painel.

![Atribuir ColorPickerWheel ao seletor de pincel](images/mr213-brushselector-500px.jpg)
* No **hierarquia** do painel, em **BrushSelector** pré-fabricado, selecione o **Menu** objeto.
* No **Inspector** do painel, na **LineObjectCollection** componente, abra o **objetos** lista suspensa de matriz. Você verá 6 slots vazios.
* Dos **hierarquia** do painel, arraste cada um as pai em pré-fabricados a **pincéis** GameObject nestes slots em qualquer ordem. (Verifique se que você estiver arrastando os pré-fabricados da cena, não os pré-fabricados na pasta do projeto.)

![Seletor de pincel](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector pré-fabricado**

Uma vez que o **BrushSelector** herda **AttachToController**, ele mostra **destro/canhoto** e **elemento** opções no  **Inspetor de** painel. Selecionamos **direita** e **apontando para representar** anexar ferramentas de pincel para o controlador de mão direita com direção para frente.

O **BrushSelector** faz uso de dois utilitários:
* **Elipse**: usado para gerar pontos no espaço ao longo de uma forma de elipse.
* **LineObjectCollection**: distribui objetos usando os pontos de gerados por qualquer classe de linha (por exemplo, a elipse). Esse é o que usaremos para colocar nosso pincéis ao longo da forma de elipse.

Quando combinados, esses utilitários podem ser usados para criar um menu radial.

**Script LineObjectCollection**

**LineObjectCollection** tem controles para o tamanho, posição e rotação de objetos distribuídos ao longo de sua linha. Isso é útil para a criação de menus radiais como o seletor de pincel. Para criar a aparência de pincéis que se ajustam-se de nada como eles abordam a posição do Centro de selecionado, o **ObjectScale** curva picos no centro e menos acentuada desativado nas bordas.

**Script BrushSelector**

No caso do **BrushSelector**, escolhemos usar animação procedural. Primeiro, modelos de pincel são distribuídos em uma elipse, o **LineObjectCollection** script. Em seguida, cada pincel é responsável por manter sua posição em mãos do usuário com base em seu **DisplayMode** valor, que as alterações com base na seleção. Devido à alta probabilidade de transições de posição de pincel que está sendo interrompida conforme o usuário seleciona pincéis, escolhemos uma abordagem de procedimentos. Animações Mecanim podem lidar com interrupções normalmente, mas ela costuma ser mais complicado do que uma operação de Lerp simples.

**BrushSelector** usa uma combinação de ambos. Quando for detectada entrada touchpad, opções de pincel se tornam visíveis e escalar verticalmente ao longo do menu radial. Após um período de tempo limite (o que indica que o usuário tiver feito uma seleção) o pincel de opções de dimensionamento para baixo novamente, deixando apenas o pincel selecionado.

**Visualizando touchpad entrada**

Mesmo nos casos em que o modelo do controlador foi substituído completamente, pode ser útil mostrar a entrada em entradas do modelo original. Isso ajuda a Terra as ações do usuário, na realidade. Para o **BrushSelector** que escolhemos para tornar o touchpad brevemente visíveis quando a entrada é recebida. Isso foi feito, recuperando o elemento Touchpad do controlador, substituindo seu material com um material personalizado, em seguida, aplicar um gradiente para a cor do material que baseia o touchpad de tempo a última entrada foi recebida.

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

**Seleção de ferramenta pincel com a entrada do teclado sensível ao toque**

Quando o seletor de pincel detecta a entrada de pressionado do touchpad, ele verifica a posição da entrada para determinar se ele foi para a esquerda ou direita.

**Espessura do traço com selectPressedAmount**

Em vez do **InteractionSourcePressType.Select** evento na **InteractionSourcePressed()**, você pode obter o valor analógico do valor pressionado por meio de **selectPressedAmount**. Esse valor pode ser recuperado no **InteractionSourceUpdated()**.

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

**Borracha** é um tipo especial de pincel que substitui a base **pincel**do **DrawOverTime()** função. Enquanto o desenho for true, a borracha verifica para ver se sua dica faz interseção com todos os traços do pincel existente. Se isso acontecer, eles são adicionados a uma fila para ser reduzido para baixo e excluídos.

## <a name="advanced-design---teleportation-and-locomotion"></a>Design avançado - Teleportation e locomotion

Se você quiser permitir que o usuário move a cena com teleportation usando direcional, use **MixedRealityCameraParent** em vez de **MixedRealityCamera**. Você também precisa adicionar **InputManager** e **DefaultCusor**. Uma vez que **MixedRealityCameraParent** já inclui **MotionControllers** e **limite** como componentes filho, você deve remover existente  **MotionControllers** e **ambiente** pré-fabricado.

### <a name="instructions"></a>Instruções

* No **hierarquia** do painel, exclua **MixedRealityCamera**, **ambiente** e **MotionControllers**
* Do **painel projeto**, a pesquisa e arraste os seguintes pré-fabricados para o **hierarquia** painel:
    * Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/**InputManager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

![Realidade misturada câmera pai](images/mr213-cameraparent-300px.png)
* No **hierarquia** do painel, clique em **Input Manager**
* No **Inspector** do painel, role para baixo até a **seletor único de ponteiro simples** seção
* Dos **hierarquia** do painel, arraste **DefaultCursor** na **Cursor** campo

![Atribuição de DefaultCursor](images/mr213-defaultcursor-500px.png)
* **Salve** a cena e clique em de **reproduzir** botão. Você poderá usar o analógico para girar esquerda/direita ou ser transportado.

## <a name="the-end"></a>Fim

E esse é o final deste tutorial! Você aprendeu:
* Como trabalhar com modelos de controlador de movimento no modo de jogo do Unity e o tempo de execução.
* Como usar diferentes tipos de eventos do botão e seus aplicativos.
* Como elementos de interface do usuário sobre o controlador de sobreposição ou totalmente personalizá-lo.

Agora você está pronto para começar a criar sua própria experiência de imersão com controladores de movimento!

## <a name="completed-scenes"></a>Cenas concluídas

* Do Unity **projeto** no painel, clique o **cenas** pasta.
* Você encontrará duas telas do Unity **MixedReality213** e **MixedReality213Advanced**.
    * **MixedReality213**: Cena concluída com pincel único
    * **MixedReality213Advanced**: Concluído cena com vários pincel com exemplo de valor pressione do botão de seleção

## <a name="see-also"></a>Consulte também

* [Arquivos de projeto MR entrada 213](https://github.com/Microsoft/MixedReality213)
* [Toolkit de realidade misturada - cena de teste de movimento do controlador](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Kit de ferramentas de realidade misturada - mecânica de captura](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Diretrizes de desenvolvimento de controlador de movimento](motion-controllers.md)
