---
title: MR e Azure 309 - Application insights
description: Conclua este curso para aprender a coletar análise sobre o comportamento do usuário dentro de um aplicativo de realidade misturada, usando o serviço de Insights de aplicativo do Azure.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidade mista, Azure, academy, unity, tutorial, api, insights de aplicativo, hololens, imersivo, vr
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694565"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br> 

# <a name="mr-and-azure-309-application-insights"></a>MR e o Azure 309: Insights de aplicativo

![final do produto-iniciar](images/AzureLabs-Lab309-00.png)

Neste curso, você aprenderá a adicionar recursos do Application Insights a um aplicativo de realidade misturada, usando a API do Azure Application Insights para coletar análises sobre o comportamento do usuário.

Application Insights é um serviço da Microsoft, permitindo que os desenvolvedores colete análises em seus aplicativos e gerenciá-lo de um portal fácil de usar. A análise pode ser qualquer coisa, desde desempenho a informações personalizadas que você deseja coletar. Para obter mais informações, visite o [página do Application Insights](https://azure.microsoft.com/services/application-insights/).

Com a conclusão deste curso, você terá um aplicativo de imersivo headset de realidade misturada que serão capaz de fazer o seguinte:

1.  Permitir que o usuário olhares e navegar em torno de uma cena.
2.  Disparar o envio de análise para o *serviço Application Insights*, com o uso de olhar e a proximidade com os objetos na cena.
3.  O aplicativo também chamará após o serviço, buscando informações sobre qual objeto foi atingido o máximo pelo usuário, nas últimas 24 horas. Esse objeto será alterar sua cor verde.

Este curso ensinará como obter os resultados do serviço Application Insights, em um aplicativo de exemplo com base no Unity. Ele será cabe a você aplicar esses conceitos para um aplicativo personalizado que você pode criar.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> MR e o Azure 309: Insights de aplicativo</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Enquanto este curso se concentra primariamente em fones de ouvido Windows Mixed Reality de imersão (VR), você também pode aplicar o que você aprenderá neste curso para o Microsoft HoloLens. Como acompanhar o curso, você verá notas quaisquer alterações que talvez seja necessário empregar para dar suporte ao HoloLens. Ao usar o HoloLens, você pode perceber algum eco durante a captura de voz.

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
- Um conjunto de fones de ouvido com um microfone interno (se o fone de ouvido não tem um microfone interno e alto-falantes)
- Acesso à Internet para a instalação do Azure e a recuperação de dados do Application Insights

## <a name="before-you-start"></a>Antes de começar

Para evitar tendo problemas para criar esse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou perto de raiz (caminhos de pasta longa podem causar problemas em tempo de compilação).

> [!WARNING] 
> Esteja ciente de dados que vai *Application Insights* leva tempo, portanto, seja paciente. Se você quiser verificar se o serviço recebeu os dados, fazer check-out [capítulo 14](#chapter-14---the-application-insights-service-portal), que mostra como navegar o portal.

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1 - Portal do Azure

Para usar *Application Insights*, você precisará criar e configurar um *serviço Application Insights* no portal do Azure.

1.  Faça logon na [Portal do Azure](https://portal.azure.com).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, você precisará criá-lo. Se você estiver seguindo este tutorial em uma situação de laboratório de sala de aula, pergunte o instrutor ou um dos proctors para ajudar na configuração de sua nova conta.

2.  Quando você estiver conectado, clique em **New** no canto superior esquerdo de canto e procure *Application Insights*e clique em **Enter**.

    > [!NOTE]
    > A palavra **New** foram substituídos por **criar um recurso**, nos portais mais recentes.

    ![Portal do Azure](images/AzureLabs-Lab309-01.png)

3.  A nova página à direita fornece uma descrição do *Azure Application Insights* Service. Na parte inferior esquerda desta página, selecione a **criar** botão para criar uma associação com este serviço.

    ![Portal do Azure](images/AzureLabs-Lab309-02.png)

4.  Depois de clicar em **criar**:

    1.  Inserir sua desejada **nome** para esta instância de serviço.

    2.  Como **tipo de aplicativo**, selecione **geral**.

    3.  Selecione uma opção apropriada **assinatura**.

    4.  Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).

        > Se você quiser ler mais sobre grupos de recursos do Azure, por favor [visite o artigo de grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5.  Selecione uma **local**.

    6.  Você também precisará confirmar que compreendeu os termos e condições aplicadas a esse serviço.

    7.  Selecione **Criar**.

        ![Portal do Azure](images/AzureLabs-Lab309-03.png)

5.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

6.  Uma notificação será exibida no portal depois que a instância do serviço é criada.

    ![Portal do Azure](images/AzureLabs-Lab309-04.png)

7.  Clique em notificações para explorar a nova instância do serviço.

    ![Portal do Azure](images/AzureLabs-Lab309-05.png)

8.  Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço. Você será levado para a nova *serviço Application Insights* instância.

    ![Portal do Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Mantenha essa página da web aberta e fácil de acesso, você será volte aqui frequentemente para ver os dados coletados.

    > [!IMPORTANT]
    > Para implementar o Application Insights, você precisará usar valores específicos três (3): **Chave de instrumentação**, **ID do aplicativo**, e **chave API**. Abaixo, você verá como recuperar esses valores de seu serviço. Anote esses valores em um espaço em branco *bloco de notas* página, pois você irá usá-los em breve em seu código.

9.  Para localizar o **chave de instrumentação**, você precisará rolar para baixo a lista de funções de serviço e clique em **propriedades**, a guia exibida revelará o **chave de serviço**.

    ![Portal do Azure](images/AzureLabs-Lab309-07.png)

10. Um pouco abaixo **propriedades**, você encontrará **acesso à API**, que você precisa clicar. O painel à direita fornece o **ID do aplicativo** do seu aplicativo.

    ![Portal do Azure](images/AzureLabs-Lab309-08.png)

11. Com o **ID do aplicativo** painel ainda estiver aberta, clique **criar chave de API**, que abrirá o *criar chave de API* painel.

    ![Portal do Azure](images/AzureLabs-Lab309-09.png)

12. Dentro de abrir o agora *criar chave de API* do painel, digite uma descrição, e **marque as caixas de três**.

13. Clique em **gerar chave**. Sua **chave de API** será criado e exibido. 

    ![Portal do Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Esta é a única vez sua **chave de serviço** será exibida, portanto, verifique se você fazer uma cópia dele agora.

## <a name="chapter-2---set-up-the-unity-project"></a>Capítulo 2 - configurar o projeto do Unity

A seguir é um conjunto típico backup para o desenvolvimento com a realidade misturada e como tal, é um bom modelo para outros projetos.

1.  Abra *Unity* e clique em **New**.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-11.png)

2.  Agora você precisará fornecer um nome de projeto do Unity, insira **MR\_Azure\_Application\_Insights**. Verifique se o *modelo* é definido como **3D**. Defina as *local* para algum lugar adequado para você (Lembre-se de que quanto mais próximo para diretórios raiz é melhor). Em seguida, clique em **criar projeto**.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-12.png)

3.  Com o Unity aberta, vale a pena verificar o padrão **Editor de scripts** é definido como **Visual Studio**. Vá para **edite \> preferências** e, em seguida, na nova janela, navegue até **ferramentas externas**. Alteração **Editor de Script externo** à **Visual Studio 2017**. Fechar o **preferências** janela.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-13.png)

4.  Em seguida, vá para **arquivo \> configurações de Build** e alterne a plataforma **plataforma Universal do Windows**, clicando no **alternar plataforma** botão.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-14.png)

5.  Vá para **arquivo \> configurações de Build** e certifique-se de que:

    1.  **Dispositivo de destino** é definido como **qualquer dispositivo**

        > Para o Microsoft HoloLens, defina **dispositivo de destino** à *HoloLens*.

    2.  **Tipo de compilação** é definido como **D3D**

    3.  **SDK** é definido como **mais recente instalada**

    4.  **Compilar e executar** é definido como **Máquina Local**

    5.  Salve a cena e adicioná-lo para a compilação.

        1.  Fazer isso selecionando **cenas abra Adicionar**. Salvamento janela será exibida.

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-15.png)

        2. Criar uma nova pasta para isso e qualquer cena futuras, clique o **nova pasta** botão para criar uma nova pasta, nomeie- **cenas**.

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-16.png)

        3. Abrir seu recém-criado **cenas** pasta e, em seguida, no *nome do arquivo:* campo de texto, digite **ApplicationInsightsScene**, em seguida, clique em **salvar**.

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-17.png)

