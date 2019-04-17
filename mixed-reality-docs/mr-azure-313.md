---
title: MR e 313 - serviço do Hub IoT do Azure
description: Concluir este curso para saber como implementar o serviço do Hub IoT em uma máquina virtual executando Ubuntu 16.4 e, em seguida, visualizar os dados da mensagem usando o Microsoft HoloLens ou um fone de ouvido imersivo (VR).
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: realidade mista, Azure, academy, borda, iot edge, tutorial, api, notificação, funções, tabelas, imersivo, hololens, vr, iot, máquina virtual, ubuntu, python
ms.openlocfilehash: 1ab7c48ac3cff1cb2283cadb171098af9e148628
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589086"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

# <a name="mr-and-azure-313-iot-hub-service"></a>MR e o Azure 313: Serviço do Hub IoT

![resultado do curso](images/AzureLabs-Lab313-00.png)

Neste curso, você aprenderá a implementar uma **serviço do Hub IoT** em uma máquina virtual executando o sistema operacional Ubuntu 16.4. Uma **aplicativo de funções do Azure** será usado para receber mensagens da sua VM do Ubuntu e armazenar o resultado dentro de uma **serviço de tabela do Azure**. Em seguida, ser capaz de exibir esses dados usando **Power BI** no Microsoft HoloLens ou imersivo fone de ouvido (VR).

O conteúdo deste curso *é aplicável* para dispositivos do IoT Edge, embora com a finalidade deste curso, o foco estará em um ambiente de máquina virtual, para que o acesso a um dispositivo físico do Edge não é necessário.

Ao concluir este curso, você aprenderá a:

- Implantar um **módulo do IoT Edge** a uma máquina Virtual Ubuntu 16 SO (), que representará o seu dispositivo IoT.
- Adicionar um **modelo do Tensorflow de visão do Azure personalizado** para o módulo de borda, com um código que analisará imagens armazenadas no contêiner.
- Configurar o módulo para enviar a mensagem de resultado de análise para seu **no Hub IOT**.
- Use uma **aplicativo de funções do Azure** para armazenar a mensagem dentro de uma **tabelas do Azure**.
- Configure **Power BI** para coletar a mensagem armazenada e criar um relatório.
- Visualize os dados de mensagem de IoT dentro **Power BI**.

Os serviços que você usará incluem:

- **O IoT Hub** é um serviço do Microsoft Azure que permite aos desenvolvedores se conectar, monitorar e gerenciar ativos de IoT. Para obter mais informações, visite o [ **serviço do Hub IoT** página](https://azure.microsoft.com/en-au/services/iot-hub/).

- **O registro de contêiner do Azure** é um serviço do Microsoft Azure que permite aos desenvolvedores armazenar imagens de contêiner para vários tipos de contêineres. Para obter mais informações, visite o [ **serviço de registro de contêiner do Azure** página](https://azure.microsoft.com/en-au/services/container-registry/).

- **Aplicativo de funções do Azure** é um serviço de Azure da Microsoft, que permite que os desenvolvedores executem pequenos trechos de código, 'funções', no Azure. Isso fornece uma maneira para delegar trabalho para a nuvem, em vez de seu aplicativo local, o que pode ter muitos benefícios. **O Azure Functions** dá suporte a várias linguagens de desenvolvimento, incluindo C\#, F\#, Node. js, Java e PHP. Para obter mais informações, visite o [ **do Azure Functions** página](https://docs.microsoft.com/azure/azure-functions/functions-overview).

- **Armazenamento do Azure: Tabelas** é um Microsoft Azure Service, que permite aos desenvolvedores armazenar a estruturadas, não-SQL, os dados na nuvem, tornando-o facilmente acessível em qualquer lugar. O serviço apresenta um design sem esquema, permitindo a evolução das tabelas conforme necessário e, portanto, é muito flexível. Para obter mais informações, visite o [ **tabelas do Azure** página](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

Este curso ensinará como configurar e usar o serviço de Hub IoT e, em seguida, visualizar uma resposta fornecida por um dispositivo. Ele será cabe a você aplicar esses conceitos para uma instalação personalizada do serviço de Hub IoT, que você pode criar.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> MR e o Azure 313: Serviço do Hub IoT</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Pré-requisitos

Para os pré-requisitos mais atualizados para o desenvolvimento de realidade misturada, incluindo o Microsoft HoloLens, visite o [instalar as ferramentas](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) artigo.

> [!NOTE]
> Este tutorial é projetado para desenvolvedores que têm experiência básica com o Python. Também esteja ciente de que os pré-requisitos e instruções por escrito neste documento representam o que tenha sido testado e verificado no momento da gravação (julho de 2018). Você é livre para usar o software mais recente, conforme listado dentro de [instalar as ferramentas de](install-the-tools.md) do artigo, embora ele não deve ser suposto que as informações neste curso perfeitamente corresponderá o que você encontrará no software mais recente do que listados abaixo.

O hardware e software a seguir é necessário:

- Windows 10 Fall Creators Update (ou posterior) **modo de desenvolvedor habilitado**

    > [!WARNING]
    > Você não pode executar uma máquina Virtual usando o Hyper-V no Windows 10 Home Edition.

- SDK do Windows 10 (versão mais recente)
- Um HoloLens, **modo de desenvolvedor habilitado**
- Visual Studio 2017.15.4 (usado apenas para acessar o Gerenciador de nuvem do Azure)
- Acesso à Internet para o Azure e para o serviço Hub IoT. Para obter mais informações, siga este [link para a página de serviço do Hub IoT](https://azure.microsoft.com/en-au/services/iot-hub/)
- Um modelo de aprendizado de máquina. Se você não tiver seu próprio pronto para usar o modelo, [você pode usar o modelo fornecido com este curso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).
- **Hyper-V** software habilitado em seu computador de desenvolvimento do Windows 10.
- Uma máquina Virtual executando Ubuntu (16.4 ou 18.4), em execução no computador de desenvolvimento ou como alternativa, você pode usar um computador separado que executa o Linux (Ubuntu 16.4 ou 18.4). Você pode encontrar mais informações sobre como criar uma VM no Windows usando o Hyper-V na [capítulo "Antes de começar"](#before-you-start). ( https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Antes de começar

1. Configurar e testar o HoloLens. Se você precisar dar suporte a configuração do seu HoloLens, [Certifique-se de visitar o artigo de instalação do HoloLens](https://docs.microsoft.com/hololens/hololens-setup).
2. É uma boa ideia realizar **calibragem** e **Sensor ajuste** ao começar a desenvolver um novo aplicativo HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).

Para obter ajuda sobre a calibragem, siga este [link para o artigo de calibragem HoloLens](calibration.md#hololens).

Para obter ajuda sobre ajuste de Sensor, siga este [link para o artigo de ajuste de Sensor HoloLens](sensor-tuning.md).

3. Configurar seu **Máquina Virtual Ubuntu** usando **Hyper-V**. Os recursos a seguir ajudará você com o processo.
    1.  Primeiro, siga este link para [Baixe o ISO do Ubuntu 16.04.4 LTS (Xenial Xerus)](http://au.releases.ubuntu.com/16.04/). Selecione o **imagem da área de trabalho do PC (AMD64) de 64 bits**.
    2.  Certifique-se **Hyper-V** está habilitado no seu computador Windows 10. Você pode seguir este link para obter orientação sobre [instalar e habilitar o Hyper-V no Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
    3.  Inicie o Hyper-V e criar uma nova VM do Ubuntu. Você pode seguir este link para um [guia passo a passo sobre como criar uma VM com o Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine). Quando solicitado **"Instalar um sistema operacional de um arquivo de imagem inicializável"**, selecione o **Ubuntu ISO** tem o download anteriormente.

    > [!NOTE]
    > Usando o **criação rápida do Hyper-V** não é sugerida.  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Capítulo 1: recuperar o modelo de visão personalizada

Com este curso, você terá acesso a um [modelo de visão personalizada pré-criados](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) que detecta teclados e mouses a partir de imagens. Se você usar essa opção, vá para [capítulo 2](#chapter-2---the-container-registry-service).

No entanto, você pode seguir estas etapas se você quiser usar seu próprio modelo de visão personalizada:

1. No seu **personalizados de projeto visão** vá para o **desempenho** guia.

    > [!WARNING]
    > O modelo deve usar um *compact* domínio, a fim de exportar o modelo. Você pode alterar seu domínio de modelos nas configurações para seu projeto.

    ![Guia de desempenho](images/AzureLabs-Lab313-01.png)

2. Selecione o **iteração** você deseja exportar e clique em **exportar**. Uma folha será exibida.

    ![folha de exportação](images/AzureLabs-Lab313-02.png)

3. Na folha, clique em **arquivo Docker**.

    ![Selecione o docker](images/AzureLabs-Lab313-03.png)

4. Clique em **Linux** no menu suspenso e, em seguida, clique em **baixar**.

    ![Clique em Baixar](images/AzureLabs-Lab313-04.png)

5. Descompacte o conteúdo. Você o usará posteriormente no curso.

## <a name="chapter-2---the-container-registry-service"></a>Capítulo 2 - o serviço de registro de contêiner

O **serviço de registro de contêiner** é o repositório usado para hospedar seus contêineres.

O **no Hub IOT** que você criar e usar neste curso, refere-se ao **serviço de registro de contêiner** para obter os contêineres para implantar em seu dispositivo de borda.

1. Primeiro, siga este [link para o Portal do Azure](https://portal.azure.com/)e faça logon com suas credenciais.

2. Vá para **criar um recurso** e procure **registro de contêiner**.

    ![registro de contêiner](images/AzureLabs-Lab313-05.png)

3. Clique em **criar**.

    ![](images/AzureLabs-Lab313-06.png)

4. Configurar o serviço de parâmetros de configuração:

    1. Insira um nome para seu projeto, neste exemplo chama **IoTCRegistry**.

    2. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar, de cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).

    3. Defina o local do serviço.

    4. Definir **usuário administrador** à **habilitar**.

    5. Definir **SKU** à **básica**. 

    ![](images/AzureLabs-Lab313-07.png)

5. Clique em **criar** e aguarde até que os serviços a serem criados. 

6. Depois que a notificação de pop-up informando sobre a criação bem-sucedida do *registro de contêiner*, clique em **ir para o recurso** ser redirecionado para sua página de serviço.

    ![](images/AzureLabs-Lab313-08.png)

7. No *registro de contêiner* página de serviço, clique em **chaves de acesso**.

8. Tome nota (você pode usar o bloco de notas) dos seguintes parâmetros:
    1. **Servidor de logon**
    2. **nome de usuário**
    3. **Senha**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Capítulo 3 - o serviço do Hub IoT

Agora, você começará a criação e configuração do seu **no Hub IOT**.

1. Se ainda não estiver conectado, faça logon na [Portal do Azure](https://portal.azure.com).

2.  Depois de conectado, clique em **criar um recurso** no canto superior esquerdo de canto e procure **IoT Hub**e clique em **Enter**.

 ![Procure a conta de armazenamento](images/AzureLabs-Lab313-10.png)

3.  A nova página fornecerá uma descrição do **conta de armazenamento** Service. Na parte inferior esquerda desse prompt, clique no **criar** botão para criar uma instância deste serviço.

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-11.png)

4.  Depois de clicar em **criar**, um painel será exibido:

    1. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira para monitorar, controlar o acesso, provisionar e gerenciar a cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).

        > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).


    2. Selecione uma opção apropriada **local** (Use o mesmo local em todos os serviços que você cria neste curso).

    3. Inserir sua desejada **nome** para esta instância de serviço.    

5.  Na parte inferior da página, clique em **Avançar: Tamanho e escala**.

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-12.png)

6.  Nessa página, selecione suas **escala e preço** (se esta for a primeira instância de serviço do Hub IoT, uma camada gratuita deve estar disponível para você).  

7.  Clique em **revisar + criar**.

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-13.png)

8.  Revise as configurações e clique em **criar**.

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-14.png)

9. Depois que a notificação de pop-up informando sobre a criação bem-sucedida do *IoT Hub* serviço, clique em **ir para o recurso** ser redirecionado para sua página de serviço.

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-15.png)

10. Role o painel lateral à esquerda até ver *gerenciamento de dispositivo automático*, clique em **IoT Edge**.

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-16.png)

11. Na janela que aparece à direita, clique em **adicionar dispositivo do IoT Edge**. Uma folha será exibida à direita.

12. Na folha, forneça seu novo dispositivo de um **ID do dispositivo** (um nome de sua escolha). Em seguida, clique em **salvar**. O *primário* e *chaves secundárias* irá gerar automaticamente, se você tiver **gerar automaticamente** marcada.

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-17.png)

13. Você navegará de volta para o *dispositivos de borda IoT* seção, onde o novo dispositivo será listado. Clique no seu novo dispositivo (destacadas em vermelho na imagem abaixo). 

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-18.png)

