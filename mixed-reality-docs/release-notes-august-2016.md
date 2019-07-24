---
title: Notas de versão – agosto de 2016
description: Notas de versão do HoloLens para a versão de aniversário do Windows 10 (Outono de 2016)
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, notas de versão, sistema operacional, plataforma, recursos, pacote comercial
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524296"
---
# <a name="release-notes---august-2016"></a>Notas de versão – agosto de 2016

A equipe do HoloLens está ouvindo comentários de desenvolvedores no programa Windows Insider para priorizar nosso trabalho. Continue a enviar [comentários](give-us-feedback.md) por meio do hub de comentários, dos [fóruns de desenvolvedores](https://forums.hololens.com) e do [ @HoloLensTwitter por meio ](https://twitter.com/hololens)do. À medida que o Windows 10 adota a atualização de aniversário, a equipe do HoloLens tem o prazer de oferecer melhor melhoria para a experiência de Holographic. Nesta atualização, nos concentramos em correções principais, melhorias e introdução de recursos solicitados por empresas e disponíveis no pacote comercial do Microsoft HoloLens.

**Versão mais recente:** Atualização do Windows Holographic de agosto de 2016 (**10.0.14393.0**, versão de aniversário do Windows 10)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Para [atualizar para a versão atual](updating-hololens.md), abra o aplicativo *configurações* , acesse *Atualizar & segurança*e, em seguida, selecione o botão *verificar atualizações* .

## <a name="new-features"></a>Novos recursos

**Anexar à depuração de processo** O HoloLens agora dá suporte à depuração de anexação de processo. Você pode usar o Visual Studio 2015 atualização 3 para se conectar a um aplicativo em execução em um HoloLens e [começar a depurá-lo](using-visual-studio.md#debugging-an-installed-or-running-app). Isso funciona sem a necessidade de implantar a partir de um projeto do Visual Studio.

**Emulador do HoloLens atualizado** Também lançamos uma versão atualizada do emulador do HoloLens.

**Suporte a gamepad** Agora você pode emparelhar e usar o Bluetooth gamepads com o HoloLens! Os S recursos de Bluetooth do Xbox Wireless recentemente lançados e podem ser usados para reproduzir seus jogos e aplicativos favoritos habilitados para Gamepad. Uma [atualização do controlador](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) deve ser aplicada antes que você possa conectar os S do controlador sem fio do Xbox com o HoloLens. Os S do controlador sem fio do Xbox são compatíveis com as APIs [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) e [Windows. Gaming. Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) . Modelos adicionais de controladores Bluetooth podem ser acessados por meio da API [Windows. Gaming. Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) .

## <a name="improvements-and-fixes"></a>Melhorias e correções

Estamos sincronizados com o restante da atualização de aniversário do Windows 10, assim, além das correções específicas do Hololens, você também está recebendo todas as impedições do Windows Update para aumentar a confiabilidade e o desempenho da plataforma. Seus comentários são altamente valorizados e priorizados para correções na versão.

Melhoramos as seguintes experiências:
* experiências de logon.
* ingresso no local de trabalho.
* eficiência de energia para transições de estado de energia do dispositivo.
* estabilidade com capturas de realidade misturada.
* confiabilidade para conectividade Bluetooth
* persistência de holograma no cenário de vários aplicativos.

Corrigimos os seguintes problemas:
* Falha ao conectar o depurador de elementos gráficos e os profileres do Visual Studio.
* as fotos & documentos não aparecem no explorador de arquivos no portal do dispositivo.
* a barra de aplicativos pode piscar quando o cursor é colocado acima dele enquanto estiver no modo de ajuste.
* Quando estiver no modo de ajuste, o cursor de ponto olhar ocular será alterado para o cursor de quatro setas um pouco mais devagar.
* "Ei Cortana Play Music" não inicia o Groove.
* após a atualização anterior, dizer "Go Home" não exibe o painel Pins corretamente.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Apresentando o pacote comercial do Microsoft HoloLens

O pacote comercial do Microsoft HoloLens está pronto para a implantação empresarial. Adicionamos vários [recursos comerciais](commercial-features.md) altamente solicitados de nossos parceiros de negócios iniciais.

Entre em contato com seu Gerenciador de conta Microsoft local para comprar o pacote comercial do Microsoft HoloLens.

### <a name="key-commercial-features"></a>Principais recursos comerciais 

* **Modo de quiosque.** Com o modo de quiosque do HoloLens, você pode limitar quais aplicativos executar para habilitar experiências de demonstração ou demonstrações.<br>
  ![Com o modo de quiosque, o HoloLens é iniciado diretamente no aplicativo de sua escolha.](images/201608-kioskmode-400px.png)
* **MDM (gerenciamento de dispositivo móvel) para o HoloLens.** O departamento de ti pode gerenciar vários dispositivos HoloLens simultaneamente usando soluções como Microsoft Intune. Você poderá gerenciar as configurações, selecionar aplicativos para instalar e configurar as configurações de segurança personalizadas às necessidades da organização.<br>
  ![O gerenciamento de dispositivos móveis no HoloLens fornece gerenciamento de dispositivos de nível empresarial em vários dispositivos.](images/201608-enterprisemanagement-400px.png)
* **Windows Update para negócios.** Atualizações controladas do sistema operacional para dispositivos e suporte para o Branch de manutenção em longo prazo.
* **Segurança de dados.** A criptografia de dados do BitLocker é habilitada no HoloLens para fornecer o mesmo nível de proteção de segurança que qualquer outro dispositivo Windows.
* **Acesso corporativo.** Qualquer pessoa em sua organização pode se conectar remotamente à rede corporativa por meio da rede virtual privada em um HoloLens. O HoloLens também pode acessar redes Wi-Fi que exigem credenciais.
* **Microsoft Store para negócios.** Seu departamento de ti também pode configurar um repositório privado corporativo, contendo somente os aplicativos da sua empresa para seu uso específico de HoloLens. Distribua com segurança seu software corporativo para o grupo selecionado de usuários corporativos.

### <a name="development-edition-vs-commercial-suite"></a>Edição de desenvolvimento vs. Pacote comercial

<table>
<tr>
<th>Recursos</th><th>Edição de desenvolvimento</th><th>Pacote comercial</th>
</tr><tr>
<td>Criptografia de dispositivo (BitLocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>VPN (Rede Virtual Privada)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Modo de quiosque</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Gerenciamento e implantação</th>
</tr><tr>
<td>Gerenciamento de Dispositivos Móveis (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Capacidade de bloquear o cancelamento de registro</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Acesso de Wi-Fi corporativo baseado em certificado</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (consumidor)</td><td style="text-align: center;">Consumidores</td><td style="text-align: center;">Filtrando por meio do MDM</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Portal de loja comercial</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Segurança e identidade</th>
</tr><tr>
<td>Fazer logon com Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Fazer logon com a conta da Microsoft (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Credenciais da próxima geração com o PIN Unlock</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Inicialização segura</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Manutenção e suporte</th>
</tr><tr>
<td>Atualizações automáticas do sistema à medida que elas chegam</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update para negócios</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Branch de manutenção em longo prazo</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Notas de versão anteriores
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte também
* [Problemas conhecidos do HoloLens](hololens-known-issues.md)
* [Recursos comerciais](commercial-features.md)
* [Instalar as ferramentas](install-the-tools.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
