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
# <a name="voice-input-in-directx"></a>Entrada de voz no DirectX

Este tópico explica como implementar [comandos de voz](voice-input.md)e pequeno reconhecimento de frase e frase em um aplicativo DirectX para Windows Mixed Reality.

>[!NOTE]
>Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a>Use um SpeechRecognizer para reconhecimento contínuo dos comandos de voz

Nesta seção, descrevemos como usar o reconhecimento de fala contínua para habilitar os comandos de voz em seu aplicativo. Este passo a passo usa o código do [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) exemplo. Ao executar o exemplo, fale o nome de um dos comandos registrados de cor para alterar a cor do cubo de rotação.

Primeiro, crie uma nova **Windows::Media::SpeechRecognition::SpeechRecognizer** instância.

Partir *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Você precisará criar uma lista de comandos de fala do reconhecedor escutar. Aqui, podemos construir um conjunto de comandos para alterar a cor de um holograma. Para fins de conveniência, também criamos os dados que usaremos para os comandos mais tarde.

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

Comandos podem ser especificados usando fonéticas palavras que podem não estar em um dicionário:

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

A lista de comandos é carregada para a lista de restrições para o reconhecedor de fala. Isso é feito usando um [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) objeto.

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

Assine a [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) evento em que o reconhecedor de fala [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx). Esse evento notifica seu aplicativo quando um dos seus comandos foi reconhecido.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

Sua **OnResultGenerated** manipulador de eventos recebe dados de evento em um [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instância. Se a confiança é maior que o limite que você definiu, seu aplicativo deve observar que o evento ocorreu. Salvar os dados de evento para que você possa fazer usá-lo em um loop de atualização subsequentes.

Partir *HolographicVoiceInputSampleMain.cpp*:

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

Fazer uso dos dados, porém aplicáveis ao seu cenário de aplicativo. Em nosso código de exemplo, podemos alterar a cor do cubo giratório holograma acordo com o comando.

Partir *HolographicVoiceInputSampleMain::Update*:

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a>Usar ditado para propagandas reconhecimento das frases de fala e frases

Você pode configurar um reconhecedor de fala para escutar frases ou sentenças faladas pelo usuário. Nesse caso, aplicamos um SpeechRecognitionTopicConstraint que informa o reconhecedor de fala que tipo de entrada esperar. O fluxo de trabalho do aplicativo é o seguinte, para esse tipo de caso de uso:
1. Seu aplicativo cria o SpeechRecognizer, fornece prompts de interface do usuário e começa a escutar um comando a ser falado imediatamente.
2. O usuário está ligado a uma frase ou sentença.
3. Reconhecimento de fala do usuário é executado, e um resultado é retornado ao aplicativo. Neste ponto, seu aplicativo deve fornecer um prompt de interface do usuário indicando que ocorreu o reconhecimento.
4. Dependendo do nível de confiança que você deseja responder e o nível de confiança do resultado de reconhecimento de fala, seu aplicativo pode processar o resultado e responder conforme apropriado.

Esta seção descreve como criar um SpeechRecognizer, compile a restrição e escutar a entrada de fala.

O código a seguir compila a restrição de tópico, que nesse caso é otimizada para pesquisa na Web.

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

Se a compilação for bem-sucedida, poderemos continuar com o reconhecimento de fala.

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

O resultado é retornado, em seguida, para o aplicativo. Se estamos confiantes no resultado, podemos processar o comando. Este exemplo de código processa os resultados com confiança de pelo menos média.

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

Sempre que você usa o reconhecimento de fala, você deve observar de exceções que podem indicar que o usuário tenha desativado o microfone nas configurações de privacidade do sistema. Isso pode acontecer durante a inicialização ou durante o reconhecimento.

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

**OBSERVAÇÃO:** Há várias predefinidos [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) disponível para otimizar o reconhecimento de fala.
* Se você deseja otimizar o ditado, use o cenário de ditado:

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* Ao usar a fala para realizar uma pesquisa na Web, você pode usar uma restrição ao cenário específico da Web da seguinte maneira:

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* Use a restrição de formulário para preencher os formulários. Nesse caso, é melhor aplicar seu próprios gramática que é otimizada para preencher o formulário.

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* Você pode fornecer seu próprio gramática usando o formato SRGS.

## <a name="use-continuous-freeform-speech-dictation"></a>Usar comandos de fala contínua, de forma livre

Consulte o exemplo de código de fala do Windows 10 UWP para o cenário de ditado contínuo [aqui.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-degradation-in-quality"></a>Lidar com a redução na qualidade

Condições do ambiente, às vezes, podem impedir que o reconhecimento de fala do trabalho. Por exemplo, o espaço pode ser muito ruidosa ou o usuário pode falar em um volume muito alto. A API de reconhecimento de fala fornece informações, sempre que possível, sobre as condições que causaram uma redução na qualidade.

Essa informação é enviada por push ao seu aplicativo usando um evento do WinRT. Aqui está um exemplo de como assinar este evento.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

Em nosso exemplo de código, podemos optar por gravar as informações de condições no console de depuração. Um aplicativo talvez queira fornecer comentários ao usuário por meio da interface do usuário, a síntese de fala e assim por diante, ou ele talvez seja necessário ter um comportamento diferente quando a fala é interrompida por uma redução temporária na qualidade.

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

Se você não estiver usando classes de referência para criar seu aplicativo DirectX, você deve cancelar o evento antes de liberar ou recriar o reconhecedor de fala. O HolographicSpeechPromptSample tem uma rotina de parar o reconhecimento e cancelar a assinatura de eventos da seguinte forma:

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a>Use a síntese de fala para fornecer os prompts de voz audível

Os exemplos de fala holográfica usam síntese de fala para fornecer instruções audíveis ao usuário. Este tópico orienta o processo de criação de uma amostra de voz sintetizada e reproduzi-lo novamente usando as APIs de áudio HRTF.

Você deve fornecer que sua própria fala solicita ao solicitar a entrada de frase. Isso também pode ser útil para indicar quando comandos de fala podem ser falados, para um cenário de reconhecimento contínuo. Aqui está um exemplo de como fazer isso com um sintetizador de fala; Observe que você também pode usar uma mensagem de voz pré-gravados, uma interface do usuário visual ou outro indicador do que diga, por exemplo em cenários em que o prompt não é dinâmico.

Primeiro, crie o objeto SpeechSynthesizer:

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

Você também precisa de uma cadeia de caracteres com o texto a ser sintetizado:

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

Fala é sintetizada de forma assíncrona usando SynthesizeTextToStreamAsync. Aqui, podemos disparar uma tarefa assíncrona para sintetizar a fala.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

A síntese de fala é enviado como um fluxo de bytes. Inicializamos uma voz XAudio2 usando esse fluxo de bytes; para nossos exemplos de código holográfica, podemos reproduzi-lo como um efeito de áudio HRTF.

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

Como com reconhecimento de fala, síntese de fala lançará uma exceção se algo der errado.

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
* [Design de aplicativos de fala](https://msdn.microsoft.com/library/dn596121.aspx)
* [Som espacial no DirectX](spatial-sound-in-directx.md)
* [Exemplo de SpeechRecognitionAndSynthesis](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
