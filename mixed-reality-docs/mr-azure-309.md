---
title: Sr e Azure 309-Application insights
description: Conclua este curso para aprender a coletar análises sobre o comportamento do usuário em um aplicativo de realidade misturada, usando o serviço do insights Aplicativo Azure.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade mista, Academia, Unity, tutorial, API, Application insights, hololens, imersão, VR
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694565"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br> 

# <a name="mr-and-azure-309-application-insights"></a>Sr e Azure 309: Application insights

![início do produto final](images/AzureLabs-Lab309-00.png)

Neste curso, você aprenderá a adicionar recursos de Application Insights a um aplicativo de realidade misturada, usando a API do Aplicativo Azure insights para coletar análises sobre o comportamento do usuário.

Application Insights é um serviço da Microsoft, permitindo aos desenvolvedores coletar análises de seus aplicativos e gerenciá-los de um portal fácil de usar. A análise pode ser qualquer coisa, desde o desempenho até as informações personalizadas que você gostaria de coletar. Para obter mais informações, visite a [página Application insights](https://azure.microsoft.com/services/application-insights/).

Após concluir este curso, você terá um aplicativo de headset de imersão de realidade misturada que poderá fazer o seguinte:

1.  Permitir que o usuário olhar e mova-se em uma cena.
2.  Dispare o envio de análises para o *serviço de Application insights*, por meio do uso de olhar e proximidade para objetos em cena.
3.  O aplicativo também chamará o serviço, buscando informações sobre qual objeto foi mais abordado pelo usuário, nas últimas 24 horas. Esse objeto alterará sua cor para verde.

Este curso ensinará a você como obter os resultados do serviço de Application Insights em um aplicativo de exemplo baseado em Unity. Será necessário aplicar esses conceitos a um aplicativo personalizado que você possa estar criando.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Sr e Azure 309: Application insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Embora este curso se concentre principalmente em fones de ouvido (VR) de realidade mista do Windows, você também pode aplicar o que aprende neste curso ao Microsoft HoloLens. Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte ao HoloLens. Ao usar o HoloLens, você pode notar um eco durante a captura de voz.

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Este tutorial foi desenvolvido para desenvolvedores que têm experiência básica com o Unity C#e o. Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (julho de 2018). Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](install-the-tools.md) , embora não seja recomendável que as informações neste curso correspondam perfeitamente ao que você encontrará no software mais recente do que o que está listado abaixo.

Recomendamos o seguinte hardware e software para este curso:

- Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)
- [Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado](install-the-tools.md#installation-checklist)
- [O SDK do Windows 10 mais recente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Um [fone de ouvido (VR) de realidade mista do Windows](immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](hololens-hardware-details.md) modo de desenvolvedor habilitado
- Um conjunto de fones de ouvido com um microfone interno (se o headset não tiver um MIC interno e alto-falantes)
- Acesso à Internet para a instalação do Azure e recuperação de dados de Application Insights

## <a name="before-you-start"></a>Antes de começar

Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).

> [!WARNING] 
> Lembre-se de que os dados enviados para *Application insights* leva tempo, portanto, seja paciente. Se você quiser verificar se o serviço recebeu seus dados, confira o [capítulo 14](#chapter-14---the-application-insights-service-portal), que lhe mostrará como navegar no Portal.

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1-o portal do Azure

Para usar *Application insights*, será necessário criar e configurar um serviço de *Application insights* no portal do Azure.

1.  Faça logon no [portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, será necessário criar uma. Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.

2.  Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure *Application insights*e clique em **Enter**.

    > [!NOTE]
    > A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.

    ![Portal do Azure](images/AzureLabs-Lab309-01.png)

3.  A nova página à direita fornecerá uma descrição do serviço de *informações de aplicativo Azure* . Na parte inferior esquerda desta página, selecione o botão **criar** para criar uma associação com esse serviço.

    ![Portal do Azure](images/AzureLabs-Lab309-02.png)

4.  Depois de clicar em **criar**:

    1.  Insira o **nome** desejado para esta instância de serviço.

    2.  Como **tipo de aplicativo**, selecione **geral**.

    3.  Selecione uma **assinatura**apropriada.

    4.  Escolha um **grupo de recursos** ou crie um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses cursos) em um grupo de recursos comum).

        > Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5.  Selecione um **local**.

    6.  Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.

    7.  Selecione **Criar**.

        ![Portal do Azure](images/AzureLabs-Lab309-03.png)

5.  Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal assim que a instância do serviço for criada.

    ![Portal do Azure](images/AzureLabs-Lab309-04.png)

7.  Clique nas notificações para explorar sua nova instância de serviço.

    ![Portal do Azure](images/AzureLabs-Lab309-05.png)

8.  Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço. Você será levado para sua nova instância do *serviço Application insights* .

    ![Portal do Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Mantenha essa página da Web aberta e fácil de acessar, você voltará aqui para ver os dados coletados.

    > [!IMPORTANT]
    > Para implementar Application Insights, você precisará usar três (3) valores específicos: **Chave**de instrumentação, **ID do aplicativo**e chave de **API**. Abaixo, você verá como recuperar esses valores do seu serviço. Lembre-se de anotar esses valores em uma página de *bloco de notas* em branco, pois você os usará em breve em seu código.

9.  Para localizar a **chave**de instrumentação, você precisará rolar a lista de funções de serviço e clicar em **Propriedades**, a guia exibida revelará a **chave de serviço**.

    ![Portal do Azure](images/AzureLabs-Lab309-07.png)

10. Um pouco abaixo **das propriedades**, você encontrará o **acesso à API**, no qual você precisa clicar. O painel à direita fornecerá a **ID do aplicativo** do seu aplicativo.

    ![Portal do Azure](images/AzureLabs-Lab309-08.png)

11. Com o painel **ID do aplicativo** ainda aberto, clique em **criar chave de API**, que abrirá o painel *criar chave de API* .

    ![Portal do Azure](images/AzureLabs-Lab309-09.png)

12. No painel abrir a *chave de API criar* agora, digite uma descrição e **marque as três caixas**.

13. Clique em **gerar chave**. Sua **chave de API** será criada e exibida. 

    ![Portal do Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Essa é a única vez que a sua **chave de serviço** será exibida, portanto, certifique-se de fazer uma cópia dela agora.

## <a name="chapter-2---set-up-the-unity-project"></a>Capítulo 2 – configurar o projeto do Unity

A seguir está uma configuração típica para o desenvolvimento com a realidade misturada e, como tal, é um bom modelo para outros projetos.

1.  Abra o *Unity* e clique em **novo**.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-11.png)

2.  Agora, você precisará fornecer um nome de projeto do Unity, inserir o **Sr\_Application\_insights do Azure\_** . Verifique se o *modelo* está definido como **3D**. Defina o *local* como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-12.png)

3.  Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**. Vá para **Editar \> preferências** e, em seguida, na janela novo, navegue até **Ferramentas externas**. Altere o **Editor de script externo** para o **Visual Studio 2017**. Feche a janela **preferências** .

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-13.png)

