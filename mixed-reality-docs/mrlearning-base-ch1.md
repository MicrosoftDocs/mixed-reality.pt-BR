---
title: Tutoriais de introdução-2. Inicializando o projeto e o primeiro aplicativo
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 3bf218b42ea8abed45a80c0dd048e791cdd8372b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926883"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. inicializando o projeto e o primeiro aplicativo

Nesta primeira lição, você aprenderá sobre alguns dos recursos que o [MRTK (Kit de ferramentas de realidade mista)]() tem a oferecer, iniciar seu primeiro aplicativo para o HoloLens 2 e implantá-lo no dispositivo.

## <a name="objectives"></a>Objetivos

* Otimizar o Unity para o desenvolvimento no HoloLens.
* Importar ativos e configurar a cena.
* Visualização da malha de mapeamento espacial, malhas à mão e o contador de taxa de quadros.

## <a name="instructions"></a>Instruções

### <a name="create-new-unity-project"></a>Crie um novo projeto do Unity

1. Inicie o Unity.
2. Selecione **Novo**.
![lição 1 section1 etapa 2](images/mrlearning-base-ch1-1-step2.JPG)

3. Insira um nome de projeto (por exemplo, "MixedRealityBase").
![lição 1 section1 etapa 3](images/mrlearning-base-ch1-1-step3.JPG)
4. Insira um local para salvar o projeto.
![lição 1 section1 etapa 4](images/mrlearning-base-ch1-1-step4.JPG)
5. Verifique se o projeto está definido como **3D**.
![lição 1 section1 Step5](images/mrlearning-base-ch1-1-step5.JPG)
6. Clique em **Criar Projeto**.
![lição 1 section1 etapa 6](images/mrlearning-base-ch1-1-step6.JPG)


### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configure o projeto do Unity para o Windows Mixed Reality

1. Abra a janela *configurações de Build* acessando **arquivo** > configurações de **Build**.
![lição 1 Section2 etapa 1](images/mrlearning-base-ch1-2-step1.JPG)
2. Selecione o *plataforma universal do Windows* e clique no botão **alternar plataforma** para alternar as plataformas. Os aplicativos em execução no HoloLens 2 devem ser compatíveis com o Plataforma Universal do Windows (UWP).
![lição 1 Section2 etapa 2](images/mrlearning-base-ch1-2-step2.JPG)
3. Habilite a realidade virtual clicando no botão **configurações do Player** na janela criar e habilite a caixa de seleção *suporte à realidade virtual* em configurações de XR no painel Inspetor, conforme mostrado na imagem abaixo. Observe que talvez seja necessário arrastar a janela *configurações de compilação* para ver o painel inspetor. A caixa de seleção *com suporte da realidade virtual* também se aplica à realidade mista e aos headsets da realidade aumentada, pois ela se refere à habilitação da visão estereoscópico (renderizando imagens diferentes para cada olho). ![lição 1 Section2 etapa 3](images/mrlearning-base-ch1-2-step3.JPG)
4. Também em configurações de XR, altere o *modo de renderização de estéreo* para *passagem única com instância*. Esse [estilo de pipeline de renderização](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) geralmente é o melhor desempenho para o HoloLens 2. Se estiver interessado em outras configurações de alto desempenho para seu ambiente de Unity, siga [estas instruções](recommended-settings-for-unity.md).
![lição 1 Section2 etapa 4](images/mrlearning-base-ch1-2-step4.jpg)
5. No mesmo painel do Inspetor, verifique se a caixa de seleção *percepção espacial* na seção recursos está habilitada em *configurações de publicação*. A percepção espacial nos permite visualizar a malha de mapeamento espacial em um dispositivo de realidade misturada, como o HoloLens 2. As configurações de publicação são encontradas no painel Inspetor, acima da XR Settings e em outras configurações.
![lição 1 Section2 Step5](images/mrlearning-base-ch1-2-step5.JPG)

    > [!NOTE]
    > Embora não seja usado nesta seção, alguns recursos comuns que talvez você queira habilitar incluem o *microfone* para comandos de voz e *internetclient* para se conectar a serviços que exigem uma conexão de rede.

