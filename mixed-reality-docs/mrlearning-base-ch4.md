---
title: Módulo MR Learning Base - interação do objeto 3D
description: Conclua este curso para aprender a implementar o reconhecimento de Face do Azure dentro de um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, hololens de tutoriais, unity,
ms.openlocfilehash: 344b3bc892839bc22445e10af644771bc7008ac3
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929588"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>Módulo MR Learning Base - interação do objeto 3D

Nesta lição, vamos percorrer conteúdo 3D básico e experiência do usuário. Aprenderemos a organizar objetos 3D como parte de uma coleção, saiba mais sobre delimitação caixas para manipulação básica, saiba mais sobre a interação de perto ou longe e saiba mais sobre o toque e pegue gestos de mão de acompanhamento. 

## <a name="objectives"></a>Objetivos

* Aprenda a organizar o conteúdo 3D usando a coleção de objetos de grade do MRTK
* Implementar caixas delimitadoras
* Configurar objetos 3D para manipulação básica (mover, girar e escala)
* Explore a interação próxima e distante
* Saiba mais sobre gestos, como toque e de captura de rastreamento de mão adicional

## <a name="instructions"></a>Instruções

### <a name="organizing-3d-objects-in-a-collection"></a>Organizando objetos 3D em uma coleção

1. Clique com botão direito em sua hierarquia e selecionar, "criar vazio". Isso cria um objeto do jogo vazio. Renomeie-o para "3DObjectCollection". Isso é onde podemos colocará todos os nossos objetos 3D. Verifique se a coleção de posicionamento está definida em x = 0, y = 0 e z = 0.

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. Importar BaseModule, ativos usando as mesmas instruções para importar os pacotes personalizados descritas [lição 1](mrlearning-base-ch1.md). Os ativos de BaseModule incluem módulos 3D e outros scripts úteis que serão usadas ao longo deste tutorial. O pacote do unity BaseModule pode ser encontrado aqui: <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. A xícara de café pré-fabricado pode ser reconhecida por um cubo azul ao lado dele. Não selecione a xícara de café com o cubo azul e um pequeno white paper (que indica o modelo 3D original e não pré-fabricado.) 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. Arraste o pré-fabricado xícara de café de sua escolha para o objeto do jogo "3DObjectCollection" da etapa 1. A xícara de café agora é um filho da coleção.

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. Em seguida, vamos adicionar mais objetos 3D na nossa cena. Abaixo está uma lista de objetos, vamos adicionar neste exemplo. Conforme você adiciona os objetos que você pode achar que eles apareçam na sua cena em vários tamanhos. Ajuste a escala de cada modelo 3D na configuração de transformação no painel Inspetor. Ajustes indicados para este exemplo são listados com os objetos abaixo. Essas palavras da pesquisa na caixa de pesquisa no seu painel do projeto e arraste pré-fabricado objeto 3D para o objeto "3DObjectCollection" semelhante à etapa anterior. Você encontrará esses coleção de pré-fabricados ativos > BaseModuleAssets > módulo de Base de pré-fabricados
- Pesquise "TheModule_BaseModuleIncomplete". Arraste na cena. Defina a escala para x = 0,03, y = 0,03, z = 0,03. 
- Pesquise "Octa_BaseModuleIncomplete". Arraste na cena. Defina a escala para x = 0.13. y = 0.13, z =0.13.
- Pesquise "EarthCore_BaseModuleIncomplete". Arraste na cena. Defina a escala para x = 50,0 y = 50,0, z = 50,0.
- Pesquise "Cheese_BaseModuleIncomplete". Arraste na cena. Defina a escala para x = 0,05, y = 0,05, z = 0,05.
- Pesquise "Model_Platonic_BaseModuleIncomplete". Arraste na cena. Defina a escala para x = 0.13, y = 0.13, z = 0.13.
- Pesquise "CoffeeCup_BaseModuleIncomplete". Arraste na cena.

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. Adicione 3 cubos na sua cena. Clique com botão direito no objeto "3DObjectCollection", selecione "objeto 3D" e selecione "Cubo". Defina a escala para x = 0,14, y = 0,14 e z = 0,14. Repita essa etapa 2 vezes adicionais para criar um total de 3 cubos. Como alternativa, você pode duplicar o cubo duas vezes para um total de 3 cubos. Você também pode optar por usar os pré-fabricados do cubo preparada três dos ativos > BaseModuleAssets > módulo de Base de pré-fabricados e selecione GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete e OrangeCube_BaseModuleIncomplete.

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. Organizar sua coleção de objetos para formar uma grade usando o procedimento descrito em [lição 2](mrlearning-base-ch2.md) usando a coleção de objetos de grade do MRTK. Consulte a imagem abaixo para ver um exemplo de como configurar os objetos em uma grade de 3x3.

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>Observação: Você notará que alguns dos objetos estão fora do centro, como os objetos na imagem acima. Isso ocorre porque o pré-fabricados ou objetos podem ter objetos filho que não estão alinhados. Fique à vontade para fazer os ajustes necessários para as posições de objeto ou posições de objeto filho para alcançar uma grade bem alinhada.


