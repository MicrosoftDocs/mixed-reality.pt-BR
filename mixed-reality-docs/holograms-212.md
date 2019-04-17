---
title: 212 - voz de entrada de MR
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para saber os detalhes dos conceitos de voz.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, voz
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589357"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-input-212-voice"></a>Entrada MR 212: Voz

[Entrada de voz](voice-input.md) nos dá uma outra maneira de interagir com nossa hologramas. Comandos de voz funcionam de maneira muito natural e fácil. Projete seus comandos de voz para que eles sejam:

* Natural
* Fácil de lembrar
* Contexto apropriado
* Suficientemente diferente de outras opções no mesmo contexto

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

Na [MR Noções básicas de 101](holograms-101.md), usamos o KeywordRecognizer para compilar os dois comandos simples de voz. MR 212 de entrada, vamos Aprofunde-se e aprender como:

* Comandos de voz de design que são otimizados para o mecanismo de fala do HoloLens.
* Que o usuário saiba quais voz comandos estão disponíveis.
* Reconhece que ouvimos de comando de voz do usuário.
* Compreender o que o usuário está dizendo, usando um reconhecedor de ditado.
* Use um reconhecedor de gramática para escutar comandos com base em um arquivo de especificação de gramática de reconhecimento de fala, ou SRGS.

Neste curso, voltaremos a Gerenciador de modelos, nós o construímos [MR entrada 210](holograms-210.md) e [MR entrada 211](holograms-211.md).

>[!IMPORTANT]
>Os vídeos incorporados em cada um dos capítulos a seguir foram registrados usando uma versão mais antiga do Unity e o Kit de ferramentas de realidade mista. Enquanto as instruções passo a passo são precisas e atuais, você poderá ver scripts e visuais nos vídeos correspondentes que estão desatualizados. Os vídeos permanecem incluídos serão lidas depois e porque os conceitos abordados ainda se aplicam.


## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td>Entrada MR 212: Voz</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).
* Alguns basic C# capacidade de programação.
* Você deve ter concluído [MR Noções básicas de 101](holograms-101.md).
* Você deve ter concluído [MR entrada 210](holograms-210.md).
* Você deve ter concluído [MR entrada 211](holograms-211.md).
* Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) exigidos pelo projeto. Requer o Unity 2017.2 ou posterior.
* Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Errata e notas

* "Habilitar apenas meu código" precisa ser desabilitado (*desmarcado*) no Visual Studio em Ferramentas -> Opções -> depuração para usar pontos de interrupção em seu código.

## <a name="unity-setup"></a>Instalação do Unity

### <a name="instructions"></a>Instruções

1. Inicie o Unity.
2. Selecione **aberto**.
3. Navegue até a **HolographicAcademy-hologramas 212 voz** pasta você anteriormente não arquivadas.
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

## <a name="chapter-1---awareness"></a>Capítulo 1 - reconhecimento

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Objetivos

* Aprenda a **dicas** do design de comando de voz.
* Use **KeywordRecognizer** adicionar olhar com base em comandos de voz.
* E informar os usuários de comandos de voz usando o cursor **comentários**.

### <a name="voice-command-design"></a>Design de comando de voz

Neste capítulo, você aprenderá sobre a criação de comandos de voz. Ao criar comandos de voz:

#### <a name="do"></a>DO

* Crie comandos concisos. Você não quiser usar *"Reproduzir o vídeo selecionado no momento"*, porque esse comando não é mais conciso e poderia ser facilmente esquecido pelo usuário. Em vez disso, você deve usar: *"Reproduzir o vídeo"*, pois ela é concisa e tem vários sílabas.
* Use um vocabulário simple. Sempre tente usar palavras e frases que são fáceis de descobrir e lembre-se o usuário comuns. Por exemplo, se o aplicativo tiver um objeto de anotação que pode ser exibido ou ocultado da exibição, você não usaria o comando *"Mostrar letreiro"*, pois "letreiro" é um termo usado raramente. Em vez disso, você usaria o comando: *"Mostrar Observação"* para revelar a anotação em seu aplicativo.
* Ser consistente. Comandos de voz devem ser mantidos consistentes entre seu aplicativo. Imagine que você tenha duas cenas no seu aplicativo e as duas cenas contêm um botão para fechar o aplicativo. Se a primeira cena usado o comando *"Sair"* para disparar o botão, mas o segundo cena usado o comando *"Fechar aplicativo"*, em seguida, o usuário vai ficar muito confuso. Se a mesma funcionalidade persiste por várias cenas, o mesmo comando de voz deve ser usado para dispará-lo.

