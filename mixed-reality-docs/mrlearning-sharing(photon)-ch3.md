---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 33f265c6333f12f7ec73ecb0c1e5730b168d4bde
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415907"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="c2fa1-104">**Conectar-se vários usuários**</span><span class="sxs-lookup"><span data-stu-id="c2fa1-104">**Connecting Multiple Users**</span></span> 

<span data-ttu-id="c2fa1-105">Nesta lição, aprenderemos para se conectar a vários usuários como parte de uma experiência de compartilhada em tempo real.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-105">In this lesson, we will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="c2fa1-106">No final desta lição, você será capaz de abrir o aplicativo em vários dispositivos e ver representações do "avatar" de cada pessoa que une (avatares representados por uma esfera).</span><span class="sxs-lookup"><span data-stu-id="c2fa1-106">By the end of this lesson, you will be able to open the application on multiple devices, and see "avatar" representations of each person that joins (avatars represented by a sphere.)</span></span> 

<span data-ttu-id="c2fa1-107">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="c2fa1-107">Objectives:</span></span>

- <span data-ttu-id="c2fa1-108">Configurar o TROCADILHO dentro de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="c2fa1-108">Configure PUN within your application</span></span>
- <span data-ttu-id="c2fa1-109">Configurar os jogadores</span><span class="sxs-lookup"><span data-stu-id="c2fa1-109">Configure players</span></span>
- <span data-ttu-id="c2fa1-110">Saiba como se conectar a vários usuários em uma experiência de compartilhado</span><span class="sxs-lookup"><span data-stu-id="c2fa1-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="c2fa1-111">Instruções</span><span class="sxs-lookup"><span data-stu-id="c2fa1-111">Instructions</span></span>

1. <span data-ttu-id="c2fa1-112">Nos ativos > recursos > pré-fabricados pasta do painel projeto, arrastar e soltar o "NetworkLobby" pré-fabricado à hierarquia, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-112">In the Assets>Resources>Prefabs folder of the project panel, drag and drop the "NetworkLobby" prefab in to the hierarchy, as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="c2fa1-114">Quando você expande o pré-fabricado "NetworkLobby", você deverá ver um objeto filho chamado "NetworkRoom".</span><span class="sxs-lookup"><span data-stu-id="c2fa1-114">When you expand the prefab "NetworkLobby," you should see a child object called "NetworkRoom."</span></span> <span data-ttu-id="c2fa1-115">Com ele selecionado, vá para o painel do Inspetor e clique em "Adicionar componente".</span><span class="sxs-lookup"><span data-stu-id="c2fa1-115">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="c2fa1-116">Pesquise "PhotonView" e adicione o componente.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-116">Search for "PhotonView" and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="c2fa1-118">Criar um novo objeto jogo vazio na hierarquia (clique com o botão direito na hierarquia e selecione "Vazio" no menu de contexto).</span><span class="sxs-lookup"><span data-stu-id="c2fa1-118">Create a new empty game object in the hierarchy (right click in the hierarchy and select "Empty" from the context menu).</span></span> <span data-ttu-id="c2fa1-119">Verifique se o posicionamento é definido como x = 0, y = 0, z = 0 e nomear o objeto, "PhotonUser".</span><span class="sxs-lookup"><span data-stu-id="c2fa1-119">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="c2fa1-121">Clique no botão "Adicionar componente" e digite "Sync Net genérico" e selecione a classe genérica sincronização Net.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-121">Click on the "Add Component" button and type "Generic Net Sync" and select the Generic Net Sync class.</span></span> <span data-ttu-id="c2fa1-122">Depois que a classe for exibida, clique na caixa de seleção de "Usuário" para ativá-lo.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-122">Once the class appears, click on the "User" check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="c2fa1-124">Novamente clique em "Adicionar componente" e, em seguida, digite "Photon exibição" e selecione a classe de exibição Photon que aparece na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-124">Again click on "Add Component" and then type "Photon View" and select the Photon View class that appears in the drop down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="c2fa1-126">Agora clique no ícone no arquivo para a classe de sincronização Net genérico, em seguida, arraste e solte-o ao campo de "Componentes observada" Photon da exibição.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-126">Now click on the File icon in for the Generic Net Sync class, then drag and drop it to the Photon View's "Observed Components" field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="c2fa1-128">Em seguida, queremos criar esferas para representar cada pessoa que une uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-128">Next, we want to create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="c2fa1-129">Clique com botão direito no objeto "PhotonUser" que você acabou de criar, vá para baixo para o "objeto 3D" e clique em "Esfera".</span><span class="sxs-lookup"><span data-stu-id="c2fa1-129">Right click the "PhotonUser" object you just created, go down to "3D Object" and click "Sphere."</span></span> <span data-ttu-id="c2fa1-130">Isso criará um objeto do jogo esfera como um filho do objeto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-130">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="c2fa1-132">Dimensionar a esfera até x = 0,06, y = 0,06, ad z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-132">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="c2fa1-134">Arraste o objeto do jogo "PhotonUser" para a pasta de "pré-fabricados" no painel de projeto.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-134">Drag the "PhotonUser" game object into the "prefabs" folder in the project panel.</span></span> <span data-ttu-id="c2fa1-135">Em seguida, exclua-o da cena.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-135">Then, delete it from the scene.</span></span> <span data-ttu-id="c2fa1-136">Agora, criamos um pré-fabricado que será usado ao gerar ou criar uma instância novos jogadores em uma experiência compartilhado.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-136">We have now created a prefab that will be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="c2fa1-138">Observação: Certifique-se de que o objeto do jogo tem copiados com êxito para a pasta "prefabs" antes de excluí-la da sua hierarquia.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-138">Note: ensure that the game object has successfully copied into the "prefabs" folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="c2fa1-139">Crie um novo objeto na hierarquia (usando instruções semelhantes da etapa 3) e nomeie-a como "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="c2fa1-139">Create a new object in the hierarchy (using similar instructions to that of Step 3), and name it "SharedPlayground."</span></span> <span data-ttu-id="c2fa1-140">Em seguida, clique em "Adicionar componente" e pesquise "Gerenciador de rede genérica" e clique nele para adicionar o componente de Gerenciador de rede genérica.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-140">Then, click "Add Component" and search for "generic network manager" and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="c2fa1-141">Altere a posição do objeto para x = 0, y = 0 e z = 0.</span><span class="sxs-lookup"><span data-stu-id="c2fa1-141">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="c2fa1-143">Parabéns</span><span class="sxs-lookup"><span data-stu-id="c2fa1-143">Congratulations</span></span>

<span data-ttu-id="c2fa1-144">Depois que todas as etapas acima forem concluídas, e o processo de compilação for concluído, quando você pressiona o botão Reproduzir e conectar sua 2 HoloLens, você deverá ver uma esfera mover-se à medida que você move a cabeça!</span><span class="sxs-lookup"><span data-stu-id="c2fa1-144">Once all the steps above are complete, and the build process is complete, when you press the play button and connect your HoloLens 2, you should see a sphere moving around as you move your head!</span></span> <span data-ttu-id="c2fa1-145">Isso será exibido para qualquer usuário que associa o seu projeto do Unity!</span><span class="sxs-lookup"><span data-stu-id="c2fa1-145">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="c2fa1-146">[Próxima lição: Lição 4 para Sharing(Photon)](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="c2fa1-146">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

