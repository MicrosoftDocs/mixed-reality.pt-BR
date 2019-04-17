---
title: Persistência no Unity
description: Persistência permite que os usuários fixar hologramas individuais ou um espaço de trabalho sempre que quiserem e em seguida, localize posteriormente em que eles esperam ao longo de muitos usa do seu aplicativo.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistência, o Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591015"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="ac33f-104">Persistência no Unity</span><span class="sxs-lookup"><span data-stu-id="ac33f-104">Persistence in Unity</span></span>

<span data-ttu-id="ac33f-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="ac33f-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="ac33f-106">**Classe:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="ac33f-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="ac33f-107">O WorldAnchorStore é a chave para a criação de experiências holográfica onde hologramas permanecem em posições do mundo real específicos entre instâncias do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ac33f-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="ac33f-108">Isso permite que os usuários fixar hologramas individuais ou um espaço de trabalho onde quer que eles desejado e, em seguida, encontrá-lo mais tarde em que eles esperam ao longo de muitos usos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ac33f-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="ac33f-109">Como persistir hologramas entre as sessões</span><span class="sxs-lookup"><span data-stu-id="ac33f-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="ac33f-110">O WorldAnchorStore permitirá que você persistir a localização do WorldAnchor entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="ac33f-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="ac33f-111">Para realmente persistir hologramas entre as sessões, você precisará separadamente manter o controle de seu GameObjects que usam uma âncora de mundo específico.</span><span class="sxs-lookup"><span data-stu-id="ac33f-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="ac33f-112">Muitas vezes faz sentido criar uma raiz de GameObject com uma âncora do mundo e ter filhos hologramas ancorados por ela com um deslocamento de posição local.</span><span class="sxs-lookup"><span data-stu-id="ac33f-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="ac33f-113">Para carregar hologramas das sessões anteriores:</span><span class="sxs-lookup"><span data-stu-id="ac33f-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="ac33f-114">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="ac33f-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="ac33f-115">Carregar dados de aplicativo relacionados à âncora do mundo que lhe dá a id da âncora de mundo</span><span class="sxs-lookup"><span data-stu-id="ac33f-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="ac33f-116">Carregar uma âncora de mundo de sua id</span><span class="sxs-lookup"><span data-stu-id="ac33f-116">Load a world anchor from its id</span></span>

<span data-ttu-id="ac33f-117">Para salvar hologramas para sessões futuras:</span><span class="sxs-lookup"><span data-stu-id="ac33f-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="ac33f-118">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="ac33f-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="ac33f-119">Salvar uma âncora de mundo especificando uma id</span><span class="sxs-lookup"><span data-stu-id="ac33f-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="ac33f-120">Salvar dados de aplicativos relacionados à âncora de mundo, juntamente com uma id</span><span class="sxs-lookup"><span data-stu-id="ac33f-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="ac33f-121">Introdução a WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="ac33f-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="ac33f-122">Queremos manter uma referência ao WorldAnchorStore em torno de, portanto, sabemos que estamos prontos para ir quando queremos executar uma operação.</span><span class="sxs-lookup"><span data-stu-id="ac33f-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="ac33f-123">Como essa é uma chamada assíncrona, potencialmente, assim que iniciar, queremos chamar</span><span class="sxs-lookup"><span data-stu-id="ac33f-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="ac33f-124">Nesse caso, StoreLoaded é nosso manipulador para quando o WorldAnchorStore concluiu o carregamento:</span><span class="sxs-lookup"><span data-stu-id="ac33f-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="ac33f-125">Agora temos uma referência para o WorldAnchorStore que usaremos para salvar e carregar âncoras específico do mundo.</span><span class="sxs-lookup"><span data-stu-id="ac33f-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="ac33f-126">Salvando uma WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="ac33f-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="ac33f-127">Para salvar, simplesmente precisamos nomear o que está salvando e passá-la no WorldAnchor obtivemos antes quando queremos salvar.</span><span class="sxs-lookup"><span data-stu-id="ac33f-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="ac33f-128">Observação: ao tentar salvar duas âncoras com a mesma cadeia falhará (store. Salvar retornará false).</span><span class="sxs-lookup"><span data-stu-id="ac33f-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="ac33f-129">Você precisa excluir o salvamento anterior antes de salvar um novo:</span><span class="sxs-lookup"><span data-stu-id="ac33f-129">You need to Delete the previous save before saving the new one:</span></span>

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="ac33f-130">Carregando um WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="ac33f-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="ac33f-131">E para carregar:</span><span class="sxs-lookup"><span data-stu-id="ac33f-131">And to load:</span></span>

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

<span data-ttu-id="ac33f-132">Além disso, podemos pode usar armazenamento. Delete () para remover uma âncora que salva anteriormente e armazenamento. Clear () para remover todos os dados salvos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ac33f-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="ac33f-133">Enumerar as âncoras de existentes</span><span class="sxs-lookup"><span data-stu-id="ac33f-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="ac33f-134">Para descobrir as âncoras armazenadas anteriormente, chame GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="ac33f-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="ac33f-135">Hologramas persistentes para vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="ac33f-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="ac33f-136">Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> para criar uma âncora de nuvem durável de um WorldAnchor local, o que seu aplicativo, em seguida, pode localizar, em vários HoloLens, dispositivos iOS e Android, mesmo se esses dispositivos não estão presentes em conjunto ao mesmo tempo tempo.</span><span class="sxs-lookup"><span data-stu-id="ac33f-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="ac33f-137">Como âncoras de nuvem são persistentes, vários dispositivos ao longo do tempo cada um verá conteúdo renderizado em relação a essa âncora no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="ac33f-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="ac33f-138">Para começar a criação de experiências compartilhadas no Unity, experimente o 5 minutos <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guias de início rápido do Azure espacial âncoras Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="ac33f-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="ac33f-139">Quando estiver em funcionamento com âncoras espacial do Azure, você pode então <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar as âncoras no Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="ac33f-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac33f-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac33f-140">See Also</span></span>
* [<span data-ttu-id="ac33f-141">Persistência de âncora espacial</span><span class="sxs-lookup"><span data-stu-id="ac33f-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="ac33f-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="ac33f-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="ac33f-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Âncoras espaciais do Azure SDK para Unity</a></span><span class="sxs-lookup"><span data-stu-id="ac33f-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
