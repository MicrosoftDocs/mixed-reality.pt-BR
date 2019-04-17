---
title: Obtenha aplicativos para o HoloLens
description: Descreve a instalação de aplicativos para o HoloLens, tanto por meio da Microsoft Store e o sideload.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: fazer sideload, carga de lado, sideload, store, uwp, aplicativo, instalar
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589083"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="afef4-104">Obtenha aplicativos para o HoloLens</span><span class="sxs-lookup"><span data-stu-id="afef4-104">Get apps for HoloLens</span></span>

<span data-ttu-id="afef4-105">Como um dispositivo Windows 10, HoloLens, dá suporte a muitos aplicativos UWP na loja de aplicativos, bem como novos aplicativos criados especificamente para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="afef4-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="afef4-106">Sobre eles, você talvez ainda queira [desenvolver](development-overview.md) e instalar seus próprios aplicativos ou aqueles dos seus amigos!</span><span class="sxs-lookup"><span data-stu-id="afef4-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="afef4-107">Instalação de aplicativos</span><span class="sxs-lookup"><span data-stu-id="afef4-107">Installing Apps</span></span>

<span data-ttu-id="afef4-108">Há três maneiras de instalar novos aplicativos em sua HoloLens.</span><span class="sxs-lookup"><span data-stu-id="afef4-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="afef4-109">O método primário será instalar novos aplicativos da Store do Windows.</span><span class="sxs-lookup"><span data-stu-id="afef4-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="afef4-110">No entanto, você também pode instalar seus próprios aplicativos usando o Portal de dispositivos ou implantá-los a partir do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="afef4-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="afef4-111">De que a Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="afef4-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="afef4-112">Executar uma [bloom](gestures.md#bloom) gesto para abrir o [Menu Iniciar](navigating-the-windows-mixed-reality-home.md#start-menu).</span><span class="sxs-lookup"><span data-stu-id="afef4-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="afef4-113">Selecione o aplicativo Store e, em seguida, toque para colocar esse bloco no seu mundo.</span><span class="sxs-lookup"><span data-stu-id="afef4-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="afef4-114">Depois que o aplicativo Store é aberta, use a barra de pesquisa para procurar qualquer aplicativo desejado.</span><span class="sxs-lookup"><span data-stu-id="afef4-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="afef4-115">Selecione **Obtenha** ou **instalar** na página do aplicativo (uma compra pode ser necessária).</span><span class="sxs-lookup"><span data-stu-id="afef4-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="afef4-116">Instalar um pacote de aplicativos com o Portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="afef4-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="afef4-117">Estabelecer uma conexão de [Portal do dispositivo](using-the-windows-device-portal.md) para o destino HoloLens.</span><span class="sxs-lookup"><span data-stu-id="afef4-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="afef4-118">Navegue até a **aplicativos** página no painel de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="afef4-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="afef4-119">Sob **pacote do aplicativo** navegue até o arquivo. AppX associado ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="afef4-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="afef4-120">Certifique-se de fazer referência a quaisquer arquivos associados de dependência e o certificado.</span><span class="sxs-lookup"><span data-stu-id="afef4-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="afef4-121">Clique em **acesse**.</span><span class="sxs-lookup"><span data-stu-id="afef4-121">Click **Go**.</span></span>

<span data-ttu-id="afef4-122">![Instalar o formulário do aplicativo no Windows Device Portal no Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="afef4-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="afef4-123">Usando o Windows Device Portal para instalar um aplicativo em HoloLens</span><span class="sxs-lookup"><span data-stu-id="afef4-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="afef4-124">Implantação do Microsoft Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="afef4-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="afef4-125">Abra a solução do Visual Studio do seu aplicativo (arquivo. sln).</span><span class="sxs-lookup"><span data-stu-id="afef4-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="afef4-126">Abra o projeto **propriedades** .</span><span class="sxs-lookup"><span data-stu-id="afef4-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="afef4-127">Selecione a configuração de compilação a seguir: Computador mestre/x86/remoto.</span><span class="sxs-lookup"><span data-stu-id="afef4-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="afef4-128">Quando você seleciona o computador remoto:</span><span class="sxs-lookup"><span data-stu-id="afef4-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="afef4-129">Verifique se os pontos de endereço para o endereço de IP de WiFi dos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="afef4-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="afef4-130">Definir a autenticação universal (protocolo não criptografado).</span><span class="sxs-lookup"><span data-stu-id="afef4-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="afef4-131">Compile sua solução.</span><span class="sxs-lookup"><span data-stu-id="afef4-131">Build your solution.</span></span>
6. <span data-ttu-id="afef4-132">Clique o **máquina remota** botão para implantar o aplicativo do seu computador de desenvolvimento para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="afef4-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="afef4-133">Se você já tiver uma compilação existente no HoloLens, selecione Sim para reinstalar essa versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="afef4-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="afef4-134">![Implantação de máquina remota para os aplicativos Microsoft HoloLens no Visual Studio](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="afef4-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="afef4-135">O aplicativo será instalar e inicializar no seu HoloLens automaticamente.</span><span class="sxs-lookup"><span data-stu-id="afef4-135">The application will install and auto launch on your HoloLens.</span></span>
