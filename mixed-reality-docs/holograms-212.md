---
title: Entrada MR 212-Voice
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes dos conceitos de voz.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, voz
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522359"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br>

# <a name="mr-input-212-voice"></a>Entrada MR 212: Voz

A [entrada de voz](voice-input.md) nos dá outra maneira de interagir com nossos hologramas. Os comandos de voz funcionam de maneira muito natural e fácil. Crie seus comandos de voz para que eles sejam:

* Natural
* Fácil de lembrar
* Contexto apropriado
* Suficientemente diferente de outras opções dentro do mesmo contexto

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

No [Sr basics 101](holograms-101.md), usamos o KeywordRecognizer para criar dois comandos simples de voz. No Sr Input 212, vamos nos aprofundar e aprender como:

* Crie comandos de voz que são otimizados para o mecanismo de fala do HoloLens.
* Faça o usuário reconhecer quais comandos de voz estão disponíveis.
* Confirme que ouvimos o comando de voz do usuário.
* Entenda o que o usuário está dizendo, usando um reconhecedor de ditado.
* Use um reconhecedor de gramática para escutar comandos com base em um arquivo de especificação de gramática de reconhecimento de fala ou SRGS.

Neste curso, revisitaremos o Gerenciador de modelos, que criamos no [Sr input 210](holograms-210.md) e no [Sr Input 211](holograms-211.md).

>[!IMPORTANT]
>Os vídeos inseridos em cada um dos capítulos abaixo foram registrados usando uma versão mais antiga do Unity e o kit de ferramentas do Mixed Reality. Embora as instruções passo a passo sejam precisas e atuais, você pode ver scripts e visuais nos vídeos correspondentes que estão desatualizados. Os vídeos permanecem incluídos para posterity e porque os conceitos abordados ainda se aplicam.


## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Entrada MR 212: Voz</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas](install-the-tools.md)corretas instaladas.
* Alguma capacidade C# básica de programação.
* Você deve ter concluído o [Sr noções básicas 101](holograms-101.md).
* Você deve ter concluído o [Sr Input 210](holograms-210.md).
* Você deve ter concluído o [Sr Input 211](holograms-211.md).
* Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) exigidos pelo projeto. Requer o Unity 2017,2 ou posterior.
* Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Errata e observações

* "Habilitar Apenas Meu Código" precisa ser desabilitado (desmarcado) no Visual Studio em ferramentas-> opções-> depuração para acessar os pontos de interrupção no código.

## <a name="unity-setup"></a>Configuração do Unity

### <a name="instructions"></a>Instruções

1. Inicie o Unity.
2. Selecione **abrir**.
3. Navegue até a pasta **HolographicAcademy-hologramas-212-Voice** que você cancelou anteriormente.
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

## <a name="chapter-1---awareness"></a>Capítulo 1-reconhecimento

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Objetivos

* Aprenda sobre o **dos e não** sobre o design de comando de voz.
* Use **KeywordRecognizer** para adicionar comandos de voz baseados em olhar.
* Fazer com que os usuários reconheçam comandos de voz usando **comentários**do cursor.

### <a name="voice-command-design"></a>Design de comando de voz

Neste capítulo, você aprenderá a criar comandos de voz. Ao criar comandos de voz:

#### <a name="do"></a>DO

* Crie comandos concisos. Você não deseja usar *"reproduzir o vídeo selecionado atualmente"* , porque esse comando não é conciso e seria facilmente esquecido pelo usuário. Em vez disso, você deve usar: *"Reproduzir vídeo"* , porque é conciso e tem várias sílabas.
* Use um vocabulário simples. Sempre tente usar palavras e frases comuns que sejam fáceis para o usuário descobrir e se lembrar. Por exemplo, se o seu aplicativo tiver um objeto note que pudesse ser exibido ou oculto da exibição, você não usará o comando *"show letreiro"* , porque "letreiro" é um termo raramente usado. Em vez disso, use o comando: *"Mostrar nota"* , para revelar a nota em seu aplicativo.
* Ser consistente. Os comandos de voz devem ser mantidos consistentes em seu aplicativo. Imagine que você tenha duas cenas em seu aplicativo e que ambas as cenas contenham um botão para fechar o aplicativo. Se a primeira cena usou o comando *"Exit"* para disparar o botão, mas a segunda cena usou o comando *"Close app"* , o usuário vai ficar muito confuso. Se a mesma funcionalidade persistir em vários bastidores, o mesmo comando de voz deverá ser usado para dispará-lo.

