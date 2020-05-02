---
title: Tutoriais de introdução – 7. Criar um aplicativo de exemplo do módulo Lunar
description: Nesta lição, você vai combinar vários conceitos aprendidos em lições anteriores para criar uma experiência de exemplo exclusiva.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031552"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. Criar um aplicativo de exemplo do módulo Lunar
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

Neste tutorial, vários conceitos são combinados de lições anteriores para criar uma experiência de exemplo exclusiva. Você aprenderá a criar um aplicativo de montagem de peça no qual um usuário precisa usar mãos acompanhadas para pegar peças e tentar montar um módulo lunar. Você usará botões pressionáveis para alternar as dicas de posicionamento entre ligadas e desligadas, redefinir a experiência e para lançar o módulo lunar no espaço!

Em tutoriais futuros, você continuará a aproveitar essa experiência, incluindo poderosos casos de uso de vários usuários que aproveitam as Âncoras Espaciais do Azure para fins de alinhamento espacial.

## <a name="objectives"></a>Objetivos

* Combine vários conceitos das lições anteriores para criar uma experiência exclusiva
* Saiba como alternar objetos
* Dispare eventos complexos usando os botões pressionáveis
* Use força e física de corpo rígido
* Explore o uso de dicas de ferramenta

## <a name="lunar-module-parts-overview"></a>Visão geral das peças do Módulo Lunar
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

Nesta seção, você criará um desafio de montagem de peças simples em que a meta do usuário é posicionar cinco peças distribuídas na mesa na localização correta do Módulo Lunar.

As principais etapas que você seguirá para conseguir isso são:

1. Adicionar o pré-fabricado do Lançador de Foguete à cena
2. Habilitar a manipulação de objetos para todas as partes
3. Adicionar e configurar o componente de Demonstração do Assembly de Parte (Script)

> [!NOTE]
> O componente de Demonstração de Montagem de Peças (Script) não faz parte do MRTK. Ele foi fornecido com os ativos deste tutorial.

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. Adicionar o pré-fabricado do Lançador de Foguete à cena

Na janela Projeto, navegue até a pasta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher**, arraste o pré-fabricado **RocketLauncher** para a janela Hierarquia para adicioná-lo à sua cena e posicione-o em uma localização adequada, por exemplo:

* Posição da Transformação X = 1,5, Y = -0,4, Z = 0, de modo que esteja posicionada à direita do usuário na altura da cintura
* Rotação da Transformação X = 0, Y = 180, Z = 0, de modo que os principais recursos da experiência estejam voltados para o usuário

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. Habilitar a manipulação de objetos para todas as partes

Na janela Hierarquia, localize o objeto RocketLauncher > **LunarModuleParts** e selecione todos os **objetos filho**, adicione o componente **Manipulador de Manipulação (Script)** e o componente **Capturável de Interação Próxima (Script)** , então configure o Manipulador de Manipulação (Script) da seguinte maneira:

