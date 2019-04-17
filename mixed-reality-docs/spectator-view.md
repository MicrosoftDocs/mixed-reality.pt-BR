---
title: Modo de exibição spectator
description: Visualize hologramas de um dispositivo externo como um meio de demonstrar uma experiência de realidade mista em um vídeo externo ou gravação de vídeo de uma experiência de realidade misturada.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Modo de exibição de spectator, iPhone, iOS, iPad, OpenCV, câmera, ARKit, HoloLens, realidade mista, MixedRealityToolkit, demonstração, registro
ms.openlocfilehash: 77102cf5fb1c23f27f7f2d651c6ca1ae9df5a1d1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590026"
---
# <a name="spectator-view-for-hololens"></a>Modo de exibição de spectator para HoloLens

![Marker](images/SpecViewPhoneHero.jpg)


## <a name="current-refactor"></a>Refatorar atual

> [!NOTE]
>Exibição spectator para HoloLens está sendo ativamente refatorada. Este trabalho se destina a consolidar a visualização e Pro bases de código e estende o suporte para o HoloLens 2. 

Para exibir o atual estado de refatorar o modo de exibição Spectator consulte ' recurso/spectatorView' ramificações em repositórios MixedRealityToolkit tanto o Unity MixedRealityToolkit:

https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/feature/spectatorView/Assets/MixedRealityToolkit.Extensions/SpectatorView

e

https://github.com/Microsoft/MixedRealityToolkit/tree/feature/spectatorView/SpectatorViewPlugin

## <a name="overview"></a>Visão geral

Quando o uso de um HoloLens, muitas vezes esquecemos que uma pessoa que não o tiver no é capaz de enfrentar as maravilhas que podemos. Exibição de spectator permite que outras pessoas vejam em uma tela 2D que um usuário do HoloLens vê em seu mundo.
Exibição de spectator (visualização) é a abordagem rápida e acessível para gravação hologramas em alta definição, enquanto o modo de exibição de Spectator Pro destina-se para a gravação de qualidade profissional de hologramas.

A tabela a seguir mostra as opções e seus recursos. Escolha a opção que melhor atenda às suas necessidades de gravação de vídeo:

|                                      | Modo de exibição spectator (visualização) |              Spectator exibir Pro              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Qualidade do HD                         |         Full HD         |        Qualidade profissional filmagem (conforme determinado pela DSLR)      |
| Movimentação da câmera fácil                      |            ✔            |                                             |
| Modo de exibição de terceira pessoa                    |            ✔            |                      ✔                      |
| Podem ser transmitidos a telas           |            ✔            |                      ✔                      |
| portátil                             |            ✔            |                                             |
| Sem fio                             |            ✔            |                                             |
| Hardware necessário adicional         |     iPhone (ou iPad)    | HoloLens + simuladores de carga + tripé + DSLR + PC + Unity |
| Investimento de hardware                  |           Baixo           |                     Alto                    |
| Plataforma cruzada                       |           iOS           |                                             |
| Visualizador pode interagir                  |            ✔            |                                             |
| Sistema de rede necessária (UNET scripting) |            ✔            |                      ✔                      |
| Duração de instalação do tempo de execução               |         Instante         |                     Modo Lento                    |

## <a name="spectator-view-preview"></a>Modo de exibição spectator (visualização)

![Marker](images/SpecViewPhoneDemo.jpg)

### <a name="use-cases"></a>Casos de uso

- Hologramas filmagem em alta definição: Usando o modo de exibição de Spectator (visualização), você pode registrar uma experiência de realidade misturada usando um iPhone. Registre-se em alta definição completa e aplicar a suavização hologramas e até mesmo sombras. É uma maneira rápida e econômica para capturar o vídeo de hologramas.
- Demonstrações ao vivo: Experiências de realidade mista do live Stream a uma Apple TV diretamente do seu iPhone ou iPad, sem atraso!
- Compartilhe a experiência com convidados: Permitem que os usuários não HoloLens experiência hologramas diretamente de seus telefones ou tablets.

### <a name="current-features"></a>Recursos atuais

- A descoberta automática de adição de telefones para a sessão de rede.
- Manipulação automática de sessão, para que os usuários são adicionados à sessão correta.
- Sincronização espacial de hologramas, para que todos vejam hologramas no mesmo local exato.
- suporte para iOS (dispositivos habilitados para ARKit).
- Diversas convidadas do iOS.
- Gravação de vídeo + hologramas + som ambiente + som holograma.
- Compartilhe folha para salvar o vídeo, envie por email ou compartilhar com outros aplicativos de suporte.


