---
title: Introdução ao módulo MR Learning Base
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 389a23129d4dfc5819cdc45d071b678e3792089d
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523160"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="c9de7-104">1. Visão geral e objetivos</span><span class="sxs-lookup"><span data-stu-id="c9de7-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="c9de7-105">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="c9de7-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c9de7-106"><strong>Curso</strong></span><span class="sxs-lookup"><span data-stu-id="c9de7-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="c9de7-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c9de7-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="c9de7-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="c9de7-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="c9de7-109"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c9de7-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="c9de7-110">❌</span><span class="sxs-lookup"><span data-stu-id="c9de7-110">❌</span></span></td>
        <td><span data-ttu-id="c9de7-111">✔️</span><span class="sxs-lookup"><span data-stu-id="c9de7-111">✔️</span></span></td>
        <td><span data-ttu-id="c9de7-112">❌</span><span class="sxs-lookup"><span data-stu-id="c9de7-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c9de7-113">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="c9de7-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c9de7-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c9de7-114">Prerequisites</span></span>

* <span data-ttu-id="c9de7-115">Um computador com Windows 10 configurado com o nome correto [tools instalado](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="c9de7-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="c9de7-116">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="c9de7-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="c9de7-117">Alguns basic C# capacidade de programação.</span><span class="sxs-lookup"><span data-stu-id="c9de7-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="c9de7-118">Um dispositivo 2 HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="c9de7-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
