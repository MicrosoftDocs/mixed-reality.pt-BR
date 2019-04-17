---
title: Controladores de movimento
description: Obter detalhes sobre os controladores de movimento de realidade misturada.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof controladores, controladores de movimento
ms.openlocfilehash: b44964ab872bd080349ecf1b04b3f7082b521a24
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590992"
---
# <a name="motion-controllers"></a>Controladores de movimento

Controladores de movimento [Acessórios de hardware](hardware-accessories.md) que permitem aos usuários executar a ação em realidade misturada. Uma vantagem dos controladores de movimento ao longo [gestos](gestures.md) é que os controladores têm uma posição precisa no espaço, permitindo refinada interação com objetos digitais. Para Windows Mixed Reality fones imersivos em exposição, controladores de movimento são a principal maneira de que os usuários terão a ação no seu mundo.

![Controladores de movimento de realidade mista do Windows](images/winmr-ck-1080x1080-350px.jpg)


## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> Controladores de movimento</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>Detalhes de hardware

>[!VIDEO https://www.youtube.com/embed/1nlcdDNOdm8]

Controladores de movimento do Windows Mixed Reality oferecem controle preciso e responsivo de movimentação em seu campo de exibição usando os sensores o Headset imersivo, que significa que não é necessário para instalar o hardware nas paredes em seu espaço de. Esses controladores de movimento oferecerá a mesma facilidade de instalação e portabilidade como fones imersivos em exposição realidade mista do Windows. Nossos parceiros de dispositivo pretende comprar e vender este feriado desses controladores em prateleiras de varejo.

![Conheça o seu controlador](images/controllerimage-750px.png)<br>
*Conheça o seu controlador*

**Recursos:**
* Acompanhamento de mídia óptico
* gatilho
* Botão de captura
* Direcional
* Touchpad

## <a name="setup"></a>Configuração

### <a name="before-you-begin"></a>Antes de começar

**Você precisará:**
* Um conjunto de dois controladores de movimento.
* Quatro baterias de AA.
* Um computador capaz de Bluetooth 4.0.

**Verificar se há atualizações do Windows, o Unity e o driver**
* Visite [instalar as ferramentas](install-the-tools.md) para as versões preferenciais do Windows, Unity, etc. para o desenvolvimento de realidade misturada.
* Verifique se você tem mais atualizadas [drivers de controlador fone de ouvido e movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software).

### <a name="pairing-controllers"></a>Controladores de emparelhamento

Controladores de movimento podem ser acoplados a PC host usando as configurações do Windows, como qualquer outro dispositivo Bluetooth.

1. Insira 2 baterias de AA na parte traseira do controlador. Omite a tampa de bateria por enquanto.
2. Se você estiver usando um adaptador de Bluetooth USB externo em vez de um rádio Bluetooth internos, consulte o [práticas recomendadas de Bluetooth](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) antes de continuar. Para a configuração da área de trabalho com a opção interna, verifique se a antena está conectada.
3. Abra **configurações do Windows** -> **dispositivos** -> **adicionar Bluetooth ou outro dispositivo** -> **Bluetooth** e remova todas as instâncias anteriores do "Motion controlador – à direita" e "Movimento controlador – à esquerda". Verifique também a outra categoria de dispositivos na parte inferior da lista.
4. Selecione **adicionar Bluetooth ou outro dispositivo** e vê-lo começando a descobrir os dispositivos Bluetooth.
5. Pressione e segure o botão do Windows do controlador para ligar o controlador, libere uma vez buzzes.
6. Pressione e mantenha pressionado o botão de emparelhamento (guia no compartimento de bateria) até que os LEDs começam pulso.
7. Aguarde "Movimento controlador - esquerda" ou "Controlador de movimento - Right" seja exibido na parte inferior da lista. Selecione a par. Quando conectado, o controlador será Vibrar uma vez.

   ![Selecione o controlador de movimento para o par, se várias instâncias de selecionar uma opção do aparecendo inferior da lista](images/450px-bluetooth-add-a-device-300px.png)<br>
   *Selecione "Controlador de movimento" ao par; Se houver várias instâncias, selecione um na parte inferior da lista*
   
8. Você verá que o controlador exibido nas configurações do Bluetooth em **"Mouse, teclado e caneta" categoria** como **conectado**. Neste ponto, você poderá receber uma atualização de firmware – consulte [próxima seção](motion-controllers.md#updating-controller-firmware).
9. Reconecte tampa da bateria.
10. Repita as etapas 1 a 9 para o segundo controlador.

Após o emparelhamento com êxito os dois controladores, suas configurações devem ser assim sob **"Mouse, teclado e caneta" categoria** 

   ![Controladores de movimento conectados](images/450px-motion-controller-connected-300px.png)<br>
   *Controladores de movimento conectados*

Se os controladores são desativados após o emparelhamento, seu status mostrará como emparelhados. Se os controladores permanentemente permanecem sob "Outros dispositivos de" emparelhamento de categoria pode ter sido apenas parcialmente concluída e precisa ser executado novamente para obter o controlador funcional.

### <a name="updating-controller-firmware"></a>Atualização do firmware do controlador

* Se um fone de ouvido imersivo é conectado ao seu computador e novo firmware do controlador está disponível, o firmware será enviado aos controladores de movimento automaticamente na próxima vez em que estão ligados. Atualizações de firmware do controlador são indicadas por um padrão de pois resolvem quadrantes de LED em um movimento circular e levar de 1 a 2 minutos.
* Após a atualização de firmware, os controladores serão reinicializar e reconecte. Ambos os controladores devem estar conectados agora. 
    
    ![Controladores conectados](images/cyk-connected-300px.jpg)<br>
    *Controladores conectados nas configurações de Bluetooth*

* Verifique se o seu trabalho controladores corretamente:
    1. Inicie **Portal de realidade misturada** e insira sua casa de realidade mista.
    2. Mover seus controladores e verifique se o rastreamento, botões de teste e verifique se [teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) funciona. Se eles não fizer isso, em seguida, confira [solução de problemas do controlador de movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers).

## <a name="gazing-and-pointing"></a>Observação e apontando

Realidade mista do Windows oferece suporte a dois modelos principais para interação, **olhares e confirmar** e **aponte e confirmar**:
* Com **olhares e confirmar**, os usuários de destino um objeto com seus [olhares](gaze.md) e, em seguida, selecione objetos com ar-toques de mão, um gamepad, um clicker ou pela voz.
* Com o **aponte e confirmar**, um usuário pode ter como objetivo um controlador de movimento com capacidade a apontando para o objeto de destino e, em seguida, selecione objetos com o gatilho do controlador.

Aplicativos que suporte apontando com controladores de movimento também deve habilitam interações controladas olhar sempre que possível, para dar aos usuários escolha no qual os dispositivos que usam de entrada.

### <a name="managing-recoil-when-pointing"></a>Gerenciando recoil quando apontando

Ao usar controladores de movimento de ponto e confirmar, seus usuários usará o controlador de destino e, em seguida, tomar atitudes puxando seu gatilho. Os usuários que o gatilho de pull agressiva podem acabar com o objetivo de controlador superior no final de seu pull de gatilho que tinha a intenção.

Para gerenciar tal recoil que pode ocorrer quando o gatilho de pull de usuários, seu aplicativo pode ajustar seu direcionamento ray quando o valor de eixo analógica do disparador sobe acima 0,0. Você pode adotar a ação usando que ray direcionamento alguns quadros mais tarde quando o valor do gatilho atinge 1.0, desde que o toque final ocorre dentro de um período curto. Ao usar o nível mais alto [gestos de toque de composição](gestures.md#composite-gestures), Windows irá gerenciar isso direcionando ray captura e o tempo limite para você.

## <a name="grip-pose-vs-pointing-pose"></a>Alça pose versus pose apontador

Realidade mista do Windows oferece suporte a controladores de movimento em uma variedade de fatores forma, com o design de cada controlador difere em sua relação entre a posição do usuário mão e natural "encaminhar" direção que aplicativos deve usar para apontando ao renderizar o controlador.

Para melhor representar esses controladores, há dois tipos de poses, você pode investigar para cada fonte de interação, o **alça pose** e o **pose ponteiro**.

### <a name="grip-pose"></a>Alça pose

O **alça pose** representa o local de palma da mão detectada por um HoloLens ou palma mantendo um controlador de animação.

Em fones imersivos em exposição, a alça pose é melhor usada para renderizar **mão do usuário** ou **um objeto é mantido em mãos do usuário**, como uma espada ou elétrons. A alça pose também é usada quando visualizando um controlador de animação, como o **que podem ser renderizado modelo** fornecida pelo Windows para um movimento controlador usa a alça pose como sua origem e o Centro de rotação.

A alça pose é definida especificamente da seguinte maneira:
* O **segure posição**: O centroide de palm pressionando o controlador naturalmente, ajustado esquerda ou direita para centralizar a posição dentro a alça. No controlador de animação do Windows Mixed Reality, essa posição geralmente se alinha com o botão de compreensão.
* O **Segure o eixo à direita da orientação**: Quando você abre completamente sua mão para formar uma dedo simples 5 pose, raio que é normal para o palm (para a frente da esquerda palm, com versões anteriores do palm à direita)
* O **Segure o eixo de encaminhamento da orientação**: Quando você fecha sua mão parcialmente (como se que mantém o controlador), o raio que aponta "forward" por meio de tubo formado por seus dedos não thumb.
* O **segure orientação backup eixo**: O eixo de cima indicado pelas definições de direito e Avançar.

### <a name="pointer-pose"></a>Ponteiro pose

O **ponteiro pose** representa a dica do controlador que aponta para a frente.

O ponteiro fornecido pelo sistema pose é melhor usado para raycast quando você estiver **Renderizando o próprio modelo de controlador**. Se você estiver renderizando algum outro objeto virtual no lugar do controlador, como um de elétrons virtual, você deve apontar com um raio que seja mais natural para esse objeto virtual, como um raio que viaja ao longo do corpo do modelo de elétrons definidas pelo aplicativo. Porque os usuários podem ver o objeto virtual e não o controlador de físico, que aponta para ao objeto virtual provavelmente será mais natural para aqueles que usam seu aplicativo.

## <a name="controller-tracking-state"></a>Estado do controlador de rastreamento

Como fones de ouvido, o controlador de animação do Windows Mixed Reality não exige nenhuma configuração de sensores de controle externo. Em vez disso, os controladores são controlados pelos sensores no fone de ouvido em si.

Se o usuário move os controladores de exibição de campo do fone de ouvido, na maioria dos casos Windows continuará inferir posições de controlador e fornecê-los para o aplicativo. Quando o controlador perdeu visual de acompanhamento de tempo suficiente, posições do controlador descartará a precisão aproximados posições.

Neste ponto, o sistema será o bloqueio de corpo de controlador para o controle do usuário, a posição do usuário conforme eles se movimentam, enquanto ainda expor orientação true do controlador, usando seus sensores de orientação interna. Muitos aplicativos que usam controladores de apontar e ativar os elementos de interface do usuário podem operar normalmente enquanto estiver em precisão aproximado sem perceber o usuário.

&nbsp;

>[!VIDEO https://www.youtube.com/embed/rkDpRllbLII]

### <a name="reasoning-about-tracking-state-explicitly"></a>Pensando sobre explicitamente o estado de controle

Aplicativos que deseja tratar as posições de maneira diferente com base no estado de controle podem ir além e inspecione as propriedades no estado do controlador, como SourceLossRisk e PositionAccuracy:

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
* **Nenhuma posição:** Enquanto o controlador pode operar em precisão aproximado por um longo tempo, às vezes, o sistema sabe que até mesmo uma posição bloqueada de corpo não é significativa no momento. Por exemplo, um controlador que foi ativado apenas talvez nunca foram observado visualmente, ou um usuário pode colocar para baixo de um controlador que é capturado por outra pessoa. Nesses momentos, o sistema não fornecerá qualquer posição para o aplicativo, e **TryGetPosition** retornará false.

## <a name="interactions-low-level-spatial-input"></a>Interações de: Entrada espacial de baixo nível

São as interações de núcleo em mãos e controladores de movimento **selecionar**, **Menu**, **segure**, **Touchpad**,  **Direcional**, e **Home**.
* **Selecione** é a interação primária para ativar um holograma, consistindo de um pressionamento seguido por uma versão. Para controladores de movimento, você deve executar um pressionamento de Select usando o disparador do controlador. Outras maneiras de executar uma seleção estão falando a [comando de voz](voice-input.md) "Select". A interação de select mesma pode ser usada em qualquer aplicativo. Pense selecione como o equivalente a um mouse clique em uma ação universal que você saiba mais uma vez e, em seguida, aplicar em todos os seus aplicativos.
* **Menu** é a interação secundária para atuar em um objeto usado para extrair um menu de contexto ou executar alguma outra ação secundária. Com os controladores de movimento, você pode executar uma ação de menu usando o controlador *menu* botão. (ou seja, o botão com o ícone de "menu" hambúrguer nele)
* **Segure** é como os usuários diretamente podem tomar medidas em objetos em sua mão para manipulá-los. Com os controladores de movimento, você pode fazer uma ação de compreensão, apertando zangados rigidamente. Um controlador de movimento pode detectar uma melhor compreensão com um botão de captura, o gatilho palm ou outro sensor.
* **Touchpad** permite que o usuário ajuste uma ação em duas dimensões junto a superfície de touchpad do controlador um movimento, confirmar a ação clicando no teclado. Touchpads fornecem um estado pressionado, tocadas e coordenadas XY do normalizado. Intervalo de X e Y de -1 para 1 entre as várias o touchpad circular, com um centro em (0, 0). Para X, -1 é à esquerda e 1 é à direita. Para Y, -1 é na parte inferior e 1 é na parte superior.
* **Direcional** permite que o usuário ajuste uma ação em duas dimensões, movendo analógico do controlador um movimento de seu intervalo circular, confirmar a ação clicando no analógico. Alavancas direcionais também fornecem um estado pressionado e normalizados coordenadas XY. Intervalo de X e Y de -1 para 1 entre as várias o touchpad circular, com um centro em (0, 0). Para X, -1 é à esquerda e 1 é à direita. Para Y, -1 é na parte inferior e 1 é na parte superior.
* **Página inicial** é uma ação de sistema especial que é usada para retornar ao Menu Iniciar. Ele é semelhante a pressionar a tecla do Windows em um teclado ou o botão do Xbox em um controlador do Xbox. Você pode ir para casa, pressionando o botão do Windows em um controlador de animação. Observe que você também sempre pode retornar ao início dizendo "Ei Cortana, Go Home". Aplicativos não é possível reagir especificamente a ação inicial, como elas são tratadas pelo sistema.

## <a name="composite-gestures-high-level-spatial-input"></a>Gestos de composição: Entrada espacial de alto nível

Ambos [gestos de mão](gestures.md) e controladores de movimento podem ser acompanhados ao longo do tempo para detectar um conjunto comum de alto nível  **[gestos compostos](gestures.md#composite-gestures)**. Isso permite que seu aplicativo detectar um alto nível **toque**, **mantenha**, **manipulação** e **navegação** gestos, se os usuários acabam usando mãos ou controladores.

## <a name="rendering-the-motion-controller-model"></a>O modelo de controlador de movimento de renderização

**Modelos 3D controlador** Windows torna disponível para aplicativos que podem ser renderizado modelo de cada controlador de animação atualmente ativos no sistema. Fazendo com que seu aplicativo carregar dinamicamente e articular esses modelos de controlador fornecido pelo sistema em tempo de execução, você pode garantir o que seu aplicativo seja designs de compatibilidade para um futuro controlador.

Esses modelos que podem ser renderizados devem ser renderizados na **alça pose** do controlador, como a origem do modelo é alinhada com esse ponto no mundo físico. Se você estiver processando os modelos de controlador, em seguida, convém raycast na sua cena do **ponteiro pose**, que representa o raio ao longo do qual os usuários naturalmente passarão a ponto, considerando o design físico do controlador em questão.

Para obter mais informações sobre como carregar modelos de controlador dinamicamente no Unity, consulte o [Renderizando o modelo de controlador de animação no Unity](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity) seção.

**Arte de linhas de controlador 2D** Embora seja recomendável anexando dicas de controlador no aplicativo e comandos para os próprios modelos de controlador no aplicativo, alguns desenvolvedores talvez queira usar representações de arte de linhas 2D dos controladores de movimento em simples "tutorial" ou "como fazer" INTERFACE DO USUÁRIO. Para os desenvolvedores, fizemos arquivos. PNG movimento controlador linha arte disponíveis em ambos os preto e branco abaixo (clique com botão direito para salvar).

![Visualização da arte de linhas de controladores de movimento](images/motioncontrollers-black-preview-300px.png)

 [Controladores de movimento de alta resolução traço em ' ' branco ' '](images/motioncontrollers-white.png)
 
 [Controladores de movimento de alta resolução traço em ' ' preto ' '](images/motioncontrollers-black.png)

## <a name="faq"></a>Perguntas frequentes

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>Eu par motion controladores a vários PCs?

Controladores de movimento suportam o emparelhamento com um único PC. Siga as instruções [instalação do controlador de movimento](motion-controllers.md#setup) emparelhar seus controladores.

### <a name="how-do-i-update-motion-controller-firmware"></a>Como atualizar o firmware do controlador de animação?

Firmware de controlador de movimento é parte do driver fone de ouvido e será atualizado automaticamente na conexão se necessário. Atualizações de firmware geralmente levam 1 a 2 minutos, dependendo da qualidade de rádio e link do Bluetooth. Em casos raros, as atualizações de firmware de controlador podem levar até 10 minutos, que podem indicar a conectividade de Bluetooth ruim ou interferência de rádio. Consulte [práticas recomendadas de Bluetooth no guia de entusiasta](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) para solucionar problemas de conectividade. Após uma atualização de firmware, controladores serão seja reinicializado e reconectar-se ao host do computador (você pode observar os LEDs vá brilhante para acompanhamento). Se uma atualização de firmware for interrompida (por exemplo, os controladores de queda de energia), ela será tentada novamente na próxima vez em que os controladores estiverem ligados.

### <a name="how-i-can-check-battery-level"></a>Como posso verificar o nível de bateria?

No [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md), você pode virar seu controlador para ver seu nível de bateria no lado oposto do modelo virtual. Há um indicador de nível de bateria físico.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>Você pode usar esses controladores sem um fone de ouvido? Apenas para a entrada de joystick/gatilho/etc.?

Não para aplicativos Windows Universal.

## <a name="troubleshooting"></a>Solução de problemas

Ver [solução de problemas do controlador de movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) no guia de entusiasta.

## <a name="filing-motion-controller-feedbackbugs"></a>Arquivar movimento controlador comentários/bugs

[Envie seus comentários](give-us-feedback.md) no Hub de comentários, usando a categoria "Realidade misturada -> entrada".

## <a name="see-also"></a>Consulte também
* [Gestos e controladores de movimento no Unity](gestures-and-motion-controllers-in-unity.md)
* [Olhar, gestos e controladores de movimento no DirectX](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [Gestos](gestures.md)
* [Entrada MR 213: Controladores de movimento](mixed-reality-213.md)
* [Guia do entusiasta: O Windows Mixed Reality inicial](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [Guia do entusiasta: Usando aplicativos e jogos no Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [Como funciona o controle de dentro para fora](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
