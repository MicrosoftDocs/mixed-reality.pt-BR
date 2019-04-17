---
title: MR espacial 220 - som espacial
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para saber os detalhes dos conceitos de som espaciais.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, som espacial
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589375"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-spatial-220-spatial-sound"></a>MR Spatial 220: Som espacial

[Som espacial](spatial-sound.md) dá vida em hologramas e lhes presença em nosso mundo. Hologramas são compostas de luz e som e se você perder de vista seu hologramas, espacial som pode ajudá-lo a encontrá-los. Som espacial não é como o som típico que você teria uma resposta no rádio, é o som que está posicionado no espaço 3D. Com o som espacial, você pode fazer hologramas som que estão atrás de você, ao lado de você, ou até mesmo em sua cabeça! Neste curso, você irá:

* Configure seu ambiente de desenvolvimento para usar o Microsoft Spatial Sound.
* Use som espacial para aprimorar as interações.
* Use som espacial em conjunto com o mapeamento espacial.
* Entenda o design de som e misturar as práticas recomendadas.
* Usar som para aprimorar efeitos especiais e trazer o usuário para o mundo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td>MR Spatial 220: Som espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).
* Alguns basic C# capacidade de programação.
* Você deve ter concluído [MR Noções básicas de 101](holograms-101.md).
* Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) exigidos pelo projeto. Requer o Unity 2017.2 ou posterior.
  * Se você ainda precisar de suporte do Unity 5.6, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip). Esta versão não pode ser atualizada.
  * Se você ainda precisar de suporte do Unity 5.5, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip). Esta versão não pode ser atualizada.
  * Se você ainda precisar de suporte de Unity 5.4, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip). Esta versão não pode ser atualizada.
* Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).

### <a name="errata-and-notes"></a>Errata e notas

* "Habilitar apenas meu código" precisa ser desabilitado (*desmarcado*) no Visual Studio em Ferramentas -> Opções -> depuração para usar pontos de interrupção em seu código.

## <a name="chapter-1---unity-setup"></a>Capítulo 1 - instalação do Unity

### <a name="objectives"></a>Objetivos

* Altere configuração de som do Unity para usar o Microsoft Spatial Sound.
* Adicione som 3D a um objeto no Unity.

### <a name="instructions"></a>Instruções

* Inicie o Unity.
* Selecione **aberto**.
* A área de trabalho e localizar a pasta que você navegue anteriormente não arquivadas.
* Clique no **Starting\Decibel** pasta e, em seguida, pressione a **Selecionar pasta** botão.
* Aguarde até que o projeto carregar no Unity.
* No **Project** painel, abra **Scenes\Decibel.unity**.
* No **hierarquia** do painel, expanda **HologramCollection** e selecione **P0LY**.
* No Inspetor de propriedades, expanda **AudioSource** e observe que não há nenhum **Spatialize** caixa de seleção.

Por padrão, o Unity não carrega um plug-in spatializer. As etapas a seguir permitirá espacial som no projeto.

* No menu superior do Unity, acesse **Editar > configurações do projeto > áudio**.
* Localizar o **plug-in do Spatializer** dropdown e selecione **MS HRTF Spatializer**.
* No **hierarquia** painel, selecione **HologramCollection > P0LY**.
* No **Inspector** do painel, localize a **Audio Source** componente.
* Verifique as **Spatialize** caixa de seleção.
* Arraste o **Blend espacial** controle deslizante até **3D**, ou insira **1** na caixa de edição.

Agora podemos compilar o projeto no Unity e configurar a solução no Visual Studio.

1. No Unity, selecione **arquivo > configurações de Build**.
2. Clique em **cenas abra Adicionar** para adicionar a cena.
3. Selecione **plataforma Universal do Windows** na **plataforma** lista e clique em **alternar plataforma**.
4. Se você estiver desenvolvendo especificamente para HoloLens, defina **dispositivo de destino** à **HoloLens**. Caso contrário, deixe-nos **qualquer dispositivo**.
5. Certifique-se **Build Type** é definido como **D3D** e **SDK** é definido como **mais recente instalada** (que deve ser SDK 16299 ou mais recente).
6. Clique em **Compilar**.
7. Criar uma **nova pasta** chamado "App".
8. Único clique a **aplicativo** pasta.
9. Pressione **Selecionar pasta**.

