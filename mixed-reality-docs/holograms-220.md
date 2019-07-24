---
title: MR espacial 220-som espacial
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes dos conceitos de som espaciais.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, som espacial
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526903"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br>

# <a name="mr-spatial-220-spatial-sound"></a>MR espacial 220: Som espacial

O [som espacial](spatial-sound.md) traz a vida para os hologramas e dá a eles presença em nosso mundo. Os hologramas são compostos por luz e som e, se você perder a visão de seus hologramas, o som espacial poderá ajudá-lo a encontrá-los. O som espacial não é como o som típico que você ouviria no rádio, é um som posicionado no espaço 3D. Com o som espacial, você pode fazer com que os hologramas pareçam estar por trás de você, ao lado de você ou mesmo à sua cabeça! Neste curso, você vai:

* Configure seu ambiente de desenvolvimento para usar o som espacial da Microsoft.
* Use o som espacial para aprimorar as interações.
* Use o som espacial em conjunto com o mapeamento espacial.
* Entenda as práticas recomendadas de design e mistura de som.
* Use o som para aprimorar os efeitos especiais e trazer o usuário para o mundo da realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>MR espacial 220: Som espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas](install-the-tools.md)corretas instaladas.
* Alguma capacidade C# básica de programação.
* Você deve ter concluído o [Sr noções básicas 101](holograms-101.md).
* Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) exigidos pelo projeto. Requer o Unity 2017,2 ou posterior.
  * Se você ainda precisar de suporte do Unity 5,6, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip). Esta versão pode não estar mais atualizada.
  * Se você ainda precisar de suporte do Unity 5,5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip). Esta versão pode não estar mais atualizada.
  * Se você ainda precisar de suporte do Unity 5,4, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip). Esta versão pode não estar mais atualizada.
* Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).

### <a name="errata-and-notes"></a>Errata e observações

* "Habilitar Apenas Meu Código" precisa ser desabilitado (desmarcado) no Visual Studio em ferramentas-> opções-> depuração para acessar os pontos de interrupção no código.

## <a name="chapter-1---unity-setup"></a>Capítulo 1 – configuração do Unity

### <a name="objectives"></a>Objetivos

* Altere a configuração de som do Unity para usar o som espacial da Microsoft.
* Adicionar som 3D a um objeto no Unity.

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **abrir**.
* Navegue até sua área de trabalho e localize a pasta que você cancelou anteriormente.
* Clique na pasta **Starting\Decibel** e pressione o botão **Selecionar pasta** .
* Aguarde até que o projeto seja carregado no Unity.
* No painel **projeto** , abra **Scenes\Decibel.Unity**.
* No painel **hierarquia** , expanda **hologramacollection** e selecione **P0LY**.
* No Inspetor, expanda o **áudio** e observe que não há nenhuma caixa de seleção **espacial** .

Por padrão, o Unity não carrega um plug-in spatializer. As etapas a seguir habilitarão o som espacial no projeto.

* No menu superior do Unity, vá para **editar > configurações do projeto > áudio**.
* Localize a lista suspensa **plug-in do Spatializer** e selecione **MS HRTF Spatializer**.
* No painel **hierarquia** , selecione **hologramacollection > P0LY**.
* No painel **Inspetor** , localize o componente **fonte de áudio** .
* Marque a  caixa de seleção espacialize.
* Arraste o controle deslizante de **mistura espacial** para **3D**ou digite **1** na caixa de edição.

Agora, criaremos o projeto no Unity e configuraremos a solução no Visual Studio.

1. No Unity, selecione **arquivo > configurações de Build**.
2. Clique em **Adicionar abrir cenas** para adicionar a cena.
3. Selecione **plataforma universal do Windows** na lista **plataforma** e clique em **alternar plataforma**.
4. Se você estiver desenvolvendo especificamente para o HoloLens, defina o **dispositivo de destino** para o **hololens**. Caso contrário, deixe em **qualquer dispositivo**.
5. Verifique se **tipo de compilação** está definido como **D3D** e se o **SDK** está definido para o **mais recente instalado** (que deve ser o SDK 16299 ou mais recente).
6. Clique em **Compilar**.
7. Crie uma **nova pasta** chamada "app".
8. Clique uma vez na pasta do **aplicativo** .
9. Pressione **Selecionar pasta**.

Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.

