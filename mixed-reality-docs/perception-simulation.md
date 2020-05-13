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
# <a name="perception-simulation"></a>Simulação de percepção

Deseja criar um teste automatizado para seu aplicativo? Você deseja que seus testes vão além dos testes de unidade de nível de componente e realmente exercitam seu aplicativo de ponta a ponta? A simulação de percepção é o que você está procurando. A biblioteca de simulação de percepção envia dados de entrada humanos e mundiais para seu aplicativo para que você possa automatizar seus testes. Por exemplo, você pode simular a entrada de uma aparência humana para uma posição específica e repetível e, em seguida, executar um gesto ou usar um controlador de movimento.

A simulação de percepção pode enviar uma entrada simulada como esta para um HoloLens físico, o emulador do HoloLens (1º gen), o emulador do HoloLens 2 ou um PC com o portal de realidade misturada instalado. A simulação de percepção ignora os sensores ao vivo em um dispositivo de realidade misturada e envia a entrada simulada para aplicativos em execução no dispositivo. Os aplicativos recebem esses eventos de entrada por meio das mesmas APIs que sempre usam e não conseguem dizer a diferença entre a execução com sensores reais versus a execução com a simulação de percepção. A simulação de percepção é a mesma tecnologia usada pelos emuladores do HoloLens para enviar a entrada simulada para a máquina virtual do HoloLens.

Para começar a usar a simulação em seu código, comece criando um objeto IPerceptionSimulationManager. A partir desse objeto, você pode emitir comandos para controlar as propriedades de um "humano" simulado, incluindo posição de cabeçalho, posição mão e gestos, e você pode habilitar e manipular controladores de movimento.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Configurando um projeto do Visual Studio para simulação de percepção
1. [Instale o emulador do HoloLens](install-the-tools.md) no seu computador de desenvolvimento. O emulador inclui as bibliotecas que serão usadas para a simulação de percepção.
2. Crie um novo projeto de desktop do Visual Studio C# (um projeto de console funciona muito bem para começar).
3. Adicione os seguintes binários ao seu projeto como referências (projeto->referência ao suplemento de >...). Você pode encontrá-los em% ProgramFiles (x86)% \ Microsoft XDE \\ (versão), como **% ProgramFiles (x86)% \ Microsoft XDE \\ 10.0.18362.0** para o emulador do HoloLens 2.  (Observação: embora os binários façam parte do emulador do HoloLens 2, eles também funcionam para a realidade mista do Windows na área de trabalho.) um. PerceptionSimulationManager. Interop. dll-invólucro C# gerenciado para simulação de percepção.
    b. PerceptionSimulationRest. dll-Library para configurar um canal de comunicação de soquete da Web para o HoloLens ou o emulador.
    c. SimulationStream. Interop. dll-tipos compartilhados para simulação.
4. Adicione o binário de implementação PerceptionSimulationManager. dll ao seu projeto a. Primeiro, adicione-o como um binário ao projeto (projeto->adicionar >item existente...). Salve-o como um link para que ele não o copie para a pasta de origem do projeto. ![Adicione PerceptionSimulationManager. dll ao projeto como um link ](images/saveaslink.png) b. Em seguida, certifique-se de que ele seja copiado para a pasta de saída na compilação. Isso está na folha de propriedades do binário. ![Marque PerceptionSimulationManager. dll para copiar para o diretório de saída](images/copyalways.png)
5. Defina sua plataforma de solução ativa como x64.  (Use o Configuration Manager para criar uma entrada de plataforma para x64 se ainda não existir uma.)

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Criando um objeto do Gerenciador de IPerceptionSimulation

Para controlar a simulação, você emitirá atualizações para objetos recuperados de um objeto IPerceptionSimulationManager. A primeira etapa é obter esse objeto e conectá-lo ao seu dispositivo de destino ou emulador. Você pode obter o endereço IP do emulador clicando no botão portal do dispositivo na barra de [ferramentas](using-the-hololens-emulator.md)

![Abrir o ícone do portal do dispositivo ](images/emulator-deviceportal.png) **abra o portal do dispositivo**: Abra o portal do dispositivo do Windows para o sistema operacional do HoloLens no emulador.  Para a realidade mista do Windows, isso pode ser recuperado no aplicativo configurações em "atualizar & segurança" e, em seguida, "para desenvolvedores" na seção "conectar usando:" em "habilitar o portal do dispositivo".  Lembre-se de anotar o endereço IP e a porta.

