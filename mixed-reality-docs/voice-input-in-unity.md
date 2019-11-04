---
title: Entrada de voz no Unity
description: O Unity expõe três maneiras de adicionar entrada de voz ao seu aplicativo Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrada de voz, KeywordRecognizer, GrammarRecognizer, microfone, ditado, voz
ms.openlocfilehash: d1cd2a2b954a195bc3f2688d915965f89aa30f98
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438192"
---
# <a name="voice-input-in-unity"></a>Entrada de voz no Unity

>[!NOTE]
>Em vez das informações abaixo, considere usar o plug-in do Unity para o SDK de serviços de fala cognitiva que tem resultados de precisão de fala muito melhores e fornece acesso fácil a decodificação de fala a texto e recursos de fala avançados, como diálogo, baseado em intenção interação, tradução, síntese de conversão de texto em fala e reconhecimento de fala em idioma natural. Encontre o exemplo e documentação aqui: https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity   

O Unity expõe três maneiras de adicionar [entrada de voz](voice-input.md) ao aplicativo Unity.

Com o KeywordRecognizer (um dos dois tipos de PhraseRecognizers), seu aplicativo pode receber uma matriz de comandos de cadeia de caracteres a serem escutados. Com o GrammarRecognizer (o outro tipo de PhraseRecognizer), seu aplicativo pode receber um arquivo SRGS definindo uma gramática específica a ser escutada. Com o DictationRecognizer, seu aplicativo pode escutar qualquer palavra e fornecer ao usuário uma nota ou outra exibição de sua fala.

>[!NOTE]
>Somente o reconhecimento de ditado ou frase pode ser manipulado de uma vez. Isso significa que se um GrammarRecognizer ou KeywordRecognizer estiver ativo, um DictationRecognizer não poderá estar ativo e vice-versa.

## <a name="enabling-the-capability-for-voice"></a>Habilitando o recurso de voz

A capacidade do **microfone** deve ser declarada para que um aplicativo aproveite a entrada de voz.
1. No editor do Unity, vá para as configurações do Player navegando até "Editar configurações do projeto > > Player"
2. Clique na guia "Windows Store"
3. Na seção "configurações de publicação > recursos", verifique a capacidade do **microfone**

## <a name="phrase-recognition"></a>Reconhecimento de frases

Para permitir que seu aplicativo Ouça frases específicas faladas pelo usuário e, em seguida, execute alguma ação, você precisa:
1. Especificar quais frases escutar usando um KeywordRecognizer ou GrammarRecognizer
2. Manipular o evento OnPhraseRecognized e tomar medidas correspondentes à frase reconhecida

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Namespace:** *UnityEngine. Windows. Speech*<br>
**Tipos:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Precisaremos de algumas instruções de uso para salvar alguns pressionamentos de tecla:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Em seguida, vamos adicionar alguns campos à sua classe para armazenar o reconhecedor e o dicionário de ação de > de palavra-chave:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Agora, adicione uma palavra-chave ao dicionário (por exemplo, dentro de um método Start ()). Estamos adicionando a palavra-chave "Activate" neste exemplo:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Crie o reconhecedor de palavra-chave e diga a ele o que desejamos reconhecer:

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

**Namespace:** *UnityEngine. Windows. Speech*<br>
**Tipos**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

O GrammarRecognizer será usado se você estiver especificando a gramática de reconhecimento usando o SRGS. Isso pode ser útil se seu aplicativo tiver mais do que apenas algumas palavras-chave, se você quiser reconhecer frases mais complexas ou se quiser ativar e desativar facilmente conjuntos de comandos. Consulte: [criar gramáticas usando o XML SRGS](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) para informações de formato de arquivo.

