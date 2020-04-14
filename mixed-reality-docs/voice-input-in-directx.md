---
title: Entrada de voz no DirectX
description: Explica como implementar comandos de voz e um pequeno reconhecimento de frases e frases em um aplicativo DirectX para a realidade mista do Windows.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Walkthrough, comando de voz, frase, reconhecimento, fala, DirectX, plataforma, Cortana, realidade do Windows Mixed
ms.openlocfilehash: 2837a0fc42e8fdebb2e1facee118d20b5668cd43
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277964"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="1319a-104">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="1319a-104">Voice input in DirectX</span></span>

<span data-ttu-id="1319a-105">Este artigo explica como implementar [comandos de voz](voice-input.md) , além de reconhecimento de frase e frases pequenas em um aplicativo do DirectX para a realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="1319a-105">This article explains how to implement [voice commands](voice-input.md) plus small-phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="1319a-106">Os trechos de código neste artigo usam C++/CX em vez de/WinRT em conformidade com C++C + +17, que é usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="1319a-106">The code snippets in this article use C++/CX rather than C++17-compliant C++/WinRT, which is used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="1319a-107">Os conceitos são equivalentes a C++um projeto/WinRT, mas você precisa converter o código.</span><span class="sxs-lookup"><span data-stu-id="1319a-107">The concepts are equivalent for a C++/WinRT project, but you need to translate the code.</span></span>

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a><span data-ttu-id="1319a-108">Usar SpeechRecognizer para reconhecimento de fala contínuo</span><span class="sxs-lookup"><span data-stu-id="1319a-108">Use SpeechRecognizer for continuous speech recognition</span></span>

<span data-ttu-id="1319a-109">Esta seção descreve como usar o reconhecimento de fala contínuo para habilitar comandos de voz em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1319a-109">This section describes how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="1319a-110">O passo a passo usa o código do exemplo [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) .</span><span class="sxs-lookup"><span data-stu-id="1319a-110">This walk-through uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) sample.</span></span> <span data-ttu-id="1319a-111">Quando o exemplo estiver em execução, fale o nome de um dos comandos de cor registrados para alterar a cor do cubo girando.</span><span class="sxs-lookup"><span data-stu-id="1319a-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="1319a-112">Primeiro, crie uma nova instância do *Windows:: Media:: SpeechRecognition:: SpeechRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="1319a-112">First, create a new *Windows::Media::SpeechRecognition::SpeechRecognizer* instance.</span></span>

<span data-ttu-id="1319a-113">De *HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="1319a-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="1319a-114">Crie uma lista de comandos de fala para o reconhecedor a ser escutado.</span><span class="sxs-lookup"><span data-stu-id="1319a-114">Create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="1319a-115">Aqui, construímos um conjunto de comandos para alterar a cor de um holograma.</span><span class="sxs-lookup"><span data-stu-id="1319a-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="1319a-116">Para sua conveniência, também criamos os dados que usaremos para os comandos mais tarde.</span><span class="sxs-lookup"><span data-stu-id="1319a-116">For convenience, we also create the data that we'll use for the commands later.</span></span>

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

<span data-ttu-id="1319a-117">Você pode usar palavras fonéticas que podem não estar em um dicionário para especificar comandos.</span><span class="sxs-lookup"><span data-stu-id="1319a-117">You can use phonetic words that might not be in a dictionary to specify commands.</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="1319a-118">Para carregar a lista de comandos na lista de restrições do reconhecedor de fala, use um objeto [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) .</span><span class="sxs-lookup"><span data-stu-id="1319a-118">To load the commands list into the list of constraints for the speech recognizer use a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

<span data-ttu-id="1319a-119">Assine o evento [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) no [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)do reconhecedor de fala.</span><span class="sxs-lookup"><span data-stu-id="1319a-119">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="1319a-120">Esse evento notifica seu aplicativo quando um de seus comandos for reconhecido.</span><span class="sxs-lookup"><span data-stu-id="1319a-120">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="1319a-121">O manipulador de eventos *OnResultGenerated* recebe dados de evento em uma instância [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) .</span><span class="sxs-lookup"><span data-stu-id="1319a-121">Your *OnResultGenerated* event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="1319a-122">Se a confiança for maior que o limite que você definiu, seu aplicativo deverá observar que o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="1319a-122">If the confidence is greater than the threshold that you defined, your app should note that the event happened.</span></span> <span data-ttu-id="1319a-123">Salve os dados do evento para que você possa usá-los em um loop de atualização subsequente.</span><span class="sxs-lookup"><span data-stu-id="1319a-123">Save the event data so that you can use it in a subsequent update loop.</span></span>