#### <a name="dont"></a>NÃO

* Use os comandos Sílaba único. Por exemplo, se você estivesse criando um comando de voz para reproduzir um vídeo, você deve evitar usar o comando simple *"Reproduzir"*, conforme ele é apenas uma Sílaba única e pode ser facilmente perdido pelo sistema. Em vez disso, você deve usar: *"Reproduzir o vídeo"*, pois ela é concisa e tem vários sílabas.
* Use os comandos do sistema. O *"Selecionar"* comando é reservado pelo sistema para acionar um evento de toque para o objeto focalizado no momento. Não use novamente o *"Selecionar"* de comando em uma palavra-chave ou frase, pois ele pode não funcionar conforme o esperado. Por exemplo, se o comando de voz para selecionar um cubo em seu aplicativo estava *"Selecione cubo"*, mas o usuário estava procurando em uma esfera quando eles escrevi o comando, em seguida, o círculo seria selecionado em vez disso. Da mesma forma da barra de comandos do aplicativo está habilitado para voz. Não use os seguintes comandos de voz no modo de exibição CoreWindow:
    1. Voltar
    2. Ferramenta de rolagem
    3. Ferramenta de zoom
    4. Ferramenta de arrastar
    5. Ajustar
    6. Remover
* Use sons semelhantes. Tente evitar o uso de comandos de voz poesia. Se você tiver um aplicativo de compras que tem suporte *"Mostrar Store"* e *"Mostrar mais"* como comandos de voz, em seguida, você desejaria desabilitar um dos comandos, enquanto a outra estava em uso. Por exemplo, você pode usar o *"Mostrar Store"* botão para abrir a loja e, em seguida, desabilite esse comando quando o repositório foi exibido para que o *"Mostrar mais"* comando pode ser usado para navegação.

### <a name="instructions"></a>Instruções

* Do Unity **hierarquia** do painel, use a ferramenta de pesquisa para localizar o **holoComm_screen_mesh** objeto.
* Clique duas vezes no **holoComm_screen_mesh** objeto para exibi-lo na **cena**. Essa é a inspeção do astronaut, que responderá a nossa comandos de voz.
* No **Inspector** do painel, localize a **fonte de entrada de fala (Script)** componente.
* Expanda o **palavras-chave** seção para ver o comando de voz com suporte: **Abra o Communicator**.
* Clique na engrenagem ao lado direito e, em seguida, selecione **Editar Script**.
* Explore **SpeechInputSource.cs** entender como ele usa o **KeywordRecognizer** para adicionar comandos de voz.

### <a name="build-and-deploy"></a>Criar e implantar

* No Unity, use **arquivo > configurações de Build** para recompilar o aplicativo.
* Abra o **aplicativo** pasta.
* Abra o **ModelExplorer Visual Studio Solution**.

(Se você já criado/implantado esse projeto no Visual Studio durante a instalação, em seguida, você pode abrir aquela instância do VS e clique em 'Recarregar todos' quando solicitado).

