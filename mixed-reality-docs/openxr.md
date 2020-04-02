---
title: OpenXR
description: Crie um mecanismo usando o padrão da API OpenXR portátil e implante-o na realidade mista do Windows e fones de ouvido 2 do HoloLens.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware
ms.openlocfilehash: 04b2404889dc74f191543466beb7ae1e516d0d42
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549372"
---
# <a name="openxr"></a>OpenXR

O OpenXR é um padrão de API livre de royalties aberto da <a href="https://www.khronos.org/" target="_blank">Khronos</a> que fornece aos mecanismos acesso nativo a uma ampla gama de dispositivos de muitos fornecedores que abrangem o [espectro de realidade misturada](mixed-reality.md).

Você pode desenvolver usando OpenXR em um headset de imersão de realidade 2 ou Windows misto na área de trabalho.  Se você não tiver acesso a um headset, poderá usar o emulador do HoloLens 2 ou o simulador de realidade mista do Windows.

## <a name="why-openxr"></a>Por que OpenXR?

Com o OpenXR, você pode criar mecanismos direcionados a ambos os dispositivos Holographic (como o HoloLens 2) que colocam o conteúdo digital no mundo real como se estivesse realmente lá, bem como dispositivos de imersão (como o Windows Mixed Realm headsets para PCs Desktop) que ocultam o físico o mundo e o substituem por uma experiência digital.  O OpenXR permite que você escreva código depois de ser portátil em uma ampla gama de plataformas de hardware.

A API OpenXR usa um carregador que conecta seu aplicativo diretamente ao suporte de plataforma nativa do headset.  Isso oferece aos seus usuários finais o desempenho máximo e a latência mínima, se eles estiverem usando um headset de realidade mista do Windows ou qualquer outro headset.

## <a name="what-is-openxr"></a>O que é o OpenXR?

A API do OpenXR fornece a funcionalidade de previsão de pose principal, temporização de quadro e entrada espacial que você precisará para criar um mecanismo que possa ter como alvo os dispositivos Holographic, como o HoloLens 2 e dispositivos de imersão, como headsets de realidade mista do Windows.

Para saber mais sobre a API do OpenXR, confira a <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação</a>do OpenXR 1,0, <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">referência de API</a> e <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guia de referência rápida</a>.  Para obter mais informações, consulte a <a href="https://www.khronos.org/openxr/" target="_blank">página Khronos OpenXR</a>.

