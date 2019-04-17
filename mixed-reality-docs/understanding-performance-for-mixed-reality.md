---
title: Noções básicas sobre desempenho para realidade misturada
description: Advanced tópicos e detalhes sobre como otimizar o desempenho para aplicativos de realidade mista do Windows
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows misturadas realidade, a realidade misturada, realidade Virtual, VR, MR, desempenho, otimização, CPU, GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590611"
---
# <a name="understanding-performance-for-mixed-reality"></a>Noções básicas sobre desempenho para realidade misturada

Este artigo é uma introdução ao racionalizar a importância do desempenho de seu aplicativo de realidade misturada.  Experiência do usuário pode ser degradada bastante, se seu aplicativo não é executado em taxa de quadros ideal. Hologramas aparecerá instáveis e controle de cabeçalho do ambiente será impreciso, levando a uma experiência ruim para o usuário. Na verdade, o desempenho deve ser considerado como um recurso de primeira classe para desenvolvimento de realidade mista e não um estabilização, no final do ciclo de tarefa.

Para revisão, os valores da taxa de quadros de alto desempenho para cada plataforma de destino estão listados abaixo.

| Plataforma | Taxa de quadros de destino |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality Ultra PCs](immersive-headset-hardware-details.md) | 90 FPS |
| [Misturadas realidade PCs do Windows](immersive-headset-hardware-details.md) | 60 FPS |

A estrutura a seguir fornece uma visão geral para as práticas recomendadas e entendimentos para atingir as taxas de quadro de destino. Para se aprofundar ainda mais detalhes, considere a leitura do [recomendações de desempenho para o artigo do Unity](performance-recommendations-for-unity.md). Em particular, este artigo relacionado discutirá como medir a taxa de quadros no seu aplicativo do Unity Windows Mixed Reality, bem como as etapas necessárias no ambiente do Unity para melhorar o desempenho.

## <a name="understanding-performance-bottlenecks"></a>Noções básicas sobre os gargalos de desempenho

Se seu aplicativo tem uma taxa de quadros com baixo desempenho, a primeira etapa é analisar e compreender onde seu aplicativo é computacionalmente intensivo. Há dois processadores principais responsável pelo trabalho de renderização de cena: a CPU e GPU. Cada um desses dois componentes lidar com operações diferentes e os estágios de seu aplicativo de realidade misturada. Há três principais locais onde os afunilamentos podem ocorrer. 

1. **Thread do aplicativo - CPU** -esse thread é responsável pela lógica do seu aplicativo. Isso inclui a entrada, animações, física e lógica/estado do outro aplicativo de processamento
2. **Renderizar Thread - CPU para GPU** -esse thread é responsável por enviar suas chamadas de desenho para a GPU. Quando seu aplicativo deseja renderizar um objeto como um cubo ou modelo, esse thread envia uma solicitação para a GPU, que tem uma arquitetura otimizada para processamento, para executar essas operações.
3. **GPU** - 
    esse processador mais comumente lida com o pipeline de gráficos do seu aplicativo para transformar dados 3D (modelos, as texturas, etc.) em pixels e, por fim, produzir uma imagem 2D para enviar a tela do dispositivo.

![Tempo de vida de um quadro](images/lifetime-of-a-frame.png)

Em geral, aplicativos HoloLens será limitado de GPU. No entanto, isso pode ocorrer em todos os aplicativos e, portanto, é recomendável usar as ferramentas e técnicas abaixo para obter a verdade para seu aplicativo.

## <a name="how-to-analyze-your-application"></a>Como analisar seu aplicativo

Há muitas ferramentas que permitem a você como desenvolvedor, entender o perfil de desempenho do seu aplicativo de realidade misturada. Eles permitem que você para os dois destino onde você tem os gargalos e como eles são manifesting si mesmos para depurá-los.

Esta é uma lista de ferramentas populares e poderosas para obter informações de criação de perfil profundas para o seu aplicativo.
- [Analisadores de desempenho de gráficos do Intel](https://software.intel.com/gpa)
- [Depuradores de elementos gráficos do Visual Studio](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Depurador do Unity quadro](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Como criar um perfil em qualquer ambiente

Há um teste simples para determinar rapidamente que se há probabilidade de GPU limitado ou CPU limitados em seu aplicativo. Se você diminuir a resolução de saída de destino de renderização, há menos pixels para calcular e assim, menos trabalho GPU precisa executar para processar uma imagem. Visor dimensionamento (dimensionamento dinâmica resolução) é a prática de renderização de sua imagem para uma menor destino de renderização, em seguida, seu dispositivo de saída pode ser exibido. O dispositivo será up-exemplo de um conjunto menor de pixels para exibir sua imagem final.

Após diminuir a resolução de renderização, se:
1) Taxa de quadros do aplicativo **aumenta**, em seguida, você provavelmente **limitado de GPU**
1) Taxa de quadros do aplicativo **inalterado**, em seguida, você provavelmente **CPU limitada**

>[!NOTE]
>Unity fornece a capacidade de modificar facilmente a resolução de destino de renderização do seu aplicativo em tempo de execução por meio de *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* propriedade. A imagem final exibida no dispositivo tem uma resolução fixa. A plataforma será a resolução mais baixa para criar uma imagem de resolução mais alta para a renderização em telas de saída de exemplo. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Como melhorar o seu aplicativo

### <a name="cpu-performance-recommendations"></a>Recomendações de desempenho de CPU

Em geral, a maior parte do trabalho em um aplicativo de realidade misturada na CPU envolve executar "simulação" da cena e processar lógica extensiva de aplicativos exclusivos. Portanto, as seguintes áreas são geralmente destinadas para otimização.

