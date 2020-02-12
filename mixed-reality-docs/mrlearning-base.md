---
title: Tutoriais de introdução-1. Visão geral e objetivos
description: Este curso mostra como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: dbae7545edb6515b5cf148fbbfb6652595d2fc0d
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129257"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="5dc1f-105">1. visão geral e objetivos</span><span class="sxs-lookup"><span data-stu-id="5dc1f-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="5dc1f-106">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="5dc1f-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5dc1f-107"><strong>Course</strong></span><span class="sxs-lookup"><span data-stu-id="5dc1f-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="5dc1f-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="5dc1f-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="5dc1f-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="5dc1f-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="5dc1f-110"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="5dc1f-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="5dc1f-111">✔️</span><span class="sxs-lookup"><span data-stu-id="5dc1f-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="5dc1f-112">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="5dc1f-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5dc1f-113">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5dc1f-113">Prerequisites</span></span>

* <span data-ttu-id="5dc1f-114">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="5dc1f-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="5dc1f-115">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="5dc1f-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="5dc1f-116">Alguma capacidade C# básica de programação</span><span class="sxs-lookup"><span data-stu-id="5dc1f-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="5dc1f-117">Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="5dc1f-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="5dc1f-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.2. X instalado e o módulo de suporte do Build plataforma universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="5dc1f-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5dc1f-119">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.2. X.</span><span class="sxs-lookup"><span data-stu-id="5dc1f-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="5dc1f-120">Isso substitui quaisquer requisitos de versão do Unity ou recomendações indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="5dc1f-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="5dc1f-121">Próxima lição: 2. inicializando o projeto e o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="5dc1f-121">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)
