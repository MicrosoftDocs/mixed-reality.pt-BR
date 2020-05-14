---
title: 4. Como tornar sua cena interativa
description: Parte 4 de um tutorial para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 17f7ab1c1126c47e5ac6388d125d45cf3f2c2d87
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851540"
---
# <a name="3-making-your-scene-interactive"></a>3. Como tornar sua cena interativa

Esta seção apresenta o plug-in software livre Ferramentas de UX do Kit de Ferramentas de Realidade Misturada, que oferece um conjunto de ferramentas para tornar sua cena interativa de maneira fácil. Ao final desta seção, as peças de xadrez responderão à entrada do usuário. 

## <a name="objectives"></a>Objetivos

* Incluir o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada em seu projeto
* Adicionar Atores de Interação à Mão ao seu alcance
* Criar e anexar os Manipuladores ao tabuleiro e às peças de xadrez 
* Usar simulação de entrada para validar seu projeto

## <a name="download-the-mixed-reality-toolkit-ux-tools-plugin"></a>Baixar o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada

1.  Clone ou baixe e descompacte a versão mais recente do plug-in Ferramentas de UX do MRTK do [Repositório de ferramentas de UX do GitHub](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)

2.  Na pasta raiz do projeto de xadrez, crie uma pasta chamada "Plugins". Copie o plug-in UXTools descompactado nessa pasta. Reinicie o editor do Unreal. 

![Criar uma pasta de plug-ins do projeto](images/unreal-uxt/4-plugins.PNG)

3.  Após a reinicialização, se você não vir o conteúdo do plug-in UXTools no painel de fontes, talvez seja necessário clicar em **Opções de Exibição > Mostrar Conteúdo do Plug-in**. Você verá que o plug-in UXTools fornece uma pasta de Conteúdo com Ponteiros, Simulação de Entrada e um Botão Simples, bem como uma pasta de Classes de C++ com subpastas separadas por função.  

![Mostrar conteúdo do plug-in](images/unreal-uxt/4-showplugincontent.PNG)

## <a name="spawn-hand-interaction-actors"></a>Gerar Atores de Interação à Mão

1.  Vamos começar gerando Atores de Interação à Mão por meio do MRPawn para que 1) possamos visualizar o MRPawn com um cursor nas pontas dos dedos indicadores do Peão, 2) possamos fornecer eventos de entrada à mão articulada (e, portanto, manipular atores diretamente) por meio do Peão e 3) possamos fornecer eventos de entrada de interação à distância por meio de raios de mão. Abra o Blueprint **MRPawn** e navegue até o **Grafo de Eventos**. 

2.  Arraste o pino de execução do Evento BeginPlay e solte-o para posicionar um novo nó. Selecione o nó **Gerar Ator por meio da Classe**. Clique na lista próxima ao pino **Classe** e pesquise **Ator de Interação à Mão Uxt**. Arraste o pino de execução do nó Ator de Interação à Mão Uxt do SpawnActor, solte-o e procure a função **Definir Mão** contida na classe Ator de Interação à Mão Uxt. Conecte o Valor Retornado do nó SpawnActor ao pino Destino do nó Definir Mão para configurar a mão do Ator de Interação à Mão como **Esquerda**. Gere um segundo **Ator de Interação à Mão Uxt**, dessa vez definindo a mão como **direita**, para que, quando o evento for iniciado, um Ator de Interação à Mão Uxt seja gerado em cada mão. 

![Gerar Atores de Interação à Mão UXT](images/unreal-uxt/4-spawnactor.PNG)

3.  Em seguida, precisamos fornecer aos Atores de Interação à Mão Uxt uma transformação inicial na qual gerar, bem como um proprietário. Arraste o pino de um dos pinos **Gerar Transformação** e solte-o para posicionar um novo nó. Procure o nó **Make Transform**. A transformação inicial realmente não importa, já que os Atores de Interação à Mão vão para as nossas mãos assim que estiverem visíveis (código que já está escrito para nós no plug-in Ferramentas de UX), caso contrário, eles desaparecerão. No entanto, a função SpawnActor requer uma Transformação como entrada para evitar um erro de compilador, portanto, vamos deixar os valores padrão em Make Transform como estão. Arraste o **Valor Retornado** de Make Transform para a Transformação de Gerar Ator de Interação da outra mão. 