- Animações
- Simplificar a física
- Alocações de memória
- Algoritmos complexos (isto é cinemática inversa, a localização de caminho)

### <a name="gpu-performance-recommendations"></a>Recomendações de desempenho de GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Noções básicas sobre taxa de preenchimento de vs de largura de banda
Durante a renderização de um quadro na GPU, um aplicativo é geralmente limitado pela taxa de preenchimento ou largura de banda de memória.

- **Largura de banda de memória** é a taxa de leituras e gravações a GPU pode executar da memória
    - Para identificar as limitações de largura de banda, reduzir a qualidade da textura e verifique se a taxa de quadros aprimorado.
    - No Unity, isso pode ser feito alterando **qualidade da textura** na **editar** > **configurações do projeto**  >   **[ Configurações de qualidade](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.
- **Taxa de preenchimento** refere-se a taxa de transferência de pixels renderizados e podem ser desenhados por segundo pela GPU.
    - Para identificar os limites de taxa de preenchimento, diminuir a resolução de vídeo e verifique se a taxa de quadros aprimorado. 
    - No Unity, isso pode ser feito por meio de *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* propriedade

Largura de banda de memória geralmente envolve as otimizações para qualquer uma
1) diminuir as resoluções de textura
2) Utilize menos texturas (isto é especular, etc. Normals)

Taxa de preenchimento principalmente está empenhada em reduzir o número de operações que precisam ser calculado para o final de um pixel renderizado. Exemplos disso geralmente se encaixam em reduzindo
1) número de objetos para renderização/processo
2) número de operações por sombreador
3) número de estágios GPU para o resultado final (sombreadores de geometria, pós-processamento efeitos, etc)
4) número de pixels para renderizar (isto é resolução de vídeo)

#### <a name="reduce-poly-count"></a>Reduzir a contagem de poly
Polígono superior conta resultam em mais operações para a GPU e reduzindo o número de polígonos na sua cena reduzirá a quantidade de tempo para renderizar esse geometria. Há outros fatores envolvidos, bem como em sombreamento de geometria que pode ser cara, mas a contagem de polígono é a métrica de base para determinar o quão caro será para renderizar a uma cena.

#### <a name="limit-overdraw"></a>Limite de excedente

Alto excedente ocorre quando vários objetos são renderizados, mas não são produzidos para a tela conforme eles ficam ocultos por occluding, geralmente mais perto de outro objeto. Imagine-se de examinar uma parede tinha várias salas e geometria por trás dele. Todos da geometria seriam processados para renderização, mas apenas a parede opaca realmente precisa ser renderizado como ele occludes o modo de exibição de todos os outros tipos de conteúdo. Isso resulta em um desperdício operações que não são necessários para a exibição atual.

#### <a name="shaders"></a>Sombreadores

Sombreadores são programas do small executados na GPU e geralmente determinam duas etapas importantes em processamento:
1) os vértices do objeto que devem ser desenhados na tela e onde eles estão no espaço de tela (ou seja o sombreador de vértices)
    - O sombreador de vértices geralmente é executado por vértice para cada GameObject
2) o que esses pixels (ou seja, de cores o sombreador de Pixel)
    - O sombreador de Pixel é executado por pixel para a textura que está sendo renderizada para o dispositivo presente

Normalmente, sombreadores executam muitos cálculos de iluminação e transformações. Embora modelos complexos de iluminação, sombras e outras operações podem gerar resultados fantásticos, eles também são fornecidos com um preço. Reduzir o número de operações computadas em sombreadores pode reduzir significativamente o trabalho geral preciso ser feito por uma GPU por quadro.

##### <a name="shader-coding-recommendations"></a>Recomendações de codificação de sombreador

- Use a filtragem bilinear sempre que possível
- Reorganizar expressões para usar intrínsecos MAD para fazer uma multiplicação e uma adição ao mesmo tempo
- Pré-calcular tanto quanto possível na CPU e passar como constantes para o material
- **Favorecer operações de movimentação de sombreador de pixel para o sombreador de vértice**
    - Geralmente, o número de vértices << n º de pixels (ou seja, 720p = = 921.600 pixels, 1080p = = 2,073,600 pixels, etc)

#### <a name="remove-gpu-stages"></a>Remover os estágios GPU
Pós-processamento efeitos pode ser muito caro e geralmente inibir a taxa de preenchimento do seu aplicativo. Isso também inclui a suavização técnicas como MSAA. Em HoloLens, é recomendável para evitar essas técnicas inteiramente. Além disso, os estágios de sombreador adicionais, como a geometria, convexa e sombreadores de cálculo devem ser evitados sempre que possível.

## <a name="memory-recommendations"></a>Recomendações de memória
Operações de alocação e desalocação de memória excessiva podem ter efeitos adversos no seu aplicativo holográfico, resultando em desempenho inconsistente, quadros congelados e outro comportamento prejudicial. É especialmente importante entender as considerações de memória durante o desenvolvimento no Unity, uma vez que o gerenciamento de memória é controlado pelo coletor de lixo.

#### <a name="object-pooling"></a>Ao pool de objetos

Pool de objetos é uma técnica popular para reduzir o custo de contínuas alocações e Desalocações de objetos. Isso é feito por alocar um grande pool de objetos idênticos e reutilização de instâncias inativas, disponíveis desse pool em vez de constantemente gerando e destruição de objetos ao longo do tempo. Pools de objeto são ótimos para componentes novamente utilizáveis que têm vida útil da variável durante a um aplicativo.

## <a name="see-also"></a>Consulte também
- [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
- [Configurações recomendadas para Unity](recommended-settings-for-unity.md)
