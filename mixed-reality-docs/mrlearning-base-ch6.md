---
title: Módulo MR Learning Base - experiência de exemplo de montagem do módulo lunar
description: Nesta lição, vamos combinar vários conceitos aprendidos em lições anteriores para criar uma experiência de exemplo exclusiva.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730843"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>Módulo MR Learning Base - experiência de exemplo de montagem do módulo lunar

Nesta lição, vamos combinar vários conceitos aprendidos em lições anteriores para criar uma experiência de exemplo exclusiva. Vamos criar um aplicativo de montagem do módulo lunar no qual um usuário precisará usar o acompanhamento da mão para pegar peças do módulo lunar e tenta montar um módulo lunar. Usaremos botões pressionáveis para alternar as dicas de posicionamento, para redefinir nossa experiência e para lançar o módulo lunar para o espaço! Em tutoriais futuros, continuaremos a aproveitar essa experiência, incluindo poderosos casos de uso de vários usuários que aproveitam as Âncoras Espaciais do Azure para fins de alinhamento espacial.

## <a name="objectives"></a>Objetivos

- Combine vários conceitos das lições anteriores para criar uma experiência exclusiva
- Saiba como alternar objetos
- Dispare eventos complexos usando os botões pressionáveis
- Use força e física de corpo rígido
- Explore o uso de dicas de ferramenta

## <a name="instructions"></a>Instruções

### <a name="configuring-the-lunar-module"></a>Configuração do módulo lunar

Neste capítulo, seremos apresentados aos vários componentes necessários para criar nossa experiência de exemplo.

1. Adicione o prefab do módulo lunar à sua cena base. Para fazer isso, na guia projeto, pesquise por "Rocket Launcher_Tutorial." Você também poderá encontrar o prefab em Assets>BaseModuleAssets>Prefabs. Você poderá ver dois prefabs de lançamento de foguetes; um com o nome "tutorial" e outro com o nome "complete." Arraste o prefab "Rocket Launcher_Tutorial" para sua cena base. Posicione o prefab como preferir em sua cena.
   Observação: O prefab "Rocket Launcher_Complete" é o lançador concluído, fornecido para referência. 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

Se você expandir o objeto de jogo "Rocket Launcher_Tutorial" em sua hierarquia e expandir mais ainda o objeto "Módulo lunar", verá diversos objetos filho que tem um material chamado "raio x". O material do "raio-x" possibilita uma cor ligeiramente translúcida que usaremos como dicas de posicionamento para o usuário. 

![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) Há cinco partes do módulo lunar com as quais o usuário vai interagir, como mostrado na imagem abaixo:

1.  O compartimento da Rover
2.  O tanque de combustível
3.  A célula de energia
4.  O Portal de Encaixe 
5.  O sensor externo

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> Observação: Os nomes de objeto do jogo que você vê em sua hierarquia da cena base não correspondem aos nomes dos objetos na cena.

Etapa 2: Adicione uma fonte de áudio ao módulo lunar. Verifique se que o módulo lunar está selecionado na hierarquia da cena base e clique em "Adicionar Componente". Pesquise por "Fonte de Áudio" e adicione-a ao objeto. Deixe em branco por enquanto. Usaremos isso para reproduzir o som de lançamento mais tarde.
 ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) Etapa 3: Adicione o script "alternar dicas de posicionamento". Clique em "Adicionar Componente" e pesquise por "Alternar Dicas de Posicionamento". Este é um script personalizado que permite ativar e desativar as dicas translúcidas (objetos com o material de raios-x) mencionadas anteriormente. 
![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) Etapa 4: Como temos 5 objetos, digite "5" para o tamanho da matriz de objeto do jogo. Em seguida, você deverá ver 5 novos elementos. 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

Arraste cada um dos objetos translúcidos para as caixas que dizem "Nenhum (Objeto do Jogo)". Arraste os seguintes objetos do módulo lunar para a cena base: 

•   Mochila

•   Tanque de combustível

•   Corpo superior esquerdo

•   Nariz

•   Giro esquerdo

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

Agora, o script "alternar dicas de posicionamento" está configurado. Isso nos permitirá ativar e desativar as dicas.

Etapa 5: Adicione o script de "lançar módulo lunar". Clique no botão "Adicionar Componente", pesquise por "módulo de lançamento lunar" e selecione-o. Esse script será responsável por lançar o módulo lunar. Quando pressionamos um botão configurado, ele adicionará uma força para cima ao componente do corpo rígido do módulo lunar e fará com que o módulo seja lançado para cima. Se você estiver em um local fechado, o módulo lunar pode bater na malha de teto. Mas, se estiver do lado de fora, ele voará para o espaço indefinidamente. 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

Etapa 6: Ajuste o impulso para que o módulo lunar voe para cima sem problemas. Tente um valor de 0,01. Deixe o campo "Rb" em branco. Rb significa corpo rígido e esse campo será preenchido automaticamente durante o tempo de execução.

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Visão geral das peças do módulo lunar
O objeto pai das peças do módulo lunar é a coleção dos objetos com os quais o usuário vai interagir. Os nomes de objeto do jogo (com os nomes das cenas entre parênteses) são fornecidos na lista abaixo:

- Mochila (tanque de combustível)
- Tanque de Combustível (célula de energia)
- Corpo Superior Esquerdo (compartimento da Rover)
- Nariz (Portal de Encaixe)
- Giro Esquerdo (sensor externo)

