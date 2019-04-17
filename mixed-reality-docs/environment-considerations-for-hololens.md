---
title: Considerações sobre o ambiente para HoloLens
description: Obter a melhor experiência possível usando HoloLens, quando você otimiza o dispositivo para seu ambiente e olhos.
author: thetuvix
ms.author: msamples
ms.date: 02/24/2019
ms.topic: article
keywords: quadro holográfico, campo de visão, fov, calibração, espaços, ambiente, instruções
ms.openlocfilehash: d5433dc923aeb70e3ae82e75c9358d3a569e8f83
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589831"
---
# <a name="environment-considerations-for-hololens"></a>Considerações sobre o ambiente para HoloLens

HoloLens que combina os holographic com o mundo "real", colocando hologramas em seu ambiente. Uma janela do aplicativo holográfica "trava" na parede, uma ballerina holográfica gira sobre o table-top, ouvidos coelho ficam na parte superior do cabeçalho do seu amigo involuntária. Quando você estiver usando um aplicativo ou jogo imersivo, o mundo holográfico espalhará para preencher o seu ambiente, mas você ainda poderá ver e mover-se o espaço.

As hologramas que você colocar permanecerão onde você os colocou, mesmo se você desativar seu dispositivo. 

Aqui estão algumas coisas para ter em mente para melhorar sua experiência com o mundo holographic. Observe que, HoloLens foi projetado para ser usada em locais fechados em um espaço seguro com sem causar tropeços e riscos. Não usá-lo ao dirigir ou realizar outras atividades que exigem sua atenção total.

## <a name="spaces"></a>Espaços

HoloLens aprende sobre o seu espaço para que ele possa se lembrar de onde você colocou hologramas. HoloLens podem se lembrar de vários espaços e foi projetado para carregar o espaço correto quando você ativá-lo.

### <a name="setting-up"></a>Como configurar

HoloLens podem mapear e lembre-se de seus espaços de melhor se você escolher o ambiente certo.
* Use uma sala com luz suficiente e espaço suficiente. Evite usar espaços escuros e salas com muita superfícies escuras, brilhantes ou translúcidas (como espelhos ou cortinas finas).
* Se você quiser HoloLens aprender um espaço, encarar os fatos diretamente, de cerca de um metro imediatamente.
* Evite espaços com uma grande quantidade de movimentação de objetos. Se um item foi movido, e você quiser que o HoloLens para aprender a nova posição (por exemplo, você moveu sua tabela de café para um novo ponto), mantenha o foco e mover ao redor dele.

### <a name="spatial-mapping"></a>Mapeamento espacial

Quando você inserir um novo espaço (ou carregar um já existente), você verá um gráfico de malha distribuindo sobre o espaço. Isso significa que o dispositivo está [mapeamento arredores](spatial-mapping-design.md). Se você estiver tendo problemas colocando hologramas, tente andando o espaço para que HoloLens podem mapeá-lo mais detalhadamente. Se seu HoloLens não é possível mapear o seu espaço ou estiver fora de calibragem, você pode entrar no modo limitado. No modo limitado, você não conseguirá colocar hologramas em seu ambiente.

### <a name="managing-your-spaces"></a>Gerenciar seus espaços

As seções de mapa e os diferentes espaços foram recolhidos em um único banco de dados armazenado localmente no dispositivo HoloLens.  O banco de dados do mapa é armazenado com segurança, com acesso disponível apenas para o sistema interno e nunca a um usuário do dispositivo, mesmo quando conectado a um PC e/ou usando o aplicativo do Explorador de arquivos.  Quando o bitlocker é habilitado, os dados de mapa armazenados também são criptografados.
Vários componentes do mapa existem quando hologramas são colocadas em locais diferentes sem um caminho connective entre os locais/hologramas.  Hologramas ancoradas na mesma seção mapa são considerados "próximo" no espaço atual existe é um desenvolvedor de API para exportar um pequeno subconjunto de "espaço atual" (uma parte o componente de mapa é reconhecido no momento) para habilitar cenários de holograma compartilhado.  Atualmente, não há nenhum mecanismo para baixar o banco de dados inteiro de todos os espaços foram mapeados.

