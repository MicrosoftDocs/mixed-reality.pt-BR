---
title: Entrada de emulador HoloLens e o simulador de realidade mista avançada
description: Instruções detalhadas para usar o teclado, mouse e controlador X pronto para simular a entrada para o emulador do HoloLens e o simulador de realidade mista do Windows.
author: ChimeraScorn
ms.author: cwhite
ms.date: 02/24/2018
ms.topic: article
keywords: HoloLens, emulador, simulação, realidade mista do Windows
ms.openlocfilehash: 59bea340a2ecdd2d65481c9ace4ab3f0bf15bc6f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589142"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Entrada de emulador HoloLens e o simulador de realidade mista avançada

A maioria dos usuários de emulador só será necessário usar os controles de entrada básicos para o [HoloLens emulador](using-the-hololens-emulator.md#basic-emulator-input) ou o [simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Os detalhes abaixo são para usuários avançados que encontraram uma necessidade para simular tipos mais complexos de entrada.

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).

## <a name="concepts"></a>Conceitos

Para começar a controlar a entrada virtual para o emulador do HoloLens e o simulador do Windows Mixed Reality, você deve primeiro compreender alguns conceitos.

Movimento se refere a controlar e alterar a posição e orientação de algo na cena. Para um objeto controlável direcionado, movimento é controlado com a rotação e translação (movimentação) ao longo de três eixos.
* **Yaw**: Por sua vez esquerda ou direita.
* **Tom**: Ative para cima ou para baixo.
* **Reverter**: Reverter lado a lado.
* **X**: Mover para a esquerda ou direita.
* **Y**: Mova para cima ou para baixo.
* **Z**: Mova para frente ou para trás.

