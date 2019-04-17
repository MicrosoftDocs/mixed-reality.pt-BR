---
title: MR e 302 do Azure - visão do computador
description: Conclua este curso para aprender a reconhecer conteúdo visual em uma imagem fornecido, usando a visão do computador do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, pesquisa Visual computacional, hololens, imersivo, vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589150"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-and-azure-302-computer-vision"></a>MR e 302 do Azure: Pesquisa Visual computacional

Neste curso, você aprenderá a reconhecer conteúdo visual em uma imagem fornecido, usando recursos de pesquisa Visual computacional do Azure em um aplicativo de realidade misturada.

Resultados do reconhecimento serão exibidos como marcas descritivas. Você pode usar esse serviço sem a necessidade para treinar um modelo de aprendizado de máquina. Se a sua implementação exija treinar um modelo de aprendizado de máquina, consulte [MR e Azure 302b](mr-azure-302b.md).

![resultado de laboratório](images/AzureLabs-Lab2-000.png)

A visão da Microsoft de computador é um conjunto de APIs projetados para fornecer aos desenvolvedores de processamento de imagens e análise (com informações de retorno), usando algoritmos avançados, tudo na nuvem. Os desenvolvedores carregar uma imagem ou URL da imagem e os algoritmos de API de visão do computador Microsoft analisar o conteúdo visual, com base em entradas escolhidas o usuário, que, em seguida, pode retornar informações, incluindo, identificando o tipo e a qualidade de uma imagem, detectar rostos humanos ( retornando suas coordenadas) e a marcação ou categorizar imagens. Para obter mais informações, visite o [página de API de visão do computador Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

Com a conclusão deste curso, você terá uma realidade misturada aplicativo HoloLens, que será capaz de fazer o seguinte:

1.  Usando o gesto de toque, a câmera do HoloLens irá capturar uma imagem.
2.  A imagem será enviada ao serviço de API de visão do computador do Azure. 
3.  Os objetos reconhecidos serão listados em um grupo de interface do usuário simple posicionado na cena Unity.

Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design. Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity. Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> MR e 302 do Azure: Pesquisa Visual computacional</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Enquanto este curso se concentra principalmente em HoloLens, você também pode aplicar o que você aprenderá neste curso para fones de ouvido Windows Mixed Reality de imersão (VR). Como fones imersivos em exposição (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu computador. Como acompanhar o curso, você verá notas quaisquer alterações que você talvez precise ser empregadas para dar suporte a fones imersivos em exposição (VR).

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
- Uma câmera conectada ao seu PC (para desenvolvimento imersivo fone de ouvido)
- Acesso à Internet para a instalação do Azure e a recuperação de API de visão do computador

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).
2.  Configurar e testar o HoloLens. Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  É uma boa ideia executar calibragem e ajuste de Sensor ao começar a desenvolver um new App HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).

Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).

## <a name="chapter-1--the-azure-portal"></a>Capítulo 1 – Portal do Azure

Para usar o *API de visão do computador* serviço no Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo.

1.  Primeiro, faça logon na [Portal do Azure](https://portal.azure.com). 

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, você precisará criá-lo. Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.

2.  Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure *API de visão do computador*e clique em **Enter**.

    ![Criar um novo recurso no Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.
 
3.  A nova página fornecerá uma descrição do *API de visão do computador* service. Na parte inferior esquerda desta página, selecione a **criar** botão para criar uma associação com este serviço.

    ![Sobre o serviço de api de visão do computador](images/AzureLabs-Lab2-01.png)
 
4.  Depois de clicar em **criar**:

    1. Inserir sua desejada **nome** para esta instância de serviço.
    2. Selecione uma **assinatura**.
    3. Selecione o **tipo de preço** apropriado para você, se esse for o primeiro tempo para criar um *API de visão do computador* serviço, uma camada gratuita (chamada F0) deve estar disponível para você.
    4. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determine o local para seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local seria o ideal é que na região em que o aplicativo é executado. Alguns ativos do Azure estão disponíveis somente em determinadas regiões.

    6. Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.
    7. Clique em criar.

        ![Informações de criação de serviço](images/AzureLabs-Lab2-02.png)

5.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.
6.  Uma notificação será exibida no portal depois que a instância do serviço é criada.

    ![Veja a nova notificação para seu novo serviço](images/AzureLabs-Lab2-03.png) 
 
7.  Clique na notificação para explorar a nova instância do serviço. 

    ![Selecione o botão Ir para o recurso.](images/AzureLabs-Lab2-04.png)
 
8. Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço. Você será levado para a nova instância de serviço de API de visão do computador. 

    ![Seu novo serviço de API de visão do computador](images/AzureLabs-Lab2-05.png)
 
9.  Dentro deste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, que é feito por meio do uso de chave de assinatura do seu serviço.
10. Dos *início rápido* página, de seu *API de visão do computador* do serviço, navegue até a primeira etapa, *pegue suas chaves*e clique em **chaves** ( Você também pode obter isso clicando no hiperlink azul chaves, localizado no menu de navegação de serviços, indicado pelo ícone de chave). Isso irá revelar o seu serviço *chaves*.
11. Faça uma cópia de uma das chaves exibidas, pois precisará dele posteriormente em seu projeto. 

12. Volte para o *início rápido* da página e a partir daí, buscar o ponto de extremidade. Lembre-se de que seu site pode ser diferente, dependendo da sua região (que se for, você precisará fazer uma alteração em seu código mais tarde). Faça uma cópia desse ponto de extremidade para uso posterior:

    ![Seu novo serviço de API de visão do computador](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > Você pode verificar quais são os vários pontos de extremidade [aqui](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). 

## <a name="chapter-2--set-up-the-unity-project"></a>Capítulo 2 – configurar o projeto do Unity

A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.

1.  Abra *Unity* e clique em **New**. 

    ![Inicie um novo projeto do Unity.](images/AzureLabs-Lab2-06.png)

2.  Agora, você precisará fornecer um nome de projeto do Unity. Inserir **MR_ComputerVision**. Verifique se o tipo de projeto é definido como **3D**. Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab2-07.png)

3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Vá para **Editar > Preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

    ![Atualize as preferências do editor de script.](images/AzureLabs-Lab2-08.png)

4.  Em seguida, vá para **arquivo > configurações de Build** e selecione **plataforma Universal do Windows**, em seguida, clique no **alternar plataforma** botão Aplicar sua seleção.

    ![Crie janela de configurações, alternar a plataforma para a UWP.](images/AzureLabs-Lab2-10.png)

5.  Enquanto estiver na **arquivo > configurações de Build** e certifique-se de que:

    1. **Dispositivo de destino** é definido como **HoloLens**

        > Para os fones imersivos em exposição, defina **dispositivo de destino** à *qualquer dispositivo*.

    2. **Tipo de compilação** é definido como **D3D**
    3. **SDK** é definido como **mais recente instalada**
    4. **Versão do Visual Studio** é definido como **mais recente instalada**
    5. **Compilar e executar** é definido como **Máquina Local**
    6. Salve a cena e adicioná-lo para a compilação.

        1. Fazer isso selecionando **cenas abra Adicionar**. Salvamento janela será exibida.
        
            ![Clique em Adicionar botão cenas aberto](images/AzureLabs-Lab2-11.png)

        2. Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.

            ![Criar nova pasta de scripts](images/AzureLabs-Lab2-12.png)

        3. Abrir seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo*: campo de texto, digite **MR_ComputerVisionScene**, em seguida, clique em **salvar** .

            ![Dê um nome de nova cena.](images/AzureLabs-Lab2-13.png)

            > Esteja ciente de que você deve salvar suas cenas de Unity dentro do *ativos* pasta, pois eles devem estar associados ao projeto do Unity. Criando a pasta de cenas (e outras pastas semelhantes) é uma maneira comum de estruturar um projeto do Unity.

    7. O restante de configurações, em *configurações de Build*, deverá ser deixado como padrão por enquanto.

6. No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado. 

    ![Abra configurações do player.](images/AzureLabs-Lab2-14.png)

7. Neste painel, algumas configurações precisam ser verificados:

    1. No **outras configurações** guia:

        1. **Versão de tempo de execução de scripts** deve ser **estável** (.NET 3.5 equivalente).
        2. **Script de back-end** deve ser **.NET**
        3. **Nível de compatibilidade de API** deve ser **.NET 4.6**

            ![Outras configurações de atualização.](images/AzureLabs-Lab2-15.png)
      
    2. Dentro de **configurações de publicação** guia, em **recursos**, verifique:

        1. **InternetClient**
        2. **Webcam**

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab2-16.png)

    3. Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.

        ![Atualize as configurações de R de X.](images/AzureLabs-Lab2-17.png)

8.  Volta *configurações de Build* _Unity C#_  projetos não fica acinzentado; marque a caixa de seleção ao lado disso. 
9.  Feche a janela de configurações de Build.
10. Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).

