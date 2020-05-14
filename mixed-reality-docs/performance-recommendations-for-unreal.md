---
title: Recomendações de desempenho para o Unreal
description: Recomendações para um desempenho ideal para aplicativos de realidade misturada no Unreal
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: 1fab2f714628f61a518d89795cf644e90130200a
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840195"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="5c47e-104">Recomendações de desempenho para o Unreal</span><span class="sxs-lookup"><span data-stu-id="5c47e-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="5c47e-105">Este artigo se baseia na discussão descrita em [Recomendações de desempenho para realidade misturada](understanding-performance-for-mixed-reality.md), mas se concentra em aprendizados específicos do ambiente do Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="5c47e-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unreal Engine environment.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="5c47e-106">Configurações recomendadas de projetos do Unreal</span><span class="sxs-lookup"><span data-stu-id="5c47e-106">Recommended Unreal project settings</span></span>

- <span data-ttu-id="5c47e-107">Usar o renderizador de VR para dispositivos móveis – nas configurações do seu projeto, verifique se a plataforma de destino está definida como "Dispositivos Móveis/Tablet" em "Projeto – Hardware de Destino"</span><span class="sxs-lookup"><span data-stu-id="5c47e-107">Use the mobile VR renderer- in your project settings, ensure your target platform is set to "Mobile/Tablet" under "Project – Target Hardware"</span></span>
- <span data-ttu-id="5c47e-108">Desabilite o refugo de oclusão – em "Mecanismo – Renderização" na seção "Refugo", desmarque "Refugo de Oclusão"</span><span class="sxs-lookup"><span data-stu-id="5c47e-108">Disable occlusion culling- under "Engine – Rendering" in the "Culling" section, uncheck "Occlusion Culling"</span></span>
    + <span data-ttu-id="5c47e-109">Se o refugo de oclusão for necessário porque uma cena muito detalhada tem que ser renderizada, é recomendável que "Suporte ao Refugo de Oclusão por Software" esteja habilitado em "Mecanismo – Renderização".</span><span class="sxs-lookup"><span data-stu-id="5c47e-109">If occlusion culling is required because a very detailed scene needs to be rendered, it is recommended that "Support Software Occlusion Culling" is enabled Under "Engine – Rendering".</span></span> <span data-ttu-id="5c47e-110">Isso permite que o Unreal faça o refugo de oclusão na CPU e evite consultas de oclusão de GPU, que têm mau desempenho no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5c47e-110">This allows Unreal to do occlusion culling on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
- <span data-ttu-id="5c47e-111">Habilite "Estéreo em Instância" e "Exibição Múltipla em Dispositivos Móveis" em "Mecanismo – Renderização" na categoria "VR".</span><span class="sxs-lookup"><span data-stu-id="5c47e-111">Enable both "Instanced Stereo" and "Mobile Multi-View" under "Engine – Rendering" in the "VR" category.</span></span> <span data-ttu-id="5c47e-112">Talvez seja necessário desmarcar "Pós-processamento em Dispositivos Móveis" para poder marcar "Exibição Múltipla em Dispositivos Móveis"</span><span class="sxs-lookup"><span data-stu-id="5c47e-112">You may need to uncheck "Mobile Post-Processing" in order to be able to check "Mobile Multi-View"</span></span>
