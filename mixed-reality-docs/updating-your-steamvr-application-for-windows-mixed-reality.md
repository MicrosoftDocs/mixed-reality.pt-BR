---
title: Atualizar seu aplicativo SteamVR para Windows Mixed Reality
description: Práticas recomendadas para atualizar seu aplicativo SteamVR para maximizar a compatibilidade com headsets realidade mista do Windows.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, compatibilidade
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589143"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a>Atualizar seu aplicativo SteamVR para Windows Mixed Reality

Incentivamos os desenvolvedores para testar e otimizar suas experiências SteamVR para ser executado no headsets realidade mista do Windows. Esta documentação aborda os aprimoramentos comuns que os desenvolvedores podem fazer para garantir que sua experiência perfeita execução no Windows Mixed Reality.

## <a name="initial-setup-instructions"></a>Instruções de configuração inicial

Para começar a testar seu jogo ou aplicativo na marca Windows Mixed Reality claro para primeiro siga nosso [guia de Introdução.](http://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>Modelos de controlador
1. Se seu aplicativo processa modelos de controlador:
    * Use o [modelos de controlador de movimento de realidade mista do Windows](motion-controllers.md#rendering-the-motion-controller-model)
    * Transforma IVRRenderModel::GetComponentState de uso para obter o local para as partes do componente (por exemplo. Ponteiro pose)
2. Experiências que tem uma noção de destro/canhoto devem obter dicas de APIs para diferenciar os controladores de entrada [(exemplo da Unity)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Controles

Ao projetar o ou ajustando o layout do controle tenha em mente o seguinte conjunto de comandos reservados:
1. Clicando em busca de **analógico esquerdo e direito analógico** é reservado para o **Steam painel**.
2. O **botão Windows** sempre retornará os usuários para o Windows Mixed Reality inicial.

Se possível, o padrão para thumb pen drive com base em teleportation para corresponder a [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation comportamento

## <a name="tooltips-and-ui"></a>Dicas de ferramenta e a interface do usuário

Muitos jogos VR tirar proveito das dicas de ferramenta de controlador de animação e sobreposições de ensinar os usuários os comandos mais importantes para seu jogo ou aplicativo. Ao ajustar seu aplicativo de realidade mista do Windows, é recomendável revisar essa parte da sua experiência para garantir que as dicas de ferramenta mapeiam para os modelos de controlador do Windows.

Além disso se não houver todos os pontos em sua experiência em que você pode exibir imagens dos controladores Certifique-se de fornecer imagens atualizadas usando os Windows Mixed Reality movimento controladores.

## <a name="haptics"></a>Haptics

Começando com o [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md), haptics agora têm suporte para SteamVR experiências em realidade mista do Windows. Se seu aplicativo SteamVR ou jogo já inclui suporte para haptics, ele agora deve funcionar (sem nenhum trabalho adicional) com [controladores de movimento do Windows Mixed Reality](motion-controllers.md).

Os controladores de movimento de realidade mista do Windows usam um motor de haptics padrão, em vez dos acionadores lineares encontrado em alguns outros SteamVR movimento controladores, que podem levar a uma experiência do usuário ligeiramente diferente que o esperado. Portanto, é recomendável testar e ajustar seu design haptics com controladores de movimento de realidade mista do Windows. Por exemplo, os pulsos hápticos, às vezes, curtos (5 a 10 ms) são menos perceptíveis em controladores de movimento de realidade mista do Windows. Para produzir um pulso mais perceptível, fazer experiências com o envio de um maior "clique" (40 70ms) para dar mais tempo para acelerar o motor antes de ser informado para power off novamente.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Iniciando aplicativos SteamVR no menu Iniciar de realidade mista do Windows

Para experiências VR distribuídas por meio do fluxo, temos [atualizado com o Windows Mixed Reality SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) junto com a versão mais recente [Windows Insider](https://insider.windows.com) RS5 voos para que os títulos de SteamVR agora aparecem no Menu Iniciar de realidade mista do Windows em "todos os aplicativos" Listar automaticamente. Com essas versões de software instaladas, os clientes agora podem iniciar títulos de SteamVR diretamente de dentro do Windows Mixed Reality doméstica sem remover os fones de ouvido.

## <a name="windows-mixed-reality-logo"></a>Logotipo do Windows Mixed Reality

Para exibir o suporte a Windows Mixed Reality seu título, acesse o link "Editar página de Store" em sua página de aterrissagem do aplicativo, clique na guia "Informações básicas" e role para baixo até "Virtual Reality". Desmarque o "Ocultar Windows Mixed Reality" e, em seguida, publicar para o armazenamento.

## <a name="bugs-and-feedback"></a>Bugs e comentários

Sua opinião é valiosa quando se trata de melhorar a experiência do Windows SteamVR de realidade mista. Envie todas as opiniões e bugs por meio de [Hub de comentários do Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback). Aqui estão alguns [dicas sobre como fazer seus comentários SteamVR tão útil quanto possível](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).

Se você tiver perguntas ou comentários para compartilhar, você pode também entrar em contato conosco em nossa [Fórum do Steam](http://steamcommunity.com/app/719950/discussions/).

## <a name="faqs-and-troubleshooting"></a>Perguntas frequentes e solução de problemas

Se você estiver com problemas gerais de configuração ou a reprodução de sua experiência [Confira as etapas de solução de problemas mais recentes](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).

## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* [Histórico de driver de controlador de fone de ouvido e movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Diretrizes de compatibilidade de hardware do Windows Mixed Reality mínimas PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
