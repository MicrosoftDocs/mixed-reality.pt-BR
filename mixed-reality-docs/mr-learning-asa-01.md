---
title: Tutoriais de Âncoras Espaciais do Azure – 1. Introdução
description: Conclua este curso para saber como implementar as Âncoras Espaciais do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 6a015b4c9f6a5c1a92697ef9909443234a98ab09
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303931"
---
# <a name="1-introduction"></a><span data-ttu-id="35967-105">1. Introdução</span><span class="sxs-lookup"><span data-stu-id="35967-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="35967-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="35967-106">Overview</span></span>

<span data-ttu-id="35967-107">Bem-vindo(a) aos tutoriais de Âncoras Espaciais do Azure!</span><span class="sxs-lookup"><span data-stu-id="35967-107">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="35967-108">Nesta série de tutoriais, você aprenderá os conceitos básicos de <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">ASA</a> (Âncoras Espaciais do Azure) e como ancorar uma experiência de realidade misturada completa no mundo real.</span><span class="sxs-lookup"><span data-stu-id="35967-108">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="35967-109">Você também aprenderá a implantar o projeto no Android e no iOS.</span><span class="sxs-lookup"><span data-stu-id="35967-109">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="35967-110">Tutoriais desta série:</span><span class="sxs-lookup"><span data-stu-id="35967-110">Tutorials in this series:</span></span>

1. [<span data-ttu-id="35967-111">Introdução</span><span class="sxs-lookup"><span data-stu-id="35967-111">Introduction</span></span>](mr-learning-asa-01.md)
2. [<span data-ttu-id="35967-112">Introdução às Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="35967-112">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="35967-113">Salvar, recuperar e compartilhar Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="35967-113">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="35967-114">Exibir os comentários da Âncora Espacial do Azure</span><span class="sxs-lookup"><span data-stu-id="35967-114">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="35967-115">Âncoras Espaciais do Azure para Android e o iOS</span><span class="sxs-lookup"><span data-stu-id="35967-115">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="35967-116">Objetivos</span><span class="sxs-lookup"><span data-stu-id="35967-116">Objectives</span></span>

* <span data-ttu-id="35967-117">Saber como criar âncoras espaciais e buscá-las no Azure</span><span class="sxs-lookup"><span data-stu-id="35967-117">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="35967-118">Saber como obter o alinhamento espacial entre sessões do aplicativo</span><span class="sxs-lookup"><span data-stu-id="35967-118">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="35967-119">Saber como obter alinhamento espacial entre vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="35967-119">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="35967-120">Saber como preparar, compilar e implantar seu projeto no Android e iOS</span><span class="sxs-lookup"><span data-stu-id="35967-120">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="35967-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="35967-121">Prerequisites</span></span>

* <span data-ttu-id="35967-122">Um computador com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="35967-122">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="35967-123">SDK do Windows 10 10.0.18362.0 ou versão posterior</span><span class="sxs-lookup"><span data-stu-id="35967-123">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="35967-124">Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="35967-124">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="35967-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.15 instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="35967-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="35967-126">Conclua a seção [Criar um recurso de Âncoras Espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [Início Rápido: Criar um aplicativo HoloLens do Unity que usa as Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="35967-126">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="35967-127">Ter concluído a série de [Tutoriais de introdução](mr-learning-base-01.md) ou ter alguma experiência anterior básica com o Unity e o MRTK</span><span class="sxs-lookup"><span data-stu-id="35967-127">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="35967-128">Ter concluído a série de [Tutoriais de Âncoras Espaciais do Azure](mr-learning-asa-01.md) ou experiência anterior criando uma conta de Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="35967-128">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or previous experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="35967-129">Se você pretende implantar no Android, bem como no HoloLens</span><span class="sxs-lookup"><span data-stu-id="35967-129">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="35967-130">Um <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">desenvolvedor habilitado</a> e um dispositivo Android <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">com capacidade para ARCore</a> com conexão USB para o seu computador com Windows ou macOS</span><span class="sxs-lookup"><span data-stu-id="35967-130">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="35967-131"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.15 instalado e o módulo de suporte de Build do Android adicionado</span><span class="sxs-lookup"><span data-stu-id="35967-131"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="35967-132">Se você pretende implantar no iOS, bem como no HoloLens</span><span class="sxs-lookup"><span data-stu-id="35967-132">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="35967-133">Um computador macOS com a versão mais recente do <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e do <a href="https://cocoapods.org" target="_blank">CocoaPods</a> instaladas</span><span class="sxs-lookup"><span data-stu-id="35967-133">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="35967-134">Um dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatível com ARKit</a> com conexão USB para seu computador macOS</span><span class="sxs-lookup"><span data-stu-id="35967-134">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="35967-135"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.15 instalado e o módulo de suporte de Build do iOS adicionado</span><span class="sxs-lookup"><span data-stu-id="35967-135"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="35967-136">A versão recomendada do Kit de Ferramentas de Realidade Misturada para esta série de tutoriais é o MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="35967-136">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="35967-137">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="35967-137">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="35967-138">Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="35967-138">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="35967-139">Próximo tutorial: 2. Introdução às Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="35967-139">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
