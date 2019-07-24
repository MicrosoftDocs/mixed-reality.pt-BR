---
title: Módulo MR Learning Base - experiência de exemplo de montagem do módulo lunar
description: Nesta lição, vamos combinar vários conceitos aprendidos em lições anteriores para criar uma experiência de exemplo exclusiva.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 79f2d3a4a3224533761ea2e4a7e73dc3d4d5e53e
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387689"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. Criando um aplicativo de exemplo de módulo lunar

Neste tutorial, combinamos vários conceitos apresentados nas lições anteriores para criar uma experiência de amostra exclusiva. Criaremos um aplicativo de assembly de módulo lunar, no qual um usuário precisa usar as mãos controladas para pegar partes do módulo lunar e tentar montar um módulo lunar. Usamos botões pressionáveis para alternar dicas de posicionamento, redefinir nossa experiência e iniciar nosso módulo lunar no espaço! Em Tutoriais futuros, continuaremos a criar essa experiência, que inclui casos avançados de uso de vários usuários que aproveitam as âncoras espaciais do Azure para o alinhamento espacial.

## <a name="objectives"></a>Objetivos

- Combine vários conceitos das lições anteriores para criar uma experiência exclusiva
- Saiba como alternar objetos
- Dispare eventos complexos usando os botões pressionáveis
- Use força e física de corpo rígido
- Explore o uso de dicas de ferramenta

## <a name="instructions"></a>Instruções

### <a name="configuring-the-lunar-module"></a>Configuração do módulo lunar

Nesta seção, apresentamos os vários componentes necessários para criar nossa experiência de exemplo.

1. Adicione o assembly de módulo lunar pré-fabricado à sua cena base. Para fazer isso, na guia projeto, pesquise por Rocket Launcher_Tutorial. 
Localize o pré-fabricado em ativos-> BaseModuleAssets-> pré-fabricados. Você também verá dois Rocket Launcher pré-fabricados; um com o nome "tutorial" e o outro com o nome "concluído". Arraste o pré-fabricado de Rocket Launcher_Tutorial para sua cena base e posicione-o como desejar.
   Observação: O pré-fabricado de Rocket Launcher_Complete é o iniciador concluído, fornecido para referência. 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

Se você expandir o objeto de jogo Rocket Launcher_Tutorial em sua hierarquia e expandir ainda mais o objeto de módulo lunar, encontrará vários objetos filho que têm um material chamado "x-ray". O material "x-ray" permite uma cor levemente translúcida que usaremos como dicas de posicionamento para o usuário. 

![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) há cinco partes para o módulo lunar com o qual o usuário irá interagir, conforme mostrado na imagem abaixo:

1.  O compartimento da Rover
2.  O tanque de combustível
3.  A célula de energia
4.  O Portal de Encaixe 
5.  O sensor externo

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> Observação: Os nomes de objetos de jogos que você vê em sua hierarquia de cena base não correspondem aos nomes dos objetos na cena.

Etapa 2: Adicione uma fonte de áudio ao módulo lunar. Verifique se o módulo lunar está selecionado na sua hierarquia de cena base e clique em Adicionar componente. Pesquise fonte de áudio e adicione-a ao objeto. Deixe em branco por enquanto. Usaremos isso para reproduzir o som de lançamento mais tarde.

 ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)  
Etapa 3: Adicione o script, alterne as dicas de posicionamento. Clique em Adicionar componente e procure alternar dicas de posicionamento. Esse é um script personalizado que permite ativar e desativar as dicas translúcidas (objetos com o material x-ray) mencionado anteriormente.  
![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)  
Etapa 4: Como temos cinco objetos, digite "5" para o tamanho da matriz de objetos do jogo. Em seguida, você verá cinco novos elementos aparecerem.  


