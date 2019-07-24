---
title: Habilitar o posicionamento de modelos 3D na página inicial
description: Como posicionar modelos 3D de seu site ou aplicativo na página inicial do Windows Mixed Reality
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modelo, lugar em casa, lugar, mundo, modelagem, realidade misturada, página inicial, Web, aplicativo
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829728"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Habilitar o posicionamento de modelos 3D no início da realidade misturada

> [!NOTE]
> Esse recurso foi adicionado como parte da [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md). As versões mais antigas do Windows não são compatíveis com esse recurso.

O [Windows Mixed Reality Home](navigating-the-windows-mixed-reality-home.md) é o ponto de partida onde os usuários vão antes de iniciar os aplicativos. Em alguns cenários, os aplicativos 2D (como o aplicativo hologramas) permitem o posicionamento de modelos 3D diretamente na casa mistura de realidade como decorações ou para uma inspeção mais detalhada no 3D completo. O *protocolo adicionar modelo* permite que você envie um modelo 3D de seu site ou aplicativo diretamente para a página inicial do Windows Mixed Realm, onde ele persistirá como inicializadores de [aplicativos 3D](3d-app-launcher-design-guidance.md), aplicativos 2D e hologramas. 

Por exemplo, se você estiver desenvolvendo um aplicativo que superfícies um catálogo de mobília 3D para criar um espaço, poderá usar o *protocolo adicionar modelo* para permitir que os usuários coloquem esses modelos de móveis 3D a partir do catálogo. Uma vez colocado no mundo, os usuários podem mover, redimensionar e remover esses modelos 3D assim como outros hologramas em casa. Este artigo fornece uma visão geral da implementação do *protocolo adicionar modelo* para que você possa começar a permitir que os usuários decorem seu mundo com objetos 3D do seu aplicativo ou da Web.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Adicionar protocolo de modelo</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="overview"></a>Visão geral

Há duas etapas para habilitar o posicionamento de modelos 3D na página inicial do Windows Mixed Reality:
1. [Verifique se seu modelo 3D é compatível com a página inicial do Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Implemente o *protocolo adicionar modelo* em seu aplicativo ou página da Web (este artigo).

## <a name="implementing-the-add-model-protocol"></a>Implementando o *protocolo adicionar modelo*

Depois de ter um [modelo 3D compatível](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), você pode implementar o *protocolo adicionar modelo* ativando o seguinte URI de qualquer página da Web ou aplicativo:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Se o URI apontar para um recurso remoto, ele será baixado automaticamente e colocado em casa. Os recursos locais serão copiados para a pasta de dados de aplicativo da página inicial da realidade misturada antes de serem colocados em casa. É recomendável projetar sua experiência para considerar cenários em que o usuário pode estar executando uma versão mais antiga do Windows que não dá suporte a esse recurso, ocultando o botão ou desabilitando-o, se possível. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Invocando o *protocolo adicionar modelo* de um aplicativo plataforma universal do Windows:

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Invocando o *protocolo adicionar modelo* de uma página da Web:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Considerações sobre headsets de imersão (VR)

* Para headsets de imersão (VR), o portal de realidade misturada não precisa estar em execução antes de invocar o *protocolo adicionar modelo*. Nesse caso, o *protocolo adicionar modelo* iniciará o portal de realidade misturada e posicionará o objeto diretamente, no qual o headset está olhando quando você chegar na casa misturada da realidade. 
* Ao invocar o *protocolo adicionar modelo* da área de trabalho com o portal da realidade misturada já em execução, verifique se o headset está "ativo". Caso contrário, o posicionamento não terá sucesso. 

## <a name="see-also"></a>Consulte também

* [Criando modelos 3D para uso na página inicial do Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Como navegar na página inicial do Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
