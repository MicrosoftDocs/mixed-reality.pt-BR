---
title: Exportando e compilando uma solução do Unity Visual Studio
description: Este artigo descreve como exportar seu projeto de realidade misturada do Unity para que você possa compilar e implantar no Visual Studio.
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Visual Studio, exportar, compilar, implantar
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525842"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Exportando e compilando uma solução do Unity Visual Studio

Se você não pretende usar o teclado do sistema em seu aplicativo, nossa recomendação é usar o *D3D* , pois seu aplicativo usará um pouco menos de memória e terá um tempo de inicialização ligeiramente mais rápido. Se você estiver usando a API TouchScreenKeyboard em seu projeto para usar o teclado do sistema, será necessário exportar como *XAML*.

## <a name="how-to-export-from-unity"></a>Como exportar do Unity

![Configurações de Build do Unity](images/unitybuildsettings-300px.png)<br>
*Configurações de Build do Unity*

1. Quando você estiver pronto para exportar seu projeto do Unity, abra o menu **arquivo** e selecione **configurações de compilação...**
2. Clique em **Adicionar abrir cenas** para adicionar sua cena à compilação.
3. Na caixa de diálogo **configurações de compilação** , escolha as seguintes opções para exportar para o HoloLens:
   * **Plataforma** *Plataforma universal do Windows* e certifique-se de selecionar **alternar plataforma** para sua seleção entrar em vigor.
   * **SDK** *Universal 10*.
   * **Tipo de compilação UWP:** *D3D*.
4. **Opcional**: **Projetos C# do Unity:** Check.

>[!NOTE]
>Marcar essa caixa permite que você:
>* Depure seu aplicativo no depurador remoto do Visual Studio.
>* Edite scripts no projeto C# do Unity ao usar o IntelliSense para APIs do WinRT.

5. Na janela **configurações de compilação...** , abra **as configurações do Player...**
6. Selecione as **configurações para plataforma universal do Windows** guia.
7. Expanda o grupo de **configurações XR** .
8. Na seção **configurações de XR** , marque a caixa de seleção **suporte à realidade virtual** para adicionar uma nova lista de **dispositivos de realidade virtual** e confirme se **"realidade mista do Windows"** está listado como um dispositivo com suporte.
9. Retorne para a caixa de diálogo **configurações de compilação** .
10. Selecione **Compilar**.
11. Na caixa de diálogo do Windows Explorer que aparece, crie uma nova pasta para manter a saída de Build do Unity. Em geral, nomeamos a pasta "app".
12. Selecione a pasta recém-criada e clique em **Selecionar pasta**.
13. Depois de concluir a compilação do Unity, uma janela do Windows Explorer será aberta para o diretório raiz do projeto. Navegue até a pasta recém-criada.
14. Abra o arquivo de solução do Visual Studio gerado localizado dentro dessa pasta.

## <a name="when-to-re-export-from-unity"></a>Quando exportar novamente do Unity

Marcar a caixaC# de seleção "projetos" ao exportar seu aplicativo do Unity cria uma solução do Visual Studio que inclui todos os arquivos de script do Unity. Isso permite que você Itere em seus scripts sem exportar novamente do Unity. No entanto, se você quiser fazer alterações em seu projeto que não estejam apenas alterando o conteúdo dos scripts, será necessário reexportar a partir do Unity. Alguns exemplos de vezes que você precisa exportar novamente do Unity são:
* Você adiciona ou remove ativos na guia projeto.
* Você altera qualquer valor na guia inspetor.
* Você adiciona ou remove objetos da guia hierarquia.
* Você altera as configurações de projeto de Unity

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Criando e implantando uma solução do Unity Visual Studio

O restante da criação e implantação de aplicativos acontece no [Visual Studio](using-visual-studio.md). Será necessário especificar uma configuração de compilação do Unity. As convenções de nomenclatura do Unity podem ser diferentes do que costuma ser usado no Visual Studio:

|  Configuração  |  Explicação | 
|----------|----------|
|  Depurar  |  Todas as otimizações desativadas e o criador de perfil está habilitado. Usado para depurar scripts. | 
|  Mestre  |  Todas as otimizações são ativadas e o criador de perfil está desabilitado. Usado para enviar aplicativos para a loja. | 
|  Versão  |  Todas as otimizações são ativadas e o criador de perfil está habilitado. Usado para avaliar o desempenho do aplicativo. | 

Observe que a lista acima é um subconjunto dos gatilhos comuns que farão com que o projeto do Visual Studio precise ser gerado. Em geral, a edição de arquivos. cs de dentro do Visual Studio não exigirá que o projeto seja regenerado no Unity.

## <a name="troubleshooting"></a>Solução de problemas

Se você achar que as edições em seus arquivos. cs não estão sendo reconhecidas em seu projeto do Visual Studio, certifique C# -se de que "projetos do Unity" esteja marcado ao gerar o projeto do vs no menu de Build do Unity.