![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

Arraste cada um dos objetos translúcidas para todas as caixas de nome (jogo obect).
Arraste os seguintes objetos do módulo lunar para a cena base: 

•   Mochila

•   Tanque de combustível

•   Corpo superior esquerdo

•   Nariz

•   Giro esquerdo

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

Agora o script alternar dicas de posicionamento está configurado. Isso nos permite ativar e desativar Dicas.

Etapa 5: Adicione o script abrir módulo lunar. Clique no botão Adicionar componente, pesquise "Iniciar módulo lunar" e selecione-o. Esse script inicia o módulo lunar. Quando pressionamos um botão configurado, ele adiciona uma força ascendente ao componente de corpo rígido do módulo lunar e faz com que o módulo seja iniciado com versões anteriores. Se você estiver em um local fechado, o módulo lunar pode bater na malha de teto. Mas, se estiver do lado de fora, ele voará para o espaço indefinidamente. 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

Etapa 6: Ajuste o impulso para que o módulo lunar voe para cima sem problemas. Tente um valor de 0,01. Deixe o campo "Rb" em branco. Rb significa corpo rígido e esse campo será preenchido automaticamente durante o tempo de execução.

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Visão geral das partes do módulo lunar
O objeto pai das partes do módulo lunar é a coleção dos objetos com os quais o usuário interage. Os nomes de objeto do jogo, com a cena rotulada nomes em paretheses, são fornecidos na lista abaixo:

- Mochila (tanque de combustível)
- Tanque de Combustível (célula de energia)
- Corpo Superior Esquerdo (compartimento da Rover)
- Nariz (Portal de Encaixe)
- Giro Esquerdo (sensor externo)

Observe que cada um desses objetos tem um manipulador de manipulação, conforme discutido na lição 4. Com o manipulador de manipulação, os usuários podem pegar e manipular o objeto. Observe também que a configuração, tipo de manipulação de duas mãos, é definida como mover e girar. Isso permite somente que o usuário mova o objeto e não altere o tamanho dele, que é a funcionalidade desejada de um aplicativo de montagem.
Além disso, a manipulação distante está desmarcada para permitir apenas a interação direta de partes do módulo.

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

O script de demonstração do assembly de parte (mostrado acima) é o script que gerencia os objetos que o usuário coloca no módulo lunar pelo usuário. 

O campo objeto a ser colocado é a transformação selecionada, conforme mostrado na imagem acima, o tanque de mochila/combustível associado ao objeto ao qual ele se conecta. 

As configurações de distância aproximada e distante determinam a proximidade com a qual as partes se encaixam ou podem ser lançadas. Por exemplo, o tanque de mochila/combustível precisa ter 0,1 unidades fora do módulo lunar antes que ele se encaixe no local. A configuração de distância distante define o local onde o objeto pode ser antes que ele possa ser desanexado do módulo lunar. Nesse caso, a mão do usuário precisa pegar a mochila/tanque de combustível e puxá-la para 0,2 unidades de distância do módulo lunar para remover.

O objeto de dica de ferramenta é o rótulo de dica de ferramenta na cena. Quando os objetos são encaixados no lugar, o rótulo é desabilitado. 

A fonte de áudio é automaticamente capturada. 

### <a name="placement-hints-buttons"></a>Botões de dicas de posicionamento
Na [Lição 2](mrlearning-base-ch2.md), você aprendeu como posicionar e configurar botões para fazer coisas como alterar a cor de um item ou fazer com que ele toque um som quando pressionado. Continuaremos a usar esses princípios conforme configuramos os botões para alternar dicas de posicionamento. 

O objetivo é configurar nosso botão para que sempre que o usuário pressionar o botão de dica de posicionamento, ele alterne a visibilidade das dicas de posicionamento translúcidas. 

Etapa 1: Mova o módulo lunar para o slot somente de tempo de execução vazio no painel Inspetor enquanto o objeto de dicas de posicionamento estiver selecionado na sua hierarquia de cena base. 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Etapa 2: Agora, clique na lista suspensa sem função. Vá até TogglePlacementHints e, no menu, selecione ToggleGameObjects (). ToggleGameObjects () alterna as dicas de posicionamento ativadas e desativadas para que fiquem visíveis ou invisíveis sempre que o botão for pressionado.  
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Configurando o botão redefinir

Haverá situações em que o usuário cometer um erro ou, acidentalmente, lançar o objeto de longe, ou apenas deseja redefinir a experiência. O botão redefinir adiciona a capacidade de reiniciar a experiência. 

Etapa 1: Selecione o botão redefinir. Na cena base, ela é nomeada, ResetRoundButton. 

Etapa 2: Arraste o módulo lunar da hierarquia de cena base para o slot vazio, no botão, pressionado o painel de Inspetor.
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

Etapa 3: Selecione o menu suspenso sem função e passe o mouse sobre LaunchLunarModule, selecione resetModule ().

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> Observação: Observe que, por padrão, o gameobject. BroadcastMessage é configurado como ResetPlacement. Isso transmite uma mensagem chamada, ResetPlacement para cada objeto filho do RocketLauncher_Tutorial. Qualquer objeto que tenha um método para ResetPlacement () responde a essa mensagem redefinindo sua posição. 

### <a name="launching-the-lunar-module"></a>Iniciando o módulo lunar
Esta seção explaings como configurar o botão Iniciar. Isso permite que o usuário pressione o botão e inicie o módulo lunar no espaço.

Etapa 1: Selecione o botão Iniciar. Na cena base, ela é chamada, LaunchRoundButton. Arraste o módulo lunar para o slot vazio em extremidade de toque no painel inspetor.
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Etapa 2: Selecione o menu suspenso sem função e passe o mouse sobre LaunchLunarModule e selecione StopThruster (). Isso controla a quantidade de Thrustmaster que o usuário deseja dar ao módulo lunar. 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)  
Etapa 3: Em ButtonPressed (), adicione o módulo lunar (clique, mantenha pressionado e arraste) para o slot vazio. 

Etapa 4: Clique no menu suspenso sem função e passe o mouse sobre LaunchLunarModule e selecione StartThruster (). 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)  
Etapa 5: Adicione música ao módulo lunar para que a música seja reproduzida quando o Rocket retirar. Para fazer isso, arraste o módulo lunar para o próximo slot vazio em botão pressionado ().

Etapa 6: Selecione o menu suspenso sem função, passe o mouse sobre Audioname e selecione PlayOneShot (AudioClip). Fique à vontade para explorar a variedade de sons incluídos no MRTK. Neste exemplo, vamos usar "MRTK_Gem".
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>Parabéns 
Você configurou totalmente este aplicativo. Agora, ao pressionar reproduzir, você pode montar totalmente o módulo lunar, alternar dicas, iniciar o módulo lunar e redefini-lo para iniciar tudo novamente.
