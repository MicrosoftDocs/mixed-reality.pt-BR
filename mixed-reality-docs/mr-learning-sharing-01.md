---
title: Tutoriais de recursos multiusuário – 1. Introdução
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: ebdef9818aace28b32e91384cd9d3278da2733b4
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376338"
---
# <a name="1-introduction"></a><span data-ttu-id="658c3-105">1. Introdução</span><span class="sxs-lookup"><span data-stu-id="658c3-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="658c3-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="658c3-106">Overview</span></span>

<span data-ttu-id="658c3-107">Bem-vindo(a) aos tutoriais de funcionalidades de vários usuários!</span><span class="sxs-lookup"><span data-stu-id="658c3-107">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="658c3-108">Nesta série de tutoriais, você aprenderá os conceitos básicos da criação de uma experiência multiusuário usando a PUN (<a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a>).</span><span class="sxs-lookup"><span data-stu-id="658c3-108">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="658c3-109">O PUN é uma das várias opções de rede disponíveis para os desenvolvedores de realidade misturada criarem experiências compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="658c3-109">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="658c3-110">Tutoriais desta série:</span><span class="sxs-lookup"><span data-stu-id="658c3-110">Tutorials in this series:</span></span>

* [<span data-ttu-id="658c3-111">Configurar o Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="658c3-111">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="658c3-112">Como conectar vários usuários</span><span class="sxs-lookup"><span data-stu-id="658c3-112">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="658c3-113">Compartilhar movimentações de objeto com vários usuários</span><span class="sxs-lookup"><span data-stu-id="658c3-113">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="658c3-114">Integrar Âncoras Espaciais do Azure a uma experiência compartilhada</span><span class="sxs-lookup"><span data-stu-id="658c3-114">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="658c3-115">Objetivos</span><span class="sxs-lookup"><span data-stu-id="658c3-115">Objectives</span></span>

* <span data-ttu-id="658c3-116">Saiba como criar um aplicativo PUN e conectar seu projeto do Unity a ele</span><span class="sxs-lookup"><span data-stu-id="658c3-116">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="658c3-117">Saiba como conectar vários usuários em uma experiência compartilhada</span><span class="sxs-lookup"><span data-stu-id="658c3-117">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="658c3-118">Saiba como compartilhar os movimentos de objeto com outros usuários</span><span class="sxs-lookup"><span data-stu-id="658c3-118">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="658c3-119">Saber como obter alinhamento espacial entre vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="658c3-119">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="658c3-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="658c3-120">Prerequisites</span></span>

* <span data-ttu-id="658c3-121">Um computador com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="658c3-121">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="658c3-122">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="658c3-122">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="658c3-123">Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="658c3-123">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="658c3-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.15 instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="658c3-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="658c3-125">Conclua a seção [Criar um recurso de Âncoras Espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [Início Rápido: Criar um aplicativo HoloLens do Unity que usa as Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="658c3-125">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="658c3-126">Ter concluído a série de [Tutoriais de introdução](mr-learning-base-01.md) ou ter alguma experiência anterior básica com o Unity e o MRTK</span><span class="sxs-lookup"><span data-stu-id="658c3-126">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="658c3-127">Ter concluído a série de [Tutoriais de Âncoras Espaciais do Azure](mr-learning-asa-01.md) ou experiência anterior criando uma conta de Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="658c3-127">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="658c3-128">Se você pretende implantar no Android, bem como no HoloLens</span><span class="sxs-lookup"><span data-stu-id="658c3-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="658c3-129">Um <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">desenvolvedor habilitado</a> e um dispositivo Android <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">com capacidade para ARCore</a> com conexão USB para o seu computador com Windows ou macOS</span><span class="sxs-lookup"><span data-stu-id="658c3-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="658c3-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.15 instalado e o módulo de suporte de Build do Android adicionado</span><span class="sxs-lookup"><span data-stu-id="658c3-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="658c3-131">Se você pretende implantar no iOS, bem como no HoloLens</span><span class="sxs-lookup"><span data-stu-id="658c3-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="658c3-132">Um computador macOS com a versão mais recente do <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e do <a href="https://cocoapods.org" target="_blank">CocoaPods</a> instaladas</span><span class="sxs-lookup"><span data-stu-id="658c3-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="658c3-133">Um dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatível com ARKit</a> com conexão USB para seu computador macOS</span><span class="sxs-lookup"><span data-stu-id="658c3-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="658c3-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.15 instalado e o módulo de suporte de Build do iOS adicionado</span><span class="sxs-lookup"><span data-stu-id="658c3-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="658c3-135">A versão recomendada do Kit de Ferramentas de Realidade Misturada para esta série de tutoriais é o MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="658c3-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="658c3-136">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="658c3-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="658c3-137">Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="658c3-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="658c3-138">Próximo tutorial: 2. Configurar uma rede Unity Photon</span><span class="sxs-lookup"><span data-stu-id="658c3-138">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
