---
title: Recomendações de desempenho para o Unity
description: Dicas específicas do Unity para melhorar o desempenho com aplicativos de realidade misturada.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: gráficos, CPU, GPU, renderização, coleta de lixo, hololens
ms.openlocfilehash: b0821f07184bff8630f6b6af0d0fc461f6fcd133
ms.sourcegitcommit: 8f3ff9738397d9b9fdf4703b14b89d416f0186a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67843341"
---
# <a name="performance-recommendations-for-unity"></a>Recomendações de desempenho para o Unity

Este artigo se baseia na discussão descrita em [recomendações de desempenho para realidade misturada](understanding-performance-for-mixed-reality.md) , mas se concentra em aprendizados específicos ao ambiente do mecanismo do Unity.

Também é altamente aconselhável que os desenvolvedores examinem as [configurações de ambiente recomendadas para o Unity](Recommended-settings-for-unity.md). Este artigo tem conteúdo com algumas das configurações de cena mais importantes em relação à criação de aplicativos de realidade misturada de alto desempenho. Algumas dessas configurações recomendadas também são destacadas abaixo.

## <a name="how-to-profile-with-unity"></a>Como criar um perfil com o Unity

O Unity fornece o **[Unity](https://docs.unity3d.com/Manual/Profiler.html)** Profiler interno, que é um ótimo recurso para coletar informações de desempenho valiosas para seu aplicativo específico. Embora seja possível executar o criador de perfil no editor, essas métricas não representam o ambiente de tempo de execução verdadeiro e, portanto, os resultados dessa tarefa devem ser usados com cautela. É recomendável criar o perfil de seu aplicativo remotamente durante a execução no dispositivo para obter informações mais precisas e acionáveis. Além disso, o [depurador de quadros](https://docs.unity3d.com/Manual/FrameDebugger.html) do Unity também é uma ferramenta muito poderosa e insight a ser utilizada.

O Unity fornece uma excelente documentação para:
1) Como conectar o [Unity Profiler aos aplicativos UWP remotamente](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) Como diagnosticar [com eficiência problemas de desempenho com o Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window) Profiler

