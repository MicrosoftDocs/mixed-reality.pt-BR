---
title: Módulo MR Learning Base - avançada de entrada
description: Conclua este curso para aprender a implementar o reconhecimento de Face do Azure dentro de um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, hololens de tutoriais, unity,
ms.openlocfilehash: c28b607e3532a7c964ab74fdb7a7d514c9293579
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929574"
---
# <a name="mr-learning-base-module---advanced-input"></a>Módulo MR Learning Base - avançada de entrada

Nesta lição, exploraremos várias opções avançadas de entrada para o HoloLens 2, incluindo o uso de comandos de voz, o gesto de Panorâmica e o acompanhamento a olho nu. 

## <a name="objectives"></a>Objetivos

- Saiba como disparar eventos usando palavras-chave e comandos de voz
- Use as mãos controladas para panorâmica texturas e objetos 3D
- Aproveitar os recursos para selecionar objetos de acompanhamento a olho nu do 2 do HoloLens

## <a name="instructions"></a>Instruções

### <a name="enabling-voice-commands"></a>Habilitar os comandos de voz

Nesta seção, podemos irá implementar dois comandos de voz. Primeiro, a capacidade de alternar o painel de diagnóstico de taxa de quadro dizendo "Ativar/desativar diagnóstico". Segundo, a capacidade de reproduzir um som com um comando de voz. Primeiro, exploraremos os perfis MRTK e configurações responsáveis por configurar comandos de voz. 

1. Na hierarquia da cena de Base, selecione "MixedRealityToolkit". No painel Inspetor, role para baixo até as configurações do sistema de entrada. Clique duas vezes para abrir o perfil de sistema de entrada. Clonar o perfil de sistema de entrada para torná-lo editável, como já vimos em [lição 1](mrlearning-base-ch1.md) 

O perfil de sistema de entrada, você verá uma variedade de configurações. Comandos de voz, descer até onde diz, "Configurações do comando de voz". 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. Clonar o perfil de comandos de fala para torná-lo editável, pois aprendemos [lição 1](mrlearning-base-ch1.md). Clique duas vezes no perfil de comando de fala, onde você perceberá uma variedade de configurações. Para obter uma descrição completa sobre essas configurações, consulte o [documentação de fala MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>). 

>Observação: Por padrão, o comportamento geral é iniciado automaticamente. Que pode ser alterado para início manual se desejado, mas para este exemplo, vamos mantê-la no início automático. O MRTK vem com vários comandos de voz padrão (por exemplo, menu Ativar/desativar diagnóstico e criador de perfil de ativar/desativar). Vamos usar a palavra-chave "Ativar/desativar diagnóstico" para ativar e desativar o contador da taxa de quadros de diagnóstico. Também adicionaremos um novo comando de voz nas etapas abaixo.
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. Adicione um novo comando de voz. Para adicionar um novo comando de voz, clique no botão "+ adicionar um novo comando de voz" e você verá uma nova linha é exibida para baixo abaixo da lista de comandos de voz existente. Digite o comando de voz que você deseja usar. Isso ex musicample, vamos usar o comando "reproduzir música".

>Dica: Você também pode definir um keycode para comandos de fala. Isso permite que os comandos de voz disparar após o pressionamento de tecla do teclado.   

4. Adicione a capacidade de responder a comandos de voz. Selecione qualquer objeto na hierarquia de cena base que não tem quaisquer outros scripts de entrada anexados a ele (por exemplo, nenhum manipulador de manipulação.) No painel de inspeção, clique em "Adicionar componente". Digite "manipulador de entrada de fala". Selecione-o.
   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

Por padrão, você verá 2 caixas de seleção, um é a caixa de seleção "é o foco necessário". Isso significa que enquanto você estiver apontando para o objeto com um olhar ray, (olho olhar, olhar head, olhar de controlador ou olhar de mão) o comando de voz será disparado. Desmarque essa caixa de seleção para torná-lo para que o usuário não precisa examinar o objeto para usar o comando de voz.

