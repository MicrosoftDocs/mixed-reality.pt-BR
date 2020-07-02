---
title: Áudio espacial no Unreal
description: Visão geral do plug-in de áudio espacial do Unreal Engine.
author: hferrone
ms.author: v-haferr
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, remoting, mixed reality, development, getting started, features, new project, emulator, documentation, guides, features, holograms, game development
ms.openlocfilehash: 404aaec7b618e951ad69c02e7aaef80e42d31dbd
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85446782"
---
# <a name="spatial-audio-in-unreal"></a>Áudio espacial no Unreal

## <a name="overview"></a>Visão geral

Ao contrário da visão, os seres humanos ouvem o som ao redor em 360 graus. O som espacial emula o modo como a audição humana funciona, fornecendo as indicações necessárias para identificar localizações de som no espaço do mundo. Ao adicionar som espacial aos seus aplicativos de realidade misturada, você está aprimorando o nível de imersão experimentado pelos usuários.  

O processamento de som espacial de alta qualidade é complexo e, portanto, o HoloLens 2 é fornecido com um hardware dedicado para processar esses objetos de som.  Para acessar esse suporte de processamento de hardware, instale o plug-in **MicrosoftSpatialSound** no seu projeto do Unreal. Este artigo descreverá a instalação e a configuração desse plug-in e indicará recursos mais aprofundados para o uso de som espacial no Unreal Engine. 

## <a name="installing-the-microsoft-spatial-sound-plugin"></a>Como instalar o plug-in do Microsoft Spatial Sound 

A primeira etapa para adicionar som espacial ao seu projeto é instalar o plug-in do Microsoft Spatial Sound, que pode ser encontrado com as seguintes etapas: 

1. Clicando em **Editar > Plug-ins** e procurando **MicrosoftSpatialSound** na caixa de pesquisa. 
2. Marcando a caixa de seleção **Habilitado** no plug-in **MicrosoftSpatialSound**. 
3. Reiniciando o editor do Unreal selecionando **Reiniciar Agora** na página de plug-ins. 

> [!NOTE]
> Se ainda não tiver feito isso, você precisará instalar os plug-ins do **Microsoft Windows Mixed Reality** e do **HoloLens** seguindo as instruções da seção **[Como inicializar seu projeto](unreal-uxt-ch2.md)** da nossa série de tutoriais do Unreal.

![Plug-in de áudio espacial do Unreal](images/unreal-spatial-audio-img-01.png)

Depois que o editor for reiniciado, o projeto estará pronto.


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a>Como configurar o plug-in de espacialização para a plataforma HoloLens 2
A configuração do plug-in de espacialização é feita de acordo com a plataforma.  Habilite o plug-in do Microsoft Spatial Sound para o HoloLens 2:
1. Selecionando **Editar > Configurações do Projeto**, rolando a página até **Plataformas** e clicando em **HoloLens**.
2. Expandindo as propriedades de **Áudio** e definindo o campo **Plug-in de Espacialização** como **Microsoft Spatial Sound**.

![Plug-in de espacialização para a plataforma HoloLens](images/unreal-spatial-audio-img-02.png)

Se você pretende visualizar seu aplicativo no editor do Unreal em um computador desktop, repita as etapas acima para a plataforma **Windows**:

![Plug-in de espacialização para a plataforma Windows](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a>Como habilitar o áudio espacial na sua estação de trabalho
O áudio espacial está desabilitado por padrão nas versões de área de trabalho do Windows. Habilite-o:
* Clicando com o botão direito do mouse no ícone de **volume** na barra de tarefas. 
    + Escolha **Som espacial -> Windows Sonic para Fones de Ouvido** para obter a melhor representação do que você ouvirá no HoloLens 2.

![Plug-in de espacialização](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
>Essa configuração só é necessária se você planeja testar seu projeto no editor do Unreal.

## <a name="creating-attenuation-objects"></a>Como criar objetos de Atenuação
Depois de instalar e configurar os plug-ins necessários:
1. Procure um ator de **Som Ambiente** na janela **Posicionar Atores** e arraste-o para a janela **Cena**.

![Como adicionar o ator de som ambiente](images/unreal-spatial-audio-img-07.png)

2. Torne o ator de **Som Ambiente** um filho de um elemento visual na cena. 
    * Um ator de Som Ambiente não tem nenhuma representação visual por padrão; portanto, você só ouvirá um som da posição dele na cena. A anexação dele a um elemento visual permite que você veja e mova o ator como qualquer outro ativo.

3.  Clique com o botão direito do mouse no **Navegador de Conteúdo** e selecione **Criar Ativo Avançado -> Sons -> Atenuação de Som**:

![Como criar um ativo de atenuação de som](images/unreal-spatial-audio-img-06.png)

4. Clique com o botão direito do mouse no ativo de **Atenuação de Som** na janela **Navegador de Conteúdo** e selecione a opção **Editar** para abrir a janela Propriedades.
    * Alterne o **Método de Espacialização** para **Binaural**.

![Definir o método de espacialização](images/unreal-spatial-audio-img-03.png)

5. Selecione o ator de **Som Ambiente** e role a página para baixo até a seção **Atenuação** no painel **Detalhes**. 
    * Defina a propriedade de **Configurações de Atenuação** como o ativo de **Atenuação de Som** criado.

![Definir a configuração de atenuação](images/unreal-spatial-audio-img-08.png)

6. Defina o **Ativo de Som** que deseja anexar ao ator de Som Ambiente atualizando a propriedade **Som** do ator de Som Ambiente para especificar o arquivo de SoundAsset a ser usado.

![Definir o ativo de som](images/unreal-spatial-audio-img-09.png)

> [!NOTE] 
> O arquivo de SoundAsset precisa ser mono para ser espacializado com o plug-in do Microsoft Spatial Sound. Encontre as propriedades do arquivo de som posicionando o cursor sobre o ativo na janela Navegador de Conteúdo, conforme mostrado na captura de tela abaixo.

![Novo ativo de atenuação de som](images/unreal-spatial-audio-img-10.png)

Quando tudo isso estiver configurado, o som ambiente poderá ser espacializado por meio do suporte de descarregamento de hardware dedicado no HoloLens 2.

## <a name="configuring-objects-for-spatialization"></a>Como configurar objetos para espacialização
Trabalhar com áudio espacial significa que você é responsável pelo gerenciamento de como o som se comporta em um ambiente virtual. Seu foco principal é a criação de objetos de som que parecem soar mais alto quando o usuário está próximo e mais baixo quando o usuário está distante. Isso é conhecido como atenuação de som, fazendo com que os sons pareçam como se estivessem posicionados em uma localização fixa.

Todos os objetos de atenuação são fornecidos com as configurações modificáveis de:
* Distância
* Espacialização
* Absorção de ar
* Foco do ouvinte
* Envio de reverberação
* Oclusão

O artigo [Atenuação de som no Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) traz detalhes e especificações de implementação sobre cada um desses tópicos.


## <a name="see-also"></a>Veja também
* [Som espacial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [Design de som espacial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [MR Espacial 220: som espacial](https://docs.microsoft.com/windows/mixed-reality/holograms-220)