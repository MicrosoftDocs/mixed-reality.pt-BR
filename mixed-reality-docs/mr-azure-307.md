---
title: Aprendizado de máquina 307 - MR e o Azure
description: Conclua este curso para aprender a implementar o Azure Machine Learning Studio dentro de um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, aprendizado de máquina, AM, o estúdio de machine learning, hololens, envolventes e vr
ms.openlocfilehash: 93263817df0fd809a09b32c1b34a636eab7026a1
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516036"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-and-azure-307-machine-learning"></a>MR e o Azure 307: Aprendizado de máquina

![final do produto-iniciar](images/AzureLabs-Lab7-0.png)

Neste curso, você aprenderá como adicionar recursos de aprendizado de máquina (ML) para um aplicativo de realidade misturada usando o Azure Machine Learning Studio.

*O Azure Machine Learning Studio* é um serviço da Microsoft, que fornece aos desenvolvedores um grande número de algoritmos de aprendizado de máquina, que pode ajudar com os dados de entrada, saída, preparação e visualização. Desses componentes, em seguida, é possível desenvolver um experimento de análise preditiva, itere sobre ela e usá-lo para treinar seu modelo. Após o treinamento, é possível fazer seu modelo operacional em nuvem do Azure, para que, em seguida, ele pode pontuar novos dados. Para obter mais informações, visite o [página do Azure Machine Learning Studio](https://azure.microsoft.com/en-au/services/machine-learning-studio/).

Com a conclusão deste curso, você terá um aplicativo de imersão headset de realidade mista e terá aprendido como fazer o seguinte:

1.  Fornecer uma tabela de dados de vendas para o *do Azure Machine Learning Studio* portal e o design de um algoritmo para prever vendas futuras itens populares.
2.  Criar uma **projeto do Unity**, que pode receber e interpretar os dados de previsão do serviço ML.
3.  Exibir os dados de predicação visualmente dentro de **projeto do Unity**, por meio de fornecer os itens mais populares de vendas, em uma prateleira.

Em seu aplicativo, ele cabe a você sobre como você irá integrar os resultados com seu design. Este curso é projetado para ensinar a você como integrar um serviço do Azure ao seu projeto do Unity. Ele é seu trabalho para usar o conhecimento obtido com este curso para aprimorar seu aplicativo de realidade misturada.

Este curso é um tutorial independente, o que não envolvem diretamente quaisquer outros laboratórios de realidade mista.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> MR e o Azure 307: Aprendizado de máquina</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Enquanto este curso se concentra primariamente em fones de ouvido Windows Mixed Reality de imersão (VR), você também pode aplicar o que você aprenderá neste curso para o Microsoft HoloLens. Como acompanhar o curso, você verá notas quaisquer alterações que talvez seja necessário empregar para dar suporte ao HoloLens. Ao usar o HoloLens, você pode perceber algum eco durante a captura de voz.

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial é projetado para desenvolvedores que têm experiência básica com o Unity e C#. Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (maio de 2018). Você é livre para usar o software mais recente, conforme listado dentro de [instalar o artigo de ferramentas](install-the-tools.md), embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente que o que é listado abaixo .

Recomendamos que o hardware e software para este curso a seguir:

- Um computador, de desenvolvimento [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de fone de ouvido imersivo (VR)
- [Windows 10 Fall Creators Update (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md#installation-checklist)
- [O SDK mais recente do Windows 10](install-the-tools.md#installation-checklist)
- [2017.4 do Unity](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Um [fone de ouvido Windows Mixed Reality de imersão (VR)](immersive-headset-hardware-details.md) ou [Microsoft HoloLens](hololens-hardware-details.md) com o modo de desenvolvedor habilitado
- Acesso à Internet para a instalação do Azure e a recuperação de dados do ML

## <a name="before-you-start"></a>Antes de começar

Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação). 

## <a name="chapter-1---azure-storage-account-setup"></a>Capítulo 1 - configuração da conta de armazenamento do Azure

Para usar a API de tradução do Azure, você precisará configurar uma instância do serviço a ser disponibilizado para seu aplicativo.
1.  Faça logon na [Portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, você precisará criá-lo. Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.

2.  Quando você estiver conectado, clique em **contas de armazenamento** no menu à esquerda.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.

3.  Sobre o **contas de armazenamento** guia, clique em **Add**.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-2.png)

4.  No **criar conta de armazenamento** painel:

    1.  Inserir uma **nome** para sua conta, lembre-se que este campo aceita apenas números e letras minúsculas.
    2.  Para **modelo de implantação** selecionar **Gerenciador de recursos**.
    3.  Para **tipo de conta**, selecione **(uso geral v1) de armazenamento**.
    4.  Para **desempenho**, selecione **padrão**.
    5.  Para **replicação** selecionar **leitura-acesso-com redundância geográfica (RA-GRS) de armazenamento**.
    6.  Deixe **transferência segura obrigatória** como **desabilitado**.
    7.  Selecione uma **assinatura**.
    4. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns).

        > Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).
    
    5.  Determinar a **local** para seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local seria o ideal é que na região em que o aplicativo é executado. Alguns ativos do Azure estão disponíveis somente em determinadas regiões.

5.  Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-3.png)

6.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

7.  Uma notificação será exibida no portal depois que a instância do serviço é criada.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>Capítulo 2 - o Azure Machine Learning Studio

Para usar o *do Azure Machine Learning*, você precisará configurar uma instância do serviço de Machine Learning para ficar disponível para seu aplicativo.

1.  No Portal do Azure, clique em **New** no canto superior esquerdo de canto e procure **espaço de trabalho do Machine Learning Studio**, pressione **Enter**.

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  A nova página fornecerá uma descrição do **espaço de trabalho do Machine Learning Studio** service. Na parte inferior esquerda desse prompt, clique no **criar** botão para criar uma associação com este serviço.

3.  Depois de clicar em **Create**, um painel será exibido em que você precisa fornecer alguns detalhes sobre sua nova **serviço de Machine Learning Studio**:

    1.  Inserir sua desejada **nome do espaço de trabalho** para esta instância de serviço.

    2.  Selecione uma **assinatura**.

    3. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados com um único projeto (por exemplo, como estes laboratórios) em um grupo de recursos comuns). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Determinar a **local** para seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local seria o ideal é que na região em que o aplicativo é executado. Alguns ativos do Azure estão disponíveis somente em determinadas regiões. Você deve usar o mesmo grupo de recursos que você usou para criar o armazenamento do Azure no capítulo anterior.

    5.  Para o **conta de armazenamento** seção, clique em **usar existente**, em seguida, clique no menu suspenso e a partir daí, clique o **conta de armazenamento** você criou no último capítulo.

    6.  Selecionar as devidas **tipo de preço do espaço de trabalho** para você, no menu suspenso.

    7.  Dentro de **plano do serviço Web** seção, clique em **Create** **novo,** , em seguida, insira um nome para ele no campo de texto.

    8.  Dos **tipo de preço de plano de serviço Web** , selecione a camada de preço de sua escolha. Um chamada de camada de teste de desenvolvimento **padrão de desenvolvimento/teste** devem estar disponíveis para você sem custo adicional.

    9.  Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.

    10. Clique em **Criar**.

        ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

5.  Uma notificação será exibida no portal depois que a instância do serviço é criada.

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  Clique na notificação para explorar a nova instância do serviço.

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço.

8.  Na página exibida, sob o **Links adicionais** seção, clique em **iniciar o estúdio de Machine Learning**, que direcionará o seu navegador para o **Machine Learning Studio** Portal.

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  Use o **entrar** botão, na parte superior direita ou no centro, para fazer logon em seu Machine Learning Studio.

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>Capítulo 3 - Machine Learning Studio: Instalação do conjunto de dados

Uma das maneiras de trabalham de algoritmos de aprendizado de máquina está analisando os dados existentes e, em seguida, tentar prever resultados futuros com base no conjunto de dados existente. Isso geralmente significa que os dados mais existentes que você tiver, melhor o algoritmo será ao prever resultados futuros.

Uma tabela de exemplo é fornecida para você, para este curso, chamado [ProductsTableCSV e pode ser baixado aqui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).

> [!IMPORTANT]
> O arquivo. zip acima contém ambas as **ProductsTableCSV** e o **unitypackage**, que será necessária no [capítulo 6](#chapter-6---importing-the-mlproducts-unity-package). Este pacote também é fornecido dentro desse capítulo, embora separado para o arquivo csv.

Esse conjunto de dados de exemplo contém um registro dos objetos mais vendidos em cada hora de cada dia do ano de 2017.
        
![O Machine Learning Studio: Instalação do conjunto de dados](images/AzureLabs-Lab7-11.png)

Por exemplo, no dia 1 de 2017, às 13:30 (hora 13), o item mais vendido era salt e pepper.

Esta tabela de exemplo contém 9998 entradas.

1.  Volte para o **Machine Learning Studio** portal, e adicione essa tabela como um **conjunto de dados** para seu ML. Faça isso clicando o **+ novo** botão no canto inferior esquerdo da tela.

    ![O Machine Learning Studio: Instalação do conjunto de dados](images/AzureLabs-Lab7-12.png)

2.  Uma seção aparecerá na parte inferior e, em que há o painel de navegação à esquerda. Clique em **Dataset**, em seguida, à direita, **do arquivo Local**.

    ![O Machine Learning Studio: Instalação do conjunto de dados](images/AzureLabs-Lab7-13.png)

3.  Carregar o novo **conjunto de dados** seguindo estas etapas:

    1. A janela de carregamento será exibida, onde você pode **procurar** seu disco rígido para o novo conjunto de dados.

        ![O Machine Learning Studio: Instalação do conjunto de dados](images/AzureLabs-Lab7-14.png)

    2.  Quando selecionado e de volta na janela de upload, deixe a caixa de seleção não marcada.

    3.  No campo de texto abaixo, insira **ProductsTableCSV.csv** como o nome do conjunto de dados (embora deve ser adicionado automaticamente).

    4.  Usando o menu suspenso para **tipo**, selecione **arquivo CSV genérico com um cabeçalho (. csv)** .

    5.  Pressione a escala na parte inferior direita da janela de carregamento e seu **conjunto de dados** será carregado.

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>Capítulo 4 - Machine Learning Studio: O experimento

Antes de compilar seu sistema de aprendizado de máquina, você precisará criar um experimento, para validar sua teoria sobre seus dados. Com os resultados, você saberá se você precisa de mais dados, ou se não houver nenhuma correlação entre os dados e um resultado possível.

Para iniciar a criação de um experimento:

1.  Clique novamente na **+ novo** botão na parte inferior esquerda da página, clique em **experimento** > **experimento em branco**.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-15.png)

2.  Uma nova página será exibida com um teste em branco:

3.  No painel à esquerda, expanda **conjuntos de dados salvos* > *Meus conjuntos de dados** e arraste o **ProductsTableCSV** para o **Tela de experimento**.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-16.png)

