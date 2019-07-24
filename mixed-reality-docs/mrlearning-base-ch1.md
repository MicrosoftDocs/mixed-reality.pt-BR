---
title: Módulo básico de aprendizagem de MR - Inicialização de projeto e primeiro aplicativo
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 51cfc123f7da8d25a53eecfb730f60cf10fe7377
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387787"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inicializando o projeto e o primeiro aplicativo

Nesta primeira lição, você aprenderá sobre alguns dos recursos que o MRTK (Kit de ferramentas de realidade mista) tem a oferecer, iniciar seu primeiro aplicativo para o HoloLens 2 e implantá-lo no dispositivo.

## <a name="objectives"></a>Objetivos

* Otimizar o Unity para o desenvolvimento no HoloLens.
* Importar ativos e configurar a cena.
* Visualizar a malha espacial, as malhas de mão e o contador da taxa de quadros.

## <a name="instructions"></a>Instruções

### <a name="create-new-unity-project"></a>Crie um novo projeto do Unity

1. Inicie o Unity.
2. Selecione **Novo**.
![Lição1 Capítulo1 Etapa2](images/Lesson1Chapter1Step2.JPG)
3. Insira um nome de projeto (por exemplo, "MixedRealityBase").
![Lição1 Capítulo1 Etapa3](images/Lesson1Chapter1Step3.JPG)
4. Insira um local para salvar o projeto.
![Lição1 Capítulo1 Etapa4](images/Lesson1Chapter1Step4.JPG)
5. Verifique se o projeto está definido como **3D**.
![Lição1 Capítulo1 Etapa5](images/Lesson1Chapter1Step5.JPG)
6. Clique em **Criar Projeto**.
![Lição1 Capítulo1 Etapa6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configure o projeto do Unity para o Windows Mixed Reality

1. Abra a janela configurações de Build acessando arquivo > configurações de Build.
![Lição1 Capítulo4 Etapa1](images/Lesson1Chapter4Step1.JPG)
2. Alterne para Plataforma Universal do Windows selecionando Plataforma Universal do Windows. Clique no botão Alternar plataforma para alternar as plataformas. Os aplicativos em execução no HoloLens 2 devem ser compatíveis com o Plataforma Universal do Windows (UWP).
![Lição1 Capítulo4 Etapa2](images/Lesson1Chapter4Step2.JPG)
3. Habilite a realidade virtual clicando em configurações do Player na janela criar e habilite a caixa de seleção suporte à realidade virtual em configurações de XR no painel Inspetor, conforme mostrado na imagem abaixo. Observe que talvez seja necessário arrastar a janela configurações de compilação para ver o painel inspetor. A caixa de seleção com suporte da realidade virtual também se aplica à realidade mista e aos headsets da realidade aumentada, pois ela se refere à habilitação da visão estereoscópico (renderizando imagens diferentes para cada olho). ![Lição1 Capítulo4 Etapa3](images/Lesson1Chapter4Step3.JPG)
4. No mesmo painel do Inspetor, verifique se a caixa de seleção percepção espacial na seção recursos está habilitada em configurações de publicação. A percepção espacial nos permite visualizar a malha de mapeamento espacial em um dispositivo de realidade misturada, como o HoloLens 2. As configurações de publicação são encontradas no painel Inspetor, acima da XR Settings e em outras configurações.
![Lição1 Capítulo4 Etapa4](images/Lesson1Chapter4Step4.JPG)

> OBSERVAÇÃO: Embora não seja usado nesta seção, alguns recursos comuns que talvez você queira habilitar incluem o microfone para comandos de voz e InternetClient para se conectar a serviços que exigem uma conexão de rede.

### <a name="import-the-mixed-reality-toolkit"></a>Importe o Kit de ferramentas de realidade misturada

1. Baixe o pacote de Unity do [Kit de ferramentas da realidade mista](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) e salve-o em uma pasta no seu computador.

2. Importe o pacote do Kit de ferramentas de realidade misturada, clicando em Ativos > Importar > Pacote Personalizado. Localize o pacote do Kit de ferramentas de realidade misturada baixado na Etapa 1 e abra-o para começar o processo de importação. Aguarde alguns minutos para a conclusão do processo de importação.
    ![Lição1 Capítulo2 Etapa2a](images/Lesson1Chapter2Step2a.JPG) ![Lição1 Capítulo2 Etapa2b](images/Lesson1Chapter2Step2b.JPG)

3. Na próxima janela pop-up, clique em importar para começar a importar o kit de ferramentas de realidade misturada. Verifique se todos os itens estão marcados conforme mostrado na imagem. Se você vir uma caixa de diálogo pop-up solicitando a aplicação das configurações padrão do kit de ferramentas da realidade misturada, clique em aplicar.
    ![Lição1 Capítulo2 Etapa3](images/Lesson1Chapter2Step3.JPG) ![Lição1 Capítulo2 Etapa3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configure o Kit de ferramentas de realidade misturada

1. Configure o MRTK selecionando o kit de ferramentas de realidade misturada > Configurar na barra de menus. Se você não vir esse item de menu depois de importar o Kit de ferramentas de realidade misturada, reinicie o Unity.
  ![Lição1 Capítulo3 Etapa1](images/Lesson1Chapter3Step1.JPG)

  > Observação: Você pode ver uma caixa de diálogo pop-up solicitando a seleção de um perfil para o kit de ferramentas de realidade misturada. Nesse caso, selecione OK e escolha o perfil chamado "DefaultMixedRealityToolkitConfigurationProfile".

2. Sua cena terá vários novos itens e modificações no MRTK. Salve sua cena com um nome diferente clicando em arquivo > salvar como e dê um nome à sua cena, como BaseScene. Mantenha sua cena organizada salvando-a na pasta de cenas na pasta de ativos do projeto.
  ![Lição1 Capítulo3 Etapa2a](images/Lesson1Chapter3Step2a.JPG)
  ![Lição1 Capítulo3 Etapa2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Crie o aplicativo para seu dispositivo

1. Se você fechou a janela configurações de compilação das seções anteriores, abra a janela configurações de compilação novamente indo para arquivo > configurações de Build.
    ![Lição1 Capítulo5 Etapa1](images/Lesson1Chapter5Step1.JPG)

2. Verifique se a cena que você deseja tentar está nos bastidores na lista de Build clicando no botão Adicionar cenas abertas.

3. Pressione o botão Compilar para iniciar o processo de compilação.
    ![Lição1 Capítulo5 Etapa3](images/Lesson1Chapter5Step3.JPG)

4. Crie e dê um nome para uma nova pasta para o seu aplicativo. Na imagem abaixo, uma pasta com o nome aplicativo foi criada para conter o aplicativo. Clique em Selecionar pasta para começar a criar na pasta recém-criada. Após a conclusão da compilação, você pode fechar a janela configurações de compilação no Unity. 
    ![Lição1 Capítulo5 Etapa4](images/Lesson1Chapter5Step4.JPG)

  > OBSERVAÇÃO: se a compilação falhar, tente compilar novamente ou reiniciar o Unity e compilar novamente. Se você vir um erro, como "erro: CS0246 = não foi possível encontrar o nome do tipo ou namespace "XX" (está faltando uma diretiva using ou uma referência de assembly?). Nesse caso, talvez seja necessário instalar o [SDK do Windows 10 (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. Depois que a compilação for concluída, abra a pasta recém-criada que contém os arquivos do novo aplicativo. Clique duas vezes na solução MixedRealityBase. sln ou no nome correspondente, se você tiver usado um nome alternativo para o seu projeto, para abrir o arquivo de solução no Visual Studio.

  > Observação: Certifique-se de abrir a pasta recém-criada (ou seja, a pasta do aplicativo, se seguir as convenções de nomenclatura das etapas anteriores), pois haverá um arquivo. sln nomeado de forma semelhante fora dessa pasta que não deve ser confundido com o arquivo. sln dentro da pasta de compilação. 

![Lição1 Capítulo5 Etapa5](images/Lesson1Chapter5Step5.JPG)

  > Observação: se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para garantir que todos os componentes necessários sejam instalados conforme especificado na [página "Instalar as ferramentas"](install-the-tools.md).

6. Conecte seu HoloLens 2 em seu PC. Embora essas instruções presumam que você implantará um teste com um dispositivo de HoloLens 2, você também pode optar por implantar no emulador do [hololens 2](using-the-hololens-emulator.md) ou optar [por criar um pacote de aplicativo para Sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Antes de compilar para seu dispositivo, verifique se ele está no Modo de Desenvolvedor. Se esta for a primeira vez que você está implantando no HoloLens 2, o Visual Studio pode solicitar que você emparelhe o seu HoloLens 2 com um PIN. Siga [estas instruções](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se você precisar ativar o modo de desenvolvedor ou emparelhar com o Visual Studio.

8. Configure o Visual Studio para a criação de seu HoloLens 2 selecionando a configuração de versão e a arquitetura ARM.
    ![Lição1 Capítulo5 Etapa8](images/Lesson1Chapter5Step8.JPG)

9. A etapa final é criar seu dispositivo selecionando Debug > Iniciar sem depuração. A seleção de iniciar sem depuração faz com que o aplicativo inicie imediatamente em seu dispositivo após uma compilação bem-sucedida, mas sem informações de depuração aparecendo no Visual Studio. Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo. Você também pode selecionar compilar > implantar solução para implantar em seu dispositivo sem que o aplicativo seja iniciado automaticamente.
    ![Lição1 Capítulo5 Etapa9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Parabéns

Agora você implantou seu primeiro aplicativo do HoloLens 2. Ao percorrer, você deve ver uma malha espacial que cobre todas as superfícies que foram percebidas pelo HoloLens 2. Além disso, você deve ver indicadores em mãos e dedos para acompanhamento à mão e um contador de taxa de quadros para ficar atento ao desempenho do aplicativo. Essas são apenas algumas das partes fundamentais predefinidas no Kit de ferramentas de realidade misturada. Nas lições a serem fornecidas, você começa a adicionar mais conteúdo e interatividade à sua cena para que possa explorar totalmente os recursos do HoloLens 2 e do kit de ferramentas de realidade misturada.

>Observação: você verá como ativar e desativar o contador da taxa de quadros usando um comando de voz na [Lição 5](mrlearning-base-ch5.md).

[Próxima lição: Interface do usuário, acompanhamento de mão e configuração do Kit de Ferramentas de Realidade Misturada](mrlearning-base-ch2.md)
