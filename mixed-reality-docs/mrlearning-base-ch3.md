---
title: Tutoriais de introdução – 4. Como posicionar o conteúdo dinâmico e usar Solucionadores
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8a85ab560d0e6b36b589970b4d5b8a441ed2bbe2
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "80362043"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. Como posicionar o conteúdo dinâmico e usar Solucionadores
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

Os hologramas ganham vida no HoloLens 2 quando seguem intuitivamente o usuário e são posicionados no ambiente físico de maneira a tornar a interação simples e elegante. Neste tutorial, exploraremos maneiras de posicionar hologramas dinamicamente usando as ferramentas de posicionamento disponíveis do MRTK, conhecidas como Solucionadores, para resolver cenários de posicionamento espacial complexos. No MRTK, os Solucionadores são um sistema de scripts e comportamentos usados para permitir que os elementos da interface do usuário sigam você, o usuário ou outros objetos do jogo na cena. Também podem ser usados para se ajustarem a determinadas posições rapidamente, tornando seu aplicativo mais intuitivo.

## <a name="objectives"></a>Objetivos

* Apresentar os Solucionadores do MRTK
* Usar os Solucionadores para fazer um conjunto de botões seguir o usuário
* Usar os Solucionadores para fazer um objeto do jogo seguir as mãos do usuário

## <a name="location-of-solvers-in-the-mrtk"></a>Localização dos Solucionadores no MRTK

 Os Solucionadores do MRTK estão localizados na pasta MRTK SDK. Para ver os Solucionadores disponíveis em seu projeto, na janela Projeto, navegue até **Ativos** > **MixedRealityToolkit.SDK** > **Recursos** > **Utilitários** > **Solucionadores**:

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

Neste tutorial, examinaremos a implementação do Solucionador Orbital e do Solucionador de Exibição Radial. Para saber mais sobre a gama completa de Solucionadores disponíveis no MRTK, você pode visitar o guia [Solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="use-a-solver-to-follow-the-user"></a>Usar um solucionador para seguir o usuário
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

Nesta seção, você aprimorará a coleção de botões criada no tutorial anterior para que siga a direção do olhar do usuário. Além disso, você também configurará o Solucionador para que a coleção de botões sempre seja:

* Girado paralelamente à direção de leitura do usuário, para leitura natural da esquerda para a direita
* Posicionado abaixo da direção do olhar horizontal do usuário para não obstruir os outros objetos que serão adicionados posteriormente neste tutorial
* Posicionado aproximadamente na metade do comprimento do braço do usuário, de modo que seja fácil pressionar os botões

Para isso, você usará o **Solucionador Orbital** que bloqueia o objeto a uma posição e deslocamento especificados do objeto referenciado.

### <a name="1-add-the-orbital-solver"></a>1. Adicionar o Solucionador Orbital

Na janela Hierarquia, selecione o objeto **ButtonCollection** e, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Orbital (Script)** ao objeto ButtonCollection.

> [!NOTE]
> Quando você adiciona um Solucionador, nesse caso, o componente Orbital (Script), o componente Manipulador do Solucionador (Script) é adicionado automaticamente, pois é exigido pelo Solucionador.

### <a name="2-configure-the-orbital-solver"></a>2. Configurar o Solucionador Orbital

Configure o componente **Manipulador do Solucionador (Script)** :

* Verifique se **Tipo de Alvo Acompanhado** está definido como **Cabeça**

Configure o componente **Orbital (Script)** :

* Verifique se **Tipo de Orientação** está definido como **Seguir Objeto Acompanhado**
* Redefinir **Deslocamento Local** para X = 0, Y = 0, Z = 0
* Alterar **Deslocamento Mundial** para X = 0, Y =-0,4, Z = 0,3

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. Testar o Solucionador Orbital usando a simulação no editor

Pressione o botão Reproduzir para entrar no modo de Jogo e pressione e mantenha pressionado o botão direito do mouse para girar a direção do olhar e observe o seguinte:

* A Posição de Transformação de ButtonCollection agora é controlada pelas configurações do Solucionador
* O Cubo, que não é afetado pelo Solucionador, permanece na mesma posição

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> Se você não vir o raio da câmera na janela Cena, verifique se o menu Gizmos está habilitado. Para saber mais sobre o menu Gizmos e como você pode usá-lo para otimizar a exibição de cena, acesse a documentação do <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menu Gizmos</a> do Unity.
>
> Para exibir a janela Cena e Jogo lado a lado como mostra a imagem acima, basta arrastar a janela Jogo para o lado direito da janela Cena. Para saber mais sobre como personalizar seu workspace, você pode visitar a documentação <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Como personalizar seu workspace</a>.

## <a name="enabling-objects-to-follow-tracked-hands"></a>Como habilitar os objetos a seguir mãos acompanhadas

Nesta seção, você configurará o objeto de cubo criado no tutorial anterior para que ele siga as mãos controladas pelo usuário, especificamente o pulso direito. Além disso, você também configurará o Solucionador para que o cubo:

* Altere sua orientação com a rotação da mão do usuário
* Posicionado no pulso do usuário

Para isso, você usará o **Solucionador de Exibição Radial** que mantém o objeto em uma conversão de cone de exibição pelo objeto referenciado.

### <a name="1-add-the-radial-view-solver"></a>1. Adicionar o Solucionador de Exibição Radial

Na janela Hierarquia, selecione o objeto **Cubo** e, em seguida, na janela Inspetor, use o botão **Adicionar componente** para adicionar o objeto de Cubo do componente **Exibição Radial (Script)** .

### <a name="2-configure-the-radial-view-solver"></a>2. Configurar o Solucionador de Exibição Radial

Configure o componente **Manipulador do Solucionador (Script)** :

* Alterar **Tipo de Destino Controlado** para **Articulação da Mão**
* Alterar **Mão Rastreada** para **Direita**
* Alterar **Articulação da Mão Rastreada** para **Pulso**

Configure o componente **Exibição Radial (Script)** :

* Altere a **Direção de Referência** para **Orientada pelo Objeto** e, em seguida, marque a caixa **Orientar para Direção de Referência**
* Altere **Distância Mínima** e **Distância Máxima** para 0

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. Testar o Solucionador de Exibição Radial usando a simulação no editor

Pressione o botão Reproduzir para entrar no modo de Jogo e pressione e segure a barra de espaços para levantar a mão. Mova o cursor do mouse para mover a mão e clique e mantenha o botão esquerdo do mouse pressionado para girar a mão:

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a usar os solucionadores do MRTK para fazer uma interface do usuário intuitiva seguir o usuário. Você também aprendeu a anexar um Solucionador a um objeto do jogo (ou seja, o cubo) para seguir as mãos acompanhadas do usuário. Para saber mais sobre esses e outros solucionadores incluídos no MRTK, acesse o guia [Solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

[Próximo tutorial: 5. Interagir com objetos 3D](mrlearning-base-ch4.md)
