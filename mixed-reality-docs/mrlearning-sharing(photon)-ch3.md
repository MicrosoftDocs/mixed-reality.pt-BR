---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 44cc41b10ed79d3085ec601ec9cf21af47b0fea5
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523310"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="2745e-104">Conectar-se vários usuários</span><span class="sxs-lookup"><span data-stu-id="2745e-104">Connecting multiple users</span></span>

<span data-ttu-id="2745e-105">Nesta lição, aprendemos como se conectar a vários usuários como parte de uma experiência de compartilhada em tempo real.</span><span class="sxs-lookup"><span data-stu-id="2745e-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="2745e-106">No final desta lição, você poderá abrir o aplicativo em vários dispositivos e ver o avatar, representado por uma esfera, representações de cada pessoa que une.</span><span class="sxs-lookup"><span data-stu-id="2745e-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="2745e-107">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="2745e-107">Objectives:</span></span>

- <span data-ttu-id="2745e-108">Configurar o TROCADILHO dentro de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2745e-108">Configure PUN within your application</span></span>
- <span data-ttu-id="2745e-109">Configurar os jogadores</span><span class="sxs-lookup"><span data-stu-id="2745e-109">Configure players</span></span>
- <span data-ttu-id="2745e-110">Saiba como se conectar a vários usuários em uma experiência de compartilhado</span><span class="sxs-lookup"><span data-stu-id="2745e-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="2745e-111">Instruções</span><span class="sxs-lookup"><span data-stu-id="2745e-111">Instructions</span></span>

1. <span data-ttu-id="2745e-112">Os ativos -> recursos -> pasta pré-fabricados no painel de projeto, arraste e solte pré-fabricado NetworkLobby à hierarquia, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="2745e-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="2745e-114">Quando você expande NetworkLobby, você verá um objeto filho chamado NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="2745e-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="2745e-115">Com NetworkRoom selecionado, vá para o painel do Inspetor e clique em Adicionar componente.</span><span class="sxs-lookup"><span data-stu-id="2745e-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="2745e-116">Pesquisar PhotonView e adicione o componente.</span><span class="sxs-lookup"><span data-stu-id="2745e-116">Search for PhotonView and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="2745e-118">Crie um novo objeto jogo vazio na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="2745e-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="2745e-119">Clique com o botão direito na hierarquia e selecione vazio no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="2745e-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="2745e-120">Verifique se o posicionamento é definido como x = 0, y = 0, z = 0 e nomear o objeto, PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="2745e-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="2745e-122">Clique em Adicionar componente e de tipo genérico de sincronização de Net. Selecione a classe genérica sincronização Net.</span><span class="sxs-lookup"><span data-stu-id="2745e-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="2745e-123">Quando a classe for exibida, clique na caixa de seleção do usuário para ativá-lo.</span><span class="sxs-lookup"><span data-stu-id="2745e-123">When the class appears, click on the User check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="2745e-125">Clique em Adicionar componente novamente e digite Photon exibição.</span><span class="sxs-lookup"><span data-stu-id="2745e-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="2745e-126">Selecione a classe de exibição Photon que aparece na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="2745e-126">Select the Photon View class that appears in the drop-down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="2745e-128">Clique no ícone de arquivo para a classe genérica sincronização Net.</span><span class="sxs-lookup"><span data-stu-id="2745e-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="2745e-129">Arraste e solte-o no campo de componentes observada Photon da exibição.</span><span class="sxs-lookup"><span data-stu-id="2745e-129">Drag and drop it in the Photon View's Observed Components field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="2745e-131">Em seguida, criamos esferas para representar cada pessoa que une uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="2745e-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="2745e-132">Clique com botão direito o objeto PhotonUser que você acabou de criar e scrolldown para "objeto 3D e clique em esfera.</span><span class="sxs-lookup"><span data-stu-id="2745e-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="2745e-133">Isso criará um objeto do jogo esfera como um filho do objeto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="2745e-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="2745e-135">Dimensionar a esfera até x = 0,06, y = 0,06, ad z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="2745e-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="2745e-137">Arraste o objeto do jogo PhotonUser na pasta pré-fabricados no painel de projeto e, em seguida, excluí-la da cena.</span><span class="sxs-lookup"><span data-stu-id="2745e-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="2745e-138">Agora, criamos um pré-fabricado que pode ser usado quando ao gerar ou criando novos jogadores em uma experiência compartilhado.</span><span class="sxs-lookup"><span data-stu-id="2745e-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="2745e-140">Observação: Certifique-se de que o objeto do jogo tem copiados com êxito para a pasta pré-fabricados antes de excluí-la da sua hierarquia.</span><span class="sxs-lookup"><span data-stu-id="2745e-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="2745e-141">Criar um novo objeto na hierarquia, seguindo as instruções na etapa 3 e nomeie-a como SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="2745e-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="2745e-142">Em seguida, clique em Add Component, pesquise o Gerenciador de rede genérica e clique nele para adicionar o componente de Gerenciador de rede genérica.</span><span class="sxs-lookup"><span data-stu-id="2745e-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="2745e-143">Altere a posição do objeto para x = 0, y = 0 e z = 0.</span><span class="sxs-lookup"><span data-stu-id="2745e-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="2745e-145">Parabéns</span><span class="sxs-lookup"><span data-stu-id="2745e-145">Congratulations</span></span>

<span data-ttu-id="2745e-146">Depois que todas as etapas acima forem concluídas, e o processo de compilação também é concluído, pressione o botão Reproduzir e conecte sua 2 HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2745e-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="2745e-147">Você deve ver uma esfera mover-se, ao mudar sua cabeça.</span><span class="sxs-lookup"><span data-stu-id="2745e-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="2745e-148">Isso será exibido para qualquer usuário que associa o seu projeto do Unity!</span><span class="sxs-lookup"><span data-stu-id="2745e-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="2745e-149">[Próxima lição: Lição 4 para Sharing(Photon)](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="2745e-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

