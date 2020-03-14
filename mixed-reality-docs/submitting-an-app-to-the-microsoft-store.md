---
title: Enviando um aplicativo para o Microsoft Store
description: Este artigo oferece dicas sobre como enviar seus aplicativos de realidade misturada para o Microsoft Store, incluindo como empacotar e testar seu aplicativo e dicas para passar a certificação e auxiliar na descoberta de seu aplicativo na loja.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: aplicativo, UWP, envio, envio, filtros, metadados, requisitos do sistema, palavras-chave, wack, certificação, pacote, Appx, merchandising
ms.openlocfilehash: f2eb4093a2bea51d8c39b94d23777e426810981e
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375803"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Enviando um aplicativo para o Microsoft Store

Tanto o [HoloLens](hololens-hardware-details.md) quanto o PC com Windows 10 que ligam o [headset de imersão](immersive-headset-hardware-details.md) executam plataforma universal do Windows aplicativos. Se você estiver enviando um aplicativo que dá suporte a HoloLens ou PC (ou ambos), você enviará seu aplicativo para o Microsoft Store por meio do [Partner Center](https://partner.microsoft.com/dashboard).

Se você ainda não tem uma conta de desenvolvedor do Partner Center, você pode [se inscrever hoje](https://developer.microsoft.com/store/register).

## <a name="packaging-a-mixed-reality-app"></a>Empacotando um aplicativo de realidade misturada

### <a name="prepare-image-assets-included-in-the-appx"></a>Preparar os ativos de imagem incluídos no Appx

Há vários ativos de imagem exigidos pelas ferramentas de criação do Appx para criar seu aplicativo em um pacote Appx para enviar à loja. Você pode saber mais sobre as [diretrizes para ativos de bloco e ícone](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) no msdn.

| Ativo necessário | Escala recomendada | Formato de imagem | Onde isso é exibido? | 
|----------|----------|----------|------------------|
| Logotipo quadrado do 71 x 71 | Qualquer |  PNG | {1&gt;N/A&lt;1} | 
| Logotipo quadrado do 150x150 | 150x150 (100% Scale) ou 225x225 (150% Scale) | PNG | Iniciar Pins e todos os aplicativos (se 310 x 310 não for fornecido), sugestões de pesquisa de repositório, página de listagem de repositório, procurar na loja, pesquisa de loja | 
|  Logotipo de largo 310x150 largo |  Qualquer  |  PNG  |  {1&gt;N/A&lt;1} | 
|  Logotipo da Store |  75x75 (escala de 150%)  |  PNG  |  Partner Center, aplicativo de relatório, escrever uma revisão, minha biblioteca | 
|  Splash Screen |  930x450 (escala de 150%)  |  PNG  |  inicializador de aplicativo 2D (Slate) | 

Também há alguns ativos recomendados para os quais o HoloLens pode aproveitar.

| Ativos recomendados | Escala recomendada | Onde isso é exibido? | 
|----------|----------|----------|
|  Logotipo quadrado do 310 x 310 |  310 x 310 (escala de 150%) |  Iniciar Pins e todos os aplicativos | 

### <a name="live-tile-requirements"></a>Requisitos de bloco dinâmico

O menu iniciar no HoloLens usará a maior imagem de bloco quadrado incluído.

Você pode ver que alguns aplicativos publicados pela Microsoft têm um iniciador 3D para seu aplicativo. Os desenvolvedores podem adicionar um inicializador 3D para seu aplicativo usando [estas instruções](implementing-3d-app-launchers.md).

### <a name="specifying-target-and-minimum-version-of-windows"></a>Especificando o destino e a versão mínima do Windows

Se o seu aplicativo de realidade misturada incluir recursos específicos de uma determinada versão do Windows, é importante especificar o destino e as versões mínimas da plataforma para as quais seu aplicativo universal do Windows dará suporte.

**Isso é especialmente verdadeiro para aplicativos direcionados a [headsets de imersão de realidade mista do Windows](immersive-headset-hardware-details.md), que exigem pelo menos a atualização do Windows 10 para criadores de outono (10,0; Crie 16299) para funcionar corretamente.**

Você será solicitado a definir o destino e a versão mínima do Windows ao criar um novo projeto universal do Windows no Visual Studio. Você também pode alterar essa configuração para um projeto existente no menu "projeto" e, em seguida, "< as propriedades de > do seu nome do aplicativo" na parte inferior do menu suspenso.

![definir versões mínimas e de plataforma de destino no Visual Studio 2019](images/visual-studio-min-version-500px.png)<br>
Definir versões mínimas e de plataforma de destino no Visual Studio

### <a name="specifying-target-device-families"></a>Especificando famílias de dispositivos de destino

Os aplicativos de realidade mista do Windows (para os [headsets](immersive-headset-hardware-details.md)de [HoloLens](hololens-hardware-details.md) e de imersão) fazem parte do plataforma universal do Windows, portanto, qualquer pacote de aplicativo com uma [família de dispositivos de destino](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx) "Windows. universal" é capaz de ser executado em computadores com o HoloLens ou Windows 10 com headsets de imersão. Dito isso, se você não especificar uma família de dispositivos de destino em seu manifesto de aplicativo, poderá abrir inadvertidamente seu aplicativo em dispositivos Windows 10 indesejados. Siga as etapas abaixo para especificar a família de dispositivos do Windows 10 pretendida e, em seguida, [Verifique se as famílias de dispositivos corretas estão selecionadas quando você carrega seu pacote de aplicativo no Partner Center para enviar à loja.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

Para definir esse campo no Visual Studio, clique com o botão direito do mouse em Package. appxmanifest e selecione "Exibir código" e, em seguida, localize o campo nome do TargetDeviceFamily. Por padrão, ele pode ser semelhante ao seguinte:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Se seu aplicativo for criado para o **HoloLens**, você poderá garantir que ele seja instalado apenas no hololens especificando uma família de dispositivos de destino "Windows. Holographic". 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Se seu aplicativo exigir a funcionalidade do **HoloLens 2** especificamente, como acompanhamento de olho ou acompanhamento de mão, você poderá garantir que ele seja destinado às versões 18362 ou superiores do Windows, especificando uma família de dispositivos de destino "Windows. Holographic" e MinVersion 10.0.18362.0. 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

Se seu aplicativo for criado para **headsets de imersão de realidade mista do Windows**, você poderá garantir que ele seja instalado apenas em computadores Windows 10 com a atualização dos criadores de outono do Windows 10 (necessário para a realidade mista do Windows), especificando uma família de dispositivos de destino "Windows. desktop" e MinVersion de "10.0.16299.0".

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

Por fim, se o seu aplicativo se destina a executar tanto no **HoloLens quanto em headsets de imersão de realidade mista do Windows**, você pode garantir que o aplicativo seja disponibilizado apenas para essas duas famílias de dispositivos e, simultaneamente, garantir que cada uma tenha como destino a versão mínima correta do Windows, incluindo uma linha para cada família de dispositivos com sua respectiva MinVersion.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Você pode saber mais sobre como direcionar as famílias de dispositivos lendo a [documentação do TARGETDEVICEFAMILY UWP](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>Associar o aplicativo à loja

No menu Projeto na sua solução do Visual Studio, escolha "armazenar > associar o aplicativo com a loja". Se você fizer isso, poderá testar cenários de compra e de notificação em seu aplicativo. Quando você associa seu aplicativo à loja, esses valores são baixados no arquivo de manifesto do aplicativo para o projeto atual em seu computador local:
* Nome de Exibição do Pacote
* {1&gt;Nome do Pacote&lt;1}
* ID do Editor
* {1&gt;Nome de Exibição do Editor&lt;1}
* {1&gt;Version&lt;1}

Se substituir o arquivo de manifesto padrão .appx criando um arquivo .xml personalizado para o manifesto, você não poderá associar seu aplicativo à Loja. Se você tentar associar um arquivo de manifesto personalizado à Loja, uma mensagem de erro será exibida.

### <a name="creating-an-upload-package"></a>Criando um pacote de carregamento

Siga as diretrizes em [empacotamento de aplicativos universais do Windows para Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2).

A etapa final da criação de um pacote de carregamento é validar o pacote usando o [Kit de certificação de aplicativos para Windows](#windows-app-certification-kit).

Se você estiver adicionando um pacote especificamente para o HoloLens a um produto existente que está disponível em outras famílias de dispositivos Windows 10, você também desejará saber [como os números de versão podem afetar quais pacotes são entregues a clientes específicos](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)e [como os pacotes são distribuídos para diferentes sistemas operacionais](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx).

As diretrizes gerais são que o pacote de número de versão mais alto aplicável a um dispositivo será aquele distribuído pelo repositório.

Se houver um pacote Windows. universal e um pacote Windows. Holographic e o pacote Windows. universal tiver um número de versão superior, um usuário do HoloLens baixará o número de versão superior do Windows. universal Package em vez do Windows. Holographic agrupa. Há várias soluções para esse problema:
1. Certifique-se de que seus pacotes específicos da plataforma, como o Windows. Holographic, sempre tenham um número de versão mais alto do que seus pacotes independentes de plataforma, como Windows. universal
2. Não empacote aplicativos como Windows. universal se você também tiver pacotes específicos da plataforma. em vez disso, empacote o pacote Windows. universal para as plataformas específicas nas quais você deseja disponibilizá-los

>[!NOTE]
> Para dar suporte ao seu aplicativo tanto no HoloLens (1º gen) quanto no HoloLen 2, você precisará carregar dois pacotes de aplicativos; um que contém x86 para HoloLens (1º gen) e um contendo ARM ou ARM64 para o HoloLens 2. 
> 
> Se você incluir o ARM e o ARM64 em seu pacote, a versão do ARM64 será usada no HoloLens 2. 

>[!NOTE]
> Você pode declarar um único pacote para ser aplicável a várias famílias de dispositivos de destino

3. Crie um único pacote Windows. universal que funcione em todas as plataformas. O suporte para isso não é ótimo no momento para que as soluções acima sejam recomendadas.

## <a name="testing-your-app"></a>Como testar seu aplicativo

### <a name="windows-app-certification-kit"></a>Kit de Certificação de Aplicativos Windows

Quando você cria pacotes de aplicativos para enviar ao Partner Center por meio do Visual Studio, o assistente para criar pacotes de aplicativos solicitará que você execute o kit de certificação de aplicativos do Windows em relação aos pacotes que são criados. Para ter um processo de envio suave na loja, é melhor verificar se os testes do kit de [certificação de aplicativos do Windows](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) são aprovados em seu aplicativo no computador local antes de enviá-los para a loja. A execução do kit de certificação de aplicativos para Windows em um HoloLens remoto não tem suporte no momento.

### <a name="run-on-all-targeted-device-families"></a>Executar em todas as famílias de dispositivos de destino

A plataforma universal do Windows permite que você crie um único aplicativo que é executado em todas as famílias de dispositivos Windows 10. No entanto, ele não garante que os aplicativos universais do Windows funcionarão apenas em todas as famílias de dispositivos. Antes de escolher tornar seu aplicativo disponível no HoloLens ou em qualquer outra família de dispositivos de destino do Windows 10, é importante que você [teste o aplicativo](testing-your-app-on-hololens.md) em cada uma dessas famílias de dispositivos para garantir uma boa experiência.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Enviando seu aplicativo de realidade misturada para a loja

Se você estiver enviando um aplicativo de realidade misturada baseado em um projeto do Unity, consulte este [vídeo](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) primeiro.

Em geral, o envio de um aplicativo de realidade mista do Windows que funciona em headsets de HoloLens e/ou de imersão é como enviar qualquer aplicativo UWP para o Microsoft Store. Depois de [criar seu aplicativo reservando seu nome](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name), você deve seguir a lista de [verificação de envio do UWP](https://docs.microsoft.com/windows/uwp/publish/app-submissions).

Uma das primeiras coisas que você fará é [selecionar uma categoria e uma subcategoria](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) para sua experiência de realidade mista. É importante que você **escolha a categoria mais precisa para seu aplicativo** para que possamos criar mercadorias em seu aplicativo nas categorias de armazenamento corretas e garantir que ele apareça usando consultas de pesquisa relevantes. **A listagem de seu título VR como um jogo não resultará em uma melhor exposição para seu aplicativo** e poderá impedi-lo de aparecer em categorias mais ajustadas e menos lotadas.

No entanto, há quatro áreas principais no processo de envio, em que você desejará fazer seleções mistas específicas da realidade:
1. Na seção **[declarações de produto](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** em [Propriedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
2. Na seção **[requisitos do sistema](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** , em [Propriedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
3. Na seção **[disponibilidade da família de dispositivos](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** , em [pacotes](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages).
4. Em vários campos da **[página de listagem de armazenamento](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** .

### <a name="mixed-reality-product-declarations"></a>Declarações de produto da realidade misturada

Na página **[Propriedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** do processo de envio do aplicativo, você encontrará várias opções relacionadas à realidade misturada na seção **[declarações de produto](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** .

![declarações de produto de realidade misturada](images/product-declarations-900px.png)<br>
Declarações de produto da realidade misturada

Primeiro, você desejará identificar os tipos de dispositivo para os quais seu aplicativo oferece uma experiência de realidade mista. Isso garante que seu aplicativo está incluído nas coleções de realidade mista do Windows na loja e que é exibido para os usuários que navegam na loja depois de conectar um headset de imersão (ou ao navegar na loja no HoloLens).

Ao lado de "esta experiência foi projetada para a realidade mista do Windows em:"
* Marque a caixa **PC** somente se seu aplicativo oferecer uma experiência VR quando um headset de imersão estiver conectado ao PC do usuário. Você deve marcar essa caixa se seu aplicativo for projetado exclusivamente para ser executado em um headset de imersão ou se for um jogo/aplicativo padrão de PC que ofereça um modo de realidade misturada e/ou conteúdo de bônus quando um headset estiver conectado.
* Marque a caixa **HoloLens** somente se seu aplicativo oferecer uma experiência Holographic quando for executado no HoloLens.
* Marque **ambas as** caixas se seu aplicativo oferecer uma experiência de realidade misturada em ambos os tipos de dispositivo, como o [aplicativo "ilha de projeto" da Academia de realidade misturada](mixed-reality-250.md) da Build 2017.

Se você selecionou "PC" acima, convém definir a "configuração de realidade mista" (nível de atividade). Isso se aplica somente a experiências de realidade misturadas que são executadas em computadores conectados a headsets de alto-fones de ouvido, pois aplicativos de realidade misturados no HoloLens são de escala mundial e o usuário não define um limite durante a instalação.
* Escolha **encaixado + posicionado** se seu aplicativo for projetado com a intenção de que o usuário permaneça em uma posição (um exemplo seria um jogo no qual você está sentado em uma cabine de uma aeronave).
* Escolha **todas as experiências** se seu aplicativo for projetado com a intenção que o usuário percorra dentro do limite definido durante a instalação (um exemplo pode ser um jogo no qual você faz uma etapa e um pato para ataques de subexposição).

### <a name="mixed-reality-system-requirements"></a>Requisitos de sistema de realidade misturada

Na página **[Propriedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** do processo de envio do aplicativo, você encontrará várias opções relacionadas à realidade misturada na seção **[requisitos do sistema](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** .

![Requisitos do sistema](images/system-reqs-800px.png)<br>
Requisitos de sistema

Nesta seção, você identificará o hardware mínimo (necessário) e o hardware recomendado (opcional) para seu aplicativo de realidade misturada.

**Hardware de entrada:**

Use as caixas de seleção para informar clientes potenciais se seu aplicativo der suporte a **microfone** (para [entrada de voz](voice-input.md)), **[controlador Xbox ou gamepad](hardware-accessories.md#bluetooth-gamepads)** e/ou **[controladores de movimento do Windows Mixed Reality](motion-controllers.md)** . Essas informações serão apresentadas na página de detalhes do produto do aplicativo na loja e ajudarão seu aplicativo a ser incluído nas coleções de jogos/aplicativos apropriadas (por exemplo, uma coleção pode existir para todos os jogos que dão suporte a controladores de movimento).

Tenha em consideração a seleção de caixas de seleção para "hardware mínimo" ou "hardware recomendado" para tipos de entrada. 

Por exemplo: 
* Se o seu jogo exigir controladores de movimento, mas aceitar entrada de voz via microfone, marque a caixa de seleção "hardware mínimo" ao lado de "controladores de movimento de realidade do Windows misto", mas a caixa de seleção "hardware recomendado" ao lado de "microfone". 
* Se o jogo puder ser reproduzido com um controlador Xbox/gamepad ou com controladores de movimento, você poderá marcar a caixa de seleção "hardware mínimo" ao lado de "controlador Xbox ou gamepad" e selecionar a caixa de seleção "hardware recomendado" ao lado de "controladores de movimento da realidade do Windows Mixed", já que os controladores de movimento provavelmente oferecerão um passo em diante no gamepad.

**Headset de imersão do Windows Mixed realm:**

Indicando se um headset de imersão é necessário para usar seu aplicativo, ou é opcional, é essencial para a satisfação e a educação do cliente.

Se seu aplicativo *só* puder ser usado por meio de um headset de imersão, marque a caixa de seleção "mínimo de hardware" ao lado de "headset de imersão do Windows Mixed Realm". Isso será exibido na página de detalhes do produto do aplicativo no repositório como um aviso acima do botão comprar para que os clientes não achem que estão comprando um aplicativo que funcionará em seu PC, como um aplicativo de desktop tradicional.

Se seu aplicativo for executado na área de trabalho como um aplicativo de PC tradicional, mas oferecer uma experiência VR quando um headset de imersão estiver conectado (se o conteúdo completo do seu aplicativo estiver disponível ou apenas uma parte), marque a caixa de seleção "hardware recomendado" ao lado de "realidade mista do Windows Headset de imersão. " Nenhum aviso será exibido acima do botão comprar na página de detalhes do produto do aplicativo se seu aplicativo funcionar como um aplicativo de área de trabalho tradicional sem um headset de imersão conectado.

**Especificações do PC:**

Se você quiser que seu aplicativo alcance o máximo possível de usuários com o fone de ouvido do Windows Mixed Realm, você desejará [direcionar](understanding-performance-for-mixed-reality.md) as especificações do PC para [PCs com o Windows Mixed Reality com gráficos integrados](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Se o seu aplicativo de realidade misturada tem como alvo os requisitos mínimos de PC do Windows Mixed Reality ou requer uma configuração de PC específica (como a GPU dedicada de um [Ultra PC do Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), você deve indicar que, com as especificações relevantes do PC na coluna "hardware mínimo".

Se o seu aplicativo de realidade misturada tiver sido projetado para funcionar melhor ou oferecer gráficos de alta resolução, em uma configuração de PC ou placa gráfica específica, você deverá indicar que, com as especificações relevantes do PC na coluna "hardware recomendado".

Isso só se aplica se o seu aplicativo de realidade misturada usar um headset de imersão conectado a um PC. Se seu aplicativo de realidade misturada só for executado no HoloLens, você não precisará indicar as especificações do PC, pois o HoloLens tem apenas uma configuração de hardware.

### <a name="device-family-availability"></a>Disponibilidade da família de dispositivos

Se você tiver [empacotado seu aplicativo corretamente](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) no Visual Studio, carregá-lo na página pacotes do processo de envio do aplicativo deverá produzir uma tabela identificando a quais famílias de dispositivos seu aplicativo estará disponível.

tabela de disponibilidade da família de dispositivos ![](images/device-family-table-900px.png)<br>
Tabela de disponibilidade da família de dispositivos

Se o seu aplicativo de realidade misturada funcionar em headsets de imersão, pelo menos "Windows 10 desktop" deverá ser selecionado na tabela. Se o seu aplicativo de realidade misturada funcionar no HoloLens, pelo menos "Windows 10 Holographic" deverá ser selecionado. Se seu aplicativo for executado em ambos os tipos de headset do Windows Mixed Reality, como o [aplicativo "ilha de projeto" da reality da Academia](mixed-reality-250.md), "Windows 10 desktop" e "Windows 10 Holographic" devem ser selecionados.

>[!TIP]
>Muitos desenvolvedores se deparam com erros ao carregar o pacote do aplicativo relacionado a incompatibilidades entre o manifesto do pacote e as informações de sua conta de aplicativo/Publicador no Partner Center. Esses erros geralmente podem ser evitados entrando-se no Visual Studio com a mesma conta associada à sua conta de desenvolvedor do Windows (aquela que você usa para entrar no Partner Center). Se você usar a mesma conta, poderá associar seu aplicativo à sua identidade no Microsoft Store antes de empacotá-lo.

![associar seu aplicativo ao Microsoft Store](images/associate-your-app-700px.png)<br>
Associar seu aplicativo ao Microsoft Store no Visual Studio

### <a name="store-listing-page"></a>Página de listagem de armazenamento

Na página de [listagem de armazenamento](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) do processo de envio de aplicativo, há vários lugares em que você pode adicionar informações úteis sobre seu aplicativo de realidade misturada.

>[!IMPORTANT]
>Para garantir que seu aplicativo seja Categorizado corretamente pela loja e tornar-se detectável para os clientes do Windows Mixed Reality, você deve adicionar **"realidade mista do Windows"** como um dos seus "termos de pesquisa" para o aplicativo (você pode encontrar termos de pesquisa expandindo a seção "campos compartilhados").

![adicionar a realidade mista do Windows aos termos de pesquisa](images/search-terms-800px.png)<br>
Adicionar "realidade mista do Windows" aos termos de pesquisa

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Oferecendo uma avaliação gratuita para seu jogo ou aplicativo

Muitos consumidores terão limitado a nenhuma experiência com a realidade virtual antes de comprar um headset de imersão de realidade mista do Windows. Eles podem não saber o que esperar de jogos intensos e podem não estar familiarizados com seu próprio limite de conforto em experiências de imersão. Muitos clientes também podem experimentar um headset de imersão de realidade misturada do Windows em computadores que não são crachás como [PCs com realidade do Windows Mixed](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines). Devido a essas considerações, é altamente recomendável que você considere a possibilidade de oferecer uma [avaliação gratuita](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) para seu aplicativo de realidade mista ou jogo pago.

## <a name="see-also"></a>Consulte também
* [Realidade misturada](mixed-reality.md)
* [Visão geral do desenvolvimento](development.md)
* [Modos de exibição do aplicativo](app-views.md)
* [Entendendo o desempenho da realidade misturada](understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para o Unity](performance-recommendations-for-unity.md)
* [Como testar seu aplicativo no HoloLens](testing-your-app-on-hololens.md)
* [Diretrizes mínimas de compatibilidade de hardware do PC do Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
