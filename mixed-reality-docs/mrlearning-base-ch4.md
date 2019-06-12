---
title: Módulo Base de Aprendizado de MR – Interação de Objeto 3D
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 45e772de0825fe2161f880a165d6c75c755b849e
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730904"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>Módulo Base de Aprendizado de MR – Interação de Objeto 3D

Nesta lição, examinaremos o conteúdo 3D básico e a experiência do usuário. Aprenderemos a organizar objetos 3D como parte de uma coleção, conheceremos mais sobre caixas delimitadoras para manipulação básica, sobre a interação próxima e distante e sobre os gestos de toque e segurar com o acompanhamento de mãos. 

## <a name="objectives"></a>Objetivos

* Aprender a organizar o conteúdo 3D usando a coleção de objetos de grade do MRTK
* Implementar caixas delimitadoras
* Configurar objetos 3D para manipulação básica (mover, girar e dimensionar)
* Explorar a interação próxima e distante
* Conhecer gestos adicionais de acompanhamento de mãos, como toque e segurar

## <a name="instructions"></a>Instruções

### <a name="organizing-3d-objects-in-a-collection"></a>Como organizar objetos 3D em uma coleção

1. Clique com o botão direito do mouse na hierarquia e selecione “Criar vazio”. Isso criará um objeto de jogo vazio. Renomeie-o para “3DObjectCollection”. Esse é o local em que colocaremos todos os nossos objetos 3D. Verifique se o posicionamento da coleção está definido como x = 0, y = 0 e z = 0.

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. Importe os ativos do BaseModule usando as mesmas instruções para importar pacotes personalizados descritas na [Lição 1](mrlearning-base-ch1.md). Os ativos do BaseModule incluem módulos 3D e outros scripts úteis que serão usados neste tutorial. O pacote do Unity BaseModule pode ser encontrado aqui: <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. O pré-fabricado da xícara de café pode ser reconhecido por um cubo azul ao lado dele. Não selecione a xícara de café com o cubo azul e o pequeno papel em branco (que indica o modelo 3D original e não o pré-fabricado.) 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. Arraste o pré-fabricado da xícara de café de sua escolha para o objeto de jogo "3DObjectCollection" da etapa 1. A xícara de café agora é um filho da coleção.

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. Em seguida, adicionaremos mais objetos 3D à nossa cena. Veja abaixo uma lista de objetos que adicionaremos neste exemplo. Conforme você adicionar os objetos, você poderá achar que eles aparecem na cena em vários tamanhos. Ajuste a escala de cada modelo 3D na configuração de transformação no painel do inspetor. Os ajustes indicados para este exemplo são listados com os objetos abaixo. Pesquise essas palavras na caixa de pesquisa do painel do projeto e arraste o objeto 3D pré-fabricado para o objeto "3DObjectCollection", de forma semelhante à etapa anterior. Você encontrará essa coleção de pré-fabricados em Ativos>BaseModuleAssets>Pré-fabricados do Módulo Base
- Pesquise “TheModule_BaseModuleIncomplete”. Arraste-o para a cena. Defina a escala como x = 0,03, y = 0,03, z = 0,03. 
- Pesquise “Octa_BaseModuleIncomplete”. Arraste-o para a cena. Defina a escala como x = 0,13. y = 0,13, z = 0,13.
- Pesquise “EarthCore_BaseModuleIncomplete”. Arraste-o para a cena. Defina a escala como x = 50,0 y = 50,0, z = 50,0.
- Pesquise “Cheese_BaseModuleIncomplete”. Arraste-o para a cena. Defina a escala como x = 0,05, y = 0,05, z = 0,05.
- Pesquise “Model_Platonic_BaseModuleIncomplete”. Arraste-o para a cena. Defina a escala como x = 0,13, y = 0,13, z = 0,13.
- Pesquise "CoffeeCup_BaseModuleIncomplete". Arraste-o para a cena.

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. Adicione três cubos à cena. Clique com o botão direito do mouse no objeto “3DObjectCollection”, selecione “Objeto 3D” e, em seguida, “Cubo”. Defina a escala como x = 0,14, y = 0,14 e z = 0,14. Repita esta etapa duas vezes mais para criar um total de três cubos. Como alternativa, você pode duplicar o cubo duas vezes para um total de três cubos. Você também pode optar por usar os pré-fabricados do cubo preparados de Ativos>BaseModuleAssets>Pré-fabricados do Módulo Base e selecionar GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete e OrangeCube_BaseModuleIncomplete.

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. Organize a coleção de objetos para formar uma grade usando o procedimento descrito na [Lição 2](mrlearning-base-ch2.md) usando a coleção de objetos de grade do MRTK. Veja a imagem abaixo para ver um exemplo de como configurar os objetos em uma grade 3x3.

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>Observação: Você poderá observar que alguns dos objetos estão fora do centro, como os objetos na imagem acima. Isso ocorre porque os pré-fabricados ou os objetos podem ter objetos filho que não estão alinhados. Fique à vontade para fazer os ajustes necessários nas posições de objetos ou de objetos filho para obter uma grade bem alinhada.