4.  No painel à esquerda, expanda **Data Transformation** > **exemplo e dividir**. Em seguida, arraste a **dividir dados** item para o **tela do experimento**. O item de dados de divisão irá dividir o conjunto de dados em duas partes. Uma parte que você usará para treinar o algoritmo de aprendizado de máquina. A segunda parte será usada para avaliar a precisão do algoritmo gerado.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-17.png)

5.  No painel à direita (enquanto os dados de divisão item na tela é selecionado), edite o **fração de linhas no primeiro conjunto de dados de saída** à **0,7**. Isso dividirá os dados em duas partes, a primeira parte será 70% dos dados e a segunda parte será de 30% restantes. Para garantir que os dados são divididos aleatoriamente, verifique se o **divisão aleatória** caixa de seleção permanece marcada.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-18.png)

6.  Arraste uma conexão da base do **ProductsTableCSV** item na tela para a parte superior do item de dados de divisão. Isso se conectará os itens e enviar o **ProductsTableCSV** saída do conjunto de dados (os dados) para a entrada de dados de divisão.  

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-19.png)

7.  No **experimentos** do painel no lado esquerdo, expanda **Machine Learning* > * Train * *. Arraste o **modelo de treinamento** item fora à tela do experimento. Sua tela deve ser o mesmo que o abaixo.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-20.png)

