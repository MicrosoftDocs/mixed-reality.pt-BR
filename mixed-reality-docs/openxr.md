---
title: OpenXR
description: Crie um mecanismo usando o padrão da API OpenXR portátil e implante-o na realidade mista do Windows e fones de ouvido 2 do HoloLens.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Mixed Realm OpenXR portal do desenvolvedor, DirectX, nativo, mecanismo personalizado do aplicativo nativo, middleware
ms.openlocfilehash: cf8795e6fed7db9fd0743d0902ce1585d56fa5e0
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438142"
---
# <a name="openxr"></a>OpenXR

O OpenXR é um padrão de API livre de royalties aberto da <a href="https://www.khronos.org/" target="_blank">Khronos</a> que fornece aos mecanismos acesso nativo a uma ampla gama de dispositivos de muitos fornecedores que abrangem o [espectro de realidade misturada](mixed-reality.md).

Você pode desenvolver usando OpenXR em um headset de imersão de realidade 2 ou Windows misto na área de trabalho.  Se você não tiver acesso a um headset, poderá usar o emulador do HoloLens 2 ou o simulador de realidade mista do Windows.

## <a name="why-openxr"></a>Por que OpenXR?

Com o OpenXR, você pode criar mecanismos direcionados a ambos os dispositivos Holographic (como o HoloLens 2) que colocam o conteúdo digital no mundo real como se estivesse realmente lá, bem como dispositivos de imersão (como o Windows Mixed Realm headsets para PCs Desktop) que ocultam o físico o mundo e o substituem por uma experiência digital.  O OpenXR permite que você escreva código depois de ser portátil em uma ampla gama de plataformas de hardware.

A API OpenXR usa um carregador que conecta seu aplicativo diretamente ao suporte de plataforma nativa do headset.  Isso oferece aos seus usuários finais o desempenho máximo e a latência mínima, se eles estiverem usando um headset de realidade mista do Windows ou qualquer outro headset.

## <a name="what-is-openxr"></a>O que é o OpenXR?

A API Core OpenXR 1,0 fornece a funcionalidade básica que você precisará para criar um mecanismo que pode ter como alvo os dispositivos Holographic, como o HoloLens 2 e dispositivos de imersão, como headsets de realidade mista do Windows:
* Sistemas + sessões
* Espaços de referência (exibição, local, estágio)
* Exibir configurações (mono, estéreo)
* Permuta + temporização de quadro
* Camadas de composição
* Entrada e haptics
* API de gráficos + integração de plataforma

Para saber mais sobre a API do OpenXR, confira a <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação</a>do OpenXR 1,0, <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">referência de API</a> e <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guia de referência rápida</a>.  Para obter mais informações, consulte a <a href="https://www.khronos.org/openxr/" target="_blank">página Khronos OpenXR</a>.

