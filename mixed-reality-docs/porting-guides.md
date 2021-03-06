---
title: Guias de portabilidade
description: Uma explicação passo a passo explicando como portar um aplicativo de imersão existente para a realidade mista do Windows.
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: porta, portabilidade, Unity, middleware, mecanismo, UWP, Win32
ms.openlocfilehash: ed6c613c8aa3649cffb42d08dbb18661f06b9a53
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476928"
---
# <a name="porting-guides"></a>Guias de portabilidade

## <a name="overview"></a>Visão geral

O Windows 10 inclui suporte direto para headsets de imersão e Holographic. Se você tiver criado conteúdo para outros dispositivos, como o Oculus Rift ou o HTC Naopak, eles têm dependências em bibliotecas que existem acima da API de plataforma do sistema operacional. A disponibilização de aplicativos existentes do Win32 Unity VR para a realidade mista do Windows envolve o redirecionamento do uso de SDKs de VR específicos do fornecedor para as APIs VR entre fornecedores do Unity.


## <a name="porting-overview"></a>Visão geral de portabilidade

Em um alto nível, as etapas a seguir estão envolvidas na portabilidade de conteúdo existente:
1. **Verifique se o PC está executando a atualização dos criadores de outono do Windows 10 (16299).** Não é mais recomendável receber compilações prévias do anel do insider skip ahead, pois essas compilações não serão as mais estáveis para o desenvolvimento de realidade misturada.
2. **Atualize para a versão mais recente do seu mecanismo de gráficos ou jogos.** Os mecanismos de jogo precisarão dar suporte à versão 10.0.15063.0 do SDK do Windows 10 (lançado em abril de 2017) ou superior.
3. **Atualize qualquer middleware, plug-ins ou componentes.** Se seu aplicativo contiver qualquer componente, é uma boa ideia atualizar para a versão mais recente.
4. **Remova dependências em SDKs duplicados**. Dependendo de qual dispositivo o seu conteúdo foi direcionado, você precisará remover ou compilar condicionalmente esse SDK (por exemplo, SteamVR) para que você possa direcionar as APIs do Windows em vez disso.
5. **Trabalhe com problemas de compilação.** Neste ponto, o exercício de portabilidade é específico para seu aplicativo, seu mecanismo e as dependências de componente que você tem.

## <a name="common-porting-steps"></a>Etapas de portabilidade comuns

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>Etapa comum 1: Verifique se você tem o hardware de desenvolvimento correto

