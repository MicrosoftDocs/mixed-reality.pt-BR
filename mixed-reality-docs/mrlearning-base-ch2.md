---
title: Módulo básico de aprendizado de MR – Configuração do kit de ferramentas de interface do usuário, acompanhamento de mão e realidade misturada
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730946"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>Módulo básico de aprendizado de MR – Configuração do kit de ferramentas de interface do usuário, acompanhamento de mão e realidade misturada

Na lição anterior, você aprendeu algumas das funcionalidades que o MRTK tem a oferecer, iniciando seu primeiro aplicativo para o HoloLens 2. Nesta próxima lição, você aprenderá como criar e organizar os botões, juntamente com os painéis de texto de interface do usuário e usar a interação padrão (toque) para interagir com cada botão. Você também explorará a adição de ações e efeitos simples, como alterar o tamanho, o som e a cor de objetos. Este módulo apresenta os conceitos básicos sobre como modificar perfis do MRTK, começando com a desativação da visualização da malha espacial. 

## <a name="objectives"></a>Objetivos

* Personalizar e configurar perfis do Kit de Ferramentas de Realidade Misturada
* Interagir com hologramas usando os botões e elementos de interface do usuário
* Interações e entrada de acompanhamento de mão básicas

## <a name="instructions"></a>Instruções

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Como configurar os perfis do Kit de Ferramentas de Realidade Misturada (alterar a opção de exibição de reconhecimento espacial)
Nesta seção, você aprenderá a personalizar e configurar os perfis do Kit de Ferramentas de Realidade Misturada padrão ajustando a opção de exibição da malha de reconhecimento espacial. Você pode seguir esses mesmos princípios para ajuste quaisquer configurações ou valores nos perfis do MRTK.

1. Selecione o MRTK (Kit de Ferramentas de Realidade Misturada) da hierarquia "BaseScene". No painel do inspetor, procure o "Script do Kit de Ferramentas de Realidade Misturada" e selecione o "perfil ativo", conforme mostrado na figura abaixo. Clique duas vezes para abri-lo.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>Observação: Por padrão, os perfis do MRTK não são editáveis. Esses são os modelos de perfil padrão que você pode copiar e personalizar. Existem várias camadas de personalização e perfis, portanto, é uma prática padrão copiar e personalizar vários perfis ao definir uma ou mais configurações.
>
>Para descobrir mais sobre perfis do MRTK e sua arquitetura, visite a [documentação do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).

2. Crie uma cópia do perfil padrão para personalizá-lo. Para copiar um perfil padrão, clique no botão “Copiar e Personalizar” (veja a imagem). Isso cria uma cópia do perfil do MRTK. Com sua própria cópia do perfil do MRTK, agora você pode personalizar as configurações nesse perfil. Você também precisará repetir a etapa de cópia/personalização para qualquer perfil adicional aninhado sob esse perfil, conforme descrito nas etapas subsequentes.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. Desabilite a visibilidade da malha de reconhecimento espacial. Para fazer isso, localize "Configurações do Sistema de Reconhecimento Espacial" conforme mostrado na imagem. Clique no botão "Clonar" à direita do "Perfil do Sistema de Reconhecimento Espacial" para substituir o perfil padrão com uma cópia personalizável. Se uma janela pop-up aparecer, pressione o botão "Clonar", conforme mostrado na segunda imagem abaixo.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Crie uma cópia personalizada do Observador da Malha Espacial de Realidade Misturada Padrão. Clique na seta para baixo ao lado de "Observador da Malha Espacial do Windows Mixed Reality" para ver opções adicionais. Nessas opções, você verá o “Observador da Malha Espacial de Realidade Misturada Padrão”, que aparece esmaecido (não editado). Você deve substituir esse perfil padrão por uma cópia personalizável para poder editá-lo. Clique no botão à direita (marcado pela seta verde) para clonar uma cópia.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. Em seguida, você ajustará as configurações para a opção de exibição dizer "oclusão". Isso torna a malha espacial invisível, mas ainda oculta objetos do jogo atrás da malha espacial (Isso é conhecido como oclusão.)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>Observação: Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e você pode interagir com ela. Qualquer holograma atrás da malha de mapeamento espacial (por exemplo, um holograma atrás de sua parede visível) não será visível por causa da configuração de oclusão.

Parabéns! Você acabou de aprender como modificar uma configuração do perfil do MRTK. Como é possível ver, para modificar as configurações do MRTK, você precisa criar cópias dos perfis padrão para poder editá-los. Você sempre terá os perfis padrão (que não são editáveis) para retornar se você quiser criar um perfil com as novas configurações ou revisar os perfis padrão. Há várias configurações que você pode ajustar. Para obter uma referência completa para as configurações de perfil do MRTK, consulte a documentação do MRTK aqui: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Botões interativos e gestos de acompanhamento de mão
Nesta seção, você aprenderá como usar o acompanhamento de mão para pressionar um botão interativo.

