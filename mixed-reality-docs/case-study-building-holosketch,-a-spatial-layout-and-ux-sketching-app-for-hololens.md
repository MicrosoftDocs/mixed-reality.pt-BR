---
title: Estudo de caso-criando HoloSketch, um layout espacial e um aplicativo de esboço de UX para o HoloLens
description: HoloSketch é um layout espacial do dispositivo e uma ferramenta de esboço de UX para o HoloLens para ajudar a criar experiências de Holographic.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, realidade mista do Windows, esboço, aplicativo
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524416"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Estudo de caso-criando HoloSketch, um layout espacial e um aplicativo de esboço de UX para o HoloLens

HoloSketch é um layout espacial do dispositivo e uma ferramenta de esboço de UX para o HoloLens para ajudar a criar experiências de Holographic. O HoloSketch funciona com um teclado e mouse Bluetooth emparelhados, bem como comandos de voz e de gesto. A finalidade do HoloSketch é fornecer uma ferramenta de layout de UX simples para visualização e iteração rápidas.

![HoloSketch: Um layout espacial e um aplicativo de esboço de UX para o HoloLens.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: layout espacial e aplicativo de esboço de UX para o HoloLens*

![Uma ferramenta de layout de UX simples para visualização e iteração rápidas.](images/holosketch-image-02.png)<br>
*Uma ferramenta de layout de UX simples para visualização e iteração rápidas*

## <a name="features"></a>Recursos

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Primitivos para estudos rápidos e criação de protótipos de escala

![Usando formas primitivas](images/holosketch-primitives-giphy.gif)

Use formas primitivas para estudos rápidos de massa e criação de protótipos de escala.

### <a name="import-objects-through-onedrive"></a>Importar objetos por meio do OneDrive

![importando objetos](images/holosketch-importobjects-giphy.gif)

Importe imagens PNG/JPG ou objetos FBX 3D (requer empacotamento no Unity) no espaço da realidade misturada por meio do OneDrive.

### <a name="manipulate-objects"></a>Manipular objetos

![manipulando objetos](images/manipulate-objects-640px.jpg)

Manipule objetos (move/gira/dimensionamento) com uma interface de objeto 3D familiar.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, mouse/teclado, gestos e comandos de voz

![dá suporte a Bluetooth](images/supports-bluetooth-640px.jpg)

O HoloSketch dá suporte a mouses Bluetooth/teclado, gestos e comandos de voz.

## <a name="background"></a>Informações preliminares

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Importância de experimentar seu design no dispositivo

Quando você cria algo para o HoloLens, é importante experimentar o design no dispositivo. Um dos maiores desafios no design de aplicativos de realidade misturada é que é difícil obter o sentido de escala, posição e profundidade, especialmente por meio de esboços 2D tradicionais.

### <a name="cost-of-2d-based-communication"></a>Custo da comunicação baseada em 2D

Para comunicar efetivamente fluxos e cenários de UX a outros, um designer pode acabar gastando muito tempo criando ativos usando ferramentas 2D tradicionais, como o Illustrator, o Photoshop e o PowerPoint. Esses designs 2D geralmente exigem um esforço adicional para convertê-los em 3D. Algumas ideias são perdidas nessa tradução de 2D para 3D.

### <a name="complex-deployment-process"></a>Processo de implantação complexo

Como a realidade misturada é uma nova tela para nós, ela envolve muita iteração de design e avaliação e erro por sua natureza. Para o designer que não estão familiarizados com ferramentas como Unity e Visual Studio, não é fácil colocar algo em conjunto no HoloLens. Normalmente, você precisa passar pelo processo abaixo para ver sua arte 2D/3D no dispositivo. Essa era uma grande barreira para os designers Iterando rapidamente em ideias e cenários.

![Processo de implantação complexo](images/holosketch-image-03-1000px.png)<br>
*Processo de implantação*

### <a name="simplified-process-with-holosketch"></a>Processo simplificado com o HoloSketch

Com o HoloSketch, queríamos simplificar esse processo sem envolver as ferramentas de desenvolvimento e o emparelhamento do portal do dispositivo. Usando o OneDrive, os usuários podem facilmente colocar ativos 2D/3D no HoloLens.

![Processo simplificado com o HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Processo simplificado com o HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Incentivando a reflexão e as soluções de design tridimensionais

Achamos que essa ferramenta daria aos designers uma oportunidade de explorar soluções em um espaço verdadeiramente tridimensional e que não estaria presa em 2D. Eles não precisam pensar em criar um plano de fundo 3D para sua interface do usuário, pois o plano de fundo é o mundo real no caso do Hololens. O HoloSketch abre uma maneira de os designers explorarem facilmente o design 3D no Hololens.

## <a name="get-started"></a>Introdução

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Como importar imagens 2D (JPG/PNG) para o HoloSketch

* Carregue imagens JPG/PNG na pasta do OneDrive ' Documents/HoloSketch '.
* No menu do OneDrive no HoloSketch, você poderá selecionar e posicionar a imagem no ambiente.

![Importando imagens 2D](images/import-2d-images-1000px.jpg)<br>
*Importando imagens e objetos 3D por meio do OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Como importar objetos 3D para o HoloSketch

Antes de carregar em sua pasta do OneDrive, siga as etapas abaixo para empacotar seus objetos 3D em um pacote de ativos do Unity. Usando esse processo, você pode importar seus Arquivos FBX/OBJ de software 3D, como Maya, cinema 4D e Microsoft Paint 3D.

>[!IMPORTANT]
>Atualmente, a criação do pacote de ativos tem suporte com o Unity versão 5.4.5 F1.

1. Baixe e abra o projeto do Unity [' AssetBunlder_Unity '](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity). Esse projeto de Unity inclui o script para a geração de ativos do pacote.
2. Crie um novo gameobject.
3. Nomeie o gameobject com base no conteúdo.
4. No painel Inspetor, clique em "Adicionar componente" e adicione "cocolisorr". 

   ![No painel Inspetor, clique em "Adicionar componente" e adicionar "Colisor de caixa"](images/holosketch-10a-assetbundles-1000px.png)
   
   ![No painel Inspetor, clique em "Adicionar componente" e adicionar "Colisor de caixa" #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importe o arquivo 3D FBX arrastando-o para o painel projeto.
6. Arraste o objeto para o painel hierarquia **em seu novo gameobject**.

   ![Arraste o objeto para o painel hierarquia em seu novo gameobject](images/holosketch-12-assetbundles-1000px.png)

7. Ajuste a dimensão do colisor se ele não corresponder ao objeto. Gire o objeto para a face do **eixo Z**.

   ![Ajuste a dimensão do colisor se ele não corresponder ao objeto.](images/holosketch-13-assetbundles-1000px.png)

8. Arraste o objeto do painel hierarquia para o painel projeto para **torná-lo pré-fabricado**.
9. Na parte inferior do painel Inspetor, clique no menu suspenso, crie e atribua um novo nome exclusivo. O exemplo abaixo mostra como adicionar e atribuir ' brownchair ' para o nome do AssetBundle. 

   ![Na parte inferior do painel Inspetor, clique na lista suspensa e atribua um novo nome exclusivo.](images/holosketch-14-assetbundles-1000px.png)

10. Prepare uma imagem em miniatura para o objeto de modelo. 
   ![Arraste uma imagem para o painel projeto e atribua o nome usado para o objeto.](images/holosketch-15-assetbundles-1000px.png)

11. Crie uma pasta chamada ' Assetbundles ' na pasta ' Asset ' do projeto de Unity.

12. No menu ativos, selecione ' Compilar AssetBundles ' para gerar o arquivo. 
   ![No menu ativos, selecione ' Compilar AssetBundles ' para gerar o arquivo.](images/holosketch-15a-assetbundles.png)


13. **Carregue o arquivo gerado para a pasta/Files/Documents/HoloSketch no OneDrive.** Carregue somente o arquivo asset_unique_name. Você não precisa carregar arquivos de manifesto ou arquivo AssetBundles. <br>
![Adicionar arquivos a arquivos/documentos/HoloSketch/pasta](images/holosketch-onedriveupload-1000px.png)
![, você verá o objeto 3D adicionado no menu do onedrive HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Como manipular os objetos

O HoloSketch dá suporte à interface tradicional que é amplamente usada em software 3D. Você pode usar mover, girar, dimensionar os objetos com gestos e um mouse. Você pode alternar rapidamente entre modos diferentes com voz ou teclado.

### <a name="object-manipulation-modes"></a>Modos de manipulação de objeto

![Como manipular os objetos](images/holosketch-image-06-1000px.png)<br>
*Como manipular os objetos*

### <a name="contextual-and-tool-belt-menus"></a>Menus contextuais e da correia de ferramenta

**Usando o menu contextual**

Toque de ar duplo para abrir o menu contextual. 

Itens de menu:
* **Superfície de layout:** Esse é um sistema de grade 3D no qual você pode fazer o layout de vários objetos e gerenciá-los como um grupo. Air de toque duplo na superfície de layout para adicionar objetos a ele.
* **Primitivos** Use cubos, por meio de cilindros e cones para estudos em massa.
* **OneDrive:** Abra o menu do OneDrive para importar objetos.
* **Ajuda:** Exibe a tela de ajuda.

![Menu contextual](images/holosketch-image-07.png)<br>
*Menu contextual*

**Usando o menu da correia de ferramentas**

Mover, girar, dimensionar, salvar e carregar a cena está disponível no menu da correia de ferramentas. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Usando teclado, gestos e comandos de voz

![Teclado, gestos e comandos de voz](images/holosketch-image-08-1000px.png)<br>
*Teclado, gestos e comandos de voz*

## <a name="download-the-app"></a>Baixar o aplicativo

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Baixe e instale o aplicativo HoloSketch gratuitamente no Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Problemas conhecidos
* Atualmente, há suporte para a criação do pacote de ativos com o **Unity versão 5.4.5 F1.**
* Dependendo da quantidade de dados em seu OneDrive, o aplicativo pode aparecer como se tiver parado durante o carregamento do conteúdo do OneDrive
* Atualmente, o recurso salvar e carregar só dá suporte a objetos primitivos
* Os menus de texto, som, vídeo e foto estão desabilitados no menu contextual
* O botão reproduzir no menu da correia de ferramenta limpa o utensílios de manipulação

## <a name="sharing-your-sketches"></a>Compartilhando seus esboços

Você pode usar o recurso de gravação de vídeo no HoloLens dizendo ' Ei Cortana, iniciar/parar a gravação '. Pressione a tecla volume para cima/para baixo para tirar uma foto do seu esboço.

## <a name="about-the-authors"></a>Sobre os autores

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Parque Yoon Dong</b><br>Designer de UX@Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>Desenvolvedor@Microsoft</td>
</tr>
</table> 
