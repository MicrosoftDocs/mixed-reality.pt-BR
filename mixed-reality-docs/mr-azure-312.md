---
title: MR e 312 Azure - integração do Bot
description: Conclua este curso para aprender a criar e implantar um bot, usando o Microsoft Bot Framework v4 e se comunicar com ele em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, pesquisa Visual computacional, hololens, vr de imersão, microsoft bot framework v4, bot de aplicativo web, estrutura do bot, bot da microsoft
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590996"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

# <a name="mr-and-azure-312-bot-integration"></a>MR e o Azure 312: Integração do bot

Neste curso, você aprenderá como criar e implantar um bot usando a V4 do Microsoft Bot Framework e se comunicar com ele por meio de um aplicativo de realidade mista do Windows. 

![](images/AzureLabs-Lab312-00.png)

O **Microsoft Bot Framework V4** é um conjunto de APIs projetado para fornecer aos desenvolvedores as ferramentas para compilar um bot extensível e escalonável com o aplicativo. Para obter mais informações, visite o [página do Microsoft Bot Framework](https://dev.botframework.com/) ou o [repositório de Git V4](https://github.com/Microsoft/botbuilder-dotnet/wiki).

Depois de concluir este curso, você terá criado um aplicativo de realidade mista do Windows, será possível fazer o seguinte:

1. Use uma **gestos de toque** para iniciar o bot de escuta de voz a usuários.
2. Quando o usuário disse algo, o bot tentará fornecer uma resposta.
3. Exibe a resposta de bots como texto, posicionado perto o bot, na cena Unity.

Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design. Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity. Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> MR e o Azure 312: Integração do bot</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- Acesso à Internet para o Azure e para recuperação de Bot do Azure. Para obter mais informações, [, siga este link](https://dev.botframework.com/).

### <a name="before-you-start"></a>Antes de começar

1.  Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).
2.  Configurar e testar o HoloLens. Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  É uma boa ideia executar calibragem e ajuste de Sensor ao começar a desenvolver um novo aplicativo HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário). 

Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).

Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).

## <a name="chapter-1--create-the-bot-application"></a>Capítulo 1 – criar o aplicativo Bot

A primeira etapa é criar seu bot como um aplicativo Web do ASP.Net Core local. Depois de concluído e testá-lo, você será publicá-lo no portal do Azure.

1.  Abra o Visual Studio. Criar um novo projeto, selecione **aplicativo Web do ASP NET Core** como o tipo de projeto (você irá encontrá-la sob a subseção do .NET Core) e chamá-lo **MyBot**. Clique em **OK**.

2.  Na janela que aparecerá select **vazio**. Também verifique se o destino é definido como **ASP NET Core 2.0** e a autenticação está definida como **sem autenticação**. Clique em **OK**.  

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-01.png)

3.  A solução agora será aberto. Clique com botão direito na solução **Mybot** na **Gerenciador de soluções** e clique em **gerenciar pacotes NuGet para solução**. 

    ![Criar o aplicativo Bot](images/AzureLabs-Lab312-02.png)

4.  No **procurar** guia, pesquise por **Microsoft.Bot.Builder.Integration.AspNet.Core** (Verifique se você tem **incluir pré-lançamento** marcada). Selecione a versão do pacote **4.0.1-Preview**, marque as caixas de projeto. Em seguida, clique em **instalar**. Agora você instalou as bibliotecas necessárias para o **v4 do Bot Framework**. Feche a página do NuGet.

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-03.png)

5.  Clique com botão direito no seu *projeto*, **MyBot**, no **Gerenciador de soluções** e clique em **adicionar** **|** **Classe**.

    ![Criar o aplicativo Bot](images/AzureLabs-Lab312-04.png)

6.  Nomeie a classe **MyBot** e clique em **Add**.

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-05.png)

7.  Repita o ponto anterior, para criar outra classe denominada **ConversationContext**. 

8.  Clique duas vezes em **wwwroot** na **Gerenciador de soluções** e clique em **Add** **|** **denovoItem**. Selecione **página HTML** (você irá encontrá-la sob a subseção da Web). Nomeie o arquivo **default. HTML**. Clique em **Adicionar**.

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-06.png)

