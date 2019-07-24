---
title: OpenXR
description: Experimente a API provisional OpenXR 0,90 com a realidade misturada OpenXR Developer Preview.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Visualização da realidade misturada do OpenXR Developer
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039177"
---
# <a name="openxr"></a>OpenXR

O OpenXR é um padrão aberto isento de royalties da [Khronos](https://www.khronos.org/) que fornece acesso nativo a uma ampla gama de dispositivos de muitos fornecedores que abrangem o [espectro de realidade misturada](mixed-reality.md).

Com o OpenXR, você pode criar aplicativos destinados a dispositivos Holographic (como o HoloLens 2) que colocam o conteúdo digital no mundo real como se estivesse realmente lá, bem como dispositivos de imersão (como o Windows Mixed realness headsets para PCs Desktop) que ocultam o mundo físico e substitua-o por uma experiência digital.  O OpenXR permite que você escreva código depois de ser portátil em uma ampla gama de plataformas de hardware.

Atualmente, o OpenXR Standard está em uma fase provisionada, com uma especificação inicial de OpenXR 0,90 lançada para comentários.  Para obter mais informações sobre OpenXR, incluindo o acesso à especificação e aos [cabeçalhos](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)de [0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) provisionos, consulte a [página OpenXR do Khronos](https://www.khronos.org/openxr/). 

Você pode experimentar a API OpenXR 0,90 provisionada em um HoloLens 2 ou em um PC desktop usando o OpenXR Developer preview da realidade misturada.  Esse tempo de execução inicial permite que os aplicativos direcionados à API do OpenXR 0,90 para direcionar headsets de imersão de realidade 2 ou Windows misto na área de trabalho.

Se você não tiver acesso a um headset, poderá usar o emulador do HoloLens 2 ou o simulador de realidade mista do Windows.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>Configurando a realidade misturada do OpenXR Developer Preview para o HoloLens 2

Para começar a usar o Mixed Reality OpenXR Developer Preview no HoloLens 2:

1. Configure um HoloLens 2 ou siga as instruções para [instalar o emulador do HoloLens 2](using-the-hololens-emulator.md).
1. Inicie o aplicativo da loja de dentro do dispositivo ou emulador e verifique se todos os aplicativos estão atualizados.  Isso instalará o Mixed Reality OpenXR Developer Preview para uso com aplicativos nesse dispositivo.  Se estiver usando o emulador, você desejará consultar as [instruções de entrada](using-the-hololens-emulator.md#basic-emulator-input) do emulador para ajudá-lo a usar o aplicativo da loja dentro do emulador.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>Configurando a realidade misturada do OpenXR Developer Preview para imersivas de área de trabalho de imersão

Para começar a usar o Mixed Reality OpenXR Developer preview em um PC desktop:

1. Verifique se você está executando a atualização do Windows 10 de outubro de 2018 (1809) ou a atualização do Windows 10 de maio de 2019 (1903).  Se você estiver em uma versão anterior do Windows 10, poderá atualizar para a atualização de maio de 2019 usando o [Assistente de atualização do Windows 10](https://www.microsoft.com/en-us/software-download/windows10).
1. Configure um headset de realidade mista do Windows ou siga as instruções para [habilitar o simulador de realidade mista do Windows](using-the-windows-mixed-reality-simulator.md).
1. Instale o [aplicativo Mixed Reality OpenXR Developer Preview](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Este aplicativo o ajudará a configurar com o tempo de execução da visualização OpenXR no Windows 10 de outubro de 2018 atualização (1809) ou posterior.  Depois de instalar esse aplicativo, a Windows Store manterá o tempo de execução atualizado.
1. Execute o aplicativo Mixed Reality OpenXR Developer Preview no menu iniciar e siga as instruções para tornar o tempo de execução ativo.  Em breve, esse aplicativo permitirá que você explore outras informações de depuração do OpenXR também.

![Aplicativo Mixed Reality OpenXR Developer Preview](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>Suporte para atualização do Windows 10 de outubro de 2018

Se você estiver executando o Windows 10 pode 2019 atualização (1903) e seguiu as etapas acima, você deve estar pronto para usar a realidade mista do OpenXR Developer Preview!

Se você não estiver pronto para [atualizar seu PC desktop para a atualização de maio de 2019](https://www.microsoft.com/en-us/software-download/windows10), poderá começar a usar a atualização do Windows 10 de outubro de 2018 (1809) seguindo mais uma etapa:

1. Siga as etapas acima para instalar o Mixed Reality OpenXR Developer Preview.
1. Para definir a realidade mista do OpenXR Developer Preview como o tempo de execução do OpenXR do seu sistema, instale o [pacote de compatibilidade da visualização do desenvolvedor do OpenXR](https://aka.ms/openxr-compat)do informativo misto.

## <a name="building-a-sample-openxr-app"></a>Criando um aplicativo OpenXR de exemplo

O projeto [BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) demonstra um exemplo de OpenXR simples com dois arquivos de projeto do Visual Studio, um para um aplicativo de área de trabalho Win32 e outro para um aplicativo UWP HoloLens 2.  Como a solução contém um projeto UWP do HoloLens, você precisará do [plataforma universal do Windows carga de trabalho de desenvolvimento](install-the-tools.md#installation-checklist) instalada no Visual Studio para abri-lo totalmente.

Observe que, embora os arquivos de projeto Win32 e UWP sejam separados devido a diferenças no empacotamento e na implantação, o código do aplicativo dentro de cada projeto é de 100% o mesmo!

## <a name="feedback"></a>Comentários

Para fornecer comentários sobre a [especificação do OpenXR Provision 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), visite os [fóruns do Khronos OpenXR](https://community.khronos.org/c/openxr), a [margem de atraso #openxr canal](https://khr.io/slack) e o rastreador de [problemas de especificação](https://github.com/KhronosGroup/OpenXR-Docs/issues).

## <a name="troubleshooting"></a>Solução de problemas

Aqui estão algumas dicas de solução de problemas para a realidade misturada do OpenXR Developer Preview.  Se você estiver atingindo outros problemas, visite os [fóruns do Khronos OpenXR](https://community.khronos.org/c/openxr) ou a [margem de atraso #openxr canal](https://khr.io/slack).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>O aplicativo OpenXR não está iniciando a realidade mista do Windows

Se seu aplicativo OpenXR não estiver iniciando a realidade mista do Windows quando você executá-lo, a visualização misturada da realidade do OpenXR Developer não poderá ser definida como o tempo de execução ativo.  Certifique-se de executar o aplicativo Mixed Reality OpenXR Developer Preview e siga as instruções para tornar o tempo de execução ativo.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>O aplicativo OpenXR Developer Preview misto não pode ser instalado 

Verifique se você está executando pelo menos a atualização de 10 de outubro de 2018 do Windows (1809).  Se você estiver em uma versão anterior do Windows 10, poderá atualizar para a atualização de maio de 2019 (1903) usando o [Assistente de atualização do Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Se o botão instalar no aplicativo Mixed Reality OpenXR Developer Preview não faz nada na atualização do Windows 10 de outubro de 2018, seu sistema pode ter requisitos de sistema obsoletos em cache para o aplicativo.  Você pode executar o comando `wsreset.exe` de um prompt de comando para limpar o cache.

## <a name="see-also"></a>Consulte também

* [Mais informações sobre o OpenXR](https://www.khronos.org/openxr/)
* [Especificação OpenXR provisiony 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [Referência de API OpenXR provisional 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [Cabeçalhos OpenXR Provision 0,90](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [Guia de referência rápida do OpenXR Provisioning 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
