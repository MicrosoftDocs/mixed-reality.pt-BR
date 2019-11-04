---
title: Entrada MR 210-olhar
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes dos conceitos de olhar.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, olhar
ms.openlocfilehash: 8608701a1dd0a9a20aede1737d16d5af2e715f6b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434687"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

# <a name="mr-input-210-gaze"></a>Entrada MR 210: olhar

[Olhar](gaze-and-commit.md) é a primeira forma de entrada e revela a intenção e a conscientização do usuário. A entrada MR 210 (também conhecida como explorador de projeto) é aprofundada nos conceitos relacionados ao olhar para a realidade mista do Windows. Adicionaremos reconhecimento contextual ao cursor e aos hologramas, aproveitando ao máximo o que seu aplicativo sabe sobre o olhar do usuário.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

Temos um Astronaut amigável aqui para ajudá-lo a aprender os conceitos de olhar. No [Sr basics 101](holograms-101.md), tínhamos um simples cursor que logo seguiu o olhar. Hoje, estamos movendo uma etapa além do cursor simples:

* Estamos fazendo com que o cursor e nossos hologramas olhar: ambos mudarão de acordo com o local em que o usuário está olhando ou para onde o usuário *não* está olhando. Isso faz com que eles reconheçam o contexto.
* Vamos adicionar comentários ao cursor e aos hologramas para dar ao usuário mais contexto sobre o que está sendo direcionado. Esses comentários podem ser áudio e Visual.
* Mostraremos as técnicas de direcionamento para ajudar os usuários a atingirem destinos menores.
* Mostraremos como atrair a atenção do usuário para seus hologramas com um indicador direcional.
* Ensinaremos técnicas para levar seus hologramas com o usuário quando ele se movimentar em seu mundo.

>[!IMPORTANT]
>Os vídeos inseridos em cada um dos capítulos abaixo foram registrados usando uma versão mais antiga do Unity e o kit de ferramentas do Mixed Reality. Embora as instruções passo a passo sejam precisas e atuais, você pode ver scripts e visuais nos vídeos correspondentes que estão desatualizados. Os vídeos permanecem incluídos para posterity e porque os conceitos abordados ainda se aplicam.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Entrada MR 210: olhar</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md).
* Alguma capacidade C# básica de programação.
* Você deve ter concluído o [Sr noções básicas 101](holograms-101.md).
* Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) exigidos pelo projeto. Requer o Unity 2017,2 ou posterior.
* Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).

### <a name="errata-and-notes"></a>Errata e observações

* No Visual Studio, "Apenas Meu Código" precisa ser desabilitado (desmarcado) em Ferramentas-> Opções-> depuração para acessar os pontos de interrupção no código.

## <a name="chapter-1---unity-setup"></a>Capítulo 1 – configuração do Unity

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>Objetivos

* Otimizar o Unity para o desenvolvimento no HoloLens.
* Importar ativos e configurar a cena.
* Exiba o Astronaut no HoloLens.

### <a name="instructions"></a>Instruções

1. Inicie o Unity.
2. Selecione **novo projeto**.
3. Nomeie o projeto **ModelExplorer**.
4. Insira o local como a pasta **olhar** que você cancelou anteriormente.
5. Verifique se o projeto está definido como **3D**.
6. Clique em **Criar Projeto**.

### <a name="unity-settings-for-hololens"></a>Configurações de Unity para o HoloLens

Precisamos deixar que o Unity saiba que o aplicativo que estamos tentando exportar deve criar uma [exibição imersiva](app-views.md) em vez de uma exibição 2D. Fazemos isso adicionando o HoloLens como um dispositivo de realidade virtual.

1. Vá para **Editar configurações de projeto > > Player**.
2. No **painel Inspetor** para configurações do Player, selecione o ícone **Windows Store** .
3. Expanda o grupo de **configurações XR** .
4. Na seção **renderização** , marque a caixa de seleção **suporte à realidade virtual** para adicionar uma nova lista de **SDKs de realidade virtual** .
5. Verifique se a **realidade mista do Windows** aparece na lista. Caso contrário, selecione o botão **+** na parte inferior da lista e escolha **Windows Holographic**.

Em seguida, precisamos definir nosso back-end de script para .NET.

