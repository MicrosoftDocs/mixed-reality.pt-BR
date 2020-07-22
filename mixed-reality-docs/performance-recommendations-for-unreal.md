---
title: Recomendações de desempenho para o Unreal
description: Recomendações para um desempenho ideal para aplicativos de realidade misturada no Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: a7972962eeb2b1480a7da38210b5ee77104f508b
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303627"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="228ef-104">Recomendações de desempenho para o Unreal</span><span class="sxs-lookup"><span data-stu-id="228ef-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="228ef-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="228ef-105">Overview</span></span>

<span data-ttu-id="228ef-106">Este artigo se baseia na discussão descrita em [recomendações de desempenho para realidade misturada](understanding-performance-for-mixed-reality.md), mas se concentra em recursos específicos do Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="228ef-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="228ef-107">Você é incentivado a detectar os gargalos do aplicativo, analisar e criar o perfil de aplicativos de realidade misturada e correções de desempenho gerais antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="228ef-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="228ef-108">Configurações recomendadas de projetos do Unreal</span><span class="sxs-lookup"><span data-stu-id="228ef-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="228ef-109">Você pode encontrar cada uma das configurações a seguir em **Editar > Configurações do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="228ef-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="228ef-110">Como usar o renderizador de VR para dispositivos móveis:</span><span class="sxs-lookup"><span data-stu-id="228ef-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="228ef-111">Role até a seção **Projeto**, selecione **Hardware de Destino** e defina a plataforma de destino como **Celular/Tablet**</span><span class="sxs-lookup"><span data-stu-id="228ef-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Configuração de destino para dispositivos móveis](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="228ef-113">Desabilitando a remoção por oclusão:</span><span class="sxs-lookup"><span data-stu-id="228ef-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="228ef-114">Role até a seção **Mecanismo**, selecione **Renderização**, expanda a seção **Remoção** e desmarque **Remoção por Oclusão**.</span><span class="sxs-lookup"><span data-stu-id="228ef-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="228ef-115">Se você precisa usar a remoção por oclusão em uma cena detalhada que está sendo renderizada, recomendamos habilitar o **Suporte a Remoção por Oclusão de Software** em **Mecanismo > Renderização**.</span><span class="sxs-lookup"><span data-stu-id="228ef-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="228ef-116">Isso permite que o Unreal faça o trabalho na CPU e evite consultas de oclusão de GPU, que têm mau desempenho no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="228ef-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![Desabilitar a remoção de oclusão](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="228ef-118">Uso da exibição múltipla em dispositivos móveis:</span><span class="sxs-lookup"><span data-stu-id="228ef-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="228ef-119">Role a página até a seção **Mecanismo**, selecione **Renderização**, expanda a seção **VR** e habilite **Estéreo Instanciado** e **Exibição Múltipla em Dispositivos Móveis**.</span><span class="sxs-lookup"><span data-stu-id="228ef-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="228ef-120">O HDR móvel deve estar desmarcado.</span><span class="sxs-lookup"><span data-stu-id="228ef-120">Mobile HDR should be unchecked.</span></span>

![Configurações de renderização de VR](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="228ef-122">Definir o **Número máximo de cascatas de CSM para renderizar** como **1** e **Luzes de spot/ponto máximas** como **0**.</span><span class="sxs-lookup"><span data-stu-id="228ef-122">Setting the **Maximum number of CSM cascades to render** to **1** and **Max Movable Spotlights / Point Lights** to **0**.</span></span> 
