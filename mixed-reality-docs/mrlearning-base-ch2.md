---
title: Tutoriais de introdução – 3. Criar a interface do usuário e configurar o Mixed Reality Toolkit
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376133"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. Criar a interface do usuário e configurar o Mixed Reality Toolkit
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

No tutorial anterior, você aprendeu sobre algumas das funcionalidades que o MRTK (Mixed Reality Toolkit) tem a oferecer, iniciando seu primeiro aplicativo para o HoloLens 2. Neste tutorial, você aprenderá como criar e organizar os botões, juntamente com os painéis de texto de interface do usuário e usar a interação padrão (toque) para interagir com cada botão. Você também explorará a adição de ações e efeitos simples, como alterar o tamanho, o som e a cor de objetos. Este módulo apresenta os conceitos básicos sobre como modificar perfis do MRTK, começando com a desativação da visualização da malha de [mapeamento espacial](spatial-mapping.md).

## <a name="objectives"></a>Objetivos

* Personalizar e configurar perfis do Kit de Ferramentas de Realidade Misturada
* Interagir com hologramas usando os botões e elementos de interface do usuário
* Interações e entrada de acompanhamento de mão básicas

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Como configurar os perfis do Mixed Reality Toolkit (alterar a opção de exibição de reconhecimento espacial)
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

Nesta seção, você aprenderá a personalizar e configurar os perfis do MRTK padrão.

Este exemplo específico mostrará como ocultar a malha de reconhecimento espacial alterando as configurações do Observador de Malha Espacial. No entanto, você pode seguir esses mesmos princípios para personalizar qualquer configuração ou valor nos perfis do MRTK.

As principais etapas que você seguirá para ocultar a malha de reconhecimento espacial são:

1. Clonar o perfil de configuração padrão
2. Habilitar o Sistema de Reconhecimento Espacial
3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão
4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão
5. Altere a visibilidade da malha de reconhecimento espacial

> [!NOTE]
> Por padrão, os perfis do MRTK não são editáveis. Esses são modelos de perfil padrão que você precisa clonar antes que eles possam ser editados. Há várias camadas aninhadas de perfis. Portanto, é comum clonar e editar vários perfis ao definir uma ou mais configurações.

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonar o perfil de configuração padrão

> [!NOTE]
> O perfil de configuração é o perfil de nível superior. Assim, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.

Com o objeto **MixedRealityToolkit** selecionado na janela Hierarquia, altere o **Perfil de Configuração** do Mixed Reality Toolkit na janela Inspetor para **DefaultHoloLens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique no botão **Copiar e Personalizar** para abrir a janela Clonar Perfil:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

Na janela Clonar Perfil, clique no botão **Clonar** para criar uma cópia editável do **DefaultHololens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

Agora, o Perfil de Configuração recém-criado é atribuído como o Perfil de Configuração para sua cena:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

No menu do Unity, selecione **Arquivo** > **Salvar** para salvar sua cena.

> [!TIP]
> Lembre-se de salvar seu trabalho em todo o tutorial.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Habilitar o Sistema de Reconhecimento Espacial

Com o objeto **MixedRealityToolkit** ainda selecionado na janela Hierarquia, na janela Inspetor, selecione a guia **Reconhecimento Espacial** e marque a caixa de seleção **Habilitar o Sistema de Reconhecimento Espacial**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão

Na guia **Reconhecimento Espacial**, clique no botão **Clonar** para abrir a janela Clonar Perfil:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

Na janela Clonar Perfil, clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

O Perfil do Sistema de Reconhecimento Espacial recém-criado agora é atribuído automaticamente ao seu Perfil de Configuração:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão

Com a guia **Reconhecimento Espacial** ainda selecionada, expanda a seção **Observador de Malha Espacial do Windows Mixed Reality** e clique no botão **Clonar** para abrir a janela Clonar Perfil:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

Na janela Clonar Perfil, clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

O Perfil de Observador de Malha de Reconhecimento Espacial recém-criado agora é automaticamente atribuído ao seu Perfil do Sistema de Reconhecimento Espacial:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Altere a visibilidade da malha de reconhecimento espacial

