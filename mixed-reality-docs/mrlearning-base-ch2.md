---
title: Tutoriais de introdução-3. Criando interface do usuário e Configurando o kit de ferramentas de realidade mista
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 925ab825c2716a847726ac763dc6800914d87c6b
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702043"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. Criando interface do usuário e Configurando o kit de ferramentas de realidade mista 

Na lição anterior, você aprendeu sobre alguns dos recursos que o MRTK (Kit de ferramentas de realidade misturada) tem a oferecer ao iniciar seu primeiro aplicativo para o HoloLens 2. Nesta próxima lição, você aprenderá a criar e organizar botões juntamente com os painéis de texto da interface do usuário e usar a interação padrão (toque) para interagir com cada botão. Você também explorará a adição de ações e efeitos simples, como alterar o tamanho, o som e a cor de objetos. Este módulo apresentará conceitos básicos sobre a modificação de perfis MRTK, começando pela desativação da visualização de malha espacial. 

## <a name="objectives"></a>Objetivos

* Personalizar e configurar perfis do Kit de Ferramentas de Realidade Misturada
* Interagir com hologramas usando elementos e botões de interface do usuário
* Interações e entrada de acompanhamento de mão básicas

## <a name="instructions"></a>Instruções

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Como configurar os perfis do Kit de Ferramentas de Realidade Misturada (alterar a opção de exibição de reconhecimento espacial)
Nesta seção, você aprenderá a personalizar e configurar os perfis de MRTK padrão ajustando a opção de exibição da malha de conscientização espacial. Você pode seguir esses mesmos princípios para ajuste quaisquer configurações ou valores nos perfis do MRTK.

1. Selecione MRTK (Kit de ferramentas de realidade mista) na hierarquia BaseScene. No painel Inspetor, procure o script Mixed Reality Toolkit e selecione o perfil ativo, conforme mostrado na figura abaixo. Clique duas vezes para abri-lo.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>Observação: Por padrão, os perfis do MRTK não são editáveis. Esses são modelos de perfil padrão que você pode copiar e personalizar. Há várias camadas de personalização e perfis. Portanto, é a prática padrão copiar e personalizar vários perfis ao configurar uma ou mais configurações.
>
>Para descobrir mais sobre perfis de MRTK e sua arquitetura, visite a [documentação do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).

2. Crie uma cópia do perfil padrão para personalizá-lo. Para copiar um perfil padrão, clique em copiar & Personalizar (consulte imagem). Isso cria uma cópia do perfil do MRTK. Com sua própria cópia do perfil do MRTK, agora você pode personalizar as configurações nesse perfil. Você também precisará repetir a etapa de cópia e personalização para quaisquer perfis adicionais aninhados sob esse perfil, conforme descrito nas etapas subsequentes.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. Desabilite a visibilidade da malha de reconhecimento espacial. Para fazer isso, localize as configurações do sistema de conscientização espacial, conforme mostrado na imagem. Clique no botão clonar à direita do perfil do sistema de conscientização espacial para substituir o perfil padrão por uma cópia personalizável. Se uma janela pop-up for exibida, pressione o botão clonar, conforme mostrado na segunda imagem abaixo.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Crie uma cópia personalizada do Observador da Malha Espacial de Realidade Misturada Padrão. Clique na seta para baixo ao lado de observador de malha espacial da realidade mista do Windows para ver opções adicionais. Nessas opções, você verá o observador de malha espacial de realidade misturada padrão que está acinzentado (não editável). Você deve substituir esse perfil padrão por uma cópia personalizável para poder editá-lo. Clique no botão à direita (marcado por uma seta verde) para clonar uma cópia.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. Em seguida, você ajustará as configurações para a opção de exibição dizer "oclusão". Isso torna a malha espacial invisível, mas ainda oculta objetos de jogo por trás da malha espacial, também conhecida como oclusão.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>Observação: Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e você pode interagir com ela. Qualquer holograma por trás da malha de mapeamento espacial, como um holograma por trás de sua parede visível, não será visível devido à configuração oclusão.

Parabéns! Você acabou de aprender como modificar uma configuração do perfil do MRTK. Como é possível ver, para modificar as configurações do MRTK, você precisa criar cópias dos perfis padrão para poder editá-los. Você sempre terá os perfis padrão, que não são editáveis, para voltar a se desejar criar um perfil com novas configurações ou se você puder consultar os perfis padrão. Há várias configurações que você pode ajustar. Para obter uma referência completa para as configurações de perfil do MRTK, consulte a documentação do MRTK aqui: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Botões interativos e gestos de acompanhamento de mão
Nesta seção, você aprenderá a usar o acompanhamento à mão para pressionar um botão que poderá ser pressionado.

1. Selecione ativos na pasta projetos.

