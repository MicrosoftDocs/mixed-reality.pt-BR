---
title: Tutoriais de introdução – 8. Como usar o acompanhamento de olho
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 31552cba9a68d1f1214395dbf4e4ed84ecd3f388
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376598"
---
# <a name="8-using-eye-tracking"></a>8. Como usar o acompanhamento de olho

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a habilitar o acompanhamento de olho para o HoloLens 2 e a adicionar acompanhamento de olho a objetos para disparar ações quando o usuário examina os objetos.

> [!NOTE]
> Se você também estiver implantando esse projeto no HoloLens (1ª geração), observe que o acompanhamento de olho só tem suporte no HoloLens 2.

## <a name="objectives"></a>Objetivos

* Saiba como habilitar o acompanhamento de olho para o HoleLens 2
* Saiba como usar o acompanhamento de olho para disparar ações

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Como garantir que a funcionalidade de Entrada de Foco de Olho esteja habilitada

No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade de Entrada de Foco de Olho** está esmaecida:

![mr-learning-base](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> A funcionalidade de Entrada de Foco deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) quando você configurou o projeto do Unity no início desta série de tutoriais. No entanto, se não estiver habilitada, faça isso agora.

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Como habilitar o foco baseado em olho no provedor de foco

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, na janela Inspetor, selecione a guia MixedRealityToolkit > **Entrada** e execute as seguintes etapas:

* Clone o **DefaultHoloLens2InputSystemProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_HoloLens2InputSystemProfile_
* Expandir a seção **Ponteiros**
* Clone o **DefaultMixedRealityPointerProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_MixedRealityPointerProfile_
* Localize a seção **Configurações de Foco** e marque a caixa de seleção **Acompanhamento de Olho Está Habilitado**

![mr-learning-base](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> Para lembrar como clonar perfis de MRTK, consulte as instruções em [Configurando os perfis do MRTK](mr-learning-base-03.md).

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>Como habilitar o controle de olho simulado para o editor do Unity

Na janela hierarquia, selecione o objeto **MixedRealityToolkit** e, em seguida, na janela Inspetor, navegue até a guia **Entrada** e, em seguida:

* Expanda a seção **Provedores de Dados de Entrada** > **Serviço de Simulação de Entrada**
* Clone o **DefaultMixedRealityInputSimulationProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_MixedRealityInputSimulationProfile_
* Localize a seção **Simulação de Olho** e marque a caixa de seleção **Simular Posição do Olho**

![mr-learning-base](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>Como adicionar acompanhamento de olho a objetos

Na janela Hierarquia, expanda o objeto RoverExplorer > **Botões** e, para cada um dos três objetos de botão filho, expanda e selecione o objeto SeeItSayItLabel > **TextMeshPro**:

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-1.png)

Com os três objetos TextMeshPro ainda selecionados, na janela Inspetor, use o botão **Adicionar Componente** para adicionar os seguintes componentes a todos os objetos selecionados:

* Componente **Colisor de Caixa**
* Componente **EyeTrackingTarget**

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-2.png)

Na janela Hierarquia, selecione o objeto **Dicas** > SeeItSayItLabel > **TextMeshPro** e configure o componente **EyeTrackingTarget** da seguinte maneira:

* Na seção de evento **On Look At Start ()**
  * Clique no ícone pequeno **+** para adicionar outro evento
  * Atribua o objeto em si, ou seja, o mesmo objeto **TextMeshPro** ao campo **Nenhum (Objeto)**
  * Na lista suspensa **Sem Função**, selecione **TextMeshPro** > **float fontSize** para atualizar esse valor da propriedade quando o evento for disparado
  * Defina o argumento como **0,06** para aumentar o tamanho da fonte atual de 0,04 em 50%
* Na seção de evento **On Look Away ()**
  * Clique no ícone pequeno **+** para adicionar outro evento
  * Atribua o objeto em si, ou seja, o mesmo objeto **TextMeshPro** ao campo **Nenhum (Objeto)**
  * Na lista suspensa **Sem Função**, selecione **TextMeshPro** > **float fontSize** para atualizar esse valor da propriedade quando o evento for disparado
  * Defina o argumento como **0,04** para redefinir o tamanho da fonte de volta para 0,04

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-3.png)

**Repita** esta etapa para o objeto **Explodir** > SeeItSayItLabel > **TextMeshPro** e o objeto **Redefinir** > SeeItSayItLabel > **TextMeshPro**.

Se agora você entrar no modo de Jogo e pressionar e manter o botão direito do mouse enquanto move o mouse até que o foco atinja um dos rótulos, verá o tamanho da fonte aumentar em 50% e ser redefinido de volta ao seu tamanho original ao desviar o olhar:

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a habilitar o acompanhamento de olho para o HoloLens 2 e a adicionar acompanhamento de olho a objetos para disparar ações quando o usuário examina os objetos.

[Próximo tutorial: 9. Usando comandos de fala](mr-learning-base-09.md)