---
title: Entendendo o desempenho da realidade misturada
description: Tópicos avançados e detalhes sobre como otimizar o desempenho para aplicativos do Windows Mixed Reality
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, desempenho, otimização, CPU, GPU
ms.openlocfilehash: 287b95363acff00ab7a0407475e0a419fc076611
ms.sourcegitcommit: 184227dc591ca2791f523d520555730ba1e95b5c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79479569"
---
# <a name="understanding-performance-for-mixed-reality"></a>Entendendo o desempenho da realidade misturada

Este artigo é uma introdução ao entendimento do significado do desempenho para seu aplicativo de realidade misturada.  A experiência do usuário pode ser bastante degradada se seu aplicativo não for executado em uma taxa de quadros ideal. Os hologramas aparecerão instáveis e o controle de cabeça do ambiente será impreciso, levando a uma experiência ruim para o usuário. O desempenho deve ser considerado um recurso de primeira classe para o desenvolvimento de realidade misturada e não uma tarefa em polonês.

Os valores de taxa de quadros de alto desempenho para cada plataforma de destino são listados abaixo.

| Platform | Taxa de quadros de destino |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality ultra PCs](immersive-headset-hardware-details.md) | 90 FPS |
| [Computadores Windows Mixed Reality](immersive-headset-hardware-details.md) | 60 FPS |

A estrutura a seguir descreve as práticas recomendadas para atingir as taxas de quadros de destino. Se estiver desenvolvendo no Unity, considere ler o [artigo recomendações de desempenho para o Unity](performance-recommendations-for-unity.md) para obter dicas sobre como medir e melhorar a taxa de quadros no ambiente do Unity.

## <a name="understanding-performance-bottlenecks"></a>Noções básicas sobre afunilamentos de desempenho

Se seu aplicativo tiver uma taxa de quadros com desempenho alto, a primeira etapa será analisar e entender onde o aplicativo é computacionalmente intensivo. Há dois processadores principais responsáveis pelo trabalho de renderizar sua cena: a CPU e a GPU. Cada um deles lida com diferentes aspectos do seu aplicativo de realidade misturada. Há três locais principais onde os afunilamentos podem ocorrer: 

1. **Thread de aplicativo-CPU** -esse thread é responsável pela lógica do aplicativo. Isso inclui o processamento de entrada, animações, física e outras lógicas de aplicativo.
2. **Renderizar thread-CPU para GPU** -esse thread é responsável por enviar suas chamadas de desenho para a GPU. Quando seu aplicativo deseja renderizar um objeto como um cubo ou modelo, esse thread envia uma solicitação para a GPU para executar essas operações.
3. **GPU** -esse processador geralmente manipula a pipeline gráfica do seu aplicativo para transformar dados 3D (modelos, texturas, etc.) em pixels. Ele finalmente produz uma imagem 2D para enviar à tela do seu dispositivo.

![Tempo de vida de um quadro](images/lifetime-of-a-frame.png)

Geralmente, os aplicativos do HoloLens serão associados à GPU, mas nem sempre. Use as ferramentas e técnicas abaixo para entender onde seu aplicativo específico está afunilado.

## <a name="how-to-analyze-your-application"></a>Como analisar seu aplicativo

Há muitas ferramentas que permitem que você entenda o perfil de desempenho do seu aplicativo de realidade misturada. Eles permitirão que você localize onde e por que você tem afunilamentos, para que possa solucioná-los.

Abaixo estão algumas ferramentas comuns para obter informações detalhadas de criação de perfil para seu aplicativo:
- [Analisadores de desempenho de gráficos Intel](https://software.intel.com/gpa)
- [Depuradores de gráficos do Visual Studio](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Criador de perfil do Unity](https://docs.unity3d.com/Manual/Profiler.html)
- [Depurador de quadros do Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Como criar um perfil em qualquer ambiente

Uma maneira de determinar se você está ligado à GPU ou a CPU associada ao seu aplicativo é diminuir a resolução da saída de destino de renderização. Ao reduzir o número de pixels a serem calculados, isso reduzirá sua carga de GPU. O dispositivo será renderizado para uma textura menor e, em seguida, a amostra para exibir a imagem final.

Depois de diminuir a resolução de renderização, se:
1) **Aumento**da taxa de quadros do aplicativo; provavelmente, você está **vinculado à GPU**
1) Taxa de quadros do aplicativo **inalterada**, provavelmente você está com a **CPU associada**

>[!NOTE]
>O Unity fornece a capacidade de modificar facilmente a resolução de destino de renderização de seu aplicativo em tempo de execução por meio da propriedade *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* . A imagem final apresentada no dispositivo tem uma resolução fixa. A plataforma obterá uma amostra da saída de resolução mais baixa para criar uma imagem de resolução mais alta para renderização em exibições. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Como melhorar seu aplicativo

### <a name="cpu-performance-recommendations"></a>Recomendações de desempenho da CPU

Em geral, a maior parte do trabalho em um aplicativo de realidade misturada na CPU envolve a execução da "simulação" da cena e o processamento da lógica do aplicativo. As seguintes áreas geralmente são destinadas à otimização:

- Animations
- Professor
- Alocações de memória
- Algoritmos complexos (ou seja, cinemática inversa, localização de caminho)

### <a name="gpu-performance-recommendations"></a>Recomendações de desempenho de GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Compreendendo a largura de banda versus a taxa de preenchimento
Ao renderizar um quadro na GPU, um aplicativo é geralmente ligado pela largura de banda da memória ou pela taxa de preenchimento.

- **Largura de banda de memória** é a taxa de leituras e gravações que a GPU pode executar da memória
    - Para identificar as limitações de largura de banda, reduza a qualidade da textura e verifique se a taxa de quadros foi aprimorada.
    - No Unity, isso pode ser feito alterando a **qualidade da textura** em **Editar** **configurações do projeto** >  > configurações de **[qualidade](https://docs.unity3d.com/Manual/class-QualitySettings.html)** .
- A **taxa de preenchimento** refere-se aos pixels que podem ser desenhados por segundo pela GPU.
    - Para identificar as limitações da taxa de preenchimento, diminua a resolução de vídeo e verifique se a taxa de quadros foi aprimorada. 
    - No Unity, isso pode ser feito por meio da propriedade *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*

A largura de banda de memória geralmente envolve otimizações para:
1) Diminuir as resoluções de textura
2) Utilizar menos texturas (normais, especulares, etc.)