2. Digite "pressablebutton" na barra de pesquisa.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. Arraste o pré-fabricado (representado por uma caixa azul) chamado "PressableButton" na sua hierarquia. 

   > Observação: Se você receber uma mensagem sobre "importando o TMP Essentials", importe-a neste momento. Se o TMP Essentials ainda não tiver feito parte do seu projeto, talvez seja necessário repetir essa etapa depois de importar os conceitos básicos do TMP, caso contrário, o texto do botão pode não aparecer.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. Clique duas vezes no objeto de jogo PressableButton, que agora deve estar em sua hierarquia BaseScene, para exibi-lo em sua cena, conforme mostrado na imagem abaixo. Os gráficos de botão podem parecer diferentes da imagem abaixo. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. No painel Inspetor, clique em Adicionar evento para dar ao botão um evento para responder quando enviado por push. Na opção exibida, selecione o menu suspenso e selecione InteractableOnPressReciever. Isso permite que o botão responda a um evento pressionado quando uma mão acompanhada pressiona o botão.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. Adicione um cubo à cena. Clique com o botão direito do mouse na área hierarquia, selecione um objeto 3D e clique em cubo. Agora, um cubo deve estar na exibição. Ele aparecerá muito grande. Você pode ajustar as coordenadas (enquanto o cubo ainda está selecionado na área hierarquia) para diminuir o tamanho. Defina os valores de escala para x = 0,1, y = 0,1 e z = 0,1. Certifique-se de posicionar o cubo na sua cena para colocá-lo próximo ao botão pressionável, mas sem sobrepor o botão. Na imagem abaixo, a posição do cubo é x = 0, y = 0,2 e z = 1. 

   > Observação: Em geral, 1 unidade no Unity é aproximadamente equivalente a 1 metro no mundo físico. Há exceções, por exemplo, quando objetos são filhos de objetos dimensionados.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. Nesta etapa você configurará o cubo para alterar a cor quando o botão for pressionado. Selecione o PressableButton no menu BaseScene. No painel Inspetor, na caixa Selecionar tipo de evento, clique no botão +. Arraste o cubo do menu BaseScene para a caixa somente de tempo de execução, conforme mostrado na imagem abaixo

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

Clique na lista suspensa que não diz nenhuma função. Selecione MeshRenderer e, em seguida, selecione material material. Isso permite que você altere o material quando o botão é pressionado. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

Vá para o painel projeto e pesquise o material para o qual você deseja alterá-lo. Você vai usar o material, MRTK_Standard_Cyan, para este exemplo, encontrado digitando "ciano" na barra de pesquisa da guia do projeto. (O MRTK inclui muitos materiais e cores para escolher.) Arraste o material para a caixa embaixo de MeshRenderer. material. Os materiais do MRTK podem ser encontrados em Ativos>MixedRealityToolkit.SDK>StandardAssets>Materiais.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

O evento agora está configurado para que quando o botão for pressionado, o cubo mudará de cor com base no material especificado. Neste exemplo, o cubo mudará para a cor ciano.

8. Em seguida, você configurará a ação de liberação de modo que, após ser solto, o botão voltará para sua cor padrão. Repita a etapa 7 acima. Mas desta vez com o evento onRelease em vez do evento onPress, conforme mostrado na imagem abaixo.

9.  No painel projeto, procure um material no qual o cubo seja padronizado na versão do botão. Nesse caso, escolhemos MRTK_Standard_LightGray. Arraste o material para a caixa abaixo do campo MeshRenderer. material.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

Agora, quando o botão for pressionado, ele será alterado para uma nova cor, ciano. Quando o botão for liberado, ele será alterado de volta para a cor padrão que você especificou (por exemplo, cinza claro). Pressione o botão reproduzir na parte superior da tela para testá-lo no editor ou implantar em seu HoloLens 2 para testar. Para saber mais sobre a simulação no editor, incluindo a simulação manual, leia a [página de documentação da simulação do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>). 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Criando um painel de botões usando a coleção de objetos de grade do MRTK

Nesta seção, você aprenderá a alinhar automaticamente vários botões em uma interface do usuário clara usando a ferramenta GridObjectCollection do MRTK.

1. Duplique o botão da seção anterior até que você tenha cinco botões. Há várias maneiras de fazer isso:
- Clique com o botão direito do mouse no botão e clique em copiar. Em seguida, vá para baixo para baixo do botão e clique com o botão direito do mouse novamente e clique em colar. 
- Clique com o botão direito do mouse no botão e clique em duplicar. 
- Use o comando de teclado clicando no cubo e pressionando CTRL D no teclado.

