---
title: Configurações recomendadas para o Unity
description: O Unity oferece alguns comportamentos específicos para a realidade misturada que pode ser alternada por meio de configurações do projeto.
author: troy-ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: Unity, configurações, realidade misturada
ms.openlocfilehash: 9b4e04e10e95f6c4f12a25a6f34236d9d2bf99a2
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278004"
---
# <a name="recommended-settings-for-unity"></a>Configurações recomendadas para o Unity

O Unity fornece um conjunto de opções padrão que geralmente são o caso médio de todas as plataformas. No entanto, o Unity oferece alguns comportamentos específicos para a realidade misturada que pode ser alternada por meio de configurações do projeto.

## <a name="performant-environment-set-up"></a>Configuração de ambiente de alto desempenho

### <a name="low-quality-settings"></a>Configurações de baixa qualidade

É importante modificar as configurações de **qualidade do Unity** para o seu ambiente para **muito baixo**. Isso ajudará a garantir que seu aplicativo esteja executando o forma definitiva na taxa de quadros apropriada. Isso é extremamente significativo para o desenvolvimento de HoloLens. Para o desenvolvimento de headsets de imersão, dependendo das especificações do desktop capacitando a experiência VR, ainda é possível obter uma taxa de quadros sem os parâmetros de qualidade mais baixos.

No Unity 2018 LTS +, o nível de qualidade do projeto pode ser definido por:

Em **Editar** **configurações do projeto** >  > **qualidade** > defina o **padrão** clicando na seta para baixo para o nível de qualidade **muito baixo**

### <a name="lighting-settings"></a>Configurações de iluminação

De forma semelhante às configurações de cena de qualidade, é importante definir as configurações de iluminação ideais para seu aplicativo de realidade misturada. No Unity, a configuração de iluminação que geralmente terá o maior impacto no desempenho em sua cena é a **iluminação global em tempo real**. Isso pode ser desativado indo em **janela** > **renderização** > configurações de **iluminação** > **iluminação global em tempo real**.

Há outra configuração de iluminação, **inclusas global iluminação**. Essa configuração pode fornecer resultados de desempenho e visualmente surpreendentes em headsets de imersão, mas geralmente não é aplicável para o desenvolvimento de HoloLens. **Inclusas global Illumniation** só é calculado para Gameobjects estáticos que geralmente não são encontrados em cenas de HoloLens devido à natureza de um ambiente desconhecido e em constante alteração.

Leia a [iluminação global do Unity](https://docs.unity3d.com/Manual/GIIntro.html) para obter mais informações. 

>[!NOTE]
> A **iluminação global em tempo real** é definida **por cena** e, portanto, os desenvolvedores devem salvar essa propriedade para cada cena do Unity em seu projeto.

### <a name="single-pass-instancing-rendering-path"></a>Caminho de renderização de instância única de passagem

Em aplicativos de realidade misturada, a cena é renderizada duas vezes, uma vez para cada olho para o usuário. Em comparação com o desenvolvimento 3D tradicional, isso efetivamente dobra a quantidade de trabalho que precisa ser computada. Portanto, é importante selecionar o caminho de renderização mais eficiente no Unity para economizar tanto na CPU quanto no tempo da GPU. A renderização de passagem única em instância otimiza o pipeline de renderização do Unity para aplicativos de realidade misturada e, portanto, é recomendável habilitar essa configuração por padrão para cada projeto.

Como habilitar esse recurso no seu projeto do Unity

1)  Abra **Configurações de XR do Player** (acesse **Editar** > **Configurações do Projeto** > **Player** > **Configurações de XR**)
2) Selecione **Instância de Passagem Única** no menu suspenso **Método de Renderização de Estéreo** (a caixa de seleção **Realidade Virtual Compatível** precisa estar marcada)

Leia os artigos a seguir do Unity para obter mais detalhes com essa abordagem de renderização.