4.  Em seguida, vá **para \> arquivo configurações de compilação** e alterne a plataforma para **plataforma universal do Windows**, clicando no botão **alternar plataforma** .

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-14.png)

5.  Vá para **arquivo \> configurações de compilação** e verifique se:

    1.  O **dispositivo de destino** está definido para **qualquer dispositivo**

        > Para o Microsoft HoloLens, defina o **dispositivo de destino** como *HoloLens*.

    2.  O **tipo de compilação** está definido como **D3D**

    3.  O **SDK** está definido para o **mais recente instalado**

    4.  **Compilar e executar** é definido como **computador local**

    5.  Salve a cena e adicione-a à compilação.

        1.  Faça isso selecionando **Adicionar abrir cenas**. Uma janela salvar será exibida.

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-15.png)

        2. Crie uma nova pasta para isso e qualquer cena futura, clique no botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-16.png)

        3. Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo:* , digite **ApplicationInsightsScene**e clique em **salvar**.

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-17.png)

6.  As configurações restantes, em **configurações de compilação**, devem ser deixadas como padrão por enquanto.

7.  Na janela **configurações de compilação** , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o **Inspetor** está localizado.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-18.png)

8. Nesse painel, algumas configurações precisam ser verificadas:

    1.  Na guia **outras configurações** :

        1.  **Criando scripts** A **versão de tempo de execução** deve ser **Experimental (.NET 4,6 equivalente)** , o que irá disparar uma necessidade de reiniciar o editor.

        2.  O **back-end de script** deve ser **.net**

        3.  O **nível de compatibilidade da API** deve ser **.NET 4,6**

        ![Configurar o projeto do Unity](images/AzureLabs-Lab309-19.png)

    2.  Na guia **configurações de publicação** , em **recursos**, marque:

        - **InternetClient**     

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-20.png)

    3.  Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual**em escala, verifique se o SDK do **Windows Mixed Reality** foi adicionado.

        ![Configurar o projeto do Unity](images/AzureLabs-Lab309-21.png)

