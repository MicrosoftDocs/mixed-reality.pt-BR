---
title: Mão-executiva
description: as mãos 3D disparadas quando o sistema não detecta as mãos do usuário para ajudar a auxiliá-las.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Realidade mista do Windows, design, direito à mão, headset de imersão, MRTK, mãos, mãos de ajuda
ms.openlocfilehash: c5f0a0c241ff71dc93f370a5a8caa627128bfb1a
ms.sourcegitcommit: 1ec628a9107194c0a9d4073b5ca09ee816030e85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2020
ms.locfileid: "78202727"
---
# <a name="hand-coach"></a>Mão-executiva

A mão do direito são as mãos modeladas em 3D que são disparadas quando o sistema não detecta as mãos do usuário. Isso é implementado como um componente "ensinando" que ajuda a orientar o usuário quando o gesto não foi ensinado. Se os usuários não tiverem feito o gesto especificado por um período, as mãos entrarão em loop com um atraso. A mão da direita poderia ser usada para representar o pressionamento de um botão ou a seleção de um holograma.  


Exemplo de ![: mão-](images/HandCoach/MRTK_handCoach.jpg)<br>
*Exemplo de HandCoach de MRTK*

## <a name="hand-coach-provided"></a>Mão da direita fornecida

O modelo de interação atual representa uma ampla variedade de controles de gesto, como rolagem, seleção extrema e quase toque. Abaixo está uma lista completa dos gestos de mão existentes fornecidos no<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:

:::row:::
    :::column:::
       ![exemplo de próximo Select](images/HandCoach/NearSelect.gif)<br>
       **Exemplo de próximo Select-used mostrar como selecionar botões ou fechar objetos que interagem**<br>
    :::column-end:::
    :::column:::
       ![exemplo de toque de ar](images/HandCoach/AirTap.gif)<br>
        **Exemplo de toque de ar – usado para mostrar como selecionar objetos que estão distantes**<br>
    :::column-end:::
    :::column:::
       ![exemplo de mover](images/HandCoach/Move.gif)<br>
       **Exemplo de movimentação de um objeto em espaço-usado para mostrar como mover um holograma no espaço**<br>
    :::column-end:::
    :::column:::
       ![exemplo de girar](images/HandCoach/Rotate.gif)<br>
       **Exemplo de rotação – usado para mostrar como girar hologramas ou objetos**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![exemplo de escala](images/HandCoach/Scale.gif)<br>
       **Exemplo de escala-usado para mostrar como manipular hologramas para serem maiores ou menores**<br>
    :::column-end:::
    :::column:::
       ![exemplo de Palm up](images/HandCoach/PalmUp.gif)<br>
        **Exemplo de Palm up – sugestão de uso, para exibir menus à mão**<br>
    :::column-end:::
    :::column:::
       ![exemplo de HandFlip](images/HandCoach/HandFlip.gif)<br>
       **Exbordo de mão invertida – outra maneira de exibir menus à mão**<br>
    :::column-end:::
    :::column:::
       ![exemplo de](images/HandCoach/Scoll.gif) de rolagem<br>
       **Exemplo de Scroll – usado para rolar uma lista ou um documento longo**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>Conceitos de design

Para Hololens2, criamos interações de mão com base em gestos de instinctual e de mão natural. Acreditamos que eles sejam intuitivos para a maioria dos usuários e, portanto, não criamos momentos de aprendizado de gestos dedicados. Em vez disso, criamos a assistência de mão para ajudar os usuários que podem ficar presos ou que não estão familiarizados com a interação com os hologramas sobre esses gestos. Sem um momento de aprendizado, sentimos que mostrar aos usuários como executar uma ação demonstrando que seria a melhor opção. Em nossos estudos, descobrimos que os usuários conseguiram descobrir o gesto, mas precisavam de uma pequena orientação. Se detectarmos que um usuário não interage com um objeto por um período, uma mão orientada seria disparada demonstrando o posicionamento correto e o local do dedo. 

