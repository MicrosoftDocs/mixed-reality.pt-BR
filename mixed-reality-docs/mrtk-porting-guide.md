---
title: Como preparar o aplicativo para o HoloLens 2
description: Destinado a desenvolvedores que têm um aplicativo no HoloLens (1ª geração) e/ou no MRTK mais antigo e buscam compatibilizá-lo para o MRTK versão 2 e o HoloLens 2.
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, teste, MRTK, MRTK versão 2, HoloLens 2
ms.openlocfilehash: 307a20f14c9602fd84b25bdec481e9a6076c5e78
ms.sourcegitcommit: e5b677f92ac4b1dff9aad6c329345a5aca4fcef5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69020193"
---
# <a name="getting-your-existing-application-ready-for-hololens-2"></a>Como preparar o aplicativo existente para o HoloLens 2

Este guia foi projetado para ajudar os desenvolvedores que têm um aplicativo do Unity para HoloLens (1ª geração) a portá-lo para o dispositivo HoloLens 2. Há quatro etapas principais para portar um aplicativo do Unity do HoloLens (1ª geração) para o HoloLens 2. As seções abaixo fornecem informações detalhadas para cada estágio. 

| Etapa 1 | Etapa 2 | Etapa 3 | Etapa 4 |
|----------|-------------------|-------------------|-------------------|
| ![Logotipo do Visual Studio](images/visualstudio_logo.png) | ![Logotipo do Unity](images/unity_logo.png)| ![Ícone do Unity](images/hololens2_icon.jpg) | ![Logotipo do MRTK](images/MRTKIcon.jpg) |
| Baixar as ferramentas mais recentes | Atualizar o projeto do Unity | Compilar para o ARM | Migrar para o MRTK v2

É **altamente recomendado** que, antes de iniciar o processo de portabilidade, os desenvolvedores usem o controle do código-fonte para salvar um instantâneo do estado original de seus aplicativos. Além disso, é recomendável *salvar* os estados de ponto de verificação em vários pontos durante o processo. Também pode ser muito útil ter outra instância do Unity do aplicativo original para permitir a comparação lado a lado durante o processo de portabilidade. 

> [!NOTE]
> Antes da portabilidade, verifique se você tem as ferramentas mais recentes instaladas para o desenvolvimento do Windows Mixed Reality. Para a maioria dos desenvolvedores existentes do HoloLens, isso envolverá principalmente a atualização para a versão mais recente do Visual Studio 2019 e a instalação do SDK do Windows apropriado. O conteúdo abaixo se aprofunda ainda mais em diferentes versões do Unity e no MRTK (Kit de ferramentas de realidade misturada) versão 2.
>
> Para obter mais informações, confira [Instalar as ferramentas](install-the-tools.md).

## <a name="migrate-project-to-latest-version-of-unity"></a>Migrar o projeto para a última versão do Unity

