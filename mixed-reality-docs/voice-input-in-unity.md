---
title: Entrada de voz no Unity
description: Unity expõe três maneiras de adicionar a entrada de voz ao seu aplicativo de realidade mista do Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrada de voz, KeywordRecognizer, GrammarRecognizer, microfone, ditado, voz
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590963"
---
# <a name="voice-input-in-unity"></a>Entrada de voz no Unity

Unity expõe três maneiras de adicionar [entrada de voz](voice-input.md) ao seu aplicativo do Unity.

Com o KeywordRecognizer (um dos dois tipos de PhraseRecognizers), seu aplicativo pode receber uma matriz de cadeia de caracteres de comandos para escutar. Com o GrammarRecognizer (o outro tipo de PhraseRecognizer), seu aplicativo pode receber um arquivo SRGS definindo uma gramática específica para escutar. Com o DictationRecognizer, seu aplicativo pode escutar qualquer palavra e fornecer ao usuário uma nota ou outra exibição de sua fala.

>[!NOTE]
>Somente o ditado ou reconhecimento de frase pode ser tratado ao mesmo tempo. Isso significa que se um GrammarRecognizer ou KeywordRecognizer estiver ativo, um DictationRecognizer não pode ser ativo e vice-versa.

## <a name="enabling-the-capability-for-voice"></a>Habilitando a funcionalidade de voz

O **microfone** recurso deve ser declarado para um aplicativo aproveitar a entrada de voz.
1. No Editor do Unity, vá para as configurações de player, navegando até "Editar > projeto Configurações > Player"
2. Clique na guia "Windows Store"
3. Na seção "> recursos de publicação configurações", verifique as **microfone** funcionalidade

## <a name="phrase-recognition"></a>Reconhecimento de frase

Para habilitar seu aplicativo escutar específicos de frases faladas pelo usuário, em seguida, executar alguma ação, você precisa:
1. Especifique quais frases para escutar usando um KeywordRecognizer ou GrammarRecognizer
2. Manipular o evento OnPhraseRecognized e tomar a ação correspondente à frase reconhecida

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Tipos:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Precisaremos de algumas instruções using ao salvar alguns pressionamentos de teclas:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Em seguida, vamos adicionar alguns campos à sua classe para armazenar o reconhecedor e a palavra-chave de dicionário de ação ->:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Agora, adicione uma palavra-chave no dicionário (por exemplo, dentro de um método Start ()). Estamos adicionando a palavra-chave "Ativar" neste exemplo:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Criar o reconhecedor de palavra-chave e informar a ele que queremos reconhecer:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Registre-se agora para o evento OnPhraseRecognized

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Um manipulador de exemplo é:

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

Por fim, comece a reconhecer!

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Tipos de**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

O GrammarRecognizer será usado se você está especificando a gramática de reconhecimento usando SRGS. Isso pode ser útil se seu aplicativo tiver mais de apenas algumas palavras-chave, se você deseja reconhecer frases mais complexos, ou se você quiser facilmente ativar e desativar conjuntos de comandos. Consulte: [Criar gramáticas usando SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) para obter informações de formato de arquivo.

