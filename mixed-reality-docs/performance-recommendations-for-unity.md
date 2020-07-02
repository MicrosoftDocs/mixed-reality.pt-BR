---
title: Recomendações de desempenho para o Unity
description: Dicas específicas do Unity para aprimorar o desempenho com aplicativos de realidade misturada.
author: troy-ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: gráficos, cpu, gpu, renderização, coleta de lixo, hololens
ms.localizationpriority: high
ms.openlocfilehash: c6c68a6dd6e8ba59bee983e158e210aed27d2b17
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216237"
---
# <a name="performance-recommendations-for-unity"></a>Recomendações de desempenho para o Unity

Este artigo se baseia na discussão descrita em [Recomendações de desempenho para realidade misturada](understanding-performance-for-mixed-reality.md), mas se concentra em aprendizados específicos do ambiente do mecanismo do Unity.

## <a name="use-recommended-unity-project-settings"></a>Usar configurações de projeto recomendadas do Unity

A primeira etapa mais importante ao otimizar o desempenho de aplicativos de realidade misturada no Unity é verificar se você está usando as [configurações de ambiente recomendadas para o Unity](recommended-settings-for-unity.md). Esse artigo traz um conteúdo com algumas das configurações de cena mais importantes para a criação de aplicativos do Mixed Reality de alto desempenho. Algumas dessas configurações recomendadas também são realçadas abaixo.

## <a name="how-to-profile-with-unity"></a>Como criar um perfil com o Unity

