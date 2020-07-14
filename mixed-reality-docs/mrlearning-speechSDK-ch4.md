---
title: Tutoriais de Serviços de Fala do Azure – 4. Como configurar a intenção e o reconhecimento vocal natural
description: Conclua este curso para saber como implementar o SDK de Fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8cebe1fb203aeed9a262a2e9f482993b4775e0a6
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303657"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. Como configurar a intenção e o reconhecimento vocal natural

Neste tutorial, você vai explorar o reconhecimento de intenção do Serviço de Fala do Azure. O reconhecimento de intenção permite que você equipe o aplicativo com comandos de fala com IA, em que os usuários podem dizer comandos de fala não específicos e ainda ter sua intenção compreendida pelo sistema.

## <a name="objectives"></a>Objetivos

* Saiba como configurar intenção, entidades e enunciados no portal do LUIS
* Saiba como implementar a intenção e o reconhecimento vocal natural em nosso aplicativo

## <a name="preparing-the-scene"></a>Preparando a cena

Na janela Hierarquia, selecione o objeto **Lunarcom** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Reconhecedor de Intenção do Lunarcom (Script)** ao objeto Lunarcom:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutoriais.GettingStarted** > **Pré-fabricados** > **RocketLauncher**, arraste o pré-fabricado **RocketLauncher_Complete** para a janela Hierarquia e coloque-o em uma localização adequada na frente da câmera, por exemplo:

* **Posição** da Transformação X = 0, Y = -0,4, Z = 1
* **Rotação** da Transformação X = 0, Y = 90, Z = 0

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

Na janela Hierarquia, selecione o objeto **Lunarcom** novamente e, em seguida, expanda o objeto **RocketLauncher_Complete** > **Botão** e atribua a cada um dos botões filho do objeto **Botões** ao campo **Botões do Iniciador Lunar** correspondente:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a>Como criar o recurso de Reconhecimento vocal do Azure

Nesta seção, você criará um recurso de previsão do Azure para o aplicativo LUIS (Serviço Inteligente de Reconhecimento vocal) que será criado na próxima seção.

Entre no <a href="https://portal.azure.com" target="_blank">Azure</a> e clique em **Criar um recurso**. Em seguida, pesquise e selecione **Reconhecimento vocal**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

Clique no botão **Criar** para criar uma instância desse serviço:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

Na página Criar, clique na opção **Previsão** e insira os seguintes valores:

* Para **Assinatura**, selecione **Avaliação Gratuita** se você tiver uma assinatura de avaliação, caso contrário, selecione uma das outras assinaturas
* Para o **Grupo de recursos**, clique no link **Criar**, insira um nome adequado, por exemplo, *MRKT-Tutoriais* e, em seguida, clique em **OK**

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> No momento da redação deste artigo, você não precisa criar um recurso de criação porque uma chave de avaliação de criação será gerada automaticamente no LUIS quando você criar o LUIS (Serviço Inteligente de Reconhecimento vocal) na próxima seção.

> [!TIP]
> Se você já tiver outro grupo de recursos adequado em sua conta do Azure, por exemplo, se tiver concluído o tutorial [Âncoras Espaciais do Azure](mr-learning-asa-01.md), poderá usar esse grupo de recursos em vez de criar um.

Enquanto ainda estiver na página Criar, insira os seguintes valores:

* Para **Nome**, insira um nome adequado para o serviço, por exemplo, *MRTK-Tutoriais-AzureSpeechServices*
* Para **Localização de previsão**, escolha uma localização próxima à localização física dos usuários do seu aplicativo, por exemplo, *(EUA) Oeste dos EUA*
* Para **Tipo de preço de previsão**, para os fins deste tutorial, selecione **F0 (cinco chamadas por segundo, dez mil chamadas por mês)**

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

Em seguida, vá para a guia **Examinar + criar**, examine os detalhes e clique no botão **Criar**, localizado na parte inferior da página, para criar o recurso, bem como no novo grupo de recursos se você tiver configurado um para ser criado:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> Depois de clicar no botão Criar, você precisará aguardar até que o serviço seja criado, o que poderá levar alguns minutos.

