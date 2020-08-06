---
title: Âncoras Espaciais do Azure no Unreal
description: Visão geral da criação das Âncoras Espaciais do Azure no Unreal Engine.
author: hferrone
services: azure-spatial-anchors
ms.author: v-haferr
ms.date: 07/01/2020
ms.topic: tutorial
ms.service: azure-spatial-anchors
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, azure development, spatial anchors, mixed reality, development, features, new project, emulator, documentation, guides, holograms, game development
ms.openlocfilehash: c7189407bea4b38e7305f0dda7637b82d3325704
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87377220"
---
# <a name="azure-spatial-anchors-in-unreal"></a>Âncoras Espaciais do Azure no Unreal

## <a name="overview"></a>Visão geral

As Âncoras Espaciais do Azure são um serviço de Realidade Misturada da Microsoft, permitindo que dispositivos de realidade aumentada descubram, compartilhem e persistam pontos de ancoragem no mundo físico. A documentação abaixo fornece instruções para integrar o serviço Âncoras Espaciais do Azure a um projeto do Unreal. Se estiver buscando mais informações, confira o [serviço Âncoras Espaciais do Azure](https://azure.microsoft.com/services/spatial-anchors/).

> [!IMPORTANT]
> As âncoras locais são armazenadas no dispositivo, enquanto as Âncoras Espaciais do Azure são armazenadas na nuvem. Se você está buscando armazenar suas âncoras localmente em um dispositivo, temos um documento [Âncoras Espaciais locais](unreal-spatial-anchors.md) que pode orientar você no processo. Você pode ter âncoras locais e do Azure no mesmo projeto sem conflitos.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este guia, verifique se você:

- Instalou o [Unreal versão 4.25](https://www.unrealengine.com/get-now) ou posterior
- Um [projeto do HoloLens 2](unreal-uxt-ch1.md) configurado no Unreal 
- Leia a [visão geral das Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/overview)
- Conhecimento básico de C++ e Unreal

## <a name="getting-azure-spatial-anchors-account-info"></a>Como obter informações da conta das Âncoras Espaciais do Azure

Para usar as Âncoras Espaciais do Azure no seu projeto, você precisará:
* [Criar um recurso de âncoras espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) e copiar os campos da conta listados abaixo. Esses valores são usados para autenticar os usuários na conta do seu aplicativo:
    * **ID da Conta**
    * **Chave de Conta**

Confira a documentação [Autenticação das Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) para obter mais informações.

> [!NOTE]
> As Âncoras Espaciais do Azure no Unreal 4.25 não dão suporte a tokens de autenticação do Azure AD, mas o suporte para essa funcionalidade será disponibilizado em uma versão posterior.

## <a name="adding-azure-spatial-anchors-plugins"></a>Como adicionar plug-ins das Âncoras Espaciais do Azure

Habilite os plug-ins das Âncoras Espaciais do Azure no editor do Unreal:
1. Clicando em **Editar > Plug-ins** e procurando **AzureSpatialAnchors** e **AzureSpatialAnchorsForWMR**.
2. Marque a caixa de seleção **Habilitado** nos dois plug-ins para permitir o acesso às bibliotecas de blueprints das Âncoras Espaciais do Azure no seu aplicativo.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-01.png)

Depois disso, reinicie o editor do Unreal para que as alterações do plug-in entrem em vigor. Agora, o projeto está pronto para usar as Âncoras Espaciais do Azure.

## <a name="starting-a-spatial-anchors-session"></a>Como iniciar uma sessão das Âncoras Espaciais
Uma sessão das Âncoras Espaciais do Azure permite que os aplicativos cliente se comuniquem com o serviço Âncoras Espaciais do Azure. Você precisará criar e iniciar uma sessão das Âncoras Espaciais do Azure para criar, persistir e compartilhar as Âncoras Espaciais do Azure:

1. Abra o blueprint do Peão que você está usando no aplicativo.
2. Adicione duas variáveis de cadeia de caracteres à **ID da Conta** e à **Chave de Conta** e atribua os valores correspondentes da sua conta das Âncoras Espaciais do Azure para autenticar a sessão.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-02.png)

Inicie uma sessão das Âncoras Espaciais do Azure:
1. Verificando se uma **Sessão de AR** está em execução no aplicativo do HoloLens, pois a sessão das Âncoras Espaciais do Azure não pode ser iniciada até que uma Sessão de AR esteja em execução. Se você não tiver uma configuração, [crie um ativo da Sessão de AR](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).
2. Adicionando o evento personalizado **Iniciar Sessão das Âncoras Espaciais do Azure** e configurando-o conforme mostrado na captura de tela abaixo.
    * A criação de uma sessão não inicia a sessão por padrão, o que permite ao desenvolvedor configurar a sessão para autenticação no serviço Âncoras Espaciais do Azure.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. Configure a sessão das Âncoras Espaciais do Azure para fornecer a **ID da Conta** e a **Chave de Conta**.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. Inicie a sessão das Âncoras Espaciais do Azure, permitindo que o aplicativo crie e localize as Âncoras Espaciais do Azure.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-05.png)

