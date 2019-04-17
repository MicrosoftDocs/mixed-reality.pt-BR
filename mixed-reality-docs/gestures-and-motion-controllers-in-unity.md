---
title: Gestos e controladores de movimento no Unity
description: Há duas maneiras principais para agir em seu foco no Unity, gestos de mão e controladores de movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimento, unity, olhar, de entrada
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589103"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Gestos e controladores de movimento no Unity

Há duas maneiras principais para agir em seu [contempla Unity](gaze-in-unity.md), [gestos de mão](gestures.md) e [controladores de movimento](motion-controllers.md). Você acessa os dados para ambas as fontes de entrada espacial por meio de APIs mesmas no Unity.

Unity fornece duas maneiras principais de acessar dados espaciais de entrada para o Windows Mixed Reality, comum *Input.GetButton/Input.GetAxis* APIs que funcionam entre vários SDKs para XR Unity, e um *InteractionManager / GestureRecognizer* API específica para o Windows Mixed Reality que expõe o conjunto completo de dados espaciais de entrada disponíveis.

## <a name="unity-buttonaxis-mapping-table"></a>Tabela de mapeamento de botão/eixo do Unity

As IDs de eixo e botão na tabela a seguir têm suporte no Unity Input Manager para controladores de movimento de realidade mista do Windows por meio de *Input.GetButton/GetAxis* APIs, enquanto a coluna "MR do Windows específica" refere-se às propriedades disponíveis para desativar o *InteractionSourceState* tipo. Cada uma dessas APIs são descritos em detalhes nas seções a seguir.

Os mapeamentos de ID do botão/eixo para Windows Mixed Reality geralmente corresponde ao botão Oculus/eixo IDs.

Os mapeamentos de ID do botão/eixo para Windows Mixed Reality diferem de mapeamentos do OpenVR de duas maneiras:
1. O mapeamento usa as IDs de touchpad são distintas de direcional, para dar suporte a controladores com alavancas direcionais e touchpads.
2. O mapeamento evita sobrecarregar o botão A e X IDs para os botões de Menu, deixar aqueles disponíveis para os botões ABXY físicos.

<table>
<tr>
<th rowspan="2">Entrada </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">APIs comuns do Unity</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">API de entrada específicos do Windows MR</a><br />(XR.WSA.Input)</th>
</tr><tr>
<th> À esquerda </th><th> Mão direita</th>
</tr><tr>
<td> Selecione o gatilho pressionado </td><td> Eixo 9 = 1.0 </td><td> Eixo 10 = 1.0 </td><td> selectPressed</td>
</tr><tr>
<td> Selecionar valor analógica do gatilho </td><td> Eixo 9 </td><td> Axis 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Selecione o gatilho parcialmente pressionado </td><td> Botão 14 <i>(compat gamepad)</i> </td><td> Botão 15 <i>(compat gamepad)</i> </td><td> selectPressedAmount &gt; 0,0</td>
</tr><tr>
<td> Botão de menu pressionado </td><td> Botão 6 * </td><td> Botão 7 * </td><td> menuPressed</td>
</tr><tr>
<td> Botão alça pressionado </td><td> Eixo 11 = 1.0 (nenhum valor analógico)<br />Botão 4 <i>(compat gamepad)</i> </td><td> Eixo 12 = 1.0 (nenhum valor analógico)<br />Botão 5 <i>(compat gamepad)</i> </td><td> foi segurado</td>
</tr><tr>
<td> X analógico <i>(à esquerda: -1,0, à direita: 1.0)</i> </td><td> Axis 1 </td><td> Eixo 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> Y analógico <i>(parte superior: -1,0, parte inferior: 1.0)</i> </td><td> Axis 2 </td><td> Eixo 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> Direcional pressionado </td><td> 8 de botão </td><td> 9 de botão </td><td> thumbstickPressed</td>
</tr><tr>
<td> X touchpad <i>(à esquerda: -1,0, à direita: 1.0)</i> </td><td> Eixo 17 * </td><td> Axis 19* </td><td> touchpadPosition.x</td>
</tr><tr>
<td> Y touchpad <i>(parte superior: -1,0, parte inferior: 1.0)</i> </td><td> Axis 18* </td><td> Axis 20* </td><td> touchpadPosition.y</td>
</tr><tr>
<td> Touchpad tocada </td><td> Botão 18 * </td><td> Botão 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> Touchpad pressionado </td><td> Botão 16 * </td><td> Botão 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF alça pose ou ponteiro pose </td><td colspan="2"> <i>Alça</i> representam apenas: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></td><td> Passar <i>alça</i> ou <i>ponteiro</i> como um argumento: sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> Estado de controle </td><td colspan="2"> <i>Posição precisão e a origem do risco de perda disponível apenas por meio da API específica MR</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Essas IDs de botão/eixo difere as IDs que usa o Unity para OpenVR devido a colisões nos mapeamentos usados pelo gamepads, toque Oculus e OpenVR.