>[!NOTE] 
>O código de exibição Spectator (versão prévia) não pode ser usado com o código da versão Spectator exibição Pro. É recomendável para implementá-la em novos projetos em que a gravação de vídeo da hologramas é necessária.

<br>

>[!VIDEO https://www.youtube.com/embed/3fXlPw_FGLg]


### <a name="licenses"></a>Licenças

- [OpenCV - (licença BSD de cláusula de 3)](https://opencv.org/license.html)
- [Unity ARKit - (licença MIT)](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/src/3691df77caca2095d632c5e72ff4ffa68ced111f/LICENSES/MIT_LICENSE?at=default&fileviewer=file-view-default)

## <a name="how-to-set-up-spectator-view-preview"></a>Como configurar o modo de exibição Spectator (visualização)

### <a name="requirements"></a>Requisitos

- [Modo de exibição de spectator plug-in e os binários necessários do OpenCV](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin) -detalhes sobre como criar o Spectator exibição nativo plug-in podem ser encontrados abaixo. Dos binários gerados, você precisará:

    - opencv_aruco343.dll
    - opencv_calib3d343.dll
    - opencv_core343.dll
    - opencv_features2d343.dll
    - opencv_flann343.dll
    - opencv_imgproc343.dll

    - zlib1.dll
    - SpectatorViewPlugin.dll
- Modo de exibição de spectator usa Unity de rede (UNET) para sua descoberta de rede e sincronizando espacial. Isso significa que toda a interatividade durante o aplicativo precisa ser sincronizado entre os dispositivos.
- Unity 2017.2.1p2 ou posterior
- Hardware
    - A HoloLens
    - PC do Windows que executam o Windows 10
    - Dispositivo compatível com o ARKit (iPhone 6s em diante / iPad Pro 2016 em diante / iPad 2017 em diante)-executando o iOS 11 ou superior
    - Mac com xcode 9.2 em diante
- Conta de desenvolvedor da Apple, livre ou [pago](https://developer.apple.com/)
- Microsoft Visual Studio 2017

### <a name="building-the-spectator-view-native-plugin"></a>Criando o plug-in nativo do modo de exibição Spectator

Para gerar os arquivos necessários, siga estas etapas: https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md

### <a name="project-setup"></a>Configuração do projeto

1. Prepare sua cena, garantindo que todos os gameobjects visível dentro de sua cena estão contidas em um gameobject de raiz do mundo.

    ![World Root](images/SpecViewPhoneWorldRoot2.PNG)

2. Adicionar pré-fabricado SpectatorView ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) na sua cena.
3. Adicionar pré-fabricado SpectatorViewNetworking ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) na sua cena.
4. Selecione o gameobject SpectatorViewNetworking e no componente SpectatorViewNetworkingManager, há algumas coisas que você pode vincular-se. Se a esquerda inalterado irá procurar esse componente scripts necessários no tempo de execução.
    - Marcador detecção HoloLens -> Hololens/SpectatorView/MarkerDetection
    - Marcador geração 3D -> SpectatorView/IPhone/SyncMarker/3DMarker

    ![Descoberta de rede SpectatorView](images/SpecViewPhoneNetworkDiscovery.PNG)

### <a name="networking-your-app"></a>Seu aplicativo de rede

- Exibição de spectator usa UNET para sua rede e gerencia todas as conexões de cliente de host para você.
- Quaisquer dados específicos do aplicativo deve ser sincronizado e implementada por você, usando, por exemplo, SyncVars, NetworkTransform, NetworkBehavior.
- Para obter mais informações sobre a rede do Unity, visite [com vários participantes e rede](https://docs.unity3d.com/Manual/UNet.html). (Observação: UNet foi preterido; o refactor atual da Base de código do modo de exibição Spectator solucionará esse problema)

### <a name="building-for-each-platform-hololens-or-ios"></a>Criando para cada plataforma (HoloLens ou iOS)

- Ao compilar para iOS, verifique se que você remove o componente GLTF de MRTK, pois isso ainda não é compatível com essa plataforma.
- No nível superior de um pré-fabricado SpectatorView há um componente chamado 'Alternador de plataforma'. Selecione a plataforma que você deseja compilar para.
    - Se você selecionar 'Hololens' você deve ver todos os gameobjects sob o gameobject iPhone no pré-fabricado SpectatorView que se tornam inativo e todos os gameobjects em 'Hololens' se tornar ativo.
    - Isso pode demorar um pouco, dependendo da plataforma que você escolher o HoloToolkit está sendo adicionado ou removido do projeto.

    ![Alternador de plataforma](images/SpecViewPhoneSwitcher.PNG)

- Verifique se que você compilar todas as versões do aplicativo usando a mesma instância de editor do Unity (Unity não fechar entre compilações do) devido a um problema não resolvido com o Unity.

### <a name="running-your-app"></a>Executar seu aplicativo

Depois que você criou e implantou uma versão do seu aplicativo no iPhone e no HoloLens, você poderá conectá-los.

1. Certifique-se de que ambos os dispositivos estão na mesma rede Wi-Fi.
2. Inicie o aplicativo em ambos os dispositivos, sem nenhuma ordem específica. O processo de iniciar o aplicativo no iPhone deve disparar a câmera HoloLens para ativar e começar a tirar fotos.
3. Assim que o aplicativo de iPhone é iniciado, ele procurará superfícies como andares ou tabelas. Quando as superfícies forem encontradas, você deverá ver um marcador semelhante ao mostrado abaixo. Mostre esse marcador para o HoloLens.

    ![Marker](images/SpecViewPhoneMarker.PNG)

4. Depois que o marcador foi detectado pelo HoloLens ele desaparecerá e ambos os dispositivos devem ser conectados e sincronizados espacialmente.

### <a name="recording-video"></a>Vídeo de gravação

1. Para capturar e salvar um vídeo do iPhone, toque e segure a tela por 1 segundo. Isso abrirá o menu de gravação.
2. Toque no botão de registro de vermelho, isso iniciará uma contagem regressiva antes de começar a gravar a tela.
3. Para concluir a gravação de toque e mantenha a tela para outra 1 segundo, em seguida, toque no botão Parar.
4. Depois que o vídeo gravado for carregada, um botão Visualizar (botão azul) será exibida, toque para assistir o vídeo gravado.
5. Abra a folha de compartilhamento e selecione Salvar a câmera.

### <a name="example-scene"></a>Cena de exemplo

Uma cena de exemplo pode ser encontrada no [HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)

### <a name="troubleshooting"></a>Solução de problemas

**O Editor do Unity não se conecte a uma sessão hospedada por um dispositivo HoloLens**

- Isso pode ser o Firewall do Windows.
- Vá para opções de Firewall do Windows.
- Permitir que um aplicativo ou recurso pelo Firewall do Windows.
- Para todas as instâncias do Editor do Unity em escala lista, domínio, privado e público.
- Em seguida, volte para as opções de Firewall do Windows.
- Clique em configurações avançadas.
- Clique em regras de entrada.
- Todas as instâncias do Editor do Unity devem ter um tique verde.
- Para todas as instâncias do Unity Editor que não têm um tique verde:
    - Clique duas vezes nele.
    - Na caixa de diálogo de ação, selecione Permitir a conexão.
    - Clique em OK.
    - Reinicie o Editor do Unity.

**Em tempo de execução, a tela de iPhone diz "Localizando Floor..." mas não exibe um marcador de AR.**

- O iPhone está procurando uma superfície horizontal então tente apontando para a câmera do iPhone em direção ao chão ou uma tabela. Isso ajudará a ARKit encontrar superfícies necessários para a sincronização espacialmente com o HoloLens.

**HoloLens câmera ativa automaticamente quando iPhone tenta ingressar.**

- Verifique se o HoloLens e iPhone estão em execução na mesma rede Wi-Fi.

**Ao iniciar um aplicativo de modo de exibição Spectator em um dispositivo móvel, outras hololens executando outros aplicativos de modo de exibição Spectator ativar sua câmera**

- Ir para o componente NewDeviceDiscovery e altere a porta a chave de difusão e difusão para dois valores exclusivos.
- Vá para SpectatorViewDiscovery e altere a chave de difusão e a porta de transmissão para outro conjunto de números exclusivos.

**O HoloLens não se conecte com o Editor do Unity do mac.**

- Esse é um problema conhecido que poderia ser vinculado para a versão do Unity. Criando para o iPhone ainda deve trabalhar e conecte-se como normal.

**A câmera HoloLens ativa, mas não é capaz de verificar o marcador.**

- Certifique-se de que você criar todas as versões do aplicativo usando a mesma instância do Editor do Unity (do Unity não fechar entre compilações). Isso é devido a um problema desconhecido com o Unity.

## <a name="spectator-view-pro"></a>Spectator exibir Pro

![Exibir configuração de spectator](images/spectatorview-300px.png)

Usando o modo de exibição de Spectator Pro envolve estes quatro componentes:
1. Um aplicativo criado especificamente para habilitar o modo de exibição spectator, que é baseado no [compartilhadas de experiências na realidade mista](shared-experiences-in-mixed-reality.md).
2. Um usuário vestindo HoloLens usando o aplicativo.
3. Um spectator exibição câmera simuladores de carga fornecendo um vídeo da perspectiva da terceira pessoa.
4. Um PC desktop executando o aplicativo de experiência e a composição de hologramas em um vídeo de modo de exibição spectator.

![Instalação de modo de exibição Pro spectator](images/hololensspectatorview-500px.jpg) 

### <a name="use-cases"></a>Casos de uso

>[!VIDEO https://www.youtube.com/embed/DgIHjxoPy_c]


*Exibição de spectator pode ser usada para compartilhar suas criações holográfica, independentemente de estarem uma demonstração ao vivo, um clipe de vídeo ou uma imagem estática.*


Há três cenários principais que funcionam bem com essa tecnologia:

**1. Captura de fotos**<br>
Usando essa tecnologia, você pode capturar imagens de alta resolução do seu hologramas. Essas imagens podem ser usadas para apresentar o conteúdo em eventos de marketing, enviar para seus clientes potenciais ou até mesmo enviar seu aplicativo para a Windows Store. Você pode decidir qual câmera foto que você deseja usar para capturar essas imagens, como tal, você pode preferir uma câmera DSLR de qualidade.


![Exemplo de captura de foto exibição Pro spectator](images/fall-350px.jpg)<br>
*Exemplo de captura de foto - facilitando aparecer o chão é composto de lava.*


**2. Captura de vídeo**<br>
Vídeos são a melhor história informando ao mecanismo para compartilhar uma experiência de aplicativo holográfica com muitas pessoas. Exibição spectator permite que você escolha a câmera, lente e enquadramento mais adequado, como você deseja demonstrar seu aplicativo. Isso coloca você no controle de qualidade de vídeo com base no hardware de vídeo, você tem disponível.

![Exemplo de captura de vídeo exibição Pro spectator](images/spectatorviewvideo.gif)<br>
*Exemplo de captura de vídeo - gravação de uma experiência de colaboração de realidade misturada.*


**3. Demonstrações ao vivo**<br>
Exibição de spectator é uma abordagem preferencial para demonstrações ao vivo em que a posição da câmera permanece estável ou controlado. Como você pode usar uma câmera de vídeo de alta qualidade, você também pode produzir destinadas a uma tela grande de imagens de alta qualidade. Isso também é adequado para streaming demonstrações ao vivo em uma tela, possivelmente para participantes adiantados esperando sua vez na linha.

### <a name="comparing-video-capture-techniques"></a>Comparando as técnicas de captura de vídeo

[Misto captura realidade](mixed-reality-capture.md) (MRC) fornece uma composição de vídeo de o usuário HoloLens está vendo de um pessoa primeiro ponto de vista. Modo de exibição spectator produz um vídeo de uma perspectiva de terceira pessoa, permitindo que o observador de vídeo ver o ambiente com hologramas e o usuário usando um dispositivo HoloLens. Como você tem uma opção de câmera, modos de exibição spectator também podem produzir uma resolução mais alta e imagens de melhor qualidade que a câmera HoloLens interna usado para imagens MRC. Por esse motivo, a exibição spectator é mais adequada para imagens de aplicativo na Store do Windows, vídeos, de marketing ou para a projeção de uma exibição ao vivo para um público-alvo.

![Câmera profissional exibição Pro spectator usada em apresentações de palestra da Microsoft](images/spectator-view-professional-red-camera-300px.jpg)<br>
*Câmera profissional exibição Pro spectator usada em apresentações de palestra da Microsoft*


Modo de exibição spectator tem sido uma parte essencial de como Microsoft HoloLens apresentou experiências para o público desde o início quando o produto foi lançado em janeiro de 2015. A instalação profissional usou tinha altas demandas e uma marca de preço cara para acompanhá-lo. Por exemplo, a câmera usa um sinal de genlock para garantir que o tempo preciso que coordena com o sistema de acompanhamento de HoloLens. Nessa configuração, mover a câmera do modo de exibição spectator era possível, mantendo hologramas estável para coincidir com a experiência de alguém que esteja vendo a experiência diretamente no HoloLens.

A versão do código-fonte aberto do modo de exibição spectator compensa a capacidade de mover os simuladores de carga de câmera para reduzir drasticamente o custo da instalação geral. Este projeto usa uma câmera externa rigidamente montada em um HoloLens tire fotos de alta definição e de vídeo do seu projeto do Unity holográfico. **Durante a demonstrações ao vivo, a câmera deve permanecer em uma posição fixa.** Movimento da câmera pode levar a tremulação holograma ou descompasso. Isso ocorre porque o tempo de quadro de vídeo e a renderização de hologramas no PC podem não ser sincronizados com precisão. Portanto, mantendo a câmera estável ou limitar o movimento produzirá um resultado perto o que pode ver a pessoa que utilize um HoloLens.

Para tornar seu aplicativo pronto para exibição spectator, você precisará criar uma [compartilhado experiência](holograms-240.md) aplicativo e certifique-se de que o aplicativo pode ser executado no HoloLens, bem como a área de trabalho no editor do Unity. A versão da área de trabalho do aplicativo terá componentes adicionais criados nessa composição de feed de vídeo com as hologramas renderizadas.

## <a name="how-to-set-up-spectator-view-pro"></a>Como configurar o modo de exibição de Spectator Pro 

### <a name="requirements"></a>Requisitos

![Modo de exibição spectator simuladores de carga Pro](images/spectatorviewrig-350px.jpg)

#### <a name="hardware-shopping-list"></a>Lista de compras de hardware

Abaixo está uma lista de recomendados de hardware, mas você pode fazer experiências com outras unidades compatíveis muito. 

|Componente de hardware                                                                     |Recomendação               | 
|:--------------------------------------------------------------------------------------|:----------------------------|
|A configuração de PC que funciona para o desenvolvimento holográfico com o emulador do HoloLens  |                              | 
|Câmera com saída de HDMI ou captura de fotos do SDK                                             | Para a foto e captura de vídeo, nós testamos a [Canon EOS 5D marca III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III) câmera. Para demonstrações ao vivo, testamos a [Blackmagic Design produção câmera 4K](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k).<br><br>Observe que todas as câmeras com HDMI horizontalmente (por exemplo, GoPro) devem funcionar. Muitos dos nossos vídeos usam o [lente do EF Canon mm 14 f/2.8 L II USM Wide ângulo fixo](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q), mas você deve escolher uma lente de câmera que atenda às suas necessidades. | 
|Captura de cartão para seu computador para obter quadros de cor da câmera para calibrar o simulador de carga e visualizar sua cena de composição |  Nós testamos a [placa de captura Blackmagic Design intensidade Pro 4K](https://www.amazon.com/dp/B00U3QNP7Q). | 
|Cabos                                                                                 |  [HDMI para Mini HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00) para anexar a câmera em seu cartão de captura. Verifique se que você comprar um fator de formulário HDMI que se ajusta sua câmera. (GoPro, por exemplo, gera sobre [Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1).)<br><br>[Cabo HDMI](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1) para exibir o feed em um monitor de visualização ou televisão de composição | 
|Máquinas colchete alumínio para se conectar a seu HoloLens à câmera. | [Colchete de alumínio](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/HoloLens_Mount.stp)   | 
|3D impresso adaptador para conectar-se a montagem de HoloLens para hotshoe a câmera.| [Adaptador de impressão 3D](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/Mount_Adapter.stl)  | 
|Fastener Hotshoe para montar o adaptador hotshoe                                       |  [Hotshoe Fastener](https://www.amazon.com/Fotasy-SCX2-Adapter-Premier-Cleaning/dp/B00HPAPFNU/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) | 
|Ferramentas, bolts e nuts variados                                                |  [4/1-20" nuts](https://www.amazon.com/Hillman-Group-150003-20-Inch-100-Pack/dp/B000BPEPNW/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img)<br>[1/4 – 20 "x 3/4" Bolts](https://www.amazon.com/Hard-Find-Fastener-014973100032-4-20-Inch/dp/B004S6RZPK/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) <br>[Driver sabor nozes 7/16](https://www.amazon.com/Klein-Tools-630-7-Cushion-Grip-Hollow-Shank/dp/B000BPG4CW/ref=sr_1_1?ie=UTF8&qid=1479853212&sr=8-1)<br>[T15 Torx](https://www.amazon.com/Stanley-60-011-Standard-Torx-Screwdriver/dp/B000KFXDWW/ref=sr_1_1?ie=UTF8&qid=1479853303&sr=8-1)<br>[T7 Torx](https://www.amazon.com/SE-7542ST-6-Piece-Professional-Screwdriver/dp/B000ST3K3W/ref=sr_1_1?ie=UTF8&qid=1479853479&sr=8-1) | 

#### <a name="software-components"></a>Componentes do software

1. Software baixado do [projeto do GitHub para o modo de exibição spectator](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView).
2. [Placa de captura de BlackMagic SDK](https://www.blackmagicdesign.com/support). \
 Pesquise pelo desenvolvedor de vídeo da área de trabalho do SDK em "Downloads mais recentes".
3. [Tempo de execução de vídeo do Desktop BlackMagic](https://www.blackmagicdesign.com/support). \
 Pesquise a atualização de Software de vídeo da área de trabalho em "Downloads mais recentes". \
 Verifique se as correspondências de número de versão a versão do SDK.
4. [3.1 OpenCV](https://opencv.org/releases.html) para calibragem ou captura de vídeo sem cartão Blackmagic captura.
5. [Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) (opcional). \
 Se você estiver usando uma câmera Canon e ter acesso ao SDK Canon, você pode vincular sua câmera a seu computador para gerar imagens de resolução mais alta.
6. O Unity para o desenvolvimento de aplicativos holográfica. \
 Versão com suporte pode ser encontrada no projeto de OSS.
7. Visual Studio 2015 com as atualizações mais recentes.

### <a name="building-your-own-spectator-view-pro-camera"></a>Criando sua própria câmera Spectator exibição Pro

**E ISENÇÃO DE RESPONSABILIDADE:** Ao fazer modificações em seu hardware HoloLens (incluindo, mas não limitado a, configurando o HoloLens para "exibição spectator") básica precauções de segurança devem sempre ser observadas. Ler todas as instruções e manuais antes de fazer modificações. É sua responsabilidade Siga todas as instruções e usar as ferramentas, conforme indicado. Tenha comprado ou licenciado seu HoloLens com uma garantia limitada ou nenhuma garantia. Leia seu aplicáveis [contrato de licença do HoloLens ou termos de uso e venda](https://www.microsoft.com/hololens/support/warranty) para entender as opções de garantia.

<br>

>[!VIDEO https://www.youtube.com/embed/aKX8UMejtWc]

#### <a name="rig-assembly"></a>Assembly de simuladores de carga

![Montado Spectator exibição Pro simuladores de carga com câmera HoloLens e DSLR.](images/assembly.gif)<br>
*Simuladores de carga Spectator exibição Pro montado com câmera HoloLens e DSLR*


* Use uma chave de fenda T7 para remover o headband do HoloLens. Depois que os parafusos são flexíveis, examinar-os com um clipe de papel do outro lado.
* Remover o limite de parafuso dentro parte frontal do visor HoloLens com uma pequena fenda.
* Use uma chave de fenda T15 para remover os bolts torx pequeno do suporte do HoloLens para remover a você e os anexos em forma de gancho.
* Coloque o HoloLens no colchete, alinhar a brecha exposta no interior do visor com a extrusão na frente do suporte. Braços dos HoloLens devem ser mantidos em vigor pelos pinos na parte inferior do colchete.
* Anexar novamente a você e os anexos em forma de gancho para proteger o HoloLens para o suporte.
* Anexe o fastener hotshoe para o hotshoe de sua câmera.
* Anexe o adaptador de montagem para o fastener hotshoe.
* Gire o adaptador para que o lado estreito é voltado para a frente e paralelo a lente da câmera.
* Proteja o adaptador em vigor com um 1/4" sabor nozes usando o driver sabor nozes 7/16.
* Posicione o colchete contra o adaptador para que frente do visor dos HoloLens é o mais próximo possível para a frente da lente da câmera.
* Anexe o colchete com 4 1/4" práticos usando o driver sabor nozes 7/16.

#### <a name="pc-setup"></a>Instalação do PC
* Instale o software a partir da seção de componentes de software.
* Adicione o cartão de captura em um slot de PCIe aberto na placa-mãe.
* Conectar um cabo HDMI da câmera para o slot HDMI externo (HDMI-entrada) no cartão de captura.
* Conecte um cabo HDMI do slot HDMI center (saída HDMI) no cartão de captura a um monitor de visualização opcionais.

#### <a name="camera-setup"></a>a instalação da câmera
* Altere sua câmera para o modo de vídeo, portanto, ele produz a resolução de 1920 x 1080 completa em vez de um cortada resolução 3:4.
* Localizar as configurações de HDMI da câmera e habilite **espelhamento** ou **Monitor duplo**.
* Defina a resolução de saída com p 1080.
* Desative **Live exibição na exibição de tela** para qualquer sobreposições de tela não aparecer na composição de feed.
* Ative sua câmera **modo de exibição ao vivo**.
* Se usando o **SDK Canon** e gostaria de usar uma unidade flash, desabilite **solucionar silenciosa de LV**.
* Conectar um cabo HDMI da câmera para o slot HDMI externo (HDMI-entrada) no cartão de captura.

#### <a name="calibration"></a>Calibragem

Depois de configurar seu simuladores de carga de modo de exibição de spectator, você deve calibrar a fim de obter o deslocamento de posição e rotação de sua câmera para o HoloLens.
* Abra a solução do Visual Studio de calibragem sob Calibration\Calibration.sln.
* Nesta solução, você encontrará dependencies.props o arquivo que cria macros para locais das fontes de terceiros 3ª inc.
* Atualizar este arquivo com o local você instalou OpenCV 3.1, o SDK de Blackmagic e o SDK Canon (se aplicável)

![Instantâneo de locais de dependência no Visual Studio](images/dependencies-600px.png)<br>
*Instantâneo de locais de dependência no Visual Studio*


* Imprima o padrão de calibragem Calibration\CalibrationPatterns\2_66_grid_FULL.png em uma superfície plana rígida.
* Conecte seu HoloLens no seu computador por USB.
* Atualize as definições de pré-processador **HOLOLENS_USER** e **HOLOLENS_PW** na **Stdafx. h** com credenciais de portal de dispositivo dos seus HoloLens.
* Anexe a câmera em seu cartão de captura sobre HDMI e ativá-lo.
* Execute a solução de calibragem.
* Mova o padrão quadriculado em torno do modo de exibição como esta:

![Calibrando a Spectator exibição Pro simuladores de carga](images/calibration.gif)<br>
*Calibrando a Spectator exibição Pro simuladores de carga*


* Uma imagem serão automaticamente executada quando Quadriculado está no modo de exibição. Procure a luz branca no visor dos HoloLens antes de Avançar para a próxima pose.
* Ao terminar, pressione **Enter** com o aplicativo de calibragem concentram-se para criar um **CalibrationData.txt** arquivo.
* Esse arquivo será salvo **Documents\CalibrationFiles\CalibrationData.txt**
* Inspecione esse arquivo para ver se os dados de calibragem serão precisos:
   * **RMS DSLR** devem ser próximas de 0.
   * **HoloLens RMS** devem ser próximas de 0.
   * **RMS estéreo** pode ser de 20 a 50, isso é aceitável, pois o campo de visualização entre as duas câmeras podem ser diferente.
   * **Tradução** é a distância da câmera dos HoloLens até lentes da câmera anexado. Isso é em metros.
   * **Rotação** deve estar próximo a identidade.
   * **DSLR_fov** valor y deve ser próximo o campo de visualização vertical esperado do comprimento do seu Lente focal e qualquer fator de corte de corpo de câmera.
* Se qualquer um dos valores acima não parece fazer sentido, recalibre.
* Copiar esse arquivo para o **ativos** diretório em seu projeto do Unity.

### <a name="compositor"></a>Compositor

O compositor é uma extensão do Unity que é executado como uma janela no editor do Unity. Para habilitar isso, a solução do Visual Studio do Compositor primeiro precisa ser criado.
* Abra a solução do Visual Studio do Compositor em Compositor\Compositor.sln
* Atualize dependencies.props com os mesmos critérios da solução de calibragem acima. Se você seguiu as etapas de calibragem, esse arquivo será já foram atualizado.
* Compile a solução inteira como a versão e a arquitetura que corresponda à arquitetura do sua versão Unity. Em caso de dúvida, compile x86 e x64.
* Se você compilou a solução para x64, crie também o projeto de SpatialPerceptionHelper como x86, pois ele será executado no HoloLens.
* Feche o Unity se ele estiver em execução em seu aplicativo. Unity precisa ser reinicializados se DLLs são alteradas em tempo de execução.
* Execute Compositor\CopyDLL.cmd para copiar as DLLs criadas a partir dessa solução para seu projeto do Unity. Esse script irá copiar as DLLs para o projeto de exemplo incluídos. Depois que você tiver seu próprio projeto configurado, você pode executar CopyDLL com um argumento de linha de comando que aponta para o diretório de ativos do seu projeto para copiar lá também.
* Inicie o aplicativo de exemplo do Unity.

### <a name="unity-app"></a>Aplicativo do Unity

O compositor é executado como uma janela do Editor do Unity. O projeto de exemplo incluído tem tudo o que estiver configurada para a trabalhar com o modo de exibição de spectator de uma vez que o compositor que DLLs são copiadas.

Modo de exibição spectator requer que o aplicativo para ser executado como um [compartilhado experiência](holograms-240.md). Isso significa que as alterações de estado do aplicativo que ocorrem no HoloLens precisam ser ligados para atualizar o aplicativo em execução no Unity muito.

Se a partir de um novo projeto do Unity, você precisará fazer algumas configurações primeiro:
* Cópia **complementos/ativos/HolographicCameraRig** do projeto ao seu projeto.
* Adicionar o MixedRealityToolkit mais recente ao seu projeto, incluindo **compartilhamento**, **RSP**, **gmcs.rsp**, e **smcs.rsp**.
* Adicionar seu **CalibrationData.txt** arquivo ao seu diretório ativos.

![Instantâneo de diretório de ativos do Unity](images/files-400px.png)

* Adicione a **HolographicCameraRig\Prefabs\SpectatorViewManager** pré-fabricado à sua cena e preencha os campos:
   * **HolographicCameraManager** deve ser preenchido com pré-fabricado HolographicCameraManager do diretório HolographicCameraRig pré-fabricado.
   * **Âncora** deve ser preenchido com pré-fabricado âncora do diretório HolographicCameraRig pré-fabricado.
   * **Compartilhamento** deve ser preenchido com pré-fabricado compartilhamento da MixedRealityToolkit.
   * Observação: Se qualquer um desses pré-fabricados já existir em sua hierarquia do projeto, os pré-fabricados existentes serão usados no lugar esses.
   * **IP do modo de exibição de spectator** deve ser o IP do seu HoloLens anexado ao seu simuladores de carga de modo de exibição de spectator.
   * **IP do serviço de compartilhamento** deve ser o IP do computador executando o MixedRealityToolkit SharingService.
   * Opcional: Se você tiver vários spectator exibir simuladores anexados ao PC vários do, **IP do computador Local** deve ser definido com o PC simuladores de carga de modo de exibição spectator se comunicará.

![Propriedades do Gerenciador de exibição de spectator no Unity](images/spectatorviewmanager-500px.png)

* Iniciar o MixedRealityToolkit **serviço de compartilhamento**
* Crie e implante o aplicativo como um UWP de D3D para o HoloLens anexado a simuladores de carga de modo de exibição spectator.
* Implante o aplicativo em qualquer outro dispositivo HoloLens na experiência.
* Verificar a **executado no plano de fundo** caixa de seleção sob **player/configurações de projeto/editar**.

![Executar na configuração do plano de fundo no Unity](images/run-in-bg-400px.png)
* Inicie a janela do compositor em **Spectator exibição/Compositor**

![Modo de exibição do compositor para exibição spectator no Unity](images/compositor-500px.png)

* Essa janela permite que você:
   * Iniciar gravação de vídeo
   * Tirar uma foto
   * Alterar a opacidade de holograma
   * Alterar o deslocamento do quadro (que ajusta o carimbo de hora de cor para compensar a latência de cartão de captura)
   * Abra o diretório em que as capturas são salvos
   * Solicitar dados de mapeamento espacial da câmera spectator exibição (se existir um SpatialMappingManager em seu projeto)
   * Visualize a exibição de composição a cena, bem como cor, hologramas e canal alfa individualmente.
   * Ative sua câmera.
   * Pressione play no Unity.
   * Quando a câmera é movida, hologramas no Unity devem ser de onde eles estão no mundo real em relação à sua cor de câmera do feed.

## <a name="see-also"></a>Consulte também

* [Captura de realidade misturada](mixed-reality-capture.md) 
* [Misto captura realidade para desenvolvedores](mixed-reality-capture-for-developers.md)
* [Compartilhado experiências na realidade mista](shared-experiences-in-mixed-reality.md)
* [Código de exibição (visualização) spectator no GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/SpectatorView)
* [Código nativo do spectator exibição (visualização) no GitHub](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)
* [Código de exibição Pro spectator no GitHub](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)