O Unity fornece o **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** interno, que é um ótimo recurso para reunir informações de desempenho úteis para seu aplicativo específico. Embora seja possível executar o criador de perfil no editor, essas métricas não representam o ambiente de runtime verdadeiro e, portanto, os resultados dessa tarefa devem ser usados com cautela. É recomendável criar o perfil do aplicativo remotamente durante a execução no dispositivo para obter insights mais precisos e práticos. Além disso, o [Depurador de Quadros](https://docs.unity3d.com/Manual/FrameDebugger.html) do Unity também é uma ferramenta de insights muito avançada a ser utilizada.

O Unity fornece uma excelente documentação para:
1) Como conectar o [Unity Profiler aos aplicativos UWP remotamente](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) Como [diagnosticar problemas de desempenho com o Unity Profiler de maneira eficaz](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> Com o Unity Profiler conectado e após a adição do criador de perfil de GPU (confira *Adicionar Criador de Perfil* no canto superior direito), é possível ver quanto tempo está sendo gasto na CPU e na GPU, respectivamente, no meio do criador de perfil. Isso permite que o desenvolvedor obtenha uma aproximação rápida caso o aplicativo esteja limitado pela CPU ou pela GPU.
>
> ![CPU vs GPU do Unity](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>Recomendações de desempenho da CPU

O conteúdo abaixo aborda mais práticas de desempenho aprofundadas, especialmente direcionadas ao desenvolvimento em C# e Unity.

#### <a name="cache-references"></a>Referências de cache

É uma melhor prática armazenar em cache as referências a todos os componentes relevantes e GameObjects na inicialização. Isso porque as chamadas de função repetitivas como *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* são significativamente mais caras em relação ao custo de memória necessário para armazenar um ponteiro. Isso também se aplica ao [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html) usado com muita frequência. Na verdade, o *Camera.main* usa apenas *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* abaixo dele, que pesquisa com alto custo o grafo de cena em busca de um objeto da câmera com a marca *"MainCamera"* .

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
> Evitar GetComponent(string) <br/>
> Ao usar *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* , há várias sobrecargas diferentes. É importante sempre usar as implementações baseadas em tipo e nunca a sobrecarga de pesquisa baseada em cadeia de caracteres. A pesquisa por cadeia de caracteres na cena é significativamente mais cara do que a pesquisa por tipo. <br/>
> (Adequado) Component GetComponent(Type type) <br/>
> (Adequado) T GetComponent\<T>() <br/>
> (Inadequado) Component GetComponent(string)> <br/>

#### <a name="avoid-expensive-operations"></a>Evitar operações caras

1) **Evite o uso do [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    Embora o LINQ possa ser muito limpo e de fácil leitura e escrita, em geral, ele exige muito mais computação e, particularmente, mais alocação de memória do que a escrita manual do algoritmo.

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

    Algumas APIs do Unity, embora úteis, podem ser muito caras de serem executadas. A maioria deles envolve a pesquisa de todo o grafo de cena em busca de alguma lista correspondente de GameObjects. Em geral, essas operações podem ser evitadas por meio do cache de referências ou da implementação de um componente de gerenciador para os GameObjects em questão, a fim de acompanhar as referências em runtime.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* e *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* devem ser eliminados a qualquer custo. Essas funções podem estar em uma ordem 1.000 vezes mais lenta do que as chamadas de função diretas.

3) **Cuidado com a conversão boxing**

    A [conversão boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) é um conceito fundamental do runtime e da linguagem C#. É o processo de encapsular variáveis de tipo de valor, como char, int, bool etc., em variáveis de tipo de referência. Quando é feita a conversão boxing de uma variável de tipo de valor, ela é encapsulada dentro de um System.Object que é armazenado no heap gerenciado. Assim, a memória é alocada e, por fim, quando descartada, precisa ser processada pelo coletor de lixo. Essas alocações e essas desalocações geram um custo de desempenho e, em muitos cenários, são desnecessárias ou podem ser substituídas com facilidade por uma alternativa menos cara.

    Uma das formas mais comuns de conversão boxing no desenvolvimento é o uso de [tipos de valor que permitem valor nulo](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/). É comum querer poder retornar nulo para um tipo de valor em uma função, especialmente quando a operação pode falhar ao tentar obter o valor. O possível problema dessa abordagem é que a alocação agora ocorre no heap e, consequentemente, precisa ser coletada como lixo mais tarde.

    **Exemplo de conversão boxing em C#**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **Exemplo de conversão boxing problemática por meio de tipos de valor que permitem valor nulo**

    Esse código demonstra uma classe de partícula fictícia que pode ser criada em um projeto do Unity. Uma chamada a `TryGetSpeed()` causará a alocação de objeto no heap, que precisará ser coletado como lixo posteriormente. Esse exemplo é particularmente problemático, pois pode haver mais de mil ou muito mais partículas em uma cena, cada uma sendo solicitada pela velocidade atual. Assim, milhares de objetos serão alocados e, consequentemente, desalocados a cada quadro, o que reduzirá muito o desempenho. A reescrita da função para retornar um valor negativo, como -1, a fim de indicar uma falha evitará esse problema e manterá a memória na pilha.

    ```csharp
        public class MyParticle
        {
            // Example of function returning nullable value type
            public int? TryGetSpeed()
            {
                // Returns current speed int value or null if fails
            }
        }
    ```

#### <a name="repeating-code-paths"></a>Repetição de caminhos de código

Uma função de retorno de chamada do Unity repetida (ou seja, Update) executada muitas vezes por segundo e/ou quadro deve ser escrita com muito cuidado. Qualquer operação cara aqui terá um impacto enorme e consistente sobre o desempenho.

1) **Funções de retorno de chamada vazio**

    Embora possa parecer não ter problema deixar o código abaixo em seu aplicativo, especialmente porque cada script do Unity é inicializado automaticamente com esse bloco de código, esses retornos de chamada vazios podem realmente ficar muito caros. O Unity opera em um limite de código não gerenciado/gerenciado, entre o código do UnityEngine e o código do aplicativo. A alternância de contexto nessa ponte é bem cara, mesmo que não haja nada a ser executado. Isso se torna especialmente problemático se o aplicativo tem centenas de GameObjects com componentes que tenham retornos de chamada repetitivos e vazios do Unity.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update() é a manifestação mais comum desse problema de desempenho, mas outros retornos de chamada repetitivos do Unity, como os seguintes, podem ser igualmente tão ruins, se não piores: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage() etc. 