Quando você tiver sua gramática SRGS e ele estiver em seu projeto em uma [pasta StreamingAssets](https://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Crie um GrammarRecognizer e passe o caminho para o arquivo SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Registre-se agora para o evento OnPhraseRecognized

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Você receberá um retorno de chamada contendo as informações especificadas na gramática SRGS, que você pode manipular adequadamente. A maioria das informações importantes será fornecida na matriz semanticMeanings.

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

**Namespace:** *UnityEngine. Windows. Speech*<br>
**Tipos**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Use o DictationRecognizer para converter a fala do usuário em texto. O DictationRecognizer expõe a funcionalidade de [ditado](voice-input.md#dictation) e dá suporte ao registro e à escuta de eventos de hipótese e de expressão concluídas, para que você possa fornecer comentários ao seu usuário enquanto eles falam e depois. Métodos Start () e Stop () respectivamente habilitam e desabilitam o reconhecimento de ditado. Depois de feito com o reconhecedor, ele deve ser descartado usando o método Dispose () para liberar os recursos que ele usa. Ele liberará esses recursos automaticamente durante a coleta de lixo com um custo de desempenho adicional se eles não forem lançados antes disso.

Há apenas algumas etapas necessárias para começar a usar o ditado:
1. Criar um novo DictationRecognizer
2. Manipular eventos de ditado
3. Iniciar o DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Habilitando o recurso de ditado

O recurso "cliente da Internet", além do recurso de "microfone" mencionado acima, deve ser declarado para que um aplicativo aproveite o ditado.
1. No editor do Unity, vá para as configurações do Player navegando para a página "Editar configurações do projeto > > Player"
2. Clique na guia "Windows Store"
3. Na seção "configurações de publicação > recursos", verifique o recurso **internetclient**

### <a name="dictationrecognizer"></a>DictationRecognizer

Crie um DictationRecognizer da seguinte maneira:

```
dictationRecognizer = new DictationRecognizer();
```

Há quatro eventos de ditado que podem ser assinados e manipulados para implementar o comportamento do ditado.
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

Esse evento é acionado depois que o usuário pausa, normalmente no final de uma sentença. A cadeia de caracteres totalmente reconhecida é retornada aqui.

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

Esse evento é acionado continuamente enquanto o usuário está conversando. Como o reconhecedor Ouve, ele fornece texto do que ele é ouvido até agora.

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

Esse evento é acionado quando o reconhecedor é interrompido, independentemente de Stop () ser chamado, um tempo limite de ocorrência ou algum outro erro.

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

Depois de assinar e tratar os eventos de ditado sobre os quais você se preocupa, inicie o reconhecedor de ditado para começar a receber eventos.

```
dictationRecognizer.Start();
```

Se você não quiser mais manter o DictationRecognizer, precisará cancelar a assinatura dos eventos e descartar o DictationRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Sobre**
* Métodos Start () e Stop () respectivamente habilitam e desabilitam o reconhecimento de ditado.
* Depois de feito com o reconhecedor, ele deve ser descartado usando o método Dispose () para liberar os recursos que ele usa. Ele liberará esses recursos automaticamente durante a coleta de lixo com um custo de desempenho adicional se eles não forem lançados antes disso.
* Os tempos limite ocorrem após um determinado período de tempo. Você pode verificar esses tempos limite no evento DictationComplete. Há dois tempos limite a serem cientes:
   1. Se o reconhecedor for iniciado e não ouvir nenhum áudio pelos primeiros cinco segundos, ele atingirá o tempo limite.
   2. Se o reconhecedor tiver dado um resultado, mas, em seguida, ouvir silêncio por vinte segundos, ele atingirá o tempo limite.

## <a name="using-both-phrase-recognition-and-dictation"></a>Usando o reconhecimento de frase e o ditado

Se você quiser usar o reconhecimento de frase e o ditado em seu aplicativo, será necessário desligar completamente um antes para poder iniciar o outro. Se você tiver vários KeywordRecognizers em execução, poderá desligá-los de uma só vez com:

```
PhraseRecognitionSystem.Shutdown();
```

Para restaurar todos os reconhecedores ao estado anterior, depois que o DictationRecognizer for interrompido, você poderá chamar:

```
PhraseRecognitionSystem.Restart();
```

Você também pode apenas iniciar um KeywordRecognizer, que reiniciará o PhraseRecognitionSystem também.

## <a name="using-the-microphone-helper"></a>Usando o auxiliar de microfone

O kit de ferramentas de realidade misturada no GitHub contém uma classe auxiliar de microfone para indicar aos desenvolvedores se há um microfone utilizável no sistema. Um uso para ele é onde você desejaria verificar se há microfone no sistema antes de mostrar qualquer dica de interação de fala no aplicativo.

O script auxiliar de microfone pode ser encontrado na [pasta de entrada/scripts/utilitários](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs). O repositório GitHub também contém um [pequeno exemplo](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrando como usar o auxiliar.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Entrada de voz no kit de ferramentas de realidade misturada
Você pode encontrar os exemplos da entrada de voz nesta cena.

- [HoloToolkit-Examples/Input/cenas/SpeechInputSource. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
