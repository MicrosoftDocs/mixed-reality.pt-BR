---
title: Problemas conhecidos do HoloLens
description: Esta é a lista dos problemas conhecidos que podem afetar os desenvolvedores do HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: solucionar problemas, problema conhecido, ajuda
ms.openlocfilehash: 1ef9e9f411e16d2f604930f3146ede1d03d7c0f6
ms.sourcegitcommit: c36b8c8573f51afa79504c4a17084e4f55d2f664
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67789486"
---
# <a name="hololens-known-issues"></a>Problemas conhecidos do HoloLens

Esta é a lista atual de problemas conhecidos que afetam os desenvolvedores de HoloLens. Verifique aqui primeiro se você estiver vendo um comportamento estranho. Essa lista será mantida atualizada à medida que novos problemas são descobertos ou relatados, ou os problemas sejam resolvidos em futuras atualizações de software do HoloLens.

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>Não é possível conectar-se e implante em HoloLens através do Visual Studio

>[!NOTE]
>Última atualização: 7/8 @ 7:25 PM - a equipe identificou a causa raiz e atualmente está trabalhando em corrigir. Solução alternativa disponível abaixo. 

Fomos capazes de identificar a causa raiz desse problema. Os usuários que é usado o Visual Studio 2015 ou versões anteriores do Visual Studio 2017 para implantar e depurar aplicativos em seus HoloLens e usadas subsequentemente as versões mais recentes do Visual Studio 2017 ou Visual Studio de 2019 com o mesmo HoloLens serão afetados. 

As versões mais recentes do Visual Studio implantem uma nova versão de um componente, mas os arquivos da versão mais antiga restantes no dispositivo, fazendo com que a versão mais recente falhe.  Isso faz com que a mensagem de erro a seguir: DEP0100: Certifique-se de que esse dispositivo de destino tem o modo de desenvolvedor habilitado. Não foi possível obter uma licença de desenvolvedor no <ip> devido ao erro 80004005.
 
**Solução alternativa**: 

No momento, nossa equipe está trabalhando em uma correção. Enquanto isso, você pode usar as seguintes etapas para contornar o problema e ajudar a desbloquear a implantação e depuração:  
1. Abrir o Visual Studio
2. Arquivo -> Novo -> projeto
3. O Visual C# -> Windows Desktop -> aplicativo de Console (.NET Framework)
4. Dê ao projeto um nome (por exemplo, HoloLensDeploymentFix) e verifique se a estrutura é definida pelo menos .NET Framework 4.5, em seguida, clique em Okey.
5. Clique com botão direito no nó referências no Gerenciador de soluções e adicione as seguintes referências (clique para a seção 'Procurar' e ' Procurar... ' botão):
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >Se você não tiver 10.0.18362.0 instalado, use a versão mais recente que você tem.
 
6. Clique com botão direito no projeto no Gerenciador de soluções e escolha Adicionar -> Item existente.
 
7. Navegue até C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86 e altere o filtro "todos os arquivos (\*.\*)"
 
8. Selecione SirepClient.dll e SshClient.dll e clique em "Adicionar".
 
9. Localize e selecione os dois arquivos no Gerenciador de soluções (eles devem estar na parte inferior da lista de arquivos) e altere "Copiar para diretório de saída" na janela Propriedades para "Copiar sempre"
 
10. Na parte superior do arquivo, adicione o seguinte à lista existente de instruções 'using': 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. Dentro de "static void Main(...)", adicione o seguinte código:
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. Compilar -> a solução de Build
 
13. Abra um prompt de comando para a pasta que contém o .exe compilado (por exemplo, C:\MyProjects\HoloLensDeploymentFix\bin\Debug)
 
14. Execute o executável e forneça o endereço IP do dispositivo como um argumento de linha de comando.  (Se estiver conectado via USB, você pode usar 127.0.0.1, caso contrário, use o endereço IP de WiFi do dispositivo.)  Por exemplo, "HoloLensDeploymentFix 127.0.0.1"
 
15. Depois que a ferramenta foi encerrado sem todas as mensagens (isso deve levar somente alguns segundos), você agora será capaz de implantar e depurar no Visual Studio 2017 ou mais recente.  O uso contínuo da ferramenta não é necessário.

Forneceremos mais atualizações à medida que elas forem disponibilizadas.

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>Problemas ao iniciar o Microsoft Store e aplicativos no HoloLens

