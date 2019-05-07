---
title: Módulo MR Learning Base - experiência de exemplo do Assembly de módulo Lunar
description: Nesta lição, vamos combina vários conceitos que aprendi com lições anteriores para criar uma experiência de exemplo exclusivo.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, hololens de tutoriais, unity,
ms.openlocfilehash: 303ed17724ba8799490aa7bca7a60600f6e5349b
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929609"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>Módulo MR Learning Base - experiência de exemplo do Assembly de módulo Lunar

Nesta lição, vamos combina vários conceitos que aprendi com lições anteriores para criar uma experiência de exemplo exclusivo. Vamos criar um aplicativo de assembly lunar módulo no qual um usuário precisará usar mãos controladas para captar lunar módulo partes e tenta montar um módulo lunar. Nós usaremos pressable botões para alternar as dicas de posicionamento, para redefinir a nossa experiência e para iniciar nosso módulo lunar no espaço! No futuro tutoriais, continuaremos a aproveitam essa experiência, incluindo poderosos multiusuários casos de uso que aproveita as âncoras espacial do Azure para alinhamento espacial.

## <a name="objectives"></a>Objetivos

- Combinar vários conceitos das lições anteriores para criar uma experiência única
- Saiba como ativar e desativar objetos
- Disparar eventos complexos usando os botões pressable
- Usar o rigidbody física e força
- Explorar o uso de dicas de ferramenta

## <a name="instructions"></a>Instruções

### <a name="configuring-the-lunar-module"></a>Configurar o módulo Lunar

Neste capítulo, podemos conhecerá os vários componentes necessários para criar nossa experiência de exemplo.

1. Adicione módulo lunar assembly pré-fabricado à sua cena de Base. Para fazer isso, na guia seu projeto, procure "Rocket Launcher_Tutorial". Você também pode achar pré-fabricado nos ativos > BaseModuleAssets > pré-fabricados. Você poderá ver duas rocket iniciador pré-fabricados; um com o nome "tutorial" e outro com o nome "concluem." Arraste pré-fabricado "Rocket Launcher_Tutorial" à sua cena de Base. Fique à vontade posicionar o posicionamento de pré-fabricado na sua cena.
   Observação: Pré-fabricado "Rocket Launcher_Complete" é o iniciador de concluído, fornecido para referência. 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

Se você expandir o objeto do jogo "Rocket Launcher_Tutorial" em sua hierarquia e expandir ainda mais o objeto "Módulo Lunar", você verá vários objetos filho que têm um material chamado "raio x". O material do "raio-x" permite que uma cor ligeiramente translúcida que usaremos como dicas de posicionamento para o usuário. 

![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) há cinco partes para o módulo lunar que o usuário vai interagir, conforme mostrado na imagem abaixo:

1.  O compartimento de exploração de Marte
2.  O tanque de combustível
3.  A célula de energia
4.  O Portal de encaixe 
5.  O sensor externo

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> Observação: Os nomes de objeto do jogo que você vê em sua hierarquia da cena base não correspondem aos nomes dos objetos na cena.

Etapa 2: Adicione uma fonte de áudio para o módulo lunar. Verifique se que o módulo lunar está selecionado na sua hierarquia da cena de base e clique em "Adicionar componente". Pesquise por "Audio Source" e adicione-o ao objeto. Deixe em branco por enquanto. Nós usaremos isso para reproduzir o som de lançamento mais tarde.
 ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) etapa 3: Adicione o script "dicas de posicionamento de alternância." Clique em "Adicionar componente" e pesquise por "Dicas de posicionamento de alternância." Este é um script personalizado que permite ativar e desativar as dicas translúcidas (objetos com o material de raios-x) mencionadas anteriormente. 
![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) etapa 4: Como temos 5 objetos, digite "5" para o tamanho da matriz de objeto do jogo. Em seguida, você deverá ver 5 novos elementos. 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

Arraste cada um dos objetos translúcidos para as caixas de dizem "None (objeto do jogo)". Arraste os seguintes objetos de módulo na sua cena base lunar: 

• Mochila

•   GasTank

• Topleftbody

• Nariz

•   LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

Agora, o script "Ativar/desativar as dicas de posicionamento" está configurado. Isso nos permitirá ativar e desativar às dicas.

Etapa 5: Adicione o script de "início lunar módulo". Clique no botão "Adicionar componente", pesquise "módulo de inicialização lunar" e selecioná-lo. Esse script será responsável por iniciar o módulo lunar. Quando clicamos em um botão configurado, ele adicionará uma força para cima ao componente de um corpo rígido lunar do módulo e fará com que o módulo Iniciar para cima. Se você estiver em locais fechados, o módulo lunar pode falhar em relação a sua malha de teto. Mas se você estiver pessoas, ele irá surgir ao espaço indefinidamente. 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

Etapa 6: Ajuste o foco para que o módulo lunar será voar normalmente. Tente um valor de 0,01. Deixe o campo "Rb" em branco. No construtor de relatórios significa um corpo rígido, e esse campo será preenchido automaticamente durante o tempo de execução.

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Visão geral do módulo Lunar partes
O objeto do módulo Lunar partes pai é a coleção de objetos que o usuário irá interagir com. Os nomes de objeto do jogo (com cenário de rotulado nomes em paretheses) são fornecidos na lista abaixo:

- Mochila (tanque de combustível)
- GasTank (célula de energia)
- TopLeftBody (exploração de Marte compartimento)
- Nariz (encaixe Portal)
- LeftTwirler (Sensor externo)

