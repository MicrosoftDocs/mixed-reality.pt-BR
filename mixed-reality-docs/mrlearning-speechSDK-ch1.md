---
title: Módulo Sr Learning SpeechSDK – reconhecimento de fala e transcrição
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: c1ca44ffcaa8dced988b829d9875ebe304f14a12
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460351"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. Integrando e usando o reconhecimento de fala e a transcrição

Este tutorial cria um aplicativo de realidade misturada que explora o uso do SDK de fala dos serviços cognitivas do Azure com o HoloLens 2. Quando terminar com esta série de tutoriais, você poderá usar o microfone do dispositivo para transcrever a fala para o texto em tempo real, traduzir sua fala em outras linguagens e aproveitar o recurso de intenção do SDK de fala para entender os comandos de voz usando inteligência artificial.

## <a name="objectives"></a>Objetivos

- Saiba como integrar o SDK de fala do Azure em um aplicativo do HoloLens 2
- Saiba como usar comandos de voz
- Saiba como usar os recursos de fala para texto

## <a name="instructions"></a>Instruções

### <a name="getting-started"></a>Guia de Introdução

1. Inicie o Unity e crie um novo projeto. Insira o nome do projeto módulo de aprendizagem do SDK de fala. Escolha um local para onde salvar o projeto. Em seguida, clique em criar projeto.

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> Observação: Verifique se o modelo está definido como 3D, conforme mostrado na imagem acima.

2. Baixe o pacote de Unity do [Kit de ferramentas da realidade mista](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) e salve-o em uma pasta no seu computador. Importe o pacote para o projeto do Unity. Para obter instruções detalhadas sobre como fazer isso, consulte a [lição 1 do módulo base](mrlearning-base-ch1.md). 

3. Baixe e importe o [SDK de fala](https://aka.ms/csspeech/unitypackage) do Azure para o pacote de ativos do Unity. Importe o pacote do SDK de fala clicando em ativos, selecionando importar pacote e, em seguida, selecionando pacote personalizado. Localize o pacote do SDK de fala baixado anteriormente e abra-o para iniciar o processo de importação. 

![Module4Chapter1step3ima](images/module4chapter1step3ima.PNG)

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. Na próxima janela pop-up, clique em importar para começar a importar o pacote do SDK de fala. Verifique se todos os itens estão marcados conforme mostrado na imagem abaixo.

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)

5. Baixe o pacote de ativos do módulo SDK de fala, também conhecido como pacote Lunarcom clicando nesse [link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2). O pacote de ativos do Lunarcom é uma coleção de ativos e scripts desenvolvidos para esta série de lições para demonstrar um uso prático do SDK de fala do Azure. É um terminal de comando de voz que, por fim, fará a interface com a experiência de montagem do módulo lunar desenvolvida no [tutorial do módulo base.](mrlearning-base-ch6.md)

6. Importe o pacote de ativos do Lunarcom para seu projeto do Unity seguindo as etapas semelhantes que você levou para importar o kit de ferramentas e o SDK de fala misturados da realidade.
7. Configure o MRTK (Kit de ferramentas de realidade mista). Para fazer isso, clique no painel do kit de ferramentas da realidade misturada na parte superior da janela e, em seguida, selecione Adicionar à cena e configurar.

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

![module4Chapter1step9ima](images/module4chapter1step9ima.PNG)

![module4Chapter1step9imb](images/module4chapter1step9imb.PNG)

8. Sua cena agora tem vários novos itens da MRTK. Salve sua cena com um nome diferente clicando em "arquivo" e, em seguida, em "salvar como" e nomeie sua cena como SpeechScene. 

> Observação: Se você pressionar reproduzir em sua cena depois de adicionar o MRTK ao seu projeto e ele não entrar no modo de reprodução, talvez seja necessário reiniciar o Unity. 

9. Com o objeto MixedRealityToolkit selecionado em sua hierarquia, clique em copiar e personalizar no painel inspetor.

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. Também no painel Inspetor (com o objeto MixedRealityToolkit selecionado em sua hierarquia), desabilite o sistema de diagnóstico desmarcando a caixa à direita de habilitar o sistema de diagnóstico.