4.  Clique na **seta para baixo** na parte inferior de ambos os nós SpawnActor para revelar o pino **Proprietário**. Arraste o pino de um dos pinos **Proprietário** e solte-o para posicionar um novo nó. Pesquise por "self" e selecione a variável **Get a reference to self**. Crie um vínculo entre o nó de referência do objeto Self e o outro pino do Proprietário do Ator de Interação à Mão. Se quiser, arraste os nós para deixar seu Blueprint mais legível. **Compile**, **salve** e retorne para a Janela principal. 

![Configuração de Ator de Interação à Mão UXT completa](images/unreal-uxt/4-fingerptrs.PNG)

Para obter mais informações sobre o Ator de Interação à Mão fornecido no plug-in Ferramentas de UX do MRTK, confira a [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html) oficial.

## <a name="attach-manipulators"></a>Anexar Manipuladores

1.  Em seguida, anexaremos os Manipuladores aos nossos Atores tabuleiro de xadrez e rei. Um Manipulador é um componente que responde à entrada de mão articulada e pode ser agarrado, girado e transladado; ao aplicar a transformação do Manipulador na de um ator, os Atores poderão ser manipulados diretamente. 

2.  Abra o Blueprint Board. No painel **Componentes**, clique em **Adicionar Componente** e pesquise **Manipulador Genérico Uxt**. No painel Detalhes, você encontrará uma seção intitulada **Manipulador Genérico** em que é possível definir se deseja habilitar a manipulação com uma ou duas mãos, o modo de rotação e a suavização. Selecione os modos que quiser e, em seguida, **Compile** e **Salve** o Board. 

![Adicionar manipulador genérico](images/unreal-uxt/4-addmanip.PNG)

![Definir o modo](images/unreal-uxt/4-setrotmode.PNG)

3.  Repita as etapas acima para o Ator WhiteKing.

Para obter mais informações sobre os Componentes do Manipulador fornecidos no plug-in Ferramentas de UX do MRTK, visite a [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html) oficial.

## <a name="test-out-your-scene-with-simulated-hands"></a>Testar a cena com mãos simuladas

1.  Na Janela principal, pressione **Reproduzir**. Você verá duas mãos de malha fornecidas pelo plug-in Ferramentas de UX do MRTK, com raios de mão que se estendem de cada uma das palmas das mãos! 

![Mãos simuladas no visor](images/unreal-uxt/4-handsim.PNG)

2.  Para controlar a **mão direita**, mantenha o botão **ALT esquerdo** pressionado. Mova o mouse para mover a mão. Role com o **botão de rolagem do mouse** para mover a mão **para frente** ou **para trás**. Clique com o botão esquerdo do mouse para **pinçar**, clique com o botão do meio do mouse para **cutucar**.

3.  Para controlar a **mão esquerda**, mantenha pressionado o botão **Shift esquerdo**. Os controles para mover a mão esquerda são os mesmos do lado direito. 

4.  Agora, tente usar as mãos simuladas para pegar, mover e posicionar o rei branco do xadrez. Você também pode manipular o tabuleiro! Experimente com a interação próxima e à distância. Observe que, quando as mãos ficam próximas o suficiente para pegar o quadro e o rei diretamente, o raio de mão desaparece e é substituído por um cursor de dedo na ponta do indicador. 

Para obter mais informações sobre o recurso de mãos simuladas fornecido pelo plug-in Ferramentas de UX do MRTK, visite a [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html) oficial.

[Próxima seção: 5. Como adicionar um botão e redefinir locais de peças](unreal-uxt-ch5.md)