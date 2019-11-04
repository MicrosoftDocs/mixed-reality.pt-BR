---
title: Simulação de percepção
description: Um guia para usar a biblioteca de simulação de percepção para automatizar a entrada simulada para aplicativos de imersão
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, simulação, teste
ms.openlocfilehash: 503533bc5a2e9307b7c5217632d42670285aac0a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437551"
---
# <a name="perception-simulation"></a><span data-ttu-id="ce3e5-104">Simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="ce3e5-104">Perception simulation</span></span>

<span data-ttu-id="ce3e5-105">Deseja criar um teste automatizado para seu aplicativo?</span><span class="sxs-lookup"><span data-stu-id="ce3e5-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="ce3e5-106">Você deseja que seus testes vão além dos testes de unidade de nível de componente e realmente exercitam seu aplicativo de ponta a ponta?</span><span class="sxs-lookup"><span data-stu-id="ce3e5-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="ce3e5-107">A simulação de percepção é o que você está procurando.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="ce3e5-108">A biblioteca de simulação de percepção envia dados de entrada humanos e mundiais para seu aplicativo para que você possa automatizar seus testes.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="ce3e5-109">Por exemplo, você pode simular a entrada de uma aparência humana para uma posição específica e repetível e, em seguida, executar um gesto ou usar um controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="ce3e5-110">A simulação de percepção pode enviar uma entrada simulada como esta para um HoloLens físico, o emulador do HoloLens (1º gen), o emulador do HoloLens 2 ou um PC com o portal de realidade misturada instalado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="ce3e5-111">A simulação de percepção ignora os sensores ao vivo em um dispositivo de realidade misturada e envia a entrada simulada para aplicativos em execução no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="ce3e5-112">Os aplicativos recebem esses eventos de entrada por meio das mesmas APIs que sempre usam e não conseguem dizer a diferença entre a execução com sensores reais versus a execução com a simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="ce3e5-113">A simulação de percepção é a mesma tecnologia usada pelos emuladores do HoloLens para enviar a entrada simulada para a máquina virtual do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="ce3e5-114">Para começar a usar a simulação em seu código, comece criando um objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="ce3e5-115">A partir desse objeto, você pode emitir comandos para controlar as propriedades de um "humano" simulado, incluindo posição de cabeçalho, posição mão e gestos, e você pode habilitar e manipular controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="ce3e5-116">Configurando um projeto do Visual Studio para simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="ce3e5-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="ce3e5-117">[Instale o emulador do HoloLens](install-the-tools.md) no seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="ce3e5-118">O emulador inclui as bibliotecas que serão usadas para a simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="ce3e5-119">Crie um novo projeto de C# desktop do Visual Studio (um projeto de console funciona muito bem para começar).</span><span class="sxs-lookup"><span data-stu-id="ce3e5-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="ce3e5-120">Adicione os seguintes binários ao seu projeto como referências (projeto-> referência ao suplemento de >...). Você pode encontrá-los em% ProgramFiles (x86)% \ Microsoft XDE\\(versão), como **% ProgramFiles (x86)% \ Microsoft XDE\\10.0.18362.0** para o emulador do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="ce3e5-121">(Observação: embora os binários façam parte do emulador do HoloLens 2, eles também funcionam para a realidade mista do Windows na área de trabalho.) um.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="ce3e5-122">PerceptionSimulationManager. Interop. dll-wrapper C# gerenciado para simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="ce3e5-123">b.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-123">b.</span></span> <span data-ttu-id="ce3e5-124">PerceptionSimulationRest. dll-Library para configurar um canal de comunicação de soquete da Web para o HoloLens ou o emulador.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="ce3e5-125">c.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-125">c.</span></span> <span data-ttu-id="ce3e5-126">SimulationStream. Interop. dll-tipos compartilhados para simulação.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="ce3e5-127">Adicione o binário de implementação PerceptionSimulationManager. dll ao seu projeto a.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="ce3e5-128">Primeiro, adicione-o como um binário ao projeto (projeto-> Adicionar > item existente...). Salve-o como um link para que ele não o copie para a pasta de origem do projeto.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="ce3e5-129">![adicionar PerceptionSimulationManager. dll ao projeto como um link](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="ce3e5-130">Em seguida, certifique-se de que ele seja copiado para a pasta de saída na compilação.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="ce3e5-131">Isso está na folha de propriedades do binário.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="ce3e5-132">![marcar PerceptionSimulationManager. dll para copiar para o diretório de saída](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="ce3e5-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="ce3e5-133">Defina sua plataforma de solução ativa como x64.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="ce3e5-134">(Use o Configuration Manager para criar uma entrada de plataforma para x64 se ainda não existir uma.)</span><span class="sxs-lookup"><span data-stu-id="ce3e5-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="ce3e5-135">Criando um objeto do Gerenciador de IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="ce3e5-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="ce3e5-136">Para controlar a simulação, você emitirá atualizações para objetos recuperados de um objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="ce3e5-137">A primeira etapa é obter esse objeto e conectá-lo ao seu dispositivo de destino ou emulador.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="ce3e5-138">Você pode obter o endereço IP do emulador clicando no botão portal do dispositivo na barra de [ferramentas](using-the-hololens-emulator.md)</span><span class="sxs-lookup"><span data-stu-id="ce3e5-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="ce3e5-139">![ícone do portal de dispositivo aberto](images/emulator-deviceportal.png) **abrir o portal do dispositivo**: Abra o portal do dispositivo do Windows para o sistema operacional do HoloLens no emulador.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="ce3e5-140">Para a realidade mista do Windows, isso pode ser recuperado no aplicativo configurações em "atualizar & segurança" e, em seguida, "para desenvolvedores" na seção "conectar usando:" em "habilitar o portal do dispositivo".</span><span class="sxs-lookup"><span data-stu-id="ce3e5-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="ce3e5-141">Lembre-se de anotar o endereço IP e a porta.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="ce3e5-142">Primeiro, você chamará RestSimulationStreamSink. Create para obter um objeto RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="ce3e5-143">Esse é o dispositivo ou emulador de destino que você controlará em uma conexão http.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="ce3e5-144">Seus comandos serão passados e manipulados pelo portal do [dispositivo Windows](using-the-windows-device-portal.md) em execução no dispositivo ou emulador.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="ce3e5-145">Os quatro parâmetros necessários para criar um objeto são:</span><span class="sxs-lookup"><span data-stu-id="ce3e5-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="ce3e5-146">URI-Uri-endereço IP do dispositivo de destino (por exemplo, "https://123.123.123.123" ou "https://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="ce3e5-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="ce3e5-147">System .net. NetworkCredential credenciais-nome de usuário/senha para se conectar ao [portal de dispositivo do Windows](using-the-windows-device-portal.md) no dispositivo ou emulador de destino.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="ce3e5-148">Se você estiver se conectando ao emulador por meio de seu endereço local (por exemplo,*168...* \*) no mesmo PC, todas as credenciais serão aceitas.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="ce3e5-149">bool normal-true para prioridade normal, false para baixa prioridade.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="ce3e5-150">Em geral, você desejará definir isso como *verdadeiro* para cenários de teste, o que permite que seu teste assuma o controle.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="ce3e5-151">O emulador e a simulação de realidade mista do Windows usam conexões de baixa prioridade.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="ce3e5-152">Se o teste também usar uma conexão de baixa prioridade, a conexão estabelecida mais recentemente estará no controle.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="ce3e5-153">System. Threading. CancellationToken token-token para cancelar a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="ce3e5-154">Em segundo lugar, você criará o IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="ce3e5-155">Esse é o objeto que você usa para controlar a simulação.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="ce3e5-156">Observe que isso também deve ser feito em um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="ce3e5-157">Controlar o humano simulado</span><span class="sxs-lookup"><span data-stu-id="ce3e5-157">Control the simulated Human</span></span>

