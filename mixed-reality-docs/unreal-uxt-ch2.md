---
title: 2. Inicializar o projeto e seu primeiro aplicativo
description: Parte 2 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 1fce9c34b1d31c56eb628979089399926f3cbf51
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376498"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inicializar o projeto e seu primeiro aplicativo

## <a name="overview"></a>Visão geral

Neste primeiro tutorial, você começará com um novo aplicativo do Unreal para o HoloLens 2. Isso incluirá adicionar o plug-in do HoloLens, criar e iluminar um nível e populá-lo com um jogo de tabuleiro e uma peça de xadrez. Você usará ativos pré-criados para a peça de xadrez 3D e materiais de objeto, então não será necessário fazer a modelagem de nada do zero. No final deste tutorial, você terá uma tela em branco que está pronta para a realidade misturada.

Antes de continuar, verifique se você atende a todos os pré-requisitos da página [Introdução](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1).

## <a name="objectives"></a>Objetivos
* Como configurar um projeto do Unreal para desenvolvimento no HoloLens
* Como importar ativos e configurar um cenário
* Como criar Atores e eventos em nível de script com blueprints

## <a name="creating-a-new-unreal-project"></a>Como criar um projeto do Unreal
A primeira coisa que você precisa é de um projeto com o qual trabalhar. Se esta é a primeira vez que você empacota um aplicativo do Unreal para o HoloLens, [baixe os arquivos de suporte](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) do Epic Launcher.

1. Iniciar Unreal Engine

2. Selecione **Jogos** em **Novas Categorias de Projeto** e clique em **Avançar**. 

![Selecionar um modelo de projeto de jogos](images/unreal-uxt/2-gamestemplate.png)

3. Selecione o modelo **Em Branco** e clique em **Avançar**. 

![Selecionar o modelo Em Branco](images/unreal-uxt/2-template.PNG)

4. Defina **C++** , **3D ou 2D Escalonável, Celular/Tablet** e **Nenhum Conteúdo Inicial** como as **Configurações de Projeto** e escolha uma localização de salvamento e clique em **Criar Projeto**. 

> [!NOTE]
> Você precisará selecionar um projeto C++ em vez de um projeto Blueprint para criar o plug-in das Ferramentas de UX, que você vai configurar mais adiante na seção 4.

![Configurações iniciais do projeto](images/unreal-uxt/2-project-settings.PNG)

O projeto deve ser aberto automaticamente no editor Unreal, o que significa que você está pronto para a próxima seção.

## <a name="enabling-required-plugins"></a>Como habilitar os plugins necessários
Antes de começar a adicionar objetos à cena, você precisará habilitar dois plug-ins.

1. Abra **Editar > Plug-ins** e selecione **Realidade Aumentada** na lista de opções internas. 
    * Role para baixo até **HoloLens** e marque **Habilitado**. 

![Como habilitar plugins do HoloLens](images/unreal-uxt/2-plugins.PNG)

2. Selecione **Realidade Virtual** na lista de opções internas. 
    * Role a página para baixo até **Microsoft Windows Mixed Reality**, marque a opção **Habilitado** e reinicie o editor. 