Primeiro, você chamará RestSimulationStreamSink. Create para obter um objeto RestSimulationStreamSink. Esse é o dispositivo ou emulador de destino que você controlará em uma conexão http. Seus comandos serão passados e manipulados pelo portal do [dispositivo Windows](using-the-windows-device-portal.md) em execução no dispositivo ou emulador. Os quatro parâmetros necessários para criar um objeto são:
* URI Uri-endereço IP do dispositivo de destino (por exemplo, " https://123.123.123.123 " ou " https://123.123.123.123:50080 ")
* System .net. NetworkCredential credenciais-nome de usuário/senha para se conectar ao [portal de dispositivo do Windows](using-the-windows-device-portal.md) no dispositivo ou emulador de destino. Se você estiver se conectando ao emulador por meio de seu endereço local (por exemplo,*168...* *) no mesmo PC, todas as credenciais serão aceitas.
* bool normal-true para prioridade normal, false para baixa prioridade. Em geral, você desejará definir isso como *verdadeiro* para cenários de teste, o que permite que seu teste assuma o controle.  O emulador e a simulação de realidade mista do Windows usam conexões de baixa prioridade.  Se o teste também usar uma conexão de baixa prioridade, a conexão estabelecida mais recentemente estará no controle.
* System. Threading. CancellationToken token-token para cancelar a operação assíncrona.

Em segundo lugar, você criará o IPerceptionSimulationManager. Esse é o objeto que você usa para controlar a simulação. Observe que isso também deve ser feito em um método assíncrono.

## <a name="control-the-simulated-human"></a>Controlar o humano simulado

Um IPerceptionSimulationManager tem uma propriedade humana que retorna um objeto ISimulatedHuman. Para controlar o humano simulado, execute operações nesse objeto. Por exemplo:

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Aplicativo de console C# de exemplo básico

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

## <a name="extended-sample-c-console-application"></a>Aplicativo de console C# de exemplo estendido

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

## <a name="note-on-6-dof-controllers"></a>Observação em controladores 6-DOF

Antes de chamar qualquer propriedade em métodos em um controlador de 6 DOF simulado, você deve ativar o controlador.  Não fazer isso resultará em uma exceção.  A partir da atualização do Windows 10 de maio de 2019, os controladores 6 DOF simulados podem ser instalados e ativados definindo a propriedade status no objeto ISimulatedSixDofController como SimulatedSixDofControllerStatus. Active.
Na atualização do Windows 10 de outubro de 2018 e anterior, você deve instalar separadamente um controlador de 6 DOF simulado primeiro chamando a ferramenta PerceptionSimulationDevice localizada na pasta \Windows\System32.  O uso dessa ferramenta é o seguinte:


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

Por exemplo

```
    PerceptionSimulationDevice.exe i 6dof 1
```

As ações com suporte são:
* i = instalar
* q = consulta
* r = remover

As instâncias com suporte são:
* 1 = o controlador de 6 DOF à esquerda
* 2 = o controlador de 6 DOF à direita

O código de saída do processo indicará êxito (um valor de retorno zero) ou falha (um valor de retorno diferente de zero).  Ao usar a ação ' q ' para consultar se um controlador está ou não instalado, o valor de retorno será zero (0) se o controlador ainda não estiver instalado ou um (1) se o controlador estiver instalado.

Ao remover um controlador na atualização do Windows 10 de outubro de 2018 ou anterior, defina seu status como off por meio da API primeiro e, em seguida, chame a ferramenta PerceptionSimulationDevice.

Observe que essa ferramenta deve ser executada como administrador.




## <a name="api-reference"></a>Referência de API

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft. PerceptionSimulation. SimulatedDeviceType

Descreve um tipo de dispositivo simulado

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft. PerceptionSimulation. SimulatedDeviceType. Reference**

Um dispositivo de referência fictícia, o padrão para PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft. PerceptionSimulation. HeadTrackerMode

Descreve um modo de controlador de cabeçalho

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft. PerceptionSimulation. HeadTrackerMode. Default**

Rastreamento de cabeçalho padrão. Isso significa que o sistema pode selecionar o melhor modo de controle de cabeçalho com base nas condições de tempo de execução.

**Microsoft. PerceptionSimulation. HeadTrackerMode. Orientation**

Controle de cabeçalho somente orientação. Isso significa que a posição controlada pode não ser confiável, e algumas funcionalidades dependentes da posição de cabeçalho podem não estar disponíveis.

