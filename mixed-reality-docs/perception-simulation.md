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
# <a name="perception-simulation"></a>Simulação de percepção

Você deseja criar um teste automatizado para seu aplicativo? Você deseja que seus testes ir além dos testes de unidade de nível de componente e realmente exercitar seu aplicativo ponta a ponta? Simulação de percepção é o que você está procurando. A biblioteca de simulação de percepção envia falsos humanos e dados de entrada do mundo para seu aplicativo para que você possa automatizar seus testes. Por exemplo, você pode simular a entrada de um humano procurando esquerda e direita e, em seguida, executar um gesto.

Simulação de percepção pode enviar entrada simulada como esta para um HoloLens físico, o emulador do HoloLens ou um PC com o Portal de realidade misturada instalado. Percepção de simulação ignora os sensores em tempo real em um dispositivo de realidade mista e envia simulados de entrada para aplicativos em execução no dispositivo. Aplicativos recebem esses eventos de entrada fictícios por meio das mesmas APIs que eles sempre usam e que não é possível determinar a diferença entre a execução com sensores reais versus executando com simulação de percepção. Simulação de percepção é a mesma tecnologia usada pelo emulador do HoloLens enviem dados de entrada para a máquina Virtual HoloLens simulado.

Simulação começa criando um objeto IPerceptionSimulationManager. A partir desse objeto, você pode emitir comandos para controlar propriedades de um simulado "humana", incluindo posição principal, a posição de mão e gestos.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Como configurar um projeto do Visual Studio para a percepção de simulação
1. [Instalar o emulador do HoloLens](install-the-tools.md) em seu computador de desenvolvimento. O emulador inclui as bibliotecas que você usará para a simulação de percepção.
2. Criar um novo Visual Studio C# projeto da área de trabalho (um projeto de Console funciona muito bem de começar a usar).
3. Adicione os seguintes binários ao seu projeto como referências (projeto -> Adicionar -> referência...). Você pode encontrá-los no **% ProgramFiles (x86) %\Microsoft XDE\10.0.11082.0** um. PerceptionSimulationManager.Interop.dll - gerenciados C# wrapper para a simulação de percepção.
    b. PerceptionSimulationRest.dll - Library para configurar um canal de comunicação de soquete da web para o HoloLens ou emulador.
    c. SimulationStream.Interop.dll - tipos compartilhados para simulação.
4. Adicione a implementação PerceptionSimulationManager.dll binário ao seu projeto de um. Primeiro adicioná-lo como um binário para o projeto (Project -> Adicionar -> Item existente...). Salve-o como um link para que ele não copie-o para sua pasta de origem do projeto. ![Adicionar PerceptionSimulationManager.dll ao projeto como um link](images/saveaslink.png) b. Em seguida, certifique-se de que ele obtenha do copiado para a pasta de saída no build. Isso é na folha de propriedades para o binário. ![Marcar PerceptionSimulationManager.dll para copiar para diretório de saída](images/copyalways.png)

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Criar um objeto do Gerenciador de IPerceptionSimulation

Para controlar a simulação, você vai emitir atualizações para objetos recuperados de um objeto IPerceptionSimulationManager. A primeira etapa é obter esse objeto e conectá-lo ao seu dispositivo de destino ou o emulador. Você pode obter o endereço IP do seu emulador clicando no botão no Portal do dispositivo o [barra de ferramentas](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)