### <a name="import-the-mixed-reality-toolkit"></a>Importe o Kit de ferramentas de realidade misturada

1. Baixe a [versão 2.1.0 do pacote](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) do [Kit de ferramentas da realidade mista](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) do Unity Foundation e salve-a em uma pasta em seu computador.

2. Importe o pacote do *Kit de ferramentas da realidade mista* que você baixou na etapa anterior. Comece clicando em **ativos** > **importar** > **pacote personalizado** e selecione *Microsoft. MixedReality. Toolkit. Unity. Foundation. 2.1.0. unitypackage* e abra-o para iniciar o processo de importação. Aguarde alguns minutos para que o processo de importação seja concluído.
    ![lição 1 Section3 Step2a](images/mrlearning-base-ch1-3-step2a.JPG) ![lição 1 Section3 Step2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. Na próxima janela pop-up, clique em **importar** para começar a importar o pacote selecionado para o projeto do Unity. Verifique se todos os itens estão marcados conforme mostrado na imagem.
    ![lição 1 Section3 etapa 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > Se você vir uma caixa de diálogo pop-up solicitando a aplicação das configurações padrão do kit de ferramentas da realidade misturada, clique em **aplicar**. O MRTK analisa seu projeto para qualquer configuração recomendada ausente quando importada para a instalação automatizada. Dependendo das configurações, o pop-up pode parecer diferente da imagem abaixo.

    ![Lição 1 Section3 etapa 4 Note1](images/mrlearning-base-ch1-3-step4-note1.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configure o Kit de ferramentas de realidade misturada

1. Adicione o *Kit de ferramentas de realidade misturada* à sua cena atual selecionando o **Kit de ferramentas de realidade misturada** > **Adicionar à cena e configurar..** na barra de menus. Se você não vir esse item de menu depois de importar o Kit de ferramentas de realidade misturada, reinicie o Unity.
    ![lição 1 Section4 etapa 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > Você pode ver uma caixa de diálogo pop-up para selecionar um [perfil para o kit de ferramentas da realidade misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html). Escolha o perfil chamado *DefaultHoloLens2ConfigurationProfile* clicando duas vezes nele.

2. Sua cena terá vários novos itens e modificações. Salve sua cena com um nome diferente clicando em **arquivo** > **salvar como...** e dê um nome à sua cena, como *BaseScene*. Mantenha sua cena organizada salvando-a na pasta de *cenas* na pasta de *ativos* do projeto.
    ![lição 1 Section4 Step2a](images/mrlearning-base-ch1-4-step2a.JPG) ![lição 1 Section4 Step2b](images/mrlearning-base-ch1-4-step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Crie o aplicativo para seu dispositivo

1. Se você fechou a janela *configurações de compilação* das seções anteriores, abra a janela configurações de *compilação* novamente indo para **arquivo** > **configurações de Build**.
    ![lição 1 Section5 etapa 1](images/mrlearning-base-ch1-5-step1.JPG)

2. Verifique se a cena que você acabou de criar está nos *bastidores na* lista de Build clicando no botão **Adicionar cenas abertas** enquanto sua cena está aberta no Unity.

3. Pressione o botão **Compilar** para iniciar o processo de compilação.
    ![lição 1 Section5 etapa 3](images/mrlearning-base-ch1-5-step3.JPG)

4. Crie e dê um nome para uma nova pasta para o seu aplicativo. Na imagem abaixo, uma pasta com o nome aplicativo foi criada para conter o aplicativo. Clique em **Selecionar pasta** para começar a criar na pasta recém-criada. Após a conclusão da compilação, você pode fechar a janela *configurações de compilação* no Unity.
    ![lição 1 Section5 etapa 4](images/mrlearning-base-ch1-5-step4.JPG)

  > [!IMPORTANT]
  > se a compilação falhar, tente compilar novamente ou reiniciar o Unity e compilar novamente. Se você vir um erro, como "erro: CS0246 = o tipo ou nome do namespace" XX "não pôde ser encontrado (está faltando uma diretiva using ou uma referência de assembly?). Nesse caso, talvez seja necessário instalar o [SDK do Windows 10 (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)

5. Depois que a compilação for concluída, abra a pasta recém-criada que contém os arquivos do novo aplicativo. Clique duas vezes na solução *MixedRealityBase. sln* ou no nome correspondente, se você tiver usado um nome alternativo para o seu projeto, para abrir o arquivo de solução no Visual Studio.

    > [!NOTE]
    > Certifique-se de abrir a pasta recém-criada (ou seja, a pasta do *aplicativo* , se seguir as convenções de nomenclatura das etapas anteriores), pois haverá um arquivo. sln nomeado de forma semelhante fora dessa pasta que não deve ser confundido com o arquivo. sln dentro da pasta de compilação. A estrutura de pastas deve ser semelhante à imagem abaixo.
    >
    > se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para garantir que todos os componentes necessários sejam instalados conforme especificado na [página "Instalar as ferramentas"](install-the-tools.md).

    ![Lição 1 Section5 Step5](images/mrlearning-base-ch1-5-step5.JPG)

6. Conecte seu HoloLens 2 em seu PC. Embora essas instruções presumam que você estará implantando em um dispositivo de HoloLens 2, você também pode optar por implantar no [emulador do hololens 2](using-the-hololens-emulator.md) ou optar por criar um [pacote de aplicativo para Sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)

    > [!IMPORTANT]
    > Antes de criar seu dispositivo, o dispositivo deve estar no *modo de desenvolvedor* e emparelhado com o computador de desenvolvimento. Essas duas etapas podem ser concluídas seguindo [estas instruções](using-visual-studio.md)

7. Configure o Visual Studio para a criação de seu HoloLens 2 selecionando a *versão* ou a configuração *mestre* , a arquitetura *ARM* e o *dispositivo* como destino.
    ![lição 1 Section5 Step8](images/mrlearning-base-ch1-5-step7.JPG)

8. A etapa final é criar e implantar em seu dispositivo selecionando **Debug** > **Iniciar sem depuração**. Selecionar *Iniciar sem depuração* faz com que o aplicativo inicie imediatamente em seu dispositivo após uma compilação bem-sucedida, mas sem o depurador anexado e as informações que aparecem no Visual Studio. Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo.

    > [!NOTE]
    > Você também pode selecionar **compilar** > **implantar solução** para implantar em seu dispositivo sem que o aplicativo seja iniciado automaticamente.

    ![Lição 1 Section5 Step9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>Parabéns

Agora você implantou seu primeiro aplicativo do HoloLens 2. Ao percorrer, você deve ver uma malha de mapeamento espacial que cobre todas as superfícies que foram percebidas pelo HoloLens 2. Além disso, você deve ver indicadores em mãos e dedos para acompanhamento à mão e um contador de taxa de quadros para ficar atento ao desempenho do aplicativo. Essas são apenas algumas das partes fundamentais predefinidas no Kit de ferramentas de realidade misturada. Nas lições a serem fornecidas, você começará a adicionar mais conteúdo e interatividade à sua cena para que você possa explorar totalmente os recursos do HoloLens 2 e do kit de ferramentas de realidade misturada.

> [!NOTE]
> No aplicativo, você pode observar o criador de perfil do Visual. Você explicará como alternar o contador de taxa de quadros usando um comando de voz na [lição 5](mrlearning-base-ch5.md). Geralmente, é recomendável manter o criador de perfil Visual visível em todos os momentos durante o desenvolvimento para entender quando as alterações de código podem ter impactado o desempenho. O aplicativo HoloLens 2 deve [ser executado continuamente às 60 fps](understanding-performance-for-mixed-reality.md).

[Próxima lição: 3. criando a interface do usuário e Configurando o kit de ferramentas de realidade mista](mrlearning-base-ch2.md)
