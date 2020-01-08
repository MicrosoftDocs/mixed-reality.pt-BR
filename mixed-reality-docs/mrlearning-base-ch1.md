---
title: Tutoriais de introdução – 2. Inicializar o projeto e seu primeiro aplicativo
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: realidade misturada, Unity, tutorial, HoloLens
ms.openlocfilehash: d0c166f760884efab9719ecba1ff83285872e2ef
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334416"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="9bda8-105">2. Inicializar o projeto e seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="9bda8-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="9bda8-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="9bda8-106">Overview</span></span>

<span data-ttu-id="9bda8-107">Nesta primeira lição, você aprenderá mais sobre algumas das funcionalidades que o <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Kit de Ferramentas de Realidade Misturada)</a> tem a oferecer, iniciará seu primeiro aplicativo do HoloLens 2 e o implantará no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9bda8-107">In this first lesson, you'll learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="9bda8-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9bda8-108">Objectives</span></span>

* <span data-ttu-id="9bda8-109">Configure o Unity para o desenvolvimento no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9bda8-109">Configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="9bda8-110">Importe ativos e configure a cena.</span><span class="sxs-lookup"><span data-stu-id="9bda8-110">Import assets and set up the scene.</span></span>
* <span data-ttu-id="9bda8-111">Visualização da malha de mapeamento espacial, das malhas da mão e do contador da taxa de quadros.</span><span class="sxs-lookup"><span data-stu-id="9bda8-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="9bda8-112">Crie um novo projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="9bda8-112">Create new Unity project</span></span>

1. <span data-ttu-id="9bda8-113">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="9bda8-113">Start Unity.</span></span>

2. <span data-ttu-id="9bda8-114">Selecione **Novo**.</span><span class="sxs-lookup"><span data-stu-id="9bda8-114">Select **New**.</span></span>

    ![Lesson1 Section1 Step2](images/mrlearning-base-ch1-1-step2.JPG)

3. <span data-ttu-id="9bda8-116">Insira um nome de projeto (por exemplo, "MixedRealityBase").</span><span class="sxs-lookup"><span data-stu-id="9bda8-116">Enter a project name (e.g. "MixedRealityBase").</span></span>

    ![Lesson1 Section1 Step3](images/mrlearning-base-ch1-1-step3.JPG)

4. <span data-ttu-id="9bda8-118">Insira um local para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="9bda8-118">Enter a location to save your project.</span></span>

    ![Lesson1 Section1 Step4](images/mrlearning-base-ch1-1-step4.JPG)

5. <span data-ttu-id="9bda8-120">Verifique se o projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="9bda8-120">Make sure the project is set to **3D**.</span></span>

    ![Lesson1 Section1 Step5](images/mrlearning-base-ch1-1-step5.JPG)

6. <span data-ttu-id="9bda8-122">Clique em **Criar Projeto**.</span><span class="sxs-lookup"><span data-stu-id="9bda8-122">Click **Create Project**.</span></span>

    ![Lesson1 Section1 Step6](images/mrlearning-base-ch1-1-step6.JPG)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="9bda8-124">Configure o projeto do Unity para o Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="9bda8-124">Configure the Unity project for Windows Mixed Reality</span></span>

1. <span data-ttu-id="9bda8-125">Abra a janela *Configurações de Build* acessando **Arquivo** > **Configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="9bda8-125">Open the *Build Settings* window by going to **File** > **Build Settings**.</span></span>

    ![Lesson1 Section2 Step1](images/mrlearning-base-ch1-2-step1.JPG)

