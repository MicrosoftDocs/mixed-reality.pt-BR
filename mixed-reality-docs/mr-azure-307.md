---
title: Sr e Azure 307-aprendizado de máquina
description: Conclua este curso para aprender a implementar Azure Machine Learning Studio em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, Machine Learning, ml, estúdio de Machine Learning, hololens, imersão, VR
ms.openlocfilehash: e302e287049cd746a436904c2af2bcc2b0835796
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926615"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br>

# <a name="mr-and-azure-307-machine-learning"></a>Sr e Azure 307: aprendizado de máquina

![início do produto final](images/AzureLabs-Lab7-0.png)

Neste curso, você aprenderá a adicionar recursos de Machine Learning (ML) a um aplicativo de realidade misturada usando Azure Machine Learning Studio.

*Azure Machine Learning Studio* é um serviço da Microsoft, que fornece aos desenvolvedores um grande número de algoritmos de aprendizado de máquina, que podem ajudar com a entrada, a saída, a preparação e a visualização de dados. A partir desses componentes, é possível desenvolver um experimento de análise preditiva, iterar sobre ele e usá-lo para treinar seu modelo. Após o treinamento, você pode tornar seu modelo operacional na nuvem do Azure, para que ele possa pontuar novos dados. Para obter mais informações, visite a [página Azure Machine Learning Studio](https://azure.microsoft.com/services/machine-learning-studio/).

Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada e aprenderá como fazer o seguinte:

1.  Forneça uma tabela de dados de vendas para o portal de *Azure Machine Learning Studio* e crie um algoritmo para prever as vendas futuras de itens populares.
2.  Crie um **projeto do Unity**, que pode receber e interpretar dados de previsão do serviço ml.
3.  Exiba os dados do predicação visualmente no **projeto do Unity**, por meio do fornecimento dos itens de vendas mais populares, em uma prateleira.

Em seu aplicativo, cabe a você como você integrará os resultados com seu design. Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity. É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.

Este curso é um tutorial independente, que não envolve diretamente nenhum outro laboratório de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Sr e Azure 307: aprendizado de máquina</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Embora este curso se concentre principalmente em fones de ouvido (VR) de realidade mista do Windows, você também pode aplicar o que aprende neste curso ao Microsoft HoloLens. Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte ao HoloLens. Ao usar o HoloLens, você pode notar um eco durante a captura de voz.

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018). Você está livre para usar o software mais recente, conforme listado no [artigo instalar as ferramentas](install-the-tools.md), embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)
- [Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md#installation-checklist)
- [O SDK do Windows 10 mais recente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado
- Acesso à Internet para a instalação do Azure e recuperação de dados de ML

## <a name="before-you-start"></a>Antes de começar

Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação). 

## <a name="chapter-1---azure-storage-account-setup"></a>Capítulo 1-configuração da conta de armazenamento do Azure

Para usar a API do Azure Translator, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.
1.  Faça logon no [portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  Depois de fazer logon, clique em **contas de armazenamento** no menu à esquerda.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.

3.  Na guia **contas de armazenamento** , clique em **Adicionar**.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-2.png)

4.  No painel **criar conta de armazenamento** :

    1.  Insira um **nome** para sua conta, lembre-se de que esse campo aceita apenas números e letras minúsculas.
    2.  Para **modelo de implantação,** selecione **Gerenciador de recursos**.
    3.  Para **tipo de conta**, selecione **armazenamento (uso geral v1)** .
    4.  Para **desempenho**, selecione **padrão**.
    5.  Para **replicação** **, selecione leitura-acesso-armazenamento com REDUNDÂNCIA geográfica (ra-grs)** .
    6.  Deixe a **transferência segura necessária** como **desabilitada**.
    7.  Selecione uma **assinatura**.
    4. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).

        > Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).
    
    5.  Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões.

5.  Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-3.png)

6.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

