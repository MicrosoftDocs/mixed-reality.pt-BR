---
title: Tutoriais de introdução – 9. Usando comandos de fala
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: ed31c3b11497a0adc91b7ddc1c09b3fb4ca1c573
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303963"
---
# <a name="9-using-speech-commands"></a>9. Usando comandos de fala

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a criar comandos de fala e a controlá-los globalmente. Você também aprenderá a controlar os comandos de fala locais que exigem que o usuário examine o objeto que controla o comando de fala.

## <a name="objectives"></a>Objetivos

* Saber como criar comandos de fala
* Aprender a controlar comandos de fala globalmente e localmente

## <a name="ensuring-the-microphone-capability-is-enabled"></a>Garantir que a funcionalidade do Microfone esteja habilitada

No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade do Microfone** está esmaecida:

![mr-learning-base](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> A funcionalidade do Microfone deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) quando você configurou o projeto do Unity no início desta série de tutoriais. No entanto, se não estiver habilitada, faça isso agora.

## <a name="creating-speech-commands"></a>Criando comandos de fala

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, na janela Inspetor, selecione a guia MixedRealityToolkit > **Entrada** e execute as seguintes etapas:

* Expanda a seção **Fala**
* Clone o **DefaultMixedRealitySpeechCommandsProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_MixedRealitySpeechCommandsProfile_
* Verifique se o **Comportamento de Inicialização** está definido como **Iniciar Automaticamente**

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> Para lembrar como clonar perfis de MRTK, consulte as instruções em [Configurando os perfis do MRTK](mr-learning-base-03.md).

Na seção Fala > **Comandos de Fala**, clique no botão **+ Adicionar um Novo Comando de Fala** quatro vezes para adicionar quatro novos comandos de fala à lista de comandos de fala existentes e, em seguida, nos campos **Palavra-Chave** digite as seguintes frases:

* Habilitar Indicador
* Habilitar Toque para Posicionar
* Habilitar Caixa Delimitadora
* Desabilitar Caixa Delimitadora

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> Se o computador não tiver um microfone, atribua um KeyCode aos comandos de fala, o que lhe permitirá dispará-los quando a tecla correspondente for pressionada.

## <a name="controlling-speech-commands"></a>Controlar comandos de fala

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK** > **SDK** > **Recursos** > **UX** > **Pré-fabricados** > **Dica de Ferramenta** para localizar os pré-fabricados de dica de ferramenta:

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-1.png)

Na janela Hierarquia, clique com o botão direito do mouse em um ponto vazio e selecione **Criar Vazio** para adicionar um objeto vazio à sua cena.

Nomeie o objeto como **SpeechInputHandler_Global** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **SpeechInputHandler** e configure-o da seguinte maneira:

* **Desmarque** a caixa de seleção **Foco É Necessário** para que os usuários não precisem examinar o objeto com o componente SpeechInputHandler para disparar o comando de fala
* Na janela Projeto, atribua o pré-fabricado **SpeechConfirmation Tooltip** ao campo **Speech Confirmation Tooltip Prefab**, para que esse pré-fabricado seja exibido quando um comando de fala for reconhecido

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-2.png)

No componente SpeechInputHandler, clique no ícone de pequeno **+** três vezes para adicionar três elementos de palavra-chave:

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-3.png)

Expanda **Elemento 0** e configure-o da seguinte maneira:

* No campo **Palavra-chave**, digite **Habilitar Indicador** para fazer referência ao comando de fala Habilitar Indicador criado na seção anterior
* Clique no ícone pequeno **+** para adicionar um evento
* Na janela Hierarquia, atribua o objeto **Indicador** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **GameObject** > **SetActive (bool)** para definir essa função como a ação a ser executada quando o evento for disparado
* Verifique se a caixa de seleção de argumento está **marcada**

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-4.png)

Expanda **Elemento 1** e configure-o da seguinte maneira:

* No campo **Palavra-chave**, digite **Habilitar Caixa Delimitadora** para fazer referência ao comando de fala Habilitar Caixa Delimitadora criado na seção anterior
* Clique no ícone pequeno **+** para adicionar um evento
* Na janela Hierarquia, atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **BoundingBox** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção de argumento está **marcada**
* Clique no ícone pequeno **+** para adicionar outro evento
* Na janela Hierarquia, atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção de argumento está **marcada**

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-5.png)

Expanda **Elemento 2** e configure-o da seguinte maneira:

* No campo **Palavra-chave**, digite **Desabilitar Caixa Delimitadora** para fazer referência ao comando de fala Desabilitar Caixa Delimitadora criado na seção anterior
* Clique no ícone pequeno **+** para adicionar um evento
* Na janela Hierarquia, atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **BoundingBox** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **desmarcada**
* Clique no ícone pequeno **+** para adicionar outro evento
* Na janela Hierarquia, atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **desmarcada**

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-6.png)

Na janela hierarquia, selecione o objeto RoverExplorer > **RoverAssembly** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **SpeechInputHandler** e configure-o da seguinte maneira:

* Verifique se a caixa de seleção **Foco É Necessário** está **marcada** para que os usuários precisem examinar o objeto com o componente SpeechInputHandler, ou seja, o RoverAssembly, para disparar o comando de fala
* Na janela Projeto, atribua o pré-fabricado **SpeechConfirmation Tooltip** ao campo **Speech Confirmation Tooltip Prefab**, para que esse pré-fabricado seja exibido quando um comando de fala for reconhecido

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-7.png)

No componente SpeechInputHandler, clique no ícone pequeno **+** para adicionar um elemento de palavra-chave. Expanda o elemento recém-criado e configure-o da seguinte maneira:

* No campo **Palavra-chave**, digite **Habilitar Toque para Posicionar** para fazer referência ao comando de fala Habilitar Toque para Posicionar criado na seção anterior
* Clique no ícone pequeno **+** para adicionar um evento
* Na janela Hierarquia, atribua o objeto em si, ou seja, o mesmo objeto **RoverAssembly** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **TapToPlace** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção de argumento está **marcada**

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a criar comandos de fala e a controlá-los globalmente. Você também aprendeu a controlar os comandos de fala locais que exigem que o usuário examine o objeto que controla o comando de fala.

Isso também conclui a série de [Tutoriais de introdução](mr-learning-base-01.md). Por meio desses tutoriais, você criou com êxito uma experiência de realidade misturada completa do zero usando o MRTK.

Na próxima duas série de tutoriais, [Tutoriais de Âncoras Espaciais do Azure](mr-learning-asa-01.md) e [Tutoriais de funcionalidades de vários usuários](mr-learning-sharing-01.md), você aprenderá primeiro a integrar Âncoras Espaciais do Azure em seu projeto para ancorar a experiência do Rover Explorer criada no mundo real. Em seguida, você aprenderá a adicionar recursos de vários usuários ao seu projeto para compartilhar movimentações de usuários e objetos em tempo real.
