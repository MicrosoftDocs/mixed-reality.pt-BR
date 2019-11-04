---
title: Problemas conhecidos do HoloLens
description: Esta é a lista de problemas conhecidos que podem afetar os desenvolvedores do HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: solução de problemas, problema conhecido, ajuda
ms.openlocfilehash: fe4e83764433cea5a772b26796d79ac156a59c5d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434254"
---
# <a name="hololens-known-issues"></a>Problemas conhecidos do HoloLens

Esta é a lista atual de problemas conhecidos para o HoloLens que está afetando os desenvolvedores. Verifique primeiro se você está vendo um comportamento estranho. Essa lista será mantida atualizada conforme novos problemas forem descobertos ou relatados, ou conforme os problemas forem resolvidos em futuras atualizações de software do HoloLens.

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>Não é possível conectar e implantar no HoloLens por meio do Visual Studio

>[!NOTE]
>Última atualização: 8/8 @ 5:23h-o Visual Studio lançou o VS 2019 versão 16,2, que inclui uma correção para esse problema. É recomendável atualizar para esta versão mais recente para evitar que esse erro seja apresentado.

O Visual Studio lançou o VS 2019 versão 16,2, que inclui uma correção para esse problema. É recomendável atualizar para esta versão mais recente para evitar que esse erro seja apresentado.

Causa raiz do problema: os usuários que usaram o Visual Studio 2015 ou versões anteriores do Visual Studio 2017 para implantar e depurar aplicativos em seu HoloLens e, posteriormente, usaram as versões mais recentes do Visual Studio 2017 ou do Visual Studio 2019 com o mesmo HoloLens serão afeta. As versões mais recentes do Visual Studio implantam uma nova versão de um componente, mas os arquivos da versão mais antiga são deixados no dispositivo, fazendo com que a versão mais recente falhe.  Isso causa a seguinte mensagem de erro: DEP0100: Verifique se o dispositivo de destino tem o modo de desenvolvedor habilitado. Não foi possível obter uma licença de desenvolvedor no <ip> devido ao erro 80004005.
 
**Solução do problema**: 

Embora esse problema seja corrigido no Visual Studio 2019 16,2, os desenvolvedores que optam por permanecer em versões anteriores do Visual Studio podem usar as etapas a seguir para contornar o problema e ajudar a desbloquear a implantação e a depuração:  
1. Abrir o Visual Studio
2. Arquivo-> Novo > projeto
3. Visual C# -> área de trabalho do Windows-> aplicativo de Console (.NET Framework)
4. Dê um nome ao projeto (por exemplo, HoloLensDeploymentFix) e verifique se a estrutura está definida para pelo menos .NET Framework 4,5 e clique em OK.
5. Clique com o botão direito do mouse no nó referências em Gerenciador de Soluções e adicione as seguintes referências (clique na seção "procurar" e clique no botão "procurar..." botão):
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >Se você não tiver o 10.0.18362.0 instalado, use a versão mais recente que você tem.
 
6. Clique com o botão direito do mouse no projeto no Gerenciador de Soluções e escolha Adicionar-> item existente.
 
7. Navegue até C:\Arquivos de programas (x86) \Windows Kits\10\bin\10.0.18362.0\x86 e altere o filtro para "todos os arquivos (\*.\*) "
 
8. Selecione SirepClient. dll e SshClient. dll e clique em "Adicionar".
 
9. Localize e selecione ambos os arquivos em Gerenciador de Soluções (eles devem estar na parte inferior da lista de arquivos) e altere "copiar para diretório de saída" na janela Propriedades para "copiar sempre"
 
10. Na parte superior do arquivo, adicione o seguinte à lista existente de instruções ' Using ': 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. Dentro de "static void main (...)", adicione o seguinte código:
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. Build-> solução de compilação
 
13. Abra um prompt de comando para a pasta que contém o Compiled. exe (por exemplo, C:\MyProjects\HoloLensDeploymentFix\bin\Debug)
 
14. Execute o executável e forneça o endereço IP do dispositivo como um argumento de linha de comando.  (Se conectado via USB, você pode usar 127.0.0.1, caso contrário, use o endereço IP WiFi do dispositivo.)  Por exemplo, "HoloLensDeploymentFix 127.0.0.1"
 
15. Depois que a ferramenta sair sem nenhuma mensagem (isso deve levar apenas alguns segundos), agora você poderá implantar e depurar do Visual Studio 2017 ou mais recente.  O uso contínuo da ferramenta não é necessário.


## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>Problemas ao iniciar o Microsoft Store e os aplicativos no HoloLens

