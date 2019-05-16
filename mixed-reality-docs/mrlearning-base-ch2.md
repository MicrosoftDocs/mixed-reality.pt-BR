---
title: MR Learning Base mão de módulo - Interface do usuário, rastreamento e misto de configuração do Kit de ferramentas de realidade
description: Conclua este curso para aprender a implementar o reconhecimento de Face do Azure dentro de um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realidade misturada, hololens de tutoriais, unity,
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730946"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>MR Learning Base mão de módulo - Interface do usuário, rastreamento e misto de configuração do Kit de ferramentas de realidade

Na lição anterior, você aprendeu alguns dos recursos que de MRTK tem a oferecer, iniciando seu primeiro aplicativo para o HoloLens 2. Nesta próxima lição, você aprenderá como criar e organizar os botões, juntamente com os painéis de texto de interface do usuário e usar a interação padrão (toque) para interagir com cada botão. Você também vai explorar a adição de ações simples e efeitos, como alterar o tamanho, som e a cor de objetos. Este módulo apresenta os conceitos básicos sobre como modificar perfis MRTK, começando com a desativar a visualização da malha espacial. 

## <a name="objectives"></a>Objetivos

* Personalizar e configurar perfis de kit de ferramentas de realidade mista
* Interagindo com hologramas usando os botões e elementos de interface do usuário
* As interações e entrada de controle de mão básico

## <a name="instructions"></a>Instruções

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Como configurar os perfis do Kit de ferramentas de realidade misturada (opção de exibição de percepção espacial de alteração)
Nesta seção, que você aprenderá a personalizar e configurar os perfis de kit de ferramentas de realidade misturada padrão ajustando-se a opção de exibição de reconhecimento de espacial da malha. Você pode seguir esses mesmos princípios para ajuste quaisquer configurações ou os valores nos perfis MRTK.

1. Selecione o Kit de ferramentas de realidade mista (MRTK) da hierarquia de "BaseScene". No painel Inspetor, procure o "misto realidade Kit de ferramentas de Script" e selecione "perfil ativo", conforme mostrado na figura abaixo. Clique duas vezes para abri-lo.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>Observação: Por padrão, os perfis MRTK não são editáveis. Esses são os modelos de perfil padrão do qual você pode copiar e personalizar. Existem vários níveis de personalização e perfis, portanto, é uma prática padrão para copiar e personalizar vários perfis ao configurar uma ou mais configurações.
>
>Para descobrir mais sobre perfis MRTK e sua arquitetura, visite o [documentação MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).

2. Crie uma cópia do perfil padrão para personalizá-lo. Para copiar um perfil padrão, clique em de "cópia e personalizar" botão (consulte a imagem). Isso cria uma cópia do perfil MRTK. Com sua própria cópia do perfil MRTK, agora você tem a capacidade de personalizar as configurações neste perfil. Você também precisará repetir a etapa de cópia/personalizar para qualquer perfis adicionais aninhados sob esse perfil, conforme descrito nas etapas subsequentes.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. Desabilite a visibilidade da malha percepção espacial. Para fazer isso, localize "Configurações de sistema de reconhecimento espacial" conforme mostrado na imagem. Clique no botão "clonar" à direita do o "espacial reconhecimento de perfil do sistema" para substituir o perfil padrão com uma cópia personalizável. Se uma janela pop-up aparecer, pressione o botão "Reproduzir", conforme mostrado na segunda imagem abaixo.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Crie uma cópia personalizada do padrão misto realidade espacial de malha Observer. Clique na seta para baixo ao lado do Windows misto realidade espacial de malha "observador" para ver outras opções. Essas opções, você verá o padrão misto realidade espacial de malha "observador" que aparece esmaecida (não editável). Você deve substituir esse perfil padrão com uma cópia personalizável para que você pode editá-lo. Clique no botão à direita (marcado por seta verde) para clonar uma cópia.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. Em seguida, você irá ajustar as configurações para a opção de exibição dizer "oclusão." Isso torna a malha espacial invisível, mas ainda ocultar objetos do jogo por trás da malha espacial (Isso é conhecido como oclusão.)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>Observação: Enquanto a malha de mapeamento espacial não estiver visível, ele ainda está presente e você pode interagir com ele. Qualquer hologramas por trás da malha de mapeamento espacial (por exemplo, um holograma por trás de sua parede visível) não será visíveis por causa da configuração de oclusão.

Parabéns! Você acabou de aprender como modificar uma configuração do perfil MRTK. Como você pode ver, para modificar as configurações de MRTK você precisa criar cópias dos perfis padrão para que você pode editá-los. Você sempre tenha os perfis padrão (que não são editáveis) para retornar ao se você quisesse criar um perfil com as novas configurações, ou consulte os perfis padrão. Há várias configurações que você pode ajustar. Para obter uma referência completa para as configurações de perfil MRTK, consulte a documentação de MRTK aqui: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Botões Interagível e gestos de mão de acompanhamento
Nesta seção, você aprenderá como usar a mão de acompanhamento para pressionar um botão interagível.

