---
title: MR e Azure 304 - reconhecimento facial
description: Conclua este curso para aprender a implementar o reconhecimento de Face do Azure dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, misto realidade, academy, unity, tutorial, api, o reconhecimento, hololens, vr de imersão, facial
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590741"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>MR e o Azure 304: Reconhecimento facial

![resultado de concluírem este curso](images/AzureLabs-Lab4-00.png)

Neste curso você aprenderá como adicionar recursos de reconhecimento de face a um aplicativo de realidade misturada, usando serviços Cognitivos do Azure, com a API de detecção facial da Microsoft.

*API de detecção facial do Azure* é um serviço da Microsoft, que fornece aos desenvolvedores com os algoritmos mais avançados de detecção facial, tudo na nuvem. O *API de detecção facial* tem duas funções principais: detecção com atributos facial e reconhecimento facial. Isso permite que os desenvolvedores simplesmente definir um conjunto de grupos de rostos e, em seguida, enviar imagens de consulta para o serviço posteriormente, para determinar à qual pertence uma face. Para obter mais informações, visite o [página de reconhecimento de Face Azure](https://azure.microsoft.com/services/cognitive-services/face/).

Com a conclusão deste curso, você terá uma realidade misturada aplicativo HoloLens, que será capaz de fazer o seguinte:

1. Use uma **gestos de toque** para iniciar a captura de uma imagem usando a câmera HoloLens integrada. 
2. Enviar a imagem capturada para o *API de detecção facial Azure* service.
3. Receber os resultados do *API de detecção facial* algoritmo.
4. Use uma Interface de usuário simples, para exibir o nome das pessoas correspondentes.

Isso irá ensiná-lo como obter os resultados do serviço de API de detecção facial em seu aplicativo de realidade misturada com base no Unity.

Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design. Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity. Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> MR e o Azure 304: Reconhecimento facial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Enquanto este curso se concentra principalmente em HoloLens, você também pode aplicar o que você aprenderá neste curso para fones de ouvido Windows Mixed Reality de imersão (VR). Como fones imersivos em exposição (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu computador. Como acompanhar o curso, você verá notas quaisquer alterações que você talvez precise ser empregadas para dar suporte a fones imersivos em exposição (VR).

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#. Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018). Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .

Recomendamos que o hardware e software para este curso a seguir:

- Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md)
- [O SDK mais recente do Windows 10](install-the-tools.md)
- [2017.4 do Unity](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado
- Uma câmera conectada ao seu PC (para desenvolvimento imersivo fone de ouvido)
- Acesso à Internet para a instalação do Azure e a recuperação de API de detecção facial

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).
2.  Configurar e testar o HoloLens. Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  É uma boa ideia executar calibragem e ajuste de Sensor ao começar a desenvolver um new App HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).

Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1 - Portal do Azure

Para usar o *API de detecção facial* serviço no Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo.