7.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![Configuração da conta de armazenamento do Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>Capítulo 2-o Azure Machine Learning Studio

Para usar o *Azure Machine Learning*, você precisará configurar uma instância do serviço de Machine Learning a ser disponibilizada para seu aplicativo.

1.  No portal do Azure, clique em **novo** no canto superior esquerdo e procure **Machine Learning Studio espaço de trabalho**, pressione **Enter**.

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  A nova página fornecerá uma descrição do serviço de **espaço de trabalho Machine Learning Studio** . Na parte inferior esquerda desse prompt, clique no botão **criar** para criar uma associação com esse serviço.

3.  Depois de clicar em **criar**, um painel será exibido onde você precisa fornecer alguns detalhes sobre o novo serviço de **Machine Learning Studio**:

    1.  Insira o **nome do espaço de trabalho** desejado para esta instância de serviço.

    2.  Selecione uma **assinatura**.

    3. Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum). 

        > Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Determine o **local** do seu grupo de recursos (se você estiver criando um novo grupo de recursos). O local ideal seria na região em que o aplicativo seria executado. Alguns ativos do Azure só estão disponíveis em determinadas regiões. Você deve usar o mesmo grupo de recursos que usou para criar o armazenamento do Azure no capítulo anterior.

    5.  Para a seção **conta de armazenamento** , clique em **usar existente**e, em seguida, clique no menu suspenso e, a partir daí, clique na **conta de armazenamento** que você criou no último capítulo.

    6.  Selecione o **tipo de preço do espaço de trabalho** apropriado para você, no menu suspenso.

    7.  Na seção **plano de serviço Web** , clique em **criar** **novo e** Insira um nome para ele no campo de texto.

    8.  Na seção tipo de preço do **plano de serviço Web** , selecione o tipo de preço de sua escolha. Um nível de teste de desenvolvimento chamado **DEVTEST Standard** deve estar disponível para você sem custos.

    9.  Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.

    10. Clique em **Criar**.

        ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

5.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  Clique na notificação para explorar sua nova instância de serviço.

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.

8.  Na página exibida, na seção **links adicionais** , clique em **Iniciar Machine Learning Studio**, que direcionará o navegador para o portal do **Machine Learning Studio** .

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  Use o botão **entrar** , na parte superior direita ou no centro, para fazer logon em seu Machine Learning Studio.

    ![O Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>Capítulo 3-a configuração do Machine Learning Studio: DataSet

Uma das maneiras de Machine Learning algoritmos funciona ao analisar os dados existentes e, em seguida, tentar prever os resultados futuros com base no conjunto de dados existente. Isso geralmente significa que quanto mais dados existentes você tiver, melhor será o algoritmo prevendo resultados futuros.

Uma tabela de exemplo é fornecida para você, para este curso, chamado [ProductsTableCSV e pode ser baixado aqui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).

> [!IMPORTANT]
> O arquivo. zip acima contém o **ProductsTableCSV** e o **. unitypackage**, que serão necessários no [capítulo 6](#chapter-6---importing-the-mlproducts-unity-package). Esse pacote também é fornecido dentro desse capítulo, embora separado para o arquivo CSV.

Este conjunto de dados de exemplo contém um registro dos objetos mais vendidos a cada hora de cada dia do ano de 2017.
        
![A configuração do Machine Learning Studio: DataSet](images/AzureLabs-Lab7-11.png)

Por exemplo, no dia 1 de 2017, às às 13:00 (hora 13), o item de vendas melhores era Salt e molho.

Esta tabela de exemplo contém 9998 entradas.

1.  Volte para o portal de **Machine Learning Studio** e adicione essa tabela como um **conjunto** de uma para seu ml. Para fazer isso, clique no botão **+ novo** no canto inferior esquerdo da tela.

    ![A configuração do Machine Learning Studio: DataSet](images/AzureLabs-Lab7-12.png)

2.  Uma seção será exibida na parte inferior e, dentro dela, há painel de navegação à esquerda. Clique em **conjunto**de um e, à direita disso, em **arquivo local**.

    ![A configuração do Machine Learning Studio: DataSet](images/AzureLabs-Lab7-13.png)

3.  Carregue o novo **conjunto** de novos, seguindo estas etapas:

    1. A janela de carregamento será exibida, onde você poderá **procurar** o novo conjunto de um disco rígido.

        ![A configuração do Machine Learning Studio: DataSet](images/AzureLabs-Lab7-14.png)

    2.  Depois de selecionado e de volta à janela carregar, deixe a caixa de seleção sem marcação.

    3.  No campo de texto abaixo, insira **ProductsTableCSV. csv** como o nome do conjunto de os (embora deva ser adicionado automaticamente).

    4.  Usando o menu suspenso para **tipo**, selecione **arquivo CSV genérico com um cabeçalho (. csv)** .

    5.  Pressione a escala no canto inferior direito da janela carregar e seu **conjunto** de resultados será carregado.

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>Capítulo 4-o Machine Learning Studio: o experimento

Antes de criar seu sistema de aprendizado de máquina, você precisará criar um experimento para validar sua teoria sobre seus dados. Com os resultados, você saberá se precisa de mais dados ou se não há nenhuma correlação entre os dados e um resultado possível.

Para começar a criar um experimento:

1.  Clique novamente no botão **+ novo** na parte inferior esquerda da página e **, em seguida** , clique em experimento > **experimento em branco**.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-15.png)

2.  Uma nova página será exibida com um experimento em branco:

3.  No painel à esquerda, expanda os **conjuntos** de itens salvos > **meus conjuntos** de os e arraste o **ProductsTableCSV** para a **tela do experimento**.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-16.png)

