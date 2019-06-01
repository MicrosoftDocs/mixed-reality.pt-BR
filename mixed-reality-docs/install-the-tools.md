---
title: Instalar as ferramentas
description: Comece aqui para se preparar para o desenvolvimento de realidade misturada. Este artigo sempre deve refletir as versões mais recentes do Unity, Visual Studio e outras ferramentas recomendadas para o desenvolvimento de fone de ouvido imersivo HoloLens e realidade mista do Windows.
author: yoyozilla
ms.author: yoyozilla
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: atualizados, ferramentas, começar a usar, Noções básicas, o unity, o visual studio, o Kit de ferramentas
ms.openlocfilehash: 32dcda0eceb8d3717de7b2502d86f03cda975b8f
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453731"
---
# <a name="install-the-tools"></a>Instalar as ferramentas

Obtenha as ferramentas que necessárias para criar aplicativos para o Microsoft HoloLens e fones de ouvido Windows Mixed Reality de imersão (VR). Não há nenhuma separação de desenvolvimento do SDK para Windows Mixed Reality; Você usará o Visual Studio com o SDK do Windows 10.

Você não tem um dispositivo de realidade misturada? Você pode instalar o [HoloLens emulador](using-the-hololens-emulator.md) para testar algumas funcionalidades de aplicativos de realidade misturada sem um HoloLens. Você também pode usar o [simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md) para testar seus aplicativos de realidade misturada fones imersivos em exposição.

É recomendável instalar o mecanismo de jogos do Unity como aplicativos de realidade mista de maneira mais fácil de começar a criar, no entanto, você também pode compilar em relação a DirectX se você quiser usar um mecanismo personalizado.

>[!TIP]
>Marque esta página e verifique-o regularmente para manter atualizado sobre a versão mais recente de cada ferramenta recomendada para desenvolvimento de realidade misturada.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>Lista de verificação de instalação


