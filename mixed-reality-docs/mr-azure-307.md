---
title: Aprendizado de máquina 307 - MR e o Azure
description: Conclua este curso para aprender a implementar o Azure Machine Learning Studio dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, aprendizado de máquina, AM, o estúdio de machine learning, hololens, envolventes e vr
ms.openlocfilehash: 726a6cce91d46ad878f8502381d085fb979ac72a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589628"
---
>[!NOTE]
><span data-ttu-id="70a62-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="70a62-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="70a62-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="70a62-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="70a62-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="70a62-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="70a62-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="70a62-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="70a62-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="70a62-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="70a62-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="70a62-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="70a62-110">MR e o Azure 307: Aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="70a62-110">MR and Azure 307: Machine learning</span></span>

![final do produto-iniciar](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="70a62-112">Neste curso, você aprenderá como adicionar recursos de aprendizado de máquina (ML) para um aplicativo de realidade misturada usando o Azure Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="70a62-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="70a62-113">*O Azure Machine Learning Studio* é um serviço da Microsoft, que fornece aos desenvolvedores um grande número de algoritmos de aprendizado de máquina, que pode ajudar com os dados de entrada, saída, preparação e visualização.</span><span class="sxs-lookup"><span data-stu-id="70a62-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="70a62-114">Desses componentes, em seguida, é possível desenvolver um experimento de análise preditiva, itere sobre ela e usá-lo para treinar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="70a62-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="70a62-115">Após o treinamento, é possível fazer seu modelo operacional em nuvem do Azure, para que, em seguida, ele pode pontuar novos dados.</span><span class="sxs-lookup"><span data-stu-id="70a62-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="70a62-116">Para obter mais informações, visite o [página do Azure Machine Learning Studio](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span><span class="sxs-lookup"><span data-stu-id="70a62-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span></span>

<span data-ttu-id="70a62-117">Com a conclusão deste curso, você terá um aplicativo de imersão headset de realidade mista e terá aprendido como fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="70a62-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="70a62-118">Fornecer uma tabela de dados de vendas para o *do Azure Machine Learning Studio* portal e o design de um algoritmo para prever vendas futuras itens populares.</span><span class="sxs-lookup"><span data-stu-id="70a62-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="70a62-119">Criar uma **projeto do Unity**, que pode receber e interpretar os dados de previsão do serviço ML.</span><span class="sxs-lookup"><span data-stu-id="70a62-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="70a62-120">Exibir os dados de predicação visualmente dentro de **projeto do Unity**, por meio de fornecer os itens mais populares de vendas, em uma prateleira.</span><span class="sxs-lookup"><span data-stu-id="70a62-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="70a62-121">Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="70a62-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="70a62-122">Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="70a62-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="70a62-123">Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="70a62-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="70a62-124">Este curso é um tutorial independente, o que não envolvem diretamente quaisquer outros laboratórios de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="70a62-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="70a62-125">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="70a62-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="70a62-126">Curso</span><span class="sxs-lookup"><span data-stu-id="70a62-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="70a62-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="70a62-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="70a62-128"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="70a62-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="70a62-129">MR e o Azure 307: Aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="70a62-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="70a62-130">✔️</span><span class="sxs-lookup"><span data-stu-id="70a62-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="70a62-131">✔️</span><span class="sxs-lookup"><span data-stu-id="70a62-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="70a62-132">Enquanto este curso se concentra primariamente em fones de ouvido Windows Mixed Reality de imersão (VR), você também pode aplicar o que você aprenderá neste curso para o Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="70a62-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="70a62-133">Como acompanhar o curso, você verá notas quaisquer alterações que talvez seja necessário empregar para dar suporte ao HoloLens.</span><span class="sxs-lookup"><span data-stu-id="70a62-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="70a62-134">Ao usar o HoloLens, você pode perceber algum eco durante a captura de voz.</span><span class="sxs-lookup"><span data-stu-id="70a62-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="70a62-135">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="70a62-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="70a62-136">Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="70a62-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="70a62-137">Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="70a62-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="70a62-138">Você é livre para usar o software mais recente, conforme listado dentro de [instalar o artigo de ferramentas](install-the-tools.md), embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .</span><span class="sxs-lookup"><span data-stu-id="70a62-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="70a62-139">Recomendamos que o hardware e software para este curso a seguir:</span><span class="sxs-lookup"><span data-stu-id="70a62-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="70a62-140">Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)</span><span class="sxs-lookup"><span data-stu-id="70a62-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="70a62-141">Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="70a62-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="70a62-142">O SDK mais recente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="70a62-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="70a62-143">2017.4 do Unity</span><span class="sxs-lookup"><span data-stu-id="70a62-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="70a62-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="70a62-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="70a62-145">Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="70a62-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="70a62-146">Acesso à Internet para a instalação do Azure e a recuperação de dados do ML</span><span class="sxs-lookup"><span data-stu-id="70a62-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="70a62-147">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="70a62-147">Before you start</span></span>

<span data-ttu-id="70a62-148">Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="70a62-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="70a62-149">Capítulo 1 - configuração da conta de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="70a62-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="70a62-150">Para usar a API de tradução do Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="70a62-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="70a62-151">Faça logon na [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="70a62-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="70a62-152">Se você ainda não tiver uma conta do Azure, você precisará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="70a62-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="70a62-153">Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="70a62-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="70a62-154">Quando você estiver conectado, clique em **contas de armazenamento** no menu à esquerda.</span><span class="sxs-lookup"><span data-stu-id="70a62-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="70a62-156">A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="70a62-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="70a62-157">Sobre o **contas de armazenamento** guia, clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="70a62-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="70a62-159">No **criar conta de armazenamento** painel:</span><span class="sxs-lookup"><span data-stu-id="70a62-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="70a62-160">Inserir uma **nome** para sua conta, lembre-se que este campo aceita apenas números e letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="70a62-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="70a62-161">Para **modelo de implantação** selecionar **Gerenciador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="70a62-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="70a62-162">Para **tipo de conta**, selecione **(uso geral v1) de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="70a62-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="70a62-163">Para **desempenho**, selecione **padrão**.</span><span class="sxs-lookup"><span data-stu-id="70a62-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="70a62-164">Para **replicação** selecionar **leitura-acesso-com redundância geográfica (RA-GRS) de armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="70a62-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="70a62-165">Deixe **transferência segura obrigatória** como **desabilitado**.</span><span class="sxs-lookup"><span data-stu-id="70a62-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="70a62-166">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="70a62-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="70a62-167">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="70a62-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="70a62-168">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="70a62-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="70a62-169">É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="70a62-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="70a62-170">Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="70a62-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="70a62-171">Determinar a **local** para seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="70a62-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="70a62-172">O local seria o ideal é que na região em que o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="70a62-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="70a62-173">Alguns ativos do Azure estão disponíveis somente em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="70a62-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="70a62-174">Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="70a62-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="70a62-176">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="70a62-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="70a62-177">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="70a62-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="70a62-179">Capítulo 2 - o Azure Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="70a62-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="70a62-180">Para usar o *do Azure Machine Learning*, você precisará configurar uma instância do serviço de Machine Learning para ficar disponível para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="70a62-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="70a62-181">No Portal do Azure, clique em **New** no canto superior esquerdo de canto e procure **espaço de trabalho do Machine Learning Studio**, pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="70a62-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="70a62-183">A nova página fornecerá uma descrição do **espaço de trabalho do Machine Learning Studio** service.</span><span class="sxs-lookup"><span data-stu-id="70a62-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="70a62-184">Na parte inferior esquerda desse prompt, clique no **criar** botão para criar uma associação com este serviço.</span><span class="sxs-lookup"><span data-stu-id="70a62-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="70a62-185">Depois de clicar em **Create**, um painel será exibido em que você precisa fornecer alguns detalhes sobre sua nova **serviço de Machine Learning Studio**:</span><span class="sxs-lookup"><span data-stu-id="70a62-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="70a62-186">Inserir sua desejada **nome do espaço de trabalho** para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="70a62-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="70a62-187">Selecione uma **assinatura**.</span><span class="sxs-lookup"><span data-stu-id="70a62-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="70a62-188">Escolha uma **grupo de recursos** ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="70a62-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="70a62-189">Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="70a62-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="70a62-190">É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).</span><span class="sxs-lookup"><span data-stu-id="70a62-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="70a62-191">Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="70a62-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="70a62-192">Determinar a **local** para seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="70a62-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="70a62-193">O local seria o ideal é que na região em que o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="70a62-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="70a62-194">Alguns ativos do Azure estão disponíveis somente em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="70a62-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="70a62-195">Você deve usar o mesmo grupo de recursos que você usou para criar o armazenamento do Azure no capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="70a62-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="70a62-196">Para o **conta de armazenamento** seção, clique em **usar existente**, em seguida, clique no menu suspenso e a partir daí, clique o **conta de armazenamento** você criou no último capítulo.</span><span class="sxs-lookup"><span data-stu-id="70a62-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="70a62-197">Selecionar as devidas **tipo de preço do espaço de trabalho** para você, no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="70a62-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="70a62-198">Dentro de **plano do serviço Web** seção, clique em **Create** **novo,** , em seguida, insira um nome para ele no campo de texto.</span><span class="sxs-lookup"><span data-stu-id="70a62-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="70a62-199">Dos **tipo de preço de plano de serviço Web** , selecione a camada de preço de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="70a62-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="70a62-200">Um chamada de camada de teste de desenvolvimento **padrão de desenvolvimento/teste** devem estar disponíveis para você sem custo adicional.</span><span class="sxs-lookup"><span data-stu-id="70a62-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="70a62-201">Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="70a62-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="70a62-202">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="70a62-202">Click **Create**.</span></span>

        ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="70a62-204">Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="70a62-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="70a62-205">Uma notificação será exibida no portal depois que a instância do serviço é criada.</span><span class="sxs-lookup"><span data-stu-id="70a62-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="70a62-207">Clique na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="70a62-207">Click on the notification to explore your new Service instance.</span></span>

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="70a62-209">Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="70a62-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="70a62-210">Na página exibida, sob o **Links adicionais** seção, clique em **iniciar o estúdio de Machine Learning**, que direcionará o seu navegador para o **Machine Learning Studio** Portal.</span><span class="sxs-lookup"><span data-stu-id="70a62-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="70a62-212">Use o **entrar** botão, na parte superior direita ou no centro, para fazer logon em seu Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="70a62-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="70a62-214">Capítulo 3 - Machine Learning Studio: Instalação do conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="70a62-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="70a62-215">Uma das maneiras de trabalham de algoritmos de aprendizado de máquina está analisando os dados existentes e, em seguida, tentar prever resultados futuros com base no conjunto de dados existente.</span><span class="sxs-lookup"><span data-stu-id="70a62-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="70a62-216">Isso geralmente significa que os dados mais existentes que você tiver, melhor o algoritmo será ao prever resultados futuros.</span><span class="sxs-lookup"><span data-stu-id="70a62-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="70a62-217">Uma tabela de exemplo é fornecida para você, para este curso, chamado [ProductsTableCSV e pode ser baixado aqui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span><span class="sxs-lookup"><span data-stu-id="70a62-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70a62-218">O arquivo. zip acima contém ambas as **ProductsTableCSV** e o **unitypackage**, que será necessária no [capítulo 6](#chapter-6---importing-the-mlproducts-unity-package).</span><span class="sxs-lookup"><span data-stu-id="70a62-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="70a62-219">Este pacote também é fornecido dentro desse capítulo, embora separado para o arquivo csv.</span><span class="sxs-lookup"><span data-stu-id="70a62-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="70a62-220">Esse conjunto de dados de exemplo contém um registro dos objetos mais vendidos em cada hora de cada dia do ano de 2017.</span><span class="sxs-lookup"><span data-stu-id="70a62-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![O Machine Learning Studio: Instalação do conjunto de dados](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="70a62-222">Por exemplo, no dia 1 de 2017, às 13:30 (hora 13), o item mais vendido era salt e pepper.</span><span class="sxs-lookup"><span data-stu-id="70a62-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="70a62-223">Esta tabela de exemplo contém 9998 entradas.</span><span class="sxs-lookup"><span data-stu-id="70a62-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="70a62-224">Volte para o **Machine Learning Studio** portal, e adicione essa tabela como um **conjunto de dados** para seu ML.</span><span class="sxs-lookup"><span data-stu-id="70a62-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="70a62-225">Faça isso clicando o **+ novo** botão no canto inferior esquerdo da tela.</span><span class="sxs-lookup"><span data-stu-id="70a62-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![O Machine Learning Studio: Instalação do conjunto de dados](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="70a62-227">Uma seção aparecerá na parte inferior e, em que há o painel de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="70a62-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="70a62-228">Clique em **Dataset**, em seguida, à direita, **do arquivo Local**.</span><span class="sxs-lookup"><span data-stu-id="70a62-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![O Machine Learning Studio: Instalação do conjunto de dados](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="70a62-230">Carregar o novo **conjunto de dados** seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="70a62-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="70a62-231">A janela de carregamento será exibida, onde você pode **procurar** seu disco rígido para o novo conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="70a62-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![O Machine Learning Studio: Instalação do conjunto de dados](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="70a62-233">Quando selecionado e de volta na janela de upload, deixe a caixa de seleção não marcada.</span><span class="sxs-lookup"><span data-stu-id="70a62-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="70a62-234">No campo de texto abaixo, insira **ProductsTableCSV.csv** como o nome do conjunto de dados (embora deve ser adicionado automaticamente).</span><span class="sxs-lookup"><span data-stu-id="70a62-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="70a62-235">Usando o menu suspenso para **tipo**, selecione **arquivo CSV genérico com um cabeçalho (. csv)**.</span><span class="sxs-lookup"><span data-stu-id="70a62-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="70a62-236">Pressione a escala na parte inferior direita da janela de carregamento e seu **conjunto de dados** será carregado.</span><span class="sxs-lookup"><span data-stu-id="70a62-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="70a62-237">Capítulo 4 - Machine Learning Studio: O experimento</span><span class="sxs-lookup"><span data-stu-id="70a62-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="70a62-238">Antes de compilar seu sistema de aprendizado de máquina, você precisará criar um experimento, para validar sua teoria sobre seus dados.</span><span class="sxs-lookup"><span data-stu-id="70a62-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="70a62-239">Com os resultados, você saberá se você precisa de mais dados, ou se não houver nenhuma correlação entre os dados e um resultado possível.</span><span class="sxs-lookup"><span data-stu-id="70a62-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="70a62-240">Para iniciar a criação de um experimento:</span><span class="sxs-lookup"><span data-stu-id="70a62-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="70a62-241">Clique novamente na **+ novo** botão na parte inferior esquerda da página, clique em **experimento** > **experimento em branco**.</span><span class="sxs-lookup"><span data-stu-id="70a62-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="70a62-243">Uma nova página será exibida com um teste em branco:</span><span class="sxs-lookup"><span data-stu-id="70a62-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="70a62-244">No painel esquerdo expandir \**conjuntos de dados salvos* > \* Meus conjuntos de dados \* \* e arraste a **ProductsTableCSV** para o **tela do experimento**.</span><span class="sxs-lookup"><span data-stu-id="70a62-244">From the panel on the left expand \**Saved Datasets* > \*My Datasets\*\* and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="70a62-246">No painel à esquerda, expanda **Data Transformation** > **exemplo e dividir**.</span><span class="sxs-lookup"><span data-stu-id="70a62-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="70a62-247">Em seguida, arraste a **dividir dados** item para o **tela do experimento**.</span><span class="sxs-lookup"><span data-stu-id="70a62-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="70a62-248">O item de dados de divisão irá dividir o conjunto de dados em duas partes.</span><span class="sxs-lookup"><span data-stu-id="70a62-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="70a62-249">Uma parte que você usará para treinar o algoritmo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="70a62-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="70a62-250">A segunda parte será usada para avaliar a precisão do algoritmo gerado.</span><span class="sxs-lookup"><span data-stu-id="70a62-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="70a62-252">No painel à direita (enquanto os dados de divisão item na tela é selecionado), edite o **fração de linhas no primeiro conjunto de dados de saída** à **0,7**.</span><span class="sxs-lookup"><span data-stu-id="70a62-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="70a62-253">Isso dividirá os dados em duas partes, a primeira parte será 70% dos dados e a segunda parte será de 30% restantes.</span><span class="sxs-lookup"><span data-stu-id="70a62-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="70a62-254">Para garantir que os dados são divididos aleatoriamente, verifique se o **divisão aleatória** caixa de seleção permanece marcada.</span><span class="sxs-lookup"><span data-stu-id="70a62-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="70a62-256">Arraste uma conexão da base do **ProductsTableCSV** item na tela para a parte superior do item de dados de divisão.</span><span class="sxs-lookup"><span data-stu-id="70a62-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="70a62-257">Isso se conectará os itens e enviar o **ProductsTableCSV** saída do conjunto de dados (os dados) para a entrada de dados de divisão.</span><span class="sxs-lookup"><span data-stu-id="70a62-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="70a62-259">No **experimentos** do painel no lado esquerdo, expanda \**Machine Learning* > \* Train **. Arraste o **treinar modelo \* \* item out em à tela do experimento.</span><span class="sxs-lookup"><span data-stu-id="70a62-259">In the **Experiments** panel on the left side, expand \**Machine Learning* > \*Train **. Drag the **Train Model\*\* item out in to the Experiment canvas.</span></span> <span data-ttu-id="70a62-260">Sua tela deve ser o mesmo que o abaixo.</span><span class="sxs-lookup"><span data-stu-id="70a62-260">Your canvas should look the same as the below.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="70a62-262">Do ***canto inferior esquerdo*** da **dividir dados** item arrastar uma conexão para o **parte superior direita** do **treinar modelo** item.</span><span class="sxs-lookup"><span data-stu-id="70a62-262">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="70a62-263">A primeira divisão de 70% do conjunto de dados será usada pelo modelo de treinamento para treinar o algoritmo.</span><span class="sxs-lookup"><span data-stu-id="70a62-263">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="70a62-265">Selecione o **modelo de treinamento** item na tela e, no **propriedades** painel (no lado direito da janela do navegador), clique o **iniciar seletor de coluna**  botão.</span><span class="sxs-lookup"><span data-stu-id="70a62-265">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="70a62-266">Na caixa de texto Digite **produto** e, em seguida, pressione **Enter**, *produto* será definido como uma coluna para treinar previsões.</span><span class="sxs-lookup"><span data-stu-id="70a62-266">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="70a62-267">Depois disso, clique no **escala** no canto inferior direito para fechar a caixa de diálogo de seleção.</span><span class="sxs-lookup"><span data-stu-id="70a62-267">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="70a62-269">Você pretende treinar uma **Regressão logística Multiclasse** algoritmo para prever mais vendidos **produto** com base na hora do dia e a data.</span><span class="sxs-lookup"><span data-stu-id="70a62-269">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="70a62-270">Ele está além do escopo deste documento para explicar os detalhes dos diferentes algoritmos fornecidos pelo Azure Machine Learning studio, no entanto, você pode descobrir mais sobre o [folha de consulta de algoritmo do Machine Learning](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="70a62-270">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="70a62-271">No painel de itens de teste à esquerda, expanda \* \**Machine Learning* > *inicializar modelo* > \* classificação \***e arraste o **Multiclasse Logística regressão \* \* item para a tela do experimento.</span><span class="sxs-lookup"><span data-stu-id="70a62-271">From the experiment items panel on the left, expand \*\**Machine Learning* > *Initialize Model* > \*Classification\***, and drag the **Multiclass Logistic Regression\*\* item on to the experiment canvas.</span></span>

13. <span data-ttu-id="70a62-272">Conecte a saída, da parte inferior da **Regressão logística Multiclasse**, com a entrada do canto superior esquerdo do **treinar modelo** item.</span><span class="sxs-lookup"><span data-stu-id="70a62-272">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="70a62-274">Na lista de itens do experimento no painel à esquerda, expanda \**Machine Learning* > \* pontuação**e arraste o **item de modelo de pontuação \* \* na tela de desenho.</span><span class="sxs-lookup"><span data-stu-id="70a62-274">In list of experiment items in the panel on the left, expand \**Machine Learning* > \*Score **, and drag the **Score Model\*\* item on to the canvas.</span></span>

15. <span data-ttu-id="70a62-275">Conecte a saída, da parte inferior da **modelo de treinamento**, com a entrada do canto superior esquerdo do **modelo de pontuação**.</span><span class="sxs-lookup"><span data-stu-id="70a62-275">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="70a62-276">Conecte a saída do canto inferior direito da **dividir dados**, com a entrada do canto superior direito do \**modelo de pontuação* item \*.</span><span class="sxs-lookup"><span data-stu-id="70a62-276">Connect the bottom-right output from **Split Data**, to the top-right input of the \**Score Model* item\*.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="70a62-278">Na lista de **experimento** itens no painel à esquerda, expanda \* \**Machine Learning* > \* \* Evaluate**e arraste o **avaliar modelo \* \* item para a tela.</span><span class="sxs-lookup"><span data-stu-id="70a62-278">In the list of **Experiment** items in the panel on the left, expand \*\**Machine Learning* > \*Evaluate\***, and drag the **Evaluate Model\*\* item onto the canvas.</span></span>

18. <span data-ttu-id="70a62-279">Conecte a saída do **modelo de pontuação** para a entrada do canto superior esquerdo do **avaliar modelo**.</span><span class="sxs-lookup"><span data-stu-id="70a62-279">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="70a62-281">Você criou seu primeiro experimento de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="70a62-281">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="70a62-282">Agora você pode salvar e executar o teste.</span><span class="sxs-lookup"><span data-stu-id="70a62-282">You can now save and run the experiment.</span></span> <span data-ttu-id="70a62-283">No menu na parte inferior da página, clique no **salve** botão para salvar seu experimento e, em seguida, clique em **executar** para iniciar o teste.</span><span class="sxs-lookup"><span data-stu-id="70a62-283">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="70a62-285">Você pode ver os **status** do experimento no canto superior direito da tela.</span><span class="sxs-lookup"><span data-stu-id="70a62-285">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="70a62-286">Aguarde alguns instantes para que o teste a fim de concluir.</span><span class="sxs-lookup"><span data-stu-id="70a62-286">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="70a62-287">Se você tiver um conjunto de dados grande (reais), é provável que o teste pode levar horas para ser executado.</span><span class="sxs-lookup"><span data-stu-id="70a62-287">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="70a62-289">Clique com botão direito do **avaliar modelo** item na tela e de passagem do menu de contexto o mouse sobre **resultados da avaliação**, em seguida, selecione **visualizar**.</span><span class="sxs-lookup"><span data-stu-id="70a62-289">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="70a62-291">Os resultados da avaliação serão exibidos mostrando os resultados previstos versus os resultados reais.</span><span class="sxs-lookup"><span data-stu-id="70a62-291">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="70a62-292">Isso usa a 30% do conjunto de dados original, que foi dividido em versões anteriores, para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="70a62-292">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="70a62-293">Você pode ver que os resultados não são ótimos, o ideal é que você teria o número mais alto em cada linha ser o item realçado nas colunas.</span><span class="sxs-lookup"><span data-stu-id="70a62-293">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="70a62-295">Fechar o **resultados**.</span><span class="sxs-lookup"><span data-stu-id="70a62-295">Close the **Results**.</span></span>

24. <span data-ttu-id="70a62-296">Usar o modelo de Machine Learning treinado recentemente, você precisa para expô-lo como um **serviço Web**.</span><span class="sxs-lookup"><span data-stu-id="70a62-296">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="70a62-297">Para fazer isso, clique no **configurar o serviço Web** menu item no menu na parte inferior da página e clique em **serviço Web preditivo**.</span><span class="sxs-lookup"><span data-stu-id="70a62-297">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="70a62-299">Uma nova guia será criada e o modelo de treinamento são mesclados para criar o novo serviço web.</span><span class="sxs-lookup"><span data-stu-id="70a62-299">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="70a62-300">No menu na parte inferior da página, clique em **salve**, em seguida, clique em **executar**.</span><span class="sxs-lookup"><span data-stu-id="70a62-300">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span><span data-ttu-id="70a62-301"> Você verá o status seja atualizado no canto superior direito da tela do experimento.</span><span class="sxs-lookup"><span data-stu-id="70a62-301"> You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="70a62-303">Depois de terminar a execução, uma **implantar serviço Web** botão será exibido na parte inferior da página.</span><span class="sxs-lookup"><span data-stu-id="70a62-303">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="70a62-304">Você está pronto para implantar o serviço web.</span><span class="sxs-lookup"><span data-stu-id="70a62-304">You are ready to deploy the web service.</span></span> <span data-ttu-id="70a62-305">Clique em **implantar serviço Web** (clássico) no menu na parte inferior da página.</span><span class="sxs-lookup"><span data-stu-id="70a62-305">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="70a62-307">Pode solicitar que o navegador para permitir que um pop-up, você deve **permitem**, embora você talvez seja necessário pressionar **implantar serviço Web** novamente, se não mostrar a página de implantação.</span><span class="sxs-lookup"><span data-stu-id="70a62-307">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="70a62-308">Quando o teste tiver sido criado. você será redirecionado para um **Dashboard** página no qual você terá seu **chave de API** exibido.</span><span class="sxs-lookup"><span data-stu-id="70a62-308">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="70a62-309">Copie-o em um bloco de notas no momento, você precisará dele em seu código muito em breve.</span><span class="sxs-lookup"><span data-stu-id="70a62-309">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="70a62-310">Depois que você observou a sua chave de API, clique no **solicitação/resposta** botão na **ponto de extremidade padrão** seção sob a chave.</span><span class="sxs-lookup"><span data-stu-id="70a62-310">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="70a62-312">Se você clicar em teste nesta página, você poderá inserir dados de entrada e exibir a saída.</span><span class="sxs-lookup"><span data-stu-id="70a62-312">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="70a62-313">Insira o **dia** e **hora**.</span><span class="sxs-lookup"><span data-stu-id="70a62-313">Enter the **day** and **hour**.</span></span> <span data-ttu-id="70a62-314">Deixe o **produto** entrada em branco.</span><span class="sxs-lookup"><span data-stu-id="70a62-314">Leave the **product** entry blank.</span></span> <span data-ttu-id="70a62-315">Em seguida, clique o **confirmar** botão.</span><span class="sxs-lookup"><span data-stu-id="70a62-315">Then click the **Confirm** button.</span></span><span data-ttu-id="70a62-316"> A saída na parte inferior da página mostrará o JSON que representa a probabilidade de cada produto que está sendo a escolha.</span><span class="sxs-lookup"><span data-stu-id="70a62-316"> The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="70a62-317">Uma nova página da web será aberta, exibindo as instruções e alguns exemplos sobre a estrutura de solicitação necessários para o Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="70a62-317">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="70a62-318">Cópia de **URI de solicitação** exibidos nesta página, no seu bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="70a62-318">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="70a62-320">Você agora criou um sistema que fornece o produto mais provável de serem vendidos com base em dados históricos de compras, correlacionados com a hora do dia e dia do ano de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="70a62-320">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="70a62-321">Para chamar o serviço web, você precisará da URL para o ponto de extremidade de serviço e uma chave de API para o serviço.</span><span class="sxs-lookup"><span data-stu-id="70a62-321">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="70a62-322">Clique no **Consume** guia, no menu superior.</span><span class="sxs-lookup"><span data-stu-id="70a62-322">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="70a62-323">O **consumo** página de informações exibirá as informações que você precisará chamar o serviço web do seu código.</span><span class="sxs-lookup"><span data-stu-id="70a62-323">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="70a62-324">Faça uma cópia de **chave primária** e o **solicitação-resposta** URL.</span><span class="sxs-lookup"><span data-stu-id="70a62-324">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="70a62-325">Você precisará no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="70a62-325">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="70a62-326">Capítulo 5 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="70a62-326">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="70a62-327">Configurar e testar o fone imersivo realidade mista.</span><span class="sxs-lookup"><span data-stu-id="70a62-327">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="70a62-328">Você irá **não** exigem controladores de movimento para este curso.</span><span class="sxs-lookup"><span data-stu-id="70a62-328">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="70a62-329">Se você precisar dar suporte a configurar o fone de ouvido imersivo, clique em [aqui](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="70a62-329">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="70a62-330">Abra **Unity** e crie um novo projeto do Unity chamada **MR\_MachineLearning.**</span><span class="sxs-lookup"><span data-stu-id="70a62-330">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="70a62-331">Verifique se o tipo de projeto é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="70a62-331">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="70a62-332">Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="70a62-332">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="70a62-333">Vá para ***edite* > *preferências*** e, em seguida, na nova janela, navegue até **ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="70a62-333">Go to ***Edit* > *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="70a62-334">Alteração **Editor de Script externo** à **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="70a62-334">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="70a62-335">Fechar o **preferências** janela.</span><span class="sxs-lookup"><span data-stu-id="70a62-335">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="70a62-336">Em seguida, vá para ***arquivo* > *configurações de Build*** e alternar a plataforma **plataforma Universal do Windows**, clicando em o ***alternar plataforma*** botão.</span><span class="sxs-lookup"><span data-stu-id="70a62-336">Next, go to ***File* > *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="70a62-337">Também verifique se:</span><span class="sxs-lookup"><span data-stu-id="70a62-337">Also make sure that:</span></span>

    1.  <span data-ttu-id="70a62-338">**Dispositivo de destino** é definido como **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="70a62-338">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="70a62-339">Para o Microsoft HoloLens, defina **dispositivo de destino** à *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="70a62-339">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="70a62-340">**Tipo de compilação** é definido como **D3D**.</span><span class="sxs-lookup"><span data-stu-id="70a62-340">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="70a62-341">**SDK** é definido como **mais recente instalada**.</span><span class="sxs-lookup"><span data-stu-id="70a62-341">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="70a62-342">**Versão do Visual Studio** é definido como **mais recente instalada**.</span><span class="sxs-lookup"><span data-stu-id="70a62-342">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="70a62-343">**Compilar e executar** é definido como **computador Local**.</span><span class="sxs-lookup"><span data-stu-id="70a62-343">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="70a62-344">Não se preocupe sobre como configurar o **cenas** no momento, conforme eles são fornecidos posteriormente.</span><span class="sxs-lookup"><span data-stu-id="70a62-344">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="70a62-345">As configurações restantes devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="70a62-345">The remaining settings should be left as default for now.</span></span>

        ![Configurar o projeto do Unity](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="70a62-347">No **configurações de Build** janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o **Inspetor** está localizado.</span><span class="sxs-lookup"><span data-stu-id="70a62-347">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="70a62-348">Neste painel, algumas configurações precisam ser verificados:</span><span class="sxs-lookup"><span data-stu-id="70a62-348">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="70a62-349">No **outras configurações** guia:</span><span class="sxs-lookup"><span data-stu-id="70a62-349">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="70a62-350">**Criação de scripts** **versão de tempo de execução** deve ser **Experimental** (equivalente ao .NET 4.6)</span><span class="sxs-lookup"><span data-stu-id="70a62-350">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="70a62-351">**Script de back-end** deve ser ***.NET***</span><span class="sxs-lookup"><span data-stu-id="70a62-351">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="70a62-352">**Nível de compatibilidade de API** deve ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="70a62-352">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="70a62-354">Dentro de **configurações de publicação** guia, em **recursos**, verifique:</span><span class="sxs-lookup"><span data-stu-id="70a62-354">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="70a62-355">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="70a62-355">**InternetClient**</span></span>

            ![Configurar o projeto do Unity](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="70a62-357">Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado</span><span class="sxs-lookup"><span data-stu-id="70a62-357">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Configurar o projeto do Unity](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="70a62-359">Volta **configurações de Build** *Unity C#*  projetos não fica acinzentado; marque a caixa de seleção ao lado disso.</span><span class="sxs-lookup"><span data-stu-id="70a62-359">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="70a62-360">Feche a janela de configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="70a62-360">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="70a62-361">Salve seu projeto (**arquivo > Salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="70a62-361">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="70a62-362">Capítulos 6 - importar o pacote do Unity MLProducts</span><span class="sxs-lookup"><span data-stu-id="70a62-362">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="70a62-363">Para este curso, você precisará baixar um pacote do Unity Asset chamado [ **Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="70a62-363">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="70a62-364">Este pacote vem completo com uma cena, com todos os objetos no ou predefinidas, portanto, você pode focalizar obtendo-tudo em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="70a62-364">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="70a62-365">O **ShelfKeeper** script é fornecido, porém mantém apenas variáveis públicas, para fins de estrutura de configuração da cena.</span><span class="sxs-lookup"><span data-stu-id="70a62-365">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="70a62-366">Você precisará fazer todas as outras seções.</span><span class="sxs-lookup"><span data-stu-id="70a62-366">You will need to do all other sections.</span></span> 

<span data-ttu-id="70a62-367">Para importar este pacote:</span><span class="sxs-lookup"><span data-stu-id="70a62-367">To import this package:</span></span>

1.  <span data-ttu-id="70a62-368">Com o painel do Unity na sua frente, clique em **ativos** no menu na parte superior da tela, em seguida, clique em **Importar pacote, o pacote personalizado**.</span><span class="sxs-lookup"><span data-stu-id="70a62-368">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![Importe o pacote do Unity MLProducts](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="70a62-370">Use o seletor de arquivos para selecionar o **Azure-MR-307.unitypackage** de pacote e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="70a62-370">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="70a62-371">Uma lista de componentes para esse ativo será exibida para você.</span><span class="sxs-lookup"><span data-stu-id="70a62-371">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="70a62-372">Confirme a importação clicando **importação**.</span><span class="sxs-lookup"><span data-stu-id="70a62-372">Confirm the import by clicking **Import**.</span></span>

    ![Importe o pacote do Unity MLProducts](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="70a62-374">Quando tiver terminado a importação, você vai notar que algumas pastas novas apareceu no seu Unity **painel projeto**.</span><span class="sxs-lookup"><span data-stu-id="70a62-374">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="70a62-375">Esses são os modelos 3D e os respectivos materiais que fazem parte da cena predefinida, que você trabalhará na.</span><span class="sxs-lookup"><span data-stu-id="70a62-375">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="70a62-376">Você irá escrever a maioria do código neste curso.</span><span class="sxs-lookup"><span data-stu-id="70a62-376">You will write the majority of the code in this course.</span></span>

    ![Importe o pacote do Unity MLProducts](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="70a62-378">Dentro de **painel projeto** pasta, clique no **cenas** pasta e clique duas vezes na cena dentro (chamado **MR_MachineLearningScene**).</span><span class="sxs-lookup"><span data-stu-id="70a62-378">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="70a62-379">A cena será aberta (veja a imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="70a62-379">The scene will open (see image below).</span></span> <span data-ttu-id="70a62-380">Se os losangos vermelhos estiverem ausentes, basta clicar o **utensílios** botão na parte superior direita do **painel de jogo**.</span><span class="sxs-lookup"><span data-stu-id="70a62-380">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![Importe o pacote do Unity MLProducts](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="70a62-382">Capítulo 7 - verificando as DLLs no Unity</span><span class="sxs-lookup"><span data-stu-id="70a62-382">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="70a62-383">Para aproveitar o uso de bibliotecas JSON (usado para serializar e desserializar), uma DLL Newtonsoft tiver sido implementada com o pacote que é colocado no.</span><span class="sxs-lookup"><span data-stu-id="70a62-383">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="70a62-384">A biblioteca deve ter a configuração correta, embora vale a pena verificar (especialmente se você estiver tendo problemas com o código não está funcionando).</span><span class="sxs-lookup"><span data-stu-id="70a62-384">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="70a62-385">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="70a62-385">To do so:</span></span>

-  <span data-ttu-id="70a62-386">Clique no arquivo Newtonsoft dentro da pasta de plug-ins e examine os **painel Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="70a62-386">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="70a62-387">Certifique-se **qualquer plataforma** está marcada.</span><span class="sxs-lookup"><span data-stu-id="70a62-387">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="70a62-388">Vá para o **guia UWP** e certifique-se também **não processar** está marcada.</span><span class="sxs-lookup"><span data-stu-id="70a62-388">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Importando as DLLs no Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="70a62-390">Capítulo 8 - criar a classe ShelfKeeper</span><span class="sxs-lookup"><span data-stu-id="70a62-390">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="70a62-391">O **ShelfKeeper** classe hospeda métodos que controlam a interface do usuário e os produtos gerados na cena.</span><span class="sxs-lookup"><span data-stu-id="70a62-391">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="70a62-392">Como parte do pacote importado, você será receberam essa classe, embora ele está incompleto.</span><span class="sxs-lookup"><span data-stu-id="70a62-392">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="70a62-393">Agora é hora de conclusão dessa classe:</span><span class="sxs-lookup"><span data-stu-id="70a62-393">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="70a62-394">Clique duas vezes no **ShelfKeeper** script dentro de **Scripts** pasta para abri-lo com **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="70a62-394">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="70a62-395">Substitua todo o código existente no script com o código a seguir, que define a data e hora e tem um método para exibir um produto.</span><span class="sxs-lookup"><span data-stu-id="70a62-395">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

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

3.  <span data-ttu-id="70a62-396">Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="70a62-396">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="70a62-397">Novamente no Editor do Unity, verifique se o **ShelfKeeper** classe é semelhante a abaixo:</span><span class="sxs-lookup"><span data-stu-id="70a62-397">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![Criar a classe ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="70a62-399">Se o seu script não tem os destinos de referência (ou seja, *Data (texto de malha)*), basta arrastar os objetos correspondentes do **painel de hierarquia**, nos campos de destino.</span><span class="sxs-lookup"><span data-stu-id="70a62-399">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="70a62-400">Veja a seguir para obter explicação, se necessário:</span><span class="sxs-lookup"><span data-stu-id="70a62-400">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="70a62-401">Abra o **ponto Spawn** dentro da matriz a **ShelfKeeper** por left-clicking-lo de script do componente.</span><span class="sxs-lookup"><span data-stu-id="70a62-401">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="70a62-402">Uma subseção será exibida chamada **tamanho**, que indica o tamanho da matriz.</span><span class="sxs-lookup"><span data-stu-id="70a62-402">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="70a62-403">Tipo de **3** na caixa de texto próximo a **tamanho** e pressione **Enter**, e três slots serão criadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="70a62-403">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="70a62-404">Dentro de **hierarquia** expandir a **exibição de tempo** objeto (por left-clicking na seta ao lado dela).</span><span class="sxs-lookup"><span data-stu-id="70a62-404">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="70a62-405">Em seguida clique o ***câmera principal*** de dentro a **hierarquia**, de modo que o **Inspetor** mostra suas informações.</span><span class="sxs-lookup"><span data-stu-id="70a62-405">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="70a62-406">Selecione o **câmera principal** na **painel de hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="70a62-406">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="70a62-407">Arraste o **data** e **tempo** objetos do **painel de hierarquia** para o **texto data** e **texto de tempo de** slots dentro a **Inspector** da **câmera principal** no **ShelfKeeper** componente.</span><span class="sxs-lookup"><span data-stu-id="70a62-407">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="70a62-408">Arraste o **Spawn pontos** da **painel de hierarquia** (abaixo a *prateleira* objeto) para o **3** **elemento**referenciar destinos sob o **Spawn ponto** de matriz, conforme mostrado na imagem.</span><span class="sxs-lookup"><span data-stu-id="70a62-408">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![Criar a classe ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="70a62-410">Capítulo 9 - criar a classe ProductPrediction</span><span class="sxs-lookup"><span data-stu-id="70a62-410">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="70a62-411">A próxima classe que você pretende criar é a **ProductPrediction** classe.</span><span class="sxs-lookup"><span data-stu-id="70a62-411">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="70a62-412">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="70a62-412">This class is responsible for:</span></span>

-   <span data-ttu-id="70a62-413">Consultando o **serviço de Machine Learning** instância, o que fornece a data e hora atuais.</span><span class="sxs-lookup"><span data-stu-id="70a62-413">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="70a62-414">Desserializar a resposta JSON em dados utilizáveis.</span><span class="sxs-lookup"><span data-stu-id="70a62-414">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="70a62-415">Interpretando os dados, recuperando os 3 produtos recomendados.</span><span class="sxs-lookup"><span data-stu-id="70a62-415">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="70a62-416">Chamar o **ShelfKeeper** métodos para exibir os dados na cena de classe.</span><span class="sxs-lookup"><span data-stu-id="70a62-416">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="70a62-417">Para criar essa classe:</span><span class="sxs-lookup"><span data-stu-id="70a62-417">To create this class:</span></span>

1.  <span data-ttu-id="70a62-418">Vá para o **Scripts** pasta, no **painel projeto**.</span><span class="sxs-lookup"><span data-stu-id="70a62-418">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="70a62-419">Clique com botão direito dentro da pasta **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="70a62-419">Right-click inside the folder, **Create** > **C\# Script**.</span></span> <span data-ttu-id="70a62-420">Chame o script **ProductPrediction**.</span><span class="sxs-lookup"><span data-stu-id="70a62-420">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="70a62-421">Clique duas vezes na nova **ProductPrediction** script para abri-lo com **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="70a62-421">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="70a62-422">Se o **modificação de arquivo detectado** caixa de diálogo é exibida, clique em \***recarregar solução**.</span><span class="sxs-lookup"><span data-stu-id="70a62-422">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="70a62-423">Adicione os seguintes namespaces na parte superior da classe ProductPrediction:</span><span class="sxs-lookup"><span data-stu-id="70a62-423">Add the following namespaces to the top of the ProductPrediction class:</span></span>

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

6.  <span data-ttu-id="70a62-424">Dentro de **ProductPrediction** classe inserir os dois objetos a seguir, que são compostos de um número de classes aninhadas.</span><span class="sxs-lookup"><span data-stu-id="70a62-424">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="70a62-425">Essas classes são usadas para serializar e desserializar o JSON para o serviço de Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="70a62-425">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

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

7.  <span data-ttu-id="70a62-426">Em seguida, adicione as seguintes variáveis acima do código anterior (de modo que o JSON relacionados ao código é na parte inferior do script, todos os outros código abaixo e para fora do caminho):</span><span class="sxs-lookup"><span data-stu-id="70a62-426">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

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
    > <span data-ttu-id="70a62-427">Certifique-se de inserir o **chave primária** e **ponto de extremidade de solicitação-resposta**, do Portal de aprendizado de máquina para as variáveis aqui.</span><span class="sxs-lookup"><span data-stu-id="70a62-427">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="70a62-428">As imagens abaixo mostram onde você teria levado a chave e o ponto de extremidade de.</span><span class="sxs-lookup"><span data-stu-id="70a62-428">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="70a62-431">Inserir esse código dentro de **Start ()** método.</span><span class="sxs-lookup"><span data-stu-id="70a62-431">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="70a62-432">O **Start ()** método é chamado quando a classe é inicializado:</span><span class="sxs-lookup"><span data-stu-id="70a62-432">The **Start()** method is called when the class initializes:</span></span>

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

9.  <span data-ttu-id="70a62-433">Este é o método que coleta a data e hora do Windows e o converte em um formato que nosso teste de Machine Learning pode usar para comparar com os dados armazenados na tabela.</span><span class="sxs-lookup"><span data-stu-id="70a62-433">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

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

10. <span data-ttu-id="70a62-434">Você pode **exclua** as **Update ()** método uma vez que essa classe não irá usá-lo.</span><span class="sxs-lookup"><span data-stu-id="70a62-434">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="70a62-435">Adicione o seguinte método que irá comunicar-se a data e hora atuais para o ponto de extremidade do aprendizado de máquina e receber uma resposta no formato JSON.</span><span class="sxs-lookup"><span data-stu-id="70a62-435">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

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

12. <span data-ttu-id="70a62-436">Adicione o seguinte método, que é responsável para desserializar a resposta JSON e comunicando-se o resultado da desserialização para o **ShelfKeeper** classe.</span><span class="sxs-lookup"><span data-stu-id="70a62-436">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="70a62-437">Esse resultado será que os nomes dos três itens previstos para vender mais na data e hora atuais.</span><span class="sxs-lookup"><span data-stu-id="70a62-437">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="70a62-438">Insira o código abaixo para o **ProductPrediction** classe, abaixo do método anterior.</span><span class="sxs-lookup"><span data-stu-id="70a62-438">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

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

13. <span data-ttu-id="70a62-439">Salve **Visual Studio** e volte ao **Unity**.</span><span class="sxs-lookup"><span data-stu-id="70a62-439">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="70a62-440">Arraste o **ProductPrediction** script a partir de classe a **Script** pasta, para o **câmera principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="70a62-440">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="70a62-441">Salvar sua cena e seu projeto **arquivo** > ***salvar cena* / *arquivo***   >  **Salvar projeto**.</span><span class="sxs-lookup"><span data-stu-id="70a62-441">Save your scene and project **File** > ***Save Scene* / *File*** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="70a62-442">Capítulo 10 - Compile a solução UWP</span><span class="sxs-lookup"><span data-stu-id="70a62-442">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="70a62-443">Agora é hora de criar seu projeto como uma solução UWP, para que ele pode ser executado como um aplicativo autônomo.</span><span class="sxs-lookup"><span data-stu-id="70a62-443">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="70a62-444">Para construir:</span><span class="sxs-lookup"><span data-stu-id="70a62-444">To Build:</span></span>

1.  <span data-ttu-id="70a62-445">Salve a cena atual clicando em **arquivo** **cenas salvar**.</span><span class="sxs-lookup"><span data-stu-id="70a62-445">Save the current scene by clicking on **File** **Save Scenes**.</span></span>

2.  <span data-ttu-id="70a62-446">Vá para **arquivo** **configurações de Build**</span><span class="sxs-lookup"><span data-stu-id="70a62-446">Go to **File** **Build Settings**</span></span>

3.  <span data-ttu-id="70a62-447">Marque a caixa denominada **Unity C\# projetos** (Isso é importante porque ele permitirá que você editar as classes após a compilação for concluída).</span><span class="sxs-lookup"><span data-stu-id="70a62-447">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="70a62-448">Clique em **adicionar cenas abertas**,</span><span class="sxs-lookup"><span data-stu-id="70a62-448">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="70a62-449">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="70a62-449">Click **Build**.</span></span>

    ![Compile a solução UWP](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="70a62-451">Você será solicitado a selecionar a pasta onde você deseja criar a solução.</span><span class="sxs-lookup"><span data-stu-id="70a62-451">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="70a62-452">Criar uma **compilações** pasta e dentro dessa pasta, crie outra pasta com um nome apropriado de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="70a62-452">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="70a62-453">Clique em sua nova pasta e, em seguida, clique em **Selecionar pasta**, para iniciar a compilação nesse local.</span><span class="sxs-lookup"><span data-stu-id="70a62-453">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![Compile a solução UWP](images/AzureLabs-Lab7-55.png)

    ![Compile a solução UWP](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="70a62-456">Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um **Explorador de arquivos** janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).</span><span class="sxs-lookup"><span data-stu-id="70a62-456">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="70a62-457">Capítulo 11 - implantar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="70a62-457">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="70a62-458">Para implantar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="70a62-458">To deploy your application:</span></span>

1.  <span data-ttu-id="70a62-459">Navegue até seu novo build do Unity (o **App** pasta) e abra o arquivo de solução com **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="70a62-459">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="70a62-460">Com o Visual Studio aberta, você precisa restaurar pacotes do NuGet, que pode ser feito por meio de sua solução MachineLearningLab_Build, do Gerenciador de soluções (localizado à direita do Visual Studio), botão direito do mouse e, em seguida, clicando em Restaurar pacotes do NuGet:</span><span class="sxs-lookup"><span data-stu-id="70a62-460">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![Adicionar pacotes NuGet](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="70a62-462">No, selecione a configuração da solução **depurar**.</span><span class="sxs-lookup"><span data-stu-id="70a62-462">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="70a62-463">Na plataforma da solução, selecione **x86**, **Máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="70a62-463">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="70a62-464">Para o Microsoft HoloLens, talvez você ache mais fácil de definir isso como *máquina remota*, de modo que você não estiver vinculado ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="70a62-464">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="70a62-465">No entanto, você precisará também fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="70a62-465">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="70a62-466">Saber a **endereço IP** de seu HoloLens, que podem ser encontrado dentro a *Configurações > rede e Internet > Wi-Fi > Opções avançadas de*; o IPv4 é o endereço que você deve usar.</span><span class="sxs-lookup"><span data-stu-id="70a62-466">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="70a62-467">Certifique-se **modo de desenvolvedor** é **na**; encontrado na *Configurações > atualização e segurança > para os desenvolvedores*.</span><span class="sxs-lookup"><span data-stu-id="70a62-467">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Adicionar pacotes NuGet](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="70a62-469">Vá para **menu Build** e clique em **implantar solução** para carregar o aplicativo a seu computador.</span><span class="sxs-lookup"><span data-stu-id="70a62-469">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="70a62-470">Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="70a62-470">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="70a62-471">Quando você executa o aplicativo de realidade misturada, você verá o banco que foi definido na sua cena do Unity e de inicialização, os dados que você configurar no Azure serão buscados.</span><span class="sxs-lookup"><span data-stu-id="70a62-471">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="70a62-472">Os dados serão desserializados dentro de seu aplicativo e os três primeiros resultados para a data e hora atuais serão fornecidos visualmente, como três modelos sobre o banco.</span><span class="sxs-lookup"><span data-stu-id="70a62-472">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="70a62-473">O aplicativo de aprendizado de máquina concluído</span><span class="sxs-lookup"><span data-stu-id="70a62-473">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="70a62-474">Parabéns, você criou um aplicativo de realidade mista que aproveita o Azure Machine Learning para fazer previsões de dados e exibi-lo na sua cena.</span><span class="sxs-lookup"><span data-stu-id="70a62-474">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![Adicionar pacotes NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="70a62-476">Exercício</span><span class="sxs-lookup"><span data-stu-id="70a62-476">Exercise</span></span>

<span data-ttu-id="70a62-477">**Exercício 1**</span><span class="sxs-lookup"><span data-stu-id="70a62-477">**Exercise 1**</span></span>

<span data-ttu-id="70a62-478">Fazer experiências com a ordem de classificação do seu aplicativo e ter as previsões de três inferior são exibidos na prateleira, como esses dados potencialmente seria útil também.</span><span class="sxs-lookup"><span data-stu-id="70a62-478">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="70a62-479">**Exercício 2**</span><span class="sxs-lookup"><span data-stu-id="70a62-479">**Exercise 2**</span></span>

<span data-ttu-id="70a62-480">Usando o **tabelas do Azure** popular uma nova tabela com informações meteorológicas e criar um novo experimento usando os dados.</span><span class="sxs-lookup"><span data-stu-id="70a62-480">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
