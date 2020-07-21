---
title: Tutoriais de Nuvem do Azure – 3. Integrar a Visão Personalizada do Azure
description: Conclua este curso para aprender a implementar a Visão Personalizada do Azure em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, hololens 2, visão personalizada do azure, serviços cognitivos do azure
ms.localizationpriority: high
ms.openlocfilehash: c3ba5a715b0e77d7869d598a472341cd390c2d23
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303965"
---
# <a name="3-integrating-azure-custom-vision"></a>3. Integrar a Visão Personalizada do Azure

Neste tutorial, você aprenderá a usar a **Visão Personalizada do Azure**. Você carregará um conjunto de fotos para associá-lo a um *Objeto Rastreado*, carregá-lo no serviço de **Visão Personalizada** e iniciar o processo de treinamento. Em seguida, você usará o serviço para detectar o *Objeto Rastreado* capturando fotos do feed da webcam.

## <a name="objectives"></a>Objetivos

* Aprender os conceitos básicos sobre a Visão Personalizada do Azure
* Saber como configurar a cena para usar a Visão Personalizada neste projeto
* Saber como integrar o upload, treinar e detectar imagens

## <a name="understanding-azure-custom-vision"></a>Compreender a Visão Personalizada do Azure

A **Visão Personalizada do Azure** faz parte da família de **Serviços Cognitivos** e é usada para treinar classificadores de imagem. O classificador de imagens é um serviço de IA que usa o modelo treinado para aplicar marcas correspondentes. Esse recurso de classificação será usado pelo nosso aplicativo para detectar *Objetos Rastreados*.

Saiba mais sobre a [Visão Personalizada do Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).

## <a name="preparing-azure-custom-vision"></a>Como preparar a Visão Personalizada do Azure

Para começar, crie um projeto de visão personalizada. A maneira mais rápida é usando o portal da Web.

Siga este [tutorial de início rápido](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) para configurar a sua conta e o projeto até a seção *Carregar e marcar imagens*.

> [!WARNING]
> Para treinar um modelo, você precisa ter pelo menos duas marcas e cinco imagens por marca. Para usar esse aplicativo, você deve criar pelo menos uma marca com cinco imagens, para que o processo de treinamento não falhe posteriormente.

## <a name="preparing-the-scene"></a>Preparando a cena

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureCloudServices** > **Pré-fabricados** > **Gerenciador**.

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-1.png)

Em seguida, arraste o pré-fabricado **ObjectDetectionManager** para a Hierarquia de cena.

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-2.png)

Na janela Hierarquia, localize o objeto **ObjectDetectionManager** e selecione-o.
O pré-fabricado **ObjectDetectionManager** contém o componente **ObjectDetectionManager (script)** e, como você pode ver na janela Inspetor, ele depende de várias configurações.

## <a name="retrieving-azure-api-resource-credentials"></a>Como recuperar credenciais de recurso da API do Azure

As credenciais necessárias para as configurações **ObjectDetectionManager (script)** podem ser recuperadas no Portal do Azure e no portal da visão personalizada.

### <a name="azure-portal"></a>Portal do Azure

Localize o recurso de visão personalizada do tipo **Serviços Cognitivos** que você criou na seção *Preparar a cena* deste tutorial. Em seguida, clique em *Chaves e Ponto de Extremidade* para recuperar as credenciais necessárias.

### <a name="custom-vision-dashboard"></a>Painel da Visão Personalizada

No painel da [visão personalizada](https://www.customvision.ai/projects), abra o projeto que você criou para este tutorial e clique no canto superior direito da página no ícone de engrenagem para abrir a página de configurações. Aqui, na seção *Recursos* à direita, você encontrará as credenciais necessárias.

Agora, com o **ObjectDetectionManager (script)** configurado corretamente, localize o objeto **SceneController** na sua Hierarquia de cena e selecione-o.

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-3.png)

Veja se o campo *Gerenciador de Detecção de Objetos* no componente **SceneController** está vazio, arraste o **ObjectDetectionManager** da Hierarquia para esse campo e salve a cena.

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a>Criar e carregar imagens

Execute a cena, clique em **Definir Objeto** e digite o nome de um dos **Objetos Rastreados** que você criou na [lição anterior](mr-learning-azure-02.md). Agora, clique no botão **Pesquisa Visual Computacional** que está na parte inferior do **Cartão do Objeto**.

Uma nova janela será aberta, na qual você precisará tirar seis fotos para treinar o modelo de reconhecimento de imagem. Clique no botão **Câmera** e execute um AirTap ao examinar o objeto que você deseja rastrear. Faça isso seis vezes.

> [!TIP]
> Para melhorar o treinamento do modelo, tente usar cada imagem de diferentes ângulos e condições de iluminação.

Quando tiver imagens suficientes, clique no botão **Treinar** para iniciar o processo de treinamento de modelo na nuvem. A ativação do treinamento carregará todas as imagens e, em seguida, iniciará o treinamento. Isso pode levar até um minuto ou mais. Uma mensagem no menu indica o progresso atual e, quando ela indicar a conclusão, você poderá interromper o aplicativo

> [!TIP]
> O **ObjectDetectionManager (script)** carrega diretamente as imagens feitas no serviço de Visão Personalizada. Como alternativa, a API da visão personalizada aceita URLs para as imagens. Como um exercício, você pode modificar o **ObjectDetectionManager (script)** para carregar as imagens para um Armazenamento de blobs.

## <a name="detect-objects"></a>Detectar objetos

Agora você pode testar o modelo treinado, executar o aplicativo e, no *menu principal* clicar em **Pesquisar Objeto** e digitar o nome do **Objeto Rastreado** em questão. O **Cartão de Objeto** aparecerá; clique no botão **Visão Personalizada**. A partir daqui, o **ObjectDetectionManager** começará a fazer capturas de imagem em segundo plano da câmera e o progresso será indicado no menu. Aponte a câmera para o objeto usado para treinar o modelo e você verá que, após um curto período, ele detectará o objeto.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu como a Visão Personalizada do Azure pode ser usada para treinar imagens e usar o serviço de classificação para detectar imagens que correspondem ao **Objeto Rastreado** associado.

No próximo tutorial, você aprenderá a usar as Âncoras Espaciais do Azure para vincular um *Objeto Rastreado* a uma localização no mundo físico e como exibir uma seta que orientará o usuário para a localização vinculada do Objeto Rastreado.

[Próximo tutorial: 4. Integrar as Âncoras Espaciais do Azure](mr-learning-azure-04.md)
