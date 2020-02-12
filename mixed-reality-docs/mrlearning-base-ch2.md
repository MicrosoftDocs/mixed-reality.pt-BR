---
title: Tutoriais de introdução-3. Criando interface do usuário e Configurando o kit de ferramentas de realidade mista
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 067832a130f130ffbaa8d455007b8e77e1b13671
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130437"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. criando a interface do usuário e Configurando o kit de ferramentas de realidade mista
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

No tutorial anterior, você aprendeu sobre alguns dos recursos que o MRTK (Kit de ferramentas de realidade misturada) tem a oferecer ao iniciar seu primeiro aplicativo para o HoloLens 2. Neste tutorial, você aprenderá a criar e organizar botões juntamente com os painéis de texto da interface do usuário e usar a interação padrão (toque) para interagir com cada botão. Você também explorará a adição de ações e efeitos simples, como alterar o tamanho, o som e a cor de objetos. Este módulo apresentará conceitos básicos sobre a modificação de perfis MRTK, começando pela desativação da visualização de malha de [mapeamento espacial](spatial-mapping.md) .

## <a name="objectives"></a>Objetivos

* Personalizar e configurar perfis do Kit de Ferramentas de Realidade Misturada
* Interagir com hologramas usando elementos e botões de interface do usuário
* Interações e entrada de acompanhamento de mão básicas

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Como configurar os perfis do kit de ferramentas de realidade misturada (alterar a opção de exibição de conscientização espacial)
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

Nesta seção, você aprenderá a personalizar e configurar os perfis de MRTK padrão.

Este exemplo específico mostrará como ocultar a malha de conscientização espacial alterando as configurações do observador de malha espacial. No entanto, você pode seguir esses mesmos princípios para personalizar qualquer configuração ou valor nos perfis MRTK.

As principais etapas que você seguirá para ocultar a malha de conscientização espacial são:

1. Clonar o perfil de configuração padrão
2. Habilitar o sistema de conscientização espacial
3. Clonar o perfil do sistema de reconhecimento espacial padrão
4. Clonar o perfil de observador de malha de conscientização espacial padrão
5. Alterar a visibilidade da malha de conscientização espacial

> [!NOTE]
> Por padrão, os perfis do MRTK não são editáveis. Esses são modelos de perfil padrão que você precisa clonar antes que eles possam ser editados. Há várias camadas aninhadas de perfis. Portanto, é comum clonar e editar vários perfis ao configurar uma ou mais configurações.

### <a name="1-clone-the-default-configuration-profile"></a>1. clonar o perfil de configuração padrão

> [!NOTE]
> O perfil de configuração é o perfil de nível superior. Consequentemente, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.

Com o objeto **MixedRealityToolkit** selecionado na janela hierarquia, na janela Inspetor, clique no botão **copiar & Personalizar** para abrir a janela clonar perfil:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

Na janela clonar perfil, clique no botão **clonar** para criar uma cópia editável do **DefaultHololens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

Agora, o perfil de configuração recém-criado é atribuído como o perfil de configuração para sua cena:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

No menu do Unity, selecione **arquivo** > **salvar** para salvar sua cena.

> [!TIP]
> Lembre-se de salvar seu trabalho em todo o tutorial.

### <a name="2-enable-the-spatial-awareness-system"></a>2. habilitar o sistema de conscientização espacial

Com o objeto **MixedRealityToolkit** ainda selecionado na janela hierarquia, na janela Inspetor, selecione a guia **reconhecimento espacial** e marque a caixa de seleção **habilitar sistema de conscientização espacial** :

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. clonar o perfil do sistema de reconhecimento espacial padrão

Na guia **reconhecimento espacial** , clique no botão **clonar** para abrir a janela clonar perfil:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

Na janela clonar perfil, clique no botão **clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

O perfil do sistema de conscientização espacial recém-criado agora é atribuído automaticamente ao seu perfil de configuração:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. clonar o perfil de observador de malha de conscientização espacial padrão

Com a guia **conscientização espacial** ainda selecionada, expanda a seção **observador de malha espacial do Windows Mixed Realm** e clique no botão **clonar** para abrir a janela clonar perfil:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

