---
title: MR e 302b do Azure - visão personalizada
description: Conclua este curso para aprender a treinar um modelo de aprendizado de máquina e, em seguida, use o modelo treinado para reconhecer objetos semelhantes dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, visão personalizada, hololens, imersivo, vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589572"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>MR e 302b do Azure: Visão personalizada

Neste curso, você aprenderá a reconhecer conteúdo visual personalizado em uma imagem fornecido, usando recursos de visão personalizada do Azure em um aplicativo de realidade misturada.

Esse serviço permitirá que você treinar um modelo de aprendizado de máquina usando imagens de objeto. Em seguida, usará o modelo treinado para reconhecer objetos semelhantes, conforme fornecido pela captura de câmera do Microsoft HoloLens ou de uma câmera conectada ao seu PC para fones imersivos em exposição (VR).

![resultado do curso](images/AzureLabs-Lab302b-00.png)

Visão personalizada do Azure é um serviço cognitivo da Microsoft que permite aos desenvolvedores criar classificadores de imagem personalizada. Os classificadores, em seguida, podem ser usados com novas imagens para reconhecer ou classificam objetos em se a nova imagem. O serviço fornece um portal simple, fácil de usar on-line para simplificar o processo. Para obter mais informações, visite o [página do serviço de visão personalizada do Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).

Após a conclusão deste curso, você terá um aplicativo de realidade mista que será capaz de trabalhar em dois modos:

-   **Modo de análise**: configurar o serviço personalizado de visão manualmente por carregar imagens, criação de marcas e o serviço de treinamento para reconhecer a diferentes objetos (nesse caso do mouse e teclado). Em seguida, você irá criar um aplicativo do HoloLens que capturar imagens usando a câmera e tente reconhecer esses objetos no mundo real.

-   **Modo de treinamento**: você implementará o código que permitirá que um "modo de treinamento" em seu aplicativo. O modo de treinamento permitirá que você capturar imagens usando a câmera dos HoloLens, carregar as imagens capturadas para o serviço e treinar o modelo de visão personalizada.

