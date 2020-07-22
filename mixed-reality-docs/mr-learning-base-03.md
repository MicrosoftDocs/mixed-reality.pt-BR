---
title: Tutoriais de introdução – 3. Como configurar os perfis do MRTK
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2c413964a435814275a1b908770ca977412f92be
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304154"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Como configurar os perfis do MRTK

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a personalizar e configurar os perfis do MRTK.

Este exemplo específico mostrará como ocultar a malha de reconhecimento espacial alterando as configurações do Observador de Malha Espacial. No entanto, você pode seguir esses mesmos princípios para personalizar qualquer configuração ou valor nos perfis do MRTK.

## <a name="objectives"></a>Objetivos

* Saiba como personalizar e configurar perfis do MRTK
* Ocultar a malha de reconhecimento espacial

## <a name="changing-the-spatial-awareness-display-option"></a>Como alterar a opção de exibição de reconhecimento espacial

As principais etapas que você seguirá para ocultar a malha de reconhecimento espacial são:

1. Clonar o perfil de configuração padrão
2. Habilitar o Sistema de Reconhecimento Espacial
3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão
4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão
5. Altere a visibilidade da malha de reconhecimento espacial

> [!NOTE]
> Por padrão, os perfis do MRTK não são editáveis. Esses são modelos de perfil padrão que você precisa clonar antes que eles possam ser editados. Há várias camadas aninhadas de perfis. Portanto, é comum clonar e editar vários perfis ao definir uma ou mais configurações.

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonar o perfil de configuração padrão

> [!NOTE]
> O perfil de configuração é o perfil de nível superior. Assim, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, altere o Perfil de Configuração do **MixedRealityToolkit** para o **DefaultHoloLens2ConfigurationProfile**:

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-1.png)

Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique no botão **Copiar e Personalizar** para abrir a janela Clonar Perfil:

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_HoloLens2ConfigurationProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultHololens2ConfigurationProfile**:

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

Agora, o Perfil de Configuração recém-criado é atribuído como o Perfil de Configuração para sua cena:

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

No menu do Unity, selecione **Arquivo** > **Salvar** para salvar sua cena.

> [!TIP]
> Lembre-se de salvar seu trabalho ao longo dos tutoriais.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Habilitar o Sistema de Reconhecimento Espacial

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, selecione a guia **Reconhecimento Espacial** e marque a caixa de seleção **Habilitar o Sistema de Reconhecimento Espacial**:

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão

Na guia **Reconhecimento Espacial**, clique no botão **Clonar** para abrir a janela Clonar Perfil:

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

O Perfil do Sistema de Reconhecimento Espacial recém-criado agora é atribuído automaticamente ao seu Perfil de Configuração:

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão

Com a guia **Reconhecimento Espacial** ainda selecionada, expanda a seção **Observador de Malha Espacial do Windows Mixed Reality** e clique no botão **Clonar** para abrir a janela Clonar Perfil:

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

O Perfil de Observador de Malha de Reconhecimento Espacial recém-criado agora é automaticamente atribuído ao seu Perfil do Sistema de Reconhecimento Espacial:

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Altere a visibilidade da malha de reconhecimento espacial

Em **Configurações do Observador de Malha Espacial**, altere a **Opção de Exibição** para **Oclusão** para tornar a malha de mapeamento espacial invisível, mas ainda funcional:

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional. Por exemplo, os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.

Você acabou de aprender como modificar uma configuração do perfil do MRTK. Como você pode ver, para personalizar as configurações de MRTK, primeiro é necessário criar cópias dos perfis padrão. Como os perfis padrão não são editáveis, você sempre os terá como referência se quiser reverter para as configurações padrão. Para saber mais sobre os perfis do MRTK e sua arquitetura, você pode consultar o [Guia de configuração do perfil do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a clonar, personalizar e definir uma configurações e perfis do MRTK.

[Próximo tutorial: 4. Como posicionar objetos na cena](mr-learning-base-04.md)
