---
title: Tutoriais de introdução – 6. Explorar as opções avançadas de entrada
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: ec078015304e1cddc9b042fb5e94cf1904a302cb
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376083"
---
# <a name="6-exploring-advanced-input-options"></a>6. Explorar as opções avançadas de entrada

Neste tutorial, você explorará várias algumas opções avançadas de entrada para o HoloLens 2, incluindo o uso de comandos de voz, o gesto de panorâmica e o acompanhamento ocular.

## <a name="objectives"></a>Objetivos

* Disparar eventos usando palavras-chave e comandos de voz
* Usar mãos rastreadas para aplicar a panorâmica de texturas e objetos 3D com mãos acompanhadas
* Aproveitar funcionalidades de acompanhamento ocular do HoloLens 2 para selecionar objetos

## <a name="enabling-voice-commands"></a>Habilitando comandos de voz
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

Nesta seção, você implementará um comando de fala para permitir que o usuário reproduza um som no objeto Octa. Para isso, você criará um comando de fala e, em seguida, configurará o evento para que ele dispare a ação desejada quando a palavra-chave do comando de fala for falada.

As principais etapas que você seguirá para conseguir isso são:

1. Clonar o Perfil do Sistema de Entrada padrão
2. Clonar o Perfil de Comandos de Fala padrão
3. Criar um comando de fala
4. Adicionar e configurar o componente do Manipulador de Entrada de Fala (Script)
5. Implementar o evento de Resposta para o comando de fala

### <a name="1-clone-the-default-input-system-profile"></a>1. Clonar o Perfil do Sistema de Entrada padrão

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, em seguida, na janela Inspetor, selecione a guia **Entrada** e clone o **DefaultHoloLens2InputSystemProfile** para substituí-lo por seu **Perfil do Sistema de Entrada** personalizável:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> Para obter um lembrete de como clonar perfis MRTK, você pode consultar as instruções de [Como configurar os perfis do Mixed Reality Toolkit](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).

### <a name="2-clone-the-default-speech-commands-profile"></a>2. Clonar o Perfil de Comandos de Fala padrão

Expanda a seção **Fala** e clone **DefaultMixedRealitySpeechCommandsProfile** para substituí-lo pelo seu **Perfil de Comandos de Fala** personalizável:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. Criar um comando de fala

Na seção **Comandos de Fala**, clique no botão **+ Adicionar Novo Comando de Fala** para adicionar um novo comando de fala à parte inferior da lista de comandos de fala existentes e, em seguida, no campo **Palavra-chave**, insira uma palavra ou frase adequada, por exemplo **Reproduzir Música**:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> Se o computador não tiver um microfone e você quiser testar o comando de fala usando a simulação no editor, poderá atribuir um KeyCode ao comando de fala, o que permitirá que você o dispare quando a chave correspondente for pressionada.

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. Adicionar e configurar o componente do Manipulador de Entrada de Fala (Script)

Na janela Hierarquia, selecione o objeto **Octa** e adicione o componente **Manipulador de Entrada de Fala (Script)** ao objeto Octa. Em seguida, desmarque a caixa de seleção **Foco É Necessário** para que o usuário não precise examinar o objeto Octa para disparar o comando de fala:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. Implementar o evento de Resposta para o comando de fala

No componente Manipulador de Entrada de Fala (Script), clique no botão **+** pequeno para adicionar um elemento de palavra-chave à lista de palavras-chaves:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

Clique no **Elemento 0** que acaba de ser criado para expandi-lo e, em seguida, na lista suspensa de **Palavra-chave**, escolha a palavra-chave **Reproduzir Música** criada anteriormente:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> As palavras-chave na lista suspensa Palavras-chaves são preenchidas com base nas palavras-chaves definidas na lista Comandos de Fala no Perfil de Comandos de Fala.

Crie um evento **Response ()** , configure o objeto **Octa** para receber o evento, defina **AudioSource.PlayOneShot** como a ação a ser disparada e atribua um clipe de áudio adequado ao campo **Clipe de Áudio**, por exemplo, o clipe de áudio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> Para obter um lembrete sobre como implementar eventos e atribuir um clipe de áudio, você pode consultar as instruções para [Implementar o evento On Touch Started](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event).

## <a name="the-pan-gesture"></a>O gesto de panorâmica

O gesto de panorâmica é útil para rolagem usando o dedo ou a mão para rolar pelo conteúdo. Neste exemplo, você aprenderá primeiro a rolar uma interface do usuário 2D e, em seguida, expandir isso para poder rolar em uma coleção de objetos 3D.

As principais etapas que você seguirá para conseguir isso são:

1. Criar um objeto Quad que pode ser usado para panorâmica
2. Adicionar o componente Tocável de Interação Próxima (Script)
3. Adicionar o componente de Zoom e Panorâmica da Interação Manual (Script)
4. Adicionar conteúdo 2D a ser rolado
5. Adicionar conteúdo 3D a ser rolado
6. Adicionar o componente Mover com Panorâmica (Script)