Para direcionar o conjunto de recursos completo do HoloLens 2, você também usará extensões de OpenXR específicas de fornecedor e de fornecedor que habilitam recursos adicionais além do OpenXR 1,0 Core, como controle de mão articulado, acompanhamento de olho, mapeamento espacial e âncoras espaciais.  Consulte a [seção de roteiro](#roadmap) abaixo para obter mais informações sobre as extensões lançadas posteriormente neste ano.

Observe que o OpenXR não é, em si, um mecanismo de realidade misturada.  Em vez disso, o OpenXR permite que mecanismos como Unity e inreais gravem código portátil uma vez que possam acessar os recursos da plataforma nativa do dispositivo Holographic ou de imersão do usuário, independentemente de qual fornecedor criou essa plataforma.

## <a name="roadmap"></a>Roadmap

A especificação OpenXR define um mecanismo de extensão que permite que implementadores de tempo de execução exponham funcionalidades adicionais além dos [principais recursos](#what-is-openxr) definidos na <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificação OpenXR 1,0 base</a>.

Há três tipos de extensões OpenXR:
* **Extensões de fornecedor (por exemplo, `MSFT`):** Habilita a inovação por fornecedor em recursos de hardware ou software.  Qualquer fornecedor de tempo de execução pode introduzir e enviar uma extensão de fornecedor a qualquer momento.
  * **Extensões experimentais do fornecedor (por exemplo, `MSFT_preview`):** Extensões experimentais do fornecedor sendo visualizadas para coletar comentários.  as extensões de `MSFT_preview` são apenas para dispositivos de desenvolvedor e serão removidas quando a extensão real for entregue.  Para experimentá-los, você pode [habilitar as extensões de visualização em seu dispositivo de desenvolvedor](openxr-getting-started.md#using-preview-extensions).
* **Extensões de `EXT` entre fornecedores:** Extensões entre fornecedores que várias empresas definem e implementam.  Grupos de empresas interessadas podem introduzir extensões EXT a qualquer momento.
* **Extensões de `KHR` oficial:** As extensões Khronos oficiais são ratificadas como parte de uma versão de especificação principal.  As extensões KHR são cobertas pela mesma licença que a principal espec.

Em julho de 2020, o tempo de execução do Windows Mixed Reality OpenXR dará suporte a um conjunto de extensões de `MSFT` e `EXT` que trazem o conjunto completo de recursos do HoloLens 2 para aplicativos OpenXR:

| Área do recurso | Disponibilidade da extensão |
|--------------|------------------------|
| Sistemas + sessões | **Especificação de núcleo do OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Espaços de referência (exibição, local, estágio)](coordinate-systems.md) | **Especificação de núcleo do OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Exibir configurações (mono, estéreo) | **Especificação de núcleo do OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Permuta](rendering.md) + [intervalo de quadros](understanding-performance-for-mixed-reality.md) | **Especificação de núcleo do OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Camadas de composição<br />(projeção, Quad) | **Especificação de núcleo do OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Entrada e haptics](interaction-fundamentals.md) | **Especificação de núcleo do OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Integração do Direct3D 11 | **Extensão de `KHR` oficial liberada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code><br /> |
| Integração do Direct3D 12 | **Extensão de `KHR` oficial definida:** *(ainda não há suporte)*<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code><br /><p>**Suporte de visualização**: abril *de 2020 (planejado)*</p><p>**Suporte completo**: maio *de 2020 (planejado)*</p> |
| [Espaço de referência não associado<br />(experiências de escala mundial)](coordinate-systems.md#building-a-world-scale-experience) | **extensão de `MSFT` liberada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Âncoras espaciais](spatial-anchors.md) | **extensão de `MSFT` liberada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [<br />de interação manual (alça/AIM pose, Air-TAP, segure)](hands-and-tools.md) | **extensão de `MSFT_preview` disponível:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_interaction_preview">XR_MSFT_hand_interaction_preview</a></code><p>**versão do`MSFT`** : abril *de 2020 (planejada)*</p> |
| [Mão Articulation + malha à mão](hands-and-tools.md) | **extensão de `MSFT_preview` disponível:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_preview">XR_MSFT_hand_tracking_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_mesh_preview">XR_MSFT_hand_tracking_mesh_preview</a></code><p>**versão de`MSFT`** : maio *de 2020 (planejada)*</p> |
| Interoperabilidade com outros SDKs do HoloLens (por exemplo, [QR](qr-code-tracking.md)) | **extensão de `MSFT_preview` disponível:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_graph_bridge_preview">XR_MSFT_spatial_graph_bridge_preview</a></code><p>**versão de`MSFT`** : maio *de 2020 (planejada)*</p> |
| [Foco com o olhar](eye-tracking.md) | <p>**extensão de`EXT` definida**: *(ainda não há suporte)*<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code><p>**Suporte de visualização**: abril *de 2020 (planejado)*</p><p>**Suporte completo**: maio *de 2020 (planejado)*</p> |
| [<br />de captura de realidade misturada (terceiro processamento da câmera PV)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) | **extensão de `MSFT_preview` disponível:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_secondary_view_configuration_preview">XR_MSFT_secondary_view_configuration_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_first_person_observer_preview">XR_MSFT_first_person_observer_preview</a></code><br /><p>**versão de`MSFT`** : junho *de 2020 (planejada)*</p> |
| [Modelos de renderização do controlador de movimento](motion-controllers.md#rendering-the-motion-controller-model) | <p>**`MSFT_preview`** : abril *de 2020 (planejada)*</p><p>**versão`MSFT`** : julho *de 2020 (planejada)*</p> |
| [Compreensão da cena (planos, malhas)](scene-understanding.md) | <p>**`MSFT_preview`** : maio *de 2020 (planejada)*</p><p>**versão`MSFT`** : julho *de 2020 (planejada)*</p> |

Embora algumas dessas extensões possam ser iniciadas como extensões de `MSFT` específicas do fornecedor, a Microsoft e outros fornecedores de tempo de execução OpenXR estão trabalhando em conjunto para criar `EXT` de fornecedores ou extensões de `KHR` para muitas dessas áreas de recursos.  Isso permitirá que o código que você escreve para esses recursos seja portável em fornecedores de tempo de execução, assim como na Especificação principal.

## <a name="get-started-with-openxr"></a>Introdução ao OpenXR

Você pode desenvolver usando OpenXR em um headset de imersão de realidade 2 ou Windows misto na área de trabalho.  Se você não tiver acesso a um headset, poderá usar o emulador do HoloLens 2 ou o simulador de realidade mista do Windows.

Para começar a desenvolver aplicativos OpenXR para fones de ouvido do Windows com o HoloLens 2 ou de imersão, consulte como começar a usar [o desenvolvimento do OpenXR](openxr-getting-started.md).

## <a name="see-also"></a>Consulte também

* <a href="https://www.khronos.org/openxr/" target="_blank">Mais informações sobre o OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Especificação do OpenXR 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Referência de API do OpenXR 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guia de referência rápida do OpenXR 1,0</a>
