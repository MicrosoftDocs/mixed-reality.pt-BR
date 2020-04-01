---
title: Tutoriais de introdução – 5. Como interagir com objetos 3D
description: Saiba mais sobre as experiências básicas de conteúdo e de usuário 3D, como organizar objetos 3D e caixas delimitadoras para manipulação básica.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 65bcef6a7c10450816d7a928302b0b266b132f0f
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362073"
---
# <a name="5-interacting-with-3d-objects"></a>5. Como interagir com objetos 3D

Neste tutorial, você aprenderá sobre o conteúdo básico de 3D e a experiência do usuário, como organizar objetos 3D como parte de uma coleção, caixas delimitadoras para manipulação básica, interação próxima e distante e gestos de toque e captura com acompanhamento de mão.

## <a name="objectives"></a>Objetivos

* Criar um painel de objetos 3D que serão usados para os outros objetivos de aprendizado
* Implementar caixas delimitadoras
* Configurar objetos 3D para manipulação básica, como mover, girar e dimensionar
* Explorar a interação próxima e distante
* Conhecer gestos adicionais de acompanhamento de mãos, como toque e segurar

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Baixe e importe o pacote personalizado do Unity:

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Importar o Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

## <a name="decluttering-the-scene-view"></a>Como desobstruir o modo de exibição de cena

Para facilitar o trabalho com sua cena, defina a **visibilidade da cena** para os objetos **Cube** e **ButtonCollection** como desligada clicando no ícone de **olho** à esquerda dos objetos. Isso oculta o objeto na janela Cena sem alterar a visibilidade no jogo:

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> Para saber mais sobre os controles de visibilidade da cena e como usá-los para otimizar o fluxo de trabalho e a exibição de cena, você pode acessar a documentação de <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Visibilidade da Cena</a> do Unity.

## <a name="organizing-3d-objects-in-a-collection"></a>Como organizar objetos 3D em uma coleção

Nesta seção, você criará um painel de objetos 3D que será usado ao explorar várias maneiras de interagir com objetos 3D nas seções a seguir deste tutorial. Especificamente, você configurará os objetos 3D a serem posicionados em uma grade 3 x 3.

Da mesma forma que quando você [criou um painel de botões](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), as principais etapas que você seguirá para fazer isso são:

1. Subordinar os objetos 3D a um objeto pai
2. Adicionar e configurar o componente de Coleção de Objetos de Grade (Script)

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. Subordinar os objetos 3D a um objeto pai

Na janela Hierarquia, **criar um objeto vazio**, dê a ele um nome adequado, por exemplo, **3DObjectCollection** e posicione-o em uma localização adequada, por exemplo, X = 0, Y = -0,2, Z = 2.

Na janela Projeto, navegue até **Ativos** > **MRTK.Tutoriais.GettingStarted** > **Pré-fabricados**, então **subordine** os seguintes pré-fabricados à **3DObjectCollection**:

* Cheese
* CoffeeCup
* EarthCore
* Octa
* Platonic
* TheModule

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

Na janela Hierarquia, **crie três cubos** como objetos filho do objeto **3DObjectCollection** e defina sua **Escala** de Transformação para X = 0,15, Y = 0,15, Z = 0,15:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> Para obter um lembrete sobre como executar as etapas listadas acima, confira o tutorial [Como criar a interface do usuário e configurar o Mixed Reality Toolkit](mrlearning-base-ch2.md).

Reposicione os cubos para que você possa ver cada cubo:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

Na janela Projeto, navegue até **Ativos** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materiais** para ver os materiais fornecidos com o MRTK.

**Clique e arraste** um material adequado para cada propriedade de Elemento 0 de **Materiais** do Renderizador de Malha, por exemplo:

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Adicionar e configurar o componente de Coleção de Objetos de Grade (Script)

Adicione um componente da **Coleção de objetos de grade (script)** ao objeto **3DObjectCollection** e configure-o da seguinte maneira:

* Altere **Tipo de Classificação** para **Ordem Filho** para garantir que os objetos filho sejam classificados na ordem em que você os colocou sob o objeto pai

Em seguida, clique no botão **Atualizar Coleção** para aplicar a nova configuração:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>Como manipular objetos 3D

Nesta seção, você adicionará a capacidade de manipular todos os objetos 3D no painel criado na seção anterior. Além disso, para os objetos pré-fabricado, você permitirá que os usuários atinjam e peguem esses objetos com mãos controladas. Em seguida, você vai explorar alguns comportamentos de manipulação que podem ser aplicados aos seus objetos.

As principais etapas que você seguirá para conseguir isso são:

1. Adicionar o componente Manipulador de Manipulação (Script) a todos os objetos
2. Adicionar o componente de Capturável de Interação Próxima (Script) aos objetos pré-fabricados
3. Configurar o componente Manipulador de Manipulação (Script)