1. Abra a pasta do **aplicativo** .
2. Abra a **solução de Decibéi Visual Studio**.

Se estiver implantando no HoloLens:

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.
2. Clique na seta suspensa ao lado do botão computador local e selecione **computador remoto**.
3. Insira **o endereço IP do dispositivo de HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)** . Clique em **Selecionar**. Se você não souber o endereço IP do dispositivo, examine **configurações > rede & Internet > opções avançadas**.
4. Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**. Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com o Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).

Se estiver implantando em um headset de imersão:

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x64**.
2. Verifique se o destino de implantação está definido como **computador local**.
3. Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.

## <a name="chapter-2---spatial-sound-and-interaction"></a>Capítulo 2-som espacial e interação

### <a name="objectives"></a>Objetivos

* Aprimore o holograma de uso de um som.
* Direcionar o olhar do usuário usando o som.
* Forneça comentários sobre gestos usando som.

### <a name="part-1---enhancing-realism"></a>Parte 1-aprimorando o realm

#### <a name="key-concepts"></a>Conceitos Principais

* Esespaciair sons de holograma.
* As fontes de som devem ser colocadas em um local apropriado no holograma.

O local apropriado para o som vai depender do holograma. Por exemplo, se o holograma for de um humano, a origem do som deverá ser localizada perto da boca e não dos pés.

#### <a name="instructions"></a>Instruções

As instruções a seguir anexarão um som espacial a um holograma.

* No painel **hierarquia** , expanda **hologramacollection** e selecione **P0LY**.
* No painel **Inspetor** , na mensagem de **áudio**, clique no círculo ao lado de **AudioClip** e selecione  polifocalizar no pop-up.
* Clique no círculo ao lado de **saída** e selecione **SoundEffects** no pop-up.

O projeto Decibéi usa um componente **AudioMixer** do Unity para habilitar o ajuste dos níveis de som para grupos de sons. Ao agrupar sons dessa forma, o volume geral pode ser ajustado mantendo o volume relativo de cada som.

* Em **áudio**, expanda **configurações de som 3D**.
* Defina o **nível de Doppler** como **0**.

Definir o nível de Doppler como zero desabilita as alterações em pitch causadas pelo Motion (do holograma ou do usuário). Um exemplo clássico de Doppler é um carro com movimentação rápida. À medida que o carro se aproxima de um ouvinte estacionário, a inclinação do motor aumenta. Quando ele passa o ouvinte, a densidade diminui com distância.

### <a name="part-2---directing-the-users-gaze"></a>Parte 2-direcionando o olhar do usuário

#### <a name="key-concepts"></a>Conceitos Principais

* Use o som para chamar a atenção para hologramas importantes.
* Os ouvidos ajudam a direcionar onde devem ser os olhos.
* O cérebro tem algumas expectativas aprendidas.

Um exemplo de expectativas aprendidas é que os pássaros geralmente estão acima da cabeça dos seres humanos. Se um usuário ouve um som de pássaro, sua reação inicial é Pesquisar. Colocar um pássaro abaixo do usuário pode levar a eles voltados para a direção correta do som, mas não consegue encontrar o holograma com base na expectativa de precisar pesquisar.

#### <a name="instructions"></a>Instruções

As instruções a seguir permitem que P0LY sejam ocultadas para trás, para que você possa usar o som para localizar o holograma.

* No painel **hierarquia** , selecione **gerentes**.
* No painel **Inspetor** , encontre o **manipulador de entrada de fala**.
* Em **manipulador de entrada de fala**, expanda **ir ocultar**.
* Altere **nenhuma função** para **GoHide**.

