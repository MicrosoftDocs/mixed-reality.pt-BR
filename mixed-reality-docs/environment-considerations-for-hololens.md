---
title: Considerações de ambiente para o HoloLens
description: Obtenha a melhor experiência possível usando o HoloLens ao otimizar o dispositivo para seus olhos e seu ambiente. Muitos fatores ambientais diferentes são misturados para permitir o acompanhamento, mas como um desenvolvedor de realidade misturada, há vários fatores que você pode ter em mente para ajustar um espaço para melhorar os hologramas.
author: dorreneb
ms.author: dobrown
ms.date: 04/22/2019
ms.topic: article
keywords: quadro Holographic, campo de exibição, FOV, calibração, espaços, ambiente, instruções
ms.openlocfilehash: fd5c5020916b3fde6f91663135c3bc2b6c334b44
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69565992"
---
# <a name="environment-considerations-for-hololens"></a>Considerações de ambiente para o HoloLens

O HoloLens mistura o Holographic com o mundo "real", colocando hologramas no seu ambiente. Uma janela de aplicativo Holographic "trava" na parede, uma Holographic Ballerina gira na mesa, ouvidos de coelhinho está sobre o seu amigo involuntária. Quando você estiver usando um jogo ou aplicativo de imersão, o Holographic World se espalhará para preencher seus arredores, mas você ainda poderá ver e se movimentar pelo espaço.

Os hologramas que você colocar permanecerão onde você os colocou, mesmo se você desligar o dispositivo. 

## <a name="setting-up-an-environment"></a>Configurando um ambiente

Os dispositivos do HoloLens sabem como posicionar hologramas estáveis e precisos acompanhando os usuários em um espaço. Sem o acompanhamento adequado, o dispositivo não entende o ambiente ou o usuário dentro dele; portanto, os hologramas podem aparecer nos locais errados, não aparecem no mesmo ponto a cada vez ou não aparecem. Os dados usados para rastrear os usuários são representados no *mapa espacial*. 

O controle do desempenho é bastante influenciado pelo ambiente no qual o usuário está e o ajuste de um ambiente para induzir o acompanhamento estável e consistente é uma arte em vez de uma ciência. Muitos fatores ambientais diferentes são misturados para permitir o acompanhamento, mas como um desenvolvedor de realidade misturada, há vários fatores que você pode ter em mente para ajustar um espaço para um melhor acompanhamento.
 
### <a name="lighting"></a>Iluminação
A realidade mista do Windows usa a luz Visual para acompanhar o local do usuário. Quando um ambiente é muito brilhante, as câmeras podem ficar saturadas e nada é visto. Se o ambiente for muito escuro, as câmeras não poderão pegar informações suficientes e nada será visto. A iluminação deve ser uniforme e suficientemente brilhante que um humano possa ver sem esforço, mas não tão claro que a luz é difícil de examinar.

As áreas em que há pontos de luz brilhante em uma área de Dim geral também são problemáticas, uma vez que a câmera precisa ser ajustada ao se mover para dentro e para fora dos espaços brilhantes. Isso pode fazer com que o dispositivo "seja perdido" e considere que a alteração na luz equivale a uma alteração no local. Os níveis de luz estáveis em uma área resultarão em um melhor controle.

Qualquer iluminação externa também pode causar instabilidade no controlador, pois o sol pode variar consideravelmente ao longo do tempo. Por exemplo, o controle no mesmo espaço no verão versus o inverno pode produzir resultados drasticamente diferentes, pois a luz Secondhand externa pode ser maior em diferentes momentos do ano.

Se você tiver um luxmeter, um Lux de 500-1000 estável é um bom lugar para começar. 

#### <a name="types-of-lighting"></a>Tipos de iluminação
Tipos diferentes de luz em um espaço também podem influenciar o controle. O pulso de lâmpadas com a eletricidade AC em execução por ela – se a frequência AC for 50Hz, então os pulsos de luz em 50Hz. Para uma pessoa, essa Pulsing não é percebida. No entanto, a câmera ' 30fps ' do HoloLens vê essas alterações – alguns quadros estarão bem acesos, alguns ficarão insatisfatórios e outros serão superexpostos à medida que a câmera tentar compensar os pulsos leves.