>[!NOTE]
>Última atualização: 4 2 @ 10h - problema resolvido. 

Você pode enfrentar problemas ao tentar iniciar o Microsoft Store e aplicativos no HoloLens. Determinamos que o problema ocorre quando as atualizações de aplicativo em segundo plano implantem uma versão mais recente dos pacotes de estrutura em sequências específicas enquanto um ou mais dos seus aplicativos dependentes ainda estão em execução. Nesse caso, uma atualização de aplicativo automáticos entregue a uma nova versão do .NET Native Framework (versão 10.0.25531 para 10.0.27413) causou os aplicativos em execução não está corretamente a atualização para todos os aplicativos em execução, consumindo a versão anterior do framework.  O fluxo para atualizar o framework é o seguinte:-

1.  O novo pacote de estrutura é baixado do repositório e instalado
2.  Todos os aplicativos usando a estrutura mais antiga 'atualizados' para usar a versão mais recente

Se a etapa 2 é interrompida antes da conclusão, em seguida, todos os aplicativos para o qual a estrutura mais recente não foi registrada não serão iniciado do menu Iniciar.  Acreditamos que qualquer aplicativo em HoloLens pode ser afetado por esse problema.

Alguns usuários têm relatado que fechar os aplicativos travados e iniciar outros aplicativos, como o Hub de comentários, 3D visualizador ou fotos resolve o problema para que eles – no entanto, isso não funcionar 100% do tempo.

Temos causados que esse problema não foi causado a atualização em si, mas um bug no sistema operacional que resultaram na atualização do framework .NET nativo que está sendo manipulada incorretamente. Temos o prazer de anunciar que podemos ter identificado uma correção e lançamos uma atualização (versão do sistema operacional 17763.380) que contém a correção. 

Para ver se seu dispositivo pode levar entre a atualização:

1.  Vá para o aplicativo de "Configurações" e abra a "Atualização e segurança"
2.  Clique em "Verificar atualizações"
3.  Se a atualização 17763.380 estiver disponível, atualize para esta compilação para receber a correção do bug de travamento do aplicativo
4.  Após atualizar para esta versão do sistema operacional, os aplicativos devem funcionar conforme o esperado.

Além disso, como fazemos com cada versão do sistema operacional do HoloLens, publicamos a imagem FFU para Microsoft Download Center em https://aka.ms/hololensdownload/10.0.17763.380. 

Se você não gostaria da atualização, lançamos uma nova versão do aplicativo Microsoft Store UWP a partir de 3/29. Uma vez que a versão atualizada do Store:

1) Abra o Store e confirme se ele é carregado.
2) Use o gesto de Bloom para abrir o menu.
3) Tentativa de abrir aplicativos anteriormente interrompidos
3) Se ele ainda não pode ser iniciado, pressionado o ícone do aplicativo quebrado e selecione Desinstalar.
4) Resinstall esses aplicativos da loja.

Se o dispositivo for ainda não foi possível carregar aplicativos, você pode carregar uma versão do .NET Framework nativo e do tempo de execução por meio do Centro de download da prática:

1)  Baixe [este arquivo zip](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) do Microsoft Download Center.  Descompactar produzirá os dois arquivos.  Microsoft.NET.Native.Runtime.1.7.appx e Microsoft.NET.Native.Framework.1.7.appx
2)  Verifique se o dispositivo é desbloqueado de desenvolvimento.  Se ainda não tiver feito isso antes das instruções para fazer isso estão [aqui](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0).
3)  Em seguida, você deseja colocar o Windows Device Portal.  Nossa recomendação é fazer isso por USB e que você faria isso digitando http://127.0.0.1:10080 no seu navegador.  
4)  Uma vez que o do Windows Device Portal-se de você precisa de "sideload" são os dois arquivos que você baixou.  Para fazer isso, você precisará ir para baixo da barra lateral esquerda até chegar à seção "Aplicativos" e clique em "Aplicativos".
5)  Em seguida, você verá uma tela semelhante ao abaixo.  Você deseja ir para a seção que diz "Instalar o aplicativo" e navegue até onde você descompactou esses dois arquivos APPX.  Você pode fazer apenas uma de cada vez, então, depois de selecionar o primeiro deles, clique em "Ir" sob a seção de implantação.  Em seguida, faça isso para o segundo arquivo APPX. 
  ![Windows Device Portal para instalar aplicativos de Sideload](images/20190322-DevicePortal.png)<br>
