---
title: Configurar um novo projeto do Unity para a realidade mista do Windows
description: configurar projeto do Unity sem MRTK
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, realidade mista, desenvolvimento, introdução, novo projeto
ms.openlocfilehash: 99c72f2d9d900c8a05fb7d8b9b8de10d657fdd13
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502647"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Configurar um novo projeto do Unity para a realidade mista do Windows 

(pule se você já importou o MRTK v2 para seu projeto do Unity)

Se você quiser criar um novo projeto do Unity sem importar o kit de ferramentas de realidade misturada, há um pequeno conjunto de configurações de Unity que você precisará alterar manualmente para a realidade mista do Windows, dividida em duas categorias: por projeto e por cena.

## <a name="per-project-settings"></a>Configurações por projeto

Para direcionar a realidade mista do Windows, primeiro você precisa definir seu projeto do Unity para exportar como um aplicativo Plataforma Universal do Windows: 
1. Selecione **arquivo > configurações de Build...**
2. Selecione **plataforma universal do Windows** na lista plataforma e clique em **alternar plataforma**
3. Definir o **SDK** como **Universal 10**
4. Definir o **dispositivo de destino** para **qualquer dispositivo** para dar suporte a headsets de imersão ou alternar para o **HoloLens**
5. Definir **tipo de compilação** como **D3D**
6. Definir o **SDK do UWP** para o **mais recente instalado**

Em seguida, você precisa deixar que o Unity saiba que o aplicativo que você está tentando exportar deve criar uma [exibição de imersão](app-views.md) em vez de uma exibição 2D. Você faz isso habilitando a "realidade virtual com suporte":
1. Na janela **configurações de compilação...** , abra **as configurações do Player...**
2. Selecione a guia **configurações para plataforma universal do Windows**
3. Expandir o grupo de **configurações XR**
4. Na seção **configurações de XR** , marque a caixa de seleção **suporte à realidade virtual** para adicionar a lista de **dispositivos de realidade virtual** .
5. No grupo de **configurações XR** , confirme se **"Windows Mixed Realm"** está listado como um dispositivo com suporte. (isso pode aparecer como "Windows Holographic" em versões mais antigas do Unity)

![configurações de qualidade do Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Configurações de Unity XR*

Seu aplicativo agora pode fazer a renderização Holographic básica e a entrada espacial. Para ir além e aproveitar determinadas funcionalidades, seu aplicativo deve declarar os recursos apropriados em seu manifesto. As declarações de manifesto podem ser feitas no Unity para que elas sejam incluídas em todas as exportações de projeto subsequentes. As configurações são encontradas nas configurações **do Player > configurações para Plataforma Universal do Windows > configurações de publicação > recursos**. Os recursos aplicáveis para habilitar as APIs do Unity comumente usadas para realidade misturada são:

|  Capacidade  |  APIs que exigem capacidade | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (acesso a malhas de [mapeamento espacial](spatial-mapping.md) no HoloLens)&mdash;*nenhum recurso necessário para acompanhamento espacial geral do headset* | 
|  Integrada  |  VideoCapture e fotocaptura | 
|  PicturesLibrary / VideosLibrary  |  VideoCapture, respectivamente (ao armazenar o conteúdo capturado) | 
|  Microfone  |  VideoCapture (ao capturar áudio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e para usar o criador de perfil do Unity) | 

**Configurações de qualidade do Unity**

![configurações de qualidade do Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Configurações de qualidade do Unity*

O HoloLens tem uma GPU de classe móvel. Se seu aplicativo estiver direcionando para o HoloLens, você desejará que as configurações de qualidade sejam ajustadas para um desempenho mais rápido para garantir que mantemos a taxa de quadros completa
1. Selecione **Editar configurações do projeto > > qualidade**
2. Selecione o **menu suspenso** sob o logotipo da **Windows Store** e selecione **muito baixo**. Você saberá que a configuração é aplicada corretamente quando a caixa na coluna da Windows Store e a linha **muito baixa** estiverem verdes.

## <a name="per-scene-settings"></a>Configurações por cena

**Configurações da câmera do Unity**

![configurações da câmera do Unity](images/Unitycamerasettings.png)<br>
*Configurações da câmera do Unity*

Depois de habilitar a caixa de seleção "realidade virtual com suporte", o componente [câmera do Unity](camera-in-unity.md) lida com o [controle de cabeçalho e a renderização estereoscópico](rendering.md). Não é necessário substituí-lo por uma câmera personalizada para fazer isso.

Se seu aplicativo estiver direcionando para o HoloLens especificamente, há algumas configurações que precisam ser alteradas para otimizar para as exibições transparentes do dispositivo, para que seu aplicativo seja exibido ao mundo físico:
1. Na **hierarquia**, selecione a **câmera principal**
2. No painel de **inspetores** , defina a **posição** de transformação como **0, 0,** portanto, o local da cabeça do usuário começa na origem do Unity World.
3. Alterar **sinalizadores claros** para **cor sólida**.
4. Altere a cor do **plano de fundo** para **RGBA 0, 0, 0, 0**. O preto é renderizado como transparente no HoloLens.
5. Alterar os **planos de recorte-próximo** ao [HoloLens recomendado](camera-in-unity.md#clip-planes) 0,85 (metros).

Se você excluir e criar uma nova câmera, verifique se a câmera está **marcada** como **MainCamera**.


## <a name="see-also"></a>Veja também
* [Kit de Ferramentas de Realidade Misturada v2](mrtk-getting-started.md)
* [Visão geral do desenvolvimento do Unity](unity-development-overview.md)
