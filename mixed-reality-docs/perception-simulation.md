---
title: Simulação de percepção
description: Um guia para usar a biblioteca de simulação de percepção para automatizar entrada simulada para aplicativos imersivos
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, simulação, testando
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414528"
---
# <a name="perception-simulation"></a><span data-ttu-id="dc454-104">Simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="dc454-104">Perception simulation</span></span>

<span data-ttu-id="dc454-105">Você deseja criar um teste automatizado para seu aplicativo?</span><span class="sxs-lookup"><span data-stu-id="dc454-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="dc454-106">Você deseja que seus testes ir além dos testes de unidade de nível de componente e realmente exercitar seu aplicativo ponta a ponta?</span><span class="sxs-lookup"><span data-stu-id="dc454-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="dc454-107">Simulação de percepção é o que você está procurando.</span><span class="sxs-lookup"><span data-stu-id="dc454-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="dc454-108">A biblioteca de simulação de percepção envia humana e world dados de entrada para seu aplicativo para que você possa automatizar seus testes.</span><span class="sxs-lookup"><span data-stu-id="dc454-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="dc454-109">Por exemplo, você pode simular a entrada de um humano procurando uma posição específica, repetível e, em seguida, executar um gesto ou usando um controlador de animação.</span><span class="sxs-lookup"><span data-stu-id="dc454-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="dc454-110">Simulação de percepção pode enviar entrada simulada como esta para um HoloLens físico, o emulador do HoloLens instalado do (1º gen), o HoloLens 2 emulador ou em um computador com o Portal de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="dc454-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="dc454-111">Percepção de simulação ignora os sensores em tempo real em um dispositivo de realidade mista e envia simulados de entrada para aplicativos em execução no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="dc454-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="dc454-112">Aplicativos recebem esses eventos de entrada por meio das mesmas APIs que eles sempre usam e não podem determinar a diferença entre executar com sensores reais versus executando com simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="dc454-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="dc454-113">Simulação de percepção é a mesma tecnologia usada por emuladores do HoloLens enviem dados de entrada para a máquina Virtual HoloLens simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="dc454-114">Para começar a usar a simulação em seu código, comece criando um objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="dc454-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="dc454-115">A partir desse objeto, você pode emitir comandos para controlar propriedades de um simulado "humana", incluindo o cabeçalho de posição, a posição de mão e gestos, e você pode habilitar e manipular os controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="dc454-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="dc454-116">Como configurar um projeto do Visual Studio para a percepção de simulação</span><span class="sxs-lookup"><span data-stu-id="dc454-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="dc454-117">[Instalar o emulador do HoloLens](install-the-tools.md) em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="dc454-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="dc454-118">O emulador inclui as bibliotecas que você usará para a simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="dc454-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="dc454-119">Criar um novo Visual Studio C# projeto da área de trabalho (um projeto de Console funciona muito bem de começar a usar).</span><span class="sxs-lookup"><span data-stu-id="dc454-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="dc454-120">Adicione os seguintes binários ao seu projeto como referências (projeto -> Adicionar -> referência...). Você pode encontrá-los em % ProgramFiles (x86) %\Microsoft XDE\\(versão), como **% ProgramFiles (x86) %\Microsoft XDE\\10.0.18362.0** para o emulador de 2 HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dc454-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="dc454-121">(Observação: Embora os binários fazem parte do emulador 2 HoloLens, eles também funcionam para o Windows Mixed Reality na área de trabalho.) a.</span><span class="sxs-lookup"><span data-stu-id="dc454-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="dc454-122">PerceptionSimulationManager.Interop.dll - gerenciados C# wrapper para a simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="dc454-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="dc454-123">b.</span><span class="sxs-lookup"><span data-stu-id="dc454-123">b.</span></span> <span data-ttu-id="dc454-124">PerceptionSimulationRest.dll - Library para configurar um canal de comunicação de soquete da web para o HoloLens ou emulador.</span><span class="sxs-lookup"><span data-stu-id="dc454-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="dc454-125">c.</span><span class="sxs-lookup"><span data-stu-id="dc454-125">c.</span></span> <span data-ttu-id="dc454-126">SimulationStream.Interop.dll - tipos compartilhados para simulação.</span><span class="sxs-lookup"><span data-stu-id="dc454-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="dc454-127">Adicione a implementação PerceptionSimulationManager.dll binário ao seu projeto de um.</span><span class="sxs-lookup"><span data-stu-id="dc454-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="dc454-128">Primeiro adicioná-lo como um binário para o projeto (Project -> Adicionar -> Item existente...). Salve-o como um link para que ele não copie-o para sua pasta de origem do projeto.</span><span class="sxs-lookup"><span data-stu-id="dc454-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="dc454-129">![Adicionar PerceptionSimulationManager.dll ao projeto como um link](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="dc454-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="dc454-130">Em seguida, certifique-se de que ele obtenha do copiado para a pasta de saída no build.</span><span class="sxs-lookup"><span data-stu-id="dc454-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="dc454-131">Isso é na folha de propriedades para o binário.</span><span class="sxs-lookup"><span data-stu-id="dc454-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="dc454-132">![Marcar PerceptionSimulationManager.dll para copiar para diretório de saída](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="dc454-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="dc454-133">Defina sua plataforma de solução ativa como x64.</span><span class="sxs-lookup"><span data-stu-id="dc454-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="dc454-134">(Use o Configuration Manager para criar uma entrada de plataforma para x64, se ainda não existir).</span><span class="sxs-lookup"><span data-stu-id="dc454-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="dc454-135">Criar um objeto do Gerenciador de IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="dc454-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="dc454-136">Para controlar a simulação, você vai emitir atualizações para objetos recuperados de um objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="dc454-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="dc454-137">A primeira etapa é obter esse objeto e conectá-lo ao seu dispositivo de destino ou o emulador.</span><span class="sxs-lookup"><span data-stu-id="dc454-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="dc454-138">Você pode obter o endereço IP do seu emulador clicando no botão no Portal do dispositivo o [barra de ferramentas](using-the-hololens-emulator.md)</span><span class="sxs-lookup"><span data-stu-id="dc454-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="dc454-139">![Ícone do Portal do dispositivo aberto](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: Abre o Portal de Dispositivos do Windows para o sistema operacional HoloLens no emulador.</span><span class="sxs-lookup"><span data-stu-id="dc454-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="dc454-140">Para Windows Mixed Reality, isso pode ser recuperado no aplicativo de configurações em "Atualização e segurança" e "para desenvolvedores" no "conectar-se usando:" seção em "Habilitar Portal de dispositivo".</span><span class="sxs-lookup"><span data-stu-id="dc454-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="dc454-141">Certifique-se de observar o endereço IP e a porta.</span><span class="sxs-lookup"><span data-stu-id="dc454-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="dc454-142">Primeiro, você chamará RestSimulationStreamSink.Create para obter um objeto RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="dc454-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="dc454-143">Esse é o dispositivo de destino ou o emulador que você irá controlar ao longo de uma conexão http.</span><span class="sxs-lookup"><span data-stu-id="dc454-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="dc454-144">Serão passados para seus comandos e tratados pelos [Windows Device Portal](using-the-windows-device-portal.md) em execução no dispositivo ou emulador.</span><span class="sxs-lookup"><span data-stu-id="dc454-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="dc454-145">Os quatro parâmetros, que você precisará criar um objeto são:</span><span class="sxs-lookup"><span data-stu-id="dc454-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="dc454-146">Uri de URI - endereço IP do dispositivo de destino (por exemplo, "http://123.123.123.123"ou"http://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="dc454-146">Uri uri - IP address of the target device (e.g., "http://123.123.123.123" or "http://123.123.123.123:50080")</span></span>
* <span data-ttu-id="dc454-147">System.Net.NetworkCredential credenciais - nome de usuário e senha para conexão com o [Windows Device Portal](using-the-windows-device-portal.md) no emulador ou dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="dc454-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="dc454-148">Se você estiver se conectando ao emulador por meio de seu endereço local (por exemplo, 168. *.* . \*) no mesmo computador, todas as credenciais serão aceitas.</span><span class="sxs-lookup"><span data-stu-id="dc454-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="dc454-149">bool normal - True para false para baixa prioridade com prioridade normal.</span><span class="sxs-lookup"><span data-stu-id="dc454-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="dc454-150">Geralmente, é recomendável definir isso como *verdadeira* para cenários de teste, que permite que seu teste para assumir o controle.</span><span class="sxs-lookup"><span data-stu-id="dc454-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="dc454-151">O emulador e a simulação de realidade mista do Windows usam conexões de baixa prioridade.</span><span class="sxs-lookup"><span data-stu-id="dc454-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="dc454-152">Se o teste também usa uma conexão de baixa prioridade, mais recentemente estabelecida conexão será no controle.</span><span class="sxs-lookup"><span data-stu-id="dc454-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="dc454-153">Token cancellationtoken - Token para cancelar a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="dc454-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="dc454-154">Em segundo lugar, você criará o IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="dc454-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="dc454-155">Esse é o objeto que você pode usar para controlar a simulação.</span><span class="sxs-lookup"><span data-stu-id="dc454-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="dc454-156">Observe que isso também deve ser feito em um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="dc454-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="dc454-157">Controle o ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="dc454-157">Control the simulated Human</span></span>

<span data-ttu-id="dc454-158">Um IPerceptionSimulationManager tem uma propriedade humana que retorna um objeto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="dc454-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="dc454-159">Para controlar o ser humano simulado, execute operações nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="dc454-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="dc454-160">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="dc454-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="dc454-161">Exemplo básico C# aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="dc454-161">Basic Sample C# console application</span></span>

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
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="dc454-162">Estendida de exemplo C# aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="dc454-162">Extended Sample C# console application</span></span>

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
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

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

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="dc454-163">Observe nos controladores DOF 6</span><span class="sxs-lookup"><span data-stu-id="dc454-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="dc454-164">Antes de chamar métodos em um controlador de 6-DOF simulado todas as propriedades, você deve ativar o controlador.</span><span class="sxs-lookup"><span data-stu-id="dc454-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="dc454-165">Isso resultará em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="dc454-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="dc454-166">Começando com o Windows 10 atualização de 2019 de maio, controladores de 6-DOF simulado podem ser instalados e ativados, definindo a propriedade de Status no objeto ISimulatedSixDofController para SimulatedSixDofControllerStatus.Active.</span><span class="sxs-lookup"><span data-stu-id="dc454-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="dc454-167">No Windows 10 de outubro de 2018 atualizar e anterior, você deve separadamente instalar um controlador de 6-DOF simulado primeiro ao chamar a ferramenta PerceptionSimulationDevice localizada na pasta \Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="dc454-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="dc454-168">O uso dessa ferramenta é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="dc454-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="dc454-169">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="dc454-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="dc454-170">Ações com suporte são:</span><span class="sxs-lookup"><span data-stu-id="dc454-170">Supported actions are:</span></span>
* <span data-ttu-id="dc454-171">Eu = install</span><span class="sxs-lookup"><span data-stu-id="dc454-171">i = install</span></span>
* <span data-ttu-id="dc454-172">q = query</span><span class="sxs-lookup"><span data-stu-id="dc454-172">q = query</span></span>
* <span data-ttu-id="dc454-173">r = remove</span><span class="sxs-lookup"><span data-stu-id="dc454-173">r = remove</span></span>

<span data-ttu-id="dc454-174">Instâncias com suporte são:</span><span class="sxs-lookup"><span data-stu-id="dc454-174">Supported instances are:</span></span>
* <span data-ttu-id="dc454-175">1 = o controlador de 6-DOF esquerdo</span><span class="sxs-lookup"><span data-stu-id="dc454-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="dc454-176">2 = o controlador certo 6-DOF</span><span class="sxs-lookup"><span data-stu-id="dc454-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="dc454-177">O código de saída do processo de indicará êxito (valor de retorno de um zero) ou falha (um valor retornado diferente de zero).</span><span class="sxs-lookup"><span data-stu-id="dc454-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="dc454-178">Ao usar a ação 'p' para consultar ou não um controlador está instalado, o valor de retorno será 0 (zero) se o controlador já não estiver instalado ou um (1) se o controlador está instalado.</span><span class="sxs-lookup"><span data-stu-id="dc454-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="dc454-179">Ao remover um controlador no Windows 10 de outubro de 2018 atualizar ou anteriormente, definir seu status como desativado por meio da API em primeiro lugar, em seguida, chame a ferramenta PerceptionSimulationDevice.</span><span class="sxs-lookup"><span data-stu-id="dc454-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="dc454-180">Observe que essa ferramenta deve ser executada como administrador.</span><span class="sxs-lookup"><span data-stu-id="dc454-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="dc454-181">Referência da API</span><span class="sxs-lookup"><span data-stu-id="dc454-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="dc454-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="dc454-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="dc454-183">Descreve um tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="dc454-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="dc454-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="dc454-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="dc454-185">Um dispositivo de referência fictícia, o padrão para PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="dc454-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="dc454-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="dc454-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="dc454-187">Descreve um modo de rastreador principal</span><span class="sxs-lookup"><span data-stu-id="dc454-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="dc454-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="dc454-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="dc454-189">Padrão de controle de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="dc454-189">Default Head Tracking.</span></span> <span data-ttu-id="dc454-190">Isso significa que o sistema pode selecionar o melhor head com base em condições de tempo de execução do modo de controle.</span><span class="sxs-lookup"><span data-stu-id="dc454-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="dc454-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="dc454-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="dc454-192">Orientação de acompanhamento somente cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="dc454-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="dc454-193">Isso significa que a posição controlada pode não ser confiável, e alguma funcionalidade dependente de posição principal pode não estar disponível.</span><span class="sxs-lookup"><span data-stu-id="dc454-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="dc454-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="dc454-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="dc454-195">Controle de cabeçalho posicionais.</span><span class="sxs-lookup"><span data-stu-id="dc454-195">Positional Head Tracking.</span></span> <span data-ttu-id="dc454-196">Isso significa que a posição de cabeçalho controlada e orientação são confiáveis</span><span class="sxs-lookup"><span data-stu-id="dc454-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="dc454-197">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="dc454-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="dc454-198">Descreve um gesto simulado</span><span class="sxs-lookup"><span data-stu-id="dc454-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="dc454-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="dc454-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="dc454-200">Um valor de sentinela usado para não indicar nenhum gestos.</span><span class="sxs-lookup"><span data-stu-id="dc454-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="dc454-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="dc454-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="dc454-202">Um dedo pressionado gesto.</span><span class="sxs-lookup"><span data-stu-id="dc454-202">A finger pressed gesture.</span></span>

<span data-ttu-id="dc454-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="dc454-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="dc454-204">Um gesto de dedo lançado.</span><span class="sxs-lookup"><span data-stu-id="dc454-204">A finger released gesture.</span></span>

<span data-ttu-id="dc454-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="dc454-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="dc454-206">O gesto do sistema de home /.</span><span class="sxs-lookup"><span data-stu-id="dc454-206">The home/system gesture.</span></span>

<span data-ttu-id="dc454-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="dc454-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="dc454-208">O gesto válido máximo.</span><span class="sxs-lookup"><span data-stu-id="dc454-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="dc454-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="dc454-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="dc454-210">Os possíveis estados de um controlador de 6-DOF simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="dc454-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span><span class="sxs-lookup"><span data-stu-id="dc454-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="dc454-212">O controlador DOF 6 está desativado.</span><span class="sxs-lookup"><span data-stu-id="dc454-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="dc454-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span><span class="sxs-lookup"><span data-stu-id="dc454-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="dc454-214">O controlador DOF 6 está ligado e controlado.</span><span class="sxs-lookup"><span data-stu-id="dc454-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="dc454-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="dc454-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="dc454-216">O controlador DOF 6 está ativado, mas não pode ser rastreado.</span><span class="sxs-lookup"><span data-stu-id="dc454-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="dc454-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="dc454-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="dc454-218">Os botões com suporte em um controlador de 6-DOF simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-218">The supported buttons on a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

<span data-ttu-id="dc454-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span><span class="sxs-lookup"><span data-stu-id="dc454-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="dc454-220">Um valor de sentinela usado para não indicar nenhum botão.</span><span class="sxs-lookup"><span data-stu-id="dc454-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="dc454-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span><span class="sxs-lookup"><span data-stu-id="dc454-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="dc454-222">A página inicial é pressionado.</span><span class="sxs-lookup"><span data-stu-id="dc454-222">The Home button is pressed.</span></span>

<span data-ttu-id="dc454-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span><span class="sxs-lookup"><span data-stu-id="dc454-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="dc454-224">O botão de Menu for pressionado.</span><span class="sxs-lookup"><span data-stu-id="dc454-224">The Menu button is pressed.</span></span>

<span data-ttu-id="dc454-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span><span class="sxs-lookup"><span data-stu-id="dc454-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="dc454-226">A alça é pressionado.</span><span class="sxs-lookup"><span data-stu-id="dc454-226">The Grip button is pressed.</span></span>

<span data-ttu-id="dc454-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="dc454-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="dc454-228">O TouchPad é pressionado.</span><span class="sxs-lookup"><span data-stu-id="dc454-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="dc454-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span><span class="sxs-lookup"><span data-stu-id="dc454-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="dc454-230">O botão de seleção é pressionado.</span><span class="sxs-lookup"><span data-stu-id="dc454-230">The Select button is pressed.</span></span>

<span data-ttu-id="dc454-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="dc454-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="dc454-232">O TouchPad é atingido.</span><span class="sxs-lookup"><span data-stu-id="dc454-232">The TouchPad is touched.</span></span>

<span data-ttu-id="dc454-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="dc454-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="dc454-234">O analógico é pressionado.</span><span class="sxs-lookup"><span data-stu-id="dc454-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="dc454-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span><span class="sxs-lookup"><span data-stu-id="dc454-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="dc454-236">O botão máximo válido.</span><span class="sxs-lookup"><span data-stu-id="dc454-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="dc454-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="dc454-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="dc454-238">O estado de calibragem dos olhos simulados</span><span class="sxs-lookup"><span data-stu-id="dc454-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="dc454-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="dc454-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="dc454-240">A calibragem olhos não está disponível.</span><span class="sxs-lookup"><span data-stu-id="dc454-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="dc454-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span><span class="sxs-lookup"><span data-stu-id="dc454-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="dc454-242">Têm sido calibrados os olhos.</span><span class="sxs-lookup"><span data-stu-id="dc454-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="dc454-243">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="dc454-243">This is the default value.</span></span>

<span data-ttu-id="dc454-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span><span class="sxs-lookup"><span data-stu-id="dc454-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="dc454-245">Estão sendo calibrados os olhos.</span><span class="sxs-lookup"><span data-stu-id="dc454-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="dc454-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="dc454-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="dc454-247">Os olhos precisam ser calibrado.</span><span class="sxs-lookup"><span data-stu-id="dc454-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="dc454-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="dc454-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="dc454-249">A precisão de acompanhamento de uma união da mão.</span><span class="sxs-lookup"><span data-stu-id="dc454-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="dc454-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="dc454-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="dc454-251">Junção não é controlada.</span><span class="sxs-lookup"><span data-stu-id="dc454-251">The joint is not tracked.</span></span>

<span data-ttu-id="dc454-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span><span class="sxs-lookup"><span data-stu-id="dc454-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="dc454-253">A posição do conjunta é inferida.</span><span class="sxs-lookup"><span data-stu-id="dc454-253">The joint position is inferred.</span></span>

<span data-ttu-id="dc454-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span><span class="sxs-lookup"><span data-stu-id="dc454-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="dc454-255">Junção totalmente é rastreada.</span><span class="sxs-lookup"><span data-stu-id="dc454-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="dc454-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="dc454-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="dc454-257">A precisão de acompanhamento de uma união da mão.</span><span class="sxs-lookup"><span data-stu-id="dc454-257">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

<span data-ttu-id="dc454-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span><span class="sxs-lookup"><span data-stu-id="dc454-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="dc454-259">Junções de dedo da mão são configuradas para refletir uma pose fechada.</span><span class="sxs-lookup"><span data-stu-id="dc454-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="dc454-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span><span class="sxs-lookup"><span data-stu-id="dc454-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="dc454-261">Junções de dedo da mão são configuradas para refletir uma pose aberto.</span><span class="sxs-lookup"><span data-stu-id="dc454-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="dc454-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span><span class="sxs-lookup"><span data-stu-id="dc454-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="dc454-263">Junções de dedo da mão são configuradas para refletir uma pose apontando.</span><span class="sxs-lookup"><span data-stu-id="dc454-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="dc454-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span><span class="sxs-lookup"><span data-stu-id="dc454-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="dc454-265">Junções de dedo da mão são configuradas para refletir uma pose apertar.</span><span class="sxs-lookup"><span data-stu-id="dc454-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="dc454-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span><span class="sxs-lookup"><span data-stu-id="dc454-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="dc454-267">O valor válido máximo para SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="dc454-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="dc454-268">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="dc454-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="dc454-269">Descreve o estado de uma reprodução.</span><span class="sxs-lookup"><span data-stu-id="dc454-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="dc454-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="dc454-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="dc454-271">A gravação está atualmente parado e pronto para ser reproduzido.</span><span class="sxs-lookup"><span data-stu-id="dc454-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="dc454-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="dc454-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="dc454-273">A gravação está sendo executado atualmente.</span><span class="sxs-lookup"><span data-stu-id="dc454-273">The recording is currently playing.</span></span>

<span data-ttu-id="dc454-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="dc454-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="dc454-275">A gravação está em pausa no momento.</span><span class="sxs-lookup"><span data-stu-id="dc454-275">The recording is currently paused.</span></span>

<span data-ttu-id="dc454-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="dc454-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="dc454-277">A gravação atingiu o fim.</span><span class="sxs-lookup"><span data-stu-id="dc454-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="dc454-278">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="dc454-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="dc454-279">Descreve um vetor de 3 componentes, que pode descrever um ponto ou um vetor no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="dc454-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="dc454-280">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="dc454-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="dc454-281">O componente X do vetor.</span><span class="sxs-lookup"><span data-stu-id="dc454-281">The X component of the vector.</span></span>

<span data-ttu-id="dc454-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="dc454-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="dc454-283">O componente Y do vetor.</span><span class="sxs-lookup"><span data-stu-id="dc454-283">The Y component of the vector.</span></span>

<span data-ttu-id="dc454-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="dc454-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="dc454-285">O componente Z do vetor.</span><span class="sxs-lookup"><span data-stu-id="dc454-285">The Z component of the vector.</span></span>

<span data-ttu-id="dc454-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="dc454-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="dc454-287">Construa um novo Vector3.</span><span class="sxs-lookup"><span data-stu-id="dc454-287">Construct a new Vector3.</span></span>

<span data-ttu-id="dc454-288">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-288">Parameters</span></span>
* <span data-ttu-id="dc454-289">x - o componente x do vetor.</span><span class="sxs-lookup"><span data-stu-id="dc454-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="dc454-290">y - o componente y do vetor.</span><span class="sxs-lookup"><span data-stu-id="dc454-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="dc454-291">z - o componente z do vetor.</span><span class="sxs-lookup"><span data-stu-id="dc454-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="dc454-292">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="dc454-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="dc454-293">Descreve uma rotação de 3 componentes.</span><span class="sxs-lookup"><span data-stu-id="dc454-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="dc454-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="dc454-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="dc454-295">O componente de tom de rotação, faz uma busca em torno do eixo X.</span><span class="sxs-lookup"><span data-stu-id="dc454-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="dc454-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="dc454-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="dc454-297">O componente do desvio da rotação em torno do eixo Y.</span><span class="sxs-lookup"><span data-stu-id="dc454-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="dc454-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="dc454-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="dc454-299">O componente de distribuição da rotação em torno do eixo Z.</span><span class="sxs-lookup"><span data-stu-id="dc454-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="dc454-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="dc454-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="dc454-301">Construa um novo Rotation3.</span><span class="sxs-lookup"><span data-stu-id="dc454-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="dc454-302">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-302">Parameters</span></span>
* <span data-ttu-id="dc454-303">Tom - o componente de tom da rotação.</span><span class="sxs-lookup"><span data-stu-id="dc454-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="dc454-304">yaw - o componente do desvio da rotação.</span><span class="sxs-lookup"><span data-stu-id="dc454-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="dc454-305">roll - o componente de distribuição da rotação.</span><span class="sxs-lookup"><span data-stu-id="dc454-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="dc454-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="dc454-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="dc454-307">Descreve a configuração de uma união em uma mão simulada.</span><span class="sxs-lookup"><span data-stu-id="dc454-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="dc454-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span><span class="sxs-lookup"><span data-stu-id="dc454-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="dc454-309">A posição da junção.</span><span class="sxs-lookup"><span data-stu-id="dc454-309">The position of the joint.</span></span>

<span data-ttu-id="dc454-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span><span class="sxs-lookup"><span data-stu-id="dc454-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="dc454-311">A rotação da junção.</span><span class="sxs-lookup"><span data-stu-id="dc454-311">The rotation of the joint.</span></span>

<span data-ttu-id="dc454-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="dc454-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="dc454-313">A precisão de acompanhamento da junção.</span><span class="sxs-lookup"><span data-stu-id="dc454-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="dc454-314">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="dc454-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="dc454-315">Descreve um frustum do modo de exibição, como normalmente usada por uma câmera.</span><span class="sxs-lookup"><span data-stu-id="dc454-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="dc454-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="dc454-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="dc454-317">A distância mínima que está contida no frustum.</span><span class="sxs-lookup"><span data-stu-id="dc454-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="dc454-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="dc454-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="dc454-319">A distância máxima que está contida no frustum.</span><span class="sxs-lookup"><span data-stu-id="dc454-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="dc454-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="dc454-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="dc454-321">O campo de exibição horizontal de frustum, em radianos (menor que o PI).</span><span class="sxs-lookup"><span data-stu-id="dc454-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="dc454-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="dc454-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="dc454-323">A taxa de campo de exibição horizontal para o campo de exibição vertical.</span><span class="sxs-lookup"><span data-stu-id="dc454-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="dc454-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="dc454-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="dc454-325">Raiz para gerar os pacotes usados para controlar um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="dc454-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="dc454-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="dc454-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="dc454-327">Recupere o objeto de dispositivo simulado que interpreta o ser humano simulado e o mundo simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="dc454-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="dc454-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="dc454-329">Recupere o objeto que controla o ser humano simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="dc454-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="dc454-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="dc454-331">Redefine a simulação para seu estado padrão.</span><span class="sxs-lookup"><span data-stu-id="dc454-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="dc454-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="dc454-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="dc454-333">Interface que descreve o dispositivo que interpreta o mundo simulado e o ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="dc454-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="dc454-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="dc454-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="dc454-335">Recupere a posição da cabeça do dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="dc454-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="dc454-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="dc454-337">Recupere o rastreador de mão do dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="dc454-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="dc454-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="dc454-339">Defina as propriedades do dispositivo simulado para corresponder ao tipo de dispositivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="dc454-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="dc454-340">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-340">Parameters</span></span>
* <span data-ttu-id="dc454-341">Digite - o novo tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="dc454-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="dc454-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="dc454-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="dc454-343">Interface que descreve a parte do dispositivo simulado que rastreia o cabeçalho do ser humano simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="dc454-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="dc454-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="dc454-345">Recupera e define o modo atual do controlador principal.</span><span class="sxs-lookup"><span data-stu-id="dc454-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="dc454-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="dc454-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="dc454-347">Interface que descreve a parte do dispositivo simulado que rastreia as mãos do ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="dc454-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="dc454-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="dc454-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="dc454-349">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="dc454-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="dc454-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="dc454-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="dc454-351">Recuperar e definir a posição do controlador mão simulado, em relação ao centro do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="dc454-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="dc454-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="dc454-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="dc454-353">Recuperar e definir o tom para baixo do controlador mão simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="dc454-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="dc454-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="dc454-355">Recuperar e definir se o frustum do controlador mão simulado é ignorado.</span><span class="sxs-lookup"><span data-stu-id="dc454-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="dc454-356">Quando ignoradas, ambas as mãos estão sempre visíveis.</span><span class="sxs-lookup"><span data-stu-id="dc454-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="dc454-357">Quando não ignoradas (padrão) mãos são visíveis apenas quando estes estiverem dentro a frustum do controlador disponível.</span><span class="sxs-lookup"><span data-stu-id="dc454-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="dc454-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="dc454-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="dc454-359">Recuperar e definir as propriedades de frustum usadas para determinar se as mãos são visíveis para o rastreador de mão simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="dc454-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="dc454-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="dc454-361">Interface de nível superior para controlar o ser humano simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="dc454-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="dc454-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="dc454-363">Recuperar e definir a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="dc454-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="dc454-364">A posição corresponde a um ponto no Centro de metros do humanos.</span><span class="sxs-lookup"><span data-stu-id="dc454-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="dc454-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="dc454-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="dc454-366">Recuperar e definir a direção de faces humanas simuladas no mundo.</span><span class="sxs-lookup"><span data-stu-id="dc454-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="dc454-367">0 radianos faces para baixo do eixo Z negativo.</span><span class="sxs-lookup"><span data-stu-id="dc454-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="dc454-368">Radianos positivos giram no sentido horário sobre o eixo Y.</span><span class="sxs-lookup"><span data-stu-id="dc454-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="dc454-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="dc454-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="dc454-370">Recuperar e definir a altura do ser humano simulado, em metros.</span><span class="sxs-lookup"><span data-stu-id="dc454-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="dc454-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="dc454-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="dc454-372">Recupere o lado esquerdo do ser humano simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="dc454-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="dc454-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="dc454-374">Recupere o direito do ser humano simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="dc454-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="dc454-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="dc454-376">Recupere o cabeçalho do ser humano simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="dc454-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="dc454-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="dc454-378">Mova o ser humano simulado em relação à posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="dc454-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="dc454-379">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-379">Parameters</span></span>
* <span data-ttu-id="dc454-380">conversão - a tradução para mover em relação à posição atual.</span><span class="sxs-lookup"><span data-stu-id="dc454-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="dc454-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="dc454-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="dc454-382">Girar o ser humano simulado em relação à sua direção atual, no sentido horário sobre o eixo Y</span><span class="sxs-lookup"><span data-stu-id="dc454-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="dc454-383">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-383">Parameters</span></span>
* <span data-ttu-id="dc454-384">radianos - a quantidade de rotação ao redor do eixo Y.</span><span class="sxs-lookup"><span data-stu-id="dc454-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="dc454-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="dc454-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="dc454-386">Propriedades adicionais estão disponíveis ao converter o ISimulatedHuman para ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="dc454-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="dc454-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span><span class="sxs-lookup"><span data-stu-id="dc454-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="dc454-388">Recupere o controlador de 6-DOF à esquerda.</span><span class="sxs-lookup"><span data-stu-id="dc454-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="dc454-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span><span class="sxs-lookup"><span data-stu-id="dc454-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="dc454-390">Recupere o controlador de 6-DOF à direita.</span><span class="sxs-lookup"><span data-stu-id="dc454-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="dc454-391">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="dc454-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="dc454-392">Interface que descreve uma mão do ser humano simulado</span><span class="sxs-lookup"><span data-stu-id="dc454-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="dc454-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="dc454-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="dc454-394">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="dc454-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="dc454-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="dc454-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="dc454-396">Recuperar e definir a posição da mão simulado em relação ao ser humano, em metros.</span><span class="sxs-lookup"><span data-stu-id="dc454-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="dc454-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="dc454-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="dc454-398">Recuperar e definir se a mão está ativada no momento.</span><span class="sxs-lookup"><span data-stu-id="dc454-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="dc454-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="dc454-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="dc454-400">Recupere se a mão está atualmente visível para o SimulatedDevice (ou seja, seja em uma posição para ser detectada pelo HandTracker).</span><span class="sxs-lookup"><span data-stu-id="dc454-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="dc454-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="dc454-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="dc454-402">Mova a mão, que é visível para o SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="dc454-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="dc454-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="dc454-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="dc454-404">Mova a posição da mão simulado em relação à posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="dc454-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="dc454-405">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-405">Parameters</span></span>
* <span data-ttu-id="dc454-406">tradução - o valor para converter a mão simulada.</span><span class="sxs-lookup"><span data-stu-id="dc454-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="dc454-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="dc454-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="dc454-408">Execute um gesto usando a mão simulada.</span><span class="sxs-lookup"><span data-stu-id="dc454-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="dc454-409">Ele só será detectado pelo sistema se a mão está habilitada.</span><span class="sxs-lookup"><span data-stu-id="dc454-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="dc454-410">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-410">Parameters</span></span>
* <span data-ttu-id="dc454-411">gesto - o gesto a executar.</span><span class="sxs-lookup"><span data-stu-id="dc454-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="dc454-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="dc454-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="dc454-413">Propriedades adicionais estão disponíveis ao converter um ISimulatedHand para ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="dc454-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="dc454-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span><span class="sxs-lookup"><span data-stu-id="dc454-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="dc454-415">Recuperar ou definir a rotação da mão simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="dc454-416">Radianos girar no sentido horário ao procurar ao longo do eixo positivo.</span><span class="sxs-lookup"><span data-stu-id="dc454-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="dc454-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="dc454-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="dc454-418">Propriedades adicionais estão disponíveis ao converter um ISimulatedHand para ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="dc454-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="dc454-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="dc454-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="dc454-420">Obter a configuração comum para o conjunto especificado.</span><span class="sxs-lookup"><span data-stu-id="dc454-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="dc454-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="dc454-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="dc454-422">Defina a configuração conjunta de junção especificada.</span><span class="sxs-lookup"><span data-stu-id="dc454-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="dc454-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="dc454-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="dc454-424">Defina a mão para uma pose conhecida com um sinalizador opcional para animar.</span><span class="sxs-lookup"><span data-stu-id="dc454-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="dc454-425">Observação: animando não resultará em junções imediatamente refletindo suas configurações conjuntas finais.</span><span class="sxs-lookup"><span data-stu-id="dc454-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="dc454-426">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="dc454-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="dc454-427">Interface que descreve o cabeçalho do ser humano simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="dc454-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="dc454-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="dc454-429">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="dc454-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="dc454-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="dc454-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="dc454-431">Recupere a rotação da cabeça de simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="dc454-432">Radianos girar no sentido horário ao procurar ao longo do eixo positivo.</span><span class="sxs-lookup"><span data-stu-id="dc454-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="dc454-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="dc454-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="dc454-434">Recupere o diâmetro da cabeça simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="dc454-435">Esse valor é usado para determinar o centro do head (ponto de rotação).</span><span class="sxs-lookup"><span data-stu-id="dc454-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="dc454-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="dc454-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="dc454-437">Gire o head simulado em relação à sua rotação atual.</span><span class="sxs-lookup"><span data-stu-id="dc454-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="dc454-438">Radianos girar no sentido horário ao procurar ao longo do eixo positivo.</span><span class="sxs-lookup"><span data-stu-id="dc454-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="dc454-439">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-439">Parameters</span></span>
* <span data-ttu-id="dc454-440">rotação - a quantidade para girar.</span><span class="sxs-lookup"><span data-stu-id="dc454-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="dc454-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="dc454-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="dc454-442">Propriedades adicionais estão disponíveis ao converter um ISimulatedHead para ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="dc454-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="dc454-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span><span class="sxs-lookup"><span data-stu-id="dc454-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="dc454-444">Recupere os olhos do ser humano simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="dc454-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="dc454-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="dc454-446">Interface que descrevem um controlador de 6 DOF associado com o ser humano simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

<span data-ttu-id="dc454-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="dc454-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="dc454-448">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="dc454-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="dc454-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span><span class="sxs-lookup"><span data-stu-id="dc454-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="dc454-450">Recuperar ou definir o estado atual do controlador.</span><span class="sxs-lookup"><span data-stu-id="dc454-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="dc454-451">O status do controlador deve ser definido como um valor diferente de desativado antes de qualquer chamada para mover, girar ou pressione botões terá êxito.</span><span class="sxs-lookup"><span data-stu-id="dc454-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="dc454-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span><span class="sxs-lookup"><span data-stu-id="dc454-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="dc454-453">Recuperar ou definir a posição do controlador simulado em relação ao ser humano, em metros.</span><span class="sxs-lookup"><span data-stu-id="dc454-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="dc454-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span><span class="sxs-lookup"><span data-stu-id="dc454-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="dc454-455">Recuperar ou definir a orientação do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="dc454-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="dc454-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="dc454-457">Mova a posição do controlador simulado em relação à posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="dc454-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="dc454-458">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-458">Parameters</span></span>
* <span data-ttu-id="dc454-459">tradução - o valor para converter o controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="dc454-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="dc454-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="dc454-461">Pressione um botão no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="dc454-462">Ele só será detectado pelo sistema se o controlador está habilitado.</span><span class="sxs-lookup"><span data-stu-id="dc454-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="dc454-463">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-463">Parameters</span></span>
* <span data-ttu-id="dc454-464">botão - à imprensa.</span><span class="sxs-lookup"><span data-stu-id="dc454-464">button - The button to press.</span></span>

<span data-ttu-id="dc454-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="dc454-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="dc454-466">Libera um botão no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="dc454-467">Ele só será detectado pelo sistema se o controlador está habilitado.</span><span class="sxs-lookup"><span data-stu-id="dc454-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="dc454-468">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-468">Parameters</span></span>
* <span data-ttu-id="dc454-469">botão - o para liberar.</span><span class="sxs-lookup"><span data-stu-id="dc454-469">button - The button to release.</span></span>

<span data-ttu-id="dc454-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="dc454-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="dc454-471">Obtenha a posição de um dedo simulado em touchpad do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="dc454-472">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-472">Parameters</span></span>
* <span data-ttu-id="dc454-473">x - a posição horizontal do dedo.</span><span class="sxs-lookup"><span data-stu-id="dc454-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="dc454-474">y - a posição vertical do dedo.</span><span class="sxs-lookup"><span data-stu-id="dc454-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="dc454-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="dc454-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="dc454-476">Defina a posição de um dedo simulado em touchpad do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="dc454-477">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-477">Parameters</span></span>
* <span data-ttu-id="dc454-478">x - a posição horizontal do dedo.</span><span class="sxs-lookup"><span data-stu-id="dc454-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="dc454-479">y - a posição vertical do dedo.</span><span class="sxs-lookup"><span data-stu-id="dc454-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="dc454-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="dc454-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="dc454-481">Propriedades e métodos adicionais estão disponíveis ao converter um ISimulatedSixDofController para ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="dc454-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="dc454-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="dc454-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="dc454-483">Obtenha a posição do analógico simulado no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="dc454-484">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-484">Parameters</span></span>
* <span data-ttu-id="dc454-485">x - a posição horizontal do analógico.</span><span class="sxs-lookup"><span data-stu-id="dc454-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="dc454-486">y - a posição vertical do analógico.</span><span class="sxs-lookup"><span data-stu-id="dc454-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="dc454-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="dc454-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="dc454-488">Defina a posição do analógico simulado no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="dc454-489">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-489">Parameters</span></span>
* <span data-ttu-id="dc454-490">x - a posição horizontal do analógico.</span><span class="sxs-lookup"><span data-stu-id="dc454-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="dc454-491">y - a posição vertical do analógico.</span><span class="sxs-lookup"><span data-stu-id="dc454-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="dc454-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="dc454-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="dc454-493">Recuperar ou definir o nível de bateria do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="dc454-494">O valor deve ser maior que 0,0 e menor ou igual a 100.0.</span><span class="sxs-lookup"><span data-stu-id="dc454-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="dc454-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="dc454-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="dc454-496">Interface que descreve os olhos do ser humano simulado.</span><span class="sxs-lookup"><span data-stu-id="dc454-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="dc454-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span><span class="sxs-lookup"><span data-stu-id="dc454-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="dc454-498">Recupere a rotação dos olhos simulados.</span><span class="sxs-lookup"><span data-stu-id="dc454-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="dc454-499">Radianos girar no sentido horário ao procurar ao longo do eixo positivo.</span><span class="sxs-lookup"><span data-stu-id="dc454-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="dc454-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="dc454-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="dc454-501">Gire os olhos simulados em relação à sua rotação atual.</span><span class="sxs-lookup"><span data-stu-id="dc454-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="dc454-502">Radianos girar no sentido horário ao procurar ao longo do eixo positivo.</span><span class="sxs-lookup"><span data-stu-id="dc454-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="dc454-503">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-503">Parameters</span></span>
* <span data-ttu-id="dc454-504">rotação - a quantidade para girar.</span><span class="sxs-lookup"><span data-stu-id="dc454-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="dc454-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="dc454-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="dc454-506">Recupera ou define o estado de calibragem dos olhos simulados.</span><span class="sxs-lookup"><span data-stu-id="dc454-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="dc454-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="dc454-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="dc454-508">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="dc454-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="dc454-509">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="dc454-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="dc454-510">Carregar a interface para interagir com uma única gravação para reprodução.</span><span class="sxs-lookup"><span data-stu-id="dc454-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="dc454-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="dc454-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="dc454-512">Recupera a lista de tipos de dados na gravação.</span><span class="sxs-lookup"><span data-stu-id="dc454-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="dc454-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="dc454-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="dc454-514">Recupera o estado atual da gravação.</span><span class="sxs-lookup"><span data-stu-id="dc454-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="dc454-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="dc454-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="dc454-516">Inicie a reprodução.</span><span class="sxs-lookup"><span data-stu-id="dc454-516">Start the playback.</span></span> <span data-ttu-id="dc454-517">Se a gravação for pausada, a reprodução será retomada do local em pausa; Se interrompida, a reprodução será iniciada no início.</span><span class="sxs-lookup"><span data-stu-id="dc454-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="dc454-518">Se já em execução, essa chamada é ignorada.</span><span class="sxs-lookup"><span data-stu-id="dc454-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="dc454-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="dc454-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="dc454-520">Pausa a reprodução em seu local atual.</span><span class="sxs-lookup"><span data-stu-id="dc454-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="dc454-521">Se a gravação for interrompida, a chamada será ignorada.</span><span class="sxs-lookup"><span data-stu-id="dc454-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="dc454-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="dc454-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="dc454-523">Procura a gravação de tempo especificado (em intervalos de 100 nanossegundos desde o início) e faz uma pausa nesse local.</span><span class="sxs-lookup"><span data-stu-id="dc454-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="dc454-524">Se o tempo está além do fim da gravação, ele está em pausa no último quadro.</span><span class="sxs-lookup"><span data-stu-id="dc454-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="dc454-525">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-525">Parameters</span></span>
* <span data-ttu-id="dc454-526">tiques - o tempo para o qual buscar.</span><span class="sxs-lookup"><span data-stu-id="dc454-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="dc454-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="dc454-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="dc454-528">Interrompe a reprodução e redefine a posição para o início.</span><span class="sxs-lookup"><span data-stu-id="dc454-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="dc454-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="dc454-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="dc454-530">A interface para receber alterações de estado durante a reprodução.</span><span class="sxs-lookup"><span data-stu-id="dc454-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="dc454-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="dc454-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="dc454-532">Chamado quando o estado de reprodução de um ISimulationRecording foi alterado.</span><span class="sxs-lookup"><span data-stu-id="dc454-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="dc454-533">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-533">Parameters</span></span>
* <span data-ttu-id="dc454-534">newState - o novo estado da gravação.</span><span class="sxs-lookup"><span data-stu-id="dc454-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="dc454-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="dc454-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="dc454-536">Objeto raiz para a criação de objetos de simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="dc454-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="dc454-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="dc454-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="dc454-538">Crie no objeto para gerar pacotes simulados e entregá-los para o coletor fornecido.</span><span class="sxs-lookup"><span data-stu-id="dc454-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="dc454-539">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-539">Parameters</span></span>
* <span data-ttu-id="dc454-540">coletor - coletor que receberá os pacotes gerados.</span><span class="sxs-lookup"><span data-stu-id="dc454-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="dc454-541">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="dc454-541">Return value</span></span>

<span data-ttu-id="dc454-542">O Gerenciador de criado.</span><span class="sxs-lookup"><span data-stu-id="dc454-542">The created Manager.</span></span>

<span data-ttu-id="dc454-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="dc454-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="dc454-544">Crie um coletor que armazena os pacotes recebidos tudo em um arquivo no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="dc454-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="dc454-545">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-545">Parameters</span></span>
* <span data-ttu-id="dc454-546">caminho - o caminho do arquivo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="dc454-546">path - The path of the file to create.</span></span>

<span data-ttu-id="dc454-547">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="dc454-547">Return value</span></span>

<span data-ttu-id="dc454-548">O coletor criado.</span><span class="sxs-lookup"><span data-stu-id="dc454-548">The created sink.</span></span>

<span data-ttu-id="dc454-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="dc454-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="dc454-550">Carregar uma gravação do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="dc454-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="dc454-551">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-551">Parameters</span></span>
* <span data-ttu-id="dc454-552">caminho - o caminho do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="dc454-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="dc454-553">fábrica - um alocador usado pela gravação para a criação de um ISimulationStreamSink quando necessário.</span><span class="sxs-lookup"><span data-stu-id="dc454-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="dc454-554">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="dc454-554">Return value</span></span>

<span data-ttu-id="dc454-555">A gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="dc454-555">The loaded recording.</span></span>

<span data-ttu-id="dc454-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="dc454-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="dc454-557">Carregar uma gravação do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="dc454-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="dc454-558">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-558">Parameters</span></span>
* <span data-ttu-id="dc454-559">caminho - o caminho do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="dc454-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="dc454-560">fábrica - um alocador usado pela gravação para a criação de um ISimulationStreamSink quando necessário.</span><span class="sxs-lookup"><span data-stu-id="dc454-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="dc454-561">retorno de chamada - um retorno de chamada que recebe atualizações regrading status da gravação.</span><span class="sxs-lookup"><span data-stu-id="dc454-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="dc454-562">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="dc454-562">Return value</span></span>

<span data-ttu-id="dc454-563">A gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="dc454-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="dc454-564">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="dc454-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="dc454-565">Descreve os diferentes tipos de fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="dc454-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="dc454-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="dc454-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="dc454-567">Um valor de sentinela usado para não indicar nenhum tipo de fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="dc454-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="dc454-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="dc454-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="dc454-569">Stream de dados em relação à posição e orientação do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="dc454-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="dc454-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="dc454-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="dc454-571">Stream de dados em relação à posição e gestos de mãos.</span><span class="sxs-lookup"><span data-stu-id="dc454-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="dc454-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="dc454-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="dc454-573">Stream de dados relativos ao mapeamento espacial do ambiente.</span><span class="sxs-lookup"><span data-stu-id="dc454-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="dc454-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="dc454-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="dc454-575">Stream de dados em relação à calibragem do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="dc454-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="dc454-576">Pacotes de calibragem somente são aceitas por um sistema no modo remoto.</span><span class="sxs-lookup"><span data-stu-id="dc454-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="dc454-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="dc454-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="dc454-578">Stream de dados sobre o ambiente do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="dc454-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="dc454-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="dc454-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="dc454-580">Um valor de sentinela usado para indicar todos os tipos de dados gravados.</span><span class="sxs-lookup"><span data-stu-id="dc454-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="dc454-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="dc454-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="dc454-582">Um objeto que recebe os pacotes de dados de um fluxo de simulação.</span><span class="sxs-lookup"><span data-stu-id="dc454-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="dc454-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span><span class="sxs-lookup"><span data-stu-id="dc454-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="dc454-584">Recebe um único pacote, o que é internamente com tipo e com controle de versão.</span><span class="sxs-lookup"><span data-stu-id="dc454-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="dc454-585">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc454-585">Parameters</span></span>
* <span data-ttu-id="dc454-586">comprimento - o tamanho do pacote.</span><span class="sxs-lookup"><span data-stu-id="dc454-586">length - The length of the packet.</span></span>
* <span data-ttu-id="dc454-587">pacote - os dados do pacote.</span><span class="sxs-lookup"><span data-stu-id="dc454-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="dc454-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="dc454-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="dc454-589">Um objeto que cria ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="dc454-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="dc454-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="dc454-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="dc454-591">Cria uma única instância de ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="dc454-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="dc454-592">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="dc454-592">Return value</span></span>

<span data-ttu-id="dc454-593">O coletor criado.</span><span class="sxs-lookup"><span data-stu-id="dc454-593">The created sink.</span></span>