Depois que o processo de criação de recursos for concluído, você verá a mensagem **Sua implantação foi concluída**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a>Como criar o LUIS (Serviço Inteligente de Reconhecimento Vocal)

Nesta seção, você criará um aplicativo LUIS, configurará e treinará seu modelo de previsão e o conectará ao recurso de previsão do Azure criado na etapa anterior.

Especificamente, você criará uma intenção de que, se o usuário disser que uma ação deve ser executada, o aplicativo disparará o evento Interactable.OnClick() em um dos três botões vermelhos na cena, dependendo de a qual botão o usuário faz referência.

Por exemplo, se o usuário disser **ir em frente e lançar o foguete**, o aplicativo preverá que **vá em frente** significa que algumas **ações** devem ser executadas e que o evento Interactable.OnClick() para o **destino** está no botão **lançar**.

As principais etapas que você seguirá para conseguir isso são:

1. Criar um aplicativo LUIS
2. Criar intenções
3. Criar exemplos de enunciados
4. Criar entidades
5. Atribuir entidades a exemplos de enunciados
6. Treinar, testar e publicar o aplicativo
7. Atribuir um recurso de previsão do Azure ao aplicativo

### <a name="1-create-a-luis-app"></a>1. Criar um aplicativo LUIS

Usando a mesma conta de usuário usada ao criar o recurso do Azure na seção anterior, entre no <a href="https://www.luis.ai" target="_blank">LUIS</a>, selecione seu país/região e concorde com os Termos de uso. Na próxima etapa, quando você for solicitado a **Vincular sua conta do Azure**, escolha **Continuar usando sua chave de avaliação** para usar um recurso de criação do Azure em vez disso.

> [!NOTE]
> Se você já se inscreveu no LUIS e sua chave de avaliação de criação expirou, pode ver a documentação [Migrar para uma chave de criação de recursos do Azure](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) para alternar o recurso de criação do LUIS para o Azure.

Depois de conectado, navegue até a página **Meus aplicativos**, clique em **Criar aplicativo** e insira os seguintes valores na janela pop-up **Criar aplicativo**:

* Para **Nome**, insira um nome adequado, por exemplo, *Tutoriais do MRTK – AzureSpeechServices*
* Para **Cultura**, selecione **Inglês**
* Para **Descrição**, opcionalmente, insira uma descrição adequada

Em seguida, clique no botão **Concluído** para criar o aplicativo:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

Quando o aplicativo tiver sido criado, você será levado para a página **Painel** desse aplicativo:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a>2. Criar intenções

Na página Painel, navegue até a página Criar > Ativos de Aplicativo > **Intenções**, clique em **Criar intenção** e insira o seguinte valor na janela pop-up **Criar intenção**:

* Para **Nome da intenção**, insira **PressButton**

Em seguida, clique no botão **Concluído** para criar a intenção:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> Para os fins deste tutorial, seu projeto do Unity fará referência a essa intenção por seu nome, ou seja, 'PressButton'. Assim, é extremamente importante que você dê à sua intenção um nome exatamente igual.

Quando a intenção for criada, você será levado para a página dessa intenção:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a>3. Criar exemplos de enunciados

Para a lista **Enunciado de exemplo** da intenção **PressButton**, adicione os seguintes enunciados de exemplo:

* ativar sequência de inicialização
* mostrar-me uma dica de posicionamento
* iniciar a sequência de inicialização
* pressionar o botão de dicas de posicionamento
* dê-me uma dica
* pressione o botão iniciar
* preciso de uma dica
* pressione o botão redefinir
* tempo para redefinir a experiência
* Ir em frente e lançar o foguete

Quando todos os enunciados de exemplo tiverem sido adicionados, sua página de intenção de PressButton deverá ser semelhante a esta:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> Para os fins deste tutorial, seu projeto do Unity fará referência às palavras "dica", "dicas", "redefinir" e "iniciar". Assim, é extremamente importante que você escreva essas palavras exatamente da mesma maneira.

### <a name="4-create-entities"></a>4. Criar entidades

