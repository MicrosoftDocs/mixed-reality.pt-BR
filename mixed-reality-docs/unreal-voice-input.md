---
title: Entrada de voz
description: Tutorial sobre como configurar e usar a entrada de voz no HoloLens 2 e no mecanismo inreal
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Realidade mista do Windows, inreal, Engine 4, UE4, HoloLens 2, voz, entrada de voz, reconhecimento de fala, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, desenvolvimento de jogos
ms.openlocfilehash: c5de0cd912674ccd681fd398fb6fe5fd345ab6f2
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330628"
---
# <a name="voice-input-in-unreal"></a>Entrada de voz em não real

## <a name="overview"></a>Visão geral
A entrada de voz permite interagir com um holograma sem a necessidade de usar gestos de mão e tem suporte no HoloLens (1º gen) e no HoloLens 2. Ele é alimentado pelo mesmo mecanismo que dá suporte à fala em todos os outros aplicativos universais do Windows e pode adicionar uma sensação natural à maneira como você interage em realidade misturada. 

Os recursos de voz com suporte incluem:
- O [comando SELECT](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)
- [Ei, Cortana](https://docs.microsoft.com/windows/mixed-reality/voice-input#hey-cortana)
- "Vê-lo, digamos" para interação entre botões e rótulos
- Ditado

Para obter mais informações, confira a documentação principal de [entrada de voz](voice-input.md) .

## <a name="enabling-speech-recognition"></a>Habilitando o reconhecimento de fala

Para habilitar o reconhecimento de fala no HoloLens:
1. Selecione **configurações do projeto > plataforma > recursos de > do HoloLens** e habilite o **microfone**. 
2. Habilitado Recogniztion de fala em **configurações > privacidade > fala** e selecione **Inglês**.

> [!NOTE]
> O reconhecimento de fala sempre funciona no idioma de exibição do Windows configurado no aplicativo **configurações** . É recomendável que você também habilite o **reconhecimento de fala online** para a melhor qualidade de serviço.

![Configurações de reconhecimento de fala do Windows](images/unreal/speech-recognition-settings.png)

3. Uma caixa de diálogo será exibida quando o aplicativo começar a perguntar se você deseja habilitar o microfone. Selecionar **Sim** inicia a entrada de voz no aplicativo.

A entrada de voz não requer nenhuma API especial do Windows Mixed Reality; Ele foi criado na API de mapeamento de [entrada](https://docs.unrealengine.com/Gameplay/Input/index.html) do mecanismo 4 inreal existente. 

## <a name="adding-speech-mappings"></a>Adicionando mapeamentos de fala
Conectar a fala a ação é uma etapa importante ao usar a entrada de voz. Esses mapeamentos monitoram o aplicativo para palavras-chave de fala que um usuário pode dizer e, em seguida, dispara uma ação vinculada. Você pode encontrar mapeamentos de fala de:
1. Selecione **editar > configurações do projeto**, role até a seção **mecanismo** e clique em **entrada**.

Para adicionar um novo mapeamento de fala para um comando de salto:
1. Clique no **+** ícone ao lado de **elementos da matriz** e preencha os seguintes valores:
    * **jumpWord** para o **nome da ação**
    * **ir** para **palavra-chave de fala**

> [!NOTE]
> Qualquer palavra (s) em inglês ou sentenças curtas podem ser usadas como uma palavra-chave. 

![Configurações de entrada do mecanismo UE4](images/unreal/engine-input.png)

Os mapeamentos de fala podem ser usados como componentes de entrada como mapeamentos de ação ou de eixo ou como nós de plano gráfico no grafo de eventos. Por exemplo, você pode vincular o comando de salto para imprimir dois logs diferentes dependendo de quando a palavra for falada:

1. Clique duas vezes em um plano gráfico para abri-lo no **grafo de eventos**.
2. **Clique com o botão direito do mouse** e pesquise pelo **nome da ação** do seu mapeamento de fala (neste caso, **jumpWord**) e pressione **Enter**. Isso adiciona um nó de **ação de entrada** ao grafo.
3. Arraste e solte o pino **pressionado** para **Imprimir** o nó da cadeia de caracteres, conforme mostrado na imagem abaixo. Você pode deixar o PIN **liberado** vazio, ele não executará nada para mapeamentos de fala.
 
![Ação simples para voz](images/unreal/voice-input-img-03.png)

4. Reproduza o aplicativo, digamos que a palavra **salte** e assista ao console para imprimir os logs!

Essa é toda a configuração que você precisará para começar a adicionar entrada de voz aos seus aplicativos de HoloLens em um não real. Você pode encontrar mais informações sobre a fala e a interatividade nos links abaixo e certifique-se de pensar sobre a experiência que está criando para seus usuários.

## <a name="see-also"></a>Confira também
* [Focar e confirmar](gaze-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada do MR 212: voz](holograms-212.md)