<span data-ttu-id="ce3e5-158">Um IPerceptionSimulationManager tem uma propriedade humana que retorna um objeto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="ce3e5-159">Para controlar o humano simulado, execute operações nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="ce3e5-160">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ce3e5-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="ce3e5-161">Aplicativo de C# console de exemplo básico</span><span class="sxs-lookup"><span data-stu-id="ce3e5-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="ce3e5-162">Aplicativo de C# console de exemplo estendido</span><span class="sxs-lookup"><span data-stu-id="ce3e5-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="ce3e5-163">Observação em controladores 6-DOF</span><span class="sxs-lookup"><span data-stu-id="ce3e5-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="ce3e5-164">Antes de chamar qualquer propriedade em métodos em um controlador de 6 DOF simulado, você deve ativar o controlador.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="ce3e5-165">Não fazer isso resultará em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="ce3e5-166">A partir da atualização do Windows 10 de maio de 2019, os controladores 6 DOF simulados podem ser instalados e ativados definindo a propriedade status no objeto ISimulatedSixDofController como SimulatedSixDofControllerStatus. Active.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="ce3e5-167">Na atualização do Windows 10 de outubro de 2018 e anterior, você deve instalar separadamente um controlador de 6 DOF simulado primeiro chamando a ferramenta PerceptionSimulationDevice localizada na pasta \Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="ce3e5-168">O uso dessa ferramenta é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ce3e5-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="ce3e5-169">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="ce3e5-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="ce3e5-170">As ações com suporte são:</span><span class="sxs-lookup"><span data-stu-id="ce3e5-170">Supported actions are:</span></span>
* <span data-ttu-id="ce3e5-171">i = instalar</span><span class="sxs-lookup"><span data-stu-id="ce3e5-171">i = install</span></span>
* <span data-ttu-id="ce3e5-172">q = consulta</span><span class="sxs-lookup"><span data-stu-id="ce3e5-172">q = query</span></span>
* <span data-ttu-id="ce3e5-173">r = remover</span><span class="sxs-lookup"><span data-stu-id="ce3e5-173">r = remove</span></span>

