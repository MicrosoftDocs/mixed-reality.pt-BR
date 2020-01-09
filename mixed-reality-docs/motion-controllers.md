---
title: controladores de movimentos
description: Detalhes sobre os controladores de movimento de realidade misturada.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: controladores de 6DOF, controladores de movimento
ms.openlocfilehash: e4b3946401bcc9abfcefeb3e33bb79f01526ba20
ms.sourcegitcommit: d0da0214fdd2bbac5a91a5d895bf0e87413b29b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597669"
---
# <a name="motion-controllers"></a>controladores de movimentos

:::row:::
    :::column:::
        Os controladores de movimento são [acessórios de hardware](hardware-accessories.md) que permitem que os usuários executem ações em realidade misturada. Uma vantagem dos controladores de movimento em [gestos](gaze-and-commit.md#composite-gestures) é que os controladores têm uma posição precisa no espaço, permitindo uma interação refinada com objetos digitais. Para os headsets de imersão de realidade misturada do Windows, os controladores de movimento são a principal maneira que os usuários executarão ações em seu mundo.<br>
        <br>
        *Imagem: um controlador de movimento do Windows Mixed Reality*
    :::column-end:::
        :::column:::
       ![Controladores de movimento do Windows Mixed Reality](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="device-support"></a>Suporte a dispositivos

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Recurso</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
</tr>
<tr>
     <td>controladores de movimentos</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>Detalhes do hardware

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Os controladores de movimento de realidade mista do Windows oferecem acompanhamento preciso e responsivo de movimento em seu campo de exibição usando os sensores no headset de imersão, o que significa que não há necessidade de instalar o hardware nas paredes no seu espaço. Esses controladores de movimento oferecerão a mesma facilidade de instalação e portabilidade que os headsets de imersão de realidade misturada do Windows. Nossos parceiros de dispositivo planejam comercializar e vender esses controladores em prateleiras de varejo neste feriado.

![conhecer seu controlador](images/controllerimage-750px.png)<br>
*Conheça seu controlador*

**Recursos:**
* Rastreamento óptico
* Disparador
* Botão de captura
* Thumbstick
* Touchpad

## <a name="setup"></a>Configuração

### <a name="before-you-begin"></a>Antes de começar

**Você precisará de:**
* Um conjunto de dois controladores de movimento.
* Quatro baterias AA.
* Um PC capaz de Bluetooth 4,0.

**Verificar atualizações do Windows, Unity e driver**
* Visite [instalar as ferramentas](install-the-tools.md) para as versões preferenciais do Windows, Unity, etc. para o desenvolvimento de realidade misturada.
* Verifique se você tem os drivers mais atualizados do [headset e do controlador de movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software).

### <a name="pairing-controllers"></a>Controladores de emparelhamento

Os controladores de movimento podem ser acoplados ao computador host usando as configurações do Windows como qualquer outro dispositivo Bluetooth.

1. Insira 2 baterias AA na parte traseira do controlador. Deixe a tampa da bateria desativada por enquanto.
2. Se você estiver usando um adaptador USB Bluetooth externo em vez de um rádio Bluetooth interno, examine as [práticas recomendadas do Bluetooth](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) antes de continuar. Para configuração de desktop com rádio interno, verifique se a antena está conectada.
3. Abra **as configurações do Windows** -> **dispositivos** -> **adicionar Bluetooth ou outro dispositivo** -> **Bluetooth** e remova as instâncias anteriores de "controlador de movimento – direita" e "controlador de movimento – à esquerda". Verifique também a categoria outros dispositivos na parte inferior da lista.
4. Selecione **Adicionar Bluetooth ou outro dispositivo** e veja se ele está começando a descobrir dispositivos Bluetooth.
5. Pressione e segure o botão do Windows do controlador para ligar o controlador e solte-o quando ele for repercussão.
6. Pressione e segure o botão de emparelhamento (guia no compartimento de bateria) até que os LEDs comecem a Pulsing.

:::row:::
    :::column:::
7. Espere "controlador de movimento à esquerda" ou "controlador de movimento-direita" para aparecer na parte inferior da lista. Selecione para emparelhar. O controlador irá vibrar uma vez quando conectado.<br>
        <br>
        *Imagem: selecione "controlador de movimento" para emparelhar; Se houver várias instâncias, selecione uma na parte inferior da lista*
    :::column-end:::
        :::column:::
       ![Selecione o controlador de movimento a ser emparelhado, se várias instâncias selecionarem uma na parte inferior da lista](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. Você verá o controlador aparecer nas configurações de Bluetooth na **categoria "mouse, teclado, & Pen"** como **conectado**. Neste ponto, você pode obter uma atualização de firmware – consulte a [próxima seção](motion-controllers.md#updating-controller-firmware).
9. Reconecte a tampa da bateria.
10. Repita as etapas de 1-9 para o segundo controlador.

<br>

:::row:::
    :::column:::
        Depois de emparelhar os dois controladores com êxito, suas configurações devem ser semelhantes às seguintes, na **categoria "mouse, teclado, & caneta"** <br>
        <br>
        *Imagem: controladores de movimento conectados*
    :::column-end:::
        :::column:::
       ![Controladores de movimento conectados](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

Se os controladores estiverem desativados após o emparelhamento, seu status será exibido como emparelhado. Se os controladores permanecerem permanentemente sob a categoria "outros dispositivos", o emparelhamento pode ter sido apenas parcialmente concluído e precisa ser executado novamente para que o controlador fique funcional.

### <a name="updating-controller-firmware"></a>Atualizando firmware do controlador

* Se um headset de imersão estiver conectado ao seu computador e o novo firmware do controlador estiver disponível, o firmware será enviado por push para seus controladores de movimento automaticamente na próxima vez que forem ativados. As atualizações de firmware do controlador são indicadas por um padrão de quadrantes de LED de iluminação em um movimento circular e levar de 1-2 minutos.


:::row:::
    :::column:::
* Após a conclusão da atualização do firmware, os controladores serão reinicializados e reconectados. Ambos os controladores devem estar conectados agora. <br>
        <br>
        *Imagem: controladores conectados em configurações de Bluetooth*
    :::column-end:::
        :::column:::
       ![Controladores conectados](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* Verifique se os controladores funcionam corretamente:
    1. Inicie o **portal de realidade misturada** e insira sua página inicial de realidade misturada.
    2. Mova seus controladores e verifique o acompanhamento, os botões de teste e verifique se a [teleportabilidade](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) funciona. Se não estiverem, verifique a [solução de problemas do controlador de movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers).

## <a name="gazing-and-pointing"></a>Nuvens e apontando

O Windows Mixed Reality dá suporte a dois modelos principais para interação; **olhar e commit** e Begin e **Commit**:
* Com **olhar e commit**, os usuários direcionam um objeto com seus [olhar](gaze-and-commit.md) e, em seguida, selecionam objetos com toques de ar à mão, um gamepad, um selecionador ou sua voz.
* Com o **ponto e a confirmação**, um usuário pode direcionar um controlador de movimento com capacidade para apontar no objeto de destino e, em seguida, selecionar objetos com o gatilho do controlador.

Os aplicativos que dão suporte ao uso de controladores de movimento também devem habilitar as interações controladas por olhar sempre que possível, para dar aos usuários uma opção de quais dispositivos de entrada eles usam.

### <a name="managing-recoil-when-pointing"></a>Gerenciando a rebobinação ao apontar

Ao usar os controladores de movimento para apontar e confirmar, os usuários usarão o controlador para o destino e, em seguida, executarão uma ação ao extrair seu gatilho. Os usuários que recebem o gatilho rigorosamente podem acabar mirando o controlador no final do seu gatilho de pull do que pretendia.

Para gerenciar tal rebobinação que pode ocorrer quando os usuários puxam o gatilho, seu aplicativo pode ajustar seu direcionamento de destino quando o valor do eixo analógico do gatilho se elevar acima de 0,0. Em seguida, você pode tomar medidas usando essa meta de raio alguns quadros depois, uma vez que o valor do gatilho atinja 1,0, desde que a última vez ocorra em uma pequena janela de tempo. Ao usar o [gesto de toque composto](gaze-and-commit.md#composite-gestures)de nível superior, o Windows gerenciará essa captura de raio de destino e o tempo limite para você.

## <a name="grip-pose-vs-pointing-pose"></a>Segurar pose vs. ponto de apontar

O Windows Mixed Reality dá suporte a controladores de movimento em uma variedade de fatores forma, sendo que o design de cada controlador difere em sua relação entre a posição da mão do usuário e a direção natural "encaminhar" que os aplicativos devem usar para apontar ao renderizar o controle.

Para representar melhor esses controladores, há dois tipos de poses que você pode investigar para cada fonte de interação; a pose de **alça** e a **pose do ponteiro**.

### <a name="grip-pose"></a>Segurar pose

A **alça de pose** representa o local da palma de uma mão detectada por um HoloLens ou o Palm que está segurando um controlador de movimento.

Em headsets de imersão, a alça de fixação é mais bem usada para renderizar **a mão do usuário** ou **um objeto mantido na mão do usuário**, como uma gumes ou uma arma. A pose de alça também é usada ao visualizar um controlador de movimento, pois o **modelo renderizado** fornecido pelo Windows para um controlador de movimento usa a alça de pose como sua origem e o centro de rotação.

A pose de alça é definida especificamente da seguinte maneira:
* A **posição de alça**: o Palm centróide ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralizar a posição dentro da alça. No controlador de movimento de realidade mista do Windows, essa posição geralmente se alinha com o botão compreender.
* O **eixo direito da orientação de alça**: quando você abre completamente a mão para formar uma pose plana de 5 dedos, o raio normal para o Palm (para frente do Palm esquerdo, para trás do Palm direito)
* O **eixo de encaminhamento da orientação de alça**: quando você fecha a sua mão parcialmente (como se você mantiver o controlador), o raio que aponta para "encaminhar" por meio do tubo formado por seus dedos não-thumbs.
* O **eixo superior da orientação de alça**: o eixo superior implícito pelas definições direita e avançar.

### <a name="pointer-pose"></a>Pose de ponteiro

A **pose do ponteiro** representa a ponta do controlador que está apontando para frente.

A pose de ponteiro fornecida pelo sistema é mais bem usada para Raycast quando você está **renderizando o próprio modelo de controlador**. Se você estiver renderizando algum outro objeto virtual no lugar do controlador, como uma arma virtual, você deve apontar com um raio mais natural para esse objeto virtual, como um Ray que viaja ao longo do cilindro do modelo de pressão definido pelo aplicativo. Como os usuários podem ver o objeto virtual e não o controlador físico, apontar com o objeto virtual provavelmente será mais natural para aqueles que usam seu aplicativo.

## <a name="controller-tracking-state"></a>Estado de controle do controlador

Assim como os headsets, o controlador de movimento do Windows Mixed Reality não requer nenhuma configuração de sensores de controle externo. Em vez disso, os controladores são acompanhados por sensores no próprio headset.

Se o usuário mover os controladores para fora do campo de exibição do headset, na maioria dos casos, o Windows continuará inferindo as posições do controlador e as fornecerá ao aplicativo. Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada.

Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna. Muitos aplicativos que usam controladores para apontar e ativar elementos de interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a>Raciocínio sobre o estado de rastreamento explicitamente

Os aplicativos que desejam tratar as posições de forma diferente com base no estado de controle podem ir além e inspecionar as propriedades no estado do controlador, como SourceLossRisk e PositionAccuracy:

<table>
<tr>
<th> Estado de acompanhamento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Alta precisão</b> </td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Alta </td><td style="background-color: green; color: white"> verdadeiro</td>
</tr><tr>
<td> <b>Alta precisão (com risco de perda)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Alta </td><td style="background-color: green; color: white"> verdadeiro</td>
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
* **Sem posição:** Embora o controlador possa operar com precisão aproximada por um longo tempo, às vezes o sistema sabe que até mesmo uma posição bloqueada pelo corpo não é significativa no momento. Por exemplo, um controlador que acabou de ser ativado pode nunca ter sido observado visualmente ou um usuário pode colocar um controlador selecionado por outra pessoa. Naqueles momentos, o sistema não fornecerá nenhuma posição para o aplicativo e **TryGetPosition** retornará false.

## <a name="interactions-low-level-spatial-input"></a>Interações: entrada espacial de nível baixo

As interações principais entre os controladores de mãos e de movimento são **Select**, **menu**, **Segure**, **Touchpad**, **Thumbstick**e **Home**.
* **Select** é a principal interação para ativar um holograma, que consiste em uma prensa seguida por uma versão. Para os controladores de movimento, você executa uma operação SELECT usando o gatilho do controlador. Outras maneiras de executar uma seleção são falando sobre o [comando de voz](voice-input.md) "Select". A mesma interação SELECT pode ser usada em qualquer aplicativo. Considere Select como o equivalente a um clique do mouse; uma ação universal que você aprende uma vez e, em seguida, se aplica em todos os seus aplicativos.
* O **menu** é a interação secundária para atuar em um objeto, usado para efetuar pull de um menu de contexto ou executar alguma outra ação secundária. Com os controladores de movimento, você pode executar uma ação de menu usando o botão de *menu* do controlador. (ou seja, o botão com o ícone de "menu" de "p")
* **Segure** é como os usuários podem agir diretamente em objetos à sua disposição para manipulá-los. Com os controladores de movimento, você pode fazer uma ação compreender apertando seu punho. Um controlador de movimento pode detectar um entendimento com um botão de captura, um gatilho de Palm ou outro sensor.
* O **Touchpad** permite que o usuário ajuste uma ação em duas dimensões ao longo da superfície do Touchpad de um controlador de movimento, confirmando a ação clicando no Touchpad. Os touchpads fornecem um estado pressionado, coordenadas de estado tocado e normalizadas. Intervalo X e Y de-1 a 1 no intervalo do Touchpad circular, com um centro em (0, 0). Para X,-1 está à esquerda e 1 está à direita. Para Y,-1 está na parte inferior e 1 está na parte superior.
* O **Thumbstick** permite que o usuário ajuste uma ação em duas dimensões movendo o Thumbstick de um controlador de movimento dentro de seu intervalo circular, confirmando a ação clicando em baixo no Thumbstick. Thumbsticks também fornece um estado pressionado e coordenadas XY normalizadas. Intervalo X e Y de-1 a 1 no intervalo do Touchpad circular, com um centro em (0, 0). Para X,-1 está à esquerda e 1 está à direita. Para Y,-1 está na parte inferior e 1 está na parte superior.
* **Home** é uma ação especial do sistema que é usada para voltar ao menu iniciar. É semelhante a pressionar a tecla Windows em um teclado ou o botão Xbox em um controlador Xbox. Você pode ir para casa pressionando o botão Windows em um controlador de movimento. Observe que você sempre pode retornar para começar dizendo "Ei Cortana, Go Home". Os aplicativos não podem reagir especificamente às ações iniciais, pois elas são manipuladas pelo sistema.

## <a name="composite-gestures-high-level-spatial-input"></a>Gestos compostos: entrada espacial de alto nível

Os [gestos à mão](gaze-and-commit.md#composite-gestures) e os controladores de movimento podem ser acompanhados ao longo do tempo para detectar um conjunto comum de **[gestos compostos](gaze-and-commit.md#composite-gestures)** de alto nível. Isso permite que seu aplicativo detecte gestos de **toque**, **retenção**, **manipulação** e **navegação** de alto nível, se os usuários acabarem usando mãos ou controladores.

## <a name="rendering-the-motion-controller-model"></a>Renderizando o modelo do controlador de movimento

**modelos de controlador 3D** O Windows disponibiliza para aplicativos um modelo renderizado de cada controlador de movimento atualmente ativo no sistema. Ao fazer com que seu aplicativo carregue e articule dinamicamente esses modelos de controlador fornecidos pelo sistema em tempo de execução, você pode garantir que seu aplicativo seja compatível com todos os designs futuros do controlador.

Esses modelos processáveis devem ser renderizados na **pose de alça** do controlador, pois a origem do modelo é alinhada com esse ponto no mundo físico. Se você estiver renderizando modelos de controlador, você pode querer Raycast em sua cena na **pose do ponteiro**, que representa o raio ao longo do qual os usuários serão naturalmente informados, considerando o design físico do controlador.

Para obter mais informações sobre como carregar modelos de controlador dinamicamente no Unity, consulte a seção [renderizando o modelo de controlador de movimento no Unity](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity) .

**arte de linhas do controlador 2D** Embora seja recomendável anexar as dicas e comandos do controlador no aplicativo aos próprios modelos do App Controller, alguns desenvolvedores podem querer usar representações de arte de linha 2D dos controladores de movimento em interface "tutorial" simples ou "instruções". Para esses desenvolvedores, fizemos. arquivos de arte de linha do controlador de animação png disponíveis em preto e branco abaixo (clique com o botão direito do mouse para salvar).

![Visualização da arte de linhas de controladores de movimento](images/motioncontrollers-black-preview-300px.png)

[Controladores de movimento de resolução completa de linha artística em ' ' ' branco ' ' '](images/motioncontrollers-white.png)
 
[Controladores de movimento de resolução completa de linha artística em ' ' ' preto ' ' '](images/motioncontrollers-black.png)

## <a name="faq"></a>Perguntas frequentes

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>Posso emparelhar os controladores de movimento com vários PCs?

Os controladores de movimento dão suporte ao emparelhamento com um único PC. Siga as instruções na [configuração do controlador de movimento](motion-controllers.md#setup) para emparelhar seus controladores.

### <a name="how-do-i-update-motion-controller-firmware"></a>Como fazer atualizar o firmware do controlador de movimento?

O firmware do controlador de movimento faz parte do driver do headset e será atualizado automaticamente na conexão, se necessário. As atualizações de firmware geralmente levam 1-2 minutos, dependendo da qualidade do link e da rádio do Bluetooth. Em casos raros, as atualizações de firmware do controlador podem levar até 10 minutos, o que pode indicar pouca conectividade Bluetooth ou interferência de rádio. Consulte [práticas recomendadas de Bluetooth no guia de entusiasta](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) para solucionar problemas de conectividade. Depois de uma atualização de firmware, os controladores serão reinicializados e reconectados ao PC host (você pode notar que os LEDs são mais brilhantes para acompanhamento). Se uma atualização de firmware for interrompida (por exemplo, os controladores perderão energia), ela será tentada novamente na próxima vez em que os controladores estiverem ligados.

### <a name="how-i-can-check-battery-level"></a>Como posso verificar o nível da bateria?

Na [página inicial do Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md), você pode transformar seu controlador para ver seu nível de bateria no lado inverso do modelo virtual. Não há indicador de nível de bateria física.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>Você pode usar esses controladores sem um headset? Apenas para a entrada joystick/Trigger/etc?

Não para aplicativos universais do Windows.

## <a name="troubleshooting"></a>Painel de controle da

Consulte [solução de problemas do controlador de movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) no guia de entusiasta.

## <a name="filing-motion-controller-feedbackbugs"></a>Arquivando comentários/bugs do controlador de movimento

[Envie-nos comentários](give-us-feedback.md) no Hub de comentários usando a categoria "realidade misturada-> entrada".

## <a name="see-also"></a>Veja também
* [Gestos e controladores de movimento no Unity](gestures-and-motion-controllers-in-unity.md)
* [Controladores de mãos e emovimento no DirectX](hands-and-motion-controllers-in-directx.md)
* [Gestos](gaze-and-commit.md#composite-gestures)
* [Entrada MR 213: controladores de movimento](mixed-reality-213.md)
* [Guia de entusiastas: sua página inicial do Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [Guia de entusiastas: usando jogos & aplicativos no Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [Como funciona o acompanhamento interno](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
