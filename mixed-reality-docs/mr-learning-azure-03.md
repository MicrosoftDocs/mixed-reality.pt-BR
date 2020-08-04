---
title: Tutoriais de Nuvem do Azure – 3. Integrar a Visão Personalizada do Azure
description: Conclua este curso para aprender a implementar a Visão Personalizada do Azure em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, hololens 2, visão personalizada do azure, serviços cognitivos do azure
ms.localizationpriority: high
ms.openlocfilehash: 0fc3793315dd05f91a6193b68343205f53a3092a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376458"
---
# <a name="3-integrating-azure-custom-vision"></a><span data-ttu-id="0cb72-105">3. Integrar a Visão Personalizada do Azure</span><span class="sxs-lookup"><span data-stu-id="0cb72-105">3. Integrating Azure Custom Vision</span></span>

<span data-ttu-id="0cb72-106">Neste tutorial, você aprenderá a usar a **Visão Personalizada do Azure**. Você carregará um conjunto de fotos para associá-lo a um *Objeto Rastreado*, carregá-lo no serviço de **Visão Personalizada** e iniciar o processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="0cb72-106">In this tutorial, you will learn how to use **Azure Custom Vision**.You will upload a set of photos to associate it with a *Tracked Object*, upload them to the **Custom Vision** service and start the training process.</span></span> <span data-ttu-id="0cb72-107">Em seguida, você usará o serviço para detectar o *Objeto Rastreado* capturando fotos do feed da webcam.</span><span class="sxs-lookup"><span data-stu-id="0cb72-107">Then you will use the service to detect the *Tracked Object* by capturing photos from the webcam feed.</span></span>

## <a name="objectives"></a><span data-ttu-id="0cb72-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0cb72-108">Objectives</span></span>

* <span data-ttu-id="0cb72-109">Aprender os conceitos básicos sobre a Visão Personalizada do Azure</span><span class="sxs-lookup"><span data-stu-id="0cb72-109">Learn the basics about Azure Custom Vision</span></span>
* <span data-ttu-id="0cb72-110">Saber como configurar a cena para usar a Visão Personalizada neste projeto</span><span class="sxs-lookup"><span data-stu-id="0cb72-110">Learn how to setup the scene to use Custom Vision in this project</span></span>
* <span data-ttu-id="0cb72-111">Saber como integrar o upload, treinar e detectar imagens</span><span class="sxs-lookup"><span data-stu-id="0cb72-111">Learn how to integrate upload, train and detect images</span></span>

## <a name="understanding-azure-custom-vision"></a><span data-ttu-id="0cb72-112">Compreender a Visão Personalizada do Azure</span><span class="sxs-lookup"><span data-stu-id="0cb72-112">Understanding Azure Custom Vision</span></span>

<span data-ttu-id="0cb72-113">A **Visão Personalizada do Azure** faz parte da família de **Serviços Cognitivos** e é usada para treinar classificadores de imagem.</span><span class="sxs-lookup"><span data-stu-id="0cb72-113">**Azure Custom Vision** is part of the **Cognitive Services** family and is used to train image classifiers.</span></span> <span data-ttu-id="0cb72-114">O classificador de imagens é um serviço de IA que usa o modelo treinado para aplicar marcas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="0cb72-114">The image classifier is an AI service that uses the trained model to apply matching tags.</span></span> <span data-ttu-id="0cb72-115">Esse recurso de classificação será usado pelo nosso aplicativo para detectar *Objetos Rastreados*.</span><span class="sxs-lookup"><span data-stu-id="0cb72-115">This classification feature will be used by our application to detect *Tracked Objects*.</span></span>

