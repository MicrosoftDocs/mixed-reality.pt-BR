---
title: Sr e Azure 307-aprendizado de máquina
description: Conclua este curso para aprender a implementar Azure Machine Learning Studio em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, Machine Learning, ml, estúdio de Machine Learning, hololens, imersão, VR
ms.openlocfilehash: c86c592573dd39d926869d8cce6025fa264cc90f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437927"
---
>[!NOTE]
><span data-ttu-id="79566-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="79566-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="79566-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="79566-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="79566-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="79566-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="79566-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="79566-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="79566-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="79566-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="79566-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="79566-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="79566-110">Sr e Azure 307: aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="79566-110">MR and Azure 307: Machine learning</span></span>

![início do produto final](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="79566-112">Neste curso, você aprenderá a adicionar recursos de Machine Learning (ML) a um aplicativo de realidade misturada usando Azure Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="79566-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="79566-113">*Azure Machine Learning Studio* é um serviço da Microsoft, que fornece aos desenvolvedores um grande número de algoritmos de aprendizado de máquina, que podem ajudar com a entrada, a saída, a preparação e a visualização de dados.</span><span class="sxs-lookup"><span data-stu-id="79566-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="79566-114">A partir desses componentes, é possível desenvolver um experimento de análise preditiva, iterar sobre ele e usá-lo para treinar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="79566-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="79566-115">Após o treinamento, você pode tornar seu modelo operacional na nuvem do Azure, para que ele possa pontuar novos dados.</span><span class="sxs-lookup"><span data-stu-id="79566-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="79566-116">Para obter mais informações, visite a [página Azure Machine Learning Studio](https://azure.microsoft.com/services/machine-learning-studio/).</span><span class="sxs-lookup"><span data-stu-id="79566-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/services/machine-learning-studio/).</span></span>

<span data-ttu-id="79566-117">Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada e aprenderá como fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="79566-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="79566-118">Forneça uma tabela de dados de vendas para o portal de *Azure Machine Learning Studio* e crie um algoritmo para prever as vendas futuras de itens populares.</span><span class="sxs-lookup"><span data-stu-id="79566-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="79566-119">Crie um **projeto do Unity**, que pode receber e interpretar dados de previsão do serviço ml.</span><span class="sxs-lookup"><span data-stu-id="79566-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="79566-120">Exiba os dados do predicação visualmente no **projeto do Unity**, por meio do fornecimento dos itens de vendas mais populares, em uma prateleira.</span><span class="sxs-lookup"><span data-stu-id="79566-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="79566-121">Em seu aplicativo, cabe a você como você integrará os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="79566-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="79566-122">Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="79566-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="79566-123">É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="79566-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="79566-124">Este curso é um tutorial independente, que não envolve diretamente nenhum outro laboratório de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="79566-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="79566-125">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="79566-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="79566-126">Course</span><span class="sxs-lookup"><span data-stu-id="79566-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="79566-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="79566-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="79566-128"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="79566-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="79566-129">Sr e Azure 307: aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="79566-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="79566-130">✔️</span><span class="sxs-lookup"><span data-stu-id="79566-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="79566-131">✔️</span><span class="sxs-lookup"><span data-stu-id="79566-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="79566-132">Embora este curso se concentre principalmente em fones de ouvido (VR) de realidade mista do Windows, você também pode aplicar o que aprende neste curso ao Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79566-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="79566-133">Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79566-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="79566-134">Ao usar o HoloLens, você pode notar um eco durante a captura de voz.</span><span class="sxs-lookup"><span data-stu-id="79566-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79566-135">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="79566-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="79566-136">Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o.</span><span class="sxs-lookup"><span data-stu-id="79566-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="79566-137">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="79566-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="79566-138">Você está livre para usar o software mais recente, conforme listado no [artigo instalar as ferramentas](install-the-tools.md), embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="79566-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="79566-139">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="79566-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="79566-140">Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)</span><span class="sxs-lookup"><span data-stu-id="79566-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="79566-141">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="79566-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="79566-142">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="79566-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="79566-143">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="79566-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="79566-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="79566-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="79566-145">Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="79566-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="79566-146">Acesso à Internet para a instalação do Azure e recuperação de dados de ML</span><span class="sxs-lookup"><span data-stu-id="79566-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="79566-147">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="79566-147">Before you start</span></span>

<span data-ttu-id="79566-148">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="79566-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="79566-149">Capítulo 1-configuração da conta de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="79566-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="79566-150">Para usar a API do Azure Translator, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79566-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="79566-151">Faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="79566-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="79566-152">Se você ainda não tiver uma conta do Azure, será necessário criar uma.</span><span class="sxs-lookup"><span data-stu-id="79566-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="79566-153">Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="79566-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="79566-154">Depois de fazer logon, clique em **contas de armazenamento** no menu à esquerda.</span><span class="sxs-lookup"><span data-stu-id="79566-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="79566-156">A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="79566-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="79566-157">Na guia **contas de armazenamento** , clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="79566-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="79566-159">No painel **criar conta de armazenamento** :</span><span class="sxs-lookup"><span data-stu-id="79566-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="79566-160">Insira um **nome** para sua conta, lembre-se de que esse campo aceita apenas números e letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="79566-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="79566-161">Para **modelo de implantação,** selecione **Gerenciador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="79566-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="79566-162">Para **tipo de conta**, selecione **armazenamento (uso geral v1)** .</span><span class="sxs-lookup"><span data-stu-id="79566-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="79566-163">Para **desempenho**, selecione **padrão**.</span><span class="sxs-lookup"><span data-stu-id="79566-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="79566-164">Para **replicação** **, selecione leitura-acesso-armazenamento com REDUNDÂNCIA geográfica (ra-grs)** .</span><span class="sxs-lookup"><span data-stu-id="79566-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="79566-165">Deixe a **transferência segura necessária** como **desabilitada**.</span><span class="sxs-lookup"><span data-stu-id="79566-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="79566-166">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="79566-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="79566-167">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="79566-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="79566-168">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="79566-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="79566-169">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="79566-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="79566-170">Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="79566-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="79566-171">Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="79566-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="79566-172">O local ideal seria na região em que o aplicativo seria executado.</span><span class="sxs-lookup"><span data-stu-id="79566-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="79566-173">Alguns ativos do Azure só estão disponíveis em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="79566-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="79566-174">Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="79566-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="79566-176">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="79566-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="79566-177">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="79566-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="79566-179">Capítulo 2-o Azure Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="79566-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="79566-180">Para usar o *Azure Machine Learning*, você precisará configurar uma instância do serviço de Machine Learning a ser disponibilizada para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79566-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="79566-181">No portal do Azure, clique em **novo** no canto superior esquerdo e procure **Machine Learning Studio espaço de trabalho**, pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="79566-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="79566-183">A nova página fornecerá uma descrição do serviço de **espaço de trabalho Machine Learning Studio** .</span><span class="sxs-lookup"><span data-stu-id="79566-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="79566-184">Na parte inferior esquerda desse prompt, clique no botão **criar** para criar uma associação com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="79566-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="79566-185">Depois de clicar em **criar**, um painel será exibido onde você precisa fornecer alguns detalhes sobre o novo serviço de **Machine Learning Studio**:</span><span class="sxs-lookup"><span data-stu-id="79566-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="79566-186">Insira o **nome do espaço de trabalho** desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="79566-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="79566-187">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="79566-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="79566-188">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="79566-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="79566-189">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="79566-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="79566-190">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="79566-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="79566-191">Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="79566-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="79566-192">Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="79566-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="79566-193">O local ideal seria na região em que o aplicativo seria executado.</span><span class="sxs-lookup"><span data-stu-id="79566-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="79566-194">Alguns ativos do Azure só estão disponíveis em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="79566-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="79566-195">Você deve usar o mesmo grupo de recursos que usou para criar o armazenamento do Azure no capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="79566-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="79566-196">Para a seção **conta de armazenamento** , clique em **usar existente**e, em seguida, clique no menu suspenso e, a partir daí, clique na **conta de armazenamento** que você criou no último capítulo.</span><span class="sxs-lookup"><span data-stu-id="79566-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="79566-197">Selecione o **tipo de preço do espaço de trabalho** apropriado para você, no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="79566-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="79566-198">Na seção **plano de serviço Web** , clique em **criar** **novo e** Insira um nome para ele no campo de texto.</span><span class="sxs-lookup"><span data-stu-id="79566-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="79566-199">Na seção tipo de preço do **plano de serviço Web** , selecione o tipo de preço de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="79566-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="79566-200">Um nível de teste de desenvolvimento chamado **DEVTEST Standard** deve estar disponível para você sem custos.</span><span class="sxs-lookup"><span data-stu-id="79566-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="79566-201">Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="79566-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="79566-202">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="79566-202">Click **Create**.</span></span>

        ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="79566-204">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="79566-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="79566-205">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="79566-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="79566-207">Clique na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="79566-207">Click on the notification to explore your new Service instance.</span></span>

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="79566-209">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="79566-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="79566-210">Na página exibida, na seção **links adicionais** , clique em **Iniciar Machine Learning Studio**, que direcionará o navegador para o portal do **Machine Learning Studio** .</span><span class="sxs-lookup"><span data-stu-id="79566-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="79566-212">Use o botão **entrar** , na parte superior direita ou no centro, para fazer logon em seu Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="79566-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="79566-214">Capítulo 3-a configuração do Machine Learning Studio: DataSet</span><span class="sxs-lookup"><span data-stu-id="79566-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="79566-215">Uma das maneiras de Machine Learning algoritmos funciona ao analisar os dados existentes e, em seguida, tentar prever os resultados futuros com base no conjunto de dados existente.</span><span class="sxs-lookup"><span data-stu-id="79566-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="79566-216">Isso geralmente significa que quanto mais dados existentes você tiver, melhor será o algoritmo prevendo resultados futuros.</span><span class="sxs-lookup"><span data-stu-id="79566-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="79566-217">Uma tabela de exemplo é fornecida para você, para este curso, chamado [ProductsTableCSV e pode ser baixado aqui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span><span class="sxs-lookup"><span data-stu-id="79566-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79566-218">O arquivo. zip acima contém o **ProductsTableCSV** e o **. unitypackage**, que serão necessários no [capítulo 6](#chapter-6---importing-the-mlproducts-unity-package).</span><span class="sxs-lookup"><span data-stu-id="79566-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="79566-219">Esse pacote também é fornecido dentro desse capítulo, embora separado para o arquivo CSV.</span><span class="sxs-lookup"><span data-stu-id="79566-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="79566-220">Este conjunto de dados de exemplo contém um registro dos objetos mais vendidos a cada hora de cada dia do ano de 2017.</span><span class="sxs-lookup"><span data-stu-id="79566-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![A configuração do Machine Learning Studio: DataSet](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="79566-222">Por exemplo, no dia 1 de 2017, às às 13:00 (hora 13), o item de vendas melhores era Salt e molho.</span><span class="sxs-lookup"><span data-stu-id="79566-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="79566-223">Esta tabela de exemplo contém 9998 entradas.</span><span class="sxs-lookup"><span data-stu-id="79566-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="79566-224">Volte para o portal de **Machine Learning Studio** e adicione essa tabela como um **conjunto** de uma para seu ml.</span><span class="sxs-lookup"><span data-stu-id="79566-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="79566-225">Para fazer isso, clique no botão **+ novo** no canto inferior esquerdo da tela.</span><span class="sxs-lookup"><span data-stu-id="79566-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![A configuração do Machine Learning Studio: DataSet](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="79566-227">Uma seção será exibida na parte inferior e, dentro dela, há painel de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="79566-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="79566-228">Clique em **conjunto**de um e, à direita disso, em **arquivo local**.</span><span class="sxs-lookup"><span data-stu-id="79566-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![A configuração do Machine Learning Studio: DataSet](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="79566-230">Carregue o novo **conjunto** de novos, seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="79566-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="79566-231">A janela de carregamento será exibida, onde você poderá **procurar** o novo conjunto de um disco rígido.</span><span class="sxs-lookup"><span data-stu-id="79566-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![A configuração do Machine Learning Studio: DataSet](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="79566-233">Depois de selecionado e de volta à janela carregar, deixe a caixa de seleção sem marcação.</span><span class="sxs-lookup"><span data-stu-id="79566-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="79566-234">No campo de texto abaixo, insira **ProductsTableCSV. csv** como o nome do conjunto de os (embora deva ser adicionado automaticamente).</span><span class="sxs-lookup"><span data-stu-id="79566-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="79566-235">Usando o menu suspenso para **tipo**, selecione **arquivo CSV genérico com um cabeçalho (. csv)** .</span><span class="sxs-lookup"><span data-stu-id="79566-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="79566-236">Pressione a escala no canto inferior direito da janela carregar e seu **conjunto** de resultados será carregado.</span><span class="sxs-lookup"><span data-stu-id="79566-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="79566-237">Capítulo 4-o Machine Learning Studio: o experimento</span><span class="sxs-lookup"><span data-stu-id="79566-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="79566-238">Antes de criar seu sistema de aprendizado de máquina, você precisará criar um experimento para validar sua teoria sobre seus dados.</span><span class="sxs-lookup"><span data-stu-id="79566-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="79566-239">Com os resultados, você saberá se precisa de mais dados ou se não há nenhuma correlação entre os dados e um resultado possível.</span><span class="sxs-lookup"><span data-stu-id="79566-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="79566-240">Para começar a criar um experimento:</span><span class="sxs-lookup"><span data-stu-id="79566-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="79566-241">Clique novamente no botão **+ novo** na parte inferior esquerda da página e **, em seguida** , clique em experimento > **experimento em branco**.</span><span class="sxs-lookup"><span data-stu-id="79566-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="79566-243">Uma nova página será exibida com um experimento em branco:</span><span class="sxs-lookup"><span data-stu-id="79566-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="79566-244">No painel à esquerda, expanda os **conjuntos** de itens salvos > **meus conjuntos** de os e arraste o **ProductsTableCSV** para a **tela do experimento**.</span><span class="sxs-lookup"><span data-stu-id="79566-244">From the panel on the left expand **Saved Datasets** > **My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="79566-246">No painel à esquerda, expanda **transformação de dados** > **amostra e divisão**.</span><span class="sxs-lookup"><span data-stu-id="79566-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="79566-247">Em seguida, arraste o item **dividir dados** para a **tela do experimento**.</span><span class="sxs-lookup"><span data-stu-id="79566-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="79566-248">O item dividir dados dividirá o conjunto de dados em duas partes.</span><span class="sxs-lookup"><span data-stu-id="79566-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="79566-249">Uma parte que será usada para treinar o algoritmo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="79566-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="79566-250">A segunda parte será usada para avaliar a precisão do algoritmo gerado.</span><span class="sxs-lookup"><span data-stu-id="79566-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="79566-252">No painel direito (enquanto o item dividir dados na tela está selecionado), edite a **fração de linhas no primeiro conjunto** de dado de saída para **0,7**.</span><span class="sxs-lookup"><span data-stu-id="79566-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="79566-253">Isso dividirá os dados em duas partes, a primeira parte será de 70% dos dados e a segunda parte será os 30% restantes.</span><span class="sxs-lookup"><span data-stu-id="79566-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="79566-254">Para garantir que os dados sejam divididos aleatoriamente, verifique se a caixa de seleção **divisão aleatória** permanece marcada.</span><span class="sxs-lookup"><span data-stu-id="79566-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="79566-256">Arraste uma conexão da base do item **ProductsTableCSV** na tela para a parte superior do item dividir dados.</span><span class="sxs-lookup"><span data-stu-id="79566-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="79566-257">Isso irá conectar os itens e enviar a saída do conjunto de dados **ProductsTableCSV** (os dados) para a entrada Split Data.</span><span class="sxs-lookup"><span data-stu-id="79566-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="79566-259">No painel **experimentos** no lado esquerdo, expanda **Machine Learning** > **Train**.</span><span class="sxs-lookup"><span data-stu-id="79566-259">In the **Experiments** panel on the left side, expand **Machine Learning** > **Train**.</span></span> <span data-ttu-id="79566-260">Arraste o item **modelo de treinamento** para fora até a tela do experimento.</span><span class="sxs-lookup"><span data-stu-id="79566-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="79566-261">Sua tela deve ter a seguinte aparência.</span><span class="sxs-lookup"><span data-stu-id="79566-261">Your canvas should look the same as the below.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="79566-263">Na ***parte inferior esquerda*** do item **dividir dados** , arraste uma conexão para a **parte superior direita** do item de **modelo de treinamento** .</span><span class="sxs-lookup"><span data-stu-id="79566-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="79566-264">A primeira 70% de divisão do conjunto de um será usada pelo modelo de treinamento para treinar o algoritmo.</span><span class="sxs-lookup"><span data-stu-id="79566-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="79566-266">Selecione o item **treinar modelo** na tela e, no painel **Propriedades** (no lado direito da janela do navegador), clique no botão **Iniciar seletor de coluna** .</span><span class="sxs-lookup"><span data-stu-id="79566-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="79566-267">Na caixa de texto, digite **produto** e pressione **Enter**, o *produto* será definido como uma coluna para treinar previsões.</span><span class="sxs-lookup"><span data-stu-id="79566-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="79566-268">Depois disso, clique no **tique** no canto inferior direito para fechar a caixa de diálogo de seleção.</span><span class="sxs-lookup"><span data-stu-id="79566-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="79566-270">Você vai treinar um algoritmo de **regressão logística multiclasse** para prever o **produto** mais vendido com base na hora do dia e na data.</span><span class="sxs-lookup"><span data-stu-id="79566-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="79566-271">Está além do escopo deste documento para explicar os detalhes dos diferentes algoritmos fornecidos pelo Azure Machine Learning Studio, porém, você pode saber mais sobre a folha de consulta do [algoritmo de Machine Learning](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="79566-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="79566-272">No painel itens de experimento à esquerda, expanda **Machine Learning** > **inicializar o modelo** > **classificação**e arraste o item **regressão logística multiclasse** para a tela do experimento.</span><span class="sxs-lookup"><span data-stu-id="79566-272">From the experiment items panel on the left, expand **Machine Learning** > **Initialize Model** > **Classification**, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="79566-273">Conecte a saída, da parte inferior da **regressão logística multiclasse**, à entrada superior esquerda do item de modelo de **treinamento** .</span><span class="sxs-lookup"><span data-stu-id="79566-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="79566-275">Na lista de itens de teste no painel à esquerda, expanda **Machine Learning** > **Pontuação**e arraste o item de **modelo de Pontuação** para a tela.</span><span class="sxs-lookup"><span data-stu-id="79566-275">In list of experiment items in the panel on the left, expand **Machine Learning** > **Score**, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="79566-276">Conecte a saída, na parte inferior do **modelo de treinamento**, à entrada superior esquerda do **modelo de Pontuação**.</span><span class="sxs-lookup"><span data-stu-id="79566-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="79566-277">Conecte a saída inferior direita de **dividir dados**à entrada superior direita do item de **modelo de Pontuação** .</span><span class="sxs-lookup"><span data-stu-id="79566-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model** item.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="79566-279">Na lista de itens de **teste** no painel à esquerda, expanda **Machine Learning** > **avaliar**e arraste o item **modelo de avaliação** para a tela.</span><span class="sxs-lookup"><span data-stu-id="79566-279">In the list of **Experiment** items in the panel on the left, expand **Machine Learning** > **Evaluate**, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="79566-280">Conecte a saída do **modelo de Pontuação** à entrada superior esquerda do **modelo de avaliação**.</span><span class="sxs-lookup"><span data-stu-id="79566-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="79566-282">Você criou seu primeiro experimento de Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="79566-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="79566-283">Agora você pode salvar e executar o experimento.</span><span class="sxs-lookup"><span data-stu-id="79566-283">You can now save and run the experiment.</span></span> <span data-ttu-id="79566-284">No menu na parte inferior da página, clique no botão **salvar** para salvar o experimento e, em seguida, clique em **executar** para iniciar o experimento.</span><span class="sxs-lookup"><span data-stu-id="79566-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="79566-286">Você pode ver o **status** do experimento no canto superior direito da tela.</span><span class="sxs-lookup"><span data-stu-id="79566-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="79566-287">Aguarde alguns instantes até que o experimento seja concluído.</span><span class="sxs-lookup"><span data-stu-id="79566-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="79566-288">Se você tiver um grande conjunto de grandes (mundo real), é provável que o experimento possa levar horas para ser executado.</span><span class="sxs-lookup"><span data-stu-id="79566-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="79566-290">Clique com o botão direito do mouse no item **modelo** de avaliação na tela e, no menu de contexto, passe o mouse sobre **os resultados da avaliação**e selecione **Visualizar**.</span><span class="sxs-lookup"><span data-stu-id="79566-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="79566-292">Os resultados da avaliação serão exibidos mostrando as exibições previstas em relação aos resultados reais.</span><span class="sxs-lookup"><span data-stu-id="79566-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="79566-293">Isso usa 30% do conjunto de um original, que foi dividido anteriormente, para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="79566-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="79566-294">Você pode ver que os resultados não são ótimos, idealmente você teria o número mais alto em cada linha ser o item realçado nas colunas.</span><span class="sxs-lookup"><span data-stu-id="79566-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="79566-296">Feche os **resultados**.</span><span class="sxs-lookup"><span data-stu-id="79566-296">Close the **Results**.</span></span>

24. <span data-ttu-id="79566-297">Para usar o modelo de Machine Learning treinado recentemente, você precisa expô-lo como um **serviço Web**.</span><span class="sxs-lookup"><span data-stu-id="79566-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="79566-298">Para fazer isso, clique no item de menu **configurar serviço Web** no menu na parte inferior da página e clique em **serviço Web de previsão**.</span><span class="sxs-lookup"><span data-stu-id="79566-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="79566-300">Uma nova guia será criada e o modelo de treinamento mesclado para criar o novo serviço Web.</span><span class="sxs-lookup"><span data-stu-id="79566-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="79566-301">No menu na parte inferior da página, clique em **salvar**e em **executar**.</span><span class="sxs-lookup"><span data-stu-id="79566-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="79566-302">Você verá o status atualizado no canto superior direito da tela do experimento.</span><span class="sxs-lookup"><span data-stu-id="79566-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="79566-304">Quando a execução for concluída, um botão **implantar serviço Web** aparecerá na parte inferior da página.</span><span class="sxs-lookup"><span data-stu-id="79566-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="79566-305">Você está pronto para implantar o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="79566-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="79566-306">Clique em **implantar serviço Web** (clássico) no menu na parte inferior da página.</span><span class="sxs-lookup"><span data-stu-id="79566-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="79566-308">O navegador pode solicitar a permissão de um pop-up, que você deve **permitir**, embora seja necessário pressionar **implantar serviço Web** novamente, se a página implantar não for mostrada.</span><span class="sxs-lookup"><span data-stu-id="79566-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="79566-309">Depois que o experimento tiver sido criado, você será redirecionado para uma página de **painel** onde você terá sua **chave de API** exibida.</span><span class="sxs-lookup"><span data-stu-id="79566-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="79566-310">Copie-o em um bloco de notas por enquanto, você precisará dele em seu código em breve.</span><span class="sxs-lookup"><span data-stu-id="79566-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="79566-311">Depois de anotar sua chave de API, clique no botão **solicitação/resposta** na seção **ponto de extremidade padrão** abaixo da chave.</span><span class="sxs-lookup"><span data-stu-id="79566-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="79566-313">Se você clicar em testar nesta página, poderá inserir dados de entrada e exibir a saída.</span><span class="sxs-lookup"><span data-stu-id="79566-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="79566-314">Insira o **dia** e a **hora**.</span><span class="sxs-lookup"><span data-stu-id="79566-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="79566-315">Deixe a entrada do **produto** em branco.</span><span class="sxs-lookup"><span data-stu-id="79566-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="79566-316">Em seguida, clique no botão **confirmar** .</span><span class="sxs-lookup"><span data-stu-id="79566-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="79566-317">A saída na parte inferior da página mostrará o JSON que representa a probabilidade de cada produto ser a opção.</span><span class="sxs-lookup"><span data-stu-id="79566-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="79566-318">Uma nova página da Web será aberta, exibindo as instruções e alguns exemplos sobre a estrutura de solicitação exigida pelo Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="79566-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="79566-319">Copie o **URI de solicitação** exibido nesta página, no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="79566-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="79566-321">Agora você criou um sistema de aprendizado de máquina que fornece o produto mais provável para ser vendido com base nos dados de compra históricos, correlacionados com a hora do dia e dia do ano.</span><span class="sxs-lookup"><span data-stu-id="79566-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="79566-322">Para chamar o serviço Web, você precisará da URL para o ponto de extremidade de serviço e uma chave de API para o serviço.</span><span class="sxs-lookup"><span data-stu-id="79566-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="79566-323">Clique na guia **consumir** , no menu superior.</span><span class="sxs-lookup"><span data-stu-id="79566-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="79566-324">A página informações de **consumo** exibirá as informações necessárias para chamar o serviço Web do seu código.</span><span class="sxs-lookup"><span data-stu-id="79566-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="79566-325">Faça uma cópia da **chave primária** e da URL da **solicitação-resposta** .</span><span class="sxs-lookup"><span data-stu-id="79566-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="79566-326">Você precisará deles no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="79566-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="79566-327">Capítulo 5-Configurando o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="79566-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="79566-328">Configure e teste seu headset de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="79566-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="79566-329">Você **não** precisará de controladores de animação para este curso.</span><span class="sxs-lookup"><span data-stu-id="79566-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="79566-330">Se você precisar de suporte para configurar o headset de imersão, clique [aqui](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="79566-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="79566-331">Abra o **Unity** e crie um novo projeto de Unity chamado **Mr\_MachineLearning.**</span><span class="sxs-lookup"><span data-stu-id="79566-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="79566-332">Verifique se o tipo de projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="79566-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="79566-333">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="79566-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="79566-334">Vá para **Editar** **preferências** de > e, em seguida, na nova janela, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="79566-334">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="79566-335">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="79566-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="79566-336">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="79566-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="79566-337">Em seguida, vá para **arquivo** > **configurações de Build** e alterne a plataforma para **plataforma universal do Windows**clicando no botão ***alternar plataforma*** .</span><span class="sxs-lookup"><span data-stu-id="79566-337">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="79566-338">Verifique também se:</span><span class="sxs-lookup"><span data-stu-id="79566-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="79566-339">O **dispositivo de destino** está definido como **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="79566-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="79566-340">Para o Microsoft HoloLens, defina o **dispositivo de destino** como *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="79566-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="79566-341">O **tipo de compilação** está definido como **D3D**.</span><span class="sxs-lookup"><span data-stu-id="79566-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="79566-342">O **SDK** está definido para o **mais recente instalado**.</span><span class="sxs-lookup"><span data-stu-id="79566-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="79566-343">A **versão do Visual Studio** está definida como **mais recente instalada**.</span><span class="sxs-lookup"><span data-stu-id="79566-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="79566-344">**Compilar e executar** é definido como **computador local**.</span><span class="sxs-lookup"><span data-stu-id="79566-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="79566-345">Não se preocupe com a configuração de **cenas** no momento, pois elas são fornecidas mais tarde.</span><span class="sxs-lookup"><span data-stu-id="79566-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="79566-346">As configurações restantes devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="79566-346">The remaining settings should be left as default for now.</span></span>

        ![Configurando o projeto do Unity](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="79566-348">Na janela **configurações de compilação** , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o **Inspetor** está localizado.</span><span class="sxs-lookup"><span data-stu-id="79566-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="79566-349">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="79566-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="79566-350">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="79566-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="79566-351">A **versão de tempo de execução** de **script** deve ser **experimental** (.NET 4,6 equivalente)</span><span class="sxs-lookup"><span data-stu-id="79566-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="79566-352">O **back-end de script** deve ser ***.net***</span><span class="sxs-lookup"><span data-stu-id="79566-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="79566-353">O **nível de compatibilidade da API** deve ser **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="79566-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Configurando o projeto do Unity](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="79566-355">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="79566-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="79566-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="79566-356">**InternetClient**</span></span>

            ![Configurando o projeto do Unity](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="79566-358">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o **SDK do Windows Mixed Reality** foi adicionado</span><span class="sxs-lookup"><span data-stu-id="79566-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Configurando o projeto do Unity](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="79566-360">De volta **às configurações de Build** , os projetos do  *C# Unity* não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste.</span><span class="sxs-lookup"><span data-stu-id="79566-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="79566-361">Feche a janela configurações de compilação.</span><span class="sxs-lookup"><span data-stu-id="79566-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="79566-362">Salve seu projeto (**arquivo > salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="79566-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="79566-363">Capítulo 6-importando o pacote do MLProducts Unity</span><span class="sxs-lookup"><span data-stu-id="79566-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="79566-364">Para este curso, você precisará baixar um pacote de ativos do Unity chamado [**Azure-Mr-307. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="79566-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="79566-365">Esse pacote vem completo com uma cena, com todos os objetos criados, para que você possa se concentrar em fazê-lo funcionar.</span><span class="sxs-lookup"><span data-stu-id="79566-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="79566-366">O script **ShelfKeeper** é fornecido, embora só mantenha as variáveis públicas, para fins de estrutura de configuração de cena.</span><span class="sxs-lookup"><span data-stu-id="79566-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="79566-367">Você precisará fazer todas as outras seções.</span><span class="sxs-lookup"><span data-stu-id="79566-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="79566-368">Para importar este pacote:</span><span class="sxs-lookup"><span data-stu-id="79566-368">To import this package:</span></span>

1.  <span data-ttu-id="79566-369">Com o painel do Unity na frente, clique em **ativos** no menu na parte superior da tela e, em seguida, clique em **Importar pacote, pacote personalizado**.</span><span class="sxs-lookup"><span data-stu-id="79566-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![Importando o pacote do MLProducts Unity](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="79566-371">Use o seletor de arquivos para selecionar o pacote **Azure-Mr-307. unitypackage** e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="79566-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="79566-372">Uma lista de componentes para este ativo será exibida para você.</span><span class="sxs-lookup"><span data-stu-id="79566-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="79566-373">Confirme a importação clicando em **importar**.</span><span class="sxs-lookup"><span data-stu-id="79566-373">Confirm the import by clicking **Import**.</span></span>

    ![Importando o pacote do MLProducts Unity](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="79566-375">Depois de concluir a importação, você observará que algumas novas pastas apareciam no painel de **projeto**do Unity.</span><span class="sxs-lookup"><span data-stu-id="79566-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="79566-376">Esses são os modelos 3D e os respectivos materiais que fazem parte da cena previamente realizada na qual você trabalhará.</span><span class="sxs-lookup"><span data-stu-id="79566-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="79566-377">Você escreverá a maioria do código neste curso.</span><span class="sxs-lookup"><span data-stu-id="79566-377">You will write the majority of the code in this course.</span></span>

    ![Importando o pacote do MLProducts Unity](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="79566-379">Na pasta do **painel Projeto** , clique na pasta **cenas** e clique duas vezes na cena dentro (chamada de **MR_MachineLearningScene**).</span><span class="sxs-lookup"><span data-stu-id="79566-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="79566-380">A cena será aberta (consulte a imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="79566-380">The scene will open (see image below).</span></span> <span data-ttu-id="79566-381">Se os losangos vermelhos estiverem ausentes, basta clicar no botão **utensílios** , na parte superior direita do **painel Game**.</span><span class="sxs-lookup"><span data-stu-id="79566-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![Importando o pacote do MLProducts Unity](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="79566-383">Capítulo 7-verificando as DLLs no Unity</span><span class="sxs-lookup"><span data-stu-id="79566-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="79566-384">Para aproveitar o uso de bibliotecas JSON (usadas para serialização e desserialização), uma DLL Newtonsoft foi implementada com o pacote que você colocou.</span><span class="sxs-lookup"><span data-stu-id="79566-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="79566-385">A biblioteca deve ter a configuração correta, embora vale a pena verificar (especialmente se você estiver tendo problemas com o código não funcionando).</span><span class="sxs-lookup"><span data-stu-id="79566-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="79566-386">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="79566-386">To do so:</span></span>

-  <span data-ttu-id="79566-387">Clique com o botão esquerdo do mouse no arquivo Newtonsoft dentro da pasta plugins e examine o **painel Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="79566-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="79566-388">Verifique se **todas as plataformas** estão marcadas.</span><span class="sxs-lookup"><span data-stu-id="79566-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="79566-389">Vá para a **guia UWP** e verifique também se **não processar** está marcado.</span><span class="sxs-lookup"><span data-stu-id="79566-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Importando as DLLs no Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="79566-391">Capítulo 8-criar a classe ShelfKeeper</span><span class="sxs-lookup"><span data-stu-id="79566-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="79566-392">A classe **ShelfKeeper** hospeda métodos que controlam a interface do usuário e os produtos gerados na cena.</span><span class="sxs-lookup"><span data-stu-id="79566-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="79566-393">Como parte do pacote importado, você receberá essa classe, embora ela esteja incompleta.</span><span class="sxs-lookup"><span data-stu-id="79566-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="79566-394">Agora é hora de concluir essa classe:</span><span class="sxs-lookup"><span data-stu-id="79566-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="79566-395">Clique duas vezes no script **ShelfKeeper** , na pasta **scripts** , para abri-lo com o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="79566-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="79566-396">Substitua todo o código existente no script pelo código a seguir, que define a data e a hora e tem um método para mostrar um produto.</span><span class="sxs-lookup"><span data-stu-id="79566-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  <span data-ttu-id="79566-397">Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="79566-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="79566-398">De volta ao editor do Unity, verifique se a classe **ShelfKeeper** é semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="79566-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![Criar a classe ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="79566-400">Se o seu script não tiver os destinos de referência (ou seja, *Data (malha de texto)* ), basta arrastar os objetos correspondentes do **painel hierarquia**para os campos de destino.</span><span class="sxs-lookup"><span data-stu-id="79566-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="79566-401">Veja abaixo a explicação, se necessário:</span><span class="sxs-lookup"><span data-stu-id="79566-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="79566-402">Abra a matriz de **ponto de geração** dentro do script do componente **ShelfKeeper** clicando nela com o botão esquerdo.</span><span class="sxs-lookup"><span data-stu-id="79566-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="79566-403">Uma subseção será exibida chamada de **tamanho**, o que indica o tamanho da matriz.</span><span class="sxs-lookup"><span data-stu-id="79566-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="79566-404">Digite **3** na caixa de texto ao lado de **tamanho** e pressione **Enter**, e três slots serão criados abaixo.</span><span class="sxs-lookup"><span data-stu-id="79566-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="79566-405">Na **hierarquia** , expanda o objeto de **exibição de hora** (clicando com o botão esquerdo do mouse na seta ao lado dele).</span><span class="sxs-lookup"><span data-stu-id="79566-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="79566-406">Em seguida, clique na ***câmera principal*** de dentro da **hierarquia**, para que o **Inspetor** mostre suas informações.</span><span class="sxs-lookup"><span data-stu-id="79566-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="79566-407">Selecione a **câmera principal** no **painel hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="79566-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="79566-408">Arraste os objetos de **Data** e **hora** do **painel hierarquia** para os slots de texto de **Data** e **hora** dentro do **Inspetor** da **câmera principal** no componente **ShelfKeeper** .</span><span class="sxs-lookup"><span data-stu-id="79566-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="79566-409">Arraste os **pontos de geração** do **painel hierarquia** (abaixo do objeto *prateleira* ) para os **três** destinos de referência de **elemento** abaixo da matriz de **ponto de geração** , conforme mostrado na imagem.</span><span class="sxs-lookup"><span data-stu-id="79566-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![Criar a classe ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="79566-411">Capítulo 9-criar a classe ProductPrediction</span><span class="sxs-lookup"><span data-stu-id="79566-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="79566-412">A próxima classe que você vai criar é a classe **ProductPrediction** .</span><span class="sxs-lookup"><span data-stu-id="79566-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="79566-413">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="79566-413">This class is responsible for:</span></span>

-   <span data-ttu-id="79566-414">Consultando a instância do **serviço de Machine Learning** , fornecendo a data e hora atuais.</span><span class="sxs-lookup"><span data-stu-id="79566-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="79566-415">Desserializando a resposta JSON em dados utilizáveis.</span><span class="sxs-lookup"><span data-stu-id="79566-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="79566-416">Interpretação dos dados, recuperação dos 3 produtos recomendados.</span><span class="sxs-lookup"><span data-stu-id="79566-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="79566-417">Chamar os métodos da classe **ShelfKeeper** para exibir os dados na cena.</span><span class="sxs-lookup"><span data-stu-id="79566-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="79566-418">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="79566-418">To create this class:</span></span>

1.  <span data-ttu-id="79566-419">Vá para a pasta **scripts** , no **painel Projeto**.</span><span class="sxs-lookup"><span data-stu-id="79566-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="79566-420">Clique com o botão direito do mouse dentro da pasta, **crie** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="79566-420">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="79566-421">Chame o script **ProductPrediction**.</span><span class="sxs-lookup"><span data-stu-id="79566-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="79566-422">Clique duas vezes no novo script **ProductPrediction** para abri-lo com o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="79566-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="79566-423">Se a caixa de diálogo **modificação de arquivo detectada** for exibida, clique em \***recarregar solução**.</span><span class="sxs-lookup"><span data-stu-id="79566-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="79566-424">Adicione os seguintes namespaces à parte superior da classe ProductPrediction:</span><span class="sxs-lookup"><span data-stu-id="79566-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  <span data-ttu-id="79566-425">Dentro da classe **ProductPrediction** , insira os dois objetos a seguir que são compostos de várias classes aninhadas.</span><span class="sxs-lookup"><span data-stu-id="79566-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="79566-426">Essas classes são usadas para serializar e desserializar o JSON para o serviço de Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="79566-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  <span data-ttu-id="79566-427">Em seguida, adicione as seguintes variáveis acima do código anterior (para que o código relacionado ao JSON esteja na parte inferior do script, abaixo de todos os demais códigos e do caminho):</span><span class="sxs-lookup"><span data-stu-id="79566-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="79566-428">Certifique-se de inserir a **chave primária** e o **ponto de extremidade de solicitação-resposta**, no portal Machine Learning, nas variáveis aqui.</span><span class="sxs-lookup"><span data-stu-id="79566-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="79566-429">As imagens abaixo mostram onde você teria levado a chave e o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="79566-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="79566-432">Insira este código dentro do método **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="79566-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="79566-433">O método **Start ()** é chamado quando a classe é inicializada:</span><span class="sxs-lookup"><span data-stu-id="79566-433">The **Start()** method is called when the class initializes:</span></span>

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  <span data-ttu-id="79566-434">Este é o método que coleta a data e a hora do Windows e a converte em um formato que o experimento de Machine Learning pode usar para comparar com os dados armazenados na tabela.</span><span class="sxs-lookup"><span data-stu-id="79566-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. <span data-ttu-id="79566-435">Você pode **excluir** o método **Update ()** , pois essa classe não o usará.</span><span class="sxs-lookup"><span data-stu-id="79566-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="79566-436">Adicione o seguinte método que irá comunicar a data e hora atuais para o ponto de extremidade Machine Learning e receber uma resposta no formato JSON.</span><span class="sxs-lookup"><span data-stu-id="79566-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. <span data-ttu-id="79566-437">Adicione o método a seguir, que é responsável pela desserialização da resposta JSON e pela comunicação do resultado da desserialização para a classe **ShelfKeeper** .</span><span class="sxs-lookup"><span data-stu-id="79566-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="79566-438">Esse resultado será o nome dos três itens previstos para vender o máximo em data e hora atuais.</span><span class="sxs-lookup"><span data-stu-id="79566-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="79566-439">Insira o código abaixo na classe **ProductPrediction** , abaixo do método anterior.</span><span class="sxs-lookup"><span data-stu-id="79566-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. <span data-ttu-id="79566-440">Salve o **Visual Studio** e vá de volta para o **Unity**.</span><span class="sxs-lookup"><span data-stu-id="79566-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="79566-441">Arraste o script da classe **ProductPrediction** da pasta **script** para o objeto **principal da câmera** .</span><span class="sxs-lookup"><span data-stu-id="79566-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="79566-442">Salve seu **arquivo** de cena e de projeto > **salvar a cena/arquivo** > **salvar projeto**.</span><span class="sxs-lookup"><span data-stu-id="79566-442">Save your scene and project **File** > **Save Scene/File** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="79566-443">Capítulo 10 – criar a solução UWP</span><span class="sxs-lookup"><span data-stu-id="79566-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="79566-444">Agora é hora de criar seu projeto como uma solução UWP, para que ele possa ser executado como um aplicativo autônomo.</span><span class="sxs-lookup"><span data-stu-id="79566-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="79566-445">Para compilar:</span><span class="sxs-lookup"><span data-stu-id="79566-445">To Build:</span></span>

1.  <span data-ttu-id="79566-446">Salve a cena atual clicando em **arquivo** > **salvar cenas**.</span><span class="sxs-lookup"><span data-stu-id="79566-446">Save the current scene by clicking on **File** > **Save Scenes**.</span></span>

2.  <span data-ttu-id="79566-447">Vá para **arquivo** > **configurações de Build**</span><span class="sxs-lookup"><span data-stu-id="79566-447">Go to **File** > **Build Settings**</span></span>

3.  <span data-ttu-id="79566-448">Marque a caixa denominada **projetos do Unity C#**  (isso é importante porque permitirá que você edite as classes após a conclusão da compilação).</span><span class="sxs-lookup"><span data-stu-id="79566-448">Check the box called **Unity C# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="79566-449">Clique em **Adicionar e abrir cenas**,</span><span class="sxs-lookup"><span data-stu-id="79566-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="79566-450">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="79566-450">Click **Build**.</span></span>

    ![Compilar a solução UWP](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="79566-452">Você será solicitado a selecionar a pasta na qual deseja criar a solução.</span><span class="sxs-lookup"><span data-stu-id="79566-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="79566-453">Crie uma pasta **Builds** e dentro dessa pasta crie outra pasta com um nome apropriado de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="79566-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="79566-454">Clique na nova pasta e, em seguida, clique em **Selecionar pasta**para iniciar a compilação nesse local.</span><span class="sxs-lookup"><span data-stu-id="79566-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![Compilar a solução UWP](images/AzureLabs-Lab7-55.png)

    ![Compilar a solução UWP](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="79566-457">Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).</span><span class="sxs-lookup"><span data-stu-id="79566-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="79566-458">Capítulo 11 – implantar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="79566-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="79566-459">Para implantar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="79566-459">To deploy your application:</span></span>

1.  <span data-ttu-id="79566-460">Navegue até sua nova compilação do Unity (a pasta do **aplicativo** ) e abra o arquivo de solução com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="79566-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="79566-461">Com o Visual Studio aberto, você precisa restaurar os pacotes NuGet, o que pode ser feito clicando com o botão direito do mouse na solução MachineLearningLab_Build, da Gerenciador de Soluções (localizada à direita do Visual Studio) e, em seguida, clicando em restaurar pacotes NuGet:</span><span class="sxs-lookup"><span data-stu-id="79566-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![Adicionar pacotes NuGet](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="79566-463">Na configuração da solução, selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="79566-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="79566-464">Na plataforma da solução, selecione **x86**, **computador local**.</span><span class="sxs-lookup"><span data-stu-id="79566-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="79566-465">Para o Microsoft HoloLens, você pode achar mais fácil definir isso como *computador remoto*, para que você não esteja vinculado ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="79566-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="79566-466">No entanto, também será necessário fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="79566-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="79566-467">Conheça o **endereço IP** do seu HoloLens, que pode ser encontrado dentro das *configurações > rede & Internet > Wi-Fi > opções avançadas*; o IPv4 é o endereço que você deve usar.</span><span class="sxs-lookup"><span data-stu-id="79566-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="79566-468">Verificar se o modo **de** **desenvolvedor** está ativado; encontrado em *configurações > atualização & > de segurança para desenvolvedores*.</span><span class="sxs-lookup"><span data-stu-id="79566-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Adicionar pacotes NuGet](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="79566-470">Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu PC.</span><span class="sxs-lookup"><span data-stu-id="79566-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="79566-471">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="79566-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="79566-472">Ao executar o aplicativo de realidade misturada, você verá o banco que foi configurado em sua cena do Unity e a partir da inicialização, os dados configurados no Azure serão buscados.</span><span class="sxs-lookup"><span data-stu-id="79566-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="79566-473">Os dados serão desserializados em seu aplicativo, e os três resultados principais para sua data e hora atuais serão fornecidos visualmente, como três modelos no banco.</span><span class="sxs-lookup"><span data-stu-id="79566-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="79566-474">Seu aplicativo Machine Learning concluído</span><span class="sxs-lookup"><span data-stu-id="79566-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="79566-475">Parabéns, você criou um aplicativo de realidade misturada que aproveita as Azure Machine Learning para fazer previsões de dados e exibi-las em sua cena.</span><span class="sxs-lookup"><span data-stu-id="79566-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![Adicionar pacotes NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="79566-477">Utilização</span><span class="sxs-lookup"><span data-stu-id="79566-477">Exercise</span></span>

<span data-ttu-id="79566-478">**Exercício 1**</span><span class="sxs-lookup"><span data-stu-id="79566-478">**Exercise 1**</span></span>

<span data-ttu-id="79566-479">Experimente a ordem de classificação do seu aplicativo e faça com que as três previsões inferiores apareçam na prateleira, pois esses dados seriam potencialmente úteis também.</span><span class="sxs-lookup"><span data-stu-id="79566-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="79566-480">**Exercício 2**</span><span class="sxs-lookup"><span data-stu-id="79566-480">**Exercise 2**</span></span>

<span data-ttu-id="79566-481">Usando **tabelas do Azure** , preencha uma nova tabela com informações de clima e crie um novo experimento usando os dados.</span><span class="sxs-lookup"><span data-stu-id="79566-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
