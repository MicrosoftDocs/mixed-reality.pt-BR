---
title: Módulo Sr Learning SpeechSDK – reconhecimento de fala e transcrição
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: b434b9c79a702067a9c3db6fb25b0f75cdc6030d
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485784"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. Configurando a intenção e a compreensão do idioma natural

Nesta lição, exploraremos o recurso de intenção do serviço de fala do Azure. O recurso de intenção nos permite equipar nosso aplicativo com comandos de voz alimentados por ia, onde os usuários podem dizer comandos de voz não específicos e ainda ter sua intenção compreendida pelo sistema. Durante esta lição, vamos configurar nosso portal de LUIS do Azure, configurar nossa intenção/entidades/declarações, publicar nosso recurso de intenção, conectar nosso aplicativo do Unity ao nosso recurso de intenção e fazer nossa primeira chamada à API de nossa intenção.

## <a name="objectives"></a>Objetivos

- Saiba como configurar o reconhecimento de intenções e de idioma natural em nosso aplicativo
- Saiba como configurar o portal LUIS do Azure
- Saiba como configurar intenção, entidades e declarações no Azure

## <a name="instructions"></a>Instruções
1. Permitir que seu computador habilite o ditado, vá para configurações do Windows, selecione "privacidade", depois "fala" e, finalmente, "escrita à tinta & digitação" e ative os serviços de fala e as sugestões de digitação.

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. Faça logon no [portal do Azure](https://portal.azure.com/). Depois de fazer logon, clique em criar um recurso e pesquise por "Reconhecimento vocal" e clique em Enter.

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. Selecione o botão criar para criar uma instância desse serviço. Nomeie seu projeto como "Speech_SDK_Learning_Module" e selecione "pré-pago".

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. Selecione sua região.  Para fins deste tutorial, selecione "(EUA) oeste dos EUA". Em seguida, escolha "F0" para o tipo de preço. Agora, clique em "criar" (localizado no canto inferior esquerdo) para criar o recurso.

>  Observação: depois de clicar em "criar", você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

5. Uma notificação será exibida no portal assim que o recurso for criado. Clique nessa notificação e selecione "ir para o recurso".

6. Na página "Início Rápido" do serviço "API do LUIS", navegue até a primeira etapa, pegue suas "chaves" e clique em "chaves" (você também pode conseguir isso clicando no hiperlink azul "chaves", mostrado na imagem abaixo). Isso revelará seu serviço, "chaves". Salve uma cópia de uma das chaves para que você possa usá-la posteriormente no aplicativo.

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. De volta à página "Início Rápido" na seção 2B, clique em "portal de Reconhecimento vocal" (mostrado na imagem acima) para ser redirecionado para a página da Web que você usará para criar seu novo serviço, dentro do aplicativo LUIS.

> Observação: Ao atingir o "portal de Reconhecimento vocal", talvez seja necessário fazer logon, se você ainda não tiver, com as mesmas credenciais do portal do Azure. Se esta for a primeira vez que você usa o LUIS, você precisará rolar para baixo até a parte inferior da página de boas-vindas, para localizar e clicar no botão "criar LUIS" do aplicativo.

8. Depois de conectado, clique em meus aplicativos (se você não estiver na seção no momento). Em seguida, você pode clicar em criar novo aplicativo. Nomeie o novo aplicativo "módulo de aprendizagem SDK de fala". Adicione "módulo de aprendizagem do SDK de fala" ao campo de descrição também. Em seguida, clique em "concluído".

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> anotações Se seu aplicativo deve entender uma linguagem diferente do inglês, você deve alterar a "cultura" para o idioma apropriado.

9. Clique em "Compilar" localizado no canto superior direito.

10. Em ativos do aplicativo à esquerda, selecione "intenções" e, em seguida, clique em "criar nova tentativa" e nomeie-o como "PressButton". 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> Observação: É importante usar os nomes de intenções e entidades usadas neste tutorial porque o aplicativo Lunarcom fará referência a eles por nome. 
>
> Observação: agora você deve ter duas intenções – "PressButton" e "None".

11. Em ativos do aplicativo à esquerda, selecione "entidades" e clique em "criar nova entidade" e nomeie-a como "ação" e mantenha o tipo de entidade como "simples".

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. Clique em "criar nova entidade" novamente e nomeie-a como "destino" e mantenha o tipo de entidade como "simples" também.

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. Em ativos do aplicativo à esquerda, selecione "intenções" e clique na intenção de "PressButton" que você criou na etapa 10.

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. Clique na lista suspensa "opções de exibição" à direita e selecione "mostrar valores de entidade". 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)Clique no botão "inserir um exemplo..." texto. Em seguida, insira o seguinte declarações: 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. Clique na lista suspensa "opções de exibição" à direita e selecione "mostrar nomes de entidade".

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. Verifique se cada um dos 10 declarações tem os seguintes rótulos de entidade nos seguintes lugares em 1.) clicando em palavras que são rotuladas e, no pop-up, selecionando "remover rótulo" e 2.) clicando em palavras que devem ser rotuladas e, no pop-up, selecionando o rótulo apropriado.

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. Agora, para publicar o modelo, clique em "treinar" no canto superior direito. Em seguida, depois de concluir o processamento, clique em "testar" no canto superior direito.

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. Insira "Selecione o botão Iniciar" na caixa de texto.

