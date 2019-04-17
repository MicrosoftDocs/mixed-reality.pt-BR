---
title: MR e Azure 301 - conversão de linguagem
description: Conclua este curso para saber como implementar a API de texto de tradução do Azure dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, tradução de texto, hololens, imersivo, vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590691"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-and-azure-301-language-translation"></a>MR e o Azure 301: Tradução de idioma

Neste curso, você aprenderá como adicionar funcionalidades de tradução para um aplicativo de realidade misturada usando serviços Cognitivos do Azure, com a API de tradução de texto.

![Final do produto](images/AzureLabs-Lab1-00.png)

A API de tradução de texto é uma serviço que funciona em tempo quase real de conversão. O serviço é baseado em nuvem e, usando uma chamada à API REST, um aplicativo pode fazer uso da tecnologia de tradução automática neural para traduzir o texto em outra linguagem. Para obter mais informações, visite o [página do Azure API de tradução de texto](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).

Após a conclusão deste curso, você terá um aplicativo de realidade mista que serão capaz de fazer o seguinte:

1.  O usuário irá falar em um microfone conectado a um fone de ouvido imersivo (VR) (ou o microfone interno do HoloLens).
2.  O aplicativo irá capturar o ditado e enviá-lo para a API de texto de tradução do Azure.
3.  O resultado da conversão será exibido em um grupo de interface do usuário simple na cena Unity.

Este curso ensinará você a obter os resultados do serviço Translator em um aplicativo de exemplo com base no Unity. Ele será cabe a você aplicar esses conceitos para um aplicativo personalizado que você pode criar.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> MR e o Azure 301: Tradução de idioma</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Enquanto este curso se concentra primariamente em fones de ouvido Windows Mixed Reality de imersão (VR), você também pode aplicar o que você aprenderá neste curso para o Microsoft HoloLens. Como acompanhar o curso, você verá notas quaisquer alterações que talvez seja necessário empregar para dar suporte ao HoloLens. Ao usar o HoloLens, você pode perceber algum eco durante a captura de voz.

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#. Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018). Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .

Recomendamos que o hardware e software para este curso a seguir:

- Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md#installation-checklist)
- [O SDK mais recente do Windows 10](install-the-tools.md#installation-checklist)
- [2017.4 do Unity](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado
- Um conjunto de fones de ouvido com um microfone interno (se o fone de ouvido não tiver um mic internos e alto-falantes)
- Acesso à Internet para a recuperação do Azure de instalação e translation

## <a name="before-you-start"></a>Antes de começar

- Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).
- O código neste tutorial permitirá que você grave do microfone padrão dispositivo conectado ao seu computador. Verifique se que o dispositivo de microfone padrão está definido para o dispositivo que você planeja usar para capturar sua voz.
- Para permitir que seu computador habilitar o ditado, vá para **Configurações > privacidade > fala, escrita à tinta e digitando** e selecione o botão **ativar serviços de fala e sugestões de digitação**.
- Se você estiver usando um microfone e fones de ouvido (ou internos) fone de ouvido, verifique se a opção "Quando eu wear meu fone de ouvido, alternar para o fone de ouvido mic" está ativado no **Configurações > realidade misturada > áudio e fala**.

   ![Configurações de realidade misturada](images/AzureLabs-Lab1-00-5.png)

   ![Configuração do microfone](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Lembre-se de que, se você estiver desenvolvendo para um fone de ouvido envolvente para este laboratório, você poderá enfrentar problemas de dispositivo de saída de áudio. Isso é devido a um problema com o Unity, que é fixo em versões posteriores do Unity (Unity 2018.2). O problema impede que o Unity altere o dispositivo de saída de áudio padrão em tempo de execução. Como uma solução alternativa, verifique se que você concluiu as etapas acima e feche e reabra o Editor, quando esse problema se apresenta.

## <a name="chapter-1--the-azure-portal"></a>Capítulo 1 – Portal do Azure

Para usar a API de tradução do Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo.

1.  Faça logon na [Portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, você precisará criá-lo. Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.

2.  Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure "Tradução de texto API". Selecione **insira**.

    ![Novo recurso](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.

3.  A nova página fornecerá uma descrição do *API de tradução de texto* Service. Na parte inferior esquerda desta página, selecione a **criar** botão para criar uma associação com este serviço.

    ![Criar serviço de API do Translator texto](images/AzureLabs-Lab1-03.png)

4.  Depois de clicar em **criar**:

    1. Inserir sua desejada **nome** para esta instância de serviço.
    2. Selecione uma opção apropriada **assinatura**.
    3. Selecione o **tipo de preço** apropriado para você, se esse for o primeiro tempo para criar um *serviço de tradução de texto*, uma camada gratuita (chamada F0) deve estar disponível para você.
    4. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).

        > Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determinar a **local** para seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local seria o ideal é que na região em que o aplicativo é executado. Alguns ativos do Azure estão disponíveis somente em determinadas regiões.
    6. Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.
    7. Selecione **Criar**.

        ![Selecione o botão Criar.](images/AzureLabs-Lab1-04.png)

5.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.
6.  Uma notificação será exibida no portal depois que a instância do serviço é criada. 

    ![Notificação de criação de serviço do Azure](images/AzureLabs-Lab1-05.png)

7.  Clique na notificação para explorar a nova instância do serviço. 

    ![Vá para a janela pop-up de recurso.](images/AzureLabs-Lab1-06.png)

8.  Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço. Você será levado à instância do serviço de API do Translator texto novo. 

    ![Página de serviço de API de texto do tradutor](images/AzureLabs-Lab1-07.png)

9.  Dentro deste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, que é feito por meio do uso de chave de assinatura do seu serviço. 
10. Dos *início rápido* página do seu *tradução de texto* Service, navegue até a primeira etapa, *pegue suas chaves*e clique em **chaves** (você pode também fazer isso clicando no hiperlink azul chaves, localizado no menu de navegação de serviços, indicado pelo ícone de chave). Isso irá revelar o seu serviço *chaves*.
11. Faça uma cópia de uma das chaves exibidas, pois precisará dele posteriormente em seu projeto. 

## <a name="chapter-2--set-up-the-unity-project"></a>Capítulo 2 – configurar o projeto do Unity

Configurar e testar o headset de realidade misturada envolvente.

> [!NOTE]
> Você não precisará controladores de movimento para este curso. Se você precisar dar suporte a configurar um fone de ouvido imersivo, faça [siga estas etapas](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

A seguir é um conjunto típico backup para o desenvolvimento de realidade mista e, dessa forma, é um bom modelo para outros projetos:

1.  Abra *Unity* e clique em **New**. 

    ![Inicie um novo projeto do Unity.](images/AzureLabs-Lab1-08.png)

2.  Agora, você precisará fornecer um nome de projeto do Unity. Inserir **MR_Translation**. Verifique se o tipo de projeto é definido como **3D**. Defina as *local* para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab1-09.png)

3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Vá para **Editar > Preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

    ![Atualize as preferências do editor de script.](images/AzureLabs-Lab1-10.png)

4.  Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma **plataforma Universal do Windows**, clicando no **alternar plataforma** botão.

    ![Crie janela de configurações, alternar a plataforma para a UWP.](images/AzureLabs-Lab1-11.png)

5.  Vá para **arquivo > configurações de Build** e certifique-se de que:

    1. **Dispositivo de destino** é definido como **qualquer dispositivo**.

        > Para o Microsoft HoloLens, defina **dispositivo de destino** à *HoloLens*.

    2. **Tipo de compilação** é definido como **D3D**
    3. **SDK** é definido como **mais recente instalada**
    4. **Versão do Visual Studio** é definido como **mais recente instalada**
    5. **Compilar e executar** é definido como **Máquina Local**
    6. Salve a cena e adicioná-lo para a compilação.

        1. Fazer isso selecionando **cenas abra Adicionar**. Salvamento janela será exibida.

            ![Clique em Adicionar botão cenas aberto](images/AzureLabs-Lab1-12.png)

        2. Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.

            ![Criar nova pasta de scripts](images/AzureLabs-Lab1-13.png)

        3. Abra seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo*: campo de texto, digite **MR_TranslationScene**, em seguida, pressione **salvar**.

            ![Dê um nome de nova cena.](images/AzureLabs-Lab1-14.png)

            > Esteja ciente de que você deve salvar suas cenas de Unity dentro do *ativos* pasta, pois eles devem estar associados ao projeto do Unity. Criando a pasta de cenas (e outras pastas semelhantes) é uma maneira comum de estruturar um projeto do Unity.

    7. O restante de configurações, em *configurações de Build*, deverá ser deixado como padrão por enquanto.

6. No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado. 

    ![Abra configurações do player.](images/AzureLabs-Lab1-15.png)

7. Neste painel, algumas configurações precisam ser verificados:

    1. No **outras configurações** guia:

        1. **Versão de tempo de execução de scripts** deve ser **estável** (.NET 3.5 equivalente).
        2. **Script de back-end** deve ser **.NET**
        3. **Nível de compatibilidade de API** deve ser **.NET 4.6**

            ![Outras configurações de atualização.](images/AzureLabs-Lab1-16.png)
      
    2. Dentro de **configurações de publicação** guia, em **recursos**, verifique:

        1. **InternetClient**
        2. **Microfone**

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab1-17.png)

    3. Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.

        ![Atualize as configurações de R de X.](images/AzureLabs-Lab1-18.png)

8.  Volta **configurações de Build**, *Unity C# projetos* não fica acinzentado; marque a caixa de seleção ao lado disso. 
9.  Feche a janela de configurações de Build.
10. Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).

## <a name="chapter-3--main-camera-setup"></a>Capítulo 3 – instalação de câmera principal

> [!IMPORTANT]
> Se você quiser ignorar a *configurar o Unity* componente deste curso e continuar diretamente no código, fique à vontade para [baixar esse unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), importá-lo para seu projeto como um [ *Pacote personalizado*](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 5](#chapter-5--create-the-results-class). Você ainda precisará criar um projeto do Unity.

1.  No *painel de hierarquia*, você encontrará um objeto chamado **câmera principal**, este objeto representa o ponto de vista de "head" quando estiver "dentro" de seu aplicativo.
2.  Com o painel do Unity na sua frente, selecione a **GameObject de câmera principal**. Você observará que o *painel Inspetor* (geralmente encontrado para a direita, no painel) mostrará os vários componentes do que *GameObject*, com *transformar* na parte superior, seguido por *câmera*e alguns outros componentes. Você precisará redefinir a transformação da câmera principal, para que ele está posicionado corretamente.
3.  Para fazer isso, selecione a **engrenagem** ícone ao lado da câmera *transformar* componente e selecionando **redefinir**. 

    ![Redefina a transformação de câmera principal.](images/AzureLabs-Lab1-19.png)
 
4.  O *transformar* componente, em seguida, deve se parecer com:

    1. O *posição* é definido como **0, 0, 0**
    2. *Rotação* é definido como **0, 0, 0**
    3. E *dimensionamento* é definido como **1, 1, 1**

        ![Transformar informações de câmera](images/AzureLabs-Lab1-20.png)

5.  Em seguida, com o **câmera principal** objeto selecionado, consulte o **Add Component** botão localizado na parte inferior do *painel Inspetor*. 
6.  Selecione esse botão e de pesquisa (digitando *Audio Source* no campo de pesquisa ou navegação as seções) para o componente chamado **Audio Source** conforme mostrado abaixo e selecioná-lo (pressionando enter nele também funciona).
7.  Uma *Audio Source* componente será adicionado para o **câmera principal**, conforme demonstrado a seguir.

    ![Adicione um componente de Audio Source.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Para o Microsoft HoloLens, você precisará alterar também o seguinte, que fazem parte dos **câmera** componente no seu **câmera principal**:
    > - **Limpe os sinalizadores de:** Cor sólida.
    > - **Plano de fundo** ' preto, alfa 0' – cor hexadecimal: 00000000 #.

## <a name="chapter-4--setup-debug-canvas"></a>Capítulo 4-tela de depuração do programa de instalação

Para mostrar a entrada e saída da tradução, uma interface do usuário básica precisa ser criado. Para este curso, você criará um objeto de tela da interface do usuário, com vários objetos de 'Text' para mostrar os dados.

1.  Com o botão direito em uma área vazia do *painel de hierarquia*, em **UI**, adicionar um **tela**.

    ![Adicione um novo objeto de tela da interface do usuário.](images/AzureLabs-Lab1-22.png)

2.  Com o objeto de tela selecionado, o *painel Inspetor* (dentro do componente 'Tela'), altere **modo de renderização** para **espaço de mundo**. 
3.  Em seguida, alterar os seguintes parâmetros na *Rect transformação do painel do Inspetor*:

    1. *POS* -  **X** 0 **Y** 0 **Z** 40
    2. *Largura* - 500
    3. *Height* -   300
    4. *Escala* - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![Atualize a transformação rect para a tela.](images/AzureLabs-Lab1-23.png)
 
4.  Clique com botão direito no **Canvas** na *painel de hierarquia*, em **interface do usuário**e adicione um **painel**. Isso **painel** fornecerá um plano de fundo para o texto que você deseja exibir na cena.
5.  Clique com botão direito no **painel** na *painel de hierarquia*, em **interface do usuário**e adicione um **objeto de texto**. Repita o mesmo processo até que você criou quatro objetos de texto de interface do usuário no total (Dica: se você tiver o primeiro objeto de 'Text' selecionado, você pode simplesmente pressionar **'Ctrl' + tinha '**, duplicar, até que você tenha quatro no total). 
6.  Para cada **objeto de texto**, selecioná-lo e usar as tabelas para definir os parâmetros no abaixo a *painel Inspetor*.

    1. Para o *Rect transformação* componente:

        | Nome                   | Transformar - *posição*             | Largura      | Height    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Para o **texto (Script)** componente:


        | Nome                   | Texto               | Tamanho da fonte    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | Status de microfone: | 20           |
        | AzureResponseLabel     | Azure Web Response | 20           |
        | DictationLabel         |   Você disse:   | 20           |
        | TranslationResultLabel |    Tradução:    | 20           |

        ![Os valores correspondentes para os rótulos da interface do usuário de entrada.](images/AzureLabs-Lab1-24.png)

    3. Além disso, verifique o estilo da fonte **negrito**. Isso tornará o texto mais fácil de ler.

        ![Fonte em negrito.](images/AzureLabs-Lab1-25.png)

7.  Para cada *objeto de texto de interface do usuário* criado na [capítulo 5](#chapter-5--create-the-results-class), crie um novo *filho* **objeto de texto de interface do usuário**. Esses filhos exibirá a saída do aplicativo. Crie *filho* objetos por meio de seu pai pretendido botão direito do mouse (por exemplo, *MicrophoneStatusLabel*) e, em seguida, selecione **interface de usuário** e, em seguida, selecione **texto**.
8.  Para cada um desses filhos, selecione-o e use as tabelas para definir os parâmetros no painel Inspetor abaixo.

    1. Para o **Rect transformação** componente:

        | Nome                  | Transformar - *posição* | Largura      | Height    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y -30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y -30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y -30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y -30 Z 0          | 300        | 30        |

    2. Para o **texto (Script)** componente:

        | Nome                  | Texto          | Tamanho da fonte    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. Em seguida, selecione a opção de alinhamento 'centre' para cada componente de texto:

    ![Alinhe o texto.](images/AzureLabs-Lab1-26.png)

10. Para garantir que o **filho do texto da interface** objetos são fáceis de ler, alterar suas *cor*. Faça isso clicando na barra de (atualmente ' preto') ao lado *cor*. 

    ![Entrada correspondente valores para as saídas do texto da interface do usuário.](images/AzureLabs-Lab1-27.png)
 
11. Em seguida, no novo, pequena, *cor* janela, altere o *cor Hex* para: **0032EAFF**

    ![Atualize a cor para azul.](images/AzureLabs-Lab1-28.png)
 
12. Veja abaixo como o **interface do usuário** deve se parecer.
    1.  No *painel de hierarquia*:

        ![Tem a hierarquia na estrutura fornecida.](images/AzureLabs-Lab1-29.png)

    2.  No *cena* e *modos de exibição de jogos*:

        ![Ter os modos de exibição de cena e jogo na mesma estrutura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Capítulo 5 – criar a classe de resultados

É o primeiro script que você precisa criar o *resultados* classe, que é responsável por fornecer uma maneira de ver os resultados da tradução. A classe armazena e exibe o seguinte: 

- O resultado da resposta do Azure.
- O status de microfone. 
- O resultado do ditado (voz em texto).
- O resultado da conversão.

Para criar essa classe: 

1.  Clique com botão direito no *painel do projeto*, em seguida, **criar > pasta**. Nomeie a pasta **Scripts**. 
 
    ![Crie a pasta de scripts.](images/AzureLabs-Lab1-31.png)

    ![Abra a pasta de scripts.](images/AzureLabs-Lab1-32.png)
 
2.  Com o **Scripts** pasta criar, clique duas vezes nele para abrir. Em seguida, dentro dessa pasta, clique com botão direito e selecione **criar >** , em seguida,  **C# Script**. Nomeie o script *resultados*. 

    ![Crie o primeiro script.](images/AzureLabs-Lab1-33.png)
 
3.  Clique duas vezes na nova *resultados* script para abri-lo com **Visual Studio**.
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

6.  Em seguida, adicione a *Awake()* método, que será chamado quando a classe inicializa. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Por fim, adicione os métodos que são responsáveis por produzir várias informações de resultados na interface do usuário. 

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

## <a name="chapter-6--create-the-microphonemanager-class"></a>Capítulo 6 – criar o *MicrophoneManager* classe

É a segunda classe que você pretende criar o *MicrophoneManager*.

Essa classe é responsável por:

- Detectando o dispositivo de gravação anexado ao computador (o que é o padrão) ou fone de ouvido.
- Capturar áudio (voz) e usar ditado para armazená-la como uma cadeia de caracteres.
- Depois que a voz foi pausado, envie o ditado para a classe de conversor.
- Hospede um método que pode parar a captura de voz, se desejado.

Para criar essa classe: 
1.  Clique duas vezes no **Scripts** pasta para abri-lo. 
2.  Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**. Nomeie o script *MicrophoneManager*. 
3.  Clique duas vezes no novo script para abri-lo com o Visual Studio.
4.  Atualizar os namespaces para ser o mesmo que o seguinte, na parte superior do *MicrophoneManager* classe:

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro do *MicrophoneManager* classe:

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

6.  Código para o *Awake()* e *Start ()* métodos agora precisa ser adicionado. Eles serão chamados quando inicializa a classe:

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

7.  Você pode *exclua* as *Update ()* método uma vez que essa classe não irá usá-lo.
8.  Agora, você precisa que os métodos que o aplicativo usa para iniciar e parar a captura de voz e passá-lo para o *tradutor* classe, que você criará em breve. Copie o código a seguir e cole-a sob o *Start ()* método.

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
    > Embora este aplicativo não fará usá-lo, o *StopCapturingAudio()* método também foi fornecido aqui, você deve implementar a capacidade de parar a captura de áudio em seu aplicativo.

9.  Agora, você precisará adicionar um manipulador de ditado que será invocado quando a voz é interrompido. Esse método, em seguida, passará o texto ditado para o *tradutor* classe.

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

10. Certifique-se de salvar suas alterações no Visual Studio antes de retornar para o Unity.

> [!WARNING]  
> Neste ponto, você observará um erro que aparecem na *Console do Unity Editor* painel ("o nome 'Conversor' não existe..."). Isso ocorre porque o código faz referência a *tradutor* classe, que você criará no próximo capítulo.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Capítulo 7 – chamada ao serviço do Azure e tradução

É o último script que você precisa criar o *tradutor* classe. 

Essa classe é responsável por:

-   Autenticar o aplicativo com *Azure*, no exchange para um **Token de autenticação**.
-   Use o **Token de autenticação** para enviar texto (recebido do *MicrophoneManager* classe) a ser traduzido.
-   Receber o resultado convertido e passá-lo para o *resultados* classe a ser visualizado na interface do usuário.

Para criar essa classe: 
1.  Vá para o **Scripts** pasta que você criou anteriormente. 
2.  Clique com botão direito no **painel do projeto**, **criar > C# Script**. Chame o script *tradutor*.
3.  Clique duas vezes na nova *tradutor* script para abri-lo **com o Visual Studio**.
4.  Adicione os namespaces a seguir na parte superior do arquivo:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro do *tradutor* classe:

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
    > - Os idiomas inseridos para as linguagens **enum** são apenas exemplos. Fique à vontade para adicionar mais se desejar; o [API dá suporte a mais de 60 idiomas](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (incluindo Klingon)!
    > - Há um [página mais interativa que abrangem os idiomas disponíveis](https://www.microsoft.com/translator/business/languages/), porém lembre-se a página será exibida apenas trabalhar quando o idioma do site é definido como ' en-us' (e o site da Microsoft será a probabilidade de redirecionamento para seu idioma nativo). Você pode alterar o idioma na parte inferior da página ou alterando a URL do site.
    > - O **authorizationKey** valor, no trecho de código acima deve ser a **chave** recebida quando você se inscreveu para o *Azure API de tradução de texto*. Isso foi abordado em [capítulo 1](#chapter-1--the-azure-portal).

6.  Código para o *Awake()* e *Start ()* métodos agora precisa ser adicionado. 
7.  Nesse caso, o código será fazer uma chamada para *Azure* usando a autorização de chave, para obter uma *Token*.

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
    > O token expirará após 10 minutos. Dependendo do cenário para seu aplicativo, você terá que fazer com que a mesma corrotina chamada várias vezes.

8.  A corrotina para obter o Token é o seguinte:

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
    > Se você editar o nome do método IEnumerator **GetTokenCoroutine()**, você precisa atualizar o *StartCoroutine* e *StopCoroutine* chamar valores de cadeia de caracteres no código acima. [De acordo com a documentação do Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), para interromper um determinado *Corrotina*, você precisa usar o método de valor de cadeia de caracteres.

9.  Em seguida, adicione a corrotina (com um método do fluxo "suporte" logo abaixo dele) para obter a tradução do texto recebido pelo *MicrophoneManager* classe. Esse código cria uma cadeia de caracteres de consulta para enviar para o *Azure API de tradução de texto*e, em seguida, usa a classe Unity UnityWebRequest interna para fazer uma chamada de 'Get' para o ponto de extremidade com a cadeia de caracteres de consulta. O resultado, em seguida, é usado para definir a tradução em seu objeto de resultados. O código a seguir mostra a implementação:

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

1.  Novamente no Editor do Unity, clique e arraste a *resultados* classe *de* o **Scripts** pasta para o **câmera principal** objeto no  *Painel de hierarquia*.
2.  Clique no **câmera principal** e examine o *painel Inspetor*. Você observará que na recém-adicionada *Script* componente, há quatro campos com valores vazios. Essas são as referências de saída para as propriedades no código. 
3.  Arraste apropriado **texto** objetos das *painel de hierarquia* para esse quatro slots, conforme mostrado na imagem abaixo.

    ![Atualize referências de destino com valores especificados.](images/AzureLabs-Lab1-34.png)
  
4.  Em seguida, clique e arraste a *Translator* classe o **Scripts** pasta para o **câmera principal** do objeto no *painel de hierarquia*. 
5.  Em seguida, clique e arraste o *MicrophoneManager* classe o **Scripts** pasta para o **câmera principal** do objeto no *painel hierarquia*. 
6.  Por fim, clique no **câmera principal** e examine o *painel Inspetor*. Você observará que o script que no qual você arrastou, há duas caixas suspensas para que permitirá que você defina os idiomas.
 
    ![Verifique se que os idiomas de tradução pretendida são de entrada.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Capítulo 9 – teste na realidade mista

Neste ponto, você precisa testar a cena foi implementada corretamente.

Certifique-se de que:

- Todas as configurações mencionadas [capítulo 1](#chapter-1--the-azure-portal) estão definidas corretamente. 
- O *resultados*, *Translator*, e *MicrophoneManager*, scripts estão anexados ao **câmera principal** objeto. 
- Você fez sua *Azure API de tradução de texto* serviço **chave** dentro a **authorizationKey** variável dentro a *Translator* Script.  
- Todos os campos a *painel de Inspetor de câmera principal* são atribuídas corretamente.
- O microfone está funcionando ao executar sua cena (se não, verifique se o microfone anexado é o *padrão* dispositivo e se você tem [configurá-lo corretamente dentro do Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).

Você pode testar o fone de ouvido imersivo, pressionando as **reproduzir** botão na *Editor do Unity*.
O aplicativo deve estar funcionando por meio de fone de ouvido imersivo anexado.

> [!WARNING]  
> Se você vir um erro no console do Unity sobre o dispositivo de áudio padrão a alteração, a cena pode não funcionar conforme o esperado. Isso é devido à maneira como o portal de realidade misturada lida com microfones internos para fones de ouvido que têm-los. Se você vir esse erro, simplesmente parar a cena e iniciá-lo novamente e as coisas devem funcionar como esperado.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Capítulo 10 – compilar a solução UWP e carregar no computador local

Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído, portanto, é hora de criá-lo do Unity.

1.  Navegue até **configurações de Build**: **Arquivo > configurações de Build...**
2.  Dos **configurações de Build** janela, clique em **Build**.

    ![Compile a cena do Unity.](images/AzureLabs-Lab1-36.png)
  
3.  Se ainda não estiver, marque **Unity C# projetos**.
4.  Clique em **Compilar**. Unity iniciará uma *Explorador de arquivos* janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em. Criar pasta agora e nomeie- *aplicativo*. Em seguida, com o *App* pasta selecionada, pressione **Selecionar pasta**. 
5.  Unity começará a compilar seu projeto para o *aplicativo* pasta. 
6.  Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um *Explorador de arquivos* janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).

## <a name="chapter-11--deploy-your-application"></a>Capítulo 11 – implantar seu aplicativo

Para implantar seu aplicativo:

1.  Navegue até seu novo build do Unity (o *App* pasta) e abra o arquivo de solução com *Visual Studio*.
2.  No, selecione a configuração da solução **depurar**.
3.  Na plataforma da solução, selecione **x86**, **Máquina Local**. 

    > Para o Microsoft HoloLens, talvez você ache mais fácil de definir isso como *máquina remota*, de modo que você não estiver vinculado ao seu computador. No entanto, você precisará também fazer o seguinte:
    > - Saber a **endereço IP** de seu HoloLens, que podem ser encontrado dentro a *Configurações > rede e Internet > Wi-Fi > Opções avançadas de*; o IPv4 é o endereço que você deve usar. 
    > - Certifique-se *modo de desenvolvedor* é **na**; encontrado na *Configurações > atualização e segurança > para os desenvolvedores*.

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  Vá para **menu Build** e clique em **implantar solução** para carregar o aplicativo a seu computador.
5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado.
6.  Depois de iniciado, o aplicativo solicitará que você autorizar o acesso ao microfone. Certifique-se de clicar o **Sim** botão.
7.  Agora você está pronto para começar a traduzir!

## <a name="your-finished-translation-text-api-application"></a>O aplicativo de API de tradução de texto concluído

Parabéns, você criou um aplicativo de realidade mista que aproveita a API de texto de tradução do Azure para converter fala em texto traduzido.

![Produto final.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Você pode adicionar funcionalidade de texto em fala para o aplicativo, para que o texto retornado é falado?

### <a name="exercise-2"></a>Exercício 2

Tornam possível para o usuário altere os idiomas de origem e de saída ('de' e 'para') dentro do próprio aplicativo, portanto, o aplicativo não precisa ser recriado sempre que você deseja alterar os idiomas.
