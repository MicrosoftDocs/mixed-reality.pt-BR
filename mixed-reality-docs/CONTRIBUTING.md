---
title: Instruções de contribuição
description: Como Contribuir para a documentação do Windows Mixed Reality.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590930"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>Contribuindo para a documentação do desenvolvedor do Windows Mixed Reality

Bem-vindo à [repositório público para a documentação do desenvolvedor do Windows Mixed Reality](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)! Qualquer artigo, você cria ou edita neste repositório **estarão visíveis para o público.** 

Os documentos de realidade mista do Windows agora estão na plataforma docs.microsoft.com, que usa Markdown para GitHub (com recursos de Markdig). Essencialmente, o conteúdo que você pode editar este repositório se transformam em formatado e estilizadas páginas que aparecem em https://docs.microsoft.com/windows/mixed-reality. 

Esta página aborda as etapas básicas e diretrizes para contribuir, bem como links para Noções básicas de Markdown. Agradecemos sua contribuição!

## <a name="before-you-start"></a>Antes de começar

Se você não tiver uma, você precisará [criar uma conta do GitHub](https://github.com/join).

>[!NOTE]
>Se você for um funcionário da Microsoft, vincular sua conta do GitHub para seu alias da Microsoft sobre o [portal do Microsoft Open Source](https://repos.opensource.microsoft.com/). Junte-se a **"Microsoft"** e **"MicrosoftDocs"** organizações).

Ao configurar sua conta do GitHub, também recomendamos essas precauções de segurança:
- Criar uma [senha forte para sua conta do Github](https://github.com/settings/admin).
- Habilitar [autenticação de dois fatores](https://github.com/settings/two_factor_authentication/configure).
- Salvar sua [códigos de recuperação](https://github.com/settings/auth/recovery-codes) em um local seguro.
- Atualização de seu [configurações de perfil público](https://github.com/settings/profile).
   - Defina seu nome e considere a configuração de seu *email público* ao *não mostrar o meu endereço de email*.
   - É recomendável que você carregar uma foto de perfil, como uma miniatura será mostrada nas páginas do docs para o qual você contribuir.
- Se você planeja usar um fluxo de trabalho de linha de comando, considere a configuração de [Git Credential Manager para Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) para que você não precise inserir sua senha cada vez que você faça uma contribuição.

Executar essas etapas é importante, pois o sistema de publicação está vinculado ao GitHub e você será listado como autor ou colaborador para cada artigo usando seu alias do GitHub.

## <a name="editing-an-existing-article"></a>Editando um artigo existente

Use o seguinte fluxo de trabalho para fazer atualizações para *um artigo existente* por meio do GitHub em um navegador da web:

1. Navegue até o artigo que deseja editar na pasta "misto-realidade-docs".
2. Selecione o botão Editar (ícone de lápis) no canto superior direito. Isso bifurcará automaticamente uma ramificação descartável desativar o branch 'mestre'.

   ![Edite um artigo.](images/editpage.png)
3. Para editar o conteúdo do artigo (consulte ["Noções básicas de Markdown"](#markdown-basics) abaixo para obter orientação).
4. Atualize os metadados conforme relevante na parte superior de cada artigo:
   * title: Isso é o título da página que aparece na guia do navegador quando o artigo estiver sendo exibido. Como isso é usado para SEO e indexação, você não deve alterar o título, a menos que necessário (embora isso seja menos crítico antes de se tornar pública documentação).
   * description: Escreva uma breve descrição do conteúdo do artigo. Isso ajuda na descoberta e SEO.
   * Autor: Se você for o proprietário principal da página, adicione aqui seu alias do GitHub.
   * ms.author: Se você for o proprietário principal da página, adicione o alias aqui da Microsoft (você não precisa @microsoft.com, apenas o alias).
   * ms.date: Atualize a data, se você estiver adicionando o conteúdo principal para a página, mas não para correções como esclarecimento, formatação, gramática, ou de ortografia.
   * palavras-chave: Palavras-chave ajudam a SEO (otimização do mecanismo de pesquisa). Adicionar palavras-chave, separadas por uma vírgula e um espaço, que são específicas para seu artigo (mas sem pontuação após a última palavra-chave em sua lista); Você não precisa adicionar palavras-chave global que se aplicam a todos os artigos, como aqueles são gerenciados em outros lugares. 
5. Quando tiver concluído suas edições de artigo, role para baixo e clique no **propor alteração de arquivo** botão.
6. Na próxima página, clique em **criar solicitação de pull** para mesclar sua ramificação criada automaticamente em 'mestre'.
7. Repita as etapas acima para o próximo artigo que você deseja editar.

## <a name="creating-a-new-article"></a>Criar um novo artigo

Use o seguinte fluxo de trabalho para *criar novos artigos* no repositório de documentação por meio do GitHub em um navegador da web:

1. Crie uma bifurcação de branch 'mestre' MicrosoftDocs/realidade misturada (usando o **bifurcação** botão no canto superior direito).

   ![A ramificação mestre da bifurcação.](images/forkbranch.png)
2. Na pasta "misto-realidade-docs", clique o **criar novo arquivo** botão no canto superior direito.
3. Criar um nome de página para o artigo (use hifens em vez de espaços e não use pontuação ou apóstrofos) e acrescente ". MD"

   ![Nomeie a nova página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Verifique se que você cria o novo artigo de dentro da pasta "misto-realidade-docs". Você pode confirmar isso verificando "/ misto-realidade-docs /" na linha do nome de arquivo novo.

4. Na parte superior da sua nova página, adicione o seguinte bloco de metadados:

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. Preencha os campos de metadados relevantes pelas instruções de [acima da seção](#editing-an-existing-article).
6. Gravação artigo conteúdo usando [Noções básicas de Markdown](#markdown-basics).
7. Adicionar um `## See also` seção na parte inferior do artigo com links para outros artigos pertinentes.
8. Quando terminar, clique em **confirmação novo arquivo**.
9. Clique em **nova solicitação de pull** e mesclar a branch 'mestre' de seu fork em MicrosoftDocs/realidade misturada 'master' (Verifique se a seta está apontando a maneira correta).

   ![Criar solicitação de pull da bifurcação em MicrosoftDocs/realidade misturada](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Noções básicas de markdown

Os recursos a seguir ajudarão você a aprender como editar a documentação usando a linguagem Markdown:

- [Noções básicas de markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Pôster de referência de markdown no instantâneo](images/MarkdownPoster.pdf)
- [Recursos adicionais para a gravação de Markdown para docs.microsoft.com](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Adicionando tabelas

Por causa das tabelas de estilos de docs.microsoft.com de forma, eles não terão bordas ou estilos personalizados, mesmo se você tentar CSSS embutidas. Ele parecerá funcionar por um curto período de tempo, mas, eventualmente, a plataforma será retirar o estilo para fora da tabela. Portanto, planeje com antecedência e manter suas tabelas simples. [Aqui está um site que facilita as tabelas Markdown](http://www.tablesgenerator.com/markdown_tables).

O [extensão de Markdown do Docs para Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) também torna a tabela geração fácil se você estiver usando [Visual Studio Code (veja abaixo)](#using-visual-studio-code) para editar a documentação.

### <a name="adding-images"></a>Adicionando imagens

Você precisará carregar suas imagens para a pasta "misto-realidade-docs/imagens" no repositório e, em seguida, referenciá-los adequadamente no artigo. Imagens serão exibidos automaticamente em tamanho normal, que significa que se sua imagem for grande, ele preencherá toda a largura do artigo. Assim, é recomendável previamente suas imagens de dimensionamento antes de carregá-los. A largura recomendada é entre pixels de 600 e 700, embora você deve dimensionar para cima ou para baixo, se for uma captura de tela densa ou uma fração de uma captura de tela, respectivamente.

>[!IMPORTANT]
>Você só pode carregar imagens ao seu repositório bifurcado antes da mesclagem. Portanto, se você planeja adicionar imagens a um artigo, você precisará [usar o Visual Studio Code](#using-visual-studio-code) para adicionar imagens à pasta do seu fork "imagens" pela primeira vez ou certifique-se de fazer o seguinte em um navegador da web:
>
>1. Bifurcado o repositório MicrosoftDocs/realidade misturada.
>2. Editar o artigo na sua bifurcação.
>3. Carregamos as imagens que você está fazendo referência em seu artigo para a pasta "misto-realidade-docs/imagens" na sua bifurcação.
>4. Criado um **solicitação de pull** para mesclar sua bifurcação ao branch 'mestre' MicrosoftDocs/realidade misturada.
>
>Para saber como configurar seu próprio repositório bifurcado, siga as instruções para [criando um novo artigo](#creating-a-new-article).

## <a name="previewing-your-work"></a>Visualizando seu trabalho

Ao editar no GitHub por meio de um navegador da web, você pode clicar na **visualização** guia na parte superior da página para visualizar seu trabalho antes de confirmar. 

>[!NOTE]
>Visualizar as alterações em review.docs.microsoft.com só está disponível para os funcionários da Microsoft

Os funcionários da Microsoft: depois que suas contribuições foram mescladas no branch 'mestre', você pode ver a aparência a documentação antes de ele se tornar público no https://review.docs.microsoft.com/windows/mixed-reality?branch=master (encontrar seu artigo usando o sumário na coluna à esquerda).

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Editar no navegador versus edição com um cliente de desktop

Editar no navegador é a maneira mais fácil de fazer alterações, no entanto, há algumas desvantagens:

- Você não obterá a verificação ortográfica.
- Você não terá qualquer inteligente vinculação para outros artigos (você precisa digitar manualmente o nome de arquivo do artigo).
- Ele pode ser um problema para carregar e imagens de referência.

Se você seria melhor não lidar com esses problemas, talvez você prefira usar um cliente da área de trabalho, como [Visual Studio Code](https://code.visualstudio.com/) com algumas [extensões úteis](#useful-extensions) pode contribuir com documentação.

## <a name="using-visual-studio-code"></a>Usando o Visual Studio Code

Pelas razões listadas [acima](#editing-in-the-browser-vs-editing-with-a-desktop-client), talvez você prefira usando um cliente de área de trabalho para editar a documentação em vez de um navegador da web. É recomendável usar [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Configuração

Siga estas etapas para configurar o Visual Studio Code para trabalhar com este repositório:

1. Em um navegador da web:
    1. Instale [Git para seu PC](https://git-scm.com/downloads).
    2. Instale [Visual Studio Code](https://code.visualstudio.com/).
    3. [Crie um fork MicrosoftDocs/realidade misturada](#creating-a-new-article) se você ainda não fez isso.
    4. Na sua bifurcação, clique em **clonar ou baixar** e copie a URL.
2. Crie um clone local da sua bifurcação no Visual Studio Code:
    1. Dos **modo de exibição** menu, selecione **paleta de comandos**.
    2. Tipo "Git:Clone".
    3. Cole a URL que você acabou de copiar.
    4. Escolha onde salvar o clone em seu computador.
    5. Clique em **abrir repositório** no pop-up.

### <a name="editing-documentation"></a>Documentação de edição

Use o seguinte fluxo de trabalho para fazer alterações a documentação do Visual Studio Code:

>[!NOTE]
>Todas as diretrizes para [editando](#editing-an-existing-article) e [criando](#creating-a-new-article) artigos e o [Noções básicas de edição de Markdown](#markdown-basics), acima aplica-se ao usar o Visual Studio Code também.

1. Verifique se que seu fork clonado está atualizada com o repositório oficial.
   1. Em um navegador da web, crie uma solicitação de pull para sincronizar as alterações recentes de outros colaboradores no MicrosoftDocs/realidade misturada 'mestre' para a bifurcação (Verifique se a seta está apontando da maneira correta).
      
      ![Alterações de sincronização de MicrosoftDocs/realidade misturada para sua bifurcação](images/sync_repos.PNG)
   2. No Visual Studio Code, clique no botão de sincronização para sincronizar seu fork recentemente atualizada para o clone local.
      
      ![Clique no botão de sincronização](images/sync_clone.png)
2. Criar ou editar artigos no repositório clonado usando o Visual Studio Code.
   1. Edite um ou mais artigos (Adicionar imagens a pasta "imagens" se necessário).
   2. **Salve** alterações na **Explorer**.
      
      ![Escolher "Salvar todos os" no Explorer](images/explorer_save.png)
   3. **Confirmar tudo** alterações na **controle de origem** (gravar a mensagem de confirmação quando solicitado).
      
      ![Escolha "Confirmar tudo" no controle de origem](images/source_control_commit.png)
   4. Clique o **sincronização** botão para sincronizar suas alterações de volta para a origem (seu fork no GitHub).
      
      ![Clique no botão de sincronização](images/sync_back.png)
3. Em um navegador da web, crie uma solicitação de pull para sincronizar as novas alterações na sua bifurcação para MicrosoftDocs/realidade misturada 'master' (Verifique se a seta está apontando a maneira correta).

   ![Criar solicitação de pull da bifurcação em MicrosoftDocs/realidade misturada](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Extensões úteis

As seguintes extensões do Visual Studio Code são muito úteis quando você editar a documentação:

- [Extensão de Markdown do docs para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -Use **Alt + M** para abrir um menu de opções, como de criação do docs:
   - Imagens de referência e de pesquisa que você carregou.
   - Adicione formatação, como listas, tabelas e balões específicas de documentos, como `>[!NOTE]`.
   - Pesquisa e referência de links internos e indicadores (links para seções específicas dentro de uma página).
   - Erros de formatação são realçados (passar o mouse sobre o erro para obter mais informações).
- [Código de verificação ortográfica](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -palavras incorretas serão sublinhadas; clique duas vezes em uma palavra incorreta para alterá-la ou salvá-lo ao dicionário.
