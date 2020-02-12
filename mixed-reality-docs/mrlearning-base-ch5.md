---
title: Tutoriais de introdução-6. Explorando opções de entrada avançadas
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 18bcbc95746a2e66b88d83f279603aa7f171bbcb
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129567"
---
# <a name="6-exploring-advanced-input-options"></a>6. explorando opções de entrada avançadas

Neste tutorial, você vai explorar algumas opções de entrada avançadas para o HoloLens 2, incluindo o uso de comandos de voz, gesto de panorâmica e acompanhamento de olho.

## <a name="objectives"></a>Objetivos

* Disparar eventos usando comandos de voz e palavras-chave
* Usar mãos controladas para deslocar texturas e objetos 3D com mãos controladas
* Aproveitar os recursos de acompanhamento de olho do HoloLens 2 para selecionar objetos

## <a name="enabling-voice-commands"></a>Habilitando comandos de voz
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

Nesta seção, você implementará um comando de fala para permitir que o usuário reproduza um som no objeto Octa. Para isso, você criará um novo comando de fala e, em seguida, configurará o evento para que ele dispare a ação desejada quando a palavra-chave do comando de fala for falada.

As principais etapas que você seguirá para conseguir isso são:

1. Clonar o perfil do sistema de entrada padrão
2. Clonar o perfil de comandos de fala padrão
3. Criar um novo comando de fala
4. Adicionar e configurar o componente do manipulador de entrada de fala (script)
5. Implementar o evento de resposta para o comando de fala

### <a name="1-clone-the-default-input-system-profile"></a>1. clonar o perfil do sistema de entrada padrão

Na janela hierarquia, selecione o objeto **MixedRealityToolkit** e, em seguida, na janela Inspetor, selecione a guia **entrada** e clone o **DefaultHoloLens2InputSystemProfile** para substituí-lo pelo seu próprio **perfil de sistema de entrada**personalizável:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> Para obter um lembrete sobre como clonar perfis MRTK, você pode consultar as instruções [como configurar os perfis do kit de ferramentas de realidade misturada](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .

### <a name="2-clone-the-default-speech-commands-profile"></a>2. clonar o perfil de comandos de fala padrão

Expanda a seção **fala** e clone o **DefaultMixedRealitySpeechCommandsProfile** para substituí-lo por seu próprio **perfil de comandos de fala**personalizável:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. criar um novo comando de fala

Na seção **comandos de fala** , clique no botão **+ Adicionar um novo comando de fala** para adicionar um novo comando de fala à parte inferior da lista de comandos de fala existentes. em seguida, no campo **palavra-chave** , insira uma palavra ou frase adequada, por exemplo, **reproduzir música**:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> Se o computador não tiver um microfone e você quiser testar o comando de fala usando a simulação no editor, você poderá atribuir um código de chave ao comando de fala, o que permitirá que você o dispare quando a chave correspondente for pressionada.

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. adicionar e configurar o componente do manipulador de entrada de fala (script)

Na janela hierarquia, selecione o objeto **Octa** e adicione o componente **manipulador de entrada de fala (script)** ao objeto Octa. Em seguida, desmarque a caixa de seleção **é o foco necessário** para que o usuário não precise examinar o objeto Octa para disparar o comando de fala:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. implementar o evento de resposta para o comando de fala

No componente manipulador de entrada de fala (script), clique no pequeno **+** botão para adicionar uma palavra-chave e, em seguida, na lista suspensa de **palavras-chave** , escolha a palavra-chave **reproduzir música** criada anteriormente:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

> [!NOTE]
> As palavras-chave no menu suspenso de palavras-chaves são preenchidas com base nas palavras-chaves definidas na lista de comandos de fala no perfil de comandos de fala.

Crie um novo evento **Response ()** , configure o objeto **Octa** para receber o evento, defina **audioname. PlayOneShot** como a ação a ser disparada e atribua um clipe de áudio adequado ao campo de **clipe de áudio** , por exemplo, o clipe de áudio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!TIP]
> Para obter um lembrete sobre como implementar eventos e atribuir um clipe de áudio, você pode consultar as instruções [implementar o evento on Touch Started](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) .

## <a name="the-pan-gesture"></a>O gesto de panorâmica

O gesto de panorâmica é útil para rolar usando o dedo ou a mão para rolar pelo conteúdo. Neste exemplo, você aprenderá primeiro a rolar uma interface do usuário 2D e, em seguida, expandir isso para poder percorrer uma coleção de objetos 3D.

As principais etapas que você seguirá para conseguir isso são:

1. Criar um objeto Quad que pode ser usado para panorâmica
2. Adicionar o componente Near-Touch (script) de interação próxima
3. Adicionar o componente de zoom (script) de panorâmica de interação à mão
4. Adicionar conteúdo 2D a ser rolado
5. Adicionar conteúdo 3D a ser rolado
6. Adicionar a movimentação com componente Pan (script)