Em **Configurações do Observador de Malha Espacial**, altere a **Opção de Exibição** para **Oclusão** para tornar a malha de mapeamento espacial invisível, mas ainda funcional:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional. Por exemplo, os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.

Você acabou de aprender como modificar uma configuração do perfil do MRTK. Como você pode ver, para personalizar as configurações de MRTK, primeiro é necessário criar cópias dos perfis padrão. Como os perfis padrão não são editáveis, você sempre os terá como referência se quiser reverter para as configurações padrão. Para saber mais sobre os perfis do MRTK e sua arquitetura, você pode visitar o [Guia de configuração do perfil do Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>Botões interativos e gestos de acompanhamento da mão

Nesta seção, você aprenderá a usar o acompanhamento de mão para pressionar um botão e disparar eventos para provocar uma ação quando o botão for pressionado.

Este exemplo específico mostrará como alterar a cor de um cubo quando o botão for pressionado e alterá-la de volta para a cor original quando o botão for liberado. No entanto, você pode seguir esses mesmos princípios para criar outros eventos.

As principais etapas que você seguirá para alterar a cor do cubo são:

1. Adicionar um botão pressionável pré-fabricado à cena
2. Adicione um cubo à cena
3. Configurar o tipo de evento InteractableOnPressReceiver
4. Configurar o cubo para receber o evento On Press
5. Definir a ação a ser disparada pelo evento On Press
6. Configurar o cubo para receber o evento Ao Liberar
7. Definir a ação a ser disparada pelo evento Ao Liberar
8. Testar o botão usando a simulação no editor

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. Adicionar um botão pressionável pré-fabricado à cena

> [!TIP]
> Um <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">pré-fabricado</a> é um GameObject pré-configurado armazenado como um Ativo Unitário e pode ser reutilizado em todo o seu projeto.

Na **janela Projeto**, pesquise **PressableButtonHoloLens2** para localizar o pré-fabricado que será usado para este exemplo:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

No resultado de **Pesquisar**, selecione o pré-fabricado **PressableButtonHoloLens2** e **arraste-o** para a janela **Hierarquia** para adicioná-la à sua cena:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> Para exibir sua cena conforme mostrado na imagem abaixo, clique duas vezes no objeto PressableButtonHoloLens2 na janela Hierarquia para colocá-lo em foco e, em seguida, use o <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Gizmo de Cena</a>, localizado no canto superior direito da janela Cena, para ajustar o ângulo de exibição ao longo do eixo Z de avanço.

Com o objeto **PressableButtonHoloLens2** ainda selecionado, na janela **Inspetor**:

* Altere sua **Posição** de Transformação de modo que ela esteja posicionada na frente da câmera, que está posicionada na origem, por exemplo, x = 0, y = 0 e z = 0,5

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> Em geral, 1 unidade de posição no Unity é aproximadamente equivalente a 1 metro no mundo físico. Porém, há exceções, por exemplo, quando objetos são filhos de objetos dimensionados.

### <a name="2-add-a-cube-to-the-scene"></a>2. Adicione um cubo à cena

Clique com o botão direito do mouse em um ponto vazio dentro da janela Hierarquia e selecione **Objeto 3D** > **Cubo** para adicionar um cubo à sua cena:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

Com o objeto **Cubo** ainda selecionado, na janela **Inspetor**:

* Altere sua **Posição** de Transformação para que fique perto do botão pressionável, mas não se sobreponha a ela, por exemplo, x = 0, y = 0,04 e z = 0,5
* Altere sua **Escala** de Transformação para um tamanho adequado, por exemplo, x = 0,02, y = 0,02 e z = 0,02

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. Configurar o tipo de evento InteractableOnPressReceiver

Na janela Hierarquia, selecione o objeto **PressableButtonHoloLens2** e, em seguida, na janela **Inspetor**, **menu de hambúrguer**, selecione **Recolher Todos os Componentes** para obter uma visão geral de todos os componentes neste objeto:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

Expanda o componente **Item Passível de Interação (Script)** e, em seguida, localize e expanda a seção **Eventos** > **Receptores**:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

Clique no botão **Adicionar Evento** para criar um receptor de evento do Tipo de Receptor de Evento **InteractableOnPressReceiver**:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> O Tipo de Receptor de Evento chamado InteractableOnPressReceiver permite que o botão responda a um evento pressionado quando uma mão acompanhada pressiona o botão.

Para o receptor de eventos que acaba de ser criado, altere **Filtro de Interação** para **Próximo e Distante**:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. Configurar o cubo para receber o evento On Press

Na janela Hierarquia, **clique e arraste** o **Cubo** para o campo **Propriedades do Evento** para o evento **On Press ()**  para atribuir o cubo como um destinatário do evento On Press ():

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. Definir a ação a ser disparada pelo evento On Press

Clique no menu suspenso de ação, atribuído no momento a **Nenhuma Função**, e selecione **MeshRenderer** > **Material de material** para definir a propriedade de material do Cubo a ser alterada quando o evento On Press () for disparado:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

Clique no ícone de **círculo** pequeno ao lado do campo material, atualmente preenchido com **Nenhum (Material)** , para abrir a janela Selecionar Material:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

Na janela Selecionar Material, **pesquise** **MRTK_Standard** e selecione um material adequado, por exemplo, **MRTK_Standard_Cyan** para que a cor do Cubo seja alterada para ciano quando o botão for pressionado:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. Configurar o cubo para receber o evento Ao Liberar

**Repita** a Etapa 4 para o evento Ao Liberar para atribuir o **Cubo** como um receptor do evento **Ao Liberar ()** .

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. Definir a ação a ser disparada pelo evento Ao Liberar

**Repita** a Etapa 5 para o evento Ao Liberar, mas escolha o material **MRTK_Standard_LightGray** para que a cor do Cubo retorne à cor cinza-claro original quando o botão for liberado:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. Testar o botão usando a simulação no editor

Pressione o botão **Reproduzir** para entrar no modo de jogo e use a simulação de entrada no editor para testar seu botão recentemente configurado.

Botão não pressionado (barra de espaços + roda de rolagem do mouse para trás):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

Botão pressionado (barra de espaços + roda de rolagem do mouse para frente):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> Para saber como usar a simulação de entrada no editor, você pode consultar o guia [Como usar a simulação de entrada de mão no editor para testar uma cena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) no [Portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Como criar um painel de botões usando a coleção de objetos de grade do MRTK

Nesta seção, você aprenderá como alinhar automaticamente vários botões em uma interface do usuário nítida usando a ferramenta Coleção de Objetos de Grade do MRTK.

Este exemplo específico mostrará como criar um painel com cinco botões alinhados horizontalmente. No entanto, você pode seguir esses mesmos princípios para criar outros layouts.

As principais etapas que você seguirá para conseguir isso são:

1. Subordine os objetos de botão a um objeto pai
2. Adicionar e configurar o componente de Coleção de Objetos de Grade (Script)
3. Testar os botões usando a simulação no editor

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. Subordine os objetos de botão a um objeto pai

Clique com o botão direito do mouse em um ponto vazio dentro da janela Hierarquia e selecione **Criar Vazio**:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

Clique com o botão direito do mouse no objeto recém-criado, selecione **Renomear** e dê a ele um nome adequado, por exemplo, **ButtonCollection**:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

Selecione o objeto **PressableButtonHoloLens2** e **arraste**-o para a parte superior do objeto **ButtonCollection** para torná-lo um filho do objeto ButtonCollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

Clique com o botão direito do mouse no objeto **PressableButtonHoloLens2** e selecione **Duplicar** para criar uma cópia dele:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

**Repita** esta etapa quatro vezes até que você tenha um total de cinco objetos PressableButtonHoloLens2.

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Adicionar e configurar o componente de Coleção de Objetos de Grade (Script)

Com o objeto ButtonCollection selecionado na janela Hierarquia, na janela Inspetor, clique no botão **Adicionar Componente**. Em seguida, pesquise e selecione **Coleção de Objetos de Grade** para adicionar um componente Coleção de Objetos de Grade (Script) ao objeto ButtonCollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

Configure a Coleção de Objetos de Grade (Script) da seguinte maneira:

* Altere **Número de Linhas** para 1 para alinhar todos os botões em uma só linha
* Altere **Largura da Célula** para 0,05 para espaçar os botões dentro da linha

Em seguida, clique no botão **Atualizar Coleção** para aplicar a nova configuração:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> As alterações de configuração que você acabou de aplicar representam as alterações mínimas necessárias para atingir o objetivo de colocar os botões em uma só linha. No entanto, em projetos futuros, dependendo de fatores como a orientação dos objetos pai e filho, talvez seja necessário ajustar outras configurações, como o tipo de orientação. Para saber mais sobre a coleção de objetos de grade do MRTK, você pode acessar o guia [Scripts da coleção de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) no [Portal da Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

Com o objeto ButtonCollection ainda selecionado na janela Hierarquia, na janela Inspetor, altere a **Posição** da Transformação do objeto ButtonCollection para que seus objetos de botão filho sejam posicionados na frente da câmera, que está posicionada na origem, por exemplo, x = 0, y = 0 e z = 0,5:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> Quando você adicionou pela primeira vez o pré-fabricado PressableButtonHoloLens2 à cena na seção [Gestos de acompanhamento de mão e botões de interação](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) acima, você o posicionou na frente da câmera. No entanto, como a Coleção de Objetos de Grade controla a posição de objetos filho imediatos, a posição Z dos objetos filho PressableButtonHoloLens2 foi redefinida como 0 de acordo com a Distância padrão da Coleção de Objetos de Grade do valor pai 0. Esse (e para manter a relação posicional pai/filho organizada) é o motivo pelo qual mudamos a posição do objeto ButtonCollection pai para frente, em vez de configurar a Distância do valor pai para mover os objetos filho PressableButtonHoloLens2 para frente.

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. Testar os botões usando a simulação no editor

Pressione o botão Reproduzir para entrar no modo de Jogo e use a simulação de entrada no editor para testar cada um dos botões no painel de botões que acaba de ser criado:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> No momento, quando você pressiona qualquer um dos cinco botões, a cor do cubo muda para ciano. Para tornar a experiência mais interessante, use o que você acaba de aprender para configurar cada botão para alterar o cubo para uma cor diferente.

## <a name="adding-text-into-your-scene"></a>Como adicionar texto à sua cena

Nesta seção, você aprenderá a adicionar texto às suas experiências de realidade misturada usando o TextMesh Pro da Unity, que você preparou na seção [Importar Recursos Essenciais do TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) do tutorial anterior.

Neste exemplo específico, você adicionará um rótulo simples sob a coleção de botões que você criou na seção anterior.

Clique com o botão direito do mouse no objeto ButtonCollection e selecione **Objeto 3D** > **Text-TextMeshPro** para criar um objeto TextMeshPro como um filho do objeto ButtonCollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

Com o objeto TextMeshPro que acaba de ser criado, o Texto nomeado (TMP), ainda selecionado, na janela Inspetor, muda de posição e tamanho para que o rótulo seja posicionado de maneira organizada abaixo da coleção de botões, por exemplo:

* Alterar a **Pos Y** de Rect Transform para -0,0425
* Alterar a **Largura** de Rect Transform para 0,24
* Alterar a **Altura** de Rect Transform para 0,024

Em seguida, atualize o texto para refletir qual é o rótulo e escolha as propriedades da fonte para que o texto caiba no rótulo, por exemplo:

* Alterar o **Texto** do Text Mesh Pro (Script) para Coleção de Botões
* Alterar o **Estilo da Fonte** do Text Mesh Pro (Script) para Negrito
* Alterar o **Tamanho da Fonte** do Text Mesh Pro (Script) para 0,2
* Alterar o **Alinhamento** do Text Mesh Pro (Script) para Centro e Meio

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a clonar, personalizar e definir uma configuração de perfil do MRTK. Você também aprendeu a interagir com botões para disparar eventos usando mãos rastreadas no HoloLens 2. Por fim, você aprendeu a criar uma interface do usuário simples usando o componente Coleção de Objetos de Grade do MRTK e o Text Mesh Pro do Unity.

[Próximo tutorial: 4. Colocar o conteúdo dinâmico e usar solucionadores](mrlearning-base-ch3.md)
