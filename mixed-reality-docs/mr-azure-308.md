---
title: Sr e Azure 308-notificações entre dispositivos
description: Conclua este curso para aprender a implementar hubs de notificação do Azure, Azure Functions e armazenamento e tabelas do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, notificação, funções, tabelas, hubs de notificação, hololens, imersão, VR
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694602"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>Sr e Azure 308: Notificações entre dispositivos

![início do produto final](images/AzureLabs-Lab8-00.png)

Neste curso, você aprenderá a adicionar recursos de hubs de notificação a um aplicativo de realidade misturada usando os hubs de notificação do Azure, tabelas do Azure e Azure Functions.

Os **hubs de notificação do Azure** são um serviço da Microsoft, que permite aos desenvolvedores enviar notificações por push direcionadas e personalizadas para qualquer plataforma, tudo na nuvem. Isso pode efetivamente permitir que os desenvolvedores se comuniquem com os usuários finais ou até mesmo se comunicarem entre vários aplicativos, dependendo do cenário. Para obter mais informações, visite a [página](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview) **hubs de notificação do Azure** .

**Azure Functions** é um serviço da Microsoft, que permite aos desenvolvedores executar pequenas partes de código, ' Functions ', no Azure. Isso fornece uma maneira de delegar trabalho para a nuvem, em vez de seu aplicativo local, que pode ter muitos benefícios. O **Azure Functions** dá suporte a várias linguagens\#de desenvolvimento\#, incluindo C, F, Node. js, Java e php. Para obter mais informações, visite a [página](https://docs.microsoft.com/azure/azure-functions/functions-overview) **Azure Functions** .

As **tabelas do Azure** são um serviço de nuvem da Microsoft, que permite aos desenvolvedores armazenar dados estruturados não SQL na nuvem, tornando-os facilmente acessíveis em qualquer lugar. O serviço apresenta um design sem esquema, permitindo a evolução das tabelas conforme necessário e, portanto, é muito flexível. Para obter mais informações, visite a [página](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) **tabelas do Azure**

Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada e um aplicativo de PC desktop, que poderá fazer o seguinte:

1. O aplicativo de PC Desktop permitirá que o usuário mova um objeto em espaço 2D (X e Y), usando o mouse.

2. A movimentação de objetos no aplicativo de PC será enviada para a nuvem usando JSON, que estará na forma de uma cadeia de caracteres, contendo uma ID de objeto, tipo e informações de transformação (coordenadas X e Y). 

3. O aplicativo de realidade misturada, que tem uma cena idêntica ao aplicativo da área de trabalho, receberá notificações referentes à movimentação de objetos, do serviço de hubs de notificação (que acabou de ser atualizado pelo aplicativo de PC desktop). 

4. Após receber uma notificação, que conterá a ID do objeto, o tipo e as informações de transformação, o aplicativo de realidade misturada aplicará as informações recebidas à sua própria cena.

