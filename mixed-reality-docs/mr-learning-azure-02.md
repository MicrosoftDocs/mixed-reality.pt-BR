---
title: Tutoriais de Nuvem do Azure – 2. Integrar o armazenamento do Azure
description: Conclua este curso para aprender a implementar o Armazenamento de Tabelas do Azure e o Armazenamento de Blobs do Azure em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, hololens 2, azure storage
ms.localizationpriority: high
ms.openlocfilehash: a8d91bc55b3ce73d6e1fb46e5d696d853adcf871
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376468"
---
# <a name="2-integrating-azure-storage"></a>2. Integrar o armazenamento do Azure

Neste tutorial, você aprenderá a salvar dados de entidade no armazenamento de Tabela do Azure e imagens em miniatura no Armazenamento de Blobs do Azure. Esse recurso nos permitirá armazenar e recuperar *Objetos Rastreados* com os dados como ID, Nome, Imagem em Miniatura etc. entre sessões e dispositivos na nuvem.

## <a name="objectives"></a>Objetivos

* Aprender os conceitos básicos sobre o armazenamento do Azure
* Saber como armazenar, modificar e recuperar dados do armazenamento de Tabelas
* Saber como armazenar e excluir imagens do armazenamento de Blobs

## <a name="understanding-azure-storage"></a>Noções básicas sobre o armazenamento do Azure

O **armazenamento do Azure** é uma solução de armazenamento da Microsoft na nuvem que pode abranger vários cenários e requisitos. Ele é massivamente escalonável e facilmente acessível pelos desenvolvedores. Todos os serviços podem ser consumidos no âmbito de **Conta de armazenamento do Azure**. Para nosso caso de uso, usaremos o *Armazenamento de Tabelas* e o *Armazenamento de Blobs*.

Saiba mais sobre os [serviços de armazenamento do Azure](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview).

### <a name="azure-table-storage"></a>Armazenamento de Tabela do Azure

Esses serviços nos permitem armazenar dados em NoSQL; neste projeto, usaremos o serviço para armazenar informações sobre o *Objeto Rastreado* como: nome, descrição, ID de âncora espacial e muito mais.

No contexto do aplicativo de demonstração, você precisa de duas tabelas, uma para armazenar informações sobre o projeto com informações sobre o estado dos modelos treinados – saiba mais sobre isso no tutorial ([Integrar a Visão Personalizada do Azure](mr-learning-azure-03.md)) – e uma segunda tabela para armazenar informações sobre *Objetos Rastreados*.

