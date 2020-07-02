---
title: 3. Como configurar seu projeto para a realidade misturada
description: Parte 3 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: f79985b2ce9e26971c23acf36a3538bf7f3c166e
ms.sourcegitcommit: ff0e89b07d0b4a945967d64c5b8845a21dc5f476
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84879552"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. Como configurar seu projeto para a realidade misturada

## <a name="overview"></a>Visão geral

No tutorial anterior, você passou tempo configurando o projeto de aplicativo de xadrez. Esta seção vai orientá-lo pela configuração do aplicativo para o desenvolvimento de realidade misturada, o que significa adicionar uma sessão de RA. Para essa tarefa, você usará um ativo de dados ARSessionConfig que tem muitas configurações úteis de RA, como mapeamento espacial e oclusão. Se você quiser se aprofundar, a documentação do Unreal Engine tem mais detalhes sobre o ativo [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) e a classe [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).

## <a name="objectives"></a>Objetivos
* Como trabalhar com configurações de RA do Unreal Engine 
* Como usar um ativo de dados do ARSessionConfig
* Como configurar um peão e um modo de jogo

## <a name="adding-the-session-asset"></a>Como adicionar o ativo de sessão
As sessões de RA no Unreal não acontecem espontaneamente. Para usar uma sessão, você precisa de um ativo de dados do ARSessionConfig com o qual trabalhar, que é sua próxima tarefa:

1. Clique em **Adicionar Novo > Diversos > Ativo de Dados** no **Navegador de Conteúdo**. Verifique se você está no nível raiz da pasta **Conteúdo**. 
    * Selecione **ARSessionConfig**, clique em **Selecionar** e nomeie o ativo **ARSessionConfig**.

![Criar um ativo de dados](images/unreal-uxt/3-createasset.PNG)

3. Clique duas vezes em **ARSessionConfig** para abri-lo, deixe todas as configurações padrão e clique em **Salvar**. Volte para a Janela principal. 

![Configuração de sessão de RA](images/unreal-uxt/3-arsessionconfig.PNG)

Com isso feito, a próxima etapa será verificar se a sessão de RA começa quando o nível é carregado e se ela é interrompida quando o nível é encerrado. O Unreal tem um tipo especial de blueprint chamado **Blueprint de Nível**, que atua como um grafo de eventos global em todo esse nível. Conectar o ativo ARSessionConfig no **Blueprint de Nível** garante que a sessão de RA será disparada exatamente quando o jogo começar.

1. Clique em **Blueprints > Abrir Blueprint de Nível** na barra de ferramentas do editor: 

![Abrir Blueprint de Nível](images/unreal-uxt/3-level-blueprint.PNG)

5. Arraste o nó de execução (ícone de seta para a esquerda) saindo de **Evento BeginPlay** e solte-o. Procure o nó **Iniciar Sessão de RA** e pressione ENTER.  
    * Clique na lista suspensa **Selecionar Ativo** em **Configuração de Sessão** e escolha o ativo **ARSessionConfig**. 

![Iniciar Sessão de RA](images/unreal-uxt/3-start-ar-session.PNG)

6. Clique com o botão direito do mouse em qualquer lugar do EventGraph e crie um nó **EndPlay de Evento**. Arraste o pino de execução e solte-o. Procure um nó **Interromper Sessão de RA** e pressione ENTER. Se a sessão de RA não for interrompida quando o nível for encerrado, alguns recursos poderão parar de funcionar se você reiniciar o aplicativo durante o streaming para um headset. 
    * Escolha **Compilar**, depois **Salvar** e retorne para a Janela principal.

![Interromper Sessão de RA](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a>Criar um Peão
Neste ponto, o projeto ainda precisa de um objeto de jogador. No Unreal, um **Peão** representa o usuário no jogo, mas neste caso, será a experiência do HoloLens 2.

1. Clique em **Adicionar Novo > Classe de Blueprint** na pasta **Conteúdo** e expanda a seção **Todas as Classes** na parte inferior. 
    * Pesquise por **DefaultPawn**, clique em **Selecionar** e clique duas vezes no ativo para abrir. 

![Criar um Peão herdando de DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> Por padrão, os Peões têm componentes de malha e colisão. Na maioria dos projetos do Unreal, os Peões são objetos sólidos que podem colidir com outros componentes. Já que o peão e o usuário são a mesma coisa em realidade misturada, você deseja ser capaz de passar pelos hologramas sem nenhuma colisão. 

2. Selecione **CollisionComponent** no painel **Componentes** e role para baixo até a seção **Colisão** do painel **Detalhes**. 
    * Clique na lista suspensa de **Predefinições de Colisão** e altere o valor para **NoCollision**. 
    * Faça o mesmo para o **MeshComponent** e, em seguida, escolha **Compilar** e **Salvar** o Blueprint. 

![Ajustar as Predefinições de Colisão do Peão](images/unreal-uxt/3-nocollision.PNG)

Com seu trabalho aqui terminado, retorne para a Janela principal.

## <a name="create-a-game-mode"></a>Criar um Modo de Jogo
A última peça do quebra-cabeça da configuração da realidade misturada é o Modo de Jogo. O Modo de Jogo determina um diversas configurações para o jogo ou a experiência, incluindo o peão padrão a ser usado.

1.  Clique em **Adicionar Novo > Classe de Blueprint** na pasta **Conteúdo** e expanda a seção **Todas as Classes** na parte inferior. 
    * Pesquise por **Base do Modo de Jogo**, nomeie-a como **MRGameMode** e clique duas vezes para abri-la. 

![MRGameMode no Navegador de Conteúdo](images/unreal-uxt/3-gamemode.PNG)

2.  Vá para a seção **Classes** no painel **Detalhes** e altere a **Classe de Peão Padrão** para **MRPawn**. 
    * Escolha **Compilar**, depois **Salvar** e retorne para a Janela principal. 

![Definir a Classe Peão Padrão](images/unreal-uxt/3-setpawn.PNG)

3.  Selecione **Editar > Configurações de Projetos** e clique em **Mapas e Modos** na lista à esquerda. 
    * Expanda **Modos Padrão** e altere **Modo de Jogo Padrão** para **MRGameMode**. 
    * Expanda **Mapas Padrão** e altere **EditorStartupMap** e **GameDefaultMap** para **Principal**. Dessa forma, quando você fechar o editor e abri-lo novamente ou jogar o jogo, o mapa Principal estará selecionado por padrão.

![Configurações do projeto – Mapas e Modos](images/unreal-uxt/3-mapsandmodes.PNG)

Com o projeto totalmente configurado para realidade misturada, você está pronto para passar para o próximo tutorial e começar a adicionar a entrada do usuário ao cenário. 

[Próxima seção: 4. Como tornar sua cena interativa](unreal-uxt-ch4.md)