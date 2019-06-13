---
title: Módulo básico de aprendizagem de MR - Inicialização de projeto e primeiro aplicativo
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: c5490e6a3b542a5ca677b309e5ed1171f8666fe7
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "65814007"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>Módulo básico de aprendizagem de MR - Inicialização de projeto e primeiro aplicativo

Nesta primeira lição, você aprenderá alguns dos recursos que o Kit de ferramentas de realidade misturada tem a oferecer, iniciará seu primeiro aplicativo para o HoloLens 2 e o implantará no dispositivo.

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

1. Abra a janela de configurações de compilação, acessando Arquivo > Configurações de Compilação.
![Lição1 Capítulo4 Etapa1](images/Lesson1Chapter4Step1.JPG)
2. Alterne para a "Plataforma Universal do Windows", selecionando "Plataforma Universal do Windows" e, em seguida, clique no botão "Alternar Plataforma" para alternar as plataformas. Os aplicativos em execução no HoloLens 2 precisam ser da Plataforma Universal do Windows (UWP).
![Lição1 Capítulo4 Etapa2](images/Lesson1Chapter4Step2.JPG)
3. Habilite a realidade virtual clicando nas Configurações do Player na Janela de Compilação e, no painel do inspetor, marque a caixa de seleção "Suporte à Realidade Virtual" nas configurações de XR, conforme mostrado na imagem abaixo. Observe que talvez seja necessário arrastar a janela de "Configurações de Compilação" para longe para ver o painel do inspetor. A caixa de seleção "Suporte à Realidade Virtual" também se aplica aos headsets de realidade misturada/RA porque trata da ativação da visão estereoscópica (renderização de imagens diferentes para cada olho.) ![Lição1 Capítulo4 Etapa3](images/Lesson1Chapter4Step3.JPG)
4. No painel do inspetor, verifique se a caixa de seleção "Percepção Espacial" está marcada na seção de recursos, sob as Configurações de Publicação. A Percepção Espacial nos permitirá visualizar a malha de mapeamento espacial em um dispositivo de realidade misturada, como o HoloLens 2. As Configurações de Publicação são encontradas no painel do inspetor, acima das "Configurações de XR" e em "Outras Configurações".
![Lição1 Capítulo4 Etapa4](images/Lesson1Chapter4Step4.JPG)

> OBSERVAÇÃO: embora não sejam usados nesta seção, alguns outros recursos comuns que talvez você queira ativar incluem o Microfone (para comandos de voz) e o InternetClient (para conectar-se aos serviços que exigem uma conexão de rede).

### <a name="import-the-mixed-reality-toolkit"></a>Importe o Kit de ferramentas de realidade misturada

1. Baixe o pacote Unity do [Kit de ferramentas de realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) e salve-o em uma pasta em seu computador.

2. Importe o pacote do Kit de ferramentas de realidade misturada, clicando em Ativos > Importar > Pacote Personalizado. Localize o pacote do Kit de ferramentas de realidade misturada baixado na Etapa 1 e abra-o para começar o processo de importação. Aguarde alguns minutos para a conclusão do processo de importação.
    ![Lição1 Capítulo2 Etapa2a](images/Lesson1Chapter2Step2a.JPG) ![Lição1 Capítulo2 Etapa2b](images/Lesson1Chapter2Step2b.JPG)

