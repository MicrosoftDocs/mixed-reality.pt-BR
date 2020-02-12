---
title: Tutoriais de introdução-5. Interagindo com objetos 3D
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: a1b26d56b4693ef23f2d77ba53e0961693489a3a
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130187"
---
# <a name="5-interacting-with-3d-objects"></a>5. interagindo com objetos 3D

Neste tutorial, você aprenderá sobre o conteúdo básico de 3D e a experiência do usuário, como organizar objetos 3D como parte de uma coleção, caixas delimitadoras para manipulação básica, interação próxima e extrema e gestos de toque e captura com acompanhamento manual.

## <a name="objectives"></a>Objetivos

* Criar um painel de objetos 3D que serão usados para os outros objetivos de aprendizado
* Implementar caixas delimitadoras
* Configurar objetos 3D para manipulação básica, como mover, girar e dimensionar
* Explorar a interação próxima e distante
* Saiba mais sobre gestos de acompanhamento de mão, como pegar e tocar

## <a name="importing-the-tutorial-assets"></a>Importando os ativos do tutorial

Baixe e importe o pacote personalizado do Unity:

* [MRTK. HoloLens2. Unity. tutoriais. assets. GettingStarted. 2.2.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage)

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções de [importação do kit de ferramentas da realidade misturada](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .

## <a name="decluttering-the-scene-view"></a>Desobstruindo o modo de exibição de cena

Para facilitar o trabalho com sua cena, defina a visibilidade da **cena** para os objetos Cube e buttoncollection como off clicando no ícone de **olho** à esquerda dos objetos. Isso oculta o objeto na janela de cena sem alterar sua visibilidade no jogo:

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> Para saber mais sobre os controles de visibilidade da cena e como usá-los para otimizar o fluxo de trabalho e a exibição de cena, você pode visitar a documentação de <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilidade da cena</a> do Unity.

## <a name="organizing-3d-objects-in-a-collection"></a>Organizando objetos 3D em uma coleção

Nesta seção, você criará um painel de objetos 3D que será usado ao explorar várias maneiras de interagir com objetos 3D nas seções a seguir deste tutorial. Especificamente, você configurará os objetos 3D a serem posicionados em uma grade 3 x 3.

Da mesma forma que quando você [criou um painel de botões](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), as principais etapas que você seguirá para fazer isso são:

1. Pai dos objetos 3D para um objeto pai
2. Adicionar e configurar o componente de coleção de objetos de grade (script)

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. pai dos objetos 3D para um objeto pai

Na janela hierarquia, **crie um objeto vazio**, dê a ele um nome adequado, por exemplo, **3DObjectCollection**, e posicione-o em um local adequado, por exemplo, X = 0, Y =-0,2, Z = 2.

Na janela do projeto, navegue até **ativos** > **MRTK. Tutoriais. GettingStarted** > **pré-fabricados**e, em seguida, **pai** o seguinte pré-fabricados para o **3DObjectCollection**:

* Queijo
* CoffeeCup
* EarthCore
* Octa
* Platão
* O módulo

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

Na janela hierarquia, **crie três cubos** como objetos filho do **3DObjectCollection** e defina a **escala** de transformação como X = 0,15, Y = 0,15, Z = 0,15:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

<!-- TODO: Finish -->
> [!TIP]
> Para obter um lembrete sobre como executar as etapas listadas acima, você pode consultar o tutorial [criando a interface do usuário e configurar o kit de ferramentas de realidade misturada](mrlearning-base-ch2.md) .

Reposicione os cubos para que você possa ver cada cubo:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

Na janela do projeto, navegue até **ativos** > **MixedRealityToolkit. SDK** > **StandardAssets** > **materiais** para ver os materiais fornecidos com o MRTK.

**Clique e arraste** um material adequado para a propriedade elemento 0 de **materiais** do processador de malha de cada cubo, por exemplo:

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. adicionar e configurar o componente de coleção de objetos de grade (script)

Adicione um componente de **coleção de objetos de grade (script)** ao objeto 3DObjectCollection e configure-o da seguinte maneira:

* Altere o **tipo de classificação** para ordem filho para garantir que os objetos filho sejam classificados na ordem em que você os colocou sob o objeto pai

Em seguida, clique no botão **Atualizar coleção** para aplicar a nova configuração:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>Manipulando objetos 3D

Nesta seção, você adicionará a capacidade de manipular todos os objetos 3D no painel criado na seção anterior. Além disso, para os objetos pré-fabricado, você permitirá que os usuários atinjam e peguem esses objetos com mãos controladas. Em seguida, você irá explorar alguns comportamentos de manipulação que podem ser aplicados aos seus objetos.

As principais etapas que você seguirá para conseguir isso são:

1. Adicionar o componente manipulador de manipulação (script) a todos os objetos
2. Adicionar o componente de proximidade de interação Near (script) aos objetos pré-fabricado
3. Configurar o componente manipulador de manipulação (script)

> [!IMPORTANT]
> Para poder **manipular um objeto**, o objeto deve ter os seguintes componentes:
>
> * Componente **colisor** , por exemplo, um colisor de caixa
> * Componente **manipulador de manipulação (script)**
>
> Para poder **manipular** e **obter um objeto com mãos controladas**, o objeto deve ter os seguintes componentes:
>
> * Componente **colisor** , por exemplo, um colisor de caixa
> * Componente **manipulador de manipulação (script)**
> * Componente **de captura de proximidade (script) próximo de interação**

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. Adicionar o componente manipulador de manipulação (script) a todos os objetos

Na janela hierarquia, selecione o objeto **queijo** , mantenha pressionada a tecla **Shift** e, em seguida, selecione o objeto **Cube ()** e adicione o componente **manipulador de manipulação (script)** a todos os objetos:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> Para fins deste tutorial, os colisors já foram adicionados ao pré-fabricados. Para primitivos do Unity, como os objetos de cubo, o componente colisor é adicionado automaticamente quando o objeto é criado. Na imagem acima, os colisors são representados pelos contornos verdes. Para saber mais sobre os colisors, você pode visitar a documentação do <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Colider</a> do Unity.

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. Adicione o componente de "script" de interação Near a objetos pré-fabricado

Na janela hierarquia, selecione o objeto **queijo** , mantenha pressionada a tecla **Shift** e, em seguida, selecione o objeto do **módulo** e adicione o componente de controle de **interação Near (script)** a todos os objetos:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. configurar o componente manipulador de manipulação (script)

#### <a name="default-manipulation"></a>Manipulação padrão

Para o objeto **Cube** , deixe todas as propriedades em padrão, para experimentar o comportamento de manipulação padrão:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> Para redefinir um componente para seus valores padrão, você pode selecionar o ícone de configurações do componente e selecionar redefinir.

#### <a name="restrict-manipulation-to-scale-only"></a>Restringir a manipulação somente para escala

Para o objeto **Cube (1)** , altere o **tipo de manipulação de duas mãos** para dimensionar para permitir que o usuário altere o tamanho do objeto:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>Restringir o movimento a uma distância fixa do usuário

Para o objeto **Cube (2)** , altere a **restrição no movimento** para corrigir a distância do cabeçalho para que, quando o objeto for movido, ele permaneça à mesma distância do usuário:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>Manipulação de captura padrão

Para os objetos **queijo**, **CoffeCup**e **EarthCore** , deixe todas as propriedades em padrão para experimentar o comportamento de manipulação de captura padrão:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>Remover a capacidade de manipulação distante

Para o objeto **Octa** , desmarque a caixa de seleção **permitir manipulação distante** para que o usuário possa interagir apenas com o objeto diretamente usando as mãos rastreadas:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>Fazer um objeto girar em volta do seu centro

Para o objeto **Platão** , altere o **modo de rotação de uma mão próximo** e o **modo de rotação de uma mão** para girar sobre a central de objetos para fazê-lo quando o usuário girar o objeto com uma mão, ele gira em torno do centro do objeto:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="prevent-movement-after-object-is-released"></a>Impedir movimento após o lançamento do objeto

Para o objeto do **módulo** , altere o **comportamento da liberação** para nada, de modo que depois que o objeto for liberado da mão do usuário, ele não continuará a ser movido:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

Para saber mais sobre o componente do manipulador de manipulação e suas propriedades associadas, você pode visitar o guia do [manipulador de manipulação](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) no portal de [documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-bounding-boxes"></a>Adicionando caixas delimitadoras

As caixas delimitadoras tornam mais fácil e mais intuitivo manipular objetos com uma mão para interação próxima e extrema, fornecendo identificadores que podem ser usados para dimensionamento e rotação.

Neste exemplo, você adicionará uma caixa delimitadora ao objeto EarthCore para que esse objeto agora possa interagir usando a manipulação de objeto configurada na seção anterior, bem como, dimensionada e girada usando os identificadores da caixa delimitadora.

> [!IMPORTANT]
> Para poder usar uma **caixa delimitadora**, o objeto deve ter os seguintes componentes:
>
> * Componente **colisor** , por exemplo, um colisor de caixa
> * Componente **de caixa delimitadora (script)**

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. Adicionar o componente de caixa delimitadora (script) ao objeto EarthCore

Na janela Inspetor, selecione o objeto **EarthCore** e adicione o componente de **caixa delimitadora (script)** ao objeto EarthCore:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> As visualizações da caixa delimitadora são criadas em tempo de execução e, portanto, não são visíveis antes de você entrar no modo de jogo.

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. visualize e teste a caixa delimitadora usando a simulação no editor

Pressione o botão reproduzir para entrar no modo de jogo. Em seguida, pressione e segure a barra de espaços para abrir a mão e use o mouse para interagir com a caixa delimitadora:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

Para saber mais sobre o componente de caixa delimitadora e suas propriedades associadas, você pode visitar o guia de [caixa delimitadora](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) no [portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-touch-effects"></a>Adicionando efeitos de toque

Neste exemplo, você permitirá que os eventos sejam disparados quando você tocar em um objeto com sua mão. Especificamente, você configurará o objeto Octa para reproduzir um efeito de som quando o usuário o tocar.

As principais etapas que você seguirá para conseguir isso são:

1. Adicionar um componente de fonte de áudio ao objeto
2. Adicionar o componente de interação de proximidade (script) ao objeto
3. Adicionar o componente de toque de interação à mão (script) ao objeto
4. Implementar o evento on Touch Started
5. Testar a interação de toque usando a simulação no editor

> [!IMPORTANT]
> Para poder **disparar eventos de toque**, o objeto deve ter os seguintes componentes:
>
> * Componente **colisor** , preferencialmente um colisor de caixa
> * Componente **de toque próximo à interação (script)**
> * Componente **de toque de interação manual (script)**

> [!NOTE]
> O componente de toque de interação manual (script) não faz parte do MRTK. Ele foi importado com os ativos deste tutorial e, originalmente, parte dos exemplos do MixedReality Toolkit Unity.

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. adicionar um componente de fonte de áudio ao objeto

Na janela hierarquia, selecione o objeto **Octa** , adicione um componente **fonte de áudio** ao objeto Octa e altere a **mistura espacial** para 1 para habilitar o áudio espacial:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. Adicionar o componente de interação Near-toque (script) ao objeto

Com o objeto **Octa** ainda selecionado, adicione o componente de inclusão de **interação Near (script)** ao objeto Octa e, em seguida, clique nos botões **corrigir limites** e **corrigir centro** para atualizar as propriedades centro local e limites da interação próxima touchável (script) para corresponder ao BoxCollider:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. Adicionar o componente de toque de interação da mão (script) ao objeto

Com o objeto **Octa** ainda selecionado, adicione o componente de **toque de interação da mão (script)** ao objeto Octa:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. implementar o evento on Touch Started

No componente de toque de interação à mão (script), clique no ícone de **+** pequeno para criar um novo **no evento de toque iniciado ()** . Em seguida, configure o objeto **Octa** para receber o evento e defina o **audioname. PlayOneShot** como a ação a ser disparada:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

Navegue até **ativos** > **MixedRealityToolkit. SDK** > **StandardAssets** > materiais para ver os clipes de áudio fornecidos com o MRTK e, em seguida, atribua um clipe de áudio adequado ao campo **clipe de áudio** , por exemplo, o clipe de áudio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> Para obter um lembrete sobre como implementar eventos, consulte as instruções [gestos de acompanhamento de mão e botões](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) que podem interagir.

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. testar a interação de toque usando a simulação no editor

Pressione o botão reproduzir para entrar no modo de jogo. Em seguida, pressione e segure a barra de espaços para abrir a mão e usar o mouse para tocar no objeto Octa e disparar o efeito de som:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> Como vimos ao testar a interação de toque e, conforme mostrado na imagem acima, a cor do objeto Octa pulsated enquanto ela foi tocada. Esse efeito é embutido em código no componente de toque de interação manual (script) e não resultado da configuração de evento que você concluiu nas etapas acima.
>
> Se você quiser desabilitar esse efeito, poderá, por exemplo, comentar ou a linha 32 ' TargetRenderer = GetComponentInChildren<Renderer>(); ', o que resultará em TargetRenderer nulo restante e a cor não Pulsating.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a organizar objetos 3D em uma coleção de grade e a manipular esses objetos (dimensionamento, rotação e movimentação) usando a interação próxima (pegando diretamente com as mãos controladas) e a interação extrema (usando raios olhar ou raios de mão). Você também aprendeu como colocar caixas delimitadoras em objetos 3D e aprendeu como usar e personalizar as alças nas caixas delimitadoras. Por fim, você aprendeu a disparar eventos ao tocar um objeto.

[Próxima lição: 6. explorando opções de entrada avançadas](mrlearning-base-ch5.md)
