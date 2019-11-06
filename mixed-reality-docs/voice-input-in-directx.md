---
title: Entrada de voz no DirectX
description: Explica como implementar comandos de voz e um pequeno reconhecimento de frases e frases em um aplicativo DirectX para a realidade mista do Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Walkthrough, comando de voz, frase, reconhecimento, fala, DirectX, plataforma, Cortana, realidade do Windows Mixed
ms.openlocfilehash: 0dcfaae13f763c9b8a06910f11558d2fd8e00276
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641086"
---
# <a name="voice-input-in-directx"></a>Entrada de voz no DirectX

Este tópico explica como implementar [comandos de voz](voice-input.md)e um pequeno reconhecimento de frases e frases em um aplicativo DirectX para a realidade mista do Windows.

>[!NOTE]
>Os trechos de código neste artigo demonstram atualmente o C++uso de/CX em vez de/WinRT em C++conformidade com C + +17, conforme usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes a C++um projeto/WinRT, embora você precise converter o código.

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a>Usar um SpeechRecognizer para reconhecimento contínuo de comandos de voz

Nesta seção, descreveremos como usar o reconhecimento de fala contínuo para habilitar comandos de voz em seu aplicativo. Este passo a passos usa o código do exemplo [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) . Quando o exemplo estiver em execução, fale o nome de um dos comandos de cor registrados para alterar a cor do cubo girando.

Primeiro, crie uma nova instância do **Windows:: Media:: SpeechRecognition:: SpeechRecognizer** .

De *HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Você precisará criar uma lista de comandos de fala para o reconhecedor a ser escutado. Aqui, construímos um conjunto de comandos para alterar a cor de um holograma. Por questões de conveniência, também criamos os dados que usaremos para os comandos posteriormente.

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

Os comandos podem ser especificados usando palavras fonéticas que podem não estar em um dicionário:

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

A lista de comandos é carregada na lista de restrições para o reconhecedor de fala. Isso é feito usando um objeto [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) .

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

Assine o evento [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) no [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)do reconhecedor de fala. Esse evento notifica seu aplicativo quando um de seus comandos for reconhecido.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

O manipulador de eventos **OnResultGenerated** recebe dados de evento em uma instância [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) . Se a confiança for maior que o limite definido, seu aplicativo deverá observar que o evento ocorreu. Salve os dados do evento para que você possa usá-los em um loop de atualização subsequente.

De *HolographicVoiceInputSampleMain. cpp*:

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

No entanto, use os dados aplicáveis ao cenário do aplicativo. Em nosso código de exemplo, alteramos a cor do cubo de holograma girando de acordo com o comando do usuário.

De *HolographicVoiceInputSampleMain:: Update*:

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a>Use o ditado para reconhecimento único de frases e sentenças de fala

Você pode configurar um reconhecedor de fala para ouvir frases ou frases faladas pelo usuário. Nesse caso, aplicamos um SpeechRecognitionTopicConstraint que informa ao reconhecedor de fala o tipo de entrada a ser esperado. O fluxo de trabalho do aplicativo é o seguinte para este tipo de caso de uso:
1. Seu aplicativo cria o SpeechRecognizer, fornece prompts de interface do usuário e começa a escutar que um comando seja falado imediatamente.
2. O usuário fala uma frase ou frase.
3. O reconhecimento da fala do usuário é executado e um resultado é retornado para o aplicativo. Neste ponto, seu aplicativo deve fornecer um prompt da interface do usuário indicando que o reconhecimento ocorreu.
4. Dependendo do nível de confiança que você deseja responder e do nível de confiança do resultado do reconhecimento de fala, seu aplicativo poderá processar o resultado e responder conforme apropriado.

Esta seção descreve como criar um SpeechRecognizer, compilar a restrição e ouvir a entrada de fala.

O código a seguir compila a restrição de tópico, que nesse caso é otimizada para pesquisa na Web.

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

