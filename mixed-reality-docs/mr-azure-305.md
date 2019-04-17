---
title: MR e Azure 305 - funções e armazenamento
description: Conclua este curso para aprender a implementar o armazenamento do Azure e funções dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, funções, armazenamento, hololens, vr imersivo,
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589232"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>MR e o Azure 305: Funções e armazenamento

![final do produto-iniciar](images/AzureLabs-Lab5-00.png)

Neste curso, você aprenderá como criar e usar o Azure Functions e armazenar dados com um recurso de armazenamento do Azure, dentro de um aplicativo de realidade misturada.

*O Azure Functions* é um serviço da Microsoft, que permite que os desenvolvedores executem pequenos trechos de código, 'funções', no Azure. Isso fornece uma maneira para delegar trabalho para a nuvem, em vez de seu aplicativo local, o que pode ter muitos benefícios. *O Azure Functions* dá suporte a várias linguagens de desenvolvimento, incluindo C\#, F\#, Node. js, Java e PHP. Para obter mais informações, visite o [artigo do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).

*O armazenamento do Azure* é um serviço de nuvem da Microsoft, que permite aos desenvolvedores armazenar dados, com o seguro que será altamente disponível, seguro, durável, escalonável e redundante. Isso significa que a Microsoft lidar com todos os manutenção e os problemas críticos para você. Para obter mais informações, visite o [artigo do armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction).

Com a conclusão deste curso, você terá um aplicativo de imersivo headset de realidade misturada que serão capaz de fazer o seguinte:

1.  Permitir que o usuário olhares em torno de uma cena.
2.  Dispare a geração de objetos quando o usuário gazes em um 'button' 3D.
3.  Os objetos gerados serão escolhidos por uma função do Azure.
4.  Conforme cada objeto for gerado, o aplicativo irá armazenar o tipo de objeto em um *arquivos do Azure*, localizado na *armazenamento do Azure*.
5.  Ao carregar uma segunda vez, o *arquivos do Azure* dados serão recuperados e usados para reproduzir as ações de geração da instância anterior do aplicativo.

Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design. Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity. Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td>MR e o Azure 305: Funções e armazenamento</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Enquanto este curso se concentra primariamente em fones de ouvido Windows Mixed Reality de imersão (VR), você também pode aplicar o que você aprenderá neste curso para o Microsoft HoloLens. Como acompanhar o curso, você verá notas quaisquer alterações que talvez seja necessário empregar para dar suporte ao HoloLens.

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
- Uma assinatura para uma conta do Azure para a criação de recursos do Azure
- Acesso à Internet para recuperação de dados e de instalação do Azure

## <a name="before-you-start"></a>Antes de começar

Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1 - Portal do Azure

Para usar o **serviço de armazenamento do Azure**, você precisará criar e configurar um **conta de armazenamento** no portal do Azure.

1.  Faça logon na [Portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, você precisará criá-lo. Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.

2.  Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure *conta de armazenamento*e clique em **Enter**.

    ![pesquisa de armazenamento do Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.

3.  A nova página fornecerá uma descrição do *conta de armazenamento do Azure* service. Na parte inferior esquerda desse prompt, selecione a **criar** botão para criar uma associação com este serviço.

    ![Criar serviço](images/AzureLabs-Lab5-02.png)

4.  Depois de clicar em **criar**:

    1.  Inserir uma *nome* para sua conta, lembre-se que este campo aceita apenas números e letras minúsculas.

    2.  Para *modelo de implantação*, selecione **Gerenciador de recursos**.

    3.  Para *tipo de conta*, selecione **(uso geral v1) de armazenamento**.

    4.  Determinar a *local* para seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local seria o ideal é que na região em que o aplicativo é executado. Alguns ativos do Azure estão disponíveis somente em determinadas regiões.

    5.  Para *replicação* selecionar **leitura-acesso-com redundância geográfica (RA-GRS) de armazenamento**.

    6.  Para *desempenho*, selecione **padrão**.

    7.  Deixe *transferência segura obrigatória* como **desabilitado**.

    8.  Selecione uma *assinatura*.

    9. Escolha uma *grupo de recursos* ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.

    11. Selecione **Criar**.

        ![informações do serviço de entrada](images/AzureLabs-Lab5-03.png)

5.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal depois que a instância do serviço é criada.

    ![nova notificação no portal do azure](images/AzureLabs-Lab5-04.png)

7.  Clique em notificações para explorar a nova instância do serviço.

    ![Ir para o recurso](images/AzureLabs-Lab5-05.png)

8.  Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço. Você será levado para a nova *conta de armazenamento* instância de serviço.

    ![teclas de acesso](images/AzureLabs-Lab5-06.png)

9.  Clique em *chaves de acesso*para revelar os pontos de extremidade para esse serviço de nuvem. Use *bloco de notas* ou semelhante, a cópia de uma de suas chaves para uso posterior. Além disso, observe o *cadeia de caracteres de Conexão* de valor, pois ele será usado o *AzureServices* classe, que você criará posteriormente.

    ![Copie a cadeia de caracteres de conexão](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Capítulo 2 - configurar uma função do Azure

Agora você vai escrever um **Azure** **função** no serviço do Azure.

Você pode usar um **Azure Function** fazer quase tudo o que você faria com uma função clássica no seu código, a diferença é que essa função pode ser acessada por qualquer aplicativo que tenha credenciais para acessar sua conta do Azure.

Para criar uma função do Azure:

1.  De seu *Portal do Azure*, clique em **New** no canto superior esquerdo de canto e procure *aplicativo de funções*e clique em **Enter**.

    ![Criar aplicativo de funções](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.

2.  A nova página fornecerá uma descrição do *aplicativo de funções do Azure* service. Na parte inferior esquerda desse prompt, selecione a **criar** botão para criar uma associação com este serviço.

    ![informações do aplicativo de função](images/AzureLabs-Lab5-09.png)

3.  Depois de clicar em **criar**:

    1.  Fornecer um *nome do aplicativo*. Apenas letras e números podem ser usados aqui (maiuscula ou minúscula é permitido).

    2.  Selecione sua preferência *assinatura*.

    3. Escolha uma *grupo de recursos* ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Para este exercício, selecione *Windows* como o escolhido **SO**.

    5.  Selecione *plano de consumo* para o **plano de hospedagem**.

    6.  Determinar a *local* para seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local seria o ideal é que na região em que o aplicativo é executado. Alguns ativos do Azure estão disponíveis somente em determinadas regiões. Para otimizar o desempenho, selecione a mesma região da conta de armazenamento.

    7.  Para *armazenamento*, selecione **usar existente**, e, em seguida, usando o menu suspenso, localize seu armazenamento criado anteriormente.

    8.  Deixe *Application Insights* desativado para este exercício.

        ![detalhes do aplicativo de função de entrada](images/AzureLabs-Lab5-10.png)

4.  Clique no botão **Criar**.

5.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal depois que a instância do serviço é criada.

    ![nova notificação no portal do azure](images/AzureLabs-Lab5-11.png)

7.  Clique em notificações para explorar a nova instância do serviço. 

    ![Vá para o aplicativo de funções de recurso](images/AzureLabs-Lab5-12.png)

8.  Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço. Você será levado para a nova *aplicativo de funções* instância de serviço.

9.  No *aplicativo de funções* dashboard, passe o mouse sobre *funções*encontrado dentro do painel à esquerda e, em seguida, clique no **+ (adição)** símbolo.

    ![Criar uma nova função](images/AzureLabs-Lab5-13.png)

10. Na próxima página, verifique se **Webhook + API** está selecionada e para *escolher um idioma* selecionar **CSharp**, pois esse será o idioma usado para este tutorial. Por fim, clique o **criar esta função** botão.

    ![Selecione csharp de gancho da web](images/AzureLabs-Lab5-14.png)

11. Você será levado para o código de página (Run. CSx), caso contrário, clique na função recém-criada na lista de funções dentro do painel à esquerda.

    ![Abra a nova função](images/AzureLabs-Lab5-15.png)

12. Copie o código a seguir para sua função. Essa função simplesmente retornará um inteiro aleatório entre 0 e 2 quando chamado. Não se preocupe com o código existente, fique à vontade colar na parte superior dele.

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. Clique em **Salvar**.

14. O resultado deve ser semelhante a imagem a seguir.

15. Clique em **obter a URL da função** e anote o *ponto de extremidade* exibido. Você precisará inseri-lo para o *AzureServices* classe que você criará posteriormente no curso.

    ![obter ponto de extremidade de função](images/AzureLabs-Lab5-16.png)

    ![obter ponto de extremidade de função](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Capítulo 3 - configurar o projeto do Unity

A seguir é um conjunto típico para cima para o desenvolvimento de realidade misturada e como tal, é um bom modelo para outros projetos.

Configurar e testar o headset de realidade misturada envolvente.

> [!NOTE]
> Você irá **não** exigem controladores de movimento para este curso. Se você precisar dar suporte a configurar o fone de ouvido imersivo, faça [visite a realidade misturada configurar artigo](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abrir o Unity e clique em **New**.

    ![Criar novo projeto do unity](images/AzureLabs-Lab5-17.png)

2.  Agora, você precisará fornecer um nome de projeto do Unity. Inserir **MR_Azure_Functions**. Verifique se o tipo de projeto é definido como **3D**. Defina as *local* para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Dê um nome de novo projeto do unity](images/AzureLabs-Lab5-18.png)

3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Vá para **edite* > *preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

    ![conjunto de visual studio como editor de scripts](images/AzureLabs-Lab5-19.png)

4.  Em seguida, vá para **arquivo > configurações de Build** e alterne a plataforma **plataforma Universal do Windows**, clicando no **alternar plataforma** botão.

    ![Alternar plataforma para a uwp](images/AzureLabs-Lab5-20.png)

5.  Vá para **arquivo > configurações de Build** e certifique-se de que:

    1. **Dispositivo de destino** é definido como **qualquer dispositivo**.

        > Para o Microsoft HoloLens, defina **dispositivo de destino** à *HoloLens*.

    2. **Tipo de compilação** é definido como **D3D**

    3. **SDK** é definido como **mais recente instalada**

    4. **Versão do Visual Studio** é definido como **mais recente instalada**

    5. **Compilar e executar** é definido como **Máquina Local**

    6. Salve a cena e adicioná-lo para a compilação.

        1.  Fazer isso selecionando **cenas abra Adicionar**. Salvamento janela será exibida.

            ![Adicionar cenas abertas](images/AzureLabs-Lab5-21.png)

        2.  Crie uma nova pasta para isso e qualquer futuro, cena, em seguida, selecione a **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.

            ![Criar pasta cenas](images/AzureLabs-Lab5-22.png)

        3.  Abra seu recém-criado **cenas** pasta e, em seguida, no **nome do arquivo:** campo de texto, digite **FunctionsScene**, em seguida, pressione **salvar**.

            ![Salve a cena de funções](images/AzureLabs-Lab5-23.png)

6.  O restante de configurações, em **configurações de Build**, deverá ser deixado como padrão por enquanto.

    ![Salve a cena de funções](images/AzureLabs-Lab5-24.png)

7.  No *configurações de Build* janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o *Inspetor* está localizado.

    ![configurações do Player no Inspetor](images/AzureLabs-Lab5-25.png)

8.  Neste painel, algumas configurações precisam ser verificados:

    1.  No **outras configurações** guia:

        1.  **Versão de tempo de execução de scripts** deve ser **Experimental** (equivalente ao .NET 4.6), que irá disparar uma necessidade de reiniciar o Editor.
        2.  **Script de back-end** deve ser **.NET**
        3.  **Nível de compatibilidade de API** deve ser **.NET 4.6**

    2.  Dentro de **configurações de publicação** guia, em **recursos**, verifique:
        
        -  **InternetClient**

            ![conjunto de recursos](images/AzureLabs-Lab5-26.png)

    3.  Mais para baixo no painel, no **XR configurações** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **realidade mista do Windows SDK** é adicionado.

        ![Definir configurações de XR](images/AzureLabs-Lab5-27.png)

9.  Volta *configurações de Build* *Unity C# projetos* não fica acinzentado; marque a caixa de seleção ao lado disso.

    ![projetos c# de escala](images/AzureLabs-Lab5-28.png)

10.  Feche a janela de configurações de Build.

11. Salvar sua cena e seu projeto (**arquivo > Salvar CENA / arquivo > Salvar projeto**).

## <a name="chapter-4---setup-main-camera"></a>Capítulo 4 - câmera principal de instalação

> [!IMPORTANT]
> Se você quiser ignorar a *configurar o Unity* componentes deste curso e continuar diretamente no código, fique à vontade para [baixar esse unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importe-o para seu projeto como um [personalizado Pacote](https://docs.unity3d.com/Manual/AssetPackages.html). Isso também irá conter as DLLs do próximo capítulo. Após a importação, continuar a partir [capítulo 7](#chapter-7---create-the-azureservices-class). 

1.  No *painel de hierarquia*, você encontrará um objeto chamado **câmera principal**, este objeto representa o ponto de vista de "head" quando estiver "dentro" de seu aplicativo.

2.  Com o painel do Unity na sua frente, selecione a **GameObject de câmera principal**. Você observará que o *painel Inspetor* (geralmente encontrado para a direita, no painel) mostrará os vários componentes do que *GameObject*, com *transformar* na parte superior, seguido por *câmera*e alguns outros componentes. Você precisará redefinir a transformação da câmera principal, para que ele está posicionado corretamente.

3.  Para fazer isso, selecione a **engrenagem** ícone ao lado da câmera *transformar* componente e selecione **redefinir**.

    ![Redefinir transformação](images/AzureLabs-Lab5-29.png)

4.  Em seguida, atualize o **transformar** componente para se parecer com:

    |         |    TRANSFORMAÇÃO - POSIÇÃO   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **Y**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | TRANSFORMAÇÃO - ROTAÇÃO |       |
    | :---: | :------------------: | :----:|
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRANSFORMAÇÃO - ESCALA |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 1     | 1                 | 1     |

    ![conjunto de transformação de câmera](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Capítulo 5 – configurar a cena do Unity

1.  Clique com botão direito em uma área vazia do *painel de hierarquia*, em **objeto 3D**, adicionar um **plano**.

    ![Criar novo plano](images/AzureLabs-Lab5-31.png)

2.  Com o **plano** do objeto selecionado, altere os parâmetros a seguir na *painel Inspetor*:

    |       | TRANSFORMAÇÃO - POSIÇÃO |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 4     |

    |       | TRANSFORMAÇÃO - ESCALA |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 10    | 1                 | 10    |

    ![definir posição de plano e escala](images/AzureLabs-Lab5-32.png)

    ![exibição de cena do plano](images/AzureLabs-Lab5-33.png)

3.  Clique com botão direito em uma área vazia do *painel de hierarquia*, em **objeto 3D**, adicione um **cubo**.

    1.  Renomeie o cubo **GazeButton** (com o cubo selecionado, pressione 'F2').

    2.  Alterar os seguintes parâmetros na *painel Inspetor*:

        |       | TRANSFORMAÇÃO - POSIÇÃO |       |
        | :---: | :------------------: |:-----:|
        | **X** | **Y**                | **Z** |
        | 0     | 3                    | 5     |


        ![transformação de botão de olhar conjunto](images/AzureLabs-Lab5-34.png)

        ![Mantenha o foco de exibição de cena de botão](images/AzureLabs-Lab5-35.png)

    3.  Clique no **marca** botão suspenso e clique em **Adicionar marca** para abrir o *painel de camadas de marcas de &*.

        ![Adicionar nova marca](images/AzureLabs-Lab5-36.png)

        ![Select plus](images/AzureLabs-Lab5-37.png)

    4.  Selecione o **+ (adição)** botão e, nas *novo nome de marca* , insira **GazeButton**e pressione **salvar**.

        ![nova marca de nome](images/AzureLabs-Lab5-38.png)

    5.  Clique no **GazeButton** do objeto na *painel de hierarquia*e, na *painel Inspetor*, atribuir recém-criado **GazeButton** marca.

        ![botão de olhar de atribuir a nova marca](images/AzureLabs-Lab5-39.png)

4.  Com o botão direito no **GazeButton** objeto, o *painel de hierarquia*e adicione um **GameObject vazio** (que será adicionado como um *filho* objeto).

5.  Selecione o novo objeto e renomeá-lo **ShapeSpawnPoint**.

    1.  Alterar os seguintes parâmetros na *painel Inspetor*:

        |       | TRANSFORMAÇÃO - POSIÇÃO |       |
        | :---: | :------------------: |:----: |
        | **X** |**Y**                 | **Z** |
        | 0     | -1                   | 0     |

        ![transformação de ponto de geração de forma de atualização](images/AzureLabs-Lab5-40.png)

        ![exibição de cena de ponto de geração de forma](images/AzureLabs-Lab5-41.png)

6.  Em seguida você irá criar uma **texto 3D** objeto para fornecer comentários sobre o status do serviço do Azure.

    Clique com botão direito do **GazeButton** na hierarquia de painel novamente e adicione um **objeto 3D > texto 3D** do objeto como um *filho*.

    ![criar um novo objeto de texto 3D](images/AzureLabs-Lab5-42.png)

7.  Renomeie o **texto 3D** objeto **AzureStatusText**.

8.  Alterar o **AzureStatusText** transformação do objeto da seguinte maneira:

    |       | TRANSFORMAÇÃO - POSIÇÃO |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | TRANSFORMAÇÃO - ESCALA |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > Não se preocupe se ele aparenta estar desativado centre, pois isso será corrigido quando o abaixo do texto de malha componente é atualizado.

9.  Alterar o **texto de malha** componente para corresponder a abaixo:

    ![componente de malha do conjunto de texto](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > A cor selecionada aqui é a cor hexadecimal: **000000FF**, no entanto, fique à vontade para escolher seus próprios, apenas verifique se ele está legível.

10. A estrutura de hierarquia painel agora deve ser assim:

    ![texto de malha no modo de exibição de cena](images/AzureLabs-Lab5-43b.png)

10. Agora, sua cena deve ser assim:

    ![texto de malha no modo de exibição de cena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Capítulos 6 - importar do armazenamento do Azure para Unity

Você usará o armazenamento do Azure para Unity (que por si só aproveita o .net SDK do Azure). Você pode ler mais sobre isso na [armazenamento do Azure para o artigo do Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Atualmente, há um problema conhecido no Unity que requer o plug-ins para ser reconfigurado após a importação. Estas etapas (4 a 7 desta seção) não será necessárias depois que o bug foi resolvido.

Para importar o SDK no seu próprio projeto, verifique se você baixou a versão mais recente [unitypackage do GitHub](https://aka.ms/azstorage-unitysdk). Em seguida, faça o seguinte:

1.  Adicione a **unitypackage** arquivo para o Unity, usando o **ativos > Importar pacote > pacote personalizado** opção de menu.

2.  No **Importar pacote do Unity** caixa que é exibida, você pode selecionar tudo sob **plug-in* > * * * de armazenamento. Desmarque todas as outras, como ele não é necessário para este curso.

    ![Importar pacote](images/AzureLabs-Lab5-45.png)

3.  Clique o **importação** botão para adicionar itens ao seu projeto.

4.  Vá para o *armazenamento* pasta sob *plug-ins*, na exibição do projeto e selecione os seguintes plug-ins *apenas*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![desmarque qualquer plataforma](images/AzureLabs-Lab5-46.png)

5.  Com o *esses plug-ins específicos* selecionado, **desmarque** *Any Platform* e **desmarque** *WSAPlayer* em seguida, clique em **aplicar**.

    ![Aplicar as dlls de plataforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Nós estamos marcando esses plug-ins específicos para ser usado apenas no Editor do Unity. Isso ocorre porque há versões diferentes dos mesmos plug-ins na pasta WSA que será usado depois que o projeto é exportado do Unity.

6.  No *armazenamento* pasta Plug-in, selecione apenas:

    -   Microsoft.Data.Services.Client

        ![conjunto não processar para dlls](images/AzureLabs-Lab5-48.png)

7.  Verifique as **processo não** caixa sob *configurações de plataforma* e clique em **aplicar**.

    ![não aplicar nenhum processamento](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Nós estamos marcando esse plug-in "Não processar" porque o patcher de assembly do Unity tem dificuldade para processar esse plug-in. O plug-in ainda funcionará, mesmo que ele não será processado.

## <a name="chapter-7---create-the-azureservices-class"></a>Capítulo 7 - criar a classe AzureServices

É a primeira classe que você pretende criar o *AzureServices* classe.

O *AzureServices* classe será responsável por:

-   Armazenar credenciais de conta do Azure.

-   Chamando a função de aplicativo do Azure.

-   O upload e download de arquivo de dados em seu armazenamento em nuvem do Azure.

Para criar essa classe:

1.  Clique com botão direito no *Asset* pasta, localizada no painel de projeto, **criar > pasta**. Nomeie a pasta **Scripts**.

    ![Criar nova pasta](images/AzureLabs-Lab5-50.png)

    ![pasta chamada - scripts](images/AzureLabs-Lab5-51.png)

2.  Clique duas vezes na pasta recém-criada, para abri-lo.

3.  Clique com botão direito dentro da pasta **criar > C# Script**. Chame o script *AzureServices*.

4.  Clique duas vezes na nova *AzureServices* classe para abri-lo com *Visual Studio*.

5.  Adicione os seguintes namespaces na parte superior do *AzureServices*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Adicione os seguintes campos de Inspetor de dentro de *AzureServices* classe:

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  Em seguida, adicione as seguintes variáveis de membro dentro de *AzureServices* classe:

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > Verifique se você substituir a *ponto de extremidade* e *cadeia de caracteres de conexão* valores com os valores do armazenamento do Azure, encontradas no Portal do Azure

8.  Código para o *Awake()* e *Start ()* métodos agora precisa ser adicionado. Esses métodos serão chamados quando inicializa a classe:

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > Podemos preencherá o código para *CallAzureFunctionForNextShape()* em um [capítulo futuras](#chapter-10---completing-the-AzureServices-class).

9.  Excluir o *Update ()* método uma vez que essa classe não irá usá-lo.

10. Salve suas alterações no Visual Studio e, em seguida, retornar para o Unity.

11. Clique e arraste a *AzureServices* classe da pasta de Scripts para o objeto de câmera principal na *painel de hierarquia*.

12. Selecione a câmera principal, em seguida, pegue o **AzureStatusText** objeto filho abaixo do **GazeButton** de objeto e coloque-o no **AzureStatusText** destino da referência campo, o *Inspector*, para fornecer a referência para o *AzureServices* script.

    ![atribuir o destino de referência de texto de status do azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Capítulo 8 - criar a classe ShapeFactory

É o próximo script para criar, o *ShapeFactory* classe. A função dessa classe é criar uma nova forma, quando solicitado e manter um histórico das formas criado em uma *lista de histórico de forma*. Sempre que uma forma é criada, o *lista do histórico de forma* é atualizado na *AzureService* classe e, em seguida, armazenadas no seu *armazenamento do Azure*. Quando o aplicativo for iniciado, se um arquivo armazenado for encontrado no seu *armazenamento do Azure*, o *lista do histórico de forma* é recuperado e repetidos, com o **texto 3D** fornecendo de objeto Se a forma gerada é do armazenamento ou novo.

Para criar essa classe:

1.  Vá para o **Scripts** pasta que você criou anteriormente.

2.  Clique com botão direito dentro da pasta **criar > C# Script**. Chame o script *ShapeFactory*.

3.  Clique duas vezes na nova *ShapeFactory* script para abri-lo com *Visual Studio*.

4.  Verifique se o *ShapeFactory* classe inclui os seguintes namespaces:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Adicione as variáveis mostradas abaixo para o *ShapeFactory* classe e substituir o *Start ()* e *Awake()* funções com aquelas abaixo:

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  O *createShape ()* método gera as formas primitivas, com base em fornecido *inteiro* parâmetro. O parâmetro booliano é usado para especificar se a forma atualmente criada do armazenamento, ou novo. Coloque o seguinte código no seu *ShapeFactory* classe abaixo dos métodos anteriores:

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  Certifique-se de salvar suas alterações no Visual Studio antes de retornar para o Unity.

8.  Novamente no Editor do Unity, clique e arraste a *ShapeFactory* classe a **Scripts** pasta para o **câmera principal** do objeto no *hierarquia painel*.

9. Com a câmera principal selecionado, você vai notar a *ShapeFactory* componente de script está faltando a *Spawn ponto* referência. Para corrigi-lo, arraste a **ShapeSpawnPoint** de objeto a *painel de hierarquia* para o **Spawn ponto** destino da referência.

    ![destino da referência do conjunto de forma factory](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Capítulo 9 - criar a classe de olhar

É o último script que você precisa criar o *olhares* classe.

Essa classe é responsável por criar uma **Raycast** que será projetado para a frente da câmera principal, para detectar qual objeto de usuário está observando. Nesse caso, o Raycast precisará identificar se o usuário está observando o **GazeButton** do objeto na cena e disparar um comportamento.

Para criar essa classe:

1.  Vá para o **Scripts** pasta que você criou anteriormente.

2.  Clique com botão direito no painel de projeto, **criar > C# Script**. Chame o script *olhares*.

3.  Clique duas vezes na nova *olhares* script para abri-lo com *Visual Studio.*

4.  Certifique-se de que o namespace a seguir está incluído na parte superior do script:

    ```csharp
        using UnityEngine;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro do *olhares* classe:

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> Algumas dessas variáveis poderão ser editados na *Editor*.

6.  Código para o *Awake()* e *Start ()* métodos agora precisa ser adicionado.

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Adicione o código a seguir, que criará um objeto de cursor no início, juntamente com o *Update ()* método, que executará o método Raycast, além de ser onde o booliano GazeEnabled é alternada:

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. Em seguida adicione a *UpdateRaycast()* método, que será um Raycast do projeto e detectar o destino de ocorrência.

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

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

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. Por fim, adicione a *ResetFocusedObject()* método, que irá ativar/desativar a GazeButton objetos cor atual, que indica se ele está criando uma nova forma ou não.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  Salve suas alterações no Visual Studio antes de retornar para o Unity.

11.  Clique e arraste a *olhares* classe a partir da pasta de Scripts para o **câmera principal** objeto o *painel de hierarquia*.

## <a name="chapter-10---completing-the-azureservices-class"></a>Capítulo 10 - Concluindo a classe AzureServices

Com os outros scripts em vigor, é possível *concluída* as *AzureServices* classe. Isso será feito por meio de:

1.  Adicionando um novo método chamado *CreateCloudIdentityAsync()* para configurar as variáveis de autenticação necessárias para se comunicar com o Azure.

    > Esse método também verificará a existência de um arquivo armazenado anteriormente que contém a lista de forma.
    >
    > **Se o arquivo for encontrado**, ele desativará o usuário *olhares*e disparar a criação de forma, acordo com o padrão de formas, conforme armazenado no **arquivo de armazenamento do Azure**. O usuário pode ver isso, como o **texto de malha** fornecerá a exibição 'Armazenamento' ou 'New', dependendo da origem de formas.
    >
    > **Se nenhum arquivo for encontrado**, ele permitirá que o *olhares*, permitindo que o usuário criar formas ao examinar o **GazeButton** objeto na cena.

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  O próximo trecho de código é de dentro de *Start ()* método; no qual você será feita uma chamada para o *CreateCloudIdentityAsync()* método. Fique à vontade copiar sobre as atuais *Start ()* método, com a abaixo:

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  Preencher o código para o método *CallAzureFunctionForNextShape()*. Você usará o criado anteriormente *aplicativo de funções do Azure* para solicitar um índice de forma. Depois que a nova forma é recebida, este método enviará a forma para o *ShapeFactory* classe para criar a nova forma na cena. Use o código a seguir para concluir o corpo da *CallAzureFunctionForNextShape()*.

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  Adicione um método para criar uma cadeia de caracteres concatenando os inteiros armazenados na lista de histórico de forma e salvá-los em seu *arquivos de armazenamento do Azure*.

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  Adicione um método para recuperar o texto armazenado no arquivo localizado em sua *arquivos de armazenamento do Azure* e *desserializar* -lo em uma lista.

6.  Quando esse processo é concluído, o método reabilita o olhar para que o usuário pode adicionar mais formas para a cena.

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  Salve suas alterações no Visual Studio antes de retornar para o Unity.

## <a name="chapter-11---build-the-uwp-solution"></a>Capítulo 11 - criar a solução UWP

Para iniciar o processo de compilação:

1.  Vá para **arquivo > configurações de Build**.

    ![Compilar o aplicativo](images/AzureLabs-Lab5-54.png)

2.  Clique em **Compilar**. Unity iniciará uma *Explorador de arquivos* janela, em que você precisa para criar e, em seguida, selecione uma pasta para compilar o aplicativo em. Criar pasta agora e nomeie- *aplicativo*. Em seguida, com o *App* pasta selecionada, pressione **Selecionar pasta**.

3.  Unity começará a compilar seu projeto para o *aplicativo* pasta.

4.  Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um *Explorador de arquivos* janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).

## <a name="chapter-12---deploying-your-application"></a>Capítulo 12 - implantar seu aplicativo

Para implantar seu aplicativo:

1.  Navegue até a *App* pasta que foi criada na [último capítulo](#chapter-11---build-the-uwp-solution). Você verá um arquivo com seu nome de aplicativos, com a extensão '. sln', que você deve clicar duas vezes, portanto, para abri-lo dentro *Visual Studio*.

2.  No **plataforma da solução**, selecione **x86, computador Local**.

3.  No **configuração da solução** selecionar **depurar**.

    > Para o Microsoft HoloLens, talvez você ache mais fácil de definir isso como *máquina remota*, de modo que você não estiver vinculado ao seu computador. No entanto, você precisará também fazer o seguinte:
    > - Saber a **endereço IP** de seu HoloLens, que podem ser encontrado dentro a *Configurações > rede e Internet > Wi-Fi > Opções avançadas de*; o IPv4 é o endereço que você deve usar. 
    > - Certifique-se **modo de desenvolvedor** é **na**; encontrado na *Configurações > atualização e segurança > para os desenvolvedores*.

    ![Implantar solução](images/AzureLabs-Lab5-55.png)

4.  Vá para o **construir** menu e clique em **implantar solução** para carregar o aplicativo em seu computador.

5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado e testado!

## <a name="your-finished-azure-functions-and-storage-application"></a>O Azure Functions e o aplicativo de armazenamento concluído

Parabéns, você criou um aplicativo de realidade mista que aproveita os serviços do Azure Functions e o armazenamento do Azure. Seu aplicativo será capaz de desenhar em dados armazenados e fornecer uma ação com base nesses dados.

![final do produto-end](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Crie uma segunda geração ponto e do registro que gerar um objeto foi criado a partir do ponto. Quando você carrega o arquivo de dados, repetir as formas que estão sendo geradas do local em que eles foram originalmente criados.

### <a name="exercise-2"></a>Exercício 2

Crie uma forma para reiniciar o aplicativo, em vez de precisar abra novamente cada vez. **Carregar cenas** é um bom lugar para começar. Depois de fazer isso, crie uma maneira de limpar a lista armazenada no *armazenamento do Azure*, de modo que podem ser redefinida facilmente do seu aplicativo. 