Na página de intenção PressButton, navegue até a página Criar > Ativos de Aplicativo > **Entidades** e clique em **Criar entidade**, então insira os seguintes valores na janela pop-up **Criar entidade**:

* Para **Nome da entidade**, insira **Ação**
* Para **Tipo de entidade**, selecione **Simples**

Em seguida, clique no botão **Concluído** para criar a entidade:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

**Repita** a etapa anterior para criar outra entidade chamada **Destino** para que você tenha duas entidades chamadas Ação e Destino:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> Para os fins deste tutorial, seu projeto do Unity fará referência a essas entidades pelo nome, ou seja, "Ação" e "Alvo". Assim, é extremamente importante que você dê às suas entidades um nome exatamente igual.

### <a name="5-assign-entities-to-the-example-utterances"></a>5. Atribuir entidades a exemplos de enunciados

Na página entidades, navegue de volta para a página de intenção de **PressButton**.

Depois de voltar para a página de intenção de PressButton, clique na palavra **ir** e, em seguida, na palavra **em frente** e selecione **Ação (Simples)** no menu pop-up contextual para rotular **ir em frente** como um valor de entidade de **Ação**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

A frase **ir em frente** frase agora é definida como um valor de entidade de **Ação**. Se você passar o cursor do mouse sobre o nome da entidade de Ação, poderá ver o valor da entidade de Ação associada:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> A linha vermelha que você vê sob o rótulo na imagem acima indica que o valor da entidade não foi previsto. Isso será resolvido quando você treinar o modelo na próxima seção.

Em seguida, clique na palavra **iniciar** e, em seguida, selecione **Destino (Simples)** no menu pop-up contextual para rotular **iniciar** como um valor de entidade de **destino**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

A palavra **iniciar** agora está definida como um valor de entidade de **Destino**. Se você passar o cursor do mouse sobre o nome da entidade de Destino, poderá ver o valor da entidade de Destino associada:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

O enunciado de exemplo de intenção PressButton "ir em frente e lançar o foguete" agora está configurado para ser previsto da seguinte maneira:

* Intenção: PressButton
* Entidade de ação: vá em frente
* Entidade de destino: iniciar

**Repita** o processo anterior de duas etapas para atribuir uma ação e um rótulo de entidade de Destino a cada um dos exemplos de enunciado, tendo em mente que as seguintes palavras devem ser rotuladas como entidades de **Destino**:

* **dica** (tem como destino HintsButton no projeto do Unity)
* **dicas** (tem como destino HintsButton no projeto do Unity)
* **redefinir** (tem como destino ResetButton no projeto do Unity)
* **iniciar** (tem como destino LaunchButton no projeto do Unity)

Quando todos os enunciados de exemplo tiverem sido rotulados, sua página de intenção de PressButton deverá ser semelhante a esta:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

Como alternativa para verificar novamente se você atribuiu as entidades corretas, clique no menu **Exibir opções** e alterne a exibição para **Mostrar valores de entidade**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

Agora, com o modo de exibição definido para mostrar valores de entidade, você pode focalizar o curso do mouse sobre as palavras e frases rotuladas para verificar rapidamente o nome da entidade atribuída:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a>6. Treinar, testar e publicar o aplicativo

Para treinar o aplicativo, clique no botão **Treinar** e aguarde a conclusão do processo de treinamento:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> Como você pode ver na imagem acima, as linhas vermelhas em todos os rótulos foram removidas, indicando que todos os valores de entidade foram previstos. Observe também que o ícone de status à esquerda do botão Treinar mudou a cor de vermelho para verde.

Quando o processamento do treinamento for concluído, clique no botão **Testar**, digite **ir em frente e lançar o foguete** e pressione a tecla Enter:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

Quando o enunciado de teste tiver sido processado, clique em **Inspecionar** para ver o resultado do teste:

* Intenção: PressButton (com uma certeza de 98,5%)
* Entidade de ação: vá em frente
* Entidade de destino: iniciar

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

Para publicar o aplicativo, clique no botão **Publicar** no canto superior direito e, em seguida, na janela **Escolher o slot e as configurações de publicação**, selecione **Produção** e clique no botão **Publicar**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