>[!NOTE]
> Com o Unity Profiler conectado e depois de adicionar o criador de perfil de GPU (consulte *Adicionar criador de perfil* no canto superior direito), é possível ver quanto tempo está sendo gasto na CPU & GPU, respectivamente no meio do criador de perfil. Isso permite que o desenvolvedor obtenha uma aproximação rápida se seu aplicativo estiver limitado por CPU ou GPU.
>
> ![CPU do Unity vs GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>Recomendações de desempenho da CPU

O conteúdo abaixo aborda mais práticas de desempenho aprofundadas, especialmente direcionadas para o C# desenvolvimento de & do Unity.

#### <a name="cache-references"></a>Referências de cache

É uma prática recomendada armazenar em cache referências a todos os componentes relevantes e GameObjects na inicialização. Isso ocorre porque as chamadas de função repetidas, como *[GetComponent\<T > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* , são significativamente mais caras em relação ao custo de memória para armazenar um ponteiro. Isso também se aplica à [câmera. principal](https://docs.unity3d.com/ScriptReference/Camera-main.html), muito usada regularmente. *Camera. Main* realmente usa apenas *[FindGameObjectsWithTag ()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* abaixo, que pesquisa caro o grafo de cena para um objeto Camera com a marca *"MainCamera"* .

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
> Evitar GetComponent (cadeia de caracteres) <br/>
> Ao usar *[GetComponent ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* , há várias sobrecargas diferentes. É importante sempre usar as implementações baseadas em tipo e nunca a sobrecarga de pesquisa baseada em cadeia de caracteres. Pesquisar por cadeia de caracteres em sua cena é significativamente mais dispendioso do que Pesquisar por tipo. <br/>
> Recomendá Componente GetComponent (tipo Type) <br/>
> Recomendá T getcomponente\<t > () <br/>
> Satisfatório Componente GetComponent (String) > <br/>

#### <a name="avoid-expensive-operations"></a>Evite operações caras

1) **Evite o uso do [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    Embora o LINQ possa ser muito claro e fácil de ler e escrever, ele geralmente requer muito mais computação e, particularmente, mais alocação de memória do que gravar o algoritmo manualmente.

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

    Algumas APIs do Unity, embora úteis, podem ser muito caras para serem executadas. A maioria deles envolve a pesquisa de todo o grafo de cena em busca de alguma lista correspondente de GameObjects. Essas operações geralmente podem ser evitadas por meio de cache de referências ou implementação de um componente de gerente para o GameObjects em questão para acompanhar as referências em tempo de execução.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* e *[BroadcastMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* devem ser eliminados a todos os custos. Essas funções podem estar na ordem de mil vezes maior mais lenta do que as chamadas de função diretas.

3) **Cuidado com Boxing**

    [Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) é um conceito fundamental da linguagem C# e do tempo de execução. É o processo de encapsular variáveis de tipo de valor, como Char, int, bool, etc. em variáveis de tipo de referência. Quando uma variável de valor digitado é "Boxed", ela é encapsulada dentro de um System. Object que é armazenado no heap gerenciado. Assim, a memória é alocada e, eventualmente, quando descartado deve ser processado pelo coletor de lixo. Essas alocações e desalocações incorrem em um custo de desempenho e, em muitos cenários, são desnecessárias ou podem ser facilmente substituídas por uma alternativa menos dispendiosa.

#### <a name="repeating-code-paths"></a>Repetindo caminhos de código

Qualquer função de retorno de chamada de Unity repetida (ou seja, Atualização) que são executadas muitas vezes por segundo e/ou quadro devem ser escritos com muito cuidado. Qualquer operação cara aqui terá um impacto enorme e consistente sobre o desempenho.

1) **Funções de retorno de chamada vazias**

    Embora o código abaixo possa parecer inocente para sair em seu aplicativo, especialmente porque cada script do Unity inicializa automaticamente com esse bloco de código, esses retornos de chamada vazios podem realmente se tornar muito caros. O Unity opera em um limite de código não gerenciado/sem gerenciamento, entre o código UnityEngine e o código do aplicativo. A alternância de contexto por essa ponte é bastante cara, mesmo se não houver nada a ser executado. Isso se tornará especialmente problemático se seu aplicativo tiver 100 do GameObjects com componentes que tenham retornos de chamada de Unity vazios.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update () é a manifestação mais comum desse problema de desempenho, mas outros retornos de chamada de Unity repetitivos, como o seguinte, podem ser igualmente tão ruins se não pior: FixedUpdate (), LateUpdate (), OnPostRender ", OnPreRender (), OnRenderImage (), etc. 

2) **Operações para favorecer a execução uma vez por quadro**

    As seguintes APIs do Unity são operações comuns para muitos aplicativos Holographic. Embora nem sempre seja possível, os resultados dessas funções podem ser computados com muita frequência e os resultados são reutilizados no aplicativo para um determinado quadro.

    r) geralmente, é uma boa prática ter uma classe singleton dedicada ou um serviço para lidar com sua Raycast olhar na cena e, em seguida, reutilizar esse resultado em todos os outros componentes de cena, em vez de fazer operações Raycast repetidas e essencialmente idênticas por cada componente. É claro que alguns aplicativos podem exigir raycasts de origens diferentes ou contra diferentes [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) Evite operações GetComponent () em retornos de chamada de Unity repetidos como Update () armazenando [referências em cache](#cache-references) em Start () ou ativo ()

        UnityEngine.Object.GetComponent()

    c) é uma boa prática criar uma instância de todos os objetos, se possível, na inicialização e usar o [pool de objetos](#object-pooling) para reciclar e reutilizar Gameobjects em tempo de execução de seu aplicativo

        UnityEngine.Object.Instantiate()

3) **Evitar interfaces e construções virtuais**

    Chamar chamadas de função por meio de interfaces vs objetos diretos ou chamar funções virtuais muitas vezes pode ser muito mais caro do que utilizar construções diretas ou chamadas de função diretas. Se a interface ou a função virtual for desnecessária, ela deverá ser removida. No entanto, o impacto no desempenho dessas abordagens geralmente vale a pena se a utilização delas simplifica a colaboração de desenvolvimento, a legibilidade do código e a manutenção do código. 

4) **Evite passar structs por valor**

    Ao contrário das classes, as estruturas são de tipos de valor e, quando passadas diretamente para uma função, seu conteúdo é copiado para uma instância recém-criada. Essa cópia adiciona custo de CPU, bem como memória adicional na pilha. Para structs pequenos, o efeito é geralmente muito mínimo e, portanto, aceitável. No entanto, para as funções invocadas repetidamente todos os quadros, bem como funções que tomam grandes estruturas, se possível, modifique a definição de função para passar por referência. [Saiba mais aqui](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>Diversos

1) **Professor**

    r) geralmente, a maneira mais fácil de melhorar a física é limitar a quantidade de tempo gasto na física ou o número de iterações por segundo. É claro que isso reduzirá a precisão da simulação. Confira [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) no Unity

    b) o tipo de colisor no Unity tem características de desempenho amplamente diferentes. A ordem a seguir lista os coistores de melhor desempenho para os colisors de desempenho mínimo da esquerda para a direita. É mais importante evitar os conflitantes de malha que são consideravelmente mais caros do que os conflitantes primitivos.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    Consulte [práticas recomendadas da física do Unity](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) para obter mais informações

