---
title: 1. Introdução
description: Parte 1 de um tutorial para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 3ca47cfe7bb0a733932f3777cc8b531ef9df8e71
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840125"
---
# <a name="1-getting-started"></a><span data-ttu-id="ec2a9-104">1. Introdução</span><span class="sxs-lookup"><span data-stu-id="ec2a9-104">1. Getting started</span></span>

<span data-ttu-id="ec2a9-105">Este é um tutorial passo a passo que mostrará como criar um aplicativo de xadrez interativo do HoloLens 2 usando o Unreal Engine 4.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-105">This is a step by step tutorial that will show you how to build an interactive HoloLens 2 chess app using Unreal Engine 4.</span></span> <span data-ttu-id="ec2a9-106">Você também aprenderá a usar o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada para Unreal e acelerar o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-106">You will also learn how to use the UX Tools plugin from the Mixed Reality Toolkit for Unreal to speed up development.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="ec2a9-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ec2a9-107">Prerequisites</span></span>

* <span data-ttu-id="ec2a9-108">Windows 10 1809 ou posterior</span><span class="sxs-lookup"><span data-stu-id="ec2a9-108">Windows 10 1809 or later</span></span>
* <span data-ttu-id="ec2a9-109">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="ec2a9-109">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="ec2a9-110">Unreal Engine 4.25 ou posterior</span><span class="sxs-lookup"><span data-stu-id="ec2a9-110">Unreal Engine 4.25 or later</span></span>
* <span data-ttu-id="ec2a9-111">Dispositivo do Microsoft HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode) ou Emulador</span><span class="sxs-lookup"><span data-stu-id="ec2a9-111">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="ec2a9-112">Visual Studio 2019 (com as cargas de trabalho e os componentes abaixo)</span><span class="sxs-lookup"><span data-stu-id="ec2a9-112">Visual Studio 2019 (with below workloads and components)</span></span>

### <a name="installing-visual-studio-2019-workloads-and-components"></a><span data-ttu-id="ec2a9-113">Instalando o Visual Studio 2019, as cargas de trabalho e os componentes</span><span class="sxs-lookup"><span data-stu-id="ec2a9-113">Installing Visual Studio 2019, workloads, and components</span></span>
1. <span data-ttu-id="ec2a9-114">Instale ou atualize para a versão mais recente do Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="ec2a9-114">Install or and update to the latest version of Visual Studio 2019</span></span>
* [<span data-ttu-id="ec2a9-115">Baixar o Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="ec2a9-115">Download Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/)
2. <span data-ttu-id="ec2a9-116">Instale as seguintes cargas de trabalho:</span><span class="sxs-lookup"><span data-stu-id="ec2a9-116">Install the following workloads:</span></span>
* <span data-ttu-id="ec2a9-117">Desenvolvimento para desktop com C++</span><span class="sxs-lookup"><span data-stu-id="ec2a9-117">Desktop development with C++</span></span>
* <span data-ttu-id="ec2a9-118">Desenvolvimento para área de trabalho com .NET</span><span class="sxs-lookup"><span data-stu-id="ec2a9-118">.NET desktop development</span></span>
* <span data-ttu-id="ec2a9-119">Desenvolvimento para a Plataforma Universal do Windows</span><span class="sxs-lookup"><span data-stu-id="ec2a9-119">Universal Windows Platform development</span></span>
3. <span data-ttu-id="ec2a9-120">Instale os seguintes componentes individuais:</span><span class="sxs-lookup"><span data-stu-id="ec2a9-120">Install the following individual components:</span></span>
* <span data-ttu-id="ec2a9-121">Compiladores, ferramentas de build e runtimes > ferramentas de build MSVC v142 – VS 2019 C++ ARM64 (versão mais recente)</span><span class="sxs-lookup"><span data-stu-id="ec2a9-121">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

[<span data-ttu-id="ec2a9-122">Próxima seção: 2. Inicializar o seu projeto e o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="ec2a9-122">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)