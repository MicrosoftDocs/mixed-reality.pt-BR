---
title: Noções básicas do MR 100 - guia de Introdução com o Unity
description: Saiba como criar seu primeiro aplicativo "hello world" básico de realidade misturada.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: misto realidade, realidade mista do Windows, HoloLens, vr de imersão, mr, começar a usar, holograma, academy, tutorial
ms.openlocfilehash: fd3bed955e80ec18b7be500adbdb0fcb7062d129
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993618"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a>Noções básicas sobre MR 100: Guia de Introdução com o Unity

Este tutorial orientará você pela criação de um aplicativo básico de realidade misturada criado com o Unity.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td>Noções básicas sobre MR 100: Guia de Introdução com o Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

* Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).

## <a name="chapter-1---create-a-new-project"></a>Capítulo 1 - criar um novo projeto

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Para criar um aplicativo com o Unity, você precisa primeiro criar um projeto. Este projeto é organizado em algumas pastas, o mais importante é a sua pasta de ativos. Essa é a pasta que contém todos os ativos que você importa de ferramentas de criação de conteúdo digital, como Maya, Max Cinema 4d ou Photoshop, todo código que você criar com o Visual Studio ou seu editor de código favorito, e qualquer número de arquivos de conteúdo que o Unity cria quanto você redigir cenas , animações e outros tipos de ativos do Unity no editor.

Para compilar e implantar aplicativos UWP, o Unity pode exportar o projeto como uma solução do Visual Studio que irá conter todos os arquivos de código e ativos necessários.

1. Inicie o Unity
2. Selecione **novo**
3. Insira um nome de projeto (por exemplo "MixedRealityIntroduction")
4. Insira um local para salvar o projeto
5. Verifique se o **3D** alternância está selecionada
6. Selecione **criar projeto**

Parabéns, você está toda a configuração para começar com as personalizações de realidade misturada agora.

## <a name="chapter-2---setup-the-camera"></a>Capítulo 2 - a instalação da câmera

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

A câmera principal Unity lida com controle de cabeçalho e renderização estereoscópica. Há algumas alterações para fazer a câmera principal para usá-lo com a realidade misturada.
1. Selecione Arquivo > Nova cena

Primeiro, será mais fácil para dispor o seu aplicativo se você imaginar a posição inicial do usuário como (**X**: 0, **Y**: 0, **Z**: 0). Uma vez que a câmera principal está acompanhando a movimentação do cabeçote do usuário, a posição inicial do usuário pode ser definida, definindo a posição inicial da câmera principal.
1. Selecione **câmera principal** na **hierarquia** painel
2. No **Inspetor** do painel, localize a **transformar** componente e altere a **posição** de (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)

Segundo, o plano de fundo de câmera padrão precisa de um pouco de criatividade.

**Para aplicativos do HoloLens**, o mundo real deve aparecer por trás de tudo o que a câmera renderizar, não uma textura Skybox.
1. Com o **câmera principal** ainda selecionado na **hierarquia** do painel, localize o **câmera** componente no **Inspetor** painel e altere o **Limpar sinalizadores** dropdown do **Skybox** para **cor sólida**.
2. Selecione o **plano de fundo** selecionador de cores e altere o **RGBA** valores (0, 0, 0, 0)

**Para aplicativos de realidade misturada direcionados ao fones imersivos em exposição**, podemos usar a textura Skybox padrão que o Unity fornece.
1. Com o **câmera principal** ainda selecionado na **hierarquia** do painel, localize o **câmera** componente no **Inspetor** painel e manter o **Limpar sinalizadores** dropdown à **Skybox**.

Em terceiro lugar, vamos considerar o plano de recorte próximo no Unity e impedir que os objetos que está sendo renderizada muito próximas aos usuários olhos conforme um usuário se aproxima de um objeto ou um usuário se aproxima de um objeto.

**Para aplicativos do HoloLens**, o plano de recorte próximo pode ser definido como o [HoloLens recomendado](camera-in-unity.md#clip-planes) metros 0.85.
1. Com o **câmera principal** ainda selecionado na **hierarquia** do painel, localize o **câmera** componente no **Inspetor** painel e altere o **Perto do plano de recorte** campo do padrão **0.3** para o HoloLens recomendado **0,85**.

**Para aplicativos de realidade misturada direcionados ao fones imersivos em exposição**, podemos usar a configuração padrão que o Unity fornece.
1. Com o **câmera principal** ainda selecionado na **hierarquia** do painel, localize o **câmera** componente no **Inspetor** painel e manter o **Perto do plano de recorte** campo para o padrão **0.3**.

Por fim, vamos salve nosso progresso até o momento. Para salvar as alterações de cena, selecione **arquivo > Salvar cena como**, nomeie a cena **Main**e selecione **salvar**.

## <a name="chapter-3---setup-the-project-settings"></a>Capítulo 3 - as configurações do projeto de instalação

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

Neste capítulo, definiremos algumas configurações de projeto do Unity que ajude-no SDK do Windows Holographic para o desenvolvimento de destino. Podemos também definir algumas configurações de qualidade para nosso aplicativo. Por fim, verificaremos que nossos destinos de compilação são definidos para a Windows Store.

### <a name="unity-performance-and-quality-settings"></a>Configurações de desempenho e qualidade do Unity

**Configurações de qualidade do Unity para HoloLens**

![Configurações de qualidade do Unity para HoloLens](images/qualitysettings.png) 

Uma vez que é tão importante manter a alta taxa de quadros no HoloLens, queremos que as configurações de qualidade ajustadas para desempenho mais rápido. Para obter mais informações de desempenho [recomendações de desempenho para o Unity](performance-recommendations-for-unity.md).
1. Selecione **Editar > configurações do projeto > qualidade**
2. Selecione o **lista suspensa** sob o **Windows Store** logotipo e selecione **muito baixa**. Você saberá que a configuração seja aplicada corretamente quando a caixa na coluna Windows Store e **muito baixa** linha está verde.

**Para aplicativos de realidade misturada direcionados ao obstruídos exibe**, você pode deixar as configurações de qualidade para seus valores padrão.

### <a name="target-windows-10-sdk"></a>Destino Windows 10 SDK

**SDK do Windows Holographic do destino**

![SDK do Windows Holographic do destino](images/xrsettings.png) 

Precisamos informar Unity que o aplicativo que estamos tentando exportar deve criar uma [exibição imersiva](app-views.md) em vez de uma exibição 2D. Podemos fazer isso habilitando o suporte de realidade Virtual no Unity direcionando o SDK do Windows 10.
1. Vá para **Editar > configurações do projeto > Player**.
2. No **painel Inspetor** para configurações do Player, selecione o **Windows Store** ícone.
3. Expanda o **XR configurações** grupo.
4. No **renderização** seção, verifique os **suporte de realidade Virtual** caixa de seleção para adicionar uma nova **SDKs de realidade Virtual** lista.
5. Verifique **Windows Mixed Reality** aparece na lista. Se não estiver, selecione a **+** botão na parte inferior da lista e escolha **Windows Mixed Reality**.

>[!NOTE]
>Se você não vir as **Windows Store** ícone, verifique novamente para certificar-se de que você selecionou a Windows Store Scripting back-end .NET antes da instalação. Caso contrário, talvez seja necessário reinstalar o Unity com a instalação correta do Windows.

**Verifique se a configuração do .NET**

![Verifique se a configuração do .NET](images/configoptions-375px.png)

1. Vá para **Editar > configurações do projeto > Player** (você ainda poderá ter esse da etapa anterior).
2. No **painel Inspetor** para configurações do Player, selecione o **Windows Store** ícone.
3. No **outras configurações** configuração de seção, certifique-se de que **back-end de script** é definido como **.NET**

Trabalho formidável sobre como obter todas as configurações de projeto aplicadas. Em seguida, vamos adicione um holograma!

## <a name="chapter-4---create-a-cube"></a>Capítulo 4 - criar um cubo

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Criação de um cubo no projeto do Unity é exatamente como a criação de qualquer outro objeto no Unity. Colocar um cubo na frente do usuário é fácil porque o sistema de coordenadas do Unity está mapeado para o mundo real – onde um metro no Unity é aproximadamente um metro no mundo real.
1. No canto superior esquerdo dos **hierarquia** painel, selecione o **Create** lista suspensa e escolha **objeto 3D > cubo**.
2. Selecione o recém-criado **cubo** na **hierarquia** painel
3. No **Inspector** localizar o **transformar** componente e alteração **posição** para (**X**: 0, **Y**: 0, **Z**: 2). *Isso posiciona o cubo 2 metros na frente de posição de inicial do usuário.*
4. No **transformar** componente, alteração **rotação** para (**X**: 45, **Y**: 45, **Z**: 45) e altere **dimensionamento** para (**X**: 0,25, **Y**: 0,25, **Z**: 0.25). *Isso dimensiona o cubo para os medidores de 0,25.*
5. Para salvar as alterações de cena, selecione **arquivo > Salvar cena**.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Capítulo 5 – verificar no dispositivo a partir do editor do Unity

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

Agora que criamos nosso cubo, é hora de fazer uma verificação rápida no dispositivo. Você pode fazer isso diretamente do editor do Unity.

### <a name="initial-setup"></a>Configuração inicial
1. No seu computador, de desenvolvimento no Unity, abra **arquivo > configurações de Build** janela.
2. Alteração **plataforma** à **plataforma Universal do Windows** e clique em **alternar plataforma**

### <a name="for-hololens-use-unity-remoting"></a>Para o HoloLens usar a comunicação remota do Unity
1. Em seu HoloLens, instalar e executar o [holográfica Player de comunicação remota](holographic-remoting-player.md), disponível na Windows Store. Iniciar o aplicativo no dispositivo, e ele entrar em um estado de espera e mostrará o endereço IP do dispositivo. Anote o IP.
2. Abra **Janela > XR > emulação holográfica**.
3. Alteração **modo de emulação** de **None** para **remoto ao dispositivo**.
4. Na **máquina remota**, insira o endereço IP do seu HoloLens observado anteriormente.
5. Clique em **Conectar**.
6. Verifique se o **Status de Conexão** muda para verde **conectado**.
7. Agora você pode clicar em **reproduzir** no editor do Unity.

Agora, você poderá ver o cubo no dispositivo e no editor. Você pode pausar, inspecionar objetos e de depuração exatamente como você está executando um aplicativo no editor, porque esse é basicamente o que está acontecendo, mas com vídeo, áudio e entrada do dispositivo e para trás transmitidos pela rede entre o computador host e o dispositivo.

### <a name="for-other-mixed-reality-supported-headsets"></a>Para outra realidade misturada headsets com suporte

1. Conectar o fone de ouvido ao seu PC de desenvolvimento usando o cabo USB e o HDMI ou exibir o cabo de porta.
2. Inicie o **Portal de realidade misturada** e verifique se você concluiu a experiência de primeira execução.
3. Do Unity, agora você pode pressionar o botão Reproduzir.

Agora, você poderá ver o processamento de cubo seu Headset de realidade mista e no editor.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Capítulo 6 - criar e implantar no dispositivo do Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

Agora estamos prontos para compilar nosso projeto para o Visual Studio e implantar nosso dispositivo de destino.

### <a name="export-to-the-visual-studio-solution"></a>Exportar para a solução do Visual Studio
1.  Abra **arquivo > configurações de Build** janela.
2.  Clique em **cenas abra Adicionar** para adicionar a cena.
3.  Alteração **plataforma** à **plataforma Universal do Windows** e clique em **alternar plataforma**.
4.  Na **Windows Store** Certifique-se de configurações, **SDK** está **10 Universal**.
5.  Dispositivo de destino, deixe **qualquer dispositivo** para obstruídos exibe ou alternar para o **HoloLens**.
6.  **Tipo de compilação de UWP** deve ser **D3D**.
7.  **SDK do UWP** pode ser deixado no **mais recente instalada**.
8.  Verifique **Unity C# projetos** em depuração.
9.  Clique em **Compilar**.
10. No Explorador de arquivos, clique em **nova pasta** e nomeie a pasta **"Aplicativo"**.
11. Com o **App** pasta selecionada, clique no **Selecionar pasta** botão.
12. Quando o Unity é feito criando, será exibida uma janela do Explorador de arquivos do Windows.
13. Abra o **aplicativo** pasta no Explorador de arquivos.
14. Abra a solução do Visual Studio gerada (MixedRealityIntroduction.sln neste exemplo)

### <a name="compile-the-visual-studio-solution"></a>Compile a solução do Visual Studio

Por fim, podemos irá compilar a solução do Visual Studio exportada, implantá-lo e experimentá-lo no dispositivo.
1. Usando a barra de ferramentas superior do Visual Studio, alterar o destino do **Debug** para **Release** e do **ARM** para **X86**.

As instruções são diferentes para a implantação em um dispositivo em comparação com o emulador. Siga as instruções que correspondem à sua configuração.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Implantar em dispositivos de realidade misturada por Wi-Fi
1. Clique na seta ao lado de **computador Local** botão e, em seguida, alterar o destino de implantação para **máquina remota**.
2. Insira o endereço IP do seu dispositivo de realidade mista e altere **modo de autenticação** universal (protocolo não criptografado) para o HoloLens e **Windows** para outros dispositivos.
3. Clique em **Depurar > Iniciar sem depuração**.

**Para o HoloLens**, se esta for a primeira vez que implantar seu dispositivo, você precisará par [usando o Visual Studio](using-visual-studio.md).

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Implante em dispositivos de realidade misturada em USB

Certifique-se de o dispositivo está conectado por meio do cabo USB.
1. **Para o HoloLens**, clique na seta ao lado de **computador Local** botão e, em seguida, alterar o destino de implantação para **dispositivo**.
2. **Para direcionar dispositivos obstruídos anexados ao seu PC**, mantenha a configuração para a máquina Local. Verifique se você tem o **Portal de realidade misturada** em execução.
3. Clique em **Depurar > Iniciar sem depuração**.

### <a name="deploy-to-emulator"></a>Implantar no emulador
1. Clique na seta ao lado de **dispositivo** botão e na lista suspensa Selecionar **emulador HoloLens**.
2. Clique em **Depurar > Iniciar sem depuração**.

### <a name="try-out-your-app"></a>Testar seu aplicativo

Agora que seu aplicativo é implantado, tente mover em todo o cubo e observe que ele permaneça no mundo na sua frente.

## <a name="see-also"></a>Consulte também
* [Visão geral do desenvolvimento do Unity](unity-development-overview.md)
* [Melhores práticas para trabalhar com o Unity e o Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Noções básicas do MR 101](holograms-101.md)
* [Noções básicas do MR 101E](holograms-101e.md)
