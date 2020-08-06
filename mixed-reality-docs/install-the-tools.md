---
title: Instalar as ferramentas
description: Comece aqui para se preparar para o desenvolvimento de realidade misturada. Este artigo sempre deve refletir as versões mais recentes do Unity, do Visual Studio e das outras ferramentas recomendadas para o desenvolvimento de headset imersivo do HoloLens e do Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 07/31/2020
ms.topic: article
ms.localizationpriority: high
keywords: atualizado, ferramentas, começar, noções básicas, unity, visual studio, kit de ferramentas
ms.openlocfilehash: f5c779aa0bb89fe66b53419b03ec1b4d3e6b562b
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476878"
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

Agora que você tem o Windows 10, o Visual Studio e o SDK do Windows 10 prontos para uso, vamos escolher um mecanismo para a criação. 

[!INCLUDE[](~/includes/tools-overview.md)]
