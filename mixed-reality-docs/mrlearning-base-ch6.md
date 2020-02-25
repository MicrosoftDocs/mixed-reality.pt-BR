---
title: Tutoriais de introdução-7. Criando um aplicativo de exemplo de módulo lunar
description: Nesta lição, você combinará vários conceitos aprendidos das lições anteriores para criar uma experiência de amostra exclusiva.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 3a557be91bee9b98e750ae1546ea1c4b3103298e
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555194"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. criando um aplicativo de exemplo de módulo lunar
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

Neste tutorial, vários conceitos são combinados de lições anteriores para criar uma experiência de amostra exclusiva. Você aprenderá a criar um aplicativo de assembly de parte, no qual um usuário precisa usar mãos controladas para pegar partes e tentar montar um módulo lunar. Você usará botões que poderão ser prensados para ativar e desativar Dicas de posicionamento, para redefinir a experiência e para iniciar o módulo lunar no espaço!

Em Tutoriais futuros, você continuará a se basear nessa experiência, que inclui casos avançados de uso de vários usuários que aproveitam as âncoras espaciais do Azure para o alinhamento espacial.

## <a name="objectives"></a>Objetivos

* Combine vários conceitos das lições anteriores para criar uma experiência exclusiva
* Saiba como alternar objetos
* Dispare eventos complexos usando os botões pressionáveis
* Use força e física de corpo rígido
* Explore o uso de dicas de ferramenta

## <a name="lunar-module-parts-overview"></a>Visão geral das partes do módulo lunar
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

Nesta seção, você criará um desafio de assembly de parte simples, em que o objetivo do usuário é posicionar cinco partes que são distribuídas na tabela no local correto do módulo lunar.

As principais etapas que você seguirá para conseguir isso são:

1. Adicionar o pré-fabricado do iniciador de Rocket à cena
2. Habilitar a manipulação de objetos para todas as partes
3. Adicionar e configurar o componente de demonstração do assembly de parte (script)

> [!NOTE]
> O componente de demonstração do assembly de parte (script) não faz parte do MRTK. Ele foi fornecido com os ativos deste tutorial.

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. Adicionar o pré-fabricado do iniciador de Rocket à cena

Na janela do projeto, navegue até os **ativos** > **MRTK. Tutoriais. GettingStarted** > **pré-fabricados** > pasta **RocketLauncher** , arraste o **RocketLauncher** pré-fabricado para a janela hierarquia para adicioná-lo à sua cena e, em seguida, posicione-o em um local adequado, por exemplo:

* Transforme a posição X = 1,5, Y =-0,4, Z = 0, portanto ela está posicionada à direita do usuário na altura de estou
* Rotação de transformação X = 0, Y = 180, Z = 0, portanto, os principais recursos da experiência enfrentam o usuário

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. habilitar a manipulação de objetos para todas as partes

Na janela hierarquia, localize o objeto RocketLauncher > **LunarModuleParts** e selecione todos os **objetos filho**, adicione o componente **manipulador de manipulação (script)** e o componente de **captura de interação Near (script)** e, em seguida, configure o manipulador de manipulação (script) da seguinte maneira:

* Desmarque a caixa de seleção **permitir manipulação distante** para permitir apenas interação próxima
* Altere o **tipo de manipulação de duas mãos** para **mover girar** para que o dimensionamento seja desabilitado

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> Para um lembrete, com instruções passo a passo, sobre como implementar a manipulação de objetos, você pode consultar as instruções [manipulando objetos 3D](mrlearning-base-ch4.md#manipulating-3d-objects) .

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. adicionar e configurar o componente de demonstração (script) do assembly de parte

Com todos os objetos filho LunarModuleParts ainda selecionados, adicione um componente de **fonte de áudio** e, em seguida, configure-o da seguinte maneira:

* Atribua um clipe de áudio adequado ao campo **AudioClip** , por exemplo, MRKT_Scale_Start
* Desmarque a caixa de seleção **reproduzir no ativo** , portanto, o clipe de áudio não é tocado automaticamente quando a cena é carregada
* Alterar a **mistura espacial** para 1 para habilitar o áudio espacial

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

Com todos os objetos filho LunarModuleParts ainda selecionados, adicione o componente de **demonstração do assembly de parte (script)** :

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

Na janela hierarquia, selecione o objeto **RoverEnclosure** e configure seu componente de **demonstração do assembly de parte (script)** da seguinte maneira:

* Para o campo **objeto a ser colocado** , atribua o objeto em **si**, neste caso, o objeto RoverEnclosure
* Para o campo **local para colocação** , atribua o objeto **PlacementHints** correspondente, nesse caso, o objeto RoverEnclosure_PlacementHint
* Para o campo **objeto Tip de ferramentas** , atribua a **dica**de ferramenta correspondente, nesse caso, o objeto RoverEnclosure_ToolTip
* Para o campo **fonte de áudio** , atribua o **próprio**objeto, neste caso, o objeto RoverEnclosure

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

**Repita** para cada um dos outros objetos filho LunarModuleParts, ou seja, FuelTank, EnergyCell, DockingPortal e ExternalSensor.

Se agora você inserir o modo de jogo e mover um ' objeto para o local ' próximo ao ' local para colocação ' correspondente, você notará:

* O objeto será ajustado no lugar e será pai do objeto LunarModule para que ele se torne parte do módulo lunar
* A fonte de áudio no objeto reproduzirá o clipe de áudio atribuído no local do objeto
* O objeto da dica de ferramenta correspondente ficará oculto

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> Para obter um lembrete sobre como usar a simulação de entrada no editor, você pode consultar o [usando a simulação de entrada do no editor para testar um](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guia de cena no [portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="configuring-the-lunar-module"></a>Configuração do módulo lunar

Nesta seção, você adicionará recursos adicionais ao aplicativo de iniciador do Rocket para que o usuário possa:

* Interagir com o módulo lunar
* Iniciar o módulo lunar no espaço e tocar um som quando ele for iniciado
* Redefinir o aplicativo para que o módulo lunar e todas as partes sejam colocados de volta para sua posição original
* Oculte as dicas de posicionamento para tornar o desafio do assembly da parte mais difícil.

As principais etapas que você seguirá para conseguir isso são:

1. Habilitar manipulação de objeto
2. Habilitar física
3. Adicionar um componente de fonte de áudio
4. Adicionar e configurar o componente módulo lunar (script) de inicialização
5. Adicionar e configurar o componente alternar dicas de posicionamento (script)

> [!NOTE]
> O componente do módulo lunar de inicialização (script) e o componente alternar dicas de posicionamento (script) não fazem parte do MRTK. Eles foram fornecidos com os ativos deste tutorial.

### <a name="1-enable-object-manipulation"></a>1. habilitar a manipulação de objetos

Na janela hierarquia, selecione o objeto RocketLauncher > **LunarModule** , adicione o componente **manipulador de manipulação (script)** e o componente de **captura de interação Near (script)** e, em seguida, configure o manipulador de manipulação (script) da seguinte maneira:

* Desmarque a caixa de seleção **permitir manipulação distante** para permitir apenas interação próxima
* Altere o **tipo de manipulação de duas mãos** para mover girar para que o dimensionamento seja desabilitado

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. habilitar a física

Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione um componente **Rigidbody** e, em seguida, configure-o da seguinte maneira:

* Desmarque a caixa de seleção **usar gravidade** para que o módulo lunar não seja afetado pela gravidade
* Marque a caixa de seleção **é cinemática** para que o módulo lunar inicialmente não seja afetado por Physic Forces

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. adicionar um componente de fonte de áudio

Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione um componente **fonte de áudio** e, em seguida, configure-o da seguinte maneira:

* Altere a **mistura espacial** para 1 para habilitar o áudio espacial

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. adicionar e configurar o componente do módulo lunar de abertura (script)

Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione o componente **módulo lunar de abertura (script)** e, em seguida, configure-o da seguinte maneira:

* Altere o valor de **Thrustmaster** para que o módulo lunar seja ativado normalmente quando iniciado, por exemplo, para 0, 1

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. adicionar e configurar o componente alternar dicas de posicionamento (script)

Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione o componente **alternar dicas de posicionamento (script)** e configure-o da seguinte maneira:

* Defina a propriedade **tamanho** da matriz de objetos do jogo como 5
* Atribua cada um dos **objetos filho** do objeto RocketLauncher > LunarModule > **PlacementHints** ao campo de um **elemento** da matriz do objeto Game:

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>Configurando o botão iniciar

Na janela hierarquia, selecione os botões de > de RocketLauncher > objeto **LaunchButton** e, em seguida, no componente de **botão pressionável (script)** , crie um novo evento **botão pressionado ()** , configure o objeto **LunarModule** para receber o evento e defina **LaunchLunarModule. StartThruster** como a ação a ser disparada:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> Para obter um lembrete sobre como implementar eventos, consulte as instruções [gestos de acompanhamento de mão e botões](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) que podem interagir.

Com os botões de > RocketLauncher > objeto **LaunchButton** ainda selecionado, no componente de **botão pressionável (script)** , crie um novo evento **botão pressionado ()** , configure o objeto **LunarModule** para receber o evento, defina **audioname. PlayOneShot** como a ação a ser disparada e atribua um clipe de áudio adequado ao campo de **clipe de áudio** , por exemplo, o clipe de áudio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

Com os botões de > RocketLauncher > objeto **LaunchButton** ainda selecionado, no componente de **botão pressionável (script)** , crie um novo evento **Touch end ()** , configure o objeto **LunarModule** para receber o evento e defina **LaunchLunarModule. StopThruster** como a ação a ser disparada:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

Se agora você inserir o modo de jogo e pressionar o botão Iniciar, ouvirá a reprodução do clipe de áudio e, se mantiver o botão iniciar por cerca de um segundo ou mais, você verá o módulo lunar aberto no espaço:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>Configurando o botão redefinir

Na janela hierarquia, selecione os botões de > de RocketLauncher > objeto **ResetButton** e, em seguida, no componente de **botão pressionável (script)** , crie um novo evento **botão pressionado ()** , configure o objeto **LunarModule** para receber o evento e defina **LaunchLunarModule. ResetModule** como a ação a ser disparada:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

Com os botões de > RocketLauncher > objeto **ResetButton** ainda selecionado, no componente de **botão pressionável (script)** , crie um novo evento **botão pressionado ()** , configure o objeto **RocketLauncher** para receber o evento, defina **gameobject. BroadcastMessage** como a ação a ser disparada e digite **ResetPlacement** no campo de mensagem:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> A ação gameobject. BroadcastMessage envia a mensagem ResetPlacement do objeto RocketLauncher para todos os seus objetos filho. Qualquer objeto filho que tenha a função ResetPlacement, que é definida no componente de demonstração de assembly de parte (script) que você adicionou a todos os objetos filho LunarModuleParts, invocará a função ResetPlacement, que redefinirá o posicionamento do objeto filho.

Se agora você inserir o modo de jogo, mova algumas partes e/ou inicie o módulo lunar e, em seguida, pressione o botão redefinir para ver as partes e/ou o módulo lunar que está sendo redefinido para sua posição original:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>Configurando o botão de dicas de posicionamento
<!-- TODO: Rename to 'Configuring the Hints button'-->

Na janela hierarquia, selecione os botões de > de RocketLauncher > objeto **HintsButton** e, em seguida, no componente de **botão pressionável (script)** , crie um novo evento **botão pressionado ()** , configure o objeto **LunarModule** para receber o evento e defina **TogglePlacementHints. ToggleGameObjects** como a ação a ser disparada:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

Se você agora entrar no modo de jogo, observará que as dicas de posicionamento translúcidas estão desabilitadas por padrão, mas que você pode ativá-las e desativá-las pressionando o botão de dicas:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>Parabéns

Você configurou totalmente este aplicativo. Agora, seu aplicativo permite que os usuários montem totalmente o módulo lunar, iniciem o módulo lunar, alternem dicas e redefinam o aplicativo para que ele seja iniciado novamente.