8.  Do ***canto inferior esquerdo*** da **dividir dados** item arrastar uma conexão para o **parte superior direita** do **treinar modelo** item. A primeira divisão de 70% do conjunto de dados será usada pelo modelo de treinamento para treinar o algoritmo.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-21.png)

9.  Selecione o **modelo de treinamento** item na tela e, no **propriedades** painel (no lado direito da janela do navegador), clique o **iniciar seletor de coluna** botão.

10. Na caixa de texto Digite **produto** e, em seguida, pressione **Enter**, *produto* será definido como uma coluna para treinar previsões. Depois disso, clique no **escala** no canto inferior direito para fechar a caixa de diálogo de seleção.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-22.png)

11. Você pretende treinar uma **Regressão logística Multiclasse** algoritmo para prever mais vendidos **produto** com base na hora do dia e a data. Ele está além do escopo deste documento para explicar os detalhes dos diferentes algoritmos fornecidos pelo Azure Machine Learning studio, no entanto, você pode descobrir mais sobre o [folha de consulta de algoritmo do Machine Learning](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)

12. No painel de itens de teste à esquerda, expanda * **Machine Learning* > *inicializar modelo* > * classificação * * * e arraste o **Regressão logística Multiclasse**  item para a tela do experimento.

13. Conecte a saída, da parte inferior da **Regressão logística Multiclasse**, com a entrada do canto superior esquerdo do **treinar modelo** item.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-23.png)

