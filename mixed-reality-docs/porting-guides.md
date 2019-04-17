---
title: Guias de portabilidade
description: Uma passo a passo explicações passo a passo explicando como portar um aplicativo de imersão existente para o Windows Mixed Reality.
author: ChimeraScorn
ms.author: cwhite
ms.date: 10/02/2018
ms.topic: article
keywords: porta, portabilidade, unity, middleware, mecanismo de UWP
ms.openlocfilehash: a4a8c78f1c45fd8e3b85a767d139bae9f67540e0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590008"
---
# <a name="porting-guides"></a>Guias de portabilidade

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).

Windows 10 inclui suporte para headsets envolventes e holográfica diretamente. Se você tiver compilado o conteúdo para outro dispositivo como o Oculus Rift ou Vive HTC, eles têm dependências em bibliotecas de que existem acima da API da plataforma do sistema operacional. Trazer o conteúdo existente para o Windows Mixed Reality envolve o uso de um desses outros SDKs para as APIs do Windows de redirecionamento. O [as APIs da plataforma Windows para realidade misturada](https://docs.microsoft.com/uwp/api/Windows.Perception) só funcionam no modelo de aplicativo de plataforma Universal do Windows (UWP). Portanto, se seu aplicativo já não foi criado para a UWP, portabilidade para UWP fará parte da experiência de portabilidade.

## <a name="porting-overview"></a>Visão geral de portabilidade

Em um alto nível, estas são as etapas envolvidas na portabilidade do conteúdo existente:
1. **Verifique se que seu computador está executando o do Windows 10 Fall Creators Update (16299).** Não recomendamos receber visualizar compilações do anel Insider Skip com antecedência, como as compilações não serão mais estável para desenvolvimento de realidade misturada.
2. **Atualize para a versão mais recente do seu gráfico ou mecanismo de jogo.** Mecanismos de jogos serão necessário dar suporte ao SDK do Windows 10 versão 10.0.15063.0 (lançado em abril de 2017) ou superior.
3. **Atualize qualquer middleware, plug-ins ou componentes.** Se seu aplicativo contiver todos os componentes, é uma boa ideia atualizar para a versão mais recente. Versões mais recentes de plug-ins mais comuns têm suporte para UWP.
4. **Remover dependências duplicadas SDKs**. Dependendo de qual dispositivo foi direcionamento de seu conteúdo, você precisará remover ou compilar condicionalmente fora desse SDK (por exemplo, SteamVR) para que você pode direcionar as APIs do Windows em vez disso.
5. **Trabalhar com problemas de compilação.** Neste ponto, o exercício de portabilidade é específico para seu aplicativo, o mecanismo e as dependências do componente que você tem.

## <a name="common-porting-steps"></a>Etapas comuns de portabilidade

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>Etapa 1 comum: Verifique se que você tem o hardware certo desenvolvimento

O [instalar as ferramentas](install-the-tools.md#for-immersive-vr-headset-development) página lista o hardware recomendado de desenvolvimento.

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>Etapa 2 comum: Atualizar para o voo mais recente do Windows 10

A plataforma Windows Mixed Reality ainda está em desenvolvimento ativo, e para ser mais eficiente, é recomendável estar em voo "Windows Insider Fast". Para ter acesso a voos de windows, você precisará [ingressar no programa do Windows Insider](https://insider.windows.com/).
1. Instalar o [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [Junte-se](https://insider.windows.com/) o programa do Windows Insider.
3. Habilitar [modo de desenvolvedor](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. Alterne para o [Windows Insider Fast voos](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) por meio das configurações--> atualização e a seção de segurança

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio"></a>Etapa 3 comum: Atualizar para o build mais recente do Visual Studio
* Consulte [instalar as ferramentas](install-the-tools.md#installation-checklist) página em Visual Studio 2017

### <a name="common-step-4-be-ready-for-the-store"></a>Etapa 4 comum: Esteja pronto para a Store
* Use [Kit de certificação de aplicativos do Windows](https://developer.microsoft.com/windows/develop/app-certification-kit) (também conhecido como WACK) antecipadamente e com frequência!
* Use [Portability Analyzer](https://docs.microsoft.com/dotnet/standard/portability-analyzer) ([baixar](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer))

### <a name="common-step-5-choose-the-correct-adapter"></a>Etapa 5 comum: Escolha o adaptador correto
* Em sistemas como blocos de anotações com dois GPUs, [direcionar o adaptador correto](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Isso se aplica a aplicativos do Unity, além disso para aplicativos nativos do DirectX, onde um ID3D11Device é criado, explicitamente ou implicitamente (Media Foundation) para sua funcionalidade.

## <a name="unity-porting-guidance"></a>Diretrizes de portabilidade do Unity

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Etapa 1 do Unity: Siga as etapas de portabilidade comuns

Siga todas as etapas comuns. Quando estiver na etapa 3 #, selecione a **desenvolvimento de jogos com Unity** carga de trabalho. Você pode desmarcar o componente opcional do Editor do Unity, pois você vai instalar uma versão mais recente do Unity das instruções abaixo.

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Etapa 2 do Unity: Atualizar para a última compilação pública do Unity com suporte do Windows MR
1. Baixe o versão mais recente [recomendado compilação pública do Unity](install-the-tools.md) com realidade misturada suporte.
2. Salvar uma cópia do seu projeto antes de começar
3. Examine os [documentação](https://docs.unity3d.com/Manual/UpgradeGuides.html) disponíveis do Unity na portabilidade.
4. Siga as [instruções](https://docs.unity3d.com/Manual/APIUpdater.html) no site do Unity para usar seu atualizador automático de API
5. Verificar se há alterações adicionais que você precisa fazer para obter o projeto em execução e trabalhar com os erros e avisos restantes. Observação: Se você tiver o middleware que dependem de você, você precisa atualizar esse middleware para começar a usar (para obter mais detalhes na etapa 3 abaixo).

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Etapa 3 do Unity: Atualizar seu middleware para as versões mais recentes

Com qualquer atualização do Unity, há uma boa chance de que você precisa para atualizar um ou mais pacotes de middleware que seu jogo ou aplicativo depende. Além disso, a versão mais recente de todos os seu middleware aumentará sua probabilidade de êxito em todo o restante do processo de portabilidade. Muitos pacotes de middleware recentemente adicionou suporte para plataforma Universal do Windows (UWP), e atualizar para as versões mais recentes lhe permitirão aproveitar esse trabalho.

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Etapa 4 do Unity: Direcionar seu aplicativo para execução na plataforma Universal do Windows (UWP)

Depois de instalar as ferramentas, você precisa obter seu aplicativo em execução como um aplicativo Windows Universal.
* Siga as [passo a passo passo a passo detalhado](https://unity3d.com/partners/microsoft/porting-guides) fornecidos pelo Unity. Observe que você deve permanecer com a versão mais recente LTS (qualquer versão 20xx.4) para o Windows MR.
* Para obter mais recursos de desenvolvimento de UWP, examine os [guia de desenvolvimento de jogos do Windows 10](https://docs.microsoft.com/windows/uwp/gaming/e2e).
* Observe que o Unity continua a melhorar o suporte de IL2CPP; IL2CPP faz algumas UWP portas significativamente mais fácil. Se estiver direcionando o .net de back-end de script no momento, você deve considerar a conversão para aproveitar o back-end IL2CPP em vez disso.

Observação: Se seu aplicativo tiver dependências em serviços específicos do dispositivo, como correspondência fazendo do fluxo, você precisará desabilitá-los nesta etapa. Em um momento posterior, você pode conectar a serviços equivalentes que Windows fornece.

### <a name="unity-step-5-deprecated"></a>Etapa 5 do Unity: (Preterido)

Etapa 5 não é mais necessária. Nós são deixá-lo aqui para que a indexação das etapas permanece o mesmo.

### <a name="unity-step-6-get-your-windows-mixed-reality-hardware-set-up"></a>Etapa 6 do Unity: Obter o hardware do Windows Mixed Reality configurar
1. Analise as etapas [instalação imersivo fone de ouvido](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Saiba mais sobre [usar o simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md) e [navegar a página inicial do Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Etapa 7 do Unity: Seu aplicativo em execução no Windows Mixed Reality de destino
1. Primeiro, você deve remover ou compilar condicionalmente-out de qualquer outro suporte de biblioteca específico a um determinado VR SDK. Esses ativos frequentemente alteram as configurações e propriedades em seu projeto de maneiras que são incompatíveis com outros SDKs VR, como o Windows Mixed Reality.
    * Por exemplo, se seu projeto referencia o SDK SteamVR, você precisará atualizar seu projeto para excluir esses pré-fabricados e chamadas de API de script ao exportar para o destino de compilação do Windows Store.
    * As etapas específicas para condicionalmente excluindo outros SDKs VR estará disponível em breve.
2. Em seu projeto do Unity, [SDK do Windows 10 de destino](holograms-100.md#target-windows-10-sdk)
3. Para cada cena [a câmera de instalação](holograms-100.md#chapter-2---setup-the-camera)

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Etapa 8 para Unity: Use o estágio para colocar o conteúdo no chão

Você pode criar experiências de realidade misturada em uma ampla variedade de [experiência escalas](coordinate-systems.md).

Se você estiver portando um **escala encaixado experiência**, você deve garantir a Unity é definido como o **estacionários** acompanhamento do tipo de espaço:

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Isso define o sistema de coordenadas de mundo do Unity para acompanhar as [quadro estacionário de referência](coordinate-systems.md#spatial-coordinate-systems). No modo de acompanhamento parado, o conteúdo é colocado no editor de apenas na frente do local de padrão da câmera (para frente é -Z) será exibido na frente do usuário quando o aplicativo for iniciado. Para centralizar novamente o usuário do encaixado origem, você pode chamar do Unity [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) método.

Se você estiver portando um **experiência de escala de pé** ou **experiência de escala de sala**, será colocando conteúdo em relação ao chão. Justificar o usuário floor usando o  **[estágio espacial](coordinate-systems.md#spatial-coordinate-systems)**, que representa o usuário definidas origem do nível do chão e limite de espaço opcional, definido durante a primeira execução. Para essas experiências, você deve assegurar Unity é definido como o **RoomScale** acompanhamento do tipo de espaço. Enquanto RoomScale é o padrão, convém defini-lo explicitamente e certifique-se de que você obtém de volta for true, para detectar situações em que o usuário tem afastadas seu computador na sala que eles calibrados:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

Depois que seu aplicativo com êxito define o RoomScale espaço tipo de controle, conteúdo colocado y = 0 plano aparecerá no chão. A origem (0, 0, 0) será o local específico no chão de onde o usuário resistiu durante a instalação da sala, com a -Z que representa a direção de avançada que estavam enfrentando durante a instalação.

No código de script, você pode, em seguida, chame o método TryGetGeometry você é do tipo de UnityEngine.Experimental.XR.Boundary para obter um polígono do limite, especificando um tipo de limite de TrackedArea. Se o usuário definido um limite (você obter uma lista de vértices), você sabe que é seguro fornecer um **experiência de escala de sala** para o usuário, onde eles podem orientá-lo ao redor do cenário criar.

Observe que o sistema automaticamente renderizará o limite quando o usuário se aproxima dela. Seu aplicativo não precisa usar este polígono para renderizar o limite em si.

Para obter mais detalhes, consulte o [sistemas de coordenadas no Unity](coordinate-systems-in-unity.md) página.

Alguns aplicativos usam um retângulo para restringir sua interação. Não há suporte diretamente ao recuperar o retângulo maior inscrito na API de UWP ou Unity. O código de exemplo vinculado a seguir mostra como localizar um retângulo dentro dos limites rastreados. É a heurística com base para que não pode encontrar a solução ideal, no entanto, os resultados sejam geralmente consistentes com as expectativas. Os parâmetros no algoritmo podem ser ajustados para encontrar resultados mais precisos às custas do tempo de processamento. O algoritmo é uma bifurcação do Toolkit realidade mista que usa a versão MRTP do Unity 5.6 a visualização. Isso não está disponível publicamente. O código deve ser diretamente utilizável nas versões do Unity 2017.2 e superiores. O código será ser movido para o MRTK atual em um futuro próximo.

[arquivo zip do código no GitHub](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20) arquivos importantes:
* Assets/HoloToolkit/Stage/Scripts/StageManager.cs - exemplo de uso
* Assets/HoloToolkit/Stage/Scripts/LargestRectangle.cs - implementação do algoritmo
* Assets/HoloToolkit-UnitTests/Editor/Stage/LargestRectangleTest.cs - teste trivial do algoritmo

Exemplo dos resultados:

![Exemplo dos resultados](images/largestrectangle-400px.jpg)

Algoritmo baseia-se em um blog por Daniel Smilkov: [Retângulo maior em um polígono](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="unity-step-9-work-through-your-input-model"></a>Etapa 9 para Unity: Trabalhar com seu modelo de entrada

Cada jogo ou aplicativo direcionado a um existente HMD terá um conjunto de entradas que ele manipula, tipos de entradas que ele precisa para a experiência e APIs específicas que ele chama para obter essas entradas. Investimos na tentativa de fazer do mais simples e direto quanto possível para tirar proveito das entradas disponíveis no Windows Mixed Reality.
1. Leia as **[entrada de portabilidade de guia para Unity](input-porting-guide-for-unity.md)** para obter detalhes de como o Windows Mixed Reality expõe entrada e como isso é mapeado para que seu aplicativo pode fazer hoje.
2. Escolha se você pretende aproveitar a API de entrada entre-VR-SDK do Unity ou API de entrada específicos do MR. As APIs de Input.GetButton/Input.GetAxis geral são usadas por aplicativos Unity VR hoje para [entrada Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) e [OpenVR entrada](https://docs.unity3d.com/Manual/OpenVRControllers.html). Se seus aplicativos já estão usando essas APIs para controladores de movimento, esse é o caminho mais fácil – você só precisa remapear botões e eixos no Gerenciador de entrada.
    * Você pode acessar dados do controlador de movimento no Unity usando geral entre-VR-SDK Input.GetButton/Input.GetAxis APIs ou o MR UnityEngine.XR.WSA.Input APIs específicas. (anteriormente no namespace UnityEngine.XR.WSA.Input no Unity 5.6)
    * Consulte a [exemplo no Kit de ferramentas](https://github.com/Microsoft/HoloToolkit-Unity/pull/572) que combina controladores gamepad e movimento.

### <a name="unity-step-10-performance-testing-and-tuning"></a>Etapa 10 do Unity: Teste de desempenho e ajuste

Realidade mista do Windows será estar disponíveis em uma ampla classe de dispositivos, variando de alta terminar PCs de jogos, até amplo mercado base PCs. Dependendo de quais no mercado de destino, há uma diferença significativa nos orçamentos de elementos gráficos e computação disponíveis para seu aplicativo. Durante este exercício de portabilidade, você provavelmente aproveitando um PC premium e que tenha tido significativos orçamentos de elementos gráficos e computação disponíveis ao seu aplicativo. Se você quiser disponibilizar seu aplicativo para um público mais amplo, você deve testar e analisar seu aplicativo no [o representante de hardware que você deseja destino](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Ambos [Unity](https://docs.unity3d.com/Manual/Profiler.html) e [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) incluem os criadores de perfil de desempenho e ambos [Microsoft](understanding-performance-for-mixed-reality.md) e [Intel](https://software.intel.com/articles/vr-content-developer-guide) diretrizes de publicação criação de perfil de desempenho e otimização. Uma discussão abrangente de desempenho está disponível em [Noções básicas sobre desempenho para realidade misturada](understanding-performance-for-mixed-reality.md). Além disso, há detalhes específicos para o Unity sob [recomendações de desempenho para o Unity](performance-recommendations-for-unity.md).

## <a name="see-also"></a>Consulte também
* [Entrada de portabilidade de guia para Unity](input-porting-guide-for-unity.md)
* [Diretrizes de compatibilidade de hardware do Windows Mixed Reality mínimas PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Noções básicas sobre desempenho para realidade misturada](understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
* [Adicionar suporte a Xbox Live para o Unity para UWP](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