**Microsoft. PerceptionSimulation. HeadTrackerMode. Position**

Acompanhamento da cabeça posicional. Isso significa que a posição e a orientação da cabeça controlada são confiáveis

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft. PerceptionSimulation. SimulatedGesture

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

**Microsoft. PerceptionSimulation. SimulatedGesture. None**

Um valor de sentinela usado para indicar que não há gestos.

**Microsoft. PerceptionSimulation. SimulatedGesture. FingerPressed**

Um gesto de dedo pressionado.

**Microsoft. PerceptionSimulation. SimulatedGesture. FingerReleased**

Um gesto de liberação de dedo.

**Microsoft. PerceptionSimulation. SimulatedGesture. Home**

O gesto de residência/sistema.

**Microsoft. PerceptionSimulation. SimulatedGesture. Max**

O gesto máximo válido.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus

Os Estados possíveis de um controlador de 6 DOF simulado.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. off**

O controlador de 6 DOF está desligado.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. active**

O controlador de 6 DOF é ativado e acompanhado.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**

O controlador de 6 DOF está ativado, mas não pode ser acompanhado.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton

Os botões com suporte em um controlador de 6 DOF simulado.

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

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. None**

Um valor de sentinela usado para indicar nenhum botão.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Home**

O botão página inicial é pressionado.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. menu**

O botão de menu é pressionado.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Segure**

O botão de alça é pressionado.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**

O TouchPad é pressionado.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Select**

O botão Selecionar é pressionado.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**

O TouchPad é tocado.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Thumbstick**

O Thumbstick é pressionado.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Max**

O botão máximo válido.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState

O estado de calibragem dos olhos simulados

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. indisponível**

A calibragem de olhos não está disponível.

**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Ready**

Os olhos foram calibrados.  Esse é o valor padrão.

**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Configurando**

Os olhos estão sendo calibrados.

**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**

Os olhos precisam ser calibrados.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy

A precisão de rastreamento de um conjunto de mãos.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. indisponível**

A junção não é rastreada.

**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. aproximado**

A posição conjunta é inferida.

**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. Visible**

A junção é totalmente controlada.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft. PerceptionSimulation. SimulatedHandPose

A precisão de rastreamento de um conjunto de mãos.

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

**Microsoft. PerceptionSimulation. SimulatedHandPose. Closed**

As junções de dedo da mão são configuradas para refletir uma pose fechada.

**Microsoft. PerceptionSimulation. SimulatedHandPose. Open**

As junções de dedo da mão são configuradas para refletir uma pose aberta.

**Microsoft. PerceptionSimulation. SimulatedHandPose. Point**

As junções de dedo da mão são configuradas para refletir uma pose de apontador.

**Microsoft. PerceptionSimulation. SimulatedHandPose. pinçar**

As junções de dedo da mão são configuradas para refletir uma pose de pinçagem.

**Microsoft. PerceptionSimulation. SimulatedHandPose. Max**

O valor máximo válido para SimulatedHandPose.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft. PerceptionSimulation. Playbackstate

Descreve o estado de uma reprodução.

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft. PerceptionSimulation. Playbackstate. parado**

A gravação está atualmente parada e pronta para reprodução.

**Microsoft. PerceptionSimulation. Playbackstate. reproduzindo**

A gravação está sendo executada no momento.

**Microsoft. PerceptionSimulation. Playbackstate. Paused**

A gravação está em pausa no momento.

**Microsoft. PerceptionSimulation. Playbackstate. end**

A gravação atingiu o final.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft. PerceptionSimulation. Vector3

Descreve um vetor de 3 componentes, que pode descrever um ponto ou um vetor no espaço 3D.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft. PerceptionSimulation. Vector3. X**

O componente X do vetor.

**Microsoft. PerceptionSimulation. Vector3. Y**

O componente Y do vetor.

**Microsoft. PerceptionSimulation. Vector3. Z**

O componente Z do vetor.

**Microsoft. PerceptionSimulation. Vector3. #ctor (System. single, System. single, System. Single)**

Construa um novo Vector3.

Parâmetros
* x – o componente x do vetor.
* y-o componente y do vetor.
* z-o componente z do vetor.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft. PerceptionSimulation. Rotation3

Descreve uma rotação de 3 componentes.

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft. PerceptionSimulation. Rotation3. pitch**

O componente de pitch da rotação, em volta do eixo X.