### <a name="manipulating-3d-objects"></a>Manipulação de objetos 3D
1. Adicione a capacidade de manipular um cubo. Para adicionar a capacidade de manipular objetos 3D, você deve fazer o seguinte:
-   Selecione o objeto 3D que você deseja manipular na sua hierarquia (no exemplo, um dos seus cubos).
-   Clique em "Adicionar componente". 
-   Pesquise por "manipulação".
-   Selecione "manipulador de manipulação".
-   Repita para todos os objetos 3D sob o objeto "3DObjectCollection", mas não a "3DObjectCollection" em si.
-   Verifique se todos os objetos 3D tem um colisor ou colisor caixa (Adicionar componente > caixa colisor).

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>O manipulador de manipulação é um componente que permitirá que você ajustar as configurações de como os objetos se comportam quando que está sendo manipulado. Isso inclui a rotação, dimensionamento, mover e movimentação de restrições em determinados eixos. 

2. Restringir um cubo, de modo que ele só pode ser dimensionado. Selecione um cubo no objeto "3DObjectCollection". No painel Inspetor, ao lado de "tipo de manipulação serão entregues dois", clique no menu suspenso e selecione "escalar". Isso torna para que o usuário só pode alterar o tamanho do cubo.

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. Altere a cor de cada cubo, de modo que podemos pode diferenciar entre eles. 
-   Vá para o painel de projeto e role para baixo até que você veja "MixedRealityToolkit.SDK", em seguida, selecioná-lo.
-   Selecione a pasta de "Standard Assets".
-   Clique na pasta "de materiais".
-   Arraste um material diferente para cada um dos seus cubos. 

>Observação: Você pode escolher qualquer cor para seus cubos. Para nosso exemplo, vamos usar "glowingcyan", "glowingorange" e "verde". Fique à vontade experimentar com diferentes cores. Para adicionar a cor para o cubo, clique no cubo que você deseja alterar a cor do e arraste o material para o campo de material do renderizador de malha no painel do Inspetor do cubo. 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. Selecione outro cubo no objeto "3DObjectCollection" e torná-lo para que sua movimentação é restrito para a distância de correção de cabeçalho. Para fazer isso, à direita de "restrição em movimento", clique no menu suspenso e selecione "corrigir a distância do início". Isso torna para que o usuário só pode mover o cubo no seu campo de visão. 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

Meta de próximas etapas: Habilitaremos captura e interação com nossos objetos 3D. Aplicaremos configurações diferentes de manipulação 

5. Selecione o objeto de Queijo e no painel Inspetor, clique em "Adicionar componente". 

6. Pesquisar na caixa de pesquisa "Perto de interação Grabbable" e selecione o script. Este componente permite que os usuários alcançar e pegue os objetos com mãos controladas. Objetos também terá permissão para ser manipulado de uma distância, a menos que a caixa de seleção "Permitir muito manipulação" está desmarcada (indicado por um círculo verde na imagem abaixo).

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. Adicione "Perto de interação Grabbable" para Octa objeto, objeto Platão, core Terra, módulo lunar e xícara de café, repetindo as etapas 5 e 6 nesses objetos.

8. Remova a capacidade de manipulação mais distante do objeto Octa. Para fazer isso, selecione o Octa na hierarquia e desmarque a caixa de seleção "permitir a manipulação mais distante" (marcada por um círculo verde). Isso torna para que os usuários podem interagir somente com o octa diretamente usando mãos controladas.

