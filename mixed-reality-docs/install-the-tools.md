---
title: Instalar as ferramentas
description: Comece aqui para se preparar para o desenvolvimento de realidade misturada. Este artigo sempre deve refletir as versões mais recentes do Unity, do Visual Studio e das outras ferramentas recomendadas para o desenvolvimento de headset imersivo do HoloLens e do Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, começar, noções básicas, unity, visual studio, kit de ferramentas
ms.openlocfilehash: d2b9a3718845e755a5cd8d9866ec9716ee0c0609
ms.sourcegitcommit: 40b37104b0aec4554502dcc7dc430e340a6fa46a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "77092040"
---
# <a name="install-the-tools"></a>Instalar as ferramentas

Obtenha as ferramentas necessárias para criar aplicativos para os headsets imersivos (VR) do Microsoft HoloLens e do Windows Mixed Reality. Não há nenhum SDK separado para o desenvolvimento no Windows Mixed Reality; você usará o Visual Studio com o SDK do Windows 10.

Não tem um dispositivo de realidade misturada? Você pode instalar o [emulador do HoloLens](using-the-hololens-emulator.md) para testar algumas funcionalidades de aplicativos de realidade misturada sem um HoloLens. Você também pode usar o [simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md) para testar seus aplicativos de realidade misturada para headsets imersivos.

É recomendável instalar o mecanismo de jogos Unity como a maneira mais fácil de começar a criar aplicativos de realidade misturada. No entanto, você também poderá criar com base no DirectX se quiser usar um mecanismo personalizado.

>[!TIP]
>Adicione esta página aos favoritos e acesse-a regularmente para se manter atualizado sobre a versão mais recente de cada ferramenta recomendada para o desenvolvimento de realidade misturada.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>Lista de verificação da instalação