4.  No painel à esquerda, expanda **transformação de dados** > **amostra e divisão**. Em seguida, arraste o item **dividir dados** para a **tela do experimento**. O item dividir dados dividirá o conjunto de dados em duas partes. Uma parte que será usada para treinar o algoritmo de aprendizado de máquina. A segunda parte será usada para avaliar a precisão do algoritmo gerado.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-17.png)

5.  No painel direito (enquanto o item dividir dados na tela está selecionado), edite a **fração de linhas no primeiro conjunto** de dado de saída para **0,7**. Isso dividirá os dados em duas partes, a primeira parte será de 70% dos dados e a segunda parte será os 30% restantes. Para garantir que os dados sejam divididos aleatoriamente, verifique se a caixa de seleção **divisão aleatória** permanece marcada.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-18.png)

6.  Arraste uma conexão da base do item **ProductsTableCSV** na tela para a parte superior do item dividir dados. Isso irá conectar os itens e enviar a saída do conjunto de dados **ProductsTableCSV** (os dados) para a entrada Split Data.  

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-19.png)

7.  No painel **experimentos** no lado esquerdo, expanda **Machine Learning** > **Train**. Arraste o item **modelo de treinamento** para fora até a tela do experimento. Sua tela deve ter a seguinte aparência.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-20.png)

8.  Na ***parte inferior esquerda*** do item **dividir dados** , arraste uma conexão para a **parte superior direita** do item de **modelo de treinamento** . A primeira 70% de divisão do conjunto de um será usada pelo modelo de treinamento para treinar o algoritmo.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-21.png)

9.  Selecione o item **treinar modelo** na tela e, no painel **Propriedades** (no lado direito da janela do navegador), clique no botão **Iniciar seletor de coluna** .

10. Na caixa de texto, digite **produto** e pressione **Enter**, o *produto* será definido como uma coluna para treinar previsões. Depois disso, clique no **tique** no canto inferior direito para fechar a caixa de diálogo de seleção.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-22.png)

11. Você vai treinar um algoritmo de **regressão logística multiclasse** para prever o **produto** mais vendido com base na hora do dia e na data. Está além do escopo deste documento para explicar os detalhes dos diferentes algoritmos fornecidos pelo Azure Machine Learning Studio, porém, você pode saber mais sobre a folha de consulta do [algoritmo de Machine Learning](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)

12. No painel itens de experimento à esquerda, expanda **Machine Learning** > **inicializar o modelo** > **classificação**e arraste o item **regressão logística multiclasse** para a tela do experimento.

13. Conecte a saída, da parte inferior da **regressão logística multiclasse**, à entrada superior esquerda do item de modelo de **treinamento** .

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-23.png)

14. Na lista de itens de teste no painel à esquerda, expanda **Machine Learning** > **Pontuação**e arraste o item de **modelo de Pontuação** para a tela.

15. Conecte a saída, na parte inferior do **modelo de treinamento**, à entrada superior esquerda do **modelo de Pontuação**.

16. Conecte a saída inferior direita de **dividir dados**à entrada superior direita do item de **modelo de Pontuação** .

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-24.png)

17. Na lista de itens de **teste** no painel à esquerda, expanda **Machine Learning** > **avaliar**e arraste o item **modelo de avaliação** para a tela.

18. Conecte a saída do **modelo de Pontuação** à entrada superior esquerda do **modelo de avaliação**.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-25.png)