9.  De volta **às configurações de compilação**, os **projetos de C# Unity** não ficam mais esmaecidos; Marque a caixa de seleção ao lado deste.

10.  Feche a janela configurações de compilação.

11.  Salve sua cena e projeto (**arquivo** > **salvar cena/arquivo** > **salvar projeto**).


## <a name="chapter-3---import-the-unity-package"></a>Capítulo 3 – importar o pacote do Unity

> [!IMPORTANT]
> Se você quiser ignorar os componentes de *configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para baixar este [Azure-Mr-309. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), importe-o para seu projeto como um [**pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html). Isso também conterá as DLLs do próximo capítulo. Após a importação, continue no [**capítulo 6**](#chapter-6---create-the-applicationinsightstracker-class).

> [!IMPORTANT]
> Para usar Application Insights no Unity, você precisa importar a DLL para ela, juntamente com a DLL Newtonsoft. Atualmente, há um problema conhecido no Unity que exige que os plugins sejam reconfigurados após a importação. Essas etapas (4-7 nesta seção) não serão mais necessárias depois que o bug for resolvido.

Para importar Application Insights para seu próprio projeto, verifique se você [baixou o '. unitypackage ', que contém os plug-ins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage). Em seguida, faça o seguinte:

1.  Adicione o **. unitypackage** ao Unity usando a opção de menu **pacote \> personalizado do pacote de \> importação de ativos** .

2.  Na caixa **Importar pacote de Unity** que é exibida, verifique se tudo em (e incluindo) **plug-ins** está selecionado.

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-22.png)

3.  Clique no botão **importar** para adicionar os itens ao seu projeto.

4.  Vá para a  pasta insights em **plug-ins** na exibição do projeto e selecione os seguintes plugins *somente*:

    -   Microsoft. ApplicationInsights

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-23.png)

5.  Com este *plug-in* selecionado, verifique se **qualquer plataforma** está desmarcada e, em seguida, verifique se **WSAPlayer** também está desmarcado e clique em **aplicar**. Fazer isso é apenas para confirmar que os arquivos estão configurados corretamente.

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Marcando os plug-ins como este, os configura para serem usados apenas no editor do Unity. Há um conjunto diferente de DLLs na pasta WSA que será usado depois que o projeto for exportado do Unity.

6.  Em seguida, você precisa abrir a pasta **WSA** na pasta insights. Você verá uma cópia do mesmo arquivo que acabou de configurar. Selecione esse arquivo e, no Inspetor, verifique se **qualquer plataforma** está desmarcada e, em seguida, verifique se **somente** **WSAPlayer** está  **marcado**. Clique em **Aplicar**.

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-25.png)

7. Agora, você precisará seguir **as etapas de 4-6**, mas para os plug-ins *Newtonsoft* em vez disso. Consulte a captura de tela abaixo para saber a aparência do resultado.

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Capítulo 4-configurar os controles de câmera e de usuário