### <a name="intuitive"></a>Simples

Ao animar as mãos, deve ser óbvio e shoudn't causar qualquer confusão. A animação das mãos é uma representação do gesto que você está tentando evocar ao usuário para entender sua finalidade. 

Por exemplo, se você quiser que um usuário pressione um botão, um botão à mão será disparado.

![exemplo: mão com o direito ao lado de toque](images/HandCoach/NearSelect_unity.gif)<br>
*Mão da direita demonstrando perto de tocar em uma gem*  

### <a name="hand-scale"></a>Escala manual

Testamos vários tamanhos de mão com os menus da interface do usuário e sentimos que, se as mãos fossem verdadeiras para o tamanho, ela deu uma menacing, mas se fosse muito pequena, era difícil ver e entender o gesto. 

**Voz e mãos**

Não espere que os usuários possam ouvir um conjunto de instruções por meio de voz e assistir a instruções diferentes por meio da mão. Sequenciar suas instruções para ajudar os usuários a se concentrarem em relação à sua atenção para reduzir a sobrecarga do sensor.


## <a name="can-i-create-my-own"></a>Posso criar o meu próprio?

Sim! Incentivamos você a criar seu próprio gesto exclusivo para seu jogo e contribuir de volta para a Comunidade!
Fornecemos um arquivo Maya de um rigged Hand que pode ser usado para seu aplicativo que pode ser baixado aqui: <a href="files/HandCoach_MRTK.zip">baixar HandCoach_MRTK. zip</a>

![exemplo de mãos animadas no Maya](images/HandCoach/MayaSelect_Gif.gif)<br>
*Exemplo de mão animada ao investigar uma caixa no Maya*


**Ferramenta de criação recomendada**

Entre artistas 3D, muitos optam por usar o [Maya do Autodesk, que é capaz de usar o HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) para transformar a maneira como os ativos são criados. O arquivo hands fornecido é um arquivo binário Maya, portanto, é recomendável usar Maya para animar e exportar as mãos. Se você preferir usar outro programa 3D, aqui está um <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">Baixe HandCoachMRTK_FBX. zip</a> para criar sua própria configuração de controlador. 

Se estiver usando o arquivo de mão Maya baixado fornecido, é recomendável reduzir verticalmente as mãos no Unity para 0,6.

![exemplo: mão do Maya Rig em](images/HandCoach/MayaExample.png)<br>
*Rigged hands*

### <a name="technical-specs"></a>Especificações técnicas

*   O arquivo de dois mãos está disponível no formato ASCII Maya
*    A mão direita e esquerda está disponível no formato binário Maya
*   Definir o arquivo Maya para 24 FPS
*   Dentro do arquivo, há um lado esquerdo e direito que pode ser usado para gestos de dois mão ou de mão única. A mão direita só estará visível por padrão.
*   É recomendável deixar um buffer de cerca de 10 quadros no início e no final para esmaecer
*   Se animar um objeto com um destino especificado, sua prática recomendada será animar para uma caixa padrão ou NULL.
*   Se a mão estiver animando um objeto físico, como uma caixa, sua melhor prática para não animar a tradução em Maya, mas esperar para animá-la no Unity ou no código.
*   A animação visível deve ser 1,5 segundos para que todas as informações significativas sejam transmitidas
*   Quando você sentir satisfeito com sua animação:
    *   Selecionar todas as junções e distortar quadros-chave
    *   Exclua os controladores, selecione as junções e a malha e exporte como um FBX
    *  Se houver várias animações, você poderá usar o exportador de jogos interno do Maya: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>Exportando do Maya

Depois de estar satisfeito com sua animação
* Selecionar todas as junções: selecionar hierarquia de >

     ![Exemplo: local do menu](images/HandCoach/Hierarchy.png)<br>
