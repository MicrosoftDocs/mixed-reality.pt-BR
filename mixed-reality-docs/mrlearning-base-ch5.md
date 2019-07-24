---
title: Módulo básico de aprendizado de MR – entrada avançada
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: f9da038fe917e9e45b386de54049d6aa312ecfba
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387780"
---
# <a name="6exploring-advanced-input-options"></a>6. explorando opções de entrada avançadas

Neste tutorial, exploraremos várias opções de entrada avançadas para o HoloLens 2, incluindo o uso de comandos de voz, gesto de panorâmica e acompanhamento de olho. 

## <a name="objectives"></a>Objetivos

- Disparar eventos usando comandos de voz e palavras-chave
- Usar mãos controladas para deslocar texturas e objetos 3D com mãos controladas
- Aproveitar os recursos de acompanhamento de olho do HoloLens 2 para selecionar objetos

## <a name="instructions"></a>Instruções

### <a name="enabling-voice-commands"></a>Habilitando comandos de voz

Nesta seção, implementaremos dois comandos de voz. Primeiro, apresentaremos a capacidade de alternar o painel de diagnóstico de taxa de quadros dizendo "Toggle Diagnostics". Em segundo lugar, veremos a capacidade de tocar um som com um comando de voz. Para começar, exploraremos os perfis MRTK e as configurações responsáveis pela configuração de comandos de voz. 

1. Na hierarquia de cena de base, selecione MixedRealityToolkit. No painel Inspetor, role para baixo até entrada configurações do sistema. Clique duas vezes para abrir o perfil de sistema de entrada. Clone o perfil do sistema de entrada para torná-lo editável como aprendemos na [lição 1](mrlearning-base-ch1.md) 

No perfil do sistema de entrada, há uma variedade de configurações. Para comandos de voz, selecione configurações de comando de fala. 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. Clone o perfil de comandos de fala para torná-lo editável como aprendemos na [lição 1](mrlearning-base-ch1.md). Clique duas vezes no perfil de comando de fala, em que você observará uma variedade de configurações. Para obter uma descrição completa dessas configurações, consulte a [documentação de fala do MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>). 

>Observação: Por padrão, o comportamento geral é iniciado automaticamente. Isso pode ser alterado para início manual, se desejado. Mas, para este exemplo, vamos mantê-lo no início automático. O MRTK vem com vários comandos de voz padrão, como menu, alternância de diagnóstico e alternância do profiler. Usaremos, a palavra-chave "Toggle Diagnostics" para ativar e desativar o contador diagnóstico taxa de quadros. Também adicionaremos um novo comando de voz nas etapas abaixo.
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. Adicione um novo comando de voz. Para adicionar um novo comando de voz, clique no botão + Adicionar um novo comando de fala. Você verá uma nova linha que aparece abaixo da lista de comandos de voz existentes. Digite o comando de voz que você deseja usar. Neste exemplo, vamos usar o comando "Play Music".

>Dica: Você também pode definir um keycode para comandos de fala. Isso permite que os comandos de voz disparem eventos após a prensa de uma tecla de teclado.    

4. Adicione a capacidade de responder a comandos de voz. Selecione qualquer objeto na hierarquia de cena base que não tenha nenhum outro script de entrada anexado a ele (por exemplo, sem manipulador de manipulação). No painel Inspetor, clique em Adicionar componente. Digite "manipulador de entrada de fala" para selecioná-lo.

   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

Por padrão, você verá duas caixas de seleção. Uma é a caixa de seleção é o foco necessário. Isso significa que, desde que você esteja apontando para o objeto com um olhar Ray--olho-olhar, Head-olhar, Controller-olhar ou Hand-olhar--o comando de voz será disparado. Desmarque essa caixa de seleção para que o usuário não precise examinar o objeto para usar o comando de voz.