Observe que cada um desses objetos tem o manipulador de manipulação, conforme discutido na lição 4. Com o manipulador de manipulação, os usuários são capazes de capturar e manipular o objeto. Observe também que a configuração de "tipo de manipulação serão entregues dois" é definida como "mover e girar." Isso permite apenas que o usuário mover o objeto e não alterar seu tamanho, o que é a funcionalidade desejada para um aplicativo do assembly.
Além disso, a manipulação mais distante está desmarcada para permitir somente a interação direta de partes de módulo.

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

O script de demonstração do assembly de parte (mostrado acima) é o script que gerencia os objetos a ser colocado no módulo lunar pelo usuário. 

O campo de "Objeto para outro" é a transformação que é selecionada (n o caso da imagem acima, no tanque de combustível/mochila) com o objeto que ele possa se conectar. 

As configurações de "Quase Distance" e "Muito Distance" são responsáveis por determinar a proximidade aos quais partes serão ajustado no local ou ser liberadas. Por exemplo, no tanque de combustível/mochila precisariam ser 0,1 unidades de longe o módulo lunar para encaixar no lugar. O "muito Distance" define o local em que o objeto precisa ser desanexar do módulo lunar. Nesse caso, mão do usuário deve pegar o tanque de combustível/mochila e puxe-unidades de 0,2 distância o módulo lunar para removê-lo de volta o encaixe no lugar.

O "objeto de dica de ferramenta" é o rótulo de dica de ferramenta na cena. Quando os objetos são encaixados em vigor, o rótulo será desabilitado. 

A fonte de áudio será ser capturada automaticamente. 

### <a name="placement-hints-buttons"></a>Botões de dicas de posicionamento
Na [lição 2](mrlearning-base-ch2.md), você aprendeu como colocar e configurar os botões para fazer coisas como alterar a cor de um item ou torná-lo a executar um som quando ela é enviada por push. Continuaremos a usar esses princípios, como podemos configurar nossos botões para alternar as dicas de posicionamento. 

O objetivo é configurar o nosso botão para que toda vez que o usuário pressiona o botão de dica de posicionamento, ele irá alternar a visibilidade das dicas de posicionamento translúcido. 

Etapa 1: Mova o módulo de Lunar no slot vazio "somente tempo de execução" no painel Inspetor enquanto o objeto de dicas de posicionamento está selecionado na sua hierarquia da cena de base. 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) etapa 2: Agora, clique na lista suspensa onde não diz, "nenhuma função". Vá para baixo até "TogglePlacementHints" e, no menu Selecionar "ToggleGameObjects ()." ToggleGameObjects() alternará as dicas de posicionamento e desativar para que eles sejam visível ou invisível toda vez que o botão é pressionado.
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Configurando o botão de redefinição

Haverá situações em que o usuário faz um engano ou por acidente gera que o objeto imediatamente, ou apenas deseja posicionar a experiência. O botão Redefinir adicionará a capacidade de reiniciar a experiência. 

Etapa 1: Selecione o botão de redefinição. A cena de base, ele é denominado "ResetRoundButton". 

Etapa 2: Arraste o módulo de lunar da hierarquia de cena de base para o slot vazio em "pressionado" painel de Inspetor.
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

Etapa 3: Selecione o menu suspenso que diz: "nenhuma função" e passe o mouse sobre "LaunchLunarModule". Agora, selecione "resetModule ()."

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> Observação: Você observará que, por padrão, o "GameObject.BroadcastMessage" está configurado para "ResetPlacement". Isso será difundir uma mensagem de chamada "ResetPlacement" para todos os objetos filho de RocketLauncher_Tutorial. Qualquer objeto que tem um método para "ResetPlacement()" responderá a essa mensagem, redefinindo sua posição. 

### <a name="launching-the-lunar-module"></a>Iniciando o módulo Lunar
Este capítulo nós configuraremos o botão Iniciar. Isso permitirá que o usuário pressione o botão e inicie o módulo Lunar no espaço.

Etapa 1: Selecione o botão de inicialização (cena base é chamado "LaunchRoundButton"). Arraste o módulo de Lunar para o slot vazio em "End Touch" no painel Inspetor.
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) etapa 2: Selecione o menu suspenso que diz: "nenhuma função". Passe o mouse sobre "LaunchLunarModule" e selecione "StopThruster ()." Isso irá controlar quanto o usuário deseja dar ao módulo Lunar de foco. 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) etapa 3: Em "ButtonPressed()", adicione o módulo Lunar (clicar, mantenha e arrastar) para o slot vazio. 

Etapa 4: Clique no menu suspenso que diz: "nenhuma função" e passe o mouse sobre "LaunchLunarModule" e selecione "StartThruster ()." 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) etapa 5: Adicione música ao módulo Lunar de forma que quando o rocket crescer, a música funcionem. Para fazer isso, arraste o módulo Lunar para o próximo slot vazio em "Botão Pressed()".

Etapa 6: Selecione o menu suspenso que diz: "nenhuma função" e passe o mouse sobre "AudioSource" e selecione "PlayOneShot (AudioClip)". Fique à vontade explorar a variedade de sons incluído com o MRTK. Neste exemplo, vamos ficar com "MRTK_Gem".
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>Parabéns! 
Você configurou totalmente esse aplicativo! Agora quando você pressiona play, você pode totalmente montar o módulo Lunar, ativar/desativar as dicas, inicie o módulo Lunar e redefini-lo para fazê-lo novamente.
