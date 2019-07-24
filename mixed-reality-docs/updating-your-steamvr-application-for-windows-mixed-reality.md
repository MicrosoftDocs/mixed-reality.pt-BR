---
title: Atualizando seu aplicativo SteamVR para a realidade mista do Windows
description: Práticas recomendadas para atualizar seu aplicativo SteamVR para maximizar o compatibilidade com headsets de realidade mista do Windows.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, compatibilidade
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548670"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a>Atualizando seu aplicativo SteamVR para a realidade mista do Windows

Incentivamos os desenvolvedores a testar e otimizar suas experiências de SteamVR para serem executadas em headsets de realidade mista do Windows. Esta documentação aborda os aprimoramentos comuns que os desenvolvedores podem fazer para garantir que sua experiência seja muito boa no Windows Mixed Reality.

## <a name="initial-setup-instructions"></a>Instruções de instalação inicial

Para começar a testar seu jogo ou aplicativo no Windows Mixed Reality, siga primeiro o nosso [Guia de introdução.](http://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>Modelos de controlador
1. Se seu aplicativo renderizar modelos de controlador:
    * Usar os [modelos de controlador de movimento do Windows Mixed Reality](motion-controllers.md#rendering-the-motion-controller-model)
    * Use IVRRenderModel:: getcomponentstate para obter transformações locais em partes de componente (por exemplo, Pose de ponteiro)
2. Experiências que têm uma noção de destromente devem obter dicas das APIs de entrada para diferenciar controladores [(exemplo de Unity)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Controles

Ao criar ou ajustar seu layout de controle, tenha em mente o seguinte conjunto de comandos reservados:
1. Ao clicar na **esquerda e à direita, a Thumbstick analógica** é reservada para o **painel de fluxo**.
2. O **botão Windows** sempre retornará os usuários para a página inicial do Windows Mixed Reality.

Se possível, por padrão, a teleportação baseada em Thumb Stick deve corresponder ao comportamento de teleportagem [inicial do Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)

## <a name="tooltips-and-ui"></a>Dicas de ferramenta e interface do usuário

Muitos jogos de VR aproveitam as dicas de ferramentas e sobreposições do controlador de movimento para ensinar aos usuários os comandos mais importantes para seu jogo ou aplicativo. Ao ajustar seu aplicativo para a realidade mista do Windows, é recomendável revisar essa parte da sua experiência para garantir que as dicas de ferramentas sejam mapeadas para os modelos do controlador do Windows.

Além disso, se houver pontos em sua experiência em que você exiba imagens dos controladores, certifique-se de fornecer imagens atualizadas usando os controladores de movimento do Windows Mixed Reality.

## <a name="haptics"></a>Haptics

A partir da [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md), o haptics agora tem suporte para experiências de SteamVR no Windows Mixed Reality. Se seu aplicativo ou jogo SteamVR já inclui suporte para haptics, ele agora deve funcionar (sem nenhum trabalho adicional) com os [controladores de movimento do Windows Mixed Reality](motion-controllers.md).

Os controladores de movimento do Windows Mixed Reality usam um motor haptics padrão, ao contrário dos acionadores lineares encontrados em alguns outros controladores de movimento SteamVR, o que pode levar a uma experiência de usuário um pouco diferente do esperado. Portanto, é recomendável testar e ajustar seu design haptics com os controladores de movimento do Windows Mixed Reality. Por exemplo, às vezes, os pulsos de Haptic curtos (5-10 ms) são menos perceptíveis em controladores de movimento de realidade mista do Windows. Para produzir um pulso mais perceptível, experimente enviar um "clique" mais longo (40-70ms) para dar ao motor mais tempo para ser girado antes de ser informado para desligar novamente.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Iniciando aplicativos SteamVR no menu Iniciar do Windows Mixed Reality

Para experiências de VR distribuídas por meio do vapor, [atualizamos a realidade mista do Windows para SteamVR beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) junto com os vôos do [Windows](https://insider.windows.com) Insider RS5 mais recentes para que os títulos de SteamVR agora apareçam no menu Iniciar do Windows Mixed realm em "todos os aplicativos" listar automaticamente. Com essas versões de software instaladas, os clientes agora podem iniciar títulos de SteamVR diretamente de dentro do Windows Mixed Reality Home sem remover seus headsets.

## <a name="windows-mixed-reality-logo"></a>Logotipo do Windows Mixed Reality

Para exibir o suporte à realidade mista do Windows para seu título, vá para o link "Editar página de repositório" na página de aterrissagem do aplicativo, clique na guia "informações básicas" e role para baixo até "realidade virtual". Desmarque a "ocultar realidade mista do Windows" e, em seguida, publique na loja.

## <a name="bugs-and-feedback"></a>Bugs e comentários

Seus comentários são inúteis quando se trata de melhorar a experiência de SteamVR do Windows Mixed Reality. Envie todos os comentários e bugs por meio do [Hub de comentários do Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback). Aqui estão algumas [dicas sobre como tornar seus comentários do SteamVR tão úteis quanto possível](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).

Se você tiver dúvidas ou comentários para compartilhar, também poderá entrar em contato conosco em nosso [Fórum de fluxo](http://steamcommunity.com/app/719950/discussions/).

## <a name="faqs-and-troubleshooting"></a>Perguntas frequentes e solução de problemas

Se você estiver executando problemas gerais Configurando ou jogando sua experiência, [Confira as etapas de solução de problemas mais recentes](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).

## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* [Histórico do driver do controlador do headset e do Motion](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Diretrizes mínimas de compatibilidade de hardware do PC do Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