5. Adicione a capacidade de responder a um comando de voz. Para fazer isso, clique no botão + que está no manipulador de entrada de fala e selecione a palavra-chave que você deseja responder.

   > Observação: Essas palavras-chave são preenchidas com base no perfil editado na etapa anterior.

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. Ao lado de palavra-chave, você verá um menu suspenso. Selecione Ativar/desativar diagnóstico para que sempre que o usuário disser a frase, "ativar/desativar diagnóstico", que dispare uma ação. Observe que talvez seja necessário expandir o elemento 0 pressionando a seta ao lado dele.

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. Adicione o script de controle de demonstração de diagnóstico para ativar e desativar o diagnóstico do contador de taxa de quadros. Para fazer isso, pressione Adicionar componente e pesquise script de controles de demonstração de diagnóstico e adicione-o no menu. Esse script pode ser adicionado a qualquer objeto. Mas, para simplificar, iremos adicioná-lo ao mesmo objeto que o manipulador de entrada de fala. 

   > Observação: Esse script só é incluído com esses módulos e não está incluído no MRTK original.

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. Adicione uma nova resposta no manipulador de entrada de fala. Para fazer isso, clique no botão + abaixo do local em que diz Response () (marcado pela seta verde na imagem acima).

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. Arraste o objeto que tem a demonstração de diagnóstico controla o script para a nova resposta que você acabou de criar na etapa 8.
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. Agora, selecione a lista suspensa "nenhuma função" e selecione controle de demonstração de diagnóstico. Em seguida, selecione a função "on Toggle Diagnostics ()" que ativa e desativa o diagnóstico.  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> Observe que antes de compilar para seu dispositivo você precisa habilitar as configurações do microfone. Para fazer isso, clique em arquivo, vá para configurações de compilação, configurações do Player e verifique se a capacidade do microfone está definida.

Em seguida, adicionaremos a capacidade de reproduzir um arquivo de áudio do comando de voz usando o objeto Octa. Lembre-se da [lição 4](mrlearning-base-ch4.md) que adicionamos a capacidade de reproduzir um clipe de áudio de tocar no objeto Octa. Aproveitaremos essa mesma fonte de áudio para nosso comando de voz de música.

11. Selecione o objeto Octa na hierarquia de cena base.

12. Adicione outro manipulador de entrada de fala (repita as etapas 4 e 5), mas com o objeto Octa. 

13. Em vez de adicionar o comando Ativar voz de diagnóstico da etapa 6, adicione o comando reproduzir música Voice, conforme mostrado na imagem abaixo.
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. Assim como nas etapas 8 e 9, adicione uma nova resposta e arraste o objeto Octa para o slot de resposta vazio.

15. Selecione o menu suspenso que não diz nenhuma função. Em seguida, selecione fonte de áudio e selecione PlayOneShot (AudioClip).

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. Para este exemplo, vamos usar o mesmo clipe de áudio da [lição 4](mrlearning-base-ch4.md). Vá para o painel de projeto, pesquise por "MRTK_Gem" clipe de áudio e arraste-o para o slot de fonte de áudio, conforme mostrado na imagem abaixo. Agora, seu aplicativo responderá aos comandos de voz "Toggle Diagnostics" para alternar o painel do contador de taxa de quadros e reproduzir música para reproduzir a música MRTK_Gem.
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>O gesto de panorâmica 

Nesta seção, veremos como usar o gesto de panorâmica. Isso é útil para rolar usando o dedo ou a mão para rolar pelo conteúdo. Você também pode usar o gesto de panorâmica para girar objetos, para percorrer uma coleção de objetos 3D ou até mesmo para rolar uma interface do usuário 2D. Também aprenderemos como usar o gesto panorâmico para distorcer uma textura e como mover uma coleção de objetos 3D.

1. Crie um quadrante. Na sua hierarquia de cena base, clique com o botão direito do mouse, selecione "objeto 3D" e selecione Quad.

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. Reposicione o quadrante conforme apropriado. Para nosso exemplo, definimos o x = 0, y = 0 e z = 1,5 fora da câmera para uma posição confortável do HoloLens 2.

   > Observação: Se os blocos quádruplos ou estiverem na frente de qualquer conteúdo das lições anteriores, certifique-se de movê-lo para que ele não bloqueie nenhum dos outros objetos.

3. Aplique um material ao quadrante. Este material será o material pelo qual rolaremos com o gesto de panorâmica. 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. No painel projetos, digite a caixa de pesquisa "conteúdo de panorâmica". Arraste esse material para o quadrante na sua cena. 

> Observação: O material de conteúdo de Pan não está incluído no MRTK, mas um ativo no pacote de ativos deste módulo, como importado nas lições anteriores. 

