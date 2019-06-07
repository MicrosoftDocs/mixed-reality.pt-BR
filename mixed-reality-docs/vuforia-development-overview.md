---
title: Usando Vuforia com o Unity
description: Aproveite Vuforia para criar aplicativos de realidade mista do Windows no Unity.
author: ailyadis
ms.author: ''
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia, marcadores, as coordenadas, quadro de referência, acompanhamento
ms.openlocfilehash: c0d2f6d0707e1ddd3ee00d3eb80af9fb459f252b
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750346"
---
# <a name="using-vuforia-engine-with-unity"></a>Usando o mecanismo de Vuforia com o Unity

Mecanismo Vuforia traz um recurso importante para o HoloLens – a capacidade de conectar-se de AR experiências para imagens específicas e objetos no ambiente. Você pode usar esse recurso para instruções passo a passo guiadas sobre o mecanismo para a empresa industrial de sobreposição ou adicionar recursos digitais e experiências a um produto físico ou um jogo. 

Para obter maior flexibilidade quando experiências de desenvolvimento de AR, o mecanismo de Vuforia oferece uma ampla gama de recursos e destinos. Um dos nossos recursos mais recentes, Vuforia destinos de modelo, é uma capacidade chave para usos comerciais e industriais. Metas modelo permitem que aplicativos reconhecer objetos físicos, como máquinas, automóveis ou toys e acompanhá-las com base em um CAD ou um modelo 3D digital. Para usos industriais, esse recurso pode fornecer a trabalhadores de assembly e técnicos de serviço com AR trabalham instruções e diretrizes de procedimentos enquanto na fábrica ou out no campo. 

Aplicativos de mecanismo Vuforia existentes que foram criados para telefones e tablets facilmente podem ser configurados no Unity para executar em HoloLens. Você pode até usar o mecanismo Vuforia entrem em seu novo aplicativo HoloLens tablets Windows 10 como o Surface Book e 4 do Surface Pro.

## <a name="get-the-tools"></a>Baixe as ferramentas

[Instalar as versões recomendadas](install-the-tools.md) do Visual Studio e o Unity e, em seguida, configure o Unity para usar o Visual Studio e o IDE preferencial e o compilador. 

Ao instalar o Unity, certifique-se de instalar o "Windows Store Scripting back-end .NET" ou "Windows Store IL2CPP scripts back-end". Além disso, certifique-se de selecionar "Vuforia aumentada realidade suporte" para habilitar o mecanismo Vuforia dentro do Unity.


## <a name="getting-started-with-vuforia-engine"></a>Introdução ao mecanismo de Vuforia

Uma vez que o mecanismo de Vuforia é integrado ao Unity, os desenvolvedores não precisam baixar ou instalar nenhuma ferramenta adicional. A versão recomendada do Unity é o fluxo de LTS que está atualmente em 2017.3 e inclui o mecanismo de Vuforia 7.0.57. O melhor ponto de partida para aprender sobre como usar o mecanismo Vuforia com HoloLens é com o [Vuforia mecanismo HoloLens exemplo](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponível no Unity Asset Store). O exemplo fornece um projeto completo do HoloLens, incluindo cenas pré-configurados que podem ser implantadas em um HoloLens.

Nos bastidores mostram como usar destinos de imagem Vuforia reconhecer uma imagem e incrementá-lo com conteúdo digital em uma experiência HoloLens. Os desenvolvedores que usam versões mais recentes do Unity e Vuforia têm acesso a exemplos atualizados que incluem uma cena mostrando o uso do modelo de destinos em HoloLens. Você pode facilmente substituir seu próprio conteúdo em segundo plano para fazer experiências com a criação de aplicativos do HoloLens que usam o mecanismo de Vuforia.


## <a name="configuring-a-vuforia-app-for-hololens"></a>Configurar um aplicativo Vuforia para HoloLens

Desenvolvendo um aplicativo do mecanismo de Vuforia para HoloLens é basicamente o mesmo que o desenvolvimento de aplicativos do mecanismo Vuforia para outros dispositivos. Em seguida, você pode aplicar as definições de compilação e configurações descritas na seção a seguir. Isso é tudo o que é necessário para habilitar o mecanismo de Vuforia funcionam com o mapeamento espacial do HoloLens e posicionais de sistemas de controle.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Compilar e executar o exemplo de mecanismo de Vuforia para HoloLens
1.  Baixe o [exemplo de mecanismo de Vuforia para HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) do Unity Asset Store
2.  Aplicar o [as opções de mecanismo do Unity para desempenho e energia recomendadas](performance-recommendations-for-unity.md)
3.  Adicione as cenas de exemplo para cenas em compilação.
4.  Definir seu destino de build da plataforma para "Plataforma Universal do Windows" no arquivo > configurações de Build.
5.  Selecione as seguintes definições de configuração de build de plataforma: 
   * Dispositivo de destino = HoloLens
   * Tipo de compilação = D3D
   * SDK = a versão mais recente instalado
   * Versão do Visual Studio = a versão mais recente instalado
   * Compilar e executar = na máquina Local