1. Vá para **Editar configurações de projeto > > Player** (talvez você ainda tenha isso na etapa anterior).
2. No **painel Inspetor** para configurações do Player, selecione o ícone **Windows Store** .
3. Na seção configuração de **outras configurações** , verifique se o **back-end de script** está definido como **.net**

Por fim, atualizaremos nossas configurações de qualidade para obter um desempenho rápido no HoloLens.

1. Vá para **Editar configurações de projeto > > qualidade**.
2. Clique na seta apontando para baixo na linha **padrão** no ícone Windows Store.
3. Selecione **muito baixo** para **aplicativos da Windows Store**.

### <a name="import-project-assets"></a>Importar ativos de projeto

1. Clique com o botão direito do mouse na pasta **ativos** no painel **projeto** .
2. Clique em **Importar pacote > pacote personalizado**.
3. Navegue até os arquivos de projeto que você baixou e clique em **ModelExplorer. unitypackage**.
4. Clique em **Abrir**.
5. Depois que o pacote for carregado, clique no botão **importar** .

### <a name="setup-the-scene"></a>Configurar a cena

1. Na hierarquia, exclua a **câmera principal**.
2. Na pasta **HoloToolkit** , abra a pasta de **entrada** e, em seguida, abra a pasta **pré-fabricados** .
3. Arraste e solte o **MixedRealityCameraParent** pré-fabricado da pasta **pré-fabricados** para a **hierarquia**.
4. Clique com o botão direito do mouse na **luz direcional** na hierarquia e selecione **excluir**.
5. Na pasta **hologramas** , arraste e solte os seguintes ativos na raiz da **hierarquia**:
    * **AstroMan**
    * **Noturna**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. Inicie o **modo de reprodução** ▶ para exibir o Astronaut.
7. Clique em **modo de reprodução** ▶ novamente para **parar**.
8. Na pasta **hologramas** , localize o ativo **Fitbox** e arraste-o para a raiz da **hierarquia**.
9. Selecione o **Fitbox** no painel **hierarquia** .
10. Arraste a coleção **AstroMan** da **hierarquia** para a propriedade de **coleção de holograma** do Fitbox no painel de **Inspetor** .

### <a name="save-the-project"></a>Salvar o projeto

1. Salve a nova cena: **arquivo > salvar cena como**.
2. Clique em **nova pasta** e nomeie a pasta **cenas**.
3. Nomeie o arquivo como "**ModelExplorer**" e salve-o na pasta de **cenas** .

### <a name="build-the-project"></a>Compilar o projeto

1. No Unity, selecione **arquivo > configurações de Build**.
2. Clique em **Adicionar abrir cenas** para adicionar a cena.
3. Selecione **plataforma universal do Windows** na lista **plataforma** e clique em **alternar plataforma**.
4. Se você estiver desenvolvendo especificamente para o HoloLens, defina o **dispositivo de destino** para o **hololens**. Caso contrário, deixe em **qualquer dispositivo**.
5. Verifique se **tipo de compilação** está definido como **D3D** e se o **SDK** está definido para o **mais recente instalado** (que deve ser o SDK 16299 ou mais recente).
6. Clique em **Compilar**.
7. Crie uma **nova pasta** chamada "app".
8. Clique uma vez na pasta do **aplicativo** .
9. Pressione **Selecionar pasta**.

Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.

1. Abra a pasta do **aplicativo** .
2. Abra a **solução ModelExplorer do Visual Studio**.