Será uma boa prática limpar os recursos das Âncoras Espaciais do Azure no blueprint do Grafo de Eventos quando você não estiver mais usando o serviço:

1. Interrompa a sessão das Âncoras Espaciais do Azure. A sessão não estará mais em execução, mas os respectivos recursos associados ainda existirão no plug-in das Âncoras Espaciais do Azure.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. Destrua a sessão das Âncoras Espaciais do Azure para limpar os recursos da sessão das Âncoras Espaciais do Azure ainda conhecidos pelo plug-in das Âncoras Espaciais do Azure.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-07.png)

O blueprint do Grafo de Eventos será parecido com a captura de tela abaixo:

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-08.png)


## <a name="creating-an-anchor"></a>Como criar uma âncora
Uma Âncora Espacial do Azure representa uma pose do mundo físico no espaço do aplicativo de realidade aumentada, que bloqueia o conteúdo de realidade aumentada em localizações do mundo físico. As Âncoras Espaciais do Azure também podem ser compartilhadas entre diferentes usuários. Esse compartilhamento permite que o conteúdo de realidade aumentada desenhado em diferentes dispositivos seja posicionado na mesma localização no mundo físico. 

Para criar uma Âncora Espacial do Azure:
1. Verifique se uma sessão das Âncoras Espaciais do Azure está em execução. O aplicativo não pode criar nem manter uma Âncora Espacial do Azure quando não há nenhuma sessão das Âncoras Espaciais do Azure em execução.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. Crie ou obtenha um **[Componente de Cena](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** do Unreal que deve ter a localização persistente. 
    * Na imagem abaixo, o componente **Âncora que Precisa de um Componente de Cena** é usado como uma variável. Um Componente de Cena do Unreal é necessário para estabelecer uma transformação do mundo do aplicativo em um [Marcador de AR](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) e uma Âncora Espacial do Azure.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-10.png)

Para construir e salvar uma Âncora Espacial do Azure de um Componente de Cena do Unreal:
1. Chame o [Componente de Marcador](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) para o Componente de Cena do Unreal e especifique a **Transformação do Mundo** do Componente de Cena como a Transformação do Mundo usada para o Marcador de AR.
    * O Unreal acompanha os pontos de AR no espaço do aplicativo usando Marcadores de AR, que são usados para criar uma Âncora Espacial do Azure. No Unreal, um Marcador de AR é similar a uma SpatialAnchor no HoloLens.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. Chame **Criar Âncora de Nuvem** usando o Marcador de AR recém-criado.
    * A função Criar Âncora de Nuvem cria uma Âncora Espacial do Azure localmente, mas não no serviço Âncora Espacial do Azure. Os parâmetros para a Âncora Espacial do Azure, como uma data de validade, podem ser definidos antes da criação da Âncora Espacial do Azure com o serviço.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. Defina a validade da Âncora Espacial do Azure. O parâmetro Tempo de Vida da função permite que o desenvolvedor especifique, em segundos, quanto tempo a âncora deve ser mantida pelo serviço.
    * Por exemplo, uma validade de uma semana usará um valor igual a 60 segundos x 60 minutos x 24 horas x sete dias = 604.800 segundos.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-13.png)

Depois de definir os parâmetros de âncora, declare a âncora como pronta para ser salva. No exemplo abaixo, a Âncora Espacial recém-criada do Azure é adicionada a um conjunto das Âncoras Espaciais do Azure que precisam ser salvas. Esse conjunto é declarado como uma variável do blueprint de Peão.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a>Como salvar uma âncora

Depois de configurar a Âncora Espacial do Azure com os parâmetros, chame a função **Salvar Âncora de Nuvem**. A função Salvar âncora de Nuvem declara a âncora para o serviço Âncoras Espaciais do Azure. Quando a chamada a Salvar Âncora de Nuvem for realizada com sucesso, a Âncora Espacial do Azure estará disponível para outros usuários do serviço Âncora Espacial do Azure.  

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> A função Salvar Âncora de Nuvem é assíncrona e só pode ser chamada em um evento de thread de jogo, como **EventTick**. Talvez a função Salvar Âncora de Nuvem não seja exibida como uma função de blueprint disponível nas funções de blueprint personalizadas. No entanto, ela deve estar disponível no editor de blueprint do Grafo de Eventos do Peão.

