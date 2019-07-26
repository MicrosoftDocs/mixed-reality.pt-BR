---
title: Módulo Base de Aprendizado de MR – Interação de Objeto 3D
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 314af3e1e38e1698943f07dc32f5e1e3e2f36d4f
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485700"
---
# <a name="5-interacting-with-3d-objects"></a>5. Interagindo com objetos 3D

Neste tutorial, aprendemos sobre o conteúdo básico de 3D e a experiência do usuário. Falaremos sobre: 
* Organizar objetos 3D como parte de uma coleção.
* Caixas delimitadoras para manipulação básica.
* Interação próxima e distante.
* Gestos de toque e captura com acompanhamento manual. 

## <a name="objectives"></a>Objetivos

* Saiba como organizar o conteúdo 3D com a coleção de objetos de grade do MRTK
* Implementar caixas delimitadoras
* Configurar objetos 3D para manipulação básica – mover, girar e dimensionar
* Explorar a interação próxima e distante
* Saiba mais sobre gestos de acompanhamento de mão, como pegar e tocar

## <a name="instructions"></a>Instruções

### <a name="organizing-3d-objects-in-a-collection"></a>Como organizar objetos 3D em uma coleção

1. Clique com o botão direito do mouse na sua hierarquia e selecione criar vazio. Isso criará um objeto de jogo vazio. Renomeie-o como 3DObjectCollection. Esse é o local em que colocaremos todos os nossos objetos 3D. Verifique se o posicionamento da coleção está definido como x = 0, y = 0 e z = 0.

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. Importe ativos do BaseModule usando as mesmas instruções para importar pacotes personalizados descritos em [lição 1](mrlearning-base-ch1.md). Os ativos do BaseModule incluem módulos 3D e outros scripts úteis que são usados em todo este tutorial. O pacote do BaseModule Unity pode ser encontrado aqui:<https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. O pré-fabricado da xícara de café pode ser reconhecido por um cubo azul ao lado dele. Não selecione a xícara de café com o cubo azul e o pequeno white paper porque isso denota o modelo 3D original e não o pré-fabricado.) 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. Arraste a pré-fabricado xícara de café de sua escolha para o objeto de jogo 3DObjectCollection da etapa 1. A xícara de café agora é um filho da coleção.

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. Em seguida, adicionaremos mais objetos 3D à nossa cena. Veja abaixo uma lista de objetos que adicionaremos neste exemplo. Ao adicionar os objetos, você pode achar que eles aparecem em sua cena em vários tamanhos. Ajuste a escala de cada modelo 3D em configuração de transformação no painel de Inspetor. Os ajustes indicados para este exemplo são listados com os objetos abaixo. Pesquise essas palavras na caixa de pesquisa no painel de projeto e arraste o objeto 3D pré-fabricado para o objeto 3DObjectCollection semelhante à etapa anterior. Você encontrará essas coleções de pré-fabricados nos ativos > BaseModuleAssets > módulo base pré-fabricados
- Procure TheModule_BaseModuleIncomplete. Arraste-o para a cena. Defina a escala como x = 0,03, y = 0,03, z = 0,03. 
- Procure Octa_BaseModuleIncomplete. Arraste-o para a cena. Defina a escala como x = 0,13. y = 0,13, z = 0,13.
- Procure EarthCore_BaseModuleIncomplete. Arraste-o para a cena. Defina a escala como x = 50,0 y = 50,0, z = 50,0.
- Procure Cheese_BaseModuleIncomplete. Arraste-o para a cena. Defina a escala como x = 0,05, y = 0,05, z = 0,05.
- Procure Model_Platonic_BaseModuleIncomplete. Arraste-o para a cena. Defina a escala como x = 0,13, y = 0,13, z = 0,13.

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. Adicione três cubos à sua cena. Clique com o botão direito do mouse no objeto 3DObjectCollection, selecione objeto 3D e, em seguida, selecione cubo. Defina a escala como x = 0,14, y = 0,14 e z = 0,14. Repita essa etapa duas vezes mais para criar um total de três cubos. Como alternativa, você pode duplicar o cubo duas vezes para um total de três cubos. Você também pode optar por usar os pré-fabricados do cubo preparados de Ativos>BaseModuleAssets>Pré-fabricados do Módulo Base e selecionar GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete e OrangeCube_BaseModuleIncomplete.

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. Organize a coleção de objetos para formar uma grade usando o procedimento descrito na [Lição 2](mrlearning-base-ch2.md) usando a coleção de objetos de grade do MRTK. Veja a imagem abaixo para ver um exemplo de como configurar os objetos em uma grade 3x3.

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>Observação: Você pode observar que alguns dos objetos estão fora do centro, como os objetos na imagem acima. Isso ocorre porque os pré-fabricados ou os objetos podem ter objetos filho que não estão alinhados. Fique à vontade para fazer os ajustes necessários nas posições de objetos ou de objetos filho para obter uma grade bem alinhada.


### <a name="manipulating-3d-objects"></a>Como manipular objetos 3D
1. Adicione a capacidade de manipular um cubo. Para adicionar a capacidade de manipular objetos 3D, faça o seguinte:
-   Selecione o objeto 3D que você deseja manipular em sua hierarquia, ou seja, um de seus cubos.
-   Clique em Adicionar componente. 
-   Procure manipulação.
-   Selecione manipulador de manipulação.
-   Repita para todos os objetos 3D sob o objeto 3DObjectCollection, mas não o 3DObjectCollection em si.
-   Certifique-se de que todos os objetos 3D tenham um colisor ou Colisor de caixa (adicionar componente > do box).

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>O manipulador de manipulação é um componente que permite ajustar as configurações de como os objetos se comportam quando manipulados. Isso inclui a rotação, o dimensionamento, a movimentação e a restrição da movimentação em um eixo específico. 

2. Restrinja um cubo, de modo que ele só possa ser dimensionado. Selecione um cubo no objeto 3DObjectCollection. No painel Inspetor, ao lado de dois tipos de manipulação de mão, clique no menu suspenso e selecione escala. Isso faz com que o usuário só possa alterar o tamanho do cubo.

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. Altere a cor de cada cubo, de modo que possamos diferenciar entre eles. 
-   Vá para o painel projeto e role para baixo até ver MixedRealityToolkit. SDK e, em seguida, selecione-o.
-   Selecione a pasta ativos padrão.
-   Clique na pasta materiais.
-   Arraste outro material para cada um dos cubos. 

>Observação: Escolha qualquer cor para os cubos. Para nosso exemplo, vamos usar glowingcyan, glowingorange e Green. Fique à vontade para experimentar com cores diferentes. Para adicionar a cor ao cubo, clique no cubo que você deseja alterar e arraste o material para o campo material do processador de malha no painel Inspetor do cubo. 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. Selecione outro cubo no objeto 3DObjectCollection e faça-o para que seu movimento seja restrito a uma distância fixa do cabeçalho. Para fazer isso, à direita de restrição no rótulo de movimentação, clique no menu suspenso e selecione corrigir distância do cabeçalho. Isso faz com que o usuário só possa mover o cubo em seu campo de visão. 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

O objetivo das próximas etapas é habilitar a captura e a interação com nossos objetos 3D e a aplicação de configurações de manipulação diferentes.

5. Selecione o objeto queijo e clique em Adicionar componente no painel inspetor. 

6. Pesquise na caixa de pesquisa para obter uma interacção de interação próxima e selecione o script. Esse componente permite que os usuários alcancem e peguem objetos com mãos controladas. Os objetos também podem ser manipulados de uma distância, a menos que a caixa de seleção Permitir manipulação distante esteja desmarcada como indicado por um círculo verde na imagem abaixo.

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. Adicione uma interação próxima que seja possível para o objeto Octa, objeto Platão, núcleo terrestre, módulo lunar e xícara de café repetindo as etapas 5 e 6 nesses objetos.

8. Remova a capacidade de manipulação distante do objeto Octa. Para fazer isso, selecione o Octa na hierarquia e desmarque a caixa de seleção Permitir manipulação distante (marcada por um círculo verde). Isso faz com que os usuários só possam interagir com o Octa diretamente usando mãos rastreadas.

>Observação: Para obter a documentação completa do componente de manipulador de manipulação e as respectivas configurações associadas, confira a [Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Certifique-se de que o componente de improximidade de interação Near tenha sido adicionado ao núcleo da terra, o módulo lunar e a xícara de café (consulte a etapa 7).

10. Para o módulo lunar, altere as configurações do manipulador de manipulação para que ele gire sobre o centro do objeto para interação próxima e extrema, conforme mostrado na imagem abaixo.

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11: Para o núcleo terrestre, altere o comportamento da versão para Nothing. Isso faz com que, assim que o núcleo da terra for lançado da noção do usuário, ele não continue a se mover. 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> Observação: Essa configuração é útil para cenários como a criação de uma bola que você pode lançar. Manter a velocidade e a velocidade angular faz com que, assim que a bola for liberada, ela continuará a mudar para a velocidade em que foi lançada em, semelhante a como uma bola física se comportaria.

### <a name="adding-bounding-boxes"></a>Como adicionar caixas delimitadoras
As caixas delimitadoras facilitam e tornam intuitiva a manipulação de objetos com uma mão para a manipulação direta (interação próxima) e a manipulação baseada em raio (interação distante). As caixas delimitadoras fornecem identificadores que podem ser capturados para dimensionar e girar objetos ao longo de um eixo específico.
>Observação: Antes de adicionar uma caixa delimitadora a um objeto, primeiro você precisa ter um colisor no objeto (por exemplo, um colisor de caixa), como fizemos anteriormente nesta lição. Os colisores podem ser adicionados pela seleção do objeto e, no painel do inspetor do objeto, pela seleção de Adicionar Componente>Colisor de Caixa.
>

1. Adicione um colisor de caixa ao objeto principal do Terra se ainda não existir um. O colisor de caixa e a instalação não serão necessários se você usar o pré-fabricado fornecido na pasta de ativos de módulo base de acordo com as instruções fornecidas. No caso do núcleo terrestre, adicionamos o cocolisorr Box ao objeto node_id30, sob o núcleo terra, conforme mostrado na imagem abaixo. Selecione node_id30 na guia Inspetor do objeto, clique em Adicionar componente e procure o colisor da caixa. 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> Observação: Certifique-se de dimensionar o colisor de caixa para que ele não seja muito grande ou muito pequeno. Ele deve ter aproximadamente o mesmo tamanho do objeto do qual está ao redor (neste exemplo, o núcleo da Terra). Ajuste o colisor da caixa, conforme necessário, selecionando a opção Editar colisor no colisor do box. Você pode alterar os valores x, y e z ou arrastar os manipuladores de caixa delimitadora na janela cena do editor. 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. Adicione uma caixa delimitadora ao objeto node_id30 do núcleo da terra. Para fazer isso, selecione o objeto node_id30 do 3DObjectCollection. Na guia Inspetor, clique em Adicionar componente e procure a caixa delimitadora. Verifique se a caixa delimitadora, o colisor de caixa e os scripts de manipulação (manipulador de manipulação, segurável de interação próxima) estão todos no mesmo objeto de jogo.

3.  Na seção comportamento da caixa delimitadora, selecione Ativar no início na lista suspensa ativação. Para examinar detalhes adicionais sobre as várias opções de ativação e outras opções da caixa delimitadora, confira a [documentação sobre a caixa delimitadora do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

   

   *Nas próximas etapas, também alteraremos a aparência da caixa delimitadora ajustando o material da caixa padrão, o material enquanto ele está sendo capturado, bem como a visualização das alças do canto e do lado. O MRTK contém várias opções para personalizar a caixa delimitadora.*

4. No painel projeto, pesquise BoundingBox e você verá uma lista de materiais denotados por uma esfera azul nos resultados da pesquisa, conforme mostrado na imagem abaixo. 

5. Arraste o material de BoundingBox para o slot de material da caixa no componente da caixa delimitadora. Além disso, pegue o material do boundingboxgrabbed e coloque-o na caixa slot de material capturado no componente da caixa delimitadora.

6. Arraste o MRTK_BoundingBox_ScaleWidget pré-fabricado para o slot da alça de escala pré-fabricado no componente da caixa delimitadora. 

7. Arraste o MRTK_BoundingBox_RotateWidget pré-fabricado para o slot identificador de rotação no componente da caixa de acoplamento.

![Lesson4 Chapter3 Step4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. Verifique se a caixa delimitadora está voltada para o objeto à direita. No componente da caixa delimitadora, há o objeto de destino e os limites de substituição de scripts. Arraste o objeto que tem a caixa delimitadora em torno dele para esses dois slots. Neste exemplo, arraste o objeto node_id30 para ambos os slots, conforme mostrado na imagem abaixo.

> Quando você iniciar ou reproduzir o aplicativo, o objeto será circundado por um quadro azul. Fique à vontade para arrastar os cantos do quadro para redimensionar o objeto. Se você quiser que os identificadores de dimensionamento e os identificadores de rotação sejam maiores e mais visíveis, é recomendável usar as configurações da caixa delimitadora padrão (evitando as etapas 4 a 7). 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. Para retornar à visualização da caixa delimitadora padrão, no painel Inspetor do objeto da caixa delimitadora, selecione a alça de rotação pré-fabricado e pressione Delete. Você verá uma visualização de caixa delimitadora semelhante à imagem abaixo. Observação: as visualizações da caixa delimitadora só são exibidas no modo de reprodução.

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>Adicionando efeitos de toque
Neste exemplo, reproduziremos um efeito sonoro quando você tocar um objeto com a mão.

1. Adicione um componente de fonte de áudio ao objeto do jogo. Selecione o objeto Octa na sua hierarquia de cena. No painel Inspetor, clique no botão Adicionar componente, procure e selecione fonte de áudio. Usaremos essa fonte de áudio para reproduzir um efeito sonoro em uma etapa posterior. 

>Observação: Verifique se o objeto Octa tem um colisor de caixa nele.

2. Adicione o componente de toque próximo à interação. Clique no botão Adicionar componente no painel Inspetor e procure por uma interação próxima com o touchable. Selecione-o para adicionar o componente. 

>Observação: Anteriormente, adicionamos perto da interação. A diferença entre essa e a próxima interação é que a interação de captação destina-se a ser capturado e interagir com um objeto. O componente que deve ser tocável destina-se ao objeto a ser tocado. Ambos os componentes podem ser usados juntos para uma combinação de interações.

![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. Adicione o script de toque de interação manual. Observe que esse script está incluído na cena do Unity que você importou como parte desta demonstração e não está incluído no MRTK original. Assim como na etapa anterior, clique em Adicionar componente e pesquise por toque de interação à mão para adicioná-lo.

>Observe que você tem três opções com o script: 

>   - No toque concluído: Dispara quando você toca e libera o objeto
>   - No toque iniciado: Dispara quando o objeto é tocado
>   - Em contato atualizado: Os gatilhos periodicamente estão tocando no objeto

>   Para este exemplo, iremos trabalhar com a configuração on Touch Started.

4. Clique no botão + na opção on Touch started, conforme mostrado na imagem abaixo. Arraste o objeto Octa para o campo vazio. 

5. Na lista suspensa que não diz nenhuma função (acima do retângulo verde na imagem abaixo), selecione Audioie-> PlayOneShot. Adicionaremos um clipe de áudio a esse campo usando os seguintes conceitos:

   - O MRTK fornece uma pequena lista de clipes de áudio. Fique à vontade para explorá-los no painel do projeto. Você os encontrará na pasta MixedRealityToolkit. SDK e na pasta ativos padrão. Lá, você verá uma pasta de áudio onde todos os clipes de áudio são.
   - Para este exemplo, vamos usar o clipe de áudio MRTK_Gem. 
   - Para adicionar um clipe de áudio, basta arrastar o clipe desejado do painel do projeto para o AudioSource.PlayOneShot (marcado por uma caixa verde no exemplo acima) no painel do inspetor.

   Agora, quando o usuário chegar e tocar no objeto Octa, a faixa de áudio MRTK_Gem será reproduzida. O script de toque de interação manual também ajustará a cor do objeto quando tocado. 

![Lesson4 Chapter4 Step3 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

## <a name="congratulations"></a>Parabéns 
Neste tutorial, você aprendeu a organizar objetos 3D em uma coleção de grade e a manipular objetos 3D (dimensionamento, rotação e movimentação) usando a interação próxima (pegando diretamente com as mãos controladas) e a interação extrema (usando raios olhar ou raios de mão). Você também aprendeu como colocar caixas delimitadoras em objetos 3D e aprendeu como usar e personalizar o utensílios nas caixas delimitadoras. Por fim, você aprendeu a disparar eventos ao tocar um objeto.

[Próxima lição: 6. Explorar as opções avançadas de entrada](mrlearning-base-ch5.md)

