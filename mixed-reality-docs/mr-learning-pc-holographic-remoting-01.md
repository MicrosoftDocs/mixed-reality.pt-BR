---
title: Tutoriais de comunicação remota holográfica para PC – 1. Introdução à comunicação remota holográfica para PC
description: Conclua este curso para aprender como criar a experiência de realidade misturada remota do seu PC para o HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/29/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 4929634d70a082e835eb7bd6b5680719338a5e92
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476968"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a>1. Introdução à Comunicação Remota Holográfica para PC

## <a name="overview"></a>Visão geral

  Bem-vindo(a) aos tutoriais do HoloLens 2. Nesta série de tutoriais de duas partes, você aprenderá a criar uma demonstração de experiência de realidade misturada e a criar um aplicativo de PC para a Comunicação Remota do Holographic.

   Neste tutorial, [Criar uma experiência de realidade misturada](mr-learning-pc-holographic-remoting-01.md), você aprenderá a criar uma experiência de realidade misturada. Ele demonstrará elementos da interface do usuário, manipulação de modelo 3D, recorte de modelo e recursos de acompanhamento de olho.

  No segundo tutorial, [Criar um aplicativo de Comunicação Remota Holographic](mr-learning-pc-holographic-remoting-02.md), você aprenderá a criar um aplicativo de PC para Comunicação Remota do Holographic. E conecte-se ao HoloLens 2 a qualquer momento, fornecendo um modo de visualizar o conteúdo 3D em realidade misturada.

## <a name="objectives"></a>Objetivos

* Importar ativos e configurar a cena
* Interagir com hologramas usando os botões e elementos de interface do usuário
* Configurar objetos 3D para o recurso de recorte
* Aprenda a ativar dicas de ferramentas com acompanhamento de olho

## <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)
* Conhecimento básico de programação em C#
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.X montado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado

**Recomendamos expressamente** a conclusão da série de tutoriais de [Introdução](mr-learning-base-01.md) ou alguma experiência anterior básica com o Unity e o MRTK antes de continuar.

> [!IMPORTANT]
> * A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.3.X. Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.
> * O Holographic Remoting com projetos do MRTK só funcionará com o XR herdado. No momento, não há suporte para o SDK do XR.

## <a name="creating-and-preparing-the-unity-project"></a>Como criar e preparar o projeto do Unity

Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.

Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:

1. [Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*

1. [Como alternar a plataforma de build](mr-learning-base-02.md#configuring-the-unity-project)

1. [Como importar os Recursos Essenciais do TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Como importar o Kit de Ferramentas de Realidade Misturada](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Como configurar o projeto do Unity](mr-learning-base-02.md#configuring-the-unity-project)

1. [Criar e definir a cena](mr-learning-base-02.md#creating-and-configuring-the-scene) e dar um nome adequado à cena, por exemplo, **Comunicação Remota Holográfica para PC**

Então siga as instruções para [Alterar a Opção de Exibição de Reconhecimento Espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para alterar o perfil de configuração do MRTK para sua cena para o **DefaultHoloLens2ConfigurationProfile**. Altere as opções de exibição da malha de reconhecimento espacial para **Oclusão**.

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Baixe e **importe** o [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).

>[!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Importar o Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a>Como configurar e preparar a cena

Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.

Na janela do projeto, navegue até a pasta **Ativos** > **MRTK.Tutoriais.PCHolograhicRemoting** > **Pré-fabricados**. Enquanto pressiona o botão CTRL, clique nos seis pré-fabricados abaixo.

* ButtonParent
* ClippingObjects
* HandSpatialMapButton
* Instruções
* ModelParent
* Plataforma

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

Arraste e solte esses modelos da pasta de pré-fabricados na **janela Hierarquia**.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

Para se concentrar nos objetos da cena, você pode clicar duas vezes no objeto **ModelParent** e, em seguida, reduzir levemente o zoom de novo:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> Se você considerar que ícones grandes em sua cena, como os ícones "T" grandes, causam distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Gizmos</a> para a posição de desligado.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Como configurar os botões para operar a cena

Nesta seção, você adicionará scripts à cena para criar eventos de botão que demonstram os conceitos básicos de alternância de modelo e funcionalidade de recorte.

### <a name="1-configuring-the-interactable-script-component"></a>1. Como configurar o componente Interactable (Script)

Na janela Hierarquia, expanda o objeto **ButtonParent** e selecione o **NextButton**. Na janela Inspetor, localize o componente **Interactable (Script)** e clique no ícone **+** sob o evento **OnClick ()** .

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

Com o objeto **NextButton** ainda selecionado na janela Hierarquia, clique e arraste o objeto **ButtonParent** da janela Hierarquia para o campo vazio **Nenhum (Objeto)** do evento que você acabou de adicionar para fazer com que o objeto ButtonParent ouça o evento de clique do botão deste botão:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

Clique no menu suspenso **Nenhuma Função** do mesmo evento. Em seguida, selecione **ViewButtonControl** > **NextModel ()** para definir a função **NextModel ()** como a ação disparada quando os eventos pressionados pelo botão são acionados desse botão:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a>2. Como configurar os botões restantes

Para cada um dos botões restantes, conclua o processo descrito acima para atribuir funções aos eventos **OnClick ()** :

* Para o objeto PreviousButton, atribua a função **ViewButtonControl**l > **PreviousModel ()** .

* Para ClippingButton, selecione a função **ToggleButton** > **ToggleClipping ()** .

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a>3. Como configurar os componentes Controle de Botão de Exibição (Script) e Botão de Alternância (Script)

Agora, os botões estão configurados para demonstrar a funcionalidade de recorte e troca de modelos. É hora de adicionar modelos 3D e os objetos de recorte ao script.

Fornecemos seis modelos 3D diferentes para demonstração. Expanda o ***ModelParentobject*** para expor esses modelos 3D.

Com o objeto ButtonParent ainda selecionado na janela hierarquia, na janela Inspetor, localize o componente **Exibir Controle de Botão (Script)** e expanda a variável **Modelos**.

No campo **Tamanho**, insira o número de modelos 3D que você gostaria de ter em sua cena. Neste caso, seriam seis. Ele criará campos para adicionar modelos 3D.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

Arraste e solte cada objeto filho do objeto ModelParent nesses campos.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

Arraste e solte o objeto **ClippingObjects** da janela Hierarquia para o campo **Objeto de Recorte** do componente **Botão de Alternância (Script)** .
>[!NOTE]
>Fique somente no objeto pai do botão.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

Na janela Hierarquia, selecione o pré-fabricado **ClippingObjects** e habilite-o na janela Inspetor para ativar os objetos de Recorte.

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a>Como configurar os objetos de recorte para habilitar o recurso de recorte

Nesta seção, você adicionará o renderizador de objetos filho do objeto MarsCuriosityRover em um objeto de recorte individual para demonstrar o recorte do modelo MarsCuriosityRover.

Na janela Hierarquia, expanda o objeto **ClippingObjects** para expor os três objetos de recorte diferentes que você usará neste projeto.

Para configurar o objeto **ClippingSphere**, clique nele e, na janela Inspetor, localize o componente **Esfera de Corte (Script)** . Insira o número de renderizadores no campo tamanho que você precisa adicionar para seu modelo 3D. Nesse caso, adicione 10 para objetos filho MarsCuriosityRover. Ele criará campos para adicionar renderizadores, arrastar e soltar objetos de modelo filho do objeto MarsCuriosityRover nesses campos.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

Siga o mesmo processo e adicione os renderizadores de objetos filho de MarsCuriosityRover aos objetos **ClippingBox** e **ClippingPlane**.

Neste tutorial, somente o modelo MarsCuriosityRover será usado para demonstrar o recurso de recorte. Eles estavam adicionando recursos de recorte a mais modelos, aumentando o tamanho do renderizador e adicionando seus renderizadores de malha individuais.

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a>Como configurar o acompanhamento de olho para realçar dicas de ferramenta

Nesta seção, você vai explorar como habilitar o Acompanhamento Ocular em seu projeto. Por exemplo, você implementará a funcionalidade para realçar dicas de ferramentas anexadas às partes do MarsCuriosityRover enquanto olha para elas ocultá-las enquanto você está olhando longe delas.

### <a name="1-identify-target-objects-and-associated-tooltips"></a>1. Identificar objetos de destino e dicas de ferramenta associadas

Na janela Hierarquia, selecione o objeto ModelParent. Expanda ***MarsCuriosity -> Rover*** para encontrar cinco partes principais do MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.

* Observe cinco objetos de dica de ferramentas correspondentes associados a partes MarsCuriosityRover na janela Hierarquia.
* Você vai configurar esses objetos para realçar a experiência ao examinar as partes MarsCuriosityRover.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a>2. Implementar ao examinar os eventos At Target () e On Look Away ()

Na janela Hierarquia, selecione o objeto ***POI-Camera***. Na janela Inspetor, localize o componente **Destino de Acompanhamento de Olho (Script)** e configure os eventos **While Looking At Target ()**  & **On Look Away ()** da seguinte maneira:

* Para o campo **Nenhum (Objeto)** , atribua o objeto **POI-Camera ToolTip**
* Na lista suspensa **Nenhuma Função** do evento **While Looking At Target ()** , selecione **GameObject** > **SetActive (bool).** Marque a **Caixa de Seleção** abaixo dela para realçar a dica de ferramenta como a ação que é disparada quando você examina o objeto de destino.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* Siga o mesmo processo e clique no menu suspenso **Nenhuma Função** do ouvinte de eventos **On Look Away ()** . Em seguida, selecione **GameObject** > **SetActive (bool**) e deixe a **Caixa de Seleção** vazia para ocultar a dica de ferramenta como a ação disparada quando você olhar para longe do objeto de destino.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

Siga o mesmo processo e atribua os respectivos objetos de dica de ferramenta aos mesmos eventos **While Looking At Target ()**  & **On Look Away ()** das partes **MarsCuriosityRover**.

Para habilitar o acompanhamento de olho, siga estas [diretrizes](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a criar uma experiência de realidade misturada que demonstra elementos da interface do usuário, manipulação de modelo 3D, recorte de modelo e recursos de acompanhamento de olho. O tutorial forneceu a você o NextButton e o PreviousButton que permitem explorar a experiência do visualizador de modelos 3D. O ClippingObjectButton fez com que você ativasse objetos de recorte e experimentasse o recurso de recorte. O tutorial também forneceu a você um elemento de acompanhamento de olho para habilitar o realce das dicas de ferramenta na experiência.

Na próxima lição, você aprenderá a criar um aplicativo de Comunicação Remota Holográfico para PC para conectar o HoloLens 2 a qualquer momento, fornecendo um modo de visualizar o conteúdo 3D em realidade misturada.

[Próxima lição: 2. Criar aplicativo de Comunicação Remota Holográfico](mr-learning-pc-holographic-remoting-02.md)