### <a name="manipulating-3d-objects"></a>Como manipular objetos 3D
1. Adicione a capacidade de manipular um cubo. Para adicionar a capacidade de manipular objetos 3D, você deverá fazer o seguinte:
-   Selecione o objeto 3D que deseja manipular na hierarquia (neste exemplo, um dos cubos).
-   Clique em “Adicionar componente”. 
-   Pesquise “manipulação”.
-   Selecione “manipulador de manipulação”.
-   Repita isso para todos os objetos 3D no objeto “3DObjectCollection”, mas não no próprio “3DObjectCollection”.
-   Verifique se todos os objetos 3D têm um colisor ou um colisor de caixa (Adicionar Componente > colisor de caixa).

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>O manipulador de manipulação é um componente que permitirá que você ajuste as configurações de como os objetos se comportam quando são manipulados. Isso inclui rotação, dimensionamento, movimentação e movimento de restrições em determinados eixos. 

2. Restrinja um cubo, de modo que ele só possa ser dimensionado. Selecione um cubo no objeto “3DObjectCollection”. No painel do inspetor, ao lado de “Tipo de manipulação de duas mãos”, clique no menu suspenso e selecione “Escalar”. Isso faz com que o usuário só possa alterar o tamanho do cubo.

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. Altere a cor de cada cubo, de modo que possamos diferenciar entre eles. 
-   Acesse o painel do projeto e role a página para baixo até ver “MixedRealityToolkit.SDK” e, em seguida, selecione-o.
-   Selecione a pasta “Ativos Padrão”.
-   Clique na pasta “materiais”.
-   Arraste outro material para cada um dos cubos. 

>Observação: Escolha qualquer cor para os cubos. Para nosso exemplo, usaremos “glowingcyan,” “glowingorange” e "green". Fique à vontade para experimentar com cores diferentes. Para adicionar a cor ao cubo, clique no cubo do qual deseja alterar a cor e arraste o material para o campo do material do renderizador de malha no painel do inspetor do cubo. 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. Selecione outro cubo no objeto “3DObjectCollection” e faça com que seu movimento fique restrito à distância fixa da cabeça. Para fazer isso, à direita da “Restrição em movimento”, clique no menu suspenso e selecione “Distância fixa da cabeça”. Isso faz com que o usuário só possa mover o cubo em seu campo de visão. 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

Meta das próximas etapas: Habilitaremos a captura e a interação com nossos objetos 3D. Aplicaremos configurações diferentes de manipulação 

5. Selecione o objeto de queijo e no painel do inspetor e clique em “Adicionar componente”. 

6. Pesquise na caixa de pesquisa “Segurável de Interação Próxima” e selecione o script. Este componente permite que os usuários alcancem e segurem os objetos com as mãos rastreadas. Os objetos também poderão ser manipulados a uma distância, a menos que a caixa de seleção "Permitir Manipulação Distante" esteja desmarcada (indicado por um círculo verde na imagem abaixo).

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. Adicione o “Segurável de Interação Próxima” ao objeto Octa, ao objeto Platonic, ao núcleo da Terra, ao módulo lunar e à xícara de café repetindo as etapas 5 e 6 nesses objetos.

8. Remova a capacidade de manipulação distante do objeto Octa. Para fazer isso, selecione o Octa na hierarquia e desmarque a caixa de seleção “Permitir manipulação distante” (marcada por um círculo verde). Isso faz com que os usuários só possam interagir com o Octa diretamente usando mãos rastreadas.

