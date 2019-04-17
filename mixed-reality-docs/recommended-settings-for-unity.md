---
title: Configurações recomendadas para Unity
description: Unity oferece alguns comportamentos específicos para realidade misturada que pode ser alternada por meio das configurações de projeto.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: Unity, configurações, realidade mista
ms.openlocfilehash: a67c3a65819855be6d43941c05f9a0027abf2f6d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589603"
---
# <a name="recommended-settings-for-unity"></a>Configurações recomendadas para Unity

Unity fornece um conjunto de opções padrão que são geralmente o caso médio para todas as plataformas. No entanto, o Unity oferece alguns comportamentos específicos para realidade misturada que pode ser alternada por meio das configurações de projeto.

## <a name="performant-environment-set-up"></a>Configuração do ambiente de alto desempenho

### <a name="low-quality-setting"></a>Configuração de baixa qualidade

É importante modificar a **configurações de qualidade do Unity** para seu ambiente **"rápido"**. Isso ajudará a garantir que seu aplicativo está executando performantly na taxa de quadros apropriada. Isso é extremamente significativo para o desenvolvimento Hololens. Para o desenvolvimento em fones imersivos em exposição, dependendo das especificações da área de trabalho, capacitar a experiência VR, um ainda pode obter a taxa de quadros sem os parâmetros de qualidade mais baixas. 

No Unity 2018 LTS +, o nível de qualidade do projeto pode ser definido:

Sob **editar** > **configurações do projeto** > **qualidade** > definir a **padrão** clicando no seta para baixo para o **mais rápido** nível de qualidade

### <a name="single-pass-instancing-rendering-path"></a>Caminho de renderização instanciação única passagem

Em aplicativos de realidade misturada, a cena é renderizada duas vezes, uma vez para cada olho para o usuário. Em comparação com desenvolvimento 3D tradicional, isso efetivamente duas vezes a quantidade de trabalho que precisa ser calculado. Portanto, é importante selecionar o caminho de processamento mais eficiente no Unity para salvar ambos em tempo de CPU e GPU. Renderização de instância única passagem otimiza o pipeline de renderização do Unity para aplicativos de realidade mista e, portanto, é recomendável habilitar essa configuração por padrão para todos os projetos. 

Para habilitar esse recurso em seu projeto do Unity
1)  Abra **configurações do Player XR** (acesse **editar** > **configurações do projeto** > **Player**  >  **XR configurações**)
2) Selecione **instância única de passar** da **estéreo de método de renderização** menu suspenso (**suporte de realidade Virtual** caixa de seleção deve ser marcada)

Leia os seguintes artigos do Unity para obter mais detalhes com essa abordagem de renderização.
- [Como maximizar o desempenho de AR e VR com renderização estéreo avançada](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Instanciação de passagem única](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Um problema comum com a única passar instância renderização ocorre se os desenvolvedores têm já existente de sombreadores personalizados não escritos para criação de instância. Depois de habilitar esse recurso, os desenvolvedores podem perceber a renderização de apenas alguns GameObjects em um olho. Isso ocorre porque os sombreadores personalizados associados não tem as propriedades adequadas para criação de instância.
>
> Ver [único passar estéreo de renderização para HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) do Unity para resolver esse problema

### <a name="enable-depth-buffer-sharing"></a>Habilitar o compartilhamento de buffer de profundidade

Para obter uma melhor estabilidade holograma da percepção do usuário, é recomendável habilitar o **compartilhamento de Buffer de profundidade** propriedade no Unity. Ao ativar isso, o Unity compartilharão o mapa de profundidade produzido pelo seu aplicativo com a plataforma Windows Mixed Reality. A plataforma, em seguida, poderá otimizar melhor estabilidade holograma especificamente para sua cena para um determinado quadro que está sendo processado pelo seu aplicativo.

Para habilitar esse recurso em seu projeto do Unity
1) Abra **configurações do Player XR** (acesse **editar** > **configurações do projeto** > **Player**  >  **XR configurações**)
2) Selecione a caixa de seleção **ativar o compartilhamento de Buffer de profundidade** sob **SDKs de realidade Virtual** > **Windows Mixed Reality** expansão (**Virtual Suporte de realidade** caixa de seleção deve ser marcada)

Além disso, é recomendável selecionar **profundidade de 16 bits** sob o **formato profundidade** configuração neste painel, especialmente para desenvolvimento Hololens. Seleção de 16 bits em comparação com 24 bits reduzirá significativamente os requisitos de largura de banda conforme menos dados precisará ser movidos/processado.