6.  Definir uma única **nome do produto**, na **configurações do Player**, para servir como o nome do aplicativo quando instalado no HoloLens.
7.  Verifique **Vuforia aumentada realidade** e **realidade Virtual com suporte** em **configurações do Player > configurações XR**
8.  Também no **configurações XR**, certifique-se de que o "Windows Mixed Reality" é adicionado para o **SDKs de realidade Virtual** lista
9.  Verifique os seguintes recursos no Player Configurações > configurações de publicação 
   * InternetClient
   * WebCam
   * SpatialPerception - se você pretende usar a API do observador de superfície
10. Selecione a compilação para gerar um projeto do Visual Studio
11. Criar o arquivo executável do Visual Studio e instale-o em seu HoloLens

Observação: Começando com a versão 7.2, a amostra do mecanismo de Vuforia para HoloLens inclui uma cena de exemplo, incluindo exemplos de uso de destinos de modelo

## <a name="the-vuforia-developer-portal"></a>O Portal do desenvolvedor Vuforia

Os desenvolvedores que desejam para criar seu próprios AR experiências com o mecanismo de Vuforia e HoloLens devem se inscrever em nosso Portal do desenvolvedor Vuforia em [developer.vuforia.com](https://developer.vuforia.com/). No portal, os desenvolvedores têm acesso para o [Vuforia mecanismo fóruns](https://developer.vuforia.com/forum) onde eles podem participar de discussões da comunidade, um [biblioteca](https://library.vuforia.com/) com documentação detalhada sobre todos os recursos do mecanismo de Vuforia e a [ Gerenciador de destino Vuforia](https://developer.vuforia.com/target-manager) onde os usuários podem criar seus próprios destinos personalizados. Os desenvolvedores também podem se inscrever para uma licença de desenvolvedor gratuita usando o [Gerenciador de licenças Vuforia](https://developer.vuforia.com/license-manager).

## <a name="extended-tracking-with-vuforia"></a>Controle estendido com Vuforia

[Acompanhamento estendido](https://library.vuforia.com/articles/Training/Extended-Tracking) cria um mapa de ambiente para manter o mesmo quando um destino não está mais na exibição de controle. É a contraparte Vuforia mecanismos para o mapeamento espacial executado pelo HoloLens. Quando você habilita o controle estendido em um destino, você pode habilitar a pose do que se destinam a serem passados para o sistema de mapeamento espacial. Dessa forma, destinos podem existir no mecanismo Vuforia tanto o HoloLens sistemas de coordenadas espaciais, embora não simultaneamente.

![Janela de configurações do Unity](images/vuforia-extendedtracking.png)<br>
*Janela de configurações do Unity*

**Habilitar o controle estendido em um destino**

Mecanismo de Vuforia automaticamente transformará a pose de um destino que usa o controle estendido para o sistema de coordenadas espacial HoloLens. Isso permite que o HoloLens para assumir o controle e integrar qualquer conteúdo aumentando no mapa espacial do ambiente de destino. Esse processo ocorre entre o mecanismo Vuforia e realidade misturada APIs no Unity e não exige qualquer programação pelo desenvolvedor – ele é manipulado automaticamente.

**Aqui está o que ocorre...**
1. Destino do Vuforia rastreador reconhece o destino
2. Controle de destino, em seguida, é inicializado
3. A posição e rotação de destino são analisados para fornecer uma estimativa de pose robusto para HoloLens usar
4. Vuforia transforma pose do destino para o espaço de coordenadas do HoloLens mapeamento espacial
5. HoloLens tem sobre o acompanhamento e o rastreador de Vuforia é desativado

O desenvolvedor pode controlar esse processo, para retornar o controle para Vuforia, desabilitando o controle estendido a TargetBehaviour.

**OBSERVAÇÃO:** Começando com Vuforia 7.2, estendido de controle não estiver habilitado em uma base por destino. Em vez disso, os desenvolvedores podem ativar dispositivos de controle para habilitar uma funcionalidade semelhante em todos os destinos na cena.


## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Mapeamento espacial](spatial-mapping.md)
* [Câmera no Unity](camera-in-unity.md)
* [Como exportar e criar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Documentação do Vuforia: Desenvolvendo para Windows 10 no Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Documentação do Vuforia: Como instalar a extensão do Vuforia Unity](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Documentação do Vuforia: Trabalhando com o exemplo HoloLens no Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Documentação do Vuforia: Controle estendido no Vuforia](https://library.vuforia.com/articles/Training/Extended-Tracking)
