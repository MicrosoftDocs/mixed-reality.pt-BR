---
title: Pacotes MRTK
description: Este artigo descreve os pacotes que compõem o Toollkit realidade mista do Microsoft.
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality, MRTK, componente, o pacote
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590928"
---
# <a name="mrtk-packages"></a>Pacotes MRTK

O Kit de ferramentas de realidade misturada (MRTK) é uma coleção de pacotes que permitem o desenvolvimento de aplicativos de realidade mista de plataforma cruzada, fornecendo suporte para realidade misturada plataformas de hardware e de maneira modular.

Há três categorias de pacotes MRTK: 

* [Foundation](#foundation-packages)
* [Extensão](#extension-packages)
* [Experimental](#experimental-packages)

## <a name="foundation-packages"></a>Pacotes de base

A base de kit de ferramentas de realidade mista é o conjunto de pacotes que permitem que seu aplicativo aproveitar a funcionalidade comum entre as plataformas de realidade mista. Esses pacotes são liberados e suporte da Microsoft do código-fonte na [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) ramificação no GitHub.

![MRTK Foundation pacotes](images/mrtk-foundation.jpg)

*Pacotes de base do Kit de ferramentas de realidade mistos*

A base de MRTK é composta de:

* [Pacote de núcleo](#core-package)
* [Provedores de plataforma](#platform-providers)
* [Serviços do sistema](#system-services)
* [Ativos de recurso](#feature-assets)

As seções a seguir descrevem os tipos de pacotes em cada categoria.

### <a name="core-package"></a>Pacote de núcleo

O pacote principal é um _necessária_ componente e é executada como uma dependência por todos os pacotes de foundation MRTK.

O pacote MRTK Core inclui:

* [Tipos de dados, interfaces e classes comuns](#common-interfaces-clases-and-data-types)
* [Componente de cena MixedRealityToolkit](#mixedrealitytoolkit-scene-component)
* [Sombreador MRTK padrão](#mrtk-standard-shader)
* [Provedor de entrada do Unity](#unity-input-provider)
* [Gerenciamento de pacotes](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a>Tipos de dados, interfaces e classes comuns

O pacote de núcleo de kit de ferramentas de realidade mista contém as definições para todas as interfaces comuns, classes e tipos de dados que são usados por todos os outros componentes. É altamente recomendável que os aplicativos acessar componentes MRTK exclusivamente por meio de interfaces definidas para permitir o maior nível de compatibilidade entre plataformas.

#### <a name="mixedrealitytoolkit-scene-component"></a>Componente de cena MixedRealityToolkit

O componente de cena MixedRealityToolkit é o Gerenciador de recursos único e centralizado para o Kit de ferramentas de realidade mista. Esse componente carrega e gerencia o tempo de vida dos módulos do serviço e plataforma e fornece recursos para os sistemas acessar suas definições de configuração. 

#### <a name="mrtk-standard-shader"></a>Sombreador MRTK padrão

O sombreador padrão do MRTK fornece a base para praticamente todos os materiais fornecidos pelo MRTK. Esse sombreador é extremamente flexível e otimizado para a variedade de plataformas em que há suporte para MRTK. Vale _altamente_ recomendado que o material do seu aplicativo usa o sombreador padrão de MRTK para otimizar o desempenho.

#### <a name="unity-input-provider"></a>Provedor de entrada do Unity

O provedor de entrada do Unity fornece acesso a dispositivos de entrada comuns, como controladores de jogos, telas sensíveis ao toque e mouse espacial 3D.

#### <a name="package-management"></a>Gerenciamento de pacotes

_Em breve_

O pacote de núcleo de kit de ferramentas de realidade mista oferece suporte para descobrir e gerenciar foundation opcional, extensão e pacotes MRTK experimentais.

### <a name="platform-providers"></a>Provedores de plataforma

Os pacotes de provedor de plataforma MRTK são os componentes que habilitam o Kit de ferramentas de realidade mista para hardware de realidade mista de destino e a funcionalidade de plataforma.

Plataformas com suporte incluem:

* [Windows Mixed Reality](#windows-mixed-reality)
* [OpenVR](#openvr)
* [Windows Voice](#windows-voice)

#### <a name="windows-mixed-reality"></a>Windows Mixed Reality

O pacote do Windows Mixed Reality oferece suporte para dispositivos Microsoft HoloLens e Windows misto realidade envolventes. O pacote contém suporte de plataforma completo, incluindo:

* Mantenha o foco de direcionamento
* Gestos
* Controladores de movimento de realidade mista do Windows
* Mapeamento espacial

#### <a name="openvr"></a>OpenVR

O pacote de OpenVR fornece a plataforma de hardware e suportam para dispositivos que usam a plataforma OpenVR.

#### <a name="windows-voice"></a>Voz do Windows

O pacote de voz do Windows oferece suporte para a funcionalidade de reconhecimento e ditado de palavra-chave em dispositivos Microsoft Windows 10.

### <a name="system-services"></a>Serviços do sistema

Principais serviços de plataforma são fornecidos em pacotes de serviço do sistema. Esses pacotes contêm implementações de padrão do Toolkit de realidade misturada das interfaces de serviço de sistema, definidas na [core](#core-package) pacote.

A base MRTK inclui os seguintes serviços do sistema:

* [Sistema de limite](#boundary-system)
* [Sistema de diagnóstico](#diagnostic-system)
* [Sistema de entrada](#input-system)
* [Sistema de percepção espacial](#spatial-awareness-system)
* [Sistema de ser transportado](#teleport-system)

#### <a name="boundary-system"></a>Sistema de limite

O sistema de limite MRTK fornece dados sobre a realidade para virtual playspace. Em sistemas para os quais o usuário tiver configurado o limite, o sistema pode fornecer um plano de chão, playspace retangular, área controlada e muito mais.

#### <a name="diagnostic-system"></a>Sistema de diagnóstico

O sistema de diagnóstico MRTK fornece dados de desempenho em tempo real dentro de sua experiência de aplicativo. Em um as, você poderá exibir a taxa de quadros, tempo de processador e outras principais métricas de desempenho que você use seu aplicativo.

#### <a name="input-system"></a>Sistema de entrada

Os sistemas de entrada MRTK permite que os aplicativos acessar a entrada de uma maneira de plataforma cruzada especificando ações do usuário e atribuir essas ações para os botões mais apropriados e os eixos em controladores de destino.

#### <a name="spatial-awareness-system"></a>Sistema de percepção espacial

O sistema de percepção espacial MRTK permite acesso a dados ambientais do mundo real de dispositivos, como o Microsoft HoloLens.

#### <a name="teleport-system"></a>Sistema de ser transportado

O sistema de ser transportado MRTK fornece suporte de locomotion de realidade virtual.

### <a name="feature-assets"></a>Ativos de recurso

Ativos de recurso são coleções de funcionalidades relacionadas fornecidos, como scripts e ativos do Unity. Alguns desses recursos incluem:

* Controles de Interface do usuário
* Recursos padrão
* more

## <a name="extension-packages"></a>Pacotes de extensão

Pacotes de extensão MRTK são uma coleção de pacotes escritos pela Microsoft e pela comunidade que estendem e melhoram a funcionalidade do Kit de ferramentas de realidade mista. Os autores de extensão serão as dependências necessárias de estado, marcar o pacote como compatível com o Kit de ferramentas de realidade mista e fornecer licenciamento e dão suporte a instruções.

Pacotes de extensão podem fornecer novos recursos e suporte a nova plataforma. Ao longo do tempo, as extensões podem, com a assistência e aprovação dos autores, ser migradas para a base de MRTK no tempo em que eles serão lançados e suporte da Microsoft.

![Pacote de extensão MRTK](images/mrtk-extensions.jpg)

*Pacotes de extensão do Kit de ferramentas de realidade mistos*

## <a name="experimental-packages"></a>Pacotes experimentais

Pacotes experimentais fornecem a capacidade de recursos de protótipo de voo, versões de pré-lançamento e novas ideias interessantes. O objetivo de pacotes mais experimentais é tentar algo novo e avaliar o interesse do cliente. Muitos, embora nem todos pacotes experimentais será lançados novamente como extensões quando a criação de protótipos e a fase de teste for concluído.

![Pacotes MRTK Experimental](images/mrtk-experimental.jpg)

*Pacotes Experimental de kit de ferramentas de realidade mistos*

## <a name="conclusion"></a>Conclusão

Os pacotes de kit de ferramentas de realidade mista e o sistema de gerenciamento de pacotes são projetados para habilitar um método simple e transparente para você criar fogo recursos às suas experiências sem a necessidade de componentes desnecessários a serem incluídos no projeto.

Ao longo do tempo, o suporte ao gerenciamento de pacote será adicionado e aprimorado no Toolkit de realidade mista. Se você tiver comentários ou deseja se envolver, visite o [Kit de ferramentas de realidade misturada projeto](https://github.com/Microsoft/MixedRealityToolkit-Unity) no GitHub. 

## <a name="see-also"></a>Consulte também

* [MixedRealityToolkit-Unity (GitHub)](https://github.com/Microsoft/MixedRealityToolkit-Unity)

