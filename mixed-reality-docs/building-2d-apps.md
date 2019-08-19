---
title: Atualizando aplicativos UWP 2D para realidade misturada
description: Este artigo descreve a atualização de seu aplicativo de Plataforma Universal do Windows 2D existente para ser executado em headsets do HoloLens e do Windows Mixed realm de imersão.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: aplicativo 2D, UWP, aplicativo simples, HoloLens, headset de imersão, modelo de aplicativo, botão voltar, barra de aplicativos, DPI, resolução, escala
ms.openlocfilehash: f9792a7e5fd9729bf9f5f632c699c74c58c10ddf
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414217"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>Atualizando aplicativos UWP 2D para realidade misturada

A realidade mista do Windows permite que um usuário veja hologramas como se eles estivessem em seu lugar, em seu mundo físico ou digital. Em seu núcleo, tanto o HoloLens quanto os PCs desktop nos quais você anexa acessórios de headsets de imersão são dispositivos Windows 10; Isso significa que você é capaz de executar quase todos os aplicativos de Plataforma Universal do Windows (UWP) na loja como aplicativos 2D.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>Criando um aplicativo UWP 2D para realidade misturada

A primeira etapa para colocar um aplicativo 2D em headsets de realidade misturada é colocar seu aplicativo em execução como um aplicativo 2D padrão no monitor de sua área de trabalho.

### <a name="building-a-new-2d-uwp-app"></a>Criando um novo aplicativo UWP 2D

Para criar um novo aplicativo 2D para realidade misturada, você simplesmente cria um aplicativo de Plataforma Universal do Windows padrão 2D (UWP). Nenhuma outra alteração de aplicativo é necessária para que esse aplicativo seja executado como um Slate em realidade misturada.

Para começar a criar um aplicativo UWP 2D, confira o artigo [criar seu primeiro aplicativo](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) .

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>Trazendo um aplicativo de armazenamento 2D existente para UWP

Se você já tiver um aplicativo do Windows 2D na loja, primeiro deverá garantir que ele esteja direcionando para o Windows 10 Plataforma Universal do Windows (UWP). Aqui estão todos os pontos iniciais potenciais que você pode ter com seu aplicativo da loja hoje:
<br>

