---
title: MR e Azure 306 - Streaming de vídeo
description: Conclua este curso para aprender a implementar os serviços de mídia do Azure dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, serviços de mídia, streaming de vídeo, 360, imersivo, vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589469"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>MR e o Azure 306: Streaming de vídeo

![final do produto-inicie](images/AzureLabs-Lab6-00.png)
![final do produto-iniciar](images/AzureLabs-Lab6-01.png)

Este curso, você aprenderá como conectar os serviços de mídia do Azure para uma experiência VR de realidade mista do Windows para permitir a reprodução de vídeo de 360 graus em fones imersivos em exposição de streaming. 

**Os serviços de mídia do Azure** são uma coleção de serviços que fornece serviços de streaming vídeo com qualidade de difusão para alcançar públicos maiores nos dispositivos móveis mais populares de hoje. Para obter mais informações, visite o [página de serviços de mídia do Azure](https://azure.microsoft.com/services/media-services).

Com a conclusão deste curso, terá um aplicativo de imersão headset de realidade misturada, que será capaz de fazer o seguinte:

1. Recuperar um vídeo de 360 graus de um **armazenamento do Azure**, por meio de **serviço de mídia do Azure**.

2. Exiba o vídeo de 360 graus recuperada dentro de uma cena do Unity.

3. Navega entre duas cenas, com dois vídeos diferentes.

Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design. Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity. Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> MR e o Azure 306: Streaming de vídeo</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#. Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018). Você é livre para usar o software mais recente, conforme listado dentro de [instalar o artigo de ferramentas](install-the-tools.md), embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .

Recomendamos que o hardware e software para este curso a seguir:

- Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md#installation-checklist)
- [O SDK mais recente do Windows 10](install-the-tools.md#installation-checklist)
- [2017.4 do Unity](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md)
- Acesso à Internet para recuperação de dados e de instalação do Azure
- Dois vídeos de 360 graus em formato mp4 (você pode encontrar alguns vídeos livre de royalties [a esta página de download](https://www.mettle.com/360vr-master-series-free-360-downloads-page))

## <a name="before-you-start"></a>Antes de começar

1.  Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).
2.  Configurar e testar o fone imersivo realidade mista.

    > [!NOTE]
    > Você irá **não** exigem controladores de movimento para este curso. Se você precisar dar suporte a configurar o fone de ouvido imersivo, clique em [link sobre como configurar o Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>Capítulo 1 - Portal do Azure: criar a conta de armazenamento do Azure

Para usar o **serviço de armazenamento do Azure**, você precisará criar e configurar um **conta de armazenamento** no portal do Azure.

1.  Faça logon na [Portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, você precisará criá-lo. Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.

2.  Quando você estiver conectado, clique em **contas de armazenamento** no menu à esquerda.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-02.png)

3.  Sobre o **contas de armazenamento** guia, clique em **Add**.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-03.png)

4.  No **criar conta de armazenamento** guia:

    1.  Inserir uma **nome** para sua conta, lembre-se que este campo aceita apenas números e letras minúsculas.

    2.  Para **modelo de implantação** selecionar **Gerenciador de recursos**.

    3.  Para **tipo de conta**, selecione **(uso geral v1) de armazenamento**.

    4.  Para **desempenho**, selecione **padrão*.**

    5.  Para **replicação** selecionar **armazenamento localmente redundante (LRS)**.

    6.  Deixe **transferência segura obrigatória** como **desabilitado**.

    7.  Selecione uma **assinatura**.

    8.  Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure.

    9.  Determinar a **local** para seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local seria o ideal é que na região em que o aplicativo é executado. Alguns ativos do Azure estão disponíveis somente em determinadas regiões.

5.  Você precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-04.png)

6.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

7.  Uma notificação será exibida no portal depois que a instância do serviço é criada.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab6-05.png)

8.  Neste momento você não precisa seguir o recurso, basta mover para o próximo capítulo.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Capítulo 2 - Portal do Azure: criar o serviço de mídia

Para usar o serviço de mídia do Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo (no qual o titular da conta precisa ser um administrador).

1.  No Portal do Azure, clique em **criar um recurso** no canto superior esquerdo de canto e procure **serviço de mídia** pressione **Enter**. O recurso desejado no momento, tem um ícone rosa; Clique aqui para mostrar uma nova página.

    ![O Portal do Azure](images/AzureLabs-Lab6-06.png)

2.  A nova página fornecerá uma descrição do **serviço de mídia**. Na parte inferior esquerda desse prompt, clique no **criar** botão para criar uma associação com este serviço.

    ![O Portal do Azure](images/AzureLabs-Lab6-07.png)

3.  Depois de clicar em **criar** um painel será exibido em que você precisa fornecer alguns detalhes sobre seu novo serviço de mídia:

    1.  Inserir sua desejada **nome da conta** para esta instância de serviço.

    2.  Selecione uma **assinatura**.

    3. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns). 
    
    > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar grupos de recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Determinar a **local** para seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local seria o ideal é que na região em que o aplicativo é executado. Alguns ativos do Azure estão disponíveis somente em determinadas regiões.

    5.  Para o **conta de armazenamento** seção, clique no **selecione...**  seção e, em seguida, clique em de **conta de armazenamento** você criou no último capítulo.

    6.  Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.

    7.  Clique em **Criar**.

        ![O Portal do Azure](images/AzureLabs-Lab6-08.png)