> [!IMPORTANT]
> Para poder **manipular um objeto**, o objeto deve ter os seguintes componentes:
>
> * Componente **Colisor**, por exemplo, um Colisor de Caixa
> * Componente **Manipulador de Manipulação (Script)**
>
> Para poder **manipular** e **capturar um objeto com as mãos acompanhadas**, o objeto deve ter os seguintes componentes:
>
> * Componente **Colisor**, por exemplo, um Colisor de Caixa
> * Componente **Manipulador de Manipulação (Script)**
> * Componente **Capturável de Interação Próxima (Script)**

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. Adicionar o componente Manipulador de Manipulação (Script) a todos os objetos

Na janela Hierarquia, selecione o objeto **Cheese**, mantenha pressionada a tecla **Shift** e, em seguida, selecione o objeto **Cube () 2** e adicione o componente **Manipulador de Manipulação (Script)** a todos os objetos:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> Para os fins deste tutorial, os colisores já foram adicionados aos pré-fabricados. Para primitivos do Unity, como os objetos Cube, o componente Colisor é adicionado automaticamente quando o objeto é criado. Na imagem acima, os colisores são representados pelos contornos verdes. Para saber mais sobre os colisores, acesse a documentação do <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Colisor</a> do Unity.

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. Adicionar o componente de Capturável de Interação Próxima (Script) aos objetos pré-fabricados

Na janela Hierarquia, selecione o objeto **Cheese**, mantenha pressionada a tecla **Shift** e, em seguida, selecione o objeto **TheModule** e adicione o componente **Capturável de Interação Próxima (Script)** a todos os objetos:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. Configurar o componente Manipulador de Manipulação (Script)

#### <a name="default-manipulation"></a>Manipulação padrão

Para o objeto **Cube**, deixe todas as propriedades em padrão para obter o comportamento de manipulação padrão:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> Para redefinir um componente para seus valores padrão, você pode selecionar o ícone de Configurações do componente e selecionar Redefinir.

#### <a name="restrict-manipulation-to-scale-only"></a>Restringir a manipulação somente para escala

Para o objeto **Cube (1)** , altere **Tipo de Manipulação de Duas Mãos** para **Escala** para permitir apenas que o usuário altere o tamanho do objeto:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>Restringir o movimento a uma distância fixa do usuário

Para o objeto **Cubo (2)** , altere **Restrição no Movimento** para **Distância Fixa da Cabeça** de modo que, quando o objeto for movido, ele permaneça à mesma distância do usuário:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>Manipulação capturável padrão

Para os objetos **Cheese**, **CoffeCup** e **EarthCore**, deixe todas as propriedades conforme o padrão para obter o comportamento de manipulação capturável padrão:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>Remover a capacidade de manipulação distante

Para o objeto **Octa**, desmarque a caixa de seleção **Permitir Manipulação Distante** para que o usuário possa interagir apenas com o objeto diretamente usando as mãos acompanhadas:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>Fazer um objeto girar em torno do seu centro

Para o objeto **Platonic**, altere **Modo de Rotação de Uma Mão Próxima** e **Modo de Rotação de Uma Mão Distante** para **Girar Sobre o Centro do Objeto** para que, quando o usuário gira o objeto com uma mão, ele gire em torno do centro do objeto:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a>Manter movimento após soltar o objeto

Para o objeto **TheModule**, adicione um componente **Rigidbody** para habilitar a física e desmarque a caixa de seleção **Usar Gravidade** para que o objeto não seja afetado pela gravidade:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

De volta ao componente Manipulador de Manipulação (Script), verifique se o **Comportamento ao Liberar** está definido como **Manter a Velocidade** e **Manter a Velocidade Angular** para que, depois que o objeto for solto da mão do usuário, ele continue a se mover:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