2) **Janelas**

    Desabilite animações ociosas desabilitando o componente Animator (desabilitar o objeto de jogo não terá o mesmo efeito). Evite padrões de design em que uma Animator fica em um loop Configurando um valor para a mesma coisa. Há uma sobrecarga considerável para essa técnica, sem nenhum efeito no aplicativo. [Saiba mais aqui.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **Algoritmos complexos**

    Se seu aplicativo estiver usando algoritmos complexos, como cinemática inversa, localização de caminho, etc., procure encontrar uma abordagem mais simples ou ajustar as configurações relevantes para seu desempenho

## <a name="cpu-to-gpu-performance-recommendations"></a>Recomendações de desempenho de CPU para GPU

Geralmente, o desempenho da CPU para a GPU se resume às **chamadas de desenho** enviadas para a placa gráfica. Para melhorar **o** desempenho, as chamadas de desenho precisam ser estrategicamente reduzidas ou **b)** reestruturadas para obter resultados ideais. Como as próprias chamadas de desenho são intensivas de recursos, reduzi-las reduzirá o trabalho geral necessário. Além disso, as alterações de estado entre chamadas de desenho exigem etapas dispendiosas de validação e conversão no driver de gráficos e, portanto, a reestruturação das chamadas de desenho do seu aplicativo para limitar as alterações de estado (ou seja, materiais diferentes, etc.) podem melhorar o desempenho.

O Unity tem um ótimo artigo que fornece uma visão geral e aprofundamento em chamadas de desenho em lote para sua plataforma.
- [Lote de chamadas do Unity Draw](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>Renderização de passagem única em instância

A renderização de passagem única da instância no Unity permite que as chamadas de desenho para cada olho sejam reduzidas para uma chamada de desenho com instância. Devido à coerência de cache entre duas chamadas de desenho, também há alguma melhoria de desempenho na GPU também.

Para habilitar esse recurso em seu projeto do Unity
1)  Abra **as configurações do Player XR** (vá para **Editar** > **configurações** > do projeto configurações do**Player** > **XR**)
2) Selecione **passagem única instância** no menu suspenso **método de renderização estéreo** (a caixa de seleção**com suporte da realidade virtual** deve estar marcada)