Na janela clonar perfil, clique no botão **clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

O perfil de observador de malha de conscientização espacial recém-criado agora é automaticamente atribuído ao seu perfil do sistema de conscientização espacial:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. alterar a visibilidade da malha de conscientização espacial

Nas **configurações de observador de malha espacial**, altere a **opção de exibição** para **oclusão** para tornar a malha de mapeamento espacial invisível ao mesmo tempo em funcionamento:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional. Por exemplo, todos os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.

Você acabou de aprender como modificar uma configuração do perfil do MRTK. Como você pode ver, para personalizar as configurações de MRTK, primeiro você precisa criar cópias dos perfis padrão. Como os perfis padrão não são editáveis, você sempre os terá como referência se desejar reverter para as configurações padrão. Para saber mais sobre os perfis de MRTK e sua arquitetura, você pode visitar o [Guia de configuração do perfil do reality Toolkit misto](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) no [portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>Gestos de acompanhamento de mão e botões de interação

Nesta seção, você aprenderá a usar o rastreamento manual para pressionar um botão e disparar eventos para causar uma ação quando o botão for pressionado.

Este exemplo específico mostrará como alterar a cor de um cubo quando o botão for pressionado e alterá-lo de volta para a cor original quando o botão for liberado. No entanto, você pode seguir esses mesmos princípios para criar outros eventos.

As principais etapas que você seguirá para alterar a cor do cubo são:

1. Adicionar um botão pressionável pré-fabricado à cena
2. Adicionar um cubo à cena
3. Configurar o tipo de evento InteractableOnPressReceiver
4. Configurar o cubo para receber o evento on Press
5. Definir a ação a ser disparada pelo evento on Press
6. Configurar o cubo para receber o evento on Release
7. Definir a ação a ser disparada pelo evento na versão
8. Testar o botão usando a simulação no editor

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. adicionar um botão pressionável pré-fabricado à cena

> [!TIP]
> Um <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">pré-fabricado</a> é um gameobject pré-configurado armazenado como um ativo de Unity e pode ser reutilizado em todo o seu projeto.

Na **janela do projeto**, procure **PressableButtonHoloLens2** para localizar o pré-fabricado que será usado para este exemplo:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

No resultado da **pesquisa** , selecione **PressableButtonHoloLens2** pré-fabricado e **Arraste** -o para a janela **hierarquia** para adicioná-lo à sua cena:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> Para exibir sua cena, conforme mostrado na imagem abaixo, clique duas vezes no objeto PressableButtonHoloLens2 na janela hierarquia para colocá-lo em foco e, em seguida, use a <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">cena Gizmo</a>, localizada no canto superior direito da janela cena, para ajustar o ângulo de exibição ao longo do eixo Z de avanço.

Com o objeto PressableButtonHoloLens2 ainda selecionado, na janela **Inspetor** :

* Altere sua **posição** de transformação para que ela esteja posicionada na frente da câmera, que está posicionada na origem, por exemplo, x = 0, y = 0 e z = 0,5

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> Em geral, uma unidade de posição no Unity é aproximadamente equivalente a 1 metro no mundo físico. No entanto, há exceções a isso, por exemplo, quando os objetos são filhos de objetos dimensionados.

### <a name="2-add-a-cube-to-the-scene"></a>2. adicionar um cubo à cena

Clique com o botão direito do mouse em um ponto vazio dentro da janela hierarquia e selecione o **objeto 3d** > **cubo** para adicionar um cubo à sua cena:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

Com o objeto de cubo ainda selecionado, na janela **Inspetor** :

* Altere sua **posição** de transformação para que fique perto do botão pressionável, mas não se sobreponha a ela, por exemplo, x = 0, y = 0, 4 e z = 0,5
* Altere sua **escala** de transformação para um tamanho adequado, por exemplo, x = 0, 2, y = 0, 2 e z = 0, 2

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. configurar o tipo de evento InteractableOnPressReceiver

Com o objeto PressableButtonHoloLens2 selecionado na janela hierarquia, na janela **Inspetor** **menu**de opções, selecione **recolher todos os componentes** para obter uma visão geral de todos os componentes neste objeto:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

Expanda o componente **interagir (script)** e localize e expanda a seção **eventos** > **receptores** :

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

Para o tipo de receptor de evento **InteractableOnPressReceiver**, altere o **filtro de interação** para **perto e longe**:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> O tipo de receptor de evento chamado InteractableOnPressReceiver permite que o botão responda a um evento pressionado quando uma mão controlada pressiona o botão.

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. configurar o cubo para receber o evento on Press

Na janela hierarquia, **clique e arraste** o **cubo** para o campo objeto **Propriedades de evento** do evento **on Press ()** para atribuir o cubo como um receptor do evento on Press ():

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. definir a ação a ser disparada pelo evento on Press

Clique no menu suspenso ação, atualmente atribuído a **nenhuma função**e selecione MeshRenderer ** > material material para** definir a propriedade material do cubo a ser alterada quando o evento on Press () for disparado:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

Clique no ícone de **círculo** pequeno ao lado do campo material, preenchido atualmente com **nenhum (material)** , para abrir a janela Selecionar material:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

Na janela Selecionar material, **pesquise** **MRTK_Standard** e selecione um material adequado, por exemplo, **MRTK_Standard_Cyan** para que a cor do cubo seja alterada para ciano quando o botão for pressionado:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. configurar o cubo para receber o evento on Release

**Repetir** Etapa 4 do evento on Release para atribuir o cubo como um destinatário do evento on Release ().

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. definir a ação a ser disparada pelo evento na versão

**Repetir** Etapa 5 para o evento na versão, mas escolha o material de **MRTK_Standard_LightGray** para que a cor do cubo retorne para sua cor cinza clara original quando o botão for liberado:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. testar o botão usando a simulação no editor

Pressione o botão **reproduzir** para entrar no modo de jogo e use a simulação de entrada no editor para testar seu botão recentemente configurado.

Botão não pressionado (barra de espaços + mouse de rolagem para trás):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

Botão pressionado (barra de espaços + mouse de rolagem para frente):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> Para saber como usar a simulação de entrada no editor, você pode consultar o [usando a simulação de entrada da edição do editor para testar um](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guia de cena no [portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Criando um painel de botões usando a coleção de objetos de grade do MRTK

Nesta seção, você aprenderá a alinhar automaticamente vários botões em uma interface de usuário clara usando a ferramenta de coleção de objetos de grade do MRTK.

Este exemplo específico mostrará como criar um painel com cinco botões alinhados horizontalmente. No entanto, você pode seguir esses mesmos princípios para criar outros layouts.

As principais etapas que você seguirá para conseguir isso são:

1. Pai os objetos Button para um objeto pai
2. Adicionar e configurar o componente de coleção de objetos de grade (script)
3. Testar os botões usando a simulação no editor

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. pai os objetos Button para um objeto pai

Clique com o botão direito do mouse em um ponto vazio dentro da janela hierarquia e selecione **criar vazio**:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

Clique com o botão direito do mouse no objeto recém-criado, selecione **renomear**e dê a ele um nome adequado, por exemplo, **buttoncollection**:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

Selecione o objeto **PressableButtonHoloLens2** e **Arraste** -o para cima do objeto **buttoncollection** para torná-lo um filho do objeto buttoncollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

Clique com o botão direito do mouse no objeto **PressableButtonHoloLens2** e selecione **duplicar** para criar uma cópia dele:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

**Repita** esta etapa quatro vezes até que você tenha um total de cinco objetos PressableButtonHoloLens2.

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. adicionar e configurar o componente de coleção de objetos de grade (script)

Com o objeto Buttoncollection selecionado na janela hierarquia, na janela Inspetor, clique no botão **Adicionar componente** , procure e selecione coleção de objetos de **grade** para adicionar um componente Script (coleção de objetos de grade) ao objeto buttoncollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

Configure a coleção de objetos de grade (script) da seguinte maneira:

* Alterar o **número de linhas** para 1 para que todos os botões sejam alinhados em uma única linha
* Alterar a **largura da célula** para 0, 5 para espaçar os botões dentro da linha

Em seguida, clique no botão **Atualizar coleção** para aplicar a nova configuração:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> As alterações de configuração que você acabou de aplicar representam as alterações mínimas necessárias para atingir o objetivo de colocar os botões em uma única linha. No entanto, em projetos futuros, dependendo de fatores como, por exemplo, a orientação dos objetos pai e filho, talvez seja necessário ajustar outras configurações, como, por exemplo, o tipo de orientação. Para saber mais sobre a coleção de objetos de grade do MRTK, você pode visitar o guia de [scripts da coleção de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) no portal de documentação do [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

Com o objeto Buttoncollection ainda selecionado na janela hierarquia, na janela Inspetor, altere a **posição** de transformação do objeto buttoncollection para que seus objetos de botão filho sejam posicionados na frente da câmera, que está posicionada na origem, por exemplo, x = 0, y = 0 e z = 0,5:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> Quando você adicionou pela primeira vez o PressableButtonHoloLens2 pré-fabricado à cena na seção [gestos de acompanhamento de mão e botões que interagem](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) acima, você o posicionou na frente da câmera. No entanto, como a coleção de objetos de grade controla sua posição de objetos filho imediatos, a posição Z dos objetos filho PressableButtonHoloLens2 foi redefinida como 0 de acordo com a distância padrão da coleção de objetos de grade do valor pai 0. Isso, e para manter a relação posicional pai/filho organizada, é por isso que mudamos a posição do objeto Buttoncollection pai em vez de configurar a distância do valor pai para mover os objetos filho PressableButtonHoloLens2 para frente.

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. testar os botões usando a simulação no editor

Pressione o botão reproduzir para entrar no modo de jogo e use a simulação de entrada no editor para testar cada um dos botões em no painel recém-criado dos botões:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> Atualmente, quando você pressiona qualquer um dos cinco botões, a cor do cubo muda para ciano. Para tornar a experiência mais interessante, use o que você apenas aprende para configurar cada botão para alterar o cubo para uma cor diferente.

## <a name="adding-text-into-your-scene"></a>Adicionando texto à sua cena

Nesta seção, você aprenderá a adicionar texto às suas experiências de realidade misturada usando o netmesh pro da Unity, que você preparou na seção [importar recursos do Textmesh pro Essentials](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) do tutorial anterior.

Neste exemplo específico, você adicionará um rótulo simples sob a coleção de botões que você criou na seção anterior.

Clique com o botão direito do mouse no objeto Buttoncollection e selecione **objeto 3d** > **Text-TextMeshPro** para criar um objeto TextMeshPro como um filho do objeto buttoncollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

Com o objeto TextMeshPro recém-criado, o texto nomeado (TMP), ainda selecionado, na janela Inspetor, altere sua posição e tamanho para que o rótulo seja posicionado de forma organizada na coleção de botões, por exemplo:

* Alterar a transformação Rect **pos Y** para-0, 425
* Altere a **largura** do Rect Transform para 0,24
* Altere a **altura** do Rect Transform para 0, 24

Em seguida, atualize o texto para refletir qual é o rótulo e escolha Propriedades de fonte para que o texto caiba no rótulo, por exemplo:

* Alterar o **texto** da malha de texto pro (script) para a coleção de botões
* Altere o **estilo de fonte** pro (script) de malha de texto para negrito
* Altere o **tamanho da fonte** do pro (script de malha de texto) para 0,2
* Alterar o **alinhamento** pro (script) da malha de texto para o centro e o meio

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a clonar, personalizar e definir uma configuração de perfil MRTK. Você também aprendeu como interagir com botões para disparar eventos usando mãos controladas no HoloLens 2. Por fim, você aprendeu a criar uma interface de interface do usuário simples usando o componente de coleção de objetos de grade do MRTK e a malha de texto do Unity pro.

[Próximo tutorial: 4. colocando conteúdo dinâmico e usando os solveres](mrlearning-base-ch3.md)
