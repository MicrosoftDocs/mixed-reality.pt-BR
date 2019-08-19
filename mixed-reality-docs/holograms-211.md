---
title: Entrada MR 211-gesto
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes dos conceitos de gesto.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, gesto
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522461"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

# <a name="mr-input-211-gesture"></a>Entrada MR 211: Gesto

Os [gestos](gestures.md) desativam a intenção do usuário. Com gestos, os usuários podem interagir com os hologramas. Neste curso, veremos como acompanhar as mãos do usuário, responder a entrada do usuário e fornecer comentários para o usuário com base no estado e no local.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

No [Sr basics 101](holograms-101.md), usamos um gesto simples de toque de ar para interagir com nossos hologramas. Agora, vamos passar além do gesto de toque do ar e explorar novos conceitos para:

* Detectar quando a mão do usuário está sendo acompanhada e fornecer comentários ao usuário.
* Use um gesto de navegação para girar nossos hologramas.
* Forneça comentários quando a mão do usuário estiver prestes a sair da exibição.
* Use eventos de manipulação para permitir que os usuários movam os hologramas com suas mãos.

Neste curso, Vamos revisitar o **Explorador de modelos**de projeto do Unity, que criamos no [Sr Input 210](holograms-210.md). Nosso amigo Astronaut está voltado a nos ajudar em nossa exploração desses novos conceitos de gesto.

>[!IMPORTANT]
>Os vídeos inseridos em cada um dos capítulos abaixo foram registrados usando uma versão mais antiga do Unity e o kit de ferramentas do Mixed Reality. Embora as instruções passo a passo sejam precisas e atuais, você pode ver scripts e visuais nos vídeos correspondentes que estão desatualizados. Os vídeos permanecem incluídos para posterity e porque os conceitos abordados ainda se aplicam.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Entrada MR 211: Gesto</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas](install-the-tools.md)corretas instaladas.
* Alguma capacidade C# básica de programação.
* Você deve ter concluído o [Sr noções básicas 101](holograms-101.md).
* Você deve ter concluído o [Sr Input 210](holograms-210.md).
* Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) exigidos pelo projeto. Requer o Unity 2017,2 ou posterior.
* Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).

### <a name="errata-and-notes"></a>Errata e observações

* "Habilitar Apenas Meu Código" precisa ser desabilitado (desmarcado) no Visual Studio em ferramentas-> opções-> depuração para acessar os pontos de interrupção no código.

## <a name="chapter-0---unity-setup"></a>Capítulo 0-configuração do Unity

### <a name="instructions"></a>Instruções

1. Inicie o Unity.
2. Selecione **abrir**.
3. Navegue até a pasta de gestos que você cancelou anteriormente.
4. Localize e selecione a pasta **iniciando**/o**Gerenciador de modelos** .
5. Clique no botão **Selecionar pasta** .
6. No painel **projeto** , expanda a pasta **cenas** .
7. Clique duas vezes em cena **ModelExplorer** para carregá-la no Unity.

### <a name="building"></a>Compilação

1. No Unity, selecione **arquivo > configurações de Build**.
2. Se **cenas/ModelExplorer** não estiver listado em **cenas em compilação**, clique em **Adicionar cenas abertas** para adicionar a cena.
3. Se você estiver desenvolvendo especificamente para o HoloLens, defina o **dispositivo de destino** para o **hololens**. Caso contrário, deixe em **qualquer dispositivo**.
4. Verifique se **tipo de compilação** está definido como **D3D** e se o **SDK** está definido para o **mais recente instalado** (que deve ser o SDK 16299 ou mais recente).
5. Clique em **Compilar**.
6. Crie uma **nova pasta** chamada "app".
7. Clique uma vez na pasta do **aplicativo** .
8. Pressione **Selecionar pasta** e o Unity começará a compilar o projeto para o Visual Studio.

Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.

1. Abra a pasta do **aplicativo** .
2. Abra a **solução ModelExplorer do Visual Studio**.