Nos EUA, o padrão de frequência de eletricidade é 60, portanto, os pulsos de lâmpada são padronizados com a taxa de quadros de taxa de bits-60Hz de HoloLens alinhada com o Hololens de 30 FPS. No entanto, muitos países têm um padrão de frequência de AC de 50Hz, o que significa que alguns quadros do Hololens serão feitos durante pulsos e outros não. Em particular, a iluminação fluorescente na Europa tem sido conhecida por causar problemas. 

Há algumas coisas que você pode tentar resolver problemas de cintilação. A temperatura, a idade da lâmpada e os ciclos de aquecimento são causas comuns de oscilação fluorescente e substituição de lâmpadas pode ajudar. A restrição de lâmpadas e a garantia de que o desenho atual são constantes também podem ajudar. 

### <a name="items-in-a-space"></a>Itens em um espaço
O HoloLens usa pontos de referência ambientais exclusivos, também conhecidos como *recursos*, para se localizar em um espaço. 

Um dispositivo quase nunca pode rastrear em uma área de recursos insatisfatórios, pois o dispositivo não tem como saber onde está o espaço. A adição de recursos às paredes de um espaço é geralmente uma boa maneira de melhorar o controle. Todos os cartazes, símbolos dipostos a uma parede, plantas, objetos exclusivos ou outros itens semelhantes ajudam. Uma mesa confusa é um bom exemplo de um ambiente que leva a um bom acompanhamento: há muitos recursos diferentes em uma única área. 

Além disso, use recursos exclusivos no mesmo espaço. O mesmo pôster repetido várias vezes em uma parede, por exemplo, causará confusão no dispositivo, pois o HoloLens não saberá qual dos cartazes repetitivos ele está olhando. Uma maneira comum de adicionar recursos exclusivos é usar linhas de fita de mascaramento para criar padrões de nonrepetitve exclusivos ao longo das paredes e piso de um espaço. 

Uma boa pergunta é se perguntar: se você viu apenas uma pequena quantidade da cena, poderia se localizar exclusivamente no espaço? Caso contrário, é provável que o dispositivo também tenha problemas de acompanhamento.

#### <a name="wormholes"></a>Fendas espaciais
Se você tiver duas áreas ou regiões que parecem iguais, o rastreador poderá imaginar que são as mesmas. Isso resulta no dispositivo que se engana para pensar que ele é outro lugar. Chamamos esses tipos de áreas de *fenda espaciais*. 

Para evitar fendas espaciais, tente evitar áreas idênticas no mesmo espaço. As áreas idênticas às vezes podem incluir estações de fábrica, janelas em um prédio, racks de servidor ou estações de trabalho. As áreas de rotulagem ou a adição de recursos exclusivos a cada área de aparência semelhante podem ajudar a reduzir as fendas espaciais.
 
### <a name="movement-in-a-space"></a>Movimento em um espaço
Se o seu ambiente estiver constantemente mudando e mudando, o dispositivo não terá recursos estáveis para localização. 

Quanto mais objetos em movimento estiverem em um espaço, incluindo as pessoas, mais fácil será perder o controle. Mover as esteiras da transmissão, os itens em diferentes Estados de construção e muitas pessoas em um espaço têm sido conhecidos por causar problemas de controle.

O HoloLens pode se adaptar rapidamente a essas alterações, mas somente quando essa área estiver claramente visível para o dispositivo. As áreas que não são vistas com frequência podem atrasar por trás da realidade, o que pode causar erros no mapa espacial. Por exemplo, um usuário examina um amigo e, em seguida, gira enquanto o amigo sai da sala. Uma representação ' fantasma ' do Friend será mantida nos dados de mapeamento espacial até que o usuário Examine novamente o espaço vazio.
 
### <a name="proximity-of-the-user-to-items-in-the-space"></a>Proximidade do usuário a itens no espaço
Da mesma forma como os seres humanos não podem se concentrar bem em objetos próximos aos olhos, o HoloLens luta quando os objetos estão próximos de câmeras. Se um objeto estiver muito próximo de ser visto com ambas as câmeras ou se um objeto estiver bloqueando uma câmera, o dispositivo terá muito mais problemas com o acompanhamento do objeto. 

As câmeras podem ver não mais do que 15cm de um objeto.
 
### <a name="surfaces-in-a-space"></a>Superfícies em um espaço
Superfícies altamente reflexivas provavelmente terão uma aparência diferente, dependendo do ângulo, que afeta o controle. Imagine um carro totalmente novo – quando você se movimenta, a luz reflete e você vê diferentes objetos na superfície à medida que avança. Para o controlador, os diferentes objetos refletidos na superfície representam um ambiente de alteração e o dispositivo perde o rastreamento.

