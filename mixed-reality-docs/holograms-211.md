---
title: 211 - gesto de entrada de MR
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para saber os detalhes dos conceitos de gesto.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, gesto
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590635"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

# <a name="mr-input-211-gesture"></a>Entrada MR 211: Gesto

[Gestos](gestures.md) transformar a intenção do usuário em ação. Com gestos, os usuários podem interagir com hologramas. Neste curso, aprenderemos como acompanhar as mãos do usuário, responder à entrada do usuário e fornecem comentários ao usuário com base por lado estado e local.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

Na [MR Noções básicas de 101](holograms-101.md), usamos um gesto polegar simples para interagir com nossa hologramas. Agora, vamos ultrapassar o gesto de toque de ar e explorar os novos conceitos para:

* Detectar quando mão do usuário está sendo rastreada e fornecer comentários ao usuário.
* Use um gesto de navegação para girar o nosso hologramas.
* Fornece comentários ao lado do usuário está prestes a sair do modo de exibição.
* Use eventos de manipulação para permitir que os usuários movam hologramas com suas mãos.

Neste curso, voltaremos o projeto do Unity **Gerenciador de modelos**, que criamos [MR entrada 210](holograms-210.md). Nosso amigo astronaut está de volta para nos ajudar em nossa exploração desses novos conceitos de gesto.

>[!IMPORTANT]
>Os vídeos incorporados em cada um dos capítulos a seguir foram registrados usando uma versão mais antiga do Unity e o Kit de ferramentas de realidade mista. Enquanto as instruções passo a passo são precisas e atuais, você poderá ver scripts e visuais nos vídeos correspondentes que estão desatualizados. Os vídeos permanecem incluídos serão lidas depois e porque os conceitos abordados ainda se aplicam.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td>Entrada MR 211: Gesto</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).
* Alguns basic C# capacidade de programação.
* Você deve ter concluído [MR Noções básicas de 101](holograms-101.md).
* Você deve ter concluído [MR entrada 210](holograms-210.md).
* Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) exigidos pelo projeto. Requer o Unity 2017.2 ou posterior.
* Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).

### <a name="errata-and-notes"></a>Errata e notas

* "Habilitar apenas meu código" precisa ser desabilitado (*desmarcado*) no Visual Studio em Ferramentas -> Opções -> depuração para usar pontos de interrupção em seu código.

## <a name="chapter-0---unity-setup"></a>Capítulo 0 - instalação do Unity

### <a name="instructions"></a>Instruções