Repita esse procedimento até ter cinco botões; Consulte as cinco setas vermelhas na imagem abaixo.

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Agrupe os botões sob um objeto do jogo pai vazio. Para ter os botões na coleção de grade, você precisa agrupar os botões em um objeto pai comum. Clique com o botão direito do mouse em hiearachy e clique em criar vazio. Isso cria um objeto do jogo vazio para você colocar todos os botões. Ele aparece como gameobject. Clique com o botão direito e renomeie-o, Buttoncollection.

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Mova todos os botões para a nova coleção. Faça isso selecionando todos os cinco objetos de botão em sua hierarquia e arraste-os todos em objeto de jogo Buttoncollection, conforme mostrado na imagem abaixo. Dica: Selecione vários itens mantendo a tecla Ctrl pressionada ao selecionar itens.

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Adicione o componente coleção de objetos de grade do MRTK à coleção de botões. Para fazer isso, selecione o objeto pai Buttoncollection. No painel Inspetor, clique no botão Adicionar componente. Procure coleção de objetos de grade na barra de pesquisa e selecione-a quando ela aparecer na lista.

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

O componente coleção de objetos de grade permite organizar botões ou qualquer conjunto de objetos em uma linha, coluna ou grade organizada. Esse é um dos blocos de construção fornecidos pelo MRTK que oferece uma maneira rápida e fácil de criar interfaces de usuário atraentes.

5. Configure a coleção de objetos de grade. Para garantir que todos os botões enfrentem o usuário, selecione tipo de orientação. Em seguida, selecione frente pai encaminhar, conforme mostrado na imagem abaixo. Em seguida, altere o tamanho da célula para definir o espaço entre seus botões. Comece com 0,12 unidades por 0,12 unidades para a largura da célula e a altura da célula, conforme mostrado na imagem abaixo. Talvez seja necessário ajustar esses valores, dependendo dos ativos de objeto e de botão que foram escolhidos. Certifique-se de que as linhas estejam definidas como 1. Clique em atualizar coleção. A cena será semelhante à imagem abaixo. 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>Observação: Dependendo da orientação dos objetos pai ou objetos filho, provavelmente você precisará ajustar a orientação de configuração de forma diferente em projetos futuros. Os campos Largura da Célula e Altura da Célula também podem precisar ser definidos de forma diferente, dependendo do tamanho dos objetos na sua coleção.

### <a name="adding-text-into-your-scene"></a>Adicionando texto na sua cena

Nesta seção, você aprenderá como adicionar e editar o texto às suas experiências de realidade misturada. Caso ainda não tenha feito isso, certifique-se de que TextMeshPro esteja habilitado no Unity seguindo as instruções [aqui](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).

1. Selecione o objeto pai Buttoncollection e clique com o botão direito do mouse na coleção. Expanda objeto 3D no menu suspenso. Em seguida, selecione TextMeshPro-Text. Você deve ver um objeto TextMeshPro sob a coleção de botões, conforme mostrado na imagem abaixo.

![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. Para melhorar o tamanho do texto e o posicionamento para facilitar a leitura, ajuste o campo tamanho da fonte no componente TextMeshPro para alterar o tamanho da fonte. Você também precisará ajustar a posição e a escala de transformação Rect, conforme mostrado na imagem abaixo. Veja as imagens abaixo para obter os valores usados para nossa configuração de texto. Sinta-se à vontade para usar esses valores como um ponto de partida para melhorar ainda mais o tamanho e o posicionamento do seu campo de texto.

![Lição 2 Chapter4 etapa 3](images/Lesson2_Chapter4_Step3.JPG)

3. No campo de texto do componente TextMeshPro no painel Inspetor, conforme mostrado abaixo. Digite o texto da coleção de botões. O texto aparece na cena, mas ficará oculto atrás dos botões e/ou do tamanho errado.

![Lição 2 Chapter4 etapa 2](images/Lesson2_Chapter4_Step2.JPG)
![lição 2 Chapter4 etapa 4](images/Lesson2_Chapter4_Step4.JPG)

4. Para modificar os valores de texto nos objetos de botão, clique na seta ao lado de qualquer botão para expandi-lo e navegue até o objeto SeeItSayItLabel. Navegue até TextMeshPro, em que você pode editar o texto em seus botões, conforme descrito nas etapas acima.

![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a>Parabéns
Nesta lição, você aprendeu como copiar, personalizar e definir uma configuração de perfil do MRTK (ou seja, visibilidade de malha de percepção espacial.) Você também aprendeu como interagir com um botão para disparar eventos usando mãos rastreadas no HoloLens 2. Por fim, você aprendeu a criar uma interface do usuário simples usando a Malha de Texto Pro do Unity do componente da Coleção de Objetos de Grade do MRTK.

[Próxima lição: 4. Colocar o conteúdo dinâmico e usar solucionadores](mrlearning-base-ch3.md)

