---
title: Configurar um novo projeto do Unity para a realidade mista do Windows
description: Instruções sobre como configurar um projeto do Unity para o Windows Mixed Reality
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, realidade mista, desenvolvimento, introdução, novo projeto
ms.openlocfilehash: 64f7006bf212f49ab1c478d5dbb1fc1f5ab15497
ms.sourcegitcommit: 161f3c5a80f6988a9c4af26e29481fee06840e0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390093"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Configurar um novo projeto do Unity para a realidade mista do Windows 

## <a name="overview"></a>Visão geral

O Windows Mixed Reality (WMR) é uma plataforma da Microsoft introduzida como parte do sistema operacional Windows 10. A plataforma WMR permite que você crie aplicativos que processam conteúdo digital em dispositivos de vídeo Holographic e VR.

Ao configurar para WMR, há dois caminhos que você pode tomar. Sua primeira opção é instalar o MRTK ( [Kit de ferramentas de realidade mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) ) v2, que irá configurar automaticamente o ambiente WMR. A segunda opção é alterar manualmente algumas configurações de Unity para ficar sem interrupção com WMR. 

> [!NOTE]
> Você sempre pode importar MRTK posteriormente, portanto, não há penalidade para passar a rota manual primeiro.

Se você escolher a configuração manual do WMR, as configurações que você precisa alterar serão divididas em duas categorias: por projeto e por cena.

## <a name="per-project-settings"></a>Configurações por projeto

A primeira configuração que você precisa alterar para WMR é a plataforma do projeto: 
1. Selecione **arquivo > configurações de Build...**
2. Selecione **plataforma universal do Windows** na lista plataforma e clique em **alternar plataforma**
3. Definir o **SDK** como **Universal 10**
4. Definir o **dispositivo de destino** para **qualquer dispositivo** para dar suporte a headsets de imersão ou alternar para o **HoloLens**
5. Definir **tipo de compilação** como **D3D**
6. Definir o **SDK do UWP** para o **mais recente instalado**

![Configurações de Unity XR](images/unity-uwp-settings.png)<br>
*Configurações de Unity XR*

Depois que a plataforma estiver configurada corretamente, você precisará deixar que o Unity saiba que seu aplicativo deve criar uma [exibição imersiva](app-views.md) em vez de uma exibição 2D quando exportada:
1. Na janela **configurações de compilação...** , abra **as configurações do Player...**
2. Selecione a guia **configurações para plataforma universal do Windows** e expanda o grupo de **configurações XR**
3. Na seção **configurações de XR** , marque a caixa de seleção **suporte à realidade virtual** para adicionar a lista de **dispositivos de realidade virtual** .
4. No grupo de **configurações XR** , confirme se **"Windows Mixed Realm"** está listado como um dispositivo com suporte. (essa opção pode ser exibida como **Holographic do Windows** em versões mais antigas do Unity)

![Configurações de UWP do Unity](images/xrsettings.png)<br>
*Configurações de Unity XR*

### <a name="updating-the-manifest"></a>Atualizando o manifesto

Seu aplicativo agora pode manipular a renderização Holographic e a entrada espacial. No entanto, seu aplicativo precisa declarar os recursos apropriados em seu manifesto para aproveitar determinadas funcionalidades. Você pode encontrar os recursos de seus projetos acessando **configurações do Player > configurações para Plataforma Universal do Windows > configurações de publicação > recursos**. 

É recomendável que você faça as declarações de manifesto no Unity para incluí-las em todos os projetos futuros que você exportar. Os recursos aplicáveis para habilitar as APIs do Unity comumente usadas para realidade misturada são:

|  Funcionalidade  |  APIs que exigem capacidade | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (acesso a malhas de [mapeamento espacial](spatial-mapping.md) no HoloLens) &mdash; *nenhum recurso necessário para acompanhamento espacial geral do headset* | 
|  Integrada  |  VideoCapture e fotocaptura | 
|  PicturesLibrary / VideosLibrary  |  VideoCapture, respectivamente (ao armazenar o conteúdo capturado) | 
|  Microfone  |  VideoCapture (ao capturar áudio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e para usar o criador de perfil do Unity) | 

### <a name="quality-settings"></a>Configurações de qualidade

O HoloLens tem uma GPU de classe móvel. Se seu aplicativo estiver direcionando para o HoloLens, você desejará que as configurações de qualidade em seu aplicativo sejam ajustadas para um desempenho mais rápido, a fim de garantir que ela mantenha a taxa completa de quadros:
1. Selecione **Editar configurações do projeto > > qualidade**
2. Selecione o **menu suspenso** sob o logotipo da **Windows Store** e selecione **muito baixo**. Você saberá que a configuração terá sido aplicada corretamente quando a caixa na coluna Windows Store e na linha **Muito Baixa** estiver verde.

![Configurações de qualidade do Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Configurações de qualidade do Unity*

## <a name="per-scene-settings"></a>Configurações por cena

### <a name="unity-camera-settings"></a>Configurações da câmera do Unity

Com a **realidade virtual suportada** marcada, o componente da [câmera do Unity](camera-in-unity.md) lida com o [controle de cabeçalho e a renderização de estereoscópico](rendering.md). Isso significa que não há necessidade de substituir o objeto da câmera principal por uma câmera personalizada.

Se seu aplicativo estiver direcionando para o HoloLens especificamente, você precisará alterar algumas configurações para otimizar para as exibições transparentes do dispositivo. Essas configurações permitem que o conteúdo do Holographic seja mostrado ao mundo físico:
1. Na **hierarquia**, selecione a **câmera principal**
2. No painel de **inspetores** , defina a **posição** de transformação como **0, 0,** portanto, o local da cabeça do usuário começa na origem do Unity World.
3. Alterar **sinalizadores claros** para **cor sólida**.
4. Altere a cor do **plano de fundo** para **RGBA 0, 0, 0, 0**. O preto é renderizado como transparente no HoloLens.
5. Alterar os **planos de recorte-próximo** ao [HoloLens recomendado](camera-in-unity.md#clip-planes) 0,85 (metros).

![Configurações da câmera do Unity](images/Unitycamerasettings.png)<br>
*Configurações da câmera do Unity*

> [!IMPORTANT]
> Se você excluir e criar uma nova câmera, verifique se a nova câmera está marcada como **MainCamera**.

## <a name="see-also"></a>Confira também
* [Kit de Ferramentas de Realidade Misturada v2](mrtk-getting-started.md)
* [Visão geral do desenvolvimento do Unity](unity-development-overview.md)
