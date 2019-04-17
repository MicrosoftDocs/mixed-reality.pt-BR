---
title: Notas de versão – agosto de 2016
description: HoloLens notas de versão para o Windows 10 aniversário de versão (outono de 2016)
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, anotações, sistema operacional, plataforma, recursos, conjunto comercial de versão
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590705"
---
# <a name="release-notes---august-2016"></a>Notas de versão – agosto de 2016

A equipe do HoloLens está ouvindo comentários de desenvolvedores no programa Windows Insider para priorizar o nosso trabalho. Continue a [nos enviar comentários](give-us-feedback.md) por meio do Hub de comentários, o [fóruns para desenvolvedores](https://forums.hololens.com) e [por meio do Twitter @HoloLens ](https://twitter.com/hololens). Como o Windows 10 abraços que a atualização de aniversário, a equipe do HoloLens está feliz por entregar melhoram ainda mais a experiência holográfica. Nesta atualização, nos concentramos nos principais correções, aprimoramentos e recursos de Introdução ao solicitados por empresas e está disponível no Microsoft HoloLens Commercial Suite.

**Versão mais recente:** Atualização do Windows Holographic em agosto de 2016 (**10.0.14393.0**, versão de aniversário do Windows 10)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Para [atualização para a versão atual](updating-hololens.md), abra o *configurações* aplicativo, vá para *atualização e segurança*, em seguida, selecione o *verificar se há atualizações* botão.

## <a name="new-features"></a>Novos recursos

**Anexar ao processo de depuração** HoloLens agora dá suporte a anexar ao processo de depuração. Você pode usar o Visual Studio 2015 atualização 3 para se conectar a um aplicativo em execução em um HoloLens e [começar a depurá-lo](using-visual-studio.md#debugging-an-installed-or-running-app). Isso funciona sem a necessidade de implantar a partir de um projeto do Visual Studio.

**Atualizado o emulador do HoloLens** também lançamos uma versão atualizada do emulador HoloLens.

**Suporte de Gamepad** agora, você pode emparelhar e usar o Bluetooth gamepads com HoloLens! O controlador S recém-lançado do Xbox sem fio apresenta os recursos de Bluetooth e pode ser usado para executar seus aplicativos e jogos favoritos gamepad habilitado. Um [atualização do controlador](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) devem ser aplicadas antes de poder conectar o S de controlador do Xbox sem fio com o HoloLens. O S de controlador do Xbox sem fio é compatível com [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) e [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) APIs. Modelos adicionais dos controladores de Bluetooth podem ser acessados por meio de [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API.

## <a name="improvements-and-fixes"></a>Melhorias e correções

Estamos em sincronia com o restante da atualização de aniversário do Windows 10, portanto, além das correções específicas Hololens, que também está recebendo todas as qualidades da atualização do Windows para aumentar o desempenho e confiabilidade de plataforma. Seus comentários são altamente com valor e priorizados para obter as correções da versão.

Melhoramos as seguintes experiências:
* Faça logon em experiências.
* ingresso no local.
* eficiência de energia para as transições de estado de energia do dispositivo.
* estabilidade com a captura de realidade mista.
* confiabilidade para conectividade de Bluetooth
* persistência de holograma no cenário de aplicativo de várias.

Corrigimos os problemas a seguir:
* o depurador de gráficos e criadores de perfil do Visual Studio não conseguir se conectar.
* fotos e documentos não aparecem no Explorador de arquivos no portal do dispositivo.
* Barra de aplicativos pode piscar quando o cursor é colocado acima enquanto estiver no modo de ajuste.
* No modo de ajuste, o cursor de ponto de olhar olho será alterado para o cursor de seta 4 em algum momento mais lentamente.
* "Ei Cortana reproduzir música" não iniciar o Groove.
* Após a atualização anterior, dizer "Vá início" não será exibido o painel de pins corretamente.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Introdução ao Microsoft HoloLens comercial Suite

O Microsoft HoloLens Commercial Suite está pronto para implantação corporativa. Adicionamos vários altamente solicitados [recursos comerciais](commercial-features.md) de nossos parceiros de negócios antecipada.

Entre em contato com seu gerente de conta da Microsoft local para adquirir o Commercial Suite do Microsoft HoloLens.

### <a name="key-commercial-features"></a>Principais recursos comerciais 

* **Modo de quiosque.** Com o modo de quiosque do HoloLens, você pode limitar quais aplicativos para executar para habilitar experiências de demonstração ou apresentação.<br>
  ![Com o modo de quiosque, HoloLens inicia diretamente para o aplicativo de sua escolha.](images/201608-kioskmode-400px.png)
* **Gerenciamento de dispositivo móvel (MDM) para o HoloLens.** O departamento de TI pode gerenciar vários dispositivos HoloLens simultaneamente usando soluções como o Microsoft Intune. Você poderá gerenciar as configurações, selecionar aplicativos para instalar e configurar as configurações de segurança personalizadas às necessidades da organização.<br>
  ![Gerenciamento de dispositivo móvel em HoloLens fornece gerenciamento de dispositivo de nível empresarial em vários dispositivos.](images/201608-enterprisemanagement-400px.png)
* **Windows Update for Business.** Controlado atualizações do sistema operacional em dispositivos e suporte para o branch de manutenção de longo prazo.
* **Segurança de dados.** Criptografia de dados do BitLocker é habilitada no HoloLens para fornecer o mesmo nível de proteção de segurança como qualquer outro dispositivo do Windows.
* **Acesso de trabalho.** Qualquer pessoa em sua organização pode se conectar remotamente à rede corporativa por meio de uma rede virtual privada em um HoloLens. HoloLens também podem acessar as redes Wi-Fi que exijam credenciais.
* **Microsoft Store para empresas.** O departamento de TI também pode configurar um repositório privado do enterprise, que contém apenas os aplicativos da sua empresa para seu uso específico do HoloLens. Distribua seu software corporativo para o grupo selecionado de usuários corporativos.

### <a name="development-edition-vs-commercial-suite"></a>Development Edition versus Commercial Suite

<table>
<tr>
<th>Recursos</th><th>Development Edition</th><th>Commercial Suite</th>
</tr><tr>
<td>Criptografia de dispositivo (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>VPN (Rede Virtual Privada)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Modo de quiosque</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Gerenciamento e implantação</th>
</tr><tr>
<td>Gerenciamento de Dispositivos Móveis (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Capacidade de bloquear o cancelamento do registro</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Acesso Wi-Fi corporativa baseada em certificado</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (consumidor)</td><td style="text-align: center;">Consumidor</td><td style="text-align: center;">Filtragem por meio do MDM</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Portal de Store de negócios</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Segurança e identidade</th>
</tr><tr>
<td>Faça logon com o Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Faça logon com a conta da Microsoft (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Desbloqueio de credenciais de próxima geração com PIN</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Inicialização segura</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Manutenção e suporte</th>
</tr><tr>
<td>Assim que chegarem de atualizações automáticas do sistema</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Branch de manutenção de longo prazo</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Notas de versão prévia
* [Notas de versão – maio de 2016](release-notes-may-2016.md)
* [Notas de versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte também
* [Problemas conhecidos do HoloLens](hololens-known-issues.md)
* [Recursos comerciais](commercial-features.md)
* [Instalar as ferramentas](install-the-tools.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
