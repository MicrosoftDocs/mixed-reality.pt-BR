---
title: Navegando na página inicial do Windows Mixed Reality
description: Os headsets do HoloLens e do Windows Mixed Realm compartilham um paradigma para iniciar, colocar e manipular aplicativos e modelos 3D em seu ambiente (seja físico ou digital). Saiba como navegar na página inicial do Windows Mixed Reality em ambos os tipos de dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Shell, so, plataforma, Cliff House, casa, casa, ambiente, iniciar, menu Iniciar, menu início, Pins, aplicativo, iniciar aplicativos, colocar aplicativos, teleport, mover, navegar
ms.openlocfilehash: 9de4cb44505d6cf4d0d3e4bd0fd9c5ee681063a5
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375893"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Navegando na página inicial do Windows Mixed Reality

Assim como a experiência do PC com o Windows começa com a área de trabalho, a realidade misturada do Windows começa com a casa. O Windows Mixed Reality Home aproveita nossa capacidade de inato de entender e navegar por locais 3D. Com o HoloLens, sua página inicial é seu espaço físico. Com headsets de imersão, sua casa é um local virtual.

Sua casa também é onde você usará o menu Iniciar para abrir e colocar aplicativos e conteúdo. Você pode preencher sua casa com conteúdo misto de realidade e multitarefas usando vários aplicativos ao mesmo tempo. As coisas que você coloca em casa ficam lá, mesmo se você reiniciar o dispositivo.

## <a name="start-menu"></a>Menu Iniciar

![Menu iniciar no Microsoft HoloLens](images/start-500px.png)

O menu iniciar consiste em:
* Informações do sistema (status da rede, porcentagem da bateria, hora atual e volume)
* Cortana (em headsets de imersão, um bloco inicial; no HoloLens, na parte superior do início)
* Aplicativos fixados
* O botão todos os aplicativos (sinal de adição)
* Botões de foto e vídeo para [captura de realidade misturada](mixed-reality-capture.md)

Alterne entre os modos de exibição aplicativos fixados e todos os aplicativos selecionando os botões mais ou menos. Para abrir o menu iniciar no HoloLens, use o gesto de flor. Em um headset de imersão, pressione o botão Windows em seu controlador.

## <a name="launching-apps"></a>Iniciando aplicativos

Para iniciar um aplicativo, selecione-o em Iniciar. O menu iniciar desaparecerá e o aplicativo será aberto no modo de posicionamento, como uma janela 2D ou um [modelo 3D](implementing-3d-app-launchers.md).

Para executar o aplicativo, você precisará colocá-lo em sua página inicial:
1. Use seu [olhar](gaze-and-commit.md) ou controlador para posicionar o aplicativo onde desejar. Ele será ajustado automaticamente (em tamanho e posição) para estar em conformidade com o espaço onde você o coloca.
2. Coloque o aplicativo usando o ar-toque (HoloLens) ou o botão de seleção (headsets de imersão). Para cancelar e retornar o menu Iniciar, use o gesto de cair ou o botão do Windows.

os [aplicativos 2D](building-2d-apps.md), criados para desktop, móvel ou Xbox, podem ser modificados para serem executados como aplicativos de imersão de realidade misturada usando a [API HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx). Um aplicativo de imersão retira o usuário da casa e em uma experiência de imersão. Os usuários podem retornar a página inicial com o HoloLens (gesto de cair) ou pressionando o botão Windows em seu controlador (headsets de imersão).

Os aplicativos também podem ser iniciados por meio de uma API de aplicativo para aplicativo ou via Cortana.