1. Inicie o Unity.
2. Selecione **aberto**.
3. Navegue até a **gesto** pasta você anteriormente não arquivadas.
4. Localize e selecione o **iniciando**/**Gerenciador de modelos** pasta.
5. Clique o **Selecionar pasta** botão.
6. No **Project** do painel, expanda o **cenas** pasta.
7. Clique duas vezes em **ModelExplorer** cena para carregá-lo no Unity.

### <a name="building"></a>Compilação

1. No Unity, selecione **arquivo > configurações de Build**.
2. Se **cenas/ModelExplorer** não estiver listado em **cenas em compilação**, clique em **adicionar cenas aberto** para adicionar a cena.
3. Se você estiver desenvolvendo especificamente para HoloLens, defina **dispositivo de destino** à **HoloLens**. Caso contrário, deixe-nos **qualquer dispositivo**.
4. Certifique-se **Build Type** é definido como **D3D** e **SDK** é definido como **mais recente instalada** (que deve ser SDK 16299 ou mais recente).
5. Clique em **Compilar**.
6. Criar uma **nova pasta** chamado "App".
7. Único clique a **aplicativo** pasta.
8. Pressione **Selecionar pasta** e Unity começará a compilar o projeto para o Visual Studio.

Quando Unity é feito, será exibida uma janela do Explorador de arquivos.

1. Abra o **aplicativo** pasta.
2. Abra o **ModelExplorer Visual Studio Solution**.

Se a implantação para o HoloLens:

1. Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x86**.
2. Clique na lista suspensa na seta ao lado do botão de computador Local e selecione **computador remoto**.
3. Insira **seu endereço IP do dispositivo HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)**. Clique em **Selecionar**. Se você não souber o endereço IP do dispositivo, examine **Configurações > rede e Internet > Opções avançadas de**.
4. Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**. Se essa for a primeira vez em que implantar seu dispositivo, você precisará [emparelhá-lo com o Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Quando o aplicativo foi implantado, ignorar as **Fitbox** com um **selecione gesto**.

Se implantar em um fone de ouvido imersivo:

1. Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x64**.
2. Verifique se o destino de implantação é definido como **computador Local**.
3. Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.
4. Quando o aplicativo foi implantado, ignorar as **Fitbox** puxando o gatilho em um controlador de animação.

>[!NOTE]
>Você pode observar alguns erros vermelhos no painel de erros do Visual Studio. É seguro para ignorá-los. Alternar para o painel de saída para exibir real o progresso da compilação. Erros no painel Saída exigirá que você faça uma correção (com mais frequência eles são causados por um erro em um script).

## <a name="chapter-1---hand-detected-feedback"></a>Capítulo 1 - comentários de mão detectado

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Objetivos

* Inscrever-se para entregar os eventos de rastreamento.
* Use comentários de cursor para mostrar aos usuários quando uma mão está sendo rastreada.

### <a name="instructions"></a>Instruções

* No **hierarquia** do painel, expanda o **InputManager** objeto.
* Procure e selecione o **GesturesInput** objeto.

O **InteractionInputSource.cs** script executa estas etapas:

1. Assina os eventos InteractionSourceDetected e InteractionSourceLost.
2. Define o estado de HandDetected.
3. Cancela a assinatura dos eventos InteractionSourceDetected e InteractionSourceLost.

Em seguida, vamos fazer a atualização nosso cursor a partir [MR entrada 210](holograms-210.md) em uma que mostra os comentários, dependendo de ações do usuário.

1. No **hierarquia** painel, selecione o **Cursor** do objeto e excluí-lo.
2. No **Project** do painel, pesquise por **CursorWithFeedback** e arraste-o para o **hierarquia** painel.
3. Clique em **InputManager** na **hierarquia** do painel e, em seguida, arraste o **CursorWithFeedback** do objeto do **hierarquia** no Do InputManager **SimpleSinglePointerSelector**do **Cursor** campo na parte inferior a **Inspetor**.
4. Clique no **CursorWithFeedback** na **hierarquia**.
5. No **Inspector** do painel, expanda **dados de estado do Cursor** no **objeto Cursor** script.

O **dados de estado de Cursor** funciona como este:

* Qualquer **observar** estado significa que nenhuma disponível for detectado e o usuário está procurando simplesmente ao redor.
* Qualquer **interagir** estado significa que uma mão ou controlador foi detectado.
* Qualquer **passe o mouse** estado significa que o usuário está observando um holograma.

### <a name="build-and-deploy"></a>Criar e implantar

* No Unity, use **arquivo > configurações de Build** para recompilar o aplicativo.
* Abra o **aplicativo** pasta.
* Se não ainda estiver aberto, abra o **solução do Visual Studio ModelExplorer**.
  * (Se você já criado/implantado esse projeto no Visual Studio durante a instalação, em seguida, você pode abrir aquela instância do VS e clique em 'Recarregar todos' quando solicitado).
* No Visual Studio, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.
* Depois que o aplicativo é implantado para o HoloLens, ignore o fitbox usando o gesto de toque de ar.
* Mova a mão na exibição e apontar o dedo para o céu para iniciar o acompanhamento de mão.
* Mover a mão esquerda, direita, para cima e para baixo.
* Assista como o cursor muda quando sua mão é detectada e, em seguida, perdida do modo de exibição.
* Se você estiver em um fone de ouvido imersivo, você terá para se conectar e desconectar seu controlador. Esses comentários se torna menos interessante em um dispositivo imersivo, como um controlador conectado sempre será "disponível".

## <a name="chapter-2---navigation"></a>Capítulo 2 - navegação

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Objetivos

* Use eventos de gesto de navegação para girar a astronautas.

### <a name="instructions"></a>Instruções

Para usar gestos de navegação em nosso aplicativo, vamos editar **GestureAction.cs** girar objetos quando ocorre o gesto de navegação. Além disso, vamos adicionar comentários para o cursor a ser exibido quando a navegação está disponível.

1. No **hierarquia** do painel, expanda **CursorWithFeedback**.
2. No **hologramas** pasta, localize a **ScrollFeedback** ativo.
3. Arraste e solte a **ScrollFeedback** pré-fabricado até a **CursorWithFeedback** GameObject no **hierarquia**.
4. Clique em **CursorWithFeedback**.
5. No **Inspector** do painel, clique no **adicionar componente** botão.
6. No menu, digite na caixa de pesquisa **CursorFeedback**. Selecione o resultado da pesquisa.
7. Arrastar e soltar a **ScrollFeedback** do objeto da **hierarquia** até o **rolagem detectado jogo objeto** propriedade no **comentários de Cursor**componente do **Inspetor**.
8. No **hierarquia** painel, selecione o **AstroMan** objeto.
9. No **Inspector** do painel, clique no **adicionar componente** botão.
10. No menu, digite na caixa de pesquisa **ação de gesto**. Selecione o resultado da pesquisa.

Em seguida, abra **GestureAction.cs** no Visual Studio. Na codificação Exercício 2.c, edite o script para fazer o seguinte:

1. **Girar o AstroMan** do objeto sempre que um gesto de navegação é executado.
2. Calcular a **rotationFactor** para controlar a quantidade de rotação aplicada ao objeto.
3. **Girar o objeto** em torno do eixo y quando o usuário move sua mão esquerda ou direita.

Codificação completa exercita 2.c no script ou substitua o código com a solução completa abaixo:

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

Você observará que os outros eventos de navegação já são preenchidos com algumas informações. Podemos enviar por push o GameObject para o Kit de ferramentas pilha modal do InputSystem, portanto, o usuário não precisa manter o foco na astronautas depois que começou a rotação. Do mesmo modo, podemos pop o GameObject da pilha depois que o gesto é concluído.

### <a name="build-and-deploy"></a>Criar e implantar

1. Recompilar o aplicativo no Unity e, em seguida, criar e implantar do Visual Studio para executá-lo no HoloLens.
2. Mantenha o foco em astronaut, duas setas devem aparecer em ambos os lados do cursor. Este novo visual indica que o astronaut pode ser girado.
3. Coloque a mão na posição (dedo apontada para o céu) pronta para o HoloLens começará a mão de acompanhamento.
4. Para girar a astronautas, diminua o dedo para uma posição de aperto e, em seguida, mova a mão esquerda ou direita para disparar o gesto de NavigationX.

## <a name="chapter-3---hand-guidance"></a>Capítulo 3 - diretrizes de mão

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Objetivos

* Use **pontuação de diretrizes de entregar** para ajudar a prever quando mão de acompanhamento serão perdida.
* Fornecer **comentários sobre o cursor** para mostrar quando a borda da câmera do modo de exibição se aproximar de mão do usuário.

### <a name="instructions"></a>Instruções

1. No **hierarquia** painel, selecione o **CursorWithFeedback** objeto.
2. No **Inspector** do painel, clique no **adicionar componente** botão.
3. No menu, digite na caixa de pesquisa **diretrizes de mão**. Selecione o resultado da pesquisa.
4. No **projeto** painel **hologramas** pasta, localize o **HandGuidanceFeedback** ativo.
5. Arrastar e soltar a **HandGuidanceFeedback** ativo para o **indicador de orientação da mão** propriedade no **Inspetor** painel.

### <a name="build-and-deploy"></a>Criar e implantar

* Recompilar o aplicativo no Unity e, em seguida, criar e implantar do Visual Studio para experimentar o aplicativo em HoloLens.
* Colocar a mão em modo de exibição e disparar o dedo para rastreada.
* Iniciar a rotação a astronautas com o gesto de navegação (apertar o dedo e polegar juntos).
* Mova suas mãos à extrema esquerda, direita, para cima e para baixo.
* Conforme a mão se aproximar a borda do quadro de gesto, uma seta deve aparecer ao lado, o cursor para avisá-lo mão de acompanhamento serão perdido. A seta indica a direção na qual para mover sua mão para evitar que o acompanhamento sejam perdidas.

## <a name="chapter-4---manipulation"></a>Capítulo 4 - manipulação

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Objetivos

* Use eventos de manipulação para mover a astronautas com suas mãos.
* Fornece comentários sobre o cursor para que o usuário saiba quando a manipulação pode ser usada.

### <a name="instructions"></a>Instruções

GestureManager.cs e AstronautManager.cs, poderemos fazer o seguinte:

1. Use a palavra-chave fala "**mover Astronaut**" para habilitar **manipulação** gestos e "**Astronaut girar**" desabilitá-los.
2. Alternar para responder para o **reconhecedor de gestos de manipulação**.

Vamos começar.

1. No **hierarquia** painel, crie um novo GameObject vazio. Nomeie-o "**AstronautManager**".
2. No **Inspector** do painel, clique no **adicionar componente** botão.
3. No menu, digite na caixa de pesquisa **Astronaut Manager**. Selecione o resultado da pesquisa.
4. No **Inspector** do painel, clique no **adicionar componente** botão.
5. No menu, digite na caixa de pesquisa **fonte de entrada de fala**. Selecione o resultado da pesquisa.

Agora vamos adicionar os comandos de voz necessários para controlar o estado de interação da astronautas.

1. Expanda o **palavras-chave** seção o **Inspetor**.
2. Clique o **+** no lado direito para adicionar uma nova palavra-chave.
3. Digite a palavra-chave como **mover Astronaut**. Fique à vontade adicionar um atalho de chave, se desejado.
4. Clique o **+** no lado direito para adicionar uma nova palavra-chave.
5. Digite a palavra-chave como **girar Astronaut**. Fique à vontade adicionar um atalho de chave, se desejado.
6. O código de manipulador correspondente pode ser encontrado no **GestureAction.cs**, no **ISpeechHandler.OnSpeechKeywordRecognized** manipulador.

![Como configurar a fonte de entrada de fala para o capítulo 4](images/holograms211-speech.png)

Em seguida, podemos irá configurar os comentários da manipulação no cursor.

1. No **projeto** painel **hologramas** pasta, localize o **PathingFeedback** ativo.
2. Arraste e solte a **PathingFeedback** pré-fabricado até a **CursorWithFeedback** do objeto no **hierarquia**.
3. No **hierarquia** do painel, clique em **CursorWithFeedback**.
4. Arrastar e soltar a **PathingFeedback** do objeto da **hierarquia** até o **objeto de jogo detectados caminhos** propriedade no **comentários de Cursor**componente do **Inspetor**.

Agora, precisamos adicionar código para **GestureAction.cs** para habilitar o seguinte:

1. Adicione código para o **IManipulationHandler.OnManipulationUpdated** função, que moverá a astronautas quando um **manipulação** gesto é detectado.
2. Calcular a **vetor de movimento** determinar onde a astronautas devem ser movidas para posição de base por lado.
3. **Mover** a astronautas para a nova posição.

Codificação completa Exercício 4.a na **GestureAction.cs**, ou usar nossa solução concluída abaixo:

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

### <a name="build-and-deploy"></a>Criar e implantar

* Recompilar no Unity e, em seguida, criar e implantar do Visual Studio para executar o aplicativo no HoloLens.
* Mover a mão na frente do HoloLens e disparar o dedo para que ele pode ser rastreado.
* Concentre-se o cursor sobre o astronaut.
* Digamos que 'Mover Astronaut' para mover a astronautas com um gesto de manipulação.
* Quatro setas devem aparecer ao redor do cursor para indicar que o programa agora responderá a eventos de manipulação.
* Diminua o dedo para baixo até o polegar e mantê-los preso durante juntos.
* Ao mudar sua mão em torno de, a astronautas moverá muito (essa é a manipulação).
* Acionar o dedo para parar de manipular a astronautas.
* Observação: Se você não diz 'Mover Astronaut' antes de passar a mão, em seguida, o gesto de navegação será usado em vez disso.
* Digamos que 'Girar Astronaut' para retornar ao estado giratório.

## <a name="chapter-5---model-expansion"></a>Capítulo 5 - expansão do modelo

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Objetivos

* Expanda o modelo Astronaut em vários, partes menores que o usuário pode interagir com o.
* Mova cada parte individualmente usando gestos de navegação e manipulação.

### <a name="instructions"></a>Instruções

Nesta seção, podemos irá realizar as seguintes tarefas:

1. Adicionar uma nova palavra-chave "**expanda modelo**" para expandir o modelo astronaut.
2. Adicionar uma nova palavra-chave "**redefinição de modelo**" para retornar o modelo em sua forma original.

Faremos isso adicionando mais duas palavras-chave para a fonte de entrada de fala do capítulo anterior. Também demonstraremos outra maneira de lidar com eventos de reconhecimento.

1. Clique em Voltar na **AstronautManager** na **Inspetor** e expanda o **palavras-chave** seção o **Inspetor**.
2. Clique o **+** no lado direito para adicionar uma nova palavra-chave.
3. Digite a palavra-chave como **expandir modelo**. Fique à vontade adicionar um atalho de chave, se desejado.
4. Clique o **+** no lado direito para adicionar uma nova palavra-chave.
5. Digite a palavra-chave como **redefinição de modelo**. Fique à vontade adicionar um atalho de chave, se desejado.
6. No **Inspector** do painel, clique no **adicionar componente** botão.
7. No menu, digite na caixa de pesquisa **manipulador de entrada de fala**. Selecione o resultado da pesquisa.
8. Verifique **ouvinte Global é**, pois queremos que esses comandos funcionem independentemente do GameObject estamos nos concentrando.
9. Clique o **+** botão e selecione **expanda modelo** na lista suspensa de palavra-chave.
10. Clique o **+** em resposta e arraste o **AstronautManager** do **hierarquia** no **None (objeto)** campo.
11. Agora, clique o **nenhuma função** lista suspensa, selecione **AstronautManager**, em seguida, **ExpandModelCommand**.
12. Clique o manipulador de entrada de fala **+** botão e selecione **redefinição de modelo** na lista suspensa de palavra-chave.
13. Clique o **+** em resposta e arraste o **AstronautManager** do **hierarquia** no **None (objeto)** campo.
14. Agora, clique o **nenhuma função** lista suspensa, selecione **AstronautManager**, em seguida, **ResetModelCommand**.

![Como configurar a fonte de entrada de fala e o manipulador para o capítulo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Criar e implantar

* Experimente! Crie e implante o aplicativo para o HoloLens.
* Digamos **expanda modelo** para ver o modelo astronaut expandido.
* Use **navegação** para girar a partes individuais do naipe astronaut.
* Digamos **mover Astronaut** e, em seguida, use **manipulação** para mover as partes individuais do naipe astronaut.
* Digamos **Astronaut girar** girar as partes novamente.
* Digamos **redefinição de modelo** para retornar o astronaut para sua forma original.

## <a name="the-end"></a>Fim

Parabéns! Agora você concluiu **MR 211 de entrada: Gesto**.

* Você sabe como detectar e responder para entregar os eventos de rastreamento, navegação e manipulação.
* Você compreender a diferença entre os gestos de navegação e manipulação.
* Você sabe como alterar o cursor para fornecer comentários visuais para quando uma mão é detectada, quando uma mão está prestes a ser perdidas, e para quando um objeto oferecer suporte a interações diferentes (vs manipulação de navegação).
