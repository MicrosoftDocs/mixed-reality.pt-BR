---
title: Tutoriais de introdução-3. Criando interface do usuário e Configurando o kit de ferramentas de realidade mista
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: e961238b8fc7f2ef15bea5f25eba8a8e9eb2ef3e
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334392"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. criando a interface do usuário e Configurando o kit de ferramentas de realidade mista

Na lição anterior, você aprendeu sobre alguns dos recursos que o MRTK (Kit de ferramentas de realidade misturada) tem a oferecer ao iniciar seu primeiro aplicativo para o HoloLens 2. Nesta próxima lição, você aprenderá a criar e organizar botões juntamente com os painéis de texto da interface do usuário e usar a interação padrão (toque) para interagir com cada botão. Você também explorará a adição de ações e efeitos simples, como alterar o tamanho, o som e a cor de objetos. Este módulo apresentará conceitos básicos sobre a modificação de perfis MRTK, começando pela desativação da visualização de malha de [mapeamento espacial](spatial-mapping.md) .

## <a name="objectives"></a>Objetivos

* Personalizar e configurar perfis do Kit de Ferramentas de Realidade Misturada
* Interagir com hologramas usando elementos e botões de interface do usuário
* Interações e entrada de acompanhamento de mão básicas

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Como configurar os perfis do kit de ferramentas de realidade misturada (alterar a opção de exibição de conscientização espacial)

Nesta seção, você aprenderá a personalizar e configurar os perfis de MRTK padrão ajustando a opção de exibição da malha de conscientização espacial. Você pode seguir esses mesmos princípios para ajuste quaisquer configurações ou valores nos perfis do MRTK.

1. Selecione MRTK (Kit de ferramentas de realidade mista) na hierarquia BaseScene. No painel Inspetor, procure o script Mixed Reality Toolkit e selecione o perfil ativo, conforme mostrado na figura abaixo. Clique duas vezes para abri-lo.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step1.png)

    >[!NOTE]
    >Por padrão, os perfis do MRTK não são editáveis. Esses são modelos de perfil padrão que você pode copiar e personalizar. Há várias camadas de personalização e perfis. Portanto, é a prática padrão copiar e personalizar vários perfis ao configurar uma ou mais configurações.
    >
    >Para descobrir mais sobre perfis de MRTK e sua arquitetura, visite a [documentação do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>).

2. Crie uma cópia do perfil padrão para personalizá-lo. Comece clicando em **copiar & personalizar**.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2a.png)

    Isso abrirá a janela pop-up *perfil de clonagem* .

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2b.png)

    Clique em **clonar** para criar uma cópia do perfil MRTK. Com sua própria cópia do perfil do MRTK, agora você tem a capacidade de personalizar as configurações nesse perfil. Você também precisará repetir a etapa de cópia e personalização para quaisquer perfis adicionais aninhados sob esse perfil, conforme descrito nas etapas subsequentes.

3. Desabilite a visibilidade da malha de reconhecimento espacial. Para fazer isso, localize as configurações do sistema de conscientização espacial, conforme mostrado na imagem abaixo. Verifique se a opção **habilitar sistema de conscientização espacial** está marcada. Clique no botão **clonar** à direita do perfil do sistema de conscientização espacial para substituir o perfil padrão por uma cópia personalizável. Na janela pop-up exibida, pressione o botão **clonar** , conforme mostrado na segunda imagem abaixo.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3a.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3b.png)

4. Crie uma cópia personalizada do Observador da Malha Espacial de Realidade Misturada Padrão. Clique na seta para baixo ao lado de observador de malha espacial da realidade mista do Windows para ver opções adicionais.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4a.png)

    Nessas opções, você verá o observador de malha espacial de realidade misturada padrão que está acinzentado (não editável). Você deve substituir esse perfil padrão por uma cópia personalizável para poder editá-lo. Como você fez anteriormente, clique no botão **clonar** e, na janela pop-up exibida, pressione o botão **clonar** , conforme mostrado na segunda imagem abaixo.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4b.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4c.png)

5. Em seguida, você ajustará as configurações para a opção de exibição dizer "oclusão". Isso torna a malha de mapeamento espacial invisível, mas ainda oculta objetos de jogo por trás da malha de mapeamento espacial, também conhecida como oclusão.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step5.png)

    >[!NOTE]
    >Observação: embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e você pode interagir com ela. Qualquer holograma por trás da malha de mapeamento espacial, como um holograma por trás de sua parede visível, não será visível devido à configuração oclusão.

Parabéns! Você acabou de aprender como modificar uma configuração do perfil do MRTK. Como é possível ver, para modificar as configurações do MRTK, você precisa criar cópias dos perfis padrão para poder editá-los. Você sempre terá os perfis padrão, que não são editáveis, para voltar a se desejar criar um perfil com novas configurações ou se você puder consultar os perfis padrão. Há várias configurações que você pode ajustar. Para obter uma referência completa às configurações de perfil do MRTK, consulte a documentação do MRTK aqui: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>Botões interativos e gestos de acompanhamento de mão