Quando Unity é feito, será exibida uma janela do Explorador de arquivos.

1. Abra o **aplicativo** pasta.
2. Abra o **solução do Visual Studio decibéis**.

Se a implantação para o HoloLens:

1. Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x86**.
2. Clique na lista suspensa na seta ao lado do botão de computador Local e selecione **computador remoto**.
3. Insira **seu endereço IP do dispositivo HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)**. Clique em **Selecionar**. Se você não souber o endereço IP do dispositivo, examine **Configurações > rede e Internet > Opções avançadas de**.
4. Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**. Se essa for a primeira vez em que implantar seu dispositivo, você precisará [emparelhá-lo com o Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).

Se implantar em um fone de ouvido imersivo:

1. Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x64**.
2. Verifique se o destino de implantação é definido como **computador Local**.
3. Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.

## <a name="chapter-2---spatial-sound-and-interaction"></a>Capítulo 2 - interação e som espacial

### <a name="objectives"></a>Objetivos

* Aprimore o realismo holograma usando o som.
* Direcione olhar do usuário usando o som.
* Fornece comentários de gesto, uso de som.

### <a name="part-1---enhancing-realism"></a>Parte 1 - realismo melhorando

#### <a name="key-concepts"></a>Conceitos Principais

* Spatialize sons holograma.
* Fontes de som devem ser colocados em um local apropriado no holograma.

O local apropriado para o som será dependem de holograma. Por exemplo, se o holograma for de um ser humano, a fonte de som deve constar perto de boca e não os pés.

#### <a name="instructions"></a>Instruções

As instruções a seguir se anexará um som spatialized um holograma.

* No **hierarquia** do painel, expanda **HologramCollection** e selecione **P0LY**.
* No **Inspector** painel, o **AudioSource**, clique no círculo ao lado de **AudioClip** e selecione **PolyHover** de pop-up.
* Clique no círculo ao lado **saída** e selecione **SoundEffects** de pop-up.

Projeto decibéis usa um Unity **AudioMixer** para permitir que ajustar os níveis de som para grupos de sons. Pelo agrupamento sons dessa forma, o volume total pode ser ajustado, mantendo o volume relativo de cada som.

* No **AudioSource**, expanda **configurações de som 3D**.
* Definir **Doppler em razão nível** à **0**.

Definindo Doppler em razão nível às alterações zero desabilita no tom causado pelo motion (seja o holograma ou o usuário). Um exemplo clássico de Doppler em razão é que um carro ágeis. Como o carro se aproxima de um ouvinte estacionário, aumenta o tom do mecanismo. Ao passar o ouvinte, o tom reduz com distância.

### <a name="part-2---directing-the-users-gaze"></a>Parte 2 - direcionando olhar do usuário

#### <a name="key-concepts"></a>Conceitos Principais

* Usar som para chamar a atenção para hologramas importantes.
* Os ouvidos ajudam a direcionar onde procurar os olhos.
* O cérebro tem algumas expectativas aprendidas.

Um exemplo de expectativas aprendidos é pássaros geralmente são acima de cabeça de seres humanos. Se um usuário ouve um som bird, sua reação inicial é pesquisar. Colocar um pássaro abaixo do usuário pode levar a eles voltados para a direção correta do som, mas não ser capaz de localizar o holograma com base na expectativa de que precisam pesquisar.

#### <a name="instructions"></a>Instruções

As instruções a seguir permitem P0LY ocultar atrás de você, para que você pode usar som para localizar o holograma.

* No **hierarquia** painel, selecione **gerenciadores**.
* No **Inspector** do painel, localize **manipulador de entrada de fala**.
* Na **manipulador de entrada de fala**, expanda **vá ocultar**.
* Alteração **nenhuma função** à **PolyActions.GoHide**.

