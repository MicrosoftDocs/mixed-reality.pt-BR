---
title: Atualizando aplicativos da UWP 2D para realidade misturada
description: Este artigo descreve como atualizar seu aplicativo 2D de plataforma Universal do Windows existente para ser executado no HoloLens e o Windows Mixed Reality fones imersivos em exposição.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Fazer o headset imersivo 2D app, UWP, aplicativo simples, HoloLens, modelo de aplicativo, botão, barra de aplicativo, dpi, resolução, escala
ms.openlocfilehash: 35a2e7774a79e35893821467f7e9ef8c004efa20
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590009"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>Atualizando aplicativos da UWP 2D para realidade misturada

Realidade mista do Windows permite que um usuário Consulte hologramas como se fossem diretamente nas proximidades, em seu mundo físico ou digital. Em seu núcleo, HoloLens e PCs Desktop você anexar Acessórios de fone de ouvido envolventes para são dispositivos Windows 10; Isso significa que você é capaz de executar quase todos os aplicativos da plataforma Universal do Windows (UWP) na Store como aplicativos 2D.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>Criando um aplicativo UWP 2D para realidade misturada

A primeira etapa para levar um aplicativo 2D para realidade misturada headsets é obter o seu aplicativo em execução como um aplicativo 2D padrão no monitor da área de trabalho.

### <a name="building-a-new-2d-uwp-app"></a>Criando um novo aplicativo UWP 2D

Para criar um novo aplicativo 2D para realidade misturada, você simplesmente cria um aplicativo da plataforma Universal do Windows (UWP) de 2D padrão. Nenhuma outra alteração de aplicativo é necessárias para que o aplicativo, em seguida, executar como um slate em realidade misturada.

Para começar a compilar um aplicativo UWP 2D, confira a [criar seu primeiro aplicativo](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) artigo.

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>Colocar um aplicativo Store 2D existente para a UWP

Se você já tiver um aplicativo Windows 2D na Store, primeiro você deve assegurar está definindo como destino o Windows 10 Universal Windows Platform (UWP). Aqui estão todos os pontos de partida possíveis que você possa ter com seu aplicativo Store hoje mesmo:
<br>