<span data-ttu-id="ce3e5-174">As instâncias com suporte são:</span><span class="sxs-lookup"><span data-stu-id="ce3e5-174">Supported instances are:</span></span>
* <span data-ttu-id="ce3e5-175">1 = o controlador de 6 DOF à esquerda</span><span class="sxs-lookup"><span data-stu-id="ce3e5-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="ce3e5-176">2 = o controlador de 6 DOF à direita</span><span class="sxs-lookup"><span data-stu-id="ce3e5-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="ce3e5-177">O código de saída do processo indicará êxito (um valor de retorno zero) ou falha (um valor de retorno diferente de zero).</span><span class="sxs-lookup"><span data-stu-id="ce3e5-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="ce3e5-178">Ao usar a ação ' q ' para consultar se um controlador está ou não instalado, o valor de retorno será zero (0) se o controlador ainda não estiver instalado ou um (1) se o controlador estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="ce3e5-179">Ao remover um controlador na atualização do Windows 10 de outubro de 2018 ou anterior, defina seu status como off por meio da API primeiro e, em seguida, chame a ferramenta PerceptionSimulationDevice.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="ce3e5-180">Observe que essa ferramenta deve ser executada como administrador.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="ce3e5-181">Referência da API</span><span class="sxs-lookup"><span data-stu-id="ce3e5-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="ce3e5-182">Microsoft. PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="ce3e5-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="ce3e5-183">Descreve um tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="ce3e5-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="ce3e5-184">**Microsoft. PerceptionSimulation. SimulatedDeviceType. Reference**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="ce3e5-185">Um dispositivo de referência fictícia, o padrão para PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="ce3e5-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="ce3e5-186">Microsoft. PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="ce3e5-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="ce3e5-187">Descreve um modo de controlador de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="ce3e5-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="ce3e5-188">**Microsoft. PerceptionSimulation. HeadTrackerMode. Default**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="ce3e5-189">Rastreamento de cabeçalho padrão.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-189">Default Head Tracking.</span></span> <span data-ttu-id="ce3e5-190">Isso significa que o sistema pode selecionar o melhor modo de controle de cabeçalho com base nas condições de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="ce3e5-191">**Microsoft. PerceptionSimulation. HeadTrackerMode. Orientation**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="ce3e5-192">Controle de cabeçalho somente orientação.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="ce3e5-193">Isso significa que a posição controlada pode não ser confiável, e algumas funcionalidades dependentes da posição de cabeçalho podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="ce3e5-194">**Microsoft. PerceptionSimulation. HeadTrackerMode. Position**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="ce3e5-195">Acompanhamento da cabeça posicional.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-195">Positional Head Tracking.</span></span> <span data-ttu-id="ce3e5-196">Isso significa que a posição e a orientação da cabeça controlada são confiáveis</span><span class="sxs-lookup"><span data-stu-id="ce3e5-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="ce3e5-197">Microsoft. PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="ce3e5-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="ce3e5-198">Descreve um gesto simulado</span><span class="sxs-lookup"><span data-stu-id="ce3e5-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="ce3e5-199">**Microsoft. PerceptionSimulation. SimulatedGesture. None**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="ce3e5-200">Um valor de sentinela usado para indicar que não há gestos.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="ce3e5-201">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="ce3e5-202">Um gesto de dedo pressionado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-202">A finger pressed gesture.</span></span>

<span data-ttu-id="ce3e5-203">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="ce3e5-204">Um gesto de liberação de dedo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-204">A finger released gesture.</span></span>

<span data-ttu-id="ce3e5-205">**Microsoft. PerceptionSimulation. SimulatedGesture. Home**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="ce3e5-206">O gesto de residência/sistema.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-206">The home/system gesture.</span></span>

<span data-ttu-id="ce3e5-207">**Microsoft. PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="ce3e5-208">O gesto máximo válido.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="ce3e5-209">Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="ce3e5-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="ce3e5-210">Os Estados possíveis de um controlador de 6 DOF simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="ce3e5-211">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. off**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="ce3e5-212">O controlador de 6 DOF está desligado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="ce3e5-213">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. active**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="ce3e5-214">O controlador de 6 DOF é ativado e acompanhado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="ce3e5-215">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="ce3e5-216">O controlador de 6 DOF está ativado, mas não pode ser acompanhado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="ce3e5-217">Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="ce3e5-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="ce3e5-218">Os botões com suporte em um controlador de 6 DOF simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="ce3e5-219">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. None**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="ce3e5-220">Um valor de sentinela usado para indicar nenhum botão.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="ce3e5-221">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Home**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="ce3e5-222">O botão página inicial é pressionado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-222">The Home button is pressed.</span></span>

<span data-ttu-id="ce3e5-223">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. menu**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="ce3e5-224">O botão de menu é pressionado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-224">The Menu button is pressed.</span></span>

<span data-ttu-id="ce3e5-225">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Segure**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="ce3e5-226">O botão de alça é pressionado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-226">The Grip button is pressed.</span></span>

<span data-ttu-id="ce3e5-227">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="ce3e5-228">O TouchPad é pressionado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="ce3e5-229">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="ce3e5-230">O botão Selecionar é pressionado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-230">The Select button is pressed.</span></span>

<span data-ttu-id="ce3e5-231">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="ce3e5-232">O TouchPad é tocado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-232">The TouchPad is touched.</span></span>

<span data-ttu-id="ce3e5-233">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="ce3e5-234">O Thumbstick é pressionado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="ce3e5-235">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="ce3e5-236">O botão máximo válido.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="ce3e5-237">Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="ce3e5-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="ce3e5-238">O estado de calibragem dos olhos simulados</span><span class="sxs-lookup"><span data-stu-id="ce3e5-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="ce3e5-239">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. indisponível**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="ce3e5-240">A calibragem de olhos não está disponível.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="ce3e5-241">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Ready**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="ce3e5-242">Os olhos foram calibrados.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="ce3e5-243">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-243">This is the default value.</span></span>