14. Na lista de itens do experimento no painel à esquerda, expanda **Machine Learning* > * pontuação * * e arraste a **modelo de pontuação** item na tela de desenho.

15. Conecte a saída, da parte inferior da **modelo de treinamento**, com a entrada do canto superior esquerdo do **modelo de pontuação**.

16. Conecte a saída do canto inferior direito da **dividir dados**, à entrada do canto superior direito do  **modelo de pontuação* item*.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-24.png)

17. Na lista de **experimento** itens no painel à esquerda, expanda * **Machine Learning* > * avaliar * * * e arraste o **avaliar modelo** item para a tela.

18. Conecte a saída do **modelo de pontuação** à entrada do canto superior esquerdo a **avaliar modelo**.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-25.png)

19. Você criou seu primeiro experimento de aprendizado de máquina. Agora você pode salvar e executar o teste. No menu na parte inferior da página, clique no **salve** botão para salvar seu experimento e, em seguida, clique em **executar** para iniciar o teste.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-26.png)

20. Você pode ver os **status** do experimento no canto superior direito da tela. Aguarde alguns instantes para que o teste a fim de concluir.

    > Se você tiver um conjunto de dados grande (reais), é provável que o teste pode levar horas para ser executado.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-27.png)

21. Clique com botão direito do **avaliar modelo** item na tela e de passagem do menu de contexto o mouse sobre **resultados da avaliação**, em seguida, selecione **visualizar**.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-28.png)

22. Os resultados da avaliação serão exibidos mostrando os resultados previstos versus os resultados reais. Isso usa a 30% do conjunto de dados original, que foi dividido em versões anteriores, para avaliar o modelo. Você pode ver que os resultados não são ótimos, o ideal é que você teria o número mais alto em cada linha ser o item realçado nas colunas.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-29.png)

23. Fechar o **resultados**.

24. Usar o modelo de Machine Learning treinado recentemente, você precisa para expô-lo como um **serviço Web**. Para fazer isso, clique no **configurar o serviço Web** menu item no menu na parte inferior da página e clique em **serviço Web preditivo**.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-30.png)

25. Uma nova guia será criada e o modelo de treinamento são mesclados para criar o novo serviço web. 

26. No menu na parte inferior da página, clique em **salve**, em seguida, clique em **executar**. Você verá o status seja atualizado no canto superior direito da tela do experimento.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-31.png)

