---
title: Instruções de contribuição
description: Como contribuir para a documentação do Windows Mixed Reality.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: 934171f26571b3219bbe390aff44349fb6908f74
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437129"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>Contribuindo para a documentação do desenvolvedor do Windows Mixed Reality

Bem-vindo à [documentação de desenvolvedor do repositório público para Windows Mixed Reality](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)! Todos os artigos que você criar ou editar neste repositório **estarão visíveis para o público.** 

Os documentos de realidade misturada do Windows agora estão na plataforma docs.microsoft.com, que usa a redução do tipo GitHub (com recursos do Markdig). Essencialmente, o conteúdo que você edita nesse repositório é ativado em páginas formatadas e estilizadas que aparecem em https://docs.microsoft.com/windows/mixed-reality. 

Esta página aborda as etapas e diretrizes básicas de contribuição, bem como links para noções básicas de redução. Agradecemos sua contribuição!

## <a name="before-you-start"></a>Antes de começar

Se você ainda não tiver uma, precisará [criar uma conta do GitHub](https://github.com/join).

>[!NOTE]
>Se você for um funcionário da Microsoft, vincule sua conta do GitHub ao seu alias da Microsoft no [portal do Microsoft Open Source](https://repos.opensource.microsoft.com/). Junte-se às organizações **"Microsoft"** e **"MicrosoftDocs"** ).

Ao configurar sua conta do GitHub, também recomendamos estas precauções de segurança:
- Crie uma [senha forte para sua conta do GitHub](https://github.com/settings/admin).
- Habilite [a autenticação de dois fatores](https://github.com/settings/two_factor_authentication/configure).
- Salve seus [códigos de recuperação](https://github.com/settings/auth/recovery-codes) em um local seguro.
- Atualize suas [configurações de perfil público](https://github.com/settings/profile).
   - Defina seu nome e considere definir seu *email público* para *não mostrar meu endereço de email*.
   - Recomendamos que você carregue uma imagem de perfil, uma vez que uma miniatura será mostrada nas páginas de documentos nas quais você contribuir.
- Se você planeja usar um fluxo de trabalho de linha de comando, considere configurar o [git Credential Manager para Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) para que você não precise inserir sua senha sempre que fizer uma contribuição.

A execução dessas etapas é importante, pois o sistema de publicação está vinculado ao GitHub e você será listado como autor ou colaborador para cada artigo usando seu alias do GitHub.

## <a name="editing-an-existing-article"></a>Editando um artigo existente

Use o seguinte fluxo de trabalho para fazer atualizações em *um artigo existente* por meio do GitHub em um navegador da Web:

1. Navegue até o artigo que você deseja editar na pasta "Mixed-realde docs".
2. Selecione o botão Editar (ícone de lápis) no canto superior direito. Isso bifurcará automaticamente uma ramificação descartável da ramificação ' mestre '.

   ![Edite um artigo.](images/editpage.png)
3. Edite o conteúdo do artigo (consulte ["Noções básicas de redução"](#markdown-basics) abaixo para obter orientação).
4. Atualize os metadados como relevantes na parte superior de cada artigo:
   * Título: é o título da página que aparece na guia navegador quando o artigo está sendo exibido. Como isso é usado para a SEO e a indexação, você não deve alterar o título, a menos que seja necessário (embora isso seja menos crítico antes que a documentação fique pública).
   * Descrição: escreva uma breve descrição do conteúdo do artigo. Isso ajuda na SEO e na descoberta.
   * Autor: se você for o proprietário principal da página, adicione seu alias do GitHub aqui.
   * MS. Author: se você for o proprietário principal da página, adicione seu alias da Microsoft aqui (você não precisa de @microsoft.com, apenas o alias).
   * MS. Date: Atualize a data se você estiver adicionando conteúdo principal à página, mas não para correções como esclarecimento, formatação, gramática ou ortografia.
   * Palavras-chave: o Word ajuda na SEO (otimização do mecanismo de pesquisa). Adicione palavras-chave, separadas por uma vírgula e um espaço, que são específicos do seu artigo (mas sem pontuação após a última palavra-chave na sua lista); Você não precisa adicionar palavras-chave globais que se aplicam a todos os artigos, pois elas são gerenciadas em outro lugar. 
5. Após concluir as edições do artigo, role para baixo e clique no botão **propor alteração de arquivo** .
6. Na página seguinte, clique em **criar solicitação de pull** para mesclar sua ramificação criada automaticamente em ' mestre '.
7. Repita as etapas acima para o próximo artigo que você deseja editar.

## <a name="renaming-or-deleting-an-existing-article"></a>Renomeando ou excluindo um artigo existente

Se sua alteração for renomear ou excluir um artigo existente, certifique-se de adicionar um redirecionamento. Dessa forma, qualquer pessoa com um link para o artigo existente ainda será encerrada no lugar certo. Os redirecionamentos são gerenciados pelo arquivo. openpublishing. Redirecting. JSON na raiz do repositório.

Para adicionar um redirecionamento a. openpublishing. redirectment. JSON, adicione uma entrada à matriz de `redirections`:

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- O `source_path` é o caminho relativo do repositório para o artigo antigo que você está removendo. Verifique se o caminho começa com `mixed-reality-docs` e termina com `.md`.
- O `redirect_url` é a URL pública relativa do artigo antigo para o novo artigo. Certifique-se de que **essa URL não** contém `mixed-reality-docs` ou `.md`, pois ela se refere à URL pública e não ao caminho do repositório. É permitido vincular a uma seção dentro do novo artigo usando `#section`. Você também pode usar um caminho absoluto para outro site aqui, se necessário.
- `redirect_document_id` indica se você deseja manter a ID do documento do arquivo anterior. O padrão é `false`. Use `true` se desejar preservar o valor do atributo `ms.documentid` do artigo Redirecionado. Se você preservar a ID do documento, os dados, como exibições de página e classificações, serão transferidos para o artigo de destino. Faça isso se o redirecionamento for basicamente uma renomeação, e não um ponteiro para um artigo diferente que cobre apenas alguns dos mesmos conteúdos.

Se você adicionar um redirecionamento, certifique-se de excluir o arquivo antigo também.

## <a name="creating-a-new-article"></a>Criando um novo artigo

Use o fluxo de trabalho a seguir para *criar novos artigos* no repositório de documentação por meio do GitHub em um navegador da Web:

1. Crie uma bifurcação da ramificação "mestre" do MicrosoftDocs/Mixed-Realm (usando o botão **bifurcar** no canto superior direito).

   ![Bifurcar a ramificação mestre.](images/forkbranch.png)
2. Na pasta "Mixed-Reality-docs", clique no botão **criar novo arquivo** no canto superior direito.
3. Crie um nome de página para o artigo (use hifens em vez de espaços e não use pontuação ou apóstrofos) e acrescente ". MD"

   ![Nomeie sua nova página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Certifique-se de criar o novo artigo de dentro da pasta "Mixed-Realm docs". Você pode confirmar isso verificando "/Mixed-Reality-docs/" na nova linha de nome de arquivo.

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

5. Preencha os campos de metadados relevantes de acordo com as instruções na [seção acima](#editing-an-existing-article).
6. Escreva o conteúdo do artigo usando [noções básicas de redução](#markdown-basics).
7. Adicione uma seção `## See also` na parte inferior do artigo com links para outros artigos relevantes.
8. Quando terminar, clique em **confirmar novo arquivo**.
9. Clique em **nova solicitação de pull** e mescle a ramificação ' mestre ' de sua bifurcação em MicrosoftDocs/Mixed-Realm ' Master ' (verifique se a seta está apontando da maneira correta).

   ![Criar solicitação de pull de sua bifurcação em MicrosoftDocs/Mixed-Realm](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Noções básicas de redução

Os recursos a seguir ajudarão você a aprender a editar a documentação usando a linguagem de redução:

- [Noções básicas de redução](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Cartaz de referência de visão geral](images/MarkdownPoster.pdf)
- [Recursos adicionais para a redução do texto para docs.microsoft.com](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Adicionando tabelas

Por causa da maneira como as tabelas de estilos docs.microsoft.com, elas não terão bordas ou estilos personalizados, mesmo que você experimente o CSS embutido. Parecerá funcionar por um curto período de tempo, mas eventualmente a plataforma removerá o estilo da tabela. Então, planeje com antecedência e mantenha suas tabelas simples. [Aqui está um site que facilita a redução das tabelas](https://www.tablesgenerator.com/markdown_tables).

A [extensão de redução de documentos para Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) também facilitará a geração de tabelas se você estiver usando [Visual Studio Code (veja abaixo)](#using-visual-studio-code) para editar a documentação.

### <a name="adding-images"></a>Adicionando imagens

Você precisará carregar suas imagens na pasta "Mixed-Reality docs/images" no repositório e, em seguida, referenciá-las adequadamente no artigo. As imagens aparecerão automaticamente em tamanho normal, o que significa que, se a imagem for grande, ela preencherá toda a largura do artigo. Portanto, recomendamos o dimensionamento prévio de suas imagens antes de carregá-las. A largura recomendada é entre 600 e 700 pixels, embora você deva dimensionar ou reduzir se for uma captura de tela densa ou uma fração de uma captura de tela, respectivamente.

>[!IMPORTANT]
>Você só pode carregar imagens para seu repositório bifurcado antes de Mesclar. Portanto, se você planeja adicionar imagens a um artigo, precisará [usar Visual Studio Code](#using-visual-studio-code) para adicionar as imagens à pasta "images" de sua bifurcação primeiro ou certifique-se de ter feito o seguinte em um navegador da Web:
>
>1. Bifurcado o repositório MicrosoftDocs/Mixed-Reality.
>2. Editou o artigo em sua bifurcação.
>3. Foram carregadas as imagens que você está referenciando em seu artigo para a pasta "Mixed-Realm-docs/images" em sua bifurcação.
>4. Criou uma **solicitação de pull** para mesclar sua bifurcação no Branch ' mestre ' da reality MicrosoftDocs/Mixed.
>
>Para saber como configurar seu próprio repositório bifurcado, siga as instruções para [criar um novo artigo](#creating-a-new-article).

## <a name="previewing-your-work"></a>Visualizando seu trabalho

Ao editar no GitHub por meio de um navegador da Web, você pode clicar na guia **Visualizar** próximo à parte superior da página para visualizar seu trabalho antes de confirmar. 

>[!NOTE]
>A visualização de suas alterações no review.docs.microsoft.com só está disponível para funcionários da Microsoft

Funcionários da Microsoft: depois que suas contribuições tiverem sido mescladas no Branch ' mestre ', você poderá ver qual será a aparência da documentação antes que ela seja pública em https://review.docs.microsoft.com/windows/mixed-reality?branch=master (encontre seu artigo usando o Sumário na coluna à esquerda).

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Editando no navegador versus editando com um cliente de desktop

A edição no navegador é a maneira mais fácil de fazer alterações rápidas, no entanto, há algumas desvantagens:

- Você não tem verificação ortográfica.
- Você não obtém nenhuma vinculação inteligente com outros artigos (você precisa digitar manualmente o nome do arquivo).
- Pode ser um trabalho difícil de carregar e fazer referência a imagens.

Se você preferir não lidar com esses problemas, talvez prefira usar um cliente de desktop como [Visual Studio Code](https://code.visualstudio.com/) com algumas [extensões úteis](#useful-extensions) para contribuir para a documentação.

## <a name="using-visual-studio-code"></a>Usando Visual Studio Code

Pelos motivos listados [acima](#editing-in-the-browser-vs-editing-with-a-desktop-client), você pode preferir usar um cliente de desktop para editar a documentação em vez de um navegador da Web. É recomendável usar [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Configuração

Siga estas etapas para configurar Visual Studio Code para trabalhar com este repositório:

1. Em um navegador da Web:
    1. Instale [o Git para seu computador](https://git-scm.com/downloads).
    2. Instale o [Visual Studio Code](https://code.visualstudio.com/).
    3. [Bifurcação MicrosoftDocs/Mixed-Realm,](#creating-a-new-article) se ainda não tiver feito isso.
    4. Em sua bifurcação, clique em **clonar ou baixar** e copie a URL.
2. Crie um clone local de sua bifurcação no Visual Studio Code:
    1. No menu **Exibir** , selecione **paleta de comandos**.
    2. Digite "Git: clone".
    3. Cole a URL que você acabou de copiar.
    4. Escolha onde salvar o clone em seu PC.
    5. Clique em **abrir repositório** no pop-up.

### <a name="editing-documentation"></a>Editando a documentação

Use o seguinte fluxo de trabalho para fazer alterações na documentação com Visual Studio Code:

>[!NOTE]
>Todas as diretrizes para [edição](#editing-an-existing-article) e [criação](#creating-a-new-article) de artigos, e os [fundamentos de redução de edição](#markdown-basics), a partir de acima aplicam-se também ao usar o Visual Studio Code.

1. Verifique se sua bifurcação clonada está atualizada com o repositório oficial.
   1. Em um navegador da Web, crie uma solicitação de pull para sincronizar alterações recentes de outros colaboradores em MicrosoftDocs/Mixed-Realm ' Master ' para sua bifurcação (verifique se a seta está apontando da maneira correta).
      
      ![Sincronizar alterações de MicrosoftDocs/Mixed-realm para sua bifurcação](images/sync_repos.PNG)
   2. Em Visual Studio Code, clique no botão Sincronizar para sincronizar sua bifurcação atualizada atualizada para o clone local.
      
      ![Clique no botão Sincronizar](images/sync_clone.png)
2. Crie ou edite artigos em seu repositório clonado usando Visual Studio Code.
   1. Edite um ou mais artigos (adicione imagens à pasta "imagens", se necessário).
   2. **Salve** as alterações no **Explorer**.
      
      ![Escolha "salvar tudo" no Gerenciador](images/explorer_save.png)
   3. **Confirmar todas** as alterações no **controle do código-fonte** (gravar mensagem de confirmação quando solicitado).
      
      ![Escolha "confirmar tudo" no controle do código-fonte](images/source_control_commit.png)
   4. Clique no botão **sincronizar** para sincronizar suas alterações de volta à origem (sua bifurcação no GitHub).
      
      ![Clique no botão Sincronizar](images/sync_back.png)
3. Em um navegador da Web, crie uma solicitação de pull para sincronizar novas alterações na bifurcação de volta para MicrosoftDocs/Mixed-Realm ' Master ' (verifique se a seta está apontando da maneira correta).

   ![Criar solicitação de pull de sua bifurcação em MicrosoftDocs/Mixed-Realm](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Extensões úteis

As seguintes extensões de Visual Studio Code são muito úteis ao editar a documentação:

- [Extensão de redução de documentos para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -use **ALT + M** para abrir um menu de opções de criação de docs como:
   - Pesquisar e fazer referência a imagens que você carregou.
   - Adicione formatação como listas, tabelas e chamadas de documentos específicas, como `>[!NOTE]`.
   - Pesquisar e referenciar links internos e indicadores (links para seções específicas em uma página).
   - Erros de formatação são realçados (passe o mouse sobre o erro para saber mais).
- [Verificador ortográfico de código](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -palavras incorretas serão sublinhadas; Clique com o botão direito do mouse em uma palavra incorreta para alterá-la ou salvá-la no dicionário.