4.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

5.  Uma notificação será exibida no portal depois que a instância do serviço é criada.

    ![O Portal do Azure](images/AzureLabs-Lab6-09.png)

6.  Clique na notificação para explorar a nova instância do serviço.

    ![O Portal do Azure](images/AzureLabs-Lab6-10.png)

7.  Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.

8.  Dentro da página de serviço de mídia novo, no painel à esquerda, clique no **ativos** link, que é sobre na metade inferior.

9.  Na próxima página, no canto superior esquerdo da página, clique em **carregar**.

    ![O Portal do Azure](images/AzureLabs-Lab6-11.png)

10. Clique no **pasta** ícone Procurar seus arquivos e selecione o vídeo de 360 pela primeira vez que você deseja transmitir. 
    
    > Você pode seguir este [link para baixar um vídeo de exemplo](https://vimeo.com/214401712).

    ![O Portal do Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> Nomes de arquivo longos podem causar um problema com o codificador: por isso, para garantir que os vídeos não terá problemas, considere encurtar o comprimento de seus nomes de arquivo de vídeo.

11. A barra de progresso ficará verde quando o vídeo a conclusão do carregamento.

    ![O Portal do Azure](images/AzureLabs-Lab6-13.png)

12. Clique no texto acima (**yourservicename - ativos**) para retornar para o **ativos** página.

13. Você observará que o vídeo foi carregado com êxito. Clique nele.

    ![O Portal do Azure](images/AzureLabs-Lab6-14.png)

14. Você será redirecionado à página mostrará a que você informações detalhadas sobre seu vídeo. Para poder usar o vídeo que você precisa codificar, clicando o **Encode** botão no canto superior esquerdo da página.

    ![O Portal do Azure](images/AzureLabs-Lab6-15.png)

15. Um novo painel será exibido à direita, onde você poderá definir opções para o arquivo de codificação. Defina as propriedades a seguir (alguns serão já definido por padrão):

    1.  **Nome do codificador de mídia *Media Encoder Standard***

    2.  **Predefinição de codificação *conteúdo adaptável várias taxas de bits MP4***

    3.  **Nome do trabalho *Media Encoder Standard processamento do Video1.mp4***

    4.  **Nome do ativo de mídia de saída *Video1.mp4 – Media Encoder Standard codificado***

        ![O Portal do Azure](images/AzureLabs-Lab6-16.png)

16. Clique no botão **Criar**.

17. Você observará uma barra com **trabalho de codificação adicionada**, clique na barra e um painel será exibido com o andamento da codificação exibido nela.

    ![O Portal do Azure](images/AzureLabs-Lab6-17.png)

    ![O Portal do Azure](images/AzureLabs-Lab6-18.png)

18. Aguarde o conclusão do trabalho. Quando terminar, fique à vontade fechar o painel com o 'X' no canto superior direito desse painel.

    ![O Portal do Azure](images/AzureLabs-Lab6-19.png)

    ![O Portal do Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > O tempo que necessário para isso, depende do tamanho do arquivo de vídeo. Esse processo pode levar algum tempo.

19. Agora que a versão codificada do vídeo tiver sido criada, você pode publicá-lo para torná-lo acessível. Para fazer isso, clique no link azul **ativos** para voltar para a página de ativos.

    ![O Portal do Azure](images/AzureLabs-Lab6-21.png)

20. Você verá seu vídeo, juntamente com outra, o que é do **tipo de ativo *múltiplas taxas de bits MP4***.

    ![O Portal do Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > Você pode perceber que o novo ativo, juntamente com seu vídeo inicial, é *desconhecido*, e tem o '0' bytes para ele é **tamanho**, apenas atualize a janela para atualizá-la.

21. Clique nesse novo ativo.

    ![O Portal do Azure](images/AzureLabs-Lab6-23.png)

22. Você verá um painel semelhante àquele usado antes, apenas esse é um ativo diferente. Clique o **publicar** botão localizado na parte superior central da página.

    ![O Portal do Azure](images/AzureLabs-Lab6-24.png)

23. Você será solicitado a definir um **localizador**, que é o ponto de entrada para o arquivo/s em seus ativos. Para o seu cenário, defina as seguintes propriedades:

    1.  **Tipo de localizador** > **progressivo**.

    2.  O **data** e **tempo** será definido para você, a data atual, como uma hora no futuro (Cem anos neste caso). Deixe como está ou alterá-la de acordo com.

    > [!NOTE]
    > Para obter mais informações sobre localizadores e você pode escolher, visite o [documentação de serviços de mídia do Azure](https://docs.microsoft.com/azure/media-services/media-services-concepts).

24. Na parte inferior desse painel, clique no **adicionar** botão.

    ![O Portal do Azure](images/AzureLabs-Lab6-25.png)

25. Seu vídeo agora é publicado e pode ser transmitido por meio de seu ponto de extremidade. Ainda mais para baixo a página é uma **arquivos** seção. Isso é onde será codificado em versões diferentes do seu vídeo. Selecione a resolução mais alta possível um (na imagem abaixo é o arquivo de 1920 x 960), e um painel à direita será exibida. Lá você encontrará uma **URL de Download**. Copie essa **ponto de extremidade** conforme você o usará posteriormente em seu código.

    ![O Portal do Azure](images/AzureLabs-Lab6-26.png)    

    ![O Portal do Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > Você também pode pressionar o **reproduzir** botão para reproduzir o vídeo e testá-lo.

26. Agora, você precisará carregar o segundo vídeo que você usará neste laboratório. Siga as etapas acima, repetindo o mesmo processo para o segundo vídeo. Verifique se você copiar o segundo **ponto de extremidade** também. Use o seguinte [link para baixar um segundo vídeo](https://vimeo.com/214402865).

27. Depois que ambos os vídeos tiverem sido publicados, você está pronto para passar para o próximo capítulo.

## <a name="chapter-3---setting-up-the-unity-project"></a>Capítulo 3 - configurar o projeto do Unity

A seguir é um conjunto típico backup para o desenvolvimento com a realidade misturada e como tal, é um bom modelo para outros projetos.

1.  Abra **Unity** e clique em **New**. 

    ![O Portal do Azure](images/AzureLabs-Lab6-28.png)

2.  Agora você precisará fornecer um nome de projeto do Unity, insira **MR\_360VideoStreaming.**. Verifique se o tipo de projeto é definido como **3D**. Defina o local para um local apropriado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![O Portal do Azure](images/AzureLabs-Lab6-29.png)

3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio.** Vá para ***edite* *preferências*** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

    ![O Portal do Azure](images/AzureLabs-Lab6-30.png)

4.  Em seguida, vá para ***arquivo* *configurações de Build*** e alternar a plataforma **plataforma Universal do Windows**, clicando no **Alternar plataforma** botão.

5.  Também verifique se:

    1. **Dispositivo de destino** é definido como **qualquer dispositivo.**
    
    2.  **Tipo de compilação** é definido como **D3D.**

    3.  **SDK** é definido como **mais recente instalada.**

    4.  **Versão do Visual Studio** é definido como **mais recente instalada.**

    5.  **Compilar e executar** é definido como **Máquina Local.**

    6.  Não se preocupe sobre como configurar o **cenas** no momento, pois você irá configurar esses mais tarde.

    7.  As configurações restantes devem ser deixadas como padrão por enquanto.

        ![Configurar o projeto do Unity](images/AzureLabs-Lab6-31.png)

6.  No **configurações de Build** janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o **Inspetor** está localizado. 

7. Neste painel, algumas configurações precisam ser verificados:

    1.  No **outras configurações** guia:

        1.  **Criação de scripts** **versão de tempo de execução** deve ser **estável** (.NET 3.5 equivalente).

        2. **Script de back-end** deve ser **.NET.**

        3. **Nível de compatibilidade de API** deve ser **.NET 4.6.**

            ![Configurar o projeto do Unity](images/AzureLabs-Lab6-32.png)

    2.  Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado.

        ![Configurar o projeto do Unity](images/AzureLabs-Lab6-33.png)

    3.  Dentro de **configurações de publicação** guia, em **recursos**, verifique:

        - **InternetClient**

            ![Configurar o projeto do Unity](images/AzureLabs-Lab6-34.png)

8.  Depois de fazer essas alterações, fechar o **configurações de Build** janela.

9.  Salve seu projeto **arquivo* *Salvar projeto**.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Capítulo 4 - importar o pacote do InsideOutSphere Unity

> [!IMPORTANT]
> Se você quiser ignorar a *configurar o Unity* componente deste curso e continuar diretamente no código, fique à vontade para baixá-lo [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continuar a partir **capítulo 5**. Você ainda precisará criar um projeto do Unity.

Para este curso, você precisará baixar o pacote Unity Asset denominada [ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).

Importar instruções sobre o **unitypackage**:

1.  Com o painel do Unity na sua frente, clique em **ativos** no menu na parte superior da tela, em seguida, clique em **Importar pacote > pacote personalizado**.

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-35.png)

2.  Use o seletor de arquivos para selecionar o **InsideOutSphere.unitypackage** de pacote e clique em **abrir**. Uma lista de componentes para esse ativo será exibida para você. Confirme a importação clicando **importação**.

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-36.png)

3.  Quando tiver terminado a importação, você vai notar três novas pastas **materiais**, **modelos**, e **pré-fabricados**, foram adicionados ao seu **ativos**pasta. Esse tipo de estrutura de pastas é típico para um projeto do Unity.

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-37.png)

    1.  Abra o **modelos** pasta e você verá que o **InsideOutSphere** modelo foi importado.

    2.  Dentro de **materiais** pasta, você encontrará o **InsideOutSpheres** material *lambert1*, junto com um material chamado *ButtonMaterial*, que é usado por GazeButton, o que você verá em breve.

    3.  O **pré-fabricados** pasta contém o **InsideOutSphere** pré-fabricado que contém ambos os **InsideOutSphere** *modelo* e o  *GazeButton*.

    4.  **Nenhum código foi incluído**, você irá escrever o código seguindo este curso.


4.  Dentro de **hierarquia**, selecione o **câmera principal** de objeto e atualizar os seguintes componentes:

    1.  **Transformação**

        1.  Posição = **X**: 0, **Y**: 0, **Z**: 0.

        2. Rotação = **X**: 0, **Y**: 0, **Z**: 0.

        3. Escala **X**: 1, **Y**: 1, **Z**: 1.

    2.  **Câmera**

        1. **Limpar os sinalizadores de**: Cor sólida.

        2.  **Planos de recorte**: Próximo: 0,1, agora: 6.

            ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-38.png)

5.  Navegue até a **pré-fabricado** pasta e, em seguida, arraste o **InsideOutSphere** pré-fabricado para o **hierarquia** painel.

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-39.png)

6.  Expanda o **InsideOutSphere** dentro do objeto de **hierarquia** clicando na pequena seta ao lado dele. Você verá uma **filho** objeto abaixo dele chamado **GazeButton**. Isso será usado para alterar o plano e, portanto, vídeos.

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-40.png)

7.  Na janela Inspetor, clique no **InsideOutSphere**do componente de transformação, certifique-se de que as seguintes propriedades são definidas:

    |            |    TRANSFORMAÇÃO - POSIÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    TRANSFORMAÇÃO - ROTAÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     TRANSFORMAÇÃO - ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-41.png)

8.  Clique no **GazeButton** objeto filho e defina seu **transformar** da seguinte maneira:

    |            |    TRANSFORMAÇÃO - POSIÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    TRANSFORMAÇÃO - ROTAÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMAÇÃO - ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importe o pacote do Unity InsideOutSphere](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>Capítulo 5 - criar a classe VideoController

O **VideoController** classe hospeda as duas extremidades de vídeos que serão usadas para transmitir o conteúdo do serviço de mídia do Azure.

Para criar essa classe:

1.  Com o botão direito no **pasta ativo**, localizado na **Project** painel e clique **criar > pasta**. Nomeie a pasta **Scripts**.

    ![Criar a classe VideoController](images/AzureLabs-Lab6-43.png)

    ![Criar a classe VideoController](images/AzureLabs-Lab6-44.png)

2.  Clique duas vezes no **Scripts** pasta para abri-lo.

3.  Clique com botão direito dentro da pasta e clique em **criar > C\# Script**. Nomeie o script **VideoController**.

    ![Criar a classe VideoController](images/AzureLabs-Lab6-45.png)

4.  Clique duas vezes na nova **VideoController** script para abri-lo com **Visual Studio 2017.**

    ![Criar a classe VideoController](images/AzureLabs-Lab6-46.png)

5.  Atualize os namespaces na parte superior do arquivo de código da seguinte maneira:

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  Insira as seguintes variáveis na **VideoController** classe, juntamente com o **Awake()** método:

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

7.  Agora é o momento para inserir os pontos de extremidade de seus vídeos do serviço de mídia do Azure:

    1.  O primeiro para o *video1endpoint* variável.
    
    2.  O segundo para o *video2endpoint* variável.

    > [!WARNING]
    > Há um problema conhecido com o uso *https* dentro do Unity, com a versão 2017.4.1f1. Se os vídeos de fornecem um erro no play, tente usar 'http'.

8.  Em seguida, o **Start ()** método precisa ser editado. Esse método será disparado sempre que o usuário alterna a cena (troca, consequentemente, o vídeo), observando o botão de olhares.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  Seguindo a **Start ()** método, insira o **playVideo** *IEnumerator* método, que será usado para iniciar vídeos diretamente (de modo que não é visto nenhum repetitivo).

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

10. O último método que você precisa para essa classe é o **ChangeScene()** método, que será usado para alternar entre as cenas.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > O **ChangeScene()** método usa um C útil\# recurso chamado o *operador condicional*. Isso permite condições sejam verificadas e, em seguida, os valores retornados com base no resultado da verificação, tudo em uma única instrução. Siga esse [link para saber mais sobre o operador condicional](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).

11. Salve suas alterações no Visual Studio antes de retornar para o Unity.

12. Novamente no Editor do Unity, clique e arraste a **VideoController** classe [from] {.underline} o **Scripts** pasta para o **câmera principal** do objeto no  **Hierarquia** painel.

13. Clique no **câmera principal** e examine o **painel Inspetor**. Você observará que, no componente de Script recém-adicionados, há um campo com um valor vazio. Isso é um campo de referência, que tem como alvo as variáveis públicas dentro de seu código.

14. Arraste o **InsideOutSphere** de objeto o **painel de hierarquia** para o **esfera** slot, conforme mostrado na imagem abaixo.

    ![Criar a classe VideoController](images/AzureLabs-Lab6-47.png)
    ![criar a classe VideoController](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Capítulo 6 - criar a classe de olhar

Essa classe é responsável por criar uma **Raycast** que beprojected encaminhará da **câmera principal**, para detectar qual objeto de usuário está observando. Nesse caso, o **Raycast** precisará identificar se o usuário está observando o **GazeButton** do objeto na cena e disparar um comportamento.

Para criar essa classe:

1.  Vá para o **Scripts** pasta que você criou anteriormente.

2.  Clique com botão direito no **Project** painel, **crie* *C\# Script**. Nomeie o script **olhares**.

3.  Clique duas vezes na nova ***olhares*** script para abri-lo com **Visual Studio 2017.**

4.  Verifique se que o namespace a seguir está na parte superior do script e remova todos os outros:

    ```csharp
    using UnityEngine;
    ```

5.  Em seguida, adicione as seguintes variáveis dentro do **olhares** classe:

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

6.  Código para o **Awake()** e **Start ()** métodos agora precisa ser adicionado.

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

7.  Adicione o seguinte código na **Update ()** método um Raycast do projeto e detectar a ocorrência de destino:

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

8.  Salve suas alterações no Visual Studio antes de retornar para o Unity.

9.  Clique e arraste a **olhares** classe da pasta de Scripts para o objeto de câmera principal na **hierarquia** painel.

## <a name="chapter-7---setup-the-two-unity-scenes"></a>Capítulo 7 - instalação as duas cenas de Unity

O objetivo deste capítulo é configurar as duas cenas, cada uma hospedando um vídeo em fluxo. Você vai duplicar a cena que você já tiver criado, para que você não precisa configurá-lo novamente, embora, em seguida, você editará a nova cena, para que o *GazeButton* objeto está em um local diferente e tem uma aparência diferente. Isso é para mostrar como alterar entre as cenas.

1.  Fazer isso acessando **arquivo > Salvar cena como...** . Salvamento janela será exibida. Clique o **nova pasta** botão.

    ![Capítulo 7 - instalação as duas cenas de Unity](images/AzureLabs-Lab6-49.png)

2.  Nomeie a pasta **cenas**.

3.  O **salvar cena** janela ainda será aberta. Abra seu recém-criado **cenas** pasta.

4.  No **nome do arquivo:** campo de texto, digite **VideoScene1**, em seguida, pressione **salvar**.

5.  Novamente no Unity, abra sua **cenas** pasta e o botão esquerdo do mouse seu **VideoScene1** arquivo. Usar o teclado e pressione **Ctrl + D** duplicará essa cena

    > [!TIP]
    > O **duplicar** também pode ser executado, navegando até o comando **Editar > Duplicar**.

6.  Unity automaticamente incrementar o número de nomes da cena, mas verifique-lo de qualquer forma, se que ele corresponde ao código inserido anteriormente.

    >  Você deve ter **VideoScene1** e **VideoScene2**.

7.  Com suas duas cenas, vá para **arquivo > configurações de Build**. Com o **configurações de Build** janela aberta, arraste seu plano para o **cenas em compilação** seção.

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > Você pode selecionar ambas suas cenas de sua **cenas** pasta por meio de espera a **Ctrl** botão e, em seguida, left-clicking cada cena e, por fim, arraste os dois em.

8.  Fechar o **configurações de Build** janela e clique duas vezes na **VideoScene2**.

9.  Com a segunda cena aberta, clique no **GazeButton** objeto filho do **InsideOutSphere**e defina sua transformação da seguinte maneira:

    |            |    TRANSFORMAÇÃO - POSIÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    TRANSFORMAÇÃO - ROTAÇÃO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMAÇÃO - ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. Com o **GazeButton** filho ainda selecionado, procure na **Inspetor** e nos **filtro de malha**. Clique o destino pequeno ao lado de **malha** campo de referência:

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-51.png)

11. Um **selecionar malha** janela pop-up será exibida. Clique duas vezes o **cubo** na lista de malha **ativos**.

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-52.png)