| Ferramenta | Descrição | Observações |
|---------|---------|---------|
| ![Logotipo do Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>(Link de instalação manual)</a> | Instale a versão mais recente do Windows 10 para que o sistema operacional do seu PC corresponda à plataforma para a qual você está criando aplicativos de realidade misturada. | **Instalação do Windows 10** <br> <ul><li>Você pode instalar a versão mais recente do Windows 10 via Windows Update em configurações ou criando mídia de instalação (usando o link na coluna à esquerda).<li>Ver [notas de versão atuais](release-notes-october-2018.md) para obter informações sobre os mais recentes recursos de realidade disponíveis mistos com cada versão do Windows 10.</ul> **Habilitar o modo de desenvolvedor em seu PC** em Configurações > atualização e segurança > para desenvolvedores. <br><br> **Observação para enterprise e computadores corporativos gerenciados:** se seu PC for gerenciado por da sua organização departamento de TI, talvez seja necessário entrar em contato com eles para atualizar. <br><br> **Versões de ' n' do Windows:** Fones de ouvido Windows Mixed Reality de imersão (VR) não têm suporte em versões de ' n' do Windows. |
| ![Logotipo do Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2017**<br>(Link de instalação)</a> | Ambiente completo de desenvolvimento integrado (IDE) para Windows e muito mais. Você usará o Visual Studio para escrever código, depurar, testar e implantar. | **Cargas de trabalho para instalar:** <ul><li>Desenvolvimento para desktop com C++</li><li>Desenvolvimento na plataforma Windows universal</li></ul>**Observação sobre o Unity:** A menos que intencionalmente, você está tentando instalar uma versão (não-LTS) mais recente do Unity para uma finalidade específica, recomendamos *não* instalando a carga de trabalho do Unity como parte da instalação do Visual Studio e, em vez disso, instalando os 2018.4 LTS fluxo do Unity conforme indicado abaixo.<br> <br>**Observação:** Há alguns problemas conhecidos com o desenvolvimento de realidade misturada no Visual Studio de 2019 no momento.  Por enquanto, é recomendável que você continue usando o Visual Studio 2017. |
| ![Logotipo do Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)**<br>(Link de instalação manual)</a> | Fornece os cabeçalhos, bibliotecas, metadados e ferramentas mais recentes para a criação de aplicativos do Windows 10 em HoloLens 2. | Para compilar aplicativos HoloLens 2, você precisará instalar o Windows SDK, build 18362 ou posterior.<br> <br> Se você só estiver desenvolvendo aplicativos para desktops fones de ouvido Windows Mixed Reality ou HoloLens (1º gen), você pode usar o SDK do Windows instalado pelo Visual Studio 2017. |
| ![Logotipo do Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2087187" target="_blank">**Emulador do HoloLens 2**<br>(Link de instalação: 10.0.18362.1005)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (1º gen) emulador**<br>(Link de instalação: 10.0.17763.253)</a> | O emulador permite que você execute aplicativos em uma imagem de máquina virtual do HoloLens sem um HoloLens físico.<br> <br> Este pacote também inclui modelos de projetos DirectX holographic para o Visual Studio. | Ver [usando o emulador do HoloLens](using-the-hololens-emulator.md) para obter mais informações sobre como começar com o emulador.<br> <br> **O sistema deve dar suporte a Hyper-V** para a instalação do emulador para ter êxito. Consulte a seção de requisitos de sistema abaixo para obter detalhes. Se desejar, você pode selecionar instalar apenas os modelos sem o emulador.<br>|
| ![Logotipo do Unity](images/unity_logo.png)<br><br><a href="https://unity3d.com/unity/qa/lts-releases?version=2018.4" target="_blank">**2018.4 do Unity**<br>(Link de instalação)</a> | O mecanismo de jogos do Unity é a maneira mais fácil para criar experiências de realidade misturada, com suporte interno para recursos do Windows Mixed Reality. | É recomendável normalmente o fluxo do Unity LTS (suporte a longo prazo) como a melhor versão na qual iniciar novos projetos, atualizar para sua revisão mais recente para acompanhar as correções estáveis mais recentes.<br> <br>A recomendação atual é usar **Unity 2018.4.x**, que é a compilação LTS necessária para MRTK v2 abaixo.<br> <br>Alguns desenvolvedores talvez queira usar uma versão diferente do Unity por razões específicas. Para esses casos, o Unity oferece suporte a instalações lado a lado de versões diferentes. |
| ![Logotipo MRTK](images/MRTKIcon.jpg)<br><br><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">**Toolkit de realidade misturada (MRTK v2) para o Unity**</a> | MRTK v2 para Unity é um kit de desenvolvimento de plataforma cruzada do código-fonte aberto para aplicativos de realidade misturada.<br><br> MRTK v2 destina-se a acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens, headsets do Windows Mixed Reality imersivos (VR) e a plataforma de OpenVR. O projeto é voltado para reduzir as barreiras à entrada para criar aplicativos de realidade mista e contribuir com a comunidade como todos nós crescer. | Saiba mais sobre MRTK v2 visitando o projeto <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki" target="_blank">wiki do GitHub</a>. |


## <a name="mixed-reality-toolkit"></a>Kit de ferramentas de realidade misturada

O Kit de ferramentas de realidade misturada fornece componentes e recursos que se destinam a acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens, headsets Windows Mixed Reality e OpenVR plataforma. O projeto é voltado para reduzir as barreiras à entrada para criar aplicativos de realidade mista e contribuem na comunidade, como todos nós crescer.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">MixedRealityToolkit</a>
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Unity MixedRealityToolkit</a> – usa o código do Kit de ferramentas base e torna mais fácil de consumir no Unity.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">MixedRealityCompanionKit</a> - bits e componentes que não podem ser executados diretamente em HoloLens ou fones imersivos em exposição (VR) de código, mas em vez disso, o par com eles para criar experiências visando o Windows Mixed Reality.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Como configurar seu computador para o desenvolvimento de realidade misturada

SDK do Windows 10 funciona melhor no sistema operacional Windows 10. Esse SDK também é compatível com Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Observe que nem todas as ferramentas têm suporte em sistemas operacionais mais antigos. 

### <a name="for-hololens-development"></a>Para o desenvolvimento HoloLens

Ao configurar seu computador de desenvolvimento para desenvolvimento HoloLens, verifique se ele atende aos requisitos do sistema para ambos <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> e <a href="https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs" target="_blank">Visual Studio</a>. Se você planeja usar o HoloLens (1º gen) emulador, você vai querer garantir seu PC atende a [requisitos de sistema do emulador HoloLens](using-the-hololens-emulator.md#hololens-emulator-system-requirements) também.

Para se familiarizar com o emulador do HoloLens, consulte [usando o emulador do HoloLens](using-the-hololens-emulator.md).

Se você planeja desenvolver para o HoloLens e o Windows Mixed Reality headsets (VR) imersivos, use as recomendações de sistema e os requisitos na seção a seguir.

### <a name="for-immersive-vr-headset-development"></a>Para desenvolvimento de fone de ouvido imersivo (VR)

>[!NOTE]
>As diretrizes a seguir são as especificações atuais de mínimas e recomendadas para fone de ouvido (VR) imersivo *computador de desenvolvimento*e pode ser atualizada regularmente.

>[!WARNING]
>Não confunda isso com o [diretrizes de compatibilidade de hardware de PC mínimas](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), que descreve ao *especificações de consumidor PC* aos quais você deve direcionar seu aplicativo profunda de fone de ouvido (VR) ou um jogo.

Se seu computador de desenvolvimento imersivo fone de ouvido não tem portas HDMI e/ou USB 3.0 em tamanho normal, você precisará [adaptadores](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) para se conectar a seu fone de ouvido.

Atualmente, há [problemas conhecidos](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) com algumas configurações de hardware, especialmente com blocos de anotações com gráficos híbridos.

<table>
<tr>
<th></th><th> Mínimo</th><th> Recomendado</th>
</tr><tr>
<td> Processador</td><td> <b>Bloco de anotações:</b> Intel Mobile Core i5 7ª geração de CPU, Dual-Core com Hyper Threading <b>área de trabalho:</b> Área de trabalho do Intel i5 6ª geração de CPU, Dual-Core com Hyper Threading <b>ou</b> AMD FX4350 equivalente do 4.2 Ghz Quad-Core</td><td> <b>Área de trabalho:</b> Área de trabalho do Intel i7 6ª geração (6 núcleos) <b>ou</b> AMD Ryzen 1600 5 (6 núcleos, 12 threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Bloco de anotações:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalente ou superior DX12 GPU compatível com <b>área de trabalho:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalente ou superior DX12 GPU compatível com</td><td><b>Área de trabalho:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalente ou superior DX12 GPU compatível com</td>
</tr><tr>
<td> Versão do GPU driver WDDM</td><td colspan="2"> Driver WDDM 2.2</td>
</tr><tr>
<td> Potência do Design térmico</td><td colspan="2"> 15W ou maior</td>
</tr><tr>
<td> Portas de exibição de gráficos</td><td colspan="2"> 1 x gráfica disponível da tela de porta para o&#160;fone de ouvido (1.4 HDMI ou DisplayPort 1.2 para fones de ouvido 60Hz, 2.0 HDMI ou DisplayPort 1.2 para headsets Hz 90)</td>
</tr><tr>
<td> Resolução de vídeo</td><td colspan="2"> Resolução: SVGA (800 x 600) ou maior profundidade de bits: 32 bits de cores por pixel</td>
</tr><tr>
<td> Memória</td><td> 8&#160;GB de RAM ou superior</td><td> 16 GB de RAM ou superior</td>
</tr><tr>
<td> Armazenamento</td><td colspan="2"> &gt;Espaço livre adicional de 10 GB</td>
</tr><tr>
<td> Portas USB</td><td colspan="2"> 1 x USB disponível da porta para o fone de ouvido (USB 3.0 Type-A) <b>Observação: USB deve fornecer um mínimo de 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (para conectividade de acessório)</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também

* [Visão geral de desenvolvimento](development-overview.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Como usar o simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Visão geral do desenvolvimento do Unity](unity-development-overview.md)
* [Visão geral de desenvolvimento do DirectX](directx-development-overview.md)
* [Arquivo do emulador do HoloLens](hololens-emulator-archive.md)
