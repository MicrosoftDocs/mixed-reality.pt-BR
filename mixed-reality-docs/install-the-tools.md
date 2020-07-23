---
title: Instalar as ferramentas
description: Comece aqui para se preparar para o desenvolvimento de realidade misturada. Este artigo sempre deve refletir as versões mais recentes do Unity, do Visual Studio e das outras ferramentas recomendadas para o desenvolvimento de headset imersivo do HoloLens e do Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 3/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, começar, noções básicas, unity, visual studio, kit de ferramentas
ms.openlocfilehash: ac3e4967ce687f7cb3009de64748841f88562a92
ms.sourcegitcommit: 8daefb763d1f23fe02b95b766b00b373f04c5c2d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86447922"
---
# <a name="install-the-tools"></a>Instalar as ferramentas

Obtenha as ferramentas necessárias para criar aplicativos para os headsets imersivos (VR) do Microsoft HoloLens e do Windows Mixed Reality. Não há nenhum SDK separado para o desenvolvimento no Windows Mixed Reality; você usará o Visual Studio com o SDK do Windows 10.

Não tem um dispositivo de realidade misturada? Você pode instalar o [emulador do HoloLens](using-the-hololens-emulator.md) para testar algumas funcionalidades de aplicativos de realidade misturada sem um HoloLens. Você também pode usar o [simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md) para testar seus aplicativos de realidade misturada para headsets imersivos. Se você estiver usando o Unity, poderá usar a simulação de entrada do [MRTK (Kit de Ferramentas de Realidade Misturada)](https://github.com/Microsoft/MixedRealityToolkit-Unity) para testar vários tipos de interações de entrada, como entrada por rastreamento de mão e rastreamento ocular.

É recomendável instalar o mecanismo de jogos Unity como a maneira mais fácil de começar a criar aplicativos de realidade misturada. No entanto, você também poderá criar com base no DirectX se quiser usar um mecanismo personalizado.

>[!TIP]
>Adicione esta página aos favoritos e acesse-a regularmente para se manter atualizado sobre a versão mais recente de cada ferramenta recomendada para o desenvolvimento de realidade misturada.

<br>

## <a name="installation-checklist"></a>Lista de verificação da instalação


| Ferramenta | Observações |
|---------|---------|
| ![Logotipo do Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (link de instalação manual)</a><br><br>Instale a versão mais recente do Windows 10, para que o sistema operacional do seu computador corresponda à plataforma para a qual você está compilando aplicativos de realidade misturada.  | **Instalação do Windows 10** <br> Você pode instalar a versão mais recente do Windows 10 via Windows Update nas Configurações ou criando uma mídia de instalação, usando o link na coluna à esquerda. <br><br>Veja as [notas de versão atuais](release-notes-october-2018.md) para obter informações sobre os recursos mais recentes de realidade misturada disponíveis em cada versão do Windows 10. **Ative o modo de desenvolvedor no seu computador** em Configurações > Atualização e Segurança > Para Desenvolvedores. <br><br> **Observação para computadores empresariais e corporativos**<br>Se o computador for gerenciado pelo departamento de TI da sua organização, talvez seja necessário contatá-los para atualizar. <br><br> **"N" versões do Windows**<br> Headsets imersivos (VR) do Windows Mixed Reality não são compatíveis com as versões "N" do Windows. |
| ![Logotipo do Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.2 ou superior)** (link de instalação)</a> <br><br>Ambiente de desenvolvimento integrado (IDE) completo para Windows e muito mais. Você usará o Visual Studio para escrever o código, depurar, testar e implantar. | Certifique-se de instalar as seguintes cargas de trabalho: <br><br>**● Desenvolvimento para desktop com C++**<br>**● Desenvolvimento da UWP (Plataforma Universal do Windows)**<br><br>Na carga de trabalho da UWP, certifique-se de verificar o seguinte componente opcional caso você esteja desenvolvendo para o HoloLens:<br><br>**● Conectividade do dispositivo USB**<br><br>**Observação sobre o Unity**<br>A menos que você esteja tentando instalar intencionalmente uma versão (não LTS) mais recente do Unity para uma finalidade específica, recomendamos *não* instalar a carga de trabalho do Unity como parte da instalação do Visual Studio. Em vez disso, instale o fluxo **2019 LTS do Unity**, conforme indicado abaixo.<br><br>**Observação**<br>há alguns problemas conhecidos com a depuração de aplicativos de realidade misturada no Visual Studio 2019 versão 16.0.  Verifique se você atualizou o **Visual Studio 2019 para a versão 16.2 ou superior**. |
| ![Logotipo do Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**SDK do Windows 10 (10.0.18362.0)** (link de instalação manual)</a> <br><br>Fornece os cabeçalhos, bibliotecas, metadados e ferramentas mais recentes para a compilação de aplicativos do Windows 10 no HoloLens 2. | **Para criar aplicativos do HoloLens 2, você precisará instalar o SDK do Windows, build 18362 ou posterior.**<br> <br> Se você estiver desenvolvendo aplicativos somente para headsets do Windows Mixed Reality de área de trabalho ou HoloLens (1ª geração), poderá usar o SDK do Windows instalado pelo Visual Studio 2017. |
| ![Logotipo do Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2132415" target="_blank">**Emulador do HoloLens 2 (Windows Holographic, versão 2004, atualização do junho de 2020)** (Link de instalação: 10.0.19041.1106)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulador do HoloLens (1ª geração)** (link de instalação: 10.0.17763.134)</a> <br><br>O emulador permite executar aplicativos em uma imagem de máquina virtual do HoloLens sem um HoloLens físico.<br> <br> | Veja [Usando o emulador do HoloLens](using-the-hololens-emulator.md) para obter mais informações sobre como começar a usar o emulador.<br> <br> **O sistema deve ser compatível com Hyper-V** para a instalação do emulador ser bem-sucedida. Consulte a seção de Requisitos de sistema abaixo para obter detalhes. <br>|

## <a name="choose-your-engine"></a>Escolha seu mecanismo

:::row:::
    :::column:::
        <a href="https://unity3d.com/unity/qa/lts-releases" target="_blank">![Unity](images/unity_logo.png)<br>**Unity**</a><br>
        É recomendável usar o fluxo LTS (suporte a longo prazo) do Unity, que é a melhor versão para iniciar novos projetos. Atualize para a revisão mais recente para obter as correções estáveis mais recentes.<br>
        <br>
        A recomendação atual é usar o **Unity 2019**, que é o build LTS necessário para o MRTK v2 abaixo.<br>
        <br>
        Alguns desenvolvedores talvez queiram usar uma versão diferente do Unity por motivos específicos. Nesses casos, o Unity oferece suporte a instalações lado a lado de versões diferentes.<br>
        <br>
        Consulte a [Visão geral de desenvolvimento do Unity](unity-development-overview.md) para começar a usar o desenvolvimento do Unity para o HoloLens 2 ou os headsets imersivos do Windows Mixed Reality.<br>
        <br>
    :::column-end:::
    :::column:::
        <a href="https://docs.unrealengine.com//GettingStarted/Installation/index.html" target="_blank">![Unreal](images/Unreal_logo.png)<br>**Unreal**</a><br>
        O Unreal Engine 4 é um mecanismo de criação avançado e de software livre com suporte completo para realidade misturada em C++ e Blueprints.<br>
        <br>
        Desde o Unreal Engine 4.25, o suporte ao HoloLens é completo e pronto para produção.<br>
        <br>
        Consulte a [Visão geral do desenvolvimento do Unreal](unreal-development-overview.md) para começar a usar o desenvolvimento do Unreal para o HoloLens 2.
    :::column-end:::
    :::column:::
        ![Desenvolvimento de aplicativos nativos](images/visualstudio-small_logo.png)<br>
        [**Nativo (OpenXR)** ](openxr-getting-started.md)<br>
        O OpenXR é um padrão de API isento de royalties e aberto da Khronos, que fornece aos mecanismos acesso nativo a uma ampla gama de dispositivos de vários fornecedores, estendendo-se pelo espectro da realidade misturada.  O projeto <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> demonstra um exemplo de OpenXR simples com dois arquivos de projeto do Visual Studio, um para um aplicativo da área de trabalho Win32 e outro para um aplicativo HoloLens 2 da UWP.<br>
        <br>
        <a href="https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX" target="_blank">**Nativo (WinRT)** </a><br>
        Os <a href="https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX" target="_blank">modelos de aplicativos nativos do Windows Mixed Reality</a> fornecem todos os elementos essenciais necessários para começar a escrever um aplicativo de realidade misturada usando o DirectX com APIs nativas. Inclui um loop de renderização (ou “loop de jogo”), uma classe auxiliar DeviceResources para gerenciar o dispositivo e o contexto Direct3D e um exemplo simples de renderizador de holograma. Disponível para Direct3D11 e Direct3D 12.<br>
        <br>
        Consulte a [Visão geral de desenvolvimento nativo](directx-development-overview.md) para começar a usar o desenvolvimento de aplicativo nativo usando WinRT ou OpenXR para HoloLens 2 ou os headsets imersivos do Windows Mixed Reality.
    :::column-end:::
:::row-end:::

<br>

## <a name="mixed-reality-toolkit-mrtk"></a>MRTK (Kit de Ferramentas de Realidade Misturada)
![MRTK](images/UX/MRTK_UX_Hero.png)

O MRTK (Kit de Ferramentas de Realidade Misturada) é um kit de desenvolvimento multiplataforma de software livre para aplicativos de realidade misturada. O MRTK fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. O kit de ferramentas destina-se a acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](images/MRTK_Badge_Unity.png)<br>**Kit de Ferramentas de Realidade Misturada – Unity (GitHub)** </a><br>
    :::column-end:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](images/MRTK_Badge_Unreal.png)<br>**Kit de Ferramentas de Realidade Misturada – Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

### <a name="other-tools"></a>Outras ferramentas
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Kit Complementar de Realidade Misturada (GitHub)</a> – bits de código e componentes que não podem ser executados diretamente no HoloLens ou nos headsets imersivos (VR), mas que se emparelham com eles para criar experiências destinadas ao Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Kit de Ferramentas de Realidade Misturada – Comum (GitHub)</a> – uma coleção de scripts e componentes compartilhados.


## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Como configurar seu computador para o desenvolvimento de realidade misturada

O SDK do Windows 10 funciona melhor no sistema operacional Windows 10. Esse SDK também é compatível com: Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Observe que nem todas as ferramentas são compatíveis com sistemas operacionais mais antigos. 

### <a name="for-hololens-development"></a>Desenvolvimento para o HoloLens

Ao configurar seu computador para o desenvolvimento para o HoloLens, verifique se ele atende aos requisitos de sistema do <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> e o <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Se você planeja usar o emulador do HoloLens, verifique se o computador também atende aos [requisitos de sistema do emulador do HoloLens](using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Para começar a usar o emulador do HoloLens, veja [Usando o emulador do HoloLens](using-the-hololens-emulator.md).

Se você planeja desenvolver para headsets imersivos (VR) do HoloLens e do Windows Mixed Reality, use as recomendações e requisitos de sistema descritos na próxima seção.

### <a name="for-immersive-vr-headset-development"></a>Desenvolvimento para headset imersivo (VR)

>[!NOTE]
>As orientações a seguir são as especificações atuais mínimas e recomendadas para seu *computador de desenvolvimento* para headset imersivo (VR) e são atualizadas regularmente.

>[!WARNING]
>Não confunda essas informações com as [diretrizes de compatibilidade mínima de hardware do computador](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), que descreve as *especificações do computador do consumidor*, que é o alvo do seu jogo ou aplicativo de headset imersivo (VR).

Se seu computador de desenvolvimento de headset imersivo não tiver portas HDMI e/ou USB 3.0 padrão, você precisará de [adaptadores](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) para conectar o headset.

Atualmente, há [problemas conhecidos](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) com algumas configurações de hardware, especialmente em notebooks com gráficos híbridos.

<table>
<tr>
<th></th><th> Mínimo</th><th> Recomendado</th>
</tr><tr>
<td> Processador</td><td> <b>Notebook:</b> CPU Intel Mobile Core i5 de 7ª geração, Dual-Core com Hyper Threading <b>Área de trabalho:</b> CPU Intel i5 de 6ª geração, Dual-Core com Hyper Threading <b>OU</b> equivalente a AMD FX4350 4,2Ghz Quad-Core</td><td> <b>Área de trabalho</b>: Intel i7 de 6ª geração (6 núcleos) <b>OU</b> GPU AMD Ryzen 5 1600 (6 núcleos, 12 threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> NVIDIA GTX 965M, GPU equivalente ou superior a AMD RX 460M (2GB) com capacidade DX12 <b>Computador:</b> NVIDIA GTX 960/1050, GPU equivalente ou superior a AMD Radeon RX 460 (2GB) com capacidade DX12</td><td><b>Área de trabalho</b>: NVIDIA GTX 980/1060, GPU equivalente ou superior a AMD Radeon RX 480 (2GB) com capacidade DX12</td>
</tr><tr>
<td> Versão WDDM do driver da GPU</td><td colspan="2"> Driver WDDM 2.2</td>
</tr><tr>
<td> Potência do design térmico</td><td colspan="2"> 15W ou mais</td>
</tr><tr>
<td> Portas de vídeo</td><td colspan="2"> 1 x porta de vídeo disponível para headset (HDMI 1.4 ou DisplayPort 1.2 para headsets de 60Hz, HDMI 2.0 ou DisplayPort 1.2 para headsets de 90Hz)</td>
</tr><tr>
<td> Resolução da tela</td><td colspan="2"> Resolução: SVGA (800 x 600) ou maior Profundidade de bits: 32 bits de cores por pixel</td>
</tr><tr>
<td> Memória</td><td> 8 GB de RAM ou mais</td><td> 16 GB de RAM ou mais</td>
</tr><tr>
<td> Armazenamento</td><td colspan="2"> &gt;10 GB de espaço livre adicional</td>
</tr><tr>
<td> Portas USB</td><td colspan="2"> 1 x porta USB disponível para headset (USB 3.0 Tipo A) <b>Observação: a USB deve fornecer um mínimo de 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (para conexão de acessórios)</td>
</tr>
</table>

## <a name="see-also"></a>Veja também

* [Visão geral do desenvolvimento](development.md)
* [Como usar o emulador do HoloLens](using-the-hololens-emulator.md)
* [Como usar o simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Visão geral do desenvolvimento do Unity](unity-development-overview.md)
* [Visão geral do desenvolvimento do Unreal](unreal-development-overview.md)
* [Visão geral de desenvolvimento do DirectX](directx-development-overview.md)
* [Arquivo do emulador do HoloLens](hololens-emulator-archive.md)