> [!NOTE]
> O componente mover com Pan (script) não faz parte do MRTK. Ele foi fornecido com os ativos deste tutorial.

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. criar um objeto Quad que pode ser usado para movimento panorâmico

Na janela hierarquia, clique com o botão direito do mouse em uma área vazia e selecione **objeto 3d** > **quatro** para adicionar uma quádrupla à sua cena. Dê a ele um nome adequado, por exemplo, **PanGesture**, e posicione-o em um local adequado, por exemplo, X = 0, Y =-0,2, Z = 2.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> Para um lembrete sobre como adicionar primitivos do Unity, como um 3D Quad, à sua cena, você pode consultar o [Adicionar um cubo às instruções da cena](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) .

Assim como acontece com qualquer outra interação, o gesto de Pan também requer um colisor. Por padrão, um quad tem um colisor de malha. No entanto, o colisor de malha não é o ideal porque é extremamente fino. Para facilitar para o usuário interagir com o colisor, substituiremos o colisor de malha por um colisor de caixa.

Com o objeto PanGesture ainda selecionado, clique no ícone de **configurações** do componente **Colider de malha** e selecione **remover componente** para remover o colisor de malha:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

Na janela Inspetor, use o botão **Adicionar componente** para adicionar um **Colisor de caixa**e, em seguida, altere o **tamanho** de Colisor de caixa Z para 0,15 para aumentar a espessura do colisor de caixa:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. Adicionar o componente de interatividade de interação Near (script)

Com o objeto **PanGesture** ainda selecionado, adicione o componente de inclusão de **interação Near (script)** ao objeto PanGesture e, em seguida, clique nos botões **corrigir limites** e **corrigir centro** para atualizar as propriedades centro local e limites da interação próxima touchável (script) para corresponder ao BoxCollider:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. Adicionar o componente de zoom (script) de panorâmica de interação à mão

Com o objeto **PanGesture** ainda selecionado, adicione o componente de **zoom de Pan de interação à mão (script)** ao objeto PanGesture e marque a caixa de seleção **Bloquear horizontal** para permitir somente a rolagem vertical:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. adicionar conteúdo 2D a ser rolado

No painel projeto, procure o material **PanContent** e clique-e arraste-o para a propriedade **do elemento do** processador de malha do objeto **PanGesture** 0:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

Na janela Inspetor, expanda o componente **material do** **PanContent** recém-adicionado e, em seguida, altere-o para 0,5 para que ele corresponda ao valor X e os blocos apareçam no quadrado:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

Se agora você entrar no modo de jogo, poderá testar a rolagem do conteúdo 2D usando o gesto de Pan na simulação de editor:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. adicionar conteúdo 3D a ser rolado

Na janela hierarquia, **Crie quatro cubos** como objetos filho do **PanContent** e defina a **escala** de transformação como X = 0,15, Y = 0,15, Z = 0,15:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

Para espaçar os cubos uniformemente e economizar algum tempo, adicione o componente de coleção de objetos de grade (script) ao objeto pai dos cubos, ou seja, o objeto PanGesture e configure a coleção de objetos de grade (script) da seguinte maneira:

* Alterar o **número de linhas** para 1 para que todos os cubos sejam alinhados em uma única linha
* Alterar a **largura da célula** para 0,25 para espaçar os cubos dentro da linha

Em seguida, clique no botão **Atualizar coleção** para aplicar a nova configuração:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. adicionar a movimentação com o componente Pan (script)

Na janela hierarquia, selecione todos os **objetos filho do cubo**e, em seguida, na janela Inspetor, use o botão **Adicionar componente** para adicionar o componente **mover com Pan (script)** a todos os cubos:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> Para obter um lembrete sobre como selecionar vários objetos na janela hierarquia, tou pode referir-se ao [componente adicionar o manipulador de manipulação (script) a todas as instruções de objetos](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) .

Com todos os cubos ainda selecionados, clique e arraste o objeto **PanGesture** para o campo **fonte de entrada de Pan** :

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> O componente mover com Pan (script) em cada cubo escuta o evento de panorâmica atualizada enviado pelo componente HandInteractionPanZoom (script) no objeto PanGesture, que você atribuiu como a fonte de entrada Pan na etapa acima e atualiza a posição de cada cubo adequados.

Na janela hierarquia, selecione o objeto **PanGesture** e, em seguida, no Inspetor, **desmarque** a caixa de seleção **processador de malha** para desabilitar o componente de processador de malha:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

Se agora você entrar no modo de jogo, poderá testar a rolagem do conteúdo 3D usando o gesto de Pan na simulação de editor:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>Acompanhamento Ocular

Nesta seção, você vai explorar como habilitar o controle de olho em seu projeto. Para este exemplo, você implementará a funcionalidade para tornar cada objeto na rotação 3DObjectCollection lentamente durante a pesquisa pelo olhar de olho do usuário, bem como disparará um efeito de blip quando o objeto que está sendo examinado for selecionado pelo toque de ar ou comando de fala.