> Observação: Quando você adiciona o conteúdo de panorâmica, ele pode ser ampliado. Você pode corrigir isso ajustando os valores de x, y e z do tamanho do quadrante até estar satisfeito com aparência dele.

Para usar o gesto de panorâmica, será necessário um colisor em seu objeto. Você pode ver que o quadrante já tem um colisor de malha. No entanto, o colisor de malha não é ideal, porque ele é extremamente fino e difícil de selecionar. Sugerimos que você substitua o colisor de malha por um colisor de caixa.

5. Clique com o botão direito do mouse no Colisor de malha que está no meio do painel inspetor. Em seguida, remova-o clicando em remover componente.
    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)
6. Agora, adicione o colisor de caixa clicando em Adicionar componente e pesquisando "Colisor de caixa" o colisor de caixa adicionada padrão ainda é muito fino, portanto, clique no botão Editar colisor para editar. Quando ele é pressionado, você pode ajustar o tamanho usando os valores de x, y e z ou os elementos no editor de cena. Para nosso exemplo, gostaríamos de estender o colisor caixa um pouco atrás do quadrante. No editor de cena, arraste o colisor de caixa da parte de trás, para as extremidades (veja a imagem abaixo). Isso permite que o usuário não use apenas o dedo, mas toda a sua mão para rolar. 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. Torne interativo. Como queremos interagir com o quad diretamente, queremos usar o componente de uso de interação próximo, que usamos isso na lição 4 para reproduzir música do objeto Octa. Clique em Adicionar componente e procure "Near interling touchable" e selecione-o conforme mostrado nas imagens abaixo. 

8. Adicione a capacidade de reconhecer o gesto de panorâmica. Clique em Adicionar componente e digite "Pan de interação com a mão". você terá a opção entre o lado raio (permitindo que você faça a panorâmica de uma distância) e um dedo de índice. Neste exemplo, deixe a opção de dedo indicador. 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. No script Pan de interação à mão, as caixas de seleção Bloquear horizontal e bloquear vertical bloqueiam movimentos, respectivamente. As configurações de textura de encapsulamento fazem a textura (mapeamento de textura) seguir os movimentos de Pan do usuário. Para este exemplo, você marcará essa caixa. Também há uma velocidade ativa, que, se desmarcada, o gesto de panorâmica não funcionará. Marque essa caixa também. Agora você terá um quad habilitado para Pan.

   

   Em seguida, aprenderemos como aplicar panorâmica a objetos 3D. 

10. Clique com o botão direito do mouse no objeto Quad, selecione objeto 3D e clique em cubo. Dimensione o cubo para que ele tenha aproximadamente x = 0,1, y = 0,1 e z = 0,1. Copie esse cubo três vezes clicando com o botão direito do mouse no cubo e pressionando duplicando ou pressionando o controle/comando D. Space-out uniformemente. Sua cena deve ser semelhante à imagem abaixo.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. Selecione o quad novamente e, sob o script de Pan de interação à mão, defina as ações de panorâmica para cada um dos cubos. Nos receptores de eventos Pan, queremos especificar o número de objetos que receberão o evento. Como há quatro cubos, digite "4" e pressione Enter. Quatro campos vazios devem aparecer.


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. Arraste cada um dos cubos para cada um dos slots de elemento vazios.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Adicione o script move com Pan a todos os cubos pressionando e segurando o controle/comando e selecione cada objeto. No painel Inspetor, clique em Adicionar componente e procure "mover com Pan". Clique no script e ele será adicionado a cada cubo. Agora, os objetos 3D serão movidos com o gesto panorâmico. Se você remover a renderização da malha no seu quadrante, terá um quadrante invisível em que poderá aplicar a panorâmica por uma lista de objetos 3D.

### <a name="eye-tracking"></a>Acompanhamento Ocular

Nesta seção, exploraremos como habilitar o acompanhamento de olho em nossa demonstração. Nós vamos girar lentamente nossos itens de menu 3D quando estiverem sendo gazeddos com o olhar de olho. Também dispararemos um efeito divertido quando o item focado for selecionado.

