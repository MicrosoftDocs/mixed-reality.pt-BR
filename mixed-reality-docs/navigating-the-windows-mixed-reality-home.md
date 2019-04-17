---
title: Navegando o Windows Mixed Reality inicial
description: HoloLens e o Windows Mixed Reality headsets compartilham um paradigma para iniciar, colocar e manipular modelos 3D em seu ambiente e aplicativos (seja físico ou digital). Saiba como navegar o Windows Mixed Reality inicial em ambos os tipos de dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Shell, sistema operacional, plataforma, casa cliff, casa, home, ambiente, iniciar, menu Iniciar, menu inicial, pins, aplicativo, aplicativos de inicialização, coloque aplicativos, ser transportado, mover, navegue até
ms.openlocfilehash: 1ca6dd66506a64ad2e1c21870fee2725ddf20bd8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590979"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Navegando o Windows Mixed Reality inicial

Assim como a experiência de PC do Windows é iniciado com a área de trabalho, Windows Mixed Reality começa com a página inicial. O Windows Mixed Reality doméstica aproveita nossa capacidade inata de compreender e navegar lugares 3D. Com o HoloLens, sua página inicial é o espaço físico. Com fones imersivos em exposição, sua página inicial é um lugar virtual.

Sua casa também é onde você usará o menu Iniciar para abrir e colocar aplicativos e conteúdo. Você pode preencher sua casa com conteúdo de realidade mista e multitarefa com o uso de vários aplicativos ao mesmo tempo. As coisas que você coloca na sua casa permanecem lá, mesmo se você reiniciar seu dispositivo.

## <a name="start-menu"></a>Menu Iniciar

![Menu Iniciar no Microsoft HoloLens](images/start-500px.png)

No menu Iniciar consiste em:
* Informações do sistema (status da rede, porcentagem de bateria, hora atual e volume)
* Cortana (no fones imersivos em exposição, um bloco de início; no HoloLens, na parte superior de início)
* Aplicativos fixados
* Botão de todos os aplicativos (sinal de adição)
* Botões de fotos e vídeos para [misto captura realidade](mixed-reality-capture.md)

Alternar entre os aplicativos fixados e todos os aplicativos de modos de exibição, selecionando o sinal de mais ou menos botões. Para abrir o menu Iniciar no HoloLens, use o gesto de bloom. Em um fone de ouvido imersivo, pressione o botão do Windows em seu controlador.

## <a name="launching-apps"></a>Inicialização de aplicativos

Para iniciar um aplicativo, selecione-o no início. No menu Iniciar desaparecerá, e o aplicativo será aberto no modo de posicionamento, como uma janela de 2D ou um [modelo 3D](implementing-3d-app-launchers.md).

Para executar o aplicativo, você precisará colocá-lo, em seguida, em casa:
1. Use sua [olhares](gaze.md) ou controlador para posicionar o aplicativo no qual você deseja. Ele se ajustará automaticamente (no tamanho e posição) de acordo com o espaço onde colocá-lo.
2. Coloque o aplicativo usando o polegar (HoloLens) ou o botão de seleção (fones imersivos em exposição). Para cancelar e trazer de volta no menu Iniciar, use o gesto de bloom ou o botão do Windows.

[Aplicativos 2D](building-2d-apps.md), criado para a área de trabalho, móvel, ou Xbox pode ser modificado para serem executados como aplicativos envolventes de realidade misturada usando o [HolographicSpace API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx). Um aplicativo de imersão leva o usuário para fora a página inicial e para uma experiência imersiva. Os usuários podem retornar início com o gesto de bloom (HoloLens), ou pressionando o botão do Windows em seu controlador (fones imersivos em exposição).

Aplicativos também podem ser iniciados por meio de uma aplicativo para API ou Cortana.

