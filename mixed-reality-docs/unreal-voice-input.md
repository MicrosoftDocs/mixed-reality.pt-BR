---
title: Entrada de voz
description: Explica como usar a entrada de voz
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Realidade mista do Windows, HoloLens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835295"
---
# <a name="voice-input"></a>Entrada de voz

Para habilitar o reconhecimento de fala no HoloLens, o desenvolvedor precisa habilitar o "microfone" no editor inreal em configurações do projeto > plataforma > os recursos de > do HoloLens. O dispositivo também deve ter o reconhecimento de fala habilitado nas configurações > privacidade > fala e usar o idioma inglês.

![Configurações de reconhecimento de fala do Windows](images/unreal/speech-recognition-settings.png)

É recomendável habilitar o reconhecimento de fala online também para a melhor qualidade possível do serviço. Os detalhes técnicos do reconhecimento de fala no HoloLens podem ser encontrados [aqui](voice-input.md)

Em seguida, o usuário verá uma caixa de diálogo sobre como habilitar o microfone quando o aplicativo for iniciado pela primeira vez. Se um usuário selecionar Sim, o aplicativo começará a receber entrada de voz.

A entrada de fala não requer uma API especial do Windows Mixed Reality e, em vez disso, é criada com base na API de mapeamento de entrada do mecanismo 4 inreal existente. Os detalhes sobre como usar a API de entrada estão [aqui](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)

Os mapeamentos de fala foram adicionados à seção ligações do mecanismo – entrada abaixo dos mapeamentos de ação e eixo. 

![Configurações de entrada do mecanismo UE4](images/unreal/engine-input.png)
 
Aqui está um exemplo de monitoramento adicionado para o mundo "salto". Qualquer palavra (s) em inglês ou sentenças curtas pode ser usada. 

Depois que um mapeamento de fala é adicionado por meio de configurações de projeto, um desenvolvedor pode usar a lógica não real padrão para manipular a entrada, como no exemplo a seguir: 
 
![Ação simples para voz](images/unreal/input-action-bp.png)
