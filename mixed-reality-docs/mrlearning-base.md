---
title: Tutoriais de introdução – 1. Visão geral e objetivos
description: Este curso mostra como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 36c12d82759b8ac2ba24aa9af37a096e0faf5fb5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "80082045"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="8a401-105">1. Visão geral e objetivos</span><span class="sxs-lookup"><span data-stu-id="8a401-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="8a401-106">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="8a401-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8a401-107"><strong>Curso</strong></span><span class="sxs-lookup"><span data-stu-id="8a401-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="8a401-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8a401-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="8a401-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="8a401-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="8a401-110"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="8a401-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="8a401-111">✔️</span><span class="sxs-lookup"><span data-stu-id="8a401-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="8a401-112">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="8a401-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="8a401-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8a401-113">Prerequisites</span></span>

* <span data-ttu-id="8a401-114">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="8a401-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="8a401-115">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="8a401-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="8a401-116">Alguma habilidade básica de programação em C#</span><span class="sxs-lookup"><span data-stu-id="8a401-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="8a401-117">Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="8a401-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="8a401-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.2.X instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="8a401-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a401-119">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="8a401-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="8a401-120">Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="8a401-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="8a401-121">Próxima lição: 2. Inicializar o seu projeto e o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="8a401-121">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)
