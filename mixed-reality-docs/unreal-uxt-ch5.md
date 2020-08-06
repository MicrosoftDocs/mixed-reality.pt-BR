---
title: 5. Como adicionar um botão e redefinir locais de peças
description: Parte 5 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: e81da5a4550f258b629443df9b2b655d81108c21
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376358"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. Como adicionar um botão e redefinir locais de peças


## <a name="overview"></a>Visão geral

No tutorial anterior, você adicionou Atores de Interação à Mão aos componentes Peão e Manipulador para o tabuleiro de xadrez, a fim de torná-los interativos. Nesta seção, você continuará trabalhando com as Ferramentas de UX do Kit de Ferramentas de Realidade Misturada ao criar os recursos do seu aplicativo de xadrez. Isso inclui a criação de uma função e o aprendizado de como obter referências a Atores em um Blueprint. Ao final desta seção, você estará pronto para empacotar e implantar o aplicativo de realidade misturada em um dispositivo ou emulador.

## <a name="objectives"></a>Objetivos

* Adicionar um botão interativo
* Criar uma função para redefinir a localização de uma peça
* Vincular o botão para disparar a função quando pressionado

## <a name="creating-a-reset-function"></a>Criar uma função de redefinição
Sua primeira tarefa é criar um blueprint de função que redefina uma peça de xadrez para a posição original dela na cena. 

1.  Abra **WhiteKing**, clique no ícone **+** ao lado da seção **Funções** no **Meu Blueprint** e nomeie-o como **Redefinir Localização**. 

2.  Arraste e solte a execução de **Redefinir Localização** na grade do Blueprint para criar um nó **SetActorRelativeTransform**. 
    * Essa função define a transformação (localização, rotação e escala) de um ator em relação ao seu pai. Você usará essa função para redefinir a posição do rei no tabuleiro, mesmo que o tabuleiro tenha sido movido de sua posição original. 
    
3. Clique com o botão direito do mouse no Grafo de Eventos, selecione **Transformar** e altere a **Localização** dele para **X = -26**, **Y = 4** e **Z = 0**.
    * Conecte o **Valor Retornado** dele ao marcador **Nova Transformação Relativa** em **SetActorRelativeTransform**. 

![Função Reset Location](images/unreal-uxt/5-function.PNG)

Escolha **Compilar** e **Salvar** o projeto antes de voltar à Janela principal. 


## <a name="adding-a-button"></a>Adicionar um botão
Agora que a função está configurada corretamente, a próxima tarefa é criar um botão que a dispare quando tocado. 

1.  Clique em **Adicionar Novo > Classe de Blueprint**, expanda a seção **Todas as Classes** e pesquise por **SimpleButton**. 
    * Nomeie-o como **ResetButton** e clique duas vezes para abrir o Blueprint

> [!NOTE]
> O **SimpleButton** é um Ator de Blueprint de botão 3D que é parte do plug-in Ferramentas de UX. . 

![Subclasse do novo Blueprint de SimpleButton](images/unreal-uxt/5-subclass.PNG)

2. Clique em **Botão de Pressão (Herdado)** no painel **Componentes** e role o conteúdo do painel **Detalhes** para baixo até a seção **Eventos**. 
    * Clique no botão **+** verde próximo de **On Button Pressed** para adicionar um evento Grafo de Eventos, que será chamado quando o botão for pressionado. 
    
Deste ponto em diante, será conveniente que você chame a função **Redefinir Localização** do **WhiteKing**, que precisa de uma referência para o Ator **WhiteKing** no Nível. 

1.  No painel **Meu Blueprint**, navegue até a seção **Variáveis**, clique no botão **+** e nomeie a variável **WhiteKing**. 
    * No painel **Detalhes**, selecione a lista suspensa ao lado de **Tipo de Variável**, pesquise **WhiteKing** e selecione **Referência de Objeto**. 
    * Marque a caixa ao lado de **Instância Editável**. Isso permitirá que a variável seja definida no Nível Principal. 

![Criar uma variável](images/unreal-uxt/5-var.PNG)

2.  Arraste a variável WhiteKing de **Meu Blueprint > Variáveis** até o Grafo de Eventos do Botão Redefinir e escolha **Obter WhiteKing**. 

## <a name="firing-the-function"></a>Como disparar a função
Tudo o que resta fazer é disparar oficialmente a função de redefinição quando o botão for pressionado.

1.  Arraste o pino da saída WhiteKing e solte para posicionar um novo nó. Selecione a função **Reset Location**. Por fim, arraste o pino de execução de saída de **On Button Pressed** até o pino de execução de entrada em **Reset Location**. **Compile** e **Salve** o Blueprint ResetButton e, em seguida, retorne à Janela principal. 

![Chamar função Reset Location de On Button Pressed](images/unreal-uxt/5-callresetloc.PNG)

2.  Arraste **ResetButton** até o visor e defina a localização dele como **X = 50**, **Y = -25** e **Z = 10**. Em **Padrão**, defina o valor da variável **WhiteKing** como **WhiteKing**.

![Definir a variável](images/unreal-uxt/5-buttonlevel.PNG)

Execute o aplicativo, mova a peça de xadrez para um novo local e pressione o botão cor-de-rosa grande para ver a lógica de redefinição em ação!

Agora você tem um aplicativo de realidade misturada com uma peça e um tabuleiro de xadrez com os quais você pode interagir, bem como um botão totalmente funcional que redefinirá a localização da peça. Você pode encontrar o aplicativo concluído até esse ponto no respectivo repositório do [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp). Você pode ir além deste tutorial e configurar o restante das peças de xadrez, para que todo o tabuleiro seja redefinido quando o botão for pressionado.

![Encerrar cena no visor](images/unreal-uxt/5-endscene.PNG)

Você está pronto para prosseguir para a seção final deste tutorial, em que você aprenderá a empacotar e implantar corretamente o aplicativo em um dispositivo ou emulador.

[Próxima seção: 6. Como empacotar e implantar no dispositivo ou emulador](unreal-uxt-ch6.md)