![Como habilitar o plug-in do Windows Mixed Reality](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> Os dois plug-ins são necessários para o desenvolvimento no HoloLens 2.

Com isso feito, o nível vazio estará pronto para ter companhia.

## <a name="creating-a-level"></a>Criar um nível
A sua próxima tarefa é criar uma configuração de jogador simples com um ponto de partida e um cubo para referência e escala.

1. Selecione **Arquivo > Novo Nível** e escolha **Nível Vazio**. A cena padrão no visor agora deve estar vazia.

2. Selecione **Básico** na guia **Modos** e arraste **PlayerStart** para a cena. 
    * Defina **Localização** como **X = 0**, **Y = 0** e **Z = 0** na guia **Detalhes**. Isso define a localização do usuário no centro da cena quando o aplicativo é iniciado.

![Visor com PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. Arraste um **Cubo** da guia **Básico** para a cena. 
    * Defina **Localização** como **X = 50**, **Y = 0** e **Z = 0**. Isso posiciona o cubo a 50 cm do jogador na hora de início. 
    * Altere **Escala** para **X = 0,2**, **Y = 0,2** e **Z = 0,2** para diminuir o cubo. 

Você não poderá ver o cubo, a menos que adicione uma luz à sua cena, que é sua última tarefa antes de testar a cena em questão.

4. Alterne para a guia **Luzes** no painel **Modos** e arraste uma **Luz Direcional** até a cena. Posicione a luz acima **PlayerStart** para que você possa vê-la.

![Visor com luz adicionada](images/unreal-uxt/2-light.PNG)

5. Vá para **Arquivo > Salvar Atual**, nomeie seu nível **Principal** e clique em **Salvar**. 

Com a cena preparada, pressione **Jogar** na barra de ferramentas para ver o cubo em ação! Quando tiver terminado de admirar seu trabalho, pressione **Esc** para interromper o aplicativo.

![Um cubo no visor](images/unreal-uxt/2-cube.PNG)

Agora que a cena está configurada, você pode começar a adicionar o tabuleiro de xadrez e a peça para completar o ambiente do aplicativo.

## <a name="importing-assets"></a>Como importar ativos
A cena está parecendo um tanto vazia no momento, mas você corrigirá isso importando os ativos prontos para o projeto.

1. Baixe e descompacte a pasta de ativos do [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z).

2. Clique em **Adicionar Novo > Nova Pasta** do **Navegador de Conteúdo** e nomeie-o como **ChessAssets**. 
    * Clique duas vezes na nova pasta: é nela que você importará os ativos 3D.

![Mostrar ou ocultar o painel de fontes](images/unreal-uxt/2-showhidesources.PNG)

3. Clique em **Importar** do **Navegador de Conteúdo**, selecione todos os itens na pasta de ativos descompactados e clique em **Abrir**. 
    * Essa pasta contém as malhas de objetos 3D para o tabuleiro de xadrez e as peças no formato FBX, bem como os mapas de textura no formato TGA que você usará para os materiais.  

4. Quando a janela Opções de Importação do FBX for exibida, expanda a seção **Material** e altere **Método de Importação de Material** para **Não Criar o Material**.
    * Clique em **Importar Tudo**.

![Opções em Importar FBX](images/unreal-uxt/2-nocreatemat.PNG)

Isso é tudo o que você precisa fazer com relação aos ativos. Seu próximo conjunto de tarefas é criar os blocos de construção do aplicativo com blueprints.

## <a name="adding-blueprints"></a>Como adicionar blueprints

1. Clique em **Adicionar Novo > Nova Pasta** no **Navegador de Conteúdo** e nomeie-o como **Navegador de Conteúdo**. 

> [!NOTE]
> Se você não está familiarizado com [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), saiba que eles são ativos especiais que fornecem uma interface baseada em nó para criação de tipos de Atores e eventos de nível de script. 

2. Clique duas vezes na pasta **Blueprints**, depois clique com o botão direito do mouse e selecione **Classe de Blueprint**.         
    * Selecione **Ator** e nomeie o novo blueprint como **Tabuleiro**. 

![Selecione uma classe pai para seu Blueprint](images/unreal-uxt/2-bpparent.PNG)

O novo blueprint **Tabuleiro** agora aparece na pasta **Blueprints**, conforme mostrado na captura de tela a seguir. 

![O novo Blueprint Board](images/unreal-uxt/2-bpboard.PNG)

Você está pronto para começar a adicionar materiais aos objetos criados.

## <a name="working-with-materials"></a>Como trabalhar com materiais
Os objetos que você criou são no padrão cinza, o que não os deixa com uma aparência muito divertida. Adicionar materiais e malhas a seus objetos é o último conjunto de tarefas neste tutorial.

1. Clique duas vezes em **Painel** para abrir o editor de blueprints. 

2. Clique em **Adicionar Componente > Cena** no painel **Componentes** e nomeie-o como **Root**. Observe que **Root** aparece como um filho de **DefaultSceneRoot** na captura de tela abaixo:

![Substituindo a raiz](images/unreal-uxt/2-root-blueprint.PNG)


3. Clique e arraste **Root** para **DefaultSceneRoot** para substituí-lo e livrar-se da esfera no visor. 

![Substituindo a raiz](images/unreal-uxt/2-root.PNG)


4. Clique em **Adicionar Componente > Malha Estática** no painel **Componentes** e nomeie-o como **SM_Board**. Ele será exibido como um objeto filho em **Root**.

![Adicionando uma malha estática](images/unreal-uxt/2-sm-board.PNG)

4. Clique em **SM_Board**, role para baixo até a seção **Malha Estática** do painel **Detalhes** e selecione **ChessBoard** na lista suspensa. 

![A malha do tabuleiro no visor](images/unreal-uxt/2-sm-board-view.PNG)

5.  Ainda no painel **Detalhes**, expanda a seção **Materiais** e clique em **Criar Ativo > Material** na lista suspensa. 
    * Nomeie o material **M_ChessBoard** e salve-o na pasta **ChessAssets**. 

![Criar um material](images/unreal-uxt/2-newmat.PNG)

6.  Clique duas vezes na imagem do material **M_ChessBoard** para abrir o editor de material. 

![Abrir editor de material](images/unreal-uxt/2-material-editor.PNG)

7. No Editor de Material, clique com o botão direito do mouse e procure **Exemplo de Textura**. 
    * Expanda a seção **Base de Textura de Expressão do Material** no painel **Detalhes** e defina **Textura** para **ChessBoard_Albedo**. 
    * Arraste o marcador de saída **RGB** para o marcador de Cor Base de **M_ChessBoard**. 

![Definir a cor base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  Repita a etapa anterior quatro mais vezes para criar mais quatro nós **Exemplo de Textura** com as seguintes configurações:
    * Defina **Textura** como **ChessBoard_AO** e vincule o **RGB** ao marcador **Oclusão Ambiente**.
    * Defina **Textura** como **ChessBoard_Metal** e vincule o **RGB** ao marcador **Metálico**. 
    * Defina **Textura** como **ChessBoard_Normal** e vincule o **RGB** ao marcador **Normal**.
    * Defina **Textura** como **ChessBoard_Rough** e vincule o **RGB** ao marcador **Aspereza**. 
    * Clique em **Salvar**. 

![Conectar as texturas restantes](images/unreal-uxt/2-boardmat.PNG)

Verifique se a configuração do material está parecida com a captura de tela acima antes de continuar.

## <a name="populating-the-scene"></a>Como popular a cena
Se você retornar ao blueprint **Tabuleiro**, verá que o material que acabou de criar foi aplicado. Tudo o que falta fazer é configurar a cena! Primeiro, altere as propriedades a seguir para assegurar que o tabuleiro seja de um tamanho razoável e esteja inclinado corretamente quando posicionado na cena:
1.  Defina **Escala** como **(0,05, 0,05, 0,05)** e **Rotação Z** como **90**. 
    * Clique em **Compilar** na barra de ferramentas superior e depois em **Salvar**, então volte para a Janela principal. 

![Tabuleiro de xadrez com material aplicado](images/unreal-uxt/2-chessboard.PNG)

2.  Clique com o botão direito do mouse em **Cubo > Editar > Excluir** e arraste **Tabuleiro** do **Navegador de Conteúdo** para o visor. 
    * Defina **Localização** como **X = 80**, **Y = 0** e **Z = -20**. 

3.  Clique no botão **Jogar** para exibir o novo tabuleiro no nível. Pressione **ESC** para retornar ao editor. 

Agora você seguirá as mesmas etapas para criar uma peça de xadrez, do mesmo modo que você fez com o tabuleiro:

1. Acesse a pasta **Blueprints**, clique com o botão direito do mouse e selecione **Classe de Blueprint**, depois escolha **Ator**. Nomeie esse ator como **WhiteKing**.

2. Clique duas vezes em **WhiteKing** para abri-lo no Editor do Blueprint, clique em **Adicionar Componente > Cena** e nomeie-o como **Root**. 
    * Arraste e solte **Root** em **DefaultSceneRoot** para substituí-lo. 

3. Clique em **Adicionar Componente > Malha Estática** e nomeie-o como **SM_King**. 
    * No painel Detalhes, defina **Malha Estática** como **Chess_King** e **Material** como um novo material chamado **M_ChessWhite**. 

4. Abra **M_ChessWhite** no Editor de material e conecte os nós de **Exemplo de Textura** a seguir ao seguinte:
    * Defina **Textura** como **ChessWhite_AO** e vincule o **RGB** ao marcador **Oclusão Ambiente**.
    * Defina **Textura** como **ChessWhite_Metal** e vincule o **RGB** ao marcador **Metálico**. 
    * Defina **Textura** como **ChessWhite_Normal** e vincule o **RGB** ao marcador **Normal**.
    * Defina **Textura** como **ChessWhite_Rough** e vincule o **RGB** ao marcador **Aspereza**. 
    * Clique em **Salvar**. 

Verifique se o material **M_ChessKing** tem aparência semelhante à da imagem a seguir antes de continuar.

![Criar o material para o rei do xadrez](images/unreal-uxt/2-chesskingmat.PNG)

Você está quase lá, falta apenas adicionar a nova peça de xadrez à cena: 

1. Abra o blueprint **WhiteKing**, altere a **Escala** para **(0,05; 0,05; 0,05)** e a **Rotação em Z** para **90**.
    * Compile e salve o blueprint e, em seguida, retorne para a Janela principal. 

2.  Arraste **WhiteKing** para o visor, alterne para o painel **Esboço do Mundo** e arraste **WhiteKing** para o **Tabuleiro** para torná-lo um objeto filho.

![Contorno do Mundo](images/unreal-uxt/2-child.PNG)

3.  No painel **Detalhes**, em **Transformar**, defina a **Localização** de **WhiteKing** como **X = -26**, **Y = 4** e **Z = 0**.

Tudo concluído! Clique em **Jogar** para ver o nível preenchido em ação e pressione **Esc** quando estiver pronto para sair. Este tutorial abordou muito conteúdo sobre a criação de um projeto simples, mas seu projeto está pronto para passar para a próxima parte da série: configuração para a realidade misturada. 

[Próxima seção: 3. Configurar seu projeto para a realidade misturada](unreal-uxt-ch3.md)
