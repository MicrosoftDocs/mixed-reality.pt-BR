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
# <a name="voice-input"></a><span data-ttu-id="944d6-104">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="944d6-104">Voice Input</span></span>

<span data-ttu-id="944d6-105">Para habilitar o reconhecimento de fala no HoloLens, o desenvolvedor precisa habilitar o "microfone" no editor inreal em configurações do projeto > plataforma > os recursos de > do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="944d6-105">To enable speech recognition on HoloLens, the developer needs to enable “Microphone” in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> <span data-ttu-id="944d6-106">O dispositivo também deve ter o reconhecimento de fala habilitado nas configurações > privacidade > fala e usar o idioma inglês.</span><span class="sxs-lookup"><span data-stu-id="944d6-106">The device must also have Speech recognition enabled in Settings > Privacy > Speech and use the English language.</span></span>

![Configurações de reconhecimento de fala do Windows](images/unreal/speech-recognition-settings.png)

<span data-ttu-id="944d6-108">É recomendável habilitar o reconhecimento de fala online também para a melhor qualidade possível do serviço.</span><span class="sxs-lookup"><span data-stu-id="944d6-108">It’s recommended to enable Online speech recognition too for the best possible quality of the service.</span></span> <span data-ttu-id="944d6-109">Os detalhes técnicos do reconhecimento de fala no HoloLens podem ser encontrados [aqui](voice-input.md)</span><span class="sxs-lookup"><span data-stu-id="944d6-109">Technical details for speech recognition on HoloLens can be found [here](voice-input.md)</span></span>

<span data-ttu-id="944d6-110">Em seguida, o usuário verá uma caixa de diálogo sobre como habilitar o microfone quando o aplicativo for iniciado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="944d6-110">Then user will see a dialog about enabling the microphone when the application first starts.</span></span> <span data-ttu-id="944d6-111">Se um usuário selecionar Sim, o aplicativo começará a receber entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="944d6-111">If a user selects Yes, the application will begin getting voice input.</span></span>

<span data-ttu-id="944d6-112">A entrada de fala não requer uma API especial do Windows Mixed Reality e, em vez disso, é criada com base na API de mapeamento de entrada do mecanismo 4 inreal existente.</span><span class="sxs-lookup"><span data-stu-id="944d6-112">Speech input doesn’t require a special Windows Mixed Reality API and is instead built upon the existing Unreal Engine 4 Input mapping API.</span></span> <span data-ttu-id="944d6-113">Os detalhes sobre como usar a API de entrada estão [aqui](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)</span><span class="sxs-lookup"><span data-stu-id="944d6-113">Details on how to use the Input API are [here](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)</span></span>

<span data-ttu-id="944d6-114">Os mapeamentos de fala foram adicionados à seção ligações do mecanismo – entrada abaixo dos mapeamentos de ação e eixo.</span><span class="sxs-lookup"><span data-stu-id="944d6-114">Speech Mappings have been added to the Bindings section of Engine – Input below Action and Axis Mappings.</span></span> 

![Configurações de entrada do mecanismo UE4](images/unreal/engine-input.png)
 
<span data-ttu-id="944d6-116">Aqui está um exemplo de monitoramento adicionado para o mundo "salto".</span><span class="sxs-lookup"><span data-stu-id="944d6-116">Here is an example of added monitoring for the world “jump”.</span></span> <span data-ttu-id="944d6-117">Qualquer palavra (s) em inglês ou sentenças curtas pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="944d6-117">Any English word(s) or short sentences can be used.</span></span> 

<span data-ttu-id="944d6-118">Depois que um mapeamento de fala é adicionado por meio de configurações de projeto, um desenvolvedor pode usar a lógica não real padrão para manipular a entrada, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="944d6-118">After a Speech Mapping is added via Project Settings, a developer can then use standard Unreal logic to handle the input, as in the following example:</span></span> 
 
![Ação simples para voz](images/unreal/input-action-bp.png)
