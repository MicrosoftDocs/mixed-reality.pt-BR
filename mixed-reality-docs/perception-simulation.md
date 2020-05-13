---
title: Simulação de percepção
description: Um guia para usar a biblioteca de simulação de percepção para automatizar a entrada simulada para aplicativos de imersão
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, simulação, teste
ms.openlocfilehash: 701fd39490d87b70df9bd68cc99da6482d41b676
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228021"
---
# <a name="perception-simulation"></a><span data-ttu-id="e838a-104">Simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="e838a-104">Perception simulation</span></span>

<span data-ttu-id="e838a-105">Deseja criar um teste automatizado para seu aplicativo?</span><span class="sxs-lookup"><span data-stu-id="e838a-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="e838a-106">Você deseja que seus testes vão além dos testes de unidade de nível de componente e realmente exercitam seu aplicativo de ponta a ponta?</span><span class="sxs-lookup"><span data-stu-id="e838a-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="e838a-107">A simulação de percepção é o que você está procurando.</span><span class="sxs-lookup"><span data-stu-id="e838a-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="e838a-108">A biblioteca de simulação de percepção envia dados de entrada humanos e mundiais para seu aplicativo para que você possa automatizar seus testes.</span><span class="sxs-lookup"><span data-stu-id="e838a-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="e838a-109">Por exemplo, você pode simular a entrada de uma aparência humana para uma posição específica e repetível e, em seguida, executar um gesto ou usar um controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="e838a-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="e838a-110">A simulação de percepção pode enviar uma entrada simulada como esta para um HoloLens físico, o emulador do HoloLens (1º gen), o emulador do HoloLens 2 ou um PC com o portal de realidade misturada instalado.</span><span class="sxs-lookup"><span data-stu-id="e838a-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="e838a-111">A simulação de percepção ignora os sensores ao vivo em um dispositivo de realidade misturada e envia a entrada simulada para aplicativos em execução no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e838a-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="e838a-112">Os aplicativos recebem esses eventos de entrada por meio das mesmas APIs que sempre usam e não conseguem dizer a diferença entre a execução com sensores reais versus a execução com a simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="e838a-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="e838a-113">A simulação de percepção é a mesma tecnologia usada pelos emuladores do HoloLens para enviar a entrada simulada para a máquina virtual do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e838a-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="e838a-114">Para começar a usar a simulação em seu código, comece criando um objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="e838a-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="e838a-115">A partir desse objeto, você pode emitir comandos para controlar as propriedades de um "humano" simulado, incluindo posição de cabeçalho, posição mão e gestos, e você pode habilitar e manipular controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="e838a-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="e838a-116">Configurando um projeto do Visual Studio para simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="e838a-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="e838a-117">[Instale o emulador do HoloLens](install-the-tools.md) no seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="e838a-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="e838a-118">O emulador inclui as bibliotecas que serão usadas para a simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="e838a-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="e838a-119">Crie um novo projeto de desktop do Visual Studio C# (um projeto de console funciona muito bem para começar).</span><span class="sxs-lookup"><span data-stu-id="e838a-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="e838a-120">Adicione os seguintes binários ao seu projeto como referências (projeto->referência ao suplemento de >...). Você pode encontrá-los em% ProgramFiles (x86)% \ Microsoft XDE \\ (versão), como **% ProgramFiles (x86)% \ Microsoft XDE \\ 10.0.18362.0** para o emulador do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e838a-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="e838a-121">(Observação: embora os binários façam parte do emulador do HoloLens 2, eles também funcionam para a realidade mista do Windows na área de trabalho.) um.</span><span class="sxs-lookup"><span data-stu-id="e838a-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="e838a-122">PerceptionSimulationManager. Interop. dll-invólucro C# gerenciado para simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="e838a-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="e838a-123">b.</span><span class="sxs-lookup"><span data-stu-id="e838a-123">b.</span></span> <span data-ttu-id="e838a-124">PerceptionSimulationRest. dll-Library para configurar um canal de comunicação de soquete da Web para o HoloLens ou o emulador.</span><span class="sxs-lookup"><span data-stu-id="e838a-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="e838a-125">c.</span><span class="sxs-lookup"><span data-stu-id="e838a-125">c.</span></span> <span data-ttu-id="e838a-126">SimulationStream. Interop. dll-tipos compartilhados para simulação.</span><span class="sxs-lookup"><span data-stu-id="e838a-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="e838a-127">Adicione o binário de implementação PerceptionSimulationManager. dll ao seu projeto a.</span><span class="sxs-lookup"><span data-stu-id="e838a-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="e838a-128">Primeiro, adicione-o como um binário ao projeto (projeto->adicionar >item existente...). Salve-o como um link para que ele não o copie para a pasta de origem do projeto.</span><span class="sxs-lookup"><span data-stu-id="e838a-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="e838a-129">![Adicione PerceptionSimulationManager. dll ao projeto como um link ](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="e838a-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="e838a-130">Em seguida, certifique-se de que ele seja copiado para a pasta de saída na compilação.</span><span class="sxs-lookup"><span data-stu-id="e838a-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="e838a-131">Isso está na folha de propriedades do binário.</span><span class="sxs-lookup"><span data-stu-id="e838a-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="e838a-132">![Marque PerceptionSimulationManager. dll para copiar para o diretório de saída](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="e838a-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="e838a-133">Defina sua plataforma de solução ativa como x64.</span><span class="sxs-lookup"><span data-stu-id="e838a-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="e838a-134">(Use o Configuration Manager para criar uma entrada de plataforma para x64 se ainda não existir uma.)</span><span class="sxs-lookup"><span data-stu-id="e838a-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="e838a-135">Criando um objeto do Gerenciador de IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="e838a-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="e838a-136">Para controlar a simulação, você emitirá atualizações para objetos recuperados de um objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="e838a-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="e838a-137">A primeira etapa é obter esse objeto e conectá-lo ao seu dispositivo de destino ou emulador.</span><span class="sxs-lookup"><span data-stu-id="e838a-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="e838a-138">Você pode obter o endereço IP do emulador clicando no botão portal do dispositivo na barra de [ferramentas](using-the-hololens-emulator.md)</span><span class="sxs-lookup"><span data-stu-id="e838a-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="e838a-139">![Abrir o ícone do portal do dispositivo ](images/emulator-deviceportal.png) **abra o portal do dispositivo**: Abra o portal do dispositivo do Windows para o sistema operacional do HoloLens no emulador.</span><span class="sxs-lookup"><span data-stu-id="e838a-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="e838a-140">Para a realidade mista do Windows, isso pode ser recuperado no aplicativo configurações em "atualizar & segurança" e, em seguida, "para desenvolvedores" na seção "conectar usando:" em "habilitar o portal do dispositivo".</span><span class="sxs-lookup"><span data-stu-id="e838a-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="e838a-141">Lembre-se de anotar o endereço IP e a porta.</span><span class="sxs-lookup"><span data-stu-id="e838a-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="e838a-142">Primeiro, você chamará RestSimulationStreamSink. Create para obter um objeto RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="e838a-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="e838a-143">Esse é o dispositivo ou emulador de destino que você controlará em uma conexão http.</span><span class="sxs-lookup"><span data-stu-id="e838a-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="e838a-144">Seus comandos serão passados e manipulados pelo portal do [dispositivo Windows](using-the-windows-device-portal.md) em execução no dispositivo ou emulador.</span><span class="sxs-lookup"><span data-stu-id="e838a-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="e838a-145">Os quatro parâmetros necessários para criar um objeto são:</span><span class="sxs-lookup"><span data-stu-id="e838a-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="e838a-146">URI Uri-endereço IP do dispositivo de destino (por exemplo, " https://123.123.123.123 " ou " https://123.123.123.123:50080 ")</span><span class="sxs-lookup"><span data-stu-id="e838a-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="e838a-147">System .net. NetworkCredential credenciais-nome de usuário/senha para se conectar ao [portal de dispositivo do Windows](using-the-windows-device-portal.md) no dispositivo ou emulador de destino.</span><span class="sxs-lookup"><span data-stu-id="e838a-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="e838a-148">Se você estiver se conectando ao emulador por meio de seu endereço local (por exemplo,*168...* \*) no mesmo PC, todas as credenciais serão aceitas.</span><span class="sxs-lookup"><span data-stu-id="e838a-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="e838a-149">bool normal-true para prioridade normal, false para baixa prioridade.</span><span class="sxs-lookup"><span data-stu-id="e838a-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="e838a-150">Em geral, você desejará definir isso como *verdadeiro* para cenários de teste, o que permite que seu teste assuma o controle.</span><span class="sxs-lookup"><span data-stu-id="e838a-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="e838a-151">O emulador e a simulação de realidade mista do Windows usam conexões de baixa prioridade.</span><span class="sxs-lookup"><span data-stu-id="e838a-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="e838a-152">Se o teste também usar uma conexão de baixa prioridade, a conexão estabelecida mais recentemente estará no controle.</span><span class="sxs-lookup"><span data-stu-id="e838a-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="e838a-153">System. Threading. CancellationToken token-token para cancelar a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="e838a-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="e838a-154">Em segundo lugar, você criará o IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="e838a-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="e838a-155">Esse é o objeto que você usa para controlar a simulação.</span><span class="sxs-lookup"><span data-stu-id="e838a-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="e838a-156">Observe que isso também deve ser feito em um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="e838a-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="e838a-157">Controlar o humano simulado</span><span class="sxs-lookup"><span data-stu-id="e838a-157">Control the simulated Human</span></span>

