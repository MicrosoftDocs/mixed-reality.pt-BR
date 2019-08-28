---
title: Sr e Azure 302 – visão computacional
description: Conclua este curso para aprender a reconhecer o conteúdo visual dentro de uma imagem fornecida, usando o Azure Pesquisa Visual Computacional em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, pesquisa Visual computacional, hololens, imersão, VR
ms.openlocfilehash: 9cc526afdc36b8056afd61948fea5cf98015bb35
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047192"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br>

# <a name="mr-and-azure-302-computer-vision"></a>Sr e Azure 302: Pesquisa Visual computacional

Neste curso, você aprenderá a reconhecer o conteúdo visual dentro de uma imagem fornecida, usando os recursos de Pesquisa Visual Computacional do Azure em um aplicativo de realidade misturada.

Os resultados de reconhecimento serão exibidos como marcas descritivas. Você pode usar esse serviço sem a necessidade de treinar um modelo de aprendizado de máquina. Se sua implementação exigir treinamento de um modelo de aprendizado de máquina, consulte [Mr e Azure 302b](mr-azure-302b.md).

![resultado do laboratório](images/AzureLabs-Lab2-000.png)

O Microsoft Pesquisa Visual Computacional é um conjunto de APIs projetado para fornecer aos desenvolvedores o processamento e a análise de imagens (com informações de retorno), usando algoritmos avançados, tudo da nuvem. Os desenvolvedores carregam uma URL de imagem ou imagem, e os algoritmos de API da Pesquisa Visual Computacional da Microsoft analisam o conteúdo visual, com base nas entradas escolhidas pelo usuário, que podem retornar informações, incluindo, identificar o tipo e a qualidade de uma imagem, detectar faces humanas ( retornar suas coordenadas) e marcar ou categorizar imagens. Para obter mais informações, visite a [página de API da pesquisa Visual computacional do Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

Após a conclusão deste curso, você terá um aplicativo de HoloLens de realidade misturada, que poderá fazer o seguinte:

1.  Usando o gesto de toque, a câmera do HoloLens capturará uma imagem.
2.  A imagem será enviada para o serviço de API da Pesquisa Visual Computacional do Azure. 
3.  Os objetos reconhecidos serão listados em um grupo de interface do usuário simples posicionado na cena do Unity.

Em seu aplicativo, cabe a você como você integrará os resultados com seu design. Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity. É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Sr e Azure 302: Pesquisa Visual computacional</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Embora este curso se concentre principalmente no HoloLens, você também pode aplicar o que aprende neste curso a fones de ouvido (VR) de realidade mista do Windows. Como os headsets de imersão (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu PC. Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a headsets de imersão (VR).

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
- Uma câmera conectada ao seu PC (para desenvolvimento de headsets de imersão)
- Acesso à Internet para a instalação do Azure e recuperação de API da Pesquisa Visual Computacional

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).
2.  Configure e teste seu HoloLens. Se você precisar de suporte para configurar seu HoloLens, [visite o artigo configuração do hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  É uma boa ideia executar a calibragem e o ajuste do sensor ao começar a desenvolver um novo aplicativo do HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

Para obter ajuda sobre calibragem, siga este [link para o artigo Calibration do HoloLens](calibration.md#hololens-2).

Para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste do sensor do HoloLens](sensor-tuning.md).

## <a name="chapter-1--the-azure-portal"></a>Capítulo 1 – o portal do Azure

Para usar o serviço de *API da pesquisa Visual computacional* no Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.

1.  Primeiro, faça logon no [portal do Azure](https://portal.azure.com). 

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure *API da pesquisa Visual computacional*e clique em **Enter**.

    ![Criar um novo recurso no Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.
 
3.  A nova página fornecerá uma descrição do serviço *API da pesquisa Visual computacional* . Na parte inferior esquerda desta página, selecione o botão **criar** para criar uma associação com esse serviço.

    ![Sobre o serviço de API da pesquisa Visual computacional](images/AzureLabs-Lab2-01.png)
 
4.  Depois de clicar em **criar**:

    1. Insira o **nome** desejado para esta instância de serviço.
    2. Selecione uma **assinatura**.
    3. Selecione o **tipo de preço** apropriado para você, se esta for a primeira vez que criar um serviço de *API da pesquisa Visual computacional* , uma camada gratuita (chamada F0) deverá estar disponível para você.
    4. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determine o local do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.

    6. Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.
    7. Clique em criar.

        ![Informações de criação de serviço](images/AzureLabs-Lab2-02.png)

5.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.
6.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![Consulte a nova notificação para seu novo serviço](images/AzureLabs-Lab2-03.png) 
 
7.  Clique na notificação para explorar sua nova instância de serviço. 

    ![Selecione o botão ir para o recurso.](images/AzureLabs-Lab2-04.png)
 
8. Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. Você será levado para sua nova instância do serviço API da Pesquisa Visual Computacional. 

    ![Seu novo serviço de API da Pesquisa Visual Computacional](images/AzureLabs-Lab2-05.png)
 
9.  Neste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, o que é feito por meio do uso da chave de assinatura do serviço.
10. Na página *início rápido* , do seu serviço de *API da pesquisa Visual computacional* , navegue até a primeira etapa, *pegue as chaves*e clique em **chaves** (você também pode conseguir isso clicando nas teclas de hiperlink azul, localizadas no menu de navegação serviços, indicado pelo ícone de chave). Isso revelará suas *chaves*de serviço.
11. Faça uma cópia de uma das chaves exibidas, pois você precisará dela posteriormente em seu projeto. 

12. Volte para a página *início rápido* e, a partir daí, busque seu ponto de extremidade. Lembre-se de que seu pode ser diferente, dependendo de sua região (que, se for, você precisará fazer uma alteração no código posteriormente). Faça uma cópia deste ponto de extremidade para uso posterior:

    ![Seu novo serviço de API da Pesquisa Visual Computacional](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > Você pode verificar quais são os vários pontos de extremidade [aqui](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). 

## <a name="chapter-2--set-up-the-unity-project"></a>Capítulo 2 – configurar o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra o *Unity* e clique em **novo**. 

    ![Inicie o novo projeto do Unity.](images/AzureLabs-Lab2-06.png)

2.  Agora, você precisará fornecer um nome de projeto de Unity. Insira **MR_ComputerVision**. Verifique se o tipo de projeto está definido como **3D**. Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab2-07.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar preferências de >** e, em seguida, na nova janela, navegue até **Ferramentas externas**. Altere o **Editor de script externo** para o **Visual Studio 2017**. Feche a janela **preferências** .

    ![Atualize a preferência do editor de script.](images/AzureLabs-Lab2-08.png)

4.  Em seguida, vá para **arquivo > configurações de Build** e selecione **plataforma universal do Windows**e, em seguida, clique no botão **alternar plataforma** para aplicar sua seleção.

    ![Janela de configurações de compilação, alterne a plataforma para UWP.](images/AzureLabs-Lab2-10.png)

5.  Ainda no **arquivo > configurações de compilação** e certifique-se de que:

    1. O **dispositivo de destino** está definido como **HoloLens**

        > Para os headsets de imersão, defina **dispositivo de destino** para *qualquer dispositivo*.

    2. O **tipo de compilação** está definido como **D3D**
    3. O **SDK** está definido para o **mais recente instalado**
    4. A **versão do Visual Studio** está definida para o **mais recente instalado**
    5. **Compilar e executar** é definido como **computador local**
    6. Salve a cena e adicione-a à compilação.

        1. Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.
        
            ![Clique no botão Adicionar cenas abertas](images/AzureLabs-Lab2-11.png)

        2. Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![Criar nova pasta de scripts](images/AzureLabs-Lab2-12.png)

        3. Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo*:, digite **MR_ComputerVisionScene**e clique em **salvar**.

            ![Dê um nome à nova cena.](images/AzureLabs-Lab2-13.png)

            > Lembre-se de que você deve salvar as cenas do Unity na pasta *ativos* , pois elas devem ser associadas ao projeto do Unity. Criar a pasta de cenas (e outras pastas semelhantes) é uma maneira típica de estruturar um projeto do Unity.

    7. As configurações restantes, em *configurações de compilação*, devem ser deixadas como padrão por enquanto.

6. Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado. 

    ![Abra as configurações do Player.](images/AzureLabs-Lab2-14.png)

7. Nesse painel, algumas configurações precisam ser verificadas:

    1. Na guia **outras configurações** :

        1. A **versão de tempo de execução de script** deve ser **estável** (.net 3,5 equivalente).
        2. O **back-end de script** deve ser **.net**
        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**

            ![Atualize outras configurações.](images/AzureLabs-Lab2-15.png)
      
    2. Na guia **configurações de publicação** , em **recursos**, marque:

        1. **InternetClient**
        2. **Integrada**

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab2-16.png)

    3. Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o SDK do **Windows Mixed Reality** foi adicionado.

        ![Atualize as configurações de X R.](images/AzureLabs-Lab2-17.png)

8.  De volta *às configurações de Build* , os projetos do  _C# Unity_ não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste. 
9.  Feche a janela configurações de compilação.
10. Salve sua cena e projeto (**arquivo > salvar cena/arquivo > salvar projeto**).

## <a name="chapter-3--main-camera-setup"></a>Capítulo 3 – configuração principal da câmera

> [!IMPORTANT]
> Se você quiser ignorar o componente *de configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para baixar esse [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), importe-o para seu projeto como um [pacote personalizado](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue no [capítulo 5](#chapter-5--create-the-resultslabel-class).

1.  No *painel hierarquia*, selecione a **câmera principal**. 
2.  Depois de selecionado, você poderá ver todos os componentes da **câmera principal** no *painel Inspetor*.

    1. O **objeto de câmera** deve ser nomeado como a **câmera principal** (Observe a grafia!)
    2. A **marca** da câmera principal deve ser definida como **MainCamera** (Observe a ortografia!)
    3. Verifique se a **posição de transformação** está definida como **0, 0,** 0
    4. Defina **limpar sinalizadores** como **cor sólida** (ignore isto para fone de ouvido de imersão).
    5. Defina a cor do **plano de fundo** do componente da câmera como **preto, alfa 0 (código hex: #00000000)** (ignorar isso para headsets de imersão).

        ![Atualize os componentes da câmera.](images/AzureLabs-Lab2-18.png)
 
3.  Em seguida, você precisará criar um objeto "cursor" simples anexado à **câmera principal**, o que ajudará a posicionar a saída da análise de imagem quando o aplicativo estiver em execução. Esse cursor determinará o ponto central do foco da câmera.

Para criar o cursor:

1.  No *painel hierarquia*, clique com o botão direito do mouse na **câmera principal**. Em **objeto 3D**, clique em **esfera**.

    ![Selecione o objeto de cursor.](images/AzureLabs-Lab2-19.png)
 
2.  Renomeie a **esfera** para **cursor** (clique duas vezes no objeto de cursor ou pressione o botão de teclado "F2" com o objeto selecionado) e verifique se ele está localizado como filho da **câmera principal**.

3.  No *painel hierarquia*, clique com o botão esquerdo do **cursor**. Com o cursor selecionado, ajuste as seguintes variáveis no *painel Inspetor*:

    1. Defina a *posição de transformação* como **0, 0, 5**
    2. Defina a *escala* como **0, 2, 0, 2, 0, 2**

        ![Atualize a posição e a escala de transformação.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Capítulo 4 – configurar o sistema de etiquetas

Depois de capturar uma imagem com a câmera do HoloLens, essa imagem será enviada para a instância do serviço de *API da pesquisa Visual computacional do Azure* para análise. 

Os resultados dessa análise serão uma lista de objetos reconhecidos chamados **marcas**. 

Você usará rótulos (como um texto 3D no espaço de mundo) para exibir essas marcas no local em que a foto foi tirada.

As etapas a seguir mostrarão como configurar o objeto **Label** .

1.  Clique com o botão direito do mouse em qualquer lugar no painel hierarquia (o local não importa nesse ponto), em **objeto 3D**, adicione um **texto 3D**. Nomeie-o como **LabelText**.

    ![Criar objeto de texto 3D.](images/AzureLabs-Lab2-21.png)
 
2.  No *painel hierarquia*, clique no botão esquerdo do **LabelText**. Com o **LabelText** selecionado, ajuste as seguintes variáveis no *painel Inspetor*:

    1. Defina a **posição** como **0, 0, 0**
    2. Defina a **escala** como **0, 1, 0, 1, 0, 1**
    3. Na malha de **texto**do componente:
    4. Substituir todo o texto no **texto**, por "..."        
    5. Definir a **âncora** para o **Centro central**
    6. Definir o **alinhamento** como **centralizado**
    7. Defina o **tamanho da guia** como **4**
    8. Defina o **tamanho da fonte** como **50**
    9. Defina a **cor** como **#FFFFFFFF**

    ![Componente de texto](images/AzureLabs-Lab2-21-5.png)

3.  Arraste o **LabelText** do *painel hierarquia*para a *pasta ativo*, dentro do *painel Projeto*. Isso fará com que o **LabelText** um pré-fabricado, para que possa ser instanciado no código.

    ![Crie um pré-fabricado do objeto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  Você deve excluir o **LabelText** do *painel hierarquia*, de modo que ele não será exibido na cena de abertura. Como agora é um pré-fabricado, que você chamará para instâncias individuais da sua pasta de ativos, não há necessidade de mantê-la dentro da cena. 
5.  A estrutura final do objeto no *painel hierarquia* deve ser parecida com a mostrada na imagem abaixo:

    ![Estrutura final do painel de hierarquia.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Capítulo 5 – criar a classe ResultsLabel

O primeiro script que você precisa criar é a classe *ResultsLabel* , que é responsável pelo seguinte: 

- Criando os rótulos no espaço do mundo apropriado, em relação à posição da câmera.
- Exibindo as marcas da imagem Analysis.

Para criar esta classe: 

1.  Clique com o botão direito do mouse no *painel Projeto*e **crie > pasta**. Nomeie a pasta **scripts**. 

    ![Criar pasta de scripts.](images/AzureLabs-Lab2-24.png)

2.  Com a pasta **scripts** Create, clique duas vezes nela para abrir. Em seguida, dentro dessa pasta, clique com o botão direito do mouse **C#** e selecione **criar >** , em seguida, script. Nomeie o script *ResultsLabel*. 

3.  Clique duas vezes no novo script *ResultsLabel* para abri-lo com o **Visual Studio**.

4.  Dentro da classe, insira o seguinte código na classe *ResultsLabel* :

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.
7.  De volta ao *Editor do Unity*, clique e arraste a classe *ResultsLabel* da pasta **scripts** para o objeto da **câmera principal** no *painel hierarquia*.
8.  Clique na **câmera principal** e examine o *painel Inspetor*.

Você observará que, a partir do script que você acabou de arrastar para a câmera, há dois campos: Pré-fabricado de **cursor** e **rótulo**.

9.  Arraste o objeto chamado **cursor** do *painel hierarquia* para o slot chamado **cursor**, conforme mostrado na imagem abaixo.
10. Arraste o objeto chamado **LabelText** da *pasta ativos* no *painel Projeto* para o slot chamado **rótulo pré-fabricado**, conforme mostrado na imagem abaixo. 

    ![Defina os destinos de referência no Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Capítulo 6 – criar a classe ImageCapture

A próxima classe que você vai criar é a classe *ImageCapture* . Essa classe é responsável por:

-   Capturando uma imagem usando a câmera do HoloLens e armazenando-a na pasta do aplicativo.
-   Capturando gestos de toque do usuário.

Para criar esta classe: 

1.  Vá para a pasta **scripts** que você criou anteriormente. 
2.  Clique com o botão direito do mouse dentro da pasta, **crie > C# script**. Chame o script *ImageCapture*. 
3.  Clique duas vezes no novo script *ImageCapture* para abri-lo com o **Visual Studio**.
4.  Adicione os seguintes namespaces à parte superior do arquivo:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro da classe *ImageCapture* , acima do método *Start ()* :

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
A variável **tapsCount** armazenará o número de gestos de toque capturados do usuário. Esse número é usado na nomenclatura das imagens capturadas.

6.  O código para os métodos *ativo ()* e *Iniciar ()* agora precisa ser adicionado. Eles serão chamados quando a classe for inicializada:

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implemente um manipulador que será chamado quando ocorrer um gesto de toque. 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
O método *TapHandler ()* incrementa o número de toques capturados do usuário e usa a posição atual do cursor para determinar onde posicionar um novo rótulo.

Esse método chama o método *ExecuteImageCaptureAndAnalysis ()* para iniciar a funcionalidade principal deste aplicativo.

8.  Depois que uma imagem for capturada e armazenada, os seguintes manipuladores serão chamados. Se o processo for bem-sucedido, o resultado será passado para o *visionmanager* (que você ainda deseja criar) para análise.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  Em seguida, adicione o método que o aplicativo usa para iniciar o processo de captura de imagem e armazenar a imagem.

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> Neste ponto, você observará um erro exibido no *painel de console do editor do Unity*. Isso ocorre porque o código faz referência à classe visionmanager que você criará no próximo capítulo.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Capítulo 7 – chamar o Azure e a análise de imagem

O último script que você precisa criar é a classe visionmanager. 

Essa classe é responsável por:

-   Carregando a imagem mais recente capturada como uma matriz de bytes.
-   Enviando a matriz de bytes para a instância do serviço de *API da pesquisa Visual computacional do Azure* para análise.
-   Recebendo a resposta como uma cadeia de caracteres JSON.
-   Desserializar a resposta e passar as marcas resultantes para a classe *ResultsLabel* .
 
Para criar esta classe:

1.  Clique duas vezes na pasta **scripts** para abri-la. 
2.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > C# script**. Nomeie o script *visionmanager*. 
3.  Clique duas vezes no novo script para abri-lo com o Visual Studio.
4.  Atualize os namespaces para que sejam iguais aos seguintes, na parte superior da classe *visionmanager* :

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  Na parte superior do seu script, *dentro* da classe visionmanager (acima do método *Start ()* ), agora você precisa criar duas *classes* que irão representar a resposta JSON desserializada do Azure:

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > As classes *TagData* e *AnalysedObject* precisam ter o atributo *[System. Serializable]* adicionado antes que a declaração possa ser desserializada com as bibliotecas do Unity.

6.  Na classe Visionmanager, você deve adicionar as seguintes variáveis:

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > Certifique-se de inserir sua **chave de autenticação** na variável **authorizationKey** . Você terá anotado sua **chave de autenticação** no início deste curso, [capítulo 1](#chapter-1--the-azure-portal).

    > [!WARNING] 
    > A variável **visionAnalysisEndpoint** pode ser diferente da especificada neste exemplo. O **oeste-US** se refere estritamente a instâncias de serviço criadas para a região oeste dos EUA. Atualize isso com a [URL do ponto de extremidade](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); Aqui estão alguns exemplos de como isso pode ser:
    > - Europa Ocidental:`https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Sudeste da Ásia:`https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Leste da Austrália:`https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  O código para ativo agora precisa ser adicionado. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  Em seguida, adicione a corrotina (com o método de fluxo estático abaixo dela), que obterá os resultados da análise da imagem capturada pela classe *ImageCapture* . 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.
10. De volta ao editor do Unity, clique e arraste as classes visionmanager e *ImageCapture* da pasta **scripts** para o objeto da **câmera principal** no *painel hierarquia*. 

## <a name="chapter-8--before-building"></a>Capítulo 8 – antes de Compilar

Para executar um teste completo de seu aplicativo, você precisará Sideload-lo no seu HoloLens.
Antes de fazer isso, verifique se:

-   Todas as configurações mencionadas no [capítulo 2](#chapter-2--set-up-the-unity-project) estão definidas corretamente. 
-   Todos os scripts são anexados ao objeto da **câmera principal** . 
-   Todos os campos no *painel principal do Inspetor de câmera* são atribuídos corretamente.
-   Certifique-se de inserir sua **chave de autenticação** na variável **authorizationKey** .
-   Verifique se você também verificou seu ponto de extremidade em seu script do visionmanager e se ele está alinhado à *sua* região (este documento usa o *Oeste-EUA* por padrão).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Capítulo 9 – criar a solução UWP e sideloadr o aplicativo
Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.

1.  Navegue até *criar configurações* - **arquivo > configurações de Build...**
2.  Na janela *configurações de compilação* , clique em **Compilar**.

    ![Compilando o aplicativo do Unity](images/AzureLabs-Lab2-26.png)

3.  Se ainda não estiver, **os C# projetos de Unity**de tique.
4.  Clique em **Compilar**. O Unity iniciará uma janela *Explorador de arquivos* , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado. Crie essa pasta agora e nomeie-a como *aplicativo*. Em seguida, com a pasta de *aplicativo* selecionada, pressione **Selecionar pasta**. 
5.  O Unity começará a criar seu projeto na pasta do *aplicativo* . 
6.  Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do *Explorador de arquivos* no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).

## <a name="chapter-10--deploy-to-hololens"></a>Capítulo 10 – implantar no HoloLens

Para implantar no HoloLens:

1.  Você precisará do endereço IP do seu HoloLens (para implantação remota) e para garantir que seu HoloLens esteja no **modo de desenvolvedor**. Para fazer isso:

    1. Enquanto estiver desgastando seu HoloLens, abra as **configurações**.
    2. Acessar **Opções de rede & Internet > Wi-Fi > avançado**
    3. Anote o endereço **IPv4** .
    4. Em seguida, navegue de volta para **configurações**e, em seguida, **atualize & > de segurança para desenvolvedores** 
    5. Defina o modo de desenvolvedor em.

2.  Navegue até sua nova compilação do Unity (a pasta do *aplicativo* ) e abra o arquivo de solução com o *Visual Studio*.
3.  Na configuração da solução, selecione **depurar**.
4.  Na plataforma da solução, selecione **x86**, **computador remoto**. 

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  Vá para o **menu Compilar** e clique em **implantar solução**para Sideload o aplicativo ao seu HoloLens.
6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!

> [!NOTE]
> Para implantar em headsets de imersão, defina a **plataforma da solução** como *computador local*e defina a **configuração** a ser depurada, com *x86* como a **plataforma**. Em seguida, implante no computador local, usando o **menu Compilar**, selecionando *implantar solução*. 

## <a name="your-finished-computer-vision-api-application"></a>Seu aplicativo API da Pesquisa Visual Computacional concluído

Parabéns, você criou um aplicativo de realidade misturada que aproveita a API da Pesquisa Visual Computacional do Azure para reconhecer objetos do mundo real e exibir a confiança do que foi visto.

![resultado do laboratório](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Assim como você usou o parâmetro *Tags* (como evidenciado no ponto de *extremidade* usado no *visionmanager*), estenda o aplicativo para detectar outras informações; Veja a quais outros parâmetros você tem acesso [aqui](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).

### <a name="exercise-2"></a>Exercício 2

Exiba os dados do Azure retornados, de forma mais conversada e legível, talvez ocultando os números. Embora um bot possa estar falando para o usuário.