[Gesto](gestures.md) e movimento controlador entrada são mapeados estreitamente para como eles dispositivos físicos:
* **Ação**: Isso simula a ação de pressionar o dedo indicador para o elevador ou extraindo o botão de ação em um controlador. Por exemplo, a entrada de ação pode ser usada para simular o gesto de toque de ar, para rolar pelo conteúdo e pressionar e manter pressionado.
* **[Bloom](gestures.md#bloom) ou Home**: Os HoloLens desabrochassem gesto ou botão de início de um controlador é usado para retornar para o shell e para executar ações do sistema.

Mãos tem um rico reprresentation no HoloLens V2.  Além de ser rastreadas/não controlados e pode ser usados para gestos de condução, mãos agora tem um modelo de esqueleto articulado se ajustam a eles e expostos para o desenvolvedor.  Isso introduz 20 pontos controlados por cada lado.  
* **Conjunta**: Um dos vinte posições controladas para uma determinada mão controlada. Isso terá um ponto é um espaço 3d associado a ele.
* **Apresentar**: Uma coleção completa de todas as junções em uma mão controlada. Neste momento, esta é uma coleção de junções de 20. 

Neste momento, nós não expomos controle direto de cada posição conjunta individualmente por meio do emulador de interface do usuário. No entanto, você pode defini-las por meio da API de simulação. Em vez disso, temos um conjunto de poses representativos útil que o emulador permite alternar entre.

Você também pode controlar o estado da entrada de sensor simulados:
* **Redefinir**: Isso retornará todos os sensores simulados para seus valores padrão.
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
|  Bloom |  F2 ou Windows key (chave do Windows só funciona com o emulador do HoloLens) |  |  Botão B | 
|  Botão da alça de controlador |  G (Windows Mixed Reality somente simulador) |  |  | 
|  Botão de menu do controlador |  M (Windows Mixed Reality somente simulador) |  |  | 
|  Toque do controlador touchpad |  U (Windows Mixed Reality somente simulador) |  |  | 
|  Pressione de touchpad do controlador |  P (Windows Mixed Reality somente simulador) |  |  | 
|  Conjunto de mão Pose | 7, 8, 9 ou 0 |  |  |
|  Redefinir |  Chave de escape |  |  botão Iniciar | 
|  Acompanhamento |  T ou F3 |  |  Botão X | 


Observação: No Windows Mixed Reality simulador apenas, os botões de controlador podem ser direcionamento para uma mão ou outra usando a mão modificadores de direcionamento.

## <a name="targeting"></a>Direcionamento 

Alguns dos conceitos de entrada acima-se nos seus próprios.  Ação, Bloom, redefinição e acompanhamento são conceitos completos, não é necessário e não são afetados por qualquer modificadores adicionais para direcionamento.  No entanto, os conceitos de restantes podem ser aplicados a um dos vários destinos. Introduzimos maneiras para especificar qual pretendido seu comando deve ser aplicado de destino.  Em todos os casos, é possível especificar por meio da interface do usuário ou por meio de pressionamentos de teclado, qual objeto para targtet.  Em alguns casos, também é possível especificar diretamente com o controlador do xbox. 

A tabela a seguir descrevem as opções de direcionamento e a maneira de ativar a cada um deles.

| Objeto | Modificador de teclado | Modificador de controlador | Modificador de interface do usuário do emulador |
|----------|----------|----------|----------|
| Corpo | <default> | <default> | <default> |
| Head | Espera H | <None available> | Anotação de cabeça na interface do usuário |
| À esquerda/controlador | Botão Alt esquerdo | Botão esquerdo Shoulder | Anotação à esquerda | 
| Mão direita/controlador | Botão Alt direita | Botão de direito Shoulder | Anotação da mão direita |
| Olhos | Espera Y | <No contoller modifier available> | Pino de olhos |
  
A tabela a seguir mostra como modificador cada destino mapeia cada um dos conceitos de entrada de movimentação do core

|  Padrão (corpo) |  Mão/controlador (Segure a tecla alt / arcar) |  Head (mantenha H)  |  Olhos (mantenha Y) |
|----------|----------|----------|----------|
|  Yaw |  Ativar o corpo da esquerda / direita |  Mover mão esquerda / direita |  Ativar o cabeçalho à esquerda / direita | Olhar olho parece esquerda/direita |
|  Rotação sobre o eixo x |  Ativar o head para cima / para baixo |  Mão de mover para cima / para baixo |  Ativar o head para cima / para baixo | Procura de olhar de olho para cima/para baixo | 
|  Roll |  Reverter o cabeçalho à esquerda / direita |  |  Reverter o cabeçalho à esquerda / direita | (Nenhuma ação) |
|  X |  Corpo de slide à esquerda / direita |  Mover/controlador de mão esquerda / direita |  Ativar o cabeçalho à esquerda / direita | (Nenhuma ação) |
|  Y |  Corpo de mover para cima / para baixo |  Mover/controlador de mão cima / para baixo |  Ativar o head para cima / para baixo | (Nenhuma ação) |
|  Z |  Mover o corpo de encaminhamento / com versões anteriores |  Mover mão/controlador de encaminhamento / com versões anteriores |  Ativar o head para cima / para baixo | (Nenhuma ação) |
 
Observação: No Windows Mixed Reality simulador apenas, os botões de controlador podem ser direcionamento para uma mão ou outra usando a mão modificadores de direcionamento. Da mesma forma, o emulador do HoloLens apenas, a pose de mão articuladas pode ser direcionamento para uma mão ou outro usando os modificadores de mão. 
 
## <a name="controlling-an-app"></a>Controlando um aplicativo

Este artigo descreveu o conjunto completo de tipos de entrada e modos de entrada que estão disponíveis no simulador do Windows Mixed Reality e HoloLens emulador. O seguinte conjunto de controles é sugerido para o uso diário:

|  Operação |  Teclado e mouse |  Controlador | 
|----------|----------|----------|
|  Corpo X |  A / D |  Analógico esquerdo à esquerda / direita | 
|  Corpo Y |  Página para cima / para baixo da página |  DPad cima / para baixo | 
|  Corpo Z |  W / S |  Analógico esquerdo cima / para baixo | 
|  Corpo Yaw |  Arraste o mouse esquerdo / direito |  Alavanca direcional direita/esquerda / direita | 
|  Yaw head |  H + arrastar o mouse para a esquerda / direita |  H (no teclado) + alavanca direcional direita/esquerda / direita | 
|  Densidade de cabeça |  Arraste o mouse para cima / para baixo |  À direita analógico para cima / para baixo | 
|  Rolo de cabeça |  Q / E |  DPad à esquerda / direita | 
|  Mão X |  Alt + arrastar o mouse para a esquerda / direita |  Shoulder + alavanca direcional direita/esquerda / direita | 
|  Mão Y |  Alt + arrastar o mouse para cima / para baixo |  Shoulder + direita analógico para cima / para baixo | 
|  Mão Z |  ALT + W / S |  Shoulder + analógico esquerdo cima / para baixo | 
|  Ação |  Botão direito do mouse |  gatilho | 
|  Desabrochassem / Home |  F2 ou Windows key (chave do Windows é apenas para o emulador do HoloLens) |  Botão B | 
|  Redefinir |  Escape |  botão Iniciar | 
|  Acompanhamento |  T |  Botão X | 
|  Rolagem |  ALT + direita botão do mouse + arrasta do mouse para cima / para baixo |  Shoulder + gatilho + direita analógico para cima / para baixo | 

## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Usar o simulador de realidade mista do Windows](using-the-windows-mixed-reality-simulator.md)