1. Verifique se os perfis de MRTK estão configurados corretamente. No momento da redação deste artigo, a configuração de perfil do Kit de Ferramentas de Realidade Misturada não inclui funcionalidades de acompanhamento ocular por padrão. Para adicionar recursos de acompanhamento de olho, siga as instruções na seção "Configurando os perfis de MRTK necessários para acompanhamento de olho", conforme descrito na [documentação do kit de ferramentas da realidade misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  ). Verifique se o controle de olho está configurado corretamente seguindo as etapas restantes no link de documentação acima, incluindo a habilitação do controle de olho no GazeProvider (o componente anexado à câmera) e a habilitação da simulação de controle de olho no editor do Unity. Observe que as versões futuras do MRTK podem incluir o acompanhamento de olho por padrão.

    O link acima fornece breves instruções para:

    - Criando o Provedor de Dados de olho olhar para uso no perfil MRTK
    - Habilitar o acompanhamento ocular do Provedor de Foco
    - Configurando uma simulação de acompanhamento ocular no editor
    - Editar as funcionalidades da solução do Visual Studio para permitir o acompanhamento ocular no aplicativo criado

2. Adicione o componente de Destino de Acompanhamento Ocular aos objetos de destino. Para permitir que um objeto responda aos eventos olhar de olho, precisaremos adicionar o componente EyeTrackingTarget em cada objeto com o qual desejamos interagir usando o olho olhar. Adicione esse componente a cada um dos nove objetos 3D que fazem parte da coleção de grade. Dica: Selecione vários itens na hierarquia para adicionar o componente EyeTrackingTarget em massa.
    ![Lesson5 Chapter3 Step2](images/Lesson5Chapter3Step2.JPG)

3. Em seguida, adicionaremos o script EyeTrackingTutorialDemo para algumas interações interessantes. O script EyeTrackingTutorialDemo é incluído como parte deste repositório da série de tutoriais. Ele não é incluído por padrão com o kit de ferramentas de realidade misturada. Para cada objeto 3D na coleção de grade, adicione o script EyeTrackingTutorialDemo pesquisando o componente no menu Adicionar componente.
   ![Lesson5 Chapter3 Step3](images/Lesson5Chapter3Step3.JPG)

4. Gire o objeto enquanto olha para o destino. Queremos configurar nosso objeto 3D para girar enquanto estamos olhando para ele. Para fazer isso, insira um novo campo na seção ao examinar o destino () do componente EyeTrackingTarget, conforme mostrado na imagem abaixo. 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



No campo recém-criado, adicione o objeto de jogo atual ao campo vazio e selecione EyeTrackingTutorialDemo > RotateTarget (), conforme mostrado na imagem abaixo. Agora o objeto 3D está configurado para girar quando estiver sendo focado com o acompanhamento ocular. 

5. Adicione a capacidade de "Blip Target" que está sendo gazedda ao selecionar por Air-TAP ou dizendo "Select". Semelhante à etapa 4, desejamos disparar EyeTrackingTutorialDemo > BlipTarget () atribuindo-o ao campo Select () do objeto Game do componente EyeTrackingTarget, conforme mostrado na figura abaixo. Com isso agora configurado, você notará um ligeiro blip no objeto Game sempre que disparar uma ação Select, como o Air-TAP ou o comando de voz "Select". 
    ![Lesson5 Chapter3 Step5](images/Lesson5Chapter3Step5.JPG)
6. Certifique-se de que as funcionalidades de acompanhamento ocular estejam configuradas adequadamente antes de compilar para o HoloLens 2. No momento da redação deste artigo, o Unity ainda não tem a capacidade de definir a entrada olhar para recursos de acompanhamento de olho. A definição dessa funcionalidade é necessária para que o acompanhamento de olho funcione no HoloLens 2. Siga estas instruções na documentação do Kit de Ferramentas de Realidade Misturada para habilitar a funcionalidade de entrada de foco: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>Parabéns! 
Você adicionou com êxito os recursos básicos de acompanhamento de olho ao seu aplicativo. Essas ações são apenas o começo de um mundo de possibilidades com o acompanhamento ocular. Este capítulo também conclui a lição 5, na qual aprendemos sobre a funcionalidade de entrada avançada, como comandos de voz, gestos de panorâmica e acompanhamento de olho. 

[Próxima lição: Experiência de exemplo do assembly de módulo Lunar](mrlearning-base-ch6.md)

