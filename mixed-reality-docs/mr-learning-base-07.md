---
title: Tutoriais de introdução – 7. Como interagir com objetos 3D
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8920b35d1583777b86bc82868bb90338e25298e2
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303922"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="745d4-105">7. Como interagir com objetos 3D</span><span class="sxs-lookup"><span data-stu-id="745d4-105">7. Interacting with 3D objects</span></span>

<span data-ttu-id="745d4-106">Neste tutorial, você aprenderá a habilitar a manipulação próxima e distante de objetos 3D e limitar os tipos de manipulação permitidos.</span><span class="sxs-lookup"><span data-stu-id="745d4-106">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="745d4-107">Você também aprenderá a adicionar caixas delimitadoras em objetos 3D para facilitar o controle da manipulação de objetos.</span><span class="sxs-lookup"><span data-stu-id="745d4-107">You will also learn how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="745d4-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="745d4-108">Objectives</span></span>

* <span data-ttu-id="745d4-109">Saber como configurar objetos 3D para interagir com eles</span><span class="sxs-lookup"><span data-stu-id="745d4-109">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="745d4-110">Saber como adicionar caixas delimitadoras a objetos 3D</span><span class="sxs-lookup"><span data-stu-id="745d4-110">Learn how to add bounding boxes to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="745d4-111">Como manipular objetos 3D</span><span class="sxs-lookup"><span data-stu-id="745d4-111">Manipulating 3D objects</span></span>