Leia os artigos a seguir do Unity para obter detalhes com essa abordagem de renderização.
- [Como maximizar o desempenho de AR e VR com renderização avançada de estéreo](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Instância de passagem única](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Um problema comum com a renderização de passagem única ocorrerá se os desenvolvedores já tiverem sombreadores personalizados existentes não escritos para instanciação. Depois de habilitar esse recurso, os desenvolvedores podem perceber que alguns GameObjects são renderizados apenas de um olho. Isso ocorre porque os sombreadores personalizados associados não têm as propriedades apropriadas para instanciação.
>
> Consulte [renderização de estéreo de passagem única para o HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) do Unity para saber como resolver esse problema

#### <a name="static-batching"></a>Envio em lote estático

O Unity é capaz de fazer o lote de muitos objetos estáticos para reduzir chamadas de empates para a GPU. O envio em lote estático para a maioria dos objetos de [processador](https://docs.unity3d.com/ScriptReference/Renderer.html) no Unity que **1) compartilham o mesmo material** e **2)  são marcados como estáticos** (selecione um objeto no Unity e clique na caixa de seleção no canto superior direito do Inspetor). GameObjects marcado como *estático* não pode ser movido por todo o tempo de execução do aplicativo. Portanto, o envio em lote estático pode ser difícil de aproveitar no HoloLens, em que praticamente todos os objetos precisam ser colocados, movidos, dimensionados, etc. Para headsets de imersão, o envio em lote estático pode reduzir drasticamente as chamadas de desenho e, portanto, melhorar o desempenho.

Leia *envio em lote estático* em [desenho de chamada em lote no Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) para obter mais detalhes.

#### <a name="dynamic-batching"></a>Envio em lote dinâmico

Como é problemático marcar objetos como estáticos  para o desenvolvimento do HoloLens, o envio em lote dinâmico pode ser uma ótima ferramenta para compensar esse recurso. É claro que também pode ser útil em headsets de imersão. O envio em lote dinâmico no Unity pode ser difícil, embora seja possível habilitar, pois GameObjects deve ter **um) compartilhamento do mesmo material** e **b) que atendem a uma longa lista de outros critérios**.

Leia *envio em lote dinâmico* em [desenho de chamada em lote no Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) para obter a lista completa. Normalmente, GameObjects se tornam inválidos para serem agrupados dinamicamente porque os dados de malha associados não podem ter mais de 300 vértices.

#### <a name="other-techniques"></a>Outras técnicas

O envio em lote só poderá ocorrer se vários GameObjects forem capazes de compartilhar o mesmo material. Normalmente, isso será bloqueado pela necessidade de GameObjects ter uma textura exclusiva para seu respectivo material. É comum combinar texturas em uma textura grande, um método conhecido como [Atlas de textura](https://en.wikipedia.org/wiki/Texture_atlas).

Além disso, é geralmente preferível combinar malhas em um gameobject sempre que possível e razoável. Cada renderizador no Unity terá sua chamada Draw associada em vez de enviar uma malha combinada em um processador. 

>[!NOTE]
> Modificar as propriedades de Renderer. material em tempo de execução criará uma cópia do material e, assim, poderá interromper o envio em lote. Use Renderer. sharedMaterial para modificar propriedades de material compartilhado em GameObjects.

## <a name="gpu-performance-recommendations"></a>Recomendações de desempenho de GPU

Saiba mais sobre como [otimizar a renderização de gráficos no Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games) 

### <a name="optimize-depth-buffer-sharing"></a>Otimizar o compartilhamento de buffer de profundidade

Geralmente, é recomendável habilitar o **compartilhamento de buffer de profundidade** nas configurações do **Player XR** para otimizar a [estabilidade do holograma](Hologram-stability.md). No entanto, ao habilitar a Reprojeção de etapa tardia baseada em profundidade com essa configuração, é recomendável selecionar **formato de profundidade de 16 bits** em vez de **formato de profundidade de 24 bits**. Os buffers de profundidade de 16 bits reduzem drasticamente a largura de banda (e, portanto, a energia) associada ao tráfego de profundidade do buffer. Isso pode ser um grande ganho de energia, mas só é aplicável a experiências com uma pequena faixa de profundidade, já que o [combate a z](https://en.wikipedia.org/wiki/Z-fighting) é mais provável que ocorra com 16 bits do que 24 bits. Para evitar esses artefatos, modifique os planos de clipes próximos/distantes da [câmera do Unity](https://docs.unity3d.com/Manual/class-Camera.html) para considerar a precisão mais baixa. Para aplicativos baseados em HoloLens, um plano de recorte distante de 50 milhões em vez do 1000m padrão de Unity geralmente pode eliminar qualquer combate a z.

### <a name="reduce-poly-count"></a>Reduzir número de polylines

A contagem de polígonos geralmente é reduzida por
1) Removendo objetos de uma cena
2) Asset Decimation, que reduz o número de polígonos para uma determinada malha
3) Implementando um [sistema de LOD (nível de detalhe)](https://docs.unity3d.com/Manual/LevelOfDetail.html) em seu aplicativo que renderiza objetos distantes com a versão de polígono inferior da mesma geometria

### <a name="understanding-shaders-in-unity"></a>Compreendendo sombreadores no Unity

Uma aproximação fácil para comparar sombreadores no desempenho é identificar o número médio de operações executadas no tempo de execução. Isso pode ser feito facilmente no Unity.

1) Selecione o ativo do sombreador ou selecione um material e, no canto superior direito da janela do Inspetor, selecione o ícone de engrenagem e, em seguida, **"selecionar sombreador"**

    ![Selecionar sombreador no Unity](images/Select-shader-unity.png)