1. Selecione "Ativos" na pasta de projetos.

2. Digite "pressablebutton" na barra de pesquisa.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. Arraste o pré-fabricado (representado por uma caixa azul) chamado "PressableButton" na sua hierarquia. 

   > Observação: Se você receber uma mensagem "importando TMP Essentials", importe-o neste momento. Se o TMP Essentials ainda não fizer parte do seu projeto, poderá ser necessário repetir essa etapa depois de importar o TMP Essentials, caso contrário, o texto do botão poderá não aparecer.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. Clique duas vezes no objeto do jogo "PressableButton" (que agora deve estar em sua hierarquia BaseScene) para exibi-lo na sua cena, conforme mostrado na imagem abaixo (seus gráficos de botão podem aparecer diferentes da imagem abaixo). 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. No painel do inspetor, clique em "Adicionar Evento" para fornecer ao botão um evento ao qual responder quando enviado por push. Na opção que aparece, selecione o menu suspenso. Selecione "InteractableOnPressReciever". Isso permite que o botão responda a um evento pressionado quando uma mão acompanhada pressiona o botão.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. Adicione um cubo à cena. Clique com o botão direito do mouse na área de hierarquia, selecione o objeto 3D e clique em "cubo". Agora, um cubo deve estar na exibição. Ele aparecerá muito grande, então, ajuste as coordenadas (enquanto "cubo" ainda estiver selecionado na área de hierarquia) para diminuir o tamanho. Defina os valores de escala para x = 0,1, y = 0,1 e z = 0,1. Certifique-se de posicionar o cubo na sua cena para colocá-lo próximo ao botão pressionável, mas sem sobrepor o botão. Na imagem abaixo, a posição do cubo é x = 0, y = 0,2 e z = 1. 

   > Observação: Em geral, 1 unidade no Unity é aproximadamente equivalente a 1 metro no mundo físico. Há exceções, por exemplo, quando objetos são filhos de objetos dimensionados.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. Nesta etapa você configurará o cubo para alterar a cor quando o botão for pressionado. Selecione o PressableButton no menu "BaseScene". No painel do inspetor, na caixa "Selecionar o Tipo de Evento", clique no botão "+". Arraste o "cubo" do menu "BaseScene" para a caixa "Apenas Tempo de Execução", conforme mostrado na imagem abaixo

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

Clique na lista suspensa que diz "Nenhuma Função". Selecione "MeshRenderer" e selecione "Material material". Isso permitirá que você altere o material quando o botão for pressionado. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

Vá para o painel do projeto e pesquise o material para o qual deseja alterá-lo. Você usará o material "MRTK_Standard_Cyan" para esse exemplo, encontrado digitando "ciano" na barra de pesquisa da guia de projeto (o MRTK inclui muitos materiais e cores para escolher.) Arraste o material para a caixa sob "MeshRenderer.material". Os materiais do MRTK podem ser encontrados em Ativos>MixedRealityToolkit.SDK>StandardAssets>Materiais.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

O evento agora está configurado para que quando o botão for pressionado, o cubo mudará de cor com base no material especificado. Neste exemplo, o cubo mudará para a cor ciano.

8. Em seguida, você configurará a ação de liberação de modo que, após ser solto, o botão voltará para sua cor padrão. Repita a Etapa 7 (na etapa anterior), mas desta vez com o evento de "OnRelease" em vez de o evento "OnPress", conforme mostrado na imagem abaixo.

9.  No painel de projeto, pesquise um material para o cubo utilizar como padrão quando o botão for solto (no nosso caso, escolhemos MRTK_Standard_LightGray.) Arraste o material para a caixa abaixo do campo “MeshRenderer.material”.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

Agora, quando o botão é pressionado, ele deve mudar para uma nova cor (por exemplo, ciano) e quando o botão é solto, ele deve mudar para a cor padrão especificada (por exemplo, cinza claro.) Pressione o botão "reproduzir" na parte superior da tela para experimentar isso no editor ou implantar em seu HoloLens 2 para testar. Para saber mais sobre a simulação no editor, incluindo sobre a simulação da mão, leia a [página de documentação de simulação do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>). 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Criando um painel de botões usando a coleção de objetos de grade do MRTK

Nesta seção, você aprenderá como alinhar automaticamente vários botões em uma interface do usuário nítida usando a ferramenta GridObjectCollection do MRTK.

1. Duplique o botão da seção anterior até que você tenha 5 botões. Há várias maneiras de fazer isso:
- Clique com o botão direito do mouse no botão e clique em “copiar”, em seguida, vá para a área abaixo do botão e clique com o botão direito do mouse novamente e clique em “colar”. 
- Clique com o botão direito do mouse e clique em “duplicar”. 
- Use o comando de teclado clicando no cubo e pressionando "CTRL + D" no teclado.