<span data-ttu-id="e838a-158">Um IPerceptionSimulationManager tem uma propriedade humana que retorna um objeto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="e838a-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="e838a-159">Para controlar o humano simulado, execute operações nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="e838a-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="e838a-160">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e838a-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="e838a-161">Aplicativo de console C# de exemplo básico</span><span class="sxs-lookup"><span data-stu-id="e838a-161">Basic Sample C# console application</span></span>

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
                        new Uri("https://169.254.227.115"),
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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="e838a-162">Aplicativo de console C# de exemplo estendido</span><span class="sxs-lookup"><span data-stu-id="e838a-162">Extended Sample C# console application</span></span>

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
                        new Uri("https://169.254.227.115"),
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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="e838a-163">Observação em controladores 6-DOF</span><span class="sxs-lookup"><span data-stu-id="e838a-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="e838a-164">Antes de chamar qualquer propriedade em métodos em um controlador de 6 DOF simulado, você deve ativar o controlador.</span><span class="sxs-lookup"><span data-stu-id="e838a-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="e838a-165">Não fazer isso resultará em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="e838a-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="e838a-166">A partir da atualização do Windows 10 de maio de 2019, os controladores 6 DOF simulados podem ser instalados e ativados definindo a propriedade status no objeto ISimulatedSixDofController como SimulatedSixDofControllerStatus. Active.</span><span class="sxs-lookup"><span data-stu-id="e838a-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="e838a-167">Na atualização do Windows 10 de outubro de 2018 e anterior, você deve instalar separadamente um controlador de 6 DOF simulado primeiro chamando a ferramenta PerceptionSimulationDevice localizada na pasta \Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="e838a-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="e838a-168">O uso dessa ferramenta é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e838a-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="e838a-169">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="e838a-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="e838a-170">As ações com suporte são:</span><span class="sxs-lookup"><span data-stu-id="e838a-170">Supported actions are:</span></span>
* <span data-ttu-id="e838a-171">i = instalar</span><span class="sxs-lookup"><span data-stu-id="e838a-171">i = install</span></span>
* <span data-ttu-id="e838a-172">q = consulta</span><span class="sxs-lookup"><span data-stu-id="e838a-172">q = query</span></span>
* <span data-ttu-id="e838a-173">r = remover</span><span class="sxs-lookup"><span data-stu-id="e838a-173">r = remove</span></span>

<span data-ttu-id="e838a-174">As instâncias com suporte são:</span><span class="sxs-lookup"><span data-stu-id="e838a-174">Supported instances are:</span></span>
* <span data-ttu-id="e838a-175">1 = o controlador de 6 DOF à esquerda</span><span class="sxs-lookup"><span data-stu-id="e838a-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="e838a-176">2 = o controlador de 6 DOF à direita</span><span class="sxs-lookup"><span data-stu-id="e838a-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="e838a-177">O código de saída do processo indicará êxito (um valor de retorno zero) ou falha (um valor de retorno diferente de zero).</span><span class="sxs-lookup"><span data-stu-id="e838a-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="e838a-178">Ao usar a ação ' q ' para consultar se um controlador está ou não instalado, o valor de retorno será zero (0) se o controlador ainda não estiver instalado ou um (1) se o controlador estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="e838a-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="e838a-179">Ao remover um controlador na atualização do Windows 10 de outubro de 2018 ou anterior, defina seu status como off por meio da API primeiro e, em seguida, chame a ferramenta PerceptionSimulationDevice.</span><span class="sxs-lookup"><span data-stu-id="e838a-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="e838a-180">Observe que essa ferramenta deve ser executada como administrador.</span><span class="sxs-lookup"><span data-stu-id="e838a-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="e838a-181">Referência de API</span><span class="sxs-lookup"><span data-stu-id="e838a-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="e838a-182">Microsoft. PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="e838a-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="e838a-183">Descreve um tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="e838a-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="e838a-184">**Microsoft. PerceptionSimulation. SimulatedDeviceType. Reference**</span><span class="sxs-lookup"><span data-stu-id="e838a-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="e838a-185">Um dispositivo de referência fictícia, o padrão para PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="e838a-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="e838a-186">Microsoft. PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="e838a-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="e838a-187">Descreve um modo de controlador de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="e838a-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="e838a-188">**Microsoft. PerceptionSimulation. HeadTrackerMode. Default**</span><span class="sxs-lookup"><span data-stu-id="e838a-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="e838a-189">Rastreamento de cabeçalho padrão.</span><span class="sxs-lookup"><span data-stu-id="e838a-189">Default Head Tracking.</span></span> <span data-ttu-id="e838a-190">Isso significa que o sistema pode selecionar o melhor modo de controle de cabeçalho com base nas condições de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e838a-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="e838a-191">**Microsoft. PerceptionSimulation. HeadTrackerMode. Orientation**</span><span class="sxs-lookup"><span data-stu-id="e838a-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="e838a-192">Controle de cabeçalho somente orientação.</span><span class="sxs-lookup"><span data-stu-id="e838a-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="e838a-193">Isso significa que a posição controlada pode não ser confiável, e algumas funcionalidades dependentes da posição de cabeçalho podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="e838a-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="e838a-194">**Microsoft. PerceptionSimulation. HeadTrackerMode. Position**</span><span class="sxs-lookup"><span data-stu-id="e838a-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="e838a-195">Acompanhamento da cabeça posicional.</span><span class="sxs-lookup"><span data-stu-id="e838a-195">Positional Head Tracking.</span></span> <span data-ttu-id="e838a-196">Isso significa que a posição e a orientação da cabeça controlada são confiáveis</span><span class="sxs-lookup"><span data-stu-id="e838a-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="e838a-197">Microsoft. PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="e838a-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="e838a-198">Descreve um gesto simulado</span><span class="sxs-lookup"><span data-stu-id="e838a-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="e838a-199">**Microsoft. PerceptionSimulation. SimulatedGesture. None**</span><span class="sxs-lookup"><span data-stu-id="e838a-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="e838a-200">Um valor de sentinela usado para indicar que não há gestos.</span><span class="sxs-lookup"><span data-stu-id="e838a-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="e838a-201">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="e838a-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="e838a-202">Um gesto de dedo pressionado.</span><span class="sxs-lookup"><span data-stu-id="e838a-202">A finger pressed gesture.</span></span>

