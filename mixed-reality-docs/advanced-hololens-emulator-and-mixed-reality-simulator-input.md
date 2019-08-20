---
title: Entrada do emulador de HoloLens avançado e do simulador de realidade misturada
description: Instruções detalhadas para usar o teclado, o mouse e o controlador Xbox para simular a entrada para o emulador do HoloLens e o simulador de realidade mista do Windows.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, emulador, simulação, realidade misturada do Windows
ms.openlocfilehash: 6ea493d8c1269ff0bea1d4102b9e224e30d06aef
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580588"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Entrada do emulador de HoloLens avançado e do simulador de realidade misturada

A maioria dos usuários do emulador só precisará usar os controles de entrada básicos para o emulador do [HoloLens](using-the-hololens-emulator.md#basic-emulator-input) ou o simulador de [realidade mista do Windows](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Os detalhes a seguir são para usuários avançados que encontraram uma necessidade de simular tipos de entrada mais complexos.


## <a name="concepts"></a>Conceitos

Para começar a controlar a entrada virtual para o emulador do HoloLens e o simulador de realidade do Windows Mixed, você deve primeiro entender alguns conceitos.

O movimento se refere ao controle e à alteração da posição e da orientação de algo na cena. Para um objeto controlável direcionado, o movimento é controlado com rotação e conversão (movimento) em três eixos.
* **Guinada**: Virar à esquerda ou à direita.
* **Pitch**: Ativar ou desativar.
* **Roll**: Distribuição lado a lado.
* **X**: Mover para a esquerda ou direita.
* **Y**: Mover para cima ou para baixo.
* **Z**: Avançar ou retroceder.

As entradas do controlador de [gesto](gestures.md) e movimento são mapeadas de acordo com o modo como os dispositivos físicos:
* **Ação**: Isso simula a ação de pressionar o dedo indicador para o polegar ou extrair o botão de ação em um controlador. Por exemplo, a entrada da ação pode ser usada para simular o gesto de toque de ar, para rolar pelo conteúdo e para pressionar e manter pressionado.
* **[Bloom](gestures.md#bloom)Gesto de/estado ou página inicial**: O gesto de cair/sistema do HoloLens ou o botão página inicial de um controlador é usado para retornar ao shell e executar ações do sistema.

As mãos têm um reprresentation avançado no HoloLens 2.  Além de serem controlados/não rastreados, e utilizáveis para a condução de gestos, as mãos agora têm um modelo de esqueleto articulado que se ajusta a eles e expostos ao desenvolvedor.  Isso apresenta 26 pontos rastreados em cada mão.  
* **Conjunto**: Uma das vinte posições controladas para uma determinada mão controlada. Isso terá um ponto é o espaço 3D associado a ele.
* **Pose**: Uma coleção completa de todas as junções de uma mão controlada. Neste momento, esta é uma coleção de 26 junções. 

Neste momento, não expõemos o controle direto de cada posição conjunta individualmente por meio da interface do usuário do emulador, embora você possa defini-las por meio da API de simulação. Em vez disso, temos um conjunto de representações úteis que o emulador permite alternar entre.

Você também pode controlar o estado da entrada simulada do sensor:
* **Redefinir**: Isso retornará todos os sensores simulados para seus valores padrão.  Começando com o emulador do HoloLens 2, uma redefinição pode ter como escopo uma ou ambas as mãos ao envolver as mãos desejadas usando as chaves (s) modificadores apropriadas (es) ou os botões (Alt e/ou direita, ou o amortecedor esquerdo e/ou direito no gamepad).
* **Acompanhamento**: Percorre os modos de controle posicional. Isso inclui:
  * **Padrão**: O sistema operacional escolhe o melhor modo de controle com base nas solicitações feitas do sistema.
   * **Orientação**: Força o rastreamento somente de orientação, independentemente das solicitações feitas do sistema.
   * **Posicional**: Força o controle posicional, independentemente das solicitações feitas do sistema.

## <a name="types-of-input"></a>Tipos de entrada

A tabela a seguir mostra como cada tipo de entrada é mapeada para o teclado, o mouse e o controlador Xbox. Cada tipo tem um mapeamento diferente, dependendo do modo de controle de entrada; mais informações sobre modos de controle de entrada são fornecidas posteriormente neste documento.

|  |  Teclado |  Mouse |  Controlador Xbox | 
|----------|----------|----------|----------|
|  Yaw |  Setas à esquerda/direita |  Arrastar para a esquerda/direita |  Direita Thumbstick esquerda/direita | 
|  Rotação sobre o eixo x |  Setas para cima/para baixo |  Arrastar para cima/para baixo |  Thumbstick direita/para baixo | 
|  Roll |  P/E |  |  DPad esquerda/direita | 
|  X |  A/D |  |  Esquerda Thumbstick esquerda/direita | 
|  S |  Page up/Page Down |  |  DPad para cima/para baixo | 
|  Z |  W/S |  |  Esquerda Thumbstick para cima/para baixo | 
|  Action |  Inserir ou espaço |  Botão direito |  Um botão ou um gatilho | 
|  Flor/sistema |  F2 ou tecla do Windows |  |  Botão B | 
|  Botão de alça do controlador |  G  |  |  | 
|  Botão de menu do controlador |  M  |  |  | 
|  Touch Touch do controlador |  T  |  |  | 
|  Pressione o controlador Touchpad |  P  |  |  | 
|  Thumbstick do controlador |  K  |  |  | 
|  Estado de controle do controlador esquerdo |  F9 |  |  | 
|  Estado de controle do controlador correto |  F10 |  |  | 
|  A mão ' fechar ' da pose | 7 |  |  |
|  ' Abrir ' da pose (padrão) | 8 |  |  |
|  Pose ' Point ' de mão | 9 |  |  |
|  "Pinça" pose | 0 |  |  |
|  Redefinir |  Tecla de escape |  |  botão Iniciar | 
|  Controle alterações |  T ou F3 |  |  Botão X | 


Observação: Os botões do controlador podem ser direcionamentodos a um único lado/controlador ou ao outro usando os modificadores de destino da mão.

## <a name="targeting"></a>Direcionamento 

Alguns dos conceitos de entrada acima têm por conta própria.  A ação, a flor/sistema, a redefinição e o acompanhamento são conceitos completos, não são necessários e não são afetados pelo, quaisquer modificadores adicionais para direcionamento.  No entanto, os conceitos restantes podem ser aplicados a um de vários destinos. Apresentamos maneiras de especificar a qual destino pretendido seu comando deve ser aplicado.  Em todos os casos, é possível especificar por meio da interface do usuário ou por meio de pressionamentos de teclado, que objeto targtet.  Em alguns casos, também é possível especificar com o controlador Xbox diretamente. 

A tabela a seguir descreve as opções de direcionamento e a maneira de ativar cada uma delas.

| Object | Modificador de teclado | Modificador de controlador | Modificador de IU do emulador |
|----------|----------|----------|----------|
| Body | (padrão) | (padrão) | (padrão) |
| Principal | Manter H | (Não disponível) | (Não disponível) |
| À esquerda/controlador | Pressionar o botão Alt esquerdo | Botão manter à esquerda | Anotação à esquerda | 
| À direita/controlador | Manter botão Alt direito | Botão manter à direita | Anotação à direita |
| Mal | Reter Y | (Não disponível) | Pino de olhos |
  
A tabela a seguir mostra como cada modificador de destino mapeia cada um dos conceitos de entrada de movimento principal

|  | Padrão (corpo) |  Mão/controlador (Mantenha Alt, pressione o botão de controle do gamepad ou alterne o pino da interface do usuário) |  Cabeça (Hold H)  |  Olhos (manter Y ou alternar o pino da interface do usuário) |
|----------|----------|----------|----------|
|  Yaw |  Girar corpo para a esquerda/direita |  Mover para a esquerda/direita |  Transformar cabeçalho à esquerda/direita | Olhar de olho parece esquerda/direita |
|  Rotação sobre o eixo x |  Girar para cima/para baixo |  Mover para cima/para baixo |  Girar para cima/para baixo | Olho olhar pesquisa | 
|  Roll |  Rolar cabeçalho para a esquerda/direita |  |  Rolar cabeçalho para a esquerda/direita | (Nenhuma ação) |
|  X |  Corpo do slide à esquerda/direita |  Mover mão/controlador para a esquerda/direita |  Transformar cabeçalho à esquerda/direita | (Nenhuma ação) |
|  S |  Mover corpo para cima/para baixo |  Mover mão/controlador para cima/para baixo |  Girar para cima/para baixo | (Nenhuma ação) |
|  Z |  Mover corpo para frente/para trás |  Mover mão/avançar/voltar do controlador |  Girar para cima/para baixo | (Nenhuma ação) |
 
 
## <a name="controlling-an-app"></a>Controlando um aplicativo

O seguinte conjunto de controles é sugerido para uso do dia a dia:

|  Operação |  Teclado e mouse |  Controlador | 
|----------|----------|----------|
|  Corpo X |  A/D |  Esquerda Thumbstick esquerda/direita | 
|  Corpo Y |  Page up/Page Down |  DPad para cima/para baixo | 
|  Corpo Z |  W/S |  Esquerda Thumbstick para cima/para baixo | 
|  Guinada do corpo |  Arrastar mouse para a esquerda/direita |  Direita Thumbstick esquerda/direita | 
|  Desvio de cabeça |  H + arrastar mouse para a esquerda/direita |  H (no teclado) + direita Thumbstick esquerda/direita | 
|  Inclinação do cabeçalho |  Arrastar o mouse para cima/para baixo |  Thumbstick direita/para baixo | 
|  Rolo de cabeçalho |  P/E |  DPad esquerda/direita | 
|  Mão/controlador X |  ALT + A/D |  Tiracolo + esquerda Thumbstick esquerda/direita | 
|  Mão/controlador Y |  Alt + Page up/Page Down |  Tiracolo + DPad para cima/para baixo | 
|  Mão/controlador Z |  ALT + W/S |  Tiracolo + esquerdo Thumbstick para cima/para baixo | 
|  Desvio da mão/controlador |  Alt + arrastar mouse para a esquerda/direita |  Tiracolo + direita Thumbstick esquerda/direita | 
|  Densidade da mão/controlador |  Alt + arrastar mouse para cima/para baixo |  Tiracolo + direita Thumbstick para cima/para baixo | 
|  Distribuição à mão/controlador |  ALT + Q/E |  Tiracolo + DPad à esquerda/direita | 
|  Action |  Botão direito do mouse |  Disparador | 
|  Flor/sistema/página inicial |  F2 ou tecla do Windows |  Botão B | 
|  Redefinir |  Escape |  botão Iniciar | 
|  Controle alterações |  T |  Botão X | 
|  Rolagem |  Alt + botão direito do mouse + arrastar o mouse para cima/para baixo |  Tiracolo + gatilho + Thumbstick direita/inativo | 
|  Mover/girar mais rápido | Tecla SHIFT esquerda ou direita | Pressione e segure a Thumbstick correta |
|  Mover/girar lentamente | Tecla CTRL esquerda ou direita | Pressionar e manter o Thumbstick esquerdo |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Atalhos de teclado do painel de controle da simulação de percepção

Os atalhos de teclado a seguir estão disponíveis para acessar o painel de controle de simulação de percepção e habilitar ou desabilitar dispositivos de entrada de PC para uso com simulação.

| Operação | Atalho | Descrição/observações |
|-----------|----------|-------------|
| Alternar ' usar teclado para simulação ' | F4 | Quando desativado, a entrada do teclado vai para o aplicativo do HoloLens ou do Windows Mixed Reality. |
| Alternar ' usar o mouse para simulação ' | F5 | Quando desativado, a entrada do mouse vai para o ambiente de realidade misturada (apenas para a realidade mista do Windows) |
| Alternar ' usar o gamepad para simulação ' | F6 | Quando desativado, a entrada de gamepad é ignorada por simulação |
| Mostrar ou ocultar o painel de controle | F7 | |
| Definir o foco do teclado para o painel de controle | F8 | Se o painel não estiver visível no momento, ele será mostrado primeiro. |
| Encaixar ou desencaixar o painel de/para o emulador ou a janela do portal da realidade misturada | F9 | Se a janela for fechada quando desencaixada, ela será encaixada e ocultada. |

## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Como usar o simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
