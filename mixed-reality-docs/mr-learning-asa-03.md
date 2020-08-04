---
title: Tutoriais de Âncoras Espaciais do Azure – 3. Salvar, recuperar e compartilhar Âncoras Espaciais do Azure
description: Conclua este curso para saber como implementar as Âncoras Espaciais do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 274722588f156cb01fdd45525912e2e15687bc2d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376528"
---
# <a name="3-saving-retrieving-and-sharing-azure-spatial-anchors"></a>3. Salvar, recuperar e compartilhar Âncoras Espaciais do Azure

Neste tutorial, você aprenderá a salvar Âncoras Espaciais do Azure em várias sessões de aplicativo salvando a ID de âncora no armazenamento do HoloLens 2. Você também aprenderá a compartilhar essa ID de âncora para outros dispositivos para um alinhamento de âncora de vários dispositivos.

## <a name="objectives"></a>Objetivos

* Saber como obter o alinhamento espacial entre várias sessões de aplicativo.
* Saber como obter um alinhamento espacial entre vários dispositivos.

## <a name="preparing-the-scene"></a>Preparando a cena

Na janela Hierarquia, expanda o objeto **ButtonParent**. Selecione o **últimos quatro objetos de botão filho**. Na janela Inspetor, **marque** caixa de seleção ao lado do campo de nome para ativar todos os objetos.

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-1.png)

Na janela Hierarquia, selecione o objeto **ButtonParent**. Em seguida, na janela Inspetor, localize o componente **GridObjectCollection** e clique no botão **Atualizar Coleção** para atualizar a posição de todos os objetos filho do objeto **ButtonParent**.

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-2.png)

## <a name="persisting-azure-spatial-anchors-between-app-sessions"></a>Persistir Âncoras Espaciais do Azure entre sessões do aplicativo

Nesta seção, você aprenderá a salvar e recuperar a ID de Âncora do Azure de e para o disco local do HoloLens. Isso permitirá que você consulte a mesma ID de âncora no Azure entre diferentes sessões do aplicativo. Assim os hologramas ancorados serão posicionados no mesmo local que na sessão anterior do aplicativo.

Na janela Hierarquia, expanda o objeto **ButtonParent** e localize os dois botões chamados **SaveAzureAnchorIdToDisk** e **GetAzureAnchorIdFromDisk**:

![mr-learning-asa](images/mr-learning-asa/asa-03-section2-step1-1.png)

Siga as mesmas etapas apresentadas nas instruções para [configurar os botões para operar a cena](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) do tutorial anterior para configurar o componente **Interagir (Script)** em cada um dos dois botões:

* Para o objeto de botão **SaveAzureAnchorIdToDisk**, atribua a função AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** .
* Para o objeto de botão **GetAzureAnchorIdFromDisk**, atribua a função AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** .

Se você compilar o aplicativo atualizado para o HoloLens, agora poderá persistir as Âncoras Espaciais do Azure entre as sessões do aplicativo, salvando a ID da Âncora do Azure. Para testá-lo, você pode seguir estas etapas:

1. Mova o Rover Explorer para o local desejado
2. Inicie a Sessão do Azure
3. Crie a Âncora do Azure (cria âncoras na localização do Rover Explorer)
4. Salve a ID de Âncora do Azure no disco
5. Reinicie o aplicativo
6. Obtenha a Âncora do Azure do Disco (carrega a ID de âncora que você acabou de salvar)
7. Inicie a Sessão do Azure
8. Localize a Âncora do Azure (posiciona o Rover Explorer na localização da etapa 3)

> [!NOTE]
> Para reiniciar completamente o aplicativo, depois de sair do modo de exibição imersivo do aplicativo, a janela do aplicativo na página inicial de realidade misturada precisará ser fechada antes de reiniciar o aplicativo no menu Iniciar. Para obter detalhes adicionais, você pode consultar a documentação [Como usar aplicativos no HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens).

## <a name="sharing-azure-spatial-anchors-between-devices"></a>Compartilhar Âncoras Espaciais do Azure entre dispositivos

Nesta seção, você aprenderá a compartilhar a ID de Âncora do Azure entre vários dispositivos. Isso permitirá que vários dispositivos consultem o Azure para a mesma ID de âncora, permitindo o alinhamento espacial dos hologramas ancorados. O alinhamento espacial, ou seja, ver os mesmos hologramas na mesma localização física entre vários dispositivos, é o segredo para experiências compartilhadas locais no HoloLens 2.

Há várias maneiras de transferir IDs de Âncora do Azure entre dispositivos, incluindo métodos descritos na série de [Tutoriais de funcionalidades de vários usuários](mr-learning-sharing-02.md). Neste exemplo, você usará um serviço Web simples para carregar e baixar IDs de âncora entre dispositivos.

Na janela Hierarquia, expanda o objeto **ButtonParent**.   Localize os dois botões chamados **ShareAzureAnchorIdToNetwork** e **GetAzureAnchorIdFromNetwork**:

![mr-learning-asa](images/mr-learning-asa/asa-03-section3-step1-1.png)

Siga as mesmas etapas apresentadas nas instruções para [configurar os botões para operar a cena](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) do tutorial anterior para configurar o componente **Interagir (Script)** em cada um dos dois botões:

* Para o objeto **ShareAzureAnchorIdToNetwork**, atribua a função AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** .
* Para o objeto **GetAzureAnchorIdFromNetwork**, atribua a função AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** .

Se você compilar o aplicativo atualizado para dois dispositivos HoloLens, poderá obter o alinhamento espacial compartilhando a ID de Âncora do Azure. Para testá-lo, você pode seguir estas etapas:

1. No dispositivo HoloLens 1: Mova o Rover Explorer para o local desejado.
2. No dispositivo HoloLens 1: Inicie a Sessão do Azure.
3. No dispositivo HoloLens 1: Crie a Âncora do Azure (cria âncoras na localização do Rover Explorer).
4. No dispositivo HoloLens 1: Compartilhar a ID de Âncora do Azure para a rede.
5. No dispositivo HoloLens 2: Inicie o aplicativo.
6. No dispositivo HoloLens 2: Obtenha a ID de Âncora compartilhada da Rede (busca a ID de âncora que acaba de ser compartilhada do dispositivo HoloLens 1).
7. No dispositivo HoloLens 2: Inicie a Sessão do Azure.
8. No dispositivo HoloLens 2: Localize a Âncora do Azure (posiciona o Rover Explorer na localização da etapa 3).

> [!TIP]
> Se você tiver apenas um HoloLens, ainda poderá testar a funcionalidade reiniciando o aplicativo, em vez de usar um segundo dispositivo HoloLens.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a manter as Âncoras Espaciais do Azure entre as sessões do aplicativo e reinicializações do aplicativo salvando a ID de Âncora Espacial do Azure no disco local no HoloLens. Você também aprendeu a compartilhar as Âncoras Espaciais do Azure entre vários dispositivos para uma experiência compartilhada básica com vários usuários e com holograma estático.

No próximo tutorial, você aprenderá a fornecer aos usuários comentários em tempo real. Esses comentários incluirão informações sobre a criação da âncora, a qualidade da compreensão do ambiente e o estado da sessão do Azure. Sem comentários, os usuários podem não saber se uma âncora foi carregada com êxito no Azure, se a qualidade do ambiente é suficiente para a criação de âncora ou o estado atual.

[Próximo tutorial: 4. Exibir comentários da Âncora Espacial do Azure](mr-learning-asa-04.md)