5. Adicione a capacidade de responder a um comando de voz. Para fazer isso, clique no botão "+" que está no manipulador de entrada de fala e selecione a palavra-chave que você gostaria de responder.

   > Observação: Essas palavras-chave é preenchidos com base no perfil editado na etapa anterior.

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. Ao lado de "Palavra-chave", você verá um menu suspenso. Selecione "Ativar diagnóstico". Isso tornará para que sempre que o usuário disser a frase "Ativar/desativar diagnóstico", ele irá disparar uma ação. Observe que você talvez precise expandir "elemento 0" ao pressionar a seta ao lado dele.

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. Adicionar o "diagnóstico demonstração script de controle" para ativar o diagnóstico de contador da taxa de quadros e desativar. Para fazer isso, pressione o botão "adicionar o componente" e pesquise por "script de controle de demonstração do diagnóstico", em seguida, adicioná-lo a partir do menu. Esse script pode ser adicionado a qualquer objeto, mas para simplificar, nós a adicionaremos ao mesmo objeto como o manipulador de entrada de fala. 

   > Observação: esse script é apenas incluído nesses módulos e não está incluído com o MRTK original.

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. Adicione uma nova resposta no manipulador de entrada de fala. Para fazer isso clique no botão "+" abaixo onde está escrito "resposta ()" (marcado por uma seta verde na figura acima).

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. Arraste o objeto que tem o script de controles de demonstração do diagnóstico para a nova resposta que você criou na etapa 8.
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. Agora selecione a lista suspensa de "nenhuma função", selecione os controles de demonstração do diagnóstico, então "em Ativar/desativar (Diagnóstico)." Essa função ativa e desativa o diagnóstico.  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> Observe que, antes de compilar para seu dispositivo, você precisa habilitar as configurações do mic. Para fazer disso, clique no arquivo, vá para configurações de build, a partir daí, configurações do player e verifique se que o recurso microfone está definido.

Em seguida, estamos adicionando a capacidade de reproduzir um arquivo de áudio do comando de voz usando o objeto "octa". Lembre-se de [lição 4](mrlearning-base-ch4.md), adicionamos a capacidade de reproduzir um clipe de áudio de tocar o objeto octa. Aproveitaremos essa mesma fonte de áudio para nosso comando de voz de música.

11. Selecione o objeto de octa na hierarquia da cena de base.

12. Adicionar outro manipulador de entrada de fala (Repita as etapas 4 e 5), mas com o objeto octa. 

13. Em vez de adicionar o comando de voz "Ativar/desativar diagnóstico" da etapa 6, adicione o comando de voz "reproduzir música", conforme mostrado na imagem abaixo.
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. Assim como acontece com as etapas 8 e 9, adicione uma nova resposta e arraste o octa para o slot vazio na resposta.

15. Selecione o menu suspenso que não diz "nenhuma função," select "Audio Source", em seguida, selecione "PlayOneShot (AudioClip)."

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. Para o clipe de áudio para este exemplo vamos usar o mesmo clipe de áudio da [lição 4](mrlearning-base-ch4.md). Entrar em seu painel do projeto, pesquise "MRTK_Gem" clipe de áudio e arraste-o para o slot de fonte de áudio, conforme mostrado na imagem abaixo. Agora, seu aplicativo deve ser capaz de responder aos comandos de voz "Ativar/desativar diagnóstico" para ativar/desativar painel de contador da taxa de quadro e "reproduzir música" reproduzir música MRTK_Gem.
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>O gesto de Panorâmica 

Neste capítulo, aprenderemos a usar o gesto de panorâmica. É útil para rolagem (usando seu dedo ou mão para rolar pelo conteúdo). Você também pode usar o gesto de panorâmica para girar objetos para executar um ciclo por meio de uma coleção de objetos 3D, ou role até mesmo uma interface do usuário 2D. Podemos vai aprender como usar o gesto de panorâmica para distorcer uma textura. Também exploraremos como mover uma coleção de objetos 3D.

1. Crie um quad. Em sua hierarquia da cena de base, clique com botão direito, selecione "objeto 3D" e selecione "Quad."

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. Reposicione o quad conforme apropriado. Para nosso exemplo, definimos o x = 0, y = 0 e z = 1,5 da câmera para uma posição confortável de 2 HoloLens.

   > Observação: Se os blocos quad (é infront de) qualquer conteúdo das lições anteriores, certifique-se para movê-lo, de modo que não bloquear qualquer um dos outros objetos.

3. Aplica um material para o quad. Este material será o material que podemos será rolar por com o gesto de panorâmica. 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. No painel de seus projetos, digite na caixa de pesquisa "panorâmica de conteúdo". Arraste esse material para o quatro na sua cena. 

> Observação: O material "Panorâmica de conteúdo" não está incluído no MRTK, mas é um ativo no pacote de ativos deste módulo, como importados nas lições anteriores. 

> Observação: Quando você adiciona o conteúdo de panorâmica, ele pode ser ampliado. Você pode corrigir isso, ajustando os valores de valores de x, y e z do tamanho do quad até ficar satisfeito com a aparência.

Para usar o gesto de panorâmica, será necessário um colisor em seu objeto. Você pode ver que o quad já tem um colisor de malha. No entanto, o colisor de malha não é ideal, porque ele é extremamente fina e difícil de selecionar. Sugerimos que você substituir o colisor de malha com um box collider.

5. Clique com botão direito do colisor malha que está no quad (no painel de Inspetor) e em seguida, removê-lo clicando em "Remover componente". 
   ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. Agora, adicione o colisor caixa clicando em "adicionar o componente" e pesquisando "caixa colisor". O padrão adicionados colisor caixa ainda é muito fino, então, clique no botão "Editar colisor" para editá-lo. Quando ele é pressionado, você pode ajustar o tamanho usando o x, y e z valores ou os elementos no editor de cena. Para nosso exemplo, gostaríamos de estender o colisor caixa um pouco atrás do quad. No editor de cena, arraste o colisor caixa na parte de trás, para as extremidades (veja a imagem abaixo). O que isso fará é permitir que o usuário não só usar seu dedo, mas sua mão inteira para rolar. 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. Torna interativo. Como queremos interagir diretamente com o quatro, queremos usar o componente "near interação touchable" (também usamos isso na lição 4 para reprodução de música da octa). Clique em "adicionar o componente" e procurar "quase interação touchable" e selecioná-la, conforme mostrado nas imagens a seguir. 

8. Adicione a capacidade de reconhecer o gesto de panorâmica. Clique em "adicionar o componente" e digite "entregar panorâmica de interação". Você terá uma opção entre ray mão (permitindo que você panorâmica à distância) e o dedo. Neste exemplo, deixe dedo. 
    ![Lesson5 Chapter2 8Im etapa 7](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. No script de panorâmica de interação de mão, o "bloqueio horizontal" e caixas de seleção de "bloqueio vertical" bloqueará os movimentos, respectivamente. As configurações de textura wrap fará com que a textura (mapeamento da textura) siga movimentos de panorâmica do usuário. Neste exemplo, vamos essa caixa de seleção. Também é "velocity ativo" que, se estiver desmarcada, o gesto de panorâmica não funcionará. Bem, essa caixa de seleção. Agora você deve ter um quad panorâmica habilitado.

   

   Em seguida, aprenderemos a panorâmica objetos 3D. 

10. Clique com botão direito no objeto quad, selecione o objeto 3D clique "cubo". Dimensionar o cubo para que ele seja aproximadamente x = 0,1, y = 0,1 e z = 0,1. Copie esse cubo 3 vezes (com o botão direito clicando no cubo e pressionando duplicados ou pelo controle pressionando/comando D). Espaçá-los uniformemente. Sua cena deve ser semelhante à imagem abaixo.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. Selecione o quad novamente e, sob o script de panorâmica de interação de mão, queremos definir as ações de panorâmica a cada um dos cubos. Sob "panorâmica receptores de evento", queremos especificar o número de objetos que estão recebendo o evento. Uma vez que há 4 cubos, tipo "4" e pressione enter. 4 campos vazios devem aparecer.


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. Arraste cada um dos cubos para cada um dos slots de elemento vazio.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Adicione o script de "mover com panorâmica" para todos os cubos. Para fazer isso, pressione e mantenha o controle/comando e selecione cada objeto. Em seguida, no painel de inspeção, clique em "adicionar o componente" e pesquise por "mover com panorâmica". Clique no script e ele será adicionado a cada cubo. Agora, os objetos 3D serão movido com o gesto de Panorâmica! Se você remover a malha renderizar em seu quad, agora você deve ter um quad invisível em que você pode filtrar por meio de uma lista de objetos 3D.

### <a name="eye-tracking"></a>Acompanhamento a olho nu

Neste capítulo, exploraremos como habilitar o rastreamento de olho em nossa demonstração. Podemos girará os itens de menu 3D lentamente quando estão sendo gazed após com olhar de olho. Podemos também disparará uma diversão em vigor quando o item após gazed é selecionado.

1. Certifique-se de que os perfis do Kit de ferramentas de realidade misturada estão configurados corretamente. A partir da redação deste artigo, a configuração de perfil do Kit de ferramentas de realidade misturada não inclui o olho recursos de controle por padrão. Para adicionar funcionalidades de acompanhamento a olho nu, siga as instruções na seção "Configurando os perfis MRTK necessários para acompanhamento de olhos", conforme descrito na [documentação do Toolkit de realidade mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  ). Certifique-se de que esse acompanhamento a olho nu está configurado corretamente seguindo as etapas restantes no link de documentação acima, incluindo a habilitação de acompanhamento de olho no GazeProvider (componente anexado a câmera) e habilitar a simulação de acompanhamento no editor do Unity a olho nu. Nota de versão futura do MRTK pode incluir o acompanhamento de olho por padrão.

    O link acima fornece breves instruções para:

    - Criando o provedor de dados de olhares de olho para uso no perfil MRTK
    - Habilitando o rastreamento de olho no provedor de olhares
    - Configurar para simular o olho no editor de controle
    - Recursos da solução do Visual Studio para permitir o acompanhamento de olho no aplicativo interno de edição

2. Adicione o componente de destino de acompanhamento de olho para objetos de destino. Para permitir que um objeto responder a eventos de olhar olho, precisamos adicionar o componente EyeTrackingTarget em cada objeto que desejamos para interagir com o uso de olhar de olho. Adicione esse componente a cada um dos nove objetos 3D que fazem parte da coleção de grade. Dica: selecione vários itens na hierarquia para o componente EyeTrackingTarget de adicionar em massa.
    ![Etapa 2 de Chapter3 Lesson5](images/Lesson5Chapter3Step2.JPG)

3. Em seguida, adicionaremos o script EyeTrackingTutorialDemo para algumas interações interessantes. O script de EyeTrackingTutorialDemo é incluído como parte do repositório desta série tutoriais e não está incluído por padrão com o Kit de ferramentas de realidade mista. Para cada objeto 3D na coleção de grade, adicione o script de EyeTrackingTutorialDemo por meio de pesquisa para o componente no menu "Adicionar componente".
   ![Etapa 3 do Lesson5 Chapter3](images/Lesson5Chapter3Step3.JPG)

   4. Gire o objeto enquanto olhando o destino. Gostaríamos de configurar o nosso objeto 3D para girar enquanto estamos observando-lo. Para fazer isso, insira um novo campo na seção "Enquanto procurando em Target" do componente EyeTrackingTarget, conforme mostrado na imagem abaixo. 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



No campo recém-criado, adicione o objeto de jogo atual para o campo vazio e selecione EyeTrackingTutorialDemo > RotateTarget() conforme mostrado na imagem abaixo. Agora o objeto 3D é configurado para girar quando está sendo gazed após com o acompanhamento de olho. 

5. Adicione capacidade a "blip target" que está sendo gazed em após select (-indicador e polegar ou dizendo "selecionar"). Semelhante à etapa 4, queremos disparar EyeTrackingTutorialDemo > BlipTarget() atribuindo-o ao campo de "Select ()" do objeto do jogo do componente EyeTrackingTarget, conforme mostrado na figura abaixo. Com esse recurso agora está configurado, você vai notar um ligeiro blip no objeto do jogo, sempre que você acionar uma ação de select, como o polegar ou o comando de voz "select." 
    ![Step 5 do Lesson5 Chapter3](images/Lesson5Chapter3Step5.JPG)
6. Certifique-se de que os recursos de acompanhamento de olho estão configurados corretamente antes de compilar para HoloLens 2. A partir da redação deste artigo, Unity ainda não tem a capacidade de definir a capacidade de olhar entrada (para acompanhamento de olho). Esse recurso de configuração é necessário para o acompanhamento de olho funcionar em 2 o HoloLens. Siga estas instruções sobre a documentação do Kit de ferramentas de realidade mista para habilitar a funcionalidade de olhar entrada: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>Parabéns! 
Você adicionou com êxito o olho básico, recursos de controle para o aplicativo. Essas ações são apenas o começo de um mundo de possibilidades com acompanhamento a olho nu. Este capítulo também conclui a lição 5, em que aprendemos sobre funcionalidades avançadas de entrada, como comandos de voz, movimento panorâmico gestos e acompanhamento de olho. 

[Próxima lição: Experiência de exemplo do Assembly de módulo Lunar](mrlearning-base-ch6.md)

