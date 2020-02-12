---
title: Tutoriais de introdução-4. Colocando conteúdo dinâmico e usando os solveres
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 8275d5a97d7827d34ed3926cabe4032cc7f4cfac
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129297"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. colocando o conteúdo dinâmico e usando os Solveres
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

Os hologramas ganham vida no HoloLens 2 quando acompanham intuitivamente o usuário e são colocados no ambiente físico de forma a tornar a interação direta e elegante. Neste tutorial, exploraremos maneiras de colocar os hologramas dinamicamente usando as ferramentas de posicionamento disponíveis do MRTK, conhecidas como resolvedores, para resolver cenários de posicionamento espacial complexos. No MRTK, os resolvedores são um sistema de scripts e comportamentos que são usados para permitir que elementos da interface do usuário sigam você, o usuário ou outros objetos de jogo na cena. Também podem ser usados para se ajustarem a determinadas posições rapidamente, tornando seu aplicativo mais intuitivo.

## <a name="objectives"></a>Objetivos

* Introduza os resolvedores do MRTK
* Usar os resolvedores para que um conjunto de botões siga o usuário
* Use os Solveres para que um objeto de jogo siga as mãos controladas pelo usuário

## <a name="location-of-solvers-in-the-mrtk"></a>Local dos resolvedores no MRTK

 Os resolvedores do MRTK estão localizados na pasta MRTK SDK. Para ver os resolvedores disponíveis em seu projeto, na janela do projeto, navegue até **ativos** > **MixedRealityToolkit. SDK** > **recursos** > **utilitários** > **solveres**:

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

Neste tutorial, examinaremos a implementação do solucionador de orbital e o solucionador de exibição radial. Para saber mais sobre a gama completa de resolvedores disponíveis no MRTK, você pode visitar o guia de [resolvedores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) no portal de [documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="use-a-solver-to-follow-the-user"></a>Usar um resolvedor para seguir o usuário
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

Nesta seção, você aprimorará a coleção de botões criada no tutorial anterior para que ele siga a direção do olhar do usuário. Além disso, você também configurará o resolvedor para que a coleção de botões sempre seja:

* Girado paralelamente à direção de leitura do usuário, para leitura natural da esquerda para a direita
* Posicionado ligeiramente abaixo da direção da olhar horizontal do usuário, portanto, não está obstruindo os outros objetos que serão adicionados posteriormente neste tutorial
* Posicionado aproximadamente o comprimento de um semestre do usuário, para que os botões possam ser facilmente pressionados

Para isso, você usará o **resolvedor orbital** que bloqueia o objeto para uma posição especificada e o deslocamento do objeto referenciado.

### <a name="1-add-the-orbital-solver"></a>1. Adicionar o resolvedor orbital

Na janela hierarquia, selecione o objeto **buttoncollection** e, em seguida, na janela Inspetor, use o botão **Adicionar componente** para adicionar o componente **orbital (script)** ao objeto buttoncollection.

> [!NOTE]
> Quando você adiciona um resolvedor, nesse caso, o componente orbital (script), o componente manipulador (script) do Solver é adicionado automaticamente, pois é exigido pelo resolvedor.

### <a name="2-configure-the-orbital-solver"></a>2. configurar o resolvedor orbital

Configure o componente **manipulador (script) do Solver** :

* Verifique se o **tipo de destino controlado** está definido como **Head**

Configure o componente **orbital (script)** :

* Alterar o **tipo de orientação** para **seguir objeto acompanhado**
* Redefinir **deslocamento local** para X = 0, Y = 0, Z = 0
* Alterar o **deslocamento do mundo** para X = 0, Y =-0,4, Z = 0,3

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. testar o resolvedor orbital usando a simulação no editor

Pressione o botão reproduzir para entrar no modo de jogo e pressione e mantenha o botão direito do mouse para girar sua direção olhar e observe o seguinte:

* A posição de transformação de Buttoncollection agora é controlada pelas configurações do Solver
* O cubo, que não é afetado pelo resolvedor, permanece na mesma posição

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> Se você não vir a câmera Ray em sua janela de cena, verifique se o menu utensílios está habilitado. Para saber mais sobre o menu utensílios e como você pode usá-lo para otimizar sua exibição de cena, você pode visitar a documentação do <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menu utensílios</a> do Unity.
>
> Para exibir sua cena e a janela do jogo lado a lado, conforme mostrado na imagem acima, basta arrastar a janela do jogo para o lado direito da janela cena. Para saber mais sobre como personalizar seu espaço de trabalho, você pode visitar a documentação de <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalização de espaço de trabalho</a> do Unity.

## <a name="enabling-objects-to-follow-tracked-hands"></a>Habilitando objetos para seguir as mãos controladas

Nesta seção, você configurará o objeto de cubo criado no tutorial anterior para que ele siga as mãos controladas pelo usuário, especificamente o pulso à direita. Além disso, você também configurará o resolvedor para que o cubo:

* Altera a orientação com a rotação da mão do usuário
* Posicionado no pulso do usuário

Para isso, você usará o **solucionador de exibição radial** que mantém o objeto em uma conversão de cone de exibição pelo objeto referenciado.

### <a name="1-add-the-radial-view-solver"></a>1. Adicionar o solucionador de exibição radial

Na janela hierarquia, selecione o objeto **cubo** e, na janela Inspetor, use o botão **Adicionar componente** para adicionar o objeto de cubo de componente de **exibição radial (script)** .

### <a name="2-configure-the-radial-view-solver"></a>2. configurar o solucionador de exibição radial

Configure o componente **manipulador (script) do Solver** :

* Alterar o **tipo de destino controlado** para a **junção à mão**
* Alterar a **mão controlada** à **direita**
* Alterar **mão controlada conjunta** para **pulso**

Configure o componente de **exibição radial (script)** :

* Altere a **direção de referência** para **orientado a objeto**e marque a caixa de seleção **orientar para direção de referência**
* Alterar a distância **mínima** e a **distância máxima** para 0

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. testar o solucionador de exibição radial usando a simulação no editor

Pressione o botão reproduzir para entrar no modo de jogo e pressione e segure a barra de espaços para abrir a mão. Mova o cursor do mouse para mover a mão e clique e mantenha o botão esquerdo do mouse para girar a mão:

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a usar os resolvedores do MRTK para ter uma interface do usuário intuitivamente seguir o User. Você também aprendeu como anexar um resolvedor a um objeto (ou seja, cubo) para seguir as mãos controladas pelo usuário. Para saber mais sobre esses e outros resolvedores incluídos no MRTK, você pode visitar o guia de [resolvedores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) no [portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

[Próximo tutorial: 5. interagindo com objetos 3D](mrlearning-base-ch4.md)
