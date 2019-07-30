---
title: Sr e Azure 306-vídeo de streaming
description: Conclua este curso para aprender a implementar os serviços de mídia do Azure em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, serviços de mídia, vídeo de streaming, 360, imersão, VR
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63555570"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>Sr e Azure 306: Vídeo de streaming

![produto final –](images/AzureLabs-Lab6-00.png)
![início do produto final-início](images/AzureLabs-Lab6-01.png)

Neste curso, você aprenderá como conectar seus serviços de mídia do Azure a uma experiência do Windows Mixed Reality VR para permitir a reprodução de vídeo de streaming de 360 graus em headsets de imersão. 

Os **serviços de mídia do Azure** são uma coleção de serviços que fornece serviços de streaming de vídeo de qualidade de difusão para alcançar públicos maiores nos dispositivos móveis mais populares de hoje. Para obter mais informações, visite a [página dos serviços de mídia do Azure](https://azure.microsoft.com/services/media-services).

Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada, que poderá fazer o seguinte:

1. Recuperar um vídeo de 360 graus de um **armazenamento do Azure**por meio do **serviço de mídia do Azure**.

2. Exiba o vídeo de 360 graus recuperado em uma cena do Unity.

3. Navegue entre duas cenas, com dois vídeos diferentes.

Em seu aplicativo, cabe a você como você integrará os resultados com seu design. Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity. É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Sr e Azure 306: Vídeo de streaming</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018). Você está livre para usar o software mais recente, conforme listado no [artigo instalar as ferramentas](install-the-tools.md), embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)
- [Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md#installation-checklist)
- [O SDK do Windows 10 mais recente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md)
- Acesso à Internet para a instalação do Azure e recuperação de dados
- Vídeos de 2 360 graus no formato MP4 (você pode encontrar alguns vídeos isentos de royalties nesta [página de download](https://www.mettle.com/360vr-master-series-free-360-downloads-page))

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).
2.  Configure e teste seu headset de imersão de realidade misturada.

    > [!NOTE]
    > Você **não** precisará de controladores de animação para este curso. Se você precisar de suporte para configurar o headset de imersão, clique em [link sobre como configurar a realidade mista do Windows](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>Capítulo 1-o portal do Azure: criando a conta de armazenamento do Azure

Para usar o **serviço de armazenamento do Azure**, você precisará criar e configurar uma **conta de armazenamento** no portal do Azure.

1.  Faça logon no [portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  Depois de fazer logon, clique em **contas de armazenamento** no menu à esquerda.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-02.png)

3.  Na guia **contas de armazenamento** , clique em **Adicionar**.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-03.png)

4.  Na guia **criar conta de armazenamento** :

    1.  Insira um **nome** para sua conta, lembre-se de que esse campo aceita apenas números e letras minúsculas.

    2.  Para **modelo de implantação,** selecione **Gerenciador de recursos**.

    3.  Para **tipo de conta**, selecione **armazenamento (uso geral v1)** .

    4.  Para **desempenho**, selecione **padrão*.**

    5.  Para **replicação** , selecione **armazenamento com REDUNDÂNCIA local (LRS)** .

    6.  Deixe a **transferência segura necessária** como **desabilitada**.

    7.  Selecione uma **assinatura**.

    8.  Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.

    9.  Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.

5.  Você precisará confirmar que entendeu os termos e condições aplicados a este serviço.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-04.png)

6.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

7.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-05.png)

8.  Neste ponto, você não precisa seguir o recurso, simplesmente vá para o próximo capítulo.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Capítulo 2-o portal do Azure: criando o serviço de mídia

Para usar o serviço de mídia do Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo (onde o titular da conta precisa ser um administrador).

1.  No portal do Azure, clique em **criar um recurso** no canto superior esquerdo e procure **serviço de mídia,** pressione **Enter**. O recurso que você deseja atualmente tem um ícone rosa; Clique aqui para mostrar uma nova página.

    ![O portal do Azure](images/AzureLabs-Lab6-06.png)

2.  A nova página fornecerá uma descrição do **serviço de mídia**. Na parte inferior esquerda desse prompt, clique no botão **criar** para criar uma associação com esse serviço.

    ![O portal do Azure](images/AzureLabs-Lab6-07.png)

