---
title: Tutoriais de introdução – 7. Como interagir com objetos 3D
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: f02780a1b9421b814242727ce92311d62b5e3461
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376418"
---
# <a name="7-interacting-with-3d-objects"></a>7. Como interagir com objetos 3D

Neste tutorial, você aprenderá a habilitar a manipulação próxima e distante de objetos 3D e limitar os tipos de manipulação permitidos. Você também aprenderá a adicionar caixas delimitadoras em objetos 3D para facilitar o controle da manipulação de objetos.

## <a name="objectives"></a>Objetivos

* Saber como configurar objetos 3D para interagir com eles
* Saber como adicionar caixas delimitadoras a objetos 3D

## <a name="manipulating-3d-objects"></a>Como manipular objetos 3D

Nesta seção, você adicionará a capacidade de manipular todas as peças do Rover organizadas na tabela durante o tutorial [Como posicionar objetos na cena](mr-learning-base-04.md).

As principais etapas que você seguirá para conseguir isso são:

1. Adicionar o componente Object Manipulator (Script) a todos os objetos de peças
2. Adicionar o componente NearInteractionGrabbable a todos os objetos de peças
3. Configurar o componente Object Manipulator (Script)

> [!NOTE]
> Para poder **manipular um objeto**, o objeto deve ter os seguintes componentes:
>
> * Componente **Colisor**, por exemplo, um Colisor de Caixa
> * Componente **Object Manipulator (Script)**
>
> Para poder **manipular** e **capturar um objeto com as mãos acompanhadas**, o objeto deve ter os seguintes componentes:
>
> * Componente **Colisor**, por exemplo, um Colisor de Caixa
> * Componente **Object Manipulator (Script)**
> * Componente **NearInteractionGrabbable**

Além disso, você vai configurar o Rover Explorer para poder colocar as peças no Rover e montá-lo completamente.

Na janela Hierarquia, expanda o objeto RoverExplorer > **RoverParts** e selecione todos os seus objetos filho peças do Rover e o objeto **RoverAssembly**; em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar os seguintes componentes a todos os objetos selecionados:

* Componente **Object Manipulator (Script)**
* Componente **NearInteractionGrabbable**
* Componente **Part Assembly Controller (Script)**

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> Para selecionar vários objetos que não estão próximos uns dos outros, mantenha a tecla CTRL pressionada e use o mouse para selecionar qualquer objeto.

> [!NOTE]
> Para os fins deste tutorial, os colisores já foram adicionados às peças do Rover. Para saber mais sobre os colisores, acesse a documentação do <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Colisor</a> do Unity.

> [!NOTE]
> O Part Assembly Controller (Script) não faz parte do MRTK, mas foi incluído nos ativos do tutorial.

Com todos os objetos de peças do Rover e o objeto RoverAssembly ainda selecionados, na janela Inspetor, configure o componente **Object Manipulator (Script)** da seguinte maneira:

* Na lista suspensa **Tipo de Manipulação de Duas Mãos**, desmarque a Escala, deixando somente **Mover** e **Girar** habilitados

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> Até agora você habilitou a manipulação de objetos para todos os objetos de peças do Rover e o objeto RoverAssembly.

Na janela Projeto, navegue até a pasta **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** para localizar os clipes de áudio:

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

Na janela Hierarquia, selecione novamente todos os **objetos de peças do Rover** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Audio Sources**, configurando-o da seguinte maneira:

* Atribua o clipe de áudio **MRTK_Scale_Start** ao campo **AudioClip**
* Desmarque a caixa de seleção **Reproduzir ao Ativar**
* Altere **Spatial Blend** para 1

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

Na janela Hierarquia, expanda o objeto RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** para revelar todos os objetos de dica de posicionamento e, em seguida, selecione a primeira peça do Rover, RoverParts > **Camera_Part** e configure o componente **Part Assembly Controller (Script)** da seguinte maneira:

* Atribua o objeto **Camera_PlacementHint** ao campo **Location To Place**

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

**Repita** esta etapa para cada um dos objetos de peças do Rover restantes e o objeto RoverAssembly para configurar o componente **Part Assembly Controller (Script)** da seguinte maneira:

* Para o **Generator_Part**, atribua o objeto **Generator_PlacementHint** ao campo **Location To Place**
* Para o **Lights_Part**, atribua o objeto **Lights_PlacementHint** ao campo **Location To Place**
* Para o **UHFAntenna_Part**, atribua o objeto **UHFAntenna_PlacementHint** ao campo **Location To Place**
* Para o **Spectrometer_Part**, atribua o objeto **Spectrometer_PlacementHint** ao campo **Location To Place**
* Para o **RoverAssembly**, atribua o objeto em si, ou seja, o mesmo objeto **RoverAssembly**, para o campo **Location To Place**

Na janela Hierarquia, selecione o botão RoverExplorer > Botões > **Redefinir** e, na janela Inspetor, configure o evento **OnClick ()** interativo da seguinte maneira:

* Atribua o objeto **RoverAssembly** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **PartAssemblyController** > **ResetPlacement ()** para definir essa função como a ação a ser executada quando o evento for disparado

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

Se agora você entrar no modo de Jogo, poderá usar a interação próxima ou distante para posicionar as peças no Rover. Depois que a parte estiver próxima da dica de posicionamento correspondente, ela será encaixada no local e se tornará parte do Rover. Para redefinir os posicionamentos, pressione o botão Reset:

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

Para saber mais sobre o componente Object Manipulator e suas propriedades associadas, acesse o guia [Manipulador de Objeto](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-bounding-boxes"></a>Como adicionar caixas delimitadoras

As caixas delimitadoras tornam mais fácil e mais intuitivo manipular objetos com uma mão para interação próxima e distante fornecendo alças que podem ser usadas para dimensionamento e rotação.

Neste exemplo, você adicionará uma caixa delimitadora ao objeto RoverExplorer para que toda a experiência seja facilmente movida, girada e dimensionada. Além disso, você vai configurar o Menu para poder ativar e desativar a Caixa Delimitadora.

Na janela Hierarquia, selecione o objeto **RoverExplorer** e, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar os seguintes componentes:

* Componente **BoundingBox**
* Componente **Object Manipulator (Script)**

Em seguida, **desmarque** a caixa de seleção próxima dos dois componentes para deixá-los **desabilitados** por padrão:

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> A visualização da Caixa Delimitadora é criada em runtime e, portanto, não fica visível até que você entre no modo de Jogo.

> [!NOTE]
> O componente BoundingBox adicionará automaticamente o componente NearInteractionGrabbable em runtime. Portanto, não precisamos adicionar esse componente para pegar os objetos delimitados com as mãos controladas.

Na janela Hierarquia, expanda o objeto Menu > **ButtonCollection** para revelar os quatro botões e renomeie o terceiro botão para **BoundingBox_Enable**; em seguida, na janela Inspetor, configure o componente **Button Config Helper (Script)** da seguinte maneira:

* Altere o **Texto do Rótulo Principal** para **Habilitado**
* Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **BoundingBox** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **marcada**
* Clique no ícone pequeno **+** para adicionar outro evento
* Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **marcada**
* Deixe o **Ícone** como o ícone de "cubo com caixa delimitadora"

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

Renomeie o quarto e último botão como **BoundingBox_Disable** e, na janela Inspetor, configure o componente **Button Config Helper (Script)** da seguinte maneira:

* Altere o **Texto do Rótulo Principal** para **Desabilitado**
* Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **BoundingBox** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **desmarcada**
* Clique no ícone pequeno **+** para adicionar outro evento
* Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **desmarcada**
* Altere o **Ícone** para o ícone de "cubo com caixa delimitadora"

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

Se agora você entrar no modo de Jogo e habilitar a Caixa Delimitadora clicando no botão Enable, poderá usar a interação próxima ou distante para mover, girar e dimensionar a Caixa Delimitadora e usar o botão Disable para desabilitar a Caixa Delimitadora novamente:

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

Para saber mais sobre o componente de Caixa Delimitadora e suas propriedades associadas, acesse o guia da [Caixa Delimitadora](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu como habilitar a manipulação próxima e distante de objetos 3D e como limitar os tipos de manipulação permitidos. Você também aprendeu como adicionar caixas delimitadoras em objetos 3D para facilitar o controle da manipulação de objetos.

[Próximo tutorial: 8. Como usar o acompanhamento de olho](mr-learning-base-08.md)
