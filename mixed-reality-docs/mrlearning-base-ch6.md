---
title: Tutoriais de introdução-7. Criando um aplicativo de exemplo de módulo lunar
description: Nesta lição, você combinará vários conceitos aprendidos das lições anteriores para criar uma experiência de amostra exclusiva.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 3127ffceea08202fe9d978ad77f8fddb6fba60a3
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334376"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. criando um aplicativo de exemplo de módulo lunar

Neste tutorial, vários conceitos são combinados de lições anteriores para criar uma experiência de amostra exclusiva. Você aprenderá a criar um aplicativo de assembly de módulo lunar, no qual um usuário precisa usar mãos controladas para pegar partes de módulo lunares e tentar montar um módulo lunar. Usamos botões pressionáveis para alternar dicas de posicionamento, redefinir nossa experiência e iniciar nosso módulo lunar no espaço! Em Tutoriais futuros, continuaremos a criar essa experiência, que inclui casos avançados de uso de vários usuários que aproveitam as âncoras espaciais do Azure para o alinhamento espacial.

## <a name="objectives"></a>Objetivos

- Combine vários conceitos das lições anteriores para criar uma experiência exclusiva
- Saiba como alternar objetos
- Dispare eventos complexos usando os botões pressionáveis
- Use força e física de corpo rígido
- Explore o uso de dicas de ferramenta

## <a name="configuring-the-lunar-module"></a>Configuração do módulo lunar

Nesta seção, apresentamos os vários componentes necessários para criar nossa experiência de exemplo.

