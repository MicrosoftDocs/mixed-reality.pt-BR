---
title: Entrada de voz
description: Tutorial sobre como configurar e usar a entrada de voz no HoloLens 2 e no mecanismo inreal
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Realidade mista do Windows, inreal, Engine 4, UE4, HoloLens 2, voz, entrada de voz, reconhecimento de fala, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, desenvolvimento de jogos
ms.openlocfilehash: c5de0cd912674ccd681fd398fb6fe5fd345ab6f2
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330628"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="d20a6-104">Entrada de voz em não real</span><span class="sxs-lookup"><span data-stu-id="d20a6-104">Voice Input in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="d20a6-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d20a6-105">Overview</span></span>
<span data-ttu-id="d20a6-106">A entrada de voz permite interagir com um holograma sem a necessidade de usar gestos de mão e tem suporte no HoloLens (1º gen) e no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d20a6-106">Voice input allows you to interact with a hologram without having to use hand gestures and is supported on HoloLens (1st Gen) and HoloLens 2.</span></span> <span data-ttu-id="d20a6-107">Ele é alimentado pelo mesmo mecanismo que dá suporte à fala em todos os outros aplicativos universais do Windows e pode adicionar uma sensação natural à maneira como você interage em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="d20a6-107">It's powered by the same engine that supports speech in all other Universal Windows Apps and can add a natural feeling to the way you interact in mixed reality.</span></span> 