**Microsoft. PerceptionSimulation. Rotation3. Guinad**

O componente de guinada da rotação, logo em volta do eixo Y.

**Microsoft. PerceptionSimulation. Rotation3. roll**

O componente de roll da rotação, logo em volta do eixo Z.

**Microsoft. PerceptionSimulation. Rotation3. #ctor (System. single, System. single, System. Single)**

Construa um novo Rotation3.

Parâmetros
* Pitch-o componente de pitch da rotação.
* guinada-o componente de guinada da rotação.
* roll-o componente de rolagem da rotação.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration

Descreve a configuração de uma junção em uma mão simulada.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Position**

A posição da junção.

**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Rotation**

A rotação da junção.

**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**

A precisão de rastreamento da junção.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft. PerceptionSimulation. frustum

Descreve um frustum de exibição, como normalmente usado por uma câmera.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft. PerceptionSimulation. frustum. near**

A distância mínima que está contida no frustum.

**Microsoft. PerceptionSimulation. frustum. far**

A distância máxima que está contida no frustum.

**Microsoft. PerceptionSimulation. frustum. FieldOfView**

O campo horizontal de exibição do frustum, em radianos (menor que PI).

**Microsoft. PerceptionSimulation. frustum. AspectRatio**

A proporção do campo horizontal de exibição para o campo vertical da exibição.

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a>Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration

Descreve a configuração da exibição do headset simulado.

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

**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**

A transformação do centro da cabeça à esquerda para fins de renderização de estéreo.

**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**

A rotação do olho à esquerda para fins de renderização de estéreo.

**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**

A transformação do centro da cabeça para o olho certo para fins de renderização de estéreo.

**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**

A rotação do olho certo para fins de renderização de estéreo.

**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. IPD**

O valor de IPD relatado pelo sistema para fins de renderização de estéreo.

**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**

Se os valores fornecidos para as transformações de olho esquerdo e direito devem ser considerados válidos e aplicados ao sistema em execução.

**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**

Se o valor fornecido para o IPD deve ser considerado válido e aplicado ao sistema em execução.


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft. PerceptionSimulation. IPerceptionSimulationManager

Raiz para gerar os pacotes usados para controlar um dispositivo.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Device**

Recupere o objeto de dispositivo simulado que interpreta o humano simulado e o mundo simulado.

**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Human**

Recupere o objeto que controla o humano simulado.

**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Reset**

Redefine a simulação para seu estado padrão.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft. PerceptionSimulation. ISimulatedDevice

Interface que descreve o dispositivo que interpreta o mundo simulado e o humano simulado

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft. PerceptionSimulation. ISimulatedDevice. HeadTracker**

Recupere o controlador de cabeçalho do dispositivo simulado.

**Microsoft. PerceptionSimulation. ISimulatedDevice. HandTracker**

Recupere o rastreador de mão do dispositivo simulado.

**Microsoft. PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**

Defina as propriedades do dispositivo simulado para corresponder ao tipo de dispositivo fornecido.

Parâmetros
* tipo – o novo tipo de dispositivo simulado

### <a name="microsoftperceptionsimulationisimulateddevice2"></a>Microsoft. PerceptionSimulation. ISimulatedDevice2

Propriedades adicionais estão disponíveis por meio da conversão de ISimulatedDevice para ISimulatedDevice2

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

**Microsoft. PerceptionSimulation. ISimulatedDevice2. IsUserPresent**

Recupere ou defina se o humano simulado está ou não ativamente desativando o headset.

**Microsoft. PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**

Recupere ou defina as propriedades da exibição simulada.

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft. PerceptionSimulation. ISimulatedHeadTracker

Interface que descreve a parte do dispositivo simulado que controla o início do humano simulado.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft. PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**

Recupera e define o modo de controlador de cabeçalho atual.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft. PerceptionSimulation. ISimulatedHandTracker

Interface que descreve a parte do dispositivo simulado que controla as mãos do humano simulado

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

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. WorldPosition**

Recupere a posição do nó com relação ao mundo, em metros.

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Position**

Recupere e defina a posição do controlador de mão simulado em relação ao centro do cabeçalho.

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. pitch**

Recupere e defina o timbre inferior do controlador de mão simulado.

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**

Recupere e defina se a frustum do controlador de mão simulado é ignorada. Quando ignorado, ambas as mãos estão sempre visíveis. Quando não ignoradas (as mãos padrão) ficam visíveis apenas quando estão dentro do frustum do rastreador.

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. frustum**