<span data-ttu-id="e838a-203">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="e838a-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="e838a-204">Um gesto de liberação de dedo.</span><span class="sxs-lookup"><span data-stu-id="e838a-204">A finger released gesture.</span></span>

<span data-ttu-id="e838a-205">**Microsoft. PerceptionSimulation. SimulatedGesture. Home**</span><span class="sxs-lookup"><span data-stu-id="e838a-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="e838a-206">O gesto de residência/sistema.</span><span class="sxs-lookup"><span data-stu-id="e838a-206">The home/system gesture.</span></span>

<span data-ttu-id="e838a-207">**Microsoft. PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="e838a-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="e838a-208">O gesto máximo válido.</span><span class="sxs-lookup"><span data-stu-id="e838a-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="e838a-209">Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="e838a-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="e838a-210">Os Estados possíveis de um controlador de 6 DOF simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="e838a-211">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. off**</span><span class="sxs-lookup"><span data-stu-id="e838a-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="e838a-212">O controlador de 6 DOF está desligado.</span><span class="sxs-lookup"><span data-stu-id="e838a-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="e838a-213">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. active**</span><span class="sxs-lookup"><span data-stu-id="e838a-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="e838a-214">O controlador de 6 DOF é ativado e acompanhado.</span><span class="sxs-lookup"><span data-stu-id="e838a-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="e838a-215">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="e838a-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="e838a-216">O controlador de 6 DOF está ativado, mas não pode ser acompanhado.</span><span class="sxs-lookup"><span data-stu-id="e838a-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="e838a-217">Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="e838a-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="e838a-218">Os botões com suporte em um controlador de 6 DOF simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="e838a-219">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. None**</span><span class="sxs-lookup"><span data-stu-id="e838a-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="e838a-220">Um valor de sentinela usado para indicar nenhum botão.</span><span class="sxs-lookup"><span data-stu-id="e838a-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="e838a-221">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Home**</span><span class="sxs-lookup"><span data-stu-id="e838a-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="e838a-222">O botão página inicial é pressionado.</span><span class="sxs-lookup"><span data-stu-id="e838a-222">The Home button is pressed.</span></span>

<span data-ttu-id="e838a-223">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. menu**</span><span class="sxs-lookup"><span data-stu-id="e838a-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="e838a-224">O botão de menu é pressionado.</span><span class="sxs-lookup"><span data-stu-id="e838a-224">The Menu button is pressed.</span></span>

<span data-ttu-id="e838a-225">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Segure**</span><span class="sxs-lookup"><span data-stu-id="e838a-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="e838a-226">O botão de alça é pressionado.</span><span class="sxs-lookup"><span data-stu-id="e838a-226">The Grip button is pressed.</span></span>

<span data-ttu-id="e838a-227">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="e838a-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="e838a-228">O TouchPad é pressionado.</span><span class="sxs-lookup"><span data-stu-id="e838a-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="e838a-229">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="e838a-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="e838a-230">O botão Selecionar é pressionado.</span><span class="sxs-lookup"><span data-stu-id="e838a-230">The Select button is pressed.</span></span>

<span data-ttu-id="e838a-231">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="e838a-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="e838a-232">O TouchPad é tocado.</span><span class="sxs-lookup"><span data-stu-id="e838a-232">The TouchPad is touched.</span></span>

<span data-ttu-id="e838a-233">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="e838a-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="e838a-234">O Thumbstick é pressionado.</span><span class="sxs-lookup"><span data-stu-id="e838a-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="e838a-235">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="e838a-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="e838a-236">O botão máximo válido.</span><span class="sxs-lookup"><span data-stu-id="e838a-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="e838a-237">Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="e838a-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="e838a-238">O estado de calibragem dos olhos simulados</span><span class="sxs-lookup"><span data-stu-id="e838a-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="e838a-239">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. indisponível**</span><span class="sxs-lookup"><span data-stu-id="e838a-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="e838a-240">A calibragem de olhos não está disponível.</span><span class="sxs-lookup"><span data-stu-id="e838a-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="e838a-241">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Ready**</span><span class="sxs-lookup"><span data-stu-id="e838a-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="e838a-242">Os olhos foram calibrados.</span><span class="sxs-lookup"><span data-stu-id="e838a-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="e838a-243">Esse é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="e838a-243">This is the default value.</span></span>

<span data-ttu-id="e838a-244">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Configurando**</span><span class="sxs-lookup"><span data-stu-id="e838a-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="e838a-245">Os olhos estão sendo calibrados.</span><span class="sxs-lookup"><span data-stu-id="e838a-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="e838a-246">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="e838a-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="e838a-247">Os olhos precisam ser calibrados.</span><span class="sxs-lookup"><span data-stu-id="e838a-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="e838a-248">Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="e838a-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="e838a-249">A precisão de rastreamento de um conjunto de mãos.</span><span class="sxs-lookup"><span data-stu-id="e838a-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="e838a-250">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. indisponível**</span><span class="sxs-lookup"><span data-stu-id="e838a-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="e838a-251">A junção não é rastreada.</span><span class="sxs-lookup"><span data-stu-id="e838a-251">The joint is not tracked.</span></span>

<span data-ttu-id="e838a-252">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. aproximado**</span><span class="sxs-lookup"><span data-stu-id="e838a-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="e838a-253">A posição conjunta é inferida.</span><span class="sxs-lookup"><span data-stu-id="e838a-253">The joint position is inferred.</span></span>

<span data-ttu-id="e838a-254">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. Visible**</span><span class="sxs-lookup"><span data-stu-id="e838a-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="e838a-255">A junção é totalmente controlada.</span><span class="sxs-lookup"><span data-stu-id="e838a-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="e838a-256">Microsoft. PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="e838a-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="e838a-257">A precisão de rastreamento de um conjunto de mãos.</span><span class="sxs-lookup"><span data-stu-id="e838a-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="e838a-258">**Microsoft. PerceptionSimulation. SimulatedHandPose. Closed**</span><span class="sxs-lookup"><span data-stu-id="e838a-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="e838a-259">As junções de dedo da mão são configuradas para refletir uma pose fechada.</span><span class="sxs-lookup"><span data-stu-id="e838a-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="e838a-260">**Microsoft. PerceptionSimulation. SimulatedHandPose. Open**</span><span class="sxs-lookup"><span data-stu-id="e838a-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="e838a-261">As junções de dedo da mão são configuradas para refletir uma pose aberta.</span><span class="sxs-lookup"><span data-stu-id="e838a-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="e838a-262">**Microsoft. PerceptionSimulation. SimulatedHandPose. Point**</span><span class="sxs-lookup"><span data-stu-id="e838a-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="e838a-263">As junções de dedo da mão são configuradas para refletir uma pose de apontador.</span><span class="sxs-lookup"><span data-stu-id="e838a-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="e838a-264">**Microsoft. PerceptionSimulation. SimulatedHandPose. pinçar**</span><span class="sxs-lookup"><span data-stu-id="e838a-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="e838a-265">As junções de dedo da mão são configuradas para refletir uma pose de pinçagem.</span><span class="sxs-lookup"><span data-stu-id="e838a-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="e838a-266">**Microsoft. PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="e838a-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="e838a-267">O valor máximo válido para SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="e838a-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="e838a-268">Microsoft. PerceptionSimulation. Playbackstate</span><span class="sxs-lookup"><span data-stu-id="e838a-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="e838a-269">Descreve o estado de uma reprodução.</span><span class="sxs-lookup"><span data-stu-id="e838a-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="e838a-270">**Microsoft. PerceptionSimulation. Playbackstate. parado**</span><span class="sxs-lookup"><span data-stu-id="e838a-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="e838a-271">A gravação está atualmente parada e pronta para reprodução.</span><span class="sxs-lookup"><span data-stu-id="e838a-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="e838a-272">**Microsoft. PerceptionSimulation. Playbackstate. reproduzindo**</span><span class="sxs-lookup"><span data-stu-id="e838a-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="e838a-273">A gravação está sendo executada no momento.</span><span class="sxs-lookup"><span data-stu-id="e838a-273">The recording is currently playing.</span></span>