- [Como maximizar o desempenho de RA e VR com a renderização avançada de estéreo](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Instância de passagem única](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

>[!NOTE]
> Um problema comum na renderização com uma instância de passagem única ocorre se os desenvolvedores já têm sombreadores personalizados existentes não escritos para a criação de instância. Depois de habilitar esse recurso, os desenvolvedores poderão perceber que alguns GameObjects são renderizados apenas em um olho. Isso ocorre porque os sombreadores personalizados associados não têm as propriedades apropriadas para a criação de instância.
>
> Confira [Renderização de estéreo de passagem única para o HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) do Unity para saber como resolver esse problema

### <a name="enable-depth-buffer-sharing"></a>Habilitar compartilhamento de buffer de profundidade

Para obter uma melhor estabilidade de holograma da percepção do usuário, é recomendável habilitar a propriedade de **compartilhamento de buffer de profundidade** no Unity. Ao ativar essa ação, o Unity compartilhará o mapa de profundidade produzido por seu aplicativo com a plataforma Windows Mixed Reality. A plataforma então será capaz de otimizar melhor a estabilidade do holograma especificamente para sua cena para qualquer determinado quadro que esteja sendo renderizado pelo seu aplicativo.

Como habilitar esse recurso no seu projeto do Unity

1) Abra **Configurações de XR do Player** (acesse **Editar** > **Configurações do Projeto** > **Player** > **Configurações de XR**)
2) Marque a caixa de seleção **Habilitar compartilhamento de buffer de profundidade** em SDKs de **realidade virtual** > expansão de **realidade mista do Windows** (a caixa de seleção**com suporte da realidade virtual** deve estar marcada)

Além disso, é recomendável selecionar **profundidade de 16 bits** na configuração de **formato de profundidade** neste painel, especialmente para o desenvolvimento de HoloLens. A seleção de 16 bits em comparação a 24 bits reduzirá significativamente os requisitos de largura de banda, pois menos dados precisarão ser movidos/processados.

Para que a plataforma Windows Mixed Reality Otimize a estabilidade do holograma, ela depende do buffer de profundidade para ser preciso e corresponder a qualquer holograma renderizado na tela. Portanto, com o compartilhamento de buffer de profundidade ativado, é importante ao renderizar a cor, para também renderizar a profundidade. No Unity, a maioria dos materiais opacos ou TransparentCutouts renderizará profundidade por padrão, mas os objetos de texto e transparente geralmente não renderizarão a profundidade, embora isso seja dependente de sombreador, etc.

Se estiver usando o [sombreador standard do kit de ferramentas do reality](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md), para renderizar a profundidade para objetos transparentes:

1) Selecione o material transparente que está usando o sombreador padrão MRTK e abra a janela do editor de Inspetor
2) Selecione o botão **corrigir agora** dentro do aviso de compartilhamento de buffer de profundidade. Isso também pode ser executado manualmente definindo o **modo de renderização** como **personalizado**; em seguida, defina **modo** como **transparente** e, por fim, defina a **gravação de profundidade** como **on**

> [!IMPORTANT]
> Os desenvolvedores devem ter cuidado com o combate ao Z ao alterar esses valores juntamente com as configurações de plano próximo/longe da câmera. O combate ao Z ocorre quando dois Gameobjects tentam renderizar para o mesmo pixel e devido a limitações na fidelidade do buffer de profundidade (ou seja, z Depth), Unity não pode distinguir qual objeto está na frente do outro. Os desenvolvedores notarão uma cintilação entre dois objetos de jogo à medida que eles *lutarem* pelo mesmo valor de profundidade z. Isso pode ser resolvido alternando para o formato de profundidade de 24 bits, pois haverá um intervalo maior de valores para cada objeto a ser calculado para a profundidade z da câmera.
>
> No entanto, é recomendável, especialmente para o desenvolvimento de HoloLens, modificar os planos próximos e distantes da câmera para um intervalo menor, em vez disso, manter o formato de profundidade de 16 bits. A profundidade z é mapeada de forma não linear para o intervalo de valores nos planos de câmera próximos e distantes. Isso pode ser modificado selecionando a *câmera principal* em sua cena e, em **Inspetor**, alterar os valores de **plano de recorte próximo & longe** para reduzir seu intervalo (ou seja, de 1000m para 100 ms ou outro valor x, etc.)

>[!IMPORTANT]
> [O Unity não cria um buffer de estêncil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) ao usar o formato de profundidade de 16 bits. Assim, alguns efeitos de interface do usuário do Unity e outros efeitos requeridos pelo estêncil não funcionarão a menos que o formato de profundidade de 24 bits esteja selecionado, o que criará um [buffer de estêncil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html).

