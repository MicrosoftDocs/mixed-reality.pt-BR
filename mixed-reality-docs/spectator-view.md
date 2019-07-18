---
title: Exibição de Spectator
description: Visualize os hologramas de um dispositivo externo como um meio de demonstrar uma experiência de realidade misturada em uma exibição externa ou um vídeo de gravação de uma experiência de realidade mista.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator exibição, iPhone, iOS, iPad, OpenCV, câmera, ARKit, HoloLens, realidade misturada, MixedRealityToolkit, demonstração, registro
ms.openlocfilehash: 02088d7b218a25c72f2eb98ae24c85a90e6e5b86
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293603"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Exibição do Spectator para o HoloLens e o HoloLens 2

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>Visão geral

Ao utilizar um HoloLens, muitas vezes esquecemos que uma pessoa que não o tem em não é capaz de experimentar as Wonders que podemos. A exibição Spectator permite que outras pessoas vejam em uma tela 2D o que um usuário do HoloLens vê em seu mundo.
A exibição do Spectator oferece uma abordagem rápida e acessível para a gravação de hologramas em HD com dispositivos móveis. Ele também oferece uma gravação profissional de hologramas com câmeras DSLRs.

## <a name="key-resources"></a>Recursos principais

* [**Exibição do Spectator no GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Arquitectura**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Architecture.md)
* [**Amostras**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)
* [**Instruções de configuração do celular**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md)
* [**Instruções de instalação do DSLR**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.DSLR.md)

## <a name="use-cases"></a>Casos de uso
* Você pode registrar uma experiência de realidade mista usando um dispositivo iPhone ou Android. Registre-se em HD completo e aplique a suavização de serrilhado a hologramas e até mesmo sombras. É uma maneira econômica e rápida de capturar vídeo de hologramas.
* Transmita experiências de realidade mistas ao vivo para uma Apple TV diretamente do iPhone ou do iPad, sem atrasos!
* Compartilhe a experiência com convidados: Permita que os usuários não-HoloLens experimentem hologramas diretamente de seus telefones ou Tablets.

## <a name="current-features"></a>Recursos atuais

* Sincronização espacial de hologramas, para que todos vejam os hologramas exatamente no mesmo local.
* suporte para iOS (dispositivos habilitados para ARKit) e Android (dispositivos habilitados para ARCore).
Vários convidados do iOS.
Gravação de vídeo + hologramas + som ambiente + som de holograma.
Compartilhe a planilha para que você possa salvar vídeo, enviá-la por email ou compartilhar com outros aplicativos de suporte.

![Marcador](images/SpecViewPhoneDemo.jpg)
demarcador](images/hololensspectatorview-500px.jpg) ![ de![marcador](images/spectatorview-300px.png)

A tabela a seguir mostra a funcionalidade de exibição Spectator diferente e seus recursos. Escolha a opção que melhor se adapta às suas necessidades de gravação de vídeo:

|                                      | Celular                  |                    Câmera DSLR              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Qualidade de HD                           |         HD completo         |        Filming de qualidade profissional (conforme determinado pelo DSLR)      |
| Movimento de câmera fácil                 |            ✔            |                      ✔                      |
| Exibição de terceira pessoa                    |            ✔            |                      ✔                      |
| Pode ser transmitido para telas           |            ✔            |                      ✔                      |
| Portátil                             |            ✔            |                                             |
| Sem fio                             |            ✔            |                                             |
| Hardware adicional necessário         |     Telefone Android, iPhone    | HoloLens + Rig + Tripod + DSLR + PC + Unity |
| Investimento de hardware                  |           Baixo            |                     Alto                    |
| Plataforma cruzada                       |           Android, iOS   |                                             |
| Conteúdo sincronizado                 |            ✔            |                      ✔                      |
| Duração da instalação de tempo de execução               |         Instantâneo          |                     Modo Lento                    |
## <a name="see-also"></a>Consulte também

* [Captura de realidade misturada](mixed-reality-capture.md) 
* [Captura de realidade misturada para desenvolvedores](mixed-reality-capture-for-developers.md)
* [Experiências compartilhadas em realidade misturada](shared-experiences-in-mixed-reality.md)