9.  A lista de classes / objetos na **Gerenciador de soluções** deve se parecer com a imagem a seguir.

    ![Criar o aplicativo bot](images/AzureLabs-Lab312-07.png)

10. Clique duas vezes no **ConversationContext** classe. Essa classe é responsável por armazenar as variáveis usadas pelo bot para manter o contexto da conversa. Esses valores de contexto de conversa são mantidos em uma instância dessa classe, porque qualquer instância das **MyBot** classe será atualizada sempre que uma atividade é recebida. Adicione o seguinte código à classe:

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. Clique duas vezes no **MyBot** classe. Essa classe hospedará os manipuladores de chamada por qualquer atividade de entrada do cliente. Essa classe, você adicionará o código usado para criar a conversa entre o cliente e de bot. Como mencionado anteriormente, uma instância dessa classe será inicializada sempre que uma atividade é recebida. Adicione o seguinte código para esta classe:

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. Clique duas vezes no **inicialização** classe. Essa classe irá inicializar o bot. Adicione o seguinte código à classe:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. Abra o **programa** arquivo de classe e verifique se o código é o mesmo que o seguinte:

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. Lembre-se de salvar suas alterações, para fazer isso, vá para **arquivo** > **Salvar tudo**, na barra de ferramentas na parte superior do Visual Studio.

## <a name="chapter-2---create-the-azure-bot-service"></a>Capítulo 2 - criar o serviço de Bot do Azure

Agora que você criou o código para o bot, você precisa publicá-lo em uma instância das *Bot de aplicativo Web* serviço no Portal do Azure. Este capítulo mostra como criar e configurar o serviço de Bot do Azure e, em seguida, publicar seu código nele.

1.  Primeiro, faça logon portal do Azure (https://portal.azure.com). 

    1. Se você ainda não tiver uma conta do Azure, você precisará criá-lo. Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.

2.  Quando você estiver conectado, clique em **criar um recurso** no canto superior esquerdo de canto e procure *bot de aplicativo Web*e clique em **Enter**.

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-08.png)
 
3.  A nova página fornecerá uma descrição do *Bot de aplicativo Web* serviço. Na parte inferior esquerda desta página, selecione a **criar** botão para criar uma associação com este serviço.

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-09.png)
 
4.  Depois de clicar em **criar**:

    1. Inserir sua desejada **nome** para esta instância de serviço.
    2. Selecione uma **assinatura**.
    3. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).

        > Se você quiser ler mais sobre grupos de recursos do Azure, [, siga este link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4. Determine o local para seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local seria o ideal é que na região em que o aplicativo é executado. Alguns ativos do Azure estão disponíveis somente em determinadas regiões.
    5. Selecione o **tipo de preço** apropriado para você, se esse for o primeiro tempo para criar um *Bot de aplicativo Web* serviço, uma camada gratuita (chamada F0) deve estar disponível para você
    6. **Nome do aplicativo** pode apenas ser deixada igual a *nome do Bot*. 
    7. Deixe o *modelo de Bot* como **básica (C#)**.
    8. *Localização/plano de serviço de aplicativo* deveria ter sido preenchidos automaticamente para sua conta.
    9. Defina as **armazenamento do Azure** que você deseja usar para hospedar seu Bot. Se você ainda não tiver uma, você pode criá-lo aqui.
    10. Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.
    11. Clique em criar.
 
        ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-10.png)

5.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

6.  Uma notificação será exibida no Portal depois que a instância do serviço é criada.

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-11.png) 
 
7.  Clique na notificação para explorar a nova instância do serviço. 

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-12.png)
 
8. Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço. Você será levado para a nova instância de serviço do Azure. 

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-13.png)
 
9.  Neste ponto, você precisa configurar um recurso chamado **linha direta** para permitir que seu aplicativo cliente para se comunicar com o serviço de Bot. Clique em **canais**, em seguida, no **adicionar um canal em destaque** seção, clique em **canal de linha direta para configurar**.

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-14.png)

