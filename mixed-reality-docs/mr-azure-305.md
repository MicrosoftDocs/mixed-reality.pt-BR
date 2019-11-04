---
title: Sr e Azure 305 – funções e armazenamento
description: Conclua este curso para aprender a implementar o armazenamento e as funções do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, funções, armazenamento, hololens, imersão, VR
ms.openlocfilehash: 79c276d45163465c9921d02343d41d52d5f094e7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437982"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>Sr e Azure 305: funções e armazenamento

![início do produto final](images/AzureLabs-Lab5-00.png)

Neste curso, você aprenderá a criar e usar Azure Functions e armazenar dados com um recurso de armazenamento do Azure, em um aplicativo de realidade misturada.

*Azure Functions* é um serviço da Microsoft, que permite aos desenvolvedores executar pequenas partes de código, ' Functions ', no Azure. Isso fornece uma maneira de delegar trabalho para a nuvem, em vez de seu aplicativo local, que pode ter muitos benefícios. O *Azure Functions* dá suporte a várias linguagens de desenvolvimento, incluindo C\#, F\#, Node. js, Java e php. Para obter mais informações, visite o [artigo Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).

O *armazenamento do Azure* é um serviço de nuvem da Microsoft, que permite aos desenvolvedores armazenar dados, com o seguro de que ele será altamente disponível, seguro, durável, escalonável e redundante. Isso significa que a Microsoft tratará de toda a manutenção e problemas críticos para você. Para obter mais informações, visite o [artigo armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction).

Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada que poderá fazer o seguinte:

1.  Permitir que o usuário olhar em uma cena.
2.  Dispare a geração de objetos quando o usuário gazes em um "botão" 3D.
3.  Os objetos gerados serão escolhidos por uma função do Azure.
4.  À medida que cada objeto é gerado, o aplicativo armazenará o tipo de objeto em um *arquivo do Azure*, localizado no *armazenamento do Azure*.
5.  Ao carregar uma segunda vez, os dados de *arquivo do Azure* serão recuperados e usados para reproduzir as ações de geração da instância anterior do aplicativo.

Em seu aplicativo, cabe a você como você integrará os resultados com seu design. Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity. É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Sr e Azure 305: funções e armazenamento</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Embora este curso se concentre principalmente em fones de ouvido (VR) de realidade mista do Windows, você também pode aplicar o que aprende neste curso ao Microsoft HoloLens. Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte ao HoloLens.

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
- Uma assinatura para uma conta do Azure para criar recursos do Azure
- Acesso à Internet para a instalação do Azure e recuperação de dados

## <a name="before-you-start"></a>Antes de começar

Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1-o portal do Azure

Para usar o **serviço de armazenamento do Azure**, você precisará criar e configurar uma **conta de armazenamento** no portal do Azure.

1.  Faça logon no [portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure *conta de armazenamento*e clique em **Enter**.

    ![pesquisa de armazenamento do Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.

3.  A nova página fornecerá uma descrição do serviço de *conta de armazenamento do Azure* . Na parte inferior esquerda desse prompt, selecione o botão **criar** para criar uma associação com esse serviço.

    ![Criar serviço](images/AzureLabs-Lab5-02.png)

4.  Depois de clicar em **criar**:

    1.  Insira um *nome* para sua conta, lembre-se de que esse campo aceita apenas números e letras minúsculas.

    2.  Para *modelo de implantação*, selecione **Gerenciador de recursos**.

    3.  Para *tipo de conta*, selecione **armazenamento (uso geral v1)** .

    4.  Determine o *local* do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.

    5.  Para *replicação* **, selecione leitura-acesso-armazenamento com REDUNDÂNCIA geográfica (ra-grs)** .

    6.  Para *desempenho*, selecione **padrão**.

    7.  Deixe a *transferência segura necessária* como **desabilitada**.

    8.  Selecione uma *assinatura*.

    9. Escolha um *grupo de recursos* ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.

    11. Selecione **Criar**.

        ![informações do serviço de entrada](images/AzureLabs-Lab5-03.png)

5.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![Nova notificação no portal do Azure](images/AzureLabs-Lab5-04.png)

7.  Clique nas notificações para explorar sua nova instância de serviço.

    ![ir para o recurso](images/AzureLabs-Lab5-05.png)

8.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. Você será levado para sua nova instância de serviço da *conta de armazenamento* .

    ![teclas de acesso](images/AzureLabs-Lab5-06.png)

9.  Clique em *chaves de acesso*para revelar os pontos de extremidade para este serviço de nuvem. Use o *bloco de notas* ou semelhante para copiar uma de suas chaves para uso posterior. Além disso, observe o valor da *cadeia de conexão* , pois ele será usado na classe *azureservices* , que será criada mais tarde.

    ![copiar cadeia de conexão](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Capítulo 2-Configurando uma função do Azure

Agora, você escreverá uma **função** **do Azure** no serviço do Azure.

Você pode usar uma **função do Azure** para fazer praticamente tudo o que faria com uma função clássica em seu código, a diferença é que essa função pode ser acessada por qualquer aplicativo que tenha credenciais para acessar sua conta do Azure.

Para criar uma função do Azure:

1.  No *portal do Azure*, clique em **novo** no canto superior esquerdo e procure *aplicativo de funções*e clique em **Enter**.

    ![Criar aplicativo de funções](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.

2.  A nova página fornecerá uma descrição do serviço de *aplicativo de funções do Azure* . Na parte inferior esquerda desse prompt, selecione o botão **criar** para criar uma associação com esse serviço.

    ![informações do aplicativo de funções](images/AzureLabs-Lab5-09.png)

3.  Depois de clicar em **criar**:

    1.  Forneça um *nome de aplicativo*. Somente letras e números podem ser usados aqui (é permitido um caso superior ou inferior).

    2.  Selecione sua *assinatura*preferida.

    3. Escolha um *grupo de recursos* ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Para este exercício, selecione *Windows* como o **sistema operacional**escolhido.

    5.  Selecione *plano de consumo* para o **plano de hospedagem**.

    6.  Determine o *local* do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões. Para obter um desempenho ideal, selecione a mesma região que a conta de armazenamento.

    7.  Para *armazenamento*, selecione **usar existente**e, em seguida, usando o menu suspenso, localize o armazenamento criado anteriormente.

    8.  Deixe *Application insights* desativado para este exercício.

        ![detalhes do aplicativo de função de entrada](images/AzureLabs-Lab5-10.png)

4.  Clique no botão **Criar**.

5.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![Nova notificação do portal do Azure](images/AzureLabs-Lab5-11.png)

7.  Clique nas notificações para explorar sua nova instância de serviço. 

    ![ir para o aplicativo de função de recurso](images/AzureLabs-Lab5-12.png)

8.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. Você será levado para sua nova instância do serviço *aplicativo de funções* .

9.  No painel *aplicativo de funções* , passe o mouse sobre as *funções*, localizadas no painel à esquerda e clique no símbolo **+ (mais)** .

    ![criar nova função](images/AzureLabs-Lab5-13.png)

10. Na página seguinte, verifique se **webhook + API** está selecionado e, para *escolher um idioma,* selecione **Csharp**, pois esse será o idioma usado para este tutorial. Por fim, clique no botão **criar esta função** .

    ![selecionar o Web Hook Csharp](images/AzureLabs-Lab5-14.png)

11. Você deve ser levado para a página de código (Run. CSX), se não estiver, clique na função recém-criada na lista de funções no painel à esquerda.

    ![abrir nova função](images/AzureLabs-Lab5-15.png)

12. Copie o código a seguir em sua função. Essa função simplesmente retornará um inteiro aleatório entre 0 e 2, quando chamado. Não se preocupe com o código existente, fique à vontade para colar na parte superior.

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

13. Selecione **Salvar**.

14. O resultado deve ser semelhante à imagem abaixo.

15. Clique em **obter URL da função** e anote o *ponto de extremidade* exibido. Você precisará inseri-lo na classe *azureservices* que será criada posteriormente neste curso.

    ![obter ponto de extremidade de função](images/AzureLabs-Lab5-16.png)

    ![obter ponto de extremidade de função](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Capítulo 3-Configurando o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.

Configure e teste seu headset de imersão de realidade misturada.

> [!NOTE]
> Você **não** precisará de controladores de animação para este curso. Se você precisar de suporte para configurar o headset de imersão, [visite o artigo configuração de realidade misturada](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra o Unity e clique em **novo**.

    ![criar novo projeto de Unity](images/AzureLabs-Lab5-17.png)

2.  Agora, você precisará fornecer um nome de projeto de Unity. Insira **MR_Azure_Functions**. Verifique se o tipo de projeto está definido como **3D**. Defina o *local* como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Dê um nome ao novo projeto do Unity](images/AzureLabs-Lab5-18.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar** **preferências** de > e, em seguida, na nova janela, navegue até **Ferramentas externas**. Altere o **Editor de script externo** para o **Visual Studio 2017**. Feche a janela **preferências** .

    ![definir o Visual Studio como editor de script](images/AzureLabs-Lab5-19.png)

4.  Em seguida, vá para **arquivo** > **configurações de Build** e alterne a plataforma para **plataforma universal do Windows**clicando no botão **alternar plataforma** .

    ![alternar plataforma para UWP](images/AzureLabs-Lab5-20.png)

5.  Vá para **arquivo** > **configurações de compilação** e verifique se:

    1. O **dispositivo de destino** está definido como **qualquer dispositivo**.

        > Para o Microsoft HoloLens, defina o **dispositivo de destino** para o *hololens*.

    2. O **tipo de compilação** está definido como **D3D**

    3. O **SDK** está definido para o **mais recente instalado**

    4. A **versão do Visual Studio** está definida para o **mais recente instalado**

    5. **Compilar e executar** é definido como **computador local**

    6. Salve a cena e adicione-a à compilação.

        1.  Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.

            ![Adicionar cenas abertas](images/AzureLabs-Lab5-21.png)

        2.  Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![criar pasta de cenas](images/AzureLabs-Lab5-22.png)

        3.  Abra sua pasta de **cenas** recém-criada e, no campo **nome do arquivo:** , digite **FunctionsScene**e pressione **salvar**.

            ![cena de salvar funções](images/AzureLabs-Lab5-23.png)

6.  As configurações restantes, em **configurações de compilação**, devem ser deixadas como padrão por enquanto.

    ![cena de salvar funções](images/AzureLabs-Lab5-24.png)

7.  Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado.

    ![configurações do Player no Inspetor](images/AzureLabs-Lab5-25.png)

8.  Nesse painel, algumas configurações precisam ser verificadas:

    1.  Na guia **outras configurações** :

        1.  A **versão de tempo de execução de script** deve ser **Experimental** (.NET 4,6 equivalente), o que irá disparar uma necessidade de reiniciar o editor.
        2.  O **back-end de script** deve ser **.net**
        3.  O **nível de compatibilidade da API** deve ser **.NET 4,6**

    2.  Na guia **configurações de publicação** , em **recursos**, marque:
        
        -  **InternetClient**

            ![definir recursos](images/AzureLabs-Lab5-26.png)

    3.  Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o **SDK do Windows Mixed Reality** foi adicionado.

        ![definir configurações de XR](images/AzureLabs-Lab5-27.png)

9.  De volta *às configurações de Build* , os *projetos do C# Unity* não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste.

    ![projetos em escala em c#](images/AzureLabs-Lab5-28.png)

10.  Feche a janela configurações de compilação.

11. Salve sua cena e projeto (**arquivo** > **salvar cena/arquivo** > **salvar projeto**).

## <a name="chapter-4---setup-main-camera"></a>Capítulo 4-configurar a câmera principal

> [!IMPORTANT]
> Se você quiser ignorar os componentes de *configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para [baixar esse. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importe-o para seu projeto como um [pacote personalizado](https://docs.unity3d.com/Manual/AssetPackages.html). Isso também conterá as DLLs do próximo capítulo. Após a importação, continue no [capítulo 7](#chapter-7---create-the-azureservices-class). 

1.  No *painel hierarquia*, você encontrará um objeto chamado **câmera principal**, esse objeto representa o ponto de vista de "cabeçalho" quando você estiver "dentro" de seu aplicativo.

2.  Com o painel do Unity na frente de você, selecione a **câmera principal gameobject**. Você observará que o *painel Inspetor* (geralmente localizado à direita, dentro do painel) mostrará os vários componentes desse *gameobject*, com a *transformação* na parte superior, seguida pela *câmera*e alguns outros componentes. Você precisará redefinir a transformação da câmera principal, para que ela seja posicionada corretamente.

3.  Para fazer isso, selecione o ícone de **engrenagem** ao lado do componente *transformação* da câmera e selecione **Redefinir**.

    ![redefinir transformação](images/AzureLabs-Lab5-29.png)

4.  Em seguida, atualize o componente **transformar** para se parecer com o seguinte:

    |         |    TRANSFORMAÇÃO-POSIÇÃO   |       |
    | :-----: | :-----------------------: | :----:|
    | **W.x.y.**   | **Iar**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | TRANSFORMAÇÃO-ROTAÇÃO |       |
    | :---: | :------------------: | :----:|
    | **W.x.y.** | **Iar**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRANSFORMAR EM ESCALA |       |
    | :---: | :---------------: | :---: |
    | **W.x.y.** | **Iar**             | **Z** |
    | 1     | 1                 | 1     |

    ![definir transformação de câmera](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Capítulo 5-Configurando a cena do Unity

1.  Clique com o botão direito do mouse em uma área vazia do *painel hierarquia*, em **objeto 3D**, adicione um **plano**.

    ![criar novo plano](images/AzureLabs-Lab5-31.png)

2.  Com o objeto **plano** selecionado, altere os seguintes parâmetros no *painel Inspetor*:

    |       | TRANSFORMAÇÃO-POSIÇÃO |       |
    | :---: | :------------------: | :---: |
    | **W.x.y.** | **Iar**                | **Z** |
    | 0     | 0                    | 추가를 클릭합니다.     |

    |       | TRANSFORMAR EM ESCALA |       |
    | :---: | :---------------: | :---: |
    | **W.x.y.** | **Iar**             | **Z** |
    | 10    | 1                 | 10    |

    ![definir posição e escala do plano](images/AzureLabs-Lab5-32.png)

    ![exibição da cena do plano](images/AzureLabs-Lab5-33.png)

3.  Clique com o botão direito do mouse em uma área vazia do *painel hierarquia*, em **objeto 3D**, adicione um **cubo**.

    1.  Renomeie o cubo para **GazeButton** (com o cubo selecionado, pressione ' F2 ').

    2.  Altere os seguintes parâmetros no *painel de Inspetor*:

        |       | TRANSFORMAÇÃO-POSIÇÃO |       |
        | :---: | :------------------: |:-----:|
        | **W.x.y.** | **Iar**                | **Z** |
        | 0     | 3                    | 5     |


        ![definir transformação do botão olhar](images/AzureLabs-Lab5-34.png)

        ![exibição de cena do botão olhar](images/AzureLabs-Lab5-35.png)

    3.  Clique no botão suspenso **marca** e clique em **adicionar marca** para abrir o *painel marcas & camadas*.

        ![Adicionar nova marca](images/AzureLabs-Lab5-36.png)

        ![selecionar mais](images/AzureLabs-Lab5-37.png)

    4.  Selecione o botão **+ (mais)** e, no campo *nome da nova marca* , digite **GazeButton**e pressione **salvar**.

        ![nomear nova marca](images/AzureLabs-Lab5-38.png)

    5.  Clique no objeto **GazeButton** no *painel hierarquia*e, no *painel Inspetor*, atribua a marca **GazeButton** recém-criada.

        ![atribuir botão olhar à nova marca](images/AzureLabs-Lab5-39.png)

4.  Clique com o botão direito do mouse no objeto **GazeButton** , no *painel hierarquia*e adicione um **gameobject vazio** (que será adicionado como um objeto *filho* ).

5.  Selecione o novo objeto e renomeie-o **ShapeSpawnPoint**.

    1.  Altere os seguintes parâmetros no *painel de Inspetor*:

        |       | TRANSFORMAÇÃO-POSIÇÃO |       |
        | :---: | :------------------: |:----: |
        | **W.x.y.** |**Iar**                 | **Z** |
        | 0     | -1                   | 0     |

        ![atualizar transformação de ponto de geração de forma](images/AzureLabs-Lab5-40.png)

        ![exibição de cena de ponto de geração de forma](images/AzureLabs-Lab5-41.png)

6.  Em seguida, você criará um objeto de **texto 3D** para fornecer comentários sobre o status do serviço do Azure.

    Clique com o botão direito do mouse em **GazeButton** no painel hierarquia novamente e adicione um **objeto 3D** > objeto de **texto 3D** como um *filho*.

    ![criar novo objeto de texto 3D](images/AzureLabs-Lab5-42.png)

7.  Renomeie o objeto de **texto 3D** para **AzureStatusText**.

8.  Altere a transformação do objeto **AzureStatusText** da seguinte maneira:

    |       | TRANSFORMAÇÃO-POSIÇÃO |       |
    | :---: | :------------------: | :---: |
    | **W.x.y.** | **Iar**                | **Z** |
    | 0     | 0                    | -0,6  |

    |       | TRANSFORMAR EM ESCALA |       |
    | :---: | :---------------: | :---: |
    | **W.x.y.** | **Iar**             | **Z** |
    | 0,1   | 0,1               | 0,1   |


    > [!NOTE]
    > Não se preocupe se parece estar fora do centro, pois isso será corrigido quando o componente de malha de texto abaixo for atualizado.

9.  Altere o componente de **malha de texto** para corresponder ao seguinte:

    ![definir componente de malha de texto](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > A cor selecionada aqui é a cor hexadecimal: **000000FF**, embora sinta-se à vontade para escolher sua própria, apenas verifique se ela é legível.

10. A estrutura do painel de hierarquia agora deve ser assim:

    ![malha de texto na exibição de cena](images/AzureLabs-Lab5-43b.png)

10. Sua cena agora deve se parecer com esta:

    ![malha de texto na exibição de cena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Capítulo 6 – importar o armazenamento do Azure para o Unity

Você usará o armazenamento do Azure para Unity (que, por sua vez, utiliza o SDK do .net para o Azure). Você pode ler mais sobre isso no [artigo armazenamento do Azure para Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Atualmente, há um problema conhecido no Unity que exige que os plugins sejam reconfigurados após a importação. Essas etapas (4-7 nesta seção) não serão mais necessárias depois que o bug for resolvido.

Para importar o SDK para seu próprio projeto, verifique se você baixou o ['. unitypackage ' mais recente do GitHub](https://aka.ms/azstorage-unitysdk). Em seguida, faça o seguinte:

1.  Adicione o arquivo **. unitypackage** ao Unity usando a opção de menu **ativos** > **Importar pacote** > **pacote personalizado** .

2.  Na caixa **Importar pacote do Unity** que é exibida, você pode selecionar tudo em **armazenamento** > do **plug-in** . Desmarque todas as outras opções, pois elas não são necessárias para este curso.

    ![importar para pacote](images/AzureLabs-Lab5-45.png)

3.  Clique no botão **importar** para adicionar os itens ao seu projeto.

4.  Vá para a pasta de *armazenamento* em *plug-ins*, na exibição do projeto e selecione *apenas*os seguintes plugins:

    -   Microsoft. Data. Edm
    -   Microsoft. Data. OData
    -   Microsoft. WindowsAzure. Storage
    -   Newtonsoft. JSON
    -   System. espacial

        ![desmarcar qualquer plataforma](images/AzureLabs-Lab5-46.png)

5.  Com *esses plugins específicos* selecionados, **desmarque** *qualquer plataforma* e **desmarque** *WSAPlayer* e clique em **aplicar**.

    ![aplicar DLLs de plataforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Estamos marcando esses plugins específicos para serem usados apenas no editor do Unity. Isso ocorre porque há diferentes versões dos mesmos plug-ins na pasta WSA que serão usados depois que o projeto for exportado do Unity.

6.  Na pasta plug-in de *armazenamento* , selecione somente:

    -   Microsoft. Data. Services. Client

        ![definir não processar para DLLs](images/AzureLabs-Lab5-48.png)

7.  Marque a caixa **não processar** em *configurações da plataforma* e clique em **aplicar**.

    ![aplicar nenhum processamento](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Estamos marcando este plug-in "não processar" porque o assembly do Unity Patcher tem dificuldade para processar esse plug-in. O plug-in ainda funcionará, embora não seja processado.

## <a name="chapter-7---create-the-azureservices-class"></a>Capítulo 7-criar a classe Azureservices

A primeira classe que você pretende criar é a classe *azureservices* .

A classe *azureservices* será responsável por:

-   Armazenando as credenciais da conta do Azure.

-   Chamando sua função Azure App.

-   O upload e o download do arquivo de dados no armazenamento em nuvem do Azure.

Para criar esta classe:

1.  Clique com o botão direito do mouse na pasta *ativo* , localizada no painel projeto, **crie** > **pasta**. Nomeie a pasta **scripts**.

    ![criar nova pasta](images/AzureLabs-Lab5-50.png)

    ![pasta de chamadas-scripts](images/AzureLabs-Lab5-51.png)

2.  Clique duas vezes na pasta recém-criada para abri-la.

3.  Clique com o botão direito do mouse dentro da pasta, **crie** >  **C# script**. Chame o script *azureservices*.

4.  Clique duas vezes na nova classe *azureservices* para abri-la com o *Visual Studio*.

5.  Adicione os seguintes namespaces à parte superior do *azureservices*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Adicione os seguintes campos de Inspetor dentro da classe *azureservices* :

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

7.  Em seguida, adicione as seguintes variáveis de membro dentro da classe *azureservices* :

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
    > Substitua os valores do *ponto de extremidade* e da *cadeia de conexão* pelos valores do seu armazenamento do Azure, encontrado no portal do Azure

8.  O código para os métodos *ativo ()* e *Iniciar ()* agora precisa ser adicionado. Esses métodos serão chamados quando a classe inicializar:

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
    > Iremos preencher o código para *CallAzureFunctionForNextShape ()* em um [capítulo futuro](#chapter-10---completing-the-azureservices-class).

9.  Exclua o método *Update ()* , pois essa classe não o usará.

10. Salve suas alterações no Visual Studio e, em seguida, retorne ao Unity.

11. Clique e arraste a classe *azureservices* da pasta scripts para o objeto de câmera principal no *painel hierarquia*.

12. Selecione a câmera principal e, em seguida, pegue o objeto filho **AzureStatusText** sob o objeto **GazeButton** e coloque-o dentro do campo destino de referência do **AzureStatusText** , no *Inspetor*, para fornecer a referência ao  *Script do azureservices* .

    ![atribuir destino de referência de texto de status do Azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Capítulo 8-criar a classe ShapeFactory

O próximo script a ser criado é a classe *ShapeFactory* . A função dessa classe é criar uma nova forma, quando solicitado, e manter um histórico das formas criadas em uma *lista de histórico de formas*. Sempre que uma forma é criada, a *lista de histórico de formas* é atualizada na classe *AzureService* e, em seguida, armazenada no *armazenamento do Azure*. Quando o aplicativo for iniciado, se um arquivo armazenado for encontrado no *armazenamento do Azure*, a *lista do histórico de formas* será recuperada e reproduzida, com o objeto de **texto 3D** que fornecerá se a forma gerada é do armazenamento ou de nova.

Para criar esta classe:

1.  Vá para a pasta **scripts** que você criou anteriormente.

2.  Clique com o botão direito do mouse dentro da pasta, **crie** >  **C# script**. Chame o script *ShapeFactory*.

3.  Clique duas vezes no novo script *ShapeFactory* para abri-lo com o *Visual Studio*.

4.  Verifique se a classe *ShapeFactory* inclui os seguintes namespaces:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Adicione as variáveis mostradas abaixo à classe *ShapeFactory* e substitua as funções *Start ()* e *ativo ()* pelas seguintes:

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

6.  O método *createShape ()* gera as formas primitivas, com base no parâmetro *inteiro* fornecido. O parâmetro booliano é usado para especificar se a forma criada no momento é do armazenamento ou de nova. Coloque o seguinte código em sua classe *ShapeFactory* , abaixo dos métodos anteriores:

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

7.  Certifique-se de salvar suas alterações no Visual Studio antes de retornar ao Unity.

8.  De volta ao editor do Unity, clique e arraste a classe *ShapeFactory* da pasta **scripts** para o objeto da **câmera principal** no *painel hierarquia*.

9. Com a câmera principal selecionada, você observará que o componente de script *ShapeFactory* não tem a referência de *ponto de geração* . Para corrigi-lo, arraste o objeto **ShapeSpawnPoint** do *painel hierarquia* para o destino de referência do **ponto de geração** .

    ![definir destino de referência de fábrica de forma](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Capítulo 9-criar a classe olhar

O último script que você precisa criar é a classe *olhar* .

Essa classe é responsável por criar um **Raycast** que será projetado para a frente da câmera principal, para detectar qual objeto o usuário está olhando. Nesse caso, o Raycast precisará identificar se o usuário está olhando para o objeto **GazeButton** na cena e disparar um comportamento.

Para criar esta classe:

1.  Vá para a pasta **scripts** que você criou anteriormente.

2.  Clique com o botão direito do mouse no painel projeto, **crie** >  **C# script**. Chame o script *olhar*.

3.  Clique duas vezes no novo script *olhar* para abri-lo com o *Visual Studio.*

4.  Verifique se o namespace a seguir está incluído na parte superior do script:

    ```csharp
        using UnityEngine;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro da classe *olhar* :

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
> Algumas dessas variáveis poderão ser editadas no *Editor*.

6.  Agora, o código para os métodos *ativo ()* e *Iniciar ()* precisa ser adicionado.

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

7.  Adicione o código a seguir, que criará um objeto cursor no início, juntamente com o método *Update ()* , que executará o método Raycast, juntamente com o local em que o booliano GazeEnabled é alternado:

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

8. Em seguida, adicione o método *UpdateRaycast ()* , que projetará um Raycast e detectará o destino de acesso.

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

9. Por fim, adicione o método *ResetFocusedObject ()* , que irá alternar a cor atual dos objetos GazeButton, indicando se ele está criando uma nova forma ou não.

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

10.  Salve suas alterações no Visual Studio antes de retornar ao Unity.

11.  Clique e arraste a classe *olhar* da pasta scripts para o objeto de **câmera principal** no *painel hierarquia*.

## <a name="chapter-10---completing-the-azureservices-class"></a>Capítulo 10 – concluindo a classe Azureservices

Com os outros scripts em vigor, agora é possível *concluir* a classe *azureservices* . Isso será obtido por meio de:

1.  Adicionar um novo método chamado *CreateCloudIdentityAsync ()* para configurar as variáveis de autenticação necessárias para se comunicar com o Azure.

    > Esse método também verificará a existência de um arquivo armazenado anteriormente que contém a lista de formas.
    >
    > **Se o arquivo for encontrado**, ele desabilitará o usuário *olhar*e disparará a criação de forma, de acordo com o padrão de formas, conforme armazenado no **arquivo de armazenamento do Azure**. O usuário pode ver isso, pois a **malha de texto** fornecerá exibir ' armazenamento ' ou ' novo ', dependendo da origem das formas.
    >
    > **Se nenhum arquivo for encontrado**, ele permitirá o *olhar*, permitindo que o usuário crie formas ao examinar o objeto **GazeButton** na cena.

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

2.  O próximo trecho de código é de dentro do método *Start ()* ; Onde será feita uma chamada para o método *CreateCloudIdentityAsync ()* . Fique à vontade para copiar sobre o método *Start ()* atual, com o seguinte:

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

3.  Preencha o código para o método *CallAzureFunctionForNextShape ()* . Você usará o *Azure aplicativo de funções* criado anteriormente para solicitar um índice de forma. Depois que a nova forma for recebida, esse método enviará a forma para a classe *ShapeFactory* para criar a nova forma na cena. Use o código abaixo para concluir o corpo de *CallAzureFunctionForNextShape ()* .

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

4.  Adicione um método para criar uma cadeia de caracteres, concatenando os inteiros armazenados na lista de histórico de formas e salvando-os em seu *arquivo de armazenamento do Azure*.

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

5.  Adicione um método para recuperar o texto armazenado no arquivo localizado no arquivo de *armazenamento do Azure* e *desserializá* -lo em uma lista.

6.  Quando esse processo for concluído, o método reabilitará o olhar para que o usuário possa adicionar mais formas à cena.

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

7.  Salve suas alterações no Visual Studio antes de retornar ao Unity.

## <a name="chapter-11---build-the-uwp-solution"></a>Capítulo 11-criar a solução UWP

Para iniciar o processo de compilação:

1.  Vá para **arquivo** > **configurações de Build**.

    ![compilar o aplicativo](images/AzureLabs-Lab5-54.png)

2.  Clique em **Compilar**. O Unity iniciará uma janela *Explorador de arquivos* , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado. Crie essa pasta agora e nomeie-a como *aplicativo*. Em seguida, com a pasta de *aplicativo* selecionada, pressione **Selecionar pasta**.

3.  O Unity começará a criar seu projeto na pasta do *aplicativo* .

4.  Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do *Explorador de arquivos* no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).

## <a name="chapter-12---deploying-your-application"></a>Capítulo 12-implantando seu aplicativo

Para implantar seu aplicativo:

1.  Navegue até a pasta do *aplicativo* que foi criada no [último capítulo](#chapter-11---build-the-uwp-solution). Você verá um arquivo com o nome de seus aplicativos, com a extensão '. sln ', que você deve clicar duas vezes para abri-lo no *Visual Studio*.

2.  Na **plataforma da solução**, selecione **x86, computador local**.

3.  Na **configuração da solução** , selecione **depurar**.

    > Para o Microsoft HoloLens, você pode achar mais fácil definir isso como *computador remoto*, para que você não esteja vinculado ao seu computador. No entanto, também será necessário fazer o seguinte:
    > - Conheça o **endereço IP** do seu HoloLens, que pode ser encontrado dentro das **configurações** > **rede & Internet** > **Wi-Fi** > **Opções avançadas**; o IPv4 é o endereço que você deve usar. 
    > - Verificar se o modo **de** **desenvolvedor** está ativado; encontrado em **configurações** > **atualização &**  > **de segurança para desenvolvedores**.

    ![implantar solução](images/AzureLabs-Lab5-55.png)

4.  Vá para o menu **Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.

5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado e testado!

## <a name="your-finished-azure-functions-and-storage-application"></a>O Azure Functions e o aplicativo de armazenamento concluídos

Parabéns, você criou um aplicativo de realidade misturada que aproveita tanto o Azure Functions quanto os serviços de armazenamento do Azure. Seu aplicativo poderá desenhar dados armazenados e fornecer uma ação com base nesses dados.

![final do produto final](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Crie um segundo ponto de geração e registro do qual ponto de geração um objeto foi criado. Ao carregar o arquivo de dados, reproduza as formas que estão sendo geradas do local em que foram criadas originalmente.

### <a name="exercise-2"></a>Exercício 2

Crie uma maneira de reiniciar o aplicativo, em vez de ter que reabri-lo a cada vez. O **carregamento de cenas** é um bom ponto de partida. Depois de fazer isso, crie uma maneira de limpar a lista armazenada no *armazenamento do Azure*, para que ela possa ser redefinida facilmente do seu aplicativo. 