Aguarde a conclusão do processo de publicação:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a>7. Atribuir um recurso de previsão do Azure ao aplicativo

Navegue até a página Gerenciar > Configurações do Aplicativo > **Recursos do Azure**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

Na página Recursos do Azure, clique no botão **Adicionar recurso de previsão** e selecione os seguintes valores na janela pop-up **Atribuir um recurso ao aplicativo**:

* Para **Nome do locatário**, selecione o nome do locatário
* Para **Nome da assinatura**, selecione a mesma assinatura que você usou anteriormente ao [Criar o recurso de Reconhecimento vocal do Azure](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)
* Para **Nome de recurso LUIS**, selecione o recurso de previsão que você criou anteriormente ao [Criar o recurso de Reconhecimento vocal do Azure](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)

Em seguida, clique no botão **Atribuir recurso** para atribuir o recurso de previsão do Azure ao seu aplicativo:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

Quando o recurso tiver sido atribuído, sua página de recursos do Azure deverá ser semelhante a esta:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a>Como conectar o projeto do Unity ao aplicativo LUIS

Na página Gerenciar > Configurações do Aplicativo > **Recursos do Azure**, clique no ícone **copiar** para copiar a **Consulta de Exemplo**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

De volta ao seu projeto do Unity, na janela Hierarquia, selecione o objeto **Lunarcom** e, em seguida, na janela Inspetor, localize o componente **Lunarcom do Reconhecedor de Intenção (Script)** e configure-o da seguinte maneira:

* No campo **Ponto de Extremidade LUIS**, após a **Consulta de Exemplo** que você copiou na etapa anterior:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a>Como testar e aprimorar o reconhecimento de intenção

Para usar o reconhecimento de intenção diretamente no editor do Unity, você deve permitir que seu computador de desenvolvimento use ditado. Para verificar essa configuração, abra as **Configurações** do Windows e escolha **Privacidade** > **Fala** e garanta que **Reconhecimento de fala online** esteja ativado:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

Se agora você entrar no modo de Jogo, poderá testar o reconhecimento de intenção pressionando primeiro o botão foguete. Em seguida, supondo que o computador tenha um microfone, quando você disser o primeiro enunciado de exemplo, **ir em frente e lançar o foguete**, você verá o lançamento do LunarModule no espaço:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

Experimente todos os **enunciados de exemplo**, então algumas **variações dos enunciados de exemplo**, bem como alguns **enunciados aleatórios**.

Em seguida, retorne para <a href="https://www.luis.ai" target="_blank">LUIS</a> e navegue para a página Criar > Aprimorar o desempenho do aplicativo > **Examinar enunciados do ponto de extremidade**, use o botão de **alternância** para alternar da Exibição de Entidades padrão para **Exibição de Tokens** e, em seguida, examine os enunciados:

* Na coluna **Enunciado**, altere e remova os rótulos atribuídos conforme necessário para que eles se alinhem com a sua intenção
* Na coluna **Intenção alinhada**, verifique se a intenção está correta
* Na coluna **Adicionar/Excluir**, clique no botão de marca de seleção verde para adicionar o enunciado ou o botão x vermelho para excluí-lo

Quando você tiver examinado o número de enunciados que desejar, clique no botão **Treinar** para treinar novamente o modelo e, em seguida, no botão **Publicar** para republicar o aplicativo atualizado:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> Se um enunciado do ponto de extremidade não se alinhar com a intenção PressButton, mas você quiser que seu modelo saiba que o enunciado não tem nenhuma intenção, poderá alterar a intenção Alinhada para Nenhum.

**Repita** esse processo quantas vezes desejar para aprimorar seu modelo de aplicativo.

## <a name="congratulations"></a>Parabéns

Seu projeto agora tem comandos de fala habilitados para IA, permitindo que seu aplicativo reconheça a intenção dos usuários, mesmo que eles não enunciem comandos precisos. Execute o aplicativo em seu dispositivo para garantir que o recurso esteja funcionando corretamente.
