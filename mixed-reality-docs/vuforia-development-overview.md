---
title: Usando o Vuforia com o Unity
description: Aproveite o Vuforia para criar aplicativos de realidade mista do Windows no Unity.
author: thetuvix
ms.author: alexturn
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia, marcadores, coordenadas, quadro de referência, acompanhamento
ms.openlocfilehash: 0ab87a6262cbe74fd116fdc0a7045961bf8695d9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437140"
---
# <a name="using-vuforia-engine-with-unity"></a>Usando o mecanismo do Vuforia com o Unity

O Vuforia Engine traz um recurso importante para o HoloLens – o poder de conectar experiências do AR a imagens e objetos específicos no ambiente. Você pode usar essa capacidade para sobrepor instruções passo a passo guiadas sobre máquinas para a empresa industrial ou adicionar recursos e experiências digitais a um produto ou jogo físico. 

Para obter maior flexibilidade ao desenvolver experiências de AR, o Vuforia Engine oferece uma ampla gama de recursos e destinos. Um dos nossos mais novos recursos, Vuforia Model targets, é um recurso importante para usos comerciais e industriais. Os destinos de modelo permitem que os aplicativos reconheçam objetos físicos, como computadores, automóveis ou brinquedos, e os acompanham com base em um modelo CAD ou 3D digital. Para usos industriais, esse recurso pode fornecer operadores de assembly e técnicos de serviço com instruções de trabalho AR e diretrizes de procedimento na fábrica ou fora do campo. 

Os aplicativos do mecanismo Vuforia existentes criados para telefones e tablets podem ser facilmente configurados no Unity para serem executados no HoloLens. Você pode até mesmo usar o mecanismo de Vuforia para levar seu novo aplicativo de HoloLens para tablets do Windows 10, como o Surface Pro 4 e o livro de superfície.

## <a name="get-the-tools"></a>Baixe as ferramentas

[Instale as versões recomendadas](install-the-tools.md) do Visual Studio e do Unity e, em seguida, configure o Unity para usar o Visual Studio e o IDE e o compilador preferenciais. 

Ao instalar o Unity, certifique-se de instalar o "back-end de script do .NET da Windows Store" ou o "back-end de script do IL2CPP da Windows Store". Além disso, não se esqueça de selecionar "suporte à realidade aumentada Vuforia" para habilitar o mecanismo Vuforia no Unity.


## <a name="getting-started-with-vuforia-engine"></a>Introdução ao mecanismo do Vuforia

Como o mecanismo do Vuforia é integrado ao Unity, os desenvolvedores não precisam baixar nem instalar nenhuma ferramenta extra. A versão recomendada do Unity é o fluxo de LTS que atualmente está em 2017,3 e inclui o 7.0.57 do mecanismo Vuforia. O melhor ponto de partida para aprender sobre como usar o mecanismo Vuforia com o HoloLens é com o [exemplo de hololens do mecanismo Vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponível no repositório de ativos do Unity). O exemplo fornece um projeto completo do HoloLens, incluindo cenas pré-configuradas que podem ser implantadas em um HoloLens.

As cenas mostram como usar destinos de imagem Vuforia para reconhecer uma imagem e aumentá-la com conteúdo digital em uma experiência de HoloLens. Os desenvolvedores que usam versões mais recentes do Unity e do Vuforia têm acesso a exemplos atualizados que incluem uma cena mostrando o uso de destinos de modelo no HoloLens. Você pode facilmente substituir seu próprio conteúdo nos bastidores para experimentar a criação de aplicativos do HoloLens que usam o mecanismo Vuforia.


## <a name="configuring-a-vuforia-app-for-hololens"></a>Configurando um aplicativo Vuforia para o HoloLens

Desenvolver um aplicativo de mecanismo Vuforia para o HoloLens é fundamentalmente o mesmo que desenvolver aplicativos de mecanismo Vuforia para outros dispositivos. Em seguida, você pode aplicar as configurações de compilação e as configurações descritas na seção abaixo. Isso é tudo o que é necessário para permitir que o mecanismo de Vuforia funcione com o mapeamento espacial do HoloLens e os sistemas de controle posicional.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Compilar e executar o exemplo do mecanismo Vuforia para o HoloLens
1.  Baixe o [exemplo do mecanismo Vuforia para o HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) do repositório de ativos do Unity
2.  Aplicar as [opções recomendadas do mecanismo Unity para energia e desempenho](performance-recommendations-for-unity.md)
3.  Adicione os bastidores de exemplo em cenas no Build.
4.  Defina o destino da compilação da plataforma para "Plataforma Universal do Windows" em arquivo > configurações de compilação.
5.  Selecione as seguintes definições de configuração da criação de plataforma: 
   * Dispositivo de destino = HoloLens
   * Tipo de compilação = D3D
   * SDK = mais recente instalado
   * Visual Studio versão = mais recente instalado
   * Compilar e executar em = computador local
