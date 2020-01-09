---
title: Tutoriais de introdução-5. Interagindo com objetos 3D
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: fe068d0cfcea369f10e6fa636eb73fecb3002fa7
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334379"
---
# <a name="5-interacting-with-3d-objects"></a>5. interagindo com objetos 3D

Neste tutorial, você aprenderá sobre o conteúdo básico de 3D e a experiência do usuário, como:

* Organizando objetos 3D como parte de uma coleção
* Caixas delimitadoras para manipulação básica
* Interação próxima e distante
* Gestos de toque e captura com acompanhamento manual

## <a name="objectives"></a>Objetivos

* Saiba como organizar o conteúdo 3D com a coleção de objetos de grade do MRTK
* Implementar caixas delimitadoras
* Configurar objetos 3D para manipulação básica – mover, girar e dimensionar
* Explorar a interação próxima e distante
* Saiba mais sobre gestos de acompanhamento de mão, como pegar e tocar

## <a name="organizing-3d-objects-in-a-collection"></a>Como organizar objetos 3D em uma coleção

1. Clique com o botão direito do mouse na sua hierarquia e selecione criar vazio para criar um objeto de jogo vazio, renomeie-o como 3DObjectCollection e verifique se ele está posicionado em x = 0, y = 0 e z = 0.

    ![mrlearning-base-CH4-1-Step1. png](images/mrlearning-base-ch4-1-step1.png)

2. Baixe o pacote do Unity [Unity. HoloLens2. gettingstarted. tutoriais. Asset. 2.1.0.0](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) e importe-o usando as mesmas instruções para importar pacotes personalizados descritos em [lição 1](mrlearning-base-ch1.md). Este pacote inclui modelos 3D e outros ativos úteis que são usados em todo este tutorial.

3. No painel projeto, navegue até ativos > BaseModuleAssets > módulo base pré-fabricados e pesquise "incompleto", usaremos alguns desses pré-fabricados.

    ![mrlearning-base-CH4-1-Step3. png](images/mrlearning-base-ch4-1-step3.png)

4. Arraste a xícara de café para o objeto de jogo 3DObjectCollection da etapa 1. A xícara de café agora é um filho da coleção.

    ![mrlearning-base-CH4-1-step4. png](images/mrlearning-base-ch4-1-step4.png)

5. Em seguida, você adicionará mais objetos 3D em nossa cena seguindo o mesmo processo que na etapa anterior. Abaixo está uma lista de objetos a serem adicionados neste exemplo. À medida que você adiciona os objetos, talvez ache que eles apareçam em sua cena em vários tamanhos. Ajuste a escala de cada modelo 3D em configurações de transformação no painel inspetor. Os ajustes indicados para este exemplo são listados com os objetos abaixo.

    * Cheese_BaseModuleIncomplete. Escala: x = 0, 5, y = 0, 5, z = 0, 5.
    * CoffeeCup_BaseModuleIncomplete. Escala: x = 0,1, y = 0,1, z = 0,1.
    * EarthCore_BaseModuleIncomplete. Escala: x = 50,0 y = 50,0, z = 50,0.
    * Model_Platonic_BaseModuleIncomplete. Escala: x = 0,13, y = 0,13, z = 0,13.
    * Octa_BaseModuleIncomplete. Escala: x = 0,13. y = 0,13, z = 0,13.
    * TheModule_BaseModuleIncomplete. Escala: x = 0, 3, y = 0, 3, z = 0, 3.

    ![mrlearning-base-CH4-1-Step5. png](images/mrlearning-base-ch4-1-step5.png)

6. Adicione três cubos à sua cena. Clique com o botão direito do mouse no objeto 3DObjectCollection, selecione objeto 3D e, em seguida, selecione cubo. Defina a escala como x = 0,14, y = 0,14 e z = 0,14. Repita essa etapa duas vezes mais para criar um total de três cubos. Como alternativa, você pode duplicar o cubo duas vezes para um total de três cubos. Você também pode optar por usar os pré-fabricados do cubo preparados de Ativos>BaseModuleAssets>Pré-fabricados do Módulo Base e selecionar GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete e OrangeCube_BaseModuleIncomplete.

    ![mrlearning-base-CH4-1-step6. png](images/mrlearning-base-ch4-1-step6.png)

