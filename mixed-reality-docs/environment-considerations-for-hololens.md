---
title: Considerações sobre o ambiente para HoloLens
description: Obter a melhor experiência possível usando HoloLens, quando você otimiza o dispositivo para seu ambiente e olhos. Muitos fatores ambientais diferentes são combinados em conjunto para habilitar o controle, mas há vários fatores como um desenvolvedor de realidade misturada, você pode ter em mente para ajustar um espaço para hologramas melhor.
author: dorreneb
ms.author: dobrown
ms.date: 04/22/2019
ms.topic: article
keywords: quadro holográfico, campo de visão, fov, calibração, espaços, ambiente, instruções
ms.openlocfilehash: 0070455792e09cd59741362b201ca6b7b9af0aec
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670178"
---
# <a name="environment-considerations-for-hololens"></a>Considerações sobre o ambiente para HoloLens

HoloLens que combina os holographic com o mundo "real", colocando hologramas em seu ambiente. Uma janela do aplicativo holográfica "trava" na parede, uma ballerina holográfica gira sobre o table-top, ouvidos coelho ficam na parte superior do cabeçalho do seu amigo involuntária. Quando você estiver usando um aplicativo ou jogo imersivo, o mundo holográfico espalhará para preencher o seu ambiente, mas você ainda poderá ver e mover-se o espaço.

As hologramas que você colocar permanecerão onde você os colocou, mesmo se você desativar seu dispositivo. 

## <a name="setting-up-an-environment"></a>Como configurar um ambiente

Dispositivos do HoloLens aprende como colocar hologramas estáveis e precisas por *acompanhamento* usuários em um espaço. Sem rastreamento adequado, o dispositivo não compreender o ambiente ou o usuário dentro dela - para que hologramas podem aparecer em locais errados, não aparecer no mesmo lugar cada vez ou não aparecer de forma alguma.

Acompanhamento de desempenho é amplamente influenciado pelo ambiente do qual que o usuário está no e ajuste de um ambiente para induzir estável e consistente de acompanhamento é uma arte, em vez de uma ciência. Muitos fatores ambientais diferentes são combinados em conjunto para habilitar o controle, mas há vários fatores como um desenvolvedor de realidade misturada, você pode ter em mente para ajustar um espaço para ter melhor acompanhamento.
 
### <a name="lighting"></a>Iluminação
Realidade mista do Windows usa luz visual para acompanhar a localização do usuário. Quando um ambiente está muito claro, podem obter saturadas, câmeras, e nada é visto. Se o ambiente está muito escuro, câmeras não podem acompanhar informações suficientes e nada é visto. Iluminação deve ser o mesmo e suficientemente brilhante que uma pessoa pode ver sem esforço, mas não céu que a luz é dolorosa de examinar.

Áreas em que não há pontos de luz brilhante em uma área geral dim também são problemáticos, como a câmera precisa se ajustar ao mover de entrada e saída de espaços brilhantes. Isso pode causar o dispositivo para "obter perdido" e acho que a alteração na luz equivale a uma alteração no local. Níveis de luz estáveis em uma área leva a ter melhor acompanhamento.

Nenhuma Iluminação externa também pode causar instabilidade no controlador, como o sol pode variar consideravelmente ao longo do tempo. Por exemplo, rastreamento no mesmo espaço no verão versus inverno pode produzir resultados drasticamente diferentes, como a luz secondhand fora pode ser mais alta em diferentes momentos do ano.

Se você tiver um luxmeter, uma constante lux de 500 a 1000 é um bom lugar para começar. 

#### <a name="types-of-lighting"></a>Tipos de iluminação
Diferentes tipos de luz em um espaço também podem influenciar o rastreamento. As lâmpadas de pulso com eletricidade CA em execução por meio dele - se a frequência de AC for 50Hz, em seguida, a luz intermitentes pulsos de 50Hz. Para uma pessoa, não é percebido esse pulso. No entanto, câmera de 30fps dos HoloLens vê essas alterações - alguns quadros será bem iluminados, alguns serão iluminados mal e alguns serão excessivamente exposto como a câmera tenta compensar os pulsos de luz.

Nos EUA, a frequência de eletricidade padrão é 60Hz, para que os pulsos de lâmpada são padronizados com taxa de quadros dos HoloLens - 60Hz pulsos se alinham com a taxa de quadros do Hololens 30 FPS. No entanto, muitos países têm um padrão de frequência de AC de 50Hz, o que significa que alguns quadros Hololens serão tomados durante pulsos, mas outras não. Em particular, fluorescente na Europa conhecido por causar problemas. 

