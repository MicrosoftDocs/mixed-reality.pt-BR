---
title: Sr e Azure 311-Microsoft Graph
description: Conclua este curso para aprender a aproveitar Microsoft Graph e conectar-se aos dados que impulsionam a produtividade, em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, Microsoft Graph, hololens, imersão, VR
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694523"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

# <a name="mr-and-azure-311---microsoft-graph"></a>Sr e Azure 311-Microsoft Graph

Neste curso, você aprenderá a usar o *Microsoft Graph* para fazer logon em seu conta Microsoft usando a autenticação segura em um aplicativo de realidade misturada. Em seguida, você irá recuperar e exibir suas reuniões agendadas na interface do aplicativo.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* é um conjunto de APIs criadas para permitir o acesso a muitos dos serviços da Microsoft. A Microsoft descreve Microsoft Graph como sendo uma matriz de recursos conectados por relações, o que significa que ele permite que um aplicativo acesse todos os tipos de dados de usuário conectados. Para obter mais informações, visite a [página Microsoft Graph](https://developer.microsoft.com/graph).

O desenvolvimento incluirá a criação de um aplicativo no qual o usuário será instruído a olhar e, em seguida, tocará em uma esfera, que solicitará que o usuário faça logon com segurança em um conta Microsoft. Depois de conectado à sua conta, o usuário poderá ver uma lista de reuniões agendadas para o dia.

Após a conclusão deste curso, você terá um aplicativo de HoloLens de realidade misturada, que poderá fazer o seguinte:

1.  Usando o gesto de toque, toque em um objeto, que solicitará que o usuário faça logon em uma conta da Microsoft (saindo do aplicativo para fazer logon e, em seguida, volte para o aplicativo novamente).
2.  Exiba uma lista de reuniões agendadas para o dia. 

Em seu aplicativo, cabe a você como você integrará os resultados com seu design. Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity. É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Sr e Azure 311: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (julho de 2018). Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso correspondam perfeitamente ao que você encontrará no software mais recente do que o que está listado abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um PC de desenvolvimento
- [Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md#installation-checklist)
- [O SDK do Windows 10 mais recente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Um [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado
- Acesso à Internet para a instalação do Azure e recuperação de dados de Microsoft Graph
- Uma **conta da Microsoft** válida (pessoal ou corporativa/de estudante)
- Algumas reuniões agendadas para o dia atual, usando a mesma conta da Microsoft

### <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).
2.  Configure e teste seu HoloLens. Se você precisar de suporte para configurar seu HoloLens, [visite o artigo configuração do hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  É uma boa ideia executar a calibragem e o ajuste do sensor ao começar a desenvolver um novo aplicativo do HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

Para obter ajuda sobre calibragem, siga este [link para o artigo Calibration do HoloLens](calibration.md#hololens).

Para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste do sensor do HoloLens](sensor-tuning.md).

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>Capítulo 1-criar seu aplicativo no portal de registro de aplicativos

Para começar, você precisará criar e registrar seu aplicativo no **portal de registro de aplicativos**.

Neste capítulo, você também encontrará a chave de serviço que permitirá fazer chamadas para *Microsoft Graph* acessar o conteúdo da conta.

1.  Navegue até o [portal de registro de aplicativos da Microsoft](https://apps.dev.microsoft.com) e faça logon com sua conta da Microsoft. Depois de fazer logon, você será redirecionado para o portal de **registro de aplicativo**.

2.  Na seção **meus aplicativos** , clique no botão **Adicionar um aplicativo**.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > O **portal de registro de aplicativos** pode parecer diferente, dependendo se você já trabalhou com *Microsoft Graph*. As capturas de tela abaixo exibem essas versões diferentes.

3.  Adicione um nome para seu aplicativo e clique em **criar**.

    ![](images/AzureLabs-Lab311-03.png)

4.  Depois que o aplicativo tiver sido criado, você será redirecionado para a página principal do aplicativo. Copie a **ID do aplicativo** e anote esse valor em algum lugar seguro, você o usará em breve no seu código.

    ![](images/AzureLabs-Lab311-04.png)

5.  Na seção **plataformas** , verifique se o **aplicativo nativo** é exibido. Se *não* clique em **Adicionar plataforma** e selecione **aplicativo nativo**.

    ![](images/AzureLabs-Lab311-05.png)

6.  Role para baixo na mesma página e, na seção chamada **Microsoft Graph permissões** , você precisará adicionar permissões adicionais para o aplicativo. Clique em **Adicionar** ao lado de **permissões delegadas**.

    ![](images/AzureLabs-Lab311-06.png)

7.  Como você deseja que seu aplicativo acesse o calendário do usuário, marque a caixa chamada **calendários. Leia** e clique em **OK**.

    ![](images/AzureLabs-Lab311-07.png)

8.  Role até a parte inferior e clique no botão **salvar** .

    ![](images/AzureLabs-Lab311-08.png)

9.  Seu salvamento será confirmado e você poderá fazer logoff do **portal de registro de aplicativos**.

## <a name="chapter-2---set-up-the-unity-project"></a>Capítulo 2 – configurar o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra o *Unity* e clique em **novo**.

    ![](images/AzureLabs-Lab311-09.png)

2.  Você precisa fornecer um nome de projeto de Unity. Insira **MSGraphMR**. Verifique se o modelo de projeto está definido como **3D**. Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![](images/AzureLabs-Lab311-10.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar** > **preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**. Altere o **Editor de script externo** para o **Visual Studio 2017**. Feche a janela **preferências** .

    ![](images/AzureLabs-Lab311-11.png)

4.  Vá para **arquivo** > **configurações de compilação** e selecione **plataforma universal do Windows**, em seguida, clique no botão **alternar plataforma** para aplicar sua seleção.

    ![](images/AzureLabs-Lab311-12.png)

5.  Ainda em**configurações de compilação**de **arquivo** > , verifique se:

    1. O **dispositivo de destino** está definido como **HoloLens**
    2. O **tipo de compilação** está definido como **D3D**
    3. O **SDK** está definido para o **mais recente instalado**
    4. A **versão do Visual Studio** está definida para o **mais recente instalado**
    5. **Compilar e executar** é definido como **computador local**
    6. Salve a cena e adicione-a à compilação.

        1. Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.

            ![](images/AzureLabs-Lab311-13.png)

        2. Crie uma nova pasta para isso e qualquer cena futura. Selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![](images/AzureLabs-Lab311-14.png)

        3. Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo*:, digite **MR_ComputerVisionScene**e clique em **salvar**.

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Lembre-se de que você deve salvar as cenas do Unity na pasta *ativos* , pois elas devem ser associadas ao projeto do Unity. Criar a pasta de cenas (e outras pastas semelhantes) é uma maneira típica de estruturar um projeto do Unity.

    7.  As configurações restantes, em *configurações de compilação*, devem ser deixadas como padrão por enquanto.

6.  Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado. 

    ![](images/AzureLabs-Lab311-16.png)

7. Nesse painel, algumas configurações precisam ser verificadas:

    1. Na guia **outras configurações** :

        1.  **Criando scripts** A **versão de tempo de execução** deve ser **Experimental** (.NET 4,6 equivalente), o que irá disparar uma necessidade de reiniciar o editor.

        2. O **back-end de script** deve ser **.net**

        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  Na guia **configurações de publicação** , em **recursos**, marque:

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), verifique a **realidade virtual com suporte**, verifique se o **SDK do Windows Mixed Reality** foi adicionado.

        ![](images/AzureLabs-Lab311-19.png)

8.  De volta *às configurações de compilação*, os *projetos de C# Unity* não ficam mais esmaecidos; Marque a caixa de seleção ao lado disso.

9.  Feche a janela *configurações de compilação* .

10.  Salve sua cena e seu projeto **(arquivo salvar arquivos** > de salvamento **/**  > **salvar**arquivo).

## <a name="chapter-3---import-libraries-in-unity"></a>Capítulo 3 – importar bibliotecas no Unity

> [!IMPORTANT]
> Se você quiser ignorar o componente de *configuração do Unity* deste curso e continuar diretamente no código, sinta-se à vontade para baixar este [Azure-Mr-311. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), importá-lo em seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar no [capítulo 5 ](#chapter-5---create-meetingsui-class).

Para usar *Microsoft Graph* no Unity, você precisa fazer uso da dll **Microsoft. Identity. Client** . É possível usar o SDK do Microsoft Graph, no entanto, ele exigirá a adição de um pacote NuGet depois que você criar o projeto do Unity (ou seja, editando o projeto após a compilação). É considerado mais simples importar as DLLs necessárias diretamente para o Unity.

> [!NOTE]
> Atualmente, há um problema conhecido no Unity que exige que os plugins sejam reconfigurados após a importação. Essas etapas (4-7 nesta seção) não serão mais necessárias depois que o bug for resolvido.

Para importar *Microsoft Graph* para seu próprio projeto, [Baixe o arquivo MSGraph_LabPlugins. zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage). Este pacote foi criado com versões das bibliotecas que foram testadas.

Se você quiser saber mais sobre como adicionar DLLs personalizadas ao seu projeto do Unity, [siga este link](https://docs.unity3d.com/Manual/UsingDLL.html).

Para importar o pacote:

1.  Adicione o pacote do Unity ao Unity usando a opção de menu**pacote personalizado** do**pacote** > de importação de **ativos** > . Selecione o pacote que você acabou de baixar.

2.  Na caixa **Importar pacote de Unity** que é exibida, verifique se tudo em (e incluindo) **plug-ins** está selecionado.

    ![](images/AzureLabs-Lab311-20.png)

3.  Clique no botão **importar** para adicionar os itens ao seu projeto.

4.  Vá para a pasta **MSGraph** em **plug-ins** no *painel Projeto* e selecione o plug-in chamado **Microsoft. Identity. Client**.

    ![](images/AzureLabs-Lab311-21.png)

5.  Com o *plug-in* selecionado, verifique se **qualquer plataforma** está desmarcada e, em seguida, verifique se **WSAPlayer** também está desmarcado e clique em **aplicar**. Isso é apenas para confirmar que os arquivos estão configurados corretamente.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > Marcar esses plug-ins os configura para ser usado apenas no editor do Unity. Há um conjunto diferente de DLLs na pasta WSA que será usado depois que o projeto for exportado do Unity como um aplicativo universal do Windows.

6.  Em seguida, você precisa abrir a pasta **WSA** , dentro da pasta **MSGraph** . Você verá uma cópia do mesmo arquivo que acabou de configurar. Selecione o arquivo e, em seguida, no Inspetor:

    -   Verifique se **qualquer plataforma** está desmarcada e se **somente** **WSAPlayer** está **marcado**.

    -   Verifique se o **SDK** está definido como **UWP**e se o **back-end de script** está definido como **dot net**

    -   Verifique se **não processar** está **marcado**.

        ![](images/AzureLabs-Lab311-23.png)

7.  Clique em **Aplicar**.

## <a name="chapter-4---camera-setup"></a>Capítulo 4 – configuração da câmera

Durante este capítulo, você configurará a câmera principal da sua cena:

1.  No *painel hierarquia*, selecione a **câmera principal**.

2.  Depois de selecionado, você poderá ver todos os componentes da **câmera principal** no painel *Inspetor* .

    1.  O **objeto de câmera** deve ser nomeado como a **câmera principal** (Observe a grafia!)

    2.  A **marca** da câmera principal deve ser definida como **MainCamera** (Observe a ortografia!)

    3.  Verifique se a **posição de transformação** está definida como **0, 0,** 0

    4.  Definir **sinalizadores de limpeza** como **cor sólida**

    5.  Defina a **cor do plano de fundo** do componente da câmera como **preto, alfa 0** **(código hex: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  A estrutura final do objeto no *painel hierarquia* deve ser parecida com a mostrada na imagem abaixo:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Capítulo 5-criar classe MeetingsUI

O primeiro script que você precisa criar é **MeetingsUI**, que é responsável por hospedar e preencher a interface do usuário do aplicativo (mensagem de boas-vindas, instruções e os detalhes da reunião).

Para criar esta classe:

1.  Clique com o botão direito do mouse na pasta **ativos** no *painel Projeto*e selecione **criar** > **pasta**. Nomeie a pasta **scripts**.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  Abra a pasta **scripts** e, nessa pasta, clique com o botão direito do mouse em **criar**  >   **C# script**. Nomeie o script **MeetingsUI.**

    ![](images/AzureLabs-Lab311-28.png)

3.  Clique duas vezes no novo script **MeetingsUI** para abri-lo com o *Visual Studio*.

4.  Insira os seguintes namespaces:

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  Dentro da classe, insira as seguintes variáveis:

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  Em seguida, substitua o método **Start ()** e adicione um método **ativo ()** . Eles serão chamados quando a classe for inicializada:

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  Adicione os métodos responsáveis por criar a *interface do usuário de reuniões* e preenchê-la com as reuniões atuais quando solicitado:

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **Exclua** o método **Update ()** e **salve as alterações** no Visual Studio antes de retornar ao Unity. 

## <a name="chapter-6---create-the-graph-class"></a>Capítulo 6 – criar a classe do grafo

O próximo script a ser criado é o script do **grafo** . Esse script é responsável por fazer as chamadas autenticar o usuário e recuperar as reuniões agendadas para o dia atual do calendário do usuário.

Para criar esta classe:

1.  Clique duas vezes na pasta **scripts** para abri-la.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o **gráfico**de script.

3.  Clique duas vezes no script para abri-lo com o Visual Studio.

4.  Insira os seguintes namespaces:

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > Você observará que partes do código nesse script são encapsuladas em torno de [diretivas de pré-compilação](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), isso é para evitar problemas com as bibliotecas ao criar a solução do Visual Studio.

5.  Exclua os métodos **Start ()** e **Update ()** , pois eles não serão usados.

6.  Fora da classe do **grafo** , insira os seguintes objetos, que são necessários para desserializar o objeto JSON que representa as reuniões agendadas diariamente:

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  Dentro da classe do **grafo** , adicione as seguintes variáveis:

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > Altere o valor **AppID** para que seja a **ID do aplicativo** que você anotou no  **[capítulo 1](#chapter-1---create-your-app-in-the-application-registration-portal), etapa 4**. Esse valor deve ser o mesmo que o exibido no **portal de registro de aplicativos,** na página de registro do aplicativo.

8.  Dentro da classe do **grafo** , adicione os métodos **SignInAsync ()** e **AquireTokenAsync ()** , que solicitará que o usuário insira as credenciais de logon.

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  Adicione os dois métodos a seguir:

    1.  **BuildTodayCalendarEndpoint ()** , que compila o URI que especifica o dia e o período de tempo em que as reuniões agendadas são recuperadas.

    2.  **ListMeetingsAsync ()** , que solicita as reuniões agendadas de *Microsoft Graph*.

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. Agora você concluiu o script do **grafo** . **Salve suas alterações** no Visual Studio antes de retornar ao Unity.

## <a name="chapter-7---create-the-gazeinput-script"></a>Capítulo 7-criar o script GazeInput

Agora, você criará o **GazeInput**. Essa classe manipula e controla o olhar do usuário, usando um **Raycast** proveniente da **câmera principal**, projetando em frente.

Para criar o script:

1.  Clique duas vezes na pasta **scripts** para abri-la.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script **GazeInput**.

3.  Clique duas vezes no script para abri-lo com o Visual Studio.

4.  Altere o código de namespaces para corresponder ao mostrado abaixo, juntamente com a adição da marca ' **\[System. Serializable\]** ' acima da classe **GazeInput** , para que possa ser serializada:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  Dentro da classe **GazeInput** , adicione as seguintes variáveis:

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  Adicione o método **CreateCursor ()** para criar o cursor do HoloLens na cena e chame o método do método **Start ()** :

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  Os métodos a seguir habilitam o olhar Raycast e controlam os objetos focados.

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
                HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  **Salve suas alterações** no Visual Studio antes de retornar ao Unity.

## <a name="chapter-8---create-the-interactions-class"></a>Capítulo 8-criar a classe interações

Agora será necessário criar o script de **interações** , que é responsável por:

-   Manipular a interação de **toque** e a **câmera olhar**, que permite ao usuário interagir com o logon "Button" na cena.

-   Criando o objeto "Button" de logon na cena para o usuário interagir com o.

Para criar o script:

1.  Clique duas vezes na pasta **scripts** para abri-la.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script de interações.

3.  Clique duas vezes no script para abri-lo com o Visual Studio.

4.  Insira os seguintes namespaces:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  Altere a herança da classe de **interação** de *monocomportamento* para **GazeInput**.

    ~~interações de classe pública: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  Dentro da classe de **interação** , insira a seguinte variável:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  Substituir o método **Start** ; Observe que é um método override, que chama o método de classe ' base ' olhar. **Start ()** será chamado quando a classe for inicializada, registrando-se para o reconhecimento de entrada e criando o *botão* entrar na cena:

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  Adicione o método **CreateSignInButton ()** , que criará uma instância do *botão* entrar na cena e definirá suas propriedades:

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  Adicione o método **GestureRecognizer_Tapped ()** , que será respondido para o evento *Tap* User.

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **Exclua** o método **Update ()** e **salve as alterações** no Visual Studio antes de retornar ao Unity.

## <a name="chapter-9---set-up-the-script-references"></a>Capítulo 9-configurar as referências de script

Neste capítulo, você precisa posicionar o  script de interações na **câmera principal**. Esse script manipulará a colocação dos outros scripts onde eles precisam ser.

-  Na pasta **scripts** do *painel Projeto*, arraste as interações de  script para o objeto da **câmera principal** , conforme mostrado abaixo.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Capítulo 10-Configurando a marca

O código que manipula o olhar fará uso da marca **SignInButton** para identificar a qual objeto o usuário irá interagir para entrar no *Microsoft Graph*.

Para criar a marca:

1.  No editor do Unity, clique na **câmera principal** no *painel hierarquia*.

2.  No *painel Inspetor* , clique na marca **MainCamera**  para abrir uma lista suspensa. Clique em **adicionar marca..** .

    ![](images/AzureLabs-Lab311-30.png)

3.  Clique no **+** botão.

    ![](images/AzureLabs-Lab311-31.png)

4.  Escreva o nome da marca como **SignInButton** e clique em salvar.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>Capítulo 11-criar o projeto do Unity para UWP

Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.

1.  Navegue até *configurações de Build* (**arquivo*>*Compilar configurações**).

    ![](images/AzureLabs-Lab311-33.png)

2.  Se ainda não tiver feito isso, **projetos de unidade C\#** Tick.

3.  Clique em **Compilar**. O Unity iniciará uma janela **Explorador de arquivos** , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado. Crie essa pasta agora e nomeie-a como **aplicativo**. Em seguida, com a pasta de **aplicativo** selecionada, clique em **Selecionar pasta**.

4.  O Unity começará a criar seu projeto na pasta do **aplicativo** .

5.  Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).

## <a name="chapter-12---deploy-to-hololens"></a>Capítulo 12 – implantar no HoloLens

Para implantar no HoloLens:

1.  Você precisará do endereço IP do seu HoloLens (para implantação remota) e para garantir que seu HoloLens esteja no **modo de desenvolvedor.** Para fazer isso:

    1.  Enquanto estiver desgastando seu HoloLens, abra as **configurações**.

    2.  Vá para **rede &**  > **Opções avançadas** **de Internet Wi-Fi** > 

    3.  Anote o endereço **IPv4** .

    4.  Em seguida, navegue de volta para **configurações**e, em seguida, para **Atualizar & segurança** > **para desenvolvedores**

    5.  Defina o **modo de desenvolvedor em**.

2.  Navegue até sua nova compilação do Unity (a pasta do **aplicativo** ) e abra o arquivo de solução com o **Visual Studio**.

3.  Na **configuração da solução** , selecione **depurar**.

4.  Na **plataforma da solução**, selecione **x86, computador remoto**. Você será solicitado a inserir o **endereço IP** de um dispositivo remoto (o HoloLens, neste caso, que você anotou).

    ![](images/AzureLabs-Lab311-34.png)

5.  Vá para o menu **Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu HoloLens.

6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!

## <a name="your-microsoft-graph-hololens-application"></a>Seu aplicativo Microsoft Graph HoloLens

Parabéns, você criou um aplicativo de realidade misturada que aproveita o Microsoft Graph, para ler e exibir dados de calendário do usuário.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Use Microsoft Graph para exibir outras informações sobre o usuário

-   Email do usuário/número do telefone/imagem do perfil

### <a name="exercise-1"></a>Exercício 1

Implemente o controle de voz para navegar na interface do usuário do Microsoft Graph.