![Aplicativos no Windows Mixed Reality inicial](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Movendo e ajuste de aplicativos

Selecione **ajustar** no aplicativo barra para revelar controla que você mova, escala e girar de conteúdo de realidade mista. Quando tiver terminado, selecione **feito**.

![O slate de armazenamento no modo de ajuste (quadro azul). Observe a barra de aplicativo (superior) foi alterado para incluir 'Concluído' e 'Remover' botões.](images/adjust-500px.png)

Os aplicativos diferentes podem ter opções adicionais na barra de aplicativos. Por exemplo, tem o Microsoft Edge *rolagem*, *arraste*, e *Zoom* escolhas. 

![Barra de aplicativo para 2D aplicativos executados em HoloLens](images/holobar-500px.png)

O **volta** botão navega para telas exibidas anteriormente no aplicativo. Ele será interrompido quando você atingir o início das experiências que foram mostradas no aplicativo e não vai navegar para outros aplicativos.

## <a name="getting-around-your-home"></a>Introdução ao redor de sua casa

Com o **HoloLens**, percorrer o espaço físico para mover em torno de sua casa.

Com o **fones imersivos em exposição**, da mesma forma, você pode começar a trabalhar e sair andando seu playspace para movimentação dentro de uma área semelhante no mundo virtual. Para mover entre distâncias mais longas, você pode usar o analógico em seu controlador virtualmente "caminhar", ou você pode usar *teleportation* para saltar imediatamente distâncias mais longas.

![Teleportation no Windows Mixed Reality inicial](images/teleportation-500px.png)

**Para ser transportado:**
1. Ative o reticle teleportation.
   * Usando o [controladores de movimento](motion-controllers.md): pressione o analógico para frente e mantê-los nessa posição.
   * Usando um controlador do Xbox: pressione o analógico esquerdo para frente e mantê-los nessa posição.
   * Usando um mouse: mantenha pressionado o botão direito do mouse (e use a roda de rolagem para girar a direção em que você deseja enfrentam quando você ser transportado).
2. Coloque o reticle onde você deseja ser transportado.
   * Usando o [controladores de movimento](motion-controllers.md): inclinar o controlador (no qual você estiver mantendo o analógico para frente) para mover o reticle.
   * Usando um controlador do Xbox: usar seu [olhares](gaze.md) para mover o reticle.
   * Usando um mouse: mova o mouse para mover o reticle.
3. Solte o botão a ser transportado onde o reticle foi colocado.

**Para praticamente "percorrer:"**
* Usando o [controladores de movimento](motion-controllers.md): para baixo o analógico e manter pressionado, clique no mover a alavanca direcional na direção desejada para "conduzir".
* Usando um controlador do Xbox: clique para baixo no analógico esquerdo e mantenha e mover o analógico na direção desejada para "conduzir".

## <a name="immersive-headset-input-support"></a>Suporte à entrada de imersão fone de ouvido

[Fones imersivos em exposição Windows Mixed Reality](immersive-headset-hardware-details.md) dar suporte a vários tipos de entrada para o Windows Mixed Reality inicial de navegação. HoloLens não oferece suporte Acessórios entradas para navegação, porque você fisicamente vai e ver o seu ambiente. No entanto, faz o HoloLens [dá suporte a entradas](hardware-accessories.md) para interagir com os aplicativos.

### <a name="motion-controllers"></a>Controladores de movimento

Será a melhor experiência de realidade mista do Windows com o Windows Mixed Reality [controladores de movimento](motion-controllers.md) esse acompanhamento de 6 graus de liberdade de suporte usando apenas os sensores em fone de ouvido - nenhuma câmeras externas ou marcadores necessárias!

Comandos de navegação em breve.

### <a name="gamepad"></a>Gamepad
* **Analógico esquerdo:**
  * Pressione e segure para frente o analógico esquerdo para abrir o [teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) reticle.
  * Toque o analógico left, right, de volta para mover para a esquerda, direita ou de volta em pequenos incrementos.
  * Clique para baixo no analógico esquerdo e mantenha e mover o analógico na direção em que você deseja [praticamente "caminhar".](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Toque o **alavanca direcional direita** esquerda ou direita para girar a direção em que você está enfrentando em 45 graus.
* Pressionar o **um** botão executa select e age como o [polegar](gestures.md#air-tap) gesto.
* Pressionar o **guia de** botão abre a [menu Iniciar](navigating-the-windows-mixed-reality-home.md#start-menu) e age como o [bloom](gestures.md#bloom) gesto.
* Pressionar o **gatilhos left e right** permite que você aplicar zoom para dentro e fora de um aplicativo da área de trabalho 2D, você está interagindo com em casa.

### <a name="keyboard-and-mouse"></a>Teclado e mouse

**Observação:** Use **tecla Windows + Y** para alternar o mouse entre controlando a área de trabalho do seu PC e o Windows Mixed Reality inicial.

Dentro do Windows Mixed Reality inicial:
* Pressionar o **botão esquerdo do mouse** botão do mouse executa select e age como o [polegar](gestures.md#air-tap) gesto.
* Mantendo os **com o botão direito** botão do mouse abre o [teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) reticle.
* Pressionar o **Windows** tecla no teclado abrirá o [Menu Iniciar](navigating-the-windows-mixed-reality-home.md#start-menu) e age como o [bloom](gestures.md#bloom) gesto.
* Quando [Observação](gaze.md) em um aplicativo de área de trabalho 2D, você pode **botão esquerdo do mouse** para selecionar, **com o botão direito** para exibir menus de contexto e usar o **roda de rolagem** a rolagem (assim como na área de trabalho do seu PC).

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana) é o seu assistente pessoal na realidade mista do Windows, como em PC e telefone. HoloLens tem um microfone interno, mas fones imersivos em exposição pode exigir hardware adicional. Use a Cortana para abrir aplicativos, reiniciar seu dispositivo, procurar coisas online e muito mais. Os desenvolvedores também podem optar por [integrar o Cortana](https://dev.windows.com/cortana) em suas experiências.

Você também pode usar comandos de voz para resolver sua casa. Por exemplo, aponte para um botão (usando [olhares](gaze.md) ou um controlador, dependendo do dispositivo) e dizer "Select". Outros comandos de voz incluem "Go home", "Maior", "menor," "Fechar" e "Enfrentam me".

## <a name="store-settings-and-system-apps"></a>Aplicativos de sistema, configurações e Store

Realidade mista do Windows tem um número de aplicativos internos, tais como:
* **Microsoft Store** para obter aplicativos e jogos
* **Hub de comentários** enviar comentários sobre o sistema e aplicativos do sistema
* **As configurações** para definir configurações do sistema ([inclusive redes](connecting-to-wi-fi-on-hololens.md) e atualizações do sistema)
* **Microsoft Edge** para navegar em sites
* **Fotos** para exibir e compartilhar fotos e vídeos
* **Calibragem** (HoloLens) para ajustar a experiência do HoloLens ao usuário atual
* **Saiba os gestos** (HoloLens) ou **realidade misturada Saiba** (fones imersivos em exposição) para saber mais sobre como usar o seu dispositivo
* **Visualizador 3D** para decorar seu mundo com o conteúdo de realidade misturada
* **Misto realidade Portal** (área de trabalho) para Configurando e gerenciando o fone de ouvido envolvente e streaming de uma visualização dinâmica do modo de exibição o Headset para outras pessoas vejam.
* **Filmes e TV** para a exibição 360 vídeos e o mais recente filmes e tv mostra
* **Cortana** para todos os seu assistente virtual precisa
* **Área de trabalho** (fones imersivos em exposição) para exibir o monitor da área de trabalho enquanto estiver em um fone de ouvido envolventes
* **Explorador de arquivos** acessar arquivos e pastas localizados no seu dispositivo

## <a name="see-also"></a>Consulte também
* [Modos de exibição do aplicativo](app-views.md)
* [Controladores de movimento](motion-controllers.md)
* [Acessórios de hardware](hardware-accessories.md)
* [Considerações sobre o ambiente para HoloLens](environment-considerations-for-hololens.md)
* [Implementando os inicializadores de aplicativos 3D](implementing-3d-app-launchers.md)
* [Criar modelos 3D para uso no ambiente doméstico Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