* Distortar sua animação: alternar para animação > chave > animação de torta

     ![Exemplo: local do menu](images/HandCoach/BakeAnimation.png)<br>
* Excluir o dispositivo de controlador: contorno > MainR_Grp ou MainL_Grp

     ![Exemplo: local do menu](images/HandCoach/ControllerRig.png)<br>

* Exportar como FBX: selecione JNT + malha: arquivo > Exportar seleção (caixa de opção) > Exportar seleção

     ![Exemplo: local do menu](images/HandCoach/OptionBox.png)<br>

     ![Exemplo: local do menu](images/HandCoach/SelectionExport.png)<br>

     ![Exemplo: local do menu](images/HandCoach/FBXSelection.png)<br>


 Ao exportar como um FBX e trazido para o Unity, dimensione as mãos para 0,6. Descobrimos que esse foi um equilíbrio perfeito para a exibição das mãos. 

Exemplo de ![: configurações de Unity](images/HandCoach/HandHintScale.png)<br>
*Configurações de Unity para HandCoach_R pré-fabricado encontradas em MRTK*


## <a name="implementing-hands-into-your-unity-project"></a>Implementando mãos em seu projeto do Unity

### <a name="best-practices"></a>Práticas recomendadas
*    É recomendável reduzir verticalmente as mãos no Unity para 0,6
*   As mãos devem ser executadas duas vezes e, se não forem concluídas, passarão continuamente em loop até que o gesto seja concluído. As mãos devem ser repetidas duas vezes para garantir que o usuário tenha tempo para se registrar e ver o gesto. As mãos devem aparecer e desaparecer entre os loops. 
 *  Se as mãos do usuário estiverem visíveis por câmeras HL2, mas os usuários não estiverem fazendo a interação necessária, as mãos serão exibidas após 10 segundos.
*   Se as mãos do usuário não estiverem visíveis por câmeras HL2, as mãos aparecerão após 5 segundos.  
*   Se as mãos do usuário forem visivelmente rastreadas por câmeras HL2s no meio da animação, a animação será concluída e desaparecer.
*   Se você estiver incluindo a voz, sugerimos que ela corresponda ao gesto da mão.
*   Se você tiver ensinado as mãos pelo menos uma vez, repita o gesto se tiver detectado que o usuário está preso.
*   Se as posições de dedos/mãos específicas forem críticas, verifique se os usuários podem ver claramente essas nuances na animação. Experimente Angling as mãos para que as partes mais importantes fiquem claramente visíveis. 
* Se você perceber distorção nas mãos, precisará ir para as configurações de qualidade do Unity aumentar a quantidade de Bones. 
 Acesse as configurações de projeto de > de edição do Unity > qualidade > outros pesos do Blend >. Verifique se "4 Bones" estão selecionados para ver as junções suaves. 

   ![Exemplo: local do menu](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a>O que evitar
* Dimensionar as mãos muito grandes
* colocar as mãos muito próximas ao usuário
* As mãos só devem ser ensinadas uma vez. O excesso de ensino pode causar confusão e bagunças
*   Colocando-o no Unity, baixe o MRTK mais recente aqui: https://github.com/microsoft/MixedRealityToolkit-Unity
    *   Material: Teaching_Hand2
    *   Scripts: consulte as diretrizes do MRTK para o <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">MRTK Hand</a>
    *   Configuração por projeto
        *   Cena definida como UWP: a instrução pode ser encontrada no [projeto do Unity de configuração](Configure-Unity-Project.md) para o Windows Mixed Reality

## <a name="see-also"></a>Consulte também
* [Interação-conceitos básicos](interaction-fundamentals.md)
* [Processo de criação de ativos](asset-creation-process.md)
* [Gestos](gestures.md)
* [Instalar as ferramentas](install-the-tools.md)
* [Configurar projeto do Unity](Configure-Unity-Project.md)
* [Visão geral do desenvolvimento do Unity](unity-development-overview.md)
* [MRTK 101](mrtk-101.md)
