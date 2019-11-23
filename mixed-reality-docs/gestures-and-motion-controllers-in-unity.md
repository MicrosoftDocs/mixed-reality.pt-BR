---
title: Gestos e controladores de movimento no Unity
description: Há duas maneiras principais de agir em seu olhar no Unity, gestos de mão e controladores de movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimento, Unity, olhar, entrada
ms.openlocfilehash: a85797bfb443f33147c116e90a02c88abda63c67
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926569"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Gestos e controladores de movimento no Unity

Há duas maneiras principais de agir em sua [olhar no Unity](gaze-in-unity.md), [gestos de mão](gaze-and-commit.md#composite-gestures) e [controladores de movimento](motion-controllers.md) no HoloLens e HMD de imersão. Você acessa os dados de ambas as fontes de entrada espacial por meio das mesmas APIs no Unity.

O Unity fornece duas maneiras principais de acessar dados de entrada espaciais para a realidade mista do Windows, as APIs comuns *Input. getbutton/Input. getaxis* que funcionam em vários SDKs do Unity XR e uma API *interactionmanager/GestureRecognizer* específica para a realidade mista do Windows que expõe o conjunto completo de dados de entrada espaciais disponíveis.

## <a name="unity-buttonaxis-mapping-table"></a>Tabela de mapeamento de botões/eixos do Unity

As IDs de botão e eixo na tabela abaixo têm suporte no Gerenciador de entrada do Unity para controladores de movimento de realidade mista do Windows por meio das APIs *Input. getbutton/getaxis* , enquanto a coluna "Windows Mr-specific" refere-se às propriedades disponíveis no tipo *InteractionSourceState* . Cada uma dessas APIs é descrita detalhadamente nas seções a seguir.

Os mapeamentos de ID de botão/eixo para a realidade mista do Windows geralmente correspondem às IDs de eixo/botão Oculus.

Os mapeamentos de ID de botão/eixo para a realidade mista do Windows diferem dos mapeamentos do OpenVR de duas maneiras:
1. O mapeamento usa IDs de touchpad que são diferentes de Thumbstick para dar suporte a controladores com Thumbsticks e touchpads.
2. O mapeamento evita sobrecarregar as IDs de botão a e X para os botões de menu, para deixá-las disponíveis para botões físicos de ABXY.

<table>
<tr>
<th rowspan="2">Entrada </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">APIs comuns do Unity</a><br />(Input. getbutton/getaxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#">API de entrada específica do Windows MR</a><br />XR. WSA. Entrada</th>
</tr><tr>
<th> À esquerda </th><th> À direita</th>
</tr><tr>
<td> Selecionar gatilho pressionado </td><td> Eixo 9 = 1,0 </td><td> Eixo 10 = 1,0 </td><td> selectPressed</td>
</tr><tr>
<td> Selecionar valor analógico do gatilho </td><td> Eixo 9 </td><td> Eixo 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Selecionar gatilho parcialmente pressionado </td><td> Botão 14 <i>(o compatível com gamepad)</i> </td><td> Botão 15 <i>(compatível com gamepad)</i> </td><td> selectPressedAmount &gt; 0,0</td>
</tr><tr>
<td> Botão de menu pressionado </td><td> Botão 6 * </td><td> Botão 7 * </td><td> menuPressed</td>
</tr><tr>
<td> Botão de alça pressionado </td><td> Eixo 11 = 1,0 (sem valores analógicos)<br />Botão 4 <i>(compatível com gamepad)</i> </td><td> Eixo 12 = 1,0 (sem valores analógicos)<br />Botão 5 <i>(compatível com gamepad)</i> </td><td> compreenderam</td>
</tr><tr>
<td> Thumbstick X <i>(esquerda:-1,0, direita: 1,0)</i> </td><td> Eixo 1 </td><td> Eixo 4 </td><td> thumbstickPosition. x</td>
</tr><tr>
<td> Thumbstick Y <i>(superior:-1,0, inferior: 1,0)</i> </td><td> Eixo 2 </td><td> Eixo 5 </td><td> thumbstickPosition. y</td>
</tr><tr>
<td> Thumbstick pressionado </td><td> Botão 8 </td><td> Botão 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Touchpad X <i>(esquerda:-1,0, direita: 1,0)</i> </td><td> Eixo 17 * </td><td> Eixo 19 * </td><td> touchpadPosition. x</td>
</tr><tr>
<td> Touchpad Y <i>(superior:-1,0, inferior: 1,0)</i> </td><td> Eixo 18 * </td><td> Eixo 20 * </td><td> touchpadPosition. y</td>
</tr><tr>
<td> Touchpad tocado </td><td> Botão 18 * </td><td> Botão 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> Touchpad pressionado </td><td> Botão 16 * </td><td> Botão 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> pose da alça de 6DoF de pose ou de ponteiro </td><td colspan="2"> <i>Segure</i> somente pose: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></td><td> Passar <i>alça</i> ou <i>ponteiro</i> como um argumento: SourceState. sourcePose. TryGetPosition<br />origemstate. sourcePose. TryGetRotation<br /></td>
</tr><tr>
<td> Estado de acompanhamento </td><td colspan="2"> A <i>precisão da posição e o risco de perda de origem só estão disponíveis por meio da API específica do MR</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">origemstate. sourcePose. positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">SourceState. Properties. sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Essas IDs de botão/eixo diferem das IDs que o Unity usa para OpenVR devido a colisões nos mapeamentos usados por gamepads, Oculus Touch e OpenVR.

## <a name="grip-pose-vs-pointing-pose"></a>Segurar pose vs. ponto de apontar

O Windows Mixed Reality dá suporte a controladores de movimento em uma variedade de fatores forma, sendo que o design de cada controlador difere em sua relação entre a posição da mão do usuário e a direção natural "encaminhar" que os aplicativos devem usar para apontar ao renderizar o controle.

Para representar melhor esses controladores, há dois tipos de poses que você pode investigar para cada origem de interação, a **pose de alça** e a pose do **ponteiro**. As coordenadas de pose pose e ponteiro representam expressas por todas as APIs do Unity nas coordenadas do mundo global do Unity.

### <a name="grip-pose"></a>Segurar pose

A **alça de pose** representa o local da palma de uma mão detectada por um HoloLens ou o Palm que está segurando um controlador de movimento.

Em headsets de imersão, a alça de fixação é mais bem usada para renderizar **a mão do usuário** ou **um objeto mantido na mão do usuário**, como uma gumes ou uma arma. A pose de alça também é usada ao visualizar um controlador de movimento, pois o **modelo renderizado** fornecido pelo Windows para um controlador de movimento usa a alça de pose como sua origem e o centro de rotação.

A pose de alça é definida especificamente da seguinte maneira:
* A **posição de alça**: o Palm centróide ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralizar a posição dentro da alça. No controlador de movimento de realidade mista do Windows, essa posição geralmente se alinha com o botão compreender.
* O **eixo direito da orientação de alça**: quando você abre completamente a mão para formar uma pose plana de 5 dedos, o raio normal para o Palm (para frente do Palm esquerdo, para trás do Palm direito)
* O **eixo de encaminhamento da orientação de alça**: quando você fecha a sua mão parcialmente (como se você mantiver o controlador), o raio que aponta para "encaminhar" por meio do tubo formado por seus dedos não-thumbs.
* O **eixo superior da orientação de alça**: o eixo superior implícito pelas definições direita e avançar.

Você pode acessar a alça de pose por meio da API de entrada entre fornecedores do Unity ( *[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) ou por meio da API específica do Windows Mr (*SourceState. SourcePose. TryGetPosition/Rotation*, solicitando dados de pose para o nó de **fixação** ).

### <a name="pointer-pose"></a>Pose de ponteiro

A **pose do ponteiro** representa a ponta do controlador que está apontando para frente.

A pose de ponteiro fornecida pelo sistema é mais bem usada para Raycast quando você está **renderizando o próprio modelo de controlador**. Se você estiver renderizando algum outro objeto virtual no lugar do controlador, como uma arma virtual, você deve apontar com um raio mais natural para esse objeto virtual, como um Ray que viaja ao longo do cilindro do modelo de pressão definido pelo aplicativo. Como os usuários podem ver o objeto virtual e não o controlador físico, apontar com o objeto virtual provavelmente será mais natural para aqueles que usam seu aplicativo.

Atualmente, a pose do ponteiro está disponível no Unity somente por meio da API específica do Windows Sr, *SourceState. sourcePose. TryGetPosition/Rotation*, passando *InteractionSourceNode. pointer* como o argumento.

## <a name="controller-tracking-state"></a>Estado de controle do controlador

Assim como os headsets, o controlador de movimento do Windows Mixed Reality não requer nenhuma configuração de sensores de controle externo. Em vez disso, os controladores são acompanhados por sensores no próprio headset.

Se o usuário mover os controladores para fora do campo de exibição do headset, na maioria dos casos, o Windows continuará inferindo as posições do controlador e as fornecerá ao aplicativo. Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada.

Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna. Muitos aplicativos que usam controladores para apontar e ativar elementos de interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba.

A melhor maneira de ter uma ideia para isso é experimentá-lo por conta própria. Confira este vídeo com exemplos de conteúdo de imersão que funciona com controladores de movimento em vários Estados de controle:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>Raciocínio sobre o estado de rastreamento explicitamente

Os aplicativos que desejam tratar as posições de forma diferente com base no estado de controle podem ir além e inspecionar as propriedades no estado do controlador, como *SourceLossRisk* e *PositionAccuracy*:

<table>
<tr>
<th> Estado de acompanhamento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Alta precisão</b> </td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> verdadeiro</td>
</tr><tr>
<td> <b>Alta precisão (com risco de perda)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> verdadeiro</td>
</tr><tr>
<td> <b>Precisão aproximada</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: green; color: white"> verdadeiro</td>
</tr><tr>
<td> <b>Sem posição</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: orange"> false</td>
</tr>
</table>

Esses Estados de acompanhamento do controlador de movimento são definidos da seguinte maneira:
* **Alta precisão:** Embora o controlador de movimento esteja dentro do campo de exibição do headset, ele geralmente fornecerá posições de alta precisão, com base no rastreamento visual. Observe que um controlador móvel que deixa momentaneamente o campo de exibição ou que é momentaneamente obscurecido dos sensores do headset (por exemplo, por outro lado do usuário) continuará retornando poses de alta precisão por um curto período, com base no acompanhamento inércia do controlador próprio.
* **Alta precisão (com risco de perda):** Quando o usuário move o controlador de movimento para cima da borda do campo de exibição do headset, o headset em breve não será capaz de rastrear visualmente a posição do controlador. O aplicativo sabe quando o controlador atingiu esse limite de FOV vendo o **SourceLossRisk** REACH 1,0. Nesse ponto, o aplicativo pode optar por pausar gestos do controlador que exigem um fluxo constante de poses de alta qualidade.
* **Precisão aproximada:** Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada. Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna. Muitos aplicativos que usam controladores para apontar para e ativar elementos da interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba. Os aplicativos com requisitos de entrada mais pesados podem optar por detectar essa queda de **alta** precisão à precisão **aproximada** inspecionando a propriedade **PositionAccuracy** , por exemplo, para dar ao usuário um hitbox mais generosa em destinos fora da tela durante esse tempo.
* **Sem posição:** Embora o controlador possa operar com precisão aproximada por um longo tempo, às vezes o sistema sabe que até mesmo uma posição bloqueada pelo corpo não é significativa no momento. Por exemplo, um controlador que acabou de ser ativado pode nunca ter sido observado visualmente ou um usuário pode colocar um controlador selecionado por outra pessoa. Naqueles momentos, o sistema não fornecerá nenhuma posição para o aplicativo e *TryGetPosition* retornará false.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>APIs comuns do Unity (Input. getbutton/getaxis)

**Namespace:** *UnityEngine*, *UnityEngine. XR*<br>
**Tipos**: *Input*, *XR. InputTracking*

No momento, o Unity usa suas APIs de *entrada geral. getbutton/Input. getaxis* para expor a entrada para [o SDK do OCULUS](https://docs.unity3d.com/Manual/OculusControllers.html), [o SDK do OpenVR e a](https://docs.unity3d.com/Manual/OpenVRControllers.html) realidade mista do Windows, incluindo controladores de mãos e de movimento. Se seu aplicativo usa essas APIs para entrada, ele pode facilmente dar suporte a controladores de movimento em vários SDKs do XR, incluindo a realidade mista do Windows.

### <a name="getting-a-logical-buttons-pressed-state"></a>Obtendo o estado pressionado de um botão lógico

Para usar as APIs de entrada gerais da Unity, você normalmente começará com a vinculação de botões e eixos a nomes lógicos no [Gerenciador de entrada do Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), ligando um botão ou IDs de eixo a cada nome. Em seguida, você pode escrever código que se refere a esse botão lógico/nome do eixo.

Por exemplo, para mapear o botão de gatilho do controlador de movimento à esquerda para a ação enviar, acesse **editar > configurações do projeto > entrada** no Unity e expanda as propriedades da seção enviar em eixos. Altere o **botão positivo** ou a propriedade do **botão Alt positivo** para ler o **botão 14 do joystick**, desta forma:

](images/unity-input-manager.png) InputManager do ![Unity<br>
*InputManager do Unity*

O script pode, então, verificar a ação de envio usando *Input. getbutton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Você pode adicionar mais botões lógicos alterando a propriedade **tamanho** em **eixos**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Obtendo um estado de botão físico pressionado diretamente

Você também pode acessar os botões manualmente por seu nome totalmente qualificado, usando *Input. GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Obter uma pose do controlador de movimento ou mão

Você pode acessar a posição e a rotação do controlador, usando o *XR. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

Observe que isso representa a pose de alça do controlador (onde o usuário mantém o controlador), que é útil para renderizar uma gumes ou uma arma na mão do usuário ou um modelo do próprio controlador.

Observe que a relação entre essa pose de alça e a pose do ponteiro (onde a ponta do controlador está apontando) pode diferir entre os controladores. Neste momento, o acesso à pose do ponteiro do controlador só é possível por meio da API de entrada específica do MR, descrita nas seções a seguir.

## <a name="windows-specific-apis-xrwsainput"></a>APIs específicas do Windows (XR. WSA. Entrada

**Namespace:** *UnityEngine. XR. WSA. Input*<br>
**Tipos**: *interactionmanager*, *InteractionSourceState*, *peractionname*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Para obter informações mais detalhadas sobre a entrada da mão de realidade mista do Windows (para o HoloLens) e os controladores de movimento, você pode optar por usar as APIs de entrada espaciais específicas do Windows no namespace *UnityEngine. XR. WSA. Input* . Isso permite que você acesse informações adicionais, como precisão de posição ou tipo de fonte, permitindo que você diga as mãos e os controladores.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Sondando o estado dos controladores de mãos e de movimento

Você pode sondar o estado deste quadro para cada fonte de interação (controlador de mão ou de movimento) usando o método *GetCurrentReading* .

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Cada *InteractionSourceState* que você retorna representa uma fonte de interação no momento atual. O *InteractionSourceState* expõe informações como:
* Que [tipos de prensas](motion-controllers.md) estão ocorrendo (Select/menu/Segure/Touchpad/Thumbstick)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Outros dados específicos de controladores de movimento, como as coordenadas XY do Touchpad e/ou do Thumbstick e o estado tocado

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* O InteractionSourceKind para saber se a origem é uma mão ou um controlador de movimento

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Sondagem para encaminhar representações de renderização previstas

* Durante a sondagem de dados de origem de interação de mãos e controladores, as poses que você obtém são as mais previstas para o momento em que o fótons do quadro atingirá os olhos do usuário.  Essas poses previstas antecipadas são mais bem usadas para **renderizar** o controlador ou um objeto mantido em cada quadro.  Se você estiver direcionando um determinado Press ou Release com o controlador, isso será mais preciso se você usar as APIs de eventos de histórico descritas abaixo.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* Você também pode obter a pose de cabeça prevista para este quadro atual.  Assim como acontece com o pose de origem, isso é útil para **renderizar** um cursor, embora o direcionamento de uma determinada prensa ou versão seja mais preciso se você usar as APIs de evento históricas descritas abaixo.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Tratamento de eventos de origem de interação

Para lidar com eventos de entrada à medida que eles acontecem com seus dados históricos de histórico precisos, você pode manipular eventos de origem de interação em vez de sondagem.

Para lidar com eventos de origem de interação:
* Registre-se para um evento de entrada entre *ações* . Para cada tipo de evento de interação em que você está interessado, você precisa assiná-lo.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* Manipule o evento. Depois de se inscrever em um evento de interação, você receberá o retorno de chamada quando apropriado. No exemplo de *SourcePressed* , isso será depois que a origem for detectada e antes de ser liberada ou perdida.

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>Como parar de lidar com um evento

Você precisa parar de lidar com um evento quando não estiver mais interessado no evento ou se estiver destruindo o objeto que assinou o evento. Para parar de lidar com o evento, cancele a assinatura do evento.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Lista de eventos de origem de interação

Os eventos de origem de interação disponíveis são:
* *InteractionSourceDetected* (a origem se torna ativa)
* *InteractionSourceLost* (torna-se inativo)
* *InteractionSourcePressed* (toque, pressionamento de botão ou "selecionar" desmarcado)
* *InteractionSourceReleased* (fim de um toque, botão liberado ou fim de "selecionar" exmovida)
* *InteractionSourceUpdated* (move ou altera qualquer Estado)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Os eventos de direcionamento histórico representam que correspondem mais precisamente a uma prensa ou liberação

As APIs de sondagem descritas anteriormente fornecem às suas representações previstas de seu aplicativo.  Embora essas poses previstas sejam melhores para renderizar o controlador ou um objeto portátil Virtual, as poses futuras não são ideais para o direcionamento, por dois motivos principais:
* Quando o usuário pressiona um botão em um controlador, pode haver cerca de 20 ms de latência sem fio sobre o Bluetooth antes que o sistema receba a prensa.
* Em seguida, se você estiver usando uma pose prevista para o futuro, haveria mais 10 20 ms de previsão de encaminhamento aplicada ao destino quando o fótons do quadro atual atingirá os olhos do usuário.

Isso significa que a sondagem fornece uma pose de origem ou uma pose de cabeça que é de 30 a 40ms para frente, de onde a cabeça do usuário e as mãos realmente estavam de volta quando a imprensa ou a versão ocorreu.  Para entrada à mão do HoloLens, enquanto não há atraso de transmissão sem fio, há um atraso de processamento semelhante para detectar a prensa.

Para ter um destino com precisão com base na intenção original do usuário para um pressionamento de mão ou de controlador, você deve usar a pose de origem histórica ou de cabeçalho desse evento de entrada *InteractionSourcePressed* ou *InteractionSourceReleased* .

Você pode direcionar um Press ou Release com dados históricos de pose do cabeçalho do usuário ou de seu controlador:
* A parte de cabeça no momento em que uma ocorrência de gesto ou controlador ocorreu, que pode ser **usada para determinar** o que o usuário estava [nuvensndo](gaze-and-commit.md) :

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* A origem representa no momento em que uma ocorrência de controlador de movimento ocorreu, que pode ser **usada para determinar a que o** usuário estava apontando o controlador.  Esse será o estado do controlador que sofreu a prensa.  Se você estiver renderizando o próprio controlador, poderá solicitar a pose do ponteiro em vez da pose de alça, para atingir o direcionamento de raio a partir do que o usuário considerará a dica natural desse controlador renderizado:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>Exemplo de manipuladores de eventos

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>APIs de gesto de composição de alto nível (GestureRecognizer)

**Namespace:** *UnityEngine. XR. WSA. Input*<br>
**Tipos**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

Seu aplicativo também pode reconhecer gestos de composição de nível superior para fontes de entrada espaciais, toque, retenção, manipulação e gestos de navegação. Você pode reconhecer esses gestos compostos entre os controladores de [mão](gaze-and-commit.md#composite-gestures) e de [movimento](motion-controllers.md) usando o GestureRecognizer.

Cada evento de gesto no GestureRecognizer fornece o SourceKind para a entrada, bem como a cabeça de destino Ray no momento do evento. Alguns eventos fornecem informações adicionais específicas do contexto.

Há apenas algumas etapas necessárias para capturar gestos usando um reconhecedor de gestos:
1. Criar um novo reconhecedor de gestos
2. Especificar quais gestos observar
3. Assinar eventos para esses gestos
4. Começar a capturar gestos

### <a name="create-a-new-gesture-recognizer"></a>Criar um novo reconhecedor de gestos

Para usar o *GestureRecognizer*, você deve ter criado um *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Especificar quais gestos observar

Especifique em quais gestos você está interessado por meio de *SetRecognizableGestures ()* :

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Assinar eventos para esses gestos

Assine eventos para os gestos nos quais você está interessado.

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>Os gestos de navegação e manipulação são mutuamente exclusivos em uma instância de um *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Começar a capturar gestos

Por padrão, um *GestureRecognizer* não monitora a entrada até que *StartCapturingGestures ()* seja chamado. É possível que um evento de gesto possa ser gerado após *StopCapturingGestures ()* ser chamado se a entrada tiver sido executada antes do quadro em que *StopCapturingGestures ()* foi processado. O *GestureRecognizer* se lembrará se ele estava ativado ou desativado durante o quadro anterior no qual o gesto realmente ocorreu e, portanto, é confiável para iniciar e parar o monitoramento de gestos com base no direcionamento de olhar deste quadro.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Parar a captura de gestos

Para interromper o reconhecimento de gesto:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Removendo um reconhecedor de gesto

Lembre-se de cancelar a assinatura de eventos assinados antes de destruir um objeto *GestureRecognizer* .

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Renderizando o modelo de controlador de movimento no Unity

modelo de controlador de movimento ![e teleportação](images/motioncontrollertest-teleport-1000px.png)<br>
*Modelo de controlador de movimento e teleportação*

Para renderizar os controladores de movimento em seu aplicativo que correspondam aos controladores físicos que os usuários estão mantendo e articulados conforme vários botões são pressionados, você pode usar o **MotionController pré-fabricado** no [Kit de ferramentas da realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Esse pré-fabricado dinamicamente carrega o modelo de glTF correto em tempo de execução do driver do controlador de movimento instalado do sistema.  É importante carregar esses modelos dinamicamente, em vez de importá-los manualmente no editor, para que seu aplicativo mostre modelos 3D fisicamente precisos para todos os controladores atuais e futuros que seus usuários possam ter.

1. Siga as instruções de [introdução](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) para baixar o kit de ferramentas de realidade misturada e adicioná-lo ao seu projeto do Unity.
2. Se você substituiu a câmera pelo *MixedRealityCameraParent* pré-fabricado como parte das etapas introdução, está pronto!  Esse pré-fabricado inclui a renderização do controlador de movimento.  Caso contrário, adicione *assets/HoloToolkit/Input/pré-fabricados/MotionControllers. pré-fabricado* à sua cena no painel do projeto.  Você desejará adicionar esse pré-fabricado como um filho de qualquer objeto pai usado para mover a câmera quando o usuário estiver em sua cena, para que os controladores acompanhem o usuário.  Se seu aplicativo não envolver a teleportabilidade, basta adicionar o pré-fabricado na raiz da sua cena.

## <a name="throwing-objects"></a>Lançando objetos

A geração de objetos na realidade virtual é um problema mais difícil e, em primeiro lugar, pode parecer. Assim como acontece com a maioria das interações com base fisicamente, quando o jogo atua de forma inesperada, ele é imediatamente óbvio e quebra imersão. Nós gastamos algum tempo pensando em como representar um comportamento de lançamento fisicamente correto e apresentamos algumas diretrizes, habilitadas por meio de atualizações em nossa plataforma, que gostaríamos de compartilhar com você.

Você pode encontrar um exemplo de como é recomendável implementar o lançamento [aqui](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). Este exemplo segue estas quatro diretrizes:
* **Use a *velocidade* do controlador em vez da posição**. Na atualização de novembro do Windows, apresentamos uma alteração no comportamento no estado de [controle posicional ' ' aproximado](motion-controllers.md#controller-tracking-state)'. Quando nesse estado, as informações de velocidade sobre o controlador continuarão sendo relatadas durante o período em que acreditamos que seja alta precisão, o que geralmente é maior que a posição permanece com alta precisão.
* **Incorpore a *velocidade angular* do controlador**. Essa lógica está incluída no arquivo `throwing.cs` no método estático `GetThrownObjectVelAngVel`, dentro do pacote vinculado acima:
   1. À medida que a velocidade angular é conservada, o objeto gerado deve manter a mesma velocidade angular que tinha no momento do lançamento: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Como o centro da massa do objeto gerado provavelmente não está na origem da pose de alça, ele provavelmente tem uma velocidade diferente do controlador no quadro de referência do usuário. A parte da velocidade do objeto que contribuiu dessa forma é a velocidade tangential instantânea do centro da massa do objeto gerado em relação à origem do controlador. Essa velocidade de tangential é o produto cruzado da velocidade angular do controlador com o vetor que representa a distância entre a origem do controlador e o centro da massa do objeto gerado.
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. A velocidade total do objeto gerado é, portanto, a soma da velocidade do controlador e dessa velocidade de tangential: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Preste muita atenção à *hora* em que aplicamos a velocidade**. Quando um botão é pressionado, pode levar até 20 ms para que esse evento seja emergido por meio do Bluetooth para o sistema operacional. Isso significa que, se você sondar uma alteração de estado do controlador de pressionado para não pressionado ou vice-versa, o controlador apresentará as informações que você obtém com ele, na verdade, estará à frente dessa alteração no estado. Além disso, a pose do controlador apresentada por nossa API de sondagem está prevista para refletir uma causa provável no momento em que o quadro será exibido, o que poderia ser mais 20 ms no futuro. Isso é bom para *renderizar* objetos mantidos, mas aumenta nosso problema de tempo para *direcionar* o objeto à medida que calculamos a trajetória para o momento em que o usuário lançou o seu lançamento. Felizmente, com a atualização de novembro, quando um evento do Unity como *InteractionSourcePressed* ou *InteractionSourceReleased* é enviado, o estado inclui os dados históricos de back quando o botão foi realmente pressionado ou liberado.  Para obter a renderização de controlador e o direcionamento de controlador mais precisos durante as jogadas, você deve usar corretamente a sondagem e o evento, conforme apropriado:
   * Para **renderizar** cada quadro do controlador, seu aplicativo deve posicionar o *gameobject* do controlador no controlador previsto para o momento da Photon do quadro atual.  Você obtém esses dados de APIs de sondagem do Unity como a *[XR. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* ou *[XR. WSA. Entrada. interactionmanager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .
   * Para **direcionamento de controlador** em uma prensa ou liberação, seu aplicativo deve Raycast e calcular as trajetórias com base na pose do controlador histórico para esse evento de Press ou Release.  Você obtém esses dados das APIs de eventos do Unity, como *[interactionmanager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .
* **Use a pose de alça**. A velocidade angular e a velocidade são relatadas em relação à pose de alça, não à pose de ponteiro.

O lançamento continuará a melhorar com futuras atualizações do Windows e você poderá esperar mais informações sobre ela aqui.

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a>Controladores de gesto e movimento no MRTK v2

Você pode acessar o gesto e o controlador de movimento do Gerenciador de entrada. 
* [Gesto no MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [Controlador de movimento no MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a>Siga junto com os tutoriais

Os tutoriais passo a passo, com exemplos de personalização mais detalhados, estão disponíveis na Academia de realidade misturada:

- [Entrada MR 211: gesto](holograms-211.md)
- [Entrada MR 213: controladores de movimento](mixed-reality-213.md)

[![Sr Input 213-controlador de movimento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*Entrada MR 213-controlador de movimento*

## <a name="see-also"></a>Consulte também

* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Controladores de movimentos](motion-controllers.md)