3. Na próxima janela pop-up, clique em "Importar" para começar a importar o Kit de ferramentas de realidade misturada. Verifique se que todos os itens estão marcadas, conforme mostrado na imagem. Se você vir uma caixa de diálogo pop-up solicitando-o para aplicar as configurações padrão do Kit de ferramentas de realidade misturada, clique em "Aplicar".
    ![Lição1 Capítulo2 Etapa3](images/Lesson1Chapter2Step3.JPG) ![Lição1 Capítulo2 Etapa3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configure o Kit de ferramentas de realidade misturada

1. Configure o Kit de ferramentas de realidade misturada selecionando na barra de menus Kit de Ferramentas de Realidade Misturada > Configurar. Se você não vir esse item de menu depois de importar o Kit de ferramentas de realidade misturada, reinicie o Unity.
![Lição1 Capítulo3 Etapa1](images/Lesson1Chapter3Step1.JPG)
2. Sua cena agora terá vários novos itens e as modificações do Kit de ferramentas de realidade misturada. Salve sua cena com outro nome, clicando em Arquivo > Salvar Como e dê um nome para sua cena, por exemplo, BaseScene. Mantenha sua cena, organizada, salvando-a na pasta "Cenas" na pasta de Ativos do seu projeto.
![Lição1 Capítulo3 Etapa2a](images/Lesson1Chapter3Step2a.JPG)
![Lição1 Capítulo3 Etapa2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Crie o aplicativo para seu dispositivo

1. Se você fechou a janela de Configurações de compilação das seções anteriores, abra-a novamente em Arquivo > Configurações de Compilação.
    ![Lição1 Capítulo5 Etapa1](images/Lesson1Chapter5Step1.JPG)

2. Verifique se a cena que você deseja experimentar está na lista de "Cenas em Compilação", clicando no botão "Adicionar Cenas Abertas".

3. Pressione o botão Compilar para iniciar o processo de compilação.
    ![Lição1 Capítulo5 Etapa3](images/Lesson1Chapter5Step3.JPG)

4. Crie e dê um nome para uma nova pasta para o seu aplicativo. Na imagem abaixo, uma pasta com o nome "Aplicativo" foi criada para armazenar o aplicativo. Clique em "Selecionar Pasta" para começar a compilar na pasta recém-criada. Após a compilação, você pode fechar a janela "Configurações de Compilação" no Unity. 
    ![Lição1 Capítulo5 Etapa4](images/Lesson1Chapter5Step4.JPG)

  > OBSERVAÇÃO: se a compilação falhar, tente compilar novamente ou reiniciar o Unity e compilar novamente. Se você vir um erro, como "Erro: CS0246 = O nome do tipo ou do namespace ‘XX’ não pôde ser encontrado (não pode ser encontrado (está faltando uma diretiva using ou uma referência de assembly?) ", talvez precise instalar o [SDK do Windows 10 (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>).
  >

5. Depois que a compilação for concluída, abra a pasta recém-criada que contém os arquivos do novo aplicativo. Clique duas vezes na solução "MixedRealityBase.sln" (ou no nome correspondente, se você usou um nome alternativo para o seu projeto) para abrir o arquivo de solução no Visual Studio.

  > Observação: certifique-se de abrir a pasta recém-criada (ou seja, "Aplicativo", se estiver seguindo as convenções de nomenclatura das etapas anteriores), pois haverá um arquivo .sln com nome semelhante fora dessa pasta que não deve ser confundido com o arquivo .sln dentro da pasta de compilação. 

![Lição1 Capítulo5 Etapa5](images/Lesson1Chapter5Step5.JPG)

  > Observação: se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para garantir que todos os componentes necessários sejam instalados conforme especificado na [página "Instalar as ferramentas"](install-the-tools.md).

6. Conecte o HoloLens 2 ao computador usando o cabo USB. Embora essas instruções pressuponham que você esteja implantando um teste com um dispositivo HoloLens 2, também é possível optar por implantar o [emulador do HoloLens 2](using-the-hololens-emulator.md) ou criar um [pacote do aplicativo para sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>).

7. Antes de compilar para seu dispositivo, verifique se ele está no Modo de Desenvolvedor. Se for a primeira vez que você implanta o HoloLens 2, o Visual Studio pode solicitar o emparelhamento do seu HoloLens 2 com um pin. Siga [estas instruções](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se você precisar ativar o modo de desenvolvedor ou emparelhar com o Visual Studio.

8. Configure o Visual Studio para compilar seu HoloLens 2, selecionando a configuração "Versão" e a arquitetura "ARM".
    ![Lição1 Capítulo5 Etapa8](images/Lesson1Chapter5Step8.JPG)

9. A etapa final é compilar para seu dispositivo, selecionando Depurar > Iniciar sem Depuração. Selecionar "Iniciar sem Depuração" fará com que o aplicativo inicie imediatamente em seu dispositivo após uma compilação bem-sucedida, mas sem exibir informações de Depuração no Visual Studio. Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo. Você também pode selecionar Compilação > Implantar Solução para implantar seu dispositivo sem iniciar o aplicativo automaticamente.
    ![Lição1 Capítulo5 Etapa9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Parabéns

Você acabou de implantar seu primeiro aplicativo do HoloLens 2. Enquanto caminha, você deve ver uma malha espacial cobrindo todas as superfícies percebidas pelo HoloLens 2. Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo. Essas são apenas algumas das partes fundamentais predefinidas no Kit de ferramentas de realidade misturada. Nas próximas lições, você começará a adicionar conteúdo e interatividade à sua cena, de modo a explorar totalmente os recursos do HoloLens 2 e do Kit de ferramentas de realidade misturada.

>Observação: você verá como ativar e desativar o contador da taxa de quadros usando um comando de voz na [Lição 5](mrlearning-base-ch5.md).

[Próxima lição: Interface do usuário, acompanhamento de mão e configuração do Kit de Ferramentas de Realidade Misturada](mrlearning-base-ch2.md)
