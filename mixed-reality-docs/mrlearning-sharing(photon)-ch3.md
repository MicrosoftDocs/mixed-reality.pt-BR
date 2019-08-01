---
title: Tutoriais de funcionalidades de vários usuários-3. Conectando vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: d3068a1ebbbc2b6db8b563be8bf8c6e488e9491a
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701937"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="6d0f5-105">3. Conectando vários usuários</span><span class="sxs-lookup"><span data-stu-id="6d0f5-105">3. Connecting multiple users</span></span>

<span data-ttu-id="6d0f5-106">Nesta lição, aprenderemos como conectar vários usuários como parte de uma experiência compartilhada ao vivo.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="6d0f5-107">Ao final desta lição, você poderá abrir o aplicativo em vários dispositivos e ver o Avatar, representado por uma esfera, representações de cada pessoa que ingressar.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-107">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="6d0f5-108">Seus</span><span class="sxs-lookup"><span data-stu-id="6d0f5-108">Objectives:</span></span>

- <span data-ttu-id="6d0f5-109">Configurar o trocadilho em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="6d0f5-109">Configure PUN within your application</span></span>
- <span data-ttu-id="6d0f5-110">Configurar players</span><span class="sxs-lookup"><span data-stu-id="6d0f5-110">Configure players</span></span>
- <span data-ttu-id="6d0f5-111">Saiba como conectar vários usuários em uma experiência compartilhada</span><span class="sxs-lookup"><span data-stu-id="6d0f5-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="6d0f5-112">Instruções</span><span class="sxs-lookup"><span data-stu-id="6d0f5-112">Instructions</span></span>

1. <span data-ttu-id="6d0f5-113">Na pasta ativos-> recursos-> pré-fabricados no painel projeto, arraste e solte o NetworkLobby pré-fabricado para a hierarquia, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-113">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="6d0f5-115">Ao expandir NetworkLobby, você verá um objeto filho chamado NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="6d0f5-116">Com NetworkRoom selecionado, vá para o painel Inspetor e clique em Adicionar componente.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-116">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="6d0f5-117">Procure PhotonView e adicione o componente.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-117">Search for PhotonView and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="6d0f5-119">Crie um novo objeto de jogo vazio na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="6d0f5-120">Clique com o botão direito do mouse na hierarquia e selecione vazio no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-120">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="6d0f5-121">Verifique se o posicionamento está definido como x = 0, y = 0, z = 0 e nomeie o objeto, PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="6d0f5-123">Clique em Adicionar componente e digite sincronização de rede genérica. Selecione a classe genérica net Sync.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-123">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="6d0f5-124">Quando a classe for exibida, clique na caixa de seleção do usuário para ativá-la.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-124">When the class appears, click on the User check box to turn it on.</span></span> 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="6d0f5-126">Clique em Adicionar componente novamente e digite Photon exibição.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-126">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="6d0f5-127">Selecione a classe de exibição Photon que aparece na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-127">Select the Photon View class that appears in the drop-down list.</span></span>

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="6d0f5-129">Clique no ícone de arquivo para a classe genérica net Sync.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="6d0f5-130">Arraste e solte-o no campo componentes observados da exibição de Photon.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-130">Drag and drop it in the Photon View's Observed Components field.</span></span> 

![module3chapter3updateStep6im. png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="6d0f5-132">Em seguida, criamos um aqui para representar cada pessoa que une uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="6d0f5-133">Clique com o botão direito do mouse no objeto PhotonUser que você acabou de criar e scrolldown para "objeto 3D e clique em esfera.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-133">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="6d0f5-134">Isso criará um objeto de jogo de esfera como um filho do objeto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="6d0f5-136">Dimensione a esfera para baixo para x = 0.06, y = 0.06, AD z = 0.06.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="6d0f5-138">Arraste o objeto de jogo PhotonUser para a pasta pré-fabricados no painel projeto e, em seguida, exclua-o da cena.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="6d0f5-139">Agora, criamos um pré-fabricado que pode ser usado ao gerar ou criar uma instância de novos jogadores em uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-139">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="6d0f5-141">Observação: Verifique se o objeto de jogo foi copiado com êxito na pasta pré-fabricados antes de excluí-lo da sua hierarquia.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-141">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="6d0f5-142">Crie um novo objeto na hierarquia seguindo as instruções na etapa 3 e nomeie-o SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-142">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="6d0f5-143">Em seguida, clique em Adicionar componente e pesquise Gerenciador de rede genérico e clique nele para adicionar o componente do Gerenciador de rede genérico.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-143">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="6d0f5-144">Altere a posição do objeto para x = 0, y = 0 e z = 0.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-144">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="6d0f5-146">Parabéns</span><span class="sxs-lookup"><span data-stu-id="6d0f5-146">Congratulations</span></span>

<span data-ttu-id="6d0f5-147">Depois que todas as etapas acima forem concluídas e o processo de compilação também for concluído, pressione o botão reproduzir e conecte seu HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-147">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="6d0f5-148">Você deve ver uma esfera se movimentando à medida que move sua cabeça.</span><span class="sxs-lookup"><span data-stu-id="6d0f5-148">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="6d0f5-149">Isso será mostrado para qualquer usuário que ingressar em seu projeto do Unity!</span><span class="sxs-lookup"><span data-stu-id="6d0f5-149">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="6d0f5-150">[Próxima lição: 4. Compartilhar movimentações de objeto com vários usuários](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="6d0f5-150">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>

