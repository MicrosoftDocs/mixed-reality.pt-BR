---
title: Recomendações de desempenho para Unity
description: Dicas de específicas do Unity para melhorar o desempenho com aplicativos de realidade misturada.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: elementos gráficos, cpu, gpu, renderização, coleta de lixo, hololens
ms.openlocfilehash: b0821f07184bff8630f6b6af0d0fc461f6fcd133
ms.sourcegitcommit: 8f3ff9738397d9b9fdf4703b14b89d416f0186a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67843341"
---
# <a name="performance-recommendations-for-unity"></a>Recomendações de desempenho para Unity

Este artigo se baseia na discussão descrita [recomendações de desempenho para realidade misturada](understanding-performance-for-mixed-reality.md) mas enfatiza os conhecimentos específicos do ambiente de mecanismo do Unity.

Também é altamente recomendável que os desenvolvedores examinar a [configurações de ambiente para o artigo do Unity recomendadas](Recommended-settings-for-unity.md). Este artigo possui conteúdo com algumas das configurações mais importantes de cena no que diz respeito à criação de aplicativos de realidade mista de alto desempenho. Algumas dessas configurações recomendadas estão destacadas abaixo também.

## <a name="how-to-profile-with-unity"></a>Como criar um perfil com o Unity

Unity fornece a **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** interna que é um ótimo recurso para coletar informações de desempenho valioso para seu aplicativo. Embora o criador de perfil no editor pode ser executada, essas métricas não representam o ambiente de tempo de execução true e dessa forma, os resultados deste devem ser usados com cautela. É recomendável para o perfil remotamente seu aplicativo durante a execução no dispositivo para obter informações mais precisas e acionáveis. Além disso, do Unity [quadro depurador](https://docs.unity3d.com/Manual/FrameDebugger.html) também é muito eficiente e ferramenta de análise de utilizar.

Unity fornece excelente documentação para:
1) Como conectar-se a [Unity profiler para aplicativos UWP remotamente](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) Como efetivamente [diagnosticar problemas de desempenho com o Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> Com o Profiler Unity conectado e depois de adicionar o criador de perfil GPU (consulte *Profiler adicionar* no canto superior direito), é possível ver quanto tempo é gasto na CPU e GPU respectivamente no meio do criador de perfil. Isso permite que o desenvolvedor obter uma aproximação rápida se seu aplicativo é a CPU ou GPU limitado.
>
> ![CPU do Unity vs GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>Recomendações de desempenho de CPU

O conteúdo abaixo aborda mais práticas abrangentes de desempenho, especialmente orientadas para Unity & C# desenvolvimento.

#### <a name="cache-references"></a>Referências de cache

É uma prática recomendada para referências de cache para todos os componentes relevantes e GameObjects na inicialização. Isso ocorre porque, como chamadas de função de repetição *[GetComponent\<T > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* são significativamente mais caro em relação à custo para armazenar um ponteiro de memória. Isso também se aplica a para o bastante, regularmente usada [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html). *Camera.main* , na verdade, apenas utiliza *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* sob qual forma mais barata pesquisará seu grafo de cena para um objeto de câmera com a *"MainCamera"*  marca.

```CS
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    private Camera cam;
    private CustomComponent comp;

    void Start() 
    {
        cam = Camera.main;
        comp = GetComponent<CustomComponent>();
    }

    void Update()
    {
        // Good
        this.transform.position = cam.transform.position + cam.transform.forward * 10.0f;

        // Bad
        this.transform.position = Camera.main.transform.position + Camera.main.transform.forward * 10.0f;

        // Good
        comp.DoSomethingAwesome();

        // Bad
        GetComponent<CustomComponent>().DoSomethingAwesome();
    }
}
```

>[!NOTE] 
> Evite GetComponent(string) <br/>
> Ao usar  *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* , há uma série de sobrecargas diferentes. É importante usar sempre as implementações de tipo com base e nunca a sobrecarga de pesquisa com base em cadeia de caracteres. Pesquisar pela cadeia de caracteres na sua cena é significativamente mais caro do que a pesquisa por tipo. <br/>
> (BOM) Componente GetComponent (tipo) <br/>
> (BOM) T GetComponent\<T >) <br/>
> (Inválido) Componente GetComponent(string) > <br/>

#### <a name="avoid-expensive-operations"></a>Evite operações dispendiosas

1) **Evite o uso de [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    Embora o LINQ pode ser muito claro e fácil de ler e gravar, ele geralmente requer computação muito mais e mais particularmente alocação de memória do que escrever o algoritmo manualmente.

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **APIs comuns do Unity**

    Determinadas APIs do Unity, embora úteis, pode ser muito caro para executar. A maioria delas envolve pesquisando seu grafo de cena inteira para alguma lista correspondente de GameObjects. Essas operações geralmente podem ser evitadas com referências de cache ou implementar um componente do Gerenciador de GameObjects em questão acompanhar as referências em tempo de execução.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)*  e *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* deve ser eliminado a todo custo. Essas funções podem ser na ordem de 1000 x mais lento do que chamadas de função direta.

3) **Lembre-se de conversão boxing**

    [Conversão boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) é um conceito fundamental do C# idioma e o tempo de execução. Ele é o processo de quebra automática de variáveis de tipo de valor, como char, int, bool, etc. em variáveis do tipo de referência. Quando uma variável de tipo de valor é "demarcada", ele é encapsulado dentro de um System. Object, que é armazenado na heap gerenciada. Portanto, a memória é alocada e, eventualmente, quando descartado devem ser processadas pelo coletor de lixo. Essas alocações e desalocações incorrer um custo de desempenho e em muitos cenários são desnecessárias ou podem ser facilmente substituídas por uma alternativa mais barata.

#### <a name="repeating-code-paths"></a>Caminhos de código de repetição

Quaisquer funções de retorno de chamada de Unity (isto é, repetição Atualização) que são executadas várias vezes por segundo e/ou quadro deve ser escrito com muito cuidado. Quaisquer operações dispendiosas aqui terá consistente e enorme impacto no desempenho.

1) **Funções de retorno vazia**

    Embora o código a seguir pode parecer inocente para deixar no seu aplicativo, especialmente porque cada Unity script automático inicializa com este bloco de código, esses retornos de chamada vazios podem, na verdade, tornam-se muito caros. Unity funciona e para trás ao longo de um limite de código não gerenciado/gerenciado, entre o código de UnityEngine e o código do aplicativo. Essa ponte troca de contexto é relativamente caro, mesmo se não houver nada a executar. Isso se torna especialmente problemático se seu aplicativo tiver centenas de GameObjects com componentes que têm retornos de chamada de Unity repetição vazios.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update () é a manifestação mais comum desse problema de desempenho, mas outros retornos de chamada do Unity repetitivos, como a seguir podem ser igualmente tão ruim se não é pior: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc. 

2) **Operações para favorecer a executar uma vez por quadro**

    As seguintes APIs do Unity são operações comuns para muitos aplicativos Holographic. Embora não é sempre possível, os resultados dessas funções muito comum podem ser calculados uma vez e os resultados novamente utilizados no aplicativo para um determinado período.

    a) geralmente é recomendável ter uma classe Singleton ou um serviço para manipular seu foco Raycast na cena e, em seguida, reutilizar esse resultado em todos os outros componentes de cena, em vez de fazer essencialmente idênticas e repetidas operações de Raycast por cada dedicado componente. Obviamente, alguns aplicativos podem exigir raycasts de origens diferentes ou em relação a diferentes [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) evitar operações GetComponent() nos retornos de chamada de Unity repetidas, como Update () por [referências de cache](#cache-references) em Start () ou Awake()

        UnityEngine.Object.GetComponent()

    c) é uma boa prática para criar uma instância de todos os objetos, se possível, na inicialização e usar [pool de objetos](#object-pooling) reciclagem e reutilização GameObjects ao longo do tempo de execução do seu aplicativo

        UnityEngine.Object.Instantiate()

3) **Evite interfaces e construções virtuais**

    Invocando chamadas de função por meio de interfaces vs direct objetos ou chamar funções virtuais às vezes podem ser muito mais caros do que utiliza construções diretas ou chamadas de função direta. Se a função virtual ou a interface é desnecessária, ela deverá ser removida. No entanto, o desempenho de ocorrências para essas abordagens são geralmente que vale a pena a compensação se utilizar-os simplifica a colaboração de desenvolvimento, a legibilidade do código e manutenção de código. 

4) **Evite structs de passagem por valor**

    Diferentemente das classes, structs são tipos de valor e quando passados diretamente para uma função, seu conteúdo é copiado para uma instância recém-criada. Essa cópia adiciona custo, bem como memória adicional na pilha de CPU. Para structs pequeno, o efeito é geralmente muito mínima e, portanto, é aceitável. No entanto, para as funções chamadas repetidamente a cada quadro, bem como funções que levam a grandes structs, se possível modificar a definição de função para passar por referência. [Saiba mais aqui](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>Diversos

1) **Física**

    a) em geral, a maneira mais fácil para melhorar a física é limitar a quantidade de tempo gasto em física ou o número de iterações por segundo. Obviamente, isso reduzirá precisão de simulação. Ver [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) no Unity

    b) o tipo de colisores no Unity ter características de desempenho muito diferentes. A ordem a seguir lista as maioria dos colisores alto desempenho para menos colisores de alto desempenho da esquerda para a direita. É muito importante evitar Colisores de malha que são significativamente mais caro do que o primitivos colisores.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    Ver [práticas recomendadas do Unity física](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) para obter mais informações

2) **Animações**

    Desabilitar animações ociosas, desabilitando o componente Animator (desabilitar o objeto do jogo não terá o mesmo efeito). Evite os padrões de design onde um animator se encontra em um loop de definir um valor para a mesma coisa. Há uma sobrecarga considerável para essa técnica, sem afetar o aplicativo. [Saiba mais aqui.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **Algoritmos complexos**

    Se seu aplicativo está usando algoritmos complexos como cinemática inversa, a localização do caminho, etc, procure para localizar uma abordagem mais simples ou ajustar as configurações relevantes para o desempenho

## <a name="cpu-to-gpu-performance-recommendations"></a>Recomendações de desempenho de CPU para GPU

Em geral, o desempenho de CPU para GPU é fornecido para baixo até a **chamadas de desenho** enviado para a placa gráfica. Para melhorar o desempenho, chamadas de desenho precisam ser estrategicamente **a) reduzido** ou **b) reestruturados** para obter melhores resultados. Como as chamadas de desenho em si são intensivo de recursos, reduzindo-os reduzirá trabalho geral necessário. Além disso, estado é alterado entre chamadas de desenho exige validação dispendiosa e etapas de conversão no driver de gráficos e assim, reestruturação de chamadas de desenho do seu aplicativo para limitar as alterações de estado (ou seja, materiais diferentes, etc.) pode melhorar o desempenho.

Unity tem um ótimo artigo que fornece uma visão geral e mergulha envio em lote as chamadas de desenho para a plataforma deles.
- [Unity desenhar a chamada de envio em lote](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>Renderização de instância única passagem

Passagem única Instanced renderização no Unity permite chamadas de desenho para cada olho seja reduzido para baixo até a chamada de um desenho instanciado. Devido a coerência de cache entre as duas chamadas de desenho, também há alguma melhoria de desempenho na GPU também.

Para habilitar esse recurso em seu projeto do Unity
1)  Abra **configurações do Player XR** (acesse **editar** > **configurações do projeto** > **Player**  >  **XR configurações**)
2) Selecione **instância única de passar** da **estéreo de método de renderização** menu suspenso (**suporte de realidade Virtual** caixa de seleção deve ser marcada)

