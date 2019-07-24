---
title: Práticas recomendadas para trabalhar com o Unity e o Visual Studio
description: Dicas e truques para simplificar o fluxo de trabalho de criação de um aplicativo de realidade misturada com o Unity e o Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: implantar, Unity, Visual Studio, HoloLens, HoloLens 2, headset de imersão
ms.openlocfilehash: b2c345a8cc9bddcbc447531eb5f6cdacc62f2e98
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522316"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Práticas recomendadas para trabalhar com o Unity e o Visual Studio

Um desenvolvedor que cria um aplicativo de realidade misturada com o Unity precisará alternar entre o Unity e o Visual Studio para criar o pacote de aplicativos que é implantado no HoloLens e/ou um headset de imersão. Por padrão, duas instâncias do Visual Studio são necessárias (uma para modificar scripts do Unity e outra para implantar no dispositivo e depurar). O procedimento a seguir permite o desenvolvimento usando uma única instância do Visual Studio, reduz a frequência de exportação de projetos do Unity e melhora a experiência de depuração.

## <a name="improving-iteration-time"></a>Melhorando o tempo de iteração

O suporte para o back-end de script do .NET no Unity está sendo substituído no Unity 2018 e removido no Unity 2019 +. Portanto, é aconselhável mudar para [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). No entanto, isso pode incorrer em tempos de compilação mais longos do Unity para o Visual Studio. Para melhorar a iteração mais rápida, é necessário configurar o ambiente para obter melhores resultados de compilação.

1) Aproveite a criação incremental criando seu projeto no mesmo diretório a cada vez, reutilizando os arquivos predefinidos ali
2) Desabilitar verificações de software antimalware para seu projeto & criar pastas
   - Abra o **vírus & proteção contra ameaças** em seu aplicativo de configurações do Windows 10
   - Selecione **gerenciar configurações** em **vírus & ameaças proteção configurações**
   - Selecione **Adicionar ou remover exclusões** na seção **exclusões**
   - Clique em **Adicionar uma exclusão** e selecione a pasta que contém o código do projeto do Unity e as saídas da compilação
3) Utilizar um SSD para compilação

Leia otimizando os [tempos de compilação para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obter mais informações. Além disso, leia [depuração em back-end de script IL2CPP](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).

Além disso, considere instalar a [extensão do Visual Studio *UnityScriptAnalyzer* ](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer). Essa ferramenta analisa seus scripts de C# Unity para o código que pode ser capaz de ser escrito de maneira mais otimizada.

## <a name="visual-studio-tools-for-unity"></a>Ferramentas do Visual Studio para Unity

Baixar [Ferramentas do Visual Studio para Unity](https://docs.microsoft.com/en-us/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity?view=vs-2019)

**Benefícios do Ferramentas do Visual Studio para Unity**
* Depure o modo de reprodução do Unity no editor do Visual Studio colocando pontos de interrupção, avaliando variáveis e expressões complexas.
* Use o explorador de projeto do Unity para localizar o script com exatamente a mesma hierarquia que o Unity exibe.
* Obtenha o console do Unity diretamente dentro do Visual Studio.
* Use assistentes para criar ou navegar rapidamente para scripts.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Expor C# variáveis de classe para um ajuste fácil

Há duas maneiras de expor variáveis de classe. A maneira recomendada de fazer isso é adicionar o atributo [Serializefield] às suas variáveis privadas. Isso permite que eles sejam acessados do editor, mas não expostos de forma programática.  A outra opção é tornar C# as variáveis de classe públicas para expô-las na interface do usuário do editor. 

Ambas as abordagens possibilitam o ajuste fácil de variáveis durante a execução no editor. Isso é especialmente útil para ajustar propriedades mecânicas de interação.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Regenerar soluções do Visual Studio UWP após a atualização do SDK do Windows ou do Unity

As soluções UWP do Visual Studio com check-in no controle do código-fonte podem ficar desatualizadas após a atualização para um novo SDK do Windows ou mecanismo do Unity. Você pode resolver isso após a atualização criando uma nova solução UWP do Unity e, em seguida, mesclando quaisquer diferenças na solução com check-in.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Usar ativos de formato de texto para uma comparação fácil de alterações de conteúdo

O armazenamento de ativos em formato de texto facilita a revisão de diferenciações de alteração de conteúdo no Visual Studio. Você pode habilitar isso em "Editar configurações de projeto > editor de >" alterando o modo de **serialização de ativos** para **forçar o texto**. No entanto, mesclar alterações de arquivo de ativo de texto é propenso a erros e não recomendado, portanto, considere habilitar check-outs binários exclusivos no sistema de controle do código-fonte.

## <a name="see-also"></a>Consulte também
- [Ferramentas do Visual Studio para Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Otimizando os tempos de compilação para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Extensão do Visual Studio](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)