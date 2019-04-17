---
title: Entrada de voz no DirectX
description: Explica como implementar comandos de voz e reconhecimento de frase e frase pequeno em um aplicativo DirectX para Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: instruções passo a passo, o comando de voz, frase, reconhecimento, fala, directx, plataforma, cortana, realidade mista do windows
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591020"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="61abb-104">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="61abb-104">Voice input in DirectX</span></span>

<span data-ttu-id="61abb-105">Este tópico explica como implementar [comandos de voz](voice-input.md)e pequeno reconhecimento de frase e frase em um aplicativo DirectX para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="61abb-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="61abb-106">Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="61abb-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="61abb-107">Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.</span><span class="sxs-lookup"><span data-stu-id="61abb-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="61abb-108">Use um SpeechRecognizer para reconhecimento contínuo dos comandos de voz</span><span class="sxs-lookup"><span data-stu-id="61abb-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="61abb-109">Nesta seção, descrevemos como usar o reconhecimento de fala contínua para habilitar os comandos de voz em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61abb-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="61abb-110">Este passo a passo usa o código do [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) exemplo.</span><span class="sxs-lookup"><span data-stu-id="61abb-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="61abb-111">Ao executar o exemplo, fale o nome de um dos comandos registrados de cor para alterar a cor do cubo de rotação.</span><span class="sxs-lookup"><span data-stu-id="61abb-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="61abb-112">Primeiro, crie uma nova **Windows::Media::SpeechRecognition::SpeechRecognizer** instância.</span><span class="sxs-lookup"><span data-stu-id="61abb-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="61abb-113">Partir *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="61abb-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="61abb-114">Você precisará criar uma lista de comandos de fala do reconhecedor escutar.</span><span class="sxs-lookup"><span data-stu-id="61abb-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="61abb-115">Aqui, podemos construir um conjunto de comandos para alterar a cor de um holograma.</span><span class="sxs-lookup"><span data-stu-id="61abb-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="61abb-116">Para fins de conveniência, também criamos os dados que usaremos para os comandos mais tarde.</span><span class="sxs-lookup"><span data-stu-id="61abb-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="61abb-117">Comandos podem ser especificados usando fonéticas palavras que podem não estar em um dicionário:</span><span class="sxs-lookup"><span data-stu-id="61abb-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="61abb-118">A lista de comandos é carregada para a lista de restrições para o reconhecedor de fala.</span><span class="sxs-lookup"><span data-stu-id="61abb-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="61abb-119">Isso é feito usando um [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) objeto.</span><span class="sxs-lookup"><span data-stu-id="61abb-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="61abb-120">Assine a [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) evento em que o reconhecedor de fala [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span><span class="sxs-lookup"><span data-stu-id="61abb-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="61abb-121">Esse evento notifica seu aplicativo quando um dos seus comandos foi reconhecido.</span><span class="sxs-lookup"><span data-stu-id="61abb-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="61abb-122">Sua **OnResultGenerated** manipulador de eventos recebe dados de evento em um [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="61abb-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="61abb-123">Se a confiança é maior que o limite que você definiu, seu aplicativo deve observar que o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="61abb-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="61abb-124">Salvar os dados de evento para que você possa fazer usá-lo em um loop de atualização subsequentes.</span><span class="sxs-lookup"><span data-stu-id="61abb-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="61abb-125">Partir *HolographicVoiceInputSampleMain.cpp*:</span><span class="sxs-lookup"><span data-stu-id="61abb-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="61abb-126">Fazer uso dos dados, porém aplicáveis ao seu cenário de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61abb-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="61abb-127">Em nosso código de exemplo, podemos alterar a cor do cubo giratório holograma acordo com o comando.</span><span class="sxs-lookup"><span data-stu-id="61abb-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="61abb-128">Partir *HolographicVoiceInputSampleMain::Update*:</span><span class="sxs-lookup"><span data-stu-id="61abb-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="61abb-129">Usar ditado para propagandas reconhecimento das frases de fala e frases</span><span class="sxs-lookup"><span data-stu-id="61abb-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="61abb-130">Você pode configurar um reconhecedor de fala para escutar frases ou sentenças faladas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="61abb-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="61abb-131">Nesse caso, aplicamos um SpeechRecognitionTopicConstraint que informa o reconhecedor de fala que tipo de entrada esperar.</span><span class="sxs-lookup"><span data-stu-id="61abb-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="61abb-132">O fluxo de trabalho do aplicativo é o seguinte, para esse tipo de caso de uso:</span><span class="sxs-lookup"><span data-stu-id="61abb-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="61abb-133">Seu aplicativo cria o SpeechRecognizer, fornece prompts de interface do usuário e começa a escutar um comando a ser falado imediatamente.</span><span class="sxs-lookup"><span data-stu-id="61abb-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="61abb-134">O usuário está ligado a uma frase ou sentença.</span><span class="sxs-lookup"><span data-stu-id="61abb-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="61abb-135">Reconhecimento de fala do usuário é executado, e um resultado é retornado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61abb-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="61abb-136">Neste ponto, seu aplicativo deve fornecer um prompt de interface do usuário indicando que ocorreu o reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="61abb-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="61abb-137">Dependendo do nível de confiança que você deseja responder e o nível de confiança do resultado de reconhecimento de fala, seu aplicativo pode processar o resultado e responder conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="61abb-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="61abb-138">Esta seção descreve como criar um SpeechRecognizer, compile a restrição e escutar a entrada de fala.</span><span class="sxs-lookup"><span data-stu-id="61abb-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="61abb-139">O código a seguir compila a restrição de tópico, que nesse caso é otimizada para pesquisa na Web.</span><span class="sxs-lookup"><span data-stu-id="61abb-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="61abb-140">Se a compilação for bem-sucedida, poderemos continuar com o reconhecimento de fala.</span><span class="sxs-lookup"><span data-stu-id="61abb-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="61abb-141">O resultado é retornado, em seguida, para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61abb-141">The result is then returned to the app.</span></span> <span data-ttu-id="61abb-142">Se estamos confiantes no resultado, podemos processar o comando.</span><span class="sxs-lookup"><span data-stu-id="61abb-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="61abb-143">Este exemplo de código processa os resultados com confiança de pelo menos média.</span><span class="sxs-lookup"><span data-stu-id="61abb-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="61abb-144">Sempre que você usa o reconhecimento de fala, você deve observar de exceções que podem indicar que o usuário tenha desativado o microfone nas configurações de privacidade do sistema.</span><span class="sxs-lookup"><span data-stu-id="61abb-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="61abb-145">Isso pode acontecer durante a inicialização ou durante o reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="61abb-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="61abb-146">**OBSERVAÇÃO:** Há várias predefinidos [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) disponível para otimizar o reconhecimento de fala.</span><span class="sxs-lookup"><span data-stu-id="61abb-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="61abb-147">Se você deseja otimizar o ditado, use o cenário de ditado:</span><span class="sxs-lookup"><span data-stu-id="61abb-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="61abb-148">Ao usar a fala para realizar uma pesquisa na Web, você pode usar uma restrição ao cenário específico da Web da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="61abb-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="61abb-149">Use a restrição de formulário para preencher os formulários.</span><span class="sxs-lookup"><span data-stu-id="61abb-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="61abb-150">Nesse caso, é melhor aplicar seu próprios gramática que é otimizada para preencher o formulário.</span><span class="sxs-lookup"><span data-stu-id="61abb-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="61abb-151">Você pode fornecer seu próprio gramática usando o formato SRGS.</span><span class="sxs-lookup"><span data-stu-id="61abb-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="61abb-152">Usar comandos de fala contínua, de forma livre</span><span class="sxs-lookup"><span data-stu-id="61abb-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="61abb-153">Consulte o exemplo de código de fala do Windows 10 UWP para o cenário de ditado contínuo [aqui.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="61abb-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="61abb-154">Lidar com a redução na qualidade</span><span class="sxs-lookup"><span data-stu-id="61abb-154">Handle degradation in quality</span></span>

<span data-ttu-id="61abb-155">Condições do ambiente, às vezes, podem impedir que o reconhecimento de fala do trabalho.</span><span class="sxs-lookup"><span data-stu-id="61abb-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="61abb-156">Por exemplo, o espaço pode ser muito ruidosa ou o usuário pode falar em um volume muito alto.</span><span class="sxs-lookup"><span data-stu-id="61abb-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="61abb-157">A API de reconhecimento de fala fornece informações, sempre que possível, sobre as condições que causaram uma redução na qualidade.</span><span class="sxs-lookup"><span data-stu-id="61abb-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="61abb-158">Essa informação é enviada por push ao seu aplicativo usando um evento do WinRT.</span><span class="sxs-lookup"><span data-stu-id="61abb-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="61abb-159">Aqui está um exemplo de como assinar este evento.</span><span class="sxs-lookup"><span data-stu-id="61abb-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="61abb-160">Em nosso exemplo de código, podemos optar por gravar as informações de condições no console de depuração.</span><span class="sxs-lookup"><span data-stu-id="61abb-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="61abb-161">Um aplicativo talvez queira fornecer comentários ao usuário por meio da interface do usuário, a síntese de fala e assim por diante, ou ele talvez seja necessário ter um comportamento diferente quando a fala é interrompida por uma redução temporária na qualidade.</span><span class="sxs-lookup"><span data-stu-id="61abb-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="61abb-162">Se você não estiver usando classes de referência para criar seu aplicativo DirectX, você deve cancelar o evento antes de liberar ou recriar o reconhecedor de fala.</span><span class="sxs-lookup"><span data-stu-id="61abb-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="61abb-163">O HolographicSpeechPromptSample tem uma rotina de parar o reconhecimento e cancelar a assinatura de eventos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="61abb-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="61abb-164">Use a síntese de fala para fornecer os prompts de voz audível</span><span class="sxs-lookup"><span data-stu-id="61abb-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="61abb-165">Os exemplos de fala holográfica usam síntese de fala para fornecer instruções audíveis ao usuário.</span><span class="sxs-lookup"><span data-stu-id="61abb-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="61abb-166">Este tópico orienta o processo de criação de uma amostra de voz sintetizada e reproduzi-lo novamente usando as APIs de áudio HRTF.</span><span class="sxs-lookup"><span data-stu-id="61abb-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="61abb-167">Você deve fornecer que sua própria fala solicita ao solicitar a entrada de frase.</span><span class="sxs-lookup"><span data-stu-id="61abb-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="61abb-168">Isso também pode ser útil para indicar quando comandos de fala podem ser falados, para um cenário de reconhecimento contínuo.</span><span class="sxs-lookup"><span data-stu-id="61abb-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="61abb-169">Aqui está um exemplo de como fazer isso com um sintetizador de fala; Observe que você também pode usar uma mensagem de voz pré-gravados, uma interface do usuário visual ou outro indicador do que diga, por exemplo em cenários em que o prompt não é dinâmico.</span><span class="sxs-lookup"><span data-stu-id="61abb-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="61abb-170">Primeiro, crie o objeto SpeechSynthesizer:</span><span class="sxs-lookup"><span data-stu-id="61abb-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="61abb-171">Você também precisa de uma cadeia de caracteres com o texto a ser sintetizado:</span><span class="sxs-lookup"><span data-stu-id="61abb-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="61abb-172">Fala é sintetizada de forma assíncrona usando SynthesizeTextToStreamAsync.</span><span class="sxs-lookup"><span data-stu-id="61abb-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="61abb-173">Aqui, podemos disparar uma tarefa assíncrona para sintetizar a fala.</span><span class="sxs-lookup"><span data-stu-id="61abb-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="61abb-174">A síntese de fala é enviado como um fluxo de bytes.</span><span class="sxs-lookup"><span data-stu-id="61abb-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="61abb-175">Inicializamos uma voz XAudio2 usando esse fluxo de bytes; para nossos exemplos de código holográfica, podemos reproduzi-lo como um efeito de áudio HRTF.</span><span class="sxs-lookup"><span data-stu-id="61abb-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="61abb-176">Como com reconhecimento de fala, síntese de fala lançará uma exceção se algo der errado.</span><span class="sxs-lookup"><span data-stu-id="61abb-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="61abb-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61abb-177">See also</span></span>
* [<span data-ttu-id="61abb-178">Design de aplicativos de fala</span><span class="sxs-lookup"><span data-stu-id="61abb-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="61abb-179">Som espacial no DirectX</span><span class="sxs-lookup"><span data-stu-id="61abb-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="61abb-180">Exemplo de SpeechRecognitionAndSynthesis</span><span class="sxs-lookup"><span data-stu-id="61abb-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
