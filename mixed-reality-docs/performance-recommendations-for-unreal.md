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

![Desabilitar a remoção de oclusão](images/unreal/performance-recommendations-img-02.png)

3. Uso da exibição múltipla em dispositivos móveis:
    * Role a página até a seção **Mecanismo**, selecione **Renderização**, expanda a seção **VR** e habilite **Estéreo Instanciado** e **Exibição Múltipla em Dispositivos Móveis**. O HDR móvel deve estar desmarcado.

![Configurações de renderização de VR](images/unreal/performance-recommendations-img-03.png)

4. Definir o **Número máximo de cascatas de CSM para renderizar** como **1** e **Luzes de spot/ponto máximas** como **0**. 
