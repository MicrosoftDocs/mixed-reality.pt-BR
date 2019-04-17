---
title: Salvando e encontrar seus arquivos
description: Como localizar, salvar e compartilhar arquivos em HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: como fazer, seletor de arquivos, arquivos, fotos, vídeos, imagens, OneDrive, o armazenamento, o Explorador de arquivos
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590474"
---
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="67a33-104">Salvando e encontrar seus arquivos</span><span class="sxs-lookup"><span data-stu-id="67a33-104">Saving and finding your files</span></span>

<span data-ttu-id="67a33-105">Arquivos podem ser salvos e gerenciados de maneira semelhante a outros Windows 10 Desktop e dispositivos móveis:</span><span class="sxs-lookup"><span data-stu-id="67a33-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="67a33-106">Usando o Explorador de arquivos de aplicativo para acessar pastas locais</span><span class="sxs-lookup"><span data-stu-id="67a33-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="67a33-107">Dentro de um armazenamento do aplicativo</span><span class="sxs-lookup"><span data-stu-id="67a33-107">Within an app's own storage</span></span>
* <span data-ttu-id="67a33-108">Em uma pasta especial conhecida (como a biblioteca de vídeo ou música)</span><span class="sxs-lookup"><span data-stu-id="67a33-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="67a33-109">Usando um serviço de armazenamento que inclui um selecionador de aplicativo e arquivo (como OneDrive)</span><span class="sxs-lookup"><span data-stu-id="67a33-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="67a33-110">Usando um computador desktop conectado à sua HoloLens via USB, por meio do suporte da consulta MTP (protocolo de transferência de mídia)</span><span class="sxs-lookup"><span data-stu-id="67a33-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="67a33-111">Explorador de Arquivos</span><span class="sxs-lookup"><span data-stu-id="67a33-111">File Explorer</span></span>

<span data-ttu-id="67a33-112">Você pode usar o aplicativo Explorador de arquivos para mover e excluir arquivos a partir do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="67a33-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="67a33-113">Se você não vir todos os arquivos no Explorador de arquivos, o filtro "Recentes" pode estar ativo (o ícone de relógio é realçado no painel esquerdo).</span><span class="sxs-lookup"><span data-stu-id="67a33-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="67a33-114">Para corrigir isso, selecione a **este dispositivo** documentar o ícone no painel esquerdo (abaixo do ícone de relógio), ou abra o menu e selecione **este dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="67a33-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="67a33-115">Arquivos dentro de um aplicativo</span><span class="sxs-lookup"><span data-stu-id="67a33-115">Files within an app</span></span>

<span data-ttu-id="67a33-116">Se um aplicativo salva os arquivos em seu dispositivo, você pode usar esse aplicativo para acessá-los.</span><span class="sxs-lookup"><span data-stu-id="67a33-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="67a33-117">Onde estão Meus fotos/vídeos?</span><span class="sxs-lookup"><span data-stu-id="67a33-117">Where are my photos/videos?</span></span>

<span data-ttu-id="67a33-118">[Misto captura realidade](mixed-reality-capture.md) fotos e vídeos são salvos para pasta de câmera do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="67a33-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="67a33-119">Eles podem ser acessados por meio de [aplicativo fotos](see-your-photos.md#photos-app).</span><span class="sxs-lookup"><span data-stu-id="67a33-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="67a33-120">Você pode usar o aplicativo de fotos para sincronizar suas fotos e vídeos no OneDrive.</span><span class="sxs-lookup"><span data-stu-id="67a33-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="67a33-121">Você também pode acessar suas fotos e vídeos por meio da página de captura de realidade mista do [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span><span class="sxs-lookup"><span data-stu-id="67a33-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="67a33-122">Solicitando os arquivos de outro aplicativo</span><span class="sxs-lookup"><span data-stu-id="67a33-122">Requesting files from another app</span></span>

<span data-ttu-id="67a33-123">Um aplicativo pode solicitar para salvar um arquivo ou abrir um arquivo de outro aplicativo por meio [selecionadores de arquivo](app-model.md#file-pickers).</span><span class="sxs-lookup"><span data-stu-id="67a33-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="67a33-124">Pastas conhecidas</span><span class="sxs-lookup"><span data-stu-id="67a33-124">Known folders</span></span>

<span data-ttu-id="67a33-125">HoloLens dá suporte a inúmeros [conhecido pastas](app-model.md#known-folders) que os aplicativos podem solicitar permissão para acessar.</span><span class="sxs-lookup"><span data-stu-id="67a33-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="67a33-126">Arquivos em um serviço</span><span class="sxs-lookup"><span data-stu-id="67a33-126">Files in a service</span></span>

<span data-ttu-id="67a33-127">Para salvar um arquivo (ou acessar arquivos de) um serviço, o aplicativo associado com o serviço deve ser instalado.</span><span class="sxs-lookup"><span data-stu-id="67a33-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="67a33-128">Para salvar arquivos e acessar arquivos do OneDrive, você precisará instalar o [aplicativo OneDrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span><span class="sxs-lookup"><span data-stu-id="67a33-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="67a33-129">MTP (protocolo de transferência de mídia)</span><span class="sxs-lookup"><span data-stu-id="67a33-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="67a33-130">Semelhante aos outros dispositivos móveis, conecte o HoloLens para seu computador desktop e abra o Explorador de arquivos no PC para acessar suas bibliotecas do HoloLens (fotos, vídeos, documentos) para facilitar a transferência.</span><span class="sxs-lookup"><span data-stu-id="67a33-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="67a33-131">Esclarecimentos</span><span class="sxs-lookup"><span data-stu-id="67a33-131">Clarifications</span></span>

* <span data-ttu-id="67a33-132">HoloLens não oferece suporte para se conectar a unidades de disco rígido externas ou cartões SD.</span><span class="sxs-lookup"><span data-stu-id="67a33-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="67a33-133">Desde o [Windows 10 de abril de 2018 atualização (RS4) para o HoloLens](release-notes-april-2018.md), HoloLens inclui o Explorador de arquivos para salvar e gerenciar arquivos no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="67a33-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="67a33-134">A adição do Explorador de arquivos também oferece a capacidade de escolher seu seletor de arquivos (por exemplo, salvar um arquivo em seu dispositivo ou para o OneDrive).</span><span class="sxs-lookup"><span data-stu-id="67a33-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