10. Nesta página você encontrará os **chaves secretas** que permitirá que seu aplicativo cliente autenticar com o bot. Clique no **Mostrar** botão e faça uma cópia de uma das chaves exibidas, pois precisará dele posteriormente em seu projeto. 

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Capítulo 3 – publicar o Bot para o serviço de Bot do aplicativo Web do Azure

Agora que seu serviço estiver pronto, você precisa publicar seu código de Bot, o que você criou anteriormente, ao serviço de Bot de aplicativo Web recém-criado.

> [!NOTE] 
> Você precisará publicar seu Bot para o serviço do Azure sempre que você fizer alterações à solução Bot / code.

1.  Volte para sua solução do Visual Studio que você criou anteriormente. 
2.  Clique com botão direito no seu **MyBot** projeto, o **Gerenciador de soluções**, em seguida, clique em **publicar**.

    ![Publicar o Bot para o serviço de Bot do aplicativo Web do Azure](images/AzureLabs-Lab312-16.png)

3.  Sobre o *escolher um destino de publicação* , clique em **serviço de aplicativo**, em seguida, **selecionar existente**, por fim, clique em **criar perfil** (talvez você precise Clique na seta suspensa ao lado de *publicar* botão, se não estiver visível).

    ![Publicar o Bot para o serviço de Bot do aplicativo Web do Azure](images/AzureLabs-Lab312-17.png)

4. Se você ainda não está conectados em seu Account da Microsoft, você precisa fazê-lo aqui.
5. Sobre o **publicar** página você encontrará, você deve definir o mesmo **assinatura** que você usou para o *Bot de aplicativo Web* criação de serviço. Em seguida, defina a **modo de exibição** como **grupo de recursos** e, no menu suspenso de estrutura de pasta, selecione o **grupo de recursos** criado anteriormente. Clique em **OK**. 

    ![Publicar o Bot para o serviço de Bot do aplicativo Web do Azure](images/AzureLabs-Lab312-18.png)

6.  Agora, clique na **publicar** botão e, em seguida, aguarde até que o Bot para serem publicados (pode levar alguns minutos).

    ![Publicar o Bot para o serviço de Bot do aplicativo Web do Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Capítulo 4-configurar o projeto do Unity

A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.

1.  Abra *Unity* e clique em **New**. 

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-20.png)

2.  Agora, você precisará fornecer um nome de projeto do Unity. Inserir **Hololens Bot**. Verifique se o modelo de projeto é definido como **3D**. Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-21.png)

3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Vá para **Editar > Preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-22.png)

4.  Em seguida, vá para **arquivo > configurações de Build** e selecione **plataforma Universal do Windows**, em seguida, clique no **alternar plataforma** botão Aplicar sua seleção.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-23.png)

5.  Enquanto estiver na **arquivo > configurações de Build** e certifique-se de que:

    1.  **Dispositivo de destino** é definido como **Hololens**

        > Para os fones imersivos em exposição, defina **dispositivo de destino** à *qualquer dispositivo*.

    2.  **Tipo de compilação** é definido como **D3D**

    3.  **SDK** é definido como **mais recente instalada**

    4.  **Versão do Visual Studio** é definido como **mais recente instalada**

    5.  **Compilar e executar** é definido como **Máquina Local**

    6.  Salve a cena e adicioná-lo para a compilação. 

        1. Fazer isso selecionando **cenas abra Adicionar**. Salvamento janela será exibida.
        
            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-24.png)

        2. Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.

             ![Configurar o projeto do Unity](images/AzureLabs-Lab312-25.png)

        3. Abrir seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo*: campo de texto, digite **BotScene**, em seguida, clique em **salvar**.

            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-26.png)

    7. O restante de configurações, em **configurações de Build**, deverá ser deixado como padrão por enquanto.

6. No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado. 

    ![Configurar o projeto do Unity](images/AzureLabs-Lab312-27.png)

