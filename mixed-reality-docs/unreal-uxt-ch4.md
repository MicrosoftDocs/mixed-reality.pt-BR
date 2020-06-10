---
title: 4. Como tornar sua cena interativa
description: Parte 4 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: a9de5755ab86c96322a8d50fecd7ba2cdea866d3
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330213"
---
# <a name="4-making-your-scene-interactive"></a>4. Como tornar sua cena interativa

## <a name="overview"></a>Visão geral

No tutorial anterior, você adicionou um ARSession, peão e modo de jogo para concluir a configuração de realidade misturada para o aplicativo de xadrez. Esta seção concentra-se no plug-in de software livre [Ferramentas de UX do Kit de Ferramentas de Realidade Misturada](https://github.com/microsoft/MixedReality-UXTools-Unreal), que oferece ferramentas para tornar sua cena interativa. Ao final desta seção, você poderá mover as peças de xadrez com base na entrada do usuário. 

## <a name="objectives"></a>Objetivos

* Como baixar o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada 
* Como adicionar Atores de Interação à Mão às pontas dos seus dedos
* Como criar e adicionar manipuladores a objetos na cena
* Como usar simulação de entrada para validar o projeto

## <a name="downloading-the-mrtk-ux-tools-plugin"></a>Como baixar o plug-in de Ferramentas de UX do MRTK
Antes de começar a trabalhar com a entrada do usuário, você precisará adicionar o plug-in ao projeto.

1.  Clone ou baixe a versão mais recente do plug-in Ferramentas de UX do MRTK do [Repositório de ferramentas de UX do GitHub](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases) e descompacte o arquivo.

2.  Na pasta raiz do projeto, crie uma pasta chamada **Plugins**. Copie o plug-in UXTools descompactado para essa pasta e reinicie o editor Unreal. 

![Criar uma pasta de plug-ins do projeto](images/unreal-uxt/4-plugins.PNG)

3.  O plug-in UXTools fornece uma pasta Conteúdo com subpastas para **Ponteiros**, **Simulação de Entrada** e um **Botão Simples**, bem como uma pasta de Classes de C++ separadas por função.  

> [!NOTE]
> Se você não vir a seção **Conteúdo do UXTools** no **Navegador de Conteúdo**, clique em **Exibir Opções > Mostrar Conteúdo do Plug-in**. 

![Mostrar conteúdo do plug-in](images/unreal-uxt/4-showplugincontent.PNG)

Com o plug-in instalado com segurança, você está pronto para começar a usar as ferramentas que ele tem a oferecer, começando com os atores de interação à mão.

## <a name="spawning-hand-interaction-actors"></a>Como gerar Atores de Interação à Mão
A interação à mão com elementos de UX é executada com Atores de Interação à Mão, que criam e orientam os ponteiros e visuais para interações próximas e distantes.
- As *interações próximas* são executadas apertando os elementos entre o dedo indicador e o polegar ou tocando nesses elementos com a ponta de um dedo. 
- As *interações distantes* são executadas apontando um raio da mão virtual a um elemento e pressionando o indicador e o polegar juntos.

Em nosso caso, adicionar um Ator de Interação Manual a **MRPawn** vai:
- Adicionar um cursor às pontas dos dedos indicadores do peão.
- Fornecer eventos de entrada com a mão articulada, que podem ser manipulados por meio do peão.
- Permita eventos de entrada de interação distante por meio de raios de mão, que se estendem das palmas das mãos virtuais.

Para impulsionar esses conceitos, você é incentivado a ler a [documentação](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.8.x/Docs/HandInteraction.md) sobre as interações de mão antes de continuar. 

Quando você estiver pronto, abra o Blueprint **MRPawn** e navegue até o **Grafo de Eventos**. 

1. Arraste o marcador de execução do **Evento BeginPlay** e solte-o para criar um nó no local desejado. 
    * Selecione **Gerar Ator Com Base em Classe**, clique na lista suspensa próxima ao marcador **Classe** e pesquise por **Ator de Interação à Mão Uxt**. 

2. Arraste o marcador de execução do nó **Ator de Interação à Mão Uxt do SpawnActor**, solte-o e procure a função **Definir Mão** na classe **Ator de Interação à Mão Uxt**. 
    * Conecte o **Valor Retornado** do nó **SpawnActor** ao marcador **Destino** do nó **Definir Mão**. Isso configura a mão do Ator de Interação à Mão como **Esquerda**. 

3. Gera um segundo **Ator de Interação à Mão Uxt**, desta vez definindo a mão como **Direita**. Quando o evento for iniciado, um Ator de Interação à Mão Uxt será gerado em cada mão. 

Seu **Grafo do Eventos** deve corresponder à seguinte captura de tela:

![Gerar Atores de Interação à Mão UXT](images/unreal-uxt/4-spawnactor.PNG)

Ambos os Atores de Interação à Mão Uxt precisam de proprietários e locais de transformação inicial. A transformação inicial não importa, pois os Atores de Interação à Mão passarão às mãos virtuais assim que estiverem visíveis (esse comportamento está incluído no plug-in de Ferramentas de UX). No entanto, a função `SpawnActor` requer uma entrada de Transformação para evitar um erro de compilador, então você usará os valores padrão. 

1. Arraste o marcador de um dos marcadores **Gerar Transformação** e solte-o para criar um nó no local desejado. 
    * Procure o nó **Efetuar Transformação** e, em seguida, arraste o **Valor Retornado** para o pino **Gerar Transformação** da outra mão para que ambos os nós **SpawnActor** sejam conectados. 

3.  Clique na **seta para baixo** na parte inferior de ambos os nós **SpawnActor** para revelar o marcador **Proprietário**.    
    * Arraste o pino de um dos pinos **Proprietário** e solte-o para posicionar um novo nó. 
    * Pesquise por **próprio** e selecione a variável **obter uma referência a si próprio** e, em seguida, crie um link entre o nó de referência do objeto **Próprio** e o marcador **Proprietário** do outro Ator de Interação à Mão. 
    * **Compile**, **salve** e retorne para a Janela principal. 

Verifique se as conexões correspondem à captura de tela a seguir, mas fique à vontade para arrastar os nós para tornar seu Blueprint mais legível

![Configuração de Ator de Interação à Mão UXT completa](images/unreal-uxt/4-fingerptrs.PNG) 

Você pode encontrar mais informações sobre o Ator de Interação à Mão fornecido no plug-in Ferramentas de UX do MRTK na [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html).

Agora, as mãos virtuais no projeto têm uma forma de selecionar objetos, mas ainda não podem manipulá-los. Sua última tarefa antes de testar o aplicativo é adicionar componentes de Manipulador aos atores na cena.

## <a name="attaching-manipulators"></a>Como anexar manipuladores

Um manipulador é um componente que responde à entrada de mão articulada e pode ser pego, girado e traduzido. Aplicar a transformação do Manipulador a uma transformação de Atores permite a manipulação direta do Ator. 

1. Abra o blueprint **Tabuleiro**, clique em **Adicionar Componente** e pesquise por **Manipulador Genérico Uxt** no painel **Componentes**.

![Adicionar manipulador genérico](images/unreal-uxt/4-addmanip.PNG)

2. Expanda a seção **Manipulador Genérico** no painel **Detalhes**. Nela, você pode definir a manipulação de uma ou duas mãos, o modo de rotação e a suavização. Selecione os modos que quiser e, em seguida, **Compile** e **Salve** o Board. 

![Definir o modo](images/unreal-uxt/4-setrotmode.PNG)

3. Repita as etapas acima para o Ator **WhiteKing**.

É possível encontrar mais informações sobre os Componentes do Manipulador fornecidos no plug-in Ferramentas de UX do MRTK na [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html).

## <a name="testing-the-scene"></a>Como testar a cena
Boa notícia para todos! Você está pronto para testar o aplicativo com as novas mãos virtuais e entrada do usuário dele. Pressione **Jogar** na Janela Principal e você verá duas mãos de malha fornecidas pelo plug-in Ferramentas de UX do MRTK, com raios de mão que se estendem da palma de cada uma das mãos. Você pode controlar as mãos e as respectivas interações da seguinte maneira:
- Mantenha pressionada a tecla **Alt esquerda** para controlar a **mão esquerda** e a tecla **Shift esquerda** para controlar a **mão direita**. 
- Mova o cursor do mouse para mover a mão e use o **botão de rolagem do mouse** para mover a mão **para frente** ou **para trás**. 
- Clique com o botão esquerdo do mouse para **pinçar**, clique no botão do meio do mouse para **cutucar**. 

![Mãos simuladas no visor](images/unreal-uxt/4-handsim.PNG)

Tente usar as mãos simuladas para pegar, mover e posicionar o rei branco do xadrez e manipular o tabuleiro! Experimente com a interação próxima e à distância. Observe que, quando as mãos ficam próximas o suficiente para pegar o quadro e o rei diretamente, o raio de mão desaparece e é substituído por um cursor na ponta do dedo indicador. 

Você pode obter mais informações sobre o recurso de mãos simuladas fornecido pelo plug-in Ferramentas de UX do MRTK na [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html).

Agora que suas mãos virtuais podem interagir com objetos, você está pronto para passar para o próximo tutorial e adicionar interfaces do usuário e eventos.

[Próxima seção: 5. Como adicionar um botão e redefinir locais de peças](unreal-uxt-ch5.md)
