---
title: Entendendo o desempenho da realidade misturada
description: Tópicos avançados e detalhes sobre como otimizar o desempenho para aplicativos do Windows Mixed Reality
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, desempenho, otimização, CPU, GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548837"
---
# <a name="understanding-performance-for-mixed-reality"></a>Entendendo o desempenho da realidade misturada

Este artigo é uma introdução à racionalização do significado do desempenho para seu aplicativo de realidade misturada.  A experiência do usuário pode ser bastante degradada se seu aplicativo não for executado em uma taxa de quadros ideal. Os hologramas aparecerão instáveis e o controle de carga do ambiente não será preciso, levando a uma experiência ruim para o usuário. Na verdade, o desempenho deve ser considerado como um recurso de primeira classe para o desenvolvimento de realidade misturada e não uma tarefa de fim de ciclo.

Para revisão, os valores de taxa de quadros de alto desempenho para cada plataforma de destino são listados abaixo.

| Plataforma | Taxa de quadros de destino |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality ultra PCs](immersive-headset-hardware-details.md) | 90 FPS |
| [Computadores Windows Mixed Reality](immersive-headset-hardware-details.md) | 60 FPS |

A estrutura a seguir fornece uma estrutura geral para práticas recomendadas e entendimentos para atingir as taxas de quadros de destino. Para aprofundar-se nos detalhes, considere ler o [artigo recomendações de desempenho para o Unity](performance-recommendations-for-unity.md). Em particular, este artigo relacionado discutirá como medir a taxa de quadros em seu aplicativo do Unity Windows Mixed Reality, bem como as etapas a serem executadas no ambiente do Unity para melhorar o desempenho.

## <a name="understanding-performance-bottlenecks"></a>Noções básicas sobre afunilamentos de desempenho

Se seu aplicativo tiver uma taxa de quadros com desempenho alto, a primeira etapa será analisar e entender onde o aplicativo é computacionalmente intensivo. Há dois processadores principais responsáveis pelo trabalho de renderizar sua cena: a CPU e a GPU. Cada um desses dois componentes lida com operações e estágios diferentes de seu aplicativo de realidade misturada. Há três locais principais onde os afunilamentos podem ocorrer. 

1. **Thread de aplicativo-CPU** -esse thread é responsável pela lógica do aplicativo. Isso inclui o processamento de entrada, animações, física e outra lógica/estado do aplicativo
2. **Renderizar thread-CPU para GPU** -esse thread é responsável por enviar suas chamadas de desenho para a GPU. Quando seu aplicativo deseja renderizar um objeto, como um cubo ou modelo, esse thread envia uma solicitação para a GPU, que tem uma arquitetura otimizada para renderização, para executar essas operações.
3. **GPU** - 
    Esse processador geralmente manipula a pipeline gráfica de seu aplicativo para transformar dados 3D (modelos, texturas, etc.) em pixels e, por fim, produzir uma imagem 2D para enviar à tela do dispositivo.

![Tempo de vida de um quadro](images/lifetime-of-a-frame.png)

Em geral, os aplicativos do HoloLens serão ligados à GPU. No entanto, isso não é verdadeiro em todos os aplicativos e, portanto, é recomendável usar as ferramentas & técnicas abaixo para chegar à verdade para o seu aplicativo em particular.

## <a name="how-to-analyze-your-application"></a>Como analisar seu aplicativo

Há muitas ferramentas que permitem que você como desenvolvedor entenda o perfil de desempenho do seu aplicativo de realidade misturada. Eles permitirão que você faça o destino onde você tem gargalos e como eles se manifestam para depurá-los.

Esta é uma lista de ferramentas populares e poderosas para obter informações aprofundadas de criação de perfil para seu aplicativo.
- [Analisadores de desempenho de gráficos Intel](https://software.intel.com/gpa)
- [Depuradores de gráficos do Visual Studio](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Criador de perfil do Unity](https://docs.unity3d.com/Manual/Profiler.html)
- [Depurador de quadros do Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Como criar um perfil em qualquer ambiente

Há um teste simples para determinar rapidamente se você provavelmente está ligado à GPU ou à CPU limitada em seu aplicativo. Se você diminuir a resolução da saída de destino de renderização, haverá menos pixels para calcular e, portanto, menos trabalho que a GPU precisa executar para renderizar uma imagem. O dimensionamento de visor (dimensionamento de resolução dinâmica) é a prática de renderizar a imagem para um destino de renderização menor, e o dispositivo de saída pode ser exibido. O dispositivo terá um exemplo de um conjunto menor de pixels para exibir a imagem final.

Depois de diminuir a resolução de renderização, se:
1) **Aumento**da taxa de quadros do aplicativo; provavelmente, você está **vinculado à GPU**
1) Taxa de quadros do aplicativo inalterada, provavelmente você está **limitado à CPU**

>[!NOTE]
>O Unity fornece a capacidade de modificar facilmente a resolução de destino de renderização de seu aplicativo em tempo de execução por meio da propriedade *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* . A imagem final apresentada no dispositivo tem uma resolução fixa. A plataforma obterá uma amostra da saída de resolução mais baixa para criar uma imagem de resolução mais alta para renderização em exibições. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Como melhorar seu aplicativo

### <a name="cpu-performance-recommendations"></a>Recomendações de desempenho da CPU

Em geral, a maior parte do trabalho em um aplicativo de realidade misturada na CPU envolve a execução da "simulação" da cena e o processamento de uma lógica de aplicativo extensivamente exclusiva. Portanto, as áreas a seguir geralmente são destinadas à otimização.

- Animations
- Simplificar a física
- Alocações de memória
- Algoritmos complexos (ou seja, cinemática inversa, localização de caminho)

### <a name="gpu-performance-recommendations"></a>Recomendações de desempenho de GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Noções básicas sobre largura de banda vs. taxa de preenchimento
Ao renderizar um quadro na GPU, um aplicativo geralmente é limitado pela largura de banda da memória ou pela taxa de preenchimento.

- **Largura de banda de memória** é a taxa de leituras e gravações que a GPU pode executar da memória
    - Para identificar limitações de largura de banda, reduza a qualidade da textura e verifique se a taxa de quadros melhorou
    - No Unity, isso pode ser feito alterando **a qualidade da textura** em **Editar** > **configurações** > do projeto configurações de **[qualidade](https://docs.unity3d.com/Manual/class-QualitySettings.html)** .
- A **taxa de preenchimento** refere-se à taxa de transferência de pixels renderizados que podem ser desenhados por segundo pela GPU.
    - Para identificar as limitações da taxa de preenchimento, diminua a resolução de vídeo e verifique se a taxa de quadros foi aprimorada. 
    - No Unity, isso pode ser feito por meio da propriedade *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*

A largura de banda de memória geralmente envolve otimizações para
1) diminuir as resoluções de textura
2) utilizar menos texturas (ou seja, Normals, especular etc.)