6.  O restante de configurações, em **configurações de Build**, deverá ser deixado como padrão por enquanto.

7.  No **configurações de Build** janela, clique na **configurações do Player** botão, isso abrirá o painel relacionado no espaço de onde o **Inspetor** está localizado.

    ![Configurar o projeto do Unity](images/AzureLabs-Lab309-18.png)

8. Neste painel, algumas configurações precisam ser verificados:

    1.  No **outras configurações** guia:

        1.  **Criação de scripts** **versão de tempo de execução** deve ser **Experimental (equivalente ao .NET 4.6)** , que irá disparar uma necessidade de reiniciar o Editor.

        2.  **Script de back-end** deve ser **.NET**

        3.  **Nível de compatibilidade de API** deve ser **.NET 4.6**

        ![Configurar o projeto do Unity](images/AzureLabs-Lab309-19.png)

    2.  Dentro de **configurações de publicação** guia, em **recursos**, verifique:

        - **InternetClient**     

            ![Configurar o projeto do Unity](images/AzureLabs-Lab309-20.png)

    3.  Mais para baixo no painel, no **XR configurações** (encontrada abaixo **configurações de publicação**), escala **suporte de realidade Virtual**, certifique-se a **realidade mista do Windows SDK** é adicionado.

        ![Configurar o projeto do Unity](images/AzureLabs-Lab309-21.png)

