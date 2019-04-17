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
# <a name="persistence-in-unity"></a>Persistência no Unity

**Namespace:** *UnityEngine.XR.WSA.Persistence*<br>
**Classe:** *WorldAnchorStore*

O WorldAnchorStore é a chave para a criação de experiências holográfica onde hologramas permanecem em posições do mundo real específicos entre instâncias do aplicativo. Isso permite que os usuários fixar hologramas individuais ou um espaço de trabalho onde quer que eles desejado e, em seguida, encontrá-lo mais tarde em que eles esperam ao longo de muitos usos do seu aplicativo.

## <a name="how-to-persist-holograms-across-sessions"></a>Como persistir hologramas entre as sessões

O WorldAnchorStore permitirá que você persistir a localização do WorldAnchor entre as sessões. Para realmente persistir hologramas entre as sessões, você precisará separadamente manter o controle de seu GameObjects que usam uma âncora de mundo específico. Muitas vezes faz sentido criar uma raiz de GameObject com uma âncora do mundo e ter filhos hologramas ancorados por ela com um deslocamento de posição local.

Para carregar hologramas das sessões anteriores:
1. Obter o WorldAnchorStore
2. Carregar dados de aplicativo relacionados à âncora do mundo que lhe dá a id da âncora de mundo
3. Carregar uma âncora de mundo de sua id

Para salvar hologramas para sessões futuras:
1. Obter o WorldAnchorStore
2. Salvar uma âncora de mundo especificando uma id
3. Salvar dados de aplicativos relacionados à âncora de mundo, juntamente com uma id

### <a name="getting-the-worldanchorstore"></a>Introdução a WorldAnchorStore

Queremos manter uma referência ao WorldAnchorStore em torno de, portanto, sabemos que estamos prontos para ir quando queremos executar uma operação. Como essa é uma chamada assíncrona, potencialmente, assim que iniciar, queremos chamar

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

Nesse caso, StoreLoaded é nosso manipulador para quando o WorldAnchorStore concluiu o carregamento:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Agora temos uma referência para o WorldAnchorStore que usaremos para salvar e carregar âncoras específico do mundo.

### <a name="saving-a-worldanchor"></a>Salvando uma WorldAnchor

Para salvar, simplesmente precisamos nomear o que está salvando e passá-la no WorldAnchor obtivemos antes quando queremos salvar. Observação: ao tentar salvar duas âncoras com a mesma cadeia falhará (store. Salvar retornará false). Você precisa excluir o salvamento anterior antes de salvar um novo:

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

### <a name="loading-a-worldanchor"></a>Carregando um WorldAnchor

E para carregar:

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

Além disso, podemos pode usar armazenamento. Delete () para remover uma âncora que salva anteriormente e armazenamento. Clear () para remover todos os dados salvos anteriormente.

### <a name="enumerating-existing-anchors"></a>Enumerar as âncoras de existentes

Para descobrir as âncoras armazenadas anteriormente, chame GetAllIds.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Hologramas persistentes para vários dispositivos

Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> para criar uma âncora de nuvem durável de um WorldAnchor local, o que seu aplicativo, em seguida, pode localizar, em vários HoloLens, dispositivos iOS e Android, mesmo se esses dispositivos não estão presentes em conjunto ao mesmo tempo tempo.  Como âncoras de nuvem são persistentes, vários dispositivos ao longo do tempo cada um verá conteúdo renderizado em relação a essa âncora no mesmo local físico.

Para começar a criação de experiências compartilhadas no Unity, experimente o 5 minutos <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guias de início rápido do Azure espacial âncoras Unity</a>.

Quando estiver em funcionamento com âncoras espacial do Azure, você pode então <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar as âncoras no Unity</a>.

## <a name="see-also"></a>Consulte também
* [Persistência de âncora espacial](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras espaciais do Azure</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Âncoras espaciais do Azure SDK para Unity</a>
