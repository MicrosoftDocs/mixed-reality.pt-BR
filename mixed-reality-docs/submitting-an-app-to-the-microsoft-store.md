---
title: Enviar um aplicativo para a Microsoft Store
description: Este artigo oferece dicas sobre como enviar seus aplicativos de realidade mista para a Microsoft Store, incluindo como empacotar e testar seu aplicativo e dicas para passar na certificação e ajudar a detectabilidade de seu aplicativo na Store.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: aplicativo, uwp, enviar, envio, filtros, metadados, requisitos do sistema, as palavras-chave, wack, certificação, pacote, appx, gerenciamento de mercadorias
ms.openlocfilehash: 4eb69fbaa22f4864305f09d5e1bf1c1860a0d31f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589745"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Enviar um aplicativo para a Microsoft Store

Ambos [HoloLens](hololens-hardware-details.md) e ativar o computador com Windows 10 seu [fone de ouvido imersivo](immersive-headset-hardware-details.md) executar aplicativos da plataforma Universal do Windows. Se você enviar um aplicativo que dá suporte ao HoloLens ou PC (ou ambos), você vai enviar seu aplicativo para a Microsoft Store por meio [Partner Center](https://partner.microsoft.com/dashboard).

Se você ainda não tiver uma conta de desenvolvedor do Partner Center, você poderá [Inscreva-se hoje](https://developer.microsoft.com/store/register).

## <a name="packaging-a-mixed-reality-app"></a>Empacotando um aplicativo de realidade misturada

### <a name="prepare-image-assets-included-in-the-appx"></a>Preparar os ativos de imagem incluídos o AppX

Há vários ativos de imagem necessários pelo appx Criando ferramentas para compilar seu aplicativo em um pacote appx para enviar para a Store. Você pode saber mais sobre [diretrizes para ativos de bloco e ícone](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) no MSDN.

| Ativos necessários | Escala recomendada | Formato de imagem | Em que isso é exibido? | 
|----------|----------|----------|------------------|
| Logotipo quadrado de 71 x 71 | Qualquer |  PNG | N/D | 
| Logotipo quadrado 150 x 150 | 150 x 150 (100% da escala) ou 225, 225 (150% em escala) | PNG | Iniciar os pinos e todos os aplicativos (se não for fornecido 310 x 310), Store Store sugestões de pesquisa, página de listagem da Store, navegar, pesquisar Store | 
|  Logotipo largo de 310x150 |  Qualquer  |  PNG  |  N/D | 
|  Logotipo da Store |  75 x 75 (150% em escala)  |  PNG  |  Partner Center, o relatório de aplicativo, escrever uma revisão, minha biblioteca | 
|  Tela inicial |  930 x 450 (150% em escala)  |  PNG  |  Iniciador de aplicativos 2D (slate) | 

Também há alguns ativos recomendados que HoloLens podem aproveitar.

| Ativos recomendados | Escala recomendada | Em que isso é exibido? | 
|----------|----------|----------|
|  Logotipo quadrado de 310 x 310 |  310 x 310 (150% em escala) |  Pinos de início e de todos os aplicativos | 

### <a name="live-tile-requirements"></a>Requisitos de bloco em tempo real

O menu Iniciar no HoloLens usará a maior imagem de bloco quadrado incluído.

Você pode ver que alguns aplicativos publicados pela Microsoft tem um iniciador 3D para seu aplicativo. Os desenvolvedores podem adicionar um iniciador 3D para seu aplicativo usando [estas instruções](implementing-3d-app-launchers.md).

### <a name="specifying-target-and-minimum-version-of-windows"></a>Especificando o destino e a versão mínima do Windows

Se seu aplicativo de realidade misturada inclui recursos que são específicos para uma determinada versão do Windows, é importante especificar o destino e as versões de plataforma mínimas que terão suporte no seu aplicativo Windows Universal.

**Isso é especialmente verdadeiro para aplicativos destinados ao [fones imersivos em exposição Windows Mixed Reality](immersive-headset-hardware-details.md), que requerem pelo menos a do Windows 10 Fall Creators Update (10.0; Build 16299) para funcionar corretamente.**

Você será solicitado a definir a versão mínima do Windows e destino quando você cria um novo projeto Universal do Windows no Visual Studio. Você também pode alterar essa configuração para um projeto existente no menu "Project", em seguida, "propriedades do < nome do seu aplicativo >" na parte inferior do menu suspenso.

![Definir mínimo e destinados a versões de plataforma no Visual Studio 2017](images/visual-studio-min-version-500px.png)<br>
Definir mínimo e destinados a versões de plataforma no Visual Studio

### <a name="specifying-target-device-families"></a>Especificando as famílias de dispositivos de destino

Aplicativos de realidade mista do Windows (para ambos [HoloLens](hololens-hardware-details.md) e [fones imersivos em exposição](immersive-headset-hardware-details.md)) fazem parte da plataforma Universal do Windows, portanto, qualquer pacote de aplicativo com um [dafamíliadodispositivodedestino](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)de "Universal" é capaz de executar em HoloLens ou em computadores com Windows 10 com fones imersivos em exposição. Dito isso, se você não especificar uma família de dispositivos de destino em seu manifesto de aplicativo você inadvertidamente pode abrir seu aplicativo até dispositivos do Windows 10 não intencionais. Siga as etapas abaixo para especificar uma família de dispositivos Windows 10 pretendida e, em seguida, [verificar que as famílias de dispositivo corretos sejam selecionadas quando você carregar seu pacote do aplicativo no Partner Center para enviar para a Store.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

Para definir esse campo no Visual Studio, clique com botão direito no Package. appxmanifest e selecione "Exibir código" e localizar o campo de nome TargetDeviceFamily. Por padrão, ele pode parecer com o seguinte:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Se seu aplicativo é criado para **HoloLens**, em seguida, você pode garantir que ele só é instalado em HoloLens, especificando uma família de dispositivo de destino de "Windows.Holographic". 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Se seu aplicativo é criado para **fones imersivos em exposição Windows Mixed Reality**, em seguida, você pode garantir que ele só é instalado em computadores com Windows 10 com o do Windows 10 Fall Creators Update (necessário para o Windows Mixed Reality) ao especificar um destino família do dispositivo de "Windows.Desktop" e MinVersion de "10.0.16299.0".

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

Por fim, se seu aplicativo se destina a ser executados no **HoloLens e o Windows Mixed Reality fones imersivos em exposição**, você pode garantir o aplicativo só fica disponível para essas famílias de dispositivo de duas e ao mesmo tempo garantir que cada um tem como alvo correto versão mínima do Windows, incluindo uma linha para cada família do dispositivo de destino com seu respectivo MinVersion.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Você pode aprender mais sobre o direcionamento de famílias de dispositivos, lendo a [documentação da UWP TargetDeviceFamily](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>Associar aplicativo com a Store

No menu do projeto em sua solução do Visual Studio, escolha "Store > associar aplicativo com o Store". Se você fizer isso, você pode testar os cenários de compra e notificação em seu aplicativo. Quando você associa o seu aplicativo com a Store, esses valores são baixados para o arquivo de manifesto de aplicativo para o projeto atual no computador local:
* Nome de exibição do pacote
* Nome do pacote
* ID do publicador
* Nome de exibição do publicador
* Versão

Se você substituir o arquivo Package. appxmanifest padrão criando um arquivo. XML personalizado para o manifesto, você não pode associar seu aplicativo com o Store. Se você tentar associar um arquivo de manifesto personalizado com a Store, você verá uma mensagem de erro.

### <a name="creating-an-upload-package"></a>Criando um pacote de carregamento

Siga as diretrizes em [Windows Universal de empacotamento de aplicativos para Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2).

A etapa final de criação de um pacote de carregamento é a validação de pacote usando o [Kit de certificação de aplicativos do Windows](#windows-app-certification-kit).

Se você está adicionando um pacote especificamente para HoloLens a um produto existente que está disponível em outras famílias de dispositivos Windows 10, você também deseja saber mais sobre [como números de versão podem afetar os pacotes que são entregues aos clientes específicos ](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx), e [como os pacotes forem distribuídos para sistemas operacionais diferentes](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx).

A orientação geral é que o pacote do número de versão mais alto que é aplicável a um dispositivo será aquele distribuídos pela Store.

Se houver um pacote universal e um pacote de Windows.Holographic e o pacote universal possui um número de versão superior, um usuário do HoloLens baixará o pacote universal número de versão superior, em vez do Windows.Holographic pacote. Há várias soluções para esse problema:
1. Verifique se seus pacotes específicos de plataforma, como Windows.Holographic sempre ter um número de versão superior seus pacotes independentes de plataforma como universal
2. Não é empacotar aplicativos conforme universal se você também tiver pacotes específicos da plataforma - empacotar o pacote universal para as plataformas específicas que você deseja disponível em vez disso

>[!NOTE]
> Você pode declarar um único pacote seja aplicável a várias famílias de dispositivos de destino

3. Crie um único pacote universal que funciona em todas as plataformas. Suporte para isso não é bom no momento para que as soluções acima são recomendadas.

## <a name="testing-your-app"></a>Testando seu aplicativo

### <a name="windows-app-certification-kit"></a>Kit de Certificação de Aplicativos Windows

Quando você cria pacotes de aplicativos para enviar ao centro de parceiros por meio do Visual Studio, o assistente criar pacotes de aplicativos solicitará que você execute o Kit de certificação de aplicativos do Windows contra os pacotes que são criados. Para ter um processo de envio smooth para a Store, é aconselhável verificar se o [Kit de certificação de aplicativos do Windows testa](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) passar em relação a seu aplicativo em seu computador local antes de enviá-los para a Store. Executar o Kit de certificação de aplicativos do Windows em um HoloLens remoto não é suportado atualmente.

### <a name="run-on-all-targeted-device-families"></a>Executar em todas as famílias de dispositivo de destino

A plataforma Universal do Windows permite que você crie um único aplicativo que seja executado em todas as famílias de dispositivo Windows 10. No entanto, ele não garante que os aplicativos Universal Windows funcionará apenas em todas as famílias de dispositivos. Antes de você optar por tornar seu aplicativo disponível em HoloLens ou qualquer outra família de dispositivo do Windows 10 destino, é importante que você [teste o aplicativo](testing-your-app-on-hololens.md) em cada uma dessas famílias de dispositivos para garantir uma boa experiência.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Enviando seu aplicativo de realidade mista para a Store

Se você estiver enviando um aplicativo de realidade misturada baseia-se em um projeto do Unity, consulte este [vídeo](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) primeiro.

Em geral, o aplicativo que funciona no HoloLens e/ou fones imersivos em exposição enviando uma realidade mista do Windows é exatamente como enviar qualquer aplicativo UWP para a Microsoft Store. Depois que você tiver [criou seu aplicativo ao reservar o nome dele](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name), você deve seguir os [lista de verificação de envio de UWP](https://docs.microsoft.com/windows/uwp/publish/app-submissions).

Uma das primeiras coisas que você fará é [selecione uma categoria e subcategoria](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) para a sua experiência de realidade misturada. É importante que você **escolha a categoria mais precisa para seu aplicativo** para que possamos comercialize seu aplicativo nas categorias Store à direita e verifique se ele é exibido usando consultas de pesquisa relevantes. **Listando seu título VR como um jogo não resultará em uma melhor exposição para seu aplicativo,** e podem impedir que ela aparecendo em categorias de ajuste mais e menos cheia.

No entanto, há quatro áreas principais no processo de envio em que você vai querer fazer seleções de específicas de realidade mistas:
1. No **[declarações do produto](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** seção no [propriedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
2. No **[requisitos do sistema](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** seção no [propriedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
3. No **[disponibilidade família do dispositivo](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** seção no [pacotes](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages).
4. Em vários dos **[página de listagem de Store](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** campos.

### <a name="mixed-reality-product-declarations"></a>Declarações de produto de realidade misturada

No **[propriedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** página do processo de envio de aplicativo, você encontrará várias opções relacionadas a realidade misturada no **[declarações de produto](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** seção.

![Declarações de produto de realidade misturada](images/product-declarations-900px.png)<br>
Declarações de produto de realidade misturada

Primeiro, você desejará identificar os tipos de dispositivo para o qual seu aplicativo oferece uma experiência de realidade misturada. Isso garante que seu aplicativo está incluído em coleções, Windows Mixed Reality na Store, e que ele é mostrado aos usuários que navegam a Store depois de se conectar a um fone de ouvido imersivo (ou ao procurar o Store em HoloLens).

Ao lado de "essa experiência foi projetada para Windows Mixed Reality em:"
* Verifique as **PC** caixa apenas se seu aplicativo oferece uma experiência VR quando um fone de ouvido imersivo está conectado ao computador do usuário. Você deve marcar essa caixa se seu aplicativo foi desenvolvido exclusivamente para ser executado em um fone de ouvido imersivo ou se é um PC jogo/aplicativo padrão que oferece um conteúdo de modo de e/ou bônus de realidade misturada quando estiver conectado a um fone de ouvido.
* Verifique as **HoloLens** caixa apenas se seu aplicativo oferece uma experiência holográfica quando ele é executado em HoloLens.
* Verifique **ambos** caixas, se seu aplicativo oferecer uma realidade misturada experiência em ambos os tipos de dispositivo, como o [Academy de realidade mista "Ilha de projeto" aplicativo](mixed-reality-250.md) da Build 2017.

Se você tiver selecionado "PC" acima, você vai querer definir a configuração de realidade misturada"" (nível de atividade). Isso se aplica somente a experiências de realidade mista que são executados em computadores conectados para fones imersivos em exposição, como aplicativos de realidade misturada em HoloLens são mundo em escala e o usuário não define um limite durante a instalação.
* Escolher **Seated + permanente** se seu aplicativo foi projetado com a intenção de que o usuário permaneça em uma posição (um exemplo seria um jogo em que você está encaixado em uma cabine de uma aeronave).
* Escolher **todas as experiências** se seu aplicativo foi projetado com a intenção de que o usuário orienta em torno de dentro dos limites que ele ou ela definida durante a instalação (um exemplo pode ser um jogo onde você etapa lado e pato dodge ataques).

### <a name="mixed-reality-system-requirements"></a>Requisitos do sistema de realidade misturada

Sobre o **[propriedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** página do processo de envio de aplicativo, você encontrará várias opções relacionadas a realidade misturada no **[requisitos do sistema](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** seção.

![Requisitos do sistema](images/system-reqs-800px.png)<br>
Requisitos de sistema

Nesta seção, você identificará mínimos de hardware (obrigatório) e recomendados de hardware (opcional) para seu aplicativo de realidade misturada.

**Entrada de hardware:**

Use as caixas de seleção para informar ao clientes em potencial se seu aplicativo aceita **microfone** (para [entrada de voz](voice-input.md)), **[Xbox controlador ou gamepad](hardware-accessories.md#bluetooth-gamepads)**, e/ou  **[controladores de movimento do Windows Mixed Reality](motion-controllers.md)**. Essas informações serão exibidas na página de detalhes do produto do seu aplicativo na Store e o ajudará a seu aplicativo serão incluídas nas coleções de aplicativo/jogo apropriado (por exemplo, uma coleção pode existir para todos os jogos que dão suporte a controladores de movimento).

Ser ponderada sobre como selecionar as caixas de seleção "mínimos de hardware" ou "hardware recomendado" para tipos de entrada. 

Por exemplo:  
* Se o seu jogo exige controladores de movimento, mas aceita a entrada de voz por meio do microfone, marque a caixa de seleção ao lado de "Controladores de movimento do Windows Mixed Reality" "mínimos de hardware", mas a caixa de seleção "hardware recomendado" ao lado de "Microfone". 
* Se o seu jogo pode ser reproduzido com qualquer um controlador/gamepad ou movimento controladores do Xbox, você pode selecionar a caixa de seleção ao lado de "controlador do Xbox ou gamepad" "mínimos de hardware" e marque a caixa de seleção "hardware recomendado" ao lado do movimento de realidade mista do Windows" controladores de"como controladores de movimento provavelmente oferecerá um Step-up na experiência do gamepad.

**Fone de ouvido imersivo Windows Mixed Reality:**

Que indica se um fone de ouvido imersivo é necessária para usar seu aplicativo, ou é opcional, é essencial para educação e satisfação do cliente.

Se seu aplicativo puder *apenas* ser usado por um fone de ouvido imersivo, marque a caixa de seleção "mínimos de hardware" ao lado de "Windows Mixed Reality imersivo fone de ouvido." Isso será mostrado na página de detalhes do produto do seu aplicativo na Store como um aviso acima do botão de compra para que os clientes não pense que ele vai adquirir um aplicativo que funcionará no seu PC como um aplicativo de desktop tradicional.

Se seu aplicativo é executado na área de trabalho, como um aplicativo tradicional do PC, mas oferece uma experiência VR quando estiver conectado a um fone de ouvido imersivo (se o conteúdo completo do seu aplicativo está disponível, ou apenas uma parte), marque a caixa de seleção "hardware recomendado" ao lado de "Windows Mixed Reality headset imersivo." Nenhum aviso será mostrado acima do botão de compra na página de detalhes do produto do seu aplicativo se suas funções de aplicativo como um aplicativo de desktop tradicional sem um fone de ouvido imersivo conectado.

**Especificações de PC:**

Se você quiser que seu aplicativo para alcançar tantos usuários imersivo headset de realidade mista do Windows quanto possível, você vai querer [alvo](understanding-performance-for-mixed-reality.md) as especificações de PC para [PCs de realidade mista do Windows com gráficos integrados](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Se seu aplicativo de realidade misturada tem como alvo os requisitos mínimos do PC de realidade mista do Windows, ou exige uma configuração específica do PC (como a GPU dedicada de um [PC do Windows Mixed Reality Ultra](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), você deve indicar que com os principais Especificações de PC na coluna "mínimos de hardware".

Se seu aplicativo de realidade misturada foi projetado para funcionar melhor ou oferecer a gráficos de resolução mais alta, em uma configuração de PC específico ou placa de vídeo, você deve indicar que com as especificações de PC relevantes na coluna "hardware recomendado".

Isso se aplica somente se seu aplicativo de realidade misturada usa uma imersão headset conectado a um PC. Se seu aplicativo de realidade misturada só é executado no HoloLens, você não precisará indicar as especificações de PC como HoloLens tem apenas uma configuração de hardware.

### <a name="device-family-availability"></a>Disponibilidade da família de dispositivos

Se você já [seu aplicativo for empacotado corretamente](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) no Visual Studio, carregá-lo na página de pacotes do processo de envio de aplicativo deve produzir uma tabela que identifica quais famílias de dispositivo estará disponível para ser seu aplicativo.

![Tabela de disponibilidade de família do dispositivo](images/device-family-table-900px.png)<br>
Tabela de disponibilidade de família do dispositivo

Se seu aplicativo de realidade misturada funciona em fones imersivos em exposição, em seguida, no mínimo "Windows 10 Desktop" deve ser selecionado na tabela. Se seu aplicativo de realidade misturada funciona em HoloLens, em seguida, no mínimo "Windows 10 Holographic" deve ser selecionado. Se seu aplicativo for executado em ambos os tipos de headset de realidade mista do Windows, como o [Academy de realidade mista "Ilha de projeto" aplicativo](mixed-reality-250.md), "Windows 10 Desktop" e "Windows 10 Holographic" devem ser selecionada.

>[!TIP]
>Muitos desenvolvedores encontram erros ao carregar seu pacote de app relacionado a incompatibilidades entre o manifesto do pacote e suas informações de conta de Editor do aplicativo no Partner Center. Esses erros geralmente podem ser evitados com entrando no Visual Studio com a mesma conta associada com sua conta de desenvolvedor do Windows (aquela que você usa para entrar no Partner Center). Se você usar a mesma conta, você poderá associar seu aplicativo com sua identidade da Microsoft Store antes de compactá-la.

![Associar o aplicativo com a Microsoft Store](images/associate-your-app-700px.png)<br>
Associar o aplicativo com a Microsoft Store no Visual Studio

### <a name="store-listing-page"></a>Página de listagem da Store

Sobre o [listagem Store](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) processar a página de envio de aplicativo, existem diversos lugares, você pode adicionar informações úteis sobre o seu aplicativo de realidade misturada.

>[!IMPORTANT]
>Para garantir que seu aplicativo corretamente categorizado pelo Store e tornam detectável para os clientes do Windows Mixed Reality, você deve adicionar **"Windows Mixed Reality"** como um dos seus "termos de pesquisa" o aplicativo (você pode encontrar os termos de pesquisa, expandindo "Shared campos" seção).

![Adicionar o Windows Mixed Reality para termos de pesquisa](images/search-terms-800px.png)<br>
Adicionar "Windows Mixed Reality" para os termos de pesquisa

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Oferecendo uma avaliação gratuita para o seu jogo ou aplicativo

Muitos consumidores terá limitadas nenhuma experiência com a realidade virtual antes de comprar um fone de ouvido Windows Mixed Reality envolvente. Eles talvez não saiba o que esperar de jogos intenso e talvez não esteja familiarizados com seu próprio limite de conforto em experiências imersivas. Muitos clientes também podem tentar um fone de ouvido imersivo realidade mista do Windows em computadores que não estão com selo como [PCs de realidade mista do Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines). Devido a essas considerações, é altamente recomendável você considerar a oferta de uma [avaliação gratuita](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) para seu aplicativo de realidade misturada paga ou de um jogo.

## <a name="see-also"></a>Consulte também
* [Realidade misturada](mixed-reality.md)
* [Visão geral de desenvolvimento](development-overview.md)
* [Modos de exibição do aplicativo](app-views.md)
* [Noções básicas sobre desempenho para realidade misturada](understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
* [Testar seu aplicativo no HoloLens](testing-your-app-on-hololens.md)
* [Diretrizes de compatibilidade de hardware do Windows Mixed Reality mínimas PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