2. <span data-ttu-id="9bda8-127">Selecione a *Plataforma Universal do Windows* e clique no botão **Alternar Plataforma** para alternar as plataformas.</span><span class="sxs-lookup"><span data-stu-id="9bda8-127">Select the *Universal Windows Platform* and click the **Switch Platform** button to switch platforms.</span></span> <span data-ttu-id="9bda8-128">Os aplicativos em execução no HoloLens 2 precisam ser compatíveis com o UWP (Plataforma Universal do Windows).</span><span class="sxs-lookup"><span data-stu-id="9bda8-128">Applications running on HoloLens 2 are required to be Universal Windows Platform (UWP) compatible.</span></span>

    ![Lesson1 Section2 Step2](images/mrlearning-base-ch1-2-step2.JPG)

3. <span data-ttu-id="9bda8-130">Habilite a realidade virtual clicando no botão **Configurações do Player** na janela de build e habilite a caixa de seleção *Realidade Virtual Compatível* nas configurações de XR no painel do inspetor, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="9bda8-130">Enable virtual reality by clicking the **Player Settings** button in the Build Window, and enable the *Virtual Reality Supported* checkbox under XR Settings from the inspector panel, as shown in the image below.</span></span> <span data-ttu-id="9bda8-131">Observe que talvez seja necessário arrastar a janela *Configurações de Build* para o lado para ver o painel do inspetor.</span><span class="sxs-lookup"><span data-stu-id="9bda8-131">Note that you might need to drag the *Build Settings* window out of the way in order to see the inspector panel.</span></span> <span data-ttu-id="9bda8-132">A caixa de seleção *Realidade Virtual Compatível* também se aplica aos headsets de realidade misturada e realidade aumentada, pois se refere à habilitação da visão estereoscópica (renderização de imagens diferentes para cada olho).</span><span class="sxs-lookup"><span data-stu-id="9bda8-132">The *Virtual Reality Supported* checkbox also applies to Mixed Reality and Augmented Reality headsets because it refers to the enabling of stereoscopic vision (rendering different images for each eye.)</span></span>

    ![Lesson1 Section2 Step3](images/mrlearning-base-ch1-2-step3.JPG)

4. <span data-ttu-id="9bda8-134">Também nas configurações de XR, altere o *Modo de Renderização Estéreo* para *Instanciado de Passagem Única*.</span><span class="sxs-lookup"><span data-stu-id="9bda8-134">Also under XR Settings, change the *Stereo Rendering Mode* to *Single Pass Instanced*.</span></span> <span data-ttu-id="9bda8-135">Esse [estilo de pipeline de renderização](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) geralmente tem o melhor desempenho no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9bda8-135">This [rendering pipeline style](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) is generally most performant for HoloLens 2.</span></span> <span data-ttu-id="9bda8-136">Se estiver interessado em outras configurações de alto desempenho para o ambiente do Unity, siga [estas instruções](recommended-settings-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="9bda8-136">If interested in other performant configurations for your Unity environment, follow [these instructions](recommended-settings-for-unity.md).</span></span>

    ![Lesson1 Section2 Step4](images/mrlearning-base-ch1-2-step4.jpg)

5. <span data-ttu-id="9bda8-138">No mesmo painel do inspetor, verifique se a caixa de seleção *Percepção Espacial* está marcada na seção de funcionalidades em *Configurações de Publicação*.</span><span class="sxs-lookup"><span data-stu-id="9bda8-138">From the same inspector panel, ensure that the *Spatial Perception* checkbox in the capabilities section is enabled under *Publishing Settings*.</span></span> <span data-ttu-id="9bda8-139">A Percepção Espacial nos permite visualizar a malha de mapeamento espacial em um dispositivo de realidade misturada, como o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9bda8-139">Spatial Perception allows us to visualize the spatial mapping mesh on a mixed reality device, such as HoloLens 2.</span></span> <span data-ttu-id="9bda8-140">As Configurações de Publicação são encontradas no painel do inspetor, acima das Configurações de XR e em Outras Configurações.</span><span class="sxs-lookup"><span data-stu-id="9bda8-140">Publishing Settings are found in the inspector panel, above XR Settings and under Other Settings.</span></span>

    ![Lesson1 Section2 Step5](images/mrlearning-base-ch1-2-step5.JPG)

    >[!NOTE]
    ><span data-ttu-id="9bda8-142">Embora não sejam usadas nesta seção, algumas outras funcionalidades comuns que talvez você queira habilitar incluem o *Microfone* para comandos de voz e o *InternetClient* para se conectar aos serviços que exigem uma conexão de rede.</span><span class="sxs-lookup"><span data-stu-id="9bda8-142">While not used in this section, some other common capabilities you might want to enable include the *Microphone* for voice commands, and *InternetClient* for connecting to services requiring a network connection.</span></span>

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="9bda8-143">Importe o Kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="9bda8-143">Import the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="9bda8-144">Baixe o [pacote de fundamentos versão 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) do [Kit de Ferramentas de Realidade Misturada](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) para Unity e salve-o em uma pasta no computador.</span><span class="sxs-lookup"><span data-stu-id="9bda8-144">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation package version 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) and save it to a folder on your PC.</span></span>

