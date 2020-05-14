---
title: 3. Como configurar seu projeto para a realidade misturada
description: Parte 3 de um tutorial para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: b5b5e2de787279602341e60f2bfa29aa05ea9b31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840615"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. Como configurar seu projeto para a realidade misturada

Esta seção orienta você no processo de configuração de seu aplicativo para o desenvolvimento da realidade misturada. 

## <a name="objectives"></a>Objetivos

* Entender como configurar um projeto de realidade misturada com ARSessionConfig, Peão e GameMode

## <a name="configure-the-session"></a>Configurar a sessão

1. No Navegador de Conteúdo, navegue de volta para a pasta **Conteúdo**. Clique em **Adicionar Novo > Diversos > Ativos de Dados**. 

2. Escolha **ARSessionConfig** como a classe e clique em **Selecionar**. Nomeie o ativo como "ARSessionConfig".

![Criar um ativo de dados](images/unreal-uxt/3-createasset.PNG)

3. Clique duas vezes em ARSessionConfig para abri-lo. Um ativo de dados ARSessionConfig contém uma série de configurações úteis de RA, incluindo mapeamento espacial e oclusão. Para obter mais detalhes sobre o ARSessionConfig, dê uma olhada na documentação do Unreal Engine em [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html). Para nosso aplicativo de xadrez, não precisaremos modificar nenhuma configuração, portanto, basta clicar em **Salvar** e retornar à Janela principal. 

![Configuração de sessão de RA](images/unreal-uxt/3-arsessionconfig.PNG)

4. Na barra de ferramentas acima do visor, clique em **Blueprints > Abrir Blueprint de Nível**. O Blueprint de Nível é um blueprint especial que atua como um grafo de eventos global de nível geral. Vamos iniciar uma sessão RA aqui, para que nossa configuração de sessão RA seja aplicada no início do nível.  

5. Arraste o nó de execução saindo de **Evento BeginPlay** e solte-o. Pesquise o nó **Iniciar Sessão de RA**. Clique em **Configuração de Sessão** e selecione o ativo **ARSessionConfig** criado recentemente. Clique **Compilar** e, em seguida, **Salvar**. Volte para a Janela principal.

![Iniciar Sessão de RA](images/unreal-uxt/3-startarsession.PNG)

## <a name="create-a-pawn"></a>Criar um Peão

1.  Na pasta Conteúdo, crie um Blueprint que herde de **DefaultPawn**. No Unreal, um Peão representa o usuário no jogo ou, nesse caso, a experiência do HoloLens 2. Renomeie o novo Peão como "MRPawn" e clique duas vezes no MRPawn para abri-lo. 

![Criar um Peão herdando de DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

2.  Por padrão, o Peão tem um componente de malha e um componente de colisão, já que, na maioria dos projetos do Unreal, os Peões controlados pelo usuário são objetos sólidos que colidem com outros componentes. Nessa situação, como o usuário é o Peão, queremos atravessar hologramas sem gerar colisões. No painel Componentes, selecione o **CollisionComponent**. No painel Detalhes, role para baixo até a seção Colisão e clique na lista suspensa ao lado de Predefinições de Colisão. Altere esse Peão para **NoCollision**. Faça o mesmo para o **MeshComponent**. **Compile** e, em seguida, **Salve** Blueprint. Volte para a Janela principal. 

![Ajustar as Predefinições de Colisão do Peão](images/unreal-uxt/3-nocollision.PNG)

## <a name="create-a-game-mode"></a>Criar um Modo de Jogo

1.  Na pasta Conteúdo do Navegador de Conteúdo, crie um Blueprint com a **Base Modo de Jogo** pai. Nomeie-o como MRGameMode e clique duas vezes para abri-lo. No Unreal, o Modo de Jogo determina um diversas configurações para o jogo ou a experiência, incluindo o peão padrão a ser usado. 

![MRGameMode no Navegador de Conteúdo](images/unreal-uxt/3-gamemode.PNG)

2.  No painel Detalhes, localize a seção Classes. Altere a Classe Peão Padrão de DefaultPawn para **MRPawn** que você acabou de criar. Clique **Compilar** e, em seguida, **Salvar**. Volte para a Janela principal. 

![Definir a Classe Peão Padrão](images/unreal-uxt/3-setpawn.PNG)

3.  A última etapa na configuração de seu projeto é informar ao Unreal para tornar MRGameMode padrão. Vá para **Editar > Configurações de Projetos > Mapas e Modos** na seção (Projetos). Na seção Modos Padrão, clique na lista suspensa e escolha **MRGameMode**. Na seção Mapas Padrão logo abaixo, altere **EditorStartupMap** e **GameDefaultMap** to **Principal**. Dessa forma, quando você fechar o editor e abri-lo novamente, o mapa Principal será selecionado por padrão. Da mesma forma, quando você jogar o jogo, o mapa Principal será o nível que é iniciado. 

![Configurações do projeto – Mapas e Modos](images/unreal-uxt/3-mapsandmodes.PNG)

[Próxima seção: 4. Como tornar sua cena interativa](unreal-uxt-ch4.md)