Se você estiver usando o [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), o [Unity 2018 LTS](https://unity3d.com/unity/qa/lts-releases) será o melhor caminho de suporte de longo prazo sem alterações da falha no Unity ou no MRTK. Além disso, o MRTK v2 sempre garante o suporte para o Unity 2018 LTS, mas não necessariamente garante o suporte para cada iteração do Unity 2019.x. 

Para ajudar a esclarecer outras diferenças entre o [Unity 2018 LTS](https://unity3d.com/unity/qa/lts-releases) e o Unity 2019.1.x, o material a seguir descreve os prós e contras entre essas duas versões. A principal diferença entre as duas é a capacidade de compilar para ARM64 no Unity 2019. 

Os desenvolvedores devem avaliar as [dependências de plug-in](https://docs.unity3d.com/Manual/Plugins.html) que existem atualmente em seus projetos e se essas DLLs podem ser compiladas para o ARM64. Se um plug-in de dependência forte não puder ser criado para o ARM64, será necessário usar o Unity 2018 LTS.


| Unity 2018.4.x | Unity 2019.1 e posterior |
|----------|-------------------|
| Suporte de build do ARM32 | Suporte de build do ARM32 e do ARM64 |
| Versão estável de build LTS | Estabilidade de beta |
| [Back-end de script do .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *preterido* | [Back-end de script do .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *removido* |
| Rede UNET *preterida* | Rede UNET *preterida* |

## <a name="update-sceneproject-settings-in-unity"></a>Atualizar as configurações de cena/projeto no Unity

Depois de fazer a atualização para o [Unity 2018 LTS](https://unity3d.com/unity/qa/lts-releases) ou o Unity 2019 e posterior, é recomendável atualizar configurações específicas no Unity para obter melhores resultados no dispositivo. Essas configurações são descritas detalhadamente em **[Configurações recomendadas para o Unity](Recommended-settings-for-Unity.md)** .

Deve-se reiterar que o [back-end de script do .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) está sendo preterido no Unity 2018 e *removido* no Unity 2019. É altamente recomendável que os desenvolvedores mudem seu projeto para [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). 

> [!NOTE]
> O back-end de script do IL2CPP pode causar tempos de build mais longos do Unity para o Visual Studio e, portanto, os desenvolvedores devem configurar seus computadores de desenvolvedor para [otimização dos tempos de build do IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).
> Além disso, também pode ser benéfico configurar um [Servidor de Cache](https://docs.unity3d.com/Manual/CacheServer.html), especialmente para projetos do Unity com uma grande quantidade de ativos (excluindo arquivos de script) ou que estejam constantemente alterando cenas e ativos. Ao abrir um projeto, o Unity armazena os ativos qualificados em um formato de cache interno no computador do desenvolvedor. Os itens precisam ser importados novamente e processados novamente quando modificados. Esse processo pode ser feito uma vez e salvo em um servidor de cache e, consequentemente, compartilhado com outros desenvolvedores para economizar tempo, em vez de todos os desenvolvedores processarem a nova importação de novas alterações localmente.

Depois de lidar com as alterações da falha após a migração para a versão atualizada do Unity, os desenvolvedores deverão criar e testar os aplicativos atuais no HoloLens (1ª geração). Esse é um bom momento para criar e salvar uma confirmação no controle do código-fonte. 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Compilar dependências/plug-ins para o processador ARM

O HoloLens (1ª geração) executa aplicativos em um processador x86, enquanto o HoloLens 2 usa um processador ARM. Portanto, é necessário portar os aplicativos HoloLens existentes para que eles deem suporte ao ARM. Conforme indicado anteriormente, o Unity 2018 LTS é compatível com a compilação de aplicativos ARM32, enquanto o Unity 2019.x é compatível com a compilação de aplicativos ARM64. Em geral, o desenvolvimento para aplicativos ARM64 é preferível, pois há uma diferença substancial de desempenho. No entanto, isso exige que todas as [dependências de plug-in](https://docs.unity3d.com/Manual/Plugins.html) também sejam compiladas para o ARM64. 

Examine todas as dependências de DLL em seu aplicativo. Se uma dependência não for mais necessária, será recomendável removê-la do projeto. Para os plug-ins restantes que são necessários, ingira os respectivos binários do ARM32 ou do ARM64 no projeto do Unity. 

Após a ingestão das DLLs relevantes, compile uma solução do Visual Studio por meio do Unity e, em seguida, compile um AppX para ARM no Visual Studio para testar se o aplicativo pode ser compilado para processadores ARM. É recomendável salvar o aplicativo como uma confirmação na solução de controle do código-fonte. 

## <a name="update-to-mrtk-version-2"></a>Atualizar para o MRTK versão 2

O [MRTK versão 2](https://github.com/microsoft/MixedRealityToolkit-Unity) é o novo kit de ferramentas baseado no Unity que dá suporte ao HoloLens (1ª geração) e ao HoloLens 2 e no qual todas as novas funcionalidades do HoloLens 2, tais como interações com as mãos e acompanhamento ocular, foram adicionadas.

Leia o seguinte para obter mais informações sobre como usar o MRTK versão 2:
- [Página de aterrissagem do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
- [Introdução ao MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
- [Mãos do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSystem/HandTracking.html)
- [Acompanhamento ocular do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

### <a name="prepare-for-the-migration"></a>Preparar a migração

Antes da ingestão dos novos arquivos [*.unitypackage para o MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), é recomendável fazer um inventário de **1) qualquer código personalizado integrado ao MRTK v1** e **2) qualquer código personalizado para interações de entrada ou componentes de experiência do usuário**. O conflito mais comum e predominante para um desenvolvedor de realidade misturada que ingere o MRTK v2 envolve a entrada e as interações. É recomendável começar a ler e entender o [modelo de entrada do MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html).

Por fim, o novo [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) fez a transição de um modelo de scripts e objetos de gerenciador na cena para uma configuração e uma arquitetura de provedor de serviços. Isso resulta em um modelo de arquitetura e hierarquia de cena mais limpo, mas exige uma curva de aprendizado para entender os novos perfis de configuração. Portanto, leia o [Guia de Configuração do Kit de Ferramentas de Realidade Misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) para começar a se familiarizar com os perfis e as configurações importantes para se ajustar às necessidades de seu aplicativo. 

### <a name="perform-the-migration"></a>Realizar a migração

Depois de importar o [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), seu projeto do Unity provavelmente terá muitos erros relacionados ao compilador. Esses se devem comumente à nova estrutura de namespace e aos novos nomes de componentes. Resolva esses erros modificando os scripts para os novos namespaces e componentes. 

Para obter mais informações sobre as diferenças de API específicas entre o HTK/o MRTK e o MRTK versão 2, confira o guia de portabilidade no [wiki do MRTK versão 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html).

### <a name="best-practices"></a>Práticas recomendadas

- Prefira o uso do [sombreador padrão do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html).
- Trabalhe em um tipo de alteração da falha por vez (por exemplo: IFocusable para [IMixedRealityFocusHandler](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler.html)).
- Faça um teste após cada alteração e use o controle do código-fonte.
- Use a experiência do usuário padrão do MRTK (botões, slates etc.) quando possível.
- Evite modificar os arquivos do MRTK diretamente; em vez disso, crie wrappers em torno de componentes do MRTK.
    - Isso protege contra futuras ingestões e atualizações do MRTK.
- Examine e explore cenas de exemplo fornecidas no MRTK, especialmente *HandInteractionExamples.scene*.
- Recompile a interface do usuário baseada em tela com quadrantes, colisores e texto do TextMeshPro.
- Habilite o [Compartilhamento de buffer de profundidade](camera-in-unity.md#sharing-your-depth-buffers-with-windows) e/ou [defina o ponto de foco](focus-point-in-unity.md); use um buffer de profundidade de 16 bits para ter melhor desempenho. Verifique se, ao renderizar a cor, você também renderiza a profundidade. O Unity geralmente não grava profundidade para gameobjects de texto e transparentes. 
- Defina o caminho de renderização instanciado de passagem única.
- Usar o [perfil de configuração do Hololens 2 para MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html#hololens-2-profile)

### <a name="testing-your-application"></a>Como testar seu aplicativo

Agora que os componentes e as funcionalidades do HoloLens 2 estão disponíveis no MRTK versão 2, do [RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1) em diante, você pode simular as interações com as mãos diretamente no Unity, bem como realizar o desenvolvimento com as novas APIs para interações com as mãos e acompanhamento ocular. O dispositivo HoloLens 2 é necessário para criar uma experiência de usuário satisfatória. Para adquirir uma melhor compreensão, é recomendável que você comece a estudar a documentação e as ferramentas. O [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) é compatível com o desenvolvimento no HoloLens (1ª geração) e, assim, os modelos de entrada tradicionais (tais como selecionar por meio do gesto de fechar e abrir dedos indicador e polegar) podem ser testados em HoloLens (1ª geração). 

## <a name="updating-your-interaction-model-for-hololens-2"></a>Como atualizar o modelo de interação para o HoloLens 2

Depois que o aplicativo for portado e preparado para o HoloLens 2, você estará pronto para considerar a atualização do modelo de interação e dos posicionamentos de design dos hologramas.
No HoloLens (1ª geração), o aplicativo provavelmente tem um modelo de interação de foco e confirmação com hologramas relativamente distantes para se ajustarem ao campo de visão.

Etapas para atualizar o design de seu aplicativo a fim de torná-lo mais adequado para o HoloLens 2:
1.  Componentes do MRTK: De acordo com o trabalho prévio, se você tiver adicionado o [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), haverá vários componentes/scripts a serem aproveitados que foram projetados e otimizados para o HoloLens 2.

2.  Modelo de interação: Considere a atualização do modelo de interação. Para a maioria dos cenários, recomendamos a alternância do foco e da confirmação com as mãos. Com os hologramas normalmente ficando fora do alcance dos braços, a alternância para as mãos resulta em raios de apontador de interação e gestos de segurar distantes.

3.  Posicionamento de hologramas: Depois de alternar para um modelo de interação com as mãos, considere a aproximação de alguns hologramas, a fim de interagir diretamente com eles com as mãos, usando gestos de segurar com interação próxima. Os tipos de hologramas recomendados para aproximação a fim de segurar ou interagir diretamente são menus de destino menores, controles, botões e hologramas menores que se ajustam ao campo de visão do HoloLens 2 ao segurar e inspecionar o holograma.
<br>
Cada aplicativo e cenário é diferente. Continuaremos refinando e postando diretrizes de design com base nos comentários e em aprendizados contínuos.


## <a name="additional-caveats-and-learnings-about-moving-applications-from-x86-to-arm"></a>Advertências e aprendizados adicionais sobre como mover aplicativos do x86 para o ARM

- Os aplicativos diretos do Unity são simples porque você pode criar um pacote de aplicativo ARM ou implantá-lo diretamente no dispositivo para que o pacote seja executado. Alguns plug-ins nativos do Unity podem apresentar certos desafios de desenvolvimento. Por isso, você deve atualizar todos os plug-ins nativos do Unity para o Visual Studio 2019 e, em seguida, recompilar para o ARM com o Unity 2019, ARM64.

- Um aplicativo usou o plug-in AudioKinetic Wwise para Unity e essa versão do Unity não tinha um plug-in de ARM do UWP, o que causou um esforço considerável recriando as funcionalidades de som do aplicativo em questão para que executassem no ARM. Verifique se todos os plug-ins necessários para os planos de desenvolvimento estão instalados e disponíveis no Unity.

- Em alguns casos, um plug-in do UWP/ARM pode não existir para os plug-ins requeridos pelo aplicativo, o que bloqueia a capacidade de portar o aplicativo e executá-lo no HoloLens 2. Entre em contato com seu provedor de plug-in para resolver o problema e fornecer suporte para o ARM.

- O minfloat (e variantes como min16float, minint etc.) em sombreadores pode se comportar de modo diferente no HoloLens (1ª geração) e no HoloLens 2. Especificamente, eles garantem que pelo menos o número especificado de bits seja usado. Em GPUs da Intel/NVIDIA, por exemplo, eles são apenas tratados como 32 bits. No ARM, o número de bits especificado é realmente respeitado. Isso significa que, na prática, esses números podem ter menos precisão ou alcance no HoloLens 2 do que tinham no HoloLens (1ª geração).

- As instruções de _asm não parecem funcionar no ARM, o que significa que qualquer código que use as instruções de _asm precisa ser reescrito.

- A instrução SIMD definida não é compatível com o ARM porque vários cabeçalhos, como xmmintrin.h, emmintrin.h, tmmintrin.h e immintrin.h, não estão disponíveis no ARM.

- O compilador de sombreador no ARM é executado durante a primeira chamada de desenho depois que o sombreador é carregado ou algo do qual o sombreador depende é alterado, não no tempo de carregamento do sombreador. O impacto na taxa de quadros pode ser perceptível, dependendo de quantos sombreadores precisam ser compilados. Isso tem várias implicações de como os sombreadores devem ser tratados, empacotados e atualizados de maneira diferente no HoloLens 2 em relação ao HoloLens (1ª geração).

## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* [Introdução ao MRTK versão 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [APIs do HTK para APIs do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
* [Configurações recomendadas do Unity](recommended-settings-for-unity.md)
* [Noções básicas sobre o desempenho da Realidade Misturada](understanding-performance-for-mixed-reality.md)

