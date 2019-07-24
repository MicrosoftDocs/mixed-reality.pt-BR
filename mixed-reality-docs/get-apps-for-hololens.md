---
title: Obter aplicativos para o HoloLens
description: Descreve a instalação de aplicativos para o HoloLens, por meio do Microsoft Store e do carregamento lateral.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Sideload, carga lateral, carga, armazenamento, UWP, aplicativo, instalação
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522545"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="8ad01-104">Obter aplicativos para o HoloLens</span><span class="sxs-lookup"><span data-stu-id="8ad01-104">Get apps for HoloLens</span></span>

<span data-ttu-id="8ad01-105">Como um dispositivo Windows 10, o HoloLens dá suporte a muitos aplicativos UWP existentes da loja de aplicativos, bem como novos aplicativos criados especificamente para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8ad01-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="8ad01-106">Além desses, talvez você queira até mesmo [desenvolver](development-overview.md) e instalar seus próprios aplicativos ou aqueles de seus amigos!</span><span class="sxs-lookup"><span data-stu-id="8ad01-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="8ad01-107">Instalando aplicativos</span><span class="sxs-lookup"><span data-stu-id="8ad01-107">Installing Apps</span></span>

<span data-ttu-id="8ad01-108">Há três maneiras de instalar novos aplicativos em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8ad01-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="8ad01-109">O método principal será instalar novos aplicativos da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="8ad01-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="8ad01-110">No entanto, você também pode instalar seus próprios aplicativos usando o portal do dispositivo ou implantando-os no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8ad01-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="8ad01-111">Da Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="8ad01-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="8ad01-112">Execute um gesto de [cair](gestures.md#bloom) para abrir o [menu iniciar](navigating-the-windows-mixed-reality-home.md#start-menu).</span><span class="sxs-lookup"><span data-stu-id="8ad01-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="8ad01-113">Selecione o aplicativo da loja e, em seguida, toque para colocar esse bloco em seu mundo.</span><span class="sxs-lookup"><span data-stu-id="8ad01-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="8ad01-114">Quando o aplicativo da loja for aberto, use a barra de pesquisa para procurar qualquer aplicativo desejado.</span><span class="sxs-lookup"><span data-stu-id="8ad01-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="8ad01-115">Selecione **obter** ou **instalar** na página do aplicativo (pode ser necessária uma compra).</span><span class="sxs-lookup"><span data-stu-id="8ad01-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="8ad01-116">Instalando um pacote de aplicativos com o portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="8ad01-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="8ad01-117">Estabeleça uma conexão do [portal do dispositivo](using-the-windows-device-portal.md) com o HoloLens de destino.</span><span class="sxs-lookup"><span data-stu-id="8ad01-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="8ad01-118">Navegue até a página **aplicativos** no painel de navegação esquerdo.</span><span class="sxs-lookup"><span data-stu-id="8ad01-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="8ad01-119">Em **pacote do aplicativo** , navegue até o arquivo. Appx associado ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8ad01-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="8ad01-120">Certifique-se de fazer referência a qualquer dependência associada e arquivos de certificado.</span><span class="sxs-lookup"><span data-stu-id="8ad01-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="8ad01-121">Clique em **ir**.</span><span class="sxs-lookup"><span data-stu-id="8ad01-121">Click **Go**.</span></span>

<span data-ttu-id="8ad01-122">![Instalar formulário de aplicativo no portal de dispositivo do Windows no Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="8ad01-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="8ad01-123">Usando o portal de dispositivos do Windows para instalar um aplicativo no HoloLens</span><span class="sxs-lookup"><span data-stu-id="8ad01-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="8ad01-124">Implantando do Microsoft Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="8ad01-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="8ad01-125">Abra a solução do Visual Studio do seu aplicativo (arquivo. sln).</span><span class="sxs-lookup"><span data-stu-id="8ad01-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="8ad01-126">Abra as **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="8ad01-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="8ad01-127">Selecione a seguinte configuração de compilação: Mestre/x86/computador remoto.</span><span class="sxs-lookup"><span data-stu-id="8ad01-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="8ad01-128">Quando você seleciona computador remoto:</span><span class="sxs-lookup"><span data-stu-id="8ad01-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="8ad01-129">Verifique se o endereço aponta para o endereço IP WiFi do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8ad01-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="8ad01-130">Defina a autenticação como universal (protocolo não criptografado).</span><span class="sxs-lookup"><span data-stu-id="8ad01-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="8ad01-131">Crie sua solução.</span><span class="sxs-lookup"><span data-stu-id="8ad01-131">Build your solution.</span></span>
6. <span data-ttu-id="8ad01-132">Clique no botão **máquina remota** para implantar o aplicativo do seu computador de desenvolvimento em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8ad01-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="8ad01-133">Se você já tiver uma compilação existente no HoloLens, selecione Sim para reinstalar essa nova versão.</span><span class="sxs-lookup"><span data-stu-id="8ad01-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="8ad01-134">![Implantação de máquina remota para aplicativos para o Microsoft HoloLens no Visual Studio](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="8ad01-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="8ad01-135">O aplicativo será instalado e iniciado automaticamente no seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8ad01-135">The application will install and auto launch on your HoloLens.</span></span>