## <a name="grip-pose-vs-pointing-pose"></a>Alça pose versus pose apontador

Realidade mista do Windows oferece suporte a controladores de movimento em uma variedade de fatores forma, com o design de cada controlador difere em sua relação entre a posição do usuário mão e natural "encaminhar" direção que aplicativos deve usar para apontando ao renderizar o controlador.

Para melhor representar esses controladores, há dois tipos de poses, você pode investigar para cada fonte de interação, o **alça pose** e o **pose ponteiro**. Ambas as as alça pose e ponteiro representam as coordenadas são expressas por todas as APIs do Unity em coordenadas de mundo globais do Unity.

### <a name="grip-pose"></a>Alça pose

O **alça pose** representa o local de palma da mão detectada por um HoloLens ou palma mantendo um controlador de animação.

Em fones imersivos em exposição, a alça pose é melhor usada para renderizar **mão do usuário** ou **um objeto é mantido em mãos do usuário**, como uma espada ou elétrons. A alça pose também é usada quando visualizando um controlador de animação, como o **que podem ser renderizado modelo** fornecida pelo Windows para um movimento controlador usa a alça pose como sua origem e o Centro de rotação.

A alça pose é definida especificamente da seguinte maneira:
* O **segure posição**: O centroide de palm pressionando o controlador naturalmente, ajustado esquerda ou direita para centralizar a posição dentro a alça. No controlador de animação do Windows Mixed Reality, essa posição geralmente se alinha com o botão de compreensão.
* O **Segure o eixo à direita da orientação**: Quando você abre completamente sua mão para formar uma dedo simples 5 pose, raio que é normal para o palm (para a frente da esquerda palm, com versões anteriores do palm à direita)
* O **Segure o eixo de encaminhamento da orientação**: Quando você fecha sua mão parcialmente (como se que mantém o controlador), o raio que aponta "forward" por meio de tubo formado por seus dedos não thumb.
* O **segure orientação backup eixo**: O eixo de cima indicado pelas definições de direito e Avançar.

Você pode acessar a alça pose por meio da API de entrada entre fornecedores do Unity, qualquer um dos (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) ou por meio da API do Windows MR específica (*sourceState.sourcePose.TryGetPosition/Rotation*, solicitando apresentam dados para o **alça** nó).

### <a name="pointer-pose"></a>Ponteiro pose

O **ponteiro pose** representa a dica do controlador que aponta para a frente.

O ponteiro fornecido pelo sistema pose é melhor usado para raycast quando você estiver **Renderizando o próprio modelo de controlador**. Se você estiver renderizando algum outro objeto virtual no lugar do controlador, como um de elétrons virtual, você deve apontar com um raio que seja mais natural para esse objeto virtual, como um raio que viaja ao longo do corpo do modelo de elétrons definidas pelo aplicativo. Porque os usuários podem ver o objeto virtual e não o controlador de físico, que aponta para ao objeto virtual provavelmente será mais natural para aqueles que usam seu aplicativo.

Atualmente, pose o ponteiro está disponível no Unity apenas pela API do Windows MR específico, *sourceState.sourcePose.TryGetPosition/Rotation*, passando *InteractionSourceNode.Pointer* como o argumento.

## <a name="controller-tracking-state"></a>Estado do controlador de rastreamento

Como fones de ouvido, o controlador de animação do Windows Mixed Reality não exige nenhuma configuração de sensores de controle externo. Em vez disso, os controladores são controlados pelos sensores no fone de ouvido em si.

Se o usuário move os controladores de exibição de campo do fone de ouvido, na maioria dos casos Windows continuará inferir posições de controlador e fornecê-los para o aplicativo. Quando o controlador perdeu visual de acompanhamento de tempo suficiente, posições do controlador descartará a precisão aproximados posições.