Leia os seguintes artigos do Unity para obter detalhes com essa abordagem de renderização.
- [Como maximizar o desempenho de AR e VR com renderização estéreo avançada](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Instanciação de passagem única](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Um problema comum com a única passar instância renderização ocorre se os desenvolvedores têm já existente de sombreadores personalizados não escritos para criação de instância. Depois de habilitar esse recurso, os desenvolvedores podem perceber a renderização de apenas alguns GameObjects em um olho. Isso ocorre porque os sombreadores personalizados associados não tem as propriedades adequadas para criação de instância.
>
> Ver [único passar estéreo de renderização para HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) do Unity para resolver esse problema

#### <a name="static-batching"></a>Envio em lote estático

Unity é capaz de muitos objetos estáticos para reduzir as chamadas de desenho para a GPU do lote. Envio em lote estático funciona para a maioria [renderizador](https://docs.unity3d.com/ScriptReference/Renderer.html) objetos no Unity que **1) compartilham o mesmo material** e **2) são todos marcado como *estático***  ( Selecione um objeto no Unity e clique na caixa de seleção no canto superior direito da inspeção de). GameObjects marcados como *estático* não podem ser movidos ao longo do tempo de execução do seu aplicativo. Assim, envio em lote estático pode ser difícil aproveitar o HoloLens, onde praticamente todo objeto precisa ser colocada, movidos, dimensionada, etc. Para fones imersivos em exposição, o envio em lote estático pode reduzir drasticamente as chamadas de desenho e, portanto, melhorar o desempenho.

Leia *envio em lote estáticos* sob [desenhar chamar envio em lote no Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) para obter mais detalhes.

#### <a name="dynamic-batching"></a>Envio em lote dinâmico

Uma vez que é problemático para marcar objetos como *estático* para desenvolvimento HoloLens, envio em lote dinâmico pode ser uma excelente ferramenta para compensar isso na falta de recurso. Naturalmente, é possível também ser útil em fones imersivos em exposição também. Envio em lote dinâmico no Unity pode ser difícil entanto habilitar porque GameObjects deve **a) compartilhar o mesmo Material** e **b) atender a uma longa lista de outros critérios**.

Leia *envio em lote dinâmico* sob [desenhar chamar envio em lote no Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) para obter a lista completa. Mais comumente, GameObjects se tornar inválidos a ser agrupadas dinamicamente, como os dados de malha associado podem ser vértices não mais do que 300.

#### <a name="other-techniques"></a>outras técnicas

Envio em lote só pode ocorrer se vários GameObjects são capazes de compartilhar o mesmo material. Normalmente, isso será bloqueado pela necessidade de GameObjects ter uma textura exclusiva para seu respectivo Material. É comum para combinar texturas em uma textura grande, um método conhecido como [textura Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).

Além disso, é geralmente preferível para combinar as malhas em um GameObject onde possível e razoável. Cada renderizador no Unity terá associou chamadas de desenho versus enviando uma malha combinada em um renderizador. 

>[!NOTE]
> Modificando as propriedades de Renderer.material em tempo de execução criará uma cópia do Material e, portanto, potencialmente quebrar envio em lote. Use Renderer.sharedMaterial para modificar as propriedades de material compartilhadas em GameObjects.

## <a name="gpu-performance-recommendations"></a>Recomendações de desempenho de GPU

Saiba mais sobre [otimizando a renderização de gráficos no Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games) 

### <a name="optimize-depth-buffer-sharing"></a>Otimizar o compartilhamento de buffer de profundidade

