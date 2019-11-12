---
title: TUTORIAIS dos serviços de fala do Azure-1. Integrando e usando o reconhecimento de fala e a transcrição
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: defa33e56cfe4450a8d42855bd11dc23973dc401
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913500"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. integrando e usando o reconhecimento de fala e a transcrição

Este tutorial cria um aplicativo de realidade misturada que explora o uso do SDK de fala dos serviços cognitivas do Azure com o HoloLens 2. Quando terminar com esta série de tutoriais, você poderá usar o microfone do dispositivo para transcrever a fala para o texto em tempo real, traduzir sua fala em outras linguagens e aproveitar o recurso de intenção do SDK de fala para entender os comandos de voz usando inteligência artificial.

## <a name="objectives"></a>Objetivos

- Saiba como integrar o SDK de fala do Azure em um aplicativo do HoloLens 2
- Saiba como usar comandos de voz
- Saiba como usar os recursos de fala para texto

## <a name="instructions"></a>Instruções

### <a name="getting-started"></a>Introdução

1. Inicie o Unity e crie um novo projeto. Insira o nome do projeto módulo de aprendizagem do SDK de fala. Escolha um local para onde salvar o projeto. Em seguida, clique em criar projeto.

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    >Verifique se o modelo está definido como 3D, conforme mostrado na imagem acima.

2. Baixe a [versão 2.1.0 do pacote](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) do [Kit de ferramentas da realidade mista](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) do Unity Foundation e salve-a em uma pasta em seu computador. Importe o pacote para o projeto do Unity. Para obter instruções detalhadas sobre como fazer isso, consulte os [tutoriais de introdução – lição 2. Inicializando o projeto e o primeiro aplicativo](mrlearning-base-ch1.md).