Neste capítulo, você configurará a câmera e os controles para permitir que o usuário veja e mova-se na cena.

1.  Clique com o botão direito do mouse em uma área vazia no painel hierarquia e, em seguida, em **criar** > **vazio**.

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-26.png)

2.  Renomeie o novo gameobject vazio para a **câmera pai**.

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-27.png)

3.  Clique com o botão direito do mouse em uma área vazia no painel hierarquia, depois em **objeto 3D**e, em seguida, em **esfera**.

4.  Renomeie a esfera para a **direita**.

5.  Defina a **escala de transformação** da mão direita para **0,1, 0,1, 0,1**

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-28.png)

6.  Remova o **componente colisor do Sphere** do lado direito clicando na **engrenagem** no componente colisor do *Sphere* e, em seguida, **remover componente**.

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-29.png)

7.  No painel hierarquia, arraste a **câmera principal** e os objetos **à direita** para o objeto **pai da câmera** .

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-30.png)

8.  Defina a **posição de transformação** da **câmera principal** e o objeto à **direita** como **0, 0, 0**.

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-31.png)

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Capítulo 5 – configurar os objetos na cena do Unity

Agora você vai criar algumas formas básicas para sua cena, com as quais o usuário pode interagir.

1.  Clique com o botão direito do mouse em uma área vazia no *painel hierarquia*e, em seguida, em **objeto 3D**, selecione **plano**.

2.  Defina a **posição de transformação** plano como **0,-1, 0**.

3.  Defina a **escala de transformação** do plano como **5, 1, 5**.

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-33.png)

4.  Crie um material básico para usar com o seu objeto **plano** , para que as outras formas sejam mais fáceis de ver. Navegue até o *painel do projeto*, clique com o botão direito do mouse em, em seguida, **crie**, seguido por **pasta**, para criar uma nova pasta. Nomeie os **materiais**de ti.

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-34.png) ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-35.png)

5.  Abra a pasta **materiais** , clique com o botão direito do mouse em, clique em **criar**, em **material**, para criar um novo material. Nomeie-o como **azul**.

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-36.png) ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-37.png)

6.  Com o novo material **azul** selecionado, examine o *Inspetor*e clique na janela retangular junto com **albedo**. Selecione uma cor azul (a imagem abaixo é **uma cor hexadecimal: \#3592FFFF**). Clique no botão fechar depois de escolher.

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-38.png)

7.  Arraste o novo material da pasta **materiais** para o **plano**recém-criado, dentro de sua cena (ou solte-o no objeto **plano** dentro da *hierarquia*).

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-39.png)

8.  Clique com o botão direito do mouse em uma área vazia no *painel hierarquia*e, em seguida, em **objeto 3D, cápsula**.

    -  Com a **cápsula** selecionada, altere sua  *posição* de transformação para: **-10, 1, 0**.

9.  Clique com o botão direito do mouse em uma área vazia no *painel hierarquia*e, em seguida, em **objeto 3D, cubo**.

    -  Com o **cubo** selecionado, altere sua  *posição* de transformação para: **0, 0, 10**.

10. Clique com o botão direito do mouse em uma área vazia no *painel hierarquia*e, em seguida, em **objeto 3D, esfera**.

    -  Com a **esfera** selecionada, altere sua  *posição* de transformação para: **10, 0, 0**.

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Esses valores de *posição* são *sugestões*. Você tem a liberdade de definir as posições dos objetos para o que desejar, embora seja mais fácil para o usuário do aplicativo se as distâncias dos objetos não estiverem muito longe da câmera.

11. Quando seu aplicativo está em execução, ele precisa ser capaz de identificar os objetos na cena, para conseguir isso, eles precisam ser marcados. Selecione um dos objetos e, no painel *Inspetor* , clique em **adicionar marca...** , que vai alternar o *Inspetor* com as **marcas & painel camadas** .

    ![Configurar os objetos na cena](images/AzureLabs-Lab309-41.png) do Unity![](images/AzureLabs-Lab309-42.png)

