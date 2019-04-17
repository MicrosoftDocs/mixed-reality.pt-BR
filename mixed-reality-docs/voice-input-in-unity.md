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
# <a name="voice-input-in-unity"></a><span data-ttu-id="81900-104">Entrada de voz no Unity</span><span class="sxs-lookup"><span data-stu-id="81900-104">Voice input in Unity</span></span>

<span data-ttu-id="81900-105">Unity expõe três maneiras de adicionar [entrada de voz](voice-input.md) ao seu aplicativo do Unity.</span><span class="sxs-lookup"><span data-stu-id="81900-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="81900-106">Com o KeywordRecognizer (um dos dois tipos de PhraseRecognizers), seu aplicativo pode receber uma matriz de cadeia de caracteres de comandos para escutar.</span><span class="sxs-lookup"><span data-stu-id="81900-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="81900-107">Com o GrammarRecognizer (o outro tipo de PhraseRecognizer), seu aplicativo pode receber um arquivo SRGS definindo uma gramática específica para escutar.</span><span class="sxs-lookup"><span data-stu-id="81900-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="81900-108">Com o DictationRecognizer, seu aplicativo pode escutar qualquer palavra e fornecer ao usuário uma nota ou outra exibição de sua fala.</span><span class="sxs-lookup"><span data-stu-id="81900-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="81900-109">Somente o ditado ou reconhecimento de frase pode ser tratado ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="81900-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="81900-110">Isso significa que se um GrammarRecognizer ou KeywordRecognizer estiver ativo, um DictationRecognizer não pode ser ativo e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="81900-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="81900-111">Habilitando a funcionalidade de voz</span><span class="sxs-lookup"><span data-stu-id="81900-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="81900-112">O **microfone** recurso deve ser declarado para um aplicativo aproveitar a entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="81900-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="81900-113">No Editor do Unity, vá para as configurações de player, navegando até "Editar > projeto Configurações > Player"</span><span class="sxs-lookup"><span data-stu-id="81900-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="81900-114">Clique na guia "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="81900-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="81900-115">Na seção "> recursos de publicação configurações", verifique as **microfone** funcionalidade</span><span class="sxs-lookup"><span data-stu-id="81900-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="81900-116">Reconhecimento de frase</span><span class="sxs-lookup"><span data-stu-id="81900-116">Phrase Recognition</span></span>

<span data-ttu-id="81900-117">Para habilitar seu aplicativo escutar específicos de frases faladas pelo usuário, em seguida, executar alguma ação, você precisa:</span><span class="sxs-lookup"><span data-stu-id="81900-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="81900-118">Especifique quais frases para escutar usando um KeywordRecognizer ou GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="81900-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="81900-119">Manipular o evento OnPhraseRecognized e tomar a ação correspondente à frase reconhecida</span><span class="sxs-lookup"><span data-stu-id="81900-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="81900-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="81900-120">KeywordRecognizer</span></span>

<span data-ttu-id="81900-121">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="81900-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="81900-122">**Tipos:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="81900-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="81900-123">Precisaremos de algumas instruções using ao salvar alguns pressionamentos de teclas:</span><span class="sxs-lookup"><span data-stu-id="81900-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="81900-124">Em seguida, vamos adicionar alguns campos à sua classe para armazenar o reconhecedor e a palavra-chave de dicionário de ação ->:</span><span class="sxs-lookup"><span data-stu-id="81900-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="81900-125">Agora, adicione uma palavra-chave no dicionário (por exemplo, dentro de um método Start ()).</span><span class="sxs-lookup"><span data-stu-id="81900-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="81900-126">Estamos adicionando a palavra-chave "Ativar" neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="81900-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="81900-127">Criar o reconhecedor de palavra-chave e informar a ele que queremos reconhecer:</span><span class="sxs-lookup"><span data-stu-id="81900-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="81900-128">Registre-se agora para o evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="81900-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="81900-129">Um manipulador de exemplo é:</span><span class="sxs-lookup"><span data-stu-id="81900-129">An example handler is:</span></span>

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

<span data-ttu-id="81900-130">Por fim, comece a reconhecer!</span><span class="sxs-lookup"><span data-stu-id="81900-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="81900-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="81900-131">GrammarRecognizer</span></span>