Em seu aplicativo, cabe a você como você integrará os resultados com seu design. Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity. É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada. Este curso é um tutorial independente, que não envolve diretamente nenhum outro laboratório de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Sr e Azure 308: Notificações entre dispositivos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Embora este curso se concentre principalmente em fones de ouvido (VR) de realidade mista do Windows, você também pode aplicar o que aprende neste curso ao Microsoft HoloLens. Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte ao HoloLens. Ao usar o HoloLens, você pode notar um eco durante a captura de voz.

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018). Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)
- [Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md#installation-checklist)
- [O SDK do Windows 10 mais recente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado
- Acesso à Internet para a instalação do Azure e para acessar os hubs de notificação

## <a name="before-you-start"></a>Antes de começar

- Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).
- Você deve ser o proprietário do seu portal do desenvolvedor da Microsoft e seu portal de registro de aplicativo, caso contrário, você não terá permissão para acessar o aplicativo no [capítulo 2](#chapter-2---retrieve-your-new-apps-credentials).

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Capítulo 1-criar um aplicativo no portal do desenvolvedor da Microsoft

Para usar o serviço de **hubs de notificação do Azure** , você precisará criar um aplicativo no portal do desenvolvedor da Microsoft, pois seu aplicativo precisará ser registrado, para que ele possa enviar e receber notificações.

1.  Faça logon no [portal do desenvolvedor da Microsoft](https://developer.microsoft.com/dashboard).

    > Você precisará fazer logon em sua conta da Microsoft.

2.  No painel, clique em **criar um novo aplicativo**.

    ![Criar um aplicativo](images/AzureLabs-Lab8-01.png)

3.  Um pop-up será exibido, onde você precisa reservar um nome para o novo aplicativo. Na caixa de texto, insira um nome apropriado; Se o nome escolhido estiver disponível, um tique aparecerá à direita da caixa de texto. Quando você tiver um nome disponível inserido, clique no botão **reservar o nome do produto** na parte inferior esquerda do pop-up.

    ![inverter um nome](images/AzureLabs-Lab8-02.png)

4.  Com o aplicativo criado agora, você está pronto para ir para o próximo capítulo.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Capítulo 2-recuperar suas novas credenciais de aplicativos

Faça logon no portal de registro de aplicativo, em que seu novo aplicativo será listado e recupere as credenciais que serão usadas para configurar o **serviço de hubs de notificação** no **portal do Azure**.

1.  Navegue até o [portal de registro de aplicativos](http://apps.dev.microsoft.com).

    ![Portal de registro de aplicativos](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > Você precisará usar sua conta da Microsoft para fazer logon.  
    > Essa **deve** ser a conta da Microsoft que você usou no [capítulo](#chapter-1---create-an-application-on-the-microsoft-developer-portal)anterior, com o portal do desenvolvedor da Windows Store.

2.  Você encontrará seu aplicativo na seção **meus aplicativos** . Depois de encontrá-lo, clique nele e você será levado para uma nova página que tem o nome do aplicativo e o **registro**.

    ![seu aplicativo recentemente registrado](images/AzureLabs-Lab8-04.png)

3.  Role para baixo na página de registro para localizar a seção **segredos do aplicativo** e o **SID do pacote** para seu aplicativo. Copie ambos para uso com a configuração do **serviço de hubs de notificação do Azure** no próximo capítulo.

    ![segredos do aplicativo](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Capítulo 3-configurar o portal do Azure: criar serviço de hubs de notificação

Com suas credenciais de aplicativos recuperadas, você precisará ir para o portal do Azure, no qual você criará um serviço de hubs de notificação do Azure.

1.  Faça logon no [portal do Azure](https://portal.azure.com).

    > [!NOTE] 
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure **Hub de notificação**e clique em ***Enter***.

    ![Pesquisar Hub de notificação](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > A palavra ***novo*** pode ter sido substituída por **criar um recurso**, em portais mais recentes.

3.  A nova página fornecerá uma descrição do serviço de *hubs de notificação* . Na parte inferior esquerda desse prompt, selecione o botão **criar** para criar uma associação com esse serviço.

    ![criar instância de hubs de notificação](images/AzureLabs-Lab8-07.png)

4.  Depois de clicar em ***criar***:

    1.  Insira o nome desejado para esta instância de serviço.

    2.  Forneça um **namespace** que você poderá associar a este aplicativo.

    3.  Selecione um **local.**

    4.  Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).

        > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal). 

    5.  Selecione uma **assinatura**apropriada.

    6.  Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.

    7. Selecione **Criar**.

        ![detalhes do serviço de preenchimento](images/AzureLabs-Lab8-08.png)

5.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![notificação](images/AzureLabs-Lab8-09.png)

7.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. Você será levado para sua nova instância de serviço do **Hub de notificação** .

    ![Ir para o recurso](images/AzureLabs-Lab8-10.png)
    
8.  Na página Visão geral, na metade inferior da página, clique em **Windows (WNS).** O painel à direita será alterado para mostrar dois campos de texto, que exigem o **SID do pacote** e a **chave de segurança**do aplicativo que você configurou anteriormente.

    ![serviço de hubs recém-criado](images/AzureLabs-Lab8-11.png)

9. Depois de copiar os detalhes nos campos corretos, clique em **salvar**e você receberá uma notificação quando o Hub de notificação tiver sido atualizado com êxito.

    ![Copiar detalhes de segurança](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Capítulo 4-configurar o portal do Azure: criar serviço de tabela

Depois de criar sua instância de serviço de hubs de notificação, navegue de volta para o portal do Azure, onde você criará um serviço de tabelas do Azure criando um recurso de armazenamento.

1.  Se ainda não estiver conectado, faça logon no [portal do Azure](https://portal.azure.com).

2.  Depois de conectado, clique em **novo** no canto superior esquerdo e procure **conta de armazenamento**e clique em **Enter**.

    > [!NOTE] 
    > A palavra ***novo*** pode ter sido substituída por **criar um recurso**, em portais mais recentes.

3.  Selecione **conta de armazenamento-BLOB, arquivo, tabela, fila** na lista.

    ![Pesquisar conta de armazenamento](images/AzureLabs-Lab8-13.png)

4.  A nova página fornecerá uma descrição do serviço de **conta de armazenamento** . Na parte inferior esquerda deste prompt, selecione o botão **criar** para criar uma instância desse serviço.

    ![criar instância de armazenamento](images/AzureLabs-Lab8-14.png)

5.  Depois de clicar em **criar**, um painel será exibido:

    1. Insira o **nome** desejado para esta instância de serviço (deve estar em letras minúsculas).

    2. Para **modelo de implantação**, clique em **Gerenciador de recursos**.

    3.  Para **tipo de conta**, usando o menu suspenso, selecione **armazenamento (uso geral v1)** .

    4. Selecione um **local**apropriado.
    
    5.  Para o menu suspenso **replicação** , selecione **armazenamento com redundância geográfica e acesso de leitura (ra-grs)** .

    6.  Para **desempenho**, clique em **padrão**.

    7.  Na seção **transferência segura necessária** , selecione **desabilitado**.

    8.  No menu suspenso **assinatura** , selecione uma assinatura apropriada.

    9.  Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).

        > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Deixe as **redes virtuais** como **desabilitadas** se essa for uma opção para você.

    11. Clique em **Criar**.

        ![preencher detalhes do armazenamento](images/AzureLabs-Lab8-15.png)

6.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

7.  Uma notificação será exibida no portal assim que a instância do serviço for criada. Clique nas notificações para explorar sua nova instância de serviço.

    ![Nova notificação de armazenamento](images/AzureLabs-Lab8-16.png)

8.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. Você será levado para sua página de visão geral da nova instância do serviço de armazenamento.

    ![Ir para o recurso](images/AzureLabs-Lab8-17.PNG)

9. Na página Visão geral, no lado direito, clique em **tabelas**.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. O painel à direita será alterado para mostrar as informações do **serviço tabela** , onde você precisa adicionar uma nova tabela. Para fazer isso, clique **+** no botão **tabela** no canto superior esquerdo.

    ![Abrir tabelas](images/AzureLabs-Lab8-19.png)

11. Uma nova página será mostrada, onde você precisa inserir um nome de **tabela**. Esse é o nome que você usará para se referir aos dados em seu aplicativo em capítulos posteriores. Insira um nome apropriado e clique em **OK**.

    ![criar nova tabela](images/AzureLabs-Lab8-20.png)    

12. Depois que a nova tabela tiver sido criada, você poderá vê-la na página de **serviço tabela** (na parte inferior).

    ![nova tabela criada](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Capítulo 5 – concluindo a tabela do Azure no Visual Studio

Agora que a conta de armazenamento do **serviço de tabela** foi configurada, é hora de adicionar dados a ela, que será usada para armazenar e recuperar informações. A edição das tabelas pode ser feita por meio do **Visual Studio**.

1.  Abra o **Visual Studio**.

2.  No menu, clique em **Exibir** > **Cloud Explorer**.

    ![abrir o Cloud Explorer](images/AzureLabs-Lab8-22.png)

3.  O **Cloud Explorer** será aberto como um item encaixado (seja paciente, pois o carregamento pode levar tempo).

    > [!NOTE] 
    > Se a assinatura que você usou para criar suas *contas de armazenamento* não estiver visível, verifique se você tem: 
    > - Conectado à mesma conta que você usou para o portal do Azure.
    > - Selecione sua assinatura na página de gerenciamento de conta (talvez seja necessário aplicar um filtro de suas configurações de conta):  
    >
    >   ![Localizar assinatura](images/AzureLabs-Lab8-22-5.png)

4.  Os serviços de nuvem do Azure serão mostrados. Localize **contas de armazenamento** e clique na seta à esquerda dela para expandir suas contas.

    ![abrir contas de armazenamento](images/AzureLabs-Lab8-23.png)

5.  Uma vez expandido, sua **conta de armazenamento** recém-criada deve estar disponível. Clique na seta à esquerda do armazenamento e, depois de expandida, localize as **tabelas** e clique na seta ao lado dela para revelar a **tabela** que você criou no último capítulo. Clique duas vezes em sua **tabela**.

    ![Abrir tabela de objetos de cena](images/AzureLabs-Lab8-24.png)

6.  Sua tabela será aberta no centro da janela do Visual Studio. Clique no ícone de tabela com **+** o (mais) nele.

    ![Adicionar nova tabela](images/AzureLabs-Lab8-25.png)

7.  Uma janela será exibida solicitando que você *adicione a entidade*. Você criará três entidades no total, cada uma com várias propriedades. Você observará que *PartitionKey* e *RowKey* já foram fornecidos, pois eles são usados pela tabela para localizar seus dados. 

    ![partição e chave de linha](images/AzureLabs-Lab8-26.png)

8. Atualize o *valor* de **PartitionKey** e **RowKey** da seguinte maneira (Lembre-se de fazer isso para cada propriedade de linha que você adicionar, ao mesmo tempo em que incrementa o RowKey a cada vez):

    ![Adicionar valores corretos](images/AzureLabs-Lab8-26-5.png)

9.  Clique em **Adicionar Propriedade** para adicionar linhas extras de dados. Faça sua primeira tabela vazia corresponder à tabela abaixo.

10. Clique em **OK** quando terminar.

    ![clique em OK quando terminar](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Verifique se você alterou o **tipo** das entradas **X**, **Y**e **Z**para **Double**. 

11. Você notará que a tabela agora tem uma linha de dados. Clique no **+** ícone (mais) novamente para adicionar outra entidade.

    ![primeira linha](images/AzureLabs-Lab8-27-5.png)

12. Crie uma propriedade adicional e, em seguida, defina os valores da nova entidade para que correspondam às mostradas abaixo.

    ![Adicionar cubo](images/AzureLabs-Lab8-28.png)

13. Repita a última etapa para adicionar outra entidade. Defina os valores dessa entidade como os mostrados abaixo.

    ![Adicionar cilindro](images/AzureLabs-Lab8-29.png)

14. Agora, sua tabela deve ser parecida com a seguinte.

    ![tabela concluída](images/AzureLabs-Lab8-30.png)

15. Você concluiu este capítulo. Certifique-se de salvar.

## <a name="chapter-6---create-an-azure-function-app"></a>Capítulo 6-criar uma Aplicativo de funções do Azure

Crie uma Aplicativo de funções do Azure, que será chamada pelo aplicativo da área de trabalho para atualizar o serviço **tabela** e enviar uma notificação por meio do **Hub de notificação**.

Primeiro, você precisa criar um arquivo que permitirá que o Azure function carregue as bibliotecas necessárias.

1.  Abra o **bloco de notas** (pressione a tecla Windows e digite notepad).

    ![abrir bloco de notas](images/AzureLabs-Lab8-31.png)

2.  Com o bloco de notas aberto, insira a estrutura JSON abaixo dele. Depois de fazer isso, salve-o em sua área de trabalho como **Project. JSON**. É importante que a nomenclatura esteja correta: Verifique se ela **não tem uma extensão de arquivo. txt** . Esse arquivo define as bibliotecas que sua função usará, se você tiver usado o NuGet, parecerá familiar.

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

3.  Faça logon no [portal do Azure](https://portal.azure.com).

4.  Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure **aplicativo de funções**, pressione **Enter**.

    ![Pesquisar o aplicativo de funções](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.

5.  A nova página fornecerá uma descrição do serviço **aplicativo de funções** . Na parte inferior esquerda desse prompt, selecione o botão **criar** para criar uma associação com esse serviço.

    ![instância do aplicativo de funções](images/AzureLabs-Lab8-33.png)

6.  Depois de clicar em **criar**, preencha o seguinte:

    1. Para **nome do aplicativo**, insira o nome desejado para esta instância de serviço.

    2. Selecione uma **assinatura**.

    3. Selecione o tipo de preço apropriado para você, se esta for a primeira vez que criar um **serviço de aplicativo de funções**, uma camada gratuita deverá estar disponível para você.

    4. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).

        > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Para o **sistema operacional**, clique em Windows, pois essa é a plataforma pretendida.

    6. Selecione um **plano de hospedagem** (este tutorial está usando um **plano de consumo**.

    7. Selecione um **local** **(escolha o mesmo local do armazenamento que você criou na etapa anterior)**

    8. Para a seção de **armazenamento** , **você deve selecionar o serviço de armazenamento criado na etapa anterior**.

    9. Você não precisará de *Application insights* neste aplicativo, portanto, fique à vontade para deixá-lo **desativado**.

    10. Clique em **Criar**.

        ![criar nova instância](images/AzureLabs-Lab8-34.png)

7.  Depois de clicar em **criar** , você precisará aguardar a criação do serviço; isso pode levar um minuto.

8.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![Nova notificação](images/AzureLabs-Lab8-35.png)

9.  Clique nas notificações para explorar sua nova instância de serviço.

10. Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. 

    ![Ir para o recurso](images/AzureLabs-Lab8-36.png)

11. Clique no **+** ícone (mais) ao lado de *funções*, para *criar novo*.

    ![Adicionar nova função](images/AzureLabs-Lab8-37.png)

12. No painel central, a janela de criação da **função** será exibida. Ignore as informações na metade superior do painel e clique em **função personalizada**, que está localizada próximo à parte inferior (na área azul, como abaixo).

    ![função personalizada](images/AzureLabs-Lab8-38.png)

13. A nova página dentro da janela mostrará vários tipos de função. Role para baixo para exibir os tipos roxos e clique no elemento **http Put** .

    ![link http put](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Talvez você precise rolar mais para baixo na página (e essa imagem pode não parecer exatamente a mesma, se as atualizações do portal do Azure tiverem sido realizadas), no entanto, você está procurando um elemento chamado *http Put*.

14. A janela **http Put** será exibida, na qual você precisa configurar a função (veja abaixo para obter a imagem).

    1.  Para **idioma,** usando o menu suspenso, selecione C\#.

    2.  Para **nome,** Insira um nome apropriado.

    3.  No menu suspenso **nível de autenticação** , selecione **função**.

    4.  Para a seção **nome da tabela** , você precisa usar o nome exato usado para criar o serviço **tabela** anteriormente (incluindo o mesmo caso de letra).

    5.  Na seção **conexão da conta de armazenamento** , use o menu suspenso e selecione sua conta de armazenamento a partir daí. Se não estiver lá, clique no **novo** hiperlink junto com o título da seção, para mostrar outro painel, em que sua conta de armazenamento deve ser listada.

        ![novo armazenamento](images/AzureLabs-Lab8-40.png)

15. Clique em **criar** e você receberá uma notificação informando que suas configurações foram atualizadas com êxito.

    ![criar função](images/AzureLabs-Lab8-41.png)

16. Depois de clicar em **criar**, você será redirecionado para o editor de funções.

    ![atualizar código de função](images/AzureLabs-Lab8-42.png)

17. Insira o código a seguir no editor de função (substituindo o código na função):

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
    > Usando as bibliotecas incluídas, a função recebe o nome e o local do objeto que foi movido na cena do Unity (como um C# objeto, chamado **UnityGameObject**). Esse objeto é usado para atualizar os parâmetros de objeto na tabela criada. Depois disso, a função faz uma chamada para o serviço de Hub de notificação criado, que notifica todos os aplicativos assinados.

18. Com o código em vigor, clique em **salvar**.

19. Em seguida, clique **\<** no ícone (seta), no lado direito da página.

    ![Abrir painel de carregamento](images/AzureLabs-Lab8-43.png)

20. Um painel será deslizado da direita. Nesse painel, clique em **carregar**e um navegador de arquivos será exibido.

21. Navegue até e clique no arquivo **Project. JSON** , que você criou anteriormente no **bloco de notas** e, em seguida, clique no botão **abrir** . Esse arquivo define as bibliotecas que sua função usará.

    ![carregar JSON](images/AzureLabs-Lab8-44.png)

22. Quando o arquivo for carregado, ele será exibido no painel à direita. Clicar nele irá abri-lo no editor de **funções** . Ele deve ser **exatamente** o mesmo que a próxima imagem (abaixo da etapa 23).

23. Em seguida, no painel à esquerda, abaixo de **funções**, clique no link **integrar** .

    ![função de integração](images/AzureLabs-Lab8-45.png)

24. Na página seguinte, no canto superior direito, clique em **Editor avançado** (como abaixo).

    ![abrir editor avançado](images/AzureLabs-Lab8-46.png)

25. Um arquivo **Function. JSON** será aberto no painel central, que precisa ser substituído pelo seguinte trecho de código. Isso define a função que você está criando e os parâmetros passados para a função.

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

26. O editor agora deve se parecer com a imagem abaixo:

    ![voltar ao editor padrão](images/AzureLabs-Lab8-47.png)

27. Você pode observar que os parâmetros de entrada que você acabou de inserir podem não corresponder aos detalhes da tabela e do armazenamento e, portanto, precisarão ser atualizados com suas informações. Não **faça isso aqui**, pois ele será abordado a seguir. Basta clicar no link **editor padrão** , no canto superior direito da página, para voltar.

28. De volta ao **editor padrão**, clique em **armazenamento de tabela do Azure (tabela)** , em **entradas**. 
    
    ![Entradas de tabela](images/AzureLabs-Lab8-47-5.png)

29. Garanta a seguinte correspondência com **suas** informações, pois elas podem ser diferentes (há uma imagem abaixo das seguintes etapas):

    1.  **Nome da tabela**: o nome da tabela que você criou em seu armazenamento do Azure, serviço de tabelas.

    2.  **Conexão da conta de armazenamento:** clique em **novo**, que aparece junto com o menu suspenso, e um painel será exibido à direita da janela.

        ![novo armazenamento](images/AzureLabs-Lab8-48.png)

        1.  Selecione sua **conta de armazenamento**, que você criou anteriormente para hospedar os **aplicativos de funções.**

        2. Você observará que o valor de conexão da **conta de armazenamento** foi criado.

        3. Certifique-se de pressionar **salvar** quando terminar.

    3.  A página de **entradas** agora deve corresponder à mostrada abaixo, mostrando **suas** informações.

        ![entradas concluídas](images/AzureLabs-Lab8-49.png)

30. Em seguida, clique em **Hub de notificação do Azure (notificação)** -em **saídas**. Verifique se os itens a seguir correspondem às **suas** informações, pois podem ser diferentes (há uma imagem abaixo das seguintes etapas):

    1.  **Nome do hub de notificação**: Este é o nome da sua instância de serviço do **Hub de notificação** , que você criou anteriormente.

    2.  **Conexão de namespace de hubs de notificação**: clique em **novo**, que aparece junto com o menu suspenso.

        ![verificar saídas](images/AzureLabs-Lab8-50.png)

    3. O pop-up de **conexão** será exibido (consulte a imagem abaixo), onde você precisa selecionar o **namespace** do **Hub de notificação**, que você configurou anteriormente.

    4. Selecione o nome do **Hub de notificação** no menu suspenso central.

    5.  Defina o menu suspenso **política** como **DefaultFullSharedAccessSignature**.

    6. Clique no botão **selecionar** para voltar.

        ![atualização de saída](images/AzureLabs-Lab8-51.png)

31.  A página de **saídas** agora deve corresponder à mostrada abaixo, mas com **suas** informações. Certifique-se de pressionar **salvar**.

> [!WARNING]
> *Não edite o nome do hub de notificação diretamente* (isso deve ser feito usando o **Editor avançado**, desde que você tenha seguido as etapas anteriores corretamente.

![saídas concluídas](images/AzureLabs-Lab8-50.png)

32. Neste ponto, você deve testar a função para garantir que ela esteja funcionando. Para fazer isso: 

    1. Navegue até a página de função mais uma vez:

        ![saídas concluídas](images/AzureLabs-Lab8-50-1.png)

    2. De volta à página função, clique na guia **teste** no canto mais à direita da página para abrir a folha *teste* :

        ![saídas concluídas](images/AzureLabs-Lab8-50-2.png)

    3. Na caixa de texto **corpo da solicitação** da folha, Cole o código abaixo:

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

    4. Com o código de teste em vigor, clique no botão **executar** na parte inferior direita e o teste será executado. Os logs de saída do teste serão exibidos na área do console, abaixo do seu código de função.

        ![saídas concluídas](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Se o teste acima falhar, você precisará verificar se você seguiu as etapas acima exatamente, principalmente as configurações no **painel integrar**. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Capítulo 7-configurar o projeto de desktop Unity

> [!IMPORTANT]
> O aplicativo de área de trabalho que você está criando agora **não** funcionará no editor do Unity. Ele precisa ser executado fora do editor, seguindo a compilação do aplicativo, usando o Visual Studio (ou o aplicativo implantado). 

Veja a seguir uma configuração típica para o desenvolvimento com o Unity e a realidade misturada e, como tal, é um bom modelo para outros projetos.

Configure e teste seu headset de imersão de realidade misturada.

> [!NOTE] 
> Você **não** precisará de controladores de animação para este curso. Se você precisar de suporte para configurar o headset de imersão, siga este [link sobre como configurar a realidade mista do Windows](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra o **Unity** e clique em **novo**.

    ![novo projeto do Unity](images/AzureLabs-Lab8-52.png)

2.  Você precisa fornecer um nome de projeto de Unity, inserir **UnityDesktopNotifHub**. Verifique se o tipo de projeto está definido como **3D**. Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Criar projeto](images/AzureLabs-Lab8-53.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar** > **preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**. Altere o **Editor de script externo** para o **Visual Studio 2017**. Feche a janela **preferências** .

    ![definir ferramentas VS externas](images/AzureLabs-Lab8-54.png)

4.  Em seguida, vá para **arquivo** > **configurações de compilação** e selecione **plataforma universal do Windows**, em seguida, clique no botão **alternar plataforma** para aplicar sua seleção.

    ![alternar plataformas](images/AzureLabs-Lab8-55.png)

5.  Ainda em**configurações de compilação**de **arquivo** > , verifique se:

    1.  O **dispositivo de destino** está definido para **qualquer dispositivo**

        > Esse aplicativo será para sua área de trabalho, portanto, deve ser **qualquer dispositivo**

    2.  O **tipo de compilação** está definido como **D3D**

    3.  O **SDK** está definido para o **mais recente instalado**

    4.  A **versão do Visual Studio** está definida para o **mais recente instalado**

    5.  **Compilar e executar** é definido como **computador local**

    6.  Enquanto isso, vale a pena salvar a cena e adicioná-la à compilação.

        1. Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.

            ![Adicionar cenas abertas](images/AzureLabs-Lab8-56.png)

        2. Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![nova pasta de cenas](images/AzureLabs-Lab8-57.png)

        3. Abra sua pasta de **cenas** recém-criada e, em seguida, no campo **nome do arquivo:** texto, digite **cena do\_NH desktop\_** e, em seguida, pressione **salvar**.

            ![novo NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  As configurações restantes, em **configurações de compilação**, devem ser deixadas como padrão por enquanto.

6.  Na mesma janela, clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o **Inspetor** está localizado.

7.  Nesse painel, algumas configurações precisam ser verificadas:

    1.  Na guia **outras configurações** :

        1.  A **versão de tempo de execução de script** deve ser **Experimental (.NET 4,6 equivalente)**

        2. O **back-end de script** deve ser **.net**

        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**

            ![versão do 4,6 net](images/AzureLabs-Lab8-59.png)

    2.  Na guia **configurações de publicação** , em **recursos**, marque:

        - **InternetClient**

            ![cliente de Internet em escala](images/AzureLabs-Lab8-60.png)

8.  De volta às **configurações de compilação** , projetos do *Unity C\#*  não ficam mais esmaecidos; marque a caixa de seleção ao lado disso.

9.  Feche a janela **configurações de compilação** .

10. Salve sua cena e **arquivo** > de projeto**salvar cena/arquivo** > **salvar projeto**.

    > [!IMPORTANT]
    > Se você quiser ignorar o componente de *configuração do Unity* para este projeto (aplicativo de desktop) e continuar diretamente no código, fique à vontade para baixá-lo [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importe-o para seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue do [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).  Ainda será necessário adicionar os componentes de script.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Capítulo 8-importando as DLLs no Unity

Você usará o armazenamento do Azure para Unity (que, por sua vez, utiliza o SDK do .net para o Azure). Para obter mais informações, siga este [link sobre o armazenamento do Azure para Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Atualmente, há um problema conhecido no Unity que exige que os plugins sejam reconfigurados após a importação. Essas etapas (4-7 nesta seção) não serão mais necessárias depois que o bug for resolvido.

Para importar o SDK para seu próprio projeto, certifique-se de ter baixado o [ **. unitypackage**](https://aka.ms/azstorage-unitysdk) mais recente do github. Em seguida, faça o seguinte:

1.  Adicione o **. unitypackage** ao Unity usando a opção de menu **pacote \> personalizado do pacote de \> importação de ativos** .

2.  Na caixa **Importar pacote de Unity** que é exibida, você pode selecionar tudo em * **plugin* \> * armazenamento * * *.  Desmarque todas as outras opções, pois elas não são necessárias para este curso.

    ![importar para pacote](images/AzureLabs-Lab8-61.png)

3.  Clique no botão ***importar*** para adicionar os itens ao seu projeto.

4.  Vá para a pasta **armazenamento** em **plug-ins** na exibição do projeto e selecione os seguintes plugins *somente*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft. WindowsAzure. Storage
    -   Newtonsoft.Json
    -   System.Spatial

![desmarcar qualquer plataforma](images/AzureLabs-Lab8-62.png)

5.  Com *esses plugins específicos* selecionados, **desmarque** **qualquer plataforma** e **desmarque** **WSAPlayer** e clique em **aplicar**.

    ![aplicar DLLs de plataforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Estamos marcando esses plugins específicos para serem usados apenas no editor do Unity. Isso ocorre porque há diferentes versões dos mesmos plug-ins na pasta WSA que serão usados depois que o projeto for exportado do Unity.

6.  Na pasta plug-in de **armazenamento** , selecione somente:

    -   Microsoft. Data. Services. Client

        ![definir não processar para DLLs](images/AzureLabs-Lab8-64.png)

7.  Marque a caixa **não processar** em **configurações da plataforma** e clique em ***aplicar***.

    ![aplicar nenhum processamento](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Estamos marcando este plug-in "não processar", porque o assembly do Unity Patcher tem dificuldade para processar esse plug-in. O plug-in ainda funcionará, embora não seja processado.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Capítulo 9-criar a classe TableToScene no projeto de desktop Unity

Agora você precisa criar os scripts que contêm o código para executar este aplicativo.

O primeiro script que você precisa criar é **TableToScene**, que é responsável por:

-   Lendo entidades na tabela do Azure.
-   Usando os dados da tabela, determine quais objetos gerar e em qual posição.

O segundo script que você precisa criar é **CloudScene**, que é responsável por:

-   Registrando o evento de clique com o botão esquerdo, para permitir que o usuário arraste objetos em volta da cena.
-   Serializar os dados de objeto desta cena do Unity e enviá-los para o Aplicativo de funções do Azure.

Para criar esta classe:

1.  Clique com o botão direito do mouse na pasta de **ativos** localizada no painel projeto, **crie** > a**pasta**. Nomeie a pasta **scripts**.

    ![criar pasta de scripts](images/AzureLabs-Lab8-66.png)

    ![criar a pasta de scripts 2](images/AzureLabs-Lab8-67.png)

2.  Clique duas vezes na pasta recém-criada para abri-la.

3.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script **TableToScene**.

    ![novo script](images/AzureLabs-Lab8-68.png)
    ![c# TableToScene renomear](images/AzureLabs-Lab8-69.png)

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
    > Substitua o valor **accountName** pelo nome do serviço de armazenamento do Azure e pelo valor de **accountKey** pelo valor de chave encontrado no serviço de armazenamento do Azure, no portal do Azure (consulte a imagem abaixo). 
    >
    > ![buscar chave de conta](images/AzureLabs-Lab8-70.png)

7.  Agora, adicione os métodos **Start ()** e **ativo ()** para inicializar a classe.

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

8.  Dentro da classe **TableToScene** , adicione o método que recuperará os valores da tabela do Azure e use-os para gerar os primitivos apropriados na cena.

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

9.  Fora da classe **TableToScene** , você precisa definir a classe usada pelo aplicativo para serializar e desserializar as **entidades de tabela**.

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

10. Certifique-se de **salvar** antes de voltar para o editor do Unity.

11. Clique na **câmera principal** do painel **hierarquia** , para que suas propriedades apareçam no **Inspetor**.

12. Com a pasta **scripts** aberta, selecione o **arquivo script TableToScene** e arraste-o para a **câmera principal**. O resultado deve ser o seguinte:

    ![Adicionar script à câmera principal](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Capítulo 10 – criar a classe CloudScene no projeto de desktop Unity

O segundo script que você precisa criar é **CloudScene**, que é responsável por:

-   Registrando o evento de clique com o botão esquerdo, para permitir que o usuário arraste objetos em volta da cena.

-   Serializar os dados de objeto desta cena do Unity e enviá-los para o Aplicativo de funções do Azure.

Para criar o segundo script:

1.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar**, **script C\#** . Nomeie o script **CloudScene**
    
    ![novo script](images/AzureLabs-Lab8-72.png)
    ![c# renomear CloudScene](images/AzureLabs-Lab8-73.png)

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

4.  Substitua o valor **azureFunctionEndpoint** pela URL de aplicativo de funções do Azure encontrada no serviço de aplicativo de funções do Azure, no portal do Azure, conforme mostrado na imagem abaixo:

    ![Obter URL da função](images/AzureLabs-Lab8-74.png)

5.  Agora, adicione os métodos **Start ()** e **ativo ()** para inicializar a classe.

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

6.  Dentro do método **Update ()** , adicione o seguinte código que irá detectar a entrada do mouse e arrastar, que, por sua vez, moverá Gameobjects na cena. Se o usuário tiver arrastado e descartado um objeto, ele passará o nome e as coordenadas do objeto para o método **UpdateCloudScene ()** , que chamará o serviço de aplicativo de funções do Azure, que atualizará a tabela do Azure e disparará a notificação.

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

7.  Agora, adicione o método **UpdateCloudScene ()** , como abaixo:

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

9.  Arraste o script **CloudScene** para a **câmera principal**. 

    1. Clique na **câmera principal** do painel **hierarquia** , para que suas propriedades apareçam no **Inspetor**. 

    2. Com a pasta **scripts** aberta, selecione o script **CloudScene** e arraste-o para a **câmera principal**. O resultado deve ser o seguinte:

        > ![Arraste o script de nuvem para a câmera principal](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>Capítulo 11-criar o projeto de desktop para UWP

Tudo o que é necessário para a seção do Unity deste projeto foi concluído.

1.  Navegue até **configurações de compilação** (**configurações de compilação**de**arquivo** > ).

2.  Na janela **configurações de compilação** , clique em **Compilar**.

    ![Compilar projeto](images/AzureLabs-Lab8-76.png)

3.  Uma janela do **Explorador de arquivos** será Popup, solicitando um local para compilar. Crie uma nova pasta (clicando em **nova pasta** no canto superior esquerdo) e nomeie-a como **Build**.

    ![nova pasta para compilação](images/AzureLabs-Lab8-77.png)

    1.  Abra a nova  pasta builds e crie outra pasta (usando a **nova pasta** mais uma vez) e nomeie-a **\_NH desktop\_app**.

        ![nome da pasta NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Com o **aplicativo\_de\_área de trabalho NH** selecionado. Clique em **Selecionar pasta**. O projeto levará um minuto ou mais para ser compilado.

4.  Após a compilação, o **Explorador de arquivos** aparecerá mostrando o local do novo projeto. No entanto, não é necessário abri-lo, pois você precisa criar o outro projeto do Unity primeiro, nos próximos capítulos.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Capítulo 12-configurar o projeto de Unity da realidade misturada

A seguir está uma configuração típica para o desenvolvimento com a realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra o **Unity** e clique em **novo**.

    ![novo projeto do Unity](images/AzureLabs-Lab8-79.png)

2.  Agora, você precisará fornecer um nome de projeto de Unity, inserir **UnityMRNotifHub**. Verifique se o tipo de projeto está definido como **3D**. Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![nome UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar** > **preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**. Altere o **Editor de script externo** para o **Visual Studio 2017**. Feche a janela **preferências** .

    ![definir editor externo como VS](images/AzureLabs-Lab8-81.png)

4.  Em seguida, vá para **arquivo** > **configurações de compilação** e alterne a plataforma para **plataforma universal do Windows**, clicando no botão **alternar plataforma** .

    ![alternar plataformas para UWP](images/AzureLabs-Lab8-82.png)

5.  Vá para **arquivo** > **configurações de compilação** e verifique se:

    1.  O **dispositivo de destino** está definido para **qualquer dispositivo**

        > Para o Microsoft HoloLens, defina o **dispositivo de destino** como *HoloLens*.

    2.  O **tipo de compilação** está definido como **D3D**

    3.  O **SDK** está definido para o **mais recente instalado**

    4.  A **versão do Visual Studio** está definida para o **mais recente instalado**

    5.  **Compilar e executar** é definido como **computador local**

    6.  Enquanto isso, vale a pena salvar a cena e adicioná-la à compilação.

        1. Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.

            ![Adicionar cenas abertas](images/AzureLabs-Lab8-83.png)

        2. Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![nova pasta de cenas](images/AzureLabs-Lab8-84.png)

        3. Abra sua pasta de **cenas** recém-criada e, em seguida, no campo **nome do arquivo:** texto, digite **\_NH Mr\_Scene**e pressione **salvar**.

            ![nova cena-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  As configurações restantes, em **configurações de compilação**, devem ser deixadas como padrão por enquanto.

6.  Na mesma janela, clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o **Inspetor** está localizado.    

    ![abrir configurações do Player](images/AzureLabs-Lab8-86.png)

7.  Nesse painel, algumas configurações precisam ser verificadas:

    1.  Na guia **outras configurações** :

        1.  A **versão de tempo de execução de script** deve ser **Experimental** (.NET 4,6 equivalente)
        2.  O **back-end de script** deve ser ***.net***
        3.  O **nível de compatibilidade da API** deve ser **.NET 4,6**

            ![compatibilidade de API](images/AzureLabs-Lab8-87.png)

    2.  Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o SDK do **Windows Mixed Reality** foi adicionado

        ![configurações de atualização XR](images/AzureLabs-Lab8-88.png)        

    3.  Na guia **configurações de publicação** , em **recursos**, verificar:

        - **InternetClient**           

            ![cliente de Internet em escala](images/AzureLabs-Lab8-89.png)

8.  De volta às **configurações de compilação**, os projetos de **Unity C#**  não ficam mais esmaecidos: marque a caixa de seleção ao lado disso.

9.  Com essas alterações feitas, feche a janela configurações de compilação.

10. Salve sua cena e **arquivo** > de projeto**salvar cena/arquivo** > **salvar projeto**.

    > [!IMPORTANT]
    > Se você quiser ignorar o componente de *configuração do Unity* para este projeto (aplicativo de realidade misturada) e continuar diretamente no código, fique à vontade para baixá-lo [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importe-o para seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue de [ Capítulo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project). Ainda será necessário adicionar os componentes de script.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Capítulo 13-importando as DLLs no projeto de Unity da realidade misturada

Você usará o armazenamento do Azure para biblioteca do Unity (que usa o SDK do .net para Azure). Siga este [link sobre como usar o armazenamento do Azure com o Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).
Atualmente, há um problema conhecido no Unity que exige que os plugins sejam reconfigurados após a importação. Essas etapas (4-7 nesta seção) não serão mais necessárias depois que o bug for resolvido.

Para importar o SDK para seu próprio projeto, certifique-se de ter baixado o [. unitypackage](https://aka.ms/azstorage-unitysdk)mais recente. Em seguida, faça o seguinte:

1.  Adicione o. unitypackage que você baixou do, para o Unity usando a opção de menu**pacote personalizado** de**importação** > de **ativos** > .

2.  Na caixa **Importar pacote de Unity** que aparece, você pode selecionar tudo em**armazenamento**de **plug-in** > .

    ![Importar pacote](images/AzureLabs-Lab8-90.png)

3.  Clique no botão **importar** para adicionar os itens ao seu projeto.

4.  Vá para a pasta **armazenamento** em **plug-ins** na exibição do projeto e selecione os seguintes plugins *somente*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft. WindowsAzure. Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![selecionar plug-ins](images/AzureLabs-Lab8-91.png)

5.  Com *esses plugins específicos* selecionados, **desmarque** **qualquer plataforma** e **desmarque** **WSAPlayer** e clique em **aplicar**.

    ![aplicar alterações de plataforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Você está marcando esses plugins específicos para serem usados apenas no editor do Unity. Isso ocorre porque há diferentes versões dos mesmos plug-ins na pasta WSA que serão usados depois que o projeto for exportado do Unity.

6.  Na pasta plug-in de **armazenamento** , selecione somente:

    -   Microsoft. Data. Services. Client

        ![selecionar cliente de serviços de dados](images/AzureLabs-Lab8-93.png)

7.  Marque a caixa **não processar** em **configurações da plataforma** e clique em **aplicar**.

    ![não processar](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Você está marcando este plug-in "não processar" porque o assembly do Unity Patcher tem dificuldade para processar esse plug-in. O plug-in ainda funcionará, embora não seja processado.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Capítulo 14-criando a classe TableToScene no projeto de Unity de realidade misturada

A classe **TableToScene** é idêntica à explicada no [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project). Crie a mesma classe no projeto de Unity de realidade misturada seguindo o mesmo procedimento explicado no [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).

Depois de concluir este capítulo, os dois projetos do **Unity** terão essa classe configurada na câmera principal.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Capítulo 15 – criando a classe NotificationReceiver no projeto de Unity de realidade misturada

O segundo script que você precisa criar é **NotificationReceiver**, que é responsável por:

-   Registrando o aplicativo com o Hub de notificação na inicialização.
-   Escutando notificações provenientes do hub de notificação.
-   Desserializando os dados de objeto de notificações recebidas.
-   Mova o GameObjects na cena, com base nos dados desserializados.

Para criar o script **NotificationReceiver** :

1.  Clique com o botão direito do mouse na pasta **scripts** , clique em **criar**, **script C\#** . Nomeie o script **NotificationReceiver**.

    ![criar novo script](images/AzureLabs-Lab8-95.png)
    ![c# nome it NotificationReceiver](images/AzureLabs-Lab8-96.png)

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

5.  Substitua o valor **hubName** pelo nome do serviço do hub de notificação e o valor **hubListenEndpoint** com o valor do ponto de extremidade encontrado na guia políticas de acesso, serviço Hub de notificação do Azure, no portal do Azure (consulte a imagem abaixo).

    ![Inserir ponto de extremidade de política de hubs de notificação](images/AzureLabs-Lab8-97.png)

6.  Agora, adicione os métodos **Start ()** e **ativo ()** para inicializar a classe.

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

7.  Adicione o método **WaitForNotification** para permitir que o aplicativo receba notificações da biblioteca do hub de notificação sem conflitar com o thread principal:

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

8.  O método a seguir, **InitNotificationAsync ()** , registrará o aplicativo com o serviço de Hub de notificação na inicialização. O código é comentado, pois o Unity não poderá compilar o projeto. Você removerá os comentários quando importar o pacote NuGet de mensagens do Azure no Visual Studio.

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

9.  O manipulador a seguir **,\_PushNotificationReceived de canal ()** , será disparado sempre que uma notificação for recebida. Ele desserializará a notificação, que será a entidade de tabela do Azure que foi movida no aplicativo da área de trabalho e, em seguida, moverá o gameobject correspondente na cena MR para a mesma posição. 
    
    > [!IMPORTANT]
    > O código é comentado porque o código faz referência à biblioteca de mensagens do Azure, que você adicionará depois de criar o projeto do Unity usando o Gerenciador de pacotes NuGet, no Visual Studio. Assim, o projeto do Unity não será capaz de Compilar, a menos que seja comentado. Lembre-se de que, se você criar seu projeto e desejar retornar ao Unity, será necessário **comentar novamente** esse código.

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

10. Lembre-se de salvar suas alterações antes de voltar para o editor do Unity.

11. Clique na **câmera principal** do painel **hierarquia** , para que suas propriedades apareçam no **Inspetor**.

12. Com a pasta **scripts** aberta, selecione o script **NotificationReceiver** e arraste-o para a **câmera principal**. O resultado deve ser o seguinte:

    ![Arraste o script do receptor de notificação para a câmera](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Se estiver desenvolvendo isso para o Microsoft HoloLens, você precisará atualizar o componente da *câmera* da **câmera principal**, para que:
    > - Limpar sinalizadores: Cor sólida
    > - Seguindo Preto

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Capítulo 16-criar o projeto de realidade misturada para UWP

Este capítulo é idêntico ao processo de compilação para o projeto anterior. Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.

1.  Navegue até **configurações de compilação** (**configurações de compilação** de **arquivo** > ).

2.  No menu **configurações de Build** , verifique se os **projetos do Unity C#** * estão com tiques (o que permitirá que você edite os scripts neste projeto, após a compilação).

3.  Depois que isso for feito, clique em **Compilar**.

    ![Compilar projeto](images/AzureLabs-Lab8-99.png)

4.  Uma janela do **Explorador de arquivos** será Popup, solicitando um local para compilar. Crie uma nova pasta (clicando em **nova pasta** no canto superior esquerdo) e nomeie-a como **Build**.

    ![criar pasta de builds](images/AzureLabs-Lab8-100.png)

    1.  Abra a nova  pasta builds e crie outra pasta (usando a **nova pasta** mais uma vez) e nomeie-a como **\_aplicativo NH\_Mr**.

        ![criar pasta NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  Com o **aplicativo\_NH\_Mr** selecionado. Clique em **Selecionar pasta**. O projeto levará um minuto ou mais para ser compilado.

5.  Após a compilação, uma janela **Explorador de arquivos** será aberta no local do novo projeto.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>Capítulo 17 – adicionar pacotes NuGet à solução UnityMRNotifHub

> [!WARNING] 
> Lembre-se de que, depois de adicionar os seguintes pacotes do NuGet (e remover o comentário do código no próximo [capítulo](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), o código, quando reaberto no projeto do Unity, apresentará erros. Se desejar voltar e continuar a edição no editor do Unity, você precisará comentar o código errosome e, em seguida, remover o comentário novamente mais tarde, depois de voltar ao Visual Studio. 

Após a conclusão da compilação da realidade misturada, navegue até o projeto de realidade misturada, que você criou e clique duas vezes no arquivo da solução (. sln) dentro dessa pasta para abrir sua solução com o Visual Studio 2017.
Agora, você precisará adicionar o pacote NuGet **WindowsAzure. Messaging. Managed** ; Esta é uma biblioteca que é usada para receber notificações do hub de notificação.

Para importar o pacote NuGet:

1.  Na **Gerenciador de soluções**, clique com o botão direito do mouse em sua solução

2.  Clique em **gerenciar pacotes NuGet**.

    ![abrir o Gerenciador do NuGet](images/AzureLabs-Lab8-102.png)

3.  Selecione a guia ***procurar*** e procure **WindowsAzure. Messaging. Managed**.

    ![Localizar pacote de mensagens do Windows Azure](images/AzureLabs-Lab8-103.png)

4.  Selecione o resultado (como mostrado abaixo) e, na janela à direita, marque a caixa de seleção ao lado de **projeto**. Isso coloca um tique na caixa de seleção ao lado de **Project**, juntamente com a caixa de seleção ao lado do projeto **assembly-Csharp** e **UnityMRNotifHub** .

    ![todos os projetos em escala](images/AzureLabs-Lab8-104.png)

5.  A versão fornecida inicialmente **pode não** ser compatível com este projeto. Portanto, clique no menu suspenso ao lado de **versão**e clique em **versão 0.1.7.9**, em seguida, clique em **instalar**.

6.  Agora você terminou de instalar o pacote NuGet. Localize o código comentado que você inseriu na classe **NotificationReceiver** e remova os comentários.



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Capítulo 18-editar aplicativo UnityMRNotifHub, classe NotificationReceiver

Depois de ter adicionado os **pacotes NuGet**, você precisará remover o *Comentário* de parte do código dentro da classe **NotificationReceiver** .

Isso inclui:

1. O namespace na parte superior:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Todo o código dentro do método **InitNotificationsAsync ()** :

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
> O código acima tem um comentário: Certifique-se de que você não tenha desmarcado *acidentalmente esse* comentário (pois o código não será compilado se você tiver!).

3. E, por fim, o evento **Channel_PushNotificationReceived** :

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

Com esses comentários, certifique-se de salvar e, em seguida, vá para o próximo capítulo.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Capítulo 19 – associar o projeto de realidade misturada ao aplicativo da loja

Agora você precisa associar o projeto de **realidade misturada** ao aplicativo da loja criado no no início do laboratório.

1.  Abra a solução.

2.  Clique com o botão direito do mouse no projeto de aplicativo UWP no painel de Gerenciador de Soluções, acesse **armazenar**e **associe o aplicativo à loja...** .

    ![abrir Associação de armazenamento](images/AzureLabs-Lab8-105.png)

3.  Uma nova janela será exibida chamada **associar seu aplicativo à Windows Store**. Clique em **Avançar**.

    ![ir para a próxima tela](images/AzureLabs-Lab8-106.png)

4.  Ele carregará todos os aplicativos associados à conta em que você fez logon. Se você não estiver conectado à sua conta, poderá **fazer logon** nesta página.

5.  Localize o **nome do aplicativo da loja** que você criou no início deste tutorial e selecione-o. Clique em **Avançar**.

    ![Localizar e selecionar o nome do repositório](images/AzureLabs-Lab8-107.png)

6.  Clique em **associar**.

    ![associar o aplicativo](images/AzureLabs-Lab8-108.png)

7.  Seu aplicativo agora está **associado** ao aplicativo da loja. Isso é necessário para habilitar as notificações.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Capítulo 20-implantar aplicativos UnityMRNotifHub e UnityDesktopNotifHub

Este capítulo pode ser mais fácil com duas pessoas, pois o resultado incluirá ambos os aplicativos em execução, um em execução na área de trabalho do computador e o outro no headset de imersão.

O aplicativo de headset de imersão está aguardando para receber alterações na cena (alterações de posição do GameObjects local) e o aplicativo de área de trabalho fará alterações em sua cena local (alterações de posição), que será compartilhada para o aplicativo MR. Faz sentido implantar o aplicativo Sr primeiro, seguido pelo aplicativo de desktop, para que o receptor possa começar a escutar.

Para implantar o aplicativo **UnityMRNotifHub** em seu computador local:

1.  Abra o arquivo de solução do seu aplicativo **UnityMRNotifHub** no **Visual Studio 2017**.

2.  Na **plataforma da solução**, selecione **x86, computador local**.

3.  Na **configuração da solução** , selecione **depurar**.

    ![definir configuração do projeto](images/AzureLabs-Lab8-109.png)

4.  Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.

5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.

Para implantar o aplicativo **UnityDesktopNotifHub** no computador local:

1.  Abra o arquivo de solução do seu aplicativo **UnityDesktopNotifHub** no **Visual Studio 2017**.

2.  Na **plataforma da solução**, selecione **x86, computador local**.

3.  Na **configuração da solução** , selecione **depurar**.

    ![definir configuração do projeto](images/AzureLabs-Lab8-110.png)

4.  Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.

5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.

6.  Inicie o aplicativo de realidade misturada, seguido pelo aplicativo de desktop.

Com ambos os aplicativos em execução, mova um objeto na cena da área de trabalho (usando o botão esquerdo do mouse). Essas alterações posicionais serão feitas localmente, serializadas e enviadas para o serviço de Aplicativo de funções. O serviço de Aplicativo de funções atualizará a tabela junto com o Hub de notificação. Após ter recebido uma atualização, o Hub de notificação enviará os dados atualizados diretamente para todos os aplicativos registrados (nesse caso, o aplicativo de headsets de imersão), que desserializará os dados de entrada e aplicará os novos dados posicionais aos objetos locais, movendo-os em cena.


## <a name="your-finished-your-azure-notification-hubs-application"></a>Seu aplicativo de hubs de notificação do Azure foi concluído
 
Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço de hubs de notificação do Azure e permite a comunicação entre aplicativos.
 
![final do produto final](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Você pode solucionar como alterar a cor do GameObjects e enviar essa notificação para outros aplicativos que visualizam a cena?

### <a name="exercise-2"></a>Exercício 2

Você pode adicionar movimento do GameObjects ao seu aplicativo MR e ver a cena atualizada em seu aplicativo de desktop?
