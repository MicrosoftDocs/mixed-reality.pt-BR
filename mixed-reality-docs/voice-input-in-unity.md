---
title: Entrada de voz no Unity
description: O Unity expõe três maneiras de adicionar entrada de voz ao seu aplicativo Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrada de voz, KeywordRecognizer, GrammarRecognizer, microfone, ditado, voz
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548686"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="e4161-104">Entrada de voz no Unity</span><span class="sxs-lookup"><span data-stu-id="e4161-104">Voice input in Unity</span></span>

<span data-ttu-id="e4161-105">O Unity expõe três maneiras de adicionar [entrada de voz](voice-input.md) ao aplicativo Unity.</span><span class="sxs-lookup"><span data-stu-id="e4161-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="e4161-106">Com o KeywordRecognizer (um dos dois tipos de PhraseRecognizers), seu aplicativo pode receber uma matriz de comandos de cadeia de caracteres a serem escutados.</span><span class="sxs-lookup"><span data-stu-id="e4161-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="e4161-107">Com o GrammarRecognizer (o outro tipo de PhraseRecognizer), seu aplicativo pode receber um arquivo SRGS definindo uma gramática específica a ser escutada.</span><span class="sxs-lookup"><span data-stu-id="e4161-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="e4161-108">Com o DictationRecognizer, seu aplicativo pode escutar qualquer palavra e fornecer ao usuário uma nota ou outra exibição de sua fala.</span><span class="sxs-lookup"><span data-stu-id="e4161-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="e4161-109">Somente o reconhecimento de ditado ou frase pode ser manipulado de uma vez.</span><span class="sxs-lookup"><span data-stu-id="e4161-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="e4161-110">Isso significa que se um GrammarRecognizer ou KeywordRecognizer estiver ativo, um DictationRecognizer não poderá estar ativo e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="e4161-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="e4161-111">Habilitando o recurso de voz</span><span class="sxs-lookup"><span data-stu-id="e4161-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="e4161-112">A capacidade do **microfone** deve ser declarada para que um aplicativo aproveite a entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="e4161-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="e4161-113">No editor do Unity, vá para as configurações do Player navegando até "Editar configurações do projeto > > Player"</span><span class="sxs-lookup"><span data-stu-id="e4161-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="e4161-114">Clique na guia "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="e4161-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="e4161-115">Na seção "configurações de publicação > recursos", verifique a capacidade do **microfone**</span><span class="sxs-lookup"><span data-stu-id="e4161-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="e4161-116">Reconhecimento de frases</span><span class="sxs-lookup"><span data-stu-id="e4161-116">Phrase Recognition</span></span>

<span data-ttu-id="e4161-117">Para permitir que seu aplicativo Ouça frases específicas faladas pelo usuário e, em seguida, execute alguma ação, você precisa:</span><span class="sxs-lookup"><span data-stu-id="e4161-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="e4161-118">Especificar quais frases escutar usando um KeywordRecognizer ou GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="e4161-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="e4161-119">Manipular o evento OnPhraseRecognized e tomar medidas correspondentes à frase reconhecida</span><span class="sxs-lookup"><span data-stu-id="e4161-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="e4161-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="e4161-120">KeywordRecognizer</span></span>

<span data-ttu-id="e4161-121">**Namespace:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="e4161-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="e4161-122">**Digita** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="e4161-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="e4161-123">Precisaremos de algumas instruções de uso para salvar alguns pressionamentos de tecla:</span><span class="sxs-lookup"><span data-stu-id="e4161-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="e4161-124">Em seguida, vamos adicionar alguns campos à sua classe para armazenar o reconhecedor e o dicionário de ação de > de palavra-chave:</span><span class="sxs-lookup"><span data-stu-id="e4161-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="e4161-125">Agora, adicione uma palavra-chave ao dicionário (por exemplo, dentro de um método Start ()).</span><span class="sxs-lookup"><span data-stu-id="e4161-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="e4161-126">Estamos adicionando a palavra-chave "Activate" neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="e4161-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="e4161-127">Crie o reconhecedor de palavra-chave e diga a ele o que desejamos reconhecer:</span><span class="sxs-lookup"><span data-stu-id="e4161-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="e4161-128">Registre-se agora para o evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="e4161-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="e4161-129">Um manipulador de exemplo é:</span><span class="sxs-lookup"><span data-stu-id="e4161-129">An example handler is:</span></span>

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