12. O **filtro de malha** atualizará e ser agora uma **cubo**. Agora, clique o **engrenagem** ícone próximo ao **esfera Colisor** e clique em **remover componente**, para excluir o colisor deste objeto.

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-53.png)

13. Com o **GazeButton** ainda selecionada, clique o **Add Component** botão na parte inferior da **Inspetor**. No campo de pesquisa, digite **caixa de**, e **Box Collider** será ser uma opção – clique que, para adicionar um **Box Collider** ao seu **GazeButton** objeto .

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-54.png)

14. O **GazeButton** está agora parcialmente atualizada, para uma aparência diferente, no entanto, agora você criará uma nova **Material**, de modo que ele tem uma aparência completamente diferente e é mais fácil de reconhecer como um objeto diferente, que o objeto na cena primeiro.

15. Navegue até sua **materiais** pasta, dentro de **painel projeto**. Duplicar o **ButtonMaterial** Material (pressione **Ctrl** + **1!d** no teclado ou o botão esquerdo do mouse a **Material**, em seguida, dos **edite** opção de menu, selecione arquivo **duplicar**).

    ![Capítulo 7-- Configurar as duas cenas Unity](images/AzureLabs-Lab6-55.png)
    ![capítulo 7-- configurar as duas cenas de Unity](images/AzureLabs-Lab6-56.png)

16. Selecione a nova **ButtonMaterial** Material (aqui chamado **ButtonMaterial 1**) e dentro a **Inspetor**, clique no **Albedo** cor janela. Um pop-up será exibida, onde você pode selecionar outra cor (escolha aquele que você deseja), em seguida, feche o janela pop-up. O Material será sua própria instância e diferente do original.

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-57.png)

17. Arraste o novo **Material** até a **GazeButton** filho, agora atualizar completamente sua aparência, para que ele seja facilmente perceptível a partir do primeiro botão de segundo plano.

    ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-58.png)

18. Neste ponto, você pode testar o projeto no Editor antes de compilar o projeto UWP.

    -  Pressione a **reproduzir** botão na **Editor** e o desgaste fone de ouvido.

        ![Capítulo 7-- Configurar as duas cenas de Unity](images/AzureLabs-Lab6-59.png)

19. Examinar os dois **GazeButton** objetos para alternar entre o primeiro e segundo vídeo.

## <a name="chapter-8---build-the-uwp-solution"></a>Capítulo 8 - Compile a solução UWP

Depois que você garante que o editor não tem erros, você está pronto para compilação.

Para construir:

1.  Salve a cena atual clicando em **arquivo > Salvar**.

2.  Marque a caixa denominada **Unity C\# projetos** (Isso é importante porque ele permitirá que você editar as classes após a compilação for concluída).

