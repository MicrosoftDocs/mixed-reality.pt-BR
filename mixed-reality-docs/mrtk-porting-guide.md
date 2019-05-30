---
title: Preparar seu aplicativo para o HoloLens 2
description: Destinado a desenvolvedores que têm um aplicativo existente no HoloLens (1º gen) e/ou mais antiga MRTK e procurando portar para MRTK versão 2 e HoloLens 2.
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, testar, MRTK, MRTK versão 2, 2 HoloLens
ms.openlocfilehash: 02dabd21b7a6add2ce53fe291a447e49057184d0
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270391"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>Preparar seu aplicativo existente para o HoloLens 2

Este guia especificamente projetado para ajudar os desenvolvedores que têm um aplicativo existente do Unity para HoloLens (1º gen) portar seu aplicativo para o novo dispositivo 2 HoloLens. Há quatro etapas principais para portar um HoloLens (1º gen) o aplicativo do Unity para HoloLens 2. As seções a seguir detalha informações para cada estágio. 

| Etapa 1 | Etapa 2 | Etapa 3 | Etapa 4 |
|----------|-------------------|-------------------|-------------------|
| ![Logotipo do Visual Studio](images/visualstudio_logo.png) | ![Logotipo do Unity](images/unity_logo.png)| ![Ícone do Unity](images/hololens2_icon.jpg) | ![Logotipo MRTK](images/MRTKIcon.jpg) |
| Baixe as ferramentas mais recentes | Atualizar o projeto do Unity | Compilar para ARM | Migrar para o MRTK v2

Vale **altamente recomendado** que, antes de iniciar o processo de portabilidade, os desenvolvedores utilizam o controle de origem para salvar um instantâneo do estado original do seu aplicativo. Além disso, é recomendável *salvar* estados de ponto de verificação em vários pontos durante o processo. Ele também pode ser muito útil ter outra instância do Unity do aplicativo original para permitir a comparação lado a lado durante o processo de porta. 

> [!NOTE]
> Antes da portabilidade, verifique se que você tem as ferramentas mais recentes instaladas para o desenvolvimento de realidade mista do Windows. Para a maioria dos desenvolvedores HoloLens existente, isso envolverá principalmente atualizando para o Visual Studio 2017 mais recente e instalar o SDK do Windows apropriada. O conteúdo abaixo irá se aprofundar em diferentes versões do Unity e a versão 2 do Kit de ferramentas de realidade mista.
>
> Para obter mais informações, consulte [instalar as ferramentas](install-the-tools.md).

## <a name="migrate-project-to-latest-version-of-unity"></a>Migrar o projeto para a versão mais recente do Unity

Se usar o v2 MRTK, Unity 2018 LTS será o melhor caminho de suporte sem alterações significativas no Unity ou no MRTK.  A compilação recomendada do Unity, pelo acima "instalar as ferramentas" é 2018.3 do Unity, que se tornará a versão de LTS de Unity 2018.  Além disso, o v2 MRTK será sempre garantir suporte para Unity 2018 LTS, mas não necessariamente garantir suporte para cada iteração do Unity 2019.x. 

Para ajudar a esclarecer outras diferenças entre o Unity 2018.3.x ou Unity 2019.1.x abaixo descreve as vantagens e desvantagens entre essas duas versões, com a principal diferença de significância sendo a capacidade de compilar para ARM64 em Unity de 2019. 

