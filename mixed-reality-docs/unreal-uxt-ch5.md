---
title: 5. Como adicionar um botão e redefinir locais de peças
description: Parte 5 de um tutorial para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 77fe2b59db970a2ac4b531d69efec6794478f7d5
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519988"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. Como adicionar um botão e redefinir locais de peças

Esta seção continua a demonstração das funcionalidades do plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada e a criação dos recursos do seu aplicativo de xadrez. Você criará uma nova função e aprenderá a levar referências para Atores do seu Nível até um Blueprint.

## <a name="objectives"></a>Objetivos

* Adicionar um botão ao seu projeto
* Criar uma função "Reset Location" que envia uma peça de volta para seu local original
* Vincular o botão para disparar a função recém-criada quando pressionado

## <a name="create-a-function-to-reset-location"></a>Criar uma função para redefinir o local

1.  Abra **WhiteKing**. No painel **Meu Blueprint**, clique no botão "+" ao lado da seção **Funções** para criar uma função. Nomeie essa função como "Reset Location". 

2.  No Blueprint **Reset Location** criado recentemente, arraste o pino de execução e solte-o em qualquer lugar na grade do Blueprint para chamar um nó **SetActorRelativeTransform**. Essa função define a transformação (localização, rotação e escala) de um ator em relação ao seu pai. Usaremos essa função para redefinir a posição do rei no tabuleiro, mesmo que o tabuleiro tenha sido movido de sua posição original. Crie um nó **Make Transform** com o local X = -26, Y = 4, Z = 0 e conecte-o à entrada Nova Transformação Relativa. 

![Função Reset Location](images/unreal-uxt/5-function.PNG)

3.  Compile e salve o **WhiteKing**. Volte para a Janela principal. 

## <a name="add-a-button"></a>Adicionar um botão

1.  Na pasta **Blueprints**, crie um Blueprint como subclasse de SimpleButton. O SimpleButton é um Ator de Blueprint de botão 3D que é fornecido como parte do plug-in Ferramentas de UX. Nomeie esse botão como "ResetButton" e clique duas vezes para abrir o Blueprint. 

![Subclasse do novo Blueprint de SimpleButton](images/unreal-uxt/5-subclass.PNG)

2.  No painel **Componentes**, clique em **PressableButton (Herdado)** . No painel Detalhes, role até ver a seção **Eventos**. Clique no botão de adição verde próximo de **On Button Pressed**. Isso adicionará um evento **On Button Pressed** ao Grafo de Eventos, que será chamado quando o botão for pressionado. Agora chamaremos a função Reset Location do WhiteKing. Para fazer isso, primeiro precisaremos obter uma referência ao Ator WhiteKing em nosso Nível. 

3.  No painel **Meu Blueprint**, localize a seção **Variáveis** e clique no botão **+** para adicionar uma nova variável. Nomeie essa variável como "WhiteKing". No painel Detalhes, selecione a lista suspensa próxima de **Tipo de Variável**, pesquise por "WhiteKing" e selecione a **Referência de Objeto**. Por fim, marque a caixa próxima de **Instância Editável**. Isso permitirá que a variável seja definida no Nível Principal. 

![Criar uma variável](images/unreal-uxt/5-var.PNG)

4.  Arraste a variável WhiteKing de **Meu Blueprint > Variáveis** até o Grafo de Eventos do Botão Redefinir. Escolha **Obter WhiteKing**. 

5.  Arraste o pino da saída WhiteKing e solte para posicionar um novo nó. Selecione a função **Reset Location**. Por fim, arraste o pino de execução de saída de **On Button Pressed** até o pino de execução de entrada em **Reset Location**. **Compile** e **Salve** o Blueprint ResetButton e, em seguida, retorne à Janela principal. 

![Chamar função Reset Location de On Button Pressed](images/unreal-uxt/5-callresetloc.PNG)

6.  Arraste **ResetButton** até o visor e defina seu local como X = 50, Y = -25, Z = 10. Em **Padrão**, defina o valor da variável WhiteKing como **WhiteKing**.

![Definir a variável](images/unreal-uxt/5-buttonlevel.PNG)

Agora você tem um aplicativo de realidade misturada com uma peça e um tabuleiro de xadrez que podem ser pegados, bem como um botão totalmente funcional que redefinirá o local da peça quando for pressionado. O aplicativo criado até esse ponto pode ser encontrado no [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp). Você pode ir além deste tutorial e configurar o restante das peças de xadrez, para que todo o tabuleiro seja redefinido quando o usuário pressionar o botão.

![Encerrar cena no visor](images/unreal-uxt/5-endscene.PNG)

[Próxima seção: 6. Como empacotar e implantar no dispositivo ou emulador](unreal-uxt-ch6.md)