* Desmarque a caixa de seleção **Permitir Manipulação Distante** para permitir apenas interação próxima
* Altere **Tipo de Manipulação de Duas Mãos** para **Mover Girar** para que o dimensionamento seja desabilitado

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> Como um lembrete, para obter instruções passo a passo sobre como implementar a manipulação de objetos, você pode consultar as instruções de [Como manipular objetos 3D](mrlearning-base-ch4.md#manipulating-3d-objects).

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. Adicionar e configurar o componente de Demonstração do Assembly de Parte (Script)

Com todos os objetos filho LunarModuleParts ainda selecionados, adicione um componente de **Fonte de Áudio** e, em seguida, configure-o da seguinte maneira:

* Atribua um clipe de áudio adequado ao campo **AudioClip**, por exemplo, MRKT_Scale_Start
* Desmarque a caixa de seleção **Reproduzir ao Despertar** para que o clipe de áudio não seja automaticamente tocado quando a cena for carregada
* Alterar **Mistura Espacial** para 1 para habilitar o áudio espacial

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

Com todos os objetos filho LunarModuleParts ainda selecionados, adicione o componente **Demonstração do Assembly de Parte (Script)** :

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

Na janela Hierarquia, selecione o objeto **RoverEnclosure** e configure seu componente **Demonstração do Assembly de Parte (Script)** da seguinte maneira:

* Para o campo **objeto a ser Posicionado**, atribua o objeto **em si**, neste caso, o objeto RoverEnclosure
* Para o campo **Localização a Posicionar**, atribua o objeto **PlacementHints** correspondente, neste caso, o objeto RoverEnclosure_PlacementHint
* Para o campo **Objeto de Dica de Ferramenta**, atribua a **Dica de Ferramenta** correspondente, neste caso, o objeto RoverEnclosure_ToolTip
* Para o campo **Fonte de Áudio**, atribua o objeto **em si**, neste caso, o objeto RoverEnclosure

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

**Repita** para cada um dos outros objetos filho LunarModuleParts, ou seja, FuelTank, EnergyCell, DockingPortal e ExternalSensor.

Se agora você inserir o modo de Jogo e mover um "Objeto a Posicionar" próximo de seu "Localização a Posicionar" correspondente, você notará:

* O objeto será encaixado no lugar e subordinado sob o objeto LunarModule para que ele passe a fazer parte do Módulo Lunar
* A Fonte de Áudio no objeto reproduzirá o Clipe de Áudio atribuído na localização do objeto
* O objeto da Dica de Ferramenta correspondente ficará oculto

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> Para um lembrete de como usar a simulação de entrada no editor, você pode consultar o guia [Como usar a simulação de entrada de mão no editor para testar uma cena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) no [Portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="configuring-the-lunar-module"></a>Configuração do módulo lunar

Nesta seção, você adicionará mais recursos ao aplicativo Lançador de Foguete para que o usuário possa:

* Interagir com o Módulo Lunar
* Lançar o Módulo Lunar no espaço e tocar um som quando ele for lançado
* Redefinir o aplicativo para que o Módulo Lunar e todas as partes sejam colocados de volta em sua posição original
* Oculte as dicas de posicionamento para tornar o desafio de montagem de peças mais difícil.

As principais etapas que você seguirá para conseguir isso são:

1. Habilitar a manipulação de objetos 3D
2. Habilitar a física
3. Adicionar um componente de Fonte de Áudio
4. Adicionar e configurar o componente de Iniciar o Módulo Lunar (Script)
5. Adicionar e configurar o componente Alternar Dicas de Posicionamento (Script)

> [!NOTE]
> O componente do Lançar Módulo Lunar (Script) e o componente Alternar Dicas de Posicionamento (Script) não fazem parte do MRTK. Eles foram fornecidos com os ativos deste tutorial.

### <a name="1-enable-object-manipulation"></a>1. Habilitar a manipulação de objetos 3D

Na janela Hierarquia, selecione o objeto RocketLauncher > **LunarModule**, adicione o componente **Manipulador de Manipulação (Script)** e o componente **Capturável de Interação Próxima (Script)** , então configure o Manipulador de Manipulação (Script) da seguinte maneira:

* Desmarque a caixa de seleção **Permitir Manipulação Distante** para permitir apenas interação próxima
* Altere **Tipo de Manipulação de Duas Mãos** para Mover Girar para que o dimensionamento seja desabilitado

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. Habilitar a física

Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione um componente **Rigidbody** e, em seguida, configure-o da seguinte maneira:

* Desmarque a caixa de seleção **Usar Gravidade** para que o módulo lunar não seja afetado pela gravidade
* Marque a caixa de seleção **Is Kinematic** para que o Módulo Lunar inicialmente não seja afetado por forças físicas

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. Adicionar um componente de Fonte de Áudio

Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione um componente **Fonte de Áudio** e, em seguida, configure-o da seguinte maneira:

* Alterar **Mistura Espacial** para 1 para habilitar o áudio espacial

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. Adicionar e configurar o componente de Iniciar o Módulo Lunar (Script)

Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione o componente **Lançar Módulo Lunar (Script)** e, em seguida, configure-o da seguinte maneira:

* Altere o valor **Confiança** de modo que o Módulo Lunar voe de modo gracioso quando lançado, por exemplo, para 0,01

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. Adicionar e configurar o componente Alternar Dicas de Posicionamento (Script)

Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione o componente **Alternar Dicas de Posicionamento (Script)** e, em seguida, configure-o da seguinte maneira:

* Defina a propriedade **Tamanho** da Matriz de Objetos do Jogo como 5
* Atribua cada um dos **objetos filho** do objeto RocketLauncher > LunarModule > **PlacementHints** para o campo **Elemento** na Matriz de Objeto do Jogo:

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>Como configurar o botão Lançar

Na janela Hierarquia, selecione o objeto RocketLauncher > Botões > **LaunchButton**, então, no componente **Botão Pressionável (Script)** , crie um evento **Botão Pressionado ()** , configure o objeto **LunarModule** para receber o evento e defina **LaunchLunarModule.StartThruster** como a ação a ser acionada:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> Para obter um lembrete sobre como implementar eventos, você pode consultar as instruções de [Gestos de acompanhamento da mão e botões interativos](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).

Com o objeto RocketLauncher > Botões > **LaunchButton** ainda selecionado, no componente **Botão Pressionável (Script)** , crie um evento **Botão Pressionado ()** , configure o objeto **LunarModule** para receber o evento, defina **AudioSource.PlayOneShot** como a ação a ser acionada e atribua um clipe de áudio adequado ao campo **Clipe de Áudio**, por exemplo, o clipe de áudio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

Com o objeto RocketLauncher > Botões > **LaunchButton** ainda selecionado, no componente **Botão Pressionável (Script)** , crie um evento **Extremidade de Toque ()** , configure o objeto **LunarModule** para receber o evento e defina **LaunchLunarModule.StopThruster** como a ação a ser acionada:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

Se agora você inserir o modo de Jogo e pressionar o botão Lançar, ouvirá a reprodução do clipe de áudio e, se mantiver o botão Lançar pressionado por aproximadamente um segundo ou mais, verá o Módulo Lunar ser lançado no espaço:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>Como configurar o botão Redefinir

Na janela hierarquia, selecione o objeto RocketLauncher > Botões > **ResetButton** e, em seguida, no componente **Botão Pressionável (Script)** , crie um evento de **Botão Pressionado ()** , configure o objeto **LunarModule** para receber o evento e defina **LaunchLunarModule.ResetModule** como a ação a ser disparada:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

Com o objeto RocketLauncher > Botões > **ResetButton** ainda selecionado, no componente **Botão Pressionável (Script)** , crie um evento **Botão Pressionado ()** , configure o objeto **RocketLauncher** para receber o evento, defina **GameObject.BroadcastMessage** como a ação a ser disparada e insira **ResetPlacement** no campo de mensagem:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> A ação GameObject.BroadcastMessage envia a mensagem ResetPlacement do objeto RocketLauncher para todos os seus objetos filho. Qualquer objeto filho que tenha a função ResetPlacement, que é definida no componente de Demonstração de Montagem de Peças (script) que você adicionou a todos os objetos filho LunarModuleParts, invocará a função ResetPlacement, que redefinirá o posicionamento do objeto filho.

Se agora você entrar no modo de Jogo, mover algumas peças e/ou iniciar o Módulo Lunar e então pressionar o botão Redefinir, verá as peças e/ou o Módulo Lunar sendo redefinido para a posição original:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>Como configurar o botão Dicas de Posicionamento
<!-- TODO: Rename to 'Configuring the Hints button'-->

Na janela hierarquia, selecione o objeto RocketLauncher > Botões > **HintsButton** e, em seguida, no componente **Botão Pressionável (Script)** , crie um evento de **Botão Pressionado ()** , configure o objeto **LunarModule** para receber o evento e defina **TogglePlacementHints.ToggleGameObjects** como a ação a ser disparada:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

Se agora você entrar no modo Jogo, observará que as dicas de posicionamento translúcidas estão desabilitadas por padrão, mas que você pode ativá-las e desativá-las pressionando o botão Dicas:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>Parabéns

Você configurou totalmente este aplicativo. Agora, seu aplicativo permite que os usuários montem totalmente o Módulo Lunar, lancem o Módulo Lunar, alternem dicas e redefinam o aplicativo para que ele seja iniciado novamente.