<span data-ttu-id="0cb72-116">Saiba mais sobre a [Visão Personalizada do Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="0cb72-116">Learn more about [Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

## <a name="preparing-azure-custom-vision"></a><span data-ttu-id="0cb72-117">Como preparar a Visão Personalizada do Azure</span><span class="sxs-lookup"><span data-stu-id="0cb72-117">Preparing Azure Custom Vision</span></span>

<span data-ttu-id="0cb72-118">Para começar, crie um projeto de visão personalizada. A maneira mais rápida é usando o portal da Web.</span><span class="sxs-lookup"><span data-stu-id="0cb72-118">Before you can start, you have to create a custom vision project, the fastest way is by using the web portal.</span></span>

<span data-ttu-id="0cb72-119">Siga este [tutorial de início rápido](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) para configurar a sua conta e o projeto até a seção *Carregar e marcar imagens*.</span><span class="sxs-lookup"><span data-stu-id="0cb72-119">Follow this [quickstart tutorial](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) to setup your account and project until section *Upload and tag images*.</span></span>

> [!WARNING]
> <span data-ttu-id="0cb72-120">Para treinar um modelo, você precisa ter pelo menos duas marcas e cinco imagens por marca.</span><span class="sxs-lookup"><span data-stu-id="0cb72-120">To train a model you need to have at least 2 tags and 5 images per tag.</span></span> <span data-ttu-id="0cb72-121">Para usar esse aplicativo, você deve criar pelo menos uma marca com cinco imagens, para que o processo de treinamento não falhe posteriormente.</span><span class="sxs-lookup"><span data-stu-id="0cb72-121">To use this application you should at least create one tag with 5 images, so that the training process later won't fail.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="0cb72-122">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="0cb72-122">Preparing the scene</span></span>

<span data-ttu-id="0cb72-123">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureCloudServices** > **Pré-fabricados** > **Gerenciador**.</span><span class="sxs-lookup"><span data-stu-id="0cb72-123">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-1.png)

<span data-ttu-id="0cb72-125">Em seguida, arraste o pré-fabricado **ObjectDetectionManager** para a Hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="0cb72-125">From there drag the prefab **ObjectDetectionManager** into the scene Hierarchy.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-2.png)

<span data-ttu-id="0cb72-127">Na janela Hierarquia, localize o objeto **ObjectDetectionManager** e selecione-o.</span><span class="sxs-lookup"><span data-stu-id="0cb72-127">In the Hierarchy window locate the **ObjectDetectionManager** object and select it.</span></span>
<span data-ttu-id="0cb72-128">O pré-fabricado **ObjectDetectionManager** contém o componente **ObjectDetectionManager (script)** e, como você pode ver na janela Inspetor, ele depende de várias configurações.</span><span class="sxs-lookup"><span data-stu-id="0cb72-128">The **ObjectDetectionManager** prefab contains the **ObjectDetectionManager (script)** component and as you can see from the Inspector window it depends on several settings.</span></span>

## <a name="retrieving-azure-api-resource-credentials"></a><span data-ttu-id="0cb72-129">Como recuperar credenciais de recurso da API do Azure</span><span class="sxs-lookup"><span data-stu-id="0cb72-129">Retrieving Azure api resource credentials</span></span>

<span data-ttu-id="0cb72-130">As credenciais necessárias para as configurações **ObjectDetectionManager (script)** podem ser recuperadas no Portal do Azure e no portal da visão personalizada.</span><span class="sxs-lookup"><span data-stu-id="0cb72-130">The necessary credentials for the **ObjectDetectionManager (script)** settings can be retrieve from the Azure Portal and the custom vision portal.</span></span>

### <a name="azure-portal"></a><span data-ttu-id="0cb72-131">Portal do Azure</span><span class="sxs-lookup"><span data-stu-id="0cb72-131">Azure Portal</span></span>

<span data-ttu-id="0cb72-132">Localize o recurso de visão personalizada do tipo **Serviços Cognitivos** que você criou na seção *Preparar a cena* deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="0cb72-132">Find and locate the custom vision resource of type **Cognitive Services** you have created in the *Preparing the scene* section of this tutorial.</span></span> <span data-ttu-id="0cb72-133">Em seguida, clique em *Chaves e Ponto de Extremidade* para recuperar as credenciais necessárias.</span><span class="sxs-lookup"><span data-stu-id="0cb72-133">There click on *Keys and Endpoint* to retrieve the necessary credentials.</span></span>

### <a name="custom-vision-dashboard"></a><span data-ttu-id="0cb72-134">Painel da Visão Personalizada</span><span class="sxs-lookup"><span data-stu-id="0cb72-134">Custom Vision Dashboard</span></span>