<span data-ttu-id="ce3e5-244">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Configurando**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="ce3e5-245">Os olhos estão sendo calibrados.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="ce3e5-246">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="ce3e5-247">Os olhos precisam ser calibrados.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="ce3e5-248">Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="ce3e5-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="ce3e5-249">A precisão de rastreamento de um conjunto de mãos.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="ce3e5-250">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. indisponível**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="ce3e5-251">A junção não é rastreada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-251">The joint is not tracked.</span></span>

<span data-ttu-id="ce3e5-252">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. aproximado**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="ce3e5-253">A posição conjunta é inferida.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-253">The joint position is inferred.</span></span>

<span data-ttu-id="ce3e5-254">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. Visible**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="ce3e5-255">A junção é totalmente controlada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="ce3e5-256">Microsoft. PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="ce3e5-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="ce3e5-257">A precisão de rastreamento de um conjunto de mãos.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="ce3e5-258">**Microsoft. PerceptionSimulation. SimulatedHandPose. Closed**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="ce3e5-259">As junções de dedo da mão são configuradas para refletir uma pose fechada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="ce3e5-260">**Microsoft. PerceptionSimulation. SimulatedHandPose. Open**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="ce3e5-261">As junções de dedo da mão são configuradas para refletir uma pose aberta.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="ce3e5-262">**Microsoft. PerceptionSimulation. SimulatedHandPose. Point**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="ce3e5-263">As junções de dedo da mão são configuradas para refletir uma pose de apontador.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="ce3e5-264">**Microsoft. PerceptionSimulation. SimulatedHandPose. pinçar**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="ce3e5-265">As junções de dedo da mão são configuradas para refletir uma pose de pinçagem.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="ce3e5-266">**Microsoft. PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="ce3e5-267">O valor máximo válido para SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="ce3e5-268">Microsoft. PerceptionSimulation. Playbackstate</span><span class="sxs-lookup"><span data-stu-id="ce3e5-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="ce3e5-269">Descreve o estado de uma reprodução.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="ce3e5-270">**Microsoft. PerceptionSimulation. Playbackstate. parado**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="ce3e5-271">A gravação está atualmente parada e pronta para reprodução.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="ce3e5-272">**Microsoft. PerceptionSimulation. Playbackstate. reproduzindo**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="ce3e5-273">A gravação está sendo executada no momento.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-273">The recording is currently playing.</span></span>

<span data-ttu-id="ce3e5-274">**Microsoft. PerceptionSimulation. Playbackstate. Paused**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="ce3e5-275">A gravação está em pausa no momento.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-275">The recording is currently paused.</span></span>

<span data-ttu-id="ce3e5-276">**Microsoft. PerceptionSimulation. Playbackstate. end**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="ce3e5-277">A gravação atingiu o final.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="ce3e5-278">Microsoft. PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="ce3e5-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="ce3e5-279">Descreve um vetor de 3 componentes, que pode descrever um ponto ou um vetor no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="ce3e5-280">**Microsoft. PerceptionSimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="ce3e5-281">O componente X do vetor.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-281">The X component of the vector.</span></span>

<span data-ttu-id="ce3e5-282">**Microsoft. PerceptionSimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="ce3e5-283">O componente Y do vetor.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-283">The Y component of the vector.</span></span>

<span data-ttu-id="ce3e5-284">**Microsoft. PerceptionSimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="ce3e5-285">O componente Z do vetor.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-285">The Z component of the vector.</span></span>

<span data-ttu-id="ce3e5-286">**Microsoft. PerceptionSimulation. Vector3. #ctor (System. single, System. single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="ce3e5-287">Construa um novo Vector3.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-287">Construct a new Vector3.</span></span>

<span data-ttu-id="ce3e5-288">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-288">Parameters</span></span>
* <span data-ttu-id="ce3e5-289">x – o componente x do vetor.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="ce3e5-290">y-o componente y do vetor.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="ce3e5-291">z-o componente z do vetor.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="ce3e5-292">Microsoft. PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="ce3e5-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="ce3e5-293">Descreve uma rotação de 3 componentes.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="ce3e5-294">**Microsoft. PerceptionSimulation. Rotation3. pitch**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="ce3e5-295">O componente de pitch da rotação, em volta do eixo X.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="ce3e5-296">**Microsoft. PerceptionSimulation. Rotation3. Guinad**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="ce3e5-297">O componente de guinada da rotação, logo em volta do eixo Y.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="ce3e5-298">**Microsoft. PerceptionSimulation. Rotation3. roll**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="ce3e5-299">O componente de roll da rotação, logo em volta do eixo Z.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="ce3e5-300">**Microsoft. PerceptionSimulation. Rotation3. #ctor (System. single, System. single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="ce3e5-301">Construa um novo Rotation3.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="ce3e5-302">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-302">Parameters</span></span>
* <span data-ttu-id="ce3e5-303">Pitch-o componente de pitch da rotação.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="ce3e5-304">guinada-o componente de guinada da rotação.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="ce3e5-305">roll-o componente de rolagem da rotação.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="ce3e5-306">Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce3e5-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="ce3e5-307">Descreve a configuração de uma junção em uma mão simulada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="ce3e5-308">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="ce3e5-309">A posição da junção.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-309">The position of the joint.</span></span>

<span data-ttu-id="ce3e5-310">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Rotation**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="ce3e5-311">A rotação da junção.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-311">The rotation of the joint.</span></span>

