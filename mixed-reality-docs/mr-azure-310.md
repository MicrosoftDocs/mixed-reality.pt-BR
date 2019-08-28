---
title: Sr e Azure 310-detecção de objeto
description: Conclua este curso para aprender a treinar um modelo de aprendizado de máquina e, em seguida, usar o modelo treinado para reconhecer objetos semelhantes e sua posição no mundo real de dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, visão personalizada, detecção de objetos, realidade misturada, Academia, Unity, tutorial, API, hololens
ms.openlocfilehash: 71370db84a9b90b017e8d5fac0799a862883d046
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047221"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

# <a name="mr-and-azure-310-object-detection"></a>Sr e Azure 310: Detecção de objeto

Neste curso, você aprenderá a reconhecer o conteúdo Visual personalizado e sua posição espacial dentro de uma imagem fornecida, usando o Azure Visão Personalizada recursos de "detecção de objeto" em um aplicativo de realidade misturada.

Este serviço permitirá que você treine um modelo de aprendizado de máquina usando imagens de objeto. Em seguida, você usará o modelo treinado para reconhecer objetos semelhantes e aproximar seu local no mundo real, conforme fornecido pela captura de câmera do Microsoft HoloLens ou uma câmera conectar-se a um PC para headsets de imersão (VR).

![resultado do curso](images/AzureLabs-Lab310-00.png)

**Visão personalizada do Azure, a detecção de objeto** é um serviço da Microsoft que permite aos desenvolvedores criar classificadores de imagem personalizados. Esses classificadores podem ser usados com novas imagens para detectar objetos nessa nova imagem, fornecendo **limites de caixa** dentro da própria imagem. O serviço fornece um portal online simples, fácil de usar, para simplificar esse processo. Para obter mais informações, visite os links a seguir:

* [Página de Visão Personalizada do Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [Limites e cotas](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

Após a conclusão deste curso, você terá um aplicativo de realidade misturada que poderá fazer o seguinte:

1. O usuário poderá *olhar* em um objeto, que foi treinado usando a serviço de visão personalizada do Azure, a detecção de objetos. 
2. O usuário usará o gesto de *toque* para capturar uma imagem do que está olhando.
3. O aplicativo enviará a imagem para a Serviço de Visão Personalizada do Azure.
4. Haverá uma resposta do serviço que exibirá o resultado do reconhecimento como texto de espaço mundial. Isso será realizado por meio da utilização do acompanhamento espacial do Microsoft HoloLens, como uma maneira de entender a posição mundial do objeto reconhecido e, em seguida, usar a *marca* associada ao que é detectado na imagem, para fornecer o texto do rótulo.

O curso também abordará manualmente o carregamento de imagens, a criação de marcas e o treinamento do serviço, para reconhecer objetos diferentes (no exemplo fornecido, uma xícara), definindo a *caixa de limite* na imagem que você envia. 

> [!IMPORTANT]
> Após a criação e o uso do aplicativo, o desenvolvedor deve navegar de volta para a Serviço de Visão Personalizada do Azure e identificar as previsões feitas pelo serviço e determinar se elas estavam corretas ou não (por meio da marcação de qualquer coisa que o serviço perdeu e ajustando as *caixas*delimitadoras). Em seguida, o serviço pode ser treinado novamente, o que aumentará a probabilidade de reconhecê-los em objetos do mundo real.

Este curso ensinará como obter os resultados da Serviço de Visão Personalizada do Azure, detecção de objetos, em um aplicativo de exemplo baseado em Unity. Será necessário aplicar esses conceitos a um aplicativo personalizado que você possa estar criando.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Sr e Azure 310: Detecção de objeto</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (julho de 2018). Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) , embora não seja recomendável que as informações neste curso correspondam perfeitamente ao que você encontrará no software mais recente do que o que está listado abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um PC de desenvolvimento
- [Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [O SDK do Windows 10 mais recente](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017,4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- Um [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) com o modo de desenvolvedor habilitado
- Acesso à Internet para a instalação do Azure e recuperação de Serviço de Visão Personalizada
-  Uma série de pelo menos quinze (15) imagens são necessárias) para cada objeto que você deseja que o Visão Personalizada reconheça. Se desejar, você pode usar as imagens já fornecidas com este curso, [uma série de CUPS](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).
2.  Configure e teste seu HoloLens. Se você precisar de suporte para configurar seu HoloLens, [visite o artigo configuração do hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  É uma boa ideia executar a calibragem e o ajuste do sensor ao começar a desenvolver um novo aplicativo do HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

Para obter ajuda sobre calibragem, siga este [link para o artigo Calibration do HoloLens](calibration.md#hololens-2).

Para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste do sensor do HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-portal"></a>Capítulo 1-o portal de Visão Personalizada

Para usar o **serviço de visão personalizada do Azure**, você precisará configurar uma instância dele para ser disponibilizada para seu aplicativo.

1.  Navegue [até a página principal do **serviço de visão personalizada** ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Clique em **introdução**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Entre no portal de Visão Personalizada.

    ![](images/AzureLabs-Lab310-02.png)

4.  Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

5.  Depois de fazer logon pela primeira vez, você será solicitado com o painel *termos de serviço* . Clique na caixa de seleção para *concordar com os termos*. Em seguida, clique em **concordo**.

    ![](images/AzureLabs-Lab310-03.png)

6.  Tendo acordado os termos, agora você está na seção *meus projetos* . Clique em **novo projeto**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Uma guia será exibida no lado direito, o que solicitará que você especifique alguns campos para o projeto.

    1.  Inserir um nome para seu projeto

    2.  Inserir uma descrição para seu projeto (**opcional**)

    3.  Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Se você quiser [ler mais sobre os grupos de recursos do Azure, navegue até o docs associado](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4.  Defina os **tipos de projeto** como **detecção de objeto (versão prévia)** .

8.  Quando terminar, clique em **criar projeto**e você será redirecionado para a página do projeto serviço de visão personalizada.


## <a name="chapter-2---training-your-custom-vision-project"></a>Capítulo 2-treinando seu Visão Personalizada projeto

Uma vez no portal de Visão Personalizada, seu objetivo principal é treinar seu projeto para reconhecer objetos específicos em imagens.

Você precisa de pelo menos quinze (15) imagens para cada objeto que você deseja que seu aplicativo reconheça. Você pode usar as imagens fornecidas com este curso ([uma série de CUPS](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

Para treinar seu projeto de Visão Personalizada:

1.  Clique no **+** botão ao lado de **marcas**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Adicione um **nome** para a marca que será usada para associar suas imagens ao. Neste exemplo, estamos usando imagens de CUPS para reconhecimento e, portanto, nomeamos a marca para isso, **Cup**. Clique em **salvar** após concluir.

    ![](images/AzureLabs-Lab310-07.png)

3.  Você notará que sua **marca** foi adicionada (talvez seja necessário recarregar sua página para que ela apareça). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Clique em **Adicionar imagens** no centro da página.

    ![](images/AzureLabs-Lab310-09.png)

5.  Clique em **procurar arquivos locais**e navegue até as imagens que você deseja carregar para um objeto, com o mínimo de quinze (15).

    > [!TIP]
    >  Você pode selecionar várias imagens de cada vez para carregar.

    ![](images/AzureLabs-Lab310-10.png)

6.  Pressione **carregar arquivos** depois de selecionar todas as imagens com as quais você gostaria de treinar o projeto. Os arquivos começarão a ser carregados. Depois de confirmar o carregamento, clique em **concluído**.

    ![](images/AzureLabs-Lab310-11.png)

7.  Neste ponto, suas imagens são carregadas, mas não marcadas.

    ![](images/AzureLabs-Lab310-12.png)

8.  Para marcar suas imagens, use o mouse. À medida que você passa o mouse sobre a imagem, um realce de seleção o ajudará a desenhar automaticamente uma seleção em volta do objeto. Se não for preciso, você poderá desenhar o seu próprio. Isso é feito mantendo o clique com o botão esquerdo do mouse e arrastando a região de seleção para abranger seu objeto. 

    ![](images/AzureLabs-Lab310-13.png) 

9. Após a seleção do objeto na imagem, um pequeno prompt solicitará que você *adicione a marca de região*. Selecione a marca criada anteriormente (' Cup ', no exemplo acima) ou, se você estiver adicionando mais marcas, digite-as em e clique no botão **+ (mais)** .

    ![](images/AzureLabs-Lab310-14.png) 

10. Para marcar a próxima imagem, você pode clicar na seta à direita da folha ou fechar a folha de marca (clicando no **X** no canto superior direito da folha) e, em seguida, na imagem seguinte. Quando a próxima imagem estiver pronta, repita o mesmo procedimento. Faça isso para todas as imagens que você carregou, até que todas estejam marcadas. 

    > [!NOTE]
    >  Você pode selecionar vários objetos na mesma imagem, como a imagem abaixo: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Depois de ter marcado todos eles, clique no botão **marcado** , à esquerda da tela, para revelar as imagens marcadas. 

    ![](images/AzureLabs-Lab310-16.png)

12. Agora você está pronto para treinar seu serviço. Clique no botão **treinar** e a primeira iteração de treinamento será iniciada.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. Depois de compilado, você poderá ver dois botões chamados **Make Default** e predição **URL**. Clique em **tornar padrão** primeiro e, em seguida, clique em **URL de previsão**.

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > O ponto de extremidade fornecido por isso é definido para qualquer *iteração* marcada como padrão. Dessa forma, se você fizer uma nova *iteração* e atualizá-la como padrão, não será necessário alterar seu código.

14. Depois de clicar em **URL de previsão**, abra o *bloco de notas*e copie e cole a **URL** (também chamada de ponto de extremidade de **previsão**) e a chave de **previsão do serviço**para que você possa recuperá-la quando precisar mais tarde no código.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3 – configurar o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra o **Unity** e clique em **novo**.

    ![](images/AzureLabs-Lab310-21.png)

2.  Agora, você precisará fornecer um nome de projeto de Unity. Insira **CustomVisionObjDetection**. Verifique se o tipo de projeto está definido como **3D**e defina o **local** como algum lugar apropriado para você (Lembre-se de que mais próximo aos diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![](images/AzureLabs-Lab310-22.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar* > *preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**. Altere o **Editor de script externo** para o **Visual Studio**. Feche a janela **preferências** .

    ![](images/AzureLabs-Lab310-23.png)

4.  Em seguida, vá para **arquivo > configurações de compilação** , alterne a **plataforma** para *plataforma universal do Windows*e, em seguida, clique no botão **alternar plataforma** .

    ![](images/AzureLabs-Lab310-24.png)

5.  Na mesma janela **configurações de compilação** , verifique se o seguinte está definido:

    1.  O **dispositivo de destino** está definido como **HoloLens**        
    2.  O **tipo de compilação** está definido como **D3D**
    3.  O **SDK** está definido para o **mais recente instalado**
    4.  A **versão do Visual Studio** está definida para o **mais recente instalado**
    5.  **Compilar e executar** é definido como **computador local**            
    6.  As configurações restantes, em **configurações de compilação**, devem ser deixadas como padrão por enquanto.

        ![](images/AzureLabs-Lab310-25.png)

6.  Na mesma janela **configurações de compilação** , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o **Inspetor** está localizado.

7. Nesse painel, algumas configurações precisam ser verificadas:

    1.  Na guia **outras configurações** :

        1.  A **versão de tempo de execução de script** deve ser **Experimental** (.NET 4,6 equivalente), o que irá disparar uma necessidade de reiniciar o editor.

        2. O **back-end de script** deve ser **.net**.

        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**.

            ![](images/AzureLabs-Lab310-26.png)

    2.  Na guia **configurações de publicação** , em **recursos**, marque:

        1. **InternetClient**

        2.  **Integrada**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**de tique, em seguida, verifique se o SDK do **Windows Mixed Reality** foi adicionado.

        ![](images/AzureLabs-Lab310-29.png)

8.  De volta às **configurações de compilação**, *\# projetos Unity C* não estão mais esmaecidos: marque a caixa de seleção ao lado disso.

9.  Feche a janela **configurações de compilação** .

10. No **Editor**, clique em **Editar** > **configurações** > do projeto**gráficos**.

    ![](images/AzureLabs-Lab310-30.png)

11. No **painel Inspetor** , as *configurações de gráficos* serão abertas. Role para baixo até ver uma matriz chamada **sempre incluir sombreadores**. Adicione um slot aumentando a variável de **tamanho** em um (neste exemplo, ele era 8, então fizemos 9). Um novo slot será exibido na última posição da matriz, conforme mostrado abaixo:

    ![](images/AzureLabs-Lab310-31.png)

12. No slot, clique no círculo de destino pequeno ao lado do slot para abrir uma lista de sombreadores. Procure por sombreadores herdados/sombreador **transparente/difuso** e clique duas vezes nele. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Capítulo 4-importando o pacote do CustomVisionObjDetection Unity

Para este curso, você receberá um pacote de ativos de Unity chamado **Azure-Mr-310. unitypackage**. 

> Dicas Todos os objetos com suporte do Unity, incluindo cenas inteiras, podem ser empacotados em um arquivo **. unitypackage** e exportados/importados em outros projetos. É a maneira mais segura, e mais eficiente, de mover ativos entre diferentes **projetos do Unity**.

Você pode encontrar o [pacote Azure-Mr-310 que você precisa baixar aqui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).

1.  Com o painel do Unity na frente, clique em **ativos** no menu na parte superior da tela e, em seguida, clique em **Importar pacote > pacote personalizado**.

    ![](images/AzureLabs-Lab310-33.png)

2.  Use o seletor de arquivos para selecionar o pacote **Azure-Mr-310. unitypackage** e clique em **abrir**. Uma lista de componentes para este ativo será exibida para você. Confirme a importação clicando no botão **importar** .

    ![](images/AzureLabs-Lab310-34.png)

3.  Depois de concluir a importação, você observará que as pastas do pacote agora foram adicionadas à sua pasta de **ativos** . Esse tipo de estrutura de pastas é típico para um projeto do Unity.

    ![](images/AzureLabs-Lab310-35.png)

    1.  A pasta **materiais** contém o material usado pelo **cursor olhar**. 

    2.  A pasta **plugins** contém a dll Newtonsoft usada pelo código para desserializar a resposta da Web do serviço. As duas (2) diferentes versões contidas na pasta e na subpasta são necessárias para permitir que a biblioteca seja usada e criada pelo editor de Unity e pela compilação UWP. 

    3.  A pasta **pré-fabricados** contém o pré-fabricados contido na cena. São eles:

        1.  O **GazeCursor**, o cursor usado no aplicativo. Trabalhará junto com o SpatialMapping pré-fabricado para poder ser colocado na cena sobre objetos físicos.
        2.  O **rótulo**, que é o objeto de interface do usuário usado para exibir a marca de objeto na cena quando necessário.
        3.  O **SpatialMapping**, que é o objeto que permite que o aplicativo use criar um mapa virtual, usando o acompanhamento espacial do Microsoft HoloLens.

    4.  A pasta de **cenas** que atualmente contém a cena pré-criada para este curso.

4.  Abra a pasta de **cenas** , no **painel Projeto**e clique duas vezes em **ObjDetectionScene**para carregar a cena que será usada para este curso.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **Nenhum código está incluído**, você escreverá o código seguindo este curso.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Capítulo 5 – criar a classe CustomVisionAnalyser.

Neste ponto, você está pronto para escrever um código. Você começará com a classe **CustomVisionAnalyser** .

> [!NOTE]
> As chamadas para o **serviço de visão personalizada**, feitas no código mostrado abaixo, são feitas usando a **API REST do visão personalizada**. Ao usar isso, você verá como implementar e usar essa API (útil para entender como implementar algo semelhante por conta própria). Lembre-se de que a Microsoft oferece um **SDK Visão personalizada** que também pode ser usado para fazer chamadas para o serviço. Para obter mais informações, visite o [artigo visão personalizada SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).

Essa classe é responsável por:

- Carregando a imagem mais recente capturada como uma matriz de bytes.

- Enviando a matriz de bytes para a instância de **serviço de visão personalizada** do Azure para análise.

- Recebendo a resposta como uma cadeia de caracteres JSON.

- Desserializar a resposta e passar a **previsão** resultante para a classe **SceneOrganiser** , que cuidará de como a resposta deve ser exibida.

Para criar esta classe:

1.  Clique com o botão direito do mouse na **pasta ativo**, localizada no **painel Projeto**, e clique em **criar** > **pasta**. Chame os **scripts**da pasta.

    ![](images/AzureLabs-Lab310-37.png)

2.  Clique duas vezes na pasta recém-criada para abri-la.

3.  Clique com o botão direito do mouse dentro da pasta e clique em **criar** > **script C\#** . Nomeie o script **CustomVisionAnalyser.**

4.  Clique duas vezes no novo script **CustomVisionAnalyser** para abri-lo com o **Visual Studio.**

5.  Verifique se você tem os seguintes namespaces referenciados na parte superior do arquivo:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  Na classe **CustomVisionAnalyser** , adicione as seguintes variáveis:

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
    > Certifique-se de inserir sua **chave de previsão de serviço** na variável **PredictionKey** e seu **ponto de extremidade de previsão** na variável **predictionEndpoint** . Você os copiou no [bloco de notas anteriormente, no capítulo 2, etapa 14](#chapter-2---training-your-custom-vision-project).

7.  O código para **ativo ()** agora precisa ser adicionado para inicializar a variável de instância:

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

8.  Adicione a corrotina (com o método estático **GetImageAsByteArray ()** abaixo dela), que obterá os resultados da análise da imagem, capturada pela classe **ImageCapture** .

    > [!NOTE]
    > Na **AnalyseImageCapture** corrotina, há uma chamada para a classe **SceneOrganiser** que você ainda deseja criar. Portanto, **deixe essas linhas comentadas por enquanto**.

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

9. Exclua os métodos **Start ()** e **Update ()** , pois eles não serão usados. 

10.  Certifique-se de salvar as alterações no **Visual Studio**antes de retornar ao **Unity**.

> [!IMPORTANT]
> Como mencionado anteriormente, não se preocupe com o código que pode parecer ter um erro, pois você fornecerá mais classes em breve, o que corrigirá esses erros.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Capítulo 6-criar a classe CustomVisionObjects

A classe que você criará agora é a classe **CustomVisionObjects** .

Esse script contém vários objetos usados por outras classes para serializar e desserializar as chamadas feitas ao Serviço de Visão Personalizada.

Para criar esta classe:

1.  Clique com o botão direito do mouse na pasta **scripts** e clique em **criar** > **script C\#** . Chame o script **CustomVisionObjects.**

2.  Clique duas vezes no novo script **CustomVisionObjects** para abri-lo com o **Visual Studio.**

3.  Verifique se você tem os seguintes namespaces referenciados na parte superior do arquivo:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Exclua os métodos **Start ()** e **Update ()** dentro da classe **CustomVisionObjects** , essa classe agora deve estar vazia.

    > [!WARNING]
    > É importante seguir atentamente a próxima instrução. Se você colocar as novas declarações de classe dentro da classe **CustomVisionObjects** , receberá erros de compilação no [capítulo 10](#chapter-10---create-the-imagecapture-class), informando que **AnalysisRootObject** e **BoundingBox** não foram encontrados.

5.  Adicione as seguintes classes *fora* da classe **CustomVisionObjects** . Esses objetos são usados pela biblioteca **Newtonsoft** para serializar e desserializar os dados de resposta:

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

6.  Certifique-se de salvar as alterações no **Visual Studio**antes de retornar ao **Unity**.

## <a name="chapter-7---create-the-spatialmapping-class"></a>Capítulo 7-criar a classe SpatialMapping

Essa classe definirá o **conflito de mapeamento espacial** na cena para que seja possível detectar colisões entre objetos virtuais e objetos reais.

Para criar esta classe:

1.  Clique com o botão direito do mouse na pasta **scripts** e clique em **criar** > **script C\#** . Chame o script **SpatialMapping.**

2.  Clique duas vezes no novo script **SpatialMapping** para abri-lo com o **Visual Studio.**

3.  Verifique se você tem os seguintes namespaces referenciados acima da classe **SpatialMapping** :

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  Em seguida, adicione as seguintes variáveis dentro da classe **SpatialMapping** , acima do método **Start ()** :

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

5.  Adicione o **ativo ()** e o **início ()** :

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

6.  Exclua o método **Update ()** .

7.  Certifique-se de salvar as alterações no **Visual Studio**antes de retornar ao **Unity**.


## <a name="chapter-8---create-the-gazecursor-class"></a>Capítulo 8-criar a classe GazeCursor

Essa classe é responsável por configurar o cursor no local correto em espaço real, fazendo uso do **SpatialMappingCollider**, criado no capítulo anterior.

Para criar esta classe:

1.  Clique com o botão direito do mouse na pasta **scripts** e clique em **criar** > **script C\#** . Chamar o script **GazeCursor**

2.  Clique duas vezes no novo script **GazeCursor** para abri-lo com o **Visual Studio.**

3.  Verifique se você tem o seguinte namespace mencionado acima da classe **GazeCursor** :

    ```csharp
    using UnityEngine;
    ```

4.  Em seguida, adicione a seguinte variável dentro da classe **GazeCursor** , acima do método **Start ()** . 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Atualize o método **Start ()** com o seguinte código:

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

6.  Atualize o método **Update ()** com o seguinte código:

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
    > Não se preocupe com o erro para a classe **SceneOrganiser** não ser encontrada, você a criará no próximo capítulo.

7. Certifique-se de salvar as alterações no **Visual Studio**antes de retornar ao **Unity**.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Capítulo 9-criar a classe SceneOrganiser

Essa classe irá:

-   Configure a *câmera principal* anexando os componentes apropriados a ela.

-   Quando um objeto é detectado, ele será responsável por calcular sua posição no mundo real e colocar um rótulo de **marca** próximo a ele com o **nome de marca**apropriado.    

Para criar esta classe:

1.  Clique com o botão direito do mouse na pasta **scripts** e clique em **criar** > **script C\#** . Nomeie o script **SceneOrganiser**.

2.  Clique duas vezes no novo script **SceneOrganiser** para abri-lo com o **Visual Studio.**

3.  Verifique se você tem os seguintes namespaces referenciados acima da classe **SceneOrganiser** :

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  Em seguida, adicione as seguintes variáveis dentro da classe **SceneOrganiser** , acima do método **Start ()** :

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

5.  Exclua os métodos **Start ()** e **Update ()** .

6.  Sob as variáveis, adicione o método **ativo ()** , que irá inicializar a classe e configurar a cena.

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

7.  Adicione o método **PlaceAnalysisLabel ()** , que criará *uma instância* do rótulo na cena (que, neste ponto, é invisível para o usuário). Ele também coloca o quad (também invisível) em que a imagem é colocada e se sobrepõe ao mundo real. Isso é importante porque as coordenadas de caixa recuperadas do serviço após a análise são rastreadas de volta para esse Quad para determinar o local aproximado do objeto no mundo real. 

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

8.  Adicione o método **FinaliseLabel ()** . É responsável por:

    *   Definindo o texto do *rótulo* com a *marca* da previsão com a maior confiança.
    *   Chamar o cálculo da *caixa* delimitadora no objeto Quad, posicionado anteriormente e colocar o rótulo na cena.
    *   Ajuste da profundidade do rótulo usando um Raycast em direção à *caixa*delimitadora, que deve colidir com o objeto no mundo real.
    * Redefinição do processo de captura para permitir que o usuário Capture outra imagem.

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

9.  Adicione o método **CalculateBoundingBoxPosition ()** , que hospeda vários cálculos necessários para converter as coordenadas da *caixa* delimitadora recuperadas do serviço e recriá-las proporcionalmente no Quad.

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

10. Certifique-se de salvar as alterações no **Visual Studio**antes de retornar ao **Unity**.

    > [!IMPORTANT]
    > Antes de continuar, abra a classe **CustomVisionAnalyser** e, dentro do método **AnalyseLastImageCaptured ()** , *remova os comentários* das seguintes linhas:
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
> Não se preocupe com a mensagem "não foi possível encontrar a classe **ImageCapture** ", você a criará no próximo capítulo.


## <a name="chapter-10---create-the-imagecapture-class"></a>Capítulo 10 – criar a classe ImageCapture

A próxima classe que você vai criar é a classe **ImageCapture** .

Essa classe é responsável por:

*   Capturando uma imagem usando a câmera do HoloLens e armazenando-a na pasta do *aplicativo* .
*   Lidando com gestos de *toque* do usuário.

Para criar esta classe:

1.  Vá para a pasta **scripts** que você criou anteriormente.

2.  Clique com o botão direito do mouse dentro da pasta e clique em **criar** > **script C\#** . Nomeie o script **ImageCapture**.

3.  Clique duas vezes no novo script **ImageCapture** para abri-lo com o **Visual Studio.**

4.  Substitua os namespaces na parte superior do arquivo pelo seguinte:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro da classe **ImageCapture** , acima do método **Start ()** :

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

6.  O código para os métodos **ativo ()** e **Iniciar ()** agora precisa ser adicionado:

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

7.  Implemente um manipulador que será chamado quando ocorrer um gesto de toque:

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
    > Quando o cursor estiver **verde**, isso significa que a câmera está disponível para tirar a imagem. Quando o cursor estiver **vermelho**, significa que a câmera está ocupada.

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

9.  Adicione os manipuladores que serão chamados quando a foto tiver sido capturada e quando ela estiver pronta para ser analisada. O resultado é passado para o **CustomVisionAnalyser** para análise.

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

10. Certifique-se de salvar as alterações no **Visual Studio**antes de retornar ao **Unity**.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Capítulo 11-Configurando os scripts na cena

Agora que você escreveu todo o código necessário para esse projeto, é hora de configurar os scripts na cena e, no pré-fabricados, para que eles se comportem corretamente.

1.  No **Editor do Unity**, no **painel hierarquia**, selecione a **câmera principal**.
2.  No **painel Inspetor**, com a **câmera principal** selecionada, clique em **Adicionar componente**, em seguida, procure o script **SceneOrganiser** e clique duas vezes para adicioná-lo.

    ![](images/AzureLabs-Lab310-38.png)

3.  No **painel Projeto**, abra a **pasta pré-fabricados**, arraste o **rótulo** pré-fabricado para a área de entrada destino de referência vazia do *rótulo* , no script **SceneOrganiser** que você acabou de adicionar à *câmera principal*, conforme mostrado na a imagem abaixo:

    ![](images/AzureLabs-Lab310-39.png)

4.  No **painel hierarquia**, selecione o filho **GazeCursor** da **câmera principal**.
5.  No **painel Inspetor**, com o **GazeCursor** selecionado, clique em **Adicionar componente**, em seguida, pesquise por **GazeCursor** script e clique duas vezes para adicioná-lo.

    ![](images/AzureLabs-Lab310-40.png)

6.  Novamente, no **painel hierarquia**, selecione o filho **SpatialMapping** da **câmera principal**.
7.  No **painel Inspetor**, com o **SpatialMapping** selecionado, clique em **Adicionar componente**, em seguida, pesquise por **SpatialMapping** script e clique duas vezes para adicioná-lo.

    ![](images/AzureLabs-Lab310-41.png)

Os scripts restantes que você não tiver definido serão adicionados pelo código no script **SceneOrganiser** , durante o tempo de execução.

## <a name="chapter-12---before-building"></a>Capítulo 12 – antes de Compilar

Para executar um teste completo de seu aplicativo, você precisará Sideload-lo no Microsoft HoloLens.

Antes de fazer isso, verifique se:

-  Todas as configurações mencionadas no [capítulo 3](#chapter-3---set-up-the-unity-project) estão definidas corretamente.
- O script **SceneOrganiser** é anexado ao objeto da **câmera principal** .
- O script **GazeCursor** é anexado ao objeto **GazeCursor** .
- O script **SpatialMapping** é anexado ao objeto **SpatialMapping** .
- No [capítulo 5](#chapter-5---create-the-customvisionanalyser-class), etapa 6:

    - Certifique-se de inserir sua **chave de previsão de serviço** na variável **predictionKey** .
    - Você inseriu o **ponto de extremidade de previsão** na classe **predictionEndpoint** .

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Capítulo 13-criar a solução UWP e Sideload seu aplicativo

Agora você está pronto para compilar seu aplicativo como uma solução UWP que você poderá implantar no Microsoft HoloLens. Para iniciar o processo de compilação:

1.  Vá para **arquivo > configurações de Build**.

2.  **Projetos em tique\# Unity C**.

3.  Clique em **Adicionar cenas de abertura**. Isso adicionará a cena aberta no momento à compilação.

    ![](images/AzureLabs-Lab310-42.png)

4.  Clique em **Compilar**. O Unity iniciará uma janela *Explorador de arquivos* , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado. Crie essa pasta agora e nomeie-a como **aplicativo**. Em seguida, com a pasta de **aplicativo** selecionada, clique em **Selecionar pasta**.

5.  O Unity começará a criar seu projeto na pasta do **aplicativo** .

6.  Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).

7.  Para implantar o no Microsoft HoloLens, você precisará do endereço IP desse dispositivo (para implantação remota) e para garantir que ele também tenha o **modo de desenvolvedor** definido. Para fazer isso:

    1.  Enquanto estiver desgastando seu HoloLens, abra as **configurações**.

    2.  Vá para **rede &**  > **Opções avançadas** **de Internet Wi-Fi** > 

    3.  Anote o endereço **IPv4** .

    4.  Em seguida, navegue de volta para **configurações**e, em seguida, para **Atualizar & segurança** > **para desenvolvedores**

    5.  Defina o **modo de desenvolvedor** *em*.

8.  Navegue até sua nova compilação do Unity (a pasta do **aplicativo** ) e abra o arquivo de solução com o **Visual Studio**.

9.  Na configuração da solução, selecione **depurar**.

10. Na plataforma da solução, selecione **x86, computador remoto**. Você será solicitado a inserir o **endereço IP** de um dispositivo remoto (o Microsoft HoloLens, neste caso, que você anotou).

    ![](images/AzureLabs-Lab310-43.png)

11. Vá para o menu **Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu HoloLens.

12. Seu aplicativo agora deve aparecer na lista de aplicativos instalados no Microsoft HoloLens, pronto para ser iniciado!

### <a name="to-use-the-application"></a>Para usar o aplicativo:

* Examine um objeto, que você tem treinado com sua **serviço de visão personalizada do Azure, detecção de objetos**e use o **gesto de toque**.
* Se o objeto for detectado com êxito, um *texto de rótulo* de espaço mundial será exibido com o nome da marca.

> [!IMPORTANT]
> Sempre que você captura uma foto e a envia para o serviço, pode voltar para a página de serviço e treinar novamente o serviço com as imagens recentemente capturadas. No início, você provavelmente também precisará corrigir as *caixas* delimitadores para ser mais preciso e treinar novamente o serviço.

> [!NOTE]
> O texto do rótulo colocado pode não aparecer próximo ao objeto quando os sensores do Microsoft HoloLens e/ou o SpatialTrackingComponent no Unity falharem em colocar os colisor apropriados, em relação aos objetos do mundo real. Tente usar o aplicativo em uma superfície diferente, se esse for o caso.

## <a name="your-custom-vision-object-detection-application"></a>Seu Visão Personalizada, aplicativo de detecção de objeto

Parabéns, você criou um aplicativo de realidade misturada que aproveita o Visão Personalizada do Azure, a API de detecção de objeto, que pode reconhecer um objeto de uma imagem e, em seguida, fornecer uma posição aproximada para esse objeto no espaço 3D.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Adicionando ao rótulo de texto, use um cubo semitransparente para encapsular o objeto real em uma *caixa*delimitadora 3D.

### <a name="exercise-2"></a>Exercício 2

Treine sua Serviço de Visão Personalizada para reconhecer mais objetos.

### <a name="exercise-3"></a>Exercício 3

Tocar um som quando um objeto for reconhecido.

### <a name="exercise-4"></a>Exercício 4

Use a API para treinar novamente seu serviço com as mesmas imagens que seu aplicativo está analisando, para tornar o serviço mais preciso (faça a previsão e o treinamento simultaneamente).