![Module4Chapter1step9imd](images/module4chapter1step9imd.PNG)

11. Para habilitar os comandos de voz, selecione o perfil MRTK recém-criado a ser personalizado. Neste tutorial, estamos usando os comandos de fala de entrada para reconhecimento e transcrição de fala. Vamos clonar o perfil de entrada para fazer alterações nas configurações de fala.

![Module4Chapter1step11imb](images/module4chapter1step11imb.PNG)

![Module4Chapter1step11imd](images/module4chapter1step11imd.PNG)

12. Depois que o perfil de entrada for clonado, vá para comandos de fala e clone os comandos de fala.

![Module4Chapter1step12imb](images/module4chapter1step12imb.PNG)

![Module4Chapter1step12imc](images/module4chapter1step12imc.PNG)

13. Agora, em comandos de fala, vá para "configurações gerais" e defina "Iniciar comportamento" como "início manual"

![Module4Chapter1step13imb](images/module4chapter1step13imb.PNG)

14. No painel projeto, expanda a pasta Lunarcom e arraste Lunarcom_Base pré-fabricado para sua hierarquia.

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

15. Selecione o objeto Lunarcom_Base em sua hierarquia e verifique se a posição está definida como x = 0, y = 0 e z = 0, bem como a rotação definida como x = 0, y = 0 e z = 0. Defina a escala como leitura x = 0.008, y = 0.008 e z = 0,01.

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. Clique em Adicionar componente e procure e selecione LunarcomController. Esse script está incluído no pacote de ativos do Lunarcom que você importou na etapa 6.

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. Para conectar nosso aplicativo aos serviços cognitivas do Azure, você deve inserir uma chave de assinatura (também conhecida como chave de API) para o serviço de fala. Siga as instruções [aqui](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) para obter uma chave de assinatura gratuita. Depois de obter a chave de assinatura, insira-a no campo chave de API do serviço de fala do componente LunarcomController no painel Inspetor, conforme mostrado na imagem abaixo.

18. Insira a região que você escolheu ao se inscrever na chave de assinatura no campo região do serviço de fala do componente LunarcomController no painel inspetor. Por exemplo, para o tipo de região "oeste dos EUA" em "westus"

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. Em sua hierarquia, expanda o objeto Lunarcom_Base clicando na seta à esquerda dele. Em seguida, faça o mesmo para seu objeto filho "terminal", conforme mostrado na imagem abaixo.

20. Enquanto Lunarcom_Base estiver selecionado, clique e arraste Lunarcom texto da hierarquia para o slot de texto de saída no componente LunarcomController no painel Inspetor, conforme mostrado na imagem abaixo.

21. Faça a mesma coisa com o objeto de terminal no slot de terminal e no objeto de luz de conexão para o slot do controlador de luz de conexão.

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. Clique na seta ao lado da seção de botões Lunarcom do script LunarcomController no painel Inspetor e altere o tamanho para 3. Pressione Enter ou Return. Isso faz com que três novos campos de elemento sejam exibidos.

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. Expanda os botões Lunarcom clicando na seta ao lado dele em sua hierarquia e usando o mesmo processo acima, arraste o MIC, o satélite e o Rocket Gameobjects para o elemento 0, 1 e 2 referências, respectivamente, no componente LunarcomController no Painel de Inspetor. 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. Selecione o objeto Lunarcom_Base "em sua hierarquia. Clique em Adicionar componente no painel Inspetor e procure e selecione LunarcomWakeWordRecognizer.

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. No slot de palavra de ativação, digite ativar terminal. No slot de palavras ignorar, digite fechar terminal.

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a>Crie o aplicativo para seu dispositivo

1. Abra a janela configurações de compilação novamente indo para arquivo > configurações de Build.

![Lição 1 Chapter5 etapa 1](images/Lesson1Chapter5Step1.JPG)

2. Verifique se a cena que você deseja experimentar está na lista de "Cenas em Compilação", clicando no botão "Adicionar Cenas Abertas".

