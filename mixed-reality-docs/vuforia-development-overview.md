---
title: Usando o Vuforia com o Unity
description: Aproveite o Vuforia para criar aplicativos de realidade mista do Windows no Unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia, marcadores, coordenadas, quadro de referência, acompanhamento
ms.openlocfilehash: 2d7cc27cd9a5fe9bb6502edaa6df0b7a80755049
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334470"
---
# <a name="using-vuforia-engine-with-unity"></a>Usando o mecanismo do Vuforia com o Unity

O Vuforia Engine traz um recurso importante para o HoloLens – o poder de conectar experiências do AR a imagens e objetos específicos no ambiente. Você pode usar essa capacidade para sobrepor instruções passo a passo guiadas sobre máquinas para a empresa industrial ou adicionar recursos e experiências digitais a um produto ou jogo físico.

Para obter maior flexibilidade ao desenvolver experiências de AR, o Vuforia Engine oferece uma ampla gama de recursos e destinos. Um dos nossos mais novos recursos, Vuforia Model targets, é um recurso importante para usos comerciais e industriais. Os destinos de modelo permitem que os aplicativos reconheçam objetos físicos, como computadores, automóveis ou brinquedos, e os acompanham com base em um modelo CAD ou 3D digital. Para usos industriais, esse recurso pode fornecer operadores de assembly e técnicos de serviço com instruções de trabalho AR e diretrizes de procedimento na fábrica ou fora do campo.

Os aplicativos do mecanismo Vuforia existentes criados para telefones e tablets podem ser facilmente configurados no Unity para serem executados no HoloLens. Você pode até mesmo usar o mecanismo de Vuforia para levar seu novo aplicativo de HoloLens para tablets do Windows 10, como o Surface pro e o livro de superfície.


## <a name="get-the-tools"></a>Baixe as ferramentas

[Instale as versões recomendadas](install-the-tools.md) do Visual Studio e do Unity e, em seguida, configure o Unity para usar o Visual Studio e o IDE e o compilador preferenciais. 

Ao instalar o Unity, certifique-se de instalar o "back-end de script do IL2CPP da Windows Store".

Adicionar o suporte do mecanismo Vuforia funciona de maneira diferente, dependendo da sua versão do Unity:
*   Unity 2018,4: baixar o instalador do mecanismo do Vuforia para o Unity 2018,4 no portal do desenvolvedor do Vuforia
*   Unity 2019,2: obter o [pacote de mecanismo Vuforia](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html) mais recente 

## <a name="getting-started-with-vuforia-engine"></a>Introdução ao mecanismo do Vuforia

O melhor ponto de partida para aprender sobre como usar o mecanismo Vuforia com o HoloLens é com o [exemplo de hololens do mecanismo Vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponível no repositório de ativos do Unity). O exemplo fornece um projeto completo do HoloLens, incluindo cenas pré-configuradas que podem ser implantadas em um HoloLens.

As cenas mostram como usar destinos de imagem Vuforia para reconhecer uma imagem e aumentá-la com conteúdo digital em uma experiência de HoloLens. O exemplo de Hololens do mecanismo Vuforia também inclui uma cena que mostra o uso de destinos de modelo e VuMarks no HoloLens. Você pode facilmente substituir seu próprio conteúdo nos bastidores para experimentar a criação de aplicativos do HoloLens que usam o mecanismo Vuforia.



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

Os desenvolvedores que desejam criar suas próprias experiências de AR com o Vuforia Engine e o HoloLens devem se inscrever em nosso portal do desenvolvedor Vuforia em [Developer.vuforia.com](https://developer.vuforia.com/). No portal, os desenvolvedores têm acesso aos [fóruns do mecanismo Vuforia](https://developer.vuforia.com/forum) , onde podem ingressar em discussões da Comunidade, uma [biblioteca](https://library.vuforia.com/) com documentação detalhada sobre todos os recursos do mecanismo do Vuforia e o Gerenciador de [destino do Vuforia](https://developer.vuforia.com/target-manager) , onde os usuários podem criar seus próprios destinos personalizados. Os desenvolvedores também podem se inscrever para uma licença de desenvolvedor gratuita usando o [Gerenciador de licenças do Vuforia](https://developer.vuforia.com/license-manager).

## <a name="extended-tracking-with-vuforia"></a>Acompanhamento estendido com Vuforia

O [controle estendido](https://library.vuforia.com/articles/Training/Extended-Tracking) mantém o rastreamento mesmo quando um destino não está mais na exibição. Ele é habilitado automaticamente para todos os destinos quando o controlador de dispositivo posicional está habilitado. Para aplicativos HoloLens, o controlador de dispositivo posicional é iniciado automaticamente no Unity.

O mecanismo de Vuforia combina automaticamente as poses do rastreamento espacial da câmera e do HoloLens para fornecer um destino estável, independentemente de o destino ser visto pela câmera ou não.

Como o processo é manipulado automaticamente, ele não requer nenhuma programação pelo desenvolvedor.


**Veja a seguir uma descrição de alto nível do processo:**
1. O controlador de destino do Vuforia reconhece o destino
2. O rastreamento de destino é inicializado
3. A posição e a rotação do destino são analisadas para fornecer uma estimativa de pose robusta para o HoloLens
4. O mecanismo Vuforia transforma a pose do destino no espaço de coordenadas do mapeamento espacial do HoloLens
5. O HoloLens assumirá o controle se o destino não estiver mais na exibição. Sempre que você olhar novamente o destino, o Vuforia continuará a rastrear as imagens e os objetos com precisão.

Os destinos que são detectados, mas que não estão mais na exibição, são relatados como EXTENDED_TRACKED. Nesses casos, o script DefaultTrackableEventHandler usado em todos os destinos continua a renderizar o conteúdo de aumento. O desenvolvedor pode controlar esse comportamento implementando um script de manipulador de eventos rastreável personalizado.


## <a name="performance-mode-with-vuforia-engine"></a>Modo de desempenho com mecanismo Vuforia 

É possível que o mecanismo Vuforia gerencie o desempenho no HoloLens para realizar experiências de AR e reduzir a carga de trabalho na CPU. O mecanismo Vuforia oferece três modos que podem ser selecionados: padrão, para otimizar a velocidade e para otimizar a qualidade. 

*   MODE_OPTIMIZE_SPEED permite minimizar a carga de trabalho no dispositivo do HoloLens e é ótimo para estender as experiências do AR. É recomendável para situações em que o aplicativo está acompanhando objetos/destinos estáticos.
*   MODE_DEFAULT é o modo normal que pode ser usado na maioria dos cenários.
*   MODE_OPTIMIZE_QUALITY é melhor para controlar destinos móveis ou destinos de modelo que você espera que sejam coletados.

**Definindo o modo**

Para alterar o modo de desempenho no Unity, navegue até configuração do Vuforia (Ctrl + Shift + V/Cmd + Shift + V) que está localizado como um componente no ARCamera gameobject. 
*   Selecione o menu suspenso para o modo de dispositivo de câmera e selecione uma das três opções.


## <a name="see-also"></a>Veja também
* [Instalar as ferramentas](install-the-tools.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Mapeamento espacial](spatial-mapping.md)
* [Câmera no Unity](camera-in-unity.md)
* [Como exportar e criar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Documentação do Vuforia: desenvolvendo para o Windows 10 no Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Documentação do Vuforia: como instalar a extensão do Vuforia Unity](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Documentação do Vuforia: trabalhando com o exemplo de HoloLens no Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Documentação do Vuforia: controle estendido em Vuforia](https://library.vuforia.com/articles/Training/Extended-Tracking)