9.  Volta **configurações de Build**, **Unity C# projetos** não fica acinzentado; marque a caixa de seleção ao lado disso.

10.  Feche a janela de configurações de Build.

11.  Salvar sua cena e seu projeto (**arquivo** > **salvar CENA de arquivos** > **Salvar projeto**).


## <a name="chapter-3---import-the-unity-package"></a>Capítulo 3: importar o pacote do Unity

> [!IMPORTANT]
> Se você quiser ignorar a *configurar o Unity* componentes deste curso e continuar diretamente no código, fique à vontade para baixá-lo [MR-Azure-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), importá-lo para seu projeto como um [ **Pacote personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html). Isso também irá conter as DLLs do próximo capítulo. Após a importação, continuar a partir [ **capítulo 6**](#chapter-6---create-the-applicationinsightstracker-class).

> [!IMPORTANT]
> Para usar o Application Insights dentro do Unity, você precisa importar a DLL para ele, junto com a DLL da Newtonsoft. Atualmente, há um problema conhecido no Unity que requer o plug-ins para ser reconfigurado após a importação. Estas etapas (4 a 7 desta seção) não será necessárias depois que o bug foi resolvido.

Para importar o Application Insights em seu próprio projeto, certifique-se de ter [baixado de 'unitypackage', que contém os plug-ins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage). Em seguida, faça o seguinte:

1.  Adicionar o **unitypackage** para o Unity, usando o **ativos \> Importar pacote \> pacote personalizado** opção de menu.

2.  No **Importar pacote do Unity** caixa é exibido para cima, certifique-se de tudo em (e incluindo) **plug-ins** está selecionado.

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-22.png)

3.  Clique o **importação** botão para adicionar itens ao seu projeto.

4.  Vá para o **Insights** pasta sob **plug-ins** no projeto, exibir e selecione os seguintes plug-ins *apenas*:

    -   Microsoft.ApplicationInsights

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-23.png)

5.  Com isso *plug-in* selecionado, certifique-se de que **qualquer plataforma** é **desmarcada**, em seguida, certifique-se de que **WSAPlayer** também é  **não verificado**, em seguida, clique em **aplicar**. Fazer isso é apenas para confirmar se os arquivos estão configurados corretamente.

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Marcar os plug-ins como este, configura para ser usado apenas no Editor do Unity. Há um conjunto diferente de DLLs na pasta do WSA que será usado depois que o projeto é exportado do Unity.