<span data-ttu-id="e4161-130">Por fim, comece a reconhecer!</span><span class="sxs-lookup"><span data-stu-id="e4161-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="e4161-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="e4161-131">GrammarRecognizer</span></span>

<span data-ttu-id="e4161-132">**Namespace:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="e4161-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="e4161-133">**Tipos**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="e4161-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="e4161-134">O GrammarRecognizer será usado se você estiver especificando a gramática de reconhecimento usando o SRGS.</span><span class="sxs-lookup"><span data-stu-id="e4161-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="e4161-135">Isso pode ser útil se seu aplicativo tiver mais do que apenas algumas palavras-chave, se você quiser reconhecer frases mais complexas ou se quiser ativar e desativar facilmente conjuntos de comandos.</span><span class="sxs-lookup"><span data-stu-id="e4161-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="e4161-136">Consulte: [Crie gramáticas usando o XML SRGS](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) para informações de formato de arquivo.</span><span class="sxs-lookup"><span data-stu-id="e4161-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="e4161-137">Quando você tiver sua gramática SRGS e ele estiver em seu projeto em uma [pasta StreamingAssets](http://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="e4161-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="e4161-138">Crie um GrammarRecognizer e passe o caminho para o arquivo SRGS:</span><span class="sxs-lookup"><span data-stu-id="e4161-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="e4161-139">Registre-se agora para o evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="e4161-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="e4161-140">Você receberá um retorno de chamada contendo as informações especificadas na gramática SRGS, que você pode manipular adequadamente.</span><span class="sxs-lookup"><span data-stu-id="e4161-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="e4161-141">A maioria das informações importantes será fornecida na matriz semanticMeanings.</span><span class="sxs-lookup"><span data-stu-id="e4161-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="e4161-142">Por fim, comece a reconhecer!</span><span class="sxs-lookup"><span data-stu-id="e4161-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="e4161-143">Ditado</span><span class="sxs-lookup"><span data-stu-id="e4161-143">Dictation</span></span>

<span data-ttu-id="e4161-144">**Namespace:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="e4161-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="e4161-145">**Tipos**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="e4161-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="e4161-146">Use o DictationRecognizer para converter a fala do usuário em texto.</span><span class="sxs-lookup"><span data-stu-id="e4161-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="e4161-147">O DictationRecognizer expõe a funcionalidade [de ditado](voice-input.md#dictation) e dá suporte ao registro e à escuta de eventos de hipótese e de expressão concluídas, para que você possa fornecer comentários ao seu usuário enquanto eles falam e depois.</span><span class="sxs-lookup"><span data-stu-id="e4161-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="e4161-148">Métodos Start () e Stop () respectivamente habilitam e desabilitam o reconhecimento de ditado.</span><span class="sxs-lookup"><span data-stu-id="e4161-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="e4161-149">Depois de feito com o reconhecedor, ele deve ser descartado usando o método Dispose () para liberar os recursos que ele usa.</span><span class="sxs-lookup"><span data-stu-id="e4161-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="e4161-150">Ele liberará esses recursos automaticamente durante a coleta de lixo com um custo de desempenho adicional se eles não forem lançados antes disso.</span><span class="sxs-lookup"><span data-stu-id="e4161-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="e4161-151">Há apenas algumas etapas necessárias para começar a usar o ditado:</span><span class="sxs-lookup"><span data-stu-id="e4161-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="e4161-152">Criar um novo DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="e4161-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="e4161-153">Manipular eventos de ditado</span><span class="sxs-lookup"><span data-stu-id="e4161-153">Handle Dictation events</span></span>
3. <span data-ttu-id="e4161-154">Iniciar o DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="e4161-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="e4161-155">Habilitando o recurso de ditado</span><span class="sxs-lookup"><span data-stu-id="e4161-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="e4161-156">O recurso "cliente da Internet", além do recurso de "microfone" mencionado acima, deve ser declarado para que um aplicativo aproveite o ditado.</span><span class="sxs-lookup"><span data-stu-id="e4161-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="e4161-157">No editor do Unity, vá para as configurações do Player navegando para a página "Editar configurações do projeto > > Player"</span><span class="sxs-lookup"><span data-stu-id="e4161-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="e4161-158">Clique na guia "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="e4161-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="e4161-159">Na seção "configurações de publicação > recursos", verifique o recurso **internetclient**</span><span class="sxs-lookup"><span data-stu-id="e4161-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="e4161-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="e4161-160">DictationRecognizer</span></span>