#### <a name="dont"></a>NÃO

* Use comandos de sílaba única. Por exemplo, se você estivesse criando um comando de voz para reproduzir um vídeo, evite usar o comando simples *"Play"* , pois ele é apenas uma única sílaba e pode ser facilmente perdido pelo sistema. Em vez disso, você deve usar: *"Reproduzir vídeo"* , porque é conciso e tem várias sílabas.
* Use comandos do sistema. O comando *"Select"* é reservado pelo sistema para disparar um evento TAP para o objeto atualmente focalizado. Não use novamente o comando *"Select"* em uma palavra-chave ou frase, pois ele pode não funcionar conforme o esperado. Por exemplo, se o comando de voz para selecionar um cubo em seu aplicativo era *"Selecionar Cubo"* , mas o usuário estava olhando para uma esfera quando estivessem o comando, então a esfera seria selecionada em vez disso. De forma semelhante, os comandos da barra de aplicativos estão habilitados para voz Não use os seguintes comandos de fala em sua exibição do CoreWindow:
    1. Voltar
    2. Ferramenta Scroll
    3. Ferramenta de zoom
    4. Ferramenta de arrastar
    5. Ajustar
    6. Remover
* Use sons semelhantes. Tente evitar o uso de comandos de voz que Rhyme. Se você tivesse um aplicativo de compras com suporte para *"mostrar armazenamento"* e *"mostrar mais"* como comandos de voz, convém desabilitar um dos comandos enquanto o outro estava em uso. Por exemplo, você pode usar o botão *"mostrar armazenamento"* para abrir o repositório e, em seguida, desabilitar esse comando quando o repositório foi exibido para que o comando *"mostrar mais"* pudesse ser usado para navegação.

### <a name="instructions"></a>Instruções

* No painel **hierarquia** do Unity, use a ferramenta de pesquisa para localizar o objeto **holoComm_screen_mesh** .
* Clique duas vezes no objeto **holoComm_screen_mesh** para exibi-lo na **cena**. Essa é a inspeção do Astronaut, que responderá aos nossos comandos de voz.
* No painel **Inspetor** , localize o componente **fonte de entrada de fala (script)** .
* Expanda a seção **palavras-chave** para ver o comando de voz com suporte: **Abra o Communicator**.
* Clique no engrenagem no lado direito e selecione **Editar script**.
* Explore o **SpeechInputSource.cs** para entender como ele usa o **KeywordRecognizer** para adicionar comandos de voz.

### <a name="build-and-deploy"></a>Compilar e implantar

* No Unity, use **as configurações de Build de > de arquivo** para recompilar o aplicativo.
* Abra a pasta do **aplicativo** .
* Abra a **solução ModelExplorer do Visual Studio**.

(Se você já criou/implantou esse projeto no Visual Studio durante a instalação, poderá abrir essa instância do VS e clicar em ' recarregar tudo ' quando solicitado).