Neste ponto, o sistema será o bloqueio de corpo de controlador para o controle do usuário, a posição do usuário conforme eles se movimentam, enquanto ainda expor orientação true do controlador, usando seus sensores de orientação interna. Muitos aplicativos que usam controladores de apontar e ativar os elementos de interface do usuário podem operar normalmente enquanto estiver em precisão aproximado sem perceber o usuário.

A melhor maneira de ter uma noção do que isso é para testá-lo. Confira este vídeo com exemplos de conteúdo de imersão que funciona com os controladores de movimento em vários estados de controle:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>Pensando sobre explicitamente o estado de controle

Aplicativos que deseja tratar as posições de maneira diferente com base no estado de controle podem ir além e inspecione as propriedades no estado do controlador, como *SourceLossRisk* e *PositionAccuracy*:

<table>
<tr>
<th> Estado de controle </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Alta precisão</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> verdadeiro</td>
</tr><tr>
<td> <b>Alta precisão (correm o risco de perda)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> verdadeiro</td>
</tr><tr>
<td> <b>Precisão aproximado</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: green; color: white"> verdadeiro</td>
</tr><tr>
<td> <b>Nenhuma posição</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: orange"> false</td>
</tr>
</table>

Esses estados de acompanhamento do movimento controlador são definidos da seguinte maneira:
* **Alta precisão:** Enquanto o controlador de animação estiver dentro do campo de visão do fone de ouvido, geralmente fornecerá posições de alta precisão, com base no acompanhamento visual. Observe que um controlador de movimentação que momentaneamente deixa o campo de visualização ou obscurecida momentaneamente dos sensores fone de ouvido (por exemplo, por outro lado do usuário) continuarão a retornar apresenta alta precisão por um curto período, com base em controle inércia do controlador em si.
* **Alta precisão (correm o risco de perda):** Quando o usuário move o controlador de animação além da borda da exibição de campo do fone de ouvido, o fone de ouvido em breve será possível rastrear visualmente a posição do controlador. O aplicativo sabe quando o controlador atingiu esse limite FOV vendo os **SourceLossRisk** alcançar 1.0. Nesse ponto, o aplicativo pode optar por pausar gestos de controlador que exigem um fluxo constante de poses de alta qualidade.
* **Precisão aproximado:** Quando o controlador perdeu visual de acompanhamento de tempo suficiente, posições do controlador descartará a precisão aproximados posições. Neste ponto, o sistema será o bloqueio de corpo de controlador para o controle do usuário, a posição do usuário conforme eles se movimentam, enquanto ainda expor orientação true do controlador, usando seus sensores de orientação interna. Muitos aplicativos que usam controladores de apontar e ativar os elementos de interface do usuário podem funcionar como tempo normal em precisão aproximado sem perceber o usuário. Aplicativos com requisitos de entrada pesados podem optar por sentido Essa queda da **alta** precisão **aproximado** precisão inspecionando o **PositionAccuracy** propriedade, para exemplo para dar ao usuário um hitbox mais amplas em destinos de fora da tela durante esse tempo.
* **Nenhuma posição:** Enquanto o controlador pode operar em precisão aproximado por um longo tempo, às vezes, o sistema sabe que até mesmo uma posição bloqueada de corpo não é significativa no momento. Por exemplo, um controlador que foi ativado apenas talvez nunca foram observado visualmente, ou um usuário pode colocar para baixo de um controlador que é capturado por outra pessoa. Nesses momentos, o sistema não fornecerá qualquer posição para o aplicativo, e *TryGetPosition* retornará false.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>APIs comuns do Unity (Input.GetButton/GetAxis)

**Namespace:** *UnityEngine*, *UnityEngine.XR*<br>
**Tipos de**: *Input*, *XR.InputTracking*