<span data-ttu-id="ce3e5-312">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="ce3e5-313">A precisão de rastreamento da junção.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="ce3e5-314">Microsoft. PerceptionSimulation. frustum</span><span class="sxs-lookup"><span data-stu-id="ce3e5-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="ce3e5-315">Descreve um frustum de exibição, como normalmente usado por uma câmera.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="ce3e5-316">**Microsoft. PerceptionSimulation. frustum. near**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="ce3e5-317">A distância mínima que está contida no frustum.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="ce3e5-318">**Microsoft. PerceptionSimulation. frustum. far**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="ce3e5-319">A distância máxima que está contida no frustum.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="ce3e5-320">**Microsoft. PerceptionSimulation. frustum. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="ce3e5-321">O campo horizontal de exibição do frustum, em radianos (menor que PI).</span><span class="sxs-lookup"><span data-stu-id="ce3e5-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="ce3e5-322">**Microsoft. PerceptionSimulation. frustum. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="ce3e5-323">A proporção do campo horizontal de exibição para o campo vertical da exibição.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="ce3e5-324">Microsoft. PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="ce3e5-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="ce3e5-325">Raiz para gerar os pacotes usados para controlar um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="ce3e5-326">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Device**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="ce3e5-327">Recupere o objeto de dispositivo simulado que interpreta o humano simulado e o mundo simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="ce3e5-328">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Human**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="ce3e5-329">Recupere o objeto que controla o humano simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="ce3e5-330">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Reset**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="ce3e5-331">Redefine a simulação para seu estado padrão.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="ce3e5-332">Microsoft. PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="ce3e5-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="ce3e5-333">Interface que descreve o dispositivo que interpreta o mundo simulado e o humano simulado</span><span class="sxs-lookup"><span data-stu-id="ce3e5-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="ce3e5-334">**Microsoft. PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="ce3e5-335">Recupere o controlador de cabeçalho do dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="ce3e5-336">**Microsoft. PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="ce3e5-337">Recupere o rastreador de mão do dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="ce3e5-338">**Microsoft. PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="ce3e5-339">Defina as propriedades do dispositivo simulado para corresponder ao tipo de dispositivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="ce3e5-340">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-340">Parameters</span></span>
* <span data-ttu-id="ce3e5-341">tipo – o novo tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="ce3e5-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="ce3e5-342">Microsoft. PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="ce3e5-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="ce3e5-343">Interface que descreve a parte do dispositivo simulado que controla o início do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="ce3e5-344">**Microsoft. PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="ce3e5-345">Recupera e define o modo de controlador de cabeçalho atual.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="ce3e5-346">Microsoft. PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="ce3e5-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="ce3e5-347">Interface que descreve a parte do dispositivo simulado que controla as mãos do humano simulado</span><span class="sxs-lookup"><span data-stu-id="ce3e5-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="ce3e5-348">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="ce3e5-349">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="ce3e5-350">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Position**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="ce3e5-351">Recupere e defina a posição do controlador de mão simulado em relação ao centro do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="ce3e5-352">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. pitch**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="ce3e5-353">Recupere e defina o timbre inferior do controlador de mão simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="ce3e5-354">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="ce3e5-355">Recupere e defina se a frustum do controlador de mão simulado é ignorada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="ce3e5-356">Quando ignorado, ambas as mãos estão sempre visíveis.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="ce3e5-357">Quando não ignoradas (as mãos padrão) ficam visíveis apenas quando estão dentro do frustum do rastreador.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="ce3e5-358">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. frustum**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="ce3e5-359">Recupere e defina as propriedades frustum usadas para determinar se as mãos estão visíveis para o controlador de mão simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="ce3e5-360">Microsoft. PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="ce3e5-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="ce3e5-361">Interface de nível superior para controlar o humano simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="ce3e5-362">**Microsoft. PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="ce3e5-363">Recupere e defina a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="ce3e5-364">A posição corresponde a um ponto no centro dos pés humanos.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="ce3e5-365">**Microsoft. PerceptionSimulation. ISimulatedHuman. Direction**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="ce3e5-366">Recupere e defina a direção das faces humanas simuladas do mundo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="ce3e5-367">0 radianos está voltado para baixo no eixo Z negativo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="ce3e5-368">Radianos positivos giram no sentido horário sobre o eixo Y.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="ce3e5-369">**Microsoft. PerceptionSimulation. ISimulatedHuman. Height**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="ce3e5-370">Recupere e defina a altura do humano simulado, em metros.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="ce3e5-371">**Microsoft. PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="ce3e5-372">Recupere o lado esquerdo do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="ce3e5-373">**Microsoft. PerceptionSimulation. ISimulatedHuman. RightHand**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="ce3e5-374">Recupere o lado direito do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="ce3e5-375">**Microsoft. PerceptionSimulation. ISimulatedHuman. Head**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="ce3e5-376">Recupere o cabeçalho do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="ce3e5-377">**Microsoft. PerceptionSimulation. ISimulatedHuman. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="ce3e5-378">Mova o humano simulado relativo à sua posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="ce3e5-379">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-379">Parameters</span></span>
* <span data-ttu-id="ce3e5-380">translação-a tradução a ser movida, relativa à posição atual.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="ce3e5-381">**Microsoft. PerceptionSimulation. ISimulatedHuman. Rotate (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="ce3e5-382">Girar o humano simulado em relação à sua direção atual, no sentido horário, sobre o eixo Y</span><span class="sxs-lookup"><span data-stu-id="ce3e5-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="ce3e5-383">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-383">Parameters</span></span>
* <span data-ttu-id="ce3e5-384">radianos-o valor a ser girado em volta do eixo Y.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="ce3e5-385">Microsoft. PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="ce3e5-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="ce3e5-386">Propriedades adicionais estão disponíveis por meio da conversão de ISimulatedHuman para ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="ce3e5-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="ce3e5-387">**Microsoft. PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="ce3e5-388">Recupere o controlador esquerdo 6-DOF.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="ce3e5-389">**Microsoft. PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="ce3e5-390">Recupere o controlador de 6 DOF à direita.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="ce3e5-391">Microsoft. PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="ce3e5-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="ce3e5-392">Interface que descreve uma mão do humano simulado</span><span class="sxs-lookup"><span data-stu-id="ce3e5-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="ce3e5-393">**Microsoft. PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="ce3e5-394">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="ce3e5-395">**Microsoft. PerceptionSimulation. ISimulatedHand. Position**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="ce3e5-396">Recupere e defina a posição da mão simulada em relação ao humano, em metros.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="ce3e5-397">**Microsoft. PerceptionSimulation. ISimulatedHand. Activated**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="ce3e5-398">Recuperar e definir se a mão está ativada no momento.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="ce3e5-399">**Microsoft. PerceptionSimulation. ISimulatedHand. Visible**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="ce3e5-400">Recupere se a mão está visível no momento para o SimulatedDevice (ou seja, se está em uma posição a ser detectada pelo HandTracker).</span><span class="sxs-lookup"><span data-stu-id="ce3e5-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="ce3e5-401">**Microsoft. PerceptionSimulation. ISimulatedHand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="ce3e5-402">Mova a mão de modo que fique visível para o SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="ce3e5-403">**Microsoft. PerceptionSimulation. ISimulatedHand. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="ce3e5-404">Mova a posição da mão simulada em relação à sua posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="ce3e5-405">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-405">Parameters</span></span>
* <span data-ttu-id="ce3e5-406">translation-o valor para converter a mão simulada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="ce3e5-407">**Microsoft. PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="ce3e5-408">Execute um gesto usando a mão simulada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="ce3e5-409">Ele só será detectado pelo sistema se a mão estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="ce3e5-410">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-410">Parameters</span></span>
* <span data-ttu-id="ce3e5-411">gesto-o gesto a ser executado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="ce3e5-412">Microsoft. PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="ce3e5-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="ce3e5-413">Propriedades adicionais estão disponíveis por meio da conversão de um ISimulatedHand em ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="ce3e5-414">**Microsoft. PerceptionSimulation. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="ce3e5-415">Recupere ou defina a rotação da mão simulada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="ce3e5-416">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="ce3e5-417">Microsoft. PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="ce3e5-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="ce3e5-418">Propriedades adicionais estão disponíveis por meio da conversão de um ISimulatedHand para ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="ce3e5-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="ce3e5-419">**Microsoft. PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="ce3e5-420">Obter a configuração conjunta para a junção especificada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="ce3e5-421">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="ce3e5-422">Defina a configuração conjunta para a junção especificada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="ce3e5-423">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="ce3e5-424">Defina a mão como uma pose conhecida com um sinalizador opcional para animar.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="ce3e5-425">Observação: a animação não resultará em junções imediatamente refletindo suas configurações de conjuntos finais.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="ce3e5-426">Microsoft. PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="ce3e5-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="ce3e5-427">Interface que descreve o cabeçalho do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="ce3e5-428">**Microsoft. PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="ce3e5-429">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="ce3e5-430">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotation**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="ce3e5-431">Recupere a rotação da cabeça simulada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="ce3e5-432">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="ce3e5-433">**Microsoft. PerceptionSimulation. ISimulatedHead. diâmetro**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="ce3e5-434">Recupere o diâmetro da cabeça simulada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="ce3e5-435">Esse valor é usado para determinar o centro da cabeça (ponto de rotação).</span><span class="sxs-lookup"><span data-stu-id="ce3e5-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="ce3e5-436">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="ce3e5-437">Girar a cabeça simulada em relação à sua rotação atual.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="ce3e5-438">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="ce3e5-439">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-439">Parameters</span></span>
* <span data-ttu-id="ce3e5-440">rotação-o valor a ser girado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="ce3e5-441">Microsoft. PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="ce3e5-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="ce3e5-442">Propriedades adicionais estão disponíveis por meio da conversão de um ISimulatedHead para ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="ce3e5-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="ce3e5-443">**Microsoft. PerceptionSimulation. ISimulatedHead2. eyess**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="ce3e5-444">Recupere os olhos do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="ce3e5-445">Microsoft. PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="ce3e5-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="ce3e5-446">Interface que descreve um controlador de 6 DOF associado ao humano simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="ce3e5-447">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="ce3e5-448">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="ce3e5-449">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. status**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="ce3e5-450">Recupere ou defina o estado atual do controlador.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="ce3e5-451">O status do controlador deve ser definido com um valor diferente de desativado antes que as chamadas para mover, girar ou pressionar botões tenham sucesso.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="ce3e5-452">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Position**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="ce3e5-453">Recupere ou defina a posição do controlador simulado em relação ao humano, em metros.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="ce3e5-454">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Orientation**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="ce3e5-455">Recupere ou defina a orientação do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="ce3e5-456">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="ce3e5-457">Mova a posição do controlador simulado em relação à sua posição atual, em metros.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="ce3e5-458">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-458">Parameters</span></span>
* <span data-ttu-id="ce3e5-459">translation-o valor para converter o controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="ce3e5-460">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="ce3e5-461">Pressione um botão no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="ce3e5-462">Ele só será detectado pelo sistema se o controlador estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="ce3e5-463">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-463">Parameters</span></span>
* <span data-ttu-id="ce3e5-464">botão-o botão para pressionar.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-464">button - The button to press.</span></span>

<span data-ttu-id="ce3e5-465">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="ce3e5-466">Libere um botão no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="ce3e5-467">Ele só será detectado pelo sistema se o controlador estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="ce3e5-468">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-468">Parameters</span></span>
* <span data-ttu-id="ce3e5-469">botão-o botão a ser liberado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-469">button - The button to release.</span></span>

<span data-ttu-id="ce3e5-470">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="ce3e5-471">Obtenha a posição de um dedo simulado no Touchpad do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="ce3e5-472">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-472">Parameters</span></span>
* <span data-ttu-id="ce3e5-473">x-a posição horizontal do dedo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="ce3e5-474">y-a posição vertical do dedo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="ce3e5-475">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="ce3e5-476">Defina a posição de um dedo simulado no Touchpad do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="ce3e5-477">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-477">Parameters</span></span>
* <span data-ttu-id="ce3e5-478">x-a posição horizontal do dedo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="ce3e5-479">y-a posição vertical do dedo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="ce3e5-480">Microsoft. PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="ce3e5-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="ce3e5-481">Propriedades e métodos adicionais estão disponíveis por meio da conversão de um ISimulatedSixDofController para ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="ce3e5-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="ce3e5-482">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="ce3e5-483">Obtém a posição do Thumbstick simulado no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="ce3e5-484">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-484">Parameters</span></span>
* <span data-ttu-id="ce3e5-485">x-a posição horizontal do Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="ce3e5-486">y-a posição vertical do Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="ce3e5-487">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="ce3e5-488">Defina a posição do Thumbstick simulado no controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="ce3e5-489">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-489">Parameters</span></span>
* <span data-ttu-id="ce3e5-490">x-a posição horizontal do Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="ce3e5-491">y-a posição vertical do Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="ce3e5-492">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="ce3e5-493">Recupere ou defina o nível de bateria do controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="ce3e5-494">O valor deve ser maior que 0,0 e menor ou igual a 100,0.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="ce3e5-495">Microsoft. PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="ce3e5-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="ce3e5-496">Interface que descreve os olhos do humano simulado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="ce3e5-497">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotation**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="ce3e5-498">Recupere a rotação dos olhos simulados.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="ce3e5-499">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="ce3e5-500">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="ce3e5-501">Gire os olhos simulados em relação à sua rotação atual.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="ce3e5-502">Radianos positivos giram no sentido horário ao olhar ao longo do eixo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="ce3e5-503">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-503">Parameters</span></span>
* <span data-ttu-id="ce3e5-504">rotação-o valor a ser girado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="ce3e5-505">**Microsoft. PerceptionSimulation. ISimulatedEyes. calibrable**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="ce3e5-506">Recupera ou define o estado de calibragem dos olhos simulados.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="ce3e5-507">**Microsoft. PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="ce3e5-508">Recupere a posição do nó com relação ao mundo, em metros.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="ce3e5-509">Microsoft. PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="ce3e5-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="ce3e5-510">Interface para interagir com uma única gravação carregada para reprodução.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="ce3e5-511">**Microsoft. PerceptionSimulation. ISimulationRecording. datatipos**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="ce3e5-512">Recupera a lista de tipos de dados na gravação.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="ce3e5-513">**Microsoft. PerceptionSimulation. ISimulationRecording. State**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="ce3e5-514">Recupera o estado atual da gravação.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="ce3e5-515">**Microsoft. PerceptionSimulation. ISimulationRecording. Play**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="ce3e5-516">Inicie a reprodução.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-516">Start the playback.</span></span> <span data-ttu-id="ce3e5-517">Se a gravação for pausada, a reprodução será retomada do local em pausa; Se for interrompido, a reprodução será iniciada no início.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="ce3e5-518">Se já estiver em execução, essa chamada será ignorada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="ce3e5-519">**Microsoft. PerceptionSimulation. ISimulationRecording. Pause**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="ce3e5-520">Pausa a reprodução em seu local atual.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="ce3e5-521">Se a gravação for interrompida, a chamada será ignorada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="ce3e5-522">**Microsoft. PerceptionSimulation. ISimulationRecording. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="ce3e5-523">Procura a gravação no tempo especificado (em intervalos de 100 nanossegundos desde o início) e pausa nesse local.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="ce3e5-524">Se o tempo estiver além do fim da gravação, ele será pausado no último quadro.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="ce3e5-525">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-525">Parameters</span></span>
* <span data-ttu-id="ce3e5-526">tiques-o tempo para o qual buscar.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="ce3e5-527">**Microsoft. PerceptionSimulation. ISimulationRecording. Stop**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="ce3e5-528">Interrompe a reprodução e redefine a posição para o início.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="ce3e5-529">Microsoft. PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="ce3e5-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="ce3e5-530">Interface para receber alterações de estado durante a reprodução.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="ce3e5-531">**Microsoft. PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. reproduzstate)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="ce3e5-532">Chamado quando o estado de reprodução de um ISimulationRecording é alterado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="ce3e5-533">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-533">Parameters</span></span>
* <span data-ttu-id="ce3e5-534">newState – o novo estado da gravação.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="ce3e5-535">Microsoft. PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="ce3e5-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="ce3e5-536">Objeto raiz para criar objetos de simulação de percepção.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="ce3e5-537">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="ce3e5-538">Crie um objeto para gerar pacotes simulados e fornecê-los ao coletor fornecido.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="ce3e5-539">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-539">Parameters</span></span>
* <span data-ttu-id="ce3e5-540">coletor-o coletor que receberá todos os pacotes gerados.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="ce3e5-541">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="ce3e5-541">Return value</span></span>

<span data-ttu-id="ce3e5-542">O gerente criado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-542">The created Manager.</span></span>

<span data-ttu-id="ce3e5-543">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System. String)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="ce3e5-544">Crie um coletor que armazena todos os pacotes recebidos em um arquivo no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="ce3e5-545">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-545">Parameters</span></span>
* <span data-ttu-id="ce3e5-546">caminho-o caminho do arquivo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-546">path - The path of the file to create.</span></span>