<span data-ttu-id="745d4-112">Nesta seção, você adicionará a capacidade de manipular todas as peças do Rover organizadas na tabela durante o tutorial [Como posicionar objetos na cena](mr-learning-base-04.md).</span><span class="sxs-lookup"><span data-stu-id="745d4-112">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="745d4-113">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="745d4-113">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="745d4-114">Adicionar o componente Object Manipulator (Script) a todos os objetos de peças</span><span class="sxs-lookup"><span data-stu-id="745d4-114">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="745d4-115">Adicionar o componente NearInteractionGrabbable a todos os objetos de peças</span><span class="sxs-lookup"><span data-stu-id="745d4-115">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="745d4-116">Configurar o componente Object Manipulator (Script)</span><span class="sxs-lookup"><span data-stu-id="745d4-116">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="745d4-117">Para poder **manipular um objeto**, o objeto deve ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="745d4-117">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="745d4-118">Componente **Colisor**, por exemplo, um Colisor de Caixa</span><span class="sxs-lookup"><span data-stu-id="745d4-118">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="745d4-119">Componente **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="745d4-119">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="745d4-120">Para poder **manipular** e **capturar um objeto com as mãos acompanhadas**, o objeto deve ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="745d4-120">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="745d4-121">Componente **Colisor**, por exemplo, um Colisor de Caixa</span><span class="sxs-lookup"><span data-stu-id="745d4-121">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="745d4-122">Componente **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="745d4-122">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="745d4-123">Componente **NearInteractionGrabbable**</span><span class="sxs-lookup"><span data-stu-id="745d4-123">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="745d4-124">Além disso, você vai configurar o Rover Explorer para poder colocar as peças no Rover e montá-lo completamente.</span><span class="sxs-lookup"><span data-stu-id="745d4-124">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="745d4-125">Na janela Hierarquia, expanda o objeto RoverExplorer > **RoverParts** e selecione todos os seus objetos filho peças do Rover e o objeto **RoverAssembly**; em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar os seguintes componentes a todos os objetos selecionados:</span><span class="sxs-lookup"><span data-stu-id="745d4-125">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="745d4-126">Componente **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="745d4-126">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="745d4-127">Componente **NearInteractionGrabbable**</span><span class="sxs-lookup"><span data-stu-id="745d4-127">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="745d4-128">Componente **Part Assembly Controller (Script)**</span><span class="sxs-lookup"><span data-stu-id="745d4-128">**Part Assembly Controller (Script)** component</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="745d4-130">Para selecionar vários objetos que não estão próximos uns dos outros, mantenha a tecla CTRL pressionada e use o mouse para selecionar qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="745d4-130">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="745d4-131">Para os fins deste tutorial, os colisores já foram adicionados às peças do Rover.</span><span class="sxs-lookup"><span data-stu-id="745d4-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="745d4-132">Para saber mais sobre os colisores, acesse a documentação do <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Colisor</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="745d4-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="745d4-133">O Part Assembly Controller (Script) não faz parte do MRTK, mas foi incluído nos ativos do tutorial.</span><span class="sxs-lookup"><span data-stu-id="745d4-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="745d4-134">Com todos os objetos de peças do Rover e o objeto RoverAssembly ainda selecionados, na janela Inspetor, configure o componente **Object Manipulator (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="745d4-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="745d4-135">Na lista suspensa **Tipo de Manipulação de Duas Mãos**, desmarque a Escala, deixando somente **Mover** e **Girar** habilitados</span><span class="sxs-lookup"><span data-stu-id="745d4-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="745d4-137">Até agora você habilitou a manipulação de objetos para todos os objetos de peças do Rover e o objeto RoverAssembly.</span><span class="sxs-lookup"><span data-stu-id="745d4-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="745d4-138">Na janela Projeto, navegue até a pasta **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** para localizar os clipes de áudio:</span><span class="sxs-lookup"><span data-stu-id="745d4-138">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** folder to locate the audio clips:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="745d4-140">Na janela Hierarquia, selecione novamente todos os **objetos de peças do Rover** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Audio Sources**, configurando-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="745d4-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="745d4-141">Atribua o clipe de áudio **MRTK_Scale_Start** ao campo **AudioClip**</span><span class="sxs-lookup"><span data-stu-id="745d4-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="745d4-142">Desmarque a caixa de seleção **Reproduzir ao Ativar**</span><span class="sxs-lookup"><span data-stu-id="745d4-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="745d4-143">Altere **Spatial Blend** para 1</span><span class="sxs-lookup"><span data-stu-id="745d4-143">Change **Spatial Blend** to 1</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="745d4-145">Na janela Hierarquia, expanda o objeto RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** para revelar todos os objetos de dica de posicionamento e, em seguida, selecione a primeira peça do Rover, RoverParts > **Camera_Part** e configure o componente **Part Assembly Controller (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="745d4-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="745d4-146">Atribua o objeto **Camera_PlacementHint** ao campo **Location To Place**</span><span class="sxs-lookup"><span data-stu-id="745d4-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="745d4-148">**Repita** esta etapa para cada um dos objetos de peças do Rover restantes e o objeto RoverAssembly para configurar o componente **Part Assembly Controller (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="745d4-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="745d4-149">Para o **Generator_Part**, atribua o objeto **Generator_PlacementHint** ao campo **Location To Place**</span><span class="sxs-lookup"><span data-stu-id="745d4-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="745d4-150">Para o **Lights_Part**, atribua o objeto **Lights_PlacementHint** ao campo **Location To Place**</span><span class="sxs-lookup"><span data-stu-id="745d4-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="745d4-151">Para o **UHFAntenna_Part**, atribua o objeto **UHFAntenna_PlacementHint** ao campo **Location To Place**</span><span class="sxs-lookup"><span data-stu-id="745d4-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="745d4-152">Para o **Spectrometer_Part**, atribua o objeto **Spectrometer_PlacementHint** ao campo **Location To Place**</span><span class="sxs-lookup"><span data-stu-id="745d4-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="745d4-153">Para o **RoverAssembly**, atribua o objeto em si, ou seja, o mesmo objeto **RoverAssembly**, para o campo **Location To Place**</span><span class="sxs-lookup"><span data-stu-id="745d4-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="745d4-154">Na janela Hierarquia, selecione o botão RoverExplorer > Botões > **Redefinir** e, na janela Inspetor, configure o evento **OnClick ()** interativo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="745d4-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="745d4-155">Atribua o objeto **RoverAssembly** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="745d4-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="745d4-156">Na lista suspensa **Sem Função**, selecione **PartAssemblyController** > **ResetPlacement ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="745d4-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="745d4-158">Se agora você entrar no modo de Jogo, poderá usar a interação próxima ou distante para posicionar as peças no Rover.</span><span class="sxs-lookup"><span data-stu-id="745d4-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="745d4-159">Depois que a parte estiver próxima da dica de posicionamento correspondente, ela será encaixada no local e se tornará parte do Rover.</span><span class="sxs-lookup"><span data-stu-id="745d4-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="745d4-160">Para redefinir os posicionamentos, pressione o botão Reset:</span><span class="sxs-lookup"><span data-stu-id="745d4-160">To reset the placements, you can press the Reset button:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="745d4-162">Para saber mais sobre o componente Object Manipulator e suas propriedades associadas, acesse o guia [Manipulador de Objeto](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="745d4-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="745d4-163">Como adicionar caixas delimitadoras</span><span class="sxs-lookup"><span data-stu-id="745d4-163">Adding bounding boxes</span></span>

<span data-ttu-id="745d4-164">As caixas delimitadoras tornam mais fácil e mais intuitivo manipular objetos com uma mão para interação próxima e distante fornecendo alças que podem ser usadas para dimensionamento e rotação.</span><span class="sxs-lookup"><span data-stu-id="745d4-164">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="745d4-165">Neste exemplo, você adicionará uma caixa delimitadora ao objeto RoverExplorer para que toda a experiência seja facilmente movida, girada e dimensionada.</span><span class="sxs-lookup"><span data-stu-id="745d4-165">In this example, you will add a bounding box to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="745d4-166">Além disso, você vai configurar o Menu para poder ativar e desativar a Caixa Delimitadora.</span><span class="sxs-lookup"><span data-stu-id="745d4-166">Additionally, you will configure the Menu so you can turn the Bounding Box on and off.</span></span>

<span data-ttu-id="745d4-167">Na janela Hierarquia, selecione o objeto **RoverExplorer** e, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="745d4-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="745d4-168">Componente **BoundingBox**</span><span class="sxs-lookup"><span data-stu-id="745d4-168">**BoundingBox** component</span></span>
* <span data-ttu-id="745d4-169">Componente **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="745d4-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="745d4-170">Em seguida, **desmarque** a caixa de seleção próxima dos dois componentes para deixá-los **desabilitados** por padrão:</span><span class="sxs-lookup"><span data-stu-id="745d4-170">Then **uncheck** the checkbox next to both components to make them **disabled** by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="745d4-172">A visualização da Caixa Delimitadora é criada em runtime e, portanto, não fica visível até que você entre no modo de Jogo.</span><span class="sxs-lookup"><span data-stu-id="745d4-172">The Bounding Box visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
> <span data-ttu-id="745d4-173">O componente BoundingBox adicionará automaticamente o componente NearInteractionGrabbable em runtime.</span><span class="sxs-lookup"><span data-stu-id="745d4-173">The BoundingBox component will automatically add the NearInteractionGrabbable component at runtime.</span></span> <span data-ttu-id="745d4-174">Portanto, não precisamos adicionar esse componente para pegar os objetos delimitados com as mãos controladas.</span><span class="sxs-lookup"><span data-stu-id="745d4-174">Therefore, we do not need to add this component to grab the enclosed objects with tracked hands.</span></span>

<span data-ttu-id="745d4-175">Na janela Hierarquia, expanda o objeto Menu > **ButtonCollection** para revelar os quatro botões e renomeie o terceiro botão para **BoundingBox_Enable**; em seguida, na janela Inspetor, configure o componente **Button Config Helper (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="745d4-175">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundingBox_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="745d4-176">Altere o **Texto do Rótulo Principal** para **Habilitado**</span><span class="sxs-lookup"><span data-stu-id="745d4-176">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="745d4-177">Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="745d4-177">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="745d4-178">Na lista suspensa **Sem Função**, selecione **BoundingBox** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="745d4-178">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="745d4-179">Verifique se a caixa de seleção do argumento está **marcada**</span><span class="sxs-lookup"><span data-stu-id="745d4-179">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="745d4-180">Clique no ícone pequeno **+** para adicionar outro evento</span><span class="sxs-lookup"><span data-stu-id="745d4-180">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="745d4-181">Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="745d4-181">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="745d4-182">Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="745d4-182">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="745d4-183">Verifique se a caixa de seleção do argumento está **marcada**</span><span class="sxs-lookup"><span data-stu-id="745d4-183">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="745d4-184">Deixe o **Ícone** como o ícone de "cubo com caixa delimitadora"</span><span class="sxs-lookup"><span data-stu-id="745d4-184">Leave the **Icon** as the 'cube with bounding box' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="745d4-186">Renomeie o quarto e último botão como **BoundingBox_Disable** e, na janela Inspetor, configure o componente **Button Config Helper (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="745d4-186">Rename the forth and last button to **BoundingBox_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="745d4-187">Altere o **Texto do Rótulo Principal** para **Desabilitado**</span><span class="sxs-lookup"><span data-stu-id="745d4-187">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="745d4-188">Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="745d4-188">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="745d4-189">Na lista suspensa **Sem Função**, selecione **BoundingBox** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="745d4-189">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="745d4-190">Verifique se a caixa de seleção do argumento está **desmarcada**</span><span class="sxs-lookup"><span data-stu-id="745d4-190">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="745d4-191">Clique no ícone pequeno **+** para adicionar outro evento</span><span class="sxs-lookup"><span data-stu-id="745d4-191">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="745d4-192">Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="745d4-192">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="745d4-193">Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="745d4-193">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="745d4-194">Verifique se a caixa de seleção do argumento está **desmarcada**</span><span class="sxs-lookup"><span data-stu-id="745d4-194">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="745d4-195">Altere o **Ícone** para o ícone de "cubo com caixa delimitadora"</span><span class="sxs-lookup"><span data-stu-id="745d4-195">Change the **Icon** to the 'cube with bounding box" icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="745d4-197">Se agora você entrar no modo de Jogo e habilitar a Caixa Delimitadora clicando no botão Enable, poderá usar a interação próxima ou distante para mover, girar e dimensionar a Caixa Delimitadora e usar o botão Disable para desabilitar a Caixa Delimitadora novamente:</span><span class="sxs-lookup"><span data-stu-id="745d4-197">If you now enter Game mode and enable the Bounding Box by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounding Box, and use the Disable button to disable the Bounding Box again:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="745d4-199">Para saber mais sobre o componente de Caixa Delimitadora e suas propriedades associadas, acesse o guia da [Caixa Delimitadora](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="745d4-199">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="745d4-200">Parabéns</span><span class="sxs-lookup"><span data-stu-id="745d4-200">Congratulations</span></span>

<span data-ttu-id="745d4-201">Neste tutorial, você aprendeu como habilitar a manipulação próxima e distante de objetos 3D e como limitar os tipos de manipulação permitidos.</span><span class="sxs-lookup"><span data-stu-id="745d4-201">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="745d4-202">Você também aprendeu como adicionar caixas delimitadoras em objetos 3D para facilitar o controle da manipulação de objetos.</span><span class="sxs-lookup"><span data-stu-id="745d4-202">You also learned how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

[<span data-ttu-id="745d4-203">Próximo tutorial: 8. Como usar o acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="745d4-203">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