<span data-ttu-id="e838a-274">**Microsoft. PerceptionSimulation. Playbackstate. Paused**</span><span class="sxs-lookup"><span data-stu-id="e838a-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="e838a-275">A gravação está em pausa no momento.</span><span class="sxs-lookup"><span data-stu-id="e838a-275">The recording is currently paused.</span></span>

<span data-ttu-id="e838a-276">**Microsoft. PerceptionSimulation. Playbackstate. end**</span><span class="sxs-lookup"><span data-stu-id="e838a-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="e838a-277">A gravação atingiu o final.</span><span class="sxs-lookup"><span data-stu-id="e838a-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="e838a-278">Microsoft. PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="e838a-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="e838a-279">Descreve um vetor de 3 componentes, que pode descrever um ponto ou um vetor no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="e838a-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="e838a-280">**Microsoft. PerceptionSimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="e838a-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="e838a-281">O componente X do vetor.</span><span class="sxs-lookup"><span data-stu-id="e838a-281">The X component of the vector.</span></span>

<span data-ttu-id="e838a-282">**Microsoft. PerceptionSimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="e838a-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="e838a-283">O componente Y do vetor.</span><span class="sxs-lookup"><span data-stu-id="e838a-283">The Y component of the vector.</span></span>

<span data-ttu-id="e838a-284">**Microsoft. PerceptionSimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="e838a-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="e838a-285">O componente Z do vetor.</span><span class="sxs-lookup"><span data-stu-id="e838a-285">The Z component of the vector.</span></span>

<span data-ttu-id="e838a-286">**Microsoft. PerceptionSimulation. Vector3. #ctor (System. single, System. single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="e838a-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="e838a-287">Construa um novo Vector3.</span><span class="sxs-lookup"><span data-stu-id="e838a-287">Construct a new Vector3.</span></span>

<span data-ttu-id="e838a-288">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-288">Parameters</span></span>
* <span data-ttu-id="e838a-289">x – o componente x do vetor.</span><span class="sxs-lookup"><span data-stu-id="e838a-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="e838a-290">y-o componente y do vetor.</span><span class="sxs-lookup"><span data-stu-id="e838a-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="e838a-291">z-o componente z do vetor.</span><span class="sxs-lookup"><span data-stu-id="e838a-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="e838a-292">Microsoft. PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="e838a-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="e838a-293">Descreve uma rotação de 3 componentes.</span><span class="sxs-lookup"><span data-stu-id="e838a-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="e838a-294">**Microsoft. PerceptionSimulation. Rotation3. pitch**</span><span class="sxs-lookup"><span data-stu-id="e838a-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="e838a-295">O componente de pitch da rotação, em volta do eixo X.</span><span class="sxs-lookup"><span data-stu-id="e838a-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="e838a-296">**Microsoft. PerceptionSimulation. Rotation3. Guinad**</span><span class="sxs-lookup"><span data-stu-id="e838a-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="e838a-297">O componente de guinada da rotação, logo em volta do eixo Y.</span><span class="sxs-lookup"><span data-stu-id="e838a-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="e838a-298">**Microsoft. PerceptionSimulation. Rotation3. roll**</span><span class="sxs-lookup"><span data-stu-id="e838a-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="e838a-299">O componente de roll da rotação, logo em volta do eixo Z.</span><span class="sxs-lookup"><span data-stu-id="e838a-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="e838a-300">**Microsoft. PerceptionSimulation. Rotation3. #ctor (System. single, System. single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="e838a-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="e838a-301">Construa um novo Rotation3.</span><span class="sxs-lookup"><span data-stu-id="e838a-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="e838a-302">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-302">Parameters</span></span>
* <span data-ttu-id="e838a-303">Pitch-o componente de pitch da rotação.</span><span class="sxs-lookup"><span data-stu-id="e838a-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="e838a-304">guinada-o componente de guinada da rotação.</span><span class="sxs-lookup"><span data-stu-id="e838a-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="e838a-305">roll-o componente de rolagem da rotação.</span><span class="sxs-lookup"><span data-stu-id="e838a-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="e838a-306">Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="e838a-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="e838a-307">Descreve a configuração de uma junção em uma mão simulada.</span><span class="sxs-lookup"><span data-stu-id="e838a-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="e838a-308">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="e838a-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="e838a-309">A posição da junção.</span><span class="sxs-lookup"><span data-stu-id="e838a-309">The position of the joint.</span></span>

<span data-ttu-id="e838a-310">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Rotation**</span><span class="sxs-lookup"><span data-stu-id="e838a-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="e838a-311">A rotação da junção.</span><span class="sxs-lookup"><span data-stu-id="e838a-311">The rotation of the joint.</span></span>

<span data-ttu-id="e838a-312">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="e838a-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="e838a-313">A precisão de rastreamento da junção.</span><span class="sxs-lookup"><span data-stu-id="e838a-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="e838a-314">Microsoft. PerceptionSimulation. frustum</span><span class="sxs-lookup"><span data-stu-id="e838a-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="e838a-315">Descreve um frustum de exibição, como normalmente usado por uma câmera.</span><span class="sxs-lookup"><span data-stu-id="e838a-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="e838a-316">**Microsoft. PerceptionSimulation. frustum. near**</span><span class="sxs-lookup"><span data-stu-id="e838a-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="e838a-317">A distância mínima que está contida no frustum.</span><span class="sxs-lookup"><span data-stu-id="e838a-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="e838a-318">**Microsoft. PerceptionSimulation. frustum. far**</span><span class="sxs-lookup"><span data-stu-id="e838a-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="e838a-319">A distância máxima que está contida no frustum.</span><span class="sxs-lookup"><span data-stu-id="e838a-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="e838a-320">**Microsoft. PerceptionSimulation. frustum. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="e838a-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="e838a-321">O campo horizontal de exibição do frustum, em radianos (menor que PI).</span><span class="sxs-lookup"><span data-stu-id="e838a-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="e838a-322">**Microsoft. PerceptionSimulation. frustum. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="e838a-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="e838a-323">A proporção do campo horizontal de exibição para o campo vertical da exibição.</span><span class="sxs-lookup"><span data-stu-id="e838a-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="e838a-324">Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="e838a-324">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="e838a-325">Descreve a configuração da exibição do headset simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-325">Describes the configuration of the simulated headset's display.</span></span>

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

