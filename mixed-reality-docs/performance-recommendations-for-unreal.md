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
# <a name="performance-recommendations-for-unreal"></a>Recomendações de desempenho para o Unreal

Este artigo se baseia na discussão descrita em [Recomendações de desempenho para realidade misturada](understanding-performance-for-mixed-reality.md), mas se concentra em aprendizados específicos do ambiente do Unreal Engine.

## <a name="recommended-unreal-project-settings"></a>Configurações recomendadas de projetos do Unreal

- Usar o renderizador de VR para dispositivos móveis – nas configurações do seu projeto, verifique se a plataforma de destino está definida como "Dispositivos Móveis/Tablet" em "Projeto – Hardware de Destino"
- Desabilite o refugo de oclusão – em "Mecanismo – Renderização" na seção "Refugo", desmarque "Refugo de Oclusão"
    + Se o refugo de oclusão for necessário porque uma cena muito detalhada tem que ser renderizada, é recomendável que "Suporte ao Refugo de Oclusão por Software" esteja habilitado em "Mecanismo – Renderização". Isso permite que o Unreal faça o refugo de oclusão na CPU e evite consultas de oclusão de GPU, que têm mau desempenho no HoloLens 2.
- Habilite "Estéreo em Instância" e "Exibição Múltipla em Dispositivos Móveis" em "Mecanismo – Renderização" na categoria "VR". Talvez seja necessário desmarcar "Pós-processamento em Dispositivos Móveis" para poder marcar "Exibição Múltipla em Dispositivos Móveis"
