---
title: MR e Azure 310 - detecção de objetos
description: Conclua este curso para aprender a treinar um modelo de aprendizado de máquina e, em seguida, use o modelo treinado para reconhecer objetos semelhantes e sua posição no mundo real de dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, visão personalizada, detecção, misto realidade, academy, unity, tutorial, api, hololens do objeto
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589102"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

# <a name="mr-and-azure-310-object-detection"></a>MR e o Azure 310: Detecção de objetos

Neste curso, você aprenderá a reconhecer conteúdo visual personalizado e sua posição espacial dentro de uma imagem fornecida, usando a visão personalizada do Azure os recursos de "Detecção de objeto" em um aplicativo de realidade misturada.

Esse serviço permitirá que você treinar um modelo de aprendizado de máquina usando imagens de objeto. Você usará o modelo treinado para reconhecer objetos semelhantes e aproximar de sua localização no mundo real, conforme fornecido pela captura de câmera do Microsoft HoloLens ou conecte-se de uma câmera em um PC para fones imersivos em exposição (VR).

![resultado do curso](images/AzureLabs-Lab310-00.png)

**Visão personalizada do Azure, detecção de objetos** é um Service Microsoft que permite aos desenvolvedores criar classificadores de imagem personalizada. Os classificadores, em seguida, podem ser usados com novas imagens para detectar objetos dentro dessa nova imagem, fornecendo **limites da caixa** dentro da imagem em si. O serviço fornece um portal simple, fácil de usar on-line para simplificar esse processo. Para obter mais informações, visite os links a seguir:

* [Página de visão personalizada do Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [Limites e cotas](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

Após a conclusão deste curso, você terá um aplicativo de realidade mista que serão capaz de fazer o seguinte:

1. O usuário será capaz *olhares* em um objeto, que têm treinados usando o serviço do Azure personalizado da pesquisa Visual computacional, detecção de objetos. 
2. O usuário usará o *toque* gesto para capturar uma imagem de que eles estão observando.
3. O aplicativo enviará a imagem para o serviço de visão personalizada do Azure.
4. Haverá uma resposta do serviço que exibe o resultado de reconhecimento como texto de espaço de mundo. Isso será realizado por meio da utilização espacial rastreando dos o Microsoft HoloLens, como uma maneira de Noções básicas sobre a posição do mundo do objeto reconhecido e, em seguida, usando o *marca* associado com o que é detectado como na imagem, Forneça o texto do rótulo.

O curso também discutirá manualmente carregar imagens, criação de marcas, e treinamento do serviço, reconhecer diferentes objetos (no exemplo fornecido, uma xícara), por definir a *caixa limite* dentro da imagem que você enviar. 

> [!IMPORTANT]
> Após a criação e uso do aplicativo, o desenvolvedor deve navegar de volta para o Azure serviço personalizado de visão, identificar as previsões feitas pelo serviço e determinar se eles estavam corretos ou não (por meio de marcação nada o serviço perdido, e ajustando o *caixas delimitadoras*). O serviço pode, em seguida, ser treinado outra vez, que aumenta a probabilidade de ele reconhecer os objetos do mundo real.

Este curso ensinará você a obter os resultados com o Azure serviço personalizado de visão, detecção de objetos em um aplicativo de exemplo com base no Unity. Ele será cabe a você aplicar esses conceitos para um aplicativo personalizado que você pode criar.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> MR e o Azure 310: Detecção de objetos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#. Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (julho de 2018). Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que está listado abaixo.

Recomendamos que o hardware e software para este curso a seguir:

- Um computador de desenvolvimento
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [O SDK mais recente do Windows 10](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- Um [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) com o modo de desenvolvedor habilitado
- Acesso à Internet para a instalação do Azure e a recuperação de serviço de visão personalizada
-  Uma série de imagens pelo menos quinze (15) são necessários) para cada objeto que você gostaria de visão personalizada para reconhecer. Se desejar, você pode usar as imagens que já é fornecidas com este curso [uma série de cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).
2.  Configurar e testar o HoloLens. Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  É uma boa ideia executar calibragem e ajuste de Sensor ao começar a desenvolver um new App HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).

Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-portal"></a>Capítulo 1 - o Portal de visão personalizada

Para usar o **serviço de visão personalizada do Azure**, você precisará configurar uma instância para ficar disponível para seu aplicativo.

1.  Navegue [para o **serviço personalizado de visão** página principal](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Clique em **Introdução ao**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Entre Portal de visão personalizada.

    ![](images/AzureLabs-Lab310-02.png)

4.  Se você ainda não tiver uma conta do Azure, você precisará criá-lo. Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.

5.  Quando você estiver conectado pela primeira vez, você será solicitado com o *termos de serviço* painel. Clique na caixa de seleção para *concordar com os termos*. Em seguida, clique em **concordo**.

    ![](images/AzureLabs-Lab310-03.png)

6.  Tendo concordou com os termos, agora você está no *meus projetos* seção. Clique em **novo projeto**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Uma guia aparecerá no lado direito, que solicitará que você especifique alguns campos para o projeto.

    1.  Insira um nome para seu projeto

    2.  Insira uma descrição para o seu projeto (**opcional**)

    3.  Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Se você quiser [Leia mais sobre grupos de recursos do Azure, navegue até os documentos associados](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4.  Defina as **tipos de projeto** como **detecção de objetos (visualização)**.

8.  Quando tiver terminado, clique em **criar projeto**, e você será redirecionado para a página do projeto de serviço personalizado de visão.


## <a name="chapter-2---training-your-custom-vision-project"></a>Capítulo 2 - treinamento de seu projeto de visão personalizada

Uma vez no Portal da pesquisa Visual computacional personalizado, seu principal objetivo é treinar seu projeto para reconhecer a objetos específicos em imagens.

Você precisa de pelo menos 15 (15) imagens para cada objeto que você deseja que seu aplicativo reconheça. Você pode usar as imagens fornecidas com este curso ([uma série de cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

Para treinar seu projeto de visão personalizada:

1.  Clique no **+** lado **marcas**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Adicionar um **nome** da marca que será usada para associar suas imagens com. Neste exemplo estamos usando imagens do cups para reconhecimento, portanto, ter chamado a marca para isso, **Cup**. Clique em **salvar** após a conclusão.

    ![](images/AzureLabs-Lab310-07.png)

3.  Você notará sua **marca** foi adicionado (talvez seja necessário recarregar a página para que ele seja exibido). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Clique em **adicionar imagens** no centro da página.

    ![](images/AzureLabs-Lab310-09.png)

5.  Clique em **procurar arquivos locais**e navegue para as imagens que você gostaria de carregar um objeto, com sendo a mínima quinze (15).

    > [!TIP]
    >  Você pode selecionar várias imagens por vez, para carregar.

    ![](images/AzureLabs-Lab310-10.png)

6.  Pressione **carregar arquivos** depois de selecionar todas as imagens você deseja treinar o projeto com. Os arquivos de começar a carregar. Depois que você tiver a confirmação do upload, clique em **feito**.

    ![](images/AzureLabs-Lab310-11.png)

7.  Neste ponto suas imagens são carregadas, mas não estão marcadas.

    ![](images/AzureLabs-Lab310-12.png)

8.  Para marcar as imagens, use o mouse. Quando você focaliza sua imagem, um realce de seleção auxiliará desenhando automaticamente uma seleção em torno de seu objeto. Se não estiverem corretas, você pode desenhar seus próprios. Isso é feito segurando o botão esquerdo do mouse no mouse e, em seguida, arrastando a região de seleção para abranger o seu objeto. 

    ![](images/AzureLabs-Lab310-13.png) 

9. Após a seleção do objeto dentro da imagem, um pequeno prompt pedirá para você *Adicionar marca de região*. Selecione sua marca criada anteriormente ('Cup', no exemplo acima), ou se você estiver adicionando mais marcas, digitar isso em e clique no **+ (adição)** botão.

    ![](images/AzureLabs-Lab310-14.png) 

10. Para marcar a imagem a seguir, que você pode clicar na seta à direita da folha ou feche a folha de marca (clicando o **X** no canto superior direito da folha) e, em seguida, clique na imagem a próxima. Depois que a próxima imagem pronta, repita o mesmo procedimento. Faça isso para todas as imagens que você carregou, até que eles estão marcados. 

    > [!NOTE]
    >  Você pode selecionar vários objetos na mesma imagem, como a imagem a seguir: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Depois que você tiver marcado todos eles, clique no **marcadas** botão à esquerda da tela, para revelar as imagens marcadas. 

    ![](images/AzureLabs-Lab310-16.png)

12. Agora você está pronto para treinar seu serviço. Clique o **Train** botão e a primeira iteração de treinamento serão iniciada.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. Depois que ele é criado, você poderá ver dois botões chamados **tornar padrão** e **URL de previsão**. Clique em **tornar padrão** pela primeira vez, em seguida, clique em **URL de previsão**.

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > O ponto de extremidade que é fornecido a partir disso, é definido como o que ocorrer *iteração* foi marcada como padrão. Como tal, se você fizer um novo mais tarde *iteração* e atualizá-lo como padrão, você não precisará alterar seu código.

14. Depois de clicar em **URL de previsão**, abra *bloco de notas*e copie e cole o **URL** (também chamado de seu **ponto de extremidade de previsão**) e o **chave do serviço previsão**, de modo que você pode recuperá-la quando precisar dele posteriormente no código.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3 - configurar o projeto do Unity

A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.

1.  Abra **Unity** e clique em **New**.

    ![](images/AzureLabs-Lab310-21.png)

2.  Agora, você precisará fornecer um nome de projeto do Unity. Inserir **CustomVisionObjDetection**. Verifique se o tipo de projeto é definido como **3D**e defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![](images/AzureLabs-Lab310-22.png)

3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Vá para **edite* > *preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio**. Fechar o **preferências** janela.

    ![](images/AzureLabs-Lab310-23.png)

4.  Em seguida, vá para **arquivo > configurações de Build** e alterne os **plataforma** para *plataforma Universal do Windows*e, em seguida, clicando no **alternar plataforma** botão.

    ![](images/AzureLabs-Lab310-24.png)

5.  No mesmo **configurações de Build** janela, verifique se a seguir está definida:

    1.  **Dispositivo de destino** é definido como **HoloLens**        
    2.  **Tipo de compilação** é definido como **D3D**
    3.  **SDK** é definido como **mais recente instalada**
    4.  **Versão do Visual Studio** é definido como **mais recente instalada**
    5.  **Compilar e executar** é definido como **Máquina Local**            
    6.  O restante de configurações, em **configurações de Build**, deverá ser deixado como padrão por enquanto.

        ![](images/AzureLabs-Lab310-25.png)

6.  No mesmo **configurações de Build** janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o **Inspetor** está localizado.

7. Neste painel, algumas configurações precisam ser verificados:

    1.  No **outras configurações** guia:

        1.  **Versão de tempo de execução de scripts** deve ser **Experimental** (equivalente ao .NET 4.6), que irá disparar uma necessidade de reiniciar o Editor.

        2. **Script de back-end** deve ser **.NET**.

        3. **Nível de compatibilidade de API** deve ser **.NET 4.6**.

            ![](images/AzureLabs-Lab310-26.png)

    2.  Dentro de **configurações de publicação** guia, em **recursos**, verifique:

        1. **InternetClient**

        2.  **Webcam**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Mais para baixo no painel, no **XR configurações** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se da **misto do Windows Realidade SDK** é adicionado.

        ![](images/AzureLabs-Lab310-29.png)

8.  Volta **configurações de Build**, *Unity C\# projetos* não fica acinzentado: marque a caixa de seleção ao lado disso.

9.  Fechar o **configurações de Build** janela.

10. No **Editor**, clique em **editar** > **configurações do projeto** > **gráficos**.

    ![](images/AzureLabs-Lab310-30.png)

11. No **painel Inspetor** as *configurações de gráficos* será aberta. Role para baixo até ver uma matriz chamada **sempre incluem sombreadores**. Adicionar um slot, aumentando a **tamanho** variável por um (neste exemplo, fosse 8 então o definimos-9). Um novo slot será exibida, na última posição da matriz, conforme mostrado abaixo:

    ![](images/AzureLabs-Lab310-31.png)

12. No slot, clique no círculo ao lado do slot para abrir uma lista de sombreadores de destino menores. Procure os **herdado sombreadores, Transparent/difusa** sombreador e clique duas vezes nele. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Capítulo 4 - importar o pacote do CustomVisionObjDetection Unity

Para este curso, você receberá um pacote do Unity Asset denominada **Azure-MR-310.unitypackage**. 

> [DICA] Todos os objetos compatíveis com o Unity, incluindo o plano inteiro, podem ser empacotados em um **unitypackage** arquivo e exportado / importado em outros projetos. É a maneira mais segura e mais eficiente, mover ativos entre diferentes **projetos do Unity**.

Você pode encontrar o [pacote Azure-MR-310 que você precisa baixar aqui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).

1.  Com o painel do Unity na sua frente, clique em **ativos** no menu na parte superior da tela, em seguida, clique em **Importar pacote > pacote personalizado**.

    ![](images/AzureLabs-Lab310-33.png)

2.  Use o seletor de arquivos para selecionar o **Azure-MR-310.unitypackage** de pacote e clique em **abrir**. Uma lista de componentes para esse ativo será exibida para você. Confirme a importação clicando o **importação** botão.

    ![](images/AzureLabs-Lab310-34.png)

3.  Quando tiver terminado a importação, você observará que pastas do pacote agora foram adicionadas ao seu **ativos** pasta. Esse tipo de estrutura de pastas é típico para um projeto do Unity.

    ![](images/AzureLabs-Lab310-35.png)

    1.  O **materiais** pasta contém o material usado pelas **olhares Cursor**. 

    2.  O **plug-ins** pasta contém a DLL da Newtonsoft usado pelo código para desserializar a resposta do serviço web. Dois (2) versões diferentes contidas na pasta e subpasta, são necessárias para permitir que a biblioteca a ser usado e compilados pelo Editor do Unity e o build UWP. 

    3.  O **pré-fabricados** pasta contém os pré-fabricados contidos na cena. Eles são:

        1.  O **GazeCursor**, o cursor usado no aplicativo. Funcionará junto com pré-fabricado SpatialMapping para poder ser colocado na cena na parte superior de objetos físicos.
        2.  O **rótulo**, que é o objeto de interface do usuário usado para exibir a marca de objeto na cena quando necessário.
        3.  O **SpatialMapping**, que é o objeto que permite que o aplicativo use criar um mapa virtual, usando o rastreamento de espacial dos o Microsoft HoloLens.

    4.  O **cenas** pasta que contém atualmente a cena pré-criados para este curso.

4.  Abra o **cenas** pasta, no **painel projeto**e clique duas vezes no **ObjDetectionScene**, para carregar a cena que você usará para este curso.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **Nenhum código foi incluído**, você irá escrever o código seguindo este curso.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Capítulo 5 - criar a classe CustomVisionAnalyser.

Neste ponto, você está pronto para escrever um código. Você começará com o **CustomVisionAnalyser** classe.

> [!NOTE]
> As chamadas para o **serviço personalizado de visão**, no código mostrado abaixo, são feitas usando o **API de REST de visão personalizada**. Usando isso, você verá como implementar e usar essa API (útil para entender como implementar algo semelhante em seu próprio). Lembre-se que a Microsoft oferece uma **SDK de visão personalizada** que também pode ser usado para fazer chamadas para o serviço. Para obter mais informações, visite o [artigo do SDK de visão personalizada](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).

Essa classe é responsável por:

- Carregando a imagem mais recente capturada como uma matriz de bytes.

- Enviando a matriz de bytes para o Azure **serviço de visão personalizada** instância para análise.

- Recebendo a resposta como uma cadeia de caracteres JSON.

- Ao desserializar a resposta e passando resultante **previsão** para o **SceneOrganiser** classe, que se encarregará de como a resposta deve ser exibida.

Para criar essa classe:

1.  Com o botão direito no **pasta ativo**, localizado na **painel projeto**, em seguida, clique em **criar** > **pasta**. Chame a pasta **Scripts**.

    ![](images/AzureLabs-Lab310-37.png)

2.  Clique duas vezes na pasta recém-criada, para abri-lo.

3.  Clique com botão direito dentro da pasta e clique em **Create** > **C\# Script**. Nomeie o script **CustomVisionAnalyser.**

4.  Clique duas vezes na nova **CustomVisionAnalyser** script para abri-lo com **Visual Studio.**

5.  Verifique se que você tem os seguintes namespaces referenciados na parte superior do arquivo:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  No **CustomVisionAnalyser** de classe, adicione as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Certifique-se de inserir seu **previsão-chave de serviço** para o **predictionKey** variável e seu **ponto de extremidade de previsão** no **predictionEndpoint**  variável. Você copiou para [bloco de notas anteriormente, no capítulo 2, etapa 14](#chapter-2---training-your-custom-vision-project).

7.  Código para o **Awake()** agora precisa ser adicionada para inicializar a variável de instância:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Adicionar a corrotina (com a estática **GetImageAsByteArray()** método abaixo dele), que irá obter os resultados da análise de imagem, capturada pelo **ImageCapture** classe.

    > [!NOTE]
    > No **AnalyseImageCapture** corrotina, há uma chamada para o **SceneOrganiser** classe que você ainda está a criar. Portanto, **deixar as linhas comentadas agora**.

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. Excluir o **Start ()** e **Update ()** métodos, pois não serão usados. 

10.  Certifique-se de salvar suas alterações no **Visual Studio**, antes de retornar ao **Unity**.

> [!IMPORTANT]
> Como mencionado anteriormente, não se preocupe sobre código que pode aparecer ter um erro, pois você fornecerá ainda mais em breve, classes que corrigi-los.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Capítulo 6 - criar a classe CustomVisionObjects

A classe que você criará agora é o **CustomVisionObjects** classe.

Esse script contém um número de objetos usados por outras classes para serializar e desserializar as chamadas feitas para o serviço personalizado de visão.

Para criar essa classe:

1.  Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**. Chame o script **CustomVisionObjects.**

2.  Clique duas vezes na nova **CustomVisionObjects** script para abri-lo com **Visual Studio.**

3.  Verifique se que você tem os seguintes namespaces referenciados na parte superior do arquivo:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Excluir o **Start ()** e **Update ()** métodos dentro de **CustomVisionObjects** classe, essa classe deve agora estar vazia.

    > [!WARNING]
    > É importante que você siga a próxima instrução com cuidado. Se você colocar novas declarações de classe dentro do **CustomVisionObjects** classe, você receberá erros de compilação na [capítulo 10](#chapter-10---create-the-imagecapture-class), informando que **AnalysisRootObject** e  **BoundingBox** não foram encontrados.

5.  Adicione as seguintes classes *fora* as **CustomVisionObjects** classe. Esses objetos são usados pelos **Newtonsoft** biblioteca para serializar e desserializar os dados de resposta:

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  Certifique-se de salvar suas alterações no **Visual Studio**, antes de retornar ao **Unity**.

## <a name="chapter-7---create-the-spatialmapping-class"></a>Capítulo 7 - criar a classe SpatialMapping

Essa classe será definido o **Colisor de mapeamento espacial** na cena, portanto, para ser capaz de detectar colisões entre objetos virtuais e objetos reais.

Para criar essa classe:

1.  Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**. Chame o script **SpatialMapping.**

2.  Clique duas vezes na nova **SpatialMapping** script para abri-lo com **Visual Studio.**

3.  Verifique se você tem os seguintes namespaces mencionados acima de **SpatialMapping** classe:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  Em seguida, adicione as seguintes variáveis dentro do **SpatialMapping** classe acima a **Start ()** método:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  Adicione a **Awake()** e **Start ()**:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  Excluir o **Update ()** método.

7.  Certifique-se de salvar suas alterações no **Visual Studio**, antes de retornar ao **Unity**.


## <a name="chapter-8---create-the-gazecursor-class"></a>Capítulo 8 - criar a classe GazeCursor

Essa classe é responsável por configurar o cursor no local correto no espaço real, ao utilizar o **SpatialMappingCollider**, criado no capítulo anterior.

Para criar essa classe:

1.  Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**. Chame o script **GazeCursor**

2.  Clique duas vezes na nova **GazeCursor** script para abri-lo com **Visual Studio.**

3.  Verifique se você tem o namespace a seguir mencionado acima de **GazeCursor** classe:

    ```csharp
    using UnityEngine;
    ```

4.  Em seguida, adicione a seguinte variável dentro de **GazeCursor** classe acima a **Start ()** método. 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Atualizar o **Start ()** método com o código a seguir:

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  Atualizar o **Update ()** método com o código a seguir:

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > Não se preocupe sobre o erro para o **SceneOrganiser** classe não foi encontrada, você criará no próximo capítulo.

7. Certifique-se de salvar suas alterações no **Visual Studio**, antes de retornar ao **Unity**.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Capítulo 9 - criar a classe SceneOrganiser

Essa classe será:

-   Configurar o *câmera principal* anexando os componentes apropriados para ele.

-   Quando um objeto é detectado, será responsável por calcular sua posição no mundo real e coloque um **etiqueta** quase-lo com os devidos **nome da marca**.    

Para criar essa classe:

1.  Com o botão direito dentro de **Scripts** pasta, em seguida, clique em **criar** > **C\# Script**. Nomeie o script **SceneOrganiser**.

2.  Clique duas vezes na nova **SceneOrganiser** script para abri-lo com **Visual Studio.**

3.  Verifique se você tem os seguintes namespaces mencionados acima de **SceneOrganiser** classe:

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  Em seguida, adicione as seguintes variáveis dentro de **SceneOrganiser** classe acima a **Start ()** método:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  Excluir o **Start ()** e **Update ()** métodos.

6.  Abaixo das variáveis, adicione a **Awake()** método, que irá inicializar a classe e configure a cena.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  Adicione a **PlaceAnalysisLabel()** método, que serão *instanciar* o rótulo na cena (que neste ponto, é invisível para o usuário). Ele também coloca o quad (também invisível) em que a imagem é colocada e se sobrepõe com o mundo real. Isso é importante porque as coordenadas da caixa recuperados do serviço após a análise são rastreadas nesse quad determinada a localização aproximada do objeto no mundo real. 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  Adicione a **FinaliseLabel()** método. Ele é responsável por:

    *   Definindo o *etiqueta* texto com o *marca* da previsão com a confiança mais alta.
    *   Chamar o cálculo do *caixa delimitadora* no objeto quad, posicionado anteriormente e colocar o rótulo na cena.
    *   Ajustando a profundidade de rótulo usando um Raycast em direção a *caixa delimitadora*, que deve entrem em conflito com o objeto no mundo real.
    * Redefinindo o processo de captura para permitir que o usuário capture outra imagem.

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  Adicione a **CalculateBoundingBoxPosition()** método, que hospeda um número de cálculos necessários para traduzir o *caixa delimitadora* coordenadas recuperados do serviço e recriá-los proporcionalmente em quad.

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. Certifique-se de salvar suas alterações no **Visual Studio**, antes de retornar ao **Unity**.

    > [!IMPORTANT]
    > Antes de continuar, abra o **CustomVisionAnalyser** classe e dentro de **AnalyseLastImageCaptured()** método, *Descomente* as seguintes linhas:
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> Não se preocupar sobre o **ImageCapture** mensagem 'não pôde ser encontrado' da classe, você criará no próximo capítulo.


## <a name="chapter-10---create-the-imagecapture-class"></a>Capítulo 10 - criar a classe ImageCapture

A próxima classe que você pretende criar é a **ImageCapture** classe.

Essa classe é responsável por:

*   Capturar uma imagem usando a câmera HoloLens e armazená-los de *aplicativo* pasta.
*   Manipulando *toque* gestos do usuário.

Para criar essa classe:

1.  Vá para o **Scripts** pasta que você criou anteriormente.

2.  Clique com botão direito dentro da pasta e clique em **Create** > **C\# Script**. Nomeie o script **ImageCapture**.

3.  Clique duas vezes na nova **ImageCapture** script para abri-lo com **Visual Studio.**

4.  Substitua os namespaces na parte superior do arquivo pelo seguinte:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro de **ImageCapture** classe acima a **Start ()** método:

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implemente um manipulador que será chamado quando ocorre um gesto de tocar:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > Quando o cursor estiver **verde**, isso significa que a câmera está disponível para capturar a imagem. Quando o cursor estiver **vermelho**, isso significa que a câmera está ocupada.

8.  Adicione o método que o aplicativo usa para iniciar o processo de captura de imagem e armazenar a imagem:

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  Adicione os manipuladores que serão chamados quando a foto tiver sido capturada e para quando ele estiver pronto para ser analisado. O resultado é então passado para o **CustomVisionAnalyser** para análise.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Certifique-se de salvar suas alterações no **Visual Studio**, antes de retornar ao **Unity**.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Capítulo 11 - como configurar os scripts na cena

Agora que você tenha escrito todo o código necessário para este projeto, é hora de configurar os scripts na cena e, em pré-fabricados, para que eles se comportam corretamente.

1.  Dentro do **Editor do Unity**, no **painel de hierarquia**, selecione o **câmera principal**.
2.  No **painel Inspetor**, com o **câmera principal** selecionado, clique em **adicionar componente**, em seguida, procure **SceneOrganiser** script e Clique duas vezes, para adicioná-lo.

    ![](images/AzureLabs-Lab310-38.png)

3.  No **painel projeto**, abra o **pasta pré-fabricados**, arraste o **rótulo** pré-fabricado no *rótulo* área, de entrada de destino da referência vazio no **SceneOrganiser** script que você acabou de adicionar para o *câmera principal*, conforme mostrado na imagem abaixo:

    ![](images/AzureLabs-Lab310-39.png)

4.  No **painel de hierarquia**, selecione o **GazeCursor** filho do **câmera principal**.
5.  No **painel Inspetor**, com o **GazeCursor** selecionado, clique em **adicionar componente**, em seguida, procure **GazeCursor** script e Clique duas vezes, para adicioná-lo.

    ![](images/AzureLabs-Lab310-40.png)

6.  Novamente, na **painel de hierarquia**, selecione o **SpatialMapping** filho do **câmera principal**.
7.  No **painel Inspetor**, com o **SpatialMapping** selecionado, clique em **adicionar componente**, em seguida, procure **SpatialMapping** script e clique duas vezes, para adicioná-lo.

    ![](images/AzureLabs-Lab310-41.png)

Os scripts restantes que você não tem conjunto será adicionado pelo código na **SceneOrganiser** script durante o tempo de execução.

## <a name="chapter-12---before-building"></a>Capítulo 12 - antes de compilar

Para executar um teste completo de seu aplicativo você precisará para fazer sideload dele para o Microsoft HoloLens.

Antes de começar, verifique se:

-  Todas as configurações mencionadas a [capítulo 3](#chapter-3---set-up-the-unity-project) estão definidas corretamente.
- O script **SceneOrganiser** está associada a **câmera principal** objeto.
- O script **GazeCursor** está associada a **GazeCursor** objeto.
- O script **SpatialMapping** está associada a **SpatialMapping** objeto.
- Na [capítulo 5](#chapter-5---create-the-customvisionanalyser-class), etapa 6:

    - Certifique-se de inserir sua **chave de previsão do serviço** para o **predictionKey** variável.
    - Você inseriu sua **ponto de extremidade de previsão** para o **predictionEndpoint** classe.

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Capítulo 13 - criar a solução UWP e fazer sideload de seu aplicativo

Agora você está pronto para compilar o aplicativo como uma solução de UWP que você será capaz de implantar para o Microsoft HoloLens. Para iniciar o processo de compilação:

1.  Vá para **arquivo > configurações de Build**.

2.  Escala **Unity C\# projetos**.

3.  Clique em **adicionar cenas abertas**. Isso adicionará a cena aberta atualmente para a compilação.

    ![](images/AzureLabs-Lab310-42.png)

4.  Clique em **Compilar**. Unity iniciará uma *Explorador de arquivos* janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em. Criar pasta agora e nomeie- **aplicativo**. Em seguida, com o **App** pasta selecionada, clique em **Selecionar pasta**.

5.  Unity começará a compilar seu projeto para o **aplicativo** pasta.

6.  Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um **Explorador de arquivos** janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).

7.  Para implantar o logon no Microsoft HoloLens, será necessário o endereço IP do dispositivo (para a implantação remota) e garantir que ele também tem **modo de desenvolvedor** definido. Para fazer isso:

    1.  Durante o uso de seu HoloLens, abra o **configurações**.

    2.  Vá para **rede e Internet** > **Wi-Fi** > **opções avançadas**

    3.  Observe a **IPv4** endereço.

    4.  Em seguida, navegue até **as configurações**e, em seguida, para **atualização e segurança** > **para desenvolvedores**

    5.  Definir **modo de desenvolvedor** *em*.

8.  Navegue até seu novo build do Unity (o **App** pasta) e abra o arquivo de solução com **Visual Studio**.

9.  No, selecione a configuração da solução **depurar**.

10. Na plataforma da solução, selecione **x86, computador remoto**. Você será solicitado a inserir o **endereço IP** de um dispositivo remoto (o Microsoft HoloLens, nesse caso, que você anotou).

    ![](images/AzureLabs-Lab310-43.png)

11. Vá para o **construir** menu e clique em **implantar solução** para carregar o aplicativo para o HoloLens.

12. Seu aplicativo agora deve aparecer na lista de aplicativos instalados no seu Microsoft HoloLens, pronto para ser iniciado!

### <a name="to-use-the-application"></a>Para usar o aplicativo:

* Examinar um objeto, que você ter treinado com seu **serviço de visão personalizada do Azure, detecção de objetos**e usar o **gesto de toque**.
* Se o objeto for detectado com êxito, um espaço de mundo *texto do rótulo* aparecerá com o nome da marca.

> [!IMPORTANT]
> Sempre que você captura uma foto e enviá-lo para o serviço, você pode voltar para a página de serviço e readaptar o serviço com as imagens capturadas recentemente. No início, você provavelmente também precisará corrigir a *caixas delimitadoras* sejam mais precisos e readaptar o serviço.

> [!NOTE]
> O texto do rótulo colocado poderão não aparecer perto o objeto quando os sensores do Microsoft HoloLens e/ou o SpatialTrackingComponent no Unity não conseguir colocar os colisores apropriados, em relação os objetos do mundo real. Tente usar o aplicativo em uma superfície diferente se esse for o caso.

## <a name="your-custom-vision-object-detection-application"></a>Sua visão personalizada, o aplicativo de detecção de objetos

Parabéns, você criou um aplicativo de realidade mista que aproveita a visão personalizada do Azure, API de detecção de objeto, que pode reconhecer um objeto de uma imagem e, em seguida, fornecem uma posição aproximada para esse objeto no espaço 3D.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Adicionando para o rótulo de texto, use um cubo semitransparente para encapsular o objeto real em um 3D *caixa delimitadora*.

### <a name="exercise-2"></a>Exercício 2

Treine seu serviço personalizado de visão para reconhecer mais objetos.

### <a name="exercise-3"></a>Exercício 3

Tocar um som quando um objeto é reconhecido.

### <a name="exercise-4"></a>Exercício 4

Usar a API para treinar novamente seu serviço com as mesmas imagens de análise de seu aplicativo, portanto, para tornar o serviço mais precisos (fazer a previsão e o treinamento simultaneamente).