Se a compilação for realizada com sucesso, podemos continuar com o reconhecimento de fala.

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

O resultado é retornado para o aplicativo. Se tivermos confiança suficiente no resultado, poderemos processar o comando. Este exemplo de código processa resultados com pelo menos confiança média.

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

Sempre que usar o reconhecimento de fala, você deve observar as exceções que podem indicar que o usuário desativou o microfone nas configurações de privacidade do sistema. Isso pode ocorrer durante a inicialização ou durante o reconhecimento.

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

**Observação:** Há vários [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) predefinidos disponíveis para otimizar o reconhecimento de fala.
* Se você quiser otimizar para o ditado, use o cenário de ditado:

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* Ao usar a fala para executar uma pesquisa na Web, você pode usar uma restrição de cenário específica da Web da seguinte maneira:

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* Use a restrição formulário para preencher formulários. Nesse caso, é melhor aplicar sua própria gramática otimizada para preencher o formulário.

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* Você pode fornecer sua própria gramática usando o formato SRGS.

## <a name="use-continuous-freeform-speech-dictation"></a>Usar ditado de fala de forma livre contínua

Consulte o exemplo de código de fala do Windows 10 UWP para o cenário de ditado contínuo [aqui.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-degradation-in-quality"></a>Tratar a degradação na qualidade

Às vezes, as condições no ambiente podem impedir que o reconhecimento de fala funcione. Por exemplo, a sala pode estar muito ruidosa ou o usuário pode falar em um volume muito alto. A API de reconhecimento de fala fornece informações, quando possível, sobre condições que causaram uma degradação na qualidade.

Essas informações são enviadas por push para seu aplicativo usando um evento do WinRT. Aqui está um exemplo de como assinar esse evento.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

Em nosso exemplo de código, optamos por gravar as informações de condições no console de depuração. Um aplicativo pode querer fornecer comentários para o usuário por meio da interface de usuário, síntese de fala e assim por diante, ou talvez precise se comportar de forma diferente quando a fala é interrompida por uma redução temporária na qualidade.

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

Se você não estiver usando classes de referência para criar seu aplicativo do DirectX, deverá cancelar a assinatura do evento antes de liberar ou recriar seu reconhecedor de fala. O HolographicSpeechPromptSample tem uma rotina para parar o reconhecimento e cancelar a assinatura de eventos como este:

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a>Usar a síntese de fala para fornecer prompts de voz audíveis

Os exemplos de fala do Holographic usam a síntese de fala para fornecer instruções audíveis ao usuário. Este tópico percorre o processo de criação de um exemplo de voz sintetizado e sua reprodução usando as APIs de áudio HRTF.

Você deve fornecer seus próprios prompts de fala ao solicitar entrada de frase. Isso também pode ser útil para indicar quando os comandos de fala podem ser falados, para um cenário de reconhecimento contínuo. Aqui está um exemplo de como fazer isso com um sintetizador de fala; Observe que você também pode usar um clipe de voz previamente gravado, uma interface do usuário visual ou outro indicador do que dizer, por exemplo, em cenários em que o prompt não é dinâmico.

Primeiro, crie o objeto SpeechSynthesizer:

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

Você também precisa de uma cadeia de caracteres com o texto a ser sintetizado:

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

A fala é sintetizada de forma assíncrona usando SynthesizeTextToStreamAsync. Aqui, começamos uma tarefa assíncrona para sintetizar a fala.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

A síntese de fala é enviada como um fluxo de bytes. Podemos inicializar uma voz XAudio2 usando esse fluxo de bytes; para nossos exemplos de código Holographic, vamos reproduzi-lo como um efeito de áudio HRTF.

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

Assim como no reconhecimento de fala, a síntese de fala gerará uma exceção se algo der errado.

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

## <a name="see-also"></a>Consulte também
* [Design do aplicativo de fala](https://msdn.microsoft.com/library/dn596121.aspx)
* [Exemplo de SpeechRecognitionAndSynthesis](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
