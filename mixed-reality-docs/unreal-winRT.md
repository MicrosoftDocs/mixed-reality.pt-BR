---
title: WinRT no Unreal
description: Visão geral do plug-in de áudio espacial do Unreal Engine.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, remoting, mixed reality, development, getting started, features, new project, emulator, documentation, guides, features, holograms, game development
ms.openlocfilehash: 7a64002a5fa48bb589ab113f0a8dc1bfcb92d535
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408214"
---
# <a name="winrt-in-unreal"></a>WinRT no Unreal

## <a name="overview"></a>Visão geral

Ao longo do desenvolvimento do seu HoloLens, talvez seja necessário escrever um recurso usando o WinRT. Por exemplo, abrir uma caixa de diálogo de arquivo em um aplicativo HoloLens precisaria do FileSavePicker no arquivo de cabeçalho winrt/Windows. Storage....  Como inreal não compila nativamente o código WinRT, é seu trabalho criar um binário separado e que pode ser consumido pelo sistema de compilação não real. Este tutorial guiará você pelo cenário desse tipo.

## <a name="objectives"></a>Objetivos
- Criar uma DLL universal do Windows que abre um FileSaveDialogue
- Vincular essa DLL a um projeto de jogo não real
- Salvar um arquivo no HoloLens de um projeto não real usando a nova DLL