7. Organize sua coleção de objetos para formar uma grade, por meio do procedimento descrito na [lição 2](mrlearning-base-ch2.md), usando a coleção de objetos de grade do MRTK. Consulte a imagem abaixo, para obter um exemplo de como configurar os objetos em uma grade 3x3.

    ![mrlearning-base-CH4-1-Step7. png](images/mrlearning-base-ch4-1-step7.png)

    >[!NOTE]
    >Você pode observar que alguns dos objetos estão fora do centro, como os objetos na imagem acima. Isso ocorre porque os pré-fabricados ou os objetos podem ter objetos filho que não estão alinhados. Fique à vontade para fazer os ajustes necessários nas posições de objetos ou de objetos filho para obter uma grade bem alinhada.

## <a name="manipulating-3d-objects"></a>Como manipular objetos 3D

1. Adicione a capacidade de manipular um cubo. Para adicionar a capacidade de manipular objetos 3D, faça o seguinte:
    * Selecione o objeto 3D que você deseja manipular em sua hierarquia (ou seja, um de seus cubos).
    * Clique em Adicionar componente
    * Procurar por "manipulação"
    * Selecionar manipulador de manipulação
    * Repita para todos os objetos 3D sob o objeto 3DObjectCollection, mas não o 3DObjectCollection em si.
    * Certifique-se de que todos os objetos 3D tenham um colisor ou Colisor de caixa (adicionar componente > do box).

    ![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

    >[!NOTE]
    >O manipulador de manipulação é um componente que permite ajustar as configurações de como os objetos se comportam quando manipulados. Isso inclui a rotação, o dimensionamento, a movimentação e a restrição da movimentação em um eixo específico.

2. Restrinja um cubo, de modo que ele só possa ser dimensionado. Selecione um cubo no objeto 3DObjectCollection. No painel Inspetor, ao lado de dois tipos de manipulação de mão, clique no menu suspenso e selecione escala. Isso faz com que o usuário só possa alterar o tamanho do cubo.

    ![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. Altere a cor de cada cubo, de modo que possamos diferenciar entre eles.
    * Vá para o painel projeto e role para baixo até ver MixedRealityToolkit. SDK e, em seguida, selecione-o.
    * Selecione a pasta ativos padrão.
    * Clique na pasta materiais.
    * Arraste outro material para cada um dos cubos.

    >[!NOTE]
    >Escolha qualquer cor para os cubos. Para este exemplo, glowingcyan, glowingorange e Green são usados. Fique à vontade para experimentar com cores diferentes. Para adicionar a cor ao cubo, clique no cubo que você deseja alterar e arraste o material para o campo material do processador de malha no painel Inspetor do cubo.

    ![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. Selecione outro cubo no objeto 3DObjectCollection e faça-o para que seu movimento seja restrito a uma distância fixa do cabeçalho. Para fazer isso, à direita de restrição no rótulo de movimento, clique no menu suspenso e selecione corrigir distância do cabeçalho. Isso ajusta o cubo para estar dentro de seu campo de visão.

    ![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

    O objetivo das algumas etapas a seguir é habilitar a captura e a interação com nossos objetos 3D e a aplicação de configurações de manipulação diferentes.

5. Selecione o objeto queijo e clique em Adicionar componente no painel inspetor.

6. Pesquise na caixa de pesquisa para obter uma interação próxima que seja possível capturar e selecione o script. Esse componente permite que os usuários atinjam e peguem objetos com mãos controladas. Os objetos também podem ser manipulados de uma distância, a menos que a caixa de seleção Permitir manipulação distante esteja desmarcada como indicado por um círculo verde na imagem abaixo.

    ![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. Adicione uma interação próxima que seja possível para o objeto Octa, objeto Platão, núcleo terrestre, módulo lunar e xícara de café repetindo as etapas 5 e 6 nesses objetos.

8. Remova a capacidade de manipulação distante do objeto Octa. Para fazer isso, selecione o Octa na hierarquia e desmarque a caixa de seleção Permitir manipulação distante (marcada por um círculo verde). Isso o torna para que os usuários possam interagir apenas com o Octa diretamente usando as mãos rastreadas.

    >[!NOTE]
    >Para obter a documentação completa do componente manipulador de manipulação e suas configurações associadas, consulte a [documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Certifique-se de que o componente de improximidade de interação Near tenha sido adicionado ao núcleo da terra, o módulo lunar e a xícara de café (consulte a etapa 7).

10. Para o módulo lunar, altere as configurações do manipulador de manipulação para que ele gire em volta do centro do objeto para interação próxima e distante, conforme mostrado na imagem abaixo.

    ![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11. Para o núcleo terrestre, altere o comportamento da versão para Nothing. Isso faz com que, assim que o núcleo da terra for lançado da noção do usuário, ele não continue a se mover.

    ![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

    >[!NOTE]
    >Essa configuração é útil para cenários, como a criação de uma bola que você pode lançar. Mantendo a velocidade apropriada e a velocidade angular para garantir que, depois que a bola for liberada, ela continuará a ser movida na velocidade em que foi lançada; semelhante a como uma bola física se comportaria.

## <a name="adding-bounding-boxes"></a>Como adicionar caixas delimitadoras

As caixas delimitadoras tornam mais fácil e mais intuitivo manipular objetos com uma mão para a manipulação direta (próxima interação) e a manipulação baseada em Ray (interação extrema). As caixas delimitadoras fornecem identificadores que podem ser capturados para dimensionar e girar objetos ao longo de um eixo específico.

>[!NOTE]
>Antes de adicionar uma caixa delimitadora a um objeto, primeiro você precisa ter um colisor no objeto (por exemplo, um colisor de caixa), como foi abordado anteriormente nesta lição. Os colisor podem ser adicionados selecionando-se o objeto e, no painel Inspetor do objeto, selecionando Adicionar componente > caixa do colisor.

1. Adicione um colisor de caixa ao objeto principal do Terra se ainda não existir um. O colisor e a instalação do box não são necessários, se usar o pré-fabricado fornecido na pasta de ativos do módulo base de acordo com as instruções fornecidas. No caso do núcleo terrestre, adicionamos o cocolisorr Box ao objeto, node_id30, sob o núcleo terra, conforme mostrado na imagem abaixo. Selecione node_id30 na guia Inspetor do objeto, clique em Adicionar componente e procure o colisor da caixa.

    ![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

    ![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

    >[!NOTE]
    >Certifique-se de dimensionar o colisor de caixa para que ele não seja muito grande ou muito pequeno. Ele deve ter aproximadamente o mesmo tamanho do objeto do qual está ao redor (neste exemplo, o núcleo da Terra). Ajuste o colisor da caixa, conforme necessário, selecionando a opção Editar colisor no colisor do box. Você pode alterar os valores x, y e z ou arrastar os manipuladores de caixa delimitadora na janela cena do editor.

    ![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. Adicione uma caixa delimitadora ao objeto de node_id30 do núcleo da terra. Para fazer isso, selecione o objeto node_id30 do 3DObjectCollection. Na guia Inspetor, clique em Adicionar componente e procure a caixa delimitadora. Verifique se a caixa delimitadora, o colisor de caixa e os scripts de manipulação (manipulador de manipulação, segurável de interação próxima) estão todos no mesmo objeto de jogo.

3. Na seção comportamento da caixa delimitadora, selecione Ativar no início na lista suspensa ativação. Para examinar detalhes adicionais sobre as várias opções de ativação e outras opções de caixa delimitadora, consulte a [documentação da caixa delimitadora do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

    *Nas próximas etapas, também alteraremos a aparência da caixa delimitadora ajustando o material da caixa padrão, o material enquanto ele está sendo capturado, bem como a visualização das alças do canto e do lado. O MRTK contém várias opções para personalizar a caixa delimitadora.*

4. No painel projeto, pesquise "BoundingBox" e você verá uma lista de materiais denotados por uma esfera azul nos resultados da pesquisa, conforme mostrado na imagem abaixo.

5. Arraste o material de BoundingBox para o slot de material da caixa no componente da caixa delimitadora. Além disso, pegue o material de boundingboxgrabbed e coloque-o na caixa slot de material capturado no componente da caixa delimitadora.

    ![mrlearning-base-CH4-3-Step5. png](images/mrlearning-base-ch4-3-step5.png)

6. Arraste o MRTK_BoundingBox_ScaleHandle pré-fabricado para o slot pré-fabricado do identificador de escala e o MRTK_BoundingBox_RotateHandle pré-fabricado para o slot identificador de rotação no componente da caixa de acoplamento.

    ![mrlearning-base-CH4-3-step6. png](images/mrlearning-base-ch4-3-step6.png)

7. Verifique se a caixa delimitadora está voltada para o objeto à direita. No componente da caixa delimitadora, há o objeto de destino e os limites de substituição de scripts. Arraste o objeto que tem a caixa delimitadora em volta dele para ambos os slots. Neste exemplo, arraste o objeto node_id30 para ambos os slots, conforme mostrado na imagem abaixo.

    ![mrlearning-base-CH4-3-Step7. png](images/mrlearning-base-ch4-3-step7.png)

    >[!NOTE]
    >Quando você iniciar ou reproduzir o aplicativo, o objeto será circundado por um quadro azul. Fique à vontade para arrastar os cantos do quadro para redimensionar o objeto. Se você quiser que os identificadores de dimensionamento e os identificadores de rotação sejam maiores e mais visíveis, é recomendável usar as configurações da caixa delimitadora padrão (evitando as etapas 4 a 6).

8. Para retornar à visualização da caixa delimitadora padrão, no painel Inspetor do objeto da caixa delimitadora, selecione a alça de rotação pré-fabricado e pressione Delete para removê-la. Quando você entra no modo de reprodução, o wou verá uma visualização de caixa delimitadora semelhante à imagem abaixo.

    ![mrlearning-base-CH4-3-step8. png](images/mrlearning-base-ch4-3-step8.png)

    >[!NOTE]
    >As visualizações da caixa delimitadora aparecem somente no modo de reprodução.

## <a name="adding-touch-effects"></a>Adicionando efeitos de toque

Neste exemplo, reproduziremos um efeito sonoro quando você tocar um objeto com a mão.

1. Adicione um componente de fonte de áudio ao objeto do jogo. Selecione o objeto Octa na sua hierarquia de cena. No painel Inspetor, clique no botão Adicionar componente, procure e selecione fonte de áudio. Usaremos essa fonte de áudio para reproduzir um efeito sonoro em uma etapa posterior.

    >[!NOTE]
    >Verifique se o objeto Octa tem um colisor de caixa nele.

2. Adicione o componente de toque próximo à interação. Clique no botão Adicionar componente no painel Inspetor e procure por uma interação próxima. Selecione-o para adicionar o componente.

    >[!NOTE]
    >Anteriormente, adicionamos perto da interação. A diferença entre essa e a próxima interação é que a interação de captação destina-se a ser capturado e interagir com um objeto. O componente que deve ser tocável destina-se ao objeto a ser tocado. Ambos os componentes podem ser usados juntos para uma combinação de interações.

    ![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. Adicione o script de toque de interação manual. Da mesma forma que a etapa anterior, clique em Adicionar componente e procure o toque de interação à mão para adicioná-lo.

    Observe que você tem três opções com o script:
    * Com o toque concluído: gatilhos quando você toca e libera o objeto
    * No touch Started: Triggers quando o objeto é tocado
    * Com o toque atualizado: os gatilhos periodicamente estão tocando no objeto

    Para este exemplo, iremos trabalhar com a configuração on Touch Started.

    >[!NOTE]
    >Esse script está incluído no pacote do BaseModuleAssets Unity que você importou como no início deste tutorial e ele não está incluído no MRTK original.

4. Clique no botão + na opção on Touch started e arraste o objeto Octa para o campo vazio.

    ![mrlearning-base-CH4-4-step4. png](images/mrlearning-base-ch4-4-step4.png)

5. Na lista suspensa que não diz nenhuma função, selecione Audioname > PlayOneShot. Adicionaremos um clipe de áudio a esse campo usando os seguintes conceitos:

    * O MRTK fornece uma pequena lista de clipes de áudio. Sinta-se à vontade para explorá-las no painel de projeto. Você os encontrará sob os ativos > MixedRealityToolkit. SDK > a pasta de áudio do > de recursos padrão.
    * Para este exemplo, vamos usar o clipe de áudio MRTK_Gem.
    * Para adicionar um clipe de áudio, basta arrastar o clipe desejado do painel projeto para o campo Audioname. PlayOneShot.

    ![mrlearning-base-CH4-4-Step5. png](images/mrlearning-base-ch4-4-step5.png)

   Agora, quando o usuário atinge e toca o objeto Octa, a faixa de áudio MRTK_Gem será reproduzida. O script de toque de interação manual também ajustará a cor do objeto, quando tocado.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a organizar objetos 3D em uma coleção de grade e a manipular esses objetos (dimensionamento, rotação e movimentação) usando a interação próxima (pegando diretamente com as mãos controladas) e a interação extrema (usando raios olhar ou raios de mão). Você também aprendeu como colocar caixas delimitadoras em objetos 3D e aprendeu como usar e personalizar o utensílios nas caixas delimitadoras. Por fim, você aprendeu a disparar eventos ao tocar um objeto.

[Próxima lição: 6. explorando opções de entrada avançadas](mrlearning-base-ch5.md)
