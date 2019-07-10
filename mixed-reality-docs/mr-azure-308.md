---
title: MR e Azure 308 - notificações entre dispositivos
description: Conclua este curso para aprender a implementar os Hubs de notificação do Azure, Azure Functions e o armazenamento do Azure e tabelas dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, notificação, funções, tabelas, os hubs de notificação, hololens, vr de imersão,
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694602"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>MR e o Azure 308: Notificações de vários dispositivos

![final do produto-iniciar](images/AzureLabs-Lab8-00.png)

Neste curso, você aprenderá como adicionar recursos de Hubs de notificação para um aplicativo de realidade misturada usando os Hubs de notificação do Azure, tabelas do Azure e Azure Functions.

**Os Hubs de notificação do Azure** é um serviço da Microsoft, que permite aos desenvolvedores enviar notificações por push direcionadas e personalizadas para qualquer plataforma, tudo é alimentada dentro da nuvem. Isso pode efetivamente permitem que os desenvolvedores para se comunicar com os usuários finais, ou até mesmo se comunicar entre vários aplicativos, dependendo do cenário. Para obter mais informações, visite o **os Hubs de notificação do Azure** [página](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).

**O Azure Functions** é um serviço da Microsoft, que permite que os desenvolvedores executem pequenos trechos de código, 'funções', no Azure. Isso fornece uma maneira para delegar trabalho para a nuvem, em vez de seu aplicativo local, o que pode ter muitos benefícios. **O Azure Functions** dá suporte a várias linguagens de desenvolvimento, incluindo C\#, F\#, Node. js, Java e PHP. Para obter mais informações, visite o **Azure Functions** [página](https://docs.microsoft.com/azure/azure-functions/functions-overview).