27. Depois de terminar a execução, uma **implantar serviço Web** botão será exibido na parte inferior da página. Você está pronto para implantar o serviço web. Clique em **implantar serviço Web** (clássico) no menu na parte inferior da página.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-32.png)

    > Pode solicitar que o navegador para permitir que um pop-up, você deve **permitem**, embora você talvez seja necessário pressionar **implantar serviço Web** novamente, se não mostrar a página de implantação. 

28. Quando o teste tiver sido criado. você será redirecionado para um **Dashboard** página no qual você terá seu **chave de API** exibido. Copie-o em um bloco de notas no momento, você precisará dele em seu código muito em breve. Depois que você observou a sua chave de API, clique no **solicitação/resposta** botão na **ponto de extremidade padrão** seção sob a chave.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > Se você clicar em teste nesta página, você poderá inserir dados de entrada e exibir a saída. Insira o **dia** e **hora**. Deixe o **produto** entrada em branco. Em seguida, clique o **confirmar** botão. A saída na parte inferior da página mostrará o JSON que representa a probabilidade de cada produto que está sendo a escolha.

29. Uma nova página da web será aberta, exibindo as instruções e alguns exemplos sobre a estrutura de solicitação necessários para o Machine Learning Studio. Cópia de **URI de solicitação** exibidos nesta página, no seu bloco de notas.

    ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-34.png)

Você agora criou um sistema que fornece o produto mais provável de serem vendidos com base em dados históricos de compras, correlacionados com a hora do dia e dia do ano de aprendizado de máquina.

Para chamar o serviço web, você precisará da URL para o ponto de extremidade de serviço e uma chave de API para o serviço. Clique no **Consume** guia, no menu superior.

O **consumo** página de informações exibirá as informações que você precisará chamar o serviço web do seu código. Faça uma cópia de **chave primária** e o **solicitação-resposta** URL. Você precisará no próximo capítulo.

## <a name="chapter-5---setting-up-the-unity-project"></a>Capítulo 5 – configurar o projeto do Unity

Configurar e testar o fone imersivo realidade mista.