Para direcionar o conjunto de recursos completo do HoloLens 2, você também usará extensões de OpenXR específicas de fornecedor e de fornecedor que habilitam recursos adicionais além do OpenXR 1,0 Core, como controle de mão articulado, acompanhamento de olho, mapeamento espacial e âncoras espaciais.  Consulte a seção de [roteiro](openxr.md#roadmap) abaixo para obter mais informações sobre as extensões lançadas posteriormente neste ano.

Observe que o OpenXR não é, em si, um mecanismo de realidade misturada.  Em vez disso, o OpenXR permite que mecanismos como Unity e inreais gravem código portátil uma vez que possam acessar os recursos da plataforma nativa do dispositivo Holographic ou de imersão do usuário, independentemente de qual fornecedor criou essa plataforma.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introdução ao OpenXR para o HoloLens 2

Para começar a desenvolver aplicativos OpenXR para o HoloLens 2:

1. Configure um HoloLens 2 ou siga as instruções para [instalar o emulador do HoloLens 2](using-the-hololens-emulator.md).
1. Inicie o aplicativo da loja de dentro do dispositivo ou emulador e verifique se todos os aplicativos estão atualizados.  Isso garantirá que o tempo de execução do OpenXR em seu HoloLens seja atualizado para o OpenXR 1,0.  Se estiver usando o emulador, você desejará consultar as [instruções de entrada do emulador](using-the-hololens-emulator.md#basic-emulator-input) para ajudá-lo a usar o aplicativo da loja dentro do emulador.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introdução ao OpenXR for Windows Mixed realness headsets

Para começar a desenvolver aplicativos OpenXR para headsets de imersão misturadas do Windows:

1. Verifique se você está executando o Windows 10 pode 2019 atualização (1903), que é o requisito mínimo para o Windows Mixed Reality que os usuários finais executam aplicativos OpenXR.  Se você estiver em uma versão anterior do Windows 10, poderá atualizar para a atualização de maio de 2019 usando o <a href="https://www.microsoft.com//software-download/windows10" target="_blank">Assistente de atualização do Windows 10</a>.  Se você não conseguir atualizar seu computador, também será possível [desenvolver seu aplicativo OpenXR usando a atualização de 10 de outubro de 2018 (1809)](openxr.md#developing-on-windows-10-october-2018-update), embora você possa enfrentar um desempenho inferior ou outros problemas.
2. Configure um headset de realidade mista do Windows ou siga as instruções para [habilitar o simulador de realidade mista do Windows](using-the-windows-mixed-reality-simulator.md).  Depois de configurar a realidade mista do Windows, o portal de realidade misturada instalará automaticamente o tempo de execução do Windows Mixed Reality OpenXR.  O Microsoft Store manterá o tempo de execução atualizado.
3. Torne o tempo de execução do OpenXR do Windows Mixed Realm ativo iniciando o portal de realidade misturada no menu Iniciar, clicando no botão... no canto inferior esquerdo e selecionando "configurar OpenXR".<br>
![configurar o OpenXR no portal de realidade misturada](images/mixed-reality-portal-set-up-openxr.png)

Se você precisar tornar o tempo de execução do Windows Mixed Reality OpenXR ativo novamente, repita a etapa 3.

> [!NOTE]
> Em breve, o tempo de execução do Windows Mixed Reality OpenXR será configurado automaticamente para todos os usuários finais do Windows Mixed Reality.

## <a name="getting-the-mixed-reality-openxr-developer-portal"></a>Obtendo o portal do desenvolvedor OpenXR da realidade misturada

Para experimentar o tempo de execução do Windows Mixed Reality OpenXR, você pode instalar o <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">aplicativo [Mixed Reality OpenXR Developer portal</a>.  Esse aplicativo fornece uma cena de demonstração que exercita vários recursos do OpenXR, juntamente com uma página de status do sistema que fornece informações importantes sobre o tempo de execução ativo e o headset atual.

![Aplicativo de portal do desenvolvedor OpenXR de realidade misturada](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>Criando um aplicativo OpenXR de exemplo

O projeto <a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> demonstra um exemplo de OpenXR simples com dois arquivos de projeto do Visual Studio, um para um aplicativo de área de trabalho Win32 e outro para um aplicativo UWP HoloLens 2.  Como a solução contém um projeto UWP do HoloLens, você precisará do [plataforma universal do Windows carga de trabalho de desenvolvimento](install-the-tools.md#installation-checklist) instalada no Visual Studio para abri-lo totalmente.

Observe que, embora os arquivos de projeto Win32 e UWP sejam separados devido a diferenças no empacotamento e na implantação, o código do aplicativo dentro de cada projeto é de 100% o mesmo!

## <a name="roadmap"></a>Mapa

A especificação OpenXR define um mecanismo de extensão que permite que implementadores de tempo de execução exponham funcionalidades adicionais além dos [principais recursos](openxr.md#what-is-openxr) definidos na <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação OpenXR 1,0 base</a>.

Há três tipos de extensões OpenXR:
* **Extensões de fornecedor (por exemplo, MSFT):** Habilita a inovação por fornecedor em recursos de hardware ou software.  Qualquer fornecedor de tempo de execução pode introduzir e enviar uma extensão de fornecedor a qualquer momento.
* **Extensões ext:** Extensões entre fornecedores que várias empresas definem e implementam.  Grupos de empresas interessadas podem introduzir extensões EXT a qualquer momento.
* **Extensões KHR:** As extensões Khronos oficiais são ratificadas como parte de uma versão de especificação principal.  As extensões KHR são cobertas pela mesma licença que a principal espec.

Ao final do ano, o tempo de execução do Windows Mixed Reality OpenXR dará suporte a um conjunto de extensões MSFT e EXT que trazem o conjunto completo de recursos do HoloLens 2 para aplicativos OpenXR:
* [Espaço de referência não associado (experiências de escala mundial)](coordinate-systems.md#building-a-world-scale-experience)
* [Âncoras espaciais + armazenamento](spatial-anchors.md)
* [Mão Articulation + malha à mão](hands-and-tools.md)
* [Foco com o olhar](eye-tracking.md)
* [Configurações de exibição secundárias (captura de realidade mista)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [Mapeamento espacial](spatial-mapping.md)
* Interoperabilidade com APIs de SDK do Windows

Embora algumas dessas extensões possam ser iniciadas como extensões de MSFT específicas do fornecedor, a Microsoft e outros fornecedores de tempo de execução OpenXR estão trabalhando juntos para projetar extensões de extensão ou KHR de vários fornecedores para muitas dessas áreas de recursos.  Isso permitirá que o código que você escreve para esses recursos seja portável em fornecedores de tempo de execução, assim como na Especificação principal.

## <a name="troubleshooting"></a>Painel de controle da

Aqui estão algumas dicas de solução de problemas para o tempo de execução OpenXR do Windows Mixed Reality.  Se você tiver outras dúvidas sobre a <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação do OpenXR 1,0</a>, visite os <a href="https://community.khronos.org/c/openxr" target="_blank">fóruns do Khronos OpenXR</a> ou a <a href="https://khr.io/slack" target="_blank">margem de atraso #openxr canal</a>.

### <a name="developing-on-windows-10-october-2018-update"></a>Desenvolvendo no Windows 10 de outubro de 2018 atualização

Se não for possível [atualizar seu PC de desenvolvimento para a atualização de maio de 2019](https://www.microsoft.com//software-download/windows10), você poderá configurar seu PC de atualização do Windows 10 de outubro de 2018 (1809) para desenvolvimento seguindo mais uma etapa:

1. Siga as etapas acima para começar a usar o OpenXR em seu PC desktop.
1. Para definir o tempo de execução do Windows Mixed Reality OpenXR como o tempo de execução do OpenXR do seu sistema, instale o [pacote de compatibilidade do desenvolvedor do Windows Mixed Reality OpenXR](https://aka.ms/openxr-compat).

> [!NOTE]
> Embora a atualização do Windows 10 de outubro de 2018 (1809) possa ser usada ao desenvolver seus aplicativos OpenXR, a atualização do Windows 10 pode ser 2019 (1903) é o requisito mínimo para que os usuários finais usem o OpenXR com a realidade mista do Windows.  Você pode enfrentar um desempenho inferior ou outros problemas ao executar seu aplicativo OpenXR na atualização de outubro de 2018.  É altamente recomendável que você atualize seu PC de desenvolvimento para a atualização 2019 do Windows 10 (1903).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>O aplicativo OpenXR não está iniciando a realidade mista do Windows

Se seu aplicativo OpenXR não estiver iniciando a realidade mista do Windows quando você executá-lo, o tempo de execução do Windows Mixed Reality OpenXR não poderá ser definido como o tempo de execução ativo.  Siga as instruções acima para [começar a usar o OpenXR for Windows Mixed realness headsets](#getting-started-with-openxr-for-windows-mixed-reality-headsets) para tornar o tempo de execução ativo.

Você também pode executar o [portal do desenvolvedor OpenXR da realidade misturada](#getting-the-mixed-reality-openxr-developer-portal) para solucionar problemas adicionais para obter ajuda em relação ao estado do tempo de execução do Windows Mixed Reality OpenXR em seu sistema.

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>Portal de realidade misturada não mostrando o item de menu "configurar OpenXR"

Verifique se você está executando pelo menos a atualização de 10 de outubro de 2018 do Windows (1809).  Se você estiver em uma versão anterior do Windows 10, poderá atualizar para a atualização de maio de 2019 (1903) usando o [Assistente de atualização do Windows 10](https://www.microsoft.com//software-download/windows10).

O item de menu "configurar OpenXR" pode não estar disponível se você tiver uma versão mais antiga do aplicativo do portal de realidade misturada.  Verifique se há uma [atualização de aplicativo do portal da realidade misturada](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) para garantir que você tem a versão mais recente.

Observe que o item de menu "set up OpenXR" não aparecerá se o tempo de execução do Windows Mixed Reality já estiver instalado e ativo.  Você pode instalar o [portal do desenvolvedor OpenXR da realidade mista](#getting-the-mixed-reality-openxr-developer-portal) para determinar o status atual do tempo de execução do OpenXR em seu sistema.

## <a name="see-also"></a>Consulte também

* <a href="https://www.khronos.org/openxr/" target="_blank">Mais informações sobre o OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Especificação do OpenXR 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Referência de API do OpenXR 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guia de referência rápida do OpenXR 1,0</a>
