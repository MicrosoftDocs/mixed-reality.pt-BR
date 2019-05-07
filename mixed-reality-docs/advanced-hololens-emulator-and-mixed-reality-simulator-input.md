---
title: Entrada de emulador HoloLens e o simulador de realidade mista avançada
description: Instruções detalhadas para usar o teclado, mouse e controlador do Xbox para simular a entrada para o simulador de emulador HoloLens e realidade mista do Windows.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, emulador, simulação, realidade mista do Windows
ms.openlocfilehash: 6ea493d8c1269ff0bea1d4102b9e224e30d06aef
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580588"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Entrada de emulador HoloLens e o simulador de realidade mista avançada

A maioria dos usuários de emulador só será necessário usar os controles de entrada básicos para o [HoloLens emulador](using-the-hololens-emulator.md#basic-emulator-input) ou o [simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Os detalhes abaixo são para usuários avançados que encontraram uma necessidade para simular tipos mais complexos de entrada.


## <a name="concepts"></a>Conceitos

Para começar a controlar a entrada virtual para o simulador de emulador HoloLens e o Windows Mixed Reality, você deve primeiro compreender alguns conceitos.

Movimento se refere a controlar e alterar a posição e orientação de algo na cena. Para um objeto controlável direcionado, movimento é controlado com a rotação e translação (movimentação) ao longo de três eixos.
* **Yaw**: Por sua vez esquerda ou direita.
* **Tom**: Ative para cima ou para baixo.
* **Reverter**: Reverter lado a lado.
* **X**: Mover para a esquerda ou direita.
* **Y**: Mova para cima ou para baixo.
* **Z**: Mova para frente ou para trás.

[Gesto](gestures.md) e movimento controlador entrada são mapeados estreitamente para como eles dispositivos físicos:
* **Ação**: Isso simula a ação de pressionar o dedo indicador para o elevador ou extraindo o botão de ação em um controlador. Por exemplo, a entrada de ação pode ser usada para simular o gesto de toque de ar, para rolar pelo conteúdo e pressionar e manter pressionado.
* **[Bloom](gestures.md#bloom)gesto /System ou Home**: O gesto do sistema/bloom HoloLens ou botão de início de um controlador é usado para retornar para o shell e para executar ações do sistema.

Mãos tem um rico reprresentation no HoloLens 2.  Além de ser rastreadas/não controlados e pode ser usados para gestos de condução, mãos agora tem um modelo de esqueleto articulado se ajustam a eles e expostos para o desenvolvedor.  Isso introduz 26 pontos controlados por cada lado.  
* **Conjunta**: Um dos vinte posições controladas para uma determinada mão controlada. Isso terá um ponto é um espaço 3d associado a ele.
* **Apresentar**: Uma coleção completa de todas as junções em uma mão controlada. Neste momento, esta é uma coleção de 26 junções. 

Neste momento, nós não expomos controle direto de cada posição conjunta individualmente por meio da interface de usuário do emulador, embora você pode defini-las por meio da API de simulação. Em vez disso, temos um conjunto de poses representativos útil que o emulador permite alternar entre.

Você também pode controlar o estado da entrada de sensor simulados:
* **Redefinir**: Isso retornará todos os sensores simulados para seus valores padrão.  Começando com o emulador de 2 HoloLens, uma redefinição pode ser definida para uma ou ambas as mãos ao envolver a hand(s) desejado usando o (s) de modificador apropriado ou apropriados (à esquerda e/ou Alt direita ou o Amortecedor esquerdo e/ou direito no gamepad).
* **Controle**: Alterna entre os modos de acompanhamento posicionais. Isso inclui:
  * **Padrão**: O sistema operacional escolherá o melhor modo de controle com base nas solicitações feitas do sistema.
   * **Orientação**: Força somente orientação acompanhamento, independentemente das solicitações feitas do sistema.
   * **Posicionais**: Força posicionais acompanhamento, independentemente das solicitações feitas do sistema.

## <a name="types-of-input"></a>Tipos de entrada

A tabela a seguir mostra como cada tipo de entrada é mapeado para o teclado, mouse e controlador do Xbox. Cada tipo tem um mapeamento diferente dependendo do modo de controle de entrada; mais informações sobre os modos de controle de entrada são fornecidas neste documento.

|  |  Teclado |  Mouse |  Controlador do Xbox | 
|----------|----------|----------|----------|
|  Yaw |  Setas à esquerda / direita |  Arraste para a esquerda / direita |  Alavanca direcional direita/esquerda / direita | 
|  Rotação sobre o eixo x |  Para cima / para baixo setas |  Arrastar para cima / para baixo |  À direita analógico para cima / para baixo | 
|  Roll |  Q / E |  |  DPad à esquerda / direita | 
|  X |  A / D |  |  Analógico esquerdo à esquerda / direita | 
|  Y |  Página para cima / para baixo da página |  |  DPad cima / para baixo | 
|  Z |  W / S |  |  Analógico esquerdo cima / para baixo | 
|  Ação |  Insira ou espaço |  Botão à direita |  Um botão ou um gatilho | 
|  Bloom/sistema |  Tecla F2 ou Windows |  |  Botão B | 
|  Botão da alça de controlador |  G  |  |  | 
|  Botão de menu do controlador |  M  |  |  | 
|  Toque do controlador touchpad |  U  |  |  | 
|  Pressione de touchpad do controlador |  P  |  |  | 
|  Pressione do controlador direcional |  K  |  |  | 
|  Estado de controle de controlador à esquerda |  F9 |  |  | 
|  Controlador certo estado de controle |  F10 |  |  | 
|  Pose 'Fechar' de mão | 7 |  |  |
|  Entregar Pose 'Aberto' (padrão) | 8 |  |  |
|  Mão 'Aponta' Pose | 9 |  |  |
|  Mão 'Pinch' Pose | 0 |  |  |
|  Redefinir |  Chave de escape |  |  botão Iniciar | 
|  Acompanhamento |  T ou F3 |  |  Botão X | 


Observação: Os botões de controlador podem ser o direcionamento para uma mão/controlador ou a outra usando a mão modificadores de direcionamento.

## <a name="targeting"></a>Direcionamento 

Alguns dos conceitos de entrada acima-se nos seus próprios.  Ação, sistema/Bloom, redefinição e acompanhamento são conceitos completos, não é necessário e não são afetados por qualquer modificadores adicionais para direcionamento.  No entanto, os conceitos de restantes podem ser aplicados a um dos vários destinos. Introduzimos maneiras para especificar qual pretendido seu comando deve ser aplicado de destino.  Em todos os casos, é possível especificar por meio da interface do usuário ou por meio de pressionamentos de teclado, qual objeto para targtet.  Em alguns casos, também é possível especificar diretamente com o controlador do xbox. 

A tabela a seguir descrevem as opções de direcionamento e a maneira de ativar a cada um deles.

| Object | Modificador de teclado | Modificador de controlador | Modificador de interface do usuário do emulador |
|----------|----------|----------|----------|
| Corpo | (padrão) | (padrão) | (padrão) |
| Head | Espera H | (Não disponível) | (Não disponível) |
| À esquerda/controlador | Mantenha o botão Alt esquerdo | Mantenha o botão esquerdo Shoulder | Anotação à esquerda | 
| Mão direita/controlador | Mantenha o botão Alt direita | Mantenha o botão de direito Shoulder | Anotação da mão direita |
| Olhos | Espera Y | (Não disponível) | Pino de olhos |
  
A tabela a seguir mostra como modificador cada destino mapeia cada um dos conceitos de entrada de movimentação do core

|  | Padrão (corpo) |  Mão/controlador (mantenha Alt, mantenha pressionado o botão do gamepad shoulder ou ativar/desativar anotações de interface do usuário) |  Head (mantenha H)  |  Olhos (pino mantenha Y ou alternância da interface do usuário) |
|----------|----------|----------|----------|
|  Yaw |  Ativar o corpo da esquerda / direita |  Mover mão esquerda / direita |  Ativar o cabeçalho à esquerda / direita | Olhar olho parece esquerda/direita |
|  Rotação sobre o eixo x |  Ativar o head para cima / para baixo |  Mão de mover para cima / para baixo |  Ativar o head para cima / para baixo | Procura de olhar de olho para cima/para baixo | 
|  Roll |  Reverter o cabeçalho à esquerda / direita |  |  Reverter o cabeçalho à esquerda / direita | (Nenhuma ação) |
|  X |  Corpo de slide à esquerda / direita |  Mover/controlador de mão esquerda / direita |  Ativar o cabeçalho à esquerda / direita | (Nenhuma ação) |
|  Y |  Corpo de mover para cima / para baixo |  Mover/controlador de mão cima / para baixo |  Ativar o head para cima / para baixo | (Nenhuma ação) |
|  Z |  Mover o corpo de encaminhamento / com versões anteriores |  Mover mão/controlador de encaminhamento / com versões anteriores |  Ativar o head para cima / para baixo | (Nenhuma ação) |
 
 
## <a name="controlling-an-app"></a>Controlando um aplicativo

O seguinte conjunto de controles é sugerido para o uso diário:

|  Operação |  Teclado e mouse |  Controlador | 
|----------|----------|----------|
|  Corpo X |  A / D |  Analógico esquerdo à esquerda / direita | 
|  Corpo Y |  Página para cima / para baixo da página |  DPad cima / para baixo | 
|  Corpo Z |  W / S |  Analógico esquerdo cima / para baixo | 
|  Corpo Yaw |  Arraste o mouse esquerdo / direito |  Alavanca direcional direita/esquerda / direita | 
|  Yaw head |  H + arrastar o mouse para a esquerda / direita |  H (no teclado) + alavanca direcional direita/esquerda / direita | 
|  Densidade de cabeça |  Arraste o mouse para cima / para baixo |  À direita analógico para cima / para baixo | 
|  Rolo de cabeça |  Q / E |  DPad à esquerda / direita | 
|  Mão/controlador X |  ALT + A / 1!d |  Shoulder + analógico esquerdo à esquerda / direita | 
|  Mão/controlador Y |  ALT + a página para cima / para baixo da página |  Shoulder + DPad cima / para baixo | 
|  Mão/controlador Z |  ALT + W / S |  Shoulder + analógico esquerdo cima / para baixo | 
|  Yaw mão/controlador |  Alt + arrastar o mouse para a esquerda / direita |  Shoulder + alavanca direcional direita/esquerda / direita | 
|  Densidade de mão/controlador |  Alt + arrastar o mouse para cima / para baixo |  Shoulder + direita analógico para cima / para baixo | 
|  Rolo de mão/controlador |  Alt + Q / E |  Shoulder + DPad à esquerda / direita | 
|  Ação |  Botão direito do mouse |  gatilho | 
|  Bloom / sistema / Home |  Tecla F2 ou Windows |  Botão B | 
|  Redefinir |  Escape |  botão Iniciar | 
|  Acompanhamento |  T |  Botão X | 
|  Rolagem |  ALT + direita botão do mouse + arrasta do mouse para cima / para baixo |  Shoulder + gatilho + direita analógico para cima / para baixo | 
|  Mover/girar mais rápido | Tecla de Shift esquerda ou direita | Pressione e segure a alavanca direcional direita |
|  Mover/girar lento | Tecla de Ctrl direita ou esquerda | Pressione e segure o analógico esquerdo |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Atalhos de teclado do painel de controle de simulação de percepção

Os atalhos de teclado a seguir estão disponíveis para acessar o painel de controle de simulação de percepção e habilitar ou desabilitantes dispositivos de entrada de PC para usam com a simulação.

| Operação | Atalho | Descrição/observações |
|-----------|----------|-------------|
| Ativar/desativar 'Usar o teclado para simulação' | F4 | Quando desativado, a entrada do teclado vai para o aplicativo HoloLens ou Windows Mixed Reality. |
| Ativar/desativar 'Usar o mouse para simulação' | F5 | Quando desativado, a entrada do mouse vai para o ambiente de realidade misturada (Windows Mixed Reality somente) |
| Ativar/desativar 'Usar gamepad simulação' | F6 | Quando desativado, gamepad entrada é ignorada pelo simulação |
| Mostrar ou ocultar o painel de controle | F7 | |
| Definir o foco do teclado para o painel de controle | F8 | Se o painel não estiver visível no momento, ele será mostrado primeiro. |
| Encaixar ou desencaixar o painel de/para o emulador ou a janela do Portal de realidade mista | F9 | Se a janela é fechada quando desencaixado, é encaixada e oculto. |

## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Como usar o simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
