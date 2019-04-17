---
title: Notas de versão – abril de 2018
description: HoloLens e notas de versão de realidade mista do Windows para o Windows 10 de abril de 2018 atualizam (também conhecido como RS4).
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: anotações, versão, windows 10, compilação, rs4, sistema operacional de versão
ms.openlocfilehash: 1fc1b43b0581234e835379fd553b78121108086e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589753"
---
# <a name="release-notes---april-2018"></a>Notas de versão – abril de 2018

O **[atualização do Windows 10 de abril de 2018](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (também conhecido como RS4) inclui novos recursos para o HoloLens e o Windows Mixed Reality fones imersivos em exposição conectado aos computadores. 

Para atualizar para a versão mais recente de qualquer tipo de dispositivo, abra o **as configurações** aplicativo, vá para **atualização e segurança**, em seguida, selecione o **verificar se há atualizações** botão. Em um computador Windows 10, você também pode instalar manualmente o Windows 10 de abril de 2018 atualizar usando o [ferramenta de criação de mídia do Windows](https://www.microsoft.com/software-download/windows10).

**Versão mais recente para a área de trabalho:** Atualização do Windows 10 de abril de 2018 (**10.0.17134.1**)<br>
**Versão mais recente do HoloLens:** Atualização do Windows 10 de abril de 2018 (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Atualização de 10 de abril de 2018 de uma mensagem de Alex Kipman e visão geral dos novos recursos de realidade mista do Windows*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Novos recursos para fones imersivos em exposição realidade mista do Windows

O Windows 10 de abril de 2018 atualização inclui muitos aprimoramentos para o uso de fones de ouvido Windows Mixed Reality de imersão (VR) com o PC da área de trabalho, como: 

* **Novos ambientes para a página inicial de realidade misturada** -agora você pode escolher entre o Cliff House e o novo ambiente Skyloft, selecionando **casas** no menu Iniciar. Também adicionamos [um recurso experimental](add-custom-home-environments.md) que lhe permitirá usar ambientes personalizados que você criou.
* **Acesso rápido a captura de realidade misturada** -agora você pode tirar fotos de realidade misturada usando um controlador de animação. Mantenha o botão do Windows e, em seguida, toque o gatilho. Isso funciona em ambientes e aplicativos, mas não vai capturar o conteúdo protegido com DRM.
* **Novas opções para iniciar e redimensionamento de conteúdo** -aplicativos agora são colocados automaticamente na sua frente quando você iniciá-los no menu Iniciar. Você agora também pode redimensionar aplicativos 2D arrastando as bordas e cantos da janela.
* **Ir facilmente para o conteúdo com o comando de voz "ser transportado"** -agora você rapidamente pode ser transportado para estar na frente do conteúdo no Windows Mixed Reality doméstica Observação no conteúdo e dizendo "ser transportado."
* **[Animado dos inicializadores de aplicativo 3D](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#animation-guidelines) e [decorativos objetos 3D](enable-placement-of-3d-models-in-the-home.md) para a página inicial de realidade misturada** -agora você pode adicionar animação a dos inicializadores de aplicativo 3D e permitir que os usuários colocar decorativos modelos 3D de um aplicativo de página da Web ou 2D no Windows Mixed Reality inicial.
* **[Melhorias no Windows Mixed Reality for SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md)**  -Windows Mixed Reality para SteamVR está fora do "primeiro acesso" com novas atualizações, incluindo: comentários hápticos ao usar controladores de movimento, melhorar o desempenho e confiabilidade, e melhorias na aparência dos controladores de movimento em SteamVR.
* **Outras melhorias** -configurações de ajuste automático de desempenho foram atualizadas para fornecer uma experiência mais otimizada (você pode [substituir manualmente](#visual-quality) essa configuração). A instalação agora fornece que informações mais detalhadas sobre problemas comuns de compatibilidade com cartões USB 3.0 de controladores e elementos gráficos.

## <a name="new-features-for-hololens"></a>Novos recursos para o HoloLens

O Windows 10 de abril de 2018 atualização está disponível para todos os clientes do HoloLens! Essa atualização vem com melhorias que foram introduzidas desde a última versão principal do software HoloLens na [agosto de 2016](release-notes-august-2016.md).

### <a name="for-everyone"></a>Para todos

<table>
  <tr>
    <th>Recurso</th><th>Detalhes</th><th>Instruções</th>
  </tr>
  <tr>
    <td>Posicionamento automático de conteúdo 2D e 3D na inicialização</td><td>Um aplicativo UWP 2D app launcher ou 2D autolocais no mundo em um tamanho ideal e a distância quando iniciado, em vez de exigir que o usuário para colocá-lo. Se um <a href="app-views.md">aplicativo imersivo</a> usa um inicializador de aplicativos 2D em vez de uma <a href="3d-app-launcher-design-guidance.md">iniciador do aplicativo 3D</a>, o aplicativo de imersão iniciará automaticamente do iniciador de aplicativos 2D mesmo como no RS1.<br><br>Um inicializador de aplicativos 3D no menu Iniciar também autolugares do mundo. Em vez de iniciar automaticamente o aplicativo, os usuários podem, em seguida, clicar no inicializador para iniciar o aplicativo de imersão. Conteúdo 3D aberto do aplicativo hologramas e da borda também autolugares do mundo.</td><td>Ao abrir um aplicativo no menu Iniciar, você não deverá colocá-lo no mundo.<br><br>Se o aplicativo 2D /<a href="3d-app-launcher-design-guidance.md">lançador de aplicativo 3D</a> posicionamento não é ideal, você pode movê-los facilmente usando o novo manipulações de aplicativo fluida descritas abaixo. Também é possível posicionar novamente o conteúdo de inicializador/3D 2D app dizer "Mover isso" e, em seguida, usando a olhar para reposicionar o conteúdo.</td>
  </tr>
  <tr>
    <td>Manipulação de aplicativo fluidos</td><td>Mover, redimensionar e girar o conteúdo 2D e 3D sem precisar entrar no modo de "Ajuste".</td><td>Para mover um aplicativo da UWP 2D ou inicializador de aplicativos 2D, simplesmente olhar em sua barra de aplicativo e, em seguida, usar o tap + mantenha + arrastar gesto. É possível mover o conteúdo 3D, Observação em qualquer lugar no objeto e, em seguida, usando toque + mantenha + arrastar.<br><br>Para redimensionar o conteúdo 2D, mantenha o foco em seu canto. O cursor de olhar se transformará em um cursor de redimensionamento e, em seguida, você pode tocar + mantenha + arraste para redimensionar. Você também pode fazer o conteúdo 2D mais alto ou mais amplo, olhando suas bordas e arrastando.<br><br>Para redimensionar o conteúdo 3D, levante-se ambas as suas mãos no quadro de gesto, dedos na posição pronta. Você verá o cursor transformar em um estado com 2 mãos pouco. Fazer o toque e segure o gesto com ambas as suas mãos. Movendo suas mãos mais próximos ou mais distantes, você irá alterar o tamanho do objeto. Mover suas mãos progressivos e regressivos relativos uns aos outros para girar o objeto. Você também pode redimensionar/girar conteúdo 2D dessa maneira.</td>
  </tr>
  <tr>
    <td>Redimensionamento horizontal do aplicativo 2D com refluxo</td><td>Tornar um aplicativo UWP 2D maior taxa de proporção para ver mais conteúdo do aplicativo. Por exemplo, tornando o aplicativo de email largo o suficiente para mostrar o painel de visualização.</td><td>Simplesmente olhar na borda esquerda ou direita do aplicativo UWP 2D para ver o cursor de redimensionamento, em seguida, usar o tap + mantenha + arraste gesto para redimensionar.</td>
  </tr>
  <tr>
    <td>Suporte de comandos de voz expandido</td><td>Você pode fazer mais simplesmente usando a voz.</td><td>Experimente esses comandos de voz:<ul><li>"Go to Start" – abre o menu Iniciar ou sair de um <a href="app-views.md">imersivo aplicativo</a>.</li><li>"Mover isso" - permite que você mova um objeto.</li></ul></td>
  </tr>
  <tr>
    <td>Aplicativos de fotos e hologramas atualizados</td><td>Aplicativo de hologramas atualizado com novo hologramas. Aplicativo de fotos atualizado.</td><td>Você observará uma aparência atualizada para os aplicativos hologramas e fotos. O aplicativo hologramas inclui vários hologramas novo e um tomador de rótulo para a criação mais fácil de texto.</td>
  </tr>
  <tr>
    <td>Aprimorada a captura de realidade misturada</td><td>Início de atalho de hardware e de término MRC vídeo.</td><td>Mantenha Aumentar Volume + Down por 3 segundos iniciar a gravação de vídeo MRC. Toque em ambos novamente ou use o gesto de bloom para terminar.</td>
  </tr>
  <tr>
    <td>Espaços consolidados</td><td>Simplifique o gerenciamento de espaço para hologramas em um único espaço.</td><td>HoloLens localiza automaticamente o seu espaço e não requer mais gerenciar ou selecionar espaços. Se você tiver problemas com hologramas ao seu redor, você pode ir para <b>Configurações > sistema > hologramas > Remover nas proximidades hologramas</b>. Se necessário, você também pode selecionar <b>remover todos os hologramas</b>.</td>
  </tr>
  <tr>
    <td>Imersão de áudio aprimorada</td><td>Agora você pode ouvir HoloLens melhor em ambientes com ruídos e experiência de som mais realista de aplicativos como o som será ser obscurecido por paredes real detectados pelo dispositivo.</td><td>Você não precisa fazer nada para poder aproveitar o som espacial aprimorado.</td>
  </tr>
  <tr>
    <td>Explorador de Arquivos</td><td>Mover e excluir arquivos a partir do HoloLens.</td><td>Você pode usar o <b>Explorador de arquivos</b> aplicativo para mover e excluir arquivos a partir do HoloLens.<br><br><b>Dica:</b> Se você não vir todos os arquivos, o filtro "Recentes" pode estar ativo (o ícone de relógio é realçado no painel esquerdo). Para corrigir, selecione a <b>este dispositivo</b> documentar o ícone no painel esquerdo (abaixo do ícone de relógio), ou abra o menu e selecione <b>este dispositivo</b>.
</td>
  </tr>
  <tr>
    <td>Suporte MTP (protocolo de transferência de mídia)</td><td>Habilita o seu computador para acessar suas bibliotecas (fotos, vídeos, documentos) em HoloLens para facilitar a transferência.</td><td>Assim como outros dispositivos móveis, conecte-se o HoloLens a seu computador para abrir <b>Explorador de arquivos</b> para acessar suas bibliotecas do HoloLens (fotos, vídeos, documentos) para facilitar a transferência.<br><br><b>Dicas:</b><ul><li>Se você não vir todos os arquivos, verifique se que você entrar no seu HoloLens para habilitar o acesso aos seus dados.</li><li>Partir <b>Explorador de arquivos</b> em seu PC, você pode selecionar <b>propriedades do dispositivo</b> para ver o número de versão do sistema operacional do Windows Holographic (versão de firmware) e o número de série do dispositivo.</li></ul><b>Problema conhecido:</b> Renomeando HoloLens via <b>Explorador de arquivos</b> em seu computador não está habilitado.</td>
  </tr>
  <tr>
    <td>Suporte de rede do portal cativo durante a instalação</td><td>Agora você pode configurar seu HoloLens em uma rede do convidado em hotéis, centros de conferência, lojas de varejo ou empresas que usam o captive portal.</td><td>Durante a instalação, selecione a rede, verifique se conectar automaticamente, se desejado e insira as informações de rede, conforme solicitado.</td>
  </tr>
  <tr>
    <td>Sincronização de fotos e vídeos por meio do aplicativo do OneDrive</td><td>Suas fotos e vídeos do HoloLens agora serão sincronizados por meio do aplicativo OneDrive da Microsoft Store, em vez de diretamente por meio do aplicativo de fotos.</td><td>Para configurar isso, baixe e inicie o aplicativo OneDrive a Store. Na primeira execução, você deverá ser solicitado para automaticamente carregar suas fotos no OneDrive, ou você pode encontrar a opção nas configurações do aplicativo.</td>
  </tr>
</table>

### <a name="for-developers"></a>Para desenvolvedores

<table>
  <tr>
    <th>Recurso</th><th>Detalhes</th><th>Instruções</th>
  </tr>
  <tr>
    <td>Aprimoramentos de mapeamento espacial</td><td>Melhorias de qualidade, a simplificação e desempenho.</td><td>Malha de mapeamento espacial aparecerão mais clara – menos triângulos são necessários para representar o mesmo nível de detalhe. Você pode observar as alterações na densidade de triângulo na cena.</td>
  </tr>
  <tr>
    <td>Seleção automática de ponto de foco com base no buffer de profundidade</td><td>Enviar um buffer de profundidade para Windows permite HoloLens selecionar um ponto de foco automaticamente para otimizar a estabilidade holograma.</td><td>No Unity, vá para <b>Editar > configurações do projeto > Player > guia da plataforma Universal do Windows > configurações XR</b>, expanda o <b>SDK de realidade mista do Windows</b> item e, em seguida, certifique-se de <b>habilitar o Buffer de profundidade Compartilhamento</b> é verificada. Isso será verificado automaticamente para novos projetos.<br><br>Para aplicativos DirectX, verifique se você chamar o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer </a> método <b>HolographicRenderingParameters</b> cada quadro para fornecer o buffer de profundidade para Windows.
</td>
  </tr>
  <tr>
    <td>Modos de reprojection holographic</td><td>Agora você pode desabilitar reprojection posicional em HoloLens para melhorar a estabilidade holograma de rigidamente bloqueado no corpo de conteúdo como o vídeo de 360 graus.</td><td>No Unity, defina <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings.ReprojectionMode</a> à <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode.OrientationOnly</a> quando todo o conteúdo no modo de exibição é rigidamente bloqueada no corpo.<br><br>Para aplicativos DirectX, defina <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode"> HolographicCameraRenderingParameters.ReprojectionMode</a> à <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode.OrientationOnly</a> quando todo o conteúdo no modo de exibição é rigidamente bloqueada no corpo.</td>
  </tr>
  <tr>
    <td>APIs de adaptação de aplicativos</td><td>APIs do Windows saber mais sobre onde o aplicativo é executado, como se a exibição do dispositivo é (HoloLens) transparente ou opaco (fone de ouvido imersivo) e se 2D modo de exibição de um aplicativo UWP está aparecendo no shell holográfico.</td><td>Unity anteriormente tinha manualmente expostos <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings.IsDisplayOpaque</a> de forma que funcionavam antes mesmo que essa compilação.<br><br>Para aplicativos DirectX, agora você pode acessar as APIs existentes, como <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay.GetDefault(). IsOpaque</a> e <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview.IsCurrentViewPresentedOnHolographicDisplay</a> em HoloLens também.
</td>
  </tr>
  <tr>
      <td>Modo de pesquisa</td><td>Permite aos desenvolvedores acessar chaves sensores do HoloLens ao criar aplicativos acadêmicos e industriais para testar novas ideias nos campos de pesquisa Visual computacional e robótica, incluindo:<ul><li>Os quatro câmeras de acompanhamento de ambiente</li><li>Duas versões dos dados de câmera de mapeamento de profundidade</li><li>Duas versões de um fluxo de IR reflexibilidade</li></ul></td><td><a href="research-mode.md">Documentação do modo de pesquisa</a><br><a href="https://github.com/Microsoft/HoloLensForCV">Aplicativos de exemplo do modo de pesquisa</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>Para clientes comerciais

<table>
  <tr>
    <th>Recurso</th><th>Detalhes</th><th>Instruções</th>
  </tr>
  <tr>
    <td>Usar várias contas de usuário do Active Directory do Azure em um único dispositivo</td><td>Compartilhe um HoloLens com vários usuários do AD do Azure, cada um com suas próprias configurações de usuário e os dados do usuário no dispositivo.</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">IT Pro Center: Compartilhamento HoloLens com várias pessoas</a></td>
  </tr>
  <tr>
    <td>Alterar a rede Wi-Fi no sign-in</td><td>Alterar a rede Wi-Fi antes de entrar para ativar outro usuário entrar com sua conta de usuário do AD do Azure pela primeira vez, permitindo que os usuários compartilhar dispositivos em vários locais e o trabalho de sites.</td><td>Na tela de logon, você pode usar o ícone de rede abaixo do campo de senha para se conectar a uma rede. Isso é útil quando se trata a primeira vez que entrar em um dispositivo.</td>
  </tr>
  <tr>
    <td>Registro unificado</td><td>Agora é mais fácil para um usuário do HoloLens que configurar o dispositivo com uma conta pessoal da Microsoft para adicionar uma conta corporativa (Azure AD) e ingressar o dispositivo ao seu servidor MDM.</td><td>Basta entrar com uma conta do AD do Azure e registro ocorre automaticamente.</td>
  </tr>
  <tr>
    <td>Sincronização de emails sem o registro do MDM</td><td>Suporte para sincronização de emails do Exchange Active Sync (EAS) sem a necessidade de registro do MDM.</td><td>Agora você pode sincronizar email sem o registro do MDM. Você pode configurar o dispositivo com uma Account da Microsoft, baixar e instalar o aplicativo de email e adicionar uma conta de email de trabalho diretamente.</td>
  </tr>
</table>

### <a name="for-it-pros"></a>para profissionais de TI

<table>
  <tr>
    <th>Recurso</th><th>Detalhes</th><th>Instruções</th>
  </tr>
  <tr>
    <td>Novo nome de "Windows Holographic for Business" sistema operacional</td><td>Desmarque a edição de nomenclatura para reduzir a confusão no aplicativo de licença de atualização de edição quando recursos de Commercial Suite são habilitados no HoloLens.</td><td>Você pode ver qual edição do Windows Holographic está em seu dispositivo no <b>Configurações > sistema > sobre</b>. "Windows Holographic for Business" será exibida se uma atualização de edição tiver sido aplicada para habilitar recursos Commercial Suite. Saiba como <a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">desbloquear o Windows Holographic for Business recursos</a>.</td>
  </tr>
  <tr>
  <td>(WCD) do Windows Configuration Designer</td><td>Crie e edite os pacotes de provisionamento para configurar o HoloLens por meio do aplicativo WCD atualizado. Assistente para HoloLens Simple para atualização de edição, OOBE configurável, fuso horário/região, token do AD do Azure em massa, rede e desenvolvedor CSP. Editor avançado, filtrado para HoloLens suporte para opções, incluindo acesso atribuído e CSPs de gerenciamento de conta.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center: Configurar o HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
    <td>Instalação configurável (OOBE)</td><td>Oculte calibragem, treinamento do gesto/olhar e telas de configuração de Wi-Fi durante a instalação.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT Pro Center: Configurar o HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
    <td>Suporte a token em massa do Azure AD</td><td>Pré-registrar o dispositivo ao locatário de diretório do Azure AD para o fluxo de instalação mais rápido do usuário.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center: Configurar o HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
  <td>CSP DeveloperSetup</td><td>Implante o perfil para configurar o HoloLens no modo de desenvolvedor. É útil para desenvolvimento e demonstração de dispositivos.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center: Configurar o HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
  <td>CSP AccountManagement</td><td>Compartilhar um dispositivo de HoloLens e remover dados de usuário após a saída da rede ou limites de inatividade/armazenamento de uso temporário. Dá suporte a contas do Azure AD.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center: Configurar o HoloLens usando um pacote de provisionamento</a></td>
  </tr>
  <tr>
  <td>Acesso atribuído</td><td>Windows o acesso atribuído para trabalhadores da primeira linha ou demonstrações. Bloqueio único ou vários aplicativos. Não há necessidade de desenvolvedor desbloquear.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">IT Pro Center: Configurar o HoloLens no modo de quiosque</a></td>
  </tr>
  <tr>
  <td>Acesso de convidado para dispositivos de quiosque</td><td>Windows acesso atribuído com a conta de convidado sem senha para demonstrações. Bloqueio único ou vários aplicativos. Não há necessidade de desenvolvedor desbloquear.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">IT Pro Center: Configurar o HoloLens no modo de quiosque</a></td>
  </tr>
  <tr>
    <td>Configurar o diagnóstico (OOBE)</td><td>Obter logs de diagnóstico do HoloLens, portanto, você pode solucionar problemas de falhas de entrada do Azure AD (antes de Hub de comentários está disponível para o usuário cuja entrada falha).</td><td>Quando a instalação ou entrada falha, escolha o novo <b>coletar informações</b> opção para obter os logs de diagnóstico para solução de problemas.</td>
  </tr>
  <tr>
    <td>Expiração de senha indefinido de conta local</td><td>Remova a interrupção do dispositivo redefinido quando a expiração de senha de conta local.</td><td>Ao provisionar uma conta local, você não precisa alterar a senha a cada 42 dias no <b>configurações</b>, como a senha da conta não expira.</td>
  </tr>
  <tr>
    <td>Detalhes e status de sincronização do MDM</td><td>Funcionalidade padrão do Windows para entender os detalhes de dentro do HoloLens e o status de sincronização do MDM.</td><td>Você pode verificar o status de sincronização para um dispositivo no MDM <b>Configurações > contas > acesso corporativo ou estudante > informações</b>. No <b>status de sincronização do dispositivo<b> seção, você pode iniciar uma sincronização, consulte áreas gerenciadas pelo MDM e criar e exportar um relatório de diagnóstico avançado.</td>
  </tr>
</table>

## <a name="known-issues"></a>Problemas conhecidos

Trabalhamos muito para fornecer uma ótima experiência de realidade mista do Windows, mas estamos ainda estiver acompanhando alguns problemas conhecidos. Se você encontrar outras pessoas, por favor [envie seus comentários](give-us-feedback.md).

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>Após a atualização

Você pode observar os seguintes problemas após a atualização de RS1 para RS4 no seu HoloLens:
* **Redefinir PINs** -3x3 aplicativos fixados ao menu Iniciar serão redefinidas para os padrões após a atualização. 
* **Aplicativos e colocada hologramas redefinição** -aplicativos colocados no seu mundo serão removidos após a atualização e precisará ser colocado novamente em todo o seu espaço. 
* **Hub de comentários não pode iniciar imediatamente** -imediatamente após a atualização, levará alguns minutos antes de poder iniciar alguns aplicativos de caixa de entrada, como o Hub de comentários, enquanto eles se atualizam. 
* **Certificados corporativos de Wi-Fi precisam ser sincronizados novamente** -estamos investigando um problema que requer o HoloLens estar conectado a uma rede diferente em ordem para certificados corporativos a ser sincronizado novamente para o dispositivo antes que ele possa se reconectar ao redes corporativas usando certificados. 
* **Reprodução de vídeo HEVC H.265 não funciona** -aplicativos que tentam reproduzir vídeos H.265 receberá uma mensagem de erro. A solução alternativa é [acessar o Windows Device Portal](using-the-windows-device-portal.md), selecione **Apps** na barra de navegação à esquerda, e **remover** o aplicativo de HEVC. Em seguida, instale a versão mais recente [extensão de vídeo HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) da Microsoft Store. Estamos investigando o problema. 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>Para desenvolvedores: atualizar HoloLens aplicativos para dispositivos que executam o Windows atualiza de 10 de abril de 2018

Junto com uma boa lista de [novos recursos](#new-features-for-hololens), o Windows 10 abril 2018 atualização (RS4) para o HoloLens impõe alguns comportamentos de código que as versões anteriores não faziam isso:
* **Solicitações de permissão para usar recursos confidenciais (câmera, microfone, etc.)**  -RS4 em HoloLens irá impor as solicitações de permissão para aplicativos que desejam acessar recursos confidenciais, como a câmera ou o microfone. RS1 em HoloLens não forçou esses prompts, portanto, se seu aplicativo pressupõe que o acesso imediato a esses recursos, ele pode travar no RS4 (mesmo se o usuário concede permissão para o recurso solicitado). Leia o relevantes [artigo de declarações de recurso de aplicativo UWP](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) para obter mais informações.
* **Chamadas para aplicativos fora de seu próprio** -RS4 em HoloLens irá impor o uso adequado do [ *Windows.System.Launcher* classe](https://docs.microsoft.com/uwp/api/Windows.System.Launcher) para iniciar outro aplicativo de seus próprios. Por exemplo, temos visto problemas com aplicativos chamando *Windows.System.Launcher.LaunchUriForResultsAsync* de um thread não - ASTA da interface do usuário. Isso teria êxito no RS1 em HoloLens, mas RS4 requer a chamada a ser executado no thread da interface do usuário.

### <a name="windows-mixed-reality-on-desktop"></a>Realidade mista do Windows na área de trabalho

#### <a name="visual-quality"></a>Qualidade Visual

* Se você perceber depois que o Windows 10 de abril de 2018 Update que gráficos são mais desfocados que antes, ou se o campo de visualização parece menor na fone de ouvido, a configuração automática de desempenho pode ter sido alterada para manter uma taxa de quadros suficiente em menos potentes placa de vídeo (como 1050 Nvidia). Você pode substituir manualmente esse (se você escolher), navegando até **Configurações > realidade misturada > exibição de fone de ouvido > Opções de experiência > alteração** e alterando "Automático" para "Hz 90". Você também pode tentar alterar **qualidade Visual** (na mesma página de configurações) como "Alto".

#### <a name="windows-mixed-reality-setup"></a>Instalação do Windows Mixed Reality

* Ao configurar o Windows com um headset conectado, o monitor do PC poderá ficar em branco. Desconecte o headset para habilitar a saída para o monitor do PC para concluir a instalação do Windows.
* Se você não tiver fones de ouvido conectados, você poderá perder dicas adicionais quando visitar o Windows Mixed Reality inicial.
* Outros dispositivos Bluetooth podem causar interferências com controladores de movimento. Se os controladores do motion têm problemas de conexão/emparelhamento/acompanhamento, verifique se o rádio Bluetooth (se um dongle externo) está conectado a um local sem obstruções e não imediatamente ao lado do outro dongle de Bluetooth. Além disso, tente desligar outros periféricos de Bluetooth durante as sessões do Windows Mixed Reality para ver se ele ajuda.

#### <a name="games-and-apps-from-the-microsoft-store"></a>Jogos e aplicativos da Microsoft Store

* Alguns jogos graficamente intensivos, como o 7 de Motorsport Forza, podem causar problemas de desempenho em PCs com menor capacidade quando executados dentro de realidade mista do Windows.

#### <a name="audio"></a>Áudio

* Se você tiver habilitado em seu PC host antes de usar o headset de realidade mista do Windows a Cortana, você poderá perder a simulação de som espacial aplicada aos aplicativos que você coloque em torno do Windows Mixed Reality inicial. 
   * A solução alternativa é habilitar o "Windows Sonic para fones de ouvido" em todos os dispositivos de áudio conectados ao seu PC, até mesmo o fone de ouvido conectados ao dispositivo de áudio:
      1. Clique no ícone na barra de tarefas da área de trabalho e selecione na lista de dispositivos de áudio.
      2. Clique com botão direito no ícone na barra de tarefas da área de trabalho e selecione "Windows Sonic para fones de ouvido" no menu "A instalação do alto-falante".
      3. Repita essas etapas para todos os seus dispositivos de áudio (pontos de extremidade).
   * Outra opção é desativar "Cortana permitem responder a Ei Cortana" **as configurações** > **Cortana** na área de trabalho antes de iniciar o Windows Mixed Reality.
* Quando outro dispositivo USB multimídia (como uma webcam) compartilha o mesmo hub USB (externo ou dentro de seu PC) com o headset de realidade mista do Windows, em casos raros áudio jack/fones de ouvido do fone de ouvido pode ter um som zunido ou sem áudio em todos os. Você pode corrigir isso por fone de ouvido em uma porta USB que não compartilham o mesmo hub como o outro dispositivo ou outro dispositivo USB multimídia desconectar/desabilitar.
* Em casos raros, o hub USB do PC host não pode fornecer capacidade suficiente para o headset de realidade mista do Windows e você pode perceber uma intermitência de ruído dos fones de ouvido o fone de ouvido.

#### <a name="holograms"></a>Hologramas

* Se você colocou um grande número de hologramas no seu Windows Mixed Reality inicial, alguns podem desaparecer e reaparecer conforme você olha ao redor. Para evitar isso, remova algumas das hologramas o naquela área do Windows Mixed Reality inicial.

#### <a name="motion-controllers"></a>Controladores de movimento

* Se a entrada não está sendo roteada para o fone de ouvido, o controlador de movimento brevemente desaparecerá quando está sendo mantido ao lado do limite de espaço. Pressionar Win + R para garantir que exista uma faixa azul através do monitor da área de trabalho, isso será resolvido. 
* Ocasionalmente, quando você clica em uma página da web no Microsoft Edge, o conteúdo será zoom em vez de clique.

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Aplicativo da área de trabalho no Windows Mixed Reality inicial

* Ferramenta de captura não funciona no aplicativo da área de trabalho.
* Aplicativo da área de trabalho não mantém a configuração na nova inicialização.
* Se você estiver usando a visualização do Portal de realidade mista na área de trabalho, ao abrir o aplicativo da área de trabalho no Windows Mixed Reality inicial, você pode perceber o efeito de espelho infinito. 
* Executar o aplicativo da área de trabalho pode causar problemas de desempenho em não - Ultra misto realidade PCs Windows; não é recomendável.  
* Aplicativo de desktop pode iniciar automaticamente porque uma janela invisível na área de trabalho tem o foco. 
* Controle de conta de usuário da área de trabalho prompt fará fone de ouvido exibir preto até que o prompt é concluído.

#### <a name="windows-mixed-reality-for-steamvr"></a>Realidade mista do Windows para SteamVR

* Talvez você precise iniciar o Portal de realidade misturada depois de atualizar para garantir que as atualizações de software necessárias para o Windows 10 de abril de 2018 atualização concluir antes de iniciar SteamVR. 
* Você deve estar em uma versão recente do Windows Mixed Reality para SteamVR permanecer compatível com o Windows Update 10 de abril de 2018. Verifique se as atualizações automáticas estão ativadas para o Windows Mixed Reality para SteamVR, que está localizado na seção "Software" da sua biblioteca no fluxo.  

#### <a name="other-issues"></a>Outros problemas

>[!IMPORTANT]
>Uma versão anterior do Windows 10 de abril de 2018 atualização enviada por push para Insiders (versão 17134.5) não possuía uma parte dos softwares necessários para executar o Windows Mixed Reality. É recomendável evitar essa versão se usando o Windows Mixed Reality. 

Nós identificamos uma regressão de desempenho ao usar o Surface Book 2 sobre o lançamento inicial desta atualização (10.0.17134.1) que estamos trabalhando para corrigir um patch de atualização futura. Sugerimos que você espera até que esse problema foi corrigido antes de atualizar manualmente ou esperar pela atualização distribuir normalmente.

## <a name="provide-feedback-and-report-issues"></a>Fornecer comentários e relate problemas

Use o [aplicativo de Hub de comentários no computador com Windows 10 ou HoloLens](give-us-feedback.md) para fornecer comentários e relate problemas. Usar o Hub de comentários, você garante que todas as informações de diagnóstico necessárias estão incluídas para ajudar a nossos engenheiros de depurar e resolver o problema rapidamente.

>[!NOTE]
>Não se esqueça de aceitar o aviso que pergunta se você deseja que o Hub de comentários para acessar a pasta de documentos (selecione **Sim** quando solicitado).

## <a name="prior-release-notes"></a>Notas de versão prévia

* [Notas de versão – outubro de 2017](release-notes-october-2017.md)
* [Notas de versão – agosto de 2016](release-notes-august-2016.md)
* [Notas de versão – maio de 2016](release-notes-may-2016.md)
* [Notas de versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte também
* [Suporte de imersão fone de ouvido (link externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Suporte do HoloLens (link externo)](https://support.microsoft.com/products/hololens)
* [Instalar as ferramentas](install-the-tools.md)
* [Envie seus comentários](give-us-feedback.md)