Para saber mais sobre o componente do Manipulador de Manipulação e suas propriedades associadas, você pode acessar o guia do [Manipulador de Manipulação](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-bounding-boxes"></a>Como adicionar caixas delimitadoras

As caixas delimitadoras tornam mais fácil e mais intuitivo manipular objetos com uma mão para interação próxima e distante fornecendo alças que podem ser usadas para dimensionamento e rotação.

Neste exemplo, você adicionará uma caixa delimitadora ao objeto EarthCore para que esse objeto agora possa interagir usando a manipulação de objeto configurada na seção anterior, bem como, dimensionado e girado usando os identificadores da caixa delimitadora.

> [!IMPORTANT]
> Para poder usar uma **caixa delimitadora**, o objeto deve ter os seguintes componentes:
>
> * Componente **Colisor**, por exemplo, um Colisor de Caixa
> * Componente **Caixa Delimitadora (Script)**

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. Adicionar o componente de Caixa Delimitadora (Script) ao objeto EarthCore

Na janela Inspetor, selecione o objeto **EarthCore** e adicione o componente **Caixa Delimitadora (Script)** ao objeto EarthCore:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> As visualizações da Caixa Delimitadora são criadas em tempo de execução e, portanto, não são visíveis antes de você entrar no modo de Jogo.

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. Visualizar e testar a caixa delimitadora usando a simulação no editor

Pressione o botão Reproduzir para entrar no modo de Jogo. Em seguida, pressione e segure a barra de espaços para abrir a mão e use o mouse para interagir com a caixa delimitadora:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

Para saber mais sobre o componente de Caixa Delimitadora e suas propriedades associadas, acesse o guia da [Caixa Delimitadora](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-touch-effects"></a>Como adicionar efeitos de toque

Neste exemplo, você permitirá que os eventos sejam disparados quando você tocar em um objeto com sua mão. Especificamente, você configurará o objeto Octa para reproduzir um efeito de som quando o usuário o tocar.

As principais etapas que você seguirá para conseguir isso são:

1. Adicionar um componente de Fonte de Áudio ao objeto
2. Adicionar o componente Tocável de Interação Próxima (Script) ao objeto
3. Adicionar o componente de Toque de Interação Manual (Script) ao objeto
4. Implementar o evento No Toque Iniciado
5. Testar a interação de toque usando a simulação no editor

> [!IMPORTANT]
> Para poder **disparar eventos de toque**, o objeto deve ter os seguintes componentes:
>
> * Componente **Colisor**, preferencialmente um Colisor de Caixa
> * Componente **Tocável de Interação Próxima (Script)**
> * Componente **Toque de Interação da Mão (Script)**

> [!NOTE]
> O componente de Toque de Interação da Mão (Script) não faz parte do MRTK. Ele foi importado com os ativos deste tutorial e, originalmente, faz parte dos exemplos do MixedReality Toolkit do Unity.

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. Adicionar um componente de Fonte de Áudio ao objeto

Na janela Hierarquia, selecione o objeto **Octa**, adicione um componente **Fonte de Áudio** ao objeto Octa e, em seguida, altere **Mistura Espacial** para 1 para habilitar o áudio espacial:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. Adicionar o componente Tocável de Interação Próxima (Script) ao objeto

Com o objeto **Octa** ainda selecionado, adicione o componente **Tocável de Interação Próxima (Script)** ao objeto Octa e clique nos botões **Corrigir Limites** e **Corrigir Centro** para atualizar as propriedades Limites e Centro Local do Tocável de Interação Próxima (Script) para que correspondam ao BoxCollider:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. Adicionar o componente de Toque de Interação Manual (Script) ao objeto

Com o objeto **Octa** ainda selecionado, adicione o componente **Toque de Interação da Mão (Script)** ao objeto Octa:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. Implementar o evento No Toque Iniciado

No componente **Toque de Interação da Mão (Script)** , clique no ícone **+** pequeno para criar um evento **No Toque Iniciado ()** . Em seguida, configure o objeto **Octa** para receber o evento e defina **AudioSource.PlayOneShot** como a ação a ser disparada:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

Navegue até **Ativos** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Áudio** para ver os clipes de áudio fornecidos com o MRTK e, em seguida, atribua um clipe de áudio adequado ao campo **Clipe de Áudio**, por exemplo, o clipe de áudio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> Para obter um lembrete sobre como implementar eventos, você pode consultar as instruções de [Gestos de acompanhamento da mão e botões interativos](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. Testar a interação de toque usando a simulação no editor

Pressione o botão Reproduzir para entrar no modo de Jogo. Em seguida, pressione e segure a barra de espaços para abrir a mão e usar o mouse para tocar no objeto Octa e disparar o efeito de som:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> Como vimos ao testar a interação de toque e, conforme mostrado na imagem acima, a cor do objeto Octa pulsou enquanto ele foi tocado. Esse efeito é embutido em código no componente de Toque de Interação Manual (Script) e não o resultado da configuração de evento que você concluiu nas etapas acima.
>
> Se você quiser desabilitar esse efeito, poderá, por exemplo, comentar ou a linha 32 'TargetRenderer = GetComponentInChildren<Renderer>();', o que resultará em TargetRenderer permanecer nulo e a cor não pulsar.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a organizar esses objetos em uma coleção de grades e manipulá-los (dimensionamento, rotação e movimentação) usando a interação próxima (segurar com as mãos rastreadas) e a interação distante (usando os raios de foco ou os raios de mãos). Você também aprendeu a colocar caixas delimitadoras em torno de objetos 3D e usar e personalizar as alças nas caixas delimitadoras. Por fim, você aprendeu a disparar eventos ao tocar um objeto.

[Próxima lição: 6. Explorar as opções avançadas de entrada](mrlearning-base-ch5.md)