Nesta seção, você aprenderá a usar o acompanhamento à mão para pressionar um botão que poderá ser pressionado.

1. Selecione ativos na pasta projetos.

2. Digite "PressableButtonHoloLens2" na barra de pesquisa.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step2.png)

3. Arraste o pré-fabricado (representado por uma caixa azul) chamado "PressableButtonHoloLens2" na sua hierarquia e defina definir os valores de posição como x = 0, y = 0 e z = 0,2 para que o botão esteja na frente da câmera. (A câmera está posicionada na origem).

    >[!NOTE]
    >Se você receber uma mensagem sobre "importando o TMP Essentials", importe-a neste momento. Se o TMP Essentials ainda não tiver feito parte do seu projeto, talvez seja necessário repetir essa etapa depois de importar os conceitos básicos do TMP, caso contrário, o texto do botão pode não aparecer.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step3.png)

4. Adicione um cubo à cena. Clique com o botão direito do mouse na área hierarquia, selecione um objeto 3D e clique em cubo.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6a.png)

    Agora, um cubo deve estar na exibição. Ele aparecerá muito grande. Você pode ajustar as coordenadas (enquanto o cubo ainda está selecionado na área hierarquia) para diminuir o tamanho. Defina os valores de escala como x = 0, 2, y = 0, 2 e z = 0, 2. Certifique-se de posicionar o cubo em sua cena próximo ao botão, mas não se sobrepondo a ele. Na imagem abaixo, a posição do cubo é x = 0, y = 0, 4 e z = 0,2.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6b.png)

    >[!NOTE]
    >Em geral, 1 unidade no Unity é aproximadamente equivalente a 1 metro no mundo físico. Há exceções a isso; por exemplo, quando os objetos são filhos de objetos dimensionados.

5. Com o objeto de jogo PressableButtonHoloLens2 selecionado, role até a parte inferior no Inspetor para localizar a seção de eventos do componente de interação (script).

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step4.png)

6. Modificaremos o evento existente para dar ao botão um evento para responder quando for enviado por push. Como você pode ver, o tipo de receptor de evento é definido como InteractableOnPressReceiver. Isso permite que o botão responda a um evento pressionado quando uma mão acompanhada pressiona o botão. Neste ponto, você também deve alterar o filtro de interação para quase e longe.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step5.png)

7. Nesta etapa você configurará o cubo para alterar a cor quando o botão for pressionado. Selecione o PressableButtonHoloLens2 na hierarquia BaseScene e arraste o objeto de jogo cubo da hierarquia BaseScene para o campo somente tempo de execução, conforme mostrado na imagem abaixo.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7a.png)

    Clique na lista suspensa que não diz nenhuma função. Selecione MeshRenderer e, em seguida, selecione material material. Isso permite que você altere o material quando o botão é pressionado.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7b.png)

    Clique no círculo ao lado do campo material vazio para abrir o pop-up selecionar material. O MRTK inclui muitos materiais e cores para sua escolha. Para este exemplo, você vai usar o material, MRTK_Standard_Cyan, encontrado digitando "MRTK_Standard" na barra de pesquisa pop-up. Selecione o material de MRTK_Standard_Cyan para preencher o campo material.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7c.png)

    O evento agora está configurado para que quando o botão for pressionado, o cubo mudará de cor com base no material especificado. Neste exemplo, o cubo mudará para a cor ciano.

8. Em seguida, você vai configurar a ação de liberação para que, após a liberação, o botão volte à sua cor padrão. Repita a etapa 7 acima. No entanto, desta vez com o evento onRelease, em vez do material de MRTK_Standard_LightGray do onPress, conforme mostrado na imagem abaixo.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step8.png)

    Agora, quando o botão for pressionado, ele será alterado para uma nova cor; cores. Quando o botão for liberado, ele será alterado de volta para a cor padrão especificada (por exemplo, cinza claro). Pressione o botão reproduzir na parte superior da tela para testá-lo no editor ou implantar em seu HoloLens 2, para testar. Para saber mais sobre a simulação no editor, incluindo a simulação manual, leia a [página de documentação da simulação do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>).

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Criando um painel de botões usando a coleção de objetos de grade do MRTK

Nesta seção, você aprenderá a alinhar automaticamente vários botões em uma interface do usuário clara usando a ferramenta GridObjectCollection do MRTK.

