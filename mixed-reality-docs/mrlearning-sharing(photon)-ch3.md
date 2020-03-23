---
title: Tutoriais de recursos multiusuário – 3. Como conectar vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031226"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="5034d-105">3. Como conectar vários usuários</span><span class="sxs-lookup"><span data-stu-id="5034d-105">3. Connecting multiple users</span></span>

<span data-ttu-id="5034d-106">Nesta lição, aprenderemos a conectar vários usuários como parte de uma experiência compartilhada ao vivo.</span><span class="sxs-lookup"><span data-stu-id="5034d-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="5034d-107">Ao final desta lição, você poderá abrir o aplicativo em vários dispositivos e ver o avatar, representado por uma esfera, para cada pessoa que entra.</span><span class="sxs-lookup"><span data-stu-id="5034d-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span>

## <a name="objectives"></a><span data-ttu-id="5034d-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5034d-108">Objectives</span></span>

* <span data-ttu-id="5034d-109">Configurar o PUN em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="5034d-109">Configure PUN within your application</span></span>
* <span data-ttu-id="5034d-110">Configurar jogadores</span><span class="sxs-lookup"><span data-stu-id="5034d-110">Configure players</span></span>
* <span data-ttu-id="5034d-111">Saiba como conectar vários usuários em uma experiência compartilhada</span><span class="sxs-lookup"><span data-stu-id="5034d-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="5034d-112">Instruções</span><span class="sxs-lookup"><span data-stu-id="5034d-112">Instructions</span></span>

1. <span data-ttu-id="5034d-113">Na pasta Ativos->Recursos->Pré-fabricados do painel Projeto, arraste e solte o pré-fabricado NetworkLobby para a hierarquia, conforme mostra a imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="5034d-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="5034d-115">Ao expandir NetworkLobby, você verá um objeto filho chamado NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="5034d-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="5034d-116">Com NetworkRoom selecionado, vá para o painel Inspetor e clique em Adicionar Componente.</span><span class="sxs-lookup"><span data-stu-id="5034d-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="5034d-117">Procure PhotonView e adicione o componente.</span><span class="sxs-lookup"><span data-stu-id="5034d-117">Search for PhotonView and add the component.</span></span>

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="5034d-119">Crie um objeto de jogo vazio na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="5034d-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="5034d-120">Clique com o botão direito do mouse na hierarquia e selecione Vazio no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="5034d-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="5034d-121">Verifique se o posicionamento está definido como x=0, y=0, z=0 e dê ao objeto o nome de PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="5034d-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="5034d-123">Clique em Adicionar Componente e digite Generic Net Sync. Selecione a classe Generic Net Sync.</span><span class="sxs-lookup"><span data-stu-id="5034d-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="5034d-124">Quando a classe for exibida, clique na caixa de seleção do usuário para ativá-la.</span><span class="sxs-lookup"><span data-stu-id="5034d-124">When the class appears, click the User check box to turn it on.</span></span>

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="5034d-126">Clique em Adicionar Componente outra vez e digite Exibição do Photon.</span><span class="sxs-lookup"><span data-stu-id="5034d-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="5034d-127">Selecione a classe de Exibição do Photon que aparece na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="5034d-127">Select the Photon View class that appears in the drop-down list.</span></span>

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="5034d-129">Clique no ícone Arquivo para a classe Generic Net Sync.</span><span class="sxs-lookup"><span data-stu-id="5034d-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="5034d-130">Arraste e solte-o no campo Componentes Observados da Exibição do Photon.</span><span class="sxs-lookup"><span data-stu-id="5034d-130">Drag and drop it in the Photon View's Observed Components field.</span></span>

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. <span data-ttu-id="5034d-132">Em seguida, criamos esferas para representar cada pessoa que entra para uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="5034d-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="5034d-133">Clique com o botão direito do mouse no objeto PhotonUser que você acabou de criar, role para baixo até "Objeto 3D" e clique em Esfera.</span><span class="sxs-lookup"><span data-stu-id="5034d-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="5034d-134">Isso criará um objeto de jogo de esfera como um filho do objeto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="5034d-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="5034d-136">Dimensione a esfera para baixo para x=0,06, y=0,06, ad z=0,06.</span><span class="sxs-lookup"><span data-stu-id="5034d-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="5034d-138">Arraste o objeto de jogo PhotonUser para a pasta Pré-Fabricados no painel Projeto e, em seguida, exclua-o da cena.</span><span class="sxs-lookup"><span data-stu-id="5034d-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="5034d-139">Agora você criou um pré-fabricado que pode ser usado ao gerar ou criar uma instância de novos jogadores em uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="5034d-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    ><span data-ttu-id="5034d-141">Verifique se o objeto de jogo foi copiado com êxito para a pasta Pré-Fabricados antes de excluí-lo da sua hierarquia.</span><span class="sxs-lookup"><span data-stu-id="5034d-141">Ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="5034d-142">Crie um objeto na hierarquia seguindo as instruções na etapa 3 e dê a ele o nome de SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="5034d-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="5034d-143">Em seguida, clique em Adicionar Componente e pesquise o gerenciador de rede genérico.</span><span class="sxs-lookup"><span data-stu-id="5034d-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="5034d-144">Clique novamente para adicionar o componente Gerenciador de Rede Genérico.</span><span class="sxs-lookup"><span data-stu-id="5034d-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="5034d-145">Altere a posição do objeto para x=0, y=0 e z=0.</span><span class="sxs-lookup"><span data-stu-id="5034d-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a><span data-ttu-id="5034d-147">Parabéns</span><span class="sxs-lookup"><span data-stu-id="5034d-147">Congratulations</span></span>

<span data-ttu-id="5034d-148">Depois que todas as etapas acima e o processo de build também forem concluídos, pressione o botão Reproduzir e conecte seu HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5034d-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="5034d-149">Você deverá ver uma esfera se movimentando à medida que move a cabeça.</span><span class="sxs-lookup"><span data-stu-id="5034d-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="5034d-150">Isso será mostrado para qualquer usuário que ingressar em seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="5034d-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="5034d-151">[Próxima lição: 4. Compartilhar movimentações de objeto com vários usuários](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="5034d-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>