Geralmente, é recomendável habilitar **compartilhamento de buffer de profundidade** sob **configurações do Player XR** para otimizar o [estabilidade holograma](Hologram-stability.md). Ao habilitar reprojection de finais com base em profundidade com essa configuração, no entanto, é recomendável selecionar **formato de 16 bits profundidade** em vez de **formato de 24 bits profundidade**. O será de buffers de profundidade de 16 bits reduz drasticamente a largura de banda (e, portanto, do power) associado com o tráfego de buffer de profundidade. Isso pode ser uma vitória power grande, mas só é aplicável para experiências com um intervalo de profundidade pequeno como [combatendo o z](https://en.wikipedia.org/wiki/Z-fighting) é mais provável de ocorrer com 16 bits que 24 bits. Para evitar esses artefatos, modifique os planos de recorte próximo/distante do [câmera Unity](https://docs.unity3d.com/Manual/class-Camera.html) para levar em conta a precisão mais baixa. Para aplicativos baseados em HoloLens, um plano de recorte distante de 50 milhões em vez do padrão de Unity 1000 m geralmente pode eliminar qualquer combate a z.

### <a name="reduce-poly-count"></a>Reduzir a contagem de poly

Contagem de polígono geralmente é reduzida em qualquer uma
1) Removendo objetos de uma cena
2) Eliminação de ativo que reduz o número de polígonos para uma determinada malha
3) Implementando uma [sistema de nível de detalhe (LOD)](https://docs.unity3d.com/Manual/LevelOfDetail.html) em seu aplicativo que renderiza objetos com versão inferior polígono da mesma geometria de distância

### <a name="understanding-shaders-in-unity"></a>Sombreadores de Noções básicas sobre no Unity

Uma aproximação fácil comparar sombreadores no desempenho é identificar o número médio de operações de cada executa em tempo de execução. Isso pode ser feito facilmente no Unity.

1) Selecione seu ativo de sombreador ou selecione um material, no canto superior direito da janela do Inspetor, selecione o ícone de engrenagem e, em seguida, **"Selecione sombreador"**

    ![Selecione o sombreador no Unity](images/Select-shader-unity.png)
2) Com o ativo de sombreador selecionado, clique o **"Compilar e mostrar código"** botão sob a janela Inspetor

    ![Compilar o código de sombreador no Unity](images/compile-shader-code-unity.PNG)