6.  Em seguida, você precisa abrir o **WSA** pasta, dentro de **Insights** pasta. Você verá uma cópia do mesmo arquivo que você acabou de configurar. Selecione esse arquivo e, em seguida, no Inspetor de, certifique-se de que **Any Platform** é **desmarcada**, em seguida, certifique-se de que **apenas** **WSAPlayer** é **verificado**. Clique em **Aplicar**.

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-25.png)

7. Agora você precisará seguir **as etapas 4 a 6**, mas para o *Newtonsoft* plug-ins em vez disso. Consulte a captura de tela para que o resultado deve ter aparência abaixo.

    ![Importar o pacote do Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Capítulo 4 - configurar a câmera e o usuário controles

Neste capítulo você configurará a câmera e os controles para permitir que o usuário vê e mover na cena.

1.  Clique duas vezes em uma área vazia no painel de hierarquia, em seguida, em **Create** > **vazio**.

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-26.png)

2.  Renomeie o novo GameObject vazio para **pai da câmera**.

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-27.png)

3.  Clique duas vezes em uma área vazia no painel de hierarquia, em seguida, em **objeto 3D**, em seguida, na **esfera**.

4.  Renomear a esfera **mão direita**.

5.  Defina a **transformar escala** da mão direita para **0,1, 0.1, 0,1**

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-28.png)

6.  Remover o **esfera Colisor** componente da mão direita clicando na **engrenagem** no *Colisor esfera* componente e, em seguida, **remover componente** .

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-29.png)

7.  Em arrastar o painel de hierarquia a **câmera principal** e o **mão direita** objetos para o **câmera pai** objeto.

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-30.png)

8.  Defina a **transformar posição** de ambos o **câmera principal** e o **mão direita** do objeto para **0, 0, 0**.

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-31.png)

    ![Configurar a câmera e os controles de usuário](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Capítulo 5 – configurar os objetos na cena Unity

Agora, você criará algumas formas básicas para sua cena, com a qual o usuário pode interagir.

1.  Clique com botão direito em uma área vazia na *painel de hierarquia*, em seguida, na **objeto 3D**, em seguida, selecione **plano**.

2.  Defina o plano **transformar posição** à **0, -1, 0**.

3.  Defina o plano **transformar escala** à **5, 1, 5**.

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-33.png)

4.  Criar um material básico para usar com seu **plano** objeto, de modo que as outras formas são mais fácil de ver. Navegue até sua *painel projeto*, direito do mouse em seguida **Create**, seguido por **pasta**, para criar uma nova pasta. Denomine **materiais**.

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-34.png) ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-35.png)

5.  Abra o **materiais** pasta, em seguida, clique com botão direito, clique **criar**, em seguida, **Material**, para criar um novo material. Denomine **azul**.

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-36.png) ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-37.png)

6.  Com o novo **azul** material selecionado, procure na *Inspetor*e clique na janela retangular juntamente com **Albedo**. Selecione uma cor azul (uma imagem abaixo é **cor hexadecimal: \#3592FFFF**). Depois de ter escolhido, clique no botão Fechar.

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-38.png)

7.  Arraste o novo material do **materiais** pasta em seu recém-criado **plano**, dentro de sua cena (ou remova-o na **plano** dentro do objeto a  *Hierarquia*).

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-39.png)

8.  Clique com botão direito em uma área vazia na *painel de hierarquia*, em seguida, na **objeto 3D, Cápsula**.

    -  Com o **Cápsula** selecionado, altere sua **transformar** *posição* para: **-10, 1, 0**.

9.  Clique com botão direito em uma área vazia na *painel de hierarquia*, em seguida, na **objeto 3D, o cubo**.

    -  Com o **cubo** selecionado, altere sua **transformar** *posição* para: **0, 0, 10**.

10. Clique com botão direito em uma área vazia na *painel de hierarquia*, em seguida, na **objeto 3D, esfera**.

    -  Com o **esfera** selecionado, altere sua **transformar** *posição* para: **10, 0, 0**.

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Eles *posição* valores são *sugestões*. Você é livre para definir as posições dos objetos para tudo o que você gostaria, embora seja mais fácil para o usuário do aplicativo se as distâncias de objetos não são muito distante da câmera.

