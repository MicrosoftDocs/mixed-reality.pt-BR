---
title: Estudo de caso - HoloSketch de construção, um layout espacial e a experiência do usuário fazer um rascunho de aplicativo para o HoloLens
description: HoloSketch é um layout de espacial no dispositivo e a experiência do usuário fazer um rascunho de ferramenta para HoloLens ajudar a criar experiências holográfica.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, fazer um rascunho, aplicativo
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589599"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Estudo de caso - HoloSketch de construção, um layout espacial e a experiência do usuário fazer um rascunho de aplicativo para o HoloLens

HoloSketch é um layout de espacial no dispositivo e a experiência do usuário fazer um rascunho de ferramenta para HoloLens ajudar a criar experiências holográfica. HoloSketch funciona com um comandos de teclado e mouse, bem como gestos e voz de Bluetooth emparelhados. A finalidade de HoloSketch é fornecer uma ferramenta de layout de experiência do usuário simple para iteração e visualização rápida.

![HoloSketch: Um layout espacial e a experiência do usuário fazer um rascunho de aplicativo para o HoloLens.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: layout espacial e a experiência do usuário fazer um rascunho de aplicativo para o HoloLens*

![Uma ferramenta de layout de experiência do usuário simple para visualização rápida e de iteração.](images/holosketch-image-02.png)<br>
*Uma ferramenta simples de layout UX para visualização rápida e de iteração*

## <a name="features"></a>Recursos

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Primitivos para estudos rápido e criação de protótipos de escala

![Usando formas primitivas](images/holosketch-primitives-giphy.gif)

Use formas primitivas para estudos massing rápidos e criação de protótipos de escala.

### <a name="import-objects-through-onedrive"></a>Importar objetos por meio do OneDrive

![importação de objetos](images/holosketch-importobjects-giphy.gif)

Importar imagens JPG/PNG ou objetos em 3D FBX (requer o empacotamento no Unity) para o espaço de realidade misturada por meio do OneDrive.

### <a name="manipulate-objects"></a>Manipular objetos

![manipulação de objetos](images/manipulate-objects-640px.jpg)

Manipule objetos (mover/girar/escala) com uma interface familiar objeto 3D.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Comandos de Bluetooth, mouse/teclado, gestos e voz

![dá suporte a Bluetooth](images/supports-bluetooth-640px.jpg)

HoloSketch dá suporte a mouse/teclado Bluetooth, gestos e comandos de voz.

## <a name="background"></a>Histórico

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Importância de tendo seu design no dispositivo

Quando você projeta algo para HoloLens, é importante experimentar o design no dispositivo. Um dos maiores desafios no design de aplicativos de realidade misturada é que é difícil conseguir o senso de escala, a posição e a profundidade, principalmente por meio de esboços 2D tradicionais.

### <a name="cost-of-2d-based-communication"></a>Custo de 2D com base em comunicação

Para se comunicar efetivamente cenários para outras pessoas e fluxos de experiência do usuário, um designer pode acabar gastando muito tempo na criação de ativos usando ferramentas tradicionais de 2D, como Illustrator, Photoshop e do PowerPoint. Esses designs 2D geralmente exigem mais esforço para convertê-los em 3D. Algumas ideias são perdidas essa conversão de 2D para 3D.

### <a name="complex-deployment-process"></a>Processo de implantação complexas

Como realidade mista é uma nova tela para nós, ela envolve muita tentativa e erro e de iteração de design por natureza. Para o designer que não estão familiarizados com ferramentas como o Unity e o Visual Studio, não é fácil juntar algo no HoloLens. Normalmente, você precisa passar pelo processo abaixo para ver sua arte 2D/3D no dispositivo. Essa foi uma barreira grande para designers de iteração em cenários e ideias rapidamente.

![Processo de implantação complexas](images/holosketch-image-03-1000px.png)<br>
*Processo de implantação*

### <a name="simplified-process-with-holosketch"></a>Processo simplificado com HoloSketch

Com HoloSketch, queremos simplificar esse processo sem envolver o emparelhamento de portal de dispositivos e ferramentas de desenvolvimento. Usar o OneDrive, os usuários podem facilmente colocar ativos 2D/3D em HoloLens.

![Processo simplificado com HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Processo simplificado com HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Incentivar o pensamento do design tridimensional e soluções

Achamos que essa ferramenta daria designers uma oportunidade de explorar as soluções em um espaço tridimensional verdadeiramente e não estar preso em 2D. Eles não precisam pensar em criar um plano de fundo 3D para sua interface do usuário, pois o plano de fundo é o mundo real, no caso do Hololens. HoloSketch abre uma maneira para designers explorarem facilmente projeto 3D no Hololens.

## <a name="get-started"></a>Introdução

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Como importar imagens 2D (JPG/PNG) para HoloSketch

* Carregar imagens JPG/PNG sua pasta do OneDrive ' Documentos/HoloSketch'.
* No menu OneDrive no HoloSketch, você poderá selecionar e colocar a imagem no ambiente.

![A importação de imagens 2D](images/import-2d-images-1000px.jpg)<br>
*Importação de imagens e objetos 3D por meio do OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Como importar objetos 3D para HoloSketch

Antes de carregar sua pasta do OneDrive, siga as etapas abaixo para empacotar seus objetos 3D em um pacote de ativos do Unity. Usando esse processo, você pode importar os arquivos OBJ/FBX de software 3D, como Maya, Cinema 4d e o Microsoft Paint 3D.

>[!IMPORTANT]
>Atualmente, a criação do pacote ativo é compatível com o Unity versão 5.4.5f1.

1. Baixe e abra o projeto do Unity ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity). Este projeto do Unity inclui o script para a geração de ativo do pacote.
2. Crie um novo GameObject.
3. Nomeie o GameObject com base no conteúdo.
4. No painel de Inspetor, clique em 'Adicionar componente' e adicione 'Box Collider'. 

   ![No painel de inspeção, clique em 'Adicionar componente' e adicione 'Box Collider'](images/holosketch-10a-assetbundles-1000px.png)
   
   ![No painel de inspeção, clique em 'Adicionar componente' e adicione 'Box Collider' #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importe o arquivo FBX 3D, arrastando-o para o painel do projeto.
6. Arraste o objeto para o painel de hierarquia **em seu novo GameObject**.

   ![Arraste o objeto para o painel de hierarquia em seu novo GameObject](images/holosketch-12-assetbundles-1000px.png)

7. Ajuste a dimensão do colisor se ele não coincide com o objeto. Girar o objeto para enfrentar **eixo z**.

   ![Ajuste a dimensão do colisor se ele não coincide com o objeto.](images/holosketch-13-assetbundles-1000px.png)

8. Arraste o objeto do painel de hierarquia para o painel de projeto para **torná-lo pré-fabricado**.
9. Na parte inferior do painel de tarefas do Inspetor de propriedades, clique na lista suspensa, criar e atribuir um novo nome exclusivo. Exemplo abaixo mostra a adição e atribuição 'brownchair' para o nome de AssetBundle. 

   ![Na parte inferior do painel de tarefas do Inspetor de propriedades, clique na lista suspensa e atribua um novo nome exclusivo.](images/holosketch-14-assetbundles-1000px.png)

10. Prepare uma imagem em miniatura para o objeto de modelo. 
   ![Arraste uma imagem para o painel de projeto e atribua o nome usado para o objeto.](images/holosketch-15-assetbundles-1000px.png)

11. Crie uma pasta chamada 'Assetbundles' na pasta de 'Ativo' do projeto do Unity.

12. No menu de ativos, selecione 'Criar AssetBundles' para gerar o arquivo. 
   ![No menu de ativos, selecione 'Criar AssetBundles' para gerar o arquivo.](images/holosketch-15a-assetbundles.png)


13. **Carregue o arquivo gerado para a pasta /Files/Documents/HoloSketch no OneDrive.** Carregue o arquivo asset_unique_name apenas. Você não precisa carregar arquivo de AssetBundles ou arquivos de manifesto. <br>
![Adicionar arquivos ao arquivos/documentos/HoloSketch/pasta](images/holosketch-onedriveupload-1000px.png)
![você verá o objeto 3D adicionado no menu do OneDrive do HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Como manipular os objetos

HoloSketch suporta a interface tradicional que é amplamente usada em software 3D. Você pode usar mover, girar, dimensionar os objetos com gestos e um mouse. Você pode alternar rapidamente entre diferentes modos com voz ou teclado.

### <a name="object-manipulation-modes"></a>Modos de manipulação de objeto

![Como manipular os objetos](images/holosketch-image-06-1000px.png)<br>
*Como manipular os objetos*

### <a name="contextual-and-tool-belt-menus"></a>Menus contextuais e conjunto de ferramentas

**Usando o Menu Contextual**

Double e polegar para abrir o Menu Contextual. 

Itens de menu:
* **Superfície de layout:** Esse é um sistema de grade 3D em que você pode definir o layout vários objetos e gerenciá-los como um grupo. Polegar dupla na superfície de Layout para adicionar objetos a ele.
* **Primitivos:** Usar cubos, esferas, cilindros e cones para massing estudos.
* **OneDrive:** Abra o menu do OneDrive para importar objetos.
* **Ajuda:** Exibe a tela de Ajuda.

![Menu contextual](images/holosketch-image-07.png)<br>
*Menu contextual*

**Usando o Menu de faixa de ferramenta**

Mover, girar, dimensionar, salvar e cena de carga estão disponíveis no Menu de cinto de ferramenta. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Usando o teclado, gestos e comandos de voz

![Teclado, gestos e comandos de voz](images/holosketch-image-08-1000px.png)<br>
*Teclado, gestos e comandos de voz*

## <a name="download-the-app"></a>Baixe o aplicativo

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Baixe e instale o aplicativo HoloSketch gratuitamente da Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Problemas conhecidos
* Atualmente, a criação do pacote ativo é compatível com **5.4.5f1 de versão do Unity.**
* Dependendo da quantidade de dados em seu OneDrive, o aplicativo pode aparecer como se ele tiver sido interrompido durante o carregamento de conteúdo do OneDrive
* Atualmente, salvar e carregar o recurso somente dá suporte a primitivos objetos
* Menus de texto, som, vídeo e foto estão desabilitados no menu contextual
* O botão Reproduzir no menu's Tool Belt limpa os utensílios de manipulação

## <a name="sharing-your-sketches"></a>Os esboços de compartilhamento

Você pode usar o recurso de gravação de vídeo no HoloLens dizendo "Ei Cortana, Iniciar/Parar gravação '. Pressione o chave juntos para tirar uma foto do seu esboço para cima/para baixo volume.

## <a name="about-the-authors"></a>Sobre os autores

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Designer de UX @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>Desenvolvedor @Microsoft</td>
</tr>
</table> 