Os desenvolvedores devem avaliar qualquer [dependências de plug-in](https://docs.unity3d.com/Manual/Plugins.html) que existem atualmente no seu projeto e se essas DLLs podem ser criadas para ARM64. Se um plug-in forte dependência não pode ser criado para ARM64, um terá utilizar Unity 2018 LTS.


| Unity 2018.3.x | Unity 2019.1 + |
|----------|-------------------|
| Suporte de build ARM32 | Suporte ao build do ARM32 e ARM64 |
| Versão de compilação estáveis LTS | Estabilidade Beta |
| [Back-end .NET scripting](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *preterido* | [Back-end .NET scripting](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *removido* |
| Rede UNET *preterido* | Rede UNET *removido* |

## <a name="update-sceneproject-settings-in-unity"></a>Atualizar as configurações de projeto/cena no Unity

Depois de atualizar para o Unity 2018.3.x ou Unity 2019 +, é recomendável atualizar as configurações de determinado no Unity para obter melhores resultados no dispositivo. Essas configurações são descritas em detalhes sob  **[configurações recomendadas para Unity](Recommended-settings-for-Unity.md)** .

Ele deve ser iterado novamente que o [back-end .NET de script](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) está sendo substituído no Unity 2018 e *removido* em Unity 2019 e, assim, os desenvolvedores fortemente considere alternar seu projeto para [ IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). 

> [!NOTE]
> Back-end IL2CPP script pode causar tempos de build do Unity para Visual Studio e, portanto, os desenvolvedores devem configurar sua máquina de desenvolvedor para [otimizando tempos de build IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).
> Além disso, pode ser benéfico para configurar uma [servidor de Cache](https://docs.unity3d.com/Manual/CacheServer.html), especialmente para projetos do Unity com uma grande quantidade de ativos (excluindo os arquivos de script) ou constantemente mudando cenas/ativos. Ao abrir um projeto, o Unity armazena qualificados ativos em um formato de cache interno no computador do desenvolvedor. Itens devem ser importados novamente e, portanto, processados novamente quando modificado. Esse processo pode ser feito uma vez e salvo em um servidor de Cache e, consequentemente, compartilhado com outros desenvolvedores para economizar tempo, em vez de todos os desenvolvedores de processar a nova importação de novas alterações localmente.

Depois de abordar quaisquer alterações interruptivas após a mudança para a versão atualizada do Unity, os desenvolvedores devem compilar e testar seus aplicativos atuais no HoloLens (1º gen). Além disso, isso é um bom ponto para criar e salvar uma confirmação para o controle do código-fonte. 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Compilar dependências/plug-ins para processador ARM

HoloLens (1º gen) executado aplicativos em um x86 processador enquanto o novo dispositivo 2 HoloLens utiliza um processador ARM. Portanto, os aplicativos existentes precisam ser portada para dar suporte a ARM. Conforme observado anteriormente, Unity 2018 der suporte à compilação para ARM32 aplicativos enquanto o Unity 2019 + der suporte à compilação para aplicativos ARM64. Desenvolvimento para aplicativos ARM64 é geralmente preferível pois não há uma diferença de material de desempenho. No entanto, isso exige que todos os [dependências de plug-in](https://docs.unity3d.com/Manual/Plugins.html) também ser compilados para ARM64. 

Examine todas as dependências DLL em seu aplicativo no momento. Se uma dependência não for mais necessário, é aconselhável removê-lo do seu projeto. Para restantes plug-ins que são necessários, ingestão os respectivos binários ARM32 ou ARM64 em seu projeto do Unity. 

Após a ingestão de DLLs relevantes, criar uma solução do Visual Studio do Unity e, em seguida, compilar um AppX para ARM no Visual Studio para testar se o seu aplicativo pode ser compilado para processadores ARM. Esse outro ponto em que é recomendável salvar uma confirmação em sua solução de controle do código-fonte. 

## <a name="update-to-mrtk-version-2"></a>Atualizar para a versão 2 do MRTK

MRTK versão 2 é o novo Kit de ferramentas na parte superior do Unity que dão suporte a ambos os HoloLens (1º gen) e 2 do HoloLens, e onde todos os novos recursos do HoloLens 2 foram adicionados, como entregar as interações e acompanhamento de olho.

### <a name="prepare-for-the-migration"></a>Preparar para a migração

Antes da ingestão de novos [*.unitypackage arquivos para a v2 MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), é recomendável fazer um inventário dos **1) qualquer código personalizado que se integra ao MRTK v1** e **2) qualquer código personalizado para interações de entrada ou componentes UX**. Conflito mais predominante e comuns para um desenvolvedor de realidade misturada ingestão o v2 MRTK novo envolverá a entrada e interações. Portanto, é aconselhável a leitura começará e Noções básicas sobre o [modelo de entrada MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html).

Por fim, o novo v2 MRTK fez a transição de um modelo de scripts e objetos na cena manager para uma configuração e arquitetura de provedor de serviços. Isso resulta em um modelo de arquitetura e a hierarquia de cena mais limpo, mas requer uma curva de aprendizado para entender os novos perfis de configuração. Portanto, leia as [guia de configuração de kit de ferramentas de realidade mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) para começar a se familiarizar com os perfis e configurações importantes para se ajustar às necessidades do seu aplicativo. 

### <a name="perform-the-migration"></a>Executar a migração

Depois de importar MRTK v2, seu projeto do Unity provavelmente terá muitos erros relacionados ao compilador. Esses são mais comumente devido a nova estrutura de namespace e os novos nomes de componente. Vá para resolver esses erros modificando seus scripts para os novos namespaces e os componentes. 

Para obter mais informações sobre as diferenças de API específicas entre HTK/MRTK e MRTK versão 2, consulte o guia de portabilidade na [MRTK versão 2 wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html).

### <a name="best-practices"></a>Práticas recomendadas

- Prefira o uso do sombreador MRTK padrão
- Trabalho em uma quebra de alterar o tipo de cada vez (por exemplo: IFocusable para IMixedRealityFocusHandler)
- Testar após cada alteração e utilizar o controle de origem
- Usar padrão MRTK UX (botões, slates, etc.) quando possível
- Tente evitar modificar arquivos MRTK diretamente, em vez disso, criar wrappers em torno de componentes MRTK
    - Isso protegerá contra futuras ingestions de MRTK e atualizações
- Analisar e explorar cenas de exemplo fornecidas no MRTK (especialmente *HandInteractionExamples.scene*)
- Recriar a interface do usuário baseada na tela com quadrados, colisores e TextMeshPro texto em vez disso

### <a name="testing-your-application"></a>Testando seu aplicativo

Agora que os recursos e componentes do HoloLens 2 estão disponíveis no MRTK versão 2, desde [RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1), você pode simular as interações de mão diretamente no Unity e desenvolver com as novas APIs para interações de mão e acompanhamento a olho nu.  O dispositivo HoloLens 2 é necessária para criar uma ótima experiência, mas pelo menos um poderia começar a aprender nas ferramentas e documentação. Além disso, o MRTK v2 dá suporte ao desenvolvimento em HoloLens (1º gen) e assim, modelos de entrada tradicional, como select por meio do toque de ar ainda pode ser testados no HoloLens (1º gen) dispositivos. 

## <a name="updating-interaction-model-for-hololens-2"></a>Atualizando o modelo de interação para HoloLens 2

Depois que seu aplicativo com portas e preparada para HoloLens 2, você está pronto para considerar a atualização da sua interação com o modelo e holograma designs/posicionamento.
Provenientes do HoloLens (1º gen), seu aplicativo provavelmente tem um modelo de interação de olhar e commit, com hologramas relativamente à mão para o campo de visualização se encaixam.

Etapas para atualizar o design de seu aplicativo para ser a melhor para HoloLens 2:
1.  Componentes MRTK: Por trabalho prévio, se você tiver adicionado MRTK v2, há vários componentes/scripts aproveitar que tenha sido projetados e otimizadas para HoloLens 2.

2.  Modelo de interação: Considere atualizar seu modelo de interação.  Na maioria dos cenários, recomendamos a alternância de olhar e confirmar em mãos.  Com sua hologramas normalmente fiquem fora de braços alcance, a alternar para mãos resultará em raios apontador de interação mais distante e pegue gestos.
Observação: há cenários em que um modelo de interação sem intervenção é necessário, como um trabalho de tarefa que contém as ferramentas, e há diretrizes de design específicas para esses casos. 

3.  Posicionamento de holograma: Depois de alternar para um modelo de interação de mãos, considere mover alguns hologramas mais próximo para interagir diretamente com as hologramas com suas mãos, usando quase gestos de captura de interação.  Os tipos de hologramas recomendados se aproximar capturar, diretamente ou interagir são menus de destino menores, controles, botões e hologramas menores do que se ajustam o HoloLens 2 campo de visualização quando pegando e inspecionando o holograma.
<br>
Cada aplicativo e o cenário são diferente, e continuaremos a refinar e lançar o design de orientação com base nos comentários e lições aprendidas de continuação.


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>Lições aprendidas adicionais de mover aplicativos do x86 para ARM

- Aplicativos do Unity retos são simples como você pode criar um pacote de appx ARM ou implante diretamente para o dispositivo e é executado.
O desafio surge quando o aplicativo do Unity usa o plug-ins nativo.  Todos os plug-ins nativos precisam ser atualizados para o VS2017 e recompilados para ARM e com o Unity 2019, ARM64.

- Um aplicativo, usado o plug-in AudioKinetic Wwise para Unity e a versão usada não tinha um plug-in UWP ARM. Ele levou vários dias para trabalhar novamente o som no aplicativo para trabalhar em ARM.

- Em outros casos, um plug-in UWP/ARM pode não existir para aplicativo necessário plug-ins, bloqueando a capacidade de porta e executar em 2 HoloLens.  Compromisso com o provedor de plug-in pode ser necessário para desbloquear e dar suporte a ARM.

- Minfloat (e variantes como min16float, minint, etc.) em sombreadores comporte de forma diferente em 2 de HoloLen que no HoloLens (1º gen). Especificamente, eles garantem que "pelo menos o especificado será usado o número de bits". Em GPUs Nvidia/Intel, em grande parte, apenas esses são tratados como 32 bits. No ARM, o número de bits especificado, na verdade, é respeitado. Isso significa que, na prática, esses números podem ter menos precisão/intervalo em 2 HoloLens que ocupavam no HoloLens (1º gen).

- As instruções de _asm não estão funcionando no ARM, que significa que qualquer código usando instruções _asm precisa ser reescrito.

- Não há suporte para o conjunto de instruções SIMD no ARM. Isso significa que vários cabeçalhos, como xmmintrin, emmintrin, tmmintrin.h e immintrin não estão disponíveis no ARM.

- O compilador de sombreador no ARM executa durante a primeira chamada de desenho depois que o sombreador foi carregado ou algo do sombreador depende foi alterado, não no tempo de carregamento do sombreador. O impacto na taxa de quadros pode ser perceptível, dependendo de quantos sombreadores precisam ser compilado. Isso tem várias implicações para como sombreadores devem ser tratados/empacotado/atualizados diferente no vs HoloLens 2 HoloLens (1º gen).

## <a name="see-also"></a>Consulte também
* [Introdução ao MRTK versão 2](mrtk-getting-started.md)
* [MRTK versão 2 HowTo](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [Instalar as ferramentas](install-the-tools.md)
* [Configurações recomendadas do Unity](recommended-settings-for-unity.md)
* [Noções básicas sobre desempenho para realidade misturada](understanding-performance-for-mixed-reality.md)

