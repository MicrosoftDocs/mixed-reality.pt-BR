---
title: Notas de versão – abril de 2018
description: Notas de versão do HoloLens e do Windows Mixed Reality para a atualização do Windows 10 de abril de 2018 (também conhecida como RS4).
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: notas de versão, versão, Windows 10, Build, RS4, so
ms.openlocfilehash: 1fc1b43b0581234e835379fd553b78121108086e
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524179"
---
# <a name="release-notes---april-2018"></a>Notas de versão – abril de 2018

A **[atualização do Windows 10 de abril de 2018](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (também conhecida como RS4) inclui novos recursos para os fones de ouvido de imersão de realidade mista do Windows e do HoloLens conectados aos PCs. 

Para atualizar para a versão mais recente de qualquer tipo de dispositivo, abra o aplicativo **configurações** , vá para **atualização & segurança**e, em seguida, selecione o botão **verificar atualizações** . Em um PC com Windows 10, você também pode instalar manualmente a atualização do Windows 10 de abril de 2018 usando a [ferramenta de criação de mídia do Windows](https://www.microsoft.com/software-download/windows10).

**Versão mais recente do desktop:** Atualização de abril de 2018 do Windows 10 (**10.0.17134.1**)<br>
**Versão mais recente para o HoloLens:** Atualização de abril de 2018 do Windows 10 (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Uma mensagem de Alex Kipman e visão geral dos novos recursos de realidade misturada na atualização do Windows 10 de abril de 2018*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Novos recursos para os headsets de imersão de realidade mista do Windows

A atualização do Windows 10 de abril de 2018 inclui vários aprimoramentos para o uso de fones de ouvido (VR) de realidade mista do Windows com seu PC desktop, como: 

* **Novos ambientes para a realidade misturada** – agora você pode escolher entre a casa Cliff e o novo ambiente Skyloft selecionando **locais** no menu iniciar. Também adicionamos [um recurso experimental](add-custom-home-environments.md) que permitirá que você use ambientes personalizados que você criou.
* **Acesso rápido à captura de realidade mista** – agora você pode pegar fotos de realidade misturadas usando um controlador de movimento. Mantenha o botão do Windows pressionado e toque no gatilho. Isso funciona em ambientes e aplicativos, mas não capturará conteúdo protegido com DRM.
* **Novas opções para iniciar e redimensionar conteúdo** – aplicativos agora são automaticamente colocados na frente quando você os inicia no menu iniciar. Agora, você também pode redimensionar aplicativos 2D arrastando as bordas e os cantos da janela.
* **Vá facilmente para o conteúdo com o comando de voz "teleport"** – agora você pode teleport rapidamente para estar na frente do conteúdo do Windows Mixed Reality Home por nuvens no conteúdo e dizendo "teleport".
* Iniciadores de  **[aplicativos 3D animados](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#animation-guidelines) e [objetos 3D decorativos](enable-placement-of-3d-models-in-the-home.md) para a realidade misturada** – agora você pode adicionar animação a iniciadores de aplicativos 3D e permitir que os usuários coloquem modelos 3D decorativos de uma página da Web ou de um aplicativo 2D na Home real do Windows Mixed.
* **[Melhorias na realidade mista do Windows para SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md)** – a realidade mista do Windows para SteamVR está fora de "acesso antecipado" com novas atualizações, incluindo: Comentários de Haptic ao usar controladores de movimento, melhor desempenho e confiabilidade e melhorias no aparência dos controladores de movimento no SteamVR.
* **Outros aprimoramentos** – as configurações de desempenho automático foram atualizadas para fornecer uma experiência mais otimizada (você pode [substituir manualmente](#visual-quality) essa configuração). Agora, a instalação fornece informações mais detalhadas sobre problemas comuns de compatibilidade com placas gráficas e controladores USB 3,0.

## <a name="new-features-for-hololens"></a>Novos recursos para o HoloLens

A atualização do Windows 10 de abril de 2018 chegou a todos os clientes do HoloLens! Essa atualização é empacotada com melhorias que foram introduzidas desde a última versão principal do software do HoloLens em [agosto de 2016](release-notes-august-2016.md).

### <a name="for-everyone"></a>Para todos

<table>
  <tr>
    <th>Recurso</th><th>Detalhes</th><th>Instruções</th>
  </tr>
  <tr>
    <td>Colocação automática de conteúdo 2D e 3D na inicialização</td><td>Um inicializador de aplicativo 2D ou os locais automáticos do aplicativo UWP 2D no mundo em um tamanho ideal e uma distância quando são iniciados em vez de exigir que o usuário o coloque. Se um <a href="app-views.md">aplicativo de imersão</a> usar um inicializador de aplicativo 2D em vez de um iniciador de <a href="3d-app-launcher-design-guidance.md">aplicativo 3D</a>, o aplicativo de imersão será iniciado automaticamente a partir do inicializador de aplicativo 2D, como no RS1.<br><br>Um inicializador de aplicativo 3D do menu iniciar também é colocado automaticamente no mundo. Em vez de iniciar o aplicativo automaticamente, os usuários podem clicar no iniciador para iniciar o aplicativo de imersão. o conteúdo 3D aberto do aplicativo hologramas e do Edge também é colocado automaticamente no mundo.</td><td>Ao abrir um aplicativo no menu Iniciar, você não será mais solicitado a colocá-lo no mundo.<br><br>Se o posicionamento do iniciador do aplicativo 2D/<a href="3d-app-launcher-design-guidance.md">3D</a> não for o ideal, você poderá movê-los facilmente usando as novas manipulações de aplicativos fluidos descritas abaixo. Você também pode reposicionar o conteúdo do inicializador/3D do aplicativo 2D dizendo "mover isso" e, em seguida, usando olhar para reposicionar o conteúdo.</td>
  </tr>
  <tr>
    <td>Manipulação de aplicativos fluidos</td><td>Mova, redimensione e gire conteúdo 2D e 3D sem precisar inserir o modo de "ajuste".</td><td>Para mover um aplicativo UWP 2D ou inicializador de aplicativo 2D, basta olhar na sua barra de aplicativo e, em seguida, use o gesto de toque + reter + arrastar. Você pode mover o conteúdo 3D de nuvens em qualquer lugar no objeto e, em seguida, usando tocar + manter + arrastar.<br><br>Para redimensionar o conteúdo 2D, olhar em seu canto. O cursor olhar se transforma em um cursor de redimensionamento e, em seguida, você pode tocar em + Hold + arrastar para redimensionar. Você também pode tornar o conteúdo 2D mais alto ou mais largo examinando suas bordas e arrastando.<br><br>Para redimensionar o conteúdo 3D, levante o quadro do gesto de mãos para cima na posição pronta. Você verá que o cursor se transforma em um estado com duas pequenas mãos. Faça o gesto de tocar e segurar com as duas mãos. Ao mover suas mãos de perto ou de distância, você alterará o tamanho do objeto. Mover suas mãos para frente e para trás em relação umas às outras irá girar o objeto. Você também pode redimensionar/girar o conteúdo 2D dessa maneira.</td>
  </tr>
  <tr>
    <td>redimensionamento horizontal do aplicativo 2D com refluxo</td><td>Torne um aplicativo UWP 2D mais amplo na taxa de proporção para ver mais conteúdo do aplicativo. Por exemplo, tornando o aplicativo de email amplo o suficiente para mostrar o painel de visualização.</td><td>Simplesmente olhar na borda esquerda ou direita do aplicativo UWP 2D para ver o cursor de redimensionamento e, em seguida, use o gesto de toque + reter + arrastar para redimensionar.</td>
  </tr>
  <tr>
    <td>Suporte expandido a comandos de voz</td><td>Você pode fazer mais simplesmente usando sua voz.</td><td>Experimente estes comandos de voz:<ul><li>"Ir para o início" – exibe o menu iniciar ou sai de um <a href="app-views.md">aplicativo de imersão</a>.</li><li>"Mover isso" – permite que você mova um objeto.</li></ul></td>
  </tr>
  <tr>
    <td>Aplicativos de holograma e fotos atualizados</td><td>Aplicativo de hologramas atualizado com novos hologramas. Aplicativo de fotos atualizado.</td><td>Você perceberá uma aparência atualizada para os aplicativos hologramas e fotos. O aplicativo hologramas inclui vários hologramas novos e um criador de rótulo para facilitar a criação de texto.</td>
  </tr>
  <tr>
    <td>Captura de realidade misturada aprimorada</td><td>Atalho de hardware início e fim vídeo da MRC.</td><td>Mantenha o volume pressionado + Down por 3 segundos para começar a gravar o vídeo da MRC. Toque duas vezes ou use o gesto de cair para terminar.</td>
  </tr>
  <tr>
    <td>Espaços consolidados</td><td>Simplifique o gerenciamento de espaço para hologramas em um único espaço.</td><td>O HoloLens localiza seu espaço automaticamente e não exige mais que você gerencie ou selecione espaços. Se você tiver problemas com os hologramas em seu lugar, poderá ir para <b>configurações > sistema > hologramas > remover hologramas próximos</b>. Se necessário, você também pode selecionar <b>remover todos os hologramas</b>.</td>
  </tr>
  <tr>
    <td>Imersão de áudio aprimorado</td><td>Agora você pode ouvir o HoloLens melhor em ambientes com ruído e experimentar mais som realista de aplicativos, pois seu som será obscurecido por paredes reais detectadas pelo dispositivo.</td><td>Você não precisa fazer nada para aproveitar o som espacial melhorado.</td>
  </tr>
  <tr>
    <td>Explorador de Arquivos</td><td>Mova e exclua arquivos de dentro do HoloLens.</td><td>Você pode usar o aplicativo <b>Explorador de arquivos</b> para mover e excluir arquivos de dentro do HoloLens.<br><br><b>Dica:</b> Se você não vir nenhum arquivo, o filtro "recente" pode estar ativo (o ícone de relógio é realçado no painel esquerdo). Para corrigir, selecione o ícone este documento de <b>dispositivo</b> no painel esquerdo (abaixo do ícone de relógio) ou abra o menu e selecione <b>este dispositivo</b>.
</td>
  </tr>
  <tr>
    <td>Suporte a MTP (protocolo de transferência de mídia)</td><td>Permite que seu PC desktop acesse suas bibliotecas (fotos, vídeos, documentos) no HoloLens para fácil transferência.</td><td>Semelhante a outros dispositivos móveis, conecte seu HoloLens ao seu PC para exibir o <b>Explorador de arquivos</b> para acessar suas bibliotecas de hololens (fotos, vídeos, documentos) para facilitar a transferência.<br><br><b>Sobre</b><ul><li>Se você não vir nenhum arquivo, certifique-se de entrar no seu HoloLens para habilitar o acesso aos seus dados.</li><li>No <b>Explorador de arquivos</b> do seu computador, você pode selecionar <b>as propriedades do dispositivo</b> para ver o número de versão do sistema operacional Windows Holographic (versão do firmware) e o número de série do dispositivo.</li></ul><b>Problema conhecido:</b> Renomear o HoloLens por meio do <b>Explorador de arquivos</b> em seu computador não está habilitado.</td>
  </tr>
  <tr>
    <td>Suporte de rede do portal cativo durante a instalação</td><td>Agora você pode configurar seu HoloLens em uma rede de convidados em hotéis, centros de conferências, lojas de varejo ou empresas que usam o portal cativo.</td><td>Durante a instalação, selecione a rede, marque conectar automaticamente se desejar e insira as informações de rede conforme solicitado.</td>
  </tr>
  <tr>
    <td>Foto e sincronização de vídeo por meio do aplicativo OneDrive</td><td>Suas fotos e vídeos do HoloLens agora serão sincronizados por meio do aplicativo OneDrive da Microsoft Store em vez de diretamente por meio do aplicativo de fotos.</td><td>Para configurar isso, baixe e inicie o aplicativo OneDrive da loja. Na primeira execução, você deve ser solicitado a carregar automaticamente suas fotos no OneDrive ou pode encontrar a opção nas configurações do aplicativo.</td>
  </tr>
</table>

### <a name="for-developers"></a>Para desenvolvedores

<table>
  <tr>
    <th>Recurso</th><th>Detalhes</th><th>Instruções</th>
  </tr>
  <tr>
    <td>Melhorias de mapeamento espacial</td><td>Melhorias de qualidade, simplificação e desempenho.</td><td>A malha de mapeamento espacial aparecerá mais limpa – é necessário um número menor de triângulos para representar o mesmo nível de detalhe. Você pode notar alterações na densidade do triângulo na cena.</td>
  </tr>
  <tr>
    <td>Seleção automática de ponto de foco com base no buffer de profundidade</td><td>O envio de um buffer de profundidade ao Windows permite que o HoloLens selecione um ponto de foco automaticamente para otimizar a estabilidade do holograma.</td><td>No Unity, vá para <b>Editar configurações de projeto > > Player > plataforma universal do Windows guia > XR Settings</b>, expanda o item <b>SDK do Windows Mixed Reality</b> e verifique se <b>habilitar o compartilhamento de buffer de profundidade</b> está marcado. Isso será automaticamente verificado em busca de novos projetos.<br><br>Para aplicativos do DirectX, certifique-se de chamar o método <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a> em <b>HolographicRenderingParameters</b> cada quadro para fornecer o buffer de profundidade ao Windows.
</td>
  </tr>
  <tr>
    <td>Modos de Reprojeção do Holographic</td><td>Agora você pode desabilitar a Reprojeção posicional no HoloLens para melhorar a estabilidade do holograma de conteúdo com bloqueio de corpo rígido, como vídeo de 360 graus.</td><td>No Unity, defina <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings.</a> reprojemode como <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode. OrientationOnly</a> quando todo o conteúdo na exibição for um corpo rigidamente bloqueado.<br><br>Para aplicativos do DirectX, defina <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode">HolographicCameraRenderingParameters.</a> reprojemode como <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode. OrientationOnly</a> quando todo o conteúdo na exibição estiver com rigidez de corpo-bloqueado.</td>
  </tr>
  <tr>
    <td>APIs de personalização de aplicativo</td><td>As APIs do Windows sabem mais sobre onde seu aplicativo está em execução, como se a exibição do dispositivo é transparente (HoloLens) ou opaco (Headset de imersão) e se a exibição 2D do aplicativo UWP está aparecendo no Shell Holographic.</td><td>O Unity anteriormente expôs <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings. IsDisplayOpaque</a> de uma maneira que funcionou antes dessa compilação.<br><br>Para aplicativos do DirectX, agora você pode acessar APIs existentes como <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay. GetDefault (). Isopaco</a> e <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview. IsCurrentViewPresentedOnHolographicDisplay</a> no HoloLens também.
</td>
  </tr>
  <tr>
      <td>Modo de pesquisa</td><td>Permite que os desenvolvedores acessem os principais sensores do HoloLens ao criar aplicativos acadêmicos e industriais para testar novas ideias nos campos de visão do computador e robótica, incluindo:<ul><li>As quatro câmeras de acompanhamento de ambiente</li><li>Duas versões do mapeamento de profundidade dados da câmera</li><li>Duas versões de um fluxo IR-reflectivity</li></ul></td><td><a href="research-mode.md">Documentação do modo de pesquisa</a><br><a href="https://github.com/Microsoft/HoloLensForCV">Aplicativos de exemplo do modo de pesquisa</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>Para clientes comerciais

<table>
  <tr>
    <th>Recurso</th><th>Detalhes</th><th>Instruções</th>
  </tr>
  <tr>
    <td>Usar várias contas de usuário Azure Active Directory em um único dispositivo</td><td>Compartilhe um HoloLens com vários usuários do Azure AD, cada um com suas próprias configurações de usuário e dados de usuário no dispositivo.</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">Centro de profissionais de ti: Compartilhar o HoloLens com várias pessoas</a></td>
  </tr>
  <tr>
    <td>Alterar a rede Wi-Fi ao entrar</td><td>Altere a rede Wi-Fi antes de entrar para permitir que outro usuário entre com sua conta de usuário do Azure AD pela primeira vez, permitindo que os usuários compartilhem dispositivos em vários locais e sites de trabalho.</td><td>Na tela de entrada, você pode usar o ícone de rede abaixo do campo senha para se conectar a uma rede. Isso é útil quando esta é a primeira vez que se conecta a um dispositivo.</td>
  </tr>
  <tr>
    <td>Registro unificado</td><td>Agora, é fácil para um usuário do HoloLens que configure o dispositivo com um conta Microsoft pessoal para adicionar uma conta corporativa (Azure AD) e ingressar o dispositivo em seu servidor MDM.</td><td>Basta entrar com uma conta do Azure AD e o registro ocorrerá automaticamente.</td>
  </tr>
  <tr>
    <td>Sincronização de email sem registro de MDM</td><td>Suporte para sincronização de email Exchange Active Sync (EAS) sem a necessidade de registro de MDM.</td><td>Agora você pode sincronizar emails sem registro no MDM. Você pode configurar o dispositivo com uma conta da Microsoft, baixar e instalar o aplicativo de email e adicionar uma conta de email de trabalho diretamente.</td>
  </tr>
</table>

### <a name="for-it-pros"></a>para profissionais de TI

<table>
  <tr>
    <th>Recurso</th><th>Detalhes</th><th>Instruções</th>
  </tr>
  <tr>
    <td>Novo nome do sistema operacional "Windows Holographic for Business"</td><td>Limpe a nomenclatura de edição para reduzir a confusão no aplicativo de licença de atualização de edição quando os recursos do pacote comercial estiverem habilitados no HoloLens.</td><td>Você pode ver qual edição do Windows Holographic está em seu dispositivo em <b>configurações > > do sistema</b>. "Windows Holographic for Business" será exibido se uma atualização de edição tiver sido aplicada para habilitar os recursos do pacote comercial. Saiba como <a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">desbloquear os recursos do Windows Holographic for Business</a>.</td>
  </tr>
  <tr>
  <td>Windows Configuration designer (WCD)</td><td>Crie e edite pacotes de provisionamento para configurar o HoloLens por meio do aplicativo WCD atualizado. Assistente de HoloLens simples para atualização de edição, OOBE configurável, região/fuso horário, token em massa do Azure AD, rede e CSP do desenvolvedor. Editor avançado filtrado para as opções com suporte do HoloLens, incluindo o acesso atribuído e os CSPs de gerenciamento de conta.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">Centro de profissionais de ti: Configurar o HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
    <td>Configuração configurável (OOBE)</td><td>Ocultar a calibragem, treinamento de gesto/olhar e telas de configuração de Wi-Fi durante a instalação.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">Centro de profissionais de ti: Configurar o HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
    <td>Suporte a token em massa do Azure AD</td><td>Pré-Registre o dispositivo no locatário do diretório do Azure AD para um fluxo de instalação de usuário mais rápido.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">Centro de profissionais de ti: Configurar o HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
  <td>CSP DeveloperSetup</td><td>Implante o perfil para configurar o HoloLens no modo de desenvolvedor. Útil para dispositivos de desenvolvimento e demonstração.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">Centro de profissionais de ti: Configurar o HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
  <td>CSP AccountManagement</td><td>Compartilhe um dispositivo HoloLens e remova os dados do usuário após os limites de saída ou de inatividade/armazenamento para uso temporário. Dá suporte a contas do Azure AD.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">Centro de profissionais de ti: Configurar o HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
  <td>Acesso atribuído</td><td>Acesso atribuído ao Windows para trabalhadores de primeira linha ou demonstrações. Bloqueio de um ou vários aplicativos. Não é necessário desbloquear o desenvolvedor.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">Centro de profissionais de ti: Configurar o HoloLens no modo de quiosque</a></td>
  </tr>
  <tr>
  <td>Acesso de convidado para dispositivos de quiosque</td><td>Acesso atribuído ao Windows com conta de convidado sem senha para demonstrações. Bloqueio de um ou vários aplicativos. Não é necessário desbloquear o desenvolvedor.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">Centro de profissionais de ti: Configurar o HoloLens no modo de quiosque</a></td>
  </tr>
  <tr>
    <td>Diagnóstico de configuração (OOBE)</td><td>Obtenha logs de diagnóstico do HoloLens para que você possa solucionar problemas de falhas de entrada do Azure AD (antes que o Hub de comentários esteja disponível para o usuário cuja entrada falhou).</td><td>Quando a instalação ou a entrada falhar, escolha a nova opção <b>coletar informações</b> para obter os logs de diagnóstico para solução de problemas.</td>
  </tr>
  <tr>
    <td>Expiração de senha indefinida de conta local</td><td>Remova a interrupção da redefinição do dispositivo quando a senha da conta local expirar.</td><td>Ao provisionar uma conta local, você não precisa mais alterar a senha a cada 42 dias nas <b>configurações</b>, pois a senha da conta não expira mais.</td>
  </tr>
  <tr>
    <td>Status e detalhes da sincronização de MDM</td><td>A funcionalidade padrão do Windows para entender o status de sincronização do MDM e detalhes de dentro do HoloLens.</td><td>Você pode verificar o status de sincronização do MDM de um dispositivo em <b>configurações > contas > acessar informações de > corporativa ou de estudante</b>. Na seção <b>status<b> de sincronização do dispositivo, você pode iniciar uma sincronização, ver áreas gerenciadas pelo MDM e criar e exportar um relatório de diagnóstico avançado.</td>
  </tr>
</table>

## <a name="known-issues"></a>Problemas conhecidos

Trabalhamos duro para fornecer uma ótima experiência de realidade mista do Windows, mas ainda estamos acompanhando alguns problemas conhecidos. Se você encontrar outras pessoas, envie [-nos seus comentários](give-us-feedback.md).

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>Após a atualização

Você pode observar os seguintes problemas após a atualização do RS1 para o RS4 em seu HoloLens:
* **Pins** redefinidos-os aplicativos de 3x3 fixados ao menu iniciar serão redefinidos para os padrões após a atualização. 
* Os **aplicativos e os hologramas colocados** redefinidos – os aplicativos colocados em seu mundo serão removidos após a atualização e precisarão ser colocados novamente em todo o seu espaço. 
* O **Hub de comentários pode não iniciar imediatamente** -imediatamente após a atualização, levará alguns minutos para que você possa iniciar alguns aplicativos de caixa de entrada, como o Hub de comentários, enquanto eles se atualizam. 
* Os **certificados Wi-Fi corporativos precisam ser** ressincronizados-estamos investigando um problema que exige que o HoloLens esteja conectado a uma rede diferente para que os certificados corporativos sejam sincronizados novamente com o dispositivo antes que seja capaz de se reconectar à empresa redes que usam certificados. 
* A **reprodução de vídeo h. 265 HEVC não funciona** – os aplicativos que tentam reproduzir o H. 265 vídeos receberão uma mensagem de erro. A solução alternativa é [acessar o portal do dispositivo Windows](using-the-windows-device-portal.md), selecionar **aplicativos** na barra de navegação à esquerda e **remover** o aplicativo HEVC. Em seguida, instale a [extensão de vídeo HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) mais recente do Microsoft Store. Estamos investigando o problema. 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>Para desenvolvedores: Atualizando aplicativos do HoloLens para dispositivos que executam a atualização do Windows 10 de abril de 2018

Junto com uma excelente lista de [novos recursos](#new-features-for-hololens), a atualização do Windows 10 de abril de 2018 (RS4) para o HoloLens impõe alguns comportamentos de código que as versões anteriores não:
* **Solicitações de permissão para usar recursos confidenciais (câmera, microfone, etc.)** -RS4 no HoloLens irá impor solicitações de permissão para aplicativos que pretendem acessar recursos confidenciais, como a câmera ou o microfone. RS1 no HoloLens não forçava esses prompts; portanto, se seu aplicativo assumir o acesso imediato a esses recursos, ele poderá falhar no RS4 (mesmo se o usuário conceder permissão para o recurso solicitado). Leia o [artigo declarações de capacidade de aplicativo UWP](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) relevantes para obter mais informações.
* **Chamadas para aplicativos fora do seu próprio** -RS4 no HoloLens impedirão o uso adequado da [classe *Windows. System. Launcher* ](https://docs.microsoft.com/uwp/api/Windows.System.Launcher) para iniciar outro aplicativo por conta própria. Por exemplo, vimos problemas com aplicativos chamando *Windows. System. Launcher. LaunchUriForResultsAsync* de um thread não Asta (IU). Isso teria sucesso em RS1 no HoloLens, mas o RS4 exige que a chamada fosse executada no thread da interface do usuário.

### <a name="windows-mixed-reality-on-desktop"></a>Realidade mista do Windows no desktop

#### <a name="visual-quality"></a>Qualidade visual

* Se você observar após a atualização do Windows 10 de abril de 2018 que os gráficos são mais desfocados do que antes, ou que o campo de exibição parece menor no headset, a configuração de desempenho automático pode ter sido alterada para manter uma taxa de quadros suficiente de forma menos eficiente placa gráfica (como NVIDIA 1050). Você pode substituir manualmente isso (se escolher) navegando até **configurações > realidade misturada > exibição de Headset > opções de experiência > alterar** e alterar "automático" para "90 Hz". Você também pode tentar alterar a **qualidade visual** (na mesma página Configurações) para "alta".

#### <a name="windows-mixed-reality-setup"></a>Configuração do Windows Mixed Reality

* Ao configurar o Windows com um headset conectado, o monitor do PC pode ficar em branco. Desconecte seu headset para habilitar a saída para o monitor do seu PC para concluir a instalação do Windows.
* Se você não tiver fones de ouvido conectados, poderá perder dicas adicionais ao visitar pela primeira vez o Windows Mixed Reality Home.
* Outros dispositivos Bluetooth podem causar interferências com os controladores de movimento. Se os controladores de movimento tiverem problemas de conexão/emparelhamento/controle, verifique se o rádio Bluetooth (se um dongle externo) está conectado a um local inobstruído e não imediatamente ao lado de outro Dongle Bluetooth. Além disso, tente desligar outros periféricos Bluetooth durante sessões do Windows Mixed Reality para ver se ele ajuda.

#### <a name="games-and-apps-from-the-microsoft-store"></a>Jogos e aplicativos da Microsoft Store

* Alguns jogos graficamente intensivos, como Forza Motorsport 7, podem causar problemas de desempenho em PCs com menos capacidade quando reproduzidos dentro da realidade mista do Windows.

#### <a name="audio"></a>Áudio

* Se você tiver o Cortana habilitado em seu PC host antes de usar o headset de realidade misturada do Windows, poderá perder a simulação de som espacial aplicada aos aplicativos que você coloca em casa ao Windows Mixed Reality. 
   * A solução alternativa é habilitar o "Windows Sonic para fones de ouvido" em todos os dispositivos de áudio conectados ao seu PC, até mesmo no dispositivo de áudio conectado ao headset:
      1. Clique com o botão esquerdo do mouse no ícone do orador na barra de tarefas da área de trabalho e selecione na lista de dispositivos de áudio.
      2. Clique com o botão direito do mouse no ícone do orador na barra de tarefas da área de trabalho e selecione "Windows Sonic para fones de ouvido" no menu "configuração do orador".
      3. Repita essas etapas para todos os seus dispositivos de áudio (pontos de extremidade).
   * Outra opção é desativar "permitir que a Cortana responda à Ei Cortana" em **configurações** > **Cortana** na sua área de trabalho antes de iniciar a realidade mista do Windows.
* Quando outro dispositivo USB de multimídia (como uma Web Cam) compartilha o mesmo hub USB (externo ou dentro de seu PC) com o headset de realidade mista do Windows, em casos raros, a tomada de áudio/fone de ouvido do headset pode ter um som de zumbi ou nenhum áudio. Você pode corrigir isso pelo seu headset em uma porta USB que não compartilha o mesmo Hub que o outro dispositivo, ou desconectar/desabilitar o outro dispositivo de multimídia USB.
* Em casos muito raros, o hub USB do PC host não pode fornecer energia suficiente para o headset de realidade mista do Windows e você pode notar uma intermitência de ruído dos fones de ouvido conectados ao headset.

#### <a name="holograms"></a>Hologramas

* Se você tiver colocado um grande número de hologramas em sua casa do Windows Mixed Reality, alguns poderão desaparecer e reaparecerem à medida que você examinar. Para evitar isso, remova alguns dos hologramas nessa área da página inicial do Windows Mixed Reality.

#### <a name="motion-controllers"></a>Controladores de movimento

* Se a entrada não estiver sendo roteada para o headset, o controlador de movimento desaparecerá brevemente quando for mantido ao lado do limite da sala. Pressionar Win + Y para garantir que haja uma faixa azul no monitor da área de trabalho resolverá isso. 
* Ocasionalmente, quando você clica em uma página da Web no Microsoft Edge, o conteúdo será ampliado em vez de clicar.

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Aplicativo de desktop na página inicial do Windows Mixed Reality

* A ferramenta de recorte não funciona no aplicativo de desktop.
* O aplicativo de área de trabalho não mantém a configuração ao reiniciar.
* Se você estiver usando a visualização do portal de realidade misturada na sua área de trabalho, ao abrir o aplicativo de desktop na página inicial do Windows Mixed Reality, você poderá observar o efeito de espelho infinito. 
* A execução do aplicativo de área de trabalho pode causar problemas de desempenho em PCs com realidade não ultra Windows misturada; Não é recomendável.  
* O aplicativo de desktop pode ser iniciado automaticamente porque uma janela invisível no desktop tem foco. 
* O prompt de controle de conta de usuário da área de trabalho fará com que o headset apareça em preto até que o prompt seja concluído

#### <a name="windows-mixed-reality-for-steamvr"></a>Realidade mista do Windows para SteamVR

* Talvez seja necessário iniciar o portal de realidade misturada após a atualização para garantir que as atualizações de software necessárias para a atualização do Windows 10 de abril de 2018 tenham sido concluídas antes de iniciar o SteamVR. 
* Você deve estar em uma versão recente do Windows Mixed Reality for SteamVR para permanecer compatível com a atualização do Windows 10 de abril de 2018. Verifique se as atualizações automáticas estão ativadas para o Windows Mixed Reality for SteamVR, localizada na seção "software" da sua biblioteca no fluxo.  

#### <a name="other-issues"></a>Outros problemas

>[!IMPORTANT]
>Uma versão anterior da atualização do Windows 10 de abril de 2018 enviada por push para pessoas (versão 17134,5) não tinha um software necessário para executar a realidade mista do Windows. É recomendável evitar essa versão se estiver usando a realidade mista do Windows. 

Identificamos uma regressão de desempenho ao usar o livro de superfície 2 na versão inicial desta atualização (10.0.17134.1) que estamos trabalhando para corrigir em um patch de atualização futuro. Sugerimos aguardar até que isso tenha sido corrigido antes de atualizar manualmente ou esperar que a atualização seja distribuída normalmente.

## <a name="provide-feedback-and-report-issues"></a>Fornecer comentários e relatar problemas

Use o [aplicativo de Hub de comentários em seu computador do HoloLens ou do Windows 10](give-us-feedback.md) para fornecer comentários e relatar problemas. O uso do hub de comentários garante que todas as informações de diagnóstico necessárias estejam incluídas para ajudar nossos engenheiros a depurar e resolver o problema rapidamente.

>[!NOTE]
>Lembre-se de aceitar o prompt que pergunta se você deseja que o Hub de comentários acesse sua pasta documentos (selecione **Sim** quando solicitado).

## <a name="prior-release-notes"></a>Notas de versão anteriores

* [Notas sobre a versão – outubro de 2017](release-notes-october-2017.md)
* [Notas sobre a versão – agosto de 2016](release-notes-august-2016.md)
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte também
* [Suporte a headsets de imersão (link externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Suporte ao HoloLens (link externo)](https://support.microsoft.com/products/hololens)
* [Instalar as ferramentas](install-the-tools.md)
* [Faça comentários](give-us-feedback.md)

