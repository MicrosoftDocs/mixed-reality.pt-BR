---
title: Entrada de voz
description: Tutorial sobre como configurar e usar a entrada de voz no HoloLens 2 e no mecanismo inreal
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Realidade mista do Windows, inreal, Engine 4, UE4, HoloLens 2, voz, entrada de voz, reconhecimento de fala, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, desenvolvimento de jogos
ms.openlocfilehash: 134a8c5bbeb700a973d3732d24fa9078feb568ef
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84551782"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="ab94b-104">Entrada de voz em não real</span><span class="sxs-lookup"><span data-stu-id="ab94b-104">Voice Input in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="ab94b-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ab94b-105">Overview</span></span>
<span data-ttu-id="ab94b-106">A entrada de voz em forma inreal permite que você interaja com um holograma sem precisar usar gestos de mão e só tem suporte para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ab94b-106">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="ab94b-107">Embora a entrada de voz no HoloLens 2 seja alimentada pelo mesmo mecanismo que dá suporte à fala em todos os outros aplicativos universais do Windows, o não real usa um mecanismo mais limitado próprio para processar a entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="ab94b-107">Even though voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, Unreal uses a more limited engine of its own to process voice input.</span></span> <span data-ttu-id="ab94b-108">Isso limita os recursos de entrada de voz em mapeamentos de fala inreais para predefinidos, que é abordado nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="ab94b-108">This limits voice input features in Unreal to predefined speech mappings, which is covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="ab94b-109">Habilitando o reconhecimento de fala</span><span class="sxs-lookup"><span data-stu-id="ab94b-109">Enabling Speech Recognition</span></span>

<span data-ttu-id="ab94b-110">Para habilitar o reconhecimento de fala no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="ab94b-110">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="ab94b-111">Selecione **configurações do projeto > plataforma > recursos de > do HoloLens** e habilite o **microfone**.</span><span class="sxs-lookup"><span data-stu-id="ab94b-111">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="ab94b-112">Habilitado o reconhecimento de fala em **configurações > privacidade > fala** e selecione **Inglês**.</span><span class="sxs-lookup"><span data-stu-id="ab94b-112">Enabled speech recognition in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="ab94b-113">O reconhecimento de fala sempre funciona no idioma de exibição do Windows configurado no aplicativo **configurações** .</span><span class="sxs-lookup"><span data-stu-id="ab94b-113">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="ab94b-114">É recomendável que você também habilite o **reconhecimento de fala online** para a melhor qualidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="ab94b-114">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Configurações de reconhecimento de fala do Windows](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="ab94b-116">Uma caixa de diálogo será exibida quando o aplicativo começar a perguntar se você deseja habilitar o microfone.</span><span class="sxs-lookup"><span data-stu-id="ab94b-116">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="ab94b-117">Selecionar **Sim** inicia a entrada de voz no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab94b-117">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="ab94b-118">A entrada de voz não requer nenhuma API especial do Windows Mixed Reality; Ele foi criado na API de mapeamento de [entrada](https://docs.unrealengine.com/Gameplay/Input/index.html) do mecanismo 4 inreal existente.</span><span class="sxs-lookup"><span data-stu-id="ab94b-118">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="ab94b-119">Adicionando mapeamentos de fala</span><span class="sxs-lookup"><span data-stu-id="ab94b-119">Adding Speech Mappings</span></span>
<span data-ttu-id="ab94b-120">Conectar a fala a ação é uma etapa importante ao usar a entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="ab94b-120">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="ab94b-121">Esses mapeamentos monitoram o aplicativo para palavras-chave de fala que um usuário pode dizer e, em seguida, dispara uma ação vinculada.</span><span class="sxs-lookup"><span data-stu-id="ab94b-121">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="ab94b-122">Você pode encontrar mapeamentos de fala de:</span><span class="sxs-lookup"><span data-stu-id="ab94b-122">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="ab94b-123">Selecione **editar > configurações do projeto**, role até a seção **mecanismo** e clique em **entrada**.</span><span class="sxs-lookup"><span data-stu-id="ab94b-123">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="ab94b-124">Para adicionar um novo mapeamento de fala para um comando de salto:</span><span class="sxs-lookup"><span data-stu-id="ab94b-124">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="ab94b-125">Clique no **+** ícone ao lado de **elementos da matriz** e preencha os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="ab94b-125">Click the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="ab94b-126">**jumpWord** para o **nome da ação**</span><span class="sxs-lookup"><span data-stu-id="ab94b-126">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="ab94b-127">**ir** para **palavra-chave de fala**</span><span class="sxs-lookup"><span data-stu-id="ab94b-127">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="ab94b-128">Qualquer palavra (s) em inglês ou sentenças curtas podem ser usadas como uma palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="ab94b-128">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Configurações de entrada do mecanismo UE4](images/unreal/engine-input.png)

<span data-ttu-id="ab94b-130">Os mapeamentos de fala podem ser usados como componentes de entrada como mapeamentos de ação ou de eixo ou como nós de plano gráfico no grafo de eventos.</span><span class="sxs-lookup"><span data-stu-id="ab94b-130">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="ab94b-131">Por exemplo, você pode vincular o comando de salto para imprimir dois logs diferentes dependendo de quando a palavra for falada:</span><span class="sxs-lookup"><span data-stu-id="ab94b-131">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="ab94b-132">Clique duas vezes em um plano gráfico para abri-lo no **grafo de eventos**.</span><span class="sxs-lookup"><span data-stu-id="ab94b-132">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="ab94b-133">**Clique com o botão direito do mouse** e pesquise pelo **nome da ação** do seu mapeamento de fala (neste caso, **jumpWord**) e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="ab94b-133">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter**.</span></span> <span data-ttu-id="ab94b-134">Isso adiciona um nó de **ação de entrada** ao grafo.</span><span class="sxs-lookup"><span data-stu-id="ab94b-134">This adds an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="ab94b-135">Arraste e solte o pino **pressionado** para **Imprimir** o nó da cadeia de caracteres, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="ab94b-135">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="ab94b-136">Você pode deixar o PIN **liberado** vazio, ele não executará nada para mapeamentos de fala.</span><span class="sxs-lookup"><span data-stu-id="ab94b-136">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Ação simples para voz](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="ab94b-138">Reproduza o aplicativo, digamos que a palavra **salte** e assista ao console para imprimir os logs!</span><span class="sxs-lookup"><span data-stu-id="ab94b-138">Play the app, say the word **jump** and watch the console print out the logs!</span></span>

<span data-ttu-id="ab94b-139">Essa é toda a configuração que você precisará para começar a adicionar entrada de voz aos seus aplicativos de HoloLens em um não real.</span><span class="sxs-lookup"><span data-stu-id="ab94b-139">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="ab94b-140">Você pode encontrar mais informações sobre a fala e a interatividade nos links abaixo e certifique-se de pensar sobre a experiência que está criando para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="ab94b-140">You can find more information on speech and interactivity can be found at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab94b-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab94b-141">See also</span></span>
* [<span data-ttu-id="ab94b-142">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="ab94b-142">Voice Input</span></span>](voice-input.md)
* [<span data-ttu-id="ab94b-143">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="ab94b-143">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="ab94b-144">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="ab94b-144">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="ab94b-145">Entrada do MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="ab94b-145">MR Input 212: Voice</span></span>](holograms-212.md)