<span data-ttu-id="e838a-326">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="e838a-326">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="e838a-327">A transformação do centro da cabeça à esquerda para fins de renderização de estéreo.</span><span class="sxs-lookup"><span data-stu-id="e838a-327">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="e838a-328">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="e838a-328">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="e838a-329">A rotação do olho à esquerda para fins de renderização de estéreo.</span><span class="sxs-lookup"><span data-stu-id="e838a-329">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="e838a-330">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="e838a-330">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="e838a-331">A transformação do centro da cabeça para o olho certo para fins de renderização de estéreo.</span><span class="sxs-lookup"><span data-stu-id="e838a-331">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="e838a-332">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="e838a-332">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="e838a-333">A rotação do olho certo para fins de renderização de estéreo.</span><span class="sxs-lookup"><span data-stu-id="e838a-333">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="e838a-334">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. IPD**</span><span class="sxs-lookup"><span data-stu-id="e838a-334">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="e838a-335">O valor de IPD relatado pelo sistema para fins de renderização de estéreo.</span><span class="sxs-lookup"><span data-stu-id="e838a-335">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="e838a-336">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**</span><span class="sxs-lookup"><span data-stu-id="e838a-336">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="e838a-337">Se os valores fornecidos para as transformações de olho esquerdo e direito devem ser considerados válidos e aplicados ao sistema em execução.</span><span class="sxs-lookup"><span data-stu-id="e838a-337">Whether or not the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="e838a-338">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="e838a-338">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="e838a-339">Se o valor fornecido para o IPD deve ser considerado válido e aplicado ao sistema em execução.</span><span class="sxs-lookup"><span data-stu-id="e838a-339">Whether or not the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="e838a-340">Microsoft. PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="e838a-340">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="e838a-341">Raiz para gerar os pacotes usados para controlar um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e838a-341">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="e838a-342">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Device**</span><span class="sxs-lookup"><span data-stu-id="e838a-342">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="e838a-343">Recupere o objeto de dispositivo simulado que interpreta o humano simulado e o mundo simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-343">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="e838a-344">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Human**</span><span class="sxs-lookup"><span data-stu-id="e838a-344">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="e838a-345">Recupere o objeto que controla o humano simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-345">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="e838a-346">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Reset**</span><span class="sxs-lookup"><span data-stu-id="e838a-346">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="e838a-347">Redefine a simulação para seu estado padrão.</span><span class="sxs-lookup"><span data-stu-id="e838a-347">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="e838a-348">Microsoft. PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="e838a-348">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="e838a-349">Interface que descreve o dispositivo que interpreta o mundo simulado e o humano simulado</span><span class="sxs-lookup"><span data-stu-id="e838a-349">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="e838a-350">**Microsoft. PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="e838a-350">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="e838a-351">Recupere o controlador de cabeçalho do dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-351">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="e838a-352">**Microsoft. PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="e838a-352">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="e838a-353">Recupere o rastreador de mão do dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-353">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="e838a-354">**Microsoft. PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="e838a-354">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="e838a-355">Defina as propriedades do dispositivo simulado para corresponder ao tipo de dispositivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="e838a-355">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="e838a-356">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-356">Parameters</span></span>
* <span data-ttu-id="e838a-357">tipo – o novo tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="e838a-357">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="e838a-358">Microsoft. PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="e838a-358">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="e838a-359">Propriedades adicionais estão disponíveis por meio da conversão de ISimulatedDevice para ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="e838a-359">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="e838a-360">**Microsoft. PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="e838a-360">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="e838a-361">Recupere ou defina se o humano simulado está ou não ativamente desativando o headset.</span><span class="sxs-lookup"><span data-stu-id="e838a-361">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="e838a-362">**Microsoft. PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="e838a-362">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="e838a-363">Recupere ou defina as propriedades da exibição simulada.</span><span class="sxs-lookup"><span data-stu-id="e838a-363">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="e838a-364">Microsoft. PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="e838a-364">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="e838a-365">Interface que descreve a parte do dispositivo simulado que controla o início do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-365">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="e838a-366">**Microsoft. PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="e838a-366">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="e838a-367">Recupera e define o modo de controlador de cabeçalho atual.</span><span class="sxs-lookup"><span data-stu-id="e838a-367">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="e838a-368">Microsoft. PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="e838a-368">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="e838a-369">Interface que descreve a parte do dispositivo simulado que controla as mãos do humano simulado</span><span class="sxs-lookup"><span data-stu-id="e838a-369">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="e838a-370">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e838a-370">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="e838a-371">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="e838a-371">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="e838a-372">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Position**</span><span class="sxs-lookup"><span data-stu-id="e838a-372">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="e838a-373">Recupere e defina a posição do controlador de mão simulado em relação ao centro do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="e838a-373">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="e838a-374">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. pitch**</span><span class="sxs-lookup"><span data-stu-id="e838a-374">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="e838a-375">Recupere e defina o timbre inferior do controlador de mão simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-375">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="e838a-376">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="e838a-376">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="e838a-377">Recupere e defina se a frustum do controlador de mão simulado é ignorada.</span><span class="sxs-lookup"><span data-stu-id="e838a-377">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="e838a-378">Quando ignorado, ambas as mãos estão sempre visíveis.</span><span class="sxs-lookup"><span data-stu-id="e838a-378">When ignored, both hands are always visible.</span></span> <span data-ttu-id="e838a-379">Quando não ignoradas (as mãos padrão) ficam visíveis apenas quando estão dentro do frustum do rastreador.</span><span class="sxs-lookup"><span data-stu-id="e838a-379">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="e838a-380">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. frustum**</span><span class="sxs-lookup"><span data-stu-id="e838a-380">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="e838a-381">Recupere e defina as propriedades frustum usadas para determinar se as mãos estão visíveis para o controlador de mão simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-381">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="e838a-382">Microsoft. PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="e838a-382">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="e838a-383">Interface de nível superior para controlar o humano simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-383">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="e838a-384">**Microsoft. PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e838a-384">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="e838a-385">Recupere e defina a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="e838a-385">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="e838a-386">A posição corresponde a um ponto no centro dos pés humanos.</span><span class="sxs-lookup"><span data-stu-id="e838a-386">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="e838a-387">**Microsoft. PerceptionSimulation. ISimulatedHuman. Direction**</span><span class="sxs-lookup"><span data-stu-id="e838a-387">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="e838a-388">Recupere e defina a direção das faces humanas simuladas do mundo.</span><span class="sxs-lookup"><span data-stu-id="e838a-388">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="e838a-389">0 radianos está voltado para baixo no eixo Z negativo.</span><span class="sxs-lookup"><span data-stu-id="e838a-389">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="e838a-390">Radianos positivos giram no sentido horário sobre o eixo Y.</span><span class="sxs-lookup"><span data-stu-id="e838a-390">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="e838a-391">**Microsoft. PerceptionSimulation. ISimulatedHuman. Height**</span><span class="sxs-lookup"><span data-stu-id="e838a-391">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="e838a-392">Recupere e defina a altura do humano simulado, em metros.</span><span class="sxs-lookup"><span data-stu-id="e838a-392">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="e838a-393">**Microsoft. PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="e838a-393">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="e838a-394">Recupere o lado esquerdo do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-394">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="e838a-395">**Microsoft. PerceptionSimulation. ISimulatedHuman. RightHand**</span><span class="sxs-lookup"><span data-stu-id="e838a-395">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="e838a-396">Recupere o lado direito do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-396">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="e838a-397">**Microsoft. PerceptionSimulation. ISimulatedHuman. Head**</span><span class="sxs-lookup"><span data-stu-id="e838a-397">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="e838a-398">Recupere o cabeçalho do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-398">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="e838a-399">**Microsoft. PerceptionSimulation. ISimulatedHuman. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="e838a-399">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="e838a-400">Mova o humano simulado relativo à sua posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="e838a-400">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="e838a-401">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-401">Parameters</span></span>
* <span data-ttu-id="e838a-402">translação-a tradução a ser movida, relativa à posição atual.</span><span class="sxs-lookup"><span data-stu-id="e838a-402">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="e838a-403">**Microsoft. PerceptionSimulation. ISimulatedHuman. Rotate (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="e838a-403">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="e838a-404">Girar o humano simulado em relação à sua direção atual, no sentido horário, sobre o eixo Y</span><span class="sxs-lookup"><span data-stu-id="e838a-404">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="e838a-405">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-405">Parameters</span></span>
* <span data-ttu-id="e838a-406">radianos-o valor a ser girado em volta do eixo Y.</span><span class="sxs-lookup"><span data-stu-id="e838a-406">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="e838a-407">Microsoft. PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="e838a-407">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="e838a-408">Propriedades adicionais estão disponíveis por meio da conversão de ISimulatedHuman para ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="e838a-408">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="e838a-409">**Microsoft. PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="e838a-409">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="e838a-410">Recupere o controlador esquerdo 6-DOF.</span><span class="sxs-lookup"><span data-stu-id="e838a-410">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="e838a-411">**Microsoft. PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="e838a-411">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="e838a-412">Recupere o controlador de 6 DOF à direita.</span><span class="sxs-lookup"><span data-stu-id="e838a-412">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="e838a-413">Microsoft. PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="e838a-413">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="e838a-414">Interface que descreve uma mão do humano simulado</span><span class="sxs-lookup"><span data-stu-id="e838a-414">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="e838a-415">**Microsoft. PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e838a-415">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="e838a-416">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="e838a-416">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="e838a-417">**Microsoft. PerceptionSimulation. ISimulatedHand. Position**</span><span class="sxs-lookup"><span data-stu-id="e838a-417">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="e838a-418">Recupere e defina a posição da mão simulada em relação ao humano, em metros.</span><span class="sxs-lookup"><span data-stu-id="e838a-418">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="e838a-419">**Microsoft. PerceptionSimulation. ISimulatedHand. Activated**</span><span class="sxs-lookup"><span data-stu-id="e838a-419">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="e838a-420">Recuperar e definir se a mão está ativada no momento.</span><span class="sxs-lookup"><span data-stu-id="e838a-420">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="e838a-421">**Microsoft. PerceptionSimulation. ISimulatedHand. Visible**</span><span class="sxs-lookup"><span data-stu-id="e838a-421">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="e838a-422">Recupere se a mão está visível no momento para o SimulatedDevice (ou seja, se está em uma posição a ser detectada pelo HandTracker).</span><span class="sxs-lookup"><span data-stu-id="e838a-422">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="e838a-423">**Microsoft. PerceptionSimulation. ISimulatedHand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="e838a-423">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="e838a-424">Mova a mão de modo que fique visível para o SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="e838a-424">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="e838a-425">**Microsoft. PerceptionSimulation. ISimulatedHand. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="e838a-425">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="e838a-426">Mova a posição da mão simulada em relação à sua posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="e838a-426">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="e838a-427">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-427">Parameters</span></span>
* <span data-ttu-id="e838a-428">translation-o valor para converter a mão simulada.</span><span class="sxs-lookup"><span data-stu-id="e838a-428">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="e838a-429">**Microsoft. PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="e838a-429">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="e838a-430">Execute um gesto usando a mão simulada.</span><span class="sxs-lookup"><span data-stu-id="e838a-430">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="e838a-431">Ele só será detectado pelo sistema se a mão estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="e838a-431">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="e838a-432">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-432">Parameters</span></span>
* <span data-ttu-id="e838a-433">gesto-o gesto a ser executado.</span><span class="sxs-lookup"><span data-stu-id="e838a-433">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="e838a-434">Microsoft. PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="e838a-434">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="e838a-435">Propriedades adicionais estão disponíveis por meio da conversão de um ISimulatedHand em ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="e838a-435">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="e838a-436">**Microsoft. PerceptionSimulation. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="e838a-436">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="e838a-437">Recupere ou defina a rotação da mão simulada.</span><span class="sxs-lookup"><span data-stu-id="e838a-437">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="e838a-438">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="e838a-438">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="e838a-439">Microsoft. PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="e838a-439">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="e838a-440">Propriedades adicionais estão disponíveis por meio da conversão de um ISimulatedHand para ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="e838a-440">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="e838a-441">**Microsoft. PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="e838a-441">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="e838a-442">Obter a configuração conjunta para a junção especificada.</span><span class="sxs-lookup"><span data-stu-id="e838a-442">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="e838a-443">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="e838a-443">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="e838a-444">Defina a configuração conjunta para a junção especificada.</span><span class="sxs-lookup"><span data-stu-id="e838a-444">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="e838a-445">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="e838a-445">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="e838a-446">Defina a mão como uma pose conhecida com um sinalizador opcional para animar.</span><span class="sxs-lookup"><span data-stu-id="e838a-446">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="e838a-447">Observação: a animação não resultará em junções imediatamente refletindo suas configurações de conjuntos finais.</span><span class="sxs-lookup"><span data-stu-id="e838a-447">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="e838a-448">Microsoft. PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="e838a-448">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="e838a-449">Interface que descreve o cabeçalho do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-449">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="e838a-450">**Microsoft. PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e838a-450">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="e838a-451">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="e838a-451">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="e838a-452">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotation**</span><span class="sxs-lookup"><span data-stu-id="e838a-452">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="e838a-453">Recupere a rotação da cabeça simulada.</span><span class="sxs-lookup"><span data-stu-id="e838a-453">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="e838a-454">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="e838a-454">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="e838a-455">**Microsoft. PerceptionSimulation. ISimulatedHead. diâmetro**</span><span class="sxs-lookup"><span data-stu-id="e838a-455">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="e838a-456">Recupere o diâmetro da cabeça simulada.</span><span class="sxs-lookup"><span data-stu-id="e838a-456">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="e838a-457">Esse valor é usado para determinar o centro da cabeça (ponto de rotação).</span><span class="sxs-lookup"><span data-stu-id="e838a-457">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="e838a-458">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="e838a-458">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="e838a-459">Girar a cabeça simulada em relação à sua rotação atual.</span><span class="sxs-lookup"><span data-stu-id="e838a-459">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="e838a-460">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="e838a-460">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="e838a-461">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-461">Parameters</span></span>
* <span data-ttu-id="e838a-462">rotação-o valor a ser girado.</span><span class="sxs-lookup"><span data-stu-id="e838a-462">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="e838a-463">Microsoft. PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="e838a-463">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="e838a-464">Propriedades adicionais estão disponíveis por meio da conversão de um ISimulatedHead para ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="e838a-464">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="e838a-465">**Microsoft. PerceptionSimulation. ISimulatedHead2. eyess**</span><span class="sxs-lookup"><span data-stu-id="e838a-465">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="e838a-466">Recupere os olhos do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-466">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="e838a-467">Microsoft. PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="e838a-467">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="e838a-468">Interface que descreve um controlador de 6 DOF associado ao humano simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-468">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="e838a-469">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e838a-469">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="e838a-470">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="e838a-470">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="e838a-471">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. status**</span><span class="sxs-lookup"><span data-stu-id="e838a-471">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="e838a-472">Recupere ou defina o estado atual do controlador.</span><span class="sxs-lookup"><span data-stu-id="e838a-472">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="e838a-473">O status do controlador deve ser definido com um valor diferente de desativado antes que as chamadas para mover, girar ou pressionar botões tenham sucesso.</span><span class="sxs-lookup"><span data-stu-id="e838a-473">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="e838a-474">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Position**</span><span class="sxs-lookup"><span data-stu-id="e838a-474">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="e838a-475">Recupere ou defina a posição do controlador simulado em relação ao humano, em metros.</span><span class="sxs-lookup"><span data-stu-id="e838a-475">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="e838a-476">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Orientation**</span><span class="sxs-lookup"><span data-stu-id="e838a-476">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="e838a-477">Recupere ou defina a orientação do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-477">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="e838a-478">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="e838a-478">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="e838a-479">Mova a posição do controlador simulado em relação à sua posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="e838a-479">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="e838a-480">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-480">Parameters</span></span>
* <span data-ttu-id="e838a-481">translation-o valor para converter o controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-481">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="e838a-482">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="e838a-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="e838a-483">Pressione um botão no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-483">Press a button on the simulated controller.</span></span>  <span data-ttu-id="e838a-484">Ele só será detectado pelo sistema se o controlador estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="e838a-484">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="e838a-485">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-485">Parameters</span></span>
* <span data-ttu-id="e838a-486">botão-o botão para pressionar.</span><span class="sxs-lookup"><span data-stu-id="e838a-486">button - The button to press.</span></span>

<span data-ttu-id="e838a-487">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="e838a-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="e838a-488">Libere um botão no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-488">Release a button on the simulated controller.</span></span>  <span data-ttu-id="e838a-489">Ele só será detectado pelo sistema se o controlador estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="e838a-489">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="e838a-490">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-490">Parameters</span></span>
* <span data-ttu-id="e838a-491">botão-o botão a ser liberado.</span><span class="sxs-lookup"><span data-stu-id="e838a-491">button - The button to release.</span></span>

<span data-ttu-id="e838a-492">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="e838a-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="e838a-493">Obtenha a posição de um dedo simulado no Touchpad do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-493">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="e838a-494">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-494">Parameters</span></span>
* <span data-ttu-id="e838a-495">x-a posição horizontal do dedo.</span><span class="sxs-lookup"><span data-stu-id="e838a-495">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="e838a-496">y-a posição vertical do dedo.</span><span class="sxs-lookup"><span data-stu-id="e838a-496">y - The vertical position of the finger.</span></span>

<span data-ttu-id="e838a-497">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="e838a-497">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="e838a-498">Defina a posição de um dedo simulado no Touchpad do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-498">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="e838a-499">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-499">Parameters</span></span>
* <span data-ttu-id="e838a-500">x-a posição horizontal do dedo.</span><span class="sxs-lookup"><span data-stu-id="e838a-500">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="e838a-501">y-a posição vertical do dedo.</span><span class="sxs-lookup"><span data-stu-id="e838a-501">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="e838a-502">Microsoft. PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="e838a-502">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="e838a-503">Propriedades e métodos adicionais estão disponíveis por meio da conversão de um ISimulatedSixDofController para ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="e838a-503">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="e838a-504">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="e838a-504">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="e838a-505">Obtém a posição do Thumbstick simulado no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-505">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="e838a-506">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-506">Parameters</span></span>
* <span data-ttu-id="e838a-507">x-a posição horizontal do Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="e838a-507">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="e838a-508">y-a posição vertical do Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="e838a-508">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="e838a-509">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="e838a-509">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="e838a-510">Defina a posição do Thumbstick simulado no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-510">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="e838a-511">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-511">Parameters</span></span>
* <span data-ttu-id="e838a-512">x-a posição horizontal do Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="e838a-512">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="e838a-513">y-a posição vertical do Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="e838a-513">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="e838a-514">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="e838a-514">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="e838a-515">Recupere ou defina o nível de bateria do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-515">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="e838a-516">O valor deve ser maior que 0,0 e menor ou igual a 100,0.</span><span class="sxs-lookup"><span data-stu-id="e838a-516">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="e838a-517">Microsoft. PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="e838a-517">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="e838a-518">Interface que descreve os olhos do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-518">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="e838a-519">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotation**</span><span class="sxs-lookup"><span data-stu-id="e838a-519">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="e838a-520">Recupere a rotação dos olhos simulados.</span><span class="sxs-lookup"><span data-stu-id="e838a-520">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="e838a-521">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="e838a-521">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="e838a-522">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="e838a-522">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="e838a-523">Gire os olhos simulados em relação à sua rotação atual.</span><span class="sxs-lookup"><span data-stu-id="e838a-523">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="e838a-524">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="e838a-524">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="e838a-525">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-525">Parameters</span></span>
* <span data-ttu-id="e838a-526">rotação-o valor a ser girado.</span><span class="sxs-lookup"><span data-stu-id="e838a-526">rotation - The amount to rotate.</span></span>

<span data-ttu-id="e838a-527">**Microsoft. PerceptionSimulation. ISimulatedEyes. calibrable**</span><span class="sxs-lookup"><span data-stu-id="e838a-527">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="e838a-528">Recupera ou define o estado de calibragem dos olhos simulados.</span><span class="sxs-lookup"><span data-stu-id="e838a-528">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="e838a-529">**Microsoft. PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e838a-529">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="e838a-530">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="e838a-530">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="e838a-531">Microsoft. PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="e838a-531">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="e838a-532">Interface para interagir com uma única gravação carregada para reprodução.</span><span class="sxs-lookup"><span data-stu-id="e838a-532">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="e838a-533">**Microsoft. PerceptionSimulation. ISimulationRecording. datatipos**</span><span class="sxs-lookup"><span data-stu-id="e838a-533">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="e838a-534">Recupera a lista de tipos de dados na gravação.</span><span class="sxs-lookup"><span data-stu-id="e838a-534">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="e838a-535">**Microsoft. PerceptionSimulation. ISimulationRecording. State**</span><span class="sxs-lookup"><span data-stu-id="e838a-535">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="e838a-536">Recupera o estado atual da gravação.</span><span class="sxs-lookup"><span data-stu-id="e838a-536">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="e838a-537">**Microsoft. PerceptionSimulation. ISimulationRecording. Play**</span><span class="sxs-lookup"><span data-stu-id="e838a-537">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="e838a-538">Inicie a reprodução.</span><span class="sxs-lookup"><span data-stu-id="e838a-538">Start the playback.</span></span> <span data-ttu-id="e838a-539">Se a gravação for pausada, a reprodução será retomada do local em pausa; Se for interrompido, a reprodução será iniciada no início.</span><span class="sxs-lookup"><span data-stu-id="e838a-539">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="e838a-540">Se já estiver em execução, essa chamada será ignorada.</span><span class="sxs-lookup"><span data-stu-id="e838a-540">If already playing, this call is ignored.</span></span>

<span data-ttu-id="e838a-541">**Microsoft. PerceptionSimulation. ISimulationRecording. Pause**</span><span class="sxs-lookup"><span data-stu-id="e838a-541">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="e838a-542">Pausa a reprodução em seu local atual.</span><span class="sxs-lookup"><span data-stu-id="e838a-542">Pauses the playback at its current location.</span></span> <span data-ttu-id="e838a-543">Se a gravação for interrompida, a chamada será ignorada.</span><span class="sxs-lookup"><span data-stu-id="e838a-543">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="e838a-544">**Microsoft. PerceptionSimulation. ISimulationRecording. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="e838a-544">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="e838a-545">Procura a gravação no tempo especificado (em intervalos de 100 nanossegundos desde o início) e pausa nesse local.</span><span class="sxs-lookup"><span data-stu-id="e838a-545">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="e838a-546">Se o tempo estiver além do fim da gravação, ele será pausado no último quadro.</span><span class="sxs-lookup"><span data-stu-id="e838a-546">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="e838a-547">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-547">Parameters</span></span>
* <span data-ttu-id="e838a-548">tiques-o tempo para o qual buscar.</span><span class="sxs-lookup"><span data-stu-id="e838a-548">ticks - The time to which to seek.</span></span>

<span data-ttu-id="e838a-549">**Microsoft. PerceptionSimulation. ISimulationRecording. Stop**</span><span class="sxs-lookup"><span data-stu-id="e838a-549">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="e838a-550">Interrompe a reprodução e redefine a posição para o início.</span><span class="sxs-lookup"><span data-stu-id="e838a-550">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="e838a-551">Microsoft. PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="e838a-551">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="e838a-552">Interface para receber alterações de estado durante a reprodução.</span><span class="sxs-lookup"><span data-stu-id="e838a-552">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="e838a-553">**Microsoft. PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. reproduzstate)**</span><span class="sxs-lookup"><span data-stu-id="e838a-553">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="e838a-554">Chamado quando o estado de reprodução de um ISimulationRecording é alterado.</span><span class="sxs-lookup"><span data-stu-id="e838a-554">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="e838a-555">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-555">Parameters</span></span>
* <span data-ttu-id="e838a-556">newState – o novo estado da gravação.</span><span class="sxs-lookup"><span data-stu-id="e838a-556">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="e838a-557">Microsoft. PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="e838a-557">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="e838a-558">Objeto raiz para criar objetos de simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="e838a-558">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="e838a-559">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="e838a-559">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="e838a-560">Crie um objeto para gerar pacotes simulados e fornecê-los ao coletor fornecido.</span><span class="sxs-lookup"><span data-stu-id="e838a-560">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="e838a-561">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-561">Parameters</span></span>
* <span data-ttu-id="e838a-562">coletor-o coletor que receberá todos os pacotes gerados.</span><span class="sxs-lookup"><span data-stu-id="e838a-562">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="e838a-563">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e838a-563">Return value</span></span>