Observe que cada um desses objetos tem a alça de manipulação, conforme discutido na lição 4. Com a alça de manipulação, os usuários são capazes de capturar e manipular o objeto. Observe também que a configuração "tipo de manipulação com duas mãos" também está definido como "mover e girar". Isso permite somente que o usuário mova o objeto e não altere o tamanho dele, que é a funcionalidade desejada de um aplicativo de montagem.
Além disso, a manipulação distante está desmarcada para permitir apenas a interação direta de peças do módulo.

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

O script de demonstração de montagem de peças (mostrado acima) é o script que gerencia os objetos a serem colocados no módulo lunar pelo usuário. 

O campo "Objeto a Colocar" é a transformação selecionada (no caso da imagem acima, a mochila/tanque de combustível) com o objeto ao qual ela pode se conectar. 

As configurações "Distância próxima" e "Distância longe" são responsáveis pela determinação da proximidade nas quais as peças se encaixarão ou serão liberadas. Por exemplo, a mochila/tanque de combustível precisaria de 0,1 unidades de distância do módulo lunar para encaixar no lugar. A "Distância longe" define o local no qual o objeto precisa estar para se desconectar do módulo lunar. Nesse caso, a mão do usuário precisa pegar a mochila/tanque de combustível e puxá-la para 0,2 unidades de distância do módulo lunar para remover.

O "Objeto de Dica de Ferramenta" é o rótulo de dica de ferramenta na cena. Quando os objetos se encaixam no lugar, o rótulo é desabilitado. 

A Fonte de Áudio será capturada automaticamente. 

### <a name="placement-hints-buttons"></a>Botões de Dicas de Posicionamento
Na [Lição 2](mrlearning-base-ch2.md), você aprendeu como posicionar e configurar botões para fazer coisas como alterar a cor de um item ou fazer com que ele toque um som quando pressionado. Continuaremos a usar esses princípios conforme configuramos os botões para alternar dicas de posicionamento. 

O objetivo é configurar o botão para que, toda vez que o usuário pressionar o botão de dica de posicionamento, ele alterne a visibilidade das dicas de posicionamento translúcido. 

Etapa 1: Mova o módulo lunar para o slot vazio "somente tempo de execução" no painel do instrutor quando o objeto Dicas de Posicionamento estiver selecionado na hierarquia da cena base. 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Etapa 2: Agora clique na lista suspensa que diz "nenhuma função". Vá para baixo até "TogglePlacementHints" e, nesse menu, selecione "ToggleGameObjects ()." ToggleGameObjects() alternará as dicas de posicionamento entre ativadas e desativadas para que elas fiquem visíveis ou invisíveis cada vez que o botão é pressionado.
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Configurando o botão de redefinição

Haverá situações nas quais o usuário comete um erro ou joga o objeto fora por acidente ou apenas deseja reiniciar a experiência. O botão Redefinir adicionará a capacidade de reiniciar a experiência. 

Etapa 1: Selecione o botão de redefinição. Na cena base, ele se chama "ResetRoundButton". 

Etapa 2: Arraste o módulo de lunar da hierarquia de cena base para o slot vazio em "botão pressionado" no painel do inspetor.
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

Etapa 3: Selecione o menu suspenso que diz: "nenhuma função" e passe o mouse sobre "LaunchLunarModule". Agora selecione "resetModule ()."

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> Observação: Você observará que, por padrão, "GameObject.BroadcastMessage" está configurado como "ResetPlacement". Isso transmitirá uma mensagem chamada "ResetPlacement" para todos os objetos filho de RocketLauncher_Tutorial. Qualquer objeto que tem um método para "ResetPlacement()" responderá a essa mensagem, redefinindo sua posição. 

### <a name="launching-the-lunar-module"></a>Lançamento do módulo lunar
Neste capítulo, configuraremos o botão lançar. Isso permitirá que o usuário pressione o botão e lance o módulo lunar para o espaço.

Etapa 1: Selecione o botão de lançamento (na cena base é chamado de "LaunchRoundButton"). Arraste o módulo lunar para o slot vazio em "Toque Final" no painel do inspetor.
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Etapa 2: Selecione a lista suspensa que diz "nenhuma função". Passe o mouse sobre "LaunchLunarModule" e selecione "StopThruster ()." Isso controlará quanto impulso o usuário deseja dar ao módulo lunar. 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) Etapa 3: Em "ButtonPressed()", adicione o módulo lunar (clique, segure e arraste) para o slot vazio. 

Etapa 4: Clique no menu suspenso que diz: "nenhuma função" e passe o mouse sobre "LaunchLunarModule" e selecione "StartThruster ()." 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) Etapa 5: Adicione música ao módulo lunar de forma que, quando o foguete decolar, a música toque. Para fazer isso, arraste o módulo lunar para o próximo slot vazio em "Button Pressed()".

Etapa 6: Selecione o menu suspenso que diz "nenhuma função" e passe sobre "Fonte de Áudio" e selecione "PlayOneShot (AudioClip)". Fique à vontade para explorar a variedade de sons incluídos no MRTK. Neste exemplo, vamos continuar com o "MRTK_Gem."
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>Parabéns 
Você configurou totalmente esse aplicativo! Agora quando pressionar jogar, você poderá montar totalmente o módulo lunar, alternar as dicas, lançar o módulo lunar e redefini-lo para fazer tudo de novo.
