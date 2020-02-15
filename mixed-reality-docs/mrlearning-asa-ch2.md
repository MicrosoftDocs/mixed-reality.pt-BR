---
title: Tutoriais de âncoras espaciais do Azure-2. Salvando, recuperando e compartilhando âncoras espaciais do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 7b19233a9634e2568200476c9483464bbf9dd3c8
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250721"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. salvando, recuperando e compartilhando âncoras espaciais do Azure

Neste tutorial, você aprenderá como salvar âncoras espaciais do Azure em várias sessões de aplicativo salvando a ID de âncora no armazenamento do HoloLens 2. Você também aprenderá a compartilhar essa ID de âncora para outros dispositivos para um alinhamento de âncora de vários dispositivos.

## <a name="objectives"></a>Objetivos

* Saiba como salvar e recuperar IDs de âncora espacial do Azure de e para o disco local do HoloLens 2, para persistência entre sessões de aplicativo
* Saiba como compartilhar IDs de âncora espacial do Azure entre usuários em um cenário de vários dispositivos

## <a name="preparing-the-scene"></a>Preparando a cena

Na janela do projeto, navegue até **ativos** > **MRTK. Tutoriais. AzureSpatialAnchors** > pasta **pré-fabricados** Ao manter pressionado o botão CTRL, clique em **ButtonParent_SaveAnchorId** e **ButtonParent_ShareAnchorId** para selecionar os dois pré-fabricados e, em seguida, arraste-os para a janela hierarquia para adicioná-los à cena:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Persistir âncoras do Azure entre sessões de aplicativo-salvar ID de âncora em disco
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

Nesta seção, você aprenderá a salvar e recuperar a ID de âncora do Azure de e para o disco local do HoloLens 2. Isso permitirá que você consulte o Azure para a mesma ID de âncora entre diferentes sessões de aplicativo, permitindo que os hologramas ancorados sejam posicionados no mesmo local que na sessão do aplicativo anterior.

Na janela hierarquia, expanda o objeto **ButtonParent_SaveAnchorId** que contém dois botões, um botão para salvar a ID de âncora do Azure no armazenamento do HoloLens 2 e outro para recuperar a ID salva do disco:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

Siga as mesmas etapas da seção [Configurando os botões para operar as](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instruções de cena do tutorial anterior para configurar o componente de **botão pressionável holo Lens 2 (script)** e o componente de **interação (script)** em cada um dos dois botões:

* Para o objeto **SaveAzureAnchorIdToDisk** , atribua a função AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** .
* Para o objeto **GetAzureAnchorIdFromDisk** , atribua a função AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** .

Se você criar o aplicativo atualizado para seu HoloLens, agora poderá persistir as âncoras espaciais do Azure entre as sessões do aplicativo, salvando a ID da âncora do Azure. Para testá-lo, você pode seguir estas etapas:

1. Mova a experiência do Rocket Launcher para o local desejado.
2. Inicie a sessão do Azure.
3. Crie a âncora do Azure (cria âncoras no local da experiência do Rocket Launcher).
4. Salve a ID de âncora do Azure no disco.
5. Reinicie o aplicativo.
6. Obter a âncora do Azure do disco (carrega a ID de âncora que você acabou de salvar).
7. Inicie a sessão do Azure.
8. Localize a âncora do Azure (posiciona a experiência do Rocket Launcher no local da etapa 3).

## <a name="share-azure-anchors-between-multiple-devices"></a>Compartilhar âncoras do Azure entre vários dispositivos

Nesta seção, você aprenderá a compartilhar a ID de âncora do Azure entre vários dispositivos. Isso permitirá que vários dispositivos consultem o Azure para a mesma ID de âncora, permitindo que os hologramas ancorados sejam alinhados espacialmente. O alinhamento espacial, ou seja, Ver os mesmos hologramas no mesmo local físico entre vários dispositivos, é a chave para experiências compartilhadas locais no HoloLens 2.

Há várias maneiras de transferir IDs de âncora do Azure entre dispositivos, incluindo métodos descritos na série de [tutoriais de funcionalidades de vários usuários](mrlearning-sharing(photon)-ch1.md) . Neste exemplo, você usará um serviço Web simples para carregar e baixar IDs de âncora entre dispositivos.

Na janela hierarquia, expanda o objeto **ButtonParent_ShareAnchorId** que contém dois botões; um botão para carregar a ID de âncora do Azure para o servidor Web e outro para baixar a ID do servidor Web:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

Siga as mesmas etapas da seção [Configurando os botões para operar as](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instruções de cena do tutorial anterior para configurar o componente de **botão pressionável holo Lens 2 (script)** e o componente de **interação (script)** em cada um dos dois botões:

* Para o objeto **ShareAzureAnchorIdToNetwork** , atribua a função AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** .
* Para o objeto **GetAzureAnchorIdFromNetwork** , atribua a função AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** .

Se você criar o aplicativo atualizado para dois dispositivos HoloLens, agora poderá obter o alinhamento espacial entre eles compartilhando a ID de âncora do Azure. Para testá-lo, você pode seguir estas etapas:

1. No dispositivo de HoloLens 1: Mova a experiência do Rocket Launcher para o local desejado.
2. No dispositivo de HoloLens 1: Inicie a sessão do Azure.
3. No dispositivo de HoloLens 1: Crie a âncora do Azure (cria âncoras no local da experiência do Rocket Launcher).
4. No dispositivo de HoloLens 1: compartilhe a ID de âncora do Azure para a rede.
5. No dispositivo de HoloLens 2: reinicie o aplicativo.
6. No dispositivo de HoloLens 2: obter a ID de âncora compartilhada da rede (busca a ID de âncora apenas compartilhada do dispositivo do HoloLens 1).
7. No dispositivo de HoloLens 2: Inicie a sessão do Azure.
8. No dispositivo de HoloLens 2: encontre a âncora do Azure (posiciona a experiência do Rocket Launcher no local da etapa 3).

> [!TIP]
> Se você tiver apenas um HoloLens, ainda poderá testar a funcionalidade reiniciando o aplicativo em vez de usar um segundo dispositivo de HoloLens.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu como persistir as âncoras espaciais do Azure entre as sessões do aplicativo e reinicializações do aplicativo salvando a ID de âncora espacial do Azure no disco local no HoloLens. Você também aprendeu a compartilhar as âncoras espaciais do Azure entre vários dispositivos para uma experiência compartilhada básica com vários usuários e com holograma estático.

No próximo tutorial, você aprenderá a fornecer aos usuários comentários em tempo real. Esses comentários incluirão informações sobre a criação de âncora, a qualidade da compreensão do ambiente e o estado da sessão do Azure. Sem comentários, os usuários podem não saber se uma âncora foi carregada com êxito no Azure, se a qualidade do ambiente é suficiente para a criação de âncora ou para o estado atual.

[Próxima lição: 3. exibindo comentários de âncora espacial do Azure](mrlearning-asa-ch3.md)