|  Ponto de partida  |  Destino da plataforma de manifesto AppX  |  Como tornar este universal? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Manifesto do aplicativo Silverlight |  [Migrar para o WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone Universal 8,1  |  Manifesto AppX 8,1 que não inclui o destino de plataforma  |  [Migre seu aplicativo para o Plataforma Universal do Windows](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8  |  8 manifesto AppX que não inclui o destino da plataforma  |  [Migre seu aplicativo para o Plataforma Universal do Windows](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8,1 universal  |  Manifesto AppX 8,1 que não inclui o destino de plataforma  |  [Migre seu aplicativo para o Plataforma Universal do Windows](https://msdn.microsoft.com/library/mt148501.aspx) | 

Se você tiver um aplicativo de Unity 2D criado hoje como um aplicativo Win32 (o destino de compilação "PC, Mac & Linux autônomo"), poderá direcionar a realidade mista alternando o Unity para o destino de compilação "Plataforma Universal do Windows".

Falaremos sobre maneiras pelas quais você pode restringir seu aplicativo especificamente para o HoloLens usando a família de dispositivos Windows. Holographic [abaixo](#publish-and-maintain-your-universal-app).

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Executar seu aplicativo 2D em um headset de imersão de realidade mista do Windows

Se você tiver implantado seu aplicativo 2D no computador desktop em que está desenvolvendo e o tentou no monitor, já estará pronto para experimentá-lo em um headset de área de trabalho imersiva!

Basta ir para o menu iniciar dentro do headset de realidade misturada e iniciar o aplicativo a partir daí. O Shell da área de trabalho e o Shell Holographic compartilham o mesmo conjunto de aplicativos UWP e, portanto, o aplicativo já deve estar presente depois que você tiver implantado a partir do Visual Studio.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>Direcionando tanto headsets de imersão quanto HoloLens

Parabéns! Seu aplicativo agora está usando o Windows 10 Plataforma Universal do Windows (UWP).

Seu aplicativo agora é capaz de ser executado em dispositivos do Windows de hoje, como desktop, móvel, Xbox, headsets de imersão de realidade mista do Windows e HoloLens, bem como dispositivos Windows futuros. No entanto, para realmente direcionar todos esses dispositivos, você precisará garantir que seu aplicativo esteja direcionado para a família de dispositivos Windows. universal.

### <a name="change-your-device-family-to-windowsuniversal"></a>Altere a família de dispositivos para Windows. universal

Agora, vamos ir para seu manifesto AppX para garantir que seu aplicativo UWP do Windows 10 possa ser executado no HoloLens:
* Abra o arquivo de solução do aplicativo com o **Visual Studio** e navegue até o manifesto do pacote do aplicativo
* Clique com o botão direito do mouse no arquivo **Package. appxmanifest** em sua solução e vá para **Exibir código**<br>
  ![Package. appxmanifest em Gerenciador de Soluções](images/openappxmanifest-500px.png)<br>
* Verifique se a plataforma de destino é Windows. universal na seção de dependências
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* Guarde!

Se você não usar o Visual Studio para seu ambiente de desenvolvimento, poderá abrir **AppXManifest. xml** no editor de texto de sua escolha para garantir que você esteja direcionando para o **Windows. universal** *TargetDeviceFamily*.

### <a name="run-in-the-hololens-emulator"></a>Executar no emulador do HoloLens

Agora que seu aplicativo UWP tem como alvo "Windows. universal", vamos compilar seu aplicativo e executá-lo no emulador do [HoloLens](using-the-hololens-emulator.md).
* Verifique se você [instalou o emulador do HoloLens](install-the-tools.md).
* No Visual Studio, selecione a configuração de compilação **x86** para seu aplicativo

  ![configuração de build x86 no Visual Studio](images/x86setting.png)<br>
* Selecione **emulador do HoloLens** no menu suspenso destino de implantação

  ![Emulador do HoloLens na lista de destino de implantação](images/deployemulator-500px.png)<br>
* Selecione **depurar > iniciar a depuração** para implantar seu aplicativo e iniciar a depuração.
* O emulador iniciará e executará seu aplicativo.
* Com um teclado, mouse e/ou um controlador Xbox, coloque seu aplicativo no mundo para iniciá-lo.

  ![Emulador do HoloLens carregado com um exemplo de UWP](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>Próximas etapas

Neste ponto, pode acontecer uma de duas coisas:
1. Seu aplicativo mostrará seu Splash e começará a ser executado depois que ele for colocado no emulador! Incrível!
2. Ou depois de ver uma animação de carregamento para um holograma 2D, o carregamento será interrompido e você verá apenas seu aplicativo na tela inicial. Isso significa que algo deu errado e levará mais investigação para entender como dar vida ao seu aplicativo em realidade misturada.

Para chegar à parte inferior do que pode estar fazendo com que seu aplicativo UWP não inicie no HoloLens, você precisará Depurar.

### <a name="running-your-uwp-app-in-the-debugger"></a>Executando seu aplicativo UWP no depurador

Essas etapas o orientarão na depuração do seu aplicativo UWP usando o depurador do Visual Studio.
* Se você ainda não tiver feito isso, abra sua solução no Visual Studio. Altere o destino para o **emulador do HoloLens** e a configuração de Build para **x86**.
* Selecione **depurar > iniciar a depuração** para implantar seu aplicativo e iniciar a depuração.
* Coloque o aplicativo no mundo com o mouse, o teclado ou o controlador Xbox.
* O Visual Studio agora deve quebrar em algum lugar no código do aplicativo.
  - Se seu aplicativo não falhar imediatamente ou entrar no depurador devido a um erro não tratado, passe por uma etapa de teste dos principais recursos do seu aplicativo para verificar se tudo está funcionando e funcional. Você pode ver erros como mostrado abaixo (exceções internas que estão sendo tratadas). Para garantir que você não perca erros internos que afetem a experiência do seu aplicativo, execute seus testes automatizados e testes de unidade para garantir que tudo se comporta conforme o esperado.

![Emulador do HoloLens carregado com um exemplo de UWP que mostra uma exceção de sistema](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>Atualizar sua interface do usuário

Agora que seu aplicativo UWP está em execução em headsets de imersão e/ou HoloLens como um holograma de 2D, vamos garantir que ele parece lindo. Aqui estão algumas coisas a serem consideradas:
* A realidade mista do Windows executará todos os aplicativos 2D em uma resolução fixa e um DPI equivalente a 853x480 pixels efetivos. Considere se seu design precisa ser refinado nessa escala e examine as diretrizes de design abaixo para melhorar sua experiência em headsets de HoloLens e de imersão.
* A realidade mista do Windows [não dá suporte](app-model.md) a blocos dinâmicos 2D. Se sua funcionalidade principal estiver mostrando informações em um bloco dinâmico, considere mover essas informações de volta para seu aplicativo ou explorar os iniciadores de [aplicativos 3D](3d-app-launcher-design-guidance.md).

### <a name="2d-app-view-resolution-and-scale-factor"></a>resolução de exibição de aplicativo 2D e fator de escala

![Do design responsivo](images/scale-500px.png)

O Windows 10 move todo o Design Visual de pixels de tela reais para **pixels efetivos**. Isso significa que os desenvolvedores projetam suas interfaces de usuário seguindo as diretrizes de interface humana do Windows 10 para pixels efetivos, e o dimensionamento do Windows garante que os pixels efetivos sejam o tamanho certo para usabilidade em dispositivos, resoluções, DPI, etc. Veja essa [excelente leitura no MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) para saber mais, bem como esta [apresentação de Build](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx).

Mesmo com a capacidade exclusiva de posicionar aplicativos em seu mundo em uma variedade de distâncias, as distâncias de exibição do tipo TV são recomendadas para produzir a melhor legibilidade e interação com o olhar/gesto. Por isso, um Slate virtual na página inicial da realidade misturada exibirá sua exibição de UWP plana em:

**1280x720, 150% de DPI** (853x480 de pixels efetivos)

Essa resolução tem várias vantagens:
* Esse layout de pixel efetivo terá sobre a mesma densidade de informações que um Tablet ou uma área de trabalho pequena.
* Ele corresponde ao DPI fixo e aos pixels efetivos para aplicativos UWP em execução no Xbox One, permitindo experiências integradas entre dispositivos.
* Esse tamanho é bom quando dimensionado em nossa variedade de distâncias operacionais para aplicativos do mundo.

### <a name="2d-app-view-interface-design-best-practices"></a>práticas recomendadas de design da interface de exibição de aplicativo 2D

**Coincide**
* Siga as [diretrizes de interface humana do Windows 10 (HIG)](https://dev.windows.com/design) para estilos, tamanhos de fonte e tamanhos de botão. O HoloLens fará o trabalho para garantir que seu aplicativo terá padrões de aplicativo compatíveis, tamanhos de texto legíveis e dimensionamento de destino apropriado.
* Certifique-se de que sua interface do usuário segue as práticas recomendadas para o [design responsivo](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) para ter a melhor resolução de HOLOLEN e DPI exclusivas.
* Use as recomendações de tema de cores "Light" do Windows.

**Não:**
* Altere sua interface do usuário muito drasticamente quando, em realidade misturada, para garantir que os usuários tenham uma experiência familiar para entrar e sair do headset.

### <a name="understand-the-app-model"></a>Entender o modelo de aplicativo

O [modelo de aplicativo](app-model.md) para realidade misturada foi projetado para usar a realidade misturada na casa, onde muitos aplicativos residem juntos. Imagine isso como a realidade misturada equivalente da área de trabalho, em que você executa muitos aplicativos 2D ao mesmo tempo. Isso tem implicações no ciclo de vida do aplicativo, blocos e outros recursos importantes do seu aplicativo.

### <a name="app-bar-and-back-button"></a>Barra de aplicativos e botão voltar

exibições 2D são decoradas com uma barra de aplicativo acima do seu conteúdo. A barra de aplicativos tem dois pontos de personalização específica do aplicativo:

**Título:** exibe o *DisplayName* do bloco associado à instância do aplicativo

**Botão voltar:** gera o evento *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* quando pressionado. A visibilidade do botão voltar é controlada por *[SystemNavigationManager. AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* .

![Interface do usuário da barra de aplicativos na exibição de aplicativo 2D](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*Interface do usuário da barra de aplicativos na exibição de aplicativo 2D*

### <a name="test-your-2d-apps-design"></a>Testar o design de seu aplicativo 2D

É importante testar seu aplicativo para ter certeza de que o texto está legível, os botões são direcionáveis e o aplicativo geral parece correto. Você pode [testar](testing-your-app-on-hololens.md) em um headset de desktop, um HoloLens, um emulador ou um dispositivo de toque com a resolução @150definida como 1280x720%.

## <a name="new-input-possibilities"></a>Novas possibilidades de entrada

O HoloLens usa sensores de profundidade avançada para ver o mundo e ver os usuários. Isso permite gestos avançados de mão, como [flor](gestures.md#bloom) e [toque de ar](gestures.md#air-tap). Os microfones avançados também habilitam [experiências de voz](voice-input.md).

Com os headsets da área de trabalho, os usuários podem usar os controladores de movimento para apontar para os aplicativos e tomar medidas. Eles também podem usar um gamepad, direcionando objetos com seus olhar.

O Windows cuida de toda essa complexidade para aplicativos UWP, traduzindo sua entrada de controlador [olhar](gaze.md), gestos, voz e movimento para [eventos de ponteiro](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) que abstraim o mecanismo de entrada. Por exemplo, um usuário pode ter feito um toque de ar com sua mão ou ter recebido o gatilho SELECT em um controlador de movimento, mas os aplicativos 2D não precisam saber de onde veio a entrada – eles simplesmente veem um Press Touch 2D, como se fosse em uma tela touch.

Aqui estão os conceitos/cenários de alto nível que você deve entender para entrada ao trazer seu aplicativo UWP para o HoloLens:
* O [olhar](gaze.md) se transforma em eventos em foco, o que pode disparar inesperadamente menus, submenus ou outros elementos da interface do usuário para pop-up apenas por nuvens em todo o seu aplicativo.
* Olhar não é tão preciso como entrada do mouse. Use destinos de visita de tamanho adequado para o HoloLens, semelhante a aplicativos móveis amigáveis para toque. Elementos pequenos próximos às bordas do aplicativo são especialmente difíceis de interagir.
* Os usuários devem mudar os modos de entrada para passar da rolagem para a arrastar para o movimento panorâmico de dois dedos. Se seu aplicativo foi projetado para entrada por toque, considere garantir que nenhuma funcionalidade principal seja bloqueada por trás de dois panorâmicas de dedo. Nesse caso, considere ter mecanismos de entrada alternativos como botões que podem iniciar o movimento panorâmico de dois dedos. Por exemplo, o aplicativo Maps pode aplicar zoom com dois panorâmicas de dedo, mas tem um botão de adição, subtração e rotação para simular as mesmas interações de zoom com cliques únicos.

A [entrada de voz](voice-input.md) é uma parte crítica da experiência de realidade misturada. Habilitamos todas as APIs de fala que estão no Windows 10 ligando a Cortana ao usar um headset.

## <a name="publish-and-maintain-your-universal-app"></a>Publicar e manter seu aplicativo universal

Quando seu aplicativo estiver em execução, empacote seu aplicativo para [enviá-lo ao Microsoft Store](submitting-an-app-to-the-microsoft-store.md).

## <a name="see-also"></a>Consulte também
* [Modelo de aplicativo](app-model.md)
* [Foco](gaze.md)
* [Gesture](gestures.md)
* [Controladores de movimentos](motion-controllers.md)
* [Entrada de voz](voice-input.md)
* [Como enviar um aplicativo para a Microsoft Store](submitting-an-app-to-the-microsoft-store.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
