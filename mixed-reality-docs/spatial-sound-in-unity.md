---
title: Som espacial no Unity
description: Reprodução de som espacial que vem de um ponto 3D específico dentro de sua cena do Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, som espacial, HRTF, tamanho do espaço
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589075"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="f2d8e-104">Som espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="f2d8e-104">Spatial sound in Unity</span></span>

<span data-ttu-id="f2d8e-105">Este tópico descreve como usar o som espacial em seus projetos do Unity.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="f2d8e-106">Ele aborda os arquivos de plug-in necessárias, bem como os componentes de Unity e propriedades que permitem que o som de espacial.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="f2d8e-107">Habilitando o som espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="f2d8e-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="f2d8e-108">Som espacial, no Unity, é habilitado usando um plug-in spatializer áudio.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="f2d8e-109">Os arquivos de plug-in são empacotados diretamente para o Unity para habilitar o som espacial é tão fácil quanto vai **Editar > configurações do projeto > áudio** e alterando o **plug-in de Spatializer** no Inspetor de para o  **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="f2d8e-110">Como o spatializer Microsoft só dá suporte a 48000Hz no momento, você também deve definir sua taxa de amostragem do sistema para 48000 para evitar uma falha HRTF no caso raro em que o dispositivo de saída do sistema não está definido para 48000 já:</span><span class="sxs-lookup"><span data-stu-id="f2d8e-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="f2d8e-111">![Inspetor de AudioManager](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="f2d8e-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="f2d8e-112">*Inspetor de AudioManager*</span><span class="sxs-lookup"><span data-stu-id="f2d8e-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="f2d8e-113">Seu projeto do Unity agora está configurado para usar som espacial.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="f2d8e-114">Se você não estiver usando um computador Windows 10 para desenvolvimento, você não obterá espacial som no editor nem no dispositivo (mesmo se você estiver usando o SDK do Windows 10).</span><span class="sxs-lookup"><span data-stu-id="f2d8e-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="f2d8e-115">Usando o som espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="f2d8e-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="f2d8e-116">Som espacial é usado em seu projeto do Unity, ajustando as três configurações em seus componentes de fonte de áudio.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="f2d8e-117">As etapas a seguir configurará os componentes de fonte de áudio para som espacial.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="f2d8e-118">No **hierarquia** do painel, selecione o objeto do jogo que tenha um anexado **Audio Source**.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="f2d8e-119">No **Inspector** do painel, nas **Audio Source** componente</span><span class="sxs-lookup"><span data-stu-id="f2d8e-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="f2d8e-120">Verifique as **Spatialize** opção.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="f2d8e-121">Definir **Blend espacial** à **3D** (valor numérico 1).</span><span class="sxs-lookup"><span data-stu-id="f2d8e-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="f2d8e-122">Para obter melhores resultados, expanda **configurações de som 3D** e defina **Volume Rolloff** para **personalizado Rolloff**.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="f2d8e-123">![Painel de Inspetor no Unity mostrando a fonte de áudio](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="f2d8e-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="f2d8e-124">*Painel de Inspetor no Unity mostrando a fonte de áudio*</span><span class="sxs-lookup"><span data-stu-id="f2d8e-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="f2d8e-125">Os sons agora na verdade, existem dentro do ambiente do seu projeto!</span><span class="sxs-lookup"><span data-stu-id="f2d8e-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="f2d8e-126">É altamente recomendável que você se familiarize com o [diretrizes de design de som espacial](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="f2d8e-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="f2d8e-127">Essas diretrizes ajudam a integrar o seu áudio perfeitamente em seu projeto e para ainda mais que os usuários com a experiência que você criou.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="f2d8e-128">Definindo configurações de som espaciais</span><span class="sxs-lookup"><span data-stu-id="f2d8e-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="f2d8e-129">O plug-in Microsoft Spatial Sound fornece um parâmetro adicional que pode ser definido, em um acordo com a fonte de áudio, para permitir que o controle adicional da simulação áudio.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="f2d8e-130">Esse parâmetro é o tamanho da sala simulado.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="f2d8e-131">Tamanho do espaço</span><span class="sxs-lookup"><span data-stu-id="f2d8e-131">Room Size</span></span>

<span data-ttu-id="f2d8e-132">O tamanho da sala que está sendo simulada pelo som espacial.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="f2d8e-133">Os tamanhos aproximados das salas são; pequena (um escritório em uma sala de conferência pequeno), média (uma sala de conferência grande) e grande (um auditório).</span><span class="sxs-lookup"><span data-stu-id="f2d8e-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="f2d8e-134">Você também pode especificar um tamanho de sala de none para simular um ambiente ao ar livre.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="f2d8e-135">O tamanho de espaço padrão é pequeno.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="f2d8e-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f2d8e-136">Example</span></span>

<span data-ttu-id="f2d8e-137">O MixedRealityToolkit para Unity fornece uma classe estática que faz a definir as configurações de som espacial fácil.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="f2d8e-138">Essa classe pode ser encontrada na [MixedRealityToolkit\SpatialSound pasta](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) e podem ser chamados de qualquer script em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="f2d8e-139">É recomendável que você defina esses parâmetros em cada componente de fonte de áudio em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="f2d8e-140">O exemplo a seguir mostra como selecionar o tamanho médio de espaço para uma fonte de áudio anexado.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="f2d8e-141">Acessar diretamente os parâmetros do Unity</span><span class="sxs-lookup"><span data-stu-id="f2d8e-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="f2d8e-142">Se você não quiser usar as ferramentas de áudio excelente no MixedRealityToolkit, aqui está como você alteraria HRTF parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="f2d8e-143">Você pode copiar/colar isso em um script chamado *SetHRTF.cs* que você deseja anexar a cada AudioSource HRTF.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="f2d8e-144">Ele permite alterar os parâmetros importantes para HRTF.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-144">It lets you change parameters important to HRTF.</span></span>

```cs
using UnityEngine;
   using System.Collections;
   public class SetHRTF : MonoBehaviour    {
       public enum ROOMSIZE { Small, Medium, Large, None };
       public ROOMSIZE room = ROOMSIZE.Small;  // Small is regarded as the "most average"
       // defaults and docs from MSDN
       // https://msdn.microsoft.com/library/windows/desktop/mt186602(v=vs.85).aspx
       AudioSource audiosource;
       void Awake()
       {
           audiosource = this.gameObject.GetComponent<AudioSource>();
           if (audiosource == null)
           {
               print("SetHRTFParams needs an audio source to do anything.");
               return;
           }
           audiosource.spatialize = 1; // we DO want spatialized audio
           audiosource.spread = 0; // we dont want to reduce our angle of hearing
           audiosource.spatialBlend = 1;   // we do want to hear spatialized audio
           audiosource.SetSpatializerFloat(1, (float)room);    // 1 is the roomsize param
       }
   }
```
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="f2d8e-145">Som espacial no Kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="f2d8e-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="f2d8e-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="f2d8e-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="f2d8e-147">Os exemplos a seguir do Kit de ferramentas de realidade misturada são exemplos de efeito de áudio geral que demonstram formas de tornar suas experiências mais envolventes usando o som.</span><span class="sxs-lookup"><span data-stu-id="f2d8e-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="f2d8e-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span><span class="sxs-lookup"><span data-stu-id="f2d8e-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="f2d8e-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span><span class="sxs-lookup"><span data-stu-id="f2d8e-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="f2d8e-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2d8e-150">See also</span></span>
* [<span data-ttu-id="f2d8e-151">Som espacial</span><span class="sxs-lookup"><span data-stu-id="f2d8e-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="f2d8e-152">Design de som espacial</span><span class="sxs-lookup"><span data-stu-id="f2d8e-152">Spatial sound design</span></span>](spatial-sound-design.md)