Se estiver implantando no HoloLens:

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.
2. Clique na seta suspensa ao lado do botão computador local e selecione **computador remoto**.
3. Insira **o endereço IP do dispositivo de HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)** . Clique em **Selecionar**. Se você não souber o endereço IP do dispositivo, examine **configurações > rede & Internet > opções avançadas**.
4. Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**. Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com o Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Quando o aplicativo tiver sido implantado, ignore o **Fitbox** com um **gesto de seleção**.

Se estiver implantando em um headset de imersão:

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x64**.
2. Verifique se o destino de implantação está definido como **computador local**.
3. Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.
4. Quando o aplicativo tiver sido implantado, ignore o **Fitbox** puxando o gatilho em um controlador de movimento.

>[!NOTE]
>Você pode observar alguns erros vermelhos no painel de erros do Visual Studio. É seguro ignorá-los. Alterne para o painel saída para exibir o andamento real da compilação. Os erros no painel de saída exigirão que você faça uma correção (geralmente elas são causadas por um erro em um script).

## <a name="chapter-1---hand-detected-feedback"></a>Capítulo 1-comentários detectados

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Objetivos

* Assine os eventos de acompanhamento do Hand.
* Use comentários do cursor para mostrar os usuários quando uma mão estiver sendo controlada.

### <a name="instructions"></a>Instruções

* No painel **hierarquia** , expanda o objeto **InputManager** .
* Procure e selecione o objeto **GesturesInput** .

O script **InteractionInputSource.cs** executa estas etapas:

1. Assina os eventos InteractionSourceDetected e InteractionSourceLost.
2. Define o estado HandDetected.
3. Cancela a assinatura dos eventos InteractionSourceDetected e InteractionSourceLost.

Em seguida, atualizaremos nosso cursor da [entrada do sr 210](holograms-210.md) em um que mostre os comentários, dependendo das ações do usuário.

1. No painel **hierarquia** , selecione o objeto de **cursor** e exclua-o.
2. No painel **projeto** , pesquise **CursorWithFeedback** e arraste-o para o painel **hierarquia** .
3. Clique em **InputManager** no painel **hierarquia** e arraste o objeto **CursorWithFeedback** da **hierarquia** para o campo de **cursor** do **SimpleSinglePointerSelector**do InputManager, na parte inferior da **Inspetor**.
4. Clique em **CursorWithFeedback** na **hierarquia**.
5. No painel **Inspetor** , expanda **dados de estado do cursor** no script de **cursor do objeto** .

Os **dados de estado do cursor** funcionam da seguinte maneira:

* Qualquer **estado** de observação significa que nenhuma mão é detectada e o usuário está simplesmente olhando.
* Qualquer estado de **interação** significa que uma mão ou um controlador é detectado.
* Qualquer estado de **foco** significa que o usuário está observando um holograma.

### <a name="build-and-deploy"></a>Compilar e implantar

* No Unity, use **as configurações de Build de > de arquivo** para recompilar o aplicativo.
* Abra a pasta do **aplicativo** .
* Se ainda não estiver aberto, abra a **solução ModelExplorer Visual Studio**.
  * (Se você já criou/implantou esse projeto no Visual Studio durante a instalação, poderá abrir essa instância do VS e clicar em ' recarregar tudo ' quando solicitado).
* No Visual Studio, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.
* Depois que o aplicativo for implantado no HoloLens, ignore o fitbox usando o gesto de toque do ar.
* Mova sua mão para a exibição e aponte o dedo para o céu até o início do controle.
* Mova sua mão para a esquerda, para a direita, para cima e para baixo.
* Observe como o cursor é alterado quando a sua mão é detectada e perdida da exibição.
* Se você estiver em um headset de imersão, precisará se conectar e desconectar seu controlador. Esse comentário se torna menos interessante em um dispositivo de imersão, pois um controlador conectado sempre será "disponível".

## <a name="chapter-2---navigation"></a>Capítulo 2-navegação

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Objetivos

