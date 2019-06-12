---
title: Ativar a colocação de modelos 3D em casa
description: Como colocar os modelos 3D do seu site ou aplicativo em que o Windows Mixed Reality inicial
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modelo, local na página inicial, local, mundo, modelagem, realidade misturada doméstica, web, aplicativo
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829728"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Ativar a colocação de modelos 3D na realidade misturada inicial

> [!NOTE]
> Esse recurso foi adicionado como parte do [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md). Versões mais antigas do Windows não são compatíveis com esse recurso.

O [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) é o ponto de partida em que os usuários cheguem antes de iniciar aplicativos. Em alguns cenários, aplicativos 2D (como o aplicativo de hologramas) ativar a colocação de modelos 3D diretamente para a página inicial de realidade misturada como decorações ou para uma inspeção detalhada em 3D completo. O *Adicionar modelo de protocolo* permite que você envie um modelo 3D de seu site ou aplicativo diretamente para o Windows Mixed Reality doméstica, onde ele será mantido como [iniciadores de aplicativo 3D](3d-app-launcher-design-guidance.md), aplicativos 2D e hologramas. 

Por exemplo, se você estiver desenvolvendo um aplicativo que exiba um catálogo de 3D mobília para a criação de um espaço, você pode usar o *Adicionar modelo protocolo* para permitir que os usuários a colocar esses modelos 3D Mobília do catálogo. Uma vez colocado no mundo, os usuários podem mover, redimensionar e remover esses modelos 3D, assim como outros hologramas em casa. Este artigo fornece uma visão geral da implementação de *Adicionar modelo protocolo* para que você possa começar permitindo que os usuários decorar seu mundo com objetos 3D do seu aplicativo ou da web.

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
    </tr>
     <tr>
        <td>Adicionar modelo de protocolo</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="overview"></a>Visão geral

Há 2 etapas para habilitar o posicionamento dos modelos 3D no Windows Mixed Reality inicial:
1. [Verifique se seu modelo 3D é compatível com o Windows Mixed Reality doméstica](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Implemente a *Adicionar modelo protocolo* em seu aplicativo ou página da Web (Este artigo).

## <a name="implementing-the-add-model-protocol"></a>Implementando o *Adicionar modelo de protocolo*

Uma vez que um [modelo 3D compatível](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), você pode implementar o *Adicionar modelo protocolo* ativando o seguinte URI de qualquer página da Web ou aplicativo:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Se o URI aponta para um recurso remoto, em seguida, ele será automaticamente ser baixado e colocado em casa. Recursos locais serão copiados para a pasta de dados a realidade misturada página inicial aplicativo antes de ser colocada em casa. É recomendável Projetando sua experiência de conta para cenários em que o usuário pode estar executando uma versão anterior do Windows que não oferecem suporte a esse recurso, ocultar o botão ou desabilitá-lo se possível. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Invocar o *Adicionar modelo protocolo* de um aplicativo da plataforma Universal do Windows:

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Invocar o *Adicionar modelo protocolo* em uma página da Web:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Considerações para fones imersivos em exposição (VR)

* Para um fones imersivos em exposição de (VR), o Portal de realidade mista não precisa estar em execução antes de invocar o *Adicionar modelo protocolo*. Nesse caso, o *Adicionar modelo protocolo* irá iniciar o Portal de realidade mista e colocar o objeto diretamente em que o fone de ouvido é parecido quando você chegar na realidade misturada inicial. 
* Ao invocar o *Adicionar modelo protocolo* da área de trabalho com o Portal de realidade misturada já em execução, certifique-se de que o fone de ouvido está "ativo". Caso contrário, o posicionamento não terá êxito. 

## <a name="see-also"></a>Consulte também

* [Criar modelos 3D para uso no ambiente doméstico Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Como navegar na página inicial do Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
