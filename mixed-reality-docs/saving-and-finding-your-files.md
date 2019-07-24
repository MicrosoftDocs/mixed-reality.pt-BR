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
# <a name="saving-and-finding-your-files"></a>Salvando e localizando seus arquivos

Os arquivos podem ser salvos e gerenciados de maneira semelhante a outros dispositivos Windows 10 desktop e Mobile:
* Usando o aplicativo explorador de arquivos para acessar pastas locais
* Dentro do próprio armazenamento de um aplicativo
* Em uma pasta conhecida especial (como a biblioteca de vídeo ou música)
* Usando um serviço de armazenamento que inclui um seletor de aplicativo e de arquivo (como o OneDrive)
* Usando um computador desktop conectado ao seu HoloLens via USB, via suporte a MTP (protocolo de transferência de mídia)

## <a name="file-explorer"></a>Explorador de Arquivos

Você pode usar o aplicativo explorador de arquivos para mover e excluir arquivos de dentro do HoloLens.

>[!NOTE]
>Se você não vir nenhum arquivo no explorador de arquivos, o filtro "recente" pode estar ativo (o ícone de relógio é realçado no painel esquerdo). Para corrigir isso, selecione o ícone este documento de **dispositivo** no painel esquerdo (abaixo do ícone de relógio) ou abra o menu e selecione **este dispositivo**.

## <a name="files-within-an-app"></a>Arquivos em um aplicativo

Se um aplicativo salvar arquivos em seu dispositivo, você poderá usar esse aplicativo para acessá-los.

### <a name="where-are-my-photosvideos"></a>Onde estão minhas fotos/vídeos?

Fotos mistas de [captura de realidade](mixed-reality-capture.md) e vídeos são salvos na pasta de rolagem da câmera do dispositivo. Eles podem ser acessados por meio do [aplicativo fotos](see-your-photos.md#photos-app). Você pode usar o aplicativo de fotos para sincronizar suas fotos e vídeos no OneDrive. Você também pode acessar suas fotos e vídeos por meio da página de captura da realidade misturada do [portal do dispositivo do Windows](using-the-windows-device-portal.md#mixed-reality-capture).

### <a name="requesting-files-from-another-app"></a>Solicitando arquivos de outro aplicativo

Um aplicativo pode solicitar para salvar um arquivo ou abrir um arquivo de outro aplicativo por meio de selecionadores de [arquivos](app-model.md#file-pickers).

## <a name="known-folders"></a>Pastas conhecidas

O HoloLens dá suporte a várias [pastas conhecidas](app-model.md#known-folders) que os aplicativos podem solicitar permissão para acessar.

## <a name="files-in-a-service"></a>Arquivos em um serviço

Para salvar um arquivo (ou acessar arquivos de) de um serviço, o aplicativo associado ao serviço deve ser instalado. Para salvar arquivos e acessar arquivos do OneDrive, você precisará instalar o [aplicativo do onedrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).

## <a name="mtp-media-transfer-protocol"></a>MTP (protocolo de transferência de mídia)

Semelhante a outros dispositivos móveis, conecte o HoloLens ao seu PC desktop e abra o explorador de arquivos no PC para acessar suas bibliotecas de HoloLens (fotos, vídeos, documentos) para facilitar a transferência.

## <a name="clarifications"></a>Esclarecimentos

* O HoloLens não dá suporte à conexão com discos rígidos externos ou cartões SD.
* A partir da [atualização do Windows 10 de abril de 2018 (RS4) para o hololens](release-notes-april-2018.md), o hololens inclui o explorador de arquivos para salvar e gerenciar arquivos no dispositivo. A adição do explorador de arquivos também oferece a capacidade de escolher o seletor de arquivos (por exemplo, salvar um arquivo em seu dispositivo ou OneDrive).