19. Você criou seu primeiro experimento de Machine Learning. Agora você pode salvar e executar o experimento. No menu na parte inferior da página, clique no botão **salvar** para salvar o experimento e, em seguida, clique em **executar** para iniciar o experimento.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-26.png)

20. Você pode ver o **status** do experimento no canto superior direito da tela. Aguarde alguns instantes até que o experimento seja concluído.

    > Se você tiver um grande conjunto de grandes (mundo real), é provável que o experimento possa levar horas para ser executado.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-27.png)

21. Clique com o botão direito do mouse no item **modelo** de avaliação na tela e, no menu de contexto, passe o mouse sobre **os resultados da avaliação**e selecione **Visualizar**.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-28.png)

22. Os resultados da avaliação serão exibidos mostrando as exibições previstas em relação aos resultados reais. Isso usa 30% do conjunto de um original, que foi dividido anteriormente, para avaliar o modelo. Você pode ver que os resultados não são ótimos, idealmente você teria o número mais alto em cada linha ser o item realçado nas colunas.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-29.png)

23. Feche os **resultados**.

24. Para usar o modelo de Machine Learning treinado recentemente, você precisa expô-lo como um **serviço Web**. Para fazer isso, clique no item de menu **configurar serviço Web** no menu na parte inferior da página e clique em **serviço Web de previsão**.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-30.png)

25. Uma nova guia será criada e o modelo de treinamento mesclado para criar o novo serviço Web. 

26. No menu na parte inferior da página, clique em **salvar**e em **executar**. Você verá o status atualizado no canto superior direito da tela do experimento.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-31.png)

27. Quando a execução for concluída, um botão **implantar serviço Web** aparecerá na parte inferior da página. Você está pronto para implantar o serviço Web. Clique em **implantar serviço Web** (clássico) no menu na parte inferior da página.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-32.png)

    > O navegador pode solicitar a permissão de um pop-up, que você deve **permitir**, embora seja necessário pressionar **implantar serviço Web** novamente, se a página implantar não for mostrada. 

28. Depois que o experimento tiver sido criado, você será redirecionado para uma página de **painel** onde você terá sua **chave de API** exibida. Copie-o em um bloco de notas por enquanto, você precisará dele em seu código em breve. Depois de anotar sua chave de API, clique no botão **solicitação/resposta** na seção **ponto de extremidade padrão** abaixo da chave.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > Se você clicar em testar nesta página, poderá inserir dados de entrada e exibir a saída. Insira o **dia** e a **hora**. Deixe a entrada do **produto** em branco. Em seguida, clique no botão **confirmar** . A saída na parte inferior da página mostrará o JSON que representa a probabilidade de cada produto ser a opção.

29. Uma nova página da Web será aberta, exibindo as instruções e alguns exemplos sobre a estrutura de solicitação exigida pelo Machine Learning Studio. Copie o **URI de solicitação** exibido nesta página, no bloco de notas.

    ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-34.png)

Agora você criou um sistema de aprendizado de máquina que fornece o produto mais provável para ser vendido com base nos dados de compra históricos, correlacionados com a hora do dia e dia do ano.

Para chamar o serviço Web, você precisará da URL para o ponto de extremidade de serviço e uma chave de API para o serviço. Clique na guia **consumir** , no menu superior.

A página informações de **consumo** exibirá as informações necessárias para chamar o serviço Web do seu código. Faça uma cópia da **chave primária** e da URL da **solicitação-resposta** . Você precisará deles no próximo capítulo.

## <a name="chapter-5---setting-up-the-unity-project"></a>Capítulo 5-Configurando o projeto do Unity

Configure e teste seu headset de imersão de realidade misturada.