>[!NOTE]
> Os desenvolvedores devem tenha cuidado com Z fighting ao alterar esses valores junto com as configurações de plano quase/distante da câmera. Z Fighting ocorre quando dois gameobjects tenta processar para o mesmo pixel e devido a limitações de fidelidade do buffer de profundidade (ou seja profundidade z), Unity não é possível distinguir qual objeto está na frente do outro. Os desenvolvedores observarão uma cintilação entre dois objetos de jogos como eles *lutar contra* para o mesmo valor de profundidade z. Isso pode ser resolvido ao alternar para o formato de 24 bits profundidade, haverá um intervalo maior de valores para cada objeto calcular após a sua profundidade de z da câmera.
>
> No entanto, é recomendável, particularmente para Hololens desenvolvimento, para modificar a câmera do próximo e muito planos para um intervalo menor, em vez disso e mantendo a profundidade de 16 bits de formato. A profundidade de z não linearmente é mapeada para o intervalo de valores ao longo da câmera próxima e distante planos. Isso pode ser modificado, selecionando o *câmera principal* na sua cena e, em **Inspetor**, altere a **plano de recorte próximo & muito** valores para reduzir seu intervalo (ou seja, de m 1000 para 100 MB ou outro valor de x, etc.)

### <a name="building-for-il2cpp"></a>Criando para IL2CPP

Unity preteriu o suporte para o .NET scripting back-end e, portanto, é recomendável que os desenvolvedores utilizam **IL2CPP** para seu UWP build do visual studio. Embora isso traz várias vantagens, criação de sua solução do visual studio do Unity para **Il2CPP** pode ser consideravelmente mais lento do que o método antigo de .NET. Portanto, é altamente recomendável seguir as práticas recomendadas para a compilação **IL2CPP** para economizar em tempo de iteração de desenvolvimento.

1) Compilação incremental aproveite criando seu projeto no mesmo diretório cada vez, novamente usando os arquivos pré-criados existe
2) Desabilitar verificações de software antimalware para seu projeto e criar pastas
   - Abra **proteção contra vírus e ameaças** em seu aplicativo de configurações do Windows 10
   - Selecione **gerenciar definições** sob **as configurações de proteção contra vírus e ameaças**
   - Selecione **adicionar ou remover exclusões** sob o **exclusões** seção
   - Clique em **adicione uma exclusão** e selecione a pasta contém o código do seu projeto Unity e criar saídas
3) Utilize um SSD para compilação

Leia [otimizando tempos de compilação para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obter mais informações.

## <a name="publishing-properties"></a>Propriedades de publicação

### <a name="holographic-splash-screen"></a>Tela inicial holográfica

HoloLens tem um CPU e GPU, o que significa que aplicativos podem demorar um pouco mais para carregar um classe móvel. Enquanto o aplicativo é carregado, os usuários verão apenas preto e assim eles deve estar imaginando o que está acontecendo. Para reforçá-los durante o carregamento, que você pode adicionar uma tela inicial holográfica.

Para ativar/desativar a tela inicial holográfica:
1) Vá para **edite** > **configurações do projeto** > **Player** página
2) Clique no **Windows Store** guia e abra o **imagem inicial** seção
3) Aplicar sua imagem desejada sob o **Windows Holographic > holográfica imagem de abertura** propriedade.
    - Ativar/desativar a **Mostrar tela de abertura do Unity** opção habilita ou desabilita a tela de marca de abertura do Unity. Se você não tiver uma licença Pro do Unity, o Unity da marca a tela inicial será sempre exibido.
    - Se um **holográfica imagem de abertura** é aplicado, ele será sempre exibido, independentemente se a caixa de seleção Mostrar tela de abertura do Unity está habilitada ou desabilitada. Especificar uma imagem personalizada de abertura de holográfica só está disponível para desenvolvedores com uma licença Pro do Unity.

|  Mostrar tela de abertura do Unity  |  Imagem holográfica inicial  |  Comportamento |
|----------|----------|----------|
|  Ativado  |  Nenhuma  |  Mostre a tela inicial padrão do Unity por 5 segundos ou até que o aplicativo for carregado, o que for maior. | 
|  Ativado  |  Personalizado  |  Mostre telas de abertura personalizadas por 5 segundos ou até que o aplicativo for carregado, o que for maior. | 
|  Desativado  |  Nenhuma  |  Mostra preto transparente (nothing) até que o aplicativo for carregado. | 
|  Desativado  |  Personalizado  |  Mostre telas de abertura personalizadas por 5 segundos ou até que o aplicativo for carregado, o que for maior. | 

