---
title: Entretenimento baseado na localização com realidade do Windows Mixed
description: Obtenha acesso aos objetos Holographic nativos subjacentes no Unity.
author: jessemcculloch
ms.author: ishitak
ms.date: 08/22/2019
ms.topic: article
keywords: realidade misturada, VR, LBE, local
ms.openlocfilehash: e23d17ff2b07c636c98a9f19a5dd20f4dc558bf7
ms.sourcegitcommit: 5d3be2d7569d912011ea114c0a283bc3c635d5df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69983394"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>Entretenimento baseado na localização com realidade do Windows Mixed

Nos últimos anos, testemunhamos uma quantidade incrível de crescimento e inovação na categoria de entretenimento baseada na localização. Os locais tradicionais, como os parques de tema e os teatros, começaram a oferecer experiências de imersão e de vários jogadores como experiências complementares a corridas e instalações existentes. Novos operadores e locais estão trazendo experiências exclusivas de vários sensorials e vários jogadores a um preço atraente para as massas. Todas essas experiências estão empurrando o envelope para saber o que é possível com realidade misturada.

Este documento é um guia para começar a usar a realidade mista do Windows na categoria entretenimento baseado na localização. As diretrizes abaixo também podem ser aplicáveis a experiências baseadas em local além de entretenimento, como treinamento, design de produto ou outros casos de uso.

## <a name="engineering-faq"></a>Perguntas frequentes sobre Engenharia

### <a name="hardware"></a>Hardware

**PERGUNTAS Qual hardware está disponível da Microsoft e de seus parceiros que posso usar na minha configuração?**

R: A Microsoft e seus parceiros OEM oferecem um portfólio atraente de dispositivos para sua escolha, dependendo de suas necessidades.  

Se as experiências que você está fornecendo aos seus clientes exigem headsets de realidade virtual, os seguintes headsets no mercado da HP, Samsung e Acer são uma ótima opção. Cada headset tem seus próprios atributos diferenciados. Mais detalhes sobre cada um deles.