> [!NOTE]
>  Você irá **não** exigem controladores de movimento para este curso. Se você precisar dar suporte a configurar o fone de ouvido imersivo, clique em [aqui](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra **Unity** e crie um novo projeto do Unity chamada **MR\_MachineLearning.** Verifique se o tipo de projeto é definido como **3D**.

2.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Vá para ***edite* > *preferências*** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

3.  Em seguida, vá para ***arquivo* > *configurações de Build*** e alternar a plataforma **plataforma Universal do Windows**, clicando em o ***alternar plataforma*** botão.

4.  Também verifique se:

    1.  **Dispositivo de destino** é definido como **qualquer dispositivo**.

        > Para o Microsoft HoloLens, defina **dispositivo de destino** à *HoloLens*.

    2.  **Tipo de compilação** é definido como **D3D**.

    3.  **SDK** é definido como **mais recente instalada**.

    4.  **Versão do Visual Studio** é definido como **mais recente instalada**.

    5.  **Compilar e executar** é definido como **computador Local**.

    6.  Não se preocupe sobre como configurar o **cenas** no momento, conforme eles são fornecidos posteriormente.

    7.  As configurações restantes devem ser deixadas como padrão por enquanto.

        ![Configurar o projeto do Unity](images/AzureLabs-Lab7-35.png)

5.  No **configurações de Build** janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o **Inspetor** está localizado. 

6. Neste painel, algumas configurações precisam ser verificados:

    1.  No **outras configurações** guia:

        1.  **Criação de scripts** **versão de tempo de execução** deve ser **Experimental** (equivalente ao .NET 4.6)

        2. **Script de back-end** deve ser ***.NET***

        3. **Nível de compatibilidade de API** deve ser **.NET 4.6**

            ![Configurar o projeto do Unity](images/AzureLabs-Lab7-36.png)

    2.  Dentro de **configurações de publicação** guia, em **recursos**, verifique:

        - **InternetClient**

            ![Configurar o projeto do Unity](images/AzureLabs-Lab7-37.png)

    3.  Mais para baixo no painel, no **configurações XR** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **SDK de realidade mista do Windows**  é adicionado

        ![Configurar o projeto do Unity](images/AzureLabs-Lab7-38.png)

    

6.  Volta **configurações de Build** *Unity C#*  projetos não fica acinzentado; marque a caixa de seleção ao lado disso. 

7.  Feche a janela de configurações de Build.

8.  Salve seu projeto (**arquivo > Salvar projeto**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>Capítulos 6 - importar o pacote do Unity MLProducts

Para este curso, você precisará baixar um pacote do Unity Asset chamado [ **Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage). Este pacote vem completo com uma cena, com todos os objetos no ou predefinidas, portanto, você pode focalizar obtendo-tudo em funcionamento. O **ShelfKeeper** script é fornecido, porém mantém apenas variáveis públicas, para fins de estrutura de configuração da cena. Você precisará fazer todas as outras seções. 

Para importar este pacote:

1.  Com o painel do Unity na sua frente, clique em **ativos** no menu na parte superior da tela, em seguida, clique em **Importar pacote, o pacote personalizado**.

    ![Importe o pacote do Unity MLProducts](images/AzureLabs-Lab7-39.png)

2.  Use o seletor de arquivos para selecionar o **Azure-MR-307.unitypackage** de pacote e clique em **abrir**.

3.  Uma lista de componentes para esse ativo será exibida para você. Confirme a importação clicando **importação**.

    ![Importe o pacote do Unity MLProducts](images/AzureLabs-Lab7-40.png)

4.  Quando tiver terminado a importação, você vai notar que algumas pastas novas apareceu no seu Unity **painel projeto**. Esses são os modelos 3D e os respectivos materiais que fazem parte da cena predefinida, que você trabalhará na. Você irá escrever a maioria do código neste curso.

    ![Importe o pacote do Unity MLProducts](images/AzureLabs-Lab7-41.png)

5.  Dentro de **painel projeto** pasta, clique no **cenas** pasta e clique duas vezes na cena dentro (chamado **MR_MachineLearningScene**). A cena será aberta (veja a imagem abaixo). Se os losangos vermelhos estiverem ausentes, basta clicar o **utensílios** botão na parte superior direita do **painel de jogo**.

    ![Importe o pacote do Unity MLProducts](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>Capítulo 7 - verificando as DLLs no Unity

Para aproveitar o uso de bibliotecas JSON (usado para serializar e desserializar), uma DLL Newtonsoft tiver sido implementada com o pacote que é colocado no. A biblioteca deve ter a configuração correta, embora vale a pena verificar (especialmente se você estiver tendo problemas com o código não está funcionando). 

Para fazer isso:

-  Clique no arquivo Newtonsoft dentro da pasta de plug-ins e examine os **painel Inspetor**. Certifique-se **qualquer plataforma** está marcada. Vá para o **guia UWP** e certifique-se também **não processar** está marcada.

    ![Importando as DLLs no Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>Capítulo 8 - criar a classe ShelfKeeper

O **ShelfKeeper** classe hospeda métodos que controlam a interface do usuário e os produtos gerados na cena.

Como parte do pacote importado, você será receberam essa classe, embora ele está incompleto. Agora é hora de conclusão dessa classe:

1.  Clique duas vezes no **ShelfKeeper** script dentro de **Scripts** pasta para abri-lo com **Visual Studio 2017**.

2.  Substitua todo o código existente no script com o código a seguir, que define a data e hora e tem um método para exibir um produto.

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  Certifique-se de salvar suas alterações no **Visual Studio** antes de retornar ao **Unity**.

4.  Novamente no Editor do Unity, verifique se o **ShelfKeeper** classe é semelhante a abaixo:

    ![Criar a classe ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > Se o seu script não tem os destinos de referência (ou seja, *Data (texto de malha)* ), basta arrastar os objetos correspondentes do **painel de hierarquia**, nos campos de destino. Veja a seguir para obter explicação, se necessário:
    > 
    > 1.  Abra o **ponto Spawn** dentro da matriz a **ShelfKeeper** por left-clicking-lo de script do componente. Uma subseção será exibida chamada **tamanho**, que indica o tamanho da matriz. Tipo de **3** na caixa de texto próximo a **tamanho** e pressione **Enter**, e três slots serão criadas abaixo.
    > 2. Dentro de **hierarquia** expandir a **exibição de tempo** objeto (por left-clicking na seta ao lado dela). Em seguida clique o ***câmera principal*** de dentro a **hierarquia**, de modo que o **Inspetor** mostra suas informações.
    > 3. Selecione o **câmera principal** na **painel de hierarquia**. Arraste o **data** e **tempo** objetos do **painel de hierarquia** para o **texto data** e **texto de tempo de** slots dentro a **Inspector** da **câmera principal** no **ShelfKeeper** componente.
    > 4. Arraste o **Spawn pontos** da **painel de hierarquia** (abaixo a *prateleira* objeto) para o **3** **elemento**referenciar destinos sob o **Spawn ponto** de matriz, conforme mostrado na imagem.
    > 
    >     ![Criar a classe ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>Capítulo 9 - criar a classe ProductPrediction

A próxima classe que você pretende criar é a **ProductPrediction** classe.

Essa classe é responsável por:

-   Consultando o **serviço de Machine Learning** instância, o que fornece a data e hora atuais.

-   Desserializar a resposta JSON em dados utilizáveis.

-   Interpretando os dados, recuperando os 3 produtos recomendados.

-   Chamar o **ShelfKeeper** métodos para exibir os dados na cena de classe.

Para criar essa classe:

1.  Vá para o **Scripts** pasta, no **painel projeto**.

2.  Clique com botão direito dentro da pasta **Create** > **C\# Script**. Chame o script **ProductPrediction**.

3.  Clique duas vezes na nova **ProductPrediction** script para abri-lo com **Visual Studio 2017**.

4.  Se o **modificação de arquivo detectado** caixa de diálogo é exibida, clique em ***recarregar solução**.

5.  Adicione os seguintes namespaces na parte superior da classe ProductPrediction:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  Dentro de **ProductPrediction** classe inserir os dois objetos a seguir, que são compostos de um número de classes aninhadas. Essas classes são usadas para serializar e desserializar o JSON para o serviço de Machine Learning.

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  Em seguida, adicione as seguintes variáveis acima do código anterior (de modo que o JSON relacionados ao código é na parte inferior do script, todos os outros código abaixo e para fora do caminho):

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > Certifique-se de inserir o **chave primária** e **ponto de extremidade de solicitação-resposta**, do Portal de aprendizado de máquina para as variáveis aqui. As imagens abaixo mostram onde você teria levado a chave e o ponto de extremidade de. 
    >  
    > ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![O Machine Learning Studio: O experimento](images/AzureLabs-Lab7-53-2.png)

8.  Inserir esse código dentro de **Start ()** método. O **Start ()** método é chamado quando a classe é inicializado:

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  Este é o método que coleta a data e hora do Windows e o converte em um formato que nosso teste de Machine Learning pode usar para comparar com os dados armazenados na tabela.

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. Você pode **exclua** as **Update ()** método uma vez que essa classe não irá usá-lo.

11. Adicione o seguinte método que irá comunicar-se a data e hora atuais para o ponto de extremidade do aprendizado de máquina e receber uma resposta no formato JSON.

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. Adicione o seguinte método, que é responsável para desserializar a resposta JSON e comunicando-se o resultado da desserialização para o **ShelfKeeper** classe. Esse resultado será que os nomes dos três itens previstos para vender mais na data e hora atuais. Insira o código abaixo para o **ProductPrediction** classe, abaixo do método anterior.

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. Salve **Visual Studio** e volte ao **Unity**.

14. Arraste o **ProductPrediction** script a partir de classe a **Script** pasta, para o **câmera principal** objeto.

15. Salvar sua cena e seu projeto **arquivo** >  ***salvar cena* / *arquivo***   >  **Salvar projeto**.

## <a name="chapter-10---build-the-uwp-solution"></a>Capítulo 10 - Compile a solução UWP

Agora é hora de criar seu projeto como uma solução UWP, para que ele pode ser executado como um aplicativo autônomo.

Para construir:

1.  Salve a cena atual clicando em **arquivo** **cenas salvar**.

2.  Vá para **arquivo** **configurações de Build**

3.  Marque a caixa denominada **Unity C\# projetos** (Isso é importante porque ele permitirá que você editar as classes após a compilação for concluída).

4.  Clique em **adicionar cenas abertas**,

5.  Clique em **Compilar**.

    ![Compile a solução UWP](images/AzureLabs-Lab7-54.png)

6.  Você será solicitado a selecionar a pasta onde você deseja criar a solução.

7.  Criar uma **compilações** pasta e dentro dessa pasta, crie outra pasta com um nome apropriado de sua escolha.

8.  Clique em sua nova pasta e, em seguida, clique em **Selecionar pasta**, para iniciar a compilação nesse local.

    ![Compile a solução UWP](images/AzureLabs-Lab7-55.png)

    ![Compile a solução UWP](images/AzureLabs-Lab7-56.png)

9.  Uma vez Unity terminou de construção (pode levar algum tempo), ele será aberto um **Explorador de arquivos** janela no local de sua compilação (verificar sua barra de tarefas, como sempre não pode aparecer acima do windows, mas irá notificá-lo da adição de um novo janela).

## <a name="chapter-11---deploy-your-application"></a>Capítulo 11 - implantar seu aplicativo

Para implantar seu aplicativo:

1.  Navegue até seu novo build do Unity (o **App** pasta) e abra o arquivo de solução com **Visual Studio**.

2.  Com o Visual Studio aberta, você precisa restaurar pacotes do NuGet, que pode ser feito por meio de sua solução MachineLearningLab_Build, do Gerenciador de soluções (localizado à direita do Visual Studio), botão direito do mouse e, em seguida, clicando em Restaurar pacotes do NuGet:

    ![Adicionar pacotes NuGet](images/AzureLabs-Lab7-57.png)

3.  No, selecione a configuração da solução **depurar**.

4.  Na plataforma da solução, selecione **x86**, **Máquina Local**. 

    > Para o Microsoft HoloLens, talvez você ache mais fácil de definir isso como *máquina remota*, de modo que você não estiver vinculado ao seu computador. No entanto, você precisará também fazer o seguinte:
    > - Saber a **endereço IP** de seu HoloLens, que podem ser encontrado dentro a *Configurações > rede e Internet > Wi-Fi > Opções avançadas de*; o IPv4 é o endereço que você deve usar. 
    > - Certifique-se **modo de desenvolvedor** é **na**; encontrado na *Configurações > atualização e segurança > para os desenvolvedores*.

    ![Adicionar pacotes NuGet](images/AzureLabs-Lab7-58.png)

5.  Vá para **menu Build** e clique em **implantar solução** para carregar o aplicativo a seu computador.

6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado.

Quando você executa o aplicativo de realidade misturada, você verá o banco que foi definido na sua cena do Unity e de inicialização, os dados que você configurar no Azure serão buscados. Os dados serão desserializados dentro de seu aplicativo e os três primeiros resultados para a data e hora atuais serão fornecidos visualmente, como três modelos sobre o banco.


## <a name="your-finished-machine-learning-application"></a>O aplicativo de aprendizado de máquina concluído
 
Parabéns, você criou um aplicativo de realidade mista que aproveita o Azure Machine Learning para fazer previsões de dados e exibi-lo na sua cena.

![Adicionar pacotes NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>Exercício

**Exercício 1**

Fazer experiências com a ordem de classificação do seu aplicativo e ter as previsões de três inferior são exibidos na prateleira, como esses dados potencialmente seria útil também.

**Exercício 2**

Usando o **tabelas do Azure** popular uma nova tabela com informações meteorológicas e criar um novo experimento usando os dados.