|  Ponto de partida  |  Destino da plataforma de manifesto AppX  |  Como tornar esse Universal? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Manifesto de aplicativo do Silverlight |  [Migrar para o WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8.1 Universal  |  8.1 manifesto AppX que não inclua o destino da plataforma  |  [Migrar seu aplicativo para a plataforma Windows Universal](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8  |  Manifesto AppX 8 que não inclua o destino da plataforma  |  [Migrar seu aplicativo para a plataforma Windows Universal](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Universal do Windows Store 8.1  |  8.1 manifesto AppX que não inclua o destino da plataforma  |  [Migrar seu aplicativo para a plataforma Windows Universal](https://msdn.microsoft.com/library/mt148501.aspx) | 

Se você tiver um aplicativo 2D do Unity hoje é criado como um aplicativo Win32 (o "PC, Mac e Linux Standalone" destino de build), você pode direcionar a realidade misturada, alternando o Unity para o destino de build "Plataforma Universal do Windows" em vez disso.

Falaremos sobre as maneiras que você pode restringir seu aplicativo especificamente para HoloLens usando a família do dispositivo Windows.Holographic [abaixo](#publish-and-maintain-your-universal-app).

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Executar seu aplicativo 2D em um fone de ouvido imersivo realidade mista do Windows

Se você implantou seu aplicativo 2D para a máquina da área de trabalho em que você está desenvolvendo e testada no monitor, você já está pronto para experimentar uma imersão Headset da área de trabalho!

Basta ir ao menu Iniciar dentro o headset de realidade mista e inicie o aplicativo a partir daí. O shell da área de trabalho e o shell holográfico compartilham o mesmo conjunto de aplicativos UWP e, portanto, o aplicativo já deve estar presente assim que tiver implantado a partir do Visual Studio.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>Direcionamento de fones imersivos em exposição e HoloLens

Parabéns! Seu aplicativo agora está usando o Windows 10 Universal Windows Platform (UWP).

Seu aplicativo agora é capaz de executar em dispositivos do Windows hoje, como área de trabalho, móveis, Xbox, Windows Mixed Reality fones imersivos em exposição e HoloLens, futuros, bem como dispositivos do Windows. No entanto, para que, na verdade, todos os dispositivos de destino, você precisará garantir que seu aplicativo for direcionado a família do dispositivo universal.

### <a name="change-your-device-family-to-windowsuniversal"></a>Altere sua família de dispositivo para universal

Agora vamos entrar em seu manifesto AppX para garantir que seu aplicativo de UWP do Windows 10 pode ser executado HoloLens:
* Abra o arquivo de solução do seu aplicativo com **Visual Studio** e navegue até o manifesto do pacote de aplicativo
* Clique com botão direito do **Package. appxmanifest** em sua solução de arquivo e vá para **Exibir código**<br>
  ![Package. appxmanifest no Gerenciador de soluções](images/openappxmanifest-500px.png)<br>
* Verifique se que sua plataforma de destino é universal na seção de dependências
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* Salve!

Se você não usar o Visual Studio para o seu ambiente de desenvolvimento, você pode abrir **Appxmanifest** no editor de texto de sua escolha para garantir que você está direcionando o **universal**  *TargetDeviceFamily*.

### <a name="run-in-the-hololens-emulator"></a>Executar no emulador do HoloLens

Agora que seu aplicativo da UWP direcionado "Universal", vamos criar seu aplicativo e executá-lo na [HoloLens emulador](using-the-hololens-emulator.md).
* Verifique se você tem [instalou o emulador do HoloLens](install-the-tools.md).
* No Visual Studio, selecione o **x86** compilar a configuração do seu aplicativo

  ![x86 compilar a configuração no Visual Studio](images/x86setting.png)<br>
* Selecione **HoloLens emulador** no menu de lista suspensa de destino de implantação

  ![HoloLens emulador na lista de destino de implantação](images/deployemulator-500px.png)<br>
* Selecione **Depurar > Iniciar depuração** para implantar seu aplicativo e iniciar a depuração.
* O emulador iniciará e executar seu aplicativo.
* Com um teclado, mouse e/ou um controlador do Xbox, coloque seu aplicativo do mundo para iniciá-lo.

  ![HoloLens emulador carregado com um exemplo de UWP](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>Próximas etapas

Neste ponto, uma das duas coisas pode acontecer:
1. Seu aplicativo mostrará seu logotipo e iniciar a execução depois que ele é colocado no emulador! Incrível!
2. Ou, depois que você vê uma animação de carregamento para um holograma 2D, o carregamento será interrompido e você verá apenas o seu aplicativo na sua tela inicial. Isso significa que algo deu errado e demora mais investigação para compreender como trazer o seu aplicativo para a vida útil em realidade misturada.

Para obter na parte inferior do que está causando seu aplicativo UWP não seja iniciado em HoloLens, você terá que depurar.

### <a name="running-your-uwp-app-in-the-debugger"></a>Executando o aplicativo UWP no depurador

Essas etapas o guiarão através da depuração de seu aplicativo UWP usando o depurador do Visual Studio.
* Se você ainda não fez isso, abra sua solução no Visual Studio. Alterar o destino para o **HoloLens emulador** e a configuração de compilação para **x86**.
* Selecione **Depurar > Iniciar depuração** para implantar seu aplicativo e iniciar a depuração.
* Coloque o aplicativo do mundo com o mouse, teclado ou controlador do Xbox.
* Visual Studio agora deve ser interrompido em algum lugar no código do aplicativo.
  - Se seu aplicativo não imediatamente falhar ou invadir o depurador devido a um erro sem tratamento, em seguida, percorra uma aprovação de teste dos principais recursos do seu aplicativo para verificar se tudo o que está em execução e funcionais. Você poderá ver erros, como a mostrada abaixo (exceções internas que estão sendo tratadas). Para garantir que você não perca erros internos que afetam a experiência do seu aplicativo, execute seus testes automatizados e testes de unidade para verificar se tudo o que se comporta conforme o esperado.

![HoloLens emulador carregado com um exemplo UWP que mostra uma exceção do sistema](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>Atualizar a interface do usuário

Agora que seu aplicativo da UWP está em execução no fones imersivos em exposição e/ou HoloLens como um holograma 2D, em seguida faremos parece bonito. Aqui estão algumas coisas a considerar:
* Windows Mixed Reality executará todos os aplicativos 2D em uma resolução fixa e DPI é igual para 853 x 480 pixels em vigor. Considere se seu design precisa refinamento nessa escala e examine as diretrizes de design abaixo para melhorar sua experiência em HoloLens e fones imersivos em exposição.
* Windows Mixed Reality [não oferece suporte a](app-model.md) blocos dinâmicos 2D. Se sua funcionalidade principal está mostrando informações sobre um bloco dinâmico, considere mover essas informações de volta para seu aplicativo ou explore [iniciadores de aplicativo 3D](3d-app-launcher-design-guidance.md).

### <a name="2d-app-view-resolution-and-scale-factor"></a>Fator de escala e a resolução de exibição 2D app

![Desde o design responsivo](images/scale-500px.png)

Windows 10 move todo o design visual de pixels a tela real serem **pixels efetivos**. Isso significa que, os desenvolvedores criar sua interface do usuário seguindo as diretrizes de Interface humana do Windows 10 para pixels efetivos e dimensionamento do Windows garante que esses pixels relevantes são o tamanho certo para facilitar o uso em vários dispositivos, as resoluções, DPI, etc. Consulte este [ótima leitura no MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) para obter mais informações, bem como isso [compilação apresentação](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx).

Mesmo com a capacidade única de colocar aplicativos em seu mundo em um intervalo de distâncias, semelhante a TV exibindo distâncias são recomendadas para produzir a melhor legibilidade e a interação com olhar/gesto. Por causa disso, um slate virtual da casa de realidade mista exibirá sua exibição simples do UWP em:

**1280 x 720, 150% DPI** (pixels efetivos de 853 x 480)

Essa resolução tem várias vantagens:
* Esse layout de pixel efetivo terá sobre a mesma densidade de informações como um tablet ou área de trabalho pequeno.
* Ele corresponde ao DPI fixo e pixels relevantes para aplicativos UWP em execução no Xbox One, possibilitar experiências perfeitas entre dispositivos.
* Esse tamanho parece bom quando escalados em nosso intervalo de operacionais distâncias para aplicativos do mundo.

### <a name="2d-app-view-interface-design-best-practices"></a>Práticas recomendadas de design do aplicativo 2D exibir interface

**Faça:**
* Siga as [diretrizes de Interface humana do Windows 10 (HIG)](https://dev.windows.com/design) em estilos, tamanhos de fonte e tamanhos de botão. HoloLens fará o trabalho para garantir que seu aplicativo terão padrões de aplicativo compatível, tamanhos de texto legível e dimensionamento de ocorrências de destino apropriado.
* Certifique-se de sua interface do usuário segue as práticas recomendadas para [design responsivo](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) a melhor aparência do HoloLen exclusivas para resolução e DPI.
* Use as recomendações de tema de cores "light" do Windows.

**Não:**
* Altere sua interface do usuário muito drasticamente quando na realidade misturada, para garantir que os usuários tenham uma experiência familiar para dentro e fora o fone de ouvido.

### <a name="understand-the-app-model"></a>Entender o modelo de aplicativo

O [modelo de aplicativo](app-model.md) para realidade misturada foi projetada para usar a base de realidade mista, em que muitos aplicativos residem juntos. Pense nisso como o equivalente de realidade misturada da área de trabalho, em que você executar muitos aplicativos 2D ao mesmo tempo. Isso tem implicações no ciclo de vida do aplicativo, blocos e outros recursos importantes do seu aplicativo.

### <a name="app-bar-and-back-button"></a>Barra de aplicativo e o botão Voltar

Modos de exibição 2D são decorados com uma barra de aplicativo acima de seu conteúdo. A barra de aplicativo tem dois pontos de personalização específicos do aplicativo:

**Título:** exibe as *displayname* do bloco associado com a instância do aplicativo

**Botão Voltar:** gera a *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* eventos quando pressionado. Visibilidade do botão Voltar é controlada pelo  *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)*.

![Aplicativo da barra da interface do usuário no modo de exibição do aplicativo 2D](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*Aplicativo da barra da interface do usuário no modo de exibição do aplicativo 2D*

### <a name="test-your-2d-apps-design"></a>Testar o design do seu aplicativo 2D

É importante testar seu aplicativo para garantir que o texto é legível, os botões são podem ser destinos e o aplicativo geral parece correto. Você pode [testar](testing-your-app-on-hololens.md) em um fone de ouvido da área de trabalho, um HoloLens, um emulador ou um dispositivo de toque com resolução definida como 1280 x 720 @150%.

## <a name="new-input-possibilities"></a>Novas possibilidades de entrada

HoloLens usa sensores de profundidade avançadas para ver o mundo e ver os usuários. Isso permite que os gestos de mão avançadas, como [bloom](gestures.md#bloom) e [polegar](gestures.md#air-tap). Microfones poderosas também permitem [experiências de voz](voice-input.md).

Com fones de ouvido da área de trabalho, os usuários podem usar controladores de movimento para apontar os aplicativos e agir. Eles também podem usar um gamepad, direcionando objetos com sua olhar.

Windows cuida de toda essa complexidade para aplicativos UWP, convertendo sua [olhares](gaze.md), gestos, voz e entrada do controlador para o motion [eventos de ponteiro](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) que abstraem o mecanismo de entrada. Por exemplo, um usuário tenha feito um polegar com sua mão ou extraída selecione o gatilho em um controlador de movimento, mas aplicativos 2D não precisam saber qual a entrada proveniente - apenas veem um toque 2D pressione, como se estivesse em uma tela sensível ao toque.

Aqui estão os conceitos de alto níveis/cenários que você deve compreender para entrada ao levar seu aplicativo UWP para HoloLens:
* [Mantenha o foco](gaze.md) se transforma em eventos de passagem, que podem disparar inesperadamente menus, submenus ou outros elementos de interface do usuário para o pop-up apenas através da observação em torno de seu aplicativo.
* Olhar não é tão preciso quanto a entrada do mouse. Use dimensionado adequadamente os destinos de ocorrências para HoloLens, semelhante a aplicativos móveis de toque amigável. Poucos elementos perto das bordas do aplicativo são especialmente difíceis de interagir com.
* Os usuários devem alternar modos de entrada para ir de rolagem para arrastar a panorâmica de dois dedos. Se seu aplicativo foi projetado para entrada por toque, considere a garantir que nenhuma funcionalidade principal está bloqueada por trás de panorâmica de dois dedos. Nesse caso, considere ter mecanismos alternativos de entrada, como botões que iniciam a panorâmica de dois dedos. Por exemplo, o aplicativo de mapas pode aplicar zoom com dois panorâmica de dedo, mas tem um sinal de adição, subtração e girar o botão para simular as interações de zoom mesmo com cliques únicos.

[Entrada de voz](voice-input.md) é uma parte fundamental da experiência de realidade misturada. Habilitamos todos a APIs que estão no Windows 10, potencializando Cortana ao usar um fone de ouvido de fala.

## <a name="publish-and-maintain-your-universal-app"></a>Publique e mantenha seu aplicativo Universal

Depois que seu aplicativo está em execução, seu aplicativo do pacote [enviá-lo para a Microsoft Store](submitting-an-app-to-the-microsoft-store.md).

## <a name="see-also"></a>Consulte também
* [Modelo de aplicativo](app-model.md)
* [Gaze](gaze.md)
* [Gesto](gestures.md)
* [Controladores de movimento](motion-controllers.md)
* [Voz](voice-input.md)
* [Enviar um aplicativo para a Microsoft Store](submitting-an-app-to-the-microsoft-store.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