<span data-ttu-id="e838a-564">O gerente criado.</span><span class="sxs-lookup"><span data-stu-id="e838a-564">The created Manager.</span></span>

<span data-ttu-id="e838a-565">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System. String)**</span><span class="sxs-lookup"><span data-stu-id="e838a-565">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="e838a-566">Crie um coletor que armazena todos os pacotes recebidos em um arquivo no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="e838a-566">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="e838a-567">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-567">Parameters</span></span>
* <span data-ttu-id="e838a-568">caminho-o caminho do arquivo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="e838a-568">path - The path of the file to create.</span></span>

<span data-ttu-id="e838a-569">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e838a-569">Return value</span></span>

<span data-ttu-id="e838a-570">O coletor criado.</span><span class="sxs-lookup"><span data-stu-id="e838a-570">The created sink.</span></span>

<span data-ttu-id="e838a-571">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="e838a-571">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="e838a-572">Carregar uma gravação do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="e838a-572">Load a recording from the specified file.</span></span>

<span data-ttu-id="e838a-573">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-573">Parameters</span></span>
* <span data-ttu-id="e838a-574">caminho-o caminho do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="e838a-574">path - The path of the file to load.</span></span>
* <span data-ttu-id="e838a-575">Factory-uma fábrica usada pela gravação para criar um ISimulationStreamSink quando necessário.</span><span class="sxs-lookup"><span data-stu-id="e838a-575">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="e838a-576">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e838a-576">Return value</span></span>