3.  Depois de clicar em **criar** um painel, aparecerá onde você precisa fornecer alguns detalhes sobre o novo serviço de mídia:

    1.  Insira o **nome da conta** desejada para esta instância de serviço.

    2.  Selecione uma **assinatura**.

    3. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum). 
    
    > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar grupos de recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.

    5.  Para a seção **conta de armazenamento** , clique na seção **selecionar...** e clique na conta de **armazenamento** que você criou no último capítulo.

    6.  Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.

    7.  Clique em **Criar**.

        ![O portal do Azure](images/AzureLabs-Lab6-08.png)

4.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

5.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![O portal do Azure](images/AzureLabs-Lab6-09.png)

6.  Clique na notificação para explorar sua nova instância de serviço.

    ![O portal do Azure](images/AzureLabs-Lab6-10.png)

7.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.

8.  Na página novo serviço de mídia, no painel à esquerda, clique no link **ativos** , que está sobre a metade para baixo.

9.  Na página seguinte, no canto superior esquerdo da página, clique em **carregar**.

    ![O portal do Azure](images/AzureLabs-Lab6-11.png)

10. Clique no ícone de **pasta** para procurar os arquivos e selecione o primeiro vídeo 360 que você deseja transmitir. 
    
    > Você pode seguir este [link para baixar um vídeo de exemplo](https://vimeo.com/214401712).

    ![O portal do Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> Nomes de arquivo longos podem causar um problema com o codificador: para garantir que os vídeos não tenham problemas, considere reduzir o tamanho dos nomes de arquivos de vídeo.

11. A barra de progresso ficará verde quando o vídeo terminar de ser carregado.

    ![O portal do Azure](images/AzureLabs-Lab6-13.png)

12. Clique no texto acima (**yourservicename-assets**) para retornar à página **ativos** .

13. Você observará que o vídeo foi carregado com êxito. Clique nele.

    ![O portal do Azure](images/AzureLabs-Lab6-14.png)

14. A página para a qual você será redirecionado mostrará informações detalhadas sobre o vídeo. Para poder usar seu vídeo, você precisa codificá-lo clicando no botão **codificar** na parte superior esquerda da página.

    ![O portal do Azure](images/AzureLabs-Lab6-15.png)

15. Um novo painel será exibido à direita, onde você poderá definir as opções de codificação para o arquivo. Defina as propriedades a seguir (algumas já estarão definidas por padrão):

    1.  **Nome do codificador de mídia *Media Encoder Standard***

    2.  **Codificação de *taxa de bits múltipla adaptável com conteúdo* predefinido**

    3.  **Nome *do trabalho Media Encoder Standard processamento de Video1. mp4***

    4.  **Nome do ativo *de mídia de saída Video1. mp4--Media Encoder Standard codificado***

        ![O portal do Azure](images/AzureLabs-Lab6-16.png)

16. Clique no botão **Criar**.

17. Você notará uma barra com o **trabalho de codificação adicionado**, clicará nessa barra e um painel será exibido com o andamento da codificação exibido nela.

    ![O portal do Azure](images/AzureLabs-Lab6-17.png)

    ![O portal do Azure](images/AzureLabs-Lab6-18.png)

18. Aguarde a conclusão do trabalho. Quando terminar, fique à vontade para fechar o painel com o ' X ' na parte superior direita desse painel.

    ![O portal do Azure](images/AzureLabs-Lab6-19.png)

    ![O portal do Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > O tempo que isso leva, depende do tamanho do arquivo do seu vídeo. Esse processo pode levar muito tempo.

19. Agora que a versão codificada do vídeo foi criada, você pode publicá-la para torná-la acessível. Para fazer isso, clique nos **ativos** do link azul para voltar para a página ativos.

    ![O portal do Azure](images/AzureLabs-Lab6-21.png)

20. Você verá seu vídeo, juntamente com outra, o que é do **tipo de ativo *múltiplas taxas de bits MP4***.

    ![O portal do Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > Você pode notar que o novo ativo, junto com o vídeo inicial, é *desconhecido*e tem ' 0 ' bytes para seu **tamanho**, basta atualizar sua janela para que ele seja atualizado.

21. Clique nesse novo ativo.

    ![O portal do Azure](images/AzureLabs-Lab6-23.png)

22. Você verá um painel semelhante ao que você usou antes, apenas esse é um ativo diferente. Clique no botão **publicar** localizado na parte superior central da página.

    ![O portal do Azure](images/AzureLabs-Lab6-24.png)

23. Você será solicitado a definir um localizador, que é o ponto de entrada, para arquivos/s em seus ativos. Para seu cenário, defina as seguintes propriedades:

    1.  Tipo > de localizador**progressivo**.

    2.  A **Data** e a **hora** serão definidas para você, da data atual, para uma hora no futuro (100 anos, nesse caso). Deixe como está ou altere-o para o naipe.

    > [!NOTE]
    > Para obter mais informações sobre localizadores e o que você pode escolher, visite a [documentação dos serviços de mídia do Azure](https://docs.microsoft.com/azure/media-services/media-services-concepts).

24. Na parte inferior do painel, clique no botão **Adicionar** .

    ![O portal do Azure](images/AzureLabs-Lab6-25.png)

25. Seu vídeo agora está publicado e pode ser transmitido usando seu ponto de extremidade. Além disso, a página é uma seção de **arquivos** . É aí que as diferentes versões codificadas do seu vídeo serão. Selecione a resolução mais alta possível (na imagem abaixo dele é o arquivo 1920x960) e, em seguida, um painel à direita será exibido. Lá, você encontrará uma **URL de download**. Copie esse **ponto de extremidade** , pois você o usará posteriormente em seu código.

    ![O portal do Azure](images/AzureLabs-Lab6-26.png)    

    ![O portal do Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > Você também pode pressionar o botão **reproduzir** para reproduzir seu vídeo e testá-lo.

26. Agora você precisa carregar o segundo vídeo que será usado neste laboratório. Siga as etapas acima, repetindo o mesmo processo para o segundo vídeo. Certifique-se de copiar o segundo **ponto de extremidade** também. Use o link a seguir [para baixar um segundo vídeo](https://vimeo.com/214402865).

27. Depois que os dois vídeos tiverem sido publicados, você estará pronto para ir para o próximo capítulo.

## <a name="chapter-3---setting-up-the-unity-project"></a>Capítulo 3-Configurando o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com a realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra o **Unity** e clique em **novo**. 

    ![O portal do Azure](images/AzureLabs-Lab6-28.png)

2.  Agora, você precisará fornecer um nome de projeto de Unity, inserir **\_Mr 360VideoStreaming.** . Verifique se o tipo de projeto está definido como **3D**. Defina o local como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![O portal do Azure](images/AzureLabs-Lab6-29.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio.** Vá para ***Editar* *preferências*** e, em seguida, na janela novo, navegue até **Ferramentas externas**. Altere o **Editor de script externo** para o **Visual Studio 2017**. Feche a janela **preferências** .

    ![O portal do Azure](images/AzureLabs-Lab6-30.png)

4.  Em seguida, vá para ***arquivo* *configurações de compilação*** e alterne a plataforma para **plataforma universal do Windows**, clicando no botão **alternar plataforma** .

5.  Verifique também se:

    1. O **dispositivo de destino** está definido como **qualquer dispositivo.**
    
    2.  O **tipo de compilação** está definido como **D3D.**

    3.  O **SDK** está definido para o **mais recente instalado.**

    4.  A **versão do Visual Studio** está definida como **mais recente instalada.**

    5.  **Compilar e executar** é definido como **computador local.**

    6.  Não se preocupe com a configuração de **cenas** no momento, pois você as configurará posteriormente.

    7.  As configurações restantes devem ser deixadas como padrão por enquanto.

        ![Configurando o projeto do Unity](images/AzureLabs-Lab6-31.png)

6.  Na janela **configurações de compilação** , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o **Inspetor** está localizado. 

7. Nesse painel, algumas configurações precisam ser verificadas:

    1.  Na guia **outras configurações** :

        1.  **Criando scripts** A **versão de tempo de execução** deve ser **estável** (.net 3,5 equivalente).

        2. O **back-end de script** deve ser **.net.**

        3. O **nível de compatibilidade da API** deve ser **.NET 4,6.**

            ![Configurando o projeto do Unity](images/AzureLabs-Lab6-32.png)

    2.  Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o SDK do **Windows Mixed Reality** foi adicionado.

        ![Configurando o projeto do Unity](images/AzureLabs-Lab6-33.png)

    3.  Na guia **configurações de publicação** , em **recursos**, marque:

        - **InternetClient**

            ![Configurando o projeto do Unity](images/AzureLabs-Lab6-34.png)

8.  Depois de fazer essas alterações, feche a janela **configurações de compilação** .

9.  Salve seu projeto **arquivo* *Salvar projeto**.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Capítulo 4-importando o pacote do InsideOutSphere Unity

> [!IMPORTANT]
> Se você quiser ignorar o componente *de configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para baixar esse [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), importe-o para seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue no **capítulo 5**. Você ainda precisará criar um projeto do Unity.

Para este curso, você precisará baixar um pacote de ativos de Unity chamado [**InsideOutSphere. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).

Como importar o **unitypackage**:

1.  Com o painel do Unity na frente, clique em **ativos** no menu na parte superior da tela e, em seguida, clique em **Importar pacote > pacote personalizado**.

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-35.png)

2.  Use o seletor de arquivos para selecionar o pacote **InsideOutSphere. unitypackage** e clique em **abrir**. Uma lista de componentes para este ativo será exibida para você. Confirme a importação clicando em **importar**.

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-36.png)

3.  Depois de concluir a importação, você notará três novas pastas, **materiais**, **modelos**e **pré-fabricados**, foram adicionados à sua pasta de **ativos** . Esse tipo de estrutura de pastas é típico para um projeto do Unity.

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-37.png)

    1.  Abra a pasta **modelos** e você verá que o modelo **InsideOutSphere** foi importado.

    2.  Na pasta **materiais** , você encontrará o material de **InsideOutSpheres** *LAMBERT1*, junto com um material chamado *ButtonMaterial*, que é usado pelo GazeButton, que será exibido em breve.

    3.  A pasta **pré-fabricados** contém o **InsideOutSphere** pré-fabricado que contém o modelo **InsideOutSphere** e o *GazeButton*.

    4.  **Nenhum código está incluído**, você escreverá o código seguindo este curso.


4.  Na **hierarquia**, selecione o objeto de **câmera principal** e atualize os seguintes componentes:

    1.  **Tenha**

        1.  Posição = **X**: 0, **Y**: 0, **Z**: 0.

        2. Rotation = **X**: 0, **Y**: 0, **Z**: 0.

        3. Escala **X**: 1, **Y**: 1, **Z**: 1.

    2.  **Câmera**

        1. **Limpar sinalizadores**: Cor sólida.

        2.  **Planos**de recorte: Meu 0,1, longe: 6.

            ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-38.png)

5.  Navegue até a pasta **pré-fabricado** e, em seguida, arraste o **InsideOutSphere** pré-fabricado para o painel **hierarquia** .

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-39.png)

6.  Expanda o objeto **InsideOutSphere** dentro da **hierarquia** clicando na pequena seta ao lado dele. Você verá um objeto **filho** abaixo dele chamado **GazeButton**. Isso será usado para alterar cenas e vídeos assim.

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-40.png)

7.  Na janela do Inspetor, clique no componente de transformação do **InsideOutSphere**, verifique se as seguintes propriedades estão definidas:

    |            |    TRANSFORMAÇÃO-POSIÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    TRANSFORMAÇÃO-ROTAÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     TRANSFORMAR EM ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-41.png)

8.  Clique no objeto filho **GazeButton** e defina sua **transformação** da seguinte maneira:

    |            |    TRANSFORMAÇÃO-POSIÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3,6|          **Y** 1,3        |  **Z** 0  |

    |            |    TRANSFORMAÇÃO-ROTAÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMAR EM ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importando o pacote do InsideOutSphere Unity](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>Capítulo 5 – criar a classe VideoController

A classe **VideoController** hospeda os dois pontos de extremidade de vídeo que serão usados para transmitir o conteúdo do serviço de mídia do Azure.

Para criar esta classe:

1.  Clique com o botão direito do mouse na **pasta ativo**, localizada no painel **projeto** , e clique em **criar > pasta**. Nomeie a pasta **scripts**.

    ![Criar a classe VideoController](images/AzureLabs-Lab6-43.png)

    ![Criar a classe VideoController](images/AzureLabs-Lab6-44.png)

2.  Clique duas vezes na pasta **scripts** para abri-la.

3.  Clique com o botão direito do mouse dentro da pasta e clique em **criar > script C\#** . Nomeie o script **VideoController**.

    ![Criar a classe VideoController](images/AzureLabs-Lab6-45.png)

4.  Clique duas vezes no novo script **VideoController** para abri-lo com o **Visual Studio 2017.**

    ![Criar a classe VideoController](images/AzureLabs-Lab6-46.png)

5.  Atualize os namespaces na parte superior do arquivo de código da seguinte maneira:

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  Insira as variáveis a seguir na classe **VideoController** , juntamente com o método **ativo ()** :

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  Agora é o momento de inserir os pontos de extremidade dos vídeos do serviço de mídia do Azure:

    1.  O primeiro na variável *video1endpoint* .
    
    2.  O segundo na variável *video2endpoint* .

    > [!WARNING]
    > Há um problema conhecido com o uso de *https* no Unity, com a versão 2017.4.1 F1. Se os vídeos fornecerem um erro na reprodução, tente usar "http" em seu lugar.

8.  Em seguida, o método **Start ()** precisa ser editado. Esse método será disparado sempre que o usuário alternar a cena (consequentemente, alternando o vídeo) examinando o botão olhar.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  Após o método **Start ()** , insira o método **PlayVideo ()** *IEnumerator* , que será usado para iniciar vídeos diretamente (portanto, nenhum stutter é visto).

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. O último método necessário para essa classe é o método **ChangeScene ()** , que será usado para alternar entre cenas.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > O método **ChangeScene ()** usa um recurso C\# útil chamado *operador condicional*. Isso permite que as condições sejam verificadas e, em seguida, os valores retornados com base no resultado da verificação, tudo dentro de uma única instrução. Siga este [link para saber mais sobre o operador condicional](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).

11. Salve suas alterações no Visual Studio antes de retornar ao Unity.

12. De volta ao editor do Unity, clique e arraste a classe **VideoController** [de] {. Underline} a pasta **scripts** para o objeto da **câmera principal** no painel **hierarquia** .

13. Clique na **câmera principal** e examine o **painel Inspetor**. Você observará que, dentro do componente de script recém-adicionado, há um campo com um valor vazio. Este é um campo de referência, que tem como alvo as variáveis públicas no seu código.

14. Arraste o objeto **InsideOutSphere** do **painel hierarquia** para o slot de **esfera** , conforme mostrado na imagem abaixo.

    ![Criar a classe](images/AzureLabs-Lab6-47.png)
    ![VideoController criar a classe VideoController](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Capítulo 6-criar a classe olhar

Essa classe é responsável por criar um **Raycast** que será projetado para a frente da **câmera principal**, para detectar qual objeto o usuário está olhando. Nesse caso, o **Raycast** precisará identificar se o usuário está olhando para o objeto **GazeButton** na cena e disparar um comportamento.

Para criar esta classe:

1.  Vá para a pasta **scripts** que você criou anteriormente.

2.  Clique com botão direito no **Project** painel, **crie* *C\# Script**. Nomeie o script **olhar**.

3.  Clique duas vezes no novo script ***olhar*** para abri-lo com o **Visual Studio 2017.**

4.  Verifique se o namespace a seguir está na parte superior do script e remova todos os outros:

    ```csharp
    using UnityEngine;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro da classe **olhar** :

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  Agora, o código para os métodos **ativo ()** e **Iniciar ()** precisa ser adicionado.

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  Adicione o código a seguir no método **Update ()** para projetar um Raycast e detectar o destino atingido:

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  Salve suas alterações no Visual Studio antes de retornar ao Unity.

9.  Clique e arraste a classe **olhar** da pasta scripts para o objeto de câmera principal no painel **hierarquia** .

## <a name="chapter-7---setup-the-two-unity-scenes"></a>Capítulo 7-configurar as duas cenas de Unity

A finalidade deste capítulo é configurar as duas cenas, cada uma hospedando um vídeo para transmitir. Você duplicará a cena que já criou, para que não seja necessário configurá-la novamente, embora você editará a nova cena, para que o objeto *GazeButton* esteja em um local diferente e tenha uma aparência diferente. Isso é para mostrar como alterar entre cenas.

1.  Faça isso indo para **arquivo > salvar cena como...** . Uma janela salvar será exibida. Clique no botão **nova pasta** .

    ![Capítulo 7-configurar as duas cenas de Unity](images/AzureLabs-Lab6-49.png)

2.  Nomeie a pasta como **cenas**.

3.  A janela **salvar cena** ainda estará aberta. Abra sua pasta de **cenas** recém-criada.

4.  No campo **nome do arquivo:** texto, digite **VideoScene1**e pressione **salvar**.

5.  De volta ao Unity, abra a pasta **cenas** e clique com o botão esquerdo do mouse no arquivo **VideoScene1** . Use o teclado e pressione **Ctrl + D** para duplicar essa cena

    > [!TIP]
    > O comando duplicado também pode ser executado navegando para **Editar > duplicado**.

6.  O Unity incrementará automaticamente o número de nomes de cena, mas o verificará de qualquer forma, para garantir que ele corresponda ao código inserido anteriormente.

    >  Você deve ter **VideoScene1** e **VideoScene2**.

7.  Com seus dois bastidores, vá para **arquivo > configurações de Build**. Com a janela **configurações de compilação** aberta, arraste suas cenas para a seção **cenas na compilação** .

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > Você pode selecionar os dois bastidores da sua pasta de **cenas** pressionando o botão **Ctrl** e, em seguida, clicando em cada uma das cenas e, por fim, arrastando ambos.

8.  Feche a janela **configurações de Build** e clique duas vezes em **VideoScene2**.

9.  Com a segunda cena aberta, clique no objeto filho **GazeButton** do **InsideOutSphere**e defina sua transformação da seguinte maneira:

    |            |    TRANSFORMAÇÃO-POSIÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1,3         | **Z** 3,6 |

    |            |    TRANSFORMAÇÃO-ROTAÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMAR EM ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. Com o filho **GazeButton** ainda selecionado, examine o **Inspetor** e o filtro de **malha**. Clique no pequeno destino ao lado do campo de referência de **malha** :

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-51.png)

11. Uma janela pop-up **selecionar malha** será exibida. Clique duas vezes na malha do **cubo** na lista de **ativos**.

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-52.png)

12. O **filtro de malha** será atualizado e agora será um **cubo**. Agora, clique no ícone de **engrenagem** ao lado de **Colisor de esfera** e clique em **remover componente**para excluir o colisor desse objeto.

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-53.png)

13. Com o **GazeButton** ainda selecionado, clique no botão **Adicionar componente** na parte inferior do **Inspetor**. No campo de pesquisa, digite **Box**e o **colisor do box** será uma opção – clique nele para adicionar um **Colisor de caixa** ao seu objeto **GazeButton** .

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-54.png)

14. O **GazeButton** agora é parcialmente atualizado, para parecer diferente, no entanto, agora você criará um novo **material**, para que ele pareça completamente diferente e seja mais fácil de reconhecer como um objeto diferente do objeto na primeira cena.

15. Navegue até a pasta **materiais** , no **painel Projeto**. Duplique o material **ButtonMaterial** (pressione **Ctrl** + **D** no teclado ou clique com o botão esquerdo do mouse no **material**e, em seguida, na opção de menu **Editar** arquivo, selecione **duplicar**).

    ![Capítulo 7 – configurar os dois bastidores](images/AzureLabs-Lab6-55.png)
    ![do Unity capítulo 7 – configurar as duas cenas do Unity](images/AzureLabs-Lab6-56.png)

16. Selecione o novo material de **ButtonMaterial** (aqui chamado **ButtonMaterial 1**) e, dentro do **Inspetor**, clique na janela de cores **albedo** . Um pop-up será exibido, no qual você pode selecionar outra cor (escolha o que desejar) e, em seguida, feche o pop-up. O material será sua própria instância e diferente do original.

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-57.png)

17. Arraste o novo **material** para o filho do **GazeButton** , para agora atualizar completamente sua aparência, de modo que seja facilmente distinguivel do primeiro botão de cenas.

    ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-58.png)

18. Neste ponto, você pode testar o projeto no editor antes de criar o projeto UWP.

    -  Pressione o botão **reproduzir** no **Editor** e desgaste do headset.

        ![Capítulo 7 – configurar as duas cenas de Unity](images/AzureLabs-Lab6-59.png)

19. Examine os dois objetos **GazeButton** para alternar entre o primeiro e o segundo vídeo.

## <a name="chapter-8---build-the-uwp-solution"></a>Capítulo 8-compilar a solução UWP

Depois de garantir que o editor não tem erros, você estará pronto para compilar.

Para compilar:

1.  Salve a cena atual clicando em **arquivo > salvar**.

2.  Marque a caixa chamado **projetos do\# Unity C** (isso é importante porque ele permitirá que você edite as classes após a conclusão da compilação).

3.  Vá para **arquivo > configurações de compilação**, clique em **Compilar**.

4.  Você será solicitado a selecionar a pasta onde deseja buildThe a solução.

5.  Crie uma pasta builds e dentro dessa pasta crie outra pasta com um nome apropriado de sua escolha.

6.  Clique na nova pasta e, em seguida, clique em **Selecionar pasta**, para escolher essa pasta, para iniciar a compilação nesse local.

    ![Capítulo 8--criar a solução](images/AzureLabs-Lab6-60.png)
    ![UWP capítulo 8--criar a solução UWP](images/AzureLabs-Lab6-61.png)

7.  Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação.

## <a name="chapter-9---deploy-on-local-machine"></a>Capítulo 9 – implantar no computador local

Depois que a compilação for concluída, uma janela **Explorador de arquivos** será exibida no local da sua compilação. Abra a pasta que você nomeou e criou e clique duas vezes no arquivo da solução (. sln) dentro dessa pasta para abrir sua solução com o Visual Studio 2017.

A única coisa que resta fazer é implantar seu aplicativo em seu computador (ou *computador local*).

Para implantar no computador local:

1.  No **Visual Studio 2017**, abra o arquivo de solução que acabou de ser criado.

2.  Na **plataforma da solução**, selecione **x86, computador local**.

3.  Na **configuração da solução** , selecione **depurar**.

    ![Capítulo 9 – implantar no computador local](images/AzureLabs-Lab6-62.png)

4.  Agora, você precisará restaurar todos os pacotes para sua solução. Clique com o botão direito do mouse em sua **solução**e clique em **restaurar pacotes NuGet para solução...**

    > [!NOTE] 
    > Isso é feito porque os pacotes que o Unity criou precisam ser destinados para trabalhar com suas referências de computadores locais.

5.  Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador. O Visual Studio primeiro compilará e, em seguida, implantará seu aplicativo.

6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.

    ![Capítulo 9 – implantar no computador local](images/AzureLabs-Lab6-63.png)

Ao executar o aplicativo de realidade misturada, você estará dentro do modelo de **InsideOutSphere** que você usou em seu aplicativo. Essa esfera será onde o vídeo será transmitido, fornecendo uma exibição de 360 graus do vídeo de entrada (que foi cofilme para esse tipo de perspectiva). Não se surpreenda se o vídeo levar alguns segundos para ser carregado, seu aplicativo estará sujeito à velocidade da Internet disponível, uma vez que o vídeo precisa ser buscado e então baixado, portanto, para transmitir em seu aplicativo.
Quando estiver pronto, altere as cenas e abra o segundo vídeo, por nuvens na esfera vermelha! Em seguida, fique à vontade para voltar, usando o cubo azul na segunda cena!

## <a name="your-finished-azure-media-service-application"></a>Seu aplicativo de serviço de mídia do Azure concluído
 
Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço de mídia do Azure para transmitir vídeos 360.

![resultado do laboratório](images/AzureLabs-Lab6-00.png)

![resultado do laboratório](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

**Exercício 1**

É totalmente possível usar apenas uma única cena para alterar vídeos dentro deste tutorial. Experimente seu aplicativo e torne-o em uma única cena! Talvez até mesmo Adicione outro vídeo à combinação.

**Exercício 2**

Experimente com o Azure e o Unity e tente implementar a capacidade para o aplicativo selecionar automaticamente um vídeo com um tamanho de arquivo diferente, dependendo da força de uma conexão com a Internet.


