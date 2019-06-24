---
title: Configurar um novo projeto do Unity para Windows Mixed Reality
description: Configurar o projeto do Unity sem MRTK
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, misturadas realidade, desenvolvimento, introdução, novo projeto
ms.openlocfilehash: 68dded9d0fc9e861bdda56c4954d72ddafafa686
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326099"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Configurar um novo projeto do Unity para Windows Mixed Reality 

(ignore se você já importou MRTK v2 para seu projeto do Unity)

Se você deseja ter criado um novo projeto do Unity sem importar o Kit de ferramentas de realidade misturada, há um pequeno conjunto de configurações de Unity, você precisará alterar manualmente para o Windows Mixed Reality, dividido em duas categorias: por projeto e por cena.

## <a name="per-project-settings"></a>As configurações por projeto

Para direcionar o Windows Mixed Reality, primeiro você precisa definir seu projeto do Unity para exportar como um aplicativo da plataforma Universal do Windows: 
1. Selecione **arquivo > configurações de Build...**
2. Selecione **plataforma Universal do Windows** na plataforma de lista e clique em **alternar plataforma**
3. Definir **SDK** para **10 Universal**
4. Definir **dispositivo de destino** à **qualquer dispositivo** para dar suporte a fones imersivos em exposição ou alternar para **HoloLens**
5. Definir **tipo de compilação** para **D3D**
6. Definir **UWP SDK** para **mais recente instalada**

Em seguida, precisamos informar Unity que o aplicativo que estamos tentando exportar deve criar uma [exibição imersiva](app-views.md) em vez de uma exibição 2D. Podemos fazer isso habilitando o "Suporte de realidade Virtual":
1. Do **configurações de Build...**  janela, abra **configurações do Player...**
2. Selecione o **configurações para a plataforma Universal do Windows** guia
3. Expanda o **XR configurações** grupo
4. No **configurações XR** seção, verifique o **suporte de realidade Virtual** caixa de seleção para adicionar o **dispositivos de realidade Virtual** lista.
5. No **configurações XR** grupo, confirme se **"Windows Mixed Reality"** está listado como um dispositivo com suporte. (Isso pode aparecer como "Windows Holographic" em versões mais antigas do Unity)

![Configurações de qualidade do Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Configurações do Unity xr*

Seu aplicativo agora pode fazer a renderização holográfica básica e entrada espacial. Para ir adiante e tirar proveito de determinada funcionalidade, seu aplicativo deve declarar os recursos apropriados em seu manifesto. As declarações de manifesto podem ser feitas no Unity para que sejam incluídos em cada exportação projeto subsequente. A configuração são encontradas no **Player Configurações > configurações para a plataforma Universal do Windows > configurações de publicação > recursos**. Os recursos aplicáveis para habilitar APIs do Unity usados para realidade misturada são:

|  Capacidade  |  APIs que exigem a capacidade | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (acesso a [mapeamento espacial](spatial-mapping.md) malhas em HoloLens)&mdash;*nenhum recurso necessário para o rastreamento espacial geral de fone de ouvido* | 
|  WebCam  |  PhotoCapture e VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  PhotoCapture ou VideoCapture, respectivamente (ao armazenar o conteúdo capturado) | 
|  Microfone  |  VideoCapture (durante a captura de áudio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e usar o Profiler Unity) | 

**Configurações de qualidade do Unity**

![Configurações de qualidade do Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Configurações de qualidade do Unity*

HoloLens tem uma GPU de classe móvel. Se seu aplicativo for destinado ao HoloLens, você desejará as configurações de qualidade ajustadas para desempenho mais rápido para garantir que podemos manter a taxa de quadros completa:
1. Selecione **Editar > configurações do projeto > qualidade**
2. Selecione o **lista suspensa** sob o **Windows Store** logotipo e selecione **muito baixa**. Você saberá que a configuração seja aplicada corretamente quando a caixa na coluna Windows Store e **muito baixa** linha está verde.

## <a name="per-scene-settings"></a>Configurações por cena

**Configurações de câmera do Unity**

![Configurações de câmera do Unity](images/Unitycamerasettings.png)<br>
*Configurações de câmera do Unity*

Depois de habilitar a caixa de seleção "Suporte de realidade Virtual", o [Unity câmera](camera-in-unity.md) identificadores de componente [head acompanhamento e renderização estereoscópica](rendering.md). Não é necessário substituí-lo com uma câmera personalizada para fazer isso.

Se seu aplicativo for direcionado especificamente o HoloLens, há algumas configurações que precisam ser alteradas para otimizar para monitores de transparente do dispositivo, para que seu aplicativo será exibido através ao mundo físico:
1. No **hierarquia**, selecione o **câmera principal**
2. No **Inspector** do painel, defina a transformação **posição** para **0, 0, 0** para que o local da cabeça de usuários é iniciado na origem de mundo do Unity.
3. Alteração **limpar os sinalizadores** à **cor sólida**.
4. Alterar o **plano de fundo** cor a ser **RGBA 0,0,0,0**. Preto renderizado como transparente em HoloLens.
5. Alteração **recorte planos - quase** para o [HoloLens recomendado](camera-in-unity.md#clip-planes) 0,85 (metros).

Se você excluir e criar uma nova câmera, verifique se é de sua câmera **marcada** como **MainCamera**.


## <a name="see-also"></a>Consulte também
* [Realidade misturada Toolkit v2](mrtk-getting-started.md)
* [Visão geral de desenvolvimento do Unity](unity-development-overview.md)
