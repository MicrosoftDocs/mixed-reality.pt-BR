---
title: Entrada MR 210 - olhar
description: Siga este passo a passo usando o Unity, o Visual Studio e o HoloLens para saber os detalhes de olhar conceitos de codificação.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, gaze
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993554"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

# <a name="mr-input-210-gaze"></a>Entrada MR 210: Focar

[Mantenha o foco](gaze.md) é o primeiro formulário de entrada e revela a intenção do usuário e o reconhecimento. MR entrada 210 (também conhecido como o Explorador de projeto) é uma Visão aprofundada conceitos relacionados ao olhar para a realidade mista do Windows. Vamos adicionar reconhecimento contextual para nosso cursor e hologramas, aproveitando ao máximo o que seu aplicativo sabe sobre olhar do usuário.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

Temos um astronaut amigável aqui para ajudá-lo a aprender os conceitos de olhar. Na [MR Noções básicas de 101](holograms-101.md), tínhamos um cursor simple que acabou de acessar seu foco. Hoje estamos movendo um passo além, o cursor simple:

* Estamos disponibilizando o cursor e nossa hologramas reconhecimento de olhar: ambos serão alteradas com base em onde o usuário está procurando - ou onde o usuário está *não* procurando. Isso os torna sensíveis ao contexto.
* Vamos adicionar comentários ao nosso cursor e hologramas dar mais contexto sobre o que está sendo direcionado ao usuário. Esses comentários podem ser áudio e vídeo.
* Mostraremos as técnicas de direcionamento para ajudar os usuários a atingir as metas menores.
* Mostraremos a você como chamar a atenção do usuário para seu hologramas com um indicador direcional.
* Podemos ensinam técnicas para aproveitar seu hologramas com o usuário conforme ela se move em todo o mundo.

>[!IMPORTANT]
>Os vídeos incorporados em cada um dos capítulos a seguir foram registrados usando uma versão mais antiga do Unity e o Kit de ferramentas de realidade mista. Enquanto as instruções passo a passo são precisas e atuais, você poderá ver scripts e visuais nos vídeos correspondentes que estão desatualizados. Os vídeos permanecem incluídos serão lidas depois e porque os conceitos abordados ainda se aplicam.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td>Entrada MR 210: Focar</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).
* Alguns basic C# capacidade de programação.
* Você deve ter concluído [MR Noções básicas de 101](holograms-101.md).
* Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Arquivos de projeto

* Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) exigidos pelo projeto. Requer o Unity 2017.2 ou posterior.
* Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).

### <a name="errata-and-notes"></a>Errata e notas

* No Visual Studio, "Apenas meu código" precisa ser desabilitado (desmarcado) em Ferramentas -> Opções -> depuração para usar pontos de interrupção em seu código.

## <a name="chapter-1---unity-setup"></a>Capítulo 1 - instalação do Unity

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>Objetivos

* Otimize o Unity para o desenvolvimento HoloLens.
* Importar ativos e configurar a cena.
* Exiba a astronautas no HoloLens.

### <a name="instructions"></a>Instruções

1. Inicie o Unity.
2. Selecione **novo projeto**.
3. Nomeie o projeto **ModelExplorer**.
4. Insira o local como o **olhares** pasta você anteriormente não arquivadas.
5. Verifique se o projeto é definido como **3D**.
6. Clique em **criar projeto**.

### <a name="unity-settings-for-hololens"></a>Configurações do Unity para HoloLens

Precisamos informar Unity que o aplicativo que estamos tentando exportar deve criar uma [exibição imersiva](app-views.md) em vez de uma exibição 2D. Fazemos isso adicionando o HoloLens como um dispositivo de realidade virtual.

1. Vá para **Editar > configurações do projeto > Player**.
2. No **painel Inspetor** para configurações do Player, selecione o **Windows Store** ícone.
3. Expanda o **XR configurações** grupo.
4. No **renderização** seção, verifique os **suporte de realidade Virtual** caixa de seleção para adicionar uma nova **SDKs de realidade Virtual** lista.
5. Verifique **Windows Mixed Reality** aparece na lista. Se não estiver, selecione a **+** botão na parte inferior da lista e escolha **Windows Holographic**.

Em seguida, precisamos definir o nosso script back-end para o .NET.

