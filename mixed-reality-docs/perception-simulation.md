---
title: Simulação de percepção
description: Um guia para usar a biblioteca de simulação de percepção para automatizar entrada simulada para aplicativos imersivos
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, simulação, testando
ms.openlocfilehash: 693750eb753bd11cbe7d7cfb47e04f1a3506ca9a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590013"
---
# <a name="perception-simulation"></a><span data-ttu-id="0b94c-104">Simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="0b94c-104">Perception simulation</span></span>

<span data-ttu-id="0b94c-105">Você deseja criar um teste automatizado para seu aplicativo?</span><span class="sxs-lookup"><span data-stu-id="0b94c-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="0b94c-106">Você deseja que seus testes ir além dos testes de unidade de nível de componente e realmente exercitar seu aplicativo ponta a ponta?</span><span class="sxs-lookup"><span data-stu-id="0b94c-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="0b94c-107">Simulação de percepção é o que você está procurando.</span><span class="sxs-lookup"><span data-stu-id="0b94c-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="0b94c-108">A biblioteca de simulação de percepção envia falsos humanos e dados de entrada do mundo para seu aplicativo para que você possa automatizar seus testes.</span><span class="sxs-lookup"><span data-stu-id="0b94c-108">The Perception Simulation library sends fake human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="0b94c-109">Por exemplo, você pode simular a entrada de um humano procurando esquerda e direita e, em seguida, executar um gesto.</span><span class="sxs-lookup"><span data-stu-id="0b94c-109">For example, you can simulate the input of a human looking left and right and then performing a gesture.</span></span>