<span data-ttu-id="e4161-161">Crie um DictationRecognizer da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e4161-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="e4161-162">Há quatro eventos de ditado que podem ser assinados e manipulados para implementar o comportamento do ditado.</span><span class="sxs-lookup"><span data-stu-id="e4161-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="e4161-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="e4161-163">DictationResult</span></span>
2. <span data-ttu-id="e4161-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="e4161-164">DictationComplete</span></span>
3. <span data-ttu-id="e4161-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="e4161-165">DictationHypothesis</span></span>
4. <span data-ttu-id="e4161-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="e4161-166">DictationError</span></span>

<span data-ttu-id="e4161-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="e4161-167">**DictationResult**</span></span>

<span data-ttu-id="e4161-168">Esse evento é acionado depois que o usuário pausa, normalmente no final de uma sentença.</span><span class="sxs-lookup"><span data-stu-id="e4161-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="e4161-169">A cadeia de caracteres totalmente reconhecida é retornada aqui.</span><span class="sxs-lookup"><span data-stu-id="e4161-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="e4161-170">Primeiro, assine o evento DictationResult:</span><span class="sxs-lookup"><span data-stu-id="e4161-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="e4161-171">Em seguida, manipule o retorno de chamada DictationResult:</span><span class="sxs-lookup"><span data-stu-id="e4161-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="e4161-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="e4161-172">**DictationHypothesis**</span></span>

<span data-ttu-id="e4161-173">Esse evento é acionado continuamente enquanto o usuário está conversando.</span><span class="sxs-lookup"><span data-stu-id="e4161-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="e4161-174">Como o reconhecedor Ouve, ele fornece texto do que ele é ouvido até agora.</span><span class="sxs-lookup"><span data-stu-id="e4161-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="e4161-175">Primeiro, assine o evento DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="e4161-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="e4161-176">Em seguida, manipule o retorno de chamada DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="e4161-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="e4161-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="e4161-177">**DictationComplete**</span></span>

<span data-ttu-id="e4161-178">Esse evento é acionado quando o reconhecedor é interrompido, independentemente de Stop () ser chamado, um tempo limite de ocorrência ou algum outro erro.</span><span class="sxs-lookup"><span data-stu-id="e4161-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="e4161-179">Primeiro, assine o evento DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="e4161-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="e4161-180">Em seguida, manipule o retorno de chamada DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="e4161-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="e4161-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="e4161-181">**DictationError**</span></span>