Objetos menos brilhantes são mais fáceis de controlar.

### <a name="wifi-fingerprint-considerations"></a>Considerações sobre impressão digital de WiFi
Desde que o WiFi esteja habilitado, os dados do mapa serão correlacionados com uma impressão digital WiFi, mesmo quando não estiverem conectados a um roteador/rede WiFi real. Sem as informações de WiFi, o espaço e os hologramas podem ser um pouco mais lentos de reconhecer. Se os sinais de WiFi mudarem significativamente, o dispositivo poderá considerar que ele está em um espaço diferente.

A identificação de rede (ou seja, SSID, endereço MAC) não é enviada à Microsoft e todas as referências de WiFi são mantidas localmente no HoloLens.

## <a name="mapping-new-spaces"></a>Mapeando novos espaços
Quando você inserir um novo espaço (ou carregar um existente), verá um gráfico de malha espalhando o espaço. Isso significa que seu dispositivo está mapeando seus arredores. Embora um HoloLens Aprenda um espaço ao longo do tempo, há [dicas e truques para mapear espaços](use-hololens-in-new-spaces.md). 

## <a name="environment-management"></a>Gerenciamento de ambiente
Há duas configurações que permitem aos usuários "limpar" os hologramas e fazer com que o HoloLens "Esqueça" um espaço.  Eles existem em "hologramas e ambientes" no aplicativo de configurações, com a segunda configuração também exibida em "privacidade" no aplicativo de configurações.

1.  Excluir hologramas próximos – ao selecionar essa configuração, o HoloLens apagará todos os hologramas ancorados e todos os dados de mapa armazenados para o "espaço atual" onde o dispositivo está localizado.  Uma nova seção de mapa seria criada e armazenada no banco de dados para esse local depois que os hologramas forem novamente colocados no mesmo espaço.

2.  Excluir todos os hologramas – ao selecionar essa configuração, o HoloLens apagará todos os dados do mapa e os hologramas ancorados em todos os bancos de dado de espaços.  Nenhum holograma será redescoberto e quaisquer hologramas precisarão ser colocados recentemente para armazenar novamente as seções do mapa no banco de dados.


## <a name="hologram-quality"></a>Qualidade do holograma

Os hologramas podem ser colocados em todo o ambiente – alta, baixa e tudo em seu lugar — mas você os verá por meio de um [quadro Holographic](holographic-frame.md) que fica na frente dos seus olhos. Para obter a melhor exibição, certifique-se de ajustar seu dispositivo para que você possa ver o quadro inteiro. E não hesite em abordar seu ambiente e explorar!

Para que seus [hologramas](hologram.md) pareçam nítidos, claros e estáveis, seu HoloLens precisa ser calibrado apenas para você. Ao configurar o HoloLens pela primeira vez, você será orientado por esse processo. Posteriormente, se os hologramas não parecerem corretos ou se você estiver vendo muitos erros, poderá fazer ajustes.

Se você estiver tendo problemas para mapear espaços, tente excluir os hologramas próximos e remapear o espaço.

### <a name="calibration"></a>Calibragem

Se os seus hologramas parecerem com tremulação ou tremidos, ou se você tiver problemas para colocar os hologramas, a primeira coisa a ser tentada é o [aplicativo](calibration.md)de calibragem. Esse aplicativo também pode ajudar se você estiver experimentando qualquer discomfort ao usar seu HoloLens.

Para acessar o aplicativo de calibragem, acesse Configurações > sistema > Utilitários. Selecione abrir calibragem e siga as instruções.

Se você executar o aplicativo de calibragem e ainda tiver problemas com a qualidade do holograma, ou se estiver vendo uma mensagem de "acompanhamento perdido" frequente, experimente o aplicativo de ajuste do sensor. Acesse Configurações > sistema > Utilitários, selecione abrir ajuste de sensor e siga as instruções.

Se outra pessoa estiver usando seu HoloLens, ele deverá executar o aplicativo de calibração primeiro para que o dispositivo seja configurado corretamente para eles.

## <a name="see-also"></a>Consulte também
* [Projeto de mapeamento espacial](spatial-mapping-design.md)
* [Hologramas](hologram.md)
* [Calibragem](calibration.md)
* [Usar o Hololens em novos espaços](use-hololens-in-new-spaces.md)