14. Sobre o *detalhes do dispositivo* página for exibida, faça uma cópia da **cadeia de caracteres de Conexão** (chave primária).

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-19.png)

15. Volte para o painel à esquerda e clique em *políticas de acesso compartilhado*, para abri-lo. 

16. Na página que aparece, clique em **iothubowner**, e uma folha será exibida à direita da tela. 

17. Anote (no bloco de notas) a **cadeia de caracteres de Conexão** (chave primária), para uso posterior ao definir o *cadeia de caracteres de Conexão* ao seu dispositivo.

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Capítulo 4 - configuração do ambiente de desenvolvimento

Para criar e implantar módulos para *IoT Hub Edge*, serão necessários os seguintes componentes instalados no computador de desenvolvimento executando o Windows 10:

1.  [Docker para Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), ele solicitará que você crie uma conta para poder baixar. 

    [![Baixe o docker para windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker requer *Windows 10 PRO*, *Enterprise 14393*, ou *Windows Server 2016 RTM*, para executar. Se você estiver executando outras versões do Windows 10, você pode tentar instalar o Docker usando o [caixa de ferramentas do Docker](https://docs.docker.com/toolbox/toolbox_install_windows/).

2.  [Python 3.6](https://www.python.org/downloads/).

    [![Baixe o python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (também conhecido como VS Code)](https://code.visualstudio.com/download).

    [![baixar o VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

Depois de instalar o software mencionado acima, você precisará reiniciar seu computador.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Capítulo 5 – configurar o ambiente do Ubuntu

Agora você pode prosseguir com a configuração do dispositivo **executando o sistema operacional do Ubuntu**. Siga as etapas abaixo para instalar o software necessário, para implantar seus contêineres em seu quadro:

> [!IMPORTANT]
> Você sempre deve preceder os comandos de terminal com **sudo** para ser executado como usuário administrador. i.e:
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Abra o **Ubuntu Terminal**e use o comando a seguir para instalar **pip**:

    > [! Dica] você pode abrir *Terminal* muito facilmente por meio do usando o atalho de teclado: **Ctrl + Alt + T**.

    ```bash
        sudo apt-get install python-pip
    ```

2.  Em todo este capítulo, você pode ser solicitado, por *Terminal*, de permissão para usar o armazenamento do dispositivo e para que você insira **s/n** (Sim ou não), digite **'y'** e, em seguida, pressione a **Enter** chave, para aceitar.

3.  Quando esse comando for concluído, use o seguinte comando para instalar **curl**:

    ```bash
        sudo apt install curl
    ```

4.  Uma vez **pip** e **curl** são instalados, use o seguinte comando para instalar o **tempo de execução do IoT Edge**, isso é necessário para implantar e controlar os módulos em seu quadro:

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. Neste ponto, você será solicitado a abrir o *arquivo de configuração de tempo de execução*, para inserir o **cadeia de Conexão do dispositivo**, que você anotou (em seu bloco de notas), ao criar o **no Hub IOT**  ([na etapa 14, do capítulo 3](#chapter-3---the-iot-hub-service)). Execute a seguinte linha no terminal para abrir esse arquivo:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. O **config. YAML** arquivo será exibido, pronto para edição:

    > [!WARNING]
    > Quando esse arquivo é aberto, ele pode ser um pouco confuso. Você será o texto para editar esse arquivo, dentro de *Terminal* em si. 

    1.  Use as teclas de direção no teclado para rolar para baixo (você precisará rolar para baixo de maneira um pouco), para alcançar a linha que contém ":

        "**\<ADICIONAR CADEIA DE CONEXÃO DO DISPOSITIVO AQUI &GT;**".

    2. Substitua a linha, **incluindo os colchetes**, com o **cadeia de Conexão do dispositivo** anotados anteriormente.

7. Com a cadeia de Conexão em vigor no seu teclado, pressione a **Ctrl-X** chaves para salvar o arquivo. Ele solicitará que você confirme digitando **Y**. Em seguida, pressione a **Enter** chave, para confirmar. Você voltará ao normal *Terminal*. 

8. Depois que esses comandos têm todos são executados com êxito, você terá instalado a **tempo de execução do IoT Edge**. Depois de inicializado, o tempo de execução será iniciado em seu próprio toda vez que o dispositivo é ligado e serão sentar em segundo plano, aguardando módulos ser implantada com o **no Hub IOT**.

9.  Execute a seguinte linha de comando para inicializar o *tempo de execução do IoT Edge*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Se você fizer alterações ao seu arquivo. YAML ou a configuração acima, você precisará executar a linha acima de reinicialização novamente, dentro de *Terminal*.

10. Verifique as *tempo de execução do IoT Edge* status executando a seguinte linha de comando. O tempo de execução deve aparecer com status **ativo (em execução)** em texto verde.

    ```bash
        sudo systemctl status iotedge
    ```

11. Pressione a **Ctrl-C** chaves, para sair da página de status. Você pode verificar se o *tempo de execução do IoT Edge* está obtendo os contêineres corretamente digitando o seguinte comando:

    ```bash
        sudo docker ps
    ```

12. Uma lista com duas (2) contêineres deve aparecer. Esses são os módulos padrão que são criados automaticamente pelo serviço do Hub IoT (edgeAgent e edgeHub). Depois de criar e implantar seus próprios módulos, eles aparecerão nessa lista, sob os valores padrão.

## <a name="chapter-6---install-the-extensions"></a>Capítulo 6 - instalar as extensões

> [!IMPORTANT]
> Os próximos capítulos (6 a 9) devem ser executadas em seu computador Windows 10.

1. Abra **VS Code**.

2. Clique no **extensões** botão (quadrada) do esquerdo barra do VS Code, para abrir o **painel de extensões**.

3. Procurar e instalar as extensões a seguir (conforme mostrado na imagem abaixo):

    1. Azure IoT Edge
    2. Kit de ferramentas do Azure IoT
    3. Docker   

    ![Criar o contêiner](images/AzureLabs-Lab313-24.png)

4. Depois que as extensões são instaladas, feche e abra novamente o VS Code.

5. Com o VS Code, abra mais uma vez, navegue até **Exibir > terminal integrado**.

6. Você instalará **Cookiecutter**. No terminal, execute o seguinte comando do bash:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! Dica] se você tiver dificuldade com este comando: 
    >1. Reinicie o VS Code, e / ou seu computador.
    >2. Talvez seja necessário alternar os **Terminal do VS Code** ao que você usa para instalar o Python, ou seja, **Powershell** (especialmente no caso do ambiente do Python já foi instalado em seu computador). Com o Terminal aberto, você encontrará o menu suspenso no lado direito do Terminal.
     ![Criar o contêiner](images/AzureLabs-Lab313-24b.png) 
    >3. Verifique se o **Python** caminho de instalação é adicionado como **variável de ambiente** em seu computador. Cookiecutter deve fazer parte do caminho do mesmo local. Siga este [link para obter mais informações sobre variáveis de ambiente](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx), 

7. Uma vez **Cookiecutter** terminou de instalar, você deve reiniciar seu computador, para que **Cookiecutter** é reconhecido como um comando, dentro do ambiente do seu sistema.

## <a name="chapter-7---create-your-container-solution"></a>Capítulo 7 - criar sua solução de contêiner

Neste ponto, você precisará criar o contêiner, com o módulo, para ser enviados por push para o *registro de contêiner*. Depois que você tiver enviado por push seu contêiner, você usará o *IoT Hub de borda* serviço implantá-lo em seu dispositivo, que está executando o *tempo de execução do IoT Edge*.

1. No VS Code, clique em **exibição > Paleta de comandos**.

2. Na paleta, pesquisar e executar **Azure IoT Edge: Nova solução de Iot Edge**.

3. Procure em um local onde você deseja criar sua solução. Pressione a **Enter** chave, para aceitar o local.

4. Dê um nome à sua solução. Pressione a **Enter** chave, para confirmar o nome fornecido.

5. Agora você será solicitado a escolher a estrutura de modelo para sua solução. Clique em **módulo de Python**. Pressione a **Enter** chave, para confirmar se essa opção.

6. Dê um nome para seu módulo. Pressione a **Enter** chave, para confirmar o nome do seu módulo. Certifique-se de observar (com o bloco de notas) o nome do módulo, pois ele é usado posteriormente.

7. Você observará uma pré-criados *repositório de imagens do Docker* endereço aparecerá na paleta. Ele se parecerá com:

    **localhost:5000/carros / – o nome do módulo -**. 

8. Exclua **localhost:5000/carros**e em seu lugar insert a *registro de contêiner* **servidor de logon** endereço, que você anotou ao criar o **contêiner Serviço de registro** ([na etapa 8, capítulo 2](#chapter-2---the-container-registry-service)). Pressione a **Enter** chave, para confirmar o endereço.

9. Neste ponto, a solução que contém o modelo para o seu módulo de Python será criada e sua estrutura será exibida na **explorar guia**, do VS Code, no lado esquerdo da tela. Se o **explorar guia** é não está aberta, você pode abri-lo clicando no botão de mais alto, na barra à esquerda.

    ![Criar o contêiner](images/AzureLabs-Lab313-25.png)

10. A última etapa neste capítulo, é clicar e abra o **arquivo. env**, de dentro a **guia explorar**e adicione seu *registro de contêiner* **denomedeusuário** e **senha**. Esse arquivo é ignorado pelo git, mas sobre como compilar o contêiner, definirá as credenciais para acessar o **serviço de registro de contêiner**.

    ![Criar o contêiner](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Capítulo 8 - edição de sua solução de contêiner

Agora, você concluirá a solução de contêiner, atualizando os arquivos a seguir:

- *principal<span></span>. py* script python.
- *requirements.txt*.
- *deployment.template.json*.
- *Dockerfile.amd64*

Em seguida, você criará a *imagens* pasta, usada pelo script do python para verificar se há imagens para correspondência com seu *modelo de visão personalizada*. Por fim, você adicionará a *labels.txt* arquivo, para ajudar a ler o seu modelo e o *model.pb* arquivo, que é o seu modelo.

1. Com o VS Code abrir, navegue até a pasta de módulo e procure o script chamado **principal<span></span>. py**. Clique duas vezes para abri-lo.

2. Exclua o conteúdo do arquivo e insira o seguinte código:

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  Abra o arquivo chamado **Requirements. txt**e substitua seu conteúdo pelo seguinte:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Abra o arquivo chamado **deployment.template.json**e substitua o conteúdo a seguir a abaixo diretriz:

    1. Como você terá seu próprio, exclusiva, estrutura do JSON, será preciso editá-lo manualmente (em vez de copiar um exemplo). Para facilitar isso, use a imagem como um guia abaixo.
    2. Áreas que terá uma aparência diferentes para a sua, mas que você **não deve alterar são realçado em amarelo**.
    3. **As seções que você precisa excluir, são um vermelho realçado.**
    4. Tenha cuidado ao excluir os colchetes corretos e também remover as vírgulas.

        ![Criar o contêiner](images/AzureLabs-Lab313-27.png)

    5. O JSON concluído deve se parecer com a imagem a seguir (no entanto, com suas diferenças exclusivas: *referências de nome de usuário/senha/nome/módulo*):

        ![Criar o contêiner](images/AzureLabs-Lab313-28.png)

5.  Abra o arquivo chamado **Dockerfile.amd64**e substitua seu conteúdo pelo seguinte:

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  Clique com botão direito na pasta abaixo **módulos** (ele terá o nome que você forneceu anteriormente; o exemplo abaixo, ele é chamado *pythonmodule*) e clique em **nova pasta**. Nomeie a pasta **imagens**.

7.  Dentro da pasta, adicione algumas imagens que contêm o mouse ou teclado. Esses serão as imagens que serão analisadas pelo modelo do Tensorflow.

    > [!WARNING]
    > Se você estiver usando seu próprio modelo, você precisará alterar isso para refletir seus próprios dados de modelos.

8.  Agora você precisará recuperar o **labels.txt** e **model.pb** arquivos da pasta de modelo, o que você anterior baixado (ou criado a partir de seu próprio **serviço personalizado de visão** ), em [capítulo 1](#chapter-1---retrieve-the-custom-vision-model). Depois que os arquivos, coloque-os em sua solução, juntamente com os outros arquivos. O resultado final deve ser semelhante a imagem a seguir:

    ![Criar o contêiner](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Capítulo 9 - a solução como um contêiner de pacote

1.  Agora você está pronto "pacotes" de arquivos como um contêiner e enviá-los para seu **registro de contêiner do Azure**. Dentro do VS Code, abra o *Terminal integrado* (**Exibir > Terminal integrado / CTRL + '**) e use a seguinte linha para fazer logon **Docker** (substitua os valores da comando com as credenciais de sua **registro de contêiner do Azure (ACR)**):

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Clique com botão direito no arquivo **deployment.template.json**e clique em **compilar solução do IoT Edge**. Esse processo de compilação leva algum tempo (dependendo do seu dispositivo), portanto, esteja preparado para aguardar. Depois que o processo de compilação for concluída, uma **Deployment** arquivo terá sido criado dentro de uma nova pasta chamada **config**.

    ![Criar implantação](images/AzureLabs-Lab313-30.png)

3. Abra o **paleta de comandos** novamente e pesquise **Azure: Entrar no**. Siga os prompts usando suas credenciais de conta do Azure; VS Code fornecerá uma opção para *copiar e abrir*, que irá copiar o código de dispositivo em breve serão necessárias e abra o navegador da web padrão. Quando solicitado, cole o código de dispositivo, para autenticar seu computador.

    ![copiar e abrir](images/AzureLabs-Lab313-31.png)

4. Uma vez conectado em você vai notar, no lado inferior do *explorar* do painel, uma nova seção chamada **dispositivos de Hub IoT do Azure**. Clique nesta seção para expandi-la.

    ![dispositivo de borda](images/AzureLabs-Lab313-32.png)

5. Se seu dispositivo não está aqui, você precisará com o botão direito *dispositivos de Hub IoT do Azure*e, em seguida, clique em **definir cadeia de Conexão de Hub IoT**. Em seguida, você verá que o **paleta de comandos** (na parte superior do VS Code), solicitará que você insira sua *cadeia de caracteres de Conexão*. Esse é o *cadeia de caracteres de Conexão* você anotou no final da [capítulo 3](#chapter-3---the-iot-hub-service). Pressione a **Enter** da chave, depois de copiar a cadeia de caracteres no.    

6. Seu dispositivo, carregue e são exibidos. Clique com botão direito no nome do dispositivo e, em seguida, clique em **criar implantação para um único dispositivo**.

    ![Criar implantação](images/AzureLabs-Lab313-33b.png)

7. Você obterá uma *Explorador de arquivos* prompt, onde você pode navegar para o **config** pasta e, em seguida, selecione o **Deployment** arquivo. Com o arquivo selecionado, clique o **selecione o manifesto de implantação de borda** botão.

    ![Criar implantação](images/AzureLabs-Lab313-34.png)

8. Neste ponto você forneceu suas **no Hub IOT** com o manifesto implantar seu contêiner, como um módulo de seu **registro de contêiner do Azure**, efetivamente implantá-lo em seu dispositivo.

9. Para exibir as mensagens enviadas do seu dispositivo ao IoT Hub, clique com botão direito novamente em seu nome de dispositivo na **dispositivos de Hub IoT do Azure** seção, o **Explorer** do painel e, em seguida, clique em **Iniciar monitoramento Mensagem D2C**. As mensagens enviadas do seu dispositivo devem aparecer no Terminal do VS. Seja paciente, pois isso pode levar algum tempo. Consulte o capítulo seguinte para depuração e verificar se a implantação foi bem-sucedida.

Esse módulo agora irá iterar entre as imagens a **imagens** pasta e analisá-los, com cada iteração. Isso é, obviamente, apenas uma demonstração de como obter o modelo de aprendizado de máquina básico para trabalhar em um ambiente de dispositivo do IoT Edge. 

Para expandir a funcionalidade desse exemplo, você pode continuar de várias maneiras. Uma maneira de poderia ser incluindo algum código no contêiner, que captura fotos de uma webcam que está conectado ao dispositivo e salva as imagens na pasta de imagens. 

Outra maneira poderia estar apenas copiando as imagens do dispositivo IoT para o contêiner. Uma maneira prática para fazer isso é executar o comando a seguir no dispositivo IoT do Terminal (o talvez um pequeno aplicativo poderia fazer o trabalho, se você quisesse automatizar o processo). Você pode testar esse comando, executando-o manualmente do local de pasta onde os arquivos são armazenados:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Capítulo 10 - depuração de tempo de execução do IoT Edge

A seguir é uma lista de linhas de comando e dicas para ajudá-lo a monitorar e depurar as atividades de mensagem do *tempo de execução do IoT Edge*, do seu **dispositivo Ubuntu**. 

- Verifique as *tempo de execução do IoT Edge* status executando a seguinte linha de comando:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > Lembre-se de pressionar **Ctrl + C**, para terminar de exibir o status.

- Liste os contêineres que estão implantados no momento. Se o *no Hub IOT* tiver implantado os contêineres com êxito, eles serão exibidos, executando a seguinte linha de comando:

    ```bash
        sudo iotedge list
    ```

    Ou

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > As opções acima é uma boa maneira de verificar se o módulo foi implantado com êxito, como ele aparecerá na lista; Caso contrário, você irá **só** consulte o *edgeHub* e *edgeAgent*.

- Para exibir os logs de código de um contêiner, execute a seguinte linha de comando:

    ```bash
        journalctl -u iotedge
    ```

**Comandos úteis para gerenciar o tempo de execução do IoT Edge:**

-  Para excluir todos os contêineres no host:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  Para parar o *tempo de execução do IoT Edge*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Capítulo 11 - criar o serviço tabela 

Navegue de volta para seu Portal do Azure, onde você irá criar um serviço de tabelas do Azure, criando um recurso de armazenamento.

1. Se ainda não estiver conectado, faça logon na [Portal do Azure](https://portal.azure.com).

2. Depois de conectado, clique em **criar um recurso**, no canto superior esquerdo de canto e procure **conta de armazenamento**e pressione a **Enter** tecla para iniciar a pesquisa.

3. Depois que ele é exibido, clique em **conta de armazenamento - blob, arquivo, tabela, fila** na lista.

    ![Procure a conta de armazenamento](images/AzureLabs-Lab313-35.png)

4. A nova página fornecerá uma descrição do **conta de armazenamento** Service. Na parte inferior esquerda desse prompt, clique no **criar** botão para criar uma instância deste serviço.

    ![Criar instância de armazenamento](images/AzureLabs-Lab313-36.png)

5. Depois de clicar em **criar**, um painel será exibido:

    1. Inserir sua desejada **nome** para esta instância de serviço (*deve estar em letras minúsculas*).

    2. Para **modelo de implantação**, clique em **Gerenciador de recursos**.

    3. Para **tipo de conta**, usando o menu suspenso, clique em **(uso geral v1) de armazenamento**.

    4. Clique em um número apropriado **local**.
    
    5. Para o **replicação** menu suspenso, clique em **leitura-acesso-com redundância geográfica (RA-GRS) de armazenamento**.

    6. Para **desempenho**, clique em **padrão**.

    7. Dentro de **transferência segura obrigatória** seção, clique em **desabilitado**.

    8. Dos **assinatura** menu suspenso, clique em uma assinatura apropriada.

    9. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar, de cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).

        > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Deixe **redes virtuais** como **desabilitado**, se essa é uma opção para você.

    11. Clique em **Criar**.

        ![Preencha os detalhes de armazenamento](images/AzureLabs-Lab313-37.png)

6. Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

7. Uma notificação será exibida no Portal depois que a instância do serviço é criada. Clique em notificações para explorar a nova instância do serviço.

    ![nova notificação de armazenamento](images/AzureLabs-Lab313-38.png)

8. Clique o **ir para o recurso** botão na notificação e você será levado para a nova página de visão geral de instância de serviço de armazenamento.

    ![Ir para o recurso](images/AzureLabs-Lab313-39.png)

9. Na página de visão geral, para o lado direito, clique em **tabelas**.
    
    ![Tabelas](images/AzureLabs-Lab313-40.png)

10. O painel à direita será alterado para mostrar o **serviço tabela** informações, no qual você precisa adicionar uma nova tabela. Faça isso clicando o **+ tabela** botão no canto superior esquerdo.

    ![abrir tabelas](images/AzureLabs-Lab313-41.png)

11. Uma nova página será mostrada, no qual você precisa inserir uma **nome da tabela**. Esse é o nome que você usará para se referir aos dados em seu aplicativo em capítulos (criar aplicativo de funções e o Power BI). Inserir **IoTMessages** como o nome (você pode escolher seus próprios, lembre-se, quando usado neste documento) e clique em **Okey**. 

12. Quando a nova tabela tiver sido criada, você poderá vê-lo dentro de **serviço tabela** página (na parte inferior).

    ![nova tabela criada](images/AzureLabs-Lab313-42.png)  

13. Agora, clique em **chaves de acesso** e faça uma cópia do **nome da conta de armazenamento** e **chave** (usando o bloco de notas), você usará esses valores posteriormente no curso, ao criar o **Aplicativo de funções do azure**.

    ![nova tabela criada](images/AzureLabs-Lab313-43.png) 

14. Usando o painel à esquerda, role até a *serviço de tabela* seção e, em seguida, clique em **tabelas** (ou **procurar tabelas**, em portais de mais recentes) e faça uma cópia do  **URL de tabela** (usando o bloco de notas). Você usará esse valor posteriormente no curso, ao vincular a sua tabela para seu **Power BI** aplicativo.

    ![nova tabela criada](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Capítulo 12 - Concluindo a tabela do Azure

Agora que sua **serviço tabela** conta de armazenamento tiver sido configurado, é hora de adicionar dados a ele, que será usada para armazenar e recuperar informações. A edição de suas tabelas pode ser feita por meio **Visual Studio**.

1. Abra **Visual Studio** (**não** Visual Studio Code).

2. No menu, clique em **exibição > Gerenciador de nuvem**.

    ![Abra o cloud explorer](images/AzureLabs-Lab313-45.png)

3. O **Cloud Explorer** será aberto como um item encaixado (seja paciente, pois o carregamento pode levar tempo).

    > [!WARNING] 
    > Se a assinatura que você usou para criar sua *contas de armazenamento* não estiver visível, certifique-se de que você tenha: 
    > - Conectado à mesma conta que você usou para o Portal do Azure.
    > - Selecionado sua assinatura na página de gerenciamento de conta (talvez você precise aplicar um filtro de suas configurações de conta):  
    >
    >   ![localizar a assinatura](images/AzureLabs-Lab313-46.png)

4. Os serviços de nuvem do Azure serão mostrados. Encontre **contas de armazenamento** e clique na seta à esquerda do que para expandir suas contas.

    ![Abra as contas de armazenamento](images/AzureLabs-Lab313-47.png)

5. Quando expandida, seu recém-criado **conta de armazenamento** devem estar disponíveis. Clique na seta à esquerda de seu armazenamento e, em seguida, depois que é expandido, encontrar **tabelas** e clique na seta ao lado de que, para revelar as **tabela** você criou no último capítulo. Clique duas vezes em sua **tabela**.

6. A tabela será aberta no centro da janela do Visual Studio. Clique no ícone de tabela com o **+** (mais) nele.

    ![Adicionar nova tabela](images/AzureLabs-Lab313-48.png)

7. Uma janela será exibida solicitando que você *Adicionar entidade*. Você irá criar apenas uma única entidade, embora ele terá três propriedades. Você observará que *PartitionKey* e *RowKey* já são fornecidas, pois eles são usados pela tabela para localizar os dados. 

    ![chave de partição e de linha](images/AzureLabs-Lab313-49.png)

8. Atualize os valores a seguir:

    - Nome: **PartitionKey**, valor: **PK_IoTMessages** 

    - Nome: **RowKey**, valor: **RK_1_IoTMessages** 

9. Em seguida, clique em **adicionar propriedade** (para o canto inferior esquerdo das *Adicionar entidade* janela) e adicione a seguinte propriedade:

    - **O MessageContent**, como uma *cadeia de caracteres*, deixe o valor vazio.

10. Sua tabela deve corresponder na imagem abaixo:

    ![Adicione os valores corretos](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > O motivo por que a entidade tem o número 1 na chave de linha, é porque deseja adicionar mais mensagens, você deseja fazer experiências com este curso.

11. Clique em **Okey** quando tiver terminado. A tabela agora está pronta para ser usado.

## <a name="chapter-13---create-an-azure-function-app"></a>Capítulo 13 - criar um aplicativo de funções do Azure 

Chegou a hora agora para criar uma *aplicativo de funções do Azure*, que será chamado pelo *no Hub IOT* para armazenar os *do IoT Edge* mensagens de dispositivo na **tabela** Serviço, que você criou no capítulo anterior.

Primeiro, você precisa criar um arquivo que permitirá que sua função do Azure carregar as bibliotecas que necessárias.

1.  Abra **bloco de notas** (pressione a *chave do Windows*e o tipo *o bloco de notas*).

    ![Abra o bloco de notas](images/AzureLabs-Lab313-51.png)

2.  Com o bloco de notas aberto, insira a estrutura JSON abaixo nela. Depois de ter feito isso, salve-o na área de trabalho como **Project. JSON**. Esse arquivo define as bibliotecas de que sua função usará. Se você tiver usado o NuGet, parecerá familiar.
    
    > [!WARNING]
    > É importante que a nomenclatura está correta; Certifique-se de que ele faz **não tiver uma. txt** extensão de arquivo. Veja abaixo para referência:
    >
    > ![JSON save](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  Faça logon na [Portal do Azure](https://portal.azure.com).

4.  Quando você estiver conectado, clique em **criar um recurso** no canto superior esquerdo de canto e procure **aplicativo de funções**e pressione a **Enter** chave a ser pesquisado. Clique em *aplicativo de funções* nos resultados, para abrir um novo painel.

    ![Procure o aplicativo de funções](images/AzureLabs-Lab313-53.png)

5.  O novo painel fornecerá uma descrição do **aplicativo de funções** Service. Na parte inferior esquerda deste painel, clique no **criar** botão para criar uma associação com este serviço.

    ![instância do aplicativo de função](images/AzureLabs-Lab313-54.png)

6.  Depois de clicar em **criar**, preencha o seguinte:

    1. Para **nome do aplicativo**, inserir seu nome desejado para esta instância de serviço.

    2. Selecione uma **assinatura**.

    3. Selecione o tipo de preço apropriado para você, se esta for a primeira hora de criar uma **serviço de aplicativo de função**, uma camada gratuita deve estar disponível para você.

    4. Escolha uma **grupo de recursos** ou criar um novo. Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar, de cobrança para uma coleção de ativos do Azure. É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, como esses cursos) em um grupo de recursos comuns).

        > Se você quiser ler mais sobre grupos de recursos do Azure, siga este [link sobre como gerenciar um grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Para **SO**, clique em Windows, já que é a plataforma destinada.

    6. Selecione uma **plano de hospedagem** (Este tutorial está usando uma **plano de consumo**.

    7. Selecione uma **local** (escolha o mesmo local como o armazenamento que você criou na etapa anterior)

    8. Para o **armazenamento** seção, **você deve selecionar o serviço de armazenamento que você criou na etapa anterior**.

    9. Você não precisará *Application Insights* neste aplicativo, fique à vontade para deixá-lo **Off**.

    10. Clique em **Criar**.

        ![Criar nova instância](images/AzureLabs-Lab313-55.png)

7.  Depois de clicar em **criar**, você terá que aguardar o serviço a ser criado, isso pode levar um minuto.

8.  Uma notificação será exibida no Portal depois que a instância do serviço é criada.

    ![nova notificação](images/AzureLabs-Lab313-56.png)

9.  Clique na notificação, quando a implantação for bem-sucedida (terminou).

10. Clique o **ir para o recurso** botão na notificação para explorar a nova instância do serviço. 

    ![Ir para o recurso](images/AzureLabs-Lab313-57.png)

11. No lado esquerdo do novo painel, clique no **+** (mais) ícone próximo ao *funções*, para criar uma nova função.

    ![Adicionar nova função](images/AzureLabs-Lab313-58.png)

12. No painel central, o **função** será exibida a janela de criação. Role mais para baixo e clique em **função personalizada**.

    ![função personalizada](images/AzureLabs-Lab313-59.png)

13. Role para baixo próxima página, até encontrar **IoT Hub (Hub de eventos)**, em seguida, clique nele.

    ![função personalizada](images/AzureLabs-Lab313-60.png)

14. No **IoT Hub (Hub de eventos)** folha, defina as **idioma** para **C#** e, em seguida, clique em **novo**.

    ![função personalizada](images/AzureLabs-Lab313-61.png)

15. Na janela que será exibido, certifique-se de que **IoT Hub** está selecionado e o nome da *IoT Hub* campo corresponde com o nome do seu *serviço Hub IoT* que você tem criado anteriormente ([na etapa 8, do capítulo 3](#chapter-3---the-iot-hub-service)). Em seguida, clique o **selecionar** botão.

    ![função personalizada](images/AzureLabs-Lab313-62.png)

16. Volta a **IoT Hub (Hub de eventos)** folha, clique em **criar**.

    ![função personalizada](images/AzureLabs-Lab313-63.png)

17. Você será redirecionado para o editor de função.

    ![função personalizada](images/AzureLabs-Lab313-64.png)

18. Exclua todo o código nele e substitua-o com o seguinte:

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. Alterar as variáveis a seguir, para que eles correspondam com os valores apropriados (**tabela** e **armazenamento** valores, da [etapa 11 e 13, respectivamente, do Capítulo 11](#chapter-11---create-table-service)), que você encontrará em sua **conta de armazenamento**:

    - **tableName**, com o nome do seu **tabela** localizado no seu **conta de armazenamento**.
    - **tableURL**, com a URL do seu **tabela** localizado no seu **conta de armazenamento**.
    - **storageAccountName**, com o nome do valor correspondente com o nome do seu **conta de armazenamento** nome.
    - **storageAccountKey**, com a chave que você obteve no serviço de armazenamento que você criou anteriormente.

    ![função personalizada](images/AzureLabs-Lab313-65.png)

20. Com o código no local, clique em **salvar**.

21. Em seguida, clique o **\<** ícone (seta), no lado direito da página.

    ![função personalizada](images/AzureLabs-Lab313-66.png)

22. Um painel será Deslizar pela direita. Nesse painel, clique em **carregue**e um *navegador de arquivos* será exibida.

23. Navegue até e, em seguida, clique em, o **Project. JSON** arquivo, que você criou na **bloco de notas** anteriormente e, em seguida, clique no **abrir** botão. Esse arquivo define as bibliotecas que sua função usará.

    ![função personalizada](images/AzureLabs-Lab313-67.png)

24. Quando o arquivo foi carregado, ele será exibido no painel à direita. Ao clicar nele irá abri-lo dentro de **função** editor. Ele deve parecer **exatamente** o mesmo que a imagem a seguir.

    ![função personalizada](images/AzureLabs-Lab313-68.png)

25. Neste ponto, seria bom testar a funcionalidade de sua função para armazenar a mensagem em seu *tabela*. No lado superior direito da janela, clique em **teste**.

    ![função personalizada](images/AzureLabs-Lab313-69.png)

26. Inserir uma mensagem sobre o **corpo da solicitação**, conforme mostrado na imagem acima e clique em **executar**. 

27. A função será executado, exibindo o status do resultado (você observará que o verde **Status de 202 aceito**, acima o *saída* janela, o que significa que ele foi uma chamada bem-sucedida):

    ![resultado de saída](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Capítulo 14 - exibir mensagens de Active Directory

Se você abrir o Visual Studio agora (**não** Visual Studio Code), você pode visualizar o resultado da mensagem de teste, pois ele será armazenado na *o MessageContent* área de cadeia de caracteres.

![função personalizada](images/AzureLabs-Lab313-71.png)

Com o serviço de tabela e o aplicativo de funções em vigor, as mensagens de dispositivo do Ubuntu aparecerá no seu *IoTMessages* tabela. Se ainda não estiver em execução, inicie o dispositivo novamente e você poderá ver as mensagens de resultado do seu dispositivo, módulo e, dentro de sua tabela, por meio do usando o Visual Studio *Cloud Explorer*.

![Visualizar dados](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>Capítulo 15 - instalação do Power BI

Para visualizar os dados do seu dispositivo IOT, você configurará **Power BI** (versão da área de trabalho,) para coletar os dados das *tabela* serviço, que você acabou de criar. O *HoloLens* versão do Power BI, em seguida, usará esses dados para visualizar o resultado.

1.  Abra o Microsoft Store no Windows 10 e pesquise **Power BI Desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Baixe o aplicativo. Depois que o download for concluído, abra-o.

3.  Faça logon no *Power BI* com seu **conta do Microsoft 365**. Você pode ser redirecionado para um navegador, para se inscrever. Depois que você se inscreveu, vá até o aplicativo Power BI e entrar novamente.

4.  Clique em **obter dados** e, em seguida, clique em **mais...** .

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  Clique em **Azure**, **Azure Table Storage**, em seguida, clique em **Connect**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Você será solicitado a inserir o **adresa URL Tabulky** coletados anteriormente ([na etapa 13 do Capítulo 11](#chapter-11---create-table-service)), durante a criação de seu serviço de tabela. Depois de inserir a URL, exclua a parte do caminho da referência à tabela "subpasta" (que era IoTMessages, neste curso). O resultado final deve ser conforme exibido na imagem abaixo. Em seguida, clique em **Okey**.

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Você será solicitado a inserir o **chave de armazenamento** que você anotou ([na etapa 11 do Capítulo 11](#chapter-11---create-table-service)) anteriores durante a criação de seu armazenamento de tabelas. Em seguida, clique em **Connect**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Um **painel navegador** será exibida, marque a caixa ao lado de sua tabela e clique em **carga**.

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. Sua tabela agora tenha sido carregada no Power BI, mas requer uma consulta para exibir os valores nele. Para fazer isso, clique com botão direito no nome da tabela localizado na **painel CAMPOS** no lado direito da tela. Em seguida, clique em **Editar consulta**.

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. Um **Editor do Power Query** será aberta como uma nova janela, exibindo sua tabela. Clique na palavra **registro** dentro de *conteúdo* coluna da tabela, para visualizar seu conteúdo armazenado.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Clique em **em uma tabela**, no canto superior esquerdo da janela. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Clique em **fechar e aplicar**.

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. Depois de terminar de carregar a consulta dentro de **painel CAMPOS**, no lado direito da tela, marque as caixas correspondentes aos parâmetros **nome** e **valor**, para visualizar a **o MessageContent** conteúdo da coluna.

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Clique no **ícone de disco azul** na parte superior esquerda da janela para salvar seu trabalho em uma pasta de sua escolha.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. Agora, você pode clicar no botão Publicar para carregar a tabela para seu espaço de trabalho. Quando solicitado, clique em **meu espaço de trabalho** e clique em *selecione*. Aguarde exibir o resultado com êxito do envio.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> O capítulo seguinte é específico do HoloLens. Power BI não está atualmente disponível como um aplicativo imersivo, no entanto, você pode executar a versão da área de trabalho no Portal de realidade mista do Windows (também conhecido como Cliff House), por meio do aplicativo da área de trabalho.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Capítulo 16 - dados de exibição Power BI em HoloLens

1. No seu HoloLens, faça login para o **Microsoft Store**, tocando no ícone na lista de aplicativos.

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. Pesquisar e, em seguida, baixe o **Power BI** aplicativo.

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. Inicie **Power BI** da sua lista de aplicativos. 

4. **Power BI** pode solicitar que você fazer logon em seu **conta do Microsoft 365**.

5. Uma vez dentro do aplicativo, o espaço de trabalho deve exibir por padrão como mostrado na imagem abaixo. Se isso não acontecer, basta clicar no ícone no lado esquerdo da janela do espaço de trabalho.

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>A conclusão de seu aplicativo de IoT Hub

Parabéns, você criou com êxito um serviço de Hub IoT, com um dispositivo simulado de borda de máquina Virtual. Seu dispositivo pode se comunicar os resultados de um modelo de machine learning para um serviço de tabela do Azure, facilitada por um aplicativo de função do Azure, que é lido no Power BI e visualizados dentro de um Microsoft HoloLens.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Exercícios de bônus

### <a name="exercise-1"></a>Exercício 1

Expanda a estrutura de mensagens armazenada na tabela e exibi-lo como um gráfico. Você talvez queira coletar mais dados e armazená-lo na mesma tabela, a ser exibido mais tarde.

### <a name="exercise-2"></a>Exercício 2

Criar um adicional "captura com câmera" módulo a ser implantado na placa de IoT, para que ele possa capturar imagens através da câmera a serem analisados.