3) Após a compilação, procure a seção de estatísticas nos resultados com o número de operações diferentes para o sombreador de vértices e de pixel (Observação: sombreadores de pixel geralmente também são chamados de sombreadores de fragmento)

    ![Operações de padrão de sombreador do Unity](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a>Sombreadores de pixel otimizado

Observando os resultados de estatística compilados usando o método acima, o [fragmento sombreador](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) geralmente executará operações de mais do que o [sombreador de vértices](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) em média. O sombreador de fragmentos, também conhecido como o sombreador de pixel é executado por pixel na tela enquanto o sombreador de vértice é apenas executado por vértice de todas as malhas que está sendo desenhado na tela de saída. 

Assim, não apenas os sombreadores de fragmento têm mais instruções de sombreadores de vértices devido a todos os cálculos de iluminação, sombreadores de fragmento quase sempre são executados em um conjunto de dados maior. Por exemplo, se a saída de tela é um 2K pela imagem de 2 mil, em seguida, o sombreador de fragmentos pode obter executada 2, 2 * 000, 000 = 4,000,000 vezes. Se dois olhos de renderização, esse número dobra, pois há duas telas. Se um aplicativo de realidade misturada tem várias passagens, em tela inteira pós-processamento efeitos ou renderização várias malhas para o mesmo pixel, esse número aumentará significativamente. 

Portanto, reduzir o número de operações no sombreador fragmento pode geralmente fornecer ganhos de desempenho muito superior sobre otimizações no sombreador de vértice.

#### <a name="unity-standard-shader-alternatives"></a>Alternativas de padrão de sombreador do Unity

Em vez de usar uma renderização fisicamente com base (PBR) ou outro sombreador de alta qualidade, examinar utilizando um mais eficazes e mais barato do sombreador. O [Kit de ferramentas de realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece o [sombreador padrão do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) que foi otimizado para projetos de realidade misturada.

Unity também oferece um apagada, vértice aceso, opções de sombreador simplificada difusa e outras que são significativamente mais rápida quando comparadas ao sombreador padrão do Unity. Ver [uso e desempenho de sombreadores interno](https://docs.unity3d.com/Manual/shader-Performance.html) para obter mais informações.

#### <a name="shader-preloading"></a>O pré-carregamento de sombreador

Use *sombreador pré-carregamento* e outros truques para otimizar [tempo de carregamento do sombreador](http://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html). Em particular, o pré-carregamento de sombreador significa que você não verá nenhum problema ou entrave qualquer devido à compilação do sombreador de tempo de execução.

### <a name="limit-overdraw"></a>Limite de excedente

No Unity, um pode exibir exceda sua cena, ativando/desativando o [ **desenhar o menu modo** ](https://docs.unity3d.com/Manual/ViewModes.html) no canto superior esquerdo do **exibição cena** e selecionando **excedentes** .

Em geral, excedente podem ser reduzidas pela remoção de objetos de antecedência antes de serem enviadas à GPU. Unity fornece detalhes sobre a implementação [oclusão traseira](https://docs.unity3d.com/Manual/OcclusionCulling.html) seu mecanismo.

## <a name="memory-recommendations"></a>Recomendações de memória

Operações de alocação e desalocação de memória excessiva podem ter efeitos adversos no seu aplicativo holográfico, resultando em desempenho inconsistente, quadros congelados e outro comportamento prejudicial. É especialmente importante entender as considerações de memória durante o desenvolvimento no Unity, uma vez que o gerenciamento de memória é controlado pelo coletor de lixo.

#### <a name="garbage-collection"></a>Coleta de lixo

Aplicativos holográfico perderá tempo de computação de processamento para o coletor de lixo (GC) quando o GC é ativado para analisar os objetos que não estão mais no escopo durante a execução e sua memória precisa ser liberado para que ele pode ser disponibilizado para reutilização. Desalocações e alocações constante geralmente exigirá o coletor de lixo executar com mais frequência, portanto, prejudicar o desempenho e experiência do usuário.

Unity forneceu uma excelente página que explica detalhadamente como funciona o coletor de lixo e dicas para escrever um código mais eficiente em relação ao gerenciamento de memória.
- [Otimizando a coleta de lixo em jogos do Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

Uma das práticas mais comuns que leva à coleta de lixo excessiva não está armazenando em cache as referências a componentes e classes no desenvolvimento do Unity. Todas as referências devem ser capturadas durante Start () ou Awake() e reutilizadas em funções posteriores como Update () ou LateUpdate().

Outras dicas rápidas:
- Use o [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# classe para criar dinamicamente as cadeias de caracteres complexas em tempo de execução
- Remover chamadas para Debug.Log() quando não for mais necessário conforme forem executadas ainda em todas as versões de compilação de um aplicativo
- Se seu aplicativo holográfico geralmente requer muita memória, considere a possibilidade de chamar [ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) durante o carregamento fases, como ao apresentar um carregamento ou tela de transição

#### <a name="object-pooling"></a>Ao pool de objetos

Pool de objetos é uma técnica popular para reduzir o custo de contínuas alocações e Desalocações de objetos. Isso é feito por alocar um grande pool de objetos idênticos e reutilização de instâncias inativas, disponíveis desse pool em vez de constantemente gerando e destruição de objetos ao longo do tempo. Pools de objeto são ótimos para componentes novamente utilizáveis que têm vida útil da variável durante a um aplicativo.

- [Objeto de pool de Tutorial no Unity](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>Desempenho de inicialização

Você deve considerar iniciar seu aplicativo com uma cena menor e, em seguida, usando *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* para carregar o restante da cena. Isso permite que seu aplicativo chegar a um estado interativo tão rápido quanto possível. Estar ciente de que poderá haver um grande aumento de CPU enquanto a nova cena está sendo ativada e qualquer conteúdo renderizado pode "gagueje" ou qualquer contratempo. Uma maneira de solucionar esse problema é definir a propriedade AsyncOperation.allowSceneActivation como false na cena que está sendo carregada, aguarde até que a cena carregar, limpar a tela para preto e, em seguida, defina novamente como verdadeiro para concluir a ativação da cena.

Lembre-se de que, enquanto a cena de inicialização está carregando a tela inicial holográfica será exibida ao usuário.

## <a name="see-also"></a>Consulte também
- [Otimizando a renderização de gráficos em jogos do Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Otimizando a coleta de lixo em jogos do Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [Práticas recomendadas de física [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [Otimizando Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