## <a name="chapter-3--main-camera-setup"></a>Capítulo 3 – instalação de câmera principal

> [!IMPORTANT]
> Se você quiser ignorar a *configurar o Unity* componente deste curso e continuar diretamente no código, fique à vontade para baixá-lo [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), importá-lo para seu projeto como um [pacote personalizado ](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 5](#chapter-5--create-the-resultslabel-class).

1.  No *painel de hierarquia*, selecione o **câmera principal**. 
2.  Depois de selecionado, você poderá ver todos os componentes do **câmera principal** na *painel Inspetor*.

    1. O **objeto de câmera** deve ser nomeado **câmera principal** (Observe a ortografia!)
    2. A câmera principal **marca** deve ser definida como **MainCamera** (Observe a ortografia!)
    3. Verifique se o **transformar posição** é definido como **0, 0, 0**
    4. Definir **Limpar sinalizadores** à **cor sólida** (Ignorar para fone de ouvido imersivo).
    5. Definir a **em segundo plano** cor do componente a câmera **preto, alfa 0 (código hexadecimal: #00000000)** (Ignorar para fone de ouvido imersivo).

        ![Atualize os componentes de câmera.](images/AzureLabs-Lab2-18.png)
 
3.  Em seguida, você terá que criar um objeto simples "Cursor" anexado à **câmera principal**, que ajudam a posicionar a análise de imagem produzirá quando o aplicativo está em execução. Esse Cursor determinará o ponto central do foco da câmera.

Para criar o Cursor:

1.  No *painel de hierarquia*, clique com botão direito no **câmera principal**. Sob **objeto 3D**, clique em **esfera**.

    ![Selecione o objeto de Cursor.](images/AzureLabs-Lab2-19.png)
 
2.  Renomear a **esfera** à **Cursor** (clique duas vezes o objeto de Cursor ou pressione o botão de teclado 'F2' com o objeto selecionado) e verifique se ele está localizado como filho do **câmera principal**.

3.  No *painel de hierarquia*, clique com o botão esquerdo na **Cursor**. Com o Cursor selecionado, ajustar as seguintes variáveis na *painel Inspetor*:

    1. Defina as *transformar posição* para **0, 0, 5**
    2. Defina as *dimensionamento* para **0,02, 0,02, 0,02**

        ![Atualize a posição de transformação e a escala.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Capítulo 4-instalação do sistema de rótulo

Depois de capturar uma imagem com câmera dos HoloLens, essa imagem será enviada para seu *API de visão do computador Azure* instância de serviço para análise. 

Os resultados dessa análise será uma lista de objetos, reconhecidos chamado **marcas**. 

Você usará rótulos (como um texto 3D no espaço de mundo) para exibir essas marcas no local em que a foto foi tirada.

As etapas a seguir mostram como configurar o **rótulo** objeto.

1.  Clique com botão direito em qualquer lugar no painel de hierarquia (o local no momento não importa), sob **objeto 3D**, adicione uma **texto 3D**. Denomine **LabelText**.

    ![Crie objeto de texto 3D.](images/AzureLabs-Lab2-21.png)
 
2.  No *painel de hierarquia*, clique com o botão esquerdo na **LabelText**. Com o **LabelText** selecionado, ajustar as seguintes variáveis na *painel Inspetor*:

    1. Defina as **posição** para **0, 0,0**
    2. Defina as **dimensionamento** para **0,01, 0,01, 0,01**
    3. No componente **texto de malha**:
    4. Substitua todo o texto dentro **texto**, com "..."        
    5. Defina as **âncora** para **parte intermediária central**
    6. Defina as **alinhamento** para **Center**
    7. Defina as **tamanho da tabulação** para **4**
    8. Defina as **Font Size** para **50**
    9. Defina as **cor** para **#FFFFFFFF**

    ![Componente de texto](images/AzureLabs-Lab2-21-5.png)

3.  Arraste o **LabelText** da *painel de hierarquia*, no *pasta ativo*, dentro no *painel do projeto*. Isso fará com que o **LabelText** um pré-fabricado, portanto, o que ele pode ser instanciado no código.

    ![Crie um pré-fabricado do objeto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  Você deve excluir o **LabelText** da *painel de hierarquia*, de modo que ele não será exibido na cena de abertura. Como é agora um pré-fabricado, o que será chamado para instâncias individuais da sua pasta de ativos, não é necessário para mantê-la dentro da cena. 
5.  A estrutura de objeto final na *painel de hierarquia* deve ser semelhante à mostrada na imagem abaixo:

    ![Estrutura final do painel de hierarquia.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Capítulo 5 – criar a classe ResultsLabel

É o primeiro script que você precisa criar o *ResultsLabel* classe, que é responsável pelo seguinte: 

- Criando os rótulos no espaço de mundo apropriado, em relação a posição da câmera.
- Exibindo as marcas do enorme de imagem.

Para criar essa classe: 

1.  Clique com botão direito no *painel do projeto*, em seguida, **criar > pasta**. Nomeie a pasta **Scripts**. 

    ![Crie a pasta de scripts.](images/AzureLabs-Lab2-24.png)

2.  Com o **Scripts** pasta criar, clique duas vezes nele para abrir. Em seguida, dentro dessa pasta, clique com botão direito e selecione **criar >** , em seguida,  **C# Script**. Nomeie o script *ResultsLabel*. 

3.  Clique duas vezes na nova *ResultsLabel* script para abri-lo com **Visual Studio**.

4.  Dentro da classe, insira o seguinte código na *ResultsLabel* classe:

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
7.  Na *Editor do Unity*, clique e arraste o *ResultsLabel* classe da **Scripts** pasta para o **câmera principal** objeto no  *Painel de hierarquia*.
8.  Clique no **câmera principal** e examine o *painel Inspetor*.

Você vai notar que o script que você acabou de arrastar para a câmera, há dois campos: **Cursor** e **rotular pré-fabricado**.

9.  Arraste o objeto chamado **Cursor** da *painel de hierarquia* para o slot chamado **Cursor**, conforme mostrado na imagem abaixo.
10. Arraste o objeto chamado **LabelText** da *pasta ativos* no *painel projeto* para o slot chamado **rótulo pré-fabricado**, conforme mostrado no imagem abaixo. 

    ![Defina as metas de referência dentro do Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Capítulo 6 – criar a classe ImageCapture

A próxima classe que você pretende criar é a *ImageCapture* classe. Essa classe é responsável por:

-   Capturar uma imagem usando a HoloLens câmera e armazená-lo na pasta do aplicativo.
-   Capturando os gestos de toque do usuário.

Para criar essa classe: 

1.  Vá para o **Scripts** pasta que você criou anteriormente. 
2.  Clique com botão direito dentro da pasta **criar > C# Script**. Chame o script *ImageCapture*. 
3.  Clique duas vezes na nova *ImageCapture* script para abri-lo com **Visual Studio**.
4.  Adicione os namespaces a seguir na parte superior do arquivo:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro de *ImageCapture* classe acima a *Start ()* método:

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
O **tapsCount** variável armazenará o número de gestos de toque capturados do usuário. Esse número é usado na nomeação das imagens capturadas.

6.  Código para o *Awake()* e *Start ()* métodos agora precisa ser adicionado. Eles serão chamados quando inicializa a classe:

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

7.  Implemente um manipulador que será chamado quando ocorre um gesto de tocar. 

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
 
O *TapHandler()* método incrementa o número de toques capturados do usuário e usa a posição do Cursor atual para determinar onde posicionar um novo rótulo.

Esse método, em seguida, chama o *ExecuteImageCaptureAndAnalysis()* método para iniciar a funcionalidade principal desse aplicativo.

8.  Depois que uma imagem foi capturada e armazenada, os seguintes manipuladores serão chamados. Se o processo for bem-sucedida, o resultado é passado para o *VisionManager* (que ainda estão criar) para análise.

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
> Neste ponto, você observará um erro que aparecem na *painel de Console do Editor do Unity*. Isso ocorre porque o código faz referência a *VisionManager* classe que você criará no próximo capítulo.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Capítulo 7 – chamada para o Azure e análise de imagem

É o último script que você precisa criar o *VisionManager* classe. 

Essa classe é responsável por:

-   Carregando a imagem mais recente capturada como uma matriz de bytes.
-   Enviando a matriz de bytes para seu *API de visão do computador Azure* instância de serviço para análise.
-   Recebendo a resposta como uma cadeia de caracteres JSON.
-   Ao desserializar a resposta e passando as marcas resultantes para o *ResultsLabel* classe.
 
Para criar essa classe:

1.  Clique duas vezes no **Scripts** pasta para abri-lo. 
2.  Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**. Nomeie o script *VisionManager*. 
3.  Clique duas vezes no novo script para abri-lo com o Visual Studio.
4.  Atualizar os namespaces para ser o mesmo que o seguinte, na parte superior do *VisionManager* classe:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  Na parte superior do seu script *dentro de* o *VisionManager* classe (acima a *Start ()* método), agora você precisa criar dois *Classes* que representa a resposta JSON desserializada do Azure:

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
    > O *TagData* e *AnalysedObject* classes precisam ter o *[System.Serializable]* atributo adicionado antes da declaração para poder ser desserializado com o Unity bibliotecas.

6.  Na classe VisionManager, você deve adicionar as seguintes variáveis:

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
    > Certifique-se de inserir sua **Auth Key** para o **authorizationKey** variável. Você será observou sua **Auth Key** no início deste curso [capítulo 1](#chapter-1--the-azure-portal).

    > [!WARNING] 
    > O **visionAnalysisEndpoint** variável pode ser diferente do especificado neste exemplo. O **west-us** estritamente refere-se a instâncias de serviço criadas para a região Oeste dos EUA. Atualize-o com seu [URL de ponto de extremidade](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); aqui estão alguns exemplos do que podem parecer com:
    > - Europa Ocidental: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Sudeste da Ásia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Leste da Austrália: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Agora o código para Awake precisa ser adicionado. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  Em seguida, adicione a corrotina (com o fluxo estático método abaixo dele), que irá obter os resultados da análise da imagem capturada pelo *ImageCapture* classe. 

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
10. No Editor do Unity, clique em Voltar e arraste o *VisionManager* e *ImageCapture* as classes do **Scripts** pasta para o **câmera principal**objeto de *painel de hierarquia*. 

## <a name="chapter-8--before-building"></a>Capítulo 8 – antes da construção

Para executar um teste completo de seu aplicativo você precisará para fazer sideload dele para o HoloLens.
Antes de começar, verifique se:

-   Todas as configurações mencionadas [capítulo 2](#chapter-2--set-up-the-unity-project) estão definidas corretamente. 
-   Todos os scripts são anexados para o **câmera principal** objeto. 
-   Todos os campos a *painel de Inspetor de câmera principal* são atribuídas corretamente.
-   Certifique-se de inserir sua **Auth Key** para o **authorizationKey** variável.
-   Certifique-se de que você também verificou o ponto de extremidade seu *VisionManager* script e ele se alinhe com *sua* região (Este documento usa *Oeste-nos* por padrão).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Capítulo 9 – compilar a solução de UWP e carregar o aplicativo
Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído, portanto, é hora de criá-lo do Unity.

1.  Navegue até *configurações de Build* - **arquivo > configurações de Build...**
2.  Dos *configurações de Build* janela, clique em **Build**.

    ![Compilando o aplicativo do Unity](images/AzureLabs-Lab2-26.png)

3.  Se ainda não estiver, marque **Unity C# projetos**.
4.  Clique em **Compilar**. Unity iniciará uma *Explorador de arquivos* janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em. Criar pasta agora e nomeie- *aplicativo*. Em seguida, com o *App* pasta selecionada, pressione **Selecionar pasta**. 
5.  Unity começará a compilar seu projeto para o *aplicativo* pasta. 
6.  Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um *Explorador de arquivos* janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).

## <a name="chapter-10--deploy-to-hololens"></a>Capítulo 10 – implantar ao HoloLens

Para implantar o HoloLens:

1.  Será necessário o endereço IP do seu HoloLens (para a implantação remota) e garantir que seu HoloLens está em **modo de desenvolvedor**. Para fazer isso:

    1. Durante o uso de seu HoloLens, abra o **configurações**.
    2. Vá para **rede e Internet > Wi-Fi > Opções avançadas**
    3. Observe a **IPv4** endereço.
    4. Em seguida, navegue até **as configurações**e, em seguida, para **atualização e segurança > para desenvolvedores** 
    5. Definir o modo de desenvolvedor em.

2.  Navegue até seu novo build do Unity (o *App* pasta) e abra o arquivo de solução com *Visual Studio*.
3.  No, selecione a configuração da solução **depurar**.
4.  Na plataforma da solução, selecione **x86**, **máquina remota**. 

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  Vá para o **menu Build** e clique em **implantar solução**, carregar o aplicativo para o HoloLens.
6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!

> [!NOTE]
> Para implantar o fone de ouvido imersivo, defina as **plataforma da solução** para *Máquina Local*e defina o **configuração** para *depurar*, com *x86* como o **plataforma**. Em seguida, implantar no local de máquina, usando o **menu Build**, selecionando *implantar solução*. 

## <a name="your-finished-computer-vision-api-application"></a>O aplicativo de API de visão do computador concluído

Parabéns, você criou um aplicativo de realidade mista que aproveita a API de visão do computador do Azure para reconhecer os objetos do mundo real e, em seguida, exibir a confiança de que foi visto.

![resultado de laboratório](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Assim como você usou o *marcas* parâmetro (conforme evidenciado dentro a *ponto de extremidade* usados dentro a *VisionManager*), estenda o aplicativo para detectar outras informações; dar uma olhada quais outros parâmetros que você tem acesso ao [aqui](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).

### <a name="exercise-2"></a>Exercício 2

Exiba os dados retornados do Azure, de forma mais conversacional e legível, talvez ocultando os números. Como se pode estar falando um bot para o usuário.