As principais etapas que você seguirá para conseguir isso são:

1. Adicionar o componente de destino de acompanhamento de olho (script) a todos os objetos de destino
2. Adicionar o componente de demonstração do tutorial de acompanhamento de olho (script) a todos os objetos de destino
3. Implementar o ao examinar o evento de destino
4. Implementar o evento on Selected
5. Habilitar o controle de olho simulado para simulações no editor
6. Habilitar a entrada olhar nos recursos de aplicativo do projeto do Visual Studio

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. Adicionar o componente de destino de acompanhamento de olho (script) a todos os objetos de destino

Na janela hierarquia, expanda o objeto **3DObjectCollection** e selecione todos os **objetos filho**e, na janela Inspetor, use o botão **Adicionar componente** para adicionar o componente de **destino de acompanhamento de olho (script)** a todos os objetos filho:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

Com todos os **objetos filho** ainda selecionados, configure o componente de **destino de acompanhamento de olho (script)** da seguinte maneira:

* Altere a **ação Select** a **selecionar**para definir a ação de toque de ar para este objeto como SELECT
* Expandir **voz selecione** e defina o **tamanho** da lista de comandos de voz como 1 e, em seguida, na nova lista de elementos exibida, altere o **elemento 0** para **selecionar**, para definir a ação de comando de fala para esse objeto como SELECT

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. Adicionar o componente de demonstração do tutorial de acompanhamento de olho (script) a todos os objetos de destino

Com todos os **objetos filho** ainda selecionados, use o botão **Adicionar componente** para adicionar o componente **demonstração do tutorial de acompanhamento de olho (script)** a todos os objetos filho:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> O componente de destino de acompanhamento de olho (script) não faz parte do MRTK. Ele foi fornecido com os ativos deste tutorial.

### <a name="3-implement-the-while-looking-at-target-event"></a>3. implementar o ao examinar o evento de destino

Na janela hierarquia, selecione o objeto **queijo** e crie um novo **ao examinar o evento Target ()** , configure o objeto **queijo** para receber o evento e defina **EyeTrackingTutorialDemo. RotateTarget** como a ação a ser disparada:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

**Repita** para cada um dos objetos filho no 3DObjectCollection.

> [!TIP]
> Para obter um lembrete sobre como implementar eventos, consulte as instruções [gestos de acompanhamento de mão e botões](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) que podem interagir.

### <a name="4-implement-the-on-selected-event"></a>4. implementar o no evento selecionado

Na janela hierarquia, selecione o objeto **queijo** e crie um novo no evento **selecionado ()** , configure o objeto **queijo** para receber o evento e defina **EyeTrackingTutorialDemo. RotateTarget** como a ação a ser disparada:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

**Repita** para cada um dos objetos filho no 3DObjectCollection.

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. habilitar o controle de olho simulado para simulações no editor

Na janela hierarquia, selecione o objeto **MixedRealityToolkit** e, em seguida, na janela Inspetor, selecione a guia **entrada** , expanda a seção **provedores de dados de entrada** e, em seguida, a seção serviço de simulação de **entrada** e clone o **DefaultMixedRealityInputSimulationProfile** para substituí-lo pelo seu próprio perfil de **simulação de entrada**personalizável:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> Para obter um lembrete sobre como clonar perfis MRTK, você pode consultar as instruções [como configurar os perfis do kit de ferramentas de realidade misturada](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .

Na seção **simulação de olho** , marque a caixa de seleção **simular posição de olho** para habilitar a simulação de acompanhamento ocular:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

Se agora você inserir o modo de jogo, poderá testar os efeitos de rotação e blip que você implementou ajustando a exibição para que o cursor atinja um dos objetos e o comando de interação manual ou de fala para selecionar o objeto:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> Se você não usou o DefaultHoloLens2ConfigurationProfile para clonar seu perfil de configuração MRTK personalizável, conforme instruído nas instruções de [Configurar o kit de ferramentas da realidade misturada, o](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) controle de olhos pode não ser habilitado em seu projeto e precisará ser ativado. Para isso, você pode consultar as instruções de [introdução ao acompanhamento de olho em MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) .

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. habilitar a entrada olhar nos recursos de aplicativo do projeto do Visual Studio

Antes de criar e implantar seu aplicativo do Visual Studio em seu dispositivo, a entrada olhar deve ser habilitada nos recursos de aplicativo do projeto. Para isso, você pode seguir as instruções [testando seu aplicativo Unity em um HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) .

## <a name="congratulations"></a>Parabéns

Você adicionou com êxito os recursos básicos de acompanhamento de olho ao seu aplicativo. Essas ações são apenas o começo de um mundo de possibilidades com o acompanhamento ocular. Neste tutorial, você também aprendeu sobre outros recursos de entrada avançados, como comandos de voz e gestos de panorâmica.

[Próxima lição: 7. criando um aplicativo de exemplo de módulo lunar](mrlearning-base-ch6.md)