Leia [documentação de tela de abertura do Unity](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) para obter mais informações.

### <a name="tracking-loss"></a>Perda de controle

Um headset de realidade misturada depende vendo o ambiente ao redor dele para construir [sistemas de coordenadas de mundo bloqueada](coordinate-systems-in-unity.md), que permitem que hologramas permaneça na posição. Quando o fone de ouvido não conseguir localizar-se no mundo, o fone de ouvido é considerado como tendo *perdido acompanhamento*. Nesses casos, funcionalidade dependente de sistemas de coordenadas bloqueado pelo mundo, como estágios espaciais, as âncoras espaciais e mapeamento espacial, não funcionam.

Se ocorrer uma perda de acompanhamento, comportamento de padrão do Unity é hologramas de renderização de parar, pausar a [loop do jogo](http://docs.unity3d.com/Manual/ExecutionOrder.html), e exibir um rastreamento perdido a notificação ou confortavelmente segue o olhar os usuários. Notificações personalizadas também podem ser fornecidas na forma de um controle de imagem de perda. Para aplicativos que dependem de acompanhamento para toda a sua experiência, é suficiente permitir que o Unity lidar com isso completamente até que é recuperado o rastreamento. Os desenvolvedores podem fornecer uma imagem personalizada a ser mostrado durante a perda de controle. 

Para personalizar a imagem perdidos de rastreamento:
1) Vá para **edite** > **configurações do projeto** > **Player** página
2) Clique no **Windows Store** guia e abra o **imagem inicial** seção
3) Aplicar sua imagem desejada sob o **Windows Holographic > imagem de perda de controle** propriedade.

#### <a name="opt-out-of-automatic-pause"></a>Recusa de pausa automática

Alguns aplicativos podem não exigir acompanhamento (por exemplo, [aplicativos somente orientação](coordinate-systems-in-unity.md) , como visualizadores de vídeos de 360 graus) ou talvez seja necessário continuar sem interrupções durante o rastreamento de processamento é perdido. Nesses casos, aplicativos podem recusar a perda de padrão de comportamento de acompanhamento. Os desenvolvedores que escolha esta opção são responsáveis por ocultando e desabilitação de todos os objetos que não seriam renderizados corretamente em um cenário de perda de acompanhamento. Na maioria dos casos, somente o conteúdo que é recomendado para ser renderizado nesse caso é bloqueado de corpo de conteúdo, centralizado em torno da câmera principal.

Para recusar o comportamento de pausa automática:
1) Vá para **edite** > **configurações do projeto** > **Player** página
2) Clique no **Windows Store** guia e abra o **imagem inicial** seção
3) Modificar a **Windows Holographic > em pausa de perda de controle e Mostrar imagem** caixa de seleção.

#### <a name="tracking-loss-events"></a>Perda de eventos de rastreamento

Para definir o comportamento personalizado quando o controle for perdido, manipular global [perda de eventos de rastreamento](tracking-loss-in-unity.md).

### <a name="capabilities"></a>Funcionalidades

Para um aplicativo aproveitar alguns recursos, ele deve declarar os recursos apropriados em seu manifesto. As declarações de manifesto podem ser feitas no Unity para que sejam incluídos em cada exportação projeto subsequente. 

Recursos podem ser habilitados para um aplicativo de realidade misturada por:
1) Vá para **edite** > **configurações do projeto** > **Player** página
2) Clique no **Windows Store** guia e abra o **configurações de publicação** seção e procure o **recursos** lista

Os recursos aplicáveis para habilitar as APIs usadas para aplicativos holográfica são:
<br>

|  Capacidade  |  APIs que exigem a capacidade |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver | 
|  WebCam  |  PhotoCapture e VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  PhotoCapture ou VideoCapture, respectivamente (ao armazenar o conteúdo capturado) | 
|  Microfone  |  VideoCapture (durante a captura de áudio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e usar o Profiler Unity) | 

## <a name="see-also"></a>Consulte também
* [Visão geral de desenvolvimento do Unity](unity-development-overview.md)
* [Desempenho Understaing para realidade misturada](understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)