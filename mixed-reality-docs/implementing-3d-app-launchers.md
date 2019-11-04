---
title: Implementar iniciadores de aplicativos 3D (aplicativos UWP)
description: Como criar iniciadores de aplicativos 3D e logotipos para aplicativos e jogos do Windows Mixed Reality UWP (distribuídos por meio do Microsoft Store), tanto no HoloLens quanto em headsets de imersão (VR).
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, ícone, modelagem, iniciador, iniciador 3D, bloco, cubo ao vivo, link profundo, secondarytile, bloco secundário, UWP
ms.openlocfilehash: be47b590e4fd1a847ac47d9cfbcbe824c544dd59
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438019"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>Implementar iniciadores de aplicativos 3D (aplicativos UWP)

> [!NOTE]
> Esse recurso foi adicionado como parte da RS3 (atualização para criadores de outono do 2017) para headsets de imersão e tem suporte do HoloLens com a atualização do Windows 10 de abril de 2018. Verifique se seu aplicativo está direcionando para uma versão do SDK do Windows maior ou igual a 10.0.16299 em headsets de imersão e 10.0.17125 no HoloLens. Você pode encontrar as SDK do Windows mais recentes [aqui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

O [Windows Mixed Reality Home](navigating-the-windows-mixed-reality-home.md) é o ponto de partida onde os usuários vão antes de iniciar os aplicativos. Ao criar um aplicativo UWP para a realidade mista do Windows, por padrão, os aplicativos são iniciados como slates 2D com o logotipo do aplicativo. Ao desenvolver experiências para a realidade mista do Windows, um iniciador 3D pode, opcionalmente, ser definido para substituir o inicializador 2D padrão para seu aplicativo. Em geral, os iniciadores 3D são recomendados para iniciar aplicativos de imersão que levam os usuários da casa do Windows Mixed Realm, enquanto o inicializador 2D padrão é preferencial quando o aplicativo é ativado no local. Você também pode criar um [link de 3D Deep (secondaryTile)](#3d-deep-links-secondarytiles) como um iniciador 3D para o conteúdo em um aplicativo UWP 2D.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>processo de criação do inicializador de aplicativo 3D

Há três etapas para criar um iniciador de aplicativo 3D:
1. [Design e conceito](3d-app-launcher-design-guidance.md)
2. [Modelagem e exportação](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrando-o ao seu aplicativo (este artigo)

os ativos 3D a serem usados como iniciadores para seu aplicativo devem ser criados usando as [diretrizes de criação do Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantir a compatibilidade. Os ativos que não atenderem a essa especificação de criação não serão renderizados na página inicial do Windows Mixed Reality.

## <a name="configuring-the-3d-launcher"></a>Configurando o iniciador 3D

Quando você cria um novo projeto no Visual Studio, ele cria um bloco padrão simples que exibe o nome e o logotipo do seu aplicativo. Para substituir essa representação 2D por um modelo 3D personalizado, edite o manifesto de aplicativo do seu aplicativo para incluir o elemento "MixedRealityModel" como parte de sua definição de bloco padrão. Para reverter para o inicializador 2D, basta remover a definição de MixedRealityModel do manifesto.

### <a name="xml"></a>XML

Primeiro, localize o manifesto do pacote do aplicativo em seu projeto atual. Por padrão, o manifesto será nomeado Package. appxmanifest. Se você estiver usando o Visual Studio, clique com o botão direito do mouse no manifesto no seu visualizador de solução e selecione **Exibir origem** para abrir o XML para edição. 

Na parte superior do manifesto, adicione o esquema uap5 e inclua-o como um namespace ignorável:

```xml
<Package xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="https://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

Em seguida, especifique o "MixedRealityModel" no bloco padrão para seu aplicativo:

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

Os elementos MixedRealityModel aceitam um caminho de arquivo que aponta para um ativo 3D armazenado em seu pacote de aplicativo. Atualmente, apenas modelos 3D entregues usando o formato de arquivo. glb e criados em relação às [instruções de criação de ativos 3D da realidade do Windows Mixed](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) têm suporte. Os ativos devem ser armazenados no pacote do aplicativo e a animação não tem suporte no momento. Se o parâmetro "Path" for deixado em branco, o Windows mostrará o Tablet 2D em vez do iniciador 3D. **Observação:** o ativo. glb deve ser marcado como "conteúdo" em suas configurações de compilação antes de compilar e executar seu aplicativo.


![selecione o. glb no Gerenciador de soluções e use a seção Propriedades para marcá-lo como "conteúdo" nas configurações de compilação](images/buildsetting-content-300px.png)<br>
*Selecione o. glb no Gerenciador de soluções e use a seção Propriedades para marcá-lo como "conteúdo" nas configurações de compilação*

### <a name="bounding-box"></a>Caixa delimitadora

Uma caixa delimitadora pode ser usada para adicionar opcionalmente uma região de buffer adicional ao objeto. A caixa delimitadora é especificada usando um ponto central e extensões que indicam a distância do centro da caixa delimitadora às suas bordas ao longo de cada eixo. As unidades da caixa delimitadora podem ser mapeadas para 1 unidade = 1 medidor. Se uma caixa delimitadora não for fornecida, uma será ajustada automaticamente para a malha do objeto. Se a caixa delimitadora fornecida for menor do que o modelo, ela será redimensionada para se ajustar à malha.

O suporte para o atributo da caixa delimitadora será fornecido com a atualização RS4 do Windows como uma propriedade no elemento MixedRealityModel. Para definir uma caixa delimitadora primeiro na parte superior do manifesto do aplicativo, adicione o esquema uap6 e inclua-o como namespaces ignoráveis:

```xml
<Package xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="https://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="https://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
Em seguida, no MixedRealityModel, defina a propriedade SpatialBoundingBox para definir a caixa delimitadora: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Usando o Unity

Ao trabalhar com o Unity, o projeto deve ser compilado e aberto no Visual Studio antes que o manifesto do aplicativo possa ser editado. 

>[!NOTE]
>O iniciador 3D deve ser redefinido no manifesto ao compilar e implantar uma nova solução do Visual Studio do Unity.

## <a name="3d-deep-links-secondarytiles"></a>links de 3D Deep (secondaryTiles)

> [!NOTE]
> Esse recurso foi adicionado como parte da RS3 (atualização para criadores de outono) de 2017 para fones de ouvido (VR) e como parte da atualização de abril de 2018 (RS4) para o HoloLens. Verifique se seu aplicativo está direcionando para uma versão do SDK do Windows maior ou igual a 10.0.16299 em headsets de imersão (VR) e 10.0.17125 no HoloLens. Você pode encontrar as SDK do Windows mais recentes [aqui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

>[!IMPORTANT]
>os secondaryTiles (3D Deep links) funcionam apenas com aplicativos UWP 2D. No entanto, você pode criar um [iniciador de aplicativo 3D](implementing-3d-app-launchers.md) para iniciar um aplicativo exclusivo na página inicial do Windows Mixed Reality.

Seus aplicativos 2D podem ser aprimorados para a realidade mista do Windows, adicionando a capacidade de posicionar modelos 3D de seu aplicativo na [casa do Windows Mixed Realm](navigating-the-windows-mixed-reality-home.md) como links profundos para conteúdo em seu aplicativo 2D, assim como [blocos 2D secundários](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) na inicialização do Windows AdicionarMenu. Por exemplo, você pode criar fotografias de 360 ° que se vinculam diretamente a um aplicativo de visualizador de fotos 360 ° ou permitem que os usuários coloquem o conteúdo 3D de uma coleção de ativos que abre uma página de detalhes sobre o autor. Essas são apenas duas maneiras de expandir a funcionalidade do seu aplicativo 2D com conteúdo 3D.

### <a name="creating-a-3d-secondarytile"></a>Criando um "secondaryTile" 3D

Você pode posicionar o conteúdo 3D do seu aplicativo usando "secondaryTiles" definindo um modelo de realidade misturada no momento da criação. Os modelos de realidade misturada são criados referenciando um ativo 3D em seu pacote de aplicativo e, opcionalmente, definindo uma caixa delimitadora. 

> [!NOTE]
> No momento, não há suporte para a criação de "secondaryTiles" de dentro de uma exibição exclusiva.

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

Uma caixa delimitadora pode ser usada para adicionar uma região de buffer adicional em volta do objeto. A caixa delimitadora é especificada usando um ponto central e extensões que indicam a distância do centro da caixa delimitadora às suas bordas ao longo de cada eixo. As unidades da caixa delimitadora podem ser mapeadas para 1 unidade = 1 medidor. Se uma caixa delimitadora não for fornecida, uma será ajustada automaticamente para a malha do objeto. Se a caixa delimitadora fornecida for menor do que o modelo, ela será redimensionada para se ajustar à malha.

### <a name="activation-behavior"></a>Comportamento de ativação

> [!NOTE]
> Esse recurso terá suporte a partir da atualização RS4 do Windows. Verifique se seu aplicativo está direcionando para uma versão do SDK do Windows maior ou igual a 10.0.17125 se você planeja usar esse recurso

Você pode definir o comportamento de ativação para um secondaryTile 3D para controlar como ele reage quando um usuário o seleciona. Isso pode ser usado para posicionar objetos 3D no início da realidade misturada que são informativos ou decorativos Purleys. Há suporte para os seguintes tipos de comportamento de ativação:
1. Padrão: quando um usuário seleciona o secondaryTile 3D, o aplicativo é ativado
2. Nenhum: quando os usuários selecionam o 3D secondaryTile, nada acontece e o aplicativo não é ativado.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Obtendo e atualizando um "secondaryTile" existente

Os desenvolvedores podem obter uma lista de seus blocos secundários existentes, que incluem as propriedades especificadas anteriormente. Eles também podem atualizar as propriedades alterando o valor e, em seguida, chamando UpdateAsync ().

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Verificando se o usuário está no Windows Mixed Reality

os links de 3D Deep (secondaryTiles) só podem ser criados enquanto a exibição está sendo exibida em um headset de realidade mista do Windows. Quando o modo de exibição não está sendo apresentado em um headset de realidade misturada do Windows, é recomendável lidar normalmente com isso ocultando o ponto de entrada ou mostrando uma mensagem de erro. Você pode verificar isso consultando [IsCurrentViewPresentedOnHolographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).

## <a name="tile-notifications"></a>Notificações de bloco

No momento, as notificações de bloco não dão suporte ao envio de uma atualização com um ativo 3D. Isso significa que os desenvolvedores não poderão fazer o seguinte
* Notificações por push
* Sondagem periódica
* Notificações agendadas

Para obter mais informações sobre os outros recursos e atributos de blocos e como eles são usados para blocos 2D, consulte a [documentação de blocos para aplicativos UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).

## <a name="see-also"></a>Consulte também

* [Exemplo de modelo de realidade misturada](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contém um iniciador de aplicativo 3D.
* [Diretrizes de projeto do inicializador de aplicativos 3D](3d-app-launcher-design-guidance.md)
* [Criando modelos 3D para uso na página inicial do Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementando inicializadores de aplicativo 3D (aplicativos Win32)](implementing-3d-app-launchers-win32.md)
* [Como navegar na página inicial do Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
