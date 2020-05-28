---
title: Notas de versão – maio de 2020
description: As notas de versão do Windows Mixed Reality para o Windows 10 podem 2020 atualização (também conhecida como 2004).
author: tmlyon
ms.author: tmlyon
ms.date: 05/27/2020
ms.topic: article
keywords: notas de versão, versão, Windows 10, Build, 20H1, so, maio de 2020, 2004
ms.openlocfilehash: ec92259662109001c02cf631eb6b9948d61ba9de
ms.sourcegitcommit: b0d15083ec1095e08c9d776e5bae66b4449383bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84124133"
---
# <a name="release-notes---may-2020"></a>Notas de versão – maio de 2020

O **Windows 10 pode 2020 atualização (v2004)** inclui novos recursos para fones de ouvido do Windows Mixed Reality (VR), como a capacidade de iniciar aplicativos Win32 na página inicial misturada de realidade. O HoloLens (1º gen) está em manutenção a longo prazo (LTS), com atualizações de serviço a serem liberadas mensalmente.

Para atualizar para a versão mais recente em headsets do PC para Windows Mixed Reality (VR), abra o aplicativo **configurações** , acesse **Atualizar & segurança**e, em seguida, selecione o botão **verificar atualizações** . Em um PC com Windows 10, você também pode instalar manualmente a **atualização do Windows 10 pode 2020** usando a [ferramenta de criação de mídia do Windows](https://www.microsoft.com/software-download/windows10).

**Versão mais recente para área de trabalho**: Windows 10 v2004 (10.0.19041.264)

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Atualizações para headsets de imersão de realidade mista do Windows

### <a name="introducing-the-new-microsoft-edge"></a>Apresentando o novo Microsoft Edge
Como [anunciado anteriormente](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge), fizemos atualizações para dar melhor suporte ao uso do novo navegador Microsoft Edge no Windows Mixed Reality. O novo Microsoft Edge adota o projeto de software livre Chromium para criar melhor compatibilidade com a Web para clientes e menos fragmentação da Web para todos os desenvolvedores da Web. Ele também dá suporte a WebXR, o novo padrão para a criação de experiências da Web de imersão para headsets de VR, no lugar de WebVR.

### <a name="improved-settings-for-wmr"></a>Configurações aprimoradas para WMR
Graças aos seus comentários, adicionamos e esclarecemos as configurações na página de exibição do headset:

* A **qualidade visual da minha página inicial** altera essas configurações afeta apenas o ambiente doméstico da realidade misturada (Cliff House e Skyloft):

* **Ajuste o nível de detalhes e a qualidade dos efeitos na página inicial da realidade misturada** . isso altera parte da renderização que o utiliza em casa. Em particular, a qualidade visual de materiais diferentes (madeira, concreta, etc.) será dimensionada à medida que você alterar essa configuração de baixo para alto.

* **Alterar a resolução da janela do aplicativo** -por padrão, a maioria das janelas 2D iniciadas na página inicial é iniciada com uma resolução 720p. Embora seja possível redimensioná-las manualmente & verticalmente, você também pode optar por fazer com que todas elas sejam iniciadas em 1080p em vez disso. Anteriormente, essa opção estava disponível como a opção muito alta (beta) em qualidade visual. Nós o dividimos adequadamente como uma configuração separada agora.

* **Opções de experiência** – essas opções ajustam a experiência de realidade misturada para reduzir a carga em sistemas em que o hardware pode se esforçar para acompanhar uma leitura irrestrita de 90 fps. Você pode optar por habilitar ou desabilitar explicitamente essas configurações adicionais ou escolher deixar que o Windows decida e permitir que nossa heurística continue decidindo quando ativar e desativar.

* **Resolução** – se você tiver um headset de alta resolução como o HP, oferecemos suporte para executá-lo em sua resolução nativa ou em uma resolução reduzida por motivos de desempenho. Headsets anteriores, como o Samsung Odyssey e o Odyssey +, dão suporte apenas a uma única resolução, de modo que você não poderá alterar essa configuração nesses headsets.

* **Taxa de quadros** -agora você pode definir manualmente a taxa de quadros da exibição do headset ou continuar a permitir que o Windows Use sua heurística para determinar se 60 hz ou 90 Hz é mais apropriado.

* **Calibragem** -como antes, você pode ajustar seu IPD (distância interpupillary) se houver suporte para o headset.

* **Alternância de entrada** -Alterne o comportamento de alternância de foco de entrada (Win + Y) para ser automático (com base nos comentários do sensor de presença) ou manual.

### <a name="new-cortana-app"></a>Novo aplicativo da Cortana
Esta atualização do Windows inclui a versão mais recente do aplicativo Cortana, que atualmente é apenas em inglês dos EUA e não dá mais suporte a determinados comandos específicos de realidade misturada, como "tirar uma foto" e "fazer um vídeo". Você ainda poderá usar a nova Cortana para iniciar aplicativos e também dará suporte a novos comandos com foco em produtividade como, "quando é minha próxima reunião?" ou "enviar um email para o <name> que estou executando atrasado".

#### <a name="please-help-us-improve"></a>Ajude-nos a melhorar!
Estamos continuamente procurando melhorar a compatibilidade.  Se você achar que seu aplicativo Win32 clássico favorito não está se comportando corretamente durante a realidade mista do Windows, envie comentários por meio de nosso [Hub de comentários](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

## <a name="prior-release-notes"></a>Notas de versão anteriores

* [Notas de versão – maio de 2019](release-notes-may-2019.md)
* [Notas sobre a versão – outubro de 2018](release-notes-october-2018.md)
* [Notas de versão – abril de 2018](release-notes-april-2018.md)
* [Notas sobre a versão – outubro de 2017](release-notes-october-2017.md)
* [Notas sobre a versão – agosto de 2016](release-notes-august-2016.md)
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte também
* [Suporte a headsets de imersão (link externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Suporte ao HoloLens (link externo)](https://support.microsoft.com/products/hololens)
* [Instalar as ferramentas](install-the-tools.md)
* [Envie-nos seus comentários](give-us-feedback.md)