<span data-ttu-id="0cb72-135">No painel da [visão personalizada](https://www.customvision.ai/projects), abra o projeto que você criou para este tutorial e clique no canto superior direito da página no ícone de engrenagem para abrir a página de configurações.</span><span class="sxs-lookup"><span data-stu-id="0cb72-135">In the [custom vision](https://www.customvision.ai/projects) dashboard, open the project you have created for this tutorial and click on the top right corner of the page on the gear icon to open the settings page.</span></span> <span data-ttu-id="0cb72-136">Aqui, na seção *Recursos* à direita, você encontrará as credenciais necessárias.</span><span class="sxs-lookup"><span data-stu-id="0cb72-136">Here on the right hand *Resources* section you will find the necessary credentials.</span></span>

<span data-ttu-id="0cb72-137">Agora, com o **ObjectDetectionManager (script)** configurado corretamente, localize o objeto **SceneController** na sua Hierarquia de cena e selecione-o.</span><span class="sxs-lookup"><span data-stu-id="0cb72-137">Now with the **ObjectDetectionManager (script)** setup correctly, find the **SceneController** object in your scene Hierarchy and select it.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-3.png)

<span data-ttu-id="0cb72-139">Veja se o campo *Gerenciador de Detecção de Objetos* no componente **SceneController** está vazio, arraste o **ObjectDetectionManager** da Hierarquia para esse campo e salve a cena.</span><span class="sxs-lookup"><span data-stu-id="0cb72-139">You see *Object Detection Manager* field in the **SceneController** component is empty, drag the **ObjectDetectionManager** from the Hierarchy into that field and save the scene.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a><span data-ttu-id="0cb72-141">Criar e carregar imagens</span><span class="sxs-lookup"><span data-stu-id="0cb72-141">Take and upload images</span></span>

<span data-ttu-id="0cb72-142">Execute a cena, clique em **Definir Objeto** e digite o nome de um dos **Objetos Rastreados** que você criou na [lição anterior](mr-learning-azure-02.md).</span><span class="sxs-lookup"><span data-stu-id="0cb72-142">Run the scene and click on **Set Object**, type in the name for one of the **Tracked Objects** you have created in the [previous lesson](mr-learning-azure-02.md).</span></span> <span data-ttu-id="0cb72-143">Agora, clique no botão **Pesquisa Visual Computacional** que está na parte inferior do **Cartão do Objeto**.</span><span class="sxs-lookup"><span data-stu-id="0cb72-143">Now click on **Computer Vision** button you can find at the bottom of the **Object Card**.</span></span>

<span data-ttu-id="0cb72-144">Uma nova janela será aberta, na qual você precisará tirar seis fotos para treinar o modelo de reconhecimento de imagem.</span><span class="sxs-lookup"><span data-stu-id="0cb72-144">A new window will open where you have to take six photos to train the model for image recognition.</span></span> <span data-ttu-id="0cb72-145">Clique no botão **Câmera** e execute um AirTap ao examinar o objeto que você deseja rastrear. Faça isso seis vezes.</span><span class="sxs-lookup"><span data-stu-id="0cb72-145">Click on the **Camera** button and perform an AirTap when you look on the object you like to track, do this six times.</span></span>

> [!TIP]
> <span data-ttu-id="0cb72-146">Para melhorar o treinamento do modelo, tente usar cada imagem de diferentes ângulos e condições de iluminação.</span><span class="sxs-lookup"><span data-stu-id="0cb72-146">To improve the model training try to take each image from different angles and lighting conditions.</span></span>

<span data-ttu-id="0cb72-147">Quando tiver imagens suficientes, clique no botão **Treinar** para iniciar o processo de treinamento de modelo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="0cb72-147">Once you have enough images click on the **Train** button to start the model training process in the cloud.</span></span> <span data-ttu-id="0cb72-148">A ativação do treinamento carregará todas as imagens e, em seguida, iniciará o treinamento. Isso pode levar até um minuto ou mais.</span><span class="sxs-lookup"><span data-stu-id="0cb72-148">Activating the training will upload all images and then start the training, this can take up to a minute or more.</span></span> <span data-ttu-id="0cb72-149">Uma mensagem no menu indica o progresso atual e, quando ela indicar a conclusão, você poderá interromper o aplicativo</span><span class="sxs-lookup"><span data-stu-id="0cb72-149">A message inside the menu indicates the current progress and once it indicates the completion you can stop the application</span></span>

