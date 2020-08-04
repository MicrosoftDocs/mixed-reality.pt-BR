---
title: Tutoriais de introdução – 6. Como criar interfaces do usuário
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 4eecbd7d292a4d23e0dddc8e9244ed2701a10381
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376618"
---
# <a name="6-creating-user-interfaces"></a>6. Como criar interfaces do usuário

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a criar uma interface do usuário simples usando os pré-fabricados de menu e de botão do MRTK junto com o componente TextMeshPro do Unity. Você também aprenderá a configurar os botões para disparar eventos e adicionar elementos de interface do usuário de dica de ferramenta dinâmica para fornecer ao usuário informações adicionais.

## <a name="objectives"></a>Objetivos

* Saber como organizar botões em uma coleção
* Saber como usar os pré-fabricados de menu do MRTK
* Saber como interagir com hologramas usando os botões e menus da interface do usuário
* Saber como adicionar elementos de texto
* Saber como gerar dicas de ferramentas em objetos dinamicamente

## <a name="creating-a-static-panel-of-buttons"></a>Criar um painel estático de botões

Na janela Hierarquia, clique com o botão direito do mouse no objeto **RoverExplorer** e selecione **Criar Vazio** para adicionar um objeto vazio como um filho do RoverExplorer, nomeie o objeto **Buttons** e configure o componente **Transformar** da seguinte maneira:

* **Posição**: X = -0,6, Y = 0,036, Z = -0,5
* **Rotação**: X = 90, Y = 0, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-1.png)

Na janela do projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-fabricados**, clique e arraste o pré-fabricado **PressableRoundButton** no objeto **Buttons** e, em seguida, clique com o botão direito do mouse no PressableRoundButton e selecione **Duplicar** para criar uma cópia, repita até que você tenha um total de três objetos PressableRoundButton:

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-2.png)

Na janela hierarquia, selecione o objeto **Buttons**, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **GridObjectCollection** e configure-o da seguinte maneira:

* **Tipo de Classificação**: Ordem do Filho
* **Layout**: Horizontal
* **Largura da Célula**: 0,2
* **Âncora**: Centro Esquerda

Em seguida, clique no botão **Atualizar Coleção** para atualizar a posição dos objetos filho do objeto Buttons:

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-3.png)

Na janela Hierarquia, nomeie os botões **Dicas**, **Detalhar** e **Redefinir**.

Para cada botão, selecione o objeto filho **SeeItSayItLabel** > **TextMeshPro** e, em seguida, na janela Inspetor, altere o respectivo texto de componente **TextMeshPro – Texto** para corresponder aos nomes dos botões:

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-4.png)

Quando tiver terminado, recolha os objetos filho do objeto Buttons.

Na janela Hierarquia, selecione o objeto do botão **Dicas** e, na janela Inspetor, configure o evento **OnClick ()** Interativo da seguinte maneira:

* Atribua o objeto **RoverAssembly** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **PlacementHintsController** > **TogglePlacementHints ()** para definir essa função como a ação a ser executada quando o evento for disparado

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-5.png)

Na janela Hierarquia, selecione o objeto do botão **Detalhar** e, na janela Inspetor, configure o evento **OnClick ()** Interativo da seguinte maneira:

* Atribua o objeto **RoverAssembly** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **ExplodedViewController** > **ToggleExplodedView ()** para definir essa função como a ação a ser executada quando o evento for disparado

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-6.png)

Pressione o botão Reproduzir para entrar no Modo de jogo e pressione e segure o botão barra de espaço para ativar a mão; e use o mouse para pressionar o botão **Dicas** para alternar a visibilidade dos objetos de dica de posicionamento:

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-7.png)

e o botão **Detalhar** para ativar e desativar a exibição detalhada:

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a>Como criar um menu dinâmico que segue o usuário

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK** > **SDK** > **UX** > **Pré-fabricados** > **Menus**, clique e arraste o pré-fabricado **NearMenu4x1** para a janela Hierarquia, defina a sua **Posição** de Transformar como X = 0, Y = -0,4, Z = 0 e configure-o da seguinte maneira:

* Verifique se o **Tipo de Destino Rastreado** do componente **SolverHandler** está definido como **Cabeça**
* Marque a caixa de seleção ao lado do componente Solucionador **RadialView** para que ele seja habilitado por padrão

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-1.png)

Na janela Hierarquia, renomeie o objeto para **Menu** e, em seguida, expanda o seu objeto filho **ButtonCollection** para revelar os quatro botões:

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-2.png)

Renomeie o primeiro botão como **Indicador** e, na janela Inspetor, configure o componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Altere o **Texto do Rótulo Principal** para que ele corresponda ao nome do botão
* Atribua o objeto **Indicador** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **GameObject** > **SetActive (bool)** para definir essa função como a ação a ser executada quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **marcada**
* Altere o **Ícone** para o ícone "pesquisar"

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-3.png)

