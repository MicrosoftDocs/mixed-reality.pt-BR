---
title: Sr e Azure 304-reconhecimento facial
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, reconhecimento facial, hololens, imersão, VR
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63554472"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>Sr e Azure 304: Reconhecimento facial

![resultado da conclusão deste curso](images/AzureLabs-Lab4-00.png)

Neste curso, você aprenderá a adicionar recursos de reconhecimento facial a um aplicativo de realidade misturada, usando os serviços cognitivas do Azure, com o Microsoft API de Detecção Facial.

O *Azure API de detecção facial* é um serviço da Microsoft, que fornece aos desenvolvedores os algoritmos de face mais avançados, tudo na nuvem. O *API de detecção facial* tem duas funções principais: detecção facial com atributos e reconhecimento facial. Isso permite que os desenvolvedores simplesmente definam um conjunto de grupos para rostos e, em seguida, enviem imagens de consulta para o serviço posteriormente, para determinar a quem uma face pertence. Para obter mais informações, visite a [página de reconhecimento de face do Azure](https://azure.microsoft.com/services/cognitive-services/face/).

Após a conclusão deste curso, você terá um aplicativo de HoloLens de realidade misturada, que poderá fazer o seguinte:

1. Use um **gesto de toque** para iniciar a captura de uma imagem usando a câmera do HoloLens na placa. 
2. Envie a imagem capturada para o serviço de *API de detecção facial do Azure* .
3. Receba os resultados do algoritmo *API de detecção facial* .
4. Use uma interface do usuário simples para exibir o nome de pessoas correspondentes.

Isso ensinará a você como obter os resultados do serviço de API de Detecção Facial em seu aplicativo de realidade mista com base no Unity.

Em seu aplicativo, cabe a você como você integrará os resultados com seu design. Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity. É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Sr e Azure 304: Reconhecimento facial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Embora este curso se concentre principalmente no HoloLens, você também pode aplicar o que aprende neste curso a fones de ouvido (VR) de realidade mista do Windows. Como os headsets de imersão (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu PC. Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a headsets de imersão (VR).

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018). Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)
- [Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md)
- [O SDK do Windows 10 mais recente](install-the-tools.md)
- [Unity 2017,4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado
- Uma câmera conectada ao seu PC (para desenvolvimento de headsets de imersão)
- Acesso à Internet para a instalação do Azure e recuperação de API de Detecção Facial

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).
2.  Configure e teste seu HoloLens. Se você precisar de suporte para configurar seu HoloLens, [visite o artigo configuração do hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  É uma boa ideia executar a calibragem e o ajuste do sensor ao começar a desenvolver um novo aplicativo do HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

Para obter ajuda sobre calibragem, siga este [link para o artigo Calibration do HoloLens](calibration.md#hololens).

Para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste do sensor do HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1-o portal do Azure

Para usar o serviço de *API de detecção facial* no Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.

1.  Primeiro, faça logon no [portal do Azure](https://portal.azure.com). 

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure *API de detecção facial*, pressione **Enter**.

    ![Pesquisar API de detecção facial](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.

3.  A nova página fornecerá uma descrição do serviço *API de detecção facial* . Na parte inferior esquerda desse prompt, selecione o botão **criar** para criar uma associação com esse serviço.

    ![informações da API facial](images/AzureLabs-Lab4-02.png)

4.  Depois de clicar em **criar**:

    1. Insira o nome desejado para esta instância de serviço.

    2. Selecione uma assinatura.

    3. Selecione o tipo de preço apropriado para você, se esta for a primeira vez que criar um *serviço de API de detecção facial*, uma camada gratuita (chamada F0) deverá estar disponível para você.

    4. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. O aplicativo UWP, **criador de pessoas**, que você usa mais tarde, requer o uso de ' oeste dos EUA ' para o local.

    6. Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.

    7. Selecione **criar*.**

        ![Criar serviço de API facial](images/AzureLabs-Lab4-03.png)

5.  Depois de clicar em **criar*** você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![notificação de criação de serviço](images/AzureLabs-Lab4-04.png)

7.  Clique nas notificações para explorar sua nova instância de serviço.

    ![ir para notificação de recurso](images/AzureLabs-Lab4-05.png)

8.  Quando estiver pronto, clique no botão **ir para o recurso** na notificação para explorar sua nova instância de serviço.

    ![acessar chaves de API de face](images/AzureLabs-Lab4-06.png)

9.  Neste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, o que é feito por meio do uso da assinatura ' Key ' de seu serviço. Na página *início rápido* , do seu serviço de *API de detecção facial* , o primeiro ponto é o número 1, para *captar suas chaves.*

10. Na página *serviço* , selecione o hiperlink **teclas** azuis (se estiver na página início rápido) ou o link **chaves** no menu de navegação serviços (à esquerda, indicado pelo ícone "chave"), para revelar suas chaves.

    > [!NOTE] 
    > Anote qualquer uma das chaves e proteja-a, pois você precisará dela mais tarde.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Capítulo 2-usando o aplicativo UWP do ' criador de pessoas '

Certifique-se de baixar o aplicativo UWP pré-criado chamado [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip). Este aplicativo não é o produto final para este curso, apenas uma ferramenta para ajudá-lo a criar suas entradas do Azure, com as quais o projeto posterior dependerá.

O **criador** de pessoas permite que você crie entradas do Azure, que estão associadas a pessoas e grupos de pessoas. O aplicativo coloca todas as informações necessárias em um formato que, posteriormente, pode ser usado pelo FaceAPI para reconhecer as faces de pessoas que você adicionou. 

> FUNDAMENTAL O **criador de pessoas** usa uma limitação básica para ajudar a garantir que você não exceda o número de chamadas de serviço por minuto para a camada de **assinatura gratuita**. O texto verde na parte superior mudará para vermelho e será atualizado como ' ativo ' quando a limitação estiver acontecendo; Se esse for o caso, basta aguardar o aplicativo (ele aguardará até que possa continuar acessando o serviço de face, atualizando como ' IN-ACTIVE ' quando você puder usá-lo novamente).

Esse aplicativo usa as bibliotecas *Microsoft. ProjectOxford. facial* , que permitirão que você faça uso completo da API de detecção facial. Essa biblioteca está disponível gratuitamente como um pacote NuGet. Para obter mais informações sobre isso e APIs semelhantes, [visite o artigo de referência de API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).

> [!NOTE] 
> Essas são apenas as etapas necessárias, as instruções sobre como fazer essas coisas estão mais abaixo do documento. O aplicativo **Person Maker** lhe permitirá:
>
> - Crie um *grupo de pessoas*, que é um grupo composto por várias pessoas que você deseja associar a ela. Com sua conta do Azure, você pode hospedar vários grupos de pessoas.
>
> - Crie uma *pessoa*, que é um membro de um grupo de pessoas. Cada pessoa tem várias imagens de *face* associadas a ela.
>
> -  Atribua *imagens de face* a uma *pessoa*, para permitir que o serviço de API de detecção facial do Azure reconheça uma *pessoa* pela *face*correspondente.
>
> -  *Treine* seu *serviço de API de detecção facial do Azure*.

Lembre-se de que, para treinar esse aplicativo para reconhecer pessoas, você precisará de dez (10) fotos de fechamento de cada pessoa que deseja adicionar ao seu grupo de pessoas. O aplicativo de Cam do Windows 10 pode ajudá-lo a fazer isso. Você deve garantir que cada foto esteja clara (Evite desfocar, obscurecer ou estar muito longe, do assunto), ter a foto no formato de arquivo jpg ou png, com o tamanho do arquivo de imagem que não seja maior que **4 MB**e não seja menor que **1 KB**.

> [!NOTE]
> Se você estiver seguindo este tutorial, não use sua própria face para treinamento, como quando você coloca o HoloLens em, você não pode examinar por conta própria. Use a face de um colega ou colega de aluno.

**Criador de pessoas**em execução:

1.  Abra a pasta **PersonMaker** e clique duas vezes na *solução PersonMaker* para abri-la com o *Visual Studio*.

2.  Depois que a *solução PersonMaker* estiver aberta, verifique se:

    1. A *configuração da solução* está definida como **depurar**.

    2. A *plataforma da solução* está definida como **x86**

    3. A *plataforma de destino* é a **máquina local**.

    4.  Talvez você também precise *restaurar os pacotes NuGet* (clique com o botão direito do mouse na *solução* e selecione **restaurar pacotes NuGet**).

3.  Clique em *computador local* e o aplicativo será iniciado. Lembre-se de que, em telas menores, todo o conteúdo pode não estar visível, embora você possa rolar mais para baixo para exibi-lo.

    ![interface do usuário do criador de pessoas](images/AzureLabs-Lab4-07.png)

4.  Insira sua **chave de autenticação do Azure**, que você deve ter, do seu serviço de *API de detecção facial* no Azure.

5.  Inserido

    1. A *ID* que você deseja atribuir ao *grupo de pessoas*. A ID deve estar em minúsculas, sem espaços. Anote essa ID, pois ela será necessária mais tarde no seu projeto do Unity.
    2. O *nome* que você deseja atribuir ao *grupo de pessoas* (pode ter espaços).


6.  Pressione o botão **Criar grupo de pessoas** . Uma mensagem de confirmação deve aparecer abaixo do botão.

> [!NOTE]
> Se você tiver um erro de ' acesso negado ', verifique o local definido para o serviço do Azure. Conforme mencionado acima, este aplicativo foi projetado para o "oeste dos EUA".

> [!IMPORTANT]
> Você observará que também pode clicar no botão **buscar um grupo conhecido** : isso ocorrerá se você já tiver criado um grupo de pessoas e quiser usá-lo, em vez de criar um novo. Lembre-se de que, se você clicar em *criar um grupo de pessoas* com um grupo conhecido, isso também obterá um grupo.

7.  Insira o *nome* da *pessoa* que você deseja criar.

    1. Clique no botão **criar pessoa** .

    2. Uma mensagem de confirmação deve aparecer abaixo do botão.

    3. Se desejar excluir uma pessoa que você criou anteriormente, você poderá escrever o nome na caixa de texto e pressionar **excluir pessoa**

8.  Verifique se você sabe o local de dez (dez) fotos da pessoa que deseja adicionar ao seu grupo.

9.  Pressione **criar e abrir pasta** para abrir o Windows Explorer na pasta associada à pessoa. Adicione as dez (10) imagens na pasta. Eles devem ser do formato de arquivo *jpg* ou *png* .

10. Clique em **Enviar para o Azure**. Um contador mostrará o estado do envio, seguido por uma mensagem quando for concluído.

11. Depois que o contador for concluído e uma mensagem de confirmação for exibida, clique em **treinar** para treinar o serviço.

Depois que o processo for concluído, você estará pronto para passar para o Unity.

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3 – configurar o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra o *Unity* e clique em **novo**. 

    ![Inicie o novo projeto do Unity.](images/AzureLabs-Lab4-08.png)

2.  Agora, você precisará fornecer um nome de projeto de Unity. Insira **MR_FaceRecognition**. Verifique se o tipo de projeto está definido como **3D**. Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab4-09.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar preferências de >** e, em seguida, na nova janela, navegue até **Ferramentas externas**. Altere o **Editor de script externo** para o **Visual Studio 2017**. Feche a janela **preferências** .

    ![Atualize a preferência do editor de script.](images/AzureLabs-Lab4-10.png)

4.  Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma para **plataforma universal do Windows**clicando no botão **alternar plataforma** .

    ![Janela de configurações de compilação, alterne a plataforma para UWP.](images/AzureLabs-Lab4-11.png)

5.  Vá para **arquivo > configurações de compilação** e verifique se:

    1. O **dispositivo de destino** está definido como **HoloLens**

        > Para os headsets de imersão, defina **dispositivo de destino** para *qualquer dispositivo*.

    2. O **tipo de compilação** está definido como **D3D**
    3. O **SDK** está definido para o **mais recente instalado**
    4. A **versão do Visual Studio** está definida para o **mais recente instalado**
    5. **Compilar e executar** é definido como **computador local**
    6. Salve a cena e adicione-a à compilação. 

        1. Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.

            ![Clique no botão Adicionar cenas abertas](images/AzureLabs-Lab4-12.png)

        2. Selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![Criar nova pasta de scripts](images/AzureLabs-Lab4-13.png)

        3. Abra sua pasta de **cenas** recém-criada e, no campo **nome do arquivo**:, digite **FaceRecScene**e pressione **salvar**.

            ![Dê um nome à nova cena.](images/AzureLabs-Lab4-14.png)

    7. As configurações restantes, em *configurações de compilação*, devem ser deixadas como padrão por enquanto.

6. Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado. 

    ![Abra as configurações do Player.](images/AzureLabs-Lab4-15.png)

7. Nesse painel, algumas configurações precisam ser verificadas:

    1. Na guia **outras configurações** :

        1. **Criando scripts** A **versão de tempo de execução** deve ser **Experimental** (.NET 4,6 equivalente). Alterar isso irá disparar a necessidade de reiniciar o editor.
        2. O **back-end de script** deve ser **.net**
        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**

            ![Atualize outras configurações.](images/AzureLabs-Lab4-16.png)
      
    2. Na guia **configurações de publicação** , em **recursos**, marque:

        - **InternetClient**
        - **Integrada**

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab4-17.png)

    3. Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o SDK do **Windows Mixed Reality** foi adicionado.

        ![Atualize as configurações de X R.](images/AzureLabs-Lab4-18.png)

8.  De volta *às configurações de compilação*, os **projetos de C# Unity** não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste. 
9.  Feche a janela configurações de compilação.
10. Salve sua cena e projeto (**arquivo > salvar cena/arquivo > salvar projeto**).

## <a name="chapter-4---main-camera-setup"></a>Capítulo 4-configuração principal da câmera

> [!IMPORTANT]
> Se você quiser ignorar o componente de *configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para [baixar esse. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importe-o para seu projeto como um [pacote personalizado](https://docs.unity3d.com/Manual/AssetPackages.html). Lembre-se de que esse pacote também inclui a importação da *dll Newtonsoft*, abordada no [capítulo 5](#chapter-5--import-the-newtonsoft.json-library). Com isso importado, você pode continuar no [capítulo 6](#chapter-6-create-the-faceanalysis-class).

1.  No painel *hierarquia* , selecione a **câmera principal**.

2.  Depois de selecionado, você poderá ver todos os componentes da **câmera principal** no *painel Inspetor*.

    1. O **objeto de câmera** deve ser nomeado como a **câmera principal** (Observe a grafia!)

    2. A **marca** da câmera principal deve ser definida como **MainCamera** (Observe a ortografia!)

    3. Verifique se a **posição de transformação** está definida como **0, 0,** 0

    4. Definir **sinalizadores de limpeza** como **cor sólida**

    5. Defina a cor do **plano de fundo** do componente da câmera como **preto, alfa 0 (código hex: #00000000)**

        ![configurar componentes da câmera](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Capítulo 5 – importar a biblioteca Newtonsoft. JSON

> [!IMPORTANT]
> Se você importou o '. unitypackage ' no [último capítulo](#chapter-4--main-camera-setup), poderá ignorar este capítulo.

Para ajudá-lo a desserializar e serializar objetos recebidos e enviados ao serviço bot, você precisa baixar a biblioteca *Newtonsoft. JSON* . Você encontrará uma versão compatível já organizada com a estrutura de pasta do Unity correta neste [arquivo de pacote do Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage). 

Para importar a biblioteca:

1.  Baixe o pacote do Unity.
2.  Clique em **ativos**, **Importar pacote**, **pacote personalizado**.

    ![Importar a biblioteca Newtonsoft. JSON](images/AzureLabs-Lab4-20.png)

3.  Procure o pacote do Unity que você baixou e clique em abrir.
4.  Verifique se todos os componentes do pacote estão com tique e clique em **importar**.

    ![Importar a biblioteca Newtonsoft. JSON](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Capítulo 6-criar a classe FaceAnalysis

A finalidade da classe FaceAnalysis é hospedar os métodos necessários para se comunicar com o serviço de reconhecimento de face do Azure. 

- Depois de enviar a imagem de captura do serviço, ela a analisará e identificará as faces dentro e determinará se alguém pertence a uma pessoa conhecida. 
- Se uma pessoa conhecida for encontrada, essa classe exibirá seu nome como texto da interface do usuário na cena.

Para criar a classe *FaceAnalysis* :

 1. Clique com o botão direito do mouse na *pasta ativos* , localizada no painel projeto, e clique em **criar** > **pasta**. Chame os **scripts**da pasta. 

    ![Crie a classe FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  Clique duas vezes na pasta recém-criada para abri-la. 
3.  Clique com o botão direito do mouse dentro da pasta e clique em **criar**  >   **C# script**. Chame o script *FaceAnalysis*. 
4.  Clique duas vezes no novo script *FaceAnalysis* para abri-lo com o Visual Studio 2017.
5.  Insira os seguintes namespaces acima da classe *FaceAnalysis* :

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  Agora você precisa adicionar todos os objetos que são usados para deserialising. Esses objetos precisam ser adicionados **fora** do script *FaceAnalysis* (abaixo da chave inferior). 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. Os métodos *Start ()* e *Update ()* não serão usados, portanto, exclua-os agora. 

8.  Dentro da classe *FaceAnalysis* , adicione as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > Substitua a **chave** e o **PersonGroupId** pela sua chave de serviço e a ID do grupo que você criou anteriormente.

9.  Adicione o método *ativo ()* , que initialises a classe, adicionando a classe *ImageCapture* à câmera principal e chama o método de criação de rótulo:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. Adicione o método *CreateLabel ()* , que cria o objeto *Label* para exibir o resultado da análise:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. Adicione o método *DetectFacesFromImage ()* e *GetImageAsByteArray ()* . O primeiro solicitará que o serviço de reconhecimento facial detecte qualquer face possível na imagem enviada, enquanto o último é necessário para converter a imagem capturada em uma matriz de bytes:

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. Adicione o método *IdentifyFaces ()* , que solicita que o *serviço de reconhecimento facial* identifique qualquer face conhecida detectada anteriormente na imagem enviada. A solicitação retornará uma ID da pessoa identificada, mas não o nome:

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. Adicione o método *GetPerson ()* . Ao fornecer a ID Person, esse método solicita que o *serviço de reconhecimento facial* retorne o nome da pessoa identificada:

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  Lembre-se de **salvar** as alterações antes de voltar para o editor do Unity.
15.  No editor do Unity, arraste o script FaceAnalysis da pasta scripts no painel projeto para o objeto da câmera principal no *painel hierarquia*. O novo componente de script será tão adicionado à câmera principal. 

![Coloque FaceAnalysis na câmera principal](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Capítulo 7-criar a classe ImageCapture

A finalidade da classe *ImageCapture* é hospedar os métodos necessários para se comunicar com o *serviço de reconhecimento de face do Azure* para analisar a imagem que será capturada, identificando as faces e determinando se ela pertence a uma pessoa conhecida. Se uma pessoa conhecida for encontrada, essa classe exibirá seu nome como texto da interface do usuário na cena.

Para criar a classe *ImageCapture* :
 
1.  Clique com o botão direito do mouse na pasta **scripts** que você criou anteriormente e, em seguida, clique em **criar**,  **C# script**. Chame o script *ImageCapture*. 
2.  Clique duas vezes no novo script *ImageCapture* para abri-lo com o Visual Studio 2017.
3.  Insira os seguintes namespaces acima da classe ImageCapture:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  Dentro da classe *ImageCapture* , adicione as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  Adicione os métodos *ativo ()* e *Iniciar ()* necessários para inicializar a classe e permitir que o HoloLens capture os gestos do usuário:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  Adicione o *TapHandler ()* que é chamado quando o usuário executa um gesto de *toque* :

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  Adicione o método *ExecuteImageCaptureAndAnalysis ()* , que iniciará o processo de captura de imagem:

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  Adicione os manipuladores que são chamados quando o processo de captura de foto foi concluído:

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. Lembre-se de **salvar** as alterações antes de voltar para o editor do Unity.

## <a name="chapter-8---building-the-solution"></a>Capítulo 8-criando a solução

Para executar um teste completo de seu aplicativo, você precisará Sideload-lo no seu HoloLens.

Antes de fazer isso, verifique se:

-   Todas as configurações mencionadas no capítulo 3 estão definidas corretamente. 
-   O script *FaceAnalysis* é anexado ao objeto da câmera principal. 
-   A **chave de autenticação** e a **ID do grupo** foram definidas no script *FaceAnalysis* .

R neste ponto você está pronto para criar a solução. Depois que a solução tiver sido criada, você estará pronto para implantar seu aplicativo.

Para iniciar o processo de compilação:

1.  Salve a cena atual clicando em arquivo, salvar.
2.  Vá para arquivo, configurações de compilação, clique em Adicionar cenas de abertura.
3.  Certifique-se de que C# os projetos de Unity em escala.

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  Pressione compilar. Ao fazer isso, o Unity iniciará uma janela Explorador de arquivos, onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado. Crie essa pasta agora, dentro do projeto do Unity, e chame-a de App. Em seguida, com a pasta de aplicativo selecionada, pressione Selecionar pasta. 
5.  O Unity começará a compilar seu projeto, na pasta do aplicativo. 
6.  Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do explorador de arquivos no local de sua compilação.

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  Abra a pasta do aplicativo e, em seguida, abra a nova solução de projeto (como visto acima, MR_FaceRecognition. sln).


## <a name="chapter-9---deploying-your-application"></a>Capítulo 9-implantando seu aplicativo

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

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  Vá para o **menu Compilar** e clique em **implantar solução**para Sideload o aplicativo ao seu HoloLens.
6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!

> [!NOTE]
> Para implantar em headsets de imersão, defina a **plataforma da solução** como *computador local*e defina a **configuração** a ser depurada, com *x86* como a **plataforma**. Em seguida, implante no computador local, usando o **menu Compilar**, selecionando *implantar solução*. 


## <a name="chapter-10---using-the-application"></a>Capítulo 10-usando o aplicativo

1.  Desgastando o HoloLens, inicie o aplicativo.
2.  Examine a pessoa que você registrou com o *API de detecção facial*. Certifique-se de que:

    -  A face da pessoa não está muito distante e claramente visível
    -  A iluminação do ambiente não é muito escura

3.  Use o gesto de toque para capturar a imagem da pessoa.
4.  Aguarde até que o aplicativo envie a solicitação de análise e receba uma resposta.
5.  Se a pessoa tiver sido reconhecida com êxito, o nome da pessoa aparecerá como texto da interface do usuário.
6.  Você pode repetir o processo de captura usando o gesto de toque a cada poucos segundos.

## <a name="your-finished-azure-face-api-application"></a>Seu aplicativo de API de Detecção Facial do Azure concluído

Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço de reconhecimento de face do Azure para detectar rostos em uma imagem e identificar quaisquer faces conhecidas.

![resultado da conclusão deste curso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

A **API de detecção facial do Azure** é eficiente o suficiente para detectar até 64 rostos em uma única imagem. Estenda o aplicativo para que ele possa reconhecer duas ou três faces, entre muitas outras pessoas.

### <a name="exercise-2"></a>Exercício 2

O **API de detecção facial do Azure** também é capaz de fornecer de volta todos os tipos de informações de atributo. Integre-o ao aplicativo. Isso pode ser ainda mais interessante, quando combinado com o [API de detecção de emoções](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).