Depois que a gramática SRGS, e ele está em seu projeto em um [StreamingAssets pasta](http://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Crie um GrammarRecognizer e passe-o caminho para seu arquivo SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Registre-se agora para o evento OnPhraseRecognized

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Você receberá um retorno de chamada que contém informações especificadas na sua Gramática SRGS que você pode manipular adequadamente. A maioria das informações importantes será fornecida na matriz semanticMeanings.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Por fim, comece a reconhecer!

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Ditado

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Tipos de**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Use o DictationRecognizer para converter a voz do usuário em texto. Expõe o DictationRecognizer [ditado](voice-input.md#dictation) funcionalidade e dá suporte a registro e escuta de hipótese e frase concluída eventos, portanto, você pode fornecer comentários ao seu usuário enquanto eles falam e posteriormente. Métodos Start () e Stop () respectivamente habilitar e desabilitar o reconhecimento de ditado. Depois de concluir o reconhecedor, ele deve ser descartado usando o método Dispose () para liberar os recursos que ele usa. Ele liberará esses recursos automaticamente durante a coleta de lixo a um custo de desempenho adicionais se eles não são liberados antes disso.

Há apenas algumas etapas necessárias para começar com o ditado:
1. Criar um novo DictationRecognizer
2. Manipular eventos de ditado
3. Iniciar o DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Habilitando o recurso de ditado

O recurso de "Cliente da Internet", além do recurso de "Microfone" mencionado acima, deve ser declarado para um aplicativo aproveitar o ditado.
1. No Editor do Unity, vá para as configurações de player, navegando até a página "Editar > projeto Configurações > Player"
2. Clique na guia "Windows Store"
3. Na seção "> recursos de publicação configurações", verifique as **InternetClient** capacidade

### <a name="dictationrecognizer"></a>DictationRecognizer

Criar um DictationRecognizer da seguinte forma:

```
dictationRecognizer = new DictationRecognizer();
```

Há quatro eventos de ditado que podem ser assinados e manipulados para implementar o comportamento de ditado.
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

Este evento é acionado depois que o usuário faz uma pausa, normalmente no final de uma sentença. Completo reconhecido a cadeia de caracteres é retornada aqui.

Primeiro, assine o evento DictationResult:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Em seguida, manipule o retorno de chamada DictationResult:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Esse evento é acionado continuamente enquanto o usuário está se comunicando. Como o reconhecedor de escuta, ele fornece o texto da qual ele é ouvido até o momento.

Primeiro, assine o evento DictationHypothesis:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Em seguida, manipule o retorno de chamada DictationHypothesis:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Este evento é disparado quando o reconhecedor é interrompida, seja de Stop () que está sendo chamado, um tempo limite ocorra ou algum outro erro.

Primeiro, assine o evento DictationComplete:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Em seguida, manipule o retorno de chamada DictationComplete:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Esse evento é acionado quando ocorre um erro.

Primeiro, assine o evento DictationError:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Em seguida, manipule o retorno de chamada DictationError:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Depois que você tiver se inscrito e manipulados os eventos de ditado que você se preocupa, inicie o reconhecedor de ditado para começar a receber eventos.

```
dictationRecognizer.Start();
```

Se você não deseja mais manter o DictationRecognizer ao redor, você precisa cancelar a assinatura de eventos e descartar o DictationRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Dicas**
* Métodos Start () e Stop () respectivamente habilitar e desabilitar o reconhecimento de ditado.
* Depois de concluir o reconhecedor, devem ser descartado usando o método Dispose () para liberar os recursos que ele usa. Ele liberará esses recursos automaticamente durante a coleta de lixo a um custo de desempenho adicionais se eles não são liberados antes disso.
* Tempos limite ocorre após um período de tempo definido. Você pode verificar esses tempos limite no evento DictationComplete. Há dois tempos limite a serem consideradas:
   1. Se o reconhecedor começa e não ouve o áudio para os primeiros cinco segundos, ela atingirá o tempo limite.
   2. Se o reconhecedor tenha dado a um resultado, mas, em seguida, ouve silêncio por 20 segundos, ela atingirá o tempo limite.

## <a name="using-both-phrase-recognition-and-dictation"></a>Usando o reconhecimento de frase e ditado

Se você quiser usar o reconhecimento de frase e ditado em seu aplicativo, você precisará totalmente desligados um antes de iniciar outra. Se você tiver vários execução de KeywordRecognizers, você pode fechá-los todos ao mesmo tempo com:

```
PhraseRecognitionSystem.Shutdown();
```

Para restaurar todos os identificadores ao estado anterior, depois que o DictationRecognizer é interrompida, você pode chamar:

```
PhraseRecognitionSystem.Restart();
```

Você também pode começar um KeywordRecognizer, que reiniciará o PhraseRecognitionSystem também.

## <a name="using-the-microphone-helper"></a>Usando o auxiliar de microfone

O Kit de ferramentas de realidade mista no GitHub contém uma classe auxiliar de microfone para indicar a desenvolvedores, se houver um microfone utilizável no sistema. Um uso para que ele é onde desejaria Verifique se há microfone no sistema antes de Mostrar dicas de interação de qualquer fala no aplicativo.

O script auxiliar microfone pode ser encontrado na [pasta de entrada/Scripts/Utilities](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs). O repositório do GitHub também contém um [pequena amostra](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) que demonstra como usar o auxiliar.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Entrada de voz no Kit de ferramentas de realidade mista
Você pode encontrar os exemplos de entrada de voz nessa cena.

- [HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