Recupere e defina as propriedades frustum usadas para determinar se as mãos estão visíveis para o controlador de mão simulado.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft. PerceptionSimulation. ISimulatedHuman

Interface de nível superior para controlar o humano simulado.

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

**Microsoft. PerceptionSimulation. ISimulatedHuman. WorldPosition**

Recupere e defina a posição do nó com relação ao mundo, em metros. A posição corresponde a um ponto no centro dos pés humanos.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Direction**

Recupere e defina a direção das faces humanas simuladas do mundo. 0 radianos está voltado para baixo no eixo Z negativo. Radianos positivos giram no sentido horário sobre o eixo Y.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Height**

Recupere e defina a altura do humano simulado, em metros.

**Microsoft. PerceptionSimulation. ISimulatedHuman. LeftHand**

Recupere o lado esquerdo do humano simulado.

**Microsoft. PerceptionSimulation. ISimulatedHuman. RightHand**

Recupere o lado direito do humano simulado.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Head**

Recupere o cabeçalho do humano simulado.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Move (Microsoft. PerceptionSimulation. Vector3)**

Mova o humano simulado relativo à sua posição atual, em metros.

Parâmetros
* translação-a tradução a ser movida, relativa à posição atual.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Rotate (System. Single)**

Girar o humano simulado em relação à sua direção atual, no sentido horário, sobre o eixo Y

Parâmetros
* radianos-o valor a ser girado em volta do eixo Y.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft. PerceptionSimulation. ISimulatedHuman2

Propriedades adicionais estão disponíveis por meio da conversão de ISimulatedHuman para ISimulatedHuman2

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedHuman2. LeftController**

Recupere o controlador esquerdo 6-DOF.

**Microsoft. PerceptionSimulation. ISimulatedHuman2. RightController**

Recupere o controlador de 6 DOF à direita.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft. PerceptionSimulation. ISimulatedHand

Interface que descreve uma mão do humano simulado

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

**Microsoft. PerceptionSimulation. ISimulatedHand. WorldPosition**

Recupere a posição do nó com relação ao mundo, em metros.

**Microsoft. PerceptionSimulation. ISimulatedHand. Position**

Recupere e defina a posição da mão simulada em relação ao humano, em metros.

**Microsoft. PerceptionSimulation. ISimulatedHand. Activated**

Recuperar e definir se a mão está ativada no momento.

**Microsoft. PerceptionSimulation. ISimulatedHand. Visible**

Recupere se a mão está visível no momento para o SimulatedDevice (ou seja, se está em uma posição a ser detectada pelo HandTracker).

**Microsoft. PerceptionSimulation. ISimulatedHand. EnsureVisible**

Mova a mão de modo que fique visível para o SimulatedDevice.

**Microsoft. PerceptionSimulation. ISimulatedHand. Move (Microsoft. PerceptionSimulation. Vector3)**

Mova a posição da mão simulada em relação à sua posição atual, em metros.

Parâmetros
* translation-o valor para converter a mão simulada.

**Microsoft. PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**

Execute um gesto usando a mão simulada.  Ele só será detectado pelo sistema se a mão estiver habilitada.

Parâmetros
* gesto-o gesto a ser executado.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft. PerceptionSimulation. ISimulatedHand2

Propriedades adicionais estão disponíveis por meio da conversão de um ISimulatedHand em ISimulatedHand2.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedHand2. Orientation**

Recupere ou defina a rotação da mão simulada.  Radianos positivos giram no sentido horário ao olhar ao longo do eixo.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft. PerceptionSimulation. ISimulatedHand3

Propriedades adicionais estão disponíveis por meio da conversão de um ISimulatedHand para ISimulatedHand3
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft. PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**

Obter a configuração conjunta para a junção especificada.

**Microsoft. PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**

Defina a configuração conjunta para a junção especificada.

**Microsoft. PerceptionSimulation. ISimulatedHand3. SetHandPose**

Defina a mão como uma pose conhecida com um sinalizador opcional para animar.  Observação: a animação não resultará em junções imediatamente refletindo suas configurações de conjuntos finais.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft. PerceptionSimulation. ISimulatedHead

Interface que descreve o cabeçalho do humano simulado.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft. PerceptionSimulation. ISimulatedHead. WorldPosition**

Recupere a posição do nó com relação ao mundo, em metros.