3. Pressione o botão Compilar para iniciar o processo de compilação.

![Lição 1 Chapter5 etapa 3](images/Lesson1Chapter5Step3.JPG)

4. Crie e dê um nome para uma nova pasta para o seu aplicativo. Na imagem abaixo, uma pasta com o nome "Aplicativo" foi criada para armazenar o aplicativo. Clique em "Selecionar Pasta" para começar a compilar na pasta recém-criada. Após a compilação, você pode fechar a janela "Configurações de Compilação" no Unity. 

![Lição 1 Chapter5 etapa 4](images/Lesson1Chapter5Step4.JPG)

> OBSERVAÇÃO: se a compilação falhar, tente compilar novamente ou reiniciar o Unity e compilar novamente. Se você vir um erro, como "Erro: CS0246 = O nome do tipo ou do namespace ‘XX’ não pôde ser encontrado (não pode ser encontrado (está faltando uma diretiva using ou uma referência de assembly?) ", talvez precise instalar o [SDK do Windows 10 (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>).

5. Depois que a compilação for concluída, abra a pasta recém-criada que contém os arquivos do novo aplicativo. Clique duas vezes no arquivo de solução ". sln" para abrir o arquivo de solução no Visual Studio.

> Observação: certifique-se de abrir a pasta recém-criada (ou seja, "Aplicativo", se estiver seguindo as convenções de nomenclatura das etapas anteriores), pois haverá um arquivo .sln com nome semelhante fora dessa pasta que não deve ser confundido com o arquivo .sln dentro da pasta de compilação. 

![Lição1 Capítulo5 Etapa5](images/Lesson1Chapter5Step5.JPG)

> Observação: se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para garantir que todos os componentes necessários sejam instalados conforme especificado na [página "Instalar as ferramentas"](install-the-tools.md).

6. Conecte o HoloLens 2 ao computador usando o cabo USB. Embora essas instruções pressuponham que você esteja implantando um teste com um dispositivo HoloLens 2, também é possível optar por implantar o [emulador do HoloLens 2](using-the-hololens-emulator.md) ou criar um [pacote do aplicativo para sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>).

7. Antes de compilar para seu dispositivo, verifique se ele está no Modo de Desenvolvedor. Se for a primeira vez que você implanta o HoloLens 2, o Visual Studio pode solicitar o emparelhamento do seu HoloLens 2 com um pin. Siga [estas instruções](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se você precisar ativar o modo de desenvolvedor ou emparelhar com o Visual Studio.

8. Configure o Visual Studio para compilar seu HoloLens 2, selecionando a configuração "Versão" e a arquitetura "ARM".

![Lição 1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. A etapa final é compilar para seu dispositivo, selecionando Depurar > Iniciar sem Depuração. Selecionar "Iniciar sem Depuração" fará com que o aplicativo inicie imediatamente em seu dispositivo após uma compilação bem-sucedida, mas sem exibir informações de Depuração no Visual Studio. Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo. Você também pode selecionar Compilação > Implantar Solução para implantar seu dispositivo sem iniciar o aplicativo automaticamente.

![Lição 1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Parabéns

Você configurou o reconhecimento de voz em seu aplicativo, da plataforma Azure. Execute o aplicativo para garantir que todas as funções e recursos estejam funcionando corretamente. Comece dizendo a palavra de ativação que você digitou na etapa 22, ativar terminal. Selecione o botão de microfone para iniciar o reconhecimento de voz. Comece a falar. Você verá suas palavras transcritas no terminal enquanto fala. Pressione o botão de microfone uma segunda vez para parar o reconhecimento de voz. Diga ignorar terminal para ocultar o terminal Lunarcom. Na próxima lição, aprenderemos como alternar dinamicamente para usar o reconhecimento de voz alimentada por dispositivo em situações em que o SDK de fala do Azure não está disponível devido ao HoloLens 2 estar offline.

[Próximo tutorial: 2. Adicionar um modo offline para tradução de fala em texto local](mrlearning-speechSDK-ch2.md)

