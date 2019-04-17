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
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="b7928-104">Implementar iniciadores de aplicativo 3D (aplicativos UWP)</span><span class="sxs-lookup"><span data-stu-id="b7928-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="b7928-105">Esse recurso foi adicionado como parte de fones imersivos em exposição a 2017 Fall Creators Update (RS3) e é compatível com o HoloLens com o Windows Update 10 de abril de 2018.</span><span class="sxs-lookup"><span data-stu-id="b7928-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="b7928-106">Verifique se que seu aplicativo está definido em uma versão do SDK do Windows, maior que ou igual a 10.0.16299 em fones imersivos em exposição e 10.0.17125 em HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b7928-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="b7928-107">Você pode encontrar o SDK mais recente do Windows [aqui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="b7928-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="b7928-108">O [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) é o ponto de partida em que os usuários cheguem antes de iniciar aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b7928-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="b7928-109">Ao criar um aplicativo UWP para Windows Mixed Reality, por padrão, os aplicativos são iniciados como slates 2D com o logotipo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b7928-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="b7928-110">Ao desenvolver experiências para o Windows Mixed Reality, um iniciador 3D opcionalmente pode ser definido para substituir o iniciador 2D padrão para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b7928-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="b7928-111">Em geral, os inicializadores 3D são recomendados para iniciar aplicativos imersivos que levam os usuários fora do Windows Mixed Reality inicial, enquanto o iniciador 2D padrão é preferível quando o aplicativo é ativado em vigor.</span><span class="sxs-lookup"><span data-stu-id="b7928-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="b7928-112">Você também pode criar uma [link profundo 3D (secondaryTile)](#3d-deep-links-secondarytiles) como um iniciador 3D ao conteúdo dentro de um aplicativo UWP 2D.</span><span class="sxs-lookup"><span data-stu-id="b7928-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="b7928-113">Processo de criação de iniciador do aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="b7928-113">3D app launcher creation process</span></span>

<span data-ttu-id="b7928-114">Há 3 etapas para criar um inicializador de aplicativos 3D:</span><span class="sxs-lookup"><span data-stu-id="b7928-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="b7928-115">Criando e concepting</span><span class="sxs-lookup"><span data-stu-id="b7928-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="b7928-116">Modelagem e exportando</span><span class="sxs-lookup"><span data-stu-id="b7928-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="b7928-117">Integração ao seu aplicativo (Este artigo)</span><span class="sxs-lookup"><span data-stu-id="b7928-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="b7928-118">Ativos 3D para serem usados como os inicializadores para seu aplicativo devem ser criados usando o [diretrizes de criação de realidade mista do Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantir a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="b7928-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="b7928-119">Ativos que não atendem a essa especificação de criação não serão renderizados no Windows Mixed Reality inicial.</span><span class="sxs-lookup"><span data-stu-id="b7928-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="b7928-120">Configurando o iniciador do 3D</span><span class="sxs-lookup"><span data-stu-id="b7928-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="b7928-121">Quando você cria um novo projeto no Visual Studio, ele cria um bloco padrão simples que exibe o nome e o logotipo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b7928-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="b7928-122">Para substituir esse 2D representação com um modelo 3D personalizado editar o manifesto de aplicativo do seu aplicativo para incluir o elemento "MixedRealityModel" como parte da sua definição de bloco padrão.</span><span class="sxs-lookup"><span data-stu-id="b7928-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="b7928-123">Para reverter para 2D iniciador apenas remover a definição de MixedRealityModel do manifesto.</span><span class="sxs-lookup"><span data-stu-id="b7928-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="b7928-124">XML</span><span class="sxs-lookup"><span data-stu-id="b7928-124">XML</span></span>

<span data-ttu-id="b7928-125">Primeiro, localize o manifesto do pacote de aplicativo em seu projeto atual.</span><span class="sxs-lookup"><span data-stu-id="b7928-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="b7928-126">Por padrão, o manifesto será denominado Package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="b7928-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="b7928-127">Se você estiver usando o Visual Studio, o manifesto no seu visualizador de solução com o botão direito e selecione **Exibir código-fonte** para abrir o xml para edição.</span><span class="sxs-lookup"><span data-stu-id="b7928-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="b7928-128">Na parte superior do manifesto, adicione o esquema uap5 e incluí-lo como um namespace pode ser ignorado:</span><span class="sxs-lookup"><span data-stu-id="b7928-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="b7928-129">Em seguida, especifique "MixedRealityModel" no bloco padrão para seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="b7928-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

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

<span data-ttu-id="b7928-130">Os elementos MixedRealityModel aceita um caminho de arquivo que aponta para um ativo 3D armazenado em seu pacote do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b7928-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="b7928-131">Atualmente modelos 3D apenas fornecidas usando o formato de arquivo .glb e criados em relação a [ativos 3D do Windows Mixed Reality instruções de criação](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) têm suporte.</span><span class="sxs-lookup"><span data-stu-id="b7928-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="b7928-132">Ativos devem ser armazenados no pacote do aplicativo e a animação não é suportada atualmente.</span><span class="sxs-lookup"><span data-stu-id="b7928-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="b7928-133">Se o parâmetro "Caminho" é deixado em branco Windows mostrará o slate 2D, em vez de iniciador do 3D.</span><span class="sxs-lookup"><span data-stu-id="b7928-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="b7928-134">**Observação:** .glb ativo deve ser marcado como "Conteúdo" em suas configurações de compilação antes de compilar e executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b7928-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="b7928-135">![Selecione o .glb no Gerenciador de soluções e use a seção de propriedades para marcá-la como "Conteúdo" nas configurações de build](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="b7928-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="b7928-136">*Selecione o .glb no Gerenciador de soluções e use a seção de propriedades para marcá-la como "Conteúdo" nas configurações de build*</span><span class="sxs-lookup"><span data-stu-id="b7928-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="b7928-137">Caixa delimitadora</span><span class="sxs-lookup"><span data-stu-id="b7928-137">Bounding box</span></span>

<span data-ttu-id="b7928-138">Uma caixa delimitadora pode ser usada para adicionar, opcionalmente, uma região de buffer adicional em torno do objeto.</span><span class="sxs-lookup"><span data-stu-id="b7928-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="b7928-139">A caixa delimitadora é especificada usando um ponto central e extensões que indicam a distância entre o centro da caixa delimitadora e suas bordas em cada eixo.</span><span class="sxs-lookup"><span data-stu-id="b7928-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="b7928-140">Unidades para a caixa delimitadora podem ser mapeadas para 1 unidade = 1 metro.</span><span class="sxs-lookup"><span data-stu-id="b7928-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="b7928-141">Se uma caixa delimitadora não for fornecida, em seguida, um será ser ajustado automaticamente para a malha do objeto.</span><span class="sxs-lookup"><span data-stu-id="b7928-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="b7928-142">Se a caixa delimitadora fornecida for menor que o modelo, em seguida, ele será redimensionado para caber da malha.</span><span class="sxs-lookup"><span data-stu-id="b7928-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="b7928-143">Suporte para o atributo de caixa delimitadora será fornecido com a atualização do Windows RS4 como uma propriedade no elemento MixedRealityModel.</span><span class="sxs-lookup"><span data-stu-id="b7928-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="b7928-144">Para definir uma caixa delimitadora pela primeira vez, na parte superior do aplicativo, o manifesto de adicionar o esquema uap6 e incluí-lo-los como ignorável namespaces:</span><span class="sxs-lookup"><span data-stu-id="b7928-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="b7928-145">Em seguida, em que o MixedRealityModel defina a propriedade de SpatialBoundingBox para definir a caixa delimitadora:</span><span class="sxs-lookup"><span data-stu-id="b7928-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="b7928-146">Usando o Unity</span><span class="sxs-lookup"><span data-stu-id="b7928-146">Using Unity</span></span>

<span data-ttu-id="b7928-147">Ao trabalhar com o Unity o projeto deve ser criado e aberto no Visual Studio antes do manifesto do aplicativo pode ser editado.</span><span class="sxs-lookup"><span data-stu-id="b7928-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="b7928-148">O iniciador do 3D deve ser redefinido no manifesto ao criar e implantar uma nova solução do Visual Studio do Unity.</span><span class="sxs-lookup"><span data-stu-id="b7928-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="b7928-149">Profundo 3D vincula (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="b7928-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="b7928-150">Esse recurso foi adicionado como parte da atualização de criadores de outono (RS3) 2017 para fones imersivos em exposição (VR) e como parte de abril de 2018 atualização (RS4) para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b7928-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="b7928-151">Verifique se que seu aplicativo está definido em uma versão do SDK do Windows, maior que ou igual a 10.0.16299 em fones imersivos em exposição (VR) e 10.0.17125 em HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b7928-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="b7928-152">Você pode encontrar o SDK mais recente do Windows [aqui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="b7928-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="b7928-153">Links profundos 3D (secondaryTiles) só funcionam com aplicativos da UWP 2D.</span><span class="sxs-lookup"><span data-stu-id="b7928-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="b7928-154">No entanto, você pode criar uma [inicializador de aplicativos 3D](implementing-3d-app-launchers.md) para iniciar um aplicativo exclusivo a partir do Windows Mixed Reality inicial.</span><span class="sxs-lookup"><span data-stu-id="b7928-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="b7928-155">Seus aplicativos 2D podem ser aprimorados para o Windows Mixed Reality, adicionando a capacidade de colocar os modelos 3D do seu aplicativo para o [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) como links profundos para conteúdos dentro do seu aplicativo 2D, assim como [secundário 2D blocos](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) no menu Iniciar do Windows.</span><span class="sxs-lookup"><span data-stu-id="b7928-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="b7928-156">Por exemplo, você pode criar photospheres de 360° que vinculam diretamente em um aplicativo de Visualizador de fotos de 360° ou permitir que os usuários a colocar o conteúdo 3D de uma coleção de ativos que abre uma página de detalhes sobre o autor.</span><span class="sxs-lookup"><span data-stu-id="b7928-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="b7928-157">Esses são apenas duas maneiras de expandir a funcionalidade do seu aplicativo 2D com conteúdo 3D.</span><span class="sxs-lookup"><span data-stu-id="b7928-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="b7928-158">Criando um "secondaryTile" 3D</span><span class="sxs-lookup"><span data-stu-id="b7928-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="b7928-159">Você pode colocar o conteúdo 3D de seu aplicativo usando "secondaryTiles" definindo um modelo de realidade misturada no momento da criação.</span><span class="sxs-lookup"><span data-stu-id="b7928-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="b7928-160">Modelos de realidade misturada são criados, fazendo referência a um ativo de 3D em seu pacote do aplicativo e, opcionalmente, definindo uma caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="b7928-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="b7928-161">Atualmente, não há suporte para a criação de "secondaryTiles" de dentro de um modo de exibição exclusivo.</span><span class="sxs-lookup"><span data-stu-id="b7928-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

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

### <a name="bounding-box"></a><span data-ttu-id="b7928-162">Caixa delimitadora</span><span class="sxs-lookup"><span data-stu-id="b7928-162">Bounding box</span></span>

<span data-ttu-id="b7928-163">Uma caixa delimitadora pode ser usada para adicionar uma região de buffer adicional em torno do objeto.</span><span class="sxs-lookup"><span data-stu-id="b7928-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="b7928-164">A caixa delimitadora é especificada usando um ponto central e extensões que indicam a distância entre o centro da caixa delimitadora e suas bordas em cada eixo.</span><span class="sxs-lookup"><span data-stu-id="b7928-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="b7928-165">Unidades para a caixa delimitadora podem ser mapeadas para 1 unidade = 1 metro.</span><span class="sxs-lookup"><span data-stu-id="b7928-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="b7928-166">Se uma caixa delimitadora não for fornecida, em seguida, um será ser ajustado automaticamente para a malha do objeto.</span><span class="sxs-lookup"><span data-stu-id="b7928-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="b7928-167">Se a caixa delimitadora fornecida for menor que o modelo, em seguida, ele será redimensionado para caber da malha.</span><span class="sxs-lookup"><span data-stu-id="b7928-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="b7928-168">Comportamento de ativação</span><span class="sxs-lookup"><span data-stu-id="b7928-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="b7928-169">Esse recurso terá suporte a partir da atualização do Windows RS4.</span><span class="sxs-lookup"><span data-stu-id="b7928-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="b7928-170">Certifique-se que seu aplicativo está buscando uma versão do SDK do Windows, maior que ou igual a 10.0.17125 se você planeja usar esse recurso</span><span class="sxs-lookup"><span data-stu-id="b7928-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="b7928-171">Você pode definir o comportamento de ativação para um secondaryTile 3D controlar como ele reage quando um usuário o seleciona.</span><span class="sxs-lookup"><span data-stu-id="b7928-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="b7928-172">Isso pode ser usado para colocar objetos 3D na realidade misturada inicial que são purley decorativo ou informativo.</span><span class="sxs-lookup"><span data-stu-id="b7928-172">This can be used to place 3D objects in the Mixed Reality home that are purley informative or decorative.</span></span> <span data-ttu-id="b7928-173">Há suporte para os seguintes tipos de comportamento de ativação:</span><span class="sxs-lookup"><span data-stu-id="b7928-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="b7928-174">Default: Quando um usuário seleciona o secondaryTile 3D, o aplicativo é ativado</span><span class="sxs-lookup"><span data-stu-id="b7928-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="b7928-175">Nenhum: Quando o usuário seleciona o secondaryTile 3D, nada acontece e o aplicativo não está ativado.</span><span class="sxs-lookup"><span data-stu-id="b7928-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="b7928-176">Como obter e atualizar um existente "secondaryTile"</span><span class="sxs-lookup"><span data-stu-id="b7928-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="b7928-177">Os desenvolvedores podem obter uma lista de seus blocos secundários existentes, que inclui as propriedades que eles especificado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b7928-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="b7928-178">Eles também podem atualizar as propriedades de alteração do valor e, em seguida, chamando UpdateAsync().</span><span class="sxs-lookup"><span data-stu-id="b7928-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="b7928-179">Verificando se o usuário é na realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="b7928-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="b7928-180">Links profundos 3D (secondaryTiles) só podem ser criados enquanto o modo de exibição está sendo exibido em um headset de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="b7928-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="b7928-181">Quando o modo de exibição não está sendo apresentado um Headset de realidade mista do Windows, é recomendável normalmente lidar com isso, ocultando o ponto de entrada ou mostrando uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="b7928-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="b7928-182">Você pode verificar isso consultando [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span><span class="sxs-lookup"><span data-stu-id="b7928-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="b7928-183">Notificações de bloco</span><span class="sxs-lookup"><span data-stu-id="b7928-183">Tile notifications</span></span>

<span data-ttu-id="b7928-184">Notificações de bloco não damos suporte a enviar uma atualização com um ativo de 3D.</span><span class="sxs-lookup"><span data-stu-id="b7928-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="b7928-185">Isso significa que os desenvolvedores não poderão fazer o seguinte</span><span class="sxs-lookup"><span data-stu-id="b7928-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="b7928-186">Notificações por push</span><span class="sxs-lookup"><span data-stu-id="b7928-186">Push Notifications</span></span>
* <span data-ttu-id="b7928-187">Sondagem periódica</span><span class="sxs-lookup"><span data-stu-id="b7928-187">Periodic Polling</span></span>
* <span data-ttu-id="b7928-188">Notificações agendadas</span><span class="sxs-lookup"><span data-stu-id="b7928-188">Scheduled Notifications</span></span>

<span data-ttu-id="b7928-189">Para obter mais informações sobre outros recursos, blocos e atributos e como eles são usados para blocos 2D, consulte o [blocos para obter a documentação de aplicativos UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="b7928-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="b7928-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7928-190">See also</span></span>

* <span data-ttu-id="b7928-191">[Exemplo de modelo de realidade misturada](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contendo um inicializador de aplicativos 3D.</span><span class="sxs-lookup"><span data-stu-id="b7928-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="b7928-192">Diretrizes de design de iniciador do aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="b7928-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="b7928-193">Criar modelos 3D para uso no ambiente doméstico Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b7928-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="b7928-194">Implementando os inicializadores de aplicativos 3D (aplicativos Win32)</span><span class="sxs-lookup"><span data-stu-id="b7928-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="b7928-195">Navegando o Windows Mixed Reality inicial</span><span class="sxs-lookup"><span data-stu-id="b7928-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