1. Vá para **Editar > configurações do projeto > Player** (você ainda poderá ter esse da etapa anterior).
2. No **painel Inspetor** para configurações do Player, selecione o **Windows Store** ícone.
3. No **outras configurações** configuração de seção, certifique-se de que **back-end de script** é definido como **.NET**

Por fim, atualizaremos nossas configurações de qualidade para alcançar um desempenho rápido em HoloLens.

1. Vá para **Editar > configurações do projeto > qualidade**.
2. Clique na seta apontando para baixo na **padrão** linha sob o ícone do Windows Store.
3. Selecione **muito baixa** para **aplicativos da Windows Store**.

### <a name="import-project-assets"></a>Importar ativos do projeto

1. Clique com botão direito do **ativos** pasta na **projeto** painel.
2. Clique em **Importar pacote > pacote personalizado**.
3. Navegue até os arquivos de projeto que você baixou e clique em **ModelExplorer.unitypackage**.
4. Clique em **Abrir**.
5. Depois que o pacote é carregado, clique no **importação** botão.

### <a name="setup-the-scene"></a>Instalação da cena

1. Na hierarquia, exclua o **câmera principal**.
2. No **HoloToolkit** pasta, abra o **entrada** pasta, em seguida, abra o **pré-fabricados** pasta.
3. Arrastar e soltar a **MixedRealityCameraParent** pré-fabricado da **pré-fabricados** pasta para o **hierarquia**.
4. Clique com botão direito do **luz direcional** na hierarquia e selecione **excluir**.
5. No **hologramas** pasta, arraste e solte os seguintes ativos na raiz do **hierarquia**:
    * **AstroMan**
    * **luzes**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. Inicie **reproduzir modo** ▶ para exibir a astronautas.
7. Clique em **modo de reprodução** ▶ novamente para **parar**.
8. No **hologramas** pasta, localizar o **Fitbox** ativo e arraste-o para a raiz do **hierarquia**.
9. Selecione o **Fitbox** na **hierarquia** painel.
10. Arraste o **AstroMan** coleção da **hierarquia** para o **holograma coleção** o Fitbox na propriedade o **Inspetor** painel.

### <a name="save-the-project"></a>Salve o projeto

1. Salve a nova cena: **Arquivo > Salvar cena como**.
2. Clique em **nova pasta** e nomeie a pasta **cenas**.
3. Nomeie o arquivo "**ModelExplorer**" e salve-o na **cenas** pasta.

### <a name="build-the-project"></a>Compile o projeto

1. No Unity, selecione **arquivo > configurações de Build**.
2. Clique em **cenas abra Adicionar** para adicionar a cena.
3. Selecione **plataforma Universal do Windows** na **plataforma** lista e clique em **alternar plataforma**.
4. Se você estiver desenvolvendo especificamente para HoloLens, defina **dispositivo de destino** à **HoloLens**. Caso contrário, deixe-nos **qualquer dispositivo**.
5. Certifique-se **Build Type** é definido como **D3D** e **SDK** é definido como **mais recente instalada** (que deve ser SDK 16299 ou mais recente).
6. Clique em **Compilar**.
7. Criar uma **nova pasta** chamado "App".
8. Único clique a **aplicativo** pasta.
9. Pressione **Selecionar pasta**.

Quando Unity é feito, será exibida uma janela do Explorador de arquivos.

1. Abra o **aplicativo** pasta.
2. Abra o **ModelExplorer Visual Studio Solution**.

Se a implantação para o HoloLens:

1. Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x86**.
2. Clique na lista suspensa na seta ao lado do botão de computador Local e selecione **computador remoto**.
3. Insira **seu endereço IP do dispositivo HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)**. Clique em **Selecionar**. Se você não souber o endereço IP do dispositivo, examine **Configurações > rede e Internet > Opções avançadas de**.
4. Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**. Se essa for a primeira vez em que implantar seu dispositivo, você precisará [emparelhá-lo com o Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Quando o aplicativo foi implantado, ignorar as **Fitbox** com um **selecione gesto**.

Se implantar em um fone de ouvido imersivo:

1. Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x64**.
2. Verifique se o destino de implantação é definido como **computador Local**.
3. Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.
4. Quando o aplicativo foi implantado, ignorar as **Fitbox** puxando o gatilho em um controlador de animação.

## <a name="chapter-2---cursor-and-target-feedback"></a>Capítulo 2 - comentários do Cursor e de destino

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>Objetivos

* Design visual do cursor e o comportamento.
* Comentários de cursor com base em olhar.
* Comentários de holograma com base em olhar.

Vamos basear nosso trabalho sobre alguns princípios de design de cursor, ou seja:

* O cursor está sempre presente.
* Não deixe que o cursor obter muito pequeno ou grande.
* Evite obstruindo o conteúdo.

### <a name="instructions"></a>Instruções

1. No **HoloToolkit\Input\Prefabs** pasta, localize a **InputManager** ativo.
2. Arraste e solte os **InputManager** até a **hierarquia**.
3. No **HoloToolkit\Input\Prefabs** pasta, localize a **Cursor** ativo.
4. Arraste e solte os **Cursor** até a **hierarquia**.
5. Selecione o **InputManager** do objeto na **hierarquia**.
6. Arraste o **Cursor** do objeto da **hierarquia** no InputManager **SimpleSinglePointerSelector**do **Cursor** no campo a parte inferior da **Inspetor**.

![Simples de configurar seletor único de ponteiro](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>Criar e implantar

1. Recompile o aplicativo do **arquivo > configurações de Build**.
2. Abra o **pasta aplicativo**.
3. Abra o **ModelExplorer Visual Studio Solution**.
4. Clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.
5. Observe como o cursor é desenhado, e como ela altera a aparência se ele está tocando um holograma.

### <a name="instructions"></a>Instruções

1. No **hierarquia** do painel, expanda o **AstroMan**->**GEO_G**->**Back_Center** objeto.
2. Clique duas vezes em **Interactible.cs** para abri-lo no Visual Studio.
3. Remova as linhas as **IFocusable.OnFocusEnter()** e **IFocusable.OnFocusExit()** retornos de chamada no **Interactible.cs**. Eles são chamados pelo InputManager do Toolkit de realidade misturada quando foco (seja por olhar ou apontando controlador) entra e sai do colisor do GameObject específico.

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
>Usamos `EnableKeyword` e `DisableKeyword` acima. Para fazer uso deles em seu próprio aplicativo com o sombreador de padrão do Kit de ferramentas, você precisará seguir as [diretrizes do Unity para acessar os materiais por meio de script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html). Nesse caso, estamos já incluiu o [três variantes do material realçado](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) necessários na pasta de recursos (procure os materiais com realce o nome de três).

### <a name="build-and-deploy"></a>Criar e implantar

1. Como antes, compile o projeto e implantar para o HoloLens.
2. Observar o que acontece quando a olhar destina-se a um objeto e quando ele não é.

## <a name="chapter-3---targeting-techniques"></a>Capítulo 3 - técnicas de direcionamento

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>Objetivos

* Torna mais fácil hologramas de destino.
* Estabilize naturais movimentos principais.

### <a name="instructions"></a>Instruções

1. No **hierarquia** painel, selecione o **InputManager** objeto.
2. No **Inspector** do painel, localize a **olhares estabilizador** script. Clique para abrir no Visual Studio, se você quiser dar uma olhada.
    * Esse script itera em amostras de dados Raycast e ajuda a se estabilizar olhar do usuário para o direcionamento de precisão.
3. No **Inspector**, você pode editar o **amostras de estabilidade armazenados** valor. Esse valor representa o número de amostras que itera o estabilizador para calcular o valor estabilizar.

## <a name="chapter-4---directional-indicator"></a>Capítulo 4 - indicadores direcionais

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>Objetivos

* Adicione um indicador direcional no cursor para ajudar a localizar hologramas.

### <a name="instructions"></a>Instruções

Vamos usar o **DirectionIndicator.cs** arquivo que será:

1. Mostra os indicadores direcionais se o usuário não é Observação nas hologramas.
2. Oculte os indicadores direcionais, se o usuário é Observação nas hologramas.
3. Atualize os indicadores direcionais para apontar para as hologramas.

Vamos começar.

1. Clique no **AstroMan** do objeto na **hierarquia** painel e **clique na seta** para expandi-lo.
2. No **hierarquia** painel, selecione o **DirectionalIndicator** objeto sob **AstroMan**.
3. No **Inspector** do painel, clique no **adicionar componente** botão.
4. No menu, digite na caixa de pesquisa **indicador de direção**. Selecione o resultado da pesquisa.
5. No **hierarquia** do painel, arraste e solte o **Cursor** do objeto para o **Cursor** propriedade no **Inspetor**.
6. No **projeto** painel, o **hologramas** pasta, arrastar e soltar os **DirectionalIndicator** ativo para o **indicadores direcionais**propriedade de **Inspetor**.
7. Crie e implante o aplicativo.
8. Assista como o objeto de indicadores direcionais ajuda a encontrar o astronaut.

## <a name="chapter-5---billboarding"></a>Capítulo 5 - Billboarding

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>Objetivos

* Use billboarding ter hologramas sempre enfrentam na sua direção.

Vamos usar o **Billboard.cs** arquivo para manter um GameObject orientado a, de modo que ele é voltado para o usuário em todos os momentos.

1. No **hierarquia** painel, selecione o **AstroMan** objeto.
2. No **Inspector** do painel, clique no **adicionar componente** botão.
3. No menu, digite na caixa de pesquisa **mural**. Selecione o resultado da pesquisa.
4. No **Inspector** definir os **eixo pivô** para **Y**.
5. Experimente! Crie e implante o aplicativo como antes.
6. Veja como o objeto mural faces, independentemente de como você pode alterar o ponto de vista.
7. Excluir o script a partir de **AstroMan** por enquanto.

## <a name="chapter-6---tag-along"></a>Capítulos 6 - Tag-Along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>Objetivos

* Use Tag-Along para nosso hologramas Siga-nos em torno da sala.

Enquanto trabalhamos sobre esse problema, podemos serão guiados pelas seguintes restrições de design:

* O conteúdo sempre deve ser rapidamente imediatamente.
* Conteúdo não deve ser da forma.
* O conteúdo de bloqueio de cabeça é desconfortável.

A solução usada aqui é usar uma abordagem de "tag-along".

Um objeto tag-along nunca totalmente sai do modo de exibição do usuário. Você pode considerar a um tag-along como sendo um objeto anexado a cabeça do usuário por elásticos. Quando o usuário move, o conteúdo permanecerá em um relance fácil deslizando em direção à extremidade da exibição sem sair completamente. Quando o usuário gazes para o objeto tag-along, se trata mais detalhadamente no modo de exibição.

Vamos usar o **SimpleTagalong.cs** arquivo que será:

1. Determine se o objeto Tag-Along está dentro dos limites de câmera.
2. Se não estiver na frustum modo de exibição, posicionar o Tag-Along para parcialmente na frustum modo de exibição.
3. Caso contrário, posicione o Tag-Along para uma distância padrão do usuário.

Para fazer isso, podemos primeiro deve alterar o **Interactible.cs** script para chamar o **TagalongAction**.

1. Edite **Interactible.cs** ao concluir a codificação Exercício 6.a (linhas 1&gt;{2&gt;suporte 84 para 87).

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

O **InteractibleAction.cs** script, emparelhado com **Interactible.cs** executa ações personalizadas quando você toca em hologramas. Nesse caso, usaremos um especificamente para tag-along.

* No **Scripts** pasta clique em **TagalongAction.cs** ativo para abrir no Visual Studio.
* Concluir o exercício de codificação ou alterá-la a este:
  * Na parte superior do **hierarquia**, no tipo de barra de pesquisa **ChestButton_Center** e selecione o resultado.
  * No **Inspector** do painel, clique no **adicionar componente** botão.
  * No menu, digite na caixa de pesquisa **que ação**. Selecione o resultado da pesquisa.
  * Na **hologramas** localizar pasta o ativo.  ****
  * Selecione o **ChestButton_Center** do objeto na **hierarquia**. Arrastar e soltar o  do objeto do **projeto** do painel para o **Inspetor** no **objeto** a que propriedade.  ****
  * Arraste o **que ação** do objeto do **Inspetor** no **ação Interactible** campo o **Interactible** script.
* Clique duas vezes o **TagalongAction** script para abri-lo no Visual Studio.

![Configuração interactible](images/holograms210-interactible.png)

Precisamos adicionar o seguinte:

* Adicione funcionalidade à função PerformAction no script TagalongAction (herdado de InteractibleAction).
* Adicione billboarding ao objeto gazed após e defina o eixo pivô para XY.
* Em seguida, adicione Tag-Along simple para o objeto.

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
* Assista como o conteúdo segue o centro do ponto de olhar, mas não é continuamente e sem bloquear a ele.