Saiba mais sobre [Armazenamento de Tabelas do Azure](https://docs.microsoft.com/azure/storage/tables/table-storage-overview).

### <a name="azure-blob-storage"></a>Armazenamento de Blobs do Azure

Esse serviço permite armazenar arquivos binários grandes; você usará isso para armazenar fotos tiradas para *Objetos Rastreados* como miniaturas.
Para o aplicativo de demonstração, você precisa de um Contêiner de Blob para armazenar as imagens.

Saiba mais sobre [Armazenamento de Blobs do Azure](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction).

## <a name="preparing-azure-storage"></a>Preparação do Armazenamento do Azure

Para consumir os serviços de armazenamento do Azure, você precisará de uma conta de armazenamento do Azure. Para criar uma conta de armazenamento, consulte [Criar uma conta de armazenamento](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal). Para saber mais sobre contas de armazenamento, confira [Visão geral de conta de armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-account-overview).

Quando você tiver uma conta de armazenamento, recupere a cadeia de conexão no **portal do Azure**, pois será necessária na próxima seção desta lição.

### <a name="optional-azure-storage-explorer"></a>Gerenciador de Armazenamento do Azure opcional

Embora você possa ver e verificar todas as alterações de dados na interface do usuário dentro do aplicativo, é recomendável instalar o [Gerenciador de armazenamento do Azure](https://azure.microsoft.com/features/storage-explorer/). Essa ferramenta permite que você visualize os dados no armazenamento do Azure e é muito útil durante a depuração e o aprendizado.

> [!TIP]
> Para testar dentro do editor do Unity, você pode usar um emulador local:

> * no Windows 10, use o [Emulador de armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-use-emulator)
> * no MacOS/Linux, use a [Imagem do Docker Azurite](https://hub.docker.com/_/microsoft-azure-storage-azurite) para o Docker

## <a name="preparing-the-scene"></a>Preparando a cena

Na janela Hierarquia, localize o objeto **DataManager** e selecione-o.

![mr-learning-azure](images/mr-learning-azure/tutorial2-section4-step1-1.png)

Na janela Inspetor, você verá que o componente **DataManager (script)** é o local em que todas as configurações relacionadas ao **armazenamento do Azure** são mantidas. Todas as configurações relevantes já estão definidas, você só precisa substituir o campo *Cadeia de Conexão*, por aquele que pode ser recuperado no portal do Azure. Se você estiver usando uma solução de emulador de armazenamento local do Azure, mantenha a *Cadeia de Conexão* já fornecida.

O **DataManager (script)** é responsável por se comunicar com o **Armazenamento de tabela** e o **Armazenamento de blobs** que é consumido por outros scripts de controlador nos componentes da interface do usuário.

## <a name="writing-and-reading-data-from-azure-table-storage"></a>Gravando e lendo dados no armazenamento de Tabela do Azure

Com tudo preparado, é hora de criar um *Objeto Rastreado*.

Abra o aplicativo no seu HoloLens, clique em **Definir Objeto** e você verá como o objeto *EnterObjectName* se tornará ativo na hierarquia. Nesse menu, clique na *barra de pesquisa* e digite o nome que você deseja dar ao *Objeto Rastreado*. Depois de fornecer um nome, clique no botão **Definir objeto**. Isso criará o *Objeto Rastreado* no armazenamento de Tabela do Azure e você verá agora o **Cartão de Objeto**.

Este **Cartão de Objeto** é uma representação de interface do usuário do *Objeto Rastreado* e terá uma função importante várias vezes nesta série de tutoriais.

Agora, clique na *caixa de texto* de descrição e digite "Car"; depois, clique no botão **Salvar** para salvar as alterações. Interrompa o aplicativo e execute-o novamente.

Agora, clique em **Pesquisar Objeto** e digite na *barra de pesquisa* o nome que você usou ao criar o *Objeto Rastreado*. Você verá que o **Cartão de Objeto** com todos os dados será recuperado do **armazenamento de Tabela do Azure**.

Sinta-se à vontade para fechar o **Cartão de Objeto** e criar novos *Objetos Rastreados* e editar seus dados.

> [!TIP]
> Se você instalou o [Gerenciador de Armazenamento do Azure](https://azure.microsoft.com/features/storage-explorer/), examine a tabela de *objetos* e verá o *Objeto Rastreado* criado.

## <a name="uploading-and-download-image-from-azure-blob-storage"></a>Carregar e baixar a imagem no Armazenamento de blobs do Azure

Nesta seção, você usará o armazenamento de blobs do Azure para carregar e baixar imagens que serão usadas como miniaturas para *Objetos Rastreados*.

> [!NOTE]
> Neste tutorial, o aplicativo vai tirar fotos para carregar imagens no Armazenamento de blobs. Se você estiver executando isso localmente no editor do Unity, tenha uma webcam conectada ao seu computador.

Abra o aplicativo no seu HoloLens, clique em **Definir Objeto** e digite o nome "Car" na *barra de pesquisa*. Agora você verá o **Cartão de Objeto**; clique no botão **Câmera** e será instruído a fazer um AirTap para tirar uma foto. Depois de tirar uma foto, você verá uma mensagem informando sobre o carregamento ativo e, depois de um tempo, a imagem aparecerá no local em que o espaço reservado estava antes.

Agora, execute novamente o aplicativo e pesquise o *Objeto Rastreado*; a imagem carregada anteriormente deverá aparecer como miniatura.

## <a name="deleting-image-from-azure-blob-storage"></a>Excluir imagem do Armazenamento de blobs do Azure

Na seção anterior, você carregou novas imagens no Armazenamento de blobs do Azure; nesta seção, você excluirá uma miniatura de imagem dos *Objetos Rastreados*.

Abra o aplicativo no seu HoloLens, clique em **Definir Objeto** e digite o nome "Car" na *barra de pesquisa*. Agora verá o **Cartão de Objeto** com a imagem em miniatura; clique no botão **Excluir**. Você observará que a imagem em miniatura será substituída pela imagem do espaço reservado.

Agora, execute novamente o aplicativo e pesquise o *Objeto Controlado* da miniatura excluída anteriormente. Você só verá a imagem do espaço reservado.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu como os serviços de armazenamento do Azure podem ser usados para persistir dados não estruturados, como em nosso caso **Objetos Rastreados** e binários na forma de imagens em miniatura para o aplicativo de demonstração do **HoloLens 2** na nuvem.

No próximo tutorial, você aprenderá a usar a Visão Personalizada do Azure para detectar imagens associadas a um *Objeto Rastreado*.

[Próximo tutorial: 3. Integrar a Visão Personalizada do Azure](mr-learning-azure-03.md)
