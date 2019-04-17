---
title: Exportando e criando uma solução do Visual Studio do Unity
description: Este artigo descreve a exportação de seu projeto de realidade mista do Unity para que você pode criar e implantar no Visual Studio.
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: o Unity, visual studio, exportar, criar, implantar
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590713"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Exportando e criando uma solução do Visual Studio do Unity

Se você não pretende usar o teclado do sistema em seu aplicativo, nossa recomendação é usar *D3D* conforme seu aplicativo usará um pouco menos memória e têm um tempo de inicialização ligeiramente mais rápido. Se você estiver usando a API de TouchScreenKeyboard em seu projeto para usar o teclado do sistema, você precisará exportar como *XAML*.

## <a name="how-to-export-from-unity"></a>Como exportar do Unity

![Configurações de build do Unity](images/unitybuildsettings-300px.png)<br>
*Configurações de build do Unity*

1. Quando você estiver pronto para exportar o projeto do Unity, abra o **arquivo** menu e selecione **configurações de compilação...**
2. Clique em **cenas abra Adicionar** para adicionar sua cena para a compilação.
3. No **configurações de Build** caixa de diálogo, escolha as seguintes opções para exportar para o HoloLens:
   * **Plataforma:** *Plataforma universal do Windows* e certifique-se de selecionar **alternar plataforma** para sua seleção entrem em vigor.
   * **SDK:** *Universal 10*.
   * **Tipo de Build UWP:** *D3D*.
4. **Opcional**: **Unity C# projetos:** Verificado.

>[!NOTE]
>Marcar essa caixa permite que você:
>* Depure seu aplicativo no depurador remoto do Visual Studio.
>* Edite os scripts no Unity C# projeto enquanto estiver usando o IntelliSense para APIs do WinRT.

5. Do **configurações de Build...**  janela, abra **configurações do Player...**
6. Selecione o **configurações para a plataforma Universal do Windows** guia.
7. Expanda o **XR configurações** grupo.
8. No **configurações XR** seção, verifique o **suporte de realidade Virtual** caixa de seleção para adicionar uma nova **dispositivos de realidade Virtual** listar e confirmar **"misto do Windows Realidade"** está listado como um dispositivo com suporte.
9. Volte para o **configurações de Build** caixa de diálogo.
10. Selecione **Build**.
11. Na caixa de diálogo Windows Explorer que aparece, crie uma nova pasta para armazenar a saída do build do Unity. Em geral, é o nome da pasta "Aplicativo".
12. Selecione a pasta recém-criada e clique em **Selecionar pasta**.
13. Depois que o Unity terminou de construção, uma janela do Windows Explorer será aberto para o diretório raiz do projeto. Navegue até a pasta recém-criada.
14. Abra o arquivo de solução do Visual Studio gerado localizado dentro dessa pasta.

## <a name="when-to-re-export-from-unity"></a>Quando exportar novamente do Unity

Verificando o "C# projetos de" caixa de seleção quando a exportação de seu aplicativo do Unity cria uma solução do Visual Studio que inclui todos os arquivos de script do Unity. Isso permite que você itere nos seus scripts sem exportar novamente do Unity. No entanto, se você quiser fazer alterações ao seu projeto que não são apenas alterando o conteúdo de scripts, você precisará exportar novamente do Unity. Alguns exemplos de vezes que você precisa exportar novamente do Unity são:
* Você pode adicionar ou remove ativos na guia de projeto.
* Você altera qualquer valor na guia do Inspetor.
* Você pode adicionar ou remove objetos de guia de hierarquia.
* Alterar as configurações de projeto do Unity

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Criando e implantando uma solução do Visual Studio do Unity

O restante da criação e implantação de aplicativos acontece em [Visual Studio](using-visual-studio.md). Você precisará especificar uma configuração de build do Unity. Convenções de nomenclatura do Unity podem diferir das que você está normalmente usados no Visual Studio:

|  Configuração  |  Explicação | 
|----------|----------|
|  Depuração  |  Todas as otimizações de logoff e o criador de perfil está habilitado. Usado para depurar scripts. | 
|  Mestre  |  Todas as otimizações estão ativadas e o criador de perfil está desabilitado. Usado para enviar aplicativos para a Store. | 
|  Versão  |  Todas as otimizações estão ativadas e o criador de perfil está habilitado. Usado para avaliar o desempenho do aplicativo. | 

Observe que a lista acima é um subconjunto dos gatilhos comuns que fará com que o projeto do Visual Studio precisa ser gerado. Em geral, a edição de arquivos. cs, de dentro do Visual Studio não exigirão o projeto para ser regenerado a partir de dentro do Unity.

## <a name="troubleshooting"></a>Solução de problemas

Se você achar que as edições em seus arquivos. cs não são reconhecidas no seu projeto do Visual Studio, certifique-se de que "Unity C# projetos" estiver marcada quando você gera o projeto de VS no menu do Build do Unity.