2) **Operações para favorecer a execução uma vez por quadro**

    As APIs do Unity a seguir são operações comuns para muitos aplicativos holográficos. Embora nem sempre seja possível, os resultados dessas funções podem ser computados com muita frequência, e os resultados são reutilizados no aplicativo para determinado quadro.

    a) Em geral, é uma boa prática ter uma classe singleton dedicada ou um serviço para processar o foco Raycast na cena e, em seguida, reutilizar esse resultado em todos os outros componentes de cena, em vez de fazer operações Raycast repetidas e essencialmente idênticas por componente. É claro que alguns aplicativos podem exigir raycasts de diferentes origens ou em diferentes [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) Evite operações GetComponent() em retornos de chamada repetitivos do Unity, como Update(), com o [cache de referências](#cache-references) em Start() ou Awake()

        UnityEngine.Object.GetComponent()

    c) É uma boa prática criar uma instância de todos os objetos, se possível, na inicialização e usar o [pool de objetos](#object-pooling) para reciclar e reutilizar GameObjects por todo o runtime do aplicativo

        UnityEngine.Object.Instantiate()

3) **Evite interfaces e constructos virtuais**

    A invocação de chamadas de função por meio de interfaces em comparação com objetos diretos ou chamada de funções virtuais muitas vezes pode ser muito mais custosa do que a utilização de constructos diretos ou chamadas de função diretas. Se a interface ou a função virtual for desnecessária, ela deverá ser removida. No entanto, o impacto no desempenho dessas abordagens geralmente vale a pena se a utilização delas simplifica a colaboração de desenvolvimento, bem como a legibilidade e a manutenção do código.

    Em geral, a recomendação é não marcar campos e funções como virtuais, a menos que haja uma expectativa bem definida de que esse membro precise ser substituído. É preciso ser especialmente cuidadoso em relação aos caminhos de código de alta frequência que são chamados muitas vezes por quadro ou, até mesmo, uma vez por quadro, como um método `UpdateUI()`.

4) **Evite transmitir structs por valor**

    Ao contrário das classes, os structs são tipos de valor e, quando transmitidos diretamente para uma função, o conteúdo deles é copiado para uma instância recém-criada. Essa cópia adiciona custo de CPU, bem como memória adicional na pilha. Para structs pequenos, o efeito é geralmente muito mínimo e, portanto, aceitável. No entanto, para as funções invocadas repetidamente a cada quadro, bem como as funções que usam structs grandes, se possível, modifique a definição de função para transmiti-la por referência. [Saiba mais aqui](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>Diversos

1) **Física**

    r) Em geral, a maneira mais fácil de aprimorar a física é limitar o tempo gasto na física ou no número de iterações por segundo. É claro que isso reduzirá a precisão da simulação. Confira [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) no Unity

    b) Os tipos de colisores no Unity têm características de desempenho amplamente diferentes. A ordem abaixo lista os colisores com melhor desempenho até os colisores com pior desempenho, da esquerda para a direita. O mais importante é evitar os colisores de malha, que são consideravelmente mais caros do que os colisores primitivos.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    Confira [Melhores práticas de física do Unity](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) para obter mais informações

2) **Animações**

    Desabilite as animações ociosas desabilitando o componente Animator (a desabilitação do objeto de jogo não terá o mesmo efeito). Evite padrões de design em que um animador fica em um loop configurando um valor para o mesmo item. Há uma sobrecarga considerável nessa técnica, sem nenhum efeito no aplicativo. [Saiba mais aqui.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **Algoritmos complexos**

    Se o aplicativo estiver usando algoritmos complexos, como cinemática inversa, localização de caminho etc., procure encontrar uma abordagem mais simples ou ajustar as configurações relevantes para o desempenho dele

## <a name="cpu-to-gpu-performance-recommendations"></a>Recomendações do desempenho de CPU para GPU

Em geral, o desempenho de CPU para GPU se resume às **chamadas de desenho** enviadas à placa gráfica. Para aprimorar o desempenho, as chamadas de desenho precisam ser estrategicamente **a) reduzidas** ou **b) reestruturadas** para resultados ideais. Como as próprias chamadas de desenho fazem uso intensivo de recursos, a redução delas diminuirá o trabalho geral necessário. Além disso, as alterações de estado entre chamadas de desenho exigem etapas caras de validação e conversão no driver gráfico e, portanto, a reestruturação das chamadas de desenho do aplicativo para limitar as alterações de estado (ou seja, materiais diferentes etc.) podem aumentar o desempenho.

