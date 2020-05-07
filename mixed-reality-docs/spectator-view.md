---
title: Modo de exibição Espectador
description: Visualize os hologramas em um dispositivo externo como um meio de demonstrar uma experiência de realidade misturada em uma tela externa ou gravando um vídeo de uma experiência de realidade misturada.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Modo de exibição Espectador, iPhone, iOS, iPad, OpenCV, câmera, ARKit, HoloLens, realidade misturada, MixedRealityToolkit, demonstração, gravar
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "74491163"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Modo de exibição Espectador para o HoloLens e o HoloLens 2

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>Visão geral

Ao utilizar um HoloLens, muitas vezes, nós nos esquecemos de que uma pessoa sem ele não pode experimentar as maravilhas que podemos ver. O Modo de exibição Espectador permite que outras pessoas vejam em uma tela 2D o que um usuário do HoloLens vê no mundo dele.
O Modo de exibição Espectador oferece uma abordagem rápida e acessível para a gravação de hologramas em HD com dispositivos móveis. Ele também oferece uma gravação de qualidade profissional de hologramas com câmeras de vídeo.

## <a name="key-resources"></a>Principais recursos

* [**Modo de exibição Espectador no GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Documentação do Modo de exibição Espectador**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Amostras do Modo de exibição Espectador**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>Casos de uso
* Você pode gravar uma experiência de realidade misturada usando um dispositivo iPhone ou Android. Faça a gravação em Full HD e aplique a suavização aos hologramas e, até mesmo, às sombras. É uma maneira econômica e rápida de capturar um vídeo dos hologramas.
* Transmita experiências de realidade misturada ao vivo para uma Apple TV diretamente no iPhone ou no iPad, sem retardos.
* Compartilhe a experiência com seus convidados: Permita que os usuários que não sejam do HoloLens experimentem os hologramas diretamente em seus respectivos telefones ou tablets.

## <a name="current-features"></a>Recursos atuais

* Sincronização espacial de hologramas, de modo que todos vejam os hologramas exatamente no mesmo local.
* Suporte para iOS (dispositivos habilitados para ARKit) e Android (dispositivos habilitados para ARCore).
Vários convidados do iOS.
Gravação de vídeo + hologramas + som ambiente + som de holograma.
Compartilhe a planilha para salvar um vídeo, enviá-lo por email ou compartilhá-lo com outros aplicativos de suporte.

![Marcador](images/SpecViewPhoneDemo.jpg)
![Marcador](images/hololensspectatorview-500px.jpg) ![Marcador](images/spectatorview-300px.png)

A tabela a seguir mostra diferentes funcionalidades do Modo de exibição Espectador e seus recursos. Escolha a opção que melhor se adapte às suas necessidades de gravação de vídeo:

|                                      | Celular                  |                    Câmera de vídeo              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Qualidade de HD                           |         Full HD         |        Filmagem de qualidade profissional (conforme determinado pela câmera de vídeo)      |
| Fácil movimento da câmera                 |            ✔            |                      ✔                      |
| Exibição de terceira pessoa                    |            ✔            |                      ✔                      |
| Pode ser transmitido para telas           |            ✔            |                      ✔                      |
| Portátil                             |            ✔            |                                             |
| Sem fio                             |            ✔            |                                             |
| Hardware adicional necessário         |     Telefone Android, iPhone    | HoloLens + simulador + tripé + câmera de vídeo + computador + Unity |
| Investimento de hardware                  |           Baixa            |                     Alto                    |
| Plataforma cruzada                       |           Android, iOS   |                                             |
| Conteúdo sincronizado                 |            ✔            |                      ✔                      |
| Duração da instalação de runtime               |         Instantânea          |                     Lenta                    |
## <a name="see-also"></a>Veja também

* [Captura de realidade misturada](mixed-reality-capture.md) 
* [Captura de realidade misturada para desenvolvedores](mixed-reality-capture-for-developers.md)
* [Experiências compartilhadas em realidade misturada](shared-experiences-in-mixed-reality.md)
