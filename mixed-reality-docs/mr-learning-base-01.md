---
title: Tutoriais de introdução – 1. Introdução
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 330863d36abe051e8fe17b87ce913b1b110e2d3d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376428"
---
# <a name="1-introduction"></a><span data-ttu-id="e9eba-105">1. Introdução</span><span class="sxs-lookup"><span data-stu-id="e9eba-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="e9eba-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e9eba-106">Overview</span></span>

<span data-ttu-id="e9eba-107">Bem-vindo(a) à série de tutoriais d Introdução!</span><span class="sxs-lookup"><span data-stu-id="e9eba-107">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="e9eba-108">No decorrer destes tutoriais, você aprenderá sobre o MRTK (Kit de ferramentas de realidade misturada) e alguns dos recursos que ele tem a oferecer.</span><span class="sxs-lookup"><span data-stu-id="e9eba-108">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="e9eba-109">Você também criará uma experiência de realidade misturada na qual o usuário pode explorar um holograma modelado conforme o Mars Rover da NASA.</span><span class="sxs-lookup"><span data-stu-id="e9eba-109">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="e9eba-110">Ao final desta série, você terá uma noção do MRTK e como ele pode acelerar seu processo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="e9eba-110">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="e9eba-111">Os tutoriais desta série foram concebidos de modo sequencial, portanto, siga-os na ordem correta:</span><span class="sxs-lookup"><span data-stu-id="e9eba-111">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. [<span data-ttu-id="e9eba-112">Introdução</span><span class="sxs-lookup"><span data-stu-id="e9eba-112">Introduction</span></span>](mr-learning-base-01.md)
2. [<span data-ttu-id="e9eba-113">Como inicializar o seu projeto e implantar o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="e9eba-113">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="e9eba-114">Como configurar os perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="e9eba-114">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="e9eba-115">Como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="e9eba-115">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="e9eba-116">Criar conteúdo dinâmico usando Solucionadores</span><span class="sxs-lookup"><span data-stu-id="e9eba-116">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="e9eba-117">Como criar interfaces do usuário</span><span class="sxs-lookup"><span data-stu-id="e9eba-117">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="e9eba-118">Como interagir com objetos 3D</span><span class="sxs-lookup"><span data-stu-id="e9eba-118">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="e9eba-119">Como usar o acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="e9eba-119">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="e9eba-120">Como usar comandos de voz</span><span class="sxs-lookup"><span data-stu-id="e9eba-120">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="e9eba-121">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e9eba-121">Objectives</span></span>

* <span data-ttu-id="e9eba-122">Saiba como configurar o Unity para MRTK</span><span class="sxs-lookup"><span data-stu-id="e9eba-122">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="e9eba-123">Saiba como criar e implantar em seu dispositivo</span><span class="sxs-lookup"><span data-stu-id="e9eba-123">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="e9eba-124">Saiba como usar alguns dos principais recursos do MRTK</span><span class="sxs-lookup"><span data-stu-id="e9eba-124">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="e9eba-125">Criar uma experiência de realidade misturada completa</span><span class="sxs-lookup"><span data-stu-id="e9eba-125">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e9eba-126">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e9eba-126">Prerequisites</span></span>

* <span data-ttu-id="e9eba-127">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="e9eba-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="e9eba-128">[SDK do Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="e9eba-128">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="e9eba-129">Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="e9eba-129">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="e9eba-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.15 instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="e9eba-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="e9eba-131">A versão recomendada do MRTK para esta série de tutoriais é a MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="e9eba-131">The recommended MRTK version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="e9eba-132">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="e9eba-132">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="e9eba-133">Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="e9eba-133">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="e9eba-134">Próximo tutorial: 2. Como inicializar o seu projeto e implantar o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="e9eba-134">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