> [!NOTE]
> O componente Mover com Panorâmica (Script) não faz parte do MRTK. Ele foi fornecido com os ativos deste tutorial.

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. Criar um objeto Quad que pode ser usado para panorâmica

Na janela Hierarquia, clique com o botão direito do mouse em uma área vazia e selecione **Objeto 3D** > **Quad** para adicionar um quad à sua cena. Dê a ele um nome adequado, por exemplo, **PanGesture** e posicione-o em uma localização adequada, por exemplo, X = 0, Y = -0,2, Z = 2.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> Para um lembrete sobre como adicionar primitivos do Unity, como um quad 3D, à sua cena, veja as instruções para [Adicionar um cubo à cena](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene).

Assim como acontece com qualquer outra interação, o gesto de panorâmica também requer um colisor. Por padrão, um Quad tem um colisor de malha. No entanto, o colisor de malha não é ideal, porque ele é extremamente fino e difícil de selecionar. Para facilitar para o usuário interagir com o colisor, substituiremos o colisor de malha por um colisor de caixa.

Com o objeto PanGesture ainda selecionado, clique no ícone **Configurações** do componente **Colisor de Malha** e selecione **Remover Componente** para remover o colisor de malha:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

Na janela Inspetor, use o botão **Adicionar Componente** para adicionar um **Colisor de Caixa**, então altere o **Tamanho** Z do Colisor de Caixa para 0,15 para aumentar a espessura do colisor da caixa:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. Adicionar o componente Tocável de Interação Próxima (Script)

Com o objeto **PanGesture** ainda selecionado, adicione o componente **Tocável de Interação Próxima (Script)** ao objeto PanGesture e clique nos botões **Corrigir Limites** e **Corrigir Centro** para atualizar as propriedades Limites e Centro Local do Tocável de Interação Próxima (Script) para que correspondam ao BoxCollider:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. Adicionar o componente de Zoom e Panorâmica da Interação Manual (Script)

Com o objeto **PanGesture** ainda selecionado, adicione o componente **Panorâmica e Zoom da Interação da Mão (Script)** ao objeto PanGesture e marque a caixa de seleção **Bloqueio Horizontal** para permitir somente a rolagem vertical:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. Adicionar conteúdo 2D a ser rolado

No painel Projeto, pesquise o material **PanContent** e, em seguida, clique e arraste-o para a propriedade de Elemento 0 do **Material** do Renderizador de Malha do objeto **PanGesture**:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

Na janela Inspetor, expanda o componente de material **PanContent** que acaba de ser adicionado e, em seguida, altere seu valor Y de **Blocos** para 0,5 para que corresponda ao valor X e os blocos apareçam quadrados:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

Se agora você entrar no modo de Jogo, poderá testar a rolagem do conteúdo 2D usando o gesto de panorâmica na simulação no editor:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. Adicionar conteúdo 3D a ser rolado

Na janela Hierarquia, **crie quatro cubos** como objetos filho do objeto **PanGesture** e defina sua **Escala** de Transformação para X = 0,15, Y = 0,15, Z = 0,15:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

Para espaçar os cubos uniformemente e economizar algum tempo, adicione o componente **Coleção de Objetos de Grade (Script)** ao objeto pai dos cubos, ou seja, o objeto **PanGesture**, e configure a Coleção de Objetos de grade (Script) da seguinte maneira:

* Altere **Número de Linhas** para 1 para alinhar todos os cubos em uma só linha
* Altere **Largura da Célula** para 0,25 para espaçar os cubos dentro da linha

Em seguida, clique no botão **Atualizar Coleção** para aplicar a nova configuração:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. Adicionar o componente Mover com Panorâmica (Script)

Na janela Hierarquia, selecione todos os **Objetos filho de cubo**, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Mover Com Panorâmica (Script)** a todos os cubos:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> Para um lembrete de como selecionar vários objetos na janela Hierarquia, você pode consultar as instruções para [Adicionar o componente Manipulador de Manipulação (Script) a todos os objetos](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects).

Com todos os cubos ainda selecionados, clique e arraste o objeto **PanGesture** para o campo **Fonte de Entrada Panorâmica**:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> O componente Mover com Pan (Script) em cada cubo escuta o evento de Panorâmica Atualizada enviado pelo componente HandInteractionPanZoom (Script) no objeto PanGesture, que você atribuiu como a Fonte de Entrada Panorâmica na etapa acima e atualiza a posição de cada cubo de acordo.

Na janela Hierarquia, selecione o objeto **PanGesture** e, em seguida, no inspetor, **desmarque** caixa de seleção **Renderizador de Malha** para desabilitar o componente Renderizador de Malha:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

Se agora você entrar no modo de Jogo, poderá testar a rolagem do conteúdo 3D usando o gesto de panorâmica na simulação no editor:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>Acompanhamento Ocular

Nesta seção, você vai explorar como habilitar o Acompanhamento Ocular em seu projeto. Para este exemplo, você implementará a funcionalidade para fazer cada objeto na 3DObjectCollection girar lentamente enquanto estiver sendo olhado pelo usuário, bem como disparará um efeito de blip quando o objeto que está sendo observado for selecionado por toque no ar ou comando de fala.

