---
title: Âncoras espaciais no Unreal
description: Guia para uso de âncoras espaciais em Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial anchors
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840135"
---
# <a name="spatial-anchors-in-unreal"></a>Âncoras espaciais no Unreal

As âncoras espaciais são usadas para persistir os hologramas no espaço do mundo real entre as sessões do aplicativo.  Elas são exibidas por meio do Unreal como ARPins e são salvas no repositório de âncoras do HoloLens para serem carregadas em sessões futuras. 

Antes de salvar ou carregar âncoras, primeiro verifique se o repositório de âncoras está pronto.  A tentativa de chamar qualquer uma das funções de âncora do HoloLens antes que o repositório de âncora esteja pronto não terá sucesso.  

![Armazenamento de âncoras espaciais pronto](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a>Salvar âncoras

Quando o aplicativo tem um componente que precisa ser fixado no mundo, ele pode ser salvo no repositório de âncoras com a seguinte sequência: 

![Salvar âncoras espaciais](images/unreal-spatialanchors-save.PNG)

Aqui, estamos gerando um ator em um local conhecido, criando um ARPin com esse local e um nome com base na classe do ator, adicionando o ator ao ARPin e salvando o pino no repositório de âncora do HoloLens.  O nome da âncora que escolhemos deve ser exclusivo, portanto, neste exemplo, acrescentamos o carimbo de data/hora atual.  Se a âncora for salva com êxito no repositório de âncoras, ela poderá ser inspecionada no portal do dispositivo do HoloLens em Sistema > Gerenciador de mapas > Arquivos de Âncora Salvos no Dispositivo. 

## <a name="load-anchors"></a>Carregar âncoras

Quando um aplicativo é iniciado, o blueprint a seguir pode ser chamado para restaurar os componentes aos respectivos locais de âncora:

![Carregar âncoras espaciais](images/unreal-spatialanchors-load.PNG)

Neste exemplo, iteramos em todas as âncoras no repositório de âncoras, geramos um ator na identidade e fixamos o ator no ARPin do repositório de âncoras.  É importante gerar o ator na identidade, uma vez que a âncora é responsável por reposicionar o holograma no mundo com base no local em que ele foi salvo, de modo que qualquer transformação adicionada aqui adicionará um deslocamento à âncora. 

A ID da âncora também é consultada para que atores diferentes possam ser gerados dependendo do nome salvo da âncora. 

## <a name="remove-anchors"></a>Remover âncoras 

Quando terminar de usar uma âncora, o repositório de âncoras inteiro pode ser limpo ou âncoras individuais podem ser removidas do repositório de âncoras para que não sejam incluídas em sessões futuras: 

![Remover âncoras espaciais](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a>Veja também
* [Âncoras espaciais](spatial-anchors.md)
* [Sistemas de coordenadas](coordinate-systems.md)
