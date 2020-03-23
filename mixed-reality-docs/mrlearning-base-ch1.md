---
title: Tutoriais de introdução – 2. Inicializar o projeto e seu primeiro aplicativo
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 56adb4bfc66768684c8269c0f0cafd70c486ea8a
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376203"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inicializar o projeto e seu primeiro aplicativo

## <a name="overview"></a>Visão geral

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
Neste primeiro tutorial, você aprenderá mais sobre algumas das funcionalidades que o <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Kit de Ferramentas de Realidade Misturada)</a> tem a oferecer, iniciará seu primeiro aplicativo do HoloLens 2 e o implantará no dispositivo.

## <a name="objectives"></a>Objetivos

* Configurar o Unity para o desenvolvimento no HoloLens
* Importar ativos e configurar a cena
* Visualização da malha de mapeamento espacial, das malhas de mão e do contador da taxa de quadros

## <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)
* SDK do Windows 10 10.0.18362.0 ou posterior
* Alguma habilidade básica de programação em C#
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.2.X instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado

> [!IMPORTANT]
> A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.2.X. Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.

## <a name="create-new-unity-project"></a>Crie um novo projeto do Unity

Inicie o **Hub do Unity**, selecione a guia **Projetos** e clique na **seta para baixo** ao lado do botão **Novo**:

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