* Use eventos de gesto de navegação para girar o Astronaut.

### <a name="instructions"></a>Instruções

Para usar gestos de navegação em nosso aplicativo, vamos editar **GestureAction.cs** para girar objetos quando ocorrer o gesto de navegação. Além disso, adicionaremos comentários ao cursor para exibir quando a navegação estiver disponível.

1. No painel **hierarquia** , expanda **CursorWithFeedback**.
2. Na pasta **hologramas** , localize o ativo **ScrollFeedback** .
3. Arraste e solte o **ScrollFeedback** pré-fabricado no **CursorWithFeedback** gameobject na **hierarquia**.
4. Clique em **CursorWithFeedback**.
5. No painel **Inspetor** , clique no botão **Adicionar componente** .
6. No menu, digite na caixa de pesquisa **CursorFeedback**. Selecione o resultado da pesquisa.
7. Arraste e solte o objeto **ScrollFeedback** da **hierarquia** na propriedade de **objeto de jogo scroll detected Game** no componente de **comentários do cursor** no **Inspetor**.
8. No painel **hierarquia** , selecione o objeto **AstroMan** .
9. No painel **Inspetor** , clique no botão **Adicionar componente** .
10. No menu, digite a **ação de gesto**de caixa de pesquisa. Selecione o resultado da pesquisa.

Em seguida, abra **GestureAction.cs** no Visual Studio. Em código exercício 2. c, edite o script para fazer o seguinte:

1. **Gire o objeto AstroMan** sempre que um gesto de navegação for executado.
2. Calcule o **rotationFactor** para controlar a quantidade de rotação aplicada ao objeto.
3. **Gire o objeto** ao lado do eixo y quando o usuário move sua mão para a esquerda ou para a direita.

Conclua os exercícios de codificação 2. c no script ou substitua o código pela solução concluída abaixo:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

Você observará que os outros eventos de navegação já estão preenchidos com algumas informações. Enviamos o gameobject para a pilha modal do InputSystem's do kit de ferramentas, para que o usuário não precise manter o foco no Astronaut depois que a rotação for iniciada. De modo correspondente, vamos desencaixar o gameobject da pilha quando o gesto for concluído.

### <a name="build-and-deploy"></a>Compilar e implantar

1. Recompile o aplicativo no Unity e, em seguida, compile e implante a partir do Visual Studio para executá-lo no HoloLens.
2. Olhar na Astronaut, duas setas devem aparecer em ambos os lados do cursor. Esse novo visual indica que o Astronaut pode ser girado.
3. Coloque sua mão na posição pronta (o dedo aponta para o céu) para que o HoloLens comece a controlar sua mão.
4. Para girar o Astronaut, reduza o dedo do seu índice para uma posição de pinçagem e, em seguida, mova a mão para a esquerda ou para a direita para disparar o gesto de NavigationX.

## <a name="chapter-3---hand-guidance"></a>Capítulo 3-orientação

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Objetivos

* Use a **Pontuação de orientação à mão** para ajudar a prever quando o rastreamento à mão será perdido.
* Forneça **comentários sobre o cursor** para mostrar quando a mão do usuário se aproximar da borda da exibição da câmera.

### <a name="instructions"></a>Instruções

1. No painel **hierarquia** , selecione o objeto **CursorWithFeedback** .
2. No painel **Inspetor** , clique no botão **Adicionar componente** .
3. No menu, digite as **orientações**da caixa de pesquisa. Selecione o resultado da pesquisa.
4. Na pasta hologramas do painel **projeto** , localize o ativo **HandGuidanceFeedback** .
5. Arraste e solte o ativo **HandGuidanceFeedback** na propriedade **indicador de orientação à mão** no painel **Inspetor** .

### <a name="build-and-deploy"></a>Compilar e implantar