Se estiver implantando no HoloLens:

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.
2. Clique na seta suspensa ao lado do botão computador local e selecione **computador remoto**.
3. Insira **o endereço IP do dispositivo de HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)** . Clique em **Selecionar**. Se você não souber o endereço IP do dispositivo, examine **configurações > rede & Internet > opções avançadas**.
4. Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**. Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com o Visual Studio](using-visual-studio.md#pairing-your-device).
5. Quando o aplicativo tiver sido implantado, ignore o **Fitbox** com um **gesto de seleção**.

Se estiver implantando em um headset de imersão:

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x64**.
2. Verifique se o destino de implantação está definido como **computador local**.
3. Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.
4. Quando o aplicativo tiver sido implantado, ignore o **Fitbox** puxando o gatilho em um controlador de movimento.

## <a name="chapter-2---cursor-and-target-feedback"></a>Capítulo 2-comentários de cursor e destino

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>Objetivos

* Design e comportamento do Visual do cursor.
* Comentários do cursor baseado em olhar.
* Comentários sobre o holograma baseado em olhar.

Vamos basear nosso trabalho em alguns princípios de design de cursor, ou seja:

* O cursor está sempre presente.
* Não deixe o cursor ficar muito pequeno ou grande.
* Evite obstruir o conteúdo.

### <a name="instructions"></a>Instruções

1. Na pasta **HoloToolkit\Input\Prefabs** , localize o ativo **InputManager** .
2. Arraste e solte o **InputManager** na **hierarquia**.
3. Na pasta **HoloToolkit\Input\Prefabs** , localize o ativo de **cursor** .
4. Arraste e solte o **cursor** na **hierarquia**.
5. Selecione o objeto **InputManager** na **hierarquia**.
6. Arraste o objeto **cursor** da **hierarquia** para o campo de **cursor** do **SimpleSinglePointerSelector**da InputManager, na parte inferior do **Inspetor**.

![Configuração do seletor de ponteiro único simples](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>Compilar e implantar

1. Recompile o aplicativo do **arquivo > configurações de Build**.
2. Abra a **pasta do aplicativo**.
3. Abra a **solução ModelExplorer do Visual Studio**.
4. Clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.
5. Observe como o cursor é desenhado e como ele muda de aparência se estiver tocando em um holograma.

### <a name="instructions"></a>Instruções

1. No painel **hierarquia** , expanda o **AstroMan**->**GEO_G**->objeto **Back_Center** .
2. Clique duas vezes em **Interactible.cs** para abri-lo no Visual Studio.
3. Remova os comentários das linhas nos retornos de chamada **IFocusable. OnFocusEnter ()** e **IFocusable. OnFocusExit ()** em **Interactible.cs**. Eles são chamados pelo InputManager do kit de ferramentas da realidade misturada quando o foco (por olhar ou por controlador apontando) entra e sai do colisor do Jogoobject específico.

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>Usamos `EnableKeyword` e `DisableKeyword` acima. Para fazer uso deles em seu próprio aplicativo com o sombreador padrão do kit de ferramentas, você precisará seguir as [diretrizes do Unity para acessar materiais por meio de script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html). Nesse caso, já incluímos as [três variantes do material realçado](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) necessário na pasta de recursos (procure os três materiais com realce no nome).

### <a name="build-and-deploy"></a>Compilar e implantar

1. Como antes, compile o projeto e implante-o no HoloLens.
2. Observe o que acontece quando o olhar é direcionado a um objeto e quando não é.

## <a name="chapter-3---targeting-techniques"></a>Capítulo 3-técnicas de direcionamento

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>Objetivos

* Facilite o direcionamento de hologramas.
* Estabilizar movimentos de cabeça natural.

### <a name="instructions"></a>Instruções

1. No painel **hierarquia** , selecione o objeto **InputManager** .
2. No painel **Inspetor** , localize o script de **estabilizador olhar** . Clique para abrir no Visual Studio, se você quiser dar uma olhada.
    * Esse script itera sobre exemplos de dados do Raycast e ajuda a estabilizar o olhar do usuário para direcionamento de precisão.
3. No **Inspetor**, você pode editar o valor das **amostras de estabilidade armazenadas** . Esse valor representa o número de amostras que o estabilizador itera para calcular o valor estabilizado.

## <a name="chapter-4---directional-indicator"></a>Capítulo 4 – Indicador direcional

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>Objetivos

* Adicione um indicador direcional no cursor para ajudar a encontrar hologramas.

### <a name="instructions"></a>Instruções

Vamos usar o arquivo **DirectionIndicator.cs** , que:

1. Mostre o indicador direcional se o usuário não estiver nuvens nos hologramas.
2. Oculte o indicador direcional se o usuário estiver nuvensndo nos hologramas.
3. Atualize o indicador direcional para apontar para os hologramas.

Vamos começar.

1. Clique no objeto **AstroMan** no painel **hierarquia** e **clique na seta** para expandi-lo.
2. No painel **hierarquia** , selecione o objeto **DirectionalIndicator** em **AstroMan**.
3. No painel **Inspetor** , clique no botão **Adicionar componente** .
4. No menu, digite o **indicador de direção**da caixa de pesquisa. Selecione o resultado da pesquisa.
5. No painel **hierarquia** , arraste e solte o objeto **cursor** na propriedade **cursor** no **Inspetor**.
6. No painel **projeto** , na pasta **hologramas** , arraste e solte o ativo **DirectionalIndicator** para a propriedade **Indicador direcional** no **Inspetor**.
7. Crie e implante o aplicativo.
8. Observe como o objeto indicador direcional ajuda a localizar o Astronaut.

## <a name="chapter-5---billboarding"></a>Capítulo 5 – mural

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>Objetivos

* Use a mensagem para que os hologramas sempre se enfrentem para você.

Usaremos o arquivo **Billboard.cs** para manter um gameobject orientado para que ele esteja sempre voltado ao usuário.

1. No painel **hierarquia** , selecione o objeto **AstroMan** .
2. No painel **Inspetor** , clique no botão **Adicionar componente** .
3. No menu, digite o **mural**da caixa de pesquisa. Selecione o resultado da pesquisa.
4. No **Inspetor** , defina o **eixo dinâmico** como **Y**.
5. Experimente! Crie e implante o aplicativo como antes.
6. Veja como o objeto do mural o rostos não importa como você altera o ponto de vista.
7. Exclua o script do **AstroMan** por enquanto.

## <a name="chapter-6---tag-along"></a>Capítulo 6-marcar como

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>Objetivos

* Use a marca – junto com nossos hologramas nos seguem pela sala.

À medida que trabalharmos com esse problema, iremos ser guiado pelas seguintes restrições de design:

* O conteúdo deve ser sempre um breve resumido.
* O conteúdo não deve estar no caminho.
* O conteúdo de bloqueio de cabeça é desconfortável.

A solução usada aqui é usar uma abordagem de "marca".

Um objeto de marca-ao mesmo nunca deixa totalmente a exibição do usuário. Você pode considerar uma marca como sendo um objeto anexado à cabeça do usuário por faixas de borracha. À medida que o usuário se move, o conteúdo permanecerá dentro de uma visão fácil, deslizando para a borda da exibição sem sair completamente. Quando o usuário gazes em direção ao objeto de marca, ele é mais totalmente na exibição.

Vamos usar o arquivo **SimpleTagalong.cs** , que:

1. Determine se o objeto de marca está dentro dos limites da câmera.
2. Se não estiver dentro da exibição frustum, posicione a marca-junto com parcialmente dentro da exibição frustum.
3. Caso contrário, posicione a marca-junto com uma distância padrão do usuário.

Para fazer isso, primeiro devemos alterar o script **Interactible.cs** para chamar o **TagalongAction**.

1. Edite **Interactible.cs** concluindo o código exercício 6. a (removendo as linhas de comentário 84 a 87).

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

O script **InteractibleAction.cs** , emparelhado com **Interactible.cs** , executa ações personalizadas quando você toca em hologramas. Nesse caso, usaremos um especificamente para a marca.

* Na pasta **scripts** , clique em ativo **TagalongAction.cs** para abrir no Visual Studio.
* Conclua o exercício de codificação ou altere-o para:
  * Na parte superior da **hierarquia**, na barra de pesquisa, digite **ChestButton_Center** e selecione o resultado.
  * No painel **Inspetor** , clique no botão **Adicionar componente** .
  * No menu, digite a **ação que**da caixa de pesquisa. Selecione o resultado da pesquisa.
  * Na pasta **hologramas** , localize o ativo **que** .
  * Selecione o objeto **ChestButton_Center** na **hierarquia**. Arraste e solte o objeto **que** do painel **projeto** para o **Inspetor** na propriedade **objeto para que** .
  * Arraste o objeto de **ação que** do **Inspetor** para o campo de **ação Interactible** no script **Interactible** .
* Clique duas vezes no script **TagalongAction** para abri-lo no Visual Studio.

![Configuração do Interactible](images/holograms210-interactible.png)

Precisamos adicionar o seguinte:

* Adicione funcionalidade à função performaaction no script TagalongAction (Herdado de InteractibleAction).
* Adicione a mensagem ao objeto gazed e defina o eixo dinâmico como XY.
* Em seguida, adicione uma marca simples-junto ao objeto.

Aqui está nossa solução, de **TagalongAction.cs**:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* Experimente! Crie e implante o aplicativo.
* Observe como o conteúdo segue o centro do ponto de olhar, mas não continuamente e sem bloqueá-lo.