>[!NOTE]
>Última atualização: 4/2 @ 10-problema resolvido. 

Você pode enfrentar problemas ao tentar iniciar o Microsoft Store e os aplicativos no HoloLens. Determinamos que o problema ocorre quando as atualizações do aplicativo em segundo plano implantam uma versão mais recente dos pacotes do Framework em sequências específicas, enquanto um ou mais de seus aplicativos dependentes ainda estão em execução. Nesse caso, uma atualização automática de aplicativo forneceu uma nova versão do .NET Native Framework (versão 10.0.25531 para 10.0.27413) fez com que os aplicativos que estão sendo executados não sejam atualizados corretamente para todos os aplicativos em execução que consomem a versão anterior do Framework.  A atualização do Flow for Framework é a seguinte:-

1.  O novo pacote de estrutura é baixado da loja e instalado
2.  Todos os aplicativos que usam a estrutura mais antiga são "atualizados" para usar a versão mais recente

Se a etapa 2 for interrompida antes da conclusão, todos os aplicativos para os quais a estrutura mais recente não foi registrada falharão ao iniciar no menu iniciar.  Acreditamos que qualquer aplicativo no HoloLens poderia ser afetado por esse problema.

Alguns usuários relataram que o fechamento de aplicativos suspensos e a inicialização de outros aplicativos, como hub de comentários, visualizador 3D ou fotos, resolve o problema para eles-no entanto, isso não funciona 100% do tempo.

Temos a raiz causada que esse problema não foi causado pela atualização em si, mas um bug no sistema operacional que resultou na atualização do .NET Native Framework sendo tratada incorretamente. Temos o prazer de anunciar que identificamos uma correção e lançamos uma atualização (versão do sistema operacional 17763,380) que contém a correção. 

Para ver se o dispositivo pode fazer a atualização:

1.  Vá para o aplicativo "configurações" e abra "atualizar & segurança"
2.  Clique em "verificar atualizações"
3.  Se a atualização para o 17763,380 estiver disponível, atualize para esse Build para receber a correção para o bug de parada do aplicativo
4.  Após a atualização para esta versão do sistema operacional, os aplicativos devem funcionar conforme o esperado.

Além disso, como fazemos com cada versão do sistema operacional do HoloLens, publicamos a imagem FFU no centro de download da Microsoft em https://aka.ms/hololensdownload/10.0.17763.380. 

Se você não quiser fazer a atualização, lançamos uma nova versão do aplicativo Microsoft Store UWP a partir de 3/29. Quando você tiver a versão atualizada do repositório:

1) Abra o repositório e confirme se ele é carregado.
2) Use o gesto de flor para abrir o menu.
3) Tentativa de abrir aplicativos interrompidos anteriormente
3) Se ainda não puder ser iniciado, toque e mantenha o ícone do aplicativo interrompido e selecione Desinstalar.
4) Resinstall esses aplicativos da loja.

Se o dispositivo ainda não puder carregar aplicativos, você poderá Sideload uma versão do .NET Native Framework e o tempo de execução por meio do centro de download fazendo:

1)  Baixe [este arquivo zip](https://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) do centro de download da Microsoft.  O descompactar produzirá dois arquivos.  Microsoft. NET. Native. Runtime. 1.7. Appx e Microsoft. NET. Native. Framework. 1.7. Appx
2)  Verifique se o dispositivo está desbloqueado.  Se você ainda não fez isso antes das instruções para fazer isso, [Veja aqui](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2F%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0).
3)  Em seguida, você deseja entrar no portal do dispositivo Windows.  Nossa recomendação é fazer isso por USB e fazer isso digitando https://127.0.0.1:10080 em seu navegador.  
4)  Depois de ter o portal do dispositivo Windows, precisamos que você "carregue" os dois arquivos que você baixou.  Para fazer isso, você precisa descer a barra do lado esquerdo até chegar à seção "aplicativos" e clicar em "aplicativos".
5)  Em seguida, você verá uma tela semelhante à mostrada abaixo.  Você deseja ir para a seção que diz "instalar aplicativo" e procurar onde você descompactou esses dois arquivos APPX.  Você só pode fazer uma por vez, portanto, depois de selecionar a primeira, clique em "ir" na seção implantar.  Em seguida, faça isso para o segundo arquivo APPX. 
  ![o portal de dispositivos do Windows para instalar](images/20190322-DevicePortal.png) de aplicativo carregado no lado<br>
