---
title: Módulo MR Learning Base - a inicialização de projeto e o primeiro aplicativo
description: Conclua este curso para aprender a implementar o reconhecimento de Face do Azure dentro de um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, hololens de tutoriais, unity,
ms.openlocfilehash: 95ba00d68eb5fb6c990ddee343ac58ebe00dbb10
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993653"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>Módulo MR Learning Base - a inicialização de projeto e o primeiro aplicativo

Nesta primeira lição, você aprenderá alguns dos recursos que o Kit de ferramentas de realidade misturada tem a oferecer, iniciar seu primeiro aplicativo para o HoloLens 2 e implantá-lo para o dispositivo.

## <a name="objectives"></a>Objetivos

* Otimize o Unity para o desenvolvimento HoloLens.
* Importar ativos e configurar a cena.
* Visualização de malha espacial, as malhas de mão e o contador da taxa de quadros.

## <a name="instructions"></a>Instruções

### <a name="create-new-unity-project"></a>Criar novo projeto do Unity

1. Inicie o Unity.
2. Selecione **Novo**.
![Lição 1 Chapter1 Step2](images/Lesson1Chapter1Step2.JPG)
3. Insira um nome de projeto (por exemplo "MixedRealityBase").
![Lição 1 Chapter1 Step3](images/Lesson1Chapter1Step3.JPG)
4. Insira um local para salvar o projeto.
![Etapa 4 do Chapter1 lição 1](images/Lesson1Chapter1Step4.JPG)
5. Verifique se o projeto é definido como **3D**.
![Step 5 Chapter1 de lição 1](images/Lesson1Chapter1Step5.JPG)
6. Clique em **criar projeto**.
![Etapa 6 do Chapter1 lição 1](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configurar o projeto do Unity para Windows Mixed Reality

1. Abrir a janela de configurações de build indo até o arquivo > configurações de Build.
![Etapa 1 de Chapter4 lição 1](images/Lesson1Chapter4Step1.JPG)
2. Mudar para "Plataforma Universal do Windows", selecionando "Plataforma Universal do Windows" e, em seguida, clique no botão de "Alternar plataforma" para alternar as plataformas. Aplicativos em execução em 2 HoloLens são necessários para ser a plataforma Universal do Windows (UWP).
![Lição 1 Chapter4 Step2](images/Lesson1Chapter4Step2.JPG)
3. Habilitar realidade virtual clicando em configurações do Player na janela de compilação e, em seguida, no painel Inspetor habilitar a caixa de seleção "Suporte de realidade Virtual" em configurações XR, conforme mostrado na imagem abaixo. Observe que talvez seja necessário arrastar a janela de "Configurações de Build" fora do caminho para ver o painel do Inspetor. A caixa de seleção "Suporte de realidade Virtual" também se aplica a realidade misturada / headsets AR porque ele se refere a como a habilitação da visão estereoscópica (renderização imagens diferentes para cada olho.) ![Lição 1 Chapter4 Step3](images/Lesson1Chapter4Step3.JPG)
4. No painel de Inspetor, verifique que a caixa de seleção "Percepção espacial" na seção de recursos está habilitada em configurações de publicação. Percepção espacial nos permitirá visualizar a malha de mapeamento espacial em um dispositivo de realidade misturada, como o HoloLens 2. Configurações de publicação são encontradas no painel Inspetor acima "XR configurações" e em "Outras configurações."
![Etapa 4 do Chapter4 lição 1](images/Lesson1Chapter4Step4.JPG)

> OBSERVAÇÃO: Embora não usado nesta seção, alguns outros recursos comuns que talvez você queira habilitar incluem microfone (comandos de voz) e InternetClient (para conectar-se aos serviços que exigem uma conexão de rede)

### <a name="import-the-mixed-reality-toolkit"></a>Importar o Kit de ferramentas de realidade misturada

1. Baixe o [Kit de ferramentas de realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) unity empacotar e salvá-lo em uma pasta em seu computador.

2. Importar o pacote do Kit de ferramentas de realidade misturada, clicando em ativos > Importar > pacote personalizado. Localize o pacote do Kit de ferramentas de realidade misturada baixado na etapa 1 e abri-lo para começar o processo de importação. Aguarde alguns minutos para que o processo de importação.
    ![Lição 1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Step2b de Chapter2 da lição 1](images/Lesson1Chapter2Step2b.JPG)

3. Na próxima janela pop-up, clique em "Importar" para começar a importar o Kit de ferramentas de realidade mista. Verifique se que todos os itens são verificados, conforme mostrado na imagem. Se você vir uma caixa de diálogo pop-up solicitando a aplicar as configurações padrão de kit de ferramentas de realidade misturada, clique em "Aplicar".
    ![Lição 1 Chapter2 Step3](images/Lesson1Chapter2Step3.JPG) ![Step3 de Chapter2 da lição 1](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configurar o Kit de ferramentas de realidade misturada

1. Configurar o Kit de ferramentas misto selecionando no menu barra Kit de ferramentas de realidade misturada > configurar. Se você não vir esse item de menu depois de importar o Kit de ferramentas de realidade misturada, reinicie o Unity.
![Etapa 1 de Chapter3 lição 1](images/Lesson1Chapter3Step1.JPG)
2. Sua cena agora terá vários novos itens e as modificações do Kit de ferramentas de realidade mista. Salvar sua cena com um nome diferente clicando em arquivo > Salvar como e nomeie sua cena, por exemplo, BaseScene. Mantenha sua cena, organizada por salvá-lo para a pasta "Cenas" na pasta de ativos do seu projeto.
![Lição 1 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
![Step2b de Chapter3 da lição 1](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Crie seu aplicativo para seu dispositivo

1. Se você fechou a janela de configurações de compilação das seções anteriores, abra a janela de configurações de compilação novamente indo para o arquivo > configurações de Build.
    ![Etapa 1 de Chapter5 lição 1](images/Lesson1Chapter5Step1.JPG)

2. Certifique-se de que a cena para experimentar está na lista "Cenas em compilação" clicando no botão "Adicionar cenas aberto".

3. Pressione o botão de compilação para iniciar o processo de compilação.
    ![Lição 1 Chapter5 Step3](images/Lesson1Chapter5Step3.JPG)

4. Crie e nomeie uma nova pasta para o seu aplicativo. Na imagem abaixo, uma pasta com o nome "Aplicativo" foi criado para conter o aplicativo. Clique em "Selecionar pasta" para começar a criar a pasta recém-criada. Após a compilação, você pode fechar a janela "Configurações de Build" no Unity. 
    ![Etapa 4 do Chapter5 lição 1](images/Lesson1Chapter5Step4.JPG)

  > OBSERVAÇÃO: Se a compilação falhar, tente compilar novamente ou reiniciar o Unity e compilar novamente. Se você vir um erro, como "Erro: Erro CS0246 = o nome do namespace ou digite "XX" não pôde ser encontrado (está faltando um usando diretiva ou uma referência de assembly?) ", em seguida, você talvez precise instalar [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. Depois que a compilação for concluída, abra a pasta de recém-criado que contém os arquivos do aplicativo recém-criado. Clique duas vezes na solução "MixedRealityBase.sln" (ou o nome correspondente, se você usou um nome alternativo para o seu projeto) para abrir o arquivo de solução no Visual Studio.

  > Observação: Certifique-se de abrir a recém-criado pasta (ou seja, "Aplicativo", se estiver seguindo as convenções de nomenclatura das etapas anteriores), pois haverá um arquivo. sln nomeado da mesma forma, fora da pasta que não deve ser confundido com o arquivo. sln dentro da pasta de compilação. 

![Step 5 Chapter5 de lição 1](images/Lesson1Chapter5Step5.JPG)

  > Observação: Se o Visual Studio solicita a instalação de novos componentes, reserve um momento para garantir que todos os componentes de pré-requisito são instalados como especificado no [a página de "Instalar as ferramentas"](install-the-tools.md)

6. Conecte sua 2 HoloLens no seu PC com o cabo USB. Enquanto essas instruções de lição pressupõem que você estiver implantando um teste com um dispositivo de 2 HoloLens, você também pode optar por implantar o [HoloLens 2 emulador](using-the-hololens-emulator.md) ou optar por criar um [pacote do aplicativo para o sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Antes de compilar para seu dispositivo, certifique-se de que o dispositivo está no modo de desenvolvedor. Se isso for a primeira vez que implantar 2 HoloLens, Visual Studio pode solicitar que você emparelhar seu 2 HoloLens com um pin. Siga [estas instruções](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se você precisar habilitar o modo de desenvolvedor ou emparelhar com o Visual Studio.

8. Configure o Visual Studio para compilar seu 2 HoloLens, selecionando a configuração "Versão" e a arquitetura de "ARM".
    ![Lição 1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. A etapa final é criar ao seu dispositivo, selecionando Depurar > Iniciar sem depuração. Selecionar "Start without Debugging" fará com que o aplicativo para iniciar imediatamente em seu dispositivo após uma compilação bem-sucedida, mas sem informações de depuração que aparece no Visual Studio. Isso também significa que você pode desconectar o cabo USB, enquanto o aplicativo está em execução em seu 2 HoloLens sem interromper o aplicativo. Você também pode selecionar Build > implantar a solução para implantar seu dispositivo sem a necessidade do aplicativo for iniciado automaticamente.
    ![Lição 1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Parabéns!

Agora, você agora tem implantou seu primeiro aplicativo HoloLens 2. Como você conduz ao redor, você deve ver uma malha espacial cobrir todas as superfícies que foi vistas por 2 o HoloLens. Além disso, você verá indicadores em suas mãos e dedos para acompanhamento de mão e um contador da taxa de quadros para manter o olho no desempenho do aplicativo. Essas são apenas algumas das partes fundamentais, incluídas prontos, com o Kit de ferramentas de realidade mista. As lições são fornecidos, você começará adicionando mais conteúdo e interatividade à sua cena, portanto, você pode explorar totalmente os recursos de 2 a HoloLens e o Kit de ferramentas de realidade mista.

>Observação: Você abordará como ativar e desativar o contador da taxa de quadros usando um comando de voz em [lição 5](mrlearning-base-ch5.md)

[Próxima lição: Interface do usuário, mão de acompanhamento e misto de configuração do Kit de ferramentas de realidade](mrlearning-base-ch2.md)