![Aplicativos na página inicial do Windows Mixed Reality](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Movendo e ajustando aplicativos

Selecione **ajustar** na barra de aplicativos para revelar os controles que movem, dimensionam e giram o conteúdo da realidade misturada. Quando tiver terminado, selecione **concluído**.

![O Slate da loja no modo de ajuste (quadro azul). Observe que a barra de aplicativos (superior) foi alterada para incluir os botões ' Concluído ' e ' remover '.](images/adjust-500px.png)

Aplicativos diferentes podem ter opções adicionais na barra de aplicativos. Por exemplo, o Microsoft Edge tem opções de *rolagem*, *arrastar*e *zoom* . 

![Barra de aplicativos para aplicativos 2D em execução no HoloLens](images/holobar-500px.png)

O botão **voltar** navega de volta para as telas exibidas anteriormente no aplicativo. Ele será interrompido quando você chegar ao início das experiências que foram mostradas no aplicativo e não navegará para outros aplicativos.

## <a name="getting-around-your-home"></a>Entrando em casa

Com o **HoloLens**, você passa por espaço físico para se mover em casa.

Com **headsets de imersão**, você pode, de maneira semelhante, se familiarizar em seu Playspace para se mover em uma área semelhante no mundo virtual. Para mover-se por longas distâncias, você pode usar o Thumbstick em seu controlador para praticamente "andar" ou pode usar a *teleportação* para saltar imediatamente as distâncias mais longas.

![Teleportação na página inicial do Windows Mixed Reality](images/teleportation-500px.png)

**Para teleport:**
1. Abrir o reticle de teleportação.
   * Usando [controladores de movimento](motion-controllers.md): Pressione o Thumbstick para frente e segure-o nessa posição.
   * Usando um controlador Xbox: Pressione a Thumbstick esquerda para frente e segure-a nessa posição.
   * Usando um mouse: mantenha pressionado o botão com o botão direito do mouse (e use a roda de rolagem para girar a direção que você deseja enfrentar quando teleport).
2. Coloque o reticle onde você deseja teleport.
   * Usando [controladores de movimento](motion-controllers.md): Incline o controlador (no qual você está mantendo o Thumbstick Forward) para mover o reticle.
   * Usando um controlador Xbox: Use seu [olhar](gaze-and-commit.md) para mover o reticle.
   * Usando um mouse: Mova o mouse para mover o reticle.
3. Solte o botão para teleport onde o reticle foi colocado.

**Para praticamente "Walk:"**
* Usando os [controladores de movimento](motion-controllers.md): clique no botão de Thumbstick e segure e, em seguida, mova o Thumbstick na direção que você deseja "andar".
* Usando um controlador Xbox: clique com o botão esquerdo do Thumbstick e segure e, em seguida, mova o Thumbstick na direção que você deseja "percorrer".

## <a name="immersive-headset-input-support"></a>Suporte de entrada de headset de imersão

Os [headsets de imersão de realidade mista do Windows](immersive-headset-hardware-details.md) dão suporte a vários tipos de entrada para navegar na página inicial do Windows Mixed Reality. O HoloLens não oferece suporte a entradas de acessório para navegação, pois você acompanha fisicamente e vê seu ambiente. No entanto, o HoloLens [oferece suporte a entradas](hardware-accessories.md) para interagir com aplicativos.

### <a name="motion-controllers"></a>controladores de movimentos

A melhor experiência de realidade mista do Windows será com os [controladores de movimento](motion-controllers.md) do Windows Mixed Reality que dão suporte ao acompanhamento de 6 graus de liberdade usando apenas os sensores em seu headset-nenhuma câmera ou marcador externo é necessário!

Comandos de navegação em breve.

### <a name="gamepad"></a>Gamepad
* **Thumbstick esquerdo:**
  * Pressione e mantenha o Thumbstick à esquerda para abrir o reticle de [Teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) .
  * Toque em Thumbstick à esquerda, à direita ou voltar para mover para a esquerda, para a direita ou de volta em pequenos incrementos.
  * Clique no botão esquerdo Thumbstick e mantenha pressionado e, em seguida, mova o Thumbstick para a direção que você deseja [praticamente "andar".](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Toque na **Thumbstick direita** ou à direita para girar a direção que você está enfrentando em 45 graus.
* Pressionar o **botão a executa** uma seleção e age como o gesto de [toque do ar](gaze-and-commit.md#composite-gestures) .
* Pressionar o botão **guia** abre o [menu iniciar](navigating-the-windows-mixed-reality-home.md#start-menu) e atua como o gesto de [cair](system-gesture.md#bloom) .
* Pressionar os **gatilhos esquerdo e direito** permite ampliar e reduzir um aplicativo de área de trabalho 2D com o qual você está interagindo em casa.

### <a name="keyboard-and-mouse"></a>Teclado e mouse

**Observação:** Use a **tecla Windows + Y** para alternar o mouse entre controlar a área de trabalho do computador e a página inicial do Windows Mixed Reality.

Na página inicial do Windows Mixed Reality:
* Pressionar o botão **esquerdo** do mouse executa uma seleção e age como o gesto de [toque do ar](gaze-and-commit.md#composite-gestures) .
* Manter o botão **direito** do mouse abre o reticle de [teleportação](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) .
* Pressionar a tecla **Windows** no teclado abre o [menu iniciar](navigating-the-windows-mixed-reality-home.md#start-menu) e age como o gesto de [cair](system-gesture.md#bloom) .
* Quando [nuvens](gaze-and-commit.md) em um aplicativo de área de trabalho 2D, você pode **clicar** para selecionar, clicar com o **botão direito do mouse** para exibir menus de contexto e usar a **roda de rolagem** para rolar (assim como na área de trabalho do seu PC).

## <a name="cortana"></a>Cortana

O [Cortana](voice-input.md#hey-cortana) é o seu assistente pessoal no Windows Mixed Reality, assim como no PC e no telefone. O HoloLens tem um microfone interno, mas os headsets de imersão podem exigir hardware adicional. Use a Cortana para abrir aplicativos, reinicie o dispositivo, verifique as coisas online e muito mais. Os desenvolvedores também podem optar por [integrar o Cortana](https://dev.windows.com/cortana) em suas experiências.

Você também pode usar comandos de voz para colocar em sua casa. Por exemplo, aponte para um botão (usando [olhar](gaze-and-commit.md) ou um controlador, dependendo do dispositivo) e diga "Select". Outros comandos de voz incluem "ir para a casa", "maior", "menor", "fechar" e "entrar em frente".

## <a name="store-settings-and-system-apps"></a>Aplicativos de armazenamento, configurações e sistema

O Windows Mixed Reality tem vários aplicativos internos, como:
* **Microsoft Store** para obter aplicativos e jogos
* **Hub de comentários** para enviar comentários sobre o sistema e os aplicativos do sistema
* **Configurações** para definir as configurações do sistema (incluindo atualizações de sistema e de[rede](connecting-to-wi-fi-on-hololens.md) )
* **Microsoft Edge** para procurar sites
* **Fotos** para exibir e compartilhar fotos e vídeos
* **Calibragem** (somente HoloLens) para ajustar a experiência do HoloLens para o usuário atual
* **Mais informações sobre gestos** (HoloLens) ou aprenda sobre a **realidade misturada** (headsets de imersão) para saber mais sobre como usar seu dispositivo
* **visualizador 3D** para decorar seu mundo com conteúdo de realidade misturada
* **Portal de realidade misturada** (Desktop) para configurar e gerenciar o headset de imersão e transmitir uma visualização dinâmica de sua exibição no Headset para que outras pessoas vejam.
* **Filmes e TV** para exibir vídeos 360 e os filmes e programas de TV mais recentes
* **Cortana** para todas as suas necessidades de assistente virtual
* **Área de trabalho** (headsets de imersão) para exibir seu monitor de área de trabalho enquanto estiver em um headset de imersão
* **Explorador de arquivos** Acessar arquivos e pastas localizados em seu dispositivo

## <a name="see-also"></a>Consulte também
* [Modos de exibição do aplicativo](app-views.md)
* [Controladores de movimentos](motion-controllers.md)
* [Acessórios de hardware](hardware-accessories.md)
* [Considerações sobre o ambiente para HoloLens](environment-considerations-for-hololens.md)
* [Implementando iniciadores de aplicativos 3D](implementing-3d-app-launchers.md)
* [Criando modelos 3D para uso na página inicial do Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
