---
title: 2. Inicializar o projeto e seu primeiro aplicativo
description: Parte 2 de um tutorial para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: fc85f011ff3b186f3b4b5449b4f8ec49f0b6418f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851570"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inicializar o projeto e seu primeiro aplicativo

Esta seção apresenta a você uma introdução à criação de um aplicativo Unreal para o HoloLens 2. 

## <a name="objectives"></a>Objetivos

* Configurar o Unreal para o desenvolvimento no HoloLens
* Importar ativos e configurar a cena

## <a name="create-a-new-unreal-project"></a>Criar um projeto do Unreal

1. Iniciar Unreal Engine

2. Em **Novas Categorias de Projeto**, selecione **Jogos** e clique em Avançar. Selecione um modelo **Em Branco** e clique em Avançar. 

![Selecionar o modelo Em Branco](images/unreal-uxt/2-template.PNG)

3. Nas Configurações do Projeto, escolha **C++, 3D ou 2D escalonável, Mobile/Tablet** e **Nenhum Conteúdo Inicial**. Selecione um local para salvar o projeto e clique em **Criar Projeto**. Isso abrirá os arquivos do C++ em um projeto do Visual Studio e o editor do Unreal. 

![Configurações iniciais do projeto](images/unreal-uxt/2-project-settings.PNG)

4. No canto superior esquerdo, vá para **Editar > Plug-ins**. Em Realidade Aumentada, marque a caixa para habilitar o plug-in do **HoloLens**. Role para baixo até a seção Realidade Virtual e marque a caixa para habilitar o plug-in do **Microsoft Windows Mixed Reality**. Os dois plug-ins são necessários para o desenvolvimento no HoloLens 2. Reinicie o editor. 

![Plug-ins](images/unreal-uxt/2-plugins.PNG)

5. No canto superior esquerdo, vá para **Arquivo > Novo Nível**. Selecione **Nível Vazio**. A cena padrão no visor agora deve estar vazia.

6. Arraste e solte PlayerStart no painel Modos à esquerda, localizado na guia Básico. No painel Detalhes à direita, defina o local como X = 0, Y = 0, Z = 0 para que o usuário inicie na origem quando o aplicativo iniciar.

![Visor com PlayerStart](images/unreal-uxt/2-playerstart.PNG)

7. Arraste um **Cubo** da guia Básico do painel Modos para o visor. No painel Detalhes, defina o local como X = 50, Y = 0, Z = 0 para definir o cubo a 50 cm de distância do jogador no momento do início. Como o cubo padrão é muito grande, altere a escala do cubo para (0,2; 0,2; 0,2). 

8. Você não conseguirá ver o cubo a menos que adicione uma luz à cena. Alterne para a guia **Luzes** no painel Modos e arraste uma **Luz Direcional** até a cena, acima do PlayerStart.

![Visor com luz adicionada](images/unreal-uxt/2-light.PNG)

9.  Pressione o botão **Reproduzir** na barra de ferramentas para ver o cubo no visor! Pressione **ESC** para parar o nível. 

![Um cubo no visor](images/unreal-uxt/2-cube.PNG)

10. Vamos salvar o nível. No canto superior esquerdo, clique em **Arquivo > Salvar Atual**. Dê o nome "Main" ao nível e clique em **Salvar**. 

## <a name="set-up-a-chess-scene"></a>Configurar uma cena de xadrez

1. No Navegador de Conteúdo, clique no ícone em Adicionar Novo para mostrar o painel de fontes. Em seguida, clique em **Adicionar Novo > Nova Pasta** e nomeie a pasta como "ChessAssets". Clique duas vezes nessa pasta para navegar. É aqui que vamos importar os ativos de 3D para nosso conjunto de xadrez.

![Mostrar ou ocultar o painel de fontes](images/unreal-uxt/2-showhidesources.PNG)

2. Baixe o arquivo zip de ativos do [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z). Esse arquivo contém os modelos 3D para um tabuleiro de xadrez e um conjunto de xadrez. Descompacte este arquivo.

3. Na parte superior do Navegador de Conteúdo, clique em **Importar**. Navegue até a pasta que você acabou de descompactar e selecione todos os itens. Essa pasta contém arquivos FBX, que são as malhas do objeto 3D do tabuleiro e das peças de xadrez, bem como arquivos TGA que são os mapas de textura que usaremos para criar materiais para o tabuleiro e as peças. Clique em **Abrir**. 

4. Uma janela de Opções de Importação do FBX será exibida. Na seção **Material**, altere o **Método de Importação de Material** para **Não Criar Material**. Em seguida, clique em **Importar Tudo**.

![Opções em Importar FBX](images/unreal-uxt/2-nocreatemat.PNG)

5. De volta à pasta de Conteúdo, crie uma pasta chamada **Blueprints**. É aí que armazenaremos todos os blueprints, que são ativos especiais que fornecem uma interface baseada em nó para criar novos tipos de Atores e eventos de nível de script. 

6. Clique duas vezes na pasta **Blueprints** para navegar dentro dela e, em seguida, clique com o botão direito do mouse no Navegador de Conteúdo e selecione **Classe de Blueprint**. Clique em **Ator** e nomeie o novo blueprint como "Board". Clique duas vezes em Board para abri-lo. 

