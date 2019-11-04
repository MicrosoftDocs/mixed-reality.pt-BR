---
title: Sr-noções básicas 100 – introdução ao Unity
description: Saiba como criar seu primeiro aplicativo "Hello World" básico de realidade misturada.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realidade misturada, realidade do Windows Mixed, HoloLens, imersão, VR, Sr, introdução, holograma, Academia, tutorial
ms.openlocfilehash: 5e9a90af6b80333addbde2a2e11086372483b7c3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434778"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a>Sr noções básicas 100: introdução ao Unity

Este tutorial orientará você na criação de um aplicativo básico de realidade misturada criado com o Unity.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Sr noções básicas 100: introdução ao Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md).

## <a name="chapter-1---create-a-new-project"></a>Capítulo 1-criar um novo projeto

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Para criar um aplicativo com o Unity, primeiro você precisa criar um projeto. Esse projeto é organizado em algumas pastas, o mais importante deles é sua pasta de ativos. Essa é a pasta que contém todos os ativos que você importa das ferramentas de criação de conteúdo digital, como Maya, Max cinema 4D ou Photoshop, todo o código que você cria com o Visual Studio ou seu editor de código favorito e qualquer quantidade de arquivos de conteúdo que o Unity cria conforme as cenas de composição , animações e outros tipos de ativos de Unity no editor.

Para compilar e implantar aplicativos UWP, o Unity pode exportar o projeto como uma solução do Visual Studio que conterá todos os arquivos de ativos e de código necessários.

1. Iniciar o Unity
2. Selecionar **novo**
3. Insira um nome de projeto (por exemplo, "MixedRealityIntroduction")
4. Insira um local para salvar seu projeto
5. Verifique se a alternância **3D** está selecionada
6. Selecione **criar projeto**

Parabéns, você está pronto para começar a usar suas personalizações de realidade misturada agora.

## <a name="chapter-2---setup-the-camera"></a>Capítulo 2 – configurar a câmera

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

A câmera principal do Unity lida com o controle de cabeçalho e a renderização de estereoscópico. Há algumas alterações a serem feitas na câmera principal para usá-la com realidade misturada.

1. Selecionar arquivo > nova cena

Primeiro, será mais fácil definir o layout de seu aplicativo se você imaginar a posição inicial do usuário como (**X**: 0, **Y**: 0, **Z**: 0). Como a câmera principal está acompanhando a movimentação do cabeçalho do usuário, a posição inicial do usuário pode ser definida definindo a posição inicial da câmera principal.

1. Selecione a **câmera principal** no painel **hierarquia**
2. No painel **Inspetor** , localize o componente **transformação** e altere a **posição** de (**x**: 0, **y**: 1, **z**:-10) para (**x**: 0, **y**: 0, **z**: 0)

Em segundo lugar, o plano de fundo da câmera padrão precisa de algum pensamento.

**Para aplicativos de HoloLens**, o mundo real deve aparecer atrás de tudo que a câmera renderiza, não uma textura Skybox.

1. Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e altere a lista suspensa **limpar sinalizadores** de **Skybox** para **cor sólida**.
2. Selecione o seletor de cor do **plano de fundo** e altere os valores de **RGBA** para (0, 0, 0, 0)

**Para aplicativos de realidade misturados direcionados a headsets de imersão**, podemos usar a textura padrão do Skybox que o Unity fornece.

1. Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e mantenha o menu suspenso **limpar sinalizadores** em **Skybox**.

Em terceiro lugar, vamos considerar o próximo clipe no Unity e impedir que os objetos sejam renderizados muito próximos dos olhos dos usuários, uma vez que um usuário se aproxima de um objeto ou um objeto se aproxima de um usuário.