<span data-ttu-id="d20a6-108">Os recursos de voz com suporte incluem:</span><span class="sxs-lookup"><span data-stu-id="d20a6-108">Supported voice features include:</span></span>
- <span data-ttu-id="d20a6-109">O [comando SELECT](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span><span class="sxs-lookup"><span data-stu-id="d20a6-109">The [Select command](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span></span>
- [<span data-ttu-id="d20a6-110">Ei, Cortana</span><span class="sxs-lookup"><span data-stu-id="d20a6-110">Hey, Cortana</span></span>](https://docs.microsoft.com/windows/mixed-reality/voice-input#hey-cortana)
- <span data-ttu-id="d20a6-111">"Vê-lo, digamos" para interação entre botões e rótulos</span><span class="sxs-lookup"><span data-stu-id="d20a6-111">"See it, say it" for button and label interaction</span></span>
- <span data-ttu-id="d20a6-112">Ditado</span><span class="sxs-lookup"><span data-stu-id="d20a6-112">Dictation</span></span>

<span data-ttu-id="d20a6-113">Para obter mais informações, confira a documentação principal de [entrada de voz](voice-input.md) .</span><span class="sxs-lookup"><span data-stu-id="d20a6-113">For more information, check out the main [Voice Input](voice-input.md) documentation.</span></span>

## <a name="enabling-speech-recognition"></a><span data-ttu-id="d20a6-114">Habilitando o reconhecimento de fala</span><span class="sxs-lookup"><span data-stu-id="d20a6-114">Enabling Speech Recognition</span></span>

<span data-ttu-id="d20a6-115">Para habilitar o reconhecimento de fala no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="d20a6-115">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="d20a6-116">Selecione **configurações do projeto > plataforma > recursos de > do HoloLens** e habilite o **microfone**.</span><span class="sxs-lookup"><span data-stu-id="d20a6-116">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="d20a6-117">Habilitado Recogniztion de fala em **configurações > privacidade > fala** e selecione **Inglês**.</span><span class="sxs-lookup"><span data-stu-id="d20a6-117">Enabled speech recogniztion in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="d20a6-118">O reconhecimento de fala sempre funciona no idioma de exibição do Windows configurado no aplicativo **configurações** .</span><span class="sxs-lookup"><span data-stu-id="d20a6-118">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="d20a6-119">É recomendável que você também habilite o **reconhecimento de fala online** para a melhor qualidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="d20a6-119">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Configurações de reconhecimento de fala do Windows](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="d20a6-121">Uma caixa de diálogo será exibida quando o aplicativo começar a perguntar se você deseja habilitar o microfone.</span><span class="sxs-lookup"><span data-stu-id="d20a6-121">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="d20a6-122">Selecionar **Sim** inicia a entrada de voz no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d20a6-122">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="d20a6-123">A entrada de voz não requer nenhuma API especial do Windows Mixed Reality; Ele foi criado na API de mapeamento de [entrada](https://docs.unrealengine.com/Gameplay/Input/index.html) do mecanismo 4 inreal existente.</span><span class="sxs-lookup"><span data-stu-id="d20a6-123">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="d20a6-124">Adicionando mapeamentos de fala</span><span class="sxs-lookup"><span data-stu-id="d20a6-124">Adding Speech Mappings</span></span>
<span data-ttu-id="d20a6-125">Conectar a fala a ação é uma etapa importante ao usar a entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="d20a6-125">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="d20a6-126">Esses mapeamentos monitoram o aplicativo para palavras-chave de fala que um usuário pode dizer e, em seguida, dispara uma ação vinculada.</span><span class="sxs-lookup"><span data-stu-id="d20a6-126">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="d20a6-127">Você pode encontrar mapeamentos de fala de:</span><span class="sxs-lookup"><span data-stu-id="d20a6-127">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="d20a6-128">Selecione **editar > configurações do projeto**, role até a seção **mecanismo** e clique em **entrada**.</span><span class="sxs-lookup"><span data-stu-id="d20a6-128">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="d20a6-129">Para adicionar um novo mapeamento de fala para um comando de salto:</span><span class="sxs-lookup"><span data-stu-id="d20a6-129">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="d20a6-130">Clique no **+** ícone ao lado de **elementos da matriz** e preencha os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="d20a6-130">Click the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="d20a6-131">**jumpWord** para o **nome da ação**</span><span class="sxs-lookup"><span data-stu-id="d20a6-131">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="d20a6-132">**ir** para **palavra-chave de fala**</span><span class="sxs-lookup"><span data-stu-id="d20a6-132">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="d20a6-133">Qualquer palavra (s) em inglês ou sentenças curtas podem ser usadas como uma palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="d20a6-133">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Configurações de entrada do mecanismo UE4](images/unreal/engine-input.png)

<span data-ttu-id="d20a6-135">Os mapeamentos de fala podem ser usados como componentes de entrada como mapeamentos de ação ou de eixo ou como nós de plano gráfico no grafo de eventos.</span><span class="sxs-lookup"><span data-stu-id="d20a6-135">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="d20a6-136">Por exemplo, você pode vincular o comando de salto para imprimir dois logs diferentes dependendo de quando a palavra for falada:</span><span class="sxs-lookup"><span data-stu-id="d20a6-136">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="d20a6-137">Clique duas vezes em um plano gráfico para abri-lo no **grafo de eventos**.</span><span class="sxs-lookup"><span data-stu-id="d20a6-137">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="d20a6-138">**Clique com o botão direito do mouse** e pesquise pelo **nome da ação** do seu mapeamento de fala (neste caso, **jumpWord**) e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="d20a6-138">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter**.</span></span> <span data-ttu-id="d20a6-139">Isso adiciona um nó de **ação de entrada** ao grafo.</span><span class="sxs-lookup"><span data-stu-id="d20a6-139">This adds an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="d20a6-140">Arraste e solte o pino **pressionado** para **Imprimir** o nó da cadeia de caracteres, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="d20a6-140">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="d20a6-141">Você pode deixar o PIN **liberado** vazio, ele não executará nada para mapeamentos de fala.</span><span class="sxs-lookup"><span data-stu-id="d20a6-141">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Ação simples para voz](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="d20a6-143">Reproduza o aplicativo, digamos que a palavra **salte** e assista ao console para imprimir os logs!</span><span class="sxs-lookup"><span data-stu-id="d20a6-143">Play the app, say the word **jump** and watch the console print out the logs!</span></span>

<span data-ttu-id="d20a6-144">Essa é toda a configuração que você precisará para começar a adicionar entrada de voz aos seus aplicativos de HoloLens em um não real.</span><span class="sxs-lookup"><span data-stu-id="d20a6-144">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="d20a6-145">Você pode encontrar mais informações sobre a fala e a interatividade nos links abaixo e certifique-se de pensar sobre a experiência que está criando para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="d20a6-145">You can find more information on speech and interactivity can be found at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="see-also"></a><span data-ttu-id="d20a6-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="d20a6-146">See also</span></span>
* [<span data-ttu-id="d20a6-147">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="d20a6-147">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="d20a6-148">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="d20a6-148">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="d20a6-149">Entrada do MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="d20a6-149">MR Input 212: Voice</span></span>](holograms-212.md)