> Observação: não adicionamos "Select" como uma ação em qualquer um de nossos declarações-mas se você clicar em "inspecionar", o modelo reconheceu "Select" como uma entidade de ação.
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. Agora, clique em "publicar" no canto superior direito. Verifique se o menu suspenso diz "produção" e clique em "publicar" também no pop-up. 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. Depois de publicado, uma barra verde deve aparecer na parte superior da página.  Clique na barra verde a ser levada para a página "gerenciar". 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. Clique em "chaves e pontos de extremidade" em "configurações do aplicativo" à esquerda. Em seguida, defina a lista suspensa "publicar em" como "produção". Defina o fuso horário para corresponder ao seu e marque a caixa para incluir todas as pontuações de intenção prevista. Por fim, clique em "atribuir recurso".

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. Selecione locatário na primeira lista suspensa e selecione "pré-pago" na lista suspensa nome da assinatura. Em nome do recurso LUIS, escolha o recurso que criamos acima nas etapas 1-5. Em seguida, clique em "atribuir recurso". 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> Observação: Certifique-se de copiar e salvar a URL do ponto de extremidade associada ao recurso que acabamos de atribuir para que ele seja facilmente acessível para a próxima seção.
>
> Observação: Para o nome do locatário, coloque sua corporação ou perfil que você criou para este aplicativo.

23. Agora, abra o novo aplicativo no Unity e selecione o objeto Lunarcom_Base na hierarquia. Clique em "Adicionar componente" no painel Inspetor e procure e selecione "LunarcomIntentRecognizer".

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. No campo ponto de extremidade Luis do "LunarcomIntentRecognizer" no painel Inspetor, insira a URL do ponto de extremidade que você salvou na etapa 22. 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  Observação: No componente "LunarcomOfflineRecognizer" no painel Inspetor, certifique-se de que "Desabilitar" esteja selecionado para "SimulateOfflineMode" caso contrário, o teste do programa não funcionará. 

25. Pressione o botão reproduzir no editor do Unity e clique no botão Rocket para iniciar o reconhecimento de intenção. Com a frase "Selecione o botão iniciar Rocket".

>  Observação: O aplicativo reconheceu a função desejada e ativou o botão Rocket.
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>Parabéns

Nesta lição, aprendemos como adicionar comandos de fala baseados em ia! Agora, seu programa pode reconhecer a intenção dos usuários mesmo que eles não excedam comandos de voz precisos.

