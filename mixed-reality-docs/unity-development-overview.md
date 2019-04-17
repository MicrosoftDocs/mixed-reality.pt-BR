---
title: Visão geral de desenvolvimento do Unity
description: Começar a compilar obtendo misto aplicativos de realidade no Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, misturadas realidade, desenvolvimento, introdução, novo projeto, portabilidade, funcionalidade, câmera, simulação, emulação, documentação
ms.openlocfilehash: fc40ef4eae31cf22f640be2666c5af3afb717ff3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590909"
---
# <a name="unity-development-overview"></a>Visão geral de desenvolvimento do Unity

O caminho mais rápido para criar uma [aplicativos de realidade misturada](app-views.md) é com [Unity](http://aka.ms/HoloLensUnity). É recomendável que você reserve um tempo para explorar os [tutoriais do Unity](https://unity3d.com/learn/tutorials). Se você precisar de ativos, o Unity tem uma abrangente [Asset Store](https://www.assetstore.unity3d.com/). Depois que você tiver criado um backup de uma compreensão básica do Unity, você pode visitar o [Academy de realidade mista](academy.md) para conhecer as especificidades do desenvolvimento de realidade misturada com o Unity. Visite o [fóruns de realidade mista do Unity](http://forum.unity3d.com/forums/hololens.102/) interaja com o restante da comunidade da criação de aplicativos de realidade misturada no Unity e encontrar soluções para problemas que você pode enfrentar.

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Portando um aplicativo existente do Unity para Windows Mixed Reality

Se você tiver um projeto existente do Unity que você estiver portando para Windows Mixed Reality, siga juntamente com o [guia de portabilidade do Unity](porting-guides.md) para começar a usar.

## <a name="configuring-a-new-unity-project-for-windows-mixed-reality"></a>Configurando um novo projeto do Unity para Windows Mixed Reality

Para começar a criar aplicativos de realidade misturada com o Unity, primeiramente [instalar as ferramentas](install-the-tools.md). Se você vai visando fones imersivos em exposição realidade mista do Windows em vez de HoloLens, você precisará de uma versão especial do Unity por enquanto.

Se você acabou de criar um novo projeto do Unity, há um pequeno conjunto de configurações de Unity, você precisará alterar para o Windows Mixed Reality, dividido em duas categorias: por projeto e por cena.

### <a name="per-project-settings"></a>As configurações por projeto

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

Seu aplicativo agora pode fazer a renderização holográfica básica e entrada espacial. Para ir adiante e tirar proveito de determinada funcionalidade, seu aplicativo deve declarar os recursos apropriados em seu manifesto. As declarações de manifesto podem ser feitas no Unity para que sejam incluídos em cada exportação projeto subsequente. A configuração são encontradas no **Player Configurações > configurações para a plataforma Universal do Windows > configurações de publicação > recursos**. Os recursos aplicáveis para habilitar APIs do Unity usados para realidade misturada são:

|  Capacidade  |  APIs que exigem a capacidade | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (acesso a [mapeamento espacial](spatial-mapping.md) malhas em HoloLens)&mdash;*nenhum recurso necessário para o rastreamento espacial geral de fone de ouvido* | 
|  WebCam  |  PhotoCapture e VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  PhotoCapture ou VideoCapture, respectivamente (ao armazenar o conteúdo capturado) | 
|  Microfone  |  VideoCapture (durante a captura de áudio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e usar o Profiler Unity) | 

**Configurações de qualidade do Unity**

![Configurações de qualidade do Unity](images/unityqualitysettings-350px.png)<br>
*Configurações de qualidade do Unity*

HoloLens tem uma GPU de classe móvel. Se seu aplicativo for destinado ao HoloLens, você desejará as configurações de qualidade ajustadas para desempenho mais rápido para garantir que podemos manter a taxa de quadros completa:
1. Selecione **Editar > configurações do projeto > qualidade**
2. Selecione o **lista suspensa** sob o **Windows Store** logotipo e selecione **mais rápido**. Você saberá que a configuração seja aplicada corretamente quando a caixa na coluna Windows Store e **mais rápido** linha está verde.

### <a name="per-scene-settings"></a>Configurações por cena

**Configurações de câmera do Unity**

![Configurações de câmera do Unity](images/unitycamerasettings.png)<br>
*Configurações de câmera do Unity*

Depois de habilitar a caixa de seleção "Suporte de realidade Virtual", o [Unity câmera](camera-in-unity.md) identificadores de componente [head acompanhamento e renderização estereoscópica](rendering.md). Não é necessário substituí-lo com uma câmera personalizada para fazer isso.

Se seu aplicativo for direcionado especificamente o HoloLens, há algumas configurações que precisam ser alteradas para otimizar para monitores de transparente do dispositivo, para que seu aplicativo será exibido através ao mundo físico:
1. No **hierarquia**, selecione o **câmera principal**
2. No **Inspector** do painel, defina a transformação **posição** para **0, 0, 0** para que o local da cabeça de usuários é iniciado na origem de mundo do Unity.
3. Alteração **limpar os sinalizadores** à **cor sólida**.
4. Alterar o **plano de fundo** cor a ser **RGBA 0,0,0,0**. Preto renderizado como transparente em HoloLens.
5. Alteração **recorte planos - quase** para o [HoloLens recomendado](camera-in-unity.md#clip-planes) 0,85 (metros).

Se você excluir e criar uma nova câmera, verifique se é de sua câmera **marcada** como **MainCamera**.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Adicionando recursos de realidade mista e entradas

Depois que você configurou seu projeto, conforme descrito acima, objetos padrão de jogos Unity (como a câmera) acenderão imediatamente para um **experiência de escala encaixado**, com a posição da câmera atualizada automaticamente como o usuário move suas cabeças por meio do mundo.

Adicionar suporte para recursos do Windows Mixed Reality, como [estágios espaciais](coordinate-systems.md#spatial-coordinate-systems), [gestos, os controladores de movimento](gestures-and-motion-controllers-in-unity.md) ou [entrada de voz](voice-input-in-unity.md) é feito usando as APIs criadas diretamente no Unity.

Sua primeira etapa deve ser examinar as [experiência escalas](coordinate-systems.md) destinados a seu aplicativo:
* Se você deseja para criar uma **somente orientação** ou **experiência encaixado em escala**, você precisará definir tipo de espaço para rastreamento do Unity [estacionários](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se você estiver procurando para compilar um **escala permanente** ou **experiência de sala em escala**, você precisará garantir que a do Unity acompanhamento do tipo de espaço com êxito é definido como [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se você deseja para criar uma **escala mundial** experiência em HoloLens, permitindo que os usuários usam perfis móveis além dos medidores de 5, você precisará usar o [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) componente.

Todos os blocos de construção principais para aplicativos de realidade misturada são expostos de maneira consistente com as outras APIs do Unity:
* [Câmera](camera-in-unity.md)
* [Sistemas de coordenadas](coordinate-systems-in-unity.md)
* [Gaze](gaze-in-unity.md)
* [Gestos e controladores de movimento](gestures-and-motion-controllers-in-unity.md)
* [Entrada de voz](voice-input-in-unity.md)
* [Persistência](persistence-in-unity.md)
* [Som espacial](spatial-sound-in-unity.md)
* [Mapeamento espacial](spatial-mapping-in-unity.md)

Há outros recursos importantes que muitos aplicativos de realidade misturada vai querer usar, que também é exposto para aplicativos do Unity:
* [Experiências compartilhadas](shared-experiences-in-unity.md)
* [Câmera localizáveis](locatable-camera-in-unity.md)
* [Ponto de foco](focus-point-in-unity.md)
* [Perda de controle](tracking-loss-in-unity.md)
* [Teclado](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Execução do seu projeto do Unity em um dispositivo real ou simulado

Depois que você tem pronto para testar seu projeto do Unity holográfico, sua próxima etapa é [exportar e compilar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md).

Com essa solução do VS em mãos, você pode executar seu aplicativo em uma das três maneiras, usando um dispositivo real ou simulado:
* [Implantar em um headset imersivo HoloLens ou Windows Mixed Reality real](using-visual-studio.md)
* [Implantar no emulador do HoloLens](using-the-hololens-emulator.md)
* [Implantar o simulador de imersivo headset de realidade mista do Windows](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Documentação do Unity

Além desta documentação disponível no Centro de desenvolvimento do Windows, o Unity instala documentação para a funcionalidade do Windows Mixed Reality junto com o Editor do Unity. O Unity fornecida a documentação inclui duas seções separadas:
1. **Referência de script do Unity**
    * Esta seção da documentação contém detalhes da API script do Unity fornece.
    * Acessível por meio do Editor do Unity **Ajuda > Referência de script**
2. **Manual do Unity**
    * Este manual foi projetado para ajudá-lo a aprender a usar o Unity, das técnicas básicas à avançados.
    * Acessível por meio do Editor do Unity **Ajuda > Manual**

## <a name="see-also"></a>Consulte também
* [Noções básicas sobre MR 100: Guia de Introdução com o Unity](holograms-100.md)
* [Configurações recomendadas para Unity](recommended-settings-for-unity.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
* [Exportando e criando uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Usando o namespace do Windows com aplicativos do Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Práticas recomendadas para trabalhar com o Unity e Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modo de jogo do Unity](unity-play-mode.md)
* [Portabilidade de guias](porting-guides.md)