12. Clique no símbolo **+ (mais)** e digite o nome da marca como **ObjectInScene**.

    ![Configurar os objetos na cena do Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Se você usar um nome diferente para sua marca, será necessário garantir que essa alteração também tenha *DataFromAnalytics*, objecttrigger e  *olhar*, scripts mais tarde, para que seus objetos sejam encontrados e detectados dentro de sua cena.

13. Com a marca criada, agora você precisa aplicá-la a todos os três objetos. Na *hierarquia*, mantenha a tecla **Shift** pressionada e, em seguida, clique nos objetos **cápsula**, **cubo**e **esfera**, no *Inspetor*, clique no menu suspenso junto com a **marca**e, em seguida, clique no *ObjectInScene* marca que você criou.

    ![Configurar os objetos na cena](images/AzureLabs-Lab309-44.png) do Unity![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Capítulo 6-criar a classe ApplicationInsightsTracker

O primeiro script que você precisa criar é **ApplicationInsightsTracker**, que é responsável por:

1.  Criar eventos com base nas interações do usuário para enviar ao Aplicativo Azure insights.

2. Criando nomes de evento apropriados, dependendo da interação do usuário.

3. Enviando eventos para a instância do serviço de Application Insights.

Para criar esta classe:

1.  Clique com o botão direito do mouse no *painel Projeto*e **crie** > a**pasta**. Nomeie a pasta **scripts**.

    ![Criar a classe ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Criar a classe ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  Com a pasta **scripts** criada, clique duas vezes nela para abrir. Em seguida, dentro dessa pasta, clique com o botão direito do mouse em **criar**  >   **C# script**. Nomeie o script **ApplicationInsightsTracker**.

3.  Clique duas vezes no novo script **ApplicationInsightsTracker** para abri-lo com o **Visual Studio**.

4.  Atualize os namespaces na parte superior do script para que sejam os seguintes:

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  Dentro da classe, insira as seguintes variáveis:

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > Defina os valores **instrumentationKey, ApplicationId e API_Key** adequadamente, usando as *chaves de serviço* do portal do Azure, conforme mencionado no [capítulo 1](#chapter-1---the-azure-portal), etapa 9 em diante.

6.  Em seguida, adicione os métodos **Start ()** e **ativo ()** , que serão chamados quando a classe for inicializada:

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  Adicione os métodos responsáveis por enviar os eventos e as métricas registradas pelo seu aplicativo:

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-7---create-the-gaze-script"></a>Capítulo 7-criar o script olhar

O próximo script a ser criado é o script **olhar** . Esse script é responsável por criar um *Raycast* que será projetado para a frente da *câmera principal*, para detectar qual objeto o usuário está olhando. Nesse caso, o *Raycast* precisará identificar se o usuário está olhando para um objeto com a marca **ObjectInScene** e, em seguida, contar quanto tempo o usuário *gazes* nesse objeto.

1.  Clique duas vezes na pasta **scripts** para abri-la.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script **olhar**.

3.  Clique duas vezes no script para abri-lo com o Visual Studio.

4.  Substitua o código existente pelo seguinte:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  Agora, o código para os métodos **ativo ()** e **Iniciar ()** precisa ser adicionado.

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  Dentro da classe **olhar** , adicione o seguinte código no método **Update ()** para projetar um *Raycast* e detectar a visita de destino:

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  Adicione o método **ResetFocusedObject ()** para enviar dados para **Application insights** quando o usuário tiver examinado um objeto.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  Agora você concluiu o script **olhar** . Salve suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-8---create-the-objecttrigger-class"></a>Capítulo 8-criar a classe objecttrigger

O próximo script que você precisa criar é **objecttrigger**, que é responsável por:

- Adição de componentes necessários para a colisão na câmera principal.
- Detectando se a câmera está perto de um objeto marcado como **ObjectInScene**.

Para criar o script:

1.  Clique duas vezes na pasta **scripts** para abri-la.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script **loadtrigger**.

3.  Clique duas vezes no script para abri-lo com o Visual Studio. Substitua o código existente pelo seguinte:

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Capítulo 9-criar a classe DataFromAnalytics

Agora, você precisará criar o script **DataFromAnalytics** , que é responsável por:

- Buscar dados de análise sobre qual objeto foi abordado pela câmera mais.
- Usando as *chaves de serviço*, que permitem a comunicação com sua instância de serviço do aplicativo Azure insights.
- Classificação dos objetos em cena, de acordo com o qual tem a maior contagem de eventos.
- Alterar a cor do material, do objeto mais aproximado, para *verde*.

Para criar o script:

1.  Clique duas vezes na pasta **scripts** para abri-la.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script **DataFromAnalytics**.

3.  Clique duas vezes no script para abri-lo com o Visual Studio.

4.  Insira os seguintes namespaces:

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  No script, insira o seguinte:

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  Dentro da classe **DataFromAnalytics** , logo após o método **Start ()** , adicione o método a seguir chamado **FetchAnalytics ()** . Esse método é responsável por preencher a lista de pares chave-valor, com  um gameobject e um número de contagem de eventos de espaço reservado. Em seguida, ele inicializa a corotina **GetWebRequest ()** . A estrutura de consulta da chamada para *Application insights* pode ser encontrada dentro desse método também, como o ponto de extremidade da *URL de consulta* .

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  Logo abaixo do método **FetchAnalytics ()** , adicione um método chamado **GetWebRequest ()** , que retorna um *IEnumerator*. Esse método é responsável por solicitar o número de vezes que um evento, correspondente a um *gameobject*específico, foi chamado dentro de *Application insights*. Quando todas as consultas enviadas retornam, o método **DetermineWinner ()** é chamado.

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  O método Next é **DetermineWinner ()** , que classifica a lista de  pares gameobject e *int* , de acordo com a contagem de eventos mais alta. Em seguida, ele altera a cor do  material desse gameobject para *verde* (como comentários para ele com a contagem mais alta). Isso exibe uma mensagem com os resultados da análise.

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  Adicione a estrutura de classe que será usada para desserializar o objeto JSON, recebido do *Application insights*. Adicione essas classes na parte inferior do arquivo de classe **DataFromAnalytics** , **fora** da definição de classe.

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-10---create-the-movement-class"></a>Capítulo 10 – criar a classe de movimento

O script de **movimento** é o próximo script que será necessário criar. É responsável por:

- Mover a câmera principal de acordo com a direção em que a câmera está procurando.
- Adicionando todos os outros scripts a objetos de cena.

Para criar o script:

1.  Clique duas vezes na pasta **scripts** para abri-la.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie a **movimentação**do script.

3.  Clique duas vezes no script para abri-lo com o *Visual Studio*.

4.  Substitua o código existente pelo seguinte:

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  Dentro da classe de **movimento** , *abaixo* do método **Update ()** vazio, insira os seguintes métodos que permitem ao usuário usar o controlador de mão para mover no espaço virtual:

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  Adicione por último a chamada de método no método **Update ()** .

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-11---setting-up-the-scripts-references"></a>Capítulo 11-configurando as referências de scripts

Neste capítulo, você precisa posicionar o script de **movimento** no **pai da câmera** e definir seus destinos de referência. Esse script manipulará a colocação dos outros scripts onde eles precisam ser.

1.  Na pasta **scripts** do *painel Projeto*, arraste o script de **movimento** para o objeto **pai da câmera** , localizado no *painel hierarquia*.

    ![Configurando as referências de scripts na cena do Unity](images/AzureLabs-Lab309-48.png)

2.  Clique no **pai da câmera**. No *painel hierarquia*, arraste o objeto **à direita** do *painel hierarquia* para o destino de referência, **controlador**, no *painel Inspetor*. Defina a **velocidade do usuário** como **5**, conforme mostrado na imagem abaixo.

    ![Configurando as referências de scripts na cena do Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Capítulo 12-criar o projeto do Unity

Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.

1.  Navegue até **configurações de compilação**, (**configurações de compilação**de**arquivo** > ).

2.  Na janela **configurações de compilação** , clique em **Compilar**.

    ![Compilar o projeto do Unity para a solução UWP](images/AzureLabs-Lab309-50.png)

3.  Uma janela do **Explorador de arquivos** será exibida, solicitando um local para a compilação. Crie uma nova pasta (clicando em **nova pasta** no canto superior esquerdo) e nomeie-a como **Build**.

    ![Compilar o projeto do Unity para a solução UWP](images/AzureLabs-Lab309-51.png)

    1.  Abra a nova  pasta builds e crie outra pasta (usando a **nova pasta** mais uma vez) e nomeie-a como **Sr\_\_Azure Application\_insights**.

        ![Compilar o projeto do Unity para a solução UWP](images/AzureLabs-Lab309-52.png)

    2.  Com a **pasta\_Mr\_Azure\_Application** insights selecionada, clique em **Selecionar pasta**. O projeto levará um minuto ou mais para ser compilado.

4.  Após a *compilação*, o **Explorador de arquivos** aparecerá mostrando o local do novo projeto.

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a>Capítulo 13-implantar o aplicativo MR_Azure_Application_Insights em seu computador

Para implantar o **aplicativo\_de\_informações\_do aplicativo do Azure** no seu computador local:

1.  Abra o arquivo de solução do **seu\_aplicativo\_Mr\_Azure Application** insights no **Visual Studio**.

2.  Na **plataforma da solução**, selecione **x86, computador local**.

3.  Na **configuração da solução** , selecione **depurar**.

    ![Compilar o projeto do Unity para a solução UWP](images/AzureLabs-Lab309-53.png)

4.  Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo em seu computador.

5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, pronto para ser iniciado.

6. Inicie o aplicativo de realidade misturada.

7. Mova-se para a cena, abordando objetos e examinando-os, quando o *serviço do Azure* insights coletou dados de eventos suficientes, ele definirá o objeto que foi abordado o mais verde.

> [!IMPORTANT] 
> Enquanto o tempo de espera médio para os *eventos e* as métricas a serem coletados pelo serviço leva cerca de 15 minutos, em algumas ocasiões, pode levar até 1 hora.

## <a name="chapter-14---the-application-insights-service-portal"></a>Capítulo 14-o portal do serviço Application Insights

Depois de fazer roaming da cena e gazed em vários objetos, você pode ver os dados coletados no portal do *serviço de Application insights* .

1.  Volte para o portal do serviço Application Insights.

2.  Clique em *Metrics Explorer*.

    ![Examinando os dados coletados](images/AzureLabs-Lab309-54.png)

3.  Ele será aberto em uma guia que contém o grafo que representa os *eventos e* as métricas relacionados ao seu aplicativo. Conforme mencionado acima, pode levar algum tempo (até 1 hora) para que os dados sejam exibidos no grafo

    ![Examinando os dados coletados](images/AzureLabs-Lab309-55.png)

4.  Clique na *barra de eventos* no *total de eventos* por versão do aplicativo para ver uma análise detalhada dos eventos com seus nomes.

    ![Examinando os dados coletados](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Seu aplicativo de serviço Application Insights concluído

Parabéns, você criou um aplicativo de realidade misturada que aproveita o serviço de Application Insights para monitorar a atividade do usuário em seu aplicativo.

![resultado do curso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

**Exercício 1**

Tente gerar, em vez de criar manualmente, os objetos ObjectInScene e definir suas coordenadas no plano dentro de seus scripts. Dessa forma, você pode perguntar ao Azure qual era o objeto mais popular (seja de olhar ou resultados de proximidade) e gerar um *extra* desses objetos.

**Exercício 2**

Classifique seus resultados de Application Insights por tempo, para que você obtenha os dados mais relevantes e implemente esses dados confidenciais em seu aplicativo.