**Microsoft. PerceptionSimulation. ISimulatedHead. Rotation**

Recupere a rotação da cabeça simulada. Radianos positivos giram no sentido horário ao olhar ao longo do eixo.

**Microsoft. PerceptionSimulation. ISimulatedHead. diâmetro**

Recupere o diâmetro da cabeça simulada. Esse valor é usado para determinar o centro da cabeça (ponto de rotação).

**Microsoft. PerceptionSimulation. ISimulatedHead. Rotate (Microsoft. PerceptionSimulation. Rotation3)**

Girar a cabeça simulada em relação à sua rotação atual. Radianos positivos giram no sentido horário ao olhar ao longo do eixo.

Parâmetros
* rotação-o valor a ser girado.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft. PerceptionSimulation. ISimulatedHead2

Propriedades adicionais estão disponíveis por meio da conversão de um ISimulatedHead para ISimulatedHead2

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedHead2. eyess**

Recupere os olhos do humano simulado.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft. PerceptionSimulation. ISimulatedSixDofController

Interface que descreve um controlador de 6 DOF associado ao humano simulado.

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

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. WorldPosition**

Recupere a posição do nó com relação ao mundo, em metros.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. status**

Recupere ou defina o estado atual do controlador.  O status do controlador deve ser definido com um valor diferente de desativado antes que as chamadas para mover, girar ou pressionar botões tenham sucesso.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Position**

Recupere ou defina a posição do controlador simulado em relação ao humano, em metros.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Orientation**

Recupere ou defina a orientação do controlador simulado.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Move (Microsoft. PerceptionSimulation. Vector3)**

Mova a posição do controlador simulado em relação à sua posição atual, em metros.

Parâmetros
* translation-o valor para converter o controlador simulado.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**

Pressione um botão no controlador simulado.  Ele só será detectado pelo sistema se o controlador estiver habilitado.

Parâmetros
* botão-o botão para pressionar.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**

Libere um botão no controlador simulado.  Ele só será detectado pelo sistema se o controlador estiver habilitado.

Parâmetros
* botão-o botão a ser liberado.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**

Obtenha a posição de um dedo simulado no Touchpad do controlador simulado.

Parâmetros
* x-a posição horizontal do dedo.
* y-a posição vertical do dedo.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**

Defina a posição de um dedo simulado no Touchpad do controlador simulado.

Parâmetros
* x-a posição horizontal do dedo.
* y-a posição vertical do dedo.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft. PerceptionSimulation. ISimulatedSixDofController2

Propriedades e métodos adicionais estão disponíveis por meio da conversão de um ISimulatedSixDofController para ISimulatedSixDofController2

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**

Obtém a posição do Thumbstick simulado no controlador simulado.

Parâmetros
* x-a posição horizontal do Thumbstick.
* y-a posição vertical do Thumbstick.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**

Defina a posição do Thumbstick simulado no controlador simulado.

Parâmetros
* x-a posição horizontal do Thumbstick.
* y-a posição vertical do Thumbstick.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**

Recupere ou defina o nível de bateria do controlador simulado.  O valor deve ser maior que 0,0 e menor ou igual a 100,0.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft. PerceptionSimulation. ISimulatedEyes

Interface que descreve os olhos do humano simulado.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotation**

Recupere a rotação dos olhos simulados. Radianos positivos giram no sentido horário ao olhar ao longo do eixo.

**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotate (Microsoft. PerceptionSimulation. Rotation3)**

Gire os olhos simulados em relação à sua rotação atual. Radianos positivos giram no sentido horário ao olhar ao longo do eixo.

Parâmetros
* rotação-o valor a ser girado.

**Microsoft. PerceptionSimulation. ISimulatedEyes. calibrable**

Recupera ou define o estado de calibragem dos olhos simulados.

**Microsoft. PerceptionSimulation. ISimulatedEyes. WorldPosition**

Recupere a posição do nó com relação ao mundo, em metros.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft. PerceptionSimulation. ISimulationRecording

Interface para interagir com uma única gravação carregada para reprodução.

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

**Microsoft. PerceptionSimulation. ISimulationRecording. datatipos**

Recupera a lista de tipos de dados na gravação.

**Microsoft. PerceptionSimulation. ISimulationRecording. State**

Recupera o estado atual da gravação.

**Microsoft. PerceptionSimulation. ISimulationRecording. Play**