6)  Neste ponto, acreditamos que seus aplicativos devem começar a funcionar novamente e que você também pode chegar à loja.
7)  Em alguns casos, é necessário executar a etapa adicional de iniciar o aplicativo do visualizador 3D antes que os aplicativos afetados sejam iniciados. 

Agradecemos sua paciência, já que passamos pelo processo para resolver esse problema, e esperamos continuar trabalhando com nossa comunidade para criar experiências de realidade misturadas bem-sucedidas.

## <a name="connecting-to-wifi"></a>Conectando-se ao WiFi

Durante as configurações de & do OOBE, há um tempo limite de credencial de 2 minutos. O nome de usuário/senha precisa ser inserido em 2 minutos, caso contrário, o campo de nome de usuário será limpo automaticamente.

É recomendável usar um teclado Bluetooth para inserir senhas longas.

>[!NOTE]
> Se a rede incorreta for selecionada durante o OOBE, o dispositivo precisará ser totalmente redefinido. As instruções podem ser encontradas [aqui.](https://docs.microsoft.com//windows/mixed-reality/reset-or-recover-your-hololens#perform-a-full-device-recovery) 

## <a name="device-update"></a>Atualização do dispositivo
* 30 segundos após uma nova atualização, o Shell pode desaparecer uma vez. Execute o gesto de **cair** para continuar a sessão.

## <a name="visual-studio"></a>Visual Studio
* Consulte [instalar as ferramentas](install-the-tools.md) para obter a versão mais atualizada do Visual Studio recomendada para o desenvolvimento do HoloLens.
* Ao implantar um aplicativo do Visual Studio em seu HoloLens, você poderá ver o erro: **a operação solicitada não pode ser executada em um arquivo com uma seção mapeada pelo usuário aberta. (Exceção de HRESULT: 0x800704C8)** . Se isso acontecer, tente novamente e sua implantação geralmente terá sucesso.

## <a name="emulator"></a>Emulador
* Nem todos os aplicativos na Microsoft Store são compatíveis com o emulador. Por exemplo, jovens conkers e fragmentos não são reproduzidos no emulador.
* Não é possível usar a webcam do PC no emulador.
* O recurso de visualização dinâmica do portal do dispositivo Windows não funciona com o emulador. Você ainda pode capturar vídeos e imagens de realidade misturada.

## <a name="unity"></a>Unity
* Consulte [instalar as ferramentas](install-the-tools.md) para obter a versão mais atualizada do Unity recomendada para o desenvolvimento do HoloLens.
* Problemas conhecidos com a visualização técnica do Unity HoloLens são documentados nos [fóruns do Hololens Unity](https://forum.unity3d.com/threads/known-issues.394627/).

## <a name="windows-device-portal"></a>Windows Device Portal
* O recurso de visualização dinâmica na captura da realidade misturada pode exibir vários segundos de latência.
* Na página entrada virtual, os controles de gesto e de rolagem na seção gestos virtuais não são funcionais. Usá-los não terá nenhum efeito. O teclado virtual na mesma página funciona corretamente.
* Depois de habilitar o modo de desenvolvedor em configurações, pode levar alguns segundos antes que a opção para ativar o portal do dispositivo esteja habilitada.

## <a name="api"></a>API
* Se o aplicativo definir o [ponto de foco](focus-point-in-unity.md) por trás do usuário ou o normal para a câmera. encaminhar, os hologramas não aparecerão em fotos ou vídeos de captura de realidade misturada. Até que esse bug seja corrigido no Windows, se os aplicativos definirem ativamente o [ponto de foco](focus-point-in-unity.md) , eles devem garantir que o plano normal esteja definido na frente da câmera oposta (por exemplo, normal =-Camera. Forward).

## <a name="xbox-wireless-controller"></a>Controlador sem fio do Xbox
* Os S do controlador sem fio do Xbox devem ser atualizados para que possam ser usados com o HoloLens. Verifique se você está [atualizado](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) antes de tentar emparelhar seu controlador com um HoloLens.
* Se você reinicializar o HoloLens enquanto o controlador sem fio do Xbox estiver conectado, o controlador não será reconectado automaticamente ao HoloLens. A luz do botão de guia piscará lentamente até que o controlador seja desligado após 3 minutos. Para reconectar o controlador imediatamente, desligue o controlador mantendo o botão guia até que a luz se apague. Quando você ligar o controlador novamente, ele se reconectará ao HoloLens.
* Se o seu HoloLens entrar em espera enquanto o controlador sem fio do Xbox estiver conectado, qualquer entrada no controlador ativará o HoloLens. Você pode evitar isso desligando o controlador quando terminar de usá-lo.