**Para aplicativos do HoloLens**, o próximo clipe pode ser definido como o [hololens recomendado](camera-in-unity.md#clip-planes) 0,85 metros.

1. Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e altere o campo **próximo do plano do clipe** do padrão **0,3** para o HoloLens recomendado **0,85** .

**Para aplicativos de realidade misturados direcionados a headsets de imersão**, podemos usar a configuração padrão que o Unity fornece.

1. Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e mantenha o campo **próximo do plano do clipe** para o padrão **0,3**.

Por fim, vamos salvar nosso progresso até o momento. Para salvar as alterações de cena, selecione **arquivo > salvar cena como**, nomeie a cena **principal**e selecione **salvar**.

## <a name="chapter-3---setup-the-project-settings"></a>Capítulo 3-configurar as configurações do projeto

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

Neste capítulo, definiremos algumas configurações de projeto do Unity que nos ajudam a direcionar o SDK do Windows Holographic para desenvolvimento. Também definiremos algumas configurações de qualidade para nosso aplicativo. Por fim, garantiremos que nossos destinos de compilação estejam definidos como Windows Store.

### <a name="unity-performance-and-quality-settings"></a>Configurações de desempenho e qualidade do Unity

**Configurações de qualidade do Unity para o HoloLens**

![Configurações de qualidade do Unity para o HoloLens](images/qualitysettings.png)

Como a manutenção da alta taxa de quadros no HoloLens é tão importante, queremos que as configurações de qualidade sejam ajustadas para um desempenho mais rápido. Para obter informações de desempenho mais detalhadas, [recomendações de desempenho para o Unity](performance-recommendations-for-unity.md).

1. Selecione **Editar configurações do projeto > > qualidade**
2. Selecione o **menu suspenso** sob o logotipo da **Windows Store** e selecione **muito baixo**. Você saberá que a configuração é aplicada corretamente quando a caixa na coluna da Windows Store e a linha **muito baixa** estiverem verdes.

**Para aplicativos de realidade misturados direcionados a exibições do obstruído**, você pode deixar as configurações de qualidade com seus valores padrão.

### <a name="target-windows-10-sdk"></a>SDK do Windows 10 de destino

**SDK do Windows Holographic de destino**

![SDK do Windows Holographic de destino](images/xrsettings.png)

Precisamos deixar que o Unity saiba que o aplicativo que estamos tentando exportar deve criar uma [exibição imersiva](app-views.md) em vez de uma exibição 2D. Fazemos isso habilitando o suporte de realidade virtual no Unity direcionando o SDK do Windows 10.

1. Vá para **Editar configurações de projeto > > Player**.
2. No **painel Inspetor** para configurações do Player, selecione o ícone **Windows Store** .
3. Expanda o grupo de **configurações XR** .
4. Na seção **renderização** , marque a caixa de seleção **suporte à realidade virtual** para adicionar uma nova lista de **SDKs de realidade virtual** .
5. Verifique se a **realidade mista do Windows** aparece na lista. Caso contrário, selecione o botão **+** na parte inferior da lista e escolha **realidade mista do Windows**.

>[!NOTE]
>Se você não vir o ícone **Windows Store** , verifique se selecionou o back-end de script do .NET da Windows Store antes da instalação. Caso contrário, talvez seja necessário reinstalar o Unity com a instalação correta do Windows.

**Verificar configuração do .NET**

![Verificar configuração do .NET](images/configoptions-375px.png)

1. Vá para **Editar configurações de projeto > > Player** (talvez você ainda tenha isso na etapa anterior).
2. No **painel Inspetor** para configurações do Player, selecione o ícone **Windows Store** .
3. Na seção configuração de **outras configurações** , verifique se o **back-end de script** está definido como **.net**

Trabalho incrível ao obter todas as configurações de projeto aplicadas. Em seguida, vamos adicionar um holograma!

## <a name="chapter-4---create-a-cube"></a>Capítulo 4-criar um cubo

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Criar um cubo em seu projeto de Unity é como criar qualquer outro objeto no Unity. Colocar um cubo na frente do usuário é fácil porque o sistema de coordenadas do Unity é mapeado para o mundo real, em que um medidor no Unity é aproximadamente um medidor no mundo real.

1. No canto superior esquerdo do painel **hierarquia** , selecione a lista suspensa **criar** e escolha o **objeto 3D > cubo**.
2. Selecione o **cubo** recém-criado no painel **hierarquia**
3. No **Inspetor** , localize o componente de **transformação** e altere a **posição** para (**X**: 0, **Y**: 0, **Z**: 2). *Isso posiciona o cubo 2 metros na frente da posição inicial do usuário.*
4. No componente **transformar** , altere a **rotação** para (**x**: 45, **y**: 45, **z**: 45) e altere a **escala** para (**x**: 0,25, **y**: 0,25, **z**: 0,25). *Isso dimensiona o cubo para 0,25 metros.*
5. Para salvar as alterações de cena, selecione **arquivo > salvar cena**.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Capítulo 5 – verificar no dispositivo do editor do Unity

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

Agora que criamos nosso cubo, é hora de fazer um check-in rápido no dispositivo. Você pode fazer isso diretamente de dentro do editor do Unity.

### <a name="initial-setup"></a>Configuração inicial

1. No seu PC de desenvolvimento, no Unity, abra o **arquivo > janela configurações de Build** .
2. Altere a **plataforma** para **plataforma universal do Windows** e clique em **alternar platfrom**

### <a name="for-hololens-use-unity-remoting"></a>Para o HoloLens, use a comunicação remota do Unity

1. No seu HoloLens, instale e execute o [Holographic Remoting Player](holographic-remoting-player.md), disponível na Windows Store. Inicie o aplicativo no dispositivo e ele entrará em um estado de espera e mostrará o endereço IP do dispositivo. Anote o IP.
2. Abra o **Window > XR > emulação Holographic**.
3. Altere o **modo de emulação** de **nenhum** para **remoto para dispositivo**.
4. Em **computador remoto**, insira o endereço IP do seu HoloLens observado anteriormente.
5. Clique em **Conectar**.
6. Verifique se o **status da conexão** é alterado para verde **conectado**.
7. Agora você pode clicar em **reproduzir** no editor do Unity.

Agora, você poderá ver o cubo no dispositivo e no editor. Você pode pausar, inspecionar objetos e depurá-los da mesma forma que está executando um aplicativo no editor, pois isso é basicamente o que está acontecendo, mas com entrada de vídeo, áudio e dispositivo transmitida e horizontal pela rede entre a máquina host e o dispositivo.

### <a name="for-other-mixed-reality-supported-headsets"></a>Para outros fones de ouvido com suporte da realidade misturada

1. Conecte o headset ao seu computador de desenvolvimento usando o cabo USB e o HDMI ou o cabo de porta de vídeo.
2. Inicie o **portal de realidade misturada** e verifique se você concluiu a experiência de primeira execução.
3. No Unity, agora você pode pressionar o botão reproduzir.

Agora, você poderá ver a renderização do cubo em seu headset de realidade misturada e no editor.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Capítulo 6-criar e implantar no dispositivo a partir do Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

Agora estamos prontos para compilar nosso projeto no Visual Studio e implantá-lo em nosso dispositivo de destino.

### <a name="export-to-the-visual-studio-solution"></a>Exportar para a solução do Visual Studio

1.  Abra o **arquivo > janela configurações de Build** .
2.  Clique em **Adicionar abrir cenas** para adicionar a cena.
3.  Altere a **plataforma** para **plataforma universal do Windows** e clique em **alternar plataforma**.
4.  Nas configurações da **Windows Store** , verifique se o **SDK** é **Universal 10**.
5.  Para o dispositivo de destino, deixe para **qualquer dispositivo** para o obstruído exibir ou alternar para o **HoloLens**.
6.  O **tipo de compilação UWP** deve ser **D3D**.
7.  O **SDK do UWP** pode ser deixado no **mais recente instalado**.
8.  Verifique **os C# projetos do Unity** em depuração.
9.  Clique em **Compilar**.
10. No explorador de arquivos, clique em **nova pasta** e nomeie a pasta como **"aplicativo"** .
11. Com a pasta do **aplicativo** selecionada, clique no botão **Selecionar pasta** .
12. Quando o Unity terminar a compilação, uma janela do explorador de arquivos do Windows será exibida.
13. Abra a pasta do **aplicativo** no explorador de arquivos.
14. Abrir a solução do Visual Studio gerada (MixedRealityIntroduction. sln neste exemplo)

### <a name="compile-the-visual-studio-solution"></a>Compilar a solução do Visual Studio

Por fim, compilaremos a solução do Visual Studio exportada, a implantaremos e a experimentaremos no dispositivo.

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de **debug** para **Release** e de **ARM** para **x86**.

As instruções são diferentes para a implantação em um dispositivo versus o emulador. Siga as instruções que correspondem à sua configuração.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Implantar em um dispositivo de realidade mista por Wi-Fi

1. Clique na seta ao lado do botão **computador local** e altere o destino de implantação para **computador remoto**.
2. Insira o endereço IP do dispositivo de realidade misturada e altere o **modo de autenticação** para universal (protocolo não criptografado) para o HoloLens e o **Windows** para outros dispositivos.
3. Clique em **depurar > iniciar sem depuração**.

**Para o HoloLens**, se esta for a primeira vez que você está implantando em seu dispositivo, você precisará emparelhar [usando o Visual Studio](using-visual-studio.md).

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Implantar no dispositivo de realidade mista sobre USB

Verifique se o dispositivo está conectado via cabo USB.

1. **Para o HoloLens**, clique na seta ao lado do botão **computador local** e altere o destino de implantação para **dispositivo**.
2. **Para direcionar dispositivos obstruído conectados ao seu PC**, mantenha a configuração para computador local. Verifique se você tem o **portal de realidade misturada** em execução.
3. Clique em **depurar > iniciar sem depuração**.

### <a name="deploy-to-emulator"></a>Implantar no emulador

1. Clique na seta ao lado do botão **dispositivo** e, na lista suspensa, selecione **emulador do HoloLens**.
2. Clique em **depurar > iniciar sem depuração**.

### <a name="try-out-your-app"></a>Experimente seu aplicativo

Agora que seu aplicativo está implantado, tente mover tudo em todo o cubo e observe que ele permanece no mundo inteiro.

## <a name="see-also"></a>Consulte também

* [Visão geral do desenvolvimento do Unity](unity-development-overview.md)
* [Melhores práticas para trabalhar com o Unity e o Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Informações básicas do Sr 101](holograms-101.md)
* [101E noções básicas do Sr](holograms-101e.md)