<span data-ttu-id="81900-132">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="81900-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="81900-133">**Tipos de**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="81900-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="81900-134">O GrammarRecognizer será usado se você está especificando a gramática de reconhecimento usando SRGS.</span><span class="sxs-lookup"><span data-stu-id="81900-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="81900-135">Isso pode ser útil se seu aplicativo tiver mais de apenas algumas palavras-chave, se você deseja reconhecer frases mais complexos, ou se você quiser facilmente ativar e desativar conjuntos de comandos.</span><span class="sxs-lookup"><span data-stu-id="81900-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="81900-136">Consulte: [Criar gramáticas usando SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) para obter informações de formato de arquivo.</span><span class="sxs-lookup"><span data-stu-id="81900-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="81900-137">Depois que a gramática SRGS, e ele está em seu projeto em um [StreamingAssets pasta](http://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="81900-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="81900-138">Crie um GrammarRecognizer e passe-o caminho para seu arquivo SRGS:</span><span class="sxs-lookup"><span data-stu-id="81900-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="81900-139">Registre-se agora para o evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="81900-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="81900-140">Você receberá um retorno de chamada que contém informações especificadas na sua Gramática SRGS que você pode manipular adequadamente.</span><span class="sxs-lookup"><span data-stu-id="81900-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="81900-141">A maioria das informações importantes será fornecida na matriz semanticMeanings.</span><span class="sxs-lookup"><span data-stu-id="81900-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="81900-142">Por fim, comece a reconhecer!</span><span class="sxs-lookup"><span data-stu-id="81900-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="81900-143">Ditado</span><span class="sxs-lookup"><span data-stu-id="81900-143">Dictation</span></span>

<span data-ttu-id="81900-144">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="81900-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="81900-145">**Tipos de**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="81900-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="81900-146">Use o DictationRecognizer para converter a voz do usuário em texto.</span><span class="sxs-lookup"><span data-stu-id="81900-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="81900-147">Expõe o DictationRecognizer [ditado](voice-input.md#dictation) funcionalidade e dá suporte a registro e escuta de hipótese e frase concluída eventos, portanto, você pode fornecer comentários ao seu usuário enquanto eles falam e posteriormente.</span><span class="sxs-lookup"><span data-stu-id="81900-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="81900-148">Métodos Start () e Stop () respectivamente habilitar e desabilitar o reconhecimento de ditado.</span><span class="sxs-lookup"><span data-stu-id="81900-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="81900-149">Depois de concluir o reconhecedor, ele deve ser descartado usando o método Dispose () para liberar os recursos que ele usa.</span><span class="sxs-lookup"><span data-stu-id="81900-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="81900-150">Ele liberará esses recursos automaticamente durante a coleta de lixo a um custo de desempenho adicionais se eles não são liberados antes disso.</span><span class="sxs-lookup"><span data-stu-id="81900-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="81900-151">Há apenas algumas etapas necessárias para começar com o ditado:</span><span class="sxs-lookup"><span data-stu-id="81900-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="81900-152">Criar um novo DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="81900-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="81900-153">Manipular eventos de ditado</span><span class="sxs-lookup"><span data-stu-id="81900-153">Handle Dictation events</span></span>
3. <span data-ttu-id="81900-154">Iniciar o DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="81900-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="81900-155">Habilitando o recurso de ditado</span><span class="sxs-lookup"><span data-stu-id="81900-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="81900-156">O recurso de "Cliente da Internet", além do recurso de "Microfone" mencionado acima, deve ser declarado para um aplicativo aproveitar o ditado.</span><span class="sxs-lookup"><span data-stu-id="81900-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="81900-157">No Editor do Unity, vá para as configurações de player, navegando até a página "Editar > projeto Configurações > Player"</span><span class="sxs-lookup"><span data-stu-id="81900-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="81900-158">Clique na guia "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="81900-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="81900-159">Na seção "> recursos de publicação configurações", verifique as **InternetClient** capacidade</span><span class="sxs-lookup"><span data-stu-id="81900-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="81900-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="81900-160">DictationRecognizer</span></span>

<span data-ttu-id="81900-161">Criar um DictationRecognizer da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="81900-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="81900-162">Há quatro eventos de ditado que podem ser assinados e manipulados para implementar o comportamento de ditado.</span><span class="sxs-lookup"><span data-stu-id="81900-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="81900-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="81900-163">DictationResult</span></span>
2. <span data-ttu-id="81900-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="81900-164">DictationComplete</span></span>
3. <span data-ttu-id="81900-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="81900-165">DictationHypothesis</span></span>
4. <span data-ttu-id="81900-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="81900-166">DictationError</span></span>

<span data-ttu-id="81900-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="81900-167">**DictationResult**</span></span>

<span data-ttu-id="81900-168">Este evento é acionado depois que o usuário faz uma pausa, normalmente no final de uma sentença.</span><span class="sxs-lookup"><span data-stu-id="81900-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="81900-169">Completo reconhecido a cadeia de caracteres é retornada aqui.</span><span class="sxs-lookup"><span data-stu-id="81900-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="81900-170">Primeiro, assine o evento DictationResult:</span><span class="sxs-lookup"><span data-stu-id="81900-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="81900-171">Em seguida, manipule o retorno de chamada DictationResult:</span><span class="sxs-lookup"><span data-stu-id="81900-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="81900-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="81900-172">**DictationHypothesis**</span></span>

<span data-ttu-id="81900-173">Esse evento é acionado continuamente enquanto o usuário está se comunicando.</span><span class="sxs-lookup"><span data-stu-id="81900-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="81900-174">Como o reconhecedor de escuta, ele fornece o texto da qual ele é ouvido até o momento.</span><span class="sxs-lookup"><span data-stu-id="81900-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="81900-175">Primeiro, assine o evento DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="81900-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="81900-176">Em seguida, manipule o retorno de chamada DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="81900-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="81900-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="81900-177">**DictationComplete**</span></span>