* No Visual Studio, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.
* Depois que o aplicativo é implantado para o HoloLens, ignorar a caixa de ajuste usando o [polegar](gestures.md#air-tap) gesto.
* Mantenha o foco em inspeção do astronaut.
* Quando o relógio tem o foco, verifique se que o cursor muda para um microfone. Isso fornece comentários que o aplicativo está escutando comandos de voz.
* Verifique se uma dica de ferramenta aparece no relógio. Isso ajuda os usuários a descobrir os *"Communicator aberto"* comando.
* Durante a observação na inspeção, digamos *"Abrir Communicator"* para abrir o painel do communicator.

## <a name="chapter-2---acknowledgement"></a>Capítulo 2 - confirmação

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Objetivos

* Grave uma mensagem usando a entrada do microfone.
* Fornecer comentários ao usuário que o aplicativo está escutando a sua voz.

>[!NOTE]
>O **microfone** capacidade deve ser declarada para um aplicativo registrar-se do microfone. Isso é feito para que você já no MR 212 de entrada, mas lembre-se para seus próprios projetos.
>
>1. No Editor do Unity, vá para as configurações de player, navegando até "Editar > projeto Configurações > Player"
>2. Clique na guia "Plataforma Universal do Windows"
>3. Na seção "> recursos de publicação configurações", verifique as **microfone** funcionalidade

### <a name="instructions"></a>Instruções

* Do Unity **hierarquia** do painel, verifique se que o **holoComm_screen_mesh** objeto está selecionado.
* No **Inspector** do painel, localize a **Astronaut Watch (Script)** componente.
* Clique no cubo pequeno e azul que é definido como o valor da **Communicator pré-fabricado** propriedade.
* No **Project** painel, o **Communicator** pré-fabricado agora deve ter o foco.
* Clique no **Communicator** pré-fabricado na **projeto** painel para exibir seus componentes no **Inspetor**.
* Examine os **microfone Manager (Script)** componente, isso nos permitirá gravar voz do usuário.
* Observe que o **Communicator** objeto tem um **manipulador de entrada de fala (Script)** componente de resposta para o **enviar mensagem** comando.
* Examine os **Communicator (Script)** componente e clique duas vezes em que o script para abri-lo no Visual Studio.

Communicator.cs é responsável por definir os estados do botão adequada no dispositivo communicator. Isso permitirá que nossos usuários gravar uma mensagem, reproduzi-lo e enviar a mensagem para o astronaut. Ele também iniciar e parar um formulário do wave animado, para confirmar para o usuário que sua voz foi ouvido.

* Na **Communicator.cs**, exclua as linhas a seguir (81 e 82) da **iniciar** método. Isso permitirá que o botão 'Record' sobre o communicator.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Criar e implantar

* No Visual Studio, recompile seu aplicativo e implantar o dispositivo.
* Mantenha o foco em inspeção do astronautas e dizer *"Communicator aberto"* para mostrar o communicator.
* Pressione a **registro** botão (microfone) para iniciar a gravação de uma mensagem textual para o astronaut.
* Comece a falar e verifique se que a animação wave é reproduzido no communicator, que fornece comentários ao usuário que sua voz seja ouvida.
* Pressione a **parar** botão (quadrado à esquerda) e, em seguida, verifique se a animação wave para em execução.
* Pressione a **reproduzir** botão (triângulo) para reproduzir a mensagem gravada e ouvi-lo no dispositivo.
* Pressione a **parar** botão (quadrado à direita) para parar a reprodução da mensagem gravada.
* Digamos *"Enviar mensagem"* para fechar o communicator e receber uma resposta de 'Mensagem recebida' da astronautas.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Capítulo 3 - Noções básicas e o reconhecedor de ditado

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Objetivos

* Use o reconhecedor de ditado para converter a voz do usuário em texto.
* Mostre os resultados de hipotética e finais do reconhecedor de ditado do communicator.

Neste capítulo, vamos usar o reconhecedor de ditado para criar uma mensagem para o astronaut. Ao usar o reconhecedor de ditado, tenha em mente que:

* Você deve estar conectado ao Wi-Fi para o reconhecedor de ditado funcione.
* Tempos limite ocorre após um período de tempo definido. Há dois tempos limite a serem consideradas:
  * Se o reconhecedor começa e não ouve o áudio para os primeiros cinco segundos, ela atingirá o tempo limite.
  * Se o reconhecedor tenha dado a um resultado, mas, em seguida, ouve silêncio por 20 segundos, ela atingirá o tempo limite.
* Apenas um tipo de reconhecedor (palavra-chave ou ditado) pode executar por vez.

>[!NOTE]
>O **microfone** capacidade deve ser declarada para um aplicativo registrar-se do microfone. Isso é feito para que você já no MR 212 de entrada, mas lembre-se para seus próprios projetos.
>
>1. No Editor do Unity, vá para as configurações de player, navegando até "Editar > projeto Configurações > Player"
>2. Clique na guia "Plataforma Universal do Windows"
>3. Na seção "> recursos de publicação configurações", verifique as **microfone** funcionalidade

### <a name="instructions"></a>Instruções

Vamos editar **MicrophoneManager.cs** para usar o reconhecedor de ditado. Este é o que vamos adicionar:

1. Quando o **botão Record** é pressionada, vamos **iniciar o DictationRecognizer**.
2. Mostrar o **hipótese** do qual o DictationRecognizer compreendido.
3. Bloquear a **resultados** do qual o DictationRecognizer compreendido.
4. Verifique se há tempos limite do DictationRecognizer.
5. Quando o **botão Parar** é pressionada, ou o tempo limite, a sessão de mic **interromper o DictationRecognizer**.
6. Reinicie o **KeywordRecognizer**, que escutará as **enviar mensagem** comando.

Vamos começar. Conclua todos os exercícios de codificação para 3.a na **MicrophoneManager.cs**, ou copie e cole o código concluído encontrado abaixo:

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

### <a name="build-and-deploy"></a>Criar e implantar

* Recompile no Visual Studio e implantar seu dispositivo.
* Descarte a caixa de ajuste com um gesto de toque de ar.
* Mantenha o foco em inspeção do astronautas e dizer *"Communicator aberto"*.
* Selecione o **registro** botão (microfone) para gravar a mensagem.
* Comece a falar. O **ditado reconhecedor** interpretará sua fala e mostrar o texto hipotética em do communicator.
* Experimente o ditado *"Enviar mensagem"* enquanto você estiver gravando uma mensagem. Observe que o **reconhecedor de palavra-chave** não responde porque o **ditado reconhecedor** ainda está ativa.
* Pare a fala por alguns segundos. Assista como o reconhecedor de ditado conclui sua hipótese e mostra o resultado final.
* Começar a falar e, em seguida, pausa por 20 segundos. Isso fará com que o **ditado reconhecedor** atingir o tempo limite.
* Observe que o **palavra-chave reconhecedor** for habilitado novamente após o tempo de limite acima. Agora, o communicator responderá aos comandos de voz.
* Digamos *"Enviar mensagem"* para enviar a mensagem para o astronaut.

## <a name="chapter-4---grammar-recognizer"></a>Capítulo 4 - reconhecedor de gramática

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Objetivos

* Use o reconhecedor de gramática para reconhecer fala do usuário de acordo com um arquivo de especificação de gramática de reconhecimento de fala, ou SRGS.

>[!NOTE]
>O **microfone** capacidade deve ser declarada para um aplicativo registrar-se do microfone. Isso é feito para que você já no MR 212 de entrada, mas lembre-se para seus próprios projetos.
>
>1. No Editor do Unity, vá para as configurações de player, navegando até "Editar > projeto Configurações > Player"
>2. Clique na guia "Plataforma Universal do Windows"
>3. Na seção "> recursos de publicação configurações", verifique as **microfone** funcionalidade

### <a name="instructions"></a>Instruções

1. No **hierarquia** do painel, pesquise por **Jetpack_Center** e selecioná-lo.
2. Procure os **que ação** de script na **Inspetor** painel.
3. Clique no círculo pequeno à direita do **objeto à marca ao longo de** campo.
4. Na janela pop-up, pesquise **SRGSToolbox** e selecione-o na lista.
5. Dê uma olhada a **SRGSColor.xml** arquivo na **StreamingAssets** pasta.
* A especificação de design SRGS pode ser encontrada no site do W3C [aqui](https://www.w3.org/TR/speech-grammar/).
* Em nosso arquivo SRGS, temos três tipos de regras:
  * Uma regra que permite que você dizer em uma cor de uma lista de doze cores.
  * Três regras que escuta para uma combinação da regra de cor e uma das três formas.
  * A regra raiz, colorChooser, que escuta para qualquer combinação das regras de três "de cor + da forma". As formas podem ser dito em qualquer ordem e em qualquer quantidade de apenas um para todos os três. Isso é a única regra que é ouvida, conforme ele é especificado como a regra raiz na parte superior do arquivo na primeira &lt;gramática&gt; marca.

### <a name="build-and-deploy"></a>Criar e implantar

* Recompilar o aplicativo no Unity, em seguida, criar e implantar do Visual Studio para experimentar o aplicativo em HoloLens.
* Descarte a caixa de ajuste com um gesto de toque de ar.
* Mantenha o foco em jetpack do astronautas e execute um gesto de toque de ar.
* Comece a falar. O **gramática reconhecedor** interpretará sua fala e alterar as cores das formas com base no reconhecimento. Um exemplo de comando é "quadrado círculo azul, amarelo".
* Execute outro gesto de toque de ar para descartar a caixa de ferramentas.

## <a name="the-end"></a>Fim

Parabéns! Agora você concluiu **MR 212 de entrada: Voz**.

* Você sabe que dicas de comandos de voz.
* Você viu como as dicas de ferramentas foram empregadas conscientizá usuários dos comandos de voz.
* Você viu vários tipos de comentários usados para confirmar que a voz do usuário foi ouvida.
* Você sabe como alternar entre o reconhecedor de palavra-chave e o reconhecedor de ditado, e como esses dois recursos entenderem e interpretam sua voz.
* Você aprendeu como usar um arquivo SRGS e o reconhecedor de gramática de reconhecimento de fala em seu aplicativo.