>Observação: Para obter a documentação completa do componente de manipulador de manipulação e as respectivas configurações associadas, confira a [Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Verifique se o componente "Segurável de Interação Próxima" foi adicionado ao núcleo da Terra, ao módulo lunar e à xícara de café (confira a etapa 7).

10. Para o módulo lunar, altere as configurações do Manipulador de Manipulação, de modo que ele gire sobre o centro do objeto para as interações próxima e distante, conforme mostrado na imagem abaixo.

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11: Para o núcleo da Terra, altere o comportamento de liberação para “nada”. Isso faz com que, depois que o núcleo da Terra é liberado do controle dos usuários, ele não continue se movendo. 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> Observação: Essa configuração é útil para cenários como a criação de uma bola que você pode lançar. Manter a velocidade e a velocidade angular faz com que, depois que a bola é liberada, ela continue se movendo com a velocidade na qual foi liberada, semelhante ao modo como uma bola física se comportará.

### <a name="adding-bounding-boxes"></a>Como adicionar caixas delimitadoras
As caixas delimitadoras facilitam e tornam intuitiva a manipulação de objetos com uma mão para a manipulação direta (interação próxima) e a manipulação baseada em raio (interação distante). As caixas delimitadoras oferecem "alças" que podem ser seguradas para o dimensionamento e a rotação de objetos ao longo de eixos específicos.
>Observação: Antes de adicionar uma caixa delimitadora a um objeto, primeiro você precisa ter um colisor no objeto (por exemplo, um colisor de caixa). Como fizemos anteriormente nesta lição. Os colisores podem ser adicionados pela seleção do objeto e, no painel do inspetor do objeto, pela seleção de Adicionar Componente>Colisor de Caixa.
>

1. Adicione um colisor de caixa ao objeto de núcleo da Terra, se ainda não existir (o colisor de caixa e a instalação não serão necessários se você estiver usando o pré-fabricado fornecido na pasta Ativos do Módulo Base, de acordo com as instruções fornecidas.) No caso do núcleo da Terra, precisaremos adicionar o colisor de caixa ao objeto "node_id30" sob o núcleo da Terra, conforme mostrado na imagem abaixo. Selecione node_id30 e, na guia do inspetor do objeto, clique em “Adicionar componente” e pesquise “colisor de caixa”. 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> Observação: Verifique se você consegue visualizar o colisor de caixa, de modo que ele não seja muito grande nem muito pequeno. Ele deve ter aproximadamente o mesmo tamanho do objeto do qual está ao redor (neste exemplo, o núcleo da Terra). Ajuste o colisor de caixa, conforme necessário, selecionando a opção Editar colisor no colisor de caixa. Você pode alterar os valores x, y e z ou arrastar os manipuladores da caixa delimitadora na janela de cena do editor. 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. Adicione uma caixa delimitadora ao objeto "node_id30" do núcleo da Terra. Para fazer isso, selecione o objeto "node_id30" em "3DObjectCollection". Na guia do inspetor, clique em “Adicionar componente” e pesquise “caixa delimitadora”. Verifique se a caixa delimitadora, o colisor de caixa e os scripts de manipulação (manipulador de manipulação, segurável de interação próxima) estão todos no mesmo objeto de jogo.

3.  Na seção "Comportamento" da caixa delimitadora, selecione “Ativar no início” na lista suspensa Ativação. Para examinar detalhes adicionais sobre as várias opções de ativação e outras opções da caixa delimitadora, confira a [documentação sobre a caixa delimitadora do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

   

   *Nas próximas etapas, também alteraremos a aparência da caixa delimitadora ajustando o material de caixa padrão, o material enquanto ele está sendo segurado, bem como a visualização das alças (alças de canto e laterais). O MRTK contém várias opções para personalizar a caixa delimitadora.*

4. No painel do projeto, pesquisa “boundingbox” e você verá uma lista de materiais indicados por uma esfera azul nos resultados da pesquisa, conforme mostrado na imagem abaixo. 

5. Arraste o material “boundingbox” para o slot de material da caixa no componente de caixa delimitadora. Também segure o material “boundingboxgrabbed” e coloque isso no slot de material segurado da caixa no componente de caixa delimitadora.

6. Arraste o material “MRTK_BoundingBox_ScaleWidget” para o slot de pré-fabricado da alça de escala no componente de caixa delimitadora. 

7. Arraste o material “MRTK_BoundingBox_RotateWidget” para o slot da alça de rotação no componente de caixa delimitadora.

![Lesson4 Chapter3 Step4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. Verifique se a caixa delimitadora está voltada para o objeto à direita. No componente de caixa delimitadora, há o “objeto de destino” e scripts de “substituição de limites”. Arraste o objeto que tem a caixa delimitadora em torno dele para esses dois slots. Neste exemplo, arraste o objeto "node_id30" para esses dois slots, conforme mostrado na imagem abaixo.

> Quando você iniciar ou reproduzir o aplicativo, o objeto agora ficará rodeado por um quadro azul. Fique à vontade para arrastar os cantos do quadro para redimensionar o objeto. Se quisermos que as alças de dimensionamento e de rotação fiquem maiores e mais visíveis, recomendaremos o uso das configurações padrão da caixa delimitadora (evitando as etapas 4 a 7). 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. Para retornar à visualização padrão da caixa delimitadora, no painel do inspetor do objeto da caixa delimitadora, selecione o pré-fabricado da alça de rotação e pressione a tecla Delete. Agora você terá uma visualização da caixa delimitadora semelhante à imagem abaixo. Observação: as visualizações da caixa delimitadora só são exibidas no modo de reprodução.

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>Como adicionar efeitos de toque
Neste exemplo, reproduziremos um efeito sonoro quando você tocar um objeto com a mão.

1. Adicione um componente de fonte de áudio ao objeto do jogo. Selecione o objeto "octa" na hierarquia de cenas. No painel do inspetor, clique no botão "Adicionar componente", pesquise e selecione "fonte de áudio". Usaremos essa fonte de áudio para reproduzir um efeito sonoro em uma etapa posterior. 

>Observação: Verifique se o objeto "Octa" contém um colisor de caixa.

2. Adicione o componente “tocável de interação próxima”. Clique no botão "Adicionar Componente" no painel do inspetor e pesquise “tocável de interação próxima”. Selecione-o para adicionar o componente. OBSERVAÇÃO: captura de tela corrigida para realçar que estamos adicionando o componente, não apenas realçando o colisor de caixa.

>Observação: Anteriormente, adicionamos o “segurável de interação próxima”. A diferença entre isto e o “tocável com interação próxima” é que a interação "segurável" se destina a segurar um objeto e interagir com ele. O componente "tocável" destina-se a tocar o objeto. Ambos os componentes podem ser usados juntos para uma combinação de interações.

![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. Adicione o script de “toque com interação das mãos”. Observe que esse script é incluído na cena do Unity importada como parte deste pacote de demonstração e não está incluído no MRTK original. Assim como na etapa anterior, clique em “Adicionar componente” e pesquise “toque com interação das mãos” para adicioná-lo. 
   Observe que você tem três opções com o script: 

   - "Após o toque, concluído." Isso será disparado quando você tocar e soltar o objeto. 
   - "Após o toque, iniciado." Isso será disparado quando o objeto for tocado. 
   - "Após o toque, atualizado." Isso será disparado periodicamente enquanto sua mão estiver tocando o objeto. 

   Neste exemplo, trabalharemos com a configuração “Após o toque, iniciado”.

4. Clique no botão “+” na opção “Após o toque, iniciado”, conforme mostrado na imagem abaixo. Arraste o objeto Octa para o campo vazio. 

5. No menu suspenso que indica "nenhuma função" (acima do retângulo verde na imagem abaixo), selecione AudioSource>PlayOneShot. Adicionaremos um clipe de áudio a esse campo usando os seguintes conceitos:

   - O MRTK fornece uma pequena lista de clipes de áudio. Fique à vontade para explorá-los no painel do projeto. Você os encontrará na pasta “MixedRealityToolkit.SDK” e, em seguida, na pasta “ativos padrão”. Nela, você verá uma pasta “áudio” na qual estão todos os clipes de áudio.
   - Neste exemplo, usaremos o clipe de áudio "MRTK_Gem". 
   - Para adicionar um clipe de áudio, basta arrastar o clipe desejado do painel do projeto para o AudioSource.PlayOneShot (marcado por uma caixa verde no exemplo acima) no painel do inspetor.

   Agora quando o usuário alcançar e tocar o objeto Octa, a faixa de áudio "MRTK_Gem" será reproduzida. O script "Toque com Interação das Mãos" também ajustará a cor do objeto quando ele for tocado. 

![Lesson4 Chapter4 Step3 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>Parabéns 
Nesta lição, você aprendeu a organizar objetos 3D em uma coleção de grades e manipulá-los (dimensionamento, rotação e movimentação) usando a interação próxima (segurar com as mãos rastreadas) e a interação distante (usando os raios de foco ou os raios de mãos). Você também aprendeu a colocar caixas delimitadoras em torno de objetos 3D e usar e personalizar os itens nas caixas delimitadoras. Por fim, você aprendeu a disparar eventos ao tocar um objeto.

[Próxima lição: Entrada avançada](mrlearning-base-ch5.md)