3.  Vá para **arquivo > configurações de Build**, clique em **Build**.

4.  Você será solicitado a selecionar a pasta onde você deseja buildthe solução.

5.  Criar uma **compilações** pasta e dentro dessa pasta, crie outra pasta com um nome apropriado de sua escolha.

6.  Clique em sua nova pasta e, em seguida, clique em **Selecionar pasta**, portanto, para escolher a pasta, para iniciar a compilação nesse local.

    ![Capítulo 8 – Criar a solução UWP](images/AzureLabs-Lab6-60.png)
    ![capítulo 8 - Compile a solução UWP](images/AzureLabs-Lab6-61.png)

7.  Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um **Explorador de arquivos** janela no local de sua compilação.

## <a name="chapter-9---deploy-on-local-machine"></a>Capítulo 9 - implantar no computador Local

Quando a compilação for concluída, uma **Explorador de arquivos** janela será exibida no local de sua compilação. Abra a pasta denominada e criado para e, em seguida, clique duas vezes no arquivo de solução (. sln) nessa pasta, para abrir sua solução com o Visual Studio 2017.

Tudo o que resta fazer é implantar seu aplicativo no seu computador (ou *computador Local*).

Para implantar a máquina Local:

1.  Na **Visual Studio 2017**, abra o arquivo de solução que acabou de ser criado.