Reverbo HP: [Detalhes](https://hp.com/go/Reverbpro)

Samsung Odyssey +: [Detalhes](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer [Detalhes](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

Se o seu local for especializado em experiências de realidade mistas ou incrementais que exigem o uso de um headset, você poderá adquirir o Microsoft HoloLens 2 (agora aberto para interesse de ordem anterior).  

HoloLens 2: [Interesse de pré-ordem](https://www.microsoft.com/en-us/hololens/buy)

Se você estiver experimentando experiências que exigem visão avançada da computação, fala e controle de corpo, você pode encontrar o Azure Kinect DK para atender às suas necessidades.  

Kinect do Azure: [Detalhes](https://azure.microsoft.com/en-us/services/kinect-dk/)

**PERGUNTAS Qual é o portfólio de PCs mochila que posso usar para executar minhas experiências de VR no meu PC?**

Para experiências de VR para PC, nossos OEMs oferecem uma seleção incrível de PCs mochila criados exatamente para essa necessidade.

A HP acabou de lançar seu HP VR mochila G2, o PC de portátil mais poderoso do mundo – otimizado para experiências de mobilidade gratuita, agora com 30% mais energia com uma GPU de RTX 2080 dentro. [Detalhes](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>Configuração

**PERGUNTAS Como posso configurar com mais facilidade a instalação e personalizar o portal de realidade misturada para o LBE?**

>[!NOTE]
>Este recurso requer a versão 2000.19061.1011.0 ou superior.  

Você pode achar que precisa de mais personalização do portal de realidade misturada do que normalmente está disponível por meio do aplicativo para implantar aplicativos em quiosques ou experiências personalizadas. A atualização mais recente de julho do portal de realidade misturada dá suporte a várias configurações avançadas que podem ser por meio de um arquivo de configuração para fazer o seguinte:  

Permitir verificações do sistema com falha – normalmente, o processo de instalação verifica a compatibilidade do computador com o Windows Mixed Reality antes de concluir a instalação. Ignorar isso pode causar problemas ao tentar executar a realidade mista do Windows se houver problemas de compatibilidade.  

Ignorar aplicativo complementar do dispositivo – o DCA fornece etapas de configuração específicas do headset fornecidas pelo fabricante e permite a atualização do firmware do headset.  

Ignorar a configuração da sala – em vez de ser solicitado a criar um limite de sala, você pode prosseguir diretamente para o headset no modo encaixado/em pé.  

Ignorar a instalação de aplicativos da loja-a instalação normal instala vários aplicativos da loja, incluindo o visualizador 3D e o complemento do Visualizador do Edge 360. Isso ignorará a instalação desses aplicativos, mas você poderá estar sem a funcionalidade do dispositivo.  

Mostrar visualização em tela inteira – o portal de realidade misturada padrão mostrará a visualização do headset em tela inteira no PC desktop enquanto o headset está em uso.  

Ocultar novo no painel lateral – isso impede que o novo painel para você seja expandido no lançamento do portal de realidade misturada.  

#### <a name="how-to-configure"></a>Como configurar:  

Para definir qualquer uma dessas configurações, você precisa criar um arquivo chamado _userconfig. JSON_ neste diretório: _\\ $env: LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState_

Para a maioria dos usuários, isso parecerá _C:\Users\<username\\ > \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState_

O arquivo JSON deve ter o conteúdo abaixo com "true" definido para qualquer uma das configurações acima que você deseja habilitar:  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**PERGUNTAS Há alguma orientação sobre como configurar o Playspace?**

R: A configuração de um Playspace deve ser feita como você faria com uma experiência de configuração do consumidor. O processo de configuração de sala também permitirá que você defina os limites de sala. Mais detalhes sobre como configurar os limites de sala podem ser lidos [aqui](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

Conforme discutido no documento acima, a Playspace de coordenadas únicas razoável máxima é cerca de 5mx5m. Se você quiser ter uma área maior, poderá usar o recurso âncoras espaciais na pilha da API do Windows Holographic. Usar essa API exigirá engenharia personalizada nas experiências que você está produzindo.  

Mais detalhes sobre como otimizar o conteúdo para diferentes tamanhos de espaço podem ser lidos [aqui](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems).
 

**PERGUNTAS Meu espaço é muito grande e estou com erros quando tento configurar uma experiência de navegação com limites. O que devo fazer para configurar minha experiência de grande roaming de alta disponibilidade?**

R: Para configurar um espaço maior que ~ 18x18ft, você não poderá usar a experiência de limite fornecida pelo sistema.  Os sistemas de limite se baseiam no aproveitamento de uma única "âncora" de coordenada fixa, que pode se tornar instável quando um usuário estiver muito longe da âncora do estágio central. 

Em vez disso, você pode configurar o modo "encaixado", que não exibirá o limite ou configurará um limite de estágio ou Playspace.  Em seguida, você precisará configurar várias âncoras espaciais dentro do aplicativo para fazer referência a áreas de limite físicas. 

O desenvolvedor do aplicativo é responsável por exibir as proteções necessárias para que os usuários não colidem com os arredores físicos.  Elas podem ser paredes digitais dentro da experiência ou um Visual personalizado de limite de jogo. 

Orientação sobre como configurar o limite de sala com WMR pode ser encontrada [aqui](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

**PERGUNTAS Onde está a origem do Playspace?**

R: A origem do Playspace é determinada pela experiência de configuração da sala, mais especificamente a posição de HMD quando o botão central é pressionado durante a instalação. 

### <a name="multi-player-setup"></a>INSTALAÇÃO DE VÁRIOS JOGADORES

**PERGUNTAS Estou implantando uma experiência de vários jogadores no meu local. Isso tem suporte no Windows Mixed Reality?**

R: A ferramenta de pacote de dados espaciais da realidade misturada é um recurso beta que permite localizar vários players no mesmo espaço, permitindo a portabilidade dos dados espaciais de um PC para outro. Você pode acessar a ferramenta e saber mais sobre ela [aqui](mixedrealityspatialdatapackager.md).

### <a name="tracking"></a>CONTROLE ALTERAÇÕES

P: Como funciona a tecnologia de rastreamento em headsets de realidade mista do Windows?  

A realidade misturada compartilha a mesma tecnologia de controle que o HoloLens. Para saber mais sobre o sistema de acompanhamento interno, confira a documentação [aqui](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system).

Para obter uma descrição de como o sistema de mapeamento espacial de nível superior funciona, você pode ler nossa descrição [aqui](spatial-mapping-design.md).

**PERGUNTAS Há alguma prática recomendada para obter um volume de controle confiável?**

Para configurar melhor o ambiente para acompanhar o sucesso, você pode ler as práticas recomendadas nesta [postagem](environment-considerations-for-hololens.md).

**PERGUNTAS Há alguma nuance específica com acompanhamento em espaços de escala de depósito ou otimizações a serem consideradas?**

R: As práticas a seguir podem ajudar com a obtenção de um volume de controle mais confiável:  

Fornecer uma variedade de recursos na sala que se sobrepõem a várias posições ajudará o sistema de controle a obter um bloqueio sólido. Imagine a interlinhagem de pintura aleatória e a hachura, em vez de usar linhas de estilo de delimitação sólida. 

Minimize o intervalo dinâmico de iluminação em sua área sempre que possível. As câmeras de rastreamento em nossa realidade misturada HMDs não são HDR e têm AGC (lucro automático) e o AEC (exposição automática) em ordem para lidar com iluminaçãos diferentes. Dependendo da distribuição da luz da superfície, os padrões e o contraste, AGC ou AEC podem concluir que você está em um quarto de branco ou preto que pode desbotar seus recursos que podem estar na "cor" oposta. Se você estiver tentando pegar uma imagem interior na frente de uma janela exterior com um plano de fundo brilhante e ajustar a exposição para que possa ver os detalhes fora, tudo no interior será doexposto e preto. Ou, se definido para dentro, tudo o que está fora agora estará superexposto e todos os brancos.  

Destaques em uma sala (até mesmo sobrecarga) que estão na exibição se as câmeras de acompanhamento às vezes podem ser culpadas, o que confundi o AEC/AGC das câmeras de acompanhamento. A iluminação plana/difusa ajuda.  

### <a name="mixed-reality-cloud-services-and-azure"></a>SERVIÇOS DE NUVEM DE REALIDADE MISTURADA E AZURE 

**PERGUNTAS Como Microsoft Azure pode ajudar minha escala comercial?**

R: O gerenciamento remoto e local com base no Azure podem ajudar sua empresa a ser controlado por dados, reduzir os custos operacionais e dimensionar a implantação em locais novos e existentes. Os serviços de nuvem do Azure, como o armazenamento do Azure, Azure Functions, serviço de aplicativo, rede do Azure e Hub IOT podem ajudar com os seguintes casos de uso:  

Gerenciamento de & de implantação de dispositivo remoto 

Análise no local em tempo real 

LBE cheia de adaptação inteligente 

Streaming e implantação de conteúdo do LBE 

Calor de preferência do LBE Player 

LBE reserva e sistema de reservas 

**PERGUNTAS Estou desenvolvendo um MMOG espacial para implantar em grande quantidade de espaço. Todos os serviços que me ajudam a gerenciar meu conteúdo e minha persistência de objetos?**

R: As âncoras espaciais do Azure são um novo serviço de realidade misturada que permite experiências de realidade mista de vários usuários, com reconhecimento espacial, em dispositivos de HoloLens, iOS e Android. Você pode aprender mais sobre as âncoras espaciais do Azure [aqui](https://azure.microsoft.com/en-us/services/spatial-anchors/).

**PERGUNTAS. Nosso local é especialista em experiências de vários jogadores e gostaria de concentrar nosso tempo de desenvolvimento em conteúdo e desenvolvimento de front-end. Há ofertas que podem me ajudar a inicializar ou descarregar o desenvolvimento de back-end?**

R: O Azure PlayFab é uma plataforma de back-end completa para jogos ao vivo. Você pode aprender mais sobre isso [aqui](https://playfab.com/).

### <a name="misc"></a>Diversos

**PERGUNTAS Eu uso o SteamVR para implantar minhas experiências. A realidade mista do Windows funciona com o SteamVR?**

R: O Windows Mixed Reality for SteamVR permite que os usuários executem experiências de SteamVR em headsets de imersão de realidade mista do Windows. Saiba mais sobre SteamVR com WMR [aqui](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).

### <a name="support-and-community"></a>Suporte e comunidade  

Abaixo estão alguns recursos úteis para envolver especialistas em nossa equipe, obter suporte para solução de problemas e contribuir para a comunidade de desenvolvimento de realidade misturada mais ampla.  

Se você tiver problemas com recursos lançados publicamente, registre um bug usando o Hub de comentários. para obter diretrizes, consulte esta [página](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback).

Para obter ajuda adicional sobre solução de problemas com o WMR, entre em contato com nossa equipe de suporte ao cliente ao arquivar uma [solicitação de suporte](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782).

Junte-se ao nosso canal de margem de atraso HoloDevelopers para envolver os desenvolvedores que trabalham em realidade misturada e especialistas no assunto da equipe: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter Siga nossa equipe de relações de desenvolvedor da realidade misturada para notícias, eventos e atualizações@MxdRealityDev 

Se você estiver em ou em volta de San Francisco, sempre haverá algo acontecendo no reator da Microsoft. Você pode ver nosso calendário de eventos [aqui](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco).