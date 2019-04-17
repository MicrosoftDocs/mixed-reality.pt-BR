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
# <a name="saving-and-finding-your-files"></a>Salvando e encontrar seus arquivos

Arquivos podem ser salvos e gerenciados de maneira semelhante a outros Windows 10 Desktop e dispositivos móveis:
* Usando o Explorador de arquivos de aplicativo para acessar pastas locais
* Dentro de um armazenamento do aplicativo
* Em uma pasta especial conhecida (como a biblioteca de vídeo ou música)
* Usando um serviço de armazenamento que inclui um selecionador de aplicativo e arquivo (como OneDrive)
* Usando um computador desktop conectado à sua HoloLens via USB, por meio do suporte da consulta MTP (protocolo de transferência de mídia)

## <a name="file-explorer"></a>Explorador de Arquivos

Você pode usar o aplicativo Explorador de arquivos para mover e excluir arquivos a partir do HoloLens.

>[!NOTE]
>Se você não vir todos os arquivos no Explorador de arquivos, o filtro "Recentes" pode estar ativo (o ícone de relógio é realçado no painel esquerdo). Para corrigir isso, selecione a **este dispositivo** documentar o ícone no painel esquerdo (abaixo do ícone de relógio), ou abra o menu e selecione **este dispositivo**.

## <a name="files-within-an-app"></a>Arquivos dentro de um aplicativo

Se um aplicativo salva os arquivos em seu dispositivo, você pode usar esse aplicativo para acessá-los.

### <a name="where-are-my-photosvideos"></a>Onde estão Meus fotos/vídeos?

[Misto captura realidade](mixed-reality-capture.md) fotos e vídeos são salvos para pasta de câmera do dispositivo. Eles podem ser acessados por meio de [aplicativo fotos](see-your-photos.md#photos-app). Você pode usar o aplicativo de fotos para sincronizar suas fotos e vídeos no OneDrive. Você também pode acessar suas fotos e vídeos por meio da página de captura de realidade mista do [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).

### <a name="requesting-files-from-another-app"></a>Solicitando os arquivos de outro aplicativo

Um aplicativo pode solicitar para salvar um arquivo ou abrir um arquivo de outro aplicativo por meio [selecionadores de arquivo](app-model.md#file-pickers).

## <a name="known-folders"></a>Pastas conhecidas

HoloLens dá suporte a inúmeros [conhecido pastas](app-model.md#known-folders) que os aplicativos podem solicitar permissão para acessar.

## <a name="files-in-a-service"></a>Arquivos em um serviço

Para salvar um arquivo (ou acessar arquivos de) um serviço, o aplicativo associado com o serviço deve ser instalado. Para salvar arquivos e acessar arquivos do OneDrive, você precisará instalar o [aplicativo OneDrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).

## <a name="mtp-media-transfer-protocol"></a>MTP (protocolo de transferência de mídia)

Semelhante aos outros dispositivos móveis, conecte o HoloLens para seu computador desktop e abra o Explorador de arquivos no PC para acessar suas bibliotecas do HoloLens (fotos, vídeos, documentos) para facilitar a transferência.

## <a name="clarifications"></a>Esclarecimentos

* HoloLens não oferece suporte para se conectar a unidades de disco rígido externas ou cartões SD.
* Desde o [Windows 10 de abril de 2018 atualização (RS4) para o HoloLens](release-notes-april-2018.md), HoloLens inclui o Explorador de arquivos para salvar e gerenciar arquivos no dispositivo. A adição do Explorador de arquivos também oferece a capacidade de escolher seu seletor de arquivos (por exemplo, salvar um arquivo em seu dispositivo ou para o OneDrive).