![Selecione uma classe pai para seu Blueprint](images/unreal-uxt/2-bpparent.PNG)

![O novo Blueprint Board](images/unreal-uxt/2-bpboard.PNG)

7. No editor de Blueprint, navegue até o painel Componentes e clique em **Adicionar Componente > Cena**. Nomeie a cena criada recentemente como "Root" e, em seguida, clique e arraste Root sobre DefaultSceneRoot. Isso substituirá a raiz da cena padrão e se livrará da esfera no visor. 

![Substituindo a raiz](images/unreal-uxt/2-root.PNG)

8. Clique em **Adicionar Componente** novamente e, desta vez, escolha **Malha Estática**. Nomeie a nova malha estática como "SM_Board". 

![Adicionando uma malha estática](images/unreal-uxt/2-sm-board.PNG)

9. No painel **Detalhes**, localize a seção **Malha Estática** e clique na lista suspensa. Selecione **ChessBoard**. 

![A malha do tabuleiro no visor](images/unreal-uxt/2-sm-board-view.PNG)

10. Ainda no painel **Detalhes**, localize a seção **Materiais** e clique na lista suspensa. Em **Criar Ativo**, selecione **Material**. Nomeie este ativo **M_ChessBoard** e salve-o na pasta **ChessAssets**. 

![Criar um material](images/unreal-uxt/2-newmat.PNG)

11. Clique duas vezes no quadrado ao lado da lista suspensa M_ChessBoard para abrir o material M_ChessBoard recém-criado. No Editor de Material, clique com o botão direito do mouse e procure o nó **Exemplo de Textura**. No painel **Detalhes**, na seção **Base de Textura de Expressão do Material**, clique na lista suspensa e selecione **ChessBoard_Albedo**. Por fim, arraste o pino de saída **RGB** para o pino de Cor Base de **M_ChessBoard**. 

![Definir a cor base](images/unreal-uxt/2-boardalbedomat.PNG)

12. Faça o mesmo mais quatro vezes, vinculando o Exemplo de Textura **ChessBoard_AO** ao pino **Oclusão de Ambiente**, o Exemplo de Textura **ChessBoard_Metal** ao pino **Metálico**, o Exemplo de Textura **ChessBoard_Normal** ao pino **Normal** e o Exemplo de Textura **ChessBoard_Rough** ao pino **Rugosidade**. Clique em **Salvar**. 

![Conectar as texturas restantes](images/unreal-uxt/2-boardmat.PNG)

13. Retorne ao Blueprint **Board**. Você deve ver que o material que você acabou de criar foi aplicado ao Blueprint. Para garantir que o tabuleiro esteja em um tamanho e posição razoáveis depois de colocá-lo em nossa cena, altere a **Escala** do tabuleiro para (0,05; 0,05; 0,05) e a **Rotação** para Z = 90. Na barra de ferramentas na parte superior, clique em **Compilar** e, em seguida, **Salvar**. Volte para a Janela principal. 

![Tabuleiro de xadrez com material aplicado](images/unreal-uxt/2-chessboard.PNG)

14. Agora, vamos excluir o cubo e substituí-lo pelo ator Board recém-criado. No **Contorno do Mundo**, clique com o botão direito do mouse em **Cubo > Editar > Excluir**. Arraste o Board do Navegador de Conteúdo para o visor. Defina o local do tabuleiro como X = 80, Y = 0, Z = -20. 

15. Clique no botão **Reproduzir** para exibir o novo tabuleiro em seu nível. Pressione **ESC** para retornar ao editor. 

16. Agora, seguiremos as mesmas etapas para criar uma peça de xadrez, assim como fizemos com o tabuleiro, desta vez selecionando a malha e o material para a peça de xadrez:

    a) Navegue até a pasta Blueprints no Navegador de Conteúdo e crie uma classe Blueprint do tipo Ator. Nomeie esse ator como "WhiteKing".

    b) Clique duas vezes em WhiteKing para abri-lo. Adicione um novo componente Cena chamado "Root" e use-o para substituir DefaultSceneRoot. 

    c) Adicione um novo componente Malha Estática chamado "SM_King". No painel Detalhes, defina **Malha Estática** como **Chess_King** e **Material** como um novo material chamado **M_ChessWhite**. 

    d) Abra o novo material **M_ChessWhite** e conecte as texturas pertinentes às respectivas entradas de material. 

    ![Criar o material para o rei do xadrez](images/unreal-uxt/2-chesskingmat.PNG)

    e) De volta ao Blueprint **WhiteKing**, altere a **Escala** para (0,05; 0,05; 0,05) e a **Rotação** para Z = 90.

    f) Compile e salve o blueprint e, em seguida, navegue de volta para a janela principal. 

17. Arraste WhiteKing para o visor. No **Contorno do Mundo**, arraste WhiteKing até Board para que WhiteKing agora seja um filho de Board. 

![Contorno do Mundo](images/unreal-uxt/2-child.PNG)

18. No painel **Detalhes**, em **Transformar**, defina o **Local** de WhiteKing como X = -26, Y = 4, Z = 0

19. Clique em **Reproduzir** para ver seu nível. Pressione **ESC** para sair. 

[Próxima seção: 3. Configurar seu projeto para a realidade misturada](unreal-uxt-ch3.md)