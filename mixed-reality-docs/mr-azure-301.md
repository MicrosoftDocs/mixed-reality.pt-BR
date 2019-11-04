---
title: Sr e Azure 301 – tradução de idioma
description: Conclua este curso para aprender a implementar o API de Tradução de Texto do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, texto do tradutor, hololens, imersão, VR
ms.openlocfilehash: 012eb5522c866e9e0f1caf5e4024305af07e298c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438530"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br>

# <a name="mr-and-azure-301-language-translation"></a>Sr e Azure 301: tradução de idioma

Neste curso, você aprenderá a adicionar recursos de tradução a um aplicativo de realidade misturada usando os serviços cognitivas do Azure, com o API de Tradução de Texto.

![Produto final](images/AzureLabs-Lab1-00.png)

O API de Tradução de Texto é um serviço de tradução que funciona quase em tempo real. O serviço é baseado em nuvem e, usando uma chamada à API REST, um aplicativo pode usar a tecnologia de conversão de máquina neural para traduzir texto para outro idioma. Para obter mais informações, visite a [página de API de tradução de texto do Azure](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).

Após a conclusão deste curso, você terá um aplicativo de realidade misturada que poderá fazer o seguinte:

1.  O usuário vai falar em um microfone conectado a um headset de imersão (VR) (ou o microfone interno do HoloLens).
2.  O aplicativo irá capturar o ditado e enviá-lo para o API de Tradução de Texto do Azure.
3.  O resultado da tradução será exibido em um grupo de interface do usuário simples na cena do Unity.

