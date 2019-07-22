---
title: MR e 311 - Microsoft Graph do Azure
description: Conclua este curso para saber como aproveitar o Microsoft Graph e conecte-se aos dados que direcionam a produtividade, dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, o microsoft graph, hololens, imersivo, vr
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694523"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

# <a name="mr-and-azure-311---microsoft-graph"></a>MR e 311 - Microsoft Graph do Azure

Neste curso, você aprenderá a usar *Microsoft Graph* fazer logon na sua conta da Microsoft usando a autenticação segura dentro de um aplicativo de realidade misturada. Você, em seguida, recuperar e exibir suas reuniões agendadas na interface do aplicativo.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* é um conjunto de APIs projetados para permitir o acesso a muitos dos serviços da Microsoft. Microsoft descreve o Microsoft Graph como sendo uma matriz de recursos conectados por relações, o que significa que ele permite que um aplicativo para acessar todos os tipos de dados do usuário conectado. Para obter mais informações, visite o [página do Microsoft Graph](https://developer.microsoft.com/graph).

Desenvolvimento incluirá a criação de um aplicativo em que o usuário será instruído a mantenha o foco em e, em seguida, toque em uma esfera, que solicitará ao usuário para fazer logon com segurança uma conta da Microsoft. Depois de conectado à sua conta, o usuário será capaz de ver uma lista de reuniões agendadas para o dia.

Com a conclusão deste curso, você terá uma realidade misturada aplicativo HoloLens, que será capaz de fazer o seguinte:

1.  Usando o gesto de toque, toque em um objeto, que solicitará que o usuário faça logon em uma Account da Microsoft (mover para fora do aplicativo para fazer logon e, em seguida, volta para o aplicativo novamente).
2.  Exiba uma lista de reuniões agendadas para o dia. 

Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design. Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity. Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> MR e 311 do Azure: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#. Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (julho de 2018). Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que está listado abaixo.

Recomendamos que o hardware e software para este curso a seguir:

- Um computador de desenvolvimento
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md#installation-checklist)
- [O SDK mais recente do Windows 10](install-the-tools.md#installation-checklist)
- [2017.4 do Unity](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Um [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado
- Acesso à Internet para a instalação do Azure e a recuperação de dados do Microsoft Graph
- Válida **Account da Microsoft** (pessoais ou corporativas ou de estudante)
- Algumas reuniões agendadas para o dia atual, usando a mesma Account da Microsoft

### <a name="before-you-start"></a>Antes de começar

1.  Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).
2.  Configurar e testar o HoloLens. Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  É uma boa ideia executar calibragem e ajuste de Sensor ao começar a desenvolver um new App HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).

Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>Capítulo 1 - criar seu aplicativo no Portal de registro de aplicativo

Para começar, você precisará criar e registrar seu aplicativo na **Portal de registro de aplicativo**.

Neste capítulo, você também irá encontrar a chave de serviço que permitirá que você faça chamadas para *Microsoft Graph* para acessar o conteúdo da sua conta.

1.  Navegue até a [Portal de registro de aplicativo do Microsoft](https://apps.dev.microsoft.com) e faça logon com sua Account da Microsoft. Depois de ter conectado, você será redirecionado para o **Portal de registro de aplicativo**.

2.  No **meus aplicativos** seção, clique no botão **adicionar um aplicativo**.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > O **Portal de registro de aplicativo** pode ser diferente, dependendo se você tiver trabalhado anteriormente com *o Microsoft Graph*. A seguir capturas de tela exibir essas versões diferentes.

3.  Adicionar um nome para seu aplicativo e clique em **criar**.

    ![](images/AzureLabs-Lab311-03.png)

4.  Quando o aplicativo tiver sido criado, você será redirecionado para a página principal do aplicativo. Cópia de **Id do aplicativo** e anote esse valor em um lugar seguro, você irá usá-lo em breve em seu código.

    ![](images/AzureLabs-Lab311-04.png)

5.  No **plataformas** seção, certifique-se **aplicativo nativo** é exibida. Se *não* clique em **Adicionar plataforma** e selecione **aplicativo nativo**.

    ![](images/AzureLabs-Lab311-05.png)

6.  Role para baixo na mesma página e na seção chamada **permissões do Microsoft Graph** você precisará adicionar permissões adicionais para o aplicativo. Clique em **Add** lado **permissões delegadas**.

    ![](images/AzureLabs-Lab311-06.png)

7.  Como você deseja que seu aplicativo para acessar o calendário do usuário, marque a caixa denominada **Calendars** e clique em **Okey**.

    ![](images/AzureLabs-Lab311-07.png)

8.  Role para baixo e clique no **salvar** botão.

    ![](images/AzureLabs-Lab311-08.png)

9.  O salvamento será confirmado e você pode fazer logoff do **Portal de registro de aplicativo**.

## <a name="chapter-2---set-up-the-unity-project"></a>Capítulo 2 - configurar o projeto do Unity

A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.

1.  Abra *Unity* e clique em **New**.

    ![](images/AzureLabs-Lab311-09.png)

2.  Você precisa fornecer um nome de projeto do Unity. Insert **MSGraphMR**. Verifique se o modelo de projeto é definido como **3D**. Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![](images/AzureLabs-Lab311-10.png)

3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Vá para **edite** > **preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

    ![](images/AzureLabs-Lab311-11.png)

4.  Vá para **arquivo** > **configurações de Build** e selecione **plataforma Universal do Windows**, em seguida, clique no **alternar plataforma** botão Aplicar sua seleção.

    ![](images/AzureLabs-Lab311-12.png)

5.  Enquanto estiver na **arquivo** > **configurações de Build**, certifique-se de que:

    1. **Dispositivo de destino** é definido como **HoloLens**
    2. **Tipo de compilação** é definido como **D3D**
    3. **SDK** é definido como **mais recente instalada**
    4. **Versão do Visual Studio** é definido como **mais recente instalada**
    5. **Compilar e executar** é definido como **Máquina Local**
    6. Salve a cena e adicioná-lo para a compilação.

        1. Fazer isso selecionando **cenas abra Adicionar**. Salvamento janela será exibida.

            ![](images/AzureLabs-Lab311-13.png)

        2. Crie uma nova pasta para isso e qualquer futuro, cena. Selecione o **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.

            ![](images/AzureLabs-Lab311-14.png)

        3. Abrir seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo*: campo de texto, digite **MR_ComputerVisionScene**, em seguida, clique em **salvar** .

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Esteja ciente de que você deve salvar suas cenas de Unity dentro do *ativos* pasta, pois eles devem estar associados ao projeto do Unity. Criando a pasta de cenas (e outras pastas semelhantes) é uma maneira comum de estruturar um projeto do Unity.

    7.  O restante de configurações, em *configurações de Build*, deverá ser deixado como padrão por enquanto.

6.  No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado. 

    ![](images/AzureLabs-Lab311-16.png)

7. Neste painel, algumas configurações precisam ser verificados:

    1. No **outras configurações** guia:

        1.  **Criação de scripts** **versão de tempo de execução** deve ser **Experimental** (equivalente ao .NET 4.6), que irá disparar uma necessidade de reiniciar o Editor.

        2. **Script de back-end** deve ser **.NET**

        3. **Nível de compatibilidade de API** deve ser **.NET 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  Dentro de **configurações de publicação** guia, em **recursos**, verifique:

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  Mais para baixo no painel, no **XR configurações** (encontrada abaixo **configurações de publicação**), verifique **suporte de realidade Virtual**, certifique-se a **realidade mista do Windows SDK** é adicionado.

        ![](images/AzureLabs-Lab311-19.png)

8.  Volta *configurações de Build*, *Unity C# projetos* não fica acinzentado; Verifique a caixa de seleção ao lado disso.

9.  Fechar o *configurações de Build* janela.

10.  Salvar sua cena e seu projeto (**arquivo** > **salvar CENAS de arquivos** > **Salvar projeto**).

## <a name="chapter-3---import-libraries-in-unity"></a>Capítulo 3 - bibliotecas de importação no Unity

> [!IMPORTANT]
> Se você quiser ignorar a *Unity configurar* componente deste curso e continuar diretamente no código, fique à vontade para baixá-lo [MR-Azure-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 5](#chapter-5---create-meetingsui-class).

Para usar *Microsoft Graph* dentro do Unity que você precisa fazer uso das **Microsoft.Identity.Client** DLL. É possível usar o SDK do Microsoft Graph, no entanto, ela exigirá a adição de um pacote do NuGet depois de compilar o projeto do Unity (o que significa que editar pós-compilação do projeto). Ele é considerado mais simples importar as DLLs necessárias diretamente para o Unity.

> [!NOTE]
> Atualmente, há um problema conhecido no Unity que requer o plug-ins para ser reconfigurado após a importação. Estas etapas (4 a 7 desta seção) não será necessárias depois que o bug foi resolvido.

Para importar *Microsoft Graph* em seu próprio projeto [Baixe o arquivo MSGraph_LabPlugins.zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage). Este pacote foi criado com as versões das bibliotecas que foram testadas.

Se você quiser saber mais sobre como adicionar DLLs personalizadas ao seu projeto do Unity [siga este link](https://docs.unity3d.com/Manual/UsingDLL.html).

Para importar o pacote:

1.  Adicione o pacote do Unity para Unity, usando o **ativos** > **Importar pacote** > **pacote personalizado** opção de menu. Selecione o pacote que você acabou de baixar.

2.  No **Importar pacote do Unity** caixa é exibido para cima, certifique-se de tudo em (e incluindo) **plug-ins** está selecionado.

    ![](images/AzureLabs-Lab311-20.png)

3.  Clique o **importação** botão para adicionar itens ao seu projeto.

4.  Vá para o **MSGraph** pasta sob **plug-ins** no *painel projeto* e selecione o plug-in chamado **Microsoft.Identity.Client**.

    ![](images/AzureLabs-Lab311-21.png)

5.  Com o *plug-in* selecionado, certifique-se de que **plataforma Any** está desmarcada e, em seguida, certifique-se de que **WSAPlayer** também está desmarcada e, em seguida, clique em **aplicar**. Isso é apenas para confirmar que os arquivos estão configurados corretamente.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > Marcar esses plug-ins configura para ser usado apenas no Editor do Unity. Há um conjunto diferente de DLLs na pasta do WSA que será usado depois que o projeto é exportado do Unity como um aplicativo Universal do Windows.

6.  Em seguida, você precisa abrir o **WSA** pasta, dentro de **MSGraph** pasta. Você verá uma cópia do mesmo arquivo que você acabou de configurar. Selecione o arquivo e, em seguida, no Inspetor de:

    -   Certifique-se de que **plataforma Any** é **desmarcada**e que **apenas** **WSAPlayer** é **marcada**.

    -   Certifique-se **SDK** é definido como **UWP**, e **script de back-end** é definido como **plataforma Dot Net**

    -   Certifique-se de que **não processar** é **check**.

        ![](images/AzureLabs-Lab311-23.png)

7.  Clique em **Aplicar**.

## <a name="chapter-4---camera-setup"></a>Capítulo 4 - configuração de câmera

Durante este capítulo, você definirá a câmera principal da sua cena:

1.  No *painel de hierarquia*, selecione o **câmera principal**.

2.  Depois de selecionado, você poderá ver todos os componentes do **câmera principal** na *Inspetor* painel.

    1.  O **objeto de câmera** deve ser nomeado **câmera principal** (Observe a ortografia!)

    2.  A câmera principal **marca** deve ser definida como **MainCamera** (Observe a ortografia!)

    3.  Verifique se o **transformar posição** é definido como **0, 0, 0**

    4.  Definir **limpar os sinalizadores** para **cor sólida**

    5.  Defina a **cor do plano de fundo** do componente a câmera **preto, alfa 0** **(Hex código: 00000000 #)**

        ![](images/AzureLabs-Lab311-24.png)

3.  A estrutura de objeto final na *painel de hierarquia* deve ser semelhante à mostrada na imagem abaixo:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Capítulo 5 - Criar classe MeetingsUI

É o primeiro script que você precisa criar **MeetingsUI**, que é responsável pela hospedagem e preenchendo a IU do aplicativo (mensagem de boas-vinda, instruções e os detalhes de reuniões).

Para criar essa classe:

1.  Clique com botão direito no **ativos** pasta na *painel projeto*, em seguida, selecione **Create** > **pasta**. Nomeie a pasta **Scripts**.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  Abra o **Scripts** pasta em seguida, dentro dessa pasta, clique com botão direito, **Create**  >   **C# Script**. Nomeie o script **MeetingsUI.**

    ![](images/AzureLabs-Lab311-28.png)

3.  Clique duas vezes na nova **MeetingsUI** script para abri-lo com *Visual Studio*.

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

6.  Em seguida, substitua os **Start ()** método e adicione um **Awake()** método. Eles serão chamados quando inicializa a classe:

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

7.  Adicione os métodos responsáveis por criar a *interface do usuário de reuniões* e preenchê-lo com as reuniões atuais quando solicitado:

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

8. **Exclua** as **Update ()** método, e **salvar suas alterações** no Visual Studio antes de retornar para o Unity. 

## <a name="chapter-6---create-the-graph-class"></a>Capítulo 6 - criar a classe de gráfico

É o próximo script para criar o **Graph** script. Esse script é responsável por fazer as chamadas para autenticar o usuário e recuperar as reuniões agendadas para o dia atual do calendário do usuário.

Para criar essa classe:

1.  Clique duas vezes no **Scripts** pasta para abri-lo.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script **Graph**.

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
    > Você observará que as partes do código nesse script são encapsuladas em torno [pré-compilar diretivas](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), isso é para evitar problemas com as bibliotecas ao compilar a solução do Visual Studio.

5.  Excluir o **Start ()** e **Update ()** métodos, pois não serão usados.

6.  Fora de **Graph** de classe, insira os seguintes objetos são necessários para desserializar o objeto JSON que representa as diárias reuniões agendadas:

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

7.  Dentro de **Graph** de classe, adicione as seguintes variáveis:

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
    > Alterar o **appId** valor seja a **Id do aplicativo** que você observou na  **[capítulo 1](#chapter-1---create-your-app-in-the-application-registration-portal), etapa 4**. Esse valor deve ser o mesmo que o exibido na **Portal de registro de aplicativo,** na sua página de registro do aplicativo.

8.  Dentro de **Graph** classe, adicione os métodos **SignInAsync()** e **AquireTokenAsync()** , que solicitará ao usuário inserir as credenciais de logon.

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

9.  Adicione dois métodos a seguir:

    1.  **BuildTodayCalendarEndpoint()** , quais compilações o URI, especificando o dia e o período de tempo, em que as reuniões agendadas são recuperadas.

    2.  **ListMeetingsAsync()** , que solicita as reuniões agendadas de *Microsoft Graph*.

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

10. Agora você concluiu a **Graph** script. **Salve suas alterações** no Visual Studio antes de retornar para o Unity.

## <a name="chapter-7---create-the-gazeinput-script"></a>Capítulo 7 - criar o script de GazeInput

Agora você criará a **GazeInput**. Essa classe manipula e mantém o controle de olhar do usuário, usando um **Raycast** provenientes a **câmera principal**, projetando para frente.

Para criar o script:

1.  Clique duas vezes no **Scripts** pasta para abri-lo.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script **GazeInput**.

3.  Clique duas vezes no script para abri-lo com o Visual Studio.

4.  Alterar o código de namespaces para coincidir com a mostrada abaixo, junto com a adição de ' **\[System.Serializable\]** ' acima da marca seu **GazeInput** de classe, para que ele pode ser serializado:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  Dentro de **GazeInput** de classe, adicione as seguintes variáveis:

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

6.  Adicione a **CreateCursor()** método cria o cursor do HoloLens na cena e chame o método da **Start ()** método:

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

7.  Os métodos a seguir permitem o olhar Raycast e controlar os objetos com foco.

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

8.  **Salve suas alterações** no Visual Studio antes de retornar para o Unity.

## <a name="chapter-8---create-the-interactions-class"></a>Capítulo 8 - criar a classe de interações

Agora você precisará criar o **interações** script, que é responsável por:

-   Manipulando o **toque** interação e a **câmera olhares**, que permite que o usuário interaja com o log de "botão" na cena.

-   Criar o log no objeto de "botão" na cena para interagir com o usuário.

Para criar o script:

1.  Clique duas vezes no **Scripts** pasta para abri-lo.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script **interações**.

3.  Clique duas vezes no script para abri-lo com o Visual Studio.

4.  Insira os seguintes namespaces:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  Alterar a herança do **interação** classe *MonoBehaviour* para **GazeInput**.

    ~~Interações de classe pública: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  Dentro de **interação** classe inserir a seguinte variável:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  Substitua os **iniciar** método; Observe que ele é um método de substituição, que chama o método da classe 'base' olhar. **Start ()** será chamado quando a classe é inicializado, se registrar para o reconhecimento de entrada e criar a entrada *botão* na cena:

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

8.  Adicione a **CreateSignInButton()** método, que criará uma instância de entrada *botão* na cena e defina suas propriedades:

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

9.  Adicione a **GestureRecognizer_Tapped()** método, que ser responder para o *toque* evento de usuário.

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

10. **Excluir** as **Update ()** método e então **salvar suas alterações** no Visual Studio antes de retornar para o Unity.

## <a name="chapter-9---set-up-the-script-references"></a>Capítulo 9 - configurar as referências de script

Neste capítulo, você precisa colocar o **interações** gerar script para o **câmera principal**. Esse script tratará a colocar outros scripts onde elas precisam ser.

-  Do **Scripts** pasta na *painel projeto*, arraste o script **interações** para o **câmera principal** objeto, conforme ilustrado abaixo.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Capítulo 10 - como configurar a marca

O código que processa o olhar fará o uso da marca **SignInButton** para identificar qual objeto de usuário irá interagir com para entrar no *o Microsoft Graph*.

Para criar a marca:

1.  No Editor do Unity, clique no **câmera principal** na *painel de hierarquia*.

2.  No *painel Inspetor* clique no **MainCamera** *marca* para abrir uma lista suspensa. Clique em **Adicionar marca...**

    ![](images/AzureLabs-Lab311-30.png)

3.  Clique no **+** botão.

    ![](images/AzureLabs-Lab311-31.png)

4.  Grave o nome de marca como **SignInButton** e clique em Salvar.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>Capítulo 11 - compilar o projeto do Unity para UWP

Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído, portanto, é hora de criá-lo do Unity.

1.  Navegue até *configurações de Build* (**arquivo* >* Compilar configurações**).

    ![](images/AzureLabs-Lab311-33.png)

2.  Se ainda não estiver, marque **Unity C\# projetos**.

3.  Clique em **Compilar**. Unity iniciará uma **Explorador de arquivos** janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em. Criar pasta agora e nomeie- **aplicativo**. Em seguida, com o **App** pasta selecionada, clique em **Selecionar pasta**.

4.  Unity começará a compilar seu projeto para o **aplicativo** pasta.

5.  Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um **Explorador de arquivos** janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).

## <a name="chapter-12---deploy-to-hololens"></a>Capítulo 12 - implantar em HoloLens

Para implantar o HoloLens:

1.  Será necessário o endereço IP do seu HoloLens (para a implantação remota) e garantir que seu HoloLens está em **modo de desenvolvedor.** Para fazer isso:

    1.  Durante o uso de seu HoloLens, abra o **configurações**.

    2.  Vá para **rede e Internet** > **Wi-Fi** > **opções avançadas**

    3.  Observe a **IPv4** endereço.

    4.  Em seguida, navegue até **as configurações**e, em seguida, para **atualização e segurança** > **para desenvolvedores**

    5.  Definir **modo de desenvolvedor no**.

2.  Navegue até seu novo build do Unity (o **App** pasta) e abra o arquivo de solução com **Visual Studio**.

3.  No **configuração da solução** selecionar **depurar**.

4.  No **plataforma da solução**, selecione **x86, computador remoto**. Você será solicitado a inserir o **endereço IP** de um dispositivo remoto (o HoloLens, nesse caso, que você anotou).

    ![](images/AzureLabs-Lab311-34.png)

5.  Vá para **construir** menu e clique em **implantar solução** para carregar o aplicativo para o HoloLens.

6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!

## <a name="your-microsoft-graph-hololens-application"></a>Seu aplicativo do Microsoft Graph HoloLens

Parabéns, você criou um aplicativo de realidade mista que aproveita o Microsoft Graph para ler e exibir dados de calendário do usuário.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Usar o Microsoft Graph para exibir outras informações sobre o usuário

-   Email do usuário / número de telefone / imagem de perfil

### <a name="exercise-1"></a>Exercício 1

Implementar o controle de voz para navegar a interface do usuário do Microsoft Graph.