<span data-ttu-id="e4161-182">Esse evento é acionado quando ocorre um erro.</span><span class="sxs-lookup"><span data-stu-id="e4161-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="e4161-183">Primeiro, assine o evento DictationError:</span><span class="sxs-lookup"><span data-stu-id="e4161-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="e4161-184">Em seguida, manipule o retorno de chamada DictationError:</span><span class="sxs-lookup"><span data-stu-id="e4161-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="e4161-185">Depois de assinar e tratar os eventos de ditado sobre os quais você se preocupa, inicie o reconhecedor de ditado para começar a receber eventos.</span><span class="sxs-lookup"><span data-stu-id="e4161-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="e4161-186">Se você não quiser mais manter o DictationRecognizer, precisará cancelar a assinatura dos eventos e descartar o DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="e4161-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="e4161-187">**Sobre**</span><span class="sxs-lookup"><span data-stu-id="e4161-187">**Tips**</span></span>
* <span data-ttu-id="e4161-188">Métodos Start () e Stop () respectivamente habilitam e desabilitam o reconhecimento de ditado.</span><span class="sxs-lookup"><span data-stu-id="e4161-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="e4161-189">Depois de feito com o reconhecedor, ele deve ser descartado usando o método Dispose () para liberar os recursos que ele usa.</span><span class="sxs-lookup"><span data-stu-id="e4161-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="e4161-190">Ele liberará esses recursos automaticamente durante a coleta de lixo com um custo de desempenho adicional se eles não forem lançados antes disso.</span><span class="sxs-lookup"><span data-stu-id="e4161-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="e4161-191">Os tempos limite ocorrem após um determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="e4161-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="e4161-192">Você pode verificar esses tempos limite no evento DictationComplete.</span><span class="sxs-lookup"><span data-stu-id="e4161-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="e4161-193">Há dois tempos limite a serem cientes:</span><span class="sxs-lookup"><span data-stu-id="e4161-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="e4161-194">Se o reconhecedor for iniciado e não ouvir nenhum áudio pelos primeiros cinco segundos, ele atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e4161-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="e4161-195">Se o reconhecedor tiver dado um resultado, mas, em seguida, ouvir silêncio por vinte segundos, ele atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e4161-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="e4161-196">Usando o reconhecimento de frase e o ditado</span><span class="sxs-lookup"><span data-stu-id="e4161-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="e4161-197">Se você quiser usar o reconhecimento de frase e o ditado em seu aplicativo, será necessário desligar completamente um antes para poder iniciar o outro.</span><span class="sxs-lookup"><span data-stu-id="e4161-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="e4161-198">Se você tiver vários KeywordRecognizers em execução, poderá desligá-los de uma só vez com:</span><span class="sxs-lookup"><span data-stu-id="e4161-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="e4161-199">Para restaurar todos os reconhecedores ao estado anterior, depois que o DictationRecognizer for interrompido, você poderá chamar:</span><span class="sxs-lookup"><span data-stu-id="e4161-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="e4161-200">Você também pode apenas iniciar um KeywordRecognizer, que reiniciará o PhraseRecognitionSystem também.</span><span class="sxs-lookup"><span data-stu-id="e4161-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="e4161-201">Usando o auxiliar de microfone</span><span class="sxs-lookup"><span data-stu-id="e4161-201">Using the microphone helper</span></span>

<span data-ttu-id="e4161-202">O kit de ferramentas de realidade misturada no GitHub contém uma classe auxiliar de microfone para indicar aos desenvolvedores se há um microfone utilizável no sistema.</span><span class="sxs-lookup"><span data-stu-id="e4161-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="e4161-203">Um uso para ele é onde você desejaria verificar se há microfone no sistema antes de mostrar qualquer dica de interação de fala no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4161-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="e4161-204">O script auxiliar de microfone pode ser encontrado na [pasta de entrada/scripts/utilitários](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span><span class="sxs-lookup"><span data-stu-id="e4161-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="e4161-205">O repositório GitHub também contém um [pequeno exemplo](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrando como usar o auxiliar.</span><span class="sxs-lookup"><span data-stu-id="e4161-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="e4161-206">Entrada de voz no kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="e4161-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="e4161-207">Você pode encontrar os exemplos da entrada de voz nesta cena.</span><span class="sxs-lookup"><span data-stu-id="e4161-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="e4161-208">HoloToolkit-Examples/Input/cenas/SpeechInputSource. Unity</span><span class="sxs-lookup"><span data-stu-id="e4161-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