<span data-ttu-id="e838a-577">A gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="e838a-577">The loaded recording.</span></span>

<span data-ttu-id="e838a-578">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="e838a-578">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="e838a-579">Carregar uma gravação do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="e838a-579">Load a recording from the specified file.</span></span>

<span data-ttu-id="e838a-580">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-580">Parameters</span></span>
* <span data-ttu-id="e838a-581">caminho-o caminho do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="e838a-581">path - The path of the file to load.</span></span>
* <span data-ttu-id="e838a-582">Factory-uma fábrica usada pela gravação para criar um ISimulationStreamSink quando necessário.</span><span class="sxs-lookup"><span data-stu-id="e838a-582">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="e838a-583">retorno de chamada-um retorno de chamada que recebe atualizações que recebem o status da gravação.</span><span class="sxs-lookup"><span data-stu-id="e838a-583">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="e838a-584">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e838a-584">Return value</span></span>

<span data-ttu-id="e838a-585">A gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="e838a-585">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="e838a-586">Microsoft. PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="e838a-586">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="e838a-587">Descreve os diferentes tipos de dados de fluxo.</span><span class="sxs-lookup"><span data-stu-id="e838a-587">Describes the different types of stream data.</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

<span data-ttu-id="e838a-588">**Microsoft. PerceptionSimulation. StreamDataTypes. None**</span><span class="sxs-lookup"><span data-stu-id="e838a-588">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="e838a-589">Um valor de sentinela usado para indicar nenhum tipo de dados de fluxo.</span><span class="sxs-lookup"><span data-stu-id="e838a-589">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="e838a-590">**Microsoft. PerceptionSimulation. StreamDataTypes. Head**</span><span class="sxs-lookup"><span data-stu-id="e838a-590">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="e838a-591">Fluxo de dados em relação à posição e à orientação do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="e838a-591">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="e838a-592">**Microsoft. PerceptionSimulation. StreamDataTypes. hands**</span><span class="sxs-lookup"><span data-stu-id="e838a-592">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="e838a-593">Fluxo de dados em relação à posição e aos gestos de mãos.</span><span class="sxs-lookup"><span data-stu-id="e838a-593">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="e838a-594">**Microsoft. PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="e838a-594">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="e838a-595">Fluxo de dados referente ao mapeamento espacial do ambiente.</span><span class="sxs-lookup"><span data-stu-id="e838a-595">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="e838a-596">**Microsoft. PerceptionSimulation. StreamDataTypes. Calibration**</span><span class="sxs-lookup"><span data-stu-id="e838a-596">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="e838a-597">Fluxo de dados referente à calibragem do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e838a-597">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="e838a-598">Os pacotes de calibragem são aceitos apenas por um sistema no modo remoto.</span><span class="sxs-lookup"><span data-stu-id="e838a-598">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="e838a-599">**Microsoft. PerceptionSimulation. StreamDataTypes. Environment**</span><span class="sxs-lookup"><span data-stu-id="e838a-599">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="e838a-600">Fluxo de dados em relação ao ambiente do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e838a-600">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="e838a-601">**Microsoft. PerceptionSimulation. StreamDataTypes. SixDofControllers**</span><span class="sxs-lookup"><span data-stu-id="e838a-601">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="e838a-602">Fluxo de dados em relação aos controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="e838a-602">Stream of data regarding motion controllers.</span></span>