A taxa de preenchimento concentra-se na redução do número de operações que precisam ser computadas para um pixel renderizado final. Isso inclui a redução:
1) Número de objetos a serem renderizados/processados
2) Número de operações por sombreador
3) Número de estágios de GPU para o resultado final (sombreadores de geometria, efeitos de pós-processamento, etc.)
4) Número de pixels a serem renderizados (resolução de vídeo)

#### <a name="reduce-polygon-count"></a>Reduzir contagem de polígonos

Contagens de polígono mais altas resultam em mais operações para a GPU; [reduzir o número de polígonos](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) em sua cena reduzirá o tempo de renderização. Há outros fatores envolvidos no sombreamento da geometria que pode ser cara, mas a contagem de polígonos é a métrica mais simples para determinar o quão caro será a renderização de uma cena.

#### <a name="limit-overdraw"></a>Limite de extração

O alto sobreempate ocorre quando vários objetos são renderizados, mas não são mostrados na tela, pois ficam ocultos por um objeto occluding. Imagine examinar uma parede que contém objetos por trás dela. Toda a geometria seria processada para renderização, mas apenas a parede opaca precisa ser renderizada. Isso resulta em operações desnecessárias.

#### <a name="shaders"></a>Sombreadores

Os sombreadores são programas pequenos que são executados na GPU e executam duas etapas importantes na renderização:
1) Determinando quais vértices devem ser desenhados e onde estão no espaço da tela (o sombreador de vértice)
    - O sombreador de vértice geralmente é executado por vértice para cada malha.
2) Determinando a cor de cada pixel (o sombreador de pixel)
    - O sombreador de pixel é executado por pixel renderizado pela geometria à qual a textura está sendo renderizada.

Normalmente, os sombreadores executam muitas transformações e cálculos de iluminação. Embora modelos de iluminação complexos, sombras e outras operações possam gerar resultados fantásticos, eles também têm um preço. Reduzir o número de operações computadas em sombreadores pode reduzir muito o trabalho necessário para a GPU por quadro.

##### <a name="shader-coding-recommendations"></a>Recomendações de codificação de sombreador

- Use a filtragem biline, sempre que possível
- Reorganize as expressões para usar o MAD intrínsecos a fim de fazer uma multiplicação e uma adição ao mesmo tempo
- Precalcule o máximo possível na CPU e passe como constantes para o material
- **Favorecer operações de movimentação do sombreador de pixel para o sombreador de vértice**
    - Em geral, o número de vértices é muito menor do que o número de pixels (720p é de 921.600 pixels, 1080p é 2.073.600 pixels, etc.)

#### <a name="remove-gpu-stages"></a>Remover estágios de GPU

Os efeitos de pós-processamento podem ser muito caros e aumentar a taxa de preenchimento do seu aplicativo. Isso inclui técnicas de suavização de alias, como MSAA. No HoloLens, é recomendável evitar essas técnicas totalmente, bem como os estágios de sombreador adicionais, como geometria, envoltória e sombreadores de computação.

## <a name="memory-recommendations"></a>Recomendações de memória

As operações de alocação e desalocação de memória excessivas podem resultar em desempenho inconsistente, quadros congelados e outros comportamentos prejudiciais. É especialmente importante entender as considerações de memória ao desenvolver no Unity, pois o gerenciamento de memória é controlado pelo coletor de lixo.

#### <a name="object-pooling"></a>Pooling de objetos

O pool de objetos é uma técnica popular para reduzir o custo de alocações e desalocações contínuas de objetos. Isso é feito alocando um grande pool de objetos idênticos e reutilizando instâncias disponíveis inativas desse pool em vez de constantemente gerar e destruir objetos ao longo do tempo. Os pools de objetos são ótimos para componentes reutilizados que têm tempo de vida variável durante um aplicativo.

## <a name="see-also"></a>Consulte também
- [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
- [Configurações recomendadas do Unity](recommended-settings-for-unity.md)
- [Otimizar modelos 3D](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Práticas recomendadas para converter e otimizar modelos 3D em tempo real](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)