<span data-ttu-id="ce3e5-547">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="ce3e5-547">Return value</span></span>

<span data-ttu-id="ce3e5-548">O coletor criado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-548">The created sink.</span></span>

<span data-ttu-id="ce3e5-549">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="ce3e5-550">Carregar uma gravação do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="ce3e5-551">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-551">Parameters</span></span>
* <span data-ttu-id="ce3e5-552">caminho-o caminho do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="ce3e5-553">Factory-uma fábrica usada pela gravação para criar um ISimulationStreamSink quando necessário.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="ce3e5-554">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="ce3e5-554">Return value</span></span>

<span data-ttu-id="ce3e5-555">A gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-555">The loaded recording.</span></span>

<span data-ttu-id="ce3e5-556">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="ce3e5-557">Carregar uma gravação do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="ce3e5-558">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-558">Parameters</span></span>
* <span data-ttu-id="ce3e5-559">caminho-o caminho do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="ce3e5-560">Factory-uma fábrica usada pela gravação para criar um ISimulationStreamSink quando necessário.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="ce3e5-561">retorno de chamada-um retorno de chamada que recebe atualizações que recebem o status da gravação.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="ce3e5-562">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="ce3e5-562">Return value</span></span>

<span data-ttu-id="ce3e5-563">A gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="ce3e5-564">Microsoft. PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="ce3e5-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="ce3e5-565">Descreve os diferentes tipos de dados de fluxo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="ce3e5-566">**Microsoft. PerceptionSimulation. StreamDataTypes. None**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="ce3e5-567">Um valor de sentinela usado para indicar nenhum tipo de dados de fluxo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="ce3e5-568">**Microsoft. PerceptionSimulation. StreamDataTypes. Head**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="ce3e5-569">Fluxo de dados em relação à posição e à orientação do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="ce3e5-570">**Microsoft. PerceptionSimulation. StreamDataTypes. hands**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="ce3e5-571">Fluxo de dados em relação à posição e aos gestos de mãos.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="ce3e5-572">**Microsoft. PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="ce3e5-573">Fluxo de dados referente ao mapeamento espacial do ambiente.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="ce3e5-574">**Microsoft. PerceptionSimulation. StreamDataTypes. Calibration**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="ce3e5-575">Fluxo de dados referente à calibragem do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="ce3e5-576">Os pacotes de calibragem são aceitos apenas por um sistema no modo remoto.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="ce3e5-577">**Microsoft. PerceptionSimulation. StreamDataTypes. Environment**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="ce3e5-578">Fluxo de dados em relação ao ambiente do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="ce3e5-579">**Microsoft. PerceptionSimulation. StreamDataTypes. All**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="ce3e5-580">Um valor de sentinela usado para indicar todos os tipos de dados gravados.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="ce3e5-581">Microsoft. PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="ce3e5-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="ce3e5-582">Um objeto que recebe pacotes de dados de um fluxo de simulação.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="ce3e5-583">**Microsoft. PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (pacote de comprimento uint, Byte [])**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="ce3e5-584">Recebe um único pacote, que é digitado internamente e com controle de versão.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="ce3e5-585">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce3e5-585">Parameters</span></span>
* <span data-ttu-id="ce3e5-586">comprimento-o comprimento do pacote.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-586">length - The length of the packet.</span></span>
* <span data-ttu-id="ce3e5-587">pacote-os dados do pacote.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="ce3e5-588">Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="ce3e5-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="ce3e5-589">Um objeto que cria ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="ce3e5-590">**Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**</span><span class="sxs-lookup"><span data-stu-id="ce3e5-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="ce3e5-591">Cria uma única instância de ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="ce3e5-592">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="ce3e5-592">Return value</span></span>

<span data-ttu-id="ce3e5-593">O coletor criado.</span><span class="sxs-lookup"><span data-stu-id="ce3e5-593">The created sink.</span></span>
