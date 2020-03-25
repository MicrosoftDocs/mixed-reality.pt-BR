---
title: Solução de problemas do OpenXR
description: Solucionar problemas em seus aplicativos OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, solução de problemas
ms.openlocfilehash: 08ca671ded7230a4ba3cfcdc640233082af51040
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163360"
---
# <a name="openxr-troubleshooting"></a>Solução de problemas do OpenXR

Aqui estão algumas dicas de solução de problemas ao desenvolver um aplicativo OpenXR usando o tempo de execução do Windows Mixed Reality OpenXR.  Se você tiver outras dúvidas sobre a <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação do OpenXR 1,0</a>, visite os <a href="https://community.khronos.org/c/openxr" target="_blank">fóruns do Khronos OpenXR</a> ou a <a href="https://khr.io/slack" target="_blank">margem de atraso #openxr canal</a>.

>[!NOTE]
>Há problemas conhecidos no tempo de execução OpenXR misto do Windows Mixed real com aplicativos x86.  Você deve criar aplicativos de desktop OpenXR para x64 no momento.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>O aplicativo OpenXR não está iniciando a realidade mista do Windows

Se seu aplicativo OpenXR não estiver iniciando a realidade mista do Windows quando você executá-lo, o tempo de execução do Windows Mixed Reality OpenXR não poderá ser definido como o tempo de execução ativo.  Siga as instruções acima para [começar a usar o OpenXR for Windows Mixed realness headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) para tornar o tempo de execução ativo.

Você também pode executar o [portal do desenvolvedor do Windows Mixed Reality OpenXR](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-portal) para solução de problemas adicional para obter ajuda em relação ao estado do tempo de execução do Windows Mixed Reality OpenXR em seu sistema.

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>Portal de realidade misturada não mostrando o item de menu "configurar OpenXR"

Verifique se você está executando pelo menos a atualização de 10 de outubro de 2018 do Windows (1809).  Se você estiver em uma versão anterior do Windows 10, poderá atualizar para a atualização de maio de 2019 (1903) usando o [Assistente de atualização do Windows 10](https://www.microsoft.com//software-download/windows10).

O item de menu "configurar OpenXR" pode não estar disponível se você tiver uma versão mais antiga do aplicativo do portal de realidade misturada.  Verifique se há uma [atualização de aplicativo do portal da realidade misturada](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) para garantir que você tem a versão mais recente.

Observe que o item de menu "set up OpenXR" não aparecerá se o tempo de execução do Windows Mixed Reality já estiver instalado e ativo.  Você pode instalar o [portal do desenvolvedor do Windows Mixed Reality OpenXR](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-portal) para determinar o status atual do tempo de execução do OpenXR em seu sistema.