Há algumas coisas que você pode tentar resolver os problemas de cintilação. Temperatura, Bulbo idade e ciclos de aquecimento são causas comuns de cintilação fluorescentes e substituir as lâmpadas pode ajudar. Também podem ajudar a reforçar as lâmpadas e certificar-se de que desenha atual é constantes. 

### <a name="items-in-a-space"></a>Itens em um espaço
HoloLens usam pontos de referência de ambientais exclusivos, também conhecido como *recursos*, para localizar-se em um espaço. 

Um dispositivo pode controlar quase nunca em uma área de recurso ruim, pois o dispositivo não tem como saber onde no espaço que ele é. Adicionando recursos às paredes de um espaço é geralmente uma boa maneira de melhorar o acompanhamento. Cartazes, símbolos colados uma parede, plantas, objetos exclusivos ou outros itens semelhantes toda a Ajuda. Uma mesa confusa é um bom exemplo de um ambiente que leva a BOM acompanhamento – há muitos recursos diferentes em uma única área. 

Além disso, use os recursos exclusivos no mesmo espaço. O mesmo pôster repetida várias vezes ao longo de uma parede, por exemplo, fará com que confusão de dispositivo como o HoloLens não saberão qual dos cartazes repetitivos está observando. Uma maneira comum de adicionar recursos exclusivos é usar linhas de fita de mascaramento para criar exclusivo, padrões de nonrepetitve ao longo da paredes e andar de um espaço. 

É uma boa pergunta se perguntar - se você viu apenas uma pequena quantidade de cena, você exclusivamente localizou por conta própria no espaço? Caso contrário, é provável que o dispositivo terá problemas de controle também.

#### <a name="wormholes"></a>Fendas espaciais
Se você tiver duas áreas ou regiões que têm a mesma aparência, o controlador pode pensar que eles forem iguais. Isso resulta em enganar em si a pensar que dispositivo está em outro lugar. Chamamos esses tipos de áreas repetitivas *fendas espaciais*. 

Para evitar fendas espaciais, tente evitar áreas idênticas no mesmo espaço. Áreas idênticas às vezes, podem incluir as estações de fábrica, o windows em um prédio, racks de servidores ou estações de trabalho. Áreas de rotulagem ou adicionar recursos exclusivos para cada áreas semelhantes pode ajudar a atenuar fendas espaciais.
 
### <a name="temporal-stability-of-a-space"></a>Estabilidade temporal de um espaço
Se seu ambiente está constantemente mudando e a alteração, o dispositivo não tem nenhum recurso estável para localizar contra. 

O mais movimentação de objetos que estão em um espaço, incluindo pessoas, mais fácil é a perda de acompanhamento. Movendo belts da transportadora, itens em diferentes estados de construção e muitas pessoas em um espaço com são conhecidos para fazer com que o acompanhamento de problemas.
 
### <a name="proximity-of-the-user-to-items-in-the-space"></a>Proximidade do usuário para itens no espaço
Da mesma forma como as pessoas não podem se concentrar bem em objetos de perto os olhos, HoloLens luta quando objetos estão próximas de TI câmeras. Se um objeto é muito próximo sejam vistas com ambas as câmeras, ou se um objeto está bloqueando uma câmera, o dispositivo terá problemas muito mais com o controle com o objeto. 

As câmeras podem ver próximo de 15cm de um objeto.
 
### <a name="surfaces-in-a-space"></a>Superfícies em um espaço
Superfícies altamente refletivas provavelmente terá uma aparência diferentes, dependendo do ângulo, o que afeta o controle. Considere um carro novo - quando você move ao redor dela, a luz reflete e você ver diferentes objetos na superfície de conforme você move. Ao controlador de diferentes objetos refletem no surface representam um ambiente em constante mudança e o dispositivo perde o controle.

Menos objetos brilhantes são mais fáceis de acompanhar contra.

### <a name="wifi-fingerprint-considerations"></a>Considerações de impressão digital de Wi-Fi
Desde que o Wi-Fi está habilitado, os dados de mapa serão ser correlacionados com uma impressão digital de Wi-Fi, mesmo quando não conectado a um rede Wi-Fi real/roteador. Sem informações de Wi-Fi, o espaço e hologramas podem ser um pouco mais lentas reconhecer. Se os sinais Wi-Fi alterar significativamente, o dispositivo pode pensar que isso é um espaço diferente completamente.

Identificação de rede (ou seja, o SSID, endereço MAC) não são enviadas à Microsoft e Wi-Fi todas as referências são mantidas locais o HoloLens.