1.  Primeiro, faça logon na [Portal do Azure](https://portal.azure.com). 

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, você precisará criá-lo. Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.

2.  Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure *API de detecção facial*, pressione **Enter**.

    ![Pesquisar para api de detecção facial](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.

3.  A nova página fornecerá uma descrição do *API de detecção facial* service. Na parte inferior esquerda desse prompt, selecione a **criar** botão para criar uma associação com este serviço.

    ![enfrentam informações da api](images/AzureLabs-Lab4-02.png)

4.  Depois de clicar em **criar**:

    1. Insira o nome desejado para esta instância de serviço.

    2. Selecione uma assinatura.

    3. Selecione o tipo de preço apropriado para você, se esta for a primeira hora de criar uma *serviço de API de detecção facial*, uma camada gratuita (chamada F0) deve estar disponível para você.

    4. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. O aplicativo UWP **pessoa Maker**, que você usará mais tarde, requer o uso de 'Oeste dos Estados Unidos' para o local.

    6. Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.

    7. Selecione **criar *.**

        ![Criar enfrentam o serviço de api](images/AzureLabs-Lab4-03.png)

5.  Depois de clicar em **criar *** você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal depois que a instância do serviço é criada.

    ![notificação de criação de serviço](images/AzureLabs-Lab4-04.png)

7.  Clique em notificações para explorar a nova instância do serviço.

    ![Vá para a notificação do recurso](images/AzureLabs-Lab4-05.png)

8.  Quando você estiver pronto, clique em **ir para o recurso** botão na notificação para explorar a nova instância do serviço.

    ![acesso enfrentam chaves de api](images/AzureLabs-Lab4-06.png)

9.  Dentro deste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, que é feito por meio de assinatura do serviço 'key'. Do *início rápido* página, de seu *API de detecção facial* de serviço, o primeiro ponto é o número 1, para *pegue suas chaves.*

10. No *serviço* página selecionar qualquer um dos azul **chaves** hiperlink (se estiver na página de início rápido), ou o **chaves** link no menu de navegação de serviços (à esquerda, indicada pelo ' chave ' ícone), para revelar as chaves.

    > [!NOTE] 
    > Tome nota de qualquer um das chaves e protegê-lo, pois você precisará dele mais tarde.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Capítulo 2 - usando o aplicativo UWP de 'Person Maker'

Certifique-se de baixar o aplicativo de UWP predefinidos chamados [pessoa Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip). Este aplicativo não é o produto final deste curso, uma simples ferramenta para ajudá-lo a criar suas entradas do Azure, que contarão com o projeto posterior.

**Criador de pessoa** permite que você crie entradas do Azure, que estão associadas com pessoas e grupos de pessoas. O aplicativo coloca as informações necessárias em um formato que pode então ser usado posteriormente por FaceAPI, para reconhecer os rostos de pessoas com quem você adicionou. 

> [IMPORTANTE] **Pessoa Maker** usa alguns limitação básica, para ajudar a garantir que você não exceda o número de chamadas de serviço por minuto para o **nível de assinatura gratuita**. O texto verde na parte superior irá mudar para vermelho e atualizar como 'Ativo' quando a limitação está ocorrendo; Se esse for o caso, simplesmente Aguarde para o aplicativo (ele aguardará até que ele em seguida pode continuar a acessar o serviço de detecção facial, a atualização como 'Ativa em' quando você pode usá-lo novamente).

Esse aplicativo usa o *Microsoft.ProjectOxford.Face* usam de bibliotecas, o que permitirá que você faça completa da API de detecção facial. Essa biblioteca está disponível gratuitamente como um pacote do NuGet. Para obter mais informações sobre isso e é semelhante, as APIs [Certifique-se de visitar o artigo de referência de API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).

> [!NOTE] 
> São apenas as etapas necessárias, mais adiante o documento de instruções sobre como fazer essas coisas. O **pessoa Maker** aplicativo permitirá que você:
>
> - Criar uma *grupo de pessoas*, que é composto de um grupo de várias pessoas que você deseja associar a ele. Com sua conta do Azure, você pode hospedar vários grupos de pessoas.
>
> - Criar uma *pessoa*, que é um membro de um grupo de pessoas. Cada pessoa tem inúmeras *Face* imagens associadas a ele.
>
> -  Atribua *enfrentam imagens* para um *pessoa*, para permitir que o serviço de API do Azure Face reconhecer um *pessoa* por correspondente *face*.
>
> -  *Treinar* sua *Azure enfrentam o serviço de API*.

Lembre-se, portanto, para treinar esse aplicativo para reconhecer pessoas, você terá dez (10) fotos aproximadas de cada pessoa que você deseja adicionar ao seu grupo de pessoas. O aplicativo do Windows 10 Cam pode ajudar você a tirá-las. Você deve garantir que cada foto é clara (Evite desfoque, ocultando ou sendo muito longe, da entidade), têm a foto no formato de arquivo jpg ou png, com o tamanho do arquivo de imagem que está sendo não deve exceder **4MB**e não menos do que **1 KB**.

> [!NOTE]
> Se você estiver seguindo este tutorial, não use seu próprio face para treinamento, pois quando você coloca o HoloLens, você não pode examinar por conta própria. Use a face de um amigo ou colega aluno.

Executando **pessoa Maker**:

1.  Abra o **PersonMaker** pasta e clique duas vezes no *solução PersonMaker* para abri-lo com *Visual Studio*.

2.  Uma vez a *PersonMaker solução* estiver aberto, certifique-se de que:

    1. O *configuração da solução* é definido como **depurar**.

    2. O *plataforma da solução* é definido como **x86**

    3. O *plataforma de destino* é **Máquina Local**.

    4.  Você também precisará *restaurar pacotes NuGet* (com o botão direito do *solução* e selecione **restaurar pacotes do NuGet**).

3.  Clique em *computador Local* e o aplicativo será iniciado. Lembre-se em telas menores, todo o conteúdo pode não estar visível, embora você pode rolar mais adiante para exibi-lo.

    ![interface de usuário do criador de pessoa](images/AzureLabs-Lab4-07.png)

4.  Insira sua **chave de autenticação do Azure**, que você deve ter, de seu *API de detecção facial* serviço dentro do Azure.

5.  Inserir:

    1. O *identificação* você deseja atribuir à *grupo de pessoas*. A ID deve ser em letras minúsculas, sem espaços. Anote essa ID, pois ela será necessária posteriormente no seu projeto do Unity.
    2. O *nome* você deseja atribuir à *grupo de pessoas* (pode ter espaços).


6.  Pressione **criar grupo de pessoas** botão. Uma mensagem de confirmação deve aparecer abaixo do botão.

> [!NOTE]
> Se você tiver um erro "Acesso negado", verifique o local em que você definiu para o serviço do Azure. Como mencionado acima, este aplicativo foi projetado para 'Oeste dos Estados Unidos'.

> [!IMPORTANT]
> Você observará que também é possível clicar o **buscar um grupo conhecido** botão: isso é para se você já tiver criado uma pessoa, grupo e quiser usá-lo, em vez de criar um novo. Lembre-se, se você clicar *criar um grupo de pessoas* com um grupo conhecido, isso também buscará um grupo.

7.  Insira o *nome* da *pessoa* você deseja criar.

    1. Clique o **pessoa crie** botão.

    2. Uma mensagem de confirmação deve aparecer abaixo do botão.

    3. Se você desejar excluir uma pessoa criou anteriormente, você pode escrever o nome na caixa de texto e pressione **excluir pessoa**

8.  Verifique se que você souber o local de dez (10) fotos da pessoa que você deseja adicionar ao seu grupo.

9.  Pressione **criar e abrir pasta** para abrir o Windows Explorer para a pasta associada à pessoa. Adicione as imagens de dez (10) na pasta. Elas devem ter *JPG* ou *PNG* formato de arquivo.

10. Clique em **enviar para o Azure**. Um contador mostra o estado de envio, seguido por uma mensagem quando ela for concluída.

11. Depois que o contador foi concluído e uma mensagem de confirmação foi exibida, clique em **treinar** para treinar seu serviço.

Quando o processo for concluído, você está pronto para passar para o Unity.

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3 - configurar o projeto do Unity

A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.

1.  Abra *Unity* e clique em **New**. 

    ![Inicie um novo projeto do Unity.](images/AzureLabs-Lab4-08.png)

2.  Agora, você precisará fornecer um nome de projeto do Unity. Inserir **MR_FaceRecognition**. Verifique se o tipo de projeto é definido como **3D**. Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab4-09.png)

3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Vá para **Editar > Preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

    ![Atualize as preferências do editor de script.](images/AzureLabs-Lab4-10.png)

4.  Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma **plataforma Universal do Windows**, clicando no **alternar plataforma** botão.

    ![Crie janela de configurações, alternar a plataforma para a UWP.](images/AzureLabs-Lab4-11.png)

5.  Vá para **arquivo > configurações de Build** e certifique-se de que:

    1. **Dispositivo de destino** é definido como **HoloLens**

        > Para os fones imersivos em exposição, defina **dispositivo de destino** à *qualquer dispositivo*.

    2. **Tipo de compilação** é definido como **D3D**
    3. **SDK** é definido como **mais recente instalada**
    4. **Versão do Visual Studio** é definido como **mais recente instalada**
    5. **Compilar e executar** é definido como **Máquina Local**
    6. Salve a cena e adicioná-lo para a compilação. 

        1. Fazer isso selecionando **cenas abra Adicionar**. Salvamento janela será exibida.

            ![Clique em Adicionar botão cenas aberto](images/AzureLabs-Lab4-12.png)

        2. Selecione o **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.

            ![Criar nova pasta de scripts](images/AzureLabs-Lab4-13.png)

        3. Abra seu recém-criado **cenas** pasta e, em seguida, no **nome do arquivo**: campo de texto, digite **FaceRecScene**, em seguida, pressione **salvar**.

            ![Dê um nome de nova cena.](images/AzureLabs-Lab4-14.png)

    7. O restante de configurações, em *configurações de Build*, deverá ser deixado como padrão por enquanto.

6. No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado. 

    ![Abra configurações do player.](images/AzureLabs-Lab4-15.png)

7. Neste painel, algumas configurações precisam ser verificados:

    1. No **outras configurações** guia:

        1. **Criação de scripts** **versão de tempo de execução** deve ser **Experimental** (equivalente ao .NET 4.6). Essa alteração irá disparar uma necessidade de reiniciar o Editor.
        2. **Script de back-end** deve ser **.NET**
        3. **Nível de compatibilidade de API** deve ser **.NET 4.6**

            ![Outras configurações de atualização.](images/AzureLabs-Lab4-16.png)
      
    2. Dentro de **configurações de publicação** guia, em **recursos**, verifique:

        - **InternetClient**
        - **Webcam**

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab4-17.png)

    3. Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.

        ![Atualize as configurações de R de X.](images/AzureLabs-Lab4-18.png)