**As tabelas do Azure** é um serviço de nuvem da Microsoft, que permite aos desenvolvedores armazenar dados estruturados não-SQL na nuvem, tornando-o facilmente acessível em qualquer lugar. O serviço apresenta um design sem esquema, permitindo a evolução das tabelas conforme necessário e, portanto, é muito flexível. Para obter mais informações, visite o **tabelas do Azure** [página](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

Com a conclusão deste curso, você terá um aplicativo de imersão headset de realidade misturada e um aplicativo de Desktop PC, será possível fazer o seguinte:

1. O aplicativo de Desktop PC permitirá que o usuário mover um objeto no espaço 2D (X e Y), usando o mouse.

2. A movimentação de objetos dentro do aplicativo de computador será enviada para a nuvem usando JSON, que será na forma de uma cadeia de caracteres, que contém uma ID de objeto, tipo e transformar informações (coordenadas X e Y). 

3. O aplicativo de realidade misturada, que tem uma cena idêntica para o aplicativo da área de trabalho, receberá notificações sobre a movimentação de objeto do serviço de Hubs de notificação (que acabou de ser atualizado pelo aplicativo de Desktop PC). 

4. Ao receber uma notificação, que irá conter a ID de objeto, tipo e informações de transformação, o aplicativo de realidade misturada aplicará as informações recebidas à própria cena.

Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design. Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity. Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada. Este curso é um tutorial independente, o que não envolvem diretamente quaisquer outros laboratórios de realidade mista.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> MR e o Azure 308: Notificações de vários dispositivos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Enquanto este curso se concentra primariamente em fones de ouvido Windows Mixed Reality de imersão (VR), você também pode aplicar o que você aprenderá neste curso para o Microsoft HoloLens. Como acompanhar o curso, você verá notas quaisquer alterações que talvez seja necessário empregar para dar suporte ao HoloLens. Ao usar o HoloLens, você pode perceber algum eco durante a captura de voz.

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
- Acesso à Internet para a configuração do Azure e acessar os Hubs de notificação

## <a name="before-you-start"></a>Antes de começar

- Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).
- Você deve ser o proprietário do seu Portal do desenvolvedor Microsoft e o Portal de registro de aplicativo, caso contrário, você não terá permissão para acessar o aplicativo no [capítulo 2](#chapter-2---retrieve-your-new-apps-credentials).

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Capítulo 1 - criar um aplicativo no Portal do desenvolvedor Microsoft

Para usar o **os Hubs de notificação do Azure** serviço, você precisará criar um aplicativo no Portal do desenvolvedor da Microsoft, como seu aplicativo precisará ser registrado, para que ele possa enviar e receber notificações.

1.  Faça logon na [Portal do desenvolvedor Microsoft](https://developer.microsoft.com/dashboard).

    > Você precisará fazer logon no seu Account da Microsoft.

2.  No painel, clique em **criar um novo aplicativo**.

    ![Criar um aplicativo](images/AzureLabs-Lab8-01.png)

3.  Um pop-up será exibida, no qual você precisa reservar um nome para seu novo aplicativo. Na caixa de texto, insira um nome apropriado; Se o nome escolhido estiver disponível, um tique aparecerá à direita da caixa de texto. Quando você tiver um nome disponível inseridos, clique o **reservar nome do produto** botão na parte inferior esquerda do popup.

    ![um nome inversa](images/AzureLabs-Lab8-02.png)

4.  Com o aplicativo agora criado, você está pronto para passar para o próximo capítulo.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Capítulo 2 - recuperar suas novas credenciais de aplicativos

Faça logon no Portal de registro de aplicativo, onde seu novo aplicativo será listado e recuperar as credenciais que serão usadas para a instalação do **serviço de Hubs de notificação** dentro a **Portal do Azure**.

1.  Navegue até a [Portal de registro de aplicativo](http://apps.dev.microsoft.com).

    ![portal de registro de aplicativo](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > Você precisará usar sua Account da Microsoft para fazer logon.  
    > Isso **devem** ser Account da Microsoft que você usou anteriormente na [capítulo](#chapter-1---create-an-application-on-the-microsoft-developer-portal), com o portal do desenvolvedor do Windows Store.

2.  Você encontrará o seu aplicativo sob o **meus aplicativos** seção. Depois de encontrá-lo, clique nele e você será levado para uma nova página que tem o aplicativo do nome do sinal de adição **registro**.

    ![seu aplicativo recentemente registrado](images/AzureLabs-Lab8-04.png)

3.  Role para baixo a página de registro para encontrar seu **segredos do aplicativo** seção e a **SID do pacote** para seu aplicativo. Copiar ambos para uso com a configuração de **serviço de Hubs de notificação do Azure** no próximo capítulo.

    ![Segredos do aplicativo](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Capítulo 3 - Portal do programa de instalação do Azure: criar serviço de Hubs de notificação

Com suas credenciais de aplicativos recuperados, você precisará ir para o Portal do Azure, onde você irá criar um serviço de Hubs de notificação do Azure.

1.  Faça logon na [Portal do Azure](https://portal.azure.com).

    > [!NOTE] 
    > Se você ainda não tiver uma conta do Azure, você precisará criá-lo. Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.

2.  Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure **Hub de notificação**e clique em ***Enter***.

    ![Pesquisar hub de notificação](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > A palavra ***New*** foram substituídos por **criar um recurso**, nos portais mais recentes.

3.  A nova página fornecerá uma descrição do *os Hubs de notificação* service. Na parte inferior esquerda desse prompt, selecione a **criar** botão para criar uma associação com este serviço.

    ![Criar instância de hubs de notificação](images/AzureLabs-Lab8-07.png)

4.  Depois de clicar em ***criar***:

    1.  Insira o nome desejado para esta instância de serviço.

    2.  Fornecer um **namespace** que você poderá associar a esse aplicativo.

    3.  Selecione um **local.**

    4.  Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).

        > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal). 

    5.  Selecione uma opção apropriada **assinatura**.

    6.  Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.

    7. Selecione **Criar**.

        ![Preencha os detalhes do serviço](images/AzureLabs-Lab8-08.png)

5.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal depois que a instância do serviço é criada.

    ![notificação](images/AzureLabs-Lab8-09.png)

7.  Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço. Você será levado para a nova **Hub de notificação** instância de serviço.

    ![Ir para o recurso](images/AzureLabs-Lab8-10.png)
    
8.  Na página de visão geral, metade de página, clique em **Windows (WNS).** O painel à direita será alterado para mostrar dois campos de texto, que exigem sua **SID do pacote** e **chave de segurança**, do aplicativo que você configurou anteriormente.

    ![criado recentemente o serviço de hubs](images/AzureLabs-Lab8-11.png)

9. Depois de copiar os detalhes nos campos corretos, clique em **salvar**, e você receberá uma notificação quando o Hub de notificação foi atualizado com êxito.

    ![Anote os detalhes de segurança](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Capítulo 4 - Portal do programa de instalação do Azure: criar serviço de tabela

Depois de criar sua instância do serviço de Hubs de notificação, navegue de volta para seu Portal do Azure, onde você irá criar um serviço de tabelas do Azure, criando um recurso de armazenamento.

1.  Se ainda não estiver conectado, faça logon na [Portal do Azure](https://portal.azure.com).

2.  Depois de conectado, clique em **New** no canto superior esquerdo de canto e procure **conta de armazenamento**e clique em **Enter**.

    > [!NOTE] 
    > A palavra ***New*** foram substituídos por **criar um recurso**, nos portais mais recentes.

3.  Selecione **conta de armazenamento - blob, arquivo, tabela, fila** na lista.

    ![Procure a conta de armazenamento](images/AzureLabs-Lab8-13.png)

4.  A nova página fornecerá uma descrição do **conta de armazenamento** service. Na parte inferior esquerda desse prompt, selecione a **criar** botão para criar uma instância desse serviço.

    ![Criar instância de armazenamento](images/AzureLabs-Lab8-14.png)

5.  Depois de clicar em **criar**, um painel será exibido:

    1. Inserir sua desejada **nome** para esta instância de serviço (deve estar todo em letras maiusculas).

    2. Para **modelo de implantação**, clique em **Gerenciador de recursos**.

    3.  Para **tipo de conta**, usando o menu suspenso, selecione **(uso geral v1) de armazenamento**.

    4. Selecione uma opção apropriada **local**.
    
    5.  Para o **replicação** menu suspenso, selecione **leitura-acesso-com redundância geográfica (RA-GRS) de armazenamento**.

    6.  Para **desempenho**, clique em **padrão**.

    7.  Dentro de **transferência segura obrigatória** seção, selecione **desabilitado**.

    8.  Dos **assinatura** menu suspenso, selecione a assinatura apropriada.

    9.  Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).

        > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Deixe **redes virtuais** como **desabilitado** quando se trata de uma opção para você.

    11. Clique em **Criar**.

        ![Preencha os detalhes de armazenamento](images/AzureLabs-Lab8-15.png)

6.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

7.  Uma notificação será exibida no portal depois que a instância do serviço é criada. Clique em notificações para explorar a nova instância do serviço.

    ![nova notificação de armazenamento](images/AzureLabs-Lab8-16.png)

8.  Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço. Você será levado para a nova página de visão geral de instância de serviço de armazenamento.

    ![Ir para o recurso](images/AzureLabs-Lab8-17.PNG)

9. Na página de visão geral, para o lado direito, clique em **tabelas**.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. O painel à direita será alterado para mostrar o **do serviço tabela** informações, no qual você precisa adicionar uma nova tabela. Faça isso clicando o **+** **tabela** botão no canto superior esquerdo.

    ![abrir tabelas](images/AzureLabs-Lab8-19.png)

11. Uma nova página será mostrada, no qual você precisa inserir uma **nome da tabela**. Esse é o nome que você usará para se referir aos dados em seu aplicativo em capítulos. Insira um nome apropriado e clique em **Okey**.

    ![Criar nova tabela](images/AzureLabs-Lab8-20.png)    

12. Quando a nova tabela tiver sido criada, você poderá vê-lo dentro de **do serviço tabela** página (na parte inferior).

    ![nova tabela criada](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Capítulo 5 – Concluindo a tabela do Azure no Visual Studio

Agora que sua **do serviço tabela** conta de armazenamento tiver sido configurado, é hora de adicionar dados a ele, que será usada para armazenar e recuperar informações. A edição de suas tabelas pode ser feita por meio **Visual Studio**.

1.  Abra **Visual Studio**.

2.  No menu, clique em **modo de exibição** > **Cloud Explorer**.

    ![Abra o cloud explorer](images/AzureLabs-Lab8-22.png)

3.  O **Cloud Explorer** será aberto como um item encaixado (seja paciente, pois o carregamento pode levar tempo).

    > [!NOTE] 
    > Se a assinatura que você usou para criar sua *contas de armazenamento* não estiver visível, certifique-se de que você tenha: 
    > - Conectado à mesma conta que você usou para o Portal do Azure.
    > - Selecionado sua assinatura na página de gerenciamento de conta (talvez você precise aplicar um filtro de suas configurações de conta):  
    >
    >   ![localizar a assinatura](images/AzureLabs-Lab8-22-5.png)

4.  Os serviços de nuvem do Azure serão mostrados. Encontre **contas de armazenamento** e clique na seta à esquerda do que para expandir suas contas.

    ![Abra as contas de armazenamento](images/AzureLabs-Lab8-23.png)

5.  Quando expandida, seu recém-criado **conta de armazenamento** devem estar disponíveis. Clique na seta à esquerda de seu armazenamento e, em seguida, depois que é expandido, encontrar **tabelas** e clique na seta ao lado de que, para revelar as **tabela** você criou no último capítulo. Clique duas vezes em sua **tabela**.

    ![Abra a tabela de objetos de cena](images/AzureLabs-Lab8-24.png)

6.  A tabela será aberta no centro da janela do Visual Studio. Clique no ícone de tabela com o **+** (mais) nele.

    ![Adicionar nova tabela](images/AzureLabs-Lab8-25.png)

7.  Uma janela será exibida solicitando que você *Adicionar entidade*. Você criará três entidades no total, cada um com várias propriedades. Você observará que *PartitionKey* e *RowKey* já são fornecidas, pois eles são usados pela tabela para localizar os dados. 

    ![chave de partição e de linha](images/AzureLabs-Lab8-26.png)

8. Atualização a *valor* da **PartitionKey** e **RowKey** da seguinte maneira (Lembre-se de fazer isso para cada propriedade de linha que você adiciona, porém incrementar a RowKey cada vez):

    ![Adicione os valores corretos](images/AzureLabs-Lab8-26-5.png)

9.  Clique em **adicionar propriedade** para adicionar linhas extras de dados. Fazer com sua primeira tabela vazia que correspondam a tabela a seguir.

10. Clique em **Okey** quando tiver terminado.

    ![Clique em okey quando concluído](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Certifique-se de que você alterou o **tipo** da **X**, **Y**, e **Z**, entradas a serem **Double**. 

11. Você observará que sua tabela agora tem uma linha de dados. Clique o **+** (ícone novamente para adicionar outra entidade mais).

    ![primeira linha](images/AzureLabs-Lab8-27-5.png)

12. Criar uma propriedade adicional e, em seguida, defina os valores da nova entidade para corresponderem às mostradas abaixo.

    ![Adicionar o cubo](images/AzureLabs-Lab8-28.png)

13. Repita a última etapa para adicionar outra entidade. Defina os valores para essa entidade ao mostrado abaixo.

    ![Adicionar o cilindro](images/AzureLabs-Lab8-29.png)

14. Sua tabela agora deve ser semelhante a mostrada abaixo.

    ![tabela completa](images/AzureLabs-Lab8-30.png)

15. Você concluiu este capítulo. Certifique-se de salvar.

## <a name="chapter-6---create-an-azure-function-app"></a>Capítulo 6 - criar um aplicativo de funções do Azure

Criar um aplicativo de função do Azure, que será chamado pelo aplicativo da área de trabalho para atualizar o **tabela** de serviço e enviar uma notificação por meio de **Hub de notificação**.

Primeiro, você precisa criar um arquivo que permitirá que sua função do Azure carregar as bibliotecas que necessárias.

1.  Abra **bloco de notas** (pressione a tecla Windows e o bloco de notas do tipo).

    ![Abra o bloco de notas](images/AzureLabs-Lab8-31.png)

2.  Com o bloco de notas aberto, insira a estrutura JSON abaixo nela. Depois de ter feito isso, salve-o na área de trabalho como **Project. JSON**. É importante que a nomenclatura está correta: Certifique-se de que ele faz **não tiver uma. txt** extensão de arquivo. Esse arquivo define as bibliotecas de que sua função usará, se você tiver usado o NuGet parecerá familiar.

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  Faça logon na [Portal do Azure](https://portal.azure.com).

4.  Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure **aplicativo de funções**, pressione **Enter**.

    ![Procure o aplicativo de funções](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.

5.  A nova página fornecerá uma descrição do **aplicativo de funções** service. Na parte inferior esquerda desse prompt, selecione a **criar** botão para criar uma associação com este serviço.

    ![instância do aplicativo de função](images/AzureLabs-Lab8-33.png)

6.  Depois de clicar em **criar**, preencha o seguinte:

    1. Para **nome do aplicativo**, inserir seu nome desejado para esta instância de serviço.

    2. Selecione uma **assinatura**.

    3. Selecione o tipo de preço apropriado para você, se esta for a primeira hora de criar uma **serviço de aplicativo de função**, uma camada gratuita deve estar disponível para você.

    4. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).

        > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Para **SO**, clique em Windows, já que é a plataforma destinada.

    6. Selecione uma **plano de hospedagem** (Este tutorial está usando uma **plano de consumo**.

    7. Selecione uma **local** **(escolha o mesmo local como o armazenamento que você criou na etapa anterior)**

    8. Para o **armazenamento** seção, **você deve selecionar o serviço de armazenamento que você criou na etapa anterior**.

    9. Você não precisará *Application Insights* neste aplicativo, fique à vontade para deixá-lo **Off**.

    10. Clique em **Criar**.

        ![Criar nova instância](images/AzureLabs-Lab8-34.png)

7.  Depois de clicar em **criar** você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

8.  Uma notificação será exibida no portal depois que a instância do serviço é criada.

    ![nova notificação](images/AzureLabs-Lab8-35.png)

9.  Clique em notificações para explorar a nova instância do serviço.

10. Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço. 

    ![Ir para o recurso](images/AzureLabs-Lab8-36.png)

11. Clique o **+** (mais) ícone próximo ao *funções*, ao *criar novo*.

    ![Adicionar nova função](images/AzureLabs-Lab8-37.png)

12. No painel central, o **função** será exibida a janela de criação. Ignorar as informações na metade superior do painel e, em seguida, clique em **função personalizada**, que está localizado na parte inferior (na área azul, como mostrado abaixo).

    ![função personalizada](images/AzureLabs-Lab8-38.png)

13. A nova página dentro da janela mostrará os vários tipos de função. Role para baixo para exibir os tipos de roxos e clique em **HTTP PUT** elemento.

    ![Coloque o link de http](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Você talvez tenha que rolar ainda mais a para baixo a página (e essa imagem pode não exatamente a mesma aparência, se as atualizações do Portal do Azure terá ocorrido), no entanto, você estiver procurando por um elemento chamado *HTTP PUT*.

14. O **HTTP PUT** janela será exibida, onde você precisa configurar a função (consulte abaixo para imagem).

    1.  Para **linguagem** usando o menu suspenso, selecione C\#.

    2.  Para **nome,** um nome apropriado de entrada.

    3.  No **nível de autenticação** menu suspenso, selecione **função**.

    4.  Para o **nome da tabela** seção, você precisa usar o nome exato que você usou para criar sua **tabela** serviço anteriormente (incluindo a letra da mesma forma).

    5.  Dentro de **conexão de conta de armazenamento** seção, use o menu suspenso e selecione sua conta de armazenamento a partir daí. Se ainda não estiver lá, clique o **New** hiperlink junto com o título da seção, para mostrar outro painel, em que sua conta de armazenamento deve estar listada.

        ![novo armazenamento](images/AzureLabs-Lab8-40.png)

15. Clique em **criar** e você receberá uma notificação de que suas configurações foram atualizadas com êxito.

    ![Criar função](images/AzureLabs-Lab8-41.png)

16. Depois de clicar em **criar**, você será redirecionado para o editor de função.

    ![atualizar o código de função](images/AzureLabs-Lab8-42.png)

17. Insira o seguinte código no editor de função (substituindo o código na função):

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > Usando as bibliotecas incluídas, a função recebe o nome e o local do objeto que foi movido na cena Unity (como um C# objeto, chamado **UnityGameObject**). Esse objeto, em seguida, é usado para atualizar os parâmetros de objeto dentro da tabela criada. Depois disso, a função faz uma chamada para seu serviço de Hub de notificação criado, que notifica os aplicativos de todos os inscritos.

18. Com o código no local, clique em **salvar**.

19. Em seguida, clique o **\<** ícone (seta), no lado direito da página.

    ![Painel de upload aberto](images/AzureLabs-Lab8-43.png)

20. Um painel será Deslizar pela direita. Nesse painel, clique em **carregar**, e um navegador de arquivos será exibida.

21. Navegue até e, em seguida, clique em, o **Project. JSON** arquivo, que você criou na **bloco de notas** anteriormente e, em seguida, clique no **abrir** botão. Esse arquivo define as bibliotecas que sua função usará.

    ![carregar o json](images/AzureLabs-Lab8-44.png)

22. Quando o arquivo foi carregado, ele será exibido no painel à direita. Ao clicar nele irá abri-lo dentro de **função** editor. Ele deve parecer **exatamente** o mesmo que a próxima imagem (etapa abaixo 23).

23. Em seguida, no painel à esquerda, abaixo **funções**, clique no **integrar** link.

    ![integrar a função](images/AzureLabs-Lab8-45.png)

24. Na próxima página, no canto superior direito, clique em **editor avançado** (conforme mostrado abaixo).

    ![abrir editor avançado](images/AzureLabs-Lab8-46.png)

25. Um **Function. JSON** arquivo será aberto no painel central, que precisa ser substituído com o seguinte trecho de código. Isso define a função que você está criando e os parâmetros passados para a função.

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. O editor agora deve ser semelhante a imagem a seguir:

    ![volta para o editor padrão](images/AzureLabs-Lab8-47.png)

27. Você pode observar os parâmetros de entrada que você inseriu podem não corresponder a seus detalhes de tabela e armazenamento e, portanto, precisará ser atualizada com as informações. **Não faça isso aqui**, conforme ele é explicado a seguir. Basta clicar o **editor padrão** link no canto superior direito da página, para retornar.

28. Volta a **editor padrão**, clique em **armazenamento de tabela do Azure (tabela)** , em **entradas**. 
    
    ![Entradas de tabela](images/AzureLabs-Lab8-47-5.png)

29. Verifique se a correspondência seguinte **sua** informações, como eles podem ser diferentes (há uma imagem abaixo as etapas a seguir):

    1.  **Nome da tabela**: o nome da tabela que você criou no seu armazenamento do Azure, serviço de tabelas.

    2.  **Conexão da conta de armazenamento:** clique em **nova**, que é exibido junto com o menu suspenso e um painel será exibido à direita da janela.

        ![novo armazenamento](images/AzureLabs-Lab8-48.png)

        1.  Selecione suas **conta de armazenamento**, que você criou anteriormente para hospedar o **aplicativos de funções.**

        2. Você observará que o **conta de armazenamento** valor de conexão foi criado.

        3. Certifique-se de pressionar **salvar** quando terminar.

    3.  O **entradas** página agora deve corresponder a abaixo, mostrando **sua** informações.

        ![entradas concluída](images/AzureLabs-Lab8-49.png)

30. Em seguida, clique em **Hub de notificação do Azure (notificação)** – em **saídas**. Certifique-se a seguir correspondem à **sua** informações, como eles podem ser diferentes (há uma imagem abaixo as etapas a seguir):

    1.  **Nome do Hub de notificação**: esse é o nome do seu **Hub de notificação** instância de serviço, o que você criou anteriormente.

    2.  **Conexão de namespace de Hubs de notificação**: clique em **nova**, que é exibido junto com o menu suspenso.

        ![Verifique as saídas](images/AzureLabs-Lab8-50.png)

    3. O **Conexão** pop-up será exibida (consulte a imagem abaixo), em que você precisa selecionar o **Namespace** dos **Hub de notificação**, que você configurou anteriormente.

    4. Selecione suas **Hub de notificação** nome no menu suspenso central.

    5.  Defina as **diretiva** menu suspenso **DefaultFullSharedAccessSignature**.

    6. Clique o **selecionar** botão Voltar.

        ![atualização de saída](images/AzureLabs-Lab8-51.png)

31.  O **saídas** página agora deve corresponder a abaixo, mas com **sua** informações em vez disso. Certifique-se de pressionar **salvar**.

> [!WARNING]
> *Não edite o nome do Hub de notificação diretamente* (isso deve ser feito usando o **Editor Avançado**, desde que você seguiu as etapas anteriores corretamente.

![saídas concluída](images/AzureLabs-Lab8-50.png)

32. Neste ponto, você deve testar a função, para garantir que ele está funcionando. Para fazer isso: 

    1. Navegue até a página de função mais uma vez:

        ![saídas concluída](images/AzureLabs-Lab8-50-1.png)

    2. Na página de função, clique no **teste** guia na extrema direita da página, para abrir o *teste* folha:

        ![saídas concluída](images/AzureLabs-Lab8-50-2.png)

    3. Dentro de **corpo da solicitação** caixa de texto da folha, cole o código abaixo:

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. Com o código de teste em vigor, clique o **executar** botão na parte inferior direita e o teste será executado. Os logs de saída do teste serão exibidos na área de console, abaixo de seu código de função.

        ![saídas concluída](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Se o teste acima falhar, você precisará verificar duas vezes, você seguiu as etapas acima, exatamente, especialmente as configurações dentro do **integrar o painel**. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Capítulo 7 - configurar o projeto do Unity da área de trabalho

> [!IMPORTANT]
> O aplicativo da área de trabalho que você está criando agora **não** funcionam no Editor do Unity. Ele precisa ser executado fora do Editor, seguindo a criação do aplicativo, usando o Visual Studio (ou o aplicativo implantado). 

A seguir é um conjunto típico backup para o desenvolvimento com o Unity e realidade mista e como tal, é um bom modelo para outros projetos.

Configurar e testar o headset de realidade misturada envolvente.

> [!NOTE] 
> Você irá **não** exigem controladores de movimento para este curso. Se você precisar dar suporte a configurar o fone de ouvido imersivo, siga este [link sobre como configurar o Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra **Unity** e clique em **New**.

    ![novo projeto do unity](images/AzureLabs-Lab8-52.png)

2.  Você precisa fornecer um nome de projeto do Unity, insira **UnityDesktopNotifHub**. Verifique se o tipo de projeto é definido como **3D**. Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Criar projeto](images/AzureLabs-Lab8-53.png)

3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Vá para **edite** > **preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

    ![conjunto de ferramentas do VS externas](images/AzureLabs-Lab8-54.png)

4.  Em seguida, vá para **arquivo** > **configurações de Build** e selecione **plataforma Universal do Windows**, em seguida, clique no **alternar plataforma**botão Aplicar sua seleção.

    ![plataformas de switch](images/AzureLabs-Lab8-55.png)

5.  Enquanto estiver na **arquivo** > **configurações de Build**, certifique-se de que:

    1.  **Dispositivo de destino** é definido como **qualquer dispositivo**

        > Este aplicativo estará para sua área de trabalho, portanto, deve ser **qualquer dispositivo**

    2.  **Tipo de compilação** é definido como **D3D**

    3.  **SDK** é definido como **mais recente instalada**

    4.  **Versão do Visual Studio** é definido como **mais recente instalada**

    5.  **Compilar e executar** é definido como **Máquina Local**

    6.  Enquanto está aqui, vale a pena salvar cena e adicioná-lo para a compilação.

        1. Fazer isso selecionando **cenas abra Adicionar**. Salvamento janela será exibida.

            ![Adicionar cenas abertas](images/AzureLabs-Lab8-56.png)

        2. Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.

            ![nova pasta de cenas](images/AzureLabs-Lab8-57.png)

        3. Abrir seu recém-criado **cenas** pasta e, em seguida, no **nome do arquivo:** campo de texto, digite **NH\_Desktop\_cena**, em seguida, pressione **Salvar**.

            ![new NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  O restante de configurações, em **configurações de Build**, deverá ser deixado como padrão por enquanto.

6.  Na mesma janela, clique no **configurações do Player** botão, isso abrirá o painel relacionado no espaço em que o **Inspetor** está localizado.

7.  Neste painel, algumas configurações precisam ser verificados:

    1.  No **outras configurações** guia:

        1.  **Versão de tempo de execução de scripts** deve ser **Experimental (equivalente ao .NET 4.6)**

        2. **Script de back-end** deve ser **.NET**

        3. **Nível de compatibilidade de API** deve ser **.NET 4.6**

            ![.NET versão 4.6](images/AzureLabs-Lab8-59.png)

    2.  Dentro de **configurações de publicação** guia, em **recursos**, verifique:

        - **InternetClient**

            ![cliente de escala da internet](images/AzureLabs-Lab8-60.png)

8.  Volta **configurações de Build** *Unity C\# projetos* não fica acinzentado; marque a caixa de seleção ao lado disso.

9.  Fechar o **configurações de Build** janela.

10. Salvar sua cena e seu projeto **arquivo** > **salvar cena de arquivos** > **Salvar projeto**.

    > [!IMPORTANT]
    > Se você quiser ignorar a *configurar o Unity* componente para este projeto (aplicativo da área de trabalho) e continuar diretamente no código, fique à vontade para [baixar esse unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).  Você ainda precisará adicionar os componentes de script.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Capítulo 8 - importando as DLLs no Unity

Você usará o armazenamento do Azure para Unity (que por si só aproveita o .net SDK do Azure). Para obter mais informações, siga este [link sobre o armazenamento do Azure para Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Atualmente, há um problema conhecido no Unity que requer o plug-ins para ser reconfigurado após a importação. Estas etapas (4 a 7 desta seção) não será necessárias depois que o bug foi resolvido.

Para importar o SDK no seu próprio projeto, verifique se você baixou a versão mais recente [ **unitypackage** ](https://aka.ms/azstorage-unitysdk) do GitHub. Em seguida, faça o seguinte:

1.  Adicionar o **unitypackage** para o Unity, usando o **ativos \> Importar pacote \> pacote personalizado** opção de menu.

2.  No **Importar pacote do Unity** caixa que é exibida, você pode selecionar tudo em * **plug-in* \> * armazenamento * * *.  Desmarque todas as outras, como ele não é necessário para este curso.

    ![Importar pacote](images/AzureLabs-Lab8-61.png)

3.  Clique o ***importação*** botão para adicionar itens ao seu projeto.

4.  Vá para o **armazenamento** pasta sob **plug-ins** no projeto, exibir e selecione os seguintes plug-ins *apenas*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![desmarque qualquer plataforma](images/AzureLabs-Lab8-62.png)

5.  Com o *esses plug-ins específicos* selecionado, **desmarque** **Any Platform** e **desmarque** **WSAPlayer** em seguida, clique em **aplicar**.

    ![Aplicar as dlls de plataforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Nós estamos marcando esses plug-ins específicos para ser usado apenas no Editor do Unity. Isso ocorre porque há versões diferentes dos mesmos plug-ins na pasta WSA que será usado depois que o projeto é exportado do Unity.

6.  No **armazenamento** pasta Plug-in, selecione apenas:

    -   Microsoft.Data.Services.Client

        ![conjunto não processar para dlls](images/AzureLabs-Lab8-64.png)

7.  Verifique as **processo não** caixa sob **configurações de plataforma** e clique em ***aplicar***.

    ![não aplicar nenhum processamento](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Nós estamos marcando esse plug-in "Não processar", porque o patcher de assembly do Unity tem dificuldade para processar esse plug-in. O plug-in ainda funcionará, mesmo que ele não será processado.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Capítulo 9 - criar a classe TableToScene no projeto do Unity da área de trabalho

Agora você precisa criar os scripts que contém o código para executar este aplicativo.

É o primeiro script que você precisa criar **TableToScene**, que é responsável por:

-   Ler entidades dentro da tabela do Azure.
-   Usando os dados da tabela, determinar quais objetos ao gerar e em qual posição.

É o segundo script, você precisa criar **CloudScene**, que é responsável por:

-   Registrando o evento do botão esquerdo do mouse, para permitir que o usuário arrastar objetos em torno da cena.
-   Serializar os dados do objeto desta cena do Unity e enviá-la para o aplicativo de funções do Azure.

Para criar essa classe:

1.  Clique com botão direito no **ativo** pasta localizada no painel de projeto, **Create** > **pasta**. Nomeie a pasta **Scripts**.

    ![criar a pasta de scripts](images/AzureLabs-Lab8-66.png)

    ![Crie a pasta de scripts 2](images/AzureLabs-Lab8-67.png)

2.  Clique duas vezes na pasta recém-criada, para abri-lo.

3.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script **TableToScene**.

    ![novo script c#](images/AzureLabs-Lab8-68.png)
    ![TableToScene renomeação](images/AzureLabs-Lab8-69.png)

4.  Clique duas vezes no script para abri-lo no Visual Studio 2017.

5.  Adicione os seguintes namespaces:

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  Dentro da classe, insira as seguintes variáveis:

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > Substitua os **accountName** valor com o nome do serviço de armazenamento do Azure e **accountKey** valor com o valor da chave encontrado no serviço de armazenamento do Azure, no Portal do Azure (consulte imagem abaixo). 
    >
    > ![chave da conta de busca](images/AzureLabs-Lab8-70.png)

7.  Agora, adicione a **Start ()** e **Awake()** métodos para inicializar a classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  Dentro de **TableToScene** de classe, adicione o método que irá recuperar os valores da tabela do Azure e usá-las para gerar os primitivos apropriados na cena.

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  Fora de **TableToScene** classe, você precisa definir a classe usada pelo aplicativo para serializar e desserializar os **entidades de tabela**.

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. Verifique se você **salvar** antes de voltar ao Editor do Unity.

11. Clique o **câmera principal** da **hierarquia** do painel, para que suas propriedades aparecem na **Inspetor**.

12. Com o **Scripts** pasta aberta, selecione o script **arquivo TableToScene** e arraste-a para o **câmera principal**. O resultado deve ser conforme mostrado abaixo:

    ![Adicionar o script a câmera principal](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Capítulo 10 - criar a classe CloudScene no projeto do Unity a área de trabalho

É o segundo script, você precisa criar **CloudScene**, que é responsável por:

-   Registrando o evento do botão esquerdo do mouse, para permitir que o usuário arrastar objetos em torno da cena.

-   Serializar os dados do objeto desta cena do Unity e enviá-la para o aplicativo de funções do Azure.

Para criar o segundo script:

1.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create**, **C\# Script**. Nomeie o script **CloudScene**
    
    ![novo script c#](images/AzureLabs-Lab8-72.png)
    ![renomear CloudScene](images/AzureLabs-Lab8-73.png)

2.  Adicione os seguintes namespaces:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  Insira as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  Substitua os **azureFunctionEndpoint** valor com a URL do aplicativo de função do Azure encontrada no serviço de aplicativo de função do Azure, no Portal do Azure, conforme mostrado na imagem abaixo:

    ![obter URL de função](images/AzureLabs-Lab8-74.png)

5.  Agora, adicione a **Start ()** e **Awake()** métodos para inicializar a classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  Dentro de **Update ()** método, adicione o seguinte código que irá detectar a entrada de mouse e a ação de arrastar, que por sua vez moverá GameObjects na cena. Se o usuário tiver arrastado e solto um objeto, ele passará o nome e as coordenadas do objeto para o método **UpdateCloudScene()** , que chamará o serviço de aplicativo de funções do Azure, que atualizará a tabela do Azure e disparar o notificação.

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  Agora, adicione a **UpdateCloudScene()** método, conforme mostrado a seguir:

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  Salve o código e retorne ao Unity

9.  Arraste o **CloudScene** gerar script para o **câmera principal**. 

    1. Clique o **câmera principal** da **hierarquia** do painel, para que suas propriedades aparecem na **Inspetor**. 

    2. Com o **Scripts** aberto, selecione de pasta a **CloudScene** do script e arraste-a para o **câmera principal**. O resultado deve ser conforme mostrado abaixo:

        > ![Arraste o script de nuvem para a câmera principal](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>Capítulo 11 - compilar o projeto da área de trabalho para a UWP

Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído.

1.  Navegue até **configurações de Build** (**arquivo** > **configurações de Build**).

2.  Dos **configurações de Build** janela, clique em **Build**.

    ![Compilar projeto](images/AzureLabs-Lab8-76.png)

3.  Um **Explorador de arquivos** janela será pop-up, que pedirá um local para compilação. Crie uma nova pasta (clicando **nova pasta** no canto superior esquerdo) e nomeie-o **compilações**.

    ![nova pasta para o build](images/AzureLabs-Lab8-77.png)

    1.  Abra o novo **compilações** pasta e criar outra pasta (usando **nova pasta** mais uma vez) e nomeie- **NH\_Desktop\_aplicativo**.

        ![nome da pasta NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Com o **NH\_área de trabalho\_aplicativo** selecionado. Clique em **Selecionar pasta**. O projeto será levar um minuto ou mais para compilar.

4.  Compilação, a seguir **Explorador de arquivos** será exibida mostrando o local do novo projeto. Não há necessidade de abri-lo, no entanto, conforme necessário criar outro Unity projeto pela primeira vez, nos próximos capítulos.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Capítulo 12 - configurar o projeto do Unity realidade mista

A seguir é um conjunto típico backup para o desenvolvimento com a realidade misturada e como tal, é um bom modelo para outros projetos.

1.  Abra **Unity** e clique em **New**.

    ![novo projeto do unity](images/AzureLabs-Lab8-79.png)

2.  Agora você precisará fornecer um nome de projeto do Unity, insira **UnityMRNotifHub**. Verifique se o tipo de projeto é definido como **3D**. Defina as **local** para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![nome UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Vá para **edite** > **preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

    ![editor de conjunto externo para o VS](images/AzureLabs-Lab8-81.png)

4.  Em seguida, vá para **arquivo** > **configurações de Build** e alternar a plataforma **plataforma Universal do Windows**, clicando no **alternar plataforma**  botão.

    ![plataformas de comutador para UWP](images/AzureLabs-Lab8-82.png)

5.  Vá para **arquivo** > **configurações de Build** e certifique-se de que:

    1.  **Dispositivo de destino** é definido como **qualquer dispositivo**

        > Para o Microsoft HoloLens, defina **dispositivo de destino** à *HoloLens*.

    2.  **Tipo de compilação** é definido como **D3D**

    3.  **SDK** é definido como **mais recente instalada**

    4.  **Versão do Visual Studio** é definido como **mais recente instalada**

    5.  **Compilar e executar** é definido como **Máquina Local**

    6.  Enquanto está aqui, vale a pena salvar cena e adicioná-lo para a compilação.

        1. Fazer isso selecionando **cenas abra Adicionar**. Salvamento janela será exibida.

            ![Adicionar cenas abertas](images/AzureLabs-Lab8-83.png)

        2. Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.

            ![nova pasta de cenas](images/AzureLabs-Lab8-84.png)

        3. Abra seu recém-criado **cenas** pasta e, em seguida, no **nome do arquivo:** campo de texto, digite **NH\_MR\_cena**, em seguida, pressione  **Salvar**.

            ![new scene - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  O restante de configurações, em **configurações de Build**, deverá ser deixado como padrão por enquanto.

6.  Na mesma janela, clique no **configurações do Player** botão, isso abrirá o painel relacionado no espaço em que o **Inspetor** está localizado.    

    ![Abrir configurações do player](images/AzureLabs-Lab8-86.png)

7.  Neste painel, algumas configurações precisam ser verificados:

    1.  No **outras configurações** guia:

        1.  **Versão de tempo de execução de scripts** deve ser **Experimental** (equivalente ao .NET 4.6)
        2.  **Script de back-end** deve ser ***.NET***
        3.  **Nível de compatibilidade de API** deve ser **.NET 4.6**

            ![compatibilidade de API](images/AzureLabs-Lab8-87.png)

    2.  Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado

        ![atualizar as configurações de xr](images/AzureLabs-Lab8-88.png)        

    3.  Dentro de **configurações de publicação** guia, em **recursos**, fazer check-in:

        - **InternetClient**           

            ![cliente de escala da internet](images/AzureLabs-Lab8-89.png)

8.  Volta **configurações de Build**, **Unity C# projetos** não fica acinzentado: marque a caixa de seleção ao lado disso.

9.  Com essas alterações foi feitas, feche a janela de configurações de Build.

10. Salvar sua cena e seu projeto **arquivo** > **salvar cena de arquivos** > **Salvar projeto**.

    > [!IMPORTANT]
    > Se você quiser ignorar a *configurar o Unity* componente para este projeto (misturado realidade aplicativo) e continuar diretamente no código, fique à vontade para [baixar esse unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir [capítulo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project). Você ainda precisará adicionar os componentes de script.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Capítulo 13 - importando as DLLs no projeto do Unity realidade mista

Usando o armazenamento do Azure para a biblioteca de Unity (que usa o SDK do .net para Azure). Siga este [link sobre como usar o armazenamento do Azure com o Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).
Atualmente, há um problema conhecido no Unity que requer o plug-ins para ser reconfigurado após a importação. Estas etapas (4 a 7 desta seção) não será necessárias depois que o bug foi resolvido.

Para importar o SDK no seu próprio projeto, verifique se você baixou a versão mais recente [unitypackage](https://aka.ms/azstorage-unitysdk). Em seguida, faça o seguinte:

1.  Adicionar o unitypackage baixado acima, para o Unity, usando o **ativos** > **Importar pacote** > **pacote personalizado** opção de menu .

2.  No **Importar pacote do Unity** caixa que é exibida, você pode selecionar tudo sob **plug-in** > **armazenamento**.

    ![Importar pacote](images/AzureLabs-Lab8-90.png)

3.  Clique o **importação** botão para adicionar itens ao seu projeto.

4.  Vá para o **armazenamento** pasta sob **plug-ins** no projeto, exibir e selecione os seguintes plug-ins *apenas*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![Selecione o plug-ins](images/AzureLabs-Lab8-91.png)

5.  Com o *esses plug-ins específicos* selecionado, **desmarque** **Any Platform** e **desmarque** **WSAPlayer** em seguida, clique em **aplicar**.

    ![Aplicar alterações de plataforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Você marcar esses plug-ins específicos para ser usado apenas no Editor do Unity. Isso ocorre porque há versões diferentes dos mesmos plug-ins na pasta WSA que será usado depois que o projeto é exportado do Unity.

6.  No **armazenamento** pasta Plug-in, selecione apenas:

    -   Microsoft.Data.Services.Client

        ![Selecione o cliente de serviços de dados](images/AzureLabs-Lab8-93.png)

7.  Verifique as **processo não** caixa sob **configurações de plataforma** e clique em **aplicar**.

    ![não processar](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Você marcar esse plug-in "Não processar" porque o patcher de assembly do Unity tem dificuldade para processar esse plug-in. O plug-in ainda funcionará, mesmo que ele não será processado.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Capítulo 14 - criar a classe de TableToScene no projeto do Unity a realidade misturada

O **TableToScene** classe é idêntico àquele explicado [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project). Criar a mesma classe na projeto do Unity seguindo o mesmo procedimento explicado de realidade misturada [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).

Depois de concluir este capítulo, ambos seus **projetos do Unity** terá essa classe configurar na câmera principal.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Capítulo 15 - criar a classe de NotificationReceiver no projeto para Unity realidade mista

É o segundo script, você precisa criar **NotificationReceiver**, que é responsável por:

-   Ao registrar o aplicativo com o Hub de notificação na inicialização.
-   Escutar as notificações provenientes do Hub de notificação.
-   Os dados do objeto de notificações recebidas durante a desserialização.
-   Mova o GameObjects na cena, com base em dados desserializados.

Para criar o **NotificationReceiver** script:

1.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create**, **C\# Script**. Nomeie o script **NotificationReceiver**.

    ![criar um novo script c#](images/AzureLabs-Lab8-95.png)
    ![Nomeie-o NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  Clique duas vezes no script para abri-lo.

3.  Adicione os seguintes namespaces:

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  Insira as seguintes variáveis:

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  Substituto a **hubName** valor com o nome do serviço de Hub de notificação, e **hubListenEndpoint** valor com o valor de ponto de extremidade localizado na guia políticas de acesso, o serviço de Hub de notificação do Azure, além de Portal do Azure (veja a imagem abaixo).

    ![Inserir endpoint de política de hubs de notificação](images/AzureLabs-Lab8-97.png)

6.  Agora, adicione a **Start ()** e **Awake()** métodos para inicializar a classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  Adicione a **WaitForNotification** método para permitir que o aplicativo para receber notificações da biblioteca de Hub de notificação sem conflitos entre com o Thread principal:

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  O seguinte método, **InitNotificationAsync()** , registrará o aplicativo com a notificação de serviço do Hub na inicialização. O código é comentado, pois o Unity não poderá compilar o projeto. Quando você importa o pacote Nuget do sistema de mensagens do Azure no Visual Studio, você removerá os comentários.

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  O manipulador a seguir, **Channel\_PushNotificationReceived()** , será disparado sempre que uma notificação é recebida. Ele serão desserializados a notificação, que será a entidade de tabela do Azure que foi movido no aplicativo de área de trabalho e, em seguida, mova o GameObject correspondente na cena MR para a mesma posição. 
    
    > [!IMPORTANT]
    > O código é comentado porque o código faz referência a biblioteca de mensagens do Azure, que você irá adicionar depois de criar o projeto do Unity usando o Gerenciador de pacotes do Nuget, dentro do Visual Studio. Como tal, o projeto do Unity não poderão criar, a menos que ele é comentado. Lembre-se que deve compilar o projeto e, em seguida, deseja retornar para o Unity, você precisará **comentar novamente** que o código.

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. Lembre-se de salvar suas alterações antes de voltar ao Editor do Unity.

11. Clique o **câmera principal** da **hierarquia** do painel, para que suas propriedades aparecem na **Inspetor**.

12. Com o **Scripts** aberto, selecione de pasta a **NotificationReceiver** do script e arraste-a para o **câmera principal**. O resultado deve ser conforme mostrado abaixo:

    ![Arraste o script do destinatário de notificação à câmera](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Se você estiver desenvolvendo isso para o Microsoft HoloLens, você precisará atualizar o **câmera principal**do *câmera* componente, para que:
    > - Limpe os sinalizadores de: Cor sólida
    > - Em segundo plano: Preto

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Capítulo 16 - compilar o projeto de realidade mista para UWP

Este capítulo é idêntico ao criar processo para o projeto anterior. Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído, portanto, é hora de criá-lo do Unity.

1.  Navegue até **configurações de Build** ( **arquivo** > **configurações de Build** ).

2.  Do **configurações de Build** menu, verifique se **Unity C# projetos*** está marcada (que permitirá que você edite os scripts neste projeto, depois de compilação).

3.  Depois de fazer isso, clique em **Build**.

    ![Compilar projeto](images/AzureLabs-Lab8-99.png)

4.  Um **Explorador de arquivos** janela será pop-up, que pedirá um local para compilação. Crie uma nova pasta (clicando **nova pasta** no canto superior esquerdo) e nomeie-o **compilações**.

    ![Criar pasta builds](images/AzureLabs-Lab8-100.png)

    1.  Abra o novo **compilações** pasta e criar outra pasta (usando **nova pasta** mais uma vez) e nomeie- **NH\_MR\_aplicativo**.

        ![Criar pasta NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  Com o **NH\_MR\_aplicativo** selecionado. Clique em **Selecionar pasta**. O projeto será levar um minuto ou mais para compilar.

5.  Após a compilação, uma **Explorador de arquivos** janela será aberta no local do novo projeto.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>Capítulo 17 - adicionar pacotes NuGet para a solução UnityMRNotifHub

> [!WARNING] 
> Por favor, lembre-se de que, depois de adicionar os seguintes pacotes NuGet (e remova o código nos próximos [capítulo](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), o código, quando reaberta dentro do projeto do Unity, apresentará erros. Se você quiser voltar e continuar a editar no Editor do Unity, você precisa que o código errosome de comentário e, em seguida, remova os comentários novamente mais tarde, depois que você está de volta no Visual Studio. 

Quando a compilação de realidade misturada tiver sido concluída, navegue até o projeto de realidade misturada, que você criou, e clique duas vezes no arquivo de solução (. sln) nessa pasta, para abrir sua solução com o Visual Studio 2017.
Agora você precisará adicionar o **windowsazure** pacote do NuGet; essa é uma biblioteca que é usada para receber notificações do Hub de notificação.

Para importar o pacote do NuGet:

1.  No **Gerenciador de soluções**, clique com botão direito em sua solução

2.  Clique em **gerenciar pacotes NuGet**.

    ![Abra o Gerenciador do nuget](images/AzureLabs-Lab8-102.png)

3.  Selecione o ***navegue*** guia e pesquise **windowsazure**.

    ![localizar o pacote de sistema de mensagens do windows azure](images/AzureLabs-Lab8-103.png)

4.  Selecione o resultado (como mostrado abaixo) e na janela à direita, selecione a caixa de seleção ao lado **projeto**. Isso colocará um tique na caixa de seleção ao lado **Project**, juntamente com a caixa de seleção ao lado de **Assembly-CSharp** e **UnityMRNotifHub** projeto.

    ![todos os projetos de escala](images/AzureLabs-Lab8-104.png)

5.  A versão fornecida inicialmente **talvez não** ser compatível com este projeto. Portanto, clique no menu suspenso ao lado **versão**e clique em **versão 0.1.7.9**, em seguida, clique em **instalar**.

6.  Você terminou de instalar o pacote NuGet. Localizar inserido no código comentado a **NotificationReceiver** de classe e remova os comentários...



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Capítulo 18 - aplicativo de edição UnityMRNotifHub, classe NotificationReceiver

Após ter adicionado a **pacotes do NuGet**, você precisará *Descomente* algum código dentro a **NotificationReceiver** classe.

Isso inclui:

1. O namespace na parte superior:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Todo o código dentro de **InitNotificationsAsync()** método:

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> O código acima tem um comentário em si: Verifique se você não acidentalmente *sem marca de comentário* que de comentário (como o código não será compilado se você tiver!).

3. E, por fim, o **Channel_PushNotificationReceived** eventos:

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

Com essas sem marca de comentário, certifique-se de que você salve e, em seguida, vá para o próximo capítulo.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Capítulo 19 - associar o projeto de realidade mista para a app Store

Agora você precisa associar o **realidade misturada** projeto para o aplicativo Store criado no início do laboratório.

1.  Abra a solução.

2.  Clique com botão direito no aplicativo UWP projeto no painel Gerenciador de soluções, acesse **Store**, e **associar aplicativo com o Store...** .

    ![Abra o repositório de associação](images/AzureLabs-Lab8-105.png)

3.  Uma nova janela será exibida chamada **associar seu aplicativo com a Windows Store**. Clique em **Avançar**.

    ![Vá para a próxima tela](images/AzureLabs-Lab8-106.png)

4.  Ele carregará todos os aplicativos associados à conta que você fez logon. Se você não estiver conectado à sua conta, você poderá **fazer logon** nesta página.

5.  Localizar o **nome do aplicativo da Store** que você criou no início deste tutorial e selecioná-lo. Em seguida, clique em **Avançar**.

    ![Localize e selecione o nome do repositório](images/AzureLabs-Lab8-107.png)

6.  Clique em **associar**.

    ![associar o aplicativo](images/AzureLabs-Lab8-108.png)

7.  Seu aplicativo agora está **associados** com a App Store. Isso é necessário para habilitar as notificações.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Capítulo 20 - implantar aplicativos UnityMRNotifHub e UnityDesktopNotifHub

Este capítulo pode ser mais fácil com duas pessoas, como o resultado incluirá tanto aplicativos em execução, um que executa em seu computador Desktop e o outro dentro de imersão fone de ouvido.

O aplicativo de fone de ouvido imersivo está aguardando para receber alterações para a cena (alterações na posição dos GameObjects local) e o aplicativo da área de trabalho será fazer alterações à sua cena local (alterações de posição), que será compartilhada para o aplicativo MR. Faz sentido para implantar o aplicativo MR primeiro, seguido pelo aplicativo da área de trabalho, para que o receptor pode começar a escutar.

Para implantar o **UnityMRNotifHub** aplicativo em seu computador Local:

1.  Abra o arquivo de solução do seu **UnityMRNotifHub** app **Visual Studio 2017**.

2.  No **plataforma da solução**, selecione **x86, computador Local**.

3.  No **configuração da solução** selecionar **depurar**.

    ![definir a configuração de projeto](images/AzureLabs-Lab8-109.png)

4.  Vá para **menu Build** e clique em **implantar solução** para carregar o aplicativo em seu computador.

5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado.

Para implantar o **UnityDesktopNotifHub** aplicativo no computador Local:

1.  Abra o arquivo de solução do seu **UnityDesktopNotifHub** app **Visual Studio 2017**.

2.  No **plataforma da solução**, selecione **x86, computador Local**.

3.  No **configuração da solução** selecionar **depurar**.

    ![definir a configuração de projeto](images/AzureLabs-Lab8-110.png)

4.  Vá para **menu Build** e clique em **implantar solução** para carregar o aplicativo em seu computador.

5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado.

6.  Inicie o aplicativo de realidade misturada, seguido pelo aplicativo da área de trabalho.

Com ambos os aplicativos em execução, mova um objeto na cena da área de trabalho (usando o botão esquerdo do Mouse). Essas alterações posicionais serão feitas localmente, serializadas e enviadas para o serviço de aplicativo de funções. O serviço de aplicativo de funções, em seguida, atualizará a tabela junto com o Hub de notificação. Recebeu uma atualização, o Hub de notificação enviará os dados atualizados diretamente para todos os aplicativos registrados (no caso o aplicativo de imersão fone de ouvido), que serão então desserializar os dados de entrada e aplicar os novos dados posicionais para os objetos de local, movendo-os na cena.


## <a name="your-finished-your-azure-notification-hubs-application"></a>A conclusão de seu aplicativo de Hubs de notificação do Azure
 
Parabéns, você criou um aplicativo de realidade mista que aproveita o serviço de Hubs de notificação do Azure e permitir a comunicação entre aplicativos.
 
![final do produto-end](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Você pode trabalhar como alterar a cor dos GameObjects e enviar essa notificação para outros aplicativos, exibindo a cena?

### <a name="exercise-2"></a>Exercício 2

Você pode adicionar o movimento do GameObjects ao seu aplicativo MR e ver a cena atualizada em seu aplicativo da área de trabalho?