11. Quando seu aplicativo é executado, ele precisa ser capaz de identificar os objetos na cena, para fazer isso, eles precisam ser marcadas. Selecione um dos objetos e nos *Inspector* do painel, clique em **Adicionar marca...** , que alternará os *Inspetor* com o **marcas e camadas** painel.

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)

12. Clique o **+ (adição)** símbolo e, em seguida, digite o nome da marca como **ObjectInScene**.

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Se você usar um nome diferente para a sua marca, você precisará garantir que essa alteração também é feita a *DataFromAnalytics*, *ObjectTrigger*, e *olhares*, scripts mais tarde, para que seu objetos forem encontrados e detectados dentro de sua cena.

13. Com a marca criada, você precisará aplicá-la a todos os três dos seus objetos. Dos *hierarquia*, mantenha a **Shift** da chave e, em seguida, clique no **Cápsula**, **cubo**, e **esfera**, objetos, em seguida, nos *Inspector*, clique no menu suspenso ao lado **marca**, em seguida, clique no *ObjectInScene* marca que você criou.

    ![Configurar os objetos na cena Unity](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Capítulo 6 - criar a classe ApplicationInsightsTracker

É o primeiro script que você precisa criar **ApplicationInsightsTracker**, que é responsável por:

1.  Criando eventos com base em interações do usuário para enviar para o Azure Application Insights.

2. Criando nomes de eventos apropriados, dependendo da interação do usuário.

3. Enviar eventos para a instância do serviço Application Insights.

Para criar essa classe:

1.  Clique com botão direito no *painel do projeto*, em seguida, **criar** > **pasta**. Nomeie a pasta **Scripts**.

    ![Criar a classe ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Criar a classe ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  Com o **Scripts** pasta criada, clique duas vezes nele, para abrir. Em seguida, dentro dessa pasta, direito do mouse **Create**  >   **C# Script**. Nomeie o script **ApplicationInsightsTracker**.

3.  Clique duas vezes na nova **ApplicationInsightsTracker** script para abri-lo com **Visual Studio**.

4.  Atualizar os namespaces na parte superior do script para ser conforme mostrado abaixo:

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
    > Defina a **instrumentationKey, applicationId e API_Key** valores adequadamente, usando o *chaves de serviço* do Portal do Azure, conforme mencionado na [capítulo 1](#chapter-1---the-azure-portal), etapa 9 em diante.

6.  Em seguida, adicione a **Start ()** e **Awake()** métodos, que serão chamados quando a classe é inicializado:

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

7.  Adicione os métodos responsáveis por enviar os eventos e métricas registradas pelo seu aplicativo:

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

## <a name="chapter-7---create-the-gaze-script"></a>Capítulo 7 - criar o script de olhar

É o próximo script para criar o **olhares** script. Esse script é responsável por criar uma *Raycast* que será projetado para a frente do *câmera principal*, para detectar qual objeto de usuário está observando. Nesse caso, o *Raycast* precisará identificar se o usuário está observando um objeto com o **ObjectInScene** marcar e, em seguida, contar quanto tempo o usuário *gazes* no objeto.

1.  Clique duas vezes no **Scripts** pasta para abri-lo.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script **olhares**.

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

5.  Código para o **Awake()** e **Start ()** métodos agora precisa ser adicionado.

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

6.  Dentro de **olhares** de classe, adicione o seguinte código na **Update ()** método ao projeto um *Raycast* e detectar a ocorrência de destino:

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

7.  Adicione a **ResetFocusedObject()** método para enviar dados a serem **Application Insights** quando o usuário já terá analisado em um objeto.

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

8.  Agora você concluiu a **olhares** script. Salve suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-8---create-the-objecttrigger-class"></a>Capítulo 8 - criar a classe ObjectTrigger

É o próximo script, você precisa criar **ObjectTrigger**, que é responsável por:

- Adicionando componentes necessários de colisão para a câmera principal.
- Detectar se a câmera está perto de um objeto marcado como **ObjectInScene**.

Para criar o script:

1.  Clique duas vezes no **Scripts** pasta para abri-lo.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script **ObjectTrigger**.

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

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Capítulo 9 - criar a classe DataFromAnalytics

Agora você precisará criar o **DataFromAnalytics** script, que é responsável por:

- Buscando dados de análise sobre qual objeto foi abordou pela câmera mais.
- Usando o *chaves de serviço*, que permitem a comunicação com a instância do serviço do Azure Application Insights.
- Classificando os objetos na cena, acordo com os quais tem a maior contagem de eventos.
- Alterar a cor do material, do objeto mais approached, como *verde*.

Para criar o script:

1.  Clique duas vezes no **Scripts** pasta para abri-lo.

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

5.  Dentro do script, insira o seguinte:

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

6.  Dentro de **DataFromAnalytics** classe, logo após o **Start ()** método, adicione o seguinte método chamado **FetchAnalytics()** . Esse método é responsável por popular a lista de pares chave-valor, com um *GameObject* e um número de contagem de eventos do espaço reservado. Em seguida, ele inicializa o **GetWebRequest()** corrotina. A estrutura de consulta da chamada para *Application Insights* pode ser encontrado dentro desse método Além disso, como o *URL de consulta* ponto de extremidade.

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

7.  Logo abaixo do **FetchAnalytics()** método, adicione um método chamado **GetWebRequest()** , que retorna um *IEnumerator*. Esse método é responsável por solicitar o número de vezes que um evento, correspondente a um determinado *GameObject*, foi chamado dentro *Application Insights*. Quando todas as consultas enviadas tem retornado, o **DetermineWinner()** método é chamado.

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

8.  O próximo método é **DetermineWinner()** , que classifica a lista de *GameObject* e *Int* pares, de acordo com a maior contagem de eventos. Ele então altera a cor do material do que *GameObject* à *verde* (como comentários para ter a maior contagem). Isso exibe uma mensagem com os resultados da análise.

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

9.  Adicionar a estrutura de classe que será usada para desserializar o objeto JSON, proveniente *Application Insights*. Adicione essas classes na parte inferior de seu **DataFromAnalytics** arquivo de classe **fora** da definição de classe.

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

## <a name="chapter-10---create-the-movement-class"></a>Capítulo 10 - criar a classe de movimentação

O **movimentação** script é o próximo script, você precisará criar. Ele é responsável por:

- Mover a câmera principal de acordo com a direção da câmera está apontando na direção.
- Adicionando todos os outros scripts para objetos da cena.

Para criar o script:

1.  Clique duas vezes no **Scripts** pasta para abri-lo.

2.  Clique com botão direito dentro de **Scripts** pasta, clique em **Create** >  **C# Script**. Nomeie o script **movimentação**.

3.  Clique duas vezes em que o script para abri-lo com *Visual Studio*.

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

5.  Dentro de **movimentação** classe, *abaixo* vazio **Update ()** método, insira os seguintes métodos que permitem ao usuário usar o controlador de mão para mover-se no espaço virtual:

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

6.  Por fim, adicione a chamada de método dentro de **Update ()** método.

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.

## <a name="chapter-11---setting-up-the-scripts-references"></a>Capítulo 11 - Configurando as referências de scripts

Neste capítulo, você precisa colocar o **movimentação** de script para o **câmera pai** e defina seus destinos de referência. Esse script tratará a colocar outros scripts onde elas precisam ser.

1.  Do **Scripts** pasta na *painel projeto*, arraste o **movimentação** gerar um script para o **câmera pai** objeto localizado no  *Painel de hierarquia*.

    ![Configurando as referências de scripts na cena Unity](images/AzureLabs-Lab309-48.png)

2.  Clique no **pai da câmera**. No *painel de hierarquia*, arraste o **mão direita** do objeto do *painel da hierarquia* para o destino de referência, **controlador**, no *Painel Inspetor*. Defina as **usuário velocidade** para **5**, conforme mostrado na imagem abaixo.

    ![Configurando as referências de scripts na cena Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Capítulo 12 - compilar o projeto do Unity

Todos os componentes necessários para a seção de Unity desse projeto agora foi concluído, portanto, é hora de criá-lo do Unity.

1.  Navegue até **configurações de Build**, (**arquivo** > **configurações de Build**).

2.  Dos **configurações de Build** janela, clique em **Build**.

    ![Compile o projeto do Unity para solução UWP](images/AzureLabs-Lab309-50.png)

3.  Um **Explorador de arquivos** janela será pop-up, que pedirá um local para a compilação. Crie uma nova pasta (clicando **nova pasta** no canto superior esquerdo) e nomeie-o **compilações**.

    ![Compile o projeto do Unity para solução UWP](images/AzureLabs-Lab309-51.png)

    1.  Abra o novo **compilações** pasta e criar outra pasta (usando **nova pasta** mais uma vez) e nomeie- **MR\_Azure\_aplicativo\_ Insights**.

        ![Compile o projeto do Unity para solução UWP](images/AzureLabs-Lab309-52.png)

    2.  Com o **MR\_Azure\_Application\_Insights** pasta selecionada, clique em **Selecionar pasta**. O projeto será levar um minuto ou mais para compilar.

4.  A seguir *construir*, **Explorador de arquivos** será exibida mostrando o local do novo projeto.

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a>Capítulo 13 - implantar aplicativo MR_Azure_Application_Insights em seu computador

Para implantar o **MR\_Azure\_Application\_Insights** aplicativo em seu computador Local:

1.  Abra o arquivo de solução do seu **MR\_Azure\_Application\_Insights** aplicativo no **Visual Studio**.

2.  No **plataforma da solução**, selecione **x86, computador Local**.

3.  No **configuração da solução** selecionar **depurar**.

    ![Compile o projeto do Unity para solução UWP](images/AzureLabs-Lab309-53.png)

4.  Vá para **menu Build** e clique em **implantar solução** para carregar o aplicativo em seu computador.

5.  Seu aplicativo agora deve aparecer na lista de aplicativos instalados, prontos para ser iniciado.

6. Inicie o aplicativo de realidade misturada.

7. Mova a cena se aproximando objetos e examiná-los, quando o *o serviço do Azure Insight* coletou dados suficientes evento, ele definirá o objeto que abordou mais importantes para verde.

> [!IMPORTANT] 
> Durante o tempo de espera médio para o *métricas e eventos* sejam coletados pelo serviço leva cerca de 15 minutos, em algumas ocasiões ele pode levar até 1 hora.

## <a name="chapter-14---the-application-insights-service-portal"></a>Capítulo 14 - portal do serviço Application Insights

Depois que você tenha de roaming em torno da cena e gazed em vários objetos você pode ver os dados coletados na *serviço Application Insights* portal.

1.  Volte para seu portal do serviço Application Insights.

2.  Clique em *Metrics Explorer*.

    ![Observando os dados coletados](images/AzureLabs-Lab309-54.png)

3.  Ele será aberto em uma guia que contém o gráfico que representam o *métricas e eventos* relacionados ao seu aplicativo. Conforme mencionado acima, pode levar algum tempo (até 1 hora) para os dados a serem exibidos no gráfico

    ![Observando os dados coletados](images/AzureLabs-Lab309-55.png)

4.  Clique no *barra de eventos* na *Total de eventos* pela versão do aplicativo, para ver uma análise detalhada dos eventos com seus nomes.

    ![Observando os dados coletados](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>A conclusão de seu aplicativo de serviço Application Insights

Parabéns, você criou um aplicativo de realidade mista que aproveita o serviço Application Insights para monitorar a atividade do usuário dentro de seu aplicativo.

![resultado do curso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

**Exercício 1**

Tente reproduzir, em vez de criar manualmente, os objetos ObjectInScene e definir suas coordenadas no plano dentro de seus scripts. Dessa forma, você pode pedir ao Azure foi de que o objeto mais popular (qualquer um dos resultados de olhar ou proximidade) e geração de um *extra* um desses objetos.

**Exercício 2**

Classifique os resultados de Application Insights por vez, para que você obtenha os dados mais relevantes e implementa esses dados confidenciais de tempo em seu aplicativo.