| Ferramenta | Descrição | Observações |
|---------|---------|---------|
| ![Logotipo do Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (link de instalação manual)</a> | Instale a versão mais recente do Windows 10, para que o sistema operacional do seu computador corresponda à plataforma para a qual você está compilando aplicativos de realidade misturada. | **Instalação do Windows 10** <br> <ul><li>Você pode instalar a versão mais recente do Windows 10 via Windows Update nas Configurações ou criando uma mídia de instalação, usando o link na coluna à esquerda.<li>Veja as [notas de versão atuais](release-notes-october-2018.md) para obter informações sobre os recursos mais recentes de realidade misturada disponíveis em cada versão do Windows 10.</ul> **Ative o modo de desenvolvedor no seu computador** em Configurações > Atualização e Segurança > Para Desenvolvedores. <br><br> **Observação para computadores empresariais e corporativos:** se o computador for gerenciado pelo departamento de TI da sua organização, talvez seja necessário contatá-los para atualizar. <br><br> **"N" versões do Windows:** Headsets imersivos (VR) do Windows Mixed Reality não são compatíveis com as versões "N" do Windows. |
| ![Logotipo do Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.2 ou superior)** (link de instalação)</a> | Ambiente de desenvolvimento integrado (IDE) completo para Windows e muito mais. Você usará o Visual Studio para escrever o código, depurar, testar e implantar. | **Cargas de trabalho a instalar:** <ul><li>Desenvolvimento para desktop com C++</li><li>Desenvolvimento de aplicativos da UWP (Plataforma Universal do Windows)</li></ul>**Observação sobre o Unity:** a menos que você esteja tentando instalar intencionalmente uma versão (não LTS) mais recente do Unity para uma finalidade específica, recomendamos *não* instalar a carga de trabalho do Unity como parte da instalação do Visual Studio. Em vez disso, instale o fluxo 2018.4 LTS do Unity, conforme indicado abaixo.<br> <br>**Observação**: há alguns problemas conhecidos com a depuração de aplicativos de realidade misturada no Visual Studio 2019 versão 16.0.  Verifique se você atualizou o Visual Studio 2019 para a versão 16.2 ou superior. |
| ![Logotipo do Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**SDK do Windows 10 (10.0.18362.0)** (link de instalação manual)</a> | Fornece os cabeçalhos, bibliotecas, metadados e ferramentas mais recentes para a compilação de aplicativos do Windows 10 no HoloLens 2. | Para compilar aplicativos do HoloLens 2, você precisará instalar o SDK do Windows, build 18362 ou posterior.<br> <br> Se você estiver desenvolvendo aplicativos somente para headsets do Windows Mixed Reality de área de trabalho ou HoloLens (1ª geração), poderá usar o SDK do Windows instalado pelo Visual Studio 2017. |
| ![Logotipo do Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2114824" target="_blank">**Emulador do HoloLens 2 (atualização de janeiro de 2020)** (link de instalação: 10.0.18362.1044)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulador do HoloLens (1ª geração)** (link de instalação: 10.0.17763.134)</a> | O emulador permite executar aplicativos em uma imagem de máquina virtual do HoloLens sem um HoloLens físico.<br> <br> | Veja [Usando o emulador do HoloLens](using-the-hololens-emulator.md) para obter mais informações sobre como começar a usar o emulador.<br> <br> **O sistema deve ser compatível com Hyper-V** para a instalação do emulador ser bem-sucedida. Consulte a seção de Requisitos de sistema abaixo para obter detalhes. <br>|

## <a name="choose-your-engine"></a>Escolha seu mecanismo

:::row:::
    :::column:::
       [![Unity](images/unity_logo.png)](https://unity3d.com/unity/qa/lts-releases?version=2018.4)<br>
        **[Unity](https://unity3d.com/unity/qa/lts-releases?version=2018.4)**<br>
        É recomendável usar o fluxo LTS (suporte a longo prazo) do Unity, que é a melhor versão para iniciar novos projetos. Atualize para a revisão mais recente para obter as correções estáveis mais recentes.<br> <br>A recomendação atual é usar o **Unity 2018.4.x**, que é o build LTS necessário para o MRTK v2 abaixo.<br> <br>Alguns desenvolvedores talvez queiram usar uma versão diferente do Unity por motivos específicos. Nesses casos, o Unity oferece suporte a instalações lado a lado de versões diferentes.<br><br>
        [![MRTK](images/final_mrtk-small_logo.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)<br>**[MRTK (Kit de Ferramentas de Realidade Misturada)](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)**<br>O MRTK (Kit de Ferramentas de Realidade Misturada) v2 para Unity é um kit de desenvolvimento multiplataforma de software livre para aplicativos de realidade misturada.<br><br> O MRTK v2 destina-se a acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR. O projeto visa reduzir as barreiras de entrada para criar aplicativos de realidade misturada e contribuir com a comunidade à medida que nosso trabalho progride.
    :::column-end:::
    :::column:::
        [![Unreal](images/Unreal_logo.png)](https://docs.unrealengine.com//GettingStarted/Installation/index.html)<br>
        **[Unreal](https://docs.unrealengine.com//GettingStarted/Installation/index.html)**<br>
        O Unreal Engine 4 é um mecanismo de criação avançado e de software livre com suporte completo para realidade misturada em C++ e Blueprints.<br> <br>No momento, o suporte do HoloLens para Unreal Engine 4.23 está na versão beta.
    :::column-end:::
    :::column:::
        [![Modelos do aplicativo DirectX](images/visualstudio-small_logo.png)](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)<br>
        **[DirectX](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)**<br>
        Os modelos do aplicativo Windows Mixed Reality fornecem todos os elementos essenciais necessários para começar a escrever um aplicativo de realidade misturada usando o DirectX com APIs nativas. Inclui um loop de renderização (ou “loop de jogo”), uma classe auxiliar DeviceResources para gerenciar o dispositivo e o contexto Direct3D e um exemplo simples de renderizador de holograma. Disponível para Direct3D11 e Direct3D 12.
    :::column-end:::
:::row-end:::

<br>

## <a name="mixed-reality-toolkit-mrtk"></a>MRTK (Kit de Ferramentas de Realidade Misturada)

O Kit de ferramentas de realidade misturada fornece componentes e recursos para acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR. O projeto visa reduzir as barreiras de entrada para criar aplicativos de realidade misturada e contribuir com a comunidade à medida que nosso trabalho progride.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Kit de Ferramentas de Realidade Misturada</a> – uma coleção de scripts e componentes destinados a acelerar o desenvolvimento de aplicativos de realidade misturada.
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Kit de Ferramentas de Realidade Misturada-Unity</a> – usa código do kit de ferramentas básico e facilita seu consumo no Unity.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Kit Complementar de Realidade Misturada</a> – bits de código e componentes que não podem ser executados diretamente no HoloLens ou nos headsets imersivos (VR), mas que se emparelham com eles para criar experiências destinadas ao Windows Mixed Reality.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Como configurar seu computador para o desenvolvimento de realidade misturada

O SDK do Windows 10 funciona melhor no sistema operacional Windows 10. Esse SDK também é compatível com: Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Observe que nem todas as ferramentas são compatíveis com sistemas operacionais mais antigos. 

### <a name="for-hololens-development"></a>Desenvolvimento para o HoloLens

Ao configurar seu computador para o desenvolvimento para o HoloLens, verifique se ele atende aos requisitos de sistema do <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> e o <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Se você planeja usar o emulador do HoloLens (1º geração), verifique se o computador também atende aos [requisitos de sistema do emulador do HoloLens](using-the-hololens-emulator.md#hololens-emulator-system-requirements).

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