* Recompile o aplicativo no Unity e, em seguida, compile e implante a partir do Visual Studio para experimentar o aplicativo no HoloLens.
* Traga sua mão para a exibição e aumente o seu índice para ser acompanhado.
* Comece a girar o Astronaut com o gesto de navegação (Aperte o dedo do índice e o polegar juntos).
* Mova a mão para a extrema esquerda, para a direita, para cima e para baixo.
* À medida que a sua mão se aproximar da borda do quadro do gesto, uma seta deverá aparecer ao lado do cursor para avisá-lo de que o acompanhamento manual será perdido. A seta indica em qual direção mover sua mão para evitar que o rastreamento seja perdido.

## <a name="chapter-4---manipulation"></a>Capítulo 4-manipulação

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Objetivos

* Use eventos de manipulação para mover o Astronaut com suas mãos.
* Forneça comentários sobre o cursor para permitir que o usuário saiba quando a manipulação pode ser usada.

### <a name="instructions"></a>Instruções

GestureManager.cs e AstronautManager.cs nos permitirão fazer o seguinte:

1. Use a palavra-chave de fala "**move Astronaut**" para habilitar gestos de **manipulação** e "**girar Astronaut**" para desabilitá-los.
2. Alterne para responder ao reconhecedor de gestos de **manipulação**.

Vamos começar.

1. No painel **hierarquia** , crie um novo gameobject vazio. Nomeie-o como "**AstronautManager**".
2. No painel **Inspetor** , clique no botão **Adicionar componente** .
3. No menu, digite na caixa de pesquisa **Astronaut Manager**. Selecione o resultado da pesquisa.
4. No painel **Inspetor** , clique no botão **Adicionar componente** .
5. No menu, digite a caixa de pesquisa **fonte de entrada de fala**. Selecione o resultado da pesquisa.

Agora, vamos adicionar os comandos de fala necessários para controlar o estado de interação do Astronaut.

1. Expanda a seção **palavras-chave** no **Inspetor**.
2. **+** Clique no lado direito para adicionar uma nova palavra-chave.
3. Digite a palavra-chave como **mover Astronaut**. Fique à vontade para adicionar um atalho de chave, se desejado.
4. **+** Clique no lado direito para adicionar uma nova palavra-chave.
5. Digite a palavra-chave como **girar Astronaut**. Fique à vontade para adicionar um atalho de chave, se desejado.
6. O código de manipulador correspondente pode ser encontrado em **GestureAction.cs**, no manipulador **ISpeechHandler. OnSpeechKeywordRecognized** .

![Como configurar a fonte de entrada de fala para o capítulo 4](images/holograms211-speech.png)

Em seguida, vamos configurar os comentários de manipulação no cursor.

1. Na pasta hologramas do painel **projeto** , localize o ativo **PathingFeedback** .
2. Arraste e solte o **PathingFeedback** pré-fabricado no objeto **CursorWithFeedback** na **hierarquia**.
3. No painel **hierarquia** , clique em **CursorWithFeedback**.
4. Arraste e solte o objeto **PathingFeedback** da **hierarquia** para a propriedade demarcar **objeto de jogo detectado** no componente de **comentários do cursor** no **Inspetor**.

Agora, precisamos adicionar código a **GestureAction.cs** para habilitar o seguinte:

1. Adicione o código à função **IManipulationHandler. OnManipulationUpdated** , que moverá o Astronaut quando um gesto de **manipulação** for detectado.
2. Calcule o **vetor de movimento** para determinar onde o Astronaut deve ser movido com base na posição da mão.
3. **Mova** o Astronaut para a nova posição.

Conclua a codificação exercício 4. a no **GestureAction.cs**ou use nossa solução concluída abaixo:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>Compilar e implantar

