---
title: Contas no HoloLens
description: Como configurar e gerenciar contas de usuário no HoloLens.
author: tmlyon
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, usuário, conta, AAD, ADFS, conta da Microsoft, MSA, credenciais
ms.openlocfilehash: 5579cf53948b8bdbd4b41973dde7b8fc70a5aa31
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437089"
---
# <a name="accounts-on-hololens"></a>Contas no HoloLens

Durante a configuração inicial do HoloLens, os usuários precisam entrar com a conta que desejam usar no dispositivo. Essa conta pode ser uma conta Microsoft de consumidor ou uma conta empresarial configurada em Azure Active Directory (AAD) ou Serviços de Federação do Active Directory (AD FS) (ADFS).

Entrar nessa conta durante a instalação cria um perfil do usuário no dispositivo que o usuário pode usar para entrar e em que todos os aplicativos armazenarão seus dados. Essa mesma conta também fornece logon único para aplicativos como o Edge ou o Skype por meio das APIs do Gerenciador de contas do Windows.

Além disso, ao entrar em uma conta corporativa ou organizacional no dispositivo, ela também poderá aplicar a política de MDM (gerenciamento de dispositivo móvel), se configurada pelo administrador de ti.

Sempre que o dispositivo for reiniciado ou retomado do modo de espera, as credenciais dessa conta serão usadas para entrar novamente. Se a opção que impõe uma entrada explícita estiver habilitada em configurações, será necessário que o usuário digite suas credenciais novamente. Sempre que o dispositivo for reiniciado depois de receber e aplicar uma atualização do sistema operacional, será necessária uma entrada explícita.

## <a name="multi-user-support"></a>Suporte a vários usuários

>[!NOTE]
>O suporte a vários usuários requer o pacote comercial, pois esse é um recurso [do Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise) .

A partir da [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md), o HoloLens dá suporte a vários usuários de dentro do mesmo locatário do AAD. Para usar isso, você deve configurar o dispositivo inicialmente com uma conta que pertença à sua organização. Subsequentemente, outros usuários do mesmo locatário poderão entrar no dispositivo a partir da tela de entrada ou tocando no bloco do usuário no painel Iniciar para sair do usuário existente. 

Os aplicativos instalados no dispositivo estarão disponíveis para todos os outros usuários, mas cada um terá seus próprios dados e preferências de aplicativo. No entanto, remover um aplicativo também o removerá para todos os outros usuários. 

Você pode remover os usuários do dispositivo do dispositivo para recuperar espaço acessando Configurações > contas > outras pessoas. Isso também removerá todos os dados de aplicativo dos outros usuários do dispositivo. 

## <a name="linked-accounts"></a>Contas vinculadas

Em uma única conta de dispositivo, os usuários podem vincular credenciais de conta da Web adicionais para fins de acesso mais fácil em aplicativos (como a loja) ou para combinar o acesso a recursos pessoais e de trabalho, semelhante à versão de área de trabalho do Windows. A entrada em uma conta adicional dessa maneira não separa os dados do usuário criados no dispositivo, como imagens ou downloads. Depois que uma conta tiver sido conectada a um dispositivo, os aplicativos poderão usá-lo com sua permissão para reduzir a falta de entrada em cada aplicativo individualmente.

## <a name="using-single-sign-on-within-an-app"></a>Usando o logon único em um aplicativo

Como desenvolvedor de aplicativos, você pode aproveitar a existência de uma identidade conectada no HoloLens com as [APIs do Gerenciador de contas do Windows](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx), assim como faria em outros dispositivos Windows. Alguns exemplos de código para essas APIs estão disponíveis [aqui](https://go.microsoft.com/fwlink/p/?LinkId=620621).

Qualquer interrupção de conta que possa ocorrer, como solicitação de consentimento do usuário para informações de conta, autenticação de dois fatores etc., deve ser tratada quando o aplicativo solicita um token de autenticação.

Se seu aplicativo exigir um tipo de conta específico que não tenha sido vinculado anteriormente, seu aplicativo poderá solicitar que o sistema solicite ao usuário para adicionar um. Isso irá disparar o painel de configurações de conta para ser iniciado como um filho modal do seu aplicativo. Para aplicativos 2D, essa janela será renderizada diretamente sobre o centro do seu aplicativo e para aplicativos do Unity, isso fará com que o usuário saia do seu aplicativo Holographic para que essa janela filho possa ser renderizada. A personalização dos comandos e ações neste painel é descrita [aqui](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx).

## <a name="enterprise-and-other-authentication"></a>Enterprise e outras autenticações

Se seu aplicativo usa outros tipos de autenticação, como NTLM, básico ou Kerberos, você pode usar a [interface do usuário da credencial do Windows](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx) para coletar, processar e armazenar as credenciais do usuário. A experiência do usuário para coletar essas credenciais é muito semelhante a outras interrupções de conta voltadas para a nuvem e aparecerá como um aplicativo filho sobre seu aplicativo 2D ou suspenderá brevemente um aplicativo de Unity para mostrar a interface do usuário.

## <a name="deprecated-apis"></a>APIs preteridas

Uma diferença para o desenvolvimento no HoloLens da área de trabalho é que a API [OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) não tem suporte total. Embora ele retorne um token se a conta principal estiver em boas condições, as interrupções, como as descritas acima, não exibirão nenhuma interface do usuário e não conseguirão autenticar corretamente a conta.