1. Adicione o assembly de módulo lunar pré-fabricado à sua cena base. Para fazer isso, na guia projeto, navegue até ativos > BaseModuleAssets > pré-fabricados. Você verá duas pré-fabricados do iniciador de Rocket, arrastar o Rocket Launcher_Tutorial pré-fabricado para sua cena e posicioná-lo como desejar.

    >[!NOTE]
    >O Rocket Launcher_Complete pré-fabricado é o iniciador concluído, fornecido para referência.

    ![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

    Se você expandir o objeto de jogo do Rocket Launcher_Tutorial em sua hierarquia e expandir ainda mais o objeto do módulo lunar, encontrará vários objetos filho que têm um material chamado "x-ray". O material "x-ray" permite uma cor levemente translúcida que será usada como dicas de posicionamento para o usuário.

    ![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG)

    Há cinco partes para o módulo lunar com o qual o usuário irá interagir, conforme mostrado na imagem abaixo:

    1. O compartimento da Rover
    2. O tanque de combustível
    3. A célula de energia
    4. O Portal de Encaixe
    5. O sensor externo

    ![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    >Os nomes de objeto do jogo que você vê em sua hierarquia da cena base não correspondem aos nomes dos objetos na cena.

2. Adicione uma fonte de áudio ao objeto de jogo LunarModule. Verifique se o LunarModule está selecionado na sua hierarquia de cena e clique em Adicionar componente. Pesquise fonte de áudio e adicione-a ao objeto Game. Deixe o campo AudioClip em branco por enquanto, mas altere a configuração de mistura especial de 0 para 1 para habilitar o áudio espacial. Você usará essa fonte de áudio para reproduzir o som de inicialização mais tarde.

    ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. Adicione as dicas de posicionamento de alternância de script. Clique em Adicionar componente e procure alternar dicas de posicionamento. Esse é um script personalizado que permite ativar e desativar as dicas translúcidas (objetos com o material x-ray), conforme mencionado anteriormente.

    ![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. Como temos cinco objetos, digite "5" para o tamanho da matriz de objetos do jogo. Em seguida, você verá cinco novos elementos aparecerem.

    ![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

    Arraste cada um dos objetos translúcidas para todas as caixas nome (objeto de jogo). Arraste os seguintes objetos do módulo lunar em sua cena para os campos da matriz de objetos, conforme mostrado na imagem acima:

    ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

    O script alternar dicas de posicionamento agora está configurado, o que nos permite ativar e desativar as dicas.

5. Adicione o script abrir módulo lunar. Clique no botão Adicionar componente, pesquise "Iniciar módulo lunar" e selecione-o. Esse script inicia o módulo lunar. Quando pressionamos um botão configurado, ele adiciona uma força ascendente ao componente de corpo rígido do módulo lunar e faz com que o módulo seja iniciado para cima. Se você estiver em um local fechado, o módulo lunar pode bater na malha de teto. Se você estiver em uma área com grandes tetos ou sem teto, o módulo lunar irá para o espaço indefinidamente.

    ![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

6. Ajuste o impulso para que o módulo lunar voe para cima sem problemas. Tente um valor de 0,01. Deixe o campo "Rb" em branco. RB significa corpo rígido e este campo será preenchido automaticamente durante o tempo de execução.

    ![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

## <a name="lunar-module-parts-overview"></a>Visão geral das partes do módulo lunar

O objeto pai das partes do módulo lunar é a coleção dos objetos com os quais o usuário interage. Os nomes de objeto do jogo com a cena rotulada nomes entre parênteses, são fornecidos na lista abaixo:

- Mochila (célula de energia)
- GasTank (tanque de combustível)
- Corpo Superior Esquerdo (compartimento da Rover)
- Nariz (Portal de Encaixe)
- Giro Esquerdo (sensor externo)

Observe que cada um desses objetos tem um manipulador de manipulação, conforme explicado na lição 4. Esse recurso permite que os usuários obtenham e manipulem o objeto. Observe também que a configuração, tipo de manipulação de duas mãos, está definida como mover e girar. Essa opção só permite que o usuário mova o objeto e não altere seu tamanho, que é a funcionalidade desejada para um aplicativo de assembly.
Além disso, a manipulação distante está desmarcada para permitir apenas a interação direta de partes do módulo.

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

O script de demonstração do assembly de parte (mostrado acima) é o script que gerencia os objetos que o usuário coloca no módulo lunar pelo usuário.

O campo objeto a ser colocado é a transformação selecionada, conforme mostrado na imagem acima, o tanque de mochila/combustível associado ao objeto ao qual ele se conecta.

As configurações de distância aproximada e distante determinam a proximidade com a qual as partes se encaixam ou podem ser lançadas. Por exemplo, o tanque de mochila/combustível precisa ter 0,1 unidades fora do módulo lunar antes que ele se encaixe no local. A configuração de distância distante define o local onde o objeto pode ser antes que ele possa ser desanexado do módulo lunar. Nesse caso, a mão do usuário precisa pegar a mochila/tanque de combustível e puxá-la para 0,2 unidades de distância do módulo lunar para remover.

O objeto de dica de ferramenta é o rótulo de dica de ferramenta na cena. Quando os objetos são encaixados no lugar, o rótulo é desabilitado.

A fonte de áudio é automaticamente capturada.

## <a name="configuring-the-placement-hints-button"></a>Configurando o botão de dicas de posicionamento

Na [lição 2](mrlearning-base-ch2.md), você aprendeu a colocar e configurar botões para fazer coisas como alterar a cor de um item ou fazê-lo tocar um som quando enviado por push. Continuaremos a usar esses princípios conforme configuramos os botões para alternar dicas de posicionamento.

O objetivo é configurar nosso botão para que sempre que o usuário pressionar o botão de dica de posicionamento, ele alterne a visibilidade das dicas de posicionamento translúcidas.

1. Mova o módulo lunar para o slot somente de tempo de execução vazio no painel Inspetor enquanto o objeto de dicas de posicionamento estiver selecionado na sua hierarquia de cena base.

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. Clique na lista suspensa nenhuma função. Vá até TogglePlacementHints e selecione ToggleGameObjects () no menu. ToggleGameObjects () alterna as dicas de posicionamento ativadas e desativadas para que fiquem visíveis ou invisíveis sempre que o botão for pressionado.

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

## <a name="configuring-the-reset-button"></a>Configurando o botão redefinir

Haverá situações em que o usuário cometer um erro, emitirá acidentalmente o objeto para longe ou apenas deseja redefinir a experiência. O botão redefinir adiciona a capacidade de reiniciar a experiência.

1. Selecione o botão redefinir. Na cena base, ele é chamado de ResetRoundButton.

2. Arraste o módulo lunar da hierarquia de cena base para o slot vazio em botão pressionado no painel inspetor.

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. Selecione o menu suspenso sem função e focalize LaunchLunarModule e, em seguida, selecione resetModule ().

    ![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    >Observe que, por padrão, o gameobject. BroadcastMessage é configurado como ResetPlacement. Isso transmite uma mensagem chamada ResetPlacement para cada objeto filho do RocketLauncher_Tutorial. Qualquer objeto que tenha um método para ResetPlacement () responde a essa mensagem redefinindo sua posição.

## <a name="configuring-the-launch-button"></a>Configurando o botão iniciar

Esta seção explica como configurar o botão Iniciar, que permite ao usuário pressionar o botão e iniciar o módulo lunar no espaço.

1. Selecione o botão Iniciar. Na cena base, ele é chamado de LaunchRoundButton. Arraste o módulo lunar para o slot vazio em extremidade de toque no painel inspetor.

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. Selecione o menu suspenso sem função e focalize LaunchLunarModule e selecione StopThruster (). Isso controla a quantidade de Thrustmaster que o usuário deseja dar ao módulo lunar.

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. Arraste o módulo lunar da hierarquia de cena base para o slot vazio em botão pressionado no painel de Inspetor.

4. Clique no menu suspenso sem função e, em seguida, em LaunchLunarModule e selecione StartThruster ().

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. Adicione música ao módulo lunar para que a música seja reproduzida quando o Rocket retirar. Para fazer isso, arraste o módulo lunar para o próximo slot vazio em botão pressionado ().

6. Selecione o menu suspenso sem função, passe o mouse sobre Audioname e selecione PlayOneShot (AudioClip). Fique à vontade para explorar a variedade de sons incluídos no MRTK. Neste exemplo, vamos usar "MRTK_Gem".

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

## <a name="congratulations"></a>Parabéns

Você configurou totalmente este aplicativo. Agora, ao pressionar reproduzir, você pode montar totalmente o módulo lunar, alternar dicas, iniciar o módulo lunar e redefini-lo para iniciar novamente.