### <a name="building-for-il2cpp"></a>Compilando para IL2CPP

O Unity preteriu o suporte para o back-end de script do .NET e, portanto, recomenda que os desenvolvedores utilizem o **IL2CPP** para suas compilações do Visual Studio UWP. Embora isso traga várias vantagens, a criação de sua solução do Visual Studio a partir do Unity para **Il2CPP** pode ser significativamente mais lenta do que o antigo método .net. Portanto, é altamente recomendável seguir as práticas recomendadas para a criação de **IL2CPP** para economizar em tempo de iteração de desenvolvimento.

1) Aproveite a criação incremental criando seu projeto no mesmo diretório a cada vez, reutilizando os arquivos predefinidos ali
2) Desabilitar verificações de software antimalware para seu projeto & criar pastas
   - Abra o **vírus & proteção contra ameaças** em seu aplicativo de configurações do Windows 10
   - Selecione **gerenciar configurações** em **vírus & ameaças proteção configurações**
   - Selecione **Adicionar ou remover exclusões** na seção **exclusões**
   - Clique em **Adicionar uma exclusão** e selecione a pasta que contém o código do projeto de Unity e as saídas de compilação
3) Utilizar um SSD para compilação

Leia [otimizando os tempos de compilação para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obter mais informações.

> [!NOTE]
> Além disso, pode ser benéfico configurar um [Servidor de Cache](https://docs.unity3d.com/Manual/CacheServer.html), especialmente para projetos do Unity com uma grande quantidade de ativos (excluindo arquivos de script) ou que estejam constantemente alterando cenas/ativos. Ao abrir um projeto, o Unity armazena os ativos qualificados em um formato de cache interno no computador do desenvolvedor. Os itens precisam ser importados novamente e, assim, processados novamente quando modificados. Esse processo pode ser feito uma vez e salvo em um Servidor de Cache e, consequentemente, compartilhado com outros desenvolvedores para economizar tempo, em vez de todos os desenvolvedores processarem a nova importação de novas alterações localmente.

## <a name="publishing-properties"></a>Propriedades de publicação

### <a name="holographic-splash-screen"></a>Tela inicial do Holographic

O HoloLens tem uma CPU e uma GPU de classe móvel, o que significa que os aplicativos podem demorar um pouco mais para carregar. Enquanto o aplicativo estiver sendo carregado, os usuários verão apenas preto e, portanto, poderão imaginar o que está acontecendo. Para assegurá-los durante o carregamento, você pode adicionar uma tela inicial do Holographic.

Para alternar a tela inicial do Holographic:

1) Vá para **Editar** **configurações do projeto** > página > **Player**
2) Clique na guia **Windows Store** e abra a seção **imagem de abertura**
3) Aplique a imagem desejada na propriedade **imagem de abertura do Windows Holographic > Holographic** .
    - Alternar a opção **Mostrar tela inicial do Unity** habilitará ou desabilitará a tela inicial com marca do Unity. Se você não tiver uma licença do Unity pro, a tela inicial da marca do Unity será sempre exibida.
    - Se uma **imagem de abertura do Holographic** for aplicada, ela sempre será exibida, independentemente de a caixa de seleção Mostrar tela inicial do Unity estar habilitada ou desabilitada. A especificação de uma imagem de abertura Holographic personalizada só está disponível para desenvolvedores com licença do Unity pro.

|  Mostrar tela inicial do Unity  |  Imagem de abertura do Holographic  |  Comportamento |
|----------|----------|----------|
|  Ativado  |  Nenhum  |  Mostre a tela inicial do Unity padrão por 5 segundos ou até que o aplicativo seja carregado, o que for maior. |
|  Ativado  |  Personalizado  |  Mostre a tela inicial personalizada por 5 segundos ou até que o aplicativo seja carregado, o que for maior. |
|  Desativar  |  Nenhum  |  Mostrar preto transparente (Nothing) até que o aplicativo seja carregado. |
|  Desativar  |  Personalizado  |  Mostre a tela inicial personalizada por 5 segundos ou até que o aplicativo seja carregado, o que for maior. |