> [!TIP]
> <span data-ttu-id="0cb72-150">O **ObjectDetectionManager (script)** carrega diretamente as imagens feitas no serviço de Visão Personalizada.</span><span class="sxs-lookup"><span data-stu-id="0cb72-150">The **ObjectDetectionManager (script)** directly uploads taken images into the Custom Vision service.</span></span> <span data-ttu-id="0cb72-151">Como alternativa, a API da visão personalizada aceita URLs para as imagens. Como um exercício, você pode modificar o **ObjectDetectionManager (script)** para carregar as imagens para um Armazenamento de blobs.</span><span class="sxs-lookup"><span data-stu-id="0cb72-151">As an alternative the custom vision API accepts URLs to the images, as an exercise you can modify the **ObjectDetectionManager (script)** to upload the images to a Blob storage instead.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="0cb72-152">Detectar objetos</span><span class="sxs-lookup"><span data-stu-id="0cb72-152">Detect objects</span></span>

<span data-ttu-id="0cb72-153">Agora você pode testar o modelo treinado, executar o aplicativo e, no *menu principal* clicar em **Pesquisar Objeto** e digitar o nome do **Objeto Rastreado** em questão.</span><span class="sxs-lookup"><span data-stu-id="0cb72-153">You can now put the trained model to the test, run the application and from the *main menu* click on **Search Object** and type the name of the **Tracked Object** in question.</span></span> <span data-ttu-id="0cb72-154">O **Cartão de Objeto** aparecerá; clique no botão **Visão Personalizada**.</span><span class="sxs-lookup"><span data-stu-id="0cb72-154">The **Object Card** will appear and click on the **Custom Vision** button.</span></span> <span data-ttu-id="0cb72-155">A partir daqui, o **ObjectDetectionManager** começará a fazer capturas de imagem em segundo plano da câmera e o progresso será indicado no menu.</span><span class="sxs-lookup"><span data-stu-id="0cb72-155">From here the **ObjectDetectionManager** will start taking image captures in the background from the camera and the progress will be indicated on the menu.</span></span> <span data-ttu-id="0cb72-156">Aponte a câmera para o objeto usado para treinar o modelo e você verá que, após um curto período, ele detectará o objeto.</span><span class="sxs-lookup"><span data-stu-id="0cb72-156">Point the camera to the object you used to train the model and you will see that after a short while it will detect the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="0cb72-157">Parabéns</span><span class="sxs-lookup"><span data-stu-id="0cb72-157">Congratulations</span></span>

<span data-ttu-id="0cb72-158">Neste tutorial, você aprendeu como a Visão Personalizada do Azure pode ser usada para treinar imagens e usar o serviço de classificação para detectar imagens que correspondem ao **Objeto Rastreado** associado.</span><span class="sxs-lookup"><span data-stu-id="0cb72-158">In this tutorial you learned how Azure Custom Vision can be used to train images and use the classification service to detect images that match the associated **Tracked Object**.</span></span>

<span data-ttu-id="0cb72-159">No próximo tutorial, você aprenderá a usar as Âncoras Espaciais do Azure para vincular um *Objeto Rastreado* a uma localização no mundo físico e como exibir uma seta que orientará o usuário para a localização vinculada do Objeto Rastreado.</span><span class="sxs-lookup"><span data-stu-id="0cb72-159">In the next tutorial you will learn how to use Azure Spatial Anchors to link a *Tracked Object* with a location in the physical world and how to display an arrow that will guide the user back to the Tracked Object's linked location.</span></span>

[<span data-ttu-id="0cb72-160">Próximo tutorial: 4. Integrar as Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="0cb72-160">Next tutorial: 4. Integrating Azure Spatial Anchors</span></span>](mr-learning-azure-04.md)
