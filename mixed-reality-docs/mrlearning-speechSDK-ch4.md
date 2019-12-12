---
title: TUTORIAIS dos serviços de fala do Azure-4. Configurando a intenção e a compreensão do idioma natural
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: e712fc2fd66b1add5b16b7dd8e6c37551aefe43a
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003205"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. Configurando o reconhecimento de intenções e idiomas naturais

Nesta lição, você vai explorar o recurso de intenção do serviço de fala do Azure. O recurso de intenção permite que você equipate nosso aplicativo com comandos de voz alimentados por ia, onde os usuários podem dizer comandos de voz não específicos e ainda têm sua intenção compreendida pelo sistema. Durante esta lição, vamos configurar nosso portal de LUIS do Azure, configurar nossa intenção/entidades/declarações, publicar nosso recurso de intenção, conectar nosso aplicativo do Unity ao nosso recurso de intenção e fazer nossa primeira chamada à API de nossa intenção.

## <a name="objectives"></a>Objetivos

- Saiba como configurar o reconhecimento de intenções e de idioma natural em nosso aplicativo
- Saiba como configurar o portal LUIS do Azure
- Saiba como configurar intenção, entidades e declarações no Azure

## <a name="instructions"></a>Instruções

1. Permitir que seu computador habilite o ditado. Para fazer isso, vá para configurações do Windows, selecione "privacidade", em seguida, "fala", seguido por "escrita à tinta & digitação" e ative os serviços de fala e as sugestões de digitação.

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. Faça logon no [portal do Azure](https://portal.azure.com/). Depois de fazer logon, clique em criar um recurso, pesquise por "Reconhecimento vocal" e clique em Enter.

    ![mrlearning-Speech-CH4-1-Step2. png](images/mrlearning-speech-ch4-1-step2.png)

3. Clique no botão **criar** para criar uma instância desse serviço.

    ![mrlearning-Speech-CH4-1-step3a. png](images/mrlearning-speech-ch4-1-step3a.png)

    Dê um **nome**a seu recurso, por exemplo, *fala-SDK-Learning-Module*. Para **assinatura**, selecione *pagamento conforme o uso* ou *trilha gratuita* se você tiver uma conta de avaliação. Em seguida, crie um novo **grupo de recursos** clicando no link **criar novo** , insira um nome, por exemplo, *HoloLens-2-tutoriais-Resource-Group*e clique no botão **OK** .

    ![mrlearning-Speech-CH4-1-step3b. png](images/mrlearning-speech-ch4-1-step3b.png)

4. Selecione o **local de criação** e o **local do tempo de execução**. Para fins deste tutorial, use *(EUA) oeste dos EUA*e, em seguida, escolha *F0 (5 chamadas por segundo, 10K chamadas por mês)* para o **tipo de preço de criação** e tipo de preço de tempo de **execução**. Por fim, clique no botão **criar** para criar o recurso, bem como o novo grupo de recursos.

    ![mrlearning-Speech-CH4-1-step4. png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    >Depois de clicar no botão criar, você precisará aguardar até que o serviço seja criado, o que pode levar alguns minutos.

5. Depois que o processo de criação de recursos for concluído, você verá a mensagem **sua implantação está concluída**.

    ![mrlearning-Speech-CH4-1-Step5. png](images/mrlearning-speech-ch4-1-step5.png)

6. Usando a mesma conta de usuário, entre no portal do [Luis (serviço inteligente reconhecimento vocal)](https://www.luis.ai/) , selecione seu país e concorde com os termos de uso.

    >[!NOTE]
    >Ao acessar o portal de Reconhecimento vocal, talvez seja necessário fazer logon, se você ainda não tiver, com as mesmas credenciais que o portal do Azure. Se esta for a primeira vez que você usa o LUIS, você precisará rolar para baixo até a parte inferior da página de boas-vindas para localizar e clicar no botão "criar LUIS" do aplicativo.

7. Depois de conectado, clique em meus aplicativos (se você ainda não estiver nesta seção). Em seguida, você pode clicar em criar novo aplicativo. Nomeie o novo aplicativo "módulo de aprendizagem SDK de fala". Adicione "módulo de aprendizagem do SDK de fala" ao campo de descrição também. Em seguida, clique em "concluído".

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    >Se seu aplicativo deve entender uma linguagem diferente do inglês, você deve alterar a "cultura" para o idioma apropriado.

8. Clique em "Compilar" localizado no canto superior direito.

9. Em ativos do aplicativo à esquerda, selecione "intenções" e, em seguida, clique em "criar nova tentativa" e nomeie-o como "PressButton".

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    >É importante usar os nomes de intenções e entidades usadas neste tutorial porque o aplicativo Lunarcom fará referência a eles por nome.

    >[!NOTE]
    >Agora você deve ter duas intenções – "PressButton" e "None".

10. Em ativos do aplicativo à esquerda, selecione "entidades", clique em "criar nova entidade", nomeie-a como "ação" e mantenha o tipo de entidade como "simples".

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. Clique em "criar nova entidade" novamente e nomeie-a como "destino". Mantenha o tipo de entidade como "simples" também.

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. Em ativos do aplicativo à esquerda, selecione "intenções" e clique na intenção de "PressButton" que você criou na etapa 10.

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. Clique na lista suspensa "opções de exibição" à direita e selecione "mostrar valores de entidade".

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    Clique no botão "inserir um exemplo..." . Em seguida, insira o seguinte declarações:

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. Clique na lista suspensa "opções de exibição" à direita e selecione "mostrar nomes de entidade".

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. Verifique se cada um dos 10 declarações tem os seguintes rótulos de entidade nos seguintes lugares em 1.) clicando em palavras que são rotuladas e, no pop-up, selecionando "remover rótulo" e 2.) clicando em palavras que devem ser rotuladas e, no pop-up, selecionando o rótulo apropriado.

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. Agora, para publicar o modelo, clique em "treinar" no canto superior direito. Em seguida, depois de concluir o processamento, clique em "testar" no canto superior direito.

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. Insira "Selecione o botão Iniciar" na caixa de texto.

    >[!NOTE]
    >Não adicionamos "Select" como uma ação em qualquer um de nossos declarações, mas se você clicar em "inspecionar", o modelo reconheceu "Select" como uma entidade de ação.
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. Clique em "publicar" no canto superior direito. Verifique se o menu suspenso diz "produção" e clique em "publicar" também no pop-up.

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. Depois de publicado, uma barra verde deve aparecer na parte superior da página. Clique na barra verde para exibir a página "gerenciar".

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. Clique em "chaves e pontos de extremidade" em "configurações do aplicativo" à esquerda. Em seguida, defina a lista suspensa "publicar em" como "produção". Defina o fuso horário para corresponder ao seu e marque a caixa para incluir todas as pontuações de intenção prevista. Por fim, clique em "atribuir recurso".

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. Selecione locatário na primeira lista suspensa e selecione "pré-pago" na lista suspensa nome da assinatura. Em nome do recurso LUIS, escolha o recurso que criamos acima nas etapas 1-5. Em seguida, clique em "atribuir recurso".

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    >Certifique-se de copiar e salvar a URL do ponto de extremidade associada ao recurso que acabamos de atribuir, para que seja facilmente acessível para a próxima seção.

    >[!NOTE]
    >Para o nome do locatário, coloque sua corporação ou perfil que você criou para este aplicativo.

22. Agora, abra o novo aplicativo no Unity e selecione o objeto Lunarcom_Base na hierarquia. Clique em "Adicionar componente" no painel Inspetor e procure e selecione "LunarcomIntentRecognizer".

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. No campo ponto de extremidade Luis do "LunarcomIntentRecognizer" no painel Inspetor, insira a URL do ponto de extremidade que você salvou na etapa 22.

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    >No componente "LunarcomOfflineRecognizer" no painel Inspetor, certifique-se de que "Desabilitar" esteja selecionado para "SimulateOfflineMode" caso contrário, o teste do programa não funcionará.

24. Pressione o botão reproduzir no editor do Unity e clique no botão Rocket para iniciar o reconhecimento de intenção. Com a frase "Selecione o botão iniciar Rocket".

    >[!NOTE]
    >O aplicativo reconheceu a função desejada e ativou o botão Rocket.
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>Parabéns

Nesta lição, você aprendeu a adicionar comandos de fala baseados em ia. Agora seu programa pode reconhecer a intenção dos usuários, mesmo que eles não excedam comandos de voz precisos!
