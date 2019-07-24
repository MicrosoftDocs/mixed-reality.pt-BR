---
title: Salvando e localizando seus arquivos
description: Como localizar, salvar e compartilhar arquivos no HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: como fazer, seletor de arquivos, arquivos, fotos, vídeos, imagens, OneDrive, armazenamento, explorador de arquivos
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524606"
---
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="e3947-104">Salvando e localizando seus arquivos</span><span class="sxs-lookup"><span data-stu-id="e3947-104">Saving and finding your files</span></span>

<span data-ttu-id="e3947-105">Os arquivos podem ser salvos e gerenciados de maneira semelhante a outros dispositivos Windows 10 desktop e Mobile:</span><span class="sxs-lookup"><span data-stu-id="e3947-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="e3947-106">Usando o aplicativo explorador de arquivos para acessar pastas locais</span><span class="sxs-lookup"><span data-stu-id="e3947-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="e3947-107">Dentro do próprio armazenamento de um aplicativo</span><span class="sxs-lookup"><span data-stu-id="e3947-107">Within an app's own storage</span></span>
* <span data-ttu-id="e3947-108">Em uma pasta conhecida especial (como a biblioteca de vídeo ou música)</span><span class="sxs-lookup"><span data-stu-id="e3947-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="e3947-109">Usando um serviço de armazenamento que inclui um seletor de aplicativo e de arquivo (como o OneDrive)</span><span class="sxs-lookup"><span data-stu-id="e3947-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="e3947-110">Usando um computador desktop conectado ao seu HoloLens via USB, via suporte a MTP (protocolo de transferência de mídia)</span><span class="sxs-lookup"><span data-stu-id="e3947-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="e3947-111">Explorador de Arquivos</span><span class="sxs-lookup"><span data-stu-id="e3947-111">File Explorer</span></span>

<span data-ttu-id="e3947-112">Você pode usar o aplicativo explorador de arquivos para mover e excluir arquivos de dentro do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e3947-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="e3947-113">Se você não vir nenhum arquivo no explorador de arquivos, o filtro "recente" pode estar ativo (o ícone de relógio é realçado no painel esquerdo).</span><span class="sxs-lookup"><span data-stu-id="e3947-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="e3947-114">Para corrigir isso, selecione o ícone este documento de **dispositivo** no painel esquerdo (abaixo do ícone de relógio) ou abra o menu e selecione **este dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="e3947-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="e3947-115">Arquivos em um aplicativo</span><span class="sxs-lookup"><span data-stu-id="e3947-115">Files within an app</span></span>

<span data-ttu-id="e3947-116">Se um aplicativo salvar arquivos em seu dispositivo, você poderá usar esse aplicativo para acessá-los.</span><span class="sxs-lookup"><span data-stu-id="e3947-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="e3947-117">Onde estão minhas fotos/vídeos?</span><span class="sxs-lookup"><span data-stu-id="e3947-117">Where are my photos/videos?</span></span>

<span data-ttu-id="e3947-118">Fotos mistas de [captura de realidade](mixed-reality-capture.md) e vídeos são salvos na pasta de rolagem da câmera do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e3947-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="e3947-119">Eles podem ser acessados por meio do [aplicativo fotos](see-your-photos.md#photos-app).</span><span class="sxs-lookup"><span data-stu-id="e3947-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="e3947-120">Você pode usar o aplicativo de fotos para sincronizar suas fotos e vídeos no OneDrive.</span><span class="sxs-lookup"><span data-stu-id="e3947-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="e3947-121">Você também pode acessar suas fotos e vídeos por meio da página de captura da realidade misturada do [portal do dispositivo do Windows](using-the-windows-device-portal.md#mixed-reality-capture).</span><span class="sxs-lookup"><span data-stu-id="e3947-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="e3947-122">Solicitando arquivos de outro aplicativo</span><span class="sxs-lookup"><span data-stu-id="e3947-122">Requesting files from another app</span></span>

<span data-ttu-id="e3947-123">Um aplicativo pode solicitar para salvar um arquivo ou abrir um arquivo de outro aplicativo por meio de selecionadores de [arquivos](app-model.md#file-pickers).</span><span class="sxs-lookup"><span data-stu-id="e3947-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="e3947-124">Pastas conhecidas</span><span class="sxs-lookup"><span data-stu-id="e3947-124">Known folders</span></span>

<span data-ttu-id="e3947-125">O HoloLens dá suporte a várias [pastas conhecidas](app-model.md#known-folders) que os aplicativos podem solicitar permissão para acessar.</span><span class="sxs-lookup"><span data-stu-id="e3947-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="e3947-126">Arquivos em um serviço</span><span class="sxs-lookup"><span data-stu-id="e3947-126">Files in a service</span></span>

<span data-ttu-id="e3947-127">Para salvar um arquivo (ou acessar arquivos de) de um serviço, o aplicativo associado ao serviço deve ser instalado.</span><span class="sxs-lookup"><span data-stu-id="e3947-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="e3947-128">Para salvar arquivos e acessar arquivos do OneDrive, você precisará instalar o [aplicativo do onedrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span><span class="sxs-lookup"><span data-stu-id="e3947-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="e3947-129">MTP (protocolo de transferência de mídia)</span><span class="sxs-lookup"><span data-stu-id="e3947-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="e3947-130">Semelhante a outros dispositivos móveis, conecte o HoloLens ao seu PC desktop e abra o explorador de arquivos no PC para acessar suas bibliotecas de HoloLens (fotos, vídeos, documentos) para facilitar a transferência.</span><span class="sxs-lookup"><span data-stu-id="e3947-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="e3947-131">Esclarecimentos</span><span class="sxs-lookup"><span data-stu-id="e3947-131">Clarifications</span></span>

* <span data-ttu-id="e3947-132">O HoloLens não dá suporte à conexão com discos rígidos externos ou cartões SD.</span><span class="sxs-lookup"><span data-stu-id="e3947-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="e3947-133">A partir da [atualização do Windows 10 de abril de 2018 (RS4) para o hololens](release-notes-april-2018.md), o hololens inclui o explorador de arquivos para salvar e gerenciar arquivos no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e3947-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="e3947-134">A adição do explorador de arquivos também oferece a capacidade de escolher o seletor de arquivos (por exemplo, salvar um arquivo em seu dispositivo ou OneDrive).</span><span class="sxs-lookup"><span data-stu-id="e3947-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