6.  Defina um **nome de produto**exclusivo, em **configurações do Player**, para servir como o nome do aplicativo quando instalado no HoloLens.
7.  Verifique a **realidade aumentada do Vuforia** e a **realidade virtual com suporte** nas **configurações do Player > as configurações de XR**
8.  Também em **configurações de XR**, certifique-se de que "realidade misturada do Windows" seja adicionado à lista de **SDKs de realidade virtual**
9.  Verifique os seguintes recursos nas configurações do Player > configurações de publicação 
   * InternetClient
   * Integrada
   * SpatialPerception – se você pretende usar a API de observador de superfície
10. Selecione Compilar para gerar um projeto do Visual Studio
11. Compilar o executável do Visual Studio e instalá-lo em seu HoloLens

Observação: a partir da versão 7,2, o exemplo do mecanismo Vuforia para o HoloLens inclui uma cena de exemplo, incluindo o uso de exemplos de destinos de modelo

## <a name="the-vuforia-developer-portal"></a>O portal do desenvolvedor do Vuforia

Os desenvolvedores que desejam criar suas próprias experiências de AR com o Vuforia Engine e o HoloLens devem se inscrever em nosso portal do desenvolvedor Vuforia em [Developer.vuforia.com](https://developer.vuforia.com/). No portal, os desenvolvedores têm acesso aos [fóruns do mecanismo Vuforia](https://developer.vuforia.com/forum) , onde podem ingressar em discussões da Comunidade, uma [biblioteca](https://library.vuforia.com/) com documentação detalhada sobre todos os recursos do mecanismo do Vuforia e o Gerenciador de [destino do Vuforia](https://developer.vuforia.com/target-manager) , onde os usuários podem Crie seus próprios destinos personalizados. Os desenvolvedores também podem se inscrever para uma licença de desenvolvedor gratuita usando o [Gerenciador de licenças do Vuforia](https://developer.vuforia.com/license-manager).

## <a name="extended-tracking-with-vuforia"></a>Acompanhamento estendido com Vuforia

O [controle estendido](https://library.vuforia.com/articles/Training/Extended-Tracking) cria um mapa do ambiente para manter o controle mesmo quando um destino não está mais na exibição. É a contraparte do Vuforia Engines para o mapeamento espacial executado pelo HoloLens. Quando você habilita o acompanhamento estendido em um destino, permite que a pose desse destino seja passada para o sistema de mapeamento espacial. Dessa forma, os destinos podem existir nos sistemas de coordenadas espaciais do mecanismo Vuforia e do HoloLens, embora não sejam simultaneamente.

![janela Configurações do Unity](images/vuforia-extendedtracking.png)<br>
*Janela Configurações do Unity*

**Habilitando o controle estendido em um destino**

O mecanismo de Vuforia automaticamente transformará a pose de um destino que usa o controle estendido no sistema de coordenadas espaciais do HoloLens. Isso permite que o HoloLens assuma o controle e integre qualquer conteúdo que aumente o mapeamento espacial do ambiente de destino. Esse processo ocorre entre o mecanismo Vuforia e as APIs de realidade misturadas no Unity e não requer programação pelo desenvolvedor. ele é manipulado automaticamente.

**Aqui está o que ocorre...**
1. O controlador de destino do Vuforia reconhece o destino
2. O rastreamento de destino é inicializado
3. A posição e a rotação do destino são analisadas para fornecer uma estimativa de pose robusta para o HoloLens usar
4. Vuforia transforma a pose do destino no espaço de coordenadas do mapeamento espacial do HoloLens
5. O HoloLens assume o controle e o rastreador Vuforia é desativado

O desenvolvedor pode controlar esse processo para retornar o controle ao Vuforia, desabilitando o controle estendido no TargetBehaviour.

**Observação:** A partir do Vuforia 7,2, o controle estendido não é mais habilitado em uma base por destino. Em vez disso, os desenvolvedores podem ativar o rastreamento de dispositivos para habilitar a funcionalidade semelhante em todos os destinos na cena.


## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Mapeamento espacial](spatial-mapping.md)
* [Câmera no Unity](camera-in-unity.md)
* [Como exportar e criar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Documentação do Vuforia: desenvolvendo para o Windows 10 no Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Documentação do Vuforia: como instalar a extensão do Vuforia Unity](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Documentação do Vuforia: trabalhando com o exemplo de HoloLens no Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Documentação do Vuforia: controle estendido em Vuforia](https://library.vuforia.com/articles/Training/Extended-Tracking)