Selecione a versão do Unity especificada na seção [Pré-requisitos](#prerequisites) acima:

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

Na janela Criar um novo projeto:

* Verifique se **Modelos** está definido como **3D**
* Insira um **Nome de Projeto** adequado, por exemplo, _Tutoriais do MRTK_
* Escolha um **Local** adequado para armazenar seu projeto, por exemplo, _D:\MixedRealityLearning_
* Clique no botão **Criar** para criar e iniciar o novo projeto do Unity

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> Ao trabalhar no Windows, há um limite de MAX_PATH de 255 caracteres. O Unity é afetado por esses limites e pode falhar ao compilar se algum caminho de arquivo tiver mais de 255 caracteres. Consequentemente, é altamente recomendável armazenar seu projeto do Unity o mais próximo possível da raiz da unidade.

Aguarde até que o Unity crie o projeto:

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configure o projeto do Unity para o Windows Mixed Reality

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

Nesta seção, você mudará a plataforma de build, habilitará a realidade virtual e habilitará a percepção espacial.

### <a name="1-switch-build-platform"></a>1. Alternar plataforma de build

No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

Na janela Configurações de Build, selecione **Plataforma Universal do Windows** e clique no botão **Mudar Plataforma**:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

Aguarde até que o Unity termine de mudar a plataforma:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

Quando o Unity terminar de mudar a plataforma, clique no ícone vermelho **x** para fechar a janela Configurações de Build:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a>2. Habilitar realidade virtual

> [!NOTE]
> Habilitar a realidade virtual também se aplica aos headsets de realidade misturada e realidade aumentada, pois se refere à habilitação da visão estereoscópica, ou seja, renderização de imagens diferentes para cada olho.

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

Na janela Configurações de Projeto, selecione **Player** > **Configurações de XR** para expandir as Configurações de XR:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

Nas Configurações de XR, marque a caixa de seleção **Realidade Virtual Compatível** para habilitar a realidade virtual e, em seguida, clique no ícone **+** e selecione **Windows Mixed Reality** para adicionar o SDK do Windows Mixed Reality:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

Aguarde até que o Unity termine de adicionar o SDK:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

Quando o Unity terminar de adicionar o SDK, otimize as Configurações de XR da seguinte maneira:

* Defina o **Formato de Profundidade** do Windows Mixed Reality como **Profundidade de 16 bits**
* Marque a caixa de seleção **Habilitar Compartilhamento de Profundidade** do Windows Mixed Reality
* Defina o **Modo de Renderização\*** de Estéreo como **Instância de Passagem Única**

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> Para saber mais sobre a otimização do Unity para o Windows Mixed Reality, consulte a documentação [Configurações recomendadas para o Unity](recommended-settings-for-unity.md).

### <a name="3-enable-spatial-perception"></a>3. Habilitar percepção espacial

> [!NOTE]
> A percepção espacial permite a visualização da malha de mapeamento espacial em dispositivos com Windows Mixed Reality.

Na janela Configurações de Projeto, selecione **Player** > **Configurações de Publicação** para expandir as Configurações de Publicação:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

Nas Configurações de Publicação, role para baixo até a seção **Recursos** e marque a caixa de seleção **SpatialPerception**:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

Feche a janela Configurações do Projeto.

## <a name="import-textmesh-pro-essential-resources"></a>Importar recursos do TextMesh Pro Essential

> [!NOTE]
> Estamos importando este pacote porque ele é necessário para elementos da interface do usuário do Kit de Ferramentas de Realidade Misturada.

No menu do Unity, selecione **Janela** > **TextMeshPro** > **Importar recursos essenciais do TMP**:

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a>Importe o Kit de ferramentas de realidade misturada

Baixe o pacote personalizado do Unity:

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

No menu do Unity, selecione **Ativos** > **Importar Pacote** > **Pacote Personalizado...** para abrir a janela Importar pacote...:

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

Na janela Importar pacote..., selecione o **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** que você baixou e clique no botão **Abrir**:

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a>Configurar o projeto do Unity para o Kit de Ferramentas de Realidade Misturada

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

Depois que o pacote tiver sido importado, a janela Configurador de Projeto do MRTK deverá aparecer. Se não aparecer, abra a janela selecionando **Kit de Ferramentas de Realidade Misturada** > **Utilidades** > **Configurar Projeto do Unity** no menu do Unity.

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

Na janela Configurador de Projeto do MRTK, expanda a seção **Modificar Configurações**, <u>desmarque</u> a caixa de seleção **Habilitar MSBuild para Unity**, verifique se todas as outras opções estão marcadas e clique no botão **Aplicar** para aplicar as configurações:

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> O MSBuild para Unity pode não ser compatível com todos os SDKs que você usará e pode ser complicado desabilitá-lo depois que ele tiver sido habilitado. Consequentemente, é altamente recomendável não habilitar o MSBuild para o Unity.

## <a name="configure-the-mixed-reality-toolkit"></a>Configure o Kit de ferramentas de realidade misturada
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Adicionar à Cena e Configurar...** para adicionar o Kit de Ferramentas de Realidade Misturada à cena atual:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

Com o objeto MixedRealityToolkit selecionado na janela Hierarquia, na janela Inspetor, verifique se o perfil de configuração do Kit de Ferramentas de Realidade Misturada está definido como **DefaultMixedRealityToolkitConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

> [!IMPORTANT]
> Normalmente, você usará o DefaultHoloLens2ConfigurationProfile ao desenvolver para o HoloLens 2. No entanto, para fins deste tutorial, você usará o DefaultMixedRealityToolkitConfigurationProfile. Depois, no próximo tutorial, [Como criar a interface do usuário e configurar o Kit de Ferramentas de Realidade Misturada](mrlearning-base-ch2.md), altere para o DefaultHoloLens2ConfigurationProfile.

No menu do Unity, selecione **Arquivo** > **Salvar Como...** para abrir a janela Salvar Cena:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

Na janela Salvar cena, navegue até a pasta **Cenas** do seu projeto, dê um nome adequado à sua cena (por exemplo, _Introdução_) e clique no botão **Salvar** para salvar a cena:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a>Crie o aplicativo para seu dispositivo

### <a name="1-build-the-unity-project"></a>1. Compilar o projeto do Unity

No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build.

Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar sua cena atual à lista **Cenas no Build** e clique no botão **Build** para abrir a janela Compilar Plataforma Universal do Windows:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

Na janela Compilar Plataforma Universal do Windows, escolha um local adequado para armazenar seu build, por exemplo, _D:\MixedRealityLearning\Builds_, crie uma nova pasta e dê a ela um nome adequado, por exemplo, _GettingStarted_ e, em seguida, clique no botão **Selecionar Pasta** para iniciar o processo de build:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

Aguarde até que o Unity conclua o processo de build:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Compilar e implantar o aplicativo

Quando o processo de build for concluído, o Unity solicitará que o Explorador de Arquivos do Windows abra o local em que você armazenou o build. Navegue dentro da pasta e clique duas vezes no arquivo da solução para abri-lo no Visual Studio:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar que todos os componentes necessários estejam instalados conforme especificado na documentação [Instalar as Ferramentas](install-the-tools.md).

Configure o Visual Studio para o HoloLens 2 selecionando a configuração **Mestre** ou **Versão**, a arquitetura **ARM** e o **Dispositivo** como destino:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

> [!NOTE]
> Se você não vir o dispositivo como uma opção, talvez seja necessário alterar o projeto de inicialização padrão do projeto IC2Lpp para seu Projeto UWP. No **Gerenciador de Soluções**, clique com o botão direito do mouse em **nomedoseuprojeto (Windows Universal)** e selecione **Definir como Projeto de Inicialização**. 

Conecte o HoloLens 2 ao seu computador.

> [!IMPORTANT]
> Antes de compilar no dispositivo, ele precisa estar no Modo de Desenvolvedor e emparelhado com o computador de desenvolvimento. Essas duas etapas podem ser concluídas seguindo [estas instruções](using-visual-studio.md).

A etapa final é compilar e implantar no dispositivo selecionando **Depurar** > **Iniciar Sem Depuração**:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

Embora essas instruções pressuponham que você esteja implantando em um dispositivo HoloLens 2, você também pode implantar no [emulador do HoloLens 2](using-the-hololens-emulator.md) ou criar um [pacote do aplicativo para sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).

A seleção de Iniciar sem Depuração faz com que o aplicativo seja iniciado imediatamente no dispositivo após um build bem-sucedido, mas sem o depurador anexado e sem exibir as informações no Visual Studio. Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo.

Para implantar em seu dispositivo sem iniciar o aplicativo automaticamente, selecione Build > Implantar Solução.

## <a name="congratulations"></a>Parabéns

<!-- TODO: Consider cleanup and adding in app screenshots -->
Você acabou de implantar seu primeiro aplicativo do HoloLens 2. Enquanto caminha, você deverá ver uma malha de mapeamento espacial cobrindo todas as superfícies que foram percebidas pelo HoloLens 2. Além disso, você deverá ver indicadores em suas mãos e seus dedos para o acompanhamento da mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo. Essas são apenas algumas das partes fundamentais predefinidas no Kit de ferramentas de realidade misturada. Nos próximos tutoriais, você começará a adicionar mais conteúdo e interatividade à cena, de modo a explorar totalmente as funcionalidades do HoloLens 2 e do Kit de Ferramentas de Realidade Misturada.

> [!NOTE]
> No aplicativo, note o criador de perfil de Diagnóstico; você pode alternar sua visibilidade usando o comando de fala **Alternar Diagnóstico**. No entanto, geralmente é recomendável manter o criador de perfil visível o tempo todo durante o desenvolvimento para entender quando as alterações no aplicativo podem impactar o desempenho, por exemplo, o aplicativo HoloLens 2 deve [ser executado continuamente a 60 FPS](understanding-performance-for-mixed-reality.md).

[Próximo tutorial: 3. Criar a interface do usuário e configurar o Kit de Ferramentas de Realidade Misturada](mrlearning-base-ch2.md)