![Ícone do Portal do dispositivo aberto](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: Abra o Windows Device Portal para o sistema de operacional HoloLens no emulador.

Primeiro, você chamará RestSimulationStreamSink.Create para obter um objeto RestSimulationStreamSink. Esse é o dispositivo de destino ou o emulador que você irá controlar ao longo de uma conexão http. Serão passados para seus comandos e tratados pelos [Windows Device Portal](using-the-windows-device-portal.md) em execução no dispositivo ou emulador. Os quatro parâmetros, que você precisará criar um objeto são:
* Uri de URI - endereço IP do dispositivo de destino (por exemplo, "http://123.123.123.123")
* System.Net.NetworkCredential credenciais - nome de usuário e senha para conexão com o [Windows Device Portal](using-the-windows-device-portal.md) no emulador ou dispositivo de destino. Se você estiver se conectando ao emulador por meio de seu local 168. *.* . * endereço no mesmo computador, todas as credenciais serão aceitas.
* bool normal - True para false para baixa prioridade com prioridade normal. Geralmente, é recomendável definir isso como *verdadeira* para cenários de teste.
* Token cancellationtoken - Token para cancelar a operação assíncrona.

Em segundo lugar, você criará o IPerceptionSimulationManager. Esse é o objeto que você pode usar para controlar a simulação. Observe que isso também deve ser feito em um método assíncrono.

## <a name="control-the-simulated-human"></a>Controle o ser humano simulado

Um IPerceptionSimulationManager tem uma propriedade humana que retorna um objeto ISimulatedHuman. Para controlar o ser humano simulado, execute operações nesse objeto. Por exemplo: 

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Exemplo básico C# aplicativo de console

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

## <a name="extended-sample-c-console-application"></a>Estendida de exemplo C# aplicativo de console

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

## <a name="api-reference"></a>Referência da API

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft.PerceptionSimulation.SimulatedDeviceType

Descreve um tipo de dispositivo simulado

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**

Um dispositivo de referência fictícia, o padrão para PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft.PerceptionSimulation.HeadTrackerMode

Descreve um modo de rastreador principal

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**

Padrão de controle de cabeçalho. Isso significa que o sistema pode selecionar o melhor head com base em condições de tempo de execução do modo de controle.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**

Orientação de acompanhamento somente cabeçalho. Isso significa que a posição controlada pode não ser confiável, e alguma funcionalidade dependente de posição principal pode não estar disponível.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**

Controle de cabeçalho posicionais. Isso significa que a posição de cabeçalho controlada e orientação são confiáveis

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft.PerceptionSimulation.SimulatedGesture

Descreve um gesto simulado

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

**Microsoft.PerceptionSimulation.SimulatedGesture.None**

Um valor de sentinela usado para não indicar nenhum gestos

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

Um dedo pressionado gesto

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

Um gesto de dedo lançado

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

O gesto de base

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

O gesto válido máximo

### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

Descreve o estado de uma reprodução

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft.PerceptionSimulation.PlaybackState.Stopped**

A gravação está atualmente parado e pronto para reprodução

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

A gravação está em execução no momento

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

A gravação estiver em pausa

**Microsoft.PerceptionSimulation.PlaybackState.End**

A gravação atingiu o fim

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

Descreve um vetor de 3 componentes, que pode descrever um ponto ou um vetor no espaço 3D

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft.PerceptionSimulation.Vector3.X**

O componente X do vetor

**Microsoft.PerceptionSimulation.Vector3.Y**

O componente Y do vetor

**Microsoft.PerceptionSimulation.Vector3.Z**

O componente Z do vetor

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**

Construir um novo Vector3

Parâmetros
* x - o componente x do vetor
* y - o componente y do vetor
* z - o componente z do vetor

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

Descreve uma rotação de 3 componentes

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft.PerceptionSimulation.Rotation3.Pitch**

O componente de tom de rotação, faz uma busca em torno do eixo X

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

O componente do desvio da rotação em torno do eixo Y

**Microsoft.PerceptionSimulation.Rotation3.Roll**

O componente de distribuição da rotação em torno do eixo Z

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**

Construir um novo Rotation3

Parâmetros
* Tom - o componente de tom de rotação
* yaw - o componente do desvio da rotação
* roll - o componente de distribuição de rotação

### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

Descreve um frustum do modo de exibição, como normalmente usada por uma câmera

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft.PerceptionSimulation.Frustum.Near**

A distância mínima que está contida no frustum

**Microsoft.PerceptionSimulation.Frustum.Far**

A distância máxima que está contida no frustum

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

O campo de exibição horizontal de frustum, em radianos (menor que o PI)

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

A proporção de campo de exibição horizontal para o campo de exibição vertical

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

Raiz para gerar os pacotes usados para controlar um dispositivo

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**

Recupere o objeto de dispositivo simulado que interpreta o ser humano simulado e o mundo simulado.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**

Recupere o objeto que controla o ser humano simulado.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**

Redefine a simulação para seu estado padrão.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft.PerceptionSimulation.ISimulatedDevice

Interface que descreve o dispositivo que interpreta o mundo simulado e o ser humano simulado

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**

Recupere a posição da cabeça do dispositivo simulado.

**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**

Recupere o rastreador de mão do dispositivo simulado.

**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**

Defina as propriedades do dispositivo simulado para corresponder ao tipo de dispositivo fornecido.

Parâmetros
* Digite - o novo tipo de dispositivo simulado

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHeadTracker

Interface que descreve a parte do dispositivo simulado que rastreia o cabeçalho do ser humano simulado

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**

Recupera e define o modo atual do controlador principal.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHandTracker

Interface que descreve a parte do dispositivo simulado que rastreia as mãos do ser humano simulado

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

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**

Recuperar a posição do nó com relação ao mundo, em metros

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

Recuperar e definir a posição do controlador mão simulado, em relação ao centro do cabeçalho.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

Recuperar e definir o tom para baixo do controlador mão simulado

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

Recuperar e definir se o frustum do controlador mão simulado é ignorado. Quando ignoradas, ambas as mãos estão sempre visíveis. Quando não ignoradas (padrão) mãos são visíveis apenas quando estes estiverem dentro a frustum do controlador disponível.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

Recuperar e definir as propriedades de frustum usadas para determinar se as mãos são visíveis para o rastreador de mão simulado.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

Interface de nível superior para controlar o ser humano simulado

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

**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**

Recuperar e definir a posição do nó com relação ao mundo, em metros. A posição corresponde a um ponto no Centro de metros do humanos.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**

Recuperar e definir a direção de faces humanas simuladas no mundo. 0 radianos faces para baixo do eixo Z negativo. Radianos positivos giram no sentido horário sobre o eixo Y.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**

Recuperar e definir a altura do ser humano simulado, em metros

**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**

Recuperar o lado esquerdo do ser humano simulado

**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**

Recuperar o direito do ser humano simulado

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

Recuperar o cabeçalho do ser humano simulado

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**

Mover o ser humano simulado em relação à posição atual, em metros

Parâmetros
* conversão - a tradução para mover em relação à posição atual

**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**

Girar o ser humano simulado em relação à sua direção atual, no sentido horário sobre o eixo Y

Parâmetros
* radianos - a quantidade de rotação ao redor do eixo Y

### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft.PerceptionSimulation.ISimulatedHand

Interface que descreve uma mão do ser humano simulado

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

**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**

Recuperar a posição do nó com relação ao mundo, em metros

**Microsoft.PerceptionSimulation.ISimulatedHand.Position**

Recuperar e definir a posição da mão simulado em relação ao ser humano, em metros.

**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**

Recuperar e definir se a mão está ativada no momento.

**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**

Recupere se a mão está atualmente visível para o SimulatedDevice (ou seja, seja em uma posição para ser detectada pelo HandTracker).

**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**

Mova a mão, que é visível para o SimulatedDevice.

**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**

Mova a posição da mão simulado em relação à posição atual, em metros.

Parâmetros
* tradução - o valor para converter a mão simulada

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

Execute um gesto usando a mão simulada (ela só será detectada pelo sistema se a mão estiver habilitada).

Parâmetros
* gesto - o gesto para executar

### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

Interface que descreve o cabeçalho do ser humano simulado

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**

Recuperar a posição do nó com relação ao mundo, em metros

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

Recupere a rotação da cabeça de simulado. Radianos girar no sentido horário ao procurar ao longo do eixo positivo.

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

Recupere o diâmetro da cabeça simulado. Esse valor é usado para determinar o centro do head (ponto de rotação).

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Gire o head simulado em relação à sua rotação atual. Radianos girar no sentido horário ao procurar ao longo do eixo positivo.

Parâmetros
* rotação - a quantidade de rotação

### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft.PerceptionSimulation.ISimulationRecording

Carregar a interface para interagir com uma única gravação para reprodução.

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

**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**

Recupera a lista de tipos de dados na gravação.

**Microsoft.PerceptionSimulation.ISimulationRecording.State**

Recupera o estado atual da gravação.

**Microsoft.PerceptionSimulation.ISimulationRecording.Play**

Inicie a reprodução. Se a gravação for pausada, a reprodução será retomada do local em pausa; Se interrompida, a reprodução será iniciada no início. Se já em execução, essa chamada é ignorada.

**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**

Pausa a reprodução em seu local atual. Se a gravação for interrompida, a chamada será ignorada.

**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**

Procura a gravação de tempo especificado (em intervalos de 100 nanossegundos desde o início) e faz uma pausa nesse local. Se o tempo está além do fim da gravação, ele está em pausa no último quadro.

Parâmetros
* tiques - o tempo para o qual a busca

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

Interrompe a reprodução e redefine a posição para o início

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

Interface para receber alterações de estado durante a reprodução

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

Chamado quando o estado de reprodução de um ISimulationRecording foi alterado

Parâmetros
* newState - o novo estado da gravação

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Objeto raiz para a criação de objetos de simulação de percepção

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**

Crie no objeto para gerar pacotes simulados e entregá-los para o coletor fornecido.

Parâmetros
* coletor - coletor que receberá os pacotes gerados

Retornar valor

O Gerenciador de criado

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

Crie um coletor que armazena os pacotes recebidos tudo em um arquivo no caminho especificado.

Parâmetros
* caminho - o caminho do arquivo a ser criado

Retornar valor

O coletor criado

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

Carregar uma gravação do arquivo especificado

Parâmetros
* caminho - o caminho do arquivo a ser carregado
* fábrica - um alocador usado pela gravação para a criação de um ISimulationStreamSink quando necessário

Retornar valor

A gravação carregada

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

Carregar uma gravação do arquivo especificado

Parâmetros
* caminho - o caminho do arquivo a ser carregado
* fábrica - um alocador usado pela gravação para a criação de um ISimulationStreamSink quando necessário
* atualizações de um retorno de chamada que recebe o retorno de chamada - regrading status da gravação

Retornar valor

A gravação carregada

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

Descreve os diferentes tipos de fluxo de dados

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

**Microsoft.PerceptionSimulation.StreamDataTypes.None**

Um valor de sentinela usado para não indicar nenhum tipo de dados de fluxo

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

Stream de dados em relação à posição e orientação do cabeçalho

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

Stream de dados em relação à posição e gestos de mãos

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

Stream de dados relativos ao mapeamento espacial do ambiente

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

Stream de dados em relação à calibragem do dispositivo. Pacotes de calibragem somente são aceitas por um sistema no modo remoto.

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

Stream de dados sobre o ambiente do dispositivo

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

Um valor de sentinela usado para indicar todos os tipos de dados gravados

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

Um objeto que recebe os pacotes de dados de um fluxo de simulação

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**

Recebe um único pacote, o que é internamente com tipo e com controle de versão

Parâmetros
* comprimento - o tamanho do pacote
* pacote - os dados do pacote

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

Um objeto que cria ISimulationStreamSink

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

Cria uma única instância de ISimulationStreamSink

Retornar valor

O coletor criado
