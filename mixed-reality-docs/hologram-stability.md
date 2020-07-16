---
title: Estabilidade do holograma
description: O HoloLens estabiliza automaticamente os hologramas, mas há etapas que os desenvolvedores podem seguir para melhorar ainda mais a estabilidade do holograma.
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: hologramas, estabilidade, hololens
appliesto:
- HoloLens
ms.openlocfilehash: 4a489c923138808e3afb545097c314f354b5ad2a
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408204"
---
# <a name="hologram-stability"></a>Estabilidade do holograma

## <a name="overview"></a>Visão geral

Para atingir hologramas estáveis, o HoloLens tem um pipeline de estabilização de imagem interno. O pipeline de estabilização funciona automaticamente em segundo plano, portanto, você não precisa executar nenhuma etapa adicional para habilitá-lo. No entanto, você deve exercitar as técnicas que melhoram a estabilidade do holograma e evitar cenários que reduzam a estabilidade.

## <a name="hologram-quality-terminology"></a>Terminologia de qualidade do holograma

A qualidade dos hologramas é um resultado de um bom ambiente e um bom desenvolvimento de aplicativos. Aplicativos em execução em uma constante 60 de quadros por segundo em um ambiente em que o HoloLens pode rastrear os arredores garante que o holograma e o sistema de coordenadas correspondentes estejam em sincronia. Da perspectiva de um usuário, os hologramas que devem ser transportáveis não se moverão em relação ao ambiente.

