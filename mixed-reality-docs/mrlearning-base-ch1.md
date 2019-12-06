---
title: Tutoriais de introdução – 2. Inicializar o projeto e seu primeiro aplicativo
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: realidade misturada, Unity, tutorial, HoloLens
ms.openlocfilehash: cae2398582d399f2bad56b354694f7e99ef8681c
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539695"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inicializar o projeto e seu primeiro aplicativo

Nesta primeira lição, você aprenderá mais sobre algumas das funcionalidades que o [MRTK (Kit de Ferramentas de Realidade Misturada)]() tem a oferecer, iniciará seu primeiro aplicativo do HoloLens 2 e o implantará no dispositivo.

## <a name="objectives"></a>Objetivos

* Otimizar o Unity para o desenvolvimento no HoloLens.
* Importar ativos e configurar a cena.
* Visualização da malha de mapeamento espacial, das malhas da mão e do contador da taxa de quadros.

## <a name="instructions"></a>Instruções

### <a name="create-new-unity-project"></a>Crie um novo projeto do Unity

1. Inicie o Unity.
2. Selecione **Novo**.
![Lesson1 Section1 Step2](images/mrlearning-base-ch1-1-step2.JPG)

3. Insira um nome de projeto (por exemplo, "MixedRealityBase").
![Lesson1 Section1 Step3](images/mrlearning-base-ch1-1-step3.JPG)
4. Insira um local para salvar o projeto.
![Lesson1 Section1 Step4](images/mrlearning-base-ch1-1-step4.JPG)
5. Verifique se o projeto está definido como **3D**.
![Lesson1 Section1 Step5](images/mrlearning-base-ch1-1-step5.JPG)
6. Clique em **Criar Projeto**.
![Lesson1 Section1 Step6](images/mrlearning-base-ch1-1-step6.JPG)


### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configure o projeto do Unity para o Windows Mixed Reality

1. Abra a janela *Configurações de Build* acessando **Arquivo** > **Configurações de Build**.
![Lesson1 Section2 Step1](images/mrlearning-base-ch1-2-step1.JPG)
2. Selecione a *Plataforma Universal do Windows* e clique no botão **Alternar Plataforma** para alternar as plataformas. Os aplicativos em execução no HoloLens 2 precisam ser compatíveis com o UWP (Plataforma Universal do Windows).
![Lesson1 Section2 Step2](images/mrlearning-base-ch1-2-step2.JPG)
3. Habilite a realidade virtual clicando no botão **Configurações do Player** na janela de build e habilite a caixa de seleção *Realidade Virtual Compatível* nas configurações de XR no painel do inspetor, conforme mostrado na imagem abaixo. Observe que talvez seja necessário arrastar a janela *Configurações de Build* para o lado para ver o painel do inspetor. A caixa de seleção *Realidade Virtual Compatível* também se aplica aos headsets de realidade misturada e realidade aumentada, pois se refere à habilitação da visão estereoscópica (renderização de imagens diferentes para cada olho). ![Lesson1 Section2 Step3](images/mrlearning-base-ch1-2-step3.JPG)
4. Também nas configurações de XR, altere o *Modo de Renderização Estéreo* para *Instanciado de Passagem Única*. Esse [estilo de pipeline de renderização](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) geralmente tem o melhor desempenho no HoloLens 2. Se estiver interessado em outras configurações de alto desempenho para o ambiente do Unity, siga [estas instruções](recommended-settings-for-unity.md).
![Lesson1 Section2 Step4](images/mrlearning-base-ch1-2-step4.jpg)
5. No mesmo painel do inspetor, verifique se a caixa de seleção *Percepção Espacial* está marcada na seção de funcionalidades em *Configurações de Publicação*. A Percepção Espacial nos permite visualizar a malha de mapeamento espacial em um dispositivo de realidade misturada, como o HoloLens 2. As Configurações de Publicação são encontradas no painel do inspetor, acima das Configurações de XR e em Outras Configurações.
![Lesson1 Section2 Step5](images/mrlearning-base-ch1-2-step5.JPG)

    > [!NOTE]
    > Embora não sejam usadas nesta seção, algumas outras funcionalidades comuns que talvez você queira habilitar incluem o *Microfone* para comandos de voz e o *InternetClient* para se conectar aos serviços que exigem uma conexão de rede.