1. Selecione "Ativos" na pasta projetos.

2. Digite na barra de pesquisa, "pressablebutton".

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. Arraste pré-fabricado (representado por uma caixa azul) denominado "PressableButton" em sua hierarquia. 

   > Observação: Se você receber uma mensagem "importando TMP Essentials" por favor, importá-lo neste momento. Se TMP Essentials já não fazia parte do seu projeto, você precisa repetir essa etapa depois de importar o Essentials TMP, caso contrário, o texto do botão não pode aparecer.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. Clique duas vezes o objeto do jogo "PressableButton" (que agora deve estar em sua hierarquia BaseScene) para exibi-lo na sua cena, conforme mostrado na imagem abaixo (seus gráficos de botão podem aparecer diferentes da imagem abaixo). 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. No painel Inspetor, clique em "Adicionar evento" para dar ao botão um evento para responder a quando enviada por push. Na opção que aparece, selecione o menu suspenso. Selecione "InteractableOnPressReciever". Isso permite que o botão para responder a um evento pressionado quando uma mão controlada pressiona o botão.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. Adicione um cubo para a cena. Clique com o botão direito na área de hierarquia, selecione o objeto 3D e clique em "cubo". Agora, um cubo deve estar na exibição. Ele será parecem muito grande, então, ajuste as coordenadas (enquanto "cubo" ainda está selecionado na área de hierarquia) para diminuir o tamanho. Defina os valores de escala para x = 0,1, y = 0,1 e z = 0,1. Se-se de posicionar o cubo na sua cena para colocá-lo próximo botão pressable, mas não sobrepostas com o botão. Na imagem abaixo, a posição do cubo é x = 0, y = 0.2 e z = 1. 

   > Observação: Em geral, 1 unidade no Unity é aproximadamente equivalente a 1 metro no mundo físico. Há exceções, por exemplo, quando objetos são filhos dos objetos dimensionados.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. Nesta etapa você configurará o cubo para alterar a cor quando o botão é pressionado. Selecione o PressableButton no menu "BaseScene". No painel Inspetor, na caixa "Selecione o tipo de evento", clique no botão "+". Arraste o "cubo" no menu "BaseScene" na caixa "Tempo de execução apenas", conforme mostrado na imagem abaixo

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

Clique na lista suspensa que não diz "Nenhuma função". Selecione "MeshRenderer" e selecione "material Material". Isso permitirá que você altere o material quando o botão é pressionado. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

Vá para o painel projeto e procure o material que você deseja alterá-la para. Você pretende usar o material "MRTK_Standard_Cyan" para esse exemplo, encontrado digitando "ciano" na barra de pesquisa da guia de projeto (o MRTK inclui muitos materiais e cores para escolher.) Arraste o material para a caixa sob "MeshRenderer.material". Os materiais MRTK podem ser encontrados nos ativos > MixedRealityToolkit.SDK > StandardAssets > materiais.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

O evento agora é definido para que quando o botão é pressionado, o cubo mudará de cor com base no material que você especificou. Neste exemplo, o cubo será alterado para a cor ciano.

8. Em seguida, você pretende configurar a ação de liberação, de modo que após o lançamento, o botão Voltar para sua cor padrão. Repita a etapa 7 (na etapa anterior), mas desta vez com o evento de "OnRelease" em vez do evento "OnPress", conforme mostrado na imagem abaixo.

9.  No painel de projeto, procure um material para o cubo para o padrão após o botão Lançar (no nosso caso, escolhemos MRTK_Standard_LightGray.) Arraste o material na caixa abaixo do campo "MeshRenderer.material".

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

Agora, quando o botão é pressionado, ele deve alterar para uma nova cor (por exemplo, ciano) e quando o botão é liberado deve mudar para a cor padrão especificado (por exemplo, cinza claro.) Pressione o botão "reproduzir" na parte superior da tela para experimentá-lo no editor ou implantar em sua 2 HoloLens para testar! Para saber mais sobre a simulação no editor, inclusive simulação da mão leia as [página de documentação de simulação do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>). 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Criando um painel de botões usando a coleção de objetos de grade do MRTK

Nesta seção, você aprenderá como alinhar automaticamente vários botões em uma interface de usuário legal usando a ferramenta de GridObjectCollection do MRTK.

1. Duplicar o botão da seção anterior até que você tenha 5 botões. Há várias maneiras de fazer isso:
- Clique no botão direito e clique em "Copiar", em seguida, vá para baixo para abaixo do botão e clique com botão direito novamente e clique em "colar". 
- Clique no botão direito e clique em "duplicado". 
- Use o comando de teclado clicando no cubo e pressionando "ctrl D" em seu teclado.

Repita essa etapa até que você tiver 5 botões total (consulte as setas vermelhas 5 na imagem abaixo).

![Base de Mrlearning Cap2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Agrupe os botões em um objeto do jogo vazio pai. Para ter os botões na coleção de grade, você precisa agrupar seus botões em um objeto pai comum. Clique com o botão direito no hiearachy e clique em "criar vazio". Isso cria um novo objeto jogo vazio para você colocar todos os botões. Ele será exibido como "gameObject." Clique com botão direito e renomeie-o para "ButtonCollection".

![Base de Mrlearning Cap2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Mova todos os botões para a nova coleção. Faça isso selecionando todos os cinco dos objetos de botão no seu heirarch e arrastá-los tudo sob o objeto do jogo "ButtonCollection", conforme mostrado na imagem abaixo. Dica: selecione vários itens mantendo a tecla ctrl enquanto seleciona os itens.

![Base de Mrlearning Cap2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Adicione o componente de "Coleção de objetos de grade" do MRTK para a coleção de botões.  Para fazer isso, selecione o objeto pai "ButtonCollection" e no painel Inspetor, clique no botão "Adicionar componente". Em seguida, procure "Coleção de objetos de grade" na barra de pesquisa e selecione-o quando ele aparece na lista.

![Base de Mrlearning Cap2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

O componente de coleção de objetos de grade permite organizar botões ou qualquer conjunto de objetos em uma clara linha, coluna ou grade. Esse é um dos blocos de construção fornecidos pelo MRTK que fornece uma maneira rápida e simple para criar belas interfaces de usuário.

5. Configure a coleção de objetos de grade. Para garantir que todos os a face de botões do usuário, selecione "orientar o tipo" e, em seguida, selecione "face para encaminhar pai" (conforme mostrado na imagem.) Em seguida, altere o tamanho da célula para definir o espaço entre os botões. Começar com unidades 0,12 por 0,12 unidades para a largura da célula e a altura da célula, conforme mostrado na imagem abaixo. Talvez você precise ajustar esses valores, dependendo do escolhido de ativos de objeto e do botão. Certifique-se de "Linhas" for definidas como 1. Em seguida, clique em "Atualizar coleção" e a cena deve ser semelhante a figura a seguir. 


![Base de Mrlearning Cap2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>Observação: Dependendo da orientação do objeto pai ou objetos filho, provavelmente você precisará ajustar a orientação de configuração de forma diferente em projetos futuros. A largura da célula e os campos de altura da célula também precisará ser definido de forma diferente, dependendo do tamanho dos objetos em sua coleção.

### <a name="adding-text-into-your-scene"></a>Adicionando texto na sua cena

Nesta seção, você aprenderá como adicionar e editar o texto para suas experiências de realidade misturada. Se você ainda não fez isso, verifique se você tem TextMeshPro habilitada no Unity, seguindo as instruções [aqui](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).

1. Selecione o objeto pai "ButtonCollection" e clique com botão direito a coleção. Expanda "objeto 3D" no menu suspenso e selecione "TextMeshPro – Text". Você deve ver um objeto TextMeshPro sob a coleção de botões, conforme mostrado na imagem abaixo.

![Lição 2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Step1b de Chapter4 da lição 2](images/Lesson2_Chapter4_Step1b.JPG)

2. No campo de texto do componente TextMeshPro (localizado no painel Inspetor, conforme mostrado abaixo), digite "Texto de coleção do botão". O texto será exibido na cena, mas ele será ocultado por trás de botões e/ou o tamanho incorreto.

![Etapa 2 de Chapter4 da lição 2](images/Lesson2_Chapter4_Step2.JPG)

3. Para melhorar o tamanho do texto e o posicionamento para facilitar a leitura, ajuste o campo "tamanho da fonte" no componente TextMeshPro para alterar o tamanho da fonte. Você também precisará ajustar a posição do "Rect transformar" e a escala conforme mostrado na imagem abaixo. Consulte as imagens abaixo para os valores usados para nossa configuração de texto e fique à vontade usar esses valores como um ponto de partida do qual melhorar ainda mais o tamanho e o posicionamento do seu campo de texto.

![Lição 2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![etapa 4 do Chapter4 da lição 2](images/Lesson2_Chapter4_Step4.JPG)

5. Para modificar os valores de texto nos objetos de botão, clique na seta ao lado de qualquer botão para expandi-lo e navegue até o objeto "SeeItSayItLabel" e, em seguida, navegue até "TextMeshPro", onde você pode editar o texto para os botões, conforme descrito nas etapas acima.

![Step 5 de Chapter4 da lição 2](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>Parabéns!
Nesta lição, você aprendeu como copiar, personalizar e definir uma configuração de perfil MRTK (ou seja, visibilidade de malha percepção espacial.) Você também aprendeu como interagir com o botão para disparar eventos usando mãos controladas em 2 o HoloLens. Por fim, você aprendeu a criar uma interface do usuário simple usando o texto de malha Pro do Unity componente de coleção de objetos de grade do MRTK.

[Próxima lição: Solvers e posicionamento de conteúdo dinâmico](mrlearning-base-ch3.md)