Repita isso até que você tenha cinco botões no total (veja as cinco setas vermelhas na imagem abaixo).

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Agrupe os botões sob um objeto do jogo pai vazio. Para ter os botões na coleção de grade, você precisa agrupá-los sob um objeto pai comum. Clique com o botão direito do mouse na hierarquia e clique em “criar vazio”. Isso cria um objeto do jogo vazio para você colocar todos os botões. Ele será exibido como "gameObject". Clique com o botão direito do mouse e renomeie-o como "ButtonCollection".

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Mova todos os botões para a nova coleção. Faça isso selecionando todos os cinco objetos de botão na sua hierarquia e arraste-os para baixo do objeto do jogo "ButtonCollection", conforme mostrado na imagem abaixo. Dica: selecione vários itens mantendo a tecla CTRL pressionada enquanto seleciona os itens.

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Adicione o componente de "Coleção de Objetos de Grade" do MRTK à coleção de botões.  Para fazer isso, selecione o objeto pai "ButtonCollection" e, no painel do inspetor, clique no botão "Adicionar Componente". Em seguida, pesquise "Coleção de Objetos de Grade" na barra de pesquisa e selecione-o quando aparecer na lista.

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

O componente Coleção de Objetos de Grade permite organizar botões ou qualquer conjunto de objetos em uma linha, coluna ou grade nítida. Esse é um dos blocos de construção fornecidos pelo MRTK que oferece uma maneira rápida e simples de criar belas interfaces de usuário.

5. Configure a coleção de objetos de grade. Para garantir que todos os botões estejam voltados para o usuário, selecione “tipo de orientação” e, em seguida, “voltar o pai para a frente” (como mostrado na imagem). Em seguida, altere o tamanho da célula para definir o espaço entre seus botões. Comece com 0,12 por 0,12 unidade para a Largura da Célula e a Altura da Célula, conforme mostrado na imagem abaixo. Talvez você precise ajustar esses valores, dependendo dos ativos de objeto/botão escolhidos. Certifique-se de que "Linhas" está definido como 1. Em seguida, clique em "Atualizar Coleção" e a cena deve ser semelhante à figura a seguir. 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>Observação: Dependendo da orientação dos objetos pai ou objetos filho, provavelmente você precisará ajustar a orientação de configuração de forma diferente em projetos futuros. Os campos Largura da Célula e Altura da Célula também podem precisar ser definidos de forma diferente, dependendo do tamanho dos objetos na sua coleção.

### <a name="adding-text-into-your-scene"></a>Adicionando texto na sua cena

Nesta seção, você aprenderá como adicionar e editar o texto às suas experiências de realidade misturada. Caso ainda não tenha feito isso, certifique-se de que TextMeshPro esteja habilitado no Unity seguindo as instruções [aqui](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).

1. Selecione o objeto pai "ButtonCollection" e clique com o botão direito do mouse na coleção. Expanda "Objeto 3D" no menu suspenso e selecione "TextMeshPro – Texto". Você deve ver um objeto TextMeshPro sob a coleção de botões, conforme mostrado na imagem abaixo.

![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. No campo Texto do componente TextMeshPro (localizado no painel do inspetor, conforme mostrado abaixo), digite "Texto da Coleção do Botão". O texto será exibido na cena, mas ele será ocultado atrás de botões e/ou o tamanho incorreto.

![Lesson2 Chapter4 Step2](images/Lesson2_Chapter4_Step2.JPG)

3. Para melhorar o tamanho do texto e o posicionamento para facilitar a leitura, ajuste o campo "tamanho da fonte" no componente TextMeshPro para alterar o tamanho da fonte. Você também precisará ajustar a posição do "Transformação de ret." e a escala conforme mostrado na imagem abaixo. Consulte as imagens abaixo para encontrar os valores usados para nossa configuração de texto e fique à vontade para usar esses valores como um ponto de partida do qual melhorar o tamanho e o posicionamento do seu campo de texto.

![Lesson2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Chapter4 Step4](images/Lesson2_Chapter4_Step4.JPG)

5. Para modificar os valores de texto nos objetos de botão, clique na seta ao lado de qualquer botão para expandi-lo e navegue até o objeto "SeeItSayItLabel" e, em seguida, navegue até "TextMeshPro", em que você pode editar o texto para os botões, conforme descrito nas etapas acima.

![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>Parabéns
Nesta lição, você aprendeu como copiar, personalizar e definir uma configuração de perfil do MRTK (ou seja, visibilidade de malha de percepção espacial.) Você também aprendeu como interagir com um botão para disparar eventos usando mãos rastreadas no HoloLens 2. Por fim, você aprendeu a criar uma interface do usuário simples usando a Malha de Texto Pro do Unity do componente da Coleção de Objetos de Grade do MRTK.

[Próxima lição: Solucionadores e posicionamento de conteúdo dinâmico](mrlearning-base-ch3.md)