A taxa de preenchimento se concentra principalmente na redução do número de operações que precisam ser computadas para um pixel renderizado final. Exemplos disso normalmente se enquadram na redução
1) número de objetos a serem renderizados/processados
2) número de operações por sombreador
3) número de estágios de GPU para o resultado final (sombreadores de geometria, efeitos de pós-processamento, etc)
4) número de pixels a serem renderizados (ou seja, resolução de vídeo)

#### <a name="reduce-poly-count"></a>Reduzir número de polylines
Contagens de polígono mais altas resultam em mais operações para a GPU e a redução do número de polígonos em sua cena reduzirá a quantidade de tempo para renderizar essa geometria. Também há outros fatores envolvidos no sombreamento da geometria que ainda pode ser cara, mas a contagem de polígonos é a métrica base para determinar o quão caro será a renderização de uma cena.

#### <a name="limit-overdraw"></a>Limite de extração

O alto sobreempate ocorre quando vários objetos são processados, mas não são enviados para a tela, pois eles ficam ocultos por outro objeto occluding, geralmente mais próximo,. Imagine examinar uma parede que tinha várias salas e geometria por trás dela. Toda a geometria seria processada para renderização, mas apenas a parede opaca realmente precisa ser renderizada, pois ela occludes a exibição de todo o outro conteúdo. Isso resulta em desperdício de operações que não são necessárias para a exibição atual.

#### <a name="shaders"></a>Sombreadores

Os sombreadores são programas pequenos que são executados na GPU e geralmente determinam duas etapas importantes na renderização:
1) quais vértices do objeto devem ser desenhados na tela e onde estão no espaço da tela (ou seja, o sombreador de vértice)
    - O sombreador de vértice geralmente é executado por vértice para cada gameobject
2) o que colorir esses pixels (ou seja, o sombreador de pixel)
    - O sombreador de pixel é executado por pixel para a textura que está sendo renderizada para o dispositivo presente

Normalmente, os sombreadores executam muitas transformações e cálculos de iluminação. Embora modelos de iluminação complexos, sombras e outras operações possam gerar resultados fantásticos, eles também têm um preço. Reduzir o número de operações computadas em sombreadores pode reduzir muito o trabalho geral necessário para ser feito por uma GPU por quadro.

##### <a name="shader-coding-recommendations"></a>Recomendações de codificação de sombreador

- Use a filtragem biline sempre que possível
- Reorganize as expressões para usar o MAD intrínsecos a fim de fazer uma multiplicação e uma adição ao mesmo tempo
- Precalcule o máximo possível na CPU e passe como constantes para o material
- **Favorecer operações de movimentação do sombreador de pixel para o sombreador de vértice**
    - Geralmente, o número de vértices < < # de pixels (ou seja, 720p = = 921.600 pixels, 1080p = = 2.073.600 pixels, etc.)

#### <a name="remove-gpu-stages"></a>Remover estágios de GPU
Os efeitos de pós-processamento podem ser muito caros e geralmente inibim a taxa de preenchimento do seu aplicativo. Isso também inclui técnicas de suavização de alias, como MSAA. No HoloLens, é recomendável evitar essas técnicas inteiramente. Além disso, os estágios adicionais do sombreador, como Geometry, envoltória e sombreadores de computação, devem ser evitados quando possível.

## <a name="memory-recommendations"></a>Recomendações de memória
A alocação de memória excessiva & as operações de desalocação podem ter efeitos adversos em seu aplicativo Holographic, resultando em desempenho inconsistente, quadros congelados e outros comportamentos prejudiciais. É especialmente importante entender as considerações de memória ao desenvolver no Unity, uma vez que o gerenciamento de memória é controlado pelo coletor de lixo.

#### <a name="object-pooling"></a>Pooling de objetos

O pooling de objetos é uma técnica popular para reduzir o custo de alocações contínuas & desalocações de objetos. Isso é feito alocando um grande pool de objetos idênticos e reutilizando instâncias disponíveis inativas desse pool em vez de constantemente gerar e destruir objetos ao longo do tempo. Os pools de objetos são ótimos para componentes reutilizados que têm tempo de vida variável durante um aplicativo.

## <a name="see-also"></a>Consulte também
- [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
- [Configurações recomendadas do Unity](recommended-settings-for-unity.md)
