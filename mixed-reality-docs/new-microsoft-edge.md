---
title: Realidade mista do Windows e o novo Microsoft Edge
description: Prepare-se para o novo Microsoft Edge no Windows Mixed Reality. Inclui alterações esperadas, atualizações a serem verificadas e problemas conhecidos.
author: mattzmsft
ms.author: mazeller
ms.date: 01/15/2020
ms.topic: article
keywords: Edge, novo, imersão Web, Microsoft Edge, navegador, VR
ms.openlocfilehash: e38cd83cef274281f0d36ae8714ea82aac5f0c65
ms.sourcegitcommit: e9e4e722f4b607888ce69185f8bda9549ad526ad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76041003"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Realidade mista do Windows e o novo Microsoft Edge

O [novo Microsoft Edge agora está disponível para download](https://blogs.windows.com/windowsexperience/?p=173496), mas os clientes também podem [esperar que ele seja instalado em uma atualização futura do Windows 10](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/), seguindo uma abordagem medida de distribuição nos próximos meses. 

Com essa notícia, **queríamos deixar que os clientes do Windows Mixed Reality VR do headset saibam o que esperar do novo Microsoft Edge e informam sobre algumas atualizações pendentes que melhorarão sua experiência de navegação na Web no Windows Mixed Reality**.

## <a name="introducing-the-new-microsoft-edge"></a>Apresentando o novo Microsoft Edge

O novo Microsoft Edge [adota o projeto](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) de software livre Chromium na área de trabalho para criar melhor compatibilidade com a Web para clientes e menos fragmentação da Web para todos os desenvolvedores da Web. Ele também dará suporte a WebXR na inicialização, o novo padrão para a criação de experiências da Web de imersão para headsets de VR, no lugar de WebVR.

>[!IMPORTANT]
>Quando você instalar o Microsoft Edge em um dispositivo Windows 10 atualizado, ele substituirá a versão anterior (herdada) em seu computador.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Preparando-se para o novo Microsoft Edge

Os clientes de headset do Windows Mixed Reality VR que desejam usar o novo Microsoft Edge na realidade misturada devem **atualizar para o Windows 10 versão 1903 ou posterior para o suporte nativo de aplicativos Win32 (como o novo Microsoft Edge)** na página inicial misturada de realidade. Verifique Windows Update ou [Instale manualmente a versão mais recente do Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Para obter a melhor experiência do Microsoft Edge possível no início da realidade misturada, também recomendamos aguardar **algumas otimizações de realidade misturada do Windows para o novo Microsoft Edge chegando com a atualização cumulativa 2020-01 para o Windows 10 versão 1903 (ou posterior)** , que deve estar disponível no Windows Update no final de Janeiro.

>[!IMPORTANT]
>Se você optar por baixar o novo Microsoft Edge antes de realizar essas atualizações, haverá alguns problemas conhecidos com seu comportamento no Windows Mixed Reality (que pode ser lido abaixo).

## <a name="known-issues"></a>Problemas conhecidos

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemas conhecidos resolvidos pela atualização cumulativa 2020-01 para o Windows 10 versão 1903 (ou posterior)

- Iniciar qualquer aplicativo Win32, incluindo o novo Microsoft Edge, faz com que a tela do headset congele brevemente.
- O bloco Microsoft Edge desaparece do menu Iniciar do Windows Mixed Reality (você pode encontrá-lo na pasta "aplicativos clássicos").
- As janelas do Microsoft Edge anterior ainda são colocadas em todo o início da realidade misturada, mas não podem ser usadas. A tentativa de ativar essas janelas inicia a borda dentro do aplicativo da área de trabalho.
- A seleção de um hiperlink na página inicial da realidade misturada inicia um navegador da Web na área de trabalho em vez da casa mistura de realidade.
- O aplicativo de demonstração do WebVR está presente na casa da realidade misturada, apesar de WebVR não ter mais suporte.
- Aprimoramentos gerais na inicialização e visuais do teclado.

### <a name="additional-known-issues"></a>Problemas conhecidos adicionais

-   Os sites abertos no Windows Mixed Realm serão perdidos quando o portal da realidade misturada for fechado, embora as janelas do Microsoft Edge permaneçam onde foram colocadas na casa misturada da realidade.
-   O áudio do Microsoft Edge Windows não está espacial.
-   Abrir um vídeo 360 do YouTube no Windows Mixed Reality pode resultar na distorção do vídeo no headset. Atualizar a página do vídeo do YouTube e reiniciar o vídeo 360 *pode* corrigir o problema, mas ouvimos comentários de que o problema pode persistir.
-   Durante as sessões de realidade mista do Windows, os monitores virtuais serão exibidos como monitores físicos genéricos em Configurações > sistema > exibição.