1. Duplique o botão da seção anterior até que você tenha cinco botões. Há várias maneiras de fazer isso:-clique com o botão direito do mouse no botão e clique em copiar. Em seguida, vá para baixo até o botão e clique com o botão direito do mouse novamente e clique em colar.
    -Clique com o botão direito do mouse no botão e clique em duplicar.
    -Use o comando de teclado clicando no cubo e pressionando CTRL D no teclado.

    Repita esse procedimento até ter cinco botões; Consulte as cinco setas vermelhas na imagem abaixo.

    ![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Agrupe os botões sob um objeto do jogo pai vazio. Para ter os botões na coleção de grade, você precisa agrupar os botões em um objeto pai comum. Clique com o botão direito do mouse em hiearachy e clique em criar vazio. Isso cria um objeto do jogo vazio para você colocar todos os botões. Ele aparece como gameobject. Clique e renomeie-o com o botão direito do mouse.

    ![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Mova todos os botões para a nova coleção. Faça isso selecionando todos os cinco objetos de botão em sua hierarquia e arraste-os todos em objeto de jogo Buttoncollection, conforme mostrado na imagem abaixo. Dica: Selecione vários itens mantendo a tecla Ctrl pressionada ao selecionar itens.

    ![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Adicione o componente coleção de objetos de grade do MRTK à coleção de botões. Para fazer isso, selecione o objeto pai Buttoncollection. No painel Inspetor, clique no botão Adicionar componente. Procure coleção de objetos de grade na barra de pesquisa e selecione-a quando ela aparecer na lista.

    ![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3-step4.png)

    O componente coleção de objetos de grade permite organizar botões ou qualquer conjunto de objetos em uma linha, coluna ou grade organizada. Esse é um dos blocos de construção fornecidos pelo MRTK que oferece uma maneira rápida e fácil de criar interfaces de usuário atraentes.

5. Configure a coleção de objetos de grade. Para garantir que todos os botões enfrentem o usuário, selecione tipo de orientação. Em seguida, selecione frente pai encaminhar, conforme mostrado na imagem abaixo. Em seguida, altere o tamanho da célula para definir o espaço entre seus botões. Comece com 0, 5 unidades por 0, 5 unidades para a largura da célula e a altura da célula, conforme mostrado na imagem abaixo. Verifique se a distância está definida como 0 e se as linhas estão definidas como 1. Clique em atualizar coleção. A cena será semelhante à imagem abaixo.

    ![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3-step5.png)

    >[!NOTE]
    >Dependendo da orientação dos objetos pai ou objetos filho, provavelmente você precisará ajustar a orientação de configuração de forma diferente em projetos futuros. Os campos Largura da Célula e Altura da Célula também podem precisar ser definidos de forma diferente, dependendo do tamanho dos objetos na sua coleção.

## <a name="adding-text-into-your-scene"></a>Adicionando texto na sua cena

Nesta seção, você aprenderá como adicionar e editar o texto às suas experiências de realidade misturada. Se ainda não tiver feito isso, verifique se você tem o TextMeshPro habilitado no Unity seguindo as instruções [aqui](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).

1. Selecione o objeto pai Buttoncollection e clique com o botão direito do mouse na coleção. Expanda objeto 3D no menu suspenso. Em seguida, selecione TextMeshPro-Text. Você deve ver um objeto TextMeshPro sob a coleção de botões, conforme mostrado na imagem abaixo.

    ![lição 2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG) ![lição 2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. Para melhorar o tamanho do texto e o posicionamento para facilitar a leitura, ajuste o campo tamanho da fonte no componente TextMeshPro para alterar o tamanho da fonte. Você também precisará ajustar a posição e a escala de transformação Rect, conforme mostrado na imagem abaixo. Veja as imagens abaixo para obter os valores usados para nossa configuração de texto. Sinta-se à vontade para usar esses valores como um ponto de partida para melhorar ainda mais o tamanho e o posicionamento do seu campo de texto.

    ![Lição 2 Chapter4 etapa 3](images/mrlearning-base-ch2-4-step3.png)

3. No campo de texto do componente TextMeshPro no painel Inspetor, digite "texto da coleção de botão" e ajuste as propriedades de alinhamento para centro e superior, conforme mostrado na imagem abaixo.

    ![Lição 2 Chapter4 etapa 4](images/mrlearning-base-ch2-4-step4.png)

4. Para modificar os valores de texto nos objetos de botão, clique na seta ao lado de qualquer botão para expandi-lo e navegue até o objeto SeeItSayItLabel. Navegue até TextMeshPro, em que você pode editar o texto em seus botões, conforme descrito nas etapas acima.

    ![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a>Parabéns

Nesta lição, você aprendeu a copiar, personalizar e configurar uma configuração de perfil MRTK (ou seja, a visibilidade da malha de conscientização espacial). Você também aprendeu como interagir com um botão para disparar eventos usando mãos controladas no HoloLens 2. Por fim, você aprendeu a criar uma interface de interface do usuário simples usando a malha de texto do Unity pro e o componente de coleção de objetos de grade do MRTK.

[Próxima lição: 4. colocando o conteúdo dinâmico e usando os solveres](mrlearning-base-ch3.md)