8.  Volta *configurações de Build*, **Unity C# projetos** não fica acinzentado; marque a caixa de seleção ao lado disso. 
9.  Feche a janela de configurações de Build.
10. Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).

## <a name="chapter-4---main-camera-setup"></a>Capítulo 4 - instalação de câmera principal

> [!IMPORTANT]
> Se você quiser ignorar a *Unity configurar* componente deste curso e continuar diretamente no código, fique à vontade para [baixar esse unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importe-o para seu projeto como um [personalizado Pacote](https://docs.unity3d.com/Manual/AssetPackages.html). Lembre-se de que este pacote também inclui a importação do *DLL Newtonsoft*, abordada [capítulo 5](#chapter-5--import-the-newtonsoft.json-library). Com isso importado, você pode continuar de [capítulo 6](#chapter-6-create-the-faceanalysis-class).

1.  No *hierarquia* painel, selecione o **câmera principal**.

2.  Depois de selecionado, você poderá ver todos os componentes do **câmera principal** na *painel Inspetor*.

    1. O **objeto de câmera** deve ser nomeado **câmera principal** (Observe a ortografia!)

    2. A câmera principal **marca** deve ser definida como **MainCamera** (Observe a ortografia!)

    3. Verifique se o **transformar posição** é definido como **0, 0, 0**

    4. Definir **limpar os sinalizadores** para **cor sólida**

    5. Defina a **em segundo plano** cor do componente a câmera **preto, alfa 0 (Hex código: 00000000 #)**

        ![configurar os componentes de câmera](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Capítulo 5 – importar a biblioteca newtonsoft. JSON

> [!IMPORTANT]
> Se você tiver importado o unitypackage' ' na [último capítulo](#chapter-4--main-camera-setup), você pode ignorar este capítulo.

Para ajudá-lo a desserializam e serializam os objetos recebidos e enviados para o serviço de Bot, você precisa baixar o *newtonsoft. JSON* biblioteca. Você encontrará uma versão compatível já organizada com a estrutura de pastas do Unity correta desta [arquivo de pacote do Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage). 

Para importar a biblioteca:

1.  Baixe o pacote do Unity.
2.  Clique em **ativos**, **Importar pacote**, **pacote personalizado**.

    ![Importar a biblioteca newtonsoft. JSON](images/AzureLabs-Lab4-20.png)

3.  Procure o pacote do Unity que você baixou e clique em Abrir.
4.  Verifique se todos os componentes do pacote estão marcados e clique em **importação**.

    ![Importar a biblioteca newtonsoft. JSON](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Capítulo 6 - criar a classe FaceAnalysis

A finalidade da classe FaceAnalysis é hospedar os métodos necessários para se comunicar com o serviço de reconhecimento de Face do Azure. 

- Depois de enviar o serviço de uma imagem de captura, ele possam analisá-las e identificar as faces dentro e determinar se qualquer pertencem a uma pessoa conhecida. 
- Se uma pessoa conhecida for encontrada, essa classe exibirá seu nome como texto de interface do usuário na cena.

Para criar o *FaceAnalysis* classe:

 1. Clique com botão direito no *pasta ativos* localizado no painel de projeto, em seguida, clique em **Create** > **pasta**. Chame a pasta **Scripts**. 

    ![Crie a classe FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  Clique duas vezes na pasta recém-criada, para abri-lo. 
3.  Clique com botão direito dentro da pasta, clique em **Create**  >   **C# Script**. Chame o script *FaceAnalysis*. 
4.  Clique duas vezes na nova *FaceAnalysis* script para abri-lo com o Visual Studio 2017.
5.  Insira os seguintes namespaces acima de *FaceAnalysis* classe:

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  Agora você precisa adicionar todos os objetos que são usados para deserialising. Esses objetos precisam ser adicionados **fora** da *FaceAnalysis* script (sob a chave inferior). 

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
7. O *Start ()* e *Update ()* métodos não serão usadas, por isso, exclua-os agora. 

8.  Dentro de *FaceAnalysis* de classe, adicione as seguintes variáveis:

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
    > Substitua os **chave** e o **personGroupId** com sua chave de serviço e a Id do grupo que você criou anteriormente.

9.  Adicione a *Awake()* método, que initialises a classe, adicionando o *ImageCapture* classe para a câmera principal e chama o método de criação de rótulo:

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

10. Adicione a *CreateLabel()* método, que cria a *rótulo* objeto para exibir o resultado da análise:

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

11. Adicione a *DetectFacesFromImage()* e *GetImageAsByteArray()* método. O primeiro solicitará o serviço de reconhecimento de Face para detectar qualquer possível face na imagem enviada, enquanto o segundo é necessário para converter a imagem capturada em uma matriz de bytes:

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

12. Adicione a *IdentifyFaces()* método, que solicita a *serviço de reconhecimento de Face* para identificar qualquer face conhecido anteriormente detectado na imagem enviada. A solicitação retornará uma id da pessoa identificada, mas não o nome:

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

13. Adicione a *GetPerson()* método. Fornecendo a pessoa id, esse método e as solicitações para o *serviço de reconhecimento de Face* para retornar o nome da pessoa identificado:

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

14.  Lembre-se **salvar** as alterações antes de voltar ao Editor do Unity.
15.  No Editor do Unity, arraste o script FaceAnalysis da pasta Scripts no painel de projeto ao objeto de câmera principal na *painel de hierarquia*. O novo componente script será então, adicionado à câmera principal. 

![Coloque FaceAnalysis para a câmera principal](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Capítulo 7 - criar a classe ImageCapture

A finalidade do *ImageCapture* classe é hospedar os métodos necessários para se comunicar com seu *serviço de reconhecimento de Face do Azure* para analisar a imagem que vai capturar, identificando as faces nele e Determinando se ele pertence a uma pessoa conhecida. Se uma pessoa conhecida for encontrada, essa classe exibirá seu nome como texto de interface do usuário na cena.

Para criar o *ImageCapture* classe:
 
1.  Com o botão direito dentro de **Scripts** pasta você criou anteriormente e clique em **Create**,  **C# Script**. Chame o script *ImageCapture*. 
2.  Clique duas vezes na nova *ImageCapture* script para abri-lo com o Visual Studio 2017.
3.  Insira os seguintes namespaces acima da classe ImageCapture:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  Dentro de *ImageCapture* de classe, adicione as seguintes variáveis:

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

5.  Adicione a *Awake()* e *Start ()* métodos necessários para inicializar a classe e permitir que o HoloLens capturar os gestos do usuário:

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

6.  Adicione a *TapHandler()* que é chamado quando o usuário executa um *toque* gesto:

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

7.  Adicione a *ExecuteImageCaptureAndAnalysis()* método, que iniciará o processo de captura de imagem:

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

8.  Adicione os manipuladores que são chamados quando o processo de captura de foto for concluído:

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

9. Lembre-se **salvar** as alterações antes de voltar ao Editor do Unity.

## <a name="chapter-8---building-the-solution"></a>Capítulo 8 - Compilando a solução

Para executar um teste completo de seu aplicativo você precisará para fazer sideload dele para o HoloLens.

Antes de começar, verifique se:

-   Todas as configurações mencionadas no capítulo 3 estão definidas corretamente. 
-   O script *FaceAnalysis* está anexado ao objeto de câmera principal. 
-   Ambas as a **Auth Key** e **Id do grupo** tiver sido definida dentro a *FaceAnalysis* script.

Esse ponto você está pronto para compilar a solução. Depois que a solução foi criada, você estará pronto para implantar seu aplicativo.

Para iniciar o processo de compilação:

1.  Salve a cena atual clicando em arquivo, salvar.
2.  Ir para o arquivo de configurações de compilação, clique em Adicionar cenas aberto.
3.  Lembre-se de escala Unity C# projetos.

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  Pressione a compilação. Ao fazer isso, o Unity iniciará uma janela do Explorador de arquivos, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em. Criar pasta agora, dentro do projeto do Unity e chamá-lo o aplicativo. Em seguida, com a pasta do aplicativo, pressione Selecionar pasta. 
5.  Unity começará a compilar seu projeto para a pasta do aplicativo. 
6.  Uma vez Unity terminou de construção (pode levar algum tempo), ele abrirá uma janela do Explorador de arquivos no local de sua compilação.

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  Abra a pasta de aplicativo e, em seguida, abra a nova solução de projeto (como visto acima, MR_FaceRecognition.sln).


## <a name="chapter-9---deploying-your-application"></a>Capítulo 9 - implantação de seu aplicativo

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

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  Vá para o **menu Build** e clique em **implantar solução**, carregar o aplicativo para o HoloLens.
6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!

> [!NOTE]
> Para implantar o fone de ouvido imersivo, defina as **plataforma da solução** para *Máquina Local*e defina o **configuração** para *depurar*, com *x86* como o **plataforma**. Em seguida, implantar no local de máquina, usando o **menu Build**, selecionando *implantar solução*. 


## <a name="chapter-10---using-the-application"></a>Capítulo 10 - como usar o aplicativo

1.  Use o HoloLens, inicie o aplicativo.
2.  Examinar a pessoa que você registrou com o *API de detecção facial*. Certifique-se de que:

    -  Face da pessoa não está muito distante e claramente visíveis
    -  A iluminação ambiente não está muito escura

3.  Use o gesto de tocar para capturar a imagem da pessoa.
4.  Aguarde até que o aplicativo enviar a solicitação de análise e receber uma resposta.
5.  Se a pessoa que foi reconhecida com sucesso, o nome da pessoa será exibido como texto de interface do usuário.
6.  Você pode repetir o processo de captura usando o gesto de toque de alguns segundos.

## <a name="your-finished-azure-face-api-application"></a>Seu aplicativo de API de detecção facial do Azure concluída

Parabéns, você criou um aplicativo de realidade mista que aproveita o serviço de reconhecimento de Face do Azure para detectar faces dentro de uma imagem e identificar qualquer faces conhecidos.

![resultado de concluírem este curso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

O **API de detecção facial Azure** é poderoso o suficiente para detectar até 64 faces em uma única imagem. Estenda o aplicativo, para que ele poderia reconhece dois ou três faces, entre muitas outras pessoas.

### <a name="exercise-2"></a>Exercício 2

O **API de detecção facial Azure** também é capaz de realizar todos os tipos de informações de atributo. Integre isso ao aplicativo. Isso pode ser ainda mais interessante, quando combinado com o [API de emoções](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).
