---
title: Instruções de contribuição
description: Como contribuir para a documentação do Windows Mixed Reality.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516269"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="16acf-103">Contribuindo para a documentação do desenvolvedor do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="16acf-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="16acf-104">Bem-vindo à [documentação de desenvolvedor do repositório público para Windows Mixed Reality](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span><span class="sxs-lookup"><span data-stu-id="16acf-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="16acf-105">Todos os artigos que você criar ou editar neste repositório **estarão visíveis para o público.**</span><span class="sxs-lookup"><span data-stu-id="16acf-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="16acf-106">Os documentos de realidade misturada do Windows agora estão na plataforma docs.microsoft.com, que usa a redução do tipo GitHub (com recursos do Markdig).</span><span class="sxs-lookup"><span data-stu-id="16acf-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="16acf-107">Essencialmente, o conteúdo que você edita nesse repositório é ativado em páginas formatadas e estilizadas que aparecem em https://docs.microsoft.com/windows/mixed-reality.</span><span class="sxs-lookup"><span data-stu-id="16acf-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="16acf-108">Esta página aborda as etapas e diretrizes básicas de contribuição, bem como links para noções básicas de redução.</span><span class="sxs-lookup"><span data-stu-id="16acf-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="16acf-109">Agradecemos sua contribuição!</span><span class="sxs-lookup"><span data-stu-id="16acf-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="16acf-110">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="16acf-110">Before you start</span></span>

<span data-ttu-id="16acf-111">Se você ainda não tiver uma, precisará [criar uma conta do GitHub](https://github.com/join).</span><span class="sxs-lookup"><span data-stu-id="16acf-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="16acf-112">Se você for um funcionário da Microsoft, vincule sua conta do GitHub ao seu alias da Microsoft no [portal do Microsoft Open Source](https://repos.opensource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="16acf-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="16acf-113">Junte-se às organizações **"Microsoft"** e **"MicrosoftDocs"** ).</span><span class="sxs-lookup"><span data-stu-id="16acf-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="16acf-114">Ao configurar sua conta do GitHub, também recomendamos estas precauções de segurança:</span><span class="sxs-lookup"><span data-stu-id="16acf-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="16acf-115">Crie uma [senha forte para sua conta do GitHub](https://github.com/settings/admin).</span><span class="sxs-lookup"><span data-stu-id="16acf-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="16acf-116">Habilite [a autenticação de dois fatores](https://github.com/settings/two_factor_authentication/configure).</span><span class="sxs-lookup"><span data-stu-id="16acf-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="16acf-117">Salve seus [códigos de recuperação](https://github.com/settings/auth/recovery-codes) em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="16acf-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="16acf-118">Atualize suas [configurações de perfil público](https://github.com/settings/profile).</span><span class="sxs-lookup"><span data-stu-id="16acf-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="16acf-119">Defina seu nome e considere definir seu *email público* para *não mostrar meu endereço de email*.</span><span class="sxs-lookup"><span data-stu-id="16acf-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="16acf-120">Recomendamos que você carregue uma imagem de perfil, uma vez que uma miniatura será mostrada nas páginas de documentos nas quais você contribuir.</span><span class="sxs-lookup"><span data-stu-id="16acf-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="16acf-121">Se você planeja usar um fluxo de trabalho de linha de comando, considere configurar o [git Credential Manager para Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) para que você não precise inserir sua senha sempre que fizer uma contribuição.</span><span class="sxs-lookup"><span data-stu-id="16acf-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="16acf-122">A execução dessas etapas é importante, pois o sistema de publicação está vinculado ao GitHub e você será listado como autor ou colaborador para cada artigo usando seu alias do GitHub.</span><span class="sxs-lookup"><span data-stu-id="16acf-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="16acf-123">Editando um artigo existente</span><span class="sxs-lookup"><span data-stu-id="16acf-123">Editing an existing article</span></span>

<span data-ttu-id="16acf-124">Use o seguinte fluxo de trabalho para fazer atualizações em *um artigo existente* por meio do GitHub em um navegador da Web:</span><span class="sxs-lookup"><span data-stu-id="16acf-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="16acf-125">Navegue até o artigo que você deseja editar na pasta "Mixed-realde docs".</span><span class="sxs-lookup"><span data-stu-id="16acf-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="16acf-126">Selecione o botão Editar (ícone de lápis) no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="16acf-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="16acf-127">Isso bifurcará automaticamente uma ramificação descartável da ramificação ' mestre '.</span><span class="sxs-lookup"><span data-stu-id="16acf-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![Edite um artigo.](images/editpage.png)
3. <span data-ttu-id="16acf-129">Edite o conteúdo do artigo (consulte ["Noções básicas de redução"](#markdown-basics) abaixo para obter orientação).</span><span class="sxs-lookup"><span data-stu-id="16acf-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="16acf-130">Atualize os metadados como relevantes na parte superior de cada artigo:</span><span class="sxs-lookup"><span data-stu-id="16acf-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="16acf-131">título Este é o título da página que aparece na guia navegador quando o artigo está sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="16acf-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="16acf-132">Como isso é usado para a SEO e a indexação, você não deve alterar o título, a menos que seja necessário (embora isso seja menos crítico antes que a documentação fique pública).</span><span class="sxs-lookup"><span data-stu-id="16acf-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="16acf-133">description: Escreva uma breve descrição do conteúdo do artigo.</span><span class="sxs-lookup"><span data-stu-id="16acf-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="16acf-134">Isso ajuda na SEO e na descoberta.</span><span class="sxs-lookup"><span data-stu-id="16acf-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="16acf-135">autorização Se você for o proprietário principal da página, adicione seu alias do GitHub aqui.</span><span class="sxs-lookup"><span data-stu-id="16acf-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="16acf-136">MS. Author: Se você for o proprietário principal da página, adicione seu alias da Microsoft aqui (você não precisa @microsoft.com, apenas o alias).</span><span class="sxs-lookup"><span data-stu-id="16acf-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="16acf-137">MS. Date: Atualize a data se você estiver adicionando conteúdo principal à página, mas não para correções como esclarecimento, formatação, gramática ou ortografia.</span><span class="sxs-lookup"><span data-stu-id="16acf-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="16acf-138">Palavras-chave As palavras-chave auxiliam na SEO (otimização do mecanismo de pesquisa).</span><span class="sxs-lookup"><span data-stu-id="16acf-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="16acf-139">Adicione palavras-chave, separadas por uma vírgula e um espaço, que são específicos do seu artigo (mas sem pontuação após a última palavra-chave na sua lista); Você não precisa adicionar palavras-chave globais que se aplicam a todos os artigos, pois elas são gerenciadas em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="16acf-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="16acf-140">Após concluir as edições do artigo, role para baixo e clique no botão **propor alteração de arquivo** .</span><span class="sxs-lookup"><span data-stu-id="16acf-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="16acf-141">Na página seguinte, clique em **criar solicitação de pull** para mesclar sua ramificação criada automaticamente em ' mestre '.</span><span class="sxs-lookup"><span data-stu-id="16acf-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="16acf-142">Repita as etapas acima para o próximo artigo que você deseja editar.</span><span class="sxs-lookup"><span data-stu-id="16acf-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="16acf-143">Criando um novo artigo</span><span class="sxs-lookup"><span data-stu-id="16acf-143">Creating a new article</span></span>

<span data-ttu-id="16acf-144">Use o fluxo de trabalho a seguir para *criar novos artigos* no repositório de documentação por meio do GitHub em um navegador da Web:</span><span class="sxs-lookup"><span data-stu-id="16acf-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="16acf-145">Crie uma bifurcação da ramificação "mestre" do MicrosoftDocs/Mixed-Realm  (usando o botão bifurcar no canto superior direito).</span><span class="sxs-lookup"><span data-stu-id="16acf-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Bifurcar a ramificação mestre.](images/forkbranch.png)
2. <span data-ttu-id="16acf-147">Na pasta "Mixed-Reality-docs", clique no botão **criar novo arquivo** no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="16acf-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="16acf-148">Crie um nome de página para o artigo (use hifens em vez de espaços e não use pontuação ou apóstrofos) e acrescente ". MD"</span><span class="sxs-lookup"><span data-stu-id="16acf-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![Nomeie sua nova página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="16acf-150">Certifique-se de criar o novo artigo de dentro da pasta "Mixed-Realm docs".</span><span class="sxs-lookup"><span data-stu-id="16acf-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="16acf-151">Você pode confirmar isso verificando "/Mixed-Reality-docs/" na nova linha de nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="16acf-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="16acf-152">Na parte superior da sua nova página, adicione o seguinte bloco de metadados:</span><span class="sxs-lookup"><span data-stu-id="16acf-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="16acf-153">Preencha os campos de metadados relevantes de acordo com as instruções na [seção acima](#editing-an-existing-article).</span><span class="sxs-lookup"><span data-stu-id="16acf-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="16acf-154">Escreva o conteúdo do artigo usando [noções básicas de redução](#markdown-basics).</span><span class="sxs-lookup"><span data-stu-id="16acf-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="16acf-155">Adicione uma `## See also` seção na parte inferior do artigo com links para outros artigos relevantes.</span><span class="sxs-lookup"><span data-stu-id="16acf-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="16acf-156">Quando terminar, clique em **confirmar novo arquivo**.</span><span class="sxs-lookup"><span data-stu-id="16acf-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="16acf-157">Clique em **nova solicitação de pull** e mescle a ramificação ' mestre ' de sua bifurcação em MicrosoftDocs/Mixed-Realm ' Master ' (verifique se a seta está apontando da maneira correta).</span><span class="sxs-lookup"><span data-stu-id="16acf-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Criar solicitação de pull de sua bifurcação em MicrosoftDocs/Mixed-Realm](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="16acf-159">Noções básicas de redução</span><span class="sxs-lookup"><span data-stu-id="16acf-159">Markdown basics</span></span>

<span data-ttu-id="16acf-160">Os recursos a seguir ajudarão você a aprender a editar a documentação usando a linguagem de redução:</span><span class="sxs-lookup"><span data-stu-id="16acf-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="16acf-161">Noções básicas de redução</span><span class="sxs-lookup"><span data-stu-id="16acf-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="16acf-162">Cartaz de referência de visão geral</span><span class="sxs-lookup"><span data-stu-id="16acf-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="16acf-163">Recursos adicionais para a redução do texto para docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="16acf-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="16acf-164">Adicionando tabelas</span><span class="sxs-lookup"><span data-stu-id="16acf-164">Adding tables</span></span>

<span data-ttu-id="16acf-165">Por causa da maneira como as tabelas de estilos docs.microsoft.com, elas não terão bordas ou estilos personalizados, mesmo que você experimente o CSS embutido.</span><span class="sxs-lookup"><span data-stu-id="16acf-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="16acf-166">Parecerá funcionar por um curto período de tempo, mas eventualmente a plataforma removerá o estilo da tabela.</span><span class="sxs-lookup"><span data-stu-id="16acf-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="16acf-167">Então, planeje com antecedência e mantenha suas tabelas simples.</span><span class="sxs-lookup"><span data-stu-id="16acf-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="16acf-168">[Aqui está um site que facilita a redução das tabelas](http://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="16acf-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="16acf-169">A [extensão de redução de documentos para Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) também facilitará a geração de tabelas se você estiver usando [Visual Studio Code (veja abaixo)](#using-visual-studio-code) para editar a documentação.</span><span class="sxs-lookup"><span data-stu-id="16acf-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="16acf-170">Adicionando imagens</span><span class="sxs-lookup"><span data-stu-id="16acf-170">Adding images</span></span>

<span data-ttu-id="16acf-171">Você precisará carregar suas imagens na pasta "Mixed-Reality docs/images" no repositório e, em seguida, referenciá-las adequadamente no artigo.</span><span class="sxs-lookup"><span data-stu-id="16acf-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="16acf-172">As imagens aparecerão automaticamente em tamanho normal, o que significa que, se a imagem for grande, ela preencherá toda a largura do artigo.</span><span class="sxs-lookup"><span data-stu-id="16acf-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="16acf-173">Portanto, recomendamos o dimensionamento prévio de suas imagens antes de carregá-las.</span><span class="sxs-lookup"><span data-stu-id="16acf-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="16acf-174">A largura recomendada é entre 600 e 700 pixels, embora você deva dimensionar ou reduzir se for uma captura de tela densa ou uma fração de uma captura de tela, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="16acf-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="16acf-175">Você só pode carregar imagens para seu repositório bifurcado antes de Mesclar.</span><span class="sxs-lookup"><span data-stu-id="16acf-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="16acf-176">Portanto, se você planeja adicionar imagens a um artigo, precisará [usar Visual Studio Code](#using-visual-studio-code) para adicionar as imagens à pasta "images" de sua bifurcação primeiro ou certifique-se de ter feito o seguinte em um navegador da Web:</span><span class="sxs-lookup"><span data-stu-id="16acf-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="16acf-177">Bifurcado o repositório MicrosoftDocs/Mixed-Reality.</span><span class="sxs-lookup"><span data-stu-id="16acf-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="16acf-178">Editou o artigo em sua bifurcação.</span><span class="sxs-lookup"><span data-stu-id="16acf-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="16acf-179">Foram carregadas as imagens que você está referenciando em seu artigo para a pasta "Mixed-Realm-docs/images" em sua bifurcação.</span><span class="sxs-lookup"><span data-stu-id="16acf-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="16acf-180">Criou uma **solicitação de pull** para mesclar sua bifurcação no Branch ' mestre ' da reality MicrosoftDocs/Mixed.</span><span class="sxs-lookup"><span data-stu-id="16acf-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="16acf-181">Para saber como configurar seu próprio repositório bifurcado, siga as instruções para [criar um novo artigo](#creating-a-new-article).</span><span class="sxs-lookup"><span data-stu-id="16acf-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="16acf-182">Visualizando seu trabalho</span><span class="sxs-lookup"><span data-stu-id="16acf-182">Previewing your work</span></span>

<span data-ttu-id="16acf-183">Ao editar no GitHub por meio de um navegador da Web, você pode clicar na guia **Visualizar** próximo à parte superior da página para visualizar seu trabalho antes de confirmar.</span><span class="sxs-lookup"><span data-stu-id="16acf-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="16acf-184">A visualização de suas alterações no review.docs.microsoft.com só está disponível para funcionários da Microsoft</span><span class="sxs-lookup"><span data-stu-id="16acf-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="16acf-185">Funcionários da Microsoft: depois que suas contribuições tiverem sido mescladas na ramificação ' mestre ', você poderá ver qual será a aparência da documentação antes que ela https://review.docs.microsoft.com/windows/mixed-reality?branch=master seja pública (encontre seu artigo usando o Sumário na coluna à esquerda).</span><span class="sxs-lookup"><span data-stu-id="16acf-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="16acf-186">Editando no navegador versus editando com um cliente de desktop</span><span class="sxs-lookup"><span data-stu-id="16acf-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="16acf-187">A edição no navegador é a maneira mais fácil de fazer alterações rápidas, no entanto, há algumas desvantagens:</span><span class="sxs-lookup"><span data-stu-id="16acf-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="16acf-188">Você não tem verificação ortográfica.</span><span class="sxs-lookup"><span data-stu-id="16acf-188">You don't get spell-check.</span></span>
- <span data-ttu-id="16acf-189">Você não obtém nenhuma vinculação inteligente com outros artigos (você precisa digitar manualmente o nome do arquivo).</span><span class="sxs-lookup"><span data-stu-id="16acf-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="16acf-190">Pode ser um trabalho difícil de carregar e fazer referência a imagens.</span><span class="sxs-lookup"><span data-stu-id="16acf-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="16acf-191">Se você preferir não lidar com esses problemas, talvez prefira usar um cliente de desktop como [Visual Studio Code](https://code.visualstudio.com/) com algumas [extensões úteis](#useful-extensions) para contribuir para a documentação.</span><span class="sxs-lookup"><span data-stu-id="16acf-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="16acf-192">Usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="16acf-192">Using Visual Studio Code</span></span>

<span data-ttu-id="16acf-193">Pelos motivos listados [acima](#editing-in-the-browser-vs-editing-with-a-desktop-client), você pode preferir usar um cliente de desktop para editar a documentação em vez de um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="16acf-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="16acf-194">É recomendável usar [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="16acf-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="16acf-195">Configuração</span><span class="sxs-lookup"><span data-stu-id="16acf-195">Setup</span></span>

<span data-ttu-id="16acf-196">Siga estas etapas para configurar Visual Studio Code para trabalhar com este repositório:</span><span class="sxs-lookup"><span data-stu-id="16acf-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="16acf-197">Em um navegador da Web:</span><span class="sxs-lookup"><span data-stu-id="16acf-197">In a web browser:</span></span>
    1. <span data-ttu-id="16acf-198">Instale [o Git para seu computador](https://git-scm.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="16acf-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="16acf-199">Instale o [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="16acf-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="16acf-200">[Bifurcação MicrosoftDocs/Mixed-Realm,](#creating-a-new-article) se ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="16acf-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="16acf-201">Em sua bifurcação, clique em **clonar ou baixar** e copie a URL.</span><span class="sxs-lookup"><span data-stu-id="16acf-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="16acf-202">Crie um clone local de sua bifurcação no Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="16acf-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="16acf-203">No menu **Exibir** , selecione **paleta de comandos**.</span><span class="sxs-lookup"><span data-stu-id="16acf-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="16acf-204">Digite "Git: clone".</span><span class="sxs-lookup"><span data-stu-id="16acf-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="16acf-205">Cole a URL que você acabou de copiar.</span><span class="sxs-lookup"><span data-stu-id="16acf-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="16acf-206">Escolha onde salvar o clone em seu PC.</span><span class="sxs-lookup"><span data-stu-id="16acf-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="16acf-207">Clique em **abrir repositório** no pop-up.</span><span class="sxs-lookup"><span data-stu-id="16acf-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="16acf-208">Editando a documentação</span><span class="sxs-lookup"><span data-stu-id="16acf-208">Editing documentation</span></span>

<span data-ttu-id="16acf-209">Use o seguinte fluxo de trabalho para fazer alterações na documentação com Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="16acf-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="16acf-210">Todas as diretrizes para [edição](#editing-an-existing-article) e [criação](#creating-a-new-article) de artigos, e os [fundamentos de redução de edição](#markdown-basics), a partir de acima aplicam-se também ao usar o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="16acf-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="16acf-211">Verifique se sua bifurcação clonada está atualizada com o repositório oficial.</span><span class="sxs-lookup"><span data-stu-id="16acf-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="16acf-212">Em um navegador da Web, crie uma solicitação de pull para sincronizar alterações recentes de outros colaboradores em MicrosoftDocs/Mixed-Realm ' Master ' para sua bifurcação (verifique se a seta está apontando da maneira correta).</span><span class="sxs-lookup"><span data-stu-id="16acf-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Sincronizar alterações de MicrosoftDocs/Mixed-realm para sua bifurcação](images/sync_repos.PNG)
   2. <span data-ttu-id="16acf-214">Em Visual Studio Code, clique no botão Sincronizar para sincronizar sua bifurcação atualizada atualizada para o clone local.</span><span class="sxs-lookup"><span data-stu-id="16acf-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![Clique no botão Sincronizar](images/sync_clone.png)
2. <span data-ttu-id="16acf-216">Crie ou edite artigos em seu repositório clonado usando Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="16acf-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="16acf-217">Edite um ou mais artigos (adicione imagens à pasta "imagens", se necessário).</span><span class="sxs-lookup"><span data-stu-id="16acf-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="16acf-218">**Salve** as alterações no **Explorer**.</span><span class="sxs-lookup"><span data-stu-id="16acf-218">**Save** changes in **Explorer**.</span></span>
      
      ![Escolha "salvar tudo" no Gerenciador](images/explorer_save.png)
   3. <span data-ttu-id="16acf-220">**Confirmar todas** as alterações no **controle do código-fonte** (gravar mensagem de confirmação quando solicitado).</span><span class="sxs-lookup"><span data-stu-id="16acf-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![Escolha "confirmar tudo" no controle do código-fonte](images/source_control_commit.png)
   4. <span data-ttu-id="16acf-222">Clique no botão **sincronizar** para sincronizar suas alterações de volta à origem (sua bifurcação no GitHub).</span><span class="sxs-lookup"><span data-stu-id="16acf-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![Clique no botão Sincronizar](images/sync_back.png)
3. <span data-ttu-id="16acf-224">Em um navegador da Web, crie uma solicitação de pull para sincronizar novas alterações na bifurcação de volta para MicrosoftDocs/Mixed-Realm ' Master ' (verifique se a seta está apontando da maneira correta).</span><span class="sxs-lookup"><span data-stu-id="16acf-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Criar solicitação de pull de sua bifurcação em MicrosoftDocs/Mixed-Realm](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="16acf-226">Extensões úteis</span><span class="sxs-lookup"><span data-stu-id="16acf-226">Useful extensions</span></span>

<span data-ttu-id="16acf-227">As seguintes extensões de Visual Studio Code são muito úteis ao editar a documentação:</span><span class="sxs-lookup"><span data-stu-id="16acf-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="16acf-228">[Extensão de redução de documentos para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -use **ALT + M** para abrir um menu de opções de criação de docs como:</span><span class="sxs-lookup"><span data-stu-id="16acf-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="16acf-229">Pesquisar e fazer referência a imagens que você carregou.</span><span class="sxs-lookup"><span data-stu-id="16acf-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="16acf-230">Adicione formatação como listas, tabelas e chamadas de documentos específicas de docs como `>[!NOTE]`.</span><span class="sxs-lookup"><span data-stu-id="16acf-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="16acf-231">Pesquisar e referenciar links internos e indicadores (links para seções específicas em uma página).</span><span class="sxs-lookup"><span data-stu-id="16acf-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="16acf-232">Erros de formatação são realçados (passe o mouse sobre o erro para saber mais).</span><span class="sxs-lookup"><span data-stu-id="16acf-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="16acf-233">[Verificador ortográfico de código](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -palavras incorretas serão sublinhadas; Clique com o botão direito do mouse em uma palavra incorreta para alterá-la ou salvá-la no dicionário.</span><span class="sxs-lookup"><span data-stu-id="16acf-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