O Unity conta com um ótimo artigo que fornece uma visão geral e se aprofunda no envio em lote de chamadas de desenho para a plataforma.
- [Envio em lote de chamadas de desenho do Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>Renderização com uma instância de passagem única

A renderização com uma instância de passagem única no Unity permite que as chamadas de desenho para cada olho sejam reduzidas a uma chamada de desenho com instância. Devido à coerência de cache entre duas chamadas de desenho, também há alguma melhoria de desempenho na GPU.

Como habilitar esse recurso no seu projeto do Unity
1)  Abra **Configurações de XR do Player** (acesse **Editar** > **Configurações do Projeto** > **Player** > **Configurações de XR**)
2) Selecione **Instância de Passagem Única** no menu suspenso **Método de Renderização de Estéreo** (a caixa de seleção **Realidade Virtual Compatível** precisa estar marcada)

Leia os artigos a seguir do Unity para obter detalhes dessa abordagem de renderização.
- [Como maximizar o desempenho de RA e VR com a renderização avançada de estéreo](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Instância de passagem única](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Um problema comum na renderização com uma instância de passagem única ocorre se os desenvolvedores já têm sombreadores personalizados existentes não escritos para a criação de instância. Depois de habilitar esse recurso, os desenvolvedores poderão perceber que alguns GameObjects são renderizados apenas em um olho. Isso ocorre porque os sombreadores personalizados associados não têm as propriedades apropriadas para a criação de instância.
>
> Confira [Renderização de estéreo de passagem única para o HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) do Unity para saber como resolver esse problema

#### <a name="static-batching"></a>Envio em lote estático

O Unity pode enviar em lote muitos objetos estáticos para reduzir chamadas de desenho para a GPU. O envio em lote estático funciona para a maioria dos objetos do [renderizador](https://docs.unity3d.com/ScriptReference/Renderer.html) no Unity que **1) compartilha o material** e **2) é marcada como *Estático*** (selecione um objeto no Unity e clique na caixa de seleção no canto superior direito do inspetor). Os GameObjects marcados como *Estáticos* não podem ser movidos durante todo o runtime do aplicativo. Portanto, o envio em lote estático pode ser difícil de ser aproveitado no HoloLens, no qual praticamente todos os objetos precisam ser colocados, movidos, dimensionados etc. Para headsets imersivos, o envio em lote estático pode reduzir drasticamente as chamadas de desenho e, portanto, aprimorar o desempenho.

Leia *Envio em lote estático* em [Envio em lote de chamadas de desenho no Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) para obter mais detalhes.

#### <a name="dynamic-batching"></a>Envio em lote dinâmico

Como é problemático marcar objetos como *Estáticos* para o desenvolvimento no HoloLens, o envio em lote dinâmico pode ser uma ótima ferramenta para compensar esse recurso. É claro que isso também pode ser útil em headsets imersivos. No entanto, o envio em lote dinâmico no Unity pode ser difícil de ser habilitado, porque os GameObjects precisam **a) compartilhar o material** e **b) atender a uma lista longa de outros critérios**.

Leia *Envio em lote dinâmico* em [Envio em lote de chamadas de desenho no Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) para obter a lista completa. Normalmente, os GameObjects se tornam inválidos para serem enviados em lote dinamicamente, porque os dados de malha associados não podem ter mais de 300 vértices.

#### <a name="other-techniques"></a>Outras técnicas

