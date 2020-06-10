---
title: 1. Introdução
description: Parte 1 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: c16671fc8f4233378dafa646786df1f7b5ae18e1
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330163"
---
# <a name="1-getting-started"></a><span data-ttu-id="b5ee1-104">1. Introdução</span><span class="sxs-lookup"><span data-stu-id="b5ee1-104">1. Getting started</span></span>

<span data-ttu-id="b5ee1-105">Seja você alguém pouco familiarizado com a realidade misturada ou um profissional experiente, esse é o lugar para iniciar seu percurso com o [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) e o [Unreal Engine](https://www.unrealengine.com/en-US/).</span><span class="sxs-lookup"><span data-stu-id="b5ee1-105">Whether you're new to mixed reality or a seasoned pro, this is the place to start your journey with [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/).</span></span> <span data-ttu-id="b5ee1-106">Esta série de tutoriais fornecerá um guia passo a passo sobre como criar um aplicativo de xadrez interativo com o [plug-in de Ferramentas de UX](https://github.com/microsoft/MixedReality-UXTools-Unreal), parte do [Kit de Ferramentas de Realidade Misturada para o Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span><span class="sxs-lookup"><span data-stu-id="b5ee1-106">This tutorial series will give you a step by step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="b5ee1-107">O plug-in ajudará você a adicionar recursos comuns de UX a seus projetos pelo uso de código, blueprints e exemplos.</span><span class="sxs-lookup"><span data-stu-id="b5ee1-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![Encerrar cena no visor](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="b5ee1-109">Ao final da série, você terá experiência prática em:</span><span class="sxs-lookup"><span data-stu-id="b5ee1-109">By the end of the series you'll have hands-on experience with:</span></span>
* <span data-ttu-id="b5ee1-110">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="b5ee1-110">Starting a new project</span></span>
* <span data-ttu-id="b5ee1-111">Configurar a realidade misturada</span><span class="sxs-lookup"><span data-stu-id="b5ee1-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="b5ee1-112">Trabalhar com a entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="b5ee1-112">Working with user input</span></span>
* <span data-ttu-id="b5ee1-113">Adicionar botões</span><span class="sxs-lookup"><span data-stu-id="b5ee1-113">Adding buttons</span></span>
* <span data-ttu-id="b5ee1-114">Jogar em um emulador ou dispositivo</span><span class="sxs-lookup"><span data-stu-id="b5ee1-114">Playing on an emulator or device</span></span>

<span data-ttu-id="b5ee1-115">Se você tiver alguma dúvida, confira nossa [Visão geral do desenvolvimento com o Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span><span class="sxs-lookup"><span data-stu-id="b5ee1-115">If you have any questions, check out our [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b5ee1-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b5ee1-116">Prerequisites</span></span>
<span data-ttu-id="b5ee1-117">Verifique se você atendeu aos seguintes requisitos antes de começar:</span><span class="sxs-lookup"><span data-stu-id="b5ee1-117">Make sure you've met the following requirements before jumping in:</span></span>
* <span data-ttu-id="b5ee1-118">Windows 10 1809 ou posterior</span><span class="sxs-lookup"><span data-stu-id="b5ee1-118">Windows 10 1809 or later</span></span>
* <span data-ttu-id="b5ee1-119">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="b5ee1-119">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="b5ee1-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 ou posterior</span><span class="sxs-lookup"><span data-stu-id="b5ee1-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="b5ee1-121">Dispositivo do Microsoft HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode) ou Emulador</span><span class="sxs-lookup"><span data-stu-id="b5ee1-121">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="b5ee1-122">Visual Studio 2019 com as cargas de trabalho abaixo</span><span class="sxs-lookup"><span data-stu-id="b5ee1-122">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="b5ee1-123">Instalação do Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="b5ee1-123">Installing Visual Studio 2019</span></span>
<span data-ttu-id="b5ee1-124">A última etapa é configurar o Visual Studio da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b5ee1-124">The last step is to setup Visual Studio as follows:</span></span>
1. <span data-ttu-id="b5ee1-125">Instale a versão mais recente do [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span><span class="sxs-lookup"><span data-stu-id="b5ee1-125">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="b5ee1-126">Instale as seguintes [cargas de trabalho](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads):</span><span class="sxs-lookup"><span data-stu-id="b5ee1-126">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads):</span></span>
    * <span data-ttu-id="b5ee1-127">Desenvolvimento para desktop com C++</span><span class="sxs-lookup"><span data-stu-id="b5ee1-127">Desktop development with C++</span></span>
    * <span data-ttu-id="b5ee1-128">Desenvolvimento para área de trabalho com .NET</span><span class="sxs-lookup"><span data-stu-id="b5ee1-128">.NET desktop development</span></span>
    * <span data-ttu-id="b5ee1-129">Desenvolvimento para a Plataforma Universal do Windows</span><span class="sxs-lookup"><span data-stu-id="b5ee1-129">Universal Windows Platform development</span></span>

3. <span data-ttu-id="b5ee1-130">Instale os seguintes [componentes](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components):</span><span class="sxs-lookup"><span data-stu-id="b5ee1-130">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components):</span></span>
    * <span data-ttu-id="b5ee1-131">Compiladores, ferramentas de build e runtimes > ferramentas de build MSVC v142 – VS 2019 C++ ARM64 (versão mais recente)</span><span class="sxs-lookup"><span data-stu-id="b5ee1-131">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="b5ee1-132">Pronto!</span><span class="sxs-lookup"><span data-stu-id="b5ee1-132">That's it!</span></span> <span data-ttu-id="b5ee1-133">Você está pronto para prosseguir para a inicialização do projeto de aplicativo de xadrez.</span><span class="sxs-lookup"><span data-stu-id="b5ee1-133">You're all set to move on to starting the chess app project.</span></span>

[<span data-ttu-id="b5ee1-134">Próxima seção: 2. Inicializar o seu projeto e o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="b5ee1-134">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)