<span data-ttu-id="0b94c-110">Simulação de percepção pode enviar entrada simulada como esta para um HoloLens físico, o emulador do HoloLens ou um PC com o Portal de realidade misturada instalado.</span><span class="sxs-lookup"><span data-stu-id="0b94c-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="0b94c-111">Percepção de simulação ignora os sensores em tempo real em um dispositivo de realidade mista e envia simulados de entrada para aplicativos em execução no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0b94c-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="0b94c-112">Aplicativos recebem esses eventos de entrada fictícios por meio das mesmas APIs que eles sempre usam e que não é possível determinar a diferença entre a execução com sensores reais versus executando com simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="0b94c-112">Applications receive these fake input events through the same APIs they always use, and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="0b94c-113">Simulação de percepção é a mesma tecnologia usada pelo emulador do HoloLens enviem dados de entrada para a máquina Virtual HoloLens simulado.</span><span class="sxs-lookup"><span data-stu-id="0b94c-113">Perception Simulation is the same technology used by the HoloLens emulator to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="0b94c-114">Simulação começa criando um objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="0b94c-114">Simulation starts by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="0b94c-115">A partir desse objeto, você pode emitir comandos para controlar propriedades de um simulado "humana", incluindo posição principal, a posição de mão e gestos.</span><span class="sxs-lookup"><span data-stu-id="0b94c-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="0b94c-116">Como configurar um projeto do Visual Studio para a percepção de simulação</span><span class="sxs-lookup"><span data-stu-id="0b94c-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="0b94c-117">[Instalar o emulador do HoloLens](install-the-tools.md) em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="0b94c-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="0b94c-118">O emulador inclui as bibliotecas que você usará para a simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="0b94c-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="0b94c-119">Criar um novo Visual Studio C# projeto da área de trabalho (um projeto de Console funciona muito bem de começar a usar).</span><span class="sxs-lookup"><span data-stu-id="0b94c-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="0b94c-120">Adicione os seguintes binários ao seu projeto como referências (projeto -> Adicionar -> referência...). Você pode encontrá-los no **% ProgramFiles (x86) %\Microsoft XDE\10.0.11082.0** um.</span><span class="sxs-lookup"><span data-stu-id="0b94c-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in **%ProgramFiles(x86)%\Microsoft XDE\10.0.11082.0** a.</span></span> <span data-ttu-id="0b94c-121">PerceptionSimulationManager.Interop.dll - gerenciados C# wrapper para a simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="0b94c-121">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="0b94c-122">b.</span><span class="sxs-lookup"><span data-stu-id="0b94c-122">b.</span></span> <span data-ttu-id="0b94c-123">PerceptionSimulationRest.dll - Library para configurar um canal de comunicação de soquete da web para o HoloLens ou emulador.</span><span class="sxs-lookup"><span data-stu-id="0b94c-123">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="0b94c-124">c.</span><span class="sxs-lookup"><span data-stu-id="0b94c-124">c.</span></span> <span data-ttu-id="0b94c-125">SimulationStream.Interop.dll - tipos compartilhados para simulação.</span><span class="sxs-lookup"><span data-stu-id="0b94c-125">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="0b94c-126">Adicione a implementação PerceptionSimulationManager.dll binário ao seu projeto de um.</span><span class="sxs-lookup"><span data-stu-id="0b94c-126">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="0b94c-127">Primeiro adicioná-lo como um binário para o projeto (Project -> Adicionar -> Item existente...). Salve-o como um link para que ele não copie-o para sua pasta de origem do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b94c-127">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="0b94c-128">![Adicionar PerceptionSimulationManager.dll ao projeto como um link](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="0b94c-128">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="0b94c-129">Em seguida, certifique-se de que ele obtenha do copiado para a pasta de saída no build.</span><span class="sxs-lookup"><span data-stu-id="0b94c-129">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="0b94c-130">Isso é na folha de propriedades para o binário.</span><span class="sxs-lookup"><span data-stu-id="0b94c-130">This is in the property sheet for the binary .</span></span> <span data-ttu-id="0b94c-131">![Marcar PerceptionSimulationManager.dll para copiar para diretório de saída](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="0b94c-131">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="0b94c-132">Criar um objeto do Gerenciador de IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="0b94c-132">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="0b94c-133">Para controlar a simulação, você vai emitir atualizações para objetos recuperados de um objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="0b94c-133">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="0b94c-134">A primeira etapa é obter esse objeto e conectá-lo ao seu dispositivo de destino ou o emulador.</span><span class="sxs-lookup"><span data-stu-id="0b94c-134">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="0b94c-135">Você pode obter o endereço IP do seu emulador clicando no botão no Portal do dispositivo o [barra de ferramentas](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span><span class="sxs-lookup"><span data-stu-id="0b94c-135">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span></span>

<span data-ttu-id="0b94c-136">![Ícone do Portal do dispositivo aberto](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: Abra o Windows Device Portal para o sistema de operacional HoloLens no emulador.</span><span class="sxs-lookup"><span data-stu-id="0b94c-136">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

<span data-ttu-id="0b94c-137">Primeiro, você chamará RestSimulationStreamSink.Create para obter um objeto RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="0b94c-137">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="0b94c-138">Esse é o dispositivo de destino ou o emulador que você irá controlar ao longo de uma conexão http.</span><span class="sxs-lookup"><span data-stu-id="0b94c-138">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="0b94c-139">Serão passados para seus comandos e tratados pelos [Windows Device Portal](using-the-windows-device-portal.md) em execução no dispositivo ou emulador.</span><span class="sxs-lookup"><span data-stu-id="0b94c-139">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="0b94c-140">Os quatro parâmetros, que você precisará criar um objeto são:</span><span class="sxs-lookup"><span data-stu-id="0b94c-140">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="0b94c-141">Uri de URI - endereço IP do dispositivo de destino (por exemplo, "http://123.123.123.123")</span><span class="sxs-lookup"><span data-stu-id="0b94c-141">Uri uri - IP address of the target device (e.g., "http://123.123.123.123")</span></span>
* <span data-ttu-id="0b94c-142">System.Net.NetworkCredential credenciais - nome de usuário e senha para conexão com o [Windows Device Portal](using-the-windows-device-portal.md) no emulador ou dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="0b94c-142">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="0b94c-143">Se você estiver se conectando ao emulador por meio de seu local 168. *.* . \* endereço no mesmo computador, todas as credenciais serão aceitas.</span><span class="sxs-lookup"><span data-stu-id="0b94c-143">If you are connecting to the emulator via its local 168.*.*.\* address on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="0b94c-144">bool normal - True para false para baixa prioridade com prioridade normal.</span><span class="sxs-lookup"><span data-stu-id="0b94c-144">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="0b94c-145">Geralmente, é recomendável definir isso como *verdadeira* para cenários de teste.</span><span class="sxs-lookup"><span data-stu-id="0b94c-145">You generally want to set this to *true* for test scenarios.</span></span>
* <span data-ttu-id="0b94c-146">Token cancellationtoken - Token para cancelar a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="0b94c-146">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="0b94c-147">Em segundo lugar, você criará o IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="0b94c-147">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="0b94c-148">Esse é o objeto que você pode usar para controlar a simulação.</span><span class="sxs-lookup"><span data-stu-id="0b94c-148">This is the object you use to control simulation.</span></span> <span data-ttu-id="0b94c-149">Observe que isso também deve ser feito em um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="0b94c-149">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="0b94c-150">Controle o ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-150">Control the simulated Human</span></span>

<span data-ttu-id="0b94c-151">Um IPerceptionSimulationManager tem uma propriedade humana que retorna um objeto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="0b94c-151">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="0b94c-152">Para controlar o ser humano simulado, execute operações nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="0b94c-152">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="0b94c-153">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="0b94c-153">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="0b94c-154">Exemplo básico C# aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="0b94c-154">Basic Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="0b94c-155">Estendida de exemplo C# aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="0b94c-155">Extended Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="api-reference"></a><span data-ttu-id="0b94c-156">Referência da API</span><span class="sxs-lookup"><span data-stu-id="0b94c-156">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="0b94c-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="0b94c-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="0b94c-158">Descreve um tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-158">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="0b94c-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="0b94c-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="0b94c-160">Um dispositivo de referência fictícia, o padrão para PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="0b94c-160">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="0b94c-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="0b94c-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="0b94c-162">Descreve um modo de rastreador principal</span><span class="sxs-lookup"><span data-stu-id="0b94c-162">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="0b94c-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="0b94c-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="0b94c-164">Padrão de controle de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="0b94c-164">Default Head Tracking.</span></span> <span data-ttu-id="0b94c-165">Isso significa que o sistema pode selecionar o melhor head com base em condições de tempo de execução do modo de controle.</span><span class="sxs-lookup"><span data-stu-id="0b94c-165">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="0b94c-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="0b94c-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="0b94c-167">Orientação de acompanhamento somente cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="0b94c-167">Orientation Only Head Tracking.</span></span> <span data-ttu-id="0b94c-168">Isso significa que a posição controlada pode não ser confiável, e alguma funcionalidade dependente de posição principal pode não estar disponível.</span><span class="sxs-lookup"><span data-stu-id="0b94c-168">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="0b94c-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="0b94c-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="0b94c-170">Controle de cabeçalho posicionais.</span><span class="sxs-lookup"><span data-stu-id="0b94c-170">Positional Head Tracking.</span></span> <span data-ttu-id="0b94c-171">Isso significa que a posição de cabeçalho controlada e orientação são confiáveis</span><span class="sxs-lookup"><span data-stu-id="0b94c-171">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="0b94c-172">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="0b94c-172">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="0b94c-173">Descreve um gesto simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-173">Describes a simulated gesture</span></span>

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

<span data-ttu-id="0b94c-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="0b94c-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="0b94c-175">Um valor de sentinela usado para não indicar nenhum gestos</span><span class="sxs-lookup"><span data-stu-id="0b94c-175">A sentinel value used to indicate no gestures</span></span>

<span data-ttu-id="0b94c-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="0b94c-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="0b94c-177">Um dedo pressionado gesto</span><span class="sxs-lookup"><span data-stu-id="0b94c-177">A finger pressed gesture</span></span>

<span data-ttu-id="0b94c-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="0b94c-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="0b94c-179">Um gesto de dedo lançado</span><span class="sxs-lookup"><span data-stu-id="0b94c-179">A finger released gesture</span></span>

<span data-ttu-id="0b94c-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="0b94c-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="0b94c-181">O gesto de base</span><span class="sxs-lookup"><span data-stu-id="0b94c-181">The home gesture</span></span>

<span data-ttu-id="0b94c-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="0b94c-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="0b94c-183">O gesto válido máximo</span><span class="sxs-lookup"><span data-stu-id="0b94c-183">The maximum valid gesture</span></span>

### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="0b94c-184">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="0b94c-184">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="0b94c-185">Descreve o estado de uma reprodução</span><span class="sxs-lookup"><span data-stu-id="0b94c-185">Describes the state of a playback</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="0b94c-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="0b94c-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="0b94c-187">A gravação está atualmente parado e pronto para reprodução</span><span class="sxs-lookup"><span data-stu-id="0b94c-187">The recording is currently stopped and ready for playback</span></span>

<span data-ttu-id="0b94c-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="0b94c-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="0b94c-189">A gravação está em execução no momento</span><span class="sxs-lookup"><span data-stu-id="0b94c-189">The recording is currently playing</span></span>

<span data-ttu-id="0b94c-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="0b94c-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="0b94c-191">A gravação estiver em pausa</span><span class="sxs-lookup"><span data-stu-id="0b94c-191">The recording is currently paused</span></span>

<span data-ttu-id="0b94c-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="0b94c-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="0b94c-193">A gravação atingiu o fim</span><span class="sxs-lookup"><span data-stu-id="0b94c-193">The recording has reached the end</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="0b94c-194">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="0b94c-194">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="0b94c-195">Descreve um vetor de 3 componentes, que pode descrever um ponto ou um vetor no espaço 3D</span><span class="sxs-lookup"><span data-stu-id="0b94c-195">Describes a 3 components vector, which might describe a point or a vector in 3D space</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="0b94c-196">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="0b94c-196">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="0b94c-197">O componente X do vetor</span><span class="sxs-lookup"><span data-stu-id="0b94c-197">The X component of the vector</span></span>

<span data-ttu-id="0b94c-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="0b94c-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="0b94c-199">O componente Y do vetor</span><span class="sxs-lookup"><span data-stu-id="0b94c-199">The Y component of the vector</span></span>

<span data-ttu-id="0b94c-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="0b94c-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="0b94c-201">O componente Z do vetor</span><span class="sxs-lookup"><span data-stu-id="0b94c-201">The Z component of the vector</span></span>

<span data-ttu-id="0b94c-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="0b94c-203">Construir um novo Vector3</span><span class="sxs-lookup"><span data-stu-id="0b94c-203">Construct a new Vector3</span></span>

<span data-ttu-id="0b94c-204">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-204">Parameters</span></span>
* <span data-ttu-id="0b94c-205">x - o componente x do vetor</span><span class="sxs-lookup"><span data-stu-id="0b94c-205">x - The x component of the vector</span></span>
* <span data-ttu-id="0b94c-206">y - o componente y do vetor</span><span class="sxs-lookup"><span data-stu-id="0b94c-206">y - The y component of the vector</span></span>
* <span data-ttu-id="0b94c-207">z - o componente z do vetor</span><span class="sxs-lookup"><span data-stu-id="0b94c-207">z - The z component of the vector</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="0b94c-208">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="0b94c-208">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="0b94c-209">Descreve uma rotação de 3 componentes</span><span class="sxs-lookup"><span data-stu-id="0b94c-209">Describes a 3 components rotation</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="0b94c-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="0b94c-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="0b94c-211">O componente de tom de rotação, faz uma busca em torno do eixo X</span><span class="sxs-lookup"><span data-stu-id="0b94c-211">The Pitch component of the Rotation, down around the X axis</span></span>

<span data-ttu-id="0b94c-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="0b94c-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="0b94c-213">O componente do desvio da rotação em torno do eixo Y</span><span class="sxs-lookup"><span data-stu-id="0b94c-213">The Yaw component of the Rotation, right around the Y axis</span></span>

<span data-ttu-id="0b94c-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="0b94c-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="0b94c-215">O componente de distribuição da rotação em torno do eixo Z</span><span class="sxs-lookup"><span data-stu-id="0b94c-215">The Roll component of the Rotation, right around the Z axis</span></span>

<span data-ttu-id="0b94c-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="0b94c-217">Construir um novo Rotation3</span><span class="sxs-lookup"><span data-stu-id="0b94c-217">Construct a new Rotation3</span></span>

<span data-ttu-id="0b94c-218">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-218">Parameters</span></span>
* <span data-ttu-id="0b94c-219">Tom - o componente de tom de rotação</span><span class="sxs-lookup"><span data-stu-id="0b94c-219">pitch - The pitch component of the Rotation</span></span>
* <span data-ttu-id="0b94c-220">yaw - o componente do desvio da rotação</span><span class="sxs-lookup"><span data-stu-id="0b94c-220">yaw - The yaw component of the Rotation</span></span>
* <span data-ttu-id="0b94c-221">roll - o componente de distribuição de rotação</span><span class="sxs-lookup"><span data-stu-id="0b94c-221">roll - The roll component of the Rotation</span></span>

### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="0b94c-222">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="0b94c-222">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="0b94c-223">Descreve um frustum do modo de exibição, como normalmente usada por uma câmera</span><span class="sxs-lookup"><span data-stu-id="0b94c-223">Describes a view frustum, as typically used by a camera</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="0b94c-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="0b94c-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="0b94c-225">A distância mínima que está contida no frustum</span><span class="sxs-lookup"><span data-stu-id="0b94c-225">The minimum distance that is contained in the frustum</span></span>

<span data-ttu-id="0b94c-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="0b94c-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="0b94c-227">A distância máxima que está contida no frustum</span><span class="sxs-lookup"><span data-stu-id="0b94c-227">The maximum distance that is contained in the frustum</span></span>

<span data-ttu-id="0b94c-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="0b94c-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="0b94c-229">O campo de exibição horizontal de frustum, em radianos (menor que o PI)</span><span class="sxs-lookup"><span data-stu-id="0b94c-229">The horizontal field of view of the frustum, in radians (less than PI)</span></span>

<span data-ttu-id="0b94c-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="0b94c-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="0b94c-231">A proporção de campo de exibição horizontal para o campo de exibição vertical</span><span class="sxs-lookup"><span data-stu-id="0b94c-231">The ratio of horizontal field of view to vertical field of view</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="0b94c-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="0b94c-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="0b94c-233">Raiz para gerar os pacotes usados para controlar um dispositivo</span><span class="sxs-lookup"><span data-stu-id="0b94c-233">Root for generating the packets used to control a device</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="0b94c-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="0b94c-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="0b94c-235">Recupere o objeto de dispositivo simulado que interpreta o ser humano simulado e o mundo simulado.</span><span class="sxs-lookup"><span data-stu-id="0b94c-235">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="0b94c-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="0b94c-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="0b94c-237">Recupere o objeto que controla o ser humano simulado.</span><span class="sxs-lookup"><span data-stu-id="0b94c-237">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="0b94c-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="0b94c-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="0b94c-239">Redefine a simulação para seu estado padrão.</span><span class="sxs-lookup"><span data-stu-id="0b94c-239">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="0b94c-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="0b94c-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="0b94c-241">Interface que descreve o dispositivo que interpreta o mundo simulado e o ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-241">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="0b94c-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="0b94c-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="0b94c-243">Recupere a posição da cabeça do dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="0b94c-243">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="0b94c-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="0b94c-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="0b94c-245">Recupere o rastreador de mão do dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="0b94c-245">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="0b94c-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="0b94c-247">Defina as propriedades do dispositivo simulado para corresponder ao tipo de dispositivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="0b94c-247">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="0b94c-248">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-248">Parameters</span></span>
* <span data-ttu-id="0b94c-249">Digite - o novo tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-249">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="0b94c-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="0b94c-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="0b94c-251">Interface que descreve a parte do dispositivo simulado que rastreia o cabeçalho do ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-251">Interface describing the portion of the simulated device that tracks the head of the simulated human</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="0b94c-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="0b94c-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="0b94c-253">Recupera e define o modo atual do controlador principal.</span><span class="sxs-lookup"><span data-stu-id="0b94c-253">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="0b94c-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="0b94c-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="0b94c-255">Interface que descreve a parte do dispositivo simulado que rastreia as mãos do ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-255">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

<span data-ttu-id="0b94c-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="0b94c-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="0b94c-257">Recuperar a posição do nó com relação ao mundo, em metros</span><span class="sxs-lookup"><span data-stu-id="0b94c-257">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="0b94c-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="0b94c-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="0b94c-259">Recuperar e definir a posição do controlador mão simulado, em relação ao centro do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="0b94c-259">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="0b94c-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="0b94c-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="0b94c-261">Recuperar e definir o tom para baixo do controlador mão simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-261">Retrieve and set the downward pitch of the simulated hand tracker</span></span>

<span data-ttu-id="0b94c-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="0b94c-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="0b94c-263">Recuperar e definir se o frustum do controlador mão simulado é ignorado.</span><span class="sxs-lookup"><span data-stu-id="0b94c-263">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="0b94c-264">Quando ignoradas, ambas as mãos estão sempre visíveis.</span><span class="sxs-lookup"><span data-stu-id="0b94c-264">When ignored, both hands are always visible.</span></span> <span data-ttu-id="0b94c-265">Quando não ignoradas (padrão) mãos são visíveis apenas quando estes estiverem dentro a frustum do controlador disponível.</span><span class="sxs-lookup"><span data-stu-id="0b94c-265">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="0b94c-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="0b94c-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="0b94c-267">Recuperar e definir as propriedades de frustum usadas para determinar se as mãos são visíveis para o rastreador de mão simulado.</span><span class="sxs-lookup"><span data-stu-id="0b94c-267">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="0b94c-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="0b94c-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="0b94c-269">Interface de nível superior para controlar o ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-269">Top level interface for controlling the simulated human</span></span>

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

<span data-ttu-id="0b94c-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="0b94c-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="0b94c-271">Recuperar e definir a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="0b94c-271">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="0b94c-272">A posição corresponde a um ponto no Centro de metros do humanos.</span><span class="sxs-lookup"><span data-stu-id="0b94c-272">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="0b94c-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="0b94c-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="0b94c-274">Recuperar e definir a direção de faces humanas simuladas no mundo.</span><span class="sxs-lookup"><span data-stu-id="0b94c-274">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="0b94c-275">0 radianos faces para baixo do eixo Z negativo.</span><span class="sxs-lookup"><span data-stu-id="0b94c-275">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="0b94c-276">Radianos positivos giram no sentido horário sobre o eixo Y.</span><span class="sxs-lookup"><span data-stu-id="0b94c-276">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="0b94c-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="0b94c-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="0b94c-278">Recuperar e definir a altura do ser humano simulado, em metros</span><span class="sxs-lookup"><span data-stu-id="0b94c-278">Retrieve and set the height of the simulated human, in meters</span></span>

<span data-ttu-id="0b94c-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="0b94c-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="0b94c-280">Recuperar o lado esquerdo do ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-280">Retrieve the left hand of the simulated human</span></span>

<span data-ttu-id="0b94c-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="0b94c-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="0b94c-282">Recuperar o direito do ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-282">Retrieve the right hand of the simulated human</span></span>

<span data-ttu-id="0b94c-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="0b94c-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="0b94c-284">Recuperar o cabeçalho do ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-284">Retrieve the head of the simulated human</span></span>

<span data-ttu-id="0b94c-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="0b94c-286">Mover o ser humano simulado em relação à posição atual, em metros</span><span class="sxs-lookup"><span data-stu-id="0b94c-286">Move the simulated human relative to its current position, in meters</span></span>

<span data-ttu-id="0b94c-287">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-287">Parameters</span></span>
* <span data-ttu-id="0b94c-288">conversão - a tradução para mover em relação à posição atual</span><span class="sxs-lookup"><span data-stu-id="0b94c-288">translation - The translation to move, relative to current position</span></span>

<span data-ttu-id="0b94c-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="0b94c-290">Girar o ser humano simulado em relação à sua direção atual, no sentido horário sobre o eixo Y</span><span class="sxs-lookup"><span data-stu-id="0b94c-290">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="0b94c-291">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-291">Parameters</span></span>
* <span data-ttu-id="0b94c-292">radianos - a quantidade de rotação ao redor do eixo Y</span><span class="sxs-lookup"><span data-stu-id="0b94c-292">radians - The amount to rotate around the Y axis</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="0b94c-293">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="0b94c-293">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="0b94c-294">Interface que descreve uma mão do ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-294">Interface describing a hand of the simulated human</span></span>

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

<span data-ttu-id="0b94c-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="0b94c-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="0b94c-296">Recuperar a posição do nó com relação ao mundo, em metros</span><span class="sxs-lookup"><span data-stu-id="0b94c-296">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="0b94c-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="0b94c-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="0b94c-298">Recuperar e definir a posição da mão simulado em relação ao ser humano, em metros.</span><span class="sxs-lookup"><span data-stu-id="0b94c-298">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="0b94c-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="0b94c-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="0b94c-300">Recuperar e definir se a mão está ativada no momento.</span><span class="sxs-lookup"><span data-stu-id="0b94c-300">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="0b94c-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="0b94c-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="0b94c-302">Recupere se a mão está atualmente visível para o SimulatedDevice (ou seja, seja em uma posição para ser detectada pelo HandTracker).</span><span class="sxs-lookup"><span data-stu-id="0b94c-302">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="0b94c-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="0b94c-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="0b94c-304">Mova a mão, que é visível para o SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="0b94c-304">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="0b94c-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="0b94c-306">Mova a posição da mão simulado em relação à posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="0b94c-306">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="0b94c-307">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-307">Parameters</span></span>
* <span data-ttu-id="0b94c-308">tradução - o valor para converter a mão simulada</span><span class="sxs-lookup"><span data-stu-id="0b94c-308">translation - The amount to translate the simulated hand</span></span>

<span data-ttu-id="0b94c-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="0b94c-310">Execute um gesto usando a mão simulada (ela só será detectada pelo sistema se a mão estiver habilitada).</span><span class="sxs-lookup"><span data-stu-id="0b94c-310">Perform a gesture using the simulated hand (it will only be detected by the system if the hand is enabled).</span></span>

<span data-ttu-id="0b94c-311">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-311">Parameters</span></span>
* <span data-ttu-id="0b94c-312">gesto - o gesto para executar</span><span class="sxs-lookup"><span data-stu-id="0b94c-312">gesture - The gesture to perform</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="0b94c-313">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="0b94c-313">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="0b94c-314">Interface que descreve o cabeçalho do ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="0b94c-314">Interface describing the head of the simulated human</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="0b94c-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="0b94c-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="0b94c-316">Recuperar a posição do nó com relação ao mundo, em metros</span><span class="sxs-lookup"><span data-stu-id="0b94c-316">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="0b94c-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="0b94c-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="0b94c-318">Recupere a rotação da cabeça de simulado.</span><span class="sxs-lookup"><span data-stu-id="0b94c-318">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="0b94c-319">Radianos girar no sentido horário ao procurar ao longo do eixo positivo.</span><span class="sxs-lookup"><span data-stu-id="0b94c-319">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="0b94c-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="0b94c-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="0b94c-321">Recupere o diâmetro da cabeça simulado.</span><span class="sxs-lookup"><span data-stu-id="0b94c-321">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="0b94c-322">Esse valor é usado para determinar o centro do head (ponto de rotação).</span><span class="sxs-lookup"><span data-stu-id="0b94c-322">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="0b94c-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="0b94c-324">Gire o head simulado em relação à sua rotação atual.</span><span class="sxs-lookup"><span data-stu-id="0b94c-324">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="0b94c-325">Radianos girar no sentido horário ao procurar ao longo do eixo positivo.</span><span class="sxs-lookup"><span data-stu-id="0b94c-325">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="0b94c-326">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-326">Parameters</span></span>
* <span data-ttu-id="0b94c-327">rotação - a quantidade de rotação</span><span class="sxs-lookup"><span data-stu-id="0b94c-327">rotation - The amount to rotate</span></span>

### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="0b94c-328">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="0b94c-328">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="0b94c-329">Carregar a interface para interagir com uma única gravação para reprodução.</span><span class="sxs-lookup"><span data-stu-id="0b94c-329">Interface for interacting with a single recording loaded for playback.</span></span>

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

<span data-ttu-id="0b94c-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="0b94c-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="0b94c-331">Recupera a lista de tipos de dados na gravação.</span><span class="sxs-lookup"><span data-stu-id="0b94c-331">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="0b94c-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="0b94c-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="0b94c-333">Recupera o estado atual da gravação.</span><span class="sxs-lookup"><span data-stu-id="0b94c-333">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="0b94c-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="0b94c-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="0b94c-335">Inicie a reprodução.</span><span class="sxs-lookup"><span data-stu-id="0b94c-335">Start the playback.</span></span> <span data-ttu-id="0b94c-336">Se a gravação for pausada, a reprodução será retomada do local em pausa; Se interrompida, a reprodução será iniciada no início.</span><span class="sxs-lookup"><span data-stu-id="0b94c-336">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="0b94c-337">Se já em execução, essa chamada é ignorada.</span><span class="sxs-lookup"><span data-stu-id="0b94c-337">If already playing, this call is ignored.</span></span>

<span data-ttu-id="0b94c-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="0b94c-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="0b94c-339">Pausa a reprodução em seu local atual.</span><span class="sxs-lookup"><span data-stu-id="0b94c-339">Pauses the playback at its current location.</span></span> <span data-ttu-id="0b94c-340">Se a gravação for interrompida, a chamada será ignorada.</span><span class="sxs-lookup"><span data-stu-id="0b94c-340">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="0b94c-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="0b94c-342">Procura a gravação de tempo especificado (em intervalos de 100 nanossegundos desde o início) e faz uma pausa nesse local.</span><span class="sxs-lookup"><span data-stu-id="0b94c-342">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="0b94c-343">Se o tempo está além do fim da gravação, ele está em pausa no último quadro.</span><span class="sxs-lookup"><span data-stu-id="0b94c-343">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="0b94c-344">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-344">Parameters</span></span>
* <span data-ttu-id="0b94c-345">tiques - o tempo para o qual a busca</span><span class="sxs-lookup"><span data-stu-id="0b94c-345">ticks - The time to which to seek</span></span>

<span data-ttu-id="0b94c-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="0b94c-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="0b94c-347">Interrompe a reprodução e redefine a posição para o início</span><span class="sxs-lookup"><span data-stu-id="0b94c-347">Stops the playback and resets the position to the beginning</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="0b94c-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="0b94c-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="0b94c-349">Interface para receber alterações de estado durante a reprodução</span><span class="sxs-lookup"><span data-stu-id="0b94c-349">Interface for receiving state changes during playback</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="0b94c-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="0b94c-351">Chamado quando o estado de reprodução de um ISimulationRecording foi alterado</span><span class="sxs-lookup"><span data-stu-id="0b94c-351">Called when an ISimulationRecording's playback state has changed</span></span>

<span data-ttu-id="0b94c-352">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-352">Parameters</span></span>
* <span data-ttu-id="0b94c-353">newState - o novo estado da gravação</span><span class="sxs-lookup"><span data-stu-id="0b94c-353">newState - The new state of the recording</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="0b94c-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="0b94c-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="0b94c-355">Objeto raiz para a criação de objetos de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="0b94c-355">Root object for creating Perception Simulation objects</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="0b94c-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="0b94c-357">Crie no objeto para gerar pacotes simulados e entregá-los para o coletor fornecido.</span><span class="sxs-lookup"><span data-stu-id="0b94c-357">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="0b94c-358">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-358">Parameters</span></span>
* <span data-ttu-id="0b94c-359">coletor - coletor que receberá os pacotes gerados</span><span class="sxs-lookup"><span data-stu-id="0b94c-359">sink - The sink that will receive all generated packets</span></span>

<span data-ttu-id="0b94c-360">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="0b94c-360">Return value</span></span>

<span data-ttu-id="0b94c-361">O Gerenciador de criado</span><span class="sxs-lookup"><span data-stu-id="0b94c-361">The created Manager</span></span>

<span data-ttu-id="0b94c-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="0b94c-363">Crie um coletor que armazena os pacotes recebidos tudo em um arquivo no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="0b94c-363">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="0b94c-364">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-364">Parameters</span></span>
* <span data-ttu-id="0b94c-365">caminho - o caminho do arquivo a ser criado</span><span class="sxs-lookup"><span data-stu-id="0b94c-365">path - The path of the file to create</span></span>

<span data-ttu-id="0b94c-366">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="0b94c-366">Return value</span></span>

<span data-ttu-id="0b94c-367">O coletor criado</span><span class="sxs-lookup"><span data-stu-id="0b94c-367">The created sink</span></span>

<span data-ttu-id="0b94c-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="0b94c-369">Carregar uma gravação do arquivo especificado</span><span class="sxs-lookup"><span data-stu-id="0b94c-369">Load a recording from the specified file</span></span>

<span data-ttu-id="0b94c-370">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-370">Parameters</span></span>
* <span data-ttu-id="0b94c-371">caminho - o caminho do arquivo a ser carregado</span><span class="sxs-lookup"><span data-stu-id="0b94c-371">path - The path of the file to load</span></span>
* <span data-ttu-id="0b94c-372">fábrica - um alocador usado pela gravação para a criação de um ISimulationStreamSink quando necessário</span><span class="sxs-lookup"><span data-stu-id="0b94c-372">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>

<span data-ttu-id="0b94c-373">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="0b94c-373">Return value</span></span>

<span data-ttu-id="0b94c-374">A gravação carregada</span><span class="sxs-lookup"><span data-stu-id="0b94c-374">The loaded recording</span></span>

<span data-ttu-id="0b94c-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="0b94c-376">Carregar uma gravação do arquivo especificado</span><span class="sxs-lookup"><span data-stu-id="0b94c-376">Load a recording from the specified file</span></span>

<span data-ttu-id="0b94c-377">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-377">Parameters</span></span>
* <span data-ttu-id="0b94c-378">caminho - o caminho do arquivo a ser carregado</span><span class="sxs-lookup"><span data-stu-id="0b94c-378">path - The path of the file to load</span></span>
* <span data-ttu-id="0b94c-379">fábrica - um alocador usado pela gravação para a criação de um ISimulationStreamSink quando necessário</span><span class="sxs-lookup"><span data-stu-id="0b94c-379">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>
* <span data-ttu-id="0b94c-380">atualizações de um retorno de chamada que recebe o retorno de chamada - regrading status da gravação</span><span class="sxs-lookup"><span data-stu-id="0b94c-380">callback - A callback which receives updates regrading the recording's status</span></span>

<span data-ttu-id="0b94c-381">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="0b94c-381">Return value</span></span>

<span data-ttu-id="0b94c-382">A gravação carregada</span><span class="sxs-lookup"><span data-stu-id="0b94c-382">The loaded recording</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="0b94c-383">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="0b94c-383">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="0b94c-384">Descreve os diferentes tipos de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="0b94c-384">Describes the different types of stream data</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    All = None | Head | Hands | SpatialMapping | Calibration | Environment
}
```

<span data-ttu-id="0b94c-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="0b94c-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="0b94c-386">Um valor de sentinela usado para não indicar nenhum tipo de dados de fluxo</span><span class="sxs-lookup"><span data-stu-id="0b94c-386">A sentinel value used to indicate no stream data types</span></span>

<span data-ttu-id="0b94c-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="0b94c-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="0b94c-388">Stream de dados em relação à posição e orientação do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="0b94c-388">Stream of data regarding the position and orientation of the head</span></span>

<span data-ttu-id="0b94c-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="0b94c-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="0b94c-390">Stream de dados em relação à posição e gestos de mãos</span><span class="sxs-lookup"><span data-stu-id="0b94c-390">Stream of data regarding the position and gestures of hands</span></span>

<span data-ttu-id="0b94c-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="0b94c-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="0b94c-392">Stream de dados relativos ao mapeamento espacial do ambiente</span><span class="sxs-lookup"><span data-stu-id="0b94c-392">Stream of data regarding spatial mapping of the environment</span></span>

<span data-ttu-id="0b94c-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="0b94c-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="0b94c-394">Stream de dados em relação à calibragem do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0b94c-394">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="0b94c-395">Pacotes de calibragem somente são aceitas por um sistema no modo remoto.</span><span class="sxs-lookup"><span data-stu-id="0b94c-395">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="0b94c-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="0b94c-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="0b94c-397">Stream de dados sobre o ambiente do dispositivo</span><span class="sxs-lookup"><span data-stu-id="0b94c-397">Stream of data regarding the environment of the device</span></span>

<span data-ttu-id="0b94c-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="0b94c-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="0b94c-399">Um valor de sentinela usado para indicar todos os tipos de dados gravados</span><span class="sxs-lookup"><span data-stu-id="0b94c-399">A sentinel value used to indicate all recorded data types</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="0b94c-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="0b94c-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="0b94c-401">Um objeto que recebe os pacotes de dados de um fluxo de simulação</span><span class="sxs-lookup"><span data-stu-id="0b94c-401">An object that receives data packets from a simulation stream</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="0b94c-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span><span class="sxs-lookup"><span data-stu-id="0b94c-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="0b94c-403">Recebe um único pacote, o que é internamente com tipo e com controle de versão</span><span class="sxs-lookup"><span data-stu-id="0b94c-403">Receives a single packet, which is internally typed and versioned</span></span>

<span data-ttu-id="0b94c-404">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b94c-404">Parameters</span></span>
* <span data-ttu-id="0b94c-405">comprimento - o tamanho do pacote</span><span class="sxs-lookup"><span data-stu-id="0b94c-405">length - The length of the packet</span></span>
* <span data-ttu-id="0b94c-406">pacote - os dados do pacote</span><span class="sxs-lookup"><span data-stu-id="0b94c-406">packet - The data of the packet</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="0b94c-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="0b94c-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="0b94c-408">Um objeto que cria ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="0b94c-408">An object that creates ISimulationStreamSink</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="0b94c-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="0b94c-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="0b94c-410">Cria uma única instância de ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="0b94c-410">Creates a single instance of ISimulationStreamSink</span></span>

<span data-ttu-id="0b94c-411">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="0b94c-411">Return value</span></span>

<span data-ttu-id="0b94c-412">O coletor criado</span><span class="sxs-lookup"><span data-stu-id="0b94c-412">The created sink</span></span>
