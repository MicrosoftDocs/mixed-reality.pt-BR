---
title: Práticas recomendadas para trabalhar com o Unity e Visual Studio
description: Dicas e truques para simplificar o fluxo de trabalho de criação de um aplicativo de realidade misturada com o Unity e Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: implantar, unity, fone de ouvido de imersão do visual studio, HoloLens,
ms.openlocfilehash: 80a533851b3bee0d747a90dfececbaa558c4ec1f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590815"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Práticas recomendadas para trabalhar com o Unity e Visual Studio

Um desenvolvedor que cria um aplicativo de realidade misturada com o Unity precisará alternar entre o Unity e o Visual Studio para compilar o pacote de aplicativo é implantado para HoloLens e/ou um fone de ouvido envolvente. Por padrão, duas instâncias do Visual Studio são necessário (um para modificar os scripts do Unity) e outro para implantar o dispositivo e na depuração. O procedimento a seguir permite o desenvolvimento usando a instância única do Visual Studio, reduz a frequência de exportação de projetos do Unity e melhora a experiência de depuração.

## <a name="improving-iteration-time"></a>Melhorando o tempo de iteração

Um problema comum de fluxo de trabalho ao trabalhar com o Unity e o Visual Studio está tendo várias janelas do Visual Studio aberto e a necessidade de alternar constantemente entre o Visual Studio e o Unity para iterar.
1. **Unity** – para modificar a cena e exportar uma solução do Visual Studio
2. **Visual Studio (1)** - para modificar scripts
3. **Visual Studio (2)** – para criação e implantação do Unity exportados solução do Visual Studio para o dispositivo

Felizmente, existe uma maneira de simplificar a uma única instância do Visual Studio e reduzir o exportações frequentes do Unity.

Quando [exportando seu projeto do Unity](exporting-and-building-a-unity-visual-studio-solution.md), verifique o **Unity C# projetos** caixa de seleção no menu "Arquivo > Compilar configurações". Agora, o projeto de exportar do Unity inclui todo o seu projeto do C# scripts e tem vários benefícios:
* Usar a mesma instância do Visual Studio para escrever scripts e criação/implantação de seu projeto
* Exportar do Unity somente quando a cena é alterada no Editor do Unity; alterar o conteúdo de scripts pode ser feito no Visual Studio sem exportar novamente.

Com o **Unity C# projetos** habilitada, apenas uma instância de cada programa precisa ser aberta:
1. **Unity** – para modificar a cena e exportar uma solução do Visual Studio
2. **Visual Studio** - para modificar scripts, em seguida, criar e implantar o Unity exportados solução do Visual Studio para o dispositivo

## <a name="visual-studio-tools-for-unity"></a>Ferramentas do Visual Studio para Unity

Baixar [ferramentas do Visual Studio para Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)

**Benefícios do Visual Studio Tools for Unity**
* Depure o modo de reprodução de no editor do Unity no Visual Studio, colocando os pontos de interrupção, avaliar as varáveis e expressões complexas.
* Use o Explorador de projeto do Unity para encontrar seu script com a mesma hierarquia exata que exibe do Unity.
* Obtenha o console do Unity diretamente dentro do Visual Studio.
* Use assistentes para criar rapidamente ou navegue para scripts.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Expor C# classe variáveis para ajuste fácil

Há duas maneiras de expor as variáveis de classe. A maneira recomendada para fazer isso é adicionar o atributo [SerializeField] para suas variáveis privadas. Isso lhes permite ser acessados do editor, mas não programaticamente expostos.  A outra opção é tornar C# classe pública de variáveis para expô-las no editor de interface do usuário. 

Ambas as abordagens tornam possível ajustar facilmente variáveis durante a execução no editor. Isso é especialmente útil para propriedades mechanic de interação de ajuste.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Regenerar as soluções do Visual Studio de UWP depois de atualizar o SDK do Windows ou do Unity

Check-in no controle de origem de soluções do Visual Studio de UWP podem obter desatualizadas depois de atualizar para um novo mecanismo de SDK do Windows ou do Unity. Você pode resolver isso após a atualização ao construir uma nova solução UWP do Unity, mesclando as diferenças na solução de check-in.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Usar ativos de formato de texto para facilitar a comparação das alterações de conteúdo

Armazenar ativos no formato de texto torna mais fácil de examinar as diferenças de alteração de conteúdo no Visual Studio. Você pode habilitá-lo no "Editar > Editor de configurações do > projeto" alterando **serialização de ativo** modo **forçar texto**. No entanto, mesclar alterações do arquivo de ativo de texto é propenso a erro e não é recomendado, portanto, considere habilitar check-outs exclusivos binários no seu sistema de controle do código-fonte.