2.  No **plataforma da solução**, selecione **x86, computador Local**.

3.  No **configuração da solução** selecionar **depurar**.

    ![Capítulo 9 – Implantar no computador Local](images/AzureLabs-Lab6-62.png)

4.  Agora, você precisará restaurar todos os pacotes para sua solução. Clique com botão direito no seu **Solution**e clique em **restaurar pacotes do NuGet para solução...**

    > [!NOTE] 
    > Isso é feito porque os pacotes que Unity criado precisam ser direcionados para funcionar com as referências de computadores locais.

5.  Vá para **menu Build** e clique em **implantar solução** para carregar o aplicativo em seu computador. Visual Studio criará primeiro e, em seguida, implantar seu aplicativo.

6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado.

    ![Capítulo 9 – Implantar no computador Local](images/AzureLabs-Lab6-63.png)

Quando você executar o aplicativo de realidade misturada, você irá obedecer a **InsideOutSphere** modelo que usado dentro de seu aplicativo. Essa esfera será onde o vídeo será transmitido, fornecendo uma visão de 360 graus de vídeo de entrada (que foi é feito para esse tipo de ponto de Vista). Não se surpreenda que se o vídeo leva alguns segundos para carregar, seu aplicativo está sujeito a velocidade com a Internet disponível, como o vídeo precisa ser buscadas e, em seguida, baixados, portanto, para transmitir em seu aplicativo.
Quando você estiver pronto, alterar cenas e abra seu segundo vídeo, pela observação na esfera vermelha! Em seguida, fique à vontade voltar, usando o cubo azul na cena segundo!

## <a name="your-finished-azure-media-service-application"></a>O aplicativo de serviço de mídia do Azure concluído
 
Parabéns, você criou um aplicativo de realidade mista que aproveita o serviço de mídia do Azure para transmitir 360 vídeos.

![resultado de laboratório](images/AzureLabs-Lab6-00.png)

![resultado de laboratório](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

**Exercício 1**

Ele é totalmente possível usar apenas uma única cena para alterar o vídeos dentro deste tutorial. Experimentar seu aplicativo e torná-lo em uma única cena! Talvez, até mesmo adicione outro vídeo à combinação.

**Exercício 2**

Teste com o Azure e o Unity e tentar implementar a capacidade para o aplicativo selecionar automaticamente um vídeo com um tamanho de arquivo diferente, dependendo da força de uma conexão de Internet.