## <a name="mapping-new-spaces"></a>Mapeando novos espaços
Quando você inserir um novo espaço (ou carregar um já existente), você verá um gráfico de malha distribuindo sobre o espaço. Isso significa que o dispositivo está [mapeamento arredores](spatial-mapping-design.md). 

Se você estiver tendo problemas colocando hologramas, tente andando o espaço para que HoloLens podem mapeá-lo mais detalhadamente. 

Se seu HoloLens não é possível mapear o seu espaço ou estiver fora de calibragem, você pode entrar no modo limitado. No modo limitado, você não conseguirá colocar hologramas em seu ambiente.

## <a name="environment-management"></a>Gerenciamento de ambiente
Há duas configurações que permitem aos usuários para "Limpar" hologramas e causa HoloLens a um espaço de "Ignorar".  Elas existem no "Hologramas e ambientes" no aplicativo configurações, com a segunda configuração também serão exibidos em "Privacidade" no aplicativo configurações.

1.  Excluir nas proximidades hologramas – ao selecionar essa configuração, HoloLens apagará hologramas tudo ancoradas e todos os dados de mapa armazenado para o "espaço atual" em que o dispositivo está localizado.  Uma nova seção mapa seria criada e armazenada no banco de dados para esse local, uma vez hologramas novamente são colocadas em que o mesmo espaço.

2.  Excluir todos os hologramas – ao selecionar essa configuração, o HoloLens apagará todos os dados de mapa e ancorados hologramas nos bancos de dados inteiros de espaços.  Nenhum hologramas serão redescobertas e qualquer hologramas precisam ser colocados recentemente para armazenar novamente as seções de mapa no banco de dados.

### <a name="managing-your-spaces"></a>Gerenciar seus espaços

As seções de mapa e os diferentes espaços foram recolhidos em um único banco de dados armazenado localmente no dispositivo HoloLens. O banco de dados do mapa é armazenado com segurança, com acesso disponível apenas para o sistema interno e nunca a um usuário do dispositivo, mesmo quando conectado a um PC e/ou usando o aplicativo do Explorador de arquivos. Quando o bitlocker é habilitado, os dados de mapa armazenados também são criptografados.

Vários componentes do mapa existem quando hologramas são colocadas em locais diferentes sem um caminho connective entre os locais/hologramas.  Hologramas ancoradas na mesma seção mapa são consideradas "próximo" no espaço do atual.

Há uma API de desenvolvedor para exportar um pequeno subconjunto de "espaço atual" (uma parte o componente de mapa é reconhecido no momento) para habilitar cenários de holograma compartilhado.  Atualmente, não há nenhum mecanismo para baixar o banco de dados inteiro de todos os espaços foram mapeados.


## <a name="hologram-quality"></a>Qualidade holograma

Hologramas podem ser colocadas em todo o ambiente — alto, baixo e em todo você — mas você poderá vê-los por meio de um [quadro holográfico](holographic-frame.md) que se encontra na frente de seus olhos. Para obter o melhor modo de exibição, certifique-se de ajustar o seu dispositivo para que você possa ver todo o quadro. E, não hesite em entrar para orientá-lo em torno de seu ambiente e explorar!

Para seus [hologramas](hologram.md) para procurar estável nítido e claro, o HoloLens precisa ser calibrado só para você. Quando você primeiro configura seu HoloLens, você será guiado através desse processo. No futuro, se hologramas não parecem corretas ou se você está vendo vários erros, você pode fazer ajustes.

### <a name="calibration"></a>Calibragem

Se seu hologramas parecer tremido ou tremidos, ou se você estiver tendo problemas colocando hologramas, a primeira coisa a tentar é o [aplicativo de calibragem](calibration.md). Esse aplicativo também pode ajudar se você estiver tendo quaisquer discomfort ao usar o HoloLens.

Para obter o aplicativo de calibragem, vá para Configurações > sistema > utilitários. Selecione Abrir calibragem e siga as instruções.

Se você executa o aplicativo de calibragem e ainda estiver tendo problemas de qualidade de holograma, ou você está vendo uma mensagem de "controle perdida" frequentes, experimente o aplicativo de ajuste do Sensor. Vá para Configurações > sistema > utilitários, selecione Abrir opções de ajuste de Sensor e siga as instruções.

Se outra pessoa irá usar o HoloLens, eles devem executar o aplicativo de calibragem primeiro para que o dispositivo está configurado corretamente para eles.

## <a name="see-also"></a>Consulte também
* [Projeto de mapeamento espacial](spatial-mapping-design.md)
* [Hologramas](hologram.md)
* [Calibragem](calibration.md)
