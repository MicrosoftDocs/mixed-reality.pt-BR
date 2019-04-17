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
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="1f017-103">Contribuindo para a documentação do desenvolvedor do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1f017-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="1f017-104">Bem-vindo à [repositório público para a documentação do desenvolvedor do Windows Mixed Reality](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span><span class="sxs-lookup"><span data-stu-id="1f017-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="1f017-105">Qualquer artigo, você cria ou edita neste repositório **estarão visíveis para o público.**</span><span class="sxs-lookup"><span data-stu-id="1f017-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="1f017-106">Os documentos de realidade mista do Windows agora estão na plataforma docs.microsoft.com, que usa Markdown para GitHub (com recursos de Markdig).</span><span class="sxs-lookup"><span data-stu-id="1f017-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="1f017-107">Essencialmente, o conteúdo que você pode editar este repositório se transformam em formatado e estilizadas páginas que aparecem em https://docs.microsoft.com/windows/mixed-reality.</span><span class="sxs-lookup"><span data-stu-id="1f017-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="1f017-108">Esta página aborda as etapas básicas e diretrizes para contribuir, bem como links para Noções básicas de Markdown.</span><span class="sxs-lookup"><span data-stu-id="1f017-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="1f017-109">Agradecemos sua contribuição!</span><span class="sxs-lookup"><span data-stu-id="1f017-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1f017-110">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="1f017-110">Before you start</span></span>

<span data-ttu-id="1f017-111">Se você não tiver uma, você precisará [criar uma conta do GitHub](https://github.com/join).</span><span class="sxs-lookup"><span data-stu-id="1f017-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="1f017-112">Se você for um funcionário da Microsoft, vincular sua conta do GitHub para seu alias da Microsoft sobre o [portal do Microsoft Open Source](https://repos.opensource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="1f017-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="1f017-113">Junte-se a **"Microsoft"** e **"MicrosoftDocs"** organizações).</span><span class="sxs-lookup"><span data-stu-id="1f017-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="1f017-114">Ao configurar sua conta do GitHub, também recomendamos essas precauções de segurança:</span><span class="sxs-lookup"><span data-stu-id="1f017-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="1f017-115">Criar uma [senha forte para sua conta do Github](https://github.com/settings/admin).</span><span class="sxs-lookup"><span data-stu-id="1f017-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="1f017-116">Habilitar [autenticação de dois fatores](https://github.com/settings/two_factor_authentication/configure).</span><span class="sxs-lookup"><span data-stu-id="1f017-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="1f017-117">Salvar sua [códigos de recuperação](https://github.com/settings/auth/recovery-codes) em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="1f017-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="1f017-118">Atualização de seu [configurações de perfil público](https://github.com/settings/profile).</span><span class="sxs-lookup"><span data-stu-id="1f017-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="1f017-119">Defina seu nome e considere a configuração de seu *email público* ao *não mostrar o meu endereço de email*.</span><span class="sxs-lookup"><span data-stu-id="1f017-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="1f017-120">É recomendável que você carregar uma foto de perfil, como uma miniatura será mostrada nas páginas do docs para o qual você contribuir.</span><span class="sxs-lookup"><span data-stu-id="1f017-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="1f017-121">Se você planeja usar um fluxo de trabalho de linha de comando, considere a configuração de [Git Credential Manager para Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) para que você não precise inserir sua senha cada vez que você faça uma contribuição.</span><span class="sxs-lookup"><span data-stu-id="1f017-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="1f017-122">Executar essas etapas é importante, pois o sistema de publicação está vinculado ao GitHub e você será listado como autor ou colaborador para cada artigo usando seu alias do GitHub.</span><span class="sxs-lookup"><span data-stu-id="1f017-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="1f017-123">Editando um artigo existente</span><span class="sxs-lookup"><span data-stu-id="1f017-123">Editing an existing article</span></span>

<span data-ttu-id="1f017-124">Use o seguinte fluxo de trabalho para fazer atualizações para *um artigo existente* por meio do GitHub em um navegador da web:</span><span class="sxs-lookup"><span data-stu-id="1f017-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="1f017-125">Navegue até o artigo que deseja editar na pasta "misto-realidade-docs".</span><span class="sxs-lookup"><span data-stu-id="1f017-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="1f017-126">Selecione o botão Editar (ícone de lápis) no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="1f017-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="1f017-127">Isso bifurcará automaticamente uma ramificação descartável desativar o branch 'mestre'.</span><span class="sxs-lookup"><span data-stu-id="1f017-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![Edite um artigo.](images/editpage.png)
3. <span data-ttu-id="1f017-129">Para editar o conteúdo do artigo (consulte ["Noções básicas de Markdown"](#markdown-basics) abaixo para obter orientação).</span><span class="sxs-lookup"><span data-stu-id="1f017-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="1f017-130">Atualize os metadados conforme relevante na parte superior de cada artigo:</span><span class="sxs-lookup"><span data-stu-id="1f017-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="1f017-131">title: Isso é o título da página que aparece na guia do navegador quando o artigo estiver sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="1f017-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="1f017-132">Como isso é usado para SEO e indexação, você não deve alterar o título, a menos que necessário (embora isso seja menos crítico antes de se tornar pública documentação).</span><span class="sxs-lookup"><span data-stu-id="1f017-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="1f017-133">description: Escreva uma breve descrição do conteúdo do artigo.</span><span class="sxs-lookup"><span data-stu-id="1f017-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="1f017-134">Isso ajuda na descoberta e SEO.</span><span class="sxs-lookup"><span data-stu-id="1f017-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="1f017-135">Autor: Se você for o proprietário principal da página, adicione aqui seu alias do GitHub.</span><span class="sxs-lookup"><span data-stu-id="1f017-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="1f017-136">ms.author: Se você for o proprietário principal da página, adicione o alias aqui da Microsoft (você não precisa @microsoft.com, apenas o alias).</span><span class="sxs-lookup"><span data-stu-id="1f017-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="1f017-137">ms.date: Atualize a data, se você estiver adicionando o conteúdo principal para a página, mas não para correções como esclarecimento, formatação, gramática, ou de ortografia.</span><span class="sxs-lookup"><span data-stu-id="1f017-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="1f017-138">palavras-chave: Palavras-chave ajudam a SEO (otimização do mecanismo de pesquisa).</span><span class="sxs-lookup"><span data-stu-id="1f017-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="1f017-139">Adicionar palavras-chave, separadas por uma vírgula e um espaço, que são específicas para seu artigo (mas sem pontuação após a última palavra-chave em sua lista); Você não precisa adicionar palavras-chave global que se aplicam a todos os artigos, como aqueles são gerenciados em outros lugares.</span><span class="sxs-lookup"><span data-stu-id="1f017-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="1f017-140">Quando tiver concluído suas edições de artigo, role para baixo e clique no **propor alteração de arquivo** botão.</span><span class="sxs-lookup"><span data-stu-id="1f017-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="1f017-141">Na próxima página, clique em **criar solicitação de pull** para mesclar sua ramificação criada automaticamente em 'mestre'.</span><span class="sxs-lookup"><span data-stu-id="1f017-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="1f017-142">Repita as etapas acima para o próximo artigo que você deseja editar.</span><span class="sxs-lookup"><span data-stu-id="1f017-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="1f017-143">Criar um novo artigo</span><span class="sxs-lookup"><span data-stu-id="1f017-143">Creating a new article</span></span>

<span data-ttu-id="1f017-144">Use o seguinte fluxo de trabalho para *criar novos artigos* no repositório de documentação por meio do GitHub em um navegador da web:</span><span class="sxs-lookup"><span data-stu-id="1f017-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="1f017-145">Crie uma bifurcação de branch 'mestre' MicrosoftDocs/realidade misturada (usando o **bifurcação** botão no canto superior direito).</span><span class="sxs-lookup"><span data-stu-id="1f017-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![A ramificação mestre da bifurcação.](images/forkbranch.png)
2. <span data-ttu-id="1f017-147">Na pasta "misto-realidade-docs", clique o **criar novo arquivo** botão no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="1f017-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="1f017-148">Criar um nome de página para o artigo (use hifens em vez de espaços e não use pontuação ou apóstrofos) e acrescente ". MD"</span><span class="sxs-lookup"><span data-stu-id="1f017-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![Nomeie a nova página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="1f017-150">Verifique se que você cria o novo artigo de dentro da pasta "misto-realidade-docs".</span><span class="sxs-lookup"><span data-stu-id="1f017-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="1f017-151">Você pode confirmar isso verificando "/ misto-realidade-docs /" na linha do nome de arquivo novo.</span><span class="sxs-lookup"><span data-stu-id="1f017-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="1f017-152">Na parte superior da sua nova página, adicione o seguinte bloco de metadados:</span><span class="sxs-lookup"><span data-stu-id="1f017-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="1f017-153">Preencha os campos de metadados relevantes pelas instruções de [acima da seção](#editing-an-existing-article).</span><span class="sxs-lookup"><span data-stu-id="1f017-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="1f017-154">Gravação artigo conteúdo usando [Noções básicas de Markdown](#markdown-basics).</span><span class="sxs-lookup"><span data-stu-id="1f017-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="1f017-155">Adicionar um `## See also` seção na parte inferior do artigo com links para outros artigos pertinentes.</span><span class="sxs-lookup"><span data-stu-id="1f017-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="1f017-156">Quando terminar, clique em **confirmação novo arquivo**.</span><span class="sxs-lookup"><span data-stu-id="1f017-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="1f017-157">Clique em **nova solicitação de pull** e mesclar a branch 'mestre' de seu fork em MicrosoftDocs/realidade misturada 'master' (Verifique se a seta está apontando a maneira correta).</span><span class="sxs-lookup"><span data-stu-id="1f017-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Criar solicitação de pull da bifurcação em MicrosoftDocs/realidade misturada](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="1f017-159">Noções básicas de markdown</span><span class="sxs-lookup"><span data-stu-id="1f017-159">Markdown basics</span></span>

<span data-ttu-id="1f017-160">Os recursos a seguir ajudarão você a aprender como editar a documentação usando a linguagem Markdown:</span><span class="sxs-lookup"><span data-stu-id="1f017-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="1f017-161">Noções básicas de markdown</span><span class="sxs-lookup"><span data-stu-id="1f017-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="1f017-162">Pôster de referência de markdown no instantâneo</span><span class="sxs-lookup"><span data-stu-id="1f017-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="1f017-163">Recursos adicionais para a gravação de Markdown para docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="1f017-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="1f017-164">Adicionando tabelas</span><span class="sxs-lookup"><span data-stu-id="1f017-164">Adding tables</span></span>

<span data-ttu-id="1f017-165">Por causa das tabelas de estilos de docs.microsoft.com de forma, eles não terão bordas ou estilos personalizados, mesmo se você tentar CSSS embutidas.</span><span class="sxs-lookup"><span data-stu-id="1f017-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="1f017-166">Ele parecerá funcionar por um curto período de tempo, mas, eventualmente, a plataforma será retirar o estilo para fora da tabela.</span><span class="sxs-lookup"><span data-stu-id="1f017-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="1f017-167">Portanto, planeje com antecedência e manter suas tabelas simples.</span><span class="sxs-lookup"><span data-stu-id="1f017-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="1f017-168">[Aqui está um site que facilita as tabelas Markdown](http://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="1f017-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="1f017-169">O [extensão de Markdown do Docs para Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) também torna a tabela geração fácil se você estiver usando [Visual Studio Code (veja abaixo)](#using-visual-studio-code) para editar a documentação.</span><span class="sxs-lookup"><span data-stu-id="1f017-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="1f017-170">Adicionando imagens</span><span class="sxs-lookup"><span data-stu-id="1f017-170">Adding images</span></span>

<span data-ttu-id="1f017-171">Você precisará carregar suas imagens para a pasta "misto-realidade-docs/imagens" no repositório e, em seguida, referenciá-los adequadamente no artigo.</span><span class="sxs-lookup"><span data-stu-id="1f017-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="1f017-172">Imagens serão exibidos automaticamente em tamanho normal, que significa que se sua imagem for grande, ele preencherá toda a largura do artigo.</span><span class="sxs-lookup"><span data-stu-id="1f017-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="1f017-173">Assim, é recomendável previamente suas imagens de dimensionamento antes de carregá-los.</span><span class="sxs-lookup"><span data-stu-id="1f017-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="1f017-174">A largura recomendada é entre pixels de 600 e 700, embora você deve dimensionar para cima ou para baixo, se for uma captura de tela densa ou uma fração de uma captura de tela, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1f017-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1f017-175">Você só pode carregar imagens ao seu repositório bifurcado antes da mesclagem.</span><span class="sxs-lookup"><span data-stu-id="1f017-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="1f017-176">Portanto, se você planeja adicionar imagens a um artigo, você precisará [usar o Visual Studio Code](#using-visual-studio-code) para adicionar imagens à pasta do seu fork "imagens" pela primeira vez ou certifique-se de fazer o seguinte em um navegador da web:</span><span class="sxs-lookup"><span data-stu-id="1f017-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="1f017-177">Bifurcado o repositório MicrosoftDocs/realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="1f017-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="1f017-178">Editar o artigo na sua bifurcação.</span><span class="sxs-lookup"><span data-stu-id="1f017-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="1f017-179">Carregamos as imagens que você está fazendo referência em seu artigo para a pasta "misto-realidade-docs/imagens" na sua bifurcação.</span><span class="sxs-lookup"><span data-stu-id="1f017-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="1f017-180">Criado um **solicitação de pull** para mesclar sua bifurcação ao branch 'mestre' MicrosoftDocs/realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="1f017-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="1f017-181">Para saber como configurar seu próprio repositório bifurcado, siga as instruções para [criando um novo artigo](#creating-a-new-article).</span><span class="sxs-lookup"><span data-stu-id="1f017-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="1f017-182">Visualizando seu trabalho</span><span class="sxs-lookup"><span data-stu-id="1f017-182">Previewing your work</span></span>

<span data-ttu-id="1f017-183">Ao editar no GitHub por meio de um navegador da web, você pode clicar na **visualização** guia na parte superior da página para visualizar seu trabalho antes de confirmar.</span><span class="sxs-lookup"><span data-stu-id="1f017-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="1f017-184">Visualizar as alterações em review.docs.microsoft.com só está disponível para os funcionários da Microsoft</span><span class="sxs-lookup"><span data-stu-id="1f017-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="1f017-185">Os funcionários da Microsoft: depois que suas contribuições foram mescladas no branch 'mestre', você pode ver a aparência a documentação antes de ele se tornar público no https://review.docs.microsoft.com/windows/mixed-reality?branch=master (encontrar seu artigo usando o sumário na coluna à esquerda).</span><span class="sxs-lookup"><span data-stu-id="1f017-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="1f017-186">Editar no navegador versus edição com um cliente de desktop</span><span class="sxs-lookup"><span data-stu-id="1f017-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="1f017-187">Editar no navegador é a maneira mais fácil de fazer alterações, no entanto, há algumas desvantagens:</span><span class="sxs-lookup"><span data-stu-id="1f017-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="1f017-188">Você não obterá a verificação ortográfica.</span><span class="sxs-lookup"><span data-stu-id="1f017-188">You don't get spell-check.</span></span>
- <span data-ttu-id="1f017-189">Você não terá qualquer inteligente vinculação para outros artigos (você precisa digitar manualmente o nome de arquivo do artigo).</span><span class="sxs-lookup"><span data-stu-id="1f017-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="1f017-190">Ele pode ser um problema para carregar e imagens de referência.</span><span class="sxs-lookup"><span data-stu-id="1f017-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="1f017-191">Se você seria melhor não lidar com esses problemas, talvez você prefira usar um cliente da área de trabalho, como [Visual Studio Code](https://code.visualstudio.com/) com algumas [extensões úteis](#useful-extensions) pode contribuir com documentação.</span><span class="sxs-lookup"><span data-stu-id="1f017-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="1f017-192">Usando o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1f017-192">Using Visual Studio Code</span></span>

<span data-ttu-id="1f017-193">Pelas razões listadas [acima](#editing-in-the-browser-vs-editing-with-a-desktop-client), talvez você prefira usando um cliente de área de trabalho para editar a documentação em vez de um navegador da web.</span><span class="sxs-lookup"><span data-stu-id="1f017-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="1f017-194">É recomendável usar [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="1f017-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="1f017-195">Configuração</span><span class="sxs-lookup"><span data-stu-id="1f017-195">Setup</span></span>

<span data-ttu-id="1f017-196">Siga estas etapas para configurar o Visual Studio Code para trabalhar com este repositório:</span><span class="sxs-lookup"><span data-stu-id="1f017-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="1f017-197">Em um navegador da web:</span><span class="sxs-lookup"><span data-stu-id="1f017-197">In a web browser:</span></span>
    1. <span data-ttu-id="1f017-198">Instale [Git para seu PC](https://git-scm.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="1f017-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="1f017-199">Instale [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="1f017-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="1f017-200">[Crie um fork MicrosoftDocs/realidade misturada](#creating-a-new-article) se você ainda não fez isso.</span><span class="sxs-lookup"><span data-stu-id="1f017-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="1f017-201">Na sua bifurcação, clique em **clonar ou baixar** e copie a URL.</span><span class="sxs-lookup"><span data-stu-id="1f017-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="1f017-202">Crie um clone local da sua bifurcação no Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="1f017-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="1f017-203">Dos **modo de exibição** menu, selecione **paleta de comandos**.</span><span class="sxs-lookup"><span data-stu-id="1f017-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="1f017-204">Tipo "Git:Clone".</span><span class="sxs-lookup"><span data-stu-id="1f017-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="1f017-205">Cole a URL que você acabou de copiar.</span><span class="sxs-lookup"><span data-stu-id="1f017-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="1f017-206">Escolha onde salvar o clone em seu computador.</span><span class="sxs-lookup"><span data-stu-id="1f017-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="1f017-207">Clique em **abrir repositório** no pop-up.</span><span class="sxs-lookup"><span data-stu-id="1f017-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="1f017-208">Documentação de edição</span><span class="sxs-lookup"><span data-stu-id="1f017-208">Editing documentation</span></span>

<span data-ttu-id="1f017-209">Use o seguinte fluxo de trabalho para fazer alterações a documentação do Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="1f017-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="1f017-210">Todas as diretrizes para [editando](#editing-an-existing-article) e [criando](#creating-a-new-article) artigos e o [Noções básicas de edição de Markdown](#markdown-basics), acima aplica-se ao usar o Visual Studio Code também.</span><span class="sxs-lookup"><span data-stu-id="1f017-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="1f017-211">Verifique se que seu fork clonado está atualizada com o repositório oficial.</span><span class="sxs-lookup"><span data-stu-id="1f017-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="1f017-212">Em um navegador da web, crie uma solicitação de pull para sincronizar as alterações recentes de outros colaboradores no MicrosoftDocs/realidade misturada 'mestre' para a bifurcação (Verifique se a seta está apontando da maneira correta).</span><span class="sxs-lookup"><span data-stu-id="1f017-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Alterações de sincronização de MicrosoftDocs/realidade misturada para sua bifurcação](images/sync_repos.PNG)
   2. <span data-ttu-id="1f017-214">No Visual Studio Code, clique no botão de sincronização para sincronizar seu fork recentemente atualizada para o clone local.</span><span class="sxs-lookup"><span data-stu-id="1f017-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![Clique no botão de sincronização](images/sync_clone.png)
2. <span data-ttu-id="1f017-216">Criar ou editar artigos no repositório clonado usando o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1f017-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="1f017-217">Edite um ou mais artigos (Adicionar imagens a pasta "imagens" se necessário).</span><span class="sxs-lookup"><span data-stu-id="1f017-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="1f017-218">**Salve** alterações na **Explorer**.</span><span class="sxs-lookup"><span data-stu-id="1f017-218">**Save** changes in **Explorer**.</span></span>
      
      ![Escolher "Salvar todos os" no Explorer](images/explorer_save.png)
   3. <span data-ttu-id="1f017-220">**Confirmar tudo** alterações na **controle de origem** (gravar a mensagem de confirmação quando solicitado).</span><span class="sxs-lookup"><span data-stu-id="1f017-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![Escolha "Confirmar tudo" no controle de origem](images/source_control_commit.png)
   4. <span data-ttu-id="1f017-222">Clique o **sincronização** botão para sincronizar suas alterações de volta para a origem (seu fork no GitHub).</span><span class="sxs-lookup"><span data-stu-id="1f017-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![Clique no botão de sincronização](images/sync_back.png)
3. <span data-ttu-id="1f017-224">Em um navegador da web, crie uma solicitação de pull para sincronizar as novas alterações na sua bifurcação para MicrosoftDocs/realidade misturada 'master' (Verifique se a seta está apontando a maneira correta).</span><span class="sxs-lookup"><span data-stu-id="1f017-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Criar solicitação de pull da bifurcação em MicrosoftDocs/realidade misturada](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="1f017-226">Extensões úteis</span><span class="sxs-lookup"><span data-stu-id="1f017-226">Useful extensions</span></span>

<span data-ttu-id="1f017-227">As seguintes extensões do Visual Studio Code são muito úteis quando você editar a documentação:</span><span class="sxs-lookup"><span data-stu-id="1f017-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="1f017-228">[Extensão de Markdown do docs para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -Use **Alt + M** para abrir um menu de opções, como de criação do docs:</span><span class="sxs-lookup"><span data-stu-id="1f017-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="1f017-229">Imagens de referência e de pesquisa que você carregou.</span><span class="sxs-lookup"><span data-stu-id="1f017-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="1f017-230">Adicione formatação, como listas, tabelas e balões específicas de documentos, como `>[!NOTE]`.</span><span class="sxs-lookup"><span data-stu-id="1f017-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="1f017-231">Pesquisa e referência de links internos e indicadores (links para seções específicas dentro de uma página).</span><span class="sxs-lookup"><span data-stu-id="1f017-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="1f017-232">Erros de formatação são realçados (passar o mouse sobre o erro para obter mais informações).</span><span class="sxs-lookup"><span data-stu-id="1f017-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="1f017-233">[Código de verificação ortográfica](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -palavras incorretas serão sublinhadas; clique duas vezes em uma palavra incorreta para alterá-la ou salvá-lo ao dicionário.</span><span class="sxs-lookup"><span data-stu-id="1f017-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