<span data-ttu-id="1319a-124">De *HolographicVoiceInputSampleMain. cpp*:</span><span class="sxs-lookup"><span data-stu-id="1319a-124">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

<span data-ttu-id="1319a-125">Em nosso código de exemplo, alteramos a cor do cubo de holograma girando de acordo com o comando do usuário.</span><span class="sxs-lookup"><span data-stu-id="1319a-125">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="1319a-126">De *HolographicVoiceInputSampleMain:: Update*:</span><span class="sxs-lookup"><span data-stu-id="1319a-126">From *HolographicVoiceInputSampleMain::Update*:</span></span>

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-one-shot-recognition"></a><span data-ttu-id="1319a-127">Usar o reconhecimento "One-shot"</span><span class="sxs-lookup"><span data-stu-id="1319a-127">Use "one-shot" recognition</span></span>

<span data-ttu-id="1319a-128">Você pode configurar um reconhecedor de fala para escutar frases ou frases que o usuário fala.</span><span class="sxs-lookup"><span data-stu-id="1319a-128">You can configure a speech recognizer to listen for phrases or sentences that the user speaks.</span></span> <span data-ttu-id="1319a-129">Nesse caso, aplicamos um *SpeechRecognitionTopicConstraint* que informa ao reconhecedor de fala o tipo de entrada a ser esperado.</span><span class="sxs-lookup"><span data-stu-id="1319a-129">In this case, we apply a *SpeechRecognitionTopicConstraint* that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="1319a-130">Aqui está um fluxo de trabalho de aplicativo para este cenário:</span><span class="sxs-lookup"><span data-stu-id="1319a-130">Here's an app workflow for this scenario:</span></span>
1. <span data-ttu-id="1319a-131">Seu aplicativo cria o SpeechRecognizer, fornece prompts de interface do usuário e começa a escutar um comando falado.</span><span class="sxs-lookup"><span data-stu-id="1319a-131">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a spoken command.</span></span>
2. <span data-ttu-id="1319a-132">O usuário fala uma frase ou frase.</span><span class="sxs-lookup"><span data-stu-id="1319a-132">The user speaks a phrase or sentence.</span></span>
3. <span data-ttu-id="1319a-133">O reconhecimento da fala do usuário ocorre e um resultado é retornado para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1319a-133">Recognition of the user's speech occurs, and a result is returned to the app.</span></span> <span data-ttu-id="1319a-134">Neste ponto, seu aplicativo deve fornecer um prompt de interface do usuário para indicar que o reconhecimento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="1319a-134">At this point, your app should provide a UI prompt to indicate that recognition has occurred.</span></span>
4. <span data-ttu-id="1319a-135">Dependendo do nível de confiança que você deseja responder e do nível de confiança do resultado do reconhecimento de fala, seu aplicativo poderá processar o resultado e responder conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="1319a-135">Depending on the confidence level that you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="1319a-136">Esta seção descreve como criar um SpeechRecognizer, compilar a restrição e ouvir a entrada de fala.</span><span class="sxs-lookup"><span data-stu-id="1319a-136">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="1319a-137">O código a seguir compila a restrição de tópico, que nesse caso é otimizada para pesquisa na Web.</span><span class="sxs-lookup"><span data-stu-id="1319a-137">The following code compiles the topic constraint, which in this case is optimized for web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="1319a-138">Se a compilação for realizada com sucesso, podemos continuar com o reconhecimento de fala.</span><span class="sxs-lookup"><span data-stu-id="1319a-138">If compilation succeeds, we can proceed with speech recognition.</span></span>

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

<span data-ttu-id="1319a-139">O resultado é retornado para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1319a-139">The result is then returned to the app.</span></span> <span data-ttu-id="1319a-140">Se estivermos confiantes o suficiente no resultado, podemos processar o comando.</span><span class="sxs-lookup"><span data-stu-id="1319a-140">If we're confident enough in the result, we can process the command.</span></span> <span data-ttu-id="1319a-141">Este exemplo de código processa resultados com pelo menos confiança média.</span><span class="sxs-lookup"><span data-stu-id="1319a-141">This code example processes results with at least medium confidence.</span></span>

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

<span data-ttu-id="1319a-142">Sempre que usar o reconhecimento de fala, observe as exceções que podem indicar que o usuário desativou o microfone nas configurações de privacidade do sistema.</span><span class="sxs-lookup"><span data-stu-id="1319a-142">Whenever you use speech recognition, watch for exceptions that could indicate that the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="1319a-143">Isso pode ocorrer durante a inicialização ou o reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="1319a-143">This can happen during initialization or recognition.</span></span>

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

