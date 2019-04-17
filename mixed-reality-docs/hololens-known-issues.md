---
title: Problemas conhecidos do HoloLens
description: Esta é a lista dos problemas conhecidos que podem afetar os desenvolvedores do HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 04/1/2019
ms.topic: article
keywords: solucionar problemas, problema conhecido, ajuda
ms.openlocfilehash: a92ab52c899de44f9c5c8c86ebb6f9cd8433d395
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590990"
---
# <a name="hololens-known-issues"></a>Problemas conhecidos do HoloLens

Esta é a lista atual de problemas conhecidos que afetam os desenvolvedores de HoloLens. Verifique aqui primeiro se você estiver vendo um comportamento estranho. Essa lista será mantida atualizada à medida que novos problemas são descobertos ou relatados, ou os problemas sejam resolvidos em futuras atualizações de software do HoloLens.

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>Problemas ao iniciar o Microsoft Store e aplicativos no HoloLens

>[!IMPORTANT]
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
* Ao implantar um aplicativo do Visual Studio para o HoloLens, você poderá ver o erro: **A operação solicitada não pode ser executada em um arquivo com um usuário mapeado seção aberto. (Exceção de HRESULT: 0x800704C8)**. Se isso acontecer, tente novamente e sua implantação geralmente será bem-sucedida.

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