O envio em lote só pode ocorrer se vários GameObjects podem compartilhar o material. Normalmente, isso será bloqueado pela necessidade de os GameObjects terem uma textura exclusiva para o respectivo material. É comum combinar as texturas em uma textura grande, um método conhecido como [atlas de textura](https://en.wikipedia.org/wiki/Texture_atlas).

Além disso, geralmente é preferível combinar malhas em um só GameObject sempre que possível e razoável. Cada renderizador do Unity terá as chamadas de desenho associadas em vez de enviar uma malha combinada em um renderizador.

>[!NOTE]
> A modificação das propriedades de Renderer.material em runtime criará uma cópia do material e, portanto, poderá interromper o envio em lote. Use Renderer.sharedMaterial para modificar as propriedades de material compartilhadas em GameObjects.

## <a name="gpu-performance-recommendations"></a>Recomendações de desempenho da GPU

Saiba mais sobre [como otimizar a renderização de gráficos no Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

### <a name="optimize-depth-buffer-sharing"></a>Otimizar o compartilhamento de buffer de profundidade

Geralmente, é recomendável habilitar o **Compartilhamento de buffer de profundidade** nas **Configurações de XR do Player** para otimizar a [estabilidade do holograma](Hologram-stability.md). No entanto, ao habilitar a reprojeção de etapa tardia baseada em profundidade com essa configuração, é recomendável selecionar o **formato de profundidade de 16 bits** em vez do **formato de profundidade de 24 bits**. Os buffers de profundidade de 16 bits reduzem drasticamente a largura de banda (e, portanto, a energia) associada ao tráfego do buffer de profundidade. Isso pode ser um grande ganho na redução de energia e na melhoria do desempenho. No entanto, há dois resultados negativos possíveis com o uso do *formato de profundidade de 16 bits*.

**Luta z**

A fidelidade de intervalo de profundidade reduzida possibilita a ocorrência da [luta z](https://en.wikipedia.org/wiki/Z-fighting) mais com 16 bits do que com 24 bits. Para evitar esses artefatos, modifique os planos de clipes próximos/distantes da [câmera do Unity](https://docs.unity3d.com/Manual/class-Camera.html) para considerar a precisão mais baixa. Para aplicativos baseados no HoloLens, um plano de recorte distante de 50 m em vez dos 1.000 m padrão do Unity geralmente pode eliminar qualquer luta Z.

**Buffer de estêncil desabilitado**

Quando o Unity cria uma [textura de renderização com profundidade de 16 bits](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), nenhum buffer de estêncil é criado. A seleção do formato de profundidade de 24 bits, conforme a documentação do Unity, criará um buffer z de 24 bits, bem como um [buffer de estêncil de 8 bits] (https://docs.unity3d.com/Manual/SL-Stencil.html) (se 32 bits for aplicável em um dispositivo, que geralmente é o caso, como o HoloLens).

### <a name="avoid-full-screen-effects"></a>Evitar efeitos de tela inteira

As técnicas que operam na tela inteira podem ser bastante custosas, já que a ordem de magnitude é milhões de operações a cada quadro. Portanto, é recomendável evitar [efeitos de pós-processamento](https://docs.unity3d.com/Manual/PostProcessingOverview.html) como suavização, gestos de abrir a mão, entre outros.

### <a name="optimal-lighting-settings"></a>Configurações de iluminação ideais

A [Iluminação Global em Tempo Real](https://docs.unity3d.com/Manual/GIIntro.html) do Unity pode fornecer resultados visuais excepcionais, mas envolve cálculos de iluminação bastante custosos. É recomendável desabilitar a Iluminação Global em Tempo Real em cada arquivo de cena do Unity por meio de **Janela** > **Renderização** > **Configurações de Iluminação** > Desmarcar **Iluminação Global em Tempo Real**.

Além disso, é recomendável desabilitar toda a conversão de sombra, pois ela também adiciona passagens de GPU custosas a uma cena do Unity. As sombras podem ser desabilitadas conforme a luz, mas também podem ser controladas de maneira holística por meio das configurações de Qualidade.

**Editar** > **Configurações do Projeto** e, em seguida, selecione a categoria **Qualidade** > selecione **Baixa Qualidade** para a plataforma UWP. Também é possível definir apenas a propriedade **Shadows** como **Desabilitar Sombras**.

Recomendamos usar a iluminação integrada com seus modelos no Unity.

### <a name="reduce-poly-count"></a>Reduzir a contagem de polígonos

A contagem de polígonos geralmente é reduzida por meio dos métodos a seguir
1) Remoção de objetos de uma cena
2) Eliminação de ativos, que reduz o número de polígonos para determinada malha
3) Implementação de um [sistema de LOD (Nível de Detalhe)](https://docs.unity3d.com/Manual/LevelOfDetail.html) no aplicativo que renderiza objetos distantes com a versão de polígono mais baixo da mesma geometria

### <a name="understanding-shaders-in-unity"></a>Noções básicas sobre os sombreadores do Unity

Uma aproximação fácil para comparar os sombreadores em desempenho é identificar o número médio de operações que cada um executa em runtime. Isso pode ser feito com facilidade no Unity.

1) Selecione o ativo do sombreador ou um material e, no canto superior direito da janela do inspetor, selecione o ícone de engrenagem seguido de **"Selecionar Sombreador"**

    ![Selecionar um sombreador no Unity](images/Select-shader-unity.png)
2) Com o ativo do sombreador selecionado, clique no botão **"Compilar e mostrar código"** na janela do inspetor

    ![Compilar o código do sombreador no Unity](images/compile-shader-code-unity.PNG)

3) Após a compilação, procure a seção de estatísticas nos resultados com o número de operações diferentes para o vértice e o sombreador de pixel (observação: os sombreadores de pixel costumam ser chamados de sombreadores de fragmento)

    ![Operações de sombreador padrão do Unity](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a>Otimizar sombreadores de pixel

Observando os resultados da estatística compilada usando o método acima, em média, o [sombreador de fragmento](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) geralmente executará mais operações do que o [sombreador de vértice](https://en.wikipedia.org/wiki/Shader#Vertex_shaders). O sombreador de fragmento, também conhecido como sombreador de pixel, é executado por pixel na saída da tela, ao passo que o sombreador de vértice só é executado por vértice de todas as malhas que estão sendo desenhadas na tela. 

Portanto, os sombreadores de fragmento têm mais instruções do que os sombreadores de vértice devido a todos os cálculos de iluminação e quase sempre são executados em um conjunto de dados maior. Por exemplo, se a saída da tela for uma imagem de 2.000 por 2.000, o sombreador de fragmento poderá ser executado 2.000 * 2.000 = 4.000.000 vezes. Se a renderização de dois olhos estiver sendo feita, esse número dobrará, pois há duas telas. Se um aplicativo de realidade misturada tiver várias passagens, efeitos de pós-processamento de tela inteira ou estiver renderizando várias malhas no mesmo pixel, esse número aumentará drasticamente. 

Portanto, a redução do número de operações no sombreador de fragmento pode, em geral, proporcionar ganhos de desempenho muito maiores em otimizações no sombreador de vértice.

#### <a name="unity-standard-shader-alternatives"></a>Alternativas do sombreador padrão do Unity

Em vez de usar uma PBR (renderização baseada em física) ou outro sombreador de alta qualidade, examine a utilização de um sombreador mais barato e com melhor desempenho. O [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece o [sombreador padrão do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) que foi otimizado para projetos de realidade misturada.

O Unity também fornece um sombreador apagado, com vértice iluminado, difuso e outras opções de sombreador simplificadas que são significativamente mais rápidas em comparação com o sombreador padrão do Unity. Confira [Uso e desempenho de sombreadores internos](https://docs.unity3d.com/Manual/shader-Performance.html) para obter informações mais detalhadas.

#### <a name="shader-preloading"></a>Pré-carregamento de sombreador

Use o *Pré-carregamento de sombreador* e outros truques para otimizar o [tempo de carregamento do sombreador](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html). Em particular, o pré-carregamento de sombreador significa que você não verá nenhum problema devido à compilação do sombreador em runtime.

### <a name="limit-overdraw"></a>Limitar a sobreposição

No Unity, é possível exibir sobreposições para a cena alternando o [**menu do modo de desenho**](https://docs.unity3d.com/Manual/ViewModes.html) no canto superior esquerdo da **Exibição de cena** e selecionando **Sobreposição**.

Em geral, a sobreposição pode ser atenuada com a remoção de objetos antecipadamente ao envio para a GPU. O Unity fornece detalhes sobre como implementar a [Remoção de Oclusão](https://docs.unity3d.com/Manual/OcclusionCulling.html) para o mecanismo.

## <a name="memory-recommendations"></a>Recomendações de memória

As operações de alocação e desalocação de memória excessiva podem ter efeitos adversos no aplicativo holográfico, resultando em desempenho inconsistente, quadros congelados e outros comportamentos prejudiciais. É especialmente importante entender as considerações de memória no desenvolvimento no Unity, pois o gerenciamento de memória é controlado pelo coletor de lixo.

#### <a name="garbage-collection"></a>Coleta de lixo

Os aplicativos holográficos perderão o tempo de computação do processamento para o GC (coletor de lixo) quando o GC for ativado para analisar objetos que não estão mais no escopo durante a execução, e a memória deles precisará ser liberada, de modo que possa ser disponibilizada para reutilização. As alocações e as desalocações constantes geralmente exigirão que o coletor de lixo seja executado com mais frequência, prejudicando o desempenho e a experiência do usuário.

O Unity forneceu uma página excelente que explica em detalhes como o coletor de lixo funciona e dicas para escrever um código mais eficiente em relação ao gerenciamento de memória.
- [Como otimizar a coleta de lixo em jogos do Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

Uma das práticas mais comuns que leva ao excesso de coleta de lixo não é armazenar em cache referências a componentes e classes no desenvolvimento no Unity. Todas as referências devem ser capturadas durante Start() ou Awake() e reutilizadas em funções posteriores, como Update() ou LateUpdate().

Outras dicas rápidas:
- Use a classe C# [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) para criar dinamicamente cadeias de caracteres complexas em runtime
- Remova as chamadas a Debug.Log() quando não for mais necessário, pois elas ainda são executadas em todas as versões de build de um aplicativo
- Se o aplicativo holográfico geralmente exige muita memória, considere a possibilidade de chamar [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) durante o carregamento de fases, como ao apresentar uma tela de carregamento ou de transição

#### <a name="object-pooling"></a>Pool de objetos

O pool de objetos é uma técnica popular para reduzir o custo de alocações e desalocações contínuas de objetos. Isso é feito pela alocação de um grande pool de objetos idênticos e pela reutilização das instâncias disponíveis inativas desse pool em vez da criação e da destruição constantes de objetos ao longo do tempo. Os pools de objetos são ótimos para componentes reutilizados que têm um tempo de vida variável durante um aplicativo.

- [Tutorial de pool de objetos no Unity](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>Desempenho de inicialização

Você deve considerar iniciar seu aplicativo com uma cena menor e, em seguida, usar *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* para carregar o restante da cena. Isso permite que o aplicativo chegue a um estado interativo o mais rápido possível. Esteja ciente de que pode haver um grande pico de CPU enquanto a nova cena está sendo ativada e que qualquer conteúdo renderizado pode tremer ou apresentar algum problema. Um modo de resolver isso é definir a propriedade AsyncOperation.allowSceneActivation como "false" na cena que está sendo carregada, aguardar a cena ser carregada, limpar a tela para preto e, em seguida, defini-la novamente como "true" para concluir a ativação da cena.

Lembre-se de que, durante o carregamento da cena de inicialização, a tela inicial holográfica será exibida para o usuário.

## <a name="see-also"></a>Veja também
- [Como otimizar a renderização de gráficos em jogos do Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Como otimizar a coleta de lixo em jogos do Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [Melhores práticas de física [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [Como otimizar scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