2. <span data-ttu-id="9bda8-145">Importe o pacote do *Kit de Ferramentas de Realidade Misturada* baixado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="9bda8-145">Import the *Mixed Reality Toolkit* package that you downloaded in the previous step.</span></span> <span data-ttu-id="9bda8-146">Comece clicando em **Ativos** > **Importar** > **Pacote Personalizado**, selecione *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* e abra-o para iniciar o processo de importação.</span><span class="sxs-lookup"><span data-stu-id="9bda8-146">Start by clicking on **Assets** > **Import** > **Custom Package**, select *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* and open it to begin the importing process.</span></span> <span data-ttu-id="9bda8-147">Aguarde alguns minutos para a conclusão do processo de importação.</span><span class="sxs-lookup"><span data-stu-id="9bda8-147">Allow a few minutes for the importing process to complete.</span></span>

    ![Lesson1 Section3 Step2a](images/mrlearning-base-ch1-3-step2a.JPG)

    ![Lesson1 Section3 Step2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. <span data-ttu-id="9bda8-150">Na próxima janela pop-up, clique em **Importar** para iniciar a importação do pacote selecionado para o projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="9bda8-150">In the next pop-up window, click **Import** to begin importing the selected package into the Unity project.</span></span> <span data-ttu-id="9bda8-151">Verifique se todos os itens estão marcados, conforme mostrado na imagem.</span><span class="sxs-lookup"><span data-stu-id="9bda8-151">Ensure all items are checked as shown in the image.</span></span>

    ![Lesson1 Section3 Step3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > <span data-ttu-id="9bda8-153">Se uma caixa de diálogo pop-up for exibida solicitando a aplicação das configurações padrão do Kit de Ferramentas de Realidade Misturada, clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="9bda8-153">If you see a pop-up dialog box asking to apply the Mixed Reality Toolkit default settings, click **Apply**.</span></span> <span data-ttu-id="9bda8-154">O MRTK analisa o projeto para ver se há configurações recomendadas ausentes quando importadas para instalação automatizada.</span><span class="sxs-lookup"><span data-stu-id="9bda8-154">MRTK analyzes your project for any missing recommended settings when imported for automated setup.</span></span> <span data-ttu-id="9bda8-155">Dependendo de suas configurações, o pop-up pode parecer diferente da imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="9bda8-155">Depending on your settings, the pop-up might look different than the image below.</span></span>

    ![Lesson1 Section3 Step4 Note1](images/mrlearning-base-ch1-3-step4-note1.JPG)

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="9bda8-157">Configure o Kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="9bda8-157">Configure the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="9bda8-158">Adicione o *Kit de Ferramentas de Realidade Misturada* à cena atual selecionando **Kit de Ferramentas de Realidade Misturada** > **Adicionar à Cena e Configurar...**</span><span class="sxs-lookup"><span data-stu-id="9bda8-158">Add the *Mixed Reality Toolkit* to your current scene by selecting **Mixed Reality Toolkit** > **Add to Scene and Configure..**</span></span> <span data-ttu-id="9bda8-159">na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="9bda8-159">from the menu bar.</span></span> <span data-ttu-id="9bda8-160">Se você não vir esse item de menu depois de importar o Kit de Ferramentas de Realidade Misturada, reinicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="9bda8-160">If you don't see this menu item after importing the mixed reality toolkit, restart Unity.</span></span>

    ![Lesson1 Section4 Step1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > <span data-ttu-id="9bda8-162">Talvez você veja uma caixa de diálogo pop-up para a seleção de um [perfil para o Kit de Ferramentas de Realidade Misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span><span class="sxs-lookup"><span data-stu-id="9bda8-162">You may see a pop-up dialog box for selecting a [profile for the Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span></span> <span data-ttu-id="9bda8-163">Escolha o perfil chamado *DefaultHoloLens2ConfigurationProfile* clicando duas vezes nele.</span><span class="sxs-lookup"><span data-stu-id="9bda8-163">Choose the profile named *DefaultHoloLens2ConfigurationProfile* by double-clicking it.</span></span>

2. <span data-ttu-id="9bda8-164">A cena terá vários novos itens e modificações.</span><span class="sxs-lookup"><span data-stu-id="9bda8-164">Your scene will have several new items and modifications.</span></span> <span data-ttu-id="9bda8-165">Salve a cena com outro nome clicando em **Arquivo** > **Salvar como...** e dê um nome à cena, por exemplo, *BaseScene*.</span><span class="sxs-lookup"><span data-stu-id="9bda8-165">Save your scene under a different name by clicking **File** > **Save As...**, and give your scene a name, such as *BaseScene*.</span></span> <span data-ttu-id="9bda8-166">Mantenha a cena organizada salvando-a na pasta *Cenas* da pasta *Ativos* do projeto.</span><span class="sxs-lookup"><span data-stu-id="9bda8-166">Keep your scene organized by saving it to the *Scenes* folder in your project’s *Assets* folder.</span></span>

    ![Lesson1 Section4 Step2a](images/mrlearning-base-ch1-4-step2a.JPG)

    ![Lesson1 Section4 Step2b](images/mrlearning-base-ch1-4-step2b.JPG)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="9bda8-169">Crie o aplicativo para seu dispositivo</span><span class="sxs-lookup"><span data-stu-id="9bda8-169">Build your application to your device</span></span>

1. <span data-ttu-id="9bda8-170">Se você fechou a janela *Configurações de Build* nas seções anteriores, abra a janela *Configurações de Build* novamente acessando **Arquivo** > **Configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="9bda8-170">If you closed the *Build Settings* window from the previous sections, open the *Build Settings* window again by going to **File** > **Build Settings**.</span></span>

    ![Lesson1 Section5 Step1](images/mrlearning-base-ch1-5-step1.JPG)

2. <span data-ttu-id="9bda8-172">Verifique se a cena recém-criada está na lista *Cenas no Build* clicando no botão **Adicionar Cenas Abertas** enquanto a cena está aberta no Unity.</span><span class="sxs-lookup"><span data-stu-id="9bda8-172">Ensure the scene you just created is in the *Scenes in Build* list by clicking on the **Add Open Scenes** button while your scene is open in Unity.</span></span>

3. <span data-ttu-id="9bda8-173">Pressione o botão **Compilar** para iniciar o processo de build.</span><span class="sxs-lookup"><span data-stu-id="9bda8-173">Press the **Build** button to begin the build process.</span></span>

    ![Lesson1 Section5 Step3](images/mrlearning-base-ch1-5-step3.JPG)

4. <span data-ttu-id="9bda8-175">Crie e dê um nome para uma nova pasta para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9bda8-175">Create and name a new folder for your application.</span></span> <span data-ttu-id="9bda8-176">Na imagem abaixo, uma pasta com o nome App foi criada para armazenar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9bda8-176">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="9bda8-177">Clique em **Selecionar Pasta** para iniciar o build na pasta recém-criada.</span><span class="sxs-lookup"><span data-stu-id="9bda8-177">Click **Select Folder** to begin building to the newly created folder.</span></span> <span data-ttu-id="9bda8-178">Após a conclusão do build, feche a janela *Configurações de Build* no Unity.</span><span class="sxs-lookup"><span data-stu-id="9bda8-178">After the build has completed, you can close the *Build Settings* window in Unity.</span></span>

    ![Lesson1 Section5 Step4](images/mrlearning-base-ch1-5-step4.JPG)

    >[!IMPORTANT]
    ><span data-ttu-id="9bda8-180">se a compilação falhar, tente compilar novamente ou reiniciar o Unity e compilar novamente.</span><span class="sxs-lookup"><span data-stu-id="9bda8-180">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="9bda8-181">Se você receber um erro, como "Erro: CS0246 = O tipo ou o nome do namespace “XX” não pôde ser encontrado (uma diretiva using ou uma referência de assembly está ausente?).</span><span class="sxs-lookup"><span data-stu-id="9bda8-181">If you see an error, such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="9bda8-182">Nesse caso, talvez seja necessário instalar o [SDK do Windows 10 (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)</span><span class="sxs-lookup"><span data-stu-id="9bda8-182">If so, you might need to install [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)</span></span>

5. <span data-ttu-id="9bda8-183">Depois que a compilação for concluída, abra a pasta recém-criada que contém os arquivos do novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9bda8-183">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="9bda8-184">Clique duas vezes na solução *MixedRealityBase.sln* ou no nome correspondente, caso tenha usado um nome alternativo para o projeto, para abrir o arquivo de solução no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9bda8-184">Double-click on the *MixedRealityBase.sln* solution, or the corresponding name, if you used an alternative name for your project, to open the solution file in Visual Studio.</span></span>

    >[!NOTE]
    ><span data-ttu-id="9bda8-185">Lembre-se de abrir a pasta recém-criada (ou seja, a pasta *App*, caso esteja seguindo as convenções de nomenclatura das etapas anteriores), pois haverá um arquivo .sln com nome semelhante fora dessa pasta que não deve ser confundido com o arquivo .sln dentro da pasta de build.</span><span class="sxs-lookup"><span data-stu-id="9bda8-185">Be sure to open the newly created folder (i.e. the *App* folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder, that is not to be confused with the .sln file inside the build folder.</span></span> <span data-ttu-id="9bda8-186">A estrutura de pastas deve ser semelhante à imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="9bda8-186">The folder structure should look similar to the image below.</span></span>
    >
    ><span data-ttu-id="9bda8-187">Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar que todos os componentes necessários estejam instalados conforme especificado na [página "Instalar as ferramentas"](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="9bda8-187">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

    ![Lesson1 Section5 Step5](images/mrlearning-base-ch1-5-step5.JPG)

6. <span data-ttu-id="9bda8-189">Conecte o HoloLens 2 ao computador.</span><span class="sxs-lookup"><span data-stu-id="9bda8-189">Connect your HoloLens 2 into your PC.</span></span> <span data-ttu-id="9bda8-190">Embora essas instruções pressuponham que você esteja fazendo a implantação em um dispositivo HoloLens 2, você também pode optar por implantar o [emulador do HoloLens 2](using-the-hololens-emulator.md) ou criar um [pacote do aplicativo para sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="9bda8-190">While these instructions assume you will be deploying to a HoloLens 2 device, you might also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="9bda8-191">Antes do build no dispositivo, o dispositivo precisa estar no *Modo de Desenvolvedor* e emparelhado com o computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9bda8-191">Before building to your device, the device must be in *Developer Mode* and paired with your development machine.</span></span> <span data-ttu-id="9bda8-192">Essas duas etapas podem ser concluídas seguindo [estas instruções](using-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="9bda8-192">Both of these steps can be completed by following [these instructions](using-visual-studio.md)</span></span>

7. <span data-ttu-id="9bda8-193">Configure o Visual Studio para o build no HoloLens 2 selecionando a configuração *Versão* ou *Mestre*, a arquitetura *ARM* e *Dispositivo* como o destino.</span><span class="sxs-lookup"><span data-stu-id="9bda8-193">Configure Visual Studio for building to your HoloLens 2 by selecting the *Release* or *Master* configuration, the *ARM* architecture, and *Device* as target.</span></span>

    ![Lesson1 Section5 Step8](images/mrlearning-base-ch1-5-step7.JPG)

8. <span data-ttu-id="9bda8-195">A etapa final é o build e a implantação no dispositivo por meio da seleção de **Depurar** > **Iniciar sem depuração**.</span><span class="sxs-lookup"><span data-stu-id="9bda8-195">The final step is to build and deploy to your device by selecting **Debug** > **Start without debugging**.</span></span> <span data-ttu-id="9bda8-196">A seleção de *Iniciar sem Depuração* faz com que o aplicativo seja iniciado imediatamente no dispositivo após um build bem-sucedido, mas sem o depurador anexado e sem exibir as informações no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9bda8-196">Selecting *Start without Debugging* causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="9bda8-197">Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9bda8-197">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9bda8-198">Selecione também **Build** > **Implantar Solução** para a implantação no dispositivo sem fazer com que o aplicativo seja iniciado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9bda8-198">You might also select **Build** > **Deploy Solution** to deploy to your device without having the application automatically start.</span></span>

    ![Lesson1 Section5 Step9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a><span data-ttu-id="9bda8-200">Parabéns</span><span class="sxs-lookup"><span data-stu-id="9bda8-200">Congratulations</span></span>

<span data-ttu-id="9bda8-201">Você acabou de implantar seu primeiro aplicativo do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9bda8-201">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="9bda8-202">Enquanto caminha, você deverá ver uma malha de mapeamento espacial cobrindo todas as superfícies que foram percebidas pelo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9bda8-202">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="9bda8-203">Além disso, você deverá ver indicadores em suas mãos e seus dedos para o acompanhamento da mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9bda8-203">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="9bda8-204">Essas são apenas algumas das partes fundamentais predefinidas no Kit de ferramentas de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="9bda8-204">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="9bda8-205">Nas próximas lições, você começará a adicionar mais conteúdo e interatividade à cena, de modo a explorar totalmente as funcionalidades do HoloLens 2 e do Kit de Ferramentas de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="9bda8-205">In the lessons to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="9bda8-206">No aplicativo, é possível observar o criador de perfil visual.</span><span class="sxs-lookup"><span data-stu-id="9bda8-206">In the app, you may notice the visual profiler.</span></span> <span data-ttu-id="9bda8-207">Você verá como ativar/desativar o contador da taxa de quadros usando um comando de voz na [Lição 5](mrlearning-base-ch5.md).</span><span class="sxs-lookup"><span data-stu-id="9bda8-207">You will cover how to toggle the frame rate counter using a voice command in [Lesson 5](mrlearning-base-ch5.md).</span></span> <span data-ttu-id="9bda8-208">Geralmente, é recomendado manter o criador de perfil visual visível em todos os momentos durante o desenvolvimento para entender quando as alterações de código podem ter afetado o desempenho.</span><span class="sxs-lookup"><span data-stu-id="9bda8-208">It is generally recommended to keep the visual profiler visible at all times during development to understand when code changes may have impacted perf.</span></span> <span data-ttu-id="9bda8-209">O aplicativo do HoloLens 2 deve [ser executado continuamente a 60 FPS](understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="9bda8-209">HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="9bda8-210">Próxima lição: 3. Criar a interface do usuário e configurar o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="9bda8-210">Next Lesson: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)