>Observação: Para a documentação completa do componente de manipulador de manipulação e ele associou configurações, consulte o [MRTK documentação](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Certifique-se de que o componente "Perto de interação Grabbable" foi adicionado para o núcleo da Terra, o módulo lunar e xícara de café (consulte a etapa 7).

10. Para o módulo lunar, altere as configurações do manipulador de manipulação, de modo que ele gira sobre o objeto center para ambos próximo e distante interação, conforme mostrado na imagem abaixo.

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11: Para o núcleo da Terra, alterar o comportamento de lançamento para "nada". Isso torna para que depois que o núcleo da Terra é liberado da compreensão dos usuários, ele não continue a mover. 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> Observação: Essa configuração é útil para cenários como a criação de uma bola de que você pode lançar. Manter a velocidade e a velocidade angular facilita para que depois que a bola for lançada, ele continuará a mover com a velocidade, foi lançado em, semelhante a como uma bola física seria se comportam.

### <a name="adding-bounding-boxes"></a>Adicionando caixas delimitadoras
Caixas delimitadoras torná-lo mais fácil e intuitivo para manipular objetos com uma mão para manipulação direta (próximo interação) e manipulação com base em ray (interação distante). Caixas delimitadoras oferecem "identificadores" que podem ser capturados para o dimensionamento e rotação de objetos ao longo de eixos específicos.
>Observação: Antes de adicionar uma caixa delimitadora para um objeto, que primeiro você precisa ter um colisor no objeto (por exemplo, um box collider.) Como fizemos anteriormente nesta lição. Colisores podem ser adicionados, selecionando o objeto e, no painel do Inspetor do objeto selecionando Adicionar componente > Box Collider.
>

1. Adicionar um box collider para o objeto principal de Terra, se ainda não existir (colisor caixa e a instalação não é necessário se usar pré-fabricado fornecido na pasta ativos do módulo de Base, por que as instruções fornecidas.) No caso do núcleo da Terra, precisaremos adicionar o colisor caixa para o objeto de "node_id30" sob o núcleo da Terra, conforme mostrado na imagem abaixo. Selecione node_id30 e no guia do Inspetor do objeto, clique em "adicionar o componente" e pesquise por "caixa colisor". 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> Observação: Certifique-se de que você visualize o colisor caixa para que não seja muito grande ou muito pequeno. Ele deve ser aproximadamente o mesmo tamanho que o objeto que ela é ao redor (no exemplo, o núcleo da Terra). Ajuste o colisor caixa conforme necessário, selecionando a opção de colisor Editar na colisor caixa. Você pode alterar os x, y e valores de z ou arraste os manipuladores da caixa delimitadora na janela do editor de cena. 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. Adicione uma caixa delimitadora ao objeto de "node_id30" do núcleo Terra. Para fazer isso, selecione o objeto de "node_id30" de "3DObjectCollection". Na guia do Inspetor de propriedades, clique em "adicionar o componente" e pesquise "caixa delimitadora". Verifique se a caixa delimitadora, colisor caixa e scripts de manipulação (manipulador de manipulação, perto de interação grabbable) estão todos no mesmo objeto de jogo.

3.  Na seção de "Comportamento" da caixa delimitadora, selecione "Ativar no início" na lista suspensa de ativação. Para examinar os detalhes adicionais sobre as várias opções de ativação e outras opções de caixa delimitadora, consulte o [documentação da caixa delimitadora do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

   

   *Nas próximas etapas, podemos também alterar a aparência da caixa delimitadora, ajustando o material de caixa padrão, o material enquanto ele está sendo capturado, bem como a visualização de identificadores (alças de canto e lado). O MRTK contém várias opções para personalizar a caixa delimitadora.*

4. No painel de projeto, procure "boundingbox" e você verá uma lista de materiais indicado por um círculo azul nos resultados da pesquisa, conforme mostrado na imagem abaixo. 

5. Arraste o material "boundingbox" no slot de material de caixa no componente de caixa delimitadora. Também, pegue o material "boundingboxgrabbed" e colocar isso no slot de material grabbed caixa no componente de caixa delimitadora.

6. Arraste o material "MRTK_BoundingBox_ScaleWidget" para o slot de pré-fabricado alça de dimensionamento no componente de caixa delimitadora. 

7. Arraste o material "MRTK_BoundingBox_RotateWidget" para o slot da alça de rotação no componente de caixa de acoplamento.

![Lesson4 Chapter3 7Im da etapa 4](images/Lesson4_chapter3_step4-7im.PNG)

8. Verifique se a caixa delimitadora está voltada para o objeto à direita. O componente da caixa delimitadora, há o "objeto de destino" e "limites de substituição" scripts. Certifique-se de arrastar o objeto que tem a caixa delimitadora em torno dele para ambos esses slots. Neste exemplo, arraste o objeto de "node_id30" para os dois desses slots, conforme mostrado na imagem abaixo.

> Quando você iniciar ou executar o aplicativo, seu objeto agora ficará cercado por um quadro de azul. Você pode arrastar os cantos do quadro para redimensionar o objeto. Se quisermos que as alças de dimensionamento e os identificadores de rotação a ser maiores e mais visíveis, é recomendável usar o padrão de delimitação de configurações do box (evitando as etapas 4 a 7). 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. Para retornar para o padrão de delimitação de visualização, no painel de inspeção de objeto da caixa delimitadora, selecione pré-fabricado alça de rotação e pressione a tecla delete, agora você verá uma visualização de caixa delimitadora semelhante à imagem a seguir. Observação: as visualizações de caixa delimitadora só aparece quando no modo de execução.

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>A adição de efeitos de toque
Neste exemplo, vamos jogar um efeito sonoro quando você toca em um objeto com a mão.

1. Adicione um componente de fonte de áudio para o objeto do jogo. Selecione o objeto de "octa" em sua hierarquia da cena. No painel Inspetor, clique no botão "adicionar o componente", pesquise e selecione "fonte de áudio". Vamos usar essa fonte de áudio para reproduzir um som efeito em uma etapa posterior. 

>Observação: Certifique-se de que o objeto de "Octa" tem um box collider nele.

2. Adicione o componente "near interação touchable". Clique no botão "Adicionar componente" no painel Inspetor e procurar "quase interação touchable". Selecione para adicionar o componente. Observação: corrigi a captura de tela para destacar que estamos adicionando o componente e não apenas realce colisor caixa.

>Observação: Anteriormente, adicionamos a "quase interação grabbable." A diferença entre este e "near interação touchable" é que a interação do "grabbable" destina-se de um objeto a ser capturado e interagir com. O componente "touchable" destina-se para o objeto a ser tocado. Ambos os componentes podem ser usados juntos para uma combinação de interações.

![Lesson4 Chapter4 2Im da etapa 1](images/Lesson4_chapter4_step1-2im.PNG)

3. Adicione no script "entregar o toque de interação". Observe que esse script seja incluído na cena unity importado como parte desse pacote de demonstração e ele não está incluído no MRTK original. Assim como a etapa anterior, clique em "adicionar o componente" e pesquise por "toque de interação de mão" para adicioná-lo. 
   Observe que você tem 3 opções com o script: 

   - "No touch concluído." Isso vai disparar quando você tocar e liberar o objeto. 
   - "No touch iniciado." Isso vai disparar quando o objeto é tocado. 
   - "No touch atualizada." Isso vai disparar periodicamente enquanto sua mão tocando o objeto. 

   Neste exemplo, podemos estará trabalhando com a configuração "no touch iniciado".

4. Clique no botão "+" na opção "no touch iniciado", conforme mostrado na imagem abaixo. Arraste o objeto octa para o campo vazio. 

5. No menu suspenso que não diz "nenhuma função" (acima de retângulo verde na imagem abaixo), selecione AudioSource > PlayOneShot. Adicionaremos um clipe de áudio para este campo usando os conceitos a seguir:

   - O MRTK fornecem uma pequena lista de clipes de áudio. Fique à vontade explorar isso no seu painel do projeto. Você irá encontrá-los sob a pasta "MixedRealityToolkit.SDK" e, em seguida, a pasta de "standard assets". Lá você verá uma pasta de "áudio" onde estão todos os clipes de áudio.
   - Neste exemplo, vamos usar o clipe de áudio de "MRTK_Gem". 
   - Para adicionar um clipe de áudio, basta arraste o clipe desejado do painel de projeto para o AudioSource.PlayOneShot (marcado por caixa verde no exemplo acima) no painel Inspetor.

   Agora quando o usuário acessa e toca o objeto octa, a faixa de áudio "MRTK_Gem" será executada. O script "Mão interação Touch" também se ajustará a cor do objeto quando tocado. 

![Etapa 3 de Chapter4 Lesson4 Noteim 5](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>Parabéns! 
Nesta lição, você aprendeu como organizar objetos 3D em uma coleção de grade e manipular objetos 3D (Dimensionar, girar e mover) usando perto de interação (pegando diretamente com as mãos controladas) e interação mais distante (usando olhar raios ou raios de mão). Você também aprendeu a colocar as caixas delimitadoras em torno de objetos 3D e aprendeu a usar e personalizar os utensílios em caixas delimitadoras. Por fim, você aprendeu como disparar eventos quando tocar em um objeto.

[Próxima lição: Entrada avançada](mrlearning-base-ch5.md)