2) Com o ativo do sombreador selecionado, clique no botão **"Compilar e mostrar código"** na janela do Inspetor

    ![Compilar código de sombreador no Unity](images/compile-shader-code-unity.PNG)

3) Após a compilação, procure a seção estatísticas nos resultados com o número de operações diferentes para o vértice e o sombreador de pixel (Observação: os sombreadores de pixel costumam ser chamados de sombreadores de fragmento)

    ![Operações do sombreador padrão do Unity](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a>Sombreadores de pixel Optmize

Observando os resultados da estatística compilada usando o método acima, o sombreador de [fragmento](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) geralmente executará mais operações do que o sombreador de [vértice](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) em média. O sombreador de fragmento, também conhecido como sombreador de pixel, é executado por pixel na saída da tela enquanto o sombreador de vértice só é executado por vértice de todas as malhas que estão sendo desenhadas para a tela. 

Portanto, não apenas os sombreadores de fragmento têm mais instruções do que os sombreadores de vértice por causa de todos os cálculos de iluminação, os sombreadores de fragmento quase sempre são executados em um conjunto de um DataSet maior. Por exemplo, se a saída da tela for uma imagem de 2K por 2K, o sombreador de fragmento poderá ser executado 2000 * 2000 = 4 milhões vezes. Se estiver renderizando dois olhos, esse número dobrará desde que há duas telas. Se um aplicativo de realidade misturada tiver várias passagens, efeitos de pós-processamento de tela inteira ou renderizar várias malhas no mesmo pixel, esse número aumentará drasticamente. 

Portanto, a redução do número de operações no sombreador de fragmentos pode, em geral, proporcionar ganhos de desempenho muito maiores em otimizações no sombreador de vértice.

#### <a name="unity-standard-shader-alternatives"></a>Alternativas do sombreador padrão do Unity

Em vez de usar um PBR (processamento com base físico) ou outro sombreador de alta qualidade, examine a utilização de um sombreador mais econômico e barato. O [Kit de ferramentas de realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece o [sombreador padrão MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) que foi otimizado para projetos de realidade misturada.

O Unity também fornece um unlit, vértice iluminado, difuso e outras opções de sombreador simplificadas que são significativamente mais rápidas em comparação com o sombreador padrão do Unity. Consulte [uso e desempenho de sombreadores internos](https://docs.unity3d.com/Manual/shader-Performance.html) para obter informações mais detalhadas.

#### <a name="shader-preloading"></a>Pré-carregamento de sombreador

Use o *pré-carregamento* de sombreador e outros truques para otimizar o [tempo de carregamento](http://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)do sombreador. Em particular, o pré-carregamento de sombreador significa que você não verá nenhum hitches devido à compilação do sombreador de tempo de execução.

### <a name="limit-overdraw"></a>Limite de extração

No Unity, é possível exibir sobredesenhos para sua cena, alternando o [**menu de modo de desenho**](https://docs.unity3d.com/Manual/ViewModes.html) no canto superior esquerdo do **modo de exibição de cena** e selecionando sobredesenhe.

Em geral, o sobreempate pode ser mitigado com a remoção de objetos antecipadamente antes de serem enviados para a GPU. O Unity fornece detalhes sobre como implementar a [remoção de oclusão](https://docs.unity3d.com/Manual/OcclusionCulling.html) para seu mecanismo.

## <a name="memory-recommendations"></a>Recomendações de memória

A alocação de memória excessiva & as operações de desalocação podem ter efeitos adversos em seu aplicativo Holographic, resultando em desempenho inconsistente, quadros congelados e outros comportamentos prejudiciais. É especialmente importante entender as considerações de memória ao desenvolver no Unity, uma vez que o gerenciamento de memória é controlado pelo coletor de lixo.

#### <a name="garbage-collection"></a>Coleta de lixo

Os aplicativos holographics perderão o tempo de computação para o coletor de lixo (GC) quando o GC for ativado para analisar objetos que não estão mais no escopo durante a execução e sua memória precisa ser liberada para que possa ser disponibilizada para reutilização. Alocações e deslocalidades constantes geralmente exigem que o coletor de lixo seja executado com mais frequência, o que prejudicando o desempenho e a experiência do usuário.

O Unity forneceu uma página excelente que explica em detalhes como o coletor de lixo funciona e dicas para escrever código mais eficiente em relação ao gerenciamento de memória.
- [Otimizando a coleta de lixo em jogos do Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

Uma das práticas mais comuns que leva ao excesso de coleta de lixo não é armazenar em cache referências a componentes e classes no desenvolvimento do Unity. Todas as referências devem ser capturadas durante o início () ou ativo () e reutilizadas em funções posteriores, como Update () ou LateUpdate ().

Outras dicas rápidas:
- Use a classe [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# para criar dinamicamente cadeias de caracteres complexas em tempo de execução
- Remover chamadas para Debug. log () quando não for mais necessário, pois elas ainda são executadas em todas as versões de Build de um aplicativo
- Se seu aplicativo Holographic geralmente requer muita memória, considere chamar [ _**System. GC. Collect ()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) durante o carregamento de fases, como ao apresentar uma tela de carregamento ou de transição

#### <a name="object-pooling"></a>Pooling de objetos

O pooling de objetos é uma técnica popular para reduzir o custo de alocações contínuas & desalocações de objetos. Isso é feito alocando um grande pool de objetos idênticos e reutilizando instâncias disponíveis inativas desse pool em vez de constantemente gerar e destruir objetos ao longo do tempo. Os pools de objetos são ótimos para componentes reutilizados que têm tempo de vida variável durante um aplicativo.

- [Tutorial de pooling de objetos no Unity](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>Desempenho de inicialização

Você deve considerar iniciar seu aplicativo com uma cena menor e, em seguida, usar o *[scenemanager. LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* para carregar o restante da cena. Isso permite que seu aplicativo chegue a um estado interativo o mais rápido possível. Lembre-se de que pode haver um grande pico de CPU enquanto a nova cena está sendo ativada e que qualquer conteúdo renderizado pode stutter ou incômodo. Uma maneira de contornar isso é definir a propriedade AsyncOperation. allowSceneActivation como false na cena que está sendo carregada, aguardar a cena ser carregada, limpar a tela para preto e, em seguida, definir de volta para true para concluir a ativação da cena.

Lembre-se de que, enquanto a cena de inicialização estiver carregando, a tela inicial do Holographic será exibida para o usuário.

## <a name="see-also"></a>Consulte também
- [Otimizando a renderização de gráficos em jogos do Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Otimizando a coleta de lixo em jogos do Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [Práticas recomendadas de física [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [Otimizando scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