![Chaves Ir para ocultar](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>Parte 3-comentários do gesto

#### <a name="key-concepts"></a>Conceitos Principais

* Fornecer ao usuário uma confirmação de gesto positivo usando som
* Não sobrecarregar os sons do usuário em alta
* Os sons sutis funcionam melhor – não obscurecem a experiência

#### <a name="instructions"></a>Instruções

* No painel **hierarquia** , expanda **hologramacollection**.
* Expanda **EnergyHub** e selecione **base**.
* No painel **Inspetor** , clique em **Adicionar componente** e adicionar **manipulador de som de gesto**.
* Em **manipulador de som de gesto**, clique no círculo próximo ao **clipe de navegação** e ao clipe de navegação **atualizado** e selecione **RotateClick** do pop-up para ambos.
* Clique duas vezes em "GestureSoundHandler" para carregar no Visual Studio.

O manipulador de som de gesto executa as seguintes tarefas:

* Criar e configurar um **áudio**.
* Coloque a **audioname** no local do gameobject apropriado .
* Reproduz o **AudioClip** associado ao gesto.

#### <a name="build-and-deploy"></a>Compilar e implantar

1. No Unity, selecione **arquivo > configurações de Build**.
2. Clique em **Compilar**.
3. Clique uma vez na pasta do **aplicativo** .
4. Pressione **Selecionar pasta**.

Verifique se a barra de ferramentas diz "versão", "x86" ou "x64" e "dispositivo remoto". Caso contrário, essa é a instância de codificação do Visual Studio. Talvez seja necessário reabrir a solução na pasta do aplicativo.

* Se solicitado, recarregue os arquivos de projeto.
* Como antes, implante a partir do Visual Studio.

Após a implantação do aplicativo:

* Observe como o som muda à medida que você se move ao P0LY.
* Digamos que *"Vá ocultar"* para fazer com que o P0LY se mova para um local por trás de você. Encontre-o pelo som.
* Olhar na base do hub de energia. Toque e arraste para a esquerda ou direita para girar o holograma e observe como o clique do som confirma o gesto.

Observação: Há um painel de texto que será rotulado com você. Isso conterá os comandos de voz disponíveis que você pode usar ao longo deste curso.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>Capítulo 3-som espacial e mapeamento espacial

### <a name="objectives"></a>Objetivos

* Confirme a interação entre os hologramas e o mundo real usando som.
* Occlude sons usando o mundo físico.

### <a name="part-1---physical-world-interaction"></a>Parte 1-interação física do mundo

#### <a name="key-concepts"></a>Conceitos Principais

* Os objetos físicos geralmente fazem um som ao encontrar uma superfície ou outro objeto.
* Os sons devem ser apropriados para o contexto na experiência.

Por exemplo, definir uma xícara em uma tabela deve fazer um som mais silencioso do que descartar um Boulder em uma parte do metal.

#### <a name="instructions"></a>Instruções

* No painel **hierarquia** , expanda **hologramacollection**.
* Expanda **EnergyHub**, selecione **base**.
* No painel **Inspetor** , clique em **Adicionar componente** e adicione **tocar para inserir com som e ação**.
* Em **toque para posicionar com som e ação**:
  * Verifique o **pai ao tocar**.
  * Defina **som de posicionamento** como **local**.
  * Defina **som de retirada** para **retirada**.
  * Pressione a + no canto inferior direito em ambos **na ação de retirada** e **na ação de posicionamento**. Arraste EnergyHub da cena para os campos **nenhum (objeto)** .
    * Em **ação de retirada**, clique em **sem função** -> **EnergyHubBase** -> **ResetAnimation**.
    * Em **ação de posicionamento**, clique em **sem função** -> **EnergyHubBase** -> **OnSelect**.

![Toque para posicionar com som e ação](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>Parte 2-som oclusão

#### <a name="key-concepts"></a>Conceitos Principais

* Som, como claro, pode ser obstruído.

Um exemplo clássico é uma sala de concerto. Quando um ouvinte está fora do Hall e a porta é fechada, a música parece muffled. Normalmente, também há uma redução no volume. Quando a porta é aberta, o espectro completo do som é ouvido no volume real. Sons de alta frequência geralmente são absorvidos mais do que frequências baixas.

#### <a name="instructions"></a>Instruções

* No painel **hierarquia** , expanda **hologramacollection** e selecione **P0LY**.
* No painel **Inspetor** , clique em **Adicionar componente** e adicionar **emissor de áudio**.

A classe emissor de áudio fornece os seguintes recursos:

* Restaura todas as alterações no volume de Audioname.
* Executa uma **física. RaycastNonAlloc** da posição do usuário na direção do gameobject ao  qual o **AudioEmitter** está anexado.

O método RaycastNonAlloc é usado como uma otimização de desempenho para limitar as alocações, bem como o número de resultados retornados.

* Para cada **IAudioInfluencer** encontrado, chama o método **ApplyEffect** .
* Para cada **IAudioInfluencer** anterior que não é mais encontrado, chame o método **RemoveEffect** .

Observe que as atualizações do AudioEmitter em escalas de tempo humano, em oposição a por quadro. Isso é feito porque as pessoas geralmente não se movem com rapidez suficiente para que o efeito precise ser atualizado com mais frequência do que cada trimestre ou metade de um segundo. Os hologramas que teleport rapidamente de um local para outro podem quebrar a ilusão.

* No painel **hierarquia** , expanda **hologramacollection**.
* Expanda **EnergyHub** e selecione **BlobOutside**.
* No painel **Inspetor** , clique em **Adicionar componente** e adicione **áudio Occluder**.
* Em **áudio Occluder**, defina a **frequência de corte** como **1500**.

Essa configuração limita as frequências de áudio para 1500 Hz e abaixo.

* Defina **passagem de volume** para **0,9**.

Essa configuração reduz o volume do áudio para 90% do seu nível atual.

O áudio Occluder implementa IAudioInfluencer para:

* Aplique um efeito de oclusão usando um **AudioLowPassFilter** que é anexado ao **áudio** , gerenciado, comprar o **AudioEmitter**.
* Aplica a atenuação de volume à Audioname.
* Desabilita o efeito definindo uma frequência de corte neutra e desabilitando o filtro.

A frequência usada como neutra é 22 kHz (22000 Hz). Essa frequência foi escolhida porque está acima da frequência máxima nominal que pode ser ouvida pelo Ear humano, isso não faz nenhum impacto discernido no som.

* No painel **hierarquia** , selecione **SpatialMapping**.
* No painel **Inspetor** , clique em **Adicionar componente** e adicione **áudio Occluder**.
* Em **áudio Occluder**, defina a **frequência de corte** como **750**.

Quando vários occluders estão no caminho entre o usuário e o **AudioEmitter**, a frequência mais baixa é aplicada ao filtro.

* Defina **passagem de volume** para **0,75**.

Quando vários occluders estão no caminho entre o usuário e o **AudioEmitter**, a passagem do volume é aplicada de aditivo.

* No painel **hierarquia** , selecione **gerentes**.
* No painel **Inspetor** , expanda **manipulador de entrada de fala**.
* Em **manipulador de entrada de fala**, expanda ir para o **encargo**.
* Altere **nenhuma função** para **GoCharge**.

![Chaves Custo](images/gocharge.png)

* Expanda **aqui**.
* Altere **nenhuma função** para **ComeBack**.

![Chaves Vem cá](images/comehere.png)

#### <a name="build-and-deploy"></a>Compilar e implantar

* Como antes, compile o projeto no Unity e implante-o no Visual Studio.

Após a implantação do aplicativo:

* Digamos que "faça o *encargo"* para que o P0LY Insira o Hub de energia.

Observe a alteração no som. Ele deve parecer muffled e um pouco mais silencioso. Se você for capaz de se posicionar com uma parede ou outro objeto entre você e o Hub de energia, você deve notar um Muffling adicional do som devido à oclusão pelo mundo real.

* Diga *"Venha aqui"* para que P0LY deixe o Hub de energia e se posicione na frente de você.

Observe que o som oclusão é removido quando o P0LY sai do hub de energia. Se você ainda estiver ouvindo oclusão, P0LY poderá ser obstruído pelo mundo real. Tente mudar para garantir que você tenha uma clara linha de visão para P0LY.

### <a name="part-3---room-models"></a>Parte 3-modelos de sala

#### <a name="key-concepts"></a>Conceitos Principais

* O tamanho do espaço fornece filas subliminal que contribuem para a localização de som.
* Os modelos de sala são definidos por**áudio**.
* O [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece código para definir o modelo de sala.
* Para experiências de realidade misturada, selecione o modelo de sala que melhor se adapta ao espaço do mundo real.

Se você estiver criando um cenário de realidade virtual, selecione o modelo de sala que melhor se adapta ao ambiente virtual.

## <a name="chapter-4---sound-design"></a>Capítulo 4-design de som

### <a name="objectives"></a>Objetivos

* Entenda as considerações sobre o design de som efetivo.
* Aprenda técnicas e diretrizes de combinação.

### <a name="part-1---sound-and-experience-design"></a>Parte 1-design de som e experiência

Esta seção aborda as principais considerações e diretrizes de design de som e experiência.

#### <a name="normalize-all-sounds"></a>Normalizar todos os sons

Isso evita a necessidade de código de caso especial para ajustar os níveis de volume por som, o que pode ser demorado e limita a capacidade de atualizar facilmente os arquivos de som.

#### <a name="design-for-an-untethered-experience"></a>Design de uma experiência não de compartilhamento de Internet

O HoloLens é um computador Holographic totalmente contido e desvinculado. Os usuários podem e usarão suas experiências ao se moverem. Certifique-se de testar sua mixagem de áudio ao percorrer.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>Emitir som de locais lógicos em seus hologramas

No mundo real, um cachorro não latido de sua parte final e a voz de um humano não vem de seus pés. Evite emitir seus sons de partes inesperadas de seus hologramas.

Para hologramas pequenos, é razoável ter uma emissão sonora do centro da geometria.

#### <a name="familiar-sounds-are-most-localizable"></a>Os sons conhecidos são mais localizáveis

A voz humana e a música são muito fáceis de localizar. Se alguém chamar seu nome, você poderá determinar com precisão a direção de que a voz veio e de quanto longe. Sons curtos e desconhecidos são mais difíceis de localizar.

#### <a name="be-cognizant-of-user-expectations"></a>Cognizant as expectativas dos usuários

A experiência de vida exerce uma parte em nossa capacidade de identificar o local de um som. Esse é um dos motivos pelos quais a voz humana é particularmente fácil de localizar. É importante estar atento às expectativas aprendidas do usuário ao colocar seus sons.

Por exemplo, quando alguém ouve uma música de pássaro, ele geralmente procura, pois os pássaros tendem a estar acima da linha de visão (voador ou em uma árvore). Não é incomum um usuário ativar a direção correta de um som, mas examinar a direção vertical incorreta e ficar confuso ou frustrado quando não conseguir encontrar o holograma.

#### <a name="avoid-hidden-emitters"></a>Evitar emissores ocultos

No mundo real, se ouvimos um som, geralmente podemos identificar o objeto que está emitindo o som. Isso também deve se manter verdadeiro em suas experiências. Pode ser muito desconcerto para os usuários ouvirem um som, saber de onde o som se origina e não conseguir ver um objeto.

Há algumas exceções a essa diretriz. Por exemplo, sons de ambiente como Crickets em um campo não precisam estar visíveis. A experiência de vida nos dá familiaridade com a origem desses sons sem a necessidade de vê-los.

### <a name="part-2---sound-mixing"></a>Parte 2-mixagem de som

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>Direcione sua combinação para o volume de 70% no HoloLens

As experiências de realidade misturada permitem que os hologramas sejam vistos no mundo real. Eles também devem permitir que sons do mundo real sejam ouvidos. Um destino de volume de 70% permite que o usuário Ouça o mundo junto com o som de sua experiência.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>O HoloLens em 100% volume deve se afogar em sons externos

Um nível de volume de 100% é semelhante a uma experiência de realidade virtual. Visualmente, o usuário é transportado para um mundo diferente. O mesmo deve conter verdadeiro forma audível.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Usar o AudioMixer do Unity para ajustar as categorias de sons

Ao projetar sua combinação, geralmente é útil criar categorias de som e ter a capacidade de aumentar ou diminuir seu volume como uma unidade. Isso retém os níveis relativos de cada som, ao mesmo tempo em que permite alterações rápidas e fáceis na combinação geral. As categorias comuns incluem; efeitos de som, Ambience, voz e música em segundo plano.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>Misturar sons com base no olhar do usuário

Muitas vezes, pode ser útil alterar a mistura de som em sua experiência com base em onde um usuário está olhando (ou não). Um uso comum para essa técnica é reduzir o nível de volume para hologramas que estão fora do quadro Holographic para tornar mais fácil para o usuário se concentrar nas informações em frente deles. Outro uso é aumentar o volume de um som para chamar a atenção do usuário para um evento importante.

#### <a name="building-your-mix"></a>Criando sua combinação

Ao criar sua combinação, é recomendável começar com o áudio de segundo plano da sua experiência e adicionar camadas com base na importância. Geralmente, isso resulta em cada camada sendo mais alta do que a anterior.

Ao imaginar sua mistura como um funil invertido, com o menos importante (e geralmente sons mais silenciosos) na parte inferior, é recomendável estruturar sua mistura semelhante ao diagrama a seguir.

![Estrutura da combinação de som](images/soundlevels.png)

A voz é um cenário interessante. Com base na experiência que você está criando, talvez você queira ter um som estéreo (não localizado) ou para espacialar sua voz. Duas experiências publicadas da Microsoft ilustram excelentes exemplos de cada cenário.

O [HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa uma voz estéreo. Quando o narrador está descrevendo o local que está sendo exibido, o som é consistente e não varia de acordo com a posição do usuário. Isso permite que o narrador descreva a cena sem sair dos sons espaciais do ambiente.

Os [fragmentos](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizam uma voz espacialada na forma de uma detecção. A voz da detecção é usada para ajudar a levar a atenção do usuário a uma pista importante como se um humano real estivesse na sala. Isso permite um sentido ainda maior de imersão na experiência de resolver o mistério.

### <a name="part-3--performance"></a>Parte 3-desempenho

#### <a name="cpu-usage"></a>Uso da CPU

Ao usar o som espacial, 10-12 emissores consumirão aproximadamente 12% da CPU.

#### <a name="stream-long-audio-files"></a>Transmitir arquivos de áudio longos

Os dados de áudio podem ser grandes, especialmente em taxas de exemplo comuns (44,1 e 48 kHz). Uma regra geral é que os arquivos de áudio com mais de 5-10 segundos devem ser transmitidos para reduzir o uso de memória do aplicativo.

No Unity, você pode marcar um arquivo de áudio para streaming nas configurações de importação do arquivo.

![Configurações de importação de áudio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>Capítulo 5-efeitos especiais

### <a name="objectives"></a>Objetivos

* Adicione profundidade a "janelas mágicas".
* Traga o usuário para o mundo virtual.

### <a name="magic-windows"></a>Janelas mágicas

#### <a name="key-concepts"></a>Conceitos Principais

* Criar exibições em um mundo oculto é visualmente atraente.
* Aprimore o realm adicionando efeitos de áudio quando um holograma ou o usuário estiver perto do mundo oculto.

#### <a name="instructions"></a>Instruções

* No painel **hierarquia** , expanda **hologramacollection** e selecione **Underworld**.
* Expanda **Underworld** e selecione voicename.
* No painel **Inspetor** , clique em **Adicionar componente** e adicionar **efeito de voz do usuário**.

Um componente de **aúdio** será adicionado à **voiceprovider**.

* Em **áudio**, defina **saída** para **UserVoice (mixer)** .
* Marque a  caixa de seleção espacialize.
* Arraste o controle deslizante de **mistura espacial** para **3D**ou digite **1** na caixa de edição.
* Expanda **configurações de som 3D**.
* Defina o **nível de Doppler** como **0**.
* Em **efeito de voz do usuário**, defina **objeto pai** como o **Underworld** da cena.
* Defina a **distância máxima** como **1**.

Definir a **distância máxima** informa o **efeito de voz do usuário** como fechar o usuário deve ser ao objeto pai antes de o efeito ser habilitado.

* Em **efeito de voz do usuário**, expanda **parâmetros Chorus**.
* Defina **profundidade** como **0,1**.
* Defina **tocar 1 volume**, **toque em 2 volume** e **toque em 3 volume** para **0,8**.
* Defina o **volume de som original** como **0,5**.

As configurações anteriores configuram os parâmetros do Unity **AudioChorusFilter** usado para adicionar riqueza à voz do usuário.

* Em **efeito de voz do usuário**, expanda **parâmetros de eco**.
* Definir **atraso** como **300**
* Defina a **taxa de decaimento** como **0,2**.
* Defina o **volume de som original** como **0**.

As configurações anteriores configuram os parâmetros do Unity **AudioEchoFilter** usado para fazer com que a voz do usuário seja ecoada.

O script de efeito de voz do usuário é responsável por:

* Medindo a distância entre o usuário e  o gameobject ao qual o script está anexado.
* Determinando se o usuário está voltado para o gameobject.

O usuário deve estar voltado para o gameobject, independentemente da distância, para que o efeito seja habilitado.

* Aplicando e configurando um **AudioChorusFilter** e um **AudioEchoFilter** para a **audioname**.
* Desabilitando o efeito, desabilitando os filtros.

O efeito de voz do usuário usa o componente seletor de fluxo do MIC, do [MixedRealityToolkit para o Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), para selecionar o fluxo de voz de alta qualidade e roteá-lo no sistema de áudio do Unity.

* No painel **hierarquia** , selecione **gerentes**.
* No painel **Inspetor** , expanda **manipulador de entrada de fala**.
* Em **manipulador de entrada de fala**, expanda **Mostrar Underworld**.
* Altere **nenhuma função** para **UnderworldBase. OnEnable**.

![Chaves Mostrar Underworld](images/showunderworld.png)

* Expanda **ocultar Underworld**.
* Altere **nenhuma função** para **UnderworldBase. ondisable**.

![Chaves Ocultar Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>Compilar e implantar

* Como antes, compile o projeto no Unity e implante-o no Visual Studio.

Após a implantação do aplicativo:

* Face de uma superfície (parede, piso, tabela) e diga *"mostrar Underworld"* .

O Underworld será mostrado e todos os outros hologramas serão ocultados. Se você não vir o Underworld, verifique se está enfrentando uma superfície do mundo real.

* Abordagem em 1 metro do holograma do Underworld e comece a conversar.

Agora há efeitos de áudio aplicados à sua voz!

* Desative o Underworld e observe como o efeito não é mais aplicado.
* Diga *"Hide Underworld"* para ocultar o Underworld.

O Underworld ficará oculto e os hologramas ocultos anteriormente serão exibidos novamente.

## <a name="the-end"></a>Fim

Parabéns! Agora você concluiu **o Sr Spatial 220: Som**espacial.

Ouça o mundo e dê vida às suas experiências com o som!