3. Baixe e importe o [SDK de fala](https://aka.ms/csspeech/unitypackage) do Azure para o pacote de ativos do Unity. Importe o pacote do SDK de fala clicando em ativos, selecionando importar pacote e, em seguida, selecionando pacote personalizado. Localize o pacote do SDK de fala baixado anteriormente e abra-o para iniciar o processo de importação.

    ![mrlearning-Speech-CH1-1-step3a. png](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-Speech-CH1-1-step3b. png](images/mrlearning-speech-ch1-1-step3b.png)

4. Na próxima janela pop-up, clique em importar para começar a importar o pacote do SDK de fala. Verifique se todos os itens estão marcados conforme mostrado na imagem abaixo.

    ![mrlearning-Speech-CH1-1-step4. png](images/mrlearning-speech-ch1-1-step4.png)

5. Baixe o pacote de ativos do módulo SDK de fala, também conhecido como pacote Lunarcom clicando nesse [link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2). O pacote de ativos do Lunarcom é uma coleção de ativos e scripts desenvolvidos para esta série de lições para demonstrar um uso prático do SDK de fala do Azure. É um terminal de comando de voz que, por fim, fará a interface com a experiência de montagem do módulo lunar desenvolvida nos [tutoriais de introdução – lição 7. Criando um aplicativo de exemplo de módulo lunar](mrlearning-base-ch6.md).

6. Importe o pacote de ativos do Lunarcom para seu projeto do Unity seguindo as etapas semelhantes que você levou para importar o kit de ferramentas e o SDK de fala misturados da realidade.

7. Configure o MRTK (Kit de ferramentas de realidade mista).

    Para fazer isso, clique no painel do kit de ferramentas da realidade misturada na parte superior da janela e, em seguida, selecione Adicionar à cena e configurar.

    ![mrlearning-Speech-CH1-1-step7a. png](images/mrlearning-speech-ch1-1-step7a.png)

    No pop-up que aparece, selecione DefaultHoloLens2ConfigurationProfile para torná-lo o perfil ativo do kit de ferramentas de realidade misturada.

    ![mrlearning-Speech-CH1-1-step7b. png](images/mrlearning-speech-ch1-1-step7b.png)

8. Sua cena agora tem vários novos itens da MRTK. Salve sua cena com um nome diferente clicando em "arquivo" e, em seguida, em "salvar como" e nomeie sua cena como SpeechScene.

    >[!NOTE]
    >Se você pressionar reproduzir em sua cena depois de adicionar o MRTK ao seu projeto e ele não entrar no modo de reprodução, talvez seja necessário reiniciar o Unity.

9. Com o objeto MixedRealityToolkit selecionado em sua hierarquia de cena, clique em copiar & Personalizar no painel inspetor para abrir o pop-up perfil de clonagem. No pop-up perfil de clonagem, insira um nome adequado para seu perfil personalizado, por exemplo, HoloLens2ConfigurationProfile personalizado, e clique em clonar para criar seu perfil de configuração personalizado e defini-lo como o perfil ativo.

    ![mrlearning-Speech-CH1-1-Step9. png](images/mrlearning-speech-ch1-1-step9.png)

10. Também no painel Inspetor (com o objeto MixedRealityToolkit selecionado em sua hierarquia), desabilite o sistema de diagnóstico desmarcando a caixa à direita de habilitar o sistema de diagnóstico.

    ![mrlearning-Speech-CH1-1-step10. png](images/mrlearning-speech-ch1-1-step10.png)

11. Neste tutorial, estamos usando os comandos de fala de entrada para reconhecimento e transcrição de fala. Vamos clonar o perfil de entrada para fazer alterações nas configurações de fala.

    Com o objeto MixedRealityToolkit ainda selecionado na sua hierarquia de cena, clique no botão clonar pequeno no painel inspetor para abrir o pop-up perfil de clonagem. No pop-up perfil de clonagem, insira um nome adequado para seu perfil personalizado, por exemplo, HoloLens2InputSystemProfile personalizado, e clique em clonar para criar seu perfil de sistema de entrada personalizado e defini-lo como o perfil ativo.

    ![mrlearning-Speech-CH1-1-step11. png](images/mrlearning-speech-ch1-1-step11.png)

12. Depois que o perfil de entrada for clonado, expanda a seção fala e siga o mesmo processo da etapa anterior para clonar o perfil de comandos de fala.

    ![mrlearning-Speech-CH1-1-step12. png](images/mrlearning-speech-ch1-1-step12.png)

13. Agora, na seção fala, vá para configurações gerais e altere comportamento de início para início manual.

    ![mrlearning-Speech-CH1-1-step13. png](images/mrlearning-speech-ch1-1-step13.png)

14. No painel projeto, expanda a pasta Lunarcom e arraste o Lunarcom_Base pré-fabricado para sua hierarquia de cena.

    ![mrlearning-Speech-CH1-1-step14. png](images/mrlearning-speech-ch1-1-step14.png)

15. Selecione o objeto Lunarcom_Base em sua hierarquia e verifique se a posição está definida como x = 0, y = 0 e z = 0, bem como a rotação definida como x = 0, y = 0 e z = 0. Defina a escala como leitura x = 0.008, y = 0.008 e z = 0,01.

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. Clique em Adicionar componente e procure e selecione controlador Lunarcom. Esse script está incluído no pacote de ativos do Lunarcom que você importou na etapa 6.

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. Para conectar nosso aplicativo aos serviços cognitivas do Azure, você deve inserir uma chave de assinatura (também conhecida como chave de API) para o serviço de fala. Siga as instruções [aqui](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) para obter uma chave de assinatura gratuita. Depois de obter a chave de assinatura, insira-a no campo chave de API do serviço de fala do componente LunarcomController no painel Inspetor, conforme mostrado na imagem abaixo.

18. Insira a região que você escolheu ao se inscrever na chave de assinatura no campo região do serviço de fala do componente LunarcomController no painel inspetor. Por exemplo, para a região oeste dos EUA, digite "westus".

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. Em sua hierarquia, expanda o objeto Lunarcom_Base clicando na seta à esquerda dele. Em seguida, faça o mesmo para seu objeto filho "terminal", conforme mostrado na imagem abaixo.

20. Enquanto Lunarcom_Base estiver selecionado, clique e arraste Lunarcom texto da hierarquia para o slot de texto de saída no componente LunarcomController no painel Inspetor, conforme mostrado na imagem abaixo.

21. Faça a mesma coisa com o objeto de terminal no slot de terminal e no objeto de luz de conexão para o slot do controlador de luz de conexão.

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. Clique na seta ao lado da seção de botões Lunarcom do script LunarcomController no painel Inspetor e altere o tamanho para 3. Pressione Enter ou Return. Isso faz com que três novos campos de elemento sejam exibidos.

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. Expanda os botões Lunarcom clicando na seta ao lado dele em sua hierarquia e usando o mesmo processo acima, arraste o MIC, o satélite e o Rocket Gameobjects para o elemento 0, 1 e 2 referências, respectivamente, no componente LunarcomController no Painel de Inspetor.

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. Selecione o objeto Lunarcom_Base "em sua hierarquia. Clique em Adicionar componente no painel Inspetor e procure e selecione reconhecedor de fala Lunarcom. Repita as mesmas etapas para adicionar o Lunarcom Wake Word Recognizer.

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. No slot de palavra de ativação, digite ativar terminal. No slot de palavras ignorar, digite fechar terminal.

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a>Crie o aplicativo para seu dispositivo

1. Abra a janela configurações de compilação novamente indo para arquivo > configurações de Build.

    ![images/mrlearning-Speech-CH1-2-etapa 1](images/mrlearning-speach-ch1-2-step1.jpg)

2. Verifique se a cena que você deseja experimentar está na lista de "Cenas em Compilação", clicando no botão "Adicionar Cenas Abertas".

3. Pressione o botão Configurações do Player e vá para publicando configurações. Em recursos, habilite: Internet, servidor de cliente de Internet, servidor cliente de rede privada, microfone e percepção espacial.

4. Nas mesmas configurações do Player, vá para configurações de XR e selecione a realidade virtual com suporte para ativado.

5. Pressione o botão Compilar para iniciar o processo de compilação.

    ![mrlearning-Speech-CH1-2-Step5](images/mrlearning-speach-ch1-2-step5.jpg)

6. Crie e dê um nome para uma nova pasta para o seu aplicativo. Na imagem abaixo, uma pasta com o nome "Aplicativo" foi criada para armazenar o aplicativo. Clique em "Selecionar Pasta" para começar a compilar na pasta recém-criada. Após a compilação, você pode fechar a janela "Configurações de Compilação" no Unity.

    ![mrlearning-Speech-CH1-2-etapa 6](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    >se a compilação falhar, tente compilar novamente ou reiniciar o Unity e compilar novamente. Se você vir um erro como "erro: CS0246 = o tipo ou nome do namespace" XX "não pôde ser encontrado (está faltando uma diretiva using ou uma referência de assembly?)", talvez seja necessário instalar o [SDK do Windows 10 (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)

7. Depois que a compilação for concluída, abra a pasta recém-criada que contém os arquivos do novo aplicativo. Clique duas vezes no arquivo de solução ". sln" para abrir o arquivo de solução no Visual Studio.

    >[!NOTE]
    >certifique-se de abrir a pasta recém-criada (ou seja, "Aplicativo", se estiver seguindo as convenções de nomenclatura das etapas anteriores), pois haverá um arquivo .sln com nome semelhante fora dessa pasta que não deve ser confundido com o arquivo .sln dentro da pasta de compilação. 

    ![mrlearning-Speech-CH1-2-Step7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    >se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para garantir que todos os componentes necessários sejam instalados conforme especificado na [página "Instalar as ferramentas"](install-the-tools.md).

8. Conecte o HoloLens 2 ao computador usando o cabo USB. Embora essas instruções pressuponham que você esteja implantando um teste com um dispositivo HoloLens 2, também é possível optar por implantar o [emulador do HoloLens 2](using-the-hololens-emulator.md) ou criar um [pacote do aplicativo para sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).

9. Antes de compilar para seu dispositivo, verifique se ele está no Modo de Desenvolvedor. Se for a primeira vez que você implanta o HoloLens 2, o Visual Studio pode solicitar o emparelhamento do seu HoloLens 2 com um pin. Siga [estas instruções](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) se você precisar ativar o modo de desenvolvedor ou emparelhar com o Visual Studio.

10. Configure o Visual Studio para compilar seu HoloLens 2, selecionando a configuração "Versão" e a arquitetura "ARM".

    ![mrlearning-Speech-CH1-2-step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. A etapa final é compilar para seu dispositivo, selecionando Depurar > Iniciar sem Depuração. Selecionar "Iniciar sem Depuração" fará com que o aplicativo inicie imediatamente em seu dispositivo após uma compilação bem-sucedida, mas sem exibir informações de Depuração no Visual Studio. Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo. Você também pode selecionar Compilação > Implantar Solução para implantar seu dispositivo sem iniciar o aplicativo automaticamente.

    ![mrlearning-Speech-CH1-2-step11. JPG](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a>Parabéns

Você configurou o reconhecimento de voz em seu aplicativo, da plataforma Azure. Execute o aplicativo para garantir que todas as funções e recursos estejam funcionando corretamente. Comece dizendo a palavra de ativação que você digitou na etapa 22, ativar terminal. Selecione o botão de microfone para iniciar o reconhecimento de voz. Comece a falar. Você verá suas palavras transcritas no terminal enquanto fala. Pressione o botão de microfone uma segunda vez para parar o reconhecimento de voz. Diga ignorar terminal para ocultar o terminal Lunarcom. Na próxima lição, aprenderemos como alternar dinamicamente para usar o reconhecimento de voz alimentada por dispositivo em situações em que o SDK de fala do Azure não está disponível devido ao HoloLens 2 estar offline.

[Próximo tutorial: 2. adicionando um modo offline para conversão de fala em texto local](mrlearning-speechSDK-ch2.md)