Este curso ensinará você a obter os resultados com o serviço de visão personalizada em um aplicativo de exemplo com base no Unity. Ele será cabe a você aplicar esses conceitos para um aplicativo personalizado que você pode criar.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> MR e 302b do Azure: Visão personalizada</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Enquanto este curso se concentra principalmente em HoloLens, você também pode aplicar o que você aprenderá neste curso para fones de ouvido Windows Mixed Reality de imersão (VR). Como fones imersivos em exposição (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu computador. Como acompanhar o curso, você verá notas quaisquer alterações que você talvez precise ser empregadas para dar suporte a fones imersivos em exposição (VR).

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#. Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (julho de 2018). Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que está listado abaixo.

Recomendamos que o hardware e software para este curso a seguir:

- Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md#installation-checklist)
- [O SDK mais recente do Windows 10](install-the-tools.md#installation-checklist)
- [2017.4 do Unity](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado
- Uma câmera conectada ao seu PC (para desenvolvimento imersivo fone de ouvido)
- Acesso à Internet para a instalação do Azure e a recuperação de API de visão personalizada
- Uma série de pelo menos cinco (5) imagens (dez (10) recomendado) para cada objeto que você gostaria que o serviço personalizado de visão para reconhecer. Se desejar, você pode usar [as imagens que já é fornecidas com este curso (um mouse do computador e um teclado) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).
2.  Configurar e testar o HoloLens. Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  É uma boa ideia executar calibragem e ajuste de Sensor ao começar a desenvolver um novo aplicativo HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).

Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-service-portal"></a>Capítulo 1 - Portal do serviço de visão personalizada

Para usar o *serviço de visão personalizada* no Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo.

1.  Primeiro, [navegue até a *serviço personalizado de visão* página principal](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Clique no **começar** botão.

    ![](images/AzureLabs-Lab302b-01.png)

3.  Entrar para o *serviço personalizado de visão* Portal.

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, você precisará criá-lo. Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.

4.  Quando você estiver conectado pela primeira vez, você será solicitado com o *termos de serviço* painel. Clique na caixa de seleção para aceitar os termos. Em seguida, clique em **concordo**.

    ![](images/AzureLabs-Lab302b-03.png)

5.  Tendo concordou com os termos, você será direcionado para o *projetos* seção do Portal. Clique em **novo projeto**.

    ![](images/AzureLabs-Lab302b-04.png)

6.  Uma guia aparecerá no lado direito, que solicitará que você especifique alguns campos para o projeto.

    1.  Inserir uma *nome* para seu projeto.

    2.  Inserir uma *descrição* para seu projeto (*opcional*).

    3.  Escolha uma *grupo de recursos* ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).

    4. Defina as *tipos de projeto* para **classificação**
    
    5. Defina as *domínios* como **geral**.

        ![](images/AzureLabs-Lab302b-05.png)

        > Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

7.  Quando tiver terminado, clique em **criar projeto**, você será redirecionado para o serviço personalizado de visão, página do projeto.

## <a name="chapter-2---training-your-custom-vision-project"></a>Capítulo 2 - treinamento de seu projeto de visão personalizada

Uma vez no portal de visão personalizada, seu principal objetivo é treinar seu projeto para reconhecer a objetos específicos em imagens. Você precisa de pelo menos cinco (5) imagens, embora dez (10) é preferível, para cada objeto que você deseja que seu aplicativo reconheça. [Você pode usar as imagens fornecidas com este curso (um mouse do computador e um teclado)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip). 

Para treinar seu projeto de serviço de visão personalizada:

1.  Clique no **+** lado **marcas.**

    ![](images/AzureLabs-Lab302b-06.png)

2.  Adicione a **nome** do objeto que você gostaria de reconhecer. Clique em **salvar**.

    ![](images/AzureLabs-Lab302b-07.png)

3.  Você notará sua **marca** foi adicionado (talvez seja necessário recarregar a página para que ele seja exibido). Clique na caixa de seleção junto com sua nova marca, se já não estiver marcada.

    ![](images/AzureLabs-Lab302b-08.png)

4.  Clique em **adicionar imagens** no centro da página.

    ![](images/AzureLabs-Lab302b-09.png)

5.  Clique em **procurar arquivos locais**, pesquise e selecione as imagens que você gostaria de carregar, com o mínimo sendo cinco (5). Lembre-se de que todas essas imagens devem conter o objeto que você está ensinando.

    > [!NOTE]
    >  Você pode selecionar várias imagens por vez, para carregar.

6.  Depois que você pode ver as imagens na guia, selecione a marca apropriada na **minhas marcas** caixa.

    ![](images/AzureLabs-Lab302b-10.png)

7.  Clique em **carregar arquivos**. Os arquivos de começar a carregar. Depois que você tiver a confirmação do upload, clique em **feito**.

    ![](images/AzureLabs-Lab302b-11.png)

8.  Repita o mesmo processo para criar um novo **marca** denominado **teclado** e carregar as fotos apropriadas para ele. Certifique-se **desmarcar** *Mouse* depois de criar as novas marcas, portanto, para mostrar os *adicionar imagens* janela.

9.  Uma vez que ambas as marcas, configuradas, clique em **Train**, e a primeira iteração de treinamento iniciará a compilação.

    ![](images/AzureLabs-Lab302b-12.png)

10. Depois que ele é criado, você poderá ver dois botões chamados **tornar padrão** e **URL de previsão**. Clique em **tornar padrão** pela primeira vez, em seguida, clique em **URL de previsão**.

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > A URL de ponto de extremidade que é fornecida a partir disso, é definido como o que ocorrer *iteração* foi marcada como padrão. Como tal, se você fizer um novo mais tarde *iteração* e atualizá-lo como padrão, você não precisará alterar seu código.

11. Depois de clicar em *URL de previsão*, abra *bloco de notas*e copie e cole o **URL** e o **chave previsão**, de modo que você pode recuperá-la quando precisar dele posteriormente no código.

    ![](images/AzureLabs-Lab302b-14.png)

12. Clique no **engrenagem** na parte superior direita da tela.

    ![](images/AzureLabs-Lab302b-15.png)

13. Cópia a **chave de treinamento** e cole-o em um *o bloco de notas*, para uso posterior.

    ![](images/AzureLabs-Lab302b-16.png)

14. Também copiar sua **Id do projeto**e também colá-lo em seu *bloco de notas* arquivo para uso posterior.

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3 - configurar o projeto do Unity

A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.

1.  Abra *Unity* e clique em **New**.

    ![](images/AzureLabs-Lab302b-17.png)

2.  Agora, você precisará fornecer um nome de projeto do Unity. Inserir **AzureCustomVision.** Verifique se o modelo de projeto é definido como **3D**. Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![](images/AzureLabs-Lab302b-18.png)

3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Vá para **edite* > *preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

    ![](images/AzureLabs-Lab302b-19.png)

4.  Em seguida, vá para **arquivo > configurações de Build** e selecione **plataforma Universal do Windows**, em seguida, clique no **alternar plataforma** botão Aplicar sua seleção.

    ![](images/AzureLabs-Lab302b-20.png)

5.  Enquanto estiver na **arquivo > configurações de Build** e certifique-se de que:

    1.  **Dispositivo de destino** é definido como **Hololens**

        > Para os fones imersivos em exposição, defina **dispositivo de destino** à *qualquer dispositivo*.
        
    2.  **Tipo de compilação** é definido como **D3D**
    3.  **SDK** é definido como **mais recente instalada**
    4.  **Versão do Visual Studio** é definido como **mais recente instalada**
    5.  **Compilar e executar** é definido como **Máquina Local**
    6.  Salve a cena e adicioná-lo para a compilação. 

        1. Fazer isso selecionando **cenas abra Adicionar**. Salvamento janela será exibida.

            ![](images/AzureLabs-Lab302b-21.png)

        2. Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.

            ![](images/AzureLabs-Lab302b-22.png)

        3. Abrir seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo:* campo de texto, digite **CustomVisionScene**, em seguida, clique em **salvar**.

            ![](images/AzureLabs-Lab302b-23.png)

            > Esteja ciente de que você deve salvar suas cenas de Unity dentro do *ativos* pasta, pois eles devem estar associados ao projeto do Unity. Criando a pasta de cenas (e outras pastas semelhantes) é uma maneira comum de estruturar um projeto do Unity.
            
    7.  O restante de configurações, em *configurações de Build*, deverá ser deixado como padrão por enquanto.

        ![](images/AzureLabs-Lab302b-24.png)

6.  No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado.

7. Neste painel, algumas configurações precisam ser verificados:

    1.  No **outras configurações** guia:

        1.  **Versão de tempo de execução de scripts** deve ser **Experimental (equivalente ao .NET 4.6)**, que irá disparar uma necessidade de reiniciar o Editor.

        2. **Script de back-end** deve ser **.NET**

        3. **Nível de compatibilidade de API** deve ser **.NET 4.6**

        ![](images/AzureLabs-Lab302b-25.png)

    2.  Dentro de **configurações de publicação** guia, em **recursos**, verifique:

        1. **InternetClient**

        2.  **Webcam**

        3. **Microfone**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.

    ![](images/AzureLabs-Lab302b-27.png)

8.  Volta *configurações de Build* *Unity C\# projetos* não fica acinzentado; marque a caixa de seleção ao lado disso.

9.  Feche a janela de configurações de Build.

10.  Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Capítulo 4 - importação de DLL Newtonsoft no Unity

> [!IMPORTANT]
> Se você quiser ignorar a *Unity configurar* componente deste curso e continuar diretamente no código, fique à vontade para baixá-lo [MR-Azure-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 6](#chapter-6---create-the-customvisionanalyser-class).

Este curso requer o uso do **Newtonsoft** biblioteca, que pode ser adicionado como uma DLL para seus ativos. O pacote que contém [essa biblioteca pode ser baixada deste link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).
Para importar a biblioteca Newtonsoft para seu projeto, use o pacote do Unity que acompanha este curso.

1.  Adicionar o *unitypackage* para o Unity, usando o **ativos* > *importação* *pacote*  >  *Personalizada* *pacote** opção de menu.

2.  No **Importar pacote do Unity** caixa é exibido para cima, certifique-se de tudo em (e incluindo) **plug-ins** está selecionado.

    ![](images/AzureLabs-Lab302b-28.png)

3.  Clique o **importação** botão para adicionar itens ao seu projeto.

4.  Vá para o **Newtonsoft** pasta sob **plug-ins** na exibição do projeto e selecione o *plug-in do newtonsoft. JSON*.

    ![](images/AzureLabs-Lab302b-29.png)

5.  Com o *plug-in do newtonsoft. JSON* selecionado, certifique-se de que **Any Platform** é **desmarcada**, em seguida, certifique-se de que **WSAPlayer** também é **desmarcada**, em seguida, clique em **aplicar**. Isso é apenas para confirmar que os arquivos estão configurados corretamente.

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Marcar esses plug-ins configura para ser usado apenas no Editor do Unity. Há um conjunto diferente de-los na pasta do WSA que será usado depois que o projeto é exportado do Unity.

6.  Em seguida, você precisa abrir o **WSA** pasta, dentro de **Newtonsoft** pasta. Você verá uma cópia do mesmo arquivo que você acabou de configurar. Selecione o arquivo e, em seguida, no Inspetor de, certifique-se de que
    -   **Qualquer plataforma** é **desmarcada** 
    -   **somente** **WSAPlayer** é **marcada**
    -   **Não processar** é **marcada**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Capítulo 5 – instalação da câmera

1.  No painel de hierarquia, selecione a *câmera principal*.

2.  Depois de selecionado, você poderá ver todos os componentes do *câmera principal* na *painel Inspetor*.

    1.  O *câmera* objeto deve ser nomeado **câmera principal** (Observe a ortografia!)

    2.  A câmera principal **marca** deve ser definida como **MainCamera** (Observe a ortografia!)

    3.  Verifique se o **transformar posição** é definido como **0, 0, 0**

    4.  Definir **Limpar sinalizadores** à **cor sólida** (Ignorar para fone de ouvido imersivo).

    5.  Defina a **em segundo plano** cor da câmera componente **preto, alfa 0 (código hexadecimal: #00000000)** (Ignorar para fone de ouvido imersivo).

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Capítulo 6 - criar a classe CustomVisionAnalyser.

Neste ponto, você está pronto para escrever um código.

Você começará com o *CustomVisionAnalyser* classe.

> [!NOTE]
> As chamadas para o **serviço personalizado de visão** feitas no código mostrado a seguir são feitas usando o **API de REST de visão personalizada**. Usando isso, você verá como implementar e usar essa API (útil para entender como implementar algo semelhante em seu próprio). Lembre-se que a Microsoft oferece uma **SDK do serviço de visão personalizada** que também pode ser usado para fazer chamadas para o serviço. Para obter mais informações, visite o [SDK do serviço de visão personalizada](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) artigo.

Essa classe é responsável por:

-   Carregando a imagem mais recente capturada como uma matriz de bytes.

-   Enviando a matriz de bytes para o Azure *serviço de visão personalizada* instância para análise.

-   Recebendo a resposta como uma cadeia de caracteres JSON.

-   Ao desserializar a resposta e passando resultante *previsão* para o *SceneOrganiser* classe, que se encarregará de como a resposta deve ser exibida.

Para criar essa classe:

1.  Com o botão direito no *pasta ativo* localizado na *painel projeto*, em seguida, clique em **criar > pasta**. Chame a pasta **Scripts**.

    ![](images/AzureLabs-Lab302b-33.png)

2.  Clique duas vezes na pasta recém-criada, para abri-lo.

3.  Clique com botão direito dentro da pasta e clique em **Create** > **C\# Script**. Nomeie o script *CustomVisionAnalyser*.

4.  Clique duas vezes na nova *CustomVisionAnalyser* script para abri-lo com **Visual Studio**.

5.  Atualize os namespaces na parte superior do seu arquivo para corresponder ao seguinte:

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  No *CustomVisionAnalyser* de classe, adicione as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Certifique-se de inserir sua **chave de previsão** na **predictionKey** variável e seu **ponto de extremidade de previsão** no **predictionEndpoint** variável. Você copiou para *bloco de notas* anteriormente no curso.

7.  Código para o **Awake()** agora precisa ser adicionada para inicializar a variável de instância:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Excluir os métodos **Start ()** e **Update ()**.

9.  Em seguida, adicione a corrotina (com a estática **GetImageAsByteArray()** método abaixo dele), que irá obter os resultados da análise da imagem capturada pelo *ImageCapture* classe.

    > [!NOTE]
    > No **AnalyseImageCapture** corrotina, há uma chamada para o *SceneOrganiser* classe que você ainda está a criar. Portanto, **deixar as linhas comentadas agora**.

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Capítulo 7 - criar a classe CustomVisionObjects

A classe que você criará agora é o *CustomVisionObjects* classe.

Esse script contém um número de objetos usados por outras classes para serializar e desserializar as chamadas feitas para o *serviço de visão personalizada*.

> [!WARNING]
> É importante que você tome nota do ponto de extremidade que o serviço de visão personalizada fornece a você, como o JSON abaixo estrutura foi configurada para trabalhar com [ *previsão de visão personalizado v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290). Se você tiver uma versão diferente, talvez você precise atualizar o abaixo da estrutura.

Para criar essa classe:

1.  Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**. Chame o script *CustomVisionObjects*.

2.  Clique duas vezes na nova **CustomVisionObjects** script para abri-lo com **Visual Studio**.

3.  Adicione os namespaces a seguir na parte superior do arquivo:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Excluir o **Start ()** e **Update ()** métodos dentro de *CustomVisionObjects* classe; essa classe agora deve estar vazia.

5.  Adicione as seguintes classes **fora** as *CustomVisionObjects* classe. Esses objetos são usados pelos *Newtonsoft* biblioteca para serializar e desserializar os dados de resposta:

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Capítulo 8 - criar a classe VoiceRecognizer

Essa classe reconhecerá a entrada de voz do usuário.

Para criar essa classe:

1.  Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**. Chame o script *VoiceRecognizer*.

2.  Clique duas vezes na nova **VoiceRecognizer** script para abri-lo com **Visual Studio**.

3.  Adicione os seguintes namespaces acima de *VoiceRecognizer* classe:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  Em seguida, adicione as seguintes variáveis dentro de *VoiceRecognizer* classe acima a *Start ()* método:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  Adicione a **Awake()** e **Start ()** métodos, o último será definido pelo usuário *palavras-chave* para serem reconhecidos quando a associação de uma marca para uma imagem:

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  Excluir o **Update ()** método.

7.  Adicione o seguinte manipulador, que é chamado sempre que a entrada de voz é reconhecida:

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.

> [!NOTE]
> Não se preocupe sobre código que pode aparecer ter um erro, pois você fornecerá em breve, as classes adicionais que corrigi-los.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Capítulo 9 - criar a classe CustomVisionTrainer

Essa classe será encadear uma série de chamadas de web para treinar o *serviço de visão personalizada*. Cada chamada será explicada em detalhes logo acima do código.

Para criar essa classe:

1.  Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**. Chame o script *CustomVisionTrainer*.

2.  Clique duas vezes na nova *CustomVisionTrainer* script para abri-lo com **Visual Studio**.

3.  Adicione os seguintes namespaces acima de *CustomVisionTrainer* classe:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Em seguida, adicione as seguintes variáveis dentro de *CustomVisionTrainer* classe acima a **Start ()** método. 

    > [!NOTE]
    > A URL de treinamento usada aqui é fornecida dentro de *1.2 de treinamento de visão personalizada* documentação, e tem uma estrutura de: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Para obter mais informações, visite o [ *API de referência do treinamento de visão personalizada v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).

    > [!WARNING]
    > É importante que você tome nota do ponto de extremidade que o serviço de visão personalizada fornece para o modo de treinamento, como a estrutura do JSON usada (dentro de **CustomVisionObjects** classe) foi configurado para trabalhar com [  *Personalizado de visão treinamento v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f). Se você tiver uma versão diferente, talvez você precise atualizar o *objetos* estrutura.

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > Certifique-se de que você adicione sua **chave de serviço** valor (chave de treinamento) e **Id do projeto** valor, o que você anotou anterior; esses são os valores você [coletados a partir do portal no início do curso ( Capítulo 2, etapa 10 em diante)](#chapter-2---training-your-custom-vision-oroject).

5.  Adicione o seguinte **Start ()** e **Awake()** métodos. Esses métodos são chamados na inicialização e contenham a chamada para definir a interface do usuário:

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  Excluir o **Update ()** método. Essa classe não precisará dela.

7.  Adicione a **RequestTagSelection()** método. Esse método é o primeiro a ser chamado quando uma imagem foi capturada e armazenada no dispositivo e agora está pronto para ser enviado para o *serviço de visão personalizada*, treiná-lo. Esse método exibe no treinamento de interface do usuário, um conjunto de palavras-chave, que o usuário pode usar para marcar a imagem que foi capturada. Ele também alerta o *VoiceRecognizer* classe para começar a escutar ao usuário para entrada de voz.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Adicione a **VerifyTag()** método. Esse método receberá a entrada de voz reconhecida pelo **VoiceRecognizer** de classe e verificar sua validade e, em seguida, iniciar o processo de treinamento.

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  Adicione a **SubmitImageForTraining()** método. Esse método iniciará o processo de treinamento do serviço de visão personalizada. A primeira etapa é recuperar o **Id de marca** do serviço que está associado com a entrada de fala validado do usuário. O **Id de marca** , em seguida, será carregado junto com a imagem.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. Adicione a **TrainCustomVisionProject()** método. Depois que a imagem foi enviada e marcada, esse método será chamado. Ele criará uma nova iteração será preparada com todas as imagens anteriores enviadas ao serviço mais a imagem acabou de carregar. Depois que o treinamento for concluído, esse método chamará um método para definir o recém-criado **iteração** como **padrão**, de modo que o ponto de extremidade que você está usando para análise é a iteração mais recente treinada.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. Adicione a **SetDefaultIteration()** método. Esse método definirá a iteração anteriormente criada e treinada como *padrão*. Depois de concluído, esse método será preciso excluir iteração anterior existente no serviço. No momento da redação deste curso, há um limite de um máximo 10 (dez) iterações podem existir ao mesmo tempo em que o serviço.

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. Adicione a **DeletePreviousIteration()** método. Esse método irá localizar e excluir iteração anterior não padrão:

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. O último método para adicionar essa classe é o **GetImageAsByteArray()** método, usado em chamadas de web para converter a imagem capturada em uma matriz de bytes.

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Capítulo 10 - criar a classe SceneOrganiser

Essa classe será:

-   Criar uma **Cursor** objeto a ser anexado à câmera principal.

-   Criar uma **rótulo** objeto que será exibido quando o serviço reconhece os objetos do mundo real.

-   Configure a câmera principal, anexando os componentes apropriados para ele.

-   Quando estiver sendo **modo de análise**, gerar os rótulos em tempo de execução, no espaço de mundo apropriado em relação a posição da câmera principal e exibir os dados recebidos do serviço personalizado de visão.

-   Quando estiver sendo **modo de treinamento**, gerar a interface do usuário que exibirá os diferentes estágios do processo de treinamento.

Para criar essa classe:

1.  Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**. Nomeie o script *SceneOrganiser*.

2.  Clique duas vezes na nova *SceneOrganiser* script para abri-lo com **Visual Studio**.

3.  Só é necessário um namespace, remova as outras acima de *SceneOrganiser* classe:

    ```csharp
    using UnityEngine;
    ```

4.  Em seguida, adicione as seguintes variáveis dentro de *SceneOrganiser* classe acima a **Start ()** método:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  Excluir o **Start ()** e **Update ()** métodos.

6.  Logo abaixo das variáveis, adicione a **Awake()** método, que irá inicializar a classe e configure a cena.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  Agora, adicione a **CreateCameraCursor()** método que cria e posiciona o cursor de câmera principal, e o **CreateLabel()** método, que cria o **rótulo de análises** objeto .

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. Adicione a **SetCameraStatus()** método que manipulará as mensagens destinadas a malha de texto, fornecendo o status da câmera.

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. Adicione a **PlaceAnalysisLabel()** e **SetTagsToLastLabel()** métodos, que irá gerar e exibir os dados do serviço personalizado de visão na cena.

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. Por fim, adicione a **CreateTrainingUI()** método, que irá gerar a interface do usuário exibindo os vários estágios do processo de treinamento quando o aplicativo está no modo de treinamento. Esse método também será ser usado para criar o objeto de status de câmera.

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.

> [!IMPORTANT]
> Antes de continuar, abra o **CustomVisionAnalyser** classe e dentro de **AnalyseLastImageCaptured()** método, *Descomente* as seguintes linhas:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Capítulo 11 - criar a classe ImageCapture

A próxima classe que você pretende criar é a *ImageCapture* classe.

Essa classe é responsável por:

-   Capturar uma imagem usando a câmera HoloLens e armazená-los de *aplicativo* pasta.

-   Tratamento de gestos de toque do usuário.

-   Mantendo os *Enum* valor que determina se o aplicativo será executado no *Analysis* modo ou *treinamento* modo.

Para criar essa classe:

1.  Vá para o **Scripts** pasta que você criou anteriormente.

2.  Clique com botão direito dentro da pasta e clique em **criar > C\# Script**. Nomeie o script *ImageCapture*.

3.  Clique duas vezes na nova **ImageCapture** script para abri-lo com **Visual Studio**.

4.  Substitua os namespaces na parte superior do arquivo pelo seguinte:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro de *ImageCapture* classe acima a **Start ()** método:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  Código para o **Awake()** e **Start ()** métodos agora precisa ser adicionado:

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  Implemente um manipulador que será chamado quando ocorre um gesto de tocar.

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > Na *Analysis* modo, o **TapHandler** método atua como uma opção para iniciar ou parar o loop de captura de fotos.
    >
    > Na *treinamento* modo, ele irá capturar uma imagem da câmera.
    >
    > Quando o cursor estiver verde, significa que a câmera está disponível para capturar a imagem.
    >
    > Quando o cursor está vermelho, significa que a câmera está ocupada.

8.  Adicione o método que o aplicativo usa para iniciar o processo de captura de imagem e armazenar a imagem.

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  Adicione os manipuladores que serão chamados quando a foto tiver sido capturada e para quando ele estiver pronto para ser analisado. O resultado é então passado para o *CustomVisionAnalyser* ou o *CustomVisionTrainer* dependendo de qual modo o código é definido no.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.

11. Agora que todos os scripts tiverem sido concluídos, volte no Editor do Unity, em seguida, clique e arraste a **SceneOrganiser** classe a **Scripts** pasta para o **câmera principal** objeto de *painel de hierarquia*.

## <a name="chapter-12---before-building"></a>Capítulo 12 - antes de compilar

Para executar um teste completo de seu aplicativo você precisará para fazer sideload dele para o HoloLens.

Antes de começar, verifique se:

- Todas as configurações mencionadas a [capítulo 2](#chapter-2---training-your-custom-vision-project) estão definidas corretamente.

- Todos os campos a **câmera principal**, painel de Inspetor, são atribuídas corretamente.

- O script **SceneOrganiser** está associada a **câmera principal** objeto.

- Certifique-se de inserir sua **chave de previsão** para o **predictionKey** variável.

- Você inseriu sua **ponto de extremidade de previsão** para o **predictionEndpoint** variável.

- Você inseriu sua **chave de treinamento** na **trainingKey** variável, da *CustomVisionTrainer* classe.

- Você inseriu seu **ID do projeto** para o **projectId** variável da *CustomVisionTrainer* classe.

## <a name="chapter-13---build-and-sideload-your-application"></a>Capítulo 13 - Build e carregar seu aplicativo

Para iniciar o *Build* processo:

1.  Vá para **arquivo > configurações de Build**.

2.  Escala **Unity C\# projetos**.

3.  Clique em **Compilar**. Unity iniciará uma **Explorador de arquivos** janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em. Criar pasta agora e nomeie- **aplicativo**. Em seguida, com o **App** pasta selecionada, clique em **Selecionar pasta**.

4.  Unity começará a compilar seu projeto para o **aplicativo** pasta.

5.  Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um **Explorador de arquivos** janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).

Para implantar o HoloLens:

1.  Será necessário o endereço IP do seu HoloLens (para a implantação remota) e garantir que seu HoloLens está em **modo de desenvolvedor**. Para fazer isso:

    1.  Durante o uso de seu HoloLens, abra o **configurações**.

    2.  Vá para **rede e Internet** > **Wi-Fi** > **opções avançadas**

    3.  Observe a **IPv4** endereço.

    4.  Em seguida, navegue até **as configurações**e, em seguida, para **atualização e segurança** > **para desenvolvedores**

    5.  Definir **modo de desenvolvedor no**.

2.  Navegue até seu novo build do Unity (o **App** pasta) e abra o arquivo de solução com **Visual Studio**.

3.  No *configuração da solução* selecionar **depurar**.

4.  No *plataforma da solução*, selecione **x86, computador remoto**. Você será solicitado a inserir o **endereço IP** de um dispositivo remoto (o HoloLens, nesse caso, que você anotou).

    ![](images/AzureLabs-Lab302b-34.png)

5. Vá para **construir** menu e clique em **implantar solução** para carregar o aplicativo para o HoloLens.

6. Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!

> [!NOTE]
> Para implantar o fone de ouvido imersivo, defina as **plataforma da solução** para *Máquina Local*e defina o **configuração** para *depurar*, com *x86* como o **plataforma**. Em seguida, implantar no local de máquina, usando o **compilar** item de menu, selecionando *implantar solução*. 

## <a name="to-use-the-application"></a>Para usar o aplicativo:

Para alternar entre a funcionalidade do aplicativo *treinamento* modo e *previsão* modo, você precisa atualizar o **AppMode** variável, localizado no **Awake()** método localizado dentro de *ImageCapture* classe.

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
ou
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

Na *treinamento* modo:

- Examinar **Mouse** ou **teclado** e use o **gesto de toque**.

- Em seguida, o texto será exibida solicitando que você forneça uma marca.

- Indicar **Mouse** ou **teclado**.


Na *previsão* modo:

- Examinar o objeto e usar o **gesto de toque**.

- Texto será exibido, fornecendo o objeto detectado, com a probabilidade mais alta (Isso é normalizado).

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Capítulo 14 - avaliar e melhorar seu modelo de visão personalizada

Para fazer com que seu serviço mais precisos, você precisará continuar treinar o modelo usado para previsão. Isso é feito por meio de seu novo aplicativo, com ambos os *treinamento* e *previsão* modos, com o último exigir que você visite o portal, que é o que é abordado neste capítulo. Prepare-se de rever seu portal muitas vezes, para melhorar continuamente seu modelo.

1. Vá até o Portal do Azure personalizado visão novamente e quando estiver em seu projeto, selecione a *previsões* guia (da parte superior central da página):

    ![](images/AzureLabs-Lab302b-35.png)

2. Você verá todas as imagens que foram enviadas ao seu serviço, enquanto seu aplicativo estava em execução. Se você passar o mouse sobre as imagens, eles lhe fornecerá as previsões que foram feitas para essa imagem:

    ![](images/AzureLabs-Lab302b-36.png)

3. Selecione uma das suas imagens para abri-lo. Depois de aberto, você verá as previsões feitas dessa imagem à direita. Se você as previsões corretas, e você deseja adicionar essa imagem ao modelo de treinamento do seu serviço, clique o *minhas marcas* caixa de entrada e, em seguida, selecione a marca que você deseja associar. Quando tiver terminado, clique no *salvar e fechar* botão na parte inferior direita e prosseguir para a próxima imagem.

    ![](images/AzureLabs-Lab302b-37.png)

4. Uma vez para a grade de imagens, você observará que as imagens que você tiver adicionado marcas para (e salvo), serão removidos. Se você encontrar todas as imagens que você acha que não têm seu item marcado dentro deles, você pode excluí-los, clicando o tique nessa imagem (pode fazer isso para várias imagens) e, em seguida, clicando em *excluir* no canto superior direito da página da grade. Sobre o pop-up que segue, você pode clicar *Sim, exclua* ou *não*, para confirmar a exclusão ou cancelá-la, respectivamente. 

    ![](images/AzureLabs-Lab302b-38.png)

5. Quando você estiver pronto para continuar, clique em verde *Train* botão no canto superior direito. O modelo de serviço será ser treinado com todas as imagens que você forneceu agora (que tornam mais precisos). Quando o treinamento estiver concluído, certifique-se de clicar o *tornar padrão* botão mais uma vez, para que seu *URL de previsão* continua a usar a iteração mais atualizada de seu serviço.

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>O aplicativo de API de visão personalizada concluído

Parabéns, você criou um aplicativo de realidade mista que aproveita a API de visão personalizada do Azure para reconhecer os objetos do mundo real, treinar o modelo de serviço e, em seguida, exibir a confiança de que foi visto.

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Treinar sua **serviço de visão personalizada** a reconhecer mais objetos.

### <a name="exercise-2"></a>Exercício 2

Como uma maneira para expandir o que você aprendeu, conclua os seguintes exercícios:

Tocar um som quando um objeto é reconhecido.

### <a name="exercise-3"></a>Exercício 3

Usar a API para treinar novamente seu serviço com as mesmas imagens de análise de seu aplicativo, portanto, para tornar o serviço mais precisos (fazer a previsão e o treinamento simultaneamente).