![palavra-chave: Ocultar vá](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>Parte 3 - comentários de gesto

#### <a name="key-concepts"></a>Conceitos Principais

* Fornecer ao usuário usando o som de confirmação de gesto positivo
* Não sobrecarregar o usuário - get sons excessivamente altos da forma
* Sons sutis funcionam melhor - não obscurecem a experiência

#### <a name="instructions"></a>Instruções

* No **hierarquia** do painel, expanda **HologramCollection**.
* Expandir **EnergyHub** e selecione **Base**.
* No **Inspector** do painel, clique em **Add Component** e adicione **manipulador do gesto de som**.
* Na **manipulador do gesto de som**, clique no círculo ao lado de **navegação iniciado Clip** e **navegação atualizado Clip** e selecione **RotateClick**de pop-up para ambos.
* Clique duas vezes em "GestureSoundHandler" para carregar no Visual Studio.

Manipulador de gesto som executa as seguintes tarefas:

* Criar e configurar uma **AudioSource**.
* Coloque o **AudioSource** no local do apropriado **GameObject**.
* Reproduz o **AudioClip** associadas ao gesto.

#### <a name="build-and-deploy"></a>Criar e implantar

1. No Unity, selecione **arquivo > configurações de Build**.
2. Clique em **Compilar**.
3. Único clique a **aplicativo** pasta.
4. Pressione **Selecionar pasta**.

Verifique se a barra de ferramentas diz "Versão", "x86" ou "x64" e "Dispositivo remoto". Caso contrário, a instância de codificação do Visual Studio. Talvez você precise reabra a solução da pasta de aplicativo.

* Se solicitado, recarregue os arquivos de projeto.
* Como antes, implante do Visual Studio.

Depois que o aplicativo é implantado:

* Observe como o som é alterado conforme você movimenta P0LY.
* Digamos *"Ocultar ir"* fazer P0LY mover para um local atrás de você. Para encontrá-lo pelo som.
* Mantenha o foco na base do Hub de energia. Toque e arraste a esquerda ou direita para girar o holograma e observe como o som clicando em confirma o gesto.

Observação: Há um painel de texto que será tag-along com você. Isso irá conter os comandos de voz disponíveis que podem ser usados durante o curso.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>Capítulo 3 - mapeamento espacial do som e espacial

### <a name="objectives"></a>Objetivos

* Confirme a interação entre hologramas e o mundo real usando o som.
* Occlude som usando mundo físico.

### <a name="part-1---physical-world-interaction"></a>Parte 1 – interação do mundo físico

#### <a name="key-concepts"></a>Conceitos Principais

* Objetos físicos geralmente emita um som quando se deparar com uma superfície ou outro objeto.
* Sons devem ser apropriada em uma experiência de contexto.

Por exemplo, definindo uma xícara em uma tabela deve emitir um som mais discreta que descartar um boulder em um pedaço de metal.

#### <a name="instructions"></a>Instruções

* No **hierarquia** do painel, expanda **HologramCollection**.
* Expandir **EnergyHub**, selecione **Base**.
* No **Inspector** do painel, clique em **Add Component** e adicione **ação e toque em vigor para com som**.
* Na **toque para local com o som e ação**:
  * Verifique **colocar pai com um toque de**.
  * Definir **som de posicionamento** à **lugar**.
  * Definir **som Pickup** à **Pickup**.
  * Pressione + na parte inferior direita em ambos **na ação de Pickup** e **na ação de posicionamento**. Arraste EnergyHub da cena para o **None (objeto)** campos.
    * Sob **na ação de Pickup**, clique em **nenhuma função** -> **EnergyHubBase** -> **ResetAnimation**.
    * Sob **na ação de posicionamento**, clique em **nenhuma função** -> **EnergyHubBase** -> **OnSelect**.

![Toque para local com o som e ação](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>Parte 2 - oclusão som

#### <a name="key-concepts"></a>Conceitos Principais

* Som, como a luz, pode ser obstruído.

Um exemplo clássico é uma sala de concertos. Quando um ouvinte está aguardando fora da empresa e a porta for fechada, os sons de música muffled. Também há normalmente uma redução no volume. Quando a porta é aberta, todo o espectro do som é ouvido no volume real. Sons de alta frequência geralmente são absorvidas mais de frequências baixa.

#### <a name="instructions"></a>Instruções

* No **hierarquia** do painel, expanda **HologramCollection** e selecione **P0LY**.
* No **Inspector** do painel, clique em **Add Component** e adicione **emissor de áudio**.

A classe de emissor de áudio fornece os seguintes recursos:

* Restaura todas as alterações para o volume do **AudioSource**.
* Executa um **Physics.RaycastNonAlloc** da posição do usuário na direção do **GameObject** à qual o **AudioEmitter** está anexado.

O método RaycastNonAlloc é usado como uma otimização de desempenho para limitar as alocações, bem como o número de resultados retornados.

* Para cada **IAudioInfluencer** encontrado, chamadas a **ApplyEffect** método.
* Para cada anterior **IAudioInfluencer** que é chamada de não encontrada, o **RemoveEffect** método.

Observe que AudioEmitter atualiza em escalas de tempo humano, em vez de em uma base por quadro. Isso é feito porque seres humanos geralmente não são movidos rápido o suficiente para o efeito para precisam ser atualizadas com mais frequência do que a cada trimestre ou meio segundo. Hologramas que ser transportado rapidamente de um local para outro pode quebrar a ilusão.

* No **hierarquia** do painel, expanda **HologramCollection**.
* Expandir **EnergyHub** e selecione **BlobOutside**.
* No **Inspector** do painel, clique em **Add Component** e adicione **Occluder áudio**.
* Na **Occluder áudio**, defina **frequência de corte** para **1500**.

Essa configuração limita as frequências de AudioSource para 1500 Hz e abaixo.

* Definir **passagem de Volume** à **0.9**.

Essa configuração reduz o volume do AudioSource a 90% de seu nível atual.

Áudio Occluder implementa IAudioInfluencer para:

* Aplicar um efeito de oclusão usando um **AudioLowPassFilter** que é anexado ao **AudioSource** gerenciado comprar os **AudioEmitter**.
* Aplica-se de atenuação de volume para o AudioSource.
* Desabilita o efeito, definindo uma frequência de corte neutra e desabilitar o filtro.

A frequência usada como neutra é 22 kHz (22000 Hz). Essa frequência foi escolhida estarem acima a nominal frequência máxima que pode ser ouvida pelo ouvido humano, este fazendo nenhum impacto perceptível para o som.

* No **hierarquia** painel, selecione **SpatialMapping**.
* No **Inspector** do painel, clique em **Add Component** e adicione **Occluder áudio**.
* Na **Occluder áudio**, defina **frequência de corte** para **750**.

Quando vários occluders estão no caminho entre o usuário e o **AudioEmitter**, a frequência mais baixa é aplicada ao filtro.

* Definir **passagem de Volume** à **0,75**.

Quando vários occluders estão no caminho entre o usuário e o **AudioEmitter**, a passagem do volume é aplicada de fogo.

* No **hierarquia** painel, selecione **gerenciadores**.
* No **Inspector** do painel, expanda **manipulador de entrada de fala**.
* Na **manipulador de entrada de fala**, expanda **vá encargo**.
* Alteração **nenhuma função** à **PolyActions.GoCharge**.

![palavra-chave: Acesse o encargo](images/gocharge.png)

* Expandir **vir aqui**.
* Alteração **nenhuma função** à **PolyActions.ComeBack**.

![palavra-chave: Vem cá](images/comehere.png)

#### <a name="build-and-deploy"></a>Criar e implantar

* Como antes, compile o projeto no Unity e implantar no Visual Studio.

Depois que o aplicativo é implantado:

* Digamos *"Cobrança de ir"* ter P0LY insira o Hub de energia.

Observe a alteração no som. Ele deve parecer um pouco mais discreta e muffled. Se você for capaz de se posicionando com uma parede ou outro objeto entre você e o Hub de energia, você deve observar um muffling adicional do som devido à oclusão pelo mundo real.

* Digamos *"Vir aqui"* ter P0LY deixe o Hub de energia e se posicionar na sua frente.

Observe que o som oclusão é removida depois P0LY sai no Hub de energia. Se você ainda estiver oclusão auditivas, P0LY pode ser obstruídos pelo mundo real. Tente mover para garantir que você tenha uma linha de visão clara para P0LY.

### <a name="part-3---room-models"></a>Parte 3 – modelos de espaço

#### <a name="key-concepts"></a>Conceitos Principais

* O tamanho do espaço fornece filas subliminar que contribuem para a localização de som.
* Modelos de espaço são definidos por-**AudioSource**.
* O [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece código para definir o modelo de espaço.
* Para experiências de realidade misturada, selecione o modelo de espaço que melhor se adapta o espaço de mundo real.

Se você estiver criando um cenário de realidade Virtual, selecione o modelo de espaço que melhor se adapta o ambiente virtual.

## <a name="chapter-4---sound-design"></a>Capítulo 4 - Design som

### <a name="objectives"></a>Objetivos

* Entenda as considerações sobre design eficaz de som.
* Aprenda técnicas de mixagem e diretrizes.

### <a name="part-1---sound-and-experience-design"></a>Parte 1 - experiência de Design e som

Esta seção discute o som de chave e diretrizes e considerações de design de experiência.

#### <a name="normalize-all-sounds"></a>Normalizar todos os sons

Isso evita a necessidade de código caso especial ajustar os níveis de volume por som, que pode ser demorado e limita a capacidade de atualizar facilmente os arquivos de som.

#### <a name="design-for-an-untethered-experience"></a>Design para uma experiência de ilimitado

HoloLens é um computador holográfico totalmente independente, de forma independente. Os usuários podem e usarão suas experiências durante a movimentação. Certifique-se de testar sua combinação de áudio por andar.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>Emitir um som de locais lógicos em seu hologramas

No mundo real, não de um cachorro latido de cauda e voz de um ser humano não vem de seus pés. Evite ter que os sons de emissão de inesperado partes do seu hologramas.

Hologramas pequenas, é razoável para ter o som emitir a partir do centro da geometria.

#### <a name="familiar-sounds-are-most-localizable"></a>Parece familiar é mais localizáveis

A voz humana e a música são muito fáceis de localizar. Se alguém liga para seu nome, será possível com bastante precisão determinar de qual direção veio a voz e de como distantes. Sons de curtos e desconhecidos são mais difíceis de localizar.

#### <a name="be-cognizant-of-user-expectations"></a>Estar ciente das expectativas do usuário

Experiência de vida desempenha um papel na nossa capacidade de identificar o local de um som. Esse é um motivo por que a voz humana é particularmente fácil de localizar. É importante estar ciente das expectativas de aprendido do seu usuário ao colocar sua sons.

Por exemplo, quando alguém ouve uma música bird geralmente pesquisados, como de pássaros tendem a ser acima da linha de visão (voadora ou em uma árvore). Não é incomum para um usuário ativar na direção correta de um som, mas procurar na direção vertical errada e ficar frustrados ou confusos quando não for possível encontrar o holograma.

#### <a name="avoid-hidden-emitters"></a>Evite os emissores ocultos

No mundo real, se você respondeu a um som, geralmente podemos pode identificar o objeto que está emitindo o som. Isso também deve considerar verdadeiro em suas experiências. Ele pode ser muito desconcertante para usuários de um som, saber por onde o som se origina e não conseguir ver a um objeto.

Há algumas exceções a essa diretriz. Por exemplo, os sons de ambientes como crickets em um campo não precisam estar visíveis. Experiência de vida nos dá a familiaridade com a origem desses sons sem a necessidade de vê-lo.

### <a name="part-2---sound-mixing"></a>Parte 2 - mixagem de som

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>Direcionar sua combinação para o volume de 70% sobre o HoloLens

Experiências de realidade misturadas permitem hologramas sejam vistas no mundo real. Eles também devem permitir que os sons do mundo real para ser ouvido. Um destino de 70% volume permite que o usuário ouça o mundo ao redor deles junto com o som de sua experiência.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>HoloLens no volume de 100% devem inundar out sons externos

Um nível de volume de 100% é semelhante de uma experiência de realidade Virtual. Visualmente, o usuário é transportado para um mundo diferente. O mesmo deve considerar verdadeiro poder ouvi-lo.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Usar o Unity AudioMixer para ajustar a categorias de sons

Ao projetar sua combinação, geralmente é útil criar categorias de som e ter a capacidade de aumentar ou diminuir o volume como uma unidade. Isso mantém os níveis relativos de cada som ao mesmo tempo, permitindo que as alterações rápidas e fácil a combinação geral. As categorias comuns incluem; efeitos sonoros, ambiente, os focos de voz e música em segundo plano.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>Sons de combinação com base em olhar do usuário

Ele geralmente pode ser úteis alterar a combinação de som em sua experiência com base em onde um usuário é (ou não) procurando. Um uso comum para essa técnica são para reduzir o nível de volume para hologramas que estão fora do quadro holográfica para tornar mais fácil para o usuário para se concentrar nas informações na frente delas. Outro uso é para aumentar o volume de um som para chamar a atenção do usuário para um evento importante.

#### <a name="building-your-mix"></a>Criando sua combinação

Ao criar sua combinação, é recomendável começar com o áudio de fundo da sua experiência e adicionar camadas com base na importância. Geralmente, isso resulta em cada camada que está sendo mais alto do que o anterior.

Imaginando sua combinação como um funil invertido, com menos importante (e geralmente quietest sons) na parte inferior, é recomendável para estruturar sua combinação semelhante para o diagrama a seguir.

![Estrutura de mistura de som](images/soundlevels.png)

Os focos de voz são um cenário interessante. Com base na experiência que você está criando, talvez seja conveniente ter um som (não localizado) estéreo ou spatialize focos sua voz. Dois a Microsoft publicou experiências ilustram excelentes exemplos de cada cenário.

[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa uma voz estéreo sobre. Quando o narrator está descrevendo o local que está sendo visualizado, o som é consistente e não variam de acordo com a posição do usuário. Isso permite que o Narrador descrever a cena sem tirar longe os sons spatialized do ambiente.

[Fragmentos](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utiliza uma voz spatialized sobre na forma de um detetive. Voz do detetive é usado para ajudar a trazer a atenção do usuário para uma dica importante, como se fosse de um real humanos na sala. Isso permite que um senso ainda maior de imersão na experiência de resolver o mistério.

### <a name="part-3--performance"></a>Parte 3 - desempenho

#### <a name="cpu-usage"></a>Uso da CPU

Ao usar o som espacial, emissores de 10 a 12 consumirá aproximadamente 12% da CPU.

#### <a name="stream-long-audio-files"></a>Arquivos de áudio longa Stream

Dados de áudio podem ser grandes, especialmente em taxas de amostragem comuns (48 e 44,1 kHz). Uma regra geral é que os arquivos de áudio com mais de 5 a 10 segundos devem ser transmitidos para reduzir o uso de memória do aplicativo.

No Unity, você pode marcar um arquivo de áudio para streaming nas configurações de importação do arquivo.

![Configurações de importação de áudio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>Capítulo 5 - efeitos especiais

### <a name="objectives"></a>Objetivos

* Adicione profundidade a "Mágica do Windows".
* Traga o usuário para o mundo virtual.

### <a name="magic-windows"></a>Windows mágico

#### <a name="key-concepts"></a>Conceitos Principais

* Criando modos de exibição para o mundo oculto, é visualmente atraente.
* Aprimore o realismo adicionando efeitos de áudio, quando um holograma ou o usuário está próximo do mundo oculto.

#### <a name="instructions"></a>Instruções

* No **hierarquia** do painel, expanda **HologramCollection** e selecione **mundo virtual**.
* Expandir **mundo virtual** e selecione **VoiceSource**.
* No **Inspector** do painel, clique em **Add Component** e adicione **efeito de voz do usuário**.

Uma **AudioSource** será adicionado ao componente **VoiceSource**.

* Na **AudioSource**, defina **saída** para **UserVoice (Mixer)**.
* Verifique as **Spatialize** caixa de seleção.
* Arraste o **Blend espacial** controle deslizante até **3D**, ou insira **1** na caixa de edição.
* Expandir **configurações de som 3D**.
* Definir **Doppler em razão nível** à **0**.
* Na **efeito de voz do usuário**, defina **objeto pai** para o **mundo virtual** da cena.
* Definir **distância máxima** à **1**.

Definindo **distância máxima** informa **efeito de voz do usuário** quão próximo o usuário deve ser feita no objeto pai antes do efeito está habilitado.

* Na **efeito de voz do usuário**, expanda **coro parâmetros**.
* Definir **profundidade** à **0,1**.
* Definir **toque em 1 Volume**, **toque Volume 2** e **toque Volume 3** para **0.8**.
* Definir **Volume do som Original** à **0,5**.

As configurações anteriores configuram os parâmetros do Unity **AudioChorusFilter** usado para adicionar a riqueza a voz do usuário.

* Na **efeito de voz do usuário**, expanda **parâmetros de eco**.
* Definir **atraso** para **300**
* Definir **Decay taxa** à **0,2**.
* Definir **Volume do som Original** à **0**.

As configurações anteriores configuram os parâmetros do Unity **AudioEchoFilter** usado para fazer com que a voz do usuário repetir.

O script de efeito de voz do usuário é responsável por:

* Medir a distância entre o usuário e o **GameObject** à qual o script está associado.
* Determinando se o usuário estiver voltada para o **GameObject**.

O usuário deve ser voltada para o GameObject, independentemente da distância, para o efeito a ser habilitado.

* Aplicar e definir um **AudioChorusFilter** e uma **AudioEchoFilter** para o **AudioSource**.
* Desabilitando o efeito ao desabilitar os filtros.

Efeito de voz do usuário usa o componente de Mic Stream seletor, do [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)para selecionar o fluxo de voz de alta qualidade e encaminhá-lo no sistema de áudio do Unity.

* No **hierarquia** painel, selecione **gerenciadores**.
* No **Inspector** do painel, expanda **manipulador de entrada de fala**.
* Na **manipulador de entrada de fala**, expanda **mundo virtual de mostrar**.
* Alteração **nenhuma função** à **UnderworldBase.OnEnable**.

![palavra-chave: Mostrar o mundo virtual](images/showunderworld.png)

* Expandir **ocultar mundo virtual**.
* Alteração **nenhuma função** à **UnderworldBase.OnDisable**.

![palavra-chave: Ocultar o mundo virtual](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>Criar e implantar

* Como antes, compile o projeto no Unity e implantar no Visual Studio.

Depois que o aplicativo é implantado:

* Enfrentam uma superfície (parede, floor, tabela) e dizer *"Mundo virtual mostrar"*.

O mundo virtual será mostrada e todos os outras hologramas ficará oculta. Se você não vir o mundo virtual, certifique-se de que você está enfrentando uma superfície do mundo real.

* Abordagem de dentro de 1 metro da holograma mundo virtual e comece a falar.

Agora há efeitos de áudio aplicados a sua opinião!

* Ativar para fora o mundo virtual e observe como o efeito não é mais aplicado.
* Digamos *"Mundo virtual ocultar"* para ocultar o mundo virtual.

O mundo virtual ficará oculta e as hologramas previamente ocultas reaparecerá.

## <a name="the-end"></a>Fim

Parabéns! Agora você concluiu **MR de 220 espacial: Som espacial**.

Ouça o mundo e dinamize suas experiências com som!