> [!NOTE]
>  Você **não** precisará de controladores de animação para este curso. Se você precisar de suporte para configurar o headset de imersão, clique [aqui](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra o **Unity** e crie um novo projeto de Unity chamado **Mr\_MachineLearning.** Verifique se o tipo de projeto está definido como **3D**.

2.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar** **preferências** de > e, em seguida, na nova janela, navegue até **Ferramentas externas**. Altere o **Editor de script externo** para o **Visual Studio 2017**. Feche a janela **preferências** .

3.  Em seguida, vá para **arquivo** > **configurações de Build** e alterne a plataforma para **plataforma universal do Windows**clicando no botão ***alternar plataforma*** .

4.  Verifique também se:

    1.  O **dispositivo de destino** está definido como **qualquer dispositivo**.

        > Para o Microsoft HoloLens, defina o **dispositivo de destino** como *HoloLens*.

    2.  O **tipo de compilação** está definido como **D3D**.

    3.  O **SDK** está definido para o **mais recente instalado**.

    4.  A **versão do Visual Studio** está definida como **mais recente instalada**.

    5.  **Compilar e executar** é definido como **computador local**.

    6.  Não se preocupe com a configuração de **cenas** no momento, pois elas são fornecidas mais tarde.

    7.  As configurações restantes devem ser deixadas como padrão por enquanto.

        ![Configurando o projeto do Unity](images/AzureLabs-Lab7-35.png)

5.  Na janela **configurações de compilação** , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o **Inspetor** está localizado. 

6. Nesse painel, algumas configurações precisam ser verificadas:

    1.  Na guia **outras configurações** :

        1.  A **versão de tempo de execução** de **script** deve ser **experimental** (.NET 4,6 equivalente)

        2. O **back-end de script** deve ser ***.net***

        3. O **nível de compatibilidade da API** deve ser **.NET 4,6**

            ![Configurando o projeto do Unity](images/AzureLabs-Lab7-36.png)

    2.  Na guia **configurações de publicação** , em **recursos**, marque:

        - **InternetClient**

            ![Configurando o projeto do Unity](images/AzureLabs-Lab7-37.png)

    3.  Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o **SDK do Windows Mixed Reality** foi adicionado

        ![Configurando o projeto do Unity](images/AzureLabs-Lab7-38.png)

    

6.  De volta **às configurações de Build** , os projetos do  *C# Unity* não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste. 

7.  Feche a janela configurações de compilação.

8.  Salve seu projeto (**arquivo > salvar projeto**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>Capítulo 6-importando o pacote do MLProducts Unity

Para este curso, você precisará baixar um pacote de ativos do Unity chamado [**Azure-Mr-307. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage). Esse pacote vem completo com uma cena, com todos os objetos criados, para que você possa se concentrar em fazê-lo funcionar. O script **ShelfKeeper** é fornecido, embora só mantenha as variáveis públicas, para fins de estrutura de configuração de cena. Você precisará fazer todas as outras seções. 

Para importar este pacote:

1.  Com o painel do Unity na frente, clique em **ativos** no menu na parte superior da tela e, em seguida, clique em **Importar pacote, pacote personalizado**.

    ![Importando o pacote do MLProducts Unity](images/AzureLabs-Lab7-39.png)

2.  Use o seletor de arquivos para selecionar o pacote **Azure-Mr-307. unitypackage** e clique em **abrir**.

3.  Uma lista de componentes para este ativo será exibida para você. Confirme a importação clicando em **importar**.

    ![Importando o pacote do MLProducts Unity](images/AzureLabs-Lab7-40.png)

4.  Depois de concluir a importação, você observará que algumas novas pastas apareciam no painel de **projeto**do Unity. Esses são os modelos 3D e os respectivos materiais que fazem parte da cena previamente realizada na qual você trabalhará. Você escreverá a maioria do código neste curso.

    ![Importando o pacote do MLProducts Unity](images/AzureLabs-Lab7-41.png)

5.  Na pasta do **painel Projeto** , clique na pasta **cenas** e clique duas vezes na cena dentro (chamada de **MR_MachineLearningScene**). A cena será aberta (consulte a imagem abaixo). Se os losangos vermelhos estiverem ausentes, basta clicar no botão **utensílios** , na parte superior direita do **painel Game**.

    ![Importando o pacote do MLProducts Unity](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>Capítulo 7-verificando as DLLs no Unity

Para aproveitar o uso de bibliotecas JSON (usadas para serialização e desserialização), uma DLL Newtonsoft foi implementada com o pacote que você colocou. A biblioteca deve ter a configuração correta, embora vale a pena verificar (especialmente se você estiver tendo problemas com o código não funcionando). 

Para fazer isso:

-  Clique com o botão esquerdo do mouse no arquivo Newtonsoft dentro da pasta plugins e examine o **painel Inspetor**. Verifique se **todas as plataformas** estão marcadas. Vá para a **guia UWP** e verifique também se **não processar** está marcado.

    ![Importando as DLLs no Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>Capítulo 8-criar a classe ShelfKeeper

A classe **ShelfKeeper** hospeda métodos que controlam a interface do usuário e os produtos gerados na cena.

Como parte do pacote importado, você receberá essa classe, embora ela esteja incompleta. Agora é hora de concluir essa classe:

1.  Clique duas vezes no script **ShelfKeeper** , na pasta **scripts** , para abri-lo com o **Visual Studio 2017**.

2.  Substitua todo o código existente no script pelo código a seguir, que define a data e a hora e tem um método para mostrar um produto.

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

4.  De volta ao editor do Unity, verifique se a classe **ShelfKeeper** é semelhante à seguinte:

    ![Criar a classe ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > Se o seu script não tiver os destinos de referência (ou seja, *Data (malha de texto)* ), basta arrastar os objetos correspondentes do **painel hierarquia**para os campos de destino. Veja abaixo a explicação, se necessário:
    > 
    > 1.  Abra a matriz de **ponto de geração** dentro do script do componente **ShelfKeeper** clicando nela com o botão esquerdo. Uma subseção será exibida chamada de **tamanho**, o que indica o tamanho da matriz. Digite **3** na caixa de texto ao lado de **tamanho** e pressione **Enter**, e três slots serão criados abaixo.
    > 2. Na **hierarquia** , expanda o objeto de **exibição de hora** (clicando com o botão esquerdo do mouse na seta ao lado dele). Em seguida, clique na ***câmera principal*** de dentro da **hierarquia**, para que o **Inspetor** mostre suas informações.
    > 3. Selecione a **câmera principal** no **painel hierarquia**. Arraste os objetos de **Data** e **hora** do **painel hierarquia** para os slots de texto de **Data** e **hora** dentro do **Inspetor** da **câmera principal** no componente **ShelfKeeper** .
    > 4. Arraste os **pontos de geração** do **painel hierarquia** (abaixo do objeto *prateleira* ) para os **três** destinos de referência de **elemento** abaixo da matriz de **ponto de geração** , conforme mostrado na imagem.
    > 
    >     ![Criar a classe ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>Capítulo 9-criar a classe ProductPrediction

A próxima classe que você vai criar é a classe **ProductPrediction** .

Essa classe é responsável por:

-   Consultando a instância do **serviço de Machine Learning** , fornecendo a data e hora atuais.

-   Desserializando a resposta JSON em dados utilizáveis.

-   Interpretação dos dados, recuperação dos 3 produtos recomendados.

-   Chamar os métodos da classe **ShelfKeeper** para exibir os dados na cena.

Para criar esta classe:

1.  Vá para a pasta **scripts** , no **painel Projeto**.

2.  Clique com o botão direito do mouse dentro da pasta, **crie** >  **C# script**. Chame o script **ProductPrediction**.

3.  Clique duas vezes no novo script **ProductPrediction** para abri-lo com o **Visual Studio 2017**.

4.  Se a caixa de diálogo **modificação de arquivo detectada** for exibida, clique em ***recarregar solução**.

5.  Adicione os seguintes namespaces à parte superior da classe ProductPrediction:

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

6.  Dentro da classe **ProductPrediction** , insira os dois objetos a seguir que são compostos de várias classes aninhadas. Essas classes são usadas para serializar e desserializar o JSON para o serviço de Machine Learning.

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

7.  Em seguida, adicione as seguintes variáveis acima do código anterior (para que o código relacionado ao JSON esteja na parte inferior do script, abaixo de todos os demais códigos e do caminho):

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
    > Certifique-se de inserir a **chave primária** e o **ponto de extremidade de solicitação-resposta**, no portal Machine Learning, nas variáveis aqui. As imagens abaixo mostram onde você teria levado a chave e o ponto de extremidade. 
    >  
    > ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![O Machine Learning Studio: o experimento](images/AzureLabs-Lab7-53-2.png)

8.  Insira este código dentro do método **Start ()** . O método **Start ()** é chamado quando a classe é inicializada:

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

9.  Este é o método que coleta a data e a hora do Windows e a converte em um formato que o experimento de Machine Learning pode usar para comparar com os dados armazenados na tabela.

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

10. Você pode **excluir** o método **Update ()** , pois essa classe não o usará.

11. Adicione o seguinte método que irá comunicar a data e hora atuais para o ponto de extremidade Machine Learning e receber uma resposta no formato JSON.

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

            // Serialize the request
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

12. Adicione o método a seguir, que é responsável pela desserialização da resposta JSON e pela comunicação do resultado da desserialização para a classe **ShelfKeeper** . Esse resultado será o nome dos três itens previstos para vender o máximo em data e hora atuais. Insira o código abaixo na classe **ProductPrediction** , abaixo do método anterior.

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

13. Salve o **Visual Studio** e vá de volta para o **Unity**.

14. Arraste o script da classe **ProductPrediction** da pasta **script** para o objeto **principal da câmera** .

15. Salve seu **arquivo** de cena e de projeto > **salvar a cena/arquivo** > **salvar projeto**.

## <a name="chapter-10---build-the-uwp-solution"></a>Capítulo 10 – criar a solução UWP

Agora é hora de criar seu projeto como uma solução UWP, para que ele possa ser executado como um aplicativo autônomo.

Para compilar:

1.  Salve a cena atual clicando em **arquivo** > **salvar cenas**.

2.  Vá para **arquivo** > **configurações de Build**

3.  Marque a caixa denominada **projetos do Unity C#**  (isso é importante porque permitirá que você edite as classes após a conclusão da compilação).

4.  Clique em **Adicionar e abrir cenas**,

5.  Clique em **Compilar**.

    ![Compilar a solução UWP](images/AzureLabs-Lab7-54.png)

6.  Você será solicitado a selecionar a pasta na qual deseja criar a solução.

7.  Crie uma pasta **Builds** e dentro dessa pasta crie outra pasta com um nome apropriado de sua escolha.

8.  Clique na nova pasta e, em seguida, clique em **Selecionar pasta**para iniciar a compilação nesse local.

    ![Compilar a solução UWP](images/AzureLabs-Lab7-55.png)

    ![Compilar a solução UWP](images/AzureLabs-Lab7-56.png)

9.  Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do **Explorador de arquivos** no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).

## <a name="chapter-11---deploy-your-application"></a>Capítulo 11 – implantar seu aplicativo

Para implantar seu aplicativo:

1.  Navegue até sua nova compilação do Unity (a pasta do **aplicativo** ) e abra o arquivo de solução com o **Visual Studio**.

2.  Com o Visual Studio aberto, você precisa restaurar os pacotes NuGet, o que pode ser feito clicando com o botão direito do mouse em sua solução de MachineLearningLab_Build, na Gerenciador de Soluções (localizada à direita do Visual Studio) e clicando em restaurar pacotes NuGet:

    ![Adicionar pacotes NuGet](images/AzureLabs-Lab7-57.png)

3.  Na configuração da solução, selecione **depurar**.

4.  Na plataforma da solução, selecione **x86**, **computador local**. 

    > Para o Microsoft HoloLens, você pode achar mais fácil definir isso como *computador remoto*, para que você não esteja vinculado ao seu computador. No entanto, também será necessário fazer o seguinte:
    > - Conheça o **endereço IP** do seu HoloLens, que pode ser encontrado dentro das *configurações > rede & Internet > Wi-Fi > opções avançadas*; o IPv4 é o endereço que você deve usar. 
    > - Verificar se o modo **de** **desenvolvedor** está ativado; encontrado em *configurações > atualização & > de segurança para desenvolvedores*.

    ![Adicionar pacotes NuGet](images/AzureLabs-Lab7-58.png)

5.  Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu PC.

6.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.

Ao executar o aplicativo de realidade misturada, você verá o banco que foi configurado em sua cena do Unity e a partir da inicialização, os dados configurados no Azure serão buscados. Os dados serão desserializados em seu aplicativo, e os três resultados principais para sua data e hora atuais serão fornecidos visualmente, como três modelos no banco.


## <a name="your-finished-machine-learning-application"></a>Seu aplicativo Machine Learning concluído
 
Parabéns, você criou um aplicativo de realidade misturada que aproveita as Azure Machine Learning para fazer previsões de dados e exibi-las em sua cena.

![Adicionar pacotes NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>Utilização

**Exercício 1**

Experimente a ordem de classificação do seu aplicativo e faça com que as três previsões inferiores apareçam na prateleira, pois esses dados seriam potencialmente úteis também.

**Exercício 2**

Usando **tabelas do Azure** , preencha uma nova tabela com informações de clima e crie um novo experimento usando os dados.