A terminologia a seguir pode ajudá-lo quando você estiver identificando problemas com o ambiente, tarifas de renderização baixa ou inconsistentes ou qualquer outra coisa.
* **Correta.** Depois que o holograma é bloqueado mundialmente e colocado no mundo real, ele deve permanecer onde é colocado em relação ao ambiente ao redor e independente do movimento do usuário ou de alterações de ambiente pequenas e esparsas. Se um holograma mais tarde aparecer em um local inesperado, será um problema de *precisão* . Esses cenários podem ocorrer se duas salas distintas parecem idênticas.
* **Tremulação.** Os usuários observam a tremulação de alta frequência de um holograma, o que pode acontecer quando o controle do ambiente degrada. Para os usuários, a solução está executando o [ajuste de sensor](sensor-tuning.md).
* **Judder.** Baixas frequências de renderização resultam em animações desiguais e imagens duplas de hologramas. O judder é especialmente perceptível em hologramas com movimento. Os desenvolvedores precisam manter uma [constante 60 fps](hologram-stability.md#frame-rate).
* **Continente.** Os usuários veem a descompasso, uma vez que um holograma parece deixar de onde ele foi colocado originalmente. A descompasso acontece quando os hologramas são colocados longe das [âncoras espaciais](spatial-anchors.md), particularmente em partes do ambiente que não estão totalmente mapeadas. A criação de hologramas perto de âncoras espaciais reduz a probabilidade de descompasso.
* **Jumpize.** Quando um holograma "aparece" ou "salta" para fora de seu local ocasionalmente. A jumpização pode ocorrer conforme o controle ajusta os hologramas para que correspondam à compreensão atualizada do seu ambiente.
* **Nadam.** Quando um holograma aparenta ser o Sway correspondente ao movimento do cabeçalho do usuário. Nada acontece quando o aplicativo não implementou totalmente a [Reprojeção](hologram-stability.md#reprojection)e, se o HoloLens não for [calibrado](calibration.md) para o usuário atual. O usuário pode executar novamente o aplicativo de [calibragem](calibration.md) para corrigir o problema. Os desenvolvedores podem atualizar o plano de estabilização para melhorar ainda mais a estabilidade.
* **Separação de cores.** Os monitores no HoloLens são exibições sequenciais de cores, que canais de cores flash de vermelho-verde-azul-verde a 60 Hz (campos de cor individuais são mostrados às 240 Hz). Sempre que um usuário rastreia um holograma de movimento com seus olhos, as bordas à esquerda e à direita do holograma são separadas em suas cores constituintes, produzindo um efeito arco-íris. O grau de separação depende da velocidade do holograma. Em alguns casos raros, mover os cabeçotes rapidamente enquanto examina um holograma estacionário também pode resultar em um efeito de arco-íris, que é chamado de *[separação de cores](hologram-stability.md#color-separation)*.

## <a name="frame-rate"></a>Taxa de quadros

A taxa de quadros é o primeiro pilar da estabilidade do holograma. Para que os hologramas pareçam estáveis no mundo, cada imagem apresentada ao usuário deve ter os hologramas desenhados no local correto. O exibe na atualização do HoloLens 240 vezes por segundo, mostrando quatro campos coloridos separados para cada imagem recém processada, resultando em uma experiência do usuário de 60 FPS (quadros por segundo). Para fornecer a melhor experiência possível, os desenvolvedores de aplicativos devem manter 60 FPS, o que traduz para fornecer consistentemente uma nova imagem ao sistema operacional a cada 16 milissegundos.

**60 fps** Para desenhar hologramas para que pareçam estar sentado no mundo real, o HoloLens precisa renderizar imagens da posição do usuário. Como a renderização de imagem leva tempo, o HoloLens prevê onde o cabeçalho de um usuário será quando as imagens forem mostradas nas exibições. No entanto, esse algoritmo de previsão é uma aproximação. O HoloLens tem um hardware que ajusta a imagem renderizada para considerar a discrepância entre a posição da cabeça prevista e a posição real da cabeça. O ajuste faz a imagem que o usuário vê aparece como se fosse renderizado do local correto e os hologramas sentem-se estáveis. As atualizações de imagem funcionam melhor com pequenas alterações e não podem corrigir completamente certas coisas na imagem renderizada, como Motion-da Parallax.

Ao renderizar em 60 FPS, você está fazendo três coisas para ajudar a tornar os hologramas estáveis:
1. Minimizar a latência geral entre a renderização de uma imagem e a imagem que está sendo vista pelo usuário. Em um mecanismo com um jogo e um thread de renderização em execução no atrelada, a execução em 30FPS pode adicionar 33,3 ms de latência extra. A redução da latência diminui o erro de previsão e aumenta a estabilidade do holograma.
2. Fazendo isso, todas as imagens que atingem os olhos do usuário têm uma quantidade consistente de latência. Se você renderizar a 30 fps, a exibição ainda exibirá imagens em 60 FPS, o que significa que a mesma imagem será exibida duas vezes em uma linha. O segundo quadro terá 16,6-ms mais latência do que o primeiro quadro e terá que corrigir uma quantidade mais pronunciada de erro. Essa inconsistência na magnitude do erro pode causar judder de 60 Hz indesejadas.
3. Reduzir a aparência de trepidação, que é caracterizada pelo movimento irregular e por imagens duplas. Um movimento mais rápido do holograma e taxas de renderização mais baixas estão associados a uma trepidação mais acentuada. Empenhar-se em manter 60 FPS em todos os momentos ajudará a evitar judder para um determinado holograma de movimentação.

**Consistência de taxa de quadros** A consistência da taxa de quadros é tão importante quanto uma alta de quadros por segundo. Ocasionalmente, os quadros descartados são inevitáveis para qualquer aplicativo rico em conteúdo, e o HoloLens implementa alguns algoritmos sofisticados para se recuperar de falhas ocasionais. No entanto, uma taxa de quadros com flutuação constante é muito mais perceptível para um usuário do que executar consistentemente em taxas de quadros inferiores. Por exemplo, um aplicativo que é processado sem problemas para cinco quadros (60 FPS durante esses cinco quadros) e, em seguida, descarta todos os outros quadros para os 10 quadros seguintes (30 FPS para a duração desses 10 quadros) aparecerão mais instável do que um aplicativo que é processado consistentemente em 30 FPS.

Em uma observação relacionada, o sistema operacional limita os aplicativos a 30 FPS quando a [captura de realidade misturada](mixed-reality-capture.md) está em execução.

**Análise de desempenho** Há diferentes tipos de ferramentas que podem ser usadas para avaliar o benchmark da taxa de quadros do aplicativo, como:
* GPUView
* Depurador de Gráficos do Visual Studio
* Criadores de criação de perfil em mecanismos 3D, como o Unity

## <a name="hologram-render-distances"></a>Distâncias de renderização de holograma

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

O sistema visual humano integra vários sinais dependentes de distância quando fixates e se concentra em um objeto.
* [Acomodação](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) -o foco de um olho individual.
* [Convergência](https://en.wikipedia.org/wiki/Convergence_(eye)) -dois olhos se movendo para dentro ou para fora para o centro em um objeto.
* [Visão de binóculo](https://en.wikipedia.org/wiki/Stereopsis) – diparidades entre as imagens de olho esquerdo e direito que dependem da distância de um objeto do seu ponto de fixação da.
* Sombreamento, tamanho angular relativo e outros indícios de monocular (olho único).

A convergência e a acomodação são exclusivas porque suas indicações retinas adicionais relacionadas a como os olhos mudam para perceber os objetos em diferentes distâncias. Na visualização natural, a convergência e a acomodação são vinculadas. Quando os olhos exibem algo próximo (por exemplo, seu nariz), os olhos cruzam e acomodam a um ponto próximo. Quando os olhos visualizam algo no infinito, os olhos se tornam paralelos e os olhos se acomodam ao infinito. 

Os usuários com o HoloLens serão sempre acomodados a 2,0 m para manter uma imagem clara porque as exibições do HoloLens são fixas em uma distância óptica de aproximadamente 2,0 m para longe do usuário. Os desenvolvedores de aplicativos controlam onde os olhos dos usuários convergem colocando o conteúdo e os hologramas em várias profundidades. Quando os usuários acomodam e convergem para distâncias diferentes, o link natural entre as duas indicações é quebrado, o que pode levar ao Visual discomfort ou fadiga, especialmente quando a magnitude do conflito é grande. 

Discomfort do conflito Vergence pode ser evitado ou minimizado mantendo o conteúdo convergido o mais próximo de 2,0 m possível (ou seja, em uma cena com muito profundidade, coloque as áreas de interesse perto de 2,0 m, quando possível). Quando o conteúdo não pode ser colocado perto de 2,0 m, o discomfort do conflito de Vergence é maior quando o olhar do usuário é alternado entre distâncias diferentes. Em outras palavras, é muito mais confortável examinar um holograma estacionário que permaneça 50 cm fora do que examinar um holograma 50 cm que se move para fora e para longe de você ao longo do tempo.

Colocar o conteúdo em 2,0 m também é vantajoso, pois as duas telas são projetadas para se sobrepor totalmente nessa distância. Para imagens colocadas fora desse plano, à medida que eles se movem para fora do quadro Holographic, eles aparecerão de uma exibição, enquanto continuam sendo visíveis no outro. Este rival de binóculo pode causar interrupções na percepção de profundidade do holorgam.

**Distância ideal para colocação dos hologramas partindo do usuário**

![Distância ideal para colocação dos hologramas partindo do usuário](images/distanceguiderendering-750px.png)

**Planos de clipes** Para maior conforto, é recomendável recortar a distância de renderização em 85 cm com fade out do conteúdo começando em 1 m. Em aplicativos em que os hologramas e os usuários são estáticos, os hologramas podem ser vistos confortavelmente como se aproximando 50 cm. Nesses casos, os aplicativos devem posicionar um plano de clipes que não sejam mais de 30 cm e desaparecer devem iniciar pelo menos 10 cm fora do plano. Sempre que o conteúdo estiver mais próximo do que 85 cm, é importante garantir que os usuários não se aproximem mais de perto ou longe de hologramas ou que os hologramas não se movam com frequência mais perto ou longe do usuário, pois essas situações têm mais probabilidade de causar discomfort do conflito de Vergence. O conteúdo deve ser criado para minimizar a necessidade de interação com mais de 85 cm do usuário, mas quando o conteúdo deve ser processado mais de 85 cm, uma boa regra prática para os desenvolvedores é criar cenários em que os usuários e/ou os hologramas não se movam em profundidade mais de 25% do tempo.

**Práticas recomendadas** Quando os hologramas não podem ser colocados em 2 m e os conflitos entre a convergência e a acomodação não podem ser evitados, a zona ideal para o posicionamento do holograma é entre 1,25 m e 5 m. Em todos os casos, os designers devem estruturar o conteúdo para incentivar os usuários a interagir de 1 + m fora (por exemplo, ajustar o tamanho do conteúdo e os parâmetros de posicionamento padrão).

## <a name="reprojection"></a>Reprojeção
O HoloLens executa uma técnica de estabilização de Holographic assistida por hardware sofisticada conhecida como Reprojeção. A Reprojeção leva em conta o movimento e a alteração do ponto de vista (CameraPose) à medida que a cena anima e o usuário move a cabeça.  Os aplicativos precisam tomar ações específicas para melhor utilização da Reprojeção.


Há quatro tipos principais de Reprojeção
* **Reprojeção de profundidade:**  Produz os melhores resultados com a menor quantidade de esforço do aplicativo.  Todas as partes da cena renderizada são estabilizadas independentemente com base em sua distância do usuário.  Alguns artefatos de renderização podem estar visíveis onde há alterações nítidas em profundidade.  Essa opção só está disponível em headsets 2 e de imersão.
* **Reprojeção do planar:**  Permite o controle preciso do aplicativo sobre estabilização.  Um plano é definido pelo aplicativo e tudo nesse plano será a parte mais estável da cena.  Quanto mais um holograma estiver longe do plano, menos estável será.  Essa opção está disponível em todas as plataformas do Windows MR.
* **Reprojeção automática de planar:**  O sistema define um plano de estabilização usando informações no buffer de profundidade.  Essa opção está disponível no HoloLens geração 1 e no HoloLens 2.
* **Nenhum:** Se o aplicativo não faz nada, a Reprojeção do planar é usada com o plano de estabilização fixo em 2 metros na direção do olhar da cabeça do usuário, normalmente produzindo resultados de subpadrão.

Os aplicativos precisam executar ações específicas para habilitar os diferentes tipos de Reprojeção
* **Reprojeção de profundidade:** O aplicativo envia seu buffer de profundidade ao sistema para cada quadro renderizado.  No Unity, a Reprojeção de profundidade é feita com a opção de **buffer de profundidade compartilhada** no painel de **configurações de realidade mista do Windows** em **XR plugin Management**.  Aplicativos DirectX chamam CommitDirect3D11DepthBuffer.  O aplicativo não deve chamar SetFocusPoint.
* **Reprojeção do planar:** Em todos os quadros, os aplicativos informam ao sistema o local de um plano a ser estabilizado.  Os aplicativos do Unity chamam SetFocusPointForFrame e devem ter o **buffer de profundidade compartilhado** desabilitado.  Os aplicativos DirectX chamam SetFocusPoint e não devem chamar CommitDirect3D11DepthBuffer.
* **Reprojeção automática de planar:** Para habilitar o, o aplicativo precisa enviar seu buffer de profundidade ao sistema como faria para a Reprojeção de profundidade.  No HoloLens 2, o aplicativo precisa SetFocusPoint com um ponto de 0, 0 para cada quadro.  Para o HoloLens geração 1, o aplicativo não deve chamar SetFocusPoint.

### <a name="choosing-reprojection-technique"></a>Escolhendo a técnica de Reprojeção

Tipo de estabilização |    Headsets de imersão |    Geração de HoloLens 1 | HoloLens 2
--- | --- | --- | ---
Reprojeção de profundidade |    Recomendadas |   N/D |   Recomendadas<br/><br/>Os aplicativos do Unity devem usar o Unity 2018.4.12 ou posterior ou o Unity 2019,3 ou posterior. Caso contrário, use a Reprojeção automática de planar.
Reprojeção automática de planar | N/D |   Padrão recomendado |   Recomendado se a Reprojeção de profundidade não fornecer os melhores resultados<br/><br/>Os aplicativos do Unity são recomendados para usar o Unity 2018.4.12 ou posterior ou o Unity 2019,3 ou posterior.  As versões anteriores do Unity funcionarão com resultados de Reprojeção ligeiramente degradados.
Reprojeção do planar |   Não recomendado |   Recomendado se o planar automático não fornecer os melhores resultados | Use se nenhuma das opções de profundidade fornecer os resultados desejados    

### <a name="verifying-depth-is-set-correctly"></a>A verificação de profundidade está definida corretamente
            
Quando um método de Reprojeção usa o buffer de profundidade, é importante verificar se o conteúdo do buffer de profundidade representa a cena renderizada do aplicativo.  Vários fatores podem causar problemas. Se houver uma segunda câmera usada para renderizar sobreposições de interface do usuário, por exemplo, é provável que seja possível substituir todas as informações de profundidade da exibição real.  Objetos transparentes geralmente não definem profundidade.  Uma renderização de texto não definirá profundidade por padrão.  Haverá problemas visíveis na renderização quando a profundidade não corresponder aos hologramas renderizados.
            
O HoloLens 2 tem um visualizador para mostrar onde a profundidade está e não está sendo definida, que pode ser habilitada no portal do dispositivo.  Na guia estabilidade do holograma das **exibições**  >  **Hologram Stability** , marque a caixa de seleção **Exibir visualização de profundidade no headset** .  As áreas que têm profundidade definida corretamente serão azuis.  Itens renderizados que não têm profundidade definida são marcados em vermelho e precisam ser corrigidos.  

> [!NOTE]
> A visualização da profundidade não aparecerá na captura de realidade misturada.  Ele só é visível por meio do dispositivo.
            
Algumas ferramentas de exibição de GPU permitirão a visualização do buffer de profundidade.  Os desenvolvedores de aplicativos podem usar essas ferramentas para garantir que a profundidade esteja sendo definida corretamente.  Consulte a documentação para obter as ferramentas do aplicativo.

### <a name="using-planar-reprojection"></a>Usando a Reprojeção do planar
> [!NOTE]
> Para headsets de imersão de área de trabalho, a definição de um plano de estabilização geralmente é produtiva, pois oferece menos qualidade visual do que fornecer o buffer de profundidade do seu aplicativo ao sistema para habilitar a Reprojeção baseada em profundidade por pixel. A menos que seja executado em um HoloLens, geralmente você deve evitar definir o plano de estabilização.

![Plano de estabilização para objetos 3D](images/stab-plane-500px.jpg)

O dispositivo tentará escolher este plano automaticamente, mas o aplicativo deve ajudar selecionando o ponto de foco na cena. Os aplicativos do Unity em execução em um HoloLens devem escolher o melhor ponto de foco com base em sua cena e passá-lo para [SetFocusPoint ()](focus-point-in-unity.md). Um exemplo de configuração do ponto de foco no DirectX está incluído no modelo de cubo padrão de rotação.

O Unity enviará seu buffer de profundidade ao Windows para habilitar a Reprojeção por pixel quando você executar seu aplicativo em um headset de imersão conectado a um PC desktop, que fornece uma qualidade de imagem ainda melhor sem trabalho explícito pelo aplicativo. Você só deve fornecer um ponto de foco quando seu aplicativo estiver em execução em um HoloLens ou a Reprojeção por pixel será substituída.


```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

O posicionamento do ponto de foco em grande parte depende do que o holograma está olhando. O aplicativo tem o vetor olhar para referência e o designer de aplicativo sabe qual conteúdo ele deseja que o usuário observe.

A única coisa mais importante que um desenvolvedor pode fazer para estabilizar os hologramas é renderizar em 60 FPS. Soltar abaixo de 60 FPS reduzirá drasticamente a estabilidade do holograma, seja qual for a otimização do plano de estabilização.

**Práticas recomendadas** Não há uma maneira universal de configurar o plano de estabilização e ele é específico do aplicativo. Nossa principal recomendação é experimentar e ver o que funciona melhor para seu cenário. No entanto, tente alinhar o plano de estabilização com o máximo de conteúdo possível, pois todo o conteúdo desse plano é perfeitamente estabilizado.

Por exemplo:
* Se você tiver apenas conteúdo planar (leitura de aplicativo, aplicativo de reprodução de vídeo), alinhe o plano de estabilização com o plano que tem seu conteúdo.
* Se houver três pequenas que estão bloqueadas pelo mundo, torne o plano de estabilização "recortar", embora os centros de todas as suas interações que estão atualmente na exibição do usuário.
* Se sua cena tiver conteúdo em profundidades consideravelmente diferentes, favoreça mais objetos.
* Certifique-se de ajustar o ponto de estabilização a cada quadro para coincidir com o holograma que o usuário está olhando

**Itens a serem evitados** O plano de estabilização é uma excelente ferramenta para atingir hologramas estáveis, mas se for usado incorretamente, isso poderá resultar em instabilidade de imagem grave.
* Não "dispare e esqueça". Você pode terminar com o plano de estabilização por trás do usuário ou anexado a um objeto que não está mais no modo de exibição do usuário. Verifique se o plano de estabilização normal está definido para frente de câmera oposta (por exemplo,-Camera. Forward)
* Não altere rapidamente o plano de estabilização entre extrema e frente
* Não deixe o plano de estabilização definido para uma distância/orientação fixa
* Não deixe o plano de estabilização ser cortado pelo usuário
* Não defina o ponto de foco ao executar em um computador desktop em vez de um HoloLens e, em vez disso, confie na Reprojeção baseada em profundidade por pixel.

## <a name="color-separation"></a>Separação de cores 

Devido à natureza de exibições do HoloLens, um artefato chamado "separação de cores" pode, às vezes, ser percebido. Ele se manifesta como a imagem que separa em cores de base individuais – vermelho, verde e azul. O artefato pode ser especialmente visível ao exibir objetos brancos, pois eles têm grandes quantidades de vermelho, verde e azul. É mais pronunciado quando um usuário rastreia visualmente um holograma que está se movendo pelo quadro Holographic em alta velocidade. Outra maneira de o artefato ser manifestar é a distorção/desformação de objetos. Se um objeto tiver cores de alto contraste e/ou puras, como vermelho, verde, azul, a separação de cores será percebida como deformação de partes diferentes do objeto.

**Um exemplo de qual é a separação de cores de um cursor redondo branco de cabeçalho e arredondado como um usuário gira sua cabeça para o lado:**

![Um exemplo de qual é a separação de cores de um cursor redondo branco de cabeçalho de cabeça como um usuário gira sua cabeça para o lado.](images/colorseparationofroundwhitecursor-300px.png)

Embora seja difícil evitar completamente a separação de cores, há várias técnicas disponíveis para atenuá-las.

**A separação de cores pode ser vista em:**
* Objetos que estão se movendo rapidamente, incluindo objetos bloqueados por cabeçalho, como o [cursor](cursors.md).
* Objetos que estão significativamente longe do [plano de estabilização](hologram-stability.md#reprojection).

**Para atenuar os efeitos da separação de cores:**
* Faça o objeto atrasar o olhar do usuário. Ele deve aparecer como se tiver algum inércia e estiver anexado ao olhar "em molas". Essa abordagem reduz o cursor (reduzindo a distância de separação) e a coloca atrás do ponto de olhar provável do usuário. Desde que ele se ajuste rapidamente quando o usuário parar de mudar seu olhar, ele se sentirá natural.
* Se você quiser mover um holograma, tente manter sua velocidade de movimentação abaixo de 5 graus/segundo se você espera que o usuário o acompanhe com seus olhos.
* Use *Light* em vez de *Geometry* para o cursor. Uma fonte de iluminação virtual anexada ao olhar será percebida como um ponteiro interativo, mas não causará a separação de cores.
* Ajuste o plano de estabilização para corresponder aos hologramas em que o usuário está nuvens.
* Tornar o objeto vermelho, verde ou azul.
* Mudar para uma versão desfocada do conteúdo. Por exemplo, um cursor branco redondo pode ser alterado para uma linha levemente desfocada na direção do movimento.

Como antes, a renderização em 60 FPS e a definição do plano de estabilização são as técnicas mais importantes para a estabilidade do holograma. Se for voltada para separação de cores perceptível, primeiro verifique se a taxa de quadros atende às expectativas.

## <a name="see-also"></a>Confira também
* [Entendendo o desempenho da realidade misturada](understanding-performance-for-mixed-reality.md)
* [Cor, luz e materiais](color,-light-and-materials.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Estabilização do holograma MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html)
