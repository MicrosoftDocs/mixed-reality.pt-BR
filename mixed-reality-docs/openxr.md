---
title: OpenXR
description: Experimente a API OpenXR 0,90 provisional com a visualização do desenvolvedor de OpenXR realidade mista.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Realidade misturada OpenXR Developer Preview
ms.openlocfilehash: 0d8debf5c12cb88aaba402145c6a597f761491ee
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590704"
---
# <a name="openxr"></a>OpenXR

OpenXR é um padrão aberto de royalties partir [Khronos](https://www.khronos.org/) que fornece acesso nativo a uma ampla variedade de dispositivos de vários fornecedores que se estendem pela [espectro de realidade misturada](mixed-reality.md).

Com OpenXR, você pode criar aplicativos que se destinam a tanto holográfico dispositivos (como o HoloLens 2) que colocam conteúdo digital no mundo real, como se estivesse lá, bem como imersivos dispositivos (como Windows Mixed Reality headsets para computadores desktops) que ocultam o mundo físico e substituí-lo com uma experiência digital.  OpenXR permite escrever código depois que o que é portátil entre uma ampla variedade de plataformas de hardware.

O padrão de OpenXR está atualmente em uma fase provisória, com uma especificação de OpenXR 0,90 inicial lançada para comentários.  Para obter mais informações sobre OpenXR, incluindo o acesso à [provisória spec 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) e [cabeçalhos](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), consulte a [Khronos OpenXR página](https://www.khronos.org/openxr/).

## <a name="setting-up-the-mixed-reality-openxr-developer-preview"></a>Como configurar a visualização do desenvolvedor de OpenXR realidade mista

Você pode experimentar a API OpenXR 0,90 provisória hoje usando a visualização do desenvolvedor de OpenXR realidade mista.  Esse tempo de execução inicial permite que os aplicativos voltados para a API OpenXR 0,90 para destino Windows Mixed Reality fones imersivos em exposição na área de trabalho.  Se você não tiver acesso a um fone de ouvido, você pode usar o simulador de realidade mista do Windows em vez disso.

Para obter uma introdução a visualização do desenvolvedor de OpenXR realidade mista:

1. Certifique-se de que você estiver executando pelo menos o Windows Update 10 de outubro de 2018.  Se você estiver em uma versão anterior do Windows 10, você pode atualizar para o de outubro de 2018 atualizar usando o [Assistente de atualização do Windows 10](https://www.microsoft.com/en-us/software-download/windows10).  Se você estiver se sentindo aventureiro, você pode instalar um [compilação do Windows 10 Insider Preview](https://insider.windows.com).
1. Configurar um headset de realidade mista do Windows ou siga as instruções para [habilitar o simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md).
1. Instalar o [realidade misturada OpenXR desenvolvedor visualize o aplicativo](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Este aplicativo obtém que você configurou com o tempo de execução OpenXR preview no Windows 10 de outubro de 2018 Update ou posterior.  Depois de instalar este aplicativo, a Windows Store manterá o tempo de execução atualizado.
1. Execute o aplicativo de visualização do desenvolvedor de OpenXR realidade mista do menu Iniciar e siga as instruções para ativar o tempo de execução.  Em breve, esse aplicativo permitirá que você a explorar outras informações de depuração OpenXR também.

![Realidade misturada OpenXR desenvolvedor visualize o aplicativo](images/mixed-reality-openxr-developer-preview.png)

## <a name="support-for-windows-10-october-2018-update"></a>Suporte para atualização do Windows 10 de outubro de 2018

Para continuar com a visualização do desenvolvedor de OpenXR realidade misturada sobre o Windows 10 de outubro de 2018 atualização (a versão atual do Windows), você precisará seguir mais algumas etapas:

1. Siga as etapas acima para instalar a visualização do desenvolvedor de OpenXR realidade mista.
1. Para definir a visualização do desenvolvedor de OpenXR realidade mista como tempo de execução do seu sistema do Active Directory OpenXR, instale o [misto realidade OpenXR Developer Preview Compatibility Pack](https://aka.ms/openxr-compat).

## <a name="building-a-test-openxr-app"></a>Criação de um teste de aplicativo OpenXR

O [hello_xr](https://github.com/KhronosGroup/OpenXR-SDK/tree/master/src/tests/hello_xr) OpenXR testar o aplicativo demonstra o uso de várias partes da API.  Você pode seguir essas [instruções de build](https://github.com/KhronosGroup/OpenXR-SDK/blob/master/BUILDING.md), que criará o aplicativo de teste e os cabeçalhos de OpenXR em si.

## <a name="feedback"></a>Privacidade Jurídica

Para fornecer comentários sobre o [especificação OpenXR provisionados 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), visite o [Khronos OpenXR fóruns](https://community.khronos.org/c/openxr), [canal do Slack #openxr](https://khr.io/slack) e o [spec o Issue tracker](https://github.com/KhronosGroup/OpenXR-Docs/issues).

## <a name="troubleshooting"></a>Solução de problemas

Aqui estão algumas dicas de solução de problemas para a visualização do desenvolvedor OpenXR realidade mista.  Se você estiver acessando a quaisquer outros problemas, visite o [Khronos OpenXR fóruns](https://community.khronos.org/c/openxr) ou [canal do Slack #openxr](https://khr.io/slack).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Aplicativo OpenXR não iniciando o Windows Mixed Reality

Se seu aplicativo OpenXR não está iniciando o Windows Mixed Reality quando você executá-lo, a visualização do desenvolvedor de OpenXR realidade mista não pode ser definida como o tempo de execução ativo.  Certifique-se de executar o aplicativo de visualização do desenvolvedor de OpenXR realidade mista e siga as instruções para ativar o tempo de execução.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>Aplicativo de realidade OpenXR Developer Preview misto não pode ser instalado 

Certifique-se de que você estiver executando pelo menos o Windows Update 10 de outubro de 2018.  Se você estiver em uma versão anterior do Windows 10, você pode atualizar para o de outubro de 2018 atualizar usando o [Assistente de atualização do Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Se a instalação do botão no aplicativo misto realidade OpenXR Developer Preview não nada no Windows 10 de outubro de 2018 será atualizado, seu sistema pode ter armazenada em cache os requisitos de sistema obsoletos para o aplicativo.  Você pode executar o comando `wsreset.exe` em um prompt de comando para limpar o cache.

## <a name="see-also"></a>Consulte também

* [Saiba mais sobre OpenXR](https://www.khronos.org/openxr/)
* [Especificação de OpenXR provisionados 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [Referência da API OpenXR provisionados 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [Cabeçalhos de OpenXR provisionados 0,90](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
