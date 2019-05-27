---
title: OpenXR
description: Experimente a API OpenXR 0,90 provisional com a visualização do desenvolvedor de OpenXR realidade mista.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Realidade misturada OpenXR Developer Preview
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039177"
---
# <a name="openxr"></a>OpenXR

OpenXR é um padrão aberto de royalties partir [Khronos](https://www.khronos.org/) que fornece acesso nativo a uma ampla variedade de dispositivos de vários fornecedores que se estendem pela [espectro de realidade misturada](mixed-reality.md).

Com OpenXR, você pode criar aplicativos que se destinam a tanto holográfico dispositivos (como o HoloLens 2) que colocam conteúdo digital no mundo real, como se estivesse lá, bem como imersivos dispositivos (como Windows Mixed Reality headsets para computadores desktops) que ocultam o mundo físico e substituí-lo com uma experiência digital.  OpenXR permite escrever código depois que o que é portátil entre uma ampla variedade de plataformas de hardware.

O padrão de OpenXR está atualmente em uma fase provisória, com uma especificação de OpenXR 0,90 inicial lançada para comentários.  Para obter mais informações sobre OpenXR, incluindo o acesso à [provisória spec 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) e [cabeçalhos](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), consulte a [Khronos OpenXR página](https://www.khronos.org/openxr/). 

Você pode experimentar a API OpenXR 0,90 provisória em 2 um HoloLens ou um PC desktop usando a visualização do desenvolvedor de OpenXR realidade mista.  Esse tempo de execução inicial permite que aplicativos visando a API OpenXR 0,90 HoloLens 2 ou Windows Mixed Reality fones imersivos em exposição na área de trabalho de destino.

Se você não tiver acesso a um fone de ouvido, você pode usar o emulador de 2 HoloLens ou o simulador de realidade mista do Windows em vez disso.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>Configurando a visualização do desenvolvedor de OpenXR realidade mista para HoloLens 2

Para começar com a visualização de desenvolvedores de OpenXR realidade mista em HoloLens 2:

1. Configurar um 2 HoloLens ou siga as instruções para [instalar o emulador do HoloLens 2](using-the-hololens-emulator.md).
1. Inicie o aplicativo Store no dispositivo ou emulador e garantir que todos os aplicativos são atualizados.  Isso instalará o misto realidade OpenXR Developer Preview para uso com aplicativos no dispositivo.  Se usar o emulador, você desejará consultar os [instruções de entrada do emulador](using-the-hololens-emulator.md#basic-emulator-input) para ajudá-lo a usar o aplicativo da Store no emulador.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>Como configurar a visualização do desenvolvedor OpenXR misto realidade para fones imersivos em exposição da área de trabalho

Para começar com a visualização de desenvolvedores de OpenXR realidade mista em um PC desktop:

1. Certifique-se de que você está executando o Windows 10 de outubro de 2018 Update (1809) ou o Windows 10 podem 2019 atualizar (1903).  Se você estiver em uma versão anterior do Windows 10, você pode atualizar para o de maio de 2019 atualizar usando o [Assistente de atualização do Windows 10](https://www.microsoft.com/en-us/software-download/windows10).
1. Configurar um headset de realidade mista do Windows ou siga as instruções para [habilitar o simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md).
1. Instalar o [realidade misturada OpenXR desenvolvedor visualize o aplicativo](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Este aplicativo obtém que você configurou com o tempo de execução OpenXR preview no Windows 10 de outubro de 2018 Update (1809) ou posterior.  Depois de instalar este aplicativo, a Windows Store manterá o tempo de execução atualizado.
1. Execute o aplicativo de visualização do desenvolvedor de OpenXR realidade mista do menu Iniciar e siga as instruções para ativar o tempo de execução.  Em breve, esse aplicativo permitirá que você a explorar outras informações de depuração OpenXR também.

![Realidade misturada OpenXR desenvolvedor visualize o aplicativo](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>Suporte para atualização do Windows 10 de outubro de 2018

Se você estiver executando o Windows 10 de maio de 2019 atualizar (1903) e tiver seguido as etapas acima, você deve estar pronto para usar a visualização do desenvolvedor de OpenXR realidade mista!

Se você não estiver pronto para [atualizar seu computador para maio de 2019 atualização](https://www.microsoft.com/en-us/software-download/windows10), você pode começar a adotar o Windows 10 de outubro de 2018 atualize (1809), mais uma etapa a seguir:

1. Siga as etapas acima para instalar a visualização do desenvolvedor de OpenXR realidade mista.
1. Para definir a visualização do desenvolvedor de OpenXR realidade mista como tempo de execução do seu sistema do Active Directory OpenXR, instale o [misto realidade OpenXR Developer Preview Compatibility Pack](https://aka.ms/openxr-compat).

## <a name="building-a-sample-openxr-app"></a>Criando um aplicativo de exemplo OpenXR

O [BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) projeto demonstra um exemplo simple de OpenXR com dois arquivos de projeto de Visual Studio, um para tanto Win32 aplicativo de desktop e outro para um aplicativo UWP HoloLens 2.  Como a solução contém um projeto UWP HoloLens, será necessário o [carga de trabalho de desenvolvimento de plataforma Universal do Windows](install-the-tools.md#installation-checklist) instalado no Visual Studio totalmente abri-lo.

Observe que, embora os arquivos de projeto do Win32 e UWP são separados devido às diferenças de empacotamento e implantação, o código do aplicativo dentro de cada projeto é 100% o mesmo!

## <a name="feedback"></a>Privacidade Jurídica

Para fornecer comentários sobre o [especificação OpenXR provisionados 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), visite o [Khronos OpenXR fóruns](https://community.khronos.org/c/openxr), [canal do Slack #openxr](https://khr.io/slack) e o [spec o Issue tracker](https://github.com/KhronosGroup/OpenXR-Docs/issues).

## <a name="troubleshooting"></a>Solução de problemas

Aqui estão algumas dicas de solução de problemas para a visualização do desenvolvedor OpenXR realidade mista.  Se você estiver acessando a quaisquer outros problemas, visite o [Khronos OpenXR fóruns](https://community.khronos.org/c/openxr) ou [canal do Slack #openxr](https://khr.io/slack).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Aplicativo OpenXR não iniciando o Windows Mixed Reality

Se seu aplicativo OpenXR não está iniciando o Windows Mixed Reality quando você executá-lo, a visualização do desenvolvedor de OpenXR realidade mista não pode ser definida como o tempo de execução ativo.  Certifique-se de executar o aplicativo de visualização do desenvolvedor de OpenXR realidade mista e siga as instruções para ativar o tempo de execução.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>Aplicativo de realidade OpenXR Developer Preview misto não pode ser instalado 

Certifique-se de que você estiver executando pelo menos o Windows 10 de outubro de 2018 atualizar (1809).  Se você estiver em uma versão anterior do Windows 10, você pode atualizar para o de maio de 2019 atualizar (1903) usando o [Assistente de atualização do Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Se a instalação do botão no aplicativo misto realidade OpenXR Developer Preview não nada no Windows 10 de outubro de 2018 será atualizado, seu sistema pode ter armazenada em cache os requisitos de sistema obsoletos para o aplicativo.  Você pode executar o comando `wsreset.exe` em um prompt de comando para limpar o cache.

## <a name="see-also"></a>Consulte também

* [Saiba mais sobre OpenXR](https://www.khronos.org/openxr/)
* [Especificação de OpenXR provisionados 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [Referência da API OpenXR provisionados 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [Cabeçalhos de OpenXR provisionados 0,90](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [Guia de referência rápida OpenXR provisionados 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
