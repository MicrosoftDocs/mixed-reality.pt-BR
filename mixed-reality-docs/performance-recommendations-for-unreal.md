---
title: Recomendações de desempenho para o Unreal
description: Recomendações para um desempenho ideal para aplicativos de realidade misturada no Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: 9f128a3ef09f29fc745c21b09b7ec97f5db33605
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533118"
---
# <a name="performance-recommendations-for-unreal"></a>Recomendações de desempenho para o Unreal

## <a name="overview"></a>Visão geral

Este artigo se baseia na discussão descrita em [recomendações de desempenho para realidade misturada](understanding-performance-for-mixed-reality.md), mas se concentra em recursos específicos do Unreal Engine. Você é incentivado a detectar os gargalos do aplicativo, analisar e criar o perfil de aplicativos de realidade misturada e correções de desempenho gerais antes de continuar.

## <a name="recommended-unreal-project-settings"></a>Configurações recomendadas de projetos do Unreal
Você pode encontrar cada uma das configurações a seguir em **Editar > Configurações do Projeto**.

1. Como usar o renderizador de VR para dispositivos móveis:
    * Role até a seção **Projeto**, selecione **Hardware de Destino** e defina a plataforma de destino como **Celular/Tablet**

![Configuração de destino para dispositivos móveis](images/unreal/performance-recommendations-img-01.png)

2. Desabilitando a remoção por oclusão:
    * Role até a seção **Mecanismo**, selecione **Renderização**, expanda a seção **Remoção** e desmarque **Remoção por Oclusão**.
        + Se você precisa usar a remoção por oclusão em uma cena detalhada que está sendo renderizada, recomendamos habilitar o **Suporte a Remoção por Oclusão de Software** em **Mecanismo > Renderização**. Isso permite que o Unreal faça o trabalho na CPU e evite consultas de oclusão de GPU, que têm mau desempenho no HoloLens 2.

![Configuração de destino para dispositivos móveis](images/unreal/performance-recommendations-img-02.png)

3. Como atualizar renderização de VR:
    * Role a página até a seção **Mecanismo**, selecione **Renderização**, expanda a seção **VR** e habilite **Estéreo Instanciado** e **Exibição Múltipla em Dispositivos Móveis**.
        + Talvez seja necessário desmarcar **Pós-processamento em Dispositivos Móveis** para poder marcar **Exibição Múltipla em Dispositivos Móveis**

![Configuração de destino para dispositivos móveis](images/unreal/performance-recommendations-img-03.png)
