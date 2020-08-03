---
title: Realidade mista do Windows e o novo Microsoft Edge
description: Prepare-se para o novo Microsoft Edge no Windows Mixed Reality. Inclui alterações esperadas, atualizações a serem verificadas e problemas conhecidos.
author: mattzmsft
ms.author: mazeller
ms.date: 07/31/2020
ms.topic: article
keywords: Edge, novo, imersão Web, Microsoft Edge, navegador, VR
ms.openlocfilehash: 107b825496cc318042da0e0cd9acdbe482994a69
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476978"
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

Para obter a melhor experiência do Microsoft Edge possível no início da realidade misturada, também recomendamos aguardar **algumas otimizações de realidade misturada do Windows para o novo Microsoft Edge chegando com a atualização cumulativa 2020-01 para o Windows 10 versão 1903 (ou posterior)**, que deve estar disponível no Windows Update no final de Janeiro.

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

### <a name="monitor-and-input-handling-issues"></a>Problemas de monitor e de tratamento de entrada

Depois de pegar a atualização cumulativa 2020-01 para o Windows 10 versão 1903 (ou posterior), os monitores virtuais aparecerão como monitores físicos genéricos em **configurações > sistema > exibido** durante sessões de realidade mista do Windows. Alguns clientes, especialmente aqueles com mais de um monitor físico, podem notar problemas com o layout de área de trabalho e o tratamento de entrada como resultado.

**Por que isso acontece**

O suporte para aplicativos Win32 clássicos no Windows Mixed Reality foi introduzido com a [atualização do Windows 10 de maio de 2019](#release-notes-may-2019.md). Para habilitar esse suporte, um monitor virtual deve ser criado para hospedar o aplicativo Win32. Cada vez que um novo aplicativo Win32 é iniciado, outro monitor virtual precisa ser criado. Infelizmente, a criação de um monitor virtual é uma tarefa intensiva que pode fazer com que a tela do headset congele brevemente. Os clientes ofereciam comentários de que essa era uma experiência desconfortável e perturbadora. Por causa desses comentários, junto com o aumento do uso de aplicativos Win32, tomamos a decisão de alocar previamente três monitores virtuais durante a inicialização da realidade mista do Windows para evitar essa interrupção e permitir que os clientes iniciem até três aplicativos simultâneos do Win32 sem experimentar o congelamento de vídeo do headset.

**Solução alternativa**

Já que recebemos comentários de que alguns clientes, especialmente aqueles com vários monitores físicos, preferem desabilitar essa pré-alocação do monitor virtual. Para dar aos clientes controle e escolha, habilitamos uma solução alternativa que envolve a alteração de um valor de chave do registro (disponível com a atualização cumulativa 2020-07 para o Windows 10 versão 2004).

>[!NOTE]
>A modificação de valores de chave do registro destina-se a usuários avançados.

>[!WARNING]
>Desabilitar a pré-alocação do virtual monitor pode resultar na exibição resumida do fone de ouvido ao iniciar um aplicativo Win32 (como o fluxo, o novo Microsoft Edge ou o Google Chrome) no Windows Mixed Reality.

Para desabilitar a pré-alocação do monitor virtual:
1. Verifique **Windows Update** para a atualização cumulativa 2020-07 para o Windows 10 versão 2004 e instale a atualização quando disponível.
2. Inicie o **Editor do registro**.
3. Navegue até HKEY_CURRENT_USER \SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\PreallocateVirtualMonitors
4. Altere o valor DWORD de 1 (seu valor padrão) para 0 (zero)
    * TRUE-1
    * FALSE-0

Os monitores virtuais agora serão alocados quando você tentar iniciar um aplicativo Win32 no Windows Mixed Reality em vez de pré-instalar. Para redefinir essa configuração e reabilitar a pré-alocação do monitor virtual, retorne o valor DWORD para 1.

### <a name="additional-known-issues"></a>Problemas conhecidos adicionais

-   Os sites abertos no Windows Mixed Realm serão perdidos quando o portal da realidade misturada for fechado, embora as janelas do Microsoft Edge permaneçam onde foram colocadas na casa misturada da realidade.
- As experiências de WebXR, incluindo a extensão do visualizador 360, podem não ser iniciadas corretamente em PCs com uma configuração de GPU híbrida. Você pode contornar esse problema selecionando sua GPU dedicada como a GPU padrão em seu software de placa gráfica.
-   O áudio do Microsoft Edge Windows não está espacial.
-   **Corrigido na extensão do visualizador 360 versão 2.3.8**: abrir um vídeo 360 do YouTube no Windows Mixed Reality pode resultar na distorção do vídeo no headset. Reiniciar a borda deve atualizar invisivelmente a extensão do visualizador 360 para resolver esse problema. Você pode confirmar qual versão da extensão você tem digitando `edge://system/` na barra de endereços e selecionando o botão **expandir** ao lado de "extensões".




