---
title: Tutoriais de áudio espacial-1. Adicionando áudio espacial ao seu projeto
description: Adicione o plug-in do Microsoft Spatializer ao seu projeto do Unity para acessar o descarregamento de hardware do HoloLens 2 HRTF.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial
ms.openlocfilehash: 8978017b3ce6c49a81b3eee2fe21e9234f4e71f0
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182793"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a>Adicionando áudio espacial ao seu projeto do Unity

Bem-vindo ao tutioral de áudio espacial do Unity em HoloLens2. Esta sequência de tutorial mostra:
* Como usar o descarregamento HRTF no HoloLens 2 no Unity
* Como habilitar o reverberador ao usar o descarregamento de HRTF

O [repositório GitHub do Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tem um projeto de Unity concluído desta sequência de tutorial. 

Para nossas recomendações sobre quando pode ser útil para os sons espaciais, consulte [design de som espacial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).

## <a name="objectives"></a>Objetivos
Neste primeiro capítulo, você vai:
* Criar um projeto do Unity e importar MRTK
* Importar o plug-in Microsoft spatializer
* Habilitar o plug-in Microsoft spatializer
* Habilitar o áudio espacial em sua estação de trabalho do desenvolvedor

## <a name="create-a-project-and-add-nuget-for-unity"></a>Criar um projeto e adicionar o NuGet para o Unity
Comece com um projeto do Unity vazio e, em seguida, adicione e configure o NuGet para o Unity:
1. Baixe o [NuGetForUnity. unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) mais recente
2. Na barra de menus do Unity, clique em **ativos-> importar pacote-> pacote personalizado...** e instale o pacote NuGetForUnity:

![Importar pacote personalizado](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a>Adicionar o pacote do Windows Mixed Reality
O suporte do Windows Mixed Reality no Unity 2019 e posterior está contido em um pacote opcional. Para adicioná-lo ao seu projeto, abra o **Gerenciador de pacotes do > de janela** na barra de menus do Unity:

![Menu do Gerenciador de pacotes](images/spatial-audio/package-manager-menu.png)

Em seguida, localize e instale o pacote do **Windows Mixed Reality** :

![Janela do Gerenciador de pacotes](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a>Instalar o MRTK e o Microsoft Spatializer
Usando o NuGet para Unity, instale os plug-ins MRTK e Microsoft Spatializer:
1. Na barra de menus do Unity, clique em **NuGet-> gerenciar pacotes NuGet**.

![Gerenciar pacotes NuGet](images/spatial-audio/manage-nuget-packages.png)

2. Na caixa de **pesquisa** , digite "Microsoft. MixedReality. Toolkit" e instale o pacote do MRTK Core: **Microsoft. MixedReality. Toolkit. Foundation**

![Pacote NuGet do MRTK](images/spatial-audio/mrtk-nuget-package.png)

O [pacote NuGet do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) tem detalhes e contexto adicionais.

4. Na caixa de **pesquisa** , digite "Microsoft. SpatialAudio" e instale o pacote do Microsoft Spatializer: **Microsoft. SpatialAudio. Spatializer. Unity**

![NuGet do plugin Spatializer](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a>Configurar o MRTK em seu projeto

1. Abra a janela configurações de Build acessando **arquivo-> configurações de Build**.

2. Selecione o _plataforma universal do Windows_ e clique em **alternar plataforma**.

3. Clique em **configurações do Player** na **janela criar** para abrir as propriedades **das configurações do Player** no painel **Inspetor** .
    * Em **configurações de XR**, marque a caixa de seleção **suporte à realidade virtual**
    * Em **configurações de XR**, altere o **modo de renderização de estéreo** para **passagem única com instância**.
    * Em **configurações de publicação**, marque a caixa de seleção **percepção espacial** na seção **recursos**

4. Na barra de menus, clique em **Kit de ferramentas de realidade misturada-> adicionar à cena e configurar..** para adicionar MRTK à sua cena.

Para obter diretrizes adicionais, incluindo como criar seu aplicativo e implantá-lo em um HoloLens 2, consulte [o capítulo 1 do módulo de base de aprendizado do Mr](mrlearning-base-ch1.md).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Habilitar o plug-in Microsoft Spatializer
Habilite o plug-in **Microsoft Spatializer** . Abra o **editar > configurações do projeto-> áudio**e altere o **plug-in Spatializer** para "Microsoft Spatializer". A seção **áudio** das **configurações do projeto** terá a seguinte aparência:

![Configurações do projeto mostrando o plug-in spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Habilitar áudio espacial em sua estação de trabalho
Em versões de área de trabalho do Windows, o áudio espacial é desabilitado por padrão. Habilite-o clicando com o botão direito do mouse no ícone de volume na barra de tarefas. Para obter a melhor representação do que você ouvirá no HoloLens 2, escolha **som espacial-> Windows Sonic para fones de ouvido**.

![Configurações de áudio espacial da área de trabalho](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> Essa configuração só será necessária se você planeja testar seu projeto no editor do Unity.

## <a name="next-steps"></a>Próximas etapas
Continue no [módulo de áudio espacial do Unity capítulo 2](unity-spatial-audio-ch2.md) para os sons de interação do botão espacial.