As principais etapas que você seguirá para conseguir isso são:

1. Adicione o componente de Destino de Acompanhamento Ocular (Script) a todos os objetos de destino
2. Adicione o componente de Demonstração do Tutorial de Acompanhamento Ocular (Script) a todos os objetos de destino
3. Implementar o evento Ao Olhar para o Alvo
4. Implementar o evento Quando Selecionado
5. Habilitar o Acompanhamento Ocular simulado para simulações no editor
6. Habilitar Entrada de Olhar nas funcionalidades do aplicativo do projeto do Visual Studio

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. Adicione o componente de Destino de Acompanhamento Ocular (Script) a todos os objetos de destino

Na janela Hierarquia, expanda o objeto **3DObjectCollection** e selecione todos os **objetos filho** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Alvo de Acompanhamento Ocular (Script)** a todos os objetos filho:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

Com todos os **objetos filho** ainda selecionados, configure o componente **Alvo do Acompanhamento Ocular (Script)** da seguinte maneira:

* Altere **Selecionar Ação** para **Selecionar** para definir a ação de toque no ar para esse objeto como Selecionar
* Expanda **Seleção de Voz** e defina o **Tamanho** da lista de comandos de voz como 1 e, em seguida, na nova lista de elementos exibida, altere **Elemento 0** para **Selecionar** para definir a ação de comando de fala para esse objeto como Selecionar

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. Adicione o componente de Demonstração do Tutorial de Acompanhamento Ocular (Script) a todos os objetos de destino

Com todos os **objetos filho** ainda selecionados, use o botão **Adicionar Componente** para adicionar o componente **Demonstração do Tutorial de Acompanhamento Ocular (Script)** a todos os objetos filho:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> O componente Alvo de Acompanhamento Ocular (Script) não faz parte do MRTK. Ele foi fornecido com os ativos deste tutorial.

### <a name="3-implement-the-while-looking-at-target-event"></a>3. Implementar o evento Ao Olhar para o Alvo

Na janela Hierarquia, selecione o objeto **Queijo**, crie um evento **Ao Olhar para o Alvo ()** , configure o objeto **Queijo** para receber o evento e defina **EyeTrackingTutorialDemo.RotateTarget** como a ação a ser disparada:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

**Repita** para cada um dos objetos filho na 3DObjectCollection.

> [!TIP]
> Para obter um lembrete sobre como implementar eventos, você pode consultar as instruções de [Gestos de acompanhamento da mão e botões interativos](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).

### <a name="4-implement-the-on-selected-event"></a>4. Implementar o evento Quando Selecionado

Na janela Hierarquia, selecione o objeto **Queijo**, crie um evento **No Selecionado ()** , configure o objeto **Queijo** para receber o evento e defina **EyeTrackingTutorialDemo.BlipTarget** como a ação a ser disparada:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

**Repita** para cada um dos objetos filho na 3DObjectCollection.

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. Habilitar o Acompanhamento Ocular simulado para simulações no editor

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, em seguida, na janela Inspetor, selecione a guia **Entrada**, expanda a seção **Provedores de Dados de Entrada** e a seção **Serviço de Simulação de Entrada** e clone o **DefaultMixedRealityInputSimulationProfile** para substituí-lo pelo seu **Perfil de Simulação de Entrada** personalizável:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> Para obter um lembrete de como clonar perfis MRTK, você pode consultar as instruções de [Como configurar os perfis do Mixed Reality Toolkit](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).

Na seção **Simulação de Olho**, marque a caixa de seleção **Simular a Posição do Olho** para habilitar a simulação de acompanhamento ocular:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

Se agora você entrar no modo de Jogo, poderá testar os efeitos de rotação e blip que você implementou ajustando a exibição para que o cursor atinja um dos objetos e o comando de interação manual ou de fala para selecionar o objeto:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> Se você não tiver usado o DefaultHoloLens2ConfigurationProfile para clonar seu perfil de configuração MRTK personalizável, conforme orientado nas instruções para [Configurar o Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit), o acompanhamento ocular poderá não estar habilitado em seu projeto e precisará ser habilitado. Para isso, você pode consultar as instruções de [Introdução ao acompanhamento ocular no MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html).

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. Habilitar Entrada de Olhar nas funcionalidades do aplicativo do projeto do Visual Studio

Antes de criar e implantar seu aplicativo do Visual Studio em seu dispositivo, a Entrada de Olhar deve ser habilitada nos recursos de aplicativo do projeto. Para isso, você pode seguir as instruções em [Testar seu aplicativo Unity em um HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2).

## <a name="congratulations"></a>Parabéns

Você adicionou com êxito as funcionalidades de acompanhamento ocular ao aplicativo. Essas ações são apenas o começo de um mundo de possibilidades com o acompanhamento ocular. Neste tutorial, você também aprendeu sobre outros recursos de entrada avançados, como comandos de voz e gestos de panorâmica.

[Próxima lição: 7. Criar um aplicativo de exemplo do módulo Lunar](mrlearning-base-ch6.md)