## <a name="getting-started"></a>Introdução
1. Verifique se você tem todas as [ferramentas necessárias](unreal-uxt-ch1.md) instaladas
2. [Criar um novo projeto inreal](unreal-uxt-ch2.md#creating-a-new-unreal-project) e nomeá-lo **Consumewinrt**
3. Habilitar os [plug-ins necessários](unreal-uxt-ch2.md#enabling-required-plugins) para o desenvolvimento do HoloLens
4. [Configuração para implantação](unreal-uxt-ch6.md) em um dispositivo ou emulador

## <a name="creating-a-winrt-dll"></a>Criando uma DLL do WinRT 
1. Abra um novo projeto do Visual Studio e crie um projeto **dll (universal do Windows)** no mesmo diretório para o arquivo **uproject** do jogo inreal. 

![Criando uma DLL](images/unreal-winrt-img-01.png)

2. Nomeie o projeto **HoloLensWinrtDLL** e defina o local como um subdiretório **ThirdParty** para o arquivo uproject do jogo inreal. 
    * Selecione **posicionar solução e projeto no mesmo diretório** para simplificar a procura de caminhos mais tarde. 

![Configurando a DLL](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> Depois que o novo projeto é compilado, você deseja prestar atenção especial aos arquivos cpp e de cabeçalho em branco, chamados **HoloLensWinrtDLL. cpp** e **HoloLensWinrtDLL. h** , respectivamente. O cabeçalho é o arquivo de inclusão que usa a DLL em tempo real, enquanto a cpp mantém o corpo de todas as funções que você exporta e inclui qualquer código do WinRT que não seja possível compilar de outra forma. 

3. Antes de adicionar qualquer código, você precisa atualizar as propriedades do projeto para garantir que o código do WinRT que você precisa pode compilar: 
    * Clique com o botão direito do mouse no projeto HoloLensWinrtDLL e selecione **Propriedades**  
    * Alterar a lista suspensa de **configuração** para **todas as configurações** e a lista suspensa de **plataforma** para **todas as plataformas**  
    * Em **Propriedades de configuração> C/C++> todas as opções**:
        * Adicionar **Await** a **Opções adicionais** para garantir que possamos aguardar em tarefas assíncronas  
        * Alterar o **padrão de linguagem C++** para **ISO C++ 17 Standard (/std: C++ 17)** para incluir qualquer código do WinRT

![Configurando a DLL](images/unreal-winrt-img-03.png)

Seu projeto está pronto para atualizar a origem da DLL com o código do WinRT que abre uma caixa de diálogo de arquivo e salva um arquivo no disco do HoloLens.  

## <a name="adding-the-dll-code"></a>Adicionando o código DLL
1. Abra **HoloLensWinrtDLL. h** e adicione uma função exportada de dll para consumir inrealmente: 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. Abra **HoloLensWinrtDLL. cpp** e adicione todos os cabeçalhos que a classe usará:  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> Todo o código do WinRT é armazenado em **HoloLensWinrtDLL. cpp** , de modo que não tente incluir nenhum código do winrt ao referenciar o cabeçalho. 

3. Ainda em **HoloLensWinrtDLL. cpp**, adicione um corpo de função para OpenFileDialogue () e todo o código com suporte: 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. Adicione uma classe SaveGameManager a **HoloLensWinrtDLL. cpp** para manipular a caixa de diálogo do arquivo e salvar o arquivo: 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullprt);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. Compile a solução para a **versão > ARM64** para criar a dll para o diretório filho ARM64/Release/HoloLensWinrtDLL da solução de dll. 

## <a name="adding-the-winrt-binary-to-unreal"></a>Adicionar o binário do WinRT a um não real 
Vincular e usar uma DLL em um Unreal requer um projeto C++. Se você estiver usando um projeto Blueprint, ele poderá ser facilmente convertido em um projeto C++ adicionando uma classe C++:  

1. No editor inreal, abra **arquivo > nova classe C++...** e crie um novo **ator** chamado **WinrtActor** para executar o código na DLL: 

![Configurando a DLL](images/unreal-winrt-img-04.png)

> [!NOTE]
> Agora, uma solução foi criada no mesmo diretório que o arquivo uproject, juntamente com um novo script de compilação chamado source/ConsumeWinRT/ConsumerWinRT. Build. cs.

2. Abra a solução, procure a pasta **Games/ConsumeWinRT/origem/ConsumeWinRT** e abra **ConsumeWinRT.Build.cs**:

![Configurando a DLL](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>Vinculando a DLL
1. Em **ConsumeWinRT.Build.cs**, adicione uma propriedade para localizar o caminho de inclusão para a dll (o diretório que contém HoloLensWinrtDLL. h). A DLL está em um diretório filho para o caminho de inclusão, portanto, essa propriedade será usada como a dir raiz binária:

```cs
public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirddParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. No construtor de classe, adicione o seguinte código para atualizar o caminho de inclusão, vincular a nova lib e atrasar o carregamento e copiar a DLL para o local Appx empacotado:

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. Abra **WinrtActor. h** e adicione duas definições de função, uma que o plano gráfico pode usar e outra que use o código de dll: 
```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue;
```

4. Abra **WinrtActor. cpp** e carregue a dll em BeginPlay: 

```cpp
void AWinfrtActor::BeginPlay()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> A DLL deve ser carregada antes de chamar qualquer uma de suas funções.

### <a name="building-the-game"></a>Criando o jogo
1. Crie a solução de jogos para iniciar o editor inreal aberto no projeto de jogo: 
    * Na guia **local atores** , pesquise o novo **WinrtActor** e arraste-o para a cena 
    * Abra o Blueprint de nível para executar a função que tem o plano de execução no **WinrtActor** 

![Configurando a DLL](images/unreal-winrt-img-06.png)

2. Na estrutura **mundial**, encontre o **WindrtActor** que foi previamente colocado na cena e arraste-o para o plano Blueprint: 

![Configurando a DLL](images/unreal-winrt-img-07.png)

3. No nível Blueprint, arraste o nó saída de WinrtActor, procure a **caixa de diálogo abrir arquivo**e, em seguida, encaminhe o nó de qualquer entrada do usuário.  Nesse caso, a caixa de diálogo abrir arquivo está sendo chamada de um evento de fala: 

![Configurando a DLL](images/unreal-winrt-img-08.png)

4. [Empacote este jogo para o HoloLens](unreal-uxt-ch6.md), implante-o e execute-o.  

Quando as chamadas inreais OpenFileDialogue, uma caixa de diálogo de arquivo é aberta no HoloLens solicitando um nome de arquivo. txt.  Depois que o arquivo for salvo, vá para a guia **Explorador de arquivos** no portal do dispositivo para ver o conteúdo "Olá WinRT". 

## <a name="summary"></a>Resumo 

Incentivamos você a usar o código neste tutorial como um ponto de partida para consumir o código do WinRT em um estado inreal.  Ele permite que os usuários salvem arquivos no disco do HoloLens usando a mesma caixa de diálogo de arquivo que o Windows.  Siga o mesmo processo para exportar funções adicionais do cabeçalho HoloLensWinrtDLL e usadas em um não real.  Observe o código de DLL que aguarda em qualquer código assíncrono do WinRT em um thread MTA de segundo plano, que evita o deadlock do thread de jogo inreal. 

## <a name="see-also"></a>Confira também
* [APIs do C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [Classe FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Bibliotecas de terceiros inreais](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