<span data-ttu-id="e838a-603">**Microsoft. PerceptionSimulation. StreamDataTypes. eyess**</span><span class="sxs-lookup"><span data-stu-id="e838a-603">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="e838a-604">Fluxo de dados em relação aos olhos do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="e838a-604">Stream of data regarding the eyes of the simulated human.</span></span>

<span data-ttu-id="e838a-605">**Microsoft. PerceptionSimulation. StreamDataTypes. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="e838a-605">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="e838a-606">Fluxo de dados em relação à configuração de exibição do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e838a-606">Stream of data regarding the display configuration of the device.</span></span>

<span data-ttu-id="e838a-607">**Microsoft. PerceptionSimulation. StreamDataTypes. All**</span><span class="sxs-lookup"><span data-stu-id="e838a-607">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="e838a-608">Um valor de sentinela usado para indicar todos os tipos de dados gravados.</span><span class="sxs-lookup"><span data-stu-id="e838a-608">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="e838a-609">Microsoft. PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="e838a-609">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="e838a-610">Um objeto que recebe pacotes de dados de um fluxo de simulação.</span><span class="sxs-lookup"><span data-stu-id="e838a-610">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="e838a-611">**Microsoft. PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (pacote de comprimento uint, Byte [])**</span><span class="sxs-lookup"><span data-stu-id="e838a-611">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="e838a-612">Recebe um único pacote, que é digitado internamente e com controle de versão.</span><span class="sxs-lookup"><span data-stu-id="e838a-612">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="e838a-613">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e838a-613">Parameters</span></span>
* <span data-ttu-id="e838a-614">comprimento-o comprimento do pacote.</span><span class="sxs-lookup"><span data-stu-id="e838a-614">length - The length of the packet.</span></span>
* <span data-ttu-id="e838a-615">pacote-os dados do pacote.</span><span class="sxs-lookup"><span data-stu-id="e838a-615">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="e838a-616">Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="e838a-616">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="e838a-617">Um objeto que cria ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="e838a-617">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="e838a-618">**Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**</span><span class="sxs-lookup"><span data-stu-id="e838a-618">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="e838a-619">Cria uma única instância de ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="e838a-619">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="e838a-620">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e838a-620">Return value</span></span>

<span data-ttu-id="e838a-621">O coletor criado.</span><span class="sxs-lookup"><span data-stu-id="e838a-621">The created sink.</span></span>
