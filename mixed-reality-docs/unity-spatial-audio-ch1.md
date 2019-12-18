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
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="2a3b6-105">Adicionando áudio espacial ao seu projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="2a3b6-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="2a3b6-106">Bem-vindo ao tutioral de áudio espacial do Unity em HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-106">Welcome to the spatial audio tutioral for Unity on HoloLens2.</span></span> <span data-ttu-id="2a3b6-107">Esta sequência de tutorial mostra:</span><span class="sxs-lookup"><span data-stu-id="2a3b6-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="2a3b6-108">Como usar o descarregamento HRTF no HoloLens 2 no Unity</span><span class="sxs-lookup"><span data-stu-id="2a3b6-108">How to use HRTF offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="2a3b6-109">Como habilitar o reverberador ao usar o descarregamento de HRTF</span><span class="sxs-lookup"><span data-stu-id="2a3b6-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="2a3b6-110">O [repositório GitHub do Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tem um projeto de Unity concluído desta sequência de tutorial.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="2a3b6-111">Para nossas recomendações sobre quando pode ser útil para os sons espaciais, consulte [design de som espacial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="2a3b6-111">For our recommendations on when it can be helpful to spatialize sounds, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="objectives"></a><span data-ttu-id="2a3b6-112">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2a3b6-112">Objectives</span></span>
<span data-ttu-id="2a3b6-113">Neste primeiro capítulo, você vai:</span><span class="sxs-lookup"><span data-stu-id="2a3b6-113">In this first chapter, you'll:</span></span>
* <span data-ttu-id="2a3b6-114">Criar um projeto do Unity e importar MRTK</span><span class="sxs-lookup"><span data-stu-id="2a3b6-114">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="2a3b6-115">Importar o plug-in Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="2a3b6-115">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="2a3b6-116">Habilitar o plug-in Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="2a3b6-116">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="2a3b6-117">Habilitar o áudio espacial em sua estação de trabalho do desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="2a3b6-117">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="2a3b6-118">Criar um projeto e adicionar o NuGet para o Unity</span><span class="sxs-lookup"><span data-stu-id="2a3b6-118">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="2a3b6-119">Comece com um projeto do Unity vazio e, em seguida, adicione e configure o NuGet para o Unity:</span><span class="sxs-lookup"><span data-stu-id="2a3b6-119">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="2a3b6-120">Baixe o [NuGetForUnity. unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) mais recente</span><span class="sxs-lookup"><span data-stu-id="2a3b6-120">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="2a3b6-121">Na barra de menus do Unity, clique em **ativos-> importar pacote-> pacote personalizado...** e instale o pacote NuGetForUnity:</span><span class="sxs-lookup"><span data-stu-id="2a3b6-121">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![Importar pacote personalizado](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="2a3b6-123">Adicionar o pacote do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2a3b6-123">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="2a3b6-124">O suporte do Windows Mixed Reality no Unity 2019 e posterior está contido em um pacote opcional.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-124">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="2a3b6-125">Para adicioná-lo ao seu projeto, abra o **Gerenciador de pacotes do > de janela** na barra de menus do Unity:</span><span class="sxs-lookup"><span data-stu-id="2a3b6-125">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![Menu do Gerenciador de pacotes](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="2a3b6-127">Em seguida, localize e instale o pacote do **Windows Mixed Reality** :</span><span class="sxs-lookup"><span data-stu-id="2a3b6-127">Then find and install the **Windows Mixed Reality** package:</span></span>

![Janela do Gerenciador de pacotes](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="2a3b6-129">Instalar o MRTK e o Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="2a3b6-129">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="2a3b6-130">Usando o NuGet para Unity, instale os plug-ins MRTK e Microsoft Spatializer:</span><span class="sxs-lookup"><span data-stu-id="2a3b6-130">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="2a3b6-131">Na barra de menus do Unity, clique em **NuGet-> gerenciar pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-131">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![Gerenciar pacotes NuGet](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="2a3b6-133">Na caixa de **pesquisa** , digite "Microsoft. MixedReality. Toolkit" e instale o pacote do MRTK Core: **Microsoft. MixedReality. Toolkit. Foundation**</span><span class="sxs-lookup"><span data-stu-id="2a3b6-133">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![Pacote NuGet do MRTK](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="2a3b6-135">O [pacote NuGet do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) tem detalhes e contexto adicionais.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-135">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="2a3b6-136">Na caixa de **pesquisa** , digite "Microsoft. SpatialAudio" e instale o pacote do Microsoft Spatializer: **Microsoft. SpatialAudio. Spatializer. Unity**</span><span class="sxs-lookup"><span data-stu-id="2a3b6-136">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![NuGet do plugin Spatializer](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="2a3b6-138">Configurar o MRTK em seu projeto</span><span class="sxs-lookup"><span data-stu-id="2a3b6-138">Set up MRTK in your project</span></span>

1. <span data-ttu-id="2a3b6-139">Abra a janela configurações de Build acessando **arquivo-> configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-139">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="2a3b6-140">Selecione o _plataforma universal do Windows_ e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-140">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="2a3b6-141">Clique em **configurações do Player** na **janela criar** para abrir as propriedades **das configurações do Player** no painel **Inspetor** .</span><span class="sxs-lookup"><span data-stu-id="2a3b6-141">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="2a3b6-142">Em **configurações de XR**, marque a caixa de seleção **suporte à realidade virtual**</span><span class="sxs-lookup"><span data-stu-id="2a3b6-142">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="2a3b6-143">Em **configurações de XR**, altere o **modo de renderização de estéreo** para **passagem única com instância**.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-143">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="2a3b6-144">Em **configurações de publicação**, marque a caixa de seleção **percepção espacial** na seção **recursos**</span><span class="sxs-lookup"><span data-stu-id="2a3b6-144">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="2a3b6-145">Na barra de menus, clique em **Kit de ferramentas de realidade misturada-> adicionar à cena e configurar..**</span><span class="sxs-lookup"><span data-stu-id="2a3b6-145">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="2a3b6-146">para adicionar MRTK à sua cena.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-146">to add MRTK to your scene.</span></span>

<span data-ttu-id="2a3b6-147">Para obter diretrizes adicionais, incluindo como criar seu aplicativo e implantá-lo em um HoloLens 2, consulte [o capítulo 1 do módulo de base de aprendizado do Mr](mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="2a3b6-147">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="2a3b6-148">Habilitar o plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="2a3b6-148">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="2a3b6-149">Habilite o plug-in **Microsoft Spatializer** .</span><span class="sxs-lookup"><span data-stu-id="2a3b6-149">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="2a3b6-150">Abra o **editar > configurações do projeto-> áudio**e altere o **plug-in Spatializer** para "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="2a3b6-150">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="2a3b6-151">A seção **áudio** das **configurações do projeto** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="2a3b6-151">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Configurações do projeto mostrando o plug-in spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="2a3b6-153">Habilitar áudio espacial em sua estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="2a3b6-153">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="2a3b6-154">Em versões de área de trabalho do Windows, o áudio espacial é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-154">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="2a3b6-155">Habilite-o clicando com o botão direito do mouse no ícone de volume na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-155">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="2a3b6-156">Para obter a melhor representação do que você ouvirá no HoloLens 2, escolha **som espacial-> Windows Sonic para fones de ouvido**.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-156">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Configurações de áudio espacial da área de trabalho](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="2a3b6-158">Essa configuração só será necessária se você planeja testar seu projeto no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-158">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2a3b6-159">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2a3b6-159">Next steps</span></span>
<span data-ttu-id="2a3b6-160">Continue no [módulo de áudio espacial do Unity capítulo 2](unity-spatial-audio-ch2.md) para os sons de interação do botão espacial.</span><span class="sxs-lookup"><span data-stu-id="2a3b6-160">Continue on to [Unity spatial audio chapter 2](unity-spatial-audio-ch2.md) to spatialize button interaction sounds.</span></span>