* Recompile no Unity e, em seguida, compile e implante a partir do Visual Studio para executar o aplicativo no HoloLens.
* Mova sua mão na frente do HoloLens e aumente o dedo do índice para que ele possa ser acompanhado.
* Focalize o cursor sobre o Astronaut.
* Diga ' mover Astronaut ' para mover o Astronaut com um gesto de manipulação.
* Quatro setas devem aparecer ao contrário do cursor para indicar que o programa agora responderá a eventos de manipulação.
* Reduza o seu dedo de índice para o polegar e mantenha-os esmagados juntos.
* À medida que você mudar de lado, o Astronaut se moverá também (isso é manipulação).
* Gere o seu índice para parar de manipular o Astronaut.
* Observação: Se você não disser ' mover Astronaut ' antes de mover sua mão, o gesto de navegação será usado em vez disso.
* Diga ' Rotate Astronaut ' para retornar ao estado de rotatable.

## <a name="chapter-5---model-expansion"></a>Capítulo 5 – expansão de modelo

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Objetivos

* Expanda o modelo Astronaut em várias partes menores com as quais o usuário pode interagir.
* Mova cada peça individualmente usando gestos de navegação e manipulação.

### <a name="instructions"></a>Instruções

Nesta seção, realizaremos as seguintes tarefas:

1. Adicione uma nova palavra-chave "**Expand Model**" para expandir o modelo Astronaut.
2. Adicione uma nova palavra-chave "**Redefinir modelo**" para retornar o modelo ao seu formulário original.

Vamos fazer isso adicionando mais duas palavras-chave à fonte de entrada de fala do capítulo anterior. Também demonstraremos outra maneira de lidar com eventos de reconhecimento.

1. Clique em voltar em **AstronautManager** no **Inspetor** e expanda a seção **palavras-chave** no **Inspetor**.
2. **+** Clique no lado direito para adicionar uma nova palavra-chave.
3. Digite a palavra-chave como **modelo de expansão**. Fique à vontade para adicionar um atalho de chave, se desejado.
4. **+** Clique no lado direito para adicionar uma nova palavra-chave.
5. Digite a palavra-chave como **modelo**de redefinição. Fique à vontade para adicionar um atalho de chave, se desejado.
6. No painel **Inspetor** , clique no botão **Adicionar componente** .
7. No menu, digite o manipulador de entrada de **fala**da caixa de pesquisa. Selecione o resultado da pesquisa.
8. Verifique **se o ouvinte global**, pois queremos que esses comandos funcionem independentemente do gameobject que estamos concentrando.
9. Clique no **+** botão e selecione **expandir modelo** na lista suspensa de palavras-chave.
10. Clique em em resposta e arraste o AstronautManager da hierarquia para o campo nenhum (objeto). **+**
11. Agora, clique no menu suspenso **sem função** , selecione **AstronautManager**e **ExpandModelCommand**.
12. Clique no botão do **+** manipulador de entrada de fala e selecione **Redefinir modelo** na lista suspensa de palavras-chave.
13. Clique em em resposta e arraste o AstronautManager da hierarquia para o campo nenhum (objeto). **+**
14. Agora, clique no menu suspenso **sem função** , selecione **AstronautManager**e **ResetModelCommand**.

![Como configurar a fonte de entrada e o manipulador de fala para o capítulo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Compilar e implantar

* Experimente! Crie e implante o aplicativo no HoloLens.
* Digamos **expandir modelo** para ver o modelo de Astronaut expandido.
* Use a **navegação** para girar partes individuais do naipe Astronaut.
* Digamos **mover Astronaut** e, em seguida, usar a **manipulação** para mover partes individuais do naipe de Astronaut.
* Digamos **girar Astronaut** para girar as peças novamente.
* Digamos que redefina o **modelo** para retornar o Astronaut para seu formato original.

## <a name="the-end"></a>Fim

Parabéns! Agora você concluiu **o Sr Input 211: Gesto**.

* Você sabe como detectar e responder a eventos de rastreamento, navegação e manipulação à mão.
* Você entende a diferença entre gestos de navegação e manipulação.
* Você sabe como alterar o cursor para fornecer comentários visuais para quando uma mão é detectada, quando uma mão está prestes a ser perdida e para quando um objeto dá suporte a interações diferentes (navegação vs.).