* No Visual Studio, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.
* Depois que o aplicativo for implantado no HoloLens, descartar a caixa ajustar usando o gesto de [toque do ar](gestures.md#air-tap) .
* Olhar na inspeção do Astronaut.
* Quando o relógio tiver foco, verifique se o cursor é alterado para um microfone. Isso fornece comentários que o aplicativo está ouvindo por comandos de voz.
* Verifique se uma dica de ferramenta aparece na inspeção. Isso ajuda os usuários a descobrir o comando *"Open Communicator"* .
* Enquanto nuvens no relógio, digamos que *"Abra o Communicator"* para abrir o painel do Communicator.

## <a name="chapter-2---acknowledgement"></a>Capítulo 2-confirmação

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Objetivos

* Registre uma mensagem usando a entrada do microfone.
* Envie comentários para o usuário que o aplicativo está ouvindo em sua voz.

>[!NOTE]
>A capacidade do **microfone** deve ser declarada para um aplicativo gravar do microfone. Isso é feito para você já no Sr Input 212, mas tenha isso em mente para seus próprios projetos.
>
>1. No editor do Unity, vá para as configurações do Player navegando até "Editar configurações do projeto > > Player"
>2. Clique na guia "Plataforma Universal do Windows"
>3. Na seção "configurações de publicação > recursos", verifique a capacidade do **microfone**

### <a name="instructions"></a>Instruções

* No painel **hierarquia** do Unity, verifique se o objeto **holoComm_screen_mesh** está selecionado.
* No painel **Inspetor** , localize o componente **Astronaut Watch (script)** .
* Clique no cubo azul pequeno, que é definido como o valor da propriedade **pré-fabricado do Communicator** .
* No painel **projeto** , o pré-fabricado do **Communicator** agora deve ter foco.
* Clique no pré-fabricado do **Communicator** no painel do **projeto** para exibir seus componentes no **Inspetor**.
* Examine o componente do **Gerenciador de microfone (script)** , isso nos permitirá registrar a voz do usuário.
* Observe que o objeto do **Communicator** tem um componente de **manipulador de entrada de fala (script)** para responder ao comando **Enviar mensagem** .
* Examine o componente do **Communicator (script)** e clique duas vezes no script para abri-lo no Visual Studio.

Communicator.cs é responsável por definir os Estados de botão apropriados no dispositivo do Communicator. Isso permitirá que os usuários registrem uma mensagem, a reproduzam e enviem a mensagem para o Astronaut. Ele também iniciará e interromperá um formulário de onda animado para confirmar ao usuário que sua voz foi ouvido.

* No **Communicator.cs**, exclua as seguintes linhas (81 e 82) do método **Start** . Isso habilitará o botão ' registro ' no Communicator.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Compilar e implantar

* No Visual Studio, recompile seu aplicativo e implante-o no dispositivo.
* Olhar na inspeção do Astronaut e diga *"Open Communicator"* para mostrar o Communicator.
* Pressione o botão **gravar** (microfone) para começar a gravar uma mensagem verbal para o Astronaut.
* Comece a falar e verifique se a animação ondulada é reproduzida no Communicator, que fornece comentários para o usuário de que a voz é ouvida.
* Pressione o botão **parar** (quadrado à esquerda) e verifique se a animação de onda interrompe a execução.
* Pressione o botão **reproduzir** (triângulo à direita) para reproduzir a mensagem gravada e ouvi-la no dispositivo.
* Pressione o botão **parar** (quadrado direito) para parar a reprodução da mensagem gravada.
* Diga *"Enviar mensagem"* para fechar o Communicator e receber uma resposta "mensagem recebida" do Astronaut.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Capítulo 3-noções básicas e o reconhecedor de ditador

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Objetivos

* Use o reconhecedor de ditado para converter a fala do usuário em texto.
* Mostre os resultados hipotéticos e finais do reconhecedor de ditado no Communicator.

Neste capítulo, usaremos o reconhecedor de ditado para criar uma mensagem para o Astronaut. Ao usar o reconhecedor de ditado, tenha em mente que:

* Você deve estar conectado a WiFi para que o reconhecedor de ditado funcione.
* Os tempos limite ocorrem após um determinado período de tempo. Há dois tempos limite a serem cientes:
  * Se o reconhecedor for iniciado e não ouvir nenhum áudio pelos primeiros cinco segundos, ele atingirá o tempo limite.
  * Se o reconhecedor tiver dado um resultado, mas, em seguida, ouvir silêncio por vinte segundos, ele atingirá o tempo limite.
* Somente um tipo de reconhecedor (palavra-chave ou ditado) pode ser executado de cada vez.

>[!NOTE]
>A capacidade do **microfone** deve ser declarada para um aplicativo gravar do microfone. Isso é feito para você já no Sr Input 212, mas tenha isso em mente para seus próprios projetos.
>
>1. No editor do Unity, vá para as configurações do Player navegando até "Editar configurações do projeto > > Player"
>2. Clique na guia "Plataforma Universal do Windows"
>3. Na seção "configurações de publicação > recursos", verifique a capacidade do **microfone**

### <a name="instructions"></a>Instruções

Vamos editar **MicrophoneManager.cs** para usar o reconhecedor de ditado. Isso é o que vamos adicionar:

1. Quando o **botão gravar** for pressionado, vamos **iniciar o DictationRecognizer**.
2. Mostre a **hipótese** do que o DictationRecognizer entendeu.
3. Bloqueie os **resultados** do que o DictationRecognizer entendeu.
4. Verifique se há tempos limite do DictationRecognizer.
5. Quando o **botão parar** é pressionado, ou a sessão do MIC atinge o tempo limite, **pare o DictationRecognizer**.
6. Reinicie o **KeywordRecognizer**, que escutará o comando **Enviar mensagem** .

Vamos começar. Conclua todos os exercícios de codificação para 3. a no **MicrophoneManager.cs**, ou copie e cole o código concluído encontrado abaixo:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone. 
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>Compilar e implantar

* Recompile no Visual Studio e implante em seu dispositivo.
* Descartar a caixa ajustar com um gesto de toque de ar.
* Olhar na inspeção do Astronaut e diga *"Open Communicator"* .
* Selecione o botão **gravar** (microfone) para registrar sua mensagem.
* Comece a falar. O  reconhecedor de ditado irá interpretar a fala e mostrar o texto hipotético no Communicator.
* Tente dizer *"Enviar mensagem"* enquanto estiver gravando uma mensagem. Observe que o reconhecedor de **palavra-chave** não  responde porque o reconhecedor de ditado ainda está ativo.
* Pare de falar por alguns segundos. Observe como o reconhecedor de ditado conclui sua hipótese e mostra o resultado final.
* Comece a falar e, em seguida, pause por 20 segundos. Isso fará com que  o reconhecedor de ditado tenha tempo limite.
* Observe que o reconhecedor de **palavra-chave** é habilitado novamente após o tempo limite acima. Agora, o Communicator responderá aos comandos de voz.
* Diga *"Enviar mensagem"* para enviar a mensagem para o Astronaut.

## <a name="chapter-4---grammar-recognizer"></a>Capítulo 4-reconhecedor de gramática

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Objetivos

* Use o reconhecedor de gramática para reconhecer a fala do usuário de acordo com um arquivo SRGS ou especificação de gramática de reconhecimento de fala.

>[!NOTE]
>A capacidade do **microfone** deve ser declarada para um aplicativo gravar do microfone. Isso é feito para você já no Sr Input 212, mas tenha isso em mente para seus próprios projetos.
>
>1. No editor do Unity, vá para as configurações do Player navegando até "Editar configurações do projeto > > Player"
>2. Clique na guia "Plataforma Universal do Windows"
>3. Na seção "configurações de publicação > recursos", verifique a capacidade do **microfone**

### <a name="instructions"></a>Instruções

1. No painel **hierarquia** , procure **Jetpack_Center** e selecione-o.
2. Procure o script de **ação que** no painel **Inspetor** .
3. Clique no pequeno círculo à direita do campo **para marcar** ao lado do objeto.
4. Na janela que aparece, pesquise por **SRGSToolbox** e selecione-o na lista.
5. Dê uma olhada no arquivo **SRGSColor. xml** na pasta **StreamingAssets** .
* A especificação de design SRGS pode ser encontrada no site W3C [aqui](https://www.w3.org/TR/speech-grammar/).
* Em nosso arquivo SRGS, temos três tipos de regras:
  * Uma regra que permite que você diga uma cor de uma lista de doze cores.
  * Três regras que escutam uma combinação da regra de cor e uma das três formas.
  * A regra raiz, colorChooser, que escuta qualquer combinação das três regras de "cor + forma". As formas podem ser consideradas em qualquer ordem e em qualquer quantidade de apenas uma para a terceira. Essa é a única regra que é escutada, pois é especificada como a regra raiz na parte superior do arquivo na marca de gramática &lt;&gt; inicial.

### <a name="build-and-deploy"></a>Compilar e implantar

* Recompile o aplicativo no Unity e, em seguida, compile e implante a partir do Visual Studio para experimentar o aplicativo no HoloLens.
* Descartar a caixa ajustar com um gesto de toque de ar.
* Olhar no jetpack do Astronaut e execute um gesto de toque de ar.
* Comece a falar. O **reconhecedor gramatical** irá interpretar sua fala e alterar as cores das formas com base no reconhecimento. Um comando de exemplo é "círculo azul, quadrado amarelo".
* Execute outro gesto de toque de ar para ignorar a caixa de ferramentas.

## <a name="the-end"></a>Fim

Parabéns! Agora você concluiu **o Sr Input 212: Voz**.

* Você conhece o dos e não os comandos de voz.
* Você viu como as dicas de ferramentas foram empregadas para fazer com que os usuários reconheçam os comandos de voz.
* Você viu vários tipos de comentários usados para confirmar que a voz do usuário foi ouvida.
* Você sabe como alternar entre o reconhecedor de palavra-chave e o reconhecedor de ditador e como esses dois recursos compreendem e interpretam sua voz.
* Você aprendeu a usar um arquivo SRGS e o reconhecedor de gramática para reconhecimento de fala em seu aplicativo.