Este curso ensinará como obter os resultados do serviço do tradutor em um aplicativo de exemplo baseado em Unity. Será necessário aplicar esses conceitos a um aplicativo personalizado que você possa estar criando.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Sr e Azure 301: tradução de idioma</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Embora este curso se concentre principalmente em fones de ouvido (VR) de realidade mista do Windows, você também pode aplicar o que aprende neste curso ao Microsoft HoloLens. Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte ao HoloLens. Ao usar o HoloLens, você pode notar um eco durante a captura de voz.

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018). Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)
- [Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md#installation-checklist)
- [O SDK do Windows 10 mais recente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado
- Um conjunto de fones de ouvido com um microfone interno (se o headset não tiver um MIC interno e alto-falantes)
- Acesso à Internet para a instalação do Azure e recuperação de tradução

## <a name="before-you-start"></a>Antes de começar

- Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).
- O código neste tutorial permitirá que você registre a partir do dispositivo de microfone padrão conectado ao seu PC. Verifique se o dispositivo de microfone padrão está definido para o dispositivo que você planeja usar para capturar sua voz.
- Para permitir que seu computador habilite o ditado, vá para **configurações > privacidade > fala, digitando a tinta & digitar** e selecione o botão **ativar os serviços de fala e digitar sugestões**.
- Se você estiver usando um microfone e fones de ouvido conectados ao (ou integrados ao) seu headset, certifique-se de que a opção "quando eu usar meu Headset, mude para microfone MIC" esteja ativada em **configurações > realidade misturada > áudio e fala**.

   ![Configurações de realidade misturada](images/AzureLabs-Lab1-00-5.png)

   ![Configuração do microfone](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Lembre-se de que, se você estiver desenvolvendo um headset de imersão para este laboratório, poderá enfrentar problemas de dispositivo de saída de áudio. Isso ocorre devido a um problema com o Unity, que é corrigido em versões posteriores do Unity (Unity 2018,2). O problema impede que o Unity altere o dispositivo de saída de áudio padrão em tempo de execução. Como solução alternativa, verifique se você concluiu as etapas acima e feche e reabra o editor, quando esse problema apresenta.

## <a name="chapter-1--the-azure-portal"></a>Capítulo 1 – o portal do Azure

Para usar a API do Azure Translator, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.

1.  Faça logon no [portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  Depois de fazer logon, clique em **novo** no canto superior esquerdo e pesquise por "API de tradução de texto". Selecione **Enter**.

    ![Novo recurso](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.

3.  A nova página fornecerá uma descrição do serviço *API de tradução de texto* . Na parte inferior esquerda desta página, selecione o botão **criar** para criar uma associação com esse serviço.

    ![Criar API de Tradução de Texto serviço](images/AzureLabs-Lab1-03.png)

4.  Depois de clicar em **criar**:

    1. Insira o **nome** desejado para esta instância de serviço.
    2. Selecione uma **assinatura**apropriada.
    3. Selecione o **tipo de preço** apropriado para você, se esta for a primeira vez que criar um *serviço de tradução de texto*, uma camada gratuita (chamada F0) deverá estar disponível para você.
    4. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).

        > Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.
    6. Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.
    7. Selecione **Criar**.

        ![Selecione o botão criar.](images/AzureLabs-Lab1-04.png)

5.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.
6.  Uma notificação será exibida no portal assim que a instância do serviço for criada. 

    ![Notificação de criação de serviço do Azure](images/AzureLabs-Lab1-05.png)

7.  Clique na notificação para explorar sua nova instância de serviço. 

    ![Vá para o pop-up de recursos.](images/AzureLabs-Lab1-06.png)

8.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. Você será levado para sua nova instância do serviço API de Tradução de Texto. 

    ![API de Tradução de Texto página de serviço](images/AzureLabs-Lab1-07.png)

9.  Neste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, o que é feito por meio do uso da chave de assinatura do serviço. 
10. Na página *início rápido* do serviço de *tradução de texto* , navegue até a primeira etapa, *pegue as chaves*e clique em **chaves** (você também pode fazer isso clicando nas teclas de hiperlink azul, localizadas no menu de navegação serviços, indicado pelo ícone de chave). Isso revelará suas *chaves*de serviço.
11. Faça uma cópia de uma das chaves exibidas, pois você precisará dela posteriormente em seu projeto. 

## <a name="chapter-2--set-up-the-unity-project"></a>Capítulo 2 – configurar o projeto do Unity

Configure e teste seu headset de imersão de realidade misturada.

> [!NOTE]
> Você não precisará de controladores de animação para este curso. Se você precisar de suporte para configurar um headset de imersão, [siga estas etapas](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos:

1.  Abra o *Unity* e clique em **novo**. 

    ![Inicie o novo projeto do Unity.](images/AzureLabs-Lab1-08.png)

2.  Agora, você precisará fornecer um nome de projeto de Unity. Insira **MR_Translation**. Verifique se o tipo de projeto está definido como **3D**. Defina o *local* como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab1-09.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar preferências de >** e, em seguida, na nova janela, navegue até **Ferramentas externas**. Altere o **Editor de script externo** para o **Visual Studio 2017**. Feche a janela **preferências** .

    ![Atualize a preferência do editor de script.](images/AzureLabs-Lab1-10.png)

4.  Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma para **plataforma universal do Windows**clicando no botão **alternar plataforma** .

    ![Janela de configurações de compilação, alterne a plataforma para UWP.](images/AzureLabs-Lab1-11.png)

5.  Vá para **arquivo > configurações de compilação** e verifique se:

    1. O **dispositivo de destino** está definido como **qualquer dispositivo**.

        > Para o Microsoft HoloLens, defina o **dispositivo de destino** para o *hololens*.

    2. O **tipo de compilação** está definido como **D3D**
    3. O **SDK** está definido para o **mais recente instalado**
    4. A **versão do Visual Studio** está definida para o **mais recente instalado**
    5. **Compilar e executar** é definido como **computador local**
    6. Salve a cena e adicione-a à compilação.

        1. Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.

            ![Clique no botão Adicionar cenas abertas](images/AzureLabs-Lab1-12.png)

        2. Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![Criar nova pasta de scripts](images/AzureLabs-Lab1-13.png)

        3. Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo*:, digite **MR_TranslationScene**e pressione **salvar**.

            ![Dê um nome à nova cena.](images/AzureLabs-Lab1-14.png)

            > Lembre-se de que você deve salvar as cenas do Unity na pasta *ativos* , pois elas devem ser associadas ao projeto do Unity. Criar a pasta de cenas (e outras pastas semelhantes) é uma maneira típica de estruturar um projeto do Unity.

    7. As configurações restantes, em *configurações de compilação*, devem ser deixadas como padrão por enquanto.

6. Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado. 

    ![Abra as configurações do Player.](images/AzureLabs-Lab1-15.png)

7. Nesse painel, algumas configurações precisam ser verificadas:

    1. Na guia **outras configurações** :

        1. A **versão de tempo de execução de script** deve ser **estável** (.net 3,5 equivalente).
        2. O **back-end de script** deve ser **.net**
        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**

            ![Atualize outras configurações.](images/AzureLabs-Lab1-16.png)
      
    2. Na guia **configurações de publicação** , em **recursos**, marque:

        1. **InternetClient**
        2. **Phone**

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab1-17.png)

    3. Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o **SDK do Windows Mixed Reality** foi adicionado.

        ![Atualize as configurações de X R.](images/AzureLabs-Lab1-18.png)

8.  De volta **às configurações de compilação**, os *projetos de C# Unity* não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste. 
9.  Feche a janela configurações de compilação.
10. Salve sua cena e projeto (**arquivo > salvar cena/arquivo > salvar projeto**).

## <a name="chapter-3--main-camera-setup"></a>Capítulo 3 – configuração principal da câmera

> [!IMPORTANT]
> Se você quiser ignorar o componente *de configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para [baixar esse. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), importe-o para seu projeto como um [*pacote personalizado*](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue no [capítulo 5](#chapter-5--create-the-results-class). Você ainda precisará criar um projeto do Unity.

1.  No *painel hierarquia*, você encontrará um objeto chamado **câmera principal**, esse objeto representa o ponto de vista de "cabeçalho" quando você estiver "dentro" de seu aplicativo.
2.  Com o painel do Unity na frente de você, selecione a **câmera principal gameobject**. Você observará que o *painel Inspetor* (geralmente localizado à direita, dentro do painel) mostrará os vários componentes desse *gameobject*, com a *transformação* na parte superior, seguida pela *câmera*e alguns outros componentes. Você precisará redefinir a transformação da câmera principal, para que ela seja posicionada corretamente.
3.  Para fazer isso, selecione o ícone de **engrenagem** ao lado do componente *transformação* da câmera e selecione **Redefinir**. 

    ![Redefina a transformação principal da câmera.](images/AzureLabs-Lab1-19.png)
 
4.  O componente de *transformação* deve ter a seguinte aparência:

    1. A *posição* é definida como **0, 0,** 0
    2. A *rotação* está definida como **0, 0, 0**
    3. E *Scale* é definido como **1, 1, 1**

        ![Transformar informações da câmera](images/AzureLabs-Lab1-20.png)

5.  Em seguida, com o objeto **principal da câmera** selecionado, consulte o botão **Adicionar componente** localizado na parte inferior do *painel Inspetor*. 
6.  Selecione esse botão e pesquise (digitando fonte de *áudio* no campo de pesquisa ou navegando nas seções) para o componente chamado **fonte de áudio** , conforme mostrado abaixo, e selecione-o (pressionar Enter em também funciona).
7.  Um componente de *fonte de áudio* será adicionado à **câmera principal**, conforme demonstrado abaixo.

    ![Adicione um componente de fonte de áudio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Para o Microsoft HoloLens, você também precisará alterar o seguinte, que fazem parte do componente da **câmera** em sua **câmera principal**:
    > - **Limpar sinalizadores:** Cor sólida.
    > - **Plano de fundo** ' Black, Alpha 0 ' – cor hexadecimal: #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>Capítulo 4 – tela de depuração da instalação

Para mostrar a entrada e a saída da tradução, é necessário criar uma interface do usuário básica. Para este curso, você criará um objeto de interface do usuário de tela, com vários objetos ' Text ' para mostrar os dados.

1.  Clique com o botão direito do mouse em uma área vazia do *painel hierarquia*, em **interface do usuário**, adicionar uma **tela**.

    ![Adicionar novo objeto de interface do usuário da tela.](images/AzureLabs-Lab1-22.png)

2.  Com o objeto Canvas selecionado, no *painel Inspetor* (dentro do componente ' Canvas '), altere o **modo de processamento** para **espaço mundial**. 
3.  Em seguida, altere os seguintes parâmetros na *transformação Rect do painel Inspetor*:

    1. *POS* -  **X** 0 **Y** 0 **Z** 40
    2. *Largura* -500
    3. *Altura* -300
    4. *Escala* - **X** 0,13 **Y** 0,13 **Z** 0,13

        ![Atualize a transformação Rect para a tela.](images/AzureLabs-Lab1-23.png)
 
4.  Clique com o botão direito do mouse na **tela** no *painel hierarquia*, em **interface do usuário**e adicione um **painel**. Esse **painel** fornecerá uma tela de fundo para o texto que será exibido na cena.
5.  Clique com o botão direito do mouse no **painel** no *painel hierarquia*, em **interface do usuário**e adicione um **objeto de texto**. Repita o mesmo processo até que você tenha criado quatro objetos de texto da interface do usuário no total (dica: se você tiver o primeiro objeto ' texto ' selecionado, poderá simplesmente pressionar **' CTRL ' + ' d'** para duplicá-lo, até que você tenha quatro no total). 
6.  Para cada **objeto de texto**, selecione-o e use as tabelas abaixo para definir os parâmetros no *painel Inspetor*.

    1. Para o componente de *transformação Rect* :

        | Nome                   | Transformação- *posição*             | Largura      | Tamanho    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Para o componente de **texto (script)** :


        | Nome                   | Texto               | Tamanho da fonte    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | Status do microfone: | 20           |
        | AzureResponseLabel     | Resposta da Web do Azure | 20           |
        | DictationLabel         |   Você acabou de dizer:   | 20           |
        | TranslationResultLabel |    Transferência    | 20           |

        ![Insira os valores correspondentes para os rótulos de interface do usuário.](images/AzureLabs-Lab1-24.png)

    3. Além disso, torne o estilo da fonte em **negrito**. Isso fará com que o texto seja mais fácil de ler.

        ![Fonte em negrito.](images/AzureLabs-Lab1-25.png)

7.  Para cada *objeto de texto da interface do usuário* criado no [capítulo 5](#chapter-5--create-the-results-class), crie um novo **objeto de texto da interface do usuário** *filho* . Esses filhos exibirão a saída do aplicativo. Crie objetos *filho* clicando com o botão direito do mouse no pai pretendido (por exemplo, *MicrophoneStatusLabel*) e selecione **interface do usuário** e, em seguida, selecione **texto**.
8.  Para cada um desses filhos, selecione-o e use as tabelas abaixo para definir os parâmetros no painel inspetor.

    1. Para o componente de **transformação Rect** :

        | Nome                  | Transformação- *posição* | Largura      | Tamanho    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y-30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y-30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y-30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y-30 Z 0          | 300        | 30        |

    2. Para o componente de **texto (script)** :

        | Nome                  | Texto          | Tamanho da fonte    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. Em seguida, selecione a opção de alinhamento ' centro ' para cada componente de texto:

    ![alinhar texto.](images/AzureLabs-Lab1-26.png)

10. Para garantir que os objetos de **texto da interface do usuário filho** sejam facilmente legíveis, altere sua *cor*. Para fazer isso, clique na barra (atualmente, ' preto ') ao lado de *cor*. 

    ![Insira valores correspondentes para as saídas de texto da interface do usuário.](images/AzureLabs-Lab1-27.png)
 
11. Em seguida, na janela nova, pequena, *cor* , altere a *cor hexadecimal* para: **0032EAFF**

    ![Atualizar cor para azul.](images/AzureLabs-Lab1-28.png)
 
12. Veja abaixo a aparência da **interface do usuário** .
    1.  No *painel hierarquia*:

        ![Ter hierarquia na estrutura fornecida.](images/AzureLabs-Lab1-29.png)

    2.  Nas *exibições*de *cena* e de jogo:

        ![Ter as exibições de cena e jogo na mesma estrutura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Capítulo 5 – criar a classe Results

O primeiro script que você precisa criar é a classe *Results* , que é responsável por fornecer uma maneira de ver os resultados da tradução. A classe armazena e exibe o seguinte: 

- O resultado da resposta do Azure.
- O status do microfone. 
- O resultado do ditado (voz para texto).
- O resultado da tradução.

Para criar esta classe: 

1.  Clique com o botão direito do mouse no *painel Projeto*e **crie > pasta**. Nomeie a pasta **scripts**. 
 
    ![Criar pasta de scripts.](images/AzureLabs-Lab1-31.png)

    ![Abra a pasta scripts.](images/AzureLabs-Lab1-32.png)
 
2.  Com a pasta **scripts** Create, clique duas vezes nela para abrir. Em seguida, dentro dessa pasta, clique com o botão direito do mouse **C#** e selecione **criar >** , em seguida, script. Nomeie os *resultados*do script. 

    ![Crie o primeiro script.](images/AzureLabs-Lab1-33.png)
 
3.  Clique duas vezes no script novos *resultados* para abri-lo com o **Visual Studio**.
4.  Insira os seguintes namespaces:

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  Dentro da classe, insira as seguintes variáveis:

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  Em seguida, adicione o método *ativo ()* , que será chamado quando a classe for inicializada. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Por fim, adicione os métodos que são responsáveis pela saída de várias informações de resultados para a interface do usuário. 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-6--create-the-microphonemanager-class"></a>Capítulo 6 – criar a classe *microphonemanager*

A segunda classe que você pretende criar é o *microphonemanager*.

Essa classe é responsável por:

- Detectando o dispositivo de gravação conectado ao headset ou ao computador (o que for o padrão).
- Capture o áudio (voz) e use o ditado para armazená-lo como uma cadeia de caracteres.
- Depois que a voz for pausada, envie o ditado para a classe tradutor.
- Hospede um método que pode parar a captura de voz, se desejado.

Para criar esta classe: 
1.  Clique duas vezes na pasta **scripts** para abri-la. 
2.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > C# script**. Nomeie o script *microphonemanager*. 
3.  Clique duas vezes no novo script para abri-lo com o Visual Studio.
4.  Atualize os namespaces para ser o mesmo que o seguinte, na parte superior da classe *microphonemanager* :

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro da classe *microphonemanager* :

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  Agora, o código para os métodos *ativo ()* e *Iniciar ()* precisa ser adicionado. Eles serão chamados quando a classe for inicializada:

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  Você pode *excluir* o método *Update ()* , pois essa classe não o usará.
8.  Agora você precisa dos métodos que o aplicativo usa para iniciar e parar a captura de voz e passá-la para a classe *Tradutor* , que será criada em breve. Copie o código a seguir e cole-o abaixo do método *Start ()* .

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > Embora esse aplicativo não faça uso, o método *StopCapturingAudio ()* também foi fornecido aqui, caso você queira implementar a capacidade de interromper a captura de áudio em seu aplicativo.

9.  Agora você precisa adicionar um manipulador de ditado que será invocado quando a voz parar. Esse método passará o texto ditado para a classe do *Tradutor* .

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. Certifique-se de salvar suas alterações no Visual Studio antes de retornar ao Unity.

> [!WARNING]  
> Neste ponto, você observará um erro exibido no painel de *console do editor do Unity* ("o nome ' Tradutor ' não existe..."). Isso ocorre porque o código faz referência à classe do *Tradutor* , que será criada no próximo capítulo.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Capítulo 7 – chamada para o serviço do Azure e do Tradutor

O último script que você precisa criar é a classe *Translator* . 

Essa classe é responsável por:

-   Autenticando o aplicativo com o *Azure*, no Exchange para um **token de autenticação**.
-   Use o **token de autenticação** para enviar texto (recebido da classe *microphonemanager* ) a ser traduzido.
-   Receba o resultado traduzido e passe-o para a classe *Results* para ser visualizado na interface do usuário.

Para criar esta classe: 
1.  Vá para a pasta **scripts** que você criou anteriormente. 
2.  Clique com o botão direito do mouse no **painel Projeto**, **crie > C# script**. Chame o *Tradutor*de script.
3.  Clique duas vezes no novo script do *Tradutor* para abri-lo **com o Visual Studio**.
4.  Adicione os seguintes namespaces à parte superior do arquivo:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro da classe *Translator* :

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - Os idiomas inseridos na **Enumeração** Languages são apenas exemplos. Fique à vontade para adicionar mais se desejar; a [API dá suporte a mais de 60 idiomas](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (incluindo Klingon)!
    > - Há uma [página mais interativa que abrange os idiomas disponíveis](https://www.microsoft.com/translator/business/languages/), embora esteja ciente de que a página só parece funcionar quando o idioma do site está definido como ' ' (e o site da Microsoft provavelmente será redirecionado para seu idioma nativo). Você pode alterar o idioma do site na parte inferior da página ou alterando a URL.
    > - O valor de **authorizationKey** , no trecho de código acima, deve ser a **chave** que você recebeu quando assinou o *API de tradução de texto do Azure*. Isso foi abordado no [capítulo 1](#chapter-1--the-azure-portal).

6.  Agora, o código para os métodos *ativo ()* e *Iniciar ()* precisa ser adicionado. 
7.  Nesse caso, o código fará uma chamada para o *Azure* usando a chave de autorização para obter um *token*.

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > O token expirará após 10 minutos. Dependendo do cenário do seu aplicativo, talvez seja necessário fazer a mesma chamada de corrotina várias vezes.

8.  A corrotina para obter o token é a seguinte:

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > Se você editar o nome do método IEnumerator **GetTokenCoroutine ()** , precisará atualizar os valores de cadeia de caracteres de chamada *StartCoroutine* e *StopCoroutine* no código acima. [De](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)acordo com a documentação do Unity, para interromper uma *corrotina*específica, você precisa usar o método de valor da cadeia de caracteres.

9.  Em seguida, adicione a corrotina (com um método de fluxo de "suporte" logo abaixo) para obter a tradução do texto recebido pela classe *microphonemanager* . Esse código cria uma cadeia de caracteres de consulta para enviar ao *API de tradução de texto do Azure*e, em seguida, usa a classe interna do Unity UnityWebRequest para fazer uma chamada "Get" para o ponto de extremidade com a cadeia de caracteres de consulta. Em seguida, o resultado é usado para definir a tradução no seu objeto de resultados. O código a seguir mostra a implementação:

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-8--configure-the-unity-scene"></a>Capítulo 8 – configurar a cena do Unity

1.  De volta ao editor do Unity, clique e arraste a classe *Results* *da* pasta **scripts** para o objeto da **câmera principal** no *painel hierarquia*.
2.  Clique na **câmera principal** e examine o *painel Inspetor*. Você observará que, no componente de *script* recém-adicionado, há quatro campos com valores vazios. Essas são as referências de saída para as propriedades no código. 
3.  Arraste os objetos de **texto** apropriados do *painel hierarquia* para esses quatro slots, conforme mostrado na imagem abaixo.

    ![Atualizar referências de destino com valores especificados.](images/AzureLabs-Lab1-34.png)
  
4.  Em seguida, clique e arraste a classe *Tradutor* da pasta **scripts** para o objeto de **câmera principal** no *painel hierarquia*. 
5.  Em seguida, clique e arraste a classe *microphonemanager* da pasta **scripts** para o objeto de **câmera principal** no *painel hierarquia*. 
6.  Por fim, clique na **câmera principal** e examine o *painel Inspetor*. Você observará que, no script que você arrastou, há duas caixas suspensas que permitirão que você defina os idiomas.
 
    ![Verifique se os idiomas de tradução pretendidos são de entrada.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Capítulo 9 – testar em realidade misturada

Neste ponto, você precisa testar se a cena foi implementada corretamente.

Certifique-se de que:

- Todas as configurações mencionadas no [capítulo 1](#chapter-1--the-azure-portal) estão definidas corretamente. 
- Os *resultados*, o *Tradutor*e o *microfonemanager*, os scripts são anexados ao objeto da **câmera principal** . 
- Você colocou sua **chave** do serviço de *API de tradução de texto do Azure* dentro da variável **AuthorizationKey** dentro do script do *Tradutor* .  
- Todos os campos no *painel principal do Inspetor de câmera* são atribuídos corretamente.
- O microfone está funcionando ao executar sua cena (caso contrário, verifique se o microfone anexado é o dispositivo *padrão* e se você o [configurou corretamente no Windows](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).

Você pode testar o headset de imersão pressionando o botão **reproduzir** no *Editor do Unity*.
O aplicativo deve estar funcionando por meio do headset de imersão anexado.

> [!WARNING]  
> Se você vir um erro no console do Unity sobre a alteração do dispositivo de áudio padrão, a cena poderá não funcionar conforme o esperado. Isso ocorre devido à maneira como o portal de realidade misturada lida com microfones internos para fones de ouvido que os têm. Se você vir esse erro, simplesmente pare a cena e inicie-a novamente e as coisas devem funcionar conforme o esperado.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Capítulo 10 – criar a solução UWP e Sideload no computador local

Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.

1.  Navegue até **configurações de compilação**: **arquivo > configurações de compilação...**
2.  Na janela **configurações de compilação** , clique em **Compilar**.

    ![Compile a cena do Unity.](images/AzureLabs-Lab1-36.png)
  
3.  Se ainda não estiver, **os C# projetos de Unity**de tique.
4.  Clique em **Compilar**. O Unity iniciará uma janela *Explorador de arquivos* , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado. Crie essa pasta agora e nomeie-a como *aplicativo*. Em seguida, com a pasta de *aplicativo* selecionada, pressione **Selecionar pasta**. 
5.  O Unity começará a criar seu projeto na pasta do *aplicativo* . 
6.  Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do *Explorador de arquivos* no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).

## <a name="chapter-11--deploy-your-application"></a>Capítulo 11 – implantar seu aplicativo

Para implantar seu aplicativo:

1.  Navegue até sua nova compilação do Unity (a pasta do *aplicativo* ) e abra o arquivo de solução com o *Visual Studio*.
2.  Na configuração da solução, selecione **depurar**.
3.  Na plataforma da solução, selecione **x86**, **computador local**. 

    > Para o Microsoft HoloLens, você pode achar mais fácil definir isso como *computador remoto*, para que você não esteja vinculado ao seu computador. No entanto, também será necessário fazer o seguinte:
    > - Conheça o **endereço IP** do seu HoloLens, que pode ser encontrado dentro das *configurações > rede & Internet > Wi-Fi > opções avançadas*; o IPv4 é o endereço que você deve usar. 
    > - Verificar se o modo **de** *desenvolvedor* está ativado; encontrado em *configurações > atualização & > de segurança para desenvolvedores*.

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu PC.
5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.
6.  Depois de iniciado, o aplicativo solicitará que você autorize o acesso ao microfone. Certifique-se de clicar no botão **Sim** .
7.  Agora você está pronto para começar a traduzir!

## <a name="your-finished-translation-text-api-application"></a>Seu aplicativo de API de tradução de texto concluído

Parabéns, você criou um aplicativo de realidade misturada que aproveita a API de texto de tradução do Azure para converter a fala em texto traduzido.

![Produto final.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Você pode adicionar a funcionalidade de conversão de texto em fala ao aplicativo para que o texto retornado seja falado?

### <a name="exercise-2"></a>Exercício 2

Possibilitar que o usuário altere os idiomas de origem e saída (' de ' e ' para ') no próprio aplicativo, para que o aplicativo não precise ser recriado sempre que você quiser alterar os idiomas.