No exemplo abaixo, a Âncora Espacial do Azure é armazenada em um conjunto durante um retorno de chamada de evento de entrada. Em seguida, a âncora é salva no EventTick. Para salvar uma Âncora Espacial do Azure, podem ser necessárias várias tentativas dependendo do volume de dados espaciais criado pela sessão das Âncoras Espaciais do Azure. Por esse motivo, é uma boa ideia verificar se a chamada de salvamento foi bem-sucedida.

Se a âncora não for salva, adicione-a novamente ao conjunto de âncoras que ainda precisa ser salvo. Os EventTicks futuros tentarão salvar a âncora até que ela seja armazenada com êxito no serviço Âncora Espacial do Azure.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-16.png)

Depois que a âncora for salva, use a transformação de Marcadores de AR como uma transformação de referência para colocar conteúdo no aplicativo. Outros usuários podem detectar essa âncora e alinhar o conteúdo de AR para diferentes dispositivos no mundo físico.

## <a name="deleting-an-anchor"></a>Como excluir uma âncora

Exclua âncoras do serviço Âncora Espacial do Azure chamando **Excluir Âncora de Nuvem**.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> A função Excluir Âncora de Nuvem é latente e só pode ser chamada em um evento de thread de jogo, como EventTick. Talvez a função Excluir Âncora de Nuvem não seja exibida como uma função de blueprint disponível nas funções de blueprint personalizadas. No entanto, ela deve estar disponível no editor de blueprint do Grafo de Eventos de Peão.

No exemplo abaixo, a âncora é sinalizada para exclusão em um evento de entrada personalizado. Em seguida, é feita a tentativa de exclusão no EventTick. Se a exclusão da âncora falhar, adicione a Âncora Espacial do Azure ao conjunto de âncoras sinalizadas para exclusão e tente novamente em EventTicks posteriores.

Agora, o blueprint do Grafo de Eventos será parecido com a captura de tela abaixo:

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a>Como localizar âncoras pré-existentes

Além de criar Âncoras Espaciais do Azure, você pode detectar âncoras criadas por colegas com o serviço Âncoras Espaciais do Azure:

1. Obtenha um identificador de Âncora Espacial do Azure da âncora que deseja detectar.
    * Um identificador de âncora pode ser obtido para uma âncora criada pelo mesmo dispositivo em uma sessão anterior das Âncoras Espaciais do Azure. Ele também pode ser criado e compartilhado por dispositivos pares que interagem com o serviço Âncoras Espaciais do Azure.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. Adicione um componente **AzureSpatialAnchorsEvent** ao blueprint de Peão.
    * Esse componente permite que você assine vários eventos das Âncoras Espaciais do Azure, como eventos chamados quando as Âncoras Espaciais do Azure são localizadas.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. Assine o **Delegado Localizado de ASAAnchor** para o componente **AzureSpatialAnchorsEvent**.
    * O delegado permite que o aplicativo saiba quando são localizadas novas âncoras associadas à conta das Âncoras Espaciais do Azure.
    * Com o retorno de chamada do evento, as Âncoras Espaciais do Azure criadas pelos colegas que usam a sessão das Âncoras Espaciais do Azure não terão Marcadores de AR criados por padrão. Para criar um Marcador de AR para a Âncora Espacial do Azure detectada, os desenvolvedores podem chamar a função **Criar Marcador de RA em Torno da Âncora Espacial de Nuvem do Azure**.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-20.png)

Para localizar Âncoras Espaciais do Azure criadas pelos pares usando o serviço Âncora Espacial do Azure, o aplicativo precisará criar um **Observador das Âncoras Espaciais do Azure**:
1. Verifique se uma sessão das Âncoras Espaciais do Azure está em execução.
2. Crie um **AzureSpatialAnchorsLocateCriteria**.
    * Você pode especificar vários parâmetros de localização, como distância do usuário ou distância de outra âncora.
3. Declare o identificador desejado da Âncora Espacial do Azure em **AzureSpatialAnchorsLocateCriteria**.
4. Chame **Criar Observador**.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-21.png)

Agora, o aplicativo começa a procurar as Âncoras Espaciais do Azure conhecidas pelo serviço Âncoras Espaciais do Azure, o que significa que os usuários podem localizar as Âncoras Espaciais do Azure criadas pelos colegas.

Depois de localizar a Âncora Espacial do Azure, chame a função **Parar Observador** para interromper o Observador das Âncoras Espaciais do Azure e limpar os recursos do observador.

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-22.png)

Agora, o blueprint final do Grafo de Eventos será parecido com a captura de tela abaixo:

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-23.png)


## <a name="next-steps"></a>Próximas etapas
* [Âncoras Espaciais locais](unreal-spatial-anchors.md)
* [Documentação das Âncoras Espaciais](https://docs.microsoft.com/azure/spatial-anchors/)
* [Recursos da Âncora Espacial](https://azure.microsoft.com/services/spatial-anchors/#features)
* [Diretrizes de experiência de ancoragem efetiva](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)