> [!NOTE]
> <span data-ttu-id="1319a-144">Há vários [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) predefinidos que você pode usar para otimizar o reconhecimento de fala.</span><span class="sxs-lookup"><span data-stu-id="1319a-144">There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) that you can use to optimize speech recognition.</span></span>

* <span data-ttu-id="1319a-145">Para otimizar o ditado, use o cenário de ditado.</span><span class="sxs-lookup"><span data-stu-id="1319a-145">To optimize for dictation, use the dictation scenario.</span></span><br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* <span data-ttu-id="1319a-146">Para pesquisas na Web de fala, use a seguinte restrição de cenário específica da Web.</span><span class="sxs-lookup"><span data-stu-id="1319a-146">For speech web searches, use the following web-specific scenario constraint.</span></span>

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* <span data-ttu-id="1319a-147">Use a restrição formulário para preencher formulários.</span><span class="sxs-lookup"><span data-stu-id="1319a-147">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="1319a-148">Nesse caso, é melhor aplicar sua própria gramática otimizada para preencher o formulário.</span><span class="sxs-lookup"><span data-stu-id="1319a-148">In this case, it's best to apply your own grammar that's optimized for filling out the form.</span></span>

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* <span data-ttu-id="1319a-149">Você pode fornecer sua própria gramática no formato SRGS.</span><span class="sxs-lookup"><span data-stu-id="1319a-149">You can provide your own grammar in the SRGS format.</span></span>

## <a name="use-continuous-recognition"></a><span data-ttu-id="1319a-150">Usar reconhecimento contínuo</span><span class="sxs-lookup"><span data-stu-id="1319a-150">Use continuous recognition</span></span>

<span data-ttu-id="1319a-151">Para o cenário de ditado contínuo, consulte o [exemplo de código de fala do UWP do Windows 10](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span><span class="sxs-lookup"><span data-stu-id="1319a-151">For the continuous-dictation scenario, see the [Windows 10 UWP speech code sample](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span></span>

## <a name="handle-quality-degradation"></a><span data-ttu-id="1319a-152">Lidar com a degradação da qualidade</span><span class="sxs-lookup"><span data-stu-id="1319a-152">Handle quality degradation</span></span>

<span data-ttu-id="1319a-153">Às vezes, as condições ambientais interferem no reconhecimento de fala.</span><span class="sxs-lookup"><span data-stu-id="1319a-153">Environmental conditions sometimes interfere with speech recognition.</span></span> <span data-ttu-id="1319a-154">Por exemplo, a sala pode estar muito ruidosa ou o usuário pode falar muito alto.</span><span class="sxs-lookup"><span data-stu-id="1319a-154">For example, the room might be too noisy, or the user might speak too loudly.</span></span> <span data-ttu-id="1319a-155">Sempre que possível, a API de reconhecimento de fala fornece informações sobre as condições que causaram a degradação da qualidade.</span><span class="sxs-lookup"><span data-stu-id="1319a-155">Whenever possible, the speech recognition API provides information about the conditions that caused the quality degradation.</span></span> <span data-ttu-id="1319a-156">Essas informações são enviadas por push para seu aplicativo por meio de um evento do WinRT.</span><span class="sxs-lookup"><span data-stu-id="1319a-156">This information is pushed to your app through a WinRT event.</span></span> <span data-ttu-id="1319a-157">O exemplo a seguir mostra como assinar esse evento.</span><span class="sxs-lookup"><span data-stu-id="1319a-157">The following example shows  how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="1319a-158">Em nosso exemplo de código, escrevemos as informações de condições no console de depuração.</span><span class="sxs-lookup"><span data-stu-id="1319a-158">In our code sample, we write the conditions information to the debug console.</span></span> <span data-ttu-id="1319a-159">Um aplicativo pode querer fornecer comentários ao usuário por meio da interface do usuário, síntese de fala e outro método.</span><span class="sxs-lookup"><span data-stu-id="1319a-159">An app might want to provide feedback to the user through the UI, speech synthesis, and another method.</span></span> <span data-ttu-id="1319a-160">Ou talvez seja necessário se comportar de maneira diferente quando a fala é interrompida por uma redução temporária na qualidade.</span><span class="sxs-lookup"><span data-stu-id="1319a-160">Or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

<span data-ttu-id="1319a-161">Se você não estiver usando classes de referência para criar seu aplicativo DirectX, deverá cancelar a assinatura do evento antes de liberar ou recriar seu reconhecedor de fala.</span><span class="sxs-lookup"><span data-stu-id="1319a-161">If you're not using ref classes to create your DirectX app, you must unsubscribe from the event before you release or recreate your speech recognizer.</span></span> <span data-ttu-id="1319a-162">O HolographicSpeechPromptSample tem uma rotina para parar o reconhecimento e cancelar a assinatura de eventos.</span><span class="sxs-lookup"><span data-stu-id="1319a-162">The HolographicSpeechPromptSample has a routine to stop recognition and unsubscribe from events.</span></span>

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a><span data-ttu-id="1319a-163">Usar a síntese de fala para fornecer prompts audíveis</span><span class="sxs-lookup"><span data-stu-id="1319a-163">Use speech synthesis to provide audible prompts</span></span>

<span data-ttu-id="1319a-164">Os exemplos de fala do Holographic usam a síntese de fala para fornecer instruções audíveis ao usuário.</span><span class="sxs-lookup"><span data-stu-id="1319a-164">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="1319a-165">Esta seção mostra como criar um exemplo de voz sintetizada e reproduzi-lo novamente por meio das APIs de áudio do HRTF.</span><span class="sxs-lookup"><span data-stu-id="1319a-165">This section shows how to create a synthesized voice sample  and then play it back through the HRTF audio APIs.</span></span>

<span data-ttu-id="1319a-166">Você deve fornecer seus próprios prompts de fala ao solicitar entrada de frase.</span><span class="sxs-lookup"><span data-stu-id="1319a-166">You should provide your own speech prompts when you request phrase input.</span></span> <span data-ttu-id="1319a-167">Os prompts também podem ajudar a indicar quando os comandos de fala podem ser falados para um cenário de reconhecimento contínuo.</span><span class="sxs-lookup"><span data-stu-id="1319a-167">Prompts can also help indicate when speech commands can be spoken for a continuous-recognition scenario.</span></span> <span data-ttu-id="1319a-168">O exemplo a seguir demonstra como usar um sintetizador de fala para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="1319a-168">The following example demonstrates how to use a speech synthesizer to do this.</span></span> <span data-ttu-id="1319a-169">Você também pode usar um clipe de voz previamente gravado, uma interface do usuário visual ou outro indicador do que dizer, por exemplo, em cenários em que o prompt não é dinâmico.</span><span class="sxs-lookup"><span data-stu-id="1319a-169">You could also use a pre-recorded voice clip, a visual UI, or another indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="1319a-170">Primeiro, crie o objeto SpeechSynthesizer.</span><span class="sxs-lookup"><span data-stu-id="1319a-170">First, create the SpeechSynthesizer object.</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="1319a-171">Você também precisa de uma cadeia de caracteres que inclua o texto a ser sintetizado.</span><span class="sxs-lookup"><span data-stu-id="1319a-171">You also need a string that includes the text to  synthesize.</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="1319a-172">A fala é sintetizada de forma assíncrona por meio de SynthesizeTextToStreamAsync.</span><span class="sxs-lookup"><span data-stu-id="1319a-172">Speech is synthesized asynchronously through SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="1319a-173">Aqui, iniciamos uma tarefa assíncrona para sintetizar a fala.</span><span class="sxs-lookup"><span data-stu-id="1319a-173">Here, we start an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="1319a-174">A síntese de fala é enviada como um fluxo de bytes.</span><span class="sxs-lookup"><span data-stu-id="1319a-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="1319a-175">Podemos usar esse fluxo de bytes para inicializar uma voz XAudio2.</span><span class="sxs-lookup"><span data-stu-id="1319a-175">We can use that byte stream to initialize an XAudio2 voice.</span></span> <span data-ttu-id="1319a-176">Para nossos exemplos de código Holographic, vamos reproduzi-lo como um efeito de áudio HRTF.</span><span class="sxs-lookup"><span data-stu-id="1319a-176">For our holographic code samples, we play it back as an HRTF audio effect.</span></span>

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

<span data-ttu-id="1319a-177">Assim como com o reconhecimento de fala, a síntese de fala gera uma exceção se algo der errado.</span><span class="sxs-lookup"><span data-stu-id="1319a-177">As with speech recognition, speech synthesis throws an exception if something goes wrong.</span></span>

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a><span data-ttu-id="1319a-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1319a-178">See also</span></span>
* [<span data-ttu-id="1319a-179">Design do aplicativo de fala</span><span class="sxs-lookup"><span data-stu-id="1319a-179">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="1319a-180">Exemplo de SpeechRecognitionAndSynthesis</span><span class="sxs-lookup"><span data-stu-id="1319a-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