Na janela Hierarquia, selecione o objeto **Indicador** e, na janela Inspetor, desmarque a caixa de seleção ao lado do nome para torná-lo inativo por padrão:

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> Agora, quando o aplicativo é iniciado, o Indicador é desabilitado por padrão e pode ser habilitado pressionando o botão Indicador.

Renomeie o segundo botão como **TapToPlace** e, na janela Inspetor, configure o componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Altere o **Texto do Rótulo Principal** para que ele corresponda ao nome do botão
* Atribua o objeto RoverExplorer > **RoverAssembly** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **TapToPlace** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **marcada**
* Altere o **Ícone** para o ícone "mão com raio"

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-5.png)

Na janela Hierarquia, selecione o objeto **RoverAssembly** e, na janela Inspetor, configure o componente **Tocar para Posicionar (Script)** da seguinte maneira:

* Desmarque a caixa de seleção ao lado do nome para torná-la inativa por padrão
* Na seção de evento **On Placing Started ()** , clique no ícone **+** para adicionar um novo evento:
* Atribua o objeto RoverExplorer > **RoverAssembly** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **TapToPlace** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **desmarcada**

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> Agora, quando o aplicativo é iniciado, a funcionalidade Tocar para Posicionar é desabilitada por padrão e pode ser habilitada pressionando o botão Tocar para Posicionar. Além disso, quando o recurso tocar para posicionar for concluído, ele se desabilitará sozinho.

## <a name="adding-text-to-the-scene"></a>Como adicionar texto à cena

Na janela Hierarquia, clique com o botão direito do mouse no objeto **Tabela** e selecione **Objeto 3D** > **Texto – TextMeshPro** para adicionar um objeto de texto como um filho do objeto Table e, em seguida, na janela Inspetor, configure o componente **Transformação de Retângulo** da seguinte maneira:

* Altere a **Posição Y** para 1
* Altere a **Largura** para 1
* Altere a **Altura** para 1
* Altere a **Rotação X** para 90

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-1.png)

Em seguida, configure o componente **TextMeshPro – Texto** da seguinte maneira:

* Altere o **Texto** para o Explorador do Rover
* Altere o **Estilo da Fonte** para Negrito
* Altere o **Tamanho da Fonte** para 1
* Altere as Configurações Adicionais > **Margens** para 0,03

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a>Como adicionar dicas de ferramenta

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK** > **SDK** > **Recursos** > **UX** > **Pré-fabricados** > **Dica de Ferramenta** para localizar os pré-fabricados de dica de ferramenta:

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-1.png)

Na janela Hierarquia, expanda o objeto RoverExplorer > **RoverParts** e selecione todos os seus objetos filhos de peças do rover. Em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **ToolTipSpawner** e configurá-lo da seguinte maneira:

* Verifique se a caixa de seleção **Foco Habilitado** está marcada para exigir que o usuário olhe a peça para que a dica de ferramenta apareça
* Atribua o pré-fabricado **Dica de Ferramenta de Linha Simples** da janela Projeto para o campo **Pré-fabricado da Dica de Ferramenta**
* Altere as Configurações de Substituição da Dica de Ferramenta > **Modo de Configurações** para **Substituir**
* Altere as Configurações de Substituição da Dica de Ferramenta > **Dinamizar Manualmente a Posição da Localização Y** para **1,5**

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-2.png)

Na janela Hierarquia, selecione a primeira peça do Rover, RoverParts > **Camera_Part** e configure o componente **ToolTipSpawner** da seguinte maneira:

* Altere o **Texto da Dica de Ferramenta** para refletir o nome da peça, ou seja, **Câmera**

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-3.png)

**Repita** essa etapa para cada um dos objetos da peça do Rover para configurar o componente **ToolTipSpawner** da seguinte maneira:

* Para o **Generator_Part**, altere o **Texto da Dica de Ferramenta** para **Gerador**
* Para o **Lights_Part**, altere o **Texto da Dica de Ferramenta** para **Luzes**
* Para o **UHFAntenna_Part**, altere o **Texto da Dica de Ferramenta** para o campo **Antena UHF**
* Para o **Spectrometer_Part**, altere o **Texto da Dica de Ferramenta** para **Espectrômetro**

Pressione o botão Reproduzir para entrar no Modo de jogo e pressione e segure o botão direito do mouse enquanto move o mouse até que o olhar esteja em uma das peças e a dica de ferramenta para essa peça seja exibida:

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a criar uma interface do usuário simples usando os pré-fabricados de menu e de botão fornecidos do MRTK junto com o componente TextMeshPro do Unity e como configurar os botões para disparar eventos quando eles forem pressionados. Você também aprendeu como adicionar elementos de interface do usuário de dica de ferramenta dinâmicos para fornecer ao usuário informações adicionais.

[Próximo tutorial: 7. Interagir com objetos 3D](mr-learning-base-07.md)