7. Neste painel, algumas configurações precisam ser verificados:

    1. No **outras configurações** guia:

        1. **Versão de tempo de execução de scripts** deve ser **Experimental (NET 4.6 equivalente)**; essa alteração exigirá uma reinicialização do Editor.
        2. **Script de back-end** deve ser **.NET**
        3. **Nível de compatibilidade de API** deve ser **.NET 4.6**

            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-28.png)
      
    2. Dentro de **configurações de publicação** guia, em **recursos**, verifique:

        - **InternetClient**
        - **Microfone**

            ![Configurar o projeto do Unity](images/AzureLabs-Lab312-29.png)

    3. Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.

        ![Configurar o projeto do Unity](images/AzureLabs-Lab312-30.png)

8.  Volta *configurações de Build* _Unity C#_  projetos não fica acinzentado; marque a caixa de seleção ao lado disso. 
9.  Feche a janela de configurações de Build.
10. Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).


## <a name="chapter-5--camera-setup"></a>Capítulo 5 – instalação da câmera

> [!IMPORTANT]
> Se você quiser ignorar a *configurar o Unity* componente deste curso e continuar diretamente no código, fique à vontade para baixá-lo [Azure MR-312 Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 7](#chapter-7-–-create-the-botobjects-class).

1.  No *painel de hierarquia*, selecione o **câmera principal**. 
2.  Depois de selecionado, você poderá ver todos os componentes do **câmera principal** na *painel Inspetor*.

    1. O **objeto de câmera** deve ser nomeado **câmera principal** (Observe a ortografia)
    2. A câmera principal **marca** deve ser definida como **MainCamera** (Observe a ortografia)
    3. Verifique se o **transformar posição** é definido como **0, 0, 0**
    4. Definir **limpar os sinalizadores** à **cor sólida**.
    5. Definir a **plano de fundo** cor do componente de câmera para **preto, alfa 0 (código hexadecimal: 00000000 #)**

    ![a instalação da câmera](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Capítulo 6 – importar a biblioteca Newtonsoft

Para ajudá-lo a desserializam e serializam os objetos recebidos e enviados para o serviço de Bot, você precisa baixar o **Newtonsoft** biblioteca. Você encontrará uma [versão compatível já organizado com a estrutura pasta Unity correta aqui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage). 

Para importar a biblioteca Newtonsoft para seu projeto, use o pacote do Unity que acompanha este curso.

1.  Adicionar o *unitypackage* para o Unity, usando o **ativos** > **Importar pacote** > **pacote personalizado** opção de menu.

    ![Importar a biblioteca Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  No **Importar pacote do Unity** caixa é exibido para cima, certifique-se de tudo em (e incluindo) **plug-ins** está selecionado.

    ![Importar a biblioteca Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  Clique o **importação** botão para adicionar itens ao seu projeto.

4.  Vá para o **Newtonsoft** pasta sob **plug-ins** no modo de exibição do projeto e selecione o plug-in do Newtonsoft.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Com o plug-in Newtonsoft selecionado, certifique-se de que **Any Platform** é **desmarcada**, em seguida, certifique-se de que **WSAPlayer** também é **desmarcada**, em seguida, clique em **aplicar**. Isso é apenas para confirmar que os arquivos estão configurados corretamente.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Marcar esses plug-ins configura para ser usado apenas no Editor do Unity. Há um conjunto diferente de-los na pasta do WSA que será usado depois que o projeto é exportado do Unity.

6.  Em seguida, você precisa abrir o **WSA** pasta, dentro de **Newtonsoft** pasta. Você verá uma cópia do mesmo arquivo que você acabou de configurar. Selecione o arquivo e, em seguida, no Inspetor de, certifique-se de que
    -   **Qualquer plataforma** é **desmarcada** 
    -   **somente** **WSAPlayer** é **marcada**
    -   **Não processar** é **marcada**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Capítulo 7 – criar o BotTag

1.  Criar um novo **marca** objeto chamado **BotTag**. Selecione a câmera principal na cena. Clique no menu no painel Inspetor suspenso marca. Clique em **Adicionar marca**.

    ![a instalação da câmera](images/AzureLabs-Lab312-32.png)
 
2.  Clique no **+** símbolo. Nomeie o novo **marca** como **BotTag**, *salvar*.

    ![a instalação da câmera](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **Não o fazem** se aplicam a **BotTag** para a câmera principal. Se você acidentalmente tiver feito isso, certifique-se de alterar a câmera principal marca de volta para *MainCamera*.

## <a name="chapter-8--create-the-botobjects-class"></a>Capítulo 8 – criar a classe BotObjects

É o primeiro script que você precisa criar o **BotObjects** classe, que é uma classe vazia criada para que uma série de outros objetos de classe pode ser armazenada dentro do mesmo script e acessados por outros scripts na cena.

A criação dessa classe é puramente uma opção de arquitetura, esses objetos podem ser hospedados em vez disso, no script Bot que você criará posteriormente no curso.

Para criar essa classe: 

1.  Clique com botão direito no *painel projeto*, em seguida, **criar > pasta**. Nomeie a pasta **Scripts**. 

    ![Crie a pasta de scripts.](images/AzureLabs-Lab312-36.png)

2.  Clique duas vezes no **Scripts** pasta para abri-lo. Em seguida, dentro dessa pasta, clique com botão direito e selecione **criar > C# Script**. Nomeie o script **BotObjects**. 

3.  Clique duas vezes na nova **BotObjects** script para abri-lo com **Visual Studio**.

4.  Exclua o conteúdo do script e substitua-o pelo código a seguir:

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-9--create-the-gazeinput-class"></a>Capítulo 9 – criar a classe GazeInput

A próxima classe que você pretende criar é a **GazeInput** classe. Essa classe é responsável por:

- Criar um cursor que representará o *olhares* do player.
- Detecção de objetos atingidos pelo olhar do player e mantendo uma referência a objetos detectados.

Para criar essa classe: 

1.  Vá para o **Scripts** pasta que você criou anteriormente. 
2.  Clique com botão direito dentro da pasta **criar > C# Script**. Chame o script **GazeInput**. 
3.  Clique duas vezes na nova **GazeInput** script para abri-lo com **Visual Studio**.
4.  Insira a seguinte linha à direita no topo do nome da classe:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  Em seguida, adicione as seguintes variáveis dentro de **GazeInput** classe acima a **Start ()** método:

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

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

6.  Código para o **Start ()** método deve ser adicionado. Isso será chamado quando a classe é inicializado:

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Implemente um método que será criar uma instância e o cursor de olhar de instalação: 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  Implemente os métodos que irá configurar o Raycast da câmera principal e serão manter o controle do objeto atual com foco.

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
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
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
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-10--create-the-bot-class"></a>Capítulo 10 – criar a classe de Bot

O script que você pretende criar agora é chamado **Bot**. Esta é a classe principal do seu aplicativo, ele armazena: 

- Suas credenciais de Bot do aplicativo Web
- O método que coleta os comandos de voz do usuário
- O método necessário para iniciar conversas com seu Bot de aplicativo Web 
- O método necessário para enviar mensagens ao seu Bot de aplicativo Web 

Para enviar mensagens para o serviço de Bot, o **SendMessageToBot()** corrotina criará uma atividade, que é um objeto reconhecido pela estrutura do Bot como os dados enviados pelo usuário. 
 
Para criar essa classe: 

1. Clique duas vezes no **Scripts** pasta para abri-lo. 
2. Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**. Nomeie o script **Bot**. 
3. Clique duas vezes no novo script para abri-lo com o Visual Studio.
4. Atualizar os namespaces para ser o mesmo que o seguinte, na parte superior do **Bot** classe:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. Dentro de **Bot** classe adicione as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > Certifique-se de inserir sua **chave de segredo do Bot** para o **botSecret** variável. Você irá ter anotado sua **chave de segredo do Bot** no início deste curso, em  **[capítulo 2](#chapter-2---create-the-azure-bot-service), etapa 10**.

7. Código para o **Awake()** e **Start ()** agora precisa ser adicionado. 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. Adicione os dois manipuladores são chamados pelas bibliotecas de fala quando a captura de voz começa e termina. O *DictationRecognizer* automaticamente irá parar de capturar a voz do usuário quando o usuário para falar.

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. O manipulador a seguir coleta o resultado da entrada de voz do usuário e chama a corrotina responsável por enviar a mensagem para o serviço de Bot de aplicativo Web.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. A seguir co-rotina é chamada para iniciar uma conversa com o Bot. Você observará que quando a chamada de conversa for concluída, ele chamará o **SendMessageToCoroutine()** , passando uma série de parâmetros que definirá a atividade a ser enviada para o serviço de Bot como uma mensagem vazia. Isso é feito para solicitar que o serviço de Bot para iniciar a caixa de diálogo.

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. A seguir co-rotina é chamada para criar a atividade a ser enviada para o serviço de Bot. 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. A seguir co-rotina é chamada para solicitar uma resposta após o envio de uma atividade para o serviço de Bot. 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. O último método a ser adicionado a essa classe, é necessário para exibir a mensagem na cena:

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > Você verá um erro dentro do Console do Editor do Unity, sobre ausentes a **SceneOrganiser** classe. Ignore essa mensagem, como você criará essa classe posteriormente no tutorial.

14.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-11--create-the-interactions-class"></a>Capítulo 11 – criar a classe de interações

A classe que você pretende criar agora é chamada **interações**. Essa classe é usada para detectar a entrada de toque do HoloLens do usuário. 

Se o usuário toca ao examinar a *Bot* objeto na cena e o Bot está pronto para ouvir de entradas de voz, o objeto de Bot mudará de cor para **vermelho** e começar a escutar as entradas de voz. 

Essa classe herda a **GazeInput** de classe e, portanto, é possível fazer referência a **Start ()** método e variáveis de classe, indicado pelo uso de **base**. 
 
Para criar essa classe:

1.  Clique duas vezes no **Scripts** pasta para abri-lo. 
2.  Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**. Nomeie o script **interações**. 
3.  Clique duas vezes no novo script para abri-lo com o Visual Studio.
4.  Os namespaces e a herança de classe para ser o mesmo que o seguinte, na parte superior da atualização do **interações** classe:

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  Dentro de **interações** classe adicione a seguinte variável:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  Em seguida, adicione a **Start ()** método:

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  Adicione o manipulador que será acionado quando o usuário executa o gesto de tocar na frente da câmera HoloLens

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Capítulo 12 – criar a classe SceneOrganiser

A última classe necessária neste laboratório é chamada **SceneOrganiser**. Essa classe irá configurar a cena programaticamente, adicionando scripts e componentes para a câmera principal, e criando os objetos apropriados na cena.
 
Para criar essa classe:

1.  Clique duas vezes no **Scripts** pasta para abri-lo. 
2.  Clique com botão direito dentro do **Scripts** pasta, clique em **criar > C# Script**. Nomeie o script **SceneOrganiser**. 
3.  Clique duas vezes no novo script para abri-lo com o Visual Studio.
4.  Dentro de **SceneOrganiser** classe adicione as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  Em seguida, adicione a **Awake()** e **Start ()** métodos:

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  Adicione o seguinte método, responsável por criar o objeto de Bot na cena e como configurar os parâmetros e os componentes:

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  Adicione o seguinte método, responsável por criar o objeto de interface do usuário na cena, que representa as respostas do Bot:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.
9.  No Editor do Unity, arraste a **SceneOrganiser** script da pasta de Scripts para a câmera principal. O componente de cena Gallery agora deve aparecer no objeto de câmera principal, conforme mostrado na imagem abaixo.

    ![Criar o serviço de Bot do Azure](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Capítulo 13 – antes da construção

Para executar um teste completo de seu aplicativo você precisará para fazer sideload dele para o HoloLens.
Antes de começar, verifique se:

-   Todas as configurações mencionadas a [ **capítulo 4** ](#Chapter-4-–-Set-up-the-unity-project) estão definidas corretamente. 
-   O script **SceneOrganiser** está associada a **câmera principal** objeto. 
-   No **Bot** classe, certifique-se de inserir sua **chave de segredo do Bot** no **botSecret** variável.

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Capítulo 14 – Build e carregar para o HoloLens

Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído, portanto, é hora de criá-lo do Unity.

1.  Navegue até **configurações de Build**, **arquivo > configurações de Build...** .
2.  Dos **configurações de Build** janela, clique em **Build**.

    ![Compilando o aplicativo do Unity](images/AzureLabs-Lab312-38.png)

3.  Se ainda não estiver, marque **Unity C# projetos**.
4.  Clique em **Compilar**. Unity iniciará uma **Explorador de arquivos** janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em. Criar pasta agora e nomeie- **aplicativo**. Em seguida, com o **App** pasta selecionada, clique em **Selecionar pasta**. 
5.  Unity começará a compilar seu projeto para o **aplicativo** pasta. 
6.  Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um **Explorador de arquivos** janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).

## <a name="chapter-15--deploy-to-hololens"></a>Capítulo 15 – implantar ao HoloLens

Para implantar o HoloLens:

1.  Será necessário o endereço IP do seu HoloLens (para a implantação remota) e garantir que seu HoloLens está em **modo de desenvolvedor**. Para fazer isso:

    1. Durante o uso de seu HoloLens, abra o **configurações**.
    2. Vá para **rede e Internet > Wi-Fi > Opções avançadas**
    3. Observe a **IPv4** endereço.
    4. Em seguida, navegue até **as configurações**e, em seguida, para **atualização e segurança > para desenvolvedores** 
    5. Definir o modo de desenvolvedor em.

2.  Navegue até seu novo build do Unity (o **App** pasta) e abra o arquivo de solução com **Visual Studio**.
3.  No **configuração da solução** selecionar **depurar**.
4.  No **plataforma da solução**, selecione **x86**, **máquina remota**. 

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  Vá para o **menu Build** e clique em **implantar solução**, carregar o aplicativo para o HoloLens.
6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!

    > [!NOTE]
    > Para implantar o fone de ouvido imersivo, defina as **plataforma da solução** para *Máquina Local*e defina o **configuração** para *depurar*, com *x86* como o **plataforma**. Em seguida, implantar no local de máquina, usando o **menu Build**, selecionando *implantar solução*. 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Capítulo 16 – usando o aplicativo no HoloLens

- Quando você tiver iniciado o aplicativo, você verá o Bot como um círculo azul na sua frente.

- Use o **gestos de toque** enquanto você estiver Observação na esfera para iniciar uma conversa. 
 
- Aguarde até que a conversa iniciar (a interface do usuário exibirá uma mensagem quando isso acontece). Depois de receber a mensagem introdutória do Bot, toque em novamente no Bot para que ele fique vermelho e começar a ouvir sua voz. 

- Depois que você parar de falar, seu aplicativo enviará a mensagem para o Bot e você receberá imediatamente uma resposta que será exibida na interface do usuário. 

- Repita o processo para enviar mais mensagens para seu Bot (você precisa tocar em cada vez que você deseja enviar uma mensagem).

Esta conversa demonstra como o Bot pode reter informações (seu nome), enquanto também fornecendo informações conhecidas (como os itens que estão em estoque).

#### <a name="some-questions-to-ask-the-bot"></a>Algumas perguntas a fazer o Bot:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>O aplicativo Bot de aplicativo Web (v4) concluído

Parabéns, você criou um aplicativo de realidade mista que aproveita o Bot de aplicativo Web do Azure, o Microsoft Bot Framework v4.

![Final do produto](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

A estrutura de conversa neste laboratório é muito básica. Use Microsoft LUIS para oferecer recursos de compreensão de idioma natural de seu bot.

### <a name="exercise-2"></a>Exercício 2

Este exemplo não inclui terminando uma conversa e reiniciando uma nova. Para tornar o recurso de Bot concluir, tente implementar fechamento a conversa.