Leia a [documentação da tela inicial do Unity](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) para obter mais informações.

### <a name="tracking-loss"></a>Perda de rastreamento

Um headset de realidade misturada depende da visualização do ambiente em relação a ele para construir [sistemas de coordenadas com bloqueio mundial](coordinate-systems-in-unity.md), que permitem que os hologramas permaneçam em posição. Quando o headset não consegue se localizar no mundo, diz-se que o fone de ouvido é considerado *perdido*. Nesses casos, a funcionalidade dependente de sistemas de coordenadas bloqueados pelo mundo, como estágios espaciais, âncoras espaciais e mapeamento espacial, não funciona.

Se ocorrer uma perda de controle, o comportamento padrão do Unity será parar de renderizar os hologramas, pausar o [loop do jogo](https://docs.unity3d.com/Manual/ExecutionOrder.html)e exibir uma notificação de rastreamento perdido que siga confortavelmente os usuários olhar. As notificações personalizadas também podem ser fornecidas na forma de uma imagem de perda de rastreamento. Para aplicativos que dependem do acompanhamento de toda a sua experiência, é suficiente deixar que o Unity manipule isso totalmente até que o rastreamento seja readquirido. Os desenvolvedores podem fornecer uma imagem personalizada a ser mostrada durante a perda de controle.

Para personalizar a imagem perdida de rastreamento:

1) Vá para **Editar** **configurações do projeto** > página > **Player**
2) Clique na guia **Windows Store** e abra a seção **imagem de abertura**
3) Aplique a imagem desejada na propriedade de **imagem de perda de > do Windows Holographic de rastreamento** .

#### <a name="opt-out-of-automatic-pause"></a>Recusa de pausa automática

Alguns aplicativos podem não exigir acompanhamento (por exemplo, [aplicativos somente de orientação](coordinate-systems-in-unity.md) , como visualizadores de vídeo de 360 graus) ou talvez precisem continuar o processamento ininterrupto enquanto o rastreamento é perdido. Nesses casos, os aplicativos podem recusar a perda padrão de comportamento de controle. Os desenvolvedores que escolhem isso são responsáveis por ocultar/desabilitar todos os objetos que não são renderizados corretamente em um cenário de perda de rastreamento. Na maioria dos casos, o único conteúdo que é recomendado para ser renderizado nesse caso é o conteúdo de corpo bloqueado, centralizado em toda a câmera principal.

Para recusar o comportamento de pausa automática:

1) Vá para a **Edit** página Editar **configurações do projeto** >  > **Player**
2) Clique na guia **Windows Store** e abra a seção **imagem de abertura**
3) Modifique a caixa de seleção **> do Windows Holographic na pausa de controle de perda e mostrar imagem** .

#### <a name="tracking-loss-events"></a>Rastreando eventos de perda

Para definir o comportamento personalizado quando o rastreamento é perdido, manipule os [eventos de perda de controle](tracking-loss-in-unity.md)global.

### <a name="capabilities"></a>{1&gt;Capabilities&lt;1}

Para que um aplicativo aproveite determinadas funcionalidades, ele deve declarar os recursos apropriados em seu manifesto. As declarações de manifesto podem ser feitas no Unity para que elas sejam incluídas em todas as exportações de projeto subsequentes.

Os recursos podem ser habilitados para um aplicativo de realidade misturada:

1) Vá para **Editar** **configurações do projeto** > página > **Player**
2) Clique na guia **Windows Store** , abra a seção **configurações de publicação** e procure a lista de **recursos**

Os recursos aplicáveis para habilitar as APIs comumente usadas para aplicativos Holographic são:
<br>

|  Capability  |  APIs que exigem capacidade |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  Integrada  |  VideoCapture e fotocaptura |
|  PicturesLibrary / VideosLibrary  |  VideoCapture, respectivamente (ao armazenar o conteúdo capturado) |
|  Microfone  |  VideoCapture (ao capturar áudio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer |
|  InternetClient  |  DictationRecognizer (e para usar o criador de perfil do Unity) |

## <a name="see-also"></a>Consulte também

* [Visão geral do desenvolvimento do Unity](unity-development-overview.md)
* [Noções básicas sobre o desempenho da Realidade Misturada](understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
