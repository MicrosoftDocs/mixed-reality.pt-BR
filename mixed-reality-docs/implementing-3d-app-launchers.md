---
title: Implementar iniciadores de aplicativo 3D (aplicativos UWP)
description: Como criar logotipos para aplicativos UWP de realidade mista do Windows e jogos (distribuídos por meio do Microsoft Store) e dos inicializadores de aplicativo 3D no HoloLens e fones imersivos em exposição (VR).
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, ícone, modelagem, iniciador, iniciador 3D, bloco, ao vivo cubo, link profundo, secondarytile, bloco secundário, UWP
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590971"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>Implementar iniciadores de aplicativo 3D (aplicativos UWP)

> [!NOTE]
> Esse recurso foi adicionado como parte de fones imersivos em exposição a 2017 Fall Creators Update (RS3) e é compatível com o HoloLens com o Windows Update 10 de abril de 2018. Verifique se que seu aplicativo está definido em uma versão do SDK do Windows, maior que ou igual a 10.0.16299 em fones imersivos em exposição e 10.0.17125 em HoloLens. Você pode encontrar o SDK mais recente do Windows [aqui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

O [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) é o ponto de partida em que os usuários cheguem antes de iniciar aplicativos. Ao criar um aplicativo UWP para Windows Mixed Reality, por padrão, os aplicativos são iniciados como slates 2D com o logotipo do seu aplicativo. Ao desenvolver experiências para o Windows Mixed Reality, um iniciador 3D opcionalmente pode ser definido para substituir o iniciador 2D padrão para seu aplicativo. Em geral, os inicializadores 3D são recomendados para iniciar aplicativos imersivos que levam os usuários fora do Windows Mixed Reality inicial, enquanto o iniciador 2D padrão é preferível quando o aplicativo é ativado em vigor. Você também pode criar uma [link profundo 3D (secondaryTile)](#3d-deep-links-secondarytiles) como um iniciador 3D ao conteúdo dentro de um aplicativo UWP 2D.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>Processo de criação de iniciador do aplicativo 3D

Há 3 etapas para criar um inicializador de aplicativos 3D:
1. [Criando e concepting](3d-app-launcher-design-guidance.md)
2. [Modelagem e exportando](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integração ao seu aplicativo (Este artigo)

Ativos 3D para serem usados como os inicializadores para seu aplicativo devem ser criados usando o [diretrizes de criação de realidade mista do Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantir a compatibilidade. Ativos que não atendem a essa especificação de criação não serão renderizados no Windows Mixed Reality inicial.

## <a name="configuring-the-3d-launcher"></a>Configurando o iniciador do 3D

Quando você cria um novo projeto no Visual Studio, ele cria um bloco padrão simples que exibe o nome e o logotipo do seu aplicativo. Para substituir esse 2D representação com um modelo 3D personalizado editar o manifesto de aplicativo do seu aplicativo para incluir o elemento "MixedRealityModel" como parte da sua definição de bloco padrão. Para reverter para 2D iniciador apenas remover a definição de MixedRealityModel do manifesto.

### <a name="xml"></a>XML

Primeiro, localize o manifesto do pacote de aplicativo em seu projeto atual. Por padrão, o manifesto será denominado Package. appxmanifest. Se você estiver usando o Visual Studio, o manifesto no seu visualizador de solução com o botão direito e selecione **Exibir código-fonte** para abrir o xml para edição. 

Na parte superior do manifesto, adicione o esquema uap5 e incluí-lo como um namespace pode ser ignorado:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

Em seguida, especifique "MixedRealityModel" no bloco padrão para seu aplicativo:

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

Os elementos MixedRealityModel aceita um caminho de arquivo que aponta para um ativo 3D armazenado em seu pacote do aplicativo. Atualmente modelos 3D apenas fornecidas usando o formato de arquivo .glb e criados em relação a [ativos 3D do Windows Mixed Reality instruções de criação](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) têm suporte. Ativos devem ser armazenados no pacote do aplicativo e a animação não é suportada atualmente. Se o parâmetro "Caminho" é deixado em branco Windows mostrará o slate 2D, em vez de iniciador do 3D. **Observação:** .glb ativo deve ser marcado como "Conteúdo" em suas configurações de compilação antes de compilar e executar seu aplicativo.


![Selecione o .glb no Gerenciador de soluções e use a seção de propriedades para marcá-la como "Conteúdo" nas configurações de build](images/buildsetting-content-300px.png)<br>
*Selecione o .glb no Gerenciador de soluções e use a seção de propriedades para marcá-la como "Conteúdo" nas configurações de build*

### <a name="bounding-box"></a>Caixa delimitadora

Uma caixa delimitadora pode ser usada para adicionar, opcionalmente, uma região de buffer adicional em torno do objeto. A caixa delimitadora é especificada usando um ponto central e extensões que indicam a distância entre o centro da caixa delimitadora e suas bordas em cada eixo. Unidades para a caixa delimitadora podem ser mapeadas para 1 unidade = 1 metro. Se uma caixa delimitadora não for fornecida, em seguida, um será ser ajustado automaticamente para a malha do objeto. Se a caixa delimitadora fornecida for menor que o modelo, em seguida, ele será redimensionado para caber da malha.

Suporte para o atributo de caixa delimitadora será fornecido com a atualização do Windows RS4 como uma propriedade no elemento MixedRealityModel. Para definir uma caixa delimitadora pela primeira vez, na parte superior do aplicativo, o manifesto de adicionar o esquema uap6 e incluí-lo-los como ignorável namespaces:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
Em seguida, em que o MixedRealityModel defina a propriedade de SpatialBoundingBox para definir a caixa delimitadora: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Usando o Unity

Ao trabalhar com o Unity o projeto deve ser criado e aberto no Visual Studio antes do manifesto do aplicativo pode ser editado. 

>[!NOTE]
>O iniciador do 3D deve ser redefinido no manifesto ao criar e implantar uma nova solução do Visual Studio do Unity.

## <a name="3d-deep-links-secondarytiles"></a>Profundo 3D vincula (secondaryTiles)

> [!NOTE]
> Esse recurso foi adicionado como parte da atualização de criadores de outono (RS3) 2017 para fones imersivos em exposição (VR) e como parte de abril de 2018 atualização (RS4) para o HoloLens. Verifique se que seu aplicativo está definido em uma versão do SDK do Windows, maior que ou igual a 10.0.16299 em fones imersivos em exposição (VR) e 10.0.17125 em HoloLens. Você pode encontrar o SDK mais recente do Windows [aqui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

>[!IMPORTANT]
>Links profundos 3D (secondaryTiles) só funcionam com aplicativos da UWP 2D. No entanto, você pode criar uma [inicializador de aplicativos 3D](implementing-3d-app-launchers.md) para iniciar um aplicativo exclusivo a partir do Windows Mixed Reality inicial.

Seus aplicativos 2D podem ser aprimorados para o Windows Mixed Reality, adicionando a capacidade de colocar os modelos 3D do seu aplicativo para o [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) como links profundos para conteúdos dentro do seu aplicativo 2D, assim como [secundário 2D blocos](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) no menu Iniciar do Windows. Por exemplo, você pode criar photospheres de 360° que vinculam diretamente em um aplicativo de Visualizador de fotos de 360° ou permitir que os usuários a colocar o conteúdo 3D de uma coleção de ativos que abre uma página de detalhes sobre o autor. Esses são apenas duas maneiras de expandir a funcionalidade do seu aplicativo 2D com conteúdo 3D.

### <a name="creating-a-3d-secondarytile"></a>Criando um "secondaryTile" 3D

Você pode colocar o conteúdo 3D de seu aplicativo usando "secondaryTiles" definindo um modelo de realidade misturada no momento da criação. Modelos de realidade misturada são criados, fazendo referência a um ativo de 3D em seu pacote do aplicativo e, opcionalmente, definindo uma caixa delimitadora. 

> [!NOTE]
> Atualmente, não há suporte para a criação de "secondaryTiles" de dentro de um modo de exibição exclusivo.

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a>Caixa delimitadora

Uma caixa delimitadora pode ser usada para adicionar uma região de buffer adicional em torno do objeto. A caixa delimitadora é especificada usando um ponto central e extensões que indicam a distância entre o centro da caixa delimitadora e suas bordas em cada eixo. Unidades para a caixa delimitadora podem ser mapeadas para 1 unidade = 1 metro. Se uma caixa delimitadora não for fornecida, em seguida, um será ser ajustado automaticamente para a malha do objeto. Se a caixa delimitadora fornecida for menor que o modelo, em seguida, ele será redimensionado para caber da malha.

### <a name="activation-behavior"></a>Comportamento de ativação

> [!NOTE]
> Esse recurso terá suporte a partir da atualização do Windows RS4. Certifique-se que seu aplicativo está buscando uma versão do SDK do Windows, maior que ou igual a 10.0.17125 se você planeja usar esse recurso

Você pode definir o comportamento de ativação para um secondaryTile 3D controlar como ele reage quando um usuário o seleciona. Isso pode ser usado para colocar objetos 3D na realidade misturada inicial que são purley decorativo ou informativo. Há suporte para os seguintes tipos de comportamento de ativação:
1. Default: Quando um usuário seleciona o secondaryTile 3D, o aplicativo é ativado
2. Nenhum: Quando o usuário seleciona o secondaryTile 3D, nada acontece e o aplicativo não está ativado.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Como obter e atualizar um existente "secondaryTile"

Os desenvolvedores podem obter uma lista de seus blocos secundários existentes, que inclui as propriedades que eles especificado anteriormente. Eles também podem atualizar as propriedades de alteração do valor e, em seguida, chamando UpdateAsync().

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Verificando se o usuário é na realidade mista do Windows

Links profundos 3D (secondaryTiles) só podem ser criados enquanto o modo de exibição está sendo exibido em um headset de realidade mista do Windows. Quando o modo de exibição não está sendo apresentado um Headset de realidade mista do Windows, é recomendável normalmente lidar com isso, ocultando o ponto de entrada ou mostrando uma mensagem de erro. Você pode verificar isso consultando [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).

## <a name="tile-notifications"></a>Notificações de bloco

Notificações de bloco não damos suporte a enviar uma atualização com um ativo de 3D. Isso significa que os desenvolvedores não poderão fazer o seguinte
* Notificações por push
* Sondagem periódica
* Notificações agendadas

Para obter mais informações sobre outros recursos, blocos e atributos e como eles são usados para blocos 2D, consulte o [blocos para obter a documentação de aplicativos UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).

## <a name="see-also"></a>Consulte também

* [Exemplo de modelo de realidade misturada](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contendo um inicializador de aplicativos 3D.
* [Diretrizes de design de iniciador do aplicativo 3D](3d-app-launcher-design-guidance.md)
* [Criar modelos 3D para uso no ambiente doméstico Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementando os inicializadores de aplicativos 3D (aplicativos Win32)](implementing-3d-app-launchers-win32.md)
* [Navegando o Windows Mixed Reality inicial](navigating-the-windows-mixed-reality-home.md)