### <a name="import-the-mixed-reality-toolkit"></a>Importe o Kit de ferramentas de realidade misturada

1. Baixe o [pacote de fundamentos versão 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) do [Kit de Ferramentas de Realidade Misturada](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) para Unity e salve-o em uma pasta no computador.

2. Importe o pacote do *Kit de Ferramentas de Realidade Misturada* baixado na etapa anterior. Comece clicando em **Ativos** > **Importar** > **Pacote Personalizado**, selecione *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* e abra-o para iniciar o processo de importação. Aguarde alguns minutos para a conclusão do processo de importação.
    ![Lesson1 Section3 Step2a](images/mrlearning-base-ch1-3-step2a.JPG) ![Lesson1 Section3 Step2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. Na próxima janela pop-up, clique em **Importar** para iniciar a importação do pacote selecionado para o projeto do Unity. Verifique se todos os itens estão marcados, conforme mostrado na imagem.
    ![Lesson1 Section3 Step3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > Se uma caixa de diálogo pop-up for exibida solicitando a aplicação das configurações padrão do Kit de Ferramentas de Realidade Misturada, clique em **Aplicar**. O MRTK analisa o projeto para ver se há configurações recomendadas ausentes quando importadas para instalação automatizada. Dependendo de suas configurações, o pop-up pode parecer diferente da imagem abaixo.

    ![Lesson1 Section3 Step4 Note1](images/mrlearning-base-ch1-3-step4-note1.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configure o Kit de ferramentas de realidade misturada

1. Adicione o *Kit de Ferramentas de Realidade Misturada* à cena atual selecionando **Kit de Ferramentas de Realidade Misturada** > **Adicionar à Cena e Configurar...** na barra de menus. Se você não vir esse item de menu depois de importar o Kit de Ferramentas de Realidade Misturada, reinicie o Unity.
    ![Lesson1 Section4 Step1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > Talvez você veja uma caixa de diálogo pop-up para a seleção de um [perfil para o Kit de Ferramentas de Realidade Misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html). Escolha o perfil chamado *DefaultHoloLens2ConfigurationProfile* clicando duas vezes nele.

2. A cena terá vários novos itens e modificações. Salve a cena com outro nome clicando em **Arquivo** > **Salvar como...** e dê um nome à cena, por exemplo, *BaseScene*. Mantenha a cena organizada salvando-a na pasta *Cenas* da pasta *Ativos* do projeto.
    ![Lesson1 Section4 Step2a](images/mrlearning-base-ch1-4-step2a.JPG) ![Lesson1 Section4 Step2b](images/mrlearning-base-ch1-4-step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Crie o aplicativo para seu dispositivo

1. Se você fechou a janela *Configurações de Build* nas seções anteriores, abra a janela *Configurações de Build* novamente acessando **Arquivo** > **Configurações de Build**.
    ![Lesson1 Section5 Step1](images/mrlearning-base-ch1-5-step1.JPG)

2. Verifique se a cena recém-criada está na lista *Cenas no Build* clicando no botão **Adicionar Cenas Abertas** enquanto a cena está aberta no Unity.

3. Pressione o botão **Compilar** para iniciar o processo de build.
    ![Lesson1 Section5 Step3](images/mrlearning-base-ch1-5-step3.JPG)

4. Crie e dê um nome para uma nova pasta para o seu aplicativo. Na imagem abaixo, uma pasta com o nome App foi criada para armazenar o aplicativo. Clique em **Selecionar Pasta** para iniciar o build na pasta recém-criada. Após a conclusão do build, feche a janela *Configurações de Build* no Unity.
    ![Lesson1 Section5 Step4](images/mrlearning-base-ch1-5-step4.JPG)

  > [!IMPORTANT]
  > se a compilação falhar, tente compilar novamente ou reiniciar o Unity e compilar novamente. Se você receber um erro, como "Erro: CS0246 = O tipo ou o nome do namespace “XX” não pôde ser encontrado (uma diretiva using ou uma referência de assembly está ausente?). Nesse caso, talvez seja necessário instalar o [SDK do Windows 10 (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)

5. Depois que a compilação for concluída, abra a pasta recém-criada que contém os arquivos do novo aplicativo. Clique duas vezes na solução *MixedRealityBase.sln* ou no nome correspondente, caso tenha usado um nome alternativo para o projeto, para abrir o arquivo de solução no Visual Studio.

    > [!NOTE]
    > Lembre-se de abrir a pasta recém-criada (ou seja, a pasta *App*, caso esteja seguindo as convenções de nomenclatura das etapas anteriores), pois haverá um arquivo .sln com nome semelhante fora dessa pasta que não deve ser confundido com o arquivo .sln dentro da pasta de build. A estrutura de pastas deve ser semelhante à imagem abaixo.
    >
    > Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar que todos os componentes necessários estejam instalados conforme especificado na [página "Instalar as ferramentas"](install-the-tools.md)

    ![Lesson1 Section5 Step5](images/mrlearning-base-ch1-5-step5.JPG)

6. Conecte o HoloLens 2 ao computador. Embora essas instruções pressuponham que você esteja fazendo a implantação em um dispositivo HoloLens 2, você também pode optar por implantar o [emulador do HoloLens 2](using-the-hololens-emulator.md) ou criar um [pacote do aplicativo para sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)

    > [!IMPORTANT]
    > Antes do build no dispositivo, o dispositivo precisa estar no *Modo de Desenvolvedor* e emparelhado com o computador de desenvolvimento. Essas duas etapas podem ser concluídas seguindo [estas instruções](using-visual-studio.md)

7. Configure o Visual Studio para o build no HoloLens 2 selecionando a configuração *Versão* ou *Mestre*, a arquitetura *ARM* e *Dispositivo* como o destino.
    ![Lesson1 Section5 Step8](images/mrlearning-base-ch1-5-step7.JPG)

8. A etapa final é o build e a implantação no dispositivo por meio da seleção de **Depurar** > **Iniciar sem depuração**. A seleção de *Iniciar sem Depuração* faz com que o aplicativo seja iniciado imediatamente no dispositivo após um build bem-sucedido, mas sem o depurador anexado e sem exibir as informações no Visual Studio. Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo.

    > [!NOTE]
    > Selecione também **Build** > **Implantar Solução** para a implantação no dispositivo sem fazer com que o aplicativo seja iniciado automaticamente.

    ![Lesson1 Section5 Step9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>Parabéns

Você acabou de implantar seu primeiro aplicativo do HoloLens 2. Enquanto caminha, você deverá ver uma malha de mapeamento espacial cobrindo todas as superfícies que foram percebidas pelo HoloLens 2. Além disso, você deverá ver indicadores em suas mãos e seus dedos para o acompanhamento da mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo. Essas são apenas algumas das partes fundamentais predefinidas no Kit de ferramentas de realidade misturada. Nas próximas lições, você começará a adicionar mais conteúdo e interatividade à cena, de modo a explorar totalmente as funcionalidades do HoloLens 2 e do Kit de Ferramentas de Realidade Misturada.

> [!NOTE]
> No aplicativo, é possível observar o criador de perfil visual. Você verá como ativar/desativar o contador da taxa de quadros usando um comando de voz na [Lição 5](mrlearning-base-ch5.md). Geralmente, é recomendado manter o criador de perfil visual visível em todos os momentos durante o desenvolvimento para entender quando as alterações de código podem ter afetado o desempenho. O aplicativo do HoloLens 2 deve [ser executado continuamente a 60 FPS](understanding-performance-for-mixed-reality.md).

[Próxima lição: 3. Criar a interface do usuário e configurar o Kit de Ferramentas de Realidade Misturada](mrlearning-base-ch2.md)
