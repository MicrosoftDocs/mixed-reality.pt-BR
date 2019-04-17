---
title: Contas em HoloLens
description: Como configurar e gerenciar contas de usuário no HoloLens.
author: ''
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, user, account, aad, adfs, microsoft account, msa, credentials
ms.openlocfilehash: 14f43b08b6ccb396bcf39c4082c840c65ac78cf9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589538"
---
# <a name="accounts-on-hololens"></a>Contas em HoloLens

Durante a instalação inicial do HoloLens, os usuários precisarão entrar com a conta que deseja usar no dispositivo. Essa conta pode ser uma conta de consumidor da Microsoft ou uma conta da empresa que tenha sido configurada no Azure Active Directory (AAD) ou serviços de Federação do Active Directory (ADFS).

Entrar nessa conta durante a instalação cria um perfil de usuário no dispositivo que o usuário pode usar para entrar, e em relação a quais todos os aplicativos serão armazenam seus dados. Essa mesma conta também fornece logon único para aplicativos como o Skype por meio das APIs do Gerenciador de contas do Windows ou de borda.

Além disso, ao entrar em uma empresa ou conta organizacional no dispositivo, ele pode também se aplicam a política de gerenciamento de dispositivo móvel (MDM), se configurado pelo administrador de TI.

Sempre que o dispositivo é reiniciado ou sai do modo de espera, as credenciais dessa conta são usadas para entrar novamente. Se a opção de imposição de uma entrada explícita está habilitada nas configurações, o usuário será necessário digitar novamente suas credenciais. Sempre que o dispositivo for reiniciado depois de receber e aplicar uma atualização do sistema operacional, uma entrada explícita é necessária.

## <a name="multi-user-support"></a>Suporte a vários usuários

>[!NOTE]
>Suporte a vários usuários exige o Commercial Suite, pois essa é uma [Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise) recurso.

Começando com o [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md), HoloLens dá suporte a vários usuários de dentro do mesmo locatário do AAD. Para usá-la, você deve configurar o dispositivo inicialmente com uma conta que pertence à sua organização. Subsequentemente, outros usuários do mesmo locatário será capazes de entrar no dispositivo na tela de entrada ou tocando no bloco do usuário no painel de início para desconectar o usuário existente. 

Aplicativos instalados no dispositivo estará disponíveis para todos os outros usuários, mas cada uma terá seus próprios dados de aplicativo e preferências. Remover um aplicativo também removerá todos os outros usuários no entanto. 

Você pode remover usuários de dispositivo do dispositivo para recuperar espaço Acessando configurações > contas > outras pessoas. Isso também removerá todos os dados de aplicativo a outros usuários do dispositivo. 

## <a name="linked-accounts"></a>Contas vinculadas

Em uma conta de dispositivo único, os usuários podem vincular as credenciais da conta da web adicionais com a finalidade de facilitar o acesso dentro de aplicativos (por exemplo, a Store) ou para combinar o acesso aos recursos pessoais e de trabalho, semelhantes à versão da área de trabalho do Windows. Entrar em uma conta adicional dessa maneira não separa os dados de usuário criados no dispositivo, como imagens ou baixa. Depois que uma conta tiver sido conectada a um dispositivo, os aplicativos possam fazer usá-lo com sua permissão para reduzir a necessidade de entrar em cada aplicativo individualmente.

## <a name="using-single-sign-on-within-an-app"></a>Usando o logon único dentro de um aplicativo

Como desenvolvedor de aplicativos, você pode tirar proveito de ter uma identidade conectada no HoloLens com o [APIs do Gerenciador de conta do Windows](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx), assim como você faria em outros dispositivos do Windows. Alguns exemplos de código para essas APIs estão disponíveis [aqui](http://go.microsoft.com/fwlink/p/?LinkId=620621).

Quaisquer interrupções de conta que podem ocorrer como usuário solicitante consentimento para informações de conta, a autenticação de dois fatores etc. deve ser tratada quando o aplicativo solicita um token de autenticação.

Se seu aplicativo requer um tipo de conta específica que ainda não foi vinculado anteriormente, seu aplicativo pode pedir que o sistema solicitar que o usuário para adicionar um. Isso disparará o painel de configurações de conta para ser iniciado como um filho modal do aplicativo. Para aplicativos 2D, esta janela será renderizado diretamente sobre o centro do seu aplicativo e para aplicativos do Unity, isso brevemente levará o usuário fora do seu aplicativo holographic para que essa janela filho pode ser renderizada. Personalizar os comandos e ações nesse painel é descrito [aqui](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx).

## <a name="enterprise-and-other-authentication"></a>Enterprise e outra autenticação

Se seu aplicativo faz uso de outros tipos de autenticação, como NTLM, Basic ou Kerberos, você pode usar [interface do usuário do Windows Credential](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx) para coletar, processar e armazenar as credenciais do usuário. A experiência do usuário para coletar essas credenciais é muito semelhante de outra nuvem controlado por interrupções de conta e aparecerão como um aplicativo filho na parte superior de seu aplicativo 2D ou suspender rapidamente um aplicativo do Unity para mostrar a interface do usuário.

## <a name="deprecated-apis"></a>APIs preteridas

Uma diferença para o desenvolvimento no HoloLens da área de trabalho é que [OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) API não tem suporte total. Embora ele retornará que um token se a conta principal estiver em bem posicionado, interrompe, como as descritas acima não exibirá nenhuma interface do usuário para o usuário e falharão ao autenticar corretamente a conta.