Atualmente, o Unity usa seu gerais *Input.GetButton/Input.GetAxis* APIs para expor a entrada para [o SDK do Oculus](https://docs.unity3d.com/Manual/OculusControllers.html), [SDK OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html) e realidade mista do Windows, incluindo mãos e controladores de movimento. Se seu aplicativo usa essas APIs para entrada, ele pode facilmente dar suporte a controladores de movimento entre vários SDKs XR, incluindo Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Ao obter o estado pressionado de um botão lógica

Para usar as APIs de entrada Unity geral, normalmente comece por conectando botões e eixos para nomes lógicos na [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), associando um botão ou eixo IDs a cada nome. Em seguida, você pode escrever código que se refere a esse nome lógico de botão/eixo.

Por exemplo, para mapear o botão de gatilho do controlador de movimento à esquerda para a ação de envio, vá para **Editar > configurações do projeto > entrada** dentro do Unity e expandir as propriedades na seção de envio em eixos. Alterar o **botão positivo** ou **botão positivo de Alt** propriedade ler **botão joystick 14**, semelhante a esta:

![InputManager do Unity](images/unity-input-manager.png)<br>
*Unity InputManager*

Seu script, em seguida, pode verificar a ação de enviar usando *Input.GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Você pode adicionar botões mais lógica, alterando a **tamanho** propriedade sob **eixos**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Obtendo o estado pressionado de um botão físico diretamente

Você também pode acessar botões manualmente por seus totalmente qualificado nome, usando *Input.GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Obtendo uma mão ou pose do controlador de movimento

Você pode acessar a posição e rotação do controlador, usando *XR. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

Observe que isso representa alça pose do controlador (em que o usuário mantém o controlador), que é útil para renderizar uma espada ou elétrons em mãos do usuário ou um modelo do controlador em si.

Observe que a relação entre essa pose alça e a pose de ponteiro (em que a dica do controlador está apontando) pode ser diferente em controladores. No momento, só é possível por meio de entrada específicos MR API, descrito nas seções a seguir acessar pose do ponteiro do controlador.

## <a name="windows-specific-apis-xrwsainput"></a>APIs específicas do Windows (XR. WSA. Entrada)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Tipos de**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Para obter informações mais detalhadas sobre controladores de movimento e de entrada de mão de realidade mista do Windows (para HoloLens), você pode optar por usar as APIs de entrada espaciais específicos do Windows sob a *UnityEngine.XR.WSA.Input* namespace. Isso lhe permite acessar informações adicionais, como precisão de posição ou o tipo de fonte, permitindo que você conte mãos e controladores separados.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Sondagem para o estado das mãos e controladores de movimento

Você pode sondar para o estado desse quadro para cada fonte (manualmente ou movimento controlador) de interação usando o *GetCurrentReading* método.

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Cada *InteractionSourceState* você obter back representa uma fonte de interação no momento atual no tempo. O *InteractionSourceState* expõe informações como:
* Qual [tipos de pressionamentos de](motion-controllers.md) estão ocorrendo (selecione/Menu/compreensão/Touchpad/direcional)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Outros dados específicos para controladores de movimento, tal o touchpad e/ou do direcional coordenadas XY e estado tocado

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* O InteractionSourceKind saber se a fonte é uma mão ou um controlador de movimento

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Sondagem para renderização prevista de avanço poses

* Ao sondar dados de origem de interação de mãos e controladores, a apresenta a que você obter é poses prevista de encaminhamento para o ponto no tempo quando photons desse quadro serão chegar a atenção do usuário.  Esses poses prevista de avanço são melhor usadas para **renderização** o controlador ou um mantido cada quadro do objeto.  Se você estiver direcionando um determinado pressionamento ou com o controlador de versão, que será mais preciso, se você usar as APIs descritas abaixo de eventos históricos.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* Você também pode obter a pose principal prevista de encaminhamento para este quadro atual.  Como com a fonte pose, isso é útil para **renderização** um cursor, embora direcionado para uma determinada pressione ou versão sejam mais preciso, se você usar as APIs descritas abaixo de eventos históricos.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Manipulação de eventos de fonte de interação

Para lidar com eventos de entrada conforme acontecem com seus dados precisos pose históricos, você pode manipular eventos de fonte de interação, em vez de sondagem.

Para lidar com eventos de fonte de interação:
* Registre-se para uma *InteractionManager* evento de entrada. Para cada tipo de evento de interação que você está interessado, você precisará assiná-lo.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* Manipule o evento. Depois que você se inscreveu para um evento de interação, você obterá o retorno de chamada quando apropriado. No *SourcePressed* exemplo, este será depois que o código-fonte foi detectado e antes de ser liberado ou perdido.

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

### <a name="how-to-stop-handling-an-event"></a>Como parar manipulando um evento

Você precisa parar manipulando um evento quando você não estiver mais interessado no evento ou destruição de objeto que tiver assinado o evento. Para interromper a manipulação do evento, você cancelar o evento.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Lista de eventos de fonte de interação

Os eventos de origem de interação disponíveis são:
* *InteractionSourceDetected* (código-fonte se torne ativa)
* *InteractionSourceLost* (se torna inativo)
* *InteractionSourcePressed* (toque, pressionar o botão ou "Select" proferidos)
* *InteractionSourceReleased* (final de um toque, o botão foi liberado ou o fim do "Select" proferidos)
* *InteractionSourceUpdated* (move ou caso contrário, altera algum estado)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Eventos para poses históricos de direcionamento que correspondem a um press ou uma versão com mais precisão

As APIs de sondagem descritas anteriormente dar ao seu aplicativo poses prevista de encaminhamento.  Enquanto essas poses previstas são melhores para o controlador ou um objeto mão virtual de renderização, poses futuros não são ideais para direcionamento por dois motivos principais:
* Quando o usuário pressiona um botão em um controlador, pode haver aproximadamente 20 ms de latência sem fio via Bluetooth antes do sistema recebe o toque.
* Em seguida, se você estiver usando uma pose prevista de encaminhamento, existe seria outro 20ms de 10 de encaminhamento previsão aplicada para direcionar o tempo quando photons do quadro atual serão chegar a atenção do usuário.

Isso significa que sondagem lhe dá uma pose do código-fonte ou head representam o que é 30 40ms avanço de onde o usuário head e mãos, na verdade, estavam quando a versão ou pressione aconteceu.  Para a entrada de mão do HoloLens, embora não haja nenhum atraso de transmissão sem fio, há um atraso de processamento semelhante para detectar o toque.

Com precisão direcionar com base na intenção do usuário original para um pressionamento de mão ou controlador, você deve usar a fonte históricos pose ou pose principal de que *InteractionSourcePressed* ou *InteractionSourceReleased* eventos de entrada.

Você pode direcionar um pressionamento de ou liberar com dados de pose históricos de cabeça do usuário ou seu controlador:
* A principal pose no momento no tempo quando um controlador ou um gesto de pressionar ocorreu, o que pode ser usado para **direcionamento** para determinar o que o usuário estava [Observação](gaze.md) em:

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

* Ocorreu a pose de origem no momento no tempo quando pressiona um controlador de animação, que pode ser usado para **direcionamento** para determinar o que o usuário estava apontando o controlador na.  Esse será o estado do controlador que apresentou a imprensa.  Se você estiver Renderizando o próprio controlador, você pode solicitar a pose de ponteiro em vez de pose a alça, para acertar o raio de direcionamento do que o usuário considerará a dica natural do que renderizado controlador:

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>Gesto de composição de alto nível APIs (GestureRecognizer)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Tipos de**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

Seu aplicativo também pode reconhecer gestos de composição de nível superior para gestos de espera, navegação e manipulação de fontes de entrada espacial, toque. Você pode reconhecer esses gestos compostos entre ambos [mãos](gestures.md) e [controladores de movimento](motion-controllers.md) usando o GestureRecognizer.

Cada evento de gesto no GestureRecognizer fornece o SourceKind para a entrada, bem como o raio de cabeçalho de direcionamento no momento do evento. Alguns eventos fornecem informações específicas de contexto adicionais.

Há apenas algumas etapas necessárias para capturar os gestos usando um reconhecedor de gestos:
1. Criar um novo reconhecedor de gestos
2. Especifique quais gestos para inspecionar
3. Inscrever-se em eventos para esses gestos
4. Iniciar a captura de gestos

### <a name="create-a-new-gesture-recognizer"></a>Criar um novo reconhecedor de gestos

Para usar o *GestureRecognizer*, você deve ter criado uma *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Especifique quais gestos para inspecionar

Especifique quais gestos, você está interessado via *SetRecognizableGestures()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Inscrever-se em eventos para esses gestos

Assine eventos para os gestos que você está interessado.

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
>Gestos de navegação e manipulação são mutuamente exclusivos em uma instância de um *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Iniciar a captura de gestos

Por padrão, uma *GestureRecognizer* não monitora o processo de entrada até *StartCapturingGestures()* é chamado. É possível que um evento de gesto pode ser gerado após *StopCapturingGestures()* é chamado se a entrada foi realizada antes do quadro no qual *StopCapturingGestures()* foi processada. O *GestureRecognizer* irão se lembrar se ela foi ativada ou desativada durante o quadro previou no qual o gesto realmente ocorreu e então é confiável para iniciar e parar monitoramento de gesto baseado no olhar desse quadro direcionamento.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Parar a captura de gestos

Para interromper o reconhecimento de gesto:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Removendo um reconhecedor de gestos

Lembre-se de cancelar a assinatura de eventos assinados antes de destruir uma *GestureRecognizer* objeto.

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Renderizando o modelo de controlador de animação no Unity

![Teleportation e modelo do controlador de movimento](images/motioncontrollertest-teleport-1000px.png)<br>
*Teleportation e modelo do controlador de movimento*

Para renderizar os controladores de movimento em seu aplicativo que correspondem aos controladores de física, seus usuários estão mantendo e articulam como vários botões são pressionados, você pode usar o **MotionController pré-fabricado** no [Kit de ferramentas de realidade mista ](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Este pré-fabricado dinamicamente carrega o modelo de glTF correto em tempo de execução do driver de controlador de movimento instalado do sistema.  É importante carregar esses modelos dinamicamente em vez de importá-los manualmente no editor, para que seu aplicativo Mostrar modelos 3D fisicamente precisos para quaisquer controladores atuais e futuras de seus usuários pode ter.

1. Siga as [guia de Introdução](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instruções para baixar o Kit de ferramentas de realidade mista e adicioná-lo ao seu projeto do Unity.
2. Se você substituiu a câmera com a *MixedRealityCameraParent* pré-fabricado como parte das etapas de Introdução, você está pronto para começar!  Esse pré-fabricado inclui a renderização de controlador de animação.  Caso contrário, adicione *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* na sua cena do painel de projeto.  Você desejará adicionar pré-fabricado como um filho de qualquer objeto pai usar para mover a câmera ao redor quando teleports o usuário dentro de sua cena, para que os controladores vêm junto com o usuário.  Se seu aplicativo envolve teleporting, basta adicione pré-fabricado na raiz da sua cena.

## <a name="throwing-objects"></a>Gerando objetos

Lançamento de objetos em realidade virtual é um problema mais difícil, em seguida, ele pode primeiramente parecer. Assim como acontece com interações mais fisicamente com base, ao lançar no jogo atua de forma inesperada, ela é imediatamente óbvia e quebras de imersão. Passamos algum tempo pensando profundamente como representar um comportamento gerando fisicamente correto e surgir com algumas diretrizes, habilitadas por meio de atualizações para nossa plataforma, que gostaríamos de compartilhar com você.

Você pode encontrar um exemplo de como é recomendável implementar lançando [aqui](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). Este exemplo segue essas quatro diretrizes:
* **Usar o controlador *velocity* em vez de posição**. A atualização de novembro para Windows, apresentamos uma alteração no comportamento quando estiver na [' aproximar ' o estado do acompanhamento posicionais](motion-controllers.md#controller-tracking-state). Quando nesse estado, informações de velocidade sobre o controlador continuará a ser relatado para desde que acreditamos que é alta precisão, que é geralmente mais do que a posição permanecerá alta precisão.
* **Incorporar o *velocidade angular* do controlador**. Essa lógica está contida na `throwing.cs` arquivo o `GetThrownObjectVelAngVel` método estático, dentro do pacote no link acima:
   1. Como a velocidade angular é conservada, o objeto gerado deve manter a mesma velocidade angular como ela tinha no momento do lançamento: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Como a centro de massa do objeto gerado provavelmente que não na origem do pose a alça, provavelmente ele tem uma velocidade diferente e depois o do controlador no quadro de referência do usuário. A parte da velocidade do objeto contribuída dessa maneira é a velocidade de tangenciais instantânea da Centro de massa do objeto lançada em torno da origem do controlador. Essa velocidade tangenciais é o produto cruzado da velocidade angular do controlador com o vetor que representa a distância entre a origem do controlador e a centro de massa do objeto gerado.
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. A velocidade total do objeto lançada, portanto, é a soma da velocidade do controlador e essa velocidade tangenciais: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Preste muita atenção para o *tempo* em que podemos aplicar a velocidade**. Quando um botão é pressionado, pode levar até 20 ms para o evento de emergirem Bluetooth para o sistema operacional. Isso significa que, se você sondagem de uma alteração de estado do controlador de pressionado não pressionado ou vice-versa, as informações do controlador pose que obter com ele, na verdade, estará à frente dessa alteração no estado. Além disso, a pose controlador apresentada por nossa API de sondagem para frente é prevista para refletir uma probabilidade pose ao tempo que poderia ser mais 20ms, em seguida, no futuro o quadro será exibido. Isso é bom para *renderização* mantidos objetos, mas aumenta ainda mais o nosso problema de tempo para *direcionamento* o objeto conforme calculamos a trajetória para o momento em que o usuário soltou seu throw. Felizmente, com a atualização de novembro, quando um evento do Unity, como *InteractionSourcePressed* ou *InteractionSourceReleased* é enviada, o estado inclui os dados históricos pose de novamente quando o botão era, na verdade, pressionado ou liberado.  Para obter a renderização mais precisa do controlador e o direcionamento de controlador durante gera, você deve usar corretamente uma sondagem e eventos, conforme apropriado:
   * Para **renderização de controlador** cada quadro, seu aplicativo deve posicionar o controlador *GameObject* no controlador prevista de avanço representar para o tempo de photon do quadro atual.  Você obtém esses dados do Unity, como APIs de sondagem *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* ou  *[XR. WSA. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Para **direcionamento de controlador** após um press ou versão, seu aplicativo deve raycast e calcular trajetórias com base em pose os históricos de controlador para o evento pressione ou versão.  Obter esses dados de eventos do Unity APIs, como  *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.
* **Use a alça pose**. Velocidade angular e a velocidade são relatados em relação a pose alça, não pose de ponteiro.

Lançando continuará a melhorar com as atualizações futuras do Windows, e você pode esperar encontrar mais informações sobre ele aqui.

## <a name="accelerate-development-with-mixed-reality-toolkit"></a>Acelere o desenvolvimento com o Kit de ferramentas de realidade mista

Há duas cenas de exemplo sobre InputManager e MotionController no Unity. Por meio desses cenas, você pode aprender como usar InputManager do MRTK e acessar dados tratar eventos dentre os botões do controlador de animação.

- [HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [Detalhes técnicos arquivo Leiame](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

![Exemplo de entrada cenas no MRTK](images/MRTK_ExampleScene_Input.png)<br>
*Exemplo de entrada cenas no MRTK*

### <a name="automatic-scene-setup"></a>Instalação automática de cena

Quando você importa [MRTK liberar pacotes do Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) ou clonar o projeto a partir o [repositório GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), você vai encontrar um novo menu 'Toolkit de realidade mista' no Unity. No menu 'Configurar', você verá o menu 'Aplicar misto realidade cena configurações'. Quando você clica nele, ele remove a câmera padrão e adiciona os componentes básicos - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), e [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![Menu MRTK para a instalação de cena](images/MRTK_Input_Menu.png)<br>
*Menu MRTK para a instalação de cena*

![Instalação automática de cena no MRTK](images/MRTK_HowTo_Input1.png)<br>
*Instalação automática de cena no MRTK*

### <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera pré-fabricado

Você também pode adicionar manualmente esses do painel de projeto. Você pode encontrar esses componentes como pré-fabricados. Quando você procura **MixedRealityCamera**, você poderá ver duas pré-fabricados de câmera diferente. A diferença é que **MixedRealityCamera** é a câmera apenas pré-fabricado enquanto que o **MixedRealityCameraParent** inclui componentes adicionais para os fones imersivos em exposição como Teleportation, movimento Controlador e, limite.

![Pré-fabricados de câmera em MRTK](images/MRTK_HowTo_Input2.png)<br>
*Pré-fabricados de câmera em MRTK*

**MixedRealtyCamera** dá suporte ao HoloLens e envolvente fone de ouvido. Ele detecta o tipo de dispositivo e otimiza as propriedades como sinalizadores claras e Skybox. Abaixo você encontrará algumas das propriedades úteis que você pode personalizar como o Cursor personalizado, modelos de controlador de movimento e Floor.

![Propriedades para o controlador de movimento, Cursor e Floor](images/MRTK_HowTo_Input3.png)<br>
*Propriedades para o controlador de movimento, Cursor e Floor*

## <a name="follow-along-with-tutorials"></a>Siga tutoriais

Tutoriais passo a passo, com exemplos de personalização mais detalhados, estão disponíveis na academia de realidade mista:

- [Entrada MR 211: Gesto](holograms-211.md)
- [Entrada MR 213: Controladores de movimento](mixed-reality-213.md)

[![Entrada de MR 213 - controlador de movimento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*Entrada de MR 213 - controlador de movimento*

## <a name="see-also"></a>Consulte também

* [Gestos](gestures.md)
* [Controladores de movimento](motion-controllers.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [InteractionInputSource.cs no Unity MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
