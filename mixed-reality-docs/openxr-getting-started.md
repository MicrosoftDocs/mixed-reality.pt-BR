---
title: Introdução ao OpenXR
description: Comece a usar o padrão de API OpenXR portátil no Windows Mixed Reality e o fone de ouvido 2 do HoloLens.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Windows Mixed Reality OpenXR Ferramentas para Desenvolvedores, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, introdução, 101, extensões de visualização, versão de tempo de execução do OpenXR, status do sistema
ms.openlocfilehash: e09ff2748921789d74bafdb321f19882336ea500
ms.sourcegitcommit: 3c32f45fd941767d408cccc5a76f1ff1cec763da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86879211"
---
# <a name="getting-started-with-openxr"></a>Introdução ao OpenXR

Você pode desenvolver usando OpenXR em um headset de imersão de realidade 2 ou Windows misto na área de trabalho.  Se você não tiver acesso a um headset, poderá usar o emulador do HoloLens 2 ou o simulador de realidade mista do Windows.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introdução ao OpenXR para o HoloLens 2

Para começar a desenvolver aplicativos OpenXR para o HoloLens 2:

1. Configure um HoloLens 2 ou siga as instruções para [instalar uma versão recente do emulador do HoloLens 2](using-the-hololens-emulator.md).  Se o seu dispositivo atualizou seu sistema operacional recentemente ou se você estiver usando uma imagem de emulador recente, você já deve ter o OpenXR 1,0 pronto para começar.
1. Para verificar se você tem o tempo de execução OpenXR mais recente com todas as [extensões](openxr.md#roadmap) presentes, inicie o aplicativo da **loja** de dentro do dispositivo ou emulador, abra o menu no canto superior direito, clique em **downloads e atualizações** e clique em **obter atualizações**.  Isso garante que o tempo de execução do OpenXR em seu HoloLens esteja atualizado.  Observe que, se você estiver usando o emulador, a imagem do emulador será redefinida sempre que você iniciá-la e, portanto, sua melhor aposta é apenas verificar se você tem [a versão mais recente da imagem do emulador do HoloLens 2](using-the-hololens-emulator.md).

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introdução ao OpenXR for Windows Mixed realness headsets

Para começar a desenvolver aplicativos OpenXR para headsets de imersão misturadas do Windows:

1. Verifique se você está executando pelo menos o Windows 10 pode 2019 atualização (1903), que é o requisito mínimo para que os usuários finais da realidade mista do Windows executem aplicativos OpenXR.  Se você estiver em uma versão anterior do Windows 10, poderá atualizar usando o assistente de <a href="https://www.microsoft.com/software-download/windows10" target="_blank">atualização do Windows 10</a>.
2. Configure um headset de realidade mista do Windows ou siga as instruções para [habilitar o simulador de realidade mista do Windows](using-the-windows-mixed-reality-simulator.md).

É isso!  O tempo de execução do Windows Mixed Reality OpenXR é instalado e torna-se ativo automaticamente para todos os usuários do Windows Mixed Reality.  O Microsoft Store mantém o tempo de execução atualizado.

Se você precisar tornar o tempo de execução do Windows Mixed Reality OpenXR ativo novamente, inicie o portal de realidade misturada no menu Iniciar, clique no botão... no canto inferior esquerdo e selecione "configurar OpenXR".  Se esse item de menu estiver ausente, o tempo de execução do OpenXR já estará ativo.<br>
![Configurando o OpenXR no portal de realidade misturada](images/mixed-reality-portal-set-up-openxr.png)

## <a name="getting-the-windows-mixed-reality-openxr-developer-tools"></a>Obtendo o OpenXR da realidade mista do Windows Ferramentas para Desenvolvedores

Para experimentar o tempo de execução do Windows Mixed Reality OpenXR, você pode instalar o <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">aplicativo OpenXR ferramentas para desenvolvedores de realidade misturada</a>.  Esse aplicativo fornece uma cena de demonstração que exercita vários recursos do OpenXR, juntamente com uma página de status do sistema que fornece informações importantes sobre o tempo de execução ativo e o headset atual.

Se estiver usando o emulador do HoloLens 2, a maneira mais fácil de instalar a realidade misturada OpenXR Ferramentas para Desenvolvedores está usando o [portal de dispositivo do Windows](using-the-windows-device-portal.md), navegando até a página "OpenXR" e clicando no botão "instalar" em "recursos do desenvolvedor". (isso funciona em um dispositivo físico do HoloLens 2 também)

![Aplicativo OpenXR Ferramentas para Desenvolvedores de realidade misturada](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Criando um aplicativo OpenXR de exemplo

Certifique-se de [instalar as ferramentas](install-the-tools.md) necessárias para o desenvolvimento do OpenXR, caso ainda não tenha feito isso.

O projeto <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> demonstra um exemplo de OpenXR simples com dois arquivos de projeto do Visual Studio, um para um aplicativo da área de trabalho Win32 e outro para um aplicativo HoloLens 2 da UWP.  Como a solução contém um projeto UWP do HoloLens, você precisará do [plataforma universal do Windows carga de trabalho de desenvolvimento](install-the-tools.md#installation-checklist) instalada no Visual Studio para abri-lo totalmente.

Observe que, embora os arquivos de projeto Win32 e UWP sejam separados devido a diferenças no empacotamento e na implantação, o código do aplicativo dentro de cada projeto é quase exatamente o mesmo!

Depois de criar uma área de trabalho do Win32 do OpenXR. EXE, você pode usá-lo com um headset de VR em qualquer plataforma de VR de área de trabalho que dê suporte a OpenXR, seja um headset de realidade mista do Windows ou qualquer outro headset.

Depois de criar um pacote de aplicativo OpenXR UWP, você pode [implantar esse pacote](using-visual-studio.md) em um dispositivo do hololens 2 ou no emulador do hololens 2.

## <a name="integrate-the-openxr-loader-into-a-project"></a>Integrar o carregador do OpenXR a um projeto

Para começar a usar o OpenXR em um projeto existente, você incluirá o carregador do OpenXR.  O carregador descobre o tempo de execução do OpenXR ativo no dispositivo e fornece acesso às funções principais e às funções de extensão que ele implementa.

Você pode [fazer referência ao pacote OpenXR do NuGet oficial](#reference-official-openxr-nuget-package) do seu projeto do Visual Studio ou [incluir a origem do carregador OpenXR oficial](#include-official-openxr-loader-source) do repositório GitHub do Khronos.  Qualquer uma das abordagens fornecerá acesso aos recursos principais do OpenXR 1,0, mais publicados `KHR` `EXT` e `MSFT` extensões.

Se você estiver interessado em experimentar `MSFT_preview` extensões também, poderá [copiar os cabeçalhos de OpenXR de visualização](#using-preview-extensions) do repositório GitHub de realidade misturada.

### <a name="reference-official-openxr-nuget-package"></a>OpenXR pacote NuGet oficial de referência

O <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank">pacote NuGet **OpenXR. Loader** </a> é a maneira mais fácil de fazer referência a um carregador OpenXR pré-criado. DLL em sua solução do Visual Studio C++.  Isso dará acesso aos recursos principais do OpenXR 1,0, mais publicados `KHR` `EXT` e `MSFT` extensões.

Para adicionar uma referência de pacote NuGet OpenXR. Loader à sua solução do Visual Studio C++:
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto que usará OpenXR e selecione **gerenciar pacotes NuGet...**.
1. Alterne para a guia **procurar** e procure **OpenXR. Loader**.
1. Selecione o pacote **OpenXR. Loader** e clique em instalar no painel de detalhes à direita.
1. Clique em OK para aceitar as alterações em seu projeto.
1. Adicione `#include <openxr/openxr.h>` a um arquivo de origem para começar a usar a API OpenXR.

Para ver um exemplo da API OpenXR em ação, confira o aplicativo de exemplo <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> .

### <a name="include-official-openxr-loader-source"></a>Incluir origem do carregador de OpenXR oficial

Se você quiser criar o carregador por conta própria, por exemplo, para evitar o carregador extra. DLL, você pode extrair as fontes oficiais do Khronos OpenXR Loader para seu projeto.  Isso dará acesso aos recursos principais do OpenXR 1,0, mais publicados `KHR` `EXT` e `MSFT` extensões.

Para começar aqui, siga as instruções no <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">repositório Khronos OpenXR-SDK no GitHub</a>.  O projeto é configurado para compilar com CMake-se você estiver usando o MSBuild, será necessário copiar para o código em seu próprio projeto.

## <a name="using-preview-extensions"></a>Usando extensões de visualização

As `MSFT_preview` extensões listadas no [roteiro de extensão](openxr.md#roadmap) são extensões experimentais do fornecedor sendo visualizadas para coletar comentários.  Essas extensões são apenas para dispositivos de desenvolvedor e serão removidas quando a extensão real for entregue.

Se você estiver interessado em experimentar as extensões disponíveis `MSFT_preview` , siga as etapas a seguir para atualizar seu projeto:
1. Siga uma das abordagens acima para integrar um carregador de OpenXR ao seu projeto.
1. Substitua os cabeçalhos OpenXR padrão em seu projeto pelos <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">cabeçalhos de visualização do repositório OpenXR da realidade misturada no GitHub</a>.

Para ativar o suporte de extensão de visualização no seu PC de destino 2 ou computador desktop:
  1. Para verificar se você tem o tempo de execução OpenXR mais recente com todas as [extensões](openxr.md#roadmap) presentes, inicie o aplicativo da **loja** de dentro do dispositivo ou emulador de destino, abra o menu no canto superior direito, clique em **downloads e atualizações** e clique em **obter atualizações**.
  1. Habilitar o portal de dispositivos do Windows no dispositivo de destino:
     * Se o dispositivo de destino for um dispositivo de HoloLens 2, [siga estas instruções](using-the-windows-device-portal.md) no dispositivo de destino.  Observe que isso requer um headset físico, uma vez que um problema conhecido no emulador do HoloLens 2 impedirá que a interface do usuário na próxima etapa apareça no emulador.
     * Se o seu dispositivo de destino for um PC desktop com um fone de ouvido de imersão anexado, <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop#set-up-device-portal-on-windows-desktop" target="_blank">siga estas instruções</a> no computador desktop de destino.
  1. Navegue até a guia **OpenXR** no painel esquerdo e habilite **usar o tempo de execução do OpenXR de visualização mais recente**.  Isso habilita o tempo de execução de visualização em seu dispositivo, que tem extensões de visualização ativadas.
     ![Caixa de seleção tempo de execução do portal do dispositivo OpenXR Preview](images/device-portal-openxr-preview-runtime.png)
  1. Confirme se a **versão de tempo de execução** mostrada na guia **status do sistema** do [Windows Mixed Reality OpenXR ferramentas para desenvolvedores](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) agora corresponde à versão necessária das extensões de visualização que você planeja experimentar.  Nesse caso, você deve ver a extensão na lista de **extensões** .  Observe que, uma vez que uma extensão estável está disponível, sua extensão de visualização será removida.<br />
     ![OpenXR de realidade misturada Ferramentas para Desenvolvedores guia status do sistema de aplicativo](images/mixed-reality-openxr-developer-tools-status.png)

Consulte o <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">repositório OpenXR de realidade misturada</a> para obter a documentação dessas extensões de visualização e exemplos de como usá-las.

## <a name="troubleshooting"></a>Solução de problemas

Se você tiver problemas para entrar em funcionamento com o desenvolvimento do OpenXR, confira nossas [dicas de solução de problemas](openxr-troubleshooting.md).