#### <a name="wifi"></a>WiFi
Vs conectados. Não – desde que o Wi-Fi está habilitada, dados de mapa serão correlacionados com uma impressão digital de Wi-Fi, mesmo quando não conectado a um rede Wi-Fi real/roteador.  Isso ocorre porque a MAC endereço e intensidade do sinal (ou seja, Wi-Fi impressão digital) de um roteador está disponível sem se conectar a ele.  Identificação de rede (ou seja, o SSID, endereço MAC) não são enviadas à Microsoft e Wi-Fi todas as referências são mantidas locais o HoloLens.

Vs habilitados. Desabilitado – HoloLens sentido e lembre-se de espaços, mesmo quando o Wi-Fi for desabilitado, armazenando com segurança os dados do sensor quando hologramas são colocadas.  Sem as informações de Wi-Fi, o espaço e hologramas podem ser um pouco mais lentas reconhecer em um momento posterior, como o HoloLens precisa comparar verificações Active Directory para todas as âncoras holograma e armazenadas no dispositivo para "relocalize" na parte esquerda do mapa de seções de mapa.

#### <a name="environment-management"></a>Gerenciamento de ambiente
Há 2 configurações que permitem aos usuários para "Limpar" hologramas e causa HoloLens "esquecer um espaço".  Elas existem no "Hologramas e ambientes" no aplicativo configurações, com a segunda configuração também serão exibidos em "Privacidade" no aplicativo configurações.
1.  Excluir nas proximidades hologramas – ao selecionar essa configuração, HoloLens apagará hologramas tudo ancoradas e todos os dados de mapa armazenado para o "espaço atual" em que o dispositivo está localizado.  Uma nova seção mapa seria criada e armazenada no banco de dados para esse local, uma vez hologramas novamente são colocadas em que o mesmo espaço.
2.  Excluir todos os hologramas – ao selecionar essa configuração, o HoloLens apagará todos os dados de mapa e ancorados hologramas nos bancos de dados inteiros de espaços.  Nenhum hologramas serão redescobertas e qualquer hologramas precisam ser colocados recentemente para armazenar novamente as seções de mapa no banco de dados.


## <a name="hologram-quality"></a>Qualidade holograma

Hologramas podem ser colocadas em todo o ambiente — alto, baixo e em todo você — mas você poderá vê-los por meio de um [quadro holográfico](holographic-frame.md) que se encontra na frente de seus olhos. Para obter o melhor modo de exibição, certifique-se de ajustar o seu dispositivo para que você possa ver todo o quadro. E, não hesite em entrar para orientá-lo em torno de seu ambiente e explorar!

Para seus [hologramas](hologram.md) para procurar estável nítido e claro, o HoloLens precisa ser calibrado só para você. Quando você primeiro configura seu HoloLens, você será guiado através desse processo. No futuro, se hologramas não parecem corretas ou se você está vendo vários erros, você pode fazer ajustes.

### <a name="calibration"></a>Calibragem

Se seu hologramas parecer tremido ou tremidos, ou se você estiver tendo problemas colocando hologramas, a primeira coisa a tentar é o [aplicativo de calibragem](calibration.md). Esse aplicativo também pode ajudar se você estiver tendo quaisquer discomfort ao usar o HoloLens.

Para obter o aplicativo de calibragem, vá para Configurações > sistema > utilitários. Selecione Abrir calibragem e siga as instruções.

Se você executa o aplicativo de calibragem e ainda estiver tendo problemas de qualidade de holograma, ou você está vendo uma mensagem de "controle perdida" frequentes, experimente o aplicativo de ajuste do Sensor. Vá para Configurações > sistema > utilitários, selecione Abrir opções de ajuste de Sensor e siga as instruções.

Se outra pessoa irá usar o HoloLens, eles devem executar o aplicativo de calibragem primeiro para que o dispositivo está configurado corretamente para eles.

## <a name="see-also"></a>Consulte também
* [Design de mapeamento espacial](spatial-mapping-design.md)
* [Hologramas](hologram.md)
* [Calibragem](calibration.md)
