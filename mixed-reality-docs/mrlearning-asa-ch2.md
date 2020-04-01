---
title: Tutoriais de Âncoras Espaciais do Azure – 2. Salvar, recuperar e compartilhar Âncoras Espaciais do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 36f25229469e848a3f0612a5971cc8e9381262f5
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362004"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Salvar, recuperar e compartilhar Âncoras Espaciais do Azure

Neste tutorial, você aprenderá a salvar Âncoras Espaciais do Azure em várias sessões de aplicativo salvando a ID de âncora no armazenamento do HoloLens 2. Você também aprenderá a compartilhar essa ID de âncora para outros dispositivos para um alinhamento de âncora de vários dispositivos.

## <a name="objectives"></a>Objetivos

* Saiba como salvar e recuperar IDs de Âncora Espacial do Azure de e para o disco local do HoloLens 2 para persistência entre sessões de aplicativo
* Saiba como compartilhar IDs de Âncora Espacial do Azure entre usuários em um cenário de vários dispositivos

## <a name="preparing-the-scene"></a>Preparando a cena

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutoriais.AzureSpatialAnchors** > **Pré-Fabricados**. Ao manter pressionado o botão CTRL, clique em **ButtonParent_SaveAnchorId** e **ButtonParent_ShareAnchorId** para selecionar os dois pré-fabricados, então arraste-os para a janela Hierarquia para adicioná-los à cena:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Persistir âncoras do Azure entre sessões de aplicativo – salvar ID de âncora em disco
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

Nesta seção, você aprenderá a salvar e recuperar a ID de âncora do Azure de e para o disco local do HoloLens 2. Isso permitirá que você consulte o Azure para a mesma ID de âncora entre diferentes sessões de aplicativo, permitindo que os hologramas ancorados sejam posicionados na mesma localização que na sessão do aplicativo anterior.

Na janela Hierarquia, expanda o objeto **ButtonParent_SaveAnchorId objeto** que contém dois botões, um botão para salvar a ID de Âncora do Azure no armazenamento do HoloLens 2 e outro para recuperar a ID salva do disco:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

Siga as mesmas etapas apresentadas nas instruções para [configurar os botões para operar a cena](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) do tutorial anterior para configurar o componente **Botão pressionável do HoloLens 2 (Script)** e o componente **Interagir (Script)** em cada um dos dois botões:

* Para o objeto **SaveAzureAnchorIdToDisk**, atribua a função AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** .
* Para o objeto **GetAzureAnchorIdFromDisk**, atribua a função AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** .

Se você criar o aplicativo atualizado para seu HoloLens, agora poderá persistir as Âncoras Espaciais do Azure entre as sessões do aplicativo, salvando a ID da Âncora do Azure. Para testá-lo, você pode seguir estas etapas:

1. Mover a experiência do Rocket Launcher para a localização desejada.
2. Inicie a Sessão do Azure.
3. Criar a Âncora do Azure (cria âncoras na localização da experiência do Rocket Launcher).
4. Salve a ID de Âncora do Azure no disco.
5. Reinicie o aplicativo.
6. Obter a Âncora do Azure do Disco (carrega a ID de âncora que você acabou de salvar).
7. Inicie a Sessão do Azure.
8. Localize a Âncora do Azure (posiciona a experiência do Rocket Launcher na localização da etapa 3).

> [!NOTE]
> Para reiniciar completamente o aplicativo, depois de sair do modo de exibição do aplicativo imersivo, a janela do aplicativo na página inicial de realidade misturada precisará ser fechada antes de reiniciar o aplicativo no menu Iniciar. Para obter detalhes adicionais, você pode consultar a documentação [Como usar aplicativos no HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens).

## <a name="share-azure-anchors-between-multiple-devices"></a>Compartilhar Âncoras do Azure entre vários dispositivos

Nesta seção, você aprenderá a compartilhar a ID de Âncora do Azure entre vários dispositivos. Isso permitirá que vários dispositivos consultem o Azure para a mesma ID de âncora, permitindo o alinhamento espacial dos hologramas ancorados. O alinhamento espacial, ou seja, ver os mesmos hologramas na mesma localização física entre vários dispositivos, é o segredo para experiências compartilhadas locais no HoloLens 2.

Há várias maneiras de transferir IDs de Âncora do Azure entre dispositivos, incluindo métodos descritos na série de [tutoriais de funcionalidades de vários usuários](mrlearning-sharing(photon)-ch1.md). Neste exemplo, você usará um serviço Web simples para carregar e baixar IDs de âncora entre dispositivos.

Na janela Hierarquia, expanda o objeto **ButtonParent_ShareAnchorId**, que contém dois botões: um botão para carregar a ID de âncora do Azure para o servidor Web e outro para baixar a ID do servidor Web:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

Siga as mesmas etapas apresentadas nas instruções para [configurar os botões para operar a cena](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) do tutorial anterior para configurar o componente **Botão pressionável do HoloLens 2 (Script)** e o componente **Interagir (Script)** em cada um dos dois botões:

* Para o objeto **ShareAzureAnchorIdToNetwork**, atribua a função AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** .
* Para o objeto **GetAzureAnchorIdFromNetwork**, atribua a função AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** .

Se você criar o aplicativo atualizado para dois dispositivos HoloLens, agora poderá obter o alinhamento espacial entre eles compartilhando a ID de Âncora do Azure. Para testá-lo, você pode seguir estas etapas:

1. No dispositivo HoloLens 1: Mover a experiência do Rocket Launcher para a localização desejada.
2. No dispositivo HoloLens 1: Inicie a Sessão do Azure.
3. No dispositivo HoloLens 1: Criar a Âncora do Azure (cria âncoras na localização da experiência do Rocket Launcher).
4. No dispositivo HoloLens 1: Compartilhar a ID de Âncora do Azure para a rede.
5. No dispositivo HoloLens 2: Inicie o aplicativo.
6. No dispositivo HoloLens 2: Obtenha a ID de Âncora compartilhada da Rede (busca a ID de âncora que acaba de ser compartilhada do dispositivo HoloLens 1).
7. No dispositivo HoloLens 2: Inicie a Sessão do Azure.
8. No dispositivo HoloLens 2: Localize a Âncora do Azure (posiciona a experiência do Rocket Launcher na localização da etapa 3).

> [!TIP]
> Se você tiver apenas um HoloLens, ainda poderá testar a funcionalidade reiniciando o aplicativo, em vez de usar um segundo dispositivo HoloLens.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a manter as Âncoras Espaciais do Azure entre as sessões do aplicativo e reinicializações do aplicativo salvando a ID de Âncora Espacial do Azure no disco local no HoloLens. Você também aprendeu a compartilhar as Âncoras Espaciais do Azure entre vários dispositivos para uma experiência compartilhada básica com vários usuários e com holograma estático.

No próximo tutorial, você aprenderá a fornecer aos usuários comentários em tempo real. Esses comentários incluirão informações sobre a criação de âncora, a qualidade da compreensão do ambiente e o estado da sessão do Azure. Sem comentários, os usuários podem não saber se uma âncora foi carregada com êxito no Azure, se a qualidade do ambiente é suficiente para a criação de âncora ou o estado atual.

[Próxima lição: 3. Exibir comentários da Âncora Espacial do Azure](mrlearning-asa-ch3.md)