<span data-ttu-id="81900-178">Este evento é disparado quando o reconhecedor é interrompida, seja de Stop () que está sendo chamado, um tempo limite ocorra ou algum outro erro.</span><span class="sxs-lookup"><span data-stu-id="81900-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="81900-179">Primeiro, assine o evento DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="81900-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="81900-180">Em seguida, manipule o retorno de chamada DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="81900-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="81900-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="81900-181">**DictationError**</span></span>

<span data-ttu-id="81900-182">Esse evento é acionado quando ocorre um erro.</span><span class="sxs-lookup"><span data-stu-id="81900-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="81900-183">Primeiro, assine o evento DictationError:</span><span class="sxs-lookup"><span data-stu-id="81900-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="81900-184">Em seguida, manipule o retorno de chamada DictationError:</span><span class="sxs-lookup"><span data-stu-id="81900-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="81900-185">Depois que você tiver se inscrito e manipulados os eventos de ditado que você se preocupa, inicie o reconhecedor de ditado para começar a receber eventos.</span><span class="sxs-lookup"><span data-stu-id="81900-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="81900-186">Se você não deseja mais manter o DictationRecognizer ao redor, você precisa cancelar a assinatura de eventos e descartar o DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="81900-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="81900-187">**Dicas**</span><span class="sxs-lookup"><span data-stu-id="81900-187">**Tips**</span></span>
* <span data-ttu-id="81900-188">Métodos Start () e Stop () respectivamente habilitar e desabilitar o reconhecimento de ditado.</span><span class="sxs-lookup"><span data-stu-id="81900-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="81900-189">Depois de concluir o reconhecedor, devem ser descartado usando o método Dispose () para liberar os recursos que ele usa.</span><span class="sxs-lookup"><span data-stu-id="81900-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="81900-190">Ele liberará esses recursos automaticamente durante a coleta de lixo a um custo de desempenho adicionais se eles não são liberados antes disso.</span><span class="sxs-lookup"><span data-stu-id="81900-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="81900-191">Tempos limite ocorre após um período de tempo definido.</span><span class="sxs-lookup"><span data-stu-id="81900-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="81900-192">Você pode verificar esses tempos limite no evento DictationComplete.</span><span class="sxs-lookup"><span data-stu-id="81900-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="81900-193">Há dois tempos limite a serem consideradas:</span><span class="sxs-lookup"><span data-stu-id="81900-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="81900-194">Se o reconhecedor começa e não ouve o áudio para os primeiros cinco segundos, ela atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="81900-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="81900-195">Se o reconhecedor tenha dado a um resultado, mas, em seguida, ouve silêncio por 20 segundos, ela atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="81900-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="81900-196">Usando o reconhecimento de frase e ditado</span><span class="sxs-lookup"><span data-stu-id="81900-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="81900-197">Se você quiser usar o reconhecimento de frase e ditado em seu aplicativo, você precisará totalmente desligados um antes de iniciar outra.</span><span class="sxs-lookup"><span data-stu-id="81900-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="81900-198">Se você tiver vários execução de KeywordRecognizers, você pode fechá-los todos ao mesmo tempo com:</span><span class="sxs-lookup"><span data-stu-id="81900-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="81900-199">Para restaurar todos os identificadores ao estado anterior, depois que o DictationRecognizer é interrompida, você pode chamar:</span><span class="sxs-lookup"><span data-stu-id="81900-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="81900-200">Você também pode começar um KeywordRecognizer, que reiniciará o PhraseRecognitionSystem também.</span><span class="sxs-lookup"><span data-stu-id="81900-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="81900-201">Usando o auxiliar de microfone</span><span class="sxs-lookup"><span data-stu-id="81900-201">Using the microphone helper</span></span>

<span data-ttu-id="81900-202">O Kit de ferramentas de realidade mista no GitHub contém uma classe auxiliar de microfone para indicar a desenvolvedores, se houver um microfone utilizável no sistema.</span><span class="sxs-lookup"><span data-stu-id="81900-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="81900-203">Um uso para que ele é onde desejaria Verifique se há microfone no sistema antes de Mostrar dicas de interação de qualquer fala no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="81900-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="81900-204">O script auxiliar microfone pode ser encontrado na [pasta de entrada/Scripts/Utilities](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span><span class="sxs-lookup"><span data-stu-id="81900-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="81900-205">O repositório do GitHub também contém um [pequena amostra](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) que demonstra como usar o auxiliar.</span><span class="sxs-lookup"><span data-stu-id="81900-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="81900-206">Entrada de voz no Kit de ferramentas de realidade mista</span><span class="sxs-lookup"><span data-stu-id="81900-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="81900-207">Você pode encontrar os exemplos de entrada de voz nessa cena.</span><span class="sxs-lookup"><span data-stu-id="81900-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="81900-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span><span class="sxs-lookup"><span data-stu-id="81900-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