Inicie a reprodução. Se a gravação for pausada, a reprodução será retomada do local em pausa; Se for interrompido, a reprodução será iniciada no início. Se já estiver em execução, essa chamada será ignorada.

**Microsoft. PerceptionSimulation. ISimulationRecording. Pause**

Pausa a reprodução em seu local atual. Se a gravação for interrompida, a chamada será ignorada.

**Microsoft. PerceptionSimulation. ISimulationRecording. Seek (System. UInt64)**

Procura a gravação no tempo especificado (em intervalos de 100 nanossegundos desde o início) e pausa nesse local. Se o tempo estiver além do fim da gravação, ele será pausado no último quadro.

Parâmetros
* tiques-o tempo para o qual buscar.

**Microsoft. PerceptionSimulation. ISimulationRecording. Stop**

Interrompe a reprodução e redefine a posição para o início.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft. PerceptionSimulation. ISimulationRecordingCallback

Interface para receber alterações de estado durante a reprodução.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft. PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. reproduzstate)**

Chamado quando o estado de reprodução de um ISimulationRecording é alterado.

Parâmetros
* newState – o novo estado da gravação.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft. PerceptionSimulation. PerceptionSimulationManager

Objeto raiz para criar objetos de simulação de percepção.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**

Crie um objeto para gerar pacotes simulados e fornecê-los ao coletor fornecido.

Parâmetros
* coletor-o coletor que receberá todos os pacotes gerados.

Valor retornado

O gerente criado.

**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System. String)**

Crie um coletor que armazena todos os pacotes recebidos em um arquivo no caminho especificado.

Parâmetros
* caminho-o caminho do arquivo a ser criado.

Valor retornado

O coletor criado.

**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**

Carregar uma gravação do arquivo especificado.

Parâmetros
* caminho-o caminho do arquivo a ser carregado.
* Factory-uma fábrica usada pela gravação para criar um ISimulationStreamSink quando necessário.

Valor retornado

A gravação carregada.

**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**

Carregar uma gravação do arquivo especificado.

Parâmetros
* caminho-o caminho do arquivo a ser carregado.
* Factory-uma fábrica usada pela gravação para criar um ISimulationStreamSink quando necessário.
* retorno de chamada-um retorno de chamada que recebe atualizações que recebem o status da gravação.

Valor retornado

A gravação carregada.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft. PerceptionSimulation. StreamDataTypes

Descreve os diferentes tipos de dados de fluxo.

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

**Microsoft. PerceptionSimulation. StreamDataTypes. None**

Um valor de sentinela usado para indicar nenhum tipo de dados de fluxo.

**Microsoft. PerceptionSimulation. StreamDataTypes. Head**

Fluxo de dados em relação à posição e à orientação do cabeçalho.

**Microsoft. PerceptionSimulation. StreamDataTypes. hands**

Fluxo de dados em relação à posição e aos gestos de mãos.

**Microsoft. PerceptionSimulation. StreamDataTypes. SpatialMapping**

Fluxo de dados referente ao mapeamento espacial do ambiente.

**Microsoft. PerceptionSimulation. StreamDataTypes. Calibration**

Fluxo de dados referente à calibragem do dispositivo. Os pacotes de calibragem são aceitos apenas por um sistema no modo remoto.

**Microsoft. PerceptionSimulation. StreamDataTypes. Environment**

Fluxo de dados em relação ao ambiente do dispositivo.

**Microsoft. PerceptionSimulation. StreamDataTypes. SixDofControllers**

Fluxo de dados em relação aos controladores de movimento.

**Microsoft. PerceptionSimulation. StreamDataTypes. eyess**

Fluxo de dados em relação aos olhos do humano simulado.

**Microsoft. PerceptionSimulation. StreamDataTypes. DisplayConfiguration**

Fluxo de dados em relação à configuração de exibição do dispositivo.

**Microsoft. PerceptionSimulation. StreamDataTypes. All**

Um valor de sentinela usado para indicar todos os tipos de dados gravados.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft. PerceptionSimulation. ISimulationStreamSink

Um objeto que recebe pacotes de dados de um fluxo de simulação.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft. PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (pacote de comprimento uint, Byte [])**

Recebe um único pacote, que é digitado internamente e com controle de versão.

Parâmetros
* comprimento-o comprimento do pacote.
* pacote-os dados do pacote.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory

Um objeto que cria ISimulationStreamSink.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**

Cria uma única instância de ISimulationStreamSink.

Valor retornado

O coletor criado.