A página [instalar as ferramentas](install-the-tools.md#immersive-vr-headset-requirements) lista o hardware de desenvolvimento recomendado.

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>Etapa comum 2: atualizar para o vôo mais recente do Windows 10

A plataforma Windows Mixed Reality ainda está em desenvolvimento ativo. Recomendamos que você [ingresse no programa Windows Insider](https://insider.windows.com/) para acessar o vôo "Windows Insider Fast".
1. Instalar a [atualização do Windows 10 para criadores](https://www.microsoft.com/software-download/windows10)
2. [Junte](https://insider.windows.com/) -se ao programa Windows Insider.
3. Habilitar [modo de desenvolvedor](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. Alterne para o [Fast do Windows Insider](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) por meio **das configurações > seção atualização & segurança**

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio"></a>Etapa comum 3: atualizar para a compilação mais recente do Visual Studio
* Se você estiver usando o Visual Studio, atualize para a compilação mais recente
* Consulte [instalar a página de ferramentas](install-the-tools.md#installation-checklist) no Visual Studio 2019

### <a name="common-step-4-choose-the-correct-adapter"></a>Etapa comum 4: escolha o adaptador correto
* Em sistemas como notebooks com duas GPUs, [direcione o adaptador correto](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Isso se aplica aos aplicativos do Unity e do DirectX nativo, em que um ID3D11Device é criado, explícita ou implicitamente (Media Foundation), para sua funcionalidade.

## <a name="unity-porting-guidance"></a>Diretrizes de portabilidade do Unity

### <a name="unity-step-1-review-the-common-porting-steps-listed-above"></a>Etapa 1 do Unity: examinar as etapas de portabilidade comuns listadas acima

Examine as etapas comuns listadas acima para verificar se o ambiente de desenvolvimento está configurado corretamente. Na etapa #3, se você estiver usando o Visual Studio, deverá selecionar o **desenvolvimento do jogo com** a carga de trabalho do Unity. Você pode cancelar a seleção do componente "editor do Unity opcional", já que você instalará uma versão mais recente do Unity na próxima etapa.

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Etapa 2 do Unity: atualizar para a compilação pública mais recente do Unity com o suporte do Windows Sr
1. Baixe a [compilação pública mais recente recomendada do Unity](install-the-tools.md) com suporte misto à realidade.
2. Salve uma cópia do seu projeto antes de começar
3. Examine a [documentação](https://docs.unity3d.com/Manual/UpgradeGuides.html) disponível no Unity em atualizando se seu projeto foi criado em uma versão mais antiga do Unity.
4. Siga as [instruções](https://docs.unity3d.com/Manual/APIUpdater.html) no site do Unity para usar o atualizador automático de API
5. Verifique e veja se há alterações adicionais que você precisa fazer para que seu projeto seja executado e trabalhe com quaisquer erros e avisos restantes. 

> [!Note] 
> Se você tiver um middleware do qual depende, verifique se está usando a versão mais recente (mais detalhes na etapa 3 abaixo).

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Etapa 3 do Unity: atualizar seu middleware para as versões mais recentes

Com qualquer atualização do Unity, há uma boa chance de que você precise atualizar um ou mais pacotes de middleware dos quais seu jogo ou aplicativo depende. Além disso, estar atualizado com o middleware mais recente aumenta a probabilidade de sucesso ao longo do restante do processo de portabilidade.

### <a name="unity-step-4-target-your-application-to-run-on-win32"></a>Etapa 4 do Unity: direcionar seu aplicativo para ser executado no Win32

De dentro de seu aplicativo de Unity:

* Navegue até arquivo-> configurações de compilação
* Selecione "PC, Mac, Linux autônomo"
* Definir plataforma de destino como "Windows"
* Defina a arquitetura como "x86" selecione "alternar plataforma"

> [!NOTE] 
> Se seu aplicativo tiver quaisquer dependências de serviços específicos do dispositivo, como a realização de correspondência do fluxo, você precisará desabilitá-los nesta etapa. Você pode conectar-se aos serviços equivalentes que o Windows fornece posteriormente.

### <a name="unity-step-5-setup-your-windows-mixed-reality-hardware"></a>Etapa 5: configurar seu hardware do Windows Mixed Reality
1. Examinar as etapas na [configuração do headset de imersão](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Saiba como [usar o simulador de realidade do Windows Mixed](using-the-windows-mixed-reality-simulator.md) e [navegar na página inicial do Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-6-target-your-application-to-run-on-windows-mixed-reality"></a>Etapa 6 do Unity: direcionar seu aplicativo para ser executado no Windows Mixed Reality
1. Primeiro, você deve remover ou compilar condicionalmente qualquer outro suporte de biblioteca específico para um determinado SDK do VR. Esses ativos freqüentemente alteram as configurações e propriedades em seu projeto de maneiras incompatíveis com outros SDKs de VR, como a realidade mista do Windows.
    * Por exemplo, se o seu projeto fizer referência ao SDK do SteamVR, você precisará atualizar seu projeto para usar as APIs comuns de VR do Unity que dão suporte tanto ao Windows Mixed Reality quanto ao SteamVR.
    * Etapas específicas para excluir condicionalmente outros SDKs de VR serão disponibilizadas em breve.
2. Em seu projeto do Unity, [direcione o SDK do Windows 10](holograms-100.md#target-windows-10-sdk)
3. Para cada cena, [Configure a câmera](holograms-100.md#chapter-2---setup-the-camera)

### <a name="unity-step-7-use-the-stage-to-place-content-on-the-floor"></a>Etapa 7 do Unity: usar o estágio para posicionar o conteúdo no chão

Você pode criar experiências de realidade misturadas em uma ampla variedade de [escalas de experiência](coordinate-systems.md).

Se você estiver portando uma **experiência de escala em**posição, deverá garantir que o Unity esteja definido para o tipo de espaço de rastreamento **estacionário** :

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Este código acima define o sistema de coordenadas mundiais do Unity para acompanhar o [quadro de referência estacionário](coordinate-systems.md#spatial-coordinate-systems). No modo de rastreamento estacionário, o conteúdo colocado no editor apenas na frente do local padrão da câmera (Forward is-Z) aparece na frente do usuário quando o aplicativo é iniciado. Para recentralizar a origem colocada do usuário, você pode chamar o XR da Unity [. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) .

Se você estiver portando uma experiência de **escala em pé** ou uma **experiência em escala de sala**, colocará o conteúdo em relação ao chão. Você se deparar com o andar do usuário usando o **[estágio espacial](coordinate-systems.md#spatial-coordinate-systems)**, que representa a origem definida do nível de chão do usuário e o limite de sala opcional, configurado durante a primeira execução. Para essas experiências, você deve garantir que o Unity esteja definido como o tipo de espaço de rastreamento **RoomScale** . Embora RoomScale seja o padrão, você desejará defini-lo explicitamente e garantir que você se torne verdadeiro, para detectar situações em que o usuário moveu o computador para fora da sala que eles calibraram:

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

Depois que o aplicativo definir o tipo de espaço de acompanhamento RoomScale com êxito, o conteúdo colocado no plano y = 0 aparecerá no chão. A origem em (0, 0) será o local específico no andar em que o usuário se baseou durante a configuração da sala, com-Z representando a direção de encaminhamento que ele estava enfrentando durante a instalação.

No código de script, você pode chamar o método TryGetGeometry em você é o tipo UnityEngine. experimental. XR. limite para obter um polígono de limite, especificando um tipo de limite de TrackedArea. Se o usuário definiu um limite (você obtém uma lista de vértices), é seguro fornecer uma **experiência de escala de sala** ao usuário, na qual eles podem percorrer a cena que você criar.

O sistema irá renderizar automaticamente o limite quando o usuário o aproximar. Seu aplicativo não precisa usar este polígono para renderizar o limite em si.

Para obter mais informações, consulte a página [coordenar sistemas no Unity](coordinate-systems-in-unity.md) .

Alguns aplicativos usam um retângulo para restringir sua interação. A recuperação do maior retângulo inscrito não tem suporte direto na API ou no Unity da UWP. O código de exemplo vinculado a abaixo mostra como localizar um retângulo dentro dos limites rastreados. Ele é baseado em heurística, portanto, pode não encontrar a solução ideal, no entanto, os resultados são consistentes com as expectativas. Os parâmetros no algoritmo podem ser ajustados para encontrar resultados mais precisos no custo do tempo de processamento. O algoritmo está em uma bifurcação do kit de ferramentas da realidade misturada que usa a versão 5,6 Preview MRTP do Unity. Isso não está disponível publicamente. O código deve ser diretamente utilizável em versões 2017,2 e superiores do Unity. O código será transportado para o MRTK atual em um futuro próximo.

[arquivo zip de código no GitHub](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20) Arquivos importantes:
* Ativos/HoloToolkit/estágio/scripts/Estágiomanager. cs-exemplo de uso
* Assets/HoloToolkit/Stage/scripts/LargestRectangle. cs-implementação do algoritmo
* Assets/HoloToolkit-UnitTests/editor/Stage/LargestRectangleTest. cs – teste trivial do algoritmo

Exemplo de resultados:

![Exemplo de resultados](images/largestrectangle-400px.jpg)

O algoritmo se baseia em um blog por Daniel Smilkov: [retângulo maior em um polígono](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="unity-step-8-work-through-your-input-model"></a>Etapa 8 do Unity: trabalhar com seu modelo de entrada

Cada jogo ou aplicativo direcionado a um HMD existente terá um conjunto de entradas que ele manipula, tipos de entradas que ele precisa para a experiência e APIs específicas que ele chama para obter essas entradas. Investimos na tentativa de torná-lo tão simples e direto possível de aproveitar as informações disponíveis no Windows Mixed Reality.
1. Leia o **[Guia de porta de entrada do Unity](input-porting-guide-for-unity.md)** para obter detalhes de como a realidade mista do Windows expõe a entrada e como isso é mapeado para o que seu aplicativo pode fazer hoje.
2. Escolha se você vai aproveitar a API de entrada Cross-VR-SDK do Unity ou a API de entrada específica do MR. As APIs Input. getbutton/Input. getaxis geral são usadas pelos aplicativos do Unity VR hoje para [entrada Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) e [entrada OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html). Se seus aplicativos já estiverem usando essas APIs para controladores de movimento, esse é o caminho mais fácil: você deve apenas precisar remapear os botões e eixos no Gerenciador de entrada.
    * Você pode acessar os dados do controlador de movimento no Unity usando as APIs gerais entre as duas entradas do SDK entre as informações. getbutton/Input. getaxis ou as APIs UnityEngine. XR. WSA. de entrada específicas do Sr. (anteriormente no namespace UnityEngine. XR. WSA. Input no Unity 5,6)
    * Consulte o [exemplo no Toolkit](https://github.com/Microsoft/HoloToolkit-Unity/pull/572) que combina controladores de gamepad e de movimento.

### <a name="unity-step-9-performance-testing-and-tuning"></a>Etapa 9 do Unity: teste e ajuste de desempenho

A realidade mista do Windows estará disponível em uma ampla classe de dispositivos, desde PCs de jogos de ponta, até os principais PCs de mercado. Dependendo do mercado que você está direcionando, há uma diferença significativa nos orçamentos de computação e gráficos disponíveis para seu aplicativo. Durante esse exercício de portabilidade, você provavelmente está aproveitando um PC Premium e teve orçamentos de computação e gráficos significativos disponíveis para seu aplicativo. Se desejar disponibilizar seu aplicativo para um público mais amplo, você deverá testar e criar o perfil de seu aplicativo no [hardware representativo que deseja direcionar](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

O [Unity](https://docs.unity3d.com/Manual/Profiler.html) e o [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) incluem os infileres de desempenho e as diretrizes de publicação da [Microsoft](understanding-performance-for-mixed-reality.md) e da [Intel](https://software.intel.com/articles/vr-content-developer-guide) sobre a criação de perfil de desempenho e otimização. Há uma ampla discussão sobre o desempenho disponível em [noções básicas sobre o desempenho para realidade misturada](understanding-performance-for-mixed-reality.md). Além disso, há detalhes específicos para o Unity em [recomendações de desempenho para o Unity](performance-recommendations-for-unity.md).

## <a name="see-also"></a>Consulte também
* [Guia de portabilidade de entrada para Unity](input-porting-guide-for-unity.md)
* [Diretrizes mínimas de compatibilidade de hardware do PC do Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Entendendo o desempenho da realidade misturada](understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para o Unity](performance-recommendations-for-unity.md)