6)  Neste ponto acreditamos que os aplicativos devem começar a funcionar novamente e você também pode obter para a Store.
7)  Em alguns casos, é necessário executar a etapa adicional de iniciar o aplicativo visualizador 3D antes que os aplicativos afetados serão iniciados. 

Agradecemos sua paciência conforme, avançamos pelo processo de resolver o problema e estamos ansiosos trabalhar com nossa comunidade para criar a realidade misturada bem-sucedida de contínua experiências.

## <a name="connecting-to-wifi"></a>Conectar-se ao Wi-Fi

Durante o OOBE & configurações, há um tempo limite de credencial de 2 minutos. O nome de usuário e a senha deve ser inserido dentro de 2 minutos caso contrário, que o campo de nome de usuário será removido automaticamente.

É recomendável usar um teclado Bluetooth para inserir senhas longas.

## <a name="device-update"></a>Atualização do dispositivo
* 30 segundos depois de uma nova atualização, o shell pode desaparecer uma vez. Execute o **bloom** gesto para retomar a sessão.

## <a name="visual-studio"></a>Visual Studio
* Ver [instalar as ferramentas](install-the-tools.md) para a versão mais recente do Visual Studio recomendado para desenvolvimento HoloLens.
* Ao implantar um aplicativo do Visual Studio para o HoloLens, você poderá ver o erro: **A operação solicitada não pode ser executada em um arquivo com um usuário mapeado seção aberto. (Exceção de HRESULT: 0x800704C8)** . Se isso acontecer, tente novamente e sua implantação geralmente será bem-sucedida.

## <a name="emulator"></a>Emulador
* Nem todos os aplicativos em que a Microsoft Store são compatíveis com o emulador. Por exemplo, Conker Young e fragmentos não são reproduzidos no emulador.
* Você não pode usar a webcam do PC no emulador.
* O recurso de visualização dinâmica do Windows Device Portal não funciona com o emulador. Você ainda pode capturar imagens e vídeos de realidade misturada.

## <a name="unity"></a>Unity
* Ver [instalar as ferramentas](install-the-tools.md) para a versão mais atualizada do Unity recomendada para desenvolvimento HoloLens.
* Problemas conhecidos com o Unity HoloLens Technical Preview estão documentados a [fóruns do HoloLens Unity](http://forum.unity3d.com/threads/known-issues.394627/).

## <a name="windows-device-portal"></a>Windows Device Portal
* O recurso de visualização dinâmica na captura de realidade misturada, pode apresentar vários segundos de latência.
* Na página de entrada Virtual, os controles de gesto e rolagem sob a seção de gestos Virtual não são funcionais. Usá-los não terá efeito. O teclado virtual na mesma página funciona corretamente.
* Depois de habilitar o modo de desenvolvedor nas configurações, pode levar alguns segundos antes da opção para ativar o Portal do dispositivo está habilitada.

## <a name="api"></a>API
* Se o aplicativo define a [focar ponto](focus-point-in-unity.md) por trás do usuário ou o normal para camera.forward, hologramas não serão exibidos em realidade mista de captura fotos ou vídeos. Até que esse bug foi corrigido no Windows, se aplicativos ativamente definam o [focar ponto](focus-point-in-unity.md) eles devem garantir que o normal do plano é definido direta de câmera oposta (normal, por exemplo, = - camera.forward).

## <a name="xbox-wireless-controller"></a>Controlador sem fio do Xbox
* S de controlador do Xbox sem fio deve ser atualizado antes que ele pode ser usado com o HoloLens. Verifique se você está [atualizado](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) antes de tentar emparelhar seu controlador com um HoloLens.
* Se você reinicializar o HoloLens, enquanto o controlador do Xbox sem fio estiver conectado, o controlador não serão reconectados automaticamente à HoloLens. A guia botão acenderá lentamente até o controlador desativado após 3 minutos. Para reconectar seu controlador imediatamente, desligue o controlador, mantendo o botão da guia até que a luz apagar. Quando você liga o controlador novamente, ele se reconectará ao HoloLens.
* Se seu HoloLens entra em modo de espera enquanto o controlador do Xbox sem fio estiver conectado, qualquer entrada no controlador será ativado o HoloLens. Você pode evitar isso, desligar o controlador quando você terminar de usá